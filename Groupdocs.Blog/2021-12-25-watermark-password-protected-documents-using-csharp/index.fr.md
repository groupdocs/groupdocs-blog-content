---
title: "Filigrane des documents protégés par mot de passe à l'aide de C#"
date: Sat, 25 Dec 2021 07:54:23 +0000
draft: false
url: /fr/2021/12/25/watermark-password-protected-documents-using-csharp/
aliases:
- /2019/11/22/watermark-password-protected-documents-using-groupdocs-watermark-net-api/
author: 'Shoaib Khan'
summary: "Le filigrane est l'un des moyens de protéger vos documents contre une utilisation illégale. personnaliser vos fichiers ; mentionnant vos documents comme brouillons ou confidentiels. Afin de filigraner vos fichiers par programme, cet article vous explique **comment ajouter un filigrane à vos fichiers protégés par mot de passe à l'aide de C#**. Nous examinerons séparément l'ajout de filigranes de texte et d'image aux fichiers protégés."
tags: ['Document Watermarking', 'Watermark Protected Documents using CSharp', 'Watermark Protected Files using CSharp', 'watermark using csharp', 'Watermarking API for .NET']
categories: ['GroupDocs.Watermark Product Family']
---



{{< figure align=center src="images/watermark-protected-files-using-csharp.jpg" alt="Documents protégés par filigrane à l'aide de C #">}}


Le filigrane est l'un des moyens de protéger vos documents contre une utilisation illégale. personnaliser vos fichiers ; mentionnant vos documents comme brouillons ou confidentiels. Afin de filigraner vos fichiers par programme, cet article vous explique **comment ajouter un filigrane à vos fichiers protégés par mot de passe à l'aide de C#**. Nous examinerons séparément l'ajout de filigranes de texte et d'image aux fichiers protégés.

Les sujets suivants sont abordés ici :

* [API .NET pour filigraner les fichiers protégés par mot de passe][1]
* [Ajouter un filigrane aux fichiers protégés à l'aide de C#][2]
    * [Appliquer le filigrane de texte][3]
    * [Appliquer le filigrane de l'image][4]

## API .NET pour filigraner les fichiers protégés par mot de passe {#watermarking-dotnet-api}

[GroupDocs.Watermark][5] fournit une solution de filigrane et présente [API .NET qui permet de travailler avec des filigranes][6] dans les applications .NET. J'utiliserai cette API pour ajouter des filigranes de texte et d'image aux fichiers protégés par mot de passe.

Vous pouvez télécharger le programme d'installation **DLLs** ou **MSI** à partir de la [section téléchargements][7] ou installer l'API dans votre application .NET via [NuGet][8].

```
PM> Install-Package GroupDocs.Watermark
```

## Ajouter un filigrane aux fichiers protégés par mot de passe à l'aide de C# {#add-watermark-to-protected-files}

C'est assez simple; quelques lignes de code suffisent pour mettre un filigrane dans vos fichiers. Suivez simplement les étapes suivantes pour ajouter l'un ou l'autre type de filigrane.

* **Charger** le document/fichier protégé.
* **Appliquer** filigrane texte/image.
* **Enregistrer** le fichier en filigrane.

Voyons séparément comment ajouter des filigranes de texte, puis des filigranes d'image.

## Ajouter un filigrane de texte aux fichiers protégés à l'aide de C# {#text-watermark-to-protected-file}

Les filigranes de texte sont les plus utilisés pour mettre le nom de l'entreprise dans les documents ; mentionner le document comme BROUILLON ou CONFIDENTIEL ; ou toute autre raison similaire. Les étapes suivantes expliquent comment insérer un filigrane de texte dans des fichiers protégés par mot de passe à l'aide de C#.

* Préparez l'[option de chargement][9] en utilisant le mot de passe existant.
* Chargez le fichier protégé à l'aide de la classe [Watermarker][10] et de l'**option de chargement**.
* Préparez le filigrane en utilisant la classe [TextWatermark][11].
* Définissez le texte, l'apparence, la rotation, l'opacité, la couleur et d'autres propriétés du filigrane.
* Ajoutez un filigrane au document à l'aide de la méthode [Add()][12].
* Enregistrez le fichier filigrané à l'aide de la méthode [Save()][13].

Le code C# suivant insère un filigrane de texte dans un document PDF protégé.

```
/*
 * Apply Text Watermark to document (PDF, Word, PPT, Excel, ...) using C#
 */
LoadOptions loadOptions = new LoadOptions();
loadOptions.Password = "P@$$w0rd";
string filePath = "path/document.pdf";
using (Watermarker watermarker = new Watermarker(filePath, loadOptions))
{
    // Prepare Watermark Text and appearance. 
    TextWatermark watermark = new TextWatermark("Watermark", new Font("Arial", 12))
    {
        RotateAngle = -45,
        Opacity = .3,
        ForegroundColor = Color.Red,
    };
    // Add watermark to document and save.
    watermarker.Add(watermark);
    watermarker.Save("path/watermark-document.pdf");
}
```

## Ajouter un filigrane d'image aux fichiers protégés à l'aide de C # {#image-watermark-to-protected-file}

Si vous souhaitez insérer votre logo ou une autre image en filigrane, vous pouvez l'ajouter à l'aide de la classe ImageWatermark. Les étapes suivantes vous permettent d'ajouter un filigrane d'image à vos documents protégés par mot de passe à l'aide de C#.

* Préparez l'[option de chargement][14] en utilisant le mot de passe existant.
* Chargez le fichier protégé à l'aide de la classe [Watermarker][15] et de l'**option de chargement**.
* Chargez le fichier image du filigrane à l'aide de la classe [ImageWatermark][16].
* Définissez l'apparence, l'alignement, les coordonnées, la rotation, l'opacité et d'autres propriétés du filigrane.
* Ajoutez un filigrane au document à l'aide de la méthode [Add()][17].
* Enregistrez le fichier filigrané à l'aide de la méthode [Save()][18].

Le code C# suivant insère un filigrane d'image dans le document MS Word DOCX protégé.

```
/*
 * Apply Image Watermark to document (PDF, Word, PPT, Excel, ...) using C#
 */
LoadOptions loadOptions = new LoadOptions();
loadOptions.Password = "P@$$w0rd";
string filePath = "path/document.docx";
using (Watermarker watermarker = new Watermarker(filePath, loadOptions))
{
    // Prepare Watermark Text and appearance. 
    ImageWatermark watermark = new ImageWatermark("watermark-logo.png")
    {
        Opacity = 0.7,
        X = 70,
        Y = 350
    };    
    // Add image watermark to document and save.
    watermarker.Add(watermark);
    watermarker.Save("path/watermark-document.docx");
}
```

## Obtenez une licence API gratuite

Vous pouvez utiliser les API gratuitement en [obtenant une licence temporaire][19].

## Conclusion

Pour conclure, nous avons appris à ajouter des filigranes de texte, ainsi que des filigranes d'image aux fichiers protégés par mot de passe dans les applications .NET utilisant C#. De plus, nous avons ajouté quelques personnalisations à l'apparence des filigranes lors de l'ajout.

De même, vous pouvez appliquer des filigranes aux **pages de documents** sélectives, aux **diapositives choisies des présentations** et aux **feuilles de classeurs** spécifiques dans vos documents. Voir les [articles connexes][20] pour plus de détails.

Pour en savoir plus sur [GroupDocs.Watermark pour .NET][21], consultez sa [documentation][22]. Pour toute question, contactez-nous via le [forum][23].

## Articles Liés {#releated-articles}

* [Rechercher et **Supprimer les filigranes** des documents en C#][24]
* [Filigrane **Feuilles Excel** en utilisant C#][25]
* [Filigrane **PDF** Fichiers utilisant C#][26]
* [Ajouter un filigrane aux **diapositives de présentation** à l'aide de C#][27]
* [Ajouter un filigrane à **Images** à l'aide de C#][28]




[1]: #watermarking-dotnet-api
[2]: #add-watermark-to-protected-files
[3]: #text-watermark-to-protected-file
[4]: #image-watermark-to-protected-file
[5]: https://products.groupdocs.com/watermark/
[6]: https://products.groupdocs.com/watermark/net/
[7]: https://downloads.groupdocs.com/watermark
[8]: https://www.nuget.org/packages/groupdocs.watermark
[9]: https://apireference.groupdocs.com/watermark/net/groupdocs.watermark.options/loadoptions
[10]: https://apireference.groupdocs.com/watermark/net/groupdocs.watermark/watermarker
[11]: https://apireference.groupdocs.com/watermark/net/groupdocs.watermark.watermarks/textwatermark
[12]: https://apireference.groupdocs.com/watermark/net/groupdocs.watermark/watermarker/methods/add/index
[13]: https://apireference.groupdocs.com/watermark/net/groupdocs.watermark/watermarker/methods/save/index
[14]: https://apireference.groupdocs.com/watermark/net/groupdocs.watermark.options/loadoptions
[15]: https://apireference.groupdocs.com/watermark/net/groupdocs.watermark/watermarker
[16]: https://apireference.groupdocs.com/watermark/net/groupdocs.watermark.watermarks/imagewatermark
[17]: https://apireference.groupdocs.com/watermark/net/groupdocs.watermark/watermarker/methods/add/index
[18]: https://apireference.groupdocs.com/watermark/net/groupdocs.watermark/watermarker/methods/save/index
[19]: https://purchase.groupdocs.com/temporary-license
[20]: #releated-articles
[21]: https://products.groupdocs.com/watermark/net/
[22]: https://docs.groupdocs.com/watermark/
[23]: https://forum.groupdocs.com/
[24]: https://blog.groupdocs.com/2020/11/27/find-and-remove-watermarks-from-documents-in-csharp/
[25]: https://blog.groupdocs.com/2021/11/04/watermark-excel-sheets-using-csharp/
[26]: https://blog.groupdocs.com/2021/07/27/watermark-pdf-files-using-csharp/
[27]: https://blog.groupdocs.com/2021/05/01/add-watermark-to-presentations-using-csharp/
[28]: https://blog.groupdocs.com/2020/12/20/add-watermark-to-images-using-csharp-dotnet/


