---
title: Obtenez des métriques de police dans Aspose.Font pour .NET
linktitle: Obtenez des métriques de police dans Aspose.Font pour .NET
second_title: API Aspose.Font .NET
description: Découvrez comment obtenir des métriques de police à l’aide d’Aspose.Font pour .NET. Guide étape par étape avec des exemples de code. Prérequis et FAQ inclus. #Aspose #Font
type: docs
weight: 12
url: /fr/net/truetype-opentype/get-font-metrics/
---
## Introduction
Aspose.Font for .NET est une API puissante qui permet aux développeurs de travailler avec des polices dans leurs applications .NET. Que vous ayez besoin d'extraire des métriques de police, de manipuler des glyphes ou d'accéder à des données de police, Aspose.Font fournit des fonctionnalités complètes pour rationaliser les tâches liées aux polices. Dans ce didacticiel, nous verrons comment obtenir des métriques de police à l'aide d'Aspose.Font pour .NET.
## Conditions préalables
Avant de plonger dans ce didacticiel, assurez-vous d'avoir configuré les conditions préalables suivantes :
### 1. Aspose.Font pour l'installation de .NET
 Assurez-vous que Aspose.Font pour .NET est installé dans votre environnement de développement. Si vous ne l'avez pas déjà fait, vous pouvez télécharger l'API depuis le[Aspose.Releases](https://releases.aspose.com/font/net/) ou via le gestionnaire de packages NuGet.
### 2. Configuration de l'environnement de développement
Assurez-vous d'avoir un environnement de développement .NET configuré avec Visual Studio ou tout autre IDE compatible installé.

## Importer des espaces de noms
Dans votre application .NET, vous devez importer les espaces de noms nécessaires pour travailler avec Aspose.Font for .NET.
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
Maintenant, décomposons l'exemple fourni en plusieurs étapes et expliquons chacune en détail.
## Étape 1 : Définir le chemin du fichier de police
Tout d’abord, définissez le chemin du fichier de la police avec laquelle vous souhaitez travailler.
```csharp
string dataDir = "Your Document Directory";
string fileName = dataDir + "Montserrat-Regular.ttf"; //Nom du fichier de police avec chemin complet
```
## Étape 2 : ouvrez le fichier de police
Ensuite, ouvrez le fichier de police à l’aide de l’API Aspose.Font.
```csharp
FontDefinition fd = new FontDefinition(FontType.TTF, new FontFileDefinition("ttf", new FileSystemStreamSource(fileName)));
TtfFont font = Aspose.Font.Font.Open(fd) as TtfFont;
```
## Étape 3 : Récupérer les métriques de police
Récupérez diverses métriques de police telles que l'ascendant, le descendant, etc.
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
## Étape 4 : Obtenez la table de codage Unicode
Récupérez la table de codage Unicode (cmap) de la police.
```csharp
Aspose.Font.TtfCMapFormats.TtfCMapFormatBaseTable cmapTable = null;
if (font.TtfTables.CMapTable != null)
{
    cmapTable = font.TtfTables.CMapTable.FindUnicodeTable();
}
```
## Étape 5 : accéder aux informations sur les glyphes
Accédez aux informations sur les glyphes d'un symbole spécifique (par exemple, « A »).
```csharp
char unicode = (char)65; // Unicode pour « A »
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
## Conclusion
Dans ce didacticiel, nous avons expliqué comment obtenir des métriques de police à l'aide d'Aspose.Font pour .NET. En suivant le guide étape par étape et en comprenant les conditions préalables, vous pouvez travailler efficacement avec les polices dans vos applications .NET à l'aide de l'API Aspose.Font.
## FAQ
### 1. Puis-je utiliser Aspose.Font pour .NET avec n’importe quel format de fichier de police ?
Oui, Aspose.Font for .NET prend en charge divers formats de police tels que TrueType (TTF), OpenType (OTF), etc.
### 2. Existe-t-il un essai gratuit disponible pour Aspose.Font pour .NET ?
 Oui, vous pouvez obtenir un essai gratuit d'Aspose.Font pour .NET à partir du[site web](https://releases.aspose.com/).
### 3. Comment puis-je accéder au support d'Aspose.Font pour .NET ?
 Vous pouvez accéder à la prise en charge d'Aspose.Font pour .NET via le[forum](https://forum.aspose.com/c/font/41).
### 4. Puis-je acheter une licence temporaire pour Aspose.Font pour .NET ?
 Oui, vous pouvez acheter une licence temporaire auprès du[Magasin Aspose](https://purchase.aspose.com/temporary-license/).
### 5. Existe-t-il une documentation disponible pour Aspose.Font pour .NET ?
 Oui, vous pouvez accéder à la documentation d'Aspose.Font pour .NET[ici](https://reference.aspose.com/font/net/).