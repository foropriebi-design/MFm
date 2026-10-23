# My Finance Manager — Android project

This project wraps the finance dashboard in an Android WebView app.

## Build an APK without installing Android Studio locally

The included GitHub Actions workflow (`.github/workflows/build-apk.yml`) can build the APK in GitHub's hosted runner.

1. Sign in to GitHub and create a **private** repository.
2. Upload the contents of this project folder to the repository (not the ZIP file itself).
3. Open the repository's **Actions** tab and select **Build Android APK**.
4. Choose **Run workflow** and run it.
5. When the run succeeds, open that workflow run, scroll to **Artifacts**, and download `My-Finance-Manager-APK`.
6. Extract the downloaded artifact to get `app-debug.apk`, then transfer it to your Android phone and install it. Android may ask you to allow installation from that source.

You can also open the folder in Android Studio and use **Build → Build Bundle(s) / APK(s) → Build APK(s)**.

## Included behavior

- Single password-only screen (no email registration page).
- Financial transactions stored in the app's WebView local storage on the device.
- App locks when Android reports no validated internet connection.
- Green-and-black dashboard.
- JavaScript and DOM storage enabled for the bundled app page.
- Android backup disabled in the manifest.

## Important security notes

- Transaction data is stored locally and is **not encrypted at rest** in this version. The password gate controls app access but does not encrypt the underlying local-storage database.
- The app does not intentionally upload transaction records. It checks Android's validated internet status to enforce the online-required rule.
- Local app data can be lost if the app is uninstalled or its storage is cleared. Export backups regularly if the app offers an export option.
- The generated `app-debug.apk` is a debug build for personal testing, not a Play Store release. A release build should be signed with a private release key.
