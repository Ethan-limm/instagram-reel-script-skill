# Instagram Reel Script Skill

A Claude Code skill that writes Instagram reel scripts in a specific creator's voice. It runs as a guided multi-phase pipeline (intake, voice research, draft, audit), pulling the creator's actual past reel transcripts and brand voice rules at runtime so every script matches how that person already speaks on camera.

This repo is for review. Skill files at the top level. Real client setup inside `example-client/` so you can see what feeds into the skill at runtime.

## What's in here

```
.
├── README.md                        ← you are here
├── SKILL.md                         ← the skill prompt Claude Code loads
├── scripts/
│   └── scrape-reels.py              ← pulls fresh reel transcripts via ScrapeCreators API
└── example-client/                  ← real example: my personal-brand IG setup
    ├── audience-brief-personal.md
    ├── brand-voice-personal.md
    ├── content-pillars.md
    ├── reel-voice-fingerprint.md
    ├── instagram/
    │   ├── profile.md
    │   ├── rules.md
    │   └── swipe-file.md
    └── raw-content/
        └── instagram-transcripts/
            └── README.md   ← real client has 10-20 .txt reel transcripts here
```

## How it works at a high level

1. The skill activates on phrases like "write a reel script" or "script a reel about X."
2. Phase 1 is intake: it asks for the big idea, the platform context, the content pillar this lives under, and whether the user wants TOFU/MOFU/BOFU.
3. Phase 2 loads the creator's voice. It reads `reel-voice-fingerprint.md` first, then the transcripts in `raw-content/instagram-transcripts/`, then any platform-level rules in `instagram/rules.md`. If the transcript corpus is empty for this client, it runs `scripts/scrape-reels.py` to pull the creator's last 15 reels fresh.
4. Phase 3 writes a teleprompter-ready spoken script: hook, body beats, payoff, CTA. The body is voice-matched line by line against the transcripts so it reads like the creator actually said it.
5. Phase 4 audits the draft against the creator's `rules.md` and a generic AI-slop detector. Anything that fails the audit gets rewritten before delivery.

The skill is generic. Every client-specific detail loads from a per-client folder at runtime so the same skill works for any creator with the same folder shape.

## The `example-client/` folder

Real working example, taken from my own personal-brand setup (`@the.ethanlim`). Every file in there is what the skill actually loads when I ask it to write a reel for me.

- `reel-voice-fingerprint.md` — the single source of truth for how I sound on camera. The skill reads this first, before anything else.
- `audience-brief-personal.md` — who I'm talking to in personal-brand reels.
- `brand-voice-personal.md` — broader voice notes that layer on top of the fingerprint.
- `content-pillars.md` — the topic territories I post inside. Every reel idea maps to one of these.
- `instagram/profile.md` — the IG account context.
- `instagram/rules.md` — platform-specific hard rules (banned phrases, hook patterns, CTA conventions).
- `instagram/swipe-file.md` — high-performing reel structures I've decoded and want to clone formats from.
- `raw-content/instagram-transcripts/` — Whisper transcripts of my own past reels. These are the voice match corpus. Actual transcripts are omitted from this public repo (10-20 .txt files in a real client setup).

## The `scripts/` folder

`scrape-reels.py` calls the ScrapeCreators API to pull a creator's latest 15 reel URLs, then a separate yt-dlp + Whisper pipeline downstream transcribes them into the corpus. The skill calls this automatically when the corpus is stale or empty.

## How to run the skill

This is a Claude Code skill, so it's invoked through Claude Code itself, not through a separate runtime. To use it in your own Claude Code project:

1. Copy `SKILL.md` (and `scripts/scrape-reels.py` if you want the fresh-corpus pipeline) into `.claude/skills/instagram-reel-script/`.
2. Set up a client folder mirroring `example-client/` for whoever you're writing for.
3. In Claude Code, type something like "write a reel script for [client] about [topic]."
4. The skill loads, asks a few intake questions, and produces a teleprompter-ready script.

## Why this structure

I work with multiple clients across multiple platforms (IG, YouTube, X, LinkedIn). If the skill hardcoded any one client's voice, I'd need a separate skill per client. Putting everything client-specific into the per-client folder means the skill itself stays small and reusable, and the voice load is just a directory swap at runtime. The `example-client/` folder is the literal pattern every new client onboards to.

Open to any feedback on the structure, the prompt design, the phase split, or the voice-match loop.
