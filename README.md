# Ülésrend szervező

Böngészőben futó, **egyetlen, önálló HTML-fájlból álló**, tanároknak készült alkalmazás. Az osztály Excelben tárolt eredeti ülésrendjéből új beosztást készít a hiányzók és a **helyükön rögzített tanulók** figyelembevételével. Az eredmény Excel-fájlba menthető és kivetíthető. Opcionálisan két, a tanár által megadott csoport tagjait is keveri, hogy lehetőleg minél több vegyes pár és trió alakuljon ki.

**Az offline változat internetkapcsolat nélkül is használható.** A névlistát, a rögzítéseket és a csoportjelöléseket a böngésző helyben dolgozza fel; a program nem küldi el őket szerverre.

## Mit csinál a program?

1. **Excel-fájl betöltése és mintafájl letöltése** – Az eredeti ülésrend húzással vagy tallózással tölthető be. Az ajánlott formátum a **`.xlsx`**; a régebbi **`.xls`** állományok támogatása korlátozott. A **Próba ülésrend** kitalált nevekkel tesztelhető. A **Minta Excel letöltése** gomb megfelelő cellastruktúrájú, helyettesítő neveket, egy `Csoportok` munkalapot és a rögzítéshez szükséges oszlopot tartalmazó sablont készít. A program az azonos nevek ismétlődését jelzi, és a hibás névsort nem dolgozza fel.
2. **Hiányzók és rögzítések jelölése** – Az eredeti ülésrend fölött választható ki, hogy a nevekre kattintva a **hiányzást** vagy a **rögzítést** szeretnéd módosítani. Egy második kattintás visszavonja az adott jelölést. A két tulajdonság független: a rögzített tanuló hiányzónak is jelölhető. Az előkészítő felületen a rögzített tanulók lila, a hiányzók piros jelölést kapnak. Külön gomb állítja vissza a hiányzásokat, illetve az Excelből betöltött rögzítési alapállapotot.
3. **Új ülésrend generálása** – Minden generáláskor újrarendezi a **nem rögzített, jelen lévő** tanulókat. A jelen lévő rögzítettek az eredeti Excelben szereplő pontos ülőhelyükön maradnak. A 35 férőhelyes, rögzített teremelrendezés öt sorból áll; soronként két kétszemélyes és egy háromszemélyes pad található, közöttük folyosókkal. A program lehetőség szerint párokat alakít ki, szükség esetén triókat. A háromszemélyes padban a kétfős elhelyezés alapértelmezés szerint az első két helyet használja, kivéve, ha a rögzítések más elhelyezést tesznek szükségessé.
4. **Az eredeti padtársak lehetőség szerinti szétválasztása** – A keverhető tanulók beosztásánál a program igyekszik elkerülni, hogy az eredeti padtársak ismét együtt üljenek. Ez **törekvés, nem garantálható minden létszám- és rögzítési helyzetben**; a rögzítések elsőbbséget élveznek.
5. **Opcionális csoportkeverés** – Az Excelben megadott két csoport alapján előnyben részesíti a vegyes párokat és triókat. A **Csoportok keverése** kapcsoló csak akkor használható, ha megfelelő csoportadatok állnak rendelkezésre; az új beállítás a következő generáláskor érvényesül. A rögzítettek ebben az esetben sem mozdulnak el.
6. **Mentés, vetítés, újragenerálás** – A generált ülésrend `.xlsx` formátumban letölthető, kivetíthető vagy újragenerálható. **A generált ülésrend cellái nem kattinthatók és nem szerkeszthetők.** Ha az eredeti ülésrendnél megváltoztatod a hiányzásokat vagy a rögzítéseket, a korábbi generálás érvényét veszti; új ülésrendet kell generálni.

## Az Excel-minta kitöltése

1. Töltsd le a sablont a **Minta Excel letöltése** gombbal.
2. Az **Ülésrend** munkalapon cseréld ki a helyettesítő neveket a tanulók neveire, a megfelelő ülőhelyeken. A nem használt ülőhelyekről töröld a helyettesítő neveket. A padok és a folyosók cellastruktúráját tartsd meg.
3. A **Csoportok** munkalapon a **Név** oszlop képletekkel kapcsolódik az ülésrend megfelelő celláihoz, így a neveket nem kell kétszer beírni.
4. A **Csoport** oszlopba opcionálisan legfeljebb kétféle jelölés írható (például `A` és `B`). Ha nincs szükség csoportkeverésre, hagyd üresen.
5. A **Rögzített** oszlopban `R` betűvel jelölheted, hogy az adott tanuló az eredeti helyén maradjon, és ne vegyen részt a keverésben. **Üres cella = keverhető tanuló.** A munkalap **Kitöltési útmutató** oszlopa ezt el is magyarázza. A rögzítés csoportbesorolás nélkül is használható.
6. Mentsd el a kitöltött munkafüzetet `.xlsx` formátumban. Használatkor **mindig ezt az eredeti, kitöltött Excel-fájlt töltsd be**, majd a webes felületen jelöld az adott alkalom hiányzóit, szükség esetén módosítsd a rögzítéseket, és generálj új ülésrendet.

Példa a `Csoportok` munkalap három adatmezőjére:

| Név | Csoport | Rögzített |
| --- | --- | --- |
| Tanuló neve 1 | A | R |
| Tanuló neve 2 | B | |
| Tanuló neve 3 | A | R |

**Fontos:** a neveket először az **Ülésrend** munkalapon véglegesítsd, és csak ezután add meg a csoport- és rögzítésjelöléseket. Ha később átírod vagy átrendezed a neveket, ellenőrizd a mellettük álló jelöléseket is: a névképletek az ülőhelyeket követik, a kézzel beírt jelölések a saját cellájukban maradnak.

A régi, **egyetlen munkalapot tartalmazó** Excel-fájlok is használhatók; a `Csoportok` munkalap nem kötelező. A program az ülésrendhez az első olyan munkalapot használja, amelynek neve nem `Csoportok`. A régi, rögzítési oszlop nélküli munkafüzetek is használhatók.

## A rögzítések működése

- A rögzítés **egy tanulóra** vonatkozik, nem a teljes padra: a jelen lévő rögzített tanuló az eredeti ülőhelyén marad, a többiek továbbra is keverhetők.
- Az Excelben az `R` jelölés adja a **következő betöltéskor is érvényes alapállapotot**. A webes felületen rögzítést adhatsz hozzá vagy oldhatsz fel, de ezzel **nem változik meg a forrás-Excel**.
- A **Rögzítések visszaállítása** gomb az aktuális munkamenetben az Excelből betöltött rögzítéseket állítja vissza. A **Hiányzók visszaállítása** a hiányzásjelöléseket törli.
- Ha egy rögzített tanuló **hiányzik**, nem kerül az új beosztásba; a helye az adott generáláskor más tanuló számára felhasználható.
- Új Excel-fájl betöltésekor a korábbi alkalmi jelölések törlődnek. A program nem tárolja tartósan ezeket a böngészőben.
- A kivetített ülésrend **nem árulja el, hogy ki van rögzítve**.

**A letöltött új ülésrend nem helyettesíti az eredeti forrásfájlt.** Az új ülésrend exportja nem menti tovább a rögzítési alapállapotot: a tartós `R` jelöléseket az eredeti, kitöltött Excelben őrizd meg.

## Csoportkeverés tetszőleges szempont alapján

A **Csoportok** munkalap **Csoport** oszlopában legfeljebb kétféle jelölés használható, például **A** és **B**. Ezek jelentését a tanár határozza meg: elkülöníthetnek például különböző feladatváltozatokon dolgozó vagy eltérő előzetes tapasztalattal rendelkező tanulókat. A program a jelölésekből nem következtet személyes tulajdonságokra.

- A program lehetőleg minél több olyan padot alakít ki, amelyben **mindkét csoportból** ül tanuló. Ezt a létszámok és a rögzítések korlátozhatják.
- A csoporthoz nem rendelt tanulók is részt vehetnek a keverésben.
- Ha nincsenek érvényes csoportjelölések, a csoportkeverés nem kapcsolható be. Ha a jelenlévők között csak egy megjelölt csoport szerepel, a szokásos keverés működik.
- A hibás vagy hiányos csoportadatokra a program visszajelzést ad; az ülésrend alapfunkciói ettől még használhatók.
- A csoportjelölések **nem jelennek meg** az ülésrendben vagy a vetítésben.

A csoportkeverés és a korábbi padtársak elkerülése optimalizálási törekvés; a jelen lévő rögzített tanulók helye mindkettőnél elsőbbséget élvez.

## Kivetítés (projektoros mód)

Az eredeti és az új ülésrend egyaránt megjeleníthető a böngészőablakot kitöltő, vetítésre optimalizált nézetben. Az eredeti ülésrend vetítésekor a hiányzók halványítva, piros kiemeléssel jelennek meg. A **rögzítések jelölése nem látszik a vetítésben**. Az új beosztás csak a generáláskor jelen lévőnek jelölt tanulókat tartalmazza.

A **Tanár nézet / Diák nézet** gombbal vagy az `M` billentyűvel átváltható a terem nézőpontja. A vetítés az `Esc` billentyűvel vagy a **Bezárás** gombbal zárható be.

## Indítás és működés internet nélkül

1. Mentsd el a teljes, offline HTML-fájlt a számítógépre (a GitHub-tárhelyen `index.html` néven szerepel).
2. Nyisd meg Chrome-ban vagy más korszerű böngészőben – nincs szükség telepítésre vagy külön szerverre.
3. A fájlt **internetkapcsolat nélkül is megnyithatod**, majd használhatod az Excel-beolvasást, a generálást és a letöltést.

Ha a program GitHub Pages-oldalként érhető el, a **HTML-oldal letöltéséhez** szükség van internetre, de a jelenlegi programkód a **tanulói névlistát nem továbbítja** a tárhelyszolgáltatónak. A teljesen offline használathoz a helyben elmentett HTML-fájlt nyisd meg.

## Adatkezelés és mentés

- A fájlbeolvasás, az ülésrend generálása, a hiányzások, a rögzítések és a csoportok kezelése, valamint az Excel-fájl előállítása **a böngészőben, helyben történik**.
- A HTML-kód **nem tartalmaz névlista-feltöltést, külső adatküldést, telemetriát vagy külső JavaScript-betöltést**.
- **Nincs automatikus felhőmentés vagy tartós böngészős tárolás.** Az aktuális munkamenet adatai a lap bezárásakor vagy újratöltésekor elvesznek; a tartós rögzítéseket az eredeti Excel-fájlban tárold.
- A letöltött Excel-fájlok személyes adatokat tartalmazhatnak. Kezelésük, megosztásuk és az ülésrend vetítése során az iskola adatvédelmi szabályai irányadók.

A helyi feldolgozás csökkenti a külső adattovábbítás kockázatát, de **önmagában nem bizonyítja a teljes GDPR-megfelelőséget**.

## Technikai háttér

- Az alkalmazás egyetlen HTML-fájlból áll: ebben található a felület, a stílus, az ülésrendkészítés és az Excel-kezelés kódja.
- Az offline változat **nem használ CDN-ről betöltött SheetJS-t**. Az `.xlsx` fájlokat a program igényeire szabott, beépített olvasó–író kód és a helyben beágyazott **JSZip 3.10.1** könyvtár kezeli; licencinformációja a HTML-fájlban szerepel.
- A régebbi bináris `.xls` fájlokhoz csak **korlátozott olvasási támogatás** tartozik; ajánlott a `.xlsx` formátum. Az új fájlok `.xlsx` formátumban készülnek.
- Rögzített tanuló nélkül a korábbi keverési algoritmus használható; rögzítés esetén az algoritmus először lefoglalja az érintett eredeti helyeket, és a többi jelenlévőt osztja be a rendelkezésre álló helyekre.

**Verziómegjegyzés:** ez a README a rögzítést és a nem kattintható generált ülésrendet is tartalmazó **javított HTML-verzióhoz** készült. Amíg a GitHubon az `index.html` korábbi változata található, a README egyes új funkciói még nem érhetők el az online programban. A fájlok összhangjához a javított HTML-t is fel kell tölteni.
