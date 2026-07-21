# Botni Railway'ga deploy qilish qo'llanmasi 🚀

Railway — botni 24/7 ishlatish uchun eng oson platforma. Hozirgi kod hech qanday
o'zgarishsiz ishlaydi.

## 1-qadam: Kodni GitHub'ga yuklash

```bash
cd jasur-bot
git init
git add .
git commit -m "Jasur bot"
```

GitHub'da yangi **private** repozitoriy yarating (github.com/new), keyin:

```bash
git remote add origin https://github.com/SIZNING_USERNAME/jasur-bot.git
git branch -M main
git push -u origin main
```

> ⚠️ `.env` fayli `.gitignore` tufayli yuklanmaydi — bu to'g'ri! Tokenlar
> GitHub'ga chiqmasligi kerak.

## 2-qadam: Railway'da loyiha yaratish

1. [railway.app](https://railway.app) ga kiring va **GitHub bilan ro'yxatdan o'ting**
2. **New Project** → **Deploy from GitHub repo** → `jasur-bot` ni tanlang
3. Railway avtomatik `requirements.txt` va `Procfile` ni topib build qiladi

## 3-qadam: Muhit o'zgaruvchilarini kiritish

Loyiha ochilgach: **Variables** bo'limiga o'ting va qo'shing:

| Nomi | Qiymati |
|---|---|
| `TELEGRAM_BOT_TOKEN` | BotFather'dan olingan token |
| `ANTHROPIC_API_KEY` | console.anthropic.com'dan olingan kalit |
| `ADMIN_CODE` | `TMBB197219742008` |
| `MORNING_HOUR` | `7` |
| `TZ_OFFSET_HOURS` | `5` |

Har birini kiritgach **Add** bosing. Railway avtomatik qayta deploy qiladi.

## 4-qadam: Tekshirish

1. **Deployments** bo'limida oxirgi deploy **Active** bo'lishini kuting
2. **Logs** da `Bot ishga tushdi. Model: claude-sonnet-4-5` yozuvi chiqishi kerak
3. Telegramda botga `/start` yozing → maxfiy kodni yuboring → 👑 admin bo'lasiz!

## Yangilash

Kodni o'zgartirsangiz:

```bash
git add .
git commit -m "yangilanish"
git push
```

Railway avtomatik yangi versiyani deploy qiladi.

## ⚠️ Muhim eslatmalar

- **Narx:** Railway'da $5 bepul sinov kredit bor; keyin Hobby plan ~$5/oy.
  Bepul alternativa kerak bo'lsa: [PythonAnywhere](https://pythonanywhere.com)
  (Always-on task) yoki o'z VPS'ingiz.
- **Baza:** `jasur_bot.db` konteyner ichida saqlanadi. Railway'da qayta deploy
  qilinganda o'chib ketmasligi uchun: **Settings → Volumes → Add Volume**,
  mount path: `/data`, va Variables ga `DB_PATH=/data/jasur_bot.db` qo'shing.
- **Bitta nusxa:** Bot faqat bitta joyda ishlashi kerak (polling). Kompyuteringizda
  ham, Railway'da ham bir vaqtda ishlatmang — Telegram xato beradi.

## Alternativa: Render.com

1. [render.com](https://render.com) → **New** → **Background Worker**
2. GitHub repo ni ulang, Start Command: `python bot.py`
3. Environment Variables ni xuddi yuqoridagidek kiriting

> Render'da Background Worker pullik ($7/oy). Bepul Web Service esa botga mos
> emas (uxlab qoladi).
