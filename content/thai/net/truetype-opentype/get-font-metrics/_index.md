---
title: รับการวัดแบบอักษรใน Aspose.Font สำหรับ .NET
linktitle: รับการวัดแบบอักษรใน Aspose.Font สำหรับ .NET
second_title: Aspose.Font .NET API
description: เรียนรู้วิธีรับการวัดแบบอักษรโดยใช้ Aspose.Font สำหรับ .NET คำแนะนำทีละขั้นตอนพร้อมตัวอย่างโค้ด รวมข้อกำหนดเบื้องต้นและคำถามที่พบบ่อย #กำหนด #ฟอนต์
type: docs
weight: 12
url: /th/net/truetype-opentype/get-font-metrics/
---
## การแนะนำ
Aspose.Font สำหรับ .NET เป็น API ที่ทรงพลังที่ช่วยให้นักพัฒนาสามารถทำงานกับแบบอักษรในแอปพลิเคชัน .NET ของตนได้ ไม่ว่าคุณจะต้องการแยกเมตริกแบบอักษร จัดการสัญลักษณ์ หรือเข้าถึงข้อมูลแบบอักษร Aspose.Font มอบฟังก์ชันการทำงานที่ครอบคลุมเพื่อปรับปรุงงานที่เกี่ยวข้องกับแบบอักษร ในบทช่วยสอนนี้ เราจะสำรวจวิธีรับการวัดแบบอักษรโดยใช้ Aspose.Font สำหรับ .NET
## ข้อกำหนดเบื้องต้น
ก่อนที่จะเข้าสู่บทช่วยสอนนี้ ตรวจสอบให้แน่ใจว่าคุณได้ตั้งค่าข้อกำหนดเบื้องต้นต่อไปนี้:
### 1. Aspose.Font สำหรับการติดตั้ง .NET
 ตรวจสอบให้แน่ใจว่าคุณได้ติดตั้ง Aspose.Font สำหรับ .NET ในสภาพแวดล้อมการพัฒนาของคุณ หากคุณยังไม่ได้ดาวน์โหลด คุณสามารถดาวน์โหลด API ได้จาก[กำหนดเผยแพร่](https://releases.aspose.com/font/net/) หรือผ่านตัวจัดการแพ็คเกจ NuGet
### 2. การตั้งค่าสภาพแวดล้อมการพัฒนา
ตรวจสอบให้แน่ใจว่าคุณได้ตั้งค่าสภาพแวดล้อมการพัฒนา .NET ด้วย Visual Studio หรือ IDE อื่นๆ ที่เข้ากันได้

## นำเข้าเนมสเปซ
ในแอปพลิเคชัน .NET ของคุณ คุณต้องนำเข้าเนมสเปซที่จำเป็นเพื่อทำงานกับ Aspose.Font สำหรับ .NET
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
ตอนนี้ เรามาแบ่งตัวอย่างที่ให้ไว้เป็นหลายขั้นตอนและอธิบายแต่ละขั้นตอนโดยละเอียด
## ขั้นตอนที่ 1: กำหนดเส้นทางไฟล์ฟอนต์
ขั้นแรก กำหนดเส้นทางไฟล์ของแบบอักษรที่คุณต้องการใช้งาน
```csharp
string dataDir = "Your Document Directory";
string fileName = dataDir + "Montserrat-Regular.ttf"; //ชื่อไฟล์ฟอนต์พร้อมเส้นทางแบบเต็ม
```
## ขั้นตอนที่ 2: เปิดไฟล์ฟอนต์
จากนั้น เปิดไฟล์ฟอนต์โดยใช้ Aspose.Font API
```csharp
FontDefinition fd = new FontDefinition(FontType.TTF, new FontFileDefinition("ttf", new FileSystemStreamSource(fileName)));
TtfFont font = Aspose.Font.Font.Open(fd) as TtfFont;
```
## ขั้นตอนที่ 3: ดึงข้อมูลเมตริกแบบอักษร
ดึงข้อมูลการวัดแบบอักษรต่างๆ เช่น จากน้อยไปมาก จากมากไปน้อย เป็นต้น
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
## ขั้นตอนที่ 4: รับตารางการเข้ารหัส Unicode
ดึงตารางการเข้ารหัส Unicode (cmap) จากแบบอักษร
```csharp
Aspose.Font.TtfCMapFormats.TtfCMapFormatBaseTable cmapTable = null;
if (font.TtfTables.CMapTable != null)
{
    cmapTable = font.TtfTables.CMapTable.FindUnicodeTable();
}
```
## ขั้นตอนที่ 5: เข้าถึงข้อมูลสัญลักษณ์
เข้าถึงข้อมูลสัญลักษณ์สำหรับสัญลักษณ์เฉพาะ (เช่น 'A')
```csharp
char unicode = (char)65; // ยูนิโค้ดสำหรับ 'A'
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
## บทสรุป
ในบทช่วยสอนนี้ เราได้กล่าวถึงวิธีรับหน่วยวัดแบบอักษรโดยใช้ Aspose.Font สำหรับ .NET ด้วยการทำตามคำแนะนำทีละขั้นตอนและทำความเข้าใจข้อกำหนดเบื้องต้น คุณสามารถทำงานกับแบบอักษรในแอปพลิเคชัน .NET ของคุณโดยใช้ Aspose.Font API ได้อย่างมีประสิทธิภาพ
## คำถามที่พบบ่อย
### 1. ฉันสามารถใช้ Aspose.Font สำหรับ .NET กับไฟล์ฟอนต์ทุกรูปแบบได้หรือไม่
ใช่ Aspose.Font สำหรับ .NET รองรับรูปแบบฟอนต์ที่หลากหลาย เช่น TrueType (TTF), OpenType (OTF) และอื่นๆ
### 2. Aspose.Font สำหรับ .NET มีรุ่นทดลองใช้ฟรีหรือไม่
 ใช่ คุณสามารถทดลองใช้ Aspose.Font สำหรับ .NET ได้ฟรีจาก[เว็บไซต์](https://releases.aspose.com/).
### 3. ฉันจะเข้าถึงการสนับสนุน Aspose.Font สำหรับ .NET ได้อย่างไร
 คุณสามารถเข้าถึงการสนับสนุน Aspose.Font สำหรับ .NET ผ่านทาง[ฟอรั่ม](https://forum.aspose.com/c/font/41).
### 4. ฉันสามารถซื้อใบอนุญาตชั่วคราวสำหรับ Aspose.Font สำหรับ .NET ได้หรือไม่
 ใช่ คุณสามารถซื้อใบอนุญาตชั่วคราวได้จาก[แอสโพสสโตร์](https://purchase.aspose.com/temporary-license/).
### 5. มีเอกสารสำหรับ Aspose.Font สำหรับ .NET หรือไม่
 ใช่ คุณสามารถเข้าถึงเอกสารประกอบสำหรับ Aspose.Font สำหรับ .NET ได้[ที่นี่](https://reference.aspose.com/font/net/).