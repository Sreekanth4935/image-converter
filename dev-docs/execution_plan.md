# Image Converter: Execution Plan

*Created: 2026-05-01*
*Last updated: 2026-05-01*
*Research pass: 2026-05-01*

This plan turns the starter project into an offline image converter with a clean, premium workflow. The differentiator is privacy: conversion happens on device, selected files only, no cloud server.

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

- Use test native ad unit during development.
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
- [ ] Add native ad wrapper.
- [ ] Use test ad unit IDs only.
- [ ] Add lifecycle destroy handling.

### Day 17: Native Ad UI

- [ ] Build native ad card for result/history.
- [ ] Include visible `Ad` label, AdChoices, MediaView, CTA.
- [ ] Keep ad away from save/share buttons.
- [ ] Add loading/failed state.

### Day 18: Safe Ad Placement

- [ ] Place ad below result summary after conversion.
- [ ] Place ad after history items.
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
