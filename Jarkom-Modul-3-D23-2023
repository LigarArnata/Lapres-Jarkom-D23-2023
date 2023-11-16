# Laporan Resmi Praktikum Jarkom Modul 3

![Lambang ITS](https://www.its.ac.id/wp-content/uploads/2020/07/Lambang-ITS-2-320x320.png)

Kelompok D23 :

- Ligar Arsa Arnata (5025211244)
- Alfadito Aulia Denova (5025211157)

## Daftar Isi

- [Laporan Resmi Praktikum Jarkom Modul 3](#laporan-resmi-praktikum-jarkom-modul-3)
  - [Topologi](#topologi)
  - [Soal Nomor 1](#soal-nomor-1)
  - [Jawaban Nomor 1](#jawaban-nomor-1)
    - [Network Configuration](#network-configuration)
    - [Script DNS Server](#script-dns-server)
  - [Soal Nomor 2](#soal-nomor-2)
  - [Jawaban Nomor 2](#jawaban-nomor-2)
    - [Script IP Range melalui Switch 3](#script-ip-switch-3)
  - [Soal Nomor 3](#soal-nomor-3)
  - [Jawaban Nomor 3](#jawaban-nomor-3)
    - [Script IP Range melalui Switch 4](#script-ip-switch-4)
  - [Soal Nomor 4](#soal-nomor-4)
  - [Jawaban Nomor 4](#jawaban-nomor-4)
    - [Script Koneksi Client dan DNS Server](#script-koneksi-client-dan-dns-server)
  - [Soal Nomor 5](#soal-nomor-5)
  - [Jawaban Nomor 5](#jawaban-nomor-5)
    - [Script Update Lease Time](#script-update-lease-time)


## Topologi




## Soal Nomor 1

Lakukan Konfigurasi sesuai dengan peta yang diberikan

## Jawaban Nomor 1

### Network Configuration

Setelah membuat topologi yang sesuai, kami melakukan editing pada network configuration dengan menggunakan `Prefix IP : 10.33` untuk setiap nodenya sesuai dengan settingan seperti berikut

- Node Aura (DHCP Relay)
```
auto eth0
iface eth0 inet dhcp
up iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE -s 10.33.0.0/16

auto eth1
iface eth1 inet static
	address 10.33.1.1
	netmask 255.255.255.0

auto eth2
iface eth2 inet static
	address 10.33.2.1
	netmask 255.255.255.0

auto eth3
iface eth3 inet static
	address 10.33.3.1
		netmask 255.255.255.0

auto eth4
iface eth4 inet static
	address 10.33.4.1
		netmask 255.255.255.0
```

- Node Denken (DB dan Laravel)
```
auto eth0
iface eth0 inet static
	address 10.33.2.2
	netmask 255.255.255.0
	gateway 10.33.2.1
	up echo nameserver 192.168.122.1 > /etc/resolv.conf
```

- Node Eisen (Load Balancer)
```
auto eth0
iface eth0 inet static
	address 10.33.2.3
	netmask 255.255.255.0
	gateway 10.33.2.1
	up echo nameserver 192.168.122.1 > /etc/resolv.conf
```

- Node Frieren (Laravel Worker)
```
auto eth0
iface eth0 inet static
	address 10.33.4.4
	netmask 255.255.255.0
	gateway 10.33.4.1
	up echo nameserver 192.168.122.1 > /etc/resolv.conf
```

- Node Flame (Laravel Worker)
```
auto eth0
iface eth0 inet static
	address 10.33.4.5
	netmask 255.255.255.0
	gateway 10.33.4.1
	up echo nameserver 192.168.122.1 > /etc/resolv.conf
```

- Node Fern (Laravel Worker)
```
auto eth0
iface eth0 inet static
	address 10.33.4.6
	netmask 255.255.255.0
	gateway 10.33.4.1
	up echo nameserver 192.168.122.1 > /etc/resolv.conf
```

- Node Himmel (DHCP Server)
```
auto eth0
iface eth0 inet static
	address 10.33.1.2
	netmask 255.255.255.0
	gateway 10.33.1.1
  up echo nameserver 192.168.122.1 > /etc/resolv.conf
```

- Node Heiter (DNS Server)
```
auto eth0
iface eth0 inet static
	address 10.33.1.3
	netmask 255.255.255.0
	gateway 10.33.1.1
	up echo nameserver 192.168.122.1 > /etc/resolv.conf
```

- Node Lawine (PHP Worker)
```
auto eth0
iface eth0 inet static
	address 10.33.3.3
	netmask 255.255.255.0
	gateway 10.33.3.1
  up echo nameserver 192.168.122.1 > /etc/resolv.conf
```

- Node Linnie (PHP Worker)
```
auto eth0
iface eth0 inet static
	address 10.33.3.4
	netmask 255.255.255.0
	gateway 10.33.3.1
  up echo nameserver 192.168.122.1 > /etc/resolv.conf
```

- Node Lugner (PHP Worker)
```
auto eth0
iface eth0 inet static
	address 10.33.3.5
	netmask 255.255.255.0
	gateway 10.33.3.1
  up echo nameserver 192.168.122.1 > /etc/resolv.conf
```

- Node Revolte (Client)
```
auto eth0
iface eth0 inet dhcp
```

- Node Ritcher (Client)
```
auto eth0
iface eth0 inet dhcp
```

- Node Sein (Client)
```
auto eth0
iface eth0 inet dhcp
```

- Node Stark (Client)
```
auto eth0
iface eth0 inet dhcp
```














