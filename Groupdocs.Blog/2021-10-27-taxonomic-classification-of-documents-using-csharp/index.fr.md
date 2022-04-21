---
title: "Classification taxonomique des documents à l'aide de C # - (IAB-2 et taxonomie des documents)"
date: Wed, 27 Oct 2021 12:24:00 +0000
draft: false
url: /fr/2021/10/27/classification-taxonomique-des-documents-utilisant-csharp/
author: 'Shoaib Khan'
summary: "Une classification est essentiellement une approche dans laquelle le texte est systématiquement identifié puis organisé selon des règles. La taxonomie définit la science d'une telle classification. Lorsque vous avez affaire à un tas de documents textuels, il devient difficile de trouver un sujet de n'importe quel document jusqu'à la classification taxonomique du contenu. Dans cet article, vous apprendrez **comment classer par programmation des documents selon IAB-2 et la taxonomie des documents à l'aide de C#**."
tags: ['Classify Documents using CSharp', 'Document Classification in CSharp', 'Document Taxonomy using CSharp', 'Taxonomic Classification using CSharp']
categories: ['GroupDocs.Classification Product Family']
---

Une classification est essentiellement une approche dans laquelle le texte est systématiquement identifié puis organisé selon des règles. La taxonomie définit la science d'une telle classification. Lorsque vous avez affaire à un tas de documents textuels, il devient difficile de trouver un sujet de n'importe quel document jusqu'à la classification taxonomique du contenu. Dans cet article, vous apprendrez **comment classer par programmation des documents selon IAB-2 et la taxonomie des documents à l'aide de C#**.

Les sujets suivants sont traités ci-dessous :

* [API .NET pour la classification taxonomique][1]
* [Classification des documents avec la taxonomie IAB-2][2]
* [Classer les documents avec la taxonomie des documents][3]
* [Classer les documents protégés par mot de passe][4]

## API .NET pour la classification taxonomique des documents {#document-classification-dotnet-api}

[GroupDocs.Classification][5] fournit la solution de classification pour différents types d'applications. Son API .NET vous permet de classer des documents de différents formats de fichiers selon différentes catégories taxonomiques au sein de vos applications .NET. Nous utiliserons son API [GroupDocs.Classification for .NET][6] pour la classification des documents PDF et Word à l'aide de C#.

Vous pouvez télécharger le programme d'installation **DLLs** ou **MSI** à partir de la [section téléchargements][7] ou installer l'API dans votre application .NET via [NuGet][8].

```
PM> Install-Package GroupDocs.Classification
```

## Classer les documents avec la taxonomie IAB-2 à l'aide de C# {#classify-with-iab-2-taxonomy}

IAB-2 catégorise le contenu du document en plusieurs [sujets][9], puis le classe en fonction du niveau de profondeur. Voici les étapes pour identifier la classification taxonomique des documents avec [taxonomie IAB-2][10] à l'aide de C#.

* Instanciez le classificateur à l'aide de la classe [Classifier][11].
* Définissez le document d'entrée et le dossier d'entrée.
* Définissez la [taxonomie][12] comme **IAB2**.
* Définissez le décompte des premiers meilleurs résultats dans la réponse. (_Optionnel_)
* Obtenez les catégories taxonomiques en appelant la méthode [Classify][13] avec les paramètres définis.
* Imprimez le [Nom de la meilleure classe][14] et la [Probabilité][15] en utilisant la [réponse de classification][16] de la méthode Classifier.

Le code source C# suivant montre comment classer des documents à l'aide de la **taxonomie IAB-2** et obtenir certains des meilleurs résultats de classification de documents.

```
/*
* Classify documents (PDF, Word, ...) with IAB-2 Taxonomy using C#
*/
Classifier classifier = new Classifier();
var filename = "document.pdf";
var response = classifier.Classify(filename, "<inputFolderPath>" , 4, Taxonomy.Iab2);
response.BestResults.ToList().ForEach(bestResult => Console.WriteLine($"Class: {bestResult.Name}, \t Probability: {bestResult.Probability}"));
```

```
 Class: Technology\_&Computing,     Probability: 0.8188434 
 Class: Video\_Gaming,                     Probability: 0.12686 
 Class: Hobbies&\_Interests,             Probability: 0.03112753 
 Class: Music\_and\_Audio,                Probability: 0.006756512
```

## Classer les documents avec la taxonomie des documents à l'aide de C# {#classify-with-document-taxonomy}

La taxonomie des documents est utilisée pour identifier différentes [classes de documents][17], telles que les factures, les CV, les formulaires, les e-mails, etc. Voici les étapes pour identifier la classification taxonomique des documents avec la taxonomie des documents à l'aide de C#.

* Instanciez le classificateur à l'aide de la classe [Classifier][18].
* Définissez le document d'entrée et le dossier.
* Définissez la [Taxonomie][19] comme **Documents**.
* Définissez le nombre de meilleurs résultats dans la réponse. (_Optionnel_)
* Obtenez les groupes taxonomiques en appelant la méthode [Classify][20] avec les paramètres définis ci-dessus.
* Imprimez le [Nom de la meilleure classe][21] et la [Probabilité][22] en utilisant la [réponse de classification][23] de la méthode Classifier.

Le code source C# suivant montre comment classer les documents et obtenir certaines des meilleures catégories taxonomiques à l'aide de la **taxonomie des documents**.

```
/*
* Classify documents (PDF, Word, ...) with Document Taxonomy using C#
*/
Classifier classifier = new Classifier();
var filename = "document.pdf";
var response = classifier.Classify(filename, "<inputFolderPath>" , 4, Taxonomy.Documents);
response.BestResults.ToList().ForEach(bestResult => Console.WriteLine($"Class: {bestResult.Name}, \t Probability: {bestResult.Probability}"));
```

```
 Class: ADVE,         Probability: 0.3874436
 Class: Resume,     Probability: 0.2438204
 Class: News,         Probability: 0.1357582
 Class: Memo,        Probability: 0.0641943
```

## Classer les documents protégés par mot de passe à l'aide de C# {#classify-secured-documents}

Si votre document est sécurisé par un mot de passe, vous pouvez simplement fournir les informations d'identification lors de la classification. Voici les étapes pour la classification des documents protégés par mot de passe à l'aide de C#

* Instancier le [Classificateur][24].
* Définissez le document d'entrée, le dossier d'entrée et le mot de passe du document protégé.
* Définissez la [Taxonomie][25] comme **Documents**.
* Obtenez le groupe taxonomique en appelant la méthode [Classify][26] avec les paramètres définis.
* Obtenez le [Meilleur nom de classe][27] et la [Probabilité][28] à partir de la [réponse][29] de la méthode Classify.

L'extrait de code suivant montre comment classer les documents protégés par mot de passe et obtenir la meilleure catégorie taxonomique à l'aide de la taxonomie par défaut (IAB-2).

```
/*
* Classify password protected documents using C#
*/
Classifier classifier = new Classifier();
var filename = "password-protected.docx";
var response = classifier.Classify(filename, "<inputFolderPath>", password: "password");
Console.WriteLine($"Best Class: {response.BestClassName}, \t Probability: {response.BestClassProbability}");
```

```
Best Class: Hobbies\_&\_Interests,      Probability: 0.4548415
```

Les valeurs par défaut pour la taxonomie seraient IAB-2 et le nombre des meilleurs résultats serait 1.

## Obtenez une licence gratuite

Vous pouvez [obtenir une licence temporaire gratuite][30] afin d'utiliser l'API sans les limitations d'évaluation.

## Conclusion

Pour conclure, nous avons appris à classer différents types de documents en utilisant différentes taxonomies. Plus précisément, nous avons classé les documents PDF selon IAB-2 et les taxonomies de documents à l'aide de C#. En outre, nous avons discuté de la manière dont nous pouvons classer les documents Word protégés par mot de passe avec une classification taxonomique par défaut ou spécifique. Vous pouvez maintenant intégrer la fonctionnalité de classification de documents dans votre application .NET.

Pour en savoir plus sur l'API, consultez la [documentation][31]. Pour toute question, contactez-nous via le [forum][32].

## Voir également

* [Classer le texte avec IAB-2 et la taxonomie des documents à l'aide de C#][33]
* [Classer les commentaires des clients à l'aide de l'analyse des sentiments à l'aide de C#][34]







[1]: #document-classification-dotnet-api
[2]: #classify-with-iab-2-taxonomy
[3]: #classify-with-document-taxonomy
[4]: #classify-secured-documents
[5]: https://products.groupdocs.com/classification/
[6]: https://products.groupdocs.com/classification/net/
[7]: https://downloads.groupdocs.com/classification/net
[8]: https://www.nuget.org/packages/groupdocs.classification
[9]: https://docs.groupdocs.com/classification/net/taxonomies/
[10]: https://www.iab.com/guidelines/content-taxonomy/
[11]: https://apireference.groupdocs.com/classification/net/groupdocs.classification/classifier
[12]: https://apireference.groupdocs.com/classification/net/groupdocs.classification/taxonomy
[13]: https://apireference.groupdocs.com/classification/net/groupdocs.classification/classifier/methods/classify/index
[14]: https://apireference.groupdocs.com/classification/net/groupdocs.classification.dto/classificationresponse/properties/bestclassname
[15]: https://apireference.groupdocs.com/classification/net/groupdocs.classification.dto/classificationresponse/properties/bestclassprobability
[16]: https://apireference.groupdocs.com/classification/net/groupdocs.classification.dto/classificationresponse/properties/index
[17]: https://docs.groupdocs.com/classification/net/taxonomies/
[18]: https://apireference.groupdocs.com/classification/net/groupdocs.classification/classifier
[19]: https://apireference.groupdocs.com/classification/net/groupdocs.classification/taxonomy
[20]: https://apireference.groupdocs.com/classification/net/groupdocs.classification/classifier/methods/classify/index
[21]: https://apireference.groupdocs.com/classification/net/groupdocs.classification.dto/classificationresponse/properties/bestclassname
[22]: https://apireference.groupdocs.com/classification/net/groupdocs.classification.dto/classificationresponse/properties/bestclassprobability
[23]: https://apireference.groupdocs.com/classification/net/groupdocs.classification.dto/classificationresponse/properties/index
[24]: https://apireference.groupdocs.com/classification/net/groupdocs.classification/classifier
[25]: https://apireference.groupdocs.com/classification/net/groupdocs.classification/taxonomy
[26]: https://apireference.groupdocs.com/classification/net/groupdocs.classification/classifier/methods/classify/index
[27]: https://apireference.groupdocs.com/classification/net/groupdocs.classification.dto/classificationresponse/properties/bestclassname
[28]: https://apireference.groupdocs.com/classification/net/groupdocs.classification.dto/classificationresponse/properties/bestclassprobability
[29]: https://apireference.groupdocs.com/classification/net/groupdocs.classification.dto/classificationresponse/properties/index
[30]: https://purchase.groupdocs.com/temporary-license
[31]: https://docs.groupdocs.com/classification
[32]: https://forum.groupdocs.com/
[33]: https://blog.groupdocs.com/2021/10/31/taxonomic-classification-of-text-using-csharp/
[34]: https://blog.groupdocs.com/2020/06/17/classify-customers-feedback-using-sentiment-analysis-in-csharp/



