---
name: build-capacitor-app
description: Use when building a Capacitor mobile app. Always uses web → native wrapper, plugins, native bridging and follows platform conventions.
---

# Build a Capacitor App

Production-grade Capacitor app.

## Setup
- Project initialization
- Dependencies
- Environment configuration
- Build configuration (dev, staging, release)

## Project Structure
```
src/
├── components/
├── screens/
├── navigation/
├── state/
├── services/
├── utils/
└── types/
```

## Navigation
- Stack navigation
- Tab navigation
- Drawer navigation
- Deep linking
- Modal presentation

## State Management
- Local state
- Global state
- Server state (React Query / SWR / equivalent)
- Form state

## Platform Conventions
- iOS Human Interface Guidelines
- Android Material Design
- Platform-specific navigation patterns
- Platform-specific UI components
- Platform-specific permissions

## Performance
- List virtualization (FlatList / LazyColumn)
- Image caching
- Avoid unnecessary re-renders
- Minimize JS bridge traffic (React Native)
- Use native modules for heavy work

## Offline Support
- Local persistence (AsyncStorage / SQLite / Realm)
- Sync strategy
- Conflict resolution

## Push Notifications
- Permission request
- Token registration
- Notification handling (foreground, background, killed)
- Rich notifications

## Authentication
- OAuth via system browser (not webview)
- Biometric auth
- Secure token storage (Keychain / Keystore)
- Auto-refresh

## Permissions
- Camera, photos, location, notifications
- Just-in-time requests
- Graceful denial handling

## App Store / Play Store
- Metadata (title, description, screenshots, icon)
- Privacy policy
- App review guidelines compliance
- Release management

## Analytics & Crash Reporting
- Analytics events
- Crash reporting (Sentry, Crashlytics)
- Performance monitoring

## Forbidden Patterns
- Webview-based auth (use system browser)
- Storing tokens in plain storage
- Not handling offline state
- Ignoring platform conventions
- Bundling secrets in the app

## Output Format
1. Project structure
2. Key screens / flows
3. State management approach
4. Native integrations
5. Build & deploy setup

