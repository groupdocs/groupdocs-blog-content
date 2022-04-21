---
title: "Convertir des documents en Excel XLS, XLSX en Java"
date: Sat, 22 May 2021 18:39:23 +0000
draft: false
url: /fr/2021/05/22/convert-documents-to-excel-xls-xlsx-in-java/
author: 'Shoaib Khan'
summary: "Pour les données sous forme de tableau de vos documents PDF et Word, vous devez parfois les convertir en feuilles de calcul Excel. Nous devons automatiser cette conversion d'autant de documents en feuilles de calcul ou en plusieurs classeurs. Cet article explique comment convertir par programmation des documents Word en Excel et également comment convertir des fichiers PDF en feuilles de calcul Excel en Java."
tags: ['Convert to Excel in Java', 'DOC to XLS in Java', 'DOCX to XLSX in Java', 'PDF to Excel in Java', 'Word to Excel in Java']
categories: ['GroupDocs.Conversion Product Family']
---

Pour les données sous forme de tableau de vos documents PDF et Word, vous devez parfois les convertir en feuilles de calcul Excel. Nous devons automatiser cette conversion d'autant de documents en feuilles de calcul ou en plusieurs classeurs. Cet article explique comment convertir par programmation des documents Word en Excel et également comment convertir des fichiers PDF en feuilles de calcul Excel en Java.



{{< figure align=center src="images/pdf-word-to-xls-in-java.jpg" alt="Convertir Word et PDF en Excel en Java">}}


Les sujets suivants sont brièvement abordés ici :

* [API Java - Conversion de documents en feuilles de calcul][2]
* [Convertir un PDF en feuille de calcul Excel][3]
* [Convertir Word en feuille de calcul Excel][4]
* [Conversion PDF ou Word en feuille de calcul avec plus d'options][5]

## API Java pour la conversion en feuille de calcul {#convert-to-spreadsheet-java-api}

[GroupDocs.Conversion for Java][6] est l'API qui vous permet de convertir des documents PDF et Word en feuilles de calcul dans vos applications Java. L'API permet les conversions de documents et d'images dans de nombreux formats de fichiers. Certains des formats de document pris en charge comprennent les documents de traitement de texte, les feuilles de calcul, les présentations, les livres électroniques, les formats AutoCAD, PDF, les messages électroniques, les pages Web et les images.

### Télécharger et configurer

Vous pouvez obtenir la bibliothèque de conversion à partir de la section des téléchargements ou ajouter la configuration pom.xml suivante dans votre application Java basée sur Maven. Ensuite, vous pouvez essayer des exemples de cet article ainsi que de nombreux autres exemples disponibles sur [GitHub][7]. Pour plus de détails, vous pouvez visiter la [API Reference][8].

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
        <artifactId>groupdocs-conversion</artifactId>
        <version>21.4</version> 
</dependency>
```

## Convertir PDF en Excel en Java {#pdf-to-excel-csharp}

Les étapes suivantes peuvent être suivies pour convertir n'importe quel document PDF en une feuille de calcul Excel.

* Chargez le fichier PDF à l'aide de la classe [Converter][9].
* Préparez les options de conversion à l'aide de [SpreadsheetConvertOptions][10].
* Appelez la méthode [convert][11] avec les options créées.

L'exemple de code suivant montre comment convertir un fichier PDF en une feuille de calcul Excel XLSX en Java.

```
// Convertir un document PDF en feuille de calcul Excel en Java
Converter converter = new Converter("document.pdf");
SpreadsheetConvertOptions options = new SpreadsheetConvertOptions();
converter.convert("pdfToExcel.xlsx", options);
```

## Convertir Word en Excel en Java {#word-to-excel-csharp}

De même, tout document Word peut être converti en feuille de calcul Excel de la même manière que nous venons de convertir le document PDF. Fournissez le bon fichier source et convertissez-le en XLS ou XLSX.

Voici l'étape pour convertir n'importe quel fichier DOC DOCX en une feuille de calcul Excel.

* Chargez le fichier DOC, DOCX à l'aide de la classe Converter.
* Préparez les options de conversion à l'aide de SpreadsheetConvertOptions.
* Appelez la méthode convert de la classe Converter avec des options.

Le code source suivant montre comment convertir un fichier DOC ou DOCX au format Excel XLSX en Java.

```
// Convertir un document Word en feuille de calcul Excel en Java
Converter converter = new Converter("document.docx");
SpreadsheetConvertOptions options = new SpreadsheetConvertOptions();
converter.convert("wordToExcel.xlsx", options);
```

## Conversion PDF ou Word en feuille de calcul avec plus d'options en utilisant Java {#pdf-word-to-excel-adv}

Vous n'êtes pas obligé de convertir l'intégralité du document à chaque fois. Vous pouvez convertir uniquement les pages sélectionnées de votre document. L'API vous donne le privilège de convertir le document avec diverses options qui incluent :

* Début du **numéro de page**.
* **Nombre de pages**.
* **Pages spécifiques** pour la conversion.
* **Format** de conversion.
* **Mot de passe** pour protéger le fichier.
* **Zoom** pour l'agrandir ou le réduire.
* **Filigrane** sur le fichier du convertisseur.

Voici les étapes à suivre pour convertir certaines des pages d'un fichier PDF au format XLSX avec un zoom différent en Java.

```
// Convertir la deuxième page du fichier PDF en Excel en Java avec quelques options
Converter converter = new Converter("document.pdf");
SpreadsheetConvertOptions options = new SpreadsheetConvertOptions();
options.setPageNumber(2);
options.setPagesCount(1);
options.setFormat(SpreadsheetFileType.Xlsx);
options.setZoom(120);

converter.convert("pdfToExcelAdv.xlsx", options);
```

Le fichier PDF et la feuille de calcul convertie en sortie sont affichés ici. Il a converti la deuxième page du fichier PDF au format XLSX.



{{< figure align=center src="images/pdf-to-xls-in-csharp.jpg" alt="Convertir PDF en Excel XLS XLSX par programmation">}}


## Obtenez une licence API gratuite {#Get-a-Free-API-License}

Vous pouvez [obtenir une licence temporaire gratuite][12] afin d'utiliser l'API sans limitations d'évaluation.

## Conclusion

Dans cet article, nous avons discuté de la conversion de documents PDF et Word en une feuille de calcul Excel en Java. De plus, nous avons appris à convertir n'importe quelle partie du document avec des options telles que le filigrane, le zoom et à le protéger à l'aide d'une protection par mot de passe.

Pour plus d'options et d'exemples, consultez la [documentation][13] et le référentiel [GitHub][14]. Pour toute question, contactez-nous via le [forum][15].

## Voir également

* [Images au format PDF en Java][16]
* [Feuilles de calcul en PDF en Java][17]
* [Présentations au format PDF en Java][18]
* [Dessins CAO au format PDF en Java][19]







[1]: https://blog.groupdocs.com/2021/05/22/convert-documents-to-excel-xls-xlsx-in-java
[2]: #convert-to-spreadsheet-java-api
[3]: #pdf-to-excel-csharp
[4]: #word-to-excel-csharp
[5]: #pdf-word-to-excel-adv
[6]: https://products.groupdocs.com/conversion/net
[7]: https://github.com/groupdocs-conversion
[8]: https://apireference.groupdocs.com/conversion/java
[9]: https://apireference.groupdocs.com/java/conversion/com.groupdocs.conversion/Converter
[10]: https://apireference.groupdocs.com/conversion/java/com.groupdocs.conversion.options.convert/SpreadsheetConvertOptions
[11]: https://apireference.groupdocs.com/conversion/java/com.groupdocs.conversion/Converter#convert(java.io.OutputStream,%20com.groupdocs.conversion.contracts.ConvertedDocumentStream,%20com.groupdocs.conversion.options.convert.ConvertOptions)
[12]: https://purchase.groupdocs.com/temporary-license
[13]: https://docs.groupdocs.com/conversion
[14]: https://github.com/groupdocs-conversion
[15]: https://forum.groupdocs.com/
[16]: https://blog.groupdocs.com/2021/04/21/convert-images-to-pdf-in-java/
[17]: https://blog.groupdocs.com/2021/11/21/convert-excel-spreadsheets-to-pdf-in-java/
[18]: https://blog.groupdocs.com/2021/02/15/convert-presentations-odp-pptx-ppt-to-pdf-in-java/
[19]: https://blog.groupdocs.com/2020/10/31/convert-cad-drawings-to-pdf-in-java/


