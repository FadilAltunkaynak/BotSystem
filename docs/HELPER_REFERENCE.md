# Helper Reference

## Common Settings

Most helpers generate an INI file containing:

- `timezone`: IANA timezone such as `Europe/Istanbul`
- `timeinterval`: seconds between cycles
- `debug`: verbose local logging
- `logrotate`: log retention in days
- `notifications`: enable Apprise notifications
- `notify-urls`: one or more private notification URLs
- `3c-apikey`: dedicated 3Commas API key
- `3c-apisecret`: matching API secret

Lists such as `botids` must use JSON list syntax:

```ini
botids = [123456, 789012]
```

## Pair Selection Helpers

`altrank.py` and `galaxyscore.py` require LunarCrush settings and a target
number of pairs. `coinmarketcap.py` uses a CoinMarketCap API key and configured
rank ranges. `botassistexplorer.py` uses BotAssist list names and ranges.

## Position Management Helpers

`compound.py`, `tpincrement.py`, `trailingstoploss.py`, and `tsl_and_tp.py`
change bot or deal settings. Test every threshold with a paper account and a
single bot before expanding the bot ID list.

## Telegram Helpers

`watchlist.py` and `watchlist_100eyes.py` require Telegram developer API ID,
API hash, phone number, and channel identifier. Telegram API hashes and Apprise
URLs are secrets.

## Safe Rollout

1. Generate config.
2. Add paper-account credentials.
3. Configure one bot.
4. Run interactively with debug logging.
5. Confirm selected pairs and actions.
6. Disable debug logging.
7. Enable systemd or Docker supervision.
8. Expand scope gradually.

