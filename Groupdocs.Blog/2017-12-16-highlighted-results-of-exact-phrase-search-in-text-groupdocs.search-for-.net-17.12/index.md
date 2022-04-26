---
title: 'Highlighted Results of Exact Phrase Search in Text - GroupDocs.Search for .NET 17.12'
date: Sat, 16 Dec 2017 02:24:40 +0000
draft: false
url: /2017/12/16/highlighted-results-of-exact-phrase-search-in-text-groupdocs.search-for-.net-17.12/
author: 'Usman Aziz'
summary: ''
tags: ['.NET Text Searching API', 'c# search documents', 'search API for .NET']
categories: ['GroupDocs.Search for .NET', 'GroupDocs.Search for .NET Releases', 'GroupDocs.Search Product Family']
---

[![GroupDocs.Search for .NET](http://blog.groupdocs.com/wp-content/uploads/sites/4/2017/04/groupdocs-search-net.png)](https://www.groupdocs.com/products/search/net) We are pleased to announce the release of version 17.12 of [GroupDocs.Search for .NET](https://products.groupdocs.com/search/net). **GroupDocs.Search for .NET 17.12** has come with 4 enhancements. We have introduced the feature of getting highlighted results of exact phrase search in text. Furthermore, we have improved the calculation of relevance of search results as well as redesigned the syntax of the search query. We would recommend you to enhance your applications using this latest version.

# .NET Search API - Enhancements

**GroupDocs.Search for .NET** includes following enhancements in version 17.12.

## Highlighted results of exact phrase search in text {#GroupDocs.Searchfor.NET17.12ReleaseNotes-Implementationofhighlightedresultsforexactphrasesearchintext}In this enhancement, generating HTML-formatted text with highlighted found terms is implemented for the results of exact phrase search. Following code snippet demonstrates this feature.```
string indexFolder = @"c:\MyIndex" ;
string documentsFolder = @"c:\MyDocuments" ;

// Creating index
Index index = new Index(indexFolder);

// Indexing documents
index.AddToIndex(documentsFolder);

// Searching for phrase 'cumulative distribution function'
SearchResults results = index.Search("\"cumulative distribution function\"");

// Generating HTML-formatted text for the first document directly to the file 'HighlightedResults.html'
index.HighlightInText("HighlightedResults.html", results[0]);
```

## Improved calculation of relevance of search results {#GroupDocs.Searchfor.NET17.12ReleaseNotes-Improvedcalculationofrelevanceofsearchresults}In this enhancement, the way of calculating the relevance of search results has been changed. Now the following formula is used to calculate the relevance of each found document: **R = O / T**, where **R** is relevance; **O** is occurrence count in the document; **T** is total word count in document. Following code sample demonstrates its usage.```
// Implementing comparer
public class Comparer : IComparer
{
    public int Compare(DocumentResultInfo x, DocumentResultInfo y)
    {
        // Compare y and x in reverse order
        return y.Relevance.CompareTo(x.Relevance);
    }
}
 
...
 
string indexFolder = @"c:\MyIndex";
string documentsFolder = @"c:\MyDocuments";
 
// Creating index
Index index = new Index(indexFolder);
 
// Indexing
index.AddToIndex(documentsFolder);
 
// Creating search parameters object
SearchParameters searchParameters = new SearchParameters();
// Enabling fuzzy search
searchParameters.FuzzySearch.Enabled = true;
// Setting maximum mistake count to 1
searchParameters.FuzzySearch.FuzzyAlgorithm = new TableDiscreteFunction(1);
 
// Searching for term 'database'
// Using fuzzy search allows to find the plural form of the term 'databases'
SearchResults searchResults = index.Search("database", searchParameters);
 
// Creating and filling array for sorting
DocumentResultInfo[] array = new DocumentResultInfo[searchResults.Count];
for (int i = 0; i < array.Length; i++)
{
    array[i] = searchResults[i];
}
 
// Sorting results in array by relevance in descending order
Array.Sort(array, new Comparer());
```

## Improved representation of results of exact phrase search {#GroupDocs.Searchfor.NET17.12ReleaseNotes-Improvedrepresentationofresultsofexactphrasesearch}This enhancement is implemented to store the results of exact phrase search in a more structured and convenient form. Following code sample shows the usage of this feature.```
string indexFolder = @"c:\MyIndex";
string documentsFolder = @"c:\MyDocuments";
 
// Creating index
Index index = new Index(indexFolder);
 
// Indexing
index.AddToIndex(documentsFolder);
 
// Creating search parameters object
SearchParameters searchParameters = new SearchParameters();
// Enabling fuzzy search
searchParameters.FuzzySearch.Enabled = true;
// Setting maximum mistake count to 1
searchParameters.FuzzySearch.FuzzyAlgorithm = new TableDiscreteFunction(1);
 
// Searching for phrase 'cumulative distribution function' or phrase 'cumulative density function'
SearchResults searchResults = index.Search("\"cumulative distribution function\" OR \"cumulative density function\"", searchParameters);
 
// Displaying results
foreach (DocumentResultInfo document in searchResults)
{
    Console.WriteLine(document.FileName);
    foreach (DetailedResultInfo field in document.DetailedResults)
    {
        Console.WriteLine(field.FieldName);
        foreach (string[] phrase in field.TermSequences)
        {
            Console.Write("\t");
            foreach (string word in phrase)
            {
                Console.Write(word + " ");
            }
            Console.WriteLine();
        }
    }
}
 
// The results may contain the following phrases:
// cumulative distribution function
// cumulative distribution functions
// cumulative density function
// cumulative density functions
```

## Improved search query syntax {#GroupDocs.Searchfor.NET17.12ReleaseNotes-Improvedsearchquerysyntax}The syntax of the search query language has been redesigned to make it more understandable and conventional. For details, please visit [this](https://docs.groupdocs.com/search/net) documentation article.

# Available Channels and Resources

Here are a few channels and resources for you to download, try, learn and get technical support on GroupDocs.Search:

*   [Download](https://downloads.groupdocs.com/search/net "GroupDocs.Search MSI") - MSI Package
*   [NuGet](https://www.nuget.org/packages/GroupDocs.Search "GroupDocs.Search Nuget Package") - NuGet Install
*   [Documentation](https://docs.groupdocs.com/display/searchnet/Getting+Started) - API docs
*   [Examples/Plugins/Showcases](https://github.com/groupdocs-search/GroupDocs.Search-for-.NET "How to use Search API") - Examples and Open Source Application
*   [Video Tutorials](https://www.youtube.com/playlist?list=PL25CTxMCj5vMZGPsZX-FCtRM_UBXdLT9h "Search API video Tutorials") - YouTube Videos
*   [Product Support Forum](https://forum.groupdocs.com/c/search) - Technical Support Forum for GroupDocs.Search

# Feedback

If you have any suggestions, questions, or queries related to the [.NET Search API](https://products.groupdocs.com/search/net), we will be happy to hear from you. Just create a [forum thread](https://forum.groupdocs.com/c/search) to share your thoughts.




