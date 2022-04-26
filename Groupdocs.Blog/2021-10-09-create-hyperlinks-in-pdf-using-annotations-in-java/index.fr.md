---
title: "Créer des hyperliens en PDF à l'aide d'annotations en Java"
date: Sat, 09 Oct 2021 15:29:53 +0000
draft: false
url: /fr/2021/10/09/create-hyperlinks-in-pdf-using-annotations-in-java/
author: 'Shoaib Khan'
summary: 'Link annotations are used to create any part of the document as hyperlink. In other words, it allows us to associate external data with the specified area of the document. We can add these link annotations to documents within Java applications. In this article, you will learn **how to create hyperlinks in PDF files using Java**.

Les sujets suivants sont traités dans cet article :

* API Java pour ajouter des hyperliens dans les fichiers PDF
* Comment créer par programmation des hyperliens en PDF'
tags: ['annotate PDF', 'Annotate PDF in Java', 'Create Hyperlink in PDF', 'Link Annotation', 'Link Annotation in Java', 'Link Annotation in PDF']
categories: ['GroupDocs.Annotation Product Family']
---

Les annotations de lien sont utilisées pour créer n'importe quelle partie du document sous forme d'hyperliens. En d'autres termes, cela nous permet d'associer des données externes à la zone spécifiée du document. Nous pouvons ajouter ces annotations de lien aux documents dans les applications Java. Dans cet article, vous apprendrez **comment créer des hyperliens dans des fichiers PDF à l'aide de Java**.

Les sujets suivants sont traités ci-dessous :

* [API Java pour ajouter des hyperliens dans les fichiers PDF][1]
* [Comment créer par programmation des hyperliens dans un PDF][2]



{{< figure align=center src="images/add-link-annotation-in-pdf-using-groupdocs.jpg" alt="Créer un lien dans un PDF - par programmation">}}


## API Java pour créer des hyperliens en PDF {#hyperlink-java-api}

[GroupDocs.Annotation][3] fournit l'API Java qui permet la manipulation et l'automatisation de diverses annotations dans les documents au sein de vos applications Java. Nous utiliserons cette API pour créer une annotation de lien hypertexte dans le fichier PDF.

### Télécharger ou configurer

Téléchargez le fichier **JAR** à partir de la [section téléchargements][4], ou obtenez simplement les dernières configurations de référentiel et de dépendances pour le pox.xml de vos applications Java **basées sur maven**.

```
<repository>
	<id>GroupDocsJavaAPI</id>
	<name>GroupDocs Java API</name>
	<url>http://repository.groupdocs.com/repo/</url>
</repository>
<dependency>
        <groupId>com.groupdocs</groupId>
        <artifactId>groupdocs-annotation</artifactId>
        <version>21.7</version> 
</dependency>
```

## Créer des hyperliens en PDF en utilisant Java {#how-to-create-hyperlinks-annotations}

Voici les étapes pour créer des liens hypertexte n'importe où dans un PDF à l'aide de Java.

* Chargez le document PDF à l'aide de la classe [Annotator][5].
* Définir la liste des [Points][6] qui représentent la zone de l'hyperlien.
* Créez l'objet [LinkAnnotation][7].
* Définissez les propriétés du lien hypertexte comme l'URL, le numéro de page, les points, etc.
* Ajoutez le lien hypertexte défini au document PDF chargé à l'aide de la méthode [add][8].
* Enregistrez le PDF annoté en utilisant la méthode [save][9].

Le code Java suivant montre comment convertir n'importe quelle partie du fichier PDF en lien hypertexte par programmation.

```
// Créer des hyperliens en PDF à l'aide d'annotations de lien en Java
Annotator annotator = new Annotator("path/sample.pdf");
List<Point> points = new ArrayList<Point>();
points.add(new Point(120, 300));
points.add(new Point(600, 300));
points.add(new Point(120, 270));
points.add(new Point(600, 270));

LinkAnnotation link = new LinkAnnotation();
link.setCreatedOn(Calendar.getInstance().getTime());
link.setPageNumber(0);
link.setPoints(points);
link.setUrl("https://products.groupdocs.com/annotation");
annotator.add(link);

annotator.save("path/annotation-link.pdf");
annotator.dispose();
```

Voici la sortie du code ci-dessus.



{{< figure align=center src="images/link-annotation-in-pdf-using-groupdocs.jpg" alt="Créer un lien dans un PDF - par programmation">}}


## Obtenez une licence API gratuite

Vous pouvez [obtenir une licence temporaire gratuite][10] afin d'utiliser l'API sans les limitations d'évaluation.

## Conclusion

Pour résumer, nous avons expliqué comment ajouter par programmation des annotations de lien pour créer des hyperliens dans des fichiers PDF à l'aide de Java. En utilisant les annotations de lien, vous pouvez modifier n'importe quelle partie du document en hyperliens. De nombreux [différents types d'annotations][11] sont disponibles via l'API. Ces annotations peuvent être ajoutées de manière similaire en utilisant la même API. Pour en savoir plus sur l'API, consultez la [documentation][12]. Pour toute question, contactez-nous via le [forum][13].

## Voir également

* [Annotations de lien hypertexte dans PDF en utilisant C#][14]
* [Ajouter ou supprimer des annotations de fichiers PDF en Java][15]
* [Mise en surbrillance du PDF à l'aide des annotations en Java][16]
* [Ajouter un filigrane aux images en Java][17]







[1]: #hyperlink-java-api
[2]: #how-to-create-hyperlinks-annotations
[3]: https://products.groupdocs.com/annotation/java/
[4]: https://downloads.groupdocs.com/redaction
[5]: https://apireference.groupdocs.com/annotation/java/com.groupdocs.annotation/Annotator#Annotator(java.io.InputStream)
[6]: https://apireference.groupdocs.com/annotation/java/com.groupdocs.annotation.models/Point
[7]: https://apireference.groupdocs.com/annotation/java/com.groupdocs.annotation.models.annotationmodels/LinkAnnotation
[8]: https://apireference.groupdocs.com/annotation/java/com.groupdocs.annotation/Annotator#add(com.groupdocs.annotation.models.annotationmodels.AnnotationBase)
[9]: https://apireference.groupdocs.com/annotation/java/com.groupdocs.annotation/Annotator#save()
[10]: https://purchase.groupdocs.com/temporary-license
[11]: https://apireference.groupdocs.com/annotation/java/com.groupdocs.annotation.models.annotationmodels/package-frame
[12]: https://docs.groupdocs.com/redaction
[13]: https://forum.groupdocs.com/
[14]: https://blog.groupdocs.com/2021/10/16/create-hyperlinks-in-pdf-using-annotations-in-csharp/
[15]: https://blog.groupdocs.com/2021/04/18/annotate-pdf-files-using-java/
[16]: https://blog.groupdocs.com/2021/10/07/highlight-pdf-files-using-annotations-in-java/
[17]: https://blog.groupdocs.com/2020/09/15/add-watermark-to-images-in-java/


