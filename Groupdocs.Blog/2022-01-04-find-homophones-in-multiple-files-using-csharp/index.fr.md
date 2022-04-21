---
title: "Rechercher des homophones dans plusieurs fichiers à l'aide de C#"
date: Tue, 04 Jan 2022 10:54:00 +0000
draft: false
url: /fr/2022/01/04/trouver-des-homophones-dans-plusieurs-fichiers-en-utilisant-csharp/
author: 'Shoaib Khan'
summary: "Les mots qui se prononcent de la même manière mais dont le sens ou l'orthographe sont différents sont des **homophones**. Alors que les mots qui s'épellent de la même manière, mais qui diffèrent par leur sens ou leur prononciation sont des ** homographes **. Les **homonymes** peuvent être homophones ou homographes ; ou les deux. Ne confondons pas et automatisons-le. Dans cet article, vous apprendrez **comment rechercher des homophones dans plusieurs documents à l'aide de C#**.

Les sujets suivants seront abordés dans cet article :

* API .NET - Recherche d'homophones
* Trouver des homophones dans des documents à l'aide de C#
* Gérer le dictionnaire homophone"
tags: ['Find Homophones', 'Find Homophones in CSharp', 'Find Homophones in Files', 'Homophones']
categories: ['GroupDocs.Search Product Family']
---

Les mots qui se prononcent de la même manière mais dont le sens ou l'orthographe sont différents sont des **homophones**. Alors que les mots qui s'épellent de la même manière, mais qui diffèrent par leur sens ou leur prononciation sont des ** homographes **. Les **homonymes** peuvent être homophones ou homographes ; ou les deux. Ne confondons pas et automatisons-le. Dans cet article, vous apprendrez **comment rechercher des homophones dans plusieurs documents à l'aide de C#**.



{{< figure align=center src="images/Search-Homophones-in-Files.jpg" alt="Rechercher des homophones dans des fichiers à l'aide de GroupDocs">}}


Les sujets suivants seront abordés ci-dessous :

* [.NET API - Homophone Search](#homophone-search-dotnet-api)
* [Rechercher des homophones dans des documents à l'aide de C#](#homophone-in-different-files)
* [Jouer avec le résultat de la recherche d'homophones](#print-homophone-search)

## API .NET pour la recherche d'homophones dans plusieurs fichiers {#homophone-search-dotnet-api}

[GroupDocs.Search](https://products.groupdocs.com/search/) présente l'API .NET ([GroupDocs.Search pour .NET](https://products.groupdocs.com/search/net/)) qui permet de rechercher des mots et leurs homophones dans plusieurs fichiers du dossier spécifié. Nous utiliserons cette API dans les exemples de cet article. Il peut rechercher le contenu de différents formats différents. En plus de trouver les homophones, l'API prend en charge de nombreuses autres façons de rechercher selon les besoins. Certaines des techniques de recherche prises en charge sont les suivantes :

* Recherche de synonymes
* Recherche de phrases
* Recherche floue
* Recherche sensible à la casse
* Recherche d'expressions régulières
* Recherche par joker

Vous pouvez télécharger le programme d'installation **DLLs** ou **MSI** à partir de la [section téléchargements](https://downloads.groupdocs.com/search) ou installer l'API dans votre application .NET via [NuGet](https://www.nuget.org/packages/groupdocs.search).

```
PM> Install-Package GroupDocs.Search
```

## Trouver des homophones dans plusieurs fichiers à l'aide de C# {#homophone-in-different-files}

Les étapes suivantes expliquent comment nous pouvons rechercher des homophones (mots avec un son/une prononciation similaires) dans les fichiers d'un dossier à l'aide de C#.

* Définissez la requête de recherche, un dossier d'indexation et le dossier contenant vos fichiers.
* Créez [Index](https://apireference.groupdocs.com/search/net/groupdocs.search/index) avec le dossier d'index défini.
* Ajouter le dossier du document à l'index créé.
* Définissez les [SearchOptions](https://apireference.groupdocs.com/search/net/groupdocs.search.options/searchoptions) et définissez le [UseHomophoneSearch](https://apireference.groupdocs.com/search/net/groupdocs.search.options/searchoptions/properties/usehomophonesearch) sur true.
* Recherchez tous les homophones en appelant la méthode [Search](https://apireference.groupdocs.com/search/net/groupdocs.search/index/methods/search/index) avec les options de requête et de recherche.
* Utilisez le résumé en utilisant les propriétés du [SearchResult](https://apireference.groupdocs.com/search/net/groupdocs.search.results/searchresult) récupéré.

Le code source C# suivant trouve tous les homophones dans tous les fichiers d'un dossier défini. De plus, vous pouvez [gérer votre dictionnaire d'homophones](https://docs.groupdocs.com/search/net/homophone-dictionary/).

```
// Rechercher des homophones dans plusieurs fichiers et dossiers à l'aide de C#
string query = "right";
string indexFolder = @"path\indexFolder";
string documentsFolder = @"path\documentsFolder";

// Création d'un index dans le dossier spécifié
Index index = new Index(indexFolder);
index.Add(documentsFolder);

// Création d'un objet d'options de recherche
SearchOptions options = new SearchOptions()
{
    UseHomophoneSearch = true // Enabling Homophone Search
}; 

// Rechercher le mot "droit"
// En plus du mot 'right', les mots "rite, wright, write, ..." seront également recherchés
SearchResult result = index.Search(query, options);
Console.WriteLine("Query: " + query);
Console.WriteLine("Documents: " + result.DocumentCount);
Console.WriteLine("Occurrences: " + result.OccurrenceCount);
```

La sortie du code ci-dessus est la suivante :

```
Query: right
Documents: 2
Occurrences: 17
```

## Impression des résultats de recherche d'homophones à l'aide de C# {#print-homophone-search}

Suivez les étapes ci-dessous après avoir obtenu tous les homophones et leur nombre d'occurrences dans chaque document pour présenter les résultats de la recherche d'homophones.

* Parcourez les résultats de recherche d'homophones qui sont récupérés plus tôt.
* Obtenez chaque document en tant que [FoundDocument](https://apireference.groupdocs.com/search/net/groupdocs.search.results/founddocument) en utilisant [GetFoundDocument()](https://apireference.groupdocs.com/search/net/groupdocs.search.results/searchresult/methods/getfounddocument).
* Utilisez les propriétés de chaque FoundDocument selon vos besoins.
* Maintenant, parcourez les [FoundFields](https://apireference.groupdocs.com/search/net/groupdocs.search.results/founddocument/properties/foundfields) de FoundDocument pour obtenir [FoundDocumentField](https://apireference.groupdocs.com/search/net/groupdocs.search.results/founddocumentfield).
* Enfin, à partir de chaque FoundDocumentField, obtenez ses termes et leurs occurrences dans chaque document.

Le code source C# suivant imprime les résultats de la recherche d'homophones avec le nombre d'occurrences de chaque terme recherché.

```
// Impression des résultats de recherche d'homophones en C#
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

Voici la sortie de l'exemple de code ci-dessus.

```
Query: right
Documents: 2
Total occurrences: 17

Document: C:/documents/sample.docx
Occurrences: 11
    Field: content
    Occurrences: 11
        right             3
        rite               4
        wright           1
        write             3
Document: C:/documents/sample.txt
Occurrences: 6
    Field: content
    Occurrences: 6
        right             4
        write             2
```

## Rechercher des homophones et des résultats d'impression à l'aide de C# - Code complet {#search-and-print-synonyms-code}

Le code C# suivant résume les étapes ci-dessus, il trouve d'abord tous les homophones en fonction de la requête, puis imprime toutes les occurrences de tous les homophones dans chaque document dans le dossier fourni.

```
// Recherchez des homophones dans plusieurs fichiers et dossiers, puis imprimez les résultats à l'aide de C#
string query = "right";
string indexFolder = @"path\indexFolder";
string documentsFolder = @"path\documentsFolder";

// Création d'un index dans le dossier spécifié
Index index = new Index(indexFolder);
// Indexation de documents à partir du dossier spécifié
index.Add(documentsFolder);

// Création d'un objet d'options de recherche
SearchOptions options = new SearchOptions()
{
    UseHomophoneSearch = true // Enabling Homophone Search
}; 

// Rechercher le mot "droit"
// En plus du mot 'right', les mots "rite, wright, write, ..." seront également recherchés
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

En résumé, vous avez appris à trouver les mots et leurs homophones à partir des multiples documents du dossier spécifié à l'aide de C#. Vous pouvez essayer de créer votre propre application .NET pour rechercher des homophones dans plusieurs fichiers à l'aide de **GroupDocs.Search for .NET**.

En savoir plus [sur l'API .NET Search Automation](https://docs.groupdocs.com/search/net/) dans la documentation. Pour découvrir les fonctionnalités, vous pouvez consulter les exemples disponibles sur le référentiel [GitHub](https://github.com/groupdocs-search). Contactez-nous pour toute question via le [forum](https://forum.groupdocs.com/).

## Voir également

* [Rechercher des synonymes de mots à l'aide de C#](https://blog.groupdocs.com/2021/09/14/find-synonyms-of-words-using-csharp)
* [Créez votre solution de recherche en texte intégral en C#](https://blog.groupdocs.com/2021/06/03/build-your-full-text-search-solution-in-csharp/)
* [Indexation de texte et recherche dans vos répertoires à l'aide de C#](https://blog.groupdocs.com/2020/05/29/search-text-by-indexing-in-csharp-net/)