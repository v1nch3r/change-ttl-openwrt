# Tutorial
Fix TTL OpenWRT
Silahkan Ganti Range TTL Sesuai Yang Anda Inginkan
Kalau Silahkan Edit/Tambah Interface Yang Menurut Situ Jalur Masuk Keluar Internet
buka custom rules lalu tambahkan dan sesuaikan dengan script di bawah ini

### Interface
ETH0="eth0"
ETH1="eth1"
BRLAN="br-lan"
USB0="usb0"

### TTL Bypass
iptables -t mangle -I POSTROUTING -o $ETH0 -j TTL --ttl-set 58
iptables -t mangle -I POSTROUTING -o $ETH1 -j TTL --ttl-set 58
iptables -t mangle -I POSTROUTING -o $BRLAN -j TTL --ttl-set 58
iptables -t mangle -I POSTROUTING -o $USB0 -j TTL --ttl-set 58
iptables -t mangle -I PREROUTING -i $ETH0 -j TTL --ttl-set 58
iptables -t mangle -I PREROUTING -i $ETH1 -j TTL --ttl-set 58
iptables -t mangle -I PREROUTING -i $BRLAN -j TTL --ttl-set 58
iptables -t mangle -I POSTROUTING -o $USB0 -j TTL --ttl-set 58
