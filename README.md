# Virtual Camera — Android 16

A Kotlin Android application that lets the user choose a local video, preview it, seek, play/pause, and loop it continuously.

## Important limitation

This is an in-app video preview/player. A normal third-party APK cannot register itself as a system-wide camera device on Android 16. It will not appear as a camera source in other apps. That requires supported system-image / camera-provider integration, not an ordinary application.

## Requirements

- Android Studio (a current stable release with Android SDK 36 support)
- JDK 17
- Android SDK Platform 36
- Android Gradle Plugin 8.10.1 / Gradle 8.11.1

## Open and build

1. Extract this ZIP.
2. Open the `VirtualCameraAndroid16` folder in Android Studio.
3. Install Android SDK Platform 36 if prompted (Tools → SDK Manager → SDK Platforms).
4. Set Gradle JDK to JDK 17: Settings → Build, Execution, Deployment → Build Tools → Gradle.
5. Allow Gradle sync to finish. The first sync needs internet to download AndroidX/Media3 dependencies.
6. Connect an Android 16 phone with USB debugging enabled, or start an API 36 emulator.
7. Press Run to install and test.

## Build a debug APK

In Android Studio: Build → Build Bundle(s) / APK(s) → Build APK(s).

Output:
`app/build/outputs/apk/debug/app-debug.apk`

Or, from a terminal in the project root after configuring Gradle:
`gradle :app:assembleDebug`

## Build a signed release APK

1. Android Studio → Build → Generate Signed Bundle / APK.
2. Select APK.
3. Create a new keystore, or select an existing keystore you control.
4. Select the `release` build variant and finish.
5. Output is normally under `app/build/outputs/apk/release/`.

Keep your keystore and passwords private. If you lose the keystore, you may not be able to publish updates under the same signing identity.

## Use

1. Install and open Virtual Camera.
2. Tap **Choose video**.
3. Pick an MP4 or another Android-supported video from the system file picker.
4. Use Play/Pause and the seek bar. Loop is enabled by default and can be switched off.

The app uses Android's Storage Access Framework, so it does not request broad storage permissions.


## Build online without installing Android Studio

This project includes `.github/workflows/build-apk.yml` for GitHub Actions.

1. Create a GitHub repository and upload the *contents* of this project folder (including the hidden `.github` folder).
2. Open the repository's **Actions** tab.
3. Select **Build Virtual Camera APK** and choose **Run workflow** (or push to `main`).
4. Wait for the workflow to finish successfully.
5. Open the completed workflow run. Under **Artifacts**, download `VirtualCamera-debug-APK`.
6. Extract the downloaded artifact ZIP; it contains `app-debug.apk`. Transfer it to your Android 16 phone and install it. If Android asks, allow installation from that file manager/browser.

The GitHub Actions workflow builds a debug APK signed with the standard debug key. It is suitable for personal testing, not a Play Store release. GitHub account limits and usage quotas may apply.
