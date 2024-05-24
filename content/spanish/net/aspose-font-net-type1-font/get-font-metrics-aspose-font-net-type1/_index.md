---
title: Obtenga métricas de fuentes en Aspose.Font para .NET Tipo 1
linktitle: Obtenga métricas de fuentes en Aspose.Font para .NET Tipo 1
second_title: Aspose.Font API .NET
description: Aprenda cómo obtener métricas de fuentes usando Aspose.Font para .NET en este completo tutorial paso a paso. ¡Perfecto para desarrolladores de cualquier nivel!
type: docs
weight: 11
url: /es/net/aspose-font-net-type1-font/get-font-metrics-aspose-font-net-type1/
---
## Introducción
¡Bienvenido a la guía definitiva sobre cómo obtener métricas de fuentes utilizando Aspose.Font para .NET! Ya sea que sea un desarrollador experimentado o simplemente esté inmerso en el mundo de las fuentes, este tutorial lo guiará a través del proceso paso a paso. Al final de este artículo, podrá extraer métricas de fuentes detalladas y comprender cómo manipularlas dentro de sus aplicaciones .NET. Entonces, ¡sumergámonos y comencemos con este emocionante viaje!
## Requisitos previos
Antes de profundizar en el meollo de la cuestión, hay algunas cosas que necesitará tener implementadas:
- Visual Studio: asegúrese de tener Visual Studio instalado en su máquina.
-  Aspose.Font para .NET: descargue e instale la biblioteca Aspose.Font para .NET. Puedes conseguirlo desde el[enlace de descarga](https://releases.aspose.com/font/net/).
- Conocimientos básicos de C#: Es necesario estar familiarizado con la programación en C# para seguir los ejemplos.
- Un archivo de fuente: tenga listo un archivo de fuente TrueType (.ttf). Puede utilizar cualquier archivo .ttf para este tutorial.
Ahora que tenemos todo listo, comencemos importando los espacios de nombres necesarios.
## Importar espacios de nombres
Para comenzar a trabajar con Aspose.Font para .NET, deberá incluir los espacios de nombres apropiados en su proyecto. Así es como lo haces:
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
Con estos espacios de nombres implementados, estará listo para comenzar a trabajar con fuentes en su aplicación .NET.
## Paso 1: cargue el archivo de fuente
Primero, necesitas cargar el archivo de fuente en tu aplicación. Así es como lo haces:
### Cargar archivo de fuente
1. Defina la ruta a su archivo de fuente. 
2.  Crear un`FontDefinition` objeto.
3.  Utilizar el`Font.Open` método para cargar la fuente.
```csharp
string dataDir = "Your Document Directory";
string fileName = dataDir + "Montserrat-Regular.ttf";
FontDefinition fd = new FontDefinition(FontType.TTF, new FontFileDefinition("ttf", new FileSystemStreamSource(fileName)));
TtfFont font = Aspose.Font.Font.Open(fd) as TtfFont;
```
 Aquí estamos usando el`FontDefinition` clase para definir el tipo y la ubicación de nuestro archivo de fuente. El`Font.Open` El método carga la fuente en un`TtfFont` objeto.
## Paso 2: recuperar información básica de fuentes
Una vez cargada la fuente, puede recuperar información básica sobre ella.
### Obtener nombre de fuente y recuento de glifos
```csharp
string name = font.FontName;
Console.WriteLine("Font name: " + name);
Console.WriteLine("Glyph count: " + font.NumGlyphs);
```
Este fragmento de código imprimirá el nombre de la fuente y la cantidad de glifos que contiene.
## Paso 3: extraer métricas de fuentes
Las métricas de fuentes proporcionan información detallada sobre las características de la fuente.
### Mostrar métricas de fuentes
```csharp
string metrics = string.Format(
    "Font metrics: ascender - {0}, descender - {1}, typo ascender = {2}, typo descender = {3}, UnitsPerEm = {4}",
    font.Metrics.Ascender, font.Metrics.Descender,
    font.Metrics.TypoAscender, font.Metrics.TypoDescender, font.Metrics.UnitsPerEM);
Console.WriteLine(metrics);
```
Este fragmento formatea e imprime varias métricas de la fuente, como ascendente, descendente y unidades por EM.
## Paso 4: acceda a la tabla CMap Unicode
La tabla CMap ayuda a asignar códigos de caracteres a índices de glifos.
### Recuperar y verificar la tabla CMap
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
Este código recupera la tabla CMap e imprime PlatformID y PlatformSpecificID.
## Paso 5: obtenga información de glifos
Finalmente, recuperemos información sobre un glifo específico, como el glifo del carácter 'A'.
### Recuperar información de glifos
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
Este fragmento obtiene el índice de glifo para 'A', recupera el glifo usando este índice e imprime sus métricas, incluido el cuadro delimitador y el ancho.
## Conclusión
¡Felicidades! Ha aprendido con éxito cómo obtener métricas de fuentes usando Aspose.Font para .NET. Si sigue estos pasos, podrá extraer y manipular fácilmente la información de fuentes en sus aplicaciones. Este tutorial debería proporcionar una base sólida para operaciones de fuentes más avanzadas. ¡Feliz codificación!
## Preguntas frecuentes
### P1: ¿Puedo usar Aspose.Font para .NET con otros formatos de fuente?
Sí, Aspose.Font para .NET admite varios formatos de fuente, incluidos TrueType, OpenType, Type1 y más.
### P2: ¿Dónde puedo obtener una prueba gratuita de Aspose.Font para .NET?
 Puede descargar una prueba gratuita desde[Página de lanzamientos de Aspose](https://releases.aspose.com/).
### P3: ¿Cómo compro una licencia de Aspose.Font para .NET?
 Puede adquirir una licencia en el[Aspose página de compra](https://purchase.aspose.com/buy).
### P4: ¿Hay soporte disponible para Aspose.Font para .NET?
 Sí, puedes obtener apoyo del[Aspose foro de soporte](https://forum.aspose.com/c/font/41).
### P5: ¿Puedo utilizar Aspose.Font para .NET en un proyecto comercial?
Sí, puede utilizar Aspose.Font para .NET en proyectos comerciales, pero necesitará una licencia válida.