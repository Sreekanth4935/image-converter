# Image Converter: Play Store Compliance

*Created: 2026-05-01*

This document tracks Play Store policy compliance for Image Converter.

---

## 1. Core Compliance Principles

- **Offline-first**: All core features work without internet
- **No account required**: Zero login, zero signup, zero user data collection
- **No backend**: No server calls, no cloud storage, no API dependencies
- **No unnecessary permissions**: Only request permissions needed for core features
- **Privacy-first**: No data leaves the device in the initial version

## 2. Permissions Strategy

### Initial Version (No Permissions Required)

The initial version has no special permissions. Future versions will add only what is needed:

| Permission | When Needed | Justification |
|-----------|------------|---------------|
| POST_NOTIFICATIONS | When reminders added | Required for alarm/reminder features |
| CAMERA | If camera feature added | Only for specific tools requiring camera |
| READ_MEDIA_IMAGES | If image access needed | Scoped to specific user-initiated actions |

### Rules
- Never request MANAGE_EXTERNAL_STORAGE unless absolutely necessary
- Always explain why a permission is needed before requesting
- Provide graceful fallback when permission is denied

## 3. Content Policy

- No misleading claims in listing or UI
- No broken features shown as if they work
- No third-party branding misuse
- App description matches actual functionality

## 4. Ad Policy (Future)

- No ad before the user sees real value
- No interstitial on first open
- No ad covering primary content
- Rate-limited interstitials (max 1 per 3 minutes)
- Banner ads only on safe surfaces

## 5. Data Safety

- **Data collected**: None in initial version
- **Data shared**: None
- **Encryption**: Not applicable (no data transmission)
- **Deletion**: All data is local, user can uninstall to remove

## 6. Store Listing Rules

- Screenshots must match actual app
- Description must only mention shipped features
- No "Coming Soon" claims for major features
- Category must be accurate: Photography / Tools
