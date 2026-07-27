# Persian Subtitle Studio 🎬

**[فارسی](README.fa.md)** · English

Transcribe English videos and generate Persian (فارسی) subtitles, entirely in your browser. Your video never leaves your device.

**Try it live:** [https://github.com/Greenland-S/persian-subtitle-studio](https://greenland-s.github.io/persian-subtitle-studio/)

## Features

- 🎙️ Speech recognition with OpenAI Whisper — locally via Transformers.js, or in the cloud with Groq / Cloudflare Workers AI (nothing to download)
- 🌐 Translation with M2M-100 (local & private) or the Gemini API (cloud, best quality)
- ✂️ Sentence-by-sentence subtitles — one sentence on screen at a time, never a wall of text
- 🌍 Bilingual interface — switch the page between English and Persian at any time, with full right-to-left layout
- 🎞️ Live subtitle preview with adjustable styling (size, text color, background & opacity, position)
- ⏯️ Playback helpers — jump to previous/next subtitle line, ±5s, speed control, full screen with subtitles
- ✏️ Inline editing of Persian subtitle lines
- ⏱️ Live elapsed timer that starts the moment you press Generate and resets for every new file
- 💾 Resume after errors — finished steps are saved in your browser, so a failed run continues where it stopped
- 📅 Export as Persian .srt / .vtt or English .srt

## How to use

1. Open the app and drop in an English video (MP4, WebM, MOV) or audio file (MP3, WAV, M4A).
2. Pick a transcription model and a translation option under **Settings**.
3. Click **Generate Persian subtitles** and watch the per-step progress.
4. Preview the result on the video, edit any Persian line inline, then download your subtitle file.

Use the language dropdown at the top of the page to switch the whole interface between **English** and **فارسی**. Your choice is remembered in your browser.

## Choosing a transcription model

| Option | Runs | Download | Needs |
| --- | --- | --- | --- |
| Whisper Tiny / Base / Small | In your browser | ~40 / ~80 / ~250 MB (once) | Nothing |
| Whisper Large v3 (Groq) | Groq cloud | None | Free Groq API key |
| Whisper Large v3 Turbo (Cloudflare) | Your own Cloudflare Worker | None | Free Cloudflare account + Worker |

With the cloud options only the extracted **audio track** — never the video — is sent to the provider.

## Getting a free Gemini API key

The **Gemini API** translation option gives the best quality, but needs a free API key:

1. Go to [Google AI Studio](https://aistudio.google.com/apikey) and sign in with any Google account.
2. Click **Create API key** (if asked, let it create a new project automatically).
3. Copy the key that appears.
4. In Persian Subtitle Studio, choose **Gemini API** as the translation option and paste the key into the API key field.

Notes:

- The free tier is enough for subtitling, no credit card required.
- Your key is stored **only in your own browser** (never uploaded anywhere).
- With Gemini, only the transcribed English **text** is sent to Google, never your video or audio.
- Keep your key private: don't commit it to GitHub or share it publicly.

## Getting a free Groq API key (optional)

Groq runs Whisper Large v3 in the cloud, so there is nothing to download and transcription is fast:

1. Go to [console.groq.com/keys](https://console.groq.com/keys) and sign in (no credit card needed).
2. Create a key and copy it.
3. Choose **Whisper Large v3 — Groq cloud** as the transcription model and paste the key into Settings.

## Using Cloudflare Workers AI (optional)

Cloudflare's API can't be called directly from a web page, so this option talks to a tiny Worker on your own free account. The app shows the complete Worker code and a 3-minute setup guide under **Settings**:

1. Create a Worker in the Cloudflare dashboard and paste in the code shown in the app.
2. Add a **Workers AI** binding named exactly `AI`, then deploy again.
3. Optionally add a secret named `APP_SECRET` and type the same password into the app, so strangers can't use your quota.
4. Paste your Worker URL into Settings.

The free Workers plan includes 10,000 neurons per day (roughly 3 hours of audio) and resets at 00:00 UTC.

## Privacy

Everything runs in your browser. With the local models, nothing is sent anywhere — the AI models are downloaded once from Hugging Face and cached. With the Gemini option, only the transcribed **text** is sent to Google. With the Groq or Cloudflare options, only the extracted **audio track** is sent to that provider. Your video file itself is never uploaded, and all API keys stay in your browser's local storage.

## Run it yourself

Just open `index.html` in any modern browser — no build step, no server needed.

You need a browser with WebAssembly and Web Audio support (recent Chrome, Edge, Firefox, or Safari). The first local run downloads the AI models, so an internet connection is needed once.

## License

MIT
