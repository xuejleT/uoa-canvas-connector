# Runtime capability checks

Skill loading and browser execution are separate capabilities. This package intentionally has no fixed browser API names, executable hooks, hard-coded tool allowlist, API token dependency, or automatically installed MCP servers.

Before connecting, discover whether the current host can:

- Open/reuse a browser tab, observe the page and current URL, click controls, fill non-secret inputs, and re-read state.
- Show or hand off that same session for user password/MFA entry, then resume after login.
- Download relevant files, inspect PDFs, or upload attachments when the task requires them.

Use only tools documented by the host. An HTTP fetch or search tool cannot replace an interactive authenticated session. A headless remote browser without a user login handoff may require additional setup; do not ask the user to send passwords just to compensate.

An optional browser MCP such as [Microsoft Playwright MCP](https://github.com/microsoft/playwright-mcp) can supply browser capabilities in compatible clients. The user configures it through their agent's documented setup. This skill does not install it, change security settings, export cookies, or guarantee that a particular deployment permits UoA SSO. Browser profiles and network access belong to that runtime and can differ across agents.

If browser interaction works but a later capability is missing, complete the supported portion and explain the exact handoff (for example, a ready file that the user must upload). Do not claim a complete quiz save or upload without observable evidence.
