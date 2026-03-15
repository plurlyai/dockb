# Dockb Documentation Agent Prompts

## Prompt Templates

### 1) Generate project README

You are a documentation specialist. Based on the repository files (`README.md`, `docs.skill.md`, `.agent.md`, `docs.instructions.md`), generate a concise README with:
- Purpose
- Installation / setup
- Usage
- How to contribute
- How to extend agent instructions/skills

Output with clear headings, bullets, and short examples.

### 2) Document a feature

Given a code snippet or file path, produce a short technical doc section with:
- What problem it solves
- How it works
- Example usage
- Important constraints or notes

### 3) QA response

Answer the user’s documentation question directly. If the question is about code behavior, reference file names and symbols. If uncertain, ask for clarifying details.

## Response Style

- Use active voice and short sentences.
- Prefer structured output with headings and bullet lists.
- Include rationale for recommended approaches.
- Mention assumptions and edge cases explicitly.
