---
title: Percantik Terminal dengan ZSH + Powerlevel10k
author: Oystearl
pubDatetime: 2023-03-20T03:42:51Z
postSlug: percantik-terminal-dengan-zsh-powerlevel10k
featured: false
draft: false
tags:
  - zsh
  - terminal
description: "Percantik terminal kalian degan ZSH dan Powerlevel10k"
---

Di Linux kalian pasti bakal sering memakai terminal. Tapi kebanyakan orang takut dengan terminal karena _its just a blank screen with blip_.

Tapi bagaimana jika terminal kalian lebih dari itu? Tidak terlihat menakutkan dan juga menyenangkan saat dipakai.

Di sinilah kita akan memakai ZSH.

## ZSH

ZSH (Z SHell) adalah salah satu dari banyak Shell di Sistem Operasi Unix-Based (Mac dan Linux).

ZSH merupakan default shell di MacOS. Sedangkan di Linux default-nya adalah Bash (Bourne Againt Shell).

Kelebihan ZSH dari pada Bash antara lain:

- Punya Syntax Highlighting (mirip syntax hightling di VS Code gitu)
- Punya Auto History (Cukup ketik beberapa huruf, ZSH akan auto-suggest perintah)
- Arrow Navigasi (Gak perlu pakai tab, bisa pakai arrow)
- Punya banyak ekstensi

Oke mungkin langsung aja.

## Intallasi

### Update Repo

Pertama, kita akan update repo Ubuntu dulu

```bash
sudo apt update
```

![Update](/assets/so/1-update.png)

Kenapa harus update dulu? Bayangkan kalian ditanya teman kalian:

**"Tau Dilan Cepmek gak?"**

**"Gak tau"**

**"Ohh, kurang up-to-date nih"**

Jadi fungsi update ditujukan agar si Ubuntu tau kalau aplikasi yang kalian ingin install ada di repo Ubuntu.

Jika kalian bertanya apa itu APT (Advance Packaging Tools), Apt adalah package manager, mirip Play Store/App Store di Android/iOS.

Ibaratnya, kalau Play Store bisa di jalankan terminal, mungkin gini `sudo play-store install whatsapp`.

Dan juga, `sudo` itu mirip `Run as Administrator` di Windows.

### Install Git, ZSH dan, Curl

Jalankan perintah di bawah untuk menginstall Git, ZSH, Curl, dan font powerline.

```bash
sudo apt install git zsh curl -y
```

![install](/assets/so/2-install.png)

- `git` supaya kita bisa clone repo,
- `zsh` itu judul dari artikel ini,
- `curl` supaya kita bisa download file dari terminal aja,
- `-y` supaya langsung Yes ke semua prompt (Y/n).

## Buat file .zshrc dan folder fonts

Selanjutnya kita akan membuat file .zshrc

```bash
touch ~/.zshrc
```

- `touch` adalah perintah untuk membuat file,
- `~/` adalah lokasi nya. Tanda `~` merupakan penulisan simple dari `/home/username`
- `.zshrc` adalah nama filenya. Diberikan tanda titik didepan agar filenya hidden

Selanjutnya kita akan membuat folder **fonts**.

```bash
mkdir ~/.local/share/fonts
```

Kita buat folder untuk menyimpan font yang akan kita install nanti.

### Install Font

Jalankan perintah-perintah dibawah untuk menginstall Font MesloGS NF.

```bash
# Download FontManager
sudo bash -c "$(curl -LSs https://github.com/dfmgr/installer/raw/main/install.sh)"

# Download Font Meslo
bash -c "$(curl -LSs https://github.com/fontmgr/MesloLGSNF/raw/main/install.sh)"

# Install Font Meslo
sudo fontmgr install MesloLGSNF
```

![font](/assets/so/3-font.png)

Jika sudah klik <svg xmlns="http://www.w3.org/2000/svg" class="icon icon-tabler icon-tabler-menu-2" width="24" height="24" viewBox="0 0 24 24" stroke-width="2" stroke="currentColor" fill="none" stroke-linecap="round" stroke-linejoin="round">
<path stroke="none" d="M0 0h24v24H0z" fill="none"></path>
<path d="M4 6l16 0"></path>
<path d="M4 12l16 0"></path>
<path d="M4 18l16 0"></path>
</svg> di atas, lalu pilih `Prefereces` > `Unnamed`.

Centang bagian `Custom Fonts` lalu pilih Font `MesloLGS Nerd Font`. Klik Select lalu kembali ke Terminal.

![meslo](/assets/so/4-meslo.png)

### Install Semua Keperluan ZSH

Pertama, kita akan menginstall Oh-My-ZSH

```
sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
```

![ohmyzsh](/assets/so/5-ohmyzsh.png)

`OhMyZSH` adalah package manager untuk ZSH. Wait, ada package manager lagi?

Yupp, dunia ini penuh dengan package manager, jadi biasakanlah 😄

### Install Powerlevel10k

**Powerlevel10k** sebenarnya hanyalah salah satu dari tema ZSH.

Jalankan perintah dibawah untuk menginstallnya.

```bash
git clone --depth=1 https://github.com/romkatv/powerlevel10k.git ${ZSH_CUSTOM:-$HOME/.oh-my-zsh/custom}/themes/powerlevel10k
```

Jika sudah buka file `.zshrc` menggunakan `gedit`. (Gedit = Notepad)

```bash
gedit ~/.zshrc
```

Lalu ganti tulisan di variabel `ZSH_THEME` menjadi `"powerlevel10k/powerlevel10k"`

```bash
ZSH_THEME="powerlevel10k/powerlevel10k"
```

![zsh](/assets/so/6-zsh.png)

Jalankan perintah dibawah untuk melihat hasilnya.

```bash
source ~/.zshrc
```

![p10k](/assets/so/7-p10k.png)

Jika sudah seperti gambar diatas, tinggal kalian ikuti aja pilihannya.

Punya saya terlihat seperti gambar dibawah.

![done](/assets/so/8-done.png)

### Change Shell

Tapi, jika kalian keluar, maka settingan kalian tadi tidak akan muncul.

Itu dikarenakan kita belum mengganti shell default kita.

Jika ingin mengecek default shell, cukup jalankan `echo $SHELL`

Untuk mengganti shell, jalankan perintah dibawah.

```bash
chsh --shell /usr/bin/zsh
```

Setelah itu Logout dari Ubuntu, lalu masuk lagi, harusnya terminal kalian sudah terseting lagi 🎉.

### Tambah Plugins

Kita akan menambah plugins `auto-suggest` dan `syntax-hightlighing`.

Jalankan perintah dibawah untuk menginstall `zsh-autosuggestions` dan `zsh-syntax-highlighting`.

```bash
git clone https://github.com/zsh-users/zsh-autosuggestions.git $ZSH_CUSTOM/plugins/zsh-autosuggestions
git clone https://github.com/zsh-users/zsh-syntax-highlighting.git $ZSH_CUSTOM/plugins/zsh-syntax-highlighting
```

Jika sudah, buka lagi `.zshrc` dengan `gedit`

Lalu, ubah kalimat `plugins=(git)` (atau dikomentar) dengan kalimat dibawah ini:

```bash
# plugins=(git)
plugins=(git zsh-autosuggestions zsh-syntax-highlighting)
```

![done](/assets/so/9-plugin.png)

### Akhir Kata...

Mungkin itu dulu yang bisa saya tulis, _see ya_ ( ╹▽╹ )