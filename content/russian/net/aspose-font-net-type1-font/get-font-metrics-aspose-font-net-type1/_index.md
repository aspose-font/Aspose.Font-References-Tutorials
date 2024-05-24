---
title: Получите метрики шрифта в Aspose.Font для .NET Type 1
linktitle: Получите метрики шрифта в Aspose.Font для .NET Type 1
second_title: API Aspose.Font .NET
description: Узнайте, как получить метрики шрифта с помощью Aspose.Font для .NET, в этом подробном пошаговом руководстве. Идеально подходит для разработчиков любого уровня!
type: docs
weight: 11
url: /ru/net/aspose-font-net-type1-font/get-font-metrics-aspose-font-net-type1/
---
## Введение
Добро пожаловать в полное руководство по получению показателей шрифта с помощью Aspose.Font для .NET! Независимо от того, являетесь ли вы опытным разработчиком или просто погружаетесь в мир шрифтов, это руководство шаг за шагом проведет вас через этот процесс. К концу этой статьи вы сможете извлечь подробные метрики шрифтов и понять, как манипулировать ими в своих .NET-приложениях. Итак, давайте окунемся и начнем это увлекательное путешествие!
## Предварительные условия
Прежде чем мы углубимся в подробности, вам необходимо иметь в виду несколько вещей:
- Visual Studio: убедитесь, что на вашем компьютере установлена Visual Studio.
-  Aspose.Font для .NET: Загрузите и установите библиотеку Aspose.Font для .NET. Вы можете получить его из[ссылка для скачивания](https://releases.aspose.com/font/net/).
- Базовые знания C#: Для изучения примеров необходимо знание программирования на C#.
- Файл шрифта: подготовьте файл шрифта TrueType (.ttf). Для этого урока вы можете использовать любой файл .ttf.
Теперь, когда у нас все готово, давайте начнем с импорта необходимых пространств имен.
## Импортировать пространства имен
Чтобы начать работу с Aspose.Font для .NET, вам необходимо включить в свой проект соответствующие пространства имен. Вот как это сделать:
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
Имея эти пространства имен, вы готовы начать работу со шрифтами в своем .NET-приложении.
## Шаг 1. Загрузите файл шрифта
Сначала вам необходимо загрузить файл шрифта в ваше приложение. Вот как вы это делаете:
### Загрузить файл шрифта
1. Определите путь к файлу шрифта. 
2.  Создать`FontDefinition` объект.
3.  Использовать`Font.Open` метод загрузки шрифта.
```csharp
string dataDir = "Your Document Directory";
string fileName = dataDir + "Montserrat-Regular.ttf";
FontDefinition fd = new FontDefinition(FontType.TTF, new FontFileDefinition("ttf", new FileSystemStreamSource(fileName)));
TtfFont font = Aspose.Font.Font.Open(fd) as TtfFont;
```
 Здесь мы используем`FontDefinition` class, чтобы определить тип и расположение нашего файла шрифта.`Font.Open` метод загружает шрифт в`TtfFont` объект.
## Шаг 2. Получите основную информацию о шрифте
После загрузки шрифта вы можете получить некоторую базовую информацию о нем.
### Получить имя шрифта и количество глифов
```csharp
string name = font.FontName;
Console.WriteLine("Font name: " + name);
Console.WriteLine("Glyph count: " + font.NumGlyphs);
```
Этот фрагмент кода выведет имя шрифта и количество содержащихся в нем глифов.
## Шаг 3. Извлечение показателей шрифта
Метрики шрифта предоставляют подробную информацию о характеристиках шрифта.
### Отображение показателей шрифта
```csharp
string metrics = string.Format(
    "Font metrics: ascender - {0}, descender - {1}, typo ascender = {2}, typo descender = {3}, UnitsPerEm = {4}",
    font.Metrics.Ascender, font.Metrics.Descender,
    font.Metrics.TypoAscender, font.Metrics.TypoDescender, font.Metrics.UnitsPerEM);
Console.WriteLine(metrics);
```
Этот фрагмент форматирует и печатает различные метрики шрифта, такие как верхний, нижний колонтитул и единицы измерения на EM.
## Шаг 4. Доступ к таблице Юникода CMap
Таблица CMap помогает сопоставлять коды символов с индексами глифов.
### Получить и проверить таблицу CMap
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
Этот код извлекает таблицу CMap и печатает PlatformID и PlatformSpecificID.
## Шаг 5: Получите информацию о глифах
Наконец, давайте получим информацию о конкретном глифе, например, глифе символа «А».
### Получить информацию о глифах
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
Этот фрагмент получает индекс глифа для буквы «A», извлекает глиф, используя этот индекс, и печатает его показатели, включая ограничивающую рамку и ширину.
## Заключение
Поздравляем! Вы успешно научились получать метрики шрифта с помощью Aspose.Font для .NET. Выполнив эти шаги, вы сможете легко извлекать информацию о шрифтах и манипулировать ею в своих приложениях. Это руководство должно обеспечить прочную основу для более сложных операций со шрифтами. Приятного кодирования!
## Часто задаваемые вопросы
### Вопрос 1: Могу ли я использовать Aspose.Font для .NET с другими форматами шрифтов?
Да, Aspose.Font for .NET поддерживает различные форматы шрифтов, включая TrueType, OpenType, Type1 и другие.
### Вопрос 2. Где я могу получить бесплатную пробную версию Aspose.Font для .NET?
 Вы можете скачать бесплатную пробную версию на сайте[Страница релизов Aspose](https://releases.aspose.com/).
### Вопрос 3: Как купить лицензию на Aspose.Font для .NET?
 Вы можете приобрести лицензию на сайте[Aspose страница покупки](https://purchase.aspose.com/buy).
### Вопрос 4. Доступна ли поддержка Aspose.Font для .NET?
 Да, вы можете получить поддержку от[Форум поддержки Aspose](https://forum.aspose.com/c/font/41).
### Вопрос 5: Могу ли я использовать Aspose.Font для .NET в коммерческом проекте?
Да, вы можете использовать Aspose.Font для .NET в коммерческих проектах, но вам потребуется действующая лицензия.