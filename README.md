# Jaringan Komputer 2022
Kelas Jaringan Komputer E - Kelompok E12
### Nama Anggota
- Azzura Mahendra Putra Malinus (5025201211)
- Amanda Salwa Salsabila (5025201172)
- Michael Ariel Manihuruk (5025201158)

## Modul 1
### Soal 1
Sebutkan web server yang digunakan pada "monta.if.its.ac.id"! 
### Penjelasan
Untuk mengetahui ip sebuah web server, buka cmd dan enter command ping <web server> <br />
ping monta.if.its.ac.id <br />
<img width="416" alt="image" src="https://user-images.githubusercontent.com/90702710/192083347-bfa55ae8-99b7-4cbb-94bf-e4ff02a96c99.png"> <br />
Diketahui ip address dari monta.if.its.ac.id adalah 103.94.189.5 <br/>
Berikut adalah ekspresi untuk mencari paket yang berasal dan menuju monta.if.its.ac.id dengan protokol http pada filter
(ip.src == 103.94.189.5 || ip.dst == 103.94.189.5) && http <br />
<img width="745" alt="image" src="https://user-images.githubusercontent.com/90702710/192083335-9f7df238-a350-4e6f-91ab-ab6a7f18c34d.png"> <br />
Dengan melihat detail salah satu paket, misal pada paket yang ditandai tanda panah, dapat diketahui bahwa web server yang digunakan adalah nginx/1.10.3
  
### Soal 2
Ishaq sedang bingung mencari topik ta untuk semester ini , lalu ia datang ke website monta dan menemukan detail topik pada website “monta.if.its.ac.id” , judul TA apa yang dibuka oleh ishaq ?
### Penjelasan
Langkah pertama adalah memfilter paket yang berasal dari protokol http untuk mencari file html dari detail topik dengan menggunakan eskpresi http pada filter <br />
<img width="661" alt="image" src="https://user-images.githubusercontent.com/90702710/192083449-83436a94-29e6-458a-8004-dbd3f7ea899c.png"> <br />
Setelah ditemukan paketnya, selanjutnya adalah mengekspor paket tersebut dan menyimpan file htmlnya. Hasil yang diperoleh adalah sebagai berikut. <br />
<img width="657" alt="image" src="https://user-images.githubusercontent.com/90702710/192083474-139c32e5-f5b8-41c1-a437-d39a8af25b7c.png"> <br />
Judul yang dibuka adalah Evaluasi unjuk kerja User Space Filesystem (FUSE).
  
### Soal 3
Filter sehingga wireshark hanya menampilkan paket yang menuju port 80!
### Penjelasan
Yang harus dilakukan pertama adalah melihat semua paket yang menuju dan berasal dari port 80 dengan menggunakan ekspresi tcp.port == 80 pada filter <br />
<img width="794" alt="image" src="https://user-images.githubusercontent.com/90702710/192083583-0c20bdc7-f378-4a96-9ccb-78c136f1d107.png"> <br />
Diketahui bahwa ip address asal adalah 192.168.0.27, sehingga ekpresi sebelumnya berubah menjadi paket yang menuju/berasal dari port 80 dan  yang berasal dari ip 192.168.0.27. <br/>
tcp .port == 80 && ip.src == 192.168.0.27 <br/>
<img width="803" alt="image" src="https://user-images.githubusercontent.com/90702710/192083618-836f73b8-3857-4761-92e7-64dd811a4f14.png">

### Soal 4

### Penjelasan

### Soal 5

### Penjelasan

### Soal 6

### Penjelasan

### Soal 7
Filter sehingga wireshark hanya mengambil paket yang berasal dari ip kalian!
### Penjelasan
Kita perlu menampilkan paket yang berasal ip kita sendiri maka dari itu kita membuka capture wifi <br/>
<img width="532" alt="image" src="https://user-images.githubusercontent.com/90702710/192084504-1d92c413-b740-4abb-a8e4-c588def11aa8.png"> <br/>
Untuk mengetahui ip kita, buka cmd dan enter command ipconfig. Pilih IPV4 Address yang ada pada Wireless LAN Adapter Wi-Fi <br/>
<img width="709" alt="image" src="https://user-images.githubusercontent.com/90702710/192084485-d224cb97-1748-48b7-91e3-08e0f9cd694c.png"> <br/>
Setelah didapatkannya ip address, ambil paket yang berasal dari ip address kita dengan menggunakan ekspresi `ip.src == 192.168.211.60` dimana ip yang digunakan adalah ip kita sendiri <br/>
<img width="708" alt="image" src="https://user-images.githubusercontent.com/90702710/192084437-a958298f-05ff-4d6a-b553-109b8298d694.png">

### Soal 8
Telusuri aliran paket dalam file .pcap yang diberikan, cari informasi berguna berupa percakapan antara dua mahasiswa terkait tindakan kecurangan pada kegiatan praktikum. Percakapan tersebut dilaporkan menggunakan protokol jaringan dengan tingkat keandalan yang tinggi dalam pertukaran datanya sehingga kalian perlu menerapkan filter dengan protokol yang tersebut.
### Penjelasan
Caranya adalah dengan menggunakan ekspresi <br/> 
`tcp.stream eq 12` <br/> 
<img width="448" alt="image" src="https://user-images.githubusercontent.com/90702710/192085089-4076fc5a-db19-4022-ae5a-2fc320fdcc35.png"> <br/> 
`tcp.stream eq 41` <br/> 
<img width="445" alt="image" src="https://user-images.githubusercontent.com/90702710/192085109-91c1d0cd-b285-46b1-8545-f21e989dab17.png"> <br/> 
`tcp.stream eq 90`<br/> 
<img width="443" alt="image" src="https://user-images.githubusercontent.com/90702710/192085123-6fbc496b-db9a-4849-8dfc-6faaeb222ae3.png"> <br/> 
Dapat diketahui bahwa terdapat 3 percakapan antara dua mahasiswa terkait tindakan kecurangan pada kegiatan praktikum

### Soal 9
Terdapat laporan adanya pertukaran file yang dilakukan oleh kedua mahasiswa dalam percakapan yang diperoleh, carilah file yang dimaksud! Untuk memudahkan laporan kepada atasan, beri nama file yang ditemukan dengan format [nama_kelompok].des3 dan simpan output file dengan nama “flag.txt”
### Penjelasan
Dari percakapan pada nomor 8, dapat diketahui bahwa kedua mahasiswa tersebut sedang bertukar file salt, maka dari itu kita dapat melakukan display filter dengan keyword “salt” dengan menggunakan ekspresi `tcp contains "Salt"` atau bisa juga dengan menggunakan ekspresi `tcp.port == 9002` (clue pada percakapan pertama) <br/>
<img width="960" alt="image" src="https://user-images.githubusercontent.com/90702710/192085627-79b28e35-21bc-4f60-bd5d-113a1e5a5061.png"> <br/>
<img width="958" alt="image" src="https://user-images.githubusercontent.com/90702710/192085635-deabf95c-8b9e-495d-b948-f5b479bdc4c8.png"> <br/>
Maka, didapatkanlah file Salt yang masih terencrypt <br/>
<img width="474" alt="image" src="https://user-images.githubusercontent.com/90702710/192085560-64789834-1cfd-42b8-b9ef-541303164f96.png"> <br/>
Untuk mendecrpyt file tersebut, ubah data menjadi raw dengan cara berikut, kemudian save as E12.des3 <br/>
<img width="262" alt="image" src="https://user-images.githubusercontent.com/90702710/192085693-6c4ccad6-0ee8-4e09-a508-5822fcb892cb.png"> <br/>
Pada folder yang terdapat file .des3 tersebut, lakukan `git bash here` dengan command `openssl des3 -d -salt -in e12.des3 -out flag.txt -k nakano` (penjelasan password akan diberikan pada nomor 10) <br/>
<img width="658" alt="image" src="https://user-images.githubusercontent.com/90702710/192085770-956c19a9-f3fa-4234-9781-0427383eacc8.png"> <br/>
Outputnya berupa file flag.txt yang berisikan: <br/>
<img width="483" alt="image" src="https://user-images.githubusercontent.com/90702710/192085802-6c856c07-8554-42b1-bd7e-6dcfd976b551.png">

### Soal 10
Temukan password rahasia (flag) dari organisasi bawah tanah yang disebutkan di atas!
### Penjelasan
Isi flag.txt : JaRkOm2022{8uK4N_CtF_k0k_h3h3h3} <br/>
Password untuk openssl : nakano <br/>
<br/>
Kenapa passwordnya nakano? Karena, berdasarkan 3 percakapan yang sudah dilampirkan pada nomor 8, passwordnya berdasarkan nama dari karakter anime yang kembar lima. Anime tersebut adalah Gotoubun no Hanayome atau The Quintessential Quintuplets. Dan diberikan clue bahwa "kita tidak harus melihat perbedaannya" maka nama yang diambil adalah nama yang sama pada kelima karakter tersebut, yakni family namenya 'nakano'

## Kendala
### Soal 8
Pada saat praktikum, terdapat sedikit kendala dimana follow stream yang dilakukan masih secara manual, sehingga pengecekan dilakukan secara satu persatu. Hal tersebut menyita cukup banyak waktu
