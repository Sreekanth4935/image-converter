# Image Converter: Pre-Release Checklist

*Created: 2026-05-01*
*Last updated: 2026-05-01*

> Read this BEFORE every Play Store upload.

---

## 1. Build Verification

- [x] Debug build successful (assembleDebug)
- [ ] Release build successful (assembleRelease)
- [ ] isMinifyEnabled = true for release
- [ ] isShrinkResources = true for release
- [ ] Production keystore configured (not debug.keystore)
- [ ] Version code incremented
- [ ] Version name updated

## 2. App Launch Verification

- [x] App launches without crash
- [x] Home screen renders correctly
- [x] All buttons are clickable without crash
- [x] Edge-to-edge display works correctly
- [x] Dark mode works correctly
- [x] App icon displays correctly in launcher

## 3. Package Verification

- [x] Package name: com.sreekanth.imageconverter
- [x] App name: Image Converter
- [x] No placeholder or debug text visible

## 4. UI Verification

- [x] Home screen accessible and functional
- [ ] All screens accessible (only Home exists currently)
- [ ] No broken layouts on different screen sizes
- [x] Text is readable in both light and dark mode
- [x] Touch targets are at least 48dp

## 5. Privacy and Compliance

- [x] No unnecessary permissions in manifest
- [ ] Privacy policy linked
- [ ] Data Safety form completed
- [ ] No misleading features or claims

## 6. Play Store Assets

- [ ] App icon finalized
- [ ] Screenshots taken from real device
- [ ] Description written (only shipped features)
- [ ] Release notes written

## 7. Initial Setup Check (Day 1)

- [x] Project created
- [x] Package name verified: com.sreekanth.imageconverter
- [x] Basic UI renders correctly
- [x] Launcher icon updated from placeholder
- [x] Debug build verified on device
- [x] No crash on launch confirmed

---

## Build Commands

```bash
# Debug build
./gradlew.bat assembleDebug

# Install on device
./gradlew.bat installDebug

# Release build (after keystore setup)
./gradlew.bat bundleRelease
```

## APK Output Path

```
app/build/outputs/apk/debug/app-debug.apk
```
