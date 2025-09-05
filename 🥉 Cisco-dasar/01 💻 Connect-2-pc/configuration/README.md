# 🛠️ Menghubungkan 2 PC — Cisco Packet Tracer Lab

**Deskripsi singkat:**
Lab ini menunjukkan cara menghubungkan dua PC secara langsung menggunakan kabel LAN **crossover** di Cisco Packet Tracer, lalu mengonfigurasi alamat IP pada kedua PC dalam satu jaringan sehingga keduanya dapat saling berkomunikasi.

---

## 🔌 Topologi & Alamat

**Network:** `192.168.1.0 / 24`

**Perangkat:**

* **PC 1** — `192.168.1.1 /24`
* **PC 2** — `192.168.1.2 /24`
* **Kabel:** `Copper Crossover` (PC ↔ PC)

> Catatan: untuk lab sederhana ini kita menghubungkan PC secara langsung menggunakan kabel crossover. Jika Anda menggunakan switch, gunakan `Copper Straight-through` dan letakkan switch di antaranya; langkah konfigurasi IP tetap sama.

---

## 🔬 Fungsi Lab

* Mempraktikkan koneksi fisik antar perangkat (pemilihan kabel yang tepat).
* Mengonfigurasi alamat IP statis pada PC untuk komunikasi di jaringan lokal.
* Verifikasi konektivitas dasar menggunakan `ping` untuk memastikan jaringan berjalan.

Singkatnya: **PC1 (192.168.1.1) ↔ (crossover) ↔ PC2 (192.168.1.2) → cek ping → komunikasi berhasil.**

---

## ✅ Manfaat / Pembelajaran

* 🔌 **Paham pemilihan kabel**: kapan menggunakan crossover vs straight-through.
* 🧾 **Konfigurasi IP dasar**: penetapan IP statis dan subnet mask.
* 🔍 **Troubleshooting awal**: cara memeriksa interface, status link, dan ping.
* 🧰 **Fondasi networking**: dasar yang penting sebelum masuk ke VLAN, routing, dan layanan server.

---

## ⚙️ Langkah Singkat (Panduan Pelaksanaan)

1. **Buka Cisco Packet Tracer** dan buat workspace baru.
2. **Tarik dua device PC** ke canvas (PC-PT).
3. **Pilih kabel**: dari menu kabel pilih **Copper Crossover**.
4. **Sambungkan kabel**: hubungkan port `FastEthernet0` pada PC1 ke `FastEthernet0` pada PC2.
5. **Atur IP pada PC1**: buka `Desktop` → `IP Configuration` → masukkan `IP Address: 192.168.1.1`, `Subnet Mask: 255.255.255.0`.
6. **Atur IP pada PC2**: buka `Desktop` → `IP Configuration` → masukkan `IP Address: 192.168.1.2`, `Subnet Mask: 255.255.255.0`.
7. **Verifikasi link fisik**: periksa ikon koneksi pada masing-masing PC; pastikan interface `up` (biasanya indikator lampu menyala).
8. **Uji konektivitas**: buka `Command Prompt` di PC1, jalankan `ping 192.168.1.2` — dan sebaliknya jika perlu.
9. **Catat hasil**: jika semua reply muncul, koneksi berhasil.

---

## 🔍 Expected Result / Verifikasi

* `ping 192.168.1.2` dari PC1 menghasilkan balasan (reply).
* `ping 192.168.1.1` dari PC2 menghasilkan balasan (reply).
* Ikon link pada kedua PC menunjukkan koneksi aktif (`up`).
* Tidak ada konflik IP pada jaringan (pastikan IP unik).

---

## 🛟 Troubleshooting (Masalah Umum & Solusi)

* **Tidak ada link / interface down**

  * Pastikan kabel yang dipakai adalah **Copper Crossover** untuk koneksi PC↔PC.
  * Periksa port yang digunakan pada masing-masing PC (FastEthernet0).
* **Ping timeout / unreachable**

  * Periksa alamat IP dan subnet mask di kedua PC; pastikan keduanya dalam subnet yang sama (`/24`).
  * Cek tidak ada firewall lokal di PC yang memblok ICMP (di Packet Tracer biasanya tidak aktif).
* **IP conflict / duplicate IP**

  * Jika salah satu PC menggunakan IP yang sama dengan perangkat lain di lab, ganti IP agar unik.
* **Jika menggunakan switch tapi tidak berfungsi**

  * Pastikan gunakan `Copper Straight-through` kabel antara PC → Switch.
  * Periksa apakah port switch aktif (switch port up).


---

## 📌 Metadata

* **Judul:** Menghubungkan 2 PC di Cisco Packet Tracer
* **Author:** Raka
* **Lab:** Koneksi Direct PC↔PC (Crossover)
* **Tanggal:** 2025-08-31
