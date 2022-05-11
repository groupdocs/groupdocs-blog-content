---
title: "Supprimer des pages d'un PDF à l'aide de C# | Pair, impair, liste et plage"
seoTitle: "Supprimer des pages d'un PDF à l'aide de C# | Pair, impair, liste et plage"
date: Tue, 19 Apr 2022 11:00:00 +0000
draft: false
description: "Supprimez n'importe quel ensemble de pages des fichiers PDF à l'aide de C#. Supprimer la liste des pages, toute plage donnée, les pages paires ou impaires des fichiers PDF dans l'application .NET."
url: /fr/2022/04/19/delete-pages-from-pdf-in-csharp/
author: 'Shoaib Khan'
summary: "Nous avons souvent besoin de supprimer les pages indésirables, obsolètes et hautement confidentielles des documents lors du partage ou de la finalisation des brouillons. Dans cet article, nous allons apprendre **comment supprimer par programmation de telles pages du document PDF à l'aide de C#**. Les exigences peuvent parfois différer, nous discuterons donc de différentes manières de supprimer les différents ensembles de pages dans le document PDF."
tags: ['delete pages', 'delete pages in csharp', 'remove pages', 'remove pages in csharp', 'delete pages from pdf in csharp', 'delete pages in csharp']
categories: ['GroupDocs.Merger Product Family']
---

Nous avons souvent besoin de supprimer les pages indésirables, obsolètes et hautement confidentielles des documents lors du partage ou de la finalisation des brouillons. Dans cet article, nous allons apprendre **comment supprimer par programmation de telles pages du document PDF à l'aide de C#**. Les exigences peuvent parfois différer, nous discuterons donc de différentes manières de supprimer les différents ensembles de pages dans le document PDF.

Les sujets suivants sont abordés ci-dessous :

- [API .NET de suppression de page PDF] (#pdf-page-removal-dotnet-api)
- [Supprimer la sélection/la liste des pages] (#remove-pdf-pages-list-in-csharp)
- [Supprimer la plage de pages] (#remove-pdf-pages-range-in-csharp)
- [Supprimer la plage de pages paires ou impaires] (#remove-even-odd-pdf-pages-in-csharp)

## API .NET pour supprimer des pages d'un PDF {#pdf-page-removal-dotnet-api}

GroupDocs.Merger présente l'API .NET qui permet de supprimer par programmation des pages du document PDF. De plus, il permet aux applications .NET de modifier l'orientation des pages, de déplacer des pages, de diviser des documents, d'extraire et de faire pivoter des pages de document. Nous utiliserons ce [GroupDocs.Merger pour .NET][1] pour supprimer des pages sélectives de fichiers PDF à l'aide de C#. Pour les détails et autres fonctionnalités de l'API, vous pouvez consulter la [documentation][2].

Vous pouvez télécharger les DLL ou le programme d'installation MSI à partir de la [section des téléchargements][3] ou installer l'API dans votre application .NET via [NuGet][4].

```
PM> Install-Package GroupDocs.Merger
```

## Supprimer les pages sélectionnées du PDF à l'aide de C# {#remove-pdf-pages-list-in-csharp}

Fournissez simplement la liste des pages du document PDF chargé à supprimer. Les étapes ci-dessous permettent de supprimer la liste de pages sélectives fournie d'un document PDF à l'aide de C#.

- Initialiser la classe [RemoveOptions][5] avec la **liste des numéros de page** à supprimer.
- Instancier l'objet [Merger][6] avec le chemin ou le flux du document source.
- Appelez la méthode RemovePages() pour supprimer les pages listées.
- Appelez la méthode Save() appropriée pour enregistrer le document résultant.

L'exemple de code C# suivant supprime les 3e et 5e pages sélectionnées du document PDF.

```
// Supprimer des pages sélectives du PDF en C#
RemoveOptions removeOptions = new RemoveOptions(new int[] { 3, 5 });

using (Merger merger = new Merger("path/document-pdf"))
{
    merger.RemovePages(removeOptions);
    merger.Save("path/selected-pages-removed.pdf");
}
```

## Supprimer la plage de pages du PDF à l'aide de C # {#remove-pdf-pages-range-in-csharp}

De même, vous pouvez supprimer n'importe quelle plage de pages dans le document PDF. Les étapes suivantes permettent de supprimer une séquence de pages dans la plage fournie à l'aide de C#.

- Initialiser [RemoveOptions][5].
- Fournissez la **plage de pages** en définissant le numéro de page de **début** et de **fin**.
- Instancier l'objet [Merger][6] avec le chemin ou le flux du document source.
- Appelez la méthode RemovePages() avec la plage.
- Appelez la méthode Save() appropriée pour enregistrer le document résultant.

L'exemple de code C# suivant supprime toutes les pages du document PDF dans la plage fournie, c'est-à-dire 2 à 4.

```
// Supprimer la plage de pages sélectionnée du PDF en C #
RemoveOptions removeOptions = new RemoveOptions(2, 4);

using (Merger merger = new Merger("path/document-pdf"))
{
    merger.RemovePages(removeOptions);
    merger.Save("path/pages-range-removed.pdf");
}
```

## Supprimer les pages paires ou impaires du PDF à l'aide de C # {#remove-even-odd-pdf-pages-in-csharp}

De même, vous pouvez supprimer toutes les pages paires ou impaires du document. Les étapes suivantes montrent comment supprimer les pages paires ou impaires du fichier PDF dans la plage donnée à l'aide de C#.

- Initialiser la classe [RemoveOptions][5] avec la plage de pages.
- Réglez le mode sur **pair** ou **impair**.
- Instancier l'objet [Merger][6] avec le chemin ou le flux du document source.
- Appelez la méthode RemovePages() avec les options de suppression.
- Appelez la méthode Save() appropriée pour enregistrer le document résultant.

L'exemple de code C# suivant supprime toutes les pages paires du document PDF dans la plage fournie, c'est-à-dire 1-6.

```
// Supprimez toutes les pages paires du PDF dans la plage donnée à l'aide de C #
RemoveOptions removeOptions = new RemoveOptions(1, 6 ,RangeMode.EvenPages);

using (Merger merger = new Merger("path/document-pdf"))
{
    merger.RemovePages(removeOptions);
    merger.Save("path/even-pages-removed.pdf");
}
```

L'extrait de code C# suivant supprime toutes les pages impaires de l'ensemble du document PDF.

```
// Supprimez toutes les pages impaires du PDF dans la plage donnée à l'aide de C #
RemoveOptions removeOptions = new RemoveOptions(1, 6 ,RangeMode.OddPages);

using (Merger merger = new Merger("path/document-pdf"))
{
    merger.RemovePages(removeOptions);
    merger.Save("path/odd-pages-removed.pdf");
}
```

## Obtenez une licence API gratuite

Vous pouvez [obtenir une licence temporaire gratuite][7] afin d'utiliser l'API sans les limitations d'évaluation.

## Conclusion

Pour résumer, nous venons d'apprendre à supprimer des pages d'un document PDF à l'aide de C # dans les applications .NET. Plus précisément, nous avons vu comment supprimer des pages en fournissant des numéros de page et des plages de pages. Enfin, nous avons vu comment supprimer les pages paires ou impaires de n'importe quel document PDF. Vous pouvez essayer de créer votre propre application pour éliminer toute variation des pages sélectionnées à partir des fichiers PDF.

Pour plus de détails sur l'API, consultez la documentation. Pour toute question, contactez-nous via le [forum][8].

## Voir également
- [Supprimer les filigranes des documents PDF en C #][9]
- [Convertir un PDF en niveaux de gris à l'aide de C#][10]
- [Comment réorganiser les pages PDF à l'aide de C #][11]
- [Rechercher et remplacer du texte dans un PDF à l'aide de C#][12]
- [Verrouiller et déverrouiller les fichiers PDF avec mot de passe en utilisant C #][13]

[1]: https://products.groupdocs.com/merger/net
[2]: https://docs.groupdocs.com/merger/net/
[3]: https://downloads.groupdocs.com/merger/net
[4]: https://www.nuget.org/packages/groupdocs.merger/
[5]: https://apireference.groupdocs.com/merger/net/groupdocs.merger.domain.options/removeoptions
[6]: https://apireference.groupdocs.com/merger/net/groupdocs.merger/merger
[7]: https://purchase.groupdocs.com/temporary-license
[8]: https://forum.groupdocs.com/
[9]: https://blog.groupdocs.com/2022/03/25/remove-watermark-from-pdf-in-csharp/
[10]: https://blog.groupdocs.com/2022/03/16/convert-pdf-to-grayscale-jpg-png-images-in-csharp/
[11]: https://blog.groupdocs.com/2022/02/22/move-pdf-pages-using-csharp/
[12]: https://blog.groupdocs.com/2022/02/19/find-and-replace-text-in-pdf-using-csharp/
[13]: https://blog.groupdocs.com/2021/11/17/lock-unlock-pdf-files-with-password-using-csharp/

