---
title: Obtenha métricas de fonte em Aspose.Font para .NET
linktitle: Obtenha métricas de fonte em Aspose.Font para .NET
second_title: API Aspose.Font .NET
description: Aprenda como obter métricas de fonte usando Aspose.Font for .NET. Guia passo a passo com exemplos de código. Pré-requisitos e perguntas frequentes incluídas. #Aspose #Font
type: docs
weight: 12
url: /pt/net/truetype-opentype/get-font-metrics/
---
## Introdução
Aspose.Font for .NET é uma API poderosa que permite aos desenvolvedores trabalhar com fontes em seus aplicativos .NET. Se você precisa extrair métricas de fontes, manipular glifos ou acessar dados de fontes, Aspose.Font fornece funcionalidade abrangente para agilizar tarefas relacionadas a fontes. Neste tutorial, exploraremos como obter métricas de fonte usando Aspose.Font for .NET.
## Pré-requisitos
Antes de mergulhar neste tutorial, certifique-se de ter os seguintes pré-requisitos configurados:
### 1. Aspose.Font para instalação .NET
 Certifique-se de ter o Aspose.Font for .NET instalado em seu ambiente de desenvolvimento. Se ainda não o fez, você pode baixar a API no site[Aspose.Lançamentos](https://releases.aspose.com/font/net/) ou por meio do gerenciador de pacotes NuGet.
### 2. Configuração do ambiente de desenvolvimento
Certifique-se de ter um ambiente de desenvolvimento .NET configurado com o Visual Studio ou qualquer outro IDE compatível instalado.

## Importar namespaces
Em seu aplicativo .NET, você precisa importar os namespaces necessários para trabalhar com Aspose.Font for .NET.
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
Agora, vamos dividir o exemplo fornecido em várias etapas e explicar cada uma delas detalhadamente.
## Etapa 1: definir o caminho do arquivo de fonte
Primeiro, defina o caminho do arquivo da fonte com a qual deseja trabalhar.
```csharp
string dataDir = "Your Document Directory";
string fileName = dataDir + "Montserrat-Regular.ttf"; //Nome do arquivo da fonte com caminho completo
```
## Etapa 2: abra o arquivo de fonte
Em seguida, abra o arquivo de fonte usando a API Aspose.Font.
```csharp
FontDefinition fd = new FontDefinition(FontType.TTF, new FontFileDefinition("ttf", new FileSystemStreamSource(fileName)));
TtfFont font = Aspose.Font.Font.Open(fd) as TtfFont;
```
## Etapa 3: recuperar métricas de fonte
Recupere várias métricas de fonte, como ascendente, descendente, etc.
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
## Etapa 4: Obtenha a tabela de codificação Unicode
Recupere a tabela de codificação Unicode (cmap) da fonte.
```csharp
Aspose.Font.TtfCMapFormats.TtfCMapFormatBaseTable cmapTable = null;
if (font.TtfTables.CMapTable != null)
{
    cmapTable = font.TtfTables.CMapTable.FindUnicodeTable();
}
```
## Etapa 5: acessar informações do glifo
Acesse informações de glifo para um símbolo específico (por exemplo, 'A').
```csharp
char unicode = (char)65; // Unicode para 'A'
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
## Conclusão
Neste tutorial, abordamos como obter métricas de fonte usando Aspose.Font for .NET. Seguindo o guia passo a passo e compreendendo os pré-requisitos, você pode trabalhar com eficiência com fontes em seus aplicativos .NET usando a API Aspose.Font.
## Perguntas frequentes
### 1. Posso usar Aspose.Font for .NET com qualquer formato de arquivo de fonte?
Sim, Aspose.Font for .NET suporta vários formatos de fonte, como TrueType (TTF), OpenType (OTF) e muito mais.
### 2. Existe uma avaliação gratuita disponível para Aspose.Font for .NET?
 Sim, você pode obter uma avaliação gratuita do Aspose.Font for .NET no site[local na rede Internet](https://releases.aspose.com/).
### 3. Como posso acessar o suporte para Aspose.Font for .NET?
 Você pode acessar o suporte para Aspose.Font for .NET através do[fórum](https://forum.aspose.com/c/font/41).
### 4. Posso adquirir uma licença temporária do Aspose.Font for .NET?
 Sim, você pode comprar uma licença temporária no[Aspose loja](https://purchase.aspose.com/temporary-license/).
### 5. Existe documentação disponível para Aspose.Font for .NET?
 Sim, você pode acessar a documentação do Aspose.Font for .NET[aqui](https://reference.aspose.com/font/net/).