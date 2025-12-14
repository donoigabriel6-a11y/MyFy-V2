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

