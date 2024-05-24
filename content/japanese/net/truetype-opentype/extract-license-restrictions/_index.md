---
title: Aspose.Font for .NET のライセンス制限の抽出
linktitle: Aspose.Font for .NET のライセンス制限の抽出
second_title: Aspose.Font .NET API
description: 詳細なガイドで、Aspose.Font for .NET を使用して TrueType フォントからライセンス制限を抽出する方法を学びます。.NET でフォントを扱う開発者に最適です。
type: docs
weight: 11
url: /ja/net/truetype-opentype/extract-license-restrictions/
---
## 導入
こんにちは! .NET アプリケーションでフォントを扱う開発者にとって、フォント ファイルに埋め込まれたライセンス制限を理解することは非常に重要です。この包括的なガイドでは、Aspose.Font for .NET を使用して TrueType フォントからライセンス制限を抽出する手順を説明します。フォント ライセンスへの準拠を確実にしたい場合でも、使用しているフォントの権限について知りたいだけの場合でも、このガイドが役立ちます。このチュートリアルの最後には、TrueType フォントのライセンス制限を簡単に確認できるようになります。準備はできましたか? さあ、始めましょう!
## 前提条件
コードに進む前に、次のものを用意してください。
-  Aspose.Font for .NET: ダウンロードはこちらから[Aspose リリース ページ](https://releases.aspose.com/font/net/).
- .NET 開発環境: Visual Studio またはその他の互換性のある IDE。
- C# の基礎知識: C# プログラミングと .NET フレームワークに精通していること。
- フォントファイル: TrueTypeフォントファイル、例:`Montserrat-Regular.ttf`.
## 名前空間のインポート
Aspose.Font for .NET の使用を開始するには、必要な名前空間をインポートする必要があります。これらの名前空間は、フォント操作に必要なクラスとメソッドを提供します。
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
それでは、プロセス全体を簡単なステップに分解してみましょう。
## ステップ1: TrueTypeフォントを読み込む
まず、TrueTypeフォントをアプリケーションに読み込む必要があります。これには、ファイルパスの定義と`FontDefinition`物体。
## ステップ1.1: フォントファイルのパスを指定する
まず、フォント ファイルが保存されているディレクトリとファイルへのフル パスを指定します。
```csharp
string dataDir = "Your Document Directory";
string fileName = dataDir + "Montserrat-Regular.ttf";
```
## ステップ 1.2: FontDefinition オブジェクトを作成する
次に、`FontDefinition`フォント データを管理するオブジェクト。この手順では、フォントの種類とファイル ソースを指定します。
```csharp
FontDefinition fd = new FontDefinition(FontType.TTF, new FontFileDefinition("ttf", new FileSystemStreamSource(fileName)));
```
## ステップ2: TrueTypeフォントを開く
とともに`FontDefinition`オブジェクトの準備ができたら、次のステップは Aspose.Font for .NET を使用してフォントを開くことです。
## ステップ 2.1: Open メソッドを使用する
使用`Open`方法の`Font`クラスを使用してフォントをロードします。返されたオブジェクトを`TtfFont`.
```csharp
TtfFont font = Aspose.Font.Font.Open(fd) as TtfFont;
```
## ステップ3: ライセンス制限の抽出
フォントが読み込まれたので、ライセンス制限を抽出します。これには、フォントの OS/2 テーブルにアクセスし、ライセンス フラグを取得することが含まれます。
## ステップ 3.1: ライセンス フラグを初期化する
初期化する`LicenseFlags`ライセンス情報を保存するオブジェクト。
```csharp
LicenseFlags licenseFlags = null;
```
## ステップ 3.2: OS/2 テーブルを確認する
フォント内に OS/2 テーブルが存在するかどうかを確認し、存在する場合はライセンス フラグを取得します。
```csharp
if (font.TtfTables.Os2Table != null)
{
    licenseFlags = font.TtfTables.Os2Table.GetLicenseFlags();
}
```
## ステップ 3.3: ライセンス フラグの解釈
ライセンス フラグを解釈し、取得したフラグに基づいてライセンス制限を出力します。
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
これで完了です。Aspose.Font for .NET を使用して TrueType フォントからライセンス制限を抽出する方法を学習しました。このガイドでは、.NET アプリケーションでフォントを操作するために必要な重要な手順を説明し、ライセンス要件に準拠していることを確認できました。この知識があれば、法的ガイドラインに準拠していることを知りながら、プロジェクトで自信を持ってフォントを管理できます。
## よくある質問
### 1. Aspose.Font for .NET とは何ですか?
Aspose.Font for .NET は、開発者がフォント ファイルを操作して、.NET アプリケーション内でフォントの読み込み、編集、保存を可能にする強力な API です。
### 2. Aspose.Font for .NET を使用して他のフォント形式を扱うことはできますか?
もちろんです! Aspose.Font for .NET は、TTF、OTF、Type 1、CFF など、複数のフォント形式をサポートしています。
### 3. Aspose.Font for .NET のライセンスを取得するにはどうすればよいですか?
ライセンスは以下から購入できます。[Aspose 購入ページ](https://purchase.aspose.com/buy)評価目的で一時ライセンスを取得できます[ここ](https://purchase.aspose.com/temporary-license/).
### 4. 詳細なドキュメントはどこで入手できますか?
詳細なドキュメントは、[Aspose.Font for .NET ドキュメント ページ](https://reference.aspose.com/font/net/).
### 5. 問題が発生した場合、どうすればサポートを受けることができますか?
サポートについては、[Aspose.Font サポート フォーラム](https://forum.aspose.com/c/font/41).