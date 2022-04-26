---
title: "Convertir des documents en Excel XLS, XLSX en C#"
date: Tue, 13 Apr 2021 23:17:00 +0000
draft: false
url: /fr/2021/04/13/convert-document-to-excel-xls-xlsx-in-csharp/
aliases:
- /2019/10/23/convert-document-to-excel-xls-xlsx-with-csharp-api/
- /2019/10/23/convert-document-to-excel-xls-xlsx-in-csharp/
- /2019/10/23/convertir-un-document-en-excel-en-c/
author: 'Shoaib Khan'
summary: "If you have tabular data in PDF or Word documents format, you definitely need to convert it to Excel spreadsheets. This scenario becomes complex when there are many spreadsheets or multiple workbooks. You surely need to automate this procedure. In this article, we will see how to convert PDF to Excel and also how to convert Word documents to Excel spreadsheet programmatically in C# using .NET API."
tags: ['convert PDF to Excel in csharp', 'Convert Word to Excel in CSharp', 'document conversion', 'PDF to Excel in C#', 'Word to Excel in C#']
categories: ['GroupDocs.Conversion Product Family']
---

Si vous avez des données tabulaires au format PDF ou Word, vous devez absolument les convertir en feuilles de calcul Excel. Ce scénario devient complexe lorsqu'il existe de nombreuses feuilles de calcul ou plusieurs classeurs. Vous avez sûrement besoin d'automatiser cette procédure. Dans cet article, nous verrons comment convertir un PDF en Excel et également comment convertir des documents Word en feuilles de calcul Excel par programme en C # à l'aide de l'API .NET.



{{< figure align=center src="images/pdf-word-to-xls-in-csharp.jpg" alt="Convertir Word et PDF en Excel en C#">}}


Voici les sujets abordés brièvement dans cet article :

* API .NET - Convertir des documents en feuilles de calcul
* Convertir PDF en Excel
* Convertir Word en Excel
* Conversion PDF ou Word en feuille de calcul avec plus d'options

## API .NET - Convertir en formats de feuille de calcul

Dans cet article, j'utiliserai [GroupDocs.Conversion pour .NET][2] pour convertir des documents PDF et Word en feuilles de calcul à l'aide de C#. C'est l'API riche en fonctionnalités qui permet les conversions de documents et d'images dans de nombreux formats de fichiers. Pour mettre en évidence certains formats, l'API prend en charge les documents de traitement de texte, les feuilles de calcul, les présentations, les dessins AutoCAD, les livres électroniques, les PDF, les fichiers de courrier électronique, les pages Web, les images, les fichiers Photoshop et de nombreux autres formats de document.

Téléchargez le programme d'installation **DLLs** ou **MSI** à partir de la [section téléchargements][3] ou installez l'API dans votre application .NET via [NuGet][4].

```
PM> Install-Package GroupDocs.Conversion
```

## Convertir PDF en Excel en C#

Voici l'étape pour convertir un document PDF en une feuille de calcul Excel.

* Chargez le fichier PDF à l'aide de la classe [Converter][5].
* Initialiser l'option de conversion à l'aide de la classe [SpreadsheetConvertOptions][6].
* Appelez la méthode [Convert][7] de la classe Converter avec l'option.

L'exemple de code suivant montre comment convertir un fichier PDF au format Excel XLSX à l'aide de C#.

```
// Convertir un document PDF en feuille de calcul Excel en C#
using (Converter converter = new Converter("document.pdf"))
{
    SpreadsheetConvertOptions options = new SpreadsheetConvertOptions();
    converter.Convert("outputpath/convertedSpreadsheet.xlsx", options);
}
```

## Convertir Word en Excel en C#

Vous pouvez convertir n'importe quel document Word en une feuille de calcul Excel de la même manière que nous avons converti le fichier PDF ci-dessus. Il suffit de fournir le bon fichier source à convertir en XLS ou XLSX.

Voici l'étape pour convertir un document Word au format DOC DOCX en une feuille de calcul Excel.

* Chargez le fichier Word à l'aide de la classe [Converter][8].
* Initialiser l'option de conversion à l'aide de la classe [SpreadsheetConvertOptions][9].
* Appelez la méthode [Convert][10] de la classe Converter avec l'option.

L'exemple de code suivant montre comment convertir un fichier DOC ou DOCX au format Excel XLSX à l'aide de C#.

```
// Convertir un document Word en feuille de calcul Excel en C#
using (Converter converter = new Converter("document.docx"))
{
    SpreadsheetConvertOptions options = new SpreadsheetConvertOptions();
    converter.Convert("outputpath/convertedSpreadsheet.xlsx", options);
}
```

## Conversion PDF ou Word en feuille de calcul avec plus d'options à l'aide de C #

Vous ne pouvez convertir qu'une partie des pages sélectionnées de votre document. L'API vous donne le privilège de convertir votre document avec différentes options qui incluent :

* Début du **numéro de page**.
* **Compte de pages** à convertir.
* **Pages spécifiques** pour la conversion.
* **Format** de conversion.
* **Mot de passe** pour protéger le fichier.
* **Zoom** pour l'agrandir ou le réduire.
* **Filigrane** sur le fichier du convertisseur.

Voici les étapes à suivre pour convertir certaines des pages d'un fichier PDF au format XLSX avec un zoom différent à l'aide de C#.

```
// Convertir la deuxième page du fichier PDF en Excel en C# avec quelques options
using (Converter converter = new Converter("document.pdf"))
{
    SpreadsheetConvertOptions options = new SpreadsheetConvertOptions
    {
        PageNumber = 2,
        PagesCount = 1,
        Format = SpreadsheetFileType.Xlsx,
        Zoom = 150
    };
    converter.Convert("outputpath/convertedSpreadsheet.xlsx", options);
}
```

Voici le fichier PDF et la feuille de calcul convertie en sortie à l'aide du code ci-dessus. Il a converti la deuxième page du fichier PDF au format XLSX.



{{< figure align=center src="images/pdf-to-xls-in-csharp.jpg" alt="Convertir PDF en Excel XLS XLSX par programme">}}


## Obtenez une licence API gratuite {#Get-a-Free-API-License}

Vous pouvez [obtenir une licence temporaire gratuite][11] afin d'utiliser l'API sans limitations d'évaluation.

## Conclusion

Dans cet article, vous avez appris à convertir des documents PDF et Word dans une feuille de calcul Excel à l'aide de C#. De plus, vous avez également vu comment nous pouvons convertir n'importe quelle partie du document avec des options telles que le zoom, le filigrane et la protection par mot de passe. Vous pouvez maintenant commencer à créer votre propre application de conversion de documents .NET bases ou intégrer la ou les fonctionnalités dans votre application existante.

Pour plus de détails, d'options et d'exemples, vous pouvez visiter la [documentation][12] et le référentiel [GitHub][13]. Pour toute autre question, contactez le support sur le [forum][14].

## Voir également

* [Convertir des dessins CAO en PDF en C#][15]
* [Convertir des présentations en PDF en C#][16]
* [Convertir des feuilles de calcul Excel en PDF à l'aide de C#][17]







[1]: https://blog.groupdocs.com/2021/04/13/convert-document-to-excel-xls-xlsx-in-csharp/
[2]: https://products.groupdocs.com/conversion/net
[3]: https://downloads.groupdocs.com/conversion/net
[4]: https://www.nuget.org/packages/groupdocs.conversion
[5]: https://apireference.groupdocs.com/conversion/net/groupdocs.conversion/converter
[6]: https://apireference.groupdocs.com/conversion/net/groupdocs.conversion.options.convert/spreadsheetconvertoptions
[7]: https://apireference.groupdocs.com/conversion/net/groupdocs.conversion/converter/methods/convert/index
[8]: https://apireference.groupdocs.com/conversion/net/groupdocs.conversion/converter
[9]: https://apireference.groupdocs.com/conversion/net/groupdocs.conversion.options.convert/spreadsheetconvertoptions
[10]: https://apireference.groupdocs.com/conversion/net/groupdocs.conversion/converter/methods/convert/index
[11]: https://purchase.groupdocs.com/temporary-license
[12]: https://docs.groupdocs.com/conversion/net
[13]: https://github.com/groupdocs-conversion
[14]: https://forum.groupdocs.com/
[15]: https://blog.groupdocs.com/2020/11/08/convert-cad-drawings-to-pdf-in-csharp/
[16]: https://blog.groupdocs.com/2020/03/05/convert-presentations-pptx-ppt-to-pdf-in-csharp/
[17]: https://blog.groupdocs.com/2021/11/14/convert-excel-spreadsheets-to-pdf-using-csharp/


