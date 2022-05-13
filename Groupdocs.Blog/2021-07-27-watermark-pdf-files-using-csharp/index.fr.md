---
title: "Filigraner des fichiers PDF avec C#"
date: Tue, 27 Jul 2021 14:34:00 +0000
draft: false
url: /fr/2021/07/27/watermark-pdf-files-using-csharp/
author: 'Shoaib Khan'
summary: "Pour protéger vos fichiers de toute utilisation illégale ou pour apposer une image de marque sur vos documents, des filigranes peuvent être utilisés . Dans cet article, vous apprendrez à ajouter par programme les filigranes aux fichiers PDF à l'aide de C#. Nous examinerons séparément l'ajout de filigranes de texte et d'image en filigrane."
tags: ['dotNET Watermarking API', 'Image Watermark in C#', 'Watermark in C#', 'Watermark PDF in C#', 'Watermark Text in C#']
categories: ['GroupDocs.Watermark Product Family']
---



{{< figure align=center src="images/add-watermarks-to-pdf-in-csharp.jpg" alt="Appliquer un filigrane au PDF dans CSharp">}}


Pour protéger vos fichiers de toute utilisation illégale ou pour appliquer une image de marque à vos documents, des filigranes peuvent être utilisés. Dans cet article, vous apprendrez à ajouter par programme les filigranes aux fichiers PDF à l'aide de C#. Nous examinerons séparément l'ajout de filigranes de texte et d'image en filigrane.

Les sujets suivants sont traités ci-dessous :

* [API de filigrane .NET][1]
* [Appliquer un filigrane de texte au PDF][2]
* [Appliquer un filigrane d'image au PDF][3]

## API de filigrane .NET pour les fichiers PDF {#dotnet-watermarking-api}

[GroupDocs.Watermark][4] fournit une API de filigrane .NET qui permet de travailler avec du texte ainsi que des filigranes d'image dans les fichiers PDF. Outre les fichiers PDF, l'API permet d'ajouter, de supprimer et d'extraire des filigranes pour les documents de traitement de texte, les feuilles de calcul, les présentations, les messages électroniques, les images, les dessins Visio et de nombreux autres formats. À partir de la [documentation][5], vous pouvez vérifier davantage les fonctionnalités et les [formats de fichiers pris en charge][6].

Vous pouvez télécharger le programme d'installation **DLLs** ou **MSI** à partir de la [section téléchargements][7] ou installer l'API dans votre application .NET via [NuGet][8].

```
PM> Install-Package GroupDocs.Watermark
```

## Ajouter un filigrane de texte au PDF à l'aide de C # {#text-watermark-to-pdf}

Le texte du filigrane peut être appliqué aux fichiers PDF sur toutes les pages ou sur n'importe quelle page sélective. Il peut être ajouté en insérant le texte formaté à la position requise.

Les étapes suivantes montrent comment ajouter du texte en filigrane aux fichiers PDF.

* Chargez le document PDF à l'aide de la classe [Watermarker][9].
* Initialisez le filigrane de texte à l'aide de la classe [TextWatermark][10].
* Définissez l'apparence en ajoutant l'angle de rotation, l'alignement, l'opacité, les couleurs de premier plan et d'arrière-plan, etc.
* Définissez l'index de la page ciblée (_facultatif_). Si vous ne définissez pas l'index, le filigrane sera appliqué à toutes les pages par défaut.
* Ajoutez le filigrane de texte au fichier PDF chargé.
* Enregistrez le fichier de mise à jour avec filigrane en utilisant la méthode [Enregistrer][11] appropriée.

Le code source montre comment ajouter un filigrane de texte aux fichiers PDF à l'aide de C#.

```
// Ajouter du texte en filigrane à la ou aux pages du fichier PDF à l'aide de C #
PdfLoadOptions loadOptions = new PdfLoadOptions();
using (Watermarker watermarker = new Watermarker("path/document.pdf", loadOptions))
{
    TextWatermark textWatermark = new TextWatermark("Watermark", new Font("Arial", 80))
    {
        RotateAngle = -45,
        Opacity = .3,
        ForegroundColor = Color.DarkBlue,
        HorizontalAlignment = HorizontalAlignment.Center,
        VerticalAlignment = VerticalAlignment.Center
    };
    // If you want to add watermark text to any specific page, provde Page Index.
    /*
    PdfArtifactWatermarkOptions textWatermarkOptions = new PdfArtifactWatermarkOptions();
    textWatermarkOptions.PageIndex = 0;
    */
    watermarker.Add(textWatermark, textWatermarkOptions);
    watermarker.Save("path/text-watermark.pdf");
}
```

La sortie du code source ci-dessus affiche le filigrane de texte sur les deux pages du fichier PDF donné.



{{< figure align=center src="images/add-text-watermark-to-pdf-in-csharp-1024x646.png" alt="Ajouter un filigrane de texte au PDF à l'aide de C #">}}


## Ajouter un filigrane d'image au PDF à l'aide de C # {#image-watermark-to-pdf}

De même, vous pouvez ajouter des images au fichier PDF car nous venons d'ajouter le filigrane de texte.

Les étapes suivantes montrent comment ajouter une image aux fichiers PDF sous forme de filigranes.

* Chargez le document PDF à l'aide de la classe [Watermarker][12].
* Initialisez le filigrane de l'image à l'aide de la classe [ImageWatermark][13].
* Définissez l'apparence en ajustant l'alignement, la rotation, l'opacité et d'autres options.
* Définissez l'index de la page ciblée. (Optionnel)
* Ajoutez le filigrane de l'image au fichier PDF.
* Enregistrez le fichier filigrané à l'aide de la méthode [Enregistrer][14] appropriée.

Le code source montre comment ajouter un filigrane d'image aux fichiers PDF à l'aide de C#.

```
// Ajouter une image de filigrane à la ou aux pages du fichier PDF à l'aide de C# 
PdfLoadOptions loadOptions = new PdfLoadOptions();
using (Watermarker watermarker = new Watermarker("path/document.pdf", loadOptions))
{
    ImageWatermark imageWatermark = new ImageWatermark("watermark-logo.png")
    {
        Opacity = 0.7,
        X = 70,
        Y = 350
    };
    // Adding image watermark to the second page  
    PdfArtifactWatermarkOptions imageWatermarkOptions = new PdfArtifactWatermarkOptions();
    imageWatermarkOptions.PageIndex = 1;
    watermarker.Add(imageWatermark, imageWatermarkOptions);

    watermarker.Save("path/image-watermark.pdf");
}
```

La sortie du code source ci-dessus montre le filigrane de l'image sur la deuxième page du fichier PDF donné.



{{< figure align=center src="images/add-image-watermark-to-pdf-in-csharp-1024x625.png" alt="Filigrane d'image au format PDF à l'aide de C#">}}


## Obtenez une licence API gratuite

Vous pouvez [obtenir une licence temporaire gratuite][15] pour utiliser l'API sans les limitations d'évaluation.

## Conclusion

Pour conclure, vous avez appris à ajouter des filigranes aux fichiers PDF à l'aide de C#. Nous avons vu ajouter du texte en filigrane ainsi que des images sur des fichiers PDF en tant que filigranes. Pour plus de détails ou en savoir plus sur l'API, consultez la [documentation][16]. Pour toute question, contactez-nous via le [forum][17].

## Voir également

* [Ajouter un filigrane aux images à l'aide de C #][18]
* [Ajouter un filigrane à la présentation et aux diapositives à l'aide de C #][19]
* [Feuilles Excel en filigrane à l'aide de C #][20]
* [Protection par mot de passe pour verrouiller et déverrouiller les fichiers PDF en C#][21]







[1]: #dotnet-watermarking-api
[2]: #text-watermark-to-pdf
[3]: #image-watermark-to-pdf
[4]: https://docs.groupdocs.com/watermark
[5]: https://docs.groupdocs.com/watermark/net
[6]: https://docs.groupdocs.com/watermark/net/supported-document-formats/
[7]: https://downloads.groupdocs.com/watermark
[8]: https://www.nuget.org/packages/groupdocs.watermark
[9]: https://apireference.groupdocs.com/watermark/net/groupdocs.watermark/watermarker
[10]: https://apireference.groupdocs.com/watermark/net/groupdocs.watermark.watermarks/textwatermark
[11]: https://apireference.groupdocs.com/watermark/net/groupdocs.watermark/watermarker/methods/save/index
[12]: https://apireference.groupdocs.com/watermark/net/groupdocs.watermark/watermarker
[13]: https://apireference.groupdocs.com/watermark/net/groupdocs.watermark.watermarks/imagewatermark
[14]: https://apireference.groupdocs.com/watermark/net/groupdocs.watermark/watermarker/methods/save/index
[15]: https://purchase.groupdocs.com/temporary-license
[16]: https://docs.groupdocs.com/watermark/
[17]: https://forum.groupdocs.com/
[18]: https://blog.groupdocs.com/2020/12/20/add-watermark-to-images-using-csharp-dotnet/
[19]: https://blog.groupdocs.com/2021/05/01/add-watermark-to-presentations-using-csharp/
[20]: https://blog.groupdocs.com/2021/11/04/watermark-excel-sheets-using-csharp/
[21]: https://blog.groupdocs.com/2021/11/17/password-protection-to-pdf-files-in-csharp/


