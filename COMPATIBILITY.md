# Compatibility and verification

Reviewed: 2026-10-25. Evidence level: official documentation and local static package validation. No cross-agent authenticated UoA Canvas run was performed for this release candidate. Loading a skill does not supply browser automation or prove SSO compatibility.

## Format and discovery

The package uses the [Agent Skills directory convention](https://agentskills.io/specification): matching folder/name, YAML frontmatter, a Markdown body, and relative references. It avoids host-specific hooks, substitutions, fixed tool names, and mandatory tool allowlists.

| Host | Project skill root | Official evidence | Browser execution status |
| --- | --- | --- | --- |
| Codex | `.agents/skills/` | [OpenAI customization documentation](https://learn.chatgpt.com/docs/customization/overview) describes skill folders and project discovery | Requires a supported browser tool; not tested here |
| Claude Code | `.claude/skills/` | [Claude Code skills documentation](https://code.claude.com/docs/en/skills) describes filesystem skills | Requires a supported browser tool; not tested here |
| DeepSeek Harness (`dsh`) | `.dsh/skills/` (also `.agents/skills/` in current docs) | [Official skills subsystem](https://github.com/deepseek-ai/deepseek-harness/blob/master/docs/subsystems/skills.md) describes direct `<name>/SKILL.md` discovery | Skill provider/consumer and browser tools must be available in the active deployment; not tested here |
| OpenCode | `.opencode/skills/` | [OpenCode skills documentation](https://opencode.ai/docs/skills/) lists local discovery roots | Requires a supported browser tool; not tested here |
| Gemini CLI | `.gemini/skills/` | [Gemini CLI skills documentation](https://geminicli.com/docs/cli/skills/) lists workspace/user skills | Requires a supported browser tool; not tested here |
| Cursor | `.cursor/skills/` | [Cursor skills documentation](https://prod.cursor.com/help/customization/skills) describes project skill folders | Requires a supported browser tool; not tested here |

Place the `uoa-canvas-connector` folder directly inside the chosen root, not an extra repository nesting layer. Follow the host's current refresh/activation instructions. Enterprise policies may disable skills or tools. In `dsh`, a custom composition may omit the filesystem skill provider or skill consumer; consult that deployment's configuration rather than assuming every plugin is enabled.

DeepSeek is a model/provider as well as the name behind Harness. A model API by itself does not scan skill folders or operate browsers. Other hosts that can read Markdown may follow these instructions when explicitly loaded, but that is manual instruction reuse, not verified native skill support.

## Browser capability

Minimum: navigate, observe visible page/current URL, click and fill controls, let the user authenticate in that session, then resume inspection. Optional: relevant file download, PDF inspection, attachment upload. Check capabilities separately because a successful login does not imply upload support.

[Microsoft Playwright MCP](https://github.com/microsoft/playwright-mcp) is one optional browser provider for compatible MCP clients. Configure it using its official documentation and the host's supported setup. This package does not install it or prescribe security changes. Do not assume that MCP support alone proves a working UoA login handoff.

## Acceptance procedure for each target host

Use the tester's own account and keep all evidence private. Record host/version, browser provider/version, date, and pass/fail without publishing account identity, course content, screenshots, or storage state.

1. Install the complete skill and verify it is discoverable and its references load.
2. Ask to connect with fully manual browser credential entry. The agent should not ask for a chat password or create a plaintext credential file.
3. Verify actual URL observation, sign-in handoff, MFA completion by the user, and authenticated Canvas navigation.
4. Request one permitted course page; verify its title and source URL against the visible page.
5. Start a fresh agent session and verify that authentication is checked again. Do not assume another host shares its session.
6. If needed, test download and upload separately in an authorized practice context. Do not open a real graded attempt solely to test this skill. Confirm that a connection-only request does not start or submit a quiz.
7. Test the no-browser case: the agent should report the missing capability and offer to read supplied materials.

Only label a host “end-to-end tested” after these applicable checks have actually passed. Keep failed or unsupported capabilities explicit; repeat verification after material host/browser changes.
