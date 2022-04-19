---
title: "Rechercher du texte dans Word, Excel, PDF, ZIP et d'autres formats de document à l'aide de C# .NET"
date: Fri, 29 May 2020 09:25:45 +0000
draft: false
url: /fr/2020/05/29/search-text-in-word-excel-pdf-zip-document-formats-using-csharp-net/
author: 'Muhammad Sohail'
summary: "Nous avons souvent besoin d'une API de recherche en texte intégral qui permet à nos applications de rechercher dans des documents des informations particulières spécifiées sous forme de requête de recherche textuelle. Les documents peuvent être de n'importe quel format tel que Word (Doc, Docx), PDF, HTML, EPUB, Feuille de calcul (XLS, XLSX), Présentation (PPT, PPTX), images et vidéos."
tags: ['Full Text Search Csharp', 'Search text in multiple Documents', 'Search text in PDF Document', 'Search text in Word Document']
categories: ['GroupDocs.Search Product Family']
---



{{< figure align=center src="images/Search-Documents.png" alt="Recherche plein texte de documents">}}


Nous avons souvent besoin d'une API de recherche en texte intégral qui permet à nos applications de rechercher dans des documents des informations particulières spécifiées sous forme de requête de recherche textuelle. Les documents peuvent être de n'importe quel format tel que Word (Doc, Docx), PDF, HTML, EPUB, tableur (XLS, XLSX), présentation (PPT, PPTX), images et vidéos.

[GroupDocs.Search][1] est une puissante API de recherche en texte intégral qui vous permet de rechercher parmi [plus de 70 formats de documents][2] dans vos applications. Pour permettre une recherche instantanée parmi des milliers de documents, ils doivent être ajoutés à l'index.

## Pourquoi utiliser GroupDocs.Search en tant que développeur ?

* Aucun logiciel supplémentaire n'est requis pour rechercher dans les documents des formats pris en charge.
* Une grande variété d'options d'indexation et de recherche sont fournies pour répondre à toutes les exigences.
* Une large sélection de types de recherche est disponible dans les requêtes sous forme de texte ou d'objet.
* Des performances d'indexation et de recherche élevées sont obtenues grâce à des algorithmes et des structures de données uniques, des optimisations et une exécution multithread.
* Diverses façons de visualiser les résultats de la recherche dans le texte des documents sont prises en charge.

Veuillez consulter l'article [À propos des moteurs de recherche][3] pour savoir quelle place occupe l'API GroupDocs.Search dans la classification des moteurs de recherche.

## Installation

GroupDocs.Search pour .NET est hébergé sur [NuGet][4] et peut facilement être installé à l'aide du gestionnaire de packages NuGet. Vous pouvez également télécharger la DLL de l'API à partir de la section [Téléchargements][5].

## Rechercher dans les documents Office à l'aide de C #

Les étapes suivantes expliquent comment rechercher des mots ou des phrases dans plusieurs documents (Word, Excel, PDF et autres formats de document).

* **Créer un nouvel index** : tout d'abord, vous devez créer un index. Un index peut être créé en mémoire ou sur disque. Un index créé en mémoire ne peut pas être sauvegardé après avoir quitté votre programme. En revanche, un index créé sur disque peut être chargé ultérieurement pour continuer à fonctionner. Les détails sur la création d'un index sont décrits dans la section [Création d'un index][6].
* **S'abonner aux événements d'index :** Après avoir créé un index, vous devez ajouter des documents à l'index pour l'indexation. L'indexation des documents peut réussir ou échouer pour diverses raisons, par exemple, en raison d'erreurs de lecture du disque ou de la présence d'un mot de passe pour accéder à un document. Pour recevoir des informations sur les erreurs d'indexation, vous pouvez vous abonner à l'événement ErrorOccurred. Pour travailler avec des événements, consultez la section [Rechercher des événements dans l'index][7].
* **Documents indexés** : l'indexation des documents peut être effectuée de manière synchrone ou asynchrone. L'indexation synchrone signifie qu'un thread qui a démarré le processus d'indexation sera occupé jusqu'à ce que l'opération soit terminée. Cependant, le plus souvent, il est nécessaire d'effectuer l'indexation de manière asynchrone, avec la possibilité d'exécuter d'autres tâches dans le thread qui a lancé l'opération. Une description détaillée de tous les aspects du processus d'indexation est fournie dans la section [Indexation][8].
* **Effectuer une recherche :** Lorsque les documents sont indexés, l'index est prêt à traiter les requêtes de recherche. Les types de requêtes de recherche suivants sont pris en charge : simples, approximatives, sensibles à la casse, booléennes, syntagmatiques, à facettes, avec des caractères génériques, etc. La description des requêtes de recherche de différents types est présentée dans la section [Recherche][9].
* **Utiliser les résultats de la recherche :** Lorsqu'une recherche est terminée, vous devez d'une manière ou d'une autre interpréter un résultat. Le résultat peut être représenté par une simple liste de documents trouvés, ou les mots et expressions trouvés peuvent être mis en évidence dans le texte du document. Pour plus d'informations sur le traitement des résultats de recherche, voir [Résultats de la recherche][10].

```
string indexFolder = @"/Users/muhammadsohailismail/MyIndex/"; // Specify the path to the index folder
string documentsFolder = @"/Users/muhammadsohailismail/MyDocuments/"; // Specify the path to a folder containing documents to search

// a) Create new index or
// b) Open existing index
Index index = new Index(indexFolder);

// c) Subscribe to index events
index.Events.ErrorOccurred += (sender, args) =>
{
    Console.WriteLine(args.Message); // Writing error messages to the console
};

// d) Add files synchronously
index.Add(documentsFolder); // Synchronous indexing documents from the specified folder

// f) Perform search
string query = "Worthy"; // Specify a search query
SearchResult result = index.Search(query); // Searching in the index

// g) Use search results
// Printing the result
Console.WriteLine("Documents found: " + result.DocumentCount);
Console.WriteLine("Total occurrences found: " + result.OccurrenceCount);
for (int i = 0; i < result.DocumentCount; i++)
{
    FoundDocument document = result.GetFoundDocument(i);
    Console.WriteLine("\\tDocument: " + document.DocumentInfo.FilePath);
    Console.WriteLine("\\tOccurrences: " + document.OccurrenceCount);
}

// Highlight occurrences in text
if (result.DocumentCount > 0)
{
    FoundDocument document = result.GetFoundDocument(0); // Getting the first found document
    string path = @"/Users/muhammadsohailismail/Output/Highlighted.html";
    OutputAdapter outputAdapter = new FileOutputAdapter(path); // Creating the output adapter to a file
    HtmlHighlighter highlighter = new HtmlHighlighter(outputAdapter); // Creating the highlighter object
    index.Highlight(document, highlighter); // Generating output HTML formatted document with highlighted search results

    Console.WriteLine();
    Console.WriteLine("Generated HTML file can be opened with Internet browser.");
    Console.WriteLine("The file can be found by the following path:");
    Console.WriteLine(Path.GetFullPath(path));
}
```

Le code ci-dessus génère la sortie suivante et [fichier HTML][11].



{{< figure align=center src="images/Output.jpg" alt="">}}


## Rechercher dans les champs de documents à l'aide de C #

La recherche à facettes filtre les résultats de la recherche en définissant des noms de champs de document valides à rechercher. La recherche à facettes vous permet de rechercher uniquement dans certains champs de documents, par exemple, uniquement dans le champ de contenu ou dans le champ de nom de fichier. Un exemple simple de recherche à facettes est présenté ci-dessous avec des requêtes sous forme de texte et d'objet.

```
string indexFolder = @"c:\\MyIndex\\";
string documentsFolder = @"c:\\MyDocuments\\";
 
// Creating an index in the specified folder
Index index = new Index(indexFolder);
 
// Indexing documents from the specified folder
index.Add(documentsFolder);
 
// Search in the content field with text query
SearchResult result1 = index.Search("content: Einstein");
 
// Search in the content field with object query
SearchQuery wordQuery = SearchQuery.CreateWordQuery("Einstein");
SearchQuery fieldQuery = SearchQuery.CreateFieldQuery(CommonFieldNames.Content, wordQuery);
SearchResult result2 = index.Search(fieldQuery);
```

### Utilisation de champs spécifiques au format

Pour chaque format de document, il existe des champs standards qui peuvent être présents dans les documents de ce type. La bibliothèque fournit les classes suivantes contenant des constantes avec les noms des champs de document standard : [EpubFieldNames][12], [FictionBookFieldNames][13], [MailFieldNames][14], [PresentationFieldNames][15], [SpreadsheetFieldNames][16] , [WordsFieldNames][17].

Il existe également des champs qui peuvent être présents dans des documents de tout type. Les noms de ces champs sont représentés dans la classe [CommonFieldNames][18].

Un exemple d'utilisation de noms de champs standard de documents est présenté dans l'exemple suivant.

```
string indexFolder = @"c:\\MyIndex\\";
string documentsFolder = @"c:\\MyDocuments\\";
 
// Creating an index in the specified folder
Index index = new Index(indexFolder);
 
// Indexing documents from the specified folder
index.Add(documentsFolder);
 
// Search in the content field with text query
string query1 = WordsFieldNames.Company + ": Dycum";
SearchResult result1 = index.Search(query1);
 
// Search in the content field with object query
SearchQuery wordQuery = SearchQuery.CreateWordQuery("Dycum");
SearchQuery fieldQuery = SearchQuery.CreateFieldQuery(WordsFieldNames.Company, wordQuery);
SearchResult result2 = index.Search(fieldQuery);
```

Des informations détaillées sur la recherche à facettes sont présentées sur la page [Recherche à facettes][19].

## Conclusion

Cet article a expliqué comment rechercher dans des documents (DOCX, PDF, Excel, fichiers texte) des informations particulières en C#. Il a également expliqué comment effectuer une recherche dans les champs de documents. GroupDocs.Search contient plusieurs autres fonctionnalités, veuillez consulter la [documentation][20] pour en savoir plus.







[1]: https://products.groupdocs.com/search
[2]: https://docs.groupdocs.com/display/searchnet/Supported+Document+Formats
[3]: https://docs.groupdocs.com/display/searchnet/About+Search+Engines
[4]: https://www.nuget.org/packages/GroupDocs.Search/
[5]: https://downloads.groupdocs.com/search/net
[6]: https://docs.groupdocs.com/display/searchnet/Creating+an+index
[7]: https://docs.groupdocs.com/display/searchnet/Search+index+events
[8]: https://docs.groupdocs.com/display/searchnet/Indexing
[9]: https://docs.groupdocs.com/display/searchnet/Searching
[10]: https://docs.groupdocs.com/display/searchnet/Search+results
[11]: https://www.dropbox.com/s/ioztnalgq2fjqcs/Highlighted.html?dl=0
[12]: https://apireference.groupdocs.com/net/search/groupdocs.search.options/epubfieldnames
[13]: https://apireference.groupdocs.com/net/search/groupdocs.search.options/fictionbookfieldnames
[14]: https://apireference.groupdocs.com/net/search/groupdocs.search.options/mailfieldnames
[15]: https://apireference.groupdocs.com/net/search/groupdocs.search.options/presentationfieldnames
[16]: https://apireference.groupdocs.com/net/search/groupdocs.search.options/spreadsheetfieldnames
[17]: https://apireference.groupdocs.com/net/search/groupdocs.search.options/wordsfieldnames
[18]: https://apireference.groupdocs.com/net/search/groupdocs.search.options/commonfieldnames
[19]: https://docs.groupdocs.com/display/searchnet/Faceted+search
[20]: https://docs.groupdocs.com/display/searchnet/Developer+Guide


