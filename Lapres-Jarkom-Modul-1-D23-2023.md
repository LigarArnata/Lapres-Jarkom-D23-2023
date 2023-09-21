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
    - [File pcap dan Filtering](#file-pcap-dan-filtering)
    - [Detail TCP Seuquence dan Acknowledge Number](#Detail-TCP-Seuquence-dan-Acknowledge-Number)
    - [Seuquence dan Acknowledge Number Packet Response](#Seuquence-dan-Acknowledge-Number-Packet-Response)
    - [Flag](#flag-1)
  - [Soal Nomor 2](#soal-nomor-2)
  - [Jawaban Nomor 2](#jawaban-nomor-2)
    - [File pcap dan Filtering](#file-pcap-dan-filtering)
    - [Pemilihan packet dan Server yang digunakan](#pemilihan-packet-dan-server-yang-digunakan)
    - [Flag](#flag-2)
  - [Soal Nomor 3](#soal-nomor-3)
  - [Jawaban Nomor 3](#jawaban-nomor-3)
    - [File pcap dan Filtering](#3-langkah-1)
    - [Perhitungan dan Penentuan Protokol](#3-langkah-2)
    - [Flag](#3-langkah-3)
  - [Soal Nomor 4](#soal-nomor-4)
  - [Jawaban Nomor 4](#jawaban-nomor-4)
    - [File pcap dan Pemilihan Packet](#4-langkah-1)
    - [User Datagram Protocol](#4-langkah-2)
    - [Kendala](#4-kendala)
  - [Soal Nomor 5](#soal-nomor-5)
  - [Jawaban Nomor 5](#jawaban-nomor-5)
    - [Kendala](#5-kendala)
  - [Soal Nomor 6](#soal-nomor-6)
  - [Jawaban Nomor 6](#jawaban-nomor-6)
    - [Kendala](#6-kendala)
  - [Soal Nomor 7](#soal-nomor-7)
  - [Jawaban Nomor 7](#jawaban-nomor-7)
    - [File pcap dan Filtering](#7-langkah-1)
    - [Perhitungan jumlah packet](#7-langkah-2)
    - [Flag](#7-langkah-3)
  - [Soal Nomor 8](#soal-nomor-8)
  - [Jawaban Nomor 8](#jawaban-nomor-8)
    - [Filtering](#8-langkah-1)
    - [Flag](#8-langkah-2)
  - [Soal Nomor 9](#soal-nomor-9)
  - [Jawaban Nomor 9](#jawaban-nomor-9)
    - [Filtering](#9-langkah-1)
    - [Flag](#9-langkah-2)
  - [Soal Nomor 10](#soal-nomor-10)
  - [Jawaban Nomor 10](#jawaban-nomor-10)
    - [File pcap dan Filtering](#10-langkah-1)
    - [Pemilihan Packet dan Follow](#10-langkah-2)
    - [Informasi yang Didapat](#10-langkah-3)
    - [Kendala](#10-kendala)

  ## Soal Nomor 1

  User melakukan berbagai aktivitas dengan menggunakan protokol FTP. Salah satunya adalah mengunggah suatu file.
    - Berapakah sequence number (raw) pada packet yang menunjukkan aktivitas tersebut? 
    - Berapakah acknowledge number (raw) pada packet yang menunjukkan aktivitas tersebut? 
    - Berapakah sequence number (raw) pada packet yang menunjukkan response dari aktivitas tersebut?
    - Berapakah acknowledge number (raw) pada packet yang menunjukkan response dari aktivitas tersebut?

  ## Jawaban Nomor 1


  ### File pcap dan Filtering

  Buka File soal1.pcapng dan masukkan filter `ftp contains "STOR"` pada display filter. Filter tersebut hanya akan menampilkan packet dengan protocol FTP dan memiliki       
  request perintah STOR atau yang memiliki keterangan sebagai packet yang Meng-upload file ke FTP server

  ![No1-1](https://cdn.discordapp.com/attachments/773324309020147732/1154289009980346438/image.png)


  ### Detail TCP Sequence dan Acknowledge Number

  Cek pada bagian Transmission Control Protocol dari packet tersebut dan lihat Sequence dan Acknowledge Number

  ![No1-2](https://cdn.discordapp.com/attachments/773324309020147732/1154290301670801408/image.png)

  Ditemukan bahwa Sequence dan Acknowledge Number adalah 258040667 dan 1044861039


  ### Sequence dan Acknowledge Number Packet Response

  Untuk melihat Sequence dan Acknowledge Number dari Packet Responsenya maka hapus `contains "STOR"` dari filter sehingga menyisakan `ftp` dan pilih packet yang tepat     
  berada dibawah packet yang memiliki request perintah STOR tadi, kemudian dengan cara yang sama pada bagian Transmission Control Protocol lihat Sequence dan Acknowledge 
  Number

  ![No1-3](https://cdn.discordapp.com/attachments/773324309020147732/1154291658624618536/image.png)

  Ditemukan bahwa Sequence dan Acknowledge Number adalah 1044861039 dan 258040696


  ### Flag-1

  Berikut merupakan flag yang kami dapatkan

  ![No1-Flag](https://cdn.discordapp.com/attachments/773324309020147732/1154292297161244672/image.png)

  ## Soal Nomor 2

  Sebutkan web server yang digunakan pada portal praktikum Jaringan Komputer!

  ## Soal Nomor 2

  ### File pcap dan Filtering
  ### Pemilihan packet dan Server yang digunakan
  ### Flag-2


