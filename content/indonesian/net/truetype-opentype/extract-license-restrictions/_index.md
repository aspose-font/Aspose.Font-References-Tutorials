---
title: Ekstrak Batasan Lisensi di Aspose.Font untuk .NET
linktitle: Ekstrak Batasan Lisensi di Aspose.Font untuk .NET
second_title: Aspose.Font .NET API
description: Pelajari cara mengekstrak batasan lisensi dari font TrueType menggunakan Aspose.Font untuk .NET dengan panduan terperinci kami. Sempurna untuk pengembang yang bekerja dengan font di .NET.
type: docs
weight: 11
url: /id/net/truetype-opentype/extract-license-restrictions/
---
## Perkenalan
Hai! Jika Anda seorang pengembang yang bekerja dengan font di aplikasi .NET, memahami batasan lisensi yang tertanam dalam file font sangatlah penting. Panduan komprehensif ini akan memandu Anda dalam mengekstraksi batasan lisensi dari font TrueType menggunakan Aspose.Font untuk .NET. Baik Anda memastikan kepatuhan terhadap lisensi font atau hanya ingin tahu tentang izin font yang Anda gunakan, kami siap membantu Anda. Di akhir tutorial ini, Anda akan dapat memeriksa font TrueType apa pun untuk mengetahui batasan lisensinya dengan mudah. Siap untuk terjun? Mari kita mulai!
## Prasyarat
Sebelum kita beralih ke kode, pastikan Anda memiliki yang berikut:
-  Aspose.Font untuk .NET: Unduh dari[Halaman rilis Aspose](https://releases.aspose.com/font/net/).
- Lingkungan Pengembangan .NET: Visual Studio atau IDE lain yang kompatibel.
- Pengetahuan Dasar C#: Keakraban dengan pemrograman C# dan kerangka .NET.
- File Font: File font TrueType, seperti`Montserrat-Regular.ttf`.
## Impor Namespace
Untuk mulai menggunakan Aspose.Font untuk .NET, Anda harus mengimpor namespace yang diperlukan. Namespace ini akan memberi Anda kelas dan metode yang diperlukan untuk manipulasi font.
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
Sekarang, mari kita bagi seluruh proses menjadi langkah-langkah sederhana.
## Langkah 1: Muat Font TrueType
 Pertama, kita perlu memuat font TrueType ke dalam aplikasi kita. Ini melibatkan penentuan jalur file dan pembuatan file`FontDefinition` obyek.
## Langkah 1.1: Tentukan Jalur File Font
Mulailah dengan menentukan direktori tempat file font Anda berada dan path lengkap ke file tersebut.
```csharp
string dataDir = "Your Document Directory";
string fileName = dataDir + "Montserrat-Regular.ttf";
```
## Langkah 1.2: Buat Objek FontDefinition
 Selanjutnya, buat a`FontDefinition` objek untuk mengelola data font. Langkah ini melibatkan penentuan jenis font dan sumber file.
```csharp
FontDefinition fd = new FontDefinition(FontType.TTF, new FontFileDefinition("ttf", new FileSystemStreamSource(fileName)));
```
## Langkah 2: Buka Font TrueType
 Dengan`FontDefinition` objek sudah siap, langkah selanjutnya adalah membuka font menggunakan Aspose.Font for .NET.
## Langkah 2.1: Gunakan Metode Terbuka
 Menggunakan`Open` metode`Font` kelas untuk memuat font. Transmisikan objek yang dikembalikan ke a`TtfFont`.
```csharp
TtfFont font = Aspose.Font.Font.Open(fd) as TtfFont;
```
## Langkah 3: Ekstrak Pembatasan Lisensi
Sekarang font telah dimuat, saatnya untuk mengekstrak batasan lisensi. Ini melibatkan akses tabel OS/2 font dan mengambil flag lisensi.
## Langkah 3.1: Inisialisasi Bendera Lisensi
 Inisialisasi a`LicenseFlags` keberatan untuk menyimpan informasi lisensi.
```csharp
LicenseFlags licenseFlags = null;
```
## Langkah 3.2: Periksa Tabel OS/2
Periksa apakah tabel OS/2 ada di font dan dapatkan tanda lisensi jika ada.
```csharp
if (font.TtfTables.Os2Table != null)
{
    licenseFlags = font.TtfTables.Os2Table.GetLicenseFlags();
}
```
## Langkah 3.3: Menafsirkan Bendera Lisensi
Interpretasikan tanda lisensi dan keluarkan batasan lisensi berdasarkan tanda yang diambil.
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
## Kesimpulan
Dan itu dia! Anda telah berhasil mempelajari cara mengekstrak batasan lisensi dari font TrueType menggunakan Aspose.Font untuk .NET. Panduan ini telah memandu Anda melalui langkah-langkah penting yang diperlukan untuk bekerja dengan font di aplikasi .NET Anda, memastikan Anda mematuhi persyaratan lisensi. Dengan pengetahuan ini, Anda dapat dengan percaya diri mengelola font di proyek Anda, mengetahui bahwa Anda mematuhi pedoman hukum.
## FAQ
### 1. Apa itu Aspose.Font untuk .NET?
Aspose.Font untuk .NET adalah API canggih yang memungkinkan pengembang bekerja dengan file font, memungkinkan pemuatan, pengeditan, dan penyimpanan font dalam aplikasi .NET.
### 2. Bisakah saya bekerja dengan format font lain menggunakan Aspose.Font untuk .NET?
Sangat! Aspose.Font untuk .NET mendukung berbagai format font, antara lain TTF, OTF, Tipe 1, dan CFF.
### 3. Bagaimana cara mendapatkan lisensi Aspose.Font untuk .NET?
 Anda dapat membeli lisensi dari[Asumsikan halaman Pembelian](https://purchase.aspose.com/buy) . Untuk tujuan evaluasi, Anda bisa mendapatkan lisensi sementara[Di Sini](https://purchase.aspose.com/temporary-license/).
### 4. Di mana saya dapat menemukan dokumentasi detailnya?
 Dokumentasi terperinci tersedia di[Aspose.Font untuk halaman dokumentasi .NET](https://reference.aspose.com/font/net/).
### 5. Bagaimana saya bisa mendapatkan dukungan jika saya mengalami masalah?
 Untuk dukungan, Anda dapat mengunjungi[Forum dukungan Aspose.Font](https://forum.aspose.com/c/font/41).