# Feature Matrix

| Helper | Data/Input | Action | Local State |
| --- | --- | --- | --- |
| AltRank | LunarCrush ranking | Update bot pairs | Config/logs |
| GalaxyScore | LunarCrush score | Update bot pairs | Config/logs |
| CoinMarketCap | Market ranking | Update bot pairs | Config/logs |
| BotAssistExplorer | BotAssist list | Update bot pairs | Config/logs |
| Watchlist | Telegram messages | Trigger new deal | Config/logs |
| Watchlist 100eyes | Telegram signals | Trigger new deal | Config/logs |
| Compound | Finished deals/profit | Update bot sizing | SQLite/config/logs |
| TP Increment | Active deals | Update take profit | SQLite/config/logs |
| Trailing Stop-Loss | Futures deals | Update stop loss | SQLite/config/logs |
| TSL and TP | Deal profit/state | Update stop and TP | SQLite/config/logs |

All helpers require paper-account validation before use with real funds.

