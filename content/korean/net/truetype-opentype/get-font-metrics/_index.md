---
title: .NET용 Aspose.Font에서 글꼴 메트릭 가져오기
linktitle: .NET용 Aspose.Font에서 글꼴 메트릭 가져오기
second_title: Aspose.Font .NET API
description: .NET용 Aspose.Font를 사용하여 글꼴 메트릭을 얻는 방법을 알아보세요. 코드 예제가 포함된 단계별 가이드입니다. 전제 조건 및 FAQ가 포함되어 있습니다. #Aspose #글꼴
type: docs
weight: 12
url: /ko/net/truetype-opentype/get-font-metrics/
---
## 소개
Aspose.Font for .NET은 개발자가 .NET 애플리케이션에서 글꼴 작업을 할 수 있게 해주는 강력한 API입니다. 글꼴 메트릭을 추출하거나, 글리프를 조작하거나, 글꼴 데이터에 액세스해야 하는 경우 Aspose.Font는 글꼴 관련 작업을 간소화하는 포괄적인 기능을 제공합니다. 이 튜토리얼에서는 .NET용 Aspose.Font를 사용하여 글꼴 메트릭을 얻는 방법을 살펴보겠습니다.
## 전제조건
이 튜토리얼을 시작하기 전에 다음 전제 조건이 설정되어 있는지 확인하세요.
### 1. .NET 설치를 위한 Aspose.Font
 개발 환경에 .NET용 Aspose.Font가 설치되어 있는지 확인하세요. 아직 다운로드하지 않았다면 다음에서 API를 다운로드할 수 있습니다.[Aspose.릴리스](https://releases.aspose.com/font/net/) 또는 NuGet 패키지 관리자를 통해.
### 2. 개발 환경 설정
Visual Studio 또는 기타 호환 가능한 IDE가 설치되어 있는 .NET 개발 환경이 설정되어 있는지 확인하세요.

## 네임스페이스 가져오기
.NET 애플리케이션에서 .NET용 Aspose.Font를 사용하려면 필요한 네임스페이스를 가져와야 합니다.
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
이제 제공된 예제를 여러 단계로 나누어 각 단계를 자세히 설명하겠습니다.
## 1단계: 글꼴 파일 경로 정의
먼저 작업하려는 글꼴의 파일 경로를 정의합니다.
```csharp
string dataDir = "Your Document Directory";
string fileName = dataDir + "Montserrat-Regular.ttf"; //전체 경로가 포함된 글꼴 파일 이름
```
## 2단계: 글꼴 파일 열기
다음으로 Aspose.Font API를 사용하여 글꼴 파일을 엽니다.
```csharp
FontDefinition fd = new FontDefinition(FontType.TTF, new FontFileDefinition("ttf", new FileSystemStreamSource(fileName)));
TtfFont font = Aspose.Font.Font.Open(fd) as TtfFont;
```
## 3단계: 글꼴 메트릭 검색
어센더, 디센더 등과 같은 다양한 글꼴 측정항목을 검색합니다.
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
## 4단계: 유니코드 인코딩 테이블 가져오기
글꼴에서 유니코드 인코딩 테이블(cmap)을 검색합니다.
```csharp
Aspose.Font.TtfCMapFormats.TtfCMapFormatBaseTable cmapTable = null;
if (font.TtfTables.CMapTable != null)
{
    cmapTable = font.TtfTables.CMapTable.FindUnicodeTable();
}
```
## 5단계: 글리프 정보에 액세스
특정 기호(예: 'A')에 대한 문자 정보에 액세스합니다.
```csharp
char unicode = (char)65; // 'A'에 대한 유니코드
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
## 결론
이 튜토리얼에서는 .NET용 Aspose.Font를 사용하여 글꼴 메트릭을 얻는 방법을 다루었습니다. 단계별 가이드를 따르고 전제 조건을 이해하면 Aspose.Font API를 사용하여 .NET 애플리케이션에서 글꼴 작업을 효율적으로 수행할 수 있습니다.
## FAQ
### 1. 모든 글꼴 파일 형식으로 .NET용 Aspose.Font를 사용할 수 있나요?
예, .NET용 Aspose.Font는 TrueType(TTF), OpenType(OTF) 등과 같은 다양한 글꼴 형식을 지원합니다.
### 2. Aspose.Font for .NET에 대한 무료 평가판이 있습니까?
 예, 다음 사이트에서 Aspose.Font for .NET 무료 평가판을 받을 수 있습니다.[웹사이트](https://releases.aspose.com/).
### 3. .NET용 Aspose.Font 지원에 어떻게 접근할 수 있나요?
 다음을 통해 .NET용 Aspose.Font 지원에 액세스할 수 있습니다.[법정](https://forum.aspose.com/c/font/41).
### 4. .NET용 Aspose.Font의 임시 라이선스를 구입할 수 있나요?
 예, 다음 사이트에서 임시 라이센스를 구입할 수 있습니다.[Aspose 매장](https://purchase.aspose.com/temporary-license/).
### 5. .NET용 Aspose.Font에 대한 문서가 있습니까?
 예, .NET용 Aspose.Font 문서에 액세스할 수 있습니다.[여기](https://reference.aspose.com/font/net/).