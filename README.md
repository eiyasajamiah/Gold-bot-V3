# 🥇 بوت الذهب الموحّد v2.0 — Unified Gold Trading Bot

بوت تيليغرام لتداول الذهب (XAU/USD) يجمع **ثلاث استراتيجيات** متقدمة مع **مشغّل ذكي** يعمل على GitHub Actions.

---

## ✨ المميزات الرئيسية

### 📊 ثلاث استراتيجيات مدمجة

| الاستراتيجية | المؤشرات | الإضافات في v2.0 |
|---|---|---|
| **① V7** — متعدد الإطارات | EMA, RSI, MACD, BB, ADX, Stoch, PVP | + Ichimoku Cloud, OBV, Williams %R, **Divergence** |
| **② SMC** — Smart Money | BOS, CHoCH, OB, FVG | + **MSS**, **Liquidity Pools**, **Premium/Discount** |
| **③ OBinOB** — كتل متداخلة | HTF OB inside LTF OB × 4 أزواج | + TP1/TP2 منفصلان |

### 🎯 ثلاثة أهداف لكل إشارة
- **TP1** — هدف محافظ (50% من المركز)
- **TP2** — هدف متوسط (75% من المركز)  
- **TP3** — هدف طموح (25% من المركز)

### ⚡ المشغّل الذكي (Smart Trigger)
يفحص السوق **كل دقيقة** ويُشغّل التحليل الكامل فوراً عند:
- تغيّر السعر ≥ 0.04%
- ارتفاع الحجم × 1.8 من المتوسط
- إغلاق شمعة 5m أو 15m جديدة
- مرور 5 دقائق (إجباري)

---

## 🚀 التشغيل على GitHub Actions (مجاناً)

### الخطوة 1 — Fork المستودع
اضغط **Fork** في أعلى يمين هذه الصفحة

### الخطوة 2 — إضافة Secrets
في مستودعك: **Settings → Secrets → Actions → New repository secret**

| الاسم | القيمة |
|---|---|
| `TELEGRAM_TOKEN` | توكن البوت من [@BotFather](https://t.me/BotFather) |
| `TELEGRAM_CHAT_ID` | رقم الـ Chat ID (من [@userinfobot](https://t.me/userinfobot)) |

### الخطوة 3 — تفعيل Actions
- اذهب إلى **Actions** في مستودعك
- اضغط **Enable GitHub Actions**
- البوت يبدأ تلقائياً كل دقيقة ✅

---

## 💻 التشغيل المحلي

```bash
# 1. استنساخ المستودع
git clone https://github.com/YOUR_USERNAME/gold-bot.git
cd gold-bot

# 2. تثبيت المتطلبات
pip install -r requirements.txt

# 3. إعداد الإعدادات
cp config.example.json config.json
# عدّل config.json بتوكنك وchat_id

# 4. تشغيل البوت
python unified_gold_bot.py
```

---

## 📱 أوامر التيليغرام

| الأمر | الوصف |
|---|---|
| `/start` | اشتراك واستقبال كل شيء |
| `/signals` | إشارات الشراء/البيع فقط |
| `/analysis` | التحليلات التفصيلية فقط |
| `/all` | كل الرسائل |
| `/status` | حالة اشتراكك |
| `/perf` | أداء كل استراتيجية |
| `/help` | دليل الاستخدام الكامل |
| `/stop` | إلغاء الاشتراك |

---

## 📈 منطق الإشارات

```
الإشارة تصدر عند توافق 2+ من 3 استراتيجيات

3/3 يتوافقون → إشارة قوية جداً  (ثقة ≥ 85%)
2/3 يتوافقون → إشارة متوسطة     (ثقة 60-84%)
أقل من 2     → تحليل فقط، لا إشارة
```

**أولوية SL/TP:** OBinOB → V7 → SMC

---

## ⚙️ ضبط الإعدادات (config.json)

```json
{
  "TRIGGER_PRICE_CHANGE_PCT": 0.04,    ← حساسية السعر (0.03 = أكثر حساسية)
  "TRIGGER_FORCE_EVERY_MIN": 5,        ← تشغيل إجباري كل N دقيقة
  "UNIFIED_MIN_AGREE": 2,             ← الحد الأدنى للتوافق (2 أو 3)
  "MIN_RR": 1.5,                      ← أدنى نسبة مخاطرة/عائد
  "OB_MIN_RR": 1.8                    ← أدنى R:R لـ OBinOB
}
```

---

## 📊 هيكل الملفات

```
gold-bot/
├── unified_gold_bot.py     ← البوت الرئيسي
├── config.json             ← الإعدادات (لا ترفعه!)
├── requirements.txt        ← المتطلبات
├── .github/
│   └── workflows/
│       └── bot.yml         ← GitHub Actions
├── charts/                 ← الرسوم البيانية المولّدة
├── logs/                   ← ملفات السجل
├── subscribers.json        ← قائمة المشتركين
└── performance.json        ← سجل الأداء
```

---

## ⚠️ إخلاء مسؤولية

هذا البوت للأغراض التعليمية والمعلوماتية فقط.  
لا يُعدّ توصية استثمارية. تداول الذهب ينطوي على مخاطر عالية.  
استشر مستشاراً مالياً مؤهلاً قبل اتخاذ قرارات استثمارية.

---

*Made with ❤️ | XAU/USD Unified Gold Bot v2.0*
