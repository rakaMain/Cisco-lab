# 🛠️ Konfigurasi Basic Router — Packet Tracer Lab

**Deskripsi singkat:**
Lab ini memperagungkan cara menghubungkan beberapa jaringan IP berbeda menggunakan sebuah router sehingga dua jaringan berbeda (192.168.1.0/24 dan 192.168.2.0/24) dapat saling berkomunikasi.

---

## 🔌 Topologi & Alamat

**Network:** `192.168.1.0/24` dan `192.168.2.0/24`

**Perangkat:**

* **Router** — menghubungkan kedua subnet; interface:

  * `GigabitEthernet0/0` → `192.168.1.254/24`
  * `GigabitEthernet0/1` → `192.168.2.254/24`

* **PC0** — `192.168.1.1` (gateway: `192.168.1.254`)

* **PC1** — `192.168.1.2` (gateway: `192.168.1.254`)

* **PC2** — `192.168.2.2` (gateway: `192.168.2.254`)

* **PC3** — `192.168.2.1` (gateway: `192.168.2.254`)

* **Switch** — menghubungkan device pada masing-masing subnet (satu switch per subnet atau satu switch dengan VLAN, sesuai kebutuhan lab).

> Pastikan setiap PC memakai subnet mask `255.255.255.0` dan gateway sesuai subnetnya.

---

## 🔬 Fungsi Lab

* Router menghubungkan dua jaringan berbeda sehingga perangkat di `192.168.1.0/24` bisa berkomunikasi dengan perangkat di `192.168.2.0/24`.
* Mempelajari dasar konfigurasi interface pada router (IP address & no shutdown).
* Memahami routing antar-subnet pada jaringan kecil.

---

## 🧾 Konfigurasi Router (rapih)

```
Router> enable
Router# configure terminal
Enter configuration commands, one per line.  End with CNTL/Z.

! Konfigurasi interface untuk subnet 192.168.1.0/24
Router(config)# interface GigabitEthernet0/0
Router(config-if)# ip address 192.168.1.254 255.255.255.0
Router(config-if)# no shutdown
Router(config-if)# exit

! Konfigurasi interface untuk subnet 192.168.2.0/24
Router(config)# interface GigabitEthernet0/1
Router(config-if)# ip address 192.168.2.254 255.255.255.0
Router(config-if)# no shutdown
Router(config-if)# exit

Router(config)# end
Router# write memory
! Opsional: verifikasi
Router# show ip interface brief
```

**Catatan:** Saya merapikan nama interface menjadi `GigabitEthernet0/0` dan `GigabitEthernet0/1` untuk sesuai praktik umum. Jika perangkat Anda menggunakan penomoran berbeda (mis. `GigabitEthernet0/0/0`), sesuaikan nama interface dengan model router di Packet Tracer.

---

## ⚙️ Langkah Singkat (Panduan Pelaksanaan)

1. **Siapkan topologi**: letakkan 1 router, 2 switch (atau 1 switch dengan pengaturan VLAN), dan 4 PC di Packet Tracer.
2. **Koneksikan kabel**: hubungkan PC ke switch, switch ke router (GigabitEthernet0/0 ke switch subnet-1; GigabitEthernet0/1 ke switch subnet-2).
3. **Atur IP pada router**: gunakan konfigurasi di bagian "Konfigurasi Router".
4. **Atur IP pada PC**: tetapkan IP dan gateway sesuai tabel Topologi.
5. **Verifikasi konektivitas lokal**: ping dari PC0 ke gateway (`192.168.1.254`) dan dari PC2 ke gateway (`192.168.2.254`).
6. **Verifikasi antar-subnet**: ping dari PC0 (`192.168.1.1`) ke PC2 (`192.168.2.2`) — harus berhasil jika routing sudah aktif.
7. **Simpan konfigurasi**: `write memory` pada router.

---

## 🔍 Expected Result / Verifikasi

* Router mempunyai alamat IP `192.168.1.254` pada `GigabitEthernet0/0` dan `192.168.2.254` pada `GigabitEthernet0/1`.
* PC di subnet 192.168.1.0/24 dapat ping ke gateway 192.168.1.254.
* PC di subnet 192.168.2.0/24 dapat ping ke gateway 192.168.2.254.
* PC dari subnet berbeda (mis. PC0 → PC2) dapat saling ping, menandakan routing antar-subnet berjalan.
* `show ip interface brief` menampilkan interface up/up dengan alamat yang benar.

---

## 🛟 Troubleshooting (Masalah Umum & Solusi)

* **Interface tidak `up` atau `administratively down`**

  * Pastikan perintah `no shutdown` sudah dijalankan di masing-masing interface.
  * Periksa kabel/fisik koneksi di Packet Tracer.

* **Ping ke gateway gagal**

  * Periksa IP PC dan subnet mask apakah sesuai.
  * Pastikan gateway pada PC diisi dengan IP router yang benar untuk subnet tersebut.

* **Ping antar-subnet gagal**

  * Pastikan kedua interface router berada dalam keadaan `up` dan memiliki IP yang benar.
  * Jika ada firewall atau ACL di router (tidak umum di lab mendasar), pastikan tidak memblokir ICMP.

---

## ✅ Manfaat / Pembelajaran

* 🔎 **Memahami dasar routing antar-subnet**
* 🛠️ **Latihan konfigurasi interface router** dan verifikasi
* 🧭 **Dasar troubleshooting jaringan** (cek interface, IP, kabel)

---

## 📌 Metadata

* **Author:** Raka
* **Lab:** Basic Router
* **Tanggal:** 2025-08-30

