# 👥 Felhasználó létrehozása és jogosultságok beállítása (RBAC)


## 🛠️ Lépések:

### 1. Azure Portalon való belépés
1. Nyiss meg egy böngészőt, és menj a [https://azure.microsoft.com](https://azure.microsoft.com/hu-hu) oldalra.
2. Jelentkezz be a fiókoddal.

### 2. Microsoft Entra ID megnyitása
1. A felső keresősávba írd be: `Microsoft Entra ID` (korábban Azure Active Directory volt).
2. Kattints rá a találatok között.

   <img width="1589" height="333" alt="image" src="https://github.com/user-attachments/assets/3aeeccb8-6b1c-485b-a16f-7fccc49ea16b" />


### 3. Felhasználó létrehozása és Jelszó beállítása
1. A bal oldali menüben keress és kattints a **`Kezelés`** > **`Felhasználók`** lehetőségre.
<img width="321" height="705" alt="image" src="https://github.com/user-attachments/assets/58675586-c483-4256-937f-3b0fdb60c0c8" />

3. Felül kattints a **`Új felhasználó`** > **`Új felhasználó létrehozása`** gombra. 
<img width="684" height="295" alt="image" src="https://github.com/user-attachments/assets/78f633df-e683-45ad-8f53-d05cc6caf740" />

4. Töltsd ki az az **`Alapadatok`** fület:
   * **`Egyszerű felhasználónév`:** `tesztuser` (a legördülő menüből válaszd ki a domain neved).
   * **`Megjelenítendő név`:** `Teszt Elek`
5. A **`Jelszó`** résznél válaszd az *`Jelszó automatikus létrehozása`* lehetőséget vagy add meg saját jelszavad. 
6. ⚠️ **Fontos:** Másold ki a generált jelszót, mert az első belépésnél szükséged lesz rá!
7. Kattints a **`Áttekintés és létrehozás`**, majd a **`Létrehozás`** gombra.
8. Vagy töltsd ki akár a **`Tulajdonságok`** vagy a **`Hozzárendelések`** fület, aztán kattints a**`Létrehozás`** gombra.
<img width="1514" height="799" alt="image" src="https://github.com/user-attachments/assets/917684c1-8604-4a28-8988-5396cd5f97a9" />


### 4. Erőforráscsoport (Resource Group) létrehozása
1. A főoldalon vagy a keresőben válaszd a **`Erőforráscsoportok`** menüpontot, keress rá hasonló módon mint a 3. pontban.
<img width="1522" height="374" alt="image" src="https://github.com/user-attachments/assets/7bf63d45-71a6-4319-8a08-aa6f484362b1" />

2. Kattints a **`+ Létrehozás`** gombra.
3. Válaszd ki az előfizetésed *`Előfizetés`*.
4. **`Erőforráscsoport neve`:** Adj meg egy neked tetsző nevet (pl. `elsofeladat`).
5. **Régió:** Válaszd például: `Europe Sweden Central`.
6. Kattints a **`Felülvizsgálat + létrehozás`**, majd a **`Létrehozás`** gombra.
<img width="1575" height="872" alt="image" src="https://github.com/user-attachments/assets/94ae337c-44f0-4312-b2a2-1ca23fb21cde" />


### 5. Tárfiók (Storage Account) és Tároló (Container) létrehozása
1. Keresd meg a **`Tárfiókok`** szolgáltatást, majd kattints a **`+ Létrehozás`** gombra. 
<img width="1536" height="373" alt="image" src="https://github.com/user-attachments/assets/4db057fd-743c-4c5d-a17f-a9397723fa6c" />

2. Válaszd ki a megfelelő `Előfizetés`-t
3. **`Erőforráscsoport`**: Válaszd ki az előbb létrehozott `elsofeladat` erőforráscsoportot.
4. **`Tárfiók neve`:** Adj meg egy egyedi, kisbetűs nevet (pl. `elsotarhely2026`).
5. Kattints az **`Áttekintés + létrehozás`**, majd a **`Létrehozás`** gombra. Várj, amíg az erőforrás elkészül. 

<img width="1554" height="874" alt="image" src="https://github.com/user-attachments/assets/6d372e02-2567-41b4-a83c-4e27034c6fe0" />


6. Menj a létrehozott tárfiókba, és a bal oldali menüben keresd meg a **`Adat tárolás`** > **`Tárolók`** opciót.
7. Kattints a **`+ Tároló hozzáadása`** gombra, névnek add meg: `tesztkontener`, majd kattints a **`Létrehozás`** gombra.

<img width="1913" height="820" alt="image" src="https://github.com/user-attachments/assets/176bf122-e20d-47b5-9479-f1876c922530" />



### 6. Fájlok feltöltése a tárolóba
1. Kattints a frissen létrehozott `tesztkontener` nevű tárolóra.
2. Felül kattints az **`Feltöltés`** gombra.
3. Válaszd ki bármilyen kis méretű teszt fájlt (pl. egy `dokumentum.pdf`-et) a számítógépedről a `Fájlok keresése tallózással` lehetőséggel.
4. Vagy egérrel fogd meg a fájlt és húzd a dobozba.
5. Kattints az **`Feltöltés`** gombra a feltöltéshez. 
<img width="1908" height="824" alt="image" src="https://github.com/user-attachments/assets/2dabc3e8-f25b-498e-9b89-d6ac18dfce94" />



### 7. Felhasználó hozzáadása az erőforráscsoporthoz Olvasói (Reader) jogosultsággal
1. Navigálj vissza az `elsofeladat` nevű erőforráscsoporthoz.
2. A bal oldali menüben keresdd éskattints az **`Hozzáférés vezérlés (IAM)`** menüpontra.
3. Kattints a **`+ Hozzáadás`** > **`Szerepkör hozzárendelés hozzáadása`** opcióra. 
<img width="1912" height="411" alt="image" src="https://github.com/user-attachments/assets/2001f051-8517-48b2-8715-4c5aedf6e00d" />


4. A **`Szerepkörök`** listából válaszd ki a **`Olvasó`** szerepkört, majd kattints a *`Tovább`* gombra. 
<img width="1892" height="658" alt="image" src="https://github.com/user-attachments/assets/f1b6b36d-9aba-48a4-9022-161df9f4d021" />


5. A *`Tagok`* fülnél kattints a **`+ Tagok kiválasztása`** gombra.
6. A jobb oldali sávban keresd ki a korábban létrehozott felhasználót (`Teszt Elek`), kattints rá, majd nyomd meg a *`Kiválasztás`* gombot. 
<img width="1899" height="815" alt="image" src="https://github.com/user-attachments/assets/c7c8e032-b338-47bd-b9cb-a0ef7ced7f0b" />


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
