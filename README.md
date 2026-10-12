# FluxOS

```{=html}
<p align="center">
```
`<strong>`{=html}Build your dream.`</strong>`{=html}`<br>`{=html} Egy
saját arculatú Linux-platform játékhoz, munkához és fejlesztéshez.
```{=html}
</p>
```
```{=html}
<p align="center">
```
`<img alt="Version" src="https://img.shields.io/badge/version-5.0.0--alpha-blue">`{=html}
`<img alt="Status" src="https://img.shields.io/badge/status-in%20development-orange">`{=html}
`<img alt="Platform" src="https://img.shields.io/badge/platform-x86__64-informational">`{=html}
```{=html}
</p>
```
> **A FluxOS célja:** egy egységes, modern és bővíthető operációs
> rendszerélmény létrehozása saját asztali felülettel,
> rendszereszközökkel és alkalmazás-ökoszisztémával.

**Fejlesztési állapot:** alpha. A README-ben szereplő funkciók
fejlesztési célok, amíg az adott kiadás dokumentációja nem igazolja,
hogy ténylegesen elkészültek és tesztelve vannak.

------------------------------------------------------------------------

## Mi a FluxOS?

A FluxOS egy Linux-alapú rendszerplatform koncepciója, amely a
mindennapi használatot, a játékot és a fejlesztést egyetlen következetes
élménybe szeretné rendezni.

Nem egyetlen disztribúció felhasználói felületének átszínezése a cél. A
hosszú távú terv egy saját márkával, beállításközponttal, telepítési
élménnyel, profilrendszerrel és frissítési folyamattal rendelkező
platform.

### Alapelvek

-   **Saját élmény:** egységes asztal, első indítás, beállítások és
    rendszereszközök.
-   **Moduláris architektúra:** az UI, a rendszerintegráció és az
    alkalmazásréteg külön fejleszthető.
-   **Alapréteg-függetlenség:** a disztribúcióspecifikus műveletek külön
    adaptereken keresztül érhetők el.
-   **Biztonság alapértelmezésben:** ellenőrzött források, jogosultságok
    és átlátható frissítések.
-   **Mérhető minőség:** reprodukálható build, automatizált tesztek és
    dokumentált hardvertámogatás.
-   **Fokozatos fejlődés:** a funkciók csak tesztelés után kerülnek
    stabilként megjelölésre.

## Profilok

A profilok az alkalmazáscsomagokat és a rendszerbeállításokat a
felhasználási célhoz igazítják.

  -----------------------------------------------------------------------
  Profil                  Mire való?              Fő irány
  ----------------------- ----------------------- -----------------------
  **Gaming**              Játék, streaming,       Grafikus gyorsítás,
                          játékindítók            kompatibilitási
                                                  eszközök, felvétel

  **Office**              Tanulás, dokumentumok,  Irodai alkalmazások,
                          produktivitás           jegyzetelés, fókusz

  **Developer**           Programozás és          Fordítók, Git, IDE-k,
                          buildelés               tesztelőeszközök

  **Server**              Szolgáltatások és       Minimalizált telepítés,
                          távoli adminisztráció   naplózás, hálózati
                                                  biztonság

  **Minimal**             Saját rendszer építése  Kis alaprendszer,
                                                  opcionális komponensek
  -----------------------------------------------------------------------

A profilok közös alapra épülnek. A váltásnak meg kell őriznie a
személyes fájlokat, és egyértelműen jeleznie kell, milyen csomagokat
vagy beállításokat módosít.

## Energia- és teljesítménykezelés

A tervezett `flux-power` parancs és a grafikus beállításközpont egységes
felületet ad az energiaállapotokhoz.

  -----------------------------------------------------------------------
  Mód                                 Cél
  ----------------------------------- -----------------------------------
  **Eco**                             Energiatakarékos működés

  **Balanced**                        Általános, kiegyensúlyozott
                                      használat

  **Performance**                     Játék, fordítás és renderelés
                                      alatti nagyobb teljesítmény
  -----------------------------------------------------------------------

A tényleges hatás hardver- és driverfüggő. A rendszer nem kerülheti meg
a CPU vagy GPU biztonsági hőmérsékleti és fogyasztási korlátait.

## FluxOS-élmény

A projekt saját felületének és eszközeinek tervezett részei:

-   **Flux Desktop:** egységes asztali környezet és ablakkezelési
    élmény.
-   **Control Center:** rendszerinformációk, profilok, energia és
    eszközbeállítások.
-   **Setup Wizard:** áttekinthető telepítési és első indítási folyamat.
-   **Flux Update:** frissítések ellenőrzése, telepítése és hibajelzése.
-   **App Catalog:** alkalmazások felfedezése és telepítése ellenőrzött
    forrásból.
-   **Gaming eszközök:** játékindítók, kompatibilitási rétegek és
    streaming-eszközök.
-   **Developer eszközök:** fejlesztői környezetek és buildfolyamatok
    egyszerű elérése.

Ezek tervezett komponensek; a kiadási jegyzetnek kell megmondania,
melyik érhető el ténylegesen az adott verzióban.

## Alapréteg-független architektúra

A FluxOS nem kötheti a teljes rendszerlogikát egyetlen disztribúció
csomagkezelőjéhez.

A javasolt rétegek:

1.  **Flux UX:** asztal, beállítások, telepítő és felhasználói
    alkalmazások.
2.  **Flux Core:** profilok, konfiguráció, rendszerállapot és közös
    API-k.
3.  **Platform adapterek:** csomagtelepítés, frissítés,
    szolgáltatáskezelés, kernel- és driverinformáció.
4.  **Linux alapréteg:** az adott build által támogatott disztribúció és
    annak csomagjai.

Az adaptereknek explicit módon kell jelezniük a képességeiket. Ha egy
platformon egy funkció nem támogatott, a FluxOS adjon érthető
hibaüzenetet ahelyett, hogy más disztribúció parancsát próbálná
lefuttatni.

A „több alapréteg támogatása" csak akkor tekinthető késznek, ha minden
támogatott célhoz létezik buildkonfiguráció, telepítési útmutató és
sikeres teszt.

## Rendszerkövetelmények

Az alábbiak kezdeti célértékek, nem minden hardverre érvényes garanciák.

  -----------------------------------------------------------------------
  Erőforrás               Egyszerű használat      Gaming / fejlesztés
  ----------------------- ----------------------- -----------------------
  **CPU**                 Támogatott 64 bites     Modern, többmagos CPU
                          x86-64 CPU              

  **RAM**                 2--4 GB lehet a cél,    8 GB vagy több ajánlott
                          grafikus felülettől     
                          függően                 

  **Tárhely**             Legalább 20 GB szabad   50 GB vagy több SSD-n
                          hely                    

  **GPU**                 Támogatott integrált    Az alkalmazásokhoz illő
                          grafika                 GPU

  **Internet**            Frissítéshez és online  Stabil szélessávú
                          telepítéshez            kapcsolat
  -----------------------------------------------------------------------

A tényleges minimumot minden stabil kiadás előtt hardveren vagy
dokumentált virtuális gépben kell ellenőrizni.

## Telepítés

1.  Töltsd le az ISO-t a projekt hivatalos
    [Releases](https://github.com/bencepalko383-lgtm/Flux-OS/releases)
    oldaláról.
2.  Ellenőrizd az ellenőrzőösszeget vagy a kiadáshoz tartozó aláírást,
    ha elérhető.
3.  Készíts telepítő USB-t egy megbízható lemezképíróval.
4.  Indítsd el a számítógépet az USB-ről.
5.  Ha elérhető, próbáld ki a live környezetet a telepítés előtt.
6.  A telepítőben ellenőrizd a céllemezt, a partíciókat és a telepítési
    módot.
7.  Készíts biztonsági mentést, mielőtt bármilyen lemezmódosítást
    jóváhagysz.
8.  Az első indítás után teszteld a hálózatot, a hangot, a grafikus
    gyorsítást és a frissítéseket.

> **Figyelem:** a telepítés adatvesztést okozhat. Ne használj vakon
> példákból átvett lemezneveket vagy destruktív parancsokat; mindig
> ellenőrizd a célmeghajtót.

A hálózatkezelés, a particionálás, a bootloader és a csomagtelepítés
pontos lépései az adott FluxOS-kiadástól és alaprétegtől függenek. A
kiadási dokumentáció ezekhez konkrét, tesztelt útmutatót kell adjon.

## Frissítés, biztonság és helyreállítás

A frissítési rendszer célja:

-   a csomagok és metaadatok ellenőrzése;
-   a frissítési források egyértelmű megjelenítése;
-   naplózás és használható hibaüzenetek;
-   megszakadt frissítés kezelése;
-   támogatott rendszereken visszaállítási lehetőség biztosítása.

A FluxOS nem kérhet szükségtelen rendszergazdai jogosultságot, és nem
futtathat ellenőrizetlen távoli szkripteket automatikusan. A stabil
kiadásokhoz biztonsági frissítési folyamatot és
sérülékenység-bejelentési csatornát kell fenntartani.

## Hardverkompatibilitás

A kompatibilitást tényleges tesztek alapján kell dokumentálni. A
támogatás függ a kerneltől, a firmware-től, a driverektől és a grafikus
stacktől.

  Terület             Tesztelendő funkciók
  ------------------- ---------------------------------------
  Intel / AMD CPU     Boot, energiafelügyelet, hőmérséklet
  Intel / AMD GPU     Kijelző, gyorsítás, alvás és ébredés
  NVIDIA GPU          Megfelelő driver és grafikus stack
  Laptop              Akkumulátor, fényerő, Wi-Fi, alvó mód
  Wi-Fi / Bluetooth   Felismerés, kapcsolat, hang
  Virtuális gép       Boot, grafika, hálózat
  Több GPU            Alkalmazásonkénti GPU-választás

Egy hardver csak akkor jelölhető teljesen támogatottnak, ha a tesztelt
modell, a FluxOS-verzió és az eredmény dokumentálva van.

## Fejlesztés és minőségbiztosítás

A buildfolyamatnak külön munkakönyvtárat, hibánál leálló szkripteket,
naplózást és reprodukálható kimenetet kell használnia.

A kiadás előtti ellenőrzések:

-   build- és csomagolási tesztek;
-   ISO ellenőrzőösszeg és build-metaadat;
-   bootteszt virtuális gépben;
-   telepítési és első indítási teszt;
-   hálózat-, hang- és grafikai alaptesztek;
-   frissítési és helyreállítási teszt;
-   ismert hibák és korlátozások dokumentálása.

A buildhez szükséges pontos parancsokat és függőségeket a repository
tényleges buildszkriptjeihez kell igazítani. Ez a dokumentum nem
állítja, hogy a felsorolt tesztek már mind megvalósultak.

## Licenc és külső komponensek

A FluxOS saját komponenseinek felhasználási feltételeit a repository
licencfájlja határozza meg. A kernel, a driverek és a csomagolt külső
alkalmazások saját licencei továbbra is érvényesek.

A kiadásoknak dokumentálniuk kell a felhasznált külső összetevőket, a
szükséges szerzői jogi közleményeket és a vonatkozó licenceket. A
projekt saját licencét a tényleges terjesztési modellhez és az
alkalmazott komponensek feltételeihez kell igazítani.

## Fejlesztési ütemterv

### 1. Stabil alap

-   [ ] Reprodukálható build és ellenőrizhető ISO
-   [ ] Telepítő és első indítás
-   [ ] Boot- és hardvertesztek
-   [ ] Hibajelentési folyamat

### 2. Saját felhasználói élmény

-   [ ] Flux Desktop és Control Center
-   [ ] Gaming, Office, Developer és Server profilok
-   [ ] Energia- és teljesítménykezelés
-   [ ] Helyreállítási lehetőségek

### 3. Ökoszisztéma

-   [ ] Alkalmazáskatalógus
-   [ ] Fejlesztői SDK és dokumentáció
-   [ ] Automatizált tesztelés és kiadási pipeline
-   [ ] Támogatási és biztonsági folyamat

A jelölőnégyzetek a fejlesztési tervet jelölik, nem a jelenlegi
készültségi állapotot.

## Hibajelentés

Hibabejelentéshez add meg a FluxOS-verziót, a hardvert, a reprodukálás
lépéseit és a releváns naplórészleteket. Jelszót, tokent vagy személyes
fájlokat ne csatolj.

## Hivatkozások

-   **GitHub:**
    [bencepalko383-lgtm/Flux-OS](https://github.com/bencepalko383-lgtm/Flux-OS)
-   **Kiadások:** [FluxOS
    Releases](https://github.com/bencepalko383-lgtm/Flux-OS/releases)

------------------------------------------------------------------------

```{=html}
<p align="center">
```
`<strong>`{=html}FluxOS --- Build your dream.`</strong>`{=html}
```{=html}
</p>
```
