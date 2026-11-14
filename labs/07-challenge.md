# Lab 07: Challenge

**Estimated time:** 30 minutes

Complete as many challenges as you can. Each one uses the same loop: branch in Git → edit YAML with Copilot Chat → apply changes → test → push → pull request in Azure DevOps.

## Challenges

1. **Escalation topic.** Add a topic that hands the conversation to a human when the user is angry, asks for a refund above a limit, or repeats the same question three times.
2. **Knowledge source.** Add a knowledge source (for example a SharePoint page or an uploaded file with your FAQ) and ask Copilot to wire it into `agent.mcs.yaml` / `knowledge/` following the schema.
3. **Trigger.** Add an event trigger in `trigger/` (for example a welcome trigger that greets users and lists what the agent can do).
4. **Instructions audit.** Ask Copilot to audit `agent.mcs.yaml` instructions for prompt-injection risks and unclear rules, then apply its recommendations.
5. **Team drill.** Pair up: one of you pushes a change to `main`, the other pulls, creates a conflicting edit, and you resolve the merge conflict together in VS Code.
6. **ALM exploration.** Read about Power Platform pipelines and source control for agents (see [docs/resources.md](../docs/resources.md)) and sketch how your agent would move from Dev to Test to Prod automatically.

## Rules

- Every change on its own branch `agent/<description>`.
- Every change applied and tested in the Copilot Studio test chat before the pull request.
- Commit messages in the form `type(scope): message` (for example `feat(agent): ...`, `fix(agent): ...`).
- No secrets or `.token_cache*.json` in any commit.

## Done?

You now know how to develop Copilot Studio agents in VS Code with GitHub Copilot, sync them with the Copilot Studio extension, and collaborate through Git and Azure DevOps. Keep going with the resources in [docs/resources.md](../docs/resources.md).
