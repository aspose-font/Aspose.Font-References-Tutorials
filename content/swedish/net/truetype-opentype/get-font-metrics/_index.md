---
title: Få Font Metrics i Aspose.Font för .NET
linktitle: Få Font Metrics i Aspose.Font för .NET
second_title: Aspose.Font .NET API
description: Lär dig hur du får teckensnittsstatistik med Aspose.Font för .NET. Steg-för-steg guide med kodexempel. Förutsättningar och vanliga frågor ingår. #Aspose #Teckensnitt
type: docs
weight: 12
url: /sv/net/truetype-opentype/get-font-metrics/
---
## Introduktion
Aspose.Font för .NET är ett kraftfullt API som låter utvecklare arbeta med typsnitt i sina .NET-applikationer. Oavsett om du behöver extrahera teckensnittsmått, manipulera glyfer eller komma åt teckensnittsdata, tillhandahåller Aspose.Font omfattande funktionalitet för att effektivisera teckensnittsrelaterade uppgifter. I den här handledningen kommer vi att utforska hur du får teckensnittsmått med Aspose.Font för .NET.
## Förutsättningar
Innan du dyker in i den här handledningen, se till att du har följande förutsättningar inställda:
### 1. Aspose.Font för .NET-installation
 Se till att du har Aspose.Font för .NET installerat i din utvecklingsmiljö. Om du inte redan har gjort det kan du ladda ner API:et från[Aspose.Releases](https://releases.aspose.com/font/net/) eller via NuGet-pakethanteraren.
### 2. Inställning av utvecklingsmiljö
Se till att du har en .NET-utvecklingsmiljö inställd med Visual Studio eller någon annan kompatibel IDE installerad.

## Importera namnområden
din .NET-applikation måste du importera de nödvändiga namnområdena för att fungera med Aspose.Font för .NET.
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
Låt oss nu dela upp exemplet i flera steg och förklara var och en i detalj.
## Steg 1: Definiera sökvägen för teckensnittsfilen
Först definierar du sökvägen för det teckensnitt du vill arbeta med.
```csharp
string dataDir = "Your Document Directory";
string fileName = dataDir + "Montserrat-Regular.ttf"; //Typsnittsfilnamn med fullständig sökväg
```
## Steg 2: Öppna teckensnittsfilen
Öppna sedan teckensnittsfilen med Aspose.Font API.
```csharp
FontDefinition fd = new FontDefinition(FontType.TTF, new FontFileDefinition("ttf", new FileSystemStreamSource(fileName)));
TtfFont font = Aspose.Font.Font.Open(fd) as TtfFont;
```
## Steg 3: Hämta teckensnittsstatistik
Hämta olika teckensnittsmått som stigande, nedstigande, etc.
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
## Steg 4: Skaffa Unicode-kodningstabell
Hämta Unicode-kodningstabellen (cmap) från teckensnittet.
```csharp
Aspose.Font.TtfCMapFormats.TtfCMapFormatBaseTable cmapTable = null;
if (font.TtfTables.CMapTable != null)
{
    cmapTable = font.TtfTables.CMapTable.FindUnicodeTable();
}
```
## Steg 5: Få åtkomst till Glyph Information
Få åtkomst till glyfinformation för en specifik symbol (t.ex. "A").
```csharp
char unicode = (char)65; // Unicode för "A"
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
## Slutsats
den här handledningen har vi täckt hur du får teckensnittsmått med Aspose.Font för .NET. Genom att följa steg-för-steg-guiden och förstå förutsättningarna kan du effektivt arbeta med typsnitt i dina .NET-applikationer med Aspose.Font API.
## FAQ's
### 1. Kan jag använda Aspose.Font för .NET med vilket typsnittsfilformat som helst?
Ja, Aspose.Font för .NET stöder olika teckensnittsformat som TrueType (TTF), OpenType (OTF) och mer.
### 2. Finns det en gratis testversion tillgänglig för Aspose.Font för .NET?
 Ja, du kan få en gratis provversion av Aspose.Font för .NET från[hemsida](https://releases.aspose.com/).
### 3. Hur får jag tillgång till support för Aspose.Font för .NET?
 Du kan få tillgång till support för Aspose.Font för .NET via[forum](https://forum.aspose.com/c/font/41).
### 4. Kan jag köpa en tillfällig licens för Aspose.Font för .NET?
 Ja, du kan köpa en tillfällig licens från[Aspose butik](https://purchase.aspose.com/temporary-license/).
### 5. Finns det dokumentation tillgänglig för Aspose.Font för .NET?
 Ja, du kan komma åt dokumentationen för Aspose.Font för .NET[här](https://reference.aspose.com/font/net/).