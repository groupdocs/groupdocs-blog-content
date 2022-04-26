---
title: "Ajouter ou supprimer des annotations de fichiers PDF à l'aide de Java"
date: Sun, 18 Apr 2021 05:20:00 +0000
draft: false
url: /fr/2021/04/18/annoter-les-fichiers-pdf-en-utilisant-java/
author: 'Shoaib Khan'
summary: 'There was a time when we used to discuss document content and feedback in long email threads with multiple attachments and different file versions. Now we can simply use annotations to markup the document with messages and replies and send it. In this article, you will learn how to programmatically annotate PDF documents in Java with your application.

Voici les sujets abordés brièvement dans cet article :

* API Java pour travailler avec des annotations en PDF
* Ajouter des annotations au PDF en Java
    * Annotation de flèche au PDF
    * Annotation rectangulaire du PDF
    * Annotation Ellipse ou Ovale au format PDF
    * Annotation de distance au PDF
* Supprimer les annotations du PDF en Java

[Continuer la lecture...][1]'
tags: ['add annotations in PDF using Java', 'Annotate PDF in Java', 'Remove annotations from PDF in Java']
categories: ['GroupDocs.Annotation Product Family']
---

Il fut un temps où nous avions l'habitude de discuter du contenu des documents et des commentaires dans de longs fils de discussion avec plusieurs pièces jointes et différentes versions de fichiers. Maintenant, nous pouvons simplement utiliser des annotations pour baliser le document avec des messages et des réponses et l'envoyer. Dans cet article, vous apprendrez à annoter par programmation des documents PDF en Java avec votre application. De plus, nous verrons comment supprimer les annotations des fichiers PDF en utilisant la même API Java.

Voici les sujets abordés brièvement ci-dessous :

* [API Java pour travailler avec des annotations en PDF][2]
* [Ajouter des annotations au PDF en Java][3]
    * [Annotation fléchée dans le PDF][4]
    * [Annotation rectangulaire dans le PDF][5]
    * [Annotation Ellipse ou Ovale en PDF][6]
    * [Note de distance en PDF][7]
* [Supprimer les annotations du PDF en Java][8]

## API Java Annotateur PDF {#pdf-annotation-java-api}

Pour gérer les annotations de votre document et des images dans vos applications Java, GroupDocs fournit [GroupDocs.Annotation pour Java][9]. À l'aide de l'API, vous pouvez ajouter, supprimer et extraire des annotations de documents de **traitement de texte**, **feuilles de calcul**, **présentations**, **images**, **messages électroniques**, Visio * *dessins**, certains **AutoCAD** et **formats d'imagerie numérique** comme **DICOM**. De plus, l'API permet d'annoter des fichiers PDF. Vous pouvez consulter la documentation pour connaître la longue liste de [formats de document pris en charge pour l'annotation][10].

### Télécharger et configurer

[Obtenez la bibliothèque d'annotations][11]à partir des téléchargements ou ajoutez simplement la configuration pom.xml suivante dans vos applications Java basées sur Maven pour essayer les exemples de cet article ainsi que les nombreux autres exemples disponibles sur [GitHub][12]. Pour plus de détails, vous pouvez visiter la [API Reference][13].

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
        <artifactId>groupdocs-annotation</artifactId>
        <version>20.2</version> 
</dependency>
```

## Ajouter des annotations au PDF en Java {#add-annotations-to-pdf-in-java}

Passons rapidement à l'ajout de certains des différents types d'annotations au document PDF. Comme il existe de nombreux types d'annotations, nous ne couvrirons peut-être pas tout dans cet article. Je me contenterai de les mentionner, et vous pourrez [apprendre chaque annotation individuellement][14].

* Annotation Zone / Rectangle
* Flèche
* Distance
* Ellipse
* Souligner
* Lien
* Indiquer
* Polyligne

* Remplacement
* Rédaction des ressources
* Barré
* Champ de texte
* Rédaction de texte
* Souligner
* Filigrane

Commençons par en ajouter quelques-uns dans un document PDF.

## Ajouter une annotation de flèche au PDF en utilisant Java {#add-arrow-annotation-to-pdf-in-java}

Voici les étapes pour ajouter une annotation de flèche à un document PDF.



{{< figure align=center src="images/arrow-annotation.jpg" alt="Annotation de flèche">}}


* Chargez le document PDF en utilisant la classe [Annotator][15].
* Initialiser l'annotation fléchée à l'aide de la classe [ArrowAnnotation][16].
* Définissez la position et la taille de la flèche à l'aide de la méthode [setBox][17] d'ArrowAnnotation.
* Ajoutez l'annotation de flèche créée à l'objet Annotator.
* Enregistrez le PDF annoté en fournissant le chemin à l'aide de la méthode [save][18].

L'exemple de code suivant montre comment ajouter une annotation de flèche à un document PDF à l'aide de Java.

```
// Ajouter une annotation de flèche au PDF à l'aide de Java
final Annotator annotator = new Annotator("document.pdf");
ArrowAnnotation arrow = new ArrowAnnotation();
arrow.setBox(new Rectangle(100, 100, 100, 100)); // (x, y, width, height)
annotator.add(arrow);
annotator.save("path/annotated-with-arrow.pdf");
```

## Insérer un rectangle ou une annotation de zone dans un PDF à l'aide de Java {#rectangle-area-annotation-to-pdf-in-java}

Vous pouvez personnaliser n'importe quelle annotation tout en l'ajoutant au document. Voici les étapes pour ajouter un rectangle ou une annotation de zone à un document PDF avec un peu plus de personnalisations. Cela revient à ajouter une annotation Arrow mais utilise la classe **AreaAnnotation** à la place de **ArrowAnnotation**.

* Chargez le document PDF à l'aide de la classe [Annotator][19].
* Initialiser l'annotation du rectangle à l'aide de la classe [AreaAnnotation][20].
* Définissez la position et la taille du rectangle à l'aide de la méthode [setBox][21] de AreaAnnotation.
* Définissez d'autres propriétés telles que **color**, **background**, **opacity**, **style**, **pen width** ou même **messages** et **time** .
* Ajoutez l'annotation rectangulaire créée à l'objet Annotator.
* Enregistrez le PDF annoté en fournissant le chemin à l'aide de la méthode [save][22].



{{< figure align=center src="images/rectangle-area-annotation.jpg" alt="Annotation de rectangle ou de zone">}}


L'exemple de code suivant montre comment ajouter une annotation de rectangle/zone à un document PDF à l'aide de Java.

```
// Ajouter une annotation de zone ou une annotation de rectangle au PDF à l'aide de Java
final Annotator annotator = new Annotator("document.pdf");
AreaAnnotation area = new AreaAnnotation();
area.setBox(new Rectangle(50, 100, 500, 100));
area.setCreatedOn(Calendar.getInstance().getTime());
area.setMessage("Annotate documents and images.");
area.setOpacity(0.7);
area.setPenColor(-13076963);
area.setPenStyle(PenStyle.Dash);
area.setPenWidth((byte) 3);
// ajouter au document
annotator.add(area);
annotator.save("path/annotated-with-rectangle.pdf");
```

## Ajouter une annotation ovale ou ellipse au PDF à l'aide de Java {#oval-ellipse-annotation-to-pdf-in-java}

Voici les étapes pour ajouter une annotation ovale ou une annotation ellipse à un document PDF.



{{< figure align=center src="images/ellipses-annotation.jpg" alt="Ellipses ou annotation ovale">}}


* Chargez le document PDF en utilisant la classe [Annotator][23].
* Initialiser l'annotation d'ellipse à l'aide de la classe [EllipseAnnotation][24].
* Définissez la position et la taille de l'ellipse à l'aide de la méthode [setBox][25] d'EllipseAnnotation.
* Ajoutez l'annotation d'ellipse créée à l'objet Annotator.
* Enregistrez le PDF annoté en fournissant le chemin à l'aide de la méthode [save][26].

L'exemple de code suivant montre comment ajouter une annotation ovale ou elliptique à un document PDF à l'aide de Java.

```
// Ajouter une annotation ovale ou ellipse dans un PDF à l'aide de Java
final Annotator annotator = new Annotator("document.pdf");
// Annotation ovale ou elliptique
EllipseAnnotation ellipse = new EllipseAnnotation();
ellipse.setBox(new Rectangle(275, 505, 300, 80));
// ajouter au document
annotator.add(area);
annotator.save("path/annotated-with-ellipse.pdf");
```

## Insérer une annotation de distance dans un PDF à l'aide de Java {#distance-annotation-to-pdf-in-java}



{{< figure align=center src="images/distance-annotation.jpg" alt="Annotation des distances">}}


Vous pouvez également ajouter l'annotation de distance pour afficher la distance entre deux points. Voici les étapes pour ajouter une annotation de distance au document PDF.

* Chargez le document PDF en utilisant la classe [Annotator][27].
* Initialiser l'annotation de distance à l'aide de la classe [DistanceAnnotation][28].
* Définissez la taille et la position de l'annotation à l'aide de la méthode [setBox][29] de DistanceAnnotation.
* Ajoutez l'annotation de distance créée à l'objet Annotator.
* Enregistrez le PDF annoté en fournissant le chemin à l'aide de la méthode [save][30].

L'exemple de code suivant montre comment ajouter une annotation de distance à un document PDF à l'aide de Java.

```
// Annotation de distance à l'aide de Java
final Annotator annotator = new Annotator("document.pdf");
// Annotation des distances
DistanceAnnotation distance = new DistanceAnnotation();
distance.setBox(new Rectangle(775, 235, 0, 150));
// ajouter au document
annotator.add(area);
annotator.save("path/annotated-with-distance.pdf");
```

## Code complet

Pour résumer, voici le code Java avec la sortie montrant toutes les **annotations** et **messages** ajoutés avec des **réponses** utilisant le code Java mentionné.



{{< figure align=center src="images/added-annotations-to-pdf.jpg" alt="Ajout d'annotations au PDF">}}


Le code suivant ci-dessous ajoute une flèche, un rectangle, une ellipse, des annotations de distance, des messages et des réponses à un fichier PDF.

```
// Ajouter plusieurs annotations au PDF à l'aide de Java
// Ajout d'annotations de flèche, de zone, d'ovale (ellipse) et de distance au PDF avec des messages et des réponses à l'aide de Java
final Annotator annotator = new Annotator(Constants.INPUT);
// Définition des réponses
Reply reply1 = new Reply();
reply1.setComment("Please look in to these issues.");
reply1.setRepliedOn(Calendar.getInstance().getTime());

Reply reply2 = new Reply();
reply2.setComment("Change Description");
reply2.setRepliedOn(Calendar.getInstance().getTime());

Reply reply3 = new Reply();
reply2.setComment("On-Premises APIs");
reply2.setRepliedOn(Calendar.getInstance().getTime());

Reply reply4 = new Reply();
reply2.setComment("Add images as well.");
reply2.setRepliedOn(Calendar.getInstance().getTime());

java.util.List<Reply> replies = new ArrayList<Reply>();
replies.add(reply1);
replies.add(reply2);
replies.add(reply3);
replies.add(reply4);
// Annotation de flèche ================================
ArrowAnnotation arrow = new ArrowAnnotation();
arrow.setBox(new Rectangle(560, 250, 60, -60));
arrow.setCreatedOn(Calendar.getInstance().getTime());
arrow.setMessage("This image is little upwards.");
arrow.setOpacity(0.7);
arrow.setPenColor(-3407872);
arrow.setPenWidth((byte) 2);
arrow.setReplies(replies.subList(0, 1));
// Annotation de zone ==================================
AreaAnnotation area = new AreaAnnotation();
area.setBox(new Rectangle(50, 100, 500, 100));
area.setCreatedOn(Calendar.getInstance().getTime());
area.setMessage("Annotate documents and images.");
area.setOpacity(0.7);
area.setPenColor(-13076963);
area.setPenStyle(PenStyle.Dash);
area.setPenWidth((byte) 3);
area.setReplies(replies.subList(1, 2));
// Annotation ovale ou elliptique ========================
EllipseAnnotation ellipse = new EllipseAnnotation();
ellipse.setBox(new Rectangle(275, 505, 300, 80));
ellipse.setCreatedOn(Calendar.getInstance().getTime());
ellipse.setMessage("Shows all the available Annotation APIs.");
ellipse.setOpacity(0.7);
ellipse.setPenColor(-16034924);
ellipse.setPenStyle(PenStyle.Dot);
ellipse.setPenWidth((byte) 3);
ellipse.setReplies(replies.subList(2, 3));
// Annotation des distances ==============================
DistanceAnnotation distance = new DistanceAnnotation();
distance.setBox(new Rectangle(775, 235, 0, 150));
distance.setCreatedOn(Calendar.getInstance().getTime());
distance.setMessage("This is the heading area");
distance.setOpacity(0.7);
distance.setPenColor(-21197);
distance.setPenStyle(PenStyle.Solid);
distance.setPenWidth((byte) 1);
distance.setReplies(replies.subList(3, 4));
// Ajout d'annotations =================================
annotator.add(arrow);
annotator.add(area);
annotator.add(ellipse);
annotator.add(distance);
// Enregistrement du PDF annoté ===============================
annotator.save(outputPath);
annotator.dispose();
```

## Supprimer les annotations du PDF en Java {#remove-annotations-from-pdf-in-java}

Les étapes suivantes montrent comment supprimer toutes les annotations des fichiers PDF en Java.

* Chargez le document PDF en utilisant la classe [Annotator][31].
* Initialiser la sauvegarde des options à l'aide de la classe [SaveOptions][32].
* Définissez les types d'annotations sur Aucun.
* Enregistrez le fichier PDF en supprimant toutes les annotations, en fournissant le chemin à l'aide de la méthode [save][33].

Le code Java suivant supprime les annotations d'un fichier PDF.

```
// Supprimez toutes les annotations du document PDF à l'aide de Java
final Annotator annotator = new Annotator("document.pdf");
SaveOptions saveOptions = new SaveOptions();
saveOptions.setAnnotationTypes(AnnotationType.None);
// Enregistrez le PDF sans plus d'annotations.
annotator.save("path/annotations-removed.pdf", saveOptions);
annotator.dispose();
```

## Conclusion

En bref, vous avez appris à ajouter des annotations au PDF dans les applications Java. De plus, vous avez vu comment supprimer toutes les annotations de n'importe quel fichier PDF. Maintenant, vous devriez être sûr de créer votre propre application Java d'annotation de documents. Il peut prendre en charge différents types d'annotations à l'aide de GroupDocs.Annotation pour Java.

Pour plus de détails, d'options et d'exemples, vous pouvez visiter la [documentation][34] et le référentiel [GitHub][35]. Pour toute autre question, contactez le support sur le [forum][36].

## Voir également

* [Ajouter un filigrane aux images en Java][37]







[1]: https://blog.groupdocs.com/2021/04/18/annotate-pdf-files-using-java/
[2]: #pdf-annotation-java-api
[3]: #add-annotations-to-pdf-in-java
[4]: #add-arrow-annotation-to-pdf-in-java
[5]: #rectangle-area-annotation-to-pdf-in-java
[6]: #oval-ellipse-annotation-to-pdf-in-java
[7]: #distance-annotation-to-pdf-in-java
[8]: #remove-annotations-from-pdf-in-java
[9]: https://products.groupdocs.com/annotation/java
[10]: https://docs.groupdocs.com/annotation/java/supported-document-formats/
[11]: https://downloads.groupdocs.com/annotation/java
[12]: https://github.com/groupdocs-annotation
[13]: https://apireference.groupdocs.com/annotation/java
[14]: https://docs.groupdocs.com/annotation/java/add-annotation-to-the-document/
[15]: https://apireference.groupdocs.com/annotation/java/com.groupdocs.annotation/Annotator
[16]: https://apireference.groupdocs.com/annotation/java/com.groupdocs.annotation.models.annotationmodels/ArrowAnnotation
[17]: https://apireference.groupdocs.com/annotation/java/com.groupdocs.annotation.models.annotationmodels/ArrowAnnotation#setBox(com.groupdocs.annotation.models.Rectangle)
[18]: https://apireference.groupdocs.com/annotation/java/com.groupdocs.annotation/Annotator#save(java.lang.String)
[19]: https://apireference.groupdocs.com/annotation/java/com.groupdocs.annotation/Annotator
[20]: https://apireference.groupdocs.com/annotation/java/com.groupdocs.annotation.models.annotationmodels/AreaAnnotation
[21]: https://apireference.groupdocs.com/annotation/java/com.groupdocs.annotation.models.annotationmodels/ArrowAnnotation#setBox(com.groupdocs.annotation.models.Rectangle)
[22]: https://apireference.groupdocs.com/annotation/java/com.groupdocs.annotation/Annotator#save(java.lang.String)
[23]: https://apireference.groupdocs.com/annotation/java/com.groupdocs.annotation/Annotator
[24]: https://apireference.groupdocs.com/annotation/java/com.groupdocs.annotation.models.annotationmodels/EllipseAnnotation
[25]: https://apireference.groupdocs.com/annotation/java/com.groupdocs.annotation.models.annotationmodels/ArrowAnnotation#setBox(com.groupdocs.annotation.models.Rectangle)
[26]: https://apireference.groupdocs.com/annotation/java/com.groupdocs.annotation/Annotator#save(java.lang.String)
[27]: https://apireference.groupdocs.com/annotation/java/com.groupdocs.annotation/Annotator
[28]: https://apireference.groupdocs.com/annotation/java/com.groupdocs.annotation.models.annotationmodels/DistanceAnnotation
[29]: https://apireference.groupdocs.com/annotation/java/com.groupdocs.annotation.models.annotationmodels/ArrowAnnotation#setBox(com.groupdocs.annotation.models.Rectangle)
[30]: https://apireference.groupdocs.com/annotation/java/com.groupdocs.annotation/Annotator#save(java.lang.String)
[31]: https://apireference.groupdocs.com/annotation/java/com.groupdocs.annotation/Annotator
[32]: https://apireference.groupdocs.com/annotation/java/com.groupdocs.annotation.options.export/SaveOptions
[33]: https://apireference.groupdocs.com/annotation/java/com.groupdocs.annotation/Annotator#save(java.lang.String)
[34]: https://docs.groupdocs.com/annotation/java/
[35]: https://github.com/groupdocs-annotation
[36]: https://forum.groupdocs.com/
[37]: https://blog.groupdocs.com/2020/09/15/add-watermark-to-images-in-java/


