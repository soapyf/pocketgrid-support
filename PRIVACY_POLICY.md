# PocketGrid Privacy Policy

**Effective Date:** November 23, 2026  
**App Name:** PocketGrid (`io.github.soapyf.pocketgrid`)  
**Developer:** Soap Frenzy

PocketGrid is an independent, unofficial text-only mobile client for Second Life and compatible virtual world grids. This Privacy Policy explains what information PocketGrid processes on your device, how it is protected, and how it is shared.

---

## 1. Summary

- **No developer servers:** PocketGrid does not route your messages, credentials, or activity through any developer owned backend server.
- **No tracking, ads, or analytics:** PocketGrid contains no advertising SDKs, analytics trackers, crash-reporting SDKs, or cross-app profiling tools.
- **Direct connection only:** Your device communicates directly with the virtual world grid you choose to log into (such as Second Life servers operated by Linden Research, Inc., or a custom grid URL you provide).

---

## 2. Information Processed and Stored Locally on Your Device

All data stored by PocketGrid remains strictly on your device inside app-private storage:

1. **Login Credentials and MFA Trust Tokens (Optional):**
   - If you turn on **Remember login** or **Trust this device for 30 days**, your avatar name, password, grid selection, start location, and any 30-day MFA hash returned by the grid are stored locally using Android `EncryptedSharedPreferences`, backed by **Android Keystore** (`AES-256-GCM` / `AES-256-SIV`).
   - Passwords and MFA device hashes are never written to plain-text preferences or SQLite.

2. **Protocol Device Identifiers (`mac` / `id0`):**
   - The Second Life XML-RPC login protocol expects `mac` and `id0` client identifier strings. PocketGrid derives non-reversible MD5 hash values locally from your app-scoped Android ID (or a locally generated random UUID) and avatar name solely to complete grid authentication and preserve 30-day MFA device trust. These identifiers are not used for advertising or cross-app tracking.

3. **Messages, Contacts, Profiles, Groups, Places, and Outfits:**
   - Direct messages, conversation summaries, cached resident/group profiles, contacts, block lists, landmarks, favorite places, and outfit metadata are cached locally in an app-private SQLite database so the app remains responsive over mobile connections.
   - Per-account direct messages and sensitive profile fields are encrypted locally using `ChaCha20-Poly1305` (with key material derived via `PBKDF2-HMAC-SHA256` using your account credentials).
   - You can disable local saving of future direct messages at any time via **Settings → Persist DM history** (turning this off clears stored DM history and conversations from the local database).

4. **Cached Grid Images:**
   - Profile photos, outfit previews, and world map tiles fetched from the grid CDN are cached temporarily in app-private storage and can be cleared anytime via **Settings → Clear image cache**.

---

## 3. Information Sent Over the Network

PocketGrid sends network requests **only** directly to the virtual world grid you log into:

- **Main Grid / Beta Grid (Second Life):** XML-RPC login (`login.agni.lindenlab.com` / `login.aditi.lindenlab.com`), region simulator UDP circuits, EventQueue/capability HTTPS endpoints, and Second Life's image CDN.
- **Custom Grid (if selected by you):** The custom login URI and simulator endpoints provided by that grid operator.

Your use of Second Life or any third-party virtual world grid is subject to that operator's own terms of service and privacy policy (for Second Life, see Linden Research, Inc.'s Privacy Policy at https://www.lindenlab.com/privacy).

---

## 4. Android Permissions Used

PocketGrid requests only the permissions needed to stay connected and deliver chat notifications:

- **`INTERNET` & `ACCESS_NETWORK_STATE`:** Connect to your chosen grid and recover cleanly across Wi-Fi/cellular network handoffs.
- **`FOREGROUND_SERVICE` / `FOREGROUND_SERVICE_DATA_SYNC` & `WAKE_LOCK`:** Keep your live chat connection active in the background while you are logged in so incoming messages continue arriving reliably.
- **`POST_NOTIFICATIONS`:** Display your connection status notification and optional alerts for incoming DMs, mentions, and notices.

---

## 5. Data Retention and Deletion

Because the developer does not collect or store any user data on external servers, you remain in full control of all data saved on your device:

- Inside **Settings**, you can tap **Forget saved credentials**, **Revoke trusted device**, **Clear image cache**, or toggle off **Persist DM history**.
- Uninstalling PocketGrid or clearing **App storage** in Android Settings permanently deletes all locally stored credentials, encryption keys, cached images, and databases.

To request deletion of server-side account data or chat logs retained by Second Life itself, contact Linden Research, Inc. directly under their privacy policy.

---

## 6. Children's Privacy

PocketGrid is not intended for children under the minimum age required by Second Life or your chosen virtual world grid.

---

## 7. Changes to This Policy

We may update this Privacy Policy as PocketGrid evolves. Any updates will be published at this URL with an updated effective date.

---

## 8. Contact

If you have questions about this Privacy Policy, please contact:

- **Email:** pocketgrid@proton.me
- **Support & Docs (GitHub):** https://github.com/soapyf/pocketgrid-support
