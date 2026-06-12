# BotSystem

Open-source automation helpers for managing 3Commas trading bots, watchlists,
pair selection, take-profit rules, trailing stops, and portfolio compounding.

> This software is not financial advice. Trading can result in partial or total
> loss. Start with a paper account and grant API keys only the permissions a
> helper actually needs.

## Status

This repository is a public, sanitized baseline. It contains no production
credentials, private configuration, logs, databases, deployment archives, or
PhoenixOS source code.

## Helpers

| Helper | Purpose |
| --- | --- |
| `altrank.py` | Select pairs using AltRank market data |
| `galaxyscore.py` | Select pairs using GalaxyScore market data |
| `coinmarketcap.py` | Build pair selections from CoinMarketCap data |
| `botassistexplorer.py` | Process BotAssist data |
| `watchlist.py` | Trigger deals from Telegram watchlists |
| `watchlist_100eyes.py` | Integrate 100eyes watchlist signals |
| `compound.py` | Reinvest realized profits into bot settings |
| `tpincrement.py` | Adjust take-profit settings |
| `trailingstoploss.py` | Manage futures trailing stop-loss behavior |
| `tsl_and_tp.py` | Combine trailing stop-loss and take-profit management |

## Quick Start

Requirements: Python 3.9+, Git, a 3Commas account, and credentials for the
specific external data providers used by your chosen helper.

```bash
git clone --branch staging-publication --single-branch https://github.com/FadilAltunkaynak/BotSystem.git
cd BotSystem
python -m venv .venv
source .venv/bin/activate
python -m pip install --upgrade pip
pip install -r requirements.txt
python altrank.py
```

Expected result: the first run creates `altrank.ini` and exits or reports the
settings that must be completed. Add credentials only to that local file, then
run the same command again.

On Windows PowerShell, activate with:

```powershell
.\.venv\Scripts\Activate.ps1
```

The first run creates a helper-specific `.ini` file. Edit that local file and
never commit it. See [Installation](docs/INSTALLATION.md) and
[Configuration](docs/CONFIGURATION.md) for the full walkthrough.

## Security

- Use paper trading first.
- Never enable withdrawal permissions.
- Prefer IP-restricted API keys.
- Keep generated `.ini` files outside version control.
- Rotate any credential that has appeared in a commit, log, screenshot, issue,
  or chat message.

Report vulnerabilities privately as described in [SECURITY.md](SECURITY.md).

## Docker and Services

Container examples are under `docker/`. Example systemd units are under
`scripts/`; review users, paths, permissions, and environment handling before
installing them.

## Documentation

- [Installation](docs/INSTALLATION.md)
- [Configuration](docs/CONFIGURATION.md)
- [Operations](docs/OPERATIONS.md)
- [Architecture](docs/ARCHITECTURE.md)
- [Wiki index](docs/WIKI.md)

## License and Attribution

The BotSystem helper code is distributed under the MIT License. It is derived
from the `3commas-cyber-bots` project and retains the upstream license and
copyright terms. See [LICENSE](LICENSE) and
[THIRD_PARTY_NOTICES.md](THIRD_PARTY_NOTICES.md).
