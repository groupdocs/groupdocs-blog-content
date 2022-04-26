---
title: "Convertir JSON en XML en C#"
date: Sat, 11 Sep 2021 09:17:00 +0000
draft: false
url: /fr/2021/09/11/convert-json-to-xml-in-csharp/
author: 'Shoaib Khan'
summary: 'JSON and XML, both are the well known structured formats that are vastly used by developers to transmit data. There are many requirement where as a programmer, we need the conversion between JSON and XML data formats. In this article, you will learn how to convert JSON data into XML format using C#.

Les sujets suivants seront abordés dans cet article :

* API .NET pour la conversion JSON et XML
* Convertir par programmation JSON en XML'
tags: ['Convert JSON to XML', 'Convert JSON to XML in CSharp', 'JSON to XML', 'JSON to XML in CSharp']
categories: ['GroupDocs.Conversion Product Family']
---

JSON et XML sont tous deux des formats structurés bien connus qui sont largement utilisés par les développeurs pour transmettre des données. Il existe de nombreuses exigences pour lesquelles, en tant que programmeur, nous avons besoin de la conversion entre les formats de données JSON et XML. Dans cet article, vous apprendrez **comment convertir des données JSON au format XML à l'aide de C#**.



{{< figure align=center src="images/convert-json-to-xml-csharp.jpg" alt="Convertir JSON en XML dans CSharp">}}


Les sujets suivants sont traités ci-dessous :

* [API .NET pour la conversion JSON et XML][1]
* [Convertir par programmation JSON en XML][2]

## API .NET pour la conversion JSON et XML {#json-xml-conversion-dotnet-api}

[GroupDocs.Conversion][3] fournit une API .NET qui permet d'automatiser la conversion de différents documents, images et autres formats de fichiers les uns dans les autres. J'utilise la même API ici pour convertir des fichiers JSON au format XML en utilisant C#. Outre la conversion JSON et XML, l'API prend en charge de nombreuses autres [conversions aller-retour][4] comme les documents de traitement de texte, les présentations, les livres électroniques, JPG, PNG, WebP et bien d'autres. Vous pouvez voir les détails sur la documentation.

Vous pouvez télécharger le programme d'installation **DLLs** ou **MSI** à partir de la [section téléchargements][5] ou installer l'API dans votre application .NET via [NuGet][6].

```
PM> Install-Package GroupDocs.Conversion
```

## Convertir JSON en XML en C# {#json-to-xml}

Les formats JSON et XML sont couramment utilisés dans les applications Web pour transmettre des données. Il s'agit de formats structurés, lisibles par l'homme et hiérarchiques pour stocker et échanger des données.

Les étapes suivantes vous guident pour convertir les données JSON au format XML à l'aide de l'API .NET.

* Chargez le fichier de données JSON à l'aide de la classe [Converter][7].
* Utilisez [DataConvertOptions][8] pour définir le format de conversion sur XML.
* Appelez la méthode [Convert][9] de la classe Converter pour transformer les données JSON au format XML

Le code suivant convertit les données JSON au format XML à l'aide de C#.

```
// Convertir les données JSON au format XML à l'aide de C#
using (Converter converter = new Converter(@"path/sample.json"))
{
    DataConvertOptions options = new DataConvertOptions
    {
        Format = DataFileType.Xml
    };
    converter.Convert(@"path/jsonToXML.xml", options);
}
```

## Obtenez une licence API gratuite

Vous pouvez [obtenir une licence temporaire gratuite][10] pour utiliser l'API sans les limitations d'évaluation.

## Conclusion

Pour conclure, vous avez appris la conversion de données JSON au format XML au sein de vos applications .NET à l'aide de C#. Vous pouvez en savoir plus sur l'API .NET Conversion Automation à l'aide de la [documentation][11], ou en découvrant rapidement les exemples disponibles sur [GitHub][12]. Contactez-nous pour toute question via le [forum][13].

## Voir également

* [Convertir JSON et CSV en utilisant C#][14]
* [Convertir Excel et CSV en utilisant C#][15]







[1]: #json-xml-conversion-dotnet-api
[2]: #json-to-xml
[3]: https://products.groupdocs.com/conversion/
[4]: https://docs.groupdocs.com/conversion/net/supported-document-formats/
[5]: https://downloads.groupdocs.com/conversion
[6]: https://www.nuget.org/packages/groupdocs.conversion
[7]: https://apireference.groupdocs.com/conversion/net/groupdocs.conversion/converter
[8]: https://apireference.groupdocs.com/conversion/net/groupdocs.conversion.options.convert/dataconvertoptions
[9]: https://apireference.groupdocs.com/conversion/net/groupdocs.conversion/converter/methods/convert/index
[10]: https://purchase.groupdocs.com/temporary-license
[11]: https://docs.groupdocs.com/conversion/net/
[12]: https://github.com/groupdocs-conversion
[13]: https://forum.groupdocs.com/
[14]: https://blog.groupdocs.com/2021/06/18/convert-json-and-csv-in-csharp/
[15]: https://blog.groupdocs.com/2021/08/18/convert-excel-xls-xlsx-and-csv-in-csharp/


