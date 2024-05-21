---
title: Add License from Stream in Aspose.Font for .NET
linktitle: Add License from Stream in Aspose.Font for .NET
second_title: Aspose.Font .NET API
description: 
type: docs
weight: 11
url: /net/licensing/add-license-from-stream/
---

## Complete Source Code
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Linq;
using System.Text;
using System.Threading.Tasks;

namespace Aspose.Font.Examples.Licensing
{
    class AddLicenseFromStream
    {
        public static void Run()
        {
            //ExStart: 1
            string dataDir = @"c:\temp\";
            // Load an existing Visio file in the stream
            FileStream LicStream = new FileStream(dataDir + "Aspose.Font.lic", FileMode.Open);

            License license = new License();
            license.SetLicense(LicStream);
            //ExEnd: 1
        }
    }
}

```
