# Laporan Resmi Praktikum Jarkom Modul 1

![Lambang ITS](https://www.its.ac.id/wp-content/uploads/2020/07/Lambang-ITS-2-320x320.png)

Kelompok D23 :

- Ligar Arsa Arnata (5025211244)
- Alfadito Aulia Denova (5025211157)

## Daftar Isi

- [Laporan Resmi Praktikum Jarkom Modul 1](#laporan-resmi-praktikum-jarkom-modul-1)
  - [Daftar Isi](#daftar-isi)
  - [Soal Nomor 1](#soal-nomor-1)
  - [Jawaban Nomor 1](#jawaban-nomor-1)
    - [File pcap dan Filtering](#file-pcap-dan-filtering-1)
    - [Detail TCP Sequence dan Acknowledge Number](#detail-tcp-sequence-dan-acknowledge-number)
    - [Sequence dan Acknowledge Number Packet Response](#Sequence-dan-Acknowledge-Number-Packet-Response)
    - [Flag](#flag-1)
  - [Soal Nomor 2](#soal-nomor-2)
  - [Jawaban Nomor 2](#jawaban-nomor-2)
    - [File pcap dan Filtering](#file-pcap-dan-filtering-2)
    - [Pemilihan packet dan Server yang digunakan](#pemilihan-packet-dan-server-yang-digunakan)
    - [Flag](#flag-2)
  - [Soal Nomor 3](#soal-nomor-3)
  - [Jawaban Nomor 3](#jawaban-nomor-3)
    - [File pcap dan Filtering](#file-pcap-dan-filtering-3)
    - [Perhitungan dan Penentuan Protokol](#Perhitungan-dan-Penentuan-Protokol)
    - [Flag](#flag-3)
  - [Soal Nomor 4](#soal-nomor-4)
  - [Jawaban Nomor 4](#jawaban-nomor-4)
    - [File pcap dan Pemilihan Packet](#File-pcap-dan-Pemilihan-Packet)
    - [User Datagram Protocol](#User-Datagram-Protocol)
    - [Kendala](#kendala-nomor-4)
  - [Soal Nomor 5](#soal-nomor-5)
  - [Jawaban Nomor 5](#jawaban-nomor-5)
    - [File pcap](#file-pcap)
    - [Filtering dan Transmission Control Protocol](#filtering-dan-transmission-control-protocol)
    - [IP Public](#ip-public)
    - [Kendala](#kendala-nomor-5)
  - [Soal Nomor 6](#soal-nomor-6)
  - [Jawaban Nomor 6](#jawaban-nomor-6)
    - [Kendala](#kendala-nomor-6)
  - [Soal Nomor 7](#soal-nomor-7)
  - [Jawaban Nomor 7](#jawaban-nomor-7)
    - [File pcap dan Filtering](#File-pcap-dan-Filtering-7)
    - [Perhitungan jumlah Packet](#Perhitungan-jumlah-packet)
    - [Flag](#flag-7)
  - [Soal Nomor 8](#soal-nomor-8)
  - [Jawaban Nomor 8](#jawaban-nomor-8)
    - [Filtering](#Filtering-8)
    - [Flag](#Flag-8)
  - [Soal Nomor 9](#soal-nomor-9)
  - [Jawaban Nomor 9](#jawaban-nomor-9)
    - [Filtering](#Filtering-9)
    - [Flag](#Flag-9)
  - [Soal Nomor 10](#soal-nomor-10)
  - [Jawaban Nomor 10](#jawaban-nomor-10)
    - [File pcap dan Filtering](#File-pcap-dan-Filtering-10)
    - [Pemilihan Packet dan Follow](#Pemilihan-Packet-dan-Follow)
    - [Informasi yang Didapat](#Informasi-yang-Didapat)
    - [Kendala](#kendala-nomor-10)


  ## Soal Nomor 1

  User melakukan berbagai aktivitas dengan menggunakan protokol FTP. Salah satunya adalah mengunggah suatu file.
    - Berapakah sequence number (raw) pada packet yang menunjukkan aktivitas tersebut? 
    - Berapakah acknowledge number (raw) pada packet yang menunjukkan aktivitas tersebut? 
    - Berapakah sequence number (raw) pada packet yang menunjukkan response dari aktivitas tersebut?
    - Berapakah acknowledge number (raw) pada packet yang menunjukkan response dari aktivitas tersebut?


  ## Jawaban Nomor 1


  ### File pcap dan Filtering 1

  Buka File soal1.pcapng dan masukkan filter `ftp contains "STOR"` pada display filter. Filter tersebut hanya akan menampilkan packet dengan protocol FTP dan memiliki   request perintah STOR atau yang memiliki keterangan sebagai packet yang Meng-upload file ke FTP server

  ![No1-1](https://cdn.discordapp.com/attachments/773324309020147732/1154289009980346438/image.png)


  ### Detail TCP Sequence dan Acknowledge Number

  Cek pada bagian Transmission Control Protocol dari packet tersebut dan lihat Sequence dan Acknowledge Number

  ![No1-2](https://cdn.discordapp.com/attachments/773324309020147732/1154290301670801408/image.png)

  Ditemukan bahwa Sequence dan Acknowledge Number adalah **258040667 dan 1044861039**


  ### Sequence dan Acknowledge Number Packet Response

  Untuk melihat Sequence dan Acknowledge Number dari Packet Responsenya maka hapus `contains "STOR"` dari filter sehingga menyisakan `ftp` dan pilih packet yang tepat    berada dibawah packet yang memiliki request perintah STOR tadi, kemudian dengan cara yang sama pada bagian Transmission Control Protocol lihat Sequence dan Acknowledge Number

  ![No1-3](https://cdn.discordapp.com/attachments/773324309020147732/1154291658624618536/image.png)

  Ditemukan bahwa Sequence dan Acknowledge Number adalah **1044861039 dan 258040696**


  ### Flag 1

  Berikut merupakan flag yang kami dapatkan

  ![No1-Flag](https://cdn.discordapp.com/attachments/773324309020147732/1154292297161244672/image.png)


  ## Soal Nomor 2

  Sebutkan web server yang digunakan pada portal praktikum Jaringan Komputer!


  ## Jawaban Nomor 2


  ### File pcap dan Filtering 2

  Buka file soal2.pcapng dan masukkan filter `ip.src == 10.21.78.111 or ip.dst == 10.21.78.111` yang mana IP didapatkan langsung dari portal praktikum Jaringan Komputer sehingga filter tersebut hanya akan menampilkan packet yang berasal dan menuju portal tersebut

  ![No2-1](https://cdn.discordapp.com/attachments/773324309020147732/1154295238882512926/Screenshot_56.png)


  ### Pemilihan packet dan Server yang digunakan

  Kemudian pilih salah satu packet dan lihat informasi server yang digunakan pada bagian Hypertext Transfer Protocol packet tersebut

  ![No2-2](https://cdn.discordapp.com/attachments/773324309020147732/1154295447754653758/image.png)

  Ditemukan bahwa web server yang digunakan pada portal praktikum Jaringan Komputer adalah **gunicorn**


  ### Flag 2

  Berikut merupakan flag yang kami dapatkan

  ![No2-Flag](https://cdn.discordapp.com/attachments/773324309020147732/1154296747884019723/image.png)


  ## Soal Nomor 3

  Dapin sedang belajar analisis jaringan. Bantulah Dapin untuk mengerjakan soal berikut:
    - Berapa banyak paket yang tercapture dengan IP source maupun destination address adalah 239.255.255.250 dengan port 3702 ?
    - Protokol layer transport apa yang digunakan ?


  ## Jawaban Nomor 3


  ### File pcap dan Filtering 3

  Buka file pcap soal3.pcap dan masukkan filter `ip.src == 239.255.255.250 or ip.dst == 239.255.255.250 and udp.port == 3702`

  ![No3-1](https://cdn.discordapp.com/attachments/773324309020147732/1154298343405649980/Screenshot_57.png)


  ### Perhitungan dan Penentuan Protokol

  Lakukan perhitungan packet dari filter dan gambar diatas, kemudian penentuan protocol didapat dari percobaan filtering port yang bisa dilakukan hanya port UDP, sehingga jawaban yang kami dapatkan adalah **21 dan UDP**


  ### Flag 3

  ![No3-Flag](https://cdn.discordapp.com/attachments/773324309020147732/1154299161026506782/image.png)


  ## Soal Nomor 4

  Berapa nilai checksum yang didapat dari header pada paket nomor 130 ?


  ## Jawaban Nomor 4


  ### File pcap dan Pemilihan Packet

  Buka file soal4.pcapng kemudian pilih packet nomor 130

  ![No4-1](https://cdn.discordapp.com/attachments/773324309020147732/1154301186191671356/Screenshot_58.png)


  ### User Datagram Protocol

  Lihat pada bagian User Datagram Protocol, kemudian lihat nilai checksumnya

  ![No4-2](https://cdn.discordapp.com/attachments/773324309020147732/1154301610059649065/image.png)

  Didapatkan bahwa nilai checksumnya adalah **0x18e5**


  ### Kendala Nomor 4

  Kendala yang kami alami adalah kami berasumsi bahwa nilai yang nantinya menjadi jawaban adalah nilai dengan bentuk desimal sehingga kami selalu mengubah nilai checksum yang berbentuk heksadesimal menjadi bentuk desimal


  ## Soal Nomor 5

  Elshe menemukan suatu file packet capture yang menarik. Bantulah Elshe untuk menganalisis file packet capture tersebut.
    - Berapa banyak packet yang berhasil di capture dari file pcap tersebut ?
    - Port berapakah pada server yang digunakan untuk service SMTP ?
    - Dari semua alamat IP yang tercapture, IP berapakah yang merupakan public IP ?


  ## Jawaban Nomor 5


  ### File pcap

  Buka file soal5.pcapng dan urutkan packet berdasarkan nomornya secara _descending_

  ![No5-1](https://cdn.discordapp.com/attachments/773324309020147732/1154317337655267370/Screenshot_62.png)

  Didapatkan bahwa jumlah packet yang tercapture adalah **60**


  ### Filtering dan Transmission Control Protocol

  Masukkan filter `smtp` dan lihat Source Port pada bagian Transmission Control Protocol sebagai port yang digunakan oleh service SMTP pada server

  ![No5-2](https://cdn.discordapp.com/attachments/773324309020147732/1154318670416322560/Screenshot_63.png)

  Didapatkan bahwa Source Port yang digunakan adalah port **1470**


  ### IP Public


  ### Kendala Nomor 5

  Tidak bisa memasukkan jawaban karena tidak bisa menemukan password file zip untuk nc ke servernya. 


  ## Soal Nomor 6

  Seorang anak bernama Udin Berteman dengan SlameT yang merupakan seorang penggemar film detektif. sebagai teman yang baik, Ia selalu mengajak slamet untuk bermain valoranT bersama. suatu malam, terjadi sebuah hal yang tak terdUga. ketika udin mereka membuka game tersebut, laptop udin menunjukkan sebuah field text dan Sebuah kode Invalid bertuliskan "server SOURCE ADDRESS 7812 is invalid". ketika ditelusuri di google, hasil pencarian hanya menampilkan a1 e5 u21. jiwa detektif slamet pun bergejolak. bantulah udin dan slamet untuk menemukan solusi kode error tersebut.


  ## Jawaban Nomor 6


  ### Kendala Nomor 6

  Masih belum paham maksud soal, dan tidak cukup waktu ketika ingin mengerjakan pada saat praktikum modul 1


  ## Soal Nomor 7

  Berapa jumlah packet yang menuju IP 184.87.193.88 ?


  ## Jawaban Nomor 7


  ### File pcap dan Filtering 7

  Buka file soal6-9.pcapng dan masukkan filter `ip.dst == 184.87.193.88` sesuai dengan IP yang disediakan soal

  ![No7-1](https://cdn.discordapp.com/attachments/773324309020147732/1154304561390026783/Screenshot_59.png)


  ### Perhitungan jumlah Packet

  Hitung jumlah packet yang terlihar setelah dilakukan filtering tersebut. Sehingga jawaban yang kami temukan berjumlag **6 Packet**


  ### Flag 7

  Berikut merupakan flag yang kami dapatkan

  ![No7-Flag](https://cdn.discordapp.com/attachments/773324309020147732/1154304802117922886/image.png)


  ## Soal Nomor 8

  Berikan kueri filter sehingga wireshark hanya mengambil semua protokol paket yang menuju port 80! (Jika terdapat lebih dari 1 port, maka urutkan sesuai dengan abjad)


  ## Jawaban Nomor 8


  ### Filtering 8

  Untuk menjawab pertanyaan tersebut, kami langsung membuat filter yaitu `tcp.dstport == 80 || udp.dstport == 80` dimana berarti kita hanya akan menampilkan semua protokol paket yang menuju port 80, sesuai dengan ketentuan modul Jarkom.


  ### Flag 8

  Berikut merupakan flag yang kami dapatkan

  ![No8-Flag](https://cdn.discordapp.com/attachments/773324309020147732/1154306526538895420/image.png)


  ## Soal Nomor 9

  Berikan kueri filter sehingga wireshark hanya mengambil paket yang berasal dari alamat 10.51.40.1 tetapi tidak menuju ke alamat 10.39.55.34!


  ## Jawaban Nomor 9


  ### Filtering 9

  Untuk menjawab pertanyaan tersebut, kami langsung membuat filter yaitu ` ip.src == 10.51.40.1 && ip.dst != 10.39.55.34` dimana berarti kita hanya akan menampilkan semua paket yang berasal dari alamat 10.51.40.1 tetapi tidak menuju ke alamat 10.39.55.34, sesuai dengan ketentuan modul Jarkom.


  ### Flag 9

  Berikut merupakan flag yang kami dapatkan

  ![No9-Flag](https://cdn.discordapp.com/attachments/773324309020147732/1154307264883195965/image.png)


  ## Soal Nomor 10

  Sebutkan kredensial yang benar ketika user mencoba login menggunakan Telnet


  ## Jawaban Nomor 10


  ### File pcap dan Filtering 10

  Buka file soal10.pcapng dan masukkan filter `telnet`

  ![No10-1](https://cdn.discordapp.com/attachments/773324309020147732/1154308015151915048/Screenshot_60.png)


  ### Pemilihan Packet dan Follow

  Pilih salah satu packet kemudian follow dengan mode TCP Stream

  ![No10-2](https://cdn.discordapp.com/attachments/773324309020147732/1154308596323061770/Screenshot_61.png)


  ### Informasi yang Didapat

  Maka akan muncul informasi Username dan Password yang dapat digunakan sebagai kredensial ketika user mencoba untuk login

  ![No10-3](https://cdn.discordapp.com/attachments/773324309020147732/1154309011227816006/image.png)

  Ditemukan bahwa usernamnya adalah **Dhafin** dan passwordnya adalah **kesayangank0k0**


  ### Kendala Nomor 10

  Kami tidak tahu kenapa username yang muncul setelah difollow berisikan alphabet yang double atau terulang 2 kali, sehingga kami mengira usernamenya adalah ddhhaaffiinn


  

  


