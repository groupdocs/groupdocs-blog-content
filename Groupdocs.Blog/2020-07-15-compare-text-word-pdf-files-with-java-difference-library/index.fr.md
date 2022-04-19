---
title: "Comparer des fichiers texte, Word et PDF avec la bibliothèque de différences Java"
date: Wed, 15 Jul 2020 15:23:31 +0000
draft: false
url: /fr/2020/07/15/compare-text-word-pdf-files-with-java-difference-library/
aliases:
- /2020/07/15/comparing-text-word-pdf-files-with-java-difference-library/
author: 'Shoaib Khan'
summary: "Après avoir parcouru cet article, nous pourrons comparer des fichiers texte, des fichiers Word, des fichiers PDF et d'autres documents dans des applications basées sur Java. En utilisant cette fonctionnalité, nous pouvons comparer des factures, des contrats, des présentations, des conceptions AutoCAD, des listes de prix ou des fichiers de programmation. Nous aurons également le privilège de mettre en évidence les changements identifiés et d'avoir la possibilité d'accepter ou de rejeter tout changement. Nous pouvons même créer notre propre [outil de comparaison de documents][1] similaire à celui lancé par GroupDocs, en utilisant l'API de comparaison de documents pour Java."
tags: ['compare PDF files in Java', 'compare two files using java', 'compare Word files in java']
categories: ['GroupDocs.Comparison Product Family']
---

Après avoir parcouru cet article, nous pourrons comparer des fichiers texte, des fichiers Word, des fichiers PDF et d'autres documents dans des applications basées sur Java. En utilisant cette fonctionnalité, nous pouvons comparer des factures, des contrats, des présentations, des conceptions AutoCAD, des listes de prix ou des fichiers de programmation. Nous aurons également le privilège de mettre en évidence les changements identifiés et d'avoir la possibilité d'accepter ou de rejeter tout changement. Nous pouvons même créer notre propre [outil de comparaison de documents][2] similaire à celui lancé par GroupDocs, en utilisant l'API de comparaison de documents pour Java.

Ci-dessous, vous passerez en revue les sujets suivants :

* [Comparer les fichiers Word et montrer les différences][3].
* [Comparer les fichiers Word à l'aide de flux][4].
* [Accepter ou rejeter les modifications identifiées dans le fichier Word][5].
* [Comparer les fichiers texte et mettre en évidence les différences][6].
* [Comparer des fichiers PDF avec Java][7].

## API de comparaison de documents Java

Comme prérequis, vous pouvez obtenir [GroupDocs.Comparison pour Java][8] dans la section [downloads][9]. De plus, vous pouvez simplement ajouter ce qui suit dans votre pom.xml en cas d'applications basées sur maven :

### Référentiel```
<repository>
<id>GroupDocsJavaAPI</id>
<name>API Java GroupDocs</name>
<url>http://repository.groupdocs.com/repo/</url>
</repository>
```

### Dependency```
<dependency>
        <groupId>com.groupdocs</groupId>
        <artifactId>groupdocs-comparison</artifactId>
        <version>20.4</version> 
</dependency>
```

## Comparer des fichiers Word et afficher les différences à l'aide de Java {#compare-word-files}

Les étapes ci-dessous vous montreront comment comparer deux documents Word en quelques lignes de code Java. En conséquence, vous obtiendrez le document résultant qui mettra en évidence les modifications identifiées.

* Initialiser l'objet **[Comparer][10]** avec le chemin du document source.
* Ajoutez le deuxième document à comparer en utilisant la méthode **[add][11]**.
* Appelez la méthode **[compare][12]** pour obtenir le résultat de la comparaison. La méthode de comparaison prend le nom du document de sortie comme paramètre.

```
// Compare two Word files from the provided location on disk
Comparer comparer = new Comparer("source.docx");
try {
    comparer.add("target.docx");
    comparer.compare("comparison.docx");
}
finally {
    comparer.dispose();
}
```

Ici, j'affiche le document Word résultant généré par le code ci-dessus, et il contient les différences mises en évidence des deux documents Word comparés. Le contenu supprimé sera marqué en ROUGE, le contenu ajouté sera affiché en Bleu, cependant, le Vert montre le contenu modifié.



{{< figure align=center src="images/word-files-text-comparison-using-java.png" alt="word-file-text-comparison-and-show-dirffer">}}


## Comparer des fichiers Word pour du texte à l'aide de Stream {#compare-word-files-using-stream}

Vous pouvez également passer le document en tant que flux à la classe Comparer pour le comparer avec le deuxième document. Voici le code Java pour vous donner une idée claire :

```
// Compare two Word file using Stream
Comparer comparer = new Comparer(new FileInputStream("source.docx"));
try {
    comparer.add(new FileInputStream("target.docx"));
    comparer.compare(new FileOutputStream("result.docx"));
} 
finally {
    comparer.dispose();
}
```

## Accepter ou rejeter les modifications comparées dans le fichier Word à l'aide de Java {#accept-or-reject-changes}

Après avoir réussi à mettre en évidence les différences identifiées, vous avez la possibilité d'accepter ou de rejeter toute modification. Juste pour montrer à titre d'exemple, j'accepte et je rejette les modifications alternativement. Vous pouvez afficher chaque modification une par une avec le code similaire et prendre vos décisions pour accepter/rejeter chaque modification en fonction de vos besoins.

```
// Accept or Reject the identified changes of Word document in Java
Comparer comparer = new Comparer(source);
try {
    comparer.add(target);
    comparer.compare();
    ChangeInfo\[\] changes = comparer.getChanges();
    System.out.println("changes.length: " + changes.length + ".");
    // Accept or Reject the changes
    for (int n = 0; n < changes.length; n++) {
    	if (n % 2 == 0) {
    		changes\[n\].setComparisonAction(ComparisonAction.ACCEPT);
    	}
    	else {
    		changes\[n\].setComparisonAction(ComparisonAction.REJECT);
    	}
    }
    // Apply your decisions to get the resultant document.
    comparer.applyChanges(outputFileName, new SaveOptions(), new ApplyChangeOptions(changes));
}
finally {
    comparer.dispose();
}
```

## Comparer des fichiers texte et afficher les différences à l'aide de Java {#compare-text-files-in-java}

En utilisant la classe Comparer, nous pouvons également comparer n'importe quel fichier texte. Vous trouverez ci-dessous le code similaire permettant de comparer deux fichiers texte en Java. Les étapes sont exactement les mêmes que pour comparer deux autres documents :

* Commencez par transmettre le fichier texte à la classe [Comparer][13].
* Ajoutez le deuxième fichier en utilisant la méthode [add][14].
* Appelez la méthode [comparer][15].

```
// Compare two text files to identify and highlight changes.
Comparer comparer = new Comparer("source.txt");
try {
    comparer.add("target.txt");
    comparer.compare("comparison.txt");
}
finally {
    comparer.dispose();
}
```

Voici le document de sortie qui montre le résultat de la comparaison de la correspondance de deux fichiers texte à l'aide du code ci-dessus.



{{< figure align=center src="images/text-files-comparison-using-java.png" alt="Comparer des fichiers texte à l'aide de Java">}}


## Comparez les fichiers PDF pour la différence de texte à l'aide de Java {#compare-pdf-files-in-java}

Nous pouvons comparer les fichiers PDF en utilisant le même code ci-dessus et en changeant simplement les extensions de fichier en ".pdf". Juste pour mentionner, le code ci-dessous compare deux fichiers pdf et montre les différences en Java.

```
// Compare two PDF file using Stream
Comparer comparer = new Comparer(new FileInputStream("source.pdf"));
comparer.add(new FileInputStream("target.pdf"));
comparer.compare(new FileOutputStream("result.pdf"));
```

Vous trouverez ci-dessous le résultat après avoir comparé les fichiers PDF.



{{< figure align=center src="images/pdf-files-text-comparison-using-java.png" alt="Comparaison de texte de fichier PDF">}}


## Voir également

* [Bibliothèque C # Diff pour comparer des fichiers texte][16]
* [Comparer deux fichiers ou plus en C#][17]

De nombreux autres exemples open source sont accessibles au public sur [GitHub Repository][18]. Vous pouvez télécharger et exécuter rapidement les exemples à l'aide du guide [de démarrage][19]. En cas de question, consultez la documentation ou contactez-nous à tout moment sur le [forum][20].







[1]: https://products.groupdocs.app/comparison/total
[2]: https://products.groupdocs.app/comparison/total
[3]: https://blog.groupdocs.com/2020/07/15/compare-text-word-pdf-files-with-java-difference-library/#compare-word-files
[4]: https://blog.groupdocs.com/2020/07/15/compare-text-word-pdf-files-with-java-difference-library/#compare-word-files-using-stream
[5]: https://blog.groupdocs.com/2020/07/15/compare-text-word-pdf-files-with-java-difference-library/#accept-or-reject-changes
[6]: https://blog.groupdocs.com/2020/07/15/compare-text-word-pdf-files-with-java-difference-library/#compare-text-files-in-java
[7]: https://blog.groupdocs.com/2020/07/15/compare-text-word-pdf-files-with-java-difference-library/#compare-pdf-files-in-java
[8]: https://products.groupdocs.com/comparison/java
[9]: https://downloads.groupdocs.com/comparison/java
[10]: https://apireference.groupdocs.com/comparison/java/com.groupdocs.comparison/Comparer
[11]: https://apireference.groupdocs.com/comparison/java/com.groupdocs.comparison/Comparer#add(java.lang.String)
[12]: https://apireference.groupdocs.com/comparison/java/com.groupdocs.comparison/Comparer#compare(java.lang.String)
[13]: https://apireference.groupdocs.com/comparison/java/com.groupdocs.comparison/Comparer
[14]: https://apireference.groupdocs.com/comparison/java/com.groupdocs.comparison/Comparer#add(java.lang.String)
[15]: https://apireference.groupdocs.com/comparison/java/com.groupdocs.comparison/Comparer#compare(java.lang.String)
[16]: https://blog.groupdocs.com/2020/04/30/groupdocs-comparison-for-net-c-sharp-diff-library-for-comparing-text-files/
[17]: https://blog.groupdocs.com/2020/03/10/compare-excel-word-pdf-files-in-csharp/
[18]: https://github.com/groupdocs-comparison/GroupDocs.Comparison-for-Java
[19]: https://docs.groupdocs.com/comparison/java/getting-started/
[20]: https://forum.groupdocs.com/c/conversion


