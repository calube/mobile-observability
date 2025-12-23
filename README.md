# Mobile Observability Plugin for Claude Code

[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE)
[![Claude Code](https://img.shields.io/badge/Claude%20Code-Plugin-blueviolet)](https://claude.ai/code)
[![Platform](https://img.shields.io/badge/Platform-iOS%20%7C%20Android%20%7C%20React%20Native%20%7C%20Flutter-green)](https://github.com/calube/mobile-observability)

**Teach Claude how to instrument mobile apps correctly.**

This plugin gives Claude expert knowledge in mobile observability — what to instrument, what context to attach, and what mistakes to avoid. The result: telemetry that's useful when something breaks.

## The Problem

Most mobile teams instrument poorly:

| Problem | Symptom |
|---------|---------|
| **Instrument too little** | Can't debug production issues |
| **Instrument too much** | Noise, cost, battery drain |
| **Wrong context** | Errors without enough data to act on |

This plugin teaches Claude **User-Focused Observability** — linking user intentions with app telemetry so you can answer: *"Why did users fail to complete their goal?"*

## Installation

Requires [Claude Code](https://claude.ai/code).

**From the marketplace (recommended):**

```bash
claude plugin add calube/mobile-observability
```

**From source:**

```bash
git clone https://github.com/calube/mobile-observability.git
cd mobile-observability
claude plugins install .
```

## Workflows

### 1. Plan Instrumentation for a Codebase

```
/instrument ios
```

Claude analyzes your project and generates a prioritized instrumentation plan.

### 2. Audit Existing Telemetry

```
/audit features/onboarding
```

Find gaps in a specific module's instrumentation.

### 3. Review Before Merging

```
Launch the instrumentation-reviewer agent on features/checkout
```

Check for anti-patterns, missing context, and naming issues before code ships.

### 4. Ask Questions

Skills activate automatically:

- *"How should I instrument this payment flow?"*
- *"What context should I attach to crashes?"*
- *"Set up session replay with Sentry"*

## What's Included

### Commands

| Command | Description |
|---------|-------------|
| `/instrument [platform]` | Generate instrumentation plan |
| `/audit [path]` | Scan for instrumentation gaps |

### Agents

| Agent | Use Case |
|-------|----------|
| `codebase-analyzer` | Explore architecture, find instrumentation opportunities |
| `instrumentation-reviewer` | Review code for anti-patterns and missing context |

### Skills

8 skills for common instrumentation tasks:

| Skill | Use When |
|-------|----------|
| `instrumentation-planning` | Deciding what to measure |
| `crash-instrumentation` | Setting up crash capture with context |
| `session-replay` | Configuring visual debugging |
| `interaction-latency` | Tracking button/tap response time |
| `navigation-latency` | Measuring screen load and TTI |
| `network-tracing` | Instrumenting API calls |
| `user-journey-tracking` | Tracking funnels and conversions |
| `symbolication-setup` | Configuring dSYM, ProGuard, source maps |

### Anti-Pattern Hooks

Warnings when editing `.swift`, `.kt`, `.ts`, or `.dart` files:

- **High cardinality tags** — User IDs as metric labels explode costs
- **Unbounded payloads** — Attaching entire state objects
- **PII in telemetry** — Logging emails, phones, or user input
- **Missing context** — Events without screen/session/job

### Reference Library

25+ guides covering:

**Methodology**
- User-Focused Observability — intent, outcomes, friction signals
- Jobs-to-be-Done — instrument what matters for user goals

**Platforms**
- iOS (Swift/SwiftUI, MetricKit, os_signpost)
- Android (Kotlin/Compose, Perfetto, ANR)
- React Native (Expo, Hermes, source maps)
- Flutter (Dart error handling, native bridges, widget lifecycle)

**Topics**
- Crash capture and breadcrumbs
- Performance (app start, screen load, network)
- Business logic (decisions, state machines, background jobs)
- Feature flags (evaluation events, what not to do)
- Session replay and privacy

**Vendors**
- Sentry, Datadog, Embrace, Bugsnag, Bitdrift, Firebase, OpenTelemetry, Measure.sh

**Templates**
- Screen load tracking
- Error boundaries
- Breadcrumb managers
- Navigation tracking

## Plugin Structure

```
mobile-observability/
├── commands/       # /instrument, /audit
├── agents/         # codebase-analyzer, instrumentation-reviewer
├── skills/         # 8 instrumentation skills
├── hooks/          # Anti-pattern detection
└── references/     # 20+ guides, templates, vendor docs
```

## Who This Is For

- Mobile developers adding observability to iOS, Android, React Native, or Flutter
- Teams setting up Sentry, Datadog, Embrace, Bugsnag, Bitdrift, Firebase, or OpenTelemetry
- Anyone who wants actionable telemetry, not just data

## Contributing

Contributions welcome:

- Additional vendor guides (New Relic, AppDynamics, Instabug)
- Platform-specific examples
- Bug reports and feedback

## License

MIT — see [LICENSE](LICENSE)

---

Built with [Claude Code](https://claude.ai/code).
