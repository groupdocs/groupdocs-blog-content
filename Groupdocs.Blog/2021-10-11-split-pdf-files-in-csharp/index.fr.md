---
title: "Comment diviser des fichiers PDF à l'aide de C #"
date: Mon, 11 Oct 2021 04:14:00 +0000
draft: false
url: /fr/2021/10/11/split-pdf-files-in-csharp/
author: 'Shoaib Khan'
summary: "[PDF][1] est l'un des formats de fichiers les plus couramment utilisés qui est hautement portable. En tant que développeur, vous avez peut-être été confronté au scénario de fractionner des fichiers PDF volumineux par programmation. Aujourd'hui, cet article traite de différentes manières de **comment fractionner des fichiers PDF à l'aide de C# dans des applications .NET**."
tags: ['PDF Separator', 'Separate PDF', 'Split API', 'Split PDF', 'Split PDF Files', 'Split PDF using C#']
categories: ['GroupDocs.Merger Product Family']
---



{{< figure align=center src="images/split-pdf-into-multiple-files-using-csharp.jpg" alt="Diviser le PDF en plusieurs fichiers à l'aide de C #">}}


[PDF][2] est l'un des formats de fichiers les plus couramment utilisés qui est hautement portable. En tant que développeur, vous avez peut-être été confronté au scénario de fractionner des fichiers PDF volumineux par programme. Dans l'un des articles, nous avons appris à [diviser les fichiers PDF en Java][3]. Aujourd'hui, cet article traite de différentes manières de **comment fractionner des fichiers PDF à l'aide de C# dans des applications .NET**.

* [API .NET pour fractionner des fichiers PDF][4]
* [Fractionner le PDF en fichiers multipages][5]
* [Extraire les pages des fichiers PDF par plage][6]
* [Extraire des pages de fichiers PDF à l'aide d'un filtre pair ou impair][7]
* [Diviser le PDF en plusieurs fichiers d'une seule page][8]

## API .NET pour fractionner des fichiers PDF {#split-pdf-dontet-api}

Afin de diviser les fichiers PDF, nous utiliserons [GroupDocs.Merger pour .NET][9]. C'est l'API qui permet un développement rapide pour intégrer des fonctionnalités avec très peu de lignes de code. En plus du fractionnement, il prend en charge [la fusion, l'échange ou le rognage de documents de différents formats de fichiers][10].

Vous pouvez télécharger le programme d'installation **DLLs** ou **MSI** à partir de la [section téléchargements][11] ou installer l'API dans votre application .NET via [NuGet][12].

```
PM> Install-Package GroupDocs.Merger
```

## Diviser un fichier PDF en fichiers multipages à l'aide de C # {#split-pdf-to-multipage}

Les étapes suivantes expliquent comment diviser des fichiers PDF en fichiers multipages à l'aide de C# :

* Définissez le format des fichiers de sortie.
* Définissez les intervalles de page à l'aide de [SplitOptions][13].
* Chargez le fichier PDF en utilisant la classe [Merger][14].
* Divisez le PDF chargé selon l'intervalle défini à l'aide de la méthode [Split ()][15].

L'exemple de code suivant montre comment diviser des fichiers PDF en fichiers multipages.

```
/*
 * Split PDF files into multipage files using C#
 */
// Définir le format des fichiers de sortie
string filePathOut = "path/splitPDF_{0}.{1}";

// Définir les intervalles de fractionnement et le mode de fractionnement
SplitOptions splitOptions = new SplitOptions(filePathOut, new int[] { 3, 6, 8 }, SplitMode.Interval);

// Charger le fichier PDF et diviser le PDF en fonction des options de fractionnement
using (Merger merger = new Merger("path/document.pdf"))
{
    merger.Split(splitOptions);
} 
```

## Extraire des pages de fichiers PDF par plage {#extract-pages-by-range}

Les étapes suivantes expliquent comment extraire des pages d'un PDF à l'aide de C# en les divisant en fonction de la plage donnée :

* Définissez le format des fichiers de sortie.
* Indiquez la plage de pages à l'aide de [SplitOptions][16].
* Chargez le fichier PDF en utilisant la classe [Merger][17].
* Utilisez la méthode [Split()][18] pour diviser le PDF chargé en fonction de la plage définie.

L'extrait de code suivant montre comment diviser un PDF et extraire des pages en fournissant la plage.

```
/*
 * Split PDF file by Given Range into Single Page files using C#
 */
// Définir le format des fichiers de sortie
string filePathOut = "path/splitPDF_{0}.{1}";

// Définir la plage à extraire en tant que documents d'une seule page
SplitOptions splitOptions = new SplitOptions(filePathOut, 3, 7);

// Charger le fichier PDF et diviser le PDF en fonction des options de fractionnement
using (Merger merger = new Merger("path/document.pdf"))
{
    merger.Split(splitOptions);
}
```

## Extraire les pages paires/impaires des fichiers PDF à l'aide de C# {#extract-even-or-odd-pages}

Les étapes suivantes expliquent comment extraire les pages paires/impaires d'un fichier PDF en les divisant dans la plage donnée en appliquant simplement des filtres en C# :

* Définissez le format des fichiers de sortie.
* Indiquez la plage de pages à l'aide de [SplitOptions][19].
* Appliquez le filtre pour les pages paires, impaires ou toutes les pages à l'aide de [RangeMode][20].
* Chargez le fichier PDF en utilisant la classe [Merger][21].
* Utilisez la méthode [Split()][22] pour séparer le PDF chargé en fonction du filtre défini.

L'extrait de code suivant montre comment extraire toutes les pages paires/impaires dans la plage définie d'un fichier PDF.

```
/*
 * Split PDF file by Given Range & Filter (Even/Odd Pages) into Single Page files using C#
 */
// Définir le format des fichiers de sortie
string filePathOut = "path/splitPDF_{0}.{1}";

// Définir la plage et le filtre pour extraire toutes les pages ODD dans la plage donnée en tant que documents d'une seule page
SplitOptions splitOptions = new SplitOptions(filePathOut, 3, 7, RangeMode.OddPages);

// Charger le fichier PDF et diviser le PDF en fonction des options de fractionnement
using (Merger merger = new Merger("path/document.pdf"))
{
    merger.Split(splitOptions);
}
```

## Diviser un fichier PDF en plusieurs fichiers d'une seule page {#split-to-single-pages}

Les étapes suivantes expliquent comment diviser un PDF pour extraire des pages en plusieurs fichiers d'une seule page en C# :

* Définissez le format des fichiers de sortie.
* Définissez les numéros de page exacts à l'aide de [SplitOptions][23].
* Chargez le fichier PDF en utilisant la classe [Merger][24].
* Divisez le PDF chargé en fonction des pages définies à l'aide de la méthode [Split ()][25].

L'exemple de code suivant montre comment diviser des fichiers PDF en plusieurs fichiers d'une seule page.

```
/*
 * Split PDF file into Single Page files using C#
 */
// Définir le format des fichiers de sortie
string filePathOut = "path/splitPDF_{0}.{1}";

// Définir les pages à extraire en tant que document d'une seule page
SplitOptions splitOptions = new SplitOptions(filePathOut, new int[] { 3, 6, 8 });

// Charger le fichier PDF et diviser le PDF en fonction des options de fractionnement
using (Merger merger = new Merger("path/document.pdf"))
{
    merger.Split(splitOptions);
}
```

## Résumé des changements de code

Dans tous les scénarios, ce qui change, c'est la façon de définir **SplitOptions**. Voici le résumé du changement dans chaque extrait de code pour chaque scénario. Vous pouvez utiliser les paramètres suivants selon vos besoins dans votre code. Ici, j'ai utilisé un fichier PDF de 10 pages.

* **Pour les fichiers multipages - Utiliser l'intervalle** : \[1,2\], \[3,4,5\], \[6,7\], \[8,9,10\].

```
new SplitOptions(outputFile,  new int[] { 3, 6, 8 }, SplitMode.Interval)
```

* **Extraire les pages dans la plage** : \[3\], \[4\], \[5\], \[6\]

```
new SplitOptions(outputFile, 3, 6);
```

* **Plage avec filtre** : \[3\], \[5\], \[7\]

```
new SplitOptions(outputFile, 3, 8, (Integer)RangeMode.OddPages);
```

* **Pages individuelles** : \[3\], \[4\], \[9\]

```
new SplitOptions(outputFile, new int[] { 3, 4, 9 });
```

## Obtenez une licence API gratuite

Vous pouvez [obtenir une licence temporaire gratuite][26] afin d'utiliser l'API sans les limitations d'évaluation.

## Conclusion

Pour conclure, nous avons discuté des moyens de fractionner des fichiers PDF à l'aide de C#. Tout d'abord, nous divisons le fichier PDF en documents de plusieurs pages et d'une seule page. Nous avons également extrait des pages de fichiers PDF. Tout d'abord, nous avons extrait toutes les pages, puis les pages paires/impaires dans la plage donnée. Vous pouvez essayer de créer votre propre application .NET de fractionnement de PDF à l'aide de l'API GroupDocs.Merger.

Pour en savoir plus sur l'API, consultez la [documentation][27]. Pour toute question, contactez-nous via le [forum][28].

## Voir également

* [Fusionner des documents à l'aide de C #][29]
* [Fusionner plusieurs types de fichiers en un seul document à l'aide de C #][30]
* [Réorganiser les pages PDF à l'aide de C #][31]
* [Réorganiser les pages dans Word à l'aide de C #][32]
* [Comment diviser des fichiers PDF en Java][33]







[1]: https://docs.fileformat.com/pdf/
[2]: https://docs.fileformat.com/pdf/
[3]: https://blog.groupdocs.com/2021/10/19/split-pdf-files-in-java/
[4]: #split-pdf-dontet-api
[5]: #split-pdf-to-multipage
[6]: #extract-pages-by-range
[7]: #extract-even-or-odd-pages
[8]: https://blog.groupdocs.com/wp-admin/post.php?post=23730&action=edit#split-to-single-pages
[9]: https://products.groupdocs.com/merger/net/
[10]: https://docs.groupdocs.com/merger/net/supported-document-formats/
[11]: https://downloads.groupdocs.com/merger
[12]: https://www.nuget.org/packages/groupdocs.merger
[13]: https://apireference.groupdocs.com/merger/net/groupdocs.merger.domain.options/splitoptions
[14]: https://apireference.groupdocs.com/merger/net/groupdocs.merger/merger
[15]: https://apireference.groupdocs.com/merger/net/groupdocs.merger/merger/methods/split/index
[16]: https://apireference.groupdocs.com/merger/net/groupdocs.merger.domain.options/splitoptions
[17]: https://apireference.groupdocs.com/merger/net/groupdocs.merger/merger
[18]: https://apireference.groupdocs.com/merger/net/groupdocs.merger/merger/methods/split/index
[19]: https://apireference.groupdocs.com/merger/net/groupdocs.merger.domain.options/splitoptions
[20]: https://apireference.groupdocs.com/merger/net/groupdocs.merger.domain.options/rangemode
[21]: https://apireference.groupdocs.com/merger/net/groupdocs.merger/merger
[22]: https://apireference.groupdocs.com/merger/net/groupdocs.merger/merger/methods/split/index
[23]: https://apireference.groupdocs.com/merger/net/groupdocs.merger.domain.options/splitoptions
[24]: https://apireference.groupdocs.com/merger/net/groupdocs.merger/merger
[25]: https://apireference.groupdocs.com/merger/net/groupdocs.merger/merger/methods/split/index
[26]: https://purchase.groupdocs.com/temporary-license
[27]: https://docs.groupdocs.com/merger
[28]: https://forum.groupdocs.com/
[29]: https://blog.groupdocs.com/2020/08/19/merge-pdf-word-excel-ppt-files-in-csharp/
[30]: https://blog.groupdocs.com/2021/05/04/merge-multiple-file-types-using-csharp/
[31]: https://blog.groupdocs.com/2022/02/22/move-pdf-pages-using-csharp/
[32]: https://blog.groupdocs.com/2022/02/05/move-word-pages-using-csharp/
[33]: https://blog.groupdocs.com/2021/10/19/split-pdf-files-in-java/


