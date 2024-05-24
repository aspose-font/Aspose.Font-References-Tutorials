---
title: Szerezze be az Aspose.Font betűtípus-metrikákat a .NET Type 1-hez
linktitle: Szerezze be az Aspose.Font betűtípus-metrikákat a .NET Type 1-hez
second_title: Aspose.Font .NET API
description: Ebből az átfogó, lépésenkénti oktatóanyagból megtudhatja, hogyan szerezhet be betűtípus-metrikákat az Aspose.Font for .NET használatával. Bármilyen szintű fejlesztők számára tökéletes!
type: docs
weight: 11
url: /hu/net/aspose-font-net-type1-font/get-font-metrics-aspose-font-net-type1/
---
## Bevezetés
Üdvözöljük az Aspose.Font for .NET-hez való betűtípus-metrikák megszerzésének végső útmutatójában! Akár tapasztalt fejlesztő vagy, akár csak belemerülsz a betűtípusok világába, ez az oktatóanyag lépésről lépésre végigvezeti a folyamaton. A cikk végére képes lesz a részletes betűtípus-metrikák kibontására, és megértheti, hogyan kezelheti azokat .NET-alkalmazásaiban. Szóval, merüljünk bele, és kezdjük el ezt az izgalmas utazást!
## Előfeltételek
Mielőtt belemerülnénk az aprólékos dolgokba, néhány dolgot meg kell határoznia:
- Visual Studio: Győződjön meg arról, hogy a Visual Studio telepítve van a gépen.
-  Aspose.Font for .NET: Töltse le és telepítse az Aspose.Font for .NET könyvtárat. Beszerezheti a[letöltési link](https://releases.aspose.com/font/net/).
- Alapvető C# ismerete: A C# programozás ismerete szükséges a példák követéséhez.
- Betűtípusfájl: Készítsen TrueType betűtípusfájlt (.ttf). Ehhez az oktatóanyaghoz bármilyen .ttf fájlt használhat.
Most, hogy mindennel készen vagyunk, kezdjük a szükséges névterek importálásával.
## Névterek importálása
Az Aspose.Font for .NET használatához a megfelelő névtereket bele kell foglalnia a projektbe. Íme, hogyan kell csinálni:
```csharp
using Aspose.Font.Glyphs;
using Aspose.Font.Sources;
using Aspose.Font.Ttf;
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;
```
Ha ezekkel a névterekkel a helyükön vannak, elkezdheti a betűtípusokkal való munkát a .NET-alkalmazásában.
## 1. lépés: Töltse be a betűtípusfájlt
Először is be kell töltenie a fontfájlt az alkalmazásba. Így csináld:
### Betűtípusfájl betöltése
1. Határozza meg a betűtípusfájl elérési útját. 
2.  Hozzon létre egy`FontDefinition` tárgy.
3.  Használja a`Font.Open` a betűtípus betöltésének módja.
```csharp
string dataDir = "Your Document Directory";
string fileName = dataDir + "Montserrat-Regular.ttf";
FontDefinition fd = new FontDefinition(FontType.TTF, new FontFileDefinition("ttf", new FileSystemStreamSource(fileName)));
TtfFont font = Aspose.Font.Font.Open(fd) as TtfFont;
```
 Itt a`FontDefinition` osztályt, hogy meghatározzuk a betűtípusfájlunk típusát és helyét. A`Font.Open` metódus betölti a betűtípust a`TtfFont` tárgy.
## 2. lépés: Az alapvető betűtípus-információk lekérése
A betűtípus betöltése után lekérhet néhány alapvető információt róla.
### Get Font Name és Glyph Count
```csharp
string name = font.FontName;
Console.WriteLine("Font name: " + name);
Console.WriteLine("Glyph count: " + font.NumGlyphs);
```
Ez a kódrészlet kinyomtatja a betűtípus nevét és a benne lévő karakterjelek számát.
## 3. lépés: Betűmutatók kibontása
betűtípus-metrikák részletes információkat nyújtanak a betűtípus jellemzőiről.
### Betűtípus-metrikák megjelenítése
```csharp
string metrics = string.Format(
    "Font metrics: ascender - {0}, descender - {1}, typo ascender = {2}, typo descender = {3}, UnitsPerEm = {4}",
    font.Metrics.Ascender, font.Metrics.Descender,
    font.Metrics.TypoAscender, font.Metrics.TypoDescender, font.Metrics.UnitsPerEM);
Console.WriteLine(metrics);
```
Ez a részlet formázza és kinyomtatja a betűtípus különböző mutatóit, például növekvő, csökkenő és egységenkénti mutatót.
## 4. lépés: Nyissa meg a CMap Unicode táblázatot
A CMap tábla segít a karakterkódok karakterjel-indexekhez való hozzárendelésében.
### A CMap táblázat lekérése és ellenőrzése
```csharp
TtfCMapFormatBaseTable cmapTable = null;
if (font.TtfTables.CMapTable != null)
{
    cmapTable = font.TtfTables.CMapTable.FindUnicodeTable();
}
if (cmapTable != null && font.TtfTables.GlyfTable != null)
{
    Console.WriteLine("Font cmap unicode table: PlatformID = " + cmapTable.PlatformId + ", PlatformSpecificID = " + cmapTable.PlatformSpecificId);
}
```
Ez a kód lekéri a CMap táblát, és kinyomtatja a PlatformID és PlatformSpecificID azonosítót.
## 5. lépés: Glyph információk beszerzése
Végül kérjünk információkat egy adott karakterjelről, például az „A” karakter karakterjeléről.
### Glyph információk lekérése
```csharp
char unicode = (char)65;
uint glIndex = cmapTable.GetGlyphIndex(unicode);
if (glIndex != 0)
{
    Glyph glyph = font.GetGlyphById(glIndex);
    if (glyph != null)
    {
        Console.WriteLine("Glyph metrics for 'A' symbol:");
        string bbox = string.Format(
            "Glyph BBox: Xmin = {0}, Xmax = {1}" + ", Ymin = {2}, Ymax = {3}",
            glyph.GlyphBBox.XMin, glyph.GlyphBBox.XMax,
            glyph.GlyphBBox.YMin, glyph.GlyphBBox.YMax);
        Console.WriteLine(bbox);
        Console.WriteLine("Width:" + font.Metrics.GetGlyphWidth(new GlyphUInt32Id(glIndex)));
    }
}
```
Ez a részlet lekéri az „A” karakterjel-indexét, lekéri a karakterjelet ezzel az indexszel, és kinyomtatja annak metrikáját, beleértve a határolókeretet és a szélességet.
## Következtetés
Gratulálunk! Sikeresen megtanulta, hogyan szerezhet be betűtípus-metrikákat az Aspose.Font for .NET használatával. Az alábbi lépések követésével könnyedén kibonthatja és kezelheti a betűtípus-információkat az alkalmazásokban. Ennek az oktatóanyagnak szilárd alapot kell nyújtania a fejlettebb betűtípus-műveletekhez. Boldog kódolást!
## GYIK
### 1. kérdés: Használhatom az Aspose.Font for .NET fájlt más betűtípusokkal?
Igen, az Aspose.Font for .NET különféle betűformátumokat támogat, köztük a TrueType, OpenType, Type1 és egyebeket.
### 2. kérdés: Hol szerezhetem be az Aspose.Font ingyenes próbaverzióját .NET-hez?
 Ingyenes próbaverziót tölthet le a webhelyről[Az Aspose kiadási oldala](https://releases.aspose.com/).
### 3. kérdés: Hogyan vásárolhatok licencet az Aspose.Font .NET-hez?
 Engedélyt vásárolhat a[Aspose vásárlási oldal](https://purchase.aspose.com/buy).
### 4. kérdés: Van-e támogatás az Aspose.Font for .NET számára?
 Igen, kaphat támogatást a[Aspose támogatási fórum](https://forum.aspose.com/c/font/41).
### 5. kérdés: Használhatom az Aspose.Font for .NET fájlt kereskedelmi projektekben?
Igen, az Aspose.Font for .NET használható kereskedelmi projektekben, de érvényes licencre lesz szüksége.