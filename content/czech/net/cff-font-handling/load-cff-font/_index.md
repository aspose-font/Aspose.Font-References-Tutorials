---
title: Načtěte písmo CFF v Aspose.Font pro .NET
linktitle: Načtěte písmo CFF v Aspose.Font pro .NET
second_title: Aspose.Font .NET API
description: V této příručce se dozvíte, jak načíst písma CFF pomocí Aspose.Font for .NET. Ideální pro vývojáře, kteří chtějí vylepšit své aplikace .NET pomocí vlastních písem.
type: docs
weight: 10
url: /cs/net/cff-font-handling/load-cff-font/
---
## Úvod
Vítejte v průvodci načítáním písem CFF (Compact Font Format) pomocí Aspose.Font pro .NET! Pokud chcete do svých aplikací .NET začlenit vlastní písma, jste na správném místě. Tento podrobný návod vás provede celým procesem, od nastavení prostředí až po extrahování podrobných metrik písem. Na konci této příručky budete mít solidní přehled o práci s písmy CFF, díky čemuž budou vaše projekty vynikat jedinečnými typografickými prvky. Jste připraveni se ponořit? Začněme!
## Předpoklady
Než se ponoříme do kódu, ujistěte se, že máte vše, co potřebujete:
- Visual Studio: Ujistěte se, že máte nainstalované Visual Studio.
- Aspose.Font for .NET: Stáhněte si a nainstalujte knihovnu Aspose.Font for .NET z[odkaz ke stažení](https://releases.aspose.com/font/net/).
- Základní znalost C#: Znalost C# vám pomůže postupovat podle příkladů.
- Soubor písem CFF: Připravte si soubor ve formátu Compact Font Format (.cff). Pro tento tutoriál můžete použít jakýkoli soubor .cff.
Po pokrytí těchto předpokladů přejděme k potřebným jmenným prostorům.
## Importovat jmenné prostory
Chcete-li pracovat s Aspose.Font pro .NET, budete muset do projektu zahrnout příslušné jmenné prostory. Postup je následující:
```csharp
using Aspose.Font.Cff;
using Aspose.Font.Sources;
using System;
using System.Collections.Generic;
using System.IO;
using System.Linq;
using System.Text;
using System.Threading.Tasks;
```
Tyto jmenné prostory jsou nezbytné pro práci s písmy ve vaší aplikaci .NET.
## Krok 1: Načtěte soubor písma
Prvním krokem je načtení souboru písma CFF do vaší aplikace. Zde je postup:
### Načíst soubor písma
1. Definujte cestu k souboru s písmem.
2.  Vytvořit`FontDefinition` objekt.
3.  Použijte`Font.Open` způsob načtení písma.
```csharp
string dataDir = "Your Document Directory";
string fileName = dataDir + "OpenSans-Regular.cff";
FontDefinition fd = new FontDefinition(FontType.CFF, new FontFileDefinition("cff", new FileSystemStreamSource(fileName)));
CffFont cffFont = Aspose.Font.Font.Open(fd) as CffFont;
```
 V tomto úryvku definujeme typ a umístění písma pomocí`FontDefinition` třídy a poté načtěte písmo do a`CffFont` objekt pomocí`Font.Open` metoda.
## Krok 2: Načtěte základní informace o písmu
Jakmile je písmo načteno, můžete o něm získat některé základní informace.
### Získejte název písma a počet glyfů
```csharp
string name = cffFont.FontName;
Console.WriteLine("Font name: " + name);
Console.WriteLine("Glyph count: " + cffFont.NumGlyphs);
```
Tento úryvek vytiskne název písma a počet glyfů, které obsahuje, což vám poskytne rychlý přehled o načteném písmu.
## Krok 3: Extrahujte metriky písma
Metriky písma poskytují podrobné informace o vlastnostech písma.
### Zobrazit metriky písma
```csharp
string metrics = string.Format(
    "Font metrics: ascender - {0}, descender - {1}, units per em = {2}",
    cffFont.Metrics.Ascender, cffFont.Metrics.Descender, cffFont.Metrics.UnitsPerEM);
Console.WriteLine(metrics);
```
Tento kód naformátuje a vytiskne různé metriky písma, jako je ascender, descender a jednotky na EM, čímž získáte přehled o rozměrech písma.
## Krok 4: Přístup k glyfům písem
Glyfy jsou vizuální reprezentace znaků. Pojďme načíst informace o konkrétním glyfu, jako je glyf pro znak 'A'.
### Načíst informace o glyfech
```csharp
//Za předpokladu, že písmo má metodu, jak získat glyf podle znaku nebo indexu
int glyphIndex = cffFont.GetGlyphIndex('A');
if (glyphIndex >= 0)
{
    Glyph glyph = cffFont.GetGlyphById(glyphIndex);
    if (glyph != null)
    {
        Console.WriteLine("Glyph metrics for 'A' symbol:");
        string bbox = string.Format(
            "Glyph BBox: Xmin = {0}, Xmax = {1}, Ymin = {2}, Ymax = {3}",
            glyph.GlyphBBox.XMin, glyph.GlyphBBox.XMax, glyph.GlyphBBox.YMin, glyph.GlyphBBox.YMax);
        Console.WriteLine(bbox);
        Console.WriteLine("Width: " + cffFont.Metrics.GetGlyphWidth(glyphIndex));
    }
}
```
Tento úryvek načte index glyfu pro 'A', získá glyf pomocí tohoto indexu a vytiskne jeho metriky, včetně ohraničovacího rámečku a šířky.
## Krok 5: Práce s tabulkami písem
Tabulky písem obsahují různé údaje o písmu. U písem CFF by vás mohly zajímat tabulky jako tabulka CharStrings.
### Přístup a zobrazení tabulek písem
```csharp
var charStringsTable = cffFont.CFFTables.CharStrings;
if (charStringsTable != null)
{
    foreach (var entry in charStringsTable.Entries)
    {
        Console.WriteLine($"Glyph name: {entry.Key}, Glyph data: {entry.Value}");
    }
}
```
Tento úryvek přistupuje k tabulce CharStrings a vytiskne každý název glyfu spolu s jeho daty, což vám umožní hlouběji porozumět struktuře písma.
## Závěr
Gratulujeme! Úspěšně jste se naučili, jak načíst a zacházet s CFF fonty pomocí Aspose.Font pro .NET. Pomocí těchto kroků můžete snadno integrovat vlastní písma do svých aplikací .NET, čímž zvýšíte jejich vizuální přitažlivost a funkčnost. Ať už pracujete na projektech digitálního designu, vyvíjíte software nebo cokoli mezi tím, zvládnutí manipulace s písmy je cenná dovednost. Šťastné kódování!
## FAQ
### Q1: Mohu použít Aspose.Font pro .NET s jinými formáty písem?
Ano, Aspose.Font for .NET podporuje různé formáty písem včetně TrueType, OpenType a Type1.
### Q2: Kde mohu získat bezplatnou zkušební verzi Aspose.Font pro .NET?
 Můžete si stáhnout bezplatnou zkušební verzi z[Aspose stránku vydání](https://releases.aspose.com/).
### Q3: Jak si koupím licenci pro Aspose.Font for .NET?
 Licenci si můžete zakoupit od[Aspose nákupní stránku](https://purchase.aspose.com/buy).
### Q4: Je k dispozici podpora pro Aspose.Font pro .NET?
 Ano, můžete získat podporu od[Aspose fórum podpory](https://forum.aspose.com/c/font/41).
### Q5: Mohu použít Aspose.Font pro .NET v komerčním projektu?
Ano, Aspose.Font for .NET můžete používat v komerčních projektech, ale budete potřebovat platnou licenci.
