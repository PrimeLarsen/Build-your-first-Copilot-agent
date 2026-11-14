# Lab 05: Test, apply, and sync changes

**Estimated time:** 25 minutes

Your local YAML files are a working copy of a live cloud agent. The Copilot Studio extension synchronizes the two sides. In this lab you **apply** your Lab 04 changes to Copilot Studio, **test** the agent in the test chat, then **pull** a change made in the web UI back to VS Code and see the diff in Git.

## Objectives

- Apply local changes to the Copilot Studio environment (**Apply changes**).
- Test the updated agent in the Copilot Studio test chat.
- Preview and get remote changes (**Preview changes**, **Get changes**).
- Reattach the local folder to a different environment (**Reattach Agent**).

## Prerequisites

- Labs 01–04 complete: changes committed on a branch in the local agent folder.

## Steps

### 1. Apply changes (local → Copilot Studio)

1. In VS Code, open the **Source Control** view (`Ctrl+Shift+G`) or the Explorer over the agent folder — the Copilot Studio extension adds sync icons/actions for the open agent folder.
2. Run **Copilot Studio: Apply changes** (Command Palette `Ctrl+Shift+P`, or the sync icon). You can also find it on the agent folder in the Explorer context menu.
3. Wait for the success notification. Your agent in the `<environment>` environment is updated immediately — this is a live editing experience.

> If you get a **ConcurrencyVersionMismatch** error, someone else changed the cloud agent after your last sync. Run **Get changes** first, review the diff, then apply again.

### 2. Test the agent in Copilot Studio

1. Go to [copilotstudio.microsoft.com](https://copilotstudio.microsoft.com), select `<environment>`, and open `<agent-name>`.
2. In the **Test your agent** panel, select **Start new test session**.
3. Test the new behavior, for example:
   ```text
   I want to return my order 12345
   ```
   and an escalation case:
   ```text
   I want to return an order from 3 months ago
   ```
4. If the answers are off, iterate: adjust the topic or instructions locally (with Copilot's help), **Apply changes** again, and start a new test session.
5. When satisfied, select **Publish** in Copilot Studio to make the changes live for real users.

### 3. Pull remote changes (Copilot Studio → local)

1. In the Copilot Studio web UI, make a small change to the agent (for example edit the description in **Settings** > **Agent details**).
2. Back in VS Code, run **Copilot Studio: Preview changes** to see the diff between your local files and the cloud agent **without** modifying anything.
3. Run **Copilot Studio: Get changes** to download the cloud state into your local folder.
4. In the Source Control view, the changed file (for example `agent.mcs.yaml`) appears as modified. Review the diff, then commit:
   ```bash
   git add -A
   git commit -m "chore(agent): sync agent description from Copilot Studio"
   ```

### 4. Move between environments (Reattach Agent)

When your agent also exists in a Test or Production environment:

1. Run `Copilot Studio: Reattach Agent` from the Command Palette.
2. Select the target environment and the agent.
3. Your local folder is now connected to that environment: **Apply changes** pushes there, **Get changes** pulls from there. Test in that environment's test pane before promoting further.

> For multi-environment deployment at scale, use Power Platform **solutions and pipelines** instead of manual reattach — see [docs/resources.md](../docs/resources.md).

## Check your work

- [ ] **Apply changes** succeeded and the web UI shows your new topic/instructions.
- [ ] The test chat answers the return-policy scenario and the escalation scenario correctly.
- [ ] After a web UI change, **Get changes** brought the change into VS Code and Git shows the diff.
- [ ] You ran **Reattach Agent** at least once (or confirmed you only have one environment).

## Try it with Copilot

```text
@workspace I applied my changes but the test chat still answers like the old instructions.
List the most likely causes (not applied, wrong environment attached, test session cached,
publish not done) and the exact commands/steps to check each one in VS Code and
Copilot Studio.
```

## Next lab

[Lab 06: Git workflow — branch, push, pull, and pull request](06-git-workflow-push-pull-and-pull-request.md)
