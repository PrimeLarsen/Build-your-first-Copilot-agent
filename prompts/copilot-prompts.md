# Copilot prompt library

Copy-paste prompts for GitHub Copilot Chat (`Ctrl+Alt+I`) in VS Code, organized by lab. Replace `<agent-name>`, `<environment>`, and other placeholders. The `@workspace` tag lets Copilot see all files in the open agent folder.

## Lab 01 — Setup

```text
What exactly does the Copilot Studio extension for VS Code do, and how is "Clone agent"
different from "git clone"?
```

## Lab 02 — Clone and explore

```text
@workspace Summarize agent.mcs.yaml in plain language: name, description, instructions,
and which topics/knowledge/triggers are referenced.
```

```text
@workspace Pick one file in topics/ and explain every block of it (trigger phrases,
variables, nodes, actions) using that file as the example.
```

## Lab 03 — Azure DevOps connection

```text
@workspace Which files in this agent folder should never be committed to Git, and why?
Show me the matching .gitignore entries.
```

```text
@workspace Write the exact git commands to: clone our Azure DevOps repo
https://dev.azure.com/<organization>/<project>/_git/<repo>, create branch
agent/<description>, commit all changes, and push the branch for the first time.
```

## Lab 04 — Develop with Copilot

```text
@workspace Review the instructions in agent.mcs.yaml for the <agent-name> agent and
rewrite them to be concise and persona-driven: who the agent is, what it helps with,
what it must never do, the tone, and when to escalate to a human. Keep the YAML valid.
```

```text
@workspace Create topics/return-policy.mcs.yaml: a topic that handles return requests -
ask for the order number, allow returns within 30 days, explain the refund timeline, and
escalate orders older than 30 days to a human. Follow the Copilot Studio kind: Topic
schema exactly as used by existing files in topics/; do not invent properties.
```

```text
@workspace Add trigger phrases to topics/return-policy.mcs.yaml so the topic starts on
messages like "I want a refund", "return my order", "send it back".
```

```text
@workspace I selected a message node in a topic. Make it friendlier and end with a
follow-up question that moves the conversation forward. (Use inline chat with Ctrl+I.)
```

```text
@workspace Audit the instructions in agent.mcs.yaml for prompt-injection risks and
unclear rules, and propose concrete improvements.
```

## Lab 05 — Test and sync

```text
@workspace List the Copilot Studio extension commands to apply local changes to the
cloud agent, preview remote changes, get remote changes, and reattach to another
environment, and the order you should run them in.
```

```text
@workspace My test chat ignores the new topic. What are the likely causes (changes not
applied, wrong environment attached, cached test session, not published) and how do I
check each one?
```

## Lab 06 — Git workflow

```text
@workspace I pulled main and got a merge conflict in topics/greeting.mcs.yaml. Explain
what the <<<<<<< / ======= / >>>>>>> markers mean and how to resolve them correctly in
VS Code, step by step.
```

```text
@workspace Write a pull request description for my branch agent/<description> using
this template: summary, changed components, test scenarios in the Copilot Studio test
chat, and a checklist. Base it on `git log main..HEAD`.
```

## Lab 07 — Challenge

```text
@workspace Design a topics/escalate.mcs.yaml topic that detects an angry user or an
out-of-scope request and hands off to a human with a summary of the conversation so far.
Follow the existing topic schema in this folder.
```

```text
@workspace Add a knowledge source for our FAQ document to this agent definition:
which files change (knowledge/ folder, agent.mcs.yaml), what the YAML should look like,
and how I verify it after Apply changes.
```
