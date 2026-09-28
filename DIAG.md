# گزارش تشخیصی

```
== date: Mon Sep 28 10:15:50 UTC 2026 ==
== sshd -T (تنظیمات مؤثر) ==
authenticationmethods any
kbdinteractiveauthentication no
passwordauthentication yes
permitemptypasswords no
permitrootlogin yes
pubkeyauthentication yes
usepam yes
== passwd -S root ==
root P 09/28/2026 -1 -1 -1 -1
== sshpass test (روش ۱) ==
Warning: Permanently added '127.0.0.1' (ED25519) to the list of known hosts.
root@127.0.0.1: Permission denied (publickey,password).
== askpass test (روش ۲) ==
Warning: Permanently added '127.0.0.1' (ED25519) to the list of known hosts.
root@127.0.0.1: Permission denied (publickey,password).
== port 10000 on 127.0.0.1 ==
bash: connect: Connection refused
== port 10000 on 100.96.62.11 ==

== port 22 banner on 100.96.62.11 ==
== لاگ sshd ==
tail: cannot open '/tmp/sshd.log' for reading: No such file or directory
no sshd log
== ts status ==
100.96.62.11    gha-ubuntu        novinsazeh.mrv@  linux    idle; offers exit node     
100.85.218.16   hamid             novinsazeh.mrv@  windows  offline, last seen 4h ago  
100.74.157.108  hrg-backup        novinsazeh.mrv@  linux    offline, last seen 3m ago  
100.70.83.2     linux-server-vps  novinsazeh.mrv@  linux    idle; offers exit node     
100.98.52.75    nothing-phone-1   novinsazeh.mrv@  android  offline, last seen 2h ago  
== tags این گره ==
{"Tags":null,"OS":"linux","DNSName":"gha-ubuntu.tail3641f4.ts.net.","Online":true}
== serve status ==
|-- tcp://gha-ubuntu.tail3641f4.ts.net:10000 (TLS-terminated TCP, tailnet only)
|-- tcp://100.96.62.11:10000
|-- tcp://[fd7a:115c:a1e0::1835:3e0c]:10000
|--> tcp://127.0.0.1:22

https://gha-ubuntu.tail3641f4.ts.net:8443 (tailnet only)
|-- / proxy http://127.0.0.1:8080

== funnel status ==
|-- tcp://gha-ubuntu.tail3641f4.ts.net:10000 (TLS-terminated TCP, tailnet only)
|-- tcp://100.96.62.11:10000
|-- tcp://[fd7a:115c:a1e0::1835:3e0c]:10000
|--> tcp://127.0.0.1:22

https://gha-ubuntu.tail3641f4.ts.net:8443 (tailnet only)
|-- / proxy http://127.0.0.1:8080

== resolve عمومی نام گره ==
public DNS: NXDOMAIN
```
