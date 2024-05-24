---
title: Få Font Metrics i Aspose.Font för .NET Type 1
linktitle: Få Font Metrics i Aspose.Font för .NET Type 1
second_title: Aspose.Font .NET API
description: Lär dig hur du får teckensnittsstatistik med Aspose.Font för .NET i denna omfattande, steg-för-steg handledning. Perfekt för utvecklare på alla nivåer!
type: docs
weight: 11
url: /sv/net/aspose-font-net-type1-font/get-font-metrics-aspose-font-net-type1/
---
## Introduktion
Välkommen till den ultimata guiden för att få teckensnittsmått med Aspose.Font för .NET! Oavsett om du är en erfaren utvecklare eller bara doppar tårna i teckensnittsvärlden, kommer den här handledningen att leda dig genom processen steg-för-steg. I slutet av den här artikeln kommer du att kunna extrahera detaljerade teckensnittsmått och förstå hur du manipulerar dem i dina .NET-program. Så låt oss dyka in och komma igång med denna spännande resa!
## Förutsättningar
Innan vi dyker in i det nitty-gritty, finns det några saker du måste ha på plats:
- Visual Studio: Se till att du har Visual Studio installerat på din dator.
-  Aspose.Font för .NET: Ladda ner och installera Aspose.Font för .NET-biblioteket. Du kan få det från[nedladdningslänk](https://releases.aspose.com/font/net/).
- Grundläggande kunskaper i C#: Förtrogenhet med C#-programmering är nödvändig för att följa exemplen.
- En teckensnittsfil: Ha en TrueType-teckensnittsfil (.ttf) redo. Du kan använda vilken .ttf-fil som helst för den här handledningen.
Nu när vi har allt klart, låt oss börja med att importera de nödvändiga namnrymden.
## Importera namnområden
För att börja arbeta med Aspose.Font för .NET måste du inkludera lämpliga namnområden i ditt projekt. Så här gör du:
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
Med dessa namnrymder på plats är du redo att börja arbeta med teckensnitt i ditt .NET-program.
## Steg 1: Ladda teckensnittsfilen
Först måste du ladda teckensnittsfilen i din applikation. Så här gör du:
### Ladda teckensnittsfil
1. Definiera sökvägen till din typsnittsfil. 
2.  Skapa en`FontDefinition` objekt.
3.  Använd`Font.Open` metod för att ladda typsnittet.
```csharp
string dataDir = "Your Document Directory";
string fileName = dataDir + "Montserrat-Regular.ttf";
FontDefinition fd = new FontDefinition(FontType.TTF, new FontFileDefinition("ttf", new FileSystemStreamSource(fileName)));
TtfFont font = Aspose.Font.Font.Open(fd) as TtfFont;
```
 Här använder vi`FontDefinition` klass för att definiera typen och platsen för vår teckensnittsfil. De`Font.Open` metoden laddar typsnittet i en`TtfFont` objekt.
## Steg 2: Hämta grundläggande teckensnittsinformation
När typsnittet har laddats kan du hämta lite grundläggande information om det.
### Hämta teckensnittsnamn och antal tecken
```csharp
string name = font.FontName;
Console.WriteLine("Font name: " + name);
Console.WriteLine("Glyph count: " + font.NumGlyphs);
```
Detta kodavsnitt kommer att skriva ut teckensnittsnamnet och antalet glyfer som det innehåller.
## Steg 3: Extrahera teckensnittsmått
Teckensnittsmått ger detaljerad information om teckensnittets egenskaper.
### Visa teckensnittsstatistik
```csharp
string metrics = string.Format(
    "Font metrics: ascender - {0}, descender - {1}, typo ascender = {2}, typo descender = {3}, UnitsPerEm = {4}",
    font.Metrics.Ascender, font.Metrics.Descender,
    font.Metrics.TypoAscender, font.Metrics.TypoDescender, font.Metrics.UnitsPerEM);
Console.WriteLine(metrics);
```
Det här utdraget formaterar och skriver ut olika mätvärden för teckensnittet, till exempel stigande, nedstigande och enheter per EM.
## Steg 4: Gå till CMap Unicode-tabellen
CMap-tabellen hjälper till att mappa teckenkoder till glyfindex.
### Hämta och kontrollera CMap-tabellen
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
Denna kod hämtar CMap-tabellen och skriver ut PlatformID och PlatformSpecificID.
## Steg 5: Få glyph-information
Slutligen, låt oss hämta information om en specifik glyf, till exempel glyfen för tecknet "A".
### Hämta glyfinformation
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
Det här utdraget hämtar glyfindexet för "A", hämtar glyfen med detta index och skriver ut dess mätvärden, inklusive begränsningsram och bredd.
## Slutsats
Grattis! Du har framgångsrikt lärt dig hur du får teckensnittsmått med Aspose.Font för .NET. Genom att följa dessa steg kan du enkelt extrahera och manipulera teckensnittsinformation i dina applikationer. Denna handledning bör ge en solid grund för mer avancerade teckensnittsoperationer. Glad kodning!
## FAQ's
### F1: Kan jag använda Aspose.Font för .NET med andra teckensnittsformat?
Ja, Aspose.Font för .NET stöder olika teckensnittsformat inklusive TrueType, OpenType, Type1 och mer.
### F2: Var kan jag få en gratis provversion av Aspose.Font för .NET?
 Du kan ladda ner en gratis testversion från[Aspose releaser sida](https://releases.aspose.com/).
### F3: Hur köper jag en licens för Aspose.Font för .NET?
 Du kan köpa en licens från[Aspose köpsida](https://purchase.aspose.com/buy).
### F4: Finns det stöd tillgängligt för Aspose.Font för .NET?
 Ja, du kan få stöd från[Aspose supportforum](https://forum.aspose.com/c/font/41).
### F5: Kan jag använda Aspose.Font för .NET i ett kommersiellt projekt?
Ja, du kan använda Aspose.Font för .NET i kommersiella projekt, men du behöver en giltig licens.