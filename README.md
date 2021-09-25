# Jarkom-Modul-1-T11-2021

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
1. Untuk menemuka username dan password yang login pada FTP Server tersebut kami menggunakan filter ```ftp.request.command eq "USER" or ftp.request.command eq "PASS"``` dan didapatkan Username adalah secretuser dan passwordnya adalah aku.pengen.pw.aja seperti berikut <br> <img src="/ss/10.jpg">

## Soal 7
Ada 500 file zip yang disimpan ke FTP Server dengan nama 0.zip, 1.zip, 2.zip, ..., 499.zip. Simpan dan Buka file pdf tersebut. (Hint = nama pdf-nya "Real.pdf")

### Jawaban
1. Pertama kami mencari file yang berisi "Real.pdf" dengan menggunakan filter ```frame contains "Real.pdf"``` dan ketika sudah mendapatkan hasilnya langsung melakukan follow tcp <br> <img src="/ss/11.png">
2. Selanjutnya setelah di follow tcp, show data tersebut diubah menjadi show data as raw dan file nya di save dengan nama 201.zip sebagai gambar berikut <br> <img src="/ss/12.png">
3. Setelah itu file nya dibuka dan mendapatkan hasil seperti gambar berikut <br> <img src="/ss/13.png">

## Soal 8
Cari paket yang menunjukan pengambilan file dari FTP tersebut!

### Jawaban
1. Untuk mencari pengambilan file tersebut kami menggunakan command ```ftp.request.command == STOR``` seperti berikut <br> <img src="/ss/14.png">

### Soal 9
Dari paket-paket yang menuju FTP terdapat inidkasi penyimpanan beberapa file. Salah satunya adalah sebuah file berisi data rahasia dengan nama "secret.zip". Simpan dan buka file tersebut!

### Jawaban
1. Pertama kami mencari file yang bernama "secret.zip' dengan menggunakan command ```frame contains "secret.zip"``` seperti gambar berikut <br> <img src="/ss/15.png">
2. Setelah kami mendapatkan info yang ingin di cari selanjutanya kami melakukan follow tcp dan mengubah show data menjadi raw dan stream diubah menjadi 10 <br> <img src="/ss/16.png">
3. Selanjutnya file nya kami simpan. <br> <img src="/ss/17.png">

## Soal 10
Selain itu terdapat "history.txt" yang kemungkinan berisi history bash server tersebut! Gunakan isi dari "history.txt" untuk menemukan password untuk membuka file rahasia yang ada di "secret.zip"!

### Jawaban
1. Pertama kami menggunakan command ```frame contains "secret.zip"``` dan melakukan follow tcp kepada info yang memiliki ```STOR = "history.txt"``` seperti berikut <br> <img src="/ss/18.png">
2. Sesudah melakukan follow tcp password tersebut akan terlihat jika data tersebut show data as ASCII dan stream diubah menjadi 11 <br> <img src="/ss/19.png">
3. Setelah sudah mendapatkan password tersebut, file yang terkunci bisa dibuka dengan password yang didapatkan dan isi dari file tersebut adalah sebagai berikut <br> <img src="/ss/20.png">

## Soal 11
Filter sehingga wireshark hanya mengambil paket yang berasal dari port 80! 

### Jawaban
1.  Untuk melakukan filter yang berasal dari port 80 kami menggunakan command ```tcp.srcport == 80``` maka akan otomastis menampilkan paket paket data. Seperti gambar berikut : <br> ![Screenshot (2733)](https://user-images.githubusercontent.com/71550384/134761255-bd9f0197-c461-4558-b014-6049a4b4e3b0.png)

## Soal 12
Filter sehingga wireshark hanya mengambil paket yang mengandung port 21!

### Jawaban 
1. Untuk melakukan filter paket yang mengandung port 21 kami menggunakan command ```tcp.port == 21``` maka akan otomatis menampilkan paket-paket data. Seperti pada gambar berikut : <br> ![Screenshot (2737)](https://user-images.githubusercontent.com/71550384/134761625-50322670-750a-43c5-92a3-ee40174edb88.png)

## Soal 13
Filter sehingga wireshark hanya menampilkan paket yang menuju port 443!

### Jawaban
1. Untuk melakukan filter paket data yang menuju port 443 kami menggunakan command ```tcp.dstport == 443``` maka akan otomatis menampilkan paket-paket data tersebut. Seperti gambar berikut : <br> ![Screenshot (2734)](https://user-images.githubusercontent.com/71550384/134762143-13c9e42c-ea57-4462-bcae-71e84e8815d0.png)

## Soal 14
Filter sehingga wireshark hanya mengambil paket yang tujuannya ke kemenag.go.id!

### Jawaban 
1. Untuk mengambil paket yang menuju alamat tersebut kami menggunakan command ```http.host==kemenag.go.id``` maka akan otomatis menampilkan paket-paket data tersebut. Seperti gambar berikut : <br> ![Screenshot (2735)](https://user-images.githubusercontent.com/71550384/134762234-48398d8c-8369-42b0-b992-037436dcac04.png)

## Soal 15
Filter sehingga wireshark hanya mengambil paket yang berasal dari ip kalian!

### Jawaban
1. Untuk mengambil paket yang berasal dari alamat ip kami menggunakan command ```ip.src_host eq 192.168.100.7``` maka akan otomatis menampilkan paket-paket data tersebut. Seperti gamabr berikut : <br> ![Screenshot (2736)](https://user-images.githubusercontent.com/71550384/134762336-1817951c-786e-4532-aed6-eb4883d84b2a.png)


## Kendala
Kendala kami dalam mengerjakan praktikum ini adalah :
1. Ada beberapa filter yang belum kami ketahui, sehingga harus mencoba-coba dahulu
2. Ketika menggunakan follow tcp stream ada beberapa setting yang belum kami ketahui, sehingga awalnya kami agak tersendat di soal-soal yang perlu follow tcp stream
