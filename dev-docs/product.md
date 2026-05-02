# Image Converter: Product Overview

*Created: 2026-05-01*
*Last updated: 2026-05-02*

## App Identity

- **App Name:** Image Converter
- **Package:** com.sreekanth.imageconverter
- **Category:** Photography / Tools
- **Theme Color:** #FF6D00

## Purpose

Convert selected images between JPG, PNG, and WebP locally with quality, resize, transparency, preview, and save/share controls.

This is not meant to compete as a broad "all file converter" that claims many formats before they are implemented. The differentiator is privacy and predictability: selected files only, no cloud upload, clear input/output format, transparency handling, and result preview before save/share.

## Product Differentiator

| Broad/Cloud Converter | Image Converter |
|---|---|
| Often uploads files | Converts selected images on device |
| Claims many formats | Ships only verified supported formats |
| Weak transparency handling | Explicit background choice for transparent image to JPG |
| No clear result summary | Shows format, dimensions, file size, and preview |
| Batch-first complexity | Simple single-image V1 before batch workflows |
| Ad-heavy before value | Ads only after successful conversion and test-only until release |

## Core V1 Experience

1. User selects one image through Android Photo Picker.
2. App reads input metadata: format, dimensions, and file size.
3. User chooses output format: JPG, PNG, or WebP.
4. For JPG/WebP, user can adjust quality where supported.
5. If converting transparency to JPG, user chooses a background color.
6. User can optionally resize while preserving aspect ratio.
7. Result screen shows converted preview and before/after metadata.
8. User saves or shares the converted file.

## Target Audience

- Users converting images for forms, websites, or chat apps
- Creators who need quick JPG/PNG/WebP outputs
- Users who do not want to upload images to online converters
- Users who need transparent image handling explained clearly
- Users in regions with limited or expensive data connectivity

## Product Principles

1. **Offline-first**: All core features work without internet
2. **No account required**: Zero login, zero signup
3. **Privacy-first**: No data leaves the device
4. **Simple UX**: Every screen understandable in under 1 second
5. **Lightweight**: Minimal APK size, minimal battery usage
6. **Honest format support**: Do not list unsupported formats as core features
7. **Result clarity**: Conversion is not done until output metadata and preview are clear

## Planned Feature Layers

### V1: Useful Free App

- Single selected image workflow
- Input metadata reading
- JPG, PNG, WebP output
- Quality slider for supported lossy formats
- Transparency background handling
- Optional resize
- Result preview and metadata
- Save/share output

### V1.1: Polish and Output Options

- PDF output only if stable
- Better large-image progress state
- Recent conversion history
- Saved conversion defaults
- Test-only ads after successful conversion

### V2: Premium Direction

- Batch conversion
- HEIC support where platform allows
- TIFF/BMP support only after library verification
- Multi-image PDF export
- Saved preset packs
- One-time ad-free unlock

## Revenue Strategy (Future)

- Free tier with safe ads after successful conversion
- Test ads only until app is feature-complete and release-approved
- Prefer one-time ad-free unlock before subscription
- Subscription only if advanced recurring tools or maintained format packs exist later
- No backend costs in year 1

## Technical Foundation

- Native Android (Kotlin + Jetpack Compose)
- Material 3 Design
- MVVM architecture
- Min SDK 24 / Target SDK 35
- No backend, no API calls, no cloud
