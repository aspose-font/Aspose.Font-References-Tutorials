---
title: Získejte metriky písem v Aspose.Font pro .NET
linktitle: Získejte metriky písem v Aspose.Font pro .NET
second_title: Aspose.Font .NET API
description: Naučte se, jak získat metriky písem pomocí Aspose.Font pro .NET. Podrobný průvodce s příklady kódu. Předpoklady a FAQ v ceně. #Apose #Písmo
type: docs
weight: 12
url: /cs/net/truetype-opentype/get-font-metrics/
---
## Úvod
Aspose.Font for .NET je výkonné API, které umožňuje vývojářům pracovat s fonty v jejich aplikacích .NET. Ať už potřebujete extrahovat metriky písem, manipulovat s glyfy nebo přistupovat k datům písem, Aspose.Font poskytuje komplexní funkce pro zefektivnění úloh souvisejících s písmy. V tomto tutoriálu prozkoumáme, jak získat metriky písem pomocí Aspose.Font pro .NET.
## Předpoklady
Než se pustíte do tohoto výukového programu, ujistěte se, že máte nastaveny následující předpoklady:
### 1. Aspose.Font pro instalaci .NET
 Ujistěte se, že máte ve vývojovém prostředí nainstalovaný Aspose.Font for .NET. Pokud jste tak ještě neučinili, můžete si API stáhnout z[Aspose.Releases](https://releases.aspose.com/font/net/) nebo prostřednictvím správce balíčků NuGet.
### 2. Nastavení vývojového prostředí
Ujistěte se, že máte nainstalované vývojové prostředí .NET s Visual Studio nebo jiným kompatibilním IDE.

## Importovat jmenné prostory
Ve vaší aplikaci .NET musíte importovat potřebné jmenné prostory pro práci s Aspose.Font pro .NET.
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
Nyní si uvedený příklad rozdělíme do několika kroků a každý z nich podrobně vysvětlíme.
## Krok 1: Definujte cestu k souboru písem
Nejprve definujte cestu k souboru písma, se kterým chcete pracovat.
```csharp
string dataDir = "Your Document Directory";
string fileName = dataDir + "Montserrat-Regular.ttf"; //Název souboru písma s úplnou cestou
```
## Krok 2: Otevřete soubor písma
Dále otevřete soubor písma pomocí Aspose.Font API.
```csharp
FontDefinition fd = new FontDefinition(FontType.TTF, new FontFileDefinition("ttf", new FileSystemStreamSource(fileName)));
TtfFont font = Aspose.Font.Font.Open(fd) as TtfFont;
```
## Krok 3: Načtěte metriky písem
Načíst různé metriky písem, jako je ascender, descender atd.
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
## Krok 4: Získejte tabulku kódování Unicode
Načtěte tabulku kódování Unicode (cmap) z písma.
```csharp
Aspose.Font.TtfCMapFormats.TtfCMapFormatBaseTable cmapTable = null;
if (font.TtfTables.CMapTable != null)
{
    cmapTable = font.TtfTables.CMapTable.FindUnicodeTable();
}
```
## Krok 5: Přístup k informacím o glyfu
Přístup k informacím o glyfu pro konkrétní symbol (např. 'A').
```csharp
char unicode = (char)65; // Unicode pro „A“
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
## Závěr
tomto tutoriálu jsme se zabývali tím, jak získat metriky písem pomocí Aspose.Font pro .NET. Pokud budete postupovat podle podrobného průvodce a porozumíte předpokladům, můžete efektivně pracovat s fonty ve vašich aplikacích .NET pomocí Aspose.Font API.
## FAQ
### 1. Mohu použít Aspose.Font pro .NET s jakýmkoli formátem souboru písem?
Ano, Aspose.Font for .NET podporuje různé formáty písem, jako je TrueType (TTF), OpenType (OTF) a další.
### 2. Je k dispozici bezplatná zkušební verze pro Aspose.Font pro .NET?
 Ano, můžete získat bezplatnou zkušební verzi Aspose.Font pro .NET od[webová stránka](https://releases.aspose.com/).
### 3. Jak mohu získat přístup k podpoře pro Aspose.Font pro .NET?
 K podpoře Aspose.Font pro .NET můžete přistupovat prostřednictvím[Fórum](https://forum.aspose.com/c/font/41).
### 4. Mohu si zakoupit dočasnou licenci pro Aspose.Font pro .NET?
 Ano, můžete si zakoupit dočasnou licenci od[Aspose obchod](https://purchase.aspose.com/temporary-license/).
### 5. Je k dispozici dokumentace pro Aspose.Font pro .NET?
 Ano, máte přístup k dokumentaci pro Aspose.Font pro .NET[tady](https://reference.aspose.com/font/net/).