---
title: احصل على مقاييس الخط في Aspose.Font لـ .NET
linktitle: احصل على مقاييس الخط في Aspose.Font لـ .NET
second_title: Aspose.Font.NET API
description: تعرف على كيفية الحصول على مقاييس الخط باستخدام Aspose.Font لـ .NET. دليل خطوة بخطوة مع أمثلة التعليمات البرمجية. تم تضمين المتطلبات الأساسية والأسئلة الشائعة. #تخصيص #الخط
type: docs
weight: 12
url: /ar/net/truetype-opentype/get-font-metrics/
---
## مقدمة
Aspose.Font for .NET عبارة عن واجهة برمجة تطبيقات قوية تسمح للمطورين بالعمل مع الخطوط في تطبيقات .NET الخاصة بهم. سواء كنت بحاجة إلى استخراج مقاييس الخط أو معالجة الحروف الرسومية أو الوصول إلى بيانات الخط، فإن Aspose.Font يوفر وظائف شاملة لتبسيط المهام المتعلقة بالخط. في هذا البرنامج التعليمي، سنستكشف كيفية الحصول على مقاييس الخط باستخدام Aspose.Font لـ .NET.
## المتطلبات الأساسية
قبل الغوص في هذا البرنامج التعليمي، تأكد من إعداد المتطلبات الأساسية التالية:
### 1. Aspose.Font لتثبيت .NET
 تأكد من تثبيت Aspose.Font for .NET في بيئة التطوير لديك. إذا لم تكن قد قمت بذلك بالفعل، فيمكنك تنزيل واجهة برمجة التطبيقات (API) من[Aspose.Releases](https://releases.aspose.com/font/net/) أو عبر مدير الحزم NuGet.
### 2. إعداد بيئة التطوير
تأكد من إعداد بيئة تطوير .NET مع Visual Studio أو أي بيئة تطوير متكاملة أخرى متوافقة.

## استيراد مساحات الأسماء
في تطبيق .NET الخاص بك، تحتاج إلى استيراد مساحات الأسماء الضرورية للعمل مع Aspose.Font لـ .NET.
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
الآن، دعونا نقسم المثال المقدم إلى خطوات متعددة ونشرح كل واحدة منها بالتفصيل.
## الخطوة 1: تحديد مسار ملف الخط
أولاً، حدد مسار ملف الخط الذي تريد العمل به.
```csharp
string dataDir = "Your Document Directory";
string fileName = dataDir + "Montserrat-Regular.ttf"; //اسم ملف الخط مع المسار الكامل
```
## الخطوة 2: افتح ملف الخط
بعد ذلك، افتح ملف الخط باستخدام Aspose.Font API.
```csharp
FontDefinition fd = new FontDefinition(FontType.TTF, new FontFileDefinition("ttf", new FileSystemStreamSource(fileName)));
TtfFont font = Aspose.Font.Font.Open(fd) as TtfFont;
```
## الخطوة 3: استرداد مقاييس الخط
استرجع مقاييس الخطوط المختلفة مثل الصاعد والهابط وما إلى ذلك.
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
## الخطوة 4: احصل على جدول ترميز Unicode
قم باسترجاع جدول ترميز Unicode (cmap) من الخط.
```csharp
Aspose.Font.TtfCMapFormats.TtfCMapFormatBaseTable cmapTable = null;
if (font.TtfTables.CMapTable != null)
{
    cmapTable = font.TtfTables.CMapTable.FindUnicodeTable();
}
```
## الخطوة 5: الوصول إلى معلومات الصورة الرمزية
قم بالوصول إلى معلومات الصورة الرمزية لرمز محدد (على سبيل المثال، "A").
```csharp
char unicode = (char)65; // يونيكود لـ "أ"
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
## خاتمة
في هذا البرنامج التعليمي، تناولنا كيفية الحصول على مقاييس الخط باستخدام Aspose.Font لـ .NET. باتباع الدليل خطوة بخطوة وفهم المتطلبات الأساسية، يمكنك العمل بكفاءة مع الخطوط في تطبيقات .NET الخاصة بك باستخدام Aspose.Font API.
## الأسئلة الشائعة
### 1. هل يمكنني استخدام Aspose.Font لـ .NET مع أي تنسيق ملف خط؟
نعم، يدعم Aspose.Font for .NET تنسيقات خطوط متنوعة مثل TrueType (TTF) وOpenType (OTF) والمزيد.
### 2. هل تتوفر نسخة تجريبية مجانية من Aspose.Font لـ .NET؟
 نعم، يمكنك الحصول على نسخة تجريبية مجانية من Aspose.Font لـ .NET من[موقع إلكتروني](https://releases.aspose.com/).
### 3. كيف يمكنني الوصول إلى دعم Aspose.Font لـ .NET؟
 يمكنك الوصول إلى دعم Aspose.Font لـ .NET من خلال[المنتدى](https://forum.aspose.com/c/font/41).
### 4. هل يمكنني شراء ترخيص مؤقت لـ Aspose.Font لـ .NET؟
 نعم، يمكنك شراء ترخيص مؤقت من[متجر أسبوز](https://purchase.aspose.com/temporary-license/).
### 5. هل هناك وثائق متاحة لـ Aspose.Font لـ .NET؟
 نعم، يمكنك الوصول إلى الوثائق الخاصة بـ Aspose.Font for .NET[هنا](https://reference.aspose.com/font/net/).