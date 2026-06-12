# BotSystem Tanitimi

BotSystem, 3Commas botlarini harici piyasa verileri ve kullanici tarafindan
belirlenen kurallarla yonetmek icin gelistirilmis bagimsiz Python
yardimcilarindan olusan bir otomasyon paketidir.

Her helper tek basina calisir. Kullanici yalnizca ihtiyac duydugu helper'i
etkinlestirir ve ona ozel yerel `.ini` dosyasini yapilandirir.

## Temel Yetenekler

### Akilli Parite Secimi

`altrank.py`:

- LunarCrush AltRank verilerini takip eder
- Botun base para birimi ve borsa pazarini algilar
- 3Commas blacklist ve market verilerini kontrol eder
- Hacim ve siralama kurallarina gore parite listesi hazirlar
- Liste degistiginde bot paritelerini gunceller

`galaxyscore.py`:

- GalaxyScore tabanli coin siralamasi kullanir
- AltRank ve minimum hacim filtreleri uygulayabilir
- Botun destekledigi gecerli pariteleri secer

`coinmarketcap.py`:

- CoinMarketCap siralama araliklarini kullanir
- Farkli bot gruplari icin farkli baslangic/bitis araliklari tanimlayabilir
- Market ve blacklist kontrolunden sonra bot paritelerini gunceller

`botassistexplorer.py`:

- 3c-tools BotAssist listelerini okur
- Liste ve sira araligina gore parite uretir
- Bot/borsa uyumlulugunu kontrol eder

### Telegram Sinyal Otomasyonu

`watchlist.py`:

- Telegram kanal mesajlarini dinler
- Desteklenen sinyal formatlarindan coin/parite bilgisi cikarir
- USDT ve BTC bot gruplarina yeni deal tetikleyebilir
- Lokal veya 3Commas blacklist kontrolu uygular

`watchlist_100eyes.py`:

- 100eyes uyumlu Telegram sinyallerini isler
- Sinyali borsa/parite kurallarina gore eslestirir
- Uygun bot icin deal baslatma akisini tetikler

### Kar Birlestirme

`compound.py`:

- Tamamlanan deal karlarini izler
- Kar tutarini configured oranlara gore bot ayarlarina aktarabilir
- Base order, safety order ve bot kapasitesi gibi alanlari yonetebilir
- Islenen deal'lari yerel SQLite durum veritabaninda takip eder
- Birden fazla bot icin ayri compound politikalari destekler

### Take-Profit Otomasyonu

`tpincrement.py`:

- Aktif deal durumlarini takip eder
- Yapilandirilan increment scale'e gore take-profit seviyesini ayarlar
- Islenen deal durumlarini yerel veritabaninda saklar

### Trailing Stop-Loss

`trailingstoploss.py`:

- Futures deal'larini izler
- Aktivasyon yuzdesine ulasildiginda stop-loss degerini gunceller
- Farkli botlar icin aktivasyon ve ilk stop degerleri tanimlanabilir
- Deal durumunu yerel SQLite veritabaninda izler

`tsl_and_tp.py`:

- Trailing stop-loss ve dinamik take-profit davranisini birlestirir
- Check ve monitor interval'lerini ayri yonetir
- Aktivasyon, ilk stop ve TP increment degerlerini bot bazinda destekler
- Eski deal kayitlarini temizler

## Ortak Platform Ozellikleri

- Helper bazinda otomatik ornek config olusturma
- Config surum yukseltme/migration destegi
- Zaman dilimi ve calisma araligi ayarlari
- Debug log ve log rotation
- Apprise ile Telegram ve diger notification kanallari
- 3Commas API hata ve rate-limit isleme yardimcilari
- Lokal blacklist destegi
- Birden fazla bot ID ile calisma
- Docker ve systemd ornekleri
- Raspberry Pi, Linux ve Windows kurulumu

## Calisma Modeli

1. Helper baslatilir.
2. Yerel config okunur veya ilk config olusturulur.
3. Harici veri/sinyal kaynagi sorgulanir.
4. 3Commas hesap, bot, market ve blacklist verileri kontrol edilir.
5. Kural seti uygun bir eylem uretirse bot/deal guncellenir.
6. Sonuc loglanir ve notification gonderilebilir.
7. Helper configured interval boyunca bekler ve donguyu tekrarlar.

## Guvenlik Yaklasimi

- Paper Trading hesabi ile baslama
- Withdrawal izni olmayan ayri API key
- Mumkunse IP whitelist
- `.ini` ve log dosyalarini Git disinda tutma
- API secret ve Telegram URL'lerini public issue'larda paylasmama
- Tek bot ile kontrollu rollout

## Kimler Icin?

- 3Commas botlarini veri odakli yonetmek isteyen kullanicilar
- Parite listelerini otomatik guncellemek isteyen bot operatorleri
- Telegram sinyallerini kontrollu sekilde otomasyona baglayan ekipler
- Kar birlestirme ve risk kurallarini script ile izlemek isteyenler
- Python tabanli trading automation inceleyen gelistiriciler

## Risk Uyarisi

BotSystem emir ve bot ayarlarini degistirebilir. Yanlis config, gecikmis veri,
API hatasi veya piyasa kosullari maddi kayba neden olabilir. Once paper hesapta,
tek botla ve dusuk siklikta test edilmelidir.

Bu yazilim finansal tavsiye degildir.

