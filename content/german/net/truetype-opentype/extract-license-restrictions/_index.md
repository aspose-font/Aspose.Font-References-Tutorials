---
title: Extrahieren Sie Lizenzbeschränkungen in Aspose.Font für .NET
linktitle: Extrahieren Sie Lizenzbeschränkungen in Aspose.Font für .NET
second_title: Aspose.Font .NET API
description: Erfahren Sie in unserem ausführlichen Handbuch, wie Sie mit Aspose.Font für .NET Lizenzbeschränkungen aus TrueType-Schriftarten extrahieren. Perfekt für Entwickler, die mit Schriftarten in .NET arbeiten.
type: docs
weight: 11
url: /de/net/truetype-opentype/extract-license-restrictions/
---
## Einführung
Hallo! Wenn Sie als Entwickler mit Schriftarten in .NET-Anwendungen arbeiten, ist es wichtig, die in Schriftartdateien eingebetteten Lizenzbeschränkungen zu verstehen. Diese umfassende Anleitung führt Sie durch das Extrahieren von Lizenzbeschränkungen aus TrueType-Schriftarten mithilfe von Aspose.Font für .NET. Egal, ob Sie die Einhaltung der Schriftartlizenzen sicherstellen möchten oder einfach nur neugierig auf die Berechtigungen der von Ihnen verwendeten Schriftarten sind, wir haben alles für Sie. Am Ende dieses Tutorials können Sie jede TrueType-Schriftart problemlos auf ihre Lizenzbeschränkungen überprüfen. Bereit, loszulegen? Dann legen wir los!
## Voraussetzungen
Bevor wir in den Code einsteigen, stellen Sie sicher, dass Sie über Folgendes verfügen:
-  Aspose.Font für .NET: Laden Sie es herunter von der[Aspose-Veröffentlichungsseite](https://releases.aspose.com/font/net/).
- .NET-Entwicklungsumgebung: Visual Studio oder eine andere kompatible IDE.
- Grundkenntnisse in C#: Vertrautheit mit der C#-Programmierung und dem .NET-Framework.
- Schriftdatei: Eine TrueType-Schriftdatei, wie etwa`Montserrat-Regular.ttf`.
## Namespaces importieren
Um Aspose.Font für .NET verwenden zu können, müssen Sie die erforderlichen Namespaces importieren. Diese Namespaces stellen Ihnen die für die Schriftartbearbeitung erforderlichen Klassen und Methoden zur Verfügung.
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
Lassen Sie uns nun den gesamten Prozess in einfache Schritte unterteilen.
## Schritt 1: Laden Sie die TrueType-Schriftart
 Zuerst müssen wir die TrueType-Schriftart in unsere Anwendung laden. Dazu müssen wir den Dateipfad definieren und eine`FontDefinition` Objekt.
## Schritt 1.1: Geben Sie den Pfad für die Schriftartdatei an
Geben Sie zunächst das Verzeichnis an, in dem sich Ihre Schriftartdatei befindet, und den vollständigen Pfad zur Datei.
```csharp
string dataDir = "Your Document Directory";
string fileName = dataDir + "Montserrat-Regular.ttf";
```
## Schritt 1.2: Erstellen eines FontDefinition-Objekts
 Erstellen Sie als Nächstes eine`FontDefinition` Objekt zum Verwalten der Schriftdaten. In diesem Schritt werden der Schrifttyp und die Dateiquelle angegeben.
```csharp
FontDefinition fd = new FontDefinition(FontType.TTF, new FontFileDefinition("ttf", new FileSystemStreamSource(fileName)));
```
## Schritt 2: Öffnen Sie die TrueType-Schriftart
 Mit dem`FontDefinition` Objekt bereit, der nächste Schritt besteht darin, die Schriftart mit Aspose.Font für .NET zu öffnen.
## Schritt 2.1: Verwenden der Open-Methode
 Verwenden Sie die`Open` Methode der`Font` Klasse zum Laden der Schriftart. Konvertieren Sie das zurückgegebene Objekt in`TtfFont`.
```csharp
TtfFont font = Aspose.Font.Font.Open(fd) as TtfFont;
```
## Schritt 3: Lizenzbeschränkungen extrahieren
Nachdem die Schriftart nun geladen ist, ist es an der Zeit, die Lizenzbeschränkungen zu extrahieren. Dazu müssen Sie auf die OS/2-Tabelle der Schriftart zugreifen und die Lizenzflags abrufen.
## Schritt 3.1: Lizenz-Flags initialisieren
 Initialisieren Sie einen`LicenseFlags` Objekt zum Speichern der Lizenzinformationen.
```csharp
LicenseFlags licenseFlags = null;
```
## Schritt 3.2: OS/2-Tabelle prüfen
Überprüfen Sie, ob die OS/2-Tabelle in der Schriftart vorhanden ist, und holen Sie sich ggf. die Lizenzflags.
```csharp
if (font.TtfTables.Os2Table != null)
{
    licenseFlags = font.TtfTables.Os2Table.GetLicenseFlags();
}
```
## Schritt 3.3: Lizenz-Flags interpretieren
Interpretieren Sie die Lizenzflags und geben Sie die Lizenzbeschränkungen basierend auf den abgerufenen Flags aus.
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
## Abschluss
Und da haben Sie es! Sie haben erfolgreich gelernt, wie Sie mit Aspose.Font für .NET Lizenzbeschränkungen aus TrueType-Schriftarten extrahieren. Dieser Leitfaden hat Sie durch die wesentlichen Schritte geführt, die zum Arbeiten mit Schriftarten in Ihren .NET-Anwendungen erforderlich sind, und stellt sicher, dass Sie die Lizenzanforderungen erfüllen. Mit diesem Wissen können Sie Schriftarten in Ihren Projekten sicher verwalten und wissen, dass Sie die gesetzlichen Richtlinien einhalten.
## Häufig gestellte Fragen
### 1. Was ist Aspose.Font für .NET?
Aspose.Font für .NET ist eine leistungsstarke API, die Entwicklern die Arbeit mit Schriftdateien ermöglicht und das Laden, Bearbeiten und Speichern von Schriftarten in .NET-Anwendungen ermöglicht.
### 2. Kann ich mit Aspose.Font für .NET mit anderen Schriftformaten arbeiten?
Absolut! Aspose.Font für .NET unterstützt mehrere Schriftformate, darunter unter anderem TTF, OTF, Type 1 und CFF.
### 3. Wie erhalte ich eine Lizenz für Aspose.Font für .NET?
 Sie können eine Lizenz erwerben bei der[Aspose-Kaufseite](https://purchase.aspose.com/buy) . Zu Testzwecken können Sie eine temporäre Lizenz erwerben[Hier](https://purchase.aspose.com/temporary-license/).
### 4. Wo finde ich ausführliche Dokumentation?
 Eine ausführliche Dokumentation finden Sie auf der[Aspose.Font für .NET-Dokumentationsseite](https://reference.aspose.com/font/net/).
### 5. Wie erhalte ich Unterstützung, wenn Probleme auftreten?
 Für Unterstützung besuchen Sie bitte die[Aspose.Font Support-Forum](https://forum.aspose.com/c/font/41).