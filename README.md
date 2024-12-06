# Jarkom-Modul-5-IT09-2024

## Anggota Kelompok
| Anggota | NRP  |
| ------- | --- |
| Michael Kenneth Salim | 5027231008 | 
| Tio Axelino | 5027231065 |

## Topologi Jaringan
![Topologi(Done)](https://github.com/user-attachments/assets/5c23a194-07ba-4210-9174-500e2e354ba8)

## Rute
| **Nama Subnet** | **Rute**                                           | **Jumlah IP** | **Netmask** |
|------------------|---------------------------------------------------|---------------|-------------|
| A1              | NewEridu > SixStreet                              | 2             | /30         |
| A2              | NewEridu > SixStreet > RandomPlay > Fairy > RandomPlay > HDD | 3             | /29         |
| A3              | NewEridu > SixStreet > Metro > ScootOutpost > Metro > OuterRing | 3             | /29         |
| A4              | NewEridu > SixStreet > Metro > ScootOutpost > HollowZero | 2             | /30         |
| A5              | NewEridu > SixStreet > Metro > OuterRing > SoC > Caesar > SoC > Burnice | 56            | /26         |
| A6              | NewEridu > LuminaSquare                           | 2             | /30         |
| A7              | NewEridu > LuminaSquare > PubSec > Jane > PubSec > Policeboo | 231           | /24         |
| A8              | NewEridu > LuminaSquare > Ofc.Mewmew > HIA > BalletTwins | 3             | /29         |
| A9              | NewEridu > LuminaSquare > Ofc.Mewmew > BalletTwins > Victoria > Lycaon > Victoria > Ellen | 121           | /25         |
| **Total**       |                                                   | **423**       | **/23**     |

## Pembagian IP
| **Subnet** | **Network ID** | **Netmask**       | **Broadcast** | **Range IP**                   |
|------------|----------------|-------------------|---------------|--------------------------------|
| A1         | 10.68.1.216    | 255.255.255.252  | 10.68.1.219   | 10.68.1.217 - 10.68.1.218     |
| A2         | 10.68.1.192    | 255.255.255.248  | 10.68.1.199   | 10.68.1.193 - 10.68.1.198     |
| A3         | 10.68.1.200    | 255.255.255.248  | 10.68.1.207   | 10.68.1.201 - 10.68.1.206     |
| A4         | 10.68.1.220    | 255.255.255.252  | 10.68.1.223   | 10.68.1.221 - 10.68.1.222     |
| A5         | 10.68.1.128    | 255.255.255.192  | 10.68.1.191   | 10.68.1.129 - 10.68.1.190     |
| A6         | 10.68.1.224    | 255.255.255.252  | 10.68.1.227   | 10.68.1.225 - 10.68.1.226     |
| A7         | 10.68.0.0      | 255.255.255.0    | 10.68.0.255   | 10.68.0.1 - 10.68.0.254       |
| A8         | 10.68.1.208    | 255.255.255.248  | 10.68.1.215   | 10.68.1.209 - 10.68.1.214     |
| A9         | 10.68.1.0      | 255.255.255.128  | 10.68.1.127   | 10.68.1.1 - 10.68.1.126       |

## Configuration

### NewEridu
```sh
auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet static
	address 10.68.1.218
	netmask 255.255.255.252

auto eth2
iface eth2 inet static
	address 10.68.1.226
	netmask 255.255.255.252
```

### Six Street
```sh
auto eth0
iface eth0 inet static
  address 10.68.1.217
  netmask 255.255.255.252
  getaway 10.68.1.218

auto eth1
iface eth1 inet static
	address 10.68.1.198
	netmask 255.255.255.248

auto eth2
iface eth2 inet static
	address 10.68.1.206
	netmask 255.255.255.248
```

### HDD
```sh
auto eth0
iface eth0 inet static
  address 10.68.1.197
  netmask 255.255.255.248
  gateway 10.68.1.198
```

### Fairy
```sh
auto eth0
iface eth0 inet static
  address 10.68.1.196
  netmask 255.255.255.248
  gateway 10.68.1.198
```


### ScootOutpost
```sh
auto eth0
iface eth0 inet static
  address 10.68.1.205
  netmask 255.255.255.248
  gateway 10.68.1.206

auto eth1
iface eth1 inet static
  address 10.68.1.222
  netmask 255.255.255.252
```

### HollowZero
```sh
auto eth0
iface eth0 inet static
  address 10.68.1.221
  netmask 255.255.255.252
  gateway 10.68.1.222
```

### OuterRing
```sh
auto eth0
iface eth0 inet static
  address 10.68.1.204
  netmask 255.255.255.248
  gateway 10.68.1.206

auto eth1
iface eth1 inet static
  address 10.68.1.190
  netmask 255.255.255.192
```

### LuminaSquare
```sh
auto eth0
iface eth0 inet static
  address 10.68.1.225
  netmask 255.255.255.252
  gateway 10.68.1.224

auto eth1
iface eth1 inet static
  address 10.68.0.254
  netmask 255.255.255.0

auto eth2
iface eth2 inet static
  address 10.68.1.214
  netmask 255.255.255.248
```

### HIA
```sh
auto eth0
iface eth0 inet static
  address 10.68.1.213
  netmask 255.255.255.248
  gateway 10.68.1.214
```

### BalletTwins
```sh
auto eth0
iface eth0 inet static
  address 10.68.1.212
  netmask 255.255.255.248
  gateway 10.68.1.214

auto eth1
iface eth1 inet static
  address 10.68.1.126
  netmask 255.255.255.128
```

### Clients (Caesar, Burnice, Jane, PoliceBoo, Ellen, Lyacon)
```sh
auto eth0
iface eth0 inet dhcp
```

## Routing

### NewEridu
```sh
#A2
route add -net 10.68.1.192 netmask 255.255.255.248 gw 10.68.1.217

#A3
route add -net 10.68.1.200 netmask 255.255.255.248 gw 10.68.1.217

#A4
route add -net 10.68.1.220 netmask 255.255.255.252 gw 10.68.1.217

#A5
route add -net 10.68.1.128 netmask 255.255.255.192 gw 10.68.1.217

#A7
route add -net 10.68.0.0 netmask 255.255.255.0 gw 10.68.1.225

#A8
route add -net 10.68.1.208 netmask 255.255.255.248 gw 10.68.1.225

#A9
route add -net 10.68.1.0 netmask 255.255.255.128 gw 10.68.1.225

echo 'routing berhasil'

#iptables awal
IP_ETH0=$(ip -4 addr show eth0 | grep -oP '(?<=inet\s)\d+(\.\d+){3}')
iptables -t nat -A POSTROUTING -o eth0 -j SNAT --to-source $IP_ETH0
```

### Six Street
```sh
#A4
route add -net 10.68.1.220 netmask 255.255.255.252 gw 10.68.1.205

#A5
route add -net 10.68.1.128 netmask 255.255.255.192 gw 10.68.1.205

#A7
route add -net 10.68.0.0 netmask 255.255.255.0 gw 10.68.1.218

#A8
route add -net 10.68.1.208 netmask 255.255.255.248 gw 10.68.1.218

#A9
route add -net 10.68.1.0 netmask 255.255.255.128 gw 10.68.1.218

echo 'nameserver 192.168.122.1' > /etc/resolv.conf
apt-get update
apt install isc-dhcp-relay -y

echo 'SERVERS="10.68.1.196"
INTERFACES="eth0 eth1 eth2 eth3"
OPTIONS=""
' > /etc/default/isc-dhcp-relay

echo 'net.ipv4.ip_forward=1' >> /etc/sysctl.conf

service isc-dhcp-relay restart
```

### OuterRing
```bash
#A2
route add -net 10.68.1.220 netmask 255.255.255.252 gw 10.68.1.206

#A4
route add -net 10.68.1.192 netmask 255.255.255.252 gw 10.68.1.205

#A7
route add -net 10.68.0.0 netmask 255.255.255.00 gw 10.68.1.206

#A8
route add -net 10.68.1.208 netmask 255.255.255.248  gw 10.68.1.206

#A9
route add -net 10.68.1.0 netmask 255.255.255.128 gw 10.68.1.206

echo 'nameserver 192.168.122.1' > /etc/resolv.conf
apt-get update
apt install isc-dhcp-relay -y

echo 'SERVERS="10.68.1.196"
INTERFACES="eth0 eth1 eth2 eth3"
OPTIONS=""
' > /etc/default/isc-dhcp-relay

echo 'net.ipv4.ip_forward=1' >> /etc/sysctl.conf

service isc-dhcp-relay restart
```

### ScootOutpost
```bash
#A2
route add -net 10.68.1.192 netmask 255.255.255.248 gw 10.68.1.206

#A5
route add -net 10.68.1.128 netmask 255.255.255.192 gw 10.68.2.204

#A7
route add -net 10.68.0.0 netmask 255.255.255.0 gw 10.68.2.206

#A8
route add -net 10.68.1.208 netmask 255.255.255.248 gw 10.68.2.206

#A9
route add -net 10.68.1.0 netmask 255.255.255.128 gw 10.68.2.206

echo 'nameserver 192.168.122.1' > /etc/resolv.conf
```

### Fairy (DHCP Server)
```bash
echo 'nameserver 192.168.122.1' > /etc/resolv.conf
apt-get update
apt-get install isc-dhcp-server netcat -y

echo 'INTERFACESv4="eth0"' > /etc/default/isc-dhcp-server

echo '#A5
subnet 10.68.1.128 netmask 255.255.255.192 {
        range 10.68.1.129 10.68.1.189;
        option routers 10.68.1.190; # Gateway
        option broadcast-address 10.68.1.191;
        option domain-name-servers 10.68.1.197; #IP HDD
        default-lease-time 600;
        max-lease-time 7200;
}

#A7
subnet 10.68.0.0 netmask 255.255.255.0 {
        range 10.68.0.1 10.68.0.253;
        option routers 10.68.1.254;
        option broadcast-address 10.68.1.255;
        option domain-name-servers 10.68.1.197;
        default-lease-time 600;
        max-lease-time 7200;
}

#A9
subnet 10.68.1.0 netmask 255.255.255.128 {
        range 10.68.1.1 10.68.1.125;
        option routers 10.68.1.126;
        option broadcast-address 10.68.1.127;
        option domain-name-servers 10.68.1.197;
        default-lease-time 600;
        max-lease-time 7200;
}

subnet 10.68.1.216 netmask 255.255.255.252 {}
subnet 10.68.1.192 netmask 255.255.255.248 {}
subnet 10.68.1.220 netmask 255.255.255.252 {}
subnet 10.68.1.200 netmask 255.255.255.248 {}
subnet 10.68.1.224 netmask 255.255.255.252 {}
subnet 10.68.1.208 netmask 255.255.255.248 {}
' > /etc/dhcp/dhcpd.conf

service isc-dhcp-server restart
```

### HDD (DNS Server)
```bash
echo 'nameserver 192.168.122.1' > /etc/resolv.conf
apt-get update
apt-get install bind9 netcat -y

echo 'options {
        directory "/var/cache/bind";

        forwarders {
                192.168.122.1;
        };

        // dnssec-validation auto;
        allow-query{any;};
        auth-nxdomain no;
        listen-on-v6 { any; };
}; ' >/etc/bind/named.conf.options

service bind9 restart
```

### HIA & HollowZero (Apache Worker)
```bash
echo 'nameserver 192.168.122.1' > /etc/resolv.conf
apt-get update
apt-get install apache2 netcat -y

service apache2 start

echo 'Welcome to {hostname}' > /var/www/html/index.html

service apache2 restart
```

### LuminaSquare
```bash
#A2
route add -net 10.68.1.192 netmask 255.255.255.248 gw 10.68.1.226

#A4
route add -net 10.68.1.220 netmask 255.255.255.252 gw 10.68.1.226

#A5
route add -net 10.68.1.128 netmask 255.255.255.192 gw 10.68.1.226

#A9
route add -net 10.68.1.0 netmask 255.255.255.128 gw 10.68.1.212

echo 'nameserver 192.168.122.1' > /etc/resolv.conf
apt-get update
apt install isc-dhcp-relay -y

echo 'SERVERS="10.68.1.196"
INTERFACES="eth0 eth1 eth2 eth3"
OPTIONS=""
' > /etc/default/isc-dhcp-relay

echo 'net.ipv4.ip_forward=1' >> /etc/sysctl.conf

service isc-dhcp-relay restart
```

### BalletTwins
```bash
#A2
route add -net 10.68.1.192 netmask 255.255.255.248 gw 10.68.1.214

#A4
route add -net 10.68.1.220 netmask 255.255.255.252 gw 10.68.1.214

#A5
route add -net 10.68.1.128 netmask 255.255.255.252 gw 10.68.1.214

#A7
route add -net 10.68.0.0 netmask 255.255.255.0 gw 10.68.1.214

echo 'nameserver 192.168.122.1' > /etc/resolv.conf
apt-get update
apt install isc-dhcp-relay -y

echo 'SERVERS="10.68.1.196"
INTERFACES="eth0 eth1 eth2 eth3"
OPTIONS=""
' > /etc/default/isc-dhcp-relay

echo 'net.ipv4.ip_forward=1' >> /etc/sysctl.conf

service isc-dhcp-relay restart
```

## Misi 2
### 1. Menyambungkan NewEridu terhubung ke internet menggunakan iptables tanpa MASQUERADE

```bash
iptables -t nat -A POSTROUTING -o eth0 -j SNAT --to-source [IP eth0]
```

### 2. Agar tidak ada node yang bisa ping ke Fairy tapi Fairy tetap bisa ping ke node lain, lakukan konfigurasi berikut di Fairy

```bash
iptables -A INPUT -p icmp --icmp-type echo-request -j DROP

iptables -A OUTPUT -p icmp --icmp-type echo-request -j ACCEPT
```

Kita bisa hapus aturan dengan
```bash
iptables -D INPUT -p icmp --icmp-type echo-request -j DROP
iptables -D OUTPUT -p icmp --icmp-type echo-request -j ACCEPT
```

### 3. Agar HDD hanya bisa diakses oleh Fairy, lakukan konfigurasi berikut di HDD
```bash
iptables -A INPUT -s 10.68.1.196 -j ACCEPT

iptables -A INPUT -j REJECT
```

Lakukan pengujian dengan menggunakan netcat
```bash
#Pada HDD
nc -l -p 2456

#Pada Fairy
nc 10.68.1.196 2456
```

### 4. HollowZero hanya bisa diakses oleh 4 node dan hanya di hari Senin hingga Jumat, gunakan konfigurasi ini di HollowZero

```bash
iptables -A INPUT -p tcp -s <IP_Burnice> --dport 80 -m time --timestart 00:00 --timestop 23:59 --weekdays Mon,Tue,Wed,Thu,Fri -j ACCEPT

iptables -A INPUT -p tcp -s <IP_Caesar> --dport 80 -m time --timestart 00:00 --timestop 23:59 --weekdays Mon,Tue,Wed,Thu,Fri -j ACCEPT

iptables -A INPUT -p tcp -s <IP_Jane> --dport 80 -m time --timestart 00:00 --timestop 23:59 --weekdays Mon,Tue,Wed,Thu,Fri -j ACCEPT

iptables -A INPUT -p tcp -s <IP_Policeboo> --dport 80 -m time --timestart 00:00 --timestop 23:59 --weekdays Mon,Tue,Wed,Thu,Fri -j ACCEPT

iptables -A INPUT -p tcp --dport 80 -j REJECT
```

Menggunakan command berikut untuk verifikasi akses
```bash
curl http://10.68.1.221
```

### 5. Konfigurasi agar HIA hanya bisa diakses oleh Ellen dan Lycaon pada pukul 08:00 - 21:00 dan bisa diakses oleh Jane serta Policeboo hanya pada pukul 03:00 - 23:00

```bash
# Akses Node Ellen dan Lycaon
iptables -A INPUT -p tcp -s <IP Ellen> --dport 80 -m time --timestart 01:00 --timestop 14:00 --weekdays Mon,Tue,Wed,Thu,Fri,Sat,Sun -j ACCEPT

iptables -A INPUT -p tcp -s <IP Lycaon> --dport 80 -m time --timestart 01:00 --timestop 14:00 --weekdays Mon,Tue,Wed,Thu,Fri,Sat,Sun -j ACCEPT

# Akses Node Jane dan Policeboo
iptables -A INPUT -p tcp -s <IP Jane> --dport 80 -m time --timestart 20:00 --timestop 16:00 --weekdays Mon,Tue,Wed,Thu,Fri,Sat,Sun -j ACCEPT

iptables -A INPUT -p tcp -s <IP Policeboo> --dport 80 -m time --timestart 20:00 --timestop 16:00 --weekdays Mon,Tue,Wed,Thu,Fri,Sat,Sun -j ACCEPT

# Tolak semua koneksi lainnya
iptables -A INPUT -p tcp --dport 80 -j REJECT
```

### 6. Aktivitas di HIA harus dibatasi, HIA harus memblokir aktivitas port scanning yang melebihi 25 port dalam rentang 10 detik, penyerang yang diblokir tidak bisa ping, nc, atau curl ke HIA, log dari iptables akan tercatat untuk analisis.

```bash
# atur limit
iptables -N PORTSCAN
iptables -A INPUT -p tcp --dport 1:100 -m state --state NEW -m recent --set --name portscan
iptables -A INPUT -p tcp --dport 1:100 -m state --state NEW -m recent --update --seconds 10 --hitcount 25 --name portscan -j PORTSCAN

# Blokir IP
iptables -A PORTSCAN -m recent --set --name blacklist
iptables -A PORTSCAN -j DROP

# Blokir semua aktivitas dari IP yang ada di daftar blacklist
iptables -A INPUT -m recent --name blacklist --rcheck -j REJECT
iptables -A OUTPUT -m recent --name blacklist --rcheck -j REJECT

# Logging untuk port scanning
iptables -A PORTSCAN -j LOG --log-prefix='PORT SCAN DETECTED' --log-level 4
```

### 7. Pada HollowZero ada ketentuan bahwa hanya ada 2 koneksi aktif dari 2 IP berbeda dalam waktu bersamaan yang diperbolehkan, maka dari itu gunakan konfigurasi berikut di HollowZero

```bash
iptables -A INPUT -p tcp --dport 80 -m conntrack --ctstate NEW -m recent --set
iptables -A INPUT -p tcp --dport 80 -m conntrack --ctstate NEW -m recent --update --seconds 1 --hitcount 3 -j REJECT
iptables -A INPUT -p tcp --dport 80 -j ACCEPT
```

Lakukan pengujian bersamaan di 4 Node terkait dengan menggunakan `parallel curl -s http://IP-HollowZero ::: IP-Caesar IP-Burnice IP-Jane IP-Policeboo`

