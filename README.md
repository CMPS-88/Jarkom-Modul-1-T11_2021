# Jarkom-Modul1-T11-2021

Nama Anggota | NRP
------------------- | --------------		
Justin Alfonsius Sitanggang | 05311840000043
Daniel Evan | 05311940000016
Calvin Manuel | 05311940000049

## Soal 1
Sebutkan webserver yang digunakan pada ```ichimarumaru.tech```!

### Jawaban
1. Pertama untuk melakukan filter ke semua packet yang mengandung website ```ichimarumaru.tech``` kami menggunakan filter berikut ini ```http.host eq "ichimarumaru.tech"``` dan didapatkan hasil sebagai berikut. <br> <img src="/ss/1.JPG">
2. Selanjutnya kita follow TCP Stream dari salah satu record, dengan menggunakan filter ```follow tcp stream (tcp.stream eq 12)``` dan didapati hasil sebagai berikut. <br> <img src="/ss/2.JPG">
3. Dan didapati untuk servernya menggunakan ```nginx/1.18.0 (Ubuntu)```<br> <img src="/ss/3.JPG">

## Soal 2
Temukan paket dari web-web yang menggunakan basic authentication method!

### Jawaban
1. Untuk soal ini kami menggunakan filter ```http.authbasic``` dan didapatkan hasil sebagai berikut. <br> <img src="/ss/4.JPG">

## Soal 3
Ikuti perintah di ```basic.ichimarumaru.tech!``` Username dan password bisa didapatkan dari file .pcapng!

### Jawaban
1. Pertama kami menggunakan filter ```http.host eq "basic.ichimarumaru.tech"``` untuk mendapatkan packet yang mengandung website ```basic.ichimarumaru.tech```<br> <img src="/ss/5.JPG">
2. Kemudian kami melihat pada bagian Hypertext Transfer Protocol, bagian Authorization dan mendapatkan hasil ```kuncimenujulautan:tQKEJFbgNGC1NCZlWAOjhyCOm6o3xEbPkJhTciZN```
3. Setelah itu kami berhasil login dan memasukkan urutan kabel T568A <br> <img src="/ss/6.JPG">

## Soal 4
Temukan paket mysql yang mengandung perintah query select!

### Jawaban
1. Untuk menemukan packet yang mengandung perintah query select kami menggunakan filter ```mysql.query matches "select"``` dan didapatkan hasil sebagai berikut <br> <img src="/ss/7.JPG">

## Soal 5
Login ke ```portal.ichimarumaru.tech``` kemudian ikuti perintahnya! Username dan password bisa didapat dari query insert pada table users dari file .pcap!

### Jawaban
1. Untuk mendapatkan packet dengan perintah query insert kami menggunakan filter ```mysql.query matches "insert"``` dan didapatkan hasil sebagai berikut <br> <img src="/ss/8.JPG">
2. kami mendapatkan username:```"akakanomi"``` pass:```"pemisah4lautan"```
3. Setelah berhasil login kami menyebutkan konfigurasi kabel T568B <br> <img src="/ss/9.JPG">



## Kendala
Kendala kami dalam mengerjakan praktikum ini adalah :
1. Ada beberapa filter yang belum kami ketahui, sehingga harus mencoba-coba dahulu
2. Ketika menggunakan follow tcp stream ada beberapa setting yang belum kami ketahui, sehingga awalnya kami agak tersendat di soal-soal yang perlu follow tcp stream
