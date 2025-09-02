# 🛠️ Konfigurasi Basic Switch — Cisco Packet Tracer Lab

**Deskripsi singkat:**
Lab ini memperagakan cara menghubungkan beberapa PC menggunakan sebuah switch pada jaringan lokal sehingga setiap PC dapat saling berkomunikasi (ping, file sharing sederhana, dan akses layanan dasar). Cocok untuk pemula yang ingin memahami konsep switching dasar, alamat IP, dan verifikasi konektivitas.

---

## 🔌 Topologi & Alamat

**Network:** `192.168.1.0 / 24`

**Perangkat:**

* **PC1** — `192.168.1.1 /24`
* **PC2** — `192.168.1.2 /24`
* **PC3** — `192.168.1.3 /24`
* **PC4** — `192.168.1.4 /24`
* **PC5** — `192.168.1.5 /24`
* **PC6** — `192.168.1.6 /24`
* **Switch (Layer 2)** — menghubungkan semua PC di jaringan

> Semua device gunakan subnet mask `255.255.255.0`. Pada lab sederhana ini tidak diperlukan gateway kecuali bila ingin menambahkan router untuk mengakses jaringan lain.

---

## 🔬 Fungsi Lab

* Mempraktikkan pengkabelan dan koneksi fisik antar perangkat menggunakan switch.
* Memahami cara memberi alamat IP statis pada PC dalam satu jaringan.
* Menguji konektivitas antar host (ICMP/ping) melalui switch.
* Mengenal perilaku switch Layer 2 (forwarding berbasis MAC address) dan cara memeriksa tabel MAC.

---

## ✅ Manfaat / Pembelajaran

* 🔌 **Dasar pengkabelan jaringan**: tipe kabel dan port yang digunakan pada switch dan PC.
* 🧠 **Konsep switching**: cara switch mempelajari alamat MAC dan meneruskan frame ke port yang sesuai.
* 🔍 **Verifikasi konektivitas**: penggunaan `ping`, `arp`, dan pemeriksaan status interface.
* 🛠️ **Troubleshooting awal**: cek koneksi fisik, konfigurasi IP, dan status port switch.
* 📚 **Fondasi untuk topologi lebih kompleks** seperti VLAN atau routing antar jaringan.

---

## ⚙️ Langkah Singkat (Panduan Pelaksanaan)

1. **Siapkan topology**: letakkan 1 switch (Layer 2) dan 6 PC di Packet Tracer. Sambungkan tiap PC ke switch menggunakan kabel straight-through.
2. **Atur IP** pada tiap PC sesuai tabel Topologi: masukkan IP dan subnet mask `255.255.255.0`.
3. **Periksa koneksi fisik**: pastikan port pada switch menunjukkan `up` (link up) dan kabel terpasang ke port yang benar.
4. **Uji konektivitas dasar**:

   * Dari PC1: `ping 192.168.1.2` (PC2), `ping 192.168.1.3` (PC3), dst.
5. **Cek ARP dan MAC**:

   * Pada PC, jalankan `arp -a` untuk melihat entri ARP.
   * Pada switch (jika mendukung CLI), lihat MAC address table: `show mac address-table`.
6. **(Opsional) Sharing file sederhana**: aktifkan layanan simple HTTP/FTP pada salah satu PC/server dan coba akses dari PC lain untuk menguji layanan pada layer-3 aplikasi.
7. **Verifikasi tambahan**: pastikan ping dari setiap PC ke setiap PC lain mendapat balasan (reply).

---

## 🔍 Expected Result / Verifikasi

* Semua PC dapat saling melakukan ping (mis. dari `192.168.1.1` ke `192.168.1.6`).
* Tabel MAC pada switch menampilkan alamat MAC untuk setiap port yang terhubung.
* Entri ARP di masing-masing PC menunjukkan pemetaan IP → MAC untuk host lain.
* Jika layanan sederhana diaktifkan (mis. HTTP), PC lain dapat mengakses layanan tersebut menggunakan IP server.


---

## 📌 Metadata

* **Author:** Raka
* **Lab:** Basic Switch
* **Tanggal:** 2025-09-02

---
