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
    - [File pcap dan Filtering](#1-langkah-1)
    - [Packet dengan Request STOR](#1-langkah-2)
    - [Detail TCP Seuquence dan Acknowledge Number](#1-langkah-3)
    - [Seuquence dan Acknowledge Number Packet Response](#1-langkah-4)
    - [Flag](#1-langkah-5)
  - [Soal Nomor 2](#soal-nomor-2)
  - [Jawaban Nomor 2](#jawaban-nomor-2)
    - [File pcap dan Filtering](#2-langkah-1)
    - [Pemilihan packet dan Server yang digunakan](#2-langkah-2)
    - [Flag](#2-langkah-3)
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

