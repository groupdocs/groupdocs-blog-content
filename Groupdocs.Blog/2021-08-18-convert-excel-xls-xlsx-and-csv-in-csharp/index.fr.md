---
title: "Convertir Excel en CSV et CSV en formats Excel en C#"
date: Wed, 18 Aug 2021 03:39:00 +0000
draft: false
url: /fr/2021/08/18/convertir-excel-xls-xlsx-et-csv-en-csharp/
author: 'Shoaib Khan'
summary: "XLS et XLSX sont les formats les plus utilisés et les plus connus des feuilles de calcul MS Excel. Vous devez être bien conscient des capacités améliorées et des innombrables options de formatage de Microsoft Office pour ces formats au cours de ce siècle. D'autre part, les fichiers **CSV** sont les valeurs séparées par des virgules, normalement utilisées pour stocker des données tabulaires sans formatage. Ces fichiers peuvent être visualisés dans n'importe quel éditeur de texte et également dans MS Excel pour le format tabulaire. Cet article traite de la conversion des feuilles de calcul Excel du format **XLS/XLSX au format CSV** et du format **CSV au format XLS/XLSX **par programmation **à l'aide de C#**."
tags: ['Convert XLS and CSV in C#', 'CSV to Excel', 'CSV to Excel in C#', 'CSV to XLSX in C#', 'Excel to CSV', 'Excel to CSV in C#', 'XLSX to CSV in C#']
categories: ['GroupDocs.Conversion Product Family']
---



{{< figure align=center src="images/convert-xlsx-to-csv-and-csv-to-excel-in-csharp.jpg" alt="Convertir XLS XLSX en CSV en C#">}}


XLS et XLSX sont les formats les plus utilisés et les plus connus des feuilles de calcul MS Excel. Vous devez être bien conscient des capacités améliorées et des innombrables options de formatage de Microsoft Office pour ces formats au cours de ce siècle. D'autre part, les fichiers **CSV** sont les valeurs séparées par des virgules, normalement utilisées pour stocker des données tabulaires sans formatage. Ces fichiers peuvent être visualisés dans n'importe quel éditeur de texte et également dans MS Excel pour le format tabulaire. Cet article explique comment convertir des feuilles de calcul Excel au format **XLS/XLSX au format CSV** et **CSV au format XLS/XLSX **par programme **à l'aide de C#**.

Les sujets suivants sont traités ci-dessous :

* [API .NET pour la conversion XLS/XLSX et CSV][1]
* [Conversion Excel vers CSV][2]
* [Conversion CSV vers Excel][3]

## API .NET pour fichiers Excel et conversion CSV {#excel-csv-dotnet-api}

[GroupDocs.Conversion][4] fournit une API .NET qui permet d'automatiser la conversion de divers documents et formats de fichiers image les uns dans les autres. J'utiliserai cette API pour convertir XLSX en CSV, puis CSV en XLS ou XLSX en utilisant C#. Outre les formats de feuille de calcul, l'API prend en charge [la conversion dans les deux sens de nombreux autres formats de documents et d'images][5] comme les documents de traitement de texte, les présentations, les livres électroniques, JPG, PNG, WebP et bien d'autres.

Vous pouvez télécharger le programme d'installation **DLLs** ou **MSI** depuis la [section téléchargements][6] ou installer l'API dans votre application .NET via [NuGet][7].

```
PM> Install-Package GroupDocs.Conversion
```

## Convertir Excel (XLS/XLSX) en CSV en C# {#excel-to-csv}

Commençons par les données tabulaires et bien formatées au format XLS ou XLSX, et convertissons-les au format CSV non formaté séparé par des virgules. Les étapes suivantes permettent de convertir le format XLS ou XLSX en CSV dans les applications .NET.

* Chargez le fichier Excel (XLS ou XLSX) en utilisant la classe [Converter][8].
* Définissez le numéro de feuille de calcul de départ et le nombre de feuilles. (Optionnel)
* Définissez le format de conversion du fichier de sortie sur CSV à l'aide de [SpreadsheetConvertOptions][9].
* Appelez la méthode [Convert][10] pour transformer les données de la feuille de calcul ou des pages spécifiques au format CSV.

Le code suivant montre comment convertir XLS ou XLSX au format CSV en C#.

```
// Convertir des feuilles de calcul Excel au format CSV de valeurs séparées par des virgules en C #
string inputFile = @"path/spreadsheet.xlsx";
string outputFile = @"path/comma-sparated-values.csv";

using (Converter converter = new Converter(inputFile))
{
    SpreadsheetConvertOptions options = new SpreadsheetConvertOptions
    {
        PageNumber = 2,
        PagesCount = 1,
        Format = SpreadsheetFileType.Csv // Specify the conversion format
    };
    converter.Convert(outputFile, options);
}
```

## Convertir CSV en Excel (XLS/XLSX) en C# {#csv-to-excel}

Au contraire, si vous avez des données séparées par des virgules et que vous souhaitez les convertir dans un format tabulaire bien formaté, vous devez convertir ces données CSV au format XLS ou XLSX. Les étapes suivantes montrent comment convertir le fichier CSV au format MS Excel XLSX à l'aide de C#.

* Préparez les options de chargement pour le fichier CSV et définissez le séparateur.
* Chargez le CSV en utilisant la classe [Converter][11].
* Définissez le format de conversion sur XLSX à l'aide de [SpreadsheetConvertOptions][12].
* Utilisez la méthode [Convert][13] pour transformer les données CSV au format XLSX.

Le code suivant montre comment convertir votre fichier CSV au format XLSX en C#.

```
// Convertir des fichiers CSV au format XLS/XLSX en C#
string inputFile = @"path/comma-sparated-values.csv";
string outputFile = @"path/spreadsheet.xlsx";

Contracts.Func<LoadOptions> getLoadOptions = () => new CsvLoadOptions
{
    Separator = ','
};

using (Converter converter = new Converter(inputFile))
{
    SpreadsheetConvertOptions options = new SpreadsheetConvertOptions();
    converter.Convert(outputFile, options);
}
```

Définissez simplement le format de conversion en conséquence et fournissez le nom de fichier approprié avec l'extension pour le XLS ou tout autre format de fichier.

## Obtenez une licence API gratuite

Vous pouvez [obtenir une licence temporaire gratuite][14] afin d'utiliser l'API sans les limitations d'évaluation.

## Conclusion

Pour résumer l'article, vous avez appris la conversion dans les deux sens des feuilles de calcul MS Excel XLS/XLSX et des fichiers CSV à l'aide de C#. Vous pouvez en savoir plus sur l'API .NET Conversion Automation à l'aide de la documentation ou en découvrant les exemples disponibles sur GitHub. Contactez-nous pour toute question via le [forum][15].

## Article associé

* [Convertir CSV en Excel et (XLS ou XLSX) en CSV en Java][16]

## Voir également

* [Générer des rapports à partir de données CSV à l'aide de C#][17]
* [Convertir des feuilles de calcul Excel en PDF à l'aide de C#][18]
* [Convertir JSON en CSV et CSV en JSON en utilisant C#][19]
* [Insérer des objets OLE dans Word, Excel, PowerPoint avec C#][20]







[1]: #excel-csv-dotnet-api
[2]: #excel-to-csv
[3]: #csv-to-excel
[4]: https://products.groupdocs.com/conversion/
[5]: https://docs.groupdocs.com/conversion/net/supported-document-formats/
[6]: https://downloads.groupdocs.com/conversion
[7]: https://www.nuget.org/packages/groupdocs.conversion
[8]: https://apireference.groupdocs.com/conversion/net/groupdocs.conversion/converter
[9]: https://apireference.groupdocs.com/conversion/net/groupdocs.conversion.options.convert/spreadsheetconvertoptions
[10]: https://apireference.groupdocs.com/conversion/net/groupdocs.conversion/converter/methods/convert/index
[11]: https://apireference.groupdocs.com/conversion/net/groupdocs.conversion/converter
[12]: https://apireference.groupdocs.com/conversion/net/groupdocs.conversion.options.convert/spreadsheetconvertoptions
[13]: https://apireference.groupdocs.com/conversion/net/groupdocs.conversion/converter/methods/convert/index
[14]: https://purchase.groupdocs.com/temporary-license
[15]: https://forum.groupdocs.com/
[16]: https://blog.groupdocs.com/2021/07/31/convert-csv-and-excel-xls-xlsx-in-java/
[17]: https://blog.groupdocs.com/2021/08/15/generate-reports-from-csv-data-in-csharp/
[18]: https://blog.groupdocs.com/2021/11/14/convert-excel-spreadsheets-to-pdf-using-csharp/
[19]: https://blog.groupdocs.com/2021/06/18/convert-json-and-csv-in-csharp/
[20]: https://blog.groupdocs.com/2020/05/16/insert-ole-objects-in-word-excel-powerpoint-with-csharp/


