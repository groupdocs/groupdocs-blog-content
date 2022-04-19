---
title: "Insérer des objets OLE dans Word, Excel, PowerPoint à l'aide de Java"
date: Mon, 19 Oct 2020 06:02:40 +0000
draft: false
url: /fr/2020/10/19/insert-ole-objects-in-word-excel-powerpoint-with-java/
author: 'Shoaib Khan'
summary: "Aujourd'hui, nous allons apprendre à ** intégrer des PDF ** et d'autres documents différents ** en tant qu'objets OLE dans des fichiers Word, Excel, PowerPoint à l'aide de Java **. Pour intégrer les documents via **Object Linking and Embedding**, nous utiliserons l'API GroupDocs.Merger pour Java qui nous permet également de combiner/fusionner et diviser efficacement plusieurs documents avec un minimum de lignes de code Java."
tags: ['embed OLE objects using Java', 'insert OLE objects in Excel using Java', 'insert OLE objects in java', 'insert OLE objects in presentations using Java', 'insert OLE objects in Word using Java']
categories: ['GroupDocs.Merger Product Family']
---

Dans l'un des messages précédents, nous avons appris à programmer [insérer les objets OLE dans les documents avec C #][1]. Aujourd'hui, dans cet article, nous allons intégrer des PDF et d'autres documents différents en tant qu'objets ** OLE dans des documents Word, des feuilles de calcul Excel, des diapositives de présentation PowerPoint à l'aide de Java **.

Cet article vous guidera sur :

* [API Java pour les objets OLE][2]
* [Insérer des objets OLE dans des documents MS Word à l'aide de Java][3]
* [Ajouter des objets OLE dans des feuilles de calcul Excel à l'aide de Java][4]
* [Insérer des documents dans des présentations via OLE en utilisant Java][5]

## API Java pour les objets OLE {#java-api-for-ole-objects}



{{< figure align=center src="images/groupdocs-merger-java-90x90-no-reply.png" alt="GroupDocs. Merger pour Java">}}


Les étapes et les exemples de cet article utilisent [GroupDocs.Merger pour Java][6] pour insérer des documents dans d'autres documents via OLE (_Object Linking and Embedding_). Cette API nous permet également de combiner et de diviser efficacement plusieurs documents avec un minimum de lignes de code Java. Avant de continuer, il sera préférable de préparer l'environnement de l'une de vos manières pertinentes :

1. **Téléchargez** l'API à partir de la section [downloads][7].
2. Pour les projets **basés sur Maven**, voici la configuration de votre **pom.xml**

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
        <artifactId>groupdocs-merger</artifactId>
        <version>20.7</version> 
</dependency>
```

## Insérer un PDF en tant qu'objet OLE dans un document MS Word à l'aide de Java {#insert-ole-object-into-word-in-java}



{{< figure align=center src="images/PDF-in-Word.png" alt="Insérer un PDF dans un document Word">}}


L'étape et l'exemple de code ci-dessous **insèrent le document PDF dans un document Word en tant qu'objet OLE dans Java** à l'aide de l'API GroupDocs.Merger.

1. Instanciez l'objet [Merger][8] avec le chemin ou le flux du document de traitement de texte source.
2. Initialisez [OleWordProcessingOptions][9] avec le chemin du document PDF qui sera intégré dans le document Word.
3. Appelez la méthode [importDocument][10] de la classe de fusion.
4. Enregistrez le document Word résultant en appelant la méthode [save][11].

```
// Incorporer un PDF dans un document Word en tant qu'objet OLE
int pageNumber = 1;
OleWordProcessingOptions oleWordsOptions = new OleWordProcessingOptions("PDF-document.pdf", pageNumber);
oleWordsOptions.setWidth(200); // Setting the width and height of embedded document
oleWordsOptions.setHeight(200);
// Importer le PDF dans le document Word
Merger merger = new Merger("document.docx"); // Source Word document
merger.importDocument(oleWordsOptions);
merger.save("output-document.docx");
```

## Insérer un document Word en tant qu'objet OLE dans une feuille de calcul Excel à l'aide de Java {#insert-ole-object-into-excel-in-java}



{{< figure align=center src="images/Word-in-Excel.png" alt="Insérer un fichier Word dans une feuille de calcul Excel">}}


Les feuilles de calcul peuvent également incorporer d'autres documents, tels que des documents Word, des feuilles de calcul, des présentations, des images ou des clips audio, etc. Ici, j'ajoute un document Word dans une feuille de calcul en tant qu'objet OLE.

1. Initialisez l'objet de classe [OleSpreadsheetOptions][12] en fournissant le chemin du document Word qui sera intégré dans la feuille de calcul.
2. Définissez les options telles que les positions des lignes et des colonnes.
3. Initialisez l'objet de classe [Merger][13] avec le chemin du document de feuille de calcul.
4. Appelez la méthode [importDocument][14] en fournissant l'option de feuille de calcul OLE déjà définie.
5. Enregistrez la feuille de calcul résultante contenant le document Word intégré en appelant la méthode [save][15].

```
// Incorporer un document Word dans une feuille de calcul Excel en tant qu'objet OLE
int pageNumber = 1;
OleSpreadsheetOptions oleCellsOptions = new OleSpreadsheetOptions("document.docx", pageNumber);
oleCellsOptions.setRowIndex(2); // Set row & column number of Spreasheet to embedded document
oleCellsOptions.setColumnIndex(1);
// Importer le document Word dans la feuille de calcul
Merger merger = new Merger("spreadsheet.xlsx"); // Source Spreadsheet
merger.importDocument(oleCellsOptions);
merger.save("output-spreadsheet.xlsx");
```

## Insérer une feuille Excel en tant qu'objet OLE dans la présentation à l'aide de Java {#insert-ole-object-into-ppt-in-java}



{{< figure align=center src="images/Add-Excel-Sheet-in-PPT-Presentation-OLE.png" alt="Insérer une feuille Excel dans PowerPoint">}}


De même, si nous avons besoin d'ajouter des documents externes à nos présentations, ceux-ci peuvent être insérés à l'endroit précis avec les quelques lignes de code Java mentionnées ci-dessous :

1. Initialisez l'objet de classe [OlePresentationOptions][16] et transmettez le chemin du document de feuille de calcul.
2. Définissez les options de présentation OLE telles que les coordonnées x et y, la hauteur et la largeur pour la prochaine feuille de calcul intégrée.
3. Instanciez l'objet de classe [Merger][17] avec le chemin du document de présentation comme paramètre.
4. Intégrez la feuille de calcul dans la présentation à l'aide de la méthode [importDocument][18] de la classe Merger.
5. Appelez la méthode [save][19] pour obtenir le fichier de présentation résultant.

```
// Incorporer une feuille de calcul dans une présentation en tant qu'objet OLE
int pageNumber = 1;
OlePresentationOptions oleSlidesOptions = new OlePresentationOptions("spreadsheet.xlsx", pageNumber);
// Définir les coordonnées et les dimensions
oleSlidesOptions.setX(10);
oleSlidesOptions.setY(10);
oleSlidesOptions.setHeight(200);
oleSlidesOptions.setWidth(200);
// Importer la feuille de calcul dans la présentation
Merger merger = new Merger("presentation.pptx");
merger.importDocument(oleSlidesOptions);
merger.save("output-presentation.pptx");
```

## Conclusion

Nous avons appris **comment insérer par programmation des objets OLE dans des documents Word, Excel et Powerpoint à l'aide de Java**. La principale différence lors de l'incorporation des documents dans différents types de documents source réside simplement dans l'utilisation de la classe d'options OLE respective. C'est ça.

Pour en savoir plus sur l'API Merger pour Java, consultez la [documentation][20]. En cas de question, l'équipe d'assistance de GroupDocs se fera un plaisir de vous aider sur [Forum d'assistance gratuit][21].

## Voir également

* [Insérer des objets OLE dans Word, Excel, PowerPoint en utilisant C#][22]







[1]: https://blog.groupdocs.com/2020/05/16/insert-ole-objects-in-word-excel-powerpoint-with-csharp/
[2]: #java-api-for-ole-objects
[3]: #insert-ole-object-into-word-in-java
[4]: #insert-ole-object-into-excel-in-java
[5]: #insert-ole-object-into-ppt-in-java
[6]: https://products.groupdocs.com/merger/java/
[7]: https://downloads.groupdocs.com/merger/java
[8]: https://apireference.groupdocs.com/merger/java/com.groupdocs.merger/Merger
[9]: https://apireference.groupdocs.com/merger/java/com.groupdocs.merger.domain.options/OleWordProcessingOptions
[10]: https://apireference.groupdocs.com/merger/java/com.groupdocs.merger/Merger#importDocument(com.groupdocs.merger.domain.options.interfaces.IImportDocumentOptions)
[11]: https://apireference.groupdocs.com/merger/java/com.groupdocs.merger/Merger#save(java.lang.String)
[12]: https://apireference.groupdocs.com/merger/java/com.groupdocs.merger.domain.options/OleSpreadsheetOptions
[13]: https://apireference.groupdocs.com/merger/java/com.groupdocs.merger/Merger
[14]: https://apireference.groupdocs.com/merger/java/com.groupdocs.merger/Merger#importDocument(com.groupdocs.merger.domain.options.interfaces.IImportDocumentOptions)
[15]: https://apireference.groupdocs.com/merger/java/com.groupdocs.merger/Merger#save(java.lang.String)
[16]: https://apireference.groupdocs.com/merger/java/com.groupdocs.merger.domain.options/OlePresentationOptions
[17]: https://apireference.groupdocs.com/merger/java/com.groupdocs.merger/Merger
[18]: https://apireference.groupdocs.com/merger/java/com.groupdocs.merger/Merger#importDocument(com.groupdocs.merger.domain.options.interfaces.IImportDocumentOptions)
[19]: https://apireference.groupdocs.com/merger/java/com.groupdocs.merger/Merger#save(java.lang.String)
[20]: https://docs.groupdocs.com/merger/java/
[21]: https://forum.groupdocs.com/c/merger
[22]: https://blog.groupdocs.com/2020/05/16/insert-ole-objects-in-word-excel-powerpoint-with-csharp/


