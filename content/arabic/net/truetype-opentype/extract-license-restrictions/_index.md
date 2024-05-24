---
title: قم باستخراج قيود الترخيص في Aspose.Font لـ .NET
linktitle: قم باستخراج قيود الترخيص في Aspose.Font لـ .NET
second_title: Aspose.Font.NET API
description: تعرف على كيفية استخراج قيود الترخيص من خطوط TrueType باستخدام Aspose.Font لـ .NET من خلال دليلنا التفصيلي. مثالي للمطورين الذين يعملون مع الخطوط في .NET.
type: docs
weight: 11
url: /ar/net/truetype-opentype/extract-license-restrictions/
---
## مقدمة
مرحبًا يا من هناك! إذا كنت مطورًا يعمل مع الخطوط في تطبيقات .NET، فإن فهم قيود الترخيص المضمنة في ملفات الخطوط أمر بالغ الأهمية. سيرشدك هذا الدليل الشامل خلال عملية استخراج قيود الترخيص من خطوط TrueType باستخدام Aspose.Font for .NET. سواء كنت تتأكد من الامتثال لترخيص الخطوط أو مجرد فضول بشأن أذونات الخطوط التي تستخدمها، فنحن نوفر لك كل ما تحتاجه. بحلول نهاية هذا البرنامج التعليمي، ستتمكن من التحقق من أي خط TrueType لمعرفة قيود الترخيص الخاصة به بسهولة. على استعداد للغوص في؟ هيا بنا نبدأ!
## المتطلبات الأساسية
قبل أن ننتقل إلى الكود، تأكد من أن لديك ما يلي:
-  Aspose.Font for .NET: قم بتنزيله من[صفحة الإصدارات Aspose](https://releases.aspose.com/font/net/).
- بيئة تطوير .NET: Visual Studio أو أي بيئة تطوير متكاملة أخرى متوافقة.
- المعرفة الأساسية بـ C#: الإلمام ببرمجة C# وإطار عمل .NET.
- ملف الخط: ملف خط TrueType، مثل`Montserrat-Regular.ttf`.
## استيراد مساحات الأسماء
لبدء استخدام Aspose.Font لـ .NET، ستحتاج إلى استيراد مساحات الأسماء الضرورية. ستزودك مساحات الأسماء هذه بالفئات والأساليب المطلوبة لمعالجة الخطوط.
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
الآن، دعونا نقسم العملية برمتها إلى خطوات بسيطة.
## الخطوة 1: قم بتحميل خط TrueType
 أولاً، نحتاج إلى تحميل خط TrueType في تطبيقنا. يتضمن ذلك تحديد مسار الملف وإنشاء ملف`FontDefinition` هدف.
## الخطوة 1.1: حدد مسار ملف الخط
ابدأ بتحديد الدليل الذي يوجد به ملف الخط الخاص بك والمسار الكامل للملف.
```csharp
string dataDir = "Your Document Directory";
string fileName = dataDir + "Montserrat-Regular.ttf";
```
## الخطوة 1.2: إنشاء كائن FontDefinition
 بعد ذلك، قم بإنشاء`FontDefinition` كائن لإدارة بيانات الخط. تتضمن هذه الخطوة تحديد نوع الخط ومصدر الملف.
```csharp
FontDefinition fd = new FontDefinition(FontType.TTF, new FontFileDefinition("ttf", new FileSystemStreamSource(fileName)));
```
## الخطوة 2: افتح خط TrueType
 مع ال`FontDefinition` الكائن جاهز، والخطوة التالية هي فتح الخط باستخدام Aspose.Font لـ .NET.
## الخطوة 2.1: استخدم الطريقة المفتوحة
 استخدم ال`Open` طريقة`Font` فئة لتحميل الخط. قم بإلقاء الكائن الذي تم إرجاعه إلى أ`TtfFont`.
```csharp
TtfFont font = Aspose.Font.Font.Open(fd) as TtfFont;
```
## الخطوة 3: استخراج قيود الترخيص
الآن بعد أن تم تحميل الخط، حان الوقت لاستخراج قيود الترخيص. يتضمن ذلك الوصول إلى جدول OS/2 للخط واسترداد إشارات الترخيص.
## الخطوة 3.1: تهيئة علامات الترخيص
 تهيئة أ`LicenseFlags` كائن لتخزين معلومات الترخيص.
```csharp
LicenseFlags licenseFlags = null;
```
## الخطوة 3.2: التحقق من جدول OS/2
تحقق من وجود جدول OS/2 في الخط واحصل على إشارات الترخيص في حالة وجوده.
```csharp
if (font.TtfTables.Os2Table != null)
{
    licenseFlags = font.TtfTables.Os2Table.GetLicenseFlags();
}
```
## الخطوة 3.3: تفسير علامات الترخيص
قم بتفسير علامات الترخيص وإخراج قيود الترخيص بناءً على العلامات التي تم استردادها.
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
## خاتمة
وهناك لديك! لقد تعلمت بنجاح كيفية استخراج قيود الترخيص من خطوط TrueType باستخدام Aspose.Font لـ .NET. يرشدك هذا الدليل عبر الخطوات الأساسية اللازمة للعمل مع الخطوط في تطبيقات .NET الخاصة بك، مما يضمن التزامك بمتطلبات الترخيص. ومن خلال هذه المعرفة، يمكنك إدارة الخطوط في مشاريعك بثقة، مع العلم أنك تلتزم بالإرشادات القانونية.
## الأسئلة الشائعة
### 1. ما هو Aspose.Font لـ .NET؟
Aspose.Font for .NET عبارة عن واجهة برمجة تطبيقات قوية تسمح للمطورين بالعمل مع ملفات الخطوط، مما يتيح تحميل الخطوط وتحريرها وحفظها داخل تطبيقات .NET.
### 2. هل يمكنني العمل مع تنسيقات خطوط أخرى باستخدام Aspose.Font لـ .NET؟
قطعاً! يدعم Aspose.Font for .NET تنسيقات خطوط متعددة، بما في ذلك TTF وOTF وType 1 وCFF وغيرها.
### 3. كيف يمكنني الحصول على ترخيص Aspose.Font لـ .NET؟
 يمكنك شراء ترخيص من[Aspose صفحة الشراء](https://purchase.aspose.com/buy) . لأغراض التقييم، يمكنك الحصول على ترخيص مؤقت[هنا](https://purchase.aspose.com/temporary-license/).
### 4. أين يمكنني العثور على وثائق مفصلة؟
 الوثائق التفصيلية متاحة على[Aspose.Font لصفحة وثائق .NET](https://reference.aspose.com/font/net/).
### 5. كيف يمكنني الحصول على الدعم إذا واجهت مشاكل؟
 للحصول على الدعم، يمكنك زيارة[منتدى دعم Aspose.Font](https://forum.aspose.com/c/font/41).