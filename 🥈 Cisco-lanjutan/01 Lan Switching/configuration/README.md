# 🛠️ Ethernet LAN Switching — Cisco Packet Tracer Lab

**Deskripsi singkat:**
Lab ini membahas konsep LAN switching, ARP, dan MAC address table (CAM table) beserta langkah praktik di Cisco Packet Tracer untuk memahami cara switch meneruskan frame berdasarkan tabel MAC.

---

## 🔌 Topologi & Alamat (Contoh)

**Network:** `192.168.1.0 / 24`

**Perangkat:**

* **PC1** — `192.168.1.1`
* **PC2** — `192.168.1.2`
* **PC3** — `192.168.1.3`
* **PC4** — `192.168.1.4`
* **Switch01** — menghubungkan PC1 & PC2
* **Switch02** — menghubungkan PC3 & PC4
* **Link trunk/connection** antara Switch01 dan Switch02 (mis. Ge0/1)

> Topologi sederhana: dua switch yang dihubungkan, masing-masing punya port ke PC. IP di jaringan `192.168.1.0/24`.

---

## 🔬 Fungsi Lab

* Memahami **LAN switching**: bagaimana switch mempelajari MAC sumber dan membuat MAC table.
* Memahami **ARP**: mekanisme ARP Request (broadcast) dan ARP Reply (unicast).
* Praktek perintah CLI: `show mac address-table`, `clear mac address-table`, dan `ping`.

---

## 🔎 Penjelasan Singkat

**LAN Switching** adalah proses pengiriman frame di OSI Layer 2. Switch membangun tabel MAC (MAC address table) dengan mempelajari alamat MAC sumber pada frame yang diterima. Jika alamat tujuan sudah ada di tabel, switch meneruskan frame hanya ke port tujuan; jika belum, switch melakukan flooding (broadcast) ke semua port.

**ARP (Address Resolution Protocol)** menerjemahkan alamat IP (Layer 3) menjadi alamat MAC (Layer 2).

* **ARP Request** dikirim sebagai broadcast.
* **ARP Reply** dikirim sebagai unicast ke peminta.

**MAC Address Table (CAM table)** menyimpan pasangan MAC ↔ port sehingga switch dapat meneruskan frame secara selektif.

---

## ✅ Fungsi & Contoh Proses (Simulasi singkat)

1. **PC1 (192.168.1.1)** mengirim paket ke **PC3 (192.168.1.3)**.

   * Jika MAC PC3 belum ada di tabel, Switch01 melakukan flooding ARP Request.
   * PC3 merespons dengan ARP Reply (unicast) termasuk MAC-nya.
   * Switch belajar MAC PC3 & mencatat port yang terhubung.
2. Setelah tabel terisi, frame berikutnya akan dikirim langsung ke port tujuan tanpa flooding.

---

## ⚙️ Langkah Singkat (Panduan Pelaksanaan di Packet Tracer)

1. **Siapkan topology**: 2 switch, 4 PC, hubungkan sesuai topologi.
2. **Atur IP** pada tiap PC sesuai tabel Topologi.
3. **Tes ARP**: dari PC1 `ping 192.168.1.3` — amati ARP Request/Reply.
4. **Tampilkan MAC table** di switch: `show mac address-table`.
5. **Hapus MAC table** untuk uji ulang: `clear mac address-table` (atau `clear mac address-table dynamic`).
6. **Tes konektivitas ICMP**: `ping 192.168.1.3` dan verifikasi reply.

---

## 🔍 Expected Result / Verifikasi

* Setelah ARP Reply, switch menunjukkan entri MAC pada port yang benar (`show mac address-table`).
* `ping` antar PC memberikan `Echo Reply` bila jaringan terhubung dan ARP berhasil.
* Setelah `clear mac address-table`, switch kembali melakukan flooding saat alamat tujuan belum diketahui.

---

## 🛟 Troubleshooting (Masalah Umum & Solusi)

* **Frame selalu di-flooding (flooding terus-menerus)**:

  * Periksa apakah MAC table tidak tersimpan (memory issue) atau switch dalam mode learning disabled.
  * Pastikan tidak ada loop fisik tanpa spanning tree (STP) — periksa kabel dan konfigurasi.
* **ARP tidak mendapat reply**:

  * Pastikan IP target benar dan host dalam kondisi `up`.
  * Periksa firewall host yang mungkin memblok ICMP/ARP responses.
* **Perintah CLI tidak muncul hasil**: pastikan akses ke mode exec pada switch dan gunakan perintah yang benar (`show mac address-table`).

---

## 📌 Metadata

* **Author:** Raka
* **Lab:** Ethernet LAN Switching (Cisco Packet Tracer)
* **Tanggal:** 2025-10-16

---

## File PDF yang saya buat

* [Download ICMP_Konfigurasi_Lab.pdf](/mnt/data/ICMP_Konfigurasi_Lab.pdf)
* [Download Ethernet_LAN_Switching_Lab.pdf](/mnt/data/Ethernet_LAN_Switching_Lab.pdf)

---

