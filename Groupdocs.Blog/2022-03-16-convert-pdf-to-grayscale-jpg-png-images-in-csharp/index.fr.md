---
title: "Convertir un PDF en niveaux de gris à l'aide de C#"
date: Wed, 16 Mar 2022 12:05:00 +0000
draft: false
url: /fr/2022/03/16/convert-pdf-to-grayscale-jpg-png-images-in-csharp/
author: 'Shoaib Khan'
summary: "La première et la plus importante question qui vous vient à l'esprit pourrait être la suivante : s'agit-il uniquement de convertir une image RVB en niveaux de gris ? Non, vous pouvez convertir presque tous les formats de document (y compris les images) en une image monochrome en noir et blanc ou en niveaux de gris. Le contraste va du noir à la plus faible intensité au blanc à la plus forte. Dans cet article, nous expliquerons **comment convertir un document PDF couleur en formats d'image JPG et PNG en niveaux de gris à l'aide de C#**."
tags: ['convert to grayscale', 'Convert to Grayscale in CSharp', 'document to image', 'PDF to Grayscale', 'PDF to Grayscale in CSharp', 'PDF to JPG Grayscale', 'PDF to PNG Grayscale']
categories: ['GroupDocs.Conversion Product Family']
---

La première et la plus importante question qui vous vient à l'esprit pourrait être la suivante : s'agit-il uniquement de convertir une image RVB en niveaux de gris ? Non, vous pouvez convertir presque tous les formats de document (y compris les images) en une image monochrome en noir et blanc ou en niveaux de gris. Le contraste va du noir à la plus faible intensité au blanc à la plus forte. Dans cet article, nous expliquerons comment convertir des documents PDF couleur en **formats d'image JPG et PNG en niveaux de gris à l'aide de C#**.



{{< figure align=center src="images/Converted-Colored-PDF-to-Grayscale-1024x577.jpg" alt="PDF converti en niveaux de gris">}}


Cette fonctionnalité est très utile si vous allez faire du traitement d'image. Comme l'image RVB est représentée par 3 canaux et contient beaucoup de données/bruit, il faut donc plus de puissance de calcul pour traiter une telle image. D'autre part, une image en niveaux de gris rend ce processus relativement facile.

## API .NET pour convertir des documents en niveaux de gris

[GroupDocs.Conversion pour .NET](https://products.groupdocs.com/conversion/net/) est une API utilisée pour la conversion de documents entre une multitude de [formats de fichiers et types d'images pris en charge](https://docs.groupdocs.com/conversion/net/supported-document-formats/). Les résultats de conversion peuvent facilement être personnalisés et ajustés avec plusieurs options flexibles. J'utiliserai cette API pour convertir des documents PDF en images JPG et PNG en niveaux de gris.

Vous pouvez télécharger le programme d'installation **DLLs** ou **MSI** à partir de la [section téléchargements](https://downloads.groupdocs.com/conversion) ou installer l'API dans votre application .NET via [NuGet](https://www.nuget.org/packages/groupdocs.conversion).

```
PM> Install-Package GroupDocs.Conversion
```

  
Si nous parlons de son implémentation, il s'agit d'une API back-end qui peut être intégrée ou implémentée dans n'importe quelle application .NET sans aucune dépendance. Pour plus d'informations sur son API, consultez sa [documentation](https://docs.groupdocs.com/conversion/net/).

## Convertir un PDF en image JPG en niveaux de gris à l'aide de C#

Atteignons rapidement l'objectif en transformant le document PDF couleur en formats d'image noir et blanc. Les étapes suivantes montrent comment convertir le PDF en JPG en niveaux de gris à l'aide de C#.

* Chargez le document PDF à l'aide de la classe [Converter](https://apireference.groupdocs.com/conversion/net/groupdocs.conversion/converter).
* Préparez les [options de conversion d'image](https://apireference.groupdocs.com/conversion/net/groupdocs.conversion.options.convert/imageconvertoptions).
* Définissez le format de fichier de conversion sur JPG.
* Définissez l'option de niveaux de gris sur true.
* Convertir en image en utilisant la méthode [Convert()](https://apireference.groupdocs.com/conversion/net/groupdocs.conversion/converter/methods/convert/index).

Le code source C# suivant convertit le document PDF en une image JPG en niveaux de gris.

```
// Convertir un PDF en JPG en niveaux de gris en C#
using (Converter converter = new Converter("path/document.pdf"))
{
    ImageConvertOptions options = new ImageConvertOptions
    {
        Format = ImageFileType.Jpg,
        Grayscale = true,
        
        // Aditional Conversion Options
        Height = 1024,       
        Width = 1024,
        FlipMode = ImageFlipModes.FlipX,
        RotateAngle = 90,
        /*
        Brightness = 50,// Brightness
        Gamma = 0.5F,   // Gamma Settings
        Contrast = 50   // Contrast
        */
    };
    converter.Convert("path/grayscaleDocument.jpg", options);
}
```

De plus, il existe de nombreuses autres options pour contrôler la hauteur, la largeur, le retournement horizontal et vertical et les rotations de documents. Vous pouvez également appliquer les filigranes avec différents paramètres à l'image de sortie.

## Convertir un PDF en image PNG en niveaux de gris à l'aide de C#

De même, le document PDF couleur peut être converti en d'autres formats d'image en niveaux de gris. Les étapes suivantes montrent comment convertir le PDF en PNG en niveaux de gris à l'aide de C#.

* Chargez le document PDF à l'aide de la classe [Converter](https://apireference.groupdocs.com/conversion/net/groupdocs.conversion/converter).
* Préparez les [options de conversion d'image](https://apireference.groupdocs.com/conversion/net/groupdocs.conversion.options.convert/imageconvertoptions).
* Définissez le format de fichier de conversion en PNG.
* Définissez l'option de niveaux de gris sur true.
* Convertir en image PNG en utilisant la méthode [Convert()](https://apireference.groupdocs.com/conversion/net/groupdocs.conversion/converter/methods/convert/index).

Le code source C# suivant convertit le document PDF en une image PNG en niveaux de gris.

```
// Convertir un PDF en PNG en niveaux de gris en C#
using (Converter converter = new Converter("path/document.pdf"))
{
    ImageConvertOptions options = new ImageConvertOptions
    {
        Format = ImageFileType.Png,
        Grayscale = true
    };
    converter.Convert("path/grayscaleDocument.png", options);
}
```

## Obtenez une licence API gratuite

Vous pouvez [obtenir une licence temporaire gratuite](https://purchase.groupdocs.com/temporary-license) pour utiliser l'API sans les limitations d'évaluation.

## Conclusion

Pour conclure, nous avons appris comment convertir des documents PDF aux formats JPG ou PNG Images en C#. Pour créer votre propre application de conversion, vous pouvez en savoir plus sur les API Conversion Automation .NET à faible code et à code élevé dans la [documentation](https://docs.groupdocs.com/conversion/net/).

Le meilleur moyen est de découvrir les exemples disponibles sur [GitHub](https://github.com/groupdocs-conversion). Contactez-nous pour toute question via le [forum](https://forum.groupdocs.com/).

## Voir également

* [Convertir des images en PDF en C#](https://blog.groupdocs.com/2021/05/19/convert-images-to-pdf-in-csharp/)
* [Transformer des présentations en images à l'aide de C#](https://blog.groupdocs.com/2022/01/10/convert-presentations-to-images-using-csharp/)
* [Convertir des images WebP en JPG, PNG, TIFF et PDF en C#](https://blog.groupdocs.com/2020/06/30/convert-webp-to-jpg-png-tiff-and-pdf-in-csharp/)