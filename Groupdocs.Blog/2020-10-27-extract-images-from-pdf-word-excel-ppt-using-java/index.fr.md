---
title: "Extraire des images de documents à l'aide de Java"
date: Tue, 27 Oct 2020 05:04:09 +0000
draft: false
url: /fr/2020/10/27/extraire-images-du-pdf-word-excel-ppt-en-utilisant-java/
author: 'Shoaib Khan'
summary: "Aujourd'hui, nous allons apprendre à **extraire par programme des images de documents PDF, Excel, PowerPoint et Word à l'aide de Java**. Pour l'extraction des images, nous utiliserons [GroupDocs.Parser for Java][1]. Cette API Java prend en charge l'analyse de documents et l'extraction d'images, de texte et de métadonnées à partir de documents de traitement de texte, de feuilles de calcul, de présentations, d'archives et de documents de courrier électronique. Les images extraites peuvent être enregistrées aux formats **BMP**, **GIF**, **JPEG**, **PNG** et **WebP**."
tags: ['extract images from documents in java', 'extract images from PDF in Java', 'extract images from word in java', 'extract images in Java']
categories: ['GroupDocs.Parser Product Family']
---

Si vous avez un document et que vous souhaitez utiliser les images à l'intérieur de ce document dans d'autres documents, voici l'une des solutions. Dans cet article, nous allons apprendre à **extraire par programme des images de documents PDF, Excel, PowerPoint et Word à l'aide de Java**.

* [API Java d'extraction d'images][2]
* [Extraction d'images à partir de documents PDF en Java][3]
* [Extraire des images de documents Word, Excel, PowerPoint en Java][4]
* [Extraire l'image d'une page spécifique en Java][5]



{{< figure align=center src="images/extract-images-from-documents-in-java-1.png" alt="Extraire des images de documents en Java">}}


## API Java d'extraction d'images {#image-extraction-java-api}



{{< figure align=center src="images/groupdocs-parser-java.png" alt="Analyser des documents et extraire des données en Java">}}


Pour l'extraction des images, nous utiliserons [GroupDocs.Parser for Java][6]. Cette API Java prend en charge l'**analyse de documents** et l'**extraction d'images, de texte** et de **métadonnées** à partir de **documents de traitement de texte**, de **feuilles de calcul**, de **présentations, d'archives ,** et **envoyer par e-mail** des documents. Voici les formats de document pris en charge par l'API Java pour l'extraction d'images.

<figure class="wp-block-table is-style-stripes"><table><tbody><tr><td>**Documents de traitement de texte</td><td> DOC, DOCX, DOCM, POINT, DOTX, DOTM, ODT, OTT, RTF</td></tr><tr><td> <strong>Feuilles de calcul</strong></td><td> XLS, XLSX, XLSM, XLSB, XLT, XLTX, XLTM, ODS, OTS, XLA, XLAM, NUMÉROS</td></tr><tr><td> <strong>Présentations</strong></td><td> PPT, PPTX, PPTM, PPS, PPSX, PPSM, POT, POTX, POTM, ODP, OTP</td></tr><tr><td> <strong>Documents portables</strong></td><td> PDF</td></tr><tr><td> <strong>E-mails</strong></td><td> EML, EMLX, MSG</td></tr><tr><td> <strong>Les archives**</strong></td><td> ZIP *: FRANÇAIS</td></tr></tbody></table></figure>

Avant de commencer avec les exemples ci-dessous, je vous recommande de configurer l'environnement en téléchargeant la dernière version de l'API Java d'analyse de documents à partir de la [section des téléchargements][7] ou vous pouvez définir les configurations suivantes dans votre **maven-based* * applicatifs java :

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
	<artifactId>groupdocs-parser</artifactId>
	<version>20.8</version> 
</dependency>
```

## Extraire des images de documents PDF en Java {#extract-images-from-pdf-in-java}



{{< figure align=center src="images/PDF-with-Images.png" alt="Document PDF pour extraire des images">}}


Suivez ces étapes simples pour obtenir toutes les images du document PDF.

1. Instanciez l'objet de classe [**Parser**][8].
2. Appelez la méthode **[getImages][9]** de la classe Parser pour obtenir toutes les images.
3. Itérer sur les images en utilisant **[PageImageArea][10]**.
4. Enregistrez les images à l'aide de la méthode d'enregistrement de PageImageArea.

C'est fait. Voir le code complet ci-dessous. Les images extraites peuvent être enregistrées aux formats **BMP**, **GIF**, **JPEG**, **PNG** et **WebP**.

```
// Extraire des images de documents Word, Excel, PowerPoint et PDF par programmation à l'aide de GroupDocs.Parser pour Java
try (Parser parser = new Parser("path/document.pdf")) {
	// Extract images
	Iterable<PageImageArea> images = parser.getImages();

	// Create the options to save images in PNG format
	ImageOptions options = new ImageOptions(ImageFormat.Png);
	int imageNumber = 0;

	// Iterate over images and Save
	for (PageImageArea image : images) {
		// Print the page index, rectangle and image file type:
		System.out.println(String.format("Page: %d, R: %s, Type: %s", image.getPage().getIndex(), 
				image.getRectangle(), image.getFileType()));
		image.save(String.format("filesPath/image_%d.png", imageNumber), options);
		imageNumber++;
	}
}
```

Ce sont les images extraites du document PDF en utilisant le code ci-dessus.



{{< figure align=center src="images/Extracted-Images-from-PDF-using-GroupDocs.Parser-for-Java.png" alt="Images extraites du document à l'aide de Java">}}


## Extraire des images de fichiers Word, Excel, PowerPoint en Java {#extract-images-from-word-excel-ppt-in-java}

De même, toutes les images peuvent être extraites des fichiers de traitement de texte, des tableurs, des présentations, avec la base de code inchangée. Qu'est-ce que tu dois changer ? Juste le chemin du document source et la bonne extension de fichier.

```
Parser parser = new Parser("path/document.docx") // Word Document
// Parser parser = new Parser("path/document.xlsx") // Excel Spreadsheet
// Parser parser = new Parser("path/document.pptx") // PowerPoint Presentation
// Parser parser = new Parser("path/document.pdf") // PDF Document

```

## Extraction d'image à partir d'une page de document spécifique en Java {#extract-images-from-specific-page-in-java}

Si vous ne souhaitez pas extraire toutes les images de l'ensemble du document mais d'une page spécifique. Le code ci-dessous montre comment nous pouvons extraire des images d'une page particulière du document en Java.

```
// Extraire des images d'une page spécifique de Word, Excel, PowerPoint, PDF en Java à l'aide de GroupDocs.Parser
try (Parser parser = new Parser("path/document.pdf"")) {
	// Get the document info
	IDocumentInfo documentInfo = parser.getDocumentInfo();

	// Create the options to save images in PNG format
	ImageOptions options = new ImageOptions(ImageFormat.Jpeg);
	int imageNumber = 0;

	// Iterate over pages
	for (int pageIndex = 0; pageIndex < documentInfo.getPageCount(); pageIndex++) {
		// Print Page Numbers
		System.out.println(String.format("Page %d/%d", pageIndex + 1, documentInfo.getPageCount()));

		// Iterate over images - Ignoring NULL-Checking in the examples
		for (PageImageArea image : parser.getImages(pageIndex)) {
			// Print Image Information and Save file
			System.out.println(String.format("R: %s, Text: %s", image.getRectangle(), image.getFileType()));
			image.save(String.format("filesPath/image_%d.jpeg", imageNumber), options);
			imageNumber++;
		}
	}
}
```

## Conclusion

Aujourd'hui, nous avons appris **comment extraire des images de l'ensemble du document et de la page spécifique des documents de traitement de texte, des feuilles de calcul, des présentations et des PDF en Java**. Il n'y a aucune différence dans le code si nous devons extraire des images des fichiers de différents formats de fichiers. Nous devons juste passer le bon chemin et le nom. C'est ça.

## Voir également

* [Extraire des images de documents en C#][11]
* [Extraire des images de documents sur le cloud à l'aide de Python][12]







[1]: https://products.groupdocs.com/parser/java
[2]: #image-extraction-java-api
[3]: #extract-images-from-pdf-in-java
[4]: #extract-images-from-word-excel-ppt-in-java
[5]: #extract-images-from-specific-page-in-java
[6]: https://products.groupdocs.com/parser/java
[7]: https://downloads.groupdocs.com/parser/java
[8]: https://apireference.groupdocs.com/java/parser/com.groupdocs.parser/Parser
[9]: https://apireference.groupdocs.com/java/parser/com.groupdocs.parser/Parser#getImages()
[10]: https://apireference.groupdocs.com/java/parser/com.groupdocs.parser.data/PageImageArea
[11]: https://blog.groupdocs.com/2020/10/28/extract-images-from-pdf-word-excel-ppt-using-csharp/
[12]: https://blog.groupdocs.cloud/2020/10/25/extract-images-from-word-excel-ppt-pdf-using-python/


