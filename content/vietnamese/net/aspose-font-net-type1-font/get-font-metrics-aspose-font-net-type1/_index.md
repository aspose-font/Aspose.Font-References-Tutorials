---
title: Nhận số liệu phông chữ trong Aspose.Font cho .NET Loại 1
linktitle: Nhận số liệu phông chữ trong Aspose.Font cho .NET Loại 1
second_title: API Aspose.Font .NET
description: Tìm hiểu cách lấy số liệu phông chữ bằng Aspose.Font cho .NET trong hướng dẫn từng bước toàn diện này. Hoàn hảo cho các nhà phát triển ở mọi cấp độ!
type: docs
weight: 11
url: /vi/net/aspose-font-net-type1-font/get-font-metrics-aspose-font-net-type1/
---
## Giới thiệu
Chào mừng bạn đến với hướng dẫn cơ bản về cách lấy số liệu phông chữ bằng Aspose.Font cho .NET! Cho dù bạn là một nhà phát triển dày dạn kinh nghiệm hay chỉ mới bắt đầu bước chân vào thế giới phông chữ, hướng dẫn này sẽ hướng dẫn bạn thực hiện quy trình từng bước một. Đến cuối bài viết này, bạn sẽ có thể trích xuất các số liệu phông chữ chi tiết và hiểu cách thao tác chúng trong các ứng dụng .NET của mình. Vì vậy, hãy cùng bắt đầu cuộc hành trình thú vị này!
## Điều kiện tiên quyết
Trước khi chúng ta đi sâu vào vấn đề chi tiết, có một số điều bạn cần chuẩn bị sẵn:
- Visual Studio: Đảm bảo bạn đã cài đặt Visual Studio trên máy của mình.
-  Aspose.Font for .NET: Tải xuống và cài đặt thư viện Aspose.Font cho .NET. Bạn có thể lấy nó từ[Liên kết tải xuống](https://releases.aspose.com/font/net/).
- Kiến thức cơ bản về C#: Cần phải làm quen với lập trình C# để làm theo các ví dụ.
- Tệp Phông chữ: Chuẩn bị sẵn tệp phông chữ TrueType (.ttf). Bạn có thể sử dụng bất kỳ tệp .ttf nào cho hướng dẫn này.
Bây giờ chúng ta đã sẵn sàng mọi thứ, hãy bắt đầu bằng cách nhập các không gian tên cần thiết.
## Nhập không gian tên
Để bắt đầu làm việc với Aspose.Font cho .NET, bạn cần đưa các vùng tên thích hợp vào dự án của mình. Đây là cách bạn làm điều đó:
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
Với các không gian tên này, bạn đã sẵn sàng bắt đầu làm việc với các phông chữ trong ứng dụng .NET của mình.
## Bước 1: Tải tệp phông chữ
Trước tiên, bạn cần tải tệp phông chữ vào ứng dụng của mình. Đây là cách bạn làm điều đó:
### Tải tập tin phông chữ
1. Xác định đường dẫn đến tệp phông chữ của bạn. 
2.  Tạo một`FontDefinition` sự vật.
3.  Sử dụng`Font.Open` phương pháp tải phông chữ.
```csharp
string dataDir = "Your Document Directory";
string fileName = dataDir + "Montserrat-Regular.ttf";
FontDefinition fd = new FontDefinition(FontType.TTF, new FontFileDefinition("ttf", new FileSystemStreamSource(fileName)));
TtfFont font = Aspose.Font.Font.Open(fd) as TtfFont;
```
 Ở đây, chúng tôi đang sử dụng`FontDefinition` class để xác định loại và vị trí của tệp phông chữ của chúng tôi. Các`Font.Open` phương thức tải phông chữ vào một`TtfFont` sự vật.
## Bước 2: Truy xuất thông tin phông chữ cơ bản
Khi phông chữ được tải, bạn có thể truy xuất một số thông tin cơ bản về nó.
### Nhận tên phông chữ và số lượng Glyph
```csharp
string name = font.FontName;
Console.WriteLine("Font name: " + name);
Console.WriteLine("Glyph count: " + font.NumGlyphs);
```
Đoạn mã này sẽ in tên phông chữ và số lượng ký tự chứa trong đó.
## Bước 3: Trích xuất số liệu phông chữ
Số liệu phông chữ cung cấp thông tin chi tiết về đặc điểm của phông chữ.
### Hiển thị số liệu phông chữ
```csharp
string metrics = string.Format(
    "Font metrics: ascender - {0}, descender - {1}, typo ascender = {2}, typo descender = {3}, UnitsPerEm = {4}",
    font.Metrics.Ascender, font.Metrics.Descender,
    font.Metrics.TypoAscender, font.Metrics.TypoDescender, font.Metrics.UnitsPerEM);
Console.WriteLine(metrics);
```
Đoạn mã này định dạng và in các số liệu khác nhau của phông chữ, chẳng hạn như tăng dần, giảm dần và đơn vị trên mỗi EM.
## Bước 4: Truy cập Bảng Unicode CMap
Bảng CMap giúp ánh xạ mã ký tự tới các chỉ mục glyph.
### Truy xuất và kiểm tra bảng CMap
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
Mã này truy xuất bảng CMap và in PlatformID và PlatformSpecificID.
## Bước 5: Nhận thông tin Glyph
Cuối cùng, hãy truy xuất thông tin về một hình tượng cụ thể, chẳng hạn như hình tượng cho ký tự 'A'.
### Truy xuất thông tin Glyph
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
Đoạn mã này lấy chỉ mục hình tượng cho 'A', truy xuất hình tượng bằng cách sử dụng chỉ mục này và in các số liệu của nó, bao gồm hộp giới hạn và chiều rộng.
## Phần kết luận
Chúc mừng! Bạn đã học thành công cách lấy số liệu phông chữ bằng Aspose.Font cho .NET. Bằng cách làm theo các bước này, bạn có thể dễ dàng trích xuất và thao tác thông tin phông chữ trong ứng dụng của mình. Hướng dẫn này sẽ cung cấp nền tảng vững chắc cho các thao tác phông chữ nâng cao hơn. Chúc mừng mã hóa!
## Câu hỏi thường gặp
### Câu hỏi 1: Tôi có thể sử dụng Aspose.Font cho .NET với các định dạng phông chữ khác không?
Có, Aspose.Font for .NET hỗ trợ nhiều định dạng phông chữ khác nhau bao gồm TrueType, OpenType, Type1, v.v.
### Câu hỏi 2: Tôi có thể nhận bản dùng thử miễn phí Aspose.Font cho .NET ở đâu?
 Bạn có thể tải xuống bản dùng thử miễn phí từ[Trang phát hành Aspose](https://releases.aspose.com/).
### Câu hỏi 3: Làm cách nào để mua giấy phép Aspose.Font cho .NET?
 Bạn có thể mua giấy phép từ[Trang mua hàng](https://purchase.aspose.com/buy).
### Câu hỏi 4: Aspose.Font có hỗ trợ cho .NET không?
 Có, bạn có thể nhận được hỗ trợ từ[Diễn đàn hỗ trợ Aspose](https://forum.aspose.com/c/font/41).
### Câu hỏi 5: Tôi có thể sử dụng Aspose.Font cho .NET trong một dự án thương mại không?
Có, bạn có thể sử dụng Aspose.Font cho .NET trong các dự án thương mại, nhưng bạn cần có giấy phép hợp lệ.