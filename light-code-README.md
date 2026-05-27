# 💡 Light Code

**A free, open-source skill for Claude Code and AI coding assistants.**

> *Turning dark code into light code — one comment at a time.*

---

## The Problem: Dark Code

When AI builds your app, website, or script for you — that's called **vibe coding**. And the result is what we're calling **dark code**: it works, but nobody (including you) truly knows what was built, how it fits together, or why any particular decision was made.

Dark code is a liability. You can't maintain it. You can't hand it off. You can't debug it confidently. And if you ask the AI to modify it later, it's starting from scratch with no memory of the original reasoning.

## The Solution: Light Code

**Light Code** is a narration layer for AI-generated projects.

When Light Code is active, the AI narrates every meaningful block of code it writes — in plain English — explaining *what* it built and *why* it built it that way. Every block gets a **conventionality grade** so you immediately know what's standard practice and what's worth paying attention to before you touch it.

The result is code that's transparent, documented, and human-readable from the moment it's created — not as an afterthought.

---

## How It Works

### 1. In-Code Narration

Every meaningful block of code gets a `[LIGHT CODE]` comment written above it:

```javascript
// [LIGHT CODE]
// WHAT: Sets up the main Express server and defines the port it listens on.
// WHY: Express is the standard Node.js framework for handling HTTP requests. Port is
//      pulled from environment variables so it works locally and in deployed environments
//      without hardcoding a value.
// GRADE: ✅ Standard
const app = express();
const PORT = process.env.PORT || 3000;
```

Comments are written for **non-technical readers**. No jargon without explanation.

---

### 2. Conventionality Grading

Every block gets graded so you know exactly what you're looking at:

| Grade | Label | What It Means |
|---|---|---|
| ✅ | **Standard** | Common practice — most developers would write it this way |
| 🔵 | **Non-standard** | Works fine, just not the typical approach — worth knowing |
| ⚠️ | **Unconventional** | Notable deviation — read the full comment before modifying |
| 🔴 | **Highly Unconventional** | Significant departure — understand this fully before touching it |

Blocks graded ⚠️ or 🔴 always include an explanation of *why* the unconventional path was chosen over the standard one.

---

### 3. On-Demand Reports

Reports are never dumped automatically. You call them when you want them — mid-session or at the end.

#### `/light brief` — Summarized Report
A scannable table: block name, line number, grade, and a one-line summary. Flags anything worth your attention at the bottom.

```
| # | Block Name          | Line | Grade | Summary                                        |
|---|---------------------|------|-------|------------------------------------------------|
| 1 | Server Setup        | L12  | ✅    | Initializes Express server on env-defined port |
| 2 | Auth Middleware      | L34  | 🔵    | Custom JWT validation instead of Passport.js   |
| 3 | Rate Limiter         | L67  | ⚠️    | Manual sliding window — see full comment       |
| 4 | DB Connection        | L89  | ✅    | Standard Supabase client initialization        |

⚠️ Flags Requiring Attention:
- L34 Auth Middleware — Non-standard: custom JWT instead of established library
- L67 Rate Limiter — Unconventional: manual implementation, review before modifying
```

#### `/light full` — Full Picture Report
Every comment in complete form, organized by block, with line numbers. No code — just the full plain-English narrative of what was built and why.

Both commands work **mid-session** (while the build is still in progress) and after the session ends. Long coding sessions — five, ten hours — stay navigable because you can pull a snapshot at any point.

---

## Installation

### Claude Code (Personal)
```bash
# Copy the skill folder to your personal skills directory
cp -r light-code/ ~/.claude/skills/
```

### Claude Code (Project / Team)
```bash
# Add to your repo so everyone on the team gets it
cp -r light-code/ .claude/skills/
git add .claude/skills/light-code/
git commit -m "Add Light Code skill"
```

### Other Platforms
Light Code uses the open SKILL.md standard. It's compatible with **Claude Code, OpenAI Codex CLI, ChatGPT, GitHub Copilot, Cursor**, and other tools that support the SKILL.md format.

---

## Usage

Once installed, activate Light Code at the start of any coding session:

```
"Use light code on this project"
"Build this with light code active"
"I want light code narration"
```

Then call reports whenever you want them:

```
/light brief     → summarized index with grades and flags
/light full      → complete narration of every block
```

Reports save as `.md` files you can keep, share, or hand off.

---

## Why Free?

Light Code is released free and open-source because the concept is more valuable than the file.

If *Light Code* becomes a standard term in the vibe coding world — the way "dark mode" became a standard term in UI — that's the win. The idea should spread.

Use it. Fork it. Improve it. Build on it.

---

## Roadmap

This is v1.0. Planned improvements include:

- [ ] Multi-file session tracking
- [ ] `/light diff` command — show what changed between two report pulls
- [ ] Risk score per project based on grade distribution
- [ ] Team-facing report templates
- [ ] IDE extension concepts

Pull requests and ideas welcome.

---

## About

Light Code was conceived and created by **Gaea** (Leroy), founder of **[Cubed Websites](https://cubedwebsites.com)** — an AI automation and web design agency based in Minneapolis, MN.

The concept grew out of a simple observation: AI is writing more and more of the world's code, and almost none of it is explained. Light Code is one answer to that problem.

---

## License

MIT — free to use, modify, and distribute. Attribution appreciated but not required.

---

*Built with Claude. Narrated with Light Code.*
