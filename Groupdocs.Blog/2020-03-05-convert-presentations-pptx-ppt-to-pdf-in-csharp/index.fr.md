---
title: "Convertir des présentations PowerPoint PPT, PPTX et OpenOffice en PDF en C#"
date: Thu, 05 Mar 2020 21:59:00 +0000
draft: false
url: /fr/2020/03/05/convert-presentations-pptx-ppt-to-pdf-in-csharp/
aliases:
- /2020/03/05/convert-pptx-to-pdf-in-csharp/
- /2020/03/05/convert-ppt-to-pdf-in-csharp/
- /2020/03/05/convert-pptx-ppt-to-pdf-in-csharp/
author: 'Shoaib Khan'
summary: "[PDF][1] est sans aucun doute le [Portable Document Format][2], qui est l'un des formats de fichiers les plus couramment utilisés. Les formats [PPT][3] et [PPTX][4] de Microsoft PowerPoint partagent la popularité des documents commerciaux. En raison de la popularité des formats de document et de la nature de mise en page fixe du format PDF, il est nécessaire de **convertir le format PPT/PPTX au format PDF**."
tags: ['Convert PPT to PDF in CSharp', 'Convert PPTX to PDF in CSharp', 'CSharp PPT to PDF', 'CSharp PPTX to PDF']
categories: ['GroupDocs.Conversion Product Family']
---

[PDF][5] est sans aucun doute le [Portable Document Format][6], qui est l'un des formats de fichiers les plus couramment utilisés. Les formats [PPT][7] et [PPTX][8] de Microsoft PowerPoint partagent la popularité des documents commerciaux. En raison de la popularité des formats de document et de la nature de mise en page fixe du format PDF, il est nécessaire de **convertir le format PPT/PPTX au format PDF**.



{{< figure align=center src="images/Convert-PPT-to-PDF-csharp.png" alt="PPTX en PDF en C#">}}


Considérant les développeurs .NET d'aujourd'hui, cet article fournira la solution à la conversion de format de fichier mentionnée ci-dessus. GroupDocs prend en charge la conversion de [plus de 50 formats de documents][9], fournissant ainsi des API sur site (.NET et Java), des API cloud et des [applications de conversion][10] en ligne. Après cet article, vous vous familiariserez avec les différentes manières de convertir des présentations Microsoft et OpenOffice à l'aide de [GroupDocs.Conversion pour .NET][11].

Les sujets suivants sont abordés ci-dessous :

* [Comment convertir une présentation complète en PDF][12]
* [Convertir des diapositives PPT spécifiques en PDF][13]
* [Convertir un sous-ensemble séquentiel de diapositives en PDF][14]
* [Conversions possibles du format PowerPoint PPT/PPTX][15]
* [Convertir la présentation avec les options avancées][16]
* [Appliquer un filigrane lors de la conversion en PDF][17]

## Convertir PPT en PDF en C# {#ppt-to-pdf}

[GroupDocs.Conversion][18] a rendu cela si facile ; la conversion populaire et exigeante des fichiers de présentation. Juste avec les deux lignes de code CSharp mentionnées ci-dessous, vous pouvez convertir rapidement tout type de présentation comme PPTX ou PPT en PDF.

* Créez une nouvelle instance de [Converter][19] Class avec le document source.
* Instancier l'objet [PdfConvertOptions][20].
* Appelez la méthode [Convert()][21] de la classe Converter.

L'exemple de code suivant convertit le PowerPoint PPTX complet en PDF en C#.

```
// Convertir un PPT entier en PDF en utilisant C#
using (Converter converter = new Converter("path/presentation.pptx"))
{
    converter.Convert("path/converted-presentation.pdf", new PdfConvertOptions());
}
```

## Convertir des diapositives spécifiques de PPT en PDF en C# {#specific-slides}

Nous pourrions avoir l'obligation de convertir uniquement les diapositives sélectionnées au lieu de convertir toute la présentation. GroupDocs.Conversion permet de convertir les diapositives spécifiques d'une présentation en document PDF résultant. Vous trouverez ci-dessous les étapes et le code source C # qui montre comment y parvenir.

* **Chargez** la présentation à l'aide de la classe [Converter][22].
* Préparez [Options de conversion][23] pour PDF.
* **Liste des numéros de diapositives sélectionnés** à convertir.
* **Convertir** en PDF en utilisant la méthode [Convert()][24].

Le code source suivant convertit les diapositives numéro 1 et 3 d'une présentation en PDF.

```
// Convertissez uniquement des diapositives PPT spécifiques en PDF à l'aide de C #
using (Converter converter = new Converter("path/presentation.pptx"))
{
    PdfConvertOptions options = new PdfConvertOptions
    {
        Pages = new List<int>{ 1, 3 }
    };
    converter.Convert("path/converted-presentation.pdf", options);
}
```

## Convertir des diapositives consécutives de PPTX en PDF à l'aide de C # {#successive-slides}

Avec la petite modification de l'exigence, voici le petit changement dans le code. Certaines diapositives consécutives de la présentation peuvent être sélectionnées pour les convertir au format PDF. Définissez simplement le numéro de la page de départ et le nombre de pages successives à venir.

* **Chargez** le fichier de présentation en utilisant la classe [Converter][25].
* Définissez le **numéro de page de départ** et le **nombre de diapositives séquentielles** à l'aide des [Options de conversion PDF][26].
* **Enregistrer** les diapositives sélectionnées au format PDF en utilisant la méthode [Convert()][27].

L'extrait de code suivant convertit les diapositives numéros 2, 3 et 4 au format PDF en C#.

```
// Convertir quelques diapositives PPT consécutives en PDF à l'aide de C #
using (Converter converter = new Converter("path/presentation.pptx"))
{
    PdfConvertOptions options = new PdfConvertOptions
    {
        PageNumber = 2,
        PagesCount = 3
    };
    converter.Convert("path/converted-presentation.pdf", options);
}
```

## Conversions possibles de PPT/PPTX {#possible-conversions}

Ce n'est pas seulement le PDF qui pourrait être le format de document cible lors de la conversion. Vous pouvez vous référer à la [documentation pour toutes les conversions possibles][28]. Plus important pour les développeurs, nous pouvons récupérer tous les formats de conversion possibles des présentations PPT/PPTX en appelant simplement la méthode GetPossibleConversions() de la classe Converter.

* Définissez le format source à l'aide de la classe [Converter][29].
* Obtenez toutes les conversions possibles du format source à l'aide de la méthode [GetPossibleConversions()][30].

Le code source suivant montre comment récupérer toutes les conversions possibles des formats PPTX à l'aide de C#.

```
// Répertorier les conversions possibles de PPT à l'aide de l'API .NET
string sourceFile = "path/presentation.pptx";
using (Converter converter = new Converter(sourceFile))
{
    PossibleConversions conversions = converter.GetPossibleConversions();
    Console.WriteLine("{0} is of type {1} and could be converted to:", sourceFile, conversions.Source.Extension);
    foreach (var conversion in conversions.All)
    {
        Console.WriteLine("\t {0} as {1} conversion.", conversion.Format, conversion.IsPrimary?"primary": "secondary");
    }
}
```

## Convertir PPT en PDF avec des options avancées {#ppt-to-pdf-adv}

Il existe de nombreuses autres options lors de la conversion des présentations. Ces options sont rarement nécessaires, mais lorsqu'elles sont requises, elles prouvent leur importance. [**PdfConvertOptions**][31] permet de contrôler les résultats de la conversion lors de la conversion au format PDF. Outre les options de conversion courantes, il dispose de nombreuses options supplémentaires qui peuvent être consultées en détail dans la [documentation][32]. Juste pour un aperçu, nous pouvons personnaliser la conversion PPT avec les options mentionnées et bien plus :

* [Zoom][33]
* [Marges][34]
* [Niveaux de gris][35]
* [Options de formatage][36]
* [Qualité d'image][37]
* [Rotation][38]
* [Filigrane][39]

```
// Conversion de présentations en PDF avec des options avancées à l'aide de C#
using (Converter converter = new Converter("path/presentation.pptx"))
{
    PdfConvertOptions options = new PdfConvertOptions
    {
        PageNumber = 2,
        PagesCount = 1,
        Rotate = Rotation.On180,
        Dpi = 300,
        Width = 1024,
        Height = 768
    };
    converter.Convert("path/converted-presentation.pdf", options);
}
```

## Ajouter un filigrane lors de la conversion de PPTX ou PPT en PDF en C # {#watermarked}

Vous souhaitez sécuriser votre présentation tout en la convertissant au format PDF ? Laissez un filigrane sur le PDF résultant. Les étapes et le code source mentionnés ci-dessous montrent comment mettre un filigrane lorsqu'une présentation PPT/PPTX est convertie au format PDF.

* **Chargez** le fichier PPT en utilisant la classe [Converter][40].
* **Préparez les [options de filigrane de texte][41]** et définissez :
    
    * Texte et police du filigrane
    
    * Couleur du filigrane
    * Largeur et hauteur
    * Angle de rotation
    * Transparence
* **Ajoutez le filigrane préparé** à [Options de conversion PDF][42].
* **Enregistrer** la présentation au format PDF en utilisant la méthode [Convert()][43].

L'exemple de code C# suivant ajoute un filigrane avec un angle de rotation et une transparence lors de la conversion du PPT en PDF.

```
// Appliquez un filigrane aux diapositives de la présentation lors de sa conversion en PDF à l'aide de C #
using (Converter converter = new Converter("path/presentation.pptx"))
{
    PdfConvertOptions options = new PdfConvertOptions
    {
        Watermark = new WatermarkTextOptions("Watermark")
        {
            Color = Color.Blue,
            Width = 100,
            Height = 100,
            Background = true,
            RotationAngle = -45,
            Transparency = 0.5
        }
    };
    converter.Convert("path/converted-presentation.pdf", options);
}
```

## Conclusion

Résumons ce dont nous avons discuté. Nous avons appris différentes façons de convertir le format PPT au format PDF en C#. Nous avons examiné séparément les étapes et l'exemple de code pour convertir une **liste spécifique de diapositives**, tout **sous-ensemble successif** de diapositives de présentation et la conversion de **PPT en PDF avec un filigrane personnalisé** et d'autres options. En savoir plus sur **GroupDocs.Conversion** dans la [documentation][44].

## Parlons

Vous pouvez créer votre propre application en utilisant les fonctionnalités mises en évidence ci-dessus. Nous serons ravis si vous nous contactez sur le [forum][45] pour discuter, résoudre un problème ou partager vos commentaires. Bon temps de développement.

## Voir également

* [Convertir des présentations PowerPoint et OpenOffice en PDF en Java][46]







[1]: https://wiki.fileformat.com/view/pdf/
[2]: https://en.wikipedia.org/wiki/PDF
[3]: https://wiki.fileformat.com/presentation/ppt/
[4]: https://wiki.fileformat.com/presentation/pptx/
[5]: https://wiki.fileformat.com/view/pdf/
[6]: https://en.wikipedia.org/wiki/PDF
[7]: https://wiki.fileformat.com/presentation/ppt/
[8]: https://wiki.fileformat.com/presentation/pptx/
[9]: https://docs.groupdocs.com/conversion/net/supported-document-formats/
[10]: https://products.groupdocs.app/conversion/family
[11]: https://products.groupdocs.com/conversion/net
[12]: #ppt-to-pdf
[13]: #specific-slides
[14]: #successive-slides
[15]: #possible-conversions
[16]: #ppt-to-pdf-adv
[17]: #watermarked
[18]: https://products.groupdocs.com/conversion
[19]: https://apireference.groupdocs.com/net/conversion/groupdocs.conversion/converter
[20]: https://apireference.groupdocs.com/net/conversion/groupdocs.conversion.options.convert/pdfconvertoptions
[21]: https://apireference.groupdocs.com/net/conversion/groupdocs.conversion/converter/methods/convert/2
[22]: https://apireference.groupdocs.com/conversion/net/groupdocs.conversion/converter
[23]: https://apireference.groupdocs.com/conversion/net/groupdocs.conversion.options.convert/pdfconvertoptions
[24]: https://apireference.groupdocs.com/conversion/net/groupdocs.conversion/converter/methods/convert/index
[25]: https://apireference.groupdocs.com/conversion/net/groupdocs.conversion/converter
[26]: https://apireference.groupdocs.com/conversion/net/groupdocs.conversion.options.convert/pdfconvertoptions
[27]: https://apireference.groupdocs.com/conversion/net/groupdocs.conversion/converter/methods/convert/index
[28]: https://docs.groupdocs.com/conversion/net/supported-document-formats/
[29]: https://apireference.groupdocs.com/conversion/net/groupdocs.conversion/converter
[30]: https://apireference.groupdocs.com/conversion/net/groupdocs.conversion/converter/methods/getpossibleconversions/index
[31]: https://apireference.groupdocs.com/net/conversion/groupdocs.conversion.options.convert/pdfconvertoptions
[32]: https://docs.groupdocs.com/conversion/net/convert-to-pdf-with-advanced-options/#ConverttoPDFwithadvancedoptions-PdfOptions
[33]: https://apireference.groupdocs.com/net/conversion/groupdocs.conversion.options.convert/pdfoptions/properties/zoom
[34]: https://apireference.groupdocs.com/net/conversion/groupdocs.conversion.options.convert/pdfconvertoptions/properties/marginleft
[35]: https://apireference.groupdocs.com/net/conversion/groupdocs.conversion.options.convert/pdfoptions/properties/grayscale
[36]: https://docs.groupdocs.com/display/conversionnet/Convert+to+PDF+with+advanced+options#ConverttoPDFwithadvancedoptions-PdfFormattingOptions
[37]: https://apireference.groupdocs.com/net/conversion/groupdocs.conversion.options.convert/pdfoptimizationoptions/properties/imagequality
[38]: https://apireference.groupdocs.com/net/conversion/groupdocs.conversion.options.convert/pdfconvertoptions/properties/rotate
[39]: https://apireference.groupdocs.com/conversion/net
[40]: https://apireference.groupdocs.com/conversion/net/groupdocs.conversion/converter
[41]: https://apireference.groupdocs.com/conversion/net/groupdocs.conversion.options.convert/watermarktextoptions
[42]: https://apireference.groupdocs.com/conversion/net/groupdocs.conversion.options.convert/pdfconvertoptions
[43]: https://apireference.groupdocs.com/conversion/net/groupdocs.conversion/converter/methods/convert/index
[44]: https://docs.groupdocs.com/conversion/net/
[45]: https://forum.groupdocs.com/c/conversion
[46]: https://blog.groupdocs.com/2021/02/15/convert-presentations-odp-pptx-ppt-to-pdf-in-java/


