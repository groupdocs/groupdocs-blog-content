---
title: "Feuilles Excel en filigrane en Java"
date: Wed, 10 Nov 2021 14:04:00 +0000
draft: false
url: /fr/2021/11/10/watermark-excel-sheets-in-java/
author: 'Shoaib Khan'
summary: 'Watermarks can be added to the documents either to protect the document from piracy, or to show any sumbol or message. In other posts, we discussed ways to watermark different [documents][1], [images][2], and [presentations][3]. In this article, you will learn **how to add watermark to Excel workbooks in different ways in Java**. We will be applyling watermarks separately using each approach.

Les sujets suivants sont traités dans cet article :

* API de filigrane pour Java
* Ajouter un **texte en filigrane** aux feuilles Excel
* Appliquer un filigrane à ** Feuille Excel spécifique **
* Ajouter un filigrane à la feuille Excel ** en arrière-plan ** '
tags: ['add watermark in java', 'how to add watermark in Java', 'watermark excel', 'watermark excel sheets in Java', 'watermarking API for Java']
categories: ['GroupDocs.Watermark Product Family']
---



{{< figure align=center src="images/add-watermark-to-excel-java.jpg" alt="Ajouter un filigrane à une feuille Excel en Java">}}


Des filigranes peuvent être ajoutés aux documents soit pour protéger le document contre le piratage, soit pour afficher tout symbole ou message. Dans d'autres articles, nous avons discuté des moyens de filigraner différents documents, images et présentations. Dans cet article, vous apprendrez comment ajouter un filigrane aux classeurs Excel de différentes manières en Java. Nous appliquerons des filigranes séparément en utilisant chaque approche.

Les sujets suivants sont traités ci-dessous :

* [API de filigrane pour Java][4]
* [Ajouter un **texte en filigrane** aux feuilles Excel][5]
* [Appliquer un filigrane à ** une feuille Excel spécifique **][6]
* [Ajouter un filigrane à la feuille Excel ** en arrière-plan **][7]

## API Java pour filigraner des feuilles Excel {#watermarking-java-api}

[GroupDocs.Watermark pour Java][8] est l'API permettant d'automatiser les filigranes pour les documents, les présentations, les images et de nombreux autres formats de fichiers. La liste complète des formats de documents pris en charge est disponible dans la [documentation][9].

Vous pouvez télécharger le fichier **JAR** à partir de la [section des téléchargements][10] ou utiliser les dernières configurations de référentiel et de dépendance [Maven][11] dans vos applications Java.

```
<repository>
	<id>GroupDocsJavaAPI</id>
	<name>GroupDocs Java API</name>
	<url>https://repository.groupdocs.com/repo/</url>
</repository>
<dependency>
        <groupId>com.groupdocs</groupId>
        <artifactId>groupdocs-watermark</artifactId>
        <version>21.3</version> 
</dependency>
```

## Filigraner des feuilles Excel à l'aide de Java {#watermark-all-sheets}

L'API de filigrane permet de personnaliser tout en insérant le filigrane dans les feuilles de calcul sous forme de texte. Voici les étapes pour ajouter des filigranes aux classeurs Excel en Java.

* Chargez la feuille de calcul source à l'aide de [Watermarker][12] et [SpreadsheetLoadOptions][13].
* Définissez le texte du filigrane et les propriétés d'apparence à l'aide de [TextWatermark][14].
* Ajoutez le filigrane défini à la feuille de calcul Excel en utilisant [add()][15] mehtod.
* Enregistrez la feuille de calcul résultante avec un filigrane à l'aide de la méthode [save()][16].

L'exemple de code Java suivant ajoute le filigrane de texte à toutes les feuilles du classeur Excel avec rotation et opacité et l'alignement défini.

```
/*
 * Add watermark to all the sheets of the Excel Workbook in Java
 */
// Charger la feuille de calcul
String filename = "path/spreadsheet.xlsx";
Watermarker watermarker = new Watermarker(filename, new SpreadsheetLoadOptions());

// Définir l'apparence du filigrane du texte
TextWatermark watermark = new TextWatermark("DRAFT", new Font("Segoe UI", 19));
watermark.setHorizontalAlignment(HorizontalAlignment.Center);
watermark.setVerticalAlignment(VerticalAlignment.Center);
watermark.setRotateAngle(-45);
watermark.setSizingType(SizingType.ScaleToParentDimensions);
watermark.setScaleFactor(0.5);
watermark.setOpacity(0.5);

// Ajouter un filigrane et enregistrer la feuille de calcul avec filigrane
watermarker.add(watermark);
watermarker.save("path/watermark-all-spreadsheet.xlsx");
watermarker.close();
```

## Feuille Excel spécifique au filigrane à l'aide de Java {#watermark-any-sheet}

De même, vous pouvez également insérer des filigranes dans n'importe quelle feuille du classeur. Les étapes suivantes expliquent comment appliquer un filigrane de texte à la feuille spécifique du classeur Excel en Java.

* Chargez la feuille de calcul à l'aide du [Filigrane][17].
* Définissez l'apparence et le texte du filigrane à l'aide de [TextWatermark][18].
* Définissez l'index de la feuille de calcul afin que le filigrane ne soit appliqué qu'à la feuille mentionnée.
* Ajoutez le filigrane de texte à la feuille de calcul Excel à l'aide de la méthode [add()][19] avec les options de filigrane.
* Enregistrez la feuille de calcul de sortie avec le filigrane à l'aide de la méthode [save()][20].

L'extrait de code Java suivant applique le filigrane de texte uniquement à la feuille mentionnée du classeur Excel.

```
/*
 * Add watermark only to the mentioned sheet of the Excel Workbook using Java
 */
// Charger la feuille de calcul
String filename = "path/spreadsheet.xlsx";
Watermarker watermarker = new Watermarker(filename, new SpreadsheetLoadOptions());

// Définir le filigrane du texte et son index de feuille de calcul
TextWatermark watermark = new TextWatermark("DRAFT", new Font("Segoe UI", 19));
SpreadsheetWatermarkModernWordArtOptions options = new SpreadsheetWatermarkModernWordArtOptions();               
options.setWorksheetIndex(0);

// Ajouter un filigrane et enregistrer la feuille de calcul avec filigrane
watermarker.add(watermark, options);
watermarker.save("path/watermark-single-sheet.xlsx");
watermarker.close();
```

## Filigrane des feuilles Excel en arrière-plan à l'aide de Java {#watermark-sheet-as-background}

De même, nous pouvons également ajouter des filigranes comme arrière-plan de la feuille de calcul. Il y aura quelques modifications à l'approche ci-dessus pour appliquer des filigranes. Voici les étapes qui insèrent un filigrane de texte d'arrière-plan dans une feuille de calcul Excel en Java.

* Chargez la feuille de calcul à l'aide de [Filigrane][21].
* Préparez le texte du filigrane et son apparence à l'aide de [TextWatermark][22].
* Définissez les paramètres du filigrane pour en faire un arrière-plan à l'aide des options de filigrane en obtenant le contenu et en définissant les dimensions.
* Ajoutez le filigrane aux feuilles du classeur à l'aide de la méthode [add()][23].
* Enfin, enregistrez la feuille de calcul en filigrane à l'aide de la méthode [save()][24].

L'exemple de code suivant peut être utilisé pour ajouter un filigrane de texte d'arrière-plan à une feuille de calcul Excel en Java.

```
/*
 * Add watermark as background to Excel Workbook in Java
 */
// Charger la feuille de calcul
String filename = "path/spreadsheet.xlsx";
Watermarker watermarker = new Watermarker(filename, new SpreadsheetLoadOptions());

// Définir l'apparence du filigrane du texte
TextWatermark watermark = new TextWatermark("DRAFT", new Font("Segoe UI", 19));
watermark.setHorizontalAlignment(HorizontalAlignment.Center);
watermark.setVerticalAlignment(VerticalAlignment.Center);
watermark.setRotateAngle(-45);
watermark.setSizingType(SizingType.ScaleToParentDimensions);
watermark.setScaleFactor(0.5);
watermark.setOpacity(0.5);

// Ajouter un filigrane à l'arrière-plan
SpreadsheetContent content = watermarker.getContent(SpreadsheetContent.class);
SpreadsheetBackgroundWatermarkOptions options = new SpreadsheetBackgroundWatermarkOptions();
options.setBackgroundWidth(content.getWorksheets().get_Item(0).getContentAreaWidthPx()); /* set background width */
options.setBackgroundHeight(content.getWorksheets().get_Item(0).getContentAreaHeightPx()); /* set background height */

// Enregistrer la feuille de calcul avec filigrane
watermarker.add(watermark, options);
watermarker.save("path/watermark-background-spreadsheet.xlsx");
watermarker.close();
```



{{< figure align=center src="images/watermark-excel-sheets-programmatically.png" alt="Filigraner des feuilles Excel par programme">}}


## Obtenez une licence API gratuite

Vous pouvez [obtenir une licence temporaire gratuite][25] afin d'utiliser l'API sans les limitations d'évaluation.

## Conclusion

Dans cet article, nous avons expliqué comment ajouter des filigranes aux feuilles Excel de différentes manières dans l'application Java. Nous avons appris à insérer un filigrane de texte dans toutes les feuilles du classeur Excel, puis nous avons appliqué le filigrane à la feuille spécifique uniquement. Plus tard, nous avons appliqué le filigrane en arrière-plan. Vous pouvez maintenant utiliser cette fonctionnalité et créer votre propre application pour ajouter des filigranes aux feuilles de calcul.

En savoir plus sur l'API dans la [documentation][26]. Pour toute question, contactez-nous via le [forum][27].

## Voir également

* [Feuilles Excel en filigrane à l'aide de C #][28]
* [Fichiers PDF en filigrane en Java][29]
* [Ajouter un filigrane aux images en Java][30]
* [Diapositives de présentation en filigrane utilisant Java][31]
* [Rechercher et supprimer des filigranes de documents en Java][32]







[1]: https://blog.groupdocs.com/2021/06/26/add-watermark-to-pdf-in-java/
[2]: https://blog.groupdocs.com/2020/09/15/add-watermark-to-images-in-java/
[3]: https://blog.groupdocs.com/2021/06/09/watermark-presentation-slides-using-java/
[4]: #watermarking-java-api
[5]: #watermark-all-sheets
[6]: #watermark-any-sheet
[7]: #watermark-sheet-as-background
[8]: https://products.groupdocs.com/watermark/
[9]: https://docs.groupdocs.com/watermark/java/supported-document-formats/
[10]: https://downloads.groupdocs.com/watermark
[11]: https://repository.groupdocs.com/webapp/#/artifacts/browse/tree/General/repo/com/groupdocs/groupdocs-watermark
[12]: https://apireference.groupdocs.com/watermark/java/com.groupdocs.watermark/Watermarker
[13]: https://apireference.groupdocs.com/watermark/java/com.groupdocs.watermark.options/SpreadsheetLoadOptions
[14]: https://apireference.groupdocs.com/watermark/java/com.groupdocs.watermark.watermarks/TextWatermark
[15]: https://apireference.groupdocs.com/watermark/java/com.groupdocs.watermark/Watermarker#add(com.groupdocs.watermark.Watermark)
[16]: https://apireference.groupdocs.com/watermark/java/com.groupdocs.watermark/Watermarker#save(java.lang.String)
[17]: https://apireference.groupdocs.com/watermark/java/com.groupdocs.watermark/Watermarker
[18]: https://apireference.groupdocs.com/watermark/java/com.groupdocs.watermark.watermarks/TextWatermark
[19]: https://apireference.groupdocs.com/watermark/java/com.groupdocs.watermark/Watermarker#add(com.groupdocs.watermark.Watermark)
[20]: https://apireference.groupdocs.com/watermark/java/com.groupdocs.watermark/Watermarker#save(java.lang.String)
[21]: https://apireference.groupdocs.com/watermark/java/com.groupdocs.watermark/Watermarker
[22]: https://apireference.groupdocs.com/watermark/java/com.groupdocs.watermark.watermarks/TextWatermark
[23]: https://apireference.groupdocs.com/watermark/java/com.groupdocs.watermark/Watermarker#add(com.groupdocs.watermark.Watermark)
[24]: https://apireference.groupdocs.com/watermark/java/com.groupdocs.watermark/Watermarker#save(java.lang.String)
[25]: https://purchase.groupdocs.com/temporary-license
[26]: https://docs.groupdocs.com/watermark
[27]: https://forum.groupdocs.com/
[28]: https://blog.groupdocs.com/2021/11/04/watermark-excel-sheets-using-csharp/
[29]: https://blog.groupdocs.com/2021/06/26/add-watermark-to-pdf-in-java/
[30]: https://blog.groupdocs.com/2020/09/15/add-watermark-to-images-in-java/
[31]: https://blog.groupdocs.com/2021/06/09/watermark-presentation-slides-using-java/
[32]: https://blog.groupdocs.com/2020/11/30/find-and-remove-watermarks-from-documents-in-java/


