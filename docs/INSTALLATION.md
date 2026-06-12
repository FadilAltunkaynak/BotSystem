# Installation

## Ubuntu or Debian

```bash
sudo apt update
sudo apt install -y git python3 python3-venv python3-pip
git clone --branch staging-publication --single-branch https://github.com/FadilAltunkaynak/BotSystem.git
cd BotSystem
python3 -m venv .venv
source .venv/bin/activate
python -m pip install --upgrade pip
pip install -r requirements.txt
python altrank.py
```

Verify the installation before adding credentials:

```bash
python -m compileall -q .
python altrank.py --help
```

## Windows

Install Git and Python 3.9 or newer, then run:

```powershell
git clone --branch staging-publication --single-branch https://github.com/FadilAltunkaynak/BotSystem.git
cd BotSystem
py -m venv .venv
.\.venv\Scripts\Activate.ps1
python -m pip install --upgrade pip
pip install -r requirements.txt
python altrank.py
```

Verify:

```powershell
python -m compileall -q .
python altrank.py --help
```

## Raspberry Pi

Use a supported 64-bit Raspberry Pi OS release and follow the Debian steps.
Low-memory devices may require dependency build packages.

## Upgrade

```bash
git pull --ff-only
source .venv/bin/activate
pip install -r requirements.txt
```

Back up local `.ini` files before upgrades. They must remain untracked.

## Docker

From the repository root:

```bash
docker compose -f docker/docker-compose.yml build
docker compose -f docker/docker-compose.yml run --rm bot
```

The first run creates configuration in the `bot-config` volume. Inspect and
edit that volume before starting automated trading. Do not bake credentials
into the image.

## Common Problems

- `ModuleNotFoundError`: activate `.venv`, then run
  `pip install -r requirements.txt`.
- `api_key_invalid_or_expired`: verify the local `.ini` value and API
  permissions; never post the key publicly.
- Missing `logs/`: create it with `mkdir logs`.
- PowerShell blocks activation: run
  `Set-ExecutionPolicy -Scope CurrentUser RemoteSigned`, then activate again.
- Service exits immediately: run the helper manually first and inspect the
  redacted output.
