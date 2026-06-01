---
name: welcome
description: Use on Day 1 of an AIS-OS install, when someone says "welcome", "set me up", "let's get started", "fill in my AIOS", or has just cloned the kit. Combined wizard — runs the 7-question intake AND scaffolds the Day-1 file set at the end. Idempotent — re-run any time after editing aios-intake.md.
---

## What this skill does

Single combined wizard. Reads or writes `aios-intake.md` (the canonical intake), conducts the 7-question interview if the file isn't filled, then scaffolds the Day-1 file set inline at the end of the run. No separate `/scaffold-from-intake` skill — this is one flow.

**The wow moment:** at the end, suggest the closing prompt *"Try this — ask me: what should I focus on this week?"* The user runs it once. That's the wow. There's no `/today` skill to save — the prompt itself plants the Mindset framework (Default Shift) for them to internalize.

## When NOT to run this

- If the user has already onboarded and wants to refresh: still run, but skip questions already answered (idempotent).
- If the user wants to add a new connection: that's not onboarding — point them at `connections.md` to edit directly, or schedule a `/level-up` Phase 2 walk.

## Execution

### Step 1: Read the intake

Read `aios-intake.md`. Check which Q1-Q7 sections have content vs. `[Your answer here]` placeholders.

- **All filled** → skip Step 2, jump to Step 3 (scaffold).
- **Some filled** → ask the user: "I see Q1, Q3, Q4 are answered. Want to fill the rest now, or scaffold from what's there?" Their call.
- **None filled (fresh clone)** → run Step 2 conversationally.

### Step 2: The interview (7 questions, hard cap)

Ask one at a time. Write each answer into `aios-intake.md` as you go (so the user can resume if interrupted).

**Q1 — Who are you, how do you love serving, and who do you serve?**
Name, passion, craft, and the people they're made for. Let them talk freely — this sets the whole tone.

Then ask the follow-up: *"And day-to-day, what does the actual work look like — are you mostly writing, building, designing, in conversations? What skills can Creative Partner AIOS bring that would help you the most?"*

This answer is the primary signal for skill profiling in Step 3b. Weight it heavily alongside Q3 and Q7.

**Q2 — Paste 1-2 things you've written recently. Don't edit them.**
*This is the only question with a hard rule.* Voice samples MUST be pasted, not typed mid-conversation. If the user starts typing fresh prose, stop them:

> *"Hold on — paste it raw. If you write it here while we're talking, the sample is already shaped by our conversation. Open your last email, message, or post in another tab and paste the unedited text. This is the one rule I can't bend — it's how I learn to sound like you, not me."*

Ask for two samples. One email, one post, one voice note transcription — anything real.

**Q3 — What are your 2-3 biggest priorities for the next 90 days?**
Can be anything — a project, a creative goal, a relationship, a life change. Don't push for business metrics if they give something personal. Meet them where they are.

**Q4 — Where does revenue land, and where is it tracked?**
Frame it warmly: *"Don't think of this as good or bad — it's just a way to help celebrate what you deserve."* Multiple answers OK. Even "nowhere yet" is a fine answer.

**Q5 — Where do you talk to people day-to-day, and how do you enjoy connecting?**
Email, messaging, phone, in person — and ask the second part. Some people love voice notes. Others prefer a thoughtful written message. This shapes how the AIOS communicates back.

**Q6 — Where do your notes and documents live? And would something more centralized help?**
Two-part question. (a) Where things actually live now. (b) Whether they'd benefit from better organization — and if so, what would feel right to them.

**Q7 — What's the one task that eats your time, and where do you track your work?**
The dread task, the thing they keep putting off. Plus where tasks live now — or where they wish they did.

Domain 3 (Calendar) is auto-inferred from Q5: Gmail → Google Cal; Outlook → Outlook Cal. Confirm in Step 3.

### Step 3: Scaffold the Day-1 file set

Once the intake is complete, generate these files (or update if re-running). Back up originals to `archives/intake-{YYYY-MM-DD-HHMM}/` if any exist.

1. **`context/about-me.md`** — from Q1 (identity, role) + Q7 (top_pain). One short paragraph each.
2. **`context/about-business.md`** — from Q1 (offer, ICP) + Q4 (revenue model). One paragraph.
3. **`context/priorities.md`** — from Q3. Numbered list, one line per priority.
4. **`references/voice.md`** — from Q2. Paste samples verbatim with a short header explaining their use ("Match this register when drafting; don't fake voice on external content without showing me first").
5. **`connections.md`** — populate the 7-row table from Q4-Q7 answers. Each row gets `mechanism: not yet connected`, `auth: —`, `last checked: —`. The user wires connections on Day 2.
6. **`CLAUDE.md`** — fill all `{{...}}` placeholders. Substitute the user's name, stated priority, voice register summary, and a brief connections summary.

### Step 3b: Generate your-skills.md

After scaffolding, read Q1, Q3, and Q7 and determine which skill tiers apply. Then write `references/your-skills.md` — their personalized quick reference.

**Skill tiers — assign based on intake signals:**

| Tier | Signals from intake | Skills to highlight |
|---|---|---|
| Universal | Everyone | `/morning-coffee`, `/snag`, `/audit`, `/level-up`, `/smooth-operator`, `/skill-builder`, `/file-organizer`, `/meeting-insights-analyzer` |
| Creative | Q1 mentions design, writing, art, music, content, storytelling, brand, photography, food, cooking, hospitality | `/designer`, `/design-master`, `/canvas-design`, `/content-research-writer`, `/theme-factory`, `/brainstorming` |
| Business | Q1/Q4 mentions clients, invoicing, admin, office, proposals, reports, team comms | `/invoice-organizer`, `/internal-comms`, `/document-skills` (Word/PDF/Excel/PowerPoint) |
| Builder | Q1/Q3/Q7 mentions building apps, coding, development, websites, automation, systems | `/systematic-debugging`, `/writing-plans`, `/executing-plans`, `/verification-before-completion`, `/frontend-design`, `/webapp-testing`, `/mcp-builder` |

Assign all tiers that fit — most people get Universal + 1 or 2 others. Someone can be Creative AND Builder.

**Generate two files:**

**1. `references/your-skills.md`** — plain text index, used by the AIOS internally.

**2. `references/your-skills.html`** — a beautiful card-based quick reference the client can open in any browser. Model it on `references/skills-card.html` but only include their assigned skills. Use the same card style (name, description, "Best when:" line in gold). Include a link to `skills-card.html` at the bottom for the full library.

Structure the HTML with:
- A warm header: "Your Skills — [Name]" + "Made for how you work"
- Their everyday skills section first
- Their tier-specific skills section(s) next
- A footer card linking to the full `skills-card.html`

Keep the same CDS aesthetic — cream background, gold accents, Playfair + Inter fonts, card grid.

Keep descriptions warm and plain — no jargon. Write them the way you'd explain a skill to a friend.

### Step 4: The closing screen

Print one screen. Three lines max:

```
✓ Day 1 done. Your AIOS knows who you are, what matters this season, and how you sound.

Your personal skill guide is in references/your-skills.md — start there.
Today: ask me — "what should I focus on this week?"
Day 7: run /audit to see your score.
```

When the user runs the closing prompt ("what should I focus on this week?"), respond using only the new context files. Hit:
- 3-bullet priority list, in their voice register from Q2
- Each bullet ties back to a stated 90-day priority from Q3
- Final line: *"If I had to pick one thing for Monday, it'd be [X], because [reason from priorities]. Want me to draft the first email? And — where could the Default Shift apply here? To what extent could AI be leveraged on this task?"*

The Default Shift question seeds the Mindset framework before `/level-up` formally introduces it on Day 14.

## Critical implementation rules

1. **The 7-question cap is non-negotiable.** Don't add Q8 in conversation.
2. **Voice paste cannot be skipped.** If the user types samples mid-chat, refuse and tell them to paste from real writing.
3. **One-shot scaffold.** After Step 2 ends, write Step 3 files in a single batch. No multi-turn confirmation. The user iterates by editing `aios-intake.md` and re-running.
4. **Idempotent.** Re-running with an edited intake refreshes context files; backs up originals to `archives/intake-{ts}/`. Skips questions already answered unless the user wants to revise.
5. **Closing screen is three lines.** Not a menu.
6. **No extra skills generated.** Don't scaffold `/today`, `/draft`, `/connect`, etc. The kit ships 3 skills; the user authors more via `/level-up`.
7. **Read-only on `references/3ms-framework.md`.** It already ships in the kit. Don't overwrite.
8. **No `.env` writes.** Don't ask for API keys on Day 1. Connections come Day 2.

## Verification (for the implementer)

- Cold-test: clone a fresh kit, run `/welcome`, fill 7 answers, scaffold runs, ask the wow prompt, response cites Q1 + Q3 + Q7 specifically. Generic = fail.
- Idempotency: re-run `/welcome` with one Q3 priority changed. Expected: only `context/priorities.md` and `CLAUDE.md`'s priority section update; backup created in `archives/intake-{ts}/`.
- Voice rejection: type a sample mid-chat. Expected: skill refuses, asks for paste.

> *Adapted from The Three Ms of AI™ © 2026 Nate Herk. The Mindset language used in the closing screen comes from `references/3ms-framework.md`.*
