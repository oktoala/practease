---
title: Aplikasi Windows di Linux dan Boot Screen
author: Oystearl
pubDatetime: 2023-03-22T10:23:51Z
postSlug: install-app-windows-di-linux
featured: false
draft: false
tags:
  - sistem operasi
description: Belajar soal Wine dan Plymouth
---

Kali ini kita akan belajar beberapa hal lumayan cukup advanced, tapi gampang 😀.

Kita akan coba menginstall aplikasi Windows di Linux menggunakan [Wine](https://www.winehq.org/)

## Wine dan Install

WINE adalah sebuah _compability layer_ yang menstranlate semua Windows API menjadi POSIX API.

Jadi jika aplikasi Windows butuh audio, dia akan memakai audio driver milik Linux yang sudah ditranslate.

Cara kerjanya tidak seperti Emulator/Virtual Machine yang menjalankan satu OS Full. Bahkan **WINE** adalah akronim dari **_Wine Is Not an Emulator_**.

Wine menaruh aplikasi yang diinstallnya ke dalam sebuah container yang disebut `WineBottle`

[gambar]

Bisa kita lihat seperti gambar di atas, terdapat beberapa folder yang kalian mungkin familiar di Windows.

Kalian bisa menginstall banyak aplikasi dalam satu `WineBottle` tapi direkomendasikan untuk menginstall aplikasi dalam `Bottle` yang terpisah.

Karena tiap aplikasi membutuhkan beberapa .dll yang berbeda dari aplikasi yang lain.

Jadi kalian tidak perlu takut aplikasi kalian break saat menginstall aplikasi yang lain jika mereka terdapat di dalam `Bottle` yang terpisah.

Install Wine dengan perintah di bawah.

```bash
sudo apt update && sudo apt install wine -y
```

## Install Aplikasi Windows

Kita akan mencoba menginstall game [Deltarune](https://tobyfox.itch.io/deltarune)

[gambar]

Ekstrak .zip, saya mengekstranya di folder `Download`.

Buka terminal di folder `Download`.

Syntax umum untuk menjalankan seperti gambar dibawah.

+ WINEARCH -> Arsitektur dari Bottle kalian (32bit atau 64bit). Default ngikutin PC kalian.
+ WINEPREFIX -> Lokasi Bottlenya
+ wine -> ya wine
+ app.exe -> nama aplikasi windows yang mau diinstall

Saya akan coba menginstallnya di dalam folder/bottle `~/Games/Deltarune`.

```bash
WINEARCH=win64 WINEPREFIX=~/Games/Deltarune wine 
```
