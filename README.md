# Ülésrend szervező

Böngészőben futó, **egyetlen, önálló HTML-fájlból álló**, tanároknak készült alkalmazás. Az osztály Excelben tárolt eredeti ülésrendjéből új beosztást készít a hiányzók figyelembevételével. Az eredmény Excel-fájlba menthető és kivetíthető. Opcionálisan két, a tanár által megadott csoport tagjait is keveri, hogy lehetőleg minél több vegyes pár és trió alakuljon ki.

**Az offline változat internetkapcsolat nélkül is használható.** A névlistát és a csoportjelöléseket a böngésző helyben dolgozza fel; a program nem küldi el őket szerverre.

## Mit csinál a program?

1. **Excel-fájl betöltése és letöltése** – Az eredeti ülésrend húzással vagy tallózással tölthető be. Az ajánlott formátum a **`.xlsx`**; a régebbi **`.xls`** állományok támogatása korlátozott, ezért azoknál célszerű előbb `.xlsx` formátumban menteni a munkafüzetet. A **Próba ülésrend** kitalált nevekkel tesztelhető. A **Minta Excel letöltése** gomb megfelelő cellastruktúrájú, helyettesítő neveket és összekapcsolt munkalapokat tartalmazó sablont készít. A program az azonos nevek ismétlődését jelzi, és a hibás névsort nem dolgozza fel.
2. **Hiányzók jelölése** – A nevekre kattintva megadható, ki hiányzik; a **Hiányzók visszaállítása** gomb minden ilyen jelölést töröl. A felület a jelenlévők, a hiányzók és az összes tanuló számát is mutatja.
3. **Új ülésrend generálása** – Minden generáláskor újrarendezi a jelenlévőket. A rögzített, **35 férőhelyes** teremben öt sor van; soronként két kétszemélyes és egy háromszemélyes pad, közöttük folyosókkal. Elsősorban párokat hoz létre, és csak szükség esetén használ triókat (például páratlan létszámnál vagy 30 fő fölött). A terem kapacitásán belül minden jelenlévő helyet kap.
4. **Az eredeti padtársak lehetőség szerinti szétválasztása** – Az új beosztás készítésekor a program igyekszik elkerülni, hogy az eredetileg egy padban ülők újra ugyanabba a padba kerüljenek. Ez **törekvés, nem minden helyzetben teljesíthető garancia**. A program a csoportkeverés bekapcsolásakor annak szempontjait is megőrzi.
5. **Opcionális csoportkeverés** – Az Excelben megadott két csoport alapján előnyben részesíti a vegyes párokat és triókat. A csoportkeverés külön kapcsolóval engedélyezhető; az új beállítás a **következő generáláskor** lép életbe. A beosztás az adott feltételek között véletlenszerű elemeket is tartalmaz.
6. **Mentés és újragenerálás** – Az új ülésrend dátumot tartalmazó fájlnévvel, **`.xlsx`** formátumban tölthető le. Ha vannak csoportjelölések, a mentett ülésrendben szereplő tanulók jelölései is megmaradnak. Az új ülésrendben szintén módosíthatók a hiányzásjelölések; a helyek újraosztásához ezután az **Újra generálás** gombot kell használni.

## Az Excel-minta kitöltése

1. Töltsd le a sablont a **Minta Excel letöltése** gombbal.
2. Az **Ülésrend** munkalapon cseréld ki a helyettesítő neveket a tanulók neveire, a megfelelő ülőhelyeken. A nem használt ülőhelyekről töröld a helyettesítő neveket. A padok és folyosók cellastruktúráját tartsd meg.
3. A **Csoportok** munkalap **Név** oszlopa képletekkel kapcsolódik az ülésrend megfelelő celláihoz, ezért a neveket nem kell kétszer beírni. Az üres ülőhelyekhez itt is üres név tartozik.
4. Ha szeretnél csoportkeverést, töltsd ki a **Csoport** oszlopot, legfeljebb kétféle jelöléssel. Ha nincs rá szükség, hagyd üresen.
5. Mentsd el az Excel-munkafüzetet `.xlsx` formátumban, töltsd be a programba, jelöld a hiányzókat, és generáld az új ülésrendet. Csoportkeveréshez kapcsold be a **Csoportok keverése** opciót.

**Fontos:** A neveket először az **Ülésrend** munkalapon véglegesítsd, és csak utána add meg a csoportjelöléseket. Ha később átírod vagy átrendezed a neveket, ellenőrizd a mellettük álló jelöléseket is: a névképletek az ülőhelyeket követik, a kézzel beírt csoportjelölések viszont a saját cellájukban maradnak.

A régi, **egyetlen munkalapot tartalmazó** Excel-fájlok is használhatók; a **Csoportok** munkalap nem kötelező. A program az ülésrendhez az első olyan munkalapot használja, amelynek neve nem `Csoportok`.

## Csoportkeverés tetszőleges szempont alapján

A **Csoportok** munkalapon legfeljebb kétféle jelölés használható, például **A** és **B**. Ezek jelentését a tanár határozza meg: elkülöníthetnek például különböző feladatváltozatokon dolgozó vagy eltérő előzetes tapasztalattal rendelkező tanulókat. A program a jelölésekből nem következtet semmilyen személyes tulajdonságra.

| **Név** | **Csoport** |
| --- | --- |
| Tanuló neve 1 | A |
| Tanuló neve 2 | B |
| Tanuló neve 3 | A |

- A beosztás lehetőleg minél több olyan padot alakít ki, amelyben **mindkét csoportból** ül tanuló. Ha több az egyik csoportba tartozó diák, nem biztos, hogy minden pad vegyes lehet.
- A csoporthoz nem rendelt tanulók is részt vesznek a beosztásban; a program nem következtet csoportjukra a nevükből.
- Ha nincsenek érvényes csoportjelölések, a csoportkeverés nem kapcsolható be. Ha a jelenlévők között csak egy megjelölt csoport szerepel, a szokásos keverés működik.
- A hibás vagy hiányos csoportadatokra a program visszajelzést ad; az ülésrend alapfunkciói ettől még használhatók.
- A csoportjelölések **nem jelennek meg** sem a fő ülésrendben, sem a vetítésben.

Az algoritmus először a vegyes padok kialakítására törekszik, majd – a csoportkeverés eredményének megőrzésével – lehetőség szerint csökkenti az eredeti padtársak ismételt együtt ülését. Ez optimalizálási törekvés, nem abszolút garancia.

## Kivetítés (projektoros mód)

Az eredeti és az új ülésrend egyaránt megjeleníthető a böngészőablakot kitöltő, kivetítésre optimalizált nézetben. Az eredeti ülésrend vetítésekor a hiányzók halványítva, piros kiemeléssel jelennek meg. Az új beosztás az **utolsó generáláskor** jelenlévőnek jelölt tanulókat tartalmazza. A később hiányzónak jelölt tanulók csak újragenerálás után kerülnek ki a kiosztásból.

A **Tanár nézet / Diák nézet** gombbal vagy az `M` billentyűvel átváltható a terem nézőpontja. A vetítés az `Esc` billentyűvel vagy a **Bezárás** gombbal zárható be.

## Indítás és működés internet nélkül

1. Mentsd el a teljes, offline HTML-fájlt a számítógépre (a GitHub-tárhelyen például `index.html` néven is szerepelhet).
2. Nyisd meg Chrome-ban vagy egy másik korszerű böngészőben – nincs szükség telepítésre vagy külön szerverre.
3. A fájlt **internetkapcsolat nélkül is megnyithatod**, majd használhatod az Excel-beolvasást, a generálást és a letöltést.

Ha a programot GitHub Pages-oldalként teszed közzé, a **HTML-oldal letöltéséhez** szükség van internetre, de a jelenlegi programkód a **tanulói névlistát nem továbbítja** a tárhelyszolgáltatónak. A teljesen offline használathoz nyisd meg a helyben elmentett HTML-fájlt.

## Adatkezelés és mentés

- A fájlbeolvasás, az ülésrend generálása, a csoportok kezelése és az Excel-fájl előállítása **a böngészőben, helyben történik**.
- A jelenlegi HTML-kód **nem tartalmaz névlista-feltöltést, külső adatküldést, telemetriát vagy külső JavaScript-betöltést**.
- **Nincs automatikus felhőmentés vagy tartós böngészős tárolás.** Az aktuális adatok a lap újratöltésekor vagy bezárásakor elveszhetnek; a megőrizni kívánt ülésrendet külön töltsd le és tárold megfelelően.
- A letöltött Excel-fájlok személyes adatokat tartalmazhatnak. Ezek kezelésénél, megosztásánál és a vetítésnél az iskola adatvédelmi szabályai irányadók.

A helyi feldolgozás csökkenti a külső adattovábbítás kockázatát, de **önmagában nem jelenti a teljes GDPR-megfelelőség automatikus igazolását**.

## Technikai háttér

- Az alkalmazás egyetlen HTML-fájlból áll: ebben található a felület, a stílus, az ülésrendkészítés és az Excel-kezelés kódja.
- Az offline változat **nem használ CDN-ről betöltött SheetJS-t**. Az `.xlsx`-fájlok kezelését beépített, a program igényeire szabott olvasó–író kód és a helyben beágyazott **JSZip 3.10.1** könyvtár végzi. A JSZip licencinformációja a HTML-fájlban szerepel.
- A régebbi bináris `.xls` fájlokhoz csak **korlátozott olvasási támogatás** tartozik; ezeknél a `.xlsx`-re váltás ajánlott. A program új fájlokat `.xlsx` formátumban hoz létre.
- Az új ülésrend véletlenszerű keveréssel, valamint a csoportok és az eredeti padtársak figyelembevételével, helyben számítódik ki.

**Ez a README az önálló, offline HTML-verziót dokumentálja.** Ha a GitHub-tárhelyen még a régi, CDN-t használó `index.html` van, annak cseréjéig az ott futó verzióra nem érvényes minden itt leírt állítás.
