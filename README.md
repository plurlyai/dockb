# dockb Documentation Agent

This repository stores the instruction and skill definitions for a custom documentation agent. It defines:

- Agent behavior rules and policy guardrails
- Supported tool actions and tool bindings
- Domain knowledge and prompt templates for accurate, up-to-date docs responses

## 📁 Repository Structure

| File | Purpose |
|------|---------|
| `.agent.md` | Agent registration and tool bindings |
| `docs.instructions.md` | Behavior rules and guardrails |
| `docs.skill.md` | Capabilities and output expectations |
| `docs.prompt.md` | Reusable prompt templates |
| `docs.changelog.md` | Changelog template for agent-generated projects |

## ✅ Purpose

Use this repo to capture and evolve documentation assistant behavior. It contains:

1. **Agent rules**: how to handle docs requests, accuracy checks, and style.
2. **Tool actions**: helper commands and retrieval actions.
3. **Domain knowledge**: curated documentation context and retrieval pipelines.

## 🧠 Agent Design Guidelines

- Always prefer accurate, concise documentation outputs.
- If uncertain, return verified sources and cite file or URL context.
- Prefer structured responses with headings and code examples when applicable.
- Keep agent responses current by referencing repository docs or external docs in real time.

## 🧩 Extending the Agent

1. Add new `*.skill.md` actions for repo-specific doc tasks.
2. Add triggered tools for file-level retrieval and summarization.
3. Add tests or validation scripts if your agent execution layer supports them.

## ✅ Quick Verification

1. Open your repo in your editor.
2. Ask the agent: "Generate a project overview README."
3. Confirm output includes: purpose, setup, usage, and contribution sections.
4. Confirm style: clear headings, bullets, short code examples, and explicit assumptions.

---

## 🚀 Platform Setup Guides

These guides tell the documentation agent how to adapt the `docs.*` template files in this repository to each platform's expected file structure and conventions.

### GitHub Copilot

Reference: [Adding repository custom instructions for GitHub Copilot](https://docs.github.com/en/copilot/how-tos/configure-custom-instructions/add-repository-instructions)

When generating documentation agent configuration for a GitHub Copilot project, map the template files as follows:

| Template source | Target location | Notes |
|-----------------|-----------------|-------|
| `docs.instructions.md` | `.github/copilot-instructions.md` | Repository-wide custom instructions. Adapt the Project Context section to the target project. |
| `docs.skill.md` | `.github/instructions/docs.instructions.md` | Path-specific instructions. Add `applyTo` frontmatter to scope by file pattern (e.g., `"**/*.md,**/*.mdx"`). Merge skill rules and output expectations here. |
| `docs.prompt.md` | Not directly mapped | Use as reference when crafting prompts. GitHub Copilot does not have a dedicated prompt template file. |
| `docs.changelog.md` | Not directly mapped | Use as reference when generating a `CHANGELOG.md` for the target project. |
| `.agent.md` | `AGENTS.md` at repository root | Convert YAML agent config to Markdown agent instructions. The nearest `AGENTS.md` in the directory tree takes precedence. |

Expected target structure:

```
target-repo/
├── .github/
│   ├── copilot-instructions.md              ← from docs.instructions.md
│   └── instructions/
│       └── docs.instructions.md             ← from docs.skill.md (with applyTo frontmatter)
├── AGENTS.md                                ← from .agent.md
└── CHANGELOG.md                             ← from docs.changelog.md template
```

<!-- ### Claude Code -->

<!-- ### OpenAI Codex -->
