---
title: "Créez votre solution de recherche de texte intégral en C#"
date: Thu, 03 Jun 2021 00:20:00 +0000
draft: false
url: /fr/2021/06/03/créez-votre-solution-de-recherche-en-texte-full-dans-csharp/
aliases:
- /2019/11/22/créez-votre-solution-de-recherche-en-texte-full-dans-csharp/
author: 'Shoaib Khan'
summary: 'Full-text search is basically a more advanced way to search a text/query over a collection of documents. This approach quickly finds all instances of a term and it works by using text indexes. In this article, we will learn, how to programmatically search full-text in documents using C#.

Les sujets suivants sont abordés dans cet article :

* API .NET pour la recherche en texte intégral
* Recherche en texte intégral
* Effectuer une recherche en C#
* Mettez en surbrillance les résultats de la recherche

[Continuer la lecture...][1]'
tags: ['full text search', 'Full Text Search Csharp']
categories: ['GroupDocs.Search Product Family']
---

Avant d'entrer dans les détails, donnons un aperçu de la technique de recherche en texte intégral. La recherche en texte intégral est essentiellement un moyen plus avancé de rechercher un texte/une requête dans une collection de documents. Cette approche trouve rapidement toutes les instances d'un terme et fonctionne en utilisant des index de texte. Dans cet article, nous apprendrons comment rechercher par programmation du texte intégral dans des documents à l'aide de C#.

Après cela, vous pouvez implémenter diverses techniques de recherche pour rechercher du texte dans des documents de traitement de texte, des feuilles de calcul, des présentations, des fichiers HTML, des livres électroniques PDF, des messages électroniques, des archives ZIP et de nombreux autres fichiers.

L'un des exemples d'implémentation de la recherche en texte intégral se trouve dans les traitements de texte et les éditeurs de texte. Il vous aide à trouver une phrase ou un mot n'importe où dans le document.



{{< figure align=center src="images/TextSearch-1.png" alt="Recherche en texte intégral">}}


Les sujets suivants sont traités ci-dessous :

* [API .NET pour la recherche en texte intégral][2]
* [Recherche plein texte][3]
* [Effectuer une recherche en C#][4]
* [Surligner les résultats de la recherche][5]

## API .NET pour la recherche de texte {#full-text-search-dotnet-api}

[GroupDocs.Search for .NET][6] est une API de recherche back-end qui permet la recherche en texte intégral et peut être intégrée à n'importe quelle application .NET sans aucun outil tiers ni dépendance logicielle. Il vous permet de [rechercher parmi une multitude de formats de documents][7] dans vos applications.

Vous pouvez télécharger le programme d'installation **DLLs** ou **MSI** à partir de la [section téléchargements][8] ou installer l'API dans votre application .NET via [NuGet][9].

```
PM> Install-Package GroupDocs.Search
```

## Recherche plein texte avec C# {#full-text-search-in-csharp}

Il existe deux étapes principales pour effectuer ou implémenter une recherche plein texte.

* Indexation
* Effectuer une recherche

## Indexage

Pour pouvoir rechercher instantanément parmi des milliers de documents avec des formats de fichiers identiques ou différents, vous devez créer un index et y ajouter ces documents.

### **Qu'est-ce qu'un index ?**

Un index possède le texte numérisé de tous les documents. Par conséquent, lorsque vous allez effectuer une opération de recherche (recherche d'une requête spécifique), seul l'index est référencé, et non le texte des documents d'origine.

### **Création d'index**

Un index peut être créé en mémoire ou sur un disque. L'index créé en mémoire ne peut pas être sauvegardé après avoir quitté votre programme. En revanche, un index créé sur le disque peut être chargé ultérieurement pour continuer à fonctionner. L'exemple suivant montre comment créer un index sur un disque.

```
Index index = new Index("indexPath/FolderName/");
```

Lorsque les documents sont indexés, l'index est prêt à gérer les requêtes de recherche. Voici quelques-unes des techniques de recherche pouvant être effectuées à l'aide de GroupDocs.Search pour .NET :

* Recherche sensible à la casse
* Recherche d'expressions régulières
* Recherche de phrases
* Recherche à facettes
* Recherche de synonymes
* Recherche générique

## Effectuer une recherche en C# {#perform-search-in-csharp}

A partir d'un cas d'utilisation. Si nous avons plusieurs documents (Word, PDF, Excel et HTML) et que nous voulons effectuer une requête de recherche spécifique (terme de recherche "vidéo") sur eux.

Voici les étapes à suivre pour effectuer une recherche de texte sur plusieurs documents dans un dossier :

* Décidez du dossier des documents source et du dossier d'index.
* Préparez la chaîne de requête.
* Créez [Index][10] à l'aide du dossier d'index.
* Ajoutez le dossier des documents source à l'index.
* Effectuez une recherche à l'aide de la méthode [Recherche][11] [Classe Index][12].
* Résultats de parcours et de recherche pour les propriétés de chaque document.

Le code source suivant effectue une recherche de texte à l'aide de C# sur tous les documents du dossier fourni.

```
// Rechercher le texte de la requête dans tous les documents du dossier fourni en C#
string indexFolder =  @"indexPath/GroupDocs/index/";
string documentsFolder = @"documentPath/GroupDocs/source/";
string query = "video";

// Création d'un index dans le dossier spécifié et ajout du dossier de documents à l'index
Index index = new Index(indexFolder);
index.Add(documentsFolder);

// Recherche dans l'index
SearchResult result = index.Search(query);
Console.WriteLine("Documents found: " + result.DocumentCount);

// Parcourez chaque document du résultat de la recherche
foreach (FoundDocument document in result)
{
    Console.WriteLine("Document Path : " + document.DocumentInfo.FilePath);
    Console.WriteLine("Occurance : " + document.OccurrenceCount);
}
```

Nous obtiendrons le chemin du document et le nombre d'occurrences du terme de recherche dans tous les documents disponibles dans le dossier de documents. Voici la capture d'écran pour visualiser.



{{< figure align=center src="images/SearchTextOutput.jpg" alt="Sortie de texte de recherche complète">}}


## Mettre en surbrillance les résultats de la recherche de texte en C# {#highlight-search-results-in-csharp}

Effectuons maintenant la même recherche de texte, mais cette fois nous allons mettre en surbrillance toutes les occurrences qui correspondent à la requête.

Les étapes suivantes montrent comment mettre en surbrillance les résultats de la recherche de texte :

* Préparez la chaîne de requête.
* Créez [Index][13] en utilisant le chemin du dossier d'index.
* Ajoutez le dossier des documents source à l'index.
* Recherchez le dossier de documents à l'aide de la méthode [Rechercher][14].
* En parcourant les résultats de la recherche, créez le [Surligneur][15].
* Utilisez la méthode [Highlight][16] de la classe [Index][17] pour mettre en surbrillance les résultats de la recherche.

Le code suivant génère la sortie HTML avec les résultats de recherche en surbrillance à l'aide de C#.

```
string indexFolder =    @"indexPath/GroupDocs/index/";
string documentFolder = @"documentPath/GroupDocs/source/";
string query = "draw";

// Créer un index dans le dossier spécifié et ajouter le dossier de documents à l'index
Index index = new Index(indexFolder);
index.Add(documentFolder);

// Rechercher le mot de la requête
SearchResult result = index.Search(query);

// Mettre en surbrillance toutes les occurrences dans le texte
for (int i = 0; i < result.DocumentCount; i++)
{
    FoundDocument document = result.GetFoundDocument(i);
                    
    string path = indexFolder + "Highlighted-"+ i +".html";
    OutputAdapter outputAdapter = new FileOutputAdapter(path); 
    Highlighter highlighter = new HtmlHighlighter(outputAdapter); 
    index.Highlight(document, highlighter);
}
```

En sortie, nous obtiendrons plusieurs fichiers HTML. Chaque fichier affichera le contenu d'un document différent (par exemple, excel.xlsx, source.docx, cible.docx) avec le terme/mot de recherche en surbrillance. Vous trouverez ci-dessous la sortie HTML en surbrillance d'un fichier DOCX.



{{< figure align=center src="images/highlight-text-search-result.jpg" alt="Mettre en surbrillance les résultats de la recherche en texte intégral dans le contenu">}}


## Obtenez une licence API gratuite {#Get-a-Free-API-License}

Vous pouvez [obtenir une licence temporaire gratuite][18] afin d'utiliser l'API sans les limitations d'évaluation.

## Conclusion

Dans cet article, nous avons appris à rechercher du texte dans plusieurs documents d'un dossier à l'aide de C#. En outre, nous avons discuté de la manière de mettre en surbrillance par programmation le texte des résultats de recherche au format HTML.

Vous pouvez en savoir plus sur l'API en utilisant [documentation][19]. De nombreux autres exemples sont disponibles sur [GitHub][20]. Pour toute question, contactez-nous via le [forum][21].

## Voir également

* [Créer une solution de recherche en texte intégral en Java][22]
* [Rechercher des synonymes de mots à l'aide de C#][23]
* [Rechercher des synonymes dans plusieurs fichiers à l'aide de C#][24]
* [Rechercher et remplacer du texte dans un PDF à l'aide de C#][25]
* [Rechercher et remplacer des mots dans des documents Word à l'aide de C#][26]







[1]: https://blog.groupdocs.com/2021/06/03/build-your-full-text-search-solution-in-csharp/
[2]: #full-text-search-dotnet-api
[3]: #full-text-search-in-csharp
[4]: #perform-search-in-csharp
[5]: #highlight-search-results-in-csharp
[6]: https://products.groupdocs.com/search/net
[7]: https://docs.groupdocs.com/search/net/supported-document-formats/
[8]: https://downloads.groupdocs.com/search
[9]: https://www.nuget.org/packages/groupdocs.search
[10]: https://apireference.groupdocs.com/search/net/groupdocs.search/index
[11]: https://apireference.groupdocs.com/search/net/groupdocs.search/index/methods/search/index
[12]: https://apireference.groupdocs.com/search/net/groupdocs.search/index
[13]: https://apireference.groupdocs.com/search/net/groupdocs.search/index
[14]: https://apireference.groupdocs.com/search/net/groupdocs.search/index/methods/search/index
[15]: https://apireference.groupdocs.com/search/net/groupdocs.search.highlighters/highlighter
[16]: https://apireference.groupdocs.com/search/net/groupdocs.search/index/methods/highlight/index
[17]: https://apireference.groupdocs.com/search/net/groupdocs.search/index
[18]: https://purchase.groupdocs.com/temporary-license
[19]: https://docs.groupdocs.com/search/
[20]: https://github.com/groupdocs-search
[21]: https://forum.groupdocs.com/
[22]: https://blog.groupdocs.com/2021/08/07/build-full-text-search-solution-in-java/
[23]: https://blog.groupdocs.com/2021/09/14/find-synonyms-of-words-using-csharp/
[24]: https://blog.groupdocs.com/2021/09/17/find-synonyms-in-multiple-files-using-csharp/
[25]: https://blog.groupdocs.com/2022/02/19/find-and-replace-text-in-pdf-using-csharp/
[26]: https://blog.groupdocs.com/2022/02/15/find-and-replace-text-in-word-using-csharp/


