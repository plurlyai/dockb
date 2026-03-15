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

## ✅ Purpose

Use this repo to capture and evolve documentation assistant behavior. It contains:

1. **Agent rules**: how to handle docs requests, accuracy checks, and style.
2. **Tool actions**: helper commands and retrieval actions.
3. **Domain knowledge**: curated documentation context and retrieval pipelines.

## 🚀 Setup Guide (GitHub Copilot + VS Code)

> **Scope**: This setup applies per-repository using **GitHub Copilot** with **VS Code** as the code editor. Each repository gets its own agent configuration. Other editors or agent frameworks may require different setup steps.

### Prerequisites

- VS Code installed
- GitHub Copilot extension installed and active
- GitHub Copilot Chat extension installed
- A target repository to add documentation agent support to

### Step 1: Copy the agent definition

Copy [`.agent.md`](.agent.md) into your target repository root. Update the `name`, `description`, and `applyTo` patterns to match your project.

### Step 2: Copy the instructions file

Copy [`docs.instructions.md`](docs.instructions.md) into your target repository root. Update the Project Context section with your project type, language, and target audience.

### Step 3: Copy the skill file

Copy [`docs.skill.md`](docs.skill.md) into your target repository root. Add project-specific actions as needed.

### Step 4 (Optional): Copy the prompt template file

Copy [`docs.prompt.md`](docs.prompt.md) into your target repository root for reusable prompt patterns.

### Customizing for Your Project

1. Update `docs.instructions.md` with your project context (language, framework, audience).
2. Add project-specific actions to `docs.skill.md`.
3. Add prompt templates to `docs.prompt.md` for recurring documentation tasks.
4. Adjust `applyTo` patterns in `.agent.md` to match your file types.

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

1. Open your repo in VS Code.
2. Open GitHub Copilot Chat (Ctrl+Shift+I / Cmd+Shift+I).
3. Ask the agent: "Generate a project overview README."
4. Confirm output includes: purpose, setup, usage, and contribution sections.
5. Confirm style: clear headings, bullets, short code examples, and explicit assumptions.
