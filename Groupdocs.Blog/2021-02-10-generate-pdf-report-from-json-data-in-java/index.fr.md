---
title: "Générer des rapports à partir de données JSON en Java"
date: Wed, 10 Feb 2021 18:40:00 +0000
draft: false
url: /fr/2021/02/10/generate-pdf-report-from-json-data-in-java/
author: 'Shoaib Khan'
summary: 'JSON is a formatted and readable data interchange format to transmit data with attributes. However, the large data in JSON format is not very presentable and easily understandable. We mostly need to convert the large JSON data into a presentable format. This article will guide you to **convert JSON data into PDF report in Java** using a simple template.

[Continuer la lecture...][1]'
tags: ['Convert JSON to PDF in Java', 'Generate PDF report from JSON', 'Generate PDF Report in Java', 'JSON to PDF using Template in Java']
categories: ['GroupDocs.Assembly Product Family']
---

JSON est un format d'échange de données formaté et lisible pour transmettre des données avec des attributs. Cependant, les données volumineuses au format JSON sont peu présentables et facilement compréhensibles. Nous devons principalement convertir les grandes données JSON dans un format présentable. Cet article vous guidera pour **convertir des données JSON en rapports PDF et MS Word en Java** à l'aide d'un modèle simple.

## API Java de génération de rapports

J'utiliserai l'API [GroupDocs.Assembly for Java][2] pour générer des rapports à partir des données et du modèle **JSON** fournis au format **DOCX** et **TXT**. Il prend également en charge la génération automatique de rapports dans plusieurs formats à partir de sources de données **CSV, XML**.

### Télécharger ou configurer

Vous pouvez télécharger le fichier **JAR** à partir de la [section téléchargements][3], ou simplement obtenir les configurations du référentiel et des dépendances pour le pox.xml de vos applications Java **basées sur maven**.

```
<repository>
	<id>GroupDocsJavaAPI</id>
	<name>GroupDocs Java API</name>
	<url>http://repository.groupdocs.com/repo/</url>
</repository>
```
```
<dependency>
        <groupId>com.groupdocs</groupId>
        <artifactId>groupdocs-assembly</artifactId>
        <version>21.1</version> 
</dependency>
```

## Générer un rapport PDF à partir de données JSON en Java

Passons rapidement aux étapes qui vous amèneront à convertir les données JSON en rapport PDF formaté.

* Obtenir la source de données JSON
* Définir le modèle en fonction des données JSON
* Fournir une source de données JSON et un modèle à un code Java simple pour la génération de rapports.



{{< figure align=center src="images/json-to-pdf-report-in-java.jpg" alt="Rapport JSON en PDF en Java">}}


### Données JSON

Pour la génération de rapports PDF, j'utiliserai les exemples de données JSON suivants des gestionnaires et de leurs clients et détails respectifs.

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

Définissez le modèle suivant au format TXT ou DOCX. Cela permettra d'itérer sur les gestionnaires et leurs clients respectifs et leurs détails. Après cela, vous pouvez passer au code pour la génération de rapports.

```
<<foreach [in managers]>>Manager: <<[Name]>>
Contracts:
<<foreach [in Contract]>>- <<[Client.Name]>> ($<<[Price]>>)
<</foreach>>
<</foreach>>
```

### Étapes Java pour générer un rapport PDF à partir de JSON

Les étapes suivantes et le code Java permettent la conversion automatique des données JSON en rapport PDF selon le modèle défini.

* Définissez les chemins d'accès au fichier de données JSON, au fichier de modèle .txt et au fichier de rapport de sortie PDF.
* Instanciez [JsonDataSoure][4] avec le fichier de données JSON.
* Créez [DataSourceInfo][5] avec JsonDataSource défini.
* Appelez la méthode _**assembleDocument**_ de la classe [DocumentAssembler][6] pour générer le rapport PDF à partir des données JSON fournies et du modèle défini.

```
// Générer un rapport PDF à partir de données JSON à l'aide d'un modèle TXT en Java avec l'API GroupDocs.Assembly
// Définissez la source de données, le modèle et les fichiers de rapport de sortie.
String jsonFilePath = "dataPath/ManagerData.json";
String templateFilePath = "templatePath/template.txt";
String reportFilePath = "reportsPath/reportFromJSON.pdf";				
// Instancier la source de données JSON
JsonDataSource datasource= new JsonDataSource(jsonFilePath);			  
DataSourceInfo dataSourceInfo = new DataSourceInfo(datasource,"managers");
// Générer un rapport
DocumentAssembler assembler = new DocumentAssembler();
assembler.assembleDocument(templateFilePath,reportFilePath,dataSourceInfo);
```

## Générer un rapport MS Word à partir de données JSON en Java

De même, comme pour la génération de rapport PDF ci-dessus, vous pouvez facilement créer le rapport DOCX en :

* Définition du même modèle au format DOCX.
* Définissez le format du document de rapport de sortie sur DOCX.
* Le reste du code restera le même pour générer un rapport MS Word DOCX à partir des données JSON.

```
// Générer un rapport Word à partir de données JSON à l'aide du modèle DOCX en Java avec l'API GroupDocs.Assembly
// Définissez la source de données, le modèle et les fichiers de rapport de sortie.
String jsonFilePath = "dataPath/ManagerData.json";
String templateFilePath = "templatePath/template.docx";
String reportFilePath = "reportsPath/reportFromJSON.docx";			
// Instancier la source de données JSON
JsonDataSource datasource= new JsonDataSource(jsonFilePath);			  
DataSourceInfo dataSourceInfo = new DataSourceInfo(datasource,"managers");
// Générer un rapport
DocumentAssembler assembler = new DocumentAssembler();
assembler.assembleDocument(templateFilePath,reportFilePath,dataSourceInfo);
```

Pour plus de détails, d'options et d'exemples, vous pouvez consulter les référentiels [documentation][7] et [GitHub][8]. En cas de questions supplémentaires et d'ambiguïtés, contactez le support gratuit sur le [forum][9].

## Conclusion

J'espère que vous vous sentirez à l'aise pour créer votre propre application basée sur Java pour générer des rapports en convertissant les données JSON au format PDF. De même, vous pouvez générer des rapports dans d'autres formats comme DOCX en utilisant d'autres sources de données comme CSV et XML.

## Voir également

* [Générer des rapports à partir de données JSON en C#][10]







[1]: https://blog.groupdocs.com/2021/02/10/generate-pdf-report-from-json-data-in-java
[2]: https://products.groupdocs.com/assembly/java
[3]: https://downloads.groupdocs.com/assembly/java
[4]: https://apireference.groupdocs.com/assembly/java/com.groupdocs.assembly/JsonDataSource
[5]: https://apireference.groupdocs.com/assembly/java/com.groupdocs.assembly/DataSourceInfo
[6]: https://apireference.groupdocs.com/assembly/java/com.groupdocs.assembly/DocumentAssembler
[7]: https://docs.groupdocs.com/assembly/java/
[8]: https://github.com/groupdocs-assembly/GroupDocs.Assembly-for-Java
[9]: https://forum.groupdocs.com/c/assembly
[10]: https://blog.groupdocs.com/2021/03/20/generate-reports-from-json-data-in-csharp/


