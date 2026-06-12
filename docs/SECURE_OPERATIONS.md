# Secure Operations

- Create a separate API key for BotSystem.
- Never grant withdrawal permission.
- Restrict the key by IP when supported.
- Run under a dedicated unprivileged OS user.
- Set configuration permissions to owner-only.
- Keep logs local and redact them before sharing.
- Back up INI files only into encrypted private storage.
- Rotate credentials after operator changes or suspected exposure.
- Monitor repeated authentication errors and unexpected bot changes.

For systemd, use `ProtectSystem`, `PrivateTmp`, `NoNewPrivileges`, and a
restricted `ReadWritePaths` policy after confirming the helper's runtime paths.

