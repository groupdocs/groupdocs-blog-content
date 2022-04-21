---
title: "Ajouter ou supprimer des annotations ou des fichiers Word de balisage à l'aide de C#"
date: Wed, 23 Jun 2021 11:23:00 +0000
draft: false
url: /fr/2021/06/23/annoter-des-documents-word-avec-csharp/
aliases:
- /2021/06/24/annotate-documents-programmatically-using-groupdocs.annotation-for-.net/
- /2019/10/14/annotate-documents-programmatically-using-groupdocs.annotation-for-.net/
author: 'Shoaib Khan'
summary: 'Forget to discuss documents content and feedbacks in long email threads. Simply use annotations to markup documents with messages and replies. In this article, you will learn how to programmatically add and remove annotations to markup Word documents in C# with your .NET applications.

Les sujets suivants sont abordés dans cet article :

* API .NET pour les annotations Word DOC/DOCX
* Ajouter des annotations à Word
    * Annotations fléchées
    * Annotations rectangulaires
    * Annotations Ellipse ou Ovale
    * Annotations de distance
* Supprimer les annotations des fichiers Word'
tags: ['Add Annotations in Word using CSharp', 'Annotate Word in CSharp', 'Remove Annotations from Word in C#']
categories: ['GroupDocs.Annotation Product Family']
---

Oubliez de discuter du contenu des documents et des commentaires dans de longs fils de discussion. Utilisez simplement des annotations pour baliser les documents avec des messages et des réponses. Dans cet article, vous apprendrez à ajouter et à supprimer par programmation des annotations pour baliser des documents Word en C# avec vos applications .NET.

Voici les sujets abordés brièvement ci-dessous :

* [API .NET pour les annotations Word DOC/DOCX][1]
* [Ajouter des annotations à Word][2]
    * [Annotations fléchées][3]
    * [Annotations rectangulaires][4]
    * [Annotations Ellipse ou Ovale][5]
    * [Notes de distance][6]
* [Supprimer les annotations des fichiers Word][7]

## API .NET pour annoter et annoter des fichiers Word {#dotnet-annotation-api}

[GroupDocs.Annotation][8] fournit l'API .NET pour travailler avec les annotations de vos documents et images dans vos applications .NET. L'API vous permet d'ajouter, de supprimer et d'extraire des annotations à partir de documents Word. En outre, il prend en charge les feuilles de calcul, les présentations, les images, les fichiers PDF, les pages Web, les messages électroniques et les dessins Visio. Certains dessins AutoCAD et formats d'imagerie numérique tels que DICOM figurent également sur la liste. Pour la liste complète des [formats de document pris en charge pour l'annotation][9], vous pouvez consulter la documentation.

Téléchargez le programme d'installation **DLLs** ou **MSI** à partir de la [section téléchargements][10] ou installez l'API dans votre application .NET via [NuGet][11]. Vous pouvez également utiliser la commande suivante du gestionnaire de packages.

```
PM> Install-Package GroupDocs.Annotation
```

## Ajouter des annotations à Word en C# {#add-annotations-to-word}

Ajoutons quelques-uns des différents types d'annotations aux documents Word. Il existe de nombreux types d'annotations différents, nous n'en couvrirons donc que quelques-uns dans cet article.



{{< figure align=center src="images/add-annotations-to-doc-docx-using-groupdocs-dotnet-java-api-1024x624.png" alt="Ajouter des annotations à DOC DOCX à l'aide de l'API GroupDocs">}}


Il existe certains des types d'annotations pris en charge, vous pouvez [en savoir plus sur chaque annotation individuellement][12].

* Annotation Zone / Rectangle
* Flèche
* Souligner
* Filigrane
* Distance
* Barré
* Champ de texte
* Ellipse
* Souligner
* Lien
* Indiquer
* Polyligne
* Remplacement
* Rédaction des ressources
* Rédaction de texte

## Ajouter une annotation de flèche à Word à l'aide de C # {#add-arrow-annotation}

Voici les étapes pour ajouter une annotation de flèche à un document Word en C#.



{{< figure align=center src="images/arrow-annotation.jpg" alt="Ajouter une annotation de flèche par programmation dans Java et .NET">}}


* Chargez le document en utilisant la classe [Annotator][13].
* Initialiser l'annotation fléchée avec la classe [ArrowAnnotation][14].
* Ajustez la position, la taille, le numéro de page de l'annotation de la flèche.
* Ajoutez l'annotation de flèche créée à l'aide de la méthode [Add][15].
* Enregistrez le document Word annoté dans le chemin à l'aide de la méthode [Enregistrer][16].

L'exemple de code suivant montre comment ajouter une annotation de flèche à un document Word à l'aide de C#.

```
// Ajouter une annotation de flèche aux documents Word à l'aide de C#
using (Annotator annotator = new Annotator("path/document.docx"))
{
    ArrowAnnotation arrow = new ArrowAnnotation
    {
        Box = new Rectangle(100, 100, 50, 50),
        CreatedOn = DateTime.Now,
        Message = "Your Message",
        Opacity = 0.7,
        PageNumber = 0,
        PenColor = -3407872,
        PenStyle = PenStyle.Solid,
        PenWidth = 2
    };
    annotator.Add(arrow);
    annotator.Save("path/annotation.docx");
}
```

## Insérer un rectangle ou une annotation de zone dans Word à l'aide de C # {#add-area-annotation}

Des personnalisations peuvent être effectuées pour n'importe quelle annotation lors de son ajout au document. Voici les étapes pour ajouter une annotation de rectangle ou de zone à un document DOC/DOCX avec quelques personnalisations. Cela ressemble beaucoup à l'ajout d'annotations Arrow mais utilise cette fois la classe **AreaAnnotation**.

* Chargez le document DOC/DOCX en utilisant la classe [Annotator][17].
* Initialiser l'annotation du rectangle à l'aide de la classe [AreaAnnotation][18].
* Ajustez la position, la taille et la couleur du rectangle.
* Définissez d'autres propriétés telles que **numéro de page, arrière-plan, opacité, style, largeur du stylo**, **messages** et **heure**.
* Ajoutez l'annotation rectangulaire créée à l'annotateur.
* Enregistrez le fichier annoté dans le chemin en utilisant la méthode [Save][19].



{{< figure align=center src="images/rectangle-area-annotation.jpg" alt="Ajouter un rectangle ou une annotation de zone par programmation dans .NET et Java">}}


L'exemple de code suivant montre comment ajouter une annotation de rectangle/zone à un document Word à l'aide de C#.

```
// Ajouter une annotation de zone ou de rectangle dans des documents Word à l'aide de C #
using (Annotator annotator = new Annotator("path/document.docx"))
{
    AreaAnnotation area = new AreaAnnotation
    {
        BackgroundColor = 65535,
        Box = new Rectangle(80, 75, 450, 135),
        Message = "This is area annotation",
        Opacity = 0.2,
        PageNumber = 0,
        PenColor = -131,
        PenStyle = PenStyle.Dash,
        PenWidth = 3
    };
    annotator.Add(area);
    annotator.Save("path/annotation.docx");
}
```

## Ajouter une annotation ovale ou ellipse à Word à l'aide de C# {#add-ellipse-annotation}

Voici les étapes pour ajouter une annotation ovale ou une annotation ellipse à un document en C#.



{{< figure align=center src="images/ellipses-annotation.jpg" alt="Ajouter des ellipses ou des annotations ovales par programmation dans C# .NET et Java">}}


* Chargez le document DOC/DOCX en utilisant la classe [Annotator][20].
* Initialiser l'annotation d'ellipse à l'aide de la classe [EllipseAnnotation][21].
* Définissez la position et la taille de l'annotation d'ellipse initialisée.
* Ajoutez l'annotation d'ellipse créée à l'objet Annotator.
* Indiquez le chemin et enregistrez le fichier Word annoté en utilisant la méthode [Save][22].

L'exemple de code suivant montre comment ajouter une annotation ovale ou elliptique à un document Word à l'aide de C#.

```
// Ajouter une annotation ovale ou ellipse dans des documents Word à l'aide de C #
using (Annotator annotator = new Annotator("path/document.docx"))
{
    EllipseAnnotation ellipse = new EllipseAnnotation
    {
        BackgroundColor = -16034924,
        Box = new Rectangle(275, 475, 300, 80),
        Message = "This is ellipse annotation",
        Opacity = 0.2,
        PageNumber = 0,
        PenColor = -16034924,
        PenStyle = PenStyle.Dot,
        PenWidth = 3
    };
    annotator.Add(ellipse);
    annotator.Save("path/annotation.docx");
}
```

## Insérer une annotation de distance dans Word à l'aide de C# {#add-distance-annotation}

De même, vous pouvez ajouter l'annotation de distance pour marquer la distance entre deux points. Voici les étapes pour ajouter une annotation de distance au document.



{{< figure align=center src="images/distance-annotation.jpg" alt="Ajouter une annotation de distance par programmation dans C# .NET et Java">}}


* Après avoir chargé le document Word, initialisez l'annotation de distance à l'aide de la classe [DistanceAnnotation][23].
* Définissez l'apparence de l'annotation.
* Ajoutez l'annotation de distance à l'objet Annotator.
* Enregistrez les fichiers Word annotés à l'emplacement indiqué en spécifiant le chemin.

L'exemple de code suivant montre comment ajouter une annotation de distance à un document DOC/DOCX à l'aide de C#.

```
// Ajouter une annotation de distance aux documents Word à l'aide de C#
using (Annotator annotator = new Annotator("path/document.docx"))
{
    DistanceAnnotation distance = new DistanceAnnotation
    {
        Box = new Rectangle(750, 235, 0, 150),
        Message = "This is the heading area",
        Opacity = 0.7,
        PageNumber = 0,
        PenColor = -21197,
        PenStyle = PenStyle.Solid,
        PenWidth = 3
    };
    annotator.Add(distance);
    annotator.Save("path/annotation.docx");
}
```

## Code complet

Pour résumer, voici le code complet avec la sortie montrant toutes les **annotations** et **messages** ajoutés avec les **réponses**. Le code C# suivant ci-dessous ajoute une flèche, un rectangle, une ellipse, des annotations de distance, des messages et des réponses à un fichier Word.

```
// Ajouter plusieurs annotations à Word à l'aide de C#
// Ajout d'annotations de flèche, de zone, d'ovale (ellipse) et de distance à DOC/DOCX avec des messages et des réponses à l'aide de C#
string outputPath = @"outputPath/annotatedDoc.docx";
string inputFile = @"inputPath/document.docx";

using (Annotator annotator = new Annotator(inputFile))
{
    ArrowAnnotation arrow = new ArrowAnnotation
    {
        Box = new Rectangle(550, 250, 60, -60),
        CreatedOn = DateTime.Now,
        Message = "This image is little upwards.",
        Opacity = 0.7,
        PageNumber = 0,
        PenColor = -3407872,
        PenStyle = PenStyle.Solid,
        PenWidth = 2,
        Replies = new List<Reply>
        {
            new Reply
            {
                Comment = "Please look in to these issues.",
                RepliedOn = DateTime.Now
            },
            new Reply
            {
                    Comment = "Change Description",
                RepliedOn = DateTime.Now
            },
            new Reply
            {
                Comment = "On-Premises APIs",
                RepliedOn = DateTime.Now
            },
            new Reply
            {
                Comment = "Add images as well.",
                RepliedOn = DateTime.Now
            }
        }
    };
    AreaAnnotation area = new AreaAnnotation
    {
        BackgroundColor = 65535,
        Box = new Rectangle(80, 75, 450, 135),
        Message = "This is area annotation",
        Opacity = 0.2,
        PageNumber = 0,
        PenColor = -131,
        PenStyle = PenStyle.Dash,
        PenWidth = 3
    };
    EllipseAnnotation ellipse = new EllipseAnnotation
    {
        BackgroundColor = -16034924,
        Box = new Rectangle(275, 475, 300, 80),
        Message = "This is ellipse annotation",
        Opacity = 0.2,
        PageNumber = 0,
        PenColor = -16034924,
        PenStyle = PenStyle.Dot,
        PenWidth = 3
    };
    DistanceAnnotation distance = new DistanceAnnotation
    {
        Box = new Rectangle(750, 235, 0, 150),
        Message = "This is the heading area",
        Opacity = 0.7,
        PageNumber = 0,
        PenColor = -21197,
        PenStyle = PenStyle.Solid,
        PenWidth = 3
    };
    annotator.Add(arrow);
    annotator.Add(area);
    annotator.Add(ellipse);
    annotator.Add(distance);

    annotator.Save(outputPath);
}
```

## Supprimer les annotations des fichiers Word DOC/DOCX à l'aide de C# {#remove-annotations}

Les annotations des documents peuvent être supprimées facilement. Il existe de nombreuses options pour supprimer les annotations d'un document Word. Vous pouvez supprimer toutes les annotations à la fois. De plus, vous pouvez fournir les index pour supprimer les annotations spécifiques. Pour plus d'options, consultez l'article [documentation][24].

Voici les étapes pour supprimer toutes les annotations d'un fichier Word.

* Charger le document.
* Initialiser les options d'enregistrement à l'aide de la classe [SaveOptions][25].
* Définissez les types d'annotations sur Aucun.
* Enregistrez le fichier Word. Il n'y aura aucune annotation dedans.

Le code suivant montre comment supprimer des annotations d'un fichier Word à l'aide de C#.

```
// Supprimez toutes les annotations du document Word à l'aide de C #
using (Annotator annotator = new Annotator(outputPath))
{
    annotator.Save(remOutputPath, new SaveOptions {AnnotationTypes = AnnotationType.None});
}
```

## Conclusion

En bref, vous avez appris à ajouter des annotations aux documents Word dans les applications .NET à l'aide de C#. Plus précisément, nous avons ajouté des annotations de flèche, d'ellipse, de zone et de distance au fichier Word DOC/DOCX. De plus, vous avez également vu comment supprimer toutes les annotations de n'importe quel fichier Word. Maintenant, vous pouvez penser à créer votre propre application .NET d'annotateur de documents.

En savoir plus sur GroupDocs.Annotation pour .NET à partir de la [documentation][26] et du référentiel [GitHub][27]. Pour toute autre question, contactez le support sur le [forum][28].

## Voir également

* [Ajouter un filigrane aux images à l'aide de C #][29]
* [Annoter des fichiers PDF en Java][30]







[1]: #dotnet-annotation-api
[2]: #add-annotations-to-word
[3]: #add-arrow-annotation
[4]: #add-area-annotation
[5]: #add-ellipse-annotation
[6]: #add-distance-annotation
[7]: #remove-annotations
[8]: https://products.groupdocs.com/annotation/
[9]: https://docs.groupdocs.com/annotation/net/supported-document-formats/
[10]: https://downloads.groupdocs.com/annotation
[11]: https://www.nuget.org/packages/groupdocs.annotation
[12]: https://docs.groupdocs.com/annotation/net/add-annotation-to-the-document/
[13]: https://apireference.groupdocs.com/annotation/net/groupdocs.annotation/annotator
[14]: https://apireference.groupdocs.com/annotation/net/groupdocs.annotation.models.annotationmodels/arrowannotation
[15]: https://apireference.groupdocs.com/annotation/net/groupdocs.annotation/annotator/methods/add/index
[16]: https://apireference.groupdocs.com/annotation/net/groupdocs.annotation/annotator/methods/save/index
[17]: https://apireference.groupdocs.com/annotation/net/groupdocs.annotation/annotator
[18]: https://apireference.groupdocs.com/annotation/net/groupdocs.annotation.models.annotationmodels/areaannotation
[19]: https://apireference.groupdocs.com/annotation/net/groupdocs.annotation/annotator/methods/save/index
[20]: https://apireference.groupdocs.com/annotation/net/groupdocs.annotation/annotator
[21]: https://apireference.groupdocs.com/annotation/net/groupdocs.annotation.models.annotationmodels/ellipseannotation
[22]: https://apireference.groupdocs.com/annotation/net/groupdocs.annotation/annotator/methods/save/index
[23]: https://apireference.groupdocs.com/annotation/net/groupdocs.annotation.models.annotationmodels/distanceannotation
[24]: https://docs.groupdocs.com/annotation/net/remove-annotation-from-document/
[25]: https://apireference.groupdocs.com/annotation/net/groupdocs.annotation.options/saveoptions
[26]: https://docs.groupdocs.com/annotation/net/
[27]: https://github.com/groupdocs-annotation
[28]: https://forum.groupdocs.com/
[29]: https://blog.groupdocs.com/2020/12/20/add-watermark-to-images-using-csharp-dotnet/
[30]: https://blog.groupdocs.com/2021/04/18/annotate-pdf-files-using-java/


