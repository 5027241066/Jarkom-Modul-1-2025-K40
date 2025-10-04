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

## Soal 9
Di terminal eru, Pertama kita akan mengubah permission user ainur dengan menggunakan command “chmod a-w /srv/ftp/shared” agar user ini hanya bisa read-only. Slanjutnya kita dapat menjalankan command: “echo "teks panjang (contoh)" > /srv/ftp/shared/kitab_penciptaan.txt agar nanti terminal manwe dapat mengaksesnya.

Di terminal manwe, login dengan command “ftp 192.231.1.1” dan gunakan command “get kitab_penciptaan.txt” untuk mendapatkan filenya dan kita bisa melihat langsung perbedaannya di wireshark:

<img width="1230" height="266" alt="Image" src="https://github.com/user-attachments/assets/a5468a3a-188b-46f0-929b-fe0c5fdf4c3d" />

Disini dapat dilihat kalau user ainur melakukan request dan mendapatkan file txt tersebut.

SElanjutnya pengujian read-only, kita akan mencobanya di terminal manwe, buat dulu file random, disini kita pakai .txt dengan command:
```
echo "ini buat ngejawab soal9" > soal9.txt
```
Lalu login lagi ke ftp sebagai ainur dan coba gunakan command “put soal9.txt”, hasilnya akan menjadi seperti:

<img width="1233" height="272" alt="Image" src="https://github.com/user-attachments/assets/ffee98a8-5016-4912-bfd1-0376e52572d8" />

Disini dapat dibuktikan kalau user ainur tidak memiliki permission “writE”

## Soal 10
Untuk melakukan serangan ini, kita ke terminal melkor dan run command “ping -c 100 -i 0.2 192.231.1.1” untuk melakukan ping sebanyak 100 kali setiap 0.2 detik dengan output:

<img width="1241" height="276" alt="Image" src="https://github.com/user-attachments/assets/85cd31ca-af7a-4c0b-a707-7526683830b8" />

Disini ternyata tidak terjadi packet loss dengan average round trip timenya yaitu 0.3 ms yang berarti kinerja Eru tidak terganggu atau tidak begitu berdampak ke Eru itu sendiri.

## Soal 11
Disini, kita dapat melakukan command “telnet 192.231.1.2” dan melakukan beberapa command seperti “pwd”, “whoami” dsb. Tampilan di wireshark akan menjadi seperti berikut:

<img width="1238" height="281" alt="Image" src="https://github.com/user-attachments/assets/bc6e8542-3fd4-417d-8e3c-7ebbce831250" />

Kalau kita coba follow pada paket yang terdapat “bytes data” seperti 300  dan 302 akan muncul output seperti ini:

<img width="1151" height="477" alt="Image" src="https://github.com/user-attachments/assets/667ef87b-f6df-405c-bd85-404141e0dbbf" />

Dalam kata lain, hasilnya merekonstruksi seluruh percakapan dan secara jelas menunjukkan semua perintah yang diketik (whoami, ls -l, pwd) sebagai plain text (teks biasa) tanpa enkripsi sama sekali.

Disini terbukti kalau seluruh sesi telnet, termasuk semua perintah yang dijalankan, dapat dengan mudah diintip oleh siapa pun yang memantau jaringan.

## Soal 12
Untuk menjawab soal, kita dapat menggunakan fitur dari netcat dengan command “nc -zv 192.231.1.2 21” untuk port 21, “nc -zv 192.231.1.2 80” untuk port 80, dan seterusnya seperti foto berikut:

<img width="1244" height="252" alt="Image" src="https://github.com/user-attachments/assets/5ecef14d-e26f-471a-81a3-aea643c7509a" />

Diketahui bahwa 3 port yang diberikan saat ini dalam keadaaan tertutup.

## Soal 13
Pertama kita download terlebih dahulu SSH server menggunakan command “apt-get update && apt-get install -y openssh-server” di terminal eru. Untuk melihat secara live perbedaan wireshark, kita pergi ke aplikasi gns3 dan lakukan capture dari link yang menyambungkan client varda dengan switch2. Selanjutnya kita bisa pergi ke terminal varda dan menjalankan command “ssh ainur@192.231.2.1” dengan ini varda dapat login ke user ainur dan memasukkan password seperti berikut:

<img width="1418" height="346" alt="Image" src="https://github.com/user-attachments/assets/3c266551-636b-4a3a-a287-566c1581cc04" />

Selanjutnya kita melakukan capture pada sesi wireshark seperti berikut (contoh):

<img width="1023" height="392" alt="Image" src="https://github.com/user-attachments/assets/6b3dd608-b21b-48ec-baf1-639e88bccaef" />

<img width="1023" height="390" alt="Image" src="https://github.com/user-attachments/assets/e0992c00-bf4a-4c83-af33-9cc0a9c8dce3" />

Untuk melihat secara langsung apakah ssh mengenkripsi input dengan baik dan melihat perbedaannya dengan telnet, kita dapat memilih salah satu paket yang memiliki tulisan “encrypted packet” dan mengklik kanan paket tersebut dan melakukan follow tcp stream seperti foto berikut, disini kita memilih paket 67:

<img width="1272" height="836" alt="Image" src="https://github.com/user-attachments/assets/21ebd390-a7ce-431e-803f-68eb82460b4f" />

Disini terlihat jelas kalau enkripsi dari SSH Shell itu lebih baik jika dibandingkan telnet yang secara langsung memberikan output keystrokes dari user.

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

Kemudian muncul soal berikutnya

<img width="495" height="69" alt="image" src="https://github.com/user-attachments/assets/491fe8f7-065a-4753-ba7a-d71c35549107" />

Saya menjawab 41824 karena saya menemukan user yang berhasil login pada tcp.stream tersebut.

Kemudian muncul soal baru

<img width="410" height="73" alt="image" src="https://github.com/user-attachments/assets/67d5aff0-ad05-4b43-98e8-8aadca69e7f6" />

Setelah melakukan analisis format pada credential tersebut, saya menemukan 
`User-Agent: Fuzz Faster U Fool v2.1.0-dev`

<img width="614" height="212" alt="Screenshot 2025-09-30 013841" src="https://github.com/user-attachments/assets/7725dc54-6271-4334-96b2-ae600a433a32" />

Setelah saya submit, saya mendapatkan flag
```
KOMJAR25{Brut3_F0rc3_mpZCV3bIHooBLrXAsFDPb1FgB}
```
<img width="925" height="94" alt="image" src="https://github.com/user-attachments/assets/82256dd0-1594-427d-a579-64fb26768064" />


## Soal 15
Ketika menghubungkan ke ip yang diberikan, akan muncul pertanyaan "What device does Melkor use"

<img width="486" height="219" alt="image" src="https://github.com/user-attachments/assets/031c8396-415d-4d6b-a795-f97015ca6817" />

Berdasarkan informasi yang saya dapatkan dari packets 2, saya menemukan idVendor, idProduct, iManufacturer, dan iProduct yang kemudian saya masukan ke ChatGPT untuk identifikasi device. Output yang diberikan oleh AI adalah Keyboard. Device Keyboard yang didukung oleh penemuan pada packet berikutnya yaitu pada packet 16.

<img width="594" height="215" alt="Screenshot 2025-09-30 134648" src="https://github.com/user-attachments/assets/765f3363-3182-4eb5-ade7-ee19547e3029" />

<img width="392" height="99" alt="Screenshot 2025-09-30 135108" src="https://github.com/user-attachments/assets/78e67284-efdd-4e06-bace-d998941abc59" />

Soal berikutnya adalah "What did Melkor write?"
Kita perlu memeriksa apa yang dituliskan oleh Melkor, saya melakukan export as txt dari pcapng, kemudian saya convert hanya mengambil hid code.
<img width="947" height="299" alt="Screenshot 2025-09-30 142632" src="https://github.com/user-attachments/assets/e99ed84a-8f6f-4d20-ad56-eba2049c733c" />
<img width="221" height="221" alt="Screenshot 2025-09-30 145135" src="https://github.com/user-attachments/assets/a17c7067-a9fe-4463-b506-2a186b61b083" />

Didapatkan hex code tersebut yang kemudian saya convert menjadi plain text BASE64 seperti berikut. 

<img width="608" height="85" alt="Screenshot 2025-09-30 151111" src="https://github.com/user-attachments/assets/b40f54a1-ddd0-4a53-be13-a5a689edf65b" />
`UGx6X3ByMHYxZGVfeTB1cl91czNybjRtZV80bmRfcDRzc3cwcmQ=`

Setelah di submit akan muncul pertanyaan berikutnya yaitu "What is Melkor's secret message?"
Dari plaintext sebelumnya saya convert menggunakan BASE64 yang outputnya seperti berikut

<img width="1208" height="567" alt="Screenshot 2025-09-30 151036" src="https://github.com/user-attachments/assets/f7f5e987-df84-420f-90cc-29dcd8840d37" />
<img width="990" height="97" alt="Screenshot 2025-09-30 151119" src="https://github.com/user-attachments/assets/955d9cde-47f9-4519-ab80-78062f245b0f" />

Setelah di submit saya mendapatkan flag berikut
```
KOMJAR25{K3yb0ard_W4rr10r_G1esN3Sb9Oi1BgIaiTFgoHEA8}
```

## Soal 16
Untuk soal nomor 16, ditemukan soal berikut

<img width="673" height="281" alt="Screenshot 2025-09-30 103615" src="https://github.com/user-attachments/assets/514ce5e8-d0df-4a48-8a35-311a7f22e2cc" />

Melalui file yang didapatkan, kita dapat memeriksa FTP Protocol dan memeriksa info pada tiap packets. Saya menemukan pada FTP Protocol bagian bawah untuk user dan pass.

<img width="1919" height="108" alt="Screenshot 2025-09-30 103756" src="https://github.com/user-attachments/assets/a7feb0c5-b7a8-4dd7-a07b-7cbe637b0fc7" />
<img width="710" height="404" alt="Screenshot 2025-09-30 103812" src="https://github.com/user-attachments/assets/744177e8-2e04-4b35-ae5f-b39cfbabb81d" />

Kemudian akan muncul soal baru yaitu

<img width="723" height="94" alt="Screenshot 2025-09-30 104320" src="https://github.com/user-attachments/assets/079fd268-3f57-4b27-bb23-c62917f6e254" />

Kemudian saya menemukan pada protocol FTP-Data terdapat 5 jenis file yaitu
t.exe, r.exe, e.exe,  w.exe, q.exe

<img width="1437" height="124" alt="Screenshot 2025-09-30 104512" src="https://github.com/user-attachments/assets/e95221b6-7038-46b4-b2e7-50a06835f04b" />
<img width="1426" height="125" alt="Screenshot 2025-09-30 104544" src="https://github.com/user-attachments/assets/bdeb84b1-a406-487c-8565-cc82f72c51dd" />
<img width="1423" height="103" alt="Screenshot 2025-09-30 104607" src="https://github.com/user-attachments/assets/583bcdcd-4b50-4c38-8796-556b903933b0" />
<img width="1423" height="100" alt="Screenshot 2025-09-30 104622" src="https://github.com/user-attachments/assets/d842e8f0-6df2-4135-9d60-5f623827e1ee" />
<img width="1424" height="99" alt="Screenshot 2025-09-30 104642" src="https://github.com/user-attachments/assets/30f9a191-272a-4e99-9083-c34fefa41f72" />
<img width="575" height="70" alt="image" src="https://github.com/user-attachments/assets/57564993-6a19-4c43-96e1-55f3df8404cc" />

Kemudian muncul soal berikutnya untuk menemukan hash dari tiap file

<img width="607" height="93" alt="Screenshot 2025-09-30 110148" src="https://github.com/user-attachments/assets/32e737b3-b7bf-4f9c-8824-199fd8ba0463" />

Cara untuk menemukan hash, pertama saya follow protocol tiap file kemudian save file as raw file.
<img width="1919" height="1079" alt="image" src="https://github.com/user-attachments/assets/15814a7c-1881-42af-87ae-a9dc89d850cc" />
Setelah itu saya move file ke Kali Linux dan kemudian membuka file menggunakan `sha256 sum <file>`

<img width="760" height="175" alt="image" src="https://github.com/user-attachments/assets/a6036376-636c-4d49-8373-2ddb5356e832" />

Setelah itu saya masukkan pada ip untuk hasil bashnya dan mendapatkan flag seperti berikut

<img width="1066" height="759" alt="image" src="https://github.com/user-attachments/assets/c71f94ed-f270-43d1-889d-91c042ccd35a" />

```
Congratulations! Here is your flag: KOMJAR25{Y0u_4r3_4_g00d_4nalyz3r_k8zuJCGZKF9u4N9JTPxMyZO0a}
```

## Soal 17
Terdapat soal pertama yaitu "What is the name of the first suspicious file?"
Pertama tama saya mencoba filter untuk file .exe pada wireshark

<img width="1247" height="111" alt="image" src="https://github.com/user-attachments/assets/32bb6194-9429-4411-a316-c512ce058b25" />

Terdapat satu file yaitu knr.exe, saya coba input pada soal namun hasil disebutkan salah. Kemudian saya mencoba memeriksa adanya file lain melalui http protocol, ketika ingin saya export terlihat ada 3 file.

<img width="906" height="170" alt="image" src="https://github.com/user-attachments/assets/70f46a86-cf74-46fe-94ea-47c4ea403f79" />

Setelah saya coba input pada soal, jawaban yang benar adalah `Invoice&MSO-Request.doc`

<img width="436" height="297" alt="image" src="https://github.com/user-attachments/assets/8e4651f2-2f71-44ab-ae4f-cb3f68d34f88" />


Soal berikutnya adalah "What is the name of the second suspicious file?"
Saya menjawab `knr.exe` dan jawaban benar.

<img width="433" height="63" alt="image" src="https://github.com/user-attachments/assets/5fe984c8-f5d1-48a2-bb0c-b379fb156c44" />

Soal berikutnya adalah "What is the hash of the second suspicious file (knr.exe)?"
Untuk soal ini, saya mengerjakan sama seperti pada soal sebelumnya. Pertama tama saya export file tersebut lalu menggunakan command `sha256sum <file>` pada linux dan output sebagai berikut.

<img width="821" height="85" alt="image" src="https://github.com/user-attachments/assets/e939f63e-e99f-4f3d-8c23-f8f2220db238" />

<img width="801" height="92" alt="image" src="https://github.com/user-attachments/assets/22cc5424-ff60-4a5b-a3a5-f5310b9ceecf" />

Flag yang saya dapatkan adalah
```
Congratulations! Here is your flag: KOMJAR25{M4ster_4n4lyzer_OlM7sqeOjCN6gcU4d44PMdzOD}
```

## Soal 18
Pertama saya mendapatkan soal "How many files are suspected of containing malware?"
Sama seperti pada soal sebelumnya, saya memeriksa export dan menemukan 2 files suspected karena formatnya aneh.

<img width="1919" height="1079" alt="image" src="https://github.com/user-attachments/assets/259d1eef-54ac-4c59-878e-c33f2bc97fe1" />

Kemudian soal berikutnya adalah "What is the name of the first malicious file?"
dari list export tersebut bisa terlihat ada 2 yaitu
- `\WINDOWS\d0p2nc6ka3f.fixh0lhyg4voyfcy_smc2ho_u083urjpphnwlahjwhv_o5c0vf6.exe`
- `\WINDOWS\oiku9bu68cxqenfmcso2aek6t07_guuisqxlnliv8dx2eemqdnhvhyl46l8n.di.exe`

Kemudian saya input pada ip untuk file pertama adalah 
`
d0p2nc6ka3f_fixhohlycj4ovqfcy_smchzo_ub83urjpphrwahjwhv_o5c0fvf6.exe
`

<img width="985" height="101" alt="image" src="https://github.com/user-attachments/assets/846d7321-9c70-4f29-a2b8-d481cc8df35b" />

Muncul soal berikutnya yaitu "Apa nama file berbahaya yang kedua"
Saya input 
`
oiku9bu68cxqenfmcsos2aek6t07_guuisgxhllixv8dx2eemqddnhyh46l8n_di.exe
`

<img width="997" height="88" alt="image" src="https://github.com/user-attachments/assets/f3c7eb10-2a7d-48a1-bb17-d77d0f29dd15" />

Soal selanjutnya adalah mencari hash dari file pertama dan kedua

<img width="1696" height="264" alt="image" src="https://github.com/user-attachments/assets/16ee0199-ccdf-4f8a-a41a-024bd52f0fff" />

<img width="1236" height="237" alt="Screenshot 2025-10-04 194951" src="https://github.com/user-attachments/assets/7d03a651-d88b-41d2-b3bd-f02e282d0714" />


Kemudian saya mendapatkan flag
`
Congratulations! Here is your flag: KOMJAR25{Y0u_4re_g0dl1ke_IeMfb0VRzphjLw0RoMacwntOZ}
`

## Soal 19
Soal pertama adalah "Who sent the threatening message?"

Untuk menemukan sender saya mencari user yang berhasil melakukan login

<img width="1919" height="108" alt="image" src="https://github.com/user-attachments/assets/5a68f78c-559e-49ca-be8f-618af6389824" />

<img width="1919" height="1079" alt="Screenshot 2025-10-04 195433" src="https://github.com/user-attachments/assets/b2bbf4fb-a048-4df9-833c-8bfd1425a2e8" />

disini terlihat sender adalah Your Life
`
From: Your Life<YourLife36@7162.com>
`

<img width="611" height="294" alt="image" src="https://github.com/user-attachments/assets/4a34f5fa-ce01-4f58-954a-4667233fcb92" />


Soal berikutnya adalah "How much ransom did the attacker demand ($)?"

<img width="1232" height="458" alt="image" src="https://github.com/user-attachments/assets/87edfb49-48b0-4d53-ace8-198c4e6269f8" />

disini terlihat attacker meminta $1600 BTC

<img width="628" height="105" alt="image" src="https://github.com/user-attachments/assets/ad93a701-0de1-419a-a2cb-d44c96a48304" />

Pada soal berikutnya ditanya "What is the attacker's bitcoin wallet?"
Terlihat pada screenshot sebelumnya bitcoin wallet attacker adalah
`
1CWHmuF8dHt7HBGx5RKKLgg9QA2GmE3UyL
`

<img width="1268" height="542" alt="image" src="https://github.com/user-attachments/assets/9d8c55cf-7597-4c0c-bcdc-a801afea348e" />

Saya menemukan flag 
`
Congratulations! Here is your flag: KOMJAR25{Y0u_4re_J4rk0m_G0d_VZx4WtZCDd8OchMq8iAHyryhD}
`

## Soal 20
Soal pertama adalah "What encryption method is used?"
Ketika sory by protocol akan terlihat encryption menggunakan TLS v1.2

<img width="1919" height="656" alt="image" src="https://github.com/user-attachments/assets/289c08ec-2339-46f0-aefb-906a238a6dba" />

<img width="452" height="97" alt="image" src="https://github.com/user-attachments/assets/5f2c4f5a-2e4c-4bc8-8540-92ee6ab6d740" />

Soal berikutnya adalah "What is the name of the malicious file placed by the attacker?"

Ketika cek export http saya menemukan 2 file yaitu invest_20.dll dan docs.php

<img width="1919" height="1045" alt="Screenshot 2025-10-04 200857" src="https://github.com/user-attachments/assets/5dd0a2fe-3f32-4922-a859-7deac7b7e575" />

<img width="878" height="94" alt="image" src="https://github.com/user-attachments/assets/354a390d-eebf-469e-bd04-47e10a08d29f" />

Soal berikutnya adalah "What is the hash of the file containing the malware?"
Sama seperti sebelumnya saya menggunakan `sha256sum`

<img width="1129" height="113" alt="image" src="https://github.com/user-attachments/assets/ef7574ef-ff46-4f2d-99e5-f34bd5c619d8" />

<img width="1261" height="126" alt="image" src="https://github.com/user-attachments/assets/1ade3a83-d757-476e-a562-e355c2f86d0b" />

Saya mendapatkan flag 
`
Congratulations! Here is your flag: KOMJAR25{B3ware_0f_M4lw4re_9vAqRb3l7D6LnJ8DM0iPIibHr}
`
