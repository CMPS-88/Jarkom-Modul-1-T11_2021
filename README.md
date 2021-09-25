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

## Soal 6
Cari username dan password ketika melakukan login ke FTP Server!

### Jawaban
1. Untuk menemuka username dan password yang login pada FTP Server tersebut kami menggunakan filter ```ftp.request.command eq "USER" or ftp.request.command eq "PASS"``` dan didapatkan Username adalah secretuser dan passwordnya adalah aku.pengen.pw.aja seperti berikut

## Soal 7
Ada 500 file zip yang disimpan ke FTP Server dengan nama 0.zip, 1.zip, 2.zip, ..., 499.zip. Simpan dan Buka file pdf tersebut. (Hint = nama pdf-nya "Real.pdf")

### Jawaban
1. Pertama kami mencari file yang berisi "Real.pdf" dengan menggunakan filter ```frame contains "Real.pdf"``` dan ketika sudah mendapatkan hasilnya langsung melakukan follow tcp
2. Selanjutnya setelah di follow tcp, show data tersebut diubah menjadi show data as raw dan file nya di save dengan nama 201.zip sebagai gambar berikut
3. Setelah itu file nya dibuka dan mendapatkan hasil seperti gambar berikut

## Soal 8
Cari paket yang menunjukan pengambilan file dari FTP tersebut!

### Jawaban
1. Untuk mencari pengambilan file tersebut kami menggunakan command ```ftp.request.command == STOR``` seperti berikut

### Soal 9
Dari paket-paket yang menuju FTP terdapat inidkasi penyimpanan beberapa file. Salah satunya adalah sebuah file berisi data rahasia dengan nama "secret.zip". Simpan dan buka file tersebut!

### Jawaban
1. Pertama kami mencari file yang bernama "secret.zip' dengan menggunakan command ```frame contains "secret.zip"``` seperti gambar berikut
2. Setelah kami mendapatkan info yang ingin di cari selanjutanya kami melakukan follow tcp dan mengubah show data menjadi raw dan stream diubah menjadi 10
3. Selanjutnya file nya kami simpan.

## Soal 10
Selain itu terdapat "history.txt" yang kemungkinan berisi history bash server tersebut! Gunakan isi dari "history.txt" untuk menemukan password untuk membuka file rahasia yang ada di "secret.zip"!

### Jawaban
1. Pertama kami menggunakan command ```frame contains "secret.zip"``` dan melakukan follow tcp kepada info yang memiliki ```STOR = "history.txt"``` seperti berikut
2. Sesudah melakukan follow tcp password tersebut akan terlihat jika data tersebut show data as ASCII dan stream diubah menjadi 11
3. Setelah sudah mendapatkan password tersebut, file yang terkunci bisa dibuka dengan password yang didapatkan dan isi dari file tersebut adalah sebagai berikut

## Kendala
Kendala kami dalam mengerjakan praktikum ini adalah :
1. Ada beberapa filter yang belum kami ketahui, sehingga harus mencoba-coba dahulu
2. Ketika menggunakan follow tcp stream ada beberapa setting yang belum kami ketahui, sehingga awalnya kami agak tersendat di soal-soal yang perlu follow tcp stream
