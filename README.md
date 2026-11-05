FairSplit

Split shared expenses fairly, know exactly who owes whom, and settle up with the fewest possible payments.

FairSplit is a Flutter app for groups of friends, flatmates and travel buddies. Add a shared expense once, choose how to split it, and the app keeps every member's balance up to date. When it's time to settle, it works out the smallest set of payments that clears all debts. Everything is stored locally with SQLite, so it works offline.

Features
Groups and members – create groups (Trip, Home, Friends, Family, College, …) and add members.
Flexible splitting – split an expense equally, by custom amounts, or by percentages, between any subset of the group.
Live share preview and validation – see each person's share while you type; the app blocks splits that don't add up (e.g. percentages not totalling 100%).
Real-time balances – per-member balances inside each group, plus an overall "you are owed / you owe" summary on the home screen.
Smart settle up – a debt-simplification algorithm suggests the minimum number of payments; record a payment with one tap.
Activity feed – a single timeline of expenses and settlements with search and type filters.
Expense details – tap any expense for the category, date, payer and exact split breakdown.
Spending insights – monthly totals for shared spending, what you paid, and your share.
Multi-currency display – INR, USD, EUR and GBP.
Light and dark themes – Material 3, generated from a single seed color.
Onboarding with sample data – start from scratch or explore with demo data (removable from the Profile screen).
Offline-first – all data persisted locally with SQLite.
Screens
Screen	What it does
Onboarding	Three-slide intro; start empty or load sample data
Home	Overall balance, group cards, recent activity
Groups	All groups with your balance in each
Group details	Spending total, member balances, expense list, add expense
Add expense	Title, amount, category, payer, participants, split method, notes
Settle up	Suggested payments, confirm and record
Activity	Searchable, filterable history
Create group	Name, category, description, initial members
Profile	Insights, currency, dark theme, sample-data controls
Tech stack
Area	Choice
Framework	Flutter (Dart, SDK ^3.12.2)
UI	Material 3 (ColorScheme.fromSeed)
State management	ChangeNotifier (FairSplitState)
Local storage	sqflite, with sqflite_common_ffi for Linux and Windows
Other packages	path, cupertino_icons
Lints and tests	flutter_lints, flutter_test
Project structure
lib/
├── main.dart                    # Entry point
├── app.dart                     # App shell, theme wiring, bootstrap
├── app_state.dart               # FairSplitState: data, SQLite persistence, business logic
├── models.dart                  # Group, member, expense, settlement models + balance/debt logic
├── database_factory*.dart       # Platform-specific SQLite setup
├── theme/
│   └── app_theme.dart           # Light/dark Material 3 themes
└── screens/
    └── screens.dart             # All app screens
test/
└── widget_test.dart             # Balance, split and settlement tests
How it works
Balances

All money is stored as integer cents to avoid floating-point errors. For each group:

the payer of an expense is credited the full amount,
every participant is debited their share,
a recorded settlement credits the payer and debits the receiver.

A positive balance means the member is owed money; a negative balance means they owe money.

Settle up (debt simplification)

Members with negative balances (debtors) are matched greedily against members with positive balances (creditors). Each step pays off as much as possible between one debtor and one creditor, which keeps the number of transfers small. Recording a suggested payment adds a settlement, and balances update immediately.

Storage

Data is saved in a local SQLite database (fairsplit.db) with groups, expenses, settlements and preferences tables. Records are stored as JSON payloads, and the app state loads them on startup.

Getting started
Prerequisites
Flutter SDK compatible with Dart ^3.12.2
An Android/iOS emulator or device, or a desktop target (macOS, Linux, Windows)
Run the app
bash
git clone <your-repo-url>
cd FairSplit-Flutter
flutter pub get
flutter run

To pick a specific target:

bash
flutter devices
flutter run -d <device-id>
Run the tests
bash
flutter test
Build
bash
flutter build apk          # Android
flutter build ios          # iOS (requires macOS)
flutter build windows      # Windows
flutter build linux        # Linux
Try it quickly
Launch the app and tap Explore with sample data on the last onboarding slide.
Open Goa Trip and tap Add expense.
Try the Equal, Unequal and % split modes and watch the share preview.
Tap the payments icon to see suggested settlements and record one.
Open Profile to change currency or switch to the dark theme.
Roadmap
Edit existing expenses
Receipt photo attachments
Export and share group summaries
Recurring expenses
Cloud sync across devices
Demo video

A full walkthrough of the app: onboarding, home, group details, adding an expense with every split mode, settle up, activity search, creating a group, currency change and dark theme.

FairSplit demo video

▶️ Watch the demo video (about 1 min 45 s)
