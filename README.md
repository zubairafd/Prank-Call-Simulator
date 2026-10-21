<div align="center">

<img src="favicon.svg" alt="Phone App Logo" width="80" height="80"/>

# 📱 Phone — Prank Call Simulator

**A lifelike, fully offline incoming-call screen for Android.**  
Realistic UI · Custom ringtones · Scheduled calls · Zero permissions abuse · No ads · No account

[![Platform](https://img.shields.io/badge/Platform-Android%208.0%2B-3DDC84?style=flat-square&logo=android&logoColor=white)](https://www.android.com)
[![License](https://img.shields.io/badge/License-Free-0A8F63?style=flat-square)](#)
[![No Ads](https://img.shields.io/badge/Ads-None-brightgreen?style=flat-square)](#)
[![No Internet](https://img.shields.io/badge/Internet%20Permission-None-blue?style=flat-square)](#)
[![Version](https://img.shields.io/badge/Version-1.0-orange?style=flat-square)](#)

</div>

---

## 🌐 English

### Overview

**Phone** is a polished, privacy-first Android app that displays a hyper-realistic incoming-call screen on your own device — complete with your ringtone, a custom caller name, caller number, and SIM label. It never makes or receives real calls; it only renders a convincing call UI inside its own sandbox.

The companion **website** (this repository) is a single-file, dependency-free HTML landing page that lets users download the APK directly. No build step, no node_modules, no backend.

---

### ✨ Features

| Feature | Description |
|---|---|
| 🖥️ **Lifelike Call Screen** | Modelled on the OriginOS call layout — supports light & dark mode, SIM badge, caller name & number |
| ⏱️ **5 Timed Call Slots** | Each slot has its own time, caller, number, SIM, ringtone & repeat days. Schedules survive a reboot |
| 🎵 **Custom Ringtone** | Use the system ringtone or pick a unique one per schedule. Haptic vibration included |
| 🔒 **Answer Lock** | Hold the call ringing as long as you need. Decline always works instantly |
| ⚡ **Flash Alert** | Optional camera-flash blink while ringing; slower heartbeat pattern once "answered" |
| 🛡️ **Private by Design** | No internet, no ads, no account, no analytics. Everything stays on your device |
| 🌐 **Bilingual UI** | Full English + Roman Urdu interface, switchable from the nav bar |

---

### 🗂️ Repository Structure

```
Phone-Website/
├── index.html      → Full landing page (single file — no libraries, no CDN required)
├── phone.apk       → Signed Android APK (place your own APK here)
├── favicon.svg     → Browser tab icon
├── _headers        → Netlify / Cloudflare Pages — ensures APK downloads correctly
├── .nojekyll       → GitHub Pages — prevents Jekyll from ignoring dotfiles
└── README.md       → This file
```

---

### 🚀 Quick Start (Publishing Your Own Build)

#### Step 1 — Add Your APK

Place your signed APK file next to `index.html` and name it exactly **`phone.apk`**.

> If you prefer a different filename, update the `APP.file` variable at the bottom of `index.html`.

Without this file the **Download** button will return a `404`.

#### Step 2 — (Optional) Set Version & Checksum

Edit the `APP` object near the bottom of `index.html`:

```javascript
var APP = {
  version: "1.0",         // bump this with every release
  file:    "phone.apk",   // APK filename
  minAndroid: "8.0",      // minimum Android version
  sha256:  ""             // paste SHA-256 here to show a checksum on the page
};
```

**Generate SHA-256 on Windows (Command Prompt, inside the APK folder):**

```cmd
certutil -hashfile phone.apk SHA256
```

The website auto-detects and displays the file size when served over HTTP(S).

#### Step 3 — Deploy for Free (choose one)

| Host | Steps |
|---|---|
| **Netlify** *(easiest)* | 1. Create a free account at [app.netlify.com](https://app.netlify.com/drop) <br>2. Drag & drop the entire folder (including `phone.apk`) onto Netlify Drop <br>3. Your site is live at `something.netlify.app` |
| **GitHub Pages** | 1. Create a public repo on [github.com](https://github.com) <br>2. Upload all files via *Add file › Upload files* (note: browser uploads are capped at **25 MB per file** — use GitHub Releases for larger APKs) <br>3. Go to *Settings › Pages › Source → Deploy from branch → main / (root) → Save* <br>4. Live in ~1–2 minutes at `username.github.io/repo-name` |
| **Cloudflare Pages** | *Create a project › Upload assets* — drop the whole folder |

---

### 🔄 How to Update

1. In Android Studio, increment `versionCode` (e.g., `1` → `2`) and build a new signed APK using **the same keystore**.
2. Replace the old `phone.apk` with the new one.
3. Update `APP.version` in `index.html` (and re-generate `APP.sha256` if you use it).
4. Re-upload the folder to your hosting provider.

---

### 📲 How to Install (End-User Guide)

1. **Download** — Tap *Download for Android* on the website. If your browser asks to keep the file, choose **Keep**.
2. **Open the file** — Open `phone.apk` from the download notification or from *Files › Downloads*.
3. **Allow install** — If prompted, enable *"Install unknown apps"* for your browser or file manager, then tap **Install**.
4. **Finish setup** — Open **Phone › Setup Checklist** and tap *Fix* on each item so that timed calls fire on time.

> **On vivo / OriginOS:** Also turn on Autostart, allow high background power use, and lock Phone in Recents. The in-app OriginOS help screen walks you through every step.

---

### 🔐 Permissions Explained

| Permission | Why it's needed |
|---|---|
| Notifications | To display the incoming-call screen |
| Full-screen intent | Opens the call over the lock screen |
| Alarms & exact reminders | Fires timed calls at the precise scheduled time |
| Foreground service | Keeps the ringtone playing without being killed |
| Vibration | Vibrates while the call is ringing |
| Receive boot completed | Restores schedules after a device restart |
| Request ignore battery optimisations | Prevents the system from delaying timed calls |

**Not requested — ever:** Contacts · Call log · Phone state · SMS · Location · Microphone · Camera · Internet

---

### ❓ FAQ

<details>
<summary>Is Phone free?</summary>

Yes. Completely free — no ads, no in-app purchases, no subscription.

</details>

<details>
<summary>Why does Android / my browser show a security warning?</summary>

Android displays a warning for every app installed outside Google Play because it cannot verify the source. This is normal for sideloaded APKs. Only install from sources you trust, and compare the SHA-256 checksum shown on the download page.

</details>

<details>
<summary>Does it place or answer real calls?</summary>

No. It draws a call UI inside its own app sandbox only. It never touches your dialer, contacts, or call log.

</details>

<details>
<summary>Will it ring on a locked screen?</summary>

Yes — once the Setup Checklist inside the app shows all items as *Ready*. On vivo / OriginOS devices follow the additional steps shown in the in-app help screen.

</details>

<details>
<summary>Why isn't it on Google Play?</summary>

Publishing on Google Play requires a paid developer account ($25 one-time fee). For now, Phone is distributed directly as an APK.

</details>

<details>
<summary>How do I update or uninstall?</summary>

- **Update:** Download the latest APK and install it over the existing version.  
- **Uninstall:** *Settings › Apps › Phone › Uninstall*

</details>

---

### ⚠️ Responsible Use

> Phone is designed for **personal, harmless use** — escaping an awkward conversation, rehearsing a scenario, or running a demo. Please **do not** use it to impersonate real individuals, financial institutions, or government authorities, or to deceive or frighten anyone. Misuse may violate local laws.

---

### 🛠️ Tech Stack

| Layer | Technology |
|---|---|
| Website | Plain HTML5 + Vanilla CSS + Vanilla JS (zero dependencies) |
| Fonts | Google Fonts — *Inter*, *Libre Caslon Condensed* |
| Icons | Inline SVG sprites |
| Hosting | Netlify / GitHub Pages / Cloudflare Pages |
| Android App | Native Android (APK — sideload) |

---

### 👤 Author

**Zubair Afridi**  
Built with ❤️ — *© 2026 Phone. Not affiliated with vivo, Google, or any carrier. Android is a trademark of Google LLC.*

---

---

## 🌐 Roman Urdu *(یہ حصہ رومن اردو میں ہے)*

> **Neeche Roman Urdu mein tashrih hai — Ye hissa Roman Urdu mein likha gaya hai.**

---

### 📖 Mukhtasar Taaruf

**Phone** ek Android app hai jo aap ke apne phone par ek bilkul asli jaisi incoming call screen dikhati hai — aap ki khud ki ringtone, marzi ka caller naam, number aur SIM label ke saath. Ye app **koi asli call nahi karta**, sirf apni app ke andar ek realistic call UI banata hai.

Is repository mein jo **website** hai, wo ek single HTML file hai — koi dependency nahi, koi build step nahi — jahan se users seedha APK download kar sakte hain.

---

### ✨ Khoobiyan (Features)

| Khoobee | Tashrih |
|---|---|
| 🖥️ **Asli Jaisi Call Screen** | OriginOS call layout ki tarah, light aur dark dono modes mein, SIM badge, caller naam aur number ke saath |
| ⏱️ **5 Timed Call Slots** | Har slot ka apna waqt, caller, number, SIM, ringtone aur repeat din — restart ke baad bhi zinda rehte hain |
| 🎵 **Apni Ringtone** | System ringtone use karein ya har schedule ke liye alag ringtone chunein. Vibration bhi shamil |
| 🔒 **Answer Lock** | Call tab tak bajti rahe jab tak aap faisla na karein. Decline hamesha foran kaam karta hai |
| ⚡ **Flash Alert** | Ringing ke dauran camera flash ka optional blink, answer ke baad dheema pattern |
| 🛡️ **Privacy Pehle** | Internet nahi, ads nahi, account nahi, analytics nahi. Sab kuch sirf aap ke phone mein |
| 🌐 **Do Zubanen** | English aur Roman Urdu mein poora interface — nav bar se badlein |

---

### 🗂️ Folder ka Dhang (File Structure)

```
Phone-Website/
├── index.html      → Poori website (ek file — koi library, koi internet nahi chahiye)
├── phone.apk       → Signed Android APK (apna APK yahan rakhein)
├── favicon.svg     → Browser tab ka icon
├── _headers        → Netlify / Cloudflare Pages ke liye (APK sahi download ho)
├── .nojekyll       → GitHub Pages ke liye (khali file — delete na karein)
└── README.md       → Ye file
```

---

### 🚀 Publish Karne Ka Tareeqa

#### Qadam 1 — APK Rakhein

Apni signed APK ko `index.html` ke saath rakhein aur uska naam bilkul **`phone.apk`** rakhein.

> Alag naam rakhna chahein to `index.html` ke neeche `APP.file` badal dein.

APK ke baghair Download button **404** dega.

#### Qadam 2 — (Ikhtiyaari) Version aur Checksum

`index.html` ke neeche `APP` object mein ye values set karein:

```javascript
var APP = {
  version: "1.0",         // har naye release par badlein
  file:    "phone.apk",   // APK ka naam
  minAndroid: "8.0",      // minimum Android version
  sha256:  ""             // SHA-256 yahan paste karein
};
```

**Windows par SHA-256 nikalny ka tareeqa (Command Prompt — APK walay folder mein):**

```cmd
certutil -hashfile phone.apk SHA256
```

#### Qadam 3 — Free Mein Publish Karein (koi ek chunein)

| Host | Tareeqa |
|---|---|
| **Netlify** *(sabse aasaan)* | [app.netlify.com/drop](https://app.netlify.com/drop) kholein, free account banayein, poora folder (`phone.apk` samet) drag-and-drop karein — link mil jata hai |
| **GitHub Pages** | GitHub par public repo banayein, saari files upload karein (browser limit **25 MB per file**), phir *Settings › Pages › Source → main / root → Save* — 1–2 minute mein link tayaar |
| **Cloudflare Pages** | *Create a project › Upload assets* — poora folder upload karein |

---

### 🔄 Update Kaise Dein

1. Android Studio mein `versionCode` badhayein (masalan `1` se `2`), **wahi keystore** use karte hue naya signed APK banayein.
2. Naya APK `phone.apk` ke naam se purani file ki jagah rakhein.
3. `index.html` mein `APP.version` badlein (aur `APP.sha256` dobara nikal kar paste karein agar use karte hain).
4. Poora folder dobara upload karein.

---

### 📲 Install Karne Ka Tareeqa (User Ke Liye)

1. **Download karein** — Website par *Download for Android* dabayen. Browser puche to **Keep** chunein.
2. **File kholein** — `phone.apk` download notification ya *Files › Downloads* se kholein.
3. **Install ki ijazat dein** — Pucha jaaye to *"Install unknown apps"* allow karein, phir **Install** dabayen.
4. **Setup mukammal karein** — **Phone › Setup Checklist** kholein aur har item par *Fix* dabayen taake timed calls waqt par aayein.

> **vivo / OriginOS par:** Autostart on karein, high background power use ki ijazat dein, aur Phone ko Recents mein lock karein. App ke andar OriginOS help screen har qadam dikhati hai.

---

### 🔐 Permissions ki Wazahat

| Permission | Kyun chahiye |
|---|---|
| Notifications | Incoming call screen dikhane ke liye |
| Full-screen intent | Lock screen par call kholne ke liye |
| Alarms & exact reminders | Timed calls theek waqt par chalane ke liye |
| Foreground service | Ringtone chalti rakhne ke liye |
| Vibration | Ringing ke dauran vibrate karne ke liye |
| Boot completed | Restart ke baad schedules wapas lagne ke liye |
| Battery optimisation | System ko calls late karne se rokne ke liye |

**Jo kabhi nahi maangi jaati:** Contacts · Call log · Phone state · SMS · Location · Microphone · Camera · Internet

---

### ❓ Aam Sawalon Ke Jawab (FAQ)

<details>
<summary>Kya Phone free hai?</summary>

Ji haan — bilkul free. Na ads, na in-app purchases, na subscription.

</details>

<details>
<summary>Browser ya phone warning kyun dikhata hai?</summary>

Android Google Play se bahar se install hone wali har app par warning deta hai kyunke wo source ki zamanat nahi de sakta. Sirf wahi sources par bharosa karein jo aap jaante hain, aur download page par checksum milayein.

</details>

<details>
<summary>Kya ye asli calls karta ya uthata hai?</summary>

Nahi. Ye sirf apni app ke andar ek call screen dikhata hai. Dialer, contacts ya call log ko bilkul haath nahi lagata.

</details>

<details>
<summary>Phone lock hone par bhi bajega?</summary>

Ji haan — jab app ki Setup Checklist mein sab kuch *Ready* dikh raha ho. vivo / OriginOS par in-app help screen ke extra steps bhi follow karein.

</details>

<details>
<summary>Google Play par kyun nahi hai?</summary>

Google Play par publish karne ke liye paid developer account chahiye ($25 ek baar). Filhal Phone seedha APK ki soorat mein share ho raha hai.

</details>

<details>
<summary>Update ya remove kaise karun?</summary>

- **Update:** Nayi APK download karke purani ke upar install karein.  
- **Remove:** *Settings › Apps › Phone › Uninstall*

</details>

---

### ⚠️ Zimmedari Se Istemal Karein

> Phone **sirf aap ke apne phone ke liye** hai — baat se nikalne, mashq karne ya demo ke liye. Meherbani karke isay asli logon, bankon ya sarkaari idarohn ki naqal karne, ya kisi ko daraane ya dhoka dene ke liye **istemal na karein**. Galat istemal aap ke ilaqe ke qanoon ki khilaf warzi ho sakti hai.

---

### 🛠️ Technology (Kaun Si Cheezein Istemal Huin)

| Tabqa | Technology |
|---|---|
| Website | Plain HTML5 + Vanilla CSS + Vanilla JS (koi dependency nahi) |
| Fonts | Google Fonts — *Inter*, *Libre Caslon Condensed* |
| Icons | Inline SVG |
| Hosting | Netlify / GitHub Pages / Cloudflare Pages |
| Android App | Native Android APK (sideload) |

---

### 👤 Creator

**Zubair Afridi**  
Dil se banaya gaya ❤️ — *© 2026 Phone. vivo, Google ya kisi carrier se koi taalluq nahi. Android, Google LLC ka trademark hai.*
