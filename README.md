# FluxOS 〰️

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Version](https://img.shields.io/badge/version-0.1.0--alpha-blue)](https://github.com/)
[![Base](https://img.shields.io/badge/Based%20on-Fedora-red)](https://getfedora.org/)

A **FluxOS** egy Fedora alapú, modern és minimalista Linux disztribúció, amelyet úgy terveztünk, hogy egyszerre legyen villámgyors, pehelysúlyú és végtelenül testreszabható. Nem számít, hogy hardcore játékos, irodai alkalmazott vagy szerveradminisztrátor vagy – a FluxOS alkalmazkodik az igényeidhez.

---

## 🚀 Főbb funkciók

### 🎭 Intelligens Felhasználói Profilok
A telepítés során vagy akár utólag is egyetlen kattintással váthatsz a célnak megfelelő profilok között:
* 🎮 **Gaming:** Optimalizált kernel-beállítások, előre konfigurált Wine, Proton és Steam támogatás, minimális háttérfolyamatok a maximális FPS érdekében.
* 💼 **Office:** Letisztult, zavaró tényezőktől mentes felület, LibreOffice csomag és produktivitást segítő eszközök.
* 🖥️ **Server:** Grafikus felület nélküli (vagy minimális GUI-val rendelkező), biztonságra és stabilitásra kihegyezett környezet.

### ⚡ Dinamikus Energia Módok
A beépített `flux-power` démon segítségével azonnal válthatsz az élethelyzetednek megfelelő profilok között:
* 🔋 **Takarékos (Eco):** Maximális akkumulátor-üzemidő laptopokon, visszafogott órajelek.
* ⚖️ **Egyensúlyozott (Balanced):** Intelligens erőforrás-elosztás a mindennapi feladatokhoz.
* 🔥 **Teljesítmény (Performance):** Nyers erő limitációk nélkül – ideális játékhoz és rendereléshez.

### 📦 Előre telepített szoftverek & Extrák
* 🌐 **Brave böngésző:** Alapértelmezett, adatvédelmet szem előtt tartó böngészés reklámblokkolóval.
* 🎥 **OBS Studio:** Streamelésre és videófelvételre készen, előre optimalizált kódolókkal.
* 🏄 **In-Installer Surfing Game:** Unalmas a telepítési idő? Játssz a beépített retro szörfös játékkal, amíg a rendszer felmásolódik!
* 🔒 **Egyedi Lockscreen:** Modern, minimalista és animált zárolási képernyő beépített időjárás-előrejelzéssel.
* 🔄 **GitHub alapú frissítő:** Felejtsd el a bonyolult csomagkezelőket, a `flux-update` parancs közvetlenül a GitHub tárolóból húzza le a legfrissebb rendszerkomponenseket.

---

## 💻 Rendszerkövetelmények

| Erőforrás | Minimum követelmény | Ajánlott konfiguráció |
| :--- | :--- | :--- |
| **Processzor** | 64-bites kétmagos CPU (1.5 GHz) | Quad-core Intel i5 / AMD Ryzen 5 vagy jobb |
| **Memória** | 2 GB RAM (Server / Office profil) | 8 GB+ RAM (Gaming profil) |
| **Tárhely** | 15 GB szabad hely | 40 GB+ SSD szabad hely |
| **Grafika** | Intel HD Graphics / Integrált GPU | Nvidia GTX 1050 / AMD RX 560 vagy újabb |

---

## 💿 Telepítési útmutató

1.  **Letöltés:** Töltsd le a legfrissebb `FluxOS.iso` fájlt a [Releases](https://github.com/) menüpont alól.
2.  **Írás pendrive-ra:** Használj [BalenaEtcher](https://www.balena.io/etcher/) vagy [Rufus](https://rufus.ie/) programot az ISO fájl kiírásához egy legalább 4 GB-os pendrive-ra.
3.  **Bootolás:** Indítsd újra a számítógéped, lépj be a BIOS/UEFI menübe, és válaszd ki a pendrive-odat elsődleges boot eszközként.
4.  **Telepítő Wizard:** Kövesd a grafikus telepítő lépéseit, válaszd ki a profilodat, és közben döntsd meg a pontrekordot a szörfös játékban!

> ⚠️ **Figyelem:** A telepítés során a kiválasztott meghajtó tartalma törlődni fog. Mindig készíts biztonsági mentést a fontos adataidról!

---

## 🛠️ Fejlesztés és ISO Build

Ha szeretnéd saját magad módosítani a rendszert vagy hozzájárulni a fejlesztéshez, az ISO-t az alábbi módon tudod helyben elkészíteni.

### Előfeltételek (Fedora alapú rendszeren)
```bash
sudo dnf install lorax livecd-tools git -y
