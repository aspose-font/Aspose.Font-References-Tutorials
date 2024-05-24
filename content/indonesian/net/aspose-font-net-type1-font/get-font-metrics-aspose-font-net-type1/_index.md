---
title: Dapatkan Metrik Font di Aspose.Font untuk .NET Tipe 1
linktitle: Dapatkan Metrik Font di Aspose.Font untuk .NET Tipe 1
second_title: Aspose.Font .NET API
description: Pelajari cara mendapatkan metrik font menggunakan Aspose.Font untuk .NET dalam tutorial langkah demi langkah yang komprehensif ini. Sempurna untuk pengembang di tingkat mana pun!
type: docs
weight: 11
url: /id/net/aspose-font-net-type1-font/get-font-metrics-aspose-font-net-type1/
---
## Perkenalan
Selamat datang di panduan utama untuk mendapatkan metrik font menggunakan Aspose.Font untuk .NET! Baik Anda seorang pengembang berpengalaman atau baru saja terjun ke dunia font, tutorial ini akan memandu Anda melalui prosesnya langkah demi langkah. Di akhir artikel ini, Anda akan dapat mengekstrak metrik font terperinci dan memahami cara memanipulasinya dalam aplikasi .NET Anda. Jadi, mari selami dan mulai perjalanan menarik ini!
## Prasyarat
Sebelum kita mendalami seluk beluknya, ada beberapa hal yang perlu Anda siapkan:
- Visual Studio: Pastikan Anda telah menginstal Visual Studio di mesin Anda.
-  Aspose.Font untuk .NET: Unduh dan instal perpustakaan Aspose.Font untuk .NET. Anda bisa mendapatkannya dari[tautan unduhan](https://releases.aspose.com/font/net/).
- Pengetahuan Dasar C#: Keakraban dengan pemrograman C# diperlukan untuk mengikuti contoh.
- File Font: Siapkan file font TrueType (.ttf). Anda dapat menggunakan file .ttf apa pun untuk tutorial ini.
Sekarang semuanya sudah siap, mari kita mulai dengan mengimpor namespace yang diperlukan.
## Impor Namespace
Untuk mulai bekerja dengan Aspose.Font untuk .NET, Anda harus menyertakan namespace yang sesuai dalam proyek Anda. Inilah cara Anda melakukannya:
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
Dengan namespace ini, Anda siap untuk mulai bekerja dengan font di aplikasi .NET Anda.
## Langkah 1: Muat File Font
Pertama, Anda perlu memuat file font ke dalam aplikasi Anda. Inilah cara Anda melakukannya:
### Muat File Font
1. Tentukan jalur ke file font Anda. 
2.  Membuat`FontDefinition` obyek.
3.  Menggunakan`Font.Open` metode untuk memuat font.
```csharp
string dataDir = "Your Document Directory";
string fileName = dataDir + "Montserrat-Regular.ttf";
FontDefinition fd = new FontDefinition(FontType.TTF, new FontFileDefinition("ttf", new FileSystemStreamSource(fileName)));
TtfFont font = Aspose.Font.Font.Open(fd) as TtfFont;
```
 Di sini, kami menggunakan`FontDefinition` kelas untuk menentukan jenis dan lokasi file font kita. Itu`Font.Open` metode memuat font ke a`TtfFont` obyek.
## Langkah 2: Ambil Informasi Font Dasar
Setelah font dimuat, Anda dapat mengambil beberapa informasi dasar tentangnya.
### Dapatkan Nama Font dan Jumlah Mesin Terbang
```csharp
string name = font.FontName;
Console.WriteLine("Font name: " + name);
Console.WriteLine("Glyph count: " + font.NumGlyphs);
```
Cuplikan kode ini akan mencetak nama font dan jumlah mesin terbang yang dikandungnya.
## Langkah 3: Ekstrak Metrik Font
Metrik font memberikan informasi mendetail tentang karakteristik font.
### Metrik Font Tampilan
```csharp
string metrics = string.Format(
    "Font metrics: ascender - {0}, descender - {1}, typo ascender = {2}, typo descender = {3}, UnitsPerEm = {4}",
    font.Metrics.Ascender, font.Metrics.Descender,
    font.Metrics.TypoAscender, font.Metrics.TypoDescender, font.Metrics.UnitsPerEM);
Console.WriteLine(metrics);
```
Cuplikan ini memformat dan mencetak berbagai metrik font, seperti ascender, descender, dan unit per EM.
## Langkah 4: Akses Tabel Unicode CMap
Tabel CMap membantu dalam memetakan kode karakter ke indeks mesin terbang.
### Ambil dan Periksa Tabel CMap
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
Kode ini mengambil tabel CMap dan mencetak PlatformID dan PlatformSpecificID.
## Langkah 5: Dapatkan Informasi Mesin Terbang
Terakhir, mari kita ambil informasi tentang mesin terbang tertentu, misalnya mesin terbang untuk karakter 'A'.
### Ambil Informasi Mesin Terbang
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
Cuplikan ini mendapatkan indeks mesin terbang untuk 'A', mengambil mesin terbang menggunakan indeks ini, dan mencetak metriknya, termasuk kotak pembatas dan lebarnya.
## Kesimpulan
Selamat! Anda telah berhasil mempelajari cara mendapatkan metrik font menggunakan Aspose.Font untuk .NET. Dengan mengikuti langkah-langkah ini, Anda dapat dengan mudah mengekstrak dan memanipulasi informasi font di aplikasi Anda. Tutorial ini akan memberikan dasar yang kuat untuk pengoperasian font lebih lanjut. Selamat membuat kode!
## FAQ
### Q1: Bisakah saya menggunakan Aspose.Font untuk .NET dengan format font lain?
Ya, Aspose.Font untuk .NET mendukung berbagai format font termasuk TrueType, OpenType, Type1, dan banyak lagi.
### Q2: Di mana saya bisa mendapatkan uji coba gratis Aspose.Font untuk .NET?
 Anda dapat mengunduh uji coba gratis dari[Halaman rilis Aspose](https://releases.aspose.com/).
### Q3: Bagaimana cara membeli lisensi Aspose.Font untuk .NET?
 Anda dapat membeli lisensi dari[Asumsikan halaman pembelian](https://purchase.aspose.com/buy).
### Q4: Apakah tersedia dukungan untuk Aspose.Font untuk .NET?
 Ya, Anda bisa mendapatkan dukungan dari[Asumsikan forum dukungan](https://forum.aspose.com/c/font/41).
### Q5: Dapatkah saya menggunakan Aspose.Font untuk .NET dalam proyek komersial?
Ya, Anda dapat menggunakan Aspose.Font untuk .NET dalam proyek komersial, namun Anda memerlukan lisensi yang valid.