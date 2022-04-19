---
title: "Mettre en surbrillance un PDF à l'aide d'annotations en C#"
date: Tue, 12 Oct 2021 14:08:00 +0000
draft: false
url: /fr/2021/10/12/highlight-pdf-with-annotations-using-csharp/
author: 'Shoaib Khan'
summary: "Lors de la révision ou pour attirer le spectateur vers un contenu important, vous devrez peut-être mettre en évidence une partie du document. En tant que développeur, vous pouvez automatiser cette fonctionnalité en utilisant des annotations de surbrillance dans vos applications. Dans cet article, vous apprendrez **comment mettre en surbrillance du texte et n'importe quelle zone dans des fichiers PDF à l'aide de C#**."
tags: ['annotate PDF', 'Annotate PDF in CSharp', 'Highlight Annotation', 'Highlight PDF in CSharp', 'Highlight Text in PDF', 'Text Highlight']
categories: ['GroupDocs.Annotation Product Family']
---

Lors de la révision ou pour attirer le spectateur vers un contenu important, vous devrez peut-être mettre en évidence une partie du document. En tant que développeur, vous pouvez automatiser cette fonctionnalité en utilisant des annotations de surbrillance dans vos applications. Dans cet article, vous apprendrez **comment mettre en surbrillance du texte et n'importe quelle zone dans des fichiers PDF à l'aide de C#**.

Les sujets suivants sont traités ci-dessous :

* [API .NET pour surligner en PDF][1]
* [Comment mettre en surbrillance par programme dans PDF][2]



{{< figure align=center src="images/add-highlight-annotation-in-pdf-using-groupdocs.jpg" alt="Mettre en surbrillance du texte dans un PDF - par programme">}}


## API .NET pour surligner en PDF {#highlight-pdf-dotnet-api}

[GroupDocs.Annotation][3] fournit l'API .NET qui permet de manipuler les annotations et leur automatisation dans les documents au sein des applications .NET. J'utilise cette API pour surligner du texte dans le fichier PDF dans l'exemple de cet article.

Vous pouvez télécharger le programme d'installation **DLLs** ou **MSI** à partir de la [section téléchargements][4] ou installer l'API dans votre application .NET via [NuGet][5].

```
PM> Install-Package GroupDocs.Annotation
```

## Mettre en surbrillance dans un PDF à l'aide de C # {#how-to-highlight-pdf}

Voici les étapes pour mettre en surbrillance du texte ou n'importe quelle zone du PDF à partir de votre application .NET.

* Chargez le document PDF source à l'aide de la classe [Annotator][6].
* Créez l'objet [HighlightAnnotation][7].
* Définissez les propriétés de surbrillance telles que la couleur, l'opacité, le numéro de page et les points.
* Ajoutez la surbrillance définie au document PDF chargé à l'aide de la méthode [Ajouter][8].
* Enregistrez le PDF annoté à l'aide de la méthode [Enregistrer][9].

**Remarque :** Vous pouvez modifier la couleur de surbrillance, l'opacité et d'autres propriétés.

L'exemple de code suivant montre comment mettre en surbrillance le texte d'un PDF par programmation à l'aide de C#.

```
// Mettre en surbrillance le PDF à l'aide de l'annotation de surbrillance en C#
using (Annotator annotator = new Annotator(@"path/sample.pdf"))
{
    HighlightAnnotation highlight = new HighlightAnnotation
    {
        BackgroundColor = 0xFFF000,
        CreatedOn = DateTime.Now,
        Opacity = 0.5,
        PageNumber = 0,
        Points = new List<Point>
        {
            new Point(120, 270),
            new Point(600, 270),
            new Point(120, 300),
            new Point(600, 300)
        }
    };
    annotator.Add(highlight);
    annotator.Save(@"path/annotation-highlight.pdf");
}
```

Voici la sortie du code ci-dessus.



{{< figure align=center src="images/highlight-annotation-in-pdf-using-groupdocs.jpg" alt="Mettre en surbrillance du texte dans un PDF - par programme">}}


## Obtenez une licence API gratuite

Vous pouvez [obtenir une licence temporaire gratuite][10] afin d'utiliser l'API sans les limitations d'évaluation.

## Conclusion

Pour résumer, nous avons appris à ajouter des annotations de surbrillance dans les fichiers PDF par programmation à l'aide de C#. De plus, nous pouvons modifier la couleur de surbrillance, l'opacité et d'autres propriétés. De nombreux [différents types d'annotations][11] peuvent être ajoutés de la même manière à l'aide de la même API.

Pour en savoir plus sur l'API, consultez la [documentation][12]. Pour toute question, contactez-nous via le [forum][13].

## Voir également

* [Fichiers PDF en filigrane à l'aide de C #][14]
* [Ajouter un filigrane aux images à l'aide de C #][15]
* [Ajouter ou supprimer des annotations ou des fichiers Word de balisage à l'aide de C#][16]







[1]: #highlight-pdf-dotnet-api
[2]: #how-to-highlight-pdf
[3]: https://products.groupdocs.com/annotation/
[4]: https://downloads.groupdocs.com/annotation
[5]: https://www.nuget.org/packages/groupdocs.annotation
[6]: https://apireference.groupdocs.com/annotation/net/groupdocs.annotation/annotator
[7]: https://apireference.groupdocs.com/annotation/net/groupdocs.annotation.models.annotationmodels/highlightannotation
[8]: https://apireference.groupdocs.com/annotation/net/groupdocs.annotation/annotator/methods/add/index
[9]: https://apireference.groupdocs.com/annotation/net/groupdocs.annotation/annotator/methods/save/index
[10]: https://purchase.groupdocs.com/temporary-license
[11]: https://apireference.groupdocs.com/annotation/net/groupdocs.annotation.models.annotationmodels
[12]: https://docs.groupdocs.com/redaction
[13]: https://forum.groupdocs.com/
[14]: https://blog.groupdocs.com/2021/07/27/watermark-pdf-files-using-csharp/
[15]: https://blog.groupdocs.com/2020/12/20/add-watermark-to-images-using-csharp-dotnet/
[16]: https://blog.groupdocs.com/2021/06/23/annotate-word-documents-using-csharp/


