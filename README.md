![Artboard](https://raw.githubusercontent.com/donoigabriel6-a11y/MyFy-V2/refs/heads/main/Logo.png)
# MyFy V2 🎧

A web music player inspired by Spotify, built with **HTML/CSS/JS**, **Firebase Authentication**, and the **YouTube Data API**.  
MyFy lets users sign in with multiple providers, search YouTube for songs, play local MP3s, and save tracks to a personal library.

---

## 🚀 Live Demo

**MyFy is deployed on GitHub Pages:**

> https://donoigabriel6-a11y.github.io/MyFy-V2/  

(If this link is broken, check that GitHub Pages is enabled for the repo and that `index.html` is in the root.)

---

## ✨ Features

- 🎵 **Featured tab**  
  - Plays local MP3 files bundled with the project (e.g. demo tracks).
- 🔍 **Search tab (YouTube)**  
  - Uses the **YouTube Data API v3** to search for videos and play them in an embedded YouTube player.
- 📚 **Library tab**  
  - Save songs you like. Library is stored per-user using `localStorage` keyed by Firebase `uid`.

- 👤 **Authentication (Firebase)**  
  - Email + password  
  - **Google** sign-in  
  - **GitHub** sign-in  
  - **Yahoo** sign-in  
  - **Phone number** sign-in (SMS code via Firebase Phone Auth)
  - Email verification required for email/password accounts  
  - Password reset via email

- 🛡 **Security & Abuse Protection**
  - Global **reCAPTCHA v2** requirement before logging in or playing songs.
  - Phone sign-up uses an extra invisible reCAPTCHA instance.

- ▶️ **Player**
  - Play/pause, previous, and **skip forward 30 seconds** button.
  - Volume slider & progress bar.
  - Optional “Show video” button to reveal the embedded YouTube player.
  - Simple “Lyrics & Info” panel that shows safe text and a link to the YouTube video (no copyrighted lyrics).

---

## 🧱 Tech Stack

- **Frontend:** HTML, CSS, vanilla JavaScript
- **Auth & SMS:** Firebase Authentication
- **Media search & playback:** YouTube Data API v3 + YouTube IFrame Player API
- **Bot protection:** Google reCAPTCHA v2
- **Hosting:** GitHub Pages

---

## ⚙️ Getting Started (Your Own Copy)

### 1. Clone the repo

```bash
git clone https://github.com/donoigabriel6-a11y/MyFy-V2.git
cd MyFy-V2
```

### 2. Create a Firebase project

1. Go to [Firebase Console](https://console.firebase.google.com/).
2. Create a new project (or reuse your existing MyFy project).
3. Add a **Web app** and copy the config:

   ```js
   const firebaseConfig = {
     apiKey: "...",
     authDomain: "...",
     projectId: "...",
     storageBucket: "...",
     messagingSenderId: "...",
     appId: "...",
     measurementId: "..."
   };
   ```

4. In **Authentication → Sign-in method**, enable:
   - Email/Password
   - Google
   - GitHub (requires client ID/secret from GitHub Developer Settings)
   - Yahoo (requires client ID/secret from Yahoo Developer portal)
   - Phone  

5. In the Firebase Console, add the domains you are using (GitHub Pages URL, custom domain) to the **Authorized domains** list.

> In `index.html`, the Firebase config is already hard-coded for the current project.  
> If you fork this, replace those values with your own Firebase config.

### 3. Set up YouTube Data API v3

1. Go to [Google Cloud Console](https://console.cloud.google.com/).
2. Select the same project used for Firebase (or another one if you prefer).
3. **Enable** the API:
   - `APIs & Services → Library → YouTube Data API v3 → Enable`
4. **Create an API key** in `APIs & Services → Credentials`.
5. Restrict the key to your website:
   - Application restrictions: **HTTP referrers (websites)**
   - Add your URLs, e.g.  
     `https://donoigabriel6-a11y.github.io/*`  
     `https://your-custom-domain.com/*`
6. In `index.html`, set:

   ```js
   const YT_API_KEY = "YOUR_YOUTUBE_API_KEY_HERE";
   ```

> If you see `BILLING_NOT_ENABLED` in the console, you must attach a billing account to the Google Cloud project even if you stay within the free quota.

### 4. Set up reCAPTCHA v2

1. Go to [Google reCAPTCHA](https://www.google.com/recaptcha/admin/create).
2. Choose reCAPTCHA **v2** (“I’m not a robot” or invisible) and add your domains.
3. Copy your **site key**.
4. In `index.html`, update:

   ```html
   <div class="g-recaptcha"
        data-sitekey="YOUR_RECAPTCHA_SITE_KEY_HERE"
        data-callback="onCaptchaSuccess"></div>
   ```

5. The phone auth flow also uses an extra invisible reCAPTCHA container with ID `phoneRecaptcha`.

### 5. Local featured audio

The repo currently includes some sample MP3 files in the root directory.  
You can:

- Replace them with your **own** audio files, or
- Remove them and update the `featuredTracks` array in `index.html` so it only uses YouTube videos.

> ⚠️ If you keep songs you don’t have rights to redistribute, consider making the repo private or replacing those tracks with royalty-free or self-made audio.

---

## 🌐 Deploying to GitHub Pages

1. Commit all changes and push to GitHub.
2. In your repo, go to **Settings → Pages**.
3. Set:
   - **Source:** `Deploy from a branch`
   - **Branch:** `main` (or `master`), folder `/ (root)`
4. Save. GitHub will build and host the site.
5. Visit the URL it shows, e.g.:

   ```text
   https://<your-username>.github.io/MyFy-V2/
   ```

---

## 🧩 Common Issues

### `INVALID_LOGIN_CREDENTIALS`

- Usually means wrong email/password.
- Could also happen if the user tries to sign in to a provider you haven’t enabled in Firebase.

### `BILLING_NOT_ENABLED` (YouTube API)

- Your YouTube API call returns:

  ```json
  { "error": { "code": 400, "message": "BILLING_NOT_ENABLED", ... } }
  ```

- Fix: In Google Cloud Console, attach a **billing account** to the project that owns the YouTube API key.

### reCAPTCHA errors

- Make sure the **site key** in `index.html` matches the one listed for your domain in the reCAPTCHA admin.
- Check that the domain you’re loading the site from is listed in the reCAPTCHA allowed domains.

---

## 📄 License

This project is licensed under the **GPL-3.0 License**.  
See the [`LICENSE`](LICENSE) file for details.

---

## 🆘 Support

Contact **myfyoffical@yahoo.com** for assistance.
