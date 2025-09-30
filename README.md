# Laporan Resmi Jarkom-Modul-1-2025-K40

## Anggota Kelompok

| No | Nama                   | NRP         |
|----|------------------------|-------------|
| 1  | Ahmad Yafi Ar Rizq | 5027241066  |
| 2  | Mohammad Abyan Ranuaji     | 5027241106  |

## Soal 1
Untuk mempersiapkan pembuatan entitas selain mereka, Eru yang berperan sebagai Router membuat dua Switch/Gateway. Dimana Switch 1 akan menuju ke dua Ainur yaitu Melkor dan Manwe. Sedangkan Switch 2 akan menuju ke dua Ainur lainnya yaitu Varda dan Ulmo. Keempat Ainur tersebut diberi perintah oleh Eru untuk menjadi Client.

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
<img width="712" height="392" alt="Screenshot 2025-09-30 011520" src="https://github.com/user-attachments/assets/50e0e9ab-155e-4380-b5cf-0e23d510c1dd" />
<img width="1919" height="1079" alt="Screenshot 2025-09-30 011456" src="https://github.com/user-attachments/assets/dd6c40af-3335-4edd-b586-bd01e71ce21d" />
