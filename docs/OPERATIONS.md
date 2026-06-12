# Operations

Run a helper interactively before enabling a service. Confirm paper-account
mode, selected pairs, timing, and rate limits.

For systemd, review the examples in `scripts/`, update the user and path, then:

```bash
sudo cp scripts/3commas-altrank-bot.service /etc/systemd/system/
sudo systemctl daemon-reload
sudo systemctl enable --now 3commas-altrank-bot.service
sudo systemctl status 3commas-altrank-bot.service
journalctl -u 3commas-altrank-bot.service
```

Never paste unredacted logs into public issues.

