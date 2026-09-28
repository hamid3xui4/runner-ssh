# اطلاعات اتصال سرور

> این فایل با هر اجرای جدید به‌صورت خودکار به‌روز می‌شود.

| مورد | مقدار |
|---|---|
| آخرین به‌روزرسانی | 2026-09-28 10:11:29 UTC |
| کاربر SSH | root |
| پسورد SSH | `hamidgh69` |
| IP داخل Tailscale | `100.95.29.22` |
| نام گره | `gha-ubuntu` / `gha-ubuntu.tail3641f4.ts.net` |
| Exit node | فعال ✅ |
| Funnel | فقط داخل tailnet ⚠️ |
| تست ورود SSH با پسورد | ناموفق ❌ |
| تست SSH روی پورت ۱۰۰۰۰ (داخل tailnet) | ناموفق ❌ |
| پایان تقریبی این اجرا | 15:53 UTC |

## راه اول — از طریق Tailscale (پیشنهادی)
```bash
ssh root@100.95.29.22
```

## راه دوم — SSH روی پورت ۱۰۰۰۰ (serve/funnel)
```bash
ssh -p 10000 -o StrictHostKeyChecking=no root@gha-ubuntu.tail3641f4.ts.net
```
صفحهٔ وضعیت: https://gha-ubuntu.tail3641f4.ts.net:8443/

## Exit node روی گوشی
در اپ Tailscale، منو → Exit node → `gha-ubuntu` را انتخاب کنید.

> نکته: اگر Funnel «فقط داخل tailnet» است، باید در کنسول ادمین Tailscale
> (بخش DNS) گزینهٔ **HTTPS Certificates** یک‌بار فعال شود.
