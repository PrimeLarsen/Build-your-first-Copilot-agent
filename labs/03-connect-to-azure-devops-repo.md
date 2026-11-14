# Lab 03: Connect the agent to your Azure DevOps repo

**Estimated time:** 20 minutes

An agent definition is code — so it belongs in source control. In this lab you connect the cloned agent folder from Lab 02 to a **Git repository in Azure DevOps** and push the initial version. From now on, every change you make in VS Code is tracked with Git and shared with your team through Azure DevOps.

## Objectives

- Get the HTTPS clone URL of your Azure DevOps Git repo.
- Put the agent folder under Git and push it to Azure DevOps.
- Create a personal access token (PAT) for Git over HTTPS authentication.
- Agree on a branch naming convention.

## Prerequisites

- Lab 02 complete: the agent is cloned to a local folder `<agent-name>`.
- An Azure DevOps project with a Git repo. The repo URL has the form:
  ```text
  https://dev.azure.com/<organization>/<project>/_git/<repo>
  ```
- Permission to push code and create pull requests in that repo.

## Steps

### 1. Get the repo URL from Azure DevOps

1. In Azure DevOps, open your project and go to **Repos** > **Files**.
2. Select **Clone**, choose **HTTPS**, and copy the URL.
3. If the repo is empty, select **Initialize** to create the default `main` branch with a README.

### 2. Create a personal access token (PAT)

Git over HTTPS to Azure DevOps uses a PAT as the password:

1. In Azure DevOps, select your profile picture > **Personal access tokens** (or **User settings** > **Personal access tokens**).
2. Select **+ New Token**, give it a name (for example `vscode-agent-dev`), set expiration, and select scope **Code (Read & write)**.
3. Copy the token once and store it in a password manager. You will paste it as the password when Git prompts you. (VS Code's credential manager usually remembers it after the first successful push.)

### 3. Connect the agent folder to the DevOps repo

Choose the approach that matches your situation:

**Option A — clone the DevOps repo first, then clone the agent into it (recommended for teams):**

```bash
cd <your-projects-folder>
git clone https://dev.azure.com/<organization>/<project>/_git/<repo>
```

Open the cloned repo folder in VS Code (**File** > **Open Folder**), then repeat Lab 02's clone step and choose the repo folder as the parent, so the agent lands in `<repo>/agents/<agent-name>`.

**Option B — the agent folder already exists (from Lab 02), add the remote:**

```bash
cd <your-projects-folder>/<agent-name>
git init
git remote add origin https://dev.azure.com/<organization>/<project>/_git/<repo>
git branch -M main
git add -A
git commit -m "chore: add initial agent definition for <agent-name>"
git push -u origin main
```

Enter your Azure DevOps username and the PAT from step 2 when prompted.

### 4. Verify in Azure DevOps and set conventions

1. In Azure DevOps, go to **Repos** > **Files** — you should see `agent.mcs.yaml`, `topics/`, and the other agent files on `main`.
2. Agree with your team on these conventions (used in all later labs):
   - `main` is the default branch and always holds the last applied, tested agent definition.
   - Work happens on short-lived branches named `agent/<short-description>`, for example `agent/return-policy-topic`.
   - Never commit `.token_cache*.json` (auth token cache of the extension) — it is already in this repo's `.gitignore` if you copy it into your agent repo.
3. Optional: add this repo's [`.gitignore`](../.gitignore) and [`.github/copilot-instructions.md`](../.github/copilot-instructions.md) to your agent repo so Copilot follows the same rules there.

### 5. Team workflow (why this matters)

- The **first developer** clones the agent from Copilot Studio, initializes Git, and pushes to Azure DevOps (what you just did).
- **Every other developer** runs `git clone` on the Azure DevOps repo, opens the agent folder in VS Code, and runs the command `Copilot Studio: Reattach Agent` to connect that local folder to their Copilot Studio environment.
- From then on, collaboration is pure Git: clone, branch, commit, push, pull request.

## Check your work

- [ ] `git remote -v` in the agent folder shows your Azure DevOps URL as `origin`.
- [ ] **Repos** > **Files** in Azure DevOps shows the agent YAML files on `main`.
- [ ] A second run of `git push` says **Everything up-to-date**.
- [ ] `.token_cache*.json` files (if any) are not listed by `git status`.

## Try it with Copilot

```text
@workspace Explain the difference between "Clone agent" (Copilot Studio extension) and
"git clone" (Azure DevOps repo) in this workflow, and when each developer should run
"Copilot Studio: Reattach Agent".
```

## Next lab

[Lab 04: Develop with GitHub Copilot Chat](04-develop-with-github-copilot-chat.md)
