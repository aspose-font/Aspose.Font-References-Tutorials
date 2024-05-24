---
title: Szerezze be a betűtípus-metrikákat az Aspose.Font .NET-hez
linktitle: Szerezze be a betűtípus-metrikákat az Aspose.Font .NET-hez
second_title: Aspose.Font .NET API
description: Ismerje meg, hogyan szerezhet be betűtípus-metrikákat az Aspose.Font for .NET használatával. Útmutató lépésről lépésre kódpéldákkal. Előfeltételek és GYIK benne van. #Aspose #Font
type: docs
weight: 12
url: /hu/net/truetype-opentype/get-font-metrics/
---
## Bevezetés
Az Aspose.Font for .NET egy hatékony API, amely lehetővé teszi a fejlesztők számára, hogy fontokkal dolgozzanak .NET-alkalmazásaikban. Akár betűtípus-metrikákat kell kivonnia, akár karakterjeleket kell manipulálnia, akár betűtípusadatokat szeretne elérni, az Aspose.Font átfogó funkcionalitást biztosít a betűtípusokkal kapcsolatos feladatok egyszerűsítéséhez. Ebben az oktatóanyagban megvizsgáljuk, hogyan szerezhet be betűtípus-metrikákat az Aspose.Font for .NET használatával.
## Előfeltételek
Mielőtt belevágna ebbe az oktatóanyagba, győződjön meg arról, hogy beállította a következő előfeltételeket:
### 1. Aspose.Font .NET telepítéshez
 Győződjön meg arról, hogy az Aspose.Font for .NET telepítve van a fejlesztői környezetében. Ha még nem tette meg, letöltheti az API-t a[Aspose.Releases](https://releases.aspose.com/font/net/) vagy a NuGet csomagkezelőn keresztül.
### 2. Fejlesztői környezet beállítása
Győződjön meg arról, hogy a Visual Studio vagy bármely más kompatibilis IDE telepített .NET fejlesztői környezete be van állítva.

## Névterek importálása
.NET-alkalmazásban importálnia kell a szükséges névtereket az Aspose.Font for .NET használatához.
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
Most bontsuk fel a példát több lépésre, és magyarázzuk el mindegyiket részletesen.
## 1. lépés: Határozza meg a betűtípus fájl elérési útját
Először határozza meg annak a betűtípusnak az elérési útját, amellyel dolgozni szeretne.
```csharp
string dataDir = "Your Document Directory";
string fileName = dataDir + "Montserrat-Regular.ttf"; //Betűtípusfájl neve teljes elérési úttal
```
## 2. lépés: Nyissa meg a Font fájlt
Ezután nyissa meg a fontfájlt az Aspose.Font API segítségével.
```csharp
FontDefinition fd = new FontDefinition(FontType.TTF, new FontFileDefinition("ttf", new FileSystemStreamSource(fileName)));
TtfFont font = Aspose.Font.Font.Open(fd) as TtfFont;
```
## 3. lépés: A betűtípus-metrikák lekérése
Különféle betűtípus-metrikákat kérhet le, például emelkedő, csökkenő stb.
```csharp
string name = font.FontName;
Console.WriteLine("Font name: " + name);
Console.WriteLine("Glyph count: " + font.NumGlyphs);
string metrics = string.Format(
    "Font metrics: ascender - {0}, descender - {1}, typo ascender = {2}, typo descender = {3}, UnitsPerEm = {4}",
    font.Metrics.Ascender, font.Metrics.Descender,
    font.Metrics.TypoAscender, font.Metrics.TypoDescender, font.Metrics.UnitsPerEM);
Console.WriteLine(metrics);
```
## 4. lépés: Szerezze be az Unicode kódolási táblázatot
Töltse le a Unicode kódolási táblázatot (cmap) a betűtípusból.
```csharp
Aspose.Font.TtfCMapFormats.TtfCMapFormatBaseTable cmapTable = null;
if (font.TtfTables.CMapTable != null)
{
    cmapTable = font.TtfTables.CMapTable.FindUnicodeTable();
}
```
## 5. lépés: A Glyph Information elérése
Egy adott szimbólumhoz (pl. „A”) tartozó karakterjel-információk elérése.
```csharp
char unicode = (char)65; // Unicode az "A"-hoz
uint glIndex = cmapTable.GetGlyphIndex(unicode);
if (glIndex != 0)
{
    Glyph glyph = font.GetGlyphById(glIndex);
    if (glyph != null)
    {
        string bbox = string.Format(
            "Glyph BBox: Xmin = {0}, Xmax = {1}, Ymin = {2}, Ymax = {3}",
            glyph.GlyphBBox.XMin, glyph.GlyphBBox.XMax,
            glyph.GlyphBBox.YMin, glyph.GlyphBBox.YMax);
        Console.WriteLine(bbox);
        Console.WriteLine("Width:" + font.Metrics.GetGlyphWidth(new GlyphUInt32Id(glIndex)));
    }
}
```
## Következtetés
Ebben az oktatóanyagban bemutattuk, hogyan szerezhet be betűtípus-metrikákat az Aspose.Font for .NET használatával. A lépésenkénti útmutató követésével és az előfeltételek megértésével az Aspose.Font API segítségével hatékonyan dolgozhat a betűtípusokkal .NET-alkalmazásaiban.
## GYIK
### 1. Használhatom az Aspose.Font for .NET fájlt bármilyen betűtípus fájlformátummal?
Igen, az Aspose.Font for .NET támogatja a különféle betűtípusokat, például a TrueType-ot (TTF), az OpenType-ot (OTF) stb.
### 2. Elérhető ingyenes próbaverzió az Aspose.Font for .NET számára?
 Igen, letöltheti az Aspose.Font ingyenes próbaverzióját .NET-hez a[weboldal](https://releases.aspose.com/).
### 3. Hogyan érhetem el az Aspose.Font for .NET támogatását?
 Az Aspose.Font for .NET támogatását a következőn keresztül érheti el[fórum](https://forum.aspose.com/c/font/41).
### 4. Vásárolhatok ideiglenes licencet az Aspose.Font for .NET számára?
 Igen, vásárolhat ideiglenes licencet a[Aspose bolt](https://purchase.aspose.com/temporary-license/).
### 5. Elérhető az Aspose.Font for .NET dokumentációja?
 Igen, elérheti az Aspose.Font for .NET dokumentációját[itt](https://reference.aspose.com/font/net/).