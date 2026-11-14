# Troubleshooting

Common issues when developing Copilot Studio agents in VS Code, and how to fix them.

## Sign-in and the Copilot Studio extension

- **"Copilot Studio: Sign In" command not found / sign-in does nothing.** Reload the VS Code window (`Ctrl+Shift+P` > **Developer: Reload Window**), then open the Copilot Studio icon in the Activity Bar and select **Allow** when prompted. Sign in with the account that has access to your `<environment>`.
- **My environment is not listed in the Agents pane.** Check that you are signed in with the correct account and that the environment is shared with you. Ask your Power Platform admin to grant access.
- **Copilot Chat does not respond.** Confirm your GitHub Copilot subscription is active (Accounts icon > GitHub, or the Copilot status in the status bar). Sign out and back in if needed.

## Clone / sync operations

- **Clone agent fails or takes forever.** Check your network connection and environment access. Try the clipboard-URL method: copy the agent URL from Copilot Studio (**Settings** > **Agent details**) and select **Clone agent**.
- **ConcurrencyVersionMismatch when applying changes.** The cloud agent changed after your last sync. Run **Copilot Studio: Get changes**, review the diff, then **Apply changes** again. Rule of thumb: pull before you push.
- **Get changes overwrote local edits.** Get changes downloads the cloud state over local files. Commit your local work first (Git), or run **Preview changes** to inspect before getting.
- **IntelliSense/validation missing in a .mcs.yaml file.** The Copilot Studio language features only activate for files inside a folder created by **Clone agent**. Re-clone, or don't edit copies outside the agent folder structure.

## Git and Azure DevOps

- **Authentication failed on push.** Use a PAT with **Code (Read & write)** scope as the password (Azure DevOps > User settings > Personal access tokens). If you use SSH, make sure your key is added to Azure DevOps.
- **Push rejected: branch protection / policies.** `main` may require pull requests. Push a feature branch instead and open a PR (Lab 06).
- **Merge conflict in a YAML file.** Open the file in VS Code, use **Accept Current/Incoming/Both** or edit manually, remove all `<<<<<<<` markers, save, then `git add -A` and commit the merge.
- **I committed .token_cache*.json by accident.** Remove it and amend: `git rm --cached .token_cache*.json`, add it to `.gitignore`, commit. Then revoke/rotate the token in Azure DevOps / Copilot Studio, because the cached token was exposed.

## Copilot output quality

- **Copilot generated invalid YAML.** Compare against an existing file in the same folder; ask Copilot to fix only schema errors: `@workspace Fix the schema errors in this file according to the Copilot Studio .mcs.yaml schema; do not add new features.`
- **Answers do not match my agent.** Use `@workspace` in the prompt and name the exact file. Copilot works best with the agent folder open as the workspace root.

## Still stuck?

- Official docs: [docs/resources.md](resources.md)
- Extension issues: [github.com/microsoft/vscode-copilotstudio](https://github.com/microsoft/vscode-copilotstudio)
- Open an issue in this training repo.
