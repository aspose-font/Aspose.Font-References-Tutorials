---
title: Получите метрики шрифта в Aspose.Font для .NET
linktitle: Получите метрики шрифта в Aspose.Font для .NET
second_title: API Aspose.Font .NET
description: Узнайте, как получить метрики шрифта с помощью Aspose.Font для .NET. Пошаговое руководство с примерами кода. Включены предварительные условия и часто задаваемые вопросы. #Aspose #Шрифт
type: docs
weight: 12
url: /ru/net/truetype-opentype/get-font-metrics/
---
## Введение
Aspose.Font for .NET — это мощный API, который позволяет разработчикам работать со шрифтами в своих .NET-приложениях. Если вам нужно извлечь метрики шрифта, манипулировать глифами или получить доступ к данным шрифта, Aspose.Font предоставляет комплексные функциональные возможности для оптимизации задач, связанных со шрифтами. В этом уроке мы рассмотрим, как получить метрики шрифта с помощью Aspose.Font для .NET.
## Предварительные условия
Прежде чем приступить к изучению этого руководства, убедитесь, что у вас настроены следующие предварительные условия:
### 1. Установка Aspose.Font для .NET
 Убедитесь, что в вашей среде разработки установлен Aspose.Font for .NET. Если вы еще этого не сделали, вы можете загрузить API с сайта[Aspose.Релизы](https://releases.aspose.com/font/net/) или через менеджер пакетов NuGet.
### 2. Настройка среды разработки
Убедитесь, что у вас настроена среда разработки .NET с установленной Visual Studio или любой другой совместимой IDE.

## Импортировать пространства имен
В вашем .NET-приложении вам необходимо импортировать необходимые пространства имен для работы с Aspose.Font для .NET.
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
Теперь давайте разобьем приведенный пример на несколько этапов и подробно объясним каждый из них.
## Шаг 1. Определите путь к файлу шрифта
Сначала определите путь к файлу шрифта, с которым вы хотите работать.
```csharp
string dataDir = "Your Document Directory";
string fileName = dataDir + "Montserrat-Regular.ttf"; //Имя файла шрифта с полным путем
```
## Шаг 2. Откройте файл шрифта
Затем откройте файл шрифта с помощью API Aspose.Font.
```csharp
FontDefinition fd = new FontDefinition(FontType.TTF, new FontFileDefinition("ttf", new FileSystemStreamSource(fileName)));
TtfFont font = Aspose.Font.Font.Open(fd) as TtfFont;
```
## Шаг 3. Получение показателей шрифта
Получите различные метрики шрифта, такие как верхний, нижний и т. д.
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
## Шаг 4. Получите таблицу кодировки Юникода
Получите таблицу кодировки Юникода (cmap) из шрифта.
```csharp
Aspose.Font.TtfCMapFormats.TtfCMapFormatBaseTable cmapTable = null;
if (font.TtfTables.CMapTable != null)
{
    cmapTable = font.TtfTables.CMapTable.FindUnicodeTable();
}
```
## Шаг 5: Доступ к информации о глифах
Доступ к информации о глифах для определенного символа (например, «А»).
```csharp
char unicode = (char)65; // Юникод для буквы «А»
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
## Заключение
В этом руководстве мы рассмотрели, как получить метрики шрифта с помощью Aspose.Font для .NET. Следуя пошаговому руководству и понимая предварительные требования, вы сможете эффективно работать со шрифтами в своих .NET-приложениях с помощью API Aspose.Font.
## Часто задаваемые вопросы
### 1. Могу ли я использовать Aspose.Font для .NET с любым форматом файла шрифта?
Да, Aspose.Font для .NET поддерживает различные форматы шрифтов, такие как TrueType (TTF), OpenType (OTF) и другие.
### 2. Существует ли бесплатная пробная версия Aspose.Font для .NET?
 Да, вы можете получить бесплатную пробную версию Aspose.Font для .NET на сайте[Веб-сайт](https://releases.aspose.com/).
### 3. Как я могу получить доступ к поддержке Aspose.Font для .NET?
 Вы можете получить доступ к поддержке Aspose.Font для .NET через[Форум](https://forum.aspose.com/c/font/41).
### 4. Могу ли я приобрести временную лицензию на Aspose.Font для .NET?
 Да, вы можете приобрести временную лицензию на сайте[Aspose магазин](https://purchase.aspose.com/temporary-license/).
### 5. Есть ли документация по Aspose.Font для .NET?
 Да, вы можете получить доступ к документации по Aspose.Font для .NET.[здесь](https://reference.aspose.com/font/net/).