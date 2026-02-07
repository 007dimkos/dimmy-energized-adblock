# 🛡️ENERGIZED AdBlock Rules (Sing-box & PassWall) 🛡️ 

Автоматизированная сборка правил для очистки трафика от рекламы, трекеров и обхода блокировок (DOH/VPN/Proxy) и безопасного интернета. Сборка основана на элитных списках HaGeZi с персональными исключениями.

✅ **Обновляется ежедневно в 05:00 UTC.** ✅ **Формат:** Бинарный SRS (Sing-box 1.10+).


🔗 Прямая ссылка
https://github.com/007dimkos/dimmy-energized-adblock/releases/download/latest/dimmyenergizi.srs

🛠 Настройка

1. PassWall 2 (OpenWrt)
В поле Remote Rule Set (Удаленные правила) добавь строку:

rule-set:remote:https://github.com/007dimkos/dimmy-energized-adblock/releases/download/latest/dimmyenergizi.srs

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
