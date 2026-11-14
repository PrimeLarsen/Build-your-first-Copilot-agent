# Lab 06: Git workflow — branch, push, pull, and pull request

**Estimated time:** 30 minutes

You already connected the agent folder to Azure DevOps in Lab 03. In this lab you practice the **daily Git workflow** in VS Code: update your local `main`, create a branch, commit and push your changes, pull your teammates' changes (resolving conflicts), and open a **pull request in Azure DevOps** for review.

## Objectives

- Run the standard branch → commit → push → pull request cycle with the agent definition.
- Push and pull with Git from the VS Code terminal and the Source Control UI.
- Resolve a merge conflict in a `.mcs.yaml` file.
- Open and complete a pull request in Azure DevOps.

## Prerequisites

- Labs 01–05 complete: agent folder is a Git repo with `origin` pointing to your Azure DevOps repo, initial `main` pushed.

## Steps

### 1. Start from an up-to-date main

```bash
git switch main
git pull origin main
```

In the Source Control UI this is the **Sync Changes** button on `main`.

### 2. Create a feature branch and make a change

```bash
git switch -c agent/escalation-topic
```

Make a small change to the agent (for example use Copilot to add an escalation topic in `topics/escalate.mcs.yaml`), then:

```bash
git add -A
git commit -m "feat(agent): add escalation topic for out-of-scope requests"
git push -u origin agent/escalation-topic
```

The first push of a branch uses `-u` to set the upstream; later pushes on the same branch are just `git push`. In the Source Control UI: stage (+), write the message, **Commit**, then **Publish Branch** / **Sync Changes**.

### 3. Pull changes from the team

When a teammate pushed to `main` (or to your branch):

```bash
git fetch origin
git pull origin main
```

- If Git reports **Already up to date**, nothing changed remotely.
- If there are new commits, Git merges them. If both sides edited the same file, continue to step 4.

### 4. Resolve a conflict (guided exercise)

Conflicts happen when you and a teammate edit the same lines of a YAML file.

1. To simulate one: on `main`, edit a line in `agent.mcs.yaml`, commit and push. On your feature branch, edit the same line differently, commit, then `git pull origin main`.
2. VS Code opens the file with conflict markers (`<<<<<<<`, `=======`, `>>>>>>>`) and offers **Accept Current Change**, **Accept Incoming Change**, **Accept Both Changes**, or edit manually.
3. Choose the correct resolution (for YAML, a clean merge of both edits is often right), remove the markers, and save.
4. Finish the merge:
   ```bash
   git add -A
   git commit -m "merge: resolve conflict in agent.mcs.yaml"
   git push
   ```

> Tip: always `git pull` before you start editing and before you push. That prevents most conflicts.

### 5. Open a pull request in Azure DevOps

1. In Azure DevOps, go to **Repos** > **Pull requests** > **New pull request**.
2. Set **source branch** = `agent/escalation-topic`, **target branch** = `main`.
3. Title it like your commit (for example `feat(agent): add escalation topic`), and fill in the description using this repo's [pull request template](../.github/PULL_REQUEST_TEMPLATE.md): summary, changed components, how you tested (test chat scenarios), checklist.
4. Add reviewers from your team and select **Create**.
5. Reviewers comment and approve in the PR; you can push fixes to the same branch — the PR updates automatically.
6. When approved, select **Complete** (merge type: merge commit or squash, per your team's policy).

   Optional, from the CLI with the Azure CLI (`az extension add --name azure-devops`):
   ```bash
   az repos pr create \
     --organization https://dev.azure.com/<organization> \
     --project <project> --repository <repo> \
     --source-branch agent/escalation-topic --target-branch main \
     --title "feat(agent): add escalation topic" --description "Adds topics/escalate.mcs.yaml; tested in DEV test chat."
   ```

### 6. Clean up after the merge

```bash
git switch main
git pull origin main
git branch -d agent/escalation-topic        # local branch
git push origin --delete agent/escalation-topic   # remote branch (or delete it in the PR UI)
```

## Check your work

- [ ] Your feature branch was pushed and visible under **Repos** > **Branches** in Azure DevOps.
- [ ] You pulled `main` and resolved a conflict (or verified there was none).
- [ ] A pull request from your branch to `main` exists, has a reviewer, and was completed.
- [ ] After merging, local `main` contains the change (`git log --oneline -3`).

## Command reference

| Task | Command |
| --- | --- |
| Clone the DevOps repo | `git clone https://dev.azure.com/<organization>/<project>/_git/<repo>` |
| See remotes | `git remote -v` |
| Update local main | `git switch main` then `git pull origin main` |
| New branch | `git switch -c agent/<description>` |
| Stage + commit | `git add -A` then `git commit -m "type(scope): message"` |
| Push branch | `git push -u origin agent/<description>` |
| Pull latest | `git fetch origin` then `git pull origin main` |
| Delete branch | `git branch -d <branch>` and `git push origin --delete <branch>` |

## Next lab

[Lab 07: Challenge](07-challenge.md)
