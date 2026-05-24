# Marketing Staff Manager

مشروع ويب عربي RTL جاهز للنشر على Vercel لإدارة موظفي التسويق والحسابات والتقارير اليومية.

## التقنيات

- Next.js 15
- React 19
- TypeScript
- Tailwind CSS
- Supabase
- bcryptjs لتشفير كلمات المرور
- Session cookie آمنة موقعة من السيرفر

> تنبيه أمني: لا يتم تخزين كلمة المرور كنص عادي. يتم حفظ `password_hash` فقط باستخدام bcrypt. استخدم `SUPABASE_SERVICE_ROLE_KEY` في متغيرات بيئة Vercel فقط ولا تعرضه في المتصفح.

## الصفحات

- `/login` تسجيل الدخول
- `/dashboard` لوحة التحكم
- `/employees` إدارة الموظفين Admin فقط
- `/accounts` إدارة الحسابات Admin فقط
- `/reports` إدخال ومشاهدة التقارير
- `/settings` إنشاء المستخدمين Admin فقط

## حساب Admin الافتراضي

username: `admin`
password: `admin123`

## تشغيل المشروع محليًا

```bash
npm install
cp .env.example .env.local
npm run dev
```

افتح:

```bash
http://localhost:3000
```

## ربط Supabase

1. أنشئ مشروع جديد على Supabase.
2. من SQL Editor نفّذ الملف:

```bash
supabase/schema.sql
```

3. انسخ القيم التالية إلى `.env.local`:

```env
NEXT_PUBLIC_SUPABASE_URL=https://YOUR_PROJECT.supabase.co
NEXT_PUBLIC_SUPABASE_ANON_KEY=YOUR_ANON_KEY
SUPABASE_SERVICE_ROLE_KEY=YOUR_SERVICE_ROLE_KEY
APP_SESSION_SECRET=ضع-نص-عشوائي-طويل-جدا
```

## رفع المشروع على Vercel

1. ارفع المشروع إلى GitHub.
2. افتح Vercel واختر Import Project.
3. أضف نفس متغيرات البيئة الموجودة في `.env.example` داخل Vercel Project Settings.
4. اضغط Deploy.

## ملاحظات مهمة للإنتاج

- غيّر كلمة مرور حساب admin بعد أول دخول.
- اجعل `APP_SESSION_SECRET` قيمة طويلة وعشوائية.
- لا تضع `SUPABASE_SERVICE_ROLE_KEY` داخل أي ملف ظاهر أو داخل الكود المرسل للعميل.
- يمكن لاحقًا توسيع التكامل مع Supabase Auth عبر ربط `users.auth_user_id` بحسابات `auth.users`.
