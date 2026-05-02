# Image Converter: Execution Plan

*Created: 2026-05-01*
*Last updated: 2026-05-02*
*Research pass: 2026-05-02*

This plan turns the starter project into an offline image converter with a clean, premium workflow. The differentiator is privacy: conversion happens on device, selected files only, no cloud server.

## Agent Execution Contract

When Antigravity/Codex is asked to complete one day or a range of days, it must treat this file as the product and engineering source of truth.

- Read `product.md`, `features.md`, `ui_system.md`, `play_store_compliance.md`, `testing_log.md`, `test_cases.md`, and this file before changing code.
- Implement only the requested day range unless a dependency from an earlier day is missing; document any unavoidable prerequisite work.
- Before coding each day, expand that day's section in `test_cases.md` with concrete automated and manual test cases.
- After coding each day, run the automated checks listed in `test_cases.md`, update automated status/evidence, and leave manual status open for the user unless the user explicitly confirms it.
- Update `history.md`, `testing_log.md`, and `pre-release-checklist.md` whenever a milestone, test pass, or release gate changes.
- Never mark a day complete if build, install, launch, or the day-specific automated tests fail.

## Quality Bar

- UI must feel premium, fast, and task-first: no landing page, no clutter, no ads before the first successful conversion.
- Architecture must stay layered: Compose UI, ViewModel/state holder, domain/use cases for conversion, repositories/local output store.
- State must follow unidirectional data flow; conversion operations expose progress, cancellation, and result state clearly.
- Data must be local-first. No account, backend, analytics, or cloud dependency unless a future plan explicitly adds it.
- Conversion correctness beats format count: JPG/PNG/WebP behavior, transparency handling, dimensions, and file size must be testable.
- Accessibility is part of completion: scalable text, 48dp controls, TalkBack labels for sliders/chips/results, and non-color-only status.
- Store/UI copy must be honest about supported formats; do not claim broad format support before implementation.

## Current Status

- [x] Native Android project created
- [x] Kotlin + Jetpack Compose + Material 3 setup
- [x] Package: `com.sreekanth.imageconverter`
- [x] Debug build successful
- [x] Installed on Vivo V2426 / Android 16
- [x] Launch smoke test passed
- [x] Dev docs created
- [x] README created
- [x] Git repository initialized
- [x] Adaptive launcher icon added
- [ ] Real image conversion functionality
- [ ] Production ad units
- [ ] Play Store release assets

## Research Notes

Competitors such as PixConverter, Rectfy Image Converter, and JPG/PNG/WebP converters emphasize JPG/PNG/WebP/PDF, batch conversion, quality sliders, resolution options, preview, save/share, and converted file management. Some competitors use cloud conversion; this app should compete with offline privacy and simplicity.

Important constraints:

- Use Android Photo Picker for selected images.
- Avoid broad storage permissions where possible.
- Be honest about supported formats; do not claim 50+ formats unless implemented.
- Conversion must preserve transparency correctly for PNG/WebP where supported.

## Product Positioning

One-line promise:

Convert JPG, PNG, WebP, and PDF image outputs offline with quality and size controls.

Primary users:

- Users converting images for forms/sites
- Creators who need JPG/PNG/WebP quickly
- Users who want privacy and no cloud upload
- Users batch-converting images later in v2

## Release Strategy

- V1: Single image JPG/PNG/WebP conversion, quality control, resize option, save/share.
- V1.1: PDF output and better transparency/background controls.
- V1.2: AdMob Native Advanced after successful conversions.
- V2: Batch conversion and premium/ad-free option.

Subscription caution:

This is a utility app. Prefer ads plus one-time lifetime unlock first. Subscription only makes sense if recurring value is added, such as maintained format packs, advanced batch workflows, or continuous premium tools.

## Monetization Plan

Ad formats in scope for the full plan:

- **Adaptive banner ads**: Low-priority monetization on safe, non-conversion surfaces after useful content is visible.
- **Interstitial ads**: Frequency-capped full-screen ads only at natural transitions after successful conversion/save/share; never before selection, during options, preview, active conversion, or near save/share buttons.
- **Native Advanced video ads**: Premium-looking native ad cards with `MediaView`, visible `Ad` label, AdChoices, CTA, advertiser/icon/headline assets, and lifecycle cleanup.

Hard test-ad rule:

- Until the app is feature-complete, internally QA-passed, and release-ready, every ad integration must use test ads only.
- Use Google demo ad units during development: Adaptive Banner `ca-app-pub-3940256099942544/9214589741`, Interstitial `ca-app-pub-3940256099942544/1033173712`, Native `ca-app-pub-3940256099942544/2247696110`, Native Video `ca-app-pub-3940256099942544/1044960115`.
- Production ad unit IDs must not be added to source code, docs, or build config until a separate release-readiness task approves UMP consent, privacy policy, frequency caps, and safe placement testing.
- Debug builds must never request live ads.

Use AdMob Native Advanced with video-capable media on results and history, not during conversion setup.

Allowed ad placements:

- Conversion result screen below output summary
- History screen after recent converted files
- Settings/About bottom section
- Batch completion screen in v2

Blocked ad placements:

- Format/quality control panel
- Save/share button area
- Photo Picker flow
- Active conversion progress
- First launch before a conversion

Implementation requirements:

- Use test ad units for banner, interstitial, native, and native video during development.
- Clear `Ad` label and visible AdChoices.
- Use MediaView for image/video native ads.
- Enable hardware acceleration.
- Destroy native ads when no longer needed.
- Add UMP consent before live ads.

## Premium UI Direction

- Orange brand with clean utility feel
- First screen is "Choose Image" and format picker
- Clear input/output format chips
- Preview before and after
- Output cards show format, dimensions, file size, transparency/background
- No cloud or upload language unless a backend exists

## Day-by-Day Plan

Daily definition of done:

- Code for the requested day is implemented and scoped.
- `./gradlew.bat assembleDebug --console=plain` passes.
- If a device is connected, `./gradlew.bat installDebug --console=plain` passes and the app launches without crash.
- Relevant unit/instrumented/UI tests are added or updated for the day's behavior.
- `dev-docs/test_cases.md` has automated results recorded and manual results left for user verification.
- `dev-docs/history.md` and `dev-docs/testing_log.md` are updated with evidence.

### Day 1: Product Grounding

- [ ] Update docs around offline image conversion.
- [ ] Define v1 formats: JPG, PNG, WebP.
- [ ] Define v1 options: quality, resize, background for transparency.
- [ ] Confirm no broad storage permissions.

### Day 2: Navigation

- [ ] Add Compose Navigation.
- [ ] Create routes: Home, PickImage, ConvertOptions, Preview, Result, History, Settings, About.
- [ ] Replace placeholder UI.
- [ ] Add app shell.

### Day 3: Image Picker

- [ ] Integrate Android Photo Picker.
- [ ] Support single image selection.
- [ ] Load metadata: dimensions, MIME type, file size.
- [ ] Handle cancel/error states.

### Day 4: Format Options

- [ ] Build output format selector: JPG, PNG, WebP.
- [ ] Add quality slider for JPG/WebP.
- [ ] Add background color option when converting transparent images to JPG.
- [ ] Add resize toggle.

### Day 5: Conversion Engine

- [ ] Implement bitmap decode safely.
- [ ] Implement JPG output.
- [ ] Implement PNG output.
- [ ] Implement WebP output where Android API supports it.
- [ ] Add unit tests for output MIME/dimensions.

### Day 6: Preview Screen

- [ ] Show original preview and output settings.
- [ ] Show estimated result where possible.
- [ ] Add convert button.
- [ ] Handle large images without UI freeze.

### Day 7: Result Screen

- [ ] Show converted preview.
- [ ] Show before/after file size.
- [ ] Show format and dimensions.
- [ ] Add save/share actions.

### Day 8: Save and Share

- [ ] Save converted image through MediaStore or user-selected destination.
- [ ] Add share sheet.
- [ ] Add filename template.
- [ ] Handle failures gracefully.

### Day 9: Resize Option

- [ ] Add custom width/height.
- [ ] Add preserve aspect ratio toggle.
- [ ] Add common presets.
- [ ] Validate inputs.

### Day 10: PDF Output

- [ ] Add image-to-PDF output if stable.
- [ ] Support page size: image size, A4, letter.
- [ ] Add PDF preview placeholder.
- [ ] If not stable, move PDF to v1.1.

### Day 11: History

- [ ] Store recent conversion metadata locally.
- [ ] Show recent outputs.
- [ ] Allow re-share if file exists.
- [ ] Do not store original unnecessarily.

### Day 12: Settings

- [ ] Default output format.
- [ ] Default quality.
- [ ] Default save behavior.
- [ ] Theme mode.
- [ ] Clear history.

### Day 13: UI Polish

- [ ] Polish format chips and result cards.
- [ ] Add loading/progress animation.
- [ ] Verify dark mode.
- [ ] Verify small screen layout.

### Day 14: Accessibility

- [ ] Add content descriptions.
- [ ] Verify text scaling.
- [ ] Verify contrast.
- [ ] Ensure slider values are announced.

### Day 15: Privacy and Compliance

- [ ] Confirm conversion is offline.
- [ ] Confirm no cloud/API language.
- [ ] Confirm selected-file-only access.
- [ ] Update Play Store compliance doc.

### Day 16: Ad Architecture, Test Only

- [ ] Add Google Mobile Ads SDK.
- [ ] Add wrappers/state holders for adaptive banner, interstitial, native, and native video.
- [ ] Use test ad unit IDs only.
- [ ] Add lifecycle destroy handling for `AdView` and native ads.
- [ ] Add interstitial frequency cap and natural-transition gate.

### Day 17: Banner and Native Advanced Ad UI

- [ ] Build adaptive banner container for safe lower-content surfaces.
- [ ] Build native advanced video-capable ad card for result/history.
- [ ] Include visible `Ad` label, AdChoices, MediaView, CTA.
- [ ] Keep ad away from save/share buttons.
- [ ] Add loading/failed state.

### Day 18: Safe Ad Placement and Interstitial Gate

- [ ] Place banner/native ad below result summary after conversion.
- [ ] Place banner/native ad after history items.
- [ ] Show interstitial only after successful conversion/save/share or when leaving Result, never before output is ready.
- [ ] Add frequency cap.
- [ ] Verify no ad before first successful conversion.

### Day 19: Internal QA

- [ ] Run `assembleDebug`.
- [ ] Run `installDebug`.
- [ ] Test JPG, PNG, WebP, transparent PNG to JPG, resize, save/share.
- [ ] Update testing log.

### Day 20: Play Store Prep

- [ ] Draft store listing around offline image conversion.
- [ ] Prepare screenshots: Home, Options, Preview, Result, History.
- [ ] Prepare Data Safety notes.
- [ ] Prepare privacy policy.

### Day 21: First Release Decision

- [ ] Release if single-image conversion is stable.
- [ ] Keep batch conversion for v2.
- [ ] Do not add subscription before v1 metrics.

## Future Backlog

- Batch conversion
- TIFF/BMP support if libraries are stable
- HEIC support where platform allows
- PDF multi-image batch
- Saved conversion presets
- One-time lifetime ad-free unlock
- Subscription only if recurring premium tools exist

## Research References

- Google Play: PixConverter, Rectfy Image Converter, Image Converter JPG/PNG/WebP competitor listings
- Android Photo Picker: https://developer.android.com/training/data-storage/shared/photo-picker
- Google Play sensitive permissions: https://support.google.com/googleplay/android-developer/answer/16558241
- AdMob Native Ads Android: https://developers.google.com/admob/android/native
- AdMob advanced native options: https://developers.google.com/admob/android/native/options
- Google Play subscriptions policy: https://support.google.com/googleplay/android-developer/answer/9900533
