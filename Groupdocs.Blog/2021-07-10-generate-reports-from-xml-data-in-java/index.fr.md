---
title: "Générer des rapports à partir de données XML en Java"
date: Sat, 10 Jul 2021 10:01:00 +0000
draft: false
url: /fr/2021/07/10/generate-reports-from-xml-data-in-java/
author: 'Shoaib Khan'
summary: "**XML** est un langage **M**arkup **L**e**X**tensif qui est autodescriptif, recommandé par le W3C et conçu pour stocker et transporter des données. Après avoir reçu les données au format XML, en tant que développeur, vous pouvez les convertir dans n'importe quel autre meilleur format lisible par l'homme, comme un document PDF ou MS Word. Cet article vous guidera pour convertir des données XML en rapports PDF et MS Word en Java à l'aide de modèles simples."
tags: ['Convert XML to DOCX in Java', 'Convert XML to PDF in Java', 'Generate PDF Report from XML', 'Generate Reports in Java', 'XML to DOCX in Java', 'XML to PDF in Java']
categories: ['GroupDocs.Assembly Product Family']
---

**XML** est un langage **M**arkup **L**e**X**tensif qui est autodescriptif, recommandé par le W3C et conçu pour stocker et transporter des données. Après avoir reçu les données au format XML, en tant que développeur, vous pouvez les convertir dans n'importe quel autre meilleur format lisible par l'homme, comme un document PDF ou MS Word. Cet article vous guidera pour convertir des données XML en rapports PDF et MS Word en Java à l'aide de modèles simples.

Les sujets suivants sont abordés ci-dessous :

* [API Java pour la génération de rapports][1]
* [Rapport PDF à partir de données XML utilisant Java][2]
* [Rapport MS Word DOC/DOCX à partir de données XML utilisant Java][3]

## API Java de génération de rapports - XML vers PDF et WORD {#generate-report-java-api}

[GroupDocs.Assembly][4] fournit une API Java pour automatiser la génération de rapports à partir des données **XML** à l'aide du modèle **DOCX** ou **TXT**. Il prend également en charge ** JSON, CSV ** et d'autres sources de données pour convertir les données en rapports présentables de différents formats de fichiers.

### Télécharger ou configurer

Vous pouvez télécharger le fichier **JAR** à partir de la [section téléchargements][5], ou simplement obtenir les configurations du référentiel et des dépendances pour le pox.xml de vos applications Java **basées sur maven**.

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

## Générer un rapport PDF à partir de données XML en Java {#xml-to-pdf-report-in-java}

Passons rapidement aux étapes qui vous amèneront à convertir les données XML en rapport PDF formaté.

* Charger la source de données XML
* Définissez le modèle en fonction de vos données XML
* Fournir une source de données XML et un modèle à une méthode de génération de rapport.



{{< figure align=center src="images/xml-to-pdf-word-report-in-java.jpg" alt="Rapport XML en PDF en Java">}}


### Données XML

Pour la génération de rapport PDF, les exemples de données XML suivants sont utilisés. Il contient les données des gestionnaires et de leurs clients respectifs avec des détails.

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

Définissez le modèle suivant au format TXT ou DOCX. Cela permet une itération sur les gestionnaires et leurs clients respectifs. Après cela, utilisez le code mentionné ci-dessous pour la génération de rapport.

```
<<foreach \[in managers\]>>Manager: <<\[Name\]>>
Contracts:
<<foreach \[in Contract\]>>- <<\[Client.Name\]>> ($<<\[Price\]>>)
<</foreach>>
<</foreach>>
```

### Étapes Java pour générer un rapport PDF à partir de XML

Les étapes suivantes et le code permettent d'automatiser la génération de rapports PDF à partir des données XML selon le modèle défini.

* Définissez le fichier de données XML, le fichier de modèle de texte et les fichiers de rapport de sortie PDF.
* Instanciez [XMLDataSoure][6] avec le fichier de données XML.
* Créez [DataSourceInfo][7] avec une source de données XML définie.
* Appelez la méthode [assembleDocument][8] pour générer le rapport PDF.

Le code suivant implémente les étapes ci-dessus et génère un PDF à partir de la source de données XML en Java.

```
// Générer un rapport PDF à partir de données XML à l'aide d'un modèle TXT en Java
// Définissez la source de données, le modèle et les fichiers de rapport de sortie.
String xmlDataSource = "dataPath/Managers.xml";
String templateFilePath = "templatePath/template.txt";
String reportFilePath = "reportsPath/PDFreportFromXML.pdf";

// Charger la source de données XML
XmlDataSource datasource = new XmlDataSource(xmlDataSource);
DataSourceInfo dataSourceInfo = new DataSourceInfo(datasource,"managers");

// Assembler un document pour générer un PDF
DocumentAssembler assembler = new DocumentAssembler();
assembler.assembleDocument(templateFilePath, reportFilePath,dataSourceInfo);
```

## Générer un rapport MS Word à partir de données XML en Java {#xml-to-word-report-in-java}

De même, vous pouvez créer le rapport MS Word DOC/DOCX à partir des mêmes données XML en Java. Il n'y aura aucune différence, sauf pour changer le nom du fichier de sortie.

* Charger le fichier de données XML.
* Définition du modèle au format TXT ou DOCX.
* Définissez le format du document de rapport de sortie sur DOCX.
* Fournissez le fichier de données XML, le modèle et le chemin du fichier de sortie à DocumentAssembler pour convertir le XML en DOCX.

Le code suivant convertit le XML et génère le fichier DOCX à l'aide du modèle défini en Java.

```
// Générer un rapport MS Word à partir de données XML à l'aide d'un modèle de texte en Java
// Définissez la source de données, le modèle et les fichiers de rapport de sortie.
String xmlDataSource = "dataPath/Managers.xml";
String templateFilePath = "templatePath/template.docx";
String reportFilePath = "reportsPath/WordReportFromXML.docx";

//Instancier la source de données XML
XmlDataSource datasource = new XmlDataSource(xmlDataSource);
DataSourceInfo dataSourceInfo = new DataSourceInfo(datasource,"managers");

//Assembler le document 
DocumentAssembler assembler = new DocumentAssembler();
assembler.assembleDocument(templateFilePath, reportFilePath,dataSourceInfo);
```

## Obtenez une licence API gratuite

Vous pouvez [obtenir une licence temporaire gratuite][9] afin d'utiliser l'API sans les limitations d'évaluation.

## Conclusion

Pour conclure, vous avez appris à convertir vos données XML au format PDF sous forme de rapport en Java. De plus, vous avez vu la génération de rapport au format DOC/DOCX à partir du même XML en utilisant le modèle. Après avoir lu la série Générer des rapports PDF et MS Word à partir de [**JSON**][10], [**CSV**][11], **XML**, vous devriez être à l'aise pour créer votre propre générateur de rapports. Application Java.

De même, vous pouvez convertir de nombreuses autres sources de données en rapport. Pour plus de détails, d'options et d'exemples, vous pouvez consulter la [documentation][12] et le référentiel GitHub. En cas de questions supplémentaires, contactez-nous via le [forum][13].

## Voir également

* [Convertir des données JSON en PDF ou en rapport Word à l'aide de Java][14]
* [Transformer les données CSV en PDF ou en rapport Word à l'aide de Java][15]







[1]: #generate-report-java-api
[2]: #xml-to-pdf-report-in-java
[3]: #xml-to-word-report-in-java
[4]: https://products.groupdocs.com/assembly
[5]: https://downloads.groupdocs.com/assembly/java
[6]: https://apireference.groupdocs.com/assembly/java/com.groupdocs.assembly/XmlDataSource
[7]: https://apireference.groupdocs.com/assembly/java/com.groupdocs.assembly/DataSourceInfo
[8]: https://apireference.groupdocs.com/assembly/java/com.groupdocs.assembly/DocumentAssembler#assembleDocument-java.lang.String-java.lang.String-com.groupdocs.assembly.DataSourceInfo...-
[9]: https://purchase.groupdocs.com/temporary-license
[10]: https://blog.groupdocs.com/2021/02/10/generate-pdf-report-from-json-data-in-java/
[11]: https://blog.groupdocs.com/2021/07/07/generate-reports-from-csv-data-in-java/
[12]: https://docs.groupdocs.com/assembly/java/
[13]: https://forum.groupdocs.com/c/assembly
[14]: https://blog.groupdocs.com/2021/02/10/generate-pdf-report-from-json-data-in-java/
[15]: https://blog.groupdocs.com/2021/07/07/generate-reports-from-csv-data-in-java/


