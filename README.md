# dockb Documentation Agent

This repository stores the instruction and skill definitions for a custom documentation agent. It defines:

- Agent behavior rules and policy guardrails
- Supported tool actions and tool bindings
- Domain knowledge and prompt templates for accurate, up-to-date docs responses

## Repository Structure

| File | Purpose |
|------|---------|
| `.agent.md` | Agent registration and tool bindings |
| `docs.instructions.md` | Behavior rules and guardrails |
| `docs.skill.md` | Capabilities and output expectations |
| `docs.prompt.md` | Reusable prompt templates |
| `docs.changelog.md` | Changelog template for agent-generated projects |

## Purpose

Use this repo to capture and evolve documentation assistant behavior. It contains:

1. **Agent rules**: how to handle docs requests, accuracy checks, and style.
2. **Tool actions**: helper commands and retrieval actions.
3. **Domain knowledge**: curated documentation context and retrieval pipelines.

## Agent Design Guidelines

- Always prefer accurate, concise documentation outputs.
- If uncertain, return verified sources and cite file or URL context.
- Prefer structured responses with headings and code examples when applicable.
- Keep agent responses current by referencing repository docs or external docs in real time.

## Extending the Agent

1. Add new `*.skill.md` actions for repo-specific doc tasks.
2. Add triggered tools for file-level retrieval and summarization.
3. Add tests or validation scripts if your agent execution layer supports them.

## Quick Verification

1. Open your repo in your editor.
2. Ask the agent: "Generate a project overview README."
3. Confirm output includes: purpose, setup, usage, and contribution sections.
4. Confirm style: clear headings, bullets, short code examples, and explicit assumptions.

---

## Platform Setup Guides

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

Add agent configuration paths to the target project's `.gitignore` to keep agent files out of version control:

```gitignore
# Agent configuration (GitHub Copilot)
.github/copilot-instructions.md
.github/instructions/
AGENTS.md
```

### AWS Kiro

Reference: [Kiro Steering and Skills](https://kiro.dev/docs/steering/)

When generating documentation agent configuration for an AWS Kiro project, map the template files as follows:

| Template source | Target location | Notes |
|-----------------|-----------------|-------|
| `docs.instructions.md` | `.kiro/steering/docs-instructions.md` | Steering file with always-on inclusion (default). Adapt the Project Context section to the target project. Add frontmatter with `inclusion: auto` if you want conditional loading. |
| `docs.skill.md` | `.kiro/skills/docs-skill.md` | Skill file for documentation capabilities. Add frontmatter with `inclusion: manual` so it can be activated via `#` context key in chat. |
| `docs.prompt.md` | Not directly mapped | Use as reference when crafting prompts. Kiro does not have a dedicated prompt template file; prompt patterns can be embedded in steering or skill files. |
| `docs.changelog.md` | Not directly mapped | Use as reference when generating a `CHANGELOG.md` for the target project. Can be referenced from steering files using `#[[file:CHANGELOG.md]]` syntax. |
| `.agent.md` | `.kiro/steering/agent-config.md` | Convert YAML agent config to a Markdown steering file. Include tool preferences and behavior rules as steering instructions. |

Steering file inclusion modes:

| Mode | Frontmatter | Behavior |
|------|-------------|----------|
| Always (default) | _(none or `inclusion: auto`)_ | Included in every agent interaction |
| Conditional | `inclusion: fileMatch` + `fileMatchPattern: '**/*.md'` | Included only when matching files are in context |
| Manual | `inclusion: manual` | User activates via `#` context key in chat |

Expected target structure:

```
target-repo/
├── .kiro/
│   ├── steering/
│   │   ├── docs-instructions.md             ← from docs.instructions.md
│   │   └── agent-config.md                  ← from .agent.md
│   └── skills/
│       └── docs-skill.md                    ← from docs.skill.md
└── CHANGELOG.md                             ← from docs.changelog.md template
```

Add agent configuration paths to the target project's `.gitignore` to keep agent files out of version control:

```gitignore
# Agent configuration (AWS Kiro)
.kiro/steering/
.kiro/skills/
```

Example steering file with conditional inclusion (`docs-instructions.md`):

```markdown
---
inclusion: fileMatch
fileMatchPattern: "**/*.md,**/*.mdx,**/*.rst"
---

# Documentation Agent Instructions

(contents adapted from docs.instructions.md)
```

Example skill file with manual inclusion (`docs-skill.md`):

```markdown
---
inclusion: manual
---

# Documentation Agent Skill

(contents adapted from docs.skill.md)
```

<!-- ### Claude Code -->

<!-- ### OpenAI Codex -->
