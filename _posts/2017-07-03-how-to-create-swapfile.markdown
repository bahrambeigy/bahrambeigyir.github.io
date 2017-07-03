---
title:  "How to create swapfile"
categories: [linux, swapfile]
tags: [swapfile, linux, ubuntu, manual]
description: "How to create swapfile" 
---

Swapfile comes readlly handy when you want to increase or change the size of your swap space. 

### [Allocate](#allocate_swapfile):
Using Ubuntu you can allocate your required space using user-friendly command as follows:
```
fallocate -l 4G /swapfile
```

Or you might want to go through the hard way : 
```
dd if=/dev/zero of=/swapfile bs=1024 count=65536
```

**Explanation**: 
Set the size to the count argument as megabytes multiply 1024, for example 64 MB would be 64x1024=65536 or 8 GB would be 8x1024x1024=8388608


Now apply correct permissions, so that only root can access it : 
```
chmod 600 /swapfile
```

### [Create and Turn-on](#create_swapfile):
Using following command the previously allocated space will be converted to a swap space : 
```
mkswap /swapfile
```

Now, test your newly created swapfile: 
```
swapon /swapfile
```
### [Make it permanent](#permanent_swapfile):
You can make it permanent by adding to the `/etc/fstab` file:
```
/swapfile   none    swap    sw    0   0
```

### [Tune it](#tune_swapfile):
Now, lower the swapiness and cache pressure by putting these values into your `/etc/sysctl.conf` file: 

```
vm.swappiness=10
vm.vfs_cache_pressure = 50
```

Good Luck!
 
Reference: [DigitalOcean](https://www.digitalocean.com/community/tutorials/how-to-add-swap-space-on-ubuntu-16-04){:target="_blank"}
