---
title: Obtenga métricas de fuentes en Aspose.Font para .NET
linktitle: Obtenga métricas de fuentes en Aspose.Font para .NET
second_title: Aspose.Font API .NET
description: Aprenda cómo obtener métricas de fuentes usando Aspose.Font para .NET. Guía paso a paso con ejemplos de código. Requisitos previos y preguntas frecuentes incluidos. #Aspose #Fuente
type: docs
weight: 12
url: /es/net/truetype-opentype/get-font-metrics/
---
## Introducción
Aspose.Font para .NET es una potente API que permite a los desarrolladores trabajar con fuentes en sus aplicaciones .NET. Ya sea que necesite extraer métricas de fuentes, manipular glifos o acceder a datos de fuentes, Aspose.Font proporciona una funcionalidad integral para optimizar las tareas relacionadas con las fuentes. En este tutorial, exploraremos cómo obtener métricas de fuentes usando Aspose.Font para .NET.
## Requisitos previos
Antes de sumergirse en este tutorial, asegúrese de tener configurados los siguientes requisitos previos:
### 1. Aspose.Font para instalación de .NET
 Asegúrese de tener Aspose.Font para .NET instalado en su entorno de desarrollo. Si aún no lo ha hecho, puede descargar la API desde[Lanzamientos.Aspose](https://releases.aspose.com/font/net/) o mediante el administrador de paquetes NuGet.
### 2. Configuración del entorno de desarrollo
Asegúrese de tener un entorno de desarrollo .NET configurado con Visual Studio o cualquier otro IDE compatible instalado.

## Importar espacios de nombres
En su aplicación .NET, debe importar los espacios de nombres necesarios para trabajar con Aspose.Font para .NET.
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
Ahora, dividamos el ejemplo proporcionado en varios pasos y expliquemos cada uno en detalle.
## Paso 1: definir la ruta del archivo de fuente
Primero, defina la ruta del archivo de la fuente con la que desea trabajar.
```csharp
string dataDir = "Your Document Directory";
string fileName = dataDir + "Montserrat-Regular.ttf"; //Nombre del archivo de fuente con ruta completa
```
## Paso 2: abra el archivo de fuente
A continuación, abra el archivo de fuente usando la API Aspose.Font.
```csharp
FontDefinition fd = new FontDefinition(FontType.TTF, new FontFileDefinition("ttf", new FileSystemStreamSource(fileName)));
TtfFont font = Aspose.Font.Font.Open(fd) as TtfFont;
```
## Paso 3: recuperar métricas de fuentes
Recupere varias métricas de fuentes, como ascendentes, descendentes, etc.
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
## Paso 4: Obtenga la tabla de codificación Unicode
Recupere la tabla de codificación Unicode (cmap) de la fuente.
```csharp
Aspose.Font.TtfCMapFormats.TtfCMapFormatBaseTable cmapTable = null;
if (font.TtfTables.CMapTable != null)
{
    cmapTable = font.TtfTables.CMapTable.FindUnicodeTable();
}
```
## Paso 5: acceda a la información de glifos
Acceda a información de glifos para un símbolo específico (por ejemplo, 'A').
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
## Conclusión
En este tutorial, cubrimos cómo obtener métricas de fuentes usando Aspose.Font para .NET. Si sigue la guía paso a paso y comprende los requisitos previos, podrá trabajar de manera eficiente con fuentes en sus aplicaciones .NET utilizando la API Aspose.Font.
## Preguntas frecuentes
### 1. ¿Puedo usar Aspose.Font para .NET con cualquier formato de archivo de fuente?
Sí, Aspose.Font para .NET admite varios formatos de fuente, como TrueType (TTF), OpenType (OTF) y más.
### 2. ¿Existe una prueba gratuita de Aspose.Font para .NET?
 Sí, puede obtener una prueba gratuita de Aspose.Font para .NET desde[sitio web](https://releases.aspose.com/).
### 3. ¿Cómo puedo acceder al soporte de Aspose.Font para .NET?
 Puede acceder al soporte para Aspose.Font para .NET a través de[foro](https://forum.aspose.com/c/font/41).
### 4. ¿Puedo comprar una licencia temporal de Aspose.Font para .NET?
 Sí, puede comprar una licencia temporal en el[tienda aspose](https://purchase.aspose.com/temporary-license/).
### 5. ¿Existe documentación disponible para Aspose.Font para .NET?
 Sí, puede acceder a la documentación de Aspose.Font para .NET[aquí](https://reference.aspose.com/font/net/).