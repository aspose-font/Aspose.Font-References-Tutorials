---
title: 在 Aspose.Font 中取得 .NET Type 1 的字體規格
linktitle: 在 Aspose.Font 中取得 .NET Type 1 的字體規格
second_title: Aspose.Font .NET API
description: 在這個全面的逐步教學中了解如何使用 Aspose.Font for .NET 取得字體規格。適合任何級別的開發人員！
type: docs
weight: 11
url: /zh-hant/net/aspose-font-net-type1-font/get-font-metrics-aspose-font-net-type1/
---
## 介紹
歡迎來到使用 Aspose.Font for .NET 取得字體規格的終極指南！無論您是經驗豐富的開發人員還是剛剛涉足字體世界，本教學都將逐步引導您完成整個過程。閱讀本文後，您將能夠提取詳細的字體規格並了解如何在 .NET 應用程式中操作它們。那麼，就讓我們開始這個令人興奮的旅程吧！
## 先決條件
在我們深入討論細節之前，您需要準備好一些東西：
- Visual Studio：確保您的電腦上安裝了 Visual Studio。
-  Aspose.Font for .NET：下載並安裝 Aspose.Font for .NET 函式庫。您可以從[下載連結](https://releases.aspose.com/font/net/).
- C# 基礎知識：需要熟悉 C# 程式設計才能理解範例。
- 字型檔：準備好 TrueType 字型檔 (.ttf)。您可以在本教程中使用任何 .ttf 檔案。
現在我們已經準備好了一切，讓我們開始導入必要的命名空間。
## 導入命名空間
要開始使用 Aspose.Font for .NET，您需要在專案中包含適當的命名空間。操作方法如下：
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
這些命名空間就位後，您就可以開始在 .NET 應用程式中使用字體了。
## 第 1 步：載入字型文件
首先，您需要將字體檔案載入到您的應用程式中。您可以這樣做：
### 載入字體文件
1. 定義字體檔案的路徑。 
2. 創建一個`FontDefinition`目的。
3. 使用`Font.Open`載入字體的方法。
```csharp
string dataDir = "Your Document Directory";
string fileName = dataDir + "Montserrat-Regular.ttf";
FontDefinition fd = new FontDefinition(FontType.TTF, new FontFileDefinition("ttf", new FileSystemStreamSource(fileName)));
TtfFont font = Aspose.Font.Font.Open(fd) as TtfFont;
```
在這裡，我們使用的是`FontDefinition`類別來定義字型檔案的類型和位置。這`Font.Open`方法將字體載入到`TtfFont`目的。
## 第 2 步：檢索基本字體訊息
載入字體後，您可以檢索有關它的一些基本資訊。
### 取得字體名稱和字形計數
```csharp
string name = font.FontName;
Console.WriteLine("Font name: " + name);
Console.WriteLine("Glyph count: " + font.NumGlyphs);
```
此程式碼片段將列印字體名稱及其包含的字形數量。
## 第 3 步：提取字體規格
字體規格提供有關字體特徵的詳細資訊。
### 顯示字體規格
```csharp
string metrics = string.Format(
    "Font metrics: ascender - {0}, descender - {1}, typo ascender = {2}, typo descender = {3}, UnitsPerEm = {4}",
    font.Metrics.Ascender, font.Metrics.Descender,
    font.Metrics.TypoAscender, font.Metrics.TypoDescender, font.Metrics.UnitsPerEM);
Console.WriteLine(metrics);
```
此程式碼片段格式化並列印字體的各種度量，例如上升部分、下降部分和每個 EM 的單位。
## 步驟 4：存取 CMap Unicode 表
CMap 表有助於將字元代碼對應到字形索引。
### 檢索並檢查 CMap 表
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
此程式碼會擷取 CMap 表並列印 PlatformID 和 PlatformSpecificID。
## 第 5 步：取得字形信息
最後，讓我們檢索有關特定字形的信息，例如字元“A”的字形。
### 檢索字形資訊
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
此程式碼片段取得「A」的字形索引，使用該索引檢索字形，並列印其指標，包括邊界框和寬度。
## 結論
恭喜！您已成功學習如何使用 Aspose.Font for .NET 取得字體規格。透過執行這些步驟，您可以輕鬆提取和操作應用程式中的字體資訊。本教程應該為更高級的字體操作提供堅實的基礎。快樂編碼！
## 常見問題解答
### Q1：我可以將 Aspose.Font for .NET 與其他字體格式一起使用嗎？
是的，Aspose.Font for .NET 支援各種字體格式，包括 TrueType、OpenType、Type1 等。
### Q2：哪裡可以免費試用 Aspose.Font for .NET？
您可以從以下位置下載免費試用版：[Aspose 發佈頁面](https://releases.aspose.com/).
### Q3：如何購買 Aspose.Font for .NET 的授權？
您可以從以下位置購買許可證[Aspose購買頁面](https://purchase.aspose.com/buy).
### Q4：Aspose.Font for .NET 是否支援？
是的，您可以獲得以下方面的支持[Aspose 支援論壇](https://forum.aspose.com/c/font/41).
### Q5：我可以在商業專案中使用Aspose.Font for .NET嗎？
是的，您可以在商業專案中使用 Aspose.Font for .NET，但您需要有效的授權。