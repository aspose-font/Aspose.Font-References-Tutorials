---
title: Aspose.Font for .NET'te Yazı Tipi Metriklerini Alma
linktitle: Aspose.Font for .NET'te Yazı Tipi Metriklerini Alma
second_title: Aspose.Font .NET API'si
description: Aspose.Font for .NET'i kullanarak yazı tipi ölçümlerini nasıl alacağınızı öğrenin. Kod örnekleri içeren adım adım kılavuz. Önkoşullar ve SSS'ler dahildir. #Aspose #Yazı Tipi
type: docs
weight: 12
url: /tr/net/truetype-opentype/get-font-metrics/
---
## giriiş
Aspose.Font for .NET, geliştiricilerin .NET uygulamalarındaki yazı tipleriyle çalışmasına olanak tanıyan güçlü bir API'dir. İster yazı tipi metriklerini çıkarmaya, ister glifleri işlemeye, ister yazı tipi verilerine erişmeye ihtiyacınız olsun, Aspose.Font yazı tipiyle ilgili görevleri kolaylaştırmak için kapsamlı işlevsellik sağlar. Bu eğitimde Aspose.Font for .NET kullanarak yazı tipi ölçümlerinin nasıl alınacağını inceleyeceğiz.
## Önkoşullar
Bu eğitime dalmadan önce aşağıdaki önkoşulların ayarlandığından emin olun:
### 1. Aspose.Font for .NET Kurulumu
 Geliştirme ortamınızda Aspose.Font for .NET'in kurulu olduğundan emin olun. Henüz yapmadıysanız API'yi şuradan indirebilirsiniz:[Aspose.Release'ler](https://releases.aspose.com/font/net/) veya NuGet paket yöneticisi aracılığıyla.
### 2. Geliştirme Ortamı Kurulumu
Visual Studio veya başka bir uyumlu IDE'nin kurulu olduğu bir .NET geliştirme ortamına sahip olduğunuzdan emin olun.

## Ad Alanlarını İçe Aktar
.NET uygulamanızda Aspose.Font for .NET ile çalışmak için gerekli ad alanlarını içe aktarmanız gerekir.
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
Şimdi verilen örneği birden fazla adıma ayıralım ve her birini ayrıntılı olarak açıklayalım.
## Adım 1: Yazı Tipi Dosya Yolunu Tanımlayın
Öncelikle çalışmak istediğiniz yazı tipinin dosya yolunu tanımlayın.
```csharp
string dataDir = "Your Document Directory";
string fileName = dataDir + "Montserrat-Regular.ttf"; //Tam yolu içeren yazı tipi dosyası adı
```
## Adım 2: Yazı Tipi Dosyasını Açın
Daha sonra Aspose.Font API'yi kullanarak yazı tipi dosyasını açın.
```csharp
FontDefinition fd = new FontDefinition(FontType.TTF, new FontFileDefinition("ttf", new FileSystemStreamSource(fileName)));
TtfFont font = Aspose.Font.Font.Open(fd) as TtfFont;
```
## 3. Adım: Yazı Tipi Metriklerini Alın
Yükselen, alçalan vb. gibi çeşitli yazı tipi ölçümlerini alın.
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
## Adım 4: Unicode Kodlama Tablosunu Alın
Unicode kodlama tablosunu (cmap) yazı tipinden alın.
```csharp
Aspose.Font.TtfCMapFormats.TtfCMapFormatBaseTable cmapTable = null;
if (font.TtfTables.CMapTable != null)
{
    cmapTable = font.TtfTables.CMapTable.FindUnicodeTable();
}
```
## 5. Adım: Glif Bilgilerine Erişin
Belirli bir sembole (örneğin, 'A') ilişkin glif bilgilerine erişin.
```csharp
char unicode = (char)65; // 'A' için Unicode
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
## Çözüm
Bu eğitimde Aspose.Font for .NET kullanarak yazı tipi ölçümlerinin nasıl alınacağını ele aldık. Adım adım kılavuzu takip ederek ve önkoşulları anlayarak, Aspose.Font API'yi kullanarak .NET uygulamalarınızdaki yazı tipleriyle verimli bir şekilde çalışabilirsiniz.
## SSS'ler
### 1. Aspose.Font for .NET'i herhangi bir yazı tipi dosyası formatında kullanabilir miyim?
Evet, Aspose.Font for .NET, TrueType (TTF), OpenType (OTF) ve daha fazlası gibi çeşitli yazı tipi formatlarını destekler.
### 2. Aspose.Font for .NET'in ücretsiz deneme sürümü mevcut mu?
 Evet, Aspose.Font for .NET'in ücretsiz deneme sürümünü şu adresten edinebilirsiniz:[İnternet sitesi](https://releases.aspose.com/).
### 3. Aspose.Font for .NET desteğine nasıl erişebilirim?
 Aspose.Font for .NET desteğine şu adresten erişebilirsiniz:[forum](https://forum.aspose.com/c/font/41).
### 4. Aspose.Font for .NET için geçici lisans satın alabilir miyim?
 Evet, geçici lisansı şu adresten satın alabilirsiniz:[Aspose mağaza](https://purchase.aspose.com/temporary-license/).
### 5. Aspose.Font for .NET için dokümantasyon mevcut mu?
 Evet, Aspose.Font for .NET belgelerine erişebilirsiniz[Burada](https://reference.aspose.com/font/net/).