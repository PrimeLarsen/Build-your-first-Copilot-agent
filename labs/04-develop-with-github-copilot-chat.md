# Lab 04: Develop with GitHub Copilot Chat

**Estimated time:** 30 minutes

Now the fun part: use **GitHub Copilot Chat** in VS Code to build and refine your agent. You will improve the agent instructions in `agent.mcs.yaml`, generate a brand-new topic file, and review everything Copilot produces before committing it to Git.

## Objectives

- Use Copilot Chat (Ask, Edit, and inline modes) on the agent YAML files.
- Rewrite the agent instructions with Copilot.
- Generate a new topic `.mcs.yaml` file with Copilot and validate it against the schema.
- Use `copilot-instructions.md` to steer Copilot, and commit the change with Git.

## Prerequisites

- Labs 01–03 complete: agent cloned, connected to Azure DevOps, initial push done.

## Steps

### 1. Create a feature branch

Work on a branch, never directly on `main`:

```bash
cd <repo-or-agent-folder>
git switch -c agent/improve-instructions-and-topic
git status
```

Or use the VS Code Source Control view (`Ctrl+Shift+G`): **Create Branch**.

### 2. Refine the agent instructions with Copilot Chat

1. Open `agent.mcs.yaml`.
2. Open Copilot Chat (`Ctrl+Alt+I`) and use **@workspace** so Copilot sees the whole agent folder:
   ```text
   @workspace Review the instructions in agent.mcs.yaml for the <agent-name> agent.
   Rewrite them to be concise and persona-driven: state who the agent is, what it helps
   with (orders, returns, shipping), what it must never do, the tone to use, and when to
   escalate to a human. Keep the YAML structure valid - only change the instructions text.
   ```
3. Copilot proposes an edit. Use **Apply** in chat, or copy the new instructions into the file yourself.
4. Let the Copilot Studio extension validate the file: no red squiggles should remain.

### 3. Generate a new topic with Copilot

In Copilot Chat:

```text
@workspace Create a new topic file topics/return-policy.mcs.yaml for the <agent-name>
agent. The topic should handle customer requests to return an order: ask for the order
number, check that the order is within the 30-day return window, explain the refund
timeline, and escalate to a human agent if the order is older than 30 days. Follow the
Copilot Studio .mcs.yaml topic schema (kind: Topic) exactly as used by the existing
files in topics/ - do not invent schema properties.
```

1. Review the generated file carefully: Copilot can produce plausible-looking but invalid YAML. Check the `kind`, required fields, and node structure against an existing topic file.
2. Fix anything invalid (the extension's IntelliSense and problem panel help), then save.
3. Register the topic where the schema expects it (for example in `agent.mcs.yaml` or the topics manifest the extension maintains) — ask Copilot:
   ```text
   @workspace How is this new topic referenced by the agent definition? Show me where to
   add it so the agent can use it, using the pattern of the existing topics.
   ```

### 4. Edit inline with Ctrl+I

1. Select a block inside an existing topic (for example a message node).
2. Press `Ctrl+I` for inline chat and ask:
   ```text
   Make this message friendlier and add a follow-up question that moves the conversation
   toward resolving the return.
   ```
3. Accept or discard the suggestion, and save.

### 5. Let copilot-instructions.md steer Copilot (optional but recommended)

- This training repo ships a [`.github/copilot-instructions.md`](../.github/copilot-instructions.md). If you copied it into your agent repo, Copilot automatically follows it (valid schema only, small topics, no secrets, validate before applying).
- You can also add your own rules there, for example your company's tone of voice or naming conventions for topics.
- Optional power-up: install the **Skills for Copilot Studio** plugin (`microsoft/skills-for-copilot-studio` from the marketplace) — it teaches Copilot the Copilot Studio YAML schema and adds slash commands for authoring, testing, and troubleshooting agents.

### 6. Commit your change

```bash
git add -A
git commit -m "feat(agent): clarify instructions and add return-policy topic"
```

Or use the Source Control view: stage the changes, type the message, **Commit**.

## Check your work

- [ ] You are on branch `agent/improve-instructions-and-topic`, not `main`.
- [ ] `agent.mcs.yaml` instructions are rewritten and the file validates.
- [ ] A new `topics/return-policy.mcs.yaml` exists, follows the `.mcs.yaml` topic schema, and has no validation errors.
- [ ] The change is committed (`git log --oneline -1` shows your commit).

## Tips

- Always review AI-generated YAML against an existing file in the same folder — Copilot mirrors patterns well but can hallucinate properties.
- Ask Copilot to explain anything it generated: `@workspace Explain the trigger phrases block in topics/return-policy.mcs.yaml`.
- Keep prompts specific: name the file, the schema, and the business rule (for example "30-day return window").

## Next lab

[Lab 05: Test, apply, and sync changes](05-test-apply-and-sync-changes.md)
