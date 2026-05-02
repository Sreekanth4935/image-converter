# Image Converter

Convert images between formats (JPG, PNG, WebP, BMP, HEIC) entirely offline.

## Current Status

**Initial setup complete** - App builds, installs, and launches successfully. No real features implemented yet.

## Tech Stack

| Component | Version |
|-----------|---------|
| Kotlin | 2.1.0 |
| AGP | 8.11.2 |
| Gradle | 9.0-milestone-1 |
| Jetpack Compose | BOM 2024.12.01 |
| Material 3 | via BOM |
| Min SDK | 24 |
| Target SDK | 35 |
| Architecture | MVVM-ready |

## Build

```bash
# Debug APK
./gradlew.bat assembleDebug

# Install on connected device
./gradlew.bat installDebug
```

## APK Output

```
app/build/outputs/apk/debug/app-debug.apk
```

## Package

```
com.sreekanth.imageconverter
```

## Project Structure

```
app/src/main/java/com/sreekanth/imageconverter/
  MainActivity.kt
  ui/
    AppRoot.kt
    HomeScreen.kt
    theme/
      Color.kt
      Theme.kt
      Type.kt
  viewmodel/
    MainViewModel.kt
```

## Notes

- **Offline-first**: All features will work without internet
- **No backend**: No server, no API calls, no cloud
- **No database**: Room will be added when needed for feature development
- **No ads**: Will be integrated in a future phase
- **No analytics**: Will be integrated in a future phase
- **No login**: App works fully offline, no account required

## Documentation

See the `dev-docs/` folder for:
- Product overview
- Feature list
- UI design system
- Execution plan
- Development history
- Testing log
- Test cases and QA tracking
- Play Store compliance notes
- Pre-release checklist
