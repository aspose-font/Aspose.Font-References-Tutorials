---
title: Obtenez les métriques de police dans Aspose.Font pour .NET Type 1
linktitle: Obtenez les métriques de police dans Aspose.Font pour .NET Type 1
second_title: API Aspose.Font .NET
description: Découvrez comment obtenir des métriques de police à l'aide d'Aspose.Font pour .NET dans ce didacticiel complet, étape par étape. Parfait pour les développeurs de tous niveaux !
type: docs
weight: 11
url: /fr/net/aspose-font-net-type1-font/get-font-metrics-aspose-font-net-type1/
---
## Introduction
Bienvenue dans le guide ultime pour obtenir des métriques de polices à l'aide d'Aspose.Font pour .NET ! Que vous soyez un développeur chevronné ou que vous vous plongez simplement dans le monde des polices, ce didacticiel vous guidera pas à pas tout au long du processus. À la fin de cet article, vous serez en mesure d'extraire des métriques détaillées sur les polices et de comprendre comment les manipuler dans vos applications .NET. Alors, plongeons-nous et commençons ce voyage passionnant !
## Conditions préalables
Avant de plonger dans le vif du sujet, vous devez mettre en place quelques éléments :
- Visual Studio : assurez-vous que Visual Studio est installé sur votre ordinateur.
-  Aspose.Font pour .NET : téléchargez et installez la bibliothèque Aspose.Font pour .NET. Vous pouvez l'obtenir auprès du[lien de téléchargement](https://releases.aspose.com/font/net/).
- Connaissance de base de C# : Une familiarité avec la programmation C# est nécessaire pour suivre les exemples.
- Un fichier de police : préparez un fichier de police TrueType (.ttf). Vous pouvez utiliser n'importe quel fichier .ttf pour ce didacticiel.
Maintenant que tout est prêt, commençons par importer les espaces de noms nécessaires.
## Importer des espaces de noms
Pour commencer à travailler avec Aspose.Font pour .NET, vous devrez inclure les espaces de noms appropriés dans votre projet. Voici comment procéder :
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
Une fois ces espaces de noms en place, vous êtes prêt à commencer à travailler avec les polices dans votre application .NET.
## Étape 1 : Charger le fichier de police
Tout d’abord, vous devez charger le fichier de police dans votre application. Voici comment procéder :
### Charger le fichier de police
1. Définissez le chemin d'accès à votre fichier de police. 
2.  Créer un`FontDefinition` objet.
3.  Utilisez le`Font.Open` méthode pour charger la police.
```csharp
string dataDir = "Your Document Directory";
string fileName = dataDir + "Montserrat-Regular.ttf";
FontDefinition fd = new FontDefinition(FontType.TTF, new FontFileDefinition("ttf", new FileSystemStreamSource(fileName)));
TtfFont font = Aspose.Font.Font.Open(fd) as TtfFont;
```
 Ici, nous utilisons le`FontDefinition` classe pour définir le type et l’emplacement de notre fichier de police. Le`Font.Open` La méthode charge la police dans un`TtfFont` objet.
## Étape 2 : Récupérer les informations de base sur la police
Une fois la police chargée, vous pouvez récupérer quelques informations de base la concernant.
### Obtenir le nom de la police et le nombre de glyphes
```csharp
string name = font.FontName;
Console.WriteLine("Font name: " + name);
Console.WriteLine("Glyph count: " + font.NumGlyphs);
```
Cet extrait de code imprimera le nom de la police et le nombre de glyphes qu'elle contient.
## Étape 3 : Extraire les métriques de police
Les métriques de police fournissent des informations détaillées sur les caractéristiques de la police.
### Afficher les mesures de police
```csharp
string metrics = string.Format(
    "Font metrics: ascender - {0}, descender - {1}, typo ascender = {2}, typo descender = {3}, UnitsPerEm = {4}",
    font.Metrics.Ascender, font.Metrics.Descender,
    font.Metrics.TypoAscender, font.Metrics.TypoDescender, font.Metrics.UnitsPerEM);
Console.WriteLine(metrics);
```
Cet extrait formate et imprime diverses métriques de la police, telles que l'ascendant, le descendant et les unités par EM.
## Étape 4 : accéder à la table Unicode CMap
La table CMap aide à mapper les codes de caractères aux indices de glyphes.
### Récupérer et vérifier la table CMap
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
Ce code récupère la table CMap et imprime le PlatformID et le PlatformSpecificID.
## Étape 5 : obtenir des informations sur les glyphes
Enfin, récupérons des informations sur un glyphe spécifique, tel que le glyphe du caractère « A ».
### Récupérer les informations sur les glyphes
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
Cet extrait obtient l'index du glyphe pour « A », récupère le glyphe à l'aide de cet index et imprime ses métriques, y compris le cadre de délimitation et la largeur.
## Conclusion
Toutes nos félicitations! Vous avez appris avec succès comment obtenir des métriques de police à l’aide d’Aspose.Font pour .NET. En suivant ces étapes, vous pouvez facilement extraire et manipuler les informations sur les polices dans vos applications. Ce didacticiel devrait fournir une base solide pour des opérations de polices plus avancées. Bon codage !
## FAQ
### Q1 : Puis-je utiliser Aspose.Font pour .NET avec d’autres formats de police ?
Oui, Aspose.Font for .NET prend en charge divers formats de police, notamment TrueType, OpenType, Type1, etc.
### Q2 : Où puis-je obtenir un essai gratuit d'Aspose.Font pour .NET ?
 Vous pouvez télécharger un essai gratuit à partir du[Page des versions d'Aspose](https://releases.aspose.com/).
### Q3 : Comment acheter une licence pour Aspose.Font pour .NET ?
 Vous pouvez acheter une licence auprès du[Page d'achat Aspose](https://purchase.aspose.com/buy).
### Q4 : Existe-t-il une prise en charge disponible pour Aspose.Font pour .NET ?
 Oui, vous pouvez bénéficier de l'aide du[Forum d'assistance Aspose](https://forum.aspose.com/c/font/41).
### Q5 : Puis-je utiliser Aspose.Font pour .NET dans un projet commercial ?
Oui, vous pouvez utiliser Aspose.Font pour .NET dans des projets commerciaux, mais vous aurez besoin d'une licence valide.