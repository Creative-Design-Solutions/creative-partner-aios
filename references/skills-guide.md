# Skills Guide — Creative Partner AIOS

Skills are commands you type to activate a specific mode or behavior. They're the shortcuts that make your AIOS feel responsive and alive. Some run once and finish. Others stay active for a whole session.

Type a skill name with a `/` in front of it — like `/onboard` or `/snag`.

---

## Setup Skills

### `/onboard`
**What it does:** Your Day 1 ritual. Asks you 7 questions about yourself, your business, your goals, and your working style. Builds out the core files your AIOS uses to know who it's partnering with.

**When to use:** First time you open the system. Re-run any time your life or business changes significantly.

**Triggers:** `/onboard`, "set me up", "let's get started", "onboard me"

**Connects to:** `aios-intake.md`, `context/` folder, `connections.md`

---

### `/audit`
**What it does:** Scores your AIOS against the Four Cs — Connection, Consistency, Capability, Creativity. Shows you where your setup is strong and where the biggest gaps are. Gives you the top 3 fixes ranked by leverage.

**When to use:** End of your first week. Then weekly. Watch your score climb.

**Triggers:** `/audit`, "audit my setup", "is my AIOS working", "find gaps"

**Connects to:** Your `context/` files, `connections.md`, `sessions/log.md`

---

## Daily Skills

### `/morning-coffee`
**What it does:** Your session start ritual. Reads your project, checks recent changes, loads memory, surfaces what's relevant today, and gives you a calm oriented brief. Opens the day with clarity instead of noise.

**When to use:** Start of every work session.

**Triggers:** `/morning-coffee`, "good morning", "let's start", "what are we working on"

**Connects to:** `sessions/log.md`, `connections.md`, memory

---

### `/snag`
**What it does:** Before touching any code or guessing at an error — searches the web. Finds known issues, recent API changes, and breaking changes in seconds. One good search beats 30 minutes of blind debugging.

**When to use:** Any time you hit an unexpected error, an API behaves strangely, or something stops working after an update.

**Triggers:** `/snag`, "search this", "look this up", or any time you're about to guess at an error

**Example:** `/snag Stripe webhook signature verification failing 2026`

**Connects to:** WebSearch, WebFetch

---

### `/commit`
**What it does:** Stages, reviews, and commits your work with a meaningful commit message. Checks for secrets, debug code, and large files before committing. Keeps your history clean without you having to think about it.

**When to use:** Any time you're ready to save a chunk of work.

**Triggers:** `/commit`, "commit this", "save my work", "commit and push"

**Connects to:** Git, GitHub

---

### `/check`
**What it does:** Pre-ship quality check. Runs build, TypeScript, lint, and a self-review of changed files. Gives you confidence before you commit or share.

**When to use:** Before committing, before a PR, or any time you want a second set of eyes on your work.

**Triggers:** `/check`, "check my work", "is this ready", "run checks", "before I ship"

**Connects to:** Your project build tools

---

## Creative Skills

### `/design-master`
**What it does:** Activates a full creative design session — websites, UI, brand, emails, charts, any visual work. Stays active for the whole session so every decision is made with design thinking.

**When to use:** Any time you're starting visual work. Keep it running for the whole session.

**Triggers:** `/design-master`, "let's design", begins any creative build

**Connects to:** Frontend tools, brand assets, design tokens

---

### `/designer`
**What it does:** Activates a professional graphic designer — visual identity, brand, color theory, typography, SVG assets, icons. Also generates prompts for AI image tools like Midjourney and DALL-E.

**When to use:** Logo work, brand identity, design systems, illustrations, image generation.

**Triggers:** `/designer`, "design a logo", "create a brand", "generate an image"

**Connects to:** Brand assets, AI image generators

---

### `/frontend-design`
**What it does:** Builds front-end components, pages, and full sites. Handles HTML, CSS, and JavaScript with design sensibility baked in.

**When to use:** Building a website, landing page, UI component, or any front-end project.

**Triggers:** `/frontend-design`, "build me a site", "design a page", "make a component"

**Connects to:** GitHub Pages, hosting, your client projects

---

## Growth Skills

### `/level-up`
**What it does:** Your weekly growth ritual. Runs the 3Ms interview — finds one automation candidate, scopes it, and ships it. One run equals one shipped artifact. This is how the system compounds over time.

**When to use:** Once a week. Friday works well.

**Triggers:** `/level-up`, "what should I automate next", "find me leverage this week"

**Connects to:** `references/3ms-framework.md`, `references/creative-partner-aios.md`, `workflows/`

---

### `/workflow`
**What it does:** Analyzes your current session to optimize how you're working. Surfaces inefficiencies, saves learnings to memory, and identifies repetitive tasks worth automating.

**When to use:** After a long session or when work feels slow, expensive, or repetitive.

**Triggers:** `/workflow`, "how are we working", "optimize our workflow", "what should we automate"

**Connects to:** Memory, `sessions/log.md`

---

### `/skill-builder`
**What it does:** Creates new skills or improves existing ones. Use this when you want to teach your AIOS a new behavior it can repeat reliably.

**When to use:** When you find yourself giving the same instructions session after session — that's a skill waiting to be written.

**Triggers:** `/skill-builder`, "build me a skill", "save this as a skill"

**Connects to:** `.claude/skills/` folder

---

## Strategy Skills

### `/opus-plan`
**What it does:** Two-model planning — uses the most powerful model for deep thinking, then executes with speed. Use when the quality of the plan really matters.

**When to use:** Complex features, architecture decisions, new projects, anything where a bad plan would cost you real time.

**Triggers:** `/opus-plan`, "plan this carefully", "use opus", "think this through"

**Connects to:** Any project

---

### `/smooth-operator`
**What it does:** Logs a UX improvement pattern — captures what changed, why it feels better, and the principle behind it for future reference.

**When to use:** After fixing something that was clunky. Saves the lesson so it doesn't repeat.

**Triggers:** `/smooth-operator`

**Connects to:** `references/smooth-operator-log.md`

---

## Quick Reference

| Skill | One-line purpose | When |
|---|---|---|
| `/onboard` | Build your AIOS identity | Day 1, or after major life change |
| `/audit` | Score your setup, find gaps | Weekly |
| `/morning-coffee` | Start the day with clarity | Every session |
| `/snag` | Search before debugging | Any error or API issue |
| `/commit` | Clean, meaningful commits | Saving work |
| `/check` | Pre-ship quality check | Before committing or sharing |
| `/design-master` | Full creative design session | Any visual work |
| `/designer` | Brand, logos, image generation | Identity & visual assets |
| `/frontend-design` | Build websites and UI | Front-end projects |
| `/level-up` | Ship one automation this week | Weekly growth ritual |
| `/workflow` | Optimize how you're working | After long or slow sessions |
| `/skill-builder` | Teach your AIOS new behaviors | When patterns repeat |
| `/opus-plan` | Deep planning for hard problems | Complex decisions |
| `/smooth-operator` | Log a UX improvement | After fixing something clunky |
