# 🛠️ Access Point Dasar — Cisco Packet Tracer Lab

**Deskripsi singkat:**
Lab ini memperagakan cara menghubungkan beberapa device (PC, Laptop, Smartphone) ke jaringan nirkabel menggunakan Access Point di Cisco Packet Tracer. Setiap perangkat menggunakan **IP statik** yang ditetapkan manual sehingga peserta belajar cara memasang module nirkabel pada PC/Laptop, mengonfigurasi SSID pada Access Point, dan memastikan konektivitas antar device di jaringan `192.168.1.0/24`.

---

## 🔌 Topologi & Alamat

**Network:** `192.168.1.0 / 24`

**Perangkat:**

* **Access Point / Wireless Router** — (SSID: `RakaNet`) — mis. alamat manajemen `192.168.1.10` (opsional)
* **PC0** — `192.168.1.1 /24` (menggunakan module VMP300N pada slot LAN agar bisa terhubung Wi-Fi)
* **Laptop** — `192.168.1.2 /24` (menggunakan module VMP300N pada slot LAN agar bisa terhubung Wi-Fi)
* **Smartphone** — `192.168.1.3 /24` (terhubung ke SSID `RakaNet`)
* **Switch** — (opsional, untuk menghubungkan AP ke jaringan kabel jika diperlukan)

> Untuk lab sederhana ini, jika tidak ada router/gateway eksternal, **tidak wajib** mengisi gateway. Jika ingin mensimulasikan akses ke internet atau routing, tetapkan gateway sesuai topologi (mis. `192.168.1.254`).

---

## 🔬 Fungsi Lab

* Menghubungkan perangkat-klien ke **Access Point** menggunakan koneksi nirkabel di Packet Tracer.
* Melatih **pemasangan module VMP300N** pada PC/Laptop agar perangkat dapat menggunakan interface Wi-Fi di Packet Tracer.
* Mengatur **IP statik** pada setiap device dan memastikan konektivitas antar device melalui jaringan Wi-Fi.
* Memahami konfigurasi SSID, keamanan (WPA2 PSK sederhana), dan verifikasi koneksi.

---

## ✅ Manfaat / Pembelajaran

* 📡 **Memahami dasar wireless networking**: SSID, authentication, dan IP statik pada perangkat nirkabel.
* 🛠️ **Praktik hardware virtual**: memasang module VMP300N pada PC/Laptop di Packet Tracer.
* 🔍 **Troubleshooting Wi-Fi dasar**: cek konfigurasi module, SSID, IP, dan jangkauan sinyal.
* 🧭 **Konsep alamat statik vs DHCP**: kapan gunakan IP statik dan bagaimana pengaruhnya pada konektivitas.
* 📚 **Persiapan untuk topologi lebih kompleks**: menambahkan router, gateway, atau layanan jaringan lain.

---

## ⚙️ Langkah Khusus (Module VMP300N)

1. Pilih **PC0** atau **Laptop** → buka tab **Physical**.
2. Matikan (power off) device jika perlu.
3. Cari **module VMP300N** (wireless NIC) di daftar modul.
4. Lepas LAN module lama (jika menghalangi) lalu **seret & letakkan VMP300N** ke slot yang tersedia.
5. Nyalakan kembali device (jika diminta).
6. Setelah module terpasang, buka tab **Desktop → PC Wireless** (atau Wireless configuration) untuk melihat adapter nirkabel dan scan SSID.

> Catatan: langkah UI bisa sedikit berbeda tergantung versi Packet Tracer; intinya adalah memasang modul wireless (VMP300N) ke slot fisik perangkat agar muncul interface Wi-Fi.

---

## ⚙️ Langkah Singkat (Panduan Pelaksanaan)

1. **Siapkan topology**: letakkan 1 Access Point (atau Wireless Router), 1 switch (opsional), PC0, Laptop, dan Smartphone di Packet Tracer.
2. **Pasang module VMP300N** pada PC0 dan Laptop (lihat langkah khusus).
3. **Atur IP statik** pada tiap device:

   * PC0: `192.168.1.1 /24`
   * Laptop: `192.168.1.2 /24`
   * Smartphone: `192.168.1.3 /24`
     (Gateway dikosongkan kecuali Anda menambahkan router.)
4. **Konfigurasikan Access Point**:

   * SSID: `RakaNet`
   * Security: WPA2 Personal (PSK) — Password: `rakapass123` (contoh)
   * Channel & mode: default / auto
5. **Connect devices** ke SSID `RakaNet` melalui konfigurasi wireless pada PC/Laptop/Smartphone di Packet Tracer.
6. **Uji koneksi**: dari PC/Laptop/Smartphone jalankan `ping` ke IP perangkat lain (mis. `ping 192.168.1.2` dari PC0).
7. **Verifikasi tambahan**: cek status wireless adapter (connected, SSID, signal strength) pada masing-masing device.

---

## 🔍 Expected Result / Verifikasi

* Semua device terhubung ke SSID `RakaNet` dan menampilkan status **connected** pada wireless adapter.
* `ping 192.168.1.1` / `ping 192.168.1.2` / `ping 192.168.1.3` menghasilkan reply antar perangkat.
* Device dapat saling melakukan ARP/resolve MAC address (cek tabel ARP jika tersedia).
* Jika Access Point memiliki halaman manajemen, Anda dapat melihat daftar client terhubung (Client List) yang berisi `192.168.1.1`, `192.168.1.2`, dan `192.168.1.3`.

---

## 🛟 Troubleshooting (Masalah Umum & Solusi)

* **Perangkat tidak menemukan SSID?**

  * Pastikan module VMP300N sudah terpasang dan adapter wireless aktif di device.
  * Periksa SSID dan channel pada Access Point (jangan set ke hidden SSID).
* **Terhubung ke SSID tapi tidak bisa ping?**

  * Pastikan IP statik diisi dengan benar (subnet mask `/24`).
  * Cek apakah ada konflik IP (dua device dengan IP sama).
  * Cek pengaturan firewall di perangkat (jika ada) yang memblok ICMP.
* **Signal lemah / koneksi terputus?**

  * Periksa jarak/jangkauan Access Point di Packet Tracer (posisi perangkat).
  * Coba ubah channel atau mode wireless pada AP.
* **Module VMP300N tidak muncul di daftar modul?**

  * Gunakan device yang mendukung module atau periksa versi Packet Tracer; alternatif: gunakan laptop yang sudah memiliki Wi-Fi built-in di modelnya.

---

## 📌 Metadata

* **Author:** Raka
* **Lab:** Access Point Dasar
* **Tanggal:** 2025-09-04

