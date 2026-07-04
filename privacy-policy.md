# Privacy Policy — FaceMetrics

> **TEMPLATE — not legal advice.** Fill in the placeholders and have it reviewed
> before publishing. Host it and link the URL in `LegalUrls.PRIVACY`.

_Last updated: 2 July 2026_

## 1. Who we are (Controller)
Marne Kismann, contact: marne.kismann@gmail.com. This is the controller
responsible for data processing under the EU GDPR (DSGVO).

> **Note:** German law (§5 DDG/TMG Impressum) generally requires a physical
> postal address for a publicly distributed app/website. An email alone may not
> be sufficient. Add a postal address (or a c/o / service address) before public
> release.

## 2. The short version
- Your **photos are processed entirely on your device** and are **never uploaded,
  stored, or transmitted** by us.
- We collect **no personal data by default.**
- If you opt in, we collect **anonymous, aggregated usage statistics** to improve
  the app. You can decline and still use everything.

## 3. What we process

**a) Photos & facial analysis (on-device only).** When you pick a photo, the app
detects facial landmarks and computes measurements locally using MediaPipe,
including an **on-device estimated age**. The image, the landmarks and the
estimated age stay on your device and are not sent to us or anyone else.

**b) Anonymous usage statistics (only with your consent).** If you tick the
optional consent on first launch, each analysis sends an anonymous record to our
backend (Google Firebase / Firestore): the score range, tier, classified face
shape, symmetry value, photo-quality level, number of faces detected and a coarse
**age bracket** (e.g. “18–24” — never the exact age). These records contain
**no image, no facial data, no name, and no identifier** that links them to you
or to each other.

**c) Firebase Analytics (only with your consent).** With the same consent we use
Google Analytics for Firebase, which provides aggregated demographics such as
approximate country (derived by Google from IP address — we never see or store
your IP) and device type. See Google's processing terms.

**d) Access codes & anonymous sign-in.** To unlock results you enter a one-time
code. The app signs in anonymously (Firebase Authentication) to validate codes;
this creates a random, non-identifying user ID with no personal data attached.

## 4. Legal bases (GDPR Art. 6)
- On-device analysis: no processing of personal data by us.
- Usage statistics & Firebase Analytics: **your consent** (Art. 6(1)(a)), which
  you can withdraw at any time.
- Code validation / anonymous auth: performance of the service you request
  (Art. 6(1)(b)) and our legitimate interest in preventing abuse (Art. 6(1)(f)).

## 5. Processors & international transfers
We use **Google Firebase** (Google Ireland Ltd.) as a processor. Data may be
processed on Google servers, including outside the EU/EEA, under EU Standard
Contractual Clauses. See Google's Firebase Data Processing Terms.

## 6. Retention
Anonymous usage records are kept for 14 months, then deleted or further
aggregated. On-device data lives only as long as the app session.

## 7. Your rights
You have the right to access, rectification, erasure, restriction, portability,
and to object, and to withdraw consent at any time (in the app’s settings or by
contacting us). Because usage data is anonymous, we may be unable to link it back
to you. You may also lodge a complaint with a supervisory authority.

## 8. Children
The app is not intended for anyone under 16. We do not knowingly collect data
from children.

## 9. Changes
We may update this policy; the “last updated” date reflects the current version.

## 10. Contact
marne.kismann@gmail.com.com
