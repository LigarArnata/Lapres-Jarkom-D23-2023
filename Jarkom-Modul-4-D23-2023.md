# Laporan Resmi Praktikum Jarkom Modul 4

![Lambang ITS](https://www.its.ac.id/wp-content/uploads/2020/07/Lambang-ITS-2-320x320.png)

Kelompok D23 :

- Ligar Arsa Arnata (5025211244)
- Alfadito Aulia Denova (5025211157)

## Daftar Isi

- [Laporan Resmi Praktikum Jarkom Modul 4](#laporan-resmi-praktikum-jarkom-modul-4)
  - [Daftar Isi](#daftar-isi)
  - [Topologi](#topologi)
  - [Rute dan Subnetting](#rute-dan-subnetting)
  - [Prefix IP](#prefix-ip)
  - [VLSM](#vlsm)
    - [Pengelompokkan Subnet](#pengelompokkan-subnet)
    - [Pembagian IP](#pembagian-ip)
    - [Routing](#routing)
  - [CIDR](#cidr)
    - [Penggabungan](#penggabungan)
    - [Prefix IP dan Pembagian IP](#prefix-ip-dan-pembagian-ip)
    - [Topologi dan Routing di GNS3](#topologi-dan-routing-di-gns-3)

## Topologi

Berikut merupakan Topologi awal yang disediakan pada soal

![Topologi](https://cdn.discordapp.com/attachments/773324309020147732/1180687517050208266/Screenshot_2023-11-28_235649.png?ex=657e53f0&is=656bdef0&hm=61d60e053fc983fdb5cf7e3dda61106ddda7e89f5ab0ce51e205d5a8a9e72cd4&)

## Rute dan Subnetting

Setelah mendapatkan topologi tersebut, bisa dilakukan subnetting agar pembagian IP dapat dilakukan dengan efisien sekaligus juga dapat menentukan netmask yang akan digunakan dari setip subnet. Berikut merupakan hasil subnetting dan rute yang didapatkan

![Subnetting](https://cdn.discordapp.com/attachments/773324309020147732/1180688713508991037/image.png?ex=657e550d&is=656be00d&hm=f43acd03dbf8f96c02b2b2b678da13a2cd0b1629d6d7f72551ea9a124e78aca6&)

Langkah tersebut menghasilkan 22 Subnet dengan netmask yang juga sudah ditentukan dari jumlah host tiap subnet tersebut. Jika hasil subnetting dirutekan akan menjadi seperti berikut ini

![Rute](https://cdn.discordapp.com/attachments/773324309020147732/1180689146663161897/image.png?ex=657e5574&is=656be074&hm=fbda60adaa34c2305927392f29b7514f182e724492c3ecc67e451bb4dfe5fae2&)

## Prefix IP

Pada pembagian IP, kelompok kami akan menggunakan Prefix IP `10.33` sesuai dengan pembagian pada modul sebelumnya

## VLSM

VLSM, atau _Variable Length Subnet Masking_, adalah teknik dalam pembagian alamat IP yang memungkinkan penggunaan subnet dengan netmask yang bervariasi. Dalam konteks pembagian IP, subnetting adalah praktik membagi-bagi jaringan besar menjadi subnet-subnet yang lebih kecil untuk efisiensi manajemen dan alokasi alamat IP seperti yang sudah dilakukan sebelumnya.

### Pengelompokkan Subnet

Setelah melakukan subnetting dan mendapatkan rute dari subnet tersebut, akan dilakukan pengelompokkan tiap subnet berdasarkan netmask nya dimana akan diurutkan dari netmask terkecil ke yang terbesar. Langkah ini sama dengan pembuatan tree yang mana akan mengelompokkan dan mengurutkan subnet yang didapat berdasarkna netmasknya sesuai dengan langkah langkah pada VLSM. Berikut merupakan hasil pengelompokkan subnet berdasarkan netmasknya

![Kelompok](https://cdn.discordapp.com/attachments/773324309020147732/1180692210317000745/image.png?ex=657e584f&is=656be34f&hm=bc0074395dd9b717542467ce4de40a873add57f735638799b254524fd358ed8e&)

### Pembagian IP

Langkah selanjutnya setelah mengelompokkan subnet adalah membagi IP pada subnet subnet tersebut sesuai dengan prefix dan urutannya. Berikut merupakan hasil dari pembagian IP nya

![Pembagian](https://cdn.discordapp.com/attachments/773324309020147732/1180692671514279976/image.png?ex=657e58bd&is=656be3bd&hm=16dd4a3dbda8f4e47a44c6a349ca329d95f94b242aad3f05add6a743feddf0c7&)

### Routing

Langkah terakhir adalah melakukan routing pada tiap subnet sehingga tiap tiap subnet yang ada bisa berkomunikasi dengan satu sama lain. Routing ini dapat dilakukan dengan mengkonfigurasi router yang ada pada subnet tersebut. Konfigurasi yang dibutuhkan adalah `Network ID subnet yang lain`, `Netmask Subnet`, dan juga `IP Address dari next hop router atau router terdekat dari subnet lain yang tersambung`. Berikut merupakan beberapa hasil routing yang berhasil dimana akan menampilkan informasi mengenai keberhasilan kominukasi dari setiap endpoint antar subnet

![Routing](https://cdn.discordapp.com/attachments/773324309020147732/1180695109642244196/image.png?ex=657e5b02&is=656be602&hm=f49a64e19df1fd89d96883ac1a82a17e9c7f2a82aa036ba8f6f36ca3c1e83acd&)

Gambar diatas merupakan beberapa hasil routing yang sudah berhasil, dimana dapat dilakukan komunikasi antara `LaubHills - LakeKorridor (subnet 1 - subnet 7)`, `WileRegion - TurkRegion (subnet 10 - subnet 14)`, dan `RohrRoad - GrabeForest (subnet 3 - subnet 15)`.

## CIDR

Dalam Teknik CIDR, alias _Classless Inter Domain Routing_, Subnet-subnet kecil yang berdekatan diagabung menjadi subnet yang lebih besar. Dengan secara teori penggabungannya menaikkan subnet sebanyak yang terkecil-1, diantara dua subnet yang digabung. Dari penggabungan yang saya lakukan, didapat 8 kali penggabungan dan subnet terbesar adalah /14, tapi karena di bagian terluar masih bisa di akomodasi oleh /15, maka di pembagian ip address paling luar adalah /15.

### Penggabungan

![Screenshot_263](https://github.com/LigarArnata/Lapres-Jarkom-D23-2023/assets/89778375/fda073cd-6e52-44e1-9740-12faf4867906)

![Screenshot_264](https://github.com/LigarArnata/Lapres-Jarkom-D23-2023/assets/89778375/24d8f7d2-1298-4415-91e7-e6e9229aafca)

![Screenshot_265](https://github.com/LigarArnata/Lapres-Jarkom-D23-2023/assets/89778375/a7ca6e0d-b69d-40a5-9cab-927b64688977)

![Screenshot_266](https://github.com/LigarArnata/Lapres-Jarkom-D23-2023/assets/89778375/d53eb20c-707c-4663-a662-a30754e60436)

untuk visualisasi cakupan tiap subnet dan penggabungannya kami menggambar secara fisik tree dari CIDR tersebut. </br>
![CIDR_TREE](https://github.com/LigarArnata/Lapres-Jarkom-D23-2023/assets/89778375/a5652258-4587-4014-98ac-277ebfcee3c6)


### Prefix IP dan Pembagian IP

Karena netmask terluar/terbesarnya adalah /15. maka secara tidak langsung, Prefix IP kami berubah di bagian luar. sehingga ada node yang ber prefix 10.32., dan untuk node lain tetap menggunakan 10.33 sebagaimana yang sudah dibagikan ke kelompok kami.

![Screenshot_267](https://github.com/LigarArnata/Lapres-Jarkom-D23-2023/assets/89778375/dead14f6-af05-4852-b640-73d508ba7768)

![Screenshot_268](https://github.com/LigarArnata/Lapres-Jarkom-D23-2023/assets/89778375/a11faef9-6ab9-4101-be24-62681de1da04)

### Topologi dan Routing di GNS 3

Untuk Topologi pada GNS3 ini tidak jauh berbeda, hanya saja untuk tiap antarrouter perlu diberi Switch, agar dua router tersebut dapat berkomunikasi. </br>
![Screenshot_261](https://github.com/LigarArnata/Lapres-Jarkom-D23-2023/assets/89778375/0ed7f4ea-ee3e-4eb3-b095-310d9138f9e1)

untuk routing dan configurasi pada tiap nodenya belum di lakukan.





