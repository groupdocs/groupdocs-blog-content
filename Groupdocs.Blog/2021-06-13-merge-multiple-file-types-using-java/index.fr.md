---
title: "Fusionner plusieurs types de fichiers en un seul à l'aide de Java"
date: Sun, 13 Jun 2021 05:49:00 +0000
draft: false
url: /fr/2021/06/13/merge-multiple-file-types-using-java/
author: 'Shoaib Khan'
summary: "La fusion de différents documents est souvent nécessaire lorsque vous avez l'intention de rassembler les données dispersées de différents documents dans un seul fichier. Dans cet article, vous apprendrez à automatiser le processus de fusion de documents. Cela montrera comment fusionner par programme plusieurs documents de types de fichiers identiques ou différents en un seul fichier à l'aide de Java. Dans un autre article, nous avons discuté de [la fusion de plusieurs fichiers de différents formats à l'aide de C#][1]."
tags: ['Merge Documents in Java', 'Merge Files in Java', 'Merge multiple file types in Java', 'Merge two or more file in Java']
categories: ['GroupDocs.Merger Product Family']
---

La fusion de différents documents est souvent nécessaire lorsque vous avez l'intention de rassembler les données dispersées de différents documents dans un seul fichier. Dans cet article, vous apprendrez à automatiser le processus de fusion de documents. Cela montrera comment fusionner par programme plusieurs documents de types de fichiers identiques ou différents en un seul fichier à l'aide de Java. Dans un autre article, nous avons discuté de [la fusion de plusieurs fichiers de différents formats à l'aide de C#][2].



{{< figure align=center src="images/merged-pdf-word-excel-files-to-pdf-in-java.jpg" alt="Présentations PDF Word Excel fusionnées en un seul PDF en Java">}}


Les sujets suivants sont traités ci-dessous :

* [API Java - Fusionner plusieurs fichiers][3]
* [Fusionner des fichiers PDF, Word, Excel en un seul PDF][4]
* [Fusionner des pages sélectives de plusieurs fichiers en un seul fichier][5]

## API Java pour fusionner plusieurs types de documents {#java-api-to-merge-multiple-file-types}

J'utiliserai [GroupDocs.Merger pour Java][6] pour combiner des documents de différents formats de fichiers en un seul fichier. L'API Java permet de joindre divers documents de formats identiques ou différents dans un seul fichier. De plus, il permet aux documents de diviser, rogner, échanger, déplacer, supprimer, faire pivoter ou organiser les pages en conséquence. De plus, il prend en charge les mots de passe et leur suppression pour gérer la sécurité des [formats de document pris en charge][7].

Certains des types de documents pris en charge par l'API incluent ; documents de traitement de texte, feuilles de calcul, présentations, HTML, PDF, livres électroniques, dessins Visio, CSV et TSV.

### Télécharger et configurer

Obtenez la bibliothèque de fusion de documents à partir de la section des téléchargements. Pour les applications Java basées sur Maven, ajoutez la configuration suivante dans pom.xml. Ensuite, vous pouvez essayer des exemples de fusion de documents Java de cet article ainsi que de nombreux autres de [GitHub][8]. Pour plus de détails, vous pouvez également consulter la [API Reference][9].

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
        <artifactId>groupdocs-merger</artifactId>
        <version>21.3</version> 
</dependency>
```

## Fusionner des fichiers PDF, Word, Excel en un seul PDF en Java {#merge-multiple-files-into-one-pdf-in-java}

Les documents PDF peuvent être combinés avec vos documents Word, feuilles de calcul Excel, présentations PowerPoint et autres documents PDF avec seulement quelques lignes de code. Voici les étapes à suivre pour fusionner des documents de plusieurs types de fichiers en un seul fichier.

* Chargez le document initial en utilisant la classe [Merger][10].
* Combinez le deuxième document en utilisant la méthode [join][11].
* Continuez à fusionner les autres documents (si nécessaire) en utilisant la même méthode **joindre** ou une méthode similaire.
* Enregistrez le document combiné final sur le chemin ou le flux à l'aide de la méthode [save][12] appropriée.

Le code source suivant montre comment fusionner des documents PDF, Word et Excel en un seul fichier PDF en Java.

```
// Combinez deux ou plusieurs types de fichiers différents en un seul à l'aide de Java
Merger merger = new Merger("pdf_document.pdf");
{
  merger.join("word_document.docx");
  merger.join("spreadsheet.xlsx");
	
  merger.save("merged-document.pdf");
}
```

De même, les documents avec les mêmes types de fichiers peuvent être combinés. Ce qui est mentionné ci-dessous est la sortie obtenue en joignant un document Word, un document PDF. et une feuille de calcul utilisant le code Java mentionné ci-dessus.



{{< figure align=center src="images/merged-pdf-word-excel-to-one-file.jpg" alt="Fusionner différents types de fichiers en un seul PDF C#">}}


## Fusionner des pages sélectives de plusieurs fichiers PDF, Word, Excel en un seul PDF en Java {#merge-selective-pages-of-multiple-files-into-one-pdf-in-java}



{{< figure align=center src="images/merged-selective-pages-of-pdf-word-excel-to-one-file.jpg" alt="Fusionner une page sélective de différents types de fichiers en un seul PDF C#">}}


Si vous souhaitez sélectionner quelques pages d'un document et quelques autres pages sélectives du document suivant, etc. L'API vous permet de fusionner des pages sélectives de plusieurs types de fichiers en un seul fichier de différentes manières.

* Chargez le document initial en utilisant la classe [Merger][13].
* Préparez les options de fusion avec la classe [JoinOptions][14].
* Commencez à fusionner le document en utilisant la méthode [join][15].
* Continuez à joindre les documents en définissant les options de jonction appropriées pour chaque document.
* Enregistrez le document fusionné final en utilisant la méthode [save][16].

Le code source suivant montre comment fusionner la première page d'un document Word et les feuilles paires d'une feuille de calcul Excel dans la plage fournie en Java avec un document PDF. La sortie sera un seul fichier PDF.

```
// Combinez des pages sélectives de deux ou plusieurs types de fichiers différents en un seul à l'aide de Java
Merger merger = new Merger("pdf_document.pdf");
{
  JoinOptions joinOptions = new JoinOptions(new int[]{1});
  merger.join("word_document.docx", joinOptions);

  joinOptions = new JoinOptions(1, 2, RangeMode.EvenPages);
  merger.join("spreadsheet.xlsx", joinOptions);
    
  merger.save("merged-document.pdf");
}
```

## Obtenez une licence API gratuite {#Get-a-Free-API-License}

Vous pouvez [obtenir une licence temporaire gratuite][17] afin d'utiliser l'API sans les limitations d'évaluation.

## Conclusion

Pour conclure, vous avez appris à fusionner deux ou plusieurs documents de types de fichiers similaires ou différents en un seul fichier en utilisant Java avec votre application. De plus, vous avez appris à combiner des pages sélectives de plusieurs types de fichiers en un seul fichier.

Vous pouvez en savoir plus sur GroupDocs.Merger en utilisant la [documentation][18]. Si vous avez des questions, contactez-nous via [forum][19].

## Voir également

* [Fractionner des fichiers ou fusionner des documents en Java][20]
* [Fusionner plusieurs fichiers de différents formats en un seul en utilisant C#][21]







[1]: https://blog.groupdocs.com/2021/05/04/merge-multiple-file-types-using-csharp/
[2]: https://blog.groupdocs.com/2021/05/04/merge-multiple-file-types-using-csharp/
[3]: #java-api-to-merge-multiple-file-types
[4]: #merge-multiple-files-into-one-pdf-in-java
[5]: #merge-selective-pages-of-multiple-files-into-one-pdf-in-java
[6]: https://products.groupdocs.com/merger/java/
[7]: https://docs.groupdocs.com/merger/java/supported-document-formats/
[8]: https://github.com/groupdocs-merger
[9]: https://apireference.groupdocs.com/merger/java
[10]: https://apireference.groupdocs.com/merger/java/com.groupdocs.merger/Merger
[11]: https://apireference.groupdocs.com/merger/java/com.groupdocs.merger/Merger#join(java.io.InputStream)
[12]: https://apireference.groupdocs.com/merger/java/com.groupdocs.merger/Merger#save(java.lang.String)
[13]: https://apireference.groupdocs.com/merger/java/com.groupdocs.merger/Merger
[14]: https://apireference.groupdocs.com/merger/java/com.groupdocs.merger.domain.options/JoinOptions
[15]: https://apireference.groupdocs.com/merger/java/com.groupdocs.merger/Merger#join(java.io.InputStream)
[16]: https://apireference.groupdocs.com/merger/java/com.groupdocs.merger/Merger#save(java.lang.String)
[17]: https://purchase.groupdocs.com/temporary-license
[18]: https://docs.groupdocs.com/merger
[19]: https://forum.groupdocs.com/
[20]: https://blog.groupdocs.com/2020/05/20/merge-pdf-word-excel-powerpoint-documents-in-java/
[21]: https://blog.groupdocs.com/2021/05/04/merge-multiple-file-types-using-csharp/


