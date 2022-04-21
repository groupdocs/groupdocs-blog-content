---
title: "Classez les commentaires de vos clients à l'aide de l'analyse des sentiments en C #"
date: Wed, 17 Jun 2020 08:28:00 +0000
draft: false
url: /fr/2020/06/17/classifier-les-commentaires-des-clients-en-utilisant-l-analyse-des-sentiments-dans-csharp/
author: 'Shoaib Khan'
summary: "Supposons que vous ayez la possibilité de recevoir des commentaires ou des critiques de vos clients ou d'une autre source et que vous souhaitiez évaluer à quel point ils sont positifs. Il existe un moyen d'analyser ces commentaires appelé **analyse des sentiments**. Cet article se concentre sur l'outil d'analyse des sentiments basé sur un modèle de réseau neuronal profond utilisant C#. Ce modèle convient à un large éventail de tâches."
tags: ['csharp code for sentiment analysis', 'csharp sentiment analysis', 'sentiment analysis csharp', 'sentiment analysis in csharp', 'sentiment classification in csharp']
categories: ['GroupDocs.Classification Product Family']
---

Supposons que vous ayez la possibilité de recevoir des commentaires ou des critiques de vos clients ou d'une autre source et que vous souhaitiez évaluer à quel point ils sont positifs. Il existe un moyen d'analyser ces commentaires appelé **analyse des sentiments**. Cet article se concentre sur l'outil d'analyse des sentiments basé sur un modèle de réseau neuronal profond utilisant C#. Ce modèle convient à un large éventail de tâches.

## API d'analyse des sentiments pour .NET

Si vous souhaitez effectuer une analyse des sentiments par programmation, [GroupDocs.Classification][1] vous sert à cette fin. Il implémente un classificateur de sentiment à usage général qui peut être utilisé pour évaluer le ton des avis sur les produits, les avis sur les magasins, les avis sur les applications, les commentaires, etc.



{{< figure align=center src="images/groupdocs_classification-for-net.png" alt="GroupDocs.Classification pour .NET">}}


Cet article vous guidera vers la classification des commentaires et analysera la positivité en utilisant C# avec **GroupDocs.Classification pour .NET**. Donc, avant de commencer, assurez-vous d'installer l'API à partir de l'une des méthodes suivantes :

* Installez à l'aide de [NuGet][2] Gestionnaire de packages.
* [Téléchargez][3] la DLL et référencez-la dans le projet.

## Comment classer du texte à l'aide de l'analyse des sentiments en C#

Pour résoudre une telle tâche, nous pouvons utiliser une classe générale nommée [Classifier][4], ou nous pouvons utiliser le Sentiment Classifier qui est une classe un peu plus simple et plus légère. Voici les étapes :

* Initialiser le [SentimentClassifier][5].
* Appelez la méthode [PositiveProbability][6] de la classe SentimentClassifier et transmettez le texte en tant que paramètre à analyser.
* La méthode PositiveProbability renverra la positivité allant de 0 à 1.

Voici le code C # pour trouver le ton de toute déclaration utilisant la classification des sentiments. Nous avons choisi le sentiment suivant comme exemple :

_"L'expérience est simplement le nom que nous donnons à nos erreurs"_

```
// Analyze the positivity of text using sentiment classifier in C#.
var sentiment = "Experience is simply the name we give our mistakes";
var sentimentClassifier = new SentimentClassifier();
/// PositiveProbability method returns the positive probability of the sentiment.
var positiveProbability = sentimentClassifier.PositiveProbability(sentiment);
Console.WriteLine($"Positive Probability of the sentiment { positiveProbability }");
```
```
Positive Probability of the sentiment: **0.1118**
```

Toute valeur supérieure à 0,5 signifie que le sentiment est positif et la plage entre 0 et 0,5 indique qu'il est négatif.

Maintenant, selon la positivité extraite, vous pouvez obtenir la ** meilleure classe ** pour ce sentiment et la probabilité de cette meilleure classe. Nous avons constaté que sa probabilité positive est de 0,11, il doit donc être classé comme un commentaire **négatif** et sa meilleure classe doit être **Négatif** au lieu de Positif.

So what would be its Best Class Probability? Yes, it will be 0.89. Voyons maintenant dans le code :

```
var sentiment = "Experience is simply the name we give our mistakes";
/// Classify method returns ClassificationResult object with the best class probability and name.
var response = sentimentClassifier.Classify(sentiment);
Console.WriteLine($"Best Class Name: {response.BestClassName}");
Console.WriteLine($"Best Class Probability: { response.BestClassProbability}");
```
```
Best Class Name: **Negative**
Best Class Probability: **0.8882**
```

## Classer plusieurs commentaires à l'aide de l'analyse des sentiments en C#

Normalement, nous avons des milliers de commentaires et de commentaires, alors comment pourrions-nous analyser les commentaires de nos clients ? C'est simple, il suffit de mettre les retours dans un tableau. Laissez le tableau de chaînes être la source de l'examen. Il peut également s'agir d'un fichier ou de la réponse analysée d'une base de données ou d'un service. Nous pouvons transformer le tableau de chaînes en tableau flottant de probabilités de sentiments positifs.

```
var sentiments = new string\[\] {
                "Now that is out of the way, this thing is a beast. It is fast and runs cool.",
                "Experience is simply the name we give our mistakes",
                "When I used compressed air a cloud of dust bellowed out from the card (small scuffs and scratches).",
                "This is Pathetic."
            };
            var classifier = new GroupDocs.Classification.SentimentClassifier();
            var sentimentPositivity = sentiments.Select(x => classifier.PositiveProbability(x)).ToArray();
            Console.WriteLine(string.Join("\\n", sentimentPositivity));
```
```
**0.8959** - "Now that is out of the way, this thing is a beast..."
**0.1118** - "Experience is simply the name we give our mistakes"
**0.1252** - "When I used compressed air a cloud ..."
**0.0970** - "This is Pathetic."
```

Que pouvons-nous faire avec les sentiments cibles ? Nous pouvons mesurer la positivité moyenne ou médiane pour le produit cible, le magasin, etc. Sélectionnez les pires valeurs et répondez aux clients. Nous pouvons également effectuer des analyses telles que la recherche d'incohérences entre la valeur de probabilité positive d'un produit et sa note.

Nous espérons que vous trouverez cet article utile. Vous pouvez en savoir plus sur la classification de texte ou l'analyse des sentiments en C # à partir des ressources mentionnées.

## En savoir plus sur l'API GroupDocs.Classification

* [Documents][7]
* [Exemples de code source][8]
* [Référence API][9]

Le téléchargement et l'exécution d'exemples GitHub sont la meilleure et la plus simple façon de commencer.

## Voir également

* [Classifier le texte brut à l'aide de C # - (IAB-2 et taxonomie des documents)][10]
* [Classer les documents à l'aide de C # - (IAB-2 et taxonomie des documents)][11]







[1]: https://products.groupdocs.com/classification
[2]: https://www.nuget.org/packages/GroupDocs.Classification
[3]: https://downloads.groupdocs.com/classification/net
[4]: https://apireference.groupdocs.com/classification/net/groupdocs.classification/classifier
[5]: https://apireference.groupdocs.com/classification/net/groupdocs.classification/sentimentclassifier
[6]: https://apireference.groupdocs.com/classification/net/groupdocs.classification/sentimentclassifier/methods/positiveprobability
[7]: https://docs.groupdocs.com/display/classificationnet/Home
[8]: https://github.com/groupdocs-classification/GroupDocs.Classification-for-.NET
[9]: https://apireference.groupdocs.com/classification/net
[10]: https://blog.groupdocs.com/2021/10/31/taxonomic-classification-of-text-using-csharp/
[11]: https://blog.groupdocs.com/2021/10/27/taxonomic-classification-of-documents-using-csharp/


