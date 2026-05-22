# Panduan Instalasi Arch Linux di VirtualBox dengan `archinstall`

Panduan ini dibuat untuk kondisi ketika kamu sudah berada di layar **Arch Linux live installer** seperti ini:

```text
Arch Linux ... (tty1)
archiso login: root (automatic login)
root@archiso ~ #
```

Cara paling mudah untuk pemula adalah memakai **`archinstall`**, yaitu installer terpandu resmi yang tersedia di ISO Arch Linux.

---

## 0. Catatan Penting Sebelum Mulai

- Panduan ini ditujukan untuk instalasi **Arch Linux di Oracle VirtualBox**.
- Proses instalasi akan menghapus isi **disk virtual** di VirtualBox, bukan hard disk Windows kamu, selama kamu memilih disk VM yang benar.
- Jika masih ragu, pastikan kamu tidak memilih disk fisik Windows. Biasanya di VirtualBox disk akan muncul sebagai:
  - `/dev/sda`
  - `/dev/vda`
  - atau disk lain dengan ukuran sesuai yang kamu buat di VirtualBox.

---

## 1. Navigasi di Menu `archinstall`

Di menu `archinstall`, gunakan tombol berikut:

| Tombol | Fungsi |
|---|---|
| Panah atas / bawah | Pindah menu |
| Enter | Pilih menu |
| Esc | Kembali |
| `/` | Search |
| Ctrl + Q | Keluar |
| F1 | Show/Hide help |

---

## 2. Cek Internet

Sebelum menjalankan installer, cek internet dulu.

Ketik:

```bash
ping archlinux.org
```

Kalau muncul balasan seperti ini:

```text
64 bytes from ...
```

berarti internet sudah jalan.

Untuk berhenti dari `ping`, tekan:

```text
Ctrl + C
```

Kalau internet tidak jalan, cek setting VirtualBox:

```text
VirtualBox > Settings > Network > Adapter 1
Enable Network Adapter: ON
Attached to: NAT
```

Lalu restart VM.

---

## 3. Jalankan Installer

Di terminal Arch, ketik:

```bash
archinstall
```

Setelah itu akan muncul menu instalasi.

---

## 4. Isi Menu Utama `archinstall`

Isi bagian-bagian berikut satu per satu.

---

### 4.1 Archinstall Language

Pilih:

```text
English
```

---

### 4.2 Locales

Masuk ke menu **Locales**.

Rekomendasi:

```text
Keyboard layout: us
Locale language: en_US
Locale encoding: UTF-8
```

Kalau tersedia pilihan waktu/format regional, kamu boleh tetap pakai default.

---

### 4.3 Mirrors and Repositories

Masuk ke:

```text
Mirrors and repositories
```

Pilih region terdekat, misalnya:

```text
Indonesia
```

Kalau Indonesia lambat atau bermasalah, pilih:

```text
Singapore
```

Repository tambahan biasanya tidak perlu diubah untuk instalasi awal.

---

### 4.4 Disk Configuration

Masuk ke:

```text
Disk configuration
```

Pilih:

```text
Use a best-effort default partition layout
```

Lalu pilih disk virtual kamu, biasanya:

```text
/dev/sda
```

Kalau ditanya filesystem, pilih:

```text
ext4
```

Kalau ditanya disk encryption, pilih:

```text
No
```

Rekomendasi sederhana:

```text
Partition layout: default
Filesystem: ext4
Encryption: No
```

---

### 4.5 Swap

Masuk ke menu **Swap**.

Untuk VirtualBox, pilih:

```text
True / Enabled
```

atau pilih default saja jika sudah aktif.

---

### 4.6 Bootloader

Masuk ke:

```text
Bootloader
```

Pilih:

```text
GRUB
```

GRUB adalah pilihan aman untuk instalasi Arch Linux di VirtualBox.

---

### 4.7 Kernels

Masuk ke:

```text
Kernels
```

Pilih:

```text
linux
```

Tidak perlu memilih terlalu banyak kernel untuk instalasi awal.

---

### 4.8 Hostname

Masuk ke:

```text
Hostname
```

Isi nama komputer virtual kamu, misalnya:

```text
arch-vm
```

---

## 5. Authentication: Root Password atau User Sudo

Jika muncul pesan:

```text
Missing configurations:
- Either root-password or at least 1 user with sudo privileges must be specified
```

artinya kamu belum membuat password root atau user dengan hak sudo.

Masuk ke menu:

```text
Authentication
```

Kamu punya dua pilihan.

---

### Opsi A — Buat User Biasa dengan Sudo

Ini opsi yang paling direkomendasikan.

Pilih:

```text
User account
```

Lalu isi:

```text
Username: michael
Password: isi password kamu
Confirm password: ulangi password
```

Jika ada pertanyaan:

```text
Should this user be a superuser?
```

atau:

```text
Allow sudo?
```

pilih:

```text
Yes
```

Setelah selesai, tekan:

```text
Esc
```

untuk kembali ke menu utama.

---

### Opsi B — Buat Root Password

Kalau kamu hanya ingin membuat password root, pilih:

```text
Root password
```

Masukkan password dua kali.

Saat mengetik password, karakter password biasanya **tidak terlihat** di layar. Itu normal.

Setelah selesai, tekan:

```text
Esc
```

untuk kembali ke menu utama.

---

### Rekomendasi

Lebih baik buat user biasa dengan sudo, misalnya:

```text
Username: michael
Sudo: Yes
```

Root password boleh dibuat juga, tetapi tidak wajib kalau sudah ada user dengan sudo.

---

## 6. Profile: Pilih Desktop Environment

Masuk ke:

```text
Profile
```

Pilih:

```text
Desktop
```

Lalu pilih salah satu desktop environment.

Rekomendasi untuk pemula:

```text
KDE Plasma
```

atau:

```text
GNOME
```

Untuk VirtualBox, KDE Plasma biasanya nyaman dan tampilannya familiar.

---

## 7. Graphics Driver

Saat memilih graphics driver, pilih:

```text
All open-source
```

Kalau ada pilihan khusus VirtualBox/VM, boleh pilih itu.

---

## 8. Audio

Masuk ke bagian Audio, pilih:

```text
PipeWire
```

---

## 9. Network Configuration

Masuk ke:

```text
Network configuration
```

Pilih:

```text
NetworkManager
```

Ini penting agar internet mudah digunakan setelah instalasi selesai.

---

## 10. Pacman

Bagian **Pacman** biasanya bisa dibiarkan default.

Kalau ada pilihan parallel downloads, boleh aktifkan.

---

## 11. Additional Packages

Masuk ke:

```text
Additional packages
```

Isi paket tambahan berikut:

```text
nano vim git firefox base-devel networkmanager
```

Kalau kamu memakai KDE Plasma, boleh tambahkan juga:

```text
konsole dolphin
```

Jadi contoh lengkapnya:

```text
nano vim git firefox base-devel networkmanager konsole dolphin
```

Catatan:
- `firefox` = browser
- `git` = alat developer
- `base-devel` = paket dasar untuk build aplikasi
- `nano` / `vim` = text editor terminal
- `konsole` = terminal KDE
- `dolphin` = file manager KDE

---

## 12. Timezone

Masuk ke:

```text
Timezone
```

Pilih:

```text
Asia/Jakarta
```

---

## 13. Automatic Time Sync / NTP

Masuk ke:

```text
Automatic time sync (NTP)
```

Pilih:

```text
True / Enabled
```

---

## 14. Cek Missing Configuration

Setelah semua diisi, lihat bagian kanan layar.

Kalau masih ada tulisan:

```text
Missing configurations
```

berarti masih ada bagian yang belum lengkap.

Yang paling sering belum lengkap:
- Belum buat root password atau user sudo
- Belum pilih disk
- Belum pilih bootloader
- Belum pilih kernel
- Belum pilih network configuration

Kalau sudah tidak ada pesan error, lanjut ke instalasi.

---

## 15. Mulai Instalasi

Pilih menu:

```text
Install
```

Lalu tekan:

```text
Enter
```

Installer akan meminta konfirmasi. Pilih:

```text
Yes
```

Tunggu proses instalasi sampai selesai.

Proses ini bisa memakan waktu beberapa menit tergantung koneksi internet.

---

## 16. Setelah Instalasi Selesai

Jika muncul pertanyaan:

```text
Would you like to chroot into the newly created installation?
```

Pilih:

```text
No
```

Setelah itu reboot:

```bash
reboot
```

---

## 17. Lepaskan ISO Installer dari VirtualBox

Saat VM restart, kamu harus melepas ISO Arch Linux agar tidak masuk lagi ke installer.

Di menu VirtualBox, pilih:

```text
Devices > Optical Drives > Remove disk from virtual drive
```

Kalau muncul konfirmasi, pilih:

```text
Force Unmount
```

Lalu biarkan VM boot lagi.

Kalau berhasil, kamu akan masuk ke Arch Linux yang sudah terinstall.

---

## 18. Login Pertama Kali

Login menggunakan user yang kamu buat, misalnya:

```text
Username: michael
Password: password kamu
```

Kalau kamu install desktop, seharusnya muncul layar login grafis.

Kalau yang muncul terminal, login dulu lalu jalankan:

```bash
sudo systemctl enable --now NetworkManager
```

Jika memakai KDE, pastikan display manager aktif:

```bash
sudo systemctl enable --now sddm
```

Untuk GNOME:

```bash
sudo systemctl enable --now gdm
```

---

## 19. Update Sistem Setelah Install

Setelah masuk Arch Linux, update sistem:

```bash
sudo pacman -Syu
```

---

## 20. Install VirtualBox Guest Utils

Supaya tampilan VM lebih nyaman, install VirtualBox Guest Utils:

```bash
sudo pacman -S virtualbox-guest-utils
```

Aktifkan service-nya:

```bash
sudo systemctl enable --now vboxservice.service
```

Lalu reboot:

```bash
reboot
```

Setelah itu, kamu bisa coba fitur seperti:
- Resize layar otomatis
- Clipboard sharing
- Mouse integration lebih baik

Di VirtualBox, aktifkan juga:

```text
Devices > Shared Clipboard > Bidirectional
Devices > Drag and Drop > Bidirectional
```

---

## 21. Troubleshooting Umum

### Masalah 1 — Setelah reboot, balik lagi ke installer

Penyebab:
ISO Arch masih terpasang.

Solusi:
Lepaskan ISO:

```text
Devices > Optical Drives > Remove disk from virtual drive
```

Lalu reboot lagi.

---

### Masalah 2 — Internet tidak jalan setelah install

Coba aktifkan NetworkManager:

```bash
sudo systemctl enable --now NetworkManager
```

Cek koneksi:

```bash
ping archlinux.org
```

---

### Masalah 3 — Tidak masuk desktop, hanya terminal

Kalau pakai KDE Plasma:

```bash
sudo systemctl enable --now sddm
```

Kalau pakai GNOME:

```bash
sudo systemctl enable --now gdm
```

Lalu reboot:

```bash
reboot
```

---

### Masalah 4 — Tidak bisa pakai `sudo`

Login sebagai root, lalu tambahkan user ke wheel:

```bash
usermod -aG wheel michael
```

Edit file sudoers:

```bash
EDITOR=nano visudo
```

Cari baris:

```text
# %wheel ALL=(ALL:ALL) ALL
```

Hapus tanda `#`, sehingga menjadi:

```text
%wheel ALL=(ALL:ALL) ALL
```

Simpan:
- Tekan `Ctrl + O`
- Tekan `Enter`
- Tekan `Ctrl + X`

Lalu reboot atau logout-login kembali.

---

## 22. Checklist Singkat

Gunakan checklist ini sebelum memilih **Install**:

- [ ] Internet sudah jalan
- [ ] Mirror sudah dipilih
- [ ] Disk sudah dipilih
- [ ] Filesystem `ext4`
- [ ] Bootloader `GRUB`
- [ ] Kernel `linux`
- [ ] Hostname sudah diisi
- [ ] User sudo sudah dibuat
- [ ] Profile Desktop sudah dipilih
- [ ] NetworkManager dipilih
- [ ] Timezone `Asia/Jakarta`
- [ ] NTP aktif
- [ ] Tidak ada pesan `Missing configurations`

---

## 23. Ringkasan Pilihan yang Direkomendasikan

| Menu | Pilihan |
|---|---|
| Language | English |
| Locales | en_US.UTF-8 |
| Mirror region | Indonesia / Singapore |
| Disk layout | Best-effort default |
| Filesystem | ext4 |
| Encryption | No |
| Swap | Enabled |
| Bootloader | GRUB |
| Kernel | linux |
| Hostname | arch-vm |
| Authentication | User account + sudo |
| Profile | Desktop |
| Desktop | KDE Plasma / GNOME |
| Graphics | All open-source |
| Audio | PipeWire |
| Network | NetworkManager |
| Timezone | Asia/Jakarta |
| NTP | Enabled |

---

## 24. Sumber Resmi

- Arch Linux Installation Guide: https://wiki.archlinux.org/title/Installation_guide
- Archinstall: https://wiki.archlinux.org/title/Archinstall
- General Recommendations setelah instalasi: https://wiki.archlinux.org/title/General_recommendations

---

Selesai.
