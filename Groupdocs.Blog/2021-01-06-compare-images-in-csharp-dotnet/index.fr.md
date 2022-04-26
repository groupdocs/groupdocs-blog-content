---
title: "Comparaison d'images en C# pour repérer les différences"
date: Wed, 06 Jan 2021 17:52:00 +0000
draft: false
url: /fr/2021/01/06/comparer-images-dans-csharp-dotnet/
aliases:
- /2019/09/12/comparer-deux-images-en-c-.net-et-java/
- /2019/09/12/comparer-deux-images-dans-csharp-.net-et-java/
- /2019/09/12/comparer-deux-images-dans-csharp-dotnet-et-java/
author: 'Shoaib Khan'
summary: "Que vous souhaitiez créer une application avec la fonctionnalité Spot the Difference ou comparer deux images dans l'une de vos applications de traitement d'image basées sur .NET, vous êtes au bon endroit. Après cet article, vous pouvez facilement comparer JPG, PNG, BMP ou des images avec d'autres formats de fichiers. Sans perdre de temps, comparons des images en C# à l'aide de l'[API .NET pour la conversion de documents et d'images][1]."
tags: ['compare images in csharp', 'compare jpg or png in csharp', 'Image Comparison', 'image comparison in csharp']
categories: ['GroupDocs.Comparison Product Family']
---

Que vous souhaitiez créer une application avec la fonctionnalité Spot the Difference ou comparer deux images par programmation dans l'une de vos applications de traitement d'images basées sur .NET, vous êtes au bon endroit. Après cet article, vous pouvez facilement comparer JPG, PNG, BMP ou des images avec d'autres formats de fichiers. Sans perdre de temps, comparons des images en C# à l'aide de l'[API .NET pour la comparaison de documents et d'images][2].



{{< figure align=center src="images/compare-images-to-find-differences-in-dotnet.jpg" alt="Comparer les images pour les différences à l'aide de .NET">}}


## API de comparaison d'images .NET

J'utiliserai l'API [GroupDocs.Comparison pour .NET][3] pour comparer les images dans cet article. Cette API prend en charge la comparaison d'images **JPG, PNG, BMP, DICOM, DCM, DjVu** avec de nombreux autres [formats de fichiers pris en charge][4].

Vous pouvez télécharger les DLL ou le programme d'installation MSI à partir de la [section des téléchargements][5] ou installer l'API dans votre application .NET via [NuGet][6].

```
PM> Install-Package GroupDocs.Comparison
```

## Comparer des images en C # pour mettre en évidence les différences

Comparer deux images en C # est trop facile avec GroupDocs.Comparison dans l'application .NET. Les étapes suivantes expliquent comment nous pouvons comparer deux images JPG, PNG, BMP ou toute autre image. Il détecte avec succès les changements et les met en évidence dans l'image de sortie/résultante.

* Définissez la première image à l'aide de la classe [Comparer][7].
* Ajoutez la deuxième image en utilisant la méthode [Add][8] de l'objet Comparer.
* Appelez la méthode [Comparer][9] pour comparer les deux images et enregistrer l'image résultante qui met en évidence les différences entre les deux images.

Le code ci-dessous montre comment comparer deux images en C#. Par exemple, il compare deux images JPG et enregistre la sortie avec les différences.

```
// Comparez les formats d'image JPG, PNG, GIF et BMP à l'aide de l'API de comparaison d'images .NET en C#
using (Comparer comparer = new Comparer("filepath/soureImage.jpg"))
{
    CompareOptions options = new CompareOptions();
    options.GenerateSummaryPage = false; // To get the difference summary, set it 'true'

    comparer.Add("filepath/targetImage.jpg");
    comparer.Compare("filepath/comparisonResultImage.jpg", options);
}
```

Les images présentées au début de l'article sont utilisées dans ce code. Les images sur la gauche sont comparées et la sortie est affichée sur le côté droit qui met en évidence les différences.

## Conclusion

Dans cet article, nous avons appris à comparer deux images en C# à l'aide de l'API de comparaison d'images. Vous pouvez maintenant créer votre propre application de comparaison d'images qui peut comparer des images et mettre en évidence les différences trouvées pour ses utilisateurs.

Pour avoir une idée complète des fonctionnalités de l'API, vous pouvez parcourir la [documentation][10]. Vous pouvez également contacter l'[équipe d'assistance gratuite][11] ou l'[équipe de conseil gratuite][12] qui écrit même du code pour vous aider à comprendre l'utilisation des API GroupDocs selon vos besoins.

## Voir également

* [Comparer des images en Java pour trouver des différences][13]
* [Comparer des fichiers Excel, Word, PDF ou PowerPoint en C#][14]







[1]: https://products.groupdocs.com/comparison/net
[2]: https://products.groupdocs.com/comparison/net
[3]: https://products.groupdocs.com/comparison/net
[4]: https://docs.groupdocs.com/comparison/net/supported-document-formats/
[5]: https://downloads.groupdocs.com/comparison/net
[6]: https://www.nuget.org/packages/groupdocs.comparison
[7]: https://apireference.groupdocs.com/comparison/net/groupdocs.comparison/comparer
[8]: https://apireference.groupdocs.com/comparison/net/groupdocs.comparison/comparer/methods/add/index
[9]: https://apireference.groupdocs.com/comparison/net/groupdocs.comparison/comparer/methods/compare/index
[10]: https://docs.groupdocs.com/comparison/net/
[11]: https://forum.groupdocs.com/c/comparison
[12]: https://groupdocs-free-consulting.github.io/
[13]: https://blog.groupdocs.com/2021/06/16/compare-images-in-java/
[14]: https://blog.groupdocs.com/2020/03/10/compare-excel-word-pdf-files-in-csharp/


