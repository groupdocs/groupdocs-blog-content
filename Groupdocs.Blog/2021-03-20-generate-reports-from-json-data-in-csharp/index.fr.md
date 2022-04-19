---
title: "Générer des rapports à partir de données JSON en C#"
date: Sat, 20 Mar 2021 10:45:45 +0000
draft: false
url: /fr/2021/03/20/generate-reports-from-json-data-in-csharp/
author: 'Shoaib Khan'
summary: "Cet article traite du problème de formatage des données JSON brutes dans un format de rapport présentable et facilement compréhensible dans l'application .NET. Nous allons **convertir les données JSON en rapports PDF et DOCX en C#** à l'aide de modèles simples."
tags: ['Convert JSON to PDF in CSharp', 'Generate PDF report from JSON', 'Generate PDF Report in CSharp', 'JSON to PDF using Template in CSharp']
categories: ['GroupDocs.Assembly Product Family']
---

Cet article traite du problème de formatage des données JSON brutes dans un format de rapport présentable et facilement compréhensible dans l'application .NET. Nous allons **convertir les données JSON en rapports PDF et DOCX en C#** à l'aide de modèles simples.



{{< figure align=center src="images/json-to-pdf-or-word-report-in-csharp.jpg" alt="Générer un rapport PDF ou Word à partir de JSON dans CSharp">}}


## API .NET pour la génération de rapports

[GroupDocs.Assembly pour .NET][2] est l'API de génération de rapports et d'automatisation de documents pour les applications .NET. Il vous permet de générer des rapports à partir des données disponibles dans différents formats tels que **JSON**, **XML** ou **CSV** et le modèle dans de nombreux formats différents tels que document **Word**, **feuille de calcul Format **, **présentation** ou **texte**. Il prend également en charge de nombreuses fonctionnalités de formatage de rapport telles que **puces, listes numérotées, graphiques, tableaux, images, codes-barres**, etc.

Vous pouvez télécharger les DLL ou le programme d'installation MSI à partir de la [section des téléchargements][3] ou installer l'API dans votre application .NET via [NuGet][4].

```
PM> Install-Package GroupDocs.Assembly
```

## Générer un rapport PDF à partir de données JSON en C#

Commençons par les étapes qui vous amèneront à convertir les données JSON en rapport PDF formaté en C#.

* Obtenir la source de données JSON
* Définir le modèle en fonction des données JSON
* Fournir une source de données JSON et un modèle au code C # simple pour la génération de rapports.

### Données JSON

Tout d'abord, l'exemple de données JSON suivant est utilisé pour la génération du rapport PDF qui montre les gestionnaires et leurs clients et détails respectifs.

```
\[
	{
		"Name":"John Smith","Contract":\[
		{"Client":{"Name":"A Company"},"Price":1200000},
		{"Client":{"Name":"B Ltd."},"Price":750000},
		{"Client":{"Name":"C & D"},"Price":350000}\]
	},
	{
		"Name":"Tony Anderson","Contract":\[
		{"Client":{"Name":"E Corp."},"Price":650000},
		{"Client":{"Name":"F & Partners"},"Price":550000}\]
	},
	{
		"Name":"July James","Contract":\[
		{"Client":{"Name":"G & Co."},"Price":350000},
		{"Client":{"Name":"H Group"},"Price":250000},
		{"Client":{"Name":"I & Sons"},"Price":100000},
		{"Client":{"Name":"J Ent."},"Price":100000}\]
	}
\]
```

### Modèle

Deuxièmement, définissez le modèle suivant au format TXT, DOCX ou au format requis. Cela permet d'itérer les données des Managers et leurs Clients respectifs et leurs détails. Après cela, vous pouvez passer au code pour la génération de rapports.

```
<<foreach [in managers]>>Manager: <<[Name]>>
Contracts:
<<foreach [in Contract]>>- <<[Client.Name]>> ($<<[Price]>>)
<</foreach>>
<</foreach>>
```

### Étapes C# pour convertir le rapport JSON en PDF

Les étapes suivantes du code C# automatisent la conversion des données JSON en rapport PDF en fonction du modèle défini.

* Définissez les données JSON, le fichier modèle et les chemins du fichier de rapport de sortie PDF.
* Instanciez [JsonDataSoure][5] avec le fichier de données JSON.
* Créez [DataSourceInfo][6] avec JsonDataSource défini.
* Appelez la méthode _**AssembleDocument**_ de la classe [DocumentAssembler][7] pour générer le rapport PDF à partir des données JSON fournies et du modèle défini.

```
// Générer un rapport PDF à partir de données JSON à l'aide d'un modèle TXT en C# avec l'API GroupDocs.Assembly
// Définissez la source de données, le modèle et les fichiers de rapport de sortie.
const string strDataSource = "dataPath/ManagerData.json";
const string strDocumentTemplate = "templatePath/template.txt";
const string strDocumentReport = "reportsPath/reportFromJSON.pdf";
// Instancier la source de données JSON
JsonDataSource dataSource = new JsonDataSource(CommonUtilities.GetDataSourceDocument(strDataSource));
// Générer un rapport
DocumentAssembler assembler = new DocumentAssembler();
assembler.AssembleDocument(CommonUtilities.GetSourceDocument(strDocumentTemplate),
    CommonUtilities.SetDestinationDocument(strDocumentReport),
    new DataSourceInfo(dataSource, "managers"));
```

Le code produira le rapport PDF comme indiqué dans la figure ci-dessus. Vous pouvez également tester et ci-dessus et des exemples similaires du [référentiel GitHub][8].

## Générer un rapport MS Word à partir de données JSON en C#

De même, comme pour générer le rapport PDF ci-dessus, vous pouvez créer le rapport DOCX en suivant ces étapes :

* Définition du même modèle au format DOCX.
* Définissez le format du document de rapport de sortie sur DOCX.
* Le reste du code restera le même pour générer un rapport MS Word DOCX à partir des données JSON.

```
// Générer un rapport Word à partir de données JSON à l'aide du modèle DOCX en C# avec l'API GroupDocs.Assembly
// Définissez la source de données, le modèle et les fichiers de rapport de sortie.
const string strDataSource = "dataPath/ManagerData.json";
const string strDocumentTemplate = "templatePath/template.docx";
const string strDocumentReport = "reportsPath/reportFromJSON.docx";
// Instancier la source de données JSON
JsonDataSource dataSource = new JsonDataSource(CommonUtilities.GetDataSourceDocument(strDataSource));
// Générer un rapport
DocumentAssembler assembler = new DocumentAssembler();
assembler.AssembleDocument(CommonUtilities.GetSourceDocument(strDocumentTemplate),
    CommonUtilities.SetDestinationDocument(strDocumentReport),
    new DataSourceInfo(dataSource, "managers"));
```

Pour plus de détails, d'options et d'exemples, consultez la [documentation][9] et le référentiel [GitHub][10]. Pour toute autre question, contactez l'assistance gratuite sur le [forum][11].

## Conclusion

Dans cet article, vous avez appris à convertir vos données JSON en rapport PDF dans votre application .NET à l'aide de C#. De plus, vous pouvez générer des rapports dans d'autres formats comme DOCX en utilisant d'autres sources de données comme CSV et XML. J'espère que vous vous sentirez à l'aise pour commencer à créer votre application .NET de génération de rapports.

## Voir également

* [Générer des rapports à partir de données JSON en Java][12]







[1]: https://blog.groupdocs.com/2021/03/20/generate-reports-from-json-data-in-csharp/
[2]: https://products.groupdocs.com/assembly/net
[3]: https://downloads.groupdocs.com/assembly/net
[4]: https://www.nuget.org/packages/groupdocs.assembly
[5]: https://apireference.groupdocs.com/assembly/net/groupdocs.assembly.data/jsondatasource
[6]: https://apireference.groupdocs.com/assembly/net/groupdocs.assembly/datasourceinfo
[7]: https://apireference.groupdocs.com/assembly/net/groupdocs.assembly/documentassembler
[8]: https://github.com/groupdocs-assembly/GroupDocs.Assembly-for-.NET
[9]: https://docs.groupdocs.com/assembly/net
[10]: https://github.com/groupdocs-assembly/GroupDocs.Assembly-for-.NET
[11]: https://forum.groupdocs.com/c/assembly
[12]: https://blog.groupdocs.com/2021/02/10/generate-pdf-report-from-json-data-in-java/


