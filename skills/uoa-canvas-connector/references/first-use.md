# First-use onboarding

The public package contains no account setup. Each new user authenticates their own account, and each runtime may have a separate browser session.

## Suggested agent introduction

“我可以通过浏览器连接奥克兰大学 Canvas。请告诉我想使用的账号标识和浏览器（也可以直接在浏览器输入账号），以及手动登录还是使用已有密码管理器。密码和 MFA 验证请在浏览器中完成，不需要发到聊天里。登录后我会确认是否能进入 Canvas。”

Ask only for information not already available. Account identifiers are optional when the user chooses fully manual sign-in. Do not delay opening the sign-in page while waiting for an optional preference.

## User prompt examples

Chinese:

> 使用 uoa-canvas-connector 连接我的 UoA Canvas。账号我会在浏览器输入，密码和 MFA 我自己完成。登录后帮我查找我指定课程的作业要求。

English:

> Use uoa-canvas-connector to connect to my UoA Canvas. I will enter my account, password, and MFA in the browser. After verifying access, help me find the assignment requirements for the course I specify.

Optional autofill:

> Use my chosen browser's existing session or supported password-manager autofill. If that is unavailable, leave the sign-in page open for me. Remember only my non-secret browser preference if private storage is available.

## Agent sequence

1. Discover available browser tools and state their relevant limitations.
2. Reuse the intended user's session or open the Canvas entry in a visible/handoff-capable browser.
3. Check the sign-in origin and let the user enter credentials, or use their selected secure autofill mechanism. Do not capture sign-in screenshots containing personal details for documentation.
4. Let the user finish MFA; check for authenticated Canvas navigation afterward.
5. Report verified connection or the specific blocker, then continue the requested course task.

A university account does not grant access to every course. An empty dashboard or inaccessible course is an access limitation, not permission to try another person's account.
