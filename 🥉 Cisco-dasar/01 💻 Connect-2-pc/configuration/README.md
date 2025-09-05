# 🛠️ Konfigurasi DHCP Server — Cisco Packet Tracer Lab

**Deskripsi singkat:**
Lab ini memperagakan cara men-setup DHCP di Cisco Packet Tracer sehingga PC klien menerima konfigurasi IP secara dinamis (otomatis) tanpa perlu konfigurasi manual.

---

## 🔌 Topologi & Alamat

**Network:** `192.168.1.0 / 24`

**Perangkat:**

* **DHCP Server / Router (menyediakan DHCP)** — `192.168.1.1`
  *(menggunakan server)*

* **PC Client 1** — \[DHCP] (mengharapkan IP dari `192.168.1.10` sampai `192.168.1.19`)

* **PC Client 2** — \[DHCP]

* **PC Client 3** — \[DHCP]

* **Switch** — menghubungkan semua device di jaringan

> Untuk pool 10 client, IP yang akan diberikan umumnya `192.168.1.10` — `192.168.1.19`. Pastikan alamat statis (seperti `.1`) dikecualikan dari pool.

---

## 🔬 Fungsi Lab

* DHCP Server memberikan IP secara dinamis kepada PC sehingga user tidak perlu konfigurasi manual.
* Memberikan parameter jaringan tambahan ke klien seperti default-gateway dan domain-name (atau DNS jika diperlukan).
* Praktik ini berguna untuk memahami manajemen alamat IP otomatis pada jaringan lokal.

---

## ✅ Manfaat / Pembelajaran

* ⚡ **Otomatisasi konfigurasi IP** pada jaringan kecil/menengah.
* 🧩 **Menghindari konflik IP** dengan penggunaan excluded-address dan pengelolaan pool yang benar.
* 🔁 **Verifikasi & troubleshooting DHCP**: memeriksa binding, lease, dan alokasi alamat.
* 📚 **Pengenalan perintah Cisco dasar untuk DHCP** (berguna untuk lab dan persiapan sertifikasi dasar).

---

## 🔍 Expected Result / Verifikasi

* PC1, PC2, PC3 menerima IP secara otomatis dalam rentang `192.168.1.10` — `192.168.1.19`.
* `show ip dhcp binding` di server menampilkan binding IP → MAC untuk masing-masing PC.
* `ping 192.168.1.1` dari tiap PC berhasil (reply).
* Gateway pada PC ter-set ke `192.168.1.1`.
* Jika DNS diatur, pengujian name resolution (jika ada service DNS) harus sesuai.


---

## 📌 Metadata

* **Author:** Raka
* **Lab:** DHCP Server di Cisco Packet Tracer
* **Tanggal:** 2025-09-05

---
