<p align="center">
  <img src="https://raw.githubusercontent.com/developeraman-official/vecto-coder/master/media/brand/vecto-coder-readme-banner.png" alt="Vecto Coder — an AI coding agent for your VS Code workspace" width="100%">
</p>

# Vecto Coder

**An AI coding agent that never works behind your back.**

Most AI coding tools ask you to trust them. Vecto Coder asks you to review them: every edit is a diff, every command needs a yes, and every model is your choice.

Vecto Coder runs in VS Code–compatible editors, understands your project, and does real work, while keeping every consequential decision visible and reversible.

Published as **`developeraman.vecto-coder`** on the [VS Code Marketplace](https://marketplace.visualstudio.com/items?itemName=developeraman.vecto-coder) and Open VSX. Free to install.

<p align="center">
  <img src="https://raw.githubusercontent.com/developeraman-official/vecto-coder/master/media/vecto-coder-workflow.png" alt="Vecto Coder workflow: describe a goal, review file edits, and approve terminal commands" width="100%">
</p>

---

## Why Vecto Coder is different

| | |
|---|---|
| 🔍 **Review before it sticks** | File edits are tracked as diffs in your editor. Keep what you like, revert what you don't. File deletion through the agent is disabled. |
| 🛡️ **Permissions you choose** | Three clear modes: Manual, Safe, and Full Access. You decide how much freedom the agent gets. |
| 🔌 **Bring any model** | Use cloud or local providers with your own keys, add multiple credential slots, or start instantly with **Free AI**. |
| 🧑‍💻 **Your own specialists** | Choose built-in agents for frontend, architecture, APIs, credentials, security, and QA, or add your own. |
| 🔁 **Built for long projects** | Resume recent conversations and continue where you left off, without wasting your model budget on stale context. |
| 🔐 **Private by design** | Keys live in secure editor storage or your own environment file, never in workspace files. |

---

## Control, not just capability

| Mode | What it does |
|---|---|
| **Manual** | Asks before every terminal command. |
| **Safe** | Auto-approves only a small list of read-only commands. Everything else still needs your approval. |
| **Full Access** | For deliberate configuration work beyond your workspace. Edits still go through the same diff review. Sensitive files stay blocked. |

Hard guardrails apply in every mode:

- Credential and private-key files are blocked from model reads and edits.
- Edits to protected operating-system directories are blocked.
- Common destructive and system-control command patterns are refused, even after approval.
- Scripts can have effects a command check can't predict, so review each command before approving it.

### Interactive or Auto

- **Interactive:** the agent only stops to ask about decisions that materially affect security, data loss, compatibility, cost, or architecture.
- **Auto:** routine choices use safe, reversible defaults so work keeps moving.

---

## What you can do

- **Understand a workspace:** ask questions, search for relevant code, and use your active or recently edited file as context.
- **Resume project work:** return to recent chats and continue the selected conversation.
- **Select specialized guidance:** use bundled agents, or add project agents under `.vecto/agents/` and personal agents under `~/.vecto/agents/` or `~/.agents/agents/`. Project definitions take priority. Project skills under `.vecto/skills/<name>/SKILL.md` are discovered alongside your own, and only relevant guidance is used for a task.
- **Manage providers in chat:** add a cloud or local provider from Settings with its name, API protocol, endpoint, and credentials. Model catalogs load automatically.
- **Bring your own guidance:** keep shared rules and skills in `~/.vecto/skills/`.

---

## Install

Search for **Vecto Coder** in the Extensions view of VS Code or an Open VSX–based editor, or run:

```bash
code --install-extension developeraman.vecto-coder
```

### Release channels

Stable, beta, and test install as separate extensions and update from their own channel.

| Channel | Extension ID | Install |
|---|---|---|
| Stable | `developeraman.vecto-coder` | [VS Code Marketplace](https://marketplace.visualstudio.com/items?itemName=developeraman.vecto-coder) |
| Beta | `developeraman.vecto-coder-beta` | [Download latest beta VSIX](https://raw.githubusercontent.com/developeraman-official/vecto-coder/master/channels/beta/latest.vsix) |
| Test | `developeraman.vecto-coder-test` | [Download latest test VSIX](https://raw.githubusercontent.com/developeraman-official/vecto-coder/master/channels/test/latest.vsix) |

For beta or test, download the VSIX and choose **Install from VSIX** in the Extensions view.

---

## Get started

1. Open a project folder and select the Vecto Coder icon in the Activity Bar.
2. Choose **Free AI** to start without an API key, or open chat Settings to add your own provider.
3. Select a model and describe the outcome you want.
4. Review tracked file edits in the editor and approve any proposed terminal command in chat.

On first startup, Vecto Coder creates `~/.vecto/` and an empty `~/.vecto/.env` template. Provider definitions load from the single `~/.vecto/providers/providers.json` manifest; older protocol-specific provider files are migrated automatically. Each entry declares its API type with `protocol` (for example `openai-chat-completions`, `openai-responses`, `anthropic-messages`, `ollama`, or `custom-http`). To use portable environment credentials, add a variable to `~/.vecto/.env` and reference it from a provider definition. **Never put real keys in workspace files or share them publicly.**

---

## Privacy and safety

Vecto Coder may show occasional text-only sponsored recommendations. When enabled, derived topic/category/intent signals and a random chat-session identifier are sent to Idlen for ad selection, and impression/click events may be measured. Raw prompts, model responses, file contents, and workspace paths are not sent to Idlen. Disable sponsored recommendations with the `Vecto Coder: Idlen Ads Enabled` setting.

- Only the workspace context needed to answer your request is sent to the provider you selected.
- **Free AI** sends prompts and related context to third-party providers, which may log or use them to improve their services. Don't send confidential or personal data through this route.
- File changes are tracked for review, and permission modes control which local paths and commands the agent can use.

---

## Documentation

- 📘 [User Guide](https://github.com/developeraman-official/vecto-coder/blob/master/USER_GUIDE.md)
- 🔒 [Security notes](https://github.com/developeraman-official/vecto-coder/blob/master/SECURITY.md)
- 🛡️ [Privacy Policy](https://github.com/developeraman-official/vecto-coder/blob/master/PRIVACY_POLICY.md)
- 📄 [Terms and Conditions](https://github.com/developeraman-official/vecto-coder/blob/master/TERMS_AND_CONDITIONS.md)
- 📝 [Changelog](https://github.com/developeraman-official/vecto-coder/blob/master/CHANGELOG.md)

## License

Use of Vecto Coder is governed by [LICENSE.txt](https://github.com/developeraman-official/vecto-coder/blob/master/LICENSE.txt) and the [Terms and Conditions](https://github.com/developeraman-official/vecto-coder/blob/master/TERMS_AND_CONDITIONS.md).

---

<p align="center">Built by <a href="https://developeraman.vercel.app">developeraman</a></p>
