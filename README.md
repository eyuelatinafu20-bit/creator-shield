# Creator Shield Android TWA

This repository contains the Android Trusted Web Activity wrapper for `https://creatorshields.com/`.

## Build

The project is built from the `android-twa` directory with Gradle 8.2 and Java 17. By default it uses Android SDK 34.

Example local commands:

```bash
gradle -p android-twa lintDebug
gradle -p android-twa assembleDebug
```

## Release configuration

Release tasks require signing values to be supplied through Gradle properties or environment variables:

- `KEYSTORE_PATH`
- `KEYSTORE_PASS`
- `KEY_ALIAS`
- `KEY_PASS`
- `TWA_SHA256_FINGERPRINTS` as a comma-separated list of SHA-256 certificate fingerprints

Example:

```bash
export KEYSTORE_PATH=/absolute/path/to/release.keystore
export KEYSTORE_PASS=...
export KEY_ALIAS=...
export KEY_PASS=...
export TWA_SHA256_FINGERPRINTS=AA:BB:CC:...,11:22:33:...
gradle -p android-twa assembleRelease
```

Debug builds do not require signing secrets. Verified app-link/TWA association only becomes active after `TWA_SHA256_FINGERPRINTS` is provided.
