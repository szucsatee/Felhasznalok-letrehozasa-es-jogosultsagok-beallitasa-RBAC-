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

---


### 6. Fájlok feltöltése a tárolóba
1. Kattints a frissen létrehozott `teszt-kontener` nevű tárolóra.
2. Felül kattints az **Upload** gombra.
3. Válaszd ki bármilyen kis méretű teszt fájlt (pl. egy `dokumentum.txt`-t) a számítógépedről.
4. Kattints az **Upload** gombra a feltöltéshez.

### 7. Felhasználó hozzáadása az erőforráscsoporthoz Olvasói (Reader) jogosultsággal
1. Navigálj vissza az `rg-rbac-feladat` nevű erőforráscsoporthoz.
2. A bal oldali menüben kattints az **Access control (IAM)** menüpontra.
3. Kattints a **+ Add** > **Add role assignment** opcióra.
4. A **Role** (Szerepkörök) listából válaszd ki a **Reader** (Olvasó) szerepkört, majd kattints a *Next* gombra.
5. A *Members* fülnél kattints a **+ Select members** gombra.
6. A jobb oldali sávban keresd ki a korábban létrehozott felhasználót (`Teszt Elek`), kattints rá, majd nyomd meg a *Select* gombot.
7. Kattints a **Review + assign** gombra kétszer a mentéshez.

---

## 🧪 Tesztelési fázis (A Felhasználó nézete)

### 1. Belépés a felhasználóval az Azure Portalra
1. Nyiss egy **Privát / Incognito** böngészőablakot (hogy az admin fiókodból ne jelentkezz ki).
2. Menj a [https://azure.com](https://azure.com) oldalra.
3. Jelentkezz be a létrehozott felhasználó adataival (pl. `tesztuser@://onmicrosoft.com`).
4. A rendszer kérni fogja az ideiglenes jelszót, majd kötelezően meg kell adnod egy új, saját jelszót.

### 2. Erőforráscsoport és tároló megnyitása, fájlok megtekintése
1. A felhasználó fiókjában menj a **Resource groups** menüpontba.
2. Nyisd meg az `rg-rbac-feladat` csoportot. *(Itt készítheted az első képernyőképet a sikeres belépésről és a tartalomról).*
3. Kattints a listában szereplő tárfiókra, majd azon belül a **Containers** > **teszt-kontener** opcióra.
4. Ellenőrizd, hogy a felhasználó látja a korábban feltöltött fájlt (pl. `dokumentum.txt`).

### 3. Próbálkozás új erőforrás létrehozására (Jogosultság megtagadása)
1. Lépj vissza az `rg-rbac-feladat` erőforráscsoport kezdőlapjára a felhasználóval.
2. Kattints a **+ Create** gombra.
3. Próbálj meg létrehozni egy tetszőleges erőforrást (például egy új *Virtuális gépet* vagy *Tárfiókot*).
4. Az Azure a folyamat során (vagy a legvégén a Validation fázisban) felül egy piros bannerben vagy hibaüzenetben jelzi, hogy nincs jogosultságod a művelet elvégzésére (`Authorization failed` / `You do not have permissions`). *(Itt készítsd el a hibát igazoló képernyőképet).*

---

## 🌟 Opcionális feladat megoldása: Céges struktúra felépítése csoportokkal

Ha a jogosultságokat vállalati szinten, csoport alapon szeretnéd kezelni:

1. **Csoport létrehozása:** 
   * Rendszergazdaként menj a **Microsoft Entra ID** > **Groups** > **All groups** > **New group** menüpontba.
   * **Group type:** Security
   * **Group name:** `GRP-Olvasok-Staff`
   * Kattints a **Create** gombra.
2. **Tag hozzáadása:** Nyisd meg a létrehozott `GRP-Olvasok-Staff` csoportot, menj a **Members** > **+ Add members** részre, és add hozzá `Teszt Elek`-et.
3. **Csoport szintű RBAC beállítás:** 
   * Menj az erőforráscsoportod **Access control (IAM)** fülére.
   * Az *Add role assignment* résznél válaszd a **Reader** szerepkört.
   * A *Members* fülön a felhasználó helyett most a **GRP-Olvasok-Staff** csoportot keresd ki és jelöld ki.
   * Mentés után a csoport összes tagja (így a tesztfelhasználó is) automatikusan megkapja az Olvasó jogot.
