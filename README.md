# Ülésrend szervező

Böngészőben futó, egyetlen HTML-fájlból álló alkalmazás tanároknak: az osztály meglévő ülésrendjéből (Excel-fájlból) új, véletlenszerű ülésrendet készít, figyelembe véve a hiányzókat, majd letölthető vagy kivetíthető.

## Mit csinál a program?

1. **Excel fájl fel- és letöltése** – az eredeti ülésrend (tanulónevek a padok szerinti cellákban) húzással vagy tallózással tölthető fel `.xlsx`/`.xls` formátumban. Kipróbálható előre kitöltött **próba ülésrenddel** is, és letölthető egy üres **minta Excel sablon**, amely a program által elvárt cellastruktúrát tartalmazza. Feltöltéskor a program ellenőrzi, hogy nincs-e azonos név duplikálva, és hibaüzenettel jelzi, ha van.
2. **Hiányzók jelölése** – az eredeti ülésrend padjaira kattintva jelölhető, ki van jelen és ki hiányzik ("Jelen van" / "Hiányzik" / "Üres hely"), a jelölés egy gombbal visszaállítható. Az eredeti beosztás kivetíthető is (lásd lejjebb).
3. **Új ülésrend generálása** – a jelenlévő tanulókból véletlenszerűen új ülésrendet állít össze, a terem rögzített pad-elrendezését (páros és hármas padok, közöttük résekkel/folyosókkal) figyelembe véve. Az új beosztás Excel-fájlba menthető (a fájlnév a mai dátumot is tartalmazza), vagy egérrel a hiányzók itt is átjelölhetők és újragenerálhatók.

## Kivetítés (projektoros mód)

Az eredeti vagy az új ülésrend teljes képernyős, kivetítésre optimalizált nézetben is megjeleníthető. A hiányzó tanulók halványítva, piros kiemeléssel látszanak. A **"Tanár nézet" / "Diák nézet"** gombbal (vagy az `M` billentyűvel) a beosztás tükrözhető, mivel a kivetített kép a tanterem elrendezéséhez képest fordított oldalról nézve jelenik meg. A kivetítés az `Esc` billentyűvel zárható be.

## Hogyan működik? (technikai háttér)

- Kliensoldali, önmagában is működő, egyetlen HTML+CSS+JS fájl, nincs szükség szerverre vagy telepítésre.
- Az Excel fájlok beolvasásához és mentéséhez a **SheetJS (xlsx.js)** könyvtárat használja CDN-ről, ezért ehhez internetkapcsolat szükséges.
- A tanulói adatok csak a böngészőben, a felhasználó gépén kerülnek feldolgozásra, nem kerülnek fel semmilyen szerverre.

---

Készítette: Havassy András
