# Optional private login preferences

Remember preferences only when the current user asks. Use the host's supported private per-user memory outside the repository, skill directory, shared workspace, and distribution archive. If no such storage exists, explain that persistence is unavailable; manual login still works.

Useful non-secret values are the fixed Canvas/login origins, chosen browser/profile description, authentication preference (`existing_session`, `manual`, `browser_password_manager`, or `supported_secret_store`), and last verified time. Store an account identifier only when the user explicitly asks to remember it. A secret-store reference must be an opaque item reference chosen by that user, never a secret value.

Never store passwords, tokens, OTPs, recovery codes, cookies, browser storage, SAML assertions, or browser profile exports. Do not read credential databases or print secrets through shell commands. Do not introduce an installation-specific exception for plaintext credentials.

On later connections, check that the preference belongs to the same user and account. Discover available browsers again; stored tab IDs are not durable. A remembered timestamp is historical, not evidence that the present session is authenticated. If secure autofill is unavailable, use manual browser sign-in. Saving a new password or changing account/profile requires the user's applicable authorization.
