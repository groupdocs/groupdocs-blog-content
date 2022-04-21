---
title: "Générer des rapports à partir de données CSV en Java"
date: Wed, 07 Jul 2021 14:26:55 +0000
draft: false
url: /fr/2021/07/07/generate-reports-from-csv-data-in-java/
aliases:
- /2019/10/30/generate-reports-from-csv-xml-in-java/
- /2019/10/30/build-reports-using-csv-data-sources-in-groupdocs-assembly-for-java/
author: 'Shoaib Khan'
summary: "Le [Comma Separated Values][1] (CSV) est un format de fichier pour stocker les données sous forme de texte brut où les valeurs sont séparées par des virgules. CSV est largement utilisé pour échanger des données entre les applications. En tant que développeur, nous devons souvent convertir les grandes données CSV dans un format présentable. Cet article vous guidera pour **convertir des données CSV en rapports PDF et MS Word en Java** à l'aide d'un modèle simple."
tags: ['Convert CSV to PDF in Java', 'CSV to PDF using template', 'CSV to Word Report in Java', 'Generate PDF report from CSV', 'Generate PDF Report in Java', 'Generate Reports']
categories: ['GroupDocs.Assembly Product Family']
---

Le [Comma Separated Values][2] (CSV) est un format de fichier pour stocker les données sous forme de texte brut où les valeurs sont séparées par des virgules. CSV est largement utilisé pour échanger des données entre les applications. En tant que développeur, nous devons souvent convertir les grandes données CSV dans un format présentable. Cet article vous guidera pour **convertir des données CSV en rapports PDF et MS Word en Java** à l'aide d'un modèle simple.

Les sujets suivants sont traités ci-dessous :

* [API Java de génération de rapports][3]
* [Générer un rapport PDF à partir de données CSV][4]
* [Générer un rapport MS Word à partir de données CSV][5]

## API Java de génération de rapports {#report-generator-java-api}

[GroupDocs.Assembly pour Java][6] est l'API de génération de rapports que j'ai utilisée dans cet article pour générer des rapports à partir des données **CSV** sélectionnées et d'un modèle au format **TXT**. Il prend également en charge l'automatisation de la génération de rapports à partir de plusieurs sources de données telles que **JSON, XML**, ainsi que des fichiers **MS Word**, **Excel** et **PowerPoint** en tant que fichiers de données.

### Télécharger ou configurer

Vous pouvez télécharger le fichier **JAR** à partir de la [section téléchargements][7], ou simplement obtenir les configurations du référentiel et des dépendances pour le pox.xml de vos applications Java **basées sur maven**.

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
        <version>21.4</version> 
</dependency>
```

## Générer un rapport PDF à partir de données CSV en Java {#csv-to-pdf-report-java}

Commençons par la transformation des données en PDF présentable. Les étapes suivantes vous amèneront à convertir les données CSV en un rapport formaté au format PDF.

* Charger la source de données CSV
* Définir le modèle en fonction des données CSV
* Fournir une source de données CSV et un modèle à une méthode simple pour générer un rapport PDF.



{{< figure align=center src="images/csv-to-pdf-word-report-in-java.jpg" alt="Rapport CSV en PDF en Java">}}


### Données CSV

Pour la génération du rapport PDF, j'utiliserai les exemples de données CSV suivants de différentes personnes, ainsi que leurs âges et dates de naissance respectifs.

```
Name,Age,Birth  
John Doe,32,4/1/1989 16:00  
Jane Doe,29,1/31/1992 7:00  
John Smith,53,3/8/1968 13:00
```

### Modèle

Définissez le modèle suivant au format TXT ou DOCX. Cela permet d'itérer la liste des personnes avec leurs coordonnées. Après cela, vous pouvez passer au code pour la génération de rapport.

```
<<foreach \[in persons\]>>Name: <<\[Name\]>>, Age: <<\[Age\]>>, Date of Birth: <<\[Birth\]:"dd.MM.yyyy">>
<</foreach>>
Average age: <<\[persons.**average**(p => p.Age)\]>>
```

### Étapes Java pour générer un rapport PDF à partir de CSV

Les étapes suivantes expliquent la conversion automatique des données CSV en un rapport PDF selon le modèle défini.

* Définissez les chemins d'accès au fichier de données CSV, au fichier de modèle .txt et au fichier de rapport de sortie PDF.
* Instanciez [CsvDataSoure][8] avec le fichier de données CSV.
* Créez [DataSourceInfo][9] avec le CsvDataSource défini.
* Appelez la méthode _[assembleDocument][10]_ de la classe [DocumentAssembler][11] pour obtenir le rapport PDF généré.

Le code suivant montre comment convertir des données CSV en rapport PDF en Java.

```
// Générer un rapport PDF à partir de données CSV à l'aide d'un modèle TXT en Java avec l'API GroupDocs.Assembly
// Définissez la source de données, le modèle et les fichiers de rapport de sortie.
String csvDataSource = "dataPath/Person.csv";
String templateFilePath = "templatePath/template.txt";
String reportFilePath = "reportsPath/reportFromCSV.pdf";

// Source de données CSV chargée
CsvDataLoadOptions options = new CsvDataLoadOptions(true);
CsvDataSource datasource= new CsvDataSource(csvDataSource,options);
DataSourceInfo dataSourceInfo = new DataSourceInfo(datasource,"persons");

// Générer un rapport
DocumentAssembler assembler = new DocumentAssembler();
assembler.assembleDocument(templateFilePath, reportFilePath, dataSourceInfo);
```

## Générer un rapport MS Word à partir de données CSV en Java {#csv-to-docx-report-java}

Il est très similaire à la génération de rapport PDF ci-dessus, vous pouvez facilement créer le rapport MS Word DOC/DOCX à partir des données CSV :

* Charger les données CSV à partir du fichier.
* Définition du modèle au format TXT ou DOCX.
* Définissez le format du document de rapport de sortie sur DOC/DOCX.
* Le reste du code restera le même pour générer un rapport MS Word DOCX à partir des données CSV.

Le code suivant montre comment convertir des données CSV en rapport DOCX en Java.

```
// Générer un rapport Word à partir de données CSV à l'aide d'un modèle TXT en Java avec l'API GroupDocs.Assembly
// Définissez la source de données, le modèle et les fichiers de rapport de sortie.
String csvDataSource = "dataPath/Person.csv";
String templateFilePath = "templatePath/template.txt";
String reportFilePath = "reportsPath/reportFromCSV.docx";

// Charger la source de données CSV
CsvDataLoadOptions options = new CsvDataLoadOptions(true);
CsvDataSource datasource= new CsvDataSource(csvDataSource,options);
DataSourceInfo dataSourceInfo = new DataSourceInfo(datasource,"persons");

// Générer un rapport
DocumentAssembler assembler = new DocumentAssembler();
assembler.assembleDocument(templateFilePath, reportFilePath, dataSourceInfo);
```

## Obtenez une licence API gratuite

Vous pouvez [obtenir une licence temporaire gratuite][12] afin d'utiliser l'API sans les limitations d'évaluation.

## Conclusion

En résumé, vous avez appris à convertir les données CSV en rapports PDF et MS Word en Java. J'espère que vous êtes maintenant à l'aise pour créer votre propre application basée sur Java pour générer des rapports en convertissant les données CSV au format PDF. De même, vous pouvez générer des rapports à l'aide de sources de données telles que JSON et XML.

Pour en savoir plus sur l'API, vous pouvez consulter la [documentation][13] et le référentiel [GitHub][14]. En cas de questions supplémentaires et d'ambiguïtés, contactez le support gratuit sur le [forum][15].

## Voir également

* [Générer des rapports à partir de données JSON à l'aide de Java][16]
* [Créer des rapports à partir de données CSV à l'aide de C#][17]
* [Générer des rapports à partir de données JSON à l'aide de C#][18]







[1]: https://docs.fileformat.com/spreadsheet/csv/
[2]: https://docs.fileformat.com/spreadsheet/csv/
[3]: #report-generator-java-api
[4]: #csv-to-pdf-report-java
[5]: #csv-to-docx-report-java
[6]: https://products.groupdocs.com/assembly/java
[7]: https://downloads.groupdocs.com/assembly/java
[8]: https://apireference.groupdocs.com/assembly/java/com.groupdocs.assembly/CsvDataSource
[9]: https://apireference.groupdocs.com/assembly/java/com.groupdocs.assembly/DataSourceInfo
[10]: https://apireference.groupdocs.com/assembly/java/com.groupdocs.assembly/DocumentAssembler#assembleDocument-java.lang.String-java.lang.String-com.groupdocs.assembly.DataSourceInfo...-
[11]: https://apireference.groupdocs.com/assembly/java/com.groupdocs.assembly/DocumentAssembler
[12]: https://purchase.groupdocs.com/temporary-license
[13]: https://docs.groupdocs.com/assembly/java/
[14]: https://github.com/groupdocs-assembly/GroupDocs.Assembly-for-Java
[15]: https://forum.groupdocs.com/c/assembly
[16]: https://blog.groupdocs.com/2021/02/10/generate-pdf-report-from-json-data-in-java/
[17]: https://blog.groupdocs.com/2021/08/15/generate-reports-from-csv-data-in-csharp/
[18]: https://blog.groupdocs.com/2021/03/20/generate-reports-from-json-data-in-csharp/


