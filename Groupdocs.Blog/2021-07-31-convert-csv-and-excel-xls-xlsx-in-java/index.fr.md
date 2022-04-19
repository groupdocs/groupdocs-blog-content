---
title: "Convertir CSV en Excel (XLS XLSX) et Vice Versa en Java"
date: Sat, 31 Jul 2021 04:07:00 +0000
draft: false
url: /fr/2021/07/31/convertir-csv-et-excel-xls-xlsx-en-java/
author: 'Shoaib Khan'
summary: "**CSV** contient les valeurs séparées par des virgules, normalement utilisées pour stocker des données tabulaires sans formatage. Ces fichiers peuvent être visualisés dans n'importe quel éditeur de texte et également dans MS Excel pour le format tabulaire. D'autre part, les formats les plus utilisés pour les fichiers MS Excel sont XLS et XLSX. Ces formats prennent en charge d'innombrables options de formatage. Cet article traite de la conversion des feuilles de calcul Excel du format **XLS/XLSX au format CSV** et du format **CSV au format XLS/XLSX **par programme **à l'aide de Java**."
tags: ['Convert XLS and CSV in Java', 'CSV to Excel in Java', 'CSV to XLS in Java', 'CSV to XLSX in Java', 'Excel to CSV in Java', 'XLS to CSV in Java', 'XLSX to CSV in Java']
categories: ['GroupDocs.Conversion Product Family']
---



{{< figure align=center src="images/convert-csv-and-xls-xlsx-in-java.jpg" alt="Convertir en CSV et XLS XLSX en Java">}}


**CSV** contient les valeurs séparées par des virgules, normalement utilisées pour stocker des données tabulaires sans formatage. Ces fichiers peuvent être visualisés dans n'importe quel éditeur de texte et également dans MS Excel pour le format tabulaire. D'autre part, les formats les plus utilisés pour les fichiers MS Excel sont XLS et XLSX. Ces formats prennent en charge d'innombrables options de formatage. Cet article traite de la conversion des feuilles de calcul Excel du format **XLS/XLSX au format CSV** et du format **CSV au format XLS/XLSX **par programme **à l'aide de Java**.

Les sujets suivants sont traités ci-dessous :

* [API Java pour la conversion XLS/XLSX et CSV][1]
* [Conversion Excel vers CSV][2]
* [Conversion CSV vers Excel][3]

## API Java pour les fichiers Excel et la conversion CSV {#excel-csv-java-api}

[GroupDocs.Conversion][4] propose une API Java qui permet la conversion de formats de feuille de calcul entre eux. J'utiliserai cette API pour convertir XLSX en CSV et aussi CSV en XLS ou XLSX en utilisant Java. De plus, l'API permet la [conversion dans les deux sens de nombreux autres formats de documents et d'images][5] comme les documents de traitement de texte, les présentations, les livres électroniques, JPG, PNG, WebP et bien d'autres.

### Télécharger ou configurer

Vous pouvez télécharger le fichier **JAR** à partir de la [section téléchargements][6], ou simplement obtenir les configurations du référentiel et des dépendances pour le pox.xml de vos applications Java **basées sur maven**.

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
        <version>21.7</version> 
</dependency>
```

## Convertir CSV en Excel (XLS/XLSX) en Java {#csv-to-excel}

La transformation des données séparées par des virgules sous forme de tableau pour une meilleure présentation nécessite la conversion du format CSV au format XLS/XLSX. Les étapes suivantes permettent de convertir les fichiers CSV au format XLS/XLSX dans l'application Java.

* Préparez les options de chargement pour charger le fichier CSV.
* Chargez le CSV en utilisant la classe [Converter][7].
* Définissez le format de conversion sur XLSX à l'aide de [SpreadsheetConvertOptions][8].
* Appelez la méthode **convert** pour transformer les données CSV au format XLSX.

Le code suivant montre comment convertir votre fichier CSV au format XLSX en Java.

```
// Convertir des fichiers CSV au format XLS/XLSX en Java
CsvLoadOptions loadOptions = new CsvLoadOptions();
loadOptions.setSeparator(',');
Converter converter = new Converter("path/comma-sparated-values.csv", loadOptions);

SpreadsheetConvertOptions options = new SpreadsheetConvertOptions();
options.setFormat(SpreadsheetFileType.Xlsx);

converter.convert("path/spreadsheet.xlsx", options);
```

Pour le format XLS, définissez simplement le format de conversion en conséquence et fournissez le nom de fichier approprié avec l'extension.

## Convertir Excel (XLS/XLSX) en CSV en Java {#excel-to-csv}

De même, si le formatage n'est pas requis, vous pouvez supprimer les styles et les visuels et conserver simplement les données séparées par des virgules en convertissant le format XLS/XLSX au format CSV et en économisant de l'espace.

Les étapes suivantes permettent de convertir le format XLS ou XLSX en CSV dans les applications Java.

* Chargez le fichier Excel (XLS ou XLSX) en utilisant la classe [Converter][9].
* Définissez le format de conversion sur CSV à l'aide de [SpreadsheetConvertOptions][10].
* Appelez la méthode **convert** pour transformer les données de la feuille de calcul au format CSV.

Le code suivant montre comment convertir XLS ou XLSX au format CSV en Java.

```
// Convertir des feuilles de calcul Excel au format CSV de valeurs séparées par des virgules en Java
Converter converter = new Converter("path/spreadsheet.xlsx");

SpreadsheetConvertOptions options = new SpreadsheetConvertOptions();
options.setFormat(SpreadsheetFileType.Csv); // Specify the conversion format

converter.convert("path/convertedfile.csv", options);
```

## Obtenez une licence API gratuite

Vous pouvez [obtenir une licence temporaire gratuite][11] afin d'utiliser l'API sans les limitations d'évaluation.

## Conclusion

Pour conclure, vous avez appris comment convertir les fichiers MS Excel au format CSV et aussi la conversion des fichiers CSV au format XLS et XLSX par programmation avec vos applications Java. Vous pouvez en savoir plus sur l'API de conversion Java en utilisant la [documentation][12], ou par des exemples disponibles sur [GitHub][13]. Contactez-nous pour toute question sur le [forum][14].

## Voir également

* [Générer des rapports à partir de données CSV en Java][15]
* [Créer des rapports à partir de données XML en Java][16]
* [Convertir des feuilles de calcul Excel en PDF en Java][17]
* [Convertir des PDF, des documents Word en Excel XLS, XLSX en Java][18]







[1]: #excel-csv-java-api
[2]: #excel-to-csv
[3]: #csv-to-excel
[4]: https://products.groupdocs.com/conversion/
[5]: https://docs.groupdocs.com/conversion/java/supported-document-formats/
[6]: https://downloads.groupdocs.com/conversion
[7]: https://apireference.groupdocs.com/conversion/java/com.groupdocs.conversion/Converter
[8]: https://apireference.groupdocs.com/conversion/java/com.groupdocs.conversion.options.convert/SpreadsheetConvertOptions
[9]: https://apireference.groupdocs.com/conversion/java/com.groupdocs.conversion/Converter
[10]: https://apireference.groupdocs.com/conversion/java/com.groupdocs.conversion.options.convert/SpreadsheetConvertOptions
[11]: https://purchase.groupdocs.com/temporary-license
[12]: https://docs.groupdocs.com/conversion
[13]: https://github.com/groupdocs-conversion
[14]: https://forum.groupdocs.com/
[15]: https://blog.groupdocs.com/2021/07/07/generate-reports-from-csv-data-in-java/
[16]: https://blog.groupdocs.com/2021/07/10/generate-reports-from-xml-data-in-java/
[17]: https://blog.groupdocs.com/2021/11/21/convert-excel-spreadsheets-to-pdf-in-java/
[18]: https://blog.groupdocs.com/2021/05/22/convert-documents-to-excel-xls-xlsx-in-java/


