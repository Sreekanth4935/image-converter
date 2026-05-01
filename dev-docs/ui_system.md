# Image Converter: UI Design System

*Created: 2026-05-01*

---

## 1. Design Philosophy

### Clarity First

Every screen should instantly communicate its purpose. No clutter, no confusion.

### Design Pillars

| Pillar | Meaning |
|--------|---------|
| **Clarity** | Every element has a clear purpose |
| **Simple** | Minimal UI, maximum function |
| **Consistent** | Same visual language across all screens |
| **Accessible** | Works for all users including screen readers |

---

## 2. Color System

### Primary Color

- **Primary:** #FF6D00

### Surface Palette

| Token | Light Mode | Dark Mode |
|-------|-----------|-----------|
| background | #FAFAFA | #121212 |
| surface | #FFFFFF | #1E1E2E |
| onSurface | #1C1B1F | #E6E1E5 |

---

## 3. Typography

**Font:** System default (future: Inter or Roboto via Google Fonts)

| Style | Size | Weight | Usage |
|-------|------|--------|-------|
| headlineLarge | 28sp | Bold | Screen titles |
| titleLarge | 20sp | SemiBold | Section headers |
| bodyLarge | 16sp | Normal | Primary text |
| bodyMedium | 14sp | Normal | Secondary text |
| labelLarge | 14sp | Medium | Button labels |

---

## 4. Spacing

**Base Unit:** 4dp

| Token | Value | Usage |
|-------|-------|-------|
| sm | 8dp | Between related elements |
| md | 12dp | Between groups |
| lg | 16dp | Content padding |
| xl | 24dp | Section separators |

---

## 5. Shapes

| Token | Value | Usage |
|-------|-------|-------|
| small | 8dp | Chips, badges |
| medium | 12dp | Cards, buttons |
| large | 24dp | Bottom sheets |

---

## 6. Components (Initial)

### Home Screen
- Centered icon placeholder
- App title (headlineLarge)
- Description text (bodyLarge)
- Three action buttons: Start, Settings, Info

### Future Components
- Navigation bar
- Settings screen
- Feature-specific screens
