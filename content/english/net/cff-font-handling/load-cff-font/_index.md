---
title: Load CFF Font in Aspose.Font for .NET
linktitle: Load CFF Font in Aspose.Font for .NET
second_title: Aspose.Font .NET API
description: 
type: docs
weight: 10
url: /net/cff-font-handling/load-cff-font/
---

## Complete Source Code
```csharp
using Aspose.Font.Cff;
using Aspose.Font.Sources;
using System;
using System.Collections.Generic;
using System.IO;
using System.Linq;
using System.Text;
using System.Threading.Tasks;

namespace Aspose.Font.Examples.WorkingWithCFFFonts
{
    class LoadCFFFont
    {
        public static void Run()
        {
            string dataDir = "Your Document Directory";
            //ExStart: LoadCFFFromDisc
            string fileName = dataDir + "OpenSans-Regular.cff"; //Font file name with full path

            FontDefinition fd = new FontDefinition(FontType.CFF, new FontFileDefinition("cff", new FileSystemStreamSource(fileName)));
            CffFont ttfFont = Aspose.Font.Font.Open(fd) as CffFont;
            //ExEnd: LoadCFFFromDisc
        }

        public static void LoadCffFromByteArray()
        {
            string dataDir = "Your Document Directory";
            //ExStart: LoadCffFromByteArray
            byte[] fontMemoryData = File.ReadAllBytes(dataDir + "OpenSans-Regular.cff");
            FontDefinition fd = new FontDefinition(FontType.CFF, new FontFileDefinition("cff", new ByteContentStreamSource(fontMemoryData)));
            CffFont cffFont = Aspose.Font.Font.Open(fd) as CffFont;
            //ExEnd: LoadCffFromByteArray
        }
    }
}

```
