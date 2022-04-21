---
title: "'Ajouter ou supprimer des annotations ou des fichiers PDF balisés à l'aide de C#'"
date: Tue, 25 Jan 2022 14:15:00 +0000
draft: false
url: /fr/2022/01/25/annoter-les-fichiers-pdf-en-utilisant-csharp/
author: 'Shoaib Khan'
summary: "Plus de longues discussions dans de longs fils de discussion sur le contenu du ou des documents. Vous pouvez utiliser des annotations pour annoter des documents avec des messages personnalisés et leurs réponses. Cet article a expliqué **comment annoter par programme des fichiers PDF pour annoter des documents à l'aide de C#**. De plus, nous discuterons également de la manière de supprimer les annotations des fichiers PDF.

Les sujets suivants sont abordés dans cet article :

* API .NET pour annoter les fichiers PDF
* Ajouter des annotations au PDF
    * Annotations fléchées
    * Annotations rectangulaires
    * Annotations Ellipse ou Ovale
    * Annotations de distance
* Supprimer les annotations des fichiers PDF"
tags: ['Add annotations in PDF', 'add annotations in PDF using csharp', 'annotate PDF', 'Annotate PDF in CSharp']
categories: ['GroupDocs.Annotation Product Family']
---

Plus de longues discussions dans de longs fils de discussion sur le contenu du ou des documents. Vous pouvez utiliser des annotations pour annoter des documents avec des messages personnalisés et leurs réponses. Cet article explique **comment annoter par programme des fichiers PDF pour annoter des documents à l'aide de C#**. De plus, nous discuterons également de la manière de supprimer les annotations des fichiers PDF.

Les sujets suivants sont brièvement abordés ci-dessous :

* [API .NET pour annoter les fichiers PDF](#dotnet-annotation-api)
* [Ajouter des annotations au PDF](#add-annotations-to-pdf)
    * [Annotations fléchées](#add-arrow-annotation)
    * [Annotations rectangulaires](#add-area-annotation)
    * [Annotations Ellipse ou Ovale](#add-ellipse-annotation)
    * [Annotations de distance](#add-distance-annotation)
* [Supprimer les annotations des fichiers PDF](#remove-annotations)

## API .NET pour annoter des fichiers PDF {#dotnet-annotation-api}

[GroupDocs.Annotation](https://products.groupdocs.com/annotation/) a son API .NET pour travailler avec les annotations dans les documents et les images. Il vous permet d'ajouter, de supprimer et d'extraire des annotations à partir de documents, de feuilles de calcul et de présentations PDF et Word. De plus, il prend en charge les images, les pages Web, les messages électroniques, les dessins Visio et bien plus encore. Vous pouvez consulter la documentation pour la liste complète des [formats de document pris en charge pour l'annotation](https://docs.groupdocs.com/annotation/net/supported-document-formats/).

Téléchargez son programme d'installation **DLLs** ou **MSI** à partir de la [section téléchargements](https://downloads.groupdocs.com/annotation) ou installez l'API dans votre application .NET via [NuGet](https://www.nuget.org/packages/groupdocs.annotation). Vous pouvez également utiliser la commande suivante du gestionnaire de packages.

```
PM> Install-Package GroupDocs.Annotation
```

## Ajouter des annotations au PDF à l'aide de C# {#add-annotations-to-pdf}

Il existe de nombreux types d'annotations disponibles à ajouter dans les documents, cependant, nous n'en discuterons que quelques-uns dans cet article.



{{< figure align=center src="images/added-annotations-to-pdf.jpg" alt="Ajout d'annotations au PDF">}}


Voici quelques-unes des annotations prises en charge. Vous pouvez [en savoir plus sur chaque annotation individuellement](https://docs.groupdocs.com/annotation/net/add-annotation-to-the-document/).

<figure class="wp-block-table is-style-regular"><table><tbody><tr><td>- Annotation Zone / Rectangle<br> - Flèche<br> - Distance<br> - Ellipse<br> - Surligner<br> - Lien<br> - Indiquer<br> - Polyligne</td><td> - Remplacement<br> - Rédaction de ressources<br> - Barré<br> - Champ de texte<br> - Rédaction de texte<br> - Souligné<br> - Filigrane</td></tr></tbody></table></figure>

## Ajouter une annotation de flèche au PDF à l'aide de C# {#add-arrow-annotation}

Voici les étapes à suivre pour ajouter des annotations fléchées aux documents PDF en C#.



{{< figure align=center src="images/arrow-annotation.jpg" alt="Ajouter une annotation de flèche par programmation dans Java et C# .NET">}}


* Chargez le document PDF à l'aide de la classe [Annotator](https://apireference.groupdocs.com/annotation/net/groupdocs.annotation/annotator).
* Initialiser l'[annotation de flèche](https://apireference.groupdocs.com/annotation/net/groupdocs.annotation.models.annotationmodels/arrowannotation).
* Définissez la position, la taille, le numéro de page de l'annotation fléchée.
* Ajoutez l'annotation de flèche définie à l'aide de la méthode [Add](https://apireference.groupdocs.com/annotation/net/groupdocs.annotation/annotator/methods/add/index).
* Enregistrez le document annoté à l'aide de la méthode [Save()](https://apireference.groupdocs.com/annotation/net/groupdocs.annotation/annotator/methods/save/index) appropriée.

L'exemple de code C# suivant montre comment ajouter une annotation de flèche à un document PDF.

```
// Ajouter une annotation de flèche aux documents PDF à l'aide de C#
using (Annotator annotator = new Annotator("path/document.pdf"))
{
    ArrowAnnotation arrow = new ArrowAnnotation
    {
        Box = new Rectangle(100, 100, 50, 50),

        // optional --
        CreatedOn = DateTime.Now,
        Message = "Your Message",
        Opacity = 0.7,
        PageNumber = 0,
        PenColor = -3407872,
        PenStyle = PenStyle.Solid,
        PenWidth = 2
    };
    annotator.Add(arrow);
    annotator.Save("path/annotation.pdf");
}
```

## Insérer un rectangle ou une annotation de zone dans un PDF à l'aide de C# {#add-area-annotation}

Voici les étapes pour ajouter une annotation de rectangle ou de zone à un document PDF avec quelques personnalisations. Il est très similaire à l'ajout d'annotations Arrow mais utilise **AreaAnnotation**.

* Chargez le document PDF à l'aide de la classe [Annotator](https://apireference.groupdocs.com/annotation/net/groupdocs.annotation/annotator).
* Initialisez l'annotation rectangle à l'aide de la classe [AreaAnnotation](https://apireference.groupdocs.com/annotation/net/groupdocs.annotation.models.annotationmodels/areaannotation).
* Spécifiez la position, la taille et la couleur du rectangle.
* Vous pouvez également définir d'autres propriétés comme le **numéro de page, l'arrière-plan, l'opacité, le style, la largeur du stylo**, les **messages** et l'**heure**.
* Ajoutez l'annotation rectangulaire définie à l'Annotateur.
* Enfin, enregistrez le fichier annoté à l'aide de la méthode [Save()](https://apireference.groupdocs.com/annotation/net/groupdocs.annotation/annotator/methods/save/index).



{{< figure align=center src="images/rectangle-area-annotation.jpg" alt="Ajouter un rectangle ou une annotation de zone par programmation dans C# .NET et Java">}}


L'exemple de code suivant ajoute une annotation rectangle/zone à un document PDF à l'aide de C#.

```
// Ajouter une annotation de zone ou de rectangle dans des documents PDF à l'aide de C#
using (Annotator annotator = new Annotator("path/document.pdf"))
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
    annotator.Save("path/annotation.pdf");
}
```

## Ajouter une annotation ovale ou ellipse au PDF à l'aide de C# {#add-ellipse-annotation}

De même, ajoutons l'annotation ellipse/ovale. Les étapes suivantes montrent comment une annotation ovale ou une annotation ellipse peut être ajoutée à un fichier PDF à l'aide de C#.



{{< figure align=center src="images/ellipses-annotation.jpg" alt="Ajouter des ellipses ou des annotations ovales par programmation dans C# .NET et Java">}}


* Chargez le fichier PDF à l'aide de la classe [Annotator](https://apireference.groupdocs.com/annotation/net/groupdocs.annotation/annotator).
* Initialisez [Ellipse Annotation](https://apireference.groupdocs.com/annotation/net/groupdocs.annotation.models.annotationmodels/ellipseannotation).
* Définissez la position, la taille et d'autres propriétés de l'annotation initialisée.
* Ajoutez l'annotation d'ellipse créée à l'objet Annotator.
* Utilisez la méthode [Save()](https://apireference.groupdocs.com/annotation/net/groupdocs.annotation/annotator/methods/save/index) pour enregistrer le fichier PDF annoté.

L'exemple de code C# suivant ajoute une annotation ovale/ellipse à un document PDF.

```
// Ajouter une annotation ovale ou ellipse dans des documents PDF à l'aide de C#
using (Annotator annotator = new Annotator("path/document.pdf"))
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
    annotator.Save("path/annotation.pdf");
}
```

## Insérer une annotation de distance dans un PDF à l'aide de C# {#add-distance-annotation}

Vous pouvez utiliser l'annotation de distance pour indiquer la distance entre deux objets. Voici les étapes qui permettent d'ajouter des annotations de distance au document PDF à l'aide de C#.



{{< figure align=center src="images/distance-annotation.jpg" alt="Ajouter une annotation de distance par programmation dans C# .NET et Java">}}


* Après avoir chargé le document PDF à l'aide de la classe [Annotator](https://apireference.groupdocs.com/annotation/net/groupdocs.annotation/annotator), initialisez l'annotation de distance à l'aide de [DistanceAnnotation](https://apireference.groupdocs.com/annotation/net/groupdocs.annotation.models.annotationmodels/distanceannotation).
* Définissez l'apparence, la couleur de la ligne, l'épaisseur, le style, etc.
* Ajoutez l'annotation de distance à l'Annotateur.
* Enregistrez le fichier PDF avec l'annotation à l'aide de la méthode [Save()](https://apireference.groupdocs.com/annotation/net/groupdocs.annotation/annotator/methods/save/index) appropriée.

L'extrait de code suivant montre comment ajouter l'annotation de distance dans le PDF à l'aide de C#.

```
// Ajouter une annotation de distance aux documents PDF à l'aide de C#
using (Annotator annotator = new Annotator("path/document.pdf"))
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
    annotator.Save("path/annotation.pdf");
}
```

## Supprimer les annotations des fichiers PDF à l'aide de C# {#remove-annotations}

Il existe différentes façons de supprimer les annotations des documents PDF. Soit, vous pouvez supprimer toutes les annotations à la fois, soit vous pouvez fournir des identifiants, des index pour supprimer les annotations sélectives. Nous avons discuté des [différentes façons de supprimer les annotations](https://blog.groupdocs.com/2022/01/27/remove-annotations-from-pdf-or-word-documents-using-csharp) dans l'article séparé. Cependant, voici les étapes pour supprimer toutes les annotations d'un fichier PDF.

* Charger le document.
* Initialisez les [options de sauvegarde](https://apireference.groupdocs.com/annotation/net/groupdocs.annotation.options/saveoptions).
* Définissez les types d'annotations sur **Aucun**.
* Enregistrez le fichier PDF sans annotation à l'aide de la méthode [Save()](https://apireference.groupdocs.com/annotation/net/groupdocs.annotation/annotator/methods/save/index).

Le code C# suivant montre comment supprimer les annotations des fichiers PDF.

```
// Supprimez toutes les annotations du document PDF à l'aide de C#
using (Annotator annotator = new Annotator("path/document.pdf"))
{
    annotator.Save("path/document-noAnnotation.pdf", new SaveOptions {AnnotationTypes = AnnotationType.None});
}
```

## Conclusion

Pour conclure, vous avez appris à ajouter différentes annotations aux documents PDF dans les applications .NET à l'aide de C#. Plus précisément, nous avons ajouté des annotations de flèche, d'ellipse, de surface et de distance. De plus, vous avez également vu l'un des moyens de supprimer toutes les annotations de n'importe quel fichier PDF.

Vous pouvez penser à créer votre propre application .NET d'annotateur de documents. Pour en savoir plus sur **GroupDocs.Annotation pour .NET**, consultez la [documentation](https://docs.groupdocs.com/annotation/net/) et le [GitHub](https://github.com/groupdocs-annotation). Pour toute autre question, contactez le support sur le [forum](https://forum.groupdocs.com/).

## Voir également

* [Créer des hyperliens en PDF à l'aide d'annotations en C#](https://blog.groupdocs.com/2021/10/16/create-hyperlinks-in-pdf-using-annotations-in-csharp/)
* [Mise en surbrillance du PDF à l'aide d'annotations en C#](https://blog.groupdocs.com/2021/10/12/highlight-pdf-with-annotations-using-csharp/)
* [Ajouter ou supprimer des annotations ou des fichiers Word de balisage à l'aide de C#](https://blog.groupdocs.com/2021/06/23/annotate-word-documents-using-csharp/)





