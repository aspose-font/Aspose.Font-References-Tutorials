---
title: Holen Sie sich Schriftmetriken in Aspose.Font für .NET
linktitle: Holen Sie sich Schriftmetriken in Aspose.Font für .NET
second_title: Aspose.Font .NET API
description: Erfahren Sie, wie Sie mit Aspose.Font für .NET Schriftmetriken erhalten. Schritt-für-Schritt-Anleitung mit Codebeispielen. Voraussetzungen und FAQs enthalten. #Aspose #Font
type: docs
weight: 12
url: /de/net/truetype-opentype/get-font-metrics/
---
## Einführung
Aspose.Font für .NET ist eine leistungsstarke API, die es Entwicklern ermöglicht, mit Schriftarten in ihren .NET-Anwendungen zu arbeiten. Ob Sie nun Schriftmetriken extrahieren, Glyphen bearbeiten oder auf Schriftdaten zugreifen müssen, Aspose.Font bietet umfassende Funktionen zur Optimierung von schriftbezogenen Aufgaben. In diesem Tutorial erfahren Sie, wie Sie mit Aspose.Font für .NET Schriftmetriken abrufen.
## Voraussetzungen
Bevor Sie mit diesem Tutorial beginnen, stellen Sie sicher, dass die folgenden Voraussetzungen erfüllt sind:
### 1. Aspose.Font für .NET-Installation
 Stellen Sie sicher, dass Aspose.Font für .NET in Ihrer Entwicklungsumgebung installiert ist. Falls noch nicht geschehen, können Sie die API von der[Aspose.Veröffentlichungen](https://releases.aspose.com/font/net/) oder über den NuGet-Paketmanager.
### 2. Einrichten der Entwicklungsumgebung
Stellen Sie sicher, dass Sie eine .NET-Entwicklungsumgebung mit Visual Studio oder einer anderen kompatiblen IDE installiert haben.

## Namespaces importieren
In Ihrer .NET-Anwendung müssen Sie die erforderlichen Namespaces importieren, um mit Aspose.Font für .NET zu arbeiten.
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
Lassen Sie uns nun das bereitgestellte Beispiel in mehrere Schritte aufteilen und jeden im Detail erläutern.
## Schritt 1: Definieren Sie den Pfad für die Schriftartdatei
Definieren Sie zunächst den Dateipfad der Schriftart, mit der Sie arbeiten möchten.
```csharp
string dataDir = "Your Document Directory";
string fileName = dataDir + "Montserrat-Regular.ttf"; //Schriftartdateiname mit vollständigem Pfad
```
## Schritt 2: Öffnen Sie die Schriftartdatei
Öffnen Sie als Nächstes die Schriftdatei mithilfe der Aspose.Font-API.
```csharp
FontDefinition fd = new FontDefinition(FontType.TTF, new FontFileDefinition("ttf", new FileSystemStreamSource(fileName)));
TtfFont font = Aspose.Font.Font.Open(fd) as TtfFont;
```
## Schritt 3: Abrufen von Schriftmetriken
Rufen Sie verschiedene Schriftmetriken wie Oberlänge, Unterlänge usw. ab.
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
## Schritt 4: Unicode-Kodierungstabelle abrufen
Rufen Sie die Unicode-Kodierungstabelle (cmap) aus der Schriftart ab.
```csharp
Aspose.Font.TtfCMapFormats.TtfCMapFormatBaseTable cmapTable = null;
if (font.TtfTables.CMapTable != null)
{
    cmapTable = font.TtfTables.CMapTable.FindUnicodeTable();
}
```
## Schritt 5: Auf Glypheninformationen zugreifen
Greifen Sie auf Glypheninformationen für ein bestimmtes Symbol zu (z. B. „A“).
```csharp
char unicode = (char)65; // Unicode für 'A'
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
## Abschluss
In diesem Tutorial haben wir erläutert, wie Sie mit Aspose.Font für .NET Schriftmetriken abrufen. Wenn Sie der Schritt-für-Schritt-Anleitung folgen und die Voraussetzungen verstehen, können Sie mithilfe der Aspose.Font-API effizient mit Schriftarten in Ihren .NET-Anwendungen arbeiten.
## Häufig gestellte Fragen
### 1. Kann ich Aspose.Font für .NET mit jedem Schriftdateiformat verwenden?
Ja, Aspose.Font für .NET unterstützt verschiedene Schriftformate wie TrueType (TTF), OpenType (OTF) und mehr.
### 2. Gibt es eine kostenlose Testversion für Aspose.Font für .NET?
 Ja, Sie können eine kostenlose Testversion von Aspose.Font für .NET erhalten von der[Webseite](https://releases.aspose.com/).
### 3. Wie kann ich auf Support für Aspose.Font für .NET zugreifen?
 Sie können auf den Support für Aspose.Font für .NET zugreifen über die[Forum](https://forum.aspose.com/c/font/41).
### 4. Kann ich eine temporäre Lizenz für Aspose.Font für .NET erwerben?
 Ja, Sie können eine temporäre Lizenz erwerben bei der[Aspose-Shop](https://purchase.aspose.com/temporary-license/).
### 5. Gibt es Dokumentation für Aspose.Font für .NET?
 Ja, Sie können auf die Dokumentation für Aspose.Font für .NET zugreifen[Hier](https://reference.aspose.com/font/net/).