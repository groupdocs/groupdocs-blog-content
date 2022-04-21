---
title: "Créer des hyperliens en PDF à l'aide d'annotations en C#"
date: Sat, 16 Oct 2021 01:00:00 +0000
draft: false
url: /fr/2021/10/16/create-hyperlinks-in-pdf-using-annotations-in-csharp/
author: 'Shoaib Khan'
summary: "Les hyperliens sont normalement utilisés pour associer des données externes à n'importe quelle zone spécifiée du document. Nous pouvons transformer n'importe quelle partie des documents en hyperliens en utilisant les annotations de lien. En tant que programmeur, vous pouvez ajouter ces annotations de lien à des documents dans vos applications .NET. Dans cet article, nous allons discuter de **comment créer des hyperliens dans des fichiers PDF à l'aide de C#**."
tags: ['annotate PDF', 'Annotate PDF in CSharp', 'Create Hyperlink in PDF', 'Link Annotation', 'Link Annotation in CSharp', 'Link Annotation in PDF']
categories: ['GroupDocs.Annotation Product Family']
---

Les hyperliens sont normalement utilisés pour associer des données externes à n'importe quelle zone spécifiée du document. Nous pouvons transformer n'importe quelle partie des documents en hyperliens en utilisant les annotations de lien. En tant que programmeur, vous pouvez ajouter ces annotations de lien à des documents dans vos applications .NET. Dans cet article, nous allons discuter de **comment créer des hyperliens dans des fichiers PDF à l'aide de C#**.

Les sujets suivants sont traités ci-dessous:

* [API .NET pour ajouter des hyperliens dans les fichiers PDF][1]
* [Comment créer par programmation des hyperliens dans un PDF][2]



{{< figure align=center src="images/add-link-annotation-in-pdf-using-groupdocs.jpg" alt="Créer un lien dans un PDF - par programmation">}}


## API .NET pour créer des hyperliens en PDF {#hyperlink-dotnet-api}

[GroupDocs.Annotation][3] fournit la solution d'annotation pour différents types d'applications. Son API .NET permet la manipulation et l'automatisation de diverses annotations dans des documents au sein de vos applications .NET. Nous utiliserons son API [GroupDocs.Annotation for .NET][4] pour créer des annotations de lien hypertexte dans le fichier PDF à l'aide de C#.

Vous pouvez télécharger le programme d'installation **DLLs** ou **MSI** à partir de la [section téléchargements][5] ou installer l'API dans votre application .NET via [NuGet][6].

```
PM> Install-Package GroupDocs.Annotation
```

## Créer des hyperliens en PDF en utilisant C # {#how-to-create-hyperlink-annotations}

Voici les étapes pour créer des liens hypertexte n'importe où dans le fichier PDF à l'aide de C#.

* Chargez le document PDF source à l'aide de la classe [Annotator][7].
* Créez l'objet [Lien Annotation][8].
* Définissez les propriétés du lien hypertexte comme l'URL, le numéro de page, les points, etc.
* Ajoutez le lien hypertexte défini au document PDF chargé à l'aide de la méthode [Ajouter][9].
* Enregistrez le PDF annoté à l'aide de la méthode [Enregistrer][10].

L'exemple de code suivant montre comment convertir n'importe quelle partie du fichier PDF en lien hypertexte à l'aide de C#.

```
// Créer des hyperliens au format PDF à l'aide d'annotations de lien en C#
using (Annotator annotator = new Annotator(@"path/sample.pdf"))
{
    LinkAnnotation link = new LinkAnnotation
    {
        CreatedOn = DateTime.Now,
        PageNumber = 0,
        Points = new List<Point>
        {
            new Point(120, 300),
            new Point(600, 300),
            new Point(120, 270),
            new Point(600, 270)
        },
        Url = @"https://products.groupdocs.com/annotation"
    };
    annotator.Add(link);
    annotator.Save(@"path/annotation-link.pdf");
}
```

Voici la sortie du code ci-dessus.



{{< figure align=center src="images/link-annotation-in-pdf-using-groupdocs.jpg" alt="Créer un lien dans un PDF - par programmation">}}


## Obtenez une licence API gratuite

Vous pouvez [obtenir une licence temporaire gratuite][11] afin d'utiliser l'API sans les limitations d'évaluation.

## Conclusion

Pour conclure, vous avez appris comment les annotations de lien peuvent être ajoutées pour créer des hyperliens dans des fichiers PDF à l'aide de C#. De même, en utilisant les annotations de lien, vous pouvez convertir n'importe quelle partie du document en hyperliens. De nombreux autres [types d'annotations][12] peuvent également être ajoutés de manière similaire à l'aide de la même API. Pour en savoir plus sur l'API, consultez la [documentation][13]. Pour toute question, contactez-nous via le [forum][14].

## Voir également

* [Fichiers PDF en filigrane à l'aide de C #][15]
* [Ajouter un filigrane aux images à l'aide de C #][16]
* [Mise en surbrillance du PDF à l'aide des annotations en C#][17]
* [Ajouter ou supprimer des annotations ou des fichiers Word de balisage à l'aide de C#][18]







[1]: #hyperlink-dotnet-api
[2]: #how-to-create-hyperlink-annotations
[3]: https://products.groupdocs.com/annotation/
[4]: https://products.groupdocs.com/annotation/net/
[5]: https://downloads.groupdocs.com/annotation
[6]: https://www.nuget.org/packages/groupdocs.annotation
[7]: https://apireference.groupdocs.com/annotation/net/groupdocs.annotation/annotator
[8]: https://apireference.groupdocs.com/annotation/net/groupdocs.annotation.models.annotationmodels/linkannotation
[9]: https://apireference.groupdocs.com/annotation/net/groupdocs.annotation/annotator/methods/add/index
[10]: https://apireference.groupdocs.com/annotation/net/groupdocs.annotation/annotator/methods/save/index
[11]: https://purchase.groupdocs.com/temporary-license
[12]: https://apireference.groupdocs.com/annotation/net/groupdocs.annotation.models.annotationmodels
[13]: https://docs.groupdocs.com/redaction
[14]: https://forum.groupdocs.com/
[15]: https://blog.groupdocs.com/2021/07/27/watermark-pdf-files-using-csharp/
[16]: https://blog.groupdocs.com/2020/12/20/add-watermark-to-images-using-csharp-dotnet/
[17]: https://blog.groupdocs.com/2021/10/12/highlight-pdf-with-annotations-using-csharp/
[18]: https://blog.groupdocs.com/2021/06/23/annotate-word-documents-using-csharp/


