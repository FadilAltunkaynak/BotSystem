# Troubleshooting

## Dependency Errors

Activate the virtual environment and reinstall:

```bash
source .venv/bin/activate
python -m pip install --upgrade pip setuptools wheel
pip install -r requirements.txt
```

On Debian-based systems, install `build-essential` and `libffi-dev` if a wheel
must be compiled.

## Configuration Errors

Run the helper once to generate its `.ini`. JSON-like values such as bot ID
lists must retain square brackets. Keep booleans as `True` or `False`.

## API Errors

- Invalid key: verify the local `.ini` and rotate the credential if exposed.
- Invalid signature: check for whitespace or a mismatched secret.
- Permission denied: grant only the documented read/write permissions.
- Rate limit: increase the helper interval; do not create aggressive retries.

## Telegram Errors

Confirm the developer API ID/hash, phone number, and channel identifier. Treat
the API hash and notification URL as secrets.

## Safe Issue Report

Include OS, Python version, helper name, commit hash, and a redacted traceback.
Never include `.ini`, API keys, bot/account IDs, Telegram credentials, or
signed request data.

