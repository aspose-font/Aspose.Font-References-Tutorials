---
title: Uzyskaj metryki czcionek w Aspose.Font dla .NET
linktitle: Uzyskaj metryki czcionek w Aspose.Font dla .NET
second_title: Aspose.Font API .NET
description: Dowiedz się, jak uzyskać metryki czcionek za pomocą Aspose.Font dla .NET. Przewodnik krok po kroku z przykładami kodu. Zawiera wymagania wstępne i często zadawane pytania. #Aspose #Czcionka
type: docs
weight: 12
url: /pl/net/truetype-opentype/get-font-metrics/
---
## Wstęp
Aspose.Font dla .NET to potężny interfejs API, który umożliwia programistom pracę z czcionkami w aplikacjach .NET. Niezależnie od tego, czy chcesz wyodrębnić metryki czcionek, manipulować glifami, czy uzyskać dostęp do danych czcionek, Aspose.Font zapewnia wszechstronną funkcjonalność usprawniającą zadania związane z czcionkami. W tym samouczku omówimy, jak uzyskać metryki czcionek za pomocą Aspose.Font dla .NET.
## Warunki wstępne
Zanim zagłębisz się w ten samouczek, upewnij się, że masz skonfigurowane następujące wymagania wstępne:
### 1. Instalacja Aspose.Font dla .NET
 Upewnij się, że w środowisku programistycznym zainstalowano Aspose.Font for .NET. Jeśli jeszcze tego nie zrobiłeś, możesz pobrać interfejs API z witryny[Aspose.Wydaje](https://releases.aspose.com/font/net/) lub za pośrednictwem menedżera pakietów NuGet.
### 2. Konfiguracja środowiska programistycznego
Upewnij się, że masz skonfigurowane środowisko programistyczne .NET z zainstalowanym programem Visual Studio lub innym zgodnym IDE.

## Importuj przestrzenie nazw
aplikacji .NET musisz zaimportować niezbędne przestrzenie nazw, aby móc pracować z Aspose.Font dla .NET.
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
Podzielmy teraz podany przykład na wiele kroków i szczegółowo wyjaśnijmy każdy z nich.
## Krok 1: Zdefiniuj ścieżkę pliku czcionki
Najpierw zdefiniuj ścieżkę pliku czcionki, z którą chcesz pracować.
```csharp
string dataDir = "Your Document Directory";
string fileName = dataDir + "Montserrat-Regular.ttf"; //Nazwa pliku czcionki z pełną ścieżką
```
## Krok 2: Otwórz plik czcionki
Następnie otwórz plik czcionki za pomocą interfejsu API Aspose.Font.
```csharp
FontDefinition fd = new FontDefinition(FontType.TTF, new FontFileDefinition("ttf", new FileSystemStreamSource(fileName)));
TtfFont font = Aspose.Font.Font.Open(fd) as TtfFont;
```
## Krok 3: Pobierz metryki czcionek
Pobierz różne metryki czcionek, takie jak wznosząca się, dolna itp.
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
## Krok 4: Uzyskaj tabelę kodowania Unicode
Pobierz tabelę kodowania Unicode (cmap) z czcionki.
```csharp
Aspose.Font.TtfCMapFormats.TtfCMapFormatBaseTable cmapTable = null;
if (font.TtfTables.CMapTable != null)
{
    cmapTable = font.TtfTables.CMapTable.FindUnicodeTable();
}
```
## Krok 5: Uzyskaj dostęp do informacji o glifach
Uzyskaj dostęp do informacji o glifach dla określonego symbolu (np. „A”).
```csharp
char unicode = (char)65; // Unikod dla „A”
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
## Wniosek
tym samouczku omówiliśmy, jak uzyskać metryki czcionek za pomocą Aspose.Font dla .NET. Postępując zgodnie z przewodnikiem krok po kroku i rozumiejąc wymagania wstępne, możesz efektywnie pracować z czcionkami w aplikacjach .NET przy użyciu interfejsu API Aspose.Font.
## Często zadawane pytania
### 1. Czy mogę używać Aspose.Font dla .NET z dowolnym formatem pliku czcionki?
Tak, Aspose.Font dla .NET obsługuje różne formaty czcionek, takie jak TrueType (TTF), OpenType (OTF) i inne.
### 2. Czy dostępna jest bezpłatna wersja próbna Aspose.Font dla .NET?
 Tak, możesz uzyskać bezpłatną wersję próbną Aspose.Font dla .NET z[strona internetowa](https://releases.aspose.com/).
### 3. Jak mogę uzyskać dostęp do wsparcia dla Aspose.Font dla .NET?
 Dostęp do pomocy technicznej dla Aspose.Font dla .NET można uzyskać poprzez[forum](https://forum.aspose.com/c/font/41).
### 4. Czy mogę kupić tymczasową licencję na Aspose.Font dla .NET?
 Tak, możesz kupić tymczasową licencję na stronie[Sklep Aspose](https://purchase.aspose.com/temporary-license/).
### 5. Czy dostępna jest dokumentacja Aspose.Font dla .NET?
 Tak, możesz uzyskać dostęp do dokumentacji Aspose.Font dla .NET[Tutaj](https://reference.aspose.com/font/net/).