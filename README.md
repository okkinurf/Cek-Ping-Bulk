# 📡 IP Status Checker

Script sederhana untuk mengecek status **UP/DOWN** dari list IP menggunakan `ping`.  
Setiap IP akan dicek, hasilnya ditampilkan dengan warna hijau (UP) atau merah (DOWN) lengkap dengan timestamp.

---

## 📥 Instalasi

Clone repo atau simpan script:

```bash
git clone https://github.com/username/ip-status-checker.git
cd ip-status-checker
chmod +x check-ip.sh
```

## 📋 Persiapan

Buat file list-ip.txt yang berisi daftar IP.
Contoh isi file:
```
8.8.8.8
1.1.1.1
192.168.1.1/23
10.10.10.10
```

👉 Script akan otomatis menghapus /23 atau subnet lain, hanya mengambil IP utamanya.

## ▶️ Cara Menjalankan

```
./check-ip.sh
```

Output contoh:
```
8.8.8.8            : UP !!      [2025-09-19 00:10:01]
1.1.1.1            : UP !!      [2025-09-19 00:10:01]
192.168.1.1        : DOWN       [2025-09-19 00:10:01]
10.10.10.10        : UP !!      [2025-09-19 00:10:01]
```

## ⚙️ Fitur

✅ Warna output (Hijau = UP, Merah = DOWN)

✅ Multi IP dari file list-ip.txt

✅ Parallel check (lebih cepat)

✅ Ada timestamp hasil pengecekan

## 🛠️ Dibangun dengan

bash
ping
awk
