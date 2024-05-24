---
title: Extraia restrições de licença em Aspose.Font para .NET
linktitle: Extraia restrições de licença em Aspose.Font para .NET
second_title: API Aspose.Font .NET
description: Aprenda como extrair restrições de licença de fontes TrueType usando Aspose.Font for .NET com nosso guia detalhado. Perfeito para desenvolvedores que trabalham com fontes em .NET.
type: docs
weight: 11
url: /pt/net/truetype-opentype/extract-license-restrictions/
---
## Introdução
Ei! Se você é um desenvolvedor que trabalha com fontes em aplicativos .NET, é crucial compreender as restrições de licença incorporadas em arquivos de fontes. Este guia abrangente irá orientá-lo na extração de restrições de licença de fontes TrueType usando Aspose.Font for .NET. Esteja você garantindo a conformidade com o licenciamento de fontes ou apenas curioso sobre as permissões das fontes que está usando, nós temos o que você precisa. Ao final deste tutorial, você poderá verificar facilmente qualquer fonte TrueType quanto às restrições de licença. Pronto para mergulhar? Vamos começar!
## Pré-requisitos
Antes de entrarmos no código, certifique-se de ter o seguinte:
-  Aspose.Font para .NET: Faça o download em[Página de lançamentos do Aspose](https://releases.aspose.com/font/net/).
- Ambiente de desenvolvimento .NET: Visual Studio ou qualquer outro IDE compatível.
- Conhecimento básico de C#: Familiaridade com programação C# e o framework .NET.
- Arquivo de fonte: um arquivo de fonte TrueType, como`Montserrat-Regular.ttf`.
## Importar namespaces
Para começar a usar o Aspose.Font for .NET, você precisará importar os namespaces necessários. Esses namespaces fornecerão as classes e métodos necessários para a manipulação de fontes.
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
Agora, vamos dividir todo o processo em etapas simples.
## Etapa 1: carregar a fonte TrueType
 Primeiro, precisamos carregar a fonte TrueType em nosso aplicativo. Isso envolve definir o caminho do arquivo e criar um`FontDefinition` objeto.
## Etapa 1.1: Especifique o caminho do arquivo de fonte
Comece especificando o diretório onde o arquivo da fonte está localizado e o caminho completo para o arquivo.
```csharp
string dataDir = "Your Document Directory";
string fileName = dataDir + "Montserrat-Regular.ttf";
```
## Etapa 1.2: Criar um objeto FontDefinition
 A seguir, crie um`FontDefinition` objeto para gerenciar os dados da fonte. Esta etapa envolve a especificação do tipo de fonte e da origem do arquivo.
```csharp
FontDefinition fd = new FontDefinition(FontType.TTF, new FontFileDefinition("ttf", new FileSystemStreamSource(fileName)));
```
## Etapa 2: abra a fonte TrueType
 Com o`FontDefinition` objeto pronto, o próximo passo é abrir a fonte usando Aspose.Font for .NET.
## Etapa 2.1: Use o método aberto
 Use o`Open` método do`Font` class para carregar a fonte. Converta o objeto retornado em um`TtfFont`.
```csharp
TtfFont font = Aspose.Font.Font.Open(fd) as TtfFont;
```
## Etapa 3: extrair restrições de licença
Agora que a fonte foi carregada, é hora de extrair as restrições da licença. Isso envolve acessar a tabela OS/2 da fonte e recuperar os sinalizadores de licença.
## Etapa 3.1: inicializar sinalizadores de licença
 Inicialize um`LicenseFlags` objeto para armazenar as informações de licença.
```csharp
LicenseFlags licenseFlags = null;
```
## Etapa 3.2: Verifique a tabela OS/2
Verifique se a tabela OS/2 existe na fonte e obtenha os sinalizadores de licença, caso exista.
```csharp
if (font.TtfTables.Os2Table != null)
{
    licenseFlags = font.TtfTables.Os2Table.GetLicenseFlags();
}
```
## Etapa 3.3: Interpretar sinalizadores de licença
Interprete os sinalizadores de licença e produza as restrições de licença com base nos sinalizadores recuperados.
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
## Conclusão
E aí está! Você aprendeu com sucesso como extrair restrições de licença de fontes TrueType usando Aspose.Font for .NET. Este guia orientou você pelas etapas essenciais necessárias para trabalhar com fontes em seus aplicativos .NET, garantindo a conformidade com os requisitos de licenciamento. Com esse conhecimento, você pode gerenciar fontes em seus projetos com segurança, sabendo que está cumprindo as diretrizes legais.
## Perguntas frequentes
### 1. O que é Aspose.Font para .NET?
Aspose.Font for .NET é uma API poderosa que permite aos desenvolvedores trabalhar com arquivos de fontes, permitindo carregar, editar e salvar fontes em aplicativos .NET.
### 2. Posso trabalhar com outros formatos de fonte usando Aspose.Font for .NET?
Absolutamente! Aspose.Font for .NET oferece suporte a vários formatos de fonte, incluindo TTF, OTF, Type 1 e CFF, entre outros.
### 3. Como obtenho uma licença do Aspose.Font for .NET?
 Você pode comprar uma licença no[Página de compra do Aspose](https://purchase.aspose.com/buy) . Para fins de avaliação, você pode obter uma licença temporária[aqui](https://purchase.aspose.com/temporary-license/).
### 4. Onde posso encontrar documentação detalhada?
 A documentação detalhada está disponível no site[Página de documentação do Aspose.Font para .NET](https://reference.aspose.com/font/net/).
### 5. Como posso obter suporte se tiver problemas?
 Para suporte, você pode visitar o[Fórum de suporte Aspose.Font](https://forum.aspose.com/c/font/41).