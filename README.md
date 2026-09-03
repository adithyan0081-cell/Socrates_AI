<img width="1280" height="640" alt="git (1)" src="https://github.com/user-attachments/assets/8920b256-2ba8-4988-b824-5351134eb4bd" />



# Socrates AI 🎯

> *"Njan onnum ariyilla. Athukondu njan chodikkunnu."*
> Ellaam sheriyaayi cheyyunna AI — chodyangal mathram.

## Basic Details
### Team Name: MORPHEUS


### Team Members
- Team Lead: Adithyan S Nair - Saintgits College of Applied Sciences
- Member 2: Sachin Satheesan - Saintgits College of Applied Sciences

### Project Description
Socrates AI is an assistant that understands your task perfectly and uses that understanding exclusively to avoid doing it. You type what you want. It asks a clarifying question. You answer. It asks another one. This continues for up to 23 questions, in Manglish, until it hands you a report confirming that your requirements are now flawless and your task is still pending.

### The Problem (that doesn't exist)
Every other AI just *does* the thing. It guesses your tone, invents your audience, picks a length, and hands you output you didn't ask for. Nobody ever verified whether you wanted "Happy birthday" spelled out in full or whether "HBD" would suffice. Nobody asked what background music should play while your message is being read. Requirements gathering — the most important phase of any project — has been criminally rushed by the entire AI industry.

### The Solution (that nobody asked for)
We built an AI that is *only* the requirements gathering phase. Socrates AI reads your actual task, detects the domain and who it's for, and then asks questions that escalate through four tiers of increasingly poor judgement:

| Tier | Questions | Accent shifts to | What it asks |
|---|---|---|---|
| 1 — Baseline | 1–3 | Teal | Believable stuff. Tone, audience, length. |
| 2 — Over-specific | 4–6 | Violet | Punctuation. Timing. "Hi" vs "Hello". |
| 3 — Unnecessary | 7–10 | Amber | Should sad music play? Should it screenshot the message for documentation? |
| 4 — Existential | 11–23 | Rose | "Ee message ayakkathirunnaal aa relationship-inu enthu sambhavikkum?" |

Task completion stays locked at **0%** the entire time. The little hologram mascot watches you the whole way through, drifting from `idle` → `curious` → `suspicious` → `weary` → `crisis` → `spent`, and finishes the session `exhausted`. Then it congratulates itself.

## Technical Details
### Technologies/Components Used
For Software:
- **Languages used:** HTML5, CSS3, vanilla JavaScript (ES2020)
- **Frameworks used:** None. Zero. No React, no build step, no bundler, no `node_modules`.
- **Libraries used:** No JS libraries. Google Fonts (Space Grotesk, IBM Plex Mono) for type. Anthropic Messages API (`claude-sonnet-4-6`) as an *optional* enhancement.
- **Tools used:** A text editor and a browser. That's the whole toolchain.

Notable implementation bits:
- **Single file, ~75 KB.** The entire app — markup, styling, mascot SVG, question engine, AI integration — lives in one `.html` file. Open it with `file://` and it runs.
- **Domain detection engine.** Regex scoring across 9 domains (`birthday`, `message`, `joke`, `essay`, `code`, `image`, `food`, `plan`, `generic`) picks the *strongest* signal rather than the first match, so "exam-inu study plan undaakku" is correctly routed to `plan` instead of being hijacked by a loose verb.
- **Recipient detection.** A second regex table extracts who the task is about (Best friend, Amma, Achan, boss, crush…) so questions can address them by relationship.
- **Context-aware question generators.** Every fallback question is a function receiving live context (`task`, `short`, `who`, last answer, question number), so questions build on your previous answer instead of firing at random. A tiered pool tracker prevents repeats and degrades gracefully into the existential pool when a domain runs dry.
- **Reaction engine.** Answers are pattern-matched to spoken reactions *and* to one of 22 mascot mood states, each a set of CSS custom properties (eye scale, head tilt, halo intensity, gaze offset, orbit speed, breathing rate) tweened purely via transform/opacity.
- **Optional AI mode.** Paste an Anthropic API key and questions are generated live by Claude with a system prompt that hard-locks it into Manglish, forbids it from ever performing the task, and enforces the same 4-tier escalation ladder. Response JSON is validated (must contain `?`, must not duplicate an earlier question, options deduped and padded to exactly 4). On any failure or 15s timeout it silently falls back to the offline engine — you lose nothing.
- **Accessibility:** full keyboard operation (`Ctrl+Enter` to start, keys `1`–`4` to answer), `aria-live` regions, and a complete `prefers-reduced-motion` path that skips every animation.
- **Privacy:** the API key is held in a JS variable in your browser tab and is never persisted or transmitted anywhere except Anthropic. There is no backend, no analytics, no storage.

For Hardware:
- N/A — this project is entirely software. The only hardware requirement is a device with a browser and the patience of a saint.

### Implementation
For Software:
# Installation
```bash
# Clone it
git clone https://github.com/[your-username]/socrates-ai.git
cd socrates-ai

# That's it. There is no step two.
```

# Run
```bash
# Option A — just open it
open socrates-ai-final-message.html      # macOS
xdg-open socrates-ai-final-message.html  # Linux
start socrates-ai-final-message.html     # Windows

# Option B — serve it locally
python3 -m http.server 8000
# then visit http://localhost:8000/socrates-ai-final-message.html
```

**Optional AI mode:** on the landing screen, expand *"AI mode (optional)"* and paste an Anthropic API key (`sk-ant-...`). Questions then get generated live — more specific, more unhinged. The app is fully functional without it.

### Project Documentation
For Software:

# Screenshots (Add at least 3)
![Screenshot1](Add screenshot 1 here with proper name)
*Boot sequence — "Preparing unnecessary questions…" — with the hologram mascot materialising in standby before you're allowed into the lab.*

![Screenshot2](Add screenshot 2 here with proper name)
*The landing screen. Type any task or tap a preset chip. Note the footer: "Zero team-ukal vishwasikkunnu · Innu vare oru task-um cheythittilla · Uptime 100% · Output 0%".*

![Screenshot3](Add screenshot 3 here with proper name)
*A tier-3 session in progress. Questions asked: 09. Task completion: 0%. Absurdity level: Unnecessary. The accent colour has drifted to amber and the mascot has gone visibly suspicious.*

![Screenshot4](Add screenshot 4 here with proper name)
*The final report — "System status: successfully did nothing" — with the full transcript of everything you clarified and nothing you received.*

# Diagrams
![Workflow](Add your workflow/architecture diagram here)
*Flow: **Boot** → **Task input** → `detectDomain()` + `detectWho()` → **Question loop** (AI mode → validate → fallback on failure | Offline mode → tiered pool selection) → **Answer** → reaction + mood flash + transcript log → escalate tier → repeat until Q23 or "Mathi, report tha" → **Final report at 0% completion.***

For Hardware:

N/A — no hardware involved in this project.

### Project Demo
# Video
[Demo video](https://drive.google.com/drive/folders/11EFA5L-owYLKxW8Gjyo0nuk4VfQL7ECw?usp=drive_link)

*Walks through a full session: entering "Best friend-inu oru birthday wish ezhuthu", watching the questions escalate from "what vibe do you want" to "next year, will these same questions have to be asked again", and arriving at a beautifully formatted report containing no birthday wish.*

# Additional Demos
[Add any extra demo materials/links]

## Team Contributions
- Adithyan S Nair: [Specific contributions]
- Sachin Satheesan: [Specific contributions]

---
Made with ❤️ at TinkerHub Useless Projects 

![Static Badge](https://img.shields.io/badge/TinkerHub-24?color=%23000000&link=https%3A%2F%2Fwww.tinkerhub.org%2F)
![Static Badge](https://img.shields.io/badge/UselessProjects--26-26?link=https%3A%2F%2Ftinkerhub.org%2Fevents%2F1M8ORET9A1%2Fuseless-projects-3.0)
