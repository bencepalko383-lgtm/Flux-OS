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

## 💿 Telepítés

### 1. ISO letöltés
Töltsd le a legfrissebb `fluxos-<dátum>-<kernel>-x86_64.iso` fájlt a [Releases](https://github.com/bencepalko383-lgtm/Flux-OS/releases) alól.

### 2. Bootolható média készítése

```bash
# dd-vel (Linux)
sudo dd if=fluxos-*.iso of=/dev/sdX bs=4M status=progress oflag=sync

# vagy Ventoy-val, vagy Rufus-sal (Windows)
```

### 3. Boot és telepítés

1. Indítsd újra, válaszd a pendrive-ot boot eszközként
2. Válaszd ki a profilodat a telepítőben
3. Játssz a szörfös játékkal amíg települ
4. Restart, és kész

> ⚠️ **FIGYELEM:** A telepítés törli a célmeghajtót. Backup előtte.

---

## 🛠️ ISO Build (Natív Arch)

Ha saját ISO-t akarsz buildelni Arch Linuxon:

### Előfeltételek

```bash
sudo pacman -S --needed base-devel archiso git reflector
```

### Build

```bash
git clone https://github.com/bencepalko383-lgtm/Flux-OS.git
cd Flux-OS/build
sudo bash build-iso.sh --kernel cachyos --enable-extra-aur --use-reflector
```

### Build opciók

```bash
# Alap build CachyOS kernellel
sudo bash build-iso.sh

# Zen kernel + AUR csomagok + QEMU teszt
sudo bash build-iso.sh --kernel zen --enable-extra-aur --test-boot --test-ram 4096

# TKG kernel + paru + multilib
sudo bash build-iso.sh --kernel tkg --aur-helper paru --enable-multilib

# Dry-run (ellenőrzés)
sudo bash build-iso.sh --dry-run --verbose
```

### Build flag-ek

| Flag | Leírás |
|------|--------|
| `--kernel <név>` | Kernel választás (cachyos, zen, lts, stock, hardened, rt, ck, xanmod, mainline, tkg, clear) |
| `--aur-helper <név>` | yay, paru, pikaur, trizen, aura |
| `--enable-multilib` | 32-bites csomagok támogatása |
| `--enable-testing` | Testing repo engedélyezése |
| `--enable-extra-aur` | Extra AUR csomagok beépítése |
| `--use-reflector` | Automatikus tükörlista frissítés |
| `--compression zstd` | SquashFS tömörítés |
| `--test-boot` | QEMU boot teszt build után |
| `--write-usb /dev/sdX` | ISO közvetlen USB-re írás |
| `--upload-github` | GitHub Release feltöltés |

---

## 🔒 Forráskód — Miért nem publikus?

### Röviden: **Mert nem.**

#### Hosszabban:

A FluxOS forráskódja **zárt, privát repository-ban** van. Nem open source, nem GPL, nem MIT. Ha azt várod, hogy `git clone` után szabadon forkolhatsz és módosíthatsz, akkor rossz helyen jársz.

**Miért?**

1. **Ez egy személyes projekt.** Nem egy közösségi effort, nem kérek PR-eket, és nem akarom, hogy valaki "javítson" rajta olyan módon, ami nekem nem tetszik.

2. **A build pipeline bonyolult.** Natív Arch, AUR integráció, custom kernel forkok, saját repo kezelés — ha nem érted, úgyis eltöri. Ha érted, akkor meg írd meg magadnak.

3. **Nem vagyok nonprofit.** Ha adsz pénzt, akkor sem kapsz source hozzáférést. Az ISO ingyenes, a kód nem az üzleti modell része.

4. **A forráskód elérhető a binárisban.** Visszafejtheted, ha ennyire kell. De ne tedd, mert:
   - Nem éri meg az idődet
   - Valószínűleg jobb disztrót tudnál írni, ha már ennyire érdekel
   - Nem tudod buildelni anélkül, hogy ne törnéd el a saját rendszered

**Mit kapsz helyette?**
- Ingyenes ISO-t
- Működő rendszert
- Frissítéseket
- Egyedi telepítőt szörf játékkal

**Amit nem kapsz:**
- Forráskódot
- Magyarázatot
- Közösségi támogatást GitHub Issues formájában
- Lehetőséget, hogy forkold és "FluxOS Ultimate Edition" néven áruld

> *"Ha a forráskód olyan fontos neked, használj Gentoo-t. Ott minden forrásból buildelsz, és még a hajad is kihullik közben."*

---

## 📋 Parancsok

```bash
# Profil váltás
flux-profile switch gaming
flux-profile switch office
flux-profile switch server

# Energia mód
flux-power eco
flux-power balanced
flux-power performance

# Rendszerfrissítés
flux-update

# AUR csomag keresés
flux-aur search <csomag>

# Build info
flux-info
```

---

## 🐛 Hibajelentés

Ha hibát találsz, írj egy emailt a fejlesztőnek. Ha nem találod az email címet, akkor nem is volt olyan fontos a hiba.

---

## 📜 Licenc

**All Rights Reserved.** © FluxOS Team

A FluxOS szoftver és annak minden komponense a szerző tulajdonát képezi. A bináris ISO szabadon letölthető és használható, de a forráskód, a build szkriptek, és a disztribúcióhoz tartozó egyedi komponensek nem publikusak.

> *Használd egészséggel. Ne forkold. Ne áruld. Ne kérdezd meg mégegyszer, hogy hol a source.*

---

<p align="center">
  <b>FluxOS</b> — Arch alapú. AUR ready. Konténer nélkül. Source nélkül.
</p>
