# 👥 Feladat 1 - Felhasználó létrehozása és jogosultságok beállítása (RBAC)

Ez a leírás bemutatja, hogyan kell új felhasználót létrehozni az Azure Entra ID-ban (korábban Azure Active Directory), hogyan kell RBAC (Role-Based Access Control) alapú jogosultságokat kiosztani, és hogyan lehet tesztelni a korlátozott "Olvasó" (Reader) szerepkört.

---

## 📋 Feladat lépései és ellenőrző lista

### 🛠️ 1. Rendszergazdai feladatok (Infrastruktúra kiépítése)
- [ ] **Azure Portalon való belépés** (Globális vagy Felhasználói adminisztrátorként)
- [ ] **Microsoft Entra ID megnyitása** a szolgáltatások közül
- [ ] **Új felhasználó létrehozása** (pl. `tesztuser@://onmicrosoft.com`)
- [ ] **Kezeletlen/Ideiglenes jelszó beállítása** és másolása
- [ ] **Erőforráscsoport (Resource Group) létrehozása** (pl. `rg-rbac-teszt`)
- [ ] **Tárfiók (Storage Account) létrehozása** az adott erőforráscsoportban
- [ ] **Tároló (Container) létrehozása** a tárfiókon belül
- [ ] **Teszt fájlok feltöltése** a létrehozott tárolóba
- [ ] **Jogosultság kiosztása:** A létrehozott felhasználó hozzáadása az erőforráscsoporthoz **Olvasó (Reader)** szerepkörrel (Access control (IAM) -> Add role assignment)

### 🧪 2. Felhasználói tesztelés (Korlátozott jogok ellenőrzése)
- [ ] **Belépés az új felhasználóval** egy privát (Incognito) böngészőablakban az Azure Portalra (első belépéskor jelszómódosítás szükséges)
- [ ] **Az erőforráscsoport megnyitása** a felhasználó fiókjával
- [ ] **A tárfiók és a tároló megnyitása**
- [ ] **A feltöltött fájlok megtekintése** (Olvasási jog ellenőrzése)
- [ ] **Próbálkozás új erőforrás létrehozására** az erőforráscsoportban (Jogosultság megtagadásának tesztelése)

---

## 📸 Szükséges képernyőképek (Dokumentáció)

A feladat sikeres teljesítéséhez az alábbi képernyőképeket kell csatolni a megfelelő helyre:

### 1. Sikeres belépés az új felhasználóval
*A képernyőképen látszódnia kell a jobb felső sarokban az új felhasználó nevének.*
![Sikeres belépés](https://placeholder.com)

### 2. Az erőforráscsoport tartalma a felhasználó nézetéből
*A képernyőképen látszódnia kell, hogy a felhasználó látja a tárfiókot és az erőforráscsoport elemeit.*
![Erőforráscsoport megtekintése](https://placeholder.com)

### 3. Sikertelen erőforrás-létrehozási kísérlet
*A képernyőképen jól láthatóan meg kell jelennie az Azure hibaüzenetének (Authorization failed / No permissions), amikor a felhasználó új erőforrást próbál létrehozni.*
![Megtagadott jogosultság hibaüzenet](https://placeholder.com)

---

## 🌟 Opcionális Plusz Feladat: Céges struktúra leképezése

Ha szeretnéd magasabb szintre emelni a feladatot, valósítsd meg a jogosultságkezelést csoportok (Groups) segítségével:

1. **Csoportok létrehozása:** Hozz létre egy `🔥 IT-Admins` és egy `👁️ Read-Only-Staff` biztonsági csoportot (Security Group) az Entra ID-ban.
2. **Tagok hozzáadása:** A korábban létrehozott felhasználót ne közvetlenül az erőforráshoz rendeld, hanem add hozzá a `Read-Only-Staff` csoporthoz.
3. **Csoport szintű RBAC:** Az erőforráscsoport *Access Control (IAM)* fülén a **Csoportnak** adj *Olvasó (Reader)* jogot, ne a konkrét felhasználónak.

> 💡 **Best Practice Tipp:** Éles vállalati környezetben soha nem adunk közvetlenül felhasználónak jogot, mindig csoportok szintjén kezeljük a jogosultságokat!
