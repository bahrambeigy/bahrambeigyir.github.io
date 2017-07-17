---
title:  "Useful IP Commands"
categories: [linux, commands]
tags: [linux, ubuntu, ip, route, ifconfig, reference]
description: "Useful IP Commands in Linux" 
---

In recent Linux distributions, traditional `route` and `ifconfig` commands are deprecated and mostly cannot be found. They are replaced by a very neat tool "ip". 

### [Show, Set or Delete IP Addresses](#show_set_del_ip_address):
Instead of `ifconfig` you can use the following ip command: 
```
# ip addr show
```
The output would be something like this: 
```
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: eth0: ...
```
You can assign an IP address to the previously shown interface using ip command : 
```
# ip addr add 192.168.50.5/24 dev eth0
```
Now you must change the interface status to up by : 
```
# ip link set eth0 up
```
You might want to add your recently assigned IP address afterwards: 
```
# ip addr del 192.168.50.5/24 dev eth0
```

### [Show, Set or Delete Routes](#show_set_del_routes):
Similarly, instead of ancient `route` command you can use ip as follows:
```
# ip route show
```
The result would something like this:
```
default via 192.168.50.1 dev eth0 proto static metric 100 
192.168.50.0/24 dev eth0 proto kernel scope link src 192.168.50.6 metric 100
```
In order to add a static route, you can use the following command: 
```
# ip route add 10.10.20.0/24 via 192.168.50.100 dev eth0
```
Or somehow, you might want to delete the route you just added: 
```
# ip route del 10.10.20.0/24
```

### [Set Default Route](#set_default_route):
In the past, we used to issue the command `route add default gw`, but the ip-way is as follows:
```
# ip route add default via 192.168.50.100
```

Good Luck!
Reference: [TechMint](https://www.tecmint.com/ip-command-examples/){:target="_blank"}
