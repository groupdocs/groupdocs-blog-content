---
title: "Extraire des images d'EPUB, FB2, CHM eBooks en Java"
date: Mon, 15 Mar 2021 15:01:00 +0000
draft: false
url: /fr/2021/03/15/extraire-images-des-ebooks-en-java/
author: 'Shoaib Khan'
summary: "Les **eBooks** de différents formats sont très courants dans l'utilisation quotidienne. L'eBook peut contenir du texte ainsi que des images. Si vous souhaitez utiliser les images de n'importe quel livre électronique ailleurs, vous pouvez les extraire facilement par programmation dans votre application Java. Dans cet article, vous apprendrez à automatiser **comment extraire des images de fichiers eBook** tels que **EPUB, PDF, FB2, CHM** en **Java**."
tags: ['Extract Images from CHM in Java', 'Extract Images from eBooks in Java', 'Extract Images from FB2 in Java', 'extract images in Java', 'Parse eBooks in Java', 'Parse eBooks to Extract Images in Java']
categories: ['GroupDocs.Parser Product Family']
---

Les **eBooks** de différents formats sont très courants dans l'utilisation quotidienne. L'eBook peut contenir du texte ainsi que des images. Si vous souhaitez utiliser les images de n'importe quel livre électronique ailleurs, vous pouvez les extraire facilement par programmation dans votre application Java. Dans cet article, vous apprendrez à automatiser **comment extraire des images de fichiers eBook** tels que **EPUB, PDF, FB2, CHM** en **Java**.

Les sujets suivants seront abordés ci-dessous :

* [API Java - Extraction d'images à partir d'eBooks][2]
* [Extraire des images d'un livre électronique EPUB en Java][3]
* [Extraire des images de PDF, FB2, CHM eBooks en Java][4]

## API Java pour extraire des images de livres électroniques {#image-extraction-java-api-for-ebooks}

L'API [GroupDocs.Parser for Java][5] est une API d'automatisation riche en fonctionnalités permettant d'extraire des images de livres électroniques et de documents en Java. En plus de cela, l'API prend en charge l'analyse et l'extraction d'images, de texte et de métadonnées à partir de documents de traitement de texte, de feuilles de calcul, de PDF, de présentations, d'e-mails, d'archives ZIP et de nombreux autres [formats de document pris en charge][6].

### Télécharger et configurer

Obtenez le fichier JAR à partir de la section [downloads][7] ou ajoutez simplement la configuration pom.xml suivante dans vos applications Java basées sur Maven pour essayer les exemples mentionnés ci-dessous. Pour plus de détails, vous pouvez visiter la [API Reference][8].

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
	<version>21.2</version> 
</dependency>
```

## Extraire des images d'un livre électronique EPUB en Java {#extract-images-from-epub-in-java}

Commençons par l'eBook EPUB pour l'analyser à la recherche d'images. Les étapes suivantes analysent le livre électronique EPUB et en extraient toutes les images à l'aide du code Java.

* Créez un objet de classe [Parser][9] avec l'eBook.
* Utilisez la méthode [getImages][10] pour extraire toutes les images du livre électronique EPUB.
* Parcourez les images extraites et enregistrez-les sur le disque.



{{< figure align=center src="images/alice.png" alt="Livre électronique EPUB avec images" caption="Livre électronique EPUB d'Adobe [Sample eBook Library][11]">}}


Le code Java suivant analyse le livre électronique EPUB et enregistre les images du livre électronique une par une sur le disque.

```
// Analysez des livres électroniques pour extraire des images de fichiers PDF, EPUB, FB2, CHM en Java et enregistrez-les sur le disque.
Parser parser = new Parser("ebook.epub");
// Extrayez des images d'un livre électronique et enregistrez-les au format JPEG.
Iterable<PageImageArea> images = parser.getImages();
ImageOptions options = new ImageOptions(ImageFormat.Jpeg);
int imageNumber = 0;
// Itérer sur les images extraites
for (PageImageArea image : images) {
    image.save(Constants.getOutputFilePath(String.format("%d.jpeg", imageNumber)), options);
    imageNumber++;
}
```



{{< figure align=center src="images/alice-image-from-epub.jpg" alt="Image extraite du livre électronique EPUB">}}


Par conséquent, toutes les images seront enregistrées à l'emplacement indiqué. Voici l'une des images présentées à titre d'exemple.

Les images peuvent être enregistrées dans l'un des formats de fichier image suivants :

*JPG
*PNG
* WEBP
* GIF
* BMP

## Extraire des images de PDF, FB2, CHM eBooks en Java {#extract-images-from-pdf-fb2-chm-in-java}

En plus du format EPUB, si vous avez votre eBook au format PDF, FB2, CHM ou avec un autre format, vous pouvez extraire leurs images de la même manière. Passez simplement votre eBook au constructeur **Parser** lors de la création de l'objet. Après cela, la méthode **getImages** extraira les images de vos livres électroniques fournis en utilisant le même code Java.

```
// Provide different eBook formats to the Parser constructor to extract the images.
// Parser parser = new Parser("ebook.epub");
Parser parser = new Parser("ebook.pdf");
// Parser parser = new Parser("ebook.fb2");
// Parser parser = new Parser("ebook.chm");

Iterable<PageImageArea> images = parser.getImages();
```

## Conclusion

Dans cet article, vous avez appris à obtenir par programmation toutes les images des livres électroniques PDF, EPUB, FB2, CHM dans vos applications Java. Vous pouvez maintenant essayer de créer votre propre application Java d'extraction d'images à l'aide de l'API [GroupDocs.Parser for Java][12].

Pour en savoir plus sur l'API, vous pouvez consulter la [documentation][13] ou des exemples open source sur [GitHub][14]. Pour tout autre problème, vous pouvez contacter le support rapide sur le [forum][15].

## Voir également

* [Extraire des images d'EPUB, FB2, CHM eBooks en C#][16]
* [Extraire les données des factures et des reçus en Java][17]







[1]: https://blog.groupdocs.com/2021/03/15/extract-images-from-ebooks-in-java/
[2]: #image-extraction-java-api-for-ebooks
[3]: #extract-images-from-epub-in-java
[4]: #extract-images-from-pdf-fb2-chm-in-java
[5]: https://products.groupdocs.com/parser/java
[6]: https://docs.groupdocs.com/parser/java/supported-document-formats/
[7]: https://downloads.groupdocs.com/parser/java
[8]: https://apireference.groupdocs.com/parser/java
[9]: https://apireference.groupdocs.com/parser/java/com.groupdocs.parser/Parser
[10]: https://apireference.groupdocs.com/parser/java/com.groupdocs.parser/Parser#getImages()
[11]: https://www.adobe.com/solutions/ebook/digital-editions/sample-ebook-library.html
[12]: https://products.groupdocs.com/parser/net
[13]: https://docs.groupdocs.com/parser/java
[14]: https://github.com/groupdocs-parser/GroupDocs.Parser-for-Java
[15]: https://forum.groupdocs.com/c/parser/
[16]: https://blog.groupdocs.com/2021/02/26/extract-images-from-ebooks-in-csharp/
[17]: https://blog.groupdocs.com/2021/01/22/extract-data-from-invoices-or-receipts-in-java/


