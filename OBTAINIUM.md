# Use Vizor with Obtainium

[Obtainium](https://github.com/ImranR98/Obtainium) can monitor Vizor's GitHub
releases, notify you when an update is available, and install the selected APK.

## Add Vizor

1. Open Obtainium and choose **Add App**.
2. Enter this source URL:

   ```text
   https://github.com/chainapsis/vizor-wallet-mobile-releases
   ```

3. Open the additional options and set **Filter APKs by Regular Expression**
   to:

   ```text
   ^Vizor-android(?:-arm64-v8a|-armeabi-v7a|-x86_64)?\.apk$
   ```

4. Enable **Attempt to filter APKs by CPU architecture if possible**.
5. Set **Expected signing certificate hashes** to:

   ```text
   07:A3:2D:D9:F5:8A:0E:3B:EA:F0:C3:0D:B0:81:38:B6:06:E6:61:23:5D:0A:6C:79:0C:59:7B:5D:99:B0:FF:C7
   ```

6. Add the app and review the detected release before installing it.

Keep prereleases disabled if you only want stable Vizor releases.

## APK variants

Vizor publishes one APK for each supported CPU architecture:

| Architecture | Release asset | Intended devices |
| --- | --- | --- |
| `arm64-v8a` | `Vizor-android.apk`, `Vizor-android-arm64-v8a.apk` | Most modern Android phones and tablets |
| `armeabi-v7a` | `Vizor-android-armeabi-v7a.apk` | Legacy 32-bit ARM devices |
| `x86_64` | `Vizor-android-x86_64.apk` | Intel Chromebooks and emulators |

If Obtainium asks you to choose an APK, use the variant that matches your
device. Most users should choose `Vizor-android.apk`. The ABI-labelled
`Vizor-android-arm64-v8a.apk` file is an identical alias provided for update
clients that select APKs by filename.

## Verify the download

Official direct-download APKs use the Vizor Direct signing certificate shown
above. Obtainium's expected-certificate setting blocks installation when a
downloaded APK does not match that certificate.

Each [Vizor release](https://github.com/chainapsis/vizor-wallet-mobile-releases/releases)
also includes SHA-256 checksums and source provenance. See the
[repository README](README.md#authenticity) for manual verification steps.

## Switching from Google Play

The Google Play and direct-release versions use different signing keys. Android
therefore does not allow one version to update the other in place. Before
switching channels, back up your recovery phrase, uninstall the existing app,
and then install Vizor through Obtainium.
