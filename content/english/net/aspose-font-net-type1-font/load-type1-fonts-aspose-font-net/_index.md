---
title: Load Type 1 Fonts in Aspose.Font for .NET
linktitle: Load Type 1 Fonts in Aspose.Font for .NET
second_title: Aspose.Font .NET API
description: 
type: docs
weight: 12
url: /net/aspose-font-net-type1-font/load-type1-fonts-aspose-font-net/
---

## Complete Source Code
```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;
using Aspose.Font.Sources;
using Aspose.Font.Type1;


namespace Aspose.Font.Examples.WorkingWithType1Fonts
{
    class LoadType1Fonts
    {
        public static void Run()
        {
            string dataDir = "Your Document Directory";
            //ExStart: 1
            string fileName = dataDir + "courier.pfb"; //Font file name with full path

            FontDefinition fd = new FontDefinition(FontType.Type1, new FontFileDefinition("pfb", new FileSystemStreamSource(fileName)));
            Type1Font font = Aspose.Font.Font.Open(fd) as Type1Font;
            //ExEnd: 1
        }
    }
}

```
