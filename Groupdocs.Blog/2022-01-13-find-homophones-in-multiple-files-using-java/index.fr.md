---
title: "Rechercher des homophones dans plusieurs fichiers en Java"
date: Thu, 13 Jan 2022 06:28:19 +0000
draft: false
url: /fr/2022/01/13/trouver-des-homophones-dans-plusieurs-fichiers-en-utilisant-java/
author: 'Shoaib Khan'
summary: "Les **synonymes** sont des mots ayant une signification similaire, et les **homophones** se prononcent de la même manière mais ont des significations ou des orthographes différentes. Nous avons appris à [trouver des synonymes dans plusieurs documents en utilisant Java](https://blog.groupdocs.com/2021/10/03/find-synonyms-in-multiple-files-using-java/). Aujourd'hui, dans cet article, nous verrons **comment rechercher des homophones dans plusieurs documents en utilisant Java**.

Les sujets suivants sont traités dans cet article :

* API Java - Recherche d'homophones
* Trouver des homophones dans des documents en utilisant Java
* Jouez avec le résultat de la recherche d'homophones"
tags: ['Find Homophone in Java', 'Find Homophones', 'Find Homophones in Files', 'Homophones']
categories: ['GroupDocs.Search Product Family']
---

{{< figure align=center src="images/Search-Homophones-in-Files.jpg" alt="Rechercher des homophones dans des fichiers à l'aide de GroupDocs">}}

Les **synonymes** sont des mots ayant une signification similaire, et les **homophones** se prononcent de la même manière mais ont des significations ou des orthographes différentes. Nous avons appris à [trouver des synonymes dans plusieurs documents en utilisant Java](https://blog.groupdocs.com/2021/10/03/find-synonyms-in-multiple-files-using-java/). Aujourd'hui, dans cet article, nous verrons **comment rechercher des homophones dans plusieurs documents en utilisant Java**.

Les sujets suivants seront abordés ci-dessous :

* [API Java - Recherche d'homophones](#homophone-search-java-api)
* [Rechercher des homophones dans des documents utilisant Java](#homophone-in-different-files)
* [Jouer avec le résultat de la recherche d'homophones](#print-homophone-search)

## API Java pour la recherche d'homophones {#homophone-search-java-api}

[GroupDocs.Search](https://products.groupdocs.com/search/) présente l'API Java ([GroupDocs.Search for Java](https://products.groupdocs.com/search/net/)) qui permet trouver n'importe quel mot et ses homophones dans plusieurs fichiers d'un dossier spécifique. Il peut rechercher le contenu de [divers formats différents](https://docs.groupdocs.com/search/net/supported-document-formats/). En plus de trouver les homophones, l'API prend en charge de nombreuses autres techniques de recherche, notamment :

* Recherche sensible à la casse
* Recherche floue
* Recherche de phrases
* Recherche d'expressions régulières
* Recherche de synonymes
* Recherche par joker

Vous pouvez télécharger le fichier **JAR** à partir de la [section téléchargements](https://downloads.groupdocs.com/search) ou utiliser le dernier référentiel et dépendance [Maven](https://repository.groupdocs.com/webapp/#/artifacts/browse/tree/General/repo/com/groupdocs) configurations dans vos applications Java.

```
<repository>
	<id>GroupDocsJavaAPI</id>
	<name>GroupDocs Java API</name>
	<url>http://repository.groupdocs.com/repo/</url>
</repository>
<dependency>
        <groupId>com.groupdocs</groupId>
        <artifactId>groupdocs-search</artifactId>
        <version>21.8</version> 
</dependency>
```

```
PM> Install-Package GroupDocs.Search
```

## Find Homophones in Multiple Files in Java {#homophone-in-different-files}

Les étapes suivantes expliquent comment rechercher des homophones dans plusieurs fichiers d'un dossier en Java.

* Définissez la requête de mot de recherche, le dossier d'indexation et le dossier conteneur de vos fichiers.
* Créez [Index](https://apireference.groupdocs.com/search/java/com.groupdocs.search/Index) avec le dossier d'index défini.
* Ajouter le dossier du document à l'index.
* Définissez les [SearchOptions](https://apireference.groupdocs.com/search/java/com.groupdocs.search.options/SearchOptions) et activez l'homophoneSearch en utilisant [setUseHomophoneSearch()](https://apireference.groupdocs.com/search/java/com.groupdocs.search.options/SearchOptions#setUseHomophoneSearch(booléen)).
* Effectuez la recherche d'homophones en utilisant [search()](https://apireference.groupdocs.com/search/java/com.groupdocs.search/Index#search(com.groupdocs.search.SearchQuery,%20com.groupdocs.search.options.SearchOptions)).
* Utilisez les propriétés du [SearchResult](https://apireference.groupdocs.com/search/java/com.groupdocs.search.results/SearchResult) récupéré selon vos besoins.

Le code source Java suivant trouve tous les homophones dans les fichiers du dossier défini. De plus, vous pouvez également [gérer votre dictionnaire d'homophones](https://docs.groupdocs.com/search/java/homophone-dictionary/).

```
// Rechercher des homophones dans plusieurs fichiers et dossiers à l'aide de Java
String indexFolder = "path/indexFolder";
String documentsFolder = "path/documentsFolder";
String query = "right";

// Création d'un index dans le dossier spécifié
Index index = new Index(indexFolder);
index.add(documentsFolder);

// Création d'un objet d'options de recherche
SearchOptions options = new SearchOptions();
options.setUseHomophoneSearch(true); // Enable Homophone Search

// Rechercher le mot "droit"
// En plus du mot 'right', les homophones 'rite, write, wright, ...' seront également recherchés
SearchResult result = index.search(query, options);

System.out.println("Query: " + query);
System.out.println("Documents: " + result.getDocumentCount());
System.out.println("Word & Homophone Occurrences: " + result.getOccurrenceCount());
```

La sortie du code ci-dessus est la suivante :

```
Query: right
Documents: 2
Occurrences: 17
```

## Impression des résultats de la recherche d'homophones en Java {#print-homophone-search}

Vous pouvez utiliser les résultats de la recherche d'homophones en suivant les étapes après avoir obtenu les homophones et leurs occurrences à partir de chaque document.

*   Parcourez les résultats de la recherche.
*   Obtenez chaque [FoundDocument](https://apireference.groupdocs.com/search/java/com.groupdocs.search.results/FoundDocument) en utilisant [getFoundDocument()](https://apireference.groupdocs.com/search/java/com.groupdocs.search.results/SearchResult#getFoundDocument(int)).
*   Utilisez les propriétés de chaque FoundDocument selon vos besoins.
*   Maintenant, parcourez les champs de FoundDocument en obtenant [FoundDocumentField](https://apireference.groupdocs.com/search/java/com.groupdocs.search.results/FoundDocumentField).
*   Plus tard, à partir de chaque FoundDocumentField, récupérez tous les termes et leurs occurrences dans chaque document.

L'exemple de code Java suivant imprime les résultats de la recherche d'homophones avec le nombre d'occurrences de chaque terme recherché.

```
// Impression des résultats de la recherche d'homophones en Java
System.out.println("Query: " + query);
System.out.println("Documents: " + result.getDocumentCount());
System.out.println("Word & Homophone Occurrences: " + result.getOccurrenceCount());

// Parcourir les documents
for (int i = 0; i < result.getDocumentCount(); i++) {
    FoundDocument document = result.getFoundDocument(i);
    System.out.println("Document: " + document.getDocumentInfo().getFilePath());
    System.out.println("Occurrences: " + document.getOccurrenceCount());
  
  // Parcourir les champs trouvés
  for (FoundDocumentField field : document.getFoundFields()) {
        System.out.println("\tField: " + field.getFieldName());
        System.out.println("\tOccurrences: " + document.getOccurrenceCount());
  
        // Impression des termes trouvés
        if (field.getTerms() != null) {
            for (int k = 0; k < field.getTerms().length; k++) {
                System.out.println("\t\t" + field.getTerms()[k] + "\t - \t" + field.getTermsOccurrences()[k]);
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

## Rechercher des homophones et des résultats d'impression à l'aide de Java - Code complet {#search-and-print-synonyms-code}

Le code Java suivant combine les étapes ci-dessus. Initialement, il trouve les homophones selon la requête, puis imprime toutes les occurrences d'homophones de chaque document dans le dossier fourni.

```
// Rechercher des homophones dans plusieurs fichiers et dossiers à l'aide de Java
String indexFolder = "path/indexFolder";
String documentsFolder = "path/documentsFolder";
String query = "right";

// Création d'un index dans le dossier spécifié
Index index = new Index(indexFolder);
index.add(documentsFolder);

// Création d'un objet d'options de recherche
SearchOptions options = new SearchOptions();
options.setUseHomophoneSearch(true); // Enable Homophone Search

// Rechercher le mot "droit"
// En plus du mot 'right', les homophones 'rite, write, wright, ...' seront également recherchés
SearchResult result = index.search(query, options);

System.out.println("Query: " + query);
System.out.println("Documents: " + result.getDocumentCount());
System.out.println("Word & Homophone Occurrences: " + result.getOccurrenceCount());

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

## Conclusion

Pour conclure, vous avez appris à trouver les mots et leurs homophones à partir de plusieurs documents dans un dossier spécifié à l'aide de Java. Vous pouvez essayer de développer votre propre application Java pour rechercher des homophones à l'aide de **GroupDocs.Search for Java**.

En savoir plus [sur l'API Java Search Automation](https://docs.groupdocs.com/search/java/) dans la documentation. Pour découvrir ses fonctionnalités, vous pouvez consulter les exemples disponibles sur le référentiel [GitHub](https://github.com/groupdocs-search). Contactez-nous pour toute question via le [forum](https://forum.groupdocs.com/).

## See Also

*   [Rechercher des homophones dans plusieurs fichiers en C#](https://blog.groupdocs.com/2022/01/04/find-homophones-in-multiple-files-using-csharp/)
*   [Trouver des synonymes de mots en utilisant Java](https://blog.groupdocs.com/2021/09/30/find-synonyms-of-words-using-java/)
*   [Construisez votre solution de recherche plein texte en Java](https://blog.groupdocs.com/2021/08/07/build-full-text-search-solution-in-java/)
*   [Rechercher et remplacer des mots dans des documents à l'aide de Java](https://blog.groupdocs.com/2021/09/01/find-and-replace-text-in-documents-using-java/)
*   [Rechercher et supprimer des filigranes de documents en Java](https://blog.groupdocs.com/2020/11/30/find-and-remove-watermarks-from-documents-in-java/)





