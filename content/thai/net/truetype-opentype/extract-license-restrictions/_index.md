---
title: แยกข้อจำกัดสิทธิ์การใช้งานใน Aspose.Font สำหรับ .NET
linktitle: แยกข้อจำกัดสิทธิ์การใช้งานใน Aspose.Font สำหรับ .NET
second_title: Aspose.Font .NET API
description: เรียนรู้วิธีแยกข้อจำกัดสิทธิ์การใช้งานจากแบบอักษร TrueType โดยใช้ Aspose.Font สำหรับ .NET พร้อมคำแนะนำโดยละเอียดของเรา เหมาะสำหรับนักพัฒนาที่ทำงานกับฟอนต์ใน .NET
type: docs
weight: 11
url: /th/net/truetype-opentype/extract-license-restrictions/
---
## การแนะนำ
สวัสดี! หากคุณเป็นนักพัฒนาที่ทำงานกับฟอนต์ในแอปพลิเคชัน .NET การทำความเข้าใจข้อจำกัดสิทธิ์การใช้งานที่ฝังอยู่ในไฟล์ฟอนต์ถือเป็นสิ่งสำคัญ คู่มือที่ครอบคลุมนี้จะแนะนำคุณเกี่ยวกับการแยกข้อจำกัดสิทธิ์การใช้งานจากฟอนต์ TrueType โดยใช้ Aspose.Font สำหรับ .NET ไม่ว่าคุณจะมั่นใจในการปฏิบัติตามข้อกำหนดสิทธิ์การใช้งานแบบอักษรหรือเพียงต้องการทราบเกี่ยวกับสิทธิ์ของแบบอักษรที่คุณใช้ เราก็พร้อมช่วยคุณ เมื่อสิ้นสุดบทช่วยสอนนี้ คุณจะสามารถตรวจสอบแบบอักษร TrueType เพื่อดูข้อจำกัดสิทธิ์การใช้งานได้อย่างง่ายดาย พร้อมที่จะดำน้ำแล้วหรือยัง? มาเริ่มกันเลย!
## ข้อกำหนดเบื้องต้น
ก่อนที่เราจะพูดถึงโค้ด ตรวจสอบให้แน่ใจว่าคุณมีสิ่งต่อไปนี้:
-  Aspose.Font สำหรับ .NET: ดาวน์โหลดได้จาก[กำหนดหน้าการเผยแพร่](https://releases.aspose.com/font/net/).
- .NET Development Environment: Visual Studio หรือ IDE อื่นๆ ที่เข้ากันได้
- ความรู้พื้นฐานเกี่ยวกับ C#: ความคุ้นเคยกับการเขียนโปรแกรม C# และกรอบงาน .NET
- ไฟล์ฟอนต์: ไฟล์ฟอนต์ TrueType เช่น`Montserrat-Regular.ttf`.
## นำเข้าเนมสเปซ
หากต้องการเริ่มใช้ Aspose.Font สำหรับ .NET คุณจะต้องนำเข้าเนมสเปซที่จำเป็น เนมสเปซเหล่านี้จะให้คลาสและวิธีการที่จำเป็นสำหรับการจัดการแบบอักษร
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
ตอนนี้ เรามาแบ่งกระบวนการทั้งหมดออกเป็นขั้นตอนง่ายๆ กัน
## ขั้นตอนที่ 1: โหลดแบบอักษร TrueType
 ขั้นแรก เราต้องโหลดแบบอักษร TrueType ลงในแอปพลิเคชันของเรา สิ่งนี้เกี่ยวข้องกับการกำหนดเส้นทางของไฟล์และการสร้างไฟล์`FontDefinition` วัตถุ.
## ขั้นตอนที่ 1.1: ระบุเส้นทางไฟล์ฟอนต์
เริ่มต้นด้วยการระบุไดเร็กทอรีซึ่งเป็นที่ตั้งของไฟล์ฟอนต์และเส้นทางแบบเต็มไปยังไฟล์
```csharp
string dataDir = "Your Document Directory";
string fileName = dataDir + "Montserrat-Regular.ttf";
```
## ขั้นตอนที่ 1.2: สร้างวัตถุ FontDefinition
 ต่อไปสร้างก`FontDefinition` วัตถุเพื่อจัดการข้อมูลแบบอักษร ขั้นตอนนี้เกี่ยวข้องกับการระบุประเภทแบบอักษรและแหล่งที่มาของไฟล์
```csharp
FontDefinition fd = new FontDefinition(FontType.TTF, new FontFileDefinition("ttf", new FileSystemStreamSource(fileName)));
```
## ขั้นตอนที่ 2: เปิดแบบอักษร TrueType
 กับ`FontDefinition` เมื่อวัตถุพร้อม ขั้นตอนต่อไปคือการเปิดแบบอักษรโดยใช้ Aspose.Font สำหรับ .NET
## ขั้นตอนที่ 2.1: ใช้วิธีเปิด
 ใช้`Open` วิธีการของ`Font` คลาสเพื่อโหลดฟอนต์ ส่งวัตถุที่ส่งคืนไปที่ a`TtfFont`.
```csharp
TtfFont font = Aspose.Font.Font.Open(fd) as TtfFont;
```
## ขั้นตอนที่ 3: แยกข้อจำกัดใบอนุญาต
เมื่อโหลดแบบอักษรแล้ว ก็ถึงเวลาแยกข้อจำกัดสิทธิ์การใช้งาน สิ่งนี้เกี่ยวข้องกับการเข้าถึงตาราง OS/2 ของฟอนต์และการดึงแฟล็กลิขสิทธิ์
## ขั้นตอนที่ 3.1: เริ่มต้นการตั้งค่าสถานะใบอนุญาต
 เริ่มต้นก`LicenseFlags` คัดค้านการจัดเก็บข้อมูลใบอนุญาต
```csharp
LicenseFlags licenseFlags = null;
```
## ขั้นตอนที่ 3.2: ตรวจสอบตาราง OS/2
ตรวจสอบว่ามีตาราง OS/2 อยู่ในแบบอักษรหรือไม่ และรับแฟล็กใบอนุญาตหากมี
```csharp
if (font.TtfTables.Os2Table != null)
{
    licenseFlags = font.TtfTables.Os2Table.GetLicenseFlags();
}
```
## ขั้นตอนที่ 3.3: ตีความธงใบอนุญาต
ตีความแฟล็กสิทธิ์การใช้งานและส่งออกข้อจำกัดสิทธิ์การใช้งานตามแฟล็กที่ดึงข้อมูล
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
## บทสรุป
และคุณก็ได้แล้ว! คุณได้เรียนรู้วิธีการแยกข้อจำกัดสิทธิ์การใช้งานจากแบบอักษร TrueType โดยใช้ Aspose.Font สำหรับ .NET เรียบร้อยแล้ว คู่มือนี้ได้นำคุณผ่านขั้นตอนสำคัญที่จำเป็นในการทำงานกับแบบอักษรในแอปพลิเคชัน .NET ของคุณ เพื่อให้มั่นใจว่าคุณปฏิบัติตามข้อกำหนดสิทธิ์การใช้งาน ด้วยความรู้นี้ คุณสามารถจัดการแบบอักษรในโครงการของคุณได้อย่างมั่นใจ โดยรู้ว่าคุณปฏิบัติตามหลักเกณฑ์ทางกฎหมาย
## คำถามที่พบบ่อย
### 1. Aspose.Font สำหรับ .NET คืออะไร
Aspose.Font สำหรับ .NET เป็น API ที่ทรงพลังซึ่งช่วยให้นักพัฒนาสามารถทำงานกับไฟล์ฟอนต์ ช่วยให้สามารถโหลด แก้ไข และบันทึกฟอนต์ภายในแอปพลิเคชัน .NET ได้
### 2. ฉันสามารถทำงานกับรูปแบบฟอนต์อื่นโดยใช้ Aspose.Font สำหรับ .NET ได้หรือไม่
อย่างแน่นอน! Aspose.Font สำหรับ .NET รองรับรูปแบบฟอนต์หลายรูปแบบ รวมถึง TTF, OTF, Type 1 และ CFF และอื่นๆ อีกมากมาย
### 3. ฉันจะได้รับใบอนุญาตสำหรับ Aspose.Font สำหรับ .NET ได้อย่างไร
 คุณสามารถซื้อใบอนุญาตได้จาก[หน้ากำหนดการซื้อ](https://purchase.aspose.com/buy) - เพื่อวัตถุประสงค์ในการประเมิน คุณสามารถขอรับใบอนุญาตชั่วคราวได้[ที่นี่](https://purchase.aspose.com/temporary-license/).
### 4. ฉันจะหาเอกสารโดยละเอียดได้ที่ไหน?
 เอกสารรายละเอียดมีอยู่ที่[Aspose.Font สำหรับหน้าเอกสารประกอบ .NET](https://reference.aspose.com/font/net/).
### 5. ฉันจะรับการสนับสนุนได้อย่างไรหากฉันประสบปัญหา?
 สำหรับการสนับสนุนคุณสามารถเยี่ยมชมที่[ฟอรั่มสนับสนุน Aspose.Font](https://forum.aspose.com/c/font/41).