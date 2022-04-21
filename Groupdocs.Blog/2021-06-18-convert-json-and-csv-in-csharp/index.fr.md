---
title: "Convertir JSON en CSV et CSV en JSON en utilisant C#"
date: Fri, 18 Jun 2021 12:25:49 +0000
draft: false
url: /fr/2021/06/18/convertir-json-et-csv-en-csharp/
author: 'Shoaib Khan'
summary: "**JSON** (JavaScript Object Notation) est un format de données structurées lisible par l'homme. Il est largement utilisé dans les API, les applications et les configurations pour stocker et transmettre les données. **CSV** contient les valeurs séparées par des virgules, normalement utilisées pour stocker des données tabulaires qui peuvent être parfaitement affichées à l'aide d'applications de tableur telles que MS Excel. Pour transférer les données tabulaires ou stocker les données structurées reçues sous forme tabulaire, il faut convertir les formats les uns dans les autres. Cet article traite de la conversion du format **JSON au format CSV** et du format **CSV au format JSON** par programmation **à l'aide de C#** pour vos applications .NET."
tags: ['Convert CSV in CSharp', 'Convert JSON in CSharp', 'CSV to JSON in CSharp', 'JSON to CSV in CSharp']
categories: ['GroupDocs.Conversion Product Family']
---



{{< figure align=center src="images/convert-csv-and-json-in-csharp.jpg" alt="Convertir en CSV et JSON dans CSharp .NET">}}


**JSON** (JavaScript Object Notation) est un format de données structurées lisible par l'homme. Il est largement utilisé dans les API, les applications et les configurations pour stocker et transmettre les données. **CSV** contient les valeurs séparées par des virgules, normalement utilisées pour stocker des données tabulaires qui peuvent être parfaitement affichées à l'aide d'applications de tableur telles que MS Excel. Pour transférer les données tabulaires ou stocker les données structurées reçues sous forme tabulaire, il faut convertir les formats les uns dans les autres. Cet article traite de la conversion du format **JSON au format CSV** et du format **CSV au format JSON** par programmation **à l'aide de C#** pour vos applications .NET.

Les sujets suivants sont traités ci-dessous :

* [API .NET pour la conversion JSON et CSV][1]
* [Conversion JSON en CSV][2]
* [Conversion CSV vers JSON][3]

## API .NET pour la conversion JSON et CSV {#json-csv-dotnet-api}

[GroupDocs.Conversion][4] possède des API qui permettent la conversion de fichiers JSON et CSV entre eux. Dans cet article, nous utiliserons l'API .NET de GroupDocs.Conversion pour convertir JSON en CSV puis CSV en JSON en utilisant C#. De plus, l'API permet la [conversion aller-retour de divers autres formats de documents][5] comme les documents de traitement de texte, les feuilles de calcul, les présentations, les livres électroniques, les images et bien d'autres.

Vous pouvez télécharger le programme d'installation **DLLs** ou **MSI** depuis la [section téléchargements][6] ou installer l'API dans votre application .NET via [NuGet][7].

```
PM> Install-Package GroupDocs.Conversion
```

## Convertir JSON en CSV en C# {#json-to-csv}

Les étapes suivantes permettent de convertir les fichiers JSON au format CSV dans les applications .NET.

* Chargez le JSON à l'aide de la classe [Converter][8].
* Définissez le format de conversion sur CSV à l'aide de [SpreadsheetConvertOptions][9].
* Appelez la méthode [Convert][10] pour transformer les données JSON au format CSV.

Le code suivant montre comment convertir JSON au format CSV à l'aide de C#.

```
// Convertir des fichiers JSON au format CSV en C#
using (Converter converter = new Converter(@"path/sample.json"))
{
    SpreadsheetConvertOptions options = new SpreadsheetConvertOptions()
    {
        Format = SpreadsheetFileType.Csv
    };
                
    converter.Convert(@"path/JsonToCSV.csv", options);
}
```

## Convertir CSV en JSON en C# {#csv-to-json}

Les étapes suivantes permettent de convertir les fichiers CSV au format JSON dans l'application .NET.

* Préparez les options de chargement pour charger le fichier CSV.
* Chargez le CSV en utilisant la classe [Converter][11].
* Définissez le format de conversion sur JSON à l'aide de [DataConvertOptions][12].
* Appelez la méthode [Convert][13] pour transformer les données CSV au format JSON.

Le code suivant montre comment convertir votre fichier CSV au format JSON à l'aide de C#.

```
// Convertir le fichier CSV au format JSON en C#
var loadOptions = new CsvLoadOptions
{
    Separator = ','
};

using (Converter converter = new Converter(@"path/sample.csv", ()=> loadOptions))
{
    DataConvertOptions options = new DataConvertOptions
    {
        Format = DataFileType.Json
    };
    converter.Convert(@"path/CsvToJSON.json", options);
}
```

## Obtenez une licence API gratuite

Vous pouvez [obtenir une licence temporaire gratuite][14] afin d'utiliser l'API sans les limitations d'évaluation.

## Conclusion

Pour conclure, vous avez appris comment convertir les fichiers JSON au format CSV ainsi que la conversion des fichiers CSV au format JSON par programmation à l'aide de C#. Vous pouvez en savoir plus sur l'API de conversion .NET en utilisant la [documentation][15], ou par des exemples disponibles sur [GitHub][16]. Contactez-nous sur le [forum][17].

## Voir également

* [Convertir Excel en CSV et CSV en formats Excel en C#][18]
* [Générer des rapports à partir de données JSON en C#][19]
* [Générer des rapports à partir de données CSV et XML en C#][20]







[1]: #json-csv-dotnet-api
[2]: #json-to-csv
[3]: #csv-to-json
[4]: https://products.groupdocs.com/conversion/
[5]: https://docs.groupdocs.com/conversion/net/supported-document-formats/
[6]: https://downloads.groupdocs.com/conversion
[7]: https://www.nuget.org/packages/groupdocs.conversion
[8]: https://apireference.groupdocs.com/conversion/net/groupdocs.conversion/converter
[9]: https://apireference.groupdocs.com/conversion/net/groupdocs.conversion.options.convert/spreadsheetconvertoptions
[10]: https://apireference.groupdocs.com/conversion/net/groupdocs.conversion/converter/methods/convert/index
[11]: https://apireference.groupdocs.com/conversion/net/groupdocs.conversion/converter
[12]: https://apireference.groupdocs.com/conversion/net/groupdocs.conversion.options.convert/dataconvertoptions
[13]: https://apireference.groupdocs.com/conversion/net/groupdocs.conversion/converter/methods/convert/index
[14]: https://purchase.groupdocs.com/temporary-license
[15]: https://docs.groupdocs.com/conversion/net/
[16]: https://github.com/groupdocs-conversion
[17]: https://forum.groupdocs.com/
[18]: https://blog.groupdocs.com/2021/08/18/convert-excel-xls-xlsx-and-csv-in-csharp/
[19]: https://blog.groupdocs.com/2021/03/20/generate-reports-from-json-data-in-csharp/
[20]: https://blog.groupdocs.com/2019/10/21/generate-reports-from-csv-xml-in-csharp/


