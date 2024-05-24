---
title: Haal lettertypestatistieken op in Aspose.Font voor .NET Type 1
linktitle: Haal lettertypestatistieken op in Aspose.Font voor .NET Type 1
second_title: Aspose.Font .NET API
description: Leer hoe u lettertypestatistieken kunt verkrijgen met Aspose.Font voor .NET in deze uitgebreide, stapsgewijze zelfstudie. Perfect voor ontwikkelaars op elk niveau!
type: docs
weight: 11
url: /nl/net/aspose-font-net-type1-font/get-font-metrics-aspose-font-net-type1/
---
## Invoering
Welkom bij de ultieme gids voor het verkrijgen van lettertypestatistieken met Aspose.Font voor .NET! Of je nu een doorgewinterde ontwikkelaar bent of gewoon je verdiepen in de wereld van lettertypen, deze tutorial begeleidt je stap voor stap door het proces. Aan het einde van dit artikel kunt u gedetailleerde lettertypegegevens extraheren en begrijpen hoe u deze binnen uw .NET-toepassingen kunt manipuleren. Dus laten we erin duiken en aan de slag gaan met deze spannende reis!
## Vereisten
Voordat we in de kern duiken, zijn er een paar dingen die je moet regelen:
- Visual Studio: Zorg ervoor dat Visual Studio op uw computer is geïnstalleerd.
-  Aspose.Font voor .NET: Download en installeer de Aspose.Font voor .NET-bibliotheek. U kunt deze verkrijgen bij de[download link](https://releases.aspose.com/font/net/).
- Basiskennis van C#: Bekendheid met programmeren in C# is noodzakelijk om de voorbeelden te volgen.
- Een lettertypebestand: Zorg ervoor dat u een TrueType-lettertypebestand (.ttf) bij de hand hebt. Voor deze zelfstudie kunt u elk .ttf-bestand gebruiken.
Nu we alles gereed hebben, gaan we beginnen met het importeren van de benodigde naamruimten.
## Naamruimten importeren
Om met Aspose.Font voor .NET te gaan werken, moet u de juiste naamruimten in uw project opnemen. Zo doe je het:
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
Met deze naamruimten kunt u aan de slag met lettertypen in uw .NET-toepassing.
## Stap 1: Laad het lettertypebestand
Eerst moet u het lettertypebestand in uw toepassing laden. Zo doe je het:
### Lettertypebestand laden
1. Definieer het pad naar uw lettertypebestand. 
2.  Maak een`FontDefinition` voorwerp.
3.  Gebruik de`Font.Open` methode om het lettertype te laden.
```csharp
string dataDir = "Your Document Directory";
string fileName = dataDir + "Montserrat-Regular.ttf";
FontDefinition fd = new FontDefinition(FontType.TTF, new FontFileDefinition("ttf", new FileSystemStreamSource(fileName)));
TtfFont font = Aspose.Font.Font.Open(fd) as TtfFont;
```
 Hier gebruiken we de`FontDefinition` class om het type en de locatie van ons lettertypebestand te definiëren. De`Font.Open` methode laadt het lettertype in a`TtfFont` voorwerp.
## Stap 2: Basislettertype-informatie ophalen
Zodra het lettertype is geladen, kunt u er basisinformatie over ophalen.
### Ontvang de lettertypenaam en het aantal glyphs
```csharp
string name = font.FontName;
Console.WriteLine("Font name: " + name);
Console.WriteLine("Glyph count: " + font.NumGlyphs);
```
Dit codefragment drukt de naam van het lettertype af en het aantal glyphs dat het bevat.
## Stap 3: Lettertypestatistieken extraheren
Lettertypestatistieken bieden gedetailleerde informatie over de kenmerken van het lettertype.
### Lettertypestatistieken weergeven
```csharp
string metrics = string.Format(
    "Font metrics: ascender - {0}, descender - {1}, typo ascender = {2}, typo descender = {3}, UnitsPerEm = {4}",
    font.Metrics.Ascender, font.Metrics.Descender,
    font.Metrics.TypoAscender, font.Metrics.TypoDescender, font.Metrics.UnitsPerEM);
Console.WriteLine(metrics);
```
Met dit fragment worden verschillende statistieken van het lettertype opgemaakt en afgedrukt, zoals oplopend, aflopend en eenheden per EM.
## Stap 4: Open de CMap Unicode-tabel
De CMap-tabel helpt bij het toewijzen van tekencodes aan glyph-indices.
### CMap-tabel ophalen en controleren
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
Deze code haalt de CMap-tabel op en drukt de PlatformID en PlatformSpecificID af.
## Stap 5: Krijg Glyph-informatie
Laten we tot slot informatie ophalen over een specifieke glyph, zoals de glyph voor het teken 'A'.
### Glyph-informatie ophalen
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
Dit fragment haalt de glyph-index voor 'A' op, haalt de glyph op met behulp van deze index en drukt de bijbehorende statistieken af, inclusief het selectiekader en de breedte.
## Conclusie
Gefeliciteerd! U hebt met succes geleerd hoe u lettertypestatistieken kunt verkrijgen met Aspose.Font voor .NET. Door deze stappen te volgen, kunt u eenvoudig lettertype-informatie in uw toepassingen extraheren en manipuleren. Deze tutorial zou een solide basis moeten bieden voor geavanceerdere lettertypebewerkingen. Veel codeerplezier!
## Veelgestelde vragen
### V1: Kan ik Aspose.Font voor .NET gebruiken met andere lettertypeformaten?
Ja, Aspose.Font voor .NET ondersteunt verschillende lettertypeformaten, waaronder TrueType, OpenType, Type1 en meer.
### V2: Waar kan ik een gratis proefversie van Aspose.Font voor .NET krijgen?
 U kunt een gratis proefversie downloaden van de[Aspose-releasespagina](https://releases.aspose.com/).
### V3: Hoe koop ik een licentie voor Aspose.Font voor .NET?
 U kunt een licentie aanschaffen bij de[Aspose aankooppagina](https://purchase.aspose.com/buy).
### V4: Is er ondersteuning beschikbaar voor Aspose.Font voor .NET?
 Ja, u kunt ondersteuning krijgen van de[Aspose-ondersteuningsforum](https://forum.aspose.com/c/font/41).
### V5: Kan ik Aspose.Font voor .NET gebruiken in een commercieel project?
Ja, u kunt Aspose.Font voor .NET gebruiken in commerciële projecten, maar u heeft hiervoor een geldige licentie nodig.