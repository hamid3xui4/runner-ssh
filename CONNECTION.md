# اطلاعات اتصال سرور

> با هر اجرای جدید خودکار به‌روز می‌شود.

| مورد | مقدار |
|---|---|
| آخرین به‌روزرسانی | 2026-09-28 10:31:02 UTC |
| کاربر / پسورد | `root` / `hamidgh69` |
| کاربر پشتیبان | `hamid` / `hamidgh69` (با sudo) |
| IP داخل Tailscale | `100.125.72.20` |
| نام گره | `gha-ubuntu` = `gha-ubuntu.tail3641f4.ts.net` |
| Exit node | فعال ✅ |
| Funnel | فقط داخل tailnet ⚠️ |
| تست ورود root با پسورد | موفق ✅ |
| تست ورود hamid با پسورد | موفق ✅ |
| پایان تقریبی این اجرا | 16:13 UTC |

## راه اصلی — Tailscale (پیشنهادی)
```bash
ssh -p 22 root@100.125.72.20
```

## همهٔ راه‌ها
```bash
# ۱) از طریق Tailscale (پیشنهادی)
ssh root@100.125.72.20
ssh hamid@100.125.72.20        # سپس: sudo -i

# ۲) از طریق پورت ۱۰۰۰۰ (serve/funnel)
ssh -p 10000 -o StrictHostKeyChecking=no root@gha-ubuntu.tail3641f4.ts.net
```
صفحهٔ وضعیت: https://gha-ubuntu.tail3641f4.ts.net:8443/

## Exit node روی گوشی
اپ Tailscale → منو → Exit node → `gha-ubuntu`
