---
title: Uzyskaj metryki czcionek w Aspose.Font dla .NET Type 1
linktitle: Uzyskaj metryki czcionek w Aspose.Font dla .NET Type 1
second_title: Aspose.Font API .NET
description: Dowiedz się, jak uzyskać metryki czcionek za pomocą Aspose.Font dla .NET w tym kompleksowym samouczku krok po kroku. Idealny dla programistów na każdym poziomie!
type: docs
weight: 11
url: /pl/net/aspose-font-net-type1-font/get-font-metrics-aspose-font-net-type1/
---
## Wstęp
Witamy w najlepszym przewodniku na temat uzyskiwania metryk czcionek za pomocą Aspose.Font dla .NET! Niezależnie od tego, czy jesteś doświadczonym programistą, czy dopiero zanurzasz się w świecie czcionek, ten samouczek przeprowadzi Cię przez ten proces krok po kroku. Pod koniec tego artykułu będziesz w stanie wyodrębnić szczegółowe metryki czcionek i zrozumieć, jak nimi manipulować w aplikacjach .NET. Zanurzmy się więc i rozpocznijmy tę ekscytującą podróż!
## Warunki wstępne
Zanim zagłębimy się w sedno sprawy, jest kilka rzeczy, które musisz mieć na miejscu:
- Visual Studio: Upewnij się, że na komputerze jest zainstalowany program Visual Studio.
-  Aspose.Font dla .NET: Pobierz i zainstaluj bibliotekę Aspose.Font dla .NET. Można go zdobyć z[link do pobrania](https://releases.aspose.com/font/net/).
- Podstawowa znajomość języka C#: Znajomość programowania w języku C# jest konieczna, aby postępować zgodnie z przykładami.
- Plik czcionki: Przygotuj plik czcionek TrueType (.ttf). W tym samouczku możesz użyć dowolnego pliku .ttf.
Teraz, gdy już wszystko mamy gotowe, zacznijmy od zaimportowania niezbędnych przestrzeni nazw.
## Importuj przestrzenie nazw
Aby rozpocząć pracę z Aspose.Font dla .NET, musisz uwzględnić w swoim projekcie odpowiednie przestrzenie nazw. Oto jak to zrobić:
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
Po wprowadzeniu tych przestrzeni nazw możesz rozpocząć pracę z czcionkami w aplikacji .NET.
## Krok 1: Załaduj plik czcionki
Najpierw musisz załadować plik czcionki do swojej aplikacji. Tak to się robi:
### Załaduj plik czcionki
1. Zdefiniuj ścieżkę do pliku czcionki. 
2.  Stwórz`FontDefinition` obiekt.
3.  Użyj`Font.Open` metoda ładowania czcionki.
```csharp
string dataDir = "Your Document Directory";
string fileName = dataDir + "Montserrat-Regular.ttf";
FontDefinition fd = new FontDefinition(FontType.TTF, new FontFileDefinition("ttf", new FileSystemStreamSource(fileName)));
TtfFont font = Aspose.Font.Font.Open(fd) as TtfFont;
```
 Tutaj używamy`FontDefinition` class, aby zdefiniować typ i lokalizację naszego pliku czcionki. The`Font.Open` metoda ładuje czcionkę do pliku a`TtfFont` obiekt.
## Krok 2: Pobierz podstawowe informacje o czcionce
Po załadowaniu czcionki możesz pobrać podstawowe informacje na jej temat.
### Uzyskaj nazwę czcionki i liczbę glifów
```csharp
string name = font.FontName;
Console.WriteLine("Font name: " + name);
Console.WriteLine("Glyph count: " + font.NumGlyphs);
```
Ten fragment kodu wydrukuje nazwę czcionki i liczbę zawartych w niej glifów.
## Krok 3: Wyodrębnij metryki czcionek
Metryki czcionek dostarczają szczegółowych informacji o charakterystyce czcionki.
### Wyświetl metryki czcionek
```csharp
string metrics = string.Format(
    "Font metrics: ascender - {0}, descender - {1}, typo ascender = {2}, typo descender = {3}, UnitsPerEm = {4}",
    font.Metrics.Ascender, font.Metrics.Descender,
    font.Metrics.TypoAscender, font.Metrics.TypoDescender, font.Metrics.UnitsPerEM);
Console.WriteLine(metrics);
```
Ten fragment formatuje i drukuje różne metryki czcionki, takie jak wznosząca się, dolna część i jednostki na EM.
## Krok 4: Uzyskaj dostęp do tabeli Unicode CMap
Tabela CMap pomaga w mapowaniu kodów znaków na indeksy glifów.
### Pobierz i sprawdź tabelę CMap
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
Ten kod pobiera tabelę CMap i drukuje identyfikatory platformy i identyfikatory platformy.
## Krok 5: Uzyskaj informacje o glifach
Na koniec pobierzmy informacje o konkretnym glifie, na przykład glifie oznaczającym znak „A”.
### Pobierz informacje o glifach
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
Ten fragment kodu pobiera indeks glifu dla „A”, pobiera glif przy użyciu tego indeksu i drukuje jego metryki, w tym obwiednię i szerokość.
## Wniosek
Gratulacje! Pomyślnie nauczyłeś się, jak uzyskać metryki czcionek za pomocą Aspose.Font dla .NET. Wykonując poniższe kroki, możesz łatwo wyodrębnić i manipulować informacjami o czcionkach w swoich aplikacjach. Ten samouczek powinien zapewnić solidną podstawę do bardziej zaawansowanych operacji na czcionkach. Miłego kodowania!
## Często zadawane pytania
### P1: Czy mogę używać Aspose.Font dla .NET z innymi formatami czcionek?
Tak, Aspose.Font dla .NET obsługuje różne formaty czcionek, w tym TrueType, OpenType, Type1 i inne.
### P2: Gdzie mogę uzyskać bezpłatną wersję próbną Aspose.Font dla .NET?
 Możesz pobrać bezpłatną wersję próbną ze strony[Strona z wydaniami Aspose](https://releases.aspose.com/).
### P3: Jak kupić licencję na Aspose.Font dla .NET?
 Licencję można kupić w witrynie[Strona zakupu Aspose](https://purchase.aspose.com/buy).
### P4: Czy dostępna jest obsługa Aspose.Font dla .NET?
 Tak, możesz uzyskać wsparcie od[Forum wsparcia Aspose](https://forum.aspose.com/c/font/41).
### P5: Czy mogę używać Aspose.Font dla .NET w projekcie komercyjnym?
Tak, możesz używać Aspose.Font dla .NET w projektach komercyjnych, ale będziesz potrzebować ważnej licencji.