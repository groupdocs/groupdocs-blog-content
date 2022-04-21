---
title: "Convertir WebP en JPG, PNG, TIFF et PDF en C#"
date: Tue, 30 Jun 2020 07:03:38 +0000
draft: false
url: /fr/2020/06/30/convertir-webp-en-jpg-png-tiff-et-pdf-en-csharp/
author: 'Shoaib Khan'
summary: "Dans notre précédent [post][1], nous avons discuté des images WebP et appris à convertir les images WebP en Java. Aujourd'hui, dans cet article, nous allons apprendre à convertir par programme les images WebP en JPG, PNG, TIFF et autres formats à l'aide de C#."
tags: ['convert webp in csharp', 'convert webp to jpg in csharp', 'convert webp to pdf in csharp', 'convert webp to png in csharp']
categories: ['GroupDocs.Conversion Product Family']
---

Dans notre précédent [post][2], nous avons discuté des images WebP et appris à convertir les images WebP en Java. Aujourd'hui, dans cet article, nous allons apprendre à convertir par programme les images WebP en JPG, PNG, TIFF et autres formats à l'aide de C#.



{{< figure align=center src="images/convert-webp-to-jpg-png-in-csharp.jpg" alt="Convertir une image WebP aux formats JPG, PNG ou PDF dans CSharp">}}


Dans un premier temps, nous allons voir comment convertir les images WebP de la manière la plus simple. Plus tard, nous convertirons avec des options personnalisées telles que l'inclinaison, le retournement, les niveaux de gris, le redimensionnement, la modification du gamma, le contraste et la luminosité, et ajouterons un filigrane aux images JPG converties. Voici les liens rapides vers les sujets :

* [Convertir WebP en JPG, PNG et TIFF en C#][3]
* [Conversion WebP avec Options avancées (Appliquer des effets)][4]
* [Convertir WebP en PDF en C#][5]

Les étapes de cet article et les exemples de code utilisent [GroupDocs.Conversion for NET][6]. Assurez-vous donc d'installer l'API à partir de l'une des méthodes suivantes :

* Installez à l'aide de [NuGet][7] Gestionnaire de packages.
* [Téléchargez][8] la DLL et référencez-la dans le projet.

## Convertir WebP en JPG en C# {#convert-webp-to-jpg-png-tiff-in-csharp}

Pour convertir les images WebP dans d'autres formats, utilisez la classe **Converter**. Pour la conversion simple, vous pouvez utiliser les quelques lignes de code C# mentionnées ci-dessous. Cet exemple montre la conversion rapide d'une image WebP en un fichier JPG. Suivez simplement les étapes :

1. Instanciez l'objet [Converter][9] avec l'image WebP source.
2. Instanciez les options de conversion d'image à l'aide de la classe [ImageConvertOptions][10] et définissez simplement le format sur JPG.
3. Appelez la méthode [Convert][11] avec le chemin du fichier de sortie et les options de conversion.

```
// Convert WebP image to JPG, PNG, BMP or any other format in C#
using (Converter converter = new Converter("./Resources/groupdocs\_conversion-brand.webp"))
{
    ImageConvertOptions options = new ImageConvertOptions
    { // Set the conversion format to JPG
        Format = ImageFileType.Jpg
    };
    converter.Convert(@"./Output/converted-image.jpg", options);
}
```

Voici l'image WebP d'origine et l'image JPG convertie à l'aide du code ci-dessus :



{{< figure align=center src="images/groupdocs_conversion-brand.webp" alt="Image WebP" caption="Image WebP">}}
</td><td>

{{< figure align=center src="images/converted-image.jpg" alt="Converti de WebP en JPG" caption="Image JPG convertie">}}
</td></tr></tbody></table></figure>

### Convertir WebP en PNG, TIFF et autres formats d'image en C#

En utilisant le même code ci-dessus et en changeant simplement le format de fichier, c'est-à-dire **"ImageFileType.Jpg"** et le nom du fichier de sortie, vous pouvez facilement convertir vos fichiers WebP en JPEG, PNG, TIF, TIFF, BMP, etc.

C'était la conversion simple, maintenant convertissons avec des effets différents.

## Convertir WebP en JPG, PNG, TIFF avec des options avancées en C# {#convert-webp-and-apply-effects-in-csharp}

Parallèlement à la conversion de WebP vers d'autres formats, nous pouvons également ajouter des effets lors de la conversion. Voici quelques-uns des effets comme; convertir en **niveaux de gris** ; **retourner** les images horizontalement ou verticalement ; **faire pivoter** l'image à n'importe quel angle ; **redimensionnez** l'image pour la rendre plus petite ou plus grande ; modifier les valeurs de **contraste**, **luminosité**, **gamma** ; ou même appliquer des ** filigranes ** aux images converties.



{{< figure align=center src="images/converted-image.jpg" alt="Converti de WebP en JPG" caption="WebP en JPG">}}
</td><td class="has-text-align-center" data-align="center">

{{< figure align=center src="images/converted-and-grayscale.jpg" alt="Converti de WebP en JPG en niveaux de gris" caption="Niveaux de gris">}}
</td><td class="has-text-align-center" data-align="center">

{{< figure align=center src="images/converted-and-resize.jpg" alt="Converti de WebP en JPG avec redimensionnement" caption="Redimensionner">}}
</td></tr><tr><td class="has-text-align-center" data-align="center">

{{< figure align=center src="images/converted-and-flipped.jpg" alt="Converti de WebP en JPG avec retournement horizontal" caption="Retourner">}}
</td><td class="has-text-align-center" data-align="center">

{{< figure align=center src="images/converted-and-contrast-50.jpg" alt="Converti de WebP en JPG avec un contraste modifié" caption="Contraste">}}
</td><td class="has-text-align-center" data-align="center">

{{< figure align=center src="images/converted-with-wateramrk.jpg" alt="Converti de WebP en JPG avec filigrane" caption="Filigrane">}}
</td></tr><tr><td class="has-text-align-center" data-align="center">

{{< figure align=center src="images/converted-and-rotated-1.jpg" alt="Converti de WebP en JPG avec rotation" caption="Tourner">}}
</td><td class="has-text-align-center" data-align="center">

{{< figure align=center src="images/converted-and-brightness-50.jpg" alt="Converti de WebP en JPG avec une luminosité modifiée" caption="Luminosité">}}
</td><td class="has-text-align-center" data-align="center">

{{< figure align=center src="images/converted-with-gamma-0.5.jpg" alt="Converti de WebP en JPG avec Gamma Change" caption="Gamma">}}
</td></tr></tbody></table></figure>

Voici le code qui est utilisé pour appliquer ces effets. Vous pouvez appliquer ces effets un par un ou en combinaison pour obtenir les résultats souhaités.

```
// Apply effects while converting WebP image to other formats in C#
using (Converter converter = new Converter("./Resources/groupdocs\_conversion-brand.webp"))
{
    ImageConvertOptions options = new ImageConvertOptions
    {
        Format = ImageFileType.Jpg,
        Grayscale = true,   // Convert the image in Grayscale
        Height = 141,       // Resize the Image Height
        Width = 167,        // Resize the image Width
        FlipMode = ImageFlipModes.FlipX,    // Flip the image
        Contrast = 50,      // Change the contrast of image
        RotateAngle = 90,   // Rotate the image
        Brightness = 50,    // Change the brightness
        Gamma = 0.5F,       // Gamma Setting
        Watermark =         // Watermark Settings
        {
            Text = "GroupDocs",
            Width = 100,
            Height = 100,
            Background = false,
            Top = 70,
            Left = 90,
            RotationAngle = -45,
        }
    };
    converter.Convert(@"./Output/converted-with-options.jpg", options);
}
```

## Convertir WebP en PDF en C# {#convert-webp-to-pdf-in-csharp}

Parallèlement à la conversion d'images WebP vers d'autres formats de fichiers image, nous pouvons également convertir des images au format PDF. Suivre 3 lignes de code fera l'affaire et vous aidera à convertir l'image WebP au format PDF.

```
// Convert WebP to PDF in C#
using (Converter converter = new Converter("./Resources/groupdocs\_conversion-brand.webp"))
{
    PdfConvertOptions options = new PdfConvertOptions();
    converter.Convert(@"./Output/converted-webp-image.pdf", options);
}
```

Pour plus de détails et les options avancées de conversion en PDF, vous pouvez consulter la [documentation][12].

## Voir également

* [Convertir WebP en JPG, PNG et PDF en Java][13]

Il existe de nombreux autres exemples open source accessibles au public sur [GitHub Repository][14]. Téléchargez le code source et exécutez rapidement les exemples à l'aide du guide [de démarrage][15]. En cas de difficulté, consultez la [documentation][16] ou rejoignez-nous à tout moment sur le [forum][17].







[1]: https://blog.groupdocs.com/2020/01/26/convert-webp-to-jpg-png-and-pdf-in-java/
[2]: https://blog.groupdocs.com/2020/01/26/convert-webp-to-jpg-png-and-pdf-in-java/
[3]: https://blog.groupdocs.com/2020/06/30/convert-webp-to-jpg-png-tiff-and-pdf-in-csharp/#convert-webp-to-jpg-png-tiff-in-csharp
[4]: https://blog.groupdocs.com/2020/06/30/convert-webp-to-jpg-png-tiff-and-pdf-in-csharp/#convert-webp-and-apply-effects-in-csharp
[5]: https://blog.groupdocs.com/2020/06/30/convert-webp-to-jpg-png-tiff-and-pdf-in-csharp/#convert-webp-to-pdf-in-csharp
[6]: https://products.groupdocs.com/conversion/net
[7]: https://www.nuget.org/packages/groupdocs.conversion
[8]: https://downloads.groupdocs.com/conversion/net
[9]: https://apireference.groupdocs.com/conversion/net/groupdocs.conversion/converter
[10]: https://apireference.groupdocs.com/conversion/net/groupdocs.conversion.options.convert/imageconvertoptions
[11]: https://apireference.groupdocs.com/conversion/net/groupdocs.conversion.converter/convert/methods/16
[12]: https://docs.groupdocs.com/conversion/net/convert-to-pdf-with-advanced-options/
[13]: https://blog.groupdocs.com/2021/01/18/convert-webp-to-jpg-png-and-pdf-in-java/
[14]: https://github.com/groupdocs-conversion/GroupDocs.Conversion-for-.NET
[15]: https://docs.groupdocs.com/display/conversionnet/Getting+Started
[16]: https://docs.groupdocs.com/display/conversionnet/Home
[17]: https://forum.groupdocs.com/c/conversion


