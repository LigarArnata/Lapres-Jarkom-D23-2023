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
    - [Script Penyesuaian Fungsi Node](#script-penyesuaian-fungsi-node)
  - [Soal Nomor 2](#soal-nomor-2)
  - [Jawaban Nomor 2](#jawaban-nomor-2)
    - [Script IP Range melalui Switch 3](#script-ip-switch-3)
  - [Soal Nomor 3](#soal-nomor-3)
  - [Jawaban Nomor 3](#jawaban-nomor-3)
    - [Script IP Range melalui Switch 4](#script-ip-switch-4)
  - [Soal Nomor 4](#soal-nomor-4)
  - [Jawaban Nomor 4](#jawaban-nomor-4)
    - [Script Koneksi DNS Server](#script-koneksi-dns-server)
  - [Soal Nomor 5](#soal-nomor-5)
  - [Jawaban Nomor 5](#jawaban-nomor-5)
    - [Script Update Lease Time](#script-update-lease-time)


## Topologi

![Topologi](https://cdn.discordapp.com/attachments/773324309020147732/1174850648483840020/image.png?ex=656917ee&is=6556a2ee&hm=e9232373460493749be2041098af841f1d7350543c71d6efb4cb7e4c008bf0da&)

## Soal Nomor 1

Lakukan Konfigurasi sesuai dengan peta yang diberikan

## Jawaban Nomor 1

### Network Configuration

Setelah membuat topologi yang sesuai, kami melakukan editing pada network configuration dengan menggunakan `Prefix IP : 10.33` untuk setiap nodenya sesuai dengan settingan seperti berikut

- **Node Aura (DHCP Relay)**
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

- **Node Denken (DB dan Laravel)**
```
auto eth0
iface eth0 inet static
	address 10.33.2.2
	netmask 255.255.255.0
	gateway 10.33.2.1
	up echo nameserver 192.168.122.1 > /etc/resolv.conf
```

- **Node Eisen (Load Balancer)**
```
auto eth0
iface eth0 inet static
	address 10.33.2.3
	netmask 255.255.255.0
	gateway 10.33.2.1
	up echo nameserver 192.168.122.1 > /etc/resolv.conf
```

- **Node Frieren (Laravel Worker)**
```
auto eth0
iface eth0 inet static
	address 10.33.4.4
	netmask 255.255.255.0
	gateway 10.33.4.1
	up echo nameserver 192.168.122.1 > /etc/resolv.conf
```

- **Node Flame (Laravel Worker)**
```
auto eth0
iface eth0 inet static
	address 10.33.4.5
	netmask 255.255.255.0
	gateway 10.33.4.1
	up echo nameserver 192.168.122.1 > /etc/resolv.conf
```

- **Node Fern (Laravel Worker)**
```
auto eth0
iface eth0 inet static
	address 10.33.4.6
	netmask 255.255.255.0
	gateway 10.33.4.1
	up echo nameserver 192.168.122.1 > /etc/resolv.conf
```

- **Node Himmel (DHCP Server)**
```
auto eth0
iface eth0 inet static
	address 10.33.1.2
	netmask 255.255.255.0
	gateway 10.33.1.1
  	up echo nameserver 192.168.122.1 > /etc/resolv.conf
```

- **Node Heiter (DNS Server)**
```
auto eth0
iface eth0 inet static
	address 10.33.1.3
	netmask 255.255.255.0
	gateway 10.33.1.1
	up echo nameserver 192.168.122.1 > /etc/resolv.conf
```

- **Node Lawine (PHP Worker)**
```
auto eth0
iface eth0 inet static
	address 10.33.3.3
	netmask 255.255.255.0
	gateway 10.33.3.1
  	up echo nameserver 192.168.122.1 > /etc/resolv.conf
```

- **Node Linnie (PHP Worker)**
```
auto eth0
iface eth0 inet static
	address 10.33.3.4
	netmask 255.255.255.0
	gateway 10.33.3.1
  	up echo nameserver 192.168.122.1 > /etc/resolv.conf
```

- **Node Lugner (PHP Worker)**
```
auto eth0
iface eth0 inet static
	address 10.33.3.5
	netmask 255.255.255.0
	gateway 10.33.3.1
  	up echo nameserver 192.168.122.1 > /etc/resolv.conf
```

- **Node Revolte (Client)**
```
auto eth0
iface eth0 inet dhcp
up echo nameserver 192.168.122.1 > /etc/resolv.conf
```

- **Node Ritcher (Client)**
```
auto eth0
iface eth0 inet dhcp
up echo nameserver 192.168.122.1 > /etc/resolv.conf
```

- **Node Sein (Client)**
```
auto eth0
iface eth0 inet dhcp
up echo nameserver 192.168.122.1 > /etc/resolv.conf
```

- **Node Stark (Client)**
```
auto eth0
iface eth0 inet dhcp
up echo nameserver 192.168.122.1 > /etc/resolv.conf
```

### Script Penyesuaian Fungsi Node

Karena tiap node nantinya akan memiliki fungsi yang berbeda, maka pada tiap node tersebut harus menjalankan beberapa command yang sesuai pada script berikut ini

- **Node Aura (DHCP Relay)**
```
cat /etc/resolv.conf
echo nameserver 192.168.122.1 > /etc/resolv.conf
apt-get update 
apt-get install isc-dhcp-relay -y 
service isc-dhcp-relay start
```
Kemudian lakukan konfigurasi pada `/etc/default/isc-dhcp-relay` sebagai berikut
```
SERVERS="10.33.1.2" 
INTERFACES="eth1 eth2 eth3 eth4" 
OPTIONS=
```
Setelah itu lakukan konfigurasi untuk IP Forwarding pada `/etc/sysctl.conf` sebagai berikut
```
net.ipv4.ip_forward=1
```
Kemudian Restart Service `service isc-dhcp-relay restart`

- **Node Himmel (DHCP Server)**
```
apt-get update
apt-get install isc-dhcp-server
```

- **Node Heiter (DNS Server)**
```
apt-get update
apt-get install bind9 -y
```
Kemudian buat file config baru pada `nano /etc/bind/named.conf.local` sebagai berikut
```
zone “granz.channel.d23.com” {
	type master;
	file “/etc/bind/modul-3/granz.channel.d23.com”;
};
zone “riegel.canyon.d23.com”{
	type master;
	file “/etc/bind/modul-3/riegel.canyon.d23.com”;
};
zone “1.33.10.in-addr.arpa” {
type master;
	file “/etc/bind/modul-3/1.33.10.in-addr.arpa”;
};
```
Setelah itu copy file dengan `cp named.local.txt /etc/bind/named.conf.local`, dan buat direktori baru yang diisi konfigurasi domain web yang akan digunakan
```
mkdir /etc/bind/modul-3
cp /etc/bind/db.local /etc/bind/modul-3/granz.channel.d23.com
cp /etc/bind/db.local /etc/bind/modul-3/riegel.canyon.d23.com
```
Lakukan konfigurasi untuk domain granz.channel.d23.com `nano /etc/bind/modul-3/granz.channel.d23.com` sebagai berikut
```
;
; BIND data file for local loopback interface
;
$TTL    604800
@       IN      SOA  granz.channel.d23.com. root.granz.channel.d23.com. (
			2023111501    ; Serial
                        604800        ; Refresh
                        86400         ; Retry
                        2419200       ; Expire
                        604800 )      ; Negative Cache TTL
;
@               IN      NS      granz.channel.d23.com.
@               IN      A       10.33.2.3 ; IP Eisen
www             IN      CNAME   granz.channel.d23.com
lawine         	IN      A       10.33.3.4 ; IP Lawine
linie           IN      A       10.33.3.5 ; IP Linie
lugner         	IN      A       10.33.3.6 ; IP Lugner
```
Kemudian konfigurasi untuk domain `nano /etc/bind/modul-3/riegel.canyon.d23.com` sebagai berikut
```
;
; BIND data file for local loopback interface
;
$TTL    604800
@       IN      SOA  riegel.canyon.d23.com. root.riegel.canyon.d23.com. (
		2023111501    ; Serial
                        604800        ; Refresh
                        86400         ; Retry
                        2419200       ; Expire
                        604800 )      ; Negative Cache TTL
;
@               IN      NS      riegel.canyon.d23.com.
@               IN      A       10.33.2.2 ; IP Denken
www             IN      CNAME   riegel.canyon.d23.com
```
Setelah itu tambahkan juga beberapa file config baru untuk reverse domainnya dengan script dan config sebagai berikut
```
cp bind.txt /etc/bind/modul-3/granz.channel.d23.com
cp bind2.txt /etc/bind/modul-3/riegel.canyon.d23.com
nano /etc/bind/modul-3/1.33.10.in-addr.arpa
```
```
;
; BIND data file for local loopback interface
;
$TTL    604800
@       IN      SOA  granz.channel.d23.com. root.granz.channel.d23.com. (
			2023111501    ; Serial
                        604800        ; Refresh
                        86400         ; Retry
                        2419200       ; Expire
                        604800 )      ; Negative Cache TTL
;
1.33.10.in-addr.arpa. 		IN	NS  granz.channel.d23.com.
1				IN 	PTR granz.channel.d23.com.
```
Terakhir, lakukan restart pada DNS Servernya `Service bind9 restart`

- **Node Denken (Database Server)**
```
apt-get update
apt-get install bind9 -y
apt-get install mariadb-server -y
```

- **Node Eisen (Load Balancer)**
```
apt-get update
apt-get install nginx -y
apt-get install wget -y
wget –no-check-certificate ‘https://docs.google.com/uc?export=download&id=1ViSkRq7SmwZgdK64eRbr5Fm1EGCTPrU1’ -O granz.channel.d23.com.zip
apt-get install unzip
unzip granz.channel.d23.com.zip 
cp -r modul-3/* /var/www/html/
cp def /etc/nginx/sites-available/default
apt-get install php php-fpm
```

- **Node Frieren, Flame, Fern (Laravel Worker)**
```
apt-get update
apt-get install mariadb-server -y
apt-get install -y lsb-release ca-certificates apt-transport-https software-properties-common gnupg2
curl -sSLo /usr/share/keyrings/deb.sury.org-php.gpg https://packages.sury.org/php/apt.gpg
sh -c 'echo "deb [signed-by=/usr/share/keyrings/deb.sury.org-php.gpg] https://packages.sury.org/php/ $(lsb_release -sc) main" > /etc/apt/sources.list.d/php.list'

apt-get update
apt-get install php8.0-mbstring php8.0-xml php8.0-cli php8.0-common php8.0-intl php8.0-opcache php8.0-readline php8.0-mysql php8.0-fpm php8.0-curl unzip wget -y
apt-get install nginx -y
wget https://getcomposer.org/download/2.0.13/composer.phar
chmod +x composer.phar
mv composer.phar /usr/bin/composer

apt-get install git -y

git clone https://github.com/martuafernando/laravel-praktikum-jarkom.git
cd laravel-praktikum-jarkom
composer install
```

- **Node Lawine, Linie, Lugner (PHP Worker)**
```
apt-get update
apt-get install nginx -y
apt-get install wget -y
wget –no-check-certificate ‘https://docs.google.com/uc?export=download&id=1ViSkRq7SmwZgdK64eRbr5Fm1EGCTPrU1’ -O granz.channel.d23.com.zip
apt-get install unzip
unzip granz.channel.d23.com.zip 
cp -r modul-3/* /var/www/html/
cp def /etc/nginx/sites-available/default
apt-get install php php-fpm -y
```

- **Node Revolter, Ritcher, Sein, Stark (Client)**
```
apt-get update
apt install lynx -y
apt install htop -y
apt install apache2-utils -y
apt-get install jq -y
```

## Soal Nomor 2

Client yang melalui Switch3 mendapatkan range IP dari [prefix IP].3.16 - [prefix IP].3.32 dan [prefix IP].3.64 - [prefix IP].3.80

## Jawaban Nomor 2

### Script IP Switch 3

Untuk membagi IP Range untuk client dengan ketentuan seperti pada soal, kita perlu menjalankan command berikut ini pada node Himmel sebagai DHCP Server `/etc/dhcp/dhcpd.conf` seperti berikut
```
subnet 10.33.2.0 netmask 255.255.255.0 {
}
subnet 10.33.3.0 netmask 255.255.255.0 { 
	range 10.33.3.16 10.33.3.32;
	range 10.33.3.64 10.33.3.80; 
	option routers 10.33.3.1;
}
```

## Soal Nomor 3

Client yang melalui Switch4 mendapatkan range IP dari [prefix IP].4.12 - [prefix IP].4.20 dan [prefix IP].4.160 - [prefix IP].4.168

## Jawaban Nomor 3

### Script IP Switch 4

Sama seperti soal sebelumnya, untuk membagi IP Range untuk client dengan ketentuan seperti pada soal, kita perlu menjalankan command berikut ini pada node Himmel sebagai DHCP Server `/etc/dhcp/dhcpd.conf` seperti berikut

```
subnet 10.33.2.0 netmask 255.255.255.0 {
}
subnet 10.33.3.0 netmask 255.255.255.0 { 
	range 10.33.3.16 10.33.3.32;
	range 10.33.3.64 10.33.3.80; 
	option routers 10.33.3.1;
}
subnet 10.33.4.0 netmask 255.255.255.0 { 
	range 10.33.4.12 10.33.4.20;
	range 10.33.4.160 10.33.4.168; 
	option routers 10.33.3.1;
}
```

## Soal Nomor 4

Client mendapatkan DNS dari Heiter dan dapat terhubung dengan internet melalui DNS tersebut

## Jawaban Nomor 4

### Script Koneksi DNS Server

Agar Client dapat terhubung dengan internet melalui DNS dari node Heiter, maka diperlukan tambahan konfigurasi pada `option broadcast-address` yang berisikan IP broadcast pada subnet dan juga `option domain-name-server` yang berisikan IP DNS yang ingin kita berikan kepada client

```
subnet 10.33.2.0 netmask 255.255.255.0 {
}
subnet 10.33.3.0 netmask 255.255.255.0 { 
	range 10.33.3.16 10.33.3.32;
	range 10.33.3.64 10.33.3.80; 
	option routers 10.33.3.1;
	option broadcast-address 10.33.3.255; 
	option domain-name-servers 10.33.1.3; 
}
subnet 10.33.4.0 netmask 255.255.255.0 { 
	range 10.33.4.12 10.33.4.20;
	range 10.33.4.160 10.33.4.168; 
	option routers 10.33.3.1;
	option broadcast-address 10.33.4.255; 
	option domain-name-servers 10.33.1.3;
}
```

## Soal Nomor 5

Lama waktu DHCP server meminjamkan alamat IP kepada Client yang melalui Switch3 selama 3 menit sedangkan pada client yang melalui Switch4 selama 12 menit. Dengan waktu maksimal dialokasikan untuk peminjaman alamat IP selama 96 menit

## Jawaban Nomor 5

### Script Update Lease Time

Untuk melakukan konfigurasi pada lease time tiap clientnya, maka dibutuhkan juga konfigurasi baru yaitu `default-lease-time` sebagai lama waktu DHCP Server meminjamkan IP Address kepada client dan juga `max-lease-time` sebagai waktu maksimal yang dialokasikan untuk peminjaman IP oleh DHCP server ke client. Keduanya dalam satuan detik.

```
subnet 10.33.2.0 netmask 255.255.255.0 {
}
subnet 10.33.3.0 netmask 255.255.255.0 { 
	range 10.33.3.16 10.33.3.32;
	range 10.33.3.64 10.33.3.80; 
	option routers 10.33.3.1;
	option broadcast-address 10.33.3.255; 
	option domain-name-servers 10.33.1.3;
	default-lease-time 180; 
	max-lease-time 5760;
}
subnet 10.33.4.0 netmask 255.255.255.0 { 
	range 10.33.4.12 10.33.4.20;
	range 10.33.4.160 10.33.4.168; 
	option routers 10.33.3.1;
	option broadcast-address 10.33.4.255; 
	option domain-name-servers 10.33.1.3;
	default-lease-time 720; 
	max-lease-time 5760;
}
```




























