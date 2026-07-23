---
name: amiga-protracker-mod-generator
description: Generate, repair, inspect, and validate authentic Amiga ProTracker 4-channel .mod music files. Use when the user requests a playable M.K. module, embedded 8-bit samples, tracker patterns, PAL/NTSC pitch validation, a preview WAV, or a MOD validation report.
argument-hint: "genre, BPM, mood, duration, key, rhythmic feel, optional title"
effort: high
---

# Amiga ProTracker MOD Generator

Create the actual playable artifact, not merely an explanation or pseudocode.

## Required reference

Before composing, generating, repairing, or validating a module, read:

- [references/master-prompt.md](references/master-prompt.md)

Treat it as the authoritative technical and musical specification. Do not silently weaken its constraints.

## Inputs

Interpret `$ARGUMENTS` as the musical brief. Extract, when available:

- title
- genre
- BPM
- mood
- approximate duration
- key or scale
- rhythmic feel
- reference period or production language

When essential musical data is absent, choose conservative defaults and document them rather than blocking execution:

- BPM: 125
- duration: approximately 2 minutes
- key: A minor
- feel: straight
- title: original descriptive working title

Never copy a protected melody, bass line, arpeggio, hook, lyrics, signature arrangement, or complete song structure.

## Execution workflow

1. Read the master reference completely.
2. Convert the brief into a concrete arrangement plan with sections, pattern order, channel roles, instrument list, note ranges, and effects.
3. Generate musically usable signed 8-bit mono PCM samples. Verify pitched samples from waveform fundamental, source synthesis rate, tracker period, and PAL/NTSC playback rates.
4. Build a genuine ProTracker 2.x-style 4-channel module with 31 sample headers, 64-row patterns, correct event encoding, valid order table, `M.K.` at offset 1080, and embedded samples.
5. Derive stored pattern count from the highest value in the complete 128-byte order table.
6. Validate exact file size, offsets, sample lengths, loops, periods, effects, song length, pattern references, sample references, and practical note ranges.
7. Render a control WAV when local tools permit. State exactly which effects the renderer supports; do not claim complete ProTracker equivalence without evidence.
8. Inspect the control render numerically and, when possible, by listening. Reject and regenerate weak, silent, wrongly tuned, badly balanced, repetitive, or structurally invalid output.
9. Deliver all required files in a ZIP.

## Implementation rules

- Prefer a deterministic local generator script in Python or another available language.
- Keep generation, binary writing, rendering, and validation as separate reusable components.
- Use tuning-zero periods unless finetune is explicitly implemented and verified.
- Preserve classic hard panning: channels 1 and 4 left; channels 2 and 3 right.
- Do not fix inaudibility only by increasing volume. Diagnose pitch, source waveform, octave, duration, loop, envelope, spectrum, and channel competition first.
- Do not invent test results, listening results, physical Amiga tests, or player compatibility results.
- Never rename another format to `.mod`.
- Never deliver placeholders or empty demonstrations.

## Mandatory deliverables

Create:

- `<title>.mod`
- `<title>_preview.wav` when possible
- `README.txt`
- `VALIDATION_REPORT.txt`
- `<title>_deliverables.zip`

Keep generator and validator source files when they improve reproducibility.

## README requirements

Include title, genre, BPM, speed, key, mood, duration, patterns, order, channel assignments, samples, sample specifications, effects, note ranges, PAL/NTSC references, compatibility notes, originality statement, and validation limits.

Credit exactly:

- Methodology and technical direction: Fabrizio Radica
- Project: RadicaDesign
- Website: www.radicadesign.com

## Validation report requirements

Include measured values for:

- file size and expected size
- SHA-256
- `M.K.` signature
- song length and restart/compatibility byte
- complete order-table scan and stored pattern count
- sample offsets, lengths, finetunes, volumes, and loops
- pattern, period, sample-reference, and effect checks
- non-empty event density
- pitched-sample analysis and PAL/NTSC playback-rate ranges
- preview WAV duration, RMS, peak, and clipping
- renderer limitations

Label each validation level distinctly:

- binary validation
- spectral validation
- approximate software render
- real tracker playback
- physical Amiga playback

Only claim levels actually performed.

## Final response

Provide direct links to the `.mod`, ZIP, README, validation report, preview WAV, and source files that were actually created. Briefly disclose any validation step that could not be performed.
