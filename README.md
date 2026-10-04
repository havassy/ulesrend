# Ülésrend szervező

Böngészőben futó, egyetlen HTML-fájlból álló alkalmazás tanároknak. Az osztály meglévő, Excelben tárolt ülésrendjéből új beosztást készít, figyelembe véve a hiányzókat. Az eredmény letölthető és kivetíthető. Opcionálisan két, tetszőleges szempont szerint megadott csoport tagjait is összekeveri, hogy minél több vegyes pár és trió jöjjön létre.

## Mit csinál a program?

1. **Excel-fájl fel- és letöltése** – az eredeti ülésrend húzással vagy tallózással tölthető fel `.xlsx` vagy `.xls` formátumban. A program kipróbálható előre kitöltött **próba ülésrenddel** is. A **Minta Excel letöltése** gomb a megfelelő cellastruktúrát és összekapcsolt munkalapokat tartalmazó, helyettesítő nevekkel kitöltött sablont ad. Feltöltéskor a program ellenőrzi az azonos nevek ismétlődését, és hibaüzenettel jelzi a duplikátumokat.
2. **Hiányzók jelölése** – a tanulók nevére kattintva megadható, ki hiányzik. A jelölések a **Hiányzók visszaállítása** gombbal törölhetők. A program mutatja a jelenlévők, a hiányzók és az összes tanuló számát.
3. **Új ülésrend generálása** – minden generáláskor az összes jelenlévő tanulót újrakeveri. A rögzített, **35 férőhelyes** terem elrendezését követi: öt sorban két kétszemélyes és egy háromszemélyes pad található, közöttük folyosókkal. A páros elhelyezést részesíti előnyben; páratlan létszámnál vagy a férőhelyek kihasználásához szükség esetén triókat alakít ki. A terem kapacitásán belül minden jelenlévő helyet kap.
4. **Opcionális csoportkeverés** – az Excelben megadott két csoport alapján a lehető legtöbb vegyes párt és triót alakítja ki. Az összeállítás a megadott szemponton belül véletlenszerű marad.
5. **Mentés és újragenerálás** – az új ülésrend dátumot tartalmazó nevű Excel-fájlba menthető. Ha vannak csoportjelölések, a mentés ezeket is megőrzi a benne szereplő tanulókhoz. A hiányzók az új ülésrendben is átjelölhetők; az elhelyezés módosításához ezután újra kell generálni az ülésrendet.

## Az Excel-minta kitöltése

1. Töltsd le a sablont a **Minta Excel letöltése** gombbal.
2. Az **Ülésrend** munkalapon cseréld ki a helyettesítő neveket a tanulók nevére, a megfelelő ülőhelyeken. A nem használt helyekről töröld a helyettesítő neveket. A padok és folyosók cellastruktúráját tartsd meg.
3. A **Csoportok** munkalapon a nevek automatikusan megjelennek: a **Név** oszlop képletekkel kapcsolódik az ülésrendhez, ezért nem kell újra beírni a neveket. Az üres ülőhelyekhez itt is üres név tartozik.
4. Ha szeretnél csoportkeverést, töltsd ki a nevek melletti **Csoport** oszlopot. Egyébként hagyd üresen.
5. Mentsd el az Excel-fájlt, töltsd fel a programba, jelöld a hiányzókat, majd generáld az új ülésrendet.

A neveket először az **Ülésrend** lapon véglegesítsd, és utána add meg a csoportjelöléseket. Ha később átírod vagy átrendezed a neveket, ellenőrizd a mellettük álló jelöléseket is: a nevek képletei az ülőhelyeket követik, a kézzel beírt jelölések viszont a saját cellájukban maradnak.

## Csoportkeverés tetszőleges szempont alapján

A **Csoportok** munkalapon kétféle jelölés adható meg, például **A** és **B**. Ezek jelentését a tanár határozza meg: jelölhetnek például különböző feladatváltozatokon dolgozó tanulókat vagy kétféle előzetes tapasztalatot. A program a jelölésekhez nem rendel előre meghatározott jelentést.

| Név | Csoport |
| --- | --- |
| Tanuló neve 1 | A |
| Tanuló neve 2 | B |
| Tanuló neve 3 | A |

- A program a kialakított párok és triók közül a lehető legtöbbet állítja össze **mindkét csoport tagjaiból**.
- Ha a csoportok létszáma eltér, az elérhető legnagyobb mértékű keverésre törekszik; minden jelenlévőt elhelyez akkor is, ha nem lehet minden pad vegyes.
- A jelölés nélkül hagyott tanulók is részt vesznek a beosztásban. A program nem következtet a csoportjukra a nevükből.
- Ha nincs **Csoportok** munkalap, vagy nincsenek kitöltött jelölések, a szokásos véletlenszerű keverés működik. A korábbi, egy munkalapos Excel-fájlok továbbra is használhatók.
- A csoportjelölések az ülésrend megjelenítésében és a vetítésben nem látszanak.

## Kivetítés (projektoros mód)

Az eredeti és az új ülésrend egyaránt megjeleníthető a böngészőablakot kitöltő, kivetítésre optimalizált nézetben. Az eredeti ülésrend vetítésekor a hiányzó tanulók halványítva, piros kiemeléssel látszanak. Az új beosztás az utolsó generáláskor jelenlévőnek jelölt tanulókat tartalmazza.

A **Tanár nézet / Diák nézet** gombbal vagy az `M` billentyűvel a beosztás tükrözhető, hogy a megfelelő nézőpontból mutassa a terem elrendezését. A vetítés az `Esc` billentyűvel vagy a **Bezárás** gombbal zárható be.

## Hogyan működik? (technikai háttér)

- Egyetlen HTML-fájl tartalmazza a felületet, a stílusokat és a programkódot. Az `index.html` böngészőben megnyitható, telepítésre vagy külön szerverre nincs szükség.
- Az Excel-fájlok beolvasásához és mentéséhez a **SheetJS (xlsx.js)** könyvtárat használja, amely CDN-ről töltődik be. A könyvtár betöltéséhez internetkapcsolat szükséges.
- A tanulói adatok feldolgozása helyben, a felhasználó böngészőjében történik; az alkalmazás nem küldi el őket szerverre.

---

Készítette: Havassy András
