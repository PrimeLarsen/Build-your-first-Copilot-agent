# Lab 02: Clone your agent and explore its definition

**Estimated time:** 20 minutes

In this lab you use the **Copilot Studio extension** to **clone** an agent from your Copilot Studio environment to a local folder in VS Code. The clone downloads the full agent definition as YAML files. You then explore the folder structure — this is the code you will edit with GitHub Copilot in Lab 04.

## Objectives

- Create (or locate) an agent in Copilot Studio.
- Clone the agent to a local folder with the Copilot Studio extension.
- Understand the local YAML structure of a cloned agent.

## Prerequisites

- Lab 01 complete: VS Code, Git, extensions, and both sign-ins done.
- A Power Platform environment where you can create or edit an agent.

## Steps

### 1. Make sure you have an agent in Copilot Studio

If you already have an agent, skip to step 2. Otherwise create a starter agent in the web portal:

1. Go to [copilotstudio.microsoft.com](https://copilotstudio.microsoft.com) and select your `<environment>`.
2. Select **Create** > **New agent**, then choose **Describe** and type a short description, for example:
   ```text
   A customer service agent that answers questions about orders, returns, and shipping.
   ```
3. Select **Save** (keep the generated name, or rename it to `<agent-name>`).

### 2. Clone the agent in VS Code

You can clone in any of these ways:

- **From the Agents pane (recommended):** open the **Copilot Studio** icon in the Activity Bar, select your environment in the dropdown, right-click the agent, and select **Clone agent**.
- **From the Command Palette:** `Ctrl+Shift+P` > `Copilot Studio: Clone Agent`, then pick environment, agent, and destination folder.
- **From the agent URL:** in the Copilot Studio web portal open the agent, go to **Settings** > **Agent details**, copy the agent URL (format `https://copilotstudio.microsoft.com/environments/{guid}/bots/{guid}`), then in VS Code select **Clone agent** — the extension detects the URL in your clipboard and marks the agent *(from clipboard)*.

1. In the file picker, choose a folder where you keep your projects (for example a `dev` folder) and create/select a folder named `<agent-name>`. A path without spaces is recommended.
2. Wait for the notification **Agent cloned successfully** (usually 10–30 seconds).
3. VS Code opens the cloned folder in the Explorer.

### 3. Explore the cloned structure

The Explorer now shows the agent definition, structured like this:

```text
<agent-name>/
├── actions/                    # Connector actions (.mcs.yml files)
├── knowledge/
│   └── files/                  # Knowledge source definitions (.yaml)
├── topics/                     # Conversation topics (.mcs.yaml)
├── workflows/                  # Agent tools: each has metadata.yaml + workflow.json
├── trigger/                    # Event triggers (.mcs.yaml)
├── agent.mcs.yaml              # Main agent definition (name, description, instructions)
├── settings.mcs.yml            # Agent configuration settings
├── connectioreferences.mcs.yml # Connection references used by connectors/actions
└── icon.png                    # Agent icon used in the test panel and channels
```

Open `agent.mcs.yaml` and note:

- `name` and `description` of the agent.
- `instructions` — the system prompt that steers the agent's behavior. You will refine this with Copilot in Lab 04.
- References to topics, knowledge, and triggers.

Open one file in `topics/` and notice the **IntelliSense and validation** provided by the Copilot Studio extension: it knows the `.mcs.yaml` schema and flags errors as you type.

> Important: the local folder is a working copy of a **live cloud agent**. Editing files locally does not change the agent in Copilot Studio until you explicitly run **Apply changes** (Lab 05).

## Check your work

- [ ] The agent folder opened in VS Code and you saw **Agent cloned successfully**.
- [ ] You can see `agent.mcs.yaml`, `topics/`, `settings.mcs.yml`, and the other folders.
- [ ] Opening a `.mcs.yaml` file shows Copilot Studio IntelliSense (no plain-text-only experience) and no validation errors.

## Try it with Copilot

```text
@workspace In the cloned agent folder, summarize what agent.mcs.yaml configures and list the
existing topics in topics/. Explain what each section of a topic file (trigger phrases,
nodes, actions) is for, using one real topic file from this folder as the example.
```

## Next lab

[Lab 03: Connect to your Azure DevOps repo](03-connect-to-azure-devops-repo.md) — put this folder under Git and push it to Azure DevOps before you start editing.
