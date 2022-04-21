---
title: "Convertir des images en PDF en C#"
date: Wed, 19 May 2021 13:43:15 +0000
draft: false
url: /fr/2021/05/19/convert-images-to-pdf-in-csharp/
aliases:
- /2020/04/27/convertir-une-image-en-pdf-en-csharp/
- /2019/11/12/convert-to-pdf-using-groupdocs.conversion-for-.net-and-java/
- /2019/11/12/convertir-une-image-en-pdf-en-csharp/
author: 'Shoaib Khan'
summary: "An Image can be converted to PDF to assure that the image will display correctly across devices without being altered. PDF images are ideal for printing and for storing images online when intended to be downloaded. PDF can hold as many images in one document so can be printed easily or saved as a catalog. This article will guide you to programmatically convert images like JPG, GIF, WebP, PNG to PDF in C# using .NET API for document and image conversion."
tags: ['Convert Images to PDF in CSharp', 'Convert JPG to PDF in CSharp', 'CSharp Image Conversion', 'JPG to PDF in CSharp', 'PNG to PDF in CSharp']
categories: ['GroupDocs.Conversion Product Family']
---

Une image peut être convertie en PDF pour garantir que l'image s'affiche correctement sur tous les appareils sans être modifiée. Les images PDF sont idéales pour l'impression et le stockage d'images en ligne lorsqu'elles sont destinées à être téléchargées. Le PDF peut contenir autant d'images dans un seul document et peut donc être imprimé facilement ou enregistré en tant que catalogue. Cet article vous guidera pour convertir par programmation des images telles que JPG, GIF, WebP, PNG en PDF en C# à l'aide de l'API .NET pour la conversion de documents et d'images.

Les sujets suivants sont abordés brièvement ci-dessous :

* [API .NET de conversion d'images][2]
* [Convertir des images JPG en PDF][3]
* [Convertir des images PNG, GIF, BMP en PDF][4]
* [Conversion d'image en PDF avec options avancées][5]

## API .NET pour la conversion d'images {#image-conversion-dotnet-api}

J'utiliserai la bibliothèque [GroupDocs.Conversion for .NET][6] pour convertir des images au format PDF. La bibliothèque nous permet de convertir une longue liste de formats d'image en PDF. Certains de ceux pris en charge sont mentionnés ici. Pour la liste complète, visitez la [documentation][7].



{{< figure align=center src="images/convert-images-to-pdf-in-dotnet.jpg" alt="Convertir des images en PDF à l'aide de CSharp">}}


* IA
* BMP
* RDC
* DJVU
* GIF
* ICO
* JPEG, JPG, JP2
*PNG
* SVGZ
* TGA
* TIF, TIF
* WEBP

Outre les images, l'API permet aux développeurs de convertir des documents Word, des feuilles de calcul, des présentations, des livres électroniques, des documents Visio, des fichiers Microsoft Project, des fichiers PSD, des PDL, des messages électroniques et bien plus encore. De nombreux exemples sont disponibles sur [GitHub][8] pour le support mentionné.

Vous pouvez télécharger les DLL ou le programme d'installation MSI à partir de la [section des téléchargements][9] ou l'obtenir à partir de [NuGet][10].

```
Install-Package GroupDocs.Conversion
```

## Convertir JPG en PDF en C# {#jpg-to-pdf}



{{< figure align=center src="images/Sample.jpg" alt="Images JPEG">}}


Pour convertir simplement vos images JPG au format PDF, vous pouvez suivre les étapes ci-dessous :

* Chargez le fichier JPG en utilisant la classe [Converter][11].
* Instancier la classe [PdfConvertOptions][12].
* Appelez la méthode [Convert][13] pour convertir l'image JPG en PDF et enregistrez-la sur le chemin fourni.

Le code source suivant montre comment convertir une image JPG en PDF en C#.

```
// Convertir une image JPG en PDF en C#
using (Converter converter = new Converter("image.jpg"))
{
    PdfConvertOptions options = new PdfConvertOptions();
    converter.Convert("imageToPdf.pdf", options);
}
```

## Convertir des images PNG en PDF en C# {#png-gif-bmp-to-pdf}

Si vous souhaitez convertir une image PNG, il n'y aura aucune différence dans le code. Les étapes suivantes nous permettent de convertir une image PNG en PDF en utilisant C#.

* Chargez le fichier image PNG à l'aide de la classe [Converter][14].
* Instancier la classe [PdfConvertOptions][15].
* Appelez la méthode [Convert][16] pour convertir l'image fournie en PDF et enregistrez-la sur le chemin fourni.

Le code suivant montre comment convertir une image PNG en PDF à l'aide de C#.

```
// Convertissez n'importe quelle image en PDF en C#. PNG, WebP, JPG, GIF, TGA et bien d'autres ...
using (Converter converter = new Converter("image.png"))
{
    PdfConvertOptions options = new PdfConvertOptions();
    converter.Convert("imageToPdf.pdf", options);
}
```

## Convertir n'importe quelle image en PDF

De même, il vous suffit de fournir votre JPG, PNG, GIF, WebP ou toute autre image à la classe **Converter** lors du chargement. En outre, il existe de nombreuses [options de conversion][17] lors de la conversion au format PDF.

## Convertir des images en PDF en C# avec des options avancées {#advance-conversion}



{{< figure align=center src="images/AdvancedConversion-300x238.jpg" alt="Document de sortie après conversion">}}


GroupDocs.Conversion fournit [PdfConvertOptions][18] pour nous permettre de contrôler les résultats de la conversion lors de la conversion d'une image en PDF. Certaines des options supplémentaires sont :

* [Largeur][19] - Largeur de l'image après conversion.
* [Hauteur][20] - Hauteur de l'image après conversion.
* [MarginTop][21] - Marge supérieure de la page après conversion.
* [MarginBottom][22] - Marge inférieure de la page après conversion.
* [MarginLeft][23] - Marge gauche de la page après conversion.
* [MarginRight][24] - Marge droite de la page après conversion.
* [Rotation][25] - Rotation des pages. Les options disponibles sont : Aucun, On90, On180, On270

L'exemple de code C# suivant utilise ces options supplémentaires et convertit une image au format PDF. Il définit la hauteur et la largeur de l'image résultante, définit les marges de la page et fait également pivoter l'image à 180 degrés.

```
// Convertissez des images JPG, PNG ou d'autres images en PDF en C#. Redimensionnez, définissez les marges ou faites pivoter les images.
using (Converter converter = new Converter("image.jpg"))
{
    PdfConvertOptions options = new PdfConvertOptions
    {
        Width = 233,
        Height = 175,
        MarginTop = 20,
        MarginBottom = 20,
        MarginLeft = 20,
        MarginRight = 20,
        Rotate = Rotation.On180
    };
    converter.Convert("imageToPdfAdv.pdf", options);
}
```

## Obtenez une licence API gratuite

Vous pouvez utiliser l'API sans limitation d'évaluation en demandant une [licence temporaire gratuite][26].

## Conclusion

Pour conclure, nous avons appris à convertir des images au format PDF en utilisant l'API de conversion d'image pour .NET. Plus précisément, nous avons expliqué comment convertir par programmation des images JPG, PNG, WebP et d'autres images en PDF en C#. Vous pouvez en savoir plus sur l'API de conversion d'images à l'aide de la [documentation.][27] Pour toute question, contactez-nous via le [forum][28].

## Voir également

* [Convertir des feuilles de calcul Excel en PDF en C#][29]
* [Convertir des dessins CAO en PDF en C#][30]
* [](https://blog.groupdocs.com/2021/04/21/convert-images-to-pdf-in-java/)[Convertir un fichier EML ou MSG en PDF en C#][31]







[1]: https://blog.groupdocs.com/2021/05/19/convert-images-to-pdf-in-csharp/
[2]: #image-conversion-dotnet-api
[3]: #jpg-to-pdf
[4]: #png-gif-bmp-to-pdf
[5]: #advance-conversion
[6]: https://products.groupdocs.com/conversion/net
[7]: https://docs.groupdocs.com/conversion/net/supported-document-formats/#SupportedDocumentFormats-ConversionfromImageFiletoOtherDocumentformats
[8]: https://github.com/groupdocs-conversion
[9]: https://downloads.groupdocs.com/conversion/net
[10]: https://www.nuget.org/packages/GroupDocs.Conversion/
[11]: https://apireference.groupdocs.com/net/conversion/groupdocs.conversion/converter
[12]: https://apireference.groupdocs.com/net/conversion/groupdocs.conversion.options.convert/pdfconvertoptions
[13]: https://apireference.groupdocs.com/conversion/net/groupdocs.conversion/converter/methods/convert/index
[14]: https://apireference.groupdocs.com/net/conversion/groupdocs.conversion/converter
[15]: https://apireference.groupdocs.com/net/conversion/groupdocs.conversion.options.convert/pdfconvertoptions
[16]: https://apireference.groupdocs.com/conversion/net/groupdocs.conversion/converter/methods/convert/index
[17]: https://docs.groupdocs.com/conversion/net/convert-to-pdf-with-advanced-options/
[18]: https://apireference.groupdocs.com/net/conversion/groupdocs.conversion.options.convert/pdfconvertoptions
[19]: https://apireference.groupdocs.com/net/conversion/groupdocs.conversion.options.convert/pdfconvertoptions/properties/width
[20]: https://apireference.groupdocs.com/net/conversion/groupdocs.conversion.options.convert/pdfconvertoptions/properties/height
[21]: https://apireference.groupdocs.com/net/conversion/groupdocs.conversion.options.convert/pdfconvertoptions/properties/margintop
[22]: https://apireference.groupdocs.com/net/conversion/groupdocs.conversion.options.convert/pdfconvertoptions/properties/marginbottom
[23]: https://apireference.groupdocs.com/net/conversion/groupdocs.conversion.options.convert/pdfconvertoptions/properties/marginleft
[24]: https://apireference.groupdocs.com/net/conversion/groupdocs.conversion.options.convert/pdfconvertoptions/properties/marginright
[25]: https://apireference.groupdocs.com/net/conversion/groupdocs.conversion.options.convert/pdfconvertoptions/properties/rotate
[26]: https://purchase.groupdocs.com/temporary-license
[27]: https://docs.groupdocs.com/conversion
[28]: https://forum.groupdocs.com/
[29]: https://blog.groupdocs.com/2021/11/14/convert-excel-spreadsheets-to-pdf-using-csharp/
[30]: https://blog.groupdocs.com/2020/11/08/convert-cad-drawings-to-pdf-in-csharp/
[31]: https://blog.groupdocs.com/2019/12/06/convert-eml-or-msg-file-to-pdf-in-csharp/


