---
title: Ottieni le metriche dei caratteri in Aspose.Font per .NET Type 1
linktitle: Ottieni le metriche dei caratteri in Aspose.Font per .NET Type 1
second_title: API Aspose.Font .NET
description: Scopri come ottenere le metriche dei caratteri utilizzando Aspose.Font per .NET in questo tutorial completo e dettagliato. Perfetto per gli sviluppatori di qualsiasi livello!
type: docs
weight: 11
url: /it/net/aspose-font-net-type1-font/get-font-metrics-aspose-font-net-type1/
---
## introduzione
Benvenuti nella guida definitiva su come ottenere le metriche dei caratteri utilizzando Aspose.Font per .NET! Che tu sia uno sviluppatore esperto o che tu stia semplicemente immergendo i piedi nel mondo dei caratteri, questo tutorial ti guiderà attraverso il processo passo dopo passo. Al termine di questo articolo sarai in grado di estrarre metriche dettagliate sui caratteri e di capire come manipolarle nelle tue applicazioni .NET. Quindi, tuffiamoci e iniziamo con questo emozionante viaggio!
## Prerequisiti
Prima di addentrarci nel nocciolo della questione, ci sono alcune cose che dovrai avere a posto:
- Visual Studio: assicurati di avere Visual Studio installato sul tuo computer.
-  Aspose.Font per .NET: scarica e installa la libreria Aspose.Font per .NET. Puoi ottenerlo da[Link per scaricare](https://releases.aspose.com/font/net/).
- Conoscenza di base di C#: è necessaria la familiarità con la programmazione C# da seguire insieme agli esempi.
- Un file di caratteri: tenere pronto un file di caratteri TrueType (.ttf). È possibile utilizzare qualsiasi file .ttf per questo tutorial.
Ora che abbiamo tutto pronto, iniziamo importando gli spazi dei nomi necessari.
## Importa spazi dei nomi
Per iniziare a lavorare con Aspose.Font per .NET, dovrai includere gli spazi dei nomi appropriati nel tuo progetto. Ecco come farlo:
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
Con questi spazi dei nomi in atto, sei pronto per iniziare a lavorare con i tipi di carattere nella tua applicazione .NET.
## Passaggio 1: caricare il file dei caratteri
Innanzitutto, devi caricare il file del carattere nella tua applicazione. Ecco come farlo:
### Carica file di caratteri
1. Definisci il percorso del file del carattere. 
2.  Creare un`FontDefinition` oggetto.
3.  Usa il`Font.Open` metodo per caricare il carattere.
```csharp
string dataDir = "Your Document Directory";
string fileName = dataDir + "Montserrat-Regular.ttf";
FontDefinition fd = new FontDefinition(FontType.TTF, new FontFileDefinition("ttf", new FileSystemStreamSource(fileName)));
TtfFont font = Aspose.Font.Font.Open(fd) as TtfFont;
```
 Qui stiamo usando il`FontDefinition` class per definire il tipo e la posizione del nostro file di font. IL`Font.Open` Il metodo carica il carattere in a`TtfFont` oggetto.
## Passaggio 2: recuperare le informazioni di base sui caratteri
Una volta caricato il carattere, puoi recuperare alcune informazioni di base su di esso.
### Ottieni il nome del carattere e il conteggio dei glifi
```csharp
string name = font.FontName;
Console.WriteLine("Font name: " + name);
Console.WriteLine("Glyph count: " + font.NumGlyphs);
```
Questo frammento di codice stamperà il nome del carattere e il numero di glifi che contiene.
## Passaggio 3: estrazione delle metriche dei caratteri
Le metriche dei caratteri forniscono informazioni dettagliate sulle caratteristiche del carattere.
### Visualizza le metriche dei caratteri
```csharp
string metrics = string.Format(
    "Font metrics: ascender - {0}, descender - {1}, typo ascender = {2}, typo descender = {3}, UnitsPerEm = {4}",
    font.Metrics.Ascender, font.Metrics.Descender,
    font.Metrics.TypoAscender, font.Metrics.TypoDescender, font.Metrics.UnitsPerEM);
Console.WriteLine(metrics);
```
Questo snippet formatta e stampa varie metriche del carattere, come ascendente, discendente e unità per EM.
## Passaggio 4: accedere alla tabella Unicode CMap
La tabella CMap aiuta a mappare i codici dei caratteri sugli indici dei glifi.
### Recupera e controlla la tabella CMap
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
Questo codice recupera la tabella CMap e stampa PlatformID e PlatformSpecificID.
## Passaggio 5: ottieni informazioni sui glifi
Infine, recuperiamo le informazioni su un glifo specifico, come il glifo del carattere "A".
### Recupera informazioni sui glifi
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
Questo frammento ottiene l'indice del glifo per "A", recupera il glifo utilizzando questo indice e stampa le sue metriche, inclusi il riquadro di delimitazione e la larghezza.
## Conclusione
Congratulazioni! Hai imparato con successo come ottenere le metriche dei caratteri utilizzando Aspose.Font per .NET. Seguendo questi passaggi, puoi facilmente estrarre e manipolare le informazioni sui caratteri nelle tue applicazioni. Questo tutorial dovrebbe fornire una solida base per operazioni sui font più avanzate. Buona programmazione!
## Domande frequenti
### Q1: posso utilizzare Aspose.Font per .NET con altri formati di caratteri?
Sì, Aspose.Font per .NET supporta vari formati di caratteri tra cui TrueType, OpenType, Type1 e altri.
### Q2: Dove posso ottenere una prova gratuita di Aspose.Font per .NET?
 È possibile scaricare una versione di prova gratuita da[Pagina delle versioni di Aspose](https://releases.aspose.com/).
### Q3: Come posso acquistare una licenza per Aspose.Font per .NET?
 È possibile acquistare una licenza da[Aspose la pagina di acquisto](https://purchase.aspose.com/buy).
### Q4: è disponibile il supporto per Aspose.Font per .NET?
 Sì, puoi ottenere supporto da[Aspose forum di supporto](https://forum.aspose.com/c/font/41).
### Q5: Posso utilizzare Aspose.Font per .NET in un progetto commerciale?
Sì, puoi utilizzare Aspose.Font per .NET in progetti commerciali, ma avrai bisogno di una licenza valida.