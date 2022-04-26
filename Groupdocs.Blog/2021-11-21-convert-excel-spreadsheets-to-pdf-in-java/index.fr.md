---
title: "Convertir des feuilles de calcul Excel en PDF en Java"
date: Sun, 21 Nov 2021 07:32:11 +0000
draft: false
url: /fr/2021/11/21/convert-excel-spreadsheets-to-pdf-in-java/
author: 'Shoaib Khan'
summary: "Lorsque nous voulons partager les données dans des feuilles de calcul qui ne nécessitent pas d'édition, nous convertissons souvent ces classeurs Excel ou des feuilles spécifiques au format PDF. Dans cet article, nous allons apprendre **4 manières différentes de convertir des feuilles de calcul Excel au format PDF en Java** à l'aide de l'API de conversion de documents."
tags: ['Convert Excel in Java', 'Convert Excel to PDF', 'Convert Excel to PDF in Java', 'convert to PDF in java', 'Excel to PDF', 'Excel to PDF in Java']
categories: ['GroupDocs.Conversion Product Family']
---



{{< figure align=center src="images/excel-to-pdf-in-java.jpg" alt="Convertir une feuille de calcul Excel en PDF en Java">}}


Lorsque nous voulons partager les données dans des feuilles de calcul qui ne nécessitent pas d'édition, nous convertissons souvent ces classeurs Excel ou des feuilles spécifiques au format PDF. Dans cet article, nous allons apprendre **4 manières différentes de convertir des feuilles de calcul Excel au format PDF en Java** à l'aide de l'API de conversion de documents.

Chaque approche de conversion peut être adoptée avec un petit changement dans le code lors du chargement des feuilles de calcul ou avec quelques ajustements dans les options de conversion du format PDF. Certaines des façons possibles de convertir les feuilles de calcul dans l'article sont les suivantes.

* [API Java pour la conversion de fichiers Excel en PDF][1]
* [Convertir toutes les feuilles en PDF][2]
* [Nombre continu de feuilles Excel en conversion PDF][3]
* [Liste spécifique des feuilles Excel en conversion PDF][4]
* [Convertir la plage de cellules sélectionnée d'une feuille Excel en PDF][5]

## API Java pour convertir des fichiers Excel en PDF {#excel-conversion-java-api}

[GroupDocs.Conversion][6] fournit une API Java qui permet aux nombreux formats de fichiers Excel, notamment XLS, XLSX, de se convertir au format PDF. Dans cet article, nous utiliserons son [GroupDocs.Conversion pour Java][7]. En plus des feuilles de calcul, l'API prend en charge la conversion de documents de traitement de texte, de présentations, de livres électroniques, d'images, etc. qui sont mentionnés dans la [documentation][8].

Vous pouvez télécharger le fichier **JAR** à partir de la [section des téléchargements][9] ou utiliser les dernières configurations de référentiel et de dépendance [Maven][10] dans vos applications Java.

```
<repository>
	<id>GroupDocsJavaAPI</id>
	<name>GroupDocs Java API</name>
	<url>http://repository.groupdocs.com/repo/</url>
</repository>
<dependency>
        <groupId>com.groupdocs</groupId>
        <artifactId>groupdocs-conversion</artifactId>
        <version>21.10</version> 
</dependency>
```

## Convertir toutes les feuilles de fichiers Excel en PDF - Java {#excel-to-pdf}

Le plus simple est de convertir toutes les feuilles au format PDF. Les étapes suivantes convertissent le classeur complet (toutes les feuilles) au format PDF en Java.

* **Chargez le classeur Excel** (XLS, XLSX) à l'aide du [Convertisseur][11].
* Convertissez-le au format PDF en utilisant l'une des méthodes surchargées [convert()][12] en utilisant [PdfConvertOptions][13].

Voici les 2 lignes de code source Java qui convertissent le classeur Excel complet en PDF.

```
/*
 * Convert all the Excel sheets to PDF format in Java
 */
Converter converter = new Converter("path/spreadsheet.xlsx");
converter.convert("path/all-sheets-converted.pdf", new PdfConvertOptions());
```



{{< figure align=center src="images/Converted-Excel-to-PDF.png" alt="Convertir un PDF à partir de données Excel">}}


## Conversion de feuilles Excel successives en PDF - Java {#successive-sheets-to-pdf}

Si vous souhaitez extraire le sous-ensemble de feuilles de calcul en séquence, vous pouvez facilement le faire en fournissant le numéro de la feuille de départ et le nombre de feuilles successives. Voici les étapes pour convertir toute sous-séquence de la ou des feuilles de classeur Excel au format PDF en Java.

* **Chargez** la feuille de calcul à l'aide du [Convertisseur][14].
* Définissez les **options de conversion PDF** à l'aide de [PdfConvertOptions][15].
* Définissez le **numéro de feuille de départ** et le **nombre de feuilles suivantes**.
* **Convertissez** les feuilles sélectionnées en PDF en fonction des paramètres à l'aide de la méthode [convert()][16].

Voici l'extrait de code Java qui convertit les deux premières feuilles en PDF. (Numéros de feuille **1 et 2**)

```
/*
 * Convert sequence of Excel sheets to PDF format in Java
 */
Converter converter = new Converter("path/spreadsheet.xlsx");

PdfConvertOptions convertOptions = new PdfConvertOptions();
convertOptions.setPageNumber(1);
convertOptions.setPagesCount(2);

converter.convert("path/sequential-conversion.pdf", convertOptions);
```

## Conversion de feuilles Excel spécifiques en PDF - Java {#list-of-sheets-to-pdf}

Si vous envisagez de convertir des feuilles aléatoires (comme les numéros de feuille 1, 2, 4, 7, ...), vous pouvez simplement fournir les numéros de feuille exacts sous forme de liste lors de la conversion. Voici les étapes pour convertir une liste spécifique de numéros de feuille au format PDF en Java.

* **Chargez** le fichier Excel à l'aide du [Convertisseur][17].
* **Fournissez les numéros exacts des feuilles** sous forme de liste à l'aide de [PdfConvertOptions][18].
* **Convertissez** les feuilles répertoriées au format PDF à l'aide de la méthode [convert()][19].

L'extrait de code suivant convertit les numéros de feuille **1 et 3** au format PDF.

```
/*
 * Convert the specified list of Excel sheets to PDF format in Java
 */
Converter converter = new Converter("path/spreadsheet.xlsx");

PdfConvertOptions convertOptions = new PdfConvertOptions();
convertOptions.setPages(Arrays.asList(1,3));

converter.convert("path/specific-sheets-conversion.pdf", convertOptions);
```

## Convertir la plage de cellules d'une feuille Excel en PDF - Java {#cell-ranges-to-pdf}

Voici la façon inhabituelle de convertir n'importe quel segment de la ou des feuilles de calcul. Nous pouvons convertir toutes les plages de cellules de feuilles Excel de manière presque similaire aux autres approches décrites ci-dessus. Voici les étapes pour convertir la plage de cellules des feuilles de classeur au format PDF en Java.

* Définissez la **plage de cellules** des feuilles.
* **Chargez** le fichier de feuille de calcul.
* ** Sélectionnez les feuilles ** en fournissant une plage de feuilles successives ou le nombre exact de feuilles.
* **Convertir** les feuilles au format PDF selon les paramètres.

Le code suivant convertit la plage de cellules (A1:C20) de la feuille numéro 1 au format PDF en Java.

```
/*
 * Convert the specified Cell Range of specified Excel sheets to PDF format in Java
 */
// Préparer les options de chargement et la plage pour le fichier XLSX source
SpreadsheetLoadOptions loadOptions = new SpreadsheetLoadOptions();
loadOptions.setConvertRange("A1:C20");
Converter converter = new Converter("path/spreadsheet.xlsx", loadOptions);

PdfConvertOptions convertOptions = new PdfConvertOptions();
convertOptions.setPageNumber(1);
convertOptions.setPagesCount(1);

converter.convert("path/convert-cell-range.pdf", convertOptions);
```

## Obtenez une licence API gratuite

Vous pouvez [obtenir une licence temporaire gratuite][20] afin d'utiliser l'API sans les limitations d'évaluation.

## Conclusion

Résumons ce que nous avons appris aujourd'hui. Nous avons appris quatre façons différentes de convertir des feuilles de calcul Excel au format PDF en Java à l'aide de GroupDocs.Conversion. Dans un premier temps, nous avons converti le classeur complet au format PDF, puis les feuilles consécutives. Ensuite, plusieurs feuilles ont été modifiées en PDF en répertoriant leurs numéros de feuille exacts. Enfin, nous avons obtenu le fichier PDF à partir de la plage de cellules sélectionnée de la ou des feuilles sélectionnées.

En savoir plus sur les **API GroupDocs.Conversion** dans la [documentation][21]. Pour toute question, contactez-nous via le [forum][22].

## Voir également

* [Convertir CSV et Excel (XLS XLSX) en Java][23]
* [Convertir des documents en Excel (XLS, XLSX) en Java][24]
* [Feuilles Excel en filigrane en Java][25]
* [Fichiers PDF en filigrane en Java][26]







[1]: #excel-conversion-java-api
[2]: #excel-to-pdf
[3]: #successive-sheets-to-pdf
[4]: #list-of-sheets-to-pdf
[5]: #cell-ranges-to-pdf
[6]: https://products.groupdocs.com/conversion/
[7]: https://products.groupdocs.com/conversion/java/
[8]: https://docs.groupdocs.com/conversion/java/supported-document-formats/
[9]: https://downloads.groupdocs.com/conversion
[10]: https://repository.groupdocs.com/webapp/#/artifacts/browse/tree/General/repo/com/groupdocs/groupdocs-conversion
[11]: https://apireference.groupdocs.com/conversion/java/com.groupdocs.conversion/Converter
[12]: https://apireference.groupdocs.com/conversion/java/com.groupdocs.conversion/Converter#convert(java.lang.String,%20com.groupdocs.conversion.options.convert.ConvertOptions)
[13]: https://apireference.groupdocs.com/conversion/java/com.groupdocs.conversion.options.convert/PdfConvertOptions
[14]: https://apireference.groupdocs.com/conversion/java/com.groupdocs.conversion/Converter
[15]: https://apireference.groupdocs.com/conversion/java/com.groupdocs.conversion.options.convert/PdfConvertOptions
[16]: https://apireference.groupdocs.com/conversion/java/com.groupdocs.conversion/Converter#convert(java.lang.String,%20com.groupdocs.conversion.options.convert.ConvertOptions)
[17]: https://apireference.groupdocs.com/conversion/java/com.groupdocs.conversion/Converter
[18]: https://apireference.groupdocs.com/conversion/java/com.groupdocs.conversion.options.convert/PdfConvertOptions
[19]: https://apireference.groupdocs.com/conversion/java/com.groupdocs.conversion/Converter#convert(java.lang.String,%20com.groupdocs.conversion.options.convert.ConvertOptions)
[20]: https://purchase.groupdocs.com/temporary-license
[21]: https://docs.groupdocs.com/conversion
[22]: https://forum.groupdocs.com/
[23]: https://blog.groupdocs.com/2021/07/31/convert-csv-and-excel-xls-xlsx-in-java/
[24]: https://blog.groupdocs.com/2021/05/22/convert-documents-to-excel-xls-xlsx-in-java/
[25]: https://blog.groupdocs.com/2021/11/10/watermark-excel-sheets-in-java/
[26]: https://blog.groupdocs.com/2021/06/26/add-watermark-to-pdf-in-java/


