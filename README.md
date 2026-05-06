# 🎨 AI Photo Generator — توليد الصور بالذكاء الاصطناعي

تطبيق ويب متكامل يعمل على **Google Colab** لتوليد الصور باستخدام Stable Diffusion مع واجهة مستخدم عصرية Dark Mode بتأثير Glassmorphism.

---

## 🚀 طريقة التشغيل السريعة

### الخطوة 1 — رفع Notebook على Google Colab

1. اذهب إلى [colab.research.google.com](https://colab.research.google.com)
2. اختر **File → Upload notebook**
3. ارفع ملف `AI_Photo_Generator.ipynb`

### الخطوة 2 — تفعيل GPU

> **مهم جداً:** بدون GPU ستكون سرعة التوليد بطيئة جداً

- في Colab: **Runtime → Change runtime type → T4 GPU** → Save

### الخطوة 3 — الحصول على ngrok Token (مجاناً)

1. اذهب إلى [ngrok.com](https://ngrok.com) وأنشئ حساباً مجانياً
2. من **Dashboard** → **Your Authtoken** → انسخ التوكن
3. في **Cell 2** من الـ Notebook، ضع التوكن في:
   ```python
   NGROK_TOKEN = "ضع_توكنك_هنا"
   ```

### الخطوة 4 — تشغيل الخليتين

1. شغّل **Cell 1** (تثبيت المكتبات) — تستغرق ~2 دقيقة، مرة واحدة فقط
2. شغّل **Cell 2** (تشغيل التطبيق) — تستغرق ~3-5 دقائق لتحميل النموذج
3. ستظهر في الـ output رسالة مثل:
   ```
   🌐 ═══════════════════════════════════════
      رابط التطبيق العام: https://xxxx.ngrok-free.app
      افتحه من هاتفك أو متصفحك!
   ═══════════════════════════════════════
   ```
4. انقر على الرابط وافتحه من أي جهاز!

---

## ✨ المميزات

| الميزة | التفاصيل |
|--------|---------|
| 🤖 نموذج AI | SDXL-Turbo (أسرع) أو Stable Diffusion v1.5 (تلقائي حسب الموارد) |
| 🌍 دعم العربية | ترجمة تلقائية من العربية إلى الإنجليزية باستخدام `deep_translator` |
| 🎨 التصميم | Dark Mode كامل + Glassmorphism + Glow بنفسجي |
| 📐 أبعاد الصورة | 512×512 حتى 1024×1024 |
| ⚡ التوليد | 1–50 خطوة استدلال قابلة للتعديل |
| 🎯 Negative Prompt | إزالة عناصر غير مرغوبة من الصورة |
| 🔢 Seed | إعادة إنتاج نفس الصورة بنفس الإعدادات |
| 💾 تحميل | تحميل الصورة الناتجة بجودة PNG عالية |

---

## 🛠️ المتطلبات التقنية

```
fastapi
uvicorn[standard]
diffusers
transformers
accelerate
deep-translator
pyngrok
python-multipart
Pillow
xformers
torch (CUDA)
```

---

## ⚠️ حلول للمشاكل الشائعة

| المشكلة | الحل |
|---------|------|
| `CUDA out of memory` | استخدم أبعاداً أصغر (512×512) أو قلّل خطوات الاستدلال |
| `ngrok: session expired` | أعد تشغيل Cell 2 فقط (لا تعيد تثبيت المكتبات) |
| `Runtime disconnected` | Colab يقطع الاتصال بعد فترة خمول — أعد تشغيل الخليتين |
| التوليد بطيء جداً | تأكد من تفعيل T4 GPU في Runtime settings |
| الصورة لا تظهر | تحقق من صلاحية رابط ngrok (ينتهي بعد ~2 ساعة مجاناً) |

---

## 📁 هيكل المشروع

```
AI-PHOTO-/
└── AI_Photo_Generator.ipynb   # Notebook الكامل (خليتان)
    ├── Cell 1: تثبيت المكتبات
    └── Cell 2: التطبيق الكامل
        ├── Backend  (FastAPI)
        │   ├── GET  /         → الواجهة الأمامية
        │   ├── GET  /status   → معلومات النموذج والجهاز
        │   └── POST /generate → توليد الصورة
        └── Frontend (HTML/Tailwind/Lucide)
            ├── Header + Model badge
            ├── Sidebar (إعدادات)
            └── Main area (Prompt + Image result)
```

---

## 🔗 روابط مفيدة

- [Google Colab](https://colab.research.google.com)
- [ngrok Dashboard](https://dashboard.ngrok.com)
- [Stable Diffusion v1.5 على HuggingFace](https://huggingface.co/runwayml/stable-diffusion-v1-5)
- [SDXL-Turbo على HuggingFace](https://huggingface.co/stabilityai/sdxl-turbo)