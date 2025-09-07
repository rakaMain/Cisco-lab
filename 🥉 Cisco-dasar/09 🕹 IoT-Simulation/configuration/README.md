# 🛠️ Simulasi IoT — Cisco Packet Tracer Lab (Smart Home)

**Deskripsi singkat:**
Lab ini membuat simulasi IoT server yang akan meremote perabotan rumah (kipas angin dan penyeduh kopi) sehingga perangkat-perangkat tersebut dapat dikendalikan jarak jauh oleh sebuah komputer (PC) melalui IoT Server. IoT Server juga berfungsi sebagai DHCP server untuk memberikan IP secara wireless ke perangkat IoT dan PC.

---

## 🔌 Topologi & Alamat

**Network:** `192.168.1.0 /24`

**Perangkat:**

* **IoT Server (raka-iot-server)** — `192.168.1.1` (static) — *juga berperan sebagai DHCP Server*
* **Access Point / Wireless Router** — `192.168.1.254` (gateway/bridge ke network) *(opsional: dibutuhkan untuk koneksi wireless di Packet Tracer)*
* **PC1 (wireless)** — mendapatkan IP via DHCP dari IoT Server (mis. `192.168.1.100`)
* **Kipas Angin (IoT Fan)** — mendapatkan IP via DHCP dari IoT Server (mis. `192.168.1.101`)
* **Penyeduh Kopi (IoT Coffee Maker)** — mendapatkan IP via DHCP dari IoT Server (mis. `192.168.1.102`)

> Untuk DHCP pool contoh: `192.168.1.100` — `192.168.1.200`, subnet mask `255.255.255.0`, gateway `192.168.1.254` (atau `192.168.1.1` jika tidak ada AP).

> Semua perangkat menggunakan SSID yang sama (mis. `HomeIoT`) dan berada pada VLAN / jaringan `192.168.1.0/24`.

---

## 🔬 Fungsi Lab

* IoT Server mengelola device IoT (kipas & penyeduh kopi), menyimpan status, dan menyediakan antarmuka web/API untuk remote control.
* IoT Server berfungsi rangkap sebagai **DHCP Server** yang memberikan alamat IP ke PC dan perangkat IoT secara wireless.
* PC1 bertindak sebagai **user client** yang mengakses antarmuka IoT Server (web UI atau aplikasi) untuk menyalakan/ mematikan dan memeriksa status perangkat.
* Access Point menghubungkan perangkat wireless ke jaringan lokal sehingga komunikasi antara PC, IoT Server, dan perangkat IoT berlangsung.

Singkatnya: **PC (wireless) → connect ke AP → request ke IoT Server → IoT Server mengirim perintah ke perangkat IoT → perangkat merespon (ON/OFF, status).**

---

## ✅ Manfaat / Pembelajaran

* 🔌 **Memahami konsep IoT dasar**: device pairing, control channel, dan status reporting.
* 🌐 **Praktik jaringan wireless + DHCP**: konfigurasi DHCP di IoT Server dan pengelolaan alamat IP dinamis.
* 🧭 **Integrasi layanan**: bagaimana server mengontrol perangkat fisik virtual melalui protokol IoT (HTTP/MQTT simulasi).
* 🛠️ **Troubleshooting jaringan IoT**: cek konektivitas wireless, DHCP lease, dan log server.
* 📚 **Aplikasi nyata**: dasar penerapan smart home yang dapat dikembangkan ke automasi lebih kompleks.


---

## 🔍 Expected Result / Verifikasi

* IoT devices (Kipas & Penyeduh Kopi) menerima alamat IP dari DHCP pool (mis. `192.168.1.101`, `192.168.1.102`).
* PC1 menerima alamat IP dari DHCP dan dapat mengakses `http://192.168.1.1` (IoT Server UI).
* Saat mengklik kontrol (ON/OFF) pada IoT Server, status perangkat berubah dan perangkat mengeksekusi aksi (visual di Packet Tracer).
* Daftar perangkat (device list) di IoT Server menampilkan status terkini (online / offline / last seen).
* Jika ada fitur logging: event log mencatat perintah yang dikirim dari PC ke perangkat.

---

## 🛟 Troubleshooting (Masalah Umum & Solusi)

* **Perangkat tidak mendapat IP (DHCP gagal)**

  * Pastikan DHCP di IoT Server sudah aktif dan pool tidak kosong.
  * Pastikan Access Point bridging benar ke jaringan yang sama (SSID sama).
  * Periksa apakah perangkat wireless terhubung ke SSID yang benar.
* **PC tidak bisa mengakses UI IoT Server**

  * Cek apakah PC mendapat IP yang valid (`192.168.1.x/24`).
  * Pastikan tidak ada firewall di IoT Server memblokir port HTTP (80).
  * Pastikan alamat IoT Server yang diakses benar (`http://192.168.1.1`).
* **Perangkat tidak merespon perintah**

  * Periksa status konektivitas perangkat di IoT Server (online/offline).
  * Cek log server untuk error protokol (mis. gagal push command).
  * Jika menggunakan gateway AP, cek apakah AP mem-forward paket ke IoT Server.
* **Koneksi wireless terputus-putus**

  * Periksa jarak dan interference (di simulasi, cek channel/AP settings).
  * Restart Access Point dan ulang koneksi device.

---

## 📌 Metadata

* **Author:** Raka
* **Lab:** Simulasi IoT — Smart Home (Kipas & Penyeduh Kopi)
* **Tanggal:** 2025-09-07

-