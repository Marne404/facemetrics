# Analytics & Privacy

## What the app logs

After each analysis (only if the user consented), the app writes an **anonymous
aggregate** row to Firestore `analyses`:

| Field          | Example        | Notes                          |
|----------------|----------------|--------------------------------|
| `overall`      | 6.8            | attractiveness score           |
| `tier`         | `MMTN`         | PSL tier                       |
| `faceShape`    | `OVAL`         | classified shape               |
| `symmetry`     | 0.82           | 0–1                            |
| `qualityLevel` | `GOOD`         | photo quality                  |
| `confidence`   | 0.9            | 0–1                            |
| `facesDetected`| 1              |                                |
| `createdAt`    | timestamp      |                                |

It also sends a Firebase Analytics event `analysis_completed` (tier, face shape,
score bucket, quality).

**Never stored:** the photo, face landmarks, names, IPs, or anything tying a row
to a person. Rows are unlinkable to each other or to a user.

## Where to see the stats

- **Score / tier / face-shape / quality distributions, volume over time** →
  the **admin panel** (`admin/index.html`, Statistics card).
- **Country, device, age-group, retention** → **Firebase Console → Analytics**
  (dashboards + the `analysis_completed` event). Firebase derives country from
  IP on its side, so you never handle IP addresses yourself.

## Age estimation (bundled & working)

A TFLite age model is **bundled** at `app/src/main/assets/age_model.tflite`
(shubham0204 Age-Gender, MIT — see `THIRD_PARTY_NOTICES.md`). It's on-device,
runs on the cropped face, and was verified to load with input `[1,200,200,3]`
and output `[1,1]` (value × 116 = years). `AgeEstimator.kt` is configured to
match; if the asset is ever removed the app still works and age is omitted.

- Shown in the Rating tab (“Estimated age: ~28”).
- The exact age never leaves the device. Analytics stores only a coarse **age
  bucket** (`18-24`, …), and only with consent. The admin panel shows the
  age-group distribution.

⚠️ Estimating age from faces is sensitive under GDPR — especially since some
users may be minors. It stays bucketed/anonymous (as built); your privacy
policy already covers it (§3).

## GDPR / DSGVO — required before you enable this

You're in the EU and the app processes faces, so this is not optional:

1. **Consent first (built).** A first-run consent screen (`ConsentScreen`) blocks
   the app until accepted; analytics is opt-in and OFF unless ticked. The choice
   is stored, and Firebase Analytics collection is disabled by default via the
   manifest (`firebase_analytics_collection_enabled=false`) and only enabled at
   runtime after consent. To reset for testing, clear the app's storage.
2. **Privacy policy.** Publish one describing what you collect (anonymous usage
   stats, Firebase Analytics), why, and how to opt out. Link it in the app.
3. **Data minimisation.** Keep it aggregate/anonymous (as built). Don't add
   names, raw IPs, or stored images.
4. **On-device face processing** is a strong point — say so: images never leave
   the phone; only anonymous numbers do.

This file is guidance, not legal advice — confirm specifics for your case.
