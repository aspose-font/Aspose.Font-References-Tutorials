---
title: Detect Latin Symbols Support in TrueType Fonts
linktitle: Detect Latin Symbols Support in TrueType Fonts
second_title: Aspose.Font .NET API
description: 
type: docs
weight: 10
url: /net/truetype-opentype/detect-latin-symbols-support-truetype-fonts/
---

## Complete Source Code
```csharp
using Aspose.Font.Glyphs;
using Aspose.Font.Sources;
using Aspose.Font.Ttf;
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;

namespace Aspose.Font.Examples.WorkingWithTrueTypeAndOpenTypeFonts
{
    class DetectLatinSymbolsSupport
    {
        public static void Run()
        {
            string dataDir = "Your Document Directory";
            //ExStart: 1
            string fileName = dataDir + "Montserrat-Regular.ttf"; //Font file name with full path

            FontDefinition fd = new FontDefinition(FontType.TTF, new FontFileDefinition("ttf", new FileSystemStreamSource(fileName)));
            TtfFont ttfFont = Aspose.Font.Font.Open(fd) as TtfFont;

            bool latinText = true;


            for (uint code = 65; code < 123; code++)
            {
                GlyphId gid = ttfFont.Encoding.DecodeToGid(code);
                if (gid == null || gid == GlyphUInt32Id.NotDefId)
                {
                    latinText = false;
                }
            }

            if (latinText)
            {
                Console.WriteLine(string.Format("Font {0} supports latin symbols.", ttfFont.FontName));
            }
            else
            {
                Console.WriteLine(string.Format("Latin symbols are not supported by font {0}.", ttfFont.FontName));
            }
            //ExEnd: 1
        }
    }
}

```
