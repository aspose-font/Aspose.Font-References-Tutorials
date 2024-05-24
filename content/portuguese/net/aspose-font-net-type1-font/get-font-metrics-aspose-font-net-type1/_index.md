---
title: Obtenha métricas de fonte em Aspose.Font para .NET Tipo 1
linktitle: Obtenha métricas de fonte em Aspose.Font para .NET Tipo 1
second_title: API Aspose.Font .NET
description: Aprenda como obter métricas de fonte usando Aspose.Font for .NET neste tutorial passo a passo abrangente. Perfeito para desenvolvedores de qualquer nível!
type: docs
weight: 11
url: /pt/net/aspose-font-net-type1-font/get-font-metrics-aspose-font-net-type1/
---
## Introdução
Bem-vindo ao guia definitivo sobre como obter métricas de fontes usando Aspose.Font for .NET! Quer você seja um desenvolvedor experiente ou esteja apenas mergulhando no mundo das fontes, este tutorial o guiará pelo processo passo a passo. Ao final deste artigo, você será capaz de extrair métricas detalhadas de fontes e entender como manipulá-las em seus aplicativos .NET. Então, vamos mergulhar e começar esta jornada emocionante!
## Pré-requisitos
Antes de mergulharmos no âmago da questão, há algumas coisas que você precisa ter em mente:
- Visual Studio: certifique-se de ter o Visual Studio instalado em sua máquina.
-  Aspose.Font for .NET: Baixe e instale a biblioteca Aspose.Font for .NET. Você pode obtê-lo no[Link para Download](https://releases.aspose.com/font/net/).
- Conhecimento básico de C#: É necessária familiaridade com programação C# para acompanhar os exemplos.
- Um arquivo de fonte: tenha um arquivo de fonte TrueType (.ttf) pronto. Você pode usar qualquer arquivo .ttf para este tutorial.
Agora que temos tudo pronto, vamos começar importando os namespaces necessários.
## Importar namespaces
Para começar a trabalhar com Aspose.Font for .NET, você precisará incluir os namespaces apropriados em seu projeto. Veja como você faz isso:
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
Com esses namespaces implementados, você está pronto para começar a trabalhar com fontes em seu aplicativo .NET.
## Etapa 1: carregue o arquivo de fonte
Primeiro, você precisa carregar o arquivo de fonte em seu aplicativo. É assim que se faz:
### Carregar arquivo de fonte
1. Defina o caminho para o seu arquivo de fonte. 
2.  Criar uma`FontDefinition` objeto.
3.  Use o`Font.Open` método para carregar a fonte.
```csharp
string dataDir = "Your Document Directory";
string fileName = dataDir + "Montserrat-Regular.ttf";
FontDefinition fd = new FontDefinition(FontType.TTF, new FontFileDefinition("ttf", new FileSystemStreamSource(fileName)));
TtfFont font = Aspose.Font.Font.Open(fd) as TtfFont;
```
 Aqui, estamos usando o`FontDefinition` class para definir o tipo e localização do nosso arquivo de fonte. O`Font.Open` método carrega a fonte em um`TtfFont` objeto.
## Etapa 2: recuperar informações básicas da fonte
Depois que a fonte for carregada, você poderá recuperar algumas informações básicas sobre ela.
### Obtenha o nome da fonte e a contagem de glifos
```csharp
string name = font.FontName;
Console.WriteLine("Font name: " + name);
Console.WriteLine("Glyph count: " + font.NumGlyphs);
```
Este trecho de código imprimirá o nome da fonte e o número de glifos que ela contém.
## Etapa 3: extrair métricas de fonte
As métricas de fonte fornecem informações detalhadas sobre as características da fonte.
### Exibir métricas de fonte
```csharp
string metrics = string.Format(
    "Font metrics: ascender - {0}, descender - {1}, typo ascender = {2}, typo descender = {3}, UnitsPerEm = {4}",
    font.Metrics.Ascender, font.Metrics.Descender,
    font.Metrics.TypoAscender, font.Metrics.TypoDescender, font.Metrics.UnitsPerEM);
Console.WriteLine(metrics);
```
Este snippet formata e imprime várias métricas da fonte, como ascendente, descendente e unidades por EM.
## Etapa 4: acesse a tabela CMap Unicode
A tabela CMap ajuda no mapeamento de códigos de caracteres para índices de glifos.
### Recuperar e verificar a tabela CMap
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
Este código recupera a tabela CMap e imprime PlatformID e PlatformSpecificID.
## Etapa 5: obtenha informações sobre o glifo
Finalmente, vamos recuperar informações sobre um glifo específico, como o glifo do caractere 'A'.
### Recuperar informações do glifo
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
Este trecho obtém o índice do glifo para 'A', recupera o glifo usando esse índice e imprime suas métricas, incluindo caixa delimitadora e largura.
## Conclusão
Parabéns! Você aprendeu com sucesso como obter métricas de fonte usando Aspose.Font for .NET. Seguindo essas etapas, você pode extrair e manipular facilmente informações de fonte em seus aplicativos. Este tutorial deve fornecer uma base sólida para operações de fontes mais avançadas. Boa codificação!
## Perguntas frequentes
### Q1: Posso usar Aspose.Font for .NET com outros formatos de fonte?
Sim, Aspose.Font for .NET suporta vários formatos de fonte, incluindo TrueType, OpenType, Type1 e muito mais.
### Q2: Onde posso obter uma avaliação gratuita do Aspose.Font for .NET?
 Você pode baixar uma versão de teste gratuita no site[Página de lançamentos do Aspose](https://releases.aspose.com/).
### Q3: Como posso comprar uma licença do Aspose.Font for .NET?
 Você pode comprar uma licença no[Aspose página de compra](https://purchase.aspose.com/buy).
### Q4: Existe suporte disponível para Aspose.Font for .NET?
 Sim, você pode obter suporte do[Aspose fórum de suporte](https://forum.aspose.com/c/font/41).
### Q5: Posso usar Aspose.Font for .NET em um projeto comercial?
Sim, você pode usar Aspose.Font for .NET em projetos comerciais, mas precisará de uma licença válida.