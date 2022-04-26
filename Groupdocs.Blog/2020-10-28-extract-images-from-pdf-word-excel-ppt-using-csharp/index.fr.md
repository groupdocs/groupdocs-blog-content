---
title: "Extraire des images de documents à l'aide de C #"
date: Wed, 28 Oct 2020 18:27:00 +0000
draft: false
url: /fr/2020/10/28/extraire-images-du-pdf-word-excel-ppt-en-utilisant-csharp/
author: 'Shoaib Khan'
summary: "Dans cet article, nous allons apprendre à **extraire par programme des images de documents PDF, Excel, PowerPoint et Word dans une application C#** à l'aide de l'API .NET d'analyse de documents. [GroupDocs.Parser for .NET][1] est une API .NET d'analyse de documents et d'extraction de données. Il prend en charge l'**analyse de documents** et l'**extraction d'images, de texte** et de **métadonnées** à partir de **documents de traitement de texte**, de **feuilles de calcul**, de **présentations, d'archives** et **documents par e-mail**."
tags: ['csharp parser', 'Dcoument Parsing API', 'extract images from PDF in csharp', 'extract images in csharp', 'Image extractor']
categories: ['GroupDocs.Parser Product Family']
---

Dans le [article précédent][2], nous avons expliqué comment extraire des images de documents en Java. Aujourd'hui, nous chercherons à atteindre le même objectif en utilisant C#. Pas de soucis si vous n'avez pas visité le dernier message. Dans cet article, nous allons apprendre à **extraire par programme des images de documents PDF, Excel, PowerPoint et Word dans une application C#** à l'aide de l'API .NET d'analyse de documents.



{{< figure align=center src="images/extract-images-from-documents-in-csharp-dotnet.png" alt="Extraire des images de documents dans .NET">}}


Les sujets suivants seront abordés ici :

* [API .NET d'extraction d'images, de texte et de métadonnées][3]
* [Extraction d'images à partir de documents PDF][4]
* [Extraire des images de documents Word, Excel, PowerPoint][5]
* [Extraire l'image d'une page spécifique][6]
* [Formats pris en charge pour l'extraction d'images][7]

## API .NET d'extraction d'images, de texte et de métadonnées {#image-extraction-dotnet-api}



{{< figure align=center src="images/groupdocs-parser-net.png" alt="Analyser des documents et extraire des données dans .NET">}}


[GroupDocs.Parser for .NET][8] est une API .NET d'analyse de documents et d'extraction de données. Il prend en charge l'**analyse de documents** et l'**extraction d'images, de texte** et de **métadonnées** à partir de **documents de traitement de texte**, de **feuilles de calcul**, de **présentations, d'archives** et **documents par e-mail**. À la fin de l'article, les formats de document sont [mentionnés][9] qui sont pris en charge par l'API pour l'extraction d'images.

Dans cet article, nous utiliserons cette API, je vous recommande donc de [télécharger][10] ses binaires ou d'installer l'API à partir de [NuGet][11] pour préparer l'environnement.

## Extraire des images de documents PDF en C# {#extract-images-from-pdf-in-csharp}



{{< figure align=center src="images/PDF-with-Images.png" alt="Document PDF pour extraire des images">}}


Vous pouvez facilement récupérer toutes les images de n'importe quel document PDF en suivant ces étapes simples.

1. Instanciez l'objet de classe [Parser][12] avec le document source.
2. Appelez la méthode [GetImages][13] de la classe **Parser** pour obtenir la collection de toutes les images dans les objets [PageImageArea][14].
3. Itérer sur **PageImageArea** pour obtenir chaque image.
4. Enregistrez les images sur le disque en utilisant la méthode [Save][15] de **PageImageArea**.

Les images extraites peuvent être enregistrées aux formats **BMP**, **GIF**, **JPEG**, **PNG** et **WebP**. Le code complet est présenté ci-dessous pour illustrer l'ensemble des étapes.

```
// Extraire des images de Word, Excel, PPT, PDF en C# à l'aide de GroupDocs.Parser pour .NET
using (Parser parser = new Parser("path/document.pdf"))
{
    IEnumerable<PageImageArea> images = parser.GetImages();
    ImageOptions options = new ImageOptions(ImageFormat.Png);
    int imageNumber = 0;
    // Iterate over retrieved images
    foreach (PageImageArea image in images)
    {
        // Save Image and print page index, rectangle and image type:
        Console.WriteLine(string.Format("Page: {0}, R: {1}, Type: {2}", image.Page.Index, image.Rectangle, image.FileType));
        image.Save("imageFilePath/image-" + imageNumber.ToString() + ".png", options);
        imageNumber++;
    }
}
```



{{< figure align=center src="images/Extracted-Images-from-PDF-using-GroupDocs.Parser-for-Java.png" alt="Images extraites du document à l'aide de GroupDocs.Parser">}}


## Extraire des images de fichiers Word, Excel, PowerPoint en C# {#extract-images-from-word-excel-ppt-in-csharp}

Non limité au seul format PDF, nous pouvons extraire toutes les images des documents de traitement de texte, des tableurs, des présentations, avec la base de code inchangée. Changez simplement le chemin du document source avec l'extension de fichier, votre document sera analysé pour extraire et enregistrer toutes les images sur le disque.

```
using (Parser parser = new Parser("path/document.docx")) // Word Document
// using (Parser parser = new Parser("path/document.xlsx")) // Excel Spreadhseet
// using (Parser parser = new Parser("path/document.pptx")) // Presentation
// using (Parser parser = new Parser("path/document.pdf")) // PDF Document
```

## Extraction d'image à partir d'une page de document spécifique en C# {#extract-images-from-specific-page-in-csharp}

Si vous souhaitez extraire des images d'une page spécifique du document, cela peut être fait facilement en utilisant les étapes ci-dessous et le code C#.

* Obtenez les informations sur le document à l'aide de la méthode [GetDocumentInfo][16].
* À partir des informations sur le document, retirez le total [PageCount][17] et d'autres informations.
* Utilisez la méthode [GetImages(pageIndex)][18] et transmettez-lui l'index de votre page cible.
* Pour enregistrer les images récupérées, parcourez la collection d'images et enregistrez l'image individuelle à l'aide de la méthode [Enregistrer][19].

```
// Extraire des images d'une page spécifique de Word, Excel, PowerPoint, PDF en C # à l'aide de GroupDocs.Parser pour .NET
using (Parser parser = new Parser("path/document.pdf"))
{
    // Get the document info
    IDocumentInfo documentInfo = parser.GetDocumentInfo();
    ImageOptions options = new ImageOptions(ImageFormat.Png);
    int imageNumber = 0;

    // Iterate over pages
    for (int pageIndex = 0; pageIndex < documentInfo.PageCount; pageIndex++)
    {
        // Print a page number 
        Console.WriteLine(string.Format("Page {0}/{1}", pageIndex + 1, documentInfo.PageCount));
        // Iterate over images. Ignoring null-check in the example
        foreach (PageImageArea image in parser.GetImages(pageIndex))
        {
            // Print a rectangle and image type
            Console.WriteLine(string.Format("R: {0}, Text: {1}", image.Rectangle, image.FileType));
            image.Save("imageFilePath/image-" + imageNumber.ToString() + ".png", options);
            imageNumber++;
        }
    }
}
```

## Formats pris en charge pour l'extraction d'images en C# {#supported-formats-for-image-extraction}

Voici les formats de document pris en charge par l'API _GroupDocs.Parser pour .NET_ pour l'extraction d'images.

<figure class="wp-block-table is-style-stripes"><table><tbody><tr><td>**Documents de traitement de texte</td><td> DOC, DOCX, DOCM, POINT, DOTX, DOTM, ODT, OTT, RTF</td></tr><tr><td> <strong>Feuilles de calcul</strong></td><td> XLS, XLSX, XLSM, XLSB, XLT, XLTX, XLTM, ODS, OTS, XLA, XLAM, NUMÉROS</td></tr><tr><td> <strong>Présentations</strong></td><td> PPT, PPTX, PPTM, PPS, PPSX, PPSM, POT, POTX, POTM, ODP, OTP</td></tr><tr><td> <strong>Documents portables</strong></td><td> PDF</td></tr><tr><td> <strong>E-mails</strong></td><td> EML, EMLX, MSG</td></tr><tr><td> <strong>Les archives**</strong></td><td> ZIP *: FRANÇAIS</td></tr></tbody></table></figure>

## En savoir plus sur GroupDocs.Parser

* [Documents][20]
* [Exemples de code source][21]
* [Référence API][22]
* Famille ([API sur site][23]| [API Cloud][24] | [Application en ligne gratuite][25]

Parlons un peu plus @ [Forum d'assistance gratuit][26]

## Articles Liés

* [Extraire des images de documents à l'aide de Java][27]
* [Extraire des images de documents sur le cloud à l'aide de Python][28]







[1]: https://products.groupdocs.com/parser/net
[2]: https://blog.groupdocs.com/2020/10/27/extract-images-from-pdf-word-excel-ppt-using-java/
[3]: #image-extraction-dotnet-api
[4]: #extract-images-from-pdf-in-csharp
[5]: #extract-images-from-word-excel-ppt-in-csharp
[6]: #extract-images-from-specific-page-in-csharp
[7]: #supported-formats-for-image-extraction
[8]: https://products.groupdocs.com/parser/net
[9]: #supported-formats-for-image-extraction
[10]: https://downloads.groupdocs.com/parser/net
[11]: https://www.nuget.org/packages/GroupDocs.Parser/
[12]: https://apireference.groupdocs.com/net/parser/groupdocs.parser/parser
[13]: https://apireference.groupdocs.com/net/parser/groupdocs.parser/parser/methods/getimages
[14]: https://apireference.groupdocs.com/net/parser/groupdocs.parser.data/pageimagearea
[15]: https://apireference.groupdocs.com/parser/net/groupdocs.parser.data.pageimagearea/save/methods/1
[16]: https://apireference.groupdocs.com/parser/net/groupdocs.parser/parser/methods/getdocumentinfo
[17]: https://apireference.groupdocs.com/parser/net/groupdocs.parser.options/idocumentinfo/properties/pagecount
[18]: https://apireference.groupdocs.com/parser/net/groupdocs.parser.parser/getimages/methods/2
[19]: https://apireference.groupdocs.com/parser/net/groupdocs.parser.data.pageimagearea/save/methods/1
[20]: https://docs.groupdocs.com/parser/
[21]: https://github.com/groupdocs-parser/
[22]: https://apireference.groupdocs.com/parser
[23]: https://products.groupdocs.com/parser/family
[24]: https://products.groupdocs.cloud/parser/family
[25]: https://products.groupdocs.app/parser)
[26]: https://forum.groupdocs.com/c/parser
[27]: https://blog.groupdocs.com/2020/10/27/extract-images-from-pdf-word-excel-ppt-using-java/
[28]: https://blog.groupdocs.cloud/2020/10/25/extract-images-from-word-excel-ppt-pdf-using-python/


