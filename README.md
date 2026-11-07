# Realistic Consistent Character Videos: VideoExpress Workflow v1.0

Attach 1–2 real photos of one or two people, write a one-line story and pick an English accent for each person. Your AI agent then builds a **fast-paced, photorealistic ~30-second video** inside [VideoExpress](https://app.videoexpress.ai/) in which **the same people stay recognizable in every shot** and speak their lines with lip sync in a steady accent. It writes the character bible, makes a character anchor portrait, generates every shot with multi-shot video prompts, **trims the dead air** on the timeline and exports an MP4.

**Community page:** [Realistic Consistent Character Videos](https://community.dualup.com/@videoexpress/workflows/realistic-consistent-character-videos)

Forked from [Realistic Mini Dramas](https://github.com/ai-playbooks/realistic-mini-dramas).

## Quick start (2 minutes)

1. **Sign in** to https://app.videoexpress.ai/ (or sign in when the agent asks).
2. Open a **new chat that can control a browser**:
   - **ChatGPT (Mac/Windows app):** first set **Settings → General → Permissions → Full access** and choose Full access in the chat's permissions menu. Without it the browser automation can't start. The prompt's first message walks you through this. See [CHATGPT_SETUP.md](CHATGPT_SETUP.md).
   - **Claude:** Claude in Chrome, or the Claude desktop app's built-in browser.
3. **Paste the short prompt** from [SYSTEM_PROMPT.md](SYSTEM_PROMPT.md) (everything below the line). It tells the AI to open the full [PLAYBOOK.md](PLAYBOOK.md) from this public repo in its browser. No GitHub login is needed.
4. **Attach your photos and answer the one question** (or fill in the lines at the end of the prompt):
   - **Character 1:** 1–2 clear photos plus a name. **Best: a close, sharp, front-facing head-and-shoulders photo** (selfie distance, good light, no filter); full-body photos with a small face give a much weaker likeness
   - *(optional)* **Character 2:** 1–2 photos plus a name
   - **Story:** e.g. "Maya surprises Leo with concert tickets on a rooftop, he pretends he's busy, then admits he bought the same tickets"
   - **Accent** per person: British, Australian, American, Irish, Indian English… (English only for now)
   - *(optional)* length (default 30 s), format (Vertical 9:16 default, or 16:9), pacing (Multi-shot default, or Single-shot)
5. Wait. The agent produces, trims and exports, then sends you the download link.

There's no audit, no preflight and no approval step. The agent only comes back to you if it can't upload the photos itself, or if VideoExpress needs you to click **I Agree** on its one-time Consistent Character disclaimer, sign in, accept its one-time Terms or top up credits.

**Only use photos of people who agreed to it** (yourself, a colleague, a client). See [Good to know](#good-to-know).

## How it works

| Stage | What the agent does in VideoExpress |
|---|---|
| Character bible | A very detailed **Character Description** per person (90–140 words: face feature by feature, skin, hair, build, plus a garment-by-garment **Wardrobe Lock**), pasted verbatim into every image prompt, and a Short Tag for video prompts; at most two locations |
| Voice Lock | One voice line plus a normalized accent phrase per person (e.g. `speaking English with a natural Australian accent`), repeated word for word in every clip |
| Reference photos | Uploaded to **Media Library → My Media → Images**, then picked into **Use Consistent Character → Reference Photo** / **Reference Photo 2** |
| Anchor portraits | One chest-up portrait per person in the video's wardrobe, saved with **+ Consistent Character**; then **Reference Photo** = Character 1's anchor, **Reference Photo 2** = Character 2's anchor |
| Look | Image Type **Photorealistic (Cinematic)**, **Use Creative mode always ON** (clearly closer likeness in live tests), image **and** video prompt enhancement **off** (the video one is on by default), public gallery **off** |
| Shots | Default **4 clips × 8 s**, each with **2–3 cuts inside** (multi-shot prompting, ≈ 10 shots), or Single-shot 5 s clips. Every prompt starts with a `C## —` tag |
| Rendering | At most **5 videos in parallel**; the agent works in waves |
| Edit | Clips in order on track 1 with **Auto Align Clips** |
| **Dead-air trim** | Heads and tails only (the cuts inside each clip stay intact), gaps closed |
| Export | High / FullHD / MP4 (1080×1920 or 1920×1080), with the link from **My Videos** |

## Files

| File | Use it for |
|---|---|
| [SYSTEM_PROMPT.md](SYSTEM_PROMPT.md) | **The prompt to paste.** Short, and loads PLAYBOOK.md from GitHub. Also what goes on the community page |
| [PLAYBOOK.md](PLAYBOOK.md) | **The full instructions** the AI reads from GitHub. Edit this to update every user at once |
| [CHATGPT_SETUP.md](CHATGPT_SETUP.md) | **ChatGPT:** the Full access setting it needs, how to attach photos, and an optional Project/custom GPT setup |
| [PROMPT_COMPACT.md](PROMPT_COMPACT.md) | Under 8,000 characters, for custom GPT instructions or Claude Project instructions |
| [docs/video-prompting.md](docs/video-prompting.md) | How the multi-shot video prompts are written, with more examples |
| [examples/](examples/README.md) | Complete worked jobs with every prompt written out, e.g. [Rooftop Tickets](examples/realistic-rooftop-tickets.md) |
| [skills/realistic-consistent-character-videos/](skills/realistic-consistent-character-videos/SKILL.md) | Agent Skill version with the VideoExpress UI map |
| [AGENTS.md](AGENTS.md) / [CLAUDE.md](CLAUDE.md) | Auto-loaded by Codex / Claude Code: "run nothing, use the browser" |
| [Production checks](docs/production-checks.md) | Clip log, speaker and continuity checks, recovery after interruption, and final review |
| [docs/troubleshooting.md](docs/troubleshooting.md) | Symptom → fix, including likeness drift and accent drift |
| [docs/community-entry.md](docs/community-entry.md) | Copy-ready text for the DualUp community page |

## Make a custom GPT or Claude Project (optional)
Paste [PROMPT_COMPACT.md](PROMPT_COMPACT.md) (the part below the line) into the instructions field and turn on browsing/agent capability. Then every new chat starts with the intake question, and you attach the photos to your first message.

## Good to know
- **Consent.** The photos are of real people. Use only likenesses you have the right to use. The agent refuses sexual, humiliating, hateful, political-impersonation, fake-news or deceptive "this really happened" content of a real person, and only works with adults.
- **Privacy.** The agent unchecks **Share this in the public gallery** on every generation, because these are real faces.
- **English only for now.** Accents are English accents; non-English languages aren't supported yet.
- Each image and video generation uses your VideoExpress credits. A 30 s video is about 2 anchor portraits, 4 start images and 4 videos, plus a few retries.
- AI video can still drift (a face shifts, the wrong mouth moves, an accent wanders). The detailed Character Description, Creative mode, the anchor portrait and the Voice Lock keep that to a minimum; the agent regenerates clearly wrong clips.
- Exports stay in **My Videos** for 40 days.

See [CHANGELOG.md](CHANGELOG.md) for what changed from Realistic Mini Dramas.
