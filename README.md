# FluxOS ⚡

[![License: Proprietary](https://img.shields.io/badge/License-All%20Rights%20Reserved-red.svg)]()
[![Version](https://img.shields.io/badge/version-5.0.0--alpha-blue)](https://github.com/bencepalko383-lgtm/Flux-OS)
[![Base](https://img.shields.io/badge/Based%20on-Arch%20Linux-1793D1)](https://archlinux.org/)
[![AUR](https://img.shields.io/badge/AUR-Enabled-green)]()

> *"Nem vagyok teológus, de az Arch alapú disztró a legjobb disztró."*

A **FluxOS** egy **Arch Linux alapú**, modern és minimalista disztribúció. Nem Ubuntu, nem Fedora, és főleg nem Debian. Natív `pacman`, AUR támogatás, és egyedi build pipeline konténerek nélkül. Ha nem tudod mi az az Arch, akkor ez a disztró nem neked való — de azért nyugodtan próbáld ki, tanulni fogsz belőle.

---

## 🚀 Miért FluxOS?

### 🎭 Intelligens Profil Rendszer
Telepítéskor vagy utólag egy parancssal váltasz profil között:

| Profil | Leírás |
|--------|--------|
| 🎮 **Gaming** | CachyOS/Zen kernel, előre konfigurált Wine/Proton, Steam, minimális háttérfolyamatok |
| 💼 **Office** | Zavaró tényezők nélküli felület, LibreOffice, produktivitás eszközök |
| 🖥️ **Server** | Grafikus felület nélküli (vagy minimális GUI), biztonságra és stabilitásra optimalizálva |

### ⚡ Dinamikus Energia Módok
A `flux-power` démon azonnal vált az élethelyzetednek megfelelően:

| Mód | Leírás |
|-----|--------|
| 🔋 **Eco** | Maximális akkumulátor-üzemidő, visszafogott órajelek |
| ⚖️ **Balanced** | Intelligens erőforrás-elosztás |
| 🔥 **Performance** | Nyers erő limitációk nélkül — játék, render, compile |

### 📦 Előre telepített szoftverek

- 🌐 **Brave** — Alapértelmezett böngésző, adatvédelem-first, reklámblokkolóval
- 🎥 **OBS Studio** — Stream és felvétel, optimalizált kódolókkal
- 🏄 **In-Installer Surf Game** — Unalmas a telepítés? Játssz retro szörfözést a telepítőben
- 🔒 **Egyedi Lockscreen** — Minimalista, animált, időjárás-előrejelzéssel
- 🔄 **GitHub alapú frissítő** — `flux-update` közvetlenül a repo-ból húzza a legfrissebb komponenseket

---

## 💻 Rendszerkövetelmények

| Erőforrás | Minimum | Ajánlott |
|-----------|---------|----------|
| **CPU** | x86_64, 2 mag, 1.5 GHz | 4+ mag, Intel i5 / Ryzen 5 |
| **RAM** | 2 GB (Server/Office) | 8+ GB (Gaming / AUR compile) |
| **Tárhely** | 20 GB szabad hely | 50+ GB SSD |
| **GPU** | Integrált | GTX 1050 / RX 560 vagy jobb |
| **Internet** | 10 Mbps | 50+ Mbps (AUR build-hez) |

> **Fontos:** A build folyamat AUR csomagokat is fordít, ami több GB RAM-ot és swap-et igényelhet. 4 GB alatt ne próbálkozz AUR kernel builddel.

---

## 💿 Telepítés — Step by Step

### 0. Mi az a TTY?

A **TTY** (TeleTYpewriter) egy szöveges felület, ahol parancsokat írhatsz be. Amikor belépsz a FluxOS ISO-ba, először egy **fekete képernyőt** látsz fehér szöveggel — ez a TTY. Itt nincs egér, nincs ablak, csak te és a billentyűzet. Ha grafikus felületet akarsz, azt később telepíteni kell, vagy az `archinstall` megteszi helyetted.

> **Fontos:** Ha elrontasz valamit, nyomd meg a `Ctrl + C` billentyűket — ez megszakítja az aktuális parancsot.

> 💬 *"Miért nem szeretnek a programozók a természetben járni? Mert túl sok a bug."*

---

### 1. ISO letöltés és bootolás

1. Töltsd le a legfrissebb `fluxos-<dátum>-<kernel>-x86_64.iso` fájlt a [Releases](https://github.com/bencepalko383-lgtm/Flux-OS/releases) alól.
2. Írd ki egy pendrive-ra Ventoy-val, Rufus-sal, vagy Linuxon `dd`-vel:
   ```bash
   sudo dd if=fluxos-*.iso of=/dev/sdX bs=4M status=progress oflag=sync
   ```
3. Indítsd újra a gépet, lépj be a BIOS/UEFI-be (általában `F2`, `F10`, `F12` vagy `Del`), és válaszd a pendrive-ot elsődleges boot eszközként.
4. A FluxOS boot menüjében válaszd az első opciót (x86_64).

> ⚠️ **FIGYELEM:** A telepítés törli a célmeghajtót. Backup előtte.

> 💬 *"Miért nem megy a számítógép a terápiára? Mert mindig kikapcsolja az érzéseit."*

---

### 2. Belépés után — alapvető parancsok

Ha minden jól ment, egy fekete képernyőn fehér szöveget látsz. Ez a **TTY1** (az első terminál). A prompt így néz ki:

```
[FluxOS] root@fluxos-live:~#
```

Itt vagy. Most jön a lényeg.

> 💬 *"Miért hívják a terminált terminálnak? Mert itt minden parancs végleges."*

---

### 3. Internetkapcsolat beállítása

#### Ha kábeles (Ethernet) kapcsolatod van:

A legtöbb esetben automatikusan működik. Ellenőrizd:

```bash
ping -c 3 archlinux.org
```

Ha `3 packets transmitted, 3 received` jön vissza, van neted. Ugorhatsz a 4. lépésre.

#### Ha WiFi-re csatlakozol:

Használd az `iwctl` eszközt. Ez egy interaktív WiFi menedzser.

```bash
# 1. Belépés az iwctl interaktív módba
iwctl

# 2. Listázd az elérhető WiFi eszközöket
[iwd]# device list

# Ezt fogod látni (példa):
# Name   Address            Powered  Adapter   Mode
# wlan0  AB:CD:EF:12:34:56  on       phy0      station
#
# A "Name" oszlopban lévő név kell (pl. wlan0)

# 3. Keress hálózatokat
[iwd]# station wlan0 scan
[iwd]# station wlan0 get-networks

# 4. Csatlakozás a hálózathoz (cseréld le a NEVE-t a sajátodra)
[iwd]# station wlan0 connect "NEVE"

# Jelszó bekérésnél írd be a WiFi jelszavadat és nyomj Entert

# 5. Kilépés az iwctl-ből
[iwd]# exit
```

Ellenőrizd, hogy van-e net:

```bash
ping -c 3 archlinux.org
```

Ha nem megy, próbáld újra. Ha a WiFi chip-ed ritka, lehet, hogy firmware-t kell tölteni — ezt a FluxOS telepítője nem tudja megoldani, használj kábelt.

> 💬 *"Miért nem házasodott meg a router? Mert minden kapcsolata felhő alapú."*

---

### 4. Lemezpartíciók előkészítése (opcionális, de ajánlott)

Az `archinstall` tudja ezt is, de ha manuálisan akarod:

```bash
# Listázd a lemezeket
lsblk

# Ezt fogod látni:
# NAME   MAJ:MIN RM   SIZE RO TYPE MOUNTPOINTS
# sda      8:0    0 238.5G  0 disk
# ├─sda1   8:1    0   512M  0 part
# └─sda2   8:2    0   238G  0 part
# sdb      8:16   1  14.9G  0 disk   ← ez a pendrive

# Particionálás (példa: cfdisk-kel, egyszerű TUI)
cfdisk /dev/sda
```

A `cfdisk` egy szöveges felületű particionáló. A nyilakkal navigálsz, Enterrel választasz.

**Javasolt partíciós séma (UEFI):**

| Partíció | Méret | Típus | Cél |
|----------|-------|-------|-----|
| `/dev/sda1` | 512 MB | EFI System | Boot fájlok |
| `/dev/sda2` | 30-50 GB | Linux filesystem | Rendszer (/) |
| `/dev/sda3` | Maradék | Linux filesystem | Home (/home) |
| `/dev/sda4` | 8-16 GB | Linux swap | Swap |

Ha nem akarsz bajlódni vele, hagyd az `archinstall`-ra.

> 💬 *"Miért nem eszik a merevlemez soha? Mert tele van bite-kal."*

---

### 5. Telepítés az `archinstall`-sal

Az `archinstall` egy szöveges telepítő, ami végigvezet a folyamaton. Indítsd el:

```bash
archinstall
```

**A menüpontok sorban:**

1. **Install language** — Válaszd ki a nyelvet (pl. `hu` vagy `en`).
2. **Mirrors** — Válaszd az országodat (pl. `Hungary`), vagy hagyd `Worldwide`-on.
3. **Locales** — `en_US.UTF-8` ajánlott, vagy `hu_HU.UTF-8` ha magyarul akarod.
4. **Disk configuration** —
   - `Best-effort default partition layout` — automatikus particionálás
   - `Manual Partitioning` — ha te csináltad a partíciókat
   - Válaszd ki a céllemezt (pl. `/dev/sda`), és mondd meg, hogy UEFI vagy BIOS mód.
5. **Disk encryption** — Ha akarsz titkosítást, válaszd a `Luks`-ot, és adj meg egy jelszót. Ha nem, `No`.
6. **Bootloader** — Válaszd a `systemd-boot`-ot (UEFI) vagy `grub`-ot (BIOS).
7. **Swap** — `True` ajánlott, ha kevés a RAM.
8. **Hostname** — Add meg a gép nevét (pl. `fluxos-pc`).
9. **Root password** — Root jelszó. **Jegyezd meg.**
10. **User account** —
    - `Add a user`: felhasználónév (pl. `bence`)
    - `Password for user`: jelszó
    - `Confirm password`: jelszó mégegyszer
    - `Superuser permission`: `True` (sudo jog)
11. **Profile** — Itt válaszd ki a FluxOS profilt:
    - `FluxOS Gaming`
    - `FluxOS Office`
    - `FluxOS Server`
    - Vagy `Minimal` ha csak az alaprendszert akarod.
12. **Audio** — Válaszd a `Pipewire`-t (modern, ajánlott).
13. **Kernels** — Válaszd ki a kernelt:
    - `linux` (stock)
    - `linux-zen` (interaktív)
    - `linux-cachyos` (optimalizált)
    - `linux-lts` (stabil)
14. **Additional packages** — Ha akarsz extra csomagokat, írd be szóközzel elválasztva (pl. `neofetch htop vim`).
15. **Network configuration** — Válaszd a `NetworkManager`-t.
16. **Timezone** — Válaszd ki az időzónád (pl. `Europe/Budapest`).
17. **Optional repositories** — Ha kell, pipáld be a `multilib`-et (32-bites játékokhoz).

Ha minden kész, válaszd a `Install` opciót. A telepítő letölti és telepíti a csomagokat — ez 5-20 perc attól függően, hogy milyen neted van.

**Mi történik telepítés közben?**
- A képernyő alsó részén egy progress bar fut.
- Ha unatkozol, nyomd meg az `F2`-t — elindul a szörfös játék.
- Ha hiba van, piros szöveg jelenik meg. Fotózd le, és jelezd Discordon.

> 💬 *"Miért nem szereti a Linux a liftet? Mert mindig a root szinten akar megállni."*

---

### 6. Telepítés után

Ha kész, két opciót látsz:

- `Reboot` — Indítsd újra a gépet.
- `Exit` — Kilépés a telepítőből.

Válaszd a `Reboot`-ot. Húzd ki a pendrive-ot amikor a képernyő elsötétül.

> 💬 *"Miért nem megy a számítógép nyaralni? Mert fél a vírustól."*

---

### 7. Első boot

Ha minden jól ment, a rendszer betölti a GRUB-ot vagy a systemd-boot-ot, és látsz egy menüt. Válaszd a `FluxOS` opciót.

Bejelentkezés:
- **Felhasználónév:** amit az `archinstall`-nál megadtál
- **Jelszó:** amit megadtál

Ha grafikus felületet telepítettél (Gaming/Office profil), bejön az asztali környezet. Ha Server profilt választottál, maradsz a TTY-n.

> 💬 *"Miért visel a Linux kernel sapkát? Mert fél a hőmérséklet-csúcsoktól."*

---

### 8. Első lépések bejelentkezés után

```bash
# Rendszerfrissítés (ezt rendszeresen csináld)
sudo pacman -Syu

# FluxOS specifikus frissítés
flux-update

# Profil váltás (ha meggondoltad magad)
flux-profile switch gaming

# Energia mód váltás
flux-power balanced

# Rendszerinfo
flux-info
```

> 💬 *"Miért nem lop a hacker soha semmit? Mert mindig csak a rendszert törli."*

---

## 🖥️ Hardver Kompatibilitás

### Támogatott platformok

| Platform | Státusz | Megjegyzés |
|----------|---------|------------|
| **x86_64 (Intel/AMD)** | ✅ Teljes támogatás | Minden funkció elérhető |
| **Intel Arc GPU** | ✅ Támogatott | Mesa + Intel Xe driverek |
| **NVIDIA (proprietáris)** | ✅ Támogatott | `nvidia` csomag telepítve Gaming profilban |
| **NVIDIA (nouveau)** | ⚠️ Korlátozott | Csak alap 2D, 3D gyorsítás nélkül |
| **AMD GPU** | ✅ Teljes támogatás | Mesa RADV/AMDGPU |
| **Hybrid graphics** | ✅ Támogatott | PRIME offload konfigurálva |
| **Laptopok** | ✅ Támogatott | TLP + auto-cpufreq telepítve |
| **VM (QEMU/KVM)** | ✅ Támogatott | VirtIO driverek elérhetők |
| **VM (VirtualBox)** | ⚠️ Korlátozott | Guest additions manuálisan telepíthető |
| **Apple Silicon** | ❌ Nem támogatott | Asahi Linux nem integrált |

### WiFi / Bluetooth chipek

| Chip | Státusz |
|------|---------|
| Intel AX200/AX210 | ✅ |
| Intel 9560/9260 | ✅ |
| Broadcom BCM43xx | ✅ (wl driver) |
| Realtek RTL88x2BU | ✅ (DKMS) |
| Realtek RTL8821CE | ✅ (DKMS) |
| Mediatek MT7921 | ✅ |
| Qualcomm Atheros | ✅ |

---

## 🔧 Hibaelhárítás

### Boot után fekete képernyő

```bash
# Nomodeset kernel paraméterrel bootolj (GRUB-ban 'e' szerkesztés)
nomodeset

# Vagy a megfelelő GPU drivert telepítsd:
sudo pacman -S xf86-video-amdgpu   # AMD
sudo pacman -S xf86-video-intel    # Intel
sudo pacman -S nvidia              # NVIDIA
```

> 💬 *"Miért nem lát a monitor semmit? Mert a driver elment pihenni."*

### WiFi nem működik telepítés után

```bash
# Ellenőrizd a chipet
lspci -k | grep -A 3 -i network

# Telepítsd a megfelelő firmware-t:
sudo pacman -S linux-firmware
sudo pacman -S broadcom-wl-dkms   # Broadcom
```

> 💬 *"Miért nem megy a WiFi? Mert a routernek is rossz napja van."*

### AUR csomag build sikertelen

```bash
# Swap növelése (ha kevés a RAM)
sudo fallocate -l 4G /swapfile
sudo chmod 600 /swapfile
sudo mkswap /swapfile
sudo swapon /swapfile

# Majd újrapróbálod a telepítést
```

> 💬 *"Miért nem tud a számítógép főzni? Mert mindig elfogy a memóriája."*

### Hang nem működik

```bash
# PipeWire ellenőrzés
systemctl --user status pipewire pipewire-pulse

# Újraindítás
systemctl --user restart pipewire pipewire-pulse
```

> 💬 *"Miért nem szól a hangszóró? Mert a PipeWire elszívta a levegőt."*

---

## 🔄 Frissítési Politika

| Típus | Gyakoriság | Leírás |
|-------|-----------|--------|
| **Biztonsági** | Azonnal | CVE javítások, kernel patch-ek |
| **Csomag** | Heti | Arch repo sync + AUR frissítések |
| **ISO** | Havonta | Új ISO image a legfrissebb csomagokkal |
| **Kernel** | Opcionális | Custom kernel váltás telepítés után |

> A FluxOS a rolling release modellt követi. Nincs "verzióváltás", folyamatosan frissül.

> 💬 *"Miért nem öregszik a számítógép? Mert mindig frissít."*

---

## 🔒 Forráskód és Visszafejtés

**A FluxOS forráskódja zárt.** Nem open source. Nem GPL. Nem MIT.

### Visszafejtés TILOS

A szoftver visszafejtése, decompilálása, disassemblálása, vagy bármilyen módon történő forráskód-visszaállítása **szigorúan tilos**.

**Magyar jogi háttér:**
- A **1999. évi LXXVI. törvény** (Szerzői jog) 36. § (2) bekezdése értelmében a szerzői jogosult kizárólagos joga a számítógépi program visszafejtésének (decompilálásának) megtiltása.
- A **2012. évi C. törvény** (Btk.) 300. §-a szerint a számítógépes csalás és a jogosulatlan adathozzáférés bűncselekménynek minősülhet.
- A szoftver licenszszerződésének megsértése polgári jogi következményeket (kártérítés, szerződésszegés) és büntetőjogi eljárást vonhat maga után.

**Mit jelent ez gyakorlatban?**
- A bináris ISO visszafejtése, módosítása, és újrafordítása **illegális**.
- A forráskód kinyerése bármilyen eszközzel (IDA, Ghidra, radare2, strings, objdump, stb.) **tilos**.
- A visszafejtett kód alapján új disztribúció létrehozása és terjesztése **szerzői jogi jogsértés**.

**Következmények:**
- Polgári peres eljárás kártérítési igénnyel.
- Büntetőfeljelentés számítógépes csalás / jogosulatlan adathozzáférés miatt.
- A jogsértő anyagok eltávolításának kötelezettsége.

> *"A forráskód nem publikus. A bináris sem a tiéd. Használd, de ne bántsd."*

> 💬 *"Miért nem látja a hackert a rendőrség? Mert root jogokkal fut."*

---

## ⚠️ Hamis / Illegális Fork-ok

**Minden "FluxOS Ultimate Edition", "FluxOS Pro", "FluxOS Modified", vagy hasonló néven futó disztribúció, amely nem ezen a GitHub repository-n keresztül lett kiadva, HAMIS vagy ILLEGÁLIS.**

Ezek a fork-ok:
- Visszafejtett binárisokon alapulnak (lásd fentebb: ez illegális).
- Tartalmazhatnak malware-t, keylogger-t, vagy egyéb kártékony kódot.
- Nincsenek tesztelve, instabilak lehetnek.
- Nem kapnak frissítéseket, biztonsági patch-eket.

**Ha ilyet látsz:**
1. **NE töltsd le.**
2. **NE telepítsd.**
3. **Jelezd Discordon:** [discord.gg/fluxos](https://discord.gg/fluxos) (vagy a README tetején lévő linken)

A jelentéshez add meg:
- A hamis disztribúció nevét és URL-jét.
- Hol találtad (Reddit, YouTube, fórum, stb.).
- Ha letöltötted, a fájl hash-ét (SHA256).

Minden jelentést kivizsgálunk, és szükség esetén jogi lépéseket kezdeményezünk.

> 💬 *"Miért nem lehet megvenni a hamis FluxOS-t? Mert a pénztáros is tudja, hogy lopott áru."*

---

## 📜 Licenc

**All Rights Reserved.** © FluxOS Team

A FluxOS szoftver és annak minden komponense a szerző tulajdonát képezi. A bináris ISO szabadon letölthető és használható, de a forráskód, a build szkriptek, és a disztribúcióhoz tartozó egyedi komponensek nem publikusak.

> *Használd egészséggel. Ne forkold. Ne áruld. Ne kérdezd meg mégegyszer, hogy hol a source.*

> 💬 *"Miért nem ír alá szerződést a szabad szoftver? Mert nincs copyright-ja."*

---

<p align="center">
  <b>FluxOS</b> — Arch alapú. AUR ready. Konténer nélkül. Source nélkül.
</p>
