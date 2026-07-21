# Jasur Bot — Kundalik hayot yordamchisi 🤖

Telegram bot, AI modeli: **Claude Sonnet 4.5**. Interfeys tili: o'zbekcha.

## Imkoniyatlar

- 💬 **AI suhbat** — istalgan savolga Claude Sonnet 4.5 javob beradi (suhbat tarixini eslab qoladi)
- 📋 **Vazifalar** — `/add`, `/tasks`, `/done`, `/del`
- 🔁 **Odatlar** — `/habit`, `/habits`, `/check` (streak hisoblanadi 🔥)
- ⏰ **Eslatmalar** — `/remind 18:30 Darsga borish`
- ☀️ **Ertalabki xabar** — har kuni soat 7:00 da kun rejasi + AI motivatsiya

## O'rnatish

1. Telegramda [@BotFather](https://t.me/BotFather) ga `/newbot` yozib token oling.
2. [console.anthropic.com](https://console.anthropic.com) dan API kalit oling.
3. Fayllarni tayyorlang:

```bash
cp .env.example .env
# .env faylini ochib tokenlarni kiriting
pip install -r requirements.txt
python bot.py
```

Bot ishga tushgach, Telegramda botga `/start` yozing.

## Sozlamalar (.env)

| O'zgaruvchi | Tavsif | Default |
|---|---|---|
| `TELEGRAM_BOT_TOKEN` | BotFather token | — |
| `ANTHROPIC_API_KEY` | Anthropic API kalit | — |
| `MORNING_HOUR` / `MORNING_MINUTE` | Ertalabki xabar vaqti | 7:00 |
| `TZ_OFFSET_HOURS` | Vaqt zonasi (Toshkent=5) | 5 |

## Doimiy ishlashi uchun (server)

```bash
# oddiy variant
nohup python bot.py &

# yoki systemd / Docker / Railway / VPS da ishga tushiring
```

Ma'lumotlar `jasur_bot.db` (SQLite) faylida saqlanadi.
