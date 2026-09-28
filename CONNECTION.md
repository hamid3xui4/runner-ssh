# اطلاعات اتصال سرور

> این فایل با هر اجرای جدید به‌صورت خودکار به‌روز می‌شود.

| مورد | مقدار |
|---|---|
| آخرین به‌روزرسانی | 2026-09-28 10:04:30 UTC |
| کاربر SSH | root |
| پسورد SSH | `hamidgh69` |
| IP داخل Tailscale | `100.107.20.42` |
| نام گره | `gha-ubuntu` / `gha-ubuntu.tail3641f4.ts.net` |
| Exit node | فعال ✅ |
| Funnel | فقط داخل tailnet ⚠️ |
| پایان تقریبی این اجرا | 15:46 UTC |

## راه اول — از طریق Tailscale (پیشنهادی)
```bash
ssh root@100.107.20.42
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
