---
title: Add License from File in Aspose.Font for .NET
linktitle: Add License from File in Aspose.Font for .NET
second_title: Aspose.Font .NET API
description: 
type: docs
weight: 10
url: /net/licensing/add-license-from-file/
---

## Complete Source Code
```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;

namespace Aspose.Font.Examples.Licensing
{
    class AddLicenseFromFile
    {
        public static void Run()
        {
            //ExStart: 1
            License lic = new License();

            lic.SetLicense("path-to-licence-file.lic");
            //ExEnd: 1
        }
    }
}

```
