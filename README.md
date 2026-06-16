# 👥 Felhasználó létrehozása és jogosultságok beállítása (RBAC)


## 🛠️ Lépések:

### 1. Azure Portalon való belépés
1. Nyiss meg egy böngészőt, és navigálj a [https://azure.com](https://azure.com) oldalra.
2. Jelentkezz be a fiókoddal.

### 2. Microsoft Entra ID megnyitása
1. A felső keresősávba írd be: `Microsoft Entra ID` (korábban Azure Active Directory).
2. Kattints a szolgáltatásra a találati listában.

### 3. Felhasználó létrehozása és Jelszó beállítása
1. A bal oldali menüben kattints a **Kezelés** > **Felhasználók** opcióra.
2. Felül kattints a **Új felhasználó** > **Új felhasználó létrehozása** gombra.
3. Töltsd ki az az **Alapadatok** fület:
   * **Egyszerű felhasználónév:** `tesztuser` (a legördülő menüből válaszd ki a domain neved).
   * **Megjelenítendő név:** `Teszt Elek`
4. A **Jelszó** résznél válaszd az *Jelszó automatikus létrehozása* opciót vagy add meg manuálisan. 
5. ⚠️ **Fontos:** Másold ki a generált jelszót, mert az első belépésnél szükséged lesz rá!
6. Kattints a **Áttekintés és létrehozás**, majd a **Létrehozás** gombra.
7. Vagy töltsd ki akár a **Tulajdonságok** vagy q **Hozzárendelések** fület, aztán kattints a**Létrehozás** gombra.

### 4. Erőforráscsoport (Resource Group) létrehozása
1. A főoldalon vagy a keresőben válaszd a **Erőforráscsoportok** menüpontot.
2. Kattints a **+ Létrehozás** gombra.
3. Válaszd ki az előfizetésedet (*Előfizetés*).
4. **Erőforráscsoport neve:** Adj meg egy nevet (pl. `elsofeladat`).
5. **Régió:** Válaszd például: `(Europe Sweden Central`.
6. Kattints a **Felülvizsgálat + létrehozás**, majd a **Létrehozás** gombra.

### 5. Tárfiók (Storage Account) és Tároló (Container) létrehozása
1. Keresd meg a **Tárfiókok** szolgáltatást, majd kattints a **+ Létrehozás** gombra.
2. **Erőforráscsoport** Válaszd ki az előbb létrehozott `elsofeladat` csoportot.
3. **Tárfiók neve:** Adj meg egy egyedi, kisbetűs nevet (pl. `elsotarhely2026`).
4. Kattints az **Áttekintés + létrehozás**, majd a **Létrehozás** gombra. Várj, amíg az erőforrás elkészül.
5. Menj a létrehozott tárfiókba, és a bal oldali menüben keresd meg a **Adat tárolás** > **Tárolók** opciót.
6. Kattints a **+ Tároló hozzáadása** gombra, névnek add meg: `tesztkontener`, majd kattints a **Létrehozás** gombra.


### 6. Fájlok feltöltése a tárolóba
1. Kattints a frissen létrehozott `tesztkontener` nevű tárolóra.
2. Felül kattints az **Feltöltés** gombra.
3. Válaszd ki bármilyen kis méretű teszt fájlt (pl. egy `dokumentum.pdf`-et) a számítógépedről.
4. Kattints az **Feltöltés** gombra a feltöltéshez.

### 7. Felhasználó hozzáadása az erőforráscsoporthoz Olvasói (Reader) jogosultsággal
1. Navigálj vissza az `elsofeladat` nevű erőforráscsoporthoz.
2. A bal oldali menüben kattints az **Hozzáférés vezérlés (IAM)** menüpontra.
3. Kattints a **+ Hozzáadás** > **Szerepkör hozzárendelés hozzáadása** opcióra.
4. A **Szerepkörök** listából válaszd ki a **Olvasó** szerepkört, majd kattints a *Tovább* gombra.
5. A *Tagok* fülnél kattints a **+ Tagok kiválasztása** gombra.
6. A jobb oldali sávban keresd ki a korábban létrehozott felhasználót (`Teszt Elek`), kattints rá, majd nyomd meg a *Kiválasztás* gombot.
7. Kattints a ** Ellenőrzés és hozzárendelés** gombra kétszer a mentéshez.

---


## 🧪 Tesztelési fázis (A Felhasználó nézete)

### 1. Belépés a felhasználóval az Azure Portalra
1. Nyiss egy **Privát / Inkognitó** böngészőablakot (hogy az admin fiókodból ne jelentkezz ki).
2. Menj a [https://azure.com](https://azure.com) oldalra.
3. Jelentkezz be a létrehozott felhasználó adataival (pl. `tesztuser1234@://onmicrosoft.com`).
4. A rendszer kérni fogja az ideiglenes jelszót, majd kötelezően meg kell adnod egy új, saját jelszót.

### 2. Erőforráscsoport és tároló megnyitása, fájlok megtekintése
1. A felhasználó fiókjában menj a **Erőforráscsoportok** menüpontba.
2. Nyisd meg az `elsofeladat` csoportot. 
3. Kattints a listában szereplő tárfiókra 'elsotarhely2026', majd azon belül a **Adattárolás** > **tesztkontener** opcióra.
4. Ellenőrizd, hogy a felhasználó látja a korábban feltöltött fájlt (pl. `dokumentum.pdf`).


### 3. Próbálkozás új erőforrás létrehozására (Jogosultság megtagadása)
1. Lépj vissza az `elsofeladat` erőforráscsoport kezdőlapjára a felhasználóval.
2. Kattints a **+ Létrehozás** gombra.
3. Próbálj meg létrehozni egy tetszőleges erőforrást (például egy új *Virtuális gépet* vagy *Tárfiókot*).
4. Az Azure a folyamat során (vagy a legvégén a Validation fázisban) felül egy piros bannerben vagy hibaüzenetben jelzi, hogy nincs jogosultságod a művelet elvégzésére (`Az érvényesítés nem sikerült` / `XY ügyfél nem jogosult ZZ művelet végrehajtására`).
