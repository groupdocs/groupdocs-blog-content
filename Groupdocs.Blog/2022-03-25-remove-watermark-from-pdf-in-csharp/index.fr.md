---
title: "Supprimer les filigranes des documents PDF en C#"
date: Fri, 25 Mar 2022 19:29:00 +0000
draft: false
url: /fr/2022/03/25/remove-watermark-from-pdf-in-csharp/
author: 'Shoaib Khan'
summary: "Les filigranes sont normalement utilisés pour éviter toute utilisation illégale de documents confidentiels. Lorsque la confidentialité n'est plus nécessaire, vous feriez mieux de supprimer les filigranes de ces documents. Il peut y avoir des filigranes basés sur du texte et des images dans un document. Aujourd'hui, nous verrons **comment supprimer les filigranes des documents PDF à l'aide de C#**."
tags: ['delete watermark', 'how to remove watermark in c sharp', 'remove watermark', 'remove watermark from pdf', 'remove watermark using csharp', 'Watermark Remover', 'watermark remover application']
categories: ['GroupDocs.Watermark Product Family']
---

Les filigranes sont normalement utilisés pour éviter toute utilisation illégale de documents confidentiels. Lorsque la confidentialité n'est plus nécessaire, vous feriez mieux de supprimer les filigranes de ces documents. Il peut y avoir des filigranes basés sur du texte et des images dans un document. Aujourd'hui, nous verrons **comment supprimer les filigranes des documents PDF à l'aide de C#**.



{{< figure align=center src="images/removing-watermark-from-pdf.jpg" alt="Supprimer le filigrane des documents PDF">}}


## API .NET pour supprimer les filigranes PDF

[GroupDocs.Watermark](https://products.groupdocs.com/watermark) présente l'API .NET pour traiter les filigranes dans les documents et les images de différents [formats de fichiers](https://docs.groupdocs.com/conversion/net/supported-document-formats/). Si vous créez une _application de suppression de filigrane_, elle vous fournit des moyens utiles pour :

* Supprimer tous les filigranes du PDF
* Supprimer les filigranes avec un formatage de texte particulier
* Supprimer les filigranes de lien hypertexte

Découvrons comment un développeur C# peut supprimer les filigranes d'un PDF à l'aide de l'API [GroupDocs.Watermark pour .NET](https://products.groupdocs.com/watermark/net/) de différentes manières.

## Supprimer tous les filigranes du document PDF à l'aide de C# {#RemovingFoundWatermarks-RemoveWatermark}

L'API vous donne le pouvoir de trouver facilement puis de supprimer un filigrane particulier et tous les filigranes d'un document. Le code suivant supprime tous les filigranes d'un document PDF à l'aide de C#.

* Chargez le fichier PDF à l'aide de [Watermarker](https://apireference.groupdocs.com/watermark/net/groupdocs.watermark/watermarker).
* Récupérez tous les [filigranes possibles](https://apireference.groupdocs.com/watermark/net/groupdocs.watermark.search/possiblewatermarkcollection) en tant que collection à l'aide de la recherche.
* Parcourez toute la collection et supprimez chaque filigrane ou celui qui répond à vos critères.
* Enregistrez le PDF mis à jour sans plus de filigranes dessus.

Le code C# suivant supprime tous les filigranes d'un document PDF.

```
// Supprimez les filigranes des PDF et autres documents à l'aide de C#
using (Watermarker watermarker = new Watermarker("filepath/documentWithWatermarks.pdf"))
{
    PossibleWatermarkCollection possibleWatermarks = watermarker.Search();

    // Remove every watermark by mentioning the index within document.
    for (int i = 0; i < possibleWatermarks.Count; i++)
    {
        possibleWatermarks.RemoveAt(0);
    }
    watermarker.Save("filepath/no-watermarks.pdf");
}
```

## Supprimer le filigrane du PDF avec un formatage de texte particulier à l'aide de C# {#RemovingFoundWatermarks-RemoveWatermarkwithParticularTextFormatting}

À l'aide de l'API, vous pouvez rechercher et supprimer les filigranes sur la base du formatage du texte. Vous pouvez fournir un critère de recherche contenant le nom, la police, la taille, la couleur, etc. et l'API trouvera les filigranes avec les propriétés correspondantes. L'extrait de code suivant montre comment rechercher et supprimer des filigranes dans un fichier PDF avec une mise en forme de texte spécifique à l'aide de C#.

* Chargez le fichier PDF à l'aide de [Watermarker](https://apireference.groupdocs.com/watermark/net/groupdocs.watermark/watermarker).
* Définissez le critère de recherche à l'aide de [TextFormattingSearchCriteria](https://apireference.groupdocs.com/watermark/net/groupdocs.watermark.search.searchcriteria/textformattingsearchcriteria).
* Mentionnez toutes les propriétés de formatage requises.
* Effectuez une **Recherche()** et obtenez tous les [filigranes possibles](https://apireference.groupdocs.com/watermark/net/groupdocs.watermark.search/possiblewatermarkcollection) en tant que collection en fournissant les critères définis.
* Supprimez tous les filigranes recherchés à l'aide de la méthode **Clear()**.
* Enregistrez le PDF mis à jour sans filigrane avec les propriétés définies.

Le code C# suivant supprime les filigranes dans un document PDF ayant la mise en forme de texte spécifiée.

```
// Supprimer les filigranes avec une mise en forme de texte spécifique d'un PDF à l'aide de C#
using (Watermarker watermarker = new Watermarker("path/Watermarks.pdf"))
{
    TextFormattingSearchCriteria criteria = new TextFormattingSearchCriteria();
    criteria.ForegroundColorRange = new ColorRange();
    criteria.ForegroundColorRange.MinHue = -5;
    criteria.ForegroundColorRange.MaxHue = 10;
    criteria.ForegroundColorRange.MinBrightness = 0.01f;
    criteria.ForegroundColorRange.MaxBrightness = 0.99f;
    criteria.BackgroundColorRange = new ColorRange();
    criteria.BackgroundColorRange.IsEmpty = true;
    criteria.FontName = "Arial";
    criteria.MinFontSize = 19;
    criteria.MaxFontSize = 42;
    criteria.FontBold = true;

    PossibleWatermarkCollection possibleWatermarks = watermarker.Search(criteria);
    possibleWatermarks.Clear();

    watermarker.Save("path/removed-watermarks.pdf");
}
```

## Suppresseur de filigrane de lien hypertexte dans .NET

L'API .NET de filigrane de document vous permet de rechercher et de supprimer des liens hypertexte dans un document de n'importe quel format de document pris en charge. Les étapes suivantes permettent de supprimer les filigranes de lien hypertexte d'un document PDF dans l'application .NET à l'aide de C#.

* Chargez le fichier PDF à l'aide de [Watermarker](https://apireference.groupdocs.com/watermark/net/groupdocs.watermark/watermarker).
* Récupérez tous les [filigranes possibles](https://apireference.groupdocs.com/watermark/net/groupdocs.watermark.search/possiblewatermarkcollection) en tant que collection à l'aide de la recherche.
* Parcourez toute la collection et supprimez chaque filigrane ou celui qui répond à vos critères.
* Enregistrez le PDF mis à jour sans plus de filigranes dessus.

L'exemple de code C# suivant montre comment rechercher et supprimer des filigranes de lien hypertexte avec une URL particulière à partir d'un document PDF.

```
// Supprimer les filigranes de lien hypertexte du PDF à l'aide de C#
using (Watermarker watermarker = new Watermarker("path/Hyperlink-Watermarks.pdf"))
{
    PossibleWatermarkCollection watermarks = watermarker.Search(new TextSearchCriteria(new Regex(@"someurl\.com")));
    for (int i = 0 ; i < watermarks.Count; i++)
    {
        if (watermarks[i] is HyperlinkPossibleWatermark)
        {
            Console.WriteLine("Removing: " + watermarks[i].Text);
            watermarks.RemoveAt(i);
        }
    }
    watermarker.Save("path/no-hyperlink-watermarks.pdf");
}
```

## Conclusion

Pour conclure, nous avons appris aujourd'hui à supprimer différents filigranes des documents PDF à l'aide de C#. Je pense que vous serez désormais plus confiant pour créer votre propre application .NET pour rechercher et supprimer les filigranes de texte ainsi que les filigranes d'image des documents PDF. De plus, vous pouvez ajouter des fonctionnalités de suppression des filigranes avec un formatage spécifié et des filigranes de lien hypertexte.

En outre, vous pouvez en savoir plus sur [GroupDocs.Watermark pour .NET](https://products.groupdocs.com/watermark/net/) à partir de sa [documentation](https://docs.groupdocs.com/watermark/) . Pour toute question, contactez-nous via le [forum](https://forum.groupdocs.com/).

## Voir également

* [Documents protégés par mot de passe en filigrane utilisant C#](https://blog.groupdocs.com/2021/12/25/watermark-password-protected-documents-using-csharp/)
* [Fichiers PDF en filigrane avec C#](https://blog.groupdocs.com/2021/07/27/watermark-pdf-files-using-csharp/)
* [Ajouter un filigrane aux images à l'aide de C#](https://blog.groupdocs.com/2020/12/20/add-watermark-to-images-using-csharp-dotnet/)
* [Rechercher et supprimer des filigranes de documents en Java](https://blog.groupdocs.com/2020/11/30/find-and-remove-watermarks-from-documents-in-java/)





