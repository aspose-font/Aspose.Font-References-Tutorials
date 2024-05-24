---
title: Extrahujte licenční omezení v Aspose.Font pro .NET
linktitle: Extrahujte licenční omezení v Aspose.Font pro .NET
second_title: Aspose.Font .NET API
description: Naučte se, jak extrahovat licenční omezení z písem TrueType pomocí Aspose.Font for .NET, s naším podrobným průvodcem. Ideální pro vývojáře pracující s fonty v .NET.
type: docs
weight: 11
url: /cs/net/truetype-opentype/extract-license-restrictions/
---
## Úvod
Nazdárek! Pokud jste vývojář pracující s písmy v aplikacích .NET, pochopení licenčních omezení vložených do souborů písem je zásadní. Tento komplexní průvodce vás provede extrahováním licenčních omezení z písem TrueType pomocí Aspose.Font pro .NET. Ať už zajišťujete soulad s licencováním písem nebo se jen zajímáte o oprávnění písem, která používáte, máme pro vás řešení. Na konci tohoto tutoriálu budete moci snadno zkontrolovat licenční omezení libovolného písma TrueType. Jste připraveni se ponořit? Začněme!
## Předpoklady
Než skočíme do kódu, ujistěte se, že máte následující:
-  Aspose.Font pro .NET: Stáhněte si jej z[Aspose stránku vydání](https://releases.aspose.com/font/net/).
- Vývojové prostředí .NET: Visual Studio nebo jakékoli jiné kompatibilní IDE.
- Základní znalost C#: Znalost programování v C# a frameworku .NET.
- Soubor písma: Soubor písem TrueType, jako např`Montserrat-Regular.ttf`.
## Importovat jmenné prostory
Chcete-li začít používat Aspose.Font pro .NET, budete muset importovat potřebné jmenné prostory. Tyto jmenné prostory vám poskytnou třídy a metody potřebné pro manipulaci s písmy.
```csharp
using Aspose.Font.Sources;
using Aspose.Font.Ttf;
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;
                        + " using the embedded font, and changes may be saved.");
```
Nyní si celý proces rozdělíme do jednoduchých kroků.
## Krok 1: Načtěte písmo TrueType
 Nejprve musíme do naší aplikace načíst písmo TrueType. To zahrnuje definování cesty k souboru a vytvoření a`FontDefinition` objekt.
## Krok 1.1: Zadejte cestu k souboru písem
Začněte zadáním adresáře, kde je umístěn soubor s písmem, a úplnou cestu k souboru.
```csharp
string dataDir = "Your Document Directory";
string fileName = dataDir + "Montserrat-Regular.ttf";
```
## Krok 1.2: Vytvořte objekt FontDefinition
 Dále vytvořte a`FontDefinition` objekt pro správu dat písem. Tento krok zahrnuje určení typu písma a zdroje souboru.
```csharp
FontDefinition fd = new FontDefinition(FontType.TTF, new FontFileDefinition("ttf", new FileSystemStreamSource(fileName)));
```
## Krok 2: Otevřete písmo TrueType
 s`FontDefinition` objekt připraven, dalším krokem je otevřít písmo pomocí Aspose.Font pro .NET.
## Krok 2.1: Použijte metodu Open
 Použijte`Open` metoda`Font` třídy pro načtení písma. Odešlete vrácený objekt do a`TtfFont`.
```csharp
TtfFont font = Aspose.Font.Font.Open(fd) as TtfFont;
```
## Krok 3: Extrahujte licenční omezení
Nyní, když je písmo načteno, je čas extrahovat licenční omezení. To zahrnuje přístup k tabulce OS/2 písma a načtení příznaků licence.
## Krok 3.1: Inicializujte licenční příznaky
 Inicializovat a`LicenseFlags` objekt pro uložení licenčních informací.
```csharp
LicenseFlags licenseFlags = null;
```
## Krok 3.2: Zkontrolujte tabulku OS/2
Zkontrolujte, zda tabulka OS/2 v písmu existuje, a pokud ano, získejte licenční příznaky.
```csharp
if (font.TtfTables.Os2Table != null)
{
    licenseFlags = font.TtfTables.Os2Table.GetLicenseFlags();
}
```
## Krok 3.3: Interpretace licenčních příznaků
Interpretujte licenční příznaky a vytiskněte licenční omezení na základě získaných příznaků.
```csharp
if (licenseFlags == null || licenseFlags.FSTypeAbsent)
{
    Console.WriteLine(string.Format("Font {0} has no embedded license restrictions", font.FontName));
}
else
{
    if (licenseFlags.IsEditableEmbedding)
    {
        Console.WriteLine(
            string.Format("Font {0} may be embedded, and may be temporarily loaded on other systems.", font.FontName)
            + " In addition, editing is permitted, including ability to format new text"
            + " using the embedded font, and changes may be saved.");
    }
    else if (licenseFlags.IsInstallableEmbedding)
    {
        Console.WriteLine(
            string.Format("Font {0} may be embedded, and may be permanently installed", font.FontName)
            + " for use on remote systems, or for use by other users.");
    }
    else if (licenseFlags.IsPreviewAndPrintEmbedding)
    {
        Console.WriteLine(
            string.Format("Font {0} may be embedded, and may be temporarily loaded", font.FontName)
            + " on other systems for purposes of viewing or printing the document.");
    }
    else if (licenseFlags.IsRestrictedLicenseEmbedding)
    {
        Console.WriteLine(
            string.Format("Font {0} must not be modified, embedded or exchanged in any manner", font.FontName)
            + " without first obtaining explicit permission of the legal owner.");
    }
}
```
## Závěr
A tady to máte! Úspěšně jste se naučili, jak extrahovat licenční omezení z písem TrueType pomocí Aspose.Font pro .NET. Tato příručka vás provede základními kroky potřebnými pro práci s písmy ve vašich aplikacích .NET a zajistí splnění licenčních požadavků. S těmito znalostmi můžete s jistotou spravovat písma ve svých projektech s vědomím, že dodržujete právní pokyny.
## FAQ
### 1. Co je Aspose.Font pro .NET?
Aspose.Font for .NET je výkonné API, které umožňuje vývojářům pracovat se soubory písem a umožňuje načítání, úpravy a ukládání písem v rámci aplikací .NET.
### 2. Mohu pomocí Aspose.Font for .NET pracovat s jinými formáty písem?
Absolutně! Aspose.Font for .NET podporuje různé formáty písem, mimo jiné včetně TTF, OTF, Type 1 a CFF.
### 3. Jak získám licenci pro Aspose.Font pro .NET?
 Licenci si můžete zakoupit od[Aspose Nákup stránky](https://purchase.aspose.com/buy) . Pro účely hodnocení můžete získat dočasnou licenci[tady](https://purchase.aspose.com/temporary-license/).
### 4. Kde najdu podrobnou dokumentaci?
 Podrobná dokumentace je k dispozici na[Stránka dokumentace Aspose.Font for .NET](https://reference.aspose.com/font/net/).
### 5. Jak mohu získat podporu, pokud narazím na problémy?
 Pro podporu můžete navštívit[Fórum podpory Aspose.Font](https://forum.aspose.com/c/font/41).