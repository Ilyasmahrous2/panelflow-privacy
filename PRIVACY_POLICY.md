# Privacy Policy for PanelFlow

**Effective Date:** November 24, 2026  
**App Name:** PanelFlow  
**Package Name:** `com.panelflow.app`

PanelFlow is built with a privacy-first, local-first architecture. We do **not** require account creation and do **not** sell your personal library or reading history. This policy transparently explains what data stays on your device and what minimal data is transmitted when you opt in to Instant Cloud AI, Rewarded Ads, or Google Play Billing.

---

## 1. Data Stored Locally on Your Device

All library content and application preferences are stored inside your device's private app storage:

- **Comic & Manga Chapters:** Imported images (`CBZ`, `ZIP`, `PDF`) and captured chapter pages (converted to local WebP files).
- **Local Vault Database (Room / SQLite):** Series titles, chapter metadata, reading positions, cached OCR coordinates, cached translations, character/gender glossaries, and browser bookmarks.
- **Settings & API Keys:** Your chosen translation mode, model name, language preferences, Pro/Pass status, and any Bring-Your-Own-Key (BYOK) API keys you enter.

Your comic images and local Vault database are **never** uploaded to PanelFlow servers.

---

## 2. On-Device OCR & Offline Translation

- **Text Recognition (OCR):** PanelFlow uses Google Play Services ML Kit Text Recognition (`Latin`, `Japanese`, `Korean`, `Chinese`) to detect speech-bubble text **directly on your device**. Comic images are never sent to external OCR servers.
- **Offline Translation (100% Free Mode):** When you select **Offline Translation**, PanelFlow uses Google ML Kit On-Device Translation models downloaded to your device. All translation runs locally without sending text over the network.
- **Model Pack Downloads:** Downloading optional OCR or offline translation language packs connects directly to Google Play Services / ML Kit infrastructure.

---

## 3. PanelFlow Instant Cloud AI Proxy (Opt-In)

Only when you choose **Instant Cloud AI** (or claim Cloud AI credits/purchases):

- **Anonymous Device Identifier:** PanelFlow generates a one-way SHA-256 hash of your device's `ANDROID_ID` scoped to `com.panelflow.app` (`X-Device-Id`) solely to track your free welcome bubbles (`300` bubbles), credit balance, daily rate limits, and idempotent purchase top-ups in Cloudflare Workers KV. No name, email, or account is required.
- **Transient Speech-Bubble Text:** Only the extracted speech-bubble text (and your optional series character glossary) is transmitted over HTTPS to PanelFlow's Cloudflare Worker proxy and forwarded to the upstream AI translation provider (DeepSeek) for real-time translation. **Bubble text is processed transiently in memory and is NOT logged or stored** by PanelFlow's Worker. Comic images are never uploaded.
- **Approximate Country Code:** Cloudflare's edge provides an ISO country code (`request.cf.country`) solely to determine regional availability for optional Cloud AI rewarded ads; PanelFlow does not store your IP address or precise GPS location.

---

## 4. User-Initiated Third-Party AI Translation (BYOK)

If you choose **AI Translation (API Keys / BYOK)** and enter your own API key for a third-party provider (**Google Gemini**, **DeepSeek**, **Groq**, **Qwen / DashScope**, **OpenRouter**, or a **Custom OpenAI-Compatible Endpoint**):

- **Direct Device-to-Provider Requests:** PanelFlow sends only extracted speech-bubble text (and optional glossary) directly from your device to the provider you chose.
- **API Key Handling:** Your API keys remain stored locally on your device and are transmitted strictly as authentication headers to your selected provider.
- **Third-Party Policies:** Text processed by your chosen BYOK provider is governed by that provider's own privacy policy and terms of service.

---

## 5. Opt-In Rewarded Advertising (Google AdMob)

PanelFlow does **not** display banner or interstitial ads inside the comic reader. Users who opt in to watch a **Rewarded Ad** (e.g., to unlock a temporary 2-Hour Pro Pass or eligible Cloud AI bubble rewards) interact with the **Google Mobile Ads (AdMob) SDK**:

- **Data Collected by Google AdMob:** AdMob may collect your device's **Advertising ID**, IP address, coarse diagnostics, and ad interaction events for ad serving, fraud prevention, and measurement, in accordance with [Google's Privacy Policy](https://policies.google.com/privacy) and [Google Ads Technologies](https://policies.google.com/technologies/ads).
- **Ad-Free Option:** Purchasing any Pro or Cloud subscription or Lifetime Pro permanently disables ad prompts across the app. You can also reset or delete your Android Advertising ID anytime in Android **Settings → Privacy → Ads**.

---

## 6. In-App Purchases & Subscriptions (Google Play Billing)

Optional upgrades (Pro BYOK Monthly/Lifetime, Cloud Starter/Plus Monthly, and Bubble Credit Packs) are processed exclusively by **Google Play Billing**:

- **Payment Information:** PanelFlow never sees or stores your credit card, bank, or Google Pay payment details.
- **Purchase Verification Tokens:** For Cloud AI credit packs and subscriptions, PanelFlow transmits the Google Play `productId` and `purchaseToken` over HTTPS to PanelFlow's Cloudflare Worker to verify receipt validity and record a one-way SHA-256 transaction hash (`tx:<hash>`) to prevent duplicate redemption.

---

## 7. Built-in Web Browser

PanelFlow includes an Android `WebView` browser so you can browse comic websites and save chapters to your local Vault:

- Websites you visit receive standard HTTP requests (IP address, user-agent, cookies) directly from your device like any mobile browser.
- Bookmarks and ad/redirect filter rules run entirely locally on your device. PanelFlow does not log or transmit your browsing history.

---

## 8. Permissions Used

- **`INTERNET`:** Browsing websites, downloading optional ML Kit packs, user-initiated AI translation, AdMob rewarded ads, and Play Billing verification.
- **`FOREGROUND_SERVICE` / `FOREGROUND_SERVICE_DATA_SYNC`:** Completing user-initiated background batch chapter translation reliably when the screen turns off.
- **`POST_NOTIFICATIONS` (Optional):** Showing progress and completion notifications for background batch translation jobs.
- **`com.google.android.gms.permission.AD_ID` (Merged via AdMob SDK):** Used by Google AdMob when serving opt-in rewarded ads.

---

## 9. Data Retention & Deletion

- Delete chapters, series, character entries, or bookmarks inside PanelFlow at any time.
- Clear API keys in Settings at any time.
- Uninstalling PanelFlow or clearing app storage in Android Settings permanently deletes all local chapters, databases, caches, and keys.
- To request deletion of your anonymous Cloudflare KV credit ledger record, contact us with the SHA-256 device hash or support details.

---

## 10. Children's Privacy

PanelFlow is intended for general audiences aged 13+ and does not knowingly collect personal information from children under 13 (or the applicable age of digital consent in your jurisdiction).

---

## 11. Contact

If you have questions or privacy requests, please contact the developer via the support email listed on PanelFlow's Google Play Store listing or open an issue on the project repository.
