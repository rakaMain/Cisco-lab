
---

## Format umum `ip route`

Sintaks umum:

```
ip route <network> <netmask> <next-hop-ip | exit-interface> [administrative-distance]
```

Keterangan singkat:

- `<network>` = jaringan tujuan (contoh `192.168.3.0`)
    
- `<netmask>` = netmask tujuan (contoh `255.255.255.0` untuk /24)
    
- `<next-hop-ip>` = alamat IP router selanjutnya (gateway) menuju network tujuan  
    **atau**  
    `<exit-interface>` = interface lokal (mis. `GigabitEthernet0/0`) untuk keluar paket
    
- `[administrative-distance]` = opsional, prioritas rute (angka kecil = lebih dipercaya)
    

---

## R1 (baris yang kamu tulis)

Asli:

```
ip route 192.168.3.0 2(ip tujuan) 255.255.255.0 192.168.12.2
do sh ip route
```

**Interpretasi & koreksi**  
Sepertinya ada kekacauan urutan/penulisan. Bentuk yang benar kemungkinan maksudnya:

```
ip route 192.168.3.0 255.255.255.0 192.168.12.2
```

Artinya:

- Buat rute statis ke jaringan **192.168.3.0/24**
    
- Next-hop (gateway) adalah **192.168.12.2** — artinya R1 akan mengirim paket ke alamat ini untuk mencapai network 192.168.3.0.
    
- `do show ip route` (singkat `do sh ip route`) digunakan ketika kamu berada di mode konfigurasi (`config>`) untuk menjalankan perintah show — menampilkan tabel routing saat ini. (Di exec mode cukup `show ip route`.)
    

Di tabel routing rute ini akan tampil sebagai `S 192.168.3.0/24 [1/0] via 192.168.12.2` (S = static).

---

## R2

Asli:

```
ip route 192.168.1.0/24 (ip asal) 255.255.255.0 g0/0
ip route 192.168.3.0 2(ip tujuan) 255.255.255.0 192.168.13.3
```

**Interpretasi & koreksi**  
Kemungkinan maksud baris pertama:

```
ip route 192.168.1.0 255.255.255.0 GigabitEthernet0/0
```

Artinya:

- R2 menyatakan bahwa untuk mencapai **192.168.1.0/24**, paket dikirim keluar lewat interface **G0/0** (tanpa menyebut next-hop IP). Ini biasanya dipakai jika jaringan tujuan langsung terhubung ke segmen yang bisa dijangkau via interface tersebut.
    

Baris kedua yang dikoreksi:

```
ip route 192.168.3.0 255.255.255.0 192.168.13.3
```

Artinya:

- Tambah rute statis ke **192.168.3.0/24** dengan next-hop **192.168.13.3**.
    

---

## R3

Asli:

```
ip route 192.168.1.0/24 (ip asal) 255.255.255.0 192.168.13.2
```

**Interpretasi & koreksi**  
Bentuk yang benar kemungkinan:

```
ip route 192.168.1.0 255.255.255.0 192.168.13.2
```

Artinya:

- R3 menambahkan rute statis ke **192.168.1.0/24** melalui next-hop **192.168.13.2**.
    

---

## Ringkasan efek pada jaringan (secara logika)

- R1 tahu cara mencapai 192.168.3.0 dengan mengirim ke 192.168.12.2.
    
- R2 tahu cara menuju 192.168.1.0 lewat interface G0/0 (langsung keluar) dan juga tahu 192.168.3.0 lewat 192.168.13.3.
    
- R3 tahu cara menuju 192.168.1.0 lewat 192.168.13.2.
    

Jika next-hop yang ditentukan **tidak reachable** (mis. alamat 192.168.12.2 tidak berada di jaringan yang terhubung), maka paket tidak akan dikirim dengan benar — static route bersifat _recursive_: router akan melakukan lookup ke routing table untuk mengetahui bagaimana mencapai next-hop itu.

---

## Catatan penting / best practices

- **Urutan parameter penting**: selalu `network` lalu `mask` lalu `next-hop` atau `exit-interface`.
    
- Di IOS klasik, **jangan** tulis `192.168.1.0/24` dan mask bersamaan pada satu command — gunakan `192.168.1.0 255.255.255.0`. (Beberapa versi modern mendukung prefix-length, tapi umumnya pakai mask.)
    
- Kalau memakai **exit-interface** (mis. `GigabitEthernet0/0`) tanpa next-hop, pastikan interface itu berada pada segmen broadcast yang benar dan router lain ada di situ.
    
- Jika menggunakan **next-hop IP**, pastikan next-hop itu reachable (ada route/connected) — jika tidak, rute statis akan gagal digunakan.
    
- Untuk menghapus: `no ip route <network> <mask> <next-hop|interface>`.
    
- Untuk melihat rute statis di tabel routing: `show ip route` (akan ditandai `S`).
    
- Jika ingin fallback atau prioritas lain, tambahkan `administrative-distance` terakhir (mis. `ip route ... 192.168.13.3 200`).
    
