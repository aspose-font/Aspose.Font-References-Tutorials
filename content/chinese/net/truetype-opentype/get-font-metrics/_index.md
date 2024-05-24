---
title: 在 Aspose.Font for .NET 中获取字体指标
linktitle: 在 Aspose.Font for .NET 中获取字体指标
second_title: Aspose.Font .NET API
description: 了解如何使用 Aspose.Font for .NET 获取字体指标。带有代码示例的分步指南。包含先决条件和常见问题解答。#Aspose #Font
type: docs
weight: 12
url: /zh/net/truetype-opentype/get-font-metrics/
---
## 介绍
Aspose.Font for .NET 是一个功能强大的 API，允许开发人员在其 .NET 应用程序中使用字体。无论您需要提取字体指标、操作字形还是访问字体数据，Aspose.Font 都提供全面的功能来简化与字体相关的任务。在本教程中，我们将探讨如何使用 Aspose.Font for .NET 获取字体指标。
## 先决条件
在深入学习本教程之前，请确保您已设置以下先决条件：
### 1. Aspose.Font for .NET 安装
确保在开发环境中安装了 Aspose.Font for .NET。如果尚未安装，可以从[Aspose.Releases](https://releases.aspose.com/font/net/)或通过 NuGet 包管理器。
### 2. 开发环境设置
确保您已安装 Visual Studio 或任何其他兼容 IDE 来设置 .NET 开发环境。

## 导入命名空间
在您的.NET应用程序中，您需要导入必要的命名空间才能使用 Aspose.Font for .NET。
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
现在，让我们将提供的示例分解为多个步骤，并详细解释每个步骤。
## 步骤 1：定义字体文件路径
首先，定义您要使用的字体的文件路径。
```csharp
string dataDir = "Your Document Directory";
string fileName = dataDir + "Montserrat-Regular.ttf"; //带有完整路径的字体文件名
```
## 第 2 步：打开字体文件
接下来，使用 Aspose.Font API 打开字体文件。
```csharp
FontDefinition fd = new FontDefinition(FontType.TTF, new FontFileDefinition("ttf", new FileSystemStreamSource(fileName)));
TtfFont font = Aspose.Font.Font.Open(fd) as TtfFont;
```
## 步骤 3：检索字体规格
检索各种字体指标，如上升部、下降部等等。
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
## 步骤4：获取Unicode编码表
从字体中检索 Unicode 编码表 (cmap)。
```csharp
Aspose.Font.TtfCMapFormats.TtfCMapFormatBaseTable cmapTable = null;
if (font.TtfTables.CMapTable != null)
{
    cmapTable = font.TtfTables.CMapTable.FindUnicodeTable();
}
```
## 步骤 5：访问字形信息
访问特定符号（例如“A”）的字形信息。
```csharp
char unicode = (char)65; // Unicode 中的“A”
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
## 结论
在本教程中，我们介绍了如何使用 Aspose.Font for .NET 获取字体指标。通过遵循分步指南并了解先决条件，您可以使用 Aspose.Font API 高效地处理 .NET 应用程序中的字体。
## 常见问题解答
### 1. 我可以使用 Aspose.Font for .NET 和任何字体文件格式吗？
是的，Aspose.Font for .NET 支持各种字体格式，例如 TrueType (TTF)、OpenType (OTF) 等。
### 2. Aspose.Font for .NET 有免费试用版吗？
是的，你可以从以下网站免费试用 Aspose.Font for .NET[网站](https://releases.aspose.com/).
### 3. 如何获得对 Aspose.Font for .NET 的支持？
您可以通过以下方式访问对 Aspose.Font for .NET 的支持[论坛](https://forum.aspose.com/c/font/41).
### 4. 我可以购买 Aspose.Font for .NET 的临时许可证吗？
是的，你可以从[Aspose 商店](https://purchase.aspose.com/temporary-license/).
### 5. 有没有适用于 Aspose.Font for .NET 的文档？
是的，您可以访问 Aspose.Font for .NET 的文档[这里](https://reference.aspose.com/font/net/).