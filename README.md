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
