---
title: "Diviser ou fusionner des documents PDF, Word, Excel en Java"
date: Wed, 20 May 2020 08:22:00 +0000
draft: false
url: /fr/2020/05/20/merge-pdf-word-excel-powerpoint-documents-en-java/
aliases:
- /2020/02/20/split-or-merge-pdf-word-excel-documents-in-dotnet-or-java/
- /2020/02/20/split-or-merge-pdf-word-excel-documents-in-csharp-or-java/
- /2020/02/20/split-or-merge-pdf-word-excel-documents-in-c-or-java/
author: 'Shoaib Khan'
summary: "Vous craignez de fusionner ou de diviser des documents de différents types sur plusieurs plates-formes ? Il pourrait y avoir de nombreuses déclarations dans votre esprit : * Comment fusionner des documents PDF ensemble en Java ? * Vous souhaitez diviser des documents Word ou fusionner des feuilles de calcul Excel. * Que faire si j'ai besoin de fusionner des présentations PPT/PPTX. * Beaucoup plus de questions, la liste peut ne pas se terminer."
tags: ['Merge Documents in Java', 'Merge PDF in Java', 'Merge Word in Java', 'Split Documents in Java', 'Split PDF in Java', 'Split PPT in Java']
categories: ['GroupDocs.Merger Product Family']
---

Vous craignez de fusionner ou de diviser des documents de différents types sur plusieurs plates-formes ? Il pourrait y avoir de nombreuses déclarations dans votre esprit :

* Comment fusionner des documents PDF ensemble en Java ?
* Vous souhaitez diviser des documents Word ou fusionner des feuilles de calcul Excel.
* Que faire si j'ai besoin de fusionner des présentations PPT/PPTX.
* Beaucoup plus de questions, la liste peut ne pas se terminer.



{{< figure align=center src="images/merge-split-documents-in-java-1.png" alt="Diviser ou fusionner des documents PDF, Word, Excel en Java">}}




{{< figure align=center src="images/groupdocs-merger-java-90x90-no-reply.png" alt="GroupDocs. Merger pour Java">}}


GroupDocs fournit une [solution de fusion de documents][1] pour toutes ces exigences. Son [API Java][2] vous permet de ** fusionner des documents ** et de manipuler la structure du document en Java sur une large gamme de formats de document pris en charge. Il permet en outre de manipuler les pages du document, les transformations de page, l'extraction d'informations des documents, la génération d'aperçus, et bien plus encore.

Dans cet article, nous allons nous pencher un peu sur les sujets suivants :

* [Comment fusionner des fichiers PDF en Java][3].
* [Fusionner des documents Word, des feuilles de calcul Excel et des présentations PowerPoint][4].
* [Fusionner certaines pages du document][5].
* [Diviser n'importe quel document en plusieurs documents][6].

L'exemple de code et les étapes expliquées ci-dessous utilisent [GroupDocs.Merger pour Java][7] afin que vous puissiez [télécharger][8] ou l'intégrer dans vos applications basées sur maven avec des configurations pom.xml.

## Fusionner des fichiers PDF en Java {#merge-pdf-files-in-java}

Nous pouvons combiner deux ou plusieurs fichiers PDF en quelques lignes de code seulement. Vous trouverez ci-dessous l'extrait de code des [exemples][9], qui s'explique de lui-même et ne nécessite aucune clarification supplémentaire, et montre donc comment fusionner plusieurs documents PDF en Java. Les démarches sont très simples si vous avez décidé des documents à joindre :

* Instanciez l'objet [Merger][10], avec le premier document avec lequel d'autres documents doivent être fusionnés.
* Appelez la méthode [join][11], en passant le document à fusionner.
* Rappel de la méthode de jointure pour fusionner plus de documents.
* Appelez la méthode [save][12] pour enregistrer la sortie finale.
* C'est ça.

```
// Set paths for the documents to join together in a single file.
String filePath1 = "document-1.pdf";
String filePath2 = "document-2.pdf";
String filePath3 = "document-3.pdf";
// Merger multiple PDF documents into a single PDF file.
Merger merger = new Merger(filePath1 );
merger.join(filePath2 ); // Joining 2nd Document
merger.join(filePath3 ); // Joining 3rd Document
// Save the merged document.
String filePathOutput = "mergedDocument.pdf";
merger.save(filePathOutput);
```

## Fusionner des documents Excel, Word, PowerPoint en Java {#merge-excel-ppt-and-word-docs-in-java}

Vous pouvez combiner plusieurs documents Word, feuilles de calcul Excel, présentations PowerPoint, en fait, presque tous les documents du **même format**. Le code ci-dessus pour joindre des documents PDF peut être utilisé pour fusionner une grande variété de documents. En bas de l'article, je mentionnerai la liste des formats de fichiers pouvant être fusionnés avec le même code. Ici, pour un exemple, je montre comment, de la même manière, plus de deux documents Word peuvent être combinés en un seul fichier Word en quelques lignes de code Java.

```
// Merger multiple Word documents into a single DOCX file.
Merger merger = new Merger("document1.docx" );
merger.join("document2.docx" ); // Joining 2nd Document
merger.join("document3.docx" ); // Joining 3rd Document
// Save the merged document.
merger.save("mergedDocument.pdf");
```

## Fusionner des pages de documents en Java {#merge-document-pages-in-java}

Plusieurs documents peuvent être fusionnés par pages sélectives et également en spécifiant la plage de pages souhaitée. Votre code restera similaire à celui mentionné ci-dessus, juste un petit changement lors de la définition de vos options de fusion à l'aide de la classe [JoinOptions][13].

Vous trouverez ci-dessous l'extrait de code source qui montre comment fusionner des documents en spécifiant certaines pages.

```
// Set the start and end page number in JoinOptions class.
JoinOptions joinOptions = new JoinOptions(1, 2);
// Merge two files with selective pages using join method.
Merger merger = new Merger("document-1.docx");
merger.join("document-2.docx" , joinOptions);
merger.save("merged-Document.docx");
```

## Diviser des documents en plusieurs documents en Java {#split-documents-in-java}

Tout comme nous avons fusionné des documents ci-dessus, nous pouvons également diviser rapidement des documents Word, des feuilles de calcul Excel, des présentations, des fichiers PDF et de nombreux autres documents de différentes manières.

* Diviser par numéros de page exacts
* Diviser un document en plusieurs documents de plusieurs pages
* Diviser par plage de pages
* Diviser par pages paires et impaires

### Fractionner par numéros de page exacts

Nous pouvons diviser un document en fournissant le nombre exact de pages en Java. Le code suivant divisera un fichier PDF en 3 documents, chacun ayant la page unique mentionnée.

* Initialisez l'objet [SplitOptions][14] avec le fichier de sortie et le mode à diviser.
* Instanciez l'objet [Merger][15] avec le fichier source ou le flux à scinder.
* Appelez la méthode [split][16] pour diviser le document fourni et le sauvegarder.

```
String filePath = "document.pdf";
String filePathOut = "document\_{0}.{1}";
// Split the document into multiple single page documents.
SplitOptions splitOptions = new SplitOptions(filePathOut, new int\[\] { 3, 6, 8 });
Merger merger = new Merger(filePath);
merger.split(splitOptions);
```

### Diviser le document en documents multipages

Si vous avez un document de 6 pages, la petite modification mentionnée ci-dessous dans le code ci-dessus divisera votre document en 3 documents distincts de la manière suivante :

<figure class="wp-block-table is-style-stripes"><table><tbody><tr><td>**Nom du document</td><td> <strong>Numéros de page**</strong></td></tr><tr><td> document_1</td><td> 1, 2</td></tr><tr><td> document_2</td><td> 3, 4, 5</td></tr><tr><td> document_3</td><td> 6</td></tr></tbody></table></figure>

```
SplitOptions splitOptions = new SplitOptions(filePathOut,  SplitMode.Interval, new int\[\] { 3, 6 },);
```

### Diviser par plage de pages de début et de fin

Si vous souhaitez diviser un document en fournissant simplement la plage de pages, voici comment une présentation Powerpoint peut être divisée en 3 présentations d'une seule page.

```
String filePath = "presentation.ppt";
String filePathOut = "presentation\_{0}.{1}";
// Split the presentation into multiple single page presentations.
SplitOptions splitOptions = new SplitOptions(filePathOut, 3, 5);
Merger merger = new Merger(filePath);
merger.split(splitOptions)
```

### Diviser par plages de pages paires ou impaires

Vous pouvez définir les plages de pages paires et impaires à diviser. Suivre SplitOptions permettra de diviser le document fourni en plusieurs documents d'une page pour les pages impaires comprises entre 3 et 8.

```
SplitOptions splitOptions = new SplitOptions(filePathOut, 3, 8, RangeMode.OddPages);
```

## Formats de documents pris en charge

Comme promis, voici la liste des formats de documents qui peuvent être fusionnés ou séparés avec les exemples ci-dessus. Vous pouvez visiter [docs][17] à tout moment pour consulter la liste mise à jour.

<figure class="wp-block-table is-style-stripes"><table><tbody><tr><td>**Type de document</td><td> <strong>Formats de fichiers**</strong></td></tr><tr><td> Traitement de texte</td><td> DOC, DOCX, DOCM, POINT, DOTX, DOTM, ODT, OTT, RTF, TXT</td></tr><tr><td> Feuilles de calcul</td><td> XLS, XLSX, XLSM, XLSB, XLT, XLTX, XLTM, ODS, CSV, TSV</td></tr><tr><td> Présentations</td><td> PPT, PPTX, PPS, PPSX, ODP, OTP</td></tr><tr><td> Dessins</td><td> VSDX, VSDM, VSSX, VSSM, VSTX, VSTM, VDX, VSX, VTX</td></tr><tr><td> la toile</td><td> HTML, MHT</td></tr><tr><td> Langages de description de page</td><td> TEX, XPS</td></tr><tr><td> Livres électroniques et autres</td><td> PDF, EPUB, ONE</td></tr></tbody></table></figure>

C'est bon de vous voir ici, vous pouvez nous contacter librement sur le [forum][18] au cas où vous auriez des difficultés ou des confusions ou si vous voulez donner de bonnes suggestions.







[1]: https://products.groupdocs.com/merger
[2]: https://products.groupdocs.com/merger/java
[3]: https://blog.groupdocs.com/2020/05/20/merge-pdf-word-excel-powerpoint-documents-in-java/#merge-pdf-files-in-java
[4]: https://blog.groupdocs.com/2020/05/20/merge-pdf-word-excel-powerpoint-documents-in-java/#merge-excel-ppt-and-word-docs-in-java
[5]: https://blog.groupdocs.com/2020/05/20/merge-pdf-word-excel-powerpoint-documents-in-java/#merge-document-pages-in-java
[6]: https://blog.groupdocs.com/2020/05/20/merge-pdf-word-excel-powerpoint-documents-in-java/#split-documents-in-java
[7]: https://products.groupdocs.com/merger/java
[8]: https://downloads.groupdocs.com/merger/java
[9]: https://github.com/groupdocs-merger/GroupDocs.Merger-for-Java
[10]: https://apireference.groupdocs.com/java/merger/com.groupdocs.merger/Merger
[11]: https://apireference.groupdocs.com/java/merger/com.groupdocs.merger/Merger#join(java.lang.String)
[12]: https://apireference.groupdocs.com/java/merger/com.groupdocs.merger/Merger#save(java.lang.String)
[13]: https://apireference.groupdocs.com/merger/java/com.groupdocs.merger.domain.options/JoinOptions
[14]: https://apireference.groupdocs.com/java/merger/com.groupdocs.merger.domain.options/SplitOptions
[15]: https://apireference.groupdocs.com/java/merger/com.groupdocs.merger/Merger
[16]: https://apireference.groupdocs.com/java/merger/com.groupdocs.merger/Merger#split(com.groupdocs.merger.domain.options.interfaces.IPageSplitOptions)
[17]: https://docs.groupdocs.com/merger/java
[18]: https://forum.groupdocs.com/c/merger


