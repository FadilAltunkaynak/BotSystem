# Installation

## Ubuntu or Debian

```bash
sudo apt update
sudo apt install -y git python3 python3-venv python3-pip
git clone https://github.com/FadilAltunkaynak/BotSystem.git
cd BotSystem
python3 -m venv .venv
source .venv/bin/activate
python -m pip install --upgrade pip
pip install -r requirements.txt
python altrank.py
```

## Windows

Install Git and Python 3.9 or newer, then run:

```powershell
git clone https://github.com/FadilAltunkaynak/BotSystem.git
cd BotSystem
py -m venv .venv
.\.venv\Scripts\Activate.ps1
python -m pip install --upgrade pip
pip install -r requirements.txt
python altrank.py
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

