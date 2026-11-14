# Copilot instructions for Copilot Studio agent repositories

These instructions are picked up automatically by GitHub Copilot when you work in this repository or in a cloned Copilot Studio agent folder.

## Agent definition conventions

- A cloned Copilot Studio agent is a folder of YAML files: `agent.mcs.yaml` (main definition), `settings.mcs.yml`, `connectioreferences.mcs.yml`, and folders `topics/`, `actions/`, `knowledge/`, `workflows/`, `trigger/`.
- Component files use the `.mcs.yaml` / `.mcs.yml` extension and the Copilot Studio schema (`kind: Bot`, `kind: Topic`, and so on). Never invent properties that are not in the schema; rely on IntelliSense from the Copilot Studio extension.
- Keep each topic focused on one conversation path. Prefer several small topics over one large topic.
- Use variables instead of hard-coded values, and reference knowledge sources instead of pasting content into instructions.
- Keep agent `instructions` concise and persona-driven: who the agent is, what it can and cannot do, tone, and escalation rules.

## When editing

- Validate YAML after every AI-assisted change; fix schema errors before applying changes.
- Make small, reviewable changes and write a clear commit message per change.
- Never commit `.token_cache*.json` or any credentials, connection strings, or secrets.
- After editing, run the Copilot Studio extension's **Preview changes** or validate the files before **Apply changes**.

## When asked to explain

- Explain Copilot Studio concepts (topics, triggers, actions, knowledge sources, connection references) in plain language, with a short YAML example.
