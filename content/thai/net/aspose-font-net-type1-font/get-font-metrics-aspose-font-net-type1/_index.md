---
title: รับการวัดแบบอักษรใน Aspose.Font สำหรับ .NET Type 1
linktitle: รับการวัดแบบอักษรใน Aspose.Font สำหรับ .NET Type 1
second_title: Aspose.Font .NET API
description: เรียนรู้วิธีรับการวัดแบบอักษรโดยใช้ Aspose.Font สำหรับ .NET ในบทช่วยสอนแบบทีละขั้นตอนที่ครอบคลุมนี้ เหมาะสำหรับนักพัฒนาทุกระดับ!
type: docs
weight: 11
url: /th/net/aspose-font-net-type1-font/get-font-metrics-aspose-font-net-type1/
---
## การแนะนำ
ยินดีต้อนรับสู่คำแนะนำขั้นสูงสุดในการรับการวัดแบบอักษรโดยใช้ Aspose.Font สำหรับ .NET! ไม่ว่าคุณจะเป็นนักพัฒนาที่มีประสบการณ์หรือเพียงแค่ก้าวเข้าสู่โลกของแบบอักษร บทช่วยสอนนี้จะแนะนำคุณตลอดกระบวนการทีละขั้นตอน ในตอนท้ายของบทความนี้ คุณจะสามารถแยกเมตริกแบบอักษรโดยละเอียด และเข้าใจวิธีจัดการเมตริกเหล่านั้นภายในแอปพลิเคชัน .NET ของคุณได้ เอาล่ะ มาเริ่มต้นการเดินทางอันน่าตื่นเต้นนี้กันดีกว่า!
## ข้อกำหนดเบื้องต้น
ก่อนที่เราจะเจาะลึกเนื้อหาสำคัญ มีบางสิ่งที่คุณต้องเตรียม:
- Visual Studio: ตรวจสอบให้แน่ใจว่าคุณได้ติดตั้ง Visual Studio บนเครื่องของคุณ
-  Aspose.Font สำหรับ .NET: ดาวน์โหลดและติดตั้งไลบรารี Aspose.Font สำหรับ .NET คุณสามารถรับได้จาก[ลิ้งค์ดาวน์โหลด](https://releases.aspose.com/font/net/).
- ความรู้พื้นฐานของ C#: จำเป็นต้องมีความคุ้นเคยกับการเขียนโปรแกรม C# พร้อมกับตัวอย่าง
- ไฟล์ฟอนต์: เตรียมไฟล์ฟอนต์ TrueType (.ttf) ให้พร้อม คุณสามารถใช้ไฟล์ .ttf ใดก็ได้สำหรับบทช่วยสอนนี้
ตอนนี้เรามีทุกอย่างพร้อมแล้ว เรามาเริ่มด้วยการนำเข้าเนมสเปซที่จำเป็นกันดีกว่า
## นำเข้าเนมสเปซ
หากต้องการเริ่มทำงานกับ Aspose.Font สำหรับ .NET คุณจะต้องรวมเนมสเปซที่เหมาะสมในโครงการของคุณ นี่คือวิธีการ:
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
ด้วยเนมสเปซเหล่านี้ คุณก็พร้อมที่จะเริ่มทำงานกับฟอนต์ในแอปพลิเคชัน .NET ของคุณ
## ขั้นตอนที่ 1: โหลดไฟล์ฟอนต์
ขั้นแรก คุณต้องโหลดไฟล์ฟอนต์ลงในแอปพลิเคชันของคุณ นี่คือวิธีที่คุณทำ:
### โหลดไฟล์ฟอนต์
1. กำหนดเส้นทางไปยังไฟล์ฟอนต์ของคุณ 
2.  สร้างก`FontDefinition` วัตถุ.
3.  ใช้`Font.Open` วิธีการโหลดฟอนต์
```csharp
string dataDir = "Your Document Directory";
string fileName = dataDir + "Montserrat-Regular.ttf";
FontDefinition fd = new FontDefinition(FontType.TTF, new FontFileDefinition("ttf", new FileSystemStreamSource(fileName)));
TtfFont font = Aspose.Font.Font.Open(fd) as TtfFont;
```
 ในที่นี้เราใช้.`FontDefinition` คลาสเพื่อกำหนดประเภทและตำแหน่งของไฟล์ฟอนต์ของเรา ที่`Font.Open` วิธีการโหลดแบบอักษรลงในไฟล์`TtfFont` วัตถุ.
## ขั้นตอนที่ 2: ดึงข้อมูลแบบอักษรพื้นฐาน
เมื่อโหลดฟอนต์แล้ว คุณสามารถเรียกดูข้อมูลพื้นฐานบางอย่างเกี่ยวกับฟอนต์ได้
### รับชื่อแบบอักษรและจำนวนสัญลักษณ์
```csharp
string name = font.FontName;
Console.WriteLine("Font name: " + name);
Console.WriteLine("Glyph count: " + font.NumGlyphs);
```
ข้อมูลโค้ดนี้จะพิมพ์ชื่อแบบอักษรและจำนวนสัญลักษณ์ที่มีอยู่
## ขั้นตอนที่ 3: แยกเมตริกแบบอักษร
การวัดแบบอักษรให้ข้อมูลโดยละเอียดเกี่ยวกับคุณลักษณะของแบบอักษร
### แสดงเมตริกแบบอักษร
```csharp
string metrics = string.Format(
    "Font metrics: ascender - {0}, descender - {1}, typo ascender = {2}, typo descender = {3}, UnitsPerEm = {4}",
    font.Metrics.Ascender, font.Metrics.Descender,
    font.Metrics.TypoAscender, font.Metrics.TypoDescender, font.Metrics.UnitsPerEM);
Console.WriteLine(metrics);
```
ตัวอย่างนี้จัดรูปแบบและพิมพ์หน่วยเมตริกต่างๆ ของแบบอักษร เช่น ขึ้น ลง และหน่วยต่อ EM
## ขั้นตอนที่ 4: เข้าถึงตาราง Cmap Unicode
ตาราง Cmap ช่วยในการแมปโค้ดอักขระกับดัชนีสัญลักษณ์
### ดึงข้อมูลและตรวจสอบตาราง Cmap
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
รหัสนี้ดึงข้อมูลตาราง Cmap และพิมพ์ PlatformID และ PlatformSpecificID
## ขั้นตอนที่ 5: รับข้อมูลสัญลักษณ์
สุดท้ายนี้ เราจะดึงข้อมูลเกี่ยวกับสัญลักษณ์เฉพาะ เช่น สัญลักษณ์ของอักขระ 'A'
### ดึงข้อมูลสัญลักษณ์
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
ตัวอย่างนี้รับดัชนีสัญลักษณ์สำหรับ 'A' เรียกสัญลักษณ์สัญลักษณ์โดยใช้ดัชนีนี้ และพิมพ์หน่วยเมตริก รวมถึงกรอบขอบเขตและความกว้าง
## บทสรุป
ยินดีด้วย! คุณได้เรียนรู้วิธีรับการวัดแบบอักษรโดยใช้ Aspose.Font สำหรับ .NET เรียบร้อยแล้ว เมื่อทำตามขั้นตอนเหล่านี้ คุณจะสามารถแยกและจัดการข้อมูลแบบอักษรในแอปพลิเคชันของคุณได้อย่างง่ายดาย บทช่วยสอนนี้ควรเป็นรากฐานที่มั่นคงสำหรับการทำงานของแบบอักษรขั้นสูง ขอให้มีความสุขในการเขียนโค้ด!
## คำถามที่พบบ่อย
### คำถามที่ 1: ฉันสามารถใช้ Aspose.Font สำหรับ .NET กับรูปแบบแบบอักษรอื่นได้หรือไม่
ใช่ Aspose.Font สำหรับ .NET รองรับรูปแบบฟอนต์หลากหลาย รวมถึง TrueType, OpenType, Type1 และอื่นๆ
### คำถามที่ 2: ฉันจะทดลองใช้ Aspose.Font สำหรับ .NET ฟรีได้ที่ไหน
 คุณสามารถดาวน์โหลดรุ่นทดลองใช้ฟรีได้จาก[กำหนดหน้าการเผยแพร่](https://releases.aspose.com/).
### คำถามที่ 3: ฉันจะซื้อใบอนุญาตสำหรับ Aspose.Font สำหรับ .NET ได้อย่างไร
 คุณสามารถซื้อใบอนุญาตได้จาก[กำหนดหน้าการซื้อ](https://purchase.aspose.com/buy).
### คำถามที่ 4: มีการรองรับ Aspose.Font สำหรับ .NET หรือไม่
 ใช่ คุณสามารถรับการสนับสนุนจาก[กำหนดฟอรั่มการสนับสนุน](https://forum.aspose.com/c/font/41).
### คำถามที่ 5: ฉันสามารถใช้ Aspose.Font สำหรับ .NET ในโครงการเชิงพาณิชย์ได้หรือไม่
ได้ คุณสามารถใช้ Aspose.Font สำหรับ .NET ในโครงการเชิงพาณิชย์ได้ แต่คุณจะต้องมีใบอนุญาตที่ถูกต้อง