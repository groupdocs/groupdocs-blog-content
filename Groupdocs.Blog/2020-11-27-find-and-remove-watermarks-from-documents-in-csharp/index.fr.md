---
title: "Rechercher et supprimer des filigranes de documents en C#"
date: Fri, 27 Nov 2020 14:21:34 +0000
draft: false
url: /fr/2020/11/27/trouver-et-supprimer-les-filigranes-des-documents-dans-csharp/
author: 'Shoaib Khan'
summary: "Aujourd'hui, nous verrons **comment rechercher et supprimer les filigranes des documents en C#**. Il peut y avoir des filigranes basés sur du texte et des images dans un document. Nous pouvons facilement rechercher et supprimer par programme ces filigranes de nombreux documents pris en charge par PDF, Word, Excel, PowerPoint et Visio."
tags: ['find and remove watermarks in csharp', 'find watermarks in csharp', 'remove watermarks in csharp', 'Watermarking API for .NET']
categories: ['GroupDocs.Watermark Product Family']
---

Aujourd'hui, nous verrons **comment rechercher et supprimer les filigranes des documents en C#**. Il peut y avoir des filigranes basés sur du texte et des images dans un document. Nous pouvons facilement rechercher et supprimer par programme ces filigranes de nombreux documents pris en charge par PDF, Word, Excel, PowerPoint et Visio.

Les sujets suivants seront abordés dans cet article :

* [API .NET pour supprimer les filigranes][1]
* [Rechercher des filigranes dans des documents à l'aide de C#][2]
* [Supprimer les filigranes des documents en C#][3]



{{< figure align=center src="images/find-and-remove-watermarks-using-groupdocs.watermark-1.png" alt="Rechercher et supprimer des filigranes de documents à l'aide de l'API GroupDocs">}}


## API .NET pour la suppression des filigranes {#watermark-removing-api-for-dotnet}



{{< figure align=center src="images/groupdocs-watermark-net.png" alt="API de filigrane pour .NET - GroupDocs">}}


[GroupDocs.Watermark pour .NET][4] est une API de filigrane rapide et efficace qui ne nécessite aucun logiciel supplémentaire. Il permet d'ajouter des filigranes aux documents et aux images de telle manière qu'il serait difficile pour les outils tiers de les supprimer. Il permet également aux développeurs C# de supprimer facilement les filigranes de nombreux formats de fichiers **Microsoft** et **OpenOffice** de **documents de traitement de texte**, **feuilles de calcul**, **présentations**, **dessins Visio* *, et les documents **PDF** dans les applications .NET. Tous les [formats de fichiers pris en charge][5] sont mentionnés dans la [documentation][6].

Maintenant, je vais montrer des exemples qui trouveront et supprimeront des filigranes. Il sera donc préférable de préparer l'environnement à l'avance en suivant l'une des options appropriées :

* [NuGet][7]
*   [Direct Download][8]: MSI installer and DLLs
* **Console du gestionnaire de packages :**

```
PM> Install-Package GroupDocs.Watermark
```

## Rechercher des filigranes dans des documents à l'aide de C # {#find-watermarks-in-documents-using-csharp}

[Watermarker][9], [PossibleWatermarkCollection][10] (la collection de [PossibleWatermark][11] sont les classes de l'API permettant de trouver différents types de filigranes dans des documents avec différents critères de recherche et de les supprimer rapidement. Voici les étapes pour la recherche de base de tous les filigranes dans n'importe quel document fourni à l'aide de C #. Vous pouvez affiner davantage votre recherche de filigranes, comme indiqué plus loin dans cet article.

* Créez l'objet de classe **Watermarker** avec le fichier du document source.
* Appelez la méthode **Search**. Il renverra tous les filigranes possibles du document.
* Parcourez la collection de filigranes pour afficher des données ou effectuer n'importe quelle action sur chaque filigrane.

```
// Trouvez tous les filigranes dans les documents Word, Excel, PowerPoint, Visio et PDF à l'aide de C #
using (Watermarker watermarker = new Watermarker("filepath/documentWithWatermarks.pdf"))
{
    PossibleWatermarkCollection possibleWatermarks = watermarker.Search();
    foreach (PossibleWatermark possibleWatermark in possibleWatermarks)
    {
        if (possibleWatermark.ImageData != null)
        {
            Console.WriteLine(possibleWatermark.ImageData.Length);
        }
        Console.WriteLine(possibleWatermark.Text);
        Console.WriteLine(possibleWatermark.X);
        Console.WriteLine(possibleWatermark.Y);
        Console.WriteLine(possibleWatermark.RotateAngle);
        Console.WriteLine(possibleWatermark.Width);
        Console.WriteLine(possibleWatermark.Height);
    }
}
```

## Supprimer les filigranes des documents en C# {#remove-watermarks-from-documents-in-csharp}

De tous les filigranes recherchés, nous pouvons supprimer n'importe quel filigrane ou tous les filigranes à la fois. L'essentiel ici, que vous ayez réussi à trouver le ou les filigranes que vous souhaitez supprimer ou non. Que se passe-t-il s'il existe de nombreux types de filigranes différents dans un document ? L'API offre diverses options pour affiner votre recherche de filigranes. Le code suivant supprime le filigrane d'un document PDF en spécifiant l'index de la collection à l'aide de C#.

```
// Supprimez les filigranes des PDF et autres documents à l'aide de C #
using (Watermarker watermarker = new Watermarker("filepath/documentWithWatermarks.pdf"))
{
    PossibleWatermarkCollection possibleWatermarks = watermarker.Search();

    // Remove watermark at the specified index from the document.
    possibleWatermarks.RemoveAt(0);

    // Remove specified watermark from the document.
    possibleWatermarks.Remove(possibleWatermarks[0]);

    watermarker.Save("filepath/noWatermarks.pdf");
}
```

## Plus de critères de recherche pour les filigranes

Il existe de nombreuses autres façons de trouver des filigranes avec certains critères. Après la recherche sélective, nous pouvons supprimer le ou les filigranes de la collection en utilisant la méthode **Remove**, **RemoveAt** ou **Clear** en conséquence. Voici quelques-unes des façons de trouver des filigranes à partir des documents fournis :

* Rechercher et supprimer des filigranes avec un texte spécifique
* Rechercher des filigranes avec RegEx (Regular Expression) et supprimer
* Rechercher un filigrane avec une mise en forme de texte spécifiée
* Rechercher et supprimer les filigranes de liens hypertexte

### Rechercher et supprimer des filigranes avec un texte spécifique

Vous pouvez rechercher des filigranes de texte en spécifiant la chaîne exacte à l'aide du code C# suivant :

```
 // Find possible watermarks containing the specified text
TextSearchCriteria textSearchCriterion = new TextSearchCriteria("© 2020");
PossibleWatermarkCollection possibleWatermarks = watermarker.Search(textSearchCriterion);
```

### Rechercher des filigranes avec RegEx et supprimer

S'il existe un motif dans le texte du filigrane, vous pouvez fournir une expression régulière (RegEx) pour rechercher ces filigranes et les supprimer ultérieurement en utilisant le code C# suivant. Ce code récupérera tous les filigranes avec ©YYYY.

```
// Search Watermarks by Regular Expression
Regex regex = new Regex(@"^© \\d{4}$");
TextSearchCriteria textSearchCriterion = new TextSearchCriteria(regex);
PossibleWatermarkCollection possibleWatermarks = watermarker.Search(textSearchCriterion);
```

### Rechercher et supprimer des filigranes avec un formatage de texte spécifique

Vous pouvez également trouver les filigranes ayant une mise en forme de texte spécifique comme le nom de la police, la taille de police min/max, gras/italique/souligné, etc.

```
TextFormattingSearchCriteria criterion = new TextFormattingSearchCriteria()
{
    FontName = "Arial",
    MinFontSize = 19,
    MaxFontSize = 42,
    FontBold = true
};
PossibleWatermarkCollection watermarks = watermarker.Search(criterion);
watermarks.Clear();
```

### Rechercher et supprimer des filigranes de lien hypertexte

Vous pouvez utiliser RegEx pour trouver des filigranes de texte ayant des hyperliens dans le contenu. Plus tard, vous pouvez vérifier dans la collection s'il existe des filigranes de lien hypertexte dans le résultat de la recherche. Ceux-ci peuvent être supprimés par l'une des méthodes de suppression. Le code C# suivant supprime tous les filigranes avec des liens hypertexte.

```
PossibleWatermarkCollection watermarks = watermarker.Search(new TextSearchCriteria(new Regex(@"anyurl\\.com")));
for (int i = watermarks.Count - 1; i >= 0; i--)
{
    // Is watermark the hyperlink?
    if (watermarks\[i\] is HyperlinkPossibleWatermark)
    {
        watermarks.RemoveAt(i);
    }
}
```

Il existe de nombreuses autres façons d'affiner votre [recherche de filigranes][12]. Vous pouvez visiter [documentation][13] pour plus de détails. Pour toute question, visitez le [forum][14].

## Conclusion

Je pense que vous serez désormais plus confiant pour rechercher et supprimer les filigranes de texte ainsi que les filigranes d'image des documents Word, des feuilles de calcul Excel, des présentations Powerpoint, des documents PDF et des dessins Visio à l'aide de C# dans vos applications .NET.

## Voir également

* [Ajouter un filigrane aux images ou aux images dans les documents à l'aide de C #][15]
* [Ajouter un filigrane aux images en Java][16]
* [Rechercher et supprimer des filigranes de documents en Java][17]







[1]: #watermark-removing-api-for-dotnet
[2]: #find-watermarks-in-documents-using-csharp
[3]: #remove-watermarks-from-documents-in-csharp
[4]: https://products.groupdocs.com/watermark/net
[5]: https://docs.groupdocs.com/watermark/net/supported-document-formats/
[6]: https://docs.groupdocs.com/watermark/net/
[7]: https://www.nuget.org/packages/groupdocs.watermark
[8]: https://downloads.groupdocs.com/watermark/net
[9]: https://apireference.groupdocs.com/watermark/net/groupdocs.watermark/watermarker
[10]: https://apireference.groupdocs.com/watermark/net/groupdocs.watermark.search/possiblewatermarkcollection
[11]: https://apireference.groupdocs.com/watermark/net/groupdocs.watermark.search/possiblewatermark)
[12]: https://docs.groupdocs.com/watermark/net/searching-watermarks/
[13]: https://docs.groupdocs.com/watermark/net/
[14]: https://forum.groupdocs.com/c/watermark
[15]: https://blog.groupdocs.com/2019/10/21/add-watermark-to-images-using-csharp-dotnet-api/
[16]: https://blog.groupdocs.com/2020/09/15/add-watermark-to-images-in-java/
[17]: https://blog.groupdocs.com/2019/10/10/find-and-remove-watermarks-from-documents-in-java/


