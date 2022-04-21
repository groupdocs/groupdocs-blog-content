---
title: "Fusionner plusieurs types de fichiers dans un seul document à l'aide de C #"
date: Tue, 04 May 2021 20:10:39 +0000
draft: false
url: /fr/2021/05/04/merge-multiple-file-types-using-csharp/
author: 'Shoaib Khan'
summary: 'To combine the data that is present in multiple documents, and sometimes in documents of different file types, there comes the need to merge all your documents or the portion of the documents into one. In this article, you will learn, how to merge multiple documents of either the same or different file types in one file using C#.

Voici les sujets abordés dans cet article :

* API .NET - Fusionner plusieurs types de documents
* Fusionner des fichiers PDF, Word, Excel en un seul PDF
* Fusionner des pages sélectives de plusieurs fichiers en un seul fichier

[Continuer la lecture...][1]'
tags: ['Merge Documents in CSharp', 'Merge Files in CSharp', 'Merge multiple file types in CSharp', 'merge two or more files']
categories: ['GroupDocs.Merger Product Family']
---

Pour combiner les données présentes dans plusieurs documents, et parfois dans des documents de différents types de fichiers, il est nécessaire de fusionner tous vos documents ou une partie des documents en un seul. Dans cet article, vous apprendrez comment fusionner par programmation plusieurs documents de types de fichiers identiques ou différents dans un seul fichier à l'aide de C#.



{{< figure align=center src="images/merged-pdf-word-excel-files-to-pdf-in-csharp.jpg" alt="Fusion de présentations PDF Word Excel en un seul PDF en C#">}}


Voici les sujets abordés ci-dessous :

* [API .NET - Fusionner plusieurs types de documents][2]
* [Fusionner des fichiers PDF, Word, Excel en un seul PDF][3]
* [Fusionner des pages sélectives de plusieurs fichiers en un seul fichier][4]

## API .NET pour fusionner plusieurs types de documents {#dotnet-api-to-merge-multiple-file-types}

Aujourd'hui, j'utiliserai GroupDocs.Merger pour .NET pour combiner des documents de différents formats de fichiers en un seul fichier. L'API .NET permet de joindre divers documents de formats identiques ou différents dans un seul fichier. De plus, il permet aux documents de diviser, de rogner des documents et d'échanger, de déplacer, de supprimer, de faire pivoter ou d'organiser des pages. De plus, il prend en charge la définition ou la suppression de mots de passe pour gérer la sécurité des [formats de document pris en charge][5].

Certains des types de documents pris en charge par l'API incluent ; documents de traitement de texte, feuilles de calcul, présentations, HTML, PDF, livres électroniques, dessins Visio, CSV et TSV.

Téléchargez le programme d'installation **DLLs** ou **MSI** à partir de la [section téléchargements][6] ou installez l'API dans votre application .NET via [NuGet][7].

```
PM> Install-Package GroupDocs.Merger
```

## Fusionner des fichiers PDF, Word, Excel en un seul PDF en C# {#merge-multiple-files-into-one-pdf-in-csharp}

Vous pouvez combiner vos documents PDF avec vos documents Word, présentations et feuilles de calcul Excel avec seulement quelques lignes de code. Voici les étapes à suivre pour fusionner des documents de plusieurs types de fichiers en un seul fichier.

* Chargez le document source en utilisant la classe [Merger][8].
* Continuez à fusionner d'autres documents en utilisant la méthode [Join][9].
* Enregistrez le document combiné en tant que sortie à l'aide de la méthode [Enregistrer][10].

Le code source suivant montre comment fusionner des documents PDF, Word et Excel dans un seul fichier PDF en C#.

```
// Combinez deux ou plusieurs types de fichiers différents en un seul à l'aide de C #
using (Merger merger = new Merger("document.pdf"))
{
    merger.Join("document.docx");
    merger.Join("spreadsheet.xlsx");
    merger.Save("merge_document.pdf");
}
```

De la même manière, vous pouvez également combiner des fichiers du même format de fichier. Ce qui est mentionné ci-dessous est la sortie obtenue en joignant un document Word, un document PDF. et une feuille de calcul utilisant le code C# ci-dessus.



{{< figure align=center src="images/merged-pdf-word-excel-to-one-file.jpg" alt="Fusionner différents types de fichiers en un seul PDF C#">}}


## Fusionner des pages sélectives de plusieurs fichiers PDF, Word, Excel en un seul PDF en C# {#merge-selective-pages-of-multiple-files-into-one-pdf-in-csharp}



{{< figure align=center src="images/merged-selective-pages-of-pdf-word-excel-to-one-file.jpg" alt="Fusionner une page sélective de différents types de fichiers en un seul PDF C#">}}


Vous ne souhaitez pas toujours combiner l'ensemble du document. Vous voudrez peut-être choisir quelques pages d'un document et quelques autres pages du document suivant, et ainsi de suite. L'API propose différentes manières de fusionner des pages sélectives de plusieurs types de fichiers en un seul fichier.

* Chargez le document source à l'aide de la classe [Merger][11].
* Définissez les options de fusion à l'aide de la classe [JoinOptions][12].
* Fusionnez le document en utilisant la méthode [Join][13].
* Continuez à combiner les documents en définissant différentes options de jointure pour chaque document.
* Enregistrez le document fusionné à l'aide de la méthode [Enregistrer][14].

Le code source suivant montre comment fusionner un fichier PDF avec la première page d'un document Word et les feuilles paires du classeur Excel dans la plage fournie, en un seul fichier PDF à l'aide de C#.

```
// Combinez des pages sélectives de deux ou plusieurs types de fichiers différents en un seul à l'aide de C#
using (Merger merger = new Merger("document.pdf"))
{
    // Merge first page of DOCX file
    JoinOptions joinOptions = new JoinOptions(new int[] {1});
    merger.Join("document.docx", joinOptions);
    
    // Merge all the even pages/sheets of the spreadsheet from the provided range
    joinOptions = new JoinOptions(1,2, RangeMode.EvenPages);
    merger.Join("spreadsheet.xlsx", joinOptions);

    merger.Save("merge_document.pdf");
}
```

## Conclusion

Pour résumer, vous avez vu comment fusionner deux ou plusieurs documents de différents types de fichiers en un seul fichier à l'aide de C # dans l'application .NET. De plus, vous avez appris à combiner uniquement les pages sélectives de plusieurs types de fichiers.

Vous pouvez en savoir plus sur GroupDocs.Merger pour .NET en utilisant la [documentation][15]. Si vous avez des questions, faites-le nous savoir via notre [forum][16].

## Voir également

* [Fusionner des documents du même format en C#][17]
* [Fractionner ou fusionner des documents en Java][18]







[1]: https://blog.groupdocs.com/2021/05/04/merge-multiple-file-types-using-csharp/
[2]: #dotnet-api-to-merge-multiple-file-types
[3]: #merge-multiple-files-into-one-pdf-in-csharp
[4]: #merge-selective-pages-of-multiple-files-into-one-pdf-in-csharp
[5]: https://docs.groupdocs.com/merger/net/supported-document-formats/
[6]: https://downloads.groupdocs.com/merger/net
[7]: https://www.nuget.org/packages/groupdocs.merger
[8]: https://apireference.groupdocs.com/merger/net/groupdocs.merger/merger
[9]: https://apireference.groupdocs.com/merger/net/groupdocs.merger/merger/methods/join/index
[10]: https://apireference.groupdocs.com/merger/net/groupdocs.merger/merger/methods/save/index
[11]: https://apireference.groupdocs.com/merger/net/groupdocs.merger/merger
[12]: https://apireference.groupdocs.com/merger/net/groupdocs.merger.domain.options/joinoptions
[13]: https://apireference.groupdocs.com/merger/net/groupdocs.merger/merger/methods/join/index
[14]: https://apireference.groupdocs.com/merger/net/groupdocs.merger/merger/methods/save/index
[15]: https://docs.groupdocs.com/merger/net
[16]: https://forum.groupdocs.com/
[17]: https://blog.groupdocs.com/2020/08/19/merge-pdf-word-excel-ppt-files-in-csharp/
[18]: https://blog.groupdocs.com/2020/05/20/merge-pdf-word-excel-powerpoint-documents-in-java/


