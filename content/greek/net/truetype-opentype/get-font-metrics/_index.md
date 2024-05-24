---
title: Λάβετε μετρήσεις γραμματοσειράς στο Aspose.Font για .NET
linktitle: Λάβετε μετρήσεις γραμματοσειράς στο Aspose.Font για .NET
second_title: Aspose.Font .NET API
description: Μάθετε πώς να λαμβάνετε μετρήσεις γραμματοσειρών χρησιμοποιώντας το Aspose.Font για .NET. Οδηγός βήμα προς βήμα με παραδείγματα κώδικα. Περιλαμβάνονται προαπαιτούμενα και συχνές ερωτήσεις. #Aspose #Font
type: docs
weight: 12
url: /el/net/truetype-opentype/get-font-metrics/
---
## Εισαγωγή
Το Aspose.Font for .NET είναι ένα ισχυρό API που επιτρέπει στους προγραμματιστές να εργάζονται με γραμματοσειρές στις εφαρμογές τους .NET. Είτε θέλετε να εξαγάγετε μετρήσεις γραμματοσειράς, να χειριστείτε γλυφές ή να αποκτήσετε πρόσβαση σε δεδομένα γραμματοσειρών, το Aspose.Font παρέχει ολοκληρωμένη λειτουργικότητα για τον εξορθολογισμό των εργασιών που σχετίζονται με τις γραμματοσειρές. Σε αυτό το σεμινάριο, θα εξερευνήσουμε πώς να λαμβάνετε μετρήσεις γραμματοσειρών χρησιμοποιώντας το Aspose.Font για .NET.
## Προαπαιτούμενα
Πριν προχωρήσετε σε αυτό το σεμινάριο, βεβαιωθείτε ότι έχετε ρυθμίσει τις ακόλουθες προϋποθέσεις:
### 1. Aspose.Font για εγκατάσταση .NET
 Βεβαιωθείτε ότι έχετε εγκατεστημένο το Aspose.Font for .NET στο περιβάλλον ανάπτυξης σας. Εάν δεν το έχετε κάνει ήδη, μπορείτε να κάνετε λήψη του API από το[Aspose.Απαλλαγές](https://releases.aspose.com/font/net/) ή μέσω του διαχειριστή πακέτων NuGet.
### 2. Ρύθμιση περιβάλλοντος ανάπτυξης
Βεβαιωθείτε ότι έχετε ρυθμίσει ένα περιβάλλον ανάπτυξης .NET με εγκατεστημένο το Visual Studio ή οποιοδήποτε άλλο συμβατό IDE.

## Εισαγωγή χώρων ονομάτων
Στην εφαρμογή σας .NET, πρέπει να εισαγάγετε τους απαραίτητους χώρους ονομάτων για να εργαστείτε με το Aspose.Font για .NET.
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
Τώρα, ας αναλύσουμε το παράδειγμα που παρέχεται σε πολλά βήματα και ας εξηγήσουμε το καθένα λεπτομερώς.
## Βήμα 1: Καθορίστε τη διαδρομή αρχείου γραμματοσειράς
Αρχικά, ορίστε τη διαδρομή αρχείου της γραμματοσειράς με την οποία θέλετε να εργαστείτε.
```csharp
string dataDir = "Your Document Directory";
string fileName = dataDir + "Montserrat-Regular.ttf"; //Όνομα αρχείου γραμματοσειράς με πλήρη διαδρομή
```
## Βήμα 2: Ανοίξτε το Αρχείο γραμματοσειράς
Στη συνέχεια, ανοίξτε το αρχείο γραμματοσειράς χρησιμοποιώντας το Aspose.Font API.
```csharp
FontDefinition fd = new FontDefinition(FontType.TTF, new FontFileDefinition("ttf", new FileSystemStreamSource(fileName)));
TtfFont font = Aspose.Font.Font.Open(fd) as TtfFont;
```
## Βήμα 3: Ανάκτηση μετρήσεων γραμματοσειράς
Ανακτήστε διάφορες μετρήσεις γραμματοσειράς όπως ανοδική, φθίνουσα κ.λπ.
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
## Βήμα 4: Λήψη πίνακα κωδικοποίησης Unicode
Ανακτήστε τον πίνακα κωδικοποίησης Unicode (cmap) από τη γραμματοσειρά.
```csharp
Aspose.Font.TtfCMapFormats.TtfCMapFormatBaseTable cmapTable = null;
if (font.TtfTables.CMapTable != null)
{
    cmapTable = font.TtfTables.CMapTable.FindUnicodeTable();
}
```
## Βήμα 5: Πρόσβαση στις Πληροφορίες Γλυφικού
Πρόσβαση σε πληροφορίες γλυφών για ένα συγκεκριμένο σύμβολο (π.χ. 'A').
```csharp
char unicode = (char)65; // Unicode για το 'A'
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
## συμπέρασμα
Σε αυτό το σεμινάριο, καλύψαμε πώς να λαμβάνετε μετρήσεις γραμματοσειράς χρησιμοποιώντας το Aspose.Font για .NET. Ακολουθώντας τον οδηγό βήμα προς βήμα και κατανοώντας τις προϋποθέσεις, μπορείτε να εργαστείτε αποτελεσματικά με γραμματοσειρές στις εφαρμογές σας .NET χρησιμοποιώντας το Aspose.Font API.
## Συχνές ερωτήσεις
### 1. Μπορώ να χρησιμοποιήσω το Aspose.Font για .NET με οποιαδήποτε μορφή αρχείου γραμματοσειράς;
Ναι, το Aspose.Font for .NET υποστηρίζει διάφορες μορφές γραμματοσειράς όπως TrueType (TTF), OpenType (OTF) και άλλες.
### 2. Υπάρχει διαθέσιμη δωρεάν δοκιμή για το Aspose.Font για .NET;
 Ναι, μπορείτε να λάβετε μια δωρεάν δοκιμή του Aspose.Font για .NET από το[δικτυακός τόπος](https://releases.aspose.com/).
### 3. Πώς μπορώ να έχω πρόσβαση στην υποστήριξη του Aspose.Font για .NET;
 Μπορείτε να αποκτήσετε πρόσβαση στην υποστήριξη για Aspose.Font για .NET μέσω του[δικαστήριο](https://forum.aspose.com/c/font/41).
### 4. Μπορώ να αγοράσω μια προσωρινή άδεια χρήσης για το Aspose.Font για .NET;
 Ναι, μπορείτε να αγοράσετε μια προσωρινή άδεια από το[Κατάστημα Aspose](https://purchase.aspose.com/temporary-license/).
### 5. Υπάρχει διαθέσιμη τεκμηρίωση για το Aspose.Font για .NET;
 Ναι, μπορείτε να αποκτήσετε πρόσβαση στην τεκμηρίωση για το Aspose.Font για .NET[εδώ](https://reference.aspose.com/font/net/).