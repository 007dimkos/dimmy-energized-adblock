# 🛡️ENERGIZED AdBlock Rules (Sing-box & PassWall) 🛡️ 

Автоматизированная сборка правил для очистки трафика от рекламы, трекеров. Сборка основана списке HaGeZi с персональными исключениями.

✅ **Обновляется ежедневно.** ✅ **Формат:** Бинарный SRS (Sing-box 1.10+).


🔗 Прямая ссылка
https://github.com/007dimkos/dimmy-energized-adblock/releases/download/release-11.02.2026/dimmyenergizi.srs

🛠 Настройка

1. PassWall 2 (OpenWrt)
В поле Remote Rule Set (Удаленные правила) Domain добавь строку:
```json
rule-set:remote:https://raw.githubusercontent.com/007dimkos/dimmy-energized-adblock/refs/heads/main/dimmyenergizi.srs
```
Затем установи для этого правила действие BLACKHOLE.

2. Sing-Box
Добавьте rule_set в конфигурацию Sing-Box и правило для него:

```json
{
  "route": {
    "rule_set": [
      {
        "tag": "energized_ads",
        "type": "remote",
        "format": "binary",
        "url": "https://github.com/007dimkos/dimmy-energized-adblock/releases/download/latest/dimmyenergizi.srs"
      }
    ],
    "rules": [
      {
        "rule_set": "energized_ads",
        "outbound": "block"
      }
    ]
  }
}
```
3. Xray

Загрузите dimmyenergizi.dat в нужную директорию и добавьте правило для него:
```
{
  "routing": {
    "rules": [
      {
        "domain": "ext:dimmyenergizi.dat:hagezi-pro",
        "outboundTag": "block"
      }
    ]
  }
}
```
При использовании XKeen с Xray на роутерах Keenetic можно скачать командой в entware:
```
curl -Lfo /opt/etc/xray/dat/dimmyenergizi.dat https://github.com/007dimkos/dimmy-energized-adblock/releases/latest/download/dimmyenergizi.dat
```


4. Mihomo

Добавьте rule-set в конфигурацию Mihomo и правило для него:

```
rule-providers:
  adlist:
    type: http
    format: mrs
    behavior: domain
    url: https://github.com/007dimkos/dimmy-energized-adblock/releases/latest/download/dimmyenergizi.mrs
    path: ./rule-providers/dimmyenergizi.mrs
    interval: 86400
rules:
  - RULE-SET,adlist,REJECT
```
