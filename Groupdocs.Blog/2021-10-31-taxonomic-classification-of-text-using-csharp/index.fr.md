---
title: "Classification taxonomique du texte brut à l'aide de C # - (IAB-2 et taxonomie des documents)"
date: Sun, 31 Oct 2021 10:22:00 +0000
draft: false
url: /fr/2021/10/31/classification-taxonomique-de-texte-utilisant-csharp/
aliases:
- /2019/12/10/classify-text-using-iab-2-or-document-taxonomies-in-csharp/
author: 'Shoaib Khan'
summary: "Dans un article, nous avons discuté de la manière dont nous pouvons [analyser et classer des documents complets par programmation][1]. Il est souvent nécessaire de ne classer qu'une partie du document ou seulement quelques déclarations. Dans cet article, nous identifierons les meilleures catégories taxonomiques possibles du texte sélectionné. Nous apprendrons **comment nous pouvons classer le texte selon IAB-2 et documenter les taxonomies à l'aide de C#**."
tags: ['Classify Text using CSharp', 'document taxonomy', 'Document Taxonomy using CSharp', 'Taxonomic Classification using CSharp', 'Text Classification using CSharp']
categories: ['GroupDocs.Classification Product Family']
---

Plus tôt, nous avons discuté de la façon dont nous pouvons [automatiser l'analyse et classer des documents complets par programmation][2]. Il est souvent nécessaire de ne classer qu'une partie du document ou seulement quelques déclarations. Dans cet article, nous identifierons les meilleures catégories taxonomiques possibles du texte sélectionné. Nous apprendrons **comment nous pouvons classer le texte selon IAB-2 et documenter les taxonomies à l'aide de C#**.

Les sujets suivants sont traités ci-dessous :

- [API .NET pour la classification taxonomique du texte][3]
- [Classification de texte avec la taxonomie IAB-2 utilisant C#][4]
- [Classification de texte avec taxonomie de document à l'aide de C #][5]

## API .NET pour la classification taxonomique du texte {#text-classification-dotnet-api}

[GroupDocs.Classification for .NET][6] est l'API qui permet différentes techniques de classification du contenu textuel dans les applications .NET. Nous utiliserons cette API pour trouver les meilleures catégories taxonomiques possibles du texte fourni en utilisant C# dans les exemples.

Vous pouvez télécharger le programme d'installation **DLLs** ou **MSI** à partir de la [section téléchargements][7] ou installer l'API dans votre application .NET via [NuGet][8].

```
PM> Install-Package GroupDocs.Classification
```

## Classification de texte avec la taxonomie IAB-2 à l'aide de C# {#classify-text-with-iab-2-taxonomy}

IAB-2 catégorise le contenu en [catégories taxonomiques][9] définies, puis le classe en fonction de l'analyse. Voici les étapes de la classification taxonomique du texte avec [taxonomie IAB-2][10] en utilisant C#.

* Instanciez le classificateur à l'aide de la classe [Classifier][11].
* Définir le texte pour l'analyse taxonomique.
* Définissez la [Taxonomy][12] comme **IAB2**.
* Définissez le nombre de meilleurs résultats à la suite de la classification. (_Optionnel_)
* Obtenez les catégories taxonomiques du texte fourni en appelant la méthode [Classify][13] avec les paramètres définis.
* Imprimez les [BestResults][14] à partir de la [réponse de classification][15] de la méthode Classify.

Le code source C# suivant montre comment classer du texte à l'aide de la **taxonomie IAB-2** et obtenir les meilleures catégories avec la meilleure correspondance.

```
/*
* Classify Text with IAB-2 Taxonomy using C#
*/
Classifier classifier = new Classifier();
string statement = "Medicine is an important part of our lives";

var response = classifier.Classify(statement, 3, Taxonomy.Iab2);
response.BestResults.ToList().ForEach(bestResult => Console.WriteLine($"Class: {bestResult.Name}, \tProbability: {bestResult.Probability}"));
```

```
 Class: Healthy\_Living,      Probability: 0.4144087
 Class: Medical\_Health,     Probability: 0.2108202
 Class: Science,                 Probability: 0.1584931
```

## Classification de texte avec taxonomie de document à l'aide de C# {#classify-text-with-document-taxonomy}

La taxonomie des documents classe le contenu en différentes [classes de documents][16], telles que les publicités, les factures, les actualités, les CV, les lettres, les e-mails, etc. Voici les étapes de la classification taxonomique du texte avec la taxonomie des documents à l'aide de C#.

* Instancier le [Classificateur][17].
* Charger le texte pour l'analyse taxonomique.
* Définir le nombre de meilleurs résultats compte à la suite de la classification. (_Optionnel_)
* Définissez la [Taxonomie][18] comme **Documents**.
* Obtenez les groupes taxonomiques en appelant la méthode [Classify][19] avec les paramètres définis ci-dessus.
* Imprimez les [BestResults][20] à partir de la [réponse de classification][21] de la méthode Classify.

Le code source C# suivant montre comment classer le contenu textuel et obtenir certaines de ses principales catégories taxonomiques à l'aide de la **taxonomie de document**.

```
/*
* Classify Text with Document Taxonomy using C#
*/
Classifier classifier = new Classifier();
string statement = "Sooner or later technology will overcome labor work";

var response = classifier.Classify(statement, 2, Taxonomy.Documents);
response.BestResults.ToList().ForEach(bestResult => Console.WriteLine($"Class: {bestResult.Name}, \tProbability: {bestResult.Probability}"));
```

```
 Class: ADVE,      Probability: 0.9999645
 Class: Report,     Probability: 3.461805E-05
```

## Obtenez une licence gratuite

Vous pouvez [obtenir une licence temporaire gratuite][22] afin d'utiliser l'API sans les limitations d'évaluation.

## Conclusion

En résumé, nous avons appris à classer différents types de documents en utilisant différentes taxonomies. Dans les exemples, nous avons classé le texte selon IAB-2 et les taxonomies de documents à l'aide de C#. Après avoir parcouru la série d'articles, vous pouvez créer votre propre application de classification .NET pour [classifier des documents][23] ainsi que du texte avec différentes taxonomies et configurations.

Pour en savoir plus sur l'API, consultez la [documentation][24]. Pour toute question, contactez-nous via le [forum][25].

## Voir également

* [Classer les commentaires des clients à l'aide de l'analyse des sentiments à l'aide de C#][26]
* [Classification taxonomique des documents utilisant C#][27]







[1]: https://blog.groupdocs.com/2021/10/27/taxonomic-classification-of-documents-using-csharp/
[2]: https://blog.groupdocs.com/2021/10/27/taxonomic-classification-of-documents-using-csharp/
[3]: #text-classification-dotnet-api
[4]: #classify-text-with-iab-2-taxonomy
[5]: #classify-text-with-document-taxonomy
[6]: https://products.groupdocs.com/classification/
[7]: https://downloads.groupdocs.com/classification/net
[8]: https://www.nuget.org/packages/groupdocs.classification
[9]: https://docs.groupdocs.com/classification/net/taxonomies/
[10]: https://www.iab.com/guidelines/content-taxonomy/
[11]: https://apireference.groupdocs.com/classification/net/groupdocs.classification/classifier
[12]: https://apireference.groupdocs.com/classification/net/groupdocs.classification/taxonomy
[13]: https://apireference.groupdocs.com/classification/net/groupdocs.classification/classifier/methods/classify/index
[14]: https://apireference.groupdocs.com/classification/net/groupdocs.classification.dto/classificationresponse/properties/bestresults
[15]: https://apireference.groupdocs.com/classification/net/groupdocs.classification.dto/classificationresponse/properties/index
[16]: https://docs.groupdocs.com/classification/net/taxonomies/
[17]: https://apireference.groupdocs.com/classification/net/groupdocs.classification/classifier
[18]: https://apireference.groupdocs.com/classification/net/groupdocs.classification/taxonomy
[19]: https://apireference.groupdocs.com/classification/net/groupdocs.classification/classifier/methods/classify/index
[20]: https://apireference.groupdocs.com/classification/net/groupdocs.classification.dto/classificationresponse/properties/bestresults
[21]: https://apireference.groupdocs.com/classification/net/groupdocs.classification.dto/classificationresponse/properties/index
[22]: https://purchase.groupdocs.com/temporary-license
[23]: https://blog.groupdocs.com/2021/10/27/taxonomic-classification-of-documents-using-csharp/
[24]: https://docs.groupdocs.com/classification
[25]: https://forum.groupdocs.com/
[26]: https://blog.groupdocs.com/2020/06/17/classify-customers-feedback-using-sentiment-analysis-in-csharp/
[27]: https://blog.groupdocs.com/2021/10/27/taxonomic-classification-of-documents-using-csharp/



