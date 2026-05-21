---
name: instagram-reel-script
description: Use when the user wants to write a reel script, generate Instagram reel content, script a talking head video, create reel hooks, plan reel content, or write a script for a short-form video. Runs a strict step-by-step pre-flight (big idea + context → pillar → TOF/MOF → format suggestion → user-pasted pre-transcribed yap) BEFORE writing. Then delivers the FIRST DRAFT as TELEPROMPTER-ONLY spoken script (no production breakdown). The full production doc is built only after Ethan approves the spoken script. Always loads the client's IG transcript corpus from `../clients/{slug}/raw-content/instagram-transcripts/` for voice match. If no corpus exists, scrapes the client's last 15 reels via ScrapeCreators + Whisper before writing. Always searches online for tonal reference material before writing. Skill is GENERAL. Every client-specific detail loads from `../clients/{slug}/` at runtime.
---

# Reel Script. Step-by-Step Pre-Flight + Voice Corpus + Teleprompter-First.

This skill produces IG reel scripts through a strict pre-flight Q&A, voice-corpus loading, online tonal research, and a teleprompter-only first draft. The production doc only gets built after Ethan approves the spoken script. Every word is grounded in the client's actual recorded delivery from their IG transcript corpus.

---

## Process

```
Phase 0:  Load Foundations                       →  InfoOps doctrine (strategic layer)
Phase 1:  Pre-Flight Q&A                         →  Ask 9 fundamentals in ONE message. Wait.
Phase 1B: Load Pillar Formula + Surface Fields   →  Load pillar formula. Surface its steps as fill-in prompts. Wait.
Phase 2:  Format Suggestion                      →  Skill proposes 1-3 formats. User picks.
Phase 3:  Receive Yap (pre-transcribed text)     →  User pastes the yap transcript. NOT audio.
Phase 4:  Load Client Context                    →  Audience brief, brand voice, IG transcript corpus, swipe.
Phase 5:  Search Online for Tone                 →  Find tonal reference material that matches the topic.
Phase 6:  Write Teleprompter                     →  SPOKEN WORDS ONLY. No production breakdown.
Phase 7:  Silent Self-Audit                      →  Anti-AI, anti-generic, voice fidelity, strategic frame.
Phase 8:  Save + Deliver Teleprompter            →  File first, then paste the spoken-only script.
Phase 9 (after approval ONLY): Build Production Doc  →  Visuals, on-screen text, B-roll, audio, captions.
```

**Hard rules:**
- Never skip Phase 1. Always ask the 9 fundamentals first.
- Never skip Phase 1B. Once the pillar is named, load the formula and surface the fields. Then wait. (See `feedback_pillar_formulas_mandatory.md` in memory.)
- Never transcribe yap audio. Ethan transcribes before sending. The yap arrives as PASTED TEXT.
- Phase 8 first deliverable = teleprompter only. Spoken words. Nothing else. No headers, no [Visual], no [Note], no production markup. (See `feedback_reel_script_format.md` in memory.)
- The full production doc (Phase 9) is built ONLY after Ethan reads the teleprompter and approves it.
- If the client has no `raw-content/instagram-transcripts/` corpus, run the scrape+transcribe pipeline FIRST before writing. Without voice corpus, scripts default to AI-voice and fail voice match.

---

## Phase 0: Load Foundations

Always load first. This is the strategic layer that informs every reel.

- `context/sops/content-foundations.md`. InfoOps operating doctrine. The InfoOps reel template (Idea, Final Statement, Format, Title, Hook, Body, Conclusion) lives in Section 6 of this file. The 25-format library lives there too. The 3 content pillars + the dream-follower-vs-ICP framing + TOF/MOF formula + 80/20 voice split all live there.

Key load-bearing rules from the foundations to apply silently to every reel:
- IG reels target the **dream follower** (60% of all reels). The ICP layer happens in HOW you say things inside dream-follower reels (the 80/20 voice split. 80% authentic / 20% ICP keyword sprinkles like "funnels," "scaling," "operator," "case study").
- "Don't be the value fucker." Never write "Here are 3 ways to scale your VSL." Always tie value to the creator's lived experience.
- Every reel either redirects to YouTube (the bridge metaphor: IG gets them on the bridge, YouTube walks them across) or fits inside the story arc (Onboard → Build → Waitlist → Launch → Booked Calls → Result).
- Pure identity reels (archetypes 2B, 3, 7, 8) get NO CTA. The job is desire-building, not redirection.

---

## Phase 1: Pre-Flight Q&A (NON-NEGOTIABLE)

Ask all questions in ONE message. Wait for the user's full answers before doing anything else. Do NOT generate, suggest formats, transcribe, or write until everything is answered.

**Phase 1 message template (paste close to verbatim):**

> Before I write the reel, I need the full fundamentals so it actually lands. Drop these:
>
> **1. Big idea.** What's the core idea? One line.
>
> **2. Trigger / context.** What sparked this? A specific moment, a conversation, a pattern you noticed, a DM, a sales call, a lesson from this week? The trigger is what makes the reel feel real instead of generic advice.
>
> **3. Sub-audience inside the dream follower.** Who specifically are you talking to? E.g., a stuck $5K/mo coach, a 19yo in NS, a copywriter trying to switch to operator. Different sub-segments need different language.
>
> **4. Belief or objection you're shifting.** What does the viewer currently believe (or fear) that this reel is going to break or reframe?
>
> **5. Why now.** Why does this matter THIS week vs. last month? Tying to current relevance gives it urgency.
>
> **6. Specific anchors.** Any real numbers, names, moments, dashboards, screenshots, or stories I can use as the spine? Specifics over invented placeholders, every time.
>
> **7. Pillar.** Which one?
>    - **P1** Sell the Person (KLT, your worldview / belief / decision)
>    - **P2A** The Problem (name a structural bottleneck coaches hit)
>    - **P2B** Why an Operator (operator vs VA / employee / DIY)
>    - **P2C** The Outcome (what life looks like with an operator running things)
>    - **P3A** The Mechanism (your specific systems / process)
>    - **P3B** The Proof (results, case studies, pattern insights)
>    - **P3C** The Differentiator (what sets you apart from other operators)
>
> **8. TOF or MOF?**
>    - **TOF** (attention). Goals it must hit: desire / relatability / uniqueness. Used when client has low views + low leads.
>    - **MOF** (conviction). Goals it must hit: break a limiting belief / surface a hidden problem / pre-handle an objection. Used when client has engagement but low close.
>
> **9. Yap.** If you've got a voice memo (already transcribed by you), paste the transcript here. If not, say "no yap" and I'll write off the corpus + the fundamentals above.

After the user answers, move to Phase 2.

**If the user gives a partial answer:** ask the missing pieces before proceeding. Don't guess. Don't fill placeholders that read as generic.

**If the user pushes back ("just write it"):** explain in one sentence that the pre-flight prevents generic reels and ask the missing pieces. Do not skip.

---

## Phase 1B: Load Pillar Formula and Surface the Fields (NON-NEGOTIABLE)

The single biggest reason a reel reads as generic is that the pillar formula was never explicitly applied. The 9 fundamentals tell you WHAT the reel is about. The pillar formula is HOW that content earns trust / breaks belief / builds desire on this specific channel. Skipping this step turns every reel into "generic personality content" or "generic problem content." Always run this phase.

After the user answers the 9 fundamentals (and you know which pillar they picked), do this in one move:

1. **Load** `Content Agent/context/sops/content-pillar-formulas.md` and find the section for the exact pillar (P1, P2A, P2B, P2C, P3A, P3B, P3C).
2. **Extract the formula's 4-5 structural steps** for that pillar. Each pillar has named steps + a one-line formula + an example.
3. **Surface those steps to the user as fill-in prompts.** Pre-populate the slots with what they already gave you in Phase 1, so the user is editing/confirming/extending, not starting from scratch.
4. **Wait for the answers.** Then proceed to Phase 2.

### Per-pillar field map (use the matching pillar's set in Phase 1B)

**P1 — Sell the Person (formula: Specific belief / situation → Why you see it that way → What this reveals about how you operate → Audience alignment cue)**

> Locking the P1 formula. Fill these in so the reel maps to the framework instead of being a generic philosophical riff:
>
> 1. **Specific belief or situation.** What's the ONE belief or moment this reel anchors to?
> 2. **Why you see it that way.** What concrete experience, pattern, or moment leads you to that belief?
> 3. **What this reveals about how you operate.** What does the right viewer learn about HOW you make decisions / handle pressure / move through life?
> 4. **Audience alignment cue.** What's the line in this reel that makes the right viewer nod hard and the wrong viewer scroll?

**P2A — The Problem (formula: Surface symptom → Structural cause → Emotional / lifestyle cost → Validation without pitching)**

> Locking the P2A formula. Fill these in:
>
> 1. **Surface symptom (their words).** What does the ICP say out loud when they describe this problem? Use their exact phrasing.
> 2. **Structural cause underneath.** What's the actual systemic / structural reason the symptom keeps happening?
> 3. **Emotional or lifestyle cost.** What does this problem cost beyond money? Energy, sleep, family time, identity?
> 4. **Validation that normalises it without pitching.** How do you let them off the hook (it's a structural issue, not a them issue) without selling?

**P2B — Why an Operator (formula: Alternative they're considering → Why it fails at their level → What an operator does differently → Why rev share is zero-risk → Stage-specific why now)**

> Locking the P2B formula. Fill these in:
>
> 1. **Alternative they're considering.** VA? Employee? DIY? Another operator? Name it.
> 2. **Why it fails at their level.** What's the structural mismatch (not quality bash)?
> 3. **What an operator does differently.** Name 2-3 specific functions, not "runs your business."
> 4. **Why rev share is zero-risk.** One-line framing.
> 5. **Why now (stage-specific).** At what revenue / stage does this become the right move?

**P2C — The Outcome (formula: Current reality, specific → Operator-enabled reality, equally specific → Tangible lifestyle / revenue difference → Let the gap sell)**

> Locking the P2C formula. Fill these in:
>
> 1. **Current reality (specific).** Hours, revenue, what their Monday actually looks like.
> 2. **Operator-enabled reality (equally specific).** Hours, revenue, dashboard view, calls per day, content cadence.
> 3. **Tangible lifestyle / revenue difference.** Operational calm, not vacation photos. Paint the exact morning.
> 4. **The gap that sells itself.** What's the one specific contrast that lands hardest?

**P3A — The Mechanism (formula: Common approach that fails → Why it fails → Your approach + reasoning → Enough for conviction not implementation → Connect to their stage)**

> Locking the P3A formula. Fill these in:
>
> 1. **Common approach that fails.** What does the conventional advice say to do?
> 2. **Why it fails.** Specific structural reason.
> 3. **Your approach + reasoning.** Name the system or process. Explain the WHY before the WHAT.
> 4. **Conviction without implementation.** How much detail is enough to make them believe but not enough to do it themselves?
> 5. **Stage / situation connection.** Who specifically is this for right now?

**P3B — The Proof (formula varies by tier; pick one)**

> Locking the P3B formula. Pick a tier and fill in:
>
> - **Tier 1 (Direct results):** Starting point → What you implemented → Result → Timeframe → Lifestyle change. Fill each.
> - **Tier 2 (Process proof):** What's the artifact (dashboard, system, workflow) you're showing? What does the quality say without narration?
> - **Tier 3 (Pattern insight):** What pattern have you seen across N+ clients? Why does it predict scale or stall?

**P3C — The Differentiator (formula: What most operators do → What you do instead → Reasoning behind your approach → Result or impact → Let viewer conclude)**

> Locking the P3C formula. Fill these in:
>
> 1. **What most operators do.** The standard approach, no bashing.
> 2. **What you do instead.** ONE specific thing, go deep not wide.
> 3. **Reasoning behind your approach.** The why is more important than the what.
> 4. **Result or impact.** What happened the last time you did it this way?
> 5. **The conclusion the viewer should reach.** Stated implicitly, never claimed.

### Hard rules for Phase 1B

- **Always load the actual formulas doc.** Do not paraphrase from memory. The doc is the source of truth.
- **Pre-populate slots from Phase 1 answers.** If they already gave you the belief in fundamental #1, drop it into the P1 "Specific belief" slot in your fill-in prompt so they can edit / extend / confirm rather than re-typing.
- **Wait for the answers.** Even if the user gave a clean Phase 1, the formula slots often surface gaps the 9-fundamentals didn't catch (especially the "audience alignment cue" / "what does this reveal about how you operate" beats).
- **If the user says "just use what I gave you, write now":** confirm in one line which slots you're filling from their Phase 1 answers and which you're inferring, then proceed. Don't drop the formula step silently.
- **Surface the formula's example (one line).** Reminds the user what good output looks like for that pillar.

After the user confirms / fills the formula slots, move to Phase 2.

---

## Phase 2: Format Suggestion

After Phase 1 answers, propose **1 to 3 formats** based on the pillar + TOF/MOF + the client's existing swipe / archetype fit. State the recommendation, why it fits, and offer a backup.

Use this decision matrix as the starting point:

| Pillar | TOF / MOF | Default format pool |
|---|---|---|
| 1 (Sell the Person) | TOF | Archetype 2A or 2B (Facetime Talking Head). Or 25-format library: FaceTime, talking head, day-in-the-life, in-the-moment, podcast clip. |
| 1 (Sell the Person) | MOF | Archetype 2B (Fuck-that variant) or talking head with a belief-break. Reaction / story-time. |
| 2 (Why Operator) | TOF | Archetype 1 (My Story), Archetype 8 (Lifestyle), demo content, X-vs-Y, "for [Action], it used to be X. Now it's Y." |
| 2 (Why Operator) | MOF | Tier list ranking, X-does-this Y-does-this Z-does-this, sales call clip, Miro breakdown of why a system fails. |
| 3 (Why Work With Me) | TOF | Archetype 1 (My Story), Archetype 8 (Lifestyle), in-the-moment "just signed this client" demo. |
| 3 (Why Work With Me) | MOF / BOF | Archetype 4 (Miro/Bait-Switch), Archetype 6 (Challenge), Archetype 5 (Story-Telling Counter), client interview / sit-down case study. |

Always also check:
- The client's `swipe-file.md` for formats that have already worked for them.
- The client's `references/` folder for proven format examples.
- If the topic naturally maps to a recognizable cultural moment, consider Archetype 7 (Skits).

**Phase 2 message template:**

> Based on Pillar {N} + {TOF/MOF}, top recommendation:
>
> 1. **{Format name} ({archetype number if applicable})**. {One-sentence why}. Reference: {client swipe link OR archetype reference reel}.
> 2. **{Backup format}**. {When to switch to it.}
> 3. **{Optional third}**. {When to use this.}
>
> Pick one or tell me to swap.

After the user picks, move to Phase 3.

---

## Phase 3: Receive the Yap (Pre-Transcribed Text)

Ethan transcribes the voice memo himself before sending. The yap arrives as **pasted text in the chat**, NOT as an audio file path. Do NOT run Whisper on anything.

When the yap arrives:
1. Save the raw text to `../clients/{slug}/raw-content/voice-notes/{YYYY-MM-DD}-yap-{topic-slug}.md`. Preserve every word. Don't clean it.
2. Read it twice and extract:
   - **Direct quotes.** Word-for-word lines usable as hook, body, or close.
   - **Cadence patterns.** How he phrases things. Where he pauses. What filler words he naturally uses ("like," "honestly," "literally," "you know").
   - **Specifics.** Numbers, names, real situations, micro-details. Gold. Use over anything invented.
3. The yap is the **spine** of the script. The archetype mechanics structure it. The InfoOps template wraps it. The words come FROM the yap.

If the user said "no yap":
- Skip Phase 3.
- Pull voice cues from the IG transcript corpus loaded in Phase 4.
- Pull voice cues from `../clients/{slug}/raw-content/` (other transcripts, voice notes, Discord wins added in last 30 days).
- Pull voice cues from the brand-voice doc and existing approved scripts in `workspace/reels/`.

**Hard rule:** when a yap is provided, every spoken line in the script must trace back to either THE YAP or the IG transcript corpus. If a line has no counterpart, replace it.

---

## Phase 4: Load Client Context (and the Voice Corpus)

Before writing a single word, read ALL of the following.

**Voice corpus (LOAD-BEARING. If missing, build it FIRST. See "Voice Corpus Bootstrap" below.):**
- `../clients/{slug}/raw-content/instagram-transcripts/`. Whisper transcripts of the client's last ~15 IG reels.
- `_combined-voice-corpus.md` if it exists in the same folder. Concatenated voice corpus for fast scanning.
- This is the MOST IMPORTANT input. Without the voice corpus, scripts default to AI-voice and fail.
- Caveat: some "reels" are actually clipped from call recordings. Their transcripts may be looser than camera-ready delivery. Use them as voice signal, but treat polished on-camera reels as the higher-fidelity reference.

**Client files (always):**
- `../clients/{slug}/audience-brief.md` (or `audience-brief-personal.md` / `audience-brief-business.md` if Ethan personal brand). Who they're talking to, pain points, dream state.
- `../clients/{slug}/brand-voice.md` (or `voice-fingerprint.md`, or `brand-voice-personal.md` / `brand-voice-business.md` for Ethan). How they sound, what they avoid.
- `../clients/{slug}/content-pillars.md`. What topics they own.
- `../clients/{slug}/swipe-file.md`. What's already been validated for this creator.

**Viral reference (always):**
- `context/sops/viral-content/quick-ref.md`. Kallaway share rate model, hook system, story locks.
- `context/sops/viral-content/reel-archetypes.md`. The 8 decoded archetypes swipe file with full mechanics.

**Other raw content (always, check first):**
- `../clients/{slug}/raw-content/transcripts/`, `voice-notes/`, `discord-wins/`, `interviews/`. Anything added in last 30 days.
- **Onboarding forms + sales-call recordings + DM exchanges = idea pipeline.** Mine before generating anything.

**Existing reels (always):**
- `../clients/{slug}/workspace/reels/`. Read recent saved scripts to match cadence, structure preferences, format choices.

**If the topic involves a specific result, tool, or case study:** verify the details with Ethan before scripting. Never invent statistics, dollar amounts, or student names.

### Voice Corpus Bootstrap (run when client has no `instagram-transcripts/` folder)

This is a **basic rule for every client**. Before writing a single reel, ensure the voice corpus exists. If it doesn't, build it.

```bash
# 1. Hit ScrapeCreators IG profile endpoint
source "/Users/ethan/Downloads/Claude Code Workspace/.env"
curl -s "https://api.scrapecreators.com/v1/instagram/profile?handle={client-handle}" \
  -H "x-api-key: $SCRAPECREATORS_API_KEY" \
  -o /tmp/{slug}-profile.json

# 2. Extract video_url + shortcode pairs (first 15 reels)
# 3. For each pair:
#    - curl -sL the video_url to /tmp/{slug}-reel-{shortcode}.mp4
#    - ffmpeg extract audio to /tmp/{slug}-reel-{shortcode}.mp3
#    - whisper transcribe with --model medium --fp16 False
#    - save .txt to ../clients/{slug}/raw-content/instagram-transcripts/{shortcode}.txt
#    - delete /tmp mp4 and mp3 to avoid disk pile-up

# 4. Concatenate all transcripts into _combined-voice-corpus.md with shortcode headers.
```

For high-volume work, delegate this pipeline to a sub-agent (Agent tool with general-purpose subagent_type) so the main thread keeps its context clean.

**Why this is non-negotiable:** clients hire ghostwriters who sound like THEM, not like ChatGPT. The IG corpus is the only ground truth for cadence, fillers, sentence length, vocabulary, and the rhythm patterns that make a script read as human.

---

## Phase 5: Search Online for Tonal Reference Material (Comprehensive)

Before writing, do a comprehensive online search for the best existing takes on the topic. Goal: find canonical phrasing, ride-along cadence, and proven imagery from top voices in the niche the client respects. Internal corpus alone is not enough.

**Sources, in priority order:**

1. **Top voice tweets/posts on the exact theme.** Search X / Twitter for tweets from creators like:
   - For Ethan personal: Hormozi, Iman Gadzhi, Hamza, Dan Koe, Sam Ovens, Alex Becker, Andrew Tate-adjacent (manosphere) for the 16-26 MMO crowd specifically.
   - For Travis: top e-com / dropshipping voices (Sebastian Ghiorghiu, Trevor Mauch, etc.).
   - For Ryan: SG creator scene, freelancer-to-agency voices.
   - For Anthony / Tyler: pull from their voice doc + niche-leader handles in their `linkedin/niche-handles.txt` if it exists.
2. **Reddit threads** where the audience articulates the pain in their own words (r/Entrepreneur, r/getdisciplined, r/coaching, etc.).
3. **The client's own corpus** (`../clients/{slug}/raw-content/instagram-transcripts/`).
4. **Niche-specific quote sites + book passages** for canonical aphorisms.
5. **The niche-leader handles** if listed in the client folder.

**What to extract per source:**
- Canonical phrases / aphorisms that already exist on the topic. Don't reinvent.
- Cadence / sentence-length patterns from the tonal lane.
- Specific images, metaphors, or analogies that have already proven viral.
- Exact word choices that the audience already responds to.

**Save the research (always):**
- Save findings to `../clients/{slug}/raw-content/research/{YYYY-MM-DD}-{topic-slug}-references.md`.
- Include: source URL or @handle, the exact quote, why it's relevant, the takeaway for our reel.
- Comprehensive enough that future reels on the same theme can build on it without redoing the search.

**How to use the research when writing:**
- Reference but DON'T COPY. The phrasing should be inspired by the canonical takes, then translated into the client's voice from their own corpus.
- The client's voice is the cadence + register layer. The canonical takes are the IDEA + IMAGERY layer. The combination creates a reel that rides existing cultural momentum while sounding like the client.

---

## Phase 6: Write the Teleprompter

**Deliverable mode depends on format (set in Phase 2):**

- **FaceTime mode** (Archetype 2A, Archetype 2B, FaceTime in 25-format library) → **BULLETS**. Beat-level outline with anchor phrases, key arguments, and specifics per beat. The talent riffs each beat live in their own raw register. Writing full prose for FaceTime lands stilted, which kills the format. See `feedback_facetime_vs_talking_head.md` in memory.
- **Talking head mode** (Archetype 1, talking-head in 25-format library, demo content, scripted-VO formats, anything direct-response) → **FULL PROSE**. Direct-response copywriting where every word is engineered. Reads as a written script, performed.

Either way: spoken-only deliverable. No production markup ([Visual], [On-screen text], [Note]). Production layer is Phase 9. Both modes ship with TEXT HOOK overlay above the body and metadata header above that.

The script or beat outline is built from:
1. The yap (when provided. Actual words / cadence, the spine).
2. The voice corpus (cadence, fillers, sentence rhythm).
3. The online tonal references (canonical phrases, proven imagery).
4. The archetype's structural beats. Folded silently into the prose for talking head, surfaced as beat headers for FaceTime.

### Saved format: FaceTime (bullets)

```
# {Topic Title}

**Client:** {slug}
**Strategic frame:** {Dream follower | ICP} · {TOF | MOF} · Pillar {1 / 2a / 2b / 2c / 3a / 3b / 3c}
**Format reference:** {Archetype 2A or 2B reference reel}
**Length target:** ~{X}s
**Format mode:** FaceTime → BULLETS, not full prose. Riff each beat live in your own register.
**Big idea:** {one sentence}
**Belief shift:** {old belief → new belief}

---

**TEXT HOOK (on-screen overlay):** {3-7 word hook}

---

## Beats (riff each chunk in your own register; blank lines separate beats; no numbers, no bold headers by default)

- {Anchor phrase or key argument}
- {Sub-anchor or specific}

- {Anchor phrase for next beat}
- {Specific number / name / moment the talent must hit}

(continue for 4-6 beat chunks, blank lines between them. Each chunk hits a NEW angle, never restates a prior beat.)

- {Close: final line}
- {Action — what they should do right now, ideally a verbatim phrase from the talent's own corpus}
```

### Saved format: Talking head (prose)

```
# {Topic Title}

**Client:** {slug}
**Strategic frame:** {Dream follower | ICP} · {TOF | MOF} · Pillar {1 / 2a / 2b / 2c / 3a / 3b / 3c}
**Format reference:** {archetype number + reference reel OR 25-format library format name}
**Length target:** ~{X}s
**Format mode:** Talking head → SCRIPTED. Direct-response, every word engineered.

---

**TEXT HOOK (on-screen overlay):** {3-7 word hook}

---

{The script itself. Plain prose. Double-spaced between major thought beats. No headers in the body. No markup. Just the words.}

{Each paragraph is a thought beat or a breath. Sentences flow naturally. Fragments allowed for emphasis only, never stacked three-deep as a default.}

{Read it aloud once. If it sounds like a content piece, rewrite. If it sounds like the talent at 2am to a friend, ship.}
```

That's the entire deliverable for Phase 8. No production. No visuals. Just bullets (FaceTime) or prose (talking head).

### Hard rules for the teleprompter

- **Voice fidelity over cleverness.** If a line doesn't trace back to the yap, the corpus, or the brand voice doc, replace it.
- **Contractions throughout.** "I'm," "don't," "you're," "can't." Never "I am," "do not," "you are."
- **Varied sentence length.** Mix long flowing sentences with short punches. Don't default to 5-word fragments stacked.
- **Connective tissue.** "And," "but," "so," "because," "you know." Real speech connects thoughts. Don't strip the connectors and call it punchy.
- **No em dashes.** Periods, commas, or restructure. The AI-slop detector blocks the file otherwise.
- **No AI-vocabulary tells.** No "delve," "leverage," "fundamentally," "actually" overused, no "Here's the thing," no "Let me break this down."
- **No fragment chains.** Stacked one-word lines ("No X. No Y. No Z.") are an AI tell. Use prose with one fragment for punctuation, not three.
- **No contrast reframes.** "It's not X, it's Y" is an AI tell. Restructure.

### Archetype-specific mechanics to enforce:

**Archetype 1 (My Story):** Archived past footage in hook, kinetic typography, named student result, DM-word CTA. No stock footage.

**Archetype 2A (Facetime Talking Head, Proof/Reframe):** White/grey pill sticker full duration, sticker OFF for any proof insert, no B-roll longer than 2s, editorial-voice close, no CTA.

**Archetype 2B (Facetime Talking Head, "Fuck that"):** Grey pill sticker full duration, zero B-roll, excuses list delivered deadpan, single genuine smile only at vision beat, "Fuck that." hard stop. NO outro, sticker stays in final frame.

**Archetype 3 (POV Letterbox):** Black bars top/bottom applied in edit, "pov: YOU did" not "I did," proof screen before face, caption number ≠ screen number (deliberate gap), humble celebration prop, B&W for exactly one celebration beat.

**Archetype 4 (Miro/Bait-Switch):** Word-by-word bait build (one cut per word), creator NOT looking at camera during bait, B-roll shame gesture at exact judgment line, two-zone layout for mechanism ONLY, income figure comes after mechanism, callback close.

**Archetype 5A (Story-Telling Day Counter):** Blurred phone in hook + clear phone in result, LED color changes between timeline phases, tool screen recording with watermark intact, failure beat flat delivery, LED payoff on income reveal.

**Archetype 5B (Story-Telling Month Counter):** Month-X in blue italic cursive (not standard caption font), THREE LED colors (blue narrator / red despair / green production), external authority checklist insert, keyboard hands B-roll, "things were compounding" as the philosophical core.

**Archetype 6 (Challenge):** Animated dollar signs/colored numbers in hook, income proof on frame 2 (not at end), dark cinematic setup for hook + normal for tutorial, pointing finger on ALL screen recordings, controversy line without hesitation, named specific example with view count.

**Archetype 7 (Skits):** `pov: [reference] IRL` caption from first to last frame unchanged, no voiceover, reference must map exactly to real-world visual, night setting mandatory for car/luxury content, no explanation.

**Archetype 8 (Lifestyle):** Most aspirational visual possible as opening frame, audio lyric must describe literal activity shown, captions on travel / NO captions during action, faceless throughout, no CTA.

---

## Phase 7: Silent Self-Audit

Run all six checks internally before saving. Do not surface them. Just fix what's wrong.

**Audit 1. Anti-AI check.**
Read the spoken script aloud. Flag and rewrite any of: em dashes (replace with periods, commas, or restructure), "Here's the thing," "Let me break this down," fragment chains ("No X. No Y. No Z."), contrast reframes ("It's not X, it's Y"), three-item rhythm defaults, synthetic enthusiasm, "delve," "leverage," "fundamentally," "actually" overused. Contractions throughout. Varied sentence length. Real human cadence. **No em dashes anywhere in the file**, including the metadata header. The AI-slop detector blocks the save if any em dash slips through.

**Audit 2. Anti-generic check.**
Is every number specific? Is every location named? Is every tool named? Is every example real? If anything is vague, make it specific or flag it as a placeholder.

**Audit 3. Voice corpus fidelity check (LOAD-BEARING).**
- Open the IG transcript corpus from Phase 4. Cross-reference the script against actual phrases the client uses.
- Are the cadence + sentence length + filler words drawn from the corpus?
- Pick 5 random sentences from the script. For each, ask: "would this client say this in real life?" If the answer is no for any sentence, rewrite.

**Audit 4. Strategic frame check (InfoOps).**
- If targeting the dream follower, does the script telegraph that the creator operates in the ICP space (the 20% ICP keyword sprinkle inside the 80% authentic delivery)?
- If TOF: does the hook hit one of {desire, identity, emotionally resonating story, proof moment, contrarian opinion}? Is the format already a winning format from a real reel?
- If MOF: does the script call out one of {pain, desire, belief}, prove with context + results, create a shift, and make the next step obvious?
- "Don't be the value fucker" check: is the value tied to lived experience, or is it abstract instruction? If abstract, rewrite with specifics from the creator's history.

**Audit 5. Yap fidelity check (only if a yap was provided).**
- Are the spoken lines pulled directly from the yap, or do they sound like the model's voice?
- Are the cadence + filler words + specifics from the yap preserved?
- If a line in the script has no counterpart in the yap, the corpus, or the brand-voice doc, replace it.

**Audit 6. Teleprompter purity check.**
- Are there any [Visual] markers in the file? Remove.
- Are there any [On-screen text] markers? Remove.
- Are there any [Note] / [Why this hook works] / production directions? Remove.
- The deliverable should be: metadata header + TEXT HOOK + (FaceTime: beat bullets / Talking head: spoken prose). Nothing else.

---

## Phase 8: Save + Deliver Teleprompter + Kallaway Audit

Save to `../clients/{slug}/workspace/reels/{YYYY-MM-DD}-reel-{topic-slug}.md` BEFORE presenting in chat.

After saving, confirm the file path. Then present:
1. One-line strategic frame (Pillar / TOF-or-MOF / Format / Format mode).
2. The deliverable: beat bullets for FaceTime, spoken prose for talking head.
3. **Kallaway Audit**: scored out of 100 across 5 categories. Forces structured evaluation against Kallaway's principles instead of subjective "looks good." Drives quality compounding because the same gaps surface visibly each round. See format below.
4. Any facts that need verification before filming (unconfirmed numbers, student names, dashboard figures).
5. The line: "Approve audit (apply improvements and produce v2) / approve current script (no changes, build production doc) / edits?"

**Do not skip past Phase 8 into the production doc.** Wait for explicit approval. The audit is for the SCRIPT only, not the production doc.

### Kallaway Audit Format (always 5 categories, 20 pts each, total 100)

```
## Kallaway Audit — Score: X/100

| Category | Pts | Score | Notes |
|---|---|---|---|
| Hook (visual stun + topic clarity + on-target curiosity + Kallaway hook format match) | 20 | X | ... |
| Architecture (8-beat structure + rehook timing — first rehook 20-25s + length appropriate to platform) | 20 | X | ... |
| Story locks (embedded truths + contrast words + negative frames + loop closure + term branding + thought narration) | 20 | X | ... |
| Voice fidelity (verbatim phrases preserved + register match + YT corpus pulls) | 20 | X | ... |
| Dopamine + script quality ($100/word test + sentence variability + screenshot-able capstone + dopamine ladder progression) | 20 | X | ... |

### Improvements (priority order)
1. {Most impactful change}
2. {Next}
3. {Etc.}
```

**Audit rules:**
- Be honest. A first draft that scores 95+ is suspicious. Real Kallaway-tight scripts usually start at 75-85 and iterate up.
- Each category note explains WHY the score is below 20, not what's already working.
- Improvements are ordered by impact, not by where they appear in the script.
- After Ethan replies, only proceed to v2 if he approves the audit. If he picks "approve current," skip v2 and go straight to Phase 9 production doc.

---

## Phase 9: Build Production Doc (ONLY after Ethan approves)

Triggered when Ethan replies with "approved," "ship it," "go," "looks good," "build the production doc," or equivalent.

Save the production doc as a SEPARATE file: `../clients/{slug}/workspace/reels/{YYYY-MM-DD}-reel-{topic-slug}-production.md`. Do NOT overwrite the approved teleprompter.

The production doc adds layers on top of the spoken script:
- **Hook section.** Visual setup, on-screen text, exact framing, delivery note.
- **Body Beat sections.** Per beat: visual, on-screen text, delivery note, archetype mechanic call-out.
- **CTA section.** Visual, on-screen text, type (comment-word / bio link / no CTA / DM-word).
- **Production Notes.** Location, props, LED setup, screen recordings, B-roll, graphics/overlays, audio, lapel mic.
- **Caption.** 1-3 lines.
- **Cover Text Ideas.** 2-4 word options.

Apply archetype-specific mechanics from the matrix below:

**Archetype 1 (My Story):** Archived past footage in hook, kinetic typography, named student result, DM-word CTA. No stock footage.

**Archetype 2A (Facetime Talking Head, Proof/Reframe):** White/grey pill sticker full duration, sticker OFF for any proof insert, no B-roll longer than 2s, editorial-voice close, no CTA.

**Archetype 2B (Facetime Talking Head, "Fuck that"):** Grey pill sticker full duration, zero B-roll, excuses list delivered deadpan, single genuine smile only at vision beat, "Fuck that." hard stop. NO outro, sticker stays in final frame.

**Archetype 3 (POV Letterbox):** Black bars top/bottom applied in edit, "pov: YOU did" not "I did," proof screen before face, caption number ≠ screen number (deliberate gap), humble celebration prop, B&W for exactly one celebration beat.

**Archetype 4 (Miro/Bait-Switch):** Word-by-word bait build (one cut per word), creator NOT looking at camera during bait, B-roll shame gesture at exact judgment line, two-zone layout for mechanism ONLY, income figure comes after mechanism, callback close.

**Archetype 5A (Story-Telling Day Counter):** Blurred phone in hook + clear phone in result, LED color changes between timeline phases, tool screen recording with watermark intact, failure beat flat delivery, LED payoff on income reveal.

**Archetype 5B (Story-Telling Month Counter):** Month-X in blue italic cursive (not standard caption font), THREE LED colors (blue narrator / red despair / green production), external authority checklist insert, keyboard hands B-roll, "things were compounding" as the philosophical core.

**Archetype 6 (Challenge):** Animated dollar signs/colored numbers in hook, income proof on frame 2 (not at end), dark cinematic setup for hook + normal for tutorial, pointing finger on ALL screen recordings, controversy line without hesitation, named specific example with view count.

**Archetype 7 (Skits):** `pov: [reference] IRL` caption from first to last frame unchanged, no voiceover, reference must map exactly to real-world visual, night setting mandatory for car/luxury content, no explanation.

**Archetype 8 (Lifestyle):** Most aspirational visual possible as opening frame, audio lyric must describe literal activity shown, captions on travel / NO captions during action, faceless throughout, no CTA.

---

## What This Skill Does NOT Do

- Does not skip Phase 1 pre-flight, ever.
- Does not generate 3 generic variations and ask the user to pick. One well-matched archetype script is the deliverable.
- Does not invent statistics, student names, or income figures. Use real data or flag as needing verification.
- Does not use stock B-roll suggestions. Every visual note refers to specific real footage the creator can film or already has.
- Does not add a CTA to pure identity reels (archetypes 2B, 3, 7, 8). These are designed to build desire without asking for anything.
- Does not skip the archetype selection step. Every script must declare which archetype it follows and why.
- Does not write a script when a yap was promised but the file path failed to resolve. Stop, ask for the correct path.

---

## Quick Reference: Anti-Patterns from the Decoded Reels

None of the 10 decoded viral reels do any of these. Neither should any script written with this skill:

1. Open with a CTA ("follow me if you want to learn X")
2. Show the creator's face as the first visual. Proof or concept comes first.
3. Use a generic location ("at my desk" without specificity)
4. Show income without explaining the mechanism (even briefly)
5. Overdramatize the failure beat. Flat delivery only.
6. Add a CTA to a pure identity/lifestyle reel
7. Use round numbers when exact figures are available
8. Name a tool without showing it in use (screen recording or physical prop)
9. Run B&W grade for more than one beat
10. Use the same caption font for structural markers (Month-X, POV label) and subtitle words

---

## InfoOps Template Reference (always state these in the saved file)

The InfoOps reel template structures every reel's planning frame. State each at the top of the file under "InfoOps Template Frame":

- **Idea.** What is this video and why are we making it? One sentence.
- **Final Statement.** What impression are we trying to leave off for the viewer? Usually ties back to the hook.
- **Format.** What is the best way to get this information across to the viewer? FaceTime style for psychological concepts. Miro board for result breakdowns. Talking head with heavy editing for client case studies.
- **Title (visual hook).** If the title isn't strong, they won't make it to the hook. Two jobs: portray that the video will be valuable, and raise perceived value with a wow factor / result.
- **Hook (verbal hook).** Same two jobs as the title, plus optional controversy and optional fast visual movement at the start.

The Body and Conclusion live in the Body Beats and CTA sections of the saved file (don't duplicate them). The InfoOps template is the planning frame. The script body is the execution.
