# AtomTask

> Break tasks down. Get things done.

AtomTask is an AI-powered productivity app that decomposes overwhelming tasks into micro-actions. Built with Flutter, it helps you regain focus through task deconstruction, priority matrices, focus timers, and habit tracking — all stored locally on your device.

## Features

- **AI Task Deconstruction** — Break any task into actionable micro-steps (powered by NVIDIA API)
- **Eisenhower Priority Matrix** — Sort tasks by urgent/important automatically
- **Focus Timer** — Pomodoro-style timer with Strict Mode (screen wake-lock, no interruptions)
- **Habit Tracking** — Track daily/weekly habits with streaks
- **AI Chat Assistant** — Ask your tasks questions, get suggestions
- **Weekly Analytics** — Review your productivity trends
- **Export & PDF** — Export tasks to PDF with progress bars and checkmarks
- **Local-First & Encrypted** — All data stored in encrypted Hive on-device
- **Premium via Gumroad** — $2.99/month or $14.99/year — unlock unlimited deconstructions, strict focus, AI chat, analytics, export
- **3 Languages** — English, French, Arabic (RTL support)

## Tech Stack

| Layer | Technology |
|---|---|
| Framework | Flutter 3.44+ / Dart 3.12+ |
| State Management | Riverpod (`flutter_riverpod`) |
| Local Database | Hive (encrypted, NoSQL) |
| Backend / Auth | Supabase (Auth, Edge Functions) |
| Payments | Gumroad License Verification |
| AI | NVIDIA API (task deconstruction) |
| Notifications | `flutter_local_notifications` |
| Localization | Custom `Strings` abstract class (EN, FR, AR) |
| Fonts | IBM Plex Sans + IBM Plex Sans Arabic |
| Icons | Font Awesome 6 |
| Charts | FL Chart |

## Architecture

Feature-first Clean Architecture under `lib/features/`, each module split into:

```
feature/
├── data/          # Models, repositories, services
├── domain/        # Business logic, use cases
└── presentation/  # Providers (Riverpod), screens, widgets
```

Shared code lives in `lib/core/` (theme, constants, utilities, widgets).

## Getting Started

### Prerequisites

- Flutter SDK 3.44+ (`stable` channel)
- A Supabase project (for auth + edge functions)
- Gumroad products (for premium licensing)

### Setup

```bash
# Clone
git clone https://github.com/nacer0s/AtomTask.git
cd AtomTask

# Install dependencies
flutter pub get

# Run (requires a connected device/emulator)
flutter run
```

### Supabase

1. Create a Supabase project at [supabase.com](https://supabase.com)
2. Enable Google OAuth + email/password auth
3. Run the migration at `supabase/migrations/20260506_rls_policies.sql`
4. Deploy the edge function:
   ```bash
   supabase functions deploy gumroad-verify
   ```
5. Set the Gumroad master key (optional):
   ```bash
   supabase secrets set GUMROAD_MASTER_KEY_HASH=<sha256-of-your-key>
   ```

### Environment

Update `lib/core/constants/app_constants.dart` with your Supabase URL and anon key, or set through `main.dart`.

## Gumroad Products

| Plan | Price | Product ID |
|---|---|---|
| Monthly Premium | $2.99/mo | `jnISYl7lJswlp97p-zmErg==` |
| Yearly Premium | $14.99/yr | `8ZSvECfPQaW2HzFTt5Qbnw==` |
| Support | $1+ PWYW | `tfMEcaRW_3LFRX07b2TsXQ==` |

Licenses are verified server-side via the `gumroad-verify` Supabase Edge Function, which checks against Gumroad's License Verification API and supports an optional lifetime master key.

## Website

The `site/` directory contains a standalone marketing page (`index.html`) with EN/FR/AR + RTL support, plus privacy and terms pages (English only). No build step — open in any browser.

## Localization

Strings are defined in `lib/l10n/`:
- `strings.dart` — abstract base class (all keys)
- `strings_en.dart` — English
- `strings_fr.dart` — French
- `strings_ar.dart` — Arabic

To add a new language: implement `Strings` and register it in `app_locale.dart`.

## Version

**v1.0.0-beta.1+1** — Public beta

## License

Proprietary — see [LICENSE](LICENSE) for details.

## Contact

- Email: nacer.eddine.dev@gmail.com
- GitHub: [nacer0s/AtomTask](https://github.com/nacer0s/AtomTask)
- LinkedIn: [nacer0s](https://linkedin.com/in/nacer0s)
