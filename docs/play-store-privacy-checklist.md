# Redox Launcher Play Store Privacy Checklist

Use this checklist when filling Play Console declarations so they stay consistent with the app and privacy policy.

## Privacy Policy

- Publish `docs/privacy-policy.html` at a public, non-PDF, non-geofenced URL.
- Add that URL to Play Console.
- Keep the in-app policy text and hosted policy text aligned when privacy behavior changes.

## Advertising ID

- The final packaged manifests should not include:
  - `com.google.android.gms.permission.AD_ID`
  - `android.permission.ACCESS_ADSERVICES_AD_ID`
  - `android.permission.ACCESS_ADSERVICES_ATTRIBUTION`
- Redox does not use analytics for advertising or ad targeting.

## Data Safety

- Crash reports are optional and controlled by the `Crash reports` toggle.
- Usage analytics is optional and controlled by the `Usage analytics` toggle.
- `Delete local privacy data` clears locally stored hidden app choices, search history, PIN/recovery data, biometrics, locks, and privacy toggles without deleting the home layout.
- Declare any optional data used by enabled features, including contacts search, approximate location for weather, notification/media access for Now Playing, and Bluetooth/camera/DND access for smart controls.
- Do not declare collection of app names, package names, search text, hidden app lists, PINs, recovery phrases, files, photos, precise location, or home screen contents for Redox analytics.

## Verification Commands

```powershell
.\gradlew.bat :app:compileReleaseKotlin
rg -n "AD_ID|ACCESS_ADSERVICES" app/build/intermediates/merged_manifests app/build/intermediates/packaged_manifests
```

The `rg` command should return no matches for the final release manifests.
