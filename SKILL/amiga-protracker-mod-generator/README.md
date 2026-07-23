# Amiga ProTracker MOD Generator Skill

A Claude Code skill for generating, repairing, inspecting, and validating authentic 4-channel Amiga ProTracker `.mod` files.

## Install globally

Copy the folder `amiga-protracker-mod-generator` to:

```text
~/.claude/skills/amiga-protracker-mod-generator/
```

On Windows, the personal skill folder is normally inside your user profile:

```text
%USERPROFILE%\.claude\skills\amiga-protracker-mod-generator\
```

The final structure must be:

```text
amiga-protracker-mod-generator/
├── SKILL.md
├── README.md
├── examples/
│   └── usage.md
└── references/
    └── master-prompt.md
```

## Invoke

```text
/amiga-protracker-mod-generator "128 BPM, E minor, aggressive 1980s synth-pop dance, about 2 minutes, four-on-the-floor"
```

Claude may also activate the skill automatically when a request clearly concerns generation or validation of an Amiga ProTracker module.

## Design

`SKILL.md` remains concise to reduce recurring context usage. The complete technical methodology lives in `references/master-prompt.md` and is loaded only when the skill is used.
