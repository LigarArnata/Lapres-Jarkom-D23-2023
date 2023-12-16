# Laporan Resmi Praktikum Jarkom Modul 5

![Lambang ITS](https://www.its.ac.id/wp-content/uploads/2020/07/Lambang-ITS-2-320x320.png)

Kelompok D23 :

- Ligar Arsa Arnata (5025211244)
- Alfadito Aulia Denova (5025211157)

## Daftar Isi

- [Laporan Resmi Praktikum Jarkom Modul 5](#laporan-resmi-praktikum-jarkom-modul-5)
  - [Daftar Isi](#daftar-isi)
  - [Topologi](#topologi)
  - [Prefix IP](#prefix-ip)
  - [Rute](#rute)
  - [Pembagian IP dan Subnetting](#pembagian-ip-dan-subnetting)
  - [Routing](#routing)
  - [Konfigurasi](#konfigurasi)
    - [DNS Server](#dns-server)
    - [DHCP Server](#dhcp-server)
    - [DHCP Relay](#dhcp-relay)
    - [Web Server](#web-server)
    - [Client](#client)
  - [Soal Nomor 1](#soal-nomor-1)
  - [Jawaban Nomor 1](#jawaban-no-1)
    - [Script](#script)
  - [Soal Nomor 1](#soal-nomor-1)
  - [Jawaban Nomor 2](#jawaban-no-2)
    - [Script](#script-1)
  - [Soal Nomor 3](#soal-nomor-3)
  - [Jawaban Nomor 3](#jawaban-no-3)
    - [Script](#script-2)
  - [Soal Nomor 4](#soal-nomor-4)
  - [Jawaban Nomor 4](#jawaban-no-4)
    - [Script](#script-3)
  - [Soal Nomor 5](#soal-nomor-5)
  - [Jawaban Nomor 5](#jawaban-no-5)
    

## Topologi

Berikut merupakan topologi yang kami buat berdasarkan soal

![topologi]()

## Prefix IP

Pada pembagian IP, kelompok kami akan menggunakan Prefix IP `10.33` sesuai dengan pembagian pada modul sebelumnya

## Rute

Berikut merupakan topologi yang sudah kami bagi berdasarkan subnetnya

![subnet]()

Setelah membagi topologi tersebut menjadi beberapa subnet, berikut merupakan rute yang didapatkan beserta dengan jumlah host yang harus disediakan

![rute]()

## Pembagian IP dan Subnetting

Berdasarkan rute diatas, berikut adalah pembagian IP yang kami lakukan menggunakan metode **VLSM**

![vlsm]()

Setelah pembagian IP, berikut merupakan subnetting berdasarkan IP yang sudah ditetapkan

**Aura**
```
auto eth0
iface eth0 inet dhcp

#Subnet 2
auto eth1
iface eth1 inet static
address 10.33.13.133
netmask 255.255.255.252

#Subnet 5
auto eth2
iface eth2 inet static
address 10.33.13.137
netmask 255.255.255.252
```

**Heiter**
```
auto lo
iface lo inet loopback

#Subnet 2
auto eth0
iface eth0 inet static
address 10.33.13.134
netmask 255.255.255.252
gateway 10.33.13.133

#Subnet 3
auto eth1
iface eth1 inet static
address 10.33.1.1
netmask 255.255.252.0

#Subnet 4
auto eth2
iface eth2 inet static
address 10.33.4.1
netmask 255.255.252.0
```

**Frieren**
```
auto lo
iface lo inet loopback

#Subnet 5
auto eth0
iface eth0 inet static
address 10.33.13.138
netmask 255.255.255.252
gateway 10.33.13.137

#Subnet 6
auto eth2
iface eth2 inet static
address 10.33.10.1
netmask 255.255.255.0

#Subnet 7
auto eth1
iface eth1 inet static
address 10.33.13.141
netmask 255.255.255.252
```

**Himmel**
```
auto lo
iface lo inet loopback

#Subnet 7
auto eth0
iface eth0 inet static
address 10.33.13.142
netmask 255.255.255.252
gateway 10.33.13.141

#Subnet 8
auto eth1
iface eth1 inet static
address 10.33.8.1
netmask 255.255.254.0

#Subnet 9
auto eth2
iface eth2 inet static
address 10.33.13.1
netmask 255.255.255.128
```

**Fern**
```
auto lo
iface lo inet loopback

#Subnet 9
auto eth0
iface eth0 inet static
address 10.33.13.2
netmask 255.255.255.128
gateway 10.33.13.1

#Subnet 10
auto eth1
iface eth1 inet static
address 10.33.11.1
netmask 255.255.255.0

#Subnet 11
auto eth2
iface eth2 inet static
address 10.33.12.1
netmask 255.255.255.0
```

**Revolte**
```
auto eth0
iface eth0 inet static
address 10.33.12.2
netmask 255.255.255.0
gateway 10.33.12.1
```

**Ritcher**
```
auto eth0
iface eth0 inet static
address 10.33.11.2
netmask 255.255.255.0
gateway 10.33.11.1
```

**Stark**
```
auto eth0
iface eth0 inet static
address 10.33.10.2
netmask 255.255.255.0
gateway 10.33.10.1
```

**Sein**
```
auto eth0
iface eth0 inet static
address 10.33.4.2
netmask 255.255.255.0
gateway 10.33.4.1
```

**Client**
```
auto eth0
iface eth0 inet dhcp
```
 
    
