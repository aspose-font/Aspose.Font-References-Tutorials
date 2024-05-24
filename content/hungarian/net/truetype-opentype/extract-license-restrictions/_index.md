---
title: Licenckorlátozások kibontása az Aspose.Fontból a .NET számára
linktitle: Licenckorlátozások kibontása az Aspose.Fontból a .NET számára
second_title: Aspose.Font .NET API
description: Részletes útmutatónkból megtudhatja, hogyan vonhatja ki a licenckorlátozásokat a TrueType betűtípusokból az Aspose.Font for .NET használatával. Tökéletes a .NET-ben betűtípusokkal dolgozó fejlesztőknek.
type: docs
weight: 11
url: /hu/net/truetype-opentype/extract-license-restrictions/
---
## Bevezetés
Halihó! Ha Ön .NET-alkalmazásokban betűkészletekkel foglalkozó fejlesztő, létfontosságú, hogy megértse a fontfájlokba ágyazott licenckorlátozásokat. Ez az átfogó útmutató végigvezeti a licenckorlátozások kibontásán a TrueType betűtípusokból az Aspose.Font for .NET használatával. Akár gondoskodik a betűtípus-licencnek való megfelelésről, akár csak kíváncsi az Ön által használt betűtípusok engedélyeire, mi gondoskodunk róla. Ennek az oktatóanyagnak a végére könnyedén ellenőrizheti bármelyik TrueType betűtípus licenckorlátozását. Készen állsz a merülésre? Kezdjük el!
## Előfeltételek
Mielőtt belevágnánk a kódba, győződjön meg arról, hogy rendelkezik a következőkkel:
-  Aspose.Font for .NET: Töltse le a[Az Aspose kiadási oldala](https://releases.aspose.com/font/net/).
- .NET fejlesztői környezet: Visual Studio vagy bármely más kompatibilis IDE.
- C# alapismeretek: C# programozás és .NET keretrendszer ismerete.
- Betűtípusfájl: TrueType betűtípusfájl, mint pl`Montserrat-Regular.ttf`.
## Névterek importálása
Az Aspose.Font for .NET használatának megkezdéséhez importálnia kell a szükséges névtereket. Ezek a névterek biztosítják a betűtípusok kezeléséhez szükséges osztályokat és metódusokat.
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
Most bontsuk le az egész folyamatot egyszerű lépésekre.
## 1. lépés: Töltse be a TrueType betűtípust
 Először is be kell töltenünk a TrueType betűtípust az alkalmazásunkba. Ez magában foglalja a fájl elérési útjának meghatározását és a`FontDefinition` tárgy.
## 1.1. lépés: Adja meg a betűtípus fájl elérési útját
Először adja meg a könyvtárat, ahol a fontfájl található, és adja meg a fájl teljes elérési útját.
```csharp
string dataDir = "Your Document Directory";
string fileName = dataDir + "Montserrat-Regular.ttf";
```
## 1.2. lépés: Hozzon létre egy FontDefinition objektumot
 Ezután hozzon létre a`FontDefinition` objektum a betűtípusadatok kezelésére. Ez a lépés magában foglalja a betűtípus és a fájlforrás megadását.
```csharp
FontDefinition fd = new FontDefinition(FontType.TTF, new FontFileDefinition("ttf", new FileSystemStreamSource(fileName)));
```
## 2. lépés: Nyissa meg a TrueType betűtípust
 A ... val`FontDefinition` objektum készen áll, a következő lépés a betűtípus megnyitása az Aspose.Font for .NET használatával.
## 2.1. lépés: Használja a Nyitott módszert
 Használja a`Open` módszere a`Font` osztályt a betűtípus betöltéséhez. A visszaküldött tárgyat a`TtfFont`.
```csharp
TtfFont font = Aspose.Font.Font.Open(fd) as TtfFont;
```
## 3. lépés: Licenckorlátozások kibontása
Most, hogy a betűtípus betöltődött, ideje kibontani a licenckorlátozásokat. Ez magában foglalja a betűtípus OS/2 táblázatának elérését és a licencjelzők lekérését.
## 3.1. lépés: Inicializálja a licencjelzőket
 Inicializálás a`LicenseFlags` tiltakozik a licencinformációk tárolására.
```csharp
LicenseFlags licenseFlags = null;
```
## 3.2. lépés: Ellenőrizze az OS/2 táblázatot
Ellenőrizze, hogy az OS/2 tábla létezik-e a betűtípusban, és ha igen, szerezze be a licencjelzőket.
```csharp
if (font.TtfTables.Os2Table != null)
{
    licenseFlags = font.TtfTables.Os2Table.GetLicenseFlags();
}
```
## 3.3. lépés: A licencjelzők értelmezése
Értelmezze a licencjelzőket, és adja ki a licenckorlátozásokat a beolvasott jelzők alapján.
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
## Következtetés
És megvan! Sikeresen megtanulta, hogyan vonhatja ki a licenckorlátozásokat a TrueType betűtípusokból az Aspose.Font for .NET használatával. Ez az útmutató végigvezeti Önt a .NET-alkalmazások betűtípusainak használatához szükséges alapvető lépéseken, biztosítva, hogy megfeleljen a licenckövetelményeknek. Ennek a tudásnak a birtokában magabiztosan kezelheti a betűtípusokat projektjeiben, tudván, hogy betartja a jogi irányelveket.
## GYIK
### 1. Mi az Aspose.Font for .NET?
Az Aspose.Font for .NET egy hatékony API, amely lehetővé teszi a fejlesztők számára, hogy fontfájlokkal dolgozzanak, lehetővé téve a betűtípusok betöltését, szerkesztését és mentését a .NET-alkalmazásokon belül.
### 2. Dolgozhatok más betűtípusokkal az Aspose.Font for .NET használatával?
Teljesen! Az Aspose.Font for .NET többféle betűtípust támogat, többek között a TTF-et, az OTF-et, a Type 1-et és a CFF-et.
### 3. Hogyan szerezhetek engedélyt az Aspose.Font .NET-hez?
 Engedélyt vásárolhat a[Aspose Vásárlás oldal](https://purchase.aspose.com/buy) . Értékelés céljából ideiglenes engedélyt kaphat[itt](https://purchase.aspose.com/temporary-license/).
### 4. Hol találok részletes dokumentációt?
 A részletes dokumentáció elérhető a[Aspose.Font a .NET dokumentációs oldalához](https://reference.aspose.com/font/net/).
### 5. Hogyan kaphatok támogatást, ha problémákba ütközöm?
 Támogatásért látogassa meg a[Aspose.Font támogatási fórum](https://forum.aspose.com/c/font/41).