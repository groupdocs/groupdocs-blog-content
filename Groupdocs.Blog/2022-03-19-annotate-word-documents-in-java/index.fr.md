---
title: "Ajouter ou supprimer des annotations ou des fichiers Word de balisage en Java"
date: Sat, 19 Mar 2022 15:42:43 +0000
draft: false
url: /fr/2022/03/19/annoter-les-documents-word-en-java/
author: 'Shoaib Khan'
summary: "Les annotations sont normalement utilisées pour mentionner des erreurs dans les documents ou pour discuter de leur contenu. Avec les annotations, vous pouvez éviter les discussions longues et interminables dans les fils de discussion. Dans cet article, vous apprendrez à ajouter et à supprimer par programme des annotations pour baliser des documents Word en Java."
tags: ['Add Annotations in Java', 'Add Annotations in Word using Java', 'Annotate Word in Java', 'Annotations in Java', 'Remove Annotation from Word in Java']
categories: ['GroupDocs.Annotation Product Family']
---

Les annotations sont normalement utilisées pour mentionner des erreurs dans les documents ou pour discuter de leur contenu. Avec les annotations, vous pouvez éviter les discussions longues et interminables dans les fils de discussion. Dans cet article, vous apprendrez à ajouter et à supprimer par programme des annotations pour baliser des documents Word en Java.

Voici les sujets abordés brièvement ci-dessous :

* [API Java pour les annotations Word DOC/DOCX](#java-annotation-api)
* [Ajouter des annotations à Word](#add-annotations-to-word)
    * [Annotations fléchées](#add-arrow-annotation)
    * [Annotations rectangulaires](#add-area-annotation)
    * [Annotations Ellipse ou Ovale](#add-ellipse-annotation)
    * [Annotations de distance](#add-distance-annotation)
* [Supprimer les annotations des fichiers Word](#remove-annotations)

## API Java pour annoter et baliser des fichiers Word {#dotnet-annotation-api}

[GroupDocs.Annotation](https://products.groupdocs.com/annotation/) fournit l'API Java pour gérer les annotations. L'API permet l'ajout, la suppression et l'extraction d'annotations à partir de documents Word et de nombreux autres formats de fichiers. [Formats de document pris en charge](https://docs.groupdocs.com/annotation/java/supported-document-formats/) incluent ; feuilles de calcul, présentations, images, fichiers PDF, pages Web, messages électroniques, dessins Visio.

### Télécharger ou configurer

Téléchargez le fichier **JAR** à partir de la [section des téléchargements](https://downloads.groupdocs.com/annotation), ou obtenez simplement les dernières configurations de référentiel et de dépendance pour le pox.xml de votre **basé sur maven* * Applications Java.

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

## Ajouter des annotations à Word en Java {#add-annotations-to-word}

Ajoutons différents types d'annotations aux documents Word. Les annotations sont de plusieurs types, nous n'en couvrirons donc que quelques-unes ici.

{{< figure align=center src="images/add-annotations-to-doc-docx-using-groupdocs-dotnet-java-api-1024x624.png" alt="Ajouter des annotations à DOC DOCX à l'aide de l'API GroupDocs">}}


## Ajouter une annotation de flèche à Word en Java {#add-arrow-annotation}

Voici les étapes pour ajouter une annotation de flèche à un document Word en Java.

* Chargez le document à l'aide de la classe [Annotator](https://apireference.groupdocs.com/annotation/java/com.groupdocs.annotation/Annotator).
* Initialiser l'annotation de flèche avec la classe [ArrowAnnotation](https://apireference.groupdocs.com/annotation/java/com.groupdocs.annotation.models.annotationmodels/ArrowAnnotation).
* Ajustez la position, la taille, le numéro de page de l'annotation de la flèche.
* Ajoutez l'annotation de flèche créée à l'aide de la méthode add().
* Enregistrez le document Word annoté dans le chemin en utilisant la méthode save() appropriée.

L'exemple de code Java suivant montre comment ajouter une annotation de flèche à un document Word.

```
// Ajouter une annotation de flèche aux documents Word en Java
final Annotator annotator = new Annotator("path/document.docx");
ArrowAnnotation arrow = new ArrowAnnotation();
arrow.setBox(new Rectangle(100, 100, 100, 100));
arrow.setMessage("Arrow annotation");
arrow.setOpacity(0.7);
arrow.setPageNumber(0);
arrow.setPenColor(0x65535);
arrow.setPenStyle(PenStyle.Dot);
arrow.setPenWidth((byte) 3);
annotator.add(arrow);
annotator.save("path/annotatedDoc.docx");
```

{{< figure align=center src="images/arrow-annotation.jpg" alt="Ajouter une annotation de flèche par programmation dans Java et .NET">}}

## Insérer un rectangle ou une annotation de zone dans Word en Java {#add-area-annotation}

Voici les étapes pour ajouter une annotation de rectangle ou de zone à un document DOC/DOCX avec quelques personnalisations. C'est similaire à l'ajout d'annotations Flèche mais il utilise **AreaAnnotation**.

* Chargez le document Word DOC/DOCX à l'aide de la classe [Annotator](https://apireference.groupdocs.com/annotation/java/com.groupdocs.annotation/Annotator).
* Initialiser l'annotation rectangle à l'aide de la classe [AreaAnnotation](https://apireference.groupdocs.com/annotation/java/com.groupdocs.annotation.models.annotationmodels/AreaAnnotation).
* Ajustez la position, la taille et la couleur du rectangle.
* Définissez d'autres propriétés telles que **numéro de page, arrière-plan, opacité, style, largeur du stylo**, **messages** et **heure**.
* Ajoutez l'annotation rectangulaire créée à l'annotateur.
* Enregistrez le document Word annoté dans le chemin en utilisant la méthode save().


L'exemple de code Java suivant montre comment ajouter une annotation rectangle/zone à un document Word.

```
// Ajouter une annotation de zone ou de rectangle dans les documents Word en Java

final Annotator annotator = new Annotator("path/document.docx");

AreaAnnotation area = new AreaAnnotation();
area.setBackgroundColor(65535);
area.setBox(new Rectangle(100, 100, 100, 100));
area.setCreatedOn(Calendar.getInstance().getTime());
area.setMessage("This is area annotation");
area.setOpacity(0.7);
area.setPageNumber(0);
area.setPenColor(65535);
area.setPenStyle(PenStyle.Dot);
area.setPenWidth((byte) 3);
area.setReplies(replies);
annotator.add(area);
annotator.save("path/annotatedDoc.docx");
```

{{< figure align=center src="images/rectangle-area-annotation.jpg" alt="Ajouter un rectangle ou une annotation de zone par programmation dans .NET et Java">}}

## Ajouter une annotation ovale ou ellipse à Word en Java {#add-ellipse-annotation}

Voici les étapes pour ajouter une annotation ovale/ellipse à un document en Java.

* Chargez le document DOC/DOCX à l'aide de la classe [Annotator](https://apireference.groupdocs.com/annotation/java/com.groupdocs.annotation/Annotator).
* Initialiser l'annotation d'ellipse à l'aide de la classe [EllipseAnnotation](https://apireference.groupdocs.com/annotation/java/com.groupdocs.annotation.models.annotationmodels/EllipseAnnotation).
* Définissez la position et la taille de l'annotation d'ellipse initialisée.
* Ajoutez l'annotation d'ellipse créée à l'annotateur.
* Enregistrez le fichier Word annoté en utilisant la méthode save() appropriée.

L'exemple de code Java suivant montre comment ajouter une annotation ovale/ellipse à n'importe quel document Word.

```
// Ajouter une annotation ovale ou ellipse dans des documents Word en Java
final Annotator annotator = new Annotator("path/document.docx");

EllipseAnnotation ellipse = new EllipseAnnotation();
ellipse.setBackgroundColor(65535);
ellipse.setBox(new Rectangle(100, 100, 100, 100));
ellipse.setCreatedOn(Calendar.getInstance().getTime());
ellipse.setMessage("This is ellipse annotation");
ellipse.setOpacity(0.7);
ellipse.setPageNumber(0);
ellipse.setPenColor(65535);
ellipse.setPenStyle(PenStyle.Dot);
ellipse.setPenWidth((byte) 3);
ellipse.setReplies(replies);
annotator.add(ellipse);
annotator.save("path/annotatedDoc.docx");
```

{{< figure align=center src="images/ellipses-annotation.jpg" alt="Ajouter des ellipses ou des annotations ovales par programmation dans C# .NET et Java">}}

## Insérer une annotation de distance dans Word en Java {#add-distance-annotation}

De même, vous pouvez mentionner la distance entre deux points en utilisant l'annotation de distance. Voici les étapes pour ajouter une annotation de distance au document en Java.

* Après avoir chargé le document Word, initialisez l'annotation de distance à l'aide de la classe [DistanceAnnotation](https://apireference.groupdocs.com/annotation/java/com.groupdocs.annotation.models.annotationmodels/DistanceAnnotation).
* Définissez l'apparence de l'annotation.
* Ajoutez l'annotation de distance à l'objet Annotator.
* Enregistrez le document annoté à l'emplacement indiqué ou utilisez la bonne méthode save(),

L'exemple de code Java suivant montre comment ajouter une annotation de distance à un document DOC/DOCX.

```
// Ajouter une annotation de distance aux documents Word en Java
final Annotator annotator = new Annotator("path/document.docx");

DistanceAnnotation distance = new DistanceAnnotation();
distance.setBox(new Rectangle(200, 150, 200, 30));
distance.setCreatedOn(Calendar.getInstance().getTime());
distance.setMessage("This is distance annotation");
distance.setOpacity(0.7);
distance.setPageNumber(0);
distance.setPenColor(65535);
distance.setPenStyle(PenStyle.Dot);
distance.setPenWidth((byte) 3);
distance.setReplies(replies);
annotator.add(distance);
annotator.save("path/annotatedDoc.docx");
```

{{< figure align=center src="images/distance-annotation.jpg" alt="Ajouter une annotation de distance par programmation dans C# .NET et Java">}}

## Supprimer les annotations des fichiers Word DOC/DOCX en Java {#remove-annotations}

Il existe de nombreuses façons de supprimer les annotations des documents Word. Vous pouvez supprimer des annotations spécifiques en fournissant les index pour supprimer les annotations spécifiques. De plus, vous pouvez supprimer toutes les annotations à la fois. Les détails et le code source Java pour la suppression des annotations sont traités dans un article séparé.

Voici les étapes pour supprimer toutes les annotations d'un fichier Word.

* Charger le document.
* Initialiser [options d'enregistrement](https://apireference.groupdocs.com/annotation/java/com.groupdocs.annotation.options.export/SaveOptions).
* Définissez le [type d'annotation](https://apireference.groupdocs.com/annotation/java/com.groupdocs.annotation.options.export/AnnotationType) sur Aucun.
* Enregistrez le fichier Word. Il sera exempt d'annotations.

Le code suivant montre comment supprimer des annotations d'un fichier Word en Java.

```
// Supprimer toutes les annotations du document Word en Java
final Annotator annotator = new Annotator("path/annotatedDoc.docx");

SaveOptions saveOptions = new SaveOptions();
saveOptions.setAnnotationTypes(AnnotationType.None);
annotator.save("path/annotationsRemoved.docx", saveOptions);
```

## Conclusion

En résumé, vous avez appris à ajouter des annotations aux documents Word dans les applications Java. Plus précisément, nous avons ajouté des annotations de flèche, d'ellipse, de zone et de distance au fichier Word DOC/DOCX à l'aide de [GroupDocs.Annotation pour Java](https://products.groupdocs.com/annotation/java/). De plus, vous avez également vu comment supprimer toutes les annotations de n'importe quel fichier Word. Maintenant, vous pouvez essayer de créer votre propre application Java d'annotation de documents.

Pour en savoir plus sur l'API, consultez la [documentation](https://docs.groupdocs.com/annotation/java/) et le référentiel [GitHub](https://github.com/groupdocs-annotation). Pour toute autre question, contactez le support sur le [forum](https://forum.groupdocs.com/).

## Voir également

* [Annoter des fichiers PDF en Java](https://blog.groupdocs.com/2021/04/18/annotate-pdf-files-using-java/)
* [Render Word documents as Minified HTML in Java](https://blog.groupdocs.com/2022/03/04/render-word-documents-as-minified-html-in-java/)
* [Supprimer les annotations des documents PDF ou Word en Java](https://blog.groupdocs.com/2022/03/12/remove-annotations-from-pdf-or-word-documents-in-java/)





