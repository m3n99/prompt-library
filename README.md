# 📚 Prompt Library

A clean, growing collection of high-quality prompts — each in its own file with a short description and the ready-to-use prompt.

## Structure

```
prompts/
└── topic-name/
    └── prompt-name.md
```

Each `.md` file contains:

- **What it does** — one paragraph
- **The prompt** — copy-paste ready

## Prompts

| Prompt                                                             | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
| ------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| [Code Reviewer](prompts/code-reviewer/prompt.md)                   | A production-grade, diff-first AI code reviewer that adapts to any language, any stack, any team size. Configure it once — it never asks again. Feed it a single file, a git diff, a commit SHA, a pull request, or a full repo audit. It activates only the review categories relevant to what actually changed, ranks every finding by severity, delivers a clean verdict (merge / don't merge), and optionally writes the full report to `/code-review-output.md` in your project root. |
| [AI Interview Trainer](prompts/interview-trainer/prompt.md)        | Simulates a realistic human interviewer (Dante) with adaptive difficulty, onboarding setup, strike system, lifeline, and a detailed multi-dimension evaluation report                                                                                                                                                                                                                                                                                                                      |
| [Product Blueprint Generator](prompts/product-blueprint/prompt.md) | Transforms your product idea, target market, and Claude API goals into a concise, investor-ready blueprint covering strategy, positioning, architecture, AI integration, data pipelines, and a phased execution roadmap.                                                                                                                                                                                                                                                                   |
| [Project Blueprint Generator](prompts/project-blueprint/prompt.md) | Turns a topic + skill level + difficulty into a full project blueprint with architecture, steps, timeline, and a master AI coding prompt                                                                                                                                                                                                                                                                                                                                                   |

---

> Adding a new prompt? Drop a `.md` file in `prompts/your-topic/` and update the table above.
