---
title: "Rechercher des synonymes dans plusieurs fichiers à l'aide de Java"
date: Sun, 03 Oct 2021 07:50:04 +0000
draft: false
url: /fr/2021/10/03/trouver-des-synonymes-dans-plusieurs-fichiers-en-utilisant-java/
author: 'Shoaib Khan'
summary: "Nous avons récemment discuté de [comment obtenir tous les synonymes de n'importe quel mot][1]. Ce serait merveilleux si nous pouvions localiser ces synonymes dans de nombreux documents différents. Dans cet article, nous verrons **comment rechercher n'importe quel mot et ses synonymes dans plusieurs fichiers en utilisant Java**."
tags: ['Find in Files', 'Find in Files using Java', 'Find Synonyms', 'Find Synonyms in Java', 'Search Synonyms', 'Search Synonyms in Java']
categories: ['GroupDocs.Search Product Family']
---

Nous avons récemment discuté de [comment obtenir tous les synonymes de n'importe quel mot][2]. Ce serait merveilleux si nous pouvions localiser ces synonymes dans de nombreux documents différents. Dans cet article, nous verrons **comment rechercher n'importe quel mot et ses synonymes dans plusieurs fichiers en utilisant Java**.

Voici les sujets abordés ci-dessous :

* [API Java - Recherche de synonymes][3]
* [Rechercher des synonymes dans les documents en Java][4]
* [Présenter les résultats de la recherche de synonymes][5]
* [Code Java complet – Rechercher et imprimer les résultats de la recherche de synonymes][6]

## API Java - Rechercher des synonymes dans plusieurs fichiers {#synonym-search-java-api}

[GroupDocs.Search][7] présente l'API Java ([GroupDocs.Search for Java][8]. Il permet de rechercher des mots et leurs synonymes dans divers fichiers multiples du dossier spécifié. Il prend en charge une longue liste de formats de fichiers différents et diverses techniques de recherche. Certaines de ces fonctionnalités sont mentionnées ci-dessous et vous pouvez les utiliser en combinaison pour atteindre votre cible :

* Recherche booléenne
* Recherche sensible à la casse
* Mettez en surbrillance les résultats de la recherche
* Recherche d'homophones
* Recherche de phrases
* Recherche d'expressions régulières
* Recherche par morceaux
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
        <version>21.8</version> 
</dependency>
```

## Trouver des synonymes dans plusieurs fichiers à l'aide de Java {#synonyms-in-different-files}

Passons rapidement à la recherche de synonymes dans les fichiers. Les étapes suivantes montrent comment rechercher des synonymes (mots ayant des significations similaires) dans les fichiers d'un dossier à l'aide de Java :

* Définissez le dossier d'index, le dossier du document et la requête (le mot à rechercher).
* Créez un index à l'aide d'un dossier d'index défini à l'aide de la classe [Index][10].
* Ajouter le dossier des documents à l'index.
* Activez la recherche de synonymes à l'aide de [SearchOptions][11].
* Appelez la méthode [search][12] de la classe Index et passez la requête avec les options de recherche.
* Imprimez le résumé en utilisant les propriétés de la classe [SearchResult][13] récupérée.

Le code source suivant montre comment trouver tous les synonymes dans les fichiers à l'aide de Java :

```
// Rechercher des synonymes dans plusieurs fichiers et dossiers à l'aide de Java
String indexFolder = "path/indexFolder";
String documentsFolder = "path/documentsFolder";
String query = "make";

// Création d'un index dans le dossier spécifié
Index index = new Index(indexFolder);
index.add(documentsFolder);

// Création d'un objet d'options de recherche
SearchOptions options = new SearchOptions();
options.setUseSynonymSearch(true); // Enable Synonym Search

// Rechercher le mot "faire"
// En plus du mot 'make', les synonymes 'do, get, have, ...' seront également recherchés
SearchResult result = index.search(query, options);

System.out.println("Query: " + query);
System.out.println("Documents: " + result.getDocumentCount());
System.out.println("Word & Synonym Occurrences: " + result.getOccurrenceCount());
```

Voici la sortie du code ci-dessus :

```
Query: **make**
Documents: 3
Word & Synonym Occurrences: 44 
```

## Impression des résultats de la recherche de synonymes à l'aide de Java {#print-synonym-search}

À partir des résultats de la recherche obtenus à l'étape ci-dessus, vous pouvez obtenir les informations concernant chaque mot et synonyme de la recherche. Les étapes suivantes présentent les résultats en détail après avoir obtenu tous les synonymes et leur nombre d'occurrences dans chaque document :

* Tout d'abord, effectuez la recherche pour obtenir le [SearchResult][14].
* Traversez le résultat de la recherche pour travailler avec chaque [FoundDocument][15].
* Imprimer les propriétés respectives de chaque FoundDocument.
* Maintenant, extrayez puis parcourez le [FoundDocumentField][16] dans chaque FoundDocument.
* Chaque FoundDocumentField contient ses propres termes, occurrences et autres propriétés. Utilisez le getter correspondant.

Le code source suivant affiche le résultat de la recherche de synonymes ainsi que le nombre d'occurrences de chaque terme recherché en Java.

```
// Impression des résultats de la recherche de synonymes en Java
System.out.println("Query: " + query);
System.out.println("Documents: " + result.getDocumentCount());
System.out.println("Word & Synonym Occurrences: " + result.getOccurrenceCount());

for (int i = 0; i < result.getDocumentCount(); i++) {
    FoundDocument document = result.getFoundDocument(i);
    System.out.println("Document: " + document.getDocumentInfo().getFilePath());
    System.out.println("Occurrences: " + document.getOccurrenceCount());

  for (FoundDocumentField field : document.getFoundFields()) {
        System.out.println("\tField: " + field.getFieldName());
        System.out.println("\tOccurrences: " + document.getOccurrenceCount());
  
        // Printing found terms
        if (field.getTerms() != null) {
            for (int k = 0; k < field.getTerms().length; k++) {
                System.out.println("\t\t" + field.getTerms()[k] + "\t - \t" + field.getTermsOccurrences()[k]);
            }
        }
    }
}
```

Voici la sortie du code ci-dessus :

```
Query: **make**
Documents: 2
Total occurrences: 22

Document: C:/documents/sample.docx
Occurrences: 13
    Field: content
    Occurrences: 13
        **make**  -  2
        **have**  -  1
        **get**  -  2
        **do**  -  8
- - - - - - - - - - - - - - - - 
Document: C:/documents/sample.txt
Occurrences: 11
    Field: content
    Occurrences: 11
        **make**  -  1
        **have**  -  2
        **get**  -  1
        **do**  -  7
- - - - - - - - - - - - - - - - 
Document: C:/documents/sample.pdf
Occurrences: 20
    Field: content
    Occurrences: 20
        **make**  -  2
        **have**  -  2
        **get**  -  2
        **do**  -  14 
```

## Synonymes de recherche et résultats d'impression en Java - Code complet {#search-and-print-synonyms-code}

Combinons les deux étapes ci-dessus, voici donc le code source complet. Tout d'abord, il trouve tous les synonymes selon la requête fournie. Ensuite, il imprime toutes les occurrences de chaque synonyme dans chaque document en Java.

```
// Rechercher des synonymes dans plusieurs fichiers et dossiers à l'aide de Java
String indexFolder = "path/indexFolder";
String documentsFolder = "path/documentsFolder";
String query = "make";

// Création d'un index dans le dossier spécifié
Index index = new Index(indexFolder);
index.add(documentsFolder);

// Création d'un objet d'options de recherche
SearchOptions options = new SearchOptions();
options.setUseSynonymSearch(true); // Enable Synonym Search

// Rechercher le mot "faire"
// En plus du mot 'make', les synonymes 'do, get, have, ...' seront également recherchés
SearchResult result = index.search(query, options);

System.out.println("Query: " + query);
System.out.println("Documents: " + result.getDocumentCount());
System.out.println("Word & Synonym Occurrences: " + result.getOccurrenceCount());

for (int i = 0; i < result.getDocumentCount(); i++) {
    FoundDocument document = result.getFoundDocument(i);
    System.out.println("Document: " + document.getDocumentInfo().getFilePath());
    System.out.println("Occurrences: " + document.getOccurrenceCount());

  for (FoundDocumentField field : document.getFoundFields()) {
        System.out.println("\tField: " + field.getFieldName());
        System.out.println("\tOccurrences: " + document.getOccurrenceCount());
  
        // Printing found terms
        if (field.getTerms() != null) {
            for (int k = 0; k < field.getTerms().length; k++) {
                System.out.println("\t\t" + field.getTerms()[k] + "\t - \t" + field.getTermsOccurrences()[k]);
            }
        }
    }
}
```

## Obtenez une licence API gratuite

Vous pouvez [obtenir une licence temporaire gratuite][17] afin d'utiliser l'API sans les limitations d'évaluation.

## Conclusion

Pour résumer, nous avons expliqué comment rechercher un mot avec son synonyme dans plusieurs documents à l'aide de Java. Plus important encore, vous pouvez maintenant essayer de développer votre propre application Java pour la recherche, tout comme [GroupDocs.Search App][18].

En savoir plus [sur l'API Java Search Automation][19] dans la documentation. Pour découvrir les fonctionnalités, essayez des exemples du référentiel [GitHub][20]. N'hésitez pas à nous contacter pour toute question via le [forum][21].

## Voir également

* [Trouver des synonymes de mots en utilisant Java][22]
* [Créez votre solution de recherche de texte intégral en Java][23]
* [Rechercher et remplacer des mots dans des documents à l'aide de Java][24]
* [Rechercher et supprimer des filigranes de documents en Java][25]







[1]: https://blog.groupdocs.com/2021/09/30/find-synonyms-of-words-using-java/
[2]: https://blog.groupdocs.com/2021/09/30/find-synonyms-of-words-using-java/
[3]: #synonym-search-java-api
[4]: #synonym-search-java-api
[5]: #print-synonym-search
[6]: #search-and-print-synonyms-code
[7]: https://products.groupdocs.com/search/
[8]: https://products.groupdocs.com/search/java/)
[9]: https://downloads.groupdocs.com/search
[10]: https://apireference.groupdocs.com/search/java/com.groupdocs.search/Index
[11]: https://apireference.groupdocs.com/search/java/com.groupdocs.search.options/SearchOptions
[12]: https://apireference.groupdocs.com/search/java/com.groupdocs.search/Index#search(com.groupdocs.search.SearchQuery,%20com.groupdocs.search.options.SearchOptions)
[13]: https://apireference.groupdocs.com/search/java/com.groupdocs.search.results/SearchResult
[14]: https://apireference.groupdocs.com/search/java/com.groupdocs.search.results/SearchResult
[15]: https://apireference.groupdocs.com/search/java/com.groupdocs.search.results/FoundDocument
[16]: https://apireference.groupdocs.com/search/java/com.groupdocs.search.results/FoundDocumentField
[17]: https://purchase.groupdocs.com/temporary-license
[18]: https://products.groupdocs.app/search/total
[19]: https://docs.groupdocs.com/search/java/
[20]: https://github.com/groupdocs-search
[21]: https://forum.groupdocs.com/
[22]: https://blog.groupdocs.com/2021/09/30/find-synonyms-of-words-using-java/
[23]: https://blog.groupdocs.com/2021/08/07/build-full-text-search-solution-in-java/
[24]: https://blog.groupdocs.com/2021/09/01/find-and-replace-text-in-documents-using-java/
[25]: https://blog.groupdocs.com/2020/11/30/find-and-remove-watermarks-from-documents-in-java/


