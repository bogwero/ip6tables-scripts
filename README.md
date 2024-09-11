# ip6tables
IPv6 firewall for ip6tables

Trying to build rules for ip6tables

Thsi script intended for learning how to setup firewall with ip6tables.

----------------------------------------------


# Advanced iptables and ip6tables persistent firewall configuration

Configuration files for Linux kernel iptables firewall. Read [this article](https://cryptsus.com/blog/advanced-perimeter-based-iptables-firewall-on-linux.html) for more information.

Make iptables configuration persistent on start-up:
```bash
$ chmod +x /sbin/scripts/4iptables.sh 
$ chmod +x /sbin/scripts/6iptables.sh

$ bash /sbin/scripts/4iptables.sh 
$ bash /sbin/scripts/6iptables.sh

$ chmod +x /sbin/scripts/iptables4.rules
$ chmod +x /sbin/scripts/iptables6.rules
```

Make iptables configuration persistent on start-up:
```bash
$ vi /etc/network/if-pre-up.d/iptables
#!/bin/bash
/sbin/iptables-restore < /sbin/scripts/iptables4.rules
/sbin/ip6tables-restore < /sbin/scripts/iptables6.rules
```
Make iptables pre-up file executable for startup:
```bash
$ chmod +x /etc/network/if-pre-up.d/iptables
$ vi /etc/nftables.conf
```
Verify and troubelshoot configuration:
Make nftables persistant on boot:
```bash
$ iptables -vL
$ systemctl enable nftables
$ systemctl start nftables
$ systemctl status nftables
```
