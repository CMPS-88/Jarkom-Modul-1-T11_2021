# Jarkom-Modul1-T11-2021

Nama Anggota | NRP
------------------- | --------------		
Justin Alfonsius Sitanggang | 05311840000043
Daniel Evan | 05311940000016
Calvin Manuel | 05311940000049

## Soal 1
Sebutkan webserver yang digunakan pada ```ichimarumaru.tech```!

### Jawaban
1. Pertama untuk melakukan filter ke semua packet yang mengandung website ```ichimarumaru.tech``` kami menggunakan filter berikut ini ```http.host eq "ichimarumaru.tech"``` dan didapatkan hasil sebagai berikut.
2. Selanjutnya kita follow TCP Stream dari salah satu record, dengan menggunakan filter ```follow tcp stream (tcp.stream eq 12)``` dan didapati hasil sebagai berikut.
3. Dan didapati untuk servernya menggunakan ```nginx/1.18.0 (Ubuntu)```

## Soal 2
Temukan paket dari web-web yang menggunakan basic authentication method!

### Jawaban
1. Untuk soal ini kami menggunakan filter ```http.authbasic``` dan didapatkan hasil sebagai berikut.

## Soal 3
Ikuti perintah di ```basic.ichimarumaru.tech!``` Username dan password bisa didapatkan dari file .pcapng!

### Jawaban
1. Pertama kami menggunakan filter ```http.host eq "basic.ichimarumaru.tech"``` untuk mendapatkan packet yang mengandung website ```basic.ichimarumaru.tech```
2. Kemudian kami melihat pada bagian Hypertext Transfer Protocol, bagian Authorization dan mendapatkan hasil ```kuncimenujulautan:tQKEJFbgNGC1NCZlWAOjhyCOm6o3xEbPkJhTciZN```
3. Setelah itu kami berhasil login dan memasukkan urutan kabel T568A
