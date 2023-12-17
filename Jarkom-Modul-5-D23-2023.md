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
  - [Soal Nomor 1](#soal-nomor-1)
  - [Jawaban Nomor 2](#jawaban-no-2)
  - [Soal Nomor 3](#soal-nomor-3)
  - [Jawaban Nomor 3](#jawaban-no-3)
  - [Soal Nomor 4](#soal-nomor-4)
  - [Jawaban Nomor 4](#jawaban-no-4)
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

## Routing

Setelah melakukan konfigurasi dan subnetting pada setiap node, selanjutnya adalah melakukan routing seperti berikut

**Aura**
```
#Heiter
up route add -net 10.33.1.0 netmask 255.255.252.0 gw 10.33.13.134
up route add -net 10.33.4.0 netmask 255.255.252.0 gw 10.33.13.134

#Frieren
up route add -net 10.33.10.0 netmask 255.255.255.0 gw 10.33.13.138
up route add -net 10.33.13.140 netmask 255.255.255.252 gw 10.33.13.138
up route add -net 10.33.8.0 netmask 255.255.254.0 gw 10.33.13.138
up route add -net 10.33.13.0 netmask 255.255.255.128 gw 10.33.13.138
up route add -net 10.33.11.0 netmask 255.255.255.252 gw 10.33.13.138
up route add -net 10.33.12.0 netmask 255.255.255.252 gw 10.33.13.138
```

**Heiter**
```
up route add -net 0.0.0.0 netmask 0.0.0.0 gw 10.33.13.133
```

**Frieren**
```
up route add -net 10.33.8.0 netmask 255.255.254.0 gw 10.33.13.142
up route add -net 10.33.13.0 netmask 255.255.255.128 gw 10.33.13.142
up route add -net 10.33.11.0 netmask 255.255.255.252 gw 10.33.13.142
up route add -net 10.33.12.0 netmask 255.255.255.252 gw 10.33.13.142
up route add -net 0.0.0.0 netmask 0.0.0.0 gw 10.33.13.137
```

**Himmel**
```
up route add -net 10.33.11.0 netmask 255.255.255.252 gw 10.33.13.2
up route add -net 10.33.12.0 netmask 255.255.255.252 gw 10.33.13.2
up route add -net 0.0.0.0 netmask 0.0.0.0 gw 10.33.13.141
```

**Fern**
```
up route add -net 0.0.0.0 netmask 0.0.0.0 gw 10.33.13.1
```

## Konfigurasi

Untuk melakukan konfigurasi, jalankan perintah berikut pada node **Aura**
```
iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE -s 10.33.0.0/16
```
dan pada tiap node dijalankan perintah ``echo nameserver 192.168.122.1 > /etc/resolv.conf``

### DNS Server

Jalankan perintah berikut pada node **Ricther** yang menjadi DNS Server

```sh
echo 'nameserver 192.168.122.1' >/etc/resolv.conf

apt update
apt install netcat -y
apt install bind9 -y

echo '
options {
  directory "/var/cache/bind";
  forwarders {
    192.168.122.1;
  };
  allow-query {any;};
  auth-nxdomain no; # conform to RFC1035
  listen-on-v6 {any;};
}' > /etc/bind/named.conf.options 

service bind9 restart 
```

### DHCP Server

Jalankan perintah berikut pada node **Revolte** yang menjadi DHCP Server

```sh
echo 'nameserver 192.168.122.1' > /etc/resolv.conf

apt update
apt install netcat -y
apt install isc-dhcp-server -y

echo 'INTERFACESv4="eth0"' > /etc/default/isc-dhcp-server

echo '
# option definitions common to all supported networks...
option domain-name "example.org";
option domain-name-servers ns1.example.org, ns2.example.org;

default-lease-time 600;
max-lease-time 7200;

# have support for DDNS.)
ddns-update-style none;

# Subnet 3
subnet 10.33.1.0 netmask 255.255.252.0 {
  range 10.33.1.2 10.33.3.254;
  option routers 10.33.1.1;
  option broadcast-address 10.33.3.255;
  option domain-name-servers 10.33.11.2;
  default-lease-time 720;
  max-lease-time 7200;
}

# Subnet 4
subnet 10.33.4.0 netmask 255.255.252.0 {
  range 10.33.4.2 10.33.7.254;
  option routers 10.33.4.1;
  option broadcast-address 10.33.7.255; 
  option domain-name-servers 10.33.11.2;
  default-lease-time 720;
  max-lease-time 7200;
}

# Subnet 6
subnet 10.33.10.0 netmask 255.255.255.0 {
  range 10.33.10.2 10.33.10.254;
  option routers 10.33.10.1;
  option broadcast-address 10.33.10.255;
  option domain-name-servers 10.33.11.2;
  default-lease-time 720;
  max-lease-time 7200;
}

# Subnet 8
subnet 10.33.8.0 netmask 255.255.254.0 {
  range 10.33.8.2 10.33.9.254;
  option routers 10.33.8.1;
  option broadcast-address 10.33.9.255;
  option domain-name-servers 10.33.11.2;
  default-lease-time 720;
  max-lease-time 7200;
}

# Subnet 9
subnet 10.33.13.0 netmask 255.255.255.128 {
  range 10.33.13.2 10.33.13.126;
  option routers 10.33.13.1;
  option broadcast-address 10.33.13.127;
  option domain-name-servers 10.33.11.2;
  default-lease-time 720;
  max-lease-time 7200;
}

# Subnet 10
subnet 10.33.11.0 netmask 255.255.255.0 {
  range 10.33.11.2 10.33.11.254;
  option routers 10.33.11.1;
  option broadcast-address 10.33.11.255;
  option domain-name-servers 10.33.11.2;
  default-lease-time 720;
  max-lease-time 7200;
}

# Subnet 11
subnet 10.33.12.0 netmask 255.255.255.0 {
  range 10.33.12.2 10.33.12.254;
  option routers 10.33.12.1;
  option broadcast-address 10.33.12.255;
  option domain-name-servers 10.33.11.2;
  default-lease-time 720;
  max-lease-time 7200;
}

# Subnet 2
subnet 10.33.13.132 netmask 255.255.255.252 {}

# Subnet 5
subnet 10.33.13.136 netmask 255.255.255.252 {}

# Subnet 7
subnet 10.33.13.140 netmask 255.255.255.252 {}

' > /etc/dhcp/dhcpd.conf

service isc-dhcp-server start
```

### DHCP Relay

Lakukan konfigurasi pada node **Heiter** dan **Himmel** yang akan dijadikan DHCP Relay

```sh
echo 'nameserver 192.168.122.1' > /etc/resolv.conf

apt update
apt install netcat -y
apt install isc-dhcp-relay -y

echo '
SERVERS="10.33.12.2"
INTERFACES="eth0 eth1 eth2 eth3"
OPTIONS=""
' > /etc/default/isc-dhcp-relay

service isc-dhcp-relay restart
```

dan uncomment `net.ipv4.ip_forward=1` pada `/etc/sysctl.conf`

### Web Server

Lakukan konfigurasi pada node **Sein** dan **Stark** yang akan dijadikan web server

```sh
echo 'nameserver 192.168.122.1' > /etc/resolv.conf

apt update
apt install netcat -y
apt install apache2 -y
service apache2 start

echo '# If you just change the port or add more ports here, you will likely also
# have to change the VirtualHost statement in
# /etc/apache2/sites-enabled/000-default.conf

Listen 80
Listen 443

<IfModule ssl_module>
        Listen 443
</IfModule>

<IfModule mod_gnutls.c>
        Listen 443
</IfModule>

# vim: syntax=apache ts=4 sw=4 sts=4 sr noet' > /etc/apache2/ports.conf
```

dan tambahkan konfigurasi berikut pada  ``/var/www/html/index.html`` di node **Sein** dan **Stark**
```
echo '# Sein
Tester' > /var/www/html/index.html

echo '# Stark
Tester' > /var/www/html/index.html
```

### Client

Insttal **lynx** pada tiap tiap client yang ada dengan perintah berikut

```sh
apt update
apt install netcat -y
apt install lynx -y
```

## Soal Nomor 1

> Agar topologi yang kalian buat dapat mengakses keluar, kalian diminta untuk mengkonfigurasi Aura menggunakan iptables, tetapi tidak ingin menggunakan MASQUERADE.

## Jawaban Nomor 1

Untuk mengkonfigurasi iptables tanpa menggunakan MASQUERADE, akan dibutuhkan perintah yang dapat mengarahkan Network ID Router ke arah NAT yaitu **10.33.0.0/16**. Berikut merupakan perintah yang dapat digunakan pada node **Aura**

```sh
IPETH0="$(ip -br a | grep eth0 | awk '{print $NF}' | cut -d'/' -f1)"
iptables -t nat -A POSTROUTING -o eth0 -j SNAT --to-source "$IPETH0" -s 10.33.0.0/16
```

## Soal Nomor 2

> Kalian diminta untuk melakukan drop semua TCP dan UDP kecuali port 8080 pada TCP.

## Jawaban Nomor 2

Untuk melakukan drop semu TCP dan UDP kecuali port 8080 pada TCP, maka dapat menggunakan perintah berikut yang akan dijalankan pada node **Revolte** yang menjadi DHCP Server

```sh
iptables -A INPUT -p tcp --dport 8080 -j ACCEPT
iptables -A INPUT -p tcp -j DROP
iptables -A INPUT -p udp -j DROP
```

## Soal Nomor 3

> Kepala Suku North Area meminta kalian untuk membatasi DHCP dan DNS Server hanya dapat dilakukan ping oleh maksimal 3 device secara bersamaan, selebihnya akan di drop.

## Jawaban Nomor 3

Untuk membatasi DHCP dan DNS Server agar hanya dapat dilakukan ping oleh maksimal 3 device secara bersamaan, maka dapat menggunakan perintah berikut ini

```sh
iptables -I INPUT -p icmp -m connlimit --connlimit-above 3 --connlimit-mask 0 -j DROP
iptables -I INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT
```

## Soal Nomor 4

> Lakukan pembatasan sehingga koneksi SSH pada Web Server hanya dapat dilakukan oleh masyarakat yang berada pada GrobeForest.

## Jawaban Nomor 4

Untuk melakukan pembatasan sehingga koneksi SSH pada Web Server hanya dapat dilakukan oleh IP GrobeForest, maka dapat menggunakan perintah yang akan membatasi akses client dengan IP yang sesuai pada range IP GrobeForest yaitu `10.33.4.2 - 10.33.7.254` dengan






 
    
