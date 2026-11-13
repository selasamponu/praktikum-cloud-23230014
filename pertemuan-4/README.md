# Laporan Praktikum Cloud Computing - Pertemuan 4
**NIM:** 23230014

## 1. Versi Docker dan OS Host (Langkah 1)
- **OS Host:** Ubuntu 24.04
- **Docker Engine Version:** 27.1.1 (Sesuaikan dengan yang ada di terminal Anda)

## 2. Perbandingan OS dan Kernel (Langkah 3)
- **Host (Ubuntu):** OS = Ubuntu 24.04, Kernel = 6.8.0-147-generic
- **Container (Alpine):** OS = Alpine Linux, Kernel = 6.8.0-147-generic
- **Kesimpulan:** Container Alpine dapat berjalan di atas Ubuntu karena container tidak membawa OS utuh, melainkan memakai kernel milik host.

## 3. Nginx dalam Container (Langkah 5)
*(Tarik dan lepas screenshot halaman Nginx berisi NIM Anda ke sini)*
- [Screenshot Nginx NIM]

## 4. Penjelasan Siklus Hidup Container (Langkah 7)
- **Stop/Start:** Saat container di-stop lalu di-start kembali, perubahan yang kita buat (halaman NIM) masih ada. Ini karena container yang sama hanya dihentikan sementara (di-pause).
- **Rm/Run:** Saat container dihapus (rm) lalu dibuat ulang (run), perubahan (halaman NIM) hilang dan kembali ke "Welcome to nginx!". Ini karena container baru dibuat dari image asli yang tidak berubah.

## 5. Tabel Ukuran Image (Langkah 8)
| Image | Ukuran (SIZE) |
| :--- | :--- |
| `nginx` | 192MB |
| `nginx:alpine` | 63MB |
| `nginx:1.26` | 192MB |

## 6. Jawaban Evaluasi
1. **Container Alpine vs Host:** Hasil `uname -r` sama membuktikan bahwa container berbagi kernel dengan host. Berbeda dengan VM yang harus membawa sistem operasi dan kernel sendiri.
2. **Image vs Container:** Image adalah cetakan (resep) yang tidak berubah. Container adalah hasil jalan dari image tersebut. Di Langkah 8, satu image `nginx:alpine` bisa dijalankan menjadi container `web-alpine`.
3. **Port Mapping:** Pada `-p 8081:80`, angka **8081** adalah port host, dan angka **80** adalah port container. Ketiga container boleh memakai port 80 di dalamnya karena setiap container memiliki ruang jaringan (network namespace) yang terisolasi, sehingga tidak saling bentrok.
4. **Kenapa hilang?** Stop/start hanya mematikan proses sementara, wadah (container) aslinya masih ada. Rm/run menghapus wadah lama dan membuat wadah baru dari image asli yang bersih.
5. **Docker vs apt:** Docker jauh lebih cepat (hitungan detik) karena kita tidak perlu menginstall dependensi satu per satu. Keuntungannya, tim bisa menjalankan aplikasi yang persis sama di server cloud manapun tanpa takut ada perbedaan konfigurasi sistem operasi.
   <img width="940" height="188" alt="image" src="https://github.com/user-attachments/assets/351389ea-0bbd-4f25-8ae1-62036e0cd480" />

