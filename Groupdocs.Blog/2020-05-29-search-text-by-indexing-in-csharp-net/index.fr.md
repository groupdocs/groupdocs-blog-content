---
title: "Indexation de texte et recherche dans vos répertoires à l'aide de C#"
date: Fri, 29 May 2020 07:30:00 +0000
draft: false
url: /fr/2020/05/29/search-text-by-indexing-in-csharp-net/
author: 'Shoaib Khan'
summary: "À l'aide de l'API .NET, vous pouvez effectuer une recherche par parties et spécifier le nombre de threads de recherche en C#. Cette fonctionnalité sera plus utile lorsque vous recherchez du texte dans des index volumineux contenant des milliers de documents. De plus, vous pouvez maintenant obtenir l'heure de début et de fin, ainsi que le temps de recherche total pour obtenir les résultats de la recherche."
tags: ['search in chunk', 'search text in csharp', 'search text in folders in csharp', 'search text in parts', 'text searching using csharp']
categories: ['GroupDocs.Search Product Family']
---

À l'aide de l'API .NET, vous pouvez effectuer une recherche par parties et spécifier le nombre de threads de recherche en C#. Cette fonctionnalité sera plus utile lorsque vous recherchez du texte dans des index volumineux contenant des milliers de documents. De plus, vous pouvez maintenant obtenir l'heure de début et de fin, ainsi que le temps de recherche total pour obtenir les résultats de la recherche.

L'extrait de code suivant montre comment créer un index, puis rechercher du texte dans des morceaux du dossier mentionné en C# à l'aide de [GroupDocs.Search for .NET][1]. Pour utiliser les meilleures performances et les fonctionnalités mises à jour, je vous recommande d'[installer][2] et d'utiliser la dernière version de l'API.

## Rechercher du texte par indexation en C#

L'exemple suivant montre comment effectuer la recherche par pièces/morceaux.

* Créez l'[Index][3] avec votre dossier d'index.
* [Ajoutez][4] votre dossier de documents dans l'index créé.
* Définissez [Search Option][5] et définissez votre [IsChunkSearch][6] sur true pour la recherche par morceau/parties
* Appelez la méthode [Search][7] de votre index en fournissant votre requête de recherche et vos options de recherche.
* Maintenant, dans le résultat, vous pouvez parcourir chaque segment en utilisant [Search Next][8] et en le passant [Chunk Search Token][9] comme paramètre.

```
string indexFolder = @"c:\\MyIndex\\";
string documentsFolder = @"c:\\MyDocuments\\";
string query = "Einstein";
// Creating an index in the specified folder
Index index = new Index(indexFolder);
// Indexing documents from the specified folder
index.Add(documentsFolder);
// Creating a search options instance
SearchOptions options = new SearchOptions();
options.IsChunkSearch = true; // Enabling the search by chunks
// Starting the search by chunks
SearchResult result = index.Search(query, options);
Console.WriteLine("Document count: " + result.DocumentCount);
Console.WriteLine("Occurrence count: " + result.OccurrenceCount);
// Continuing the search by chunks
while (result.NextChunkSearchToken != null)
{
    result = index.SearchNext(result.NextChunkSearchToken);
    Console.WriteLine("Document count: " + result.DocumentCount);
    Console.WriteLine("Occurrence count: " + result.OccurrenceCount);
}
```

Pour toute suggestion, confusion ou requête liée à [.NET Search API][10], vous pouvez utiliser le [forum][11] pour une réponse rapide. Vous pouvez rapidement créer un fil de discussion pour partager vos réflexions.

## Voir également

* [Rechercher et remplacer du texte dans un PDF à l'aide de C#][12]
* [Rechercher et remplacer des mots dans des documents Word à l'aide de C#][13]







[1]: https://products.groupdocs.com/search/net
[2]: https://www.nuget.org/packages/GroupDocs.Search/
[3]: https://apireference.groupdocs.com/net/search/groupdocs.search/index
[4]: https://apireference.groupdocs.com/search/net/groupdocs.search/index/methods/add
[5]: https://apireference.groupdocs.com/search/net/groupdocs.search.options/searchoptions
[6]: https://apireference.groupdocs.com/search/net/groupdocs.search.options/searchoptions/properties/ischunksearch
[7]: https://apireference.groupdocs.com/net/search/groupdocs.search/index/methods/search/index
[8]: https://apireference.groupdocs.com/search/net/groupdocs.search/index/methods/searchnext
[9]: https://apireference.groupdocs.com/search/net/groupdocs.search.results/searchresult/properties/nextchunksearchtoken
[10]: https://products.groupdocs.com/search/net
[11]: https://forum.groupdocs.com/c/search
[12]: https://blog.groupdocs.com/2022/02/19/find-and-replace-text-in-pdf-using-csharp/
[13]: https://blog.groupdocs.com/2022/02/15/find-and-replace-text-in-word-using-csharp/


