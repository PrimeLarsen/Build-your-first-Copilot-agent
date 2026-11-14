# Pull request template for Copilot Studio agent changes

Use this template when you open a pull request for agent definition changes in Azure DevOps (Lab 06).

## Summary

<!-- What does this change do, and why? One or two sentences. -->

## Changes

<!-- Bullet list of the agent components changed: agent.mcs.yaml, topics/..., actions/..., knowledge/..., trigger/..., settings.mcs.yml -->

- [ ] `agent.mcs.yaml` instructions updated
- [ ] New topic added: `topics/<name>.mcs.yaml`
- [ ] Existing topic(s) modified: <!-- list -->
- [ ] Knowledge source added or updated
- [ ] Trigger added or updated
- [ ] Settings or connection references changed

## Testing

<!-- How was the agent tested after Apply changes? Include test chat scenarios and results. -->

- [ ] Applied changes to the `<environment>` environment in Copilot Studio
- [ ] Tested in the Copilot Studio test chat (list scenarios below)
  - Scenario 1:
  - Scenario 2:
- [ ] Verified no schema/validation errors in VS Code (Copilot Studio extension)

## Checklist

- [ ] Changes committed on a feature branch (`agent/<description>`), not on `main`
- [ ] Pulled the latest `main` before opening this PR and resolved any conflicts
- [ ] Commit messages describe the change
- [ ] No secrets, tokens, or `.token_cache*.json` files committed
- [ ] Reviewer from the team added
