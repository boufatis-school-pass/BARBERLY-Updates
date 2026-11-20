# BARBERLY-Updates

Public update metadata channel for the BARBERLY Android applications.

## Application manifests

- Barber: [barber.json](./barber.json) — package `com.barberly.barberly_barber`
- Customer: [customer.json](./customer.json) — package `com.barberly.barberly_customer`
- Validation rules: [manifest.schema.json](./manifest.schema.json)

The applications read these JSON manifests directly from the public raw GitHub URLs:

- `https://raw.githubusercontent.com/boufatis-school-pass/BARBERLY-Updates/main/barber.json`
- `https://raw.githubusercontent.com/boufatis-school-pass/BARBERLY-Updates/main/customer.json`

## Published release

BARBERLY 1.1.2 (build 5) is published in [GitHub Release V1.1.2](https://github.com/boufatis-school-pass/BARBERLY-Updates/releases/tag/V1.1.2).

- Barber APK: [barberly-barber.apk](https://github.com/boufatis-school-pass/BARBERLY-Updates/releases/download/V1.1.2/barberly-barber.apk)
- Customer APK: [barberly-customer.apk](https://github.com/boufatis-school-pass/BARBERLY-Updates/releases/download/V1.1.2/barberly-customer.apk)

Both manifests are enabled and contain the direct HTTPS download URL and SHA-256 digest reported by GitHub for the corresponding uploaded release asset. The updater independently hashes the downloaded APK before opening Android's installer.

## Manifest requirements

An enabled manifest contains:
- `applicationId`: exact Android package ID.
- `version` and `buildNumber`: release version and Android build number.
- `minimumSupportedBuildNumber`: minimum installed build allowed to continue using the app.
- `downloadUrl`: direct HTTPS APK URL.
- `sha256`: 64-character SHA-256 checksum of the exact APK bytes.
- `releaseNotes`: user-facing release notes.

The GitHub Actions validation workflow rejects malformed manifests, wrong package IDs, and a minimum supported build greater than the release build.

## Compatibility

Only app builds containing the GitHub-manifest updater can use this channel. Older installed builds that still use the earlier Firestore-based updater cannot read these GitHub manifests.

## Security

Never store signing keys, signing passwords, Firebase service-account files, or access tokens in this public repository. Android update APKs must retain the same package ID and signing certificate as the installed app.
