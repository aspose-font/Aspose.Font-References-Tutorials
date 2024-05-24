---
title: Holen Sie sich Schriftmetriken in Aspose.Font für .NET Typ 1
linktitle: Holen Sie sich Schriftmetriken in Aspose.Font für .NET Typ 1
second_title: Aspose.Font .NET API
description: Erfahren Sie in diesem umfassenden Schritt-für-Schritt-Tutorial, wie Sie mit Aspose.Font für .NET Schriftmetriken erhalten. Perfekt für Entwickler auf jedem Niveau!
type: docs
weight: 11
url: /de/net/aspose-font-net-type1-font/get-font-metrics-aspose-font-net-type1/
---
## Einführung
Willkommen zum ultimativen Leitfaden zum Abrufen von Schriftmetriken mit Aspose.Font für .NET! Egal, ob Sie ein erfahrener Entwickler sind oder gerade erst in die Welt der Schriftarten eintauchen, dieses Tutorial führt Sie Schritt für Schritt durch den Prozess. Am Ende dieses Artikels können Sie detaillierte Schriftmetriken extrahieren und verstehen, wie Sie diese in Ihren .NET-Anwendungen bearbeiten können. Tauchen Sie also ein und beginnen Sie diese aufregende Reise!
## Voraussetzungen
Bevor wir ins Detail gehen, müssen Sie einige Dinge vorbereitet haben:
- Visual Studio: Stellen Sie sicher, dass Visual Studio auf Ihrem Computer installiert ist.
-  Aspose.Font für .NET: Laden Sie die Aspose.Font für .NET-Bibliothek herunter und installieren Sie sie. Sie erhalten sie von der[Download-Link](https://releases.aspose.com/font/net/).
- Grundkenntnisse in C#: Um den Beispielen folgen zu können, sind Kenntnisse in der C#-Programmierung erforderlich.
- Eine Schriftdatei: Halten Sie eine TrueType-Schriftdatei (.ttf) bereit. Sie können für dieses Tutorial jede beliebige .ttf-Datei verwenden.
Nachdem wir nun alles vorbereitet haben, beginnen wir mit dem Importieren der erforderlichen Namespaces.
## Namespaces importieren
Um mit Aspose.Font für .NET arbeiten zu können, müssen Sie die entsprechenden Namespaces in Ihr Projekt einbinden. So geht's:
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
Wenn diese Namespaces eingerichtet sind, können Sie mit der Arbeit mit Schriftarten in Ihrer .NET-Anwendung beginnen.
## Schritt 1: Laden Sie die Schriftartdatei
Zuerst müssen Sie die Schriftartdatei in Ihre Anwendung laden. So geht's:
### Font-Datei laden
1. Definieren Sie den Pfad zu Ihrer Schriftartdatei. 
2.  Ein ... kreieren`FontDefinition` Objekt.
3.  Verwenden Sie die`Font.Open` Methode zum Laden der Schriftart.
```csharp
string dataDir = "Your Document Directory";
string fileName = dataDir + "Montserrat-Regular.ttf";
FontDefinition fd = new FontDefinition(FontType.TTF, new FontFileDefinition("ttf", new FileSystemStreamSource(fileName)));
TtfFont font = Aspose.Font.Font.Open(fd) as TtfFont;
```
 Hier verwenden wir die`FontDefinition` Klasse, um den Typ und den Speicherort unserer Schriftdatei zu definieren. Die`Font.Open` Methode lädt die Schriftart in eine`TtfFont` Objekt.
## Schritt 2: Grundlegende Schriftinformationen abrufen
Sobald die Schriftart geladen ist, können Sie einige grundlegende Informationen darüber abrufen.
### Abrufen des Schriftnamens und der Anzahl der Glyphen
```csharp
string name = font.FontName;
Console.WriteLine("Font name: " + name);
Console.WriteLine("Glyph count: " + font.NumGlyphs);
```
Dieser Codeausschnitt druckt den Schriftnamen und die Anzahl der darin enthaltenen Glyphen.
## Schritt 3: Extrahieren von Schriftmetriken
Schriftmetriken liefern detaillierte Informationen zu den Eigenschaften der Schriftart.
### Anzeige von Schriftmetriken
```csharp
string metrics = string.Format(
    "Font metrics: ascender - {0}, descender - {1}, typo ascender = {2}, typo descender = {3}, UnitsPerEm = {4}",
    font.Metrics.Ascender, font.Metrics.Descender,
    font.Metrics.TypoAscender, font.Metrics.TypoDescender, font.Metrics.UnitsPerEM);
Console.WriteLine(metrics);
```
Dieser Codeausschnitt formatiert und druckt verschiedene Maße der Schriftart, wie Oberlänge, Unterlänge und Einheiten pro EM.
## Schritt 4: Zugriff auf die CMap Unicode-Tabelle
Die CMap-Tabelle hilft beim Zuordnen von Zeichencodes zu Glyphenindizes.
### CMap-Tabelle abrufen und prüfen
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
Dieser Code ruft die CMap-Tabelle ab und druckt die PlatformID und PlatformSpecificID.
## Schritt 5: Glypheninformationen abrufen
Lassen Sie uns abschließend Informationen zu einem bestimmten Glyph abrufen, beispielsweise zum Glyph für das Zeichen „A“.
### Glypheninformationen abrufen
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
Dieser Codeausschnitt ruft den Glyphindex für „A“ ab, ruft den Glyph mithilfe dieses Indexes ab und druckt seine Maße, einschließlich Begrenzungsrahmen und Breite.
## Abschluss
Herzlichen Glückwunsch! Sie haben erfolgreich gelernt, wie Sie mit Aspose.Font für .NET Schriftmetriken abrufen. Indem Sie diese Schritte befolgen, können Sie Schriftinformationen in Ihren Anwendungen problemlos extrahieren und bearbeiten. Dieses Tutorial sollte eine solide Grundlage für fortgeschrittenere Schriftoperationen bieten. Viel Spaß beim Programmieren!
## Häufig gestellte Fragen
### F1: Kann ich Aspose.Font für .NET mit anderen Schriftformaten verwenden?
Ja, Aspose.Font für .NET unterstützt verschiedene Schriftformate, darunter TrueType, OpenType, Type1 und mehr.
### F2: Wo kann ich eine kostenlose Testversion von Aspose.Font für .NET erhalten?
 Sie können eine kostenlose Testversion herunterladen von der[Aspose-Veröffentlichungsseite](https://releases.aspose.com/).
### F3: Wie kaufe ich eine Lizenz für Aspose.Font für .NET?
 Sie können eine Lizenz erwerben bei der[Aspose-Kaufseite](https://purchase.aspose.com/buy).
### F4: Gibt es Unterstützung für Aspose.Font für .NET?
 Ja, Sie erhalten Unterstützung von der[Aspose-Supportforum](https://forum.aspose.com/c/font/41).
### F5: Kann ich Aspose.Font für .NET in einem kommerziellen Projekt verwenden?
Ja, Sie können Aspose.Font für .NET in kommerziellen Projekten verwenden, aber Sie benötigen eine gültige Lizenz.