# 🛠️ Konfigurasi Jaringan Kantor Sederhana — Cisco Packet Tracer Lab

**Deskripsi singkat:**  
Lab ini memperagakan cara membangun jaringan kantor sederhana dengan dua LAN (subnet berbeda) sehingga layanan HTTP dan DNS dapat diakses melalui domain `office.com`. Jaringan ini juga menunjukkan integrasi IoT (kipas dan 3 pintu) serta penggunaan DHCP pada satu LAN dan konfigurasi static pada LAN lainnya.

---

## 🔌 Topologi & Alamat

**lihat di file .pkt**

---

## ⚠️ Disclaimers

- Lab ini **tidak** memasukkan materi kompleks seperti STP, HSRP, OSPF, static routing antar-subnet, atau subnetting lanjutan.
    
- Fokus: konsep garis besar & praktik dasar yang dapat dipelajari dan dikembangkan nantinya.
    

---

## 🔬 10 Konsep Dasar yang Diterapkan (garis besar)

1. **Topologi jaringan** — penempatan switch, server, dan client.
    
2. **IP addressing** — penentuan alamat static dan range DHCP.
    
3. **DHCP** — pemberian IP otomatis untuk client di `192.168.1.0/24`.
    
4. **DNS** — membuat A record `office.com` → IP HTTP server.
    
5. **HTTP hosting** — men-deploy `index.html` di HTTP server untuk domain `office.com`.
    
6. **Koneksi fisik & switching** — kabel, port switch, dan interface `up/down`.
    
7. **Pengaturan client (DNS & Gateway)** — konfig network pada PC client agar resolusi nama bekerja.
    
8. **Integrasi IoT sederhana** — pemberian IP static untuk perangkat IoT (kipas & pintu).
    
9. **Verifikasi layanan** — ping, nslookup, dan akses HTTP dari client.
    
10. **Troubleshooting dasar** — pemeriksaan konektivitas dan service status.
    

---

## 🔬 Fungsi & Manfaat Lab

- **Fungsi utama:** Memahami alur resolusi nama dan akses layanan web pada jaringan lokal bertopologi sederhana.
    
- **Manfaat pembelajaran:**
    
    - Praktik konfigurasi DHCP dan static IP.
        
    - Mengenal cara membuat A record pada DNS lokal.
        
    - Men-deploy dan menguji HTTP server menggunakan domain lokal (`office.com`).
        
    - Mengintegrasikan perangkat IoT dasar ke jaringan kantor.
        
    - Melatih troubleshooting dasar (ping, nslookup, mengecek service).
        

---
## 🛎 langkah-langkah
langkah - langakah beruruan
1. [ ] setup topologi
2. [ ] konfigirasi dns
3. [ ] konfigurasi http
4. [ ] setup ip ( dhcp dan static)
5. [ ] setup wireless
6. [ ] setup komunikasi antar dua ip yang berbeda
7. [ ] konfigurasi FTP
8. [ ] konfigurasi mail server
9. [ ] konfigurasi IoT

---

## 🔍 Expected Result / Verifikasi

- `office.com` terselesaikan (resolved) menjadi `192.168.1.10` oleh DNS lokal.
    
- Browser pada PC Client menampilkan halaman `index.html` dari HTTP server.
    
- `ping office.com` menghasilkan reply dari `192.168.1.10`.
    
- `nslookup office.com 192.168.1.4` mengembalikan A record yang benar.
    
- IoT devices (`192.168.2.10–13`) dapat diakses dari Admin PC (`192.168.2.2`).
    

---

## 🛟 Troubleshooting (Masalah Umum & Solusi)

- **Client tidak dapat resolve nama?**
    
    - Pastikan DNS server (`192.168.1.4`) tercantum di konfigurasi network client atau DHCP pool.
        
    - Cek service DNS aktif pada server dan A record `office.com` telah dibuat.
        
- **HTTP tidak tampil meski resolve benar?**
    
    - Periksa service HTTP aktif dan file `index.html` ada di root web server.
        
    - Periksa firewall pada server (port 80) jika diaktifkan.
        
- **DHCP tidak mendistribusikan alamat?**
    
    - Pastikan DHCP service aktif di `192.168.1.1` dan tidak ada konflik IP.
        
    - Periksa kabel fisik dan port switch/trunk.
        
- **IoT tidak merespon?**
    
    - Pastikan IP static terpasang dengan gateway/network mask benar.
        
    - Periksa protokol komunikasi IoT (MQTT/HTTP) dan port yang digunakan.
        

---

## ✅ Manfaat Pembelajaran (Ringkasan)

- Memahami dasar DNS → HTTP flow pada lingkungan lokal.
    
- Praktik konfigurasi DHCP dan static IP.
    
- Pengenalan integrasi IoT sederhana pada jaringan kantor.
    
- Dasar-dasar verifikasi & troubleshooting layanan jaringan.
    

---

## 📌 Metadata

- **Author:** Raka
    
- **Lab:** Jaringan Kantor Sederhana — office.com
    
- **Tanggal:** 2025-09-14
    

