---
title: Aspose.Font for .NET Type 1'de Yazı Tipi Metriklerini Alma
linktitle: Aspose.Font for .NET Type 1'de Yazı Tipi Metriklerini Alma
second_title: Aspose.Font .NET API'si
description: Bu kapsamlı, adım adım eğitimde Aspose.Font for .NET kullanarak yazı tipi ölçümlerini nasıl alacağınızı öğrenin. Her seviyedeki geliştiriciler için mükemmel!
type: docs
weight: 11
url: /tr/net/aspose-font-net-type1-font/get-font-metrics-aspose-font-net-type1/
---
## giriiş
Aspose.Font for .NET'i kullanarak yazı tipi ölçümlerini elde etmeye yönelik nihai kılavuza hoş geldiniz! İster deneyimli bir geliştirici olun ister yazı tipi dünyasına yeni adım atın, bu eğitim size süreç boyunca adım adım yol gösterecektir. Bu makalenin sonunda ayrıntılı yazı tipi ölçümlerini çıkarabilecek ve bunları .NET uygulamalarınızda nasıl değiştireceğinizi anlayacaksınız. O halde haydi dalalım ve bu heyecan verici yolculuğa başlayalım!
## Önkoşullar
İşin özüne dalmadan önce, hazır olmanız gereken birkaç şey var:
- Visual Studio: Makinenizde Visual Studio'nun kurulu olduğundan emin olun.
-  Aspose.Font for .NET: Aspose.Font for .NET kitaplığını indirip yükleyin. Şu adresten alabilirsiniz:[İndirme: {link](https://releases.aspose.com/font/net/).
- Temel C# Bilgisi: Örnekleri takip etmek için C# programlamaya aşinalık gereklidir.
- Yazı Tipi Dosyası: Bir TrueType yazı tipi dosyasını (.ttf) hazır bulundurun. Bu eğitim için herhangi bir .ttf dosyasını kullanabilirsiniz.
Artık her şey hazır olduğuna göre gerekli ad alanlarını içe aktararak başlayalım.
## Ad Alanlarını İçe Aktar
Aspose.Font for .NET ile çalışmaya başlamak için projenize uygun ad alanlarını eklemeniz gerekir. İşte bunu nasıl yapacağınız:
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
Bu ad alanları mevcut olduğunda, .NET uygulamanızdaki yazı tipleriyle çalışmaya hazırsınız.
## Adım 1: Yazı Tipi Dosyasını Yükleyin
Öncelikle font dosyasını uygulamanıza yüklemeniz gerekiyor. Bunu şu şekilde yaparsınız:
### Yazı Tipi Dosyasını Yükle
1. Yazı tipi dosyanızın yolunu tanımlayın. 
2.  Oluşturmak`FontDefinition` nesne.
3.  Kullan`Font.Open` Yazı tipini yükleme yöntemi.
```csharp
string dataDir = "Your Document Directory";
string fileName = dataDir + "Montserrat-Regular.ttf";
FontDefinition fd = new FontDefinition(FontType.TTF, new FontFileDefinition("ttf", new FileSystemStreamSource(fileName)));
TtfFont font = Aspose.Font.Font.Open(fd) as TtfFont;
```
 Burada şunu kullanıyoruz:`FontDefinition` Yazı tipi dosyamızın türünü ve konumunu tanımlamak için class.`Font.Open` yöntem yazı tipini bir`TtfFont` nesne.
## Adım 2: Temel Yazı Tipi Bilgilerini Alın
Yazı tipi yüklendikten sonra onunla ilgili bazı temel bilgileri alabilirsiniz.
### Yazı Tipi Adını ve Glif Sayısını Al
```csharp
string name = font.FontName;
Console.WriteLine("Font name: " + name);
Console.WriteLine("Glyph count: " + font.NumGlyphs);
```
Bu kod parçacığı, yazı tipi adını ve içerdiği gliflerin sayısını yazdıracaktır.
## 3. Adım: Yazı Tipi Metriklerini Çıkarın
Yazı tipi ölçümleri, yazı tipinin özellikleri hakkında ayrıntılı bilgi sağlar.
### Yazı Tipi Metriklerini Görüntüle
```csharp
string metrics = string.Format(
    "Font metrics: ascender - {0}, descender - {1}, typo ascender = {2}, typo descender = {3}, UnitsPerEm = {4}",
    font.Metrics.Ascender, font.Metrics.Descender,
    font.Metrics.TypoAscender, font.Metrics.TypoDescender, font.Metrics.UnitsPerEM);
Console.WriteLine(metrics);
```
Bu kod parçası, yazı tipinin yükselen, azalan ve EM başına birimler gibi çeşitli ölçümlerini biçimlendirir ve yazdırır.
## Adım 4: CMap Unicode Tablosuna erişin
CMap tablosu, karakter kodlarının glif indeksleriyle eşleştirilmesine yardımcı olur.
### CMap Tablosunu Alma ve Kontrol Etme
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
Bu kod CMap tablosunu alır ve PlatformID ile PlatformSpecificID'yi yazdırır.
## Adım 5: Glif Bilgisini Alın
Son olarak, 'A' karakterinin glifi gibi belirli bir glif hakkında bilgi alalım.
### Glif Bilgilerini Al
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
Bu kod parçası, 'A' için glif dizinini alır, bu dizini kullanarak glifi alır ve sınırlayıcı kutu ve genişlik dahil ölçümlerini yazdırır.
## Çözüm
Tebrikler! Aspose.Font for .NET'i kullanarak yazı tipi ölçümlerini nasıl alacağınızı başarıyla öğrendiniz. Bu adımları izleyerek uygulamalarınızdaki yazı tipi bilgilerini kolayca çıkarabilir ve değiştirebilirsiniz. Bu eğitim, daha gelişmiş yazı tipi işlemleri için sağlam bir temel sağlamalıdır. Mutlu kodlama!
## SSS'ler
### S1: Aspose.Font for .NET'i diğer yazı tipi formatlarıyla kullanabilir miyim?
Evet, Aspose.Font for .NET; TrueType, OpenType, Type1 ve daha fazlasını içeren çeşitli yazı tipi formatlarını destekler.
### S2: Aspose.Font for .NET'in ücretsiz deneme sürümünü nereden edinebilirim?
 Ücretsiz deneme sürümünü şuradan indirebilirsiniz:[Aspose sürümler sayfası](https://releases.aspose.com/).
### S3: Aspose.Font for .NET lisansını nasıl satın alabilirim?
 adresinden lisans satın alabilirsiniz.[Satın alma sayfasını atayın](https://purchase.aspose.com/buy).
### S4: Aspose.Font for .NET için destek mevcut mu?
 Evet, destek alabilirsiniz[Aspose destek forumu](https://forum.aspose.com/c/font/41).
### S5: Aspose.Font for .NET'i ticari bir projede kullanabilir miyim?
Evet, Aspose.Font for .NET'i ticari projelerde kullanabilirsiniz ancak geçerli bir lisansa ihtiyacınız olacak.