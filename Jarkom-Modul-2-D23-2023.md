# Laporan Resmi Praktikum Jarkom Modul 2

![Lambang ITS](https://www.its.ac.id/wp-content/uploads/2020/07/Lambang-ITS-2-320x320.png)

Kelompok D23 :

- Ligar Arsa Arnata (5025211244)
- Alfadito Aulia Denova (5025211157)

## Daftar Isi

- [Laporan Resmi Praktikum Jarkom Modul 2](#laporan-resmi-praktikum-jarkom-modul-2)
  - [Daftar Isi](#daftar-isi)
  - [Soal Nomor 1](#soal-nomor-1)
  - [Jawaban Nomor 1](#jawaban-nomor-1)
    - [Setup Topologi](#setup-topologi)
    - [Konfigurasi Node](#konfigurasi-node)
    - [Checking Koneksi Node](#checking-koneksi-node)
  - [Soal Nomor 2](#soal-nomor-2)
  - [Jawaban Nomor 2](#jawaban-nomor-2)
    - [Setup Domain DNS Master](#setup-domain-dns-master-2)
    - [Setup Domain Node Arjuna](#setup-domain-node-arjuna)
    - [Checking Domain Arjuna](#checking-domain-arjuna)
  - [Soal Nomor 3](#soal-nomor-3)
  - [Jawaban Nomor 3](#jawaban-nomor-3)
    - [Setup Domain DNS Master](#setup-domain-dns-master-3)
    - [Setup Domain Node Abimanyu](#setup-domain-node-abimanyu)
    - [Checking Domain Abimanyu](#checking-domain-abimanyu)
  - [Soal Nomor 4](#soal-nomor-4)
  - [Jawaban Nomor 4](#jawaban-nomor-4)
    - [Penambahan Konfigurasi DNS Master](#penambahan-konfigurasi-dns-master-4)
  - [Soal Nomor 5](#soal-nomor-5)
  - [Jawaban Nomor 5](#jawaban-nomor-5)
    - [Penambahan Konfigurasi DNS Master](#penambahan-konfigurasi-dns-master-5)
  - [Soal Nomor 6](#soal-nomor-6)
  - [Jawaban Nomor 6](#jawaban-nomor-6)
    - [Penambahan Konfigurasi DNS Master](#penambahan-konfigurasi-dns-master-6)
    - [Setup DNS Slave](#setup-dns-slave)
    - [Checking DNS Slave](#checking-dns-slave)
  - [Soal Nomor 7](#soal-nomor-7)
  - [Jawaban Nomor 7](#jawaban-nomor-7)
    - [Penambahan Konfigurasi DNS Master](#penambahan-konfigurasi-dns-master-7)
    - [Penambahan Konfigurasi DNS Slave](#penambahan-konfigurasi-dns-slave-7)
  - [Soal Nomor 8](#soal-nomor-8)
  - [Jawaban Nomor 8](#jawaban-nomor-8)
    - [Penambahan Konfigurasi DNS Slave](#penambahan-konfigurasi-dns-slave-8)


## Soal Nomor 1

Yudhistira akan digunakan sebagai DNS Master, Werkudara sebagai DNS Slave, Arjuna merupakan Load Balancer yang terdiri dari beberapa Web Server yaitu Prabakusuma, Abimanyu, dan Wisanggeni. Buatlah topologinya.

## Jawaban Nomor 1

### Setup Topologi

Pada pembagian topologi, kelompok kami mendapat topologi nomor 4 sehingga susunan dari tiap node nya adalah sebagai berikut



### Konfigurasi Node

Setelah membuat topologi, kami melakukan editing pada network configuration dengan menggunakan `Prefix IP : 10.33` untuk setiap nodenya sesuai dengan settingan seperti dibawah 

- Pandudewanata
```
auto eth0
iface eth0 inet dhcp

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
```
  
- Werkudara
```
auto eth0
iface eth0 inet static
	address 10.33.1.2
	netmask 255.255.255.0
	gateway 10.33.1.1
```

- Yudhistira
```
auto eth0
iface eth0 inet static
	address 10.33.1.3
	netmask 255.255.255.0
	gateway 10.33.1.1
```

- Nakula
```
auto eth0
iface eth0 inet static
	address 10.33.2.2
	netmask 255.255.255.0
	gateway 10.33.2.1
```

- Sadewa
```
auto eth0
iface eth0 inet static
	address 10.33.2.3
	netmask 255.255.255.0
	gateway 10.33.2.1
```

- Abimanyu
```
auto eth0
iface eth0 inet static
	address 10.33.3.2
	netmask 255.255.255.0
	gateway 10.33.3.1
```

- Prabukusuma
```
auto eth0
iface eth0 inet static
	address 10.33.3.3
	netmask 255.255.255.0
	gateway 10.33.3.1
```

- Wisanggeni
```
auto eth0
iface eth0 inet static
	address 10.33.3.4
	netmask 255.255.255.0
	gateway 10.33.3.1
```

- Arjuna
```
auto eth0
iface eth0 inet static
	address 10.33.3.5
	netmask 255.255.255.0
	gateway 10.33.3.1
```











  
