# Vizor mobile releases

This repository distributes official Vizor Android APKs built from the
[Vizor Wallet source repository](https://github.com/chainapsis/vizor-wallet).
It does not contain the application source code.

## Downloads

Stable releases are published on the
[Releases page](https://github.com/chainapsis/vizor-wallet-mobile-releases/releases).
After the first stable release is published, the current release will also be
available through
[`releases/latest`](https://github.com/chainapsis/vizor-wallet-mobile-releases/releases/latest).

Each stable release is expected to contain:

- `Vizor-android.apk` and `Vizor-android.apk.sha256` — 64-bit ARM,
  recommended for most phones
- `Vizor-android-arm64-v8a.apk` and
  `Vizor-android-arm64-v8a.apk.sha256` — identical ABI-labelled alias
- `Vizor-android-armeabi-v7a.apk` and
  `Vizor-android-armeabi-v7a.apk.sha256` — legacy 32-bit ARM
- `Vizor-android-x86_64.apk` and `Vizor-android-x86_64.apk.sha256` — Intel
  Chromebooks and emulators
- `Vizor-android-metadata.json`

`Vizor-android.apk` is an arm64-v8a APK, not a universal APK. Alternative
architectures have explicit filenames so most users can use the default download
without choosing a CPU architecture.

Release candidates and internal builds are marked as GitHub prereleases and
are never selected as the latest stable release.

## Obtainium

Obtainium can monitor this repository for new Vizor releases and install the
appropriate APK. See [Use Vizor with Obtainium](OBTAINIUM.md) for manual setup
instructions.

## Authenticity

Official direct-download APKs are signed with the Vizor Direct signing
certificate. Its SHA-256 certificate fingerprint is:

```text
07:A3:2D:D9:F5:8A:0E:3B:EA:F0:C3:0D:B0:81:38:B6:06:E6:61:23:5D:0A:6C:79:0C:59:7B:5D:99:B0:FF:C7
```

You can inspect an APK with Android SDK Build Tools:

```bash
apksigner verify --verbose --print-certs Vizor-android.apk
```

Compare both the APK SHA-256 checksum and signing-certificate fingerprint with
the values published alongside the release. Do not install an APK if either
value differs.

## Source provenance

Every release identifies the corresponding source tag and exact source commit
from `chainapsis/vizor-wallet`. The accompanying `Vizor-android-metadata.json`
records that provenance together with the ABI-specific APK checksums, Android
version code, and signing-certificate fingerprint.

Source code, development, pull requests, and issue tracking remain in the
[Vizor Wallet repository](https://github.com/chainapsis/vizor-wallet).

## F-Droid

F-Droid tracks and builds the application from the public source repository;
its repository metadata and distribution are maintained separately from this
direct-download channel. The intended upstream signing identity for GitHub and
F-Droid distribution is the Vizor Direct certificate shown above, subject to
F-Droid's reproducible-build verification and signing requirements.
