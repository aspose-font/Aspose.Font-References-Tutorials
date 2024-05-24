---
title: Dapatkan Metrik Font di Aspose.Font untuk .NET
linktitle: Dapatkan Metrik Font di Aspose.Font untuk .NET
second_title: Aspose.Font .NET API
description: Pelajari cara mendapatkan metrik font menggunakan Aspose.Font untuk .NET. Panduan langkah demi langkah dengan contoh kode. Prasyarat dan FAQ disertakan. #Aspose #Font
type: docs
weight: 12
url: /id/net/truetype-opentype/get-font-metrics/
---
## Perkenalan
Aspose.Font untuk .NET adalah API canggih yang memungkinkan pengembang bekerja dengan font di aplikasi .NET mereka. Baik Anda perlu mengekstrak metrik font, memanipulasi mesin terbang, atau mengakses data font, Aspose.Font menyediakan fungsionalitas komprehensif untuk menyederhanakan tugas terkait font. Dalam tutorial ini, kita akan mempelajari cara mendapatkan metrik font menggunakan Aspose.Font untuk .NET.
## Prasyarat
Sebelum mendalami tutorial ini, pastikan Anda telah menyiapkan prasyarat berikut:
### 1. Aspose.Font untuk Instalasi .NET
 Pastikan Anda telah menginstal Aspose.Font untuk .NET di lingkungan pengembangan Anda. Jika Anda belum melakukannya, Anda dapat mengunduh API dari[Aspose.Rilis](https://releases.aspose.com/font/net/) atau melalui manajer paket NuGet.
### 2. Pengaturan Lingkungan Pengembangan
Pastikan Anda memiliki lingkungan pengembangan .NET yang diatur dengan Visual Studio atau IDE lain yang kompatibel yang diinstal.

## Impor Namespace
Di aplikasi .NET, Anda perlu mengimpor namespace yang diperlukan agar berfungsi dengan Aspose.Font untuk .NET.
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
Sekarang, mari kita bagi contoh yang diberikan menjadi beberapa langkah dan jelaskan masing-masing langkah secara mendetail.
## Langkah 1: Tentukan Jalur File Font
Pertama, tentukan jalur file font yang ingin Anda gunakan.
```csharp
string dataDir = "Your Document Directory";
string fileName = dataDir + "Montserrat-Regular.ttf"; //Nama file font dengan path lengkap
```
## Langkah 2: Buka File Font
Selanjutnya, buka file font menggunakan Aspose.Font API.
```csharp
FontDefinition fd = new FontDefinition(FontType.TTF, new FontFileDefinition("ttf", new FileSystemStreamSource(fileName)));
TtfFont font = Aspose.Font.Font.Open(fd) as TtfFont;
```
## Langkah 3: Ambil Metrik Font
Ambil berbagai metrik font seperti ascender, descender, dll.
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
## Langkah 4: Dapatkan Tabel Pengkodean Unicode
Ambil tabel pengkodean Unicode (cmap) dari font.
```csharp
Aspose.Font.TtfCMapFormats.TtfCMapFormatBaseTable cmapTable = null;
if (font.TtfTables.CMapTable != null)
{
    cmapTable = font.TtfTables.CMapTable.FindUnicodeTable();
}
```
## Langkah 5: Akses Informasi Mesin Terbang
Akses informasi mesin terbang untuk simbol tertentu (misalnya, 'A').
```csharp
char unicode = (char)65; // Unikode untuk 'A'
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
## Kesimpulan
Dalam tutorial ini, kami telah membahas cara mendapatkan metrik font menggunakan Aspose.Font untuk .NET. Dengan mengikuti panduan langkah demi langkah dan memahami prasyarat, Anda dapat bekerja secara efisien dengan font di aplikasi .NET Anda menggunakan Aspose.Font API.
## FAQ
### 1. Bisakah saya menggunakan Aspose.Font untuk .NET dengan format file font apa pun?
Ya, Aspose.Font untuk .NET mendukung berbagai format font seperti TrueType (TTF), OpenType (OTF), dan banyak lagi.
### 2. Apakah tersedia uji coba gratis untuk Aspose.Font untuk .NET?
 Ya, Anda bisa mendapatkan uji coba gratis Aspose.Font untuk .NET dari[situs web](https://releases.aspose.com/).
### 3. Bagaimana cara mengakses dukungan Aspose.Font untuk .NET?
 Anda dapat mengakses dukungan untuk Aspose.Font untuk .NET melalui[forum](https://forum.aspose.com/c/font/41).
### 4. Bisakah saya membeli lisensi sementara Aspose.Font untuk .NET?
 Ya, Anda dapat membeli lisensi sementara dari[Asumsikan toko](https://purchase.aspose.com/temporary-license/).
### 5. Apakah ada dokumentasi yang tersedia untuk Aspose.Font untuk .NET?
 Ya, Anda dapat mengakses dokumentasi Aspose.Font untuk .NET[Di Sini](https://reference.aspose.com/font/net/).