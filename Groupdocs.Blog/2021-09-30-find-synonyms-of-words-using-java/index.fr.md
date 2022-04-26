---
title: "Trouver des synonymes de mots en utilisant Java"
date: Thu, 30 Sep 2021 14:17:00 +0000
draft: false
url: /fr/2021/09/30/trouver-des-synonymes-de-mots-en-utilisant-java/
author: 'Shoaib Khan'
summary: "Évitez la répétition du même mot; utilisez **Synonymes** (deux mots différents qui signifient la même chose). Que se passe-t-il si vous avez besoin de trouver tous ces synonymes de n'importe quel mot par programmation ? Cet article vous explique comment trouver tous les synonymes de n'importe quel mot en utilisant Java. De même, un même mot peut avoir plusieurs sens. Nous verrons comment les synonymes peuvent être regroupés selon les différents sens d'un même mot."
tags: ['Find Synonyms', 'Find Synonyms in Java', 'Search Synonyms', 'Search Synonyms in Java', 'Synonyms in Java']
categories: ['GroupDocs.Search Product Family']
---

Évitez la répétition du même mot; utilisez **Synonymes** (deux mots différents qui signifient la même chose). Que faire si vous avez besoin de trouver des synonymes de n'importe quel mot par programmation ? Cet article vous guide sur **comment trouver tous les synonymes de n'importe quel mot en utilisant Java**. De même, un même mot peut avoir plusieurs sens. Nous verrons comment les synonymes peuvent être regroupés selon les différents sens d'un même mot.

Les sujets suivants seront abordés ci-dessous :

* [API Java – Rechercher des synonymes][1]
* [Obtenir les synonymes de n'importe quel mot en Java][2]
* [Obtenir des synonymes – Regroupés par différentes significations][3]

## API Java pour la recherche de synonymes {#find-synonyms-java-api}

[GroupDocs.Search][4] permet de trouver des synonymes de mots via ses API. J'utiliserai son [Java API][5] dans les exemples. Il permet en outre de rechercher le mot et tous ses synonymes dans plusieurs documents d'un dossier. Il existe de nombreuses techniques de recherche différentes qui peuvent être utilisées pour [rechercher parmi une longue liste de formats de documents][6].

### Télécharger ou configurer

Vous pouvez télécharger le fichier **JAR** à partir de la [section téléchargements][7], ou simplement obtenir les dernières configurations de référentiel et de dépendance pour le pox.xml de vos applications Java **basées sur maven**.

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

## Trouver des synonymes de n'importe quel mot en Java {#get-synonyms}

Supposons que vous ayez le mot "MONTRER" dans votre esprit. Voyons, quels pourraient être les synonymes de 'SHOW'. Voici les étapes pour obtenir des synonymes en utilisant Java.

* Tout d'abord, définissez la requête/le mot pour trouver ses synonymes.
* Créer un index en utilisant la classe [Index][8].
* À partir des différents dictionnaires, obtenez le dictionnaire des synonymes puis la collection de synonymes en passant la requête à la méthode [getSynonyms][9].
* Transversaliser les synonymes pour travailler avec chaque synonyme.

Le code source suivant montre comment obtenir tous les synonymes de n'importe quel mot fourni en Java.

```
// Obtenez tous les synonymes de n'importe quel mot en Java
String query = "show";
String[] synonyms = new Index().getDictionaries().getSynonymDictionary().getSynonyms(query);

System.out.println("Synonyms for " + query +":");

for (String synonym : synonyms) {
    System.out.println(synonym);
}
```

Voici la sortie du code Java ci-dessus qui affiche tous les synonymes du mot "show".

```
Synonyms for '**show**':

 - prove
 - testify
 - present
 - demo
 - exhibit
 - demonstrate
 - evidence  
```

## Trouver des synonymes regroupés par différentes significations en Java {#get-synonyms-as-group}

Il peut y avoir différentes significations d'un même mot selon la situation et son utilisation. Vous pouvez regrouper différents ensembles de synonymes selon leur signification. Les étapes suivantes vous permettent d'obtenir différents groupes de synonymes à l'aide de Java.

* Tout d'abord, définissez le mot dont les synonymes sont requis.
* Créez l'index en utilisant la classe [Index][10].
* À partir des différents dictionnaires, obtenez le dictionnaire de synonymes puis la collection de groupes de synonymes en passant la requête à la méthode [getSynonymGroups][11].
* Collection de groupes de synonymes transversaux pour travailler avec chaque groupe ou mot synonyme.

Le code source suivant montre comment obtenir tous les groupes de synonymes de n'importe quel mot fourni en Java.

```
// Obtenez des groupes de synonymes selon différentes significations du même mot en utilisant Java
String query = "show";
String[][] groups = new Index().getDictionaries().getSynonymDictionary().getSynonymGroups(query);

System.out.println("Synonym groups for " + query +":");

for (String[] group : groups) {
    for (String group1 : group) {
        System.out.print(group1 + " ");
    }
    System.out.println();
}
```

Ce qui suit est la sortie du code Java ci-dessus qui affiche tous les synonymes du mot fourni "show" regroupés selon sa signification différente.

```
Synonym groups for **show**:

 - evidence prove **show** testify 
 - demo demonstrate exhibit present **show** 
```

Ensuite, nous discuterons dans un article séparé, [comment trouver n'importe quel mot et ses synonymes dans plusieurs fichiers d'un dossier en utilisant Java][12].

## Conclusion

Pour résumer, nous avons discuté de la façon de trouver les synonymes possibles de n'importe quel mot en Java en utilisant des méthodes simples. De plus, nous avons discuté de la façon d'obtenir tous les groupes de synonymes créés en fonction des différentes significations de ce même mot. Maintenant, vous pouvez essayer de créer vos propres synonymes d'application Java.

En savoir plus [sur l'API Java Search Automation][13] dans la documentation. Pour découvrir les fonctionnalités, vous pouvez consulter des exemples sur le référentiel [GitHub][14]. Contactez-nous pour toute question via le [forum][15].

## Voir également

* [Rechercher des synonymes de mots à l'aide de C#][16]
* [Rechercher des synonymes dans plusieurs fichiers à l'aide de Java][17]
* [Créez votre solution de recherche de texte intégral en Java][18]
* [Rechercher et remplacer des mots dans des documents à l'aide de Java][19]
* [Rechercher et supprimer des filigranes de documents en Java][20]







[1]: #find-synonyms-java-api
[2]: #get-synonyms
[3]: #get-synonyms-as-group
[4]: https://products.groupdocs.com/search/
[5]: https://products.groupdocs.com/search/java/
[6]: https://docs.groupdocs.com/search/java/supported-document-formats/
[7]: https://downloads.groupdocs.com/search
[8]: https://apireference.groupdocs.com/search/java/com.groupdocs.search/Index
[9]: https://apireference.groupdocs.com/search/java/com.groupdocs.search.dictionaries/SynonymDictionary#getSynonyms(java.lang.String)
[10]: https://apireference.groupdocs.com/search/java/com.groupdocs.search/Index
[11]: https://apireference.groupdocs.com/search/java/com.groupdocs.search.dictionaries/SynonymDictionary#getSynonymGroups(java.lang.String)
[12]: https://blog.groupdocs.com/2021/10/03/find-synonyms-in-multiple-files-using-java/
[13]: https://docs.groupdocs.com/search/java/
[14]: https://github.com/groupdocs-search
[15]: https://forum.groupdocs.com/
[16]: https://blog.groupdocs.com/2021/09/14/find-synonyms-of-words-using-csharp/
[17]: https://blog.groupdocs.com/2021/10/03/find-synonyms-in-multiple-files-using-java/
[18]: https://blog.groupdocs.com/2021/08/07/build-full-text-search-solution-in-java/
[19]: https://blog.groupdocs.com/2021/09/01/find-and-replace-text-in-documents-using-java/
[20]: https://blog.groupdocs.com/2020/11/30/find-and-remove-watermarks-from-documents-in-java/


