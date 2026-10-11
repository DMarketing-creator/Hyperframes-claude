# MPS InvoiceNow — Rendering & QA Summary

**Deliverable:** `renders/MPS_InvoiceNow_HyperFrames.mp4`
H.264 (yuv420p) · 1920×1080 · 30 fps · 45.0 s · AAC stereo (instrumental only, no narration, no subtitles, no watermark)
Rendered locally with HyperFrames CLI 0.8.147 (headless Chrome + FFmpeg, no hosted/paid services), `--fps 30 --quality high`, ~4m50s on a software-GPU container.

## Project
`index.html` (single composition, GSAP 3.14.2 vendored locally, one paused seekable timeline), `assets/` (MPS logos, SAP Business One logo, synthesized score), `previews/` (six full-resolution scene frames taken from the final MP4).
Every scene is rebuilt from separately animated HTML/CSS/SVG layers (skyline, rings, laptop + UI, invoices, Peppol sphere, icons). The supplied six-panel graphic was used only as a visual reference; none of it appears in the video.

## Motion techniques used
1. Circular expansion/reveal: opening light → ring; clip-path radial reveals into scenes 2, 4 and 6.
2. Layered dimensional camera movement: camera pass through the ring, desk pan with parallax layers, push-ins on scenes 1, 4, 5, 6.
3. Animated UI components: laptop interface hotspots, benefit rows with drawn connector lines, count-free e-invoice assembly.
4. Moving invoice particles and network paths: desk documents streamed into one e-invoice (scene 2); seller → Peppol → buyer data streams with synchronised sphere pulses (scene 3); energy line activating five icons (scene 5).
Plus masked kinetic typography and shape-led transitions (radial reveals, an inset wipe that expands out of the invoice, a horizontal line-expansion reveal, and a line-to-ring swoosh).

## Checks run
| Check | Result |
|---|---|
| `hyperframes check` (lint, runtime, layout, motion, contrast) | Passed — 0 errors; 29/29 text contrast checks at WCAG AA; remaining warnings are structural suggestions (single-file composition) |
| Seek-safety | Path-following particles use build-time sampled points (lint flagged DOM measurement in callbacks; fixed) |
| Snapshots | ~30 frames across all scenes/transitions inspected during development; 6 final previews extracted from the MP4 |
| Fonts | Inter, deterministic @font-face injected by the renderer (Calibri not available to the renderer) |
| Safe margins | Headlines/body copy stay inside ~100 px margins; contact details legible on a dark glass bar |
| Loop | First and last frames match (same #03152F background and light spark; mean pixel difference 0.08/255) |
| Audio | Present, max −6.0 dB, no clipping |

## Issues found and fixed during QA
- Scene 1 headline overlapped the laptop → laptop, ring and cards shifted right; headline resized.
- Scene 2 sub-copy phrases overlapped and an email icon covered them → single flex row, icon moved.
- Scene 4 headline touched the laptop → headline reduced, laptop shifted.
- Scene 5 Marina Bay tower covered the fifth label → skyline lowered; icon row raised.
- Scene 5→6: added the energy-line swoosh that becomes the final ring.

## Content-accuracy notes
- Interfaces are labelled “Illustrative interface”; no real SAP screen is claimed. The SAP Business One logo is the supplied asset.
- No savings figures, funding guarantees or testimonials. The IMDA Go Digital badge was **not** included because its text states a grant-support figure; add it only if MPS confirms it applies to this solution.
- “Peppol” is a plain wordmark, not the official Peppol logo.
- Supplied MPS logos are 180×96 px, so they are shown at ≤200 px wide to stay sharp.
- The Nike benchmark video and the Booth Staff Product Overview were not received; the brief text and the six-panel graphic were used instead.
