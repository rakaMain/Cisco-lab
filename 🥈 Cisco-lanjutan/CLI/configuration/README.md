
## 1. **Pendahuluan** 🗂️

### 1.1 Pendahuluan 🎯

Modul “Dasar CLI pada Perangkat Cisco” ini akan membantu kamu:

- 🔌 **Memahami** apa itu CLI dan cara mengaksesnya.
    
- ⚙️ **Mengenali** mode‑mode operasi di CLI.
    
- 🛠️ **Belajar** perintah dasar konfigurasi, penyimpanan, dan troubleshooting.
    

**Petunjuk Penggunaan** 📘

1. Baca setiap sub‑bab berurutan.
    
2. Praktikkan langsung pada perangkat atau emulator (PacketTracer/GNS3).
    
3. Kerjakan latihan di akhir modul untuk memperkuat pemahaman.
    

---

## 2. **Isi Inti** 📚

### 2.1 Apa itu CLI? 💻

**Command‑Line Interface (CLI)** adalah antarmuka teks yang memungkinkan kamu mengonfigurasi dan mengelola perangkat jaringan Cisco secara langsung. CLI hanya memerlukan terminal (Putty, TeraTerm) dan kabel console (RJ‑45 → USB atau mini‑USB).

**Cara Akses CLI:**

- **Port Console:** Kabel rollover (RJ‑45 ke DB‑9) → adapter USB → komputer.
    
- **SSH/Telnet:** Setelah perangkat ter‑IP, buka Putty → pilih SSH → masukkan IP & port.
    

---

### 2.2 Navigasi & Bantuan di CLI 🆘

- **`?`** – Tampilkan daftar perintah atau parameter ketika ragu.
    
- **`<Tab>`** – Auto‑lengkapi perintah jika sebagian sudah diketik.
    
- **`Ctrl+Z`** – Kembali ke privileged exec mode dari mode konfigurasi.
    
- **`Ctrl+C`** – Batal perintah yang sedang diketik.
    

---

### 2.3 Mode Operasi CLI ⚙️

| Mode                     | Prompt                                       | Fungsi                                              |
| ------------------------ | -------------------------------------------- | --------------------------------------------------- |
| **User Exec**            | `Router>`                                    | Lihat status & statistik, tidak untuk konfigurasi.  |
| **Privileged Exec**      | `Router#`                                    | Akses perintah debugging & konfigurasi lanjutan.    |
| **Global Configuration** | `Router(config)#`                            | Ubah konfigurasi perangkat secara keseluruhan.      |
| **Sub‑Configuration**    | `Router(config-if)#`, `Router(config-line)#` | Konfigurasi interface, line, routing protocol, dll. |

**Pindah Mode:**

```shell
Router> enable             ← ke Privileged Exec  
Router# configure terminal ← ke Global Configuration  
Router(config)# interface GigabitEthernet0/0  ← ke Interface Config  
```

---

### 2.4 Perintah Dasar Konfigurasi 🛠️

1. **Set Password & Keamanan**
    
    ```shell
    Router(config)# enable password ccna  
    Router(config)# enable secret Cisco123    ← lebih aman (ter‑hash)  
    Router(config)# service password-encryption ← encrypt semua password plain-text  
    ```
    
    - `enable password` hanya enkripsi sederhana.
        
    - `enable secret` menggunakan MD5 hash, lebih sulit di‑buka.
        
2. **Mengelola Konfigurasi**
    
    - **Running‑Config**: konfigurasi aktif di RAM.
        
        ```shell
        Router# show running-config
        ```
        
    - **Startup‑Config**: konfigurasi yang akan dimuat saat restart (NVRAM).
        
        ```shell
        Router# show startup-config
        ```
        
3. **Menyimpan & Memuat Konfigurasi**
    
    ```shell
    Router# write memory      ← simpan running-config ke startup-config  
    Router# copy running-config startup-config  
    ```
    
4. **Membatalkan Perintah**
    
    - Tambahkan `no` di depan perintah untuk menghapus atau menonaktifkan:
        
        ```shell
        Router(config)# no interface GigabitEthernet0/1  
        Router(config)# no ip routing  
        ```
        

---

### 2.5 Contoh Kasus & Praktik 📝

> **Skenario:**  
> Kamu ingin mengamankan akses ke router dan menyimpan konfigurasi dasar.
> 
> **Langkah‑langkah:**
> 
> 1. Akses CLI via console → masuk ke Privileged Exec (`enable`).
>     
> 2. Masuk ke Global Configuration (`configure terminal`).
>     
> 3. Set password:
>     
>     ```shell
>     Router(config)# enable secret MyS3cret!
>     Router(config)# service password-encryption
>     ```
>     
> 4. Verifikasi:
>     
>     ```shell
>     Router# show running-config | include secret
>     ```
>     
> 5. Simpan konfigurasi:
>     
>     ```shell
>     Router# write memory
>     ```
>     

---

### 2.6 Latihan & Evaluasi ✅

1. **Praktik:** Hubungkan ke router via Putty, ubah prompt menjadi menampilkan nama host, lalu simpan konfigurasi.
    
2. **Soal Teori:** Jelaskan perbedaan `enable password` vs `enable secret`!
    
3. **Troubleshoot:** Coba batalkan konfigurasi interface FastEthernet0/0 dengan perintah `no`, lalu cek hasilnya.
    

---

## 3. **Penutup** 🎓

### 3.1 Rangkuman ✨

- CLI memungkinkan konfigurasi langsung perangkat Cisco lewat terminal.
    
- Tiga mode utama: User Exec (`>`), Privileged Exec (`#`), Global Configuration (`(config)#`).
    
- Perintah dasar meliputi set password, show running-config, dan save config.
    
- Gunakan `?`, `<Tab>`, & `no` untuk bantuan, auto‑lengkapi, dan membatalkan perintah.
    

### 3.2 Daftar Pustaka & Referensi 📚

1. Cisco Systems. _Cisco IOS Command Reference_.
    
2. Odom, W. _CCNA Routing and Switching 200-125 Official Cert Guide_.
    

### 3.3 Glosarium 📖

- **CLI**: Command‑Line Interface.
    
- **Rollover Cable**: Kabel console Cisco.
    
- **Running‑Config**: Konfigurasi aktif.
    
- **Startup‑Config**: Konfigurasi saat boot.
    

### 3.4 Lampiran 📎

- **Tabel Prompt & Mode** (ringkasan).
    
- **Diagram Alur Mode CLI**.
    

---
