---
title: "Feuilles Excel en filigrane à l'aide de C#"
date: Thu, 04 Nov 2021 18:46:00 +0000
draft: false
url: /fr/2021/11/04/watermark-excel-sheets-using-csharp/
author: 'Shoaib Khan'
summary: "Nous avons déjà discuté des moyens de filigraner différents [documents][1], [images][2] et [présentations][3]. Aujourd'hui, nous allons discuter de la façon d'ajouter un filigrane à un classeur Excel de différentes manières en utilisant C# avec l'application .NET."
tags: ['add watermark in csharp', 'how to add watermark in csharp', 'watermark dotnet api', 'watermark excel', 'watermark excel sheets in csharp']
categories: ['GroupDocs.Watermark Product Family']
---



{{< figure align=center src="images/add-watermark-to-excel-using-csharp.jpg" alt="Ajouter un filigrane à une feuille Excel à l'aide de C #">}}


Nous avons déjà discuté des moyens de filigraner différents [documents][4], [images][5] et [présentations][6]. Aujourd'hui, nous allons discuter de la façon d'ajouter un filigrane à un classeur Excel de différentes manières en utilisant C # avec l'application .NET.

Les sujets suivants sont traités ci-dessous :

* [API de filigrane pour .NET][7]
* [Ajouter un **texte en filigrane** aux feuilles Excel][8]
* [Appliquer un filigrane à ** une feuille Excel spécifique **][9]
* [Ajouter un filigrane à la feuille Excel ** en arrière-plan **][10]

## API .NET pour filigraner des feuilles Excel {#watermarking-dotnet-api}

[GroupDocs.Watermark][11] fournit l'API .NET pour les documents et les images de différents formats de fichiers. Nous utiliserons [GroupDocs.Watermark pour .NET][12] pour appliquer des filigranes dans les feuilles de calcul de différentes manières à l'aide de C#.

Vous pouvez télécharger les DLL ou le programme d'installation MSI à partir de la [section des téléchargements][13] ou l'obtenir à partir de [NuGet][14].

```
Install-Package GroupDocs.Watermark
```

## Feuilles Excel en filigrane à l'aide de C# {#watermark-all-sheets}

L'API vous permet d'insérer du texte dans les feuilles de calcul sous forme de filigrane avec différentes personnalisations. Voici les étapes pour ajouter un filigrane aux classeurs Excel à l'aide de C# avec les applications .NET.

* Préparez les options de chargement pour la feuille de calcul.
* Chargez la feuille de calcul à l'aide de [Filigrane][15].
* Définissez le texte et l'apparence du filigrane à l'aide de [TextWatermark][16].
* Ajoutez le filigrane de texte à la feuille de calcul Excel à l'aide de la méthode [Add][17].
* Enregistrez la feuille de calcul résultante avec filigrane à l'aide de la méthode [Enregistrer][18].

L'exemple de code C# suivant applique le filigrane de texte à toutes les feuilles du classeur Excel avec rotation et opacité.

```
/*
 * Add watermark to all the sheets of the Excel Workbook using C#
 */
SpreadsheetLoadOptions loadOptions = new SpreadsheetLoadOptions();
using (Watermarker watermarker = new Watermarker(@"path/spreadsheet.xlsx", loadOptions))
{
    // Add text watermark to the worksheet
    TextWatermark textWatermark = new TextWatermark("DRAFT", new Font("Arial", 100))
    {
        RotateAngle = -45,
        Height = 200,
        Width = 500,
        Opacity = .2,
        ForegroundColor = Color.DarkBlue
    };
    // Add watermark and save the watermarked spreadsheet.
    watermarker.Add(textWatermark);
    watermarker.Save(@"path/allpages-watermark-spreadsheet.xlsx");
}
```

## Feuille Excel spécifique au filigrane à l'aide de C # {#watermark-any-sheet}

De même, vous pouvez appliquer des filigranes à une feuille spécifique uniquement au lieu de les appliquer à toutes les feuilles du classeur. Les étapes suivantes expliquent comment insérer un filigrane de texte dans la feuille spécifique du classeur Excel à l'aide de C#.

* Préparez les options de chargement.
* Chargez la feuille de calcul à l'aide de la classe [Watermarker][19].
* Définissez l'apparence et le texte du filigrane à l'aide de la classe [TextWatermark][20].
* Définissez l'index de la feuille de calcul afin que le filigrane ne soit appliqué qu'à la feuille mentionnée.
* Ajoutez le filigrane de texte à la feuille de calcul Excel à l'aide de la méthode [Add][21] avec les options de filigrane.
* Enregistrez la feuille de calcul de sortie avec le filigrane à l'aide de la méthode [Enregistrer][22].

L'extrait de code suivant applique le filigrane de texte uniquement à la feuille mentionnée du classeur Excel.

```
/*
 * Add watermark only to the mentioned sheet of the Excel Workbook using C#
 */
SpreadsheetLoadOptions loadOptions = new SpreadsheetLoadOptions();
using (Watermarker watermarker = new Watermarker(@"path/spreadsheet.xlsx", loadOptions))
{
    // Add text watermark to the worksheet
    TextWatermark textWatermark = new TextWatermark("DRAFT", new Font("Arial", 100))
    {
        RotateAngle = -45,
        Height = 200,
        Width = 500,
        Opacity = .2,
        ForegroundColor = Color.DarkBlue
    };
    // Define the worksheet index
    SpreadsheetWatermarkShapeOptions textWatermarkOptions = new SpreadsheetWatermarkShapeOptions()
    {
        WorksheetIndex = 1
    };
    // Add watermark and save the watermarked spreadsheet.    
    watermarker.Add(textWatermark, textWatermarkOptions);
    watermarker.Save(@"path/onepage-watermark-spreadsheet.xlsx");
}
```

## Filigraner des feuilles Excel en arrière-plan à l'aide de C# {#watermark-sheet-as-background}

De même, nous pouvons également ajouter des filigranes comme arrière-plan de la feuille de calcul. Il y aura un petit changement par rapport aux techniques ci-dessus d'application de filigranes. Voici les étapes qui permettent d'insérer un filigrane de texte d'arrière-plan dans une feuille de calcul Excel à l'aide de C#.

* Préparez les options de chargement pour le chargement de la feuille de calcul.
* Chargez la feuille de calcul à l'aide de [Filigrane][23].
* Définissez le texte et l'apparence du filigrane (rotation, position, dimensions, opacité, couleur, etc.) à l'aide de [TextWatermark][24].
* Définissez les options de filigrane d'arrière-plan en obtenant le contenu et en définissant les dimensions.
* Définissez l'index de la feuille de calcul pour appliquer le filigrane. (Optionnel)
* Ajoutez le filigrane à la feuille de calcul à l'aide de la méthode [Add][25].
* Enregistrez la feuille de calcul avec filigrane à l'aide de la méthode [Enregistrer][26].

L'exemple de code suivant montre comment ajouter un filigrane d'arrière-plan à une feuille de calcul Excel à l'aide de C# dans l'application .NET.

```
/*
 * Add watermark as background to Excel Workbook using C#
 */
SpreadsheetLoadOptions loadOptions = new SpreadsheetLoadOptions();
using (Watermarker watermarker = new Watermarker(@"path/spreadsheet.xlsx", loadOptions))
{
    // Define Watermark Appearance
    TextWatermark textWatermark = new TextWatermark("DRAFT", new Font("Arial", 100))
    {
        RotateAngle = -45,
        X = 200,
        Y = 200,
        Height = 200,
        Width = 500,
        Opacity = .2,
        ForegroundColor = Color.DarkBlue
    };
    // Get dimensions of the spreadsheet content
    SpreadsheetContent content = watermarker.GetContent<SpreadsheetContent>();
    SpreadsheetBackgroundWatermarkOptions options = new SpreadsheetBackgroundWatermarkOptions();
    options.BackgroundWidth = content.Worksheets[0].ContentAreaWidthPx; /* set background width */
    options.BackgroundHeight = content.Worksheets[0].ContentAreaHeightPx; /* set background height */
    options.WorksheetIndex = 0;

    // Add watermark and save the watermarked spreadsheet.
    watermarker.Add(textWatermark, options);
    watermarker.Save(@"path/background-watermark-spreadsheet.xlsx");
}
```



{{< figure align=center src="images/watermark-excel-sheets-programmatically.png" alt="Filigraner des feuilles Excel par programme">}}


## Obtenez une licence API gratuite

Vous pouvez [obtenir une licence temporaire gratuite][27] afin d'utiliser l'API sans les limitations d'évaluation.

## Conclusion

Pour résumer, nous avons discuté de différentes façons d'ajouter un filigrane aux feuilles Excel à l'aide de C#. Tout d'abord, nous avons ajouté des filigranes de texte à toutes les feuilles du classeur Excel. Ensuite, nous avons appliqué le filigrane à la feuille spécifique uniquement. Enfin, nous avons inséré le filigrane textuel dans le classeur Excel en arrière-plan.

Consultez la [documentation][28] du produit pour en savoir plus sur l'API. Pour toute question, contactez-nous via le [forum][29].

## Voir également

* [Feuilles Excel en filigrane en Java][30]
* [Fichiers PDF en filigrane à l'aide de C #][31]
* [Ajouter un filigrane aux diapositives de présentation à l'aide de C #][32]
* [Images de filigrane à l'aide de C #][33]







[1]: https://blog.groupdocs.com/2021/07/27/watermark-pdf-files-using-csharp/
[2]: https://blog.groupdocs.com/2020/12/20/add-watermark-to-images-using-csharp-dotnet/
[3]: https://blog.groupdocs.com/2021/05/01/add-watermark-to-presentations-using-csharp/
[4]: https://blog.groupdocs.com/2021/07/27/watermark-pdf-files-using-csharp/
[5]: https://blog.groupdocs.com/2020/12/20/add-watermark-to-images-using-csharp-dotnet/
[6]: https://blog.groupdocs.com/2021/05/01/add-watermark-to-presentations-using-csharp/
[7]: #watermarking-dotnet-api
[8]: #watermark-all-sheets
[9]: #watermark-any-sheet
[10]: #watermark-sheet-as-background
[11]: https://products.groupdocs.com/watermark/
[12]: https://products.groupdocs.com/watermark/net/
[13]: https://downloads.groupdocs.com/watermark/net
[14]: https://www.nuget.org/packages/GroupDocs.Watermark/
[15]: https://apireference.groupdocs.com/watermark/net/groupdocs.watermark/watermarker
[16]: https://apireference.groupdocs.com/watermark/net/groupdocs.watermark.watermarks/textwatermark
[17]: https://apireference.groupdocs.com/watermark/net/groupdocs.watermark/watermarker/methods/add/index
[18]: https://apireference.groupdocs.com/watermark/net/groupdocs.watermark/watermarker/methods/save/index
[19]: https://apireference.groupdocs.com/watermark/net/groupdocs.watermark/watermarker
[20]: https://apireference.groupdocs.com/watermark/net/groupdocs.watermark.watermarks/textwatermark
[21]: https://apireference.groupdocs.com/watermark/net/groupdocs.watermark/watermarker/methods/add/index
[22]: https://apireference.groupdocs.com/watermark/net/groupdocs.watermark/watermarker/methods/save/index
[23]: https://apireference.groupdocs.com/watermark/net/groupdocs.watermark/watermarker
[24]: https://apireference.groupdocs.com/watermark/net/groupdocs.watermark.watermarks/textwatermark
[25]: https://apireference.groupdocs.com/watermark/net/groupdocs.watermark/watermarker/methods/add/index
[26]: https://apireference.groupdocs.com/watermark/net/groupdocs.watermark/watermarker/methods/save/index
[27]: https://purchase.groupdocs.com/temporary-license
[28]: https://docs.groupdocs.com/watermark
[29]: https://forum.groupdocs.com/
[30]: https://blog.groupdocs.com/2021/11/10/watermark-excel-sheets-in-java/
[31]: https://blog.groupdocs.com/2021/07/27/watermark-pdf-files-using-csharp/
[32]: https://blog.groupdocs.com/2021/05/01/add-watermark-to-presentations-using-csharp/
[33]: https://blog.groupdocs.com/2020/12/20/add-watermark-to-images-using-csharp-dotnet/


