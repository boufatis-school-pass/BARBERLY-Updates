# BARBERLY-Updates

Public update metadata channel for the BARBERLY Android applications.

## Application manifests

- Barber: [barber.json](./barber.json) — package `com.barberly.barberly_barber`
- Customer: [customer.json](./customer.json) — package `com.barberly.barberly_customer`
- Validation rules: [manifest.schema.json](./manifest.schema.json)

The applications read these JSON manifests directly from the public raw GitHub URLs:

- `https://raw.githubusercontent.com/boufatis-school-pass/BARBERLY-Updates/main/barber.json`
- `https://raw.githubusercontent.com/boufatis-school-pass/BARBERLY-Updates/main/customer.json`

The public manifests are metadata only. Each APK must be hosted as a separate public HTTPS binary with a direct download URL.

## Publishing requirements

A manifest may be set to `"enabled": true` only after the corresponding APK is uploaded and verified. An enabled manifest must contain:

- `applicationId`: exact Android package ID.
- `version` and `buildNumber`: release version and monotonically increasing Android build number.
- `minimumSupportedBuildNumber`: minimum installed build allowed to continue using the app.
- `downloadUrl`: direct HTTPS APK URL.
- `sha256`: 64-character SHA-256 checksum of the exact APK bytes.
- `releaseNotes`: user-facing release notes.

The repository has a GitHub Actions validation workflow. It rejects malformed manifests, wrong package IDs, and a minimum supported build greater than the release build.

## Current status

Both manifests are intentionally disabled. No verified public APK binary or direct download URL is published yet, so the app will not offer an unusable update.

The current app updater source has been changed to read these public manifests. Users must install a build containing that updater before it can use this channel. Older installed builds still contain the earlier Firestore-based updater and cannot read these GitHub manifests.

## Security

Never store signing keys, signing passwords, Firebase service-account files, or access tokens in this public repository. Android update APKs must retain the same package ID and signing certificate as the installed app. Verify the SHA-256 of the uploaded APK after upload; never use a placeholder checksum or URL.
