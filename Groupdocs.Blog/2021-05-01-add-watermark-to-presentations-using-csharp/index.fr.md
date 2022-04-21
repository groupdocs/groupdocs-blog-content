---
title: "Ajouter un filigrane aux diapositives de présentation à l'aide de C#"
date: Sat, 01 May 2021 04:00:00 +0000
draft: false
url: /fr/2021/05/01/add-watermark-to-presentations-using-csharp/
author: 'Shoaib Khan'
summary: "Watermarks are normally used to protect the documents from any unauthorized use. To protect your presentations and to claim ownership, today we will learn how to programmatically add text and image watermarks to the Microsoft PowerPoint presentations within .NET applications using C#. In a separate article, we have seen [applying watermarks to images in C#][1]."
tags: ['add watermark in csharp', 'add watermark to presentations in csharp', 'how to add watermark in csharp']
categories: ['GroupDocs.Watermark Product Family']
---



{{< figure align=center src="images/apply-watermarks-to-presentations-in-csharp.jpg" alt="Appliquer un filigrane à la présentation en C #">}}


Les filigranes sont normalement utilisés pour protéger les documents de toute utilisation non autorisée. Pour protéger vos présentations et revendiquer la propriété, nous allons apprendre aujourd'hui comment ajouter par programmation des filigranes de texte et d'image aux présentations Microsoft PowerPoint dans les applications .NET utilisant C#. Dans un article séparé, nous avons vu [appliquer des filigranes aux images en C#][3].

Passons rapidement à apprendre séparément, comment nous pouvons appliquer des filigranes basés sur du texte et des images à l'ensemble de la présentation ou à une diapositive spécifique à l'aide de l'[API de filigrane pour les applications .NET][4].

* [Ajouter des filigranes de texte aux diapositives de présentation][5].
* [Ajouter des filigranes d'image aux diapositives de présentation.][6]

## API de filigrane pour .NET

[GroupDocs.Watermark pour .NET][7] est une API de filigrane qui permet d'ajouter des filigranes de texte et d'image aux présentations et à de nombreux autres documents de différents formats de fichiers dans les applications .NET. Il fournit des méthodes de filigrane qui ajoutent des filigranes difficiles à supprimer automatiquement par d'autres outils.

Outre les présentations, l'API prend en charge l'ajout, la suppression et l'extraction de filigranes à partir de documents de traitement de texte, de feuilles de calcul, de messages électroniques, de fichiers PDF, d'images, de dessins Visio et de nombreux autres formats. Parmi les formats de fichiers de présentation, il prend en charge PPT, PPTX, PPS, PPTM, PPSX et autres. À partir de la [documentation][8], vous pouvez vérifier davantage les fonctionnalités et les [formats de fichiers pris en charge][9].

Vous pouvez télécharger les DLL ou le programme d'installation MSI à partir de la [section des téléchargements][10] ou l'obtenir à partir de [NuGet][11].

```
Install-Package GroupDocs.Watermark
```

## Ajouter du texte aux diapositives en tant que filigrane à l'aide de C# {#text-watermark-to-slides-in-csharp}

L'API fournit des personnalisations pour ajouter du texte aux présentations en filigrane. Les étapes suivantes vous expliquent comment appliquer un filigrane sur les fichiers de présentation dans l'application .NET.

* Chargez la présentation à l'aide de [Filigrane][12].
* Définissez le texte et le style du filigrane à l'aide de [TextWatermark][13].
* Définissez d'autres propriétés telles que la rotation, la taille, l'opacité, la couleur et la position.
* Fournir l'index de la diapositive pour appliquer le filigrane.
* Ajoutez le filigrane de texte formaté à l'aide de la méthode [Ajouter][14].
* Enregistrez la présentation en filigrane à l'aide de la méthode [Enregistrer][15].

L'exemple de code suivant ajoute une étiquette de texte à la présentation PPTX en tant que filigrane sur la première diapositive avec rotation à l'aide de C#.

```
// Ajouter un filigrane de texte aux diapositives de présentation en C # à l'aide de l'API .NET
using (Watermarker watermarker = new Watermarker("presentation.pptx"))
{
    // Set watermark text, coordinates and formatting
    TextWatermark watermark = new TextWatermark("Watermark", new Font("Arial", 36))
    {
        RotateAngle = -45,
        X = 100,
        Y = 100,
        Height = 400,
        Width = 400,
        Opacity = .2,
        ForegroundColor = Color.DarkBlue,
        HorizontalAlignment = HorizontalAlignment.Center,
        VerticalAlignment = VerticalAlignment.Center
    };
    // Apply Watermark to only first slide of the presentation
    PresentationWatermarkSlideOptions textWatermarkOptions = new PresentationWatermarkSlideOptions();
    textWatermarkOptions.SlideIndex = 0;
    
    // Add watermark to presentation and save.
    watermarker.Add(watermark, textWatermarkOptions);
    watermarker.Save("text-watermarked-presentation.pptx");
}
```

Si vous ne fournissez pas d'index de diapositive, le filigrane sera ajouté sur toutes les diapositives par défaut. Le code ci-dessus montre comment mentionner l'index des diapositives, cependant, je vous ai montré la sortie avec un filigrane de texte sur toutes les diapositives de la présentation PPTX.



{{< figure align=center src="images/text-watermark-to-slide.png" alt="Texte en filigrane sur la diapositive de présentation">}}


## Insérer un filigrane d'image dans les diapositives à l'aide de C# {#image-watermark-to-slides-in-csharp}

De même, vous pouvez ajouter des images sur les fichiers de présentation en filigrane. Il vous suffit d'utiliser la classe [ImageWatermark][16] au lieu de TextWatermark. Voici les étapes pour ajouter un filigrane d'image aux diapositives de présentation dans vos applications .NET.

* Chargez la présentation à l'aide de [Filigrane][17].
* Chargez le fichier image qui sera utilisé comme filigrane à l'aide de [ImageWatermark][18].
* Définissez les propriétés du filigrane de l'image telles que la rotation, la taille, l'opacité, la couleur et la position.
* Définissez l'index de diapositive sur lequel appliquer le filigrane.
* Ajoutez le filigrane de l'image à la présentation à l'aide de la méthode [Ajouter][19].
* Enregistrez la présentation en filigrane à l'aide de la méthode [Enregistrer][20].

L'exemple de code suivant ajoute une image à la présentation PPTX en tant que filigrane sur la deuxième diapositive à l'aide de C#.

```
// Ajouter un filigrane d'image aux diapositives de présentation en C # à l'aide de l'API .NET
using (Watermarker watermarker = new Watermarker("presentation.pptx"))
{
    // Set watermark image, coordinates and formatting
    ImageWatermark imageWatermark = new ImageWatermark("watermark-image.png");
    imageWatermark.Opacity = .7;
    imageWatermark.X = 80;
    imageWatermark.Y = 120;
    
    // Apply Watermark to only second slide of the presentation
    PresentationWatermarkSlideOptions ImageWatermarkOptions = new PresentationWatermarkSlideOptions();
    ImageWatermarkOptions.SlideIndex = 1;

    // Add watermark to presentation and save.
    watermarker.Add(imageWatermark, ImageWatermarkOptions);
    watermarker.Save("image-watermarked-presentation.pptx");
}
```

Ce qui suit est la sortie du code ci-dessus avec un filigrane d'image uniquement sur la deuxième diapositive de la présentation PPTX.



{{< figure align=center src="images/image-watermark-to-slide.jpg" alt="Filigrane d'image sur la diapositive de présentation">}}


## Conclusion

En résumé, vous avez appris à ajouter des filigranes de texte et d'image à vos diapositives de présentation à l'aide de C#. Vous pouvez maintenant créer votre propre application .NET qui prend en charge le texte ainsi que les filigranes d'image pour les fichiers de présentation et les diapositives spécifiques de la présentation. Consultez la documentation pour [appliquer des filigranes à divers autres formats de documents][21].

Vous pouvez avoir une [Licence temporaire gratuite][22] pour découvrir tous les aspects du produit. L'assistance gratuite se fera un plaisir de vous sortir de toute confusion et [résolvez vos questions liées aux filigranes sur le forum][23].

## Voir également

* [Ajouter un filigrane aux images à l'aide de C #][24]
* [Insérer un filigrane dans les classeurs Excel à l'aide de C #][25]
* [Rechercher et supprimer des filigranes de documents en C#][26]







[1]: https://blog.groupdocs.com/2020/12/20/add-watermark-to-images-using-csharp-dotnet/
[2]: https://blog.groupdocs.com/2021/05/01/add-watermark-to-presentations-using-csharp/
[3]: https://blog.groupdocs.com/2020/12/20/add-watermark-to-images-using-csharp-dotnet/
[4]: https://products.groupdocs.com/watermark/net
[5]: #text-watermark-to-slides-in-csharp
[6]: #image-watermark-to-slides-in-csharp
[7]: https://products.groupdocs.com/watermark/net
[8]: https://docs.groupdocs.com/watermark/net/
[9]: https://docs.groupdocs.com/watermark/net/supported-document-formats/
[10]: https://downloads.groupdocs.com/watermark/net
[11]: https://www.nuget.org/packages/GroupDocs.Watermark/
[12]: https://apireference.groupdocs.com/watermark/net/groupdocs.watermark/watermarker
[13]: https://apireference.groupdocs.com/watermark/net/groupdocs.watermark.watermarks/textwatermark
[14]: https://apireference.groupdocs.com/watermark/net/groupdocs.watermark/watermarker/methods/add/index
[15]: https://apireference.groupdocs.com/watermark/net/groupdocs.watermark/watermarker/methods/save/index
[16]: https://apireference.groupdocs.com/watermark/net/groupdocs.watermark.watermarks/imagewatermark
[17]: https://apireference.groupdocs.com/watermark/net/groupdocs.watermark/watermarker
[18]: https://apireference.groupdocs.com/watermark/net/groupdocs.watermark.watermarks/imagewatermark
[19]: https://apireference.groupdocs.com/watermark/net/groupdocs.watermark/watermarker/methods/add/index
[20]: https://apireference.groupdocs.com/watermark/net/groupdocs.watermark/watermarker/methods/save/index
[21]: https://docs.groupdocs.com/watermark/net/adding-watermarks/
[22]: https://purchase.groupdocs.com/temporary-license
[23]: https://forum.groupdocs.com/c/watermark
[24]: https://blog.groupdocs.com/2020/12/20/add-watermark-to-images-using-csharp-dotnet/
[25]: https://blog.groupdocs.com/2021/11/04/watermark-excel-sheets-using-csharp/
[26]: https://blog.groupdocs.com/2020/11/27/find-and-remove-watermarks-from-documents-in-csharp/


