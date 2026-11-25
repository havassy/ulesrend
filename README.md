# Ülésrend szervező és csoportalakító

Böngészőben futó, **egyetlen, önálló HTML-fájlból álló**, tanároknak készült alkalmazás. Az osztály Excelben tárolt eredeti ülésrendjéből új padbeosztást készít a hiányzók és a **rögzített tanulók** figyelembevételével. Ettől függetlenül a jelenlévőkből tanulócsoportokat is alakít, egyenletes létszámmal, az A/B besorolások keverésével és opcionális együtt–külön szabályokkal. Az ülésrend és a csoportbeosztás külön-külön Excel-fájlba menthető és saját vetítési nézetben megjeleníthető.

**Az offline változat internetkapcsolat nélkül is használható.** A névlistát, a rögzítéseket és a csoportjelöléseket a böngésző helyben dolgozza fel; a program nem küldi el őket szerverre.

## Mit csinál a program?

1. **Excel-fájl betöltése és mintafájl letöltése** – Az eredeti ülésrend húzással vagy tallózással tölthető be. Az ajánlott formátum a **`.xlsx`**; a régebbi **`.xls`** állományok támogatása korlátozott. A **Próba ülésrend** kitalált nevekkel tesztelhető. A **Minta Excel letöltése** gomb megfelelő cellastruktúrájú, helyettesítő neveket, egy `Csoportok` munkalapot, valamint a csoportbesorolás, a rögzítés és az együtt–külön szabályok oszlopait tartalmazó sablont készít. A program az azonos nevek ismétlődését jelzi, és a hibás névsort nem dolgozza fel.
2. **Hiányzók és rögzítések jelölése** – Az eredeti ülésrend fölött választható ki, hogy a nevekre kattintva a **hiányzást** vagy a **rögzítést** szeretnéd módosítani. Egy második kattintás visszavonja az adott jelölést. A két tulajdonság független: a rögzített tanuló hiányzónak is jelölhető. Az előkészítő felületen a rögzített tanulók lila, a hiányzók piros jelölést kapnak. Külön gomb állítja vissza a hiányzásokat, illetve az Excelből betöltött rögzítési alapállapotot.
3. **Új ülésrend generálása** – Minden generáláskor újrarendezi a **nem rögzített, jelen lévő** tanulókat. A jelen lévő rögzítettek az eredeti padjukban maradnak, és alapesetben a pontos ülőhelyüket is megtartják. A vegyes triók kialakításának kivételét [A rögzítések működése](#a-rögzítések-működése) rész ismerteti. A 35 férőhelyes, rögzített teremelrendezés öt sorból áll; soronként két kétszemélyes és egy háromszemélyes pad található, közöttük folyosókkal. A program lehetőség szerint párokat alakít ki, szükség esetén triókat. A háromszemélyes padban a kétfős elhelyezés alapértelmezés szerint az első két helyet használja, kivéve, ha a rögzítések más elhelyezést tesznek szükségessé.
4. **Az eredeti padtársak lehetőség szerinti szétválasztása** – A keverhető tanulók beosztásánál a program igyekszik elkerülni, hogy az eredeti padtársak ismét együtt üljenek. Ez **törekvés, nem garantálható minden létszám- és rögzítési helyzetben**; a rögzítések elsőbbséget élveznek.
5. **Vegyes padok kialakítása** – A korábbi **Csoportok keverése** kapcsoló új neve. Az Excelben megadott két besorolás alapján előnyben részesíti a vegyes párokat és triókat, a háromfős padokban lehetőleg A–B–A vagy B–A–B sorrenddel. Csak megfelelő csoportadatokkal használható; a beállítás a következő ülésrend-generáláskor érvényesül. Ez az ülésrendhez tartozó kapcsoló, a külön **Csoportalakítás** funkció működését nem vezérli.
6. **Mentés, vetítés, újragenerálás** – A generált ülésrend `.xlsx` formátumban letölthető, kivetíthető vagy újragenerálható. **A generált ülésrend cellái nem kattinthatók és nem szerkeszthetők.** Ha az eredeti ülésrendnél megváltoztatod a hiányzásokat vagy a rögzítéseket, a korábbi generálás érvényét veszti; új ülésrendet kell generálni.
7. **Önálló csoportalakítás** – A **4. Csoportalakítás** részben megadható a csoportok száma, bekapcsolhatók az együtt–külön szabályok, és létrehozhatók a jelenlévők csoportjai. Az eredmény kézzel cserélhető és átrendezhető, külön Excel-exporttal és egy képernyőre méretezett vetítéssel. Ehhez nem kell előbb új ülésrendet generálni.

## Az Excel-minta kitöltése

1. Töltsd le az `ulesrend_minta.xlsx` sablont a **Minta Excel letöltése** gombbal. A mintafájlt a program helyben állítja elő, ezért a gomb az offline HTML-ben internet nélkül is működik.
2. Az **Ülésrend** munkalapon cseréld ki a helyettesítő neveket a tanulók neveire, a megfelelő ülőhelyeken. A nem használt ülőhelyekről töröld a helyettesítő neveket. A padok és a folyosók cellastruktúráját tartsd meg.
3. A **Csoportok** munkalapon a **Név** oszlop képletekkel kapcsolódik az ülésrend megfelelő celláihoz, így a neveket nem kell kétszer beírni.
4. A **Csoport** oszlopba opcionálisan legfeljebb kétféle jelölés írható (például `A` és `B`). Ezeket a vegyes padok kialakítása és az önálló csoportalakító is felhasználja. Ha egyikhez sincs szükség besorolásra, hagyd üresen.
5. A **Rögzített** oszlopban `R` betűvel jelölheted, hogy az adott tanuló ne kerüljön másik padba, és ne vegyen részt az általános ülésrend-keverésben. **Üres cella = keverhető tanuló.** A vegyes triókra vonatkozó ülőhely-kivételt a **Kitöltési útmutató** is jelzi. A rögzítés csoportbesorolás nélkül is használható, és az önálló csoportalakítást nem korlátozza.
6. Az **Együtt–külön** oszlopba opcionálisan `C1`, `C2`, `C3`… vagy `D` írható. Az azonos C-jelölésű tanulók lehetőleg együtt, a D-jelölésűek egymástól külön csoportba kerülnek. Az üres cella nem ad megkötést. Ezek a jelölések kizárólag az önálló csoportalakítóban érvényesülnek.
7. Mentsd el a kitöltött munkafüzetet `.xlsx` formátumban. Használatkor **mindig ezt az eredeti, kitöltött Excel-fájlt töltsd be**, majd a webes felületen jelöld az adott alkalom hiányzóit, szükség esetén módosítsd a rögzítéseket, és generálj új ülésrendet vagy csoportbeosztást.

Példa a `Csoportok` munkalap négy adatmezőjére:

| Név | Csoport | Rögzített | Együtt–külön |
| --- | --- | --- | --- |
| Tanuló neve 1 | A | R | C1 |
| Tanuló neve 2 | B | | C1 |
| Tanuló neve 3 | A | | D |
| Tanuló neve 4 | B | | D |
| Tanuló neve 5 | A | | C2 |
| Tanuló neve 6 | B | | C2 |

**Fontos:** a neveket először az **Ülésrend** munkalapon véglegesítsd, és csak ezután add meg a csoport-, rögzítés- és együtt–külön jelöléseket. Ha később átírod vagy átrendezed a neveket, ellenőrizd a mellettük álló csoport-, rögzítés- és együtt–külön jelöléseket is: a névképletek az ülőhelyeket követik, a kézzel beírt jelölések a saját cellájukban maradnak.

A régi, **egyetlen munkalapot tartalmazó** Excel-fájlok is használhatók; a `Csoportok` munkalap nem kötelező. A program az ülésrendhez az első olyan munkalapot használja, amelynek neve nem `Csoportok`. A régi, rögzítési vagy együtt–külön oszlop nélküli munkafüzetek is használhatók; a hiányzó kiegészítő adatok nélkül működnek az alapfunkciók.

## A rögzítések működése

- A rögzítés **egy tanulóra** vonatkozik, nem a teljes padra: a jelen lévő rögzített tanuló az eredeti padjában marad, a többiek továbbra is keverhetők. Kikapcsolt **Vegyes padok kialakítása** mellett a pontos eredeti ülőhelye is változatlan.
- **Kivétel vegyes triónál:** bekapcsolt vegyespad-kialakításkor egy teljesen betöltött háromfős pad két azonos és egy eltérő jelölésű tanulóját a program lehetőleg A–B–A vagy B–A–B sorrendbe rendezi. Ehhez a pad egyetlen rögzített tanulója legfeljebb **egy szomszédos székkel** arrébb kerülhet, ugyanazon a padon belül. Ha a padban legalább két rögzített tanuló ül, ez az átrendezés elmarad.
- Az Excelben az `R` jelölés adja a **következő betöltéskor is érvényes alapállapotot**. A webes felületen rögzítést adhatsz hozzá vagy oldhatsz fel, de ezzel **nem változik meg a forrás-Excel**.
- A **Rögzítések visszaállítása** gomb az aktuális munkamenetben az Excelből betöltött rögzítéseket állítja vissza. A **Hiányzók visszaállítása** a hiányzásjelöléseket törli.
- Ha egy rögzített tanuló **hiányzik**, nem kerül az új beosztásba; a helye az adott generáláskor más tanuló számára felhasználható.
- Új Excel-fájl betöltésekor a korábbi alkalmi jelölések törlődnek. A program nem tárolja tartósan ezeket a böngészőben.
- A kivetített ülésrend **nem árulja el, hogy ki van rögzítve**.
- A rögzítés az ülésrendre vonatkozik: a jelen lévő rögzített tanuló az önálló **Csoportalakításban** ugyanúgy beosztható, cserélhető és áthelyezhető. A rögzítés változtatása az ülésrendet érvényteleníti, a már elkészült csoportbeosztást nem.

**A letöltött új ülésrend nem helyettesíti az eredeti forrásfájlt.** Az új ülésrend exportja nem menti tovább a rögzítési alapállapotot: a tartós `R` jelöléseket az eredeti, kitöltött Excelben őrizd meg.

## Vegyes padok kialakítása tetszőleges szempont alapján

Az ülésrendnél található **Vegyes padok kialakítása** a korábbi **Csoportok keverése** kapcsoló új neve. A **Csoportok** munkalap **Csoport** oszlopában legfeljebb kétféle jelölés használható, például **A** és **B**. Ezek jelentését a tanár határozza meg: elkülöníthetnek például különböző feladatváltozatokon dolgozó vagy eltérő előzetes tapasztalattal rendelkező tanulókat. A program a jelölésekből nem következtet személyes tulajdonságokra.

- A program lehetőleg minél több olyan padot alakít ki, amelyben **mindkét besorolásból** ül tanuló. Ezt a létszámok és a rögzítések korlátozhatják. A vegyes triókban lehetőleg A–B–A vagy B–A–B sorrend készül, hogy az eltérő jelölésű tanuló középre kerüljön.
- A csoporthoz nem rendelt tanulók is részt vehetnek a keverésben.
- Ha nincsenek érvényes csoportjelölések, a csoportkeverés nem kapcsolható be. Ha a jelenlévők között csak egy megjelölt csoport szerepel, a szokásos keverés működik.
- A hibás vagy hiányos csoportadatokra a program visszajelzést ad; az ülésrend alapfunkciói ettől még használhatók.
- A csoportjelölések **nem jelennek meg** az ülésrendben vagy a vetítésben.

A vegyes padok kialakítása és a korábbi padtársak elkerülése optimalizálási törekvés. A rögzített tanulók nem kerülnek másik padba; a pontos ülőhelyükre a fenti, vegyes triókra vonatkozó kivétel érvényes. A `C1`, `C2`… és `D` megkötések ezt az ülésrend-keverést nem befolyásolják.

## Önálló csoportalakítás

A **4. Csoportalakítás** az Excel betöltése vagy a próbaülésrend megnyitása után használható. Az adott alkalommal jelen lévő tanulókból állít össze csoportokat, az eredeti és a generált ülésrendtől függetlenül. A hiányzók kimaradnak, a rögzített jelenlévők részt vesznek benne.

1. Állítsd be az eredeti ülésrendnél a hiányzókat.
2. Add meg a **Csoportok száma** mezőben a kívánt csoportszámot: 1 és a jelenlévők száma közötti egész szám választható.
3. Ha az Excel tartalmaz megfelelő adatokat, döntsd el, használod-e az **Együtt–külön jelölések figyelembevétele** kapcsolót. Érvényes jelölések betöltésekor ez alapból be van kapcsolva; jelölések nélkül vagy hibás adatoknál nem kapcsolható be.
4. Kattints a **Csoportok generálása / újragenerálása** gombra. Ezután kézzel módosíthatod, Excelbe exportálhatod vagy kivetítheted a beosztást.

### Létszámelsőbbség és A/B keverés

- **Az automatikus generálás elsőbbsége az egyenletes csoportlétszám.** A legnagyobb és a legkisebb csoport között legfeljebb egy fő eltérés lesz. Például 35 jelenlévőből 9 csoport esetén nyolc 4 fős és egy 3 fős csoport készül.
- Az együtt–külön szabályok és az A/B vegyítés **nem növelik meg az előre meghatározott csoportlétszámokat**.
- Ha kétféle érvényes besorolás szerepel az Excelben, a csoportalakító automatikusan törekszik mindkettő vegyes, a jelenlévők arányát követő elosztására. Ehhez nem kell bekapcsolni az ülésrend **Vegyes padok kialakítása** kapcsolóját.
- A besorolás nélküli tanulók is csoportba kerülnek. A/B adatok nélkül is működik az egyenletes létszámú csoportalakítás.
- Az A/B jelölések nem jelennek meg a tanulók neve mellett. A szerkesztőfelület tanári háttérinformációként színnel és csoportonkénti A/B darabszámmal segíti az ellenőrzést. A diákoknak a külön vetítési nézetet használd.

### C1/C2 és D együtt–külön szabályok

Az Excel **Csoportok** munkalapjának **Együtt–külön** oszlopa az A/B besorolástól és az `R` rögzítéstől független:

| Jelölés | Jelentés a csoportalakítóban |
| --- | --- |
| `C1` | Minden jelen lévő C1-jelölésű tanuló lehetőleg ugyanabba a csoportba kerüljön. |
| `C2`, `C3`… | További, önállóan együtt tartandó társaságok, azonos jelölésenként. |
| `D` | A jelen lévő D-jelölésű tanulók lehetőleg egymástól külön csoportba kerüljenek. |
| Üres cella | Nincs együtt–külön megkötés. |

A C1 és C2 **nem az elkészülő csoportok sorszáma**. Az eltérő C-jelölések nem írnak elő elkülönítést: például egy C1-es és egy C2-es társaság ugyanabba a csoportba is kerülhet, ha elférnek. A D-jelölés a többi D-jelölésű tanulótól való elkülönítést kéri, nem az összes többi tanulótól.

Bekapcsolt szabályoknál a program az egyenletes létszámokon belül először az azonos C-jelölésűek együtt tartását, majd a D-jelölésűek különválasztását, végül az A/B elosztást részesíti előnyben. Ezek **optimalizálási törekvések, nem teljesülési garanciák**. Ha egy C-jelölésű társaság nagyobb a megengedett csoportlétszámnál, vagy több D-jelölésű tanuló van, mint csoport, minden kérés eleve nem teljesíthető. A keresés más helyzetben is hagyhat meg ütközést; a figyelmeztetés önmagában nem bizonyítja, hogy nincs jobb beosztás.

A tanári felület jelzi a szétszakadt C-társaságokat, az egy csoportba került D-jelölésűeket és azt, ha valamely többfős csoportból az egyik A/B besorolás hiányzik. Az eredmény ezekkel a figyelmeztetésekkel együtt is használható és kézzel javítható. Hibás együtt–külön adatok esetén a program a hibát jelzi, a csoportalakítás pedig ezek nélkül továbbra is használható. A jelölések csak ebben a funkcióban érvényesülnek, az ülésrendben nem.

### Kézi csere és áthelyezés

- **Csere:** kattints egy tanuló nevére, majd egy másik csoport tanulójára. A két tanuló helyet cserél, a csoportlétszámok változatlanok maradnak. A kiválasztott névre ismét kattintva megszüntetheted a kijelölést.
- **Áthelyezés:** válaszd ki a tanulót, állítsd be a **Célcsoportot**, majd kattints az **Áthelyezés** gombra. Ez megváltoztatja a két érintett csoport létszámát.
- **Áthúzás asztali gépen:** másik tanuló nevére húzva csere, másik csoport kártyájára húzva áthelyezés történik.
- A kézi módosítás felülírhatja az automatikus létszámegyensúlyt és a szabályokat. A program frissíti a létszámokat és a figyelmeztetéseket, de nem vonja vissza automatikusan a változtatást.
- Az újragenerálás felülírja a kézi beosztást. Kézi módosítás után az újragenerálás, a csoportszám és az együtt–külön kapcsoló módosítása előtt megerősítést kér a program.
- **A jelenlét módosítása érvényteleníti a csoportbeosztást, a kézi módosításokat is beleértve.** Ezután új csoportokat kell generálni. Új Excel betöltésekor szintén új beosztás szükséges.

### A csoportbeosztás Excel-exportja

A csoportalakító **Excel-export** gombja az aktuális, kézi módosításokat is tartalmazó állapotot menti `csoportbeosztas_ÉÉÉÉ-HH-NN.xlsx` néven:

- **Csoportok** munkalap: a csoportok külön oszlopokban, alattuk a tanulók neveivel.
- **Névlista** munkalap: soronként a csoport, a tanuló neve és az **A/B jelölés**.

**A részletes Excel-export tehát tartalmazza az A/B besorolást**, bár a vetítés elrejti azt. A fájl nem ülésrendsablon és nem tartalmazza a forrás összes beállítását; a következő alkalomhoz az eredeti, kitöltött Excel-fájlt őrizd meg.

## Kivetítés (projektoros mód)

### Ülésrend

Az eredeti és az új ülésrend egyaránt megjeleníthető a böngészőablakot kitöltő, vetítésre optimalizált nézetben. Az eredeti ülésrend vetítésekor a hiányzók halványítva, piros kiemeléssel jelennek meg. A **rögzítések jelölése nem látszik a vetítésben**. Az új beosztás csak a generáláskor jelen lévőnek jelölt tanulókat tartalmazza.

A **Tanár nézet / Diák nézet** gombbal vagy az `M` billentyűvel átváltható a terem nézőpontja. A vetítés az `Esc` billentyűvel vagy a **Bezárás** gombbal zárható be.

### Csoportbeosztás

A csoportalakító saját **Vetítés** gombja külön, a böngészőablakot kitöltő nézetet nyit. Csak a csoportok sorszáma, létszáma és a tanulók neve látszik: **nincsenek A/B jelölések, A/B összesítések, besorolás szerinti színek, együtt–külön jelölések vagy szerkesztőeszközök**. Itt nincs tanár/diák nézetváltás és teremelforgatás.

A csoportkártyák elrendezése és betűmérete a rendelkezésre álló képernyőhöz igazodik, hogy a teljes beosztás **egy képernyőn, görgetés nélkül** jelenjen meg. A program az ablak átméretezésekor újraszámolja a megjelenítést, és a még elférő legnagyobb névbetűméretet választja. Széles képernyőn például 9 csoport 3 × 3-as, 7–8 vagy 10–12 csoport 4 oszlopos elrendezést kap. Sok csoport vagy hosszú nevek esetén a betűk kisebbek lehetnek.

A vetítés az `Esc` billentyűvel vagy a **Bezárás** gombbal zárható be. A tanári szerkesztőfelület és annak méretezése külön marad a vetítéstől.

## Indítás és működés internet nélkül

1. Mentsd el a teljes, offline HTML-fájlt a számítógépre (a GitHub-tárhelyen `index.html` néven szerepel).
2. Nyisd meg Chrome-ban vagy más korszerű böngészőben – nincs szükség telepítésre vagy külön szerverre.
3. A fájlt **internetkapcsolat nélkül is megnyithatod**, majd használhatod az Excel-beolvasást, az ülésrend- és csoportgenerálást, a kézi csoportmódosítást, a vetítést, valamint a minta és az eredmények letöltését.

Ha a program GitHub Pages-oldalként érhető el, a **HTML-oldal letöltéséhez** szükség van internetre, de a jelenlegi programkód a **tanulói névlistát nem továbbítja** a tárhelyszolgáltatónak. A teljesen offline használathoz a helyben elmentett HTML-fájlt nyisd meg.

## Adatkezelés és mentés

- A fájlbeolvasás, az ülésrend generálása, a hiányzások, a rögzítések, az A/B besorolások és az együtt–külön megkötések kezelése, a csoportalakítás és a kézi módosítás, valamint az Excel-fájl előállítása **a böngészőben, helyben történik**.
- A HTML-kód **nem tartalmaz névlista-feltöltést, külső adatküldést, telemetriát vagy külső JavaScript-betöltést**.
- **Nincs automatikus felhőmentés vagy tartós böngészős tárolás.** Az aktuális munkamenet adatai a lap bezárásakor vagy újratöltésekor elvesznek; a tartós rögzítéseket, az A/B besorolásokat és az együtt–külön jelöléseket az eredeti Excel-fájlban tárold. A kézzel módosított csoportbeosztást az Excel-exporttal mentheted el.
- A letöltött Excel-fájlok személyes adatokat tartalmazhatnak. Kezelésük, megosztásuk és az ülésrend vetítése során az iskola adatvédelmi szabályai irányadók.

A helyi feldolgozás csökkenti a külső adattovábbítás kockázatát, de **önmagában nem bizonyítja a teljes GDPR-megfelelőséget**.

## Technikai háttér

- Az alkalmazás egyetlen HTML-fájlból áll: ebben található a felület, a stílus, az ülésrendkészítés és az Excel-kezelés kódja.
- Az offline változat **nem használ CDN-ről betöltött SheetJS-t**. Az `.xlsx` fájlokat a program igényeire szabott, beépített olvasó–író kód és a helyben beágyazott **JSZip 3.10.1** könyvtár kezeli; licencinformációja a HTML-fájlban szerepel.
- A régebbi bináris `.xls` fájlokhoz csak **korlátozott olvasási támogatás** tartozik; ajánlott a `.xlsx` formátum. Az új fájlok `.xlsx` formátumban készülnek.
- Rögzített tanuló nélkül a korábbi ülésrend-keverési algoritmus használható; rögzítés esetén az algoritmus először lefoglalja az érintett eredeti helyeket, és a többi jelenlévőt osztja be a rendelkezésre álló helyekre. Ezután bekapcsolt vegyespad-kialakításnál megtörténhet a fent ismertetett, padon belüli triórendezés.
- Az önálló csoportalakító előre meghatározza az egyenletes csoportlétszámokat, majd több véletlen kiindulásból és létszámtartó cserékkel javítja a tagok elosztását. Az ülésrend és a csoportbeosztás külön állapotként működik.
