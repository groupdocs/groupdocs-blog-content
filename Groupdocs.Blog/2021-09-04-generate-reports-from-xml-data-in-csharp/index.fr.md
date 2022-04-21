---
title: "Générer des rapports à partir de données XML en C#"
date: Sat, 04 Sep 2021 17:18:55 +0000
draft: false
url: /fr/2021/09/04/generate-reports-from-xml-data-in-csharp/
author: 'Shoaib Khan'
summary: "**XML** est un langage auto-descriptif recommandé par le W3C, conçu pour stocker et transporter des données. Un développeur peut changer le format XML en n'importe quel autre meilleur format lisible par l'homme comme un document PDF ou MS Word dans l'application .NET. Cet article explique comment convertir des données XML en rapports PDF et MS Word à l'aide de C# à l'aide de modèles simples."
tags: ['Convert XML to DOCX in CSharp', 'Convert XML to PDF in CSharp', 'Generate PDF Report from XML', 'generate reports in csharp', 'XML to DOCX in CSharp', 'XML to PDF in CSharp']
categories: ['GroupDocs.Assembly Product Family']
---

**XML** est un langage auto-descriptif recommandé par le W3C, conçu pour stocker et transporter des données. Un développeur peut changer le format XML en n'importe quel autre meilleur format lisible par l'homme comme un document PDF ou MS Word dans l'application .NET. Cet article explique **comment convertir des données XML en rapports PDF et MS Word à l'aide de C#** via des modèles simples.



{{< figure align=center src="images/xml-to-pdf-word-report-in-csharp.jpg" alt="Rapport XML vers PDF en C#">}}


Les sujets suivants sont abordés ci-dessous :

* [API .NET pour la génération de rapports][1]
* [Générer un rapport PDF à partir de données XML à l'aide de C#][2]
* [Générer un rapport MS Word DOC/DOCX à partir de données XML à l'aide de C#][3]

## API .NET de génération de rapports - XML vers PDF et WORD {#generate-report-dotnet-api}

[GroupDocs.Assembly pour .NET][4] est l'API permettant d'automatiser la génération de rapports à partir des données **XML** à l'aide du modèle **DOCX** ou **TXT**. De plus, il prend en charge ** JSON, CSV ** et d'autres sources de données pour convertir les données en rapports de différents formats de fichiers.

Vous pouvez télécharger le programme d'installation **DLLs** ou **MSI** à partir de la [section téléchargements][5] ou installer l'API dans votre application .NET via [NuGet][6].

```
PM> Install-Package GroupDocs.Assembly
```

## Générer un rapport PDF à partir de données XML en C# {#xml-to-pdf-report-in-csharp}

3 étapes simples vous amèneront à convertir les données XML dans le rapport formaté au format PDF.

1. Chargez votre source de données XML.
2. Définissez le modèle en fonction des données XML chargées.
3. Enfin, fournissez une source de données XML et un modèle à une méthode de génération de rapport.

### Données XML

Les exemples de données XML suivants sont utilisés pour les convertir en rapport PDF. Il contient les données des gestionnaires et de leurs clients respectifs avec quelques détails supplémentaires.

```
<Managers>
	<Manager>
		<Name>John Smith</Name>
		<Contract>
			<Client>
				<Name>A Company</Name>
			</Client>
			<Price>1200000</Price>
		</Contract>
		<Contract>
		...
		</Contract>
		...
	</Manager>
	<Manager>
		<Name>Tony Anderson</Name>
		...
	</Manager>
	...
</Managers>
```

### Modèle

Définissez le modèle au format TXT ou DOCX en fonction de vos données XML source. J'utilise le modèle mentionné ci-dessous qui est créé selon les données XML des gestionnaires mentionnées ci-dessus. Cela obligera le générateur de rapports à itérer sur les gestionnaires et leurs clients respectifs. Une fois le modèle terminé, vous avez presque terminé. Vous pouvez utiliser le code ci-dessous pour la génération de votre rapport.

```
<<foreach \[in managers\]>>Manager: <<\[Name\]>>
Contracts:
<<foreach \[in Contract\]>>- <<\[Client.Name\]>> ($<<\[Price\]>>)
<</foreach>>
<</foreach>>
```

### Étapes C# pour générer un rapport PDF à partir de XML

Les étapes suivantes vous permettent d'automatiser la génération de rapports PDF à partir de vos données XML selon votre modèle défini.

* Définissez le fichier de données XML, le fichier de modèle de texte et les fichiers de rapport de sortie PDF.
* Instanciez [XMLDataSoure][7] avec le fichier de données XML.
* Créez [DataSourceInfo][8] avec une source de données XML définie.
* Appelez la méthode [AssembleDocument][9] pour générer le rapport PDF.

Le code suivant implémente les étapes ci-dessus et génère un PDF à partir de la source de données XML à l'aide de C#.

```
// Générer un rapport PDF à partir de données XML à l'aide du modèle TXT dans CSharp
// Définissez la source de données, le modèle et les fichiers de rapport de sortie.
string xmlDataSource = @"dataPath/Managers.xml";
string templateFilePath = @"templatePath/xml-template.txt";
string reportFilePath = @"reportsPath/xml-to-pdf-report.pdf";
// Charger la source de données XML
XmlDataSource dataSource = new XmlDataSource(xmlDataSource);
// Assembler un document pour générer un PDF
DocumentAssembler assembler = new DocumentAssembler();
assembler.AssembleDocument(templateFilePath, reportFilePath, new DataSourceInfo(dataSource, "managers"));
```

## Générer un rapport MS Word à partir de données XML en C# {#xml-to-word-report-in-csharp}

Dans le même esprit, vous pouvez également créer le rapport au format MS Word DOC/DOCX en utilisant les mêmes données XML. Il n'y aura aucune différence dans le code de celui dont nous avons discuté ci-dessus, sauf que vous devez changer le nom du fichier de sortie.

* Charger le fichier de données XML.
* Définition du modèle au format TXT ou DOCX.
* Définissez le format du document de rapport de sortie sur DOCX.
* Fournissez le fichier de données XML, le modèle et le chemin du fichier de sortie à [DocumentAssembler][10] pour convertir le XML en DOCX.

Le code suivant convertit le XML et génère le fichier DOCX à l'aide du modèle défini à l'aide de C#.

```
// Générer un rapport MS Word à partir de données XML à l'aide d'un modèle de texte dans CSharp
// Définissez la source de données, le modèle et les fichiers de rapport de sortie.
string xmlDataSource = @"dataPath/Managers.xml";
string templateFilePath = @"templatePath/xml-template.txt";
string reportFilePath = @"reportsPath/xml-to-word-report.docx";
// Charger la source de données XML
XmlDataSource dataSource = new XmlDataSource(xmlDataSource);
// Assembler un document pour générer un rapport Word
DocumentAssembler assembler = new DocumentAssembler();
assembler.AssembleDocument(templateFilePath, reportFilePath, new DataSourceInfo(dataSource, "managers"));
```

## Obtenez une licence API gratuite

Vous pouvez [obtenir une licence temporaire gratuite][11] afin d'utiliser l'API sans les limitations d'évaluation.

## Conclusion

En résumé, vous avez appris à convertir les données XML au format PDF sous forme de rapport en utilisant C# avec l'application .NET. De plus, nous avons discuté de la génération de rapports au format DOC/DOCX à partir du même XML en utilisant le modèle. Après avoir lu cette série de publications sur la génération de rapports ; Générez des rapports PDF et MS Word à partir de **[JSON][12]**, **[CSV][13]**, **XML**, vous pouvez développer votre propre application .NET de création de rapports.

Pour en savoir plus sur GroupDocs.Assembly, les options et les exemples, consultez la [documentation][14] et le référentiel [GitHub][15]. Pour toute autre question, contactez-nous via le [forum][16].

## Voir également

* [Convertir des données JSON en PDF ou en rapport Word à l'aide de C#][17]
* [Transformer les données CSV en PDF ou en rapport Word à l'aide de C#][18]







[1]: #generate-report-dotnet-api
[2]: #xml-to-pdf-report-in-csharp
[3]: #xml-to-word-report-in-csharp
[4]: https://products.groupdocs.com/assembly/net/
[5]: https://downloads.groupdocs.com/assembly
[6]: https://www.nuget.org/packages/groupdocs.assembly
[7]: https://apireference.groupdocs.com/assembly/net/groupdocs.assembly.data/xmldatasource
[8]: https://apireference.groupdocs.com/assembly/net/groupdocs.assembly/datasourceinfo
[9]: https://apireference.groupdocs.com/assembly/net/groupdocs.assembly/documentassembler/methods/assembledocument/index
[10]: https://apireference.groupdocs.com/assembly/net/groupdocs.assembly/documentassembler
[11]: https://purchase.groupdocs.com/temporary-license
[12]: https://blog.groupdocs.com/2021/03/20/generate-reports-from-json-data-in-csharp/
[13]: https://blog.groupdocs.com/2021/08/15/generate-reports-from-csv-data-in-csharp/
[14]: https://docs.groupdocs.com/assembly/net/
[15]: https://github.com/groupdocs-assembly
[16]: https://forum.groupdocs.com/c/assembly
[17]: https://blog.groupdocs.com/2021/03/20/generate-reports-from-json-data-in-csharp/
[18]: https://blog.groupdocs.com/2021/08/15/generate-reports-from-csv-data-in-csharp/


