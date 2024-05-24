---
title: 提取 Aspose.Font for .NET 中的許可限制
linktitle: 提取 Aspose.Font for .NET 中的許可限制
second_title: Aspose.Font .NET API
description: 透過我們的詳細指南，了解如何使用 Aspose.Font for .NET 從 TrueType 字型中擷取授權限制。非常適合在 .NET 中使用字體的開發人員。
type: docs
weight: 11
url: /zh-hant/net/truetype-opentype/extract-license-restrictions/
---
## 介紹
嘿！如果您是在 .NET 應用程式中使用字體的開發人員，那麼了解字體檔案中嵌入的許可證限制至關重要。本綜合指南將引導您使用 Aspose.Font for .NET 從 TrueType 字型中擷取授權限制。無論您是要確保遵守字體許可，還是只是想了解您所使用的字體的權限，我們都能滿足您的要求。在本教學結束時，您將能夠輕鬆檢查任何 TrueType 字型的授權限制。準備好潛入了嗎？讓我們開始吧！
## 先決條件
在我們開始編寫程式碼之前，請確保您具備以下條件：
-  Aspose.Font for .NET：從[Aspose 發佈頁面](https://releases.aspose.com/font/net/).
- .NET 開發環境：Visual Studio 或任何其他相容的 IDE。
- C# 基礎：熟悉 C# 程式設計和 .NET 框架。
- 字型檔：TrueType字型文件，例如`Montserrat-Regular.ttf`.
## 導入命名空間
要開始使用 Aspose.Font for .NET，您需要匯入必要的命名空間。這些命名空間將為您提供字體操作所需的類別和方法。
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
現在，讓我們將整個過程分解為簡單的步驟。
## 第 1 步：載入 TrueType 字體
首先，我們需要將 TrueType 字型載入到我們的應用程式中。這涉及定義檔案路徑並創建`FontDefinition`目的。
## 步驟1.1：指定字型檔路徑
首先指定字型檔案所在的目錄以及檔案的完整路徑。
```csharp
string dataDir = "Your Document Directory";
string fileName = dataDir + "Montserrat-Regular.ttf";
```
## 步驟1.2：建立 FontDefinition 對象
接下來，創建一個`FontDefinition`管理字體資料的物件。此步驟涉及指定字型類型和文件來源。
```csharp
FontDefinition fd = new FontDefinition(FontType.TTF, new FontFileDefinition("ttf", new FileSystemStreamSource(fileName)));
```
## 步驟 2： 開啟 TrueType 字體
隨著`FontDefinition`物件準備就緒，下一步是使用 Aspose.Font for .NET 開啟字體。
## 步驟2.1：使用開啟方法
使用`Open`的方法`Font`類別來載入字體。將傳回的物件轉換為`TtfFont`.
```csharp
TtfFont font = Aspose.Font.Font.Open(fd) as TtfFont;
```
## 第 3 步：提取許可證限制
現在字體已加載，是時候提取許可證限制了。這涉及存取字體的 OS/2 表並檢索許可證標誌。
## 步驟 3.1：初始化許可證標誌
初始化一個`LicenseFlags`物件儲存許可證資訊。
```csharp
LicenseFlags licenseFlags = null;
```
## 步驟 3.2：檢查 OS/2 表
檢查字型中是否存在 OS/2 表，如果存在則取得授權標誌。
```csharp
if (font.TtfTables.Os2Table != null)
{
    licenseFlags = font.TtfTables.Os2Table.GetLicenseFlags();
}
```
## 步驟 3.3：解釋許可證標誌
解釋許可證標誌並根據檢索到的標誌輸出許可證限制。
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
## 結論
現在你就得到它了！您已成功學習如何使用 Aspose.Font for .NET 從 TrueType 字型中擷取授權限制。本指南引導您完成在 .NET 應用程式中使用字體所需的基本步驟，確保您遵守許可要求。有了這些知識，您就可以自信地管理專案中的字體，並知道您遵守法律準則。
## 常見問題解答
### 1. 什麼是 Aspose.Font for .NET？
Aspose.Font for .NET 是一個功能強大的 API，允許開發人員使用字體文件，從而在 .NET 應用程式中實現字體載入、編輯和保存。
### 2. 我可以使用 Aspose.Font for .NET 處理其他字體格式嗎？
絕對地！ Aspose.Font for .NET 支援多種字型格式，包括 TTF、OTF、Type 1 和 CFF 等。
### 3. 如何取得 Aspose.Font for .NET 的授權？
您可以從以下位置購買許可證[Aspose 購買頁面](https://purchase.aspose.com/buy)。出於評估目的，您可以獲得臨時許可證[這裡](https://purchase.aspose.com/temporary-license/).
### 4. 在哪裡可以找到詳細的文件？
詳細文件可在[Aspose.Font for .NET 文件頁面](https://reference.aspose.com/font/net/).
### 5. 如果遇到問題，如何獲得支援？
如需支持，您可以訪問[Aspose.Font 支援論壇](https://forum.aspose.com/c/font/41).