# runner-ssh

سرور موقت Ubuntu 22.04 روی GitHub Actions با SSH (کاربر root) و Tailscale.

- شروع دستی: Actions → ssh-runner → Run workflow
- IP و پسورد در لاگ همان اجرا چاپ می‌شود.
- حداکثر عمر هر اجرا ۶ ساعت (محدودیت GitHub).

## اتصال
1. Tailscale را روی دستگاه خود با همان اکانت فعال کنید.
2. `ssh root@<TAILSCALE_IP>` با پسورد لاگ.
