# گزارش تشخیصی

```
date: Tue Sep 29 04:25:11 UTC 2026
-- sshd -T --
authenticationmethods any
passwordauthentication yes
permitrootlogin yes
usepam yes
-- passwd -S --
root P 09/29/2026 -1 -1 -1 -1
hamid P 09/29/2026 0 99999 7 -1
-- تست root --
Warning: Permanently added '127.0.0.1' (ED25519) to the list of known hosts.
ROOT_LOGIN_OK
-- تست hamid --
Warning: Permanently added '127.0.0.1' (ED25519) to the list of known hosts.
HAMID_LOGIN_OK
-- hash پسورد (باید با $ شروع شود، نه ! یا *) --
root: $y$j
hamid: $y$j
-- pam.d/sshd --
@include common-auth
account    required     pam_nologin.so
@include common-account
session [success=ok ignore=ignore module_unknown=ignore default=bad]        pam_selinux.so close
session    required     pam_loginuid.so
session    optional     pam_keyinit.so force revoke
@include common-session
session    optional     pam_motd.so  motd=/run/motd.dynamic
session    optional     pam_motd.so noupdate
session    optional     pam_mail.so standard noenv # [1]
session    required     pam_limits.so
session    required     pam_env.so # [1]
-- pam.d/common-auth --
auth	[success=1 default=ignore]	pam_unix.so nullok
auth	requisite			pam_deny.so
auth	required			pam_permit.so
auth	optional			pam_cap.so 
-- پروسه‌های sshd --
   2648 sshd: /usr/sbin/sshd -E /tmp/sshd2.log [listener] 2 of 10-100 startups
   4294 sshd: [accepted]
   4305 sshd: [accepted]
-- لاگ sshd --
Missing privilege separation directory: /run/sshd
-- auth.log --
Sep 29 04:25:11 runnervm3p1d5 sudo: pam_unix(sudo:session): session closed for user root
Sep 29 04:25:11 runnervm3p1d5 sudo:   runner : PWD=/home/runner/work/runner-ssh/runner-ssh ; USER=root ; COMMAND=/usr/bin/grep -vE ^\\s*(#|$) /etc/pam.d/sshd
Sep 29 04:25:11 runnervm3p1d5 sudo: pam_unix(sudo:session): session opened for user root(uid=0) by (uid=1001)
Sep 29 04:25:11 runnervm3p1d5 sudo: pam_unix(sudo:session): session closed for user root
Sep 29 04:25:11 runnervm3p1d5 sudo:   runner : PWD=/home/runner/work/runner-ssh/runner-ssh ; USER=root ; COMMAND=/usr/bin/grep -vE ^\\s*(#|$) /etc/pam.d/common-auth
Sep 29 04:25:11 runnervm3p1d5 sudo: pam_unix(sudo:session): session opened for user root(uid=0) by (uid=1001)
Sep 29 04:25:11 runnervm3p1d5 sudo: pam_unix(sudo:session): session closed for user root
Sep 29 04:25:11 runnervm3p1d5 sudo:   runner : PWD=/home/runner/work/runner-ssh/runner-ssh ; USER=root ; COMMAND=/usr/bin/tail -25 /tmp/sshd.log
Sep 29 04:25:11 runnervm3p1d5 sudo: pam_unix(sudo:session): session opened for user root(uid=0) by (uid=1001)
Sep 29 04:25:11 runnervm3p1d5 sudo: pam_unix(sudo:session): session closed for user root
Sep 29 04:25:11 runnervm3p1d5 sudo:   runner : PWD=/home/runner/work/runner-ssh/runner-ssh ; USER=root ; COMMAND=/usr/bin/tail -18 /var/log/auth.log
Sep 29 04:25:11 runnervm3p1d5 sudo: pam_unix(sudo:session): session opened for user root(uid=0) by (uid=1001)
-- ts status --
100.69.53.52     gha-ubuntu        novinsazeh.mrv@  linux    idle; offers exit node      
100.85.218.16    hamid             novinsazeh.mrv@  windows  offline, last seen 11h ago  
100.67.118.27    hrg-backup-1      novinsazeh.mrv@  linux    offline, last seen 10h ago  
100.98.227.115   hrg-backup-2      novinsazeh.mrv@  linux    offline, last seen 8h ago   
100.74.237.69    hrg-backup-3      novinsazeh.mrv@  linux    offline, last seen 2h ago   
100.74.157.108   hrg-backup        novinsazeh.mrv@  linux    offline, last seen 18h ago  
100.70.83.2      linux-server-vps  novinsazeh.mrv@  linux    -                           
100.98.52.75     nothing-phone-1   novinsazeh.mrv@  android  offline, last seen 2m ago   
-- tags --
{"Tags":null,"DNSName":"gha-ubuntu.tail3641f4.ts.net.","Online":true}
-- serve status --

# Funnel on:
#     - tcp://gha-ubuntu.tail3641f4.ts.net:10000
#     - https://gha-ubuntu.tail3641f4.ts.net:8443

|-- tcp://gha-ubuntu.tail3641f4.ts.net:10000 (TLS-terminated TCP, Funnel on)
|-- tcp://100.69.53.52:10000
|-- tcp://[fd7a:115c:a1e0::4335:3536]:10000
|--> tcp://127.0.0.1:22

https://gha-ubuntu.tail3641f4.ts.net:8443 (Funnel on)
|-- / proxy http://127.0.0.1:8080

-- funnel status --

# Funnel on:
#     - tcp://gha-ubuntu.tail3641f4.ts.net:10000
#     - https://gha-ubuntu.tail3641f4.ts.net:8443

|-- tcp://gha-ubuntu.tail3641f4.ts.net:10000 (TLS-terminated TCP, Funnel on)
|-- tcp://100.69.53.52:10000
|-- tcp://[fd7a:115c:a1e0::4335:3536]:10000
|--> tcp://127.0.0.1:22

https://gha-ubuntu.tail3641f4.ts.net:8443 (Funnel on)
|-- / proxy http://127.0.0.1:8080

-- تلاش‌های funnel (ssh) --
Available on the internet:

|-- tcp://gha-ubuntu.tail3641f4.ts.net:10000 (TLS terminated)
|-- tcp://100.69.53.52:10000
|-- tcp://[fd7a:115c:a1e0::4335:3536]:10000
|--> tcp://127.0.0.1:22

Funnel started and running in the background.
To disable the proxy, run: tailscale funnel --tls-terminated-tcp=10000 off
-- تلاش‌های funnel (web 8443) --
Available on the internet:

https://gha-ubuntu.tail3641f4.ts.net:8443/
|-- proxy http://127.0.0.1:8080

Funnel started and running in the background.
To disable the proxy, run: tailscale funnel --https=8443 off
-- تلاش‌های funnel (web 443) --
cat: /tmp/f_443.log: No such file or directory
-- fallback serve --
cat: /tmp/s_ssh.log: No such file or directory
-- resolve عمومی --
2607:f740:f::b31 gha-ubuntu.tail3641f4.ts.net
2607:f740:f::67 gha-ubuntu.tail3641f4.ts.net
```
