# AI-All — Build Artifact

This repository is wired to build a downloadable artifact from `ai-trading-source.zip`.

## Add the source bundle

The repository was empty when this bootstrap was created. Download the prepared source ZIP from this ChatGPT conversation, rename it exactly to `ai-trading-source.zip`, then use **Add file → Upload files** on this repository's `main` branch and commit it.

That push starts **Build AI-All Artifact** automatically.

## What the workflow builds

- If the source ZIP contains `flutter_app/pubspec.yaml`, it builds and uploads a release Android APK.
- Otherwise, if it contains `package.json` and `vendor/TradingGoose/package.json`, it builds the Vite web app and uploads the web `dist` folder.

The source bundle supplied with this request does **not** include `flutter_app/`, so its current build path is the web artifact, not APK. Do not treat the web artifact as an APK.

## Run / download

After committing `ai-trading-source.zip`, open **Actions → Build AI-All Artifact**, wait for the run to finish, then download the artifact from that run's **Artifacts** section.

Builds require network access to install npm/Flutter dependencies. No broker API keys or TOTP values belong in this repository.
