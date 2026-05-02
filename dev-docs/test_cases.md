# Image Converter: Test Cases

*Created: 2026-05-02*
*Last updated: 2026-05-02*

This file is the daily QA contract for Antigravity/Codex and the user.

Rule: before implementing any day from `execution_plan.md`, the agent must add concrete test cases for that day in this file. After implementation, the agent must run the automated checks, record evidence, and leave the manual checks for the user unless the user explicitly confirms them.

## Status Legend

| Status | Meaning |
|---|---|
| Not written | Test cases for this day still need to be expanded before coding. |
| Ready | Test cases are written but not run. |
| Automated pass | Agent ran automated checks and they passed. |
| Automated fail | Agent ran automated checks and at least one failed. |
| Manual pending | User still needs to test on device. |
| Manual pass | User confirmed the manual check passed. |
| Manual fail | User found an issue manually. |
| Blocked | Test cannot run because of missing dependency/device/permission. |

## Required Automated Checks Every Coding Day

Run from `C:\dev\image-converter`.

| Check | Command / Method | Required Evidence |
|---|---|---|
| Build | `./gradlew.bat assembleDebug --console=plain` | Build result and error summary if failed. |
| Unit tests | `./gradlew.bat testDebugUnitTest --console=plain` once tests exist | Pass/fail count. |
| Device detection | `adb devices` | Connected device serial or blocked reason. |
| Install | `./gradlew.bat installDebug --console=plain` when device is connected | Install result. |
| Launch smoke | `adb shell monkey -p com.sreekanth.imageconverter -c android.intent.category.LAUNCHER 1` | No crash and app opens. |
| Runtime logs | Check crash/logcat only when behavior fails | Short relevant error summary. |
| Docs | Update `history.md` and `testing_log.md` | Files updated with the day result. |

## Testing Strategy

- Unit test pure logic: format selection, transparency handling decisions, quality values, resize math, output metadata, filename generation.
- Use deterministic sample images committed under test resources when conversion engine tests are added.
- Use fake image repositories for Compose UI tests so options/preview/result screens can be tested without real user media.
- Use device/instrumented tests for Photo Picker intent, save/share flows, and large-image progress when practical.
- Use manual testing for real previews, transparent PNG to JPG behavior, perceived quality, save/share UX, visual polish, and "offline/no upload" trust.

## Ad Format QA Requirements

These checks apply to every ad-related day.

| Area | Automated Check | Manual Check |
|---|---|---|
| Test-only ads | Verify debug config uses only Google demo/test IDs for adaptive banner, interstitial, native, and native video | Confirm visible ads show test labeling/headline where the SDK provides it |
| No live ads before completion | Search source/build config for production ad unit IDs before release approval | Confirm no real advertiser ad is clicked during development |
| Banner ads | Verify banner only renders on allowed safe surfaces after useful content | Confirm banner does not cover format options, conversion progress, save, or share controls |
| Interstitial ads | Verify frequency cap and natural-transition gate exist | Confirm no interstitial appears before image selection, during options/preview/progress, or before output is ready |
| Native Advanced video ads | Verify `MediaView`, visible `Ad` label, AdChoices placement, CTA/assets, and native destroy handling | Confirm video/native card is clearly an ad and visually separate from save/share actions |

## Day-by-Day QA Matrix

| Day | Feature Gate | Test Cases Written | Automated Status | Manual Status | Evidence / Notes |
|---|---|---|---|---|---|
| 1 | Product grounding | Not written | Blocked | Manual pending | Docs-only day; verify supported formats are honest. |
| 2 | Navigation | Not written | Blocked | Manual pending | Home, picker, options, preview, result, history, settings. |
| 3 | Image picker | Not written | Blocked | Manual pending | Photo Picker, metadata, cancel/error. |
| 4 | Format options | Not written | Blocked | Manual pending | JPG/PNG/WebP selector, quality, background, resize toggle. |
| 5 | Conversion engine | Not written | Blocked | Manual pending | JPG, PNG, WebP, MIME/dimensions. |
| 6 | Preview screen | Not written | Blocked | Manual pending | Original preview, settings, no UI freeze. |
| 7 | Result screen | Not written | Blocked | Manual pending | Converted preview, before/after size, save/share. |
| 8 | Save and share | Not written | Blocked | Manual pending | Save, share, filename, failures. |
| 9 | Resize option | Not written | Blocked | Manual pending | Width/height, aspect ratio, presets, validation. |
| 10 | PDF output | Not written | Blocked | Manual pending | Image-to-PDF only if stable, otherwise defer. |
| 11 | History | Not written | Blocked | Manual pending | Recent outputs without storing originals unnecessarily. |
| 12 | Settings | Not written | Blocked | Manual pending | Defaults, theme, clear history. |
| 13 | UI polish | Not written | Blocked | Manual pending | Format chips, progress, dark mode, small screen. |
| 14 | Accessibility | Not written | Blocked | Manual pending | Slider announcements, text scaling, contrast. |
| 15 | Privacy and compliance | Not written | Blocked | Manual pending | Offline wording, selected-file-only access. |
| 16 | Ad architecture test-only | Not written | Blocked | Manual pending | Banner, interstitial, native, native video test IDs and lifecycle cleanup only. |
| 17 | Banner and Native Advanced ad UI | Not written | Blocked | Manual pending | Ad below result/history, away from save/share, with banner container. |
| 18 | Safe ad placement and interstitial gate | Not written | Blocked | Manual pending | No ad before first successful conversion; interstitial frequency cap enforced. |
| 19 | Internal QA | Not written | Blocked | Manual pending | JPG, PNG, WebP, transparency, resize, save/share. |
| 20 | Play Store prep | Not written | Blocked | Manual pending | Listing/screenshots/data safety/privacy. |
| 21 | First release decision | Not written | Blocked | Manual pending | Release only if single-image conversion is stable. |

## Detailed Test Case Template

When starting a day, add a section named `Day N Detailed Test Cases` below and fill it before coding.

| ID | Type | Test Case | Steps | Expected Result | Automated Result | Manual Result | Evidence |
|---|---|---|---|---|---|---|---|
| IC-DN-A01 | Automated | Build remains green | Run the build command | Build succeeds | Ready | Manual pending | Pending |
| IC-DN-M01 | Manual | User-visible flow feels fast and private | User tests on Vivo V2426 | Flow is clear, polished, and honest about supported formats | Automated pass when applicable | Manual pending | Pending |

## Open Manual QA Queue

Manual checks stay here until the user tests them.

| Date Added | Day | Area | Manual Check | Status | User Notes |
|---|---|---|---|---|---|
| 2026-05-02 | All | Baseline | Confirm app opens, splash/icon/name look correct on device | Manual pending |  |
