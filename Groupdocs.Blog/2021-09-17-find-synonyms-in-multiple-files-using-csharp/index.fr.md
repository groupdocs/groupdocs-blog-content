---
title: "Rechercher des synonymes dans plusieurs fichiers à l'aide de C#"
date: Fri, 17 Sep 2021 10:57:00 +0000
draft: false
url: /fr/2021/09/17/trouver-des-synonymes-dans-plusieurs-fichiers-en-utilisant-csharp/
author: 'Shoaib Khan'
summary: "Dans un autre article, nous avons vu ce que sont les synonymes et comment obtenir tous les synonymes de n'importe quel mot. Et si on retrouvait ces synonymes dans différents documents. Cet article vous expliquera comment rechercher les synonymes d'une requête spécifique (mot) dans plusieurs fichiers à l'aide de C#."
tags: ['Find Synonyms', 'Find Synonyms in CSharp', 'Search Synonyms', 'Search Synonyms in CSharp', 'Search Synonyms in Files']
categories: ['GroupDocs.Search Product Family']
---

Dans un autre article, nous avons vu que sont les synonymes, et [comment obtenir tous les synonymes de n'importe quel mot][1]. Qu'en est-il de trouver ces synonymes dans différents documents ? Cet article vous expliquera comment rechercher les synonymes d'une requête spécifique (mot) dans plusieurs fichiers à l'aide de C#.

Les sujets suivants seront abordés ci-dessous :

* [API .NET - Recherche de synonymes][2]
* [Rechercher des synonymes dans des documents à l'aide de C#][3]
* [Présenter les résultats de la recherche de synonymes à l'aide de C#][4]
* [Code complet - Rechercher et imprimer les résultats de la recherche de synonymes][5]

## API .NET pour la recherche de synonymes dans plusieurs fichiers {#synonym-search-dotnet-api}

[GroupDocs.Search][6] fournit l'API .NET qui permet de rechercher n'importe quel mot et ses synonymes dans plusieurs fichiers du dossier spécifié. J'utiliserai cette API dans les exemples présentés de cet article. Il vous permet de [rechercher parmi une grande liste de formats de documents][7]. En plus de rechercher les synonymes, GroupDocs.Search pour .NET prend également en charge d'autres techniques de recherche, notamment :

* Recherche floue
* Recherche sensible à la casse
* Recherche d'homophones
* Recherche d'expressions régulières
* Recherche par joker

Vous pouvez télécharger le programme d'installation **DLLs** ou **MSI** à partir de la [section téléchargements][8] ou installer l'API dans votre application .NET via [NuGet][9].

```
PM> Install-Package GroupDocs.Search
```

## Trouver des synonymes dans plusieurs fichiers à l'aide de C # {#synonyms-in-different-files}

Les étapes montrent comment rechercher des synonymes (mots ayant des significations similaires) dans les fichiers d'un dossier à l'aide de C#.

* Définissez la requête de recherche, le dossier d'index et le dossier du document.
* Créer un index avec un dossier d'index défini à l'aide de la classe [Index][10].
* Ajouter le dossier du document à l'index.
* Créez les [SearchOptions][11] et définissez [UseSynonymSearch][12] sur true.
* Appelez la méthode [Search][13] de la classe Index et transmettez les options de requête et de recherche.
* Pour imprimer le résumé, utilisez les propriétés du [SearchResult][14] récupéré.

Le code source montre comment trouver tous les synonymes dans tous les fichiers d'un dossier à l'aide de C#

```
// Rechercher des synonymes dans plusieurs fichiers et dossiers à l'aide de C#
string query = "make";
string indexFolder = @"path\indexFolder";
string documentsFolder = @"path\documentsFolder";

// Création d'un index dans le dossier spécifié
Index index = new Index(indexFolder);
index.Add(documentsFolder);

// Création d'un objet d'options de recherche
SearchOptions options = new SearchOptions();
options.UseSynonymSearch = true; // Enabling Synonym Search

// Rechercher le mot "faire"
// En plus du mot 'make', les synonymes "do, cause, get, ..." seront également recherchés
SearchResult result = index.Search(query, options);
Console.WriteLine("Query: " + query);
Console.WriteLine("Documents: " + result.DocumentCount);
Console.WriteLine("Occurrences: " + result.OccurrenceCount);
```

```
Query: **make**
Documents: 2
Occurrences: 22
```

## Impression des résultats de la recherche de synonymes à l'aide de C# {#print-synonym-search}

Les étapes suivantes impriment les résultats en détail après avoir obtenu tous les synonymes et leur nombre d'occurrences dans chaque document.

* Parcourez les résultats de recherche qui sont récupérés à l'aide du code ci-dessus.
* Obtenez chaque [FoundDocument][15] en utilisant la méthode [GetFoundDocument][16].
* Imprimer les propriétés respectives de chaque FoundDocument.
* Parcourez les [FoundFields][17] dans chaque FoundDocument pour obtenir [Found Document Field][18].
* À partir de chaque FoundDocumentField, vous pouvez obtenir ses termes et ses occurrences dans chaque document.

Le code source suivant imprime les résultats de la recherche de synonymes avec le nombre d'occurrences de chaque terme recherché à l'aide de C#.

```
// Impression des résultats de la recherche de synonymes en C#
Console.WriteLine("Query: " + query);
Console.WriteLine("Documents: " + result.DocumentCount);
Console.WriteLine("Total occurrences: " + result.OccurrenceCount + "\n");
for (int i = 0; i < result.DocumentCount; i++)
{
    FoundDocument document = result.GetFoundDocument(i);
    Console.WriteLine("Document: " + document.DocumentInfo.FilePath);
    Console.WriteLine("Occurrences: " + document.OccurrenceCount);
    for (int j = 0; j < document.FoundFields.Length; j++)
    {
        FoundDocumentField field = document.FoundFields[j];
        Console.WriteLine("\tField: " + field.FieldName);
        Console.WriteLine("\tOccurrences: " + document.OccurrenceCount);
        // Printing found terms
        if (field.Terms != null)
        {
            for (int k = 0; k < field.Terms.Length; k++)
            {
                Console.WriteLine("\t\t" + field.Terms[k].PadRight(20) + field.TermsOccurrences[k]);
            }
        }
    }
}
```

```
Query: **make**
Documents: 2
Total occurrences: 22

Document: C:/documents/sample.docx
Occurrences: 6
    Field: content
    Occurrences: 6
        make             1
        get                 2
        cause            1
        do                  2
Document: C:/documents/sample.txt
Occurrences: 16
    Field: content
    Occurrences: 16
        get                  4
        cause             1
        do                  11
```

## Synonymes de recherche et résultats d'impression à l'aide de C# - Code complet {#search-and-print-synonyms-code}

Voici le code source complet qui trouve d'abord tous les synonymes en fonction de la requête fournie, puis imprime toutes les occurrences de tous les synonymes dans chaque document de ce dossier à l'aide de C#.

```
// Rechercher des synonymes dans plusieurs fichiers et dossiers et imprimer les résultats à l'aide de C#
string query = "make";
string indexFolder = @"path\indexFolder";
string documentsFolder = @"path\documentsFolder";

// Création d'un index dans le dossier spécifié
Index index = new Index(indexFolder);
// Indexation de documents à partir du dossier spécifié
index.Add(documentsFolder);

// Création d'un objet d'options de recherche
SearchOptions options = new SearchOptions();
options.UseSynonymSearch = true; // Enabling synonym search

// Rechercher le mot "faire"
// En plus du mot 'make', les mots "do, cause, get, ..." seront également recherchés
SearchResult result = index.Search(query, options);

// Impression du résultat
Console.WriteLine("Query: " + query);
Console.WriteLine("Documents: " + result.DocumentCount);
Console.WriteLine("Total occurrences: " + result.OccurrenceCount + "\n");
for (int i = 0; i < result.DocumentCount; i++)
{
    FoundDocument document = result.GetFoundDocument(i);
    Console.WriteLine("Document: " + document.DocumentInfo.FilePath);
    Console.WriteLine("Occurrences: " + document.OccurrenceCount);
    for (int j = 0; j < document.FoundFields.Length; j++)
    {
        FoundDocumentField field = document.FoundFields[j];
        Console.WriteLine("\tField: " + field.FieldName);
        Console.WriteLine("\tOccurrences: " + document.OccurrenceCount);
        // Printing found terms
        if (field.Terms != null)
        {
            for (int k = 0; k < field.Terms.Length; k++)
            {
                Console.WriteLine("\t\t" + field.Terms[k].PadRight(20) + field.TermsOccurrences[k]);
            }
        }
    }
}
```

## Conclusion

Pour conclure, vous avez appris à trouver les mots spécifiques ainsi que leurs synonymes dans plusieurs documents du dossier spécifié à l'aide de C#. Vous pouvez essayer de développer votre propre application .NET pour rechercher n'importe quel mot et ses synonymes dans plusieurs fichiers.

En savoir plus [sur l'API .NET Search Automation][19] dans la documentation. Pour découvrir les fonctionnalités, vous pouvez consulter des exemples sur le référentiel [GitHub][20]. Contactez-nous pour toute question via le [forum][21].

## Voir également

* [Rechercher des synonymes de mots à l'aide de C#][22]
* [Créez votre solution de recherche en texte intégral en C#][23]
* [Indexation de texte et recherche dans vos répertoires à l'aide de C#][24]







[1]: https://blog.groupdocs.com/2021/09/14/find-synonyms-of-words-using-csharp
[2]: #synonym-search-dotnet-api
[3]: #synonyms-in-different-files
[4]: #print-synonym-search
[5]: #search-and-print-synonyms-code
[6]: https://products.groupdocs.com/search/
[7]: https://docs.groupdocs.com/search/net/supported-document-formats/
[8]: https://downloads.groupdocs.com/search
[9]: https://www.nuget.org/packages/groupdocs.search
[10]: https://apireference.groupdocs.com/search/net/groupdocs.search/index
[11]: https://apireference.groupdocs.com/search/net/groupdocs.search.options/searchoptions
[12]: https://apireference.groupdocs.com/search/net/groupdocs.search.options/searchoptions/properties/usesynonymsearch
[13]: https://apireference.groupdocs.com/search/net/groupdocs.search/index/methods/search/index
[14]: https://apireference.groupdocs.com/search/net/groupdocs.search.results/searchresult
[15]: https://apireference.groupdocs.com/search/net/groupdocs.search.results/founddocument
[16]: https://apireference.groupdocs.com/search/net/groupdocs.search.results/searchresult/methods/getfounddocument
[17]: https://apireference.groupdocs.com/search/net/groupdocs.search.results/founddocument/properties/foundfields
[18]: https://apireference.groupdocs.com/search/net/groupdocs.search.results/founddocumentfield
[19]: https://docs.groupdocs.com/search/net/
[20]: https://github.com/groupdocs-search
[21]: https://forum.groupdocs.com/
[22]: https://blog.groupdocs.com/2021/09/14/find-synonyms-of-words-using-csharp
[23]: https://blog.groupdocs.com/2021/06/03/build-your-full-text-search-solution-in-csharp/
[24]: https://blog.groupdocs.com/2020/05/29/search-text-by-indexing-in-csharp-net/


