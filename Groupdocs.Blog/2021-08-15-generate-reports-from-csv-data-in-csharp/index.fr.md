---
title: "Générer des rapports à partir de données CSV à l'aide de C#"
date: Sun, 15 Aug 2021 10:50:32 +0000
draft: false
url: /fr/2021/08/15/generate-reports-from-csv-data-in-csharp/
aliases:
- /2019/10/21/generate-reports-from-csv-xml-in-csharp/
- /2019/10/21/generate-reports-from-csv-json-xml/
- /2019/10/21/generate-reports-from-csv-json-xml-in-csharp/
- /2019/10/21/generate-reports-from-csv-data-source/
- /2019/10/21/generate-reports-from-csv-data-source-in-groupdocs.assembly-for-.net-19.10/
author: 'Shoaib Khan'
summary: "Les fichiers CSV ([Comma Separated Values][1] sont largement utilisés pour l'échange de données entre les applications. Lorsque vous souhaitez que ces données soient traduites en informations présentables et significatives, vous devez les convertir dans un autre format. Dans l'un de nos articles, nous avons vu [comment convertir des données CSV dans des rapports à l'aide de Java][2].Cet article vous guidera pour **convertir des données CSV en rapports PDF et MS Word DOC/DOCX à l'aide de C#** à l'aide d'un modèle simple."
tags: ['Convert CSV to PDF in CSharp', 'CSV to PDF using template', 'CSV to Word Report in CSharp', 'Generate PDF report from CSV', 'Generate Reports', 'generate reports in csharp']
categories: ['GroupDocs.Assembly Product Family']
---

Les fichiers CSV ([Comma Separated Values][3] sont largement utilisés pour l'échange de données entre les applications. Lorsque vous souhaitez que ces données soient traduites en informations présentables et significatives, vous devez les convertir dans un autre format. Dans l'un de nos messages, nous avons vu [comment convertir des données CSV dans des rapports à l'aide de Java][4].Cet article vous guidera pour **convertir des données CSV en rapports PDF et MS Word DOC/DOCX à l'aide de C#** à l'aide d'un modèle simple.

Les sujets suivants sont traités ci-dessous :

* [API .NET de génération de rapports][5]
* [Générer un rapport PDF à partir de données CSV][6]
* [Générer un rapport MS Word à partir de données CSV][7]

## API .NET de génération de rapports {#report-generator-dotnet-api}

[GroupDocs.Assembly][8] fournit l'API de création de rapports .NET pour automatiser la génération de rapports. Dans cet article, j'ai utilisé [GroupDocs.Assembly pour .NET][9] pour générer des rapports à partir des données **CSV** sélectionnées et d'un modèle de format **TXT**. Il prend également en charge plusieurs sources de données telles que **JSON, XML**, ainsi que des fichiers **MS Word**, **Excel** et **PowerPoint** en tant que fichiers de données.

Vous pouvez télécharger le programme d'installation **DLLs** ou **MSI** à partir de la [section téléchargements][10] ou installer l'API dans votre application .NET via [NuGet][11].

```
PM> Install-Package GroupDocs.Assembly
```

## Générer un rapport PDF à partir de données CSV en C# {#csv-to-pdf-report-csharp}

Commençons par transformer les données séparées par des virgules en un PDF présentable. Les étapes suivantes vous guideront pour convertir les données CSV en un rapport PDF formaté.

* Charger la source de données CSV.
* Définir le modèle en fonction des données CSV.
* Fournir une source de données CSV et un modèle à une méthode simple pour générer un rapport PDF.



{{< figure align=center src="images/csv-to-pdf-word-report-in-csharp.jpg" alt="Rapport CSV en PDF en C#">}}


### Données CSV

Pour obtenir le rapport PDF, j'utiliserai les exemples de données CSV suivants de différentes personnes, ainsi que leurs données respectives d'âge et de date de naissance.

```
Name,Age,Birth  
John Doe,32,4/1/1989 16:00  
Jane Doe,29,1/31/1992 7:00  
John Smith,53,3/8/1968 13:00
```

### Modèle

La prochaine étape serait de définir le modèle au format TXT ou DOCX. Voici le modèle utilisé dans cet exemple et qui permet d'itérer la liste des personnes avec leurs détails.

```
<<foreach \[in persons\]>>Name: <<\[Name\]>>, Age: <<\[Age\]>>, Date of Birth: <<\[Birth\]:"dd.MM.yyyy">>
<</foreach>>
Average age: <<\[persons.Average(p => p.Age)\]>>
```

### Étapes pour générer un rapport PDF à partir de CSV en C#

Les étapes suivantes guident la conversion des données CSV en un rapport PDF selon le modèle défini à l'aide de C# avec l'API de création de rapports .NET.

* Définissez le fichier de données CSV, le fichier de modèle et les chemins du fichier de sortie PDF.
* Instanciez [CsvDataSoure][12] avec le fichier de données CSV et les options de chargement.
* Créez [DataSourceInfo][13] avec la source de données définie.
* À l'aide de [DocumentAssembler][14], appelez la méthode [AssembleDocument][15] avec le fichier modèle défini, le fichier de sortie et DataSourceInfo pour obtenir le rapport PDF en sortie.

Le code suivant montre comment convertir des données CSV en rapport PDF en C#.

```
// Générer un rapport PDF à partir de données CSV à l'aide d'un modèle TXT en C# avec l'API GroupDocs.Assembly
// Définissez la source de données, le modèle et les fichiers de rapport de sortie.
string csvDataSource = @"path/person.csv";
string templateFilePath = @"path/csv-template.txt";
string reportFilePath = @"path/csv-to-pdf-report.pdf";

// Charger la source de données CSV
CsvDataSource dataSource = new CsvDataSource(csvDataSource, new CsvDataLoadOptions(true));

// Générer un rapport au format PDF
DocumentAssembler assembler = new DocumentAssembler();
assembler.AssembleDocument(templateFilePath, reportFilePath, new DataSourceInfo(dataSource, "persons"));
```

## Générer un rapport MS Word à partir de données CSV en C# {#csv-to-docx-report-java}

Si vous souhaitez une modification manuelle dans le rapport généré automatiquement, vous pouvez également obtenir la sortie sous forme de document MS Word. Le processus sera très similaire à la génération de rapport PDF ci-dessus. Les étapes suivantes vous guideront pour générer le rapport DOC/DOCX à partir des données CSV :

* Charger les données CSV à partir du fichier.
* Définition du modèle au format TXT ou DOCX.
* Définissez le format du document de rapport de sortie sur DOC/DOCX.
* Appelez la méthode [AssembleDocument][16] pour générer un rapport MS Word DOCX à partir des données CSV.

Le code suivant montre comment convertir des données CSV en un rapport DOCX à l'aide de C#.

```
// Générer un rapport Word DOCX à partir de données CSV à l'aide d'un modèle TXT en C# avec l'API GroupDocs.Assembly
// Définissez la source de données, le modèle et les fichiers de rapport de sortie.
string csvDataSource = @"path/person.csv";
string templateFilePath = @"path/csv-template.txt";
string reportFilePath = @"path/csv-to-pdf-report.docx";

// Charger la source de données CSV
CsvDataSource dataSource = new CsvDataSource(csvDataSource, new CsvDataLoadOptions(true));

// Générer un rapport au format DOCX
DocumentAssembler assembler = new DocumentAssembler();
assembler.AssembleDocument(templateFilePath, reportFilePath, new DataSourceInfo(dataSource, "persons"));
```

## Obtenez une licence API gratuite

Vous pouvez [obtenir une licence temporaire gratuite][17] afin d'utiliser l'API sans les limitations d'évaluation.

## Conclusion

Pour conclure, vous avez appris à convertir les données CSV en rapports PDF et MS Word à l'aide de C#. Vous devez maintenant être sûr de créer votre propre application de génération de rapports .NET en convertissant les données CSV au format PDF. De même, vous pouvez également générer des rapports à l'aide d'autres sources de données telles que JSON et XML.

Pour en savoir plus sur l'API, vous pouvez consulter la [documentation][18] et le référentiel [GitHub][19]. En cas de questions supplémentaires et d'ambiguïtés, contactez le support gratuit sur le [forum][20].

## Voir également

* [Générer des rapports à partir de données JSON à l'aide de C#][21]
* [Générer des rapports à partir de données CSV à l'aide de Java][22]







[1]: https://docs.fileformat.com/spreadsheet/csv/)
[2]: https://blog.groupdocs.com/2021/07/07/generate-reports-from-csv-data-in-java/
[3]: https://docs.fileformat.com/spreadsheet/csv/)
[4]: https://blog.groupdocs.com/2021/07/07/generate-reports-from-csv-data-in-java/
[5]: #report-generator-dotnet-api
[6]: #csv-to-pdf-report-csharp
[7]: #csv-to-docx-report-java
[8]: https://products.groupdocs.com/assembly/java
[9]: https://products.groupdocs.com/assembly/net/
[10]: https://downloads.groupdocs.com/assembly/net
[11]: https://www.nuget.org/packages/groupdocs.assembly
[12]: https://apireference.groupdocs.com/net/assembly/groupdocs.assembly.data/csvdatasource
[13]: https://apireference.groupdocs.com/assembly/net/groupdocs.assembly/datasourceinfo
[14]: https://apireference.groupdocs.com/assembly/net/groupdocs.assembly/documentassembler
[15]: https://apireference.groupdocs.com/assembly/net/groupdocs.assembly/documentassembler/methods/assembledocument/index
[16]: https://apireference.groupdocs.com/assembly/net/groupdocs.assembly/documentassembler/methods/assembledocument/index
[17]: https://purchase.groupdocs.com/temporary-license
[18]: https://docs.groupdocs.com/assembly/net/
[19]: https://github.com/groupdocs-assembly
[20]: https://forum.groupdocs.com/c/assembly
[21]: https://blog.groupdocs.com/2021/03/20/generate-reports-from-json-data-in-csharp/
[22]: https://blog.groupdocs.com/2021/07/07/generate-reports-from-csv-data-in-java/


