---
title: Laden Sie die CFF-Schriftart in Aspose.Font für .NET
linktitle: Laden Sie die CFF-Schriftart in Aspose.Font für .NET
second_title: Aspose.Font .NET API
description: In diesem Handbuch erfahren Sie, wie Sie CFF-Schriftarten mit Aspose.Font für .NET laden. Perfekt für Entwickler, die ihre .NET-Anwendungen mit benutzerdefinierten Schriftarten verbessern möchten.
type: docs
weight: 10
url: /de/net/cff-font-handling/load-cff-font/
---
## Einführung
Willkommen zu Ihrem Leitfaden zum Laden von CFF-Schriftarten (Compact Font Format) mit Aspose.Font für .NET! Wenn Sie benutzerdefinierte Schriftarten in Ihre .NET-Anwendungen integrieren möchten, sind Sie hier richtig. Dieses Schritt-für-Schritt-Tutorial führt Sie durch den gesamten Prozess, vom Einrichten Ihrer Umgebung bis zum Extrahieren detaillierter Schriftmetriken. Am Ende dieses Leitfadens haben Sie ein solides Verständnis für den Umgang mit CFF-Schriftarten und können Ihre Projekte mit einzigartigen typografischen Elementen hervorheben. Bereit, einzutauchen? Dann legen wir los!
## Voraussetzungen
Bevor wir uns in den Code vertiefen, stellen wir sicher, dass Sie alles haben, was Sie brauchen:
- Visual Studio: Stellen Sie sicher, dass Sie Visual Studio installiert haben.
- Aspose.Font für .NET: Laden Sie die Aspose.Font für .NET-Bibliothek herunter und installieren Sie sie von der[Download-Link](https://releases.aspose.com/font/net/).
- Grundkenntnisse in C#: Wenn Sie mit C# vertraut sind, können Sie den Beispielen leichter folgen.
- Eine CFF-Schriftdatei: Halten Sie eine Compact Font Format-Datei (.cff) bereit. Sie können für dieses Tutorial jede beliebige .cff-Datei verwenden.
Nachdem diese Voraussetzungen erfüllt sind, fahren wir mit den erforderlichen Namespaces fort.
## Namespaces importieren
Um mit Aspose.Font für .NET zu arbeiten, müssen Sie die entsprechenden Namespaces in Ihr Projekt einbinden. So geht's:
```csharp
using Aspose.Font.Cff;
using Aspose.Font.Sources;
using System;
using System.Collections.Generic;
using System.IO;
using System.Linq;
using System.Text;
using System.Threading.Tasks;
```
Diese Namespaces sind für die Handhabung von Schriftarten in Ihrer .NET-Anwendung von entscheidender Bedeutung.
## Schritt 1: Laden Sie die Schriftartdatei
Der erste Schritt besteht darin, die CFF-Schriftdatei in Ihre Anwendung zu laden. So geht's:
### Font-Datei laden
1. Definieren Sie den Pfad zu Ihrer Schriftartdatei.
2.  Ein ... kreieren`FontDefinition` Objekt.
3.  Verwenden Sie die`Font.Open` Methode zum Laden der Schriftart.
```csharp
string dataDir = "Your Document Directory";
string fileName = dataDir + "OpenSans-Regular.cff";
FontDefinition fd = new FontDefinition(FontType.CFF, new FontFileDefinition("cff", new FileSystemStreamSource(fileName)));
CffFont cffFont = Aspose.Font.Font.Open(fd) as CffFont;
```
 In diesem Snippet definieren wir die Schriftart und den Speicherort mit dem`FontDefinition` Klasse, und laden Sie dann die Schriftart in eine`CffFont` Objekt mit dem`Font.Open` Methode.
## Schritt 2: Grundlegende Schriftinformationen abrufen
Sobald die Schriftart geladen ist, können Sie einige grundlegende Informationen darüber abrufen.
### Abrufen des Schriftnamens und der Anzahl der Glyphen
```csharp
string name = cffFont.FontName;
Console.WriteLine("Font name: " + name);
Console.WriteLine("Glyph count: " + cffFont.NumGlyphs);
```
Dieser Codeausschnitt druckt den Schriftnamen und die Anzahl der enthaltenen Glyphen und gibt Ihnen so einen schnellen Überblick über Ihre geladene Schriftart.
## Schritt 3: Extrahieren von Schriftmetriken
Schriftmetriken liefern detaillierte Informationen zu den Eigenschaften der Schriftart.
### Anzeige von Schriftmetriken
```csharp
string metrics = string.Format(
    "Font metrics: ascender - {0}, descender - {1}, units per em = {2}",
    cffFont.Metrics.Ascender, cffFont.Metrics.Descender, cffFont.Metrics.UnitsPerEM);
Console.WriteLine(metrics);
```
Dieser Code formatiert und druckt verschiedene Maße der Schriftart, wie Oberlänge, Unterlänge und Einheiten pro EM, und gibt Ihnen Einblick in die Abmessungen der Schriftart.
## Schritt 4: Auf Schriftglyphen zugreifen
Glyphen sind die visuelle Darstellung von Zeichen. Lassen Sie uns Informationen zu einer bestimmten Glyphe abrufen, beispielsweise zur Glyphe für das Zeichen „A“.
### Glypheninformationen abrufen
```csharp
//Vorausgesetzt, die Schriftart verfügt über eine Methode zum Abrufen von Glyphen nach Zeichen oder Index
int glyphIndex = cffFont.GetGlyphIndex('A');
if (glyphIndex >= 0)
{
    Glyph glyph = cffFont.GetGlyphById(glyphIndex);
    if (glyph != null)
    {
        Console.WriteLine("Glyph metrics for 'A' symbol:");
        string bbox = string.Format(
            "Glyph BBox: Xmin = {0}, Xmax = {1}, Ymin = {2}, Ymax = {3}",
            glyph.GlyphBBox.XMin, glyph.GlyphBBox.XMax, glyph.GlyphBBox.YMin, glyph.GlyphBBox.YMax);
        Console.WriteLine(bbox);
        Console.WriteLine("Width: " + cffFont.Metrics.GetGlyphWidth(glyphIndex));
    }
}
```
Dieser Codeausschnitt ruft den Glyphenindex für „A“ ab, holt die Glyphe unter Verwendung dieses Indexes und druckt ihre Maße, einschließlich Begrenzungsrahmen und Breite.
## Schritt 5: Schriftarttabellen handhaben
Schriftarttabellen enthalten verschiedene Daten zur Schriftart. Für CFF-Schriftarten könnten Sie an Tabellen wie der CharStrings-Tabelle interessiert sein.
### Zugreifen auf und Anzeigen von Schriftarttabellen
```csharp
var charStringsTable = cffFont.CFFTables.CharStrings;
if (charStringsTable != null)
{
    foreach (var entry in charStringsTable.Entries)
    {
        Console.WriteLine($"Glyph name: {entry.Key}, Glyph data: {entry.Value}");
    }
}
```
Dieser Codeausschnitt greift auf die CharStrings-Tabelle zu und druckt jeden Glyphennamen zusammen mit seinen Daten aus, wodurch Sie ein tieferes Verständnis der Struktur der Schriftart erhalten.
## Abschluss
Herzlichen Glückwunsch! Sie haben erfolgreich gelernt, wie Sie CFF-Schriftarten mit Aspose.Font für .NET laden und handhaben. Wenn Sie diese Schritte befolgen, können Sie benutzerdefinierte Schriftarten problemlos in Ihre .NET-Anwendungen integrieren und so deren visuelle Attraktivität und Funktionalität verbessern. Egal, ob Sie an digitalen Designprojekten arbeiten, Software entwickeln oder irgendetwas dazwischen tun, die Beherrschung der Schriftartenhandhabung ist eine wertvolle Fähigkeit. Viel Spaß beim Programmieren!
## Häufig gestellte Fragen
### F1: Kann ich Aspose.Font für .NET mit anderen Schriftformaten verwenden?
Ja, Aspose.Font für .NET unterstützt verschiedene Schriftformate, darunter TrueType, OpenType und Type1.
### F2: Wo kann ich eine kostenlose Testversion von Aspose.Font für .NET erhalten?
 Sie können eine kostenlose Testversion herunterladen von der[Aspose-Veröffentlichungsseite](https://releases.aspose.com/).
### F3: Wie kaufe ich eine Lizenz für Aspose.Font für .NET?
 Sie können eine Lizenz erwerben bei der[Aspose-Kaufseite](https://purchase.aspose.com/buy).
### F4: Gibt es Unterstützung für Aspose.Font für .NET?
 Ja, Sie erhalten Unterstützung von der[Aspose-Supportforum](https://forum.aspose.com/c/font/41).
### F5: Kann ich Aspose.Font für .NET in einem kommerziellen Projekt verwenden?
Ja, Sie können Aspose.Font für .NET in kommerziellen Projekten verwenden, aber Sie benötigen eine gültige Lizenz.
