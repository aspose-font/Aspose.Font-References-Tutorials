---
title: Aspose.Font for .NET でフォント メトリックを取得する
linktitle: Aspose.Font for .NET でフォント メトリックを取得する
second_title: Aspose.Font .NET API
description: Aspose.Font for .NET を使用してフォント メトリックを取得する方法を学びます。コード例を使用したステップ バイ ステップ ガイド。前提条件と FAQ が含まれています。#Aspose #Font
type: docs
weight: 12
url: /ja/net/truetype-opentype/get-font-metrics/
---
## 導入
Aspose.Font for .NET は、開発者が .NET アプリケーションでフォントを操作できるようにする強力な API です。フォント メトリックの抽出、グリフの操作、フォント データへのアクセスなど、Aspose.Font はフォント関連のタスクを効率化する包括的な機能を提供します。このチュートリアルでは、Aspose.Font for .NET を使用してフォント メトリックを取得する方法について説明します。
## 前提条件
このチュートリアルに進む前に、次の前提条件が設定されていることを確認してください。
### 1. Aspose.Font for .NET のインストール
開発環境にAspose.Font for .NETがインストールされていることを確認してください。まだインストールしていない場合は、APIを以下からダウンロードできます。[Aspose.リリース](https://releases.aspose.com/font/net/)または NuGet パッケージ マネージャー経由でも実行できます。
### 2. 開発環境のセットアップ
Visual Studio またはその他の互換性のある IDE がインストールされた .NET 開発環境がセットアップされていることを確認してください。

## 名前空間のインポート
.NET アプリケーションでは、Aspose.Font for .NET を操作するために必要な名前空間をインポートする必要があります。
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
ここで、提供された例を複数のステップに分解し、それぞれを詳しく説明しましょう。
## ステップ1: フォントファイルのパスを定義する
まず、使用するフォントのファイル パスを定義します。
```csharp
string dataDir = "Your Document Directory";
string fileName = dataDir + "Montserrat-Regular.ttf"; //フルパス付きフォントファイル名
```
## ステップ2: フォントファイルを開く
次に、Aspose.Font API を使用してフォント ファイルを開きます。
```csharp
FontDefinition fd = new FontDefinition(FontType.TTF, new FontFileDefinition("ttf", new FileSystemStreamSource(fileName)));
TtfFont font = Aspose.Font.Font.Open(fd) as TtfFont;
```
## ステップ3: フォントメトリックを取得する
アセンダー、ディセンダーなどのさまざまなフォントメトリックを取得します。
```csharp
string name = font.FontName;
Console.WriteLine("Font name: " + name);
Console.WriteLine("Glyph count: " + font.NumGlyphs);
string metrics = string.Format(
    "Font metrics: ascender - {0}, descender - {1}, typo ascender = {2}, typo descender = {3}, UnitsPerEm = {4}",
    font.Metrics.Ascender, font.Metrics.Descender,
    font.Metrics.TypoAscender, font.Metrics.TypoDescender, font.Metrics.UnitsPerEM);
Console.WriteLine(metrics);
```
## ステップ4: Unicodeエンコーディングテーブルを取得する
フォントから Unicode エンコーディング テーブル (cmap) を取得します。
```csharp
Aspose.Font.TtfCMapFormats.TtfCMapFormatBaseTable cmapTable = null;
if (font.TtfTables.CMapTable != null)
{
    cmapTable = font.TtfTables.CMapTable.FindUnicodeTable();
}
```
## ステップ5: グリフ情報にアクセスする
特定のシンボル (例: 'A') のグリフ情報にアクセスします。
```csharp
char unicode = (char)65; // 「A」のUnicode
uint glIndex = cmapTable.GetGlyphIndex(unicode);
if (glIndex != 0)
{
    Glyph glyph = font.GetGlyphById(glIndex);
    if (glyph != null)
    {
        string bbox = string.Format(
            "Glyph BBox: Xmin = {0}, Xmax = {1}, Ymin = {2}, Ymax = {3}",
            glyph.GlyphBBox.XMin, glyph.GlyphBBox.XMax,
            glyph.GlyphBBox.YMin, glyph.GlyphBBox.YMax);
        Console.WriteLine(bbox);
        Console.WriteLine("Width:" + font.Metrics.GetGlyphWidth(new GlyphUInt32Id(glIndex)));
    }
}
```
## 結論
このチュートリアルでは、Aspose.Font for .NET を使用してフォント メトリックを取得する方法について説明しました。ステップ バイ ステップ ガイドに従い、前提条件を理解することで、Aspose.Font API を使用して .NET アプリケーションでフォントを効率的に操作できるようになります。
## よくある質問
### 1. Aspose.Font for .NET はどのフォント ファイル形式でも使用できますか?
はい、Aspose.Font for .NET は、TrueType (TTF)、OpenType (OTF) など、さまざまなフォント形式をサポートしています。
### 2. Aspose.Font for .NET の無料試用版はありますか?
はい、Aspose.Font for .NETの無料トライアルをこちらから入手できます。[Webサイト](https://releases.aspose.com/).
### 3. Aspose.Font for .NET のサポートにアクセスするにはどうすればいいですか?
 Aspose.Font for .NETのサポートには、[フォーラム](https://forum.aspose.com/c/font/41).
### 4. Aspose.Font for .NET の一時ライセンスを購入できますか?
はい、一時ライセンスは[Aspose ストア](https://purchase.aspose.com/temporary-license/).
### 5. Aspose.Font for .NET のドキュメントはありますか?
はい、Aspose.Font for .NETのドキュメントにアクセスできます。[ここ](https://reference.aspose.com/font/net/).