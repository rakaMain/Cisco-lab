# 🛠️ Konfigurasi FTP Server — Cisco Packet Tracer Lab

**Deskripsi singkat:**
Lab ini memperagakan cara menyiapkan layanan FTP (File Transfer Protocol) pada jaringan lokal menggunakan Cisco Packet Tracer. FTP server akan menyimpan file yang dapat diunggah, diunduh, dan dikelola oleh client melalui koneksi FTP. Dalam lab ini juga dibuat user `raka` yang memiliki akses penuh ke direktori FTP.

---

## 🔌 Topologi & Alamat

**Network:** `192.168.1.0 /24`

**Perangkat:**

* **FTP Server** (`ftp.raka.local`) — `192.168.1.1 /24`
* **PC Client 1 (PC0)** — `192.168.1.2 /24`
* **PC Client 2 (PC1)** — `192.168.1.3 /24`
* **Switch** — menghubungkan semua device di jaringan

> **Catatan:** Anda memberikan IP duplicate untuk PC. Saya mengasumsikan `PC0 = 192.168.1.2` dan `PC1 = 192.168.1.3` agar tidak terjadi konflik IP.

> Semua device gunakan subnet mask `255.255.255.0`. Untuk lab sederhana ini tidak diperlukan router/gateway kecuali ingin menghubungkan jaringan lain.

---

## 🔬 Fungsi Lab

* Menyiapkan layanan FTP pada server lokal (Packet Tracer Server).
* Membuat user `raka` dengan akses penuh (read/write) ke direktori FTP.
* Praktik mengunggah (upload) dan mengunduh (download) file menggunakan FTP client (FileZilla/Browser/Command Prompt jika tersedia di Packet Tracer).

Singkatnya: **Client → koneksi FTP ke `192.168.1.1` (user=raka) → upload/download file.**

---

## ✅ Manfaat / Pembelajaran

* 📁 **Memahami dasar FTP:** perbedaan upload vs download, user/authentication, dan permission.
* 🔐 **Manajemen user:** membuat akun FTP dan mengatur hak akses.
* 🛠️ **Konfigurasi layanan di Packet Tracer:** mengaktifkan service FTP, membuat direktori dan user.
* 🧭 **Troubleshooting dasar layanan jaringan:** cek konektivitas, troubleshooting autentikasi, dan akses file.

---

## ⚙️ Langkah Singkat (Panduan Pelaksanaan)

1. **Siapkan topology:** letakkan 1 switch, 2 PC, dan 1 Server (gunakan device "Server" di Packet Tracer).

2. **Atur IP** pada tiap device sesuai tabel Topologi:

   * FTP Server: `192.168.1.1/24`
   * PC0: `192.168.1.2/24`
   * PC1: `192.168.1.3/24`

3. **Konfigurasikan FTP Server (Packet Tracer Server):**

   * Klik device Server → tab `Config`.
   * Aktifkan service **FTP** (centang/enable FTP service).
   * Pada bagian `FTP` atau `User` (tergantung versi Packet Tracer), tambahkan user baru:

     * **Username:** `raka`
     * **Password:** (pilih password yang mudah diingat, contoh: `Raka123!`) — simpan.
     * **Home Directory / Root:** tentukan folder root FTP (mis. `/ftp` atau `files`) — ini adalah direktori yang dapat diakses oleh user `raka`.
     * Berikan permission penuh (read/write/delete) untuk user `raka` pada direktori tersebut.

4. **Tambahkan file contoh:** pada file system Server (tab `File` atau `Desktop > File Manager`), buat atau unggah file `welcome.txt` atau `index.html` untuk diuji.

5. **Set DNS/Hostname (opsional):** jika ingin memakai nama (mis. `ftp.raka.local`), Anda bisa menambahkan entry di hosts file PC (Desktop > IP Configuration > DNS atau Hosts) — namun pada lab sederhana, cukup gunakan IP.

6. **Konfigurasikan IP Client:** pada masing-masing PC, atur IP statis seperti yang tertera dan pastikan NIC aktif.

7. **Uji koneksi jaringan:** dari PC jalankan `ping 192.168.1.1` untuk memastikan konektivitas.

8. **Tes FTP:**

   * Buka aplikasi `File Transfer`/`FTP` client di Packet Tracer (atau `Command Prompt` jika ada):

     * Host: `192.168.1.1`
     * Username: `raka`
     * Password: (password yang dibuat)
   * Coba **login**, **upload** file ke direktori home, lalu **download** file yang sama di PC lain.

9. **Verifikasi permission:** pastikan user `raka` dapat membuat, menghapus, dan mengunduh file di direktori FTP.

---

## 🔍 Expected Result / Verifikasi

* PC0 dan PC1 dapat `ping 192.168.1.1` sukses (reply).
* PC berhasil **login** ke FTP server menggunakan user `raka`.
* PC dapat **mengunggah** file ke direktori FTP dan file tersebut muncul di File Manager server.
* PC lain dapat **mengunduh** file yang sudah diunggah.
* Jika menggunakan `ftp` via command: perintah `dir`/`ls` menampilkan daftar file di direktori home user.


---

## 📌 Metadata

* **Author:** Raka
* **Lab:** Membuat FTP Server — Cisco Packet Tracer
* **User FTP:** `raka` (akses penuh ke direktori FTP)
* **Tanggal:** 2025-09-09

