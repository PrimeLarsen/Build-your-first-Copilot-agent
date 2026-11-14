# Lab 01: Set up VS Code and Copilot

**Estimated time:** 20 minutes

In this lab you install Visual Studio Code and Git, install the extensions you need — **GitHub Copilot**, **GitHub Copilot Chat**, and the **Copilot Studio** extension — and sign in to both GitHub and your Copilot Studio environment.

## Objectives

- Install VS Code and Git and verify Git works in the terminal.
- Install the GitHub Copilot, Copilot Chat, and Copilot Studio extensions.
- Sign in to GitHub in VS Code so Copilot is activated.
- Sign in to the Copilot Studio extension and see your environments in the Agents pane.

## Prerequisites

- A GitHub account with an active Copilot subscription.
- Access to a Power Platform environment with Copilot Studio (you need rights to create or edit an agent — Lab 02 uses one).
- An Azure DevOps organization, project, and Git repo (used from Lab 03 on).

## Steps

### 1. Install VS Code and Git

1. Download and install [Visual Studio Code](https://code.visualstudio.com/).
2. Install [Git](https://git-scm.com/downloads) if it is not already installed.
3. Open the VS Code integrated terminal (`Ctrl+`` `) and verify:
   ```bash
   git --version
   ```
   If the command prints a version, Git is ready.

### 2. Install the extensions

1. In VS Code, open the **Extensions** view (`Ctrl+Shift+X`).
2. Search for and install each of the following, verifying the publisher is **Microsoft** or **GitHub**:
   - **GitHub Copilot**
   - **GitHub Copilot Chat**
   - **Copilot Studio**

   Or install all three from the terminal:
   ```bash
   code --install-extension GitHub.copilot
   code --install-extension GitHub.copilot-chat
   code --install-extension ms-CopilotStudio.vscode-copilotstudio
   ```

### 3. Sign in to GitHub (activates Copilot)

1. Select the **Accounts** icon at the bottom of the Activity Bar.
2. Select **Sign in with GitHub** and complete the browser sign-in.
3. When the GitHub Copilot status appears in the status bar (or you are prompted in the Copilot Chat panel), confirm you have an active Copilot subscription. If not, start a trial or subscription first.
4. Open the **Copilot Chat** panel (`Ctrl+Alt+I`) and send a test message, for example:
   ```text
   What can you help me build in VS Code?
   ```
   A response means Copilot Chat is working.

### 4. Sign in to the Copilot Studio extension

1. Select the **Copilot Studio** icon in the Activity Bar. The first time, the extension asks for permission to sign in — select **Allow** and complete the sign-in in the browser with your work or school account.
2. In the **Copilot Studio** pane, use the environment dropdown at the top of the **Agents** view. Your accessible Power Platform environments appear, for example `<environment>`.
3. Expand an environment — the agents in it are listed (it can be empty for now).

   > Tip: you can also run the command `Copilot Studio: Focus on Agents View` from the Command Palette (`Ctrl+Shift+P`) to open this pane.

## Check your work

- [ ] `git --version` prints a version in the integrated terminal.
- [ ] GitHub Copilot, Copilot Chat, and Copilot Studio appear in the Extensions view as installed.
- [ ] Copilot Chat answers a test message.
- [ ] The Copilot Studio Agents pane lists at least one environment you can access.

## Try it with Copilot

Paste this into Copilot Chat to warm up:

```text
@workspace Explain what the Copilot Studio extension for VS Code does and list the three
main operations for syncing a local agent folder with Copilot Studio.
```

## Next lab

[Lab 02: Clone your agent and explore its definition](02-clone-agent-and-explore-definition.md)
