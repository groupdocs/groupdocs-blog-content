---
title: "Comment réorganiser les pages PDF à l'aide de C#"
date: Tue, 22 Feb 2022 12:10:45 +0000
draft: false
url: /fr/2022/02/22/move-pdf-pages-using-csharp/
author: 'Shoaib Khan'
summary: "En cette ère numérique, le PDF est l'un des formats de fichiers les plus utilisés et est populaire en raison de sa portabilité. D'autre part, la plupart du temps, nous ne pouvons pas éditer les fichiers PDF. Lorsque nous fusionnons plusieurs documents et pages pour former un document complet combiné, il arrive souvent que nous finissions de combiner les pages dans le mauvais ordre. Cet article explique **comment réorganiser les pages PDF par programmation à l'aide de C#**."
tags: ['Rearrange Document', 'Rearrange PDF Pages', 'Rearrange PDF Pages in CSharp']
categories: ['GroupDocs.Merger Product Family']
---



{{< figure align=center src="images/rearrange-pdf-pages-using-csharp-dotnet.jpg" alt="Réorganiser les pages PDF à l'aide de C# .NET">}}


En cette ère numérique, le PDF est l'un des formats de fichiers les plus utilisés et est populaire en raison de sa portabilité. D'autre part, la plupart du temps, nous ne pouvons pas éditer les fichiers PDF. Lorsque nous fusionnons plusieurs documents et pages pour former un document complet combiné, il arrive souvent que nous finissions de combiner les pages dans le mauvais ordre. Cet article explique **comment réorganiser les pages PDF par programmation à l'aide de C#**.

## API .NET pour réorganiser les pages PDF et fusionner des documents

Afin de réorganiser les pages dans les documents, GroupDocs fournit [GroupDocs.Merger pour .NET](https://products.groupdocs.com/merger/net/). L'API permet de supprimer, de fractionner et d'extraire des pages, de modifier l'orientation des pages et de faire pivoter les pages de document dans les applications .NET. Pour les détails et autres fonctionnalités de l'API, vous pouvez consulter la [documentation](https://docs.groupdocs.com/merger/net/).

Vous pouvez télécharger le programme d'installation **DLLs** ou **MSI** à partir de la [section téléchargements](https://downloads.groupdocs.com/merger) ou installer l'API dans votre application .NET via [NuGet](https://www.nuget.org/packages/groupdocs.merger).

```
PM> Install-Package GroupDocs.Merger
```

## Réorganiser les pages PDF à l'aide de C#

Voici les étapes qui réorganisent les pages des documents PDF à l'aide de C#.

* Définissez la position existante et nouvelle de la page dans la classe [MoveOptions](https://apireference.groupdocs.com/merger/net/groupdocs.merger.domain.options/moveoptions).
* Chargez le document PDF à l'aide de la classe [Merger](https://apireference.groupdocs.com/merger/net/groupdocs.merger/merger).
* Utilisez la méthode [MovePage()](https://apireference.groupdocs.com/merger/net/groupdocs.merger/merger/methods/movepage) pour réorganiser selon les options définies.
* Enregistrez le fichier PDF avec le nouvel ordre des pages à l'aide de la méthode [Save()](https://apireference.groupdocs.com/merger/net/groupdocs.merger/merger/methods/save/index).

Le code C# suivant réorganise les pages des documents PDF. Précisément, il déplace la 6ème page du document à la 1ère place.

```
// Réorganiser les pages du document PDF à l'aide de C#
int pageNumber = 6;
int newPageNumber = 1;

MoveOptions moveOptions = new MoveOptions(pageNumber, newPageNumber);
using (Merger merger = new Merger("path\document.pdf"))
{
    merger.MovePage(moveOptions);
    merger.Save("path\rearranged-document.pdf");
}
```

Voici la sortie du code ci-dessus.



{{< figure align=center src="images/Screenshot-1024x454.png" alt="">}}


## Obtenez une licence API gratuite

Vous pouvez [obtenir une licence temporaire gratuite](https://purchase.groupdocs.com/temporary-license) afin d'utiliser l'API sans les limitations d'évaluation.

## Conclusion

Pour conclure, nous avons appris à réorganiser les pages des fichiers PDF à l'aide de C# dans les applications .NET. Nous avons vu l'exemple courant pour changer la position de la page. Vous pouvez essayer de créer une application simple capable d'organiser les fichiers PDF en mélangeant facilement leurs pages.

Pour plus de détails sur l'API, consultez la [documentation](https://docs.groupdocs.com/merger/). Pour toute question, contactez-nous via le [forum](https://forum.groupdocs.com/).

## Voir également

* [Comment réorganiser les pages PDF en Java](https://blog.groupdocs.com/2022/03/10/move-pdf-pages-in-java/)
* [Protéger les fichiers PDF par mot de passe à l'aide de C#](https://blog.groupdocs.com/2021/11/17/lock-unlock-pdf-files-with-password-using-csharp/)
* [Fractionner des fichiers PDF à l'aide de C#](https://blog.groupdocs.com/2021/10/11/split-pdf-files-in-csharp/)
* [Fusionner plusieurs types de fichiers en un seul document à l'aide de C#](https://blog.groupdocs.com/2021/05/04/merge-multiple-file-types-using-csharp/)





