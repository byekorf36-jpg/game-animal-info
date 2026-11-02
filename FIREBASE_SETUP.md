# Firebase setup — required for shared farm accounts

This build has the shared-workspace integration scaffolded, but it will not sync until it is connected to a Firebase project that you own.

## 1. Create the Firebase project
1. Open https://console.firebase.google.com/ and sign in with the Google account you want to use for the farm.
2. Create a project named `Game Animal Records`.
3. Add a **Web app** in Project settings. Copy its Firebase config.
4. In `www/index.html`, replace the placeholder values in `firebaseConfig` with the values from your Firebase web app. The Firebase web API key is a project identifier, not a service-account key. Never place a service-account JSON/private key in the app.

## 2. Turn on the services
1. Authentication → Sign-in method → enable **Email/Password**.
2. Firestore Database → Create database.
3. Storage → Get started.
4. In Firestore Rules, paste the contents of `firestore.rules` and publish.
5. In Storage Rules, paste the contents of `storage.rules` and publish.
6. Set billing/usage alerts in Google Cloud/Firebase so unexpected usage is visible. Check current Firebase Storage plan requirements and pricing in the Firebase console before enabling uploads.

## 3. Create the first farm
1. Build and install the app.
2. Create your login account.
3. Choose **Create new farm workspace**.
4. Share the displayed Farm ID and invitation code only with trusted staff/family members.
5. Each person creates their own login, enters the Farm ID and invitation code, and joins the same workspace.

The invitation code is a shared secret. Share it privately and rotate it if it is exposed. This starter version does not yet have a polished in-app member-management screen or invite revocation.

## 4. Build Android
This project uses Capacitor. You need Node.js LTS, Android Studio, Android SDK Platform 36 and a compatible JDK.

```bash
npm install
npx cap add android
npx cap sync android
npx cap open android
```

In Android Studio, wait for Gradle sync and generate a **signed Android App Bundle (.aab)**. Use the permanent application ID `za.co.gameanimalrecords.app`; do not change it after publishing. Keep your upload key safe.

## Important limitations before real farm use
- This is a working development build, not yet a reviewed production release.
- Firebase configuration and security rules must be installed and tested in your own Firebase project.
- Cloud updates sync when the device is connected. Local browser storage is still used as a cache; test offline edits and conflict handling carefully before relying on it.
- Photos upload to Firebase Storage; keep uploads below the configured 8 MB limit.
- The current invitation code is a simple shared-code mechanism. For a commercial/public release, improve this with owner-controlled invitations, revocation, audit history, role management and stronger account recovery.
- Add and test a complete privacy policy, data safety declarations, account deletion process and support contact before Play Store submission.
