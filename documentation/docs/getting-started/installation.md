# Installation

Ukkin is an experimental Flutter project. Today it is built from source, not distributed as a packaged release.

## Requirements

### Toolchain
- Flutter SDK `3.1.5+` (matches `environment.sdk` in `pubspec.yaml`)
- Dart `>=3.1.5 <4.0.0`
- Git
- A sibling checkout of [`agentlib`](https://github.com/neul-labs/agentlib) at `../agentlib` (the `pubspec.yaml` declares `agentlib: path: ../agentlib`)

### Android
- Android API level 21+ (Android 5.0)
- `ANDROID_HOME` exported in your shell
- A device or emulator with the Accessibility Service permission available (required for screen automation)

### iOS
- iOS 11.0 or higher
- Xcode with iOS toolchain
- `Info.plist` permissions configured for the integrations you intend to use

## Clone and Run

```bash
git clone https://github.com/neul-labs/ukkin.git
cd ukkin
flutter pub get
flutter run
```

`flutter pub get` will resolve `agentlib` from the sibling `../agentlib` directory. If you do not have it, clone it first:

```bash
git clone https://github.com/neul-labs/agentlib.git ../agentlib
```

## First Launch

On first launch the app:

1. Initializes AgentLib via `QuickStart.initialize(mode: QuickStartMode.development, databaseName: 'ukkin')`
2. Creates a default mobile assistant via `QuickStart.createMobileAssistant(...)`
3. Prompts for any platform permissions required by the agents you create

The on-device model warm-up may take 30-60 seconds on first launch.

## Verify Installation

1. Launch the app on a device or emulator
2. The chat interface opens by default
3. Send a test message and confirm a response
4. Switch to the **Agents** tab to view the dashboard

## Next Steps

- [Quick Start](quick-start.md) - Create your first agent
- [Permissions](permissions.md) - Enable the Accessibility Service and other required permissions
