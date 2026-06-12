# BotSystem Ayrintili Kurulum Rehberi

BotSystem tek bir servis degildir. Her `.py` dosyasi ayri bir bot yardimcisidir.
Once bir helper secilir, ilk calistirmada yerel `.ini` dosyasi uretilir, sonra
yalnizca o helper icin gereken degerler doldurulur.

## Helper Secimi

| Ihtiyac | Helper |
| --- | --- |
| AltRank ile parite secimi | `altrank.py` |
| GalaxyScore ile parite secimi | `galaxyscore.py` |
| CoinMarketCap listesi | `coinmarketcap.py` |
| Telegram watchlist | `watchlist.py` |
| 100eyes Telegram sinyali | `watchlist_100eyes.py` |
| Kar birlestirme | `compound.py` |
| Take-profit artirma | `tpincrement.py` |
| Futures trailing stop | `trailingstoploss.py` |
| TSL ve TP birlikte | `tsl_and_tp.py` |

## Ubuntu 24.04

```bash
sudo apt update
sudo apt install -y git python3 python3-venv python3-pip build-essential libffi-dev
git clone --branch staging-publication --single-branch \
  https://github.com/FadilAltunkaynak/BotSystem.git
cd BotSystem
python3 -m venv .venv
source .venv/bin/activate
python -m pip install --upgrade pip setuptools wheel
pip install -r requirements.txt
python -m compileall -q .
```

## Windows PowerShell

```powershell
git clone --branch staging-publication --single-branch https://github.com/FadilAltunkaynak/BotSystem.git
cd BotSystem
py -m venv .venv
Set-ExecutionPolicy -Scope CurrentUser RemoteSigned
.\.venv\Scripts\Activate.ps1
python -m pip install --upgrade pip setuptools wheel
pip install -r requirements.txt
python -m compileall -q .
```

## Ilk Calistirma

Paper Trading hesabiyla baslayin:

```bash
python altrank.py
```

Program `altrank.ini` olusturur. Bu dosya Git tarafindan yok sayilir. Dosyada:

- timezone ve calisma araligi
- yonetilecek bot ID listesi
- 3Commas API key/secret
- kullanilan veri saglayicinin API key'i
- bildirim ayarlari

bulunur.

3Commas anahtarina withdrawal izni vermeyin. Yalnizca gerekli bot ve account
read/write izinlerini verin, mumkunse IP kisitlamasi uygulayin.

## Dogrulama

```bash
python altrank.py --help
python -m compileall -q .
git status --short
```

`git status` ciktisinda `.ini`, log veya credential gorunmemelidir.

## Arka Planda Calistirma

Once helper'i terminalde basariyla calistirin. Ardindan ornek systemd dosyasini
kopyalayip kullanici ve yollarini duzeltin:

```bash
sudo cp scripts/3commas-altrank-env-bot.service /etc/systemd/system/
sudo systemctl edit --full 3commas-altrank-env-bot.service
sudo systemctl daemon-reload
sudo systemctl enable --now 3commas-altrank-env-bot.service
sudo systemctl status 3commas-altrank-env-bot.service
```

Log:

```bash
journalctl -u 3commas-altrank-env-bot.service -f
```

Loglari paylasmadan once key, bot ID, account ID ve Telegram URL degerlerini
silin.

## Docker

```bash
docker compose -f docker/docker-compose.yml build
docker compose -f docker/docker-compose.yml run --rm bot
```

Ilk calistirma config volume icinde `.ini` olusturur. Config tamamlandiktan
sonra:

```bash
docker compose -f docker/docker-compose.yml up -d
docker compose -f docker/docker-compose.yml logs -f bot
```

## Guncelleme

```bash
git status --short
git pull --ff-only
source .venv/bin/activate
pip install -r requirements.txt
python -m compileall -q .
```

Guncelleme oncesinde `.ini` dosyalarini Git disinda sifreli olarak yedekleyin.

