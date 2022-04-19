---
title: "Créer une solution de recherche en texte intégral en Java"
date: Sat, 07 Aug 2021 08:09:00 +0000
draft: false
url: /fr/2021/08/07/build-full-text-search-solution-in-java/
author: 'Shoaib Khan'
summary: "La recherche en texte intégral est un moyen de rechercher un texte/une requête dans une collection de documents. Cette approche trouve rapidement toutes les instances d'un terme/expression et fonctionne en utilisant des index de texte. Dans cet article, nous allons apprendre à rechercher par programmation du texte intégral dans des documents à l'aide de Java."
tags: ['find in files and folder using Java', 'full text search', 'Full Text Search in Java', 'search via indexing']
categories: ['GroupDocs.Search Product Family']
---

La recherche en texte intégral est un moyen de rechercher un texte/une requête dans une collection de documents. Cette approche trouve rapidement toutes les instances d'un terme/expression et fonctionne en utilisant des index de texte. Dans cet article, nous allons apprendre à rechercher par programmation du texte intégral dans des documents à l'aide de Java.



{{< figure align=center src="images/TextSearch-1.png" alt="Recherche en texte intégral">}}


Après cela, vous pouvez mettre en œuvre diverses techniques de recherche et créer votre solution de recherche pour les documents de traitement de texte, les feuilles de calcul, les présentations, les fichiers HTML, les fichiers PDF, les livres électroniques, les e-mails, les archives ZIP et de nombreux autres [formats de document][1].

Les sujets suivants sont traités ci-dessous :

* [API Java pour la recherche en texte intégral][2]
* [Recherche en texte intégral][3]
* [Effectuer une recherche en Java][4]
* [Surligner les résultats de la recherche][5]

## API Java pour la recherche en texte intégral {#full-text-search-java-api}

[GroupDocs.Search][6] fournit une [API Java de recherche en texte intégral][7] qui peut être intégrée dans n'importe quelle application sans aucun outil tiers ni dépendance logicielle. Il vous permet de [rechercher parmi une grande liste de formats de documents][8]. Certaines des techniques de recherche pouvant être effectuées à l'aide de l'API sont les suivantes :

* Recherche sensible à la casse
* Recherche d'expressions régulières
* Recherche à facettes
* Recherche floue
* Recherche d'homophones
* Recherche de synonymes

### Télécharger ou configurer

Vous pouvez télécharger le fichier **JAR** à partir de la [section téléchargements][9], ou simplement obtenir les dernières configurations de référentiel et de dépendances pour le pox.xml de vos applications Java **basées sur maven**.

```
<repository>
	<id>GroupDocsJavaAPI</id>
	<name>GroupDocs Java API</name>
	<url>http://repository.groupdocs.com/repo/</url>
</repository>
```
```
<dependency>
        <groupId>com.groupdocs</groupId>
        <artifactId>groupdocs-search</artifactId>
        <version>21.3</version> 
</dependency>
```

## Recherche plein texte avec Java {#full-text-search}

Il y a deux étapes pour effectuer la recherche dans les fichiers stockés dans un dossier.

* Indexation
* Effectuer une recherche

## Fichiers d'indexation à l'aide de Java

Un index possède le texte numérisé de tous les documents. Par conséquent, lorsque vous allez effectuer une opération de recherche, seul l'index est référencé, et non le texte des documents originaux. Pour pouvoir rechercher instantanément parmi des milliers de documents avec des formats de fichiers identiques ou différents, vous devez créer un index et y ajouter ces documents. Lorsque les documents sont indexés, l'index est prêt à gérer les requêtes de recherche.

Les deux lignes simples suivantes créent un index et ajoutent également le dossier de documents à l'index.

```
Index index = new Index("indexingFolderPath");
index.add("documentsFolderPath");
```

## Effectuer une recherche en Java {#perform-search}

Après avoir indexé plusieurs documents de formats identiques ou différents tels que (Word, PDF, Excel et HTML), nous pouvons continuer à traiter une requête de recherche spécifique (terme de recherche "Dessiner") sur eux. Voici les étapes à suivre pour effectuer une recherche de texte sur plusieurs documents dans un dossier à l'aide de Java :

* Spécifiez le dossier source des documents et le dossier d'index.
* Créez [Index][10] à l'aide du dossier d'index.
* Ajouter le dossier source à l'index.
* Préparez la chaîne de requête.
* Effectuez une recherche en utilisant la méthode [search][11] de la classe Index.
* Parcourez chaque résultat de recherche pour les propriétés de chaque document.

Le code source suivant effectue une recherche de texte en Java sur tous les documents du dossier fourni.

```
// Rechercher du texte spécifié dans plusieurs documents PDF, Word, Excel et HTML dans un dossier à l'aide de Java
Index index = new Index("path/indexingFolder");
index.add("path/documentsFolderPath");

// Recherche dans l'index du texte spécifié
SearchResult result = index.search("Draw");

for (int i = 0; i < result.getDocumentCount(); i++) {
    FoundDocument document = result.getFoundDocument(i);
    System.out.println("Document Path: " + document.getDocumentInfo().getFilePath());
    System.out.println("Occurrence : " + document.getOccurrenceCount());
}
```

Nous obtiendrons le chemin du document et le nombre d'occurrences des termes de recherche dans tous les documents avec ce dossier spécifié. Voici la capture d'écran pour la visualisation.



{{< figure align=center src="images/SearchTextOutput.jpg" alt="Sortie de texte de recherche complète">}}


## Mettre en surbrillance les résultats de la recherche de texte en Java {#highlight-search-results}

Effectuons maintenant la même recherche plein texte et mettons également en surbrillance toutes les occurrences qui correspondent à votre requête.

Les étapes suivantes montrent comment mettre en surbrillance les résultats de la recherche de texte :

* Créez [Index][12] et ajoutez le dossier de documents à l'index.
* Préparez la chaîne de requête.
* Recherchez le dossier de documents à l'aide de la méthode [recherche][13].
* En parcourant les résultats, créez le surligneur à l'aide de [HtmlHighlighter][14].
* Utilisez la méthode de surbrillance pour mettre en surbrillance les résultats de la recherche.

Le code suivant génère la sortie HTML avec les résultats de recherche en surbrillance à l'aide de Java.

```
// Mettez en surbrillance les résultats de la recherche de texte intégral de plusieurs documents dans un dossier en Java
Index index = new Index("path/indexingFolder");
index.add("path/documentsFolderPath"); // Synchronous indexing documents from the specified folder

String query = "draw"; // Specify a search query
SearchResult result = index.search(query); // Searching in the index

for (int i = 0; i < result.getDocumentCount(); i++) 
{
    FoundDocument document = result.getFoundDocument(i);

    String path = "path/Highlighted-"+ i +".html";
    OutputAdapter outputAdapter = new FileOutputAdapter(path); 
    HtmlHighlighter highlighter = new HtmlHighlighter(outputAdapter); // Creating the highlighter
    index.highlight(document, highlighter); // Generates HTML formatted output document with highlighted search results
}
```

En sortie, nous obtiendrons plusieurs fichiers HTML. Chaque fichier affichera le contenu d'un document distinct (par exemple, excel.xlsx, source.docx, cible.docx) avec des termes/mots de recherche en surbrillance. Vous trouverez ci-dessous la sortie HTML en surbrillance d'un fichier DOCX, d'un fichier TXT et d'un fichier PDF obtenu à l'aide du code ci-dessus.



{{< figure align=center src="images/full-text-search-with-groupdocs.jpg" alt="Mettre en surbrillance les résultats de la recherche en texte intégral dans le contenu à l'aide de Java">}}


## Obtenez une licence API gratuite {#Get-a-Free-API-License}

Vous pouvez [obtenir une licence temporaire gratuite][15] afin d'utiliser l'API sans les limitations d'évaluation.

## Conclusion

Dans cet article, nous avons appris à rechercher du texte dans plusieurs documents d'un dossier en Java. En outre, nous avons expliqué comment mettre en surbrillance par programme le texte des résultats de recherche au format HTML pour les fichiers MS Word, les fichiers TXT et les fichiers PDF à l'aide de [GroupDocs.Search for Java][16].

Vous pouvez en savoir plus sur l'API en utilisant [documentation][17]. De nombreux autres exemples sont disponibles sur [GitHub][18]. Pour toute question, contactez-nous via le [forum][19].

## Voir également

* [Créez votre solution de recherche en texte intégral en C#][20]
* [Recherche de mots et remplacement de texte dans un PDF en Java][21]







[1]: https://docs.groupdocs.com/search/java/supported-document-formats/
[2]: #full-text-search-java-api
[3]: #full-text-search
[4]: #perform-search
[5]: #highlight-search-results
[6]: https://products.groupdocs.com/search/
[7]: https://products.groupdocs.com/search/java/
[8]: https://docs.groupdocs.com/search/java/supported-document-formats/
[9]: https://downloads.groupdocs.com/search
[10]: https://apireference.groupdocs.com/search/java/com.groupdocs.search/Index
[11]: https://apireference.groupdocs.com/search/java/com.groupdocs.search/Index#search(com.groupdocs.search.SearchQuery)
[12]: https://apireference.groupdocs.com/search/java/com.groupdocs.search/Index
[13]: https://apireference.groupdocs.com/search/java/com.groupdocs.search/Index#search(com.groupdocs.search.SearchQuery)
[14]: https://apireference.groupdocs.com/search/java/com.groupdocs.search.highlighters/HtmlHighlighter
[15]: https://purchase.groupdocs.com/temporary-license
[16]: https://products.groupdocs.com/search/java/
[17]: https://docs.groupdocs.com/search/
[18]: https://github.com/groupdocs-search
[19]: https://forum.groupdocs.com/
[20]: https://blog.groupdocs.com/2021/06/03/build-your-full-text-search-solution-in-csharp/
[21]: https://blog.groupdocs.com/2022/03/08/find-and-replace-text-in-pdf-in-java/


