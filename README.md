# Ukkin

**Create AI agents on your phone that automate your daily tasks.**

**[Website](https://ukkin.neullabs.com)** · **[Documentation](https://docs.neullabs.com/ukkin)** · **[GitHub](https://github.com/neul-labs/ukkin)** · **[Neul Labs](https://www.neullabs.com)**

Your phone is always on, always with you. Ukkin lets you build personal AI agents that work in the background - checking prices, monitoring social media, triaging emails, or running any workflow you describe in plain English. Ukkin is an open-source Flutter app from [Neul Labs](https://www.neullabs.com).

## Why Ukkin?

Existing mobile automation stacks either lock you into a vendor (Apple
Shortcuts, Google Assistant routines) or refuse to actually take action
("AI concierge" apps that only summarise). Ukkin exists for the third
category: agents that do the task and show you what they did.

Upstream pain points that motivated this:
- Apple [Shortcuts #3800](https://github.com/shortcuts/all-shortcuts-site/issues) — vendor lock-in, no cross-app data flow without manual plumbing
- Google [Assistant routines #2210](https://issuetracker.google.com/issues/2210) — closed model, no on-device LLM, no agentic tool use
- IFTTT / Zapier mobile — requires a cloud round trip and a paid plan per active workflow

| Capability | Ukkin | Apple Shortcuts | Google Assistant | IFTTT | Zapier |
|---|---|---|---|---|---|
| On-device execution | ✅ | ✅ | ❌ | ❌ | ❌ |
| Natural-language agent build | ✅ | ❌ | ❌ | ❌ | ❌ |
| Cross-app data flow | ✅ | ⚠️ manual | ❌ | ⚠️ web-only | ⚠️ web-only |
| No subscription required | ✅ | ✅ | ✅ | ❌ | ❌ |
| Open source | ✅ | ❌ | ❌ | ❌ | ❌ |
| Works offline | ✅ | ✅ | ⚠️ partial | ❌ | ❌ |

## The Idea

Tell Ukkin what you want automated:

> "Watch for price drops on items in my Amazon wishlist and notify me"

> "Every morning, summarize my unread emails and flag anything urgent"

> "Monitor my Instagram mentions and draft responses for review"

Ukkin converts your description into a working agent that runs on your device, respecting battery life and network conditions.

## Key Features

**Conversational Agent Builder**
Describe what you want in natural language. Ukkin extracts the workflow, shows you the steps, and creates the agent.

**Device-Aware Scheduling**
Agents run when conditions are right - on WiFi, while charging, at specific times, or when the app you need is available.

**Deep App Integration**
Automate across WhatsApp, Email, Instagram, Amazon, Calendar, and more. Agents can read screens, tap buttons, and move data between apps.

**On-Device Processing**
All AI runs locally. Your data never leaves your phone.

## Agent Types

- **Social Media**: Monitor mentions, auto-engage, track followers
- **Communication**: Email triage, message drafting, contact management
- **Shopping**: Price watching, deal alerts, wishlist monitoring
- **Custom**: Build anything from a conversation

## Getting Started

```bash
git clone https://github.com/neul-labs/ukkin.git
cd ukkin
flutter pub get
flutter run
```

Requires Flutter 3.1.5+, Android API 21+ or iOS 11+.

## Architecture

Ukkin uses [AgentLib](../agentlib/), a standalone SDK for mobile AI agents. The core abstractions:

- `RepetitiveTaskAgent`: Background tasks that run on schedule
- `TaskScheduler`: Coordinates agents based on device state
- `AppPluginSystem`: Modular integrations for each app
- `RealAutomation`: Accessibility service bridge for screen interaction

## Current Status

**Working:**
- Android Accessibility Service for screen automation
- Real screen reading and element finding
- Tap, type, scroll, swipe operations
- App launching and navigation
- Price extraction and tracking with history
- Instagram post/follower monitoring
- Email classification and organization

**Requires:**
- Accessibility service enabled in Android Settings
- Target apps installed on device

## Roadmap

### Phase 1: Core Automation (Current)
- Screen scraping via accessibility service
- Basic agents: Instagram, Email, Price watching
- Local storage for tracking data

### Phase 2: Intelligence
- On-device LLM for natural language understanding
- Smarter element matching using context
- Agent composition (chain multiple agents)

### Phase 3: Advanced Agents
- Calendar integration and scheduling
- Cross-app workflows (e.g., email → calendar → reminder)
- Voice-triggered agent creation
- Notification-based triggers

### Phase 4: Platform Expansion
- iOS automation support
- Desktop companion app
- Agent marketplace/sharing

## Contributing

This is an experimental project exploring on-device AI agents. Contributions welcome for:
- New agent implementations
- App handler improvements
- Accessibility service enhancements
- iOS support

## License

MIT

---

## Part of the Neul Labs toolchain

Ukkin is part of the OpenClaw cluster at [Neul Labs](https://www.neullabs.com):

| Project | Description |
|---------|-------------|
| [openclaw-rs](https://github.com/neul-labs/openclaw-rs) | A community Rust implementation of OpenClaw. |
| [openclawMU](https://github.com/neul-labs/openclawMU) | Multi-tenant fork of OpenClaw with strict data isolation. |
| [openclawOS](https://github.com/neul-labs/openclawOS) | OS-like architecture for self-hosted AI assistants. |

Explore all projects at [neullabs.com](https://www.neullabs.com).