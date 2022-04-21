---
title: "Trouver des synonymes de mots en utilisant C#"
date: Tue, 14 Sep 2021 13:40:00 +0000
draft: false
url: /fr/2021/09/14/trouver-des-synonymes-de-mots-en-utilisant-csharp/
author: 'Shoaib Khan'
summary: "Un synonyme est un mot qui signifie exactement ou presque la même chose qu'un autre mot. Nous utilisons normalement des synonymes pour éviter d'utiliser le même mot à plusieurs reprises. En tant que développeur, vous devrez peut-être trouver tous les mots ayant la même signification pour votre objectif de recherche ou d'analyse de documents. Cet article vous guidera sur **comment trouver tous les synonymes d'un mot spécifique en C# à l'aide de l'API .NET**. De plus, vous pouvez également obtenir différents groupes de ces synonymes qui sont organisés en fonction des différentes significations de ce même mot."
tags: ['Find Synonyms', 'Find Synonyms in CSharp', 'Search Synonyms', 'Search Synonyms in CSharp']
categories: ['GroupDocs.Search Product Family']
---

Un synonyme est un mot qui signifie exactement ou presque la même chose qu'un autre mot. Nous utilisons normalement des synonymes pour éviter d'utiliser le même mot à plusieurs reprises. En tant que développeur, vous devrez peut-être trouver tous les mots ayant la même signification pour votre objectif de recherche ou d'analyse de documents. Cet article vous guidera sur **comment trouver tous les synonymes d'un mot spécifique en C# à l'aide de l'API .NET**. De plus, vous pouvez également obtenir différents groupes de ces synonymes qui sont organisés en fonction des différentes significations de ce même mot.

Les sujets suivants seront abordés ci-dessous :

* [API .NET - Rechercher des synonymes][1]
* [Obtenir les synonymes de n'importe quel mot en C#][2]
* [Obtenir des synonymes - Regroupés en différentes significations][3]

## API .NET pour la recherche de synonymes {#find-synonyms-dotnet-api}

[GroupDocs.Search][4] fournit l'API .NET qui permet de trouver des synonymes de n'importe quel mot. Il permet également de rechercher ce mot et tous ses synonymes dans plusieurs documents d'un dossier. Il prend en charge différentes techniques de recherche pour [rechercher parmi une grande liste de formats de documents][5].

Vous pouvez télécharger le programme d'installation **DLLs** ou **MSI** depuis la [section téléchargements][6] ou installer l'API dans votre application .NET via [NuGet][7].

```
PM> Install-Package GroupDocs.Search
```

## Trouver des synonymes de n'importe quel mot en C # {#get-synonyms}

Ici vous pouvez trouver, quels pourraient être les synonymes du mot qui est dans votre esprit. Pour obtenir la liste des synonymes de n'importe quel mot dans votre application .NET, vous pouvez simplement utiliser les étapes suivantes et le code C# ci-dessous :

* Définissez la requête/le mot pour trouver ses synonymes.
* Créer un index en utilisant la classe [Index][8].
* Obtenez la collection de synonymes du dictionnaire de synonymes à l'aide de la méthode [GetSynonyms][9].
* Traversez la collection de synonymes pour travailler avec chaque mot synonyme.

```
// Obtenez tous les synonymes de n'importe quel mot en C#
string query = "make";
string[] synonyms = new Index().Dictionaries.SynonymDictionary.GetSynonyms(query);
Console.WriteLine("Synonyms for '" + query + "':");

for (int i = 0; i < synonyms.Length; i++)
{
    Console.WriteLine("- " + synonyms[i]);
}
```

Voici la sortie du code C# ci-dessus qui affiche tous les synonymes du mot fourni "make".

```
Synonyms for '**make**':
 - brand
 - construct
 - build
 - cook
 - fix
 - ready
 - prepare
 - induce
 - stimulate
 - cause
 - have
 - get
 - create
 - do
 - produce
 - reach
 - attain
 - hit
 - gain 
```

## Trouver des synonymes regroupés par différentes significations du mot à l'aide de C# {#get-synonyms-as-group}

Un même mot peut avoir plusieurs significations différentes selon la situation. Ainsi, ses synonymes peuvent également être regroupés en fonction des différentes utilisations. Les étapes et le code source suivants vous fournissent les différents groupes de synonymes en fonction des différentes significations de ce mot en C#.

* Définir le mot (requête) pour trouver ses synonymes.
* Créez l'index en utilisant la classe [Index][10].
* Obtenez la collection de groupes de synonymes à partir du dictionnaire de synonymes à l'aide de la méthode [GetSynonymGroups][11].
* Traversez la collection de groupes de synonymes pour travailler avec chaque groupe ou mot synonyme.

```
// Obtenir des groupes de synonymes en C#
string query = "make";
string[][] groups = new Index().Dictionaries.SynonymDictionary.GetSynonymGroups(query);

Console.WriteLine("Synonyms for " + query + ":");
for (int i = 0; i < groups.Length; i++)
{
    Console.Write("- ");
    string[] group = groups[i];
    for (int j = 0; j < group.Length; j++)
    {
        Console.Write(group[j] + " ");
    }
    Console.WriteLine();
}
```

Voici la sortie du code C# ci-dessus qui affiche tous les synonymes du mot fourni "make" regroupés selon sa signification différente.

```
Synonyms for **make**:

 - attain gain hit **make** reach 
 - create **make** produce 
 - do **make** 
 - cause get have induce **make** stimulate 
 - cook fix **make** prepare ready 
 - build construct **make** 
 - brand **make** 
```

Ensuite, nous verrons dans un article séparé, [comment trouver n'importe quel mot et ses synonymes dans plusieurs fichiers d'un dossier en C#][12].

## Conclusion

Pour conclure, vous avez appris à trouver les synonymes possibles de n'importe quel mot spécifique en C#. De plus, nous avons discuté de la façon d'obtenir tous les synonymes regroupés par les différentes significations de ce même mot. Vous pouvez essayer de développer votre propre application .NET pour rechercher des synonymes de n'importe quel mot.

En savoir plus [sur l'API .NET Search Automation][13] dans la documentation. Pour découvrir les fonctionnalités, vous pouvez consulter des exemples sur le référentiel [GitHub][14]. Contactez-nous pour toute question via le [forum][15].

## Voir également

* [Rechercher des synonymes dans plusieurs fichiers à l'aide de C#][16]
* [Classifier les commentaires des clients à l'aide de l'analyse des sentiments en C#][17]







[1]: #find-synonyms-dotnet-api
[2]: #get-synonyms
[3]: #get-synonyms-as-group
[4]: https://products.groupdocs.com/search/
[5]: https://docs.groupdocs.com/search/net/supported-document-formats/
[6]: https://downloads.groupdocs.com/search
[7]: https://www.nuget.org/packages/groupdocs.search
[8]: https://apireference.groupdocs.com/search/net/groupdocs.search/index
[9]: https://apireference.groupdocs.com/search/net/groupdocs.search.dictionaries/synonymdictionary/methods/getsynonyms
[10]: https://apireference.groupdocs.com/search/net/groupdocs.search/index
[11]: https://apireference.groupdocs.com/search/net/groupdocs.search.dictionaries/synonymdictionary/methods/getsynonymgroups
[12]: https://blog.groupdocs.com/2021/09/17/find-synonyms-in-multiple-files-using-csharp
[13]: https://docs.groupdocs.com/search/net/
[14]: https://github.com/groupdocs-search
[15]: https://forum.groupdocs.com/
[16]: https://blog.groupdocs.com/2021/09/17/find-synonyms-in-multiple-files-using-csharp
[17]: https://blog.groupdocs.com/2020/06/17/classify-customers-feedback-using-sentiment-analysis-in-csharp/


