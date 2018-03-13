---
title: "Restart Debian Networking"
categories: [linux, commands]
tags: [linux, ubuntu, ip, flush, networking]
description: "Restart Debian Networking" 
---


It's been a while since I haven't written anything in particular; But, That's life :)

Anyhow, when you make a change in debian network interfaces through `/etc/network/interfaces`, no matter how hard you strive, you would not be able to force it to load newly assigned IP in place. 

Here is the trick: Just flush previous IP using following command and restart your networking. 

```
# ip addr flush interface-name
# systemctl restart networking
```

Most certainly, `interface-name` needs to be replaced with your interface name. 

Enjoy :)
