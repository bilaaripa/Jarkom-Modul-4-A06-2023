# Jarkom-Modul-4-A06-2023

## Anggota Kelompok

| NRP        | Nama                        |
| ---------- | --------------------------- |
| 5025211057 | Salsabila Fatma Aripa       |
| 5025211254 | Yusna Millaturrosyidah      |

## Daftar Isi
- [Topologi CPT CIDR](#topologi-cpt-cidr)
- [Topologi GNS VLSM](#topologi-gns-vlsm)
- [Prefix IP](#prefix-ip)
- [Rute](#rute)
- [VLSM](#vlsm)
  - [Tree](#tree)
  - [Pembagian IP](#pembagian-ip)
  - [Konfigurasi Network](#konfigurasi-network)
  - [Routing](#routing)
  - [Testing](#testing) 
- [CIDR](#cidr)
  - [Penggabungan IP](#penggabungan-ip)
  - [Tree](#tree)
  - [Pembagian IP](#pembagian-ip)

## Topologi CPT CIDR
<img width="1000" alt="topologi cpt" src="https://github.com/bilaaripa/Jarkom-Modul-4-A06-2023/assets/91377793/b6269c02-ccee-4666-83a1-2f84b94277d7">

## Topologi GNS VLSM

![Screenshot 2023-12-04 021014](https://github.com/bilaaripa/Jarkom-Modul-4-A06-2023/assets/114417418/cfbee8d1-6ef4-4f58-815c-98754dfef494)

## Prefix IP
Kelompok A06 memiliki prefix IP `10.2`

## Rute

![Screenshot 2023-12-04 020832](https://github.com/bilaaripa/Jarkom-Modul-4-A06-2023/assets/114417418/31451394-ef04-4bf9-a41b-62833732df5e)

## VLSM
Variable Length Subnet Masking (VLSM) adalah sebuah metode dalam pengelompokan alamat IP pada jaringan komputer. Metode ini memungkinkan kita untuk mengalokasikan subnet dengan panjang yang bervariasi, bahkan di dalam jaringan yang sama. Salah satu implementasi dari VLSM adalah classless VLSM. Berbeda dengan konsep klasifikasi jaringan tradisional (Classful), yang membagi alamat IP menjadi kelas A, B, atau C dengan panjang subnet yang tetap, classless VLSM memungkinkan kita untuk mengalokasikan subnet dengan panjang yang sesuai dengan kebutuhan spesifik di dalam jaringan.

Keuntungan dari penggunaan VLSM melibatkan efisiensi penggunaan alamat IP, yang dapat mengurangi pemborosan sumber daya. Hal ini terutama penting dalam lingkungan jaringan yang besar atau yang memiliki lokasi-lokasi dengan jumlah perangkat yang sangat berbeda. Selain itu, VLSM memberikan fleksibilitas dalam desain jaringan, memungkinkan administrator untuk merancang jaringan yang lebih efisien dan mudah dielola sesuai dengan kebutuhan organisasi.

### Tree

![A06 - Modul 4 - Tree GNS](https://github.com/bilaaripa/Jarkom-Modul-4-A06-2023/assets/114417418/3a24ec72-85ed-4b8a-9345-fb6067a09c14)

### Pembagian IP

![Screenshot 2023-12-04 020932](https://github.com/bilaaripa/Jarkom-Modul-4-A06-2023/assets/114417418/7163c7cf-dde0-4079-a87b-c976484effd2)

### Konfigurasi Network
##### Atur Konfigurasi pada Router
- Aura
```
auto eth0
iface eth0 inet dhcp
up iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE -s 10.2.0.0/19

auto eth1
iface eth1 inet static
	address 10.2.24.113
	netmask 255.255.255.252

auto eth2
iface eth2 inet static
	address 10.2.24.133
	netmask 255.255.255.252

auto eth3
iface eth3 inet static
	address 10.2.24.129
	netmask 255.255.255.252
```
- Frieren
```
auto eth0
iface eth0 inet static
	address 10.2.24.114
	netmask 255.255.255.252
	gateway 10.2.24.113
	up echo nameserver 192.122.168.1 > /etc/resolv.conf

auto eth1
iface eth1 inet static
	address 10.2.24.65
	netmask 255.255.255.224

auto eth2
iface eth2 inet static
	address 10.2.24.117
	netmask 255.255.255.252
```
- Flamme
```
auto eth0
iface eth0 inet static
	address 10.2.24.118
	netmask 255.255.255.252
	gateway 10.2.24.117
	up echo nameserver 192.122.168.1 > /etc/resolv.conf

auto eth1
iface eth1 inet static
	address 10.2.24.121
	netmask 255.255.255.252

auto eth2
iface eth2 inet static
	address 10.2.8.1
	netmask 255.255.252.0

auto eth3
iface eth3 inet static
	address 10.2.24.125
	netmask 255.255.255.252
```
- Fern
```
auto eth0
iface eth0 inet static
	address 10.2.24.122
	netmask 255.255.255.252
	gateway 10.2.24.121
	up echo nameserver 192.122.168.1 > /etc/resolv.conf

auto eth1
iface eth1 inet static
	address 10.2.0.1
	netmask 255.255.248.0
```
- Himmel
```
auto eth0
iface eth0 inet static
	address 10.2.24.126
	netmask 255.255.255.252
	gateway 10.2.24.125
	up echo nameserver 192.122.168.1 > /etc/resolv.conf

auto eth1
iface eth1 inet static
	address 10.2.24.97
	netmask 255.255.255.248
```
- Eisen
```
auto eth0
iface eth0 inet static
	address 10.2.24.134
	netmask 255.255.255.252
	gateway 10.2.24.133
	up echo nameserver 192.122.168.1 > /etc/resolv.conf

auto eth1
iface eth1 inet static
	address 10.2.24.105
	netmask 255.255.255.248

auto eth2
iface eth2 inet static
	address 10.2.24.137
	netmask 255.255.255.252

auto eth3
iface eth3 inet static
	address 10.2.24.145
	netmask 255.255.255.252

auto eth4
iface eth4 inet static
	address 10.2.24.149
	netmask 255.255.255.252

```
- Linie
```
auto eth0
iface eth0 inet static
	address 10.2.24.138
	netmask 255.255.255.252
	gateway 10.2.24.137
	up echo nameserver 192.122.168.1 > /etc/resolv.conf

auto eth1
iface eth1 inet static
	address 10.2.24.141
	netmask 255.255.255.252

auto eth2
iface eth2 inet static
	address 10.2.20.1
	netmask 255.255.254.0
```
- Lawine
```
auto eth0
iface eth0 inet static
	address 10.2.24.142
	netmask 255.255.255.252
	gateway 10.2.24.141
	up echo nameserver 192.122.168.1 > /etc/resolv.conf

auto eth1
iface eth1 inet static
	address 10.2.24.1
	netmask 255.255.255.192
```
- Heiter
```
auto eth0
iface eth0 inet static
	address 10.2.24.2
	netmask 255.255.255.192
	gateway 10.2.24.1
	up echo nameserver 192.122.168.1 > /etc/resolv.conf

auto eth1
iface eth1 inet static
	address 10.2.12.1
	netmask 255.255.252.0
```
- Lugner
```
auto eth0
iface eth0 inet static
	address 10.2.24.146
	netmask 255.255.255.252
	gateway 10.2.24.145
	up echo nameserver 192.122.168.1 > /etc/resolv.conf

auto eth1
iface eth1 inet static
	address 10.2.16.1
	netmask 255.255.252.0

auto eth2
iface eth2 inet static
	address 10.2.23.1
	netmask 255.255.255.0
```
- Danken
```
auto eth0
iface eth0 inet static
	address 10.2.24.130
	netmask 255.255.255.252
	gateway 10.2.24.129
	up echo nameserver 192.122.168.1 > /etc/resolv.conf

auto eth1
iface eth1 inet static
	address 10.2.22.1
	netmask 255.255.255.0
```
##### Atur Konfigurasi pada Client
- LakeKoridor
```
auto eth0
iface eth0 inet static
	address 10.2.24.66
	netmask 255.255.255.224
	gateway 10.2.24.65
	up echo nameserver 192.122.168.1 > /etc/resolv.conf
```
- LaubHills
```
auto eth0
iface eth0 inet static
	address 10.2.0.2
	netmask 255.255.248.0
	gateway 10.2.0.1
	up echo nameserver 192.122.168.1 > /etc/resolv.conf
```
- ApetitRegion
```
auto eth0
iface eth0 inet static
	address 10.2.0.3
	netmask 255.255.248.0
	gateway 10.2.0.1
	up echo nameserver 192.122.168.1 > /etc/resolv.conf
```
- RohrRoad
```
auto eth0
iface eth0 inet static
	address 10.2.8.2
	netmask 255.255.252.0
	gateway 10.2.8.1
	up echo nameserver 192.122.168.1 > /etc/resolv.conf
```
- SchwerMountains
```
auto eth0
iface eth0 inet static
	address 10.2.24.98
	netmask 255.255.255.248
	gateway 10.2.24.97
	up echo nameserver 192.122.168.1 > /etc/resolv.conf
```
- Richter
```
auto eth0
iface eth0 inet static
	address 10.2.24.106
	netmask 255.255.255.248
	gateway 10.2.24.105
	up echo nameserver 192.122.168.1 > /etc/resolv.conf
```
- Revolte
```
auto eth0
iface eth0 inet static
	address 10.2.24.110
	netmask 255.255.255.248
	gateway 10.2.24.105
	up echo nameserver 192.122.168.1 > /etc/resolv.conf
```
- BredRegion
```
auto eth0
iface eth0 inet static
	address 10.2.24.2
	netmask 255.255.255.192
	gateway 10.2.24.1
	up echo nameserver 192.122.168.1 > /etc/resolv.conf
```
- Sein
```
auto eth0
iface eth0 inet static
	address 10.2.12.2
	netmask 255.255.252.0
	gateway 10.2.12.1
	up echo nameserver 192.122.168.1 > /etc/resolv.conf
```
- Reigel Canyon
```
auto eth0
iface eth0 inet static
	address 10.2.12.2
	netmask 255.255.252.0
	gateway 10.2.12.1
	up echo nameserver 192.122.168.1 > /etc/resolv.conf
```
- Granz Channel
```
auto eth0
iface eth0 inet static
	address 10.2.20.2
	netmask 255.255.254.0
	gateway 10.2.20.1
	up echo nameserver 192.122.168.1 > /etc/resolv.conf
```
- GrobeForest
```
auto eth0
iface eth0 inet static
	address 10.2.23.2
	netmask 255.255.255.0
	gateway 10.2.23.1
	up echo nameserver 192.122.168.1 > /etc/resolv.conf
```
- TurkRegion
```
auto eth0
iface eth0 inet static
	address 10.2.16.2
	netmask 255.255.252.0
	gateway 10.2.16.1
	up echo nameserver 192.122.168.1 > /etc/resolv.conf
```
- Stark
```
auto eth0
iface eth0 inet static
	address 10.2.24.150
	netmask 255.255.255.252
	gateway 10.2.24.149
	up echo nameserver 192.122.168.1 > /etc/resolv.conf
```
- WileRegion
```
auto eth0
iface eth0 inet static
	address 10.2.22.3
	netmask 255.255.255.252
	gateway 10.2.22.1
	up echo nameserver 192.122.168.1 > /etc/resolv.conf
```
- Royal Capital
```
auto eth0
iface eth0 inet static
	address 10.2.22.2
	netmask 255.255.255.252
	gateway 10.2.22.1
	up echo nameserver 192.122.168.1 > /etc/resolv.conf
```
### Routing
- Aura
```
#Kanan
route add -net 10.2.24.64 netmask 255.255.255.224 gw 10.2.24.114
route add -net 10.2.24.116 netmask 255.255.255.252 gw 10.2.24.114
route add -net 10.2.24.120 netmask 255.255.255.252 gw 10.2.24.114
route add -net 10.2.0.0 netmask 255.255.248.0 gw 10.2.24.114
route add -net 10.2.8.0 netmask 255.255.252.0 gw 10.2.24.114
route add -net 10.2.24.124 netmask 255.255.255.252 gw 10.2.24.114
route add -net 10.2.24.96 netmask 255.255.255.248 gw 10.2.24.114

#Kiri
route add -net 10.2.22.0 netmask 255.255.255.0 gw 10.2.24.130

#Bawah
route add -net 10.2.24.104 netmask 255.255.255.248 gw 10.2.24.134
route add -net 10.2.24.136 netmask 255.255.255.252 gw 10.2.24.134
route add -net 10.2.24.140 netmask 255.255.255.252 gw 10.2.24.134
route add -net 10.2.24.0 netmask 255.255.255.192 gw 10.2.24.134
route add -net 10.2.12.0 netmask 255.255.252.0 gw 10.2.24.134
route add -net 10.2.20.0 netmask 255.255.254.0 gw 10.2.24.134
route add -net 10.2.24.144 netmask 255.255.255.252 gw 10.2.24.134
route add -net 10.2.23.0 netmask 255.255.255.0 gw 10.2.24.134
route add -net 10.2.16.0 netmask 255.255.252.0 gw 10.2.24.134
route add -net 10.2.24.148 netmask 255.255.255.252 gw 10.2.24.134

```
- Frieren
```
route add -net 10.2.24.120 netmask 255.255.255.252 gw 10.2.24.118
route add -net 10.2.0.0 netmask 255.255.248.0 gw 10.2.24.118
route add -net 10.2.8.0 netmask 255.255.252.0 gw 10.2.24.118
route add -net 10.2.24.124 netmask 255.255.255.252 gw 10.2.24.118
route add -net 10.2.24.96 netmask 255.255.255.248 gw 10.2.24.118
```
- Flamme
```
route add -net 10.2.24.96 netmask 255.255.255.248 gw 10.2.24.126
route add -net 10.2.0.0 netmask 255.255.248.0 gw 10.2.24.122
```
- Eisen
```
route add -net 10.2.24.140 netmask 255.255.255.252 gw 10.2.24.138
route add -net 10.2.24.0 netmask 255.255.255.192 gw 10.2.24.138
route add -net 10.2.12.0 netmask 255.255.252.0 gw 10.2.24.138
route add -net 10.2.20.0 netmask 255.255.254.0 gw 10.2.24.138

route add -net 10.2.23.0 netmask 255.255.255.0 gw 10.2.24.146
route add -net 10.2.16.0 netmask 255.255.252.0 gw 10.2.24.146
```
- Linie
```
route add -net 10.2.24.0 netmask 255.255.255.192 gw 10.2.24.142
route add -net 10.2.12.0 netmask 255.255.252.0 gw 10.2.24.142
```
- Lawine
```
route add -net 10.2.12.0 netmask 255.255.252.0 gw 10.2.24.2
```
### Testing
Untuk melakukan testing kita perlu mengecek pada client dengan mengetikkan command
```
ping google.com -c 5
```
- Testing LakeKoridor

![lakekoridor](https://github.com/bilaaripa/Jarkom-Modul-4-A06-2023/assets/114417418/f8880bc1-6a3d-4210-a718-351084119461)

- Testing LaubHills

![laubhills](https://github.com/bilaaripa/Jarkom-Modul-4-A06-2023/assets/114417418/71005f12-c4ec-4329-bf98-9b08065abdcc)

- Testing ApetitRegion

![apetit](https://github.com/bilaaripa/Jarkom-Modul-4-A06-2023/assets/114417418/194b8a35-a3f1-473f-82b6-8f4dea5147cd)

- Testing RohrRoad

![rohr](https://github.com/bilaaripa/Jarkom-Modul-4-A06-2023/assets/114417418/4732e2b5-3a41-4b0a-9b1a-ae16fde4634d)

- Testing SchwerMountains

![schwer](https://github.com/bilaaripa/Jarkom-Modul-4-A06-2023/assets/114417418/101d61c4-6f0c-4c56-8a61-8f93b3d3a6d5)

- Testing Revolte

![revolte](https://github.com/bilaaripa/Jarkom-Modul-4-A06-2023/assets/114417418/1be2729f-bb8f-4a04-8e80-15a33c5a8f85)

- Testing BredRegion

![bred](https://github.com/bilaaripa/Jarkom-Modul-4-A06-2023/assets/114417418/1ac6030e-d7b5-446f-8cea-ec7645fd6818)

- Testing Sein

![sein](https://github.com/bilaaripa/Jarkom-Modul-4-A06-2023/assets/114417418/1ad0a380-7802-45b6-b808-be38a6d92403)

- Testing ReigelCanyon

![reigel](https://github.com/bilaaripa/Jarkom-Modul-4-A06-2023/assets/114417418/b26ae199-2a37-4893-a337-aa19c63044e3)

- Testing GranzChannel

![granz](https://github.com/bilaaripa/Jarkom-Modul-4-A06-2023/assets/114417418/1c72589a-a2fd-401f-b3a5-05868f820a8a)

- Testing GrobeForest

![grobe](https://github.com/bilaaripa/Jarkom-Modul-4-A06-2023/assets/114417418/8e968a46-6a4f-4281-9ac6-a11d22098249)

- Testing TurkRegion

![turk](https://github.com/bilaaripa/Jarkom-Modul-4-A06-2023/assets/114417418/cdf85683-0946-48ce-a909-9026137dad73)

- Testing Stark

![stark](https://github.com/bilaaripa/Jarkom-Modul-4-A06-2023/assets/114417418/b5feaf7d-f777-40fc-a332-6443c07c117a)

- Testing WileRegion

![wile](https://github.com/bilaaripa/Jarkom-Modul-4-A06-2023/assets/114417418/cef923fc-2022-459e-8f04-c8125ff9842b)

- Testing Royal Capital

![royal](https://github.com/bilaaripa/Jarkom-Modul-4-A06-2023/assets/114417418/5e4a9ed8-a921-4d21-8ea8-3eda3c2823ca)


## CIDR
CIDR (Classless Inter-Domain Routing) adalah metode pengalamatan IP yang memungkinkan pengguna untuk mengelompokkan alamat IP ke dalam blok yang lebih besar atau lebih kecil daripada pembagian tradisional berdasarkan kelas (Classful addressing). Dalam CIDR, subnetting dapat dilakukan dengan fleksibilitas tanpa harus tunduk pada batasan kelas A, B, atau C yang konvensional, sehingga memungkinan alokasi alamat IP yang lebih optimal. Notasi CIDR menggunakan format "IP address/prefix length," di mana "prefix length" menentukan jumlah bit yang digunakan untuk mengidentifikasi jaringan, sehingga dapat terbentuk blok-blok alamat dengan panjang yang bervariasi. Dengan demikian, CIDR memberikan solusi untuk permasalahan kehabisan alamat IPv4 dengan memungkinkan penggunaan sumber daya alamat IP yang terbatas dengan lebih efisien dan fleksibel.</br>

Kelebihan dari penerapan CIDR mencakup efisiensi penggunaan alamat IP dan pengurangan pemborosan. Dalam konteks CIDR, tidak perlu lagi mengalokasikan blok alamat IP dengan ukuran yang terikat pada kelas-kelas tertentu. Tidak hanya itu, CIDR juga memberikan dukungan untuk agregasi rute, sebuah aspek yang memfasilitasi penyederhanaan tabel routing di ruang Internet. Melalui penggabungan beberapa blok alamat IP menjadi satu entri routing, CIDR berperan dalam mengurangi kompleksitas tabel routing dan secara efektif meningkatkan kinerja pengelolaan lalu lintas pada tingkat global dalam jaringan.</br>

### Penggabungan IP
#### Tampilan Node Awal (A)

Pertama untuk rute yang kelompok kami gunakan adalah sebagai berikut : </br>

<img width="1000" alt="rute" src="https://github.com/bilaaripa/Jarkom-Modul-4-A06-2023/assets/91377793/71272246-dd28-4612-8f74-2157556fbafb"></br>

<img width="1000" alt="A" src="https://github.com/bilaaripa/Jarkom-Modul-4-A06-2023/assets/91377793/41b90bee-7e87-4a4b-83da-e31fbd94094a"></br>

#### Penggabungan Node Ke-1 (B)

<img width="1000" alt="B" src="https://github.com/bilaaripa/Jarkom-Modul-4-A06-2023/assets/91377793/7239b256-5784-43df-bba5-50ee3bc870d7"></br>

<img width="1000" alt="RB" src="https://github.com/bilaaripa/Jarkom-Modul-4-A06-2023/assets/91377793/b4bef109-37cd-4173-9ca6-61e03523d446"></br>

#### Penggabungan Node Ke-2 (C)

<img width="1000" alt="C" src="https://github.com/bilaaripa/Jarkom-Modul-4-A06-2023/assets/91377793/57556b6c-2e51-4864-963f-8e95bdd40f69"></br>

<img width="1000" alt="RC" src="https://github.com/bilaaripa/Jarkom-Modul-4-A06-2023/assets/91377793/18c58dcd-1edb-40f8-9862-4fcf623b1af8"></br>

#### Penggabungan Node Ke-3 (D)

<img width="1000" alt="D" src="https://github.com/bilaaripa/Jarkom-Modul-4-A06-2023/assets/91377793/305ec0a6-b939-4c63-8abf-96d48cea67f6"></br>

<img width="1000" alt="RD" src="https://github.com/bilaaripa/Jarkom-Modul-4-A06-2023/assets/91377793/a3ae1c63-795e-4d45-9955-4f4d869a2327"></br>

#### Penggabungan Node Ke-4 (E)

<img width="1000" alt="E" src="https://github.com/bilaaripa/Jarkom-Modul-4-A06-2023/assets/91377793/f9a9d11d-f328-4e2c-a77a-b0ff75218c0b"></br>

<img width="1000" alt="RE" src="https://github.com/bilaaripa/Jarkom-Modul-4-A06-2023/assets/91377793/d3ff6723-ae1d-4d22-9ea0-f5a156f180cb"></br>

#### Penggabungan Node Ke-5 (F)

<img width="1000" alt="F" src="https://github.com/bilaaripa/Jarkom-Modul-4-A06-2023/assets/91377793/fb6876c9-cf16-4fb6-8b36-5c964612d397"></br>

<img width="1000" alt="RF" src="https://github.com/bilaaripa/Jarkom-Modul-4-A06-2023/assets/91377793/345a9549-93f1-4d78-9e90-10a4e048c4d3"></br>

#### Penggabungan Node Ke-6 (G)

<img width="1000" alt="G" src="https://github.com/bilaaripa/Jarkom-Modul-4-A06-2023/assets/91377793/e8b4e0d5-c46a-4d2b-a24d-dcc8a56c6aa2"></br>

<img width="1000" alt="RG" src="https://github.com/bilaaripa/Jarkom-Modul-4-A06-2023/assets/91377793/6acd1eff-3c55-4d06-a157-9dabcebf6baa"></br>

#### Penggabungan Node Ke-7 (H)

<img width="1000" alt="H" src="https://github.com/bilaaripa/Jarkom-Modul-4-A06-2023/assets/91377793/884c0c8f-6ffb-4b18-8198-62357da73071"></br>

<img width="1000" alt="RH" src="https://github.com/bilaaripa/Jarkom-Modul-4-A06-2023/assets/91377793/44b9f058-ef95-46fd-aaa3-d5af15197ae9"></br>

#### Penggabungan Node Ke-8 (I)

<img width="1000" alt="I" src="https://github.com/bilaaripa/Jarkom-Modul-4-A06-2023/assets/91377793/b4029183-1741-4d17-8cd7-bc8f43e948c0"></br>

<img width="1000" alt="RI" src="https://github.com/bilaaripa/Jarkom-Modul-4-A06-2023/assets/91377793/e8c5a10d-cbf1-46ea-9c2a-99f77684d674"></br>

#### Penggabungan Node Ke-9 (J)

<img width="1000" alt="J" src="https://github.com/bilaaripa/Jarkom-Modul-4-A06-2023/assets/91377793/3bf81792-fbde-417a-b552-e05c429c88ae"></br>

<img width="1000" alt="RJ" src="https://github.com/bilaaripa/Jarkom-Modul-4-A06-2023/assets/91377793/1bea04c1-fea3-495c-8c5e-4ca73f0e4c73"></br>

#### Penggabungan Node Ke-10 (K)

<img width="1000" alt="K" src="https://github.com/bilaaripa/Jarkom-Modul-4-A06-2023/assets/91377793/ae58b7c1-9601-427f-86d3-3c7764ff664a"></br>

<img width="1000" alt="RK" src="https://github.com/bilaaripa/Jarkom-Modul-4-A06-2023/assets/91377793/d56d789f-68cb-4f2f-a307-e83bc31eaf74"></br>

### Tree

Setelah menggabungkan alamat IP, kemudian dilakukan pembagian IP dengan memanfaatkan Tree pada setiap kelompok yang sebelumnya telah dibentuk sebagai berikut :</br>

![A06 - Modul 4 - Tree CPT](https://github.com/bilaaripa/Jarkom-Modul-4-A06-2023/assets/91377793/18b3e878-ad11-4b8a-8628-ea8a8b7b5e71)

### Pembagian IP

Pembagian IP berdasarkan Tree yang telah dibuat adalah sebagai berikut :</br>

<img width="1000" alt="pembagian ip" src="https://github.com/bilaaripa/Jarkom-Modul-4-A06-2023/assets/91377793/debfa1dd-7114-4038-83e3-b8b1ad787c2f"></br>

