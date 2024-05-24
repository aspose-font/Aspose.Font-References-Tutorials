---
title: Získejte metriky písem v Aspose.Font pro .NET Type 1
linktitle: Získejte metriky písem v Aspose.Font pro .NET Type 1
second_title: Aspose.Font .NET API
description: Naučte se, jak získat metriky písem pomocí Aspose.Font pro .NET v tomto komplexním, podrobném tutoriálu. Ideální pro vývojáře na jakékoli úrovni!
type: docs
weight: 11
url: /cs/net/aspose-font-net-type1-font/get-font-metrics-aspose-font-net-type1/
---
## Úvod
Vítejte v dokonalém průvodci získáváním metrik písem pomocí Aspose.Font pro .NET! Ať už jste ostřílený vývojář nebo jen ponoříte prsty do světa písem, tento tutoriál vás provede procesem krok za krokem. Na konci tohoto článku budete schopni extrahovat podrobné metriky písem a pochopit, jak s nimi manipulovat v rámci vašich aplikací .NET. Pojďme se tedy ponořit a začít s touto vzrušující cestou!
## Předpoklady
Než se ponoříme do toho nejzákladnějšího, je potřeba mít připraveno několik věcí:
- Visual Studio: Ujistěte se, že máte na svém počítači nainstalované Visual Studio.
-  Aspose.Font for .NET: Stáhněte si a nainstalujte knihovnu Aspose.Font for .NET. Můžete to získat z[odkaz ke stažení](https://releases.aspose.com/font/net/).
- Základní znalost C#: Znalost programování v C# je nutné dodržovat spolu s příklady.
- Soubor písem: Připravte si soubor písem TrueType (.ttf). Pro tento tutoriál můžete použít jakýkoli soubor .ttf.
Nyní, když máme vše připraveno, začněme importem potřebných jmenných prostorů.
## Importovat jmenné prostory
Chcete-li začít pracovat s Aspose.Font pro .NET, budete muset do svého projektu zahrnout příslušné jmenné prostory. Postup je následující:
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
S těmito jmennými prostory jste připraveni začít pracovat s písmy ve vaší aplikaci .NET.
## Krok 1: Načtěte soubor písma
Nejprve musíte načíst soubor písma do aplikace. Takto to uděláte:
### Načíst soubor písma
1. Definujte cestu k souboru s písmem. 
2.  Vytvořit`FontDefinition` objekt.
3.  Použijte`Font.Open` způsob načtení písma.
```csharp
string dataDir = "Your Document Directory";
string fileName = dataDir + "Montserrat-Regular.ttf";
FontDefinition fd = new FontDefinition(FontType.TTF, new FontFileDefinition("ttf", new FileSystemStreamSource(fileName)));
TtfFont font = Aspose.Font.Font.Open(fd) as TtfFont;
```
 Zde používáme`FontDefinition` třídy k definování typu a umístění našeho souboru písem. The`Font.Open` metoda načte písmo do a`TtfFont` objekt.
## Krok 2: Načtěte základní informace o písmu
Jakmile je písmo načteno, můžete o něm získat některé základní informace.
### Získejte název písma a počet glyfů
```csharp
string name = font.FontName;
Console.WriteLine("Font name: " + name);
Console.WriteLine("Glyph count: " + font.NumGlyphs);
```
Tento fragment kódu vytiskne název písma a počet glyfů, které obsahuje.
## Krok 3: Extrahujte metriky písma
Metriky písma poskytují podrobné informace o vlastnostech písma.
### Zobrazit metriky písma
```csharp
string metrics = string.Format(
    "Font metrics: ascender - {0}, descender - {1}, typo ascender = {2}, typo descender = {3}, UnitsPerEm = {4}",
    font.Metrics.Ascender, font.Metrics.Descender,
    font.Metrics.TypoAscender, font.Metrics.TypoDescender, font.Metrics.UnitsPerEM);
Console.WriteLine(metrics);
```
Tento úryvek formátuje a tiskne různé metriky písma, jako je ascender, descender a jednotky na EM.
## Krok 4: Přístup k tabulce Unicode CMap
Tabulka CMap pomáhá při mapování kódů znaků na indexy glyfů.
### Načtěte a zkontrolujte tabulku Cmap
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
Tento kód načte tabulku CMap a vytiskne PlatformID a PlatformSpecificID.
## Krok 5: Získejte informace o glyfech
Nakonec načteme informace o konkrétním glyfu, jako je glyf pro znak 'A'.
### Načíst informace o glyfech
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
Tento úryvek získá index glyfu pro 'A', načte glyf pomocí tohoto indexu a vytiskne jeho metriky, včetně ohraničovacího rámečku a šířky.
## Závěr
Gratulujeme! Úspěšně jste se naučili, jak získat metriky písem pomocí Aspose.Font pro .NET. Pomocí těchto kroků můžete snadno extrahovat a manipulovat s informacemi o písmech ve vašich aplikacích. Tento tutoriál by měl poskytnout pevný základ pro pokročilejší operace s písmy. Šťastné kódování!
## FAQ
### Q1: Mohu použít Aspose.Font pro .NET s jinými formáty písem?
Ano, Aspose.Font for .NET podporuje různé formáty písem včetně TrueType, OpenType, Type1 a dalších.
### Q2: Kde mohu získat bezplatnou zkušební verzi Aspose.Font pro .NET?
 Můžete si stáhnout bezplatnou zkušební verzi z[Aspose stránku vydání](https://releases.aspose.com/).
### Q3: Jak si koupím licenci pro Aspose.Font for .NET?
 Licenci si můžete zakoupit od[Aspose nákupní stránku](https://purchase.aspose.com/buy).
### Q4: Je k dispozici podpora pro Aspose.Font pro .NET?
 Ano, můžete získat podporu od[Aspose fórum podpory](https://forum.aspose.com/c/font/41).
### Q5: Mohu použít Aspose.Font pro .NET v komerčním projektu?
Ano, Aspose.Font for .NET můžete používat v komerčních projektech, ale budete potřebovat platnou licenci.