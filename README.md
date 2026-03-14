# dockb Documentation Agent

This repository stores the instruction and skill definitions for a custom documentation agent used by agent frameworks. It defines:

- agent behavior rules and policy guardrails
- supported tool actions and tool bindings
- domain knowledge and prompt templates for accurate, up-to-date docs responses

## 📁 Repository Structure

This project is intentionally minimal and acts as a configuration workspace for custom agent behavior.

- `README.md`: this document
- `*.instructions.md` / `*.prompt.md` / `*.agent.md`: custom agent config files (if present)
- `SKILL.md` or `AGENTS.md`: skill metadata and custom behavior definitions

## ✅ Purpose

Use this repo to capture and evolve documentation assistant behavior for a custom agent. It should contain:

1. **Agent rules**: how to handle docs requests, accuracy checks, update frequency, and style.
2. **Tool actions**: helper commands and retrieval actions (search docs, read file, summarize, API list).
3. **Domain knowledge**: curated documentation knowledge, context, and retrieval pipelines.

## 🚀 How to Use

1. Open the repository in VS Code.
2. Create or update agent files:
   - `docs.instructions.md` (high-level behavior and guardrails)
   - `docs.skill.md` (tool and domain action definitions)
   - `docs.prompt.md` (response templates and safety prompts)
3. Use your custom agent workflow (Copilot/Agent extension) to run docs tasks.
4. Iterate based on usage: add new tools, update knowledge, and refine top-level instructions.

## 🧠 Agent Design Guidelines

- Always prefer accurate, concise documentation outputs.
- If uncertain, return verified sources and cite file or URL context.
- Prefer structured responses with headings and code examples when applicable.
- Keep agent responses current by referencing repository docs or external docs in real time.

## 💡 Example Components

- `docs.instructions.md`:
  - What the agent is for
  - What it should not do
  - Response style rules
- `docs.skill.md`:
  - Tool definitions (search, read, list, transform)
  - Domain constraints and metadata
- `docs.prompt.md`:
  - User prompt templates
  - Safety filters and fallback responses

## 🧩 Extending the Agent

1. Add new `*.skill.md` actions for repo-specific doc tasks.
2. Add triggered tools for file-level retrieval and summarization.
3. Add tests or validation scripts if your agent execution layer supports them.

## 📚 Notes

This repository currently has a minimal skeleton. Add your production instruction and skill definitions to enable the full documentation agent experience.

---

If you want, I can also add a starter `docs.instructions.md` and `docs.skill.md` scaffold now so your custom doc agent is ready to run in one pass.