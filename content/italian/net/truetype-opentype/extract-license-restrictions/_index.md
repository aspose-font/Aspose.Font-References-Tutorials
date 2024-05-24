---
title: Estrai le restrizioni di licenza in Aspose.Font per .NET
linktitle: Estrai le restrizioni di licenza in Aspose.Font per .NET
second_title: API Aspose.Font .NET
description: Scopri come estrarre le restrizioni di licenza dai caratteri TrueType utilizzando Aspose.Font per .NET con la nostra guida dettagliata. Perfetto per gli sviluppatori che lavorano con i caratteri in .NET.
type: docs
weight: 11
url: /it/net/truetype-opentype/extract-license-restrictions/
---
## introduzione
Ehilà! Se sei uno sviluppatore che lavora con tipi di carattere nelle applicazioni .NET, è fondamentale comprendere le restrizioni di licenza incorporate nei file di tipo di carattere. Questa guida completa ti guiderà attraverso l'estrazione delle restrizioni di licenza dai caratteri TrueType utilizzando Aspose.Font per .NET. Che tu stia garantendo la conformità con le licenze dei font o semplicemente curioso di conoscere le autorizzazioni dei font che stai utilizzando, abbiamo la soluzione per te. Entro la fine di questo tutorial, sarai in grado di controllare facilmente le restrizioni di licenza di qualsiasi carattere TrueType. Pronti a tuffarvi? Iniziamo!
## Prerequisiti
Prima di addentrarci nel codice, assicurati di avere quanto segue:
-  Aspose.Font per .NET: scaricalo dal file[Pagina delle versioni di Aspose](https://releases.aspose.com/font/net/).
- Ambiente di sviluppo .NET: Visual Studio o qualsiasi altro IDE compatibile.
- Conoscenza di base di C#: familiarità con la programmazione C# e il framework .NET.
- File di caratteri: un file di caratteri TrueType, ad esempio`Montserrat-Regular.ttf`.
## Importa spazi dei nomi
Per iniziare a utilizzare Aspose.Font per .NET, dovrai importare gli spazi dei nomi necessari. Questi spazi dei nomi forniranno le classi e i metodi richiesti per la manipolazione dei caratteri.
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
Ora suddividiamo l'intero processo in semplici passaggi.
## Passaggio 1: carica il carattere TrueType
 Per prima cosa dobbiamo caricare il carattere TrueType nella nostra applicazione. Ciò comporta la definizione del percorso del file e la creazione di un file`FontDefinition` oggetto.
## Passaggio 1.1: specificare il percorso del file del carattere
Inizia specificando la directory in cui si trova il file del carattere e il percorso completo del file.
```csharp
string dataDir = "Your Document Directory";
string fileName = dataDir + "Montserrat-Regular.ttf";
```
## Passaggio 1.2: creare un oggetto FontDefinition
 Successivamente, crea un file`FontDefinition` oggetto per gestire i dati dei caratteri. Questo passaggio prevede la specifica del tipo di carattere e dell'origine del file.
```csharp
FontDefinition fd = new FontDefinition(FontType.TTF, new FontFileDefinition("ttf", new FileSystemStreamSource(fileName)));
```
## Passaggio 2: apri il carattere TrueType
 Con il`FontDefinition` oggetto pronto, il passaggio successivo è aprire il carattere utilizzando Aspose.Font per .NET.
## Passaggio 2.1: utilizzare il metodo aperto
 Usa il`Open` metodo del`Font` classe per caricare il carattere. Trasmetti l'oggetto restituito a a`TtfFont`.
```csharp
TtfFont font = Aspose.Font.Font.Open(fd) as TtfFont;
```
## Passaggio 3: estrazione delle restrizioni di licenza
Ora che il carattere è caricato, è il momento di estrarre le restrizioni di licenza. Ciò comporta l'accesso alla tabella OS/2 del carattere e il recupero dei flag di licenza.
## Passaggio 3.1: inizializzare i flag di licenza
 Inizializzare a`LicenseFlags` opporsi alla memorizzazione delle informazioni sulla licenza.
```csharp
LicenseFlags licenseFlags = null;
```
## Passaggio 3.2: controllare la tabella OS/2
Controllare se la tabella OS/2 esiste nel carattere e, in caso affermativo, ottenere i contrassegni di licenza.
```csharp
if (font.TtfTables.Os2Table != null)
{
    licenseFlags = font.TtfTables.Os2Table.GetLicenseFlags();
}
```
## Passo 3.3: Interpretare i flag di licenza
Interpretare i flag di licenza e visualizzare le restrizioni di licenza in base ai flag recuperati.
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
## Conclusione
E il gioco è fatto! Hai imparato con successo come estrarre le restrizioni di licenza dai caratteri TrueType utilizzando Aspose.Font per .NET. Questa guida ti ha guidato attraverso i passaggi essenziali necessari per lavorare con i caratteri nelle tue applicazioni .NET, assicurandoti la conformità ai requisiti di licenza. Con questa conoscenza, puoi gestire con sicurezza i caratteri nei tuoi progetti, sapendo che stai rispettando le linee guida legali.
## Domande frequenti
### 1. Cos'è Aspose.Font per .NET?
Aspose.Font per .NET è una potente API che consente agli sviluppatori di lavorare con file di caratteri, consentendo il caricamento, la modifica e il salvataggio dei caratteri all'interno delle applicazioni .NET.
### 2. Posso lavorare con altri formati di carattere utilizzando Aspose.Font per .NET?
Assolutamente! Aspose.Font per .NET supporta più formati di caratteri, tra cui TTF, OTF, Type 1 e CFF, tra gli altri.
### 3. Come posso ottenere una licenza per Aspose.Font per .NET?
 È possibile acquistare una licenza da[Pagina di acquisto Aspose](https://purchase.aspose.com/buy) . A scopo di valutazione è possibile ottenere una licenza temporanea[Qui](https://purchase.aspose.com/temporary-license/).
### 4. Dove posso trovare la documentazione dettagliata?
 La documentazione dettagliata è disponibile su[Aspose.Font per la pagina della documentazione .NET](https://reference.aspose.com/font/net/).
### 5. Come posso ottenere supporto se riscontro problemi?
 Per supporto è possibile visitare il[Forum di supporto Aspose.Font](https://forum.aspose.com/c/font/41).