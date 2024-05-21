---
title: Load TrueType Fonts in Aspose.Font for .NET
linktitle: Load TrueType Fonts in Aspose.Font for .NET
second_title: Aspose.Font .NET API
description: 
type: docs
weight: 13
url: /net/truetype-opentype/load-truetype-fonts/
---

## Complete Source Code
```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;
using Aspose.Font.Sources;
using Aspose.Font.Ttf;

namespace Aspose.Font.Examples.WorkingWithTrueTypeAndOpenTypeFonts
{
    class LoadTrueTypeFonts
    {
        public static void Run()
        {
            string dataDir = "Your Document Directory";
            //ExStart: 1
            string fileName= dataDir + "Montserrat-Regular.ttf"; //Font file name with full path

            FontDefinition fd = new FontDefinition(FontType.TTF, new FontFileDefinition("ttf", new FileSystemStreamSource(fileName)));
            TtfFont ttfFont = Aspose.Font.Font.Open(fd) as TtfFont;
            //ExEnd: 1
        }
    }
}

```
