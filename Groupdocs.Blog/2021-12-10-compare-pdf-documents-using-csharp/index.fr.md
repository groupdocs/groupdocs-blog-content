---
title: "Comparez des documents PDF à l'aide de C # - Mettez en surbrillance, acceptez ou rejetez les modifications"
date: Fri, 10 Dec 2021 10:20:37 +0000
draft: false
url: /fr/2021/12/10/compare-pdf-documents-using-csharp/
aliases:
- /2019/11/06/find-differences-in-pdf-accept-or-reject-changes-in-csharp/
- /2019/11/06/accept-or-reject-pdf-comparison-changes-in-csharp/
author: 'Shoaib Khan'
summary: "Étant donné que le PDF est l'un des formats les plus utilisés dans le monde numérique, il est souvent nécessaire de comparer deux versions du même document. Cet article explique **comment comparer deux documents PDF et mettre en évidence les différences à l'aide de C#**. De plus, nous verrons comment comparer des fichiers PDF protégés par mot de passe, accepter et rejeter les modifications, ainsi que la comparaison de plus de deux fichiers PDF avec des exemples C#."
tags: ['compare PDF files', 'Compare PDF in CSharp', 'Compare PDF to Accept or Reject Changes in CSharp', 'pdf comparison']
categories: ['GroupDocs.Comparison Product Family']
---

Étant donné que le PDF est l'un des formats les plus utilisés dans le monde numérique, il est souvent nécessaire de comparer deux versions du même document. Cet article explique **comment comparer deux documents PDF et mettre en évidence les différences à l'aide de C#**. De plus, nous verrons comment comparer des fichiers PDF protégés par mot de passe, accepter et rejeter les modifications, ainsi que la comparaison de plus de deux fichiers PDF avec des exemples C#.



{{< figure align=center src="images/compare-pdf-files-using-csharp.jpg" alt="Comparez des documents PDF pour trouver des différences à l'aide de l'API .NET">}}


Les sujets suivants sont abordés ici :

* [API .NET de comparaison PDF][1]
* [Comparer deux documents PDF][2]
* [Accepter ou rejeter les modifications identifiées dans les documents PDF][3]
* [Comparer plus de deux documents PDF][4]
* [Comparer les fichiers PDF protégés par mot de passe][5]

## API .NET pour comparer des fichiers PDF {#pdf-comparison-dotnet-api}

[GroupDocs.Comparison pour .NET][6] est l'API qui permet la comparaison entre plusieurs documents PDF et de nombreux autres fichiers du même format de document dans les applications .NET. J'utiliserai cette API dans les exemples de code C# de cet article pour comparer des documents PDF.

Vous pouvez télécharger les DLL ou le programme d'installation MSI à partir de la [section des téléchargements][7] ou installer l'API dans votre application .NET via [NuGet][8].

```
PM> Install-Package GroupDocs.Comparison
```

## Comparer des documents PDF à l'aide de C# {#compare-two-pdf-files}

Si vous avez plusieurs copies d'un document PDF, vous pouvez comparer ces fichiers pour trouver les différences (ajouts, suppressions). Après avoir comparé le contenu du PDF, vous pouvez créer un nouveau document mettant en évidence toutes les modifications identifiées. Voici les étapes pour comparer deux documents PDF et mettre en évidence les différences à l'aide de C#.

* Chargez le premier document PDF à l'aide de la classe [Comparer][9].
* Ajoutez le deuxième fichier à **Comparer** en utilisant la méthode [Add()][10].
* Comparez les deux fichiers PDF et obtenez le résumé des modifications en appelant la méthode [Compare()][11].

L'extrait de code C# suivant montre comment comparer des documents PDF et mettre en évidence les modifications dans le document résultant.

```
/*
 * Compare Two PDF Documents and Hightlight Changes using C#
 */
using (Comparer comparer = new Comparer(@"path/document-ver1.pdf"))
{
    comparer.Add(@"path/document-ver2.pdf");
    comparer.Compare(@"path/compared-result.pdf");
}
```

## Accepter ou rejeter les modifications identifiées des fichiers PDF à l'aide de C# {#accept-reject-changes}

Tout comme les fonctionnalités de suivi des modifications, vous pouvez accepter ou rejeter par programmation chaque modification identifiée dans les documents PDF. Les étapes suivantes montrent comment comparer puis accepter ou rejeter les modifications identifiées dans les documents PDF.

* Chargez les fichiers PDF source et cible à l'aide de la classe [Comparer][12].
* Comparez les documents chargés à l'aide de la méthode [Compare()][13].
* Obtenez les modifications identifiées à l'aide de la méthode [GetChanges()][14].
* Parcourez maintenant les modifications et définissez [ComparisonAction][15].
    * Sélectionnez **Accepter** ou **Refuser** pour chaque modification.
* Appelez la méthode [ApplyChanges()][16] pour obtenir le document résultant avec les modifications acceptées.

L'extrait de code suivant compare deux documents PDF, puis accepte une modification identifiée, puis en rejette une autre à l'aide de C#.

```
/*
 * Accept and reject identified changes by comparing PDF documents using C#
 */
using (Comparer comparer = new Comparer(@"path/document-1.pdf"))
{
    comparer.Add(@"path/document-2.pdf");
    comparer.Compare();
    ChangeInfo[] changes = comparer.GetChanges();
    
    // Rejecting the first identified change and it will not be added to result document
    changes[0].ComparisonAction = ComparisonAction.Reject;
    comparer.ApplyChanges(@"path/rejected-change-result.pdf", new ApplyChangeOptions { Changes = changes, SaveOriginalState = true });

    changes = comparer.GetChanges();
    changes[0].ComparisonAction = ComparisonAction.Accept;
    comparer.ApplyChanges(@"path/accepted-change-result.pdf", new ApplyChangeOptions { Changes = changes });
}
```

## Comparez plus de deux fichiers PDF à l'aide de C # {#compare-multiple-pdf-documents}

De même, vous pouvez comparer plus de deux documents. Voici les étapes qui comparent plusieurs documents PDF pour les différences et mettent en évidence les modifications identifiées.

* Chargez les premiers fichiers PDF à l'aide de la classe [Comparer][17].
* Ajoutez d'autres documents à **Comparer** à l'aide de la méthode [Add()][18].
* Comparez tous les fichiers PDF à l'aide de la méthode [Comparer ()][19] et obtenez les modifications et le résumé des modifications.

L'exemple suivant montre comment comparer plusieurs fichiers PDF en C# et obtenir les modifications dans le document résultant.

```
/*
 * Compare Multiple PDF Documents using C#
 */
using (Comparer comparer = new Comparer(@"path/document-1.pdf"))
{
    comparer.Add(@"path/document-2.pdf");
    comparer.Add(@"path/document-3.pdf");
    comparer.Add(@"path/document-4.pdf");

    comparer.Compare(@"path/compare-result.pdf");
}
```

## Comparer des documents PDF protégés par mot de passe à l'aide de C# {#compare-password-protected-pdf-files}

Vous pouvez comparer les fichiers protégés par mot de passe en fournissant simplement leurs mots de passe lors du chargement de ces documents. Les étapes suivantes montrent comment nous pouvons comparer le contenu PDF de documents protégés par mot de passe à l'aide de C#.

* Préparez les options de chargement des documents source et cible en fournissant le mot de passe.
* Chargez le document source à l'aide de la classe [Comparer][20].
* Ajoutez le document cible à **Comparer** en utilisant les options de chargement préparées.
* Obtenez le résumé des différences en appelant la méthode [Compare()][21].

L'exemple suivant compare deux fichiers PDF protégés par mot de passe et met en évidence les différences identifiées dans un document distinct à l'aide de C#.

```
/*
 * Compare Password Protected PDF Documents using C#
 */
using (Comparer comparer = new Comparer(@"path/protected-document-1.pdf", new LoadOptions(){ Password = "SourceFilePassword" }))
{
    comparer.Add(@"path/protected-document-2.pdf", new LoadOptions() { Password = "TargetFilePassword" });
    comparer.Compare(@"path/compared-protected-docs-result.pdf");
}
```

## Obtenez une licence API gratuite

Vous pouvez [obtenir une licence temporaire gratuite][22] pour utiliser l'API sans les limitations d'évaluation.

## Conclusion

Pour conclure, nous avons appris à comparer deux ou plusieurs fichiers PDF à l'aide de C#. De plus, nous avons mis en évidence les différences et accepté ou rejeté par programme les modifications identifiées. Enfin, nous avons vu comment comparer des documents PDF protégés par mot de passe dans des applications .NET.

Plusieurs autres [personnalisations][23] sont disponibles pour contrôler les résultats de la comparaison. Vous pouvez définir la sensibilité de la comparaison, afficher uniquement la page de résumé, ignorer les **lacunes**, etc. En savoir plus sur **GroupDocs.Comparison pour .NET** dans la [documentation][24]. Vous pouvez créer vos propres applications de comparaison de documents pour différents [formats de documents][25]. Pour toute question, contactez-nous via le [forum][26].

## Voir également

* [Comparaison d'images à l'aide de C # et repérer les différences][27]
* [Comparer des documents Word avec C#][28]
* [Comparer des documents avec la bibliothèque de différences Java][29]







[1]: #pdf-comparison-dotnet-api
[2]: #compare-two-pdf-files
[3]: #accept-reject-changes
[4]: #compare-multiple-pdf-documents
[5]: #compare-password-protected-pdf-files
[6]: https://products.groupdocs.com/comparison/
[7]: https://downloads.groupdocs.com/comparison/net
[8]: https://www.nuget.org/packages/groupdocs.comparison
[9]: https://apireference.groupdocs.com/comparison/net/groupdocs.comparison/comparer
[10]: https://apireference.groupdocs.com/comparison/net/groupdocs.comparison/comparer/methods/add/index
[11]: https://apireference.groupdocs.com/comparison/net/groupdocs.comparison/comparer/methods/compare/index
[12]: https://apireference.groupdocs.com/comparison/net/groupdocs.comparison/comparer
[13]: https://apireference.groupdocs.com/comparison/net/groupdocs.comparison/comparer/methods/compare/index
[14]: https://apireference.groupdocs.com/comparison/net/groupdocs.comparison/comparer/methods/getchanges/index
[15]: https://apireference.groupdocs.com/comparison/net/groupdocs.comparison.result/comparisonaction
[16]: https://apireference.groupdocs.com/comparison/net/groupdocs.comparison/comparer/methods/applychanges/index
[17]: https://apireference.groupdocs.com/comparison/net/groupdocs.comparison/comparer
[18]: https://apireference.groupdocs.com/comparison/net/groupdocs.comparison/comparer/methods/add/index
[19]: https://apireference.groupdocs.com/comparison/net/groupdocs.comparison/comparer/methods/compare/index
[20]: https://apireference.groupdocs.com/comparison/net/groupdocs.comparison/comparer
[21]: https://apireference.groupdocs.com/comparison/net/groupdocs.comparison/comparer/methods/compare/index
[22]: https://purchase.groupdocs.com/temporary-license
[23]: https://docs.groupdocs.com/comparison/net/comparison/
[24]: https://docs.groupdocs.com/comparison/net
[25]: https://docs.groupdocs.com/comparison/net/supported-document-formats/
[26]: https://forum.groupdocs.com/
[27]: https://blog.groupdocs.com/2021/01/06/compare-images-in-csharp-dotnet/
[28]: https://blog.groupdocs.com/2021/12/01/compare-word-documents-using-csharp/
[29]: https://blog.groupdocs.com/2020/07/15/compare-text-word-pdf-files-with-java-difference-library/


