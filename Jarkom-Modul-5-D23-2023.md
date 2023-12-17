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
  - [Soal Nomor 6](#soal-nomor-6)
  - [Jawaban Nomor 6](#jawaban-no-6)
  - [Soal Nomor 7](#soal-nomor-7)
  - [Jawaban Nomor 7](#jawaban-no-7)
  - [Soal Nomor 8](#soal-nomor-8)
  - [Jawaban Nomor 8](#jawaban-no-8)
  - [Soal Nomor 9](#soal-nomor-9)
  - [Jawaban Nomor 9](#jawaban-no-9)
  - [Soal Nomor 10](#soal-nomor-10)
  - [Jawaban Nomor 10](#jawaban-no-10)

    

## Topologi

Berikut merupakan topologi yang kami buat berdasarkan soal

![topologi](https://cdn.discordapp.com/attachments/773324309020147732/1185751252462731454/image.png?ex=6590bfe8&is=657e4ae8&hm=b1478fe75886972df112834b328973dc027f93287068023918a6c8e4e1a7719f&)

## Prefix IP

Pada pembagian IP, kelompok kami akan menggunakan Prefix IP `10.33` sesuai dengan pembagian pada modul sebelumnya

## Rute

Berikut merupakan topologi yang sudah kami bagi berdasarkan subnetnya

![subnet](https://cdn.discordapp.com/attachments/773324309020147732/1185751523037290516/image.png?ex=6590c029&is=657e4b29&hm=0772eb3c11a0242f853e1b353ad9e3e4ec9e8015ab376145325e0300e7b77f03&)

Setelah membagi topologi tersebut menjadi beberapa subnet, berikut merupakan rute yang didapatkan beserta dengan jumlah host yang harus disediakan

![rute](https://cdn.discordapp.com/attachments/773324309020147732/1185751657515077692/image.png?ex=6590c049&is=657e4b49&hm=9a8e055e6908f7180e1dc6848f9f3b8147b4b9f61fa711ebdce24b97b6f34f02&)

## Pembagian IP dan Subnetting

Berdasarkan rute diatas, berikut adalah pembagian IP yang kami lakukan menggunakan metode **VLSM**

![vlsm](https://cdn.discordapp.com/attachments/773324309020147732/1185751783595855882/image.png?ex=6590c067&is=657e4b67&hm=96c376b478e5719b15b99aee51a9fc7006cac389914c79789e9119ce8d7182c4&)

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

Untuk melakukan pembatasan sehingga koneksi SSH pada Web Server hanya dapat dilakukan oleh IP GrobeForest, maka dapat menggunakan perintah yang akan membatasi akses client dengan IP yang sesuai pada range IP GrobeForest yaitu `10.33.4.2 - 10.33.7.254` sebagai berikut

```sh
iptables -A INPUT -p tcp --dport 22 -s 10.33.x.x -j ACCEPT
iptables -A INPUT -p tcp --dport 22 -j DROP
```

## Soal Nomor 5

> Selain itu, akses menuju WebServer hanya diperbolehkan saat jam kerja yaitu Senin-Jumat pada pukul 08.00-16.00.

## Jawaban Nomor 5

Untuk melakukan pembatasan akses WebServer agar hanya dapat dituju saat jam kerja saja, maka akan menggunakan perintah yang menetapkan timestart, timestop, serta hari masuk pada node **Sein** dan **Stark** sebagai Web Server seperti berikut ini 

```sh
iptables -A INPUT -m time --timestart 08:00 --timestop 16:00 --weekdays Mon,Tue,Wed,Thu,Fri -j ACCEPT
iptables -A INPUT -j REJECT
```

## Soal Nomor 6

> Lalu, karena ternyata terdapat beberapa waktu di mana network administrator dari WebServer tidak bisa stand by, sehingga perlu ditambahkan rule bahwa akses pada hari Senin - Kamis pada jam 12.00 - 13.00 dilarang (istirahat maksi cuy) dan akses di hari Jumat pada jam 11.00 - 13.00 juga dilarang (maklum, Jumatan rek).

## Jawaban Nomor 6

Untuk penambahan rule nomor 6 juga akan dilakukan pada node **Sein** dan **Stark** sebagai Web Server seperti berikut ini

```sh 
iptables -A INPUT -m time --timestart 12:00 --timestop 13:00 --weekdays Mon,Tue,Wed,Thu -j REJECT
iptables -A INPUT -m time --timestart 11:00 --timestop 13:00 --weekdays Fri -j REJECT
```

## Soal Nomor 7

> Karena terdapat 2 WebServer, kalian diminta agar setiap client yang mengakses Sein dengan Port 80 akan didistribusikan secara bergantian pada Sein dan Stark secara berurutan dan request dari client yang mengakses Stark dengan port 443 akan didistribusikan secara bergantian pada Sein dan Stark secara berurutan.

## Jawaban Nomor 7

## Soal Nomor 8

> Karena berbeda koalisi politik, maka subnet dengan masyarakat yang berada pada Revolte dilarang keras mengakses WebServer hingga masa pencoblosan pemilu kepala suku 2024 berakhir. Masa pemilu (hingga pemungutan dan penghitungan suara selesai) kepala suku bersamaan dengan masa pemilu Presiden dan Wakil Presiden Indonesia 2024.

## Jawaban Nomor 8

Untuk memenuhi perintah tersebut, harus ditambahakan rule baru yang akan membatasi akses ke Web Server pada hari ini sampai dengan tanggal pencoblosan pemilu yaitu mulai 2023-12-17 sampai 2024-02-15. Berikut merupakan perintah yang dapat dijalankan

```sh
iptables -A INPUT -p tcp --dport 80 -s 10.33.12.0/24 -m time --datestart 2023-12-17 --datestop 2024-02-15 -j DROP
```

## Soal Nomor 9

> Sadar akan adanya potensial saling serang antar kubu politik, maka WebServer harus dapat secara otomatis memblokir  alamat IP yang melakukan scanning port dalam jumlah banyak (maksimal 20 scan port) di dalam selang waktu 10 menit. 
(clue: test dengan nmap)

## Jawaban Nomor 9

## Soal Nomor 10

> Karena kepala suku ingin tau paket apa saja yang di-drop, maka di setiap node server dan router ditambahkan logging paket yang di-drop dengan standard syslog level.

## Jawaban Nomor 10
     
