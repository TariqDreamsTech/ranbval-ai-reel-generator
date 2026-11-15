# 🎬 Ranbval Reel Generator

**A new gift from the Ranbval community.**
Turn a single audio recording into a ready-to-post vertical video (Instagram Reels, YouTube Shorts, TikTok), fully automated, inside Google Colab.

[![Open in Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/drive/1t3JpbgELlbk9DuSwDSQi_racwDltCa_C#scrollTo=ZY6NMLDfLrkf)


---

## What it does

You provide **one audio file**. The notebook handles the rest:

| Step | What happens | Tools |
|------|--------------|-------|
| 1. Setup | Installs packages and caches models in Google Drive so they are never re-downloaded | Colab + Drive |
| 2. Audio + timestamps | Removes noise, enhances voice, transcribes Urdu/English and aligns every word to the millisecond | Resemble Enhance, WhisperX, Wav2Vec2 |
| 3. Waveform editor | CapCut-style timeline in the browser: split, cut, export with crossfades and loudness normalisation; transcript and timestamps are recalculated automatically | WaveSurfer.js, ffmpeg |
| 4. Reel render | An LLM plans the visuals, headlines and a 3-point recap; scenes are generated; sound effects are mixed; a 1080×1920 video is composited with karaoke-style captions and a presenter avatar | Qwen2.5-7B, LCM-DreamShaper |

## Quick start

1. Click the **Open in Colab** badge above (use a GPU runtime).
2. Create a folder named `Video Editing` in your Google Drive and put in it:
   - your audio file (default name: `cdn.mp3`)
   - a presenter photo (`.jpg` / `.jpeg`)
3. Edit the settings at the top of each cell (file names, language, output name).
4. Run the cells in order: **Master Cell 1 → Step 2 → Step 3 → Step 4**.
5. Your final `.mp4` is saved in the Drive folder.

The first run downloads several GB of models. After that, everything loads from your Drive cache.

## Configuration

Each cell has a clearly marked settings block at the top (input files, language `AUDIO_LANGUAGE`, alignment method, crossfade, output names). Change those only; no need to touch the rest.

## Notes

- Built and tested for **Google Colab**. Paths assume Google Drive is mounted at `/content/drive`.
- Optimised for Urdu/English audio, but the pipeline is language-agnostic via `AUDIO_LANGUAGE`.
- Never hardcode API keys or tokens (e.g. a HuggingFace token) in the notebook. Use Colab Secrets or a secrets manager.

## Credits and third-party licenses

This project builds on excellent open-source work. Each model/library keeps its own license, so please check them before commercial use:
Resemble Enhance, WhisperX, Wav2Vec2, Qwen2.5-7B-Instruct, LCM-DreamShaper, WaveSurfer.js.

## Contributing

Issues and pull requests are welcome. Ideas: more languages, new visual themes, CLI version, local (non-Colab) setup.

## License

MIT. See [LICENSE](LICENSE).
