---
title: "Comparer des documents Word à l'aide de C#"
date: Wed, 01 Dec 2021 09:58:00 +0000
draft: false
url: /fr/2021/12/01/comparer-des-documents-word-avec-csharp/
aliases:
- /2014/07/19/groupdocs-comparison-for-dot-net-library-compare-two-word-documents-in-c-sharp-asp-net/
author: 'Shoaib Khan'
summary: "Les documents de traitement de texte sont le moyen le plus courant de rédiger des contrats, des accords, des documents et de nombreux autres documents officiels. Si vous avez besoin de comparer et de fusionner deux documents Word, tout comme l'option de suivi des modifications de Microsoft Word, nous pouvons le faire par programmation dans nos applications .NET. Dans cet article, nous expliquerons **comment comparer deux documents Word et mettre en évidence les différences identifiées à l'aide de C#**. De plus, nous verrons comment comparer des documents protégés par mot de passe, **accepter et rejeter les modifications** et comparer plus de deux documents avec des exemples C#."
tags: ['automate document comparison', 'compare two word documents', 'compare two word documents and highlight differences', 'Compare Word Documents CSharp', 'compare word files in c#', 'GroupDocs Comparison']
categories: ['GroupDocs.Comparison Product Family']
---

Les documents de traitement de texte sont le moyen le plus courant de rédiger des contrats, des accords, des documents et de nombreux autres documents officiels. Si vous avez besoin de comparer et de fusionner deux documents Word, tout comme l'option de suivi des modifications de Microsoft Word, nous pouvons le faire par programmation dans nos applications .NET. Dans cet article, nous expliquerons **comment comparer deux documents Word et mettre en évidence les différences identifiées à l'aide de C#**. De plus, nous verrons comment comparer des documents protégés par mot de passe, **accepter et rejeter les modifications** et comparer plus de deux documents avec des exemples C#.



{{< figure align=center src="images/compare-word-files-using-csharp.jpg" alt="Comparez des documents Word pour trouver des différences à l'aide de l'API .NET">}}


Les sujets suivants sont abordés ici :

* [API .NET de comparaison de documents][1]
* [Comparer deux documents Word][2]
* [Accepter ou rejeter les modifications identifiées dans le document Word][3]
* [Comparer plus de deux documents Word][4]
* [Comparer les fichiers Word protégés par mot de passe][5]

## API .NET pour comparer des documents Word {#doc-comparison-dotnet-api}

[GroupDocs.Comparison][6] fournit une API .NET qui permet [de comparer puis de fusionner divers documents de plusieurs formats de fichiers][7] au sein de l'application .NET. J'utiliserai son API .NET, c'est-à-dire [GroupDocs.Comparison pour .NET][8] pour comparer des documents Word.

Vous pouvez télécharger les DLL ou le programme d'installation MSI à partir de la [section des téléchargements][9] ou installer l'API dans votre application .NET via [NuGet][10].

```
PM> Install-Package GroupDocs.Comparison
```

## Comparer des documents Word à l'aide de C # {#compare-two-word-files}

Si vous avez deux versions d'un document, vous pouvez comparer les documents pour trouver leurs différences (ajouts, suppressions) et créer un nouveau document qui montre toutes les modifications. Voici les étapes pour comparer deux documents Word et mettre en évidence les différences.

* Chargez le premier document Word en utilisant la classe [Comparer][11].
* Ajoutez le deuxième fichier à **Comparer** en utilisant la méthode [Add()][12].
* Comparez le résumé des modifications en appelant simplement la méthode [Compare()][13].

Le code C# suivant montre comment comparer des documents Word et obtenir les modifications dans le document résultant.

```
/*
 * Compare Two Word Documents and Hightlight Changes using C#
 */
using (Comparer comparer = new Comparer("path/document.docx"))
{
    comparer.Add("path/document-ver2.docx");
    comparer.Compare("path/compared-result.docx");
}
```

## Accepter ou rejeter les modifications identifiées des documents Word à l'aide de C# {#accept-reject-changes}

Semblable à l'option de suivi des modifications de MS Word, vous pouvez accepter ou rejeter chaque modification identifiée. Voici les étapes pour comparer, puis accepter ou rejeter les modifications identifiées dans les documents Word.

* Chargez le document source et ajoutez le(s) document(s) Word cible(s) à l'aide de la classe [Comparer][14].
* Effectuez la comparaison des documents chargés à l'aide de la méthode [Comparer ()][15].
* Obtenez les modifications identifiées à l'aide de la méthode [GetChanges()][16].
* Vous pouvez maintenant parcourir les modifications et définir [ComparisonAction][17] de chaque modification.
    * Pour chaque modification, vous pouvez sélectionner **Accepter** ou **Refuser**.
* Lorsque vous avez terminé avec les modifications, appelez la méthode [ApplyChanges()][18] pour obtenir le document résultant ayant les modifications appliquées.

Le code source C# suivant compare deux documents Word, puis accepte une modification identifiée, puis en rejette une autre.

```
/*
 * Accept and reject identified changes by comparing Word documents using C#
 */
using (Comparer comparer = new Comparer("path/document-1.docx"))
{
    comparer.Add("path/document-2.docx");
    comparer.Compare();
    ChangeInfo[] changes = comparer.GetChanges();
    
    // Rejecting the first identified change and it will not be added to result document
    changes[0].ComparisonAction = ComparisonAction.Reject;
    comparer.ApplyChanges("path/rejected-change-result.docx", new ApplyChangeOptions { Changes = changes, SaveOriginalState = true });

    changes = comparer.GetChanges();
    changes[0].ComparisonAction = ComparisonAction.Accept;
    comparer.ApplyChanges("path/accepted-change-result.docx", new ApplyChangeOptions { Changes = changes });
}
```

## Comparer plus de deux documents à l'aide de C # {#compare-multiple-word-documents}

De même, plus de deux documents peuvent être comparés en une seule fois. Voici les étapes pour comparer plusieurs documents Word pour les différences et mettre en évidence les modifications identifiées.

* Chargez le premier document Word en utilisant la classe [Comparer][19].
* Continuez à ajouter les autres documents à **Comparer** en utilisant la méthode [Add()][20].
* Appelez la méthode [Compare()][21] pour obtenir les modifications et le résumé des modifications.

Le code C# suivant montre comment comparer plus de deux documents Word et obtenir les modifications dans le document résultant.

```
/*
 * Compare Multiple Word Documents using C#
 */
using (Comparer comparer = new Comparer("path/document-1.docx"))
{
    comparer.Add("path/document-2.docx");
    comparer.Add("path/document-3.docx");
    comparer.Add("path/document-4.docx");

    comparer.Compare("path/compare-result.docx");
}
```

## Comparer des documents Word protégés par mot de passe à l'aide de C# {#compare-password-protected-word-docs}

Si vos documents sont protégés par un mot de passe, fournissez simplement leur mot de passe lors du chargement des documents. Les étapes suivantes montrent comment comparer le contenu de documents protégés par mot de passe à l'aide de C#.

* Préparez les options de chargement des documents source et cible en fournissant le mot de passe.
* Chargez le document source à l'aide de la classe [Comparer][22].
* Ajoutez le document cible à **Comparer** en utilisant les options de chargement préparées.
* Obtenez le résumé des différences en appelant la méthode [Compare()][23].

L'exemple de code C# suivant compare deux fichiers Word protégés par mot de passe et génère le document résultant qui met en évidence les différences.

```
/*
 * Compare Password Protected Word Documents using C#
 */
using (Comparer comparer = new Comparer("path/protected-document-1.docx", new LoadOptions(){ Password = "SourceFilePassword" }))
{
    comparer.Add("path/protected-document-2.docx", new LoadOptions() { Password = "TargetFilePassword" });
    comparer.Compare("path/compared-protected-docs-result.docx");
}
```

## Obtenez une licence API gratuite

Vous pouvez [obtenir une licence temporaire gratuite][24] pour utiliser l'API sans les limitations d'évaluation.

## Conclusion

Pour conclure, nous avons appris à comparer deux ou plusieurs documents Word à l'aide de C#. De plus, après avoir mis en évidence les différences, nous avons appris à accepter et à rejeter par programmation les changements identifiés. En fin de compte, nous avons également discuté de la manière de comparer les documents Word protégés par mot de passe dans les applications .NET.

Il existe de nombreuses autres [personnalisations pour contrôler les résultats de la comparaison][25], comme définir la sensibilité de la comparaison, afficher uniquement la page de résumé, ignorer les ** lacunes **, et bien plus encore. En savoir plus sur **GroupDocs.Comparison pour .NET**. Consultez sa [documentation][26] pour commencer à créer vos propres applications de comparaison de documents pour divers [formats de documents pris en charge][27]. Pour toute question, contactez-nous via le [forum][28].

## Voir également

* [Comparer l'image en utilisant C # pour repérer les différences][29]
* [Comparer des documents PDF à l'aide de C # - Mettre en surbrillance, accepter ou rejeter les modifications][30]
* [Comment comparer des fichiers texte, Word et PDF en Java][31]







[1]: #doc-comparison-dotnet-api
[2]: #compare-two-word-files
[3]: #accept-reject-changes
[4]: #compare-multiple-word-documents
[5]: #compare-password-protected-word-docs
[6]: https://products.groupdocs.com/comparison/
[7]: https://docs.groupdocs.com/comparison/net/supported-document-formats/
[8]: https://products.groupdocs.com/comparison/net/
[9]: https://downloads.groupdocs.com/comparison/net
[10]: https://www.nuget.org/packages/groupdocs.comparison
[11]: https://apireference.groupdocs.com/comparison/net/groupdocs.comparison/comparer
[12]: https://apireference.groupdocs.com/comparison/net/groupdocs.comparison/comparer/methods/add/index
[13]: https://apireference.groupdocs.com/comparison/net/groupdocs.comparison/comparer/methods/compare/index
[14]: https://apireference.groupdocs.com/comparison/net/groupdocs.comparison/comparer
[15]: https://apireference.groupdocs.com/comparison/net/groupdocs.comparison/comparer/methods/compare/index
[16]: https://apireference.groupdocs.com/comparison/net/groupdocs.comparison/comparer/methods/getchanges/index
[17]: https://apireference.groupdocs.com/comparison/net/groupdocs.comparison.result/comparisonaction
[18]: https://apireference.groupdocs.com/comparison/net/groupdocs.comparison/comparer/methods/applychanges/index
[19]: https://apireference.groupdocs.com/comparison/net/groupdocs.comparison/comparer
[20]: https://apireference.groupdocs.com/comparison/net/groupdocs.comparison/comparer/methods/add/index
[21]: https://apireference.groupdocs.com/comparison/net/groupdocs.comparison/comparer/methods/compare/index
[22]: https://apireference.groupdocs.com/comparison/net/groupdocs.comparison/comparer
[23]: https://apireference.groupdocs.com/comparison/net/groupdocs.comparison/comparer/methods/compare/index
[24]: https://purchase.groupdocs.com/temporary-license
[25]: https://docs.groupdocs.com/comparison/net/comparison/
[26]: https://docs.groupdocs.com/comparison/net
[27]: https://docs.groupdocs.com/comparison/net/supported-document-formats/
[28]: https://forum.groupdocs.com/
[29]: https://blog.groupdocs.com/2021/01/06/compare-images-in-csharp-dotnet/
[30]: https://blog.groupdocs.com/2021/12/10/compare-pdf-documents-using-csharp/
[31]: https://blog.groupdocs.com/2020/07/15/compare-text-word-pdf-files-with-java-difference-library/


