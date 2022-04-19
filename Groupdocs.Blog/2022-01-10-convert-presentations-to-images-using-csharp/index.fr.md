---
title: "Convertir des présentations en images à l'aide de C#"
date: Mon, 10 Jan 2022 04:03:00 +0000
draft: false
url: /fr/2022/01/10/convert-presentations-to-images-using-csharp/
author: 'Shoaib Khan'
summary: "Vous souhaitez probablement utiliser vos diapositives de présentation dans des applications Web ou vous souhaitez utiliser ses vignettes de diapositives. Dans de tels cas, vous devez convertir vos diapositives de présentation PowerPoint en images. Dans cet article, vous apprendrez **comment convertir les présentations PPT ou PPTX en images JPG et PNG** par programmation à l'aide de C#.

Les sujets suivants sont abordés dans cet article:

* API .NET pour convertir des présentations
* Convertir PPT/PPTX en image JPG
* Convertir PPT/PPTX en image PNG"
tags: ['Convert PPT', 'Convert PPT to JPG in CSharp', 'Convert PPT to PNG in CSharp', 'Convert PPTX', 'PPT to JPG in CSharp', 'PPT to PNG in CSharp']
categories: ['GroupDocs.Conversion Product Family']
---

Vous souhaitez probablement utiliser vos diapositives de présentation dans des applications Web ou vous souhaitez utiliser ses vignettes de diapositives. Dans de tels cas, vous devez convertir vos diapositives de présentation PowerPoint en images. Dans cet article, vous apprendrez **comment convertir les présentations PPT ou PPTX en fichiers image JPG et PNG** par programmation à l'aide de C#.

{{< figure align=center src="images/convert-ppt-to-jpg-png-image-using-dotnet.jpg" alt="Convertir PPT en JPG ou PNG Image en utilisant .NET">}}

Les sujets suivants sont abordés ici:

* [API .NET pour convertir des présentations](#ppt-convert-dotnet-api)
* [Convertir PPT/PPTX en image JPG](#ppt-to-jpg)
* [Convertir PPT/PPTX en image PNG](#ppt-to-png)

## API .NET pour convertir des présentations {#ppt-convert-dotnet-api}

[GroupDocs.Conversion](https://products.groupdocs.com/conversion/) présente l'API .NET qui permet la conversion de fichiers de présentation en images dans les applications .NET. Dans cet article, nous utiliserons son [GroupDocs.Conversion pour .NET](https://products.groupdocs.com/conversion/net/) pour convertir les présentations PPT/PPTX en formats d'images. De plus, l'API prend en charge la conversion de nombreux autres formats de fichiers tels que les documents de traitement de texte, les feuilles de calcul, les présentations, les livres électroniques, les images et bien d'autres qui sont mentionnés dans la [documentation](https://docs.groupdocs.com/conversion/net/supported-document-formats/).

Vous pouvez télécharger le programme d'installation **DLLs** ou **MSI** à partir de la [section téléchargements](https://downloads.groupdocs.com/conversion) ou installer l'API dans votre application .NET via [NuGet](https://www.nuget.org/packages/groupdocs.conversion).

```
PM> Install-Package GroupDocs.Conversion
```

## Convertir une présentation en image JPG à l'aide de C# {#ppt-to-jpg}

Passons rapidement à l'objectif et transformons nos présentations en formats d'image. Les étapes suivantes montrent comment convertir le format d'image Powerpoint PPT ou PPTX au format JPG en C#.

* Chargez le fichier de présentation à l'aide de la classe [Converter](https://apireference.groupdocs.com/conversion/net/groupdocs.conversion/converter).
* Préparez les options de conversion d'image à l'aide de la classe [ImageConvertOptions](https://apireference.groupdocs.com/conversion/net/groupdocs.conversion.options.convert/imageconvertoptions).
* Définissez le format de fichier de conversion en tant que JPG.
* Convertir en image en utilisant la méthode [Convert()](https://apireference.groupdocs.com/conversion/net/groupdocs.conversion/converter/methods/convert/index).

Le code source C# suivant convertit la présentation PowerPoint au format JPG.

```
// Convertir des présentations PPT, PPTX en images JPG à l'aide de C#
SavePageStream getPageStream = page => new FileStream(string.Format("path/convertedPPT{0}.jpg", page), FileMode.Create);

using (Converter converter = new Converter("path/presentation.ppt"))
{
    ImageConvertOptions options = new ImageConvertOptions 
    { 
        Format = ImageFileType.Jpg 
    };  
    converter.Convert(getPageStream, options);
}
```

## Convertir une présentation en image PNG à l'aide de C# {#ppt-to-png}

L'un des formats d'image les plus utilisés est le PNG. Convertissons nos diapositives en PNG de la même manière. Les étapes suivantes expliquent comment convertir le format d'image Powerpoint PPT ou PPTX au format PNG en C#.

* Chargez le fichier PPT/PPTX de présentation à l'aide de la classe [Converter](https://apireference.groupdocs.com/conversion/net/groupdocs.conversion/converter).
* Préparez les [Options de conversion d'image](https://apireference.groupdocs.com/conversion/net/groupdocs.conversion.options.convert/imageconvertoptions).
* Définissez le format de fichier de conversion en PNG.
* Convertissez la présentation en image à l'aide de la méthode [Convert()](https://apireference.groupdocs.com/conversion/net/groupdocs.conversion/converter/methods/convert/index).

L'exemple de code C# suivant convertit la présentation PowerPoint au format PNG.

```
// Convertir des présentations PPT, PPTX en images PNG à l'aide de C#
SavePageStream getPageStream = page => new FileStream(string.Format("path/convertedPPT{0}.png", page), FileMode.Create);

using (Converter converter = new Converter("path/presentation.ppt"))
{
    ImageConvertOptions options = new ImageConvertOptions 
    { 
        Format = ImageFileType.Png 
    };  
    converter.Convert(getPageStream, options);
}
```

## Obtenez une licence API gratuite

Vous pouvez [obtenir une licence temporaire gratuite](https://purchase.groupdocs.com/temporary-license) pour utiliser l'API sans les limitations d'évaluation.

## Conclusion

Pour conclure, nous avons appris comment les présentations peuvent être converties au format JPG ou PNG Images en C#. Pour créer votre propre application de conversion, vous pouvez en savoir plus sur l'API Conversion Automation .NET à l'aide de la [documentation](https://docs.groupdocs.com/conversion/net/). Le meilleur moyen est de découvrir les exemples disponibles sur [GitHub](https://github.com/groupdocs-conversion). Contactez-nous pour toute question via le [forum](https://forum.groupdocs.com/).

## Voir également

* [Convertir des présentations en PDF en C#](https://blog.groupdocs.com/2020/03/05/convert-presentations-pptx-ppt-to-pdf-in-csharp/)
* [Conversion de feuilles de calcul Excel en PDF à l'aide de C#](https://blog.groupdocs.com/2021/11/14/convert-excel-spreadsheets-to-pdf-using-csharp/)
* [Convertir JSON en CSV et CSV en JSON en utilisant C#](https://blog.groupdocs.com/2021/06/18/convert-json-and-csv-in-csharp/)





