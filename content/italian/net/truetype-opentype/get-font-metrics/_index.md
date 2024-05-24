---
title: Ottieni le metriche dei caratteri in Aspose.Font per .NET
linktitle: Ottieni le metriche dei caratteri in Aspose.Font per .NET
second_title: API Aspose.Font .NET
description: Scopri come ottenere le metriche dei caratteri utilizzando Aspose.Font per .NET. Guida passo passo con esempi di codice. Prerequisiti e domande frequenti inclusi. #Aspose #Font
type: docs
weight: 12
url: /it/net/truetype-opentype/get-font-metrics/
---
## introduzione
Aspose.Font per .NET è una potente API che consente agli sviluppatori di lavorare con i caratteri nelle loro applicazioni .NET. Sia che tu abbia bisogno di estrarre metriche dei caratteri, manipolare glifi o accedere ai dati dei caratteri, Aspose.Font fornisce funzionalità complete per semplificare le attività relative ai caratteri. In questo tutorial esploreremo come ottenere le metriche dei caratteri utilizzando Aspose.Font per .NET.
## Prerequisiti
Prima di immergerti in questo tutorial, assicurati di aver impostato i seguenti prerequisiti:
### 1. Aspose.Font per l'installazione .NET
 Assicurati di avere Aspose.Font per .NET installato nel tuo ambiente di sviluppo. Se non l'hai già fatto, puoi scaricare l'API dal file[Aspose.Releases](https://releases.aspose.com/font/net/) o tramite Gestione pacchetti NuGet.
### 2. Impostazione dell'ambiente di sviluppo
Assicurati di avere un ambiente di sviluppo .NET configurato con Visual Studio o qualsiasi altro IDE compatibile installato.

## Importa spazi dei nomi
Nella tua applicazione .NET, devi importare gli spazi dei nomi necessari per lavorare con Aspose.Font per .NET.
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
Ora suddividiamo l'esempio fornito in più passaggi e spieghiamo ciascuno di essi in dettaglio.
## Passaggio 1: definire il percorso del file dei caratteri
Innanzitutto, definisci il percorso del file del carattere con cui vuoi lavorare.
```csharp
string dataDir = "Your Document Directory";
string fileName = dataDir + "Montserrat-Regular.ttf"; //Nome del file del carattere con percorso completo
```
## Passaggio 2: aprire il file dei caratteri
Successivamente, apri il file del carattere utilizzando l'API Aspose.Font.
```csharp
FontDefinition fd = new FontDefinition(FontType.TTF, new FontFileDefinition("ttf", new FileSystemStreamSource(fileName)));
TtfFont font = Aspose.Font.Font.Open(fd) as TtfFont;
```
## Passaggio 3: recuperare le metriche dei caratteri
Recupera varie metriche dei caratteri come ascendente, discendente, ecc.
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
## Passaggio 4: ottieni la tabella di codifica Unicode
Recupera la tabella di codifica Unicode (cmap) dal carattere.
```csharp
Aspose.Font.TtfCMapFormats.TtfCMapFormatBaseTable cmapTable = null;
if (font.TtfTables.CMapTable != null)
{
    cmapTable = font.TtfTables.CMapTable.FindUnicodeTable();
}
```
## Passaggio 5: accedi alle informazioni sui glifi
Accedi alle informazioni sui glifi per un simbolo specifico (ad esempio, "A").
```csharp
char unicode = (char)65; // Unicode per "A"
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
## Conclusione
In questo tutorial, abbiamo spiegato come ottenere le metriche dei caratteri utilizzando Aspose.Font per .NET. Seguendo la guida passo passo e comprendendo i prerequisiti, puoi lavorare in modo efficiente con i caratteri nelle tue applicazioni .NET utilizzando l'API Aspose.Font.
## Domande frequenti
### 1. Posso utilizzare Aspose.Font per .NET con qualsiasi formato di file di caratteri?
Sì, Aspose.Font per .NET supporta vari formati di caratteri come TrueType (TTF), OpenType (OTF) e altri.
### 2. È disponibile una prova gratuita per Aspose.Font per .NET?
 Sì, puoi ottenere una prova gratuita di Aspose.Font per .NET da[sito web](https://releases.aspose.com/).
### 3. Come posso accedere al supporto per Aspose.Font per .NET?
 È possibile accedere al supporto per Aspose.Font per .NET tramite il[Forum](https://forum.aspose.com/c/font/41).
### 4. Posso acquistare una licenza temporanea per Aspose.Font per .NET?
 Sì, puoi acquistare una licenza temporanea da[Aspose negozio](https://purchase.aspose.com/temporary-license/).
### 5. È disponibile documentazione per Aspose.Font per .NET?
 Sì, puoi accedere alla documentazione di Aspose.Font per .NET[Qui](https://reference.aspose.com/font/net/).