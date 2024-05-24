---
title: Nhận số liệu phông chữ trong Aspose.Font cho .NET
linktitle: Nhận số liệu phông chữ trong Aspose.Font cho .NET
second_title: API Aspose.Font .NET
description: Tìm hiểu cách lấy số liệu phông chữ bằng Aspose.Font cho .NET. Hướng dẫn từng bước với các ví dụ về mã. Điều kiện tiên quyết và câu hỏi thường gặp bao gồm. #Aspose #Font
type: docs
weight: 12
url: /vi/net/truetype-opentype/get-font-metrics/
---
## Giới thiệu
Aspose.Font for .NET là một API mạnh mẽ cho phép các nhà phát triển làm việc với phông chữ trong ứng dụng .NET của họ. Cho dù bạn cần trích xuất số liệu phông chữ, thao tác glyph hay truy cập dữ liệu phông chữ, Aspose.Font đều cung cấp chức năng toàn diện để hợp lý hóa các tác vụ liên quan đến phông chữ. Trong hướng dẫn này, chúng ta sẽ khám phá cách lấy số liệu phông chữ bằng Aspose.Font cho .NET.
## Điều kiện tiên quyết
Trước khi đi sâu vào hướng dẫn này, hãy đảm bảo bạn đã thiết lập các điều kiện tiên quyết sau:
### 1. Aspose.Font để cài đặt .NET
 Đảm bảo bạn đã cài đặt Aspose.Font for .NET trong môi trường phát triển của mình. Nếu chưa có, bạn có thể tải xuống API từ[Aspose.Rereleases](https://releases.aspose.com/font/net/) hoặc thông qua trình quản lý gói NuGet.
### 2. Thiết lập môi trường phát triển
Đảm bảo bạn đã cài đặt môi trường phát triển .NET với Visual Studio hoặc bất kỳ IDE tương thích nào khác được cài đặt.

## Nhập không gian tên
Trong ứng dụng .NET của mình, bạn cần nhập các vùng tên cần thiết để hoạt động với Aspose.Font cho .NET.
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
Bây giờ, hãy chia ví dụ được cung cấp thành nhiều bước và giải thích chi tiết từng bước.
## Bước 1: Xác định đường dẫn tệp phông chữ
Đầu tiên, xác định đường dẫn tệp của phông chữ bạn muốn làm việc.
```csharp
string dataDir = "Your Document Directory";
string fileName = dataDir + "Montserrat-Regular.ttf"; //Tên tệp phông chữ có đường dẫn đầy đủ
```
## Bước 2: Mở tệp phông chữ
Tiếp theo, mở tệp phông chữ bằng API Aspose.Font.
```csharp
FontDefinition fd = new FontDefinition(FontType.TTF, new FontFileDefinition("ttf", new FileSystemStreamSource(fileName)));
TtfFont font = Aspose.Font.Font.Open(fd) as TtfFont;
```
## Bước 3: Truy xuất số liệu phông chữ
Truy xuất các số liệu phông chữ khác nhau như tăng dần, giảm dần, v.v.
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
## Bước 4: Lấy bảng mã hóa Unicode
Truy xuất bảng mã hóa Unicode (cmap) từ phông chữ.
```csharp
Aspose.Font.TtfCMapFormats.TtfCMapFormatBaseTable cmapTable = null;
if (font.TtfTables.CMapTable != null)
{
    cmapTable = font.TtfTables.CMapTable.FindUnicodeTable();
}
```
## Bước 5: Truy cập thông tin Glyph
Truy cập thông tin glyph cho một biểu tượng cụ thể (ví dụ: 'A').
```csharp
char unicode = (char)65; // Unicode cho 'A'
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
## Phần kết luận
Trong hướng dẫn này, chúng tôi đã đề cập đến cách lấy số liệu phông chữ bằng Aspose.Font cho .NET. Bằng cách làm theo hướng dẫn từng bước và hiểu các điều kiện tiên quyết, bạn có thể làm việc hiệu quả với các phông chữ trong ứng dụng .NET của mình bằng API Aspose.Font.
## Câu hỏi thường gặp
### 1. Tôi có thể sử dụng Aspose.Font cho .NET với bất kỳ định dạng tệp phông chữ nào không?
Có, Aspose.Font for .NET hỗ trợ nhiều định dạng phông chữ khác nhau như TrueType (TTF), OpenType (OTF), v.v.
### 2. Có bản dùng thử miễn phí Aspose.Font cho .NET không?
 Có, bạn có thể dùng thử miễn phí Aspose.Font cho .NET từ[trang mạng](https://releases.aspose.com/).
### 3. Làm cách nào tôi có thể truy cập hỗ trợ cho Aspose.Font cho .NET?
 Bạn có thể truy cập hỗ trợ cho Aspose.Font cho .NET thông qua[diễn đàn](https://forum.aspose.com/c/font/41).
### 4. Tôi có thể mua giấy phép tạm thời cho Aspose.Font cho .NET không?
 Có, bạn có thể mua giấy phép tạm thời từ[Cửa hàng Aspose](https://purchase.aspose.com/temporary-license/).
### 5. Có tài liệu nào về Aspose.Font cho .NET không?
 Có, bạn có thể truy cập tài liệu về Aspose.Font for .NET[đây](https://reference.aspose.com/font/net/).