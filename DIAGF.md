# گزارش تشخیص Funnel

```
date: Mon Sep 28 10:35:14 UTC 2026
hostname: diag-91710
fqdn: diag-91710.tail3641f4.ts.net
ts ip: 100.84.148.88
tailscale version: 1.102.4

=====Self JSON (tags/caps)=====
{
  "DNSName": "diag-91710.tail3641f4.ts.net.",
  "Tags": null,
  "CapabilityVersion": null,
  "Online": true,
  "Owner": null,
  "HostName": "diag-91710",
  "KeyExpiry": "2027-03-27T10:35:10Z"
}

=====device info از API=====
device id: 7226661929294272
{
  "hostname": "diag-91710",
  "tags": null,
  "effectiveTags": null,
  "user": "novinsazeh.mrv@gmail.com",
  "authorized": true,
  "isEphemeral": true,
  "blocksIncomingConnections": false
}

=====ACL فعلی=====
{
  "nodeAttrs": [
    {
      "target": [
        "tag:ci",
        "100.70.83.2"
      ],
      "attr": [
        "funnel"
      ]
    },
    {
      "target": [
        "100.68.36.53"
      ],
      "attr": [
        "funnel"
      ]
    },
    {
      "target": [
        "novinsazeh.mrv@gmail.com",
        "autogroup:member"
      ],
      "attr": [
        "funnel"
      ]
    }
  ],
  "autoApprovers": {
    "routes": {
      "0.0.0.0/0": [
        "novinsazeh.mrv@gmail.com",
        "tag:ci"
      ],
      "::/0": [
        "novinsazeh.mrv@gmail.com",
        "tag:ci"
      ]
    },
    "exitNode": [
      "autogroup:member",
      "novinsazeh.mrv@gmail.com",
      "tag:ci"
    ]
  },
  "tagOwners": {
    "tag:ci": [
      "autogroup:admin"
    ]
  }
}

=====تلاش ۱: funnel --bg --yes --https=443 (پورت پیش‌فرض)=====
Error: invalid argument format
try `tailscale funnel --help` for usage info
rc=0

=====تلاش ۲: funnel --bg --yes --https=8443 URL=====
Available on the internet:

https://diag-91710.tail3641f4.ts.net:8443/
|-- proxy http://127.0.0.1:8080

Funnel started and running in the background.
To disable the proxy, run: tailscale funnel --https=8443 off
rc=0

=====تلاش ۳: funnel --bg --tls-terminated-tcp=10000 (بدون --yes)=====
Available on the internet:

|-- tcp://diag-91710.tail3641f4.ts.net:10000 (TLS terminated)
|-- tcp://100.84.148.88:10000
|-- tcp://[fd7a:115c:a1e0::2d35:9459]:10000
|--> tcp://127.0.0.1:22

Funnel started and running in the background.
To disable the proxy, run: tailscale funnel --tls-terminated-tcp=10000 off
rc=0

=====تلاش ۴: funnel بدون --bg (۲۰ ثانیه)=====
sending serve config: updating config: listener already exists for port 10000
rc=0

=====funnel status --json=====
{
  "TCP": {
    "10000": {
      "TCPForward": "127.0.0.1:22",
      "TerminateTLS": "diag-91710.tail3641f4.ts.net"
    },
    "8443": {
      "HTTPS": true
    }
  },
  "Web": {
    "diag-91710.tail3641f4.ts.net:8443": {
      "Handlers": {
        "/": {
          "Proxy": "http://127.0.0.1:8080"
        }
      }
    }
  },
  "AllowFunnel": {
    "diag-91710.tail3641f4.ts.net:10000": true,
    "diag-91710.tail3641f4.ts.net:8443": true
  }
}

=====serve status=====

# Funnel on:
#     - tcp://diag-91710.tail3641f4.ts.net:10000
#     - https://diag-91710.tail3641f4.ts.net:8443

|-- tcp://diag-91710.tail3641f4.ts.net:10000 (TLS-terminated TCP, Funnel on)
|-- tcp://100.84.148.88:10000
|-- tcp://[fd7a:115c:a1e0::2d35:9459]:10000
|--> tcp://127.0.0.1:22

https://diag-91710.tail3641f4.ts.net:8443 (Funnel on)
|-- / proxy http://127.0.0.1:8080


=====تست واقعی از بیرون (curl)=====
https://diag-91710.tail3641f4.ts.net:8443/ -> 000
https://diag-91710.tail3641f4.ts.net/ -> 000

=====debug prefs=====
{
  "ServeConfig": null
}
```
