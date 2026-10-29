# Vecto Coder user guide

This guide covers setup and use of Vecto Coder in VS Code. For data handling and security controls, see [Security and privacy](./SECURITY.md).

Sponsored recommendations are optional and can be disabled with the `Vecto Coder: Idlen Ads Enabled` setting. When enabled, Vecto Coder sends derived topic/category/intent signals and a random chat-session identifier to Idlen for ad selection; raw prompts, responses, files, and workspace paths are not sent to Idlen. Ads appear separately from the conversation.

## Open the chat

Open the Vecto Coder icon in the Activity Bar, or run **Vecto Coder: Open Chat** from the Command Palette (`Ctrl+Shift+P` on Windows/Linux, `Cmd+Shift+P` on macOS). Open a workspace folder so the agent can use workspace tools.

## Configure a provider and model

Vecto Coder initializes `~/.vecto/.env` and its user folders on first startup. It does not install sample provider JSON files. Providers can be added and configured in the chat settings, or supplied through your own `*.json` files in `~/.vecto/providers/`. Optional workspace JSON overlays can be named in `vectoCoder.providerFiles`, which is empty by default.

Kilo Gateway Auto Free is included as the default model (`kilo-auto/free`) and does not require a key or account. Before its first use, the chat shows an in-chat data-use notice and asks you to continue. Kilo documents anonymous access at 200 requests per hour per IP. Auto Free may route prompts and outputs to providers that log them or use them to improve services, including NVIDIA trial endpoints. NVIDIA's trial terms restrict those endpoints to internal evaluation and exclude production or business-critical use without a subscription. Use only non-sensitive evaluation prompts with this model; choose a provider and model appropriate to the data and use case.

To add a provider, open chat settings, expand **Add a provider**, choose its protocol, and enter its name, base URL, and API key. OpenAI Chat Completions, OpenAI Responses, Anthropic Messages, Google Gemini, and Ollama are supported. Remote providers require HTTPS; local Ollama can use localhost HTTP. Models are discovered from the configured endpoint where its API supports discovery. Keys are stored in VS Code Secret Storage.

Use **Add key slot** in chat settings to add additional API keys for the selected provider, then choose the slot and save its key. Vecto Coder discovers models after saving and can spread requests across configured credentials. For portable configurations, providers can also reference variables in `~/.vecto/.env`; those values are used only for provider authentication and are never added to terminal or MCP environments.

Run **Vecto Coder: Reload Providers** after changing provider definitions or `.env` values. Choose an available model in the chat picker. Local Ollama providers can use a local endpoint and do not require a cloud API key.

See [provider configuration notes](./README.md#provider-configuration-notes) for protocol examples.

## Ask for workspace help

Describe the desired outcome and identify important files or constraints when known. The agent can list and search workspace files, read relevant portions, and—when the selected model supports tools—create, edit, or delete workspace files. It tracks edits so you can inspect a diff or revert a tracked file from the chat.

The agent can use active editor and recently edited file context to resolve references such as “this file.” Name a path directly when you want to remove ambiguity. For large files, request a specific section or task so the model receives focused context.

## Review changes and commands

Workspace edits are tracked in the chat. Open a changed-file diff to review it, or use the tracked-file revert action to restore the previous contents.

Terminal commands require approval in the Vecto Coder chat. Approve a proposed command to run it, or decline to leave it unexecuted. Set `vectoCoder.terminalPolicy` to `deny` to disable terminal execution. Optional lint and test commands can be configured per workspace; each offered command also requires approval.

## Website access

Public HTTP(S) fetching is controlled by `vectoCoder.networkAccess`, which defaults to `allow`. Set it to `deny` to block website retrieval. This setting does not disable provider API calls or release update checks. Website retrieval blocks private and loopback destinations.

## Optional integrations

### Project rules and coding conventions

Vecto Coder loads project instructions from the workspace root `AGENTS.md`, `.vecto/AGENTS.md`, and `.vecto/rules.md` and applies them as required project conventions. Put durable architecture choices, code style, and workflow preferences in `.vecto/rules.md`; keep secrets and temporary task details out. When you correct a repeatable mistake or irrelevant response, Vecto Coder records the reusable prevention rule there through the tracked file-edit flow. Project rules cannot override your request, permission settings, or safety protections.

### Custom agents and skills

The agent picker includes bundled specialists for frontend work, implementation architecture, API integration, provider credentials, security review, and QA verification. These definitions are guidance for the selected model; they do not grant new tools or permissions. Vecto Coder also bundles a system-design skill covering workload sizing, queues, caching, checkout consistency, autoscaling, and delivery planning. The agent can list and read relevant skills as needed.

Add project-specific agents as `.vecto/agents/<name>.agent.md`, or user-wide agents under `~/.vecto/agents/` and `~/.agents/agents/`. Add project skills as `.vecto/skills/<name>/SKILL.md`; user and bundled skills are also discoverable. Same-name definitions use this priority: workspace, `~/.vecto`, `~/.agents`, then bundled Vecto Coder defaults. On first activation in a local workspace, Vecto Coder creates only `.vecto/rules.md` and preserves existing rules. It does not copy or initialize agent and skill bundles. Create a project skill only when the project needs durable, reusable conventions; bundled guidance remains in the extension, and only selected relevant guidance is loaded for a task. Agent and skill files are guidance; their scripts are never executed.

The bundled `skill-creator-js` includes a browser-first runner. Use **Vecto Coder: Open Skill Creator** from the Command Palette, or open its `browser/index.html` in a browser, to validate and package skills without a separately installed Node.js runtime. Public web fetches from the extension runner use Vecto Coder's network policy and run independent URLs in parallel.

Vecto Coder also bundles the premium `brand-logo-banner-maker` and `html-intro-video-maker` skills with their references, examples, engines, and font assets. They are available automatically through skill discovery. To run their optional CLI tools, use **Vecto Coder: Install Premium Skill Dependencies**. The command copies a selected skill into `.vecto/skills`, asks which Python launcher to use, then sends the Python and (for video export/QA) npm install commands through the normal terminal approval flow. Nothing is installed automatically on activation. Browser playback of generated HTML video needs no Python; PNG/MP4 generation, voice synthesis, and QA use the optional tools described by each skill.

The bundled `svg-animation-maker` skill provides a browser-first SVG Animation Studio. Use **Vecto Coder: Open SVG Animation Studio**, or open `skills/svg-animation-maker/browser/index.html`, to create staged logo intros, path-draw reveals, and compatible path morphs. It keeps the output as offline-safe SVG and includes a reduced-motion fallback.

### MCP servers

Declare stdio MCP servers in `~/.vecto/mcp.json` or workspace `.vecto/mcp.json`. Open **Settings → Configure MCP servers and plugins** to refresh discovered servers and connect or disconnect them. A server starts only after you select **Connect**, and each tool invocation requires its own approval in the chat. See the [MCP configuration example](./README.md#mcp-servers-plugins-and-subagents).

### Plugins and subagents

Declarative plugin bundles can enable related skill guidance from `~/.vecto/plugins` or workspace `.vecto/plugins`. Open **Settings → Configure MCP servers and plugins** to refresh discovered plugins and enable or disable their guidance. The model can delegate independent read-only research tasks to subagents. Subagents cannot edit files, execute commands, connect to MCP servers, or create further subagents.

## Settings reference

Open **Preferences: Open Settings (UI)** and search for `Vecto Coder`.

| Setting | Default | Purpose |
| --- | --- | --- |
| `vectoCoder.checkForUpdates` | `true` | Check the installed release channel for updates. Installation requires confirmation. |
| `vectoCoder.networkAccess` | `allow` | Allow or block public website fetching. |
| `vectoCoder.terminalPolicy` | `ask` | Require in-chat command approval, or disable terminal execution. |
| `vectoCoder.diagnostics.enabled` | `false` | Write redacted lifecycle events to the Vecto Coder Diagnostics output channel. |
| `vectoCoder.providerFiles` | empty | Optional workspace-relative provider overlays. `~/.vecto/providers/` is loaded independently. |
| `vectoCoder.maxConcurrentRequestsPerKey` | `1` | Maximum concurrent requests assigned to one API credential. |
| `vectoCoder.validation.lintCommand` | empty | Optional lint command offered after edits; runs only after approval. |
| `vectoCoder.validation.testCommand` | empty | Optional test command offered after edits; runs only after approval. |

Settings use the `vectoCoder` identifier and each release channel keeps its settings separate.

## Local data locations

- User configuration, providers, agents, skills, plugins, and MCP config: `~/.vecto`.
- Workspace task state: `.vecto/tasks.json`.
- Provider credentials: VS Code Secret Storage or referenced variables in `~/.vecto/.env`.
- Tracked edit snapshots: local VS Code extension storage.

Vecto Coder reads its configuration only from `~/.vecto` and `.vecto` within the workspace. It does not import older configuration directories or task-history locations. See [Security and privacy](./SECURITY.md) and the [Privacy Policy](./PRIVACY_POLICY.md) for details about what is stored and sent to providers.

## Troubleshooting

### No provider or model appears

Confirm the provider appears in chat settings, check its base URL and protocol, and verify that a key is saved in the selected slot. Run **Vecto Coder: Reload Providers** after changing a manual provider file or `.env` value.

### A request fails before reaching the model

Check the provider base URL, selected model, credential reference, network connectivity, and model context/output limits. The input size check uses a conservative byte estimate instead of a provider tokenizer, so a request near the model limit may still be rejected by the provider.

### Terminal execution is unavailable

Check that `vectoCoder.terminalPolicy` is not `deny`. Commands still require an approval action in the chat. Optional validation commands must be configured in workspace settings and approved when offered.

### An update is not offered

Confirm `vectoCoder.checkForUpdates` is enabled and that the installed stable, beta, or test channel has a matching release manifest. Run **Vecto Coder: Check for Updates** to check manually. Updates are channel-specific and require confirmation before installation.

### Diagnostics

Enable `vectoCoder.diagnostics.enabled`, then open **View: Output** and select **Vecto Coder Diagnostics**. Diagnostics redact common secret patterns and exclude prompts and file contents; pattern-based redaction cannot guarantee that arbitrary sensitive text never appears.
