# 🎲 تخريب العلاقات — Richora (مرتب)

مشروع اللعبة بعد الترتيب. كل شيء خدام من `index.html` مباشرة.

## 📁 الهيكل الجديد

```
richora/
├── index.html          ← نقطة الدخول (الوحيد فالجذر مع vercel.json)
├── vercel.json         ← إعدادات النشر (rewrites ديال /room/:code)
├── css/
│   └── style.css       ← كل التنسيقات
├── js/
│   ├── board.js        ← الـ48 خانة + المجموعات + الأعلام
│   ├── cards.js        ← بطاقات Treasure / Surprise
│   ├── engine.js       ← منطق اللعبة (الدور، الشراء، البناء، البوتات)
│   ├── game-ui.js      ← العرض (القطع، النرد 3D، الأصوات، النوافذ)
│   └── app.js          ← اللوبي + بناء الطاولة + خرائط الأعلام
├── assets/
│   ├── flags/          ← أعلام البلدان (14 علم) — مستعملة فالطاولة
│   │   ├── bahrain.png, egypt.png, gb.png, iraq.png, jordan.png
│   │   ├── kuwait.png, morocco.png, palestine.png, qatar.png
│   │   ├── saudi.png, syria.png, tunisia.png, turkey.png, uae.png
│   │   └── popup/      ← نسخ بطاقات معلومات الأرض (نفس الصور مؤقتًا)
│   ├── icons/          ← أيقونات الطاولة (18) — محفوظة لـ V12
│   │   ├── start, treasure, surprise, earnings-tax, airport
│   │   ├── jail, go-to-prison, vacation, water, power, gas
│   │   ├── house, hotel, build, land-deed, money, trade
│   │   └── bankrupt
│   └── music/          ← فارغ حاليًا (ناقص rush-e.mp3)
├── sounds/             ← فارغ حاليًا (18 ملف mp3 ناقصين — شوف README)
│   └── README.txt      ← لائحة أسماء ملفات الصوت المطلوبة
└── docs/               ← ملفات التوثيق القديمة
    ├── V12_README.txt
    ├── RESTORED_PRE_ICONS_README.txt
    └── VERCEL_DEPLOY.txt
```

## 🔧 شنو تصلح فالترتيب؟

1. **نقل الملفات**: `style.css` → `css/` و ملفات JS → `js/` مع تحديث `index.html`.
2. **الأعلام**: تجمعات فـ `assets/flags/` + نسخ `popup/` (الكود كان كيقلب عليهم وماكاينينش).
3. **الأيقونات**: تجمعات فـ `assets/icons/` جاهزة لدمج V12.
4. **إصلاح خريطة الأعلام** (`js/app.js`):
   - زدت `🇬🇧 → gb.png` (لندن و المدن البريطانية كانوا كيبانو غير "GB" نص).
   - زدت `🇸🇾 popup` اللي كانت ناقصة.
5. **التوثيق**: تجمع فـ `docs/` + هاد `README.md`.

## ⚠️ الملفات الناقصة (اللعبة خدامة بلاهم)

| الملف | المسار المتوقع | الملاحظة |
|---|---|---|
| `rush-e.mp3` | `assets/music/` | موسيقى الخلفية — اللعبة ساكتة بلاها |
| 18 ملف `*.mp3` | `sounds/` | مؤثرات (النرد، الشراء...) — شوف `sounds/README.txt` |

> اللعبة مبرمجة تتجاهل الملفات الناقصة بأمان، تقدر تزيدهم واحد بواحد.

## 🚀 التشغيل

- **محليًا**: حل `index.html` فالمتصفح، ولا شغّل سيرفر صغير:
  ```bash
  cd richora && python3 -m http.server 8000
  ```
  و حل `http://localhost:8000` — و جرّب `#lobby` باش تدخل للطاولة نيشان.
- **النشر**: المجلد جاهز لـ Vercel كما هو (`vercel.json` موجود):
  ```bash
  cd richora && npx vercel --prod
  ```

## 📌 ملاحظة على turkey.png

علم تركيا موجود فالمجلد nhưng مامربوطش بأي مجموعة مدن حاليًا (مطارات IST/MUC/DAM/RUH ماعندهمش أعلام). خليتو احتياطي — إلا بغيتي نربطوه بمطار IST قولها ليا.

## ⏭️ الخطوة الجاية (V12)

أيقونات `assets/icons/` مازال مامدموجينش فالكود (الطاولة حاليًا بالإيموجي 🎁✈️🏝️).
إلا بغيتي ندمجهم (start, treasure, surprise, tax, airport, jail, vacation, utilities + house/hotel) قوليا ونكمل.
