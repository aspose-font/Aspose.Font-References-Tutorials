---
title: 在 Aspose.Font for .NET 中取得字體規格
linktitle: 在 Aspose.Font for .NET 中取得字體規格
second_title: Aspose.Font .NET API
description: 了解如何使用 Aspose.Font for .NET 取得字體規格。帶有程式碼範例的分步指南。包括先決條件和常見問題。 #Aspose #字體
type: docs
weight: 12
url: /zh-hant/net/truetype-opentype/get-font-metrics/
---
## 介紹
Aspose.Font for .NET 是一個功能強大的 API，可讓開發人員在其 .NET 應用程式中使用字體。無論您需要提取字體規格、操作字形或存取字體數據，Aspose.Font 都提供了全面的功能來簡化與字體相關的任務。在本教學中，我們將探討如何使用 Aspose.Font for .NET 取得字體規格。
## 先決條件
在深入學習本教學之前，請確保您已設定以下先決條件：
### 1.Aspose.Font for .NET安裝
請確定您的開發環境中安裝了 Aspose.Font for .NET。如果您還沒有下載 API，您可以從[Aspose. 發布](https://releases.aspose.com/font/net/)或透過 NuGet 套件管理器。
### 2. 開發環境搭建
確保您已經設定了 .NET 開發環境，並安裝了 Visual Studio 或任何其他相容的 IDE。

## 導入命名空間
在您的 .NET 應用程式中，您需要匯入必要的命名空間才能使用 Aspose.Font for .NET。
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
現在，讓我們將提供的範例分解為多個步驟並詳細解釋每個步驟。
## 第1步：定義字型檔路徑
首先，定義要使用的字體的檔案路徑。
```csharp
string dataDir = "Your Document Directory";
string fileName = dataDir + "Montserrat-Regular.ttf"; //帶有完整路徑的字型檔名
```
## 第 2 步：開啟字型文件
接下來，使用 Aspose.Font API 開啟字體檔案。
```csharp
FontDefinition fd = new FontDefinition(FontType.TTF, new FontFileDefinition("ttf", new FileSystemStreamSource(fileName)));
TtfFont font = Aspose.Font.Font.Open(fd) as TtfFont;
```
## 第 3 步：檢索字體規格
檢索各種字體規格，例如上升部分、下降部分等。
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
## 第四步：取得Unicode編碼表
從字型中檢索 Unicode 編碼表 (cmap)。
```csharp
Aspose.Font.TtfCMapFormats.TtfCMapFormatBaseTable cmapTable = null;
if (font.TtfTables.CMapTable != null)
{
    cmapTable = font.TtfTables.CMapTable.FindUnicodeTable();
}
```
## 第 5 步：存取字形信息
存取特定符號（例如“A”）的字形資訊。
```csharp
char unicode = (char)65; // 'A' 的 Unicode 編碼
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
## 結論
在本教學中，我們介紹如何使用 Aspose.Font for .NET 取得字體規格。透過遵循逐步指南並了解先決條件，您可以使用 Aspose.Font API 在 .NET 應用程式中有效地使用字體。
## 常見問題解答
### 1. 我可以將Aspose.Font for .NET與任何字體檔案格式一起使用嗎？
是的，Aspose.Font for .NET 支援各種字體格式，例如 TrueType (TTF)、OpenType (OTF) 等。
### 2. Aspose.Font for .NET 是否有免費試用版？
是的，您可以從 Aspose.Font for .NET 取得免費試用版[網站](https://releases.aspose.com/).
### 3. 如何獲得 Aspose.Font for .NET 支援？
您可以透過以下方式存取 Aspose.Font for .NET 支援：[論壇](https://forum.aspose.com/c/font/41).
### 4. 我可以購買 Aspose.Font for .NET 的臨時授權嗎？
是的，您可以從[阿斯普斯商店](https://purchase.aspose.com/temporary-license/).
### 5. 是否有 Aspose.Font for .NET 的可用文件？
是的，您可以存取 Aspose.Font for .NET 的文檔[這裡](https://reference.aspose.com/font/net/).