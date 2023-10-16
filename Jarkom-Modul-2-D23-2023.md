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
  - [Soal Nomor 9](#soal-nomor-9)
  - [Soal Nomor 10](#soal-nomor-10)
  - [Soal Nomor 11](#soal-nomor-11)
    
 
 


## Soal Nomor 1

Yudhistira akan digunakan sebagai DNS Master, Werkudara sebagai DNS Slave, Arjuna merupakan Load Balancer yang terdiri dari beberapa Web Server yaitu Prabakusuma, Abimanyu, dan Wisanggeni. Buatlah topologinya.

## Jawaban Nomor 1

### Setup Topologi

Pada pembagian topologi, kelompok kami mendapat topologi nomor 4 sehingga susunan dari tiap node nya adalah sebagai berikut

![No1](https://cdn.discordapp.com/attachments/773324309020147732/1162878352462446683/image.png?ex=653d89dc&is=652b14dc&hm=b222952a5c96e7d27c55668cc49cdc14d8dd53d64ed46437cbc3af7e1aff26e3&)

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

## Checking Koneksi Node

Setelah melakukan konfigurasi pada setiap nodenya, kami melakukan beberapa pengecekkan

- Check apakah node sudah berada pada IP yang sesuai dengan menggunakan command `ip a`

![No1-1](https://cdn.discordapp.com/attachments/773324309020147732/1162879722527670282/image.png?ex=653d8b23&is=652b1623&hm=4fe8495e56308e88ca8051d14e6a39d723fbf7cb1127a2ed9bf0c9a892df4722&)

dengan informasi seperti gambar diatas, IP yang digunakan sudah sesuai dengan kelompok kami

- Membuat topologi bisa mengakses keluar jaringan dengan menggunakan command `iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE -s 10.33.0.0/16`
- Melihat nameserver yang digunakan dengan menggunakan command `cat /etc/resolv.conf` pada Router
- Memasukkan IP DNS pada node lain dengan command `echo nameserver 192.168.122.1 > /etc/resolv.conf`
- Mencoba PING google.com pada node tersebut

![No1-2](https://cdn.discordapp.com/attachments/773324309020147732/1162881249275289790/image.png?ex=653d8c8f&is=652b178f&hm=eeac28fc1fad1a752e2abab242a96986650a670c7123b0ad64bbf3016afbee59&)

setelah dicoba pada node Yudhistira, tampil informasi seperti diatas yang berarti konfigurasi jaringan tiap nodenya sudah benar dan berjalan


## Soal Nomor 2

Buatlah website utama pada node arjuna dengan akses ke arjuna.yyy.com dengan alias www.arjuna.yyy.com dengan yyy merupakan kode kelompok.

## Jawaban Nomor 2

### Setup Domain DNS Master 2

Untuk membuat domain arjuna.yyy.com, awalnya kami melakukan setup pada DNS Master sebagai berikut

- Melakukan `apt-get update` dan `apt-get install bind9 -y` pada DNS Master
- Mengubah file named.conf.local dengan command `nano /etc/bind/named.conf.local` dan diisi dengan script seperti ini
```
zone "arjuna.D23.com" {
	type master;
	file "/etc/bind/jarkom/arjuna.D23.com";
};
```
- Membuat folder baru `mkdir /etc/bind/jarkom` dan copy semua isi pada db.local ke file baru `cp /etc/bind/db.local /etc/bind/jarkom/arjuna.D23.com`
- Ubah isi arjuna.D23.com `nano /etc/bind/jarkom/arjuna.D23.com` dengan script seperti berikut

![No2-1](https://cdn.discordapp.com/attachments/773324309020147732/1162927529972224090/image.png?ex=653db7a9&is=652b42a9&hm=e9ac7caef5d98cf9a1170aba20c135bd4f13511be6ff78461592ff89cae44ceb&)

- Restart Service `service bind9 restart`

### Setup Domain Node Arjuna

Setelah melakukan setup pada DNS Master, kemudian kami melakukan setup untuk domain di node arjuna sebagai berikut

- Melakukan `apt-get update` dan `apt-get install apache2` pada LB Arjuna
- Start service apache `service apache2 start` dan install php pada LB Arjuna `apt-get install php`
- Menambahkan isi folder index.php pada folder html di default apache dengan script sebagai berikut
```
<?php
$hostname = gethostname();
$date = date('Y-m-d H:i:s');
$php_version = phpversion();
$username = get_current_user();

echo "Hello World!<br>";
echo "Saya adalah: $username<br>";
echo "Saat ini berada di: $hostname<br>";
echo "Versi PHP yang saya gunakan: $php_version<br>";
echo "Tanggal saat ini: $date<br>";
?>
```
- Melakukan install apache untuk php `apt-get install libapache2-mod-php7.0` dan restart service `service apache2 restart`

### Checking Domain Arjuna

Setelah melakukan setup pada DNS Master, dan node arjuna kami melakukan testing domain tersebut pada node lain dengan langkah sebagai berikut

- Melakukan `apt-get update` dan install lynx `apt-get install lynx` pada node tersebut
- Akses domain dengan command `lynx http://10.33.3.5/index.php`

![No2-2](https://cdn.discordapp.com/attachments/773324309020147732/1162893722745327736/image.png?ex=653d982d&is=652b232d&hm=98c286a687e56e269010d50b85ec90ab7eb5778bb69da9fda85b87eb58d0fcde&)

dengan munculnya script php yang tadi sudah dipasang, berarti domain arjuna.D23.com sudah dapat diakses


## Soal Nomor 3

Dengan cara yang sama seperti soal nomor 2, buatlah website utama dengan akses ke abimanyu.yyy.com dan alias www.abimanyu.yyy.com.

## Jawaban Nomor 3

### Setup Domain DNS Master 3

Untuk membuat domain abimanyu.yyy.com, langkah yang kami lakukan sama seperti nomor 2

- Melakukan `apt-get update` dan `apt-get install bind9 -y` pada DNS Master
- Mengubah file named.conf.local dengan command `nano /etc/bind/named.conf.local` dan diisi dengan script seperti ini
```
zone "abimanyu.D23.com" {
	type master;
	file "/etc/bind/jarkom/arjuna.D23.com";
};

```
- Membuat folder baru `mkdir /etc/bind/jarkom` dan copy semua isi pada db.local ke file baru `cp /etc/bind/db.local /etc/bind/jarkom/abimanyu.D23.com`
- Ubah isi abibmanyu.D23.com `nano /etc/bind/jarkom/abimanyu.D23.com` dengan script seperti berikut

![No3-1](https://cdn.discordapp.com/attachments/773324309020147732/1162927716568420533/image.png?ex=653db7d5&is=652b42d5&hm=36f9ecc322837faac968e805f111fdf524114aca5223d1a035e0edbeeede9695&)

- Restart Service `service bind9 restart`

### Setup Domain Node Abimanyu

- Melakukan `apt-get update` dan `apt-get install apache2` pada Webserver Abimanyu
- Start service apache `service apache2 start` dan install php pada Webserver Abimanyu `apt-get install php`
- Menambahkan isi folder index.php pada folder html di default apache dengan script sebagai berikut
```
<?php
	if($_SERVER['REQUEST_URI'] == '/index.php/home' || $_SERVER['REQUEST_URI'] == '/home' || $_SERVER['REQUEST_URI'] == '/index.php' || $_SERVER['REQUEST_URI'] == '/') readfile('home.html');
	else http_response_code(404);
?>
```
- Melakukan install apache untuk php `apt-get install libapache2-mod-php7.0` dan restart service `service apache2 restart`

### Checking Domain Abimanyu

Setelah melakukan setup pada DNS Master, dan node arjuna kami melakukan testing domain tersebut pada node lain dengan langkah sebagai berikut

- Melakukan `apt-get update` dan install lynx `apt-get install lynx` pada node tersebut
- Akses domain dengan command `lynx http://10.33.3.2/index.php`

![No3-2](https://cdn.discordapp.com/attachments/773324309020147732/1162899818520252566/image.png?ex=653d9dda&is=652b28da&hm=58ab225ede4b0598a9a0e4da8ac8b3a5fa539432c4ddfe1a02360e8933621b2c&)

karena belum ada file html yang kami pasang, maka tampilan dari domain abimanyu.D23.com adalah seperti pada gambar tersebut


## Soal Nomor 4

Kemudian, karena terdapat beberapa web yang harus di-deploy, buatlah subdomain parikesit.abimanyu.yyy.com yang diatur DNS-nya di Yudhistira dan mengarah ke Abimanyu.

## Jawaban Nomor 4

### Penambahan Konfigurasi DNS Master 4

Pada DNS Master Yudhistira tambahkan konfigurasi di file abimanyu.D23.com nya `nano /etc/bind/jarkom/abimanyu.D23.com` sebagai berikut

![No4](https://cdn.discordapp.com/attachments/773324309020147732/1162927980356579409/image.png?ex=653db814&is=652b4314&hm=05fbcb31565b3b75f1892ad78c8ecbe285e1dc1527cbbbe948657239e41b3c81&)

Kemudian restart bind9 nya `service bind9 restart`


## Soal Nomor 5

Buat juga reverse domain untuk domain utama. (Abimanyu saja yang direverse)

## Jawaban Nomor 5

### Penambahan Konfigurasi DNS Master 5

Pada DNS Master Yudhistira tambahkan file config baru `nano /etc/bind/named.conf.local` kemudian isikan dengan script seperti berikut
```
zone "2.3.33.in-addr.arpa" {
    type master;
    file "/etc/bind/jarkom/2.3.33.in-addr.arpa";
};
```
Script tersebut menunjukkan IP domain abimanyu yang telah di reverse. Kemudia copy file db.local ke file baru `cp /etc/bind/db.local /etc/bind/jarkom/2.3.33.in-addr.arpa` dan ubah file baru `nano /etc/bind/jarkom/2.3.33.in-addr.arpa` menjadi seperti berikut 

![No5](https://cdn.discordapp.com/attachments/773324309020147732/1162901870386356245/image.png?ex=653d9fc3&is=652b2ac3&hm=653c0196a7973681162512ca01db95e54800d709d12a39ba42ec2c0a4722bd5b&)

Setealh itu restart kembali bind9 nya `service bind9 restart`


## Soal Nomor 6

Agar dapat tetap dihubungi ketika DNS Server Yudhistira bermasalah, buat juga Werkudara sebagai DNS Slave untuk domain utama.

## Jawaban Nomor 6

### Penambahan Konfigurasi DNS Master 6

Pada DNS Master ubah file named.conf.local `nano /etc/bind/named.conf.local` dengan script sebagai berikut
```
zone "arjuna.D23.com" {
    type master;
    notify yes;
    also-notify { 10.33.1.2; }; 
    allow-transfer { 10.33.1.2; }; 
    file "/etc/bind/jarkom/arjuna.D23.com";
};
```
untuk domain arjuna dan 
```
zone "abimanyu.D23.com" {
    type master;
    notify yes;
    also-notify { 10.33.1.2; }; 
    allow-transfer { 10.33.1.2; }; 
    file "/etc/bind/jarkom/abimanyu.D23.com";
};
```
untuk domain abimanyu. Script tersebut mengisyaratkan bahwa apapun yang dilakukan pada domain arjuna dan abimanyu akan ternotify ke `IP 10.33.1.2` atau node Werkudara sebagai DNS Slave. Setelah itu restart lagi bind9 nya `service bind9 restart`

### Setup DNS Slave

- Melakukan `apt-get update` dan `apt-get install bind9 -y` pada Wekudara
- Ubah file named.conf.local `nano /etc/bind/named.conf.local` dengan script sebagai berikut
```
zone "arjuna.D23.com" {
    type slave;
    masters { 10.33.1.3; }; 
    file "/var/lib/bind/arjuna.D23.com";
};
```
```
zone "abimanyu.D23.com" {
    type slave;
    masters { 10.33.1.3; }; 
    file "/var/lib/bind/abimanyu.D23.com";
};
```
- Restart bind9 `service bind9 restart`

### Checking DNS Slave

Checking ini dilakukan pada salah satu node di topologi.

- Stop service bind9 pada node Yudhistira `service bind9 stop`
- Arahkan nameserver ke IP Yudhistira dan IP Werkudara `nano /etc/resolv.conf`
```
nameserver 10.33.1.3
nameserver 10.33.1.2
```
- Kemudian ping domainnya


## Soal Nomor 7

Seperti yang kita tahu karena banyak sekali informasi yang harus diterima, buatlah subdomain khusus untuk perang yaitu baratayuda.abimanyu.yyy.com dengan alias www.baratayuda.abimanyu.yyy.com yang didelegasikan dari Yudhistira ke Werkudara dengan IP menuju ke Abimanyu dalam folder Baratayuda

## Jawaban Nomor 7

### Penambahan Konfigurasi DNS Master 7

- Pada DNS Master, kami melakukan perubahan konfigurasi di file abimanyu.D23.com `nano /etc/bind/jarkom/abimanyu.D23.com` menjadi seperti berikut ini

![No7-1](https://cdn.discordapp.com/attachments/773324309020147732/1162928729027268758/image.png?ex=653db8c7&is=652b43c7&hm=e276fb3e3eac2b5cee975ac21bd08dca3b855715d7dac63f42ee776770b698a0&)

- Setelah itu kami mencoba mengubah file named.conf.options `nano /etc/bind/named.conf.options` dengan mengcomment `dnssec-validation auto;` dan menambahkan `allow-query{any;};` di line bawahnya
- Kemudian konfigurasi ulang file named.conf.local `nano /etc/bind/named.conf.local` menjadi seperti berikut ini
```
zone "abimanyu.D23.com" {
    type master;
    file "/etc/bind/jarkom/abimanyu.D23.com";
    allow-transfer { 10.33.1.2; };
};
```
- Setelah itu restart ulang bind9 nya `service bind9 restart`

### Penambahan Konfigurasi DNS Slave 7

- Pada DNS Slave, kami juga melakukan konfigurasi ulang yang sama dengan DNS Master yaitu dengan edit file named.conf.options `nano /etc/bind/named.conf.options` dengan mengcomment `dnssec-validation auto;` dan menambahkan `allow-query{any;};` di line bawahnya
- Setelah itu kami juga mengkonfigurasi ulang file named.conf.local `nano /etc/bind/named.conf.local` menjadi seperti berikut ini

![No7-2](https://cdn.discordapp.com/attachments/773324309020147732/1162931092047810620/image.png?ex=653dbafa&is=652b45fa&hm=873967203afc0315e4d4bd486a620a51988fa4c9876ac87ffe41ac1b996aabfd&)

- Kemudian kami juga membuat directory baru dengan nama delegasi `mkdir /etc/bind/delegasi` dan mencopy seluruh file db.local ke file baru tersebut `cp /etc/bind/db.local /etc/bind/delegasi/baratayuda.abimanyu.D23.com`
- Terakhir kami mengubah isi file tersebut menjadi seperti dibawah ini

![No7-3](https://cdn.discordapp.com/attachments/773324309020147732/1162931667598586036/image.png?ex=653dbb83&is=652b4683&hm=b8c4de188217213df2039b5ab780a7bf1020d14c7932ae6e313419a7528aa540&)

Domain tersebut juga sudah diarahkan ke IP dari abimanyu. Setelah itu, restart juga bind9 nya `service bind9 restart`


## Soal Nomor 8

Untuk informasi yang lebih spesifik mengenai Ranjapan Baratayuda, buatlah subdomain melalui Werkudara dengan akses rjp.baratayuda.abimanyu.yyy.com dengan alias www.rjp.baratayuda.abimanyu.yyy.com yang mengarah ke Abimanyu.

## Jawaban Nomor 8

### Penambahan Konfigurasi DNS Slave 8

Untuk membuat subdomain baru, kami langsung menambahkan konfigurasi pada file baratayuda.abimanyu.D23.com `nano /etc/bind/delegasi/baratayuda.abimanyu.D23.com` dengan konfigurasi sebagai berikut 

![No8](https://cdn.discordapp.com/attachments/773324309020147732/1162932587602387086/image.png?ex=653dbc5f&is=652b475f&hm=9f12ebeed41f5dfa97f8e1bd2378b6614e805ae9fc9f665d729e29f108169a9f&)

Setelah menambahkan konfigurasi tersebut, kami merestart ulang bind9 nya `service bind9 restart`

## Soal Nomor 9

Arjuna merupakan suatu Load Balancer Nginx dengan tiga worker (yang juga menggunakan nginx sebagai webserver) yaitu Prabakusuma, Abimanyu, dan Wisanggeni. Lakukan deployment pada masing-masing worker.

## Jawaban Nomor 9

### Instalasi NGINX di Abimanyu, Prabakusuma, dan Wisanggeni.
```bash
echo nameserver 192.168.122.1 > /etc/resolv.conf
apt-get update 
apt-get install nginx php php-fpm -y
wget --no-check-certificate 'https://docs.google.com/uc?export=download&id=17tAM_XDKYWDvF-JJix1x7txvTBEax7vX' -O arjuna.zip
apt-get install unzip
unzip arjuna.zip
mkdir /var/www/arjuna
cp arjuna.yyy.com/index.php /var/www/arjuna/index.php
```
script ini dijalankan pada Abimanyu, Prabakusuma dan juga wisanggeni. </br>
kemudian kita cek manual di luar script versi dari php yang terinstall </br>
```php -v```</br>

![Screenshot_194](https://github.com/LigarArnata/Lapres-Jarkom-D23-2023/assets/89778375/22819c9b-58a4-4cf7-958a-01981a62e4f1)

kemudian pada file berikut ```/etc/nginx/sites-available/arjuna``` diisi dengan konfigurasi sebagai berikut
```
server {

 	listen 800X; #X diganti 1/2/3 sesuai prabakusuma,abimanyu dan wisanggeni

 	root /var/www/arjuna;

 	index index.php index.html index.htm;
 	server_name 10.33.3.X; #X diganti dengan nomor akhir 2/3/4 abi/praba/wis

 	location / {
 			try_files $uri $uri/ /index.php?$query_string;
 	}

 	# pass PHP scripts to FastCGI server
 	location ~ \.php$ {
 	include snippets/fastcgi-php.conf;
 	fastcgi_pass unix:/var/run/php/php7.0-fpm.sock; #disesuaikan dengan versi php yang diterima
 	}

 location ~ /\.ht {
 			deny all;
 	}

 	error_log /var/log/nginx/arjuna_error.log;
 	access_log /var/log/nginx/arjuna_access.log;
 }

```
kemudian lakukan linking agar bisa diakses dan restart nginx </br>
```bash
ln -s /etc/nginx/sites-available/arjuna /etc/nginx/sites-enabled
service nginx restart
nginx -t
```

## Soal Nomor 10

Kemudian gunakan algoritma Round Robin untuk Load Balancer pada Arjuna. Gunakan server_name pada soal nomor 1. Untuk melakukan pengecekan akses alamat web tersebut kemudian pastikan worker yang digunakan untuk menangani permintaan akan berganti ganti secara acak. Untuk webserver di masing-masing worker wajib berjalan di port 8001-8003. Contoh
    - Prabakusuma:8001
    - Abimanyu:8002
    - Wisanggeni:8003

## Jawaban Nomor 10

### Setup LB-Arjuna
Pada LB-Arjuna, buat file yang mengatur jalurnya load balancer untuk setiap worker
```
nano /etc/nginx/sites-available/lb-arjuna
```
dengan isi 
```
Upstream myweb {
		Server 10.33.3.2; #abimanyu
		Server 10.33.3.3; #prabakusuma
		Server 10.33.3.4; #wisanggeni
	}
	
	Server {
		Listen 8001;
		Listen 8002;
		Listen 8003;
Server_name arjuna.D23.com;
		
		location/ {
		Proxy_pass http://myweb;
		}
}

```
kemudian lakukan linking untuk mengaktifasi sites nya
```
ln -s /etc/nginx/sites-available/lb-arjuna /etc/nginx/sites-enabled
```


## Jawaban Nomor 11

### 













  
