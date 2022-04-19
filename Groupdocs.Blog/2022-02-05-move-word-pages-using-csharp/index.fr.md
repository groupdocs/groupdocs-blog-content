---
title: "'Comment réorganiser les pages dans Word à l'aide de C#'"
date: Sat, 05 Feb 2022 08:19:00 +0000
draft: false
url: /fr/2022/02/05/move-word-pages-using-csharp/
author: 'Shoaib Khan'
summary: "Dans le monde numérique, les documents de traitement de texte sont l'un des formats de fichiers les plus couramment utilisés pour créer et modifier des documents. Lorsqu'il s'agit de documents volumineux, il n'est vraiment pas facile de déplacer des pages sans perdre la mise en forme. La perte de formatage se produit souvent lorsque nous essayons de [combiner plusieurs documents de différents types](https://blog.groupdocs.com/2021/05/04/merge-multiple-file-types-using-csharp/) ou nous avons simplement [ fusionner le même type de fichiers](https://blog.groupdocs.com/2020/08/19/merge-pdf-word-excel-ppt-files-in-csharp/) en un seul document. Afin de réorganiser les pages, cet article explique, **comment déplacer par programmation des pages dans des documents Word (DOC/DOCX) à l'aide de C#**."
tags: ['Move Pages in CSharp', 'Move Pages in DOC/DOCX', 'Rearrange Document', 'Rearrange Document Pages in CSharp', 'Rearrange pages in CSharp', 'Rearrange pages in Word']
categories: ['GroupDocs.Merger Product Family']
---



{{< figure align=center src="images/rearrange-word-pages-using-csharp-dotnet.jpg" alt="Réorganiser les pages Word à l'aide de C# .NET">}}


Dans le monde numérique, les documents de traitement de texte sont l'un des formats de fichiers les plus couramment utilisés pour créer et modifier des documents. Lorsqu'il s'agit de documents volumineux, il n'est vraiment pas facile de déplacer des pages sans perdre la mise en forme. La perte de formatage se produit souvent lorsque nous essayons de [combiner plusieurs documents de différents types](https://blog.groupdocs.com/2021/05/04/merge-multiple-file-types-using-csharp/) ou nous avons simplement [ fusionner le même type de fichiers](https://blog.groupdocs.com/2020/08/19/merge-pdf-word-excel-ppt-files-in-csharp/) en un seul document. Afin de réorganiser les pages, cet article explique, **comment déplacer par programmation des pages dans des documents Word (DOC/DOCX) à l'aide de C#**.

## API .NET pour déplacer des pages de documents Word

**GroupDocs.Merger** fournit l'API .NET qui permet de déplacer, de supprimer, de diviser des documents et d'extraire des pages, de modifier l'orientation des pages et de faire pivoter les pages de document dans les applications .NET. Aujourd'hui, nous allons utiliser cette API pour déplacer des pages de fichiers DOC/DOCX à l'aide de C#. Pour les détails et autres fonctionnalités de l'API, vous pouvez consulter la [documentation](https://docs.groupdocs.com/merger/).

Vous pouvez télécharger le programme d'installation **DLLs** ou **MSI** à partir de la [section téléchargements](https://downloads.groupdocs.com/merger) ou installer l'API dans votre application .NET via [NuGet](https://www.nuget.org/packages/groupdocs.merger).

```
PM> Install-Package GroupDocs.Merger
```

## Déplacer des pages dans des documents Word à l'aide de C#

Le déplacement des pages est simple. Commandez simplement à cette page particulière de se déplacer vers sa nouvelle position. Voici les étapes qui réorganisent les pages d'un document Word à l'aide de C#.

* Définissez le numéro de page de la page cible et sa nouvelle position à l'aide de la classe [MoveOptions](https://apireference.groupdocs.com/merger/net/groupdocs.merger.domain.options/moveoptions).
* Chargez le document DOC/DOCX à l'aide de la classe [Merger](https://apireference.groupdocs.com/merger/net/groupdocs.merger/merger).
* Utilisez la méthode [MovePage()](https://apireference.groupdocs.com/merger/net/groupdocs.merger/merger/methods/movepage) pour déplacer la page.
* Enregistrez le document réorganisé à l'aide de la méthode [Save()](https://apireference.groupdocs.com/merger/net/groupdocs.merger/merger/methods/save/index).

Le code C# suivant permet de réorganiser les pages d'un document Word. Précisément, il déplace la 7e page d'un document DOCX à la 2e place.

```
// Réorganiser les pages des documents de traitement de texte (DOC/DOCX) à l'aide de C#
int pageNumber = 7;
int newPageNumber = 2;

MoveOptions moveOptions = new MoveOptions(pageNumber, newPageNumber);
using (Merger merger = new Merger("path\document.docx"))
{
    merger.MovePage(moveOptions);
    merger.Save("path\rearranged-document.docx");
}
```

## Obtenez une licence API gratuite

Vous pouvez [obtenir une licence temporaire gratuite](https://purchase.groupdocs.com/temporary-license) afin d'utiliser l'API sans les limitations d'évaluation.

## Conclusion

Pour conclure, nous avons appris à modifier l'ordre des pages dans les documents Word à l'aide de C# dans les applications .NET. Nous avons vu l'exemple de code source qui a changé la position de la page dans un fichier DOCX. Vous pouvez créer votre propre application qui peut réorganiser les pages Word en ligne en mélangeant facilement les pages.

Pour plus de détails sur l'API, consultez la [documentation](https://docs.groupdocs.com/merger/net). Pour toute question, contactez-nous via le [forum](https://forum.groupdocs.com/).

## Voir également

* [Comparer des documents Word](https://blog.groupdocs.com/2021/12/01/compare-word-documents-using-csharp/)
* [Modifier des documents Word](https://blog.groupdocs.com/2021/03/26/edit-word-documents-in-csharp/)
* [Protéger/Déprotéger les fichiers Word avec un mot de passe](https://blog.groupdocs.com/2021/11/27/password-protect-word-documents-using-csharp/)
* [Afficher les documents Word en tant que page HTML réactive](https://blog.groupdocs.com/2021/08/28/view-word-documents-as-html-responsive-page-using-csharp/)
* [Ajouter ou supprimer des annotations ou des fichiers Word de balisage](https://blog.groupdocs.com/2021/06/23/annotate-word-documents-using-csharp/)





