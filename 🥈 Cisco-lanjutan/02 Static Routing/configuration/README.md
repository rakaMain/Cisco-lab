# 🛠️ Konfigurasi Static Routing — Cisco Packet Tracer Lab

**Deskripsi singkat:**
Lab ini memperagakan cara mengonfigurasi *static routing* pada beberapa router di Cisco Packet Tracer agar setiap jaringan dapat saling berkomunikasi secara manual tanpa protokol routing dinamis.

---

## 🔌 Topologi & Alamat

**Network contoh:**

* `192.168.11.0 /24`
* `192.168.12.0 /24`
* `192.168.13.0 /24`
* `192.168.14.0 /24`

**Perangkat:**

* **R1**, **R2**, **R3**, **R4** — router utama yang terhubung antar jaringan
* **PC01** — client pada jaringan pertama (`192.168.11.0/24`)
* **PC02** — client pada jaringan tujuan (`192.168.14.0/24`)

> Setiap router memiliki interface antar-router (mis. G0/0, G0/1) dengan alamat IP berbeda sesuai subnet di atas.
> Routing dilakukan tanpa subnetting tambahan, cukup jaringan /24 untuk setiap segmen.

---

## 🔬 Fungsi Lab

* Mengonfigurasi *static route* agar paket dari PC01 dapat mencapai PC02 melalui beberapa router.
* Memahami fungsi *next hop* dan parameter perintah `ip route`.
* Melihat bagaimana router meneruskan paket sesuai tabel routing manual.

Singkatnya:
**PC01 → R1 → R2 → R3 → R4 → PC02**, dengan rute manual di setiap router.

---

## ✅ Manfaat / Pembelajaran

* 🌐 **Memahami konsep routing manual** tanpa protokol dinamis.
* 🧭 **Belajar tentang next hop**: IP tujuan berikutnya sebelum paket mencapai target akhir.
* 🛠️ **Praktik konfigurasi CLI dasar** pada Cisco Router (`ip route`, `show ip route`).
* 🔎 **Memahami tabel routing** dan cara membaca arah jalur antar-network.
* 📚 **Dasar penting untuk jaringan skala kecil** dan fondasi menuju dynamic routing (RIP, OSPF, BGP).

---

## ⚙️ Langkah Singkat (Panduan Pelaksanaan)

1. **Bangun topologi**: hubungkan empat router (R1–R4) secara berurutan, serta dua PC di ujung jaringan.
2. **Atur IP Address** pada tiap interface router dan PC sesuai subnet topologi.
3. **Aktifkan interface** dengan perintah:

   ```
   Router(config)# interface g0/0
   Router(config-if)# ip address 192.168.x.x 255.255.255.0
   Router(config-if)# no shutdown
   ```
4. **Tambahkan Static Route** pada tiap router:

   ```
   ip route <network> <netmask> <next-hop-ip>
   ```

   Contoh:

   ```
   ip route 192.168.14.0 255.255.255.0 192.168.12.2
   ```
5. **Verifikasi routing table**:

   ```
   show ip route
   ```
6. **Uji koneksi antar-PC** menggunakan `ping`. Jika konfigurasi benar, paket akan diteruskan melewati setiap router.

---

## 🔍 Expected Result / Verifikasi

* Perintah `ping` dari PC01 ke PC02 **berhasil**.
* Setiap router memiliki entri static route yang sesuai di tabel routing.
* Jalur yang ditempuh sesuai urutan R1 → R2 → R3 → R4.
* Tidak ada pesan “Destination Unreachable”.

---

## 🛟 Troubleshooting (Masalah Umum & Solusi)

* **Ping gagal:**

  * Pastikan setiap interface router dalam keadaan `up`.
  * Cek kembali IP dan subnet mask di tiap device.
  * Pastikan perintah `ip route` dimasukkan dengan *next hop* yang benar.
* **Tabel routing kosong:**

  * Gunakan `show running-config` untuk memastikan static route tersimpan.
* **Hanya satu arah yang bisa ping:**

  * Tambahkan static route balik (return route) pada router tujuan agar koneksi dua arah berjalan.

---

## 📘 Catatan Tambahan

**Perintah Dasar Static Route:**

```
ip route <network> <netmask> <next-hop-ip | exit-interface> [administrative-distance]
```

Keterangan:

* `<network>` = jaringan tujuan (mis. 192.168.3.0)
* `<netmask>` = subnet tujuan (mis. 255.255.255.0 untuk /24)
* `<next-hop-ip>` = alamat IP router berikutnya menuju jaringan tujuan
* `[administrative-distance]` = opsional, nilai prioritas rute (semakin kecil semakin dipercaya)

---

## 📌 Metadata

* **Author:** Raka
* **Lab:** Konfigurasi Static Routing
* **Tanggal:** 2025-11-07


