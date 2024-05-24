---
title: .NET Type 1용 Aspose.Font에서 글꼴 메트릭 가져오기
linktitle: .NET Type 1용 Aspose.Font에서 글꼴 메트릭 가져오기
second_title: Aspose.Font .NET API
description: 이 포괄적인 단계별 튜토리얼에서 .NET용 Aspose.Font를 사용하여 글꼴 메트릭을 얻는 방법을 알아보세요. 모든 수준의 개발자에게 적합합니다!
type: docs
weight: 11
url: /ko/net/aspose-font-net-type1-font/get-font-metrics-aspose-font-net-type1/
---
## 소개
.NET용 Aspose.Font를 사용하여 글꼴 메트릭을 얻는 방법에 대한 최고의 가이드에 오신 것을 환영합니다! 숙련된 개발자이든 아니면 그냥 글꼴 세계에 발을 담그고 있든 이 튜토리얼에서는 프로세스를 단계별로 안내합니다. 이 기사가 끝나면 자세한 글꼴 메트릭을 추출하고 .NET 애플리케이션 내에서 이를 조작하는 방법을 이해할 수 있습니다. 그럼 이제 본격적으로 이 흥미진진한 여행을 시작해보세요!
## 전제조건
핵심적인 내용을 살펴보기 전에 준비해야 할 몇 가지 사항이 있습니다.
- Visual Studio: 컴퓨터에 Visual Studio가 설치되어 있는지 확인하세요.
-  .NET용 Aspose.Font: .NET용 Aspose.Font 라이브러리를 다운로드하여 설치하세요. 에서 받으실 수 있습니다.[다운로드 링크](https://releases.aspose.com/font/net/).
- C#에 대한 기본 지식: 예제를 따라가려면 C# 프로그래밍에 대한 지식이 필요합니다.
- 글꼴 파일: 트루타입 글꼴 파일(.ttf)을 준비하세요. 이 튜토리얼에서는 모든 .ttf 파일을 사용할 수 있습니다.
이제 모든 준비가 완료되었으므로 필요한 네임스페이스를 가져오는 것부터 시작해 보겠습니다.
## 네임스페이스 가져오기
.NET용 Aspose.Font 작업을 시작하려면 프로젝트에 적절한 네임스페이스를 포함해야 합니다. 방법은 다음과 같습니다.
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
이러한 네임스페이스가 있으면 .NET 애플리케이션에서 글꼴 작업을 시작할 수 있습니다.
## 1단계: 글꼴 파일 로드
먼저, 애플리케이션에 글꼴 파일을 로드해야 합니다. 수행 방법은 다음과 같습니다.
### 글꼴 파일 로드
1. 글꼴 파일의 경로를 정의합니다. 
2.  만들기`FontDefinition` 물체.
3.  사용`Font.Open` 글꼴을 로드하는 방법입니다.
```csharp
string dataDir = "Your Document Directory";
string fileName = dataDir + "Montserrat-Regular.ttf";
FontDefinition fd = new FontDefinition(FontType.TTF, new FontFileDefinition("ttf", new FileSystemStreamSource(fileName)));
TtfFont font = Aspose.Font.Font.Open(fd) as TtfFont;
```
 여기서는`FontDefinition` 클래스를 사용하여 글꼴 파일의 유형과 위치를 정의합니다. 그만큼`Font.Open` 메소드는 글꼴을`TtfFont` 물체.
## 2단계: 기본 글꼴 정보 검색
글꼴이 로드되면 해당 글꼴에 대한 몇 가지 기본 정보를 검색할 수 있습니다.
### 글꼴 이름 및 문자 개수 가져오기
```csharp
string name = font.FontName;
Console.WriteLine("Font name: " + name);
Console.WriteLine("Glyph count: " + font.NumGlyphs);
```
이 코드 조각은 글꼴 이름과 포함된 문자 수를 인쇄합니다.
## 3단계: 글꼴 메트릭 추출
글꼴 메트릭은 글꼴 특성에 대한 자세한 정보를 제공합니다.
### 글꼴 메트릭 표시
```csharp
string metrics = string.Format(
    "Font metrics: ascender - {0}, descender - {1}, typo ascender = {2}, typo descender = {3}, UnitsPerEm = {4}",
    font.Metrics.Ascender, font.Metrics.Descender,
    font.Metrics.TypoAscender, font.Metrics.TypoDescender, font.Metrics.UnitsPerEM);
Console.WriteLine(metrics);
```
이 조각은 오름차순, 내림차순 및 EM당 단위와 같은 글꼴의 다양한 메트릭 형식을 지정하고 인쇄합니다.
## 4단계: CMap 유니코드 테이블에 액세스
CMap 테이블은 문자 코드를 문자 모양 색인에 매핑하는 데 도움이 됩니다.
### CMap 테이블 검색 및 확인
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
이 코드는 CMap 테이블을 검색하고 PlatformID 및 PlatformSpecificID를 인쇄합니다.
## 5단계: 문양 정보 가져오기
마지막으로 문자 'A'에 대한 문자 모양과 같은 특정 문자 모양에 대한 정보를 검색해 보겠습니다.
### 문양 정보 검색
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
이 스니펫은 'A'에 대한 글리프 인덱스를 가져오고, 이 인덱스를 사용하여 글리프를 검색하고, 경계 상자 및 너비를 포함한 해당 메트릭을 인쇄합니다.
## 결론
축하해요! .NET용 Aspose.Font를 사용하여 글꼴 메트릭을 얻는 방법을 성공적으로 배웠습니다. 다음 단계를 수행하면 응용 프로그램에서 글꼴 정보를 쉽게 추출하고 조작할 수 있습니다. 이 튜토리얼은 고급 글꼴 작업을 위한 견고한 기반을 제공합니다. 즐거운 코딩하세요!
## FAQ
### Q1: Aspose.Font for .NET을 다른 글꼴 형식과 함께 사용할 수 있습니까?
예, .NET용 Aspose.Font는 TrueType, OpenType, Type1 등을 포함한 다양한 글꼴 형식을 지원합니다.
### Q2: .NET용 Aspose.Font 무료 평가판은 어디서 구할 수 있나요?
 다음에서 무료 평가판을 다운로드할 수 있습니다.[Aspose 릴리스 페이지](https://releases.aspose.com/).
### Q3: .NET용 Aspose.Font 라이선스를 어떻게 구매하나요?
 다음에서 라이센스를 구입할 수 있습니다.[구매 페이지 제안](https://purchase.aspose.com/buy).
### Q4: .NET용 Aspose.Font에 대한 지원이 제공됩니까?
 네, 지원을 받으실 수 있습니다.[Aspose 지원 포럼](https://forum.aspose.com/c/font/41).
### Q5: 상용 프로젝트에서 Aspose.Font for .NET을 사용할 수 있나요?
예, 상업용 프로젝트에서 Aspose.Font for .NET을 사용할 수 있지만 유효한 라이선스가 필요합니다.