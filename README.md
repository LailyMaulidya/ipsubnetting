# Praktikum IP Subnetting dan Static Routing

Dokumentasi tugas Komunikasi dan Jaringan Komputer menggunakan **Cisco Packet Tracer**. Repositori ini disusun dalam format Markdown agar mudah dibaca melalui GitHub, dengan struktur dokumentasi yang terinspirasi dari repositori materi jaringan dosen.

## Informasi Praktikum

- **Topik:** IP Subnetting dan Routing
- **Perangkat lunak:** Cisco Packet Tracer
- **Fokus:** konfigurasi IP address, subnet mask, default gateway, routing table, static routing, dan pengujian konektivitas menggunakan `ping`.

## Tujuan

1. Memahami konfigurasi IP address pada PC dan router.
2. Memahami routing table dan konsep next hop.
3. Mengimplementasikan static routing pada topologi dua router.
4. Menguji konektivitas jaringan menggunakan perintah `ping`.

## Isi Repositori

| Berkas/Folder | Keterangan |
|---|---|
| [`laporan.md`](laporan.md) | Laporan praktikum dalam format Markdown |
| [`assets/`](assets/) | Gambar yang diekstrak dari dokumen tugas Word |

## Percobaan

### 1. Routing dengan Satu Router

Satu router menghubungkan dua LAN:

- LAN 1: `192.168.1.0/24`
- LAN 2: `192.168.2.0/24`

Router mengenali kedua jaringan sebagai jaringan yang terhubung langsung setelah interface dikonfigurasi dan diaktifkan. Pengujian `ping` digunakan untuk memeriksa konektivitas dalam satu LAN maupun antarkedua LAN.

### 2. Routing dengan Dua Router

Dua router menghubungkan LAN yang berbeda melalui jaringan transit:

- LAN 1: `192.168.1.0/24`
- Jaringan transit: `192.168.3.0/24`
- LAN 2: `192.168.2.0/24`

Static route pada setiap router digunakan agar masing-masing router mengetahui jalur menuju LAN yang tidak terhubung secara langsung. Konfigurasi harus menyediakan jalur pergi dan jalur kembali.

Contoh perintah static route sesuai rancangan pada laporan:

```text
! Pada Router 1: menuju LAN 2 melalui Router 2
ip route 192.168.2.0 255.255.255.0 192.168.3.2

! Pada Router 2: menuju LAN 1 melalui Router 1
ip route 192.168.1.0 255.255.255.0 192.168.3.1
```

> Sesuaikan alamat IP dan nama interface dengan konfigurasi aktual pada file Packet Tracer.

## Konsep yang Dibahas

- **IP address dan subnet mask:** mengidentifikasi perangkat serta menentukan bagian network dan host.
- **Default gateway:** jalur keluar PC ketika alamat tujuan berada di luar subnet lokal.
- **Routing table:** informasi rute yang digunakan router untuk meneruskan paket.
- **Static routing dan next hop:** rute yang ditambahkan secara manual untuk menjangkau jaringan lain.
- **ARP:** mencari alamat MAC perangkat pada jaringan lokal.
- **ICMP ping:** menguji apakah perangkat tujuan dapat dijangkau.
- **TTL:** membatasi umur paket IP ketika diteruskan oleh router.

Ping pertama yang menampilkan `Request timed out` tidak otomatis membuktikan ARP sebagai penyebabnya. ARP adalah salah satu kemungkinan; penyebab perlu diverifikasi melalui Simulation Mode dan pemeriksaan konfigurasi.


## Referensi

- Materi dosen: [Bab 06 — IP Subnetting](https://github.com/ferryas-pens/computer-and-network-2026/blob/main/bab-06-ip-subnetting.md)
- Repositori materi: [computer-and-network-2026](https://github.com/ferryas-pens/computer-and-network-2026)

---
