# Ai all repositry — Android and web artifacts

This repository builds two separate artifacts with GitHub Actions:

- **Native Android APK wrapper** at `android-native/`. It opens the deployed FRESHAI app at the Cloud Run URL in an Android WebView, enables JavaScript and DOM storage needed by web apps, accepts cookies, keeps HTTPS-only traffic, supports Android back navigation, and sends links to other hosts to the browser.
- **Existing web artifact** built from the prepared `ai-trading-source.zip` source bundle.

## Cloud Run app URL

`https://ais-dev-clmt6hxc2m66glvczovkmx-597262149244.asia-east1.run.app/`

The Android app is a native Android container around the existing website, not a rewrite of the trading frontend or backend. Its market data, authentication, and trading actions still depend on the deployed website and its APIs. A successful APK build does not by itself verify broker authentication, live data, paper trading, or Cloud Run security-cookie behavior.

## Build locally

Requirements: JDK 17, Android SDK (API 35 platform/build tools), and Gradle 8.9.

```bash
cd android-native
gradle --no-daemon assembleDebug
gradle --no-daemon assembleRelease
```

Release output:
`android-native/app/build/outputs/apk/release/app-release-unsigned.apk`

The CI artifact is unsigned for distribution. For public distribution, configure a signing key through GitHub Actions secrets and sign the release APK; never commit signing keys or broker/API secrets.

## Build and download from GitHub

1. Open **Actions → Build AI-All Artifact**.
2. Open the latest run on the `main` branch and wait until the Android and web jobs finish.
3. Under **Artifacts**, download `ai-all-native-android-apk` for the APK, or `ai-all-web-artifact` for the website files.
4. Android artifacts are retained for 14 days.

Workflow: `.github/workflows/build-artifact.yml`.
