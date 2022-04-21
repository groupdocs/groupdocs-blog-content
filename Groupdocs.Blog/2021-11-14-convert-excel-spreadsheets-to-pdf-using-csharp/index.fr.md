---
title: "Convertir des feuilles de calcul Excel en PDF à l'aide de C#"
date: Sun, 14 Nov 2021 17:48:00 +0000
draft: false
url: /fr/2021/11/14/convert-excel-spreadsheets-to-pdf-using-csharp/
author: 'Shoaib Khan'
summary: "Les fichiers Excel (XLS, XLSX) et PDF font partie des formats de documents largement utilisés dans presque toutes les entreprises. Pour ces fichiers couramment utilisés, il existe de nombreux scénarios dans lesquels nous devons convertir un fichier dans un autre format. Dans cet article, nous allons apprendre différentes manières de convertir des feuilles de calcul Excel au format PDF à l'aide de C # avec des applications .NET."
tags: ['Convert Excel in CSharp', 'Convert Excel to PDF', 'Convert Excel to PDF in CSharp', 'Convert to PDF in CSharp', 'Excel to PDF', 'Excel to PDF in CSharp']
categories: ['GroupDocs.Conversion Product Family']
---

Les fichiers Excel ([XLS][1], [XLSX][2] et [PDF][3] font partie des formats de documents largement utilisés dans presque toutes les entreprises. Pour ces fichiers couramment utilisés, il existe de nombreux scénarios dans lesquels nous besoin de convertir un fichier dans un autre format. Dans cet article, nous allons apprendre différentes manières de convertir des feuilles de calcul Excel au format PDF à l'aide de C # avec des applications .NET.



{{< figure align=center src="images/excel-to-pdf-in-csharp.jpg" alt="Convertir une feuille de calcul Excel en PDF à l'aide de C #">}}


* [API .NET pour la conversion de fichiers Excel en PDF][4]
* [Conversion de feuilles Excel en PDF][5]
* [Séquence de conversion de feuilles Excel en PDF][6]
* [Liste spécifique de conversion de feuilles Excel en PDF][7]
* [Convertir la plage de cellules sélectionnée d'une feuille Excel en PDF][8]

## API .NET pour la conversion de fichiers Excel en PDF {#excel-conversion-dotnet-api}

[GroupDocs.Conversion][9] fournit des API qui permettent de convertir les fichiers Excel au format PDF dans les applications .NET. Dans cet article, nous utiliserons [GroupDocs.Conversion pour .NET][10] pour convertir les données des fichiers Excel XLS/XLSX au format PDF. De plus, l'API prend en charge la conversion de nombreux autres formats de fichiers tels que les documents de traitement de texte, les feuilles de calcul, les présentations, les livres électroniques, les images, etc. qui sont mentionnés dans la [documentation][11].

Vous pouvez télécharger le programme d'installation **DLLs** ou **MSI** à partir de la [section téléchargements][12] ou installer l'API dans votre application .NET via [NuGet][13].

```
PM> Install-Package GroupDocs.Conversion
```

## Convertir des feuilles Excel en PDF - C# {#excel-to-pdf}

Les étapes suivantes convertissent le classeur complet (toutes les feuilles) au format PDF à l'aide de C#.

* Préparez les **options de chargement** à l'aide de [SpreadsheetLoadOptions][14].
* **Chargez la feuille de calcul Excel** à l'aide du [Convertisseur][15].
* Appelez la méthode [Convert()][16] en utilisant [PdfConvertOptions][17] pour **convertir** toutes les feuilles et les enregistrer au format PDF.

Voici le code source C# pour convertir le classeur Excel complet en PDF dans l'application .NET.

```
/*
 * Convert all the Excel sheets to PDF format using C#
 */
// Préparer les options de chargement et la plage pour le fichier XLSX source
Func<LoadOptions> loadOptions = () => new SpreadsheetLoadOptions
{
    OnePagePerSheet = true
};
using (var converter = new GroupDocs.Conversion.Converter(@"path/spreadsheet.xlsx", loadOptions))
{
    // Convert and save the spreadsheet in PDF format
    converter.Convert(@"path/all-sheets-converted.pdf", new PdfConvertOptions());
}
```



{{< figure align=center src="images/Converted-Excel-to-PDF.png" alt="Convertir un PDF à partir de données Excel">}}


## Séquence de conversion de feuilles Excel en PDF - C# {#sheets-sequence-to-pdf}

Il n'est pas toujours nécessaire de transformer le classeur complet. Nous pouvons également convertir n'importe quel nombre consécutif de feuilles. Voici les étapes pour convertir toute sous-séquence de la ou des feuilles de classeur Excel au format PDF à l'aide de C#.

* **Chargez** le fichier Excel à l'aide du [Convertisseur][18].
* Définissez les **options de conversion** à l'aide de [PdfConvertOptions][19].
* Définissez le **numéro de feuille de départ** et le nombre de feuilles supplémentaires dans la **séquence**.
* Appelez la méthode [Convert()][20] avec les options de **conversion** pour obtenir le sous-ensemble de feuilles en séquence enregistré au format PDF.

Voici le code source C# qui convertit les feuilles dans l'ordre, c'est-à-dire les numéros de feuille **2,3 et 4** en PDF dans l'application .NET.

```
/*
 * Convert sequence of Excel sheets to PDF format using C#
 */
using (var converter = new GroupDocs.Conversion.Converter(@"path/spreadsheet.xlsx"))
{
    // Set the starting sheet number and consecutive sheet count
    var convertOptions = new PdfConvertOptions()
    {
        PageNumber = 2,
        PagesCount = 3
    };
    // Convert and save the spreadsheet in PDF format
    converter.Convert(@"path/sequential-sheets-converted.pdf", convertOptions);
}
```

## Conversion de feuilles Excel spécifiques en PDF - C# {#list-of-sheets-to-pdf}

Nous pouvons simplement fournir la liste des numéros de feuille pour la conversion de feuilles spécifiques. Voici les étapes à suivre pour convertir une liste spécifique de numéros de feuille au format PDF à l'aide de C#.

* **Chargez** le fichier de feuille de calcul à l'aide du [Convertisseur][21].
* **Sélectionnez les numéros de feuilles** et définissez-les comme liste à l'aide de [PdfConvertOptions][22].
* Appelez la méthode [Convert()][23] avec les options de conversion pour **convertir** les feuilles répertoriées au format PDF.

L'extrait de code C# suivant convertit les numéros de feuille **1, 3 et 5** en PDF dans l'application .NET.

```
/*
 * Convert the specified list of Excel sheets to PDF format using C#
 */
using (var converter = new GroupDocs.Conversion.Converter(@"path/spreadsheet.xlsx"))
{
    // Set the list to sheet numbers on convert
    var convertOptions = new PdfConvertOptions()
    {
        Pages = new System.Collections.Generic.List<int> { 1,3,5}
    };
    // Convert and save the spreadsheet into PDF format
    converter.Convert(@"path/selected-sheets-conversion.pdf", convertOptions);
}
```

## Convertir la plage de cellules sélectionnée de la feuille Excel en PDF - C # {#cell-ranges-to-pdf}

Dernier point mais non le moindre, en fait, le plus délicat, nous pouvons également convertir n'importe quelle plage de cellules de feuille(s) Excel de manière presque similaire aux autres approches. Voici les étapes pour convertir n'importe quelle plage de cellules de feuilles de classeur au format PDF à l'aide de C#.

* Tout d'abord, définissez la **plage de cellules** pour la conversion à l'aide de [SpreadsheetLoadOptions][24].
* **Chargez** le fichier de feuille de calcul à l'aide du [Convertisseur][25].
* **Sélectionnez les feuilles** soit par numéros de feuille exacts, soit par sous-séquence à l'aide de [PdfConvertOptions][26].
* Appelez la méthode [Convert()][27] avec les options de conversion pour **convertir** la plage de cellules sélectionnée des feuilles sélectionnées au format PDF.

Le code suivant convertit la plage de cellules (A1:C20) des numéros de feuille 2, 3 et 4 au format PDF à l'aide de C#.

```
/*
 * Convert the specified Cell Range of specified Excel sheets to PDF format using C#
 */
// Préparer les options de chargement et la plage pour le fichier XLSX source
Func<LoadOptions> loadOptions = () => new SpreadsheetLoadOptions
{
    ConvertRange = "A1:C20"
};
using (var converter = new Converter(@"path/spreadsheet.xlsx", loadOptions))
{
    var convertOptions = new PdfConvertOptions()
    {
        PageNumber = 2,
        PagesCount = 3
        // Pages = new System.Collections.Generic.List<int> { 2,3,4}
    };
    // Save as PDF after conversion
    converter.Convert(@"path/cell-range-converted.pdf", convertOptions);
}
```

## Conclusion

Pour conclure, nous avons appris différentes manières de convertir des feuilles de calcul Excel au format PDF à l'aide de C#. Dans un premier temps, nous avons cherché à convertir le classeur complet au format PDF, puis nous avons converti la sous-séquence de feuilles. Plus tard, nous avons appris à convertir n'importe quelle feuille en fournissant la liste des numéros de feuille exacts, et enfin, nous avons obtenu le fichier PDF à partir de la plage de cellules sélectionnée de la ou des feuilles sélectionnées.

En savoir plus sur les **API GroupDocs.Conversion** dans la [documentation][28]. Pour toute question, contactez-nous via le [forum][29].

## Voir également

* [Convertir une feuille Excel en CSV et vice versa en C#][30]
* [Feuilles Excel en filigrane à l'aide de C #][31]
* [Fichiers PDF en filigrane à l'aide de C #][32]
* [Convertir des documents en Excel (XLS, XLSX) en C#][33]







[1]: https://docs.fileformat.com/spreadsheet/xls/
[2]: https://docs.fileformat.com/spreadsheet/xlsx/)
[3]: https://docs.fileformat.com/pdf/
[4]: #excel-conversion-dotnet-api
[5]: #excel-to-pdf
[6]: #sheets-sequence-to-pdf
[7]: #list-of-sheets-to-pdf
[8]: #cell-ranges-to-pdf
[9]: https://products.groupdocs.com/conversion/
[10]: https://products.groupdocs.com/conversion/net/
[11]: https://docs.groupdocs.com/conversion/net/supported-document-formats/
[12]: https://downloads.groupdocs.com/conversion
[13]: https://www.nuget.org/packages/groupdocs.conversion
[14]: https://apireference.groupdocs.com/conversion/net/groupdocs.conversion.options.load/spreadsheetloadoptions
[15]: https://apireference.groupdocs.com/conversion/net/groupdocs.conversion/converter
[16]: https://apireference.groupdocs.com/conversion/net/groupdocs.conversion/converter/methods/convert/index
[17]: https://apireference.groupdocs.com/conversion/net/groupdocs.conversion.options.convert/pdfconvertoptions
[18]: https://apireference.groupdocs.com/conversion/net/groupdocs.conversion/converter
[19]: https://apireference.groupdocs.com/conversion/net/groupdocs.conversion.options.convert/pdfconvertoptions
[20]: https://apireference.groupdocs.com/conversion/net/groupdocs.conversion/converter/methods/convert/index
[21]: https://apireference.groupdocs.com/conversion/net/groupdocs.conversion/converter
[22]: https://apireference.groupdocs.com/conversion/net/groupdocs.conversion.options.convert/pdfconvertoptions
[23]: https://apireference.groupdocs.com/conversion/net/groupdocs.conversion/converter/methods/convert/index
[24]: https://apireference.groupdocs.com/conversion/net/groupdocs.conversion.options.load/spreadsheetloadoptions
[25]: https://apireference.groupdocs.com/conversion/net/groupdocs.conversion/converter
[26]: https://apireference.groupdocs.com/conversion/net/groupdocs.conversion.options.convert/pdfconvertoptions
[27]: https://apireference.groupdocs.com/conversion/net/groupdocs.conversion/converter/methods/convert/index
[28]: https://docs.groupdocs.com/conversion
[29]: https://forum.groupdocs.com/
[30]: https://blog.groupdocs.com/2021/08/18/convert-excel-xls-xlsx-and-csv-in-csharp/
[31]: https://blog.groupdocs.com/2021/11/04/watermark-excel-sheets-using-csharp/
[32]: https://blog.groupdocs.com/2021/07/27/watermark-pdf-files-using-csharp/
[33]: https://blog.groupdocs.com/2021/04/13/convert-document-to-excel-xls-xlsx-in-csharp/


