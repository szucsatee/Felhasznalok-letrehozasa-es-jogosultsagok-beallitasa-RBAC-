# 👥 Felhasználó létrehozása és jogosultságok beállítása (RBAC)


## 🛠️ Lépések:

### 1. Azure Portalon való belépés
1. Nyiss meg egy böngészőt, és menj a [https://azure.microsoft.com](https://azure.microsoft.com/hu-hu) oldalra.
2. Jelentkezz be a fiókoddal.

### 2. Microsoft Entra ID megnyitása
1. A felső keresősávba írd be: `Microsoft Entra ID` (korábban Azure Active Directory volt).
2. Kattints rá a találatok között.

### 3. Felhasználó létrehozása és Jelszó beállítása
1. A bal oldali menüben keress és kattints a **`Kezelés`** > **`Felhasználók`** lehetőségre.
2. Felül kattints a **`Új felhasználó`** > **`Új felhasználó létrehozása`** gombra.
3. Töltsd ki az az **`Alapadatok`** fület:
   * **`Egyszerű felhasználónév`:** `tesztuser` (a legördülő menüből válaszd ki a domain neved).
   * **`Megjelenítendő név`:** `Teszt Elek`
4. A **`Jelszó`** résznél válaszd az *`Jelszó automatikus létrehozása`* lehetőséget vagy add meg saját jelszavad. 
5. ⚠️ **Fontos:** Másold ki a generált jelszót, mert az első belépésnél szükséged lesz rá!
6. Kattints a **`Áttekintés és létrehozás`**, majd a **`Létrehozás`** gombra.
7. Vagy töltsd ki akár a **`Tulajdonságok`** vagy a **`Hozzárendelések`** fület, aztán kattints a**`Létrehozás`** gombra.

### 4. Erőforráscsoport (Resource Group) létrehozása
1. A főoldalon vagy a keresőben válaszd a **`Erőforráscsoportok`** menüpontot, keress rá hasonló módon mint a 3. pontban.
2. Kattints a **`+ Létrehozás`** gombra.
3. Válaszd ki az előfizetésed *`Előfizetés`*.
4. **`Erőforráscsoport neve`:** Adj meg egy neked tetsző nevet (pl. `elsofeladat`).
5. **Régió:** Válaszd például: `Europe Sweden Central`.
6. Kattints a **`Felülvizsgálat + létrehozás`**, majd a **`Létrehozás`** gombra.

### 5. Tárfiók (Storage Account) és Tároló (Container) létrehozása
1. Keresd meg a **`Tárfiókok`** szolgáltatást, majd kattints a **`+ Létrehozás`** gombra.
2. Válaszd ki a megfelelő `Előfizetés`-t
3. **`Erőforráscsoport`**: Válaszd ki az előbb létrehozott `elsofeladat` erőforráscsoportot.
4. **`Tárfiók neve`:** Adj meg egy egyedi, kisbetűs nevet (pl. `elsotarhely2026`).
5. Kattints az **`Áttekintés + létrehozás`**, majd a **`Létrehozás`** gombra. Várj, amíg az erőforrás elkészül.
6. Menj a létrehozott tárfiókba, és a bal oldali menüben keresd meg a **`Adat tárolás`** > **`Tárolók`** opciót.
7. Kattints a **`+ Tároló hozzáadása`** gombra, névnek add meg: `tesztkontener`, majd kattints a **`Létrehozás`** gombra.


### 6. Fájlok feltöltése a tárolóba
1. Kattints a frissen létrehozott `tesztkontener` nevű tárolóra.
2. Felül kattints az **`Feltöltés`** gombra.
3. Válaszd ki bármilyen kis méretű teszt fájlt (pl. egy `dokumentum.pdf`-et) a számítógépedről a `Fájlok keresése tallózással` lehetőséggel.
4. Vagy egérrel fogd meg a fájlt és húzd a dobozba.
5. Kattints az **`Feltöltés`** gombra a feltöltéshez.

### 7. Felhasználó hozzáadása az erőforráscsoporthoz Olvasói (Reader) jogosultsággal
1. Navigálj vissza az `elsofeladat` nevű erőforráscsoporthoz.
2. A bal oldali menüben keresdd éskattints az **`Hozzáférés vezérlés (IAM)`** menüpontra.
3. Kattints a **`+ Hozzáadás`** > **`Szerepkör hozzárendelés hozzáadása`** opcióra.
4. A **`Szerepkörök`** listából válaszd ki a **`Olvasó`** szerepkört, majd kattints a *`Tovább`* gombra.
5. A *`Tagok`* fülnél kattints a **`+ Tagok kiválasztása`** gombra.
6. A jobb oldali sávban keresd ki a korábban létrehozott felhasználót (`Teszt Elek`), kattints rá, majd nyomd meg a *`Kiválasztás`* gombot.
7. Kattints a **` Ellenőrzés és hozzárendelés `** gombra kétszer a mentéshez.

---


## 🧪 Tesztelési fázis (A Felhasználó nézete)

### 1. Belépés a felhasználóval az Azure Portalra
1. Nyiss egy új **Privát / Inkognitó** böngészőablakot (hogy az admin fiókodból ne jelentkezz ki).
2. Menj a [https://azure.microsoft.com](https://azure.microsoft.com/hu-hu) oldalra.
3. Jelentkezz be a létrehozott felhasználó adataival (pl. `tesztuser123!4@://onmicrosoft.com`).
4. A rendszer kérni fogja a korábban generált ideiglenes jelszót, majd kötelezően meg kell adnnod egy új, saját jelszót.

### 2. Erőforráscsoport és tároló megnyitása, fájlok megtekintése
1. A felhasználó fiókjában menj a **`Erőforráscsoportok`** menüpontba.
2. Nyisd meg az `elsofeladat` csoportot. 
3. Kattints a listában szereplő tárfiókra 'elsotarhely2026', majd azon belül a **`Adattárolás`** > **`tesztkontener`** opcióra.
4. Ellenőrizd, hogy a felhasználó látja a korábban feltöltött fájlt (pl. `dokumentum.pdf`).


### 3. Próbálkozás új erőforrás létrehozására (Jogosultság megtagadása)
1. Lépj vissza az `elsofeladat` erőforráscsoport kezdőlapjára a felhasználóval.
2. Kattints a **`+ Létrehozás`** gombra.
3. Próbálj meg létrehozni egy tetszőleges erőforrást (például egy új *Virtuális gépet* vagy *Tárfiókot*).
4. Az Azure a folyamat során (vagy a legvégén a Validation fázisban) felül egy piros bannerben vagy hibaüzenetben jelzi, hogy nincs jogosultságod a művelet elvégzésére (`Az érvényesítés nem sikerült` / `XY ügyfél nem jogosult ZZ művelet végrehajtására`).
