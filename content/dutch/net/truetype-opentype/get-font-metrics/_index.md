---
title: Haal lettertypestatistieken op in Aspose.Font voor .NET
linktitle: Haal lettertypestatistieken op in Aspose.Font voor .NET
second_title: Aspose.Font .NET API
description: Leer hoe u lettertypestatistieken kunt verkrijgen met Aspose.Font voor .NET. Stapsgewijze handleiding met codevoorbeelden. Vereisten en veelgestelde vragen inbegrepen. #Aspose #Lettertype
type: docs
weight: 12
url: /nl/net/truetype-opentype/get-font-metrics/
---
## Invoering
Aspose.Font voor .NET is een krachtige API waarmee ontwikkelaars met lettertypen in hun .NET-applicaties kunnen werken. Of u nu lettertypegegevens moet extraheren, glyphs moet manipuleren of toegang moet krijgen tot lettertypegegevens, Aspose.Font biedt uitgebreide functionaliteit om lettertypegerelateerde taken te stroomlijnen. In deze zelfstudie onderzoeken we hoe u lettertypestatistieken kunt verkrijgen met Aspose.Font voor .NET.
## Vereisten
Voordat u in deze zelfstudie duikt, moet u ervoor zorgen dat u aan de volgende vereisten voldoet:
### 1. Aspose.Font voor .NET-installatie
 Zorg ervoor dat Aspose.Font voor .NET in uw ontwikkelomgeving is geïnstalleerd. Als u dat nog niet heeft gedaan, kunt u de API downloaden van de[Aspose.Releases](https://releases.aspose.com/font/net/) of via NuGet-pakketbeheerder.
### 2. Installatie van de ontwikkelomgeving
Zorg ervoor dat u een .NET-ontwikkelomgeving hebt ingesteld waarop Visual Studio of een andere compatibele IDE is geïnstalleerd.

## Naamruimten importeren
In uw .NET-toepassing moet u de benodigde naamruimten importeren om met Aspose.Font voor .NET te kunnen werken.
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
Laten we nu het gegeven voorbeeld in meerdere stappen opsplitsen en elke stap in detail uitleggen.
## Stap 1: Definieer het lettertypebestandspad
Definieer eerst het bestandspad van het lettertype waarmee u wilt werken.
```csharp
string dataDir = "Your Document Directory";
string fileName = dataDir + "Montserrat-Regular.ttf"; //Lettertypebestandsnaam met volledig pad
```
## Stap 2: Open het lettertypebestand
Open vervolgens het lettertypebestand met de Aspose.Font API.
```csharp
FontDefinition fd = new FontDefinition(FontType.TTF, new FontFileDefinition("ttf", new FileSystemStreamSource(fileName)));
TtfFont font = Aspose.Font.Font.Open(fd) as TtfFont;
```
## Stap 3: Lettertypestatistieken ophalen
Haal verschillende lettertypestatistieken op, zoals oplopend, aflopend, enz.
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
## Stap 4: Haal de Unicode-coderingstabel op
Haal de Unicode-coderingstabel (cmap) op uit het lettertype.
```csharp
Aspose.Font.TtfCMapFormats.TtfCMapFormatBaseTable cmapTable = null;
if (font.TtfTables.CMapTable != null)
{
    cmapTable = font.TtfTables.CMapTable.FindUnicodeTable();
}
```
## Stap 5: Toegang tot Glyph-informatie
Krijg toegang tot glyph-informatie voor een specifiek symbool (bijvoorbeeld 'A').
```csharp
char unicode = (char)65; // Unicode voor 'A'
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
## Conclusie
In deze zelfstudie hebben we besproken hoe u lettertypestatistieken kunt verkrijgen met Aspose.Font voor .NET. Door de stapsgewijze handleiding te volgen en de vereisten te begrijpen, kunt u efficiënt met lettertypen in uw .NET-toepassingen werken met behulp van de Aspose.Font API.
## Veelgestelde vragen
### 1. Kan ik Aspose.Font voor .NET gebruiken met elk lettertypebestandsformaat?
Ja, Aspose.Font voor .NET ondersteunt verschillende lettertypeformaten, zoals TrueType (TTF), OpenType (OTF) en meer.
### 2. Is er een gratis proefversie beschikbaar voor Aspose.Font voor .NET?
 Ja, u kunt een gratis proefversie van Aspose.Font voor .NET krijgen van de[website](https://releases.aspose.com/).
### 3. Hoe krijg ik toegang tot ondersteuning voor Aspose.Font voor .NET?
 U kunt toegang krijgen tot ondersteuning voor Aspose.Font voor .NET via de[forum](https://forum.aspose.com/c/font/41).
### 4. Kan ik een tijdelijke licentie kopen voor Aspose.Font voor .NET?
 Ja, u kunt een tijdelijke licentie aanschaffen bij de[Aspose-winkel](https://purchase.aspose.com/temporary-license/).
### 5. Is er documentatie beschikbaar voor Aspose.Font voor .NET?
 Ja, u heeft toegang tot de documentatie voor Aspose.Font voor .NET[hier](https://reference.aspose.com/font/net/).