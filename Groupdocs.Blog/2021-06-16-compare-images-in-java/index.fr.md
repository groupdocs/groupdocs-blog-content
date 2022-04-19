---
title: "Comparaison d'images en Java pour repérer les différences"
date: Wed, 16 Jun 2021 14:07:12 +0000
draft: false
url: /fr/2021/06/16/comparer-images-en-java/
author: 'Shoaib Khan'
summary: 'Worried! What is the difference? **Better automate the photo comparison.** In this article, we will discuss how to programmatically find differences between two images. After going through this, you will easily compare any images and highlight the identified differences using Java.

Les sujets suivants sont traités ci-dessous :

* API Java pour comparer des images
* Comparer des images en Java pour mettre en évidence les différences

[Continuer la lecture...][1]'
tags: ['compare images in java', 'compare jpg in java', 'compare png in java', 'Image Comparison', 'Image Comparison Java API']
categories: ['GroupDocs.Comparison Product Family']
---

Inquiet! Quelle est la différence? **Mieux automatiser la comparaison de photos.** Dans cet article, nous verrons comment trouver par programme les différences entre deux images. Après avoir parcouru cela, vous trouverez facile de comparer toutes les images et de mettre en évidence les différences identifiées à l'aide de Java.



{{< figure align=center src="images/images-for-comparison.jpg" alt="Images identiques pour comparaison">}}


Les sujets suivants sont traités ci-dessous :

* [API Java pour comparer des images][2]
* [Comparer des images en Java pour mettre en évidence les différences][3]

## API Java de comparaison d'images {#image-comparison-java-api}

Dans cet article, j'utiliserai l'[API Java de GroupDocs.Comparison][4] pour comparer des images. Outre les formats d'image les plus utilisés, tels que PNG, JPG/JPEG et GIF, il existe une [large gamme de formats de fichiers pris en charge à des fins de comparaison][5]. De plus, l'API permet de comparer des documents de traitement de texte, des feuilles de calcul, des présentations, des dessins, des pages Web, des messages électroniques, des fichiers de code source et bien plus encore.

### Télécharger et configurer

Obtenez la bibliothèque de comparaison d'images à partir de la section [téléchargements][6]. Pour les applications Java basées sur Maven, ajoutez la configuration suivante dans pom.xml. Plus tard, vous pourrez essayer les exemples de cet article ainsi que de nombreux autres de [GitHub][7]. Pour plus de détails, vous pouvez également consulter la [API Reference][8].

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
        <artifactId>groupdocs-comparison</artifactId>
        <version>21.6</version> 
</dependency>
```

## Comparer des images en Java pour mettre en évidence les différences {#compare-image-and-highlight-differences}

Comparer les images et obtenir le résultat ne prend que 3 lignes de code. Vous pouvez suivre les étapes et utiliser le code source mentionné pour comparer n'importe laquelle de vos images JPG, PNG, BMP, DICOM, DjVu, GIF et autres. Vous pouvez identifier les dissemblances ou les variations parmi celles-ci au sein de l'application Java.

Les étapes suivantes montrent comment deux images peuvent être comparées pour les différences.

* Sélectionnez la première image à comparer à l'aide de la classe [Comparer][9].
* Ajoutez la deuxième image pour comparaison en utilisant la méthode [add][10] appropriée.
* Appelez la méthode [compare][11] pour obtenir le résultat de la comparaison des deux images.

Le code suivant montre comment comparer deux images en Java. Il compare deux images JPG et enregistre la sortie qui met en évidence les différences identifiées.

```
// Comparez deux images et mettez en évidence les différences en Java
Comparer comparer = new Comparer("image-a.jpg")
comparer.add("image-b.jpg");
comparer.compare("result-Image.jpg"); // This will return the path of the resultant image.
```

Voici l'image de sortie du code ci-dessus. En outre, la sortie inclut également le résumé de la comparaison.



{{< figure align=center src="images/compared-image.jpg" alt="Comparaison d'images automatisée et mise en évidence des différences">}}


## Obtenez une licence API gratuite

Vous pouvez [obtenir une licence temporaire gratuite][12] afin d'utiliser l'API sans les limitations d'évaluation.

## Conclusion

Pour conclure de cet article, nous avons appris à comparer des images en Java. Nous avons en outre mis en évidence les différences identifiées après la comparaison. Vous pouvez désormais créer votre propre application de comparaison de photos ou utiliser ces fonctionnalités dans vos applications Java.

Pour plus de détails, d'options et d'exemples, vous pouvez consulter les référentiels [documentation][13] et [GitHub][14]. Contactez-nous sur le [forum][15] pour vos questions.

## Voir également

* [Comparer des images en C# pour trouver les différences][16]
* [Comparer n'importe quel document utilisant Java][17]







[1]: https://blog.groupdocs.com/2021/06/16/compare-images-in-java/
[2]: #image-comparison-java-api
[3]: #compare-image-and-highlight-differences
[4]: https://products.groupdocs.com/comparison/
[5]: https://docs.groupdocs.com/comparison/java/supported-document-formats/
[6]: https://downloads.groupdocs.com/comparison/java
[7]: https://github.com/groupdocs-comparison
[8]: https://apireference.groupdocs.com/comparison/java
[9]: https://apireference.groupdocs.com/comparison/java/com.groupdocs.comparison/Comparer
[10]: https://apireference.groupdocs.com/comparison/java/com.groupdocs.comparison/Comparer#add(java.lang.String)
[11]: https://apireference.groupdocs.com/comparison/java/com.groupdocs.comparison/Comparer#compare(java.lang.String)
[12]: https://purchase.groupdocs.com/temporary-license
[13]: https://docs.groupdocs.com/comparison/java/
[14]: https://github.com/groupdocs-comparison
[15]: https://forum.groupdocs.com/
[16]: https://blog.groupdocs.com/2021/01/06/compare-images-in-csharp-dotnet/
[17]: https://blog.groupdocs.com/2020/07/15/compare-text-word-pdf-files-with-java-difference-library/


