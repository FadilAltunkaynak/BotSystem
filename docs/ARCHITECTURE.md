# Architecture

Each helper is an independent long-running Python process. Shared functions
under `helpers/` handle logging, configuration, notifications, and 3Commas API
requests. Helper-specific loops fetch external signals, validate pairs or
positions, apply configured rules, and issue narrowly scoped API updates.

Runtime configuration and logs are intentionally local and excluded from Git.

