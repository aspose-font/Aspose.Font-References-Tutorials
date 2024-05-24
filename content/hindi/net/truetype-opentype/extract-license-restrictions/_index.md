---
title: .NET के लिए Aspose.Font में लाइसेंस प्रतिबंध निकालें
linktitle: .NET के लिए Aspose.Font में लाइसेंस प्रतिबंध निकालें
second_title: Aspose.Font .NET एपीआई
description: हमारे विस्तृत गाइड के साथ .NET के लिए Aspose.Font का उपयोग करके ट्रूटाइप फ़ॉन्ट से लाइसेंस प्रतिबंधों को निकालने का तरीका जानें। .NET में फ़ॉन्ट के साथ काम करने वाले डेवलपर्स के लिए बिल्कुल सही।
type: docs
weight: 11
url: /hi/net/truetype-opentype/extract-license-restrictions/
---
## परिचय
नमस्ते! यदि आप .NET अनुप्रयोगों में फ़ॉन्ट के साथ काम करने वाले डेवलपर हैं, तो फ़ॉन्ट फ़ाइलों में एम्बेड किए गए लाइसेंस प्रतिबंधों को समझना महत्वपूर्ण है। यह व्यापक मार्गदर्शिका आपको .NET के लिए Aspose.Font का उपयोग करके TrueType फ़ॉन्ट से लाइसेंस प्रतिबंधों को निकालने में मदद करेगी। चाहे आप फ़ॉन्ट लाइसेंसिंग के अनुपालन को सुनिश्चित कर रहे हों या आपके द्वारा उपयोग किए जा रहे फ़ॉन्ट की अनुमतियों के बारे में उत्सुक हों, हमने आपको कवर किया है। इस ट्यूटोरियल के अंत तक, आप किसी भी TrueType फ़ॉन्ट को उसके लाइसेंस प्रतिबंधों के लिए आसानी से जाँच सकेंगे। शुरू करने के लिए तैयार हैं? चलिए शुरू करते हैं!
## आवश्यक शर्तें
इससे पहले कि हम कोड में आगे बढ़ें, सुनिश्चित करें कि आपके पास निम्नलिखित हैं:
-  .NET के लिए Aspose.Font: इसे यहाँ से डाउनलोड करें[Aspose रिलीज़ पेज](https://releases.aspose.com/font/net/).
- .NET विकास वातावरण: विजुअल स्टूडियो या कोई अन्य संगत IDE.
- C# का मूलभूत ज्ञान: C# प्रोग्रामिंग और .NET फ्रेमवर्क से परिचित होना।
- फ़ॉन्ट फ़ाइल: एक ट्रू टाइप फ़ॉन्ट फ़ाइल, जैसे`Montserrat-Regular.ttf`.
## नामस्थान आयात करें
.NET के लिए Aspose.Font का उपयोग शुरू करने के लिए, आपको आवश्यक नामस्थान आयात करने होंगे। ये नामस्थान आपको फ़ॉन्ट हेरफेर के लिए आवश्यक क्लास और विधियाँ प्रदान करेंगे।
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
अब, आइये पूरी प्रक्रिया को सरल चरणों में विभाजित करें।
## चरण 1: ट्रूटाइप फ़ॉन्ट लोड करें
 सबसे पहले, हमें अपने एप्लीकेशन में ट्रू टाइप फ़ॉन्ट लोड करना होगा। इसमें फ़ाइल पथ को परिभाषित करना और एक बनाना शामिल है`FontDefinition` वस्तु।
## चरण 1.1: फ़ॉन्ट फ़ाइल पथ निर्दिष्ट करें
सबसे पहले उस निर्देशिका को निर्दिष्ट करें जहां आपकी फ़ॉन्ट फ़ाइल स्थित है और फ़ाइल का पूरा पथ भी निर्दिष्ट करें।
```csharp
string dataDir = "Your Document Directory";
string fileName = dataDir + "Montserrat-Regular.ttf";
```
## चरण 1.2: फ़ॉन्टडिफ़िनेशन ऑब्जेक्ट बनाएँ
 इसके बाद, एक बनाएं`FontDefinition` फ़ॉन्ट डेटा को प्रबंधित करने के लिए ऑब्जेक्ट। इस चरण में फ़ॉन्ट प्रकार और फ़ाइल स्रोत निर्दिष्ट करना शामिल है।
```csharp
FontDefinition fd = new FontDefinition(FontType.TTF, new FontFileDefinition("ttf", new FileSystemStreamSource(fileName)));
```
## चरण 2: ट्रूटाइप फ़ॉन्ट खोलें
 साथ`FontDefinition` ऑब्जेक्ट तैयार होने के बाद, अगला चरण .NET के लिए Aspose.Font का उपयोग करके फ़ॉन्ट खोलना है।
## चरण 2.1: खुली विधि का उपयोग करें
 उपयोग`Open` की विधि`Font` फ़ॉन्ट लोड करने के लिए क्लास। लौटाए गए ऑब्जेक्ट को कास्ट करें`TtfFont`.
```csharp
TtfFont font = Aspose.Font.Font.Open(fd) as TtfFont;
```
## चरण 3: लाइसेंस प्रतिबंध निकालें
अब जब फ़ॉन्ट लोड हो गया है, तो लाइसेंस प्रतिबंधों को निकालने का समय आ गया है। इसमें फ़ॉन्ट की OS/2 तालिका तक पहुँचना और लाइसेंस फ़्लैग को पुनः प्राप्त करना शामिल है।
## चरण 3.1: लाइसेंस फ़्लैग आरंभ करें
 आरंभ करें`LicenseFlags` लाइसेंस जानकारी संग्रहीत करने के लिए ऑब्जेक्ट.
```csharp
LicenseFlags licenseFlags = null;
```
## चरण 3.2: OS/2 तालिका जाँचें
जाँच करें कि फ़ॉन्ट में OS/2 तालिका मौजूद है या नहीं और यदि मौजूद है तो लाइसेंस फ़्लैग प्राप्त करें।
```csharp
if (font.TtfTables.Os2Table != null)
{
    licenseFlags = font.TtfTables.Os2Table.GetLicenseFlags();
}
```
## चरण 3.3: लाइसेंस फ़्लैग की व्याख्या करें
लाइसेंस फ़्लैग की व्याख्या करें और प्राप्त फ़्लैग के आधार पर लाइसेंस प्रतिबंधों को आउटपुट करें।
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
## निष्कर्ष
और अब आप समझ गए होंगे! आपने सफलतापूर्वक सीख लिया है कि .NET के लिए Aspose.Font का उपयोग करके TrueType फ़ॉन्ट से लाइसेंस प्रतिबंध कैसे निकालें। इस गाइड ने आपको अपने .NET अनुप्रयोगों में फ़ॉन्ट के साथ काम करने के लिए आवश्यक आवश्यक चरणों के माध्यम से ले लिया है, यह सुनिश्चित करते हुए कि आप लाइसेंसिंग आवश्यकताओं का अनुपालन करते हैं। इस ज्ञान के साथ, आप अपने प्रोजेक्ट में फ़ॉन्ट को आत्मविश्वास से प्रबंधित कर सकते हैं, यह जानते हुए कि आप कानूनी दिशानिर्देशों का पालन कर रहे हैं।
## अक्सर पूछे जाने वाले प्रश्न
### 1. .NET के लिए Aspose.Font क्या है?
.NET के लिए Aspose.Font एक शक्तिशाली API है जो डेवलपर्स को फ़ॉन्ट फ़ाइलों के साथ काम करने, .NET अनुप्रयोगों के भीतर फ़ॉन्ट लोडिंग, संपादन और सहेजने में सक्षम बनाता है।
### 2. क्या मैं .NET के लिए Aspose.Font का उपयोग करके अन्य फ़ॉन्ट प्रारूपों के साथ काम कर सकता हूं?
बिल्कुल! .NET के लिए Aspose.Font कई फ़ॉन्ट प्रारूपों का समर्थन करता है, जिसमें TTF, OTF, टाइप 1 और CFF शामिल हैं।
### 3. मुझे .NET के लिए Aspose.Font का लाइसेंस कैसे मिलेगा?
 आप यहां से लाइसेंस खरीद सकते हैं[Aspose खरीद पृष्ठ](https://purchase.aspose.com/buy) मूल्यांकन उद्देश्यों के लिए, आप एक अस्थायी लाइसेंस प्राप्त कर सकते हैं[यहाँ](https://purchase.aspose.com/temporary-license/).
### 4. मुझे विस्तृत दस्तावेज कहां मिल सकते हैं?
 विस्तृत दस्तावेज यहां उपलब्ध है[.NET के लिए Aspose.Font दस्तावेज़ पृष्ठ](https://reference.aspose.com/font/net/).
### 5. यदि मुझे कोई समस्या आती है तो मैं सहायता कैसे प्राप्त कर सकता हूँ?
 सहायता के लिए आप यहां जा सकते हैं[Aspose.Font समर्थन मंच](https://forum.aspose.com/c/font/41).