# Image Converter: Feature List

*Created: 2026-05-01*
*Last updated: 2026-05-02*

This document lists all planned features for Image Converter.

---

## 1. Core V1 Features

- **Android Photo Picker input**: User-selected image only.
- **Format detection**: Read input MIME type, dimensions, and file size.
- **JPG output**: Convert supported bitmap input to JPG.
- **PNG output**: Convert supported bitmap input to PNG.
- **WebP output**: Convert where Android API support is stable.
- **Transparency handling**: Background color choice when converting transparent input to JPG.
- **Quality settings**: Quality slider for JPG/WebP where supported.
- **Resolution control**: Optional resize with preserve-aspect-ratio toggle.
- **Preview screen**: Show selected image and output settings before conversion.
- **Result screen**: Show converted preview, format, dimensions, and before/after file size.
- **Save/share**: User-initiated output save/share.
- **Recent conversions**: Local metadata only where useful.

## 2. Settings and Customization (Planned)

- **Theme Toggle**: Dark / Light / System mode
- **Language Support**: English initially, expandable
- **Default output format**: JPG/PNG/WebP preference
- **Default quality**: Remember last quality value
- **Default background color**: For transparent-to-JPG conversion
- **Clear history**: Remove local recent-conversion metadata

## 3. Ads and Monetization

- **Test-only ads during development**: Banner, interstitial, native, and native video must use Google demo/test units only.
- **Safe banner ads**: Result/history/settings after useful content only.
- **Safe interstitial ads**: Frequency-capped after successful conversion/save/share or leaving Result, never before output is ready.
- **Native Advanced video ads**: Result/history safe surfaces with Ad label, AdChoices, MediaView, and lifecycle cleanup.
- **Ad-free unlock**: Future one-time purchase after core workflow is stable.

## 4. Premium Future Features

- **Batch conversion**: Multi-image conversion after single-image V1 is reliable.
- **PDF output**: Image-to-PDF if stable.
- **HEIC support**: Only where platform support is reliable.
- **TIFF/BMP support**: Only after library verification.
- **Saved conversion presets**: Reuse common output settings.
- **Ad-free mode**: Remove ads after app quality is proven.

## 5. Explicitly Out of Scope for V1

- "50+ formats" or broad unsupported format claims
- HEIC/TIFF/BMP as core V1 unless implemented and tested
- Cloud conversion/upload
- Batch conversion
- Broad storage access or `MANAGE_EXTERNAL_STORAGE`
- Live production ads
- Subscription-only core conversion

## 6. Privacy and Compliance

- **No Login Required**: App works fully offline
- **Local-Only Storage**: All data stays on-device
- **No Unnecessary Permissions**: Only request what is needed
- **Privacy Policy**: Will be hosted externally and linked in-app
- **Honest Format Copy**: Only shipped and tested formats may appear in store copy or primary UI
