---
title: "Extraire les données des fichiers ZIP en Java"
date: Wed, 08 Sep 2021 13:14:00 +0000
draft: false
url: /fr/2021/09/08/extract-zip-files-data-in-java/
author: 'Shoaib Khan'
summary: "Les archives ZIP sont l'un des formats de fichiers compressés les plus populaires et les plus couramment utilisés. La principale raison d'utiliser des fichiers ZIP est de réduire la taille totale du fichier et d'envoyer plusieurs fichiers en une seule archive. En tant que développeur, vous pouvez extraire le texte, les images et même les métadonnées des fichiers compressés dans les archives ZIP. Dans cet article, nous discuterons de **comment extraire les données des archives ZIP en Java**."
tags: ['Extract Archives in Java', 'Extract from ZIP', 'Extract from ZIP in Java', 'unzip data in Java']
categories: ['GroupDocs.Parser Product Family']
---

Les archives ZIP sont l'un des formats de fichiers compressés les plus populaires et les plus couramment utilisés. La principale raison d'utiliser des fichiers ZIP est de réduire la taille totale du fichier et d'envoyer plusieurs fichiers en une seule archive. En tant que développeur, vous pouvez extraire le texte, les images et même les métadonnées des fichiers compressés dans les archives ZIP. Dans cet article, nous verrons **comment extraire des données d'archives ZIP en Java**.



{{< figure align=center src="images/extract-data-from-zip-files-in-java.jpg" alt="Extraire des données de fichiers ZIP en Java">}}


Les sujets suivants sont traités ci-dessous :

* [API Java pour l'extraction de données de fichiers ZIP.][1]
* [Comment extraire les données des fichiers ZIP à l'aide de Java.][2]
* [Extraire des images à partir de fichiers dans des fichiers ZIP en Java][3]

## API Java pour extraire les données des fichiers ZIP {#zip-files-data-extraction-java-api}

[GroupDocs.Parser][4] fournit la solution d'analyse de documents pour les développeurs qui inclut également l'API Java. J'utiliserai cette [API Java pour extraire les données des fichiers ZIP][5] dans les exemples de cet article. De plus, cette API permet l'extraction de données d'images, de texte brut, de texte structuré et formaté et de métadonnées à partir d'une longue liste de [formats de documents pris en charge][6]. Ces formats de documents incluent les documents de traitement de texte, les PDF, les présentations, les feuilles de calcul, les e-mails, les bases de données, les livres électroniques et bien d'autres.

### Télécharger ou configurer

Vous pouvez télécharger le fichier **JAR** à partir de la [section téléchargements][7], ou simplement obtenir les dernières configurations de référentiel et de dépendances pour le pox.xml de vos applications Java **basées sur maven**.

```
<repository>
	<id>GroupDocsJavaAPI</id>
	<name>GroupDocs Java API</name>
	<url>https://repository.groupdocs.com/repo/</url>
</repository>
```
```
<dependency>
	<groupId>com.groupdocs</groupId>
	<artifactId>groupdocs-parser</artifactId>
	<version>21.2</version> 
</dependency>
```

## Comment extraire des données de fichiers ZIP en Java {#how-to-extract-zip-data}

Pour extraire les données de n'importe quel fichier inclus dans l'archive, vous devez d'abord obtenir tous les fichiers joints. Après cela, vous pouvez extraire davantage tout type de données de chaque fichier. Les étapes suivantes montrent comment extraire les données des fichiers ZIP et récupérer le texte de chaque fichier joint en Java.

* Chargez l'archive ZIP en utilisant la classe **[Parser][8]**.
* Extrayez la collection de pièces jointes à l'aide de la méthode **_[getContainer][9]_**.
* Parcourez les pièces jointes pour les données de chaque fichier joint.
* Vous pouvez obtenir ses différents types de données en utilisant les méthodes respectives de la classe **Parser**.

Le code source montre comment extraire les données des fichiers ZIP à l'aide de Java. L'exemple ci-dessous extrait le texte entier de tous les fichiers de l'archive ZIP.

```
// Extraire les données des archives ZIP en Java
Parser parser = new Parser("path/archive.zip");
// Extraire les pièces jointes du conteneur
Iterable<ContainerItem> attachments = parser.getContainer();

// Itérer sur la collection d'entités ZIP
for (ContainerItem item : attachments) {
    // Print the FILE INFO
    System.out.println("-----------------------------------");
    System.out.println("Name: " + item.getName());
    System.out.println("File Size: " + item.getSize() + " Bytes");
    System.out.println("-----------------------------------");

    try {
        Parser attachmentParser = item.openParser();
        TextReader reader = attachmentParser.getText();
        System.out.println(reader == null ? "No text" : reader.readToEnd());
    } 
    catch (UnsupportedDocumentFormatException ex) {
        System.out.println("Isn't supported.");
    }
}
```

La sortie du code source ci-dessus montre le texte récupéré de l'un des fichiers PDF dans le fichier ZIP.

```
 -----------------------------------
 Name: sample.pdf
 File Size: 33370 Bytes
 -----------------------------------

 Heading

 This is the first paragraph of the sample document that contains some sample
 text, bulleted list, numbered list and more.

    •  Bullet Item 1
    •  Bullet Item 2
    •  Bullet Item 3
 
 This is the second paragraph of the sample document and after this, there is a
 numbered list: 

    1. Numbered Item 1
    2. Numbered Item 2
    3. Numbered Item 3 
```

## Extraire des images à partir de fichiers dans des fichiers ZIP en Java {#extract-images-from-zip-data}

Non limité au texte, vous pouvez également extraire de la même manière les informations sur les images. Les étapes suivantes montrent comment extraire les données des fichiers ZIP et récupérer les informations sur les images de chaque fichier joint.

* Chargez l'archive ZIP en utilisant la classe **[Parser][10]**.
* Extrayez la collection de pièces jointes à l'aide de la méthode **_[getContainer][11]_**.
* Parcourez les pièces jointes pour obtenir la collection d'images dans chaque pièce jointe.
* Parcourez maintenant les images pour obtenir les informations de chaque image en utilisant la classe **[PageImageArea][12]**.

Le code source suivant montre comment extraire des données d'images à partir des fichiers inclus dans les fichiers ZIP en Java.

```
// Extraire les informations sur les images du fichier dans l'archive ZIP en Java
Parser parser = new Parser("path/archive.zip");
// Extraire les pièces jointes du conteneur
Iterable<ContainerItem> attachments = parser.getContainer();

// Itérer sur la collection d'entités ZIP
for (ContainerItem item : attachments) {
    try {
        Parser attachmentParser = item.openParser();
        Iterable<PageImageArea> images = attachmentParser.getImages();
        if (images != null) {
            int imageCount = 1;
            for (PageImageArea image : images) {
                // Print a page index, rectangle and image type:
                System.out.println(String.format("Image# %d \nPage: %d\nFile Type: %s", imageCount, image.getPage().getIndex()+1, image.getFileType()));
                imageCount++;
            }
        }
    } 
    catch (UnsupportedDocumentFormatException ex) {
        System.out.println("Isn't supported.");
    }
}
```

```
Image# 1 
Page: 1
File Type: JPEG Image (.jpeg) 
```

## Obtenez une licence API gratuite

Vous pouvez [obtenir une licence temporaire gratuite][13] pour utiliser l'API sans les limitations d'évaluation.

## Conclusion

En bref, vous avez appris à extraire des données d'archives ZIP dans vos applications Java. De plus, vous pouvez également extraire des images des fichiers ZIP à l'aide de GroupDocs.Parser pour Java. Commencez à créer votre application Java d'extraction de données pour les fichiers compressés. Pour en savoir plus sur l'API, consultez la [documentation][14]. Pour toute question, contactez-nous via le [forum][15].

## Voir également

* [Extraire les données des fichiers ZIP en C #][16]
* [Obtenir des images à partir de documents à l'aide de Java][17]
* [Extraire des images d'EPUB, FB2, CHM eBooks en Java][18]







[1]: #zip-files-data-extraction-java-api
[2]: #how-to-extract-zip-data
[3]: #extract-images-from-zip-data
[4]: https://products.groupdocs.com/parser/
[5]: https://products.groupdocs.com/parser/java/
[6]: https://docs.groupdocs.com/parser/java/supported-document-formats/
[7]: https://downloads.groupdocs.com/parser
[8]: https://apireference.groupdocs.com/parser/java/com.groupdocs.parser/Parser
[9]: https://apireference.groupdocs.com/parser/java/com.groupdocs.parser/Parser#getContainer()
[10]: https://apireference.groupdocs.com/parser/java/com.groupdocs.parser/Parser
[11]: https://apireference.groupdocs.com/parser/java/com.groupdocs.parser/Parser#getContainer()
[12]: https://apireference.groupdocs.com/parser/java/com.groupdocs.parser.data/PageImageArea
[13]: https://purchase.groupdocs.com/temporary-license
[14]: https://docs.groupdocs.com/parser/
[15]: https://forum.groupdocs.com/
[16]: https://blog.groupdocs.com/2021/08/25/extract-zip-files-data-in-csharp/
[17]: https://blog.groupdocs.com/2020/10/27/extract-images-from-pdf-word-excel-ppt-using-java/
[18]: https://blog.groupdocs.com/2021/03/15/extract-images-from-ebooks-in-java/


