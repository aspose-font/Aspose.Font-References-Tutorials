---
title: Aspose.Font for .NET'te Lisans Kısıtlamalarını Çıkarın
linktitle: Aspose.Font for .NET'te Lisans Kısıtlamalarını Çıkarın
second_title: Aspose.Font .NET API'si
description: Ayrıntılı kılavuzumuzla Aspose.Font for .NET kullanarak TrueType yazı tiplerinden lisans kısıtlamalarını nasıl çıkaracağınızı öğrenin. .NET'te yazı tipleriyle çalışan geliştiriciler için mükemmeldir.
type: docs
weight: 11
url: /tr/net/truetype-opentype/extract-license-restrictions/
---
## giriiş
Selam! .NET uygulamalarındaki yazı tipleriyle çalışan bir geliştiriciyseniz, yazı tipi dosyalarına katıştırılmış lisans kısıtlamalarını anlamak çok önemlidir. Bu kapsamlı kılavuz, Aspose.Font for .NET kullanarak TrueType yazı tiplerinden lisans kısıtlamalarını çıkarma konusunda size yol gösterecektir. İster yazı tipi lisanslamasına uygunluğu sağlıyor olun, ister sadece kullandığınız yazı tiplerinin izinlerini merak ediyor olun, yanınızdayız. Bu eğitimin sonunda herhangi bir TrueType yazı tipinin lisans kısıtlamalarını kolayca kontrol edebileceksiniz. Dalmaya hazır mısınız? Başlayalım!
## Önkoşullar
Koda geçmeden önce aşağıdakilere sahip olduğunuzdan emin olun:
-  Aspose.Font for .NET: Şu adresten indirin:[Aspose sürümler sayfası](https://releases.aspose.com/font/net/).
- .NET Geliştirme Ortamı: Visual Studio veya başka bir uyumlu IDE.
- Temel C# Bilgisi: C# programlama ve .NET çerçevesine aşinalık.
- Yazı Tipi Dosyası: Bir TrueType yazı tipi dosyası, örneğin`Montserrat-Regular.ttf`.
## Ad Alanlarını İçe Aktar
Aspose.Font for .NET'i kullanmaya başlamak için gerekli ad alanlarını içe aktarmanız gerekir. Bu ad alanları size yazı tipi manipülasyonu için gereken sınıfları ve yöntemleri sağlayacaktır.
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
Şimdi tüm süreci basit adımlara ayıralım.
## 1. Adım: TrueType Yazı Tipini Yükleyin
 Öncelikle TrueType yazı tipini uygulamamıza yüklememiz gerekiyor. Bu, dosya yolunu tanımlamayı ve bir`FontDefinition` nesne.
## Adım 1.1: Yazı Tipi Dosya Yolunu Belirleyin
Yazı tipi dosyanızın bulunduğu dizini ve dosyanın tam yolunu belirterek başlayın.
```csharp
string dataDir = "Your Document Directory";
string fileName = dataDir + "Montserrat-Regular.ttf";
```
## Adım 1.2: FontDefinition Nesnesi Oluşturun
 Sonra bir tane oluşturun`FontDefinition` yazı tipi verilerini yönetmek için nesne. Bu adım, yazı tipi türünü ve dosya kaynağını belirtmeyi içerir.
```csharp
FontDefinition fd = new FontDefinition(FontType.TTF, new FontFileDefinition("ttf", new FileSystemStreamSource(fileName)));
```
## 2. Adım: TrueType Yazı Tipini açın
 İle`FontDefinition` nesne hazırsa bir sonraki adım yazı tipini Aspose.Font for .NET kullanarak açmaktır.
## Adım 2.1: Açık Yöntemi Kullanın
 Kullan`Open` yöntemi`Font` Yazı tipini yüklemek için sınıf. Döndürülen nesneyi bir`TtfFont`.
```csharp
TtfFont font = Aspose.Font.Font.Open(fd) as TtfFont;
```
## 3. Adım: Lisans Kısıtlamalarını Çıkarın
Artık yazı tipi yüklendiğine göre lisans kısıtlamalarını çıkarmanın zamanı geldi. Bu, yazı tipinin OS/2 tablosuna erişmeyi ve lisans işaretlerini almayı içerir.
## Adım 3.1: Lisans Bayraklarını Başlatın
 Bir başlat`LicenseFlags` Lisans bilgilerinin saklanmasına itiraz edin.
```csharp
LicenseFlags licenseFlags = null;
```
## Adım 3.2: OS/2 Tablosunu Kontrol Edin
Yazı tipinde OS/2 tablosunun mevcut olup olmadığını kontrol edin ve varsa lisans bayraklarını alın.
```csharp
if (font.TtfTables.Os2Table != null)
{
    licenseFlags = font.TtfTables.Os2Table.GetLicenseFlags();
}
```
## Adım 3.3: Lisans Bayraklarını Yorumlayın
Lisans bayraklarını yorumlayın ve alınan bayraklara göre lisans kısıtlamalarının çıktısını alın.
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
## Çözüm
İşte buyur! Aspose.Font for .NET kullanarak TrueType yazı tiplerinden lisans kısıtlamalarının nasıl çıkarılacağını başarıyla öğrendiniz. Bu kılavuz, lisans gerekliliklerine uymanızı sağlayarak, .NET uygulamalarınızdaki yazı tipleriyle çalışmak için gereken temel adımları size anlatmıştır. Bu bilgiyle, projelerinizdeki yazı tiplerini, yasal yönergelere uyduğunuzu bilerek güvenle yönetebilirsiniz.
## SSS'ler
### 1. Aspose.Font for .NET nedir?
Aspose.Font for .NET, geliştiricilerin font dosyalarıyla çalışmasına olanak tanıyan, .NET uygulamaları içerisinde font yükleme, düzenleme ve kaydetme olanağı sağlayan güçlü bir API'dir.
### 2. Aspose.Font for .NET'i kullanarak diğer yazı tipi formatlarıyla çalışabilir miyim?
Kesinlikle! Aspose.Font for .NET, diğerlerinin yanı sıra TTF, OTF, Type 1 ve CFF dahil olmak üzere birden fazla yazı tipi formatını destekler.
### 3. Aspose.Font for .NET lisansını nasıl alabilirim?
 adresinden lisans satın alabilirsiniz.[Satın Alma sayfasını düşünün](https://purchase.aspose.com/buy) . Değerlendirme amacıyla geçici bir lisans alabilirsiniz[Burada](https://purchase.aspose.com/temporary-license/).
### 4. Ayrıntılı belgeleri nerede bulabilirim?
 Ayrıntılı belgeler şu adreste mevcuttur:[Aspose.Font for .NET dokümantasyon sayfası](https://reference.aspose.com/font/net/).
### 5. Sorunla karşılaşırsam nasıl destek alabilirim?
 Destek için şu adresi ziyaret edebilirsiniz:[Aspose.Font destek forumu](https://forum.aspose.com/c/font/41).