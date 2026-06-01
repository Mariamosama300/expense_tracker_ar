# مصاريفي — Arabic Expense Tracker

A beautiful, fully Arabic/RTL Flutter app for tracking monthly expenses.

## Features (MVP)
- ✅ Add expenses (amount, category, note, date)
- ✅ 7 preset Arabic categories with icons & colors
- ✅ Dashboard: Today / This Week / This Month totals
- ✅ Expense history grouped by date, with swipe-to-delete
- ✅ Analytics: Pie chart + Bar chart (fl_chart)
- ✅ Spending breakdown with progress bars
- ✅ Fully offline — Hive local storage
- ✅ Full Arabic UI + RTL layout
- ✅ Animated splash screen
- ✅ Matches the provided Stitch design system (Financial Serenity)

## Design System
Colors, typography (Cairo font — Arabic variant of Manrope), and spacing all follow the uploaded `modern_personal_finance` design spec:
- Primary: `#006876` (teal)
- Secondary: `#FF5722` (orange-red, CTAs)
- Surface: `#F4FAFF` (soft off-white)
- Font: Cairo (Arabic geometric font, similar to Manrope)

## Setup

### Prerequisites
- Flutter SDK ≥ 3.0.0
- Dart SDK ≥ 3.0.0

### Install & Run

```bash
# Install dependencies
flutter pub get

# Run code generation for Hive adapters (already pre-generated)
# Only needed if you modify the Expense model:
flutter pub run build_runner build --delete-conflicting-outputs

# Run on device/emulator
flutter run

# Build APK
flutter build apk --release

# Build App Bundle (for Play Store)
flutter build appbundle --release
```

## Project Structure

```
lib/
├── main.dart                    # App entry, Hive init, Provider setup
├── models/
│   ├── expense.dart             # Expense data model (@HiveType)
│   └── expense.g.dart           # Generated Hive adapter (pre-generated)
├── providers/
│   └── expense_provider.dart    # ChangeNotifier: CRUD + computed totals
├── screens/
│   ├── splash_screen.dart       # Animated splash, opens Hive box
│   ├── dashboard_screen.dart    # Home tab + BottomNav + FAB
│   ├── add_expense_screen.dart  # Full-screen add form
│   ├── history_screen.dart      # Grouped list with date filters
│   └── analytics_screen.dart   # fl_chart pie + bar charts
├── utils/
│   ├── app_theme.dart           # Full MaterialTheme matching design system
│   └── constants.dart           # Categories, currency, box name
└── widgets/
    └── shared_widgets.dart      # ExpenseTile, SummaryCard, CategoryChip, etc.
```

## Post-MVP Roadmap
- [ ] Custom date range filter
- [ ] Monthly budget with progress indicator
- [ ] PIN / Fingerprint lock (local_auth)
- [ ] CSV export + WhatsApp share
- [ ] Custom categories (add/remove)

## Notes
- Currency is EGP (ج.م) — change `AppConstants.currencySymbol` for other currencies
- The Hive adapter (`expense.g.dart`) is pre-generated; only re-run `build_runner` if you modify the model
- `intl` locale `'ar'` is used for Arabic date formatting
