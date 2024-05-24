---
title: احصل على مقاييس الخط في Aspose.Font لـ .NET Type 1
linktitle: احصل على مقاييس الخط في Aspose.Font لـ .NET Type 1
second_title: Aspose.Font.NET API
description: تعرف على كيفية الحصول على مقاييس الخط باستخدام Aspose.Font لـ .NET في هذا البرنامج التعليمي الشامل خطوة بخطوة. مثالية للمطورين على أي مستوى!
type: docs
weight: 11
url: /ar/net/aspose-font-net-type1-font/get-font-metrics-aspose-font-net-type1/
---
## مقدمة
مرحبًا بك في الدليل الشامل للحصول على مقاييس الخط باستخدام Aspose.Font لـ .NET! سواء كنت مطورًا متمرسًا أو مجرد غمس أصابعك في عالم الخطوط، فإن هذا البرنامج التعليمي سيرشدك خلال العملية خطوة بخطوة. بحلول نهاية هذه المقالة، ستتمكن من استخراج مقاييس الخطوط التفصيلية وفهم كيفية التعامل معها داخل تطبيقات .NET الخاصة بك. لذلك، دعونا نتعمق ونبدأ في هذه الرحلة المثيرة!
## المتطلبات الأساسية
قبل أن نتعمق في التفاصيل الجوهرية، هناك بعض الأشياء التي ستحتاج إلى توفرها:
- Visual Studio: تأكد من تثبيت Visual Studio على جهازك.
-  Aspose.Font for .NET: قم بتنزيل وتثبيت مكتبة Aspose.Font for .NET. يمكنك الحصول عليه من[رابط التحميل](https://releases.aspose.com/font/net/).
- المعرفة الأساسية بـ C#: الإلمام ببرمجة C# ضروري للمتابعة مع الأمثلة.
- ملف خط: قم بتجهيز ملف خط TrueType (.ttf). يمكنك استخدام أي ملف .ttf لهذا البرنامج التعليمي.
الآن بعد أن أصبح كل شيء جاهزًا، فلنبدأ باستيراد مساحات الأسماء الضرورية.
## استيراد مساحات الأسماء
لبدء العمل مع Aspose.Font for .NET، ستحتاج إلى تضمين مساحات الأسماء المناسبة في مشروعك. إليك كيفية القيام بذلك:
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
مع وجود مساحات الأسماء هذه في مكانها الصحيح، تصبح جاهزًا لبدء العمل مع الخطوط في تطبيق .NET الخاص بك.
## الخطوة 1: قم بتحميل ملف الخط
أولا، تحتاج إلى تحميل ملف الخط في التطبيق الخاص بك. هذا هو كيف نفعل ذلك:
### تحميل ملف الخط
1. تحديد المسار إلى ملف الخط الخاص بك. 
2.  إنشاء`FontDefinition` هدف.
3.  استخدم ال`Font.Open` طريقة تحميل الخط .
```csharp
string dataDir = "Your Document Directory";
string fileName = dataDir + "Montserrat-Regular.ttf";
FontDefinition fd = new FontDefinition(FontType.TTF, new FontFileDefinition("ttf", new FileSystemStreamSource(fileName)));
TtfFont font = Aspose.Font.Font.Open(fd) as TtfFont;
```
 وهنا نستخدم`FontDefinition` class لتحديد نوع وموقع ملف الخط الخاص بنا. ال`Font.Open` تقوم الطريقة بتحميل الخط إلى ملف`TtfFont` هدف.
## الخطوة 2: استرداد معلومات الخط الأساسية
بمجرد تحميل الخط، يمكنك استرداد بعض المعلومات الأساسية عنه.
### الحصول على اسم الخط وعدد الحروف الرسومية
```csharp
string name = font.FontName;
Console.WriteLine("Font name: " + name);
Console.WriteLine("Glyph count: " + font.NumGlyphs);
```
سيقوم مقتطف الكود هذا بطباعة اسم الخط وعدد الحروف الرسومية التي يحتوي عليها.
## الخطوة 3: استخراج مقاييس الخط
توفر مقاييس الخط معلومات تفصيلية حول خصائص الخط.
### عرض مقاييس الخط
```csharp
string metrics = string.Format(
    "Font metrics: ascender - {0}, descender - {1}, typo ascender = {2}, typo descender = {3}, UnitsPerEm = {4}",
    font.Metrics.Ascender, font.Metrics.Descender,
    font.Metrics.TypoAscender, font.Metrics.TypoDescender, font.Metrics.UnitsPerEM);
Console.WriteLine(metrics);
```
يقوم هذا المقتطف بتنسيق وطباعة مقاييس مختلفة للخط، مثل الصاعد والتنازلي والوحدات لكل EM.
## الخطوة 4: الوصول إلى جدول CMap Unicode
يساعد جدول CMap في تعيين رموز الأحرف إلى فهارس الحروف الرسومية.
### استرداد والتحقق من جدول CMap
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
يقوم هذا الرمز باسترداد جدول CMap وطباعة PlatformID وPlatformationSpecificID.
## الخطوة 5: الحصول على معلومات الصورة الرمزية
أخيرًا، دعنا نسترجع معلومات حول حرف رسومي محدد، مثل الحرف الرسومي للحرف "A".
### استرداد معلومات الصورة الرمزية
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
يحصل هذا المقتطف على فهرس الصورة الرمزية لـ "A"، ويسترد الصورة الرمزية باستخدام هذا الفهرس، ويطبع مقاييسه، بما في ذلك المربع المحيط والعرض.
## خاتمة
تهانينا! لقد تعلمت بنجاح كيفية الحصول على مقاييس الخط باستخدام Aspose.Font لـ .NET. باتباع هذه الخطوات، يمكنك بسهولة استخراج معلومات الخط ومعالجتها في تطبيقاتك. يجب أن يوفر هذا البرنامج التعليمي أساسًا متينًا لعمليات الخطوط الأكثر تقدمًا. ترميز سعيد!
## الأسئلة الشائعة
### س1: هل يمكنني استخدام Aspose.Font لـ .NET مع تنسيقات خطوط أخرى؟
نعم، يدعم Aspose.Font for .NET تنسيقات خطوط متنوعة بما في ذلك TrueType وOpenType وType1 والمزيد.
### س2: أين يمكنني الحصول على نسخة تجريبية مجانية من Aspose.Font لـ .NET؟
 يمكنك تنزيل نسخة تجريبية مجانية من[صفحة الإصدارات Aspose](https://releases.aspose.com/).
### س3: كيف يمكنني شراء ترخيص Aspose.Font لـ .NET؟
 يمكنك شراء ترخيص من[Aspose صفحة الشراء](https://purchase.aspose.com/buy).
### س4: هل يتوفر دعم لـ Aspose.Font لـ .NET؟
 نعم يمكنك الحصول على الدعم من[Aspose منتدى الدعم](https://forum.aspose.com/c/font/41).
### س5: هل يمكنني استخدام Aspose.Font لـ .NET في مشروع تجاري؟
نعم، يمكنك استخدام Aspose.Font for .NET في المشاريع التجارية، لكنك ستحتاج إلى ترخيص صالح.