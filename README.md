# FluxOS ⚡

> **FluxOS --- Build your dream.**\
> Egy saját arculatú, moduláris Linux-disztribúció és asztali platform,
> amelyet játékra, munkára és fejlesztésre lehet szabni.

![Version](https://img.shields.io/badge/version-5.0.0--alpha-blue)
![Platform](https://img.shields.io/badge/platform-x86__64-informational)
![Status](https://img.shields.io/badge/status-alpha-orange)

> **Állapot:** a FluxOS fejlesztés alatt álló projekt. Az itt felsorolt
> funkciók közül csak azok tekinthetők elérhetőnek, amelyek a jelenlegi
> buildben ténylegesen megvalósultak és tesztelve vannak.

## Mi a FluxOS?

A FluxOS célja, hogy egységes, könnyen használható Linux-élményt adjon
saját kezelőfelülettel, profilokkal, rendszereszközökkel és
alkalmazásintegrációval. Nem egyetlen disztribúció parancsait vagy
csomagkezelőjét teszi kötelezővé: a rendszer összetevőit egy cserélhető
alapréteghez tervezzük illeszteni.

A projekt céljai:

-   **Saját felhasználói élmény:** következetes asztal, beállítások és
    első indítási folyamat.
-   **Moduláris felépítés:** a grafikus felület, rendszereszközök és
    profilok külön fejleszthetők.
-   **Hardverhez igazodás:** ésszerű alapbeállítások laptopokhoz,
    asztali gépekhez és virtuális gépekhez.
-   **Ellenőrizhető build:** ismételhető összeállítás, naplózás és
    tesztek.
-   **Biztonságos frissítés:** ellenőrizhető csomagforrások, aláírások
    és visszaállítási lehetőségek.
-   **Hosszú távú bővíthetőség:** később saját alkalmazásbolt,
    csomagformátum és fejlesztői SDK is kialakítható.

## Kiadások és profilok

A profilok eltérő alapbeállításokat és alkalmazáscsomagokat választanak
ki. A profilváltásnak a felhasználói fájlokat és a személyes
beállításokat meg kell őriznie.

  -----------------------------------------------------------------------
  Profil                  Cél                     Javasolt összetevők
  ----------------------- ----------------------- -----------------------
  **Gaming**              Játék és streaming      grafikus gyorsítás,
                                                  kompatibilitási réteg,
                                                  játékindító, felvételi
                                                  eszközök

  **Office**              Tanulás és              irodai csomag, naptár,
                          produktivitás           jegyzetelés,
                                                  fókuszbeállítások

  **Server**              Szolgáltatások          minimális telepítés,
                          futtatása               távoli adminisztráció,
                                                  naplózás, szigorúbb
                                                  hálózati alapértékek

  **Developer**           Programozás és          fordítók, Git,
                          tesztelés               szerkesztők,
                                                  buildeszközök és
                                                  konténerek opcionálisan

  **Minimal**             Kis alaprendszer        csak az alapvető
                                                  rendszerkomponensek
  -----------------------------------------------------------------------

A profilok nem külön operációs rendszerek: közös alaprendszerre épülő
konfigurációk. A pontos csomaglista a kiadás és az alapréteg függvénye.

## Energia- és teljesítménymódok

A tervezett `flux-power` felület egységes parancsot ad az energia- és
teljesítményprofilokhoz. A tényleges viselkedés a hardvertől és az
elérhető rendszerkomponensektől függ.

  -----------------------------------------------------------------------
  Mód                                 Cél
  ----------------------------------- -----------------------------------
  **Eco**                             Alacsonyabb fogyasztás és hosszabb
                                      akkumulátoros üzemidő

  **Balanced**                        Általános használat
                                      kiegyensúlyozott beállításokkal

  **Performance**                     Nagyobb teljesítmény játékhoz,
                                      fordításhoz vagy rendereléshez
  -----------------------------------------------------------------------

A Performance mód nem garantál korlátlan órajelet, és nem írhatja felül
a hardver biztonsági hő- és fogyasztási korlátait.

## Alkalmazások és szolgáltatások

A FluxOS tervezett alkalmazás- és rendszerkomponensei:

-   **Böngésző:** adatvédelmi beállításokkal és frissítési folyamattal.
-   **OBS Studio:** képernyőfelvétel és streaming, ha az adott profilban
    telepítve van.
-   **Játékkompatibilitás:** a hardverhez és az alapréteghez illő
    futtatókörnyezetek.
-   **Képernyőzár:** saját arculatú felület; időjárás csak engedélyezett
    hálózati szolgáltatással.
-   **Frissítő:** a rendszer által támogatott, ellenőrzött forrásokból
    frissít.
-   **Beállításközpont:** rendszerinformáció, eszközök, energia és
    profilok kezelése.

A README nem tekinti előre telepítettnek azokat az alkalmazásokat,
amelyek még nincsenek benne az adott ISO-ban. A kiadási jegyzeteknek
kell felsorolniuk a valóban elérhető komponenseket.

## Rendszerkövetelmények

Ezek kezdeti célértékek, nem minden hardveren igazolt garanciák.

  -----------------------------------------------------------------------
  Erőforrás               Minimális cél           Ajánlott cél
  ----------------------- ----------------------- -----------------------
  **CPU**                 64 bites, támogatott    modern, többmagos CPU
                          x86-64 processzor       

  **RAM**                 2--4 GB egyszerű        8 GB vagy több;
                          használathoz            fejlesztéshez és
                                                  játékhoz több is
                                                  hasznos

  **Tárhely**             legalább 20 GB szabad   50 GB vagy több SSD-n
                          hely                    

  **GPU**                 támogatott integrált    a használt játékokhoz
                          grafika                 vagy munkafolyamatokhoz
                                                  megfelelő GPU

  **Internet**            telepítéshez és         stabil szélessávú
                          frissítéshez szükséges  kapcsolat
  -----------------------------------------------------------------------

A tényleges követelményeket az asztali környezet, a kiválasztott profil
és az alkalmazások határozzák meg. Nagyobb rendszerkomponensek
fordításához több RAM és szabad tárhely szükséges.

## Telepítés

A telepítő felülete és lépései kiadásonként változhatnak. **Csak a
projekt hivatalos kiadási oldaláról származó, ellenőrzött ISO-t
használd.**

1.  Töltsd le a kiadáshoz tartozó ISO-t és az ellenőrzőösszeget vagy
    aláírást.
2.  Ellenőrizd a letöltött fájl épségét.
3.  Készíts telepítő USB-meghajtót egy megbízható lemezképíró eszközzel.
4.  Indítsd el a gépet az USB-meghajtóról.
5.  Próbáld ki a live környezetet, ha a kiadás biztosít ilyet.
6.  A telepítőben ellenőrizd még egyszer a céllemezt és a partíciókat.
7.  Csak az adatokról készített biztonsági mentés után indítsd el a
    telepítést.
8.  Az első indítás után ellenőrizd a hálózatot, a hangot, a grafikát és
    a frissítéseket.

> **Figyelem:** a lemezparticionálás és a telepítés adatvesztést
> okozhat. Ne másolj vakon példaparancsokat, és ne feltételezd, hogy egy
> adott `/dev/sdX` mindig ugyanazt a lemezt jelenti. Előbb ellenőrizd az
> eszköz nevét és méretét.

### Internet és hálózat

A hálózat konfigurációja az alaprétegtől függ. Ha nincs kapcsolat:

1.  ellenőrizd a kábel- vagy Wi-Fi-kapcsolatot;
2.  nézd meg, hogy a hálózatkezelő szolgáltatás fut-e;
3.  ellenőrizd, hogy a megfelelő firmware és illesztőprogram elérhető-e;
4.  olvasd el az adott kiadás hibaelhárítási útmutatóját.

A pontos parancsokat a FluxOS adott kiadásához kell megadni; nem
feltételezzük, hogy minden rendszeren ugyanaz a hálózatkezelő vagy
csomagkezelő van telepítve.

## Frissítés és helyreállítás

A rendszerfrissítésnek ellenőrzött forrásból kell történnie. A FluxOS
frissítőjének célja, hogy:

-   ellenőrizze a letöltött metaadatokat és csomagokat;
-   egyértelműen jelezze a sikert vagy a hibát;
-   naplót készítsen;
-   megszakadt frissítés után biztonságos helyreállítást tegyen
    lehetővé;
-   lehetőség szerint támogassa az előző működő állapot visszaállítását.

Amíg a FluxOS saját frissítője nem érhető el az adott kiadásban, az
alapréteg hivatalos frissítési eljárását kell követni. Ne futtass
ismeretlen, távoli szkripteket rendszergazdai jogosultsággal.

## Hardverkompatibilitás

A támogatás a kernel, a firmware, a grafikus stack és a kiadás
összetevőitől függ. A kompatibilitási listát tényleges tesztek alapján
kell vezetni.

  Terület               Ellenőrizendő
  --------------------- ----------------------------------------------------
  Intel / AMD CPU       boot, energiagazdálkodás, hőmérséklet
  Intel / AMD grafika   kijelző, gyorsítás, alvásból ébredés
  NVIDIA grafika        az adott GPU-hoz illő driver és grafikus stack
  Laptop                akkumulátor, fényerő, Wi-Fi, alvó mód
  Bluetooth             eszközfelismerés és hang
  Virtuális gép         grafika, hálózat, megosztott eszközök
  Több GPU              külső GPU-ra irányított alkalmazások és fogyasztás

Egy eszköz csak akkor jelölhető teljesen támogatottnak, ha a tesztelt
hardver és a kiadás verziója dokumentálva van.

## Fejlesztés és build

A FluxOS célja a reprodukálható build. Az alapréteg kiválasztása külön
konfigurációban történjen, ne legyen szétszórva a kódban.

A buildrendszernek legalább a következőket kell biztosítania:

-   a buildhez szükséges függőségek ellenőrzése;
-   a célplatform és az alapréteg explicit kiválasztása;
-   külön munkakönyvtár, amelyet a projekt forrásai nem írnak felül;
-   naplózás és hibánál azonnali leállás;
-   a kész ISO méretének, hashének és build-metaadatainak rögzítése;
-   tesztek futtatása a kiadás előtt.

A konkrét buildparancsokat a repository aktuális szkriptjei és
dokumentációja alapján kell megadni. Ez a README önmagában nem állítja,
hogy minden célplatformhoz már kész build pipeline tartozik.

## Biztonsági alapelvek

-   Csak ellenőrzött forrásból származó csomagokat és kiadásokat
    használj.
-   A kiadásokhoz tartozzon ellenőrzőösszeg, lehetőség szerint aláírás
    is.
-   A rendszer ne kérjen folyamatosan rendszergazdai jogosultságot.
-   A frissítő ne hajtson végre ellenőrizetlen távoli kódot.
-   A hibákat naplózza, a személyes adatokat pedig ne gyűjtse
    szükségtelenül.
-   A biztonsági hibák bejelentéséhez legyen dokumentált
    kapcsolatfelvételi csatorna.

## Licenc és külső összetevők

A FluxOS saját komponenseinek licencét a repositoryban található
licencfájl határozza meg. A Linux kernel és a csomagolt külső programok
külön licencek alatt állhatnak; ezeket tiszteletben kell tartani, és a
kiadásban szereplő licenceket dokumentálni kell.

A külső nyílt forráskódú összetevők használata nem jelenti azt, hogy
azok licencei figyelmen kívül hagyhatók. A terjesztési csomagban fel
kell tüntetni a szükséges szerzői jogi és licencinformációkat.

## Ütemterv

### Alapok

-   [ ] Stabil buildfolyamat és ISO-ellenőrzés
-   [ ] Telepítő és első indítási folyamat
-   [ ] Hardver- és kompatibilitási tesztek
-   [ ] Hibajelentési és kiadási folyamat

### Felhasználói élmény

-   [ ] Egységes asztal és beállításközpont
-   [ ] Gaming, Office, Server és Developer profilok
-   [ ] Energia- és teljesítménykezelés
-   [ ] Helyreállítási lehetőségek

### Ökoszisztéma

-   [ ] Alkalmazáskatalógus
-   [ ] Fejlesztői dokumentáció és SDK
-   [ ] Automatikus tesztelés és kiadási pipeline
-   [ ] Világos támogatási és frissítési politika

A jelölőnégyzetek a projekt céljait mutatják; csak a ténylegesen
elkészült funkciókat szabad késznek jelölni.

## Közreműködés és hibajelentés

Hibajelentéskor add meg:

-   a FluxOS kiadását és verzióját;
-   a hardvert és a grafikus vezérlőt;
-   a hiba reprodukálásának lépéseit;
-   a releváns naplórészleteket;
-   hogy a probléma friss telepítés után is jelentkezik-e.

Ne küldj jelszavakat, hozzáférési tokeneket vagy személyes fájlokat a
hibajegyben.

## Projekt

-   **Repository:** [Flux-OS a
    GitHubon](https://github.com/bencepalko383-lgtm/Flux-OS)
-   **Kiadások:**
    [Releases](https://github.com/bencepalko383-lgtm/Flux-OS/releases)

------------------------------------------------------------------------

**FluxOS --- Build your dream.**
