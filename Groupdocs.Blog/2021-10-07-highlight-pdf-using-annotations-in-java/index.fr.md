---
title: "Mettre en surbrillance un PDF à l'aide d'annotations en Java"
date: Thu, 07 Oct 2021 10:35:00 +0000
draft: false
url: /fr/2021/10/07/highlight-pdf-using-annotations-in-java/
aliases:
- /2021/10/07/highlight-pdf-files-using-annotations-in-java/
author: 'Shoaib Khan'
summary: "Il est souvent nécessaire de mettre en évidence des zones importantes de vos documents à dessein. En tant que développeur, vous pouvez automatiser la mise en surbrillance dans vos applications. Dans cet article, vous apprendrez **comment mettre en surbrillance du texte et n'importe quelle zone dans des fichiers PDF à l'aide de Java**. De plus, il y aura plusieurs propriétés de mise en surbrillance qui peuvent être ajustées en fonction des besoins."
tags: ['annotate PDF', 'Annotate PDF in Java', 'Highlight Annotation', 'Highlight PDF in Java', 'Highlight Text in PDF', 'Text Highlight']
categories: ['GroupDocs.Annotation Product Family']
---

Il est souvent nécessaire de mettre en évidence des zones importantes de vos documents à dessein. En tant que développeur, vous pouvez automatiser la mise en surbrillance dans vos applications. Dans cet article, vous apprendrez **comment mettre en surbrillance du texte et n'importe quelle zone dans des fichiers PDF à l'aide de Java**. De plus, il y aura plusieurs propriétés de mise en surbrillance qui peuvent être ajustées en fonction des besoins.

Les sujets suivants sont traités ci-dessous :

* [API Java pour surligner en PDF][1]
* [Comment mettre en surbrillance par programme dans PDF][2]



{{< figure align=center src="images/add-highlight-annotation-in-pdf-using-groupdocs.jpg" alt="Mettre en surbrillance du texte dans un PDF - par programme">}}


## API Java pour surligner en PDF {#highlight-pdf-java-api}

[GroupDocs.Annotation for Java][3] est l'API qui permet une manipulation et une automatisation faciles des annotations dans les documents au sein de vos applications Java. Nous utiliserons cette API pour surligner du texte dans le fichier PDF.

### Télécharger ou configurer

Vous pouvez télécharger le fichier **JAR** à partir de la [section téléchargements][4], ou simplement obtenir les dernières configurations de référentiel et de dépendance pour le pox.xml de vos applications Java **basées sur maven**.

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

## Mettre en surbrillance dans PDF en utilisant Java {#how-to-highlight-pdf}

Voici les étapes pour mettre en surbrillance du texte ou n'importe quelle zone d'un PDF à l'aide de Java.

* Chargez le document PDF à l'aide de la classe [Annotator][5].
* Définissez une liste de [Point][6]s pour sélectionner la zone de surbrillance.
* Créez l'objet [HighlightAnnotation][7].
* Définissez les propriétés de surbrillance telles que la couleur, l'opacité et le numéro de page.
* Ajoutez la surbrillance définie au document PDF chargé à l'aide de la méthode [add][8].
* Enregistrez le PDF annoté en utilisant la méthode [save][9].

**Remarque :** Vous pouvez modifier la couleur de surbrillance, l'opacité et d'autres propriétés.

Le code Java suivant montre comment mettre en surbrillance le texte d'un PDF par programme.

```
// Mettre en surbrillance le PDF à l'aide de l'annotation de surbrillance en Java
Annotator annotator = new Annotator("path/sample.pdf");
List<Point> points = new ArrayList<Point>();
points.add(new Point(120, 270));
points.add(new Point(600, 270));
points.add(new Point(120, 300));
points.add(new Point(600, 300));

HighlightAnnotation highlight = new HighlightAnnotation();
highlight.setBackgroundColor(0xFFF000);
highlight.setOpacity(0.5);
highlight.setPageNumber(0);
highlight.setPoints(points);
annotator.add(highlight);

annotator.save("path/annotation-highlight.pdf");
annotator.dispose();
```

Voici la sortie du code ci-dessus.



{{< figure align=center src="images/highlight-annotation-in-pdf-using-groupdocs.jpg" alt="Mettre en surbrillance du texte dans un PDF - par programme">}}


## Obtenez une licence API gratuite

Vous pouvez [obtenir une licence temporaire gratuite][10] afin d'utiliser l'API sans les limitations d'évaluation.

## Conclusion

Pour conclure, nous avons expliqué comment ajouter par programmation des annotations de surbrillance dans les fichiers PDF à l'aide de Java. De plus, nous pouvons facilement modifier la couleur de surbrillance, l'opacité et d'autres propriétés. De nombreux [différents types d'annotations][11] sont disponibles via l'API. Ces annotations peuvent être ajoutées de manière similaire en utilisant la même API. Pour en savoir plus sur l'API, consultez la [documentation][12]. Pour toute question, contactez-nous via le [forum][13].

## Voir également

* [Mettre en surbrillance les annotations dans un PDF à l'aide de C#][14]
* [Ajouter ou supprimer des annotations de fichiers PDF en Java][15]
* [Fichiers PDF en filigrane en Java][16]
* [Ajouter un filigrane aux images en Java][17]







[1]: #highlight-pdf-java-api
[2]: #how-to-highlight-pdf
[3]: https://products.groupdocs.com/annotation/java/
[4]: https://downloads.groupdocs.com/redaction
[5]: https://apireference.groupdocs.com/annotation/java/com.groupdocs.annotation/Annotator#Annotator(java.io.InputStream)
[6]: https://apireference.groupdocs.com/annotation/java/com.groupdocs.annotation.models/Point
[7]: https://apireference.groupdocs.com/annotation/java/com.groupdocs.annotation.models.annotationmodels/HighlightAnnotation
[8]: https://apireference.groupdocs.com/annotation/java/com.groupdocs.annotation/Annotator#add(com.groupdocs.annotation.models.annotationmodels.AnnotationBase)
[9]: https://apireference.groupdocs.com/annotation/java/com.groupdocs.annotation/Annotator#save()
[10]: https://purchase.groupdocs.com/temporary-license
[11]: https://apireference.groupdocs.com/annotation/java/com.groupdocs.annotation.models.annotationmodels/package-frame
[12]: https://docs.groupdocs.com/redaction
[13]: https://forum.groupdocs.com/
[14]: https://blog.groupdocs.com/2021/10/12/highlight-pdf-with-annotations-using-csharp/
[15]: https://blog.groupdocs.com/2021/04/18/annotate-pdf-files-using-java/
[16]: https://blog.groupdocs.com/2021/06/26/add-watermark-to-pdf-in-java/
[17]: https://blog.groupdocs.com/2020/09/15/add-watermark-to-images-in-java/


