---
title: .NET용 Aspose.Font에서 라이센스 제한 추출
linktitle: .NET용 Aspose.Font에서 라이센스 제한 추출
second_title: Aspose.Font .NET API
description: 자세한 가이드를 통해 .NET용 Aspose.Font를 사용하여 트루타입 글꼴에서 라이센스 제한을 추출하는 방법을 알아보세요. .NET에서 글꼴을 사용하여 작업하는 개발자에게 적합합니다.
type: docs
weight: 11
url: /ko/net/truetype-opentype/extract-license-restrictions/
---
## 소개
안녕하세요! .NET 애플리케이션에서 글꼴 작업을 하는 개발자라면 글꼴 파일에 포함된 라이선스 제한 사항을 이해하는 것이 중요합니다. 이 포괄적인 가이드는 .NET용 Aspose.Font를 사용하여 트루타입 글꼴에서 라이센스 제한을 추출하는 과정을 안내합니다. 글꼴 라이센스 준수 여부를 확인하고 싶거나 사용 중인 글꼴의 권한이 궁금한 경우 모두 저희가 도와드리겠습니다. 이 튜토리얼이 끝나면 트루타입 글꼴의 라이센스 제한 사항을 쉽게 확인할 수 있습니다. 다이빙할 준비가 되셨나요? 시작하자!
## 전제조건
코드를 시작하기 전에 다음 사항이 있는지 확인하세요.
-  .NET용 Aspose.Font: 다음에서 다운로드하세요.[Aspose 릴리스 페이지](https://releases.aspose.com/font/net/).
- .NET 개발 환경: Visual Studio 또는 기타 호환 가능한 IDE.
- C#에 대한 기본 지식: C# 프로그래밍 및 .NET 프레임워크에 대한 지식.
- 글꼴 파일: 다음과 같은 트루타입 글꼴 파일입니다.`Montserrat-Regular.ttf`.
## 네임스페이스 가져오기
.NET용 Aspose.Font를 사용하려면 필요한 네임스페이스를 가져와야 합니다. 이러한 네임스페이스는 글꼴 조작에 필요한 클래스와 메서드를 제공합니다.
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
이제 전체 프로세스를 간단한 단계로 나누어 보겠습니다.
## 1단계: 트루타입 글꼴 로드
 먼저 TrueType 글꼴을 응용 프로그램에 로드해야 합니다. 여기에는 파일 경로를 정의하고`FontDefinition` 물체.
## 1.1단계: 글꼴 파일 경로 지정
글꼴 파일이 있는 디렉터리와 파일의 전체 경로를 지정하는 것부터 시작하세요.
```csharp
string dataDir = "Your Document Directory";
string fileName = dataDir + "Montserrat-Regular.ttf";
```
## 1.2단계: FontDefinition 객체 생성
 다음으로`FontDefinition` 글꼴 데이터를 관리하는 개체입니다. 이 단계에는 글꼴 유형과 파일 소스를 지정하는 작업이 포함됩니다.
```csharp
FontDefinition fd = new FontDefinition(FontType.TTF, new FontFileDefinition("ttf", new FileSystemStreamSource(fileName)));
```
## 2단계: 트루타입 글꼴 열기
 와 더불어`FontDefinition` 개체가 준비되면 다음 단계는 .NET용 Aspose.Font를 사용하여 글꼴을 여는 것입니다.
## 2.1단계: Open 메서드 사용
 사용`Open` 의 방법`Font` 글꼴을 로드하는 클래스입니다. 반환된 객체를`TtfFont`.
```csharp
TtfFont font = Aspose.Font.Font.Open(fd) as TtfFont;
```
## 3단계: 라이선스 제한 추출
이제 글꼴이 로드되었으므로 라이선스 제한을 추출할 차례입니다. 여기에는 글꼴의 OS/2 테이블에 액세스하고 라이센스 플래그를 검색하는 작업이 포함됩니다.
## 3.1단계: 라이센스 플래그 초기화
 초기화`LicenseFlags` 라이센스 정보를 저장하는 객체입니다.
```csharp
LicenseFlags licenseFlags = null;
```
## 3.2단계: OS/2 테이블 확인
OS/2 테이블이 글꼴에 있는지 확인하고 있는 경우 라이센스 플래그를 가져옵니다.
```csharp
if (font.TtfTables.Os2Table != null)
{
    licenseFlags = font.TtfTables.Os2Table.GetLicenseFlags();
}
```
## 3.3단계: 라이센스 플래그 해석
라이센스 플래그를 해석하고 검색된 플래그를 기반으로 라이센스 제한 사항을 출력합니다.
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
## 결론
그리고 거기에 있습니다! .NET용 Aspose.Font를 사용하여 트루타입 글꼴에서 라이센스 제한을 추출하는 방법을 성공적으로 배웠습니다. 이 가이드에서는 .NET 애플리케이션에서 글꼴을 사용하여 라이선스 요구 사항을 준수하는 데 필요한 필수 단계를 안내했습니다. 이러한 지식을 바탕으로 법적 지침을 준수하고 있다는 사실을 알고 프로젝트에서 글꼴을 자신있게 관리할 수 있습니다.
## FAQ
### 1. .NET용 Aspose.Font란 무엇입니까?
Aspose.Font for .NET은 개발자가 글꼴 파일 작업을 할 수 있게 해주는 강력한 API로, .NET 애플리케이션 내에서 글꼴 로딩, 편집, 저장이 가능합니다.
### 2. .NET용 Aspose.Font를 사용하여 다른 글꼴 형식으로 작업할 수 있나요?
전적으로! .NET용 Aspose.Font는 TTF, OTF, Type 1, CFF 등 다양한 글꼴 형식을 지원합니다.
### 3. .NET용 Aspose.Font 라이센스는 어떻게 얻나요?
 다음에서 라이센스를 구입할 수 있습니다.[Aspose 구매 페이지](https://purchase.aspose.com/buy) . 평가 목적으로 임시 라이센스를 얻을 수 있습니다.[여기](https://purchase.aspose.com/temporary-license/).
### 4. 자세한 문서는 어디서 찾을 수 있나요?
 자세한 문서는 다음에서 확인할 수 있습니다.[.NET 문서 페이지용 Aspose.Font](https://reference.aspose.com/font/net/).
### 5. 문제가 발생하면 어떻게 지원을 받을 수 있나요?
 지원을 받으려면 다음을 방문하세요.[Aspose.Font 지원 포럼](https://forum.aspose.com/c/font/41).