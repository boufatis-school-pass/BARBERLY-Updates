# BARBERLY-Updates

Official public update channel for the BARBERLY Android applications.

## Applications

- Barber: `com.barberly.barberly_barber`
- Customer: `com.barberly.barberly_customer`

## Release safety requirements

A release is not considered published until **both** application packages have:

1. A publicly reachable HTTPS direct-download URL.
2. A SHA-256 checksum calculated from the exact APK uploaded to that URL.
3. A version and Android build number greater than the currently distributed build.
4. The same trusted production signing certificate as the installed application.
5. A successful install/update test on a device that already has the previous version installed.

Do not publish placeholder URLs, placeholder checksums, or metadata that advertises a build before its APK is available. Do not put signing keys, passwords, Firebase service-account files, or access tokens in this public repository.

## Manifest format

`manifest.schema.json` describes the public metadata format reserved for this channel. Each app must have its own manifest and APK. Metadata must be enabled only after the corresponding APK has been uploaded and verified.

Fields:

- `enabled`: whether the release is available to clients.
- `applicationId`: exact Android package ID.
- `version` and `buildNumber`: release version and monotonically increasing Android build number.
- `minimumSupportedBuildNumber`: minimum installed build allowed to continue using the app.
- `downloadUrl`: direct HTTPS APK URL.
- `sha256`: 64-character SHA-256 checksum of that exact APK.
- `releaseNotes`: user-facing release notes.

## Current channel status

The repository is public and accessible, but no verified APK binaries or live release manifests have been published here yet. The app's current updater still reads the protected Firestore documents `appUpdates/barber` and `appUpdates/customer`; adding files to this repository alone does not change that behavior.

Publishing also requires a safe, authorized binary-upload path and a production signing key that has not been exposed. Until those requirements are met, keep the in-app update channel unpublished rather than offering an unsafe or broken update.
