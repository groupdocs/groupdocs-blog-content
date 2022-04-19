---
title: "Convertir CSV en XML en C#"
date: Mon, 27 Sep 2021 12:59:00 +0000
draft: false
url: /fr/2021/09/27/convert-csv-to-xml-in-csharp/
author: 'Shoaib Khan'
summary: "CSV et XML sont parmi les formats de fichiers les plus populaires utilisés par les développeurs. Ces formats sont normalement utilisés pour stocker et échanger des données dans et entre les applications. Il est souvent nécessaire de convertir un format dans un autre avant de stocker ou de transmettre les informations. Dans cet article, vous découvrirez **comment convertir par programmation le fichier CSV (valeurs séparées par des virgules) au format XML à l'aide de C#**."
tags: ['Convert CSV to XML', 'Convert CSV to XML in CSharp', 'CSV to XML', 'CSV to XML in CSharp']
categories: ['GroupDocs.Conversion Product Family']
---

CSV et XML sont parmi les formats de fichiers les plus populaires utilisés par les développeurs. Ces formats sont normalement utilisés pour stocker et échanger des données dans et entre les applications. Il est souvent nécessaire de convertir un format dans un autre avant de stocker ou de transmettre les informations. Dans cet article, vous découvrirez **comment convertir par programmation le fichier CSV (valeurs séparées par des virgules) au format XML à l'aide de C#**.



{{< figure align=center src="images/convert-csv-to-xml-using-csharp.jpg" alt="Convertir CSV en XML en utilisant CSharp">}}


L'article couvre les sujets suivants :

* [API .NET - Conversion CSV vers XML][1]
* [Comment convertir CSV en XML en C#][2]

## API .NET pour la conversion CSV vers XML {#csv-to-xml-dotnet-api}

[GroupDocs.Conversion][3] fournit des API qui permettent les conversions de fichiers CSV et XML. Dans cet article, nous utiliserons l'API .NET de GroupDocs.Conversion pour convertir les données au format CSV au format XML à l'aide de C#. De plus, l'API prend en charge de nombreux autres formats de fichiers pour la conversion, tels que les documents de traitement de texte, les feuilles de calcul, les présentations, les livres électroniques, les images, etc.

Vous pouvez télécharger le programme d'installation **DLLs** ou **MSI** à partir de la [section téléchargements][4] ou installer l'API dans votre application .NET via [NuGet][5].

```
PM> Install-Package GroupDocs.Conversion
```

## Convertir CSV en XML en C# {#csv-to-xml}

Les fichiers CSV peuvent être visualisés et modifiés visuellement à l'aide d'éditeurs tels que MS Excel. L'image montre les données CSV que j'ai utilisées pour la conversion. Il existe de nombreux convertisseurs CSV vers XML disponibles en ligne, cependant, le code mentionné dans cette section peut renforcer vos applications .NET avec cette simple conversion.



{{< figure align=center src="images/csv-sample-file-opened-in-excel.jpg" alt="Exemple de fichier CSV ouvert dans Excel">}}


Les étapes suivantes vous guident pour convertir les données fournies au format CSV au format XML.

* Chargez le fichier CSV en utilisant la classe [Converter][6].
* Définissez le format de conversion sur XML à l'aide de [DataConvertOptions][7].
* Appelez la méthode [Convert][8] pour obtenir les données au format XML à partir du fichier CSV chargé.

Le code source suivant convertit le fichier CSV au format XML à l'aide de C#.

```
// Convertir les données CSV au format XML à l'aide de C#
using (Converter converter = new Converter(@"path/sample.csv"))
{
    DataConvertOptions options = new DataConvertOptions
    {
        Format = DataFileType.Xml
    };
    converter.Convert(@"path/CSV-to-XML.xml", options);
}
```

La sortie du code ci-dessus est la suivante. Je partage la partie du fichier XML pour que vous ayez une idée de la sortie XML.

```
<DocumentElement>
  <Sheet1>
    <Employee>David</Employee>
    <Quarter>1</Quarter>
    <Product>Maxilaku</Product>
    <Continent>Asia</Continent>
    <Country>China</Country>
    <Sale>2000</Sale>
  </Sheet1>
  <Sheet1>
    <Employee>David</Employee>
    ...
  </Sheet1>
  <Sheet1>
    ...
  </Sheet1>
</DocumentElement>
```

## Obtenez une licence API gratuite

Vous pouvez [obtenir une licence temporaire gratuite][9] pour utiliser l'API sans les limitations d'évaluation.

## Conclusion

Pour résumer, nous avons discuté de la conversion des données CSV au format XML dans les applications .NET utilisant C#. Pour créer votre propre application de conversion, vous pouvez en savoir plus sur l'API Conversion Automation .NET à l'aide de la [documentation][10]. Le mieux est de tester les exemples disponibles sur [GitHub][11]. Contactez-nous pour toute question via le [forum][12].

## Voir également

* [Conversion JSON vers XML en C#][13]
* [Convertir JSON en CSV et CSV en JSON en utilisant C#][14]
* [Convertir Excel en CSV et CSV en formats Excel en C#][15]







[1]: #csv-to-xml-dotnet-api
[2]: #csv-to-xml
[3]: https://products.groupdocs.com/conversion/
[4]: https://downloads.groupdocs.com/conversion
[5]: https://www.nuget.org/packages/groupdocs.conversion
[6]: https://apireference.groupdocs.com/conversion/net/groupdocs.conversion/converter
[7]: https://apireference.groupdocs.com/conversion/net/groupdocs.conversion.options.convert/dataconvertoptions
[8]: https://apireference.groupdocs.com/conversion/net/groupdocs.conversion/converter/methods/convert/index
[9]: https://purchase.groupdocs.com/temporary-license
[10]: https://docs.groupdocs.com/conversion/net/
[11]: https://github.com/groupdocs-conversion
[12]: https://forum.groupdocs.com/
[13]: https://blog.groupdocs.com/2021/09/11/convert-json-to-xml-in-csharp/
[14]: https://blog.groupdocs.com/2021/06/18/convert-json-and-csv-in-csharp/
[15]: https://blog.groupdocs.com/2021/08/18/convert-excel-xls-xlsx-and-csv-in-csharp/


