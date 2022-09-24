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
