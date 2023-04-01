---
title: Kustomisasi Desktop Environment di Linux
author: Oystearl
pubDatetime: 2023-03-30T20:23:51Z
postSlug: kustomisasi-de-di-linux
featured: false
draft: false
tags:
  - sistem operasi
description: Pembahasan tentang Desktop Environment dan Kustomisasi Linux
---

Pada kali ini kita membahas soal Desktop Environment (DE) dan sedikit kustomisasi di Gnome.

Tapi sebelum membahas Desktop Environment, kita akan membahas beberapa komponent dari sebuah Desktop.

## Install App Gnome Tweaks dan Gnome Extensions

Ada yang app yang harus kita install agar proses kustomisasi kita di Ubuntu jadi lebih gampang, yaitu `gnome-tweaks` dan
`gnome-extensions`.

```bash
sudo apt update && sudo apt install gnome-tweaks gnome-shell-extension-manager -y
```

## Icon

_Icons_ harusnya kalian udah tahu, Sekumpulan gambar untuk mensimplekan sebuah navigasi di Desktop.

![fhs](/assets/so/de/1-icon.png)

### Cara ganti Icons

Kalian bisa mendownload macam-macam icons dari [pling.com](https://www.pling.com/browse?cat=132&ord=rating)

![pling](/assets/so/de/2-pling.png)

Kita akan mencoba memakai **Candy Icons**.

Klik Tab **Files (1)** seperti gambar dibawah.

![candy](/assets/so/de/3-candy.png)

Download lalu extrak menggunakan `Archive Manager` ke folder `~/.local/share/icons`

![local](/assets/so/de/4-local.png)

Jika sudah, tekan <svg version="1.1" xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink" x="0px" y="0px" viewBox="0 0 1000 1000" enable-background="new 0 0 1000 1000" xml:space="preserve">
<g><g transform="translate(0.000000,641.000000) scale(0.100000,-0.100000)"><path d="M7350.2,5949.8c-1380.9-205.8-2568.3-382.5-2637.4-391.7l-127.5-18.4V3582.7V1625.8h1356.3c745,0,1940,4.6,2657.4,10.8l1301,9.2v2340.9c0,1861.7-4.6,2339.4-18.4,2337.9C9870.8,6323.1,8731.1,6154.1,7350.2,5949.8z"/><path d="M2089.2,5172.6c-1072.2-159.8-1960-293.4-1970.7-298c-13.8-4.6-18.4-345.6-18.4-1634.4c0-895.5,4.6-1631.3,12.3-1634.4c6.2-3.1,907.8-3.1,2004.5,1.5l1992.3,7.7v1924.7v1926.2l-33.8-1.5C4055.3,5462.9,3162.9,5332.3,2089.2,5172.6z"/><path d="M100-475.5c0-914,6.1-1662,12.3-1662c7.7,0,900.1-124.4,1986.1-276.5c1084.5-152.1,1981.5-276.5,1992.3-276.5c13.8,0,18.4,396.3,18.4,1927.7V1165h-725c-399.4,0-1302.6,4.6-2004.5,10.8L100,1185V-475.5z"/><path d="M4585.3-802.7c0-1431.6,4.6-1964.6,16.9-1964.6c9.2,0,1201.2-165.9,2648.1-368.7c1445.4-202.8,2634.3-368.7,2638.9-368.7c6.1,0,10.8,1043,10.8,2317.9v2317.9l-694.3,9.2c-382.5,4.6-1579.1,12.3-2657.4,15.4l-1963.1,6.1V-802.7z"/></g></g>
</svg>, maka kalian akan masuk ke `Activies Menu`, ketik `Tweaks`. Di dalam aplikasi, klik `Appearance` > `Icons` lalu cari `Candy Icons`.

![local](/assets/so/de/5-tweaks.png)

## Window Manager

**Window Manager** sesuai namanya adalah software yang mengatur bagaimana window kalian terlihat dan berperilaku.
Biasanya berhubungan dengan `Display Server`.

![window](/assets/so/de/6-window.png)

Window Manager juga yang mengatur berapa size window terakhir kalian, apakah _maximised_ atau tidak, di tengah atau di ujung, dsb.

## Toolbar

**Toolbar** adalah _Graphical Control_ untuk mengatur _screen_ mana yang akan ditampilkan.

Contoh simplenya adalah **Taskbar** (Dock kalau di MacOS).

![window](/assets/so/de/7-taskbar.png)

## Dekstop Environment

Dekstop Environment (DE) adalah implementasi dari _desktop methapor_ yang dimana aplikasi dalam environment tersebut memiliki _look & feel_ yang sama.

Biasanya memiliki tampilan tetap mulai dari [icons](#icon), [window manager](#window-manager), [toolbar](#toolbar), beberapa aplikasi default, bahkan wallpaper sekalipun.

Di Linux, ada banyak sekali DE, seperti:

+ [Budgie](https://blog.buddiesofbudgie.org/)
+ [Cinnamon](https://github.com/linuxmint/Cinnamon)(Punya Linux Mint)
+ [Cutefish](https://cutefish-ubuntu.github.io/)
+ [Deepin](https://www.deepin.org/index/zh)
+ [Enlightment](https://www.enlightenment.org/)
+ [GNOME](https://www.gnome.org/)(Defaultnya Ubuntu)
+ [KDE Plasma](https://www.kde.org/plasma-desktop)(Defaultnya Kubuntu)
+ [LXDE](https://www.lxde.org/)
+ [MATE](https://mate-desktop.org/)
+ [Sugar](https://sugarlabs.org/)
+ [UKUI](https://www.ukui.org/)
+ [XFCE](https://xfce.org/)

Tapi kita cuman akan membahas **GNOME** dan **KDE Plasma**.

## Kustomisasi Ubuntu->GNOME

Karena Ubuntu memakai GNOME sebagai DE-nya, maka kita akan coba mengkustomisasi GNOME.

![about](/assets/so/de/8-about.png)

### Desktop Cube

Buka `Activies Menu`, ketik [Extension Manager](#install-app-gnome-tweaks-dan-gnome-extensions) lalu buka.

Jika sudah `Browse` extension `Desktop Cube` di search barnya lalu install.

![cube](/assets/so/de/9-cube.png)

Maka hasilnya akan terlihat seperti ini.

<video src="/assets/so/de/cube.webm" loop mute autoplay ></video>
(Disitu saya pakai Desktop saya sendiri, karena Ubuntu saya itu cuman VM dan gak bisa hardware acceleration).

### Burn My Windows

Cari di Extensions Manager `Burn My Windows` lalu install.

![burn](/assets/so/de/10-burn.png)

Maka hasilnya akan seperti ini.

<video src="/assets/so/de/effect.webm" loop mute autoplay ></video>

## Install Desktop Environment Lain (KDE Plasma).

GNOME merupakan desktop yang cukup customizable, walaupun masih tergantung dengan extensions dari luar.

Bagaimana jika kustomisasi itu default disediakan oleh DE-nya? Di sinilah KDE Plasma bersinar 🤩.

Kita akan coba install KDE Plasma di Ubuntu. Jalankan perintah di bawah untuk menginstall package-nya.

Di Ubuntu KDE memiliki beberapa package:
+ KDE Full, lengkap sekitar 1GB `kde-full`
+ KDE Standard, punya beberapa app default KDE, 273MB, `kde-standard`
+ KDE Plasma Desktop, minimal, 173MB, `kde-plasma-desktop`

Kita akan coba install yang Standard.

```bash
sudo apt install kde-standard
```

Jika sudah maka akan muncul pop-up seperti ini.

![prompt](/assets/so/de/11-prompt.png)

Tekan **Enter**/**Ok** saja, disitu kalian hanya diminta untuk mimilih dari dua `Display Manager`.

![sddm](/assets/so/de/12-sddm.png)

Pilih `sddm` lalu tekan Enter.

Tunggu sampai proses nya selesai. Jika sudah reboot/restart Ubuntu kalian.

Maka kalian akan masuk ke Halaman Login yang baru!

![login](/assets/so/de/13-login.png)

Login menggunakan password kalian, tunggu beberapa saat dan...

![kde](/assets/so/de/14-kde.png)

Tadaa 🎉🎉🎉

## Akhir Kata...

Mungkin itu aja yang bisa saya sampaikan, _see ya_.


