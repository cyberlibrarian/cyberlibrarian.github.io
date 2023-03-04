---
layout: post
title:  "Wireguard Internet Gateway"
author: michael
#image: assets/images/2023-xxx
tags: [networking,vpn,tunnels]
date: 2020-05-01 19:00:00
---
#
On Debian you have to add the unstable branch to /etc/apt/sources.list

	1. apt install linux-headers-$(uname -r) wireguard wireguard-dkms wireguard-tools 
	2. reboot
	3. modprobe wireguard
	4. systemctrl enable wg-quick@wg0
	5. generate wireguard key
	$ (umask 077 && wg genkey > wg-private.key)
$ wg pubkey < wg-private.key > wg-public.key
	
	From <https://wireguard.how/server/debian/> 
	
	6. Copy the key to /etc/wireguard/wg0.conf
	$ cat wg-private.key
qPF9uU7qsCbw3uKR1t2Q0gfr2HasTKZGPkCHz2AszUs=
	
	From <https://wireguard.how/server/debian/> 
	
	7. edit /etc/wireguard/wg0.conf
	8. edit /etc/network/interfaces.d/wg0
	# indicate that wg0 should be created when the system boots, and on ifup -a
auto wg0
	# describe wg0 as an IPv4 interface with static address
iface wg0 inet static
	# static IP address 
        address 10.0.2.1/24
	# before ifup, create the device with this ip link command
        pre-up ip link add $IFACE type wireguard
	# before ifup, set the WireGuard config from earlier
        pre-up wg setconf $IFACE /etc/wireguard/$IFACE.conf
	# after ifdown, destroy the wg0 interface
        post-down ip link del $IFACE
	
	From <https://wireguard.how/server/debian/> 
	9. bring up wg0
		a. ifup wg0
	10. verify
		a. ip address show dev wg0
	11. setup routing
		a. Set our default route to go over wg0
		b. Verify that our DNS is not leaking
		c. edit the default interface (ens33), and set it so there is a route to the VPS ONLY
		d. If wg0 is down, nothing should route
			i. verify
		

Server:

[Interface]
Address = 172.30.0.1/24
SaveConfig = false
ListenPort = 51820
PrivateKey = 
PostUp = iptables -A FORWARD -i wg0 -j ACCEPT; iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE
PostDown = iptables -D FORWARD -i wg0 -j ACCEPT; iptables -t nat -D POSTROUTING -o eth0 -j MASQUERADE

[Peer]
PublicKey = 4uUcAWL6VFHPCdPP0cSpnHLD9XlPPa5vW80jxO/zBz8=
AllowedIPs = 172.30.0.0/24



iptables -A PREROUTING -t nat -i eth0 -p tcp --dport 80 -j DNAT --to 192.168.1.2:8080
# iptables -A FORWARD -p tcp -d 192.168.1.2 --dport 8080 -j ACCEPT

From <https://www.systutorials.com/port-forwarding-using-iptables/> 




Client

[Interface]
Address = 172.30.0.2/24
SaveConfig = false
PrivateKey = 
PostUp = /etc/wireguard/route-up.sh
PostDown = /etc/wireguard/route-down.sh

[Peer]
PublicKey = 
AllowedIPs = 0.0.0.0/0


Route-up.sh

ip route add 165.22.228.147 via 10.0.0.1
ip route add default via 172.30.0.1

route-down.sh
ip route del default via 172.30.0.1
ip route add default via 10.0.0.1


References

	- https://medium.com/@drew2a/replace-your-vpn-provider-by-setting-up-wireguard-on-digitalocean-6954c9279b17
	- https://raw.githubusercontent.com/drew2a/wireguard/master/wg-ububtu-server-up.sh
https://raw.githubusercontent.com/drew2a/wireguard/master/wg-genconf.sh