---
title: .NET के लिए Aspose.Font में फ़ॉन्ट मेट्रिक्स प्राप्त करें
linktitle: .NET के लिए Aspose.Font में फ़ॉन्ट मेट्रिक्स प्राप्त करें
second_title: Aspose.Font .NET एपीआई
description: .NET के लिए Aspose.Font का उपयोग करके फ़ॉन्ट मेट्रिक्स प्राप्त करना सीखें। कोड उदाहरणों के साथ चरण-दर-चरण मार्गदर्शिका। पूर्वापेक्षाएँ और FAQ शामिल हैं। #Aspose #Font
type: docs
weight: 12
url: /hi/net/truetype-opentype/get-font-metrics/
---
## परिचय
Aspose.Font for .NET एक शक्तिशाली API है जो डेवलपर्स को उनके .NET अनुप्रयोगों में फ़ॉन्ट के साथ काम करने की अनुमति देता है। चाहे आपको फ़ॉन्ट मेट्रिक्स निकालने, ग्लिफ़ में हेरफेर करने या फ़ॉन्ट डेटा तक पहुँचने की आवश्यकता हो, Aspose.Font फ़ॉन्ट-संबंधित कार्यों को सुव्यवस्थित करने के लिए व्यापक कार्यक्षमता प्रदान करता है। इस ट्यूटोरियल में, हम .NET के लिए Aspose.Font का उपयोग करके फ़ॉन्ट मेट्रिक्स प्राप्त करने का तरीका जानेंगे।
## आवश्यक शर्तें
इस ट्यूटोरियल में आगे बढ़ने से पहले, सुनिश्चित करें कि आपके पास निम्नलिखित पूर्वापेक्षाएँ हैं:
### 1. .NET स्थापना के लिए Aspose.Font
 सुनिश्चित करें कि आपके विकास परिवेश में .NET के लिए Aspose.Font स्थापित है। यदि आपने पहले से ऐसा नहीं किया है, तो आप API को यहाँ से डाउनलोड कर सकते हैं।[Aspose.रिलीज़](https://releases.aspose.com/font/net/) या NuGet पैकेज मैनेजर के माध्यम से।
### 2. विकास पर्यावरण सेटअप
सुनिश्चित करें कि आपके पास Visual Studio या किसी अन्य संगत IDE के साथ .NET विकास वातावरण स्थापित है।

## नामस्थान आयात करें
अपने .NET अनुप्रयोग में, आपको .NET के लिए Aspose.Font के साथ काम करने के लिए आवश्यक नामस्थानों को आयात करना होगा।
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
अब, आइए दिए गए उदाहरण को कई चरणों में विभाजित करें और प्रत्येक को विस्तार से समझाएं।
## चरण 1: फ़ॉन्ट फ़ाइल पथ निर्धारित करें
सबसे पहले, उस फ़ॉन्ट का फ़ाइल पथ निर्धारित करें जिसके साथ आप काम करना चाहते हैं।
```csharp
string dataDir = "Your Document Directory";
string fileName = dataDir + "Montserrat-Regular.ttf"; //पूर्ण पथ के साथ फ़ॉन्ट फ़ाइल नाम
```
## चरण 2: फ़ॉन्ट फ़ाइल खोलें
इसके बाद, Aspose.Font API का उपयोग करके फ़ॉन्ट फ़ाइल खोलें।
```csharp
FontDefinition fd = new FontDefinition(FontType.TTF, new FontFileDefinition("ttf", new FileSystemStreamSource(fileName)));
TtfFont font = Aspose.Font.Font.Open(fd) as TtfFont;
```
## चरण 3: फ़ॉन्ट मेट्रिक्स पुनर्प्राप्त करें
विभिन्न फ़ॉन्ट मेट्रिक्स जैसे कि एसेंडर, डिसेंडर, आदि को पुनः प्राप्त करें।
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
## चरण 4: यूनिकोड एनकोडिंग तालिका प्राप्त करें
फ़ॉन्ट से यूनिकोड एन्कोडिंग तालिका (cmap) प्राप्त करें।
```csharp
Aspose.Font.TtfCMapFormats.TtfCMapFormatBaseTable cmapTable = null;
if (font.TtfTables.CMapTable != null)
{
    cmapTable = font.TtfTables.CMapTable.FindUnicodeTable();
}
```
## चरण 5: ग्लिफ़ जानकारी तक पहुँचें
किसी विशिष्ट प्रतीक (जैसे, 'A') के लिए ग्लिफ़ जानकारी तक पहुँचें.
```csharp
char unicode = (char)65; // 'A' के लिए यूनिकोड
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
## निष्कर्ष
इस ट्यूटोरियल में, हमने बताया है कि .NET के लिए Aspose.Font का उपयोग करके फ़ॉन्ट मेट्रिक्स कैसे प्राप्त करें। चरण-दर-चरण मार्गदर्शिका का पालन करके और पूर्वापेक्षाओं को समझकर, आप Aspose.Font API का उपयोग करके अपने .NET अनुप्रयोगों में फ़ॉन्ट के साथ कुशलतापूर्वक काम कर सकते हैं।
## अक्सर पूछे जाने वाले प्रश्न
### 1. क्या मैं किसी भी फ़ॉन्ट फ़ाइल प्रारूप के साथ .NET के लिए Aspose.Font का उपयोग कर सकता हूं?
हां, .NET के लिए Aspose.Font विभिन्न फ़ॉन्ट प्रारूपों जैसे ट्रू टाइप (TTF), ओपन टाइप (OTF), और अधिक का समर्थन करता है।
### 2. क्या .NET के लिए Aspose.Font का निःशुल्क परीक्षण उपलब्ध है?
 हां, आप .NET के लिए Aspose.Font का निःशुल्क परीक्षण प्राप्त कर सकते हैं[वेबसाइट](https://releases.aspose.com/).
### 3. मैं .NET के लिए Aspose.Font का समर्थन कैसे प्राप्त कर सकता हूं?
 आप .NET के लिए Aspose.Font हेतु समर्थन तक पहुंच सकते हैं[मंच](https://forum.aspose.com/c/font/41).
### 4. क्या मैं .NET के लिए Aspose.Font का अस्थायी लाइसेंस खरीद सकता हूँ?
 हां, आप यहां से अस्थायी लाइसेंस खरीद सकते हैं।[एस्पोज स्टोर](https://purchase.aspose.com/temporary-license/).
### 5. क्या .NET के लिए Aspose.Font हेतु कोई दस्तावेज़ उपलब्ध है?
 हां, आप .NET के लिए Aspose.Font के दस्तावेज़ तक पहुंच सकते हैं[यहाँ](https://reference.aspose.com/font/net/).