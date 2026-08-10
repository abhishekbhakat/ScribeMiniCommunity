<p align="center">
  <img src="logo.svg" width="128" height="128" alt="ScribeMini Logo">
</p>

<h1 align="center">ScribeMini</h1>

<p align="center">A minimal macOS menu bar app for voice transcription with AI enhancement and real-time meeting recording.</p>

<p align="center">
  <a href="#download">Download</a>
  &nbsp;&bull;&nbsp;
  <a href="#features">Features</a>
  &nbsp;&bull;&nbsp;
  <a href="#usage">Usage</a>
  &nbsp;&bull;&nbsp;
  <a href="#configuration">Configuration</a>
  &nbsp;&bull;&nbsp;
  <a href="#requirements">Requirements</a>
</p>

---

## Download

Get the latest release from [Releases](../../releases).

Choose the DMG that matches your Mac:
- **arm64** for Apple Silicon (M1/M2/M3/M4)
- **x64** for Intel-based Macs

## Features

### Quick Transcription

Press a hotkey, speak, press again to stop. ScribeMini transcribes your voice with Sarvam Saaras and types the result at your cursor. Optional AI enhancement cleans up filler words, fixes punctuation, and converts spoken numbers to digits.

### Meeting Recording

Record long meetings with **real-time streaming transcription**. ScribeMini captures audio and transcribes it live via Sarvam's WebSocket API, so you see the transcript as the meeting progresses. Meetings open in the built-in Meetings browser with pause/resume and reconnect support.

After the live draft is saved, an optional **batch enhance** pass can reprocess the audio with speaker diarization and attach speaker labels.

Choose what audio to capture:

| Source | What it records | Permission |
|--------|-----------------|------------|
| **Microphone** | Your voice | Microphone |
| **System Audio** | Other participants, media playback | Screen Recording |
| **Microphone + System Audio** | Both sides of the conversation | Microphone + Screen Recording |

System audio capture uses ScreenCaptureKit. ScribeMini captures audio only — no screen video is recorded. Headphones are recommended to avoid echo.

### Transcription

- **Sarvam AI** only (`saaras:v4` by default)
- Modes: Transcribe, Translate, Verbatim, Transliterate, Code-mix (default)
- Indian languages and English
- Quick transcription uses REST; meetings use the WebSocket stream

### AI Features

Optional, and independent of each other:
- **Enhance quick transcription** — polish dictation before typing it into the focused app
- **Generate meeting summaries** — powers the Generate Summary button in the Meetings browser

Providers: OpenAI (Responses API or Chat Completion), or Anthropic (Messages API).

### Speaker Profiles

Define named profiles with project jargon so AI summaries spell domain terms correctly. Assign a default profile in Meeting settings; override per meeting in the Speakers or Summary tab.

## Usage

### Quick Transcription

1. Press `Option + Space` (default hotkey)
2. Speak
3. Press the hotkey again to stop
4. Transcribed text is typed at your cursor

### Meeting Recording

1. Press the meeting hotkey (default: `Shift + Command + F`)
2. ScribeMini starts recording and streaming transcription
3. Press the meeting hotkey again to stop
4. The meeting is saved to the Meetings library; optional clipboard / Markdown export follows your settings

The two hotkeys are mutually exclusive — you can't start a meeting while quick transcription is active, and vice versa.

### Meetings Library

Every meeting is stored under:

```text
~/Music/ScribeMini/Meetings/
```

Open the Meetings browser from the menu bar to review live drafts, final transcripts, speakers, and summaries.

## Configuration

Open Settings from the menu bar icon or press `Command + ,`.

### General

- Quick transcription hotkey (customizable)
- Enable/disable the quick hotkey

### Transcription

- Model (default `saaras:v4`)
- Mode and language
- API subscription key (Keychain; sent as `api-subscription-key`)
- REST base URL and path (advanced)

### AI

- Toggle quick-transcription enhancement
- Toggle meeting summaries
- Shared provider: OpenAI Responses, Chat Completion, or Anthropic
- Base URL, model, and API key (Keychain)
- Separate system prompts for dictation polish and meeting summaries

### Meetings

- Meeting hotkey (customizable)
- Live transcription mode (Transcribe, Translate, Verbatim, Transliterate, Code-mix)
- Default speaker profile
- Audio source: Microphone, System Audio, or Both
- Enhance with speaker diarization (on by default), with expected speaker count (Auto or 2–8)
- Extra delivery: Meetings library only, also clipboard, also Markdown export, or clipboard + Markdown
- Optional Markdown export folder
- Retention: keep the last N meetings (default 25; range 5–100). Older meetings (transcript + audio) are deleted when a new recording starts.
- Advanced: WebSocket and Batch API endpoints

### Profiles

- Create and edit speaker profiles
- Project names and jargon for AI summaries

### About

- App version and links

## Requirements

- macOS 26+
- Sarvam API key
- Microphone permission (required)
- Accessibility permission (required for global hotkeys and typing)
- Screen Recording permission (optional, only for system audio capture in meetings)
- AI provider API key (optional, only if you enable enhancement or summaries)

## Permissions

On first launch, ScribeMini requests:

1. **Microphone** — for voice input
2. **Accessibility** — for global hotkeys and typing text into apps
3. **Screen Recording** (optional) — for system audio capture in meetings

Screen Recording is optional and only needed if you select System Audio or Microphone + System Audio in meeting settings. ScribeMini uses this permission only for audio — no screen video is ever recorded.

## Issues

Report bugs via [Issues](../../issues).
