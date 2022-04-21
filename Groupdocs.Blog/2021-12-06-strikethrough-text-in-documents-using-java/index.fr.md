---
title: "Texte barré dans les documents utilisant Java"
date: Mon, 06 Dec 2021 07:19:00 +0000
draft: false
url: /fr/2021/12/06/texte-barré-dans-les-documents-en-utilisant-java/
author: 'Shoaib Khan'
summary: "Vous avez probablement du contenu qui n'est plus valide. Biffons-le. Le barrage est l'un des moyens utilisés pour mettre en évidence le contenu non valide dans les documents. Afin d'automatiser le barrage au sein des applications, cet article montre comment barrer du texte dans des documents en Java."
tags: ['Cross out Text', 'Cross out Text in Java', 'Strike through Text in Java', 'Strikeout Text', 'Strikethrough Text']
categories: ['GroupDocs.Annotation Product Family']
---



{{< figure align=center src="images/strikethrough-text-using-java.jpg" alt="Texte barré à l'aide de Java">}}


Vous avez probablement du contenu qui n'est plus valide. Biffons-le. Le barrage est l'un des moyens utilisés pour mettre en évidence le contenu non valide dans les documents. Afin d'automatiser le barrage dans les applications, cet article montre **comment barrer du texte dans des documents en Java**.

Les sujets suivants sont abordés dans cet article.

* [API Java pour les annotations barrées][1]
* [Comment barrer du texte dans des documents][2]

## API Java pour texte barré {#strikethrough-text-java-api}

[GroupDocs.Annotation][3] présente l'API Java qui prend en charge diverses annotations pouvant être appliquées à plusieurs documents et images. Nous l'utiliserons dans les exemples de cet article pour rayer le texte sélectionné dans les documents.

Vous pouvez télécharger le fichier **JAR** à partir de la [section des téléchargements][4] ou utiliser les dernières configurations de référentiel et de dépendance [Maven][5] dans vos applications Java.

```
<repository>
	<id>GroupDocsJavaAPI</id>
	<name>GroupDocs Java API</name>
	<url>http://repository.groupdocs.com/repo/</url>
</repository>
<dependency>
        <groupId>com.groupdocs</groupId>
        <artifactId>groupdocs-annotation</artifactId>
        <version>21.7.2</version> 
</dependency>
```

## Comment barrer du texte dans des documents à l'aide de Java {#how-to-strikethrough-text-using-java}

Biffons la partie du document qui n'est plus valide. Les étapes suivantes vous permettent de barrer le texte dans les documents en Java.

* Chargez le document source (PDF, Word, etc.) à l'aide de la classe [Annotator][6].
* Créez et définissez l'annotation barrée à l'aide de la classe [StrikeoutAnnotation][7].
    * Définissez la couleur de la ligne pour le barré.
    * Définir l'opacité, le numéro de page du document.
    * Définissez les coordonnées et d'autres propriétés.
* Ajoutez l'annotation barrée préparée à l'annotateur à l'aide de la méthode [add()][8].
* Enfin, enregistrez le document annoté en utilisant la méthode [save()][9].

De même, vous pouvez annoter des documents Word, des feuilles de calcul, des présentations, des documents PDF, des pages Web, des messages électroniques et de nombreux autres documents.

L'exemple de code Java suivant barre le texte sélectionné dans un document PDF.

```
/*
 * Strikethrough Text in Word, PDF, Spreadsheets, Presentations using Java
 */
Annotator annotator = new Annotator("path/document.pdf");
StrikeoutAnnotation strikeout = new StrikeoutAnnotation();
strikeout.setFontColor(0xFF0000);
strikeout.setOpacity(0.7);
strikeout.setPageNumber(0);

// Ajouter des points pour le retrait
List<Point> points = new ArrayList<Point>();
points.add(new Point(180, 730));
points.add(new Point(300, 730));
points.add(new Point(180, 700));
points.add(new Point(300, 700));
strikeout.setPoints(points);

annotator.add(strikeout);
annotator.save("path/strikethrough-text.pdf");
```

## Obtenez une licence API gratuite

Vous pouvez utiliser [GroupDocs.Annotation for Java][10] gratuitement en [obtenant une licence temporaire][11].

## Conclusion

Pour conclure, nous avons discuté de l'ajout par programmation de l'annotation barrée aux documents dans les applications Java. De plus, vous pouvez barrer le texte dans les fichiers PDF, les feuilles de calcul, les présentations et les documents Word. De même, vous pouvez également utiliser d'autres annotations à votre guise.

En savoir plus sur **GroupDocs.Annotation pour Java** dans sa [documentation][12]. Essayez de créer votre propre annotateur pour les [formats de document pris en charge][13]. N'hésitez pas à nous contacter pour toute question via le [forum][14].

## Voir également

* [Ajouter ou supprimer des annotations à partir de fichiers PDF à l'aide de Java][15]
* [Mettre en surbrillance le contenu PDF en Java][16]
* [Texte barré dans les documents utilisant C#][17]

[1]: #strikethrough-text-java-api
[2]: #how-to-strikethrough-text-using-java
[3]: https://products.groupdocs.com/annotation/
[4]: https://downloads.groupdocs.com/viewer
[5]: https://repository.groupdocs.com/webapp/#/artifacts/browse/tree/General/repo/com/groupdocs
[6]: https://apireference.groupdocs.com/annotation/java/com.groupdocs.annotation/Annotator
[7]: https://apireference.groupdocs.com/annotation/java/com.groupdocs.annotation.models.annotationmodels/StrikeoutAnnotation
[8]: https://apireference.groupdocs.com/annotation/java/com.groupdocs.annotation/Annotator#add(com.groupdocs.annotation.models.annotationmodels.AnnotationBase)
[9]: https://apireference.groupdocs.com/annotation/java/com.groupdocs.annotation/Annotator#save()
[10]: https://products.groupdocs.com/annotation/java/
[11]: https://purchase.groupdocs.com/temporary-license
[12]: https://docs.groupdocs.com/annotation/java/
[13]: https://docs.groupdocs.com/annotation/java/supported-document-formats/
[14]: https://forum.groupdocs.com/
[15]: https://blog.groupdocs.com/2021/04/18/annotate-pdf-files-using-java/
[16]: https://blog.groupdocs.com/2021/10/07/highlight-pdf-using-annotations-in-java/
[17]: https://blog.groupdocs.com/2021/12/18/strikethrough-text-in-documents-using-csharp/


