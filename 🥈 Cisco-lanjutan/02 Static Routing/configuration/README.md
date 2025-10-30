apa yang akan saya sampaikan
1. apa itu routing
2. routing table on a cisco
3. routing fundamental
4. jenis routing
5. langsung membahas static routing praktic

static routing practice
konifgurasi konfigurasi dan isi dari ip route
konfigurasi gateway nya juga

static route mencari rute terbaik untuk meneuju kedestinasi
atau bisa di tentukan dengan cara

**next hop**
ip route 192.168.4.0 255.255.255.0 [ 192.168.13.3( rute yang ingin di laui) ]
atau bisa disebut next hop

dan juga konfigurasi router yang lain untuk melncarkan sebuah ping

**exit-interface** 
ip add netmask exit-interface
192.168.4.0 255.255.255.0 g0/1
atau isa juga di tambahakn next-hop
192.168.4.0 255.255.255.0 g0/1 192.168.13.3

**default route**
isi nya adalah 0.0.0.0/0 jadi menginput semua destinasi ip add
jika gak ada spesifik pakai default route
biasanya kalo ke internet

ip route 0.0.0.0 0.0.0.0 203.0.113.2 => yang langsung ke internet


---

Static routing adalah metode pengaturan rute di router di mana alamat tujuan dan jalur yang harus dilewati ditambahkan secara manual oleh administrator ke tabel routing. Dengan static route, router tidak perlu menjalankan protokol routing dinamis — ia hanya mengikuti instruksi yang sudah dikonfigurasi, sehingga sederhana, hemat sumber daya, dan sangat deterministik. Kelemahannya: tidak skalabel untuk jaringan besar dan tidak otomatis menyesuaikan jika terjadi perubahan topologi atau kegagalan jalur; setiap perubahan harus diubah secara manual oleh admin.

Rute bus pariwisata yang tetap: bus hanya lewat rute yang sudah ditentukan; rute baru tidak otomatis ditambahkan