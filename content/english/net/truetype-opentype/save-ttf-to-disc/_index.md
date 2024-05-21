---
title: Save TTF to Disc using Aspose.Font for .NET
linktitle: Save TTF to Disc using Aspose.Font for .NET
second_title: Aspose.Font .NET API
description: 
type: docs
weight: 15
url: /net/truetype-opentype/save-ttf-to-disc/
---

## Complete Source Code
```csharp
using Aspose.Font.Sources;
using Aspose.Font.Ttf;
using System;
using System.Collections.Generic;
using System.IO;
using System.Linq;
using System.Text;
using System.Threading.Tasks;

namespace Aspose.Font.Examples.WorkingWithTrueTypeAndOpenTypeFonts
{
    class SaveTTFToDisc
    {
        public static void Run()
        {
            //ExStart: 1
            //byte array to load Font from
            string dataDir = "Your Document Directory";
            
            byte[] fontMemoryData = File.ReadAllBytes(dataDir + "Montserrat-Regular.ttf");
            FontDefinition fd = new FontDefinition(FontType.TTF, new FontFileDefinition("ttf", new ByteContentStreamSource(fontMemoryData)));
            TtfFont ttfFont = Aspose.Font.Font.Open(fd) as TtfFont;

            //Work with data from just loaded TtfFont object

            //Save CffFont to disk
            //Output Font file name with full path
            string outputFile = "Your Document Directory" + "Montserrat-Regular_out.ttf";

            ttfFont.Save(outputFile);
            //ExEnd: 1
        }
    }
}

```
