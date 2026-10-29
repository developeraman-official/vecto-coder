# Changelog

All notable Vecto Coder changes are recorded here. Versions follow SemVer. Stable releases use `X.Y.Z`; beta and test releases use `X.Y.Z-beta.N` and `X.Y.Z-test.N` and are packaged under separate extension identities.

## 1.1.3

- Refresh the chat home with guided starting points, clearer product capabilities, recent-chat continuity, and a direct feature-request path.
- Add a polished settings experience with an About DeveloperAman profile, selected projects, capabilities, and public contact links.
- Bundle premium brand identity and HTML intro-video skills with their references, examples, browser engines, and optional dependency setup.
- Add a browser-first SVG Animation Studio for cinematic logo intros, path-draw reveals, compatible path morphs, and offline animated SVG export.
- Expand brand generation with distinctive ribbon, prism, wave, and lens marks plus art-directed abstract banners and stronger visual review guidance.
- Improve responsive, reduced-motion, and safe external-link behavior across the webview UI.

## 1.1.2

- Retry automatic release checks after transient failures instead of suppressing retries for six hours.
- Add a manual update check in chat settings; it remains available when automatic checks are disabled.
- Align request token estimation, Git commit cleanup, and marketplace plugin/MCP integration with current implementation.

## 1.1.1

- Refresh the marketplace and VSIX README with current installation, workflow, permissions, provider, and privacy guidance.
- Add stable-ID active-chat history retrieval with eviction and stale-read signals, bounded excerpts, and secret redaction.

## 1.0.10

- Run install, build, and test commands from the selected workspace project directory, with workspace-bound path validation and reusable integrated terminals per project.
- Obfuscate the test-channel extension bundle only; stable and beta remain minified without obfuscation.
- Preserve prior versioned VSIX packages when building and publishing newer channel releases.

## 1.0.8

- Raise the continuous tool-call limit to 2,000 while retaining the 500-round task cap, and persist the expanded continuation history.
- Add Settings controls to refresh and manage discovered MCP servers and plugin bundles.
- Prefer exact symbol and line searches before reading code, and use commands for the active terminal shell.
- Increase transient provider retry attempts to ten.

## 1.0.7

- Add a Settings panel to refresh and manage discovered MCP servers and plugin bundles.
- Raise continuous task limits to 2,000 tool calls and 500 rounds, with expanded persisted progress history.
- Prefer exact symbol and line searches before reading code, and use commands for the active terminal shell.
- Harden task-history, tool-output, and chat redaction for common credential formats.
- Add configurable public web access and terminal execution policies, plus opt-in local structured diagnostics.
- Add cross-platform extension CI and release updater flow coverage for all three channels.
- Continue longer tool-based tasks across bounded model-call rounds and resume interrupted requests from their recorded tool results.
- Use valid channel-specific Activity Bar container IDs for beta and test packages.

## 1.0.5

- Use public HTTPS image URLs in the extension README so images render in VS Code's extension details view.
- Remove upstream provider and third-party license file names from the public README while keeping the license text in `LICENSE.txt`.
- Remove obsolete duplicate third-party license documents from the production distribution.

## 1.0.4

- Keep the public Free AI bearer value out of plain-text bundle literals while preserving gateway authentication.
- Publish the README image assets with the production documentation so GitHub release pages render correctly.
- Use Vecto Coder branding in the Free AI first-use notice and explain third-party data handling without upstream provider names.

## 1.0.3

- Add chat settings for configuring OpenAI Chat Completions, OpenAI Responses, Anthropic Messages, Google Gemini, and Ollama providers.
- Support multiple credential slots per provider and discover available models from configured provider endpoints.
- Authenticate the built-in Kilo Gateway Free AI route with its public anonymous credential.
- Add npm commands to build each release channel and publish source or production updates.

## 1.0.2

- Mark Vecto Coder original components as proprietary and reserve commercial, redistribution, modification, and resale rights for written licensing and partnership agreements.
- Preserve separate MIT notices for Microsoft-derived, Kilo Code, and OpenCode components.
- Update package license metadata and release documentation.

## 1.0.1

- Use Vecto-only configuration, credentials, task history, view IDs, and command IDs under `.vecto` locations.
- Publish user-facing Terms and Conditions and Privacy Policy, including clear provider-controlled data handling notes.
- Include the legal documents and Kilo Gateway provider configuration in every release channel package.

## 0.1.3

- Added isolated stable, beta, and test release channels with checksum-verified updates.
- Added Vecto Coder user configuration and workspace task-history migration paths.
