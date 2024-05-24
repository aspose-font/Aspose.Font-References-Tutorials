---
title: Λάβετε μετρήσεις γραμματοσειράς στο Aspose.Font για .NET Type 1
linktitle: Λάβετε μετρήσεις γραμματοσειράς στο Aspose.Font για .NET Type 1
second_title: Aspose.Font .NET API
description: Μάθετε πώς να λαμβάνετε μετρήσεις γραμματοσειρών χρησιμοποιώντας το Aspose.Font για .NET σε αυτόν τον αναλυτικό, βήμα προς βήμα εκμάθηση. Ιδανικό για προγραμματιστές σε οποιοδήποτε επίπεδο!
type: docs
weight: 11
url: /el/net/aspose-font-net-type1-font/get-font-metrics-aspose-font-net-type1/
---
## Εισαγωγή
Καλώς ήρθατε στον απόλυτο οδηγό για τη λήψη μετρήσεων γραμματοσειρών χρησιμοποιώντας το Aspose.Font για .NET! Είτε είστε έμπειρος προγραμματιστής είτε απλώς βυθίζετε τα δάχτυλα των ποδιών σας στον κόσμο των γραμματοσειρών, αυτό το σεμινάριο θα σας καθοδηγήσει στη διαδικασία βήμα προς βήμα. Μέχρι το τέλος αυτού του άρθρου, θα μπορείτε να εξαγάγετε λεπτομερείς μετρήσεις γραμματοσειράς και να κατανοήσετε πώς να τις χειρίζεστε στις εφαρμογές σας .NET. Λοιπόν, ας βουτήξουμε και ας ξεκινήσουμε με αυτό το συναρπαστικό ταξίδι!
## Προαπαιτούμενα
Πριν βουτήξουμε στο νιφάκι, υπάρχουν μερικά πράγματα που θα πρέπει να έχετε στη θέση του:
- Visual Studio: Βεβαιωθείτε ότι έχετε εγκαταστήσει το Visual Studio στον υπολογιστή σας.
-  Aspose.Font για .NET: Κάντε λήψη και εγκατάσταση της βιβλιοθήκης Aspose.Font για .NET. Μπορείτε να το πάρετε από το[σύνδεσμος λήψης](https://releases.aspose.com/font/net/).
- Βασικές γνώσεις C#: Η εξοικείωση με τον προγραμματισμό C# είναι απαραίτητη για να ακολουθήσει μαζί με τα παραδείγματα.
- Ένα αρχείο γραμματοσειράς: Έχετε έτοιμο ένα αρχείο γραμματοσειράς TrueType (.ttf). Μπορείτε να χρησιμοποιήσετε οποιοδήποτε αρχείο .ttf για αυτό το σεμινάριο.
Τώρα που τα έχουμε όλα έτοιμα, ας ξεκινήσουμε εισάγοντας τους απαραίτητους χώρους ονομάτων.
## Εισαγωγή χώρων ονομάτων
Για να ξεκινήσετε να εργάζεστε με το Aspose.Font για .NET, θα πρέπει να συμπεριλάβετε τους κατάλληλους χώρους ονομάτων στο έργο σας. Δείτε πώς το κάνετε:
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
Με αυτούς τους χώρους ονομάτων στη θέση τους, είστε έτοιμοι να αρχίσετε να εργάζεστε με γραμματοσειρές στην εφαρμογή σας .NET.
## Βήμα 1: Φορτώστε το αρχείο γραμματοσειράς
Πρώτα, πρέπει να φορτώσετε το αρχείο γραμματοσειράς στην εφαρμογή σας. Έτσι το κάνεις:
### Φόρτωση αρχείου γραμματοσειράς
1. Καθορίστε τη διαδρομή προς το αρχείο γραμματοσειράς σας. 
2.  Δημιουργώ ένα`FontDefinition` αντικείμενο.
3.  Χρησιμοποιήστε το`Font.Open` μέθοδος φόρτωσης της γραμματοσειράς.
```csharp
string dataDir = "Your Document Directory";
string fileName = dataDir + "Montserrat-Regular.ttf";
FontDefinition fd = new FontDefinition(FontType.TTF, new FontFileDefinition("ttf", new FileSystemStreamSource(fileName)));
TtfFont font = Aspose.Font.Font.Open(fd) as TtfFont;
```
 Εδώ, χρησιμοποιούμε το`FontDefinition` κλάση για να ορίσουμε τον τύπο και τη θέση του αρχείου γραμματοσειράς μας. ο`Font.Open` μέθοδος φορτώνει τη γραμματοσειρά σε a`TtfFont` αντικείμενο.
## Βήμα 2: Ανάκτηση βασικών πληροφοριών γραμματοσειράς
Μόλις φορτωθεί η γραμματοσειρά, μπορείτε να ανακτήσετε κάποιες βασικές πληροφορίες σχετικά με αυτήν.
### Λάβετε το όνομα γραμματοσειράς και τον αριθμό των γλυφών
```csharp
string name = font.FontName;
Console.WriteLine("Font name: " + name);
Console.WriteLine("Glyph count: " + font.NumGlyphs);
```
Αυτό το απόσπασμα κώδικα θα εκτυπώσει το όνομα της γραμματοσειράς και τον αριθμό των γλυφών που περιέχει.
## Βήμα 3: Εξαγωγή μετρήσεων γραμματοσειράς
Οι μετρήσεις γραμματοσειράς παρέχουν λεπτομερείς πληροφορίες σχετικά με τα χαρακτηριστικά της γραμματοσειράς.
### Εμφάνιση μετρήσεων γραμματοσειράς
```csharp
string metrics = string.Format(
    "Font metrics: ascender - {0}, descender - {1}, typo ascender = {2}, typo descender = {3}, UnitsPerEm = {4}",
    font.Metrics.Ascender, font.Metrics.Descender,
    font.Metrics.TypoAscender, font.Metrics.TypoDescender, font.Metrics.UnitsPerEM);
Console.WriteLine(metrics);
```
Αυτό το απόσπασμα μορφοποιεί και εκτυπώνει διάφορες μετρήσεις της γραμματοσειράς, όπως ανοδική, φθίνουσα και μονάδες ανά EM.
## Βήμα 4: Πρόσβαση στον πίνακα Unicode CMap
Ο πίνακας CMap βοηθά στην αντιστοίχιση κωδικών χαρακτήρων σε δείκτες γλυφών.
### Ανακτήστε και ελέγξτε τον πίνακα CMap
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
Αυτός ο κώδικας ανακτά τον πίνακα CMap και εκτυπώνει το PlatformID και το PlatformSpecificID.
## Βήμα 5: Λάβετε πληροφορίες για τη γλυφή
Τέλος, ας ανακτήσουμε πληροφορίες για μια συγκεκριμένη γλυφή, όπως η γλυφή για τον χαρακτήρα «Α».
### Ανάκτηση πληροφοριών γλυφών
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
Αυτό το απόσπασμα λαμβάνει το ευρετήριο της γλυφής για το "A", ανακτά τη γλυφή χρησιμοποιώντας αυτό το ευρετήριο και εκτυπώνει τις μετρήσεις του, συμπεριλαμβανομένου του πλαισίου οριοθέτησης και του πλάτους.
## συμπέρασμα
Συγχαρητήρια! Μάθατε με επιτυχία πώς να λαμβάνετε μετρήσεις γραμματοσειρών χρησιμοποιώντας το Aspose.Font για .NET. Ακολουθώντας αυτά τα βήματα, μπορείτε εύκολα να εξαγάγετε και να χειρίζεστε πληροφορίες γραμματοσειράς στις εφαρμογές σας. Αυτό το σεμινάριο θα πρέπει να παρέχει μια σταθερή βάση για πιο προηγμένες λειτουργίες γραμματοσειράς. Καλή κωδικοποίηση!
## Συχνές ερωτήσεις
### Ε1: Μπορώ να χρησιμοποιήσω το Aspose.Font για .NET με άλλες μορφές γραμματοσειράς;
Ναι, το Aspose.Font for .NET υποστηρίζει διάφορες μορφές γραμματοσειράς, συμπεριλαμβανομένων των TrueType, OpenType, Type1 και άλλων.
### Ε2: Πού μπορώ να λάβω μια δωρεάν δοκιμή του Aspose.Font για .NET;
 Μπορείτε να κατεβάσετε μια δωρεάν δοκιμή από το[Σελίδα εκδόσεων Aspose](https://releases.aspose.com/).
### Ε3: Πώς μπορώ να αγοράσω μια άδεια χρήσης για το Aspose.Font για .NET;
 Μπορείτε να αγοράσετε άδεια από το[Σελίδα αγοράς Aspose](https://purchase.aspose.com/buy).
### Ε4: Υπάρχει διαθέσιμη υποστήριξη για το Aspose.Font για .NET;
 Ναι, μπορείτε να λάβετε υποστήριξη από το[Aspose forum υποστήριξης](https://forum.aspose.com/c/font/41).
### Ε5: Μπορώ να χρησιμοποιήσω το Aspose.Font για .NET σε ένα εμπορικό έργο;
Ναι, μπορείτε να χρησιμοποιήσετε το Aspose.Font για .NET σε εμπορικά έργα, αλλά θα χρειαστείτε έγκυρη άδεια χρήσης.