---
title: Lebih Tau Soal Linux
author: Oystearl
pubDatetime: 2023-03-22T10:23:51Z
postSlug: tips-trick-terminal-linux
featured: false
draft: false
tags:
  - sistem operasi
description: "Penjelasan tentang Linux"
---

Pada kali ini kita akan mencoba membahas beberapa hal tambahan di Linux.

## Struktur Direktori

Struktur direktori Linux menggunakan [Filesystem Hierarchy Standard](https://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard).

![fhs](/assets/so/more-linux/1-fhs.png)

Di paling atas ada `/` (root), yang merupakan starting point dari semua directory.

Yap, `/` adalah folder dan disebut root.

Jalankan `cd /` lalu `ls` untuk melihat semua folder seperti di gambar.

+ `bin` (binaries) = folder yang berisi binaries/executeable. Biasanya merupakan symlink/shortcut dari `/usr/bin`
+ `boot` = folder yang berisi file untuk booting, linux kernel ada di folder ini.
+ `dev` (devices) = folder yang berisi device dari luar, seperti flashdisk dsb.
+ `etc` (Ec TeCera / Editable Text Configuration) = folder yang berisi file config, yang kebanyakan cuman file txt.
+ `home` = folder untuk username kalian dan bisa multiuser
+ `lib` (libraries) = folder yang berisi library/dependencies untuk aplikasi/binaries. Biasanya merupakan symlink/shortcut dari `/usr/lib`.
+ `opt` (optional) = folder untuk install beberapa aplikasi optional, XAMPP dan VSCode biasanya terinstall di folder ini.
+ `root` = folder **home** untuk root user.
+ `run` = folder untuk run-time variable, buat ngecek siapa user yang login dan daemon yang berjalan.
+ `sbin` = folder bin tapi cuman untuk superuser/root user
+ `tmp` = folder untuk temporary files
+ `usr` = folder untuk share binaries dan library ke semua user. Biasanya cuman read-only.
+ `var` = folder untuk variable, untuk logs dan cache.

Jika ingin tahu sebuah aplikasi ada di folder mana, cukup jalankan ``which namaApp``.

```bash
which apt
```

![fhs](/assets/so/more-linux/2-which.png)

## Files Permissions

Files Permissions adalah cara linux mengatur bagaimana sebuah file di _read_, _write_, atau _execute_.

Fyi, [Everything is a file](https://en.wikipedia.org/wiki/Everything_is_a_file) dalam Linux (Mac juga).

Untuk melihat file permissions, cukup jalankan `ls -lh` (list) untuk menampilkan isi dari sebuah direktori.

![ls](/assets/so/more-linux/3-ls.png)

Oke, kita akan ambil contoh file `test1.txt` dan folder `Templates` sebagai contoh.

![draw](/assets/so/more-linux/4-draw.png)

Bisa kita lihat folder `Templates` dan file `test1.txt` memiliki permissions yang berbeda. 

![permis](/assets/so/more-linux/5-permis.png)

Mari kita jelaskan satu persatu.

Bagian `type` adalah tipe dari 'file'-nya. 

+ `d` = direktori
+ `-` = file biasa
+ `l` = symlink/shortcut

Permission dalam Linux ada 3, yaitu:

+ `r` = read
+ `w` = write
+ `x` = execute

Dari 3 permission tadi, bisa kita assign ke beberapa tempat, seperti **user** kita sendiri, **group** user, dan **user lain**.

Jika dilihat dari gambar diatas, pada folder `Templates` maka dapat dideskripsikan: 

+ User dapat  melakukan `read`, `write`, `execute`
+ Group user dapat melakukan `read` dan `execute`
+ User lain dapat melakukan `read` dan `execute`

Tapi apa itu Group User?

Group user adalah sebuah group yang dapat berisi beberapa user dan memiliki permissions tertentu.

Kalian bisa cek dengan `groups` atau `groups username` untuk mengecek username kalian ada di grup mana.

![groups](/assets/so/more-linux/6-groups.png)

Jika kalian bertanya "Kenapa nama username dan nama groups nya sama" itu karena Ubuntu otomatis membuat sebuah group dengan nama username kalian.

Sebagai contoh ini adalah tampilan `ls` di Arch Linux.

![groups](/assets/so/more-linux/7-arch.png)

### Cara merubah permissions

Ada dua cara dalam mengubah permissions:

1. Memakai symbol (Cara gampang).
2. Memakai _Octal notation_.

#### Dengan Symbol

Untuk mengubah dengan symbol cukup jalankan perintah dibawah.

```bash
chmod u=rwx,g=rwx,o=rwx namaFile
```

Oke, kita akan mencoba mengubah file `test1.txt` menjadi `rw---x-w-`.

Berarti perintahnya akan menjadi seperti ini.

```bash
chmod u=rw,g=x,o=w test1.txt
```
![chmod](/assets/so/more-linux/8-chmod.png)

#### Dengan Octal Notation

Sebelum itu kita harus mengetahui dulu setiap jika setiap permission memiliki angka.

+ `r`ead = 4 
+ `w`rite = 2 
+ `x`ecute = 1 
+ `-` = 0

Jika kita ingin mengubah sebuah permission menjadi `write` dan `execute` saja, berarti valuenya adalah **3**.

```python
permission = w+x
permission = 2+1
permission = 3
```

Sebagai contoh, kita akan mengubah permission folder `Templates` menjadi `-wx-rw--w-`.

Berarti perintahnya akan terlihat seperti ini.

```bash
chmod 362 Templates
```

![octal](/assets/so/more-linux/9-octal.png)

Permission default dari sebuah folder biasanya adalah `755`.

Untuk mengetahui lebih banyak soal chmod, kalian bisa ketik `man chmod` atau yang lebih user-friendly `tldr chmod`,
meskipun tidak selengkap `man`ual.

![tldr](/assets/so/more-linux/10-tldr.png)

## Tambahan Command

### Cat dan Lolcat

Untuk menampilkan isi dari file, jalankan `cat namaFile` yang merupakan singkatan dari con`cat`enate.

![cat](/assets/so/more-linux/11-cat.png)

Tapi ada yang lebih baik, yaitu `lolcat`. Install lalu jalankan dengan perintah di bawah.

```bash
sudo apt install lolcat -y
lolcat main.py
```

![lolcat](/assets/so/more-linux/12-lolcat.png)

It's became rainbow 🌈 

### Kereta (SL)

Install dulu packagenya dengan `apt`.

```bash
sudo apt install sl -y
```

Lalu jalankan dengan perintah `sl`.

<video src="/assets/so/more-linux/sl.webm" loop mute autoplay ></video>

Kalian juga bisa menggabungkan dua perintah dengan `|` (pipe). Coba jalankan `sl | lolcat` dan lihat hasilnya.

<video src="/assets/so/more-linux/slolcat.webm" loop mute autoplay ></video>

It's a Rainbow Train 🚄 🌈 

### Cmatrix 

Jalankan perintah dibawah untuk menginstallnya.

```bash
sudo apt install cmatrix -y
```

Lalu jalankan `cmatrix` untuk melihat hasilnya.

![cmatrix](/assets/so/more-linux/13-cmatrix.png)

Sekarang kalian resmi hacker 👨‍💻

### Asciiquarium

Install menggunakan command dibawah.

```bash
sudo add-apt-repository ppa:ytvwld/asciiquarium
sudo apt-get update && sudo apt-get install asciiquarium -y
```

Lalu jalankan perintah `asciiquarium`. Restart terminal jika command tidak muncul.

![asciquarium](/assets/so/more-linux/14-asciiquarium.png)

## Akhir Kata...

Mungkin itu dulu yang bisa saya tulis, _see ya_ ( ╹▽╹ )