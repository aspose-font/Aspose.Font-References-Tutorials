---
title: Trích xuất các hạn chế giấy phép trong Aspose.Font cho .NET
linktitle: Trích xuất các hạn chế giấy phép trong Aspose.Font cho .NET
second_title: API Aspose.Font .NET
description: Tìm hiểu cách trích xuất các hạn chế cấp phép từ phông chữ TrueType bằng Aspose.Font cho .NET với hướng dẫn chi tiết của chúng tôi. Hoàn hảo cho các nhà phát triển làm việc với phông chữ trong .NET.
type: docs
weight: 11
url: /vi/net/truetype-opentype/extract-license-restrictions/
---
## Giới thiệu
Này! Nếu bạn là nhà phát triển làm việc với phông chữ trong ứng dụng .NET, việc hiểu các hạn chế cấp phép được nhúng trong tệp phông chữ là rất quan trọng. Hướng dẫn toàn diện này sẽ hướng dẫn bạn cách trích xuất các hạn chế cấp phép từ phông chữ TrueType bằng Aspose.Font cho .NET. Cho dù bạn đang đảm bảo tuân thủ việc cấp phép phông chữ hay chỉ tò mò về quyền của phông chữ bạn đang sử dụng, chúng tôi đều có thể hỗ trợ bạn. Đến cuối hướng dẫn này, bạn sẽ có thể kiểm tra bất kỳ phông chữ TrueType nào để biết các hạn chế về giấy phép của nó một cách dễ dàng. Sẵn sàng để đi sâu vào? Bắt đầu nào!
## Điều kiện tiên quyết
Trước khi chúng tôi chuyển sang mã, hãy đảm bảo bạn có những điều sau:
-  Aspose.Font for .NET: Tải xuống từ[Trang phát hành Aspose](https://releases.aspose.com/font/net/).
- Môi trường phát triển .NET: Visual Studio hoặc bất kỳ IDE tương thích nào khác.
- Kiến thức cơ bản về C#: Làm quen với lập trình C# và .NET framework.
- Tệp phông chữ: Tệp phông chữ TrueType, chẳng hạn như`Montserrat-Regular.ttf`.
## Nhập không gian tên
Để bắt đầu sử dụng Aspose.Font cho .NET, bạn cần nhập các vùng tên cần thiết. Những không gian tên này sẽ cung cấp cho bạn các lớp và phương thức cần thiết để thao tác với phông chữ.
```csharp
using Aspose.Font.Sources;
using Aspose.Font.Ttf;
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;
                        + " using the embedded font, and changes may be saved.");
```
Bây giờ, hãy chia toàn bộ quá trình thành các bước đơn giản.
## Bước 1: Tải phông chữ TrueType
 Đầu tiên, chúng ta cần tải phông chữ TrueType vào ứng dụng của mình. Điều này liên quan đến việc xác định đường dẫn tập tin và tạo một`FontDefinition` sự vật.
## Bước 1.1: Chỉ định đường dẫn tệp phông chữ
Bắt đầu bằng cách chỉ định thư mục chứa tệp phông chữ của bạn và đường dẫn đầy đủ đến tệp.
```csharp
string dataDir = "Your Document Directory";
string fileName = dataDir + "Montserrat-Regular.ttf";
```
## Bước 1.2: Tạo đối tượng FontDefinition
 Tiếp theo, tạo một`FontDefinition` đối tượng để quản lý dữ liệu phông chữ. Bước này liên quan đến việc chỉ định loại phông chữ và nguồn tệp.
```csharp
FontDefinition fd = new FontDefinition(FontType.TTF, new FontFileDefinition("ttf", new FileSystemStreamSource(fileName)));
```
## Bước 2: Mở Phông chữ TrueType
 Với`FontDefinition` đối tượng đã sẵn sàng, bước tiếp theo là mở phông chữ bằng Aspose.Font cho .NET.
## Bước 2.1: Sử dụng Phương thức mở
 Sử dụng`Open` phương pháp của`Font` lớp để tải phông chữ. Truyền đối tượng được trả về tới một`TtfFont`.
```csharp
TtfFont font = Aspose.Font.Font.Open(fd) as TtfFont;
```
## Bước 3: Trích xuất các hạn chế về giấy phép
Bây giờ phông chữ đã được tải, đã đến lúc trích xuất các hạn chế về giấy phép. Điều này liên quan đến việc truy cập bảng phông chữ OS/2 và truy xuất cờ giấy phép.
## Bước 3.1: Khởi tạo cờ giấy phép
 Khởi tạo một`LicenseFlags` đối tượng để lưu trữ thông tin giấy phép.
```csharp
LicenseFlags licenseFlags = null;
```
## Bước 3.2: Kiểm tra bảng OS/2
Kiểm tra xem bảng OS/2 có tồn tại trong phông chữ hay không và nhận cờ giấy phép nếu có.
```csharp
if (font.TtfTables.Os2Table != null)
{
    licenseFlags = font.TtfTables.Os2Table.GetLicenseFlags();
}
```
## Bước 3.3: Giải thích cờ giấy phép
Giải thích các cờ giấy phép và đưa ra các hạn chế giấy phép dựa trên các cờ được truy xuất.
```csharp
if (licenseFlags == null || licenseFlags.FSTypeAbsent)
{
    Console.WriteLine(string.Format("Font {0} has no embedded license restrictions", font.FontName));
}
else
{
    if (licenseFlags.IsEditableEmbedding)
    {
        Console.WriteLine(
            string.Format("Font {0} may be embedded, and may be temporarily loaded on other systems.", font.FontName)
            + " In addition, editing is permitted, including ability to format new text"
            + " using the embedded font, and changes may be saved.");
    }
    else if (licenseFlags.IsInstallableEmbedding)
    {
        Console.WriteLine(
            string.Format("Font {0} may be embedded, and may be permanently installed", font.FontName)
            + " for use on remote systems, or for use by other users.");
    }
    else if (licenseFlags.IsPreviewAndPrintEmbedding)
    {
        Console.WriteLine(
            string.Format("Font {0} may be embedded, and may be temporarily loaded", font.FontName)
            + " on other systems for purposes of viewing or printing the document.");
    }
    else if (licenseFlags.IsRestrictedLicenseEmbedding)
    {
        Console.WriteLine(
            string.Format("Font {0} must not be modified, embedded or exchanged in any manner", font.FontName)
            + " without first obtaining explicit permission of the legal owner.");
    }
}
```
## Phần kết luận
Và bạn có nó rồi đấy! Bạn đã học thành công cách trích xuất các hạn chế cấp phép từ phông chữ TrueType bằng Aspose.Font cho .NET. Hướng dẫn này đã đưa bạn qua các bước cần thiết để làm việc với phông chữ trong ứng dụng .NET của bạn, đảm bảo bạn tuân thủ các yêu cầu cấp phép. Với kiến thức này, bạn có thể tự tin quản lý phông chữ trong dự án của mình khi biết rằng bạn đang tuân thủ các nguyên tắc pháp lý.
## Câu hỏi thường gặp
### 1. Aspose.Font cho .NET là gì?
Aspose.Font for .NET là một API mạnh mẽ cho phép các nhà phát triển làm việc với các tệp phông chữ, cho phép tải, chỉnh sửa và lưu phông chữ trong các ứng dụng .NET.
### 2. Tôi có thể làm việc với các định dạng phông chữ khác bằng Aspose.Font cho .NET không?
Tuyệt đối! Aspose.Font for .NET hỗ trợ nhiều định dạng phông chữ, bao gồm TTF, OTF, Loại 1 và CFF, cùng nhiều định dạng khác.
### 3. Làm cách nào để có được giấy phép cho Aspose.Font cho .NET?
 Bạn có thể mua giấy phép từ[Trang mua hàng giả định](https://purchase.aspose.com/buy) . Đối với mục đích đánh giá, bạn có thể có được giấy phép tạm thời[đây](https://purchase.aspose.com/temporary-license/).
### 4. Tôi có thể tìm tài liệu chi tiết ở đâu?
 Tài liệu chi tiết có sẵn trên[Trang tài liệu Aspose.Font cho .NET](https://reference.aspose.com/font/net/).
### 5. Làm cách nào tôi có thể nhận được hỗ trợ nếu gặp sự cố?
 Để được hỗ trợ, bạn có thể truy cập[Diễn đàn hỗ trợ Aspose.Font](https://forum.aspose.com/c/font/41).