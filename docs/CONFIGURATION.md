# Configuration

Run a helper once to generate its example `.ini` file. Configure only the
providers needed by that helper.

Security rules:

- Create dedicated keys.
- Grant read, bot-read, bot-write, and account-read only when required.
- Never grant withdrawal access.
- Restrict keys by source IP where supported.
- Store configuration with owner-only filesystem permissions.
- Redact keys, signatures, bot IDs, and Telegram URLs from logs and reports.

Use a 3Commas paper account until behavior is understood and monitored.

