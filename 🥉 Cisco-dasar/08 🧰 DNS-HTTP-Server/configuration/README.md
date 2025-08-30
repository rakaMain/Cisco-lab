# 🛠️ Konfigurasi DNS & HTTP Server — Cisco Packet Tracer Lab

**Deskripsi singkat:**  
Lab ini memperagakan cara menyiapkan layanan HTTP dan DNS pada jaringan lokal sehingga dua PC client dapat mengakses `raka.com` dan diarahkan ke IP server HTTP (`192.168.1.1`) melalui DNS yang kita konfigurasikan.

---

## 🔌 Topologi & Alamat

**Network:** `192.168.1.0 / 24`

**Perangkat:**

- **HTTP Server** (`raka.com`) — `192.168.1.1`
    
- **DNS Server** (A record: `raka.com` → `192.168.1.1`) — `192.168.1.4`
    
- **PC Client 1** — `192.168.1.2`
    
- **PC Client 2** — `192.168.1.3`
    
- **Switch** — menghubungkan semua device di jaringan
    

> Semua device gunakan gateway dan subnet mask yang sesuai jika diperlukan (mis. gateway jika terhubung ke router). Untuk lab sederhana ini, cukup gunakan switch dan alamat IP di jaringan `192.168.1.0/24`.

---

## 🔬 Fungsi Lab

- DNS Server akan menerjemahkan nama domain `raka.com` menjadi alamat IP `192.168.1.1`.
    
- HTTP Server menyajikan konten web (halaman HTML) yang akan diakses melalui browser client.
    
- PC client menggunakan konfigurasi DNS di pengaturan jaringannya untuk melakukan resolusi nama domain sebelum membuka halaman web.
    

Singkatnya: **Client → DNS resolve `raka.com` → dapatkan `192.168.1.1` → request HTTP ke `192.168.1.1` → tampil halaman.**

---

## ✅ Manfaat / Pembelajaran

- 🔎 **Memahami mekanisme DNS**: bagaimana nama domain diterjemahkan menjadi IP.
    
- 🌐 **Praktik hosting web dasar**: men-deploy layanan HTTP pada server lokal.
    
- 🧭 **Konfigurasi layanan di Packet Tracer**: IP assignment, service configuration, dan verifikasi.
    
- 🛠️ **Troubleshooting dasar layanan jaringan**: cara cek DNS, ping, dan akses HTTP untuk menemukan masalah.
    
- 📚 **Dasar penerapan konsep nyata** yang bisa diterapkan pada jaringan skala kecil hingga menengah.
    

---

## ⚙️ Langkah Singkat (Panduan Pelaksanaan)

1. **Siapkan topology**: letakkan 1 switch, 2 PC, 2 Server (HTTP & DNS) di Packet Tracer.
    
2. **Atur IP** pada tiap device sesuai tabel Topologi.
    
3. **Konfigurasikan HTTP Server** (`192.168.1.1`): aktifkan service HTTP, unggah file `index.html` sederhana.
    
4. **Konfigurasikan DNS Server** (`192.168.1.4`): buat A record `raka.com` → `192.168.1.1`.
    
5. **Set DNS di tiap PC**: pada pengaturan IP client, masukkan alamat DNS `192.168.1.4`.
    
6. **Uji koneksi**: buka web browser di PC, akses `http://raka.com` → halaman dari HTTP server harus tampil.
    
7. **Verifikasi tambahan**: `ping raka.com` harus resolve menjadi `192.168.1.1` sebelum ping berjalan.
    

---

## 🔍 Expected Result / Verifikasi

- `raka.com` terselesaikan (resolved) menjadi `192.168.1.1`.
    
- Browser pada PC1 & PC2 menampilkan halaman `index.html` dari HTTP server.
    
- Perintah `ping raka.com` berhasil (reply dari `192.168.1.1`).
    
- Jika `nslookup` tersedia: `nslookup raka.com 192.168.1.4` mengembalikan A record yang benar.
    

---

## 🛟 Troubleshooting (Masalah Umum & Solusi)

- **Tidak bisa resolve nama?**
    
    - Pastikan DNS server IP tercantum di konfigurasi network client.
        
    - Cek service DNS di server (service DNS aktif dan A record benar).
        
- **Tidak bisa akses HTTP meski resolve benar?**
    
    - Periksa service HTTP aktif di server dan file `index.html` ada.
        
    - Pastikan firewall (jika digunakan) mengizinkan port 80.
        
- **Ping gagal antar device?**
    
    - Periksa subnet mask dan physical connection (cable + port switch).
        
    - Pastikan interface di server/PC dalam keadaan `up`.
        

---

## 📌 Metadata

- **Author:** Raka
    
- **Lab:** Konfigurasi DNS & HTTP Server
    
- **Tanggal:** 2025-08-30
    
