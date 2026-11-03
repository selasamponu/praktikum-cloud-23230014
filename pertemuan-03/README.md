# Laporan Praktikum Cloud Computing - Pertemuan 3
**NIM:** 23230014

## 1. Identitas Jaringan (Langkah 1)
- **Antarmuka:** enp1s0
- **IP Address:** 172.30.1.2
- **Gateway:** 172.30.1.1
- **DNS Server:** 8.8.8.8 dan 1.1.1.1

## 2. Hasil DNS (Langkah 2)
- `example.com` -> 104.20.23.154
- `unriyo.ac.id` -> (Tidak ada balasan / kosong)

## 3. Port Terbuka (Langkah 3)
- Port 80 (HTTP) dijalankan oleh program **nginx**.

## 4. SSH dengan Kunci (Langkah 4)
*(Tarik dan lepas screenshot Anda ke sini)*
- [Screenshot Login SSH / Error Password]
- [Screenshot Pesan UNPROTECTED PRIVATE KEY FILE / Permission Denied]

## 5. HTTPS Self-Signed (Langkah 5)
*(Tarik dan lepas screenshot Anda ke sini)*
- [Screenshot curl -I gagal]
- [Screenshot curl -kI berhasil (200 OK)]

## 6. Jawaban Evaluasi
1. **Beda 0.0.0.0:80 dan 127.0.0.1:80:** `0.0.0.0:80` berarti server menerima koneksi dari semua antarmuka (bisa diakses dari internet). `127.0.0.1:80` hanya menerima koneksi lokal (localhost).
2. **Mengapa unggah public key?** Public key aman dibagikan. Private key bersifat rahasia dan tidak boleh keluar dari komputer pengguna.
3. **Mengapa SSH menolak izin 644?** Karena 644 berarti file bisa dibaca oleh publik. Private key harus dijaga kerahasiaannya (hanya bisa dibaca pemilik, yaitu izin 600).
4. **Mengapa self-signed diperingatkan?** Karena sertifikat dibuat sendiri, bukan oleh otoritas terpercaya (CA). Situs publik menggunakan sertifikat dari CA seperti Let's Encrypt.
5. **Port firewall web toko online:** Buka port 80 (HTTP), 443 (HTTPS), dan 22 (SSH). Port 22 sebaiknya dibatasi hanya untuk IP kantor agar aman dari serangan luar.
