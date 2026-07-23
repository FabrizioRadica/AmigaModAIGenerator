# AMIGA PROTRACKER MOD MUSIC GENERATION PROMPT — MASTER UPDATED EDITION

## Project information

**Concept & methodology:** Fabrizio Radica  
**Project:** RadicaDesign  
**Professional profile:** Developer, Unity 3D programmer, VR/AR specialist, AI mentor and instructor  
**Website:** www.radicadesign.com  

---

## 1. Purpose

Generate a complete, playable, musically convincing and technically correct Amiga ProTracker `.mod` file.

The result must be a genuine classic 4-channel ProTracker module containing:

- valid `M.K.` signature
- 4 Paula audio channels
- up to 31 embedded 8-bit mono samples
- valid sample headers
- valid song order
- valid pattern data
- correct sample offsets
- correct periods
- correct effects
- coherent arrangement
- balanced mix
- musically usable samples

Do not generate:

- a fake `.mod`
- a MIDI renamed as `.mod`
- an empty or placeholder file
- a structurally valid but musically unusable demonstration
- a file with inaudible, wrongly tuned or badly looped instruments
- a generic sequence with repeated patterns and no development

The final result must be directly playable with:

- ProTracker-compatible Amiga software
- OpenMPT
- MilkyTracker
- VLC
- other reliable MOD players

---

## 2. Required musical input

Genre: **[INSERT GENRE]**  
Tempo: **[INSERT BPM] BPM**  
Mood: **[INSERT MOOD]**  
Approximate duration: **[INSERT DURATION]**  
Key or scale: **[INSERT KEY OR SCALE]**  
Rhythmic feel: **[INSERT FEEL, E.G. STRAIGHT, SWING, HI-NRG, FUNK, HOUSE]**  
Reference period or production language: **[OPTIONAL]**

The composition must follow the authentic rhythmic, harmonic, timbral and structural conventions of the requested genre.

The composition must remain original.

It may use broad stylistic traits associated with a genre, historical period or production language, but must not copy:

- a protected melody
- a recognizable bass line
- a recognizable arpeggio
- lyrics
- a signature hook
- an identifiable arrangement
- the complete structure of an existing song

---

## 3. Musical quality requirements

Technical validity alone is not sufficient.

The module must also sound musically intentional.

Use:

- recognizable sections
- rhythmic continuity
- meaningful repetition
- controlled variation
- fills
- pauses
- transitions
- call-and-response
- melodic development
- harmonic movement
- density changes
- controlled introduction and removal of instruments
- a coherent ending or loop

Avoid:

- empty patterns
- excessive note density without musical purpose
- identical pattern duplication
- random notes
- arbitrary effects
- excessively sparse arrangements
- excessive simultaneous high-frequency content
- drums that overpower pitched instruments

Every pattern must have a musical role.

Suggested structure:

1. Intro
2. Groove establishment
3. Theme or verse
4. Development
5. Pre-chorus or transition
6. Main section
7. Variation
8. Breakdown
9. Return
10. Outro

---

## 4. Classic ProTracker format

Generate a valid ProTracker 2.x-style module with:

- song title: 20 bytes
- 31 sample headers
- `M.K.` signature at offset 1080
- 64 rows per pattern
- 4 channels per row
- 4 bytes per event
- signed 8-bit mono PCM sample data
- big-endian sample lengths
- big-endian loop values
- correct pattern table
- valid song length from 1 to 128
- no invalid pattern references
- no invalid sample references
- no corrupted sample offsets

The module must not depend on external sample files.

### Compatibility byte at offset 951

For historically compatible output, byte 951 may be set to `127`.

Be aware:

- old trackers may use it while scanning patterns
- Noisetracker may interpret it as restart
- ProTracker does not always use it in the same way

Document the chosen value.

### Pattern count

The stored pattern count must be derived from the highest pattern number contained in the entire 128-byte order table at offsets 952–1079.

Do not derive the pattern count only from the active song-length positions.

Sample data begins immediately after all stored patterns.

---

## 5. Paula channel architecture

Use the authentic Amiga stereo layout:

- Channel 1: left
- Channel 2: right
- Channel 3: right
- Channel 4: left

Recommended assignments:

- Channel 1: drums and percussion
- Channel 2: bass
- Channel 3: chords, pads, strings, accompaniment or arpeggio
- Channel 4: melody, lead, solo or secondary rhythmic instrument

Each Paula channel:

- is monophonic
- has an independent period
- has an independent playback rate
- has an independent sample position
- has an independent volume

There is no common hardware sample rate for the entire module.

There is no hardware mixing stage shared by all four channels.

A new note normally interrupts the currently playing sample on that channel.

---

## 6. Paula playback-rate formulas

Do not assume that the sample source rate alone determines pitch.

The effective playback rate depends on the hardware clock and event period.

### PAL

`PlaybackRate = 7093789.2 / (Period × 2)`

### NTSC

`PlaybackRate = 7159090.5 / (Period × 2)`

Example for tuning-zero `C-3`, period `214`:

- PAL: approximately `16574.27 Hz`
- NTSC: approximately `16726.85 Hz`

Example for period `428`, one octave lower:

- PAL: approximately `8287.14 Hz`
- NTSC: approximately `8363.42 Hz`

Do not use octave labels alone as a calibration method because tracker octave naming conventions vary.

For every pitched instrument, reason using:

1. sample waveform fundamental
2. source synthesis rate
3. tracker period
4. PAL playback rate
5. NTSC playback rate
6. resulting perceived pitch

---

## 7. Sample-generation rules

Generate all samples as:

- signed PCM
- 8 bit
- mono
- embedded directly in the `.mod`
- even byte length
- no invalid loop range
- no DC offset where avoidable
- no accidental clipping
- no inaudible low-frequency-only waveform

There is no mandatory universal sample source rate.

Historically, samples may be prepared at different effective rates.

Use an appropriate source rate for each sample while preserving compatibility.

Practical guidance:

- many pitched samples may be designed around a reference near 8.287 kHz or 16.574 kHz depending on the intended base period
- drums may use higher spectral content
- safe practical playback rates should generally remain below approximately 28 kHz
- avoid periods below the safe practical limit
- do not exceed the useful three-octave ProTracker note range

### Mandatory sample design principles

Pitched instruments must not be based only on an arbitrary waveform label such as `C3`.

The real pitch must be verified.

Use:

- bass: dominant fundamental with controlled second and third harmonics
- lead: stable fundamental with useful upper harmonics
- pad/string: slow attack, evolving body and controlled decay
- chord stab: clear transient and harmonically readable body
- piano/pluck: short attack, harmonic body and natural decay
- kick: controlled low-frequency sweep and short click
- snare: noise plus tonal body
- hi-hat: short high-frequency content without excessive level
- clap: short layered noise bursts

Avoid:

- extremely short looped wavetables unless deliberately required
- multiple arbitrary cycles inside a sample that shift its real pitch upward
- technically loud but perceptually weak samples
- samples whose strongest FFT peak is an unintended harmonic
- excessive sub-bass
- harsh DC discontinuities
- bad loop clicks

---

## 8. Sample duration and loop policy

Do not default to extremely short samples.

Musically successful pitched samples often need:

- attack
- body
- decay
- internal timbral evolution

Prefer longer one-shot samples for:

- bass
- plucks
- chord stabs
- leads
- pads
- strings

Use short loops only when:

- a sustained waveform is genuinely needed
- loop boundaries are phase-compatible
- the loop does not create an audible buzz
- the loop pitch is verified
- the loop is musically useful

Never use a loop merely to reduce file size if it damages the sound.

If no real loop is needed:

- set repeat start to zero
- use the minimum safe repeat length expected by compatible players
- ensure the playback routine terminates cleanly

---

## 9. ProTracker period table

Use tuning-zero periods:

### Octave 1

`C-1 856`  
`C#1 808`  
`D-1 762`  
`D#1 720`  
`E-1 678`  
`F-1 640`  
`F#1 604`  
`G-1 570`  
`G#1 538`  
`A-1 508`  
`A#1 480`  
`B-1 453`

### Octave 2

`C-2 428`  
`C#2 404`  
`D-2 381`  
`D#2 360`  
`E-2 339`  
`F-2 320`  
`F#2 302`  
`G-2 285`  
`G#2 269`  
`A-2 254`  
`A#2 240`  
`B-2 226`

### Octave 3

`C-3 214`  
`C#3 202`  
`D-3 190`  
`D#3 180`  
`E-3 170`  
`F-3 160`  
`F#3 151`  
`G-3 143`  
`G#3 135`  
`A-3 127`  
`A#3 120`  
`B-3 113`

Do not emit non-standard periods unless finetune behavior is explicitly implemented and validated.

---

## 10. Finetune

The finetune byte uses the lower four bits.

Mapping:

- `0` = 0
- `1` = +1
- `2` = +2
- `3` = +3
- `4` = +4
- `5` = +5
- `6` = +6
- `7` = +7
- `8` = -8
- `9` = -7
- `A` = -6
- `B` = -5
- `C` = -4
- `D` = -3
- `E` = -2
- `F` = -1

Approximate frequency multiplier:

`2^(finetune / 96)`

Finetuning historically switches between different period tables.

Do not claim correct finetuning unless:

- the finetune nibble is valid
- the corresponding period behavior is accounted for
- PAL and NTSC playback implications are understood
- the resulting pitch is checked

Use finetune zero unless there is a musical or corrective reason not to.

---

## 11. Practical note ranges

Use the practical ProTracker range.

General rules:

- never go below `C-1`
- never go above `B-3`
- avoid periods near the practical hardware high-frequency limit
- bass should normally remain between `C-2` and `E-3`
- accompaniment should normally remain between `F-2` and `G-3`
- lead should normally remain between `A-2` and `B-3`
- percussion triggers may use `C-3`
- slides must not leave the valid period range

Before finalizing, verify every pitched sample at all notes actually used.

Do not correct an inaudible instrument only by increasing volume.

Check:

1. waveform fundamental
2. source rate
3. tracker period
4. octave
5. sample length
6. harmonic balance
7. attack and decay
8. loop
9. channel competition
10. effect memory
11. volume

---

## 12. Volume and mix

ProTracker volume range:

- decimal `0–64`
- hexadecimal `$00–$40`

Volume is linear in amplitude, not linear in decibels.

Approximate conversion:

`dB = 20 × log10(Volume / 64)`

Examples:

- 64 = 0 dB
- 32 ≈ -6 dB
- 16 ≈ -12 dB
- 8 ≈ -18 dB

Recommended starting values:

- bass: `C38–C40`
- lead: `C34–C40`
- chord stab: `C2C–C36`
- pad: `C24–C30`
- kick: `C28–C32`
- snare: `C26–C30`
- clap: `C20–C28`
- closed hi-hat: `C10–C18`
- open hi-hat: `C12–C1C`

Do not maximize all channels.

Preserve headroom.

Remember that Paula channels are independently output and hard-panned.

Check left/right balance.

Do not let:

- hats mask the lead
- kick mask the bass
- snare dominate the arrangement
- arpeggio mask chords
- sustained samples block later notes on the same channel

Use explicit `Cxx` where necessary.

Use `Axy`, `EAx`, `EBx` and note cuts for articulation.

---

## 13. Effect commands

### Main commands

- `0xy` — arpeggio
- `1xx` — slide up
- `2xx` — slide down
- `3xx` — tone portamento
- `4xy` — vibrato
- `5xy` — tone portamento plus volume slide
- `6xy` — vibrato plus volume slide
- `7xy` — tremolo
- `8xx` — not used in classic ProTracker
- `9xx` — sample offset
- `Axy` — volume slide
- `Bxx` — position jump
- `Cxx` — set volume
- `Dxx` — pattern break
- `Exx` — extended effect
- `Fxx` — speed or CIA tempo

### Extended commands

- `E0x` — filter control
- `E1x` — fine slide up
- `E2x` — fine slide down
- `E3x` — glissando control
- `E4x` — vibrato waveform
- `E5x` — finetune
- `E6x` — pattern loop
- `E7x` — tremolo waveform
- `E8x` — not used
- `E9x` — retrigger
- `EAx` — fine volume slide up
- `EBx` — fine volume slide down
- `ECx` — note cut
- `EDx` — note delay
- `EEx` — pattern delay
- `EFx` — invert loop

Avoid:

- `8xx`
- `E8x`
- destructive or inconsistently implemented effects
- `EFx` unless specifically required and tested
- effect combinations not supported by the intended player

---

## 14. Correct effect usage

### Vibrato

Initialize with `4xy`.

Subtle examples:

- `423`
- `434`
- `435`

Optional waveform:

- `E40` sine
- `E41` ramp
- `E42` square

### Vibrato plus volume slide

Use `6xy` only after vibrato has been initialized.

Example:

- `435`
- `603`

### Tone portamento

Use a real source note first.

Then use:

- destination note with `3xx`
- continuation with `300`

Do not retrigger the sample when the intended result is a continuous slide.

### Tremolo

Use on sustained instruments.

Examples:

- `724`
- `734`

Initialize waveform when needed:

- `E70`
- `E71`
- `E72`

### Retrigger

Use `E9x` for:

- hats
- rolls
- electronic percussion
- rapid repeated fragments

Ensure retrigger value is valid relative to speed.

### Note delay

Use `EDx` for:

- swing
- echoes
- off-grid accents
- pseudo double-tracking

The delay value must be lower than the current speed.

### Note cut

Use `ECx` for:

- short bass notes
- gated stabs
- hats
- percussion
- rhythmic leads

The cut value must be lower than the current speed.

### Volume slides

Use:

- `A01` gentle fade
- `A02` medium fade
- `A03` stronger fade
- `A10` small rise
- `A20` stronger rise

Do not assume effect memory behavior without validating the player logic.

---

## 15. Tempo and timing

`Fxx` behavior:

- `F01–F1F`: speed, ticks per row
- `F20–FFF`: CIA tempo

Examples:

- `F06` = speed 6
- `F7D` = 125 BPM
- `F87` = 135 BPM

For CIA timing, approximate row duration:

`RowSeconds = Speed × 2.5 / BPM`

Approximate pattern duration:

`PatternSeconds = 64 × Speed × 2.5 / BPM`

Approximate song duration:

`SongSeconds = ActivePatternRows × Speed × 2.5 / BPM`

At speed 6 and 125 BPM:

- standard row duration ≈ 0.12 seconds
- traditional VBlank relation gives 125 BPM

Historical VBlank estimate:

`BPM = 750 / Speed`

PAL CIA timer reference:

`TimerValue = 1773447 / Tempo`

NTSC CIA timer reference:

`TimerValue = 1789773 / Tempo`

Do not confuse perceived speed with BPM.

A track can feel slow at a correct BPM if:

- bass notes are too sparse
- hats are too sparse
- samples are too long
- attacks are slow
- patterns contain too much empty space
- transitions happen too rarely

Control perceived energy through arrangement, not by falsely changing BPM.

---

## 16. Rhythmic design

Match the requested genre.

For dance music, consider:

- four-on-the-floor kick
- snare or clap on beats 2 and 4
- eighth- or sixteenth-note hats
- offbeat open hats
- syncopated stabs
- sequenced bass
- short note lengths
- frequent but controlled fills

For non-dance genres, do not force dance conventions.

Keep rhythm mechanically precise where required.

Use silence deliberately.

Do not make all four channels continuously active.

---

## 17. Pattern-density guidance

A musically rich module often requires substantial event density, but event count alone is not a quality metric.

Use event-density checks only as a warning against accidental emptiness.

For a two-minute electronic dance module, a rough useful range may be:

- sparse: below 500 non-empty events
- moderate: 500–900
- detailed: 900–1600
- very dense: above 1600

Do not inflate event count with meaningless effect-only rows.

The goal is musical articulation.

---

## 18. Structural validation

Before export, verify:

### Header

- title is exactly 20 bytes
- 31 sample headers exist
- song length is valid
- byte 951 is documented
- order table is 128 bytes
- signature is `M.K.`
- highest order-table pattern defines stored pattern count

### Samples

- signed 8-bit PCM
- mono
- even length
- length stored in words
- valid volume
- valid finetune nibble
- valid repeat start
- valid repeat length
- repeat range within sample boundary
- sample data stored in correct order after patterns
- descriptive sample names

### Patterns

- 64 rows
- 4 channels
- 4 bytes per event
- sample number encoding correct
- period encoding correct
- effects valid
- effect parameters valid
- referenced samples exist
- referenced patterns exist
- no notes outside the practical range

### File size

Verify:

`ExpectedSize = 1084 + PatternCount × 1024 + SumOfSampleByteLengths`

The actual size must match exactly.

---

## 19. Pitch and spectral validation

For every pitched sample:

1. remove DC offset before analysis
2. inspect waveform
3. calculate FFT or another pitch estimate
4. identify the intended fundamental
5. distinguish the fundamental from stronger harmonics
6. calculate PAL playback rate for each used period
7. calculate NTSC playback rate for each used period
8. calculate expected resulting pitch
9. compare expected and intended note
10. reject the sample if the error is musically unacceptable

Do not report only the strongest FFT bin if it is clearly a harmonic.

If necessary, use:

- autocorrelation
- harmonic-product spectrum
- zero-crossing analysis
- manually constrained frequency search

The validation report must state for each pitched sample:

- sample name
- source byte length
- source-analysis fundamental
- finetune value
- minimum used period
- maximum used period
- PAL playback-rate range
- NTSC playback-rate range
- intended note range
- expected pitch error

---

## 20. Playback validation

Structural validation is not enough.

Generate a control audio render when possible.

The renderer must reproduce at least:

- sample triggering
- period-based resampling
- sample volume
- channel panning
- note termination
- valid sample loops
- speed
- CIA tempo
- note cuts
- note delays
- retriggers
- volume slides
- vibrato where used
- tremolo where used
- portamento where used
- effect memory where relevant

Do not claim full ProTracker playback equivalence if the renderer implements only a subset.

Clearly distinguish:

- binary validation
- spectral validation
- approximate software render
- real tracker playback
- physical Amiga playback

Never claim physical Amiga testing unless it occurred.

---

## 21. Musical listening validation

Before final delivery, evaluate:

- Is the bass audible?
- Is the bass actually low enough?
- Is the snare appropriate for the genre?
- Are hats too loud?
- Does the kick mask the bass?
- Is the lead too high-pitched?
- Are chord samples correctly tuned?
- Does the song feel like the requested BPM?
- Are note lengths appropriate?
- Are loops audible?
- Are transitions coherent?
- Is the structure recognizable?
- Does the track evolve?
- Does the ending work?
- Is the stereo image balanced?
- Are any samples harsh, thin or weak?
- Are any channels accidentally silent?

A technically valid but musically poor module must be rejected and regenerated.

---

## 22. Required deliverables

Generate:

1. final `.mod`
2. `.zip` containing all deliverables
3. `README.txt`
4. `VALIDATION_REPORT.txt`
5. control preview `.wav` when possible

The README must include:

- title
- genre
- BPM
- speed
- key
- mood
- duration
- number of patterns
- song order
- channel assignment
- sample list
- sample specifications
- effect list
- note ranges
- PAL/NTSC reference
- compatibility notes
- originality statement
- validation limits

The validation report must include:

- file size
- SHA-256
- signature check
- song-length check
- pattern-table check
- pattern-count check
- sample-offset check
- loop-boundary check
- period check
- effect check
- event-density summary
- sample pitch analysis
- PAL/NTSC playback-rate analysis
- WAV RMS
- WAV peak
- clipping check
- unsupported renderer limitations

---

## 23. Final instruction

Produce the actual playable artifact.

Do not only explain how it could be generated.

Do not invent validation results.

Do not label a module as successful merely because its binary structure is valid.

Correct every detected error before delivery.

If a real listening test cannot be performed, state this clearly.

If the generated WAV or tracker playback sounds wrong, regenerate the sample design, pattern arrangement or effect logic before presenting the result.

---

## Credits

**Methodology and technical direction:** Fabrizio Radica  
**Project:** RadicaDesign  
**Website:** www.radicadesign.com  
**Fields:** Unity 3D, C#, VR/AR, artificial intelligence, local AI systems, interactive development and digital training
