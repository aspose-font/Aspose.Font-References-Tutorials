---
title: Get Font Metrics in Aspose.Font for .NET
linktitle: Get Font Metrics in Aspose.Font for .NET
second_title: Aspose.Font .NET API
description:  Learn how to get font metrics using Aspose.Font for .NET. Step-by-step guide with code examples. Prerequisites and FAQs included. #Aspose #Font
type: docs
weight: 12
url: /net/truetype-opentype/get-font-metrics/
---
## Introduction
Aspose.Font for .NET is a powerful API that allows developers to work with fonts in their .NET applications. Whether you need to extract font metrics, manipulate glyphs, or access font data, Aspose.Font provides comprehensive functionality to streamline font-related tasks. In this tutorial, we'll explore how to get font metrics using Aspose.Font for .NET.
## Prerequisites
Before diving into this tutorial, ensure you have the following prerequisites set up:
### 1. Aspose.Font for .NET Installation
Ensure you have Aspose.Font for .NET installed in your development environment. If you haven't already, you can download the API from the [Aspose.Releases](https://releases.aspose.com/font/net/) or via NuGet package manager.
### 2. Development Environment Setup
Make sure you have a .NET development environment set up with Visual Studio or any other compatible IDE installed.

## Import Namespaces
In your .NET application, you need to import the necessary namespaces to work with Aspose.Font for .NET.
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
Now, let's break down the example provided into multiple steps and explain each one in detail.
## Step 1: Define the Font File Path
First, define the file path of the font you want to work with.
```csharp
string dataDir = "Your Document Directory";
string fileName = dataDir + "Montserrat-Regular.ttf"; //Font file name with full path
```
## Step 2: Open the Font File
Next, open the font file using Aspose.Font API.
```csharp
FontDefinition fd = new FontDefinition(FontType.TTF, new FontFileDefinition("ttf", new FileSystemStreamSource(fileName)));
TtfFont font = Aspose.Font.Font.Open(fd) as TtfFont;
```
## Step 3: Retrieve Font Metrics
Retrieve various font metrics such as ascender, descender, etc.
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
## Step 4: Get Unicode Encoding Table
Retrieve the Unicode encoding table (cmap) from the font.
```csharp
Aspose.Font.TtfCMapFormats.TtfCMapFormatBaseTable cmapTable = null;
if (font.TtfTables.CMapTable != null)
{
    cmapTable = font.TtfTables.CMapTable.FindUnicodeTable();
}
```
## Step 5: Access Glyph Information
Access glyph information for a specific symbol (e.g., 'A').
```csharp
char unicode = (char)65; // Unicode for 'A'
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
## Conclusion
In this tutorial, we've covered how to get font metrics using Aspose.Font for .NET. By following the step-by-step guide and understanding the prerequisites, you can efficiently work with fonts in your .NET applications using Aspose.Font API.
## FAQ's
### 1. Can I use Aspose.Font for .NET with any font file format?
Yes, Aspose.Font for .NET supports various font formats such as TrueType (TTF), OpenType (OTF), and more.
### 2. Is there a free trial available for Aspose.Font for .NET?
Yes, you can get a free trial of Aspose.Font for .NET from the [website](https://releases.aspose.com/).
### 3. How can I access support for Aspose.Font for .NET?
You can access support for Aspose.Font for .NET through the [forum](https://forum.aspose.com/c/font/41).
### 4. Can I purchase a temporary license for Aspose.Font for .NET?
Yes, you can purchase a temporary license from the [Aspose store](https://purchase.aspose.com/temporary-license/).
### 5. Is there documentation available for Aspose.Font for .NET?
Yes, you can access the documentation for Aspose.Font for .NET [here](https://reference.aspose.com/font/net/).
