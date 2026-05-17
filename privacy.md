# BizTrackrPH Privacy Policy

**Effective date:** *17 May 2026*
**Last updated:** *17 May 2026*

This Privacy Policy describes how **BizTrackr** ("the app", "we", "our")
handles information when you use the mobile application on your Android or
iOS device. We are committed to keeping the app simple, transparent, and
respectful of your data.

If you do not agree with this Privacy Policy, please do not use BizTrackr.

---

## Short version

- **BizTrackrPH is an offline app.** It does **not** send your business data
  to any server, to us, or to any third party.
- **We do not collect, store, or have access to any personal information
  about you or your customers.**
- All product, inventory, sale, and receipt data lives **on your device
  only**, in the app's private storage.
- We use the camera (for barcode scanning), your photo library (for
  product images), and biometrics (Face ID / fingerprint, for unlocking
  the app) **only when you ask the app to.**
- Backups and receipts are shared **only when you tap Share or Export**,
  and only to the destination you choose (Files app, Drive, Mail,
  Messages, etc.).
- Backups can be encrypted with a passphrase you choose. We never see
  that passphrase.
- If you uninstall the app, your data is permanently deleted from your
  device.

---

## 1. Who we are

BizTrackr is published by HNB Software Labs ("we"), based in the Philippines.

You can contact us at:
- **Email:** henry.dev09@gmail.com
- **Mailing address:** henry.dev09@gmail.com

For matters specifically related to the Philippine **Data Privacy Act of
2012 (RA 10173)**, our designated point of contact is the same email
above.

---

## 2. Information we collect

### 2.1 Information BizTrackr does NOT collect

To be unambiguous, BizTrackr does **not** collect, transmit, or have any
ability to read any of the following:

- Your name, email address, phone number, or mailing address
- The names, contact details, or any identifiers of your customers
- Your store's location or any location data
- Your IP address, device identifier (IDFA/AAID), or other tracking
  identifiers
- Crash reports, usage analytics, or telemetry of any kind*
- Browsing history, contact list, calendar, or messages

*If we add crash reporting in a future version, this policy will be
updated and an in-app notice will appear before any reports are sent.*

### 2.2 Information you enter into the app

The app stores the following on your device only, when you choose to
enter it:

- **Store profile**: store name, address, contact, tax identification
  number (TIN), and receipt footer message
- **Products**: name, SKU, category, price, stock count, barcode,
  description, and product photos
- **Categories** and subcategories
- **Sales**: each completed transaction (product name, quantity, total,
  date)

This data is stored in the app's private storage area on your device. It
is not transmitted off the device by the app itself.

### 2.3 Security information

When you enable App Lock:

- Your **PIN** is never stored. We store only a salted, cryptographically
  hashed representation (PBKDF2-HMAC-SHA256, 200,000 iterations) inside
  the device's protected storage (Android `EncryptedSharedPreferences`
  backed by a hardware-backed key; iOS Keychain with
  `kSecAttrAccessibleAfterFirstUnlockThisDeviceOnly`).
- Your **biometric data** (fingerprint, Face ID, Touch ID) never touches
  BizTrackr. The operating system handles all biometric matching; we
  only receive a yes/no result from the OS.

---

## 3. How we use the information you enter

The information you enter is used solely to provide the in-app features
you actively use:

- Show your products in the Inventory tab
- Compute totals and stock during point-of-sale checkout
- Calculate sales summaries, top sellers, and trends in the Sales tab
- Render receipts (including your store profile) for sharing

We do not use this information for any other purpose. We do not analyse
it, profile you, or build advertising audiences from it.

---

## 4. Permissions the app requests, and why

BizTrackr asks for the following operating-system permissions. You can
revoke any of these at any time in your device settings; the app will
continue to work, with the related feature disabled.

| Permission | When it is requested | What we do with it |
|---|---|---|
| **Camera** | First time you tap the barcode-scanner button in Add Product or POS | Used only to decode product barcodes in real time. No frames are recorded or transmitted. |
| **Photo library / Photos** | First time you add or edit a product photo | Lets you select an image from your library. The chosen image is copied to the app's private storage. We do not access photos you have not explicitly picked. |
| **Face ID / biometrics** | First time you enable "Use biometric unlock" in Settings | Used solely to unlock the app. Matching is performed by iOS / Android; we never receive your biometric data. |

The app does **not** request location, contacts, calendar, microphone,
Bluetooth, notifications, or any other permission.

---

## 5. Where your data is stored

All BizTrackr data is stored locally on your device:

- **Product, category, and sales records** are stored in a private
  SQLite database file (managed by Room) inside the app's sandbox.
- **Product images** are stored as JPEG files inside the app's private
  files directory (`filesDir/products/` on Android, `Documents/` on
  iOS), accessible only by BizTrackr.
- **App-lock secrets** (PIN salt and hash) are stored in encrypted
  device storage as described in section 2.3.

No copy of your data is held by us, by our hosting provider (we have
none), or by any cloud service — unless **you** export or share it as
described below.

---

## 6. Data you choose to share

BizTrackr only ever sends data off your device when **you** initiate it.

### 6.1 Receipt sharing
When you tap **Share Receipt** after a sale, the receipt is rendered as a
PNG image and handed to the operating system's share sheet. You then
choose where to send it (Messages, Mail, Save to Files, etc.). BizTrackr
has no knowledge of where you send it or who the recipient is.

### 6.2 Backup export
When you tap **Export backup…** the app produces a single backup file
(`.btb`) containing your store profile, products, categories, and sales.

**This file is encrypted on your device before it leaves the app.** We
use AES-256-GCM with a key derived from a passphrase you choose
(PBKDF2-HMAC-SHA256, 200,000 iterations). The passphrase is never stored
or transmitted; **only you can decrypt the backup**. If you lose the
passphrase, the backup cannot be recovered — not even by us.

You decide where the encrypted backup file goes (Files, Google Drive,
iCloud Drive, email, etc.). Once it leaves the app, the destination
service's own privacy policy applies.

### 6.3 Backup import
When you tap **Restore from backup…**, you pick a backup file. If the
file is an encrypted `.btb`, the app prompts you for the passphrase and
decrypts on-device. The contents are then loaded into the local
database. No part of the backup is transmitted off the device.

---

## 7. Third-party services and SDKs

BizTrackr's user-visible features are all on-device. The libraries we
use are open-source and do not phone home in the configuration we ship.

- **Room** (AndroidX / JetBrains) — local database
- **CameraX + ML Kit Barcode Scanning** (Google) — on-device barcode
  recognition. ML Kit's barcode model runs entirely on-device; no images
  or barcode values are sent to Google.
- **Coil** — on-device image loading and caching
- **AndroidX Biometric** — wraps the OS biometric prompt
- **kotlinx.serialization** — JSON encoding for backup files
- **CryptoKit / CommonCrypto / javax.crypto** — operating-system
  cryptography for backup encryption and PIN hashing

We do **not** integrate any advertising SDK, analytics SDK, attribution
SDK, A/B-testing SDK, or crash-reporting SDK. If this changes in a
future version we will update this policy and clearly disclose the
service in advance.

---

## 8. Children's privacy

BizTrackr is a business tool intended for adult shopkeepers and
entrepreneurs. It is not directed at children under 13 (or the
equivalent minimum age in your jurisdiction). We do not knowingly
collect any information from children. If you believe a child has been
using the app, simply uninstall it — there is no online account to
delete.

---

## 9. Your rights

Because all your data is stored locally on the device under your
control, you exercise your data rights directly through the app and
your device:

- **Access**: All information is visible in the app's Inventory, Sales,
  and Settings tabs. You can also export an unencrypted plaintext JSON
  copy (legacy export) or an encrypted `.btb` for inspection elsewhere.
- **Correction**: You can edit any product, category, store-profile
  field, or transaction directly in the app.
- **Deletion**: You can delete individual products, categories, or
  sales from within the app. To delete *all* data, uninstall the app or
  use the operating system's "Clear data" option (Android) /
  "Offload App / Delete App" (iOS). Once uninstalled, no copy of your
  data persists on the device.
- **Portability**: The backup export produces a structured file you can
  move to another device or another tool.
- **Restriction / objection**: Because no processing occurs off your
  device, there is nothing to restrict beyond not using the feature.

If you have created encrypted backups stored on a cloud service (Drive,
iCloud, etc.), please consult that service's own controls to manage
those copies.

---

## 10. Security

We follow security practices appropriate to a local-only application:

- All secrets (PIN hash, salt) are stored in encrypted OS keystores
  (Keychain on iOS, `EncryptedSharedPreferences` with hardware-backed
  master keys on Android).
- App Lock with PIN and optional biometric authentication prevents
  unauthorised access to the app on a shared device.
- Auto-lock can be configured to re-lock the app after a period of
  inactivity.
- Backup files exported by the user can be encrypted with AES-256-GCM
  and a passphrase-derived key.

**No security system is perfect.** If you suspect a vulnerability,
please email us at henry.dev09@gmail.com.

---

## 11. International users

### 11.1 Philippines — Data Privacy Act of 2012 (RA 10173)

Because BizTrackr does not collect personal information as a Personal
Information Controller (PIC) or Processor (PIP), most provisions of the
Data Privacy Act do not impose specific obligations on us. Nonetheless,
we publish this policy in keeping with the spirit of the Act and the
National Privacy Commission's transparency principles. If you believe
your rights under the Act have been affected by use of the app, you may
contact the **National Privacy Commission**: <https://www.privacy.gov.ph/>.

### 11.2 European Economic Area, United Kingdom, Switzerland (GDPR / UK GDPR)

If you are in the EEA, UK, or Switzerland, no personal data leaves your
device through BizTrackr, so no cross-border transfer occurs. We do not
have, and do not act as, a controller or processor for any data about
you under the GDPR. Where you have created backups stored on a
third-party cloud service, that service is the controller for any data
it holds.

### 11.3 California, USA (CCPA / CPRA)

We do not sell, share, or otherwise disclose personal information about
California consumers. Because we do not collect such information in the
first place, your rights to access / delete / opt-out under the CCPA
have nothing to act on.

---

## 12. Changes to this policy

We may update this Privacy Policy from time to time — for example, when
we add or change a feature. The "Last updated" date at the top will
reflect any change. Material changes will be announced in the app
before they take effect. Continued use of the app after an update means
you accept the updated policy.

---

## 13. Contact

For privacy questions, requests, or concerns:

- **Email:** henry.dev09@gmail.com

If you do not receive a satisfactory response, you may also contact the
relevant data-protection authority in your country.

---

*This document is provided for transparency. It is not legal advice.
Before publishing, have it reviewed by a qualified lawyer familiar with
your jurisdiction, especially if you operate in or accept users from
the EU, the UK, California, or other regions with specific data-privacy
statutes.*
