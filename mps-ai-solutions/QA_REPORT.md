# MPS AI Solutions — Production & Quality Report

**Final video:** `renders/MPS_AI_Solutions_HyperFrames_VO.mp4` — H.264 (yuv420p), 1920×1080, 30 fps, **57.6 s**, AAC stereo. Rendered locally with HyperFrames CLI 0.8.x (headless Chrome + FFmpeg), no paid or hosted services.

## Duration
Target was ~55 s. The narration measured longer than the storyboard windows, and the brief says to adjust the timeline rather than speed the voice up, so scenes were re-timed from the measured speech: 9.2 / 8.8 / 9.4 / 11.4 / 10.2 / 8.6 s = 57.6 s.

## Voice-over
- **Method:** local neural TTS (Kokoro-82M via the HyperFrames toolchain), male voice `am_michael`, speed 0.96 (slower than default, never accelerated), longer sentence pauses for the "Your business. Smarter with AI." beat. No paid API used.
- **Pronunciation control:** AI, MPS, SAP, HR and "resume" (re-zoo-may) were set phonetically by hand.
- **Measured narration lengths:** S1 5.85 s · S2 6.61 s · S3 7.03 s · S4 9.38 s · S5 7.94 s · S6 5.62 s.
- **Loudness:** narration normalised to −16 LUFS per clip; full mix measures −16.5 LUFS integrated, −1.6 dBTP true peak, LRA 5.0 LU. No clipping.
- **Assets kept separate:** `assets/vo/scene1–6.wav` (raw), `assets/vo/scene1–6.mp3` (normalised), `assets/MPS_AI_Solutions_Voiceover.wav` (full timeline), `assets/music.mp3`, `assets/sfx_bed.mp3`, individual SFX in `assets/sfx/` plus `sfx_cues.json`.

## Audio design
- **Music:** original synthesised cinematic electronic bed (no samples, no vocals, so no licensing issues), pre-ducked by ~9 dB under each narration window with 0.35 s ramps; fades out to silence for a clean loop.
- **SFX:** 30 restrained cues (portal sweep, soft whooshes, interface ticks, department pings, network pulse, brand chord, reverse sweep on the ring contraction).

## Audio ↔ animation synchronisation
Word times were estimated by synthesising the narration prefix before each key phrase (accuracy roughly ±0.15 s):
| Spoken phrase | Time | Visual event |
|---|---|---|
| "alongside your team" | 3.4 s | AI figure connects to the business dashboards; "Alongside" headline |
| "smarter, more connected workflows" | 12.2 s | disconnected tasks absorbed by the AI core → unified dashboard |
| management / marketing / finance / operations | 19.6 / 20.4 / 20.9 / 21.8 s | each department node activates |
| "AI-assisted resume screening" / "voice interviews" / "HR teams decide" | 30.6 / 33.0 / 35.8 s | screening view / voice-interview view / HR review |
| "Automate documents" / "connect business systems" / "customised AI solutions" | 39.7 / 41.3 / 43.7 s | document processing / workflow routing / full network connects |
| "Your business." / "Smarter with AI." / "MPS Solutions" | 50.2 / 51.3 / 54.1 s | headline lines / MPS logo reveal |

## Checks performed
- `hyperframes check` (lint, runtime, layout, motion, contrast): 0 errors; text contrast issues found and fixed.
- ~35 timeline snapshots reviewed across all scenes and transitions; 6 final previews extracted from the delivered MP4 (`previews/`).
- Seamless restart: first and last frames match (same background and light spark; mean pixel difference 0.085/255). Final narration ends at 55.8 s, before the ring contracts.
- Safe margins: text kept inside ~100 px; contact block on a dark glass bar.

## Issues found and corrected
- Transition edge-glow visible at frame 0 → fixed (opacity set only at its transition time).
- Scene 2 headline collided with the MPS logo → moved.
- Department and capability text overflowed cards in scenes 3 and 5 → shortened.
- Low-contrast captions in scene 5 → lightened.
- Closing headline touched the ring → ring shifted, headline resized.
- Scene 4 pipeline now shows candidates advancing from Applied → In review.

## Limitations — please read
1. **Voice quality:** this is the best *local* neural voice available here, but it is still synthetic. It is clear and warm, not human-grade. For the exhibition I recommend replacing `assets/vo/scene*.mp3` with a studio or premium-TTS recording using the same scene lengths; the timeline is built so only the audio files need swapping.
2. **Pronunciation not machine-verified, and I could not listen:** the offline Whisper model could not be downloaded in this environment, so I could not transcribe the output back. Please audition especially "MPS", "SAP", "resume" and "customised".
3. **Reference materials:** the six-panel graphic, the Nike video and the MPS product-knowledge files were **not attached** to the message. Visuals and claims follow the written storyboard only. Please review the scene 3 and scene 5 bullet text against your product documents.
4. **People/photos:** realistic professionals are the photos you supplied earlier (reused); no new photography was generated. The SMILE portal screen is an illustrative reconstruction with fictional names and data, labelled as such.
5. **Skyline:** drawn as vector art (Marina Bay Sands, ArtScience Museum, towers), stylised rather than photographic.
6. **SAP Business One assistant, knowledge assistant and dashboard** are illustrative demonstrations, labelled "illustrative".
7. Synchronisation times are estimates (±0.15 s) from prefix synthesis, not word-level alignment.
