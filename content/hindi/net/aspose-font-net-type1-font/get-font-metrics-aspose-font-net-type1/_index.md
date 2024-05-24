---
title: .NET प्रकार 1 के लिए Aspose.Font में फ़ॉन्ट मेट्रिक्स प्राप्त करें
linktitle: .NET प्रकार 1 के लिए Aspose.Font में फ़ॉन्ट मेट्रिक्स प्राप्त करें
second_title: Aspose.Font .NET एपीआई
description: इस विस्तृत, चरण-दर-चरण ट्यूटोरियल में जानें कि .NET के लिए Aspose.Font का उपयोग करके फ़ॉन्ट मेट्रिक्स कैसे प्राप्त करें। किसी भी स्तर के डेवलपर्स के लिए बिल्कुल सही!
type: docs
weight: 11
url: /hi/net/aspose-font-net-type1-font/get-font-metrics-aspose-font-net-type1/
---
## परिचय
.NET के लिए Aspose.Font का उपयोग करके फ़ॉन्ट मेट्रिक्स प्राप्त करने के बारे में अंतिम गाइड में आपका स्वागत है! चाहे आप एक अनुभवी डेवलपर हों या फ़ॉन्ट की दुनिया में अपने पैर जमा रहे हों, यह ट्यूटोरियल आपको चरण-दर-चरण प्रक्रिया से गुजारेगा। इस लेख के अंत तक, आप विस्तृत फ़ॉन्ट मेट्रिक्स निकालने में सक्षम होंगे और समझेंगे कि उन्हें अपने .NET अनुप्रयोगों में कैसे हेरफेर करना है। तो, चलिए शुरू करते हैं और इस रोमांचक यात्रा की शुरुआत करते हैं!
## आवश्यक शर्तें
इससे पहले कि हम इसकी बारीकियों में उतरें, कुछ चीजें हैं जिन्हें आपको ध्यान में रखना होगा:
- विज़ुअल स्टूडियो: सुनिश्चित करें कि आपके मशीन पर विज़ुअल स्टूडियो स्थापित है।
-  Aspose.Font for .NET: Aspose.Font for .NET लाइब्रेरी डाउनलोड करें और इंस्टॉल करें। आप इसे यहाँ से प्राप्त कर सकते हैं[लिंक को डाउनलोड करें](https://releases.aspose.com/font/net/).
- C# का बुनियादी ज्ञान: उदाहरणों के साथ आगे बढ़ने के लिए C# प्रोग्रामिंग से परिचित होना आवश्यक है।
- फ़ॉन्ट फ़ाइल: एक ट्रू टाइप फ़ॉन्ट फ़ाइल (.ttf) तैयार रखें। आप इस ट्यूटोरियल के लिए कोई भी .ttf फ़ाइल इस्तेमाल कर सकते हैं।
अब जब हमारे पास सब कुछ तैयार है, तो आइए आवश्यक नेमस्पेस को आयात करके शुरू करें।
## नामस्थान आयात करें
.NET के लिए Aspose.Font के साथ काम करना शुरू करने के लिए, आपको अपने प्रोजेक्ट में उचित नामस्थान शामिल करने होंगे। यहाँ बताया गया है कि आप यह कैसे करते हैं:
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
इन नामस्थानों के साथ, आप अपने .NET अनुप्रयोग में फ़ॉन्ट्स के साथ काम करना शुरू करने के लिए तैयार हैं।
## चरण 1: फ़ॉन्ट फ़ाइल लोड करें
सबसे पहले, आपको अपने एप्लीकेशन में फ़ॉन्ट फ़ाइल लोड करनी होगी। आप इसे इस तरह से कर सकते हैं:
### फ़ॉन्ट फ़ाइल लोड करें
1. अपनी फ़ॉन्ट फ़ाइल का पथ निर्धारित करें. 
2.  एक बनाने के`FontDefinition` वस्तु।
3.  उपयोग`Font.Open` फ़ॉन्ट लोड करने की विधि.
```csharp
string dataDir = "Your Document Directory";
string fileName = dataDir + "Montserrat-Regular.ttf";
FontDefinition fd = new FontDefinition(FontType.TTF, new FontFileDefinition("ttf", new FileSystemStreamSource(fileName)));
TtfFont font = Aspose.Font.Font.Open(fd) as TtfFont;
```
 यहाँ, हम उपयोग कर रहे हैं`FontDefinition` क्लास का उपयोग करके फ़ॉन्ट फ़ाइल का प्रकार और स्थान निर्धारित करें।`Font.Open` विधि फ़ॉन्ट को लोड करती है`TtfFont` वस्तु।
## चरण 2: मूल फ़ॉन्ट जानकारी प्राप्त करें
एक बार फ़ॉन्ट लोड हो जाने पर, आप इसके बारे में कुछ बुनियादी जानकारी प्राप्त कर सकते हैं।
### फ़ॉन्ट नाम और ग्लिफ़ गणना प्राप्त करें
```csharp
string name = font.FontName;
Console.WriteLine("Font name: " + name);
Console.WriteLine("Glyph count: " + font.NumGlyphs);
```
यह कोड स्निपेट फ़ॉन्ट का नाम और उसमें मौजूद ग्लिफ़ की संख्या प्रिंट करेगा।
## चरण 3: फ़ॉन्ट मेट्रिक्स निकालें
फ़ॉन्ट मेट्रिक्स फ़ॉन्ट की विशेषताओं के बारे में विस्तृत जानकारी प्रदान करते हैं।
### फ़ॉन्ट मेट्रिक्स प्रदर्शित करें
```csharp
string metrics = string.Format(
    "Font metrics: ascender - {0}, descender - {1}, typo ascender = {2}, typo descender = {3}, UnitsPerEm = {4}",
    font.Metrics.Ascender, font.Metrics.Descender,
    font.Metrics.TypoAscender, font.Metrics.TypoDescender, font.Metrics.UnitsPerEM);
Console.WriteLine(metrics);
```
यह स्निपेट फ़ॉन्ट के विभिन्न मेट्रिक्स को प्रारूपित और प्रिंट करता है, जैसे कि आरोही, अवरोही, और प्रति EM इकाइयाँ।
## चरण 4: CMap यूनिकोड तालिका तक पहुंचें
CMap तालिका वर्ण कोड को ग्लिफ़ सूचकांकों में मैप करने में मदद करती है।
### CMap तालिका पुनः प्राप्त करें और जाँचें
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
यह कोड CMap तालिका को पुनः प्राप्त करता है और PlatformID तथा PlatformSpecificID को प्रिंट करता है।
## चरण 5: ग्लिफ़ जानकारी प्राप्त करें
अंत में, आइए एक विशिष्ट ग्लिफ़ के बारे में जानकारी प्राप्त करें, जैसे कि वर्ण 'A' के लिए ग्लिफ़।
### ग्लिफ़ जानकारी प्राप्त करें
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
यह स्निपेट 'A' के लिए ग्लिफ़ इंडेक्स प्राप्त करता है, इस इंडेक्स का उपयोग करके ग्लिफ़ को पुनर्प्राप्त करता है, और बाउंडिंग बॉक्स और चौड़ाई सहित इसके मेट्रिक्स को प्रिंट करता है।
## निष्कर्ष
बधाई हो! आपने सफलतापूर्वक सीख लिया है कि .NET के लिए Aspose.Font का उपयोग करके फ़ॉन्ट मेट्रिक्स कैसे प्राप्त करें। इन चरणों का पालन करके, आप आसानी से अपने अनुप्रयोगों में फ़ॉन्ट जानकारी निकाल सकते हैं और उसमें हेरफेर कर सकते हैं। यह ट्यूटोरियल अधिक उन्नत फ़ॉन्ट संचालन के लिए एक ठोस आधार प्रदान करेगा। हैप्पी कोडिंग!
## अक्सर पूछे जाने वाले प्रश्न
### प्रश्न 1: क्या मैं अन्य फ़ॉन्ट प्रारूपों के साथ .NET के लिए Aspose.Font का उपयोग कर सकता हूं?
हां, .NET के लिए Aspose.Font ट्रू टाइप, ओपन टाइप, टाइप 1 और अन्य सहित विभिन्न फ़ॉन्ट प्रारूपों का समर्थन करता है।
### प्रश्न 2: मुझे .NET के लिए Aspose.Font का निःशुल्क परीक्षण कहां मिल सकता है?
 आप यहां से निःशुल्क परीक्षण संस्करण डाउनलोड कर सकते हैं[Aspose रिलीज़ पेज](https://releases.aspose.com/).
### प्रश्न 3: मैं .NET के लिए Aspose.Font का लाइसेंस कैसे खरीदूं?
 आप यहां से लाइसेंस खरीद सकते हैं[Aspose खरीद पृष्ठ](https://purchase.aspose.com/buy).
### प्रश्न 4: क्या .NET के लिए Aspose.Font का समर्थन उपलब्ध है?
 हां, आप सहायता प्राप्त कर सकते हैं[Aspose समर्थन मंच](https://forum.aspose.com/c/font/41).
### प्रश्न 5: क्या मैं व्यावसायिक परियोजना में .NET के लिए Aspose.Font का उपयोग कर सकता हूँ?
हां, आप व्यावसायिक परियोजनाओं में .NET के लिए Aspose.Font का उपयोग कर सकते हैं, लेकिन आपको एक वैध लाइसेंस की आवश्यकता होगी।