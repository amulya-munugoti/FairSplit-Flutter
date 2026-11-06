
<div align="center">

# 💸 FairSplit

### Split fairly. Track clearly. Settle simply.

**A smart, offline-first group expense sharing app built with Flutter.**

![Flutter](https://img.shields.io/badge/Flutter-02569B?style=for-the-badge&logo=flutter&logoColor=white)
![Dart](https://img.shields.io/badge/Dart-0175C2?style=for-the-badge&logo=dart&logoColor=white)
![Material 3](https://img.shields.io/badge/Material%203-6750A4?style=for-the-badge&logo=materialdesign&logoColor=white)
![SQLite](https://img.shields.io/badge/SQLite-003B57?style=for-the-badge&logo=sqlite&logoColor=white)

**Friends • Flatmates • Families • Travel Groups**

</div>

---

## 🌈 About FairSplit

Managing shared expenses shouldn't be confusing!

**FairSplit** is a Flutter-based expense-sharing application designed for friends, flatmates, families, college groups, and travel buddies.

It allows users to record shared expenses, divide costs using flexible methods, track who owes whom, and settle debts with fewer payments.

With SQLite local storage, the application works offline and keeps data saved on the device.

---

## ✨ Features

### 👥 1. Groups and Members
- Create groups for trips, home, friends, family, and college.
- Add and manage group members.
- Track individual balances within each group.

### 💰 2. Flexible Expense Splitting
- **Equal Split:** Divide expenses equally.
- **Unequal Split:** Assign custom amounts.
- **Percentage Split:** Divide expenses using percentages.
- Select any subset of group members.

### 📊 3. Live Split Preview and Validation
- Preview each person's share while entering details.
- Automatically validate split amounts.
- Prevent invalid splits that do not add up to the total.

### ⚖️ 4. Real-Time Balance Tracking
- View how much each member owes or is owed.
- Track balances within individual groups.
- View overall amounts owed and payable on the home screen.

### 🤝 5. Smart Settle Up
- Automatically simplify debts between group members.
- Suggest a small number of payments to settle balances.
- Record suggested payments with one tap.
- Update balances immediately after settlement.

### 🕒 6. Activity Feed
- View expenses and settlements in one timeline.
- Search transaction history.
- Filter activities by transaction type.

### 🧾 7. Expense Details
- View expense title, amount, category, date, and payer.
- Check the exact split breakdown.

### 💡 8. Spending Insights
- View monthly shared spending totals.
- Track how much you paid.
- Compare payments with your actual share.

### 🌍 9. Multi-Currency Support
- INR – Indian Rupee
- USD – US Dollar
- EUR – Euro
- GBP – British Pound

### 🎨 10. Themes and Onboarding
- Light and dark themes.
- Material 3 design.
- Three-slide onboarding experience.
- Start with empty data or explore sample data.
- Remove sample data from the Profile screen.

### 📱 11. Offline-First Storage
- Uses SQLite for local data persistence.
- Stores groups, expenses, settlements, and preferences.
- Loads saved data when the app starts.
- Works without an internet connection.

---

## 📱 Application Screens

| Screen | Description |
|---|---|
| 🚀 Onboarding | Introduction and sample data option |
| 🏠 Home | Overall balance, groups, and recent activity |
| 👥 Groups | All groups and individual balances |
| 📂 Group Details | Spending, balances, and expenses |
| ➕ Add Expense | Add expenses and select split methods |
| 🤝 Settle Up | Suggested payments and settlements |
| 🕒 Activity | Searchable transaction history |
| 📝 Create Group | Create groups and add members |
| ⚙️ Profile | Insights, currency, themes, and settings |

---

## 🧠 How It Works

### Balance Calculation

FairSplit calculates each member's balance for a group.

- The person who pays an expense is credited with the full amount.
- Each participant is debited by their assigned share.
- When a settlement is recorded, the payer is credited and the receiver is debited.

**Balance interpretation:**

| Balance | Meaning |
|---|---|
| 🟢 Positive | Member is owed money |
| 🔴 Negative | Member owes money |
| ⚪ Zero | No outstanding balance |

**Money accuracy:** All monetary values are stored as integer cents to avoid floating-point calculation errors.

### Smart Debt Simplification

FairSplit uses a greedy debt-simplification algorithm.

1. Identify members with negative balances (debtors).
2. Identify members with positive balances (creditors).
3. Match one debtor with one creditor.
4. Suggest a payment equal to the smaller outstanding balance.
5. Repeat until all balances are settled.

This reduces the number of payments required to clear group debts.

### Database Storage

The application uses a local SQLite database named `fairsplit.db`.

| Table | Stores |
|---|---|
| `groups` | Group information |
| `expenses` | Shared expense records |
| `settlements` | Recorded payments |
| `preferences` | App preferences |

Records are stored as JSON payloads and loaded when the application starts.

---

## 🛠️ Tech Stack

![Flutter](https://img.shields.io/badge/Flutter-Framework-02569B?logo=flutter)
![Dart](https://img.shields.io/badge/Dart-Language-0175C2?logo=dart)
![SQLite](https://img.shields.io/badge/SQLite-Database-003B57?logo=sqlite)

| Area | Technology |
|---|---|
| Framework | Flutter |
| Programming Language | Dart |
| UI Design | Material 3 |
| State Management | ChangeNotifier (`FairSplitState`) |
| Local Database | sqflite |
| Desktop Database | sqflite_common_ffi |
| Path Handling | path |
| Icons | cupertino_icons |
| Testing | flutter_test |
| Code Quality | flutter_lints |

---

## 📂 Project Structure

```text
lib/
├── main.dart
├── app.dart
├── app_state.dart
├── models.dart
├── database_factory*.dart
├── theme/
│   └── app_theme.dart
└── screens/
    └── screens.dart

test/
└── widget_test.dart
```

### Main Components

- `main.dart` – Application entry point.
- `app.dart` – App initialization and theme configuration.
- `app_state.dart` – State management, SQLite persistence, and business logic.
- `models.dart` – Group, member, expense, and settlement models.
- `database_factory*.dart` – Platform-specific SQLite setup.
- `app_theme.dart` – Light and dark themes.
- `screens.dart` – Application screens.
- `widget_test.dart` – Widget and application tests.

---

## 🚀 Getting Started

### Prerequisites

- Flutter SDK compatible with Dart `^3.12.2`.
- Android Studio or VS Code.
- Android/iOS emulator or physical device.
- Desktop platform support (optional).

### 1. Clone the Repository

```bash
git clone <YOUR_GITHUB_REPOSITORY_URL>
```

### 2. Navigate to Project Folder

```bash
cd FairSplit-Flutter
```

### 3. Install Dependencies

```bash
flutter pub get
```

### 4. Check Flutter Setup

```bash
flutter doctor
```

### 5. Run the Application

```bash
flutter run
```

### Select a Device

```bash
flutter devices
flutter run -d <device_id>
```

---

## 🧪 Testing

Run the Flutter tests:

```bash
flutter test
```

---

## 📦 Build the Application

**Android**
```bash
flutter build apk
```

**iOS (requires macOS)**
```bash
flutter build ios
```

**Windows**
```bash
flutter build windows
```

**Linux**
```bash
flutter build linux
```

---

## 🎮 Try It Out

Explore FairSplit using sample data:

1. Launch the application.
2. Select **Explore with sample data** on the last onboarding slide.
3. Open the **Goa Trip** group.
4. Tap **Add Expense**.
5. Try Equal, Unequal, and Percentage split modes.
6. Check the live share preview.
7. Open Settle Up to view suggested payments.
8. Record a payment and check updated balances.
9. Open Profile to change currency or switch to dark mode.

You can remove sample data from the Profile screen.

---

## 🎥 Demo

**FairSplit – Application Walkthrough**

The demo covers onboarding, home screen, group details, adding expenses, different split methods, settle up, activity search, group creation, currency selection, and dark theme.

▶️ **[Watch the FairSplit Demo Video](<https://github.com/user-attachments/assets/e2211283-19d4-4187-9a3f-71536c8bfd05>)**

---

## 🔮 Future Enhancements

- [ ] Edit existing expenses.
- [ ] Receipt photo attachments.
- [ ] Export and share group summaries.
- [ ] Recurring expenses.
- [ ] Cloud synchronization across devices.

---

## 🤝 Contributing

Suggestions and contributions are welcome!

1. Fork the repository.
2. Create a feature branch.
3. Make your changes.
4. Test using `flutter test`.
5. Submit a pull request.

---

## 📄 License

Add your preferred license before distributing the project.

---

<div align="center">

### 💚 FairSplit

**Shared expenses, made simple.**

*Split fairly • Track clearly • Settle easily*

</div>

https://github.com/user-attachments/assets/e2211283-19d4-4187-9a3f-71536c8bfd05





