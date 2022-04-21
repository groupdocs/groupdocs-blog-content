---
title: "Différentes façons de fractionner des fichiers PDF en Java"
date: Tue, 19 Oct 2021 14:41:58 +0000
draft: false
url: /fr/2021/10/19/split-pdf-files-in-java/
aliases:
- /2021/10/19/split-pdf-files-in-java-2/
author: 'Shoaib Khan'
summary: "PDF est l'un des formats de fichiers les plus connus qui prennent en charge les éléments textuels, graphiques et bien d'autres. L'une des raisons de sa popularité est sa portabilité. Dans certains cas, vous devrez peut-être diviser un gros fichier PDF en plusieurs fichiers. Pour résoudre ce problème par programmation, cet article explique différentes manières de **comment fractionner des fichiers PDF en Java**."
tags: ['PDF Separator', 'Separate PDF', 'Split API', 'Split PDF', 'Split PDF Files', 'Split PDF in Java']
categories: ['GroupDocs.Merger Product Family']
---



{{< figure align=center src="images/split-pdf-into-multiple-files-in-java.jpg" alt="Diviser un PDF en plusieurs fichiers en Java">}}


[PDF][1] est l'un des formats de fichiers les plus connus qui prennent en charge les éléments textuels, graphiques et bien d'autres. L'une des raisons de sa popularité est sa portabilité. Dans certains cas, vous devrez peut-être diviser un gros fichier PDF en plusieurs fichiers. Pour résoudre ce problème par programmation, cet article explique différentes manières de **comment fractionner des fichiers PDF en Java**.

* [API Java pour fractionner des fichiers PDF][2]
* [Diviser le PDF en fichiers multipages][3]
* [Diviser le PDF en plusieurs fichiers d'une seule page][4]
* [Extraire les pages des fichiers PDF par plage en Java][5]
* [Extraire des pages de fichiers PDF à l'aide d'un filtre pair ou impair en Java][6]

## API Java pour fractionner des fichiers PDF {#split-pdf-java-api}

[GroupDocs.Merger][7] fournit la solution pour fusionner et diviser des fichiers de nombreux formats de fichiers différents. Nous utiliserons son [API Java][8] pour diviser les fichiers PDF de différentes manières. Téléchargez le fichier **JAR** à partir de la [section des téléchargements][9], ou utilisez simplement les dernières configurations de référentiel et de dépendance [Maven][10] dans vos applications Java.

```
<repository>
	<id>GroupDocsJavaAPI</id>
	<name>GroupDocs Java API</name>
	<url>http://repository.groupdocs.com/repo/</url>
</repository>
<dependency>
        <groupId>com.groupdocs</groupId>
        <artifactId>groupdocs-merger</artifactId>
        <version>21.9</version> 
</dependency>
```

## Diviser un fichier PDF en fichiers multipages en Java {#split-pdf-to-multipage}

Les étapes suivantes expliquent comment diviser un fichier PDF en fichiers multipages :

* Chargez le fichier PDF en utilisant la classe [Merger][11].
* Définissez le format des fichiers de sortie.
* Définissez les intervalles de page à l'aide de [SplitOptions][12].
* Divisez le PDF chargé selon l'intervalle défini à l'aide de la méthode [split()][13].

L'exemple de code suivant montre comment diviser des fichiers PDF en fichiers multipages en Java.

```
/*
 * Split PDF files into multiple page files in Java
 */
// Charger le fichier PDF
Merger merger = new Merger("path/document.pdf"); 

// Définir le format des fichiers de sortie
String filePathOut = "path/splitPDF_{0}.{1}";

// Définir les intervalles de fractionnement et le mode de fractionnement
SplitOptions splitOptions = new SplitOptions(filePathOut,  new int[] { 3, 6, 8 }, SplitMode.Interval);

// Diviser le PDF selon des intervalles donnés
merger.split(splitOptions);
```

## Diviser un fichier PDF en plusieurs fichiers d'une seule page en Java {#split-to-single-pages}

Les étapes suivantes expliquent comment diviser un PDF pour extraire des pages en plusieurs fichiers d'une seule page :

* Chargez le fichier PDF en utilisant la classe [Merger][14].
* Définissez le format des fichiers de sortie.
* Définissez les numéros de page exacts à l'aide de [SplitOptions][15].
* Divisez le PDF chargé en fonction des pages définies à l'aide de la méthode [split()][16].

L'exemple de code suivant montre comment diviser des fichiers PDF en plusieurs fichiers d'une seule page en Java.

```
/*
 * Split PDF file into Single Page files in Java
 */
// Charger le fichier PDF
Merger merger = new Merger("path/document.pdf");

// Définir le format des fichiers de sortie
String filePathOut = "path/splitPDF_{0}.{1}"; 

// Définir les pages à extraire en tant que document d'une seule page
SplitOptions splitOptions = new SplitOptions(filePathOut, new int[] { 3, 6, 8 });

// Fractionner le PDF selon les options de fractionnement
merger.split(splitOptions);
```

## Extraire des pages de fichiers PDF par plage en Java {#extract-pages-by-range}

Les étapes suivantes expliquent comment extraire des pages d'un PDF en les divisant selon la plage donnée :

* Chargez le fichier PDF en utilisant la classe [Merger][17].
* Définissez le format des fichiers de sortie.
* Indiquez la plage de pages à l'aide de [SplitOptions][18].
* Utilisez la méthode [split()][19] pour diviser le PDF chargé en fonction de la plage définie.

L'extrait de code suivant montre comment diviser un PDF et extraire des pages en fournissant une plage en Java.

```
/*
 * Split PDF file by Given Range into Single Page files in Java
 */
// Charger le fichier PDF
Merger merger = new Merger("path/document.pdf"); 

// Définir le format des fichiers de sortie
String filePathOut = "path/splitPDF_{0}.{1}";

// Définir la plage à extraire en tant que documents d'une seule page
SplitOptions splitOptions = new SplitOptions(filePathOut, 3, 7);

// Fractionner le PDF selon les options de fractionnement
merger.split(splitOptions);
```

## Extraire des pages de fichiers PDF à l'aide du filtre pair/impair en Java {#extract-even-or-odd-pages}

Les étapes suivantes expliquent comment extraire les pages paires/impaires dans la plage donnée du fichier PDF en les divisant :

* Chargez le fichier PDF en utilisant la classe [Merger][20].
* Définissez le format des fichiers de sortie.
* Indiquez la plage de pages à l'aide de [SplitOptions][21].
* Appliquez le filtre pair, impair ou toutes les pages à l'aide de [RangeMode][22].
* Utilisez la méthode [split()][23] pour diviser le PDF chargé en fonction du filtre défini.

L'extrait de code suivant montre comment extraire toutes les pages paires/impaires dans la plage définie d'un fichier PDF à l'aide de Java.

```
/*
 * Split PDF file by Given Range & Filter (Even/Odd Pages) into Single Page files in Java
 */
// Charger le fichier PDF
Merger merger = new Merger("path/document.pdf"); 

// Définir le format des fichiers de sortie
String filePathOut = "path/splitPDF_{0}.{1}";

// Définir la plage et le filtre pour extraire toutes les pages ODD dans la plage donnée en tant que documents d'une seule page
SplitOptions splitOptions = new SplitOptions(filePathOut, 3, 7, (Integer)RangeMode.OddPages);

// Fractionner le PDF selon les options de fractionnement
merger.split(splitOptions);
```

## Résumé des changements de code

La seule chose qui diffère dans les scénarios ci-dessus est la façon de créer **SplitOptions**. Vous pouvez utiliser les configurations suivantes selon vos besoins dans votre code.

* **Pour les fichiers multipages - Utiliser l'intervalle** : \[1,2\], \[3,4,5\], \[6,7\], \[8,9,10\].

```
new SplitOptions(outputFile,  new int[] { 3, 6, 8 }, SplitMode.Interval)
```

* **Pages individuelles** : \[3\], \[6\], \[8\]

```
new SplitOptions(outputFile, new int[] { 3, 6, 8 });
```

* **Pour extraire les pages de la plage** : \[3\], \[4\], \[5\]

```
new SplitOptions(outputFile, 3, 5);
```

* **Plage avec filtre** : \[3\], \[5\], \[7\]

```
new SplitOptions(outputFile, 3, 7, (Integer)RangeMode.OddPages);
```

## Obtenez une licence API gratuite

Vous pouvez [obtenir une licence temporaire gratuite][24] afin d'utiliser l'API sans les limitations d'évaluation.

## Conclusion

En résumé, vous avez appris différentes manières de fractionner des fichiers PDF en Java. Tout d'abord, nous divisons le fichier PDF en documents de plusieurs pages ainsi qu'en plusieurs documents d'une seule page. Ensuite, une par une, nous avons extrait toutes les pages et les pages paires/impaires du fichier PDF dans la plage donnée. Vous devriez maintenant être sûr de créer votre propre application Java de fractionnement de PDF à l'aide de l'API GroupDocs.Merger.

Pour en savoir plus sur l'API, consultez la [documentation][25]. Pour toute question, contactez-nous via le [forum][26].

## Voir également

* [Fusionner plusieurs types de fichiers en un seul à l'aide de Java][27]
* [Fusionner des documents PDF, Word, Excel en Java][28]
* [Différentes façons de fractionner des fichiers PDF à l'aide de C #][29]







[1]: https://docs.fileformat.com/pdf/
[2]: #split-pdf-java-api
[3]: #split-pdf-to-multipage
[4]: #split-to-single-pages
[5]: #extract-pages-by-range
[6]: #extract-even-or-odd-pages
[7]: https://products.groupdocs.com/merger/
[8]: https://products.groupdocs.com/merger/java/
[9]: https://downloads.groupdocs.com/merger
[10]: https://repository.groupdocs.com/webapp/#/artifacts/browse/tree/General/repo/com/groupdocs/groupdocs-merger
[11]: https://apireference.groupdocs.com/merger/java/com.groupdocs.merger/Merger
[12]: https://apireference.groupdocs.com/merger/java/com.groupdocs.merger.domain.options/SplitOptions
[13]: https://apireference.groupdocs.com/merger/java/com.groupdocs.merger/Merger#split(com.groupdocs.merger.domain.options.interfaces.ISplitOptions)
[14]: https://apireference.groupdocs.com/merger/java/com.groupdocs.merger/Merger
[15]: https://apireference.groupdocs.com/merger/java/com.groupdocs.merger.domain.options/SplitOptions
[16]: https://apireference.groupdocs.com/merger/java/com.groupdocs.merger/Merger#split(com.groupdocs.merger.domain.options.interfaces.ISplitOptions)
[17]: https://apireference.groupdocs.com/merger/java/com.groupdocs.merger/Merger
[18]: https://apireference.groupdocs.com/merger/java/com.groupdocs.merger.domain.options/SplitOptions
[19]: https://apireference.groupdocs.com/merger/java/com.groupdocs.merger/Merger#split(com.groupdocs.merger.domain.options.interfaces.ISplitOptions)
[20]: https://apireference.groupdocs.com/merger/java/com.groupdocs.merger/Merger
[21]: https://apireference.groupdocs.com/merger/java/com.groupdocs.merger.domain.options/SplitOptions
[22]: https://apireference.groupdocs.com/merger/java/com.groupdocs.merger.domain.options/RangeMode
[23]: https://apireference.groupdocs.com/merger/java/com.groupdocs.merger/Merger#split(com.groupdocs.merger.domain.options.interfaces.ISplitOptions)
[24]: https://purchase.groupdocs.com/temporary-license
[25]: https://docs.groupdocs.com/merger
[26]: https://forum.groupdocs.com/
[27]: https://blog.groupdocs.com/2021/06/13/merge-multiple-file-types-using-java/
[28]: https://blog.groupdocs.com/2020/05/20/merge-pdf-word-excel-powerpoint-documents-in-java/
[29]: https://blog.groupdocs.com/2021/10/11/split-pdf-files-in-csharp/



