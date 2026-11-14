# Build your first Copilot Studio agent in VS Code with GitHub Copilot

A hands-on introduction and training for developing **Microsoft Copilot Studio agents** the pro-code way: in **Visual Studio Code**, with the **Copilot Studio extension**, AI assistance from **GitHub Copilot**, and **Git source control connected to an Azure DevOps repository**.

Instead of clicking through the Copilot Studio web UI, you will treat your agent as code: clone its full definition to a local folder as YAML, edit it with GitHub Copilot Chat, test and sync changes back to your environment, and collaborate with your team through branches and pull requests in Azure DevOps.

## What you will learn

By completing the labs in this repository, you will be able to:

- Install and sign in to VS Code with the GitHub Copilot, Copilot Chat, and Copilot Studio extensions.
- Clone a Copilot Studio agent to a local folder with the Copilot Studio extension and understand the YAML agent definition (topics, actions, knowledge sources, triggers, settings).
- Connect the agent workspace to a **Git repository in Azure DevOps** and push the initial agent definition.
- Use **GitHub Copilot Chat** in VS Code to write and refine agent instructions, topics, and triggers in YAML.
- Test your agent and synchronize changes between VS Code and Copilot Studio (**Apply changes**, **Get changes**, **Preview changes**, **Reattach Agent**).
- Work with Git like any other code project: create branches, commit, push, pull, resolve conflicts, and open **pull requests in Azure DevOps**.

## Prerequisites

| Requirement | Details |
| --- | --- |
| Computer | Windows, macOS, or Linux with internet access |
| Visual Studio Code | Latest version from [code.visualstudio.com](https://code.visualstudio.com/) |
| Git | Installed and available in the terminal (`git --version`) |
| GitHub account | With an active **GitHub Copilot** subscription (Copilot Chat is included) |
| Microsoft Copilot Studio access | A license and a **Power Platform environment** where you can create or edit agents |
| Azure DevOps | An organization, a project, and a **Git repo** in Repos, with permission to push code and create pull requests |
| Personal access token (PAT) | An Azure DevOps PAT with **Code (Read & write)** scope, for Git over HTTPS |

> Throughout the labs, replace the placeholders: `<organization>` = your Azure DevOps organization, `<project>` = your Azure DevOps project, `<repo>` = your Git repo name, `<environment>` = your Copilot Studio environment, `<agent-name>` = your agent name.

## Lab map

Work through the labs in order. Each lab builds on the previous one.

| # | Lab | What you do | Time |
| --- | --- | --- | --- |
| 01 | [Set up VS Code and Copilot](labs/01-setup-vs-code-and-copilot.md) | Install VS Code, Git, the Copilot and Copilot Studio extensions; sign in | ~20 min |
| 02 | [Clone your agent and explore its definition](labs/02-clone-agent-and-explore-definition.md) | Clone an agent with the Copilot Studio extension; learn the YAML file structure | ~20 min |
| 03 | [Connect to your Azure DevOps repo](labs/03-connect-to-azure-devops-repo.md) | Put the agent definition under Git and push it to Azure DevOps | ~20 min |
| 04 | [Develop with GitHub Copilot Chat](labs/04-develop-with-github-copilot-chat.md) | Use Copilot to write instructions, topics, and triggers in YAML | ~30 min |
| 05 | [Test, apply, and sync changes](labs/05-test-apply-and-sync-changes.md) | Apply changes to Copilot Studio, test, pull remote changes, reattach environments | ~25 min |
| 06 | [Git workflow: branch, push, pull, pull request](labs/06-git-workflow-push-pull-and-pull-request.md) | Branch, commit, push, pull, resolve conflicts, open a PR in Azure DevOps | ~30 min |
| 07 | [Challenge](labs/07-challenge.md) | Extend the agent on your own | ~30 min |

A ready-to-use [Copilot prompt library](prompts/copilot-prompts.md) accompanies every lab.

## How to use this repository

1. Clone this training repository and read along:
   ```bash
   git clone https://github.com/PrimeLarsen/Build-your-first-Copilot-agent.git
   ```
2. Follow the labs in order. Each lab has objectives, step-by-step instructions, and a **Check your work** section.
3. Your **agent files do not live in this repo**. Lab 03 shows you how to connect the cloned agent folder to your own Azure DevOps repo — that repo is the source of truth for your agent.
4. Copy prompts from [prompts/copilot-prompts.md](prompts/copilot-prompts.md) into the Copilot Chat panel (`Ctrl+Alt+I`).

## Repository structure

```text
├── labs/                          # Step-by-step training labs (do these in order)
├── prompts/                       # Copy-paste GitHub Copilot prompts for each lab
├── docs/                          # Troubleshooting and reference links
├── .github/
│   ├── copilot-instructions.md    # Instructions GitHub Copilot follows in this repo
│   └── PULL_REQUEST_TEMPLATE.md   # Template used for pull requests in Azure DevOps
└── README.md
```

## Conventions used in the labs

- Placeholders in angle brackets, for example `<organization>`, must be replaced with your own values.
- Terminal commands are shown for the VS Code integrated terminal (`Ctrl+`` `), but any shell works.
- UI steps refer to VS Code menus and the Copilot Studio extension views.

## Getting help

- See [docs/troubleshooting.md](docs/troubleshooting.md) for common sign-in, sync, and Git issues.
- See [docs/resources.md](docs/resources.md) for official Microsoft documentation and links.
- Open an issue in this repository if a lab step does not work for you.
