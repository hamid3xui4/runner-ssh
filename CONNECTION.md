# اطلاعات اتصال سرور

> با هر اجرای جدید خودکار به‌روز می‌شود.

| مورد | مقدار |
|---|---|
| آخرین به‌روزرسانی | 2026-10-08 18:50:34 UTC |
| کاربر / پسورد | `root` / `hamidgh69` |
| کاربر پشتیبان | `hamid` / `hamidgh69` (با sudo) |
| IP داخل Tailscale | `100.124.173.56` |
| نام گره | `gha-ubuntu` = `gha-ubuntu.tail3641f4.ts.net` |
| Exit node | فعال ✅ |
| Funnel | در CLI فعال است، ولی از اینترنت تست نشد ⚠️ (رانر GitHub ورودی بیرونی ندارد) |
| تست ورود root با پسورد | موفق ✅ |
| تست ورود hamid با پسورد | موفق ✅ |
| پایان تقریبی این اجرا | 00:32 UTC |

## راه اصلی — Tailscale (راه اصلی و تضمین‌شده)
```bash
ssh -p 22 root@100.124.173.56
```

## همهٔ راه‌ها
```bash
# ۱) از طریق Tailscale (پیشنهادی)
ssh root@100.124.173.56
ssh hamid@100.124.173.56        # سپس: sudo -i

# ۲) از طریق پورت ۱۰۰۰۰ (serve/funnel)
ssh -p 10000 -o StrictHostKeyChecking=no root@gha-ubuntu.tail3641f4.ts.net
```
صفحهٔ وضعیت داخل tailnet: https://gha-ubuntu.tail3641f4.ts.net:8443/

## Exit node روی گوشی
اپ Tailscale → منو → Exit node → `gha-ubuntu`
