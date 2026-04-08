# Claude Skills for Founders

> Production-ready Claude system prompts used to build [ReQuested](https://requested.gg) — a B2B marketplace for the video game industry — as a solo founder.

These are not tutorial prompts. They are the actual system prompts I run in production, every week, to replace functions that would otherwise require a team.

---

## What's a "skill"?

A Claude skill = a system prompt that turns Claude into a specialized expert for a specific, recurring task.

Instead of writing a long prompt each time, you store the instruction set once and reuse it. The model becomes your **strategy advisor**, your **legal reviewer**, your **growth marketer** — on demand.

---

## Stack context

- **Product:** ReQuested — B2B micro-task marketplace for game studios & freelance talent
- **Model:** Claude (Sonnet / Opus via API and Claude Code)
- **Runtime:** Claude Code + MCP servers (Notion, Supabase, Gmail)
- **Workflow:** AI-native solo development — no engineers, no agencies

---

## Skills

| Category | Skill | What it does |
|----------|-------|--------------|
| 🎯 Strategy | [Startup CTO Advisor](skills/strategy/startup-cto-advisor.md) | Tech/product decisions, build-vs-buy, roadmap trade-offs |
| 🎯 Strategy | [Competitive Teardown](skills/strategy/competitive-teardown.md) | Structured competitor analysis on 6 axes |
| 🎯 Strategy | [Marketplace Metrics Coach](skills/strategy/marketplace-metrics.md) | Unit economics, take rate, LTV/CAC, GMV for two-sided platforms |
| ⚖️ Legal | [GDPR & Legal Advisor](skills/legal/gdpr-legal.md) | ToS, privacy policy, contribution rules, GDPR basics |
| 📈 Growth | [Growth Strategist](skills/growth/growth-strategist.md) | Acquisition channels, zero-budget growth, community building |
| 📈 Growth | [LinkedIn Content](skills/growth/linkedin-content.md) | High-reach posts: hooks, angles, copy — founder personal brand |
| 🛠️ Product | [Senior Frontend Reviewer](skills/product/senior-frontend.md) | React/TS code review, refactor suggestions, accessibility |
| 🛠️ Product | [Senior Architect](skills/product/senior-architect.md) | System design, scalability trade-offs, C4 diagrams |
| ⚙️ Ops | [Sprint Reporter](skills/ops/sprint-reporter.md) | Weekly progress report from git log + task tracker |
| ⚙️ Ops | [Brand Voice Guardian](skills/ops/brand-voice.md) | Tone consistency across all user-facing copy |

---

## How to use

### Option A — Claude.ai (no code)

1. Open a new Claude conversation
2. Click **"System prompt"** (or start a Project)
3. Paste the content of any `.md` file from this repo
4. Start prompting in the conversation

### Option B — Claude API

```python
import anthropic

with open("skills/strategy/competitive-teardown.md") as f:
    system_prompt = f.read()

client = anthropic.Anthropic()
message = client.messages.create(
    model="claude-opus-4-5",
    max_tokens=4096,
    system=system_prompt,
    messages=[{"role": "user", "content": "Analyze Fiverr vs Upwork vs Malt for a gaming freelance marketplace."}]
)
print(message.content[0].text)
```

### Option C — Claude Code (MCP)

Store skills in `.claude/skills/` in your project root. Claude Code picks them up automatically as slash commands.

```
your-project/
└── .claude/
    └── skills/
        ├── competitive-teardown/
        │   └── SKILL.md
        └── sprint-reporter/
            └── SKILL.md
```

---

## Design principles

1. **Role first.** Every prompt starts by defining who Claude is — not what it should do. The role frames everything else.
2. **Context-aware.** Each skill has a section for project context that you fill in once. No re-explaining your product every session.
3. **Output-driven.** Prompts specify format (tables, bullet lists, structured sections) so outputs plug directly into your workflow.
4. **Honest constraints.** Legal and financial prompts explicitly state they don't replace professionals. Accuracy > false confidence.

---

## Contributing

Found a bug in a prompt? Have a variant that performs better? PRs welcome.

Format: one skill per `.md` file, following the template in [TEMPLATE.md](TEMPLATE.md).

---

## Author

**Antoine Defer** — Solo founder, AI-native builder.
Building [ReQuested](https://requestedgames.com) at the intersection of product, AI and the video game industry.

[LinkedIn](www.linkedin.com/in/antoine-defer-6385b221b) · [Email](mailto:defer.antoine@gmail.com)

---

*These prompts are open source (MIT). Use them, fork them, improve them.
