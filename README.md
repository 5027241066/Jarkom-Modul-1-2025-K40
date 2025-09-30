# Laporan Resmi Jarkom-Modul-1-2025-K40

## Anggota Kelompok

| No | Nama                   | NRP         |
|----|------------------------|-------------|
| 1  | Ahmad Yafi Ar Rizq | 5027241066  |
| 2  | Mohammad Abyan Ranuaji     | 5027241106  |

## Soal 1
Untuk mempersiapkan pembuatan entitas selain mereka, Eru yang berperan sebagai Router membuat dua Switch/Gateway. Dimana Switch 1 akan menuju ke dua Ainur yaitu Melkor dan Manwe. Sedangkan Switch 2 akan menuju ke dua Ainur lainnya yaitu Varda dan Ulmo. Keempat Ainur tersebut diberi perintah oleh Eru untuk menjadi Client.
<img width="842" height="641" alt="Image" src="https://github.com/user-attachments/assets/bd38db14-ed1b-4872-9e21-368150fdcf06" />

## Soal 2
Untuk menghubungkan eru ke internet, kita dapat menyambungkan client Eru ke NAT dan mengubah configure Eru menjadi:

<img width="499" height="162" alt="Image" src="https://github.com/user-attachments/assets/91861cfd-644d-48b9-b2ad-8a05307f1088" />

Untuk membuktikan kalau Eru sudah terhubung dengan internet, kita dapat melakukan ping kepada suatu situs seperti youtube.com, google.com, dll.

<img width="1244" height="159" alt="Image" src="https://github.com/user-attachments/assets/c70368fd-2582-4628-ab1e-5508d88b6d5e" />

## Soal 3
Disini kita sudah berhasil menyambungkan setiap client satu sama lain.

<img width="809" height="447" alt="Image" src="https://github.com/user-attachments/assets/6ead7dff-b250-4e8c-9dd5-4bf5d2919515" />

## Soal 4
Kita dapat memastikan setiap client tersebut dapat terhubung dengan internet melalui configure masing-masing client dengan menambahkan:

<img width="561" height="189" alt="Image" src="https://github.com/user-attachments/assets/b4f73143-4ee7-452e-9495-4071a5779a1f" />

Di setiap client. Selanjutnya kita akan menggunakan command “iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE -s 192.231.0.0/16” dan melihat bagian seperti foto berikut:

<img width="924" height="182" alt="Image" src="https://github.com/user-attachments/assets/73f08745-dadc-4120-a806-b9c78535c04f" />

Jika sudah, kita pindah ke terminal Melkor dan melakukan command seperti dibawah agar client ini dapat menyambung ke internet.

<img width="1239" height="293" alt="Image" src="https://github.com/user-attachments/assets/d118c609-6a37-4a0d-a099-058a3b5f6a2d" />

Kita dapat melakukan hal yang sama dengan client lain agar semua client bisa connect dengan internet.

## Soal 5
Kita dapat menambahkan command seperti berikut pada file /root/.bashrc di bagian paling bawah agar konfigurasi tidak hilang.

<img width="1236" height="87" alt="Image" src="https://github.com/user-attachments/assets/8680d09f-ac16-446d-926f-fb55270a651d" />

## Soal 6
Pertama, kita dapat melakukan klik kanan pada link yang menyambungkan switch1 dengan manwe, lakukan start capture -> start wireshark. Disini, kita menyimpan file traffic.sh yang diberikan oleh soal kedalam terminal Manwe, berikan permission dan run file shell tersebut.

Command yang digunakan untuk memfilter yaitu “ip.addr == 10.15.43.32”. Hasil yang didapatkan seperti berikut:

<img width="1245" height="465" alt="Image" src="https://github.com/user-attachments/assets/6c4a7b8e-26a2-4911-897b-16949584cac2" />

## Soal 7
Langkah selanjutnya kita dapat melakukan command “nano /etc/vsftpd.conf” pada terminal Eru dan menambahkan beberapa line berikut

<img width="1221" height="392" alt="Image" src="https://github.com/user-attachments/assets/91439dc2-bf2b-47ee-acaf-c210bb75edbe" />

Selanjutnya, kita akan membuat 2 folder baru dengan menggunakan command “mkdir -p /srv/ftp/shared” di terminal Eru.

Kita membuat folder khusus untuk FTP yaitu “mkdir -p /srv/ftp/shared” dan memasukkan user serta password dengan command “useradd --home /srv/ftp/shared ainur” dengan permission “chown\ ainur:ainur /srv/ftp/shared” untuk read & write. Lakukan hal yang sama untuk user melkor tetapi tanpa permission karena user ini tidak akan bisa login.

Tambahkan nama melkor ke dalam file vsftpd.userlist agar aksesnya ditolak oleh FTP server.

<img width="887" height="332" alt="Image" src="https://github.com/user-attachments/assets/42981274-a54d-45a8-abdc-d03fe5ace4ca" />

Kita akan coba test ini dengan pergi ke terminal bebas, disini kita gunakan terminal ulmo, buat suatu file random seperti ini:
```
echo "ini buat ngejawab soal nomor 7" > soal7.txt
```
Lalu masuk ke ftp dengan command “ftp 192.231.2.1” disini kita bisa mencoba login dan melihat perbedaan output melkor dengan ainur.

<img width="865" height="487" alt="Image" src="https://github.com/user-attachments/assets/1921ee5a-f8e1-43cf-b61a-dec8ddb597c9" />

<img width="708" height="283" alt="Image" src="https://github.com/user-attachments/assets/1a7b7b34-d3c6-4f5b-b894-7ef166cb344d" />

## Soal 8
Pertama, kita harus klik kanan pada link yang menyambungkan olmo dengan switch2, lalu terminal ulmo mendownload terlebih dahulu untuk file zip tersebut. Login kembali menggunakan command “ftp 192.231.2.1” dan login sebagai ainur.

Selanjutnya kita dapat melakukan “put soal8.zip” untuk melihat secara langsung apa yang terjadi di wireshark.

<img width="1241" height="310" alt="Image" src="https://github.com/user-attachments/assets/a8c79d89-1ce6-4734-8f74-b18d5d2a749e" />

Gunakan filter “ftp” untuk melihat proses yang terjadi di lingkungan ftp saja seperti foto berikut:

<img width="1243" height="387" alt="Image" src="https://github.com/user-attachments/assets/303acd02-1e23-498f-b14e-9baa53d06470" />



## Soal 14
Setelah gagal mengakses FTP, Melkor melancarkan serangan brute force terhadap  Manwe. Analisis file capture yang disediakan dan identifikasi upaya brute force Melkor. IP: 10.15.43.32 3401

Pertama kita melakukan netcat pada ip yang diberikan

<img width="354" height="123.5" alt="Screenshot 2025-09-30 010528" src="https://github.com/user-attachments/assets/637cbb04-0f38-41a3-9f4c-c1d1ac70e74d" />

Kemudian akan muncul pertanyaan "How many packets are recorded in the pcapng file?"
Ketika membuka file di wireshark akan terlihat terdapat 500358 packets

<img width="141" height="37" alt="Screenshot 2025-09-30 010611" src="https://github.com/user-attachments/assets/3a464297-3c1a-41d5-8276-ba3a3bce8a7c" />

Kemudian akan muncul pertanyaan baru. "What are the user that successfully logged in?"

<img width="354 " height="99.48" alt="Screenshot 2025-09-30 010623" src="https://github.com/user-attachments/assets/048eaa28-8e6f-473c-b992-91f5c6b9c497" />

Pada pertanyaan itu saya memeriksa satu per satu setiap tcp.stream. Setelah mencoba selama 45 menit, saya menemukan user yang successfully logged in yaitu `n1enna` dan passwordnya `y4v4nn4_k3m3nt4r1`
<img width="503" height="277" alt="Screenshot 2025-09-30 011520" src="https://github.com/user-attachments/assets/50e0e9ab-155e-4380-b5cf-0e23d510c1dd" />
<img width="1357" height="763" alt="Screenshot 2025-09-30 011456" src="https://github.com/user-attachments/assets/dd6c40af-3335-4edd-b586-bd01e71ce21d" />
