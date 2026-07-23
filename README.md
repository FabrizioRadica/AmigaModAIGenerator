# Amiga ProTracker MOD Generation Prompt

A structured master prompt for generating complete, playable and technically validated Amiga ProTracker `.mod` music files with AI models.

The project focuses on classic four-channel ProTracker modules with embedded 8-bit samples, authentic Paula channel behavior, valid pattern data, musical arrangement, pitch validation and export-ready deliverables.

## Concept and Methodology

**Fabrizio Radica**
**RadicaDesign**
https://www.radicadesign.com

## Purpose

This project provides a reusable master prompt designed to guide an AI model through the generation of real Amiga ProTracker modules.

The prompt includes instructions for:

* classic four-channel ProTracker structure;
* 31 embedded sample slots;
* signed 8-bit mono PCM samples;
* Paula PAL and NTSC playback-rate calculations;
* period tables and practical note ranges;
* sample pitch and spectral validation;
* finetune handling;
* song order and pattern construction;
* tracker effect usage;
* arrangement, dynamics and musical development;
* binary validation;
* optional WAV preview rendering;
* README and validation-report generation.

The objective is not merely to produce a structurally valid `.mod` file, but to create a module that is also musically coherent, audible, balanced and usable in real tracker software.

## How to Use It

The master prompt must be loaded first.

Paste or upload the complete master prompt into the AI conversation before requesting any music generation.

After the model has read and understood the master prompt, provide a separate and much shorter musical brief describing the track you want to create.

The musical brief should normally include:

* genre;
* BPM;
* approximate duration;
* key or scale;
* mood;
* rhythmic character;
* desired instruments;
* arrangement direction;
* any specific musical priorities.

Example:

```text
Generate an energetic 1980s synth-pop dance track.

Tempo: fixed at 135 BPM
Duration: approximately 2 minutes
Key: A minor
Mood: energetic, emotional and highly danceable

Use a strong four-on-the-floor kick, gated snare, electronic clap,
sixteenth-note hi-hats, a clearly audible pulsing bass, bright chord stabs,
a mechanical arpeggio and an original melodic synth lead.

The arrangement must include an intro, groove development, main section,
breakdown, final climax and short outro.
```

Do not repeat all the technical ProTracker rules inside each musical brief. Those rules are already contained in the master prompt.

## Recommended Workflow

1. Start a new AI conversation.
2. Upload or paste the master ProTracker generation prompt.
3. Ask the model to confirm that it has understood the technical requirements.
4. Provide the musical brief.
5. Request the actual `.mod` artifact, not only a description or code example.
6. Download and test the generated module in OpenMPT, MilkyTracker, VLC or compatible Amiga software.
7. Report any audible or structural problem back to the model.
8. Ask the model to inspect, correct and regenerate the module.

For complex generations, it may be useful to work incrementally:

1. generate the initial module;
2. inspect the samples and pattern structure;
3. correct pitch, volume, loops or arrangement;
4. generate a final validated version.

## Existing Module Test

An additional and useful experiment is to provide the AI with an existing `.mod` file.

The model can then be asked to:

* analyze its structure;
* identify weak or incorrect samples;
* inspect note ranges and periods;
* correct tuning problems;
* improve the mix;
* extend the arrangement;
* add new sections;
* create pattern variations;
* modify the musical style;
* replace or improve instruments;
* repair malformed pattern or sample data.

Example request:

```text
Analyze the uploaded ProTracker module.

Preserve its main musical identity, but improve the bass, correct any tuning
problems, add pattern variations and extend the arrangement by approximately
30 seconds.

Do not replace the file with a MIDI conversion. Return a real four-channel
ProTracker MOD with embedded samples.
```

When modifying an existing module, always keep a backup of the original file.

## Expected Deliverables

A complete generation should ideally include:

```text
track_name.mod
track_name_preview.wav
README.txt
VALIDATION_REPORT.txt
track_name.zip
```

The `.mod` file is the primary artifact.

The WAV preview is useful for quickly evaluating the result, but it does not replace testing inside a real MOD player.

## Validation Limits

AI-generated modules must always be tested manually.

A file may be structurally valid while still containing:

* weak or inaudible bass;
* incorrectly tuned samples;
* excessive high-frequency content;
* poor channel balance;
* unsuitable note lengths;
* audible loop clicks;
* repetitive patterns;
* incorrect effect behavior;
* an arrangement that feels slower or less energetic than the requested BPM.

Binary validation alone does not guarantee musical quality.

Whenever possible, test the result with more than one player.

## Tested Models

The methodology has been tested with:

* **ChatGPT 5.6**
* **Claude**

At the current stage, ChatGPT 5.6 has produced the most useful and manageable workflow for this type of artifact generation.

Claude can also process the prompt, but particular care is recommended. It may consume a very large number of tokens during analysis, code generation, validation and regeneration. Results are not yet consistently satisfactory for this specific workflow.

Model behavior can change over time, so these observations should not be considered permanent performance guarantees.

## Token Usage and System Stability

This is a long and technically detailed prompt.

Generating binary music artifacts, synthesizing samples, rendering previews and performing repeated validation can require substantial context, computation and token usage.

The author is not responsible for:

* excessive token consumption;
* API or subscription costs;
* conversation limits;
* interrupted generations;
* browser or application freezes;
* model timeouts;
* system instability;
* corrupted or incomplete outputs;
* loss of work caused by the AI platform;
* differences between model versions.

Use the prompt responsibly and keep local backups of every generated file.

For models with limited context or high token consumption, use smaller and more focused musical briefs and avoid requesting unnecessary explanations during the generation process.

## Originality and Copyright

The prompt may be used to generate music inspired by broad genres, historical periods and production techniques.

It must not be used to reproduce protected melodies, lyrics, hooks, bass lines, samples or recognizable arrangements from existing recordings.

References to artists or songs should be treated as general stylistic direction only.

Generated music should remain original.

## License

This project is licensed under the **Creative Commons Attribution-ShareAlike 4.0 International License**.

You may:

* copy and redistribute the prompt;
* modify and extend it;
* translate it;
* include it in other projects;
* use it for personal or commercial work.

You must:

* credit **Fabrizio Radica / RadicaDesign**;
* indicate whether changes were made;
* preserve the same license, or an officially compatible ShareAlike license, for redistributed modified versions;
* avoid adding restrictions that remove the freedoms granted by the license.

SPDX identifier:

```text
CC-BY-SA-4.0
```

Suggested attribution:

```text
Based on the “Amiga ProTracker MOD Generation Prompt”.

Concept and methodology by Fabrizio Radica — RadicaDesign.
https://www.radicadesign.com

Licensed under CC BY-SA 4.0.
Changes from the original have been indicated.
```

## Disclaimer

This project is provided as is, without warranties.

Generated files may require manual correction and must be tested before use in production, publication, live performance, archival work or distribution.

No physical Amiga hardware compatibility is guaranteed unless the resulting module has actually been tested on real hardware.

## Credits

**Concept and methodology:** Fabrizio Radica
**Project:** RadicaDesign
**Website:** https://www.radicadesign.com
**Fields:** Unity 3D, C#, VR/AR, artificial intelligence, local AI systems, interactive development and digital training
