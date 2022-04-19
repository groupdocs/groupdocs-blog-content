---
title: "Texte barré dans les documents utilisant C#"
date: Sat, 18 Dec 2021 19:10:44 +0000
draft: false
url: /fr/2021/12/18/texte-barré-dans-les-documents-en-utilisant-csharp/
author: 'Shoaib Khan'
summary: "Il y a des cas où vous devez signaler le contenu qui contient des erreurs ou qui n'est plus valide. Barré est l'un des moyens de marquer le contenu non valide dans les documents. Afin d'automatiser la suppression dans les applications .NET, cet article montre **comment barrer du texte dans des documents à l'aide de C#**."
tags: ['Cross out Text', 'Cross out Text in CSharp', 'Strikeout Text', 'Strikethrough Text', 'Strikethrough Text in CSharp']
categories: ['GroupDocs.Annotation Product Family']
---



{{< figure align=center src="images/strikethrough-text-using-csharp.jpg" alt="Texte barré à l'aide de C #">}}


Il y a des cas où vous devez signaler le contenu qui contient des erreurs ou qui n'est plus valide. Le barrage est l'un des moyens de marquer le contenu non valide dans les documents. Ainsi, afin d'automatiser la suppression dans les applications .NET, cet article montre **comment barrer du texte dans des documents à l'aide de C#**.

Les sujets suivants sont abordés dans cet article.

* [API .NET pour les annotations barrées][1]
* [Comment barrer du texte dans des documents][2]

## API .NET pour le texte barré {#strikethrough-text-dotnet-api}

[GroupDocs.Annotation][3] est une solution d'annotation de documents et d'images qui permet d'automatiser divers types d'annotations dans plusieurs formats de documents. Par conséquent, j'utiliserai son API .NET dans les exemples de cet article pour barrer le texte dans les documents. En plus de l'annotation barrée, il existe de nombreux autres [types d'annotation pris en charge][4] mentionnés dans la [documentation][5].

Téléchargez les DLL ou le programme d'installation MSI à partir de la [section des téléchargements][6] ou installez l'API dans votre application .NET via [NuGet][7].

```
PM> Install-Package GroupDocs.Annotation
```

## Comment barrer du texte dans des documents à l'aide de C # {#strikethrough-text-using-csharp}

Commençons rapidement à rayer les erreurs identifiées avec le document. Les étapes suivantes vous permettent de barrer le texte dans les documents à l'aide de C#.

* Chargez le document source à l'aide de la classe [Annotator][8].
* Créez et définissez l'annotation barrée à l'aide de la classe [StrikeoutAnnotation][9].
    * Définissez la couleur de la ligne barrée.
    * Opacité, numéro de page du document
    * Coordonnées et autres propriétés
* Ajoutez l'annotation barrée préparée à l'annotateur à l'aide de la méthode [Add()][10].
* Enregistrez le document annoté en utilisant la méthode [Save()][11].

L'exemple de code C# suivant barre le texte sélectionné dans un document PDF.

```
/*
 * Strikethrough Text in Word, PDF, Spreadsheets, Presentations using C#
 */
using (Annotator annotator = new Annotator("path/document.pdf"))
{
    StrikeoutAnnotation strikeout = new StrikeoutAnnotation
    {
        FontColor = 0x000000,
        Opacity = 0.7,
        PageNumber = 0,
        Points = new List<Point>
        {
            new Point(183, 770),
            new Point(308, 770),
            new Point(183, 752),
            new Point(308, 752)
        }
    };
    annotator.Add(strikeout);
    annotator.Save("path/strikethrough-text.pdf");
}
```

## Obtenez une licence API gratuite

Vous pouvez utiliser gratuitement GroupDocs.Annotation pour .NET en [obtenant une licence temporaire][12].

## Conclusion

Pour résumer, vous avez appris à ajouter des annotations barrées à l'aide de C#. À l'aide de cette annotation, vous pouvez barrer par programme le texte dans Word, PDF, feuille de calcul, documents de présentation. De même, vous pouvez essayer divers autres types d'annotations en fonction de vos besoins.

En savoir plus sur **GroupDocs.Annotation pour .NET** en consultant sa [documentation][13]. Vous pouvez créer votre propre application d'annotation pour les [formats de document pris en charge][14]. Vous pouvez nous contacter pour toute question via le [forum][15].

## Voir également

* [Mise en surbrillance d'un PDF à l'aide d'annotations en C#][16]
* [Souligné ondulé dans les documents utilisant C#][17]







[1]: #strikethrough-text-dotnet-api
[2]: #strikethrough-text-using-csharp
[3]: https://products.groupdocs.com/annotation/
[4]: https://apireference.groupdocs.com/annotation/net/groupdocs.annotation.models.annotationmodels
[5]: https://docs.groupdocs.com/annotation/net/
[6]: https://downloads.groupdocs.com/annotation/net
[7]: https://www.nuget.org/packages/groupdocs.comparison
[8]: https://apireference.groupdocs.com/annotation/net/groupdocs.annotation/annotator
[9]: https://apireference.groupdocs.com/annotation/net/groupdocs.annotation.models.annotationmodels/strikeoutannotation
[10]: https://apireference.groupdocs.com/annotation/net/groupdocs.annotation/annotator/methods/add/index
[11]: https://apireference.groupdocs.com/annotation/net/groupdocs.annotation/annotator/methods/save/index
[12]: https://purchase.groupdocs.com/temporary-license
[13]: https://docs.groupdocs.com/annotation/net
[14]: https://docs.groupdocs.com/annotation/net/supported-document-formats/
[15]: https://forum.groupdocs.com/
[16]: https://blog.groupdocs.com/2021/10/12/highlight-pdf-with-annotations-using-csharp/
[17]: https://blog.groupdocs.com/2021/12/04/add-wavy-underline-in-documents-using-csharp/


