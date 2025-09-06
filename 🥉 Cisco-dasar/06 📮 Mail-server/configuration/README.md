# 🛠️ Konfigurasi Mail Server — Cisco Packet Tracer Lab

**Deskripsi singkat:**
Lab ini menunjukkan cara membuat mail server sederhana di Cisco Packet Tracer untuk menampung dan mengirim pesan antar pengguna dalam jaringan lokal.

---

## 🔌 Topologi & Alamat

**Network:** `192.168.1.0 / 24`

**Perangkat:**

* **Mail Server** (Domain: `gmail.com`) — `192.168.1.1`

* **PC Client 1** — `192.168.1.2`

* **PC Client 2** — `192.168.1.3`

* **PC Client 3** — `192.168.1.4`

* **Switch** — menghubungkan semua device di jaringan

> Catatan: Pada lab ini domain diset sebagai `gmail.com` sesuai permintaan — ini hanya contoh untuk lab lokal. Dalam praktik nyata gunakan domain yang kamu miliki atau domain lokal (mis. `lab.local`) untuk menghindari konflik dengan layanan nyata.

---

## 🔐 Akun Pengguna (Contoh)

* **raka** — `raka@gmail.com` / password: `123`
* **sri** — `sri@gmail.com` / password: `123`
* **bayu** — `bayu@gmail.com` / password: `123`

> Format alamat email di lab: `username@domain` (mis. `raka@gmail.com`).

---

## 🔬 Fungsi Lab

* Menyediakan layanan **SMTP** untuk pengiriman email antar user di jaringan lokal.
* Menyediakan layanan **POP3** (atau IMAP jika diinginkan) untuk pengambilan pesan oleh client.
* Menampung mailbox tiap user sehingga pesan dapat disimpan dan diambil kembali.
* Melatih konfigurasi layanan email pada Server dan pengaturan client email di PC.

---

## ✅ Manfaat / Pembelajaran

* 🔎 **Memahami protokol email dasar**: perbedaan peran SMTP (kirim) dan POP3/IMAP (ambil).
* 📬 **Praktik konfigurasi mail server** di lingkungan simulasi (Packet Tracer).
* 🧭 **Pengaturan akun dan autentikasi** untuk user email.
* 🛠️ **Troubleshooting konektivitas dan autentikasi**: cara cek log, ping, dan pengaturan client.

---

## ⚙️ Langkah Singkat (Panduan Pelaksanaan)

1. **Siapkan topology**: letakkan 1 switch, 3 PC, 1 Server di Packet Tracer dan hubungkan semua lewat switch.

2. **Atur IP** pada tiap device sesuai tabel Topologi (sesuaikan gateway jika ada router; untuk lab sederhana router tidak diperlukan).

3. **Konfigurasikan Mail Server (`192.168.1.1`)**:

   * Buka device *Server* → tab **Services** → pilih **Email**.
   * Set **Domain Name** menjadi `gmail.com` (atau domain lokal pilihanmu).
   * Tambahkan user accounts dengan username dan password sesuai daftar (raka, sri, bayu).
   * Pastikan service SMTP dan POP3 (atau IMAP) dalam keadaan **ON**.

4. **Konfigurasikan masing‑masing PC client**:

   * Buka PC → **Desktop** → **Email** (client mail bawaan Packet Tracer).
   * Buat akun email baru dengan konfigurasi:

     * **Email Address**: `raka@gmail.com` (sesuaikan untuk tiap user)
     * **Password**: `123`
     * **SMTP Server**: `192.168.1.1`
     * **POP3 Server**: `192.168.1.1` (atau IMAP jika diaktifkan)
   * Simpan konfigurasi.

5. **Uji pengiriman pesan**:

   * Dari PC1 (raka) kirim email ke `sri@gmail.com`.
   * Buka mailbox pada PC2 (sri) dan lakukan **Get Mail** / **Check Mail** untuk menerima pesan.

6. **Verifikasi tambahan**:

   * `ping 192.168.1.1` dari setiap PC untuk memastikan konektivitas.
   * Periksa log pada Server (jika tersedia) untuk melihat kegiatan SMTP/POP3.

---

## 🔍 Expected Result / Verifikasi

* Pengguna dapat **login** ke mailbox mereka menggunakan username & password yang dibuat.
* Email yang dikirim dari satu user dapat **diterima** oleh user lain di jaringan lokal.
* `ping 192.168.1.1` mengembalikan reply dari mail server.
* Jika `nslookup`/DNS tersedia dan digunakan, domain `gmail.com` bisa di-resolve ke `192.168.1.1` (opsional jika menambahkan DNS service pada server).

---

## 🛟 Troubleshooting (Masalah Umum & Solusi)

* **Gagal login / authentication failed**:

  * Periksa username dan password pada konfigurasi akun di Server.
  * Pastikan client menggunakan password yang sama.

* **Tidak bisa mengirim meski login berhasil**:

  * Pastikan service **SMTP** aktif di server.
  * Periksa pengaturan SMTP pada client (alamat server harus 192.168.1.1).

* **Tidak bisa menerima (Get Mail gagal)**:

  * Pastikan service **POP3/IMAP** aktif di server.
  * Periksa koneksi jaringan (ping dari client ke server).

* **Masalah konektivitas antar device**:

  * Periksa IP, subnet mask, dan kabel pada switch.
  * Pastikan interface pada server dan PC dalam keadaan `Up`.

* **Konflik domain nyata (karena menggunakan `gmail.com`)**:

  * Jika menyebabkan kebingungan, ganti domain lab ke domain lokal (mis. `lab.local` atau `raka.mail`) di pengaturan server.

---

## 📌 Metadata

* **Author:** Raka
* **Lab:** Konfigurasi Mail Server — Cisco Packet Tracer
* **Tanggal:** 2025-09-06
