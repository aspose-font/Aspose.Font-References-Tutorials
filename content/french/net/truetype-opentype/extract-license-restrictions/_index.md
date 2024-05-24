---
title: Extraire les restrictions de licence dans Aspose.Font pour .NET
linktitle: Extraire les restrictions de licence dans Aspose.Font pour .NET
second_title: API Aspose.Font .NET
description: Découvrez comment extraire les restrictions de licence des polices TrueType à l'aide d'Aspose.Font for .NET avec notre guide détaillé. Parfait pour les développeurs travaillant avec des polices dans .NET.
type: docs
weight: 11
url: /fr/net/truetype-opentype/extract-license-restrictions/
---
## Introduction
Salut! Si vous êtes un développeur travaillant avec des polices dans des applications .NET, il est crucial de comprendre les restrictions de licence intégrées dans les fichiers de polices. Ce guide complet vous guidera dans l'extraction des restrictions de licence des polices TrueType à l'aide d'Aspose.Font for .NET. Que vous souhaitiez garantir le respect des licences de polices ou que vous soyez simplement curieux de connaître les autorisations des polices que vous utilisez, nous avons ce qu'il vous faut. À la fin de ce didacticiel, vous serez en mesure de vérifier facilement n'importe quelle police TrueType pour ses restrictions de licence. Prêt à plonger ? Commençons!
## Conditions préalables
Avant de passer au code, assurez-vous d'avoir les éléments suivants :
-  Aspose.Font pour .NET : téléchargez-le depuis le[Page des versions d'Aspose](https://releases.aspose.com/font/net/).
- Environnement de développement .NET : Visual Studio ou tout autre IDE compatible.
- Connaissance de base de C# : Familiarité avec la programmation C# et le framework .NET.
- Fichier de police : un fichier de police TrueType, tel que`Montserrat-Regular.ttf`.
## Importer des espaces de noms
Pour commencer à utiliser Aspose.Font pour .NET, vous devrez importer les espaces de noms nécessaires. Ces espaces de noms vous fourniront les classes et méthodes requises pour la manipulation des polices.
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
Maintenant, décomposons l'ensemble du processus en étapes simples.
## Étape 1 : Chargez la police TrueType
 Tout d’abord, nous devons charger la police TrueType dans notre application. Cela implique de définir le chemin du fichier et de créer un`FontDefinition` objet.
## Étape 1.1 : Spécifiez le chemin du fichier de police
Commencez par spécifier le répertoire où se trouve votre fichier de police et le chemin complet du fichier.
```csharp
string dataDir = "Your Document Directory";
string fileName = dataDir + "Montserrat-Regular.ttf";
```
## Étape 1.2 : Créer un objet FontDefinition
 Ensuite, créez un`FontDefinition` objet pour gérer les données de police. Cette étape implique de spécifier le type de police et la source du fichier.
```csharp
FontDefinition fd = new FontDefinition(FontType.TTF, new FontFileDefinition("ttf", new FileSystemStreamSource(fileName)));
```
## Étape 2 : ouvrez la police TrueType
 Avec le`FontDefinition` objet prêt, l'étape suivante consiste à ouvrir la police à l'aide d'Aspose.Font for .NET.
## Étape 2.1 : utiliser la méthode ouverte
 Utilisez le`Open` méthode du`Font` classe pour charger la police. Caster l'objet retourné vers un`TtfFont`.
```csharp
TtfFont font = Aspose.Font.Font.Open(fd) as TtfFont;
```
## Étape 3 : Extraire les restrictions de licence
Maintenant que la police est chargée, il est temps d'extraire les restrictions de licence. Cela implique d'accéder à la table OS/2 de la police et de récupérer les indicateurs de licence.
## Étape 3.1 : initialiser les indicateurs de licence
 Initialiser un`LicenseFlags` objet pour stocker les informations de licence.
```csharp
LicenseFlags licenseFlags = null;
```
## Étape 3.2 : Vérifiez le tableau OS/2
Vérifiez si la table OS/2 existe dans la police et obtenez les indicateurs de licence si c'est le cas.
```csharp
if (font.TtfTables.Os2Table != null)
{
    licenseFlags = font.TtfTables.Os2Table.GetLicenseFlags();
}
```
## Étape 3.3 : Interpréter les indicateurs de licence
Interprétez les indicateurs de licence et affichez les restrictions de licence en fonction des indicateurs récupérés.
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
## Conclusion
Et voila! Vous avez appris avec succès comment extraire les restrictions de licence des polices TrueType à l'aide d'Aspose.Font for .NET. Ce guide vous a guidé à travers les étapes essentielles nécessaires pour utiliser les polices dans vos applications .NET, garantissant ainsi votre conformité aux exigences de licence. Grâce à ces connaissances, vous pouvez gérer en toute confiance les polices de vos projets, sachant que vous respectez les directives légales.
## FAQ
### 1. Qu'est-ce qu'Aspose.Font pour .NET ?
Aspose.Font for .NET est une API puissante qui permet aux développeurs de travailler avec des fichiers de polices, permettant le chargement, la modification et l'enregistrement de polices dans les applications .NET.
### 2. Puis-je travailler avec d'autres formats de polices en utilisant Aspose.Font pour .NET ?
Absolument! Aspose.Font for .NET prend en charge plusieurs formats de police, notamment TTF, OTF, Type 1 et CFF.
### 3. Comment puis-je obtenir une licence pour Aspose.Font pour .NET ?
 Vous pouvez acheter une licence auprès du[Page d'achat Aspose](https://purchase.aspose.com/buy) . À des fins d'évaluation, vous pouvez obtenir une licence temporaire[ici](https://purchase.aspose.com/temporary-license/).
### 4. Où puis-je trouver une documentation détaillée ?
 Une documentation détaillée est disponible sur le[Page de documentation Aspose.Font pour .NET](https://reference.aspose.com/font/net/).
### 5. Comment puis-je obtenir de l'aide si je rencontre des problèmes ?
 Pour obtenir de l'aide, vous pouvez visiter le[Forum d'assistance Aspose.Font](https://forum.aspose.com/c/font/41).