---
title: "Ajouter un soulignement ondulé dans Word, PDF et autres documents à l'aide de C #"
date: Sat, 04 Dec 2021 15:37:01 +0000
draft: false
url: /fr/2021/12/04/add-wavy-underline-in-documents-using-csharp/
author: 'Shoaib Khan'
summary: "Les soulignements ondulés sont normalement utilisés pour montrer les incohérences dans le document. Nous connaissons bien ces lignes car Microsoft Word utilise des soulignements ondulés rouges pour indiquer les fautes d'orthographe et des soulignements ondulés/onduleux bleus pour les problèmes de formatage. Nous pouvons également ajouter de telles annotations de soulignement dans les documents par programmation. Dans cet article, nous allons apprendre **comment ajouter des soulignements ondulés dans Word, PDF, PPT et d'autres documents à l'aide de C#**."
tags: ['Annotation in CSharp', 'Squiggly Annotation in CSharp', 'Squiggly Underline in Word', 'Wavy Underline in CSharp', 'Wavy Underline in Word']
categories: ['GroupDocs.Annotation Product Family']
---

Les soulignements ondulés sont normalement utilisés pour montrer les incohérences dans le document. Nous connaissons bien ces lignes car Microsoft Word utilise des soulignements ondulés rouges pour indiquer les fautes d'orthographe et des soulignements ondulés/onduleux bleus pour les problèmes de formatage. Nous pouvons également ajouter de telles annotations de soulignement dans les documents par programmation. Dans cet article, nous allons apprendre **comment ajouter des soulignements ondulés dans Word, PDF, PPT et d'autres documents à l'aide de C#**.



{{< figure align=center src="images/adding-squiggly-annotation.jpg" alt="Ajouter des annotations sinueuses aux documents">}}


Les sujets suivants sont abordés ci-dessous :

* [API .NET pour Wavy Underline / Squiggly Annotation][1]
* [Ajouter un soulignement ondulé au texte dans les documents Word - Annotation ondulée][2]
* [Ajouter un soulignement ondulé au texte en PDF, PPT et autres documents][3]

## API .NET pour Wavy Underline - Annotation Squiggly {#wavy-underline-dotnet-api}

[GroupDocs.Annotation][4] fournit la solution d'annotation qui permet la manipulation et l'automatisation de divers types d'annotations dans les documents au sein des applications .NET. Nous utiliserons son API [GroupDocs.Annotation for .NET][5] pour ajouter une annotation sinueuse dans les documents utilisant C#.

Vous pouvez télécharger le programme d'installation **DLLs** ou **MSI** depuis la [section téléchargements][6] ou installer l'API dans votre application .NET via [NuGet][7].

```
PM> Install-Package GroupDocs.Annotation
```

## Ajouter un soulignement ondulé au texte dans Word (DOC/DOCX) à l'aide de C# - Squiggly Annotation {#add-wavy-underline-in-word}

L'étape suivante montre comment insérer un soulignement ondulé dans un document Word à l'aide de C#.

* **Chargez** le mot (DOC, DOCX) en utilisant la classe [Annotator][8].
* **Créez le soulignement ondulé** à l'aide de la classe [SquigglyAnnotation][9].
* **Personnalisez** le soulignement ondulé en définissant sa couleur, son opacité, ses coordonnées, le numéro de page, etc.
* [**Ajouter**][10] l'annotation sinueuse à l'annotateur.
* **Enregistrer** le fichier Word mis à jour en utilisant la méthode [Save()][11].

L'exemple de code C# suivant ajoute le soulignement ondulé au texte sélectionné du document Word.

```
/*
 * Add wavy underline (Squiggly Annotation) to text in DOC, DOCX files using C#
 */
using (Annotator annotator = new Annotator("path/document.docx"))
{
    SquigglyAnnotation squiggly = new SquigglyAnnotation
    {
        BackgroundColor = 0xFFF000,
        FontColor = 0xFF0000,
        Message = "This is Squiggly Annotation",
        CreatedOn = DateTime.Now,
        Opacity = 0.5,
        PageNumber = 0,
        Points = new List<Point>
        {
            new Point(20, 170),
            new Point(290, 170),
            new Point(20, 200),
            new Point(290, 200)
        }
    };
    annotator.Add(squiggly);
    annotator.Save("path/squiggly-document.docx");
}
```

Vous pouvez ajouter n'importe quel autre type d'annotation à partir de divers [AnnotationModels][12].

## Ajouter un soulignement ondulé au texte dans les documents PDF, PPT et autres à l'aide de C # {#wavy-underline-in-pdf-ppt-etc}

De même, vous pouvez ajouter le soulignement ondulé à n'importe quel document utilisant le même code C# (vérifiez la documentation si le format de fichier de votre document prévu est pris en charge par l'API).

Voici les étapes à suivre pour insérer un soulignement ondulé dans un document PDF à l'aide de C#.

* **Chargez** le document PDF en utilisant la classe [Annotator][13].
* **Créez le soulignement ondulé** à l'aide de la classe [SquigglyAnnotation][14].
* ** Personnalisez ** la couleur, l'opacité, les coordonnées, le numéro de page, etc. pour le soulignement ondulé / ondulé.
* **Ajoutez** l'annotation sinueuse à l'annotateur à l'aide de la méthode [Add()][15].
* **Enregistrer** le fichier PDF mis à jour en utilisant la méthode [Save()][16].

L'exemple de code C# suivant ajoute le soulignement ondulé au texte sélectionné du fichier PDF.

```
/*
 * Add wavy underline (Squiggly Annotation) to text in PDF file using C#
 */
using (Annotator annotator = new Annotator("path/document.pdf"))
{
    SquigglyAnnotation squiggly = new SquigglyAnnotation
    {
        FontColor = 0xFF0000,
        Opacity = 0.5,
        PageNumber = 0,
        Points = new List<Point>
        {
            new Point(20, 100),
            new Point(150, 100),
            new Point(20, 130),
            new Point(150, 130)
        }
    };
    annotator.Add(squiggly);
    annotator.Save("path/squiggly-document.pdf");
}
```

## Conclusion

Pour résumer, nous avons discuté de la façon d'ajouter un soulignement ondulé / ondulé dans les documents Word à l'aide de C #. De plus, la même annotation ondulée peut être ajoutée à d'autres documents tels que PDF, PPT, etc. L'annotation Squiggly est un nouvel ajout à [de nombreux autres types d'annotations proposés par l'API][17].

En savoir plus sur **GroupDocs.Annotation pour .NET**. Consultez sa [documentation][18] pour commencer à créer vos propres applications d'annotation de documents pour divers [formats de documents pris en charge][19]. Pour toute question, contactez-nous via le [forum][20].

## Voir également

* [Ajouter ou supprimer des annotations ou des fichiers Word de balisage à l'aide de C#][21]
* [Ajouter ou supprimer des annotations à partir de fichiers PDF à l'aide de Java][22]







[1]: #wavy-underline-dotnet-api
[2]: #add-wavy-underline-in-word
[3]: #wavy-underline-in-pdf-ppt-etc
[4]: https://products.groupdocs.com/annotation/
[5]: https://products.groupdocs.com/annotation/net/
[6]: https://downloads.groupdocs.com/annotation
[7]: https://www.nuget.org/packages/groupdocs.annotation
[8]: https://apireference.groupdocs.com/annotation/net/groupdocs.annotation/annotator
[9]: https://apireference.groupdocs.com/annotation/net/groupdocs.annotation.models.annotationmodels/squigglyannotation
[10]: https://apireference.groupdocs.com/annotation/net/groupdocs.annotation/annotator/methods/add/index
[11]: https://apireference.groupdocs.com/annotation/net/groupdocs.annotation/annotator/methods/save/index
[12]: https://apireference.groupdocs.com/annotation/net/groupdocs.annotation.models.annotationmodels
[13]: https://apireference.groupdocs.com/annotation/net/groupdocs.annotation/annotator
[14]: https://apireference.groupdocs.com/annotation/net/groupdocs.annotation.models.annotationmodels/squigglyannotation
[15]: https://apireference.groupdocs.com/annotation/net/groupdocs.annotation/annotator/methods/add/index
[16]: https://apireference.groupdocs.com/annotation/net/groupdocs.annotation/annotator/methods/save/index
[17]: https://apireference.groupdocs.com/annotation/net/groupdocs.annotation.models.annotationmodels
[18]: https://docs.groupdocs.com/annotation/net
[19]: https://docs.groupdocs.com/annotation/net/supported-document-formats/
[20]: https://forum.groupdocs.com/
[21]: https://blog.groupdocs.com/2021/06/23/annotate-word-documents-using-csharp/
[22]: https://blog.groupdocs.com/2021/04/18/annotate-pdf-files-using-java/


