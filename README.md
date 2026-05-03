# subMatik

> AI subtitle engine — drop a video, get studio-grade subtitles in any language. 100% local, no cloud, no subscription.

[![Latest release](https://img.shields.io/github/v/release/burskozbekov/submatik-releases?style=flat-square&label=version)](https://github.com/burskozbekov/submatik-releases/releases/latest)
[![Platforms](https://img.shields.io/badge/platform-Windows%20%7C%20macOS-blue?style=flat-square)](#download)
[![License](https://img.shields.io/badge/license-Proprietary-lightgrey?style=flat-square)](#license)

---

## Download

| Platform | Installer | Patch (existing users) |
|----------|-----------|------------------------|
| **Windows** (10/11, 64-bit) | [`subMatik_v1.9.1_Setup.exe`](https://github.com/burskozbekov/submatik-releases/releases/latest/download/subMatik_v1.9.1_Setup.exe) | [`subMatik_v1.9.1_patch.zip`](https://github.com/burskozbekov/submatik-releases/releases/latest/download/subMatik_v1.9.1_patch.zip) |
| **macOS** (Apple Silicon) | [`subMatik_v1.9.1_apple-silicon.dmg`](https://github.com/burskozbekov/submatik-releases/releases/latest/download/subMatik_v1.9.1_apple-silicon.dmg) | `patch_v1.8_to_v1.9.1_apple-silicon.zip` |

Want a 30-day free trial? Visit **[catheadai.com/submatik](https://catheadai.com/submatik)** — no credit card required.

---

## What it does

- **Transcribe** any video or audio in 100+ languages with OpenAI Whisper (turbo / large-v3 models)
- **Translate** subtitles into 30+ target languages via Google or DeepL
- **Sync precision** down to ~50 ms with bundled WhisperX forced alignment (Precise Mode)
- **Export** SRT, WebVTT, ASS/SSA, plain text, bilingual SRT, or burn-in MP4
- **Cut XML** for Adobe Premiere — auto-removes silences and filler words from your edit timeline
- **Premiere JSON** for cross-tool workflows
- Runs **fully offline** once models are downloaded — your audio never leaves the machine

---

## Highlights of v1.9.1

**Subtitle sync overhaul**
- Lead-in time so the eye reads before the ear hears (broadcast-grade)
- Word-level realignment using Whisper word timestamps
- Configurable max-hold during silence (default 3 s)
- Manual global offset for fine adjustment

**Quality**
- Hallucination filter removes Whisper's stray "Thanks for watching" / `[Music]` lines
- Custom vocabulary primes Whisper for brand names, technical terms, proper nouns

**Precise Mode**
- WhisperX forced alignment is now bundled — works offline, no extra install
- English alignment model ships in the installer; Turkish prefetches in the background on first launch

**Output**
- New WebVTT (`.vtt`), plain text (`.txt`), and ffmpeg burn-in MP4 outputs
- Re-translate button: pick any existing `.srt`, translate it into a new language without re-running Whisper

**Languages**
- Added Kurdish (Kurmanji + Sorani) as translation targets
- Translation engine auto-fallback when DeepL doesn't support the chosen target

**Reliability**
- Auto-update notifications on launch (with "Skip this version" / "Remind later")
- Optional anonymous crash reporting (off by default)
- 64-bit installer; new installs land in `C:\Program Files\subMatik\` (no more `(x86)`)

See the in-app **What's new** dialog on first launch for the full tour.

---

## System requirements

| Component | Minimum | Recommended |
|-----------|---------|-------------|
| OS        | Windows 10 64-bit / macOS 12 Apple Silicon | Windows 11 / macOS 14+ |
| RAM       | 8 GB | 16 GB |
| Disk      | 6 GB free (installer + cached models) | 10 GB |
| GPU       | None (CPU works) | NVIDIA CUDA-capable GPU for ~5x speed (Windows) |
| Internet  | Required for first model download + translation | — |

`turbo` model = 809 MB - `large-v3` = 3.1 GB - WhisperX alignment ~360 MB (English, bundled) + 1.2 GB (Turkish, auto-prefetched)

---

## How it works

1. **Drop** a media file (MP4, MKV, MP3, WAV, M4A, MOV, ...) into the drop zone.
2. **Pick** a target subtitle language and translation engine.
3. **Run** — subMatik runs Whisper locally on your machine, translates segment-by-segment, and writes:
   - `<filename>_<lang>.srt`
   - Optional: WebVTT, plain text, ASS/SSA, bilingual SRT, burn-in MP4, Premiere JSON, Cut XML
4. **Done** — output folder opens automatically.

Privacy: audio and transcripts never leave your computer unless translation requires the network.

---

## Roadmap (planned)

- Website localization in DE / ES / FR / IT (parts already keyed via `data-i18n`)
- Bigger Kurdish support: investigate community wav2vec2 alignment models
- Larger model picker: `large-v3` Q4 quantized variant for low-RAM machines
- Speaker diarization (label different speakers in the SRT)

Suggestions and bug reports — [open an issue](https://github.com/burskozbekov/submatik-releases/issues) or e-mail us via [catheadai.com](https://catheadai.com).

---

## Changelog

### v1.9.1 — 2026-05
- Sync: max-hold during silence (default 3 s), configurable
- Languages: Kurdish (`ku`, `ckb`) translation targets
- Auto-update check on launch (silent, dismissable)
- Optional Sentry crash reporting (opt-in via `SUBMATIK_SENTRY_DSN`)
- "What's new" dialog after upgrade
- 64-bit installer (`Program Files\subMatik\`)
- Source-language dropdown filtered to Whisper-supported languages
- DeepL — Google graceful fallback when target is unsupported

### v1.9 — 2026-05
- WhisperX Precise Mode bundled (forced wav2vec2 alignment)
- English alignment model bundled (offline-ready)
- Turkish alignment model background prefetch
- Subtitle sync improvements: lead-in, word-realignment, manual offset
- Hallucination filter
- Custom vocabulary / hotwords (Whisper `initial_prompt`)
- WebVTT, TXT, ffmpeg burn-in outputs
- Re-translate button — translate an existing SRT to a new language
- Header layout fix (title no longer clipped)
- nltk / pydoc fix (no first-launch crash)
- Cache redirected to a writable `%APPDATA%\subMatik\align_cache\`

### v1.8 — 2026-04
- Trial system (30 days, machine-bound)
- Resizable window, taller controls panel
- Turkish I/dotted-I casing fix in transcripts
- Filename overflow fix (drop zone + status bar)
- Misc UI polish

---

## License

subMatik is commercial software. Buy or start a 30-day trial at **[catheadai.com/submatik](https://catheadai.com/submatik)**.
Licensing is handled by [Lemon Squeezy](https://lemonsqueezy.com/) and bound per machine.

For business licensing, OEM, or partnerships — contact via [catheadai.com](https://catheadai.com).

---

Made with care by **CatHead AI** — Bursa.
