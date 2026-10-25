# UoA Canvas Connector

用于验证 AI agent 通过浏览器连接奥克兰大学 Canvas、读取获授权课程材料及执行交互流程的可行性。

Portable agent instructions for University of Auckland Canvas browser sign-in and course research. No Canvas API token required. This is an independent community project, not an official University of Auckland or Instructure product.

## 使用限制与免责声明（下载前请阅读）

**本开源项目仅用于技术验证。不得用来违反校规、课程要求或学术诚信规定，不得用于考试作弊、未经允许的 AI 辅助答题、代考、冒名操作或绕过评估限制。** 测验相关功能仅限教师明确允许的练习、演示或测试环境；用户授权不能替代学校或课程的许可。不清楚是否允许时，请先向教师确认。

本项目为独立社区项目，与奥克兰大学、Instructure 及相关 agent 工具提供方无隶属、背书或官方认证关系。软件按 MIT 许可证以“现状”提供，不保证准确性、可用性、兼容性、登录成功或生成内容正确。自动化可能误操作或丢失数据，使用前应自行核查权限、课程规则及重要操作；用户对自己的使用行为负责。在适用法律允许的范围内，作者和贡献者不对使用或无法使用本项目产生的损失承担责任；本声明不排除依法不得排除或限制的责任。

**Technical validation only.** Do not use this project to violate university rules, course requirements, or academic integrity policies, including exam cheating, unauthorized AI-assisted answers, impersonation, or bypassing assessment restrictions. Assessment interactions are limited to instructor-permitted practice, demonstrations, or test environments. User consent does not replace institutional permission. This independent project has no official affiliation or endorsement. It is provided “AS IS” under the MIT license, without guarantees of correctness, availability, compatibility, or successful authentication. Users are responsible for their actions. Liability is limited only to the extent permitted by applicable law; non-excludable rights and liabilities remain unaffected.

## 首次使用

1. 按下表把 `skills/uoa-canvas-connector/` **整个文件夹**复制到你的 agent 技能目录，保留 `references/`。首次加载后确认 agent 能发现它；必要时刷新技能列表或重启会话。
2. 确保 agent 有可交互、可观察、可交还用户登录的浏览器工具。Skill 本身不会安装浏览器或 MCP。
3. 告诉 agent 要连接 UoA Canvas、使用哪个账号/浏览器，以及手动登录还是使用已有密码管理器。账号也可自行在浏览器输入；**密码和 MFA 验证在浏览器中完成，无需发送到聊天**。
4. Agent 应先复用你的现有登录态，或打开学校登录页面；看到已认证的 Canvas 导航后才能报告连接成功。

可直接发送：

> 使用 uoa-canvas-connector 连接我的 UoA Canvas。账号、密码和 MFA 我会在浏览器输入。请先确认连接成功，再帮我找指定课程的作业要求。

需要自动登录时：

> 优先使用我的现有浏览器会话或我选择的密码管理器自动填充。如果不可用，请让我手动登录。只在有私有存储时记住非敏感的浏览器偏好。

会话过期、换 agent 或换用户后可能需要重新登录。此项目不包含任何人的账号、密码、课程资料或浏览器会话。

## Agent 兼容性

下表为 **2026-10-25 官方文档核查**。支持 `SKILL.md` 加载不等于已经实测通过 UoA SSO；本次未进行这些工具的登录端到端测试。完整来源和验收步骤见 [COMPATIBILITY.md](COMPATIBILITY.md)。

| Agent | 项目安装目录（放入完整技能文件夹） | 结论 |
| --- | --- | --- |
| Codex | `.agents/skills/uoa-canvas-connector/` | 文档确认格式支持；执行需要浏览器工具 |
| Claude Code | `.claude/skills/uoa-canvas-connector/` | 文档确认格式支持；执行需要浏览器工具 |
| DeepSeek Harness (`dsh`) | `.dsh/skills/uoa-canvas-connector/` | 文档确认文件夹发现支持；需启用对应 skill 能力和浏览器工具 |
| OpenCode | `.opencode/skills/uoa-canvas-connector/` | 文档确认格式支持；执行需要浏览器工具 |
| Gemini CLI | `.gemini/skills/uoa-canvas-connector/` | 文档确认格式支持；执行需要浏览器工具 |
| Cursor | `.cursor/skills/uoa-canvas-connector/` | 文档确认格式支持；执行需要浏览器工具 |
| 其他 agent / 仅聊天界面 | 依宿主说明加载或手动阅读完整 skill 及引用 | 未核查原生发现；无浏览器时只能处理用户提供的材料 |

DeepSeek Harness 与 DeepSeek 普通聊天/API 是不同的运行环境；Claude Code 与 Claude 聊天界面也不能直接等同。能否实际执行取决于运行工具、网络、会话权限和登录交接能力。

## 能做什么

- 使用浏览器登录 Canvas，不要求创建 Canvas API token。
- 查阅指定课程的页面、模块、公告、资料和作业说明，提供可追溯来源。
- 在教师明确允许的练习、演示或测试环境中验证测验交互：区分填写、保存、上传附件和最终提交，并核查保存状态。
- 在工具不具备登录、下载或上传能力时给出具体交接步骤。

连接请求不自动授权开启测验、提交作业或批量下载课程。使用者必须遵守上述使用限制；宿主 agent 的规则和权限始终适用。

## 下载提示

源码包 `uoa-canvas-connector-source.zip` 用于审阅和分发；技能包 `uoa-canvas-connector-skill.zip` 用于安装完整 skill。**下载或安装前，请阅读本页使用限制、包内 `NOTICE.md` 和 MIT 许可证：仅用于技术验证，禁止违反校规和考试作弊。** 下载、安装或成功登录均不代表学校允许在评估中使用 AI。

Before downloading either archive, read the usage restrictions, bundled `NOTICE.md`, and MIT license. Technical validation only; no rule violations or exam cheating. Installation or successful login does not establish permission to use AI in assessments.

## English quick start

Copy the complete skill folder into your agent's supported skill directory, keeping its references. Enable an interactive browser with a user login handoff. Ask the agent to connect to UoA Canvas; enter credentials and MFA in the browser. The agent must verify authenticated Canvas navigation before claiming access. Optional autofill requires your selected supported password manager. The skill includes no accounts, browser runtime, API service, or guaranteed persistent session.

## Privacy and distribution

公开文件仅包含通用说明、大学公共入口和匿名示例。个人配置应存于仓库之外的私有用户存储。不要提交密码、账号标识、Cookie、课程下载、截图或会话导出；`.gitignore` 只是辅助，发布时仍需逐项检查文件清单。

源文件：[`SKILL.md`](skills/uoa-canvas-connector/SKILL.md)。许可证：[MIT](LICENSE)。
