# **Vinyl Record Collection** 🎶

*A mobile app to manage your vinyl records collection and wishlist.*

Vinyl Record Collection Logo *(À remplacer par votre logo)*

---

## **📌 About the Project**

**Vinyl Record Collection** is a mobile application designed for vinyl enthusiasts to:

- **Track their vinyl collection** with detailed information.
- **Manage a wishlist** of records they want to acquire.
- **Organize, search, and filter** their collection effortlessly.

This app is built with **React Native** for cross-platform compatibility (iOS & Android) and uses **Firebase** for authentication and data storage.

---

## **✨ Features**

### **📀 Core Features (MVP)**

- **Add/Edit/Delete Vinyl Records**
  - Artist, album title, release year, label, genre, condition, estimated value, and personal notes.
  - Upload cover art images.
- **Browse Your Collection**
  - View records in a list or grid layout.
  - Sort by artist, year, genre, or condition.
- **Search & Filter**
  - Search by artist, album, or genre.
  - Filter by genre, condition, or year.
- **Wishlist Management**
  - Add records to your wishlist with priority levels (Low, Medium, High).
  - View and manage your wishlist separately.
- **User Accounts**
  - Sign up and log in with email/password.
  - Reset password functionality.
- **Data Export/Import**
  - Export your collection as **CSV** or **JSON**.
  - Import records from a **CSV/JSON** file.

### **🚀 Upcoming Features**

- **Barcode/QR Code Scanning** – Quickly add records by scanning.
- **Discogs & Spotify Integration** – Fetch metadata and preview tracks.
- **Cloud Sync** – Backup and sync your collection across devices.
- **Community Features** – Share collections, trade records, and discuss with other users.
- **Price Tracking** – Monitor the value of your collection over time.
- **Advanced Statistics** – Visualize your collection by genre, artist, or condition.

---

## **🛠️ Built With**


| Category     | Technologies                                                                           |
| ------------ | -------------------------------------------------------------------------------------- |
| **Frontend** | [React Native](https://reactnative.dev/) (TypeScript)                                  |
| **Backend**  | [Firebase](https://firebase.google.com/) (Authentication, Firestore)                   |
| **Database** | [Firebase Firestore](https://firebase.google.com/docs/firestore)                       |
| **Storage**  | [Firebase Storage](https://firebase.google.com/docs/storage) (for images)              |
| **UI/UX**    | [React Navigation](https://reactnavigation.org/), [NativeBase](https://nativebase.io/) |
| **Testing**  | [Jest](https://jestjs.io/), [Detox](https://github.com/wix/Detox)                      |


---

## **📥 Getting Started**

### **Prerequisites**

- **Node.js** (v16 or later) – [Download Node.js](https://nodejs.org/)
- **npm** or **yarn** – [Install npm](https://www.npmjs.com/get-npm) / [Install yarn](https://yarnpkg.com/getting-started)
- **React Native CLI** – Install globally:
  ```bash
  npm install -g react-native-cli
  ```
- **Android Studio** (for Android) / **Xcode** (for iOS)
- **Firebase Project** – [Set up Firebase](https://firebase.google.com/docs/web/setup)

### **Installation**

1. **Clone the repository:**
  ```bash
   git clone https://github.com/your-username/vinyl-record-collection.git
   cd vinyl-record-collection
  ```
2. **Install dependencies:**
  ```bash
   npm install
   # or
   yarn install
  ```
3. **Set up Firebase:**
  - Create a Firebase project at [Firebase Console](https://console.firebase.google.com/).
  - Enable **Authentication (Email/Password)** and **Firestore Database**.
  - Download your `google-services.json` (Android) and `GoogleService-Info.plist` (iOS) files.
  - Place them in:
    - Android: `android/app/google-services.json`
    - iOS: `ios/GoogleService-Info.plist`
4. **Configure environment variables:**
  Create a `.env` file in the root directory and add your Firebase config:
5. **Run the app:**
  - **Android:**
  - **iOS:**
    ```bash
    npx react-native run-ios
    ```

---

## **📂 Project Structure**

```
vinyl-record-collection/
├── android/          # Android native code
├── ios/              # iOS native code
├── src/
│   ├── assets/       # Images, fonts, etc.
│   ├── components/   # Reusable UI components
│   ├── screens/      # App screens
│   ├── navigation/   # Navigation setup
│   ├── services/     # Firebase & API services
│   ├── utils/        # Helper functions
│   ├── types/        # TypeScript types
│   └── App.tsx       # Main app component
├── .env              # Environment variables
├── package.json      # Project dependencies
└── README.md         # This file
```

---

## **🤝 Contributing**

Contributions are welcome! Here’s how you can help:

1. **Fork the repository** and create a new branch (`git checkout -b feature/your-feature`).
2. **Commit your changes** (`git commit -m "Add your feature"`).
3. **Push to the branch** (`git push origin feature/your-feature`).
4. **Open a Pull Request** with a clear description of your changes.

### **Contribution Guidelines**

- Follow the existing code style.
- Add tests for new features.
- Update the documentation if needed.

---

## **🐛 Reporting Issues**

If you find a bug or have a feature request, please [open an issue](https://github.com/your-username/vinyl-record-collection/issues) and include:

- A clear description of the issue.
- Steps to reproduce (if applicable).
- Screenshots (if helpful).

---

## **📜 License**

This project is licensed under the **MIT License** – see the [LICENSE](LICENSE) file for details.

---

**💬 Contact**  
For questions or feedback, reach out to:

- **Email:** [your-email@example.com](mailto:your-email@example.com)
- **GitHub:** [@your-username](https://github.com/your-username)

---

*Happy collecting! 🎵*
