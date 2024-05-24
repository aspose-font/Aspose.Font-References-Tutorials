---
title: Aspose.Font for .NET Type 1 でフォント メトリックを取得する
linktitle: Aspose.Font for .NET Type 1 でフォント メトリックを取得する
second_title: Aspose.Font .NET API
description: この包括的なステップバイステップのチュートリアルでは、Aspose.Font for .NET を使用してフォント メトリックを取得する方法を学びます。あらゆるレベルの開発者に最適です。
type: docs
weight: 11
url: /ja/net/aspose-font-net-type1-font/get-font-metrics-aspose-font-net-type1/
---
## 導入
Aspose.Font for .NET を使用してフォント メトリックを取得する究極のガイドへようこそ。熟練した開発者でも、フォントの世界に足を踏み入れたばかりの人でも、このチュートリアルではプロセスをステップごとに説明します。この記事を読み終える頃には、詳細なフォント メトリックを抽出し、.NET アプリケーション内でそれらを操作する方法を理解できるようになります。さあ、このエキサイティングな旅に飛び込んでみましょう。
## 前提条件
細かい点に入る前に、準備しておく必要のあるものがいくつかあります。
- Visual Studio: マシンに Visual Studio がインストールされていることを確認します。
-  Aspose.Font for .NET: Aspose.Font for .NETライブラリをダウンロードしてインストールします。[ダウンロードリンク](https://releases.aspose.com/font/net/).
- C# の基礎知識: 例に従うには、C# プログラミングの知識が必要です。
- フォント ファイル: TrueType フォント ファイル (.ttf) を用意します。このチュートリアルでは任意の .ttf ファイルを使用できます。
すべての準備が整ったので、必要な名前空間をインポートすることから始めましょう。
## 名前空間のインポート
Aspose.Font for .NET の使用を開始するには、プロジェクトに適切な名前空間を含める必要があります。手順は次のとおりです。
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
これらの名前空間を設定すると、.NET アプリケーションでフォントの使用を開始できるようになります。
## ステップ1: フォントファイルを読み込む
まず、フォント ファイルをアプリケーションに読み込む必要があります。手順は次のとおりです。
### フォントファイルを読み込む
1. フォント ファイルへのパスを定義します。 
2. 作成する`FontDefinition`物体。
3. 使用`Font.Open`フォントをロードするメソッド。
```csharp
string dataDir = "Your Document Directory";
string fileName = dataDir + "Montserrat-Regular.ttf";
FontDefinition fd = new FontDefinition(FontType.TTF, new FontFileDefinition("ttf", new FileSystemStreamSource(fileName)));
TtfFont font = Aspose.Font.Font.Open(fd) as TtfFont;
```
ここでは、`FontDefinition`クラスを使用してフォントファイルのタイプと場所を定義します。`Font.Open`メソッドはフォントを`TtfFont`物体。
## ステップ2: 基本的なフォント情報を取得する
フォントが読み込まれると、フォントに関する基本的な情報を取得できます。
### フォント名とグリフ数を取得する
```csharp
string name = font.FontName;
Console.WriteLine("Font name: " + name);
Console.WriteLine("Glyph count: " + font.NumGlyphs);
```
このコード スニペットは、フォント名とそれに含まれるグリフの数を出力します。
## ステップ3: フォントメトリックの抽出
フォント メトリックは、フォントの特性に関する詳細な情報を提供します。
### 表示フォントメトリック
```csharp
string metrics = string.Format(
    "Font metrics: ascender - {0}, descender - {1}, typo ascender = {2}, typo descender = {3}, UnitsPerEm = {4}",
    font.Metrics.Ascender, font.Metrics.Descender,
    font.Metrics.TypoAscender, font.Metrics.TypoDescender, font.Metrics.UnitsPerEM);
Console.WriteLine(metrics);
```
このスニペットは、アセンダー、ディセンダー、EM あたりの単位など、フォントのさまざまなメトリックをフォーマットして出力します。
## ステップ4: CMap Unicodeテーブルにアクセスする
CMap テーブルは、文字コードをグリフ インデックスにマッピングするのに役立ちます。
### CMap テーブルの取得と確認
```csharp
TtfCMapFormatBaseTable cmapTable = null;
if (font.TtfTables.CMapTable != null)
{
    cmapTable = font.TtfTables.CMapTable.FindUnicodeTable();
}
if (cmapTable != null && font.TtfTables.GlyfTable != null)
{
    Console.WriteLine("Font cmap unicode table: PlatformID = " + cmapTable.PlatformId + ", PlatformSpecificID = " + cmapTable.PlatformSpecificId);
}
```
このコードは CMap テーブルを取得し、PlatformID と PlatformSpecificID を出力します。
## ステップ5: グリフ情報を取得する
最後に、文字「A」のグリフなど、特定のグリフに関する情報を取得してみましょう。
### グリフ情報を取得する
```csharp
char unicode = (char)65;
uint glIndex = cmapTable.GetGlyphIndex(unicode);
if (glIndex != 0)
{
    Glyph glyph = font.GetGlyphById(glIndex);
    if (glyph != null)
    {
        Console.WriteLine("Glyph metrics for 'A' symbol:");
        string bbox = string.Format(
            "Glyph BBox: Xmin = {0}, Xmax = {1}" + ", Ymin = {2}, Ymax = {3}",
            glyph.GlyphBBox.XMin, glyph.GlyphBBox.XMax,
            glyph.GlyphBBox.YMin, glyph.GlyphBBox.YMax);
        Console.WriteLine(bbox);
        Console.WriteLine("Width:" + font.Metrics.GetGlyphWidth(new GlyphUInt32Id(glIndex)));
    }
}
```
このスニペットは、「A」のグリフ インデックスを取得し、このインデックスを使用してグリフを取得し、境界ボックスや幅などのメトリックを出力します。
## 結論
おめでとうございます! Aspose.Font for .NET を使用してフォント メトリックを取得する方法を学習しました。これらの手順に従うことで、アプリケーションでフォント情報を簡単に抽出して操作できます。このチュートリアルは、より高度なフォント操作のための強固な基礎を提供します。コーディングを楽しんでください!
## よくある質問
### Q1: Aspose.Font for .NET を他のフォント形式で使用できますか?
はい、Aspose.Font for .NET は、TrueType、OpenType、Type1 など、さまざまなフォント形式をサポートしています。
### Q2: Aspose.Font for .NET の無料試用版はどこで入手できますか?
無料トライアルは以下からダウンロードできます。[Aspose リリース ページ](https://releases.aspose.com/).
### Q3: Aspose.Font for .NET のライセンスを購入するにはどうすればよいですか?
ライセンスは以下から購入できます。[Aspose 購入ページ](https://purchase.aspose.com/buy).
### Q4: Aspose.Font for .NET のサポートはありますか?
はい、サポートを受けることができます[Aspose サポート フォーラム](https://forum.aspose.com/c/font/41).
### Q5: Aspose.Font for .NET を商用プロジェクトで使用できますか?
はい、Aspose.Font for .NET を商用プロジェクトで使用できますが、有効なライセンスが必要です。