---
title: Extraiga restricciones de licencia en Aspose.Font para .NET
linktitle: Extraiga restricciones de licencia en Aspose.Font para .NET
second_title: Aspose.Font API .NET
description: Aprenda cómo extraer restricciones de licencia de fuentes TrueType usando Aspose.Font para .NET con nuestra guía detallada. Perfecto para desarrolladores que trabajan con fuentes en .NET.
type: docs
weight: 11
url: /es/net/truetype-opentype/extract-license-restrictions/
---
## Introducción
¡Hola! Si es un desarrollador que trabaja con fuentes en aplicaciones .NET, es fundamental comprender las restricciones de licencia integradas en los archivos de fuentes. Esta guía completa lo guiará en la extracción de restricciones de licencia de fuentes TrueType usando Aspose.Font para .NET. Ya sea que esté garantizando el cumplimiento de las licencias de fuentes o simplemente tenga curiosidad sobre los permisos de las fuentes que está utilizando, lo tenemos cubierto. Al final de este tutorial, podrá comprobar fácilmente las restricciones de licencia de cualquier fuente TrueType. ¿Listo para sumergirte? ¡Empecemos!
## Requisitos previos
Antes de pasar al código, asegúrese de tener lo siguiente:
-  Aspose.Font para .NET: Descárguelo desde[Página de lanzamientos de Aspose](https://releases.aspose.com/font/net/).
- Entorno de desarrollo .NET: Visual Studio o cualquier otro IDE compatible.
- Conocimientos básicos de C#: familiaridad con la programación en C# y el marco .NET.
- Archivo de fuente: un archivo de fuente TrueType, como`Montserrat-Regular.ttf`.
## Importar espacios de nombres
Para comenzar a usar Aspose.Font para .NET, deberá importar los espacios de nombres necesarios. Estos espacios de nombres le proporcionarán las clases y métodos necesarios para la manipulación de fuentes.
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
Ahora, dividamos todo el proceso en pasos simples.
## Paso 1: cargue la fuente TrueType
 Primero, necesitamos cargar la fuente TrueType en nuestra aplicación. Esto implica definir la ruta del archivo y crear un`FontDefinition` objeto.
## Paso 1.1: especificar la ruta del archivo de fuente
Comience especificando el directorio donde se encuentra su archivo de fuente y la ruta completa al archivo.
```csharp
string dataDir = "Your Document Directory";
string fileName = dataDir + "Montserrat-Regular.ttf";
```
## Paso 1.2: crear un objeto FontDefinition
 A continuación, cree un`FontDefinition` Objeto para gestionar los datos de fuente. Este paso implica especificar el tipo de fuente y el origen del archivo.
```csharp
FontDefinition fd = new FontDefinition(FontType.TTF, new FontFileDefinition("ttf", new FileSystemStreamSource(fileName)));
```
## Paso 2: abre la fuente TrueType
 Con el`FontDefinition` objeto listo, el siguiente paso es abrir la fuente usando Aspose.Font para .NET.
## Paso 2.1: utilice el método abierto
 Utilizar el`Open` método de la`Font` clase para cargar la fuente. Transmitir el objeto devuelto a un`TtfFont`.
```csharp
TtfFont font = Aspose.Font.Font.Open(fd) as TtfFont;
```
## Paso 3: extraer las restricciones de la licencia
Ahora que la fuente está cargada, es hora de extraer las restricciones de la licencia. Esto implica acceder a la tabla OS/2 de la fuente y recuperar los indicadores de licencia.
## Paso 3.1: Inicializar indicadores de licencia
 Inicializar un`LicenseFlags` objeto de almacenar la información de la licencia.
```csharp
LicenseFlags licenseFlags = null;
```
## Paso 3.2: Verifique la tabla OS/2
Compruebe si la tabla OS/2 existe en la fuente y obtenga los indicadores de licencia si es así.
```csharp
if (font.TtfTables.Os2Table != null)
{
    licenseFlags = font.TtfTables.Os2Table.GetLicenseFlags();
}
```
## Paso 3.3: Interpretar los indicadores de licencia
Interprete los indicadores de licencia y genere las restricciones de licencia en función de los indicadores recuperados.
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
## Conclusión
¡Y ahí lo tienes! Ha aprendido con éxito cómo extraer restricciones de licencia de fuentes TrueType usando Aspose.Font para .NET. Esta guía lo ha guiado a través de los pasos esenciales necesarios para trabajar con fuentes en sus aplicaciones .NET, garantizando que cumpla con los requisitos de licencia. Con este conocimiento, podrá administrar con confianza las fuentes en sus proyectos, sabiendo que cumple con las pautas legales.
## Preguntas frecuentes
### 1. ¿Qué es Aspose.Font para .NET?
Aspose.Font para .NET es una potente API que permite a los desarrolladores trabajar con archivos de fuentes, lo que permite cargar, editar y guardar fuentes dentro de aplicaciones .NET.
### 2. ¿Puedo trabajar con otros formatos de fuente usando Aspose.Font para .NET?
¡Absolutamente! Aspose.Font para .NET admite múltiples formatos de fuentes, incluidos TTF, OTF, Type 1 y CFF, entre otros.
### 3. ¿Cómo obtengo una licencia de Aspose.Font para .NET?
 Puede adquirir una licencia en el[Aspose página de compra](https://purchase.aspose.com/buy) . Para fines de evaluación, puede obtener una licencia temporal.[aquí](https://purchase.aspose.com/temporary-license/).
### 4. ¿Dónde puedo encontrar documentación detallada?
 La documentación detallada está disponible en el[Página de documentación de Aspose.Font para .NET](https://reference.aspose.com/font/net/).
### 5. ¿Cómo puedo obtener asistencia si tengo problemas?
 Para obtener soporte, puede visitar el[Foro de soporte de Aspose.Font](https://forum.aspose.com/c/font/41).