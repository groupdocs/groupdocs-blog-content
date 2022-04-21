---
title: "Rechercher et supprimer des filigranes de documents en Java"
date: Mon, 30 Nov 2020 10:55:51 +0000
draft: false
url: /fr/2020/11/30/trouver-et-supprimer-les-filigranes-des-documents-en-java/
aliases:
- /2019/10/10/trouver-et-supprimer-les-filigranes-des-documents-en-java/
author: 'Shoaib Khan'
summary: "Cet article est utile aux développeurs **Java** qui recherchent un moyen de **rechercher et supprimer du texte** ou des **filigranes d'image** dans **PDF, Word, Excel, PowerPoint** et **Visio ** documents. Dans l'un de nos articles, nous avons appris [trouver et supprimer les filigranes des documents en C#][1]. Passons maintenant à un aperçu rapide d'une API Java qui permet d'ajouter, de rechercher et de supprimer des filigranes de divers documents de différentes manières."
tags: ['find and remove watermarks in Java', 'find watermarks in Java', 'remove watermarks using Java', 'watermarking API for Java']
categories: ['GroupDocs.Watermark Product Family']
---

Cet article est utile aux développeurs **Java** qui recherchent un moyen de **rechercher et supprimer du texte** ou des **filigranes d'image** dans **PDF, Word, Excel, PowerPoint** et **Visio ** documents. Dans l'un de nos articles, nous avons appris [trouver et supprimer les filigranes des documents en C#][2]. Passons maintenant à un aperçu rapide d'une API Java qui permet d'ajouter, de rechercher et de supprimer des filigranes de divers documents de différentes manières.

## API Java pour le filigrane et la suppression

**[GroupDocs.Watermark pour Java][3]** L'API prend en charge l'ajout de filigranes de texte et d'image à une large gamme de formats de documents. De plus, il a également la capacité de trouver et de supprimer les filigranes des documents. L'API trouve également les objets de filigrane qui sont ajoutés à l'aide des outils tiers. Alors laissez-moi vous montrer comment vous pouvez supprimer le filigrane d'un document en quelques étapes en Java.

Vous pouvez obtenir le JAR à partir de la section [downloads][4] ou ajouter la configuration suivante dans pom.xml de votre application Java basée sur Maven. Pour plus de détails sur l'API, visitez [API Reference][5].

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
        <artifactId>groupdocs-watermark</artifactId>
        <version>20.5</version> 
</dependency>
```

## Étapes pour supprimer les filigranes d'un document en Java

Avant de commencer, jetez un œil au document PDF suivant qui contient un filigrane de texte ainsi qu'un filigrane d'image. Nous allons utiliser ce document et en supprimer les filigranes.



{{< figure align=center src="images/watermarkedpdf.png" alt="Fichier PDF avec filigranes - GroupDocs">}}


**1.** Créez un nouveau projet.

**2.** Ajoutez les importations suivantes.

```
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.search.ImageDctHashSearchCriteria;
import com.groupdocs.watermark.search.ImageSearchCriteria;
import com.groupdocs.watermark.search.PossibleWatermarkCollection;
import com.groupdocs.watermark.search.SearchCriteria;
import com.groupdocs.watermark.search.TextSearchCriteria;
```

**3\.** Créez une instance de la classe **Watermarker** et chargez le document source.

```
Watermarker watermarker = new Watermarker("filepath/watermarked.pdf");
```

**4.** Trouvez les filigranes en fonction des critères de recherche configurés à l'aide de la méthode **recherche**.

```
// Configurer le critère de recherche pour le filigrane d'image
ImageSearchCriteria imageSearchCriteria = new ImageDctHashSearchCriteria("filepath/watermark.png");
imageSearchCriteria.setMaxDifference(0.2); // Set how much the watermark can differ from the provided image.

// Configurer le critère de recherche pour le filigrane de texte
TextSearchCriteria textSearchCriteria = new TextSearchCriteria("CONFIDENTIAL");

// Combiner les critères de recherche texte et image
SearchCriteria combinedSearchCriteria = imageSearchCriteria.or(textSearchCriteria);
PossibleWatermarkCollection possibleWatermarks = watermarker.search(combinedSearchCriteria);
```

**5.** Parcourez la collection de filigranes et supprimez les filigranes à l'aide de la méthode **removeAt**.

```
//Parcourez la collection de filigranes possibles, vérifiez et supprimez les filigranes
while(possibleWatermarks.getCount()>0)
{
	if (possibleWatermarks.get_Item(0).getImageData() != null)
	{
		possibleWatermarks.removeAt(0);
		System.out.println("Removed Image Watermark.");
	}
	else
	{
		possibleWatermarks.removeAt(0);
		System.out.println("Removed Text Watermark.");
	}
} 
```

**6\.** Enregistrez le document résultant à l'aide de la méthode **save**.

```
 watermarker.save("filepath/without_watermark.pdf");
 watermarker.close(); 
```

Il existe également ** d'autres moyens de rechercher et de supprimer des filigranes ** de documents en utilisant différentes méthodes. Si vous souhaitez supprimer tous les filigranes d'un document, ou si vous souhaitez vous débarrasser de certains filigranes sélectifs de différents types :

* Vous pouvez collecter tous les filigranes possibles.
* Parcourez la collection de filigranes ou accédez directement au filigrane avec index.
* Vérifiez le type de filigrane et les données, si nécessaire.
* Retirez-le, s'il répond à vos besoins.

**remove**, **removeAt** et **clear** sont les méthodes qui peuvent être utilisées en conséquence pour supprimer les filigranes. Pour plus de détails, vous pouvez consulter l'article de la **documentation** sur [la recherche et la modification des filigranes en Java][6].

### Code complet

```
// Rechercher et supprimer des filigranes dans des documents PDF, Word, Excel, PowerPoint et Visio en Java
Watermarker watermarker = new Watermarker("filepath/watermarked.pdf"); // Provide any supported document

// Configurer le critère de recherche pour le filigrane d'image
ImageSearchCriteria imageSearchCriteria = new ImageDctHashSearchCriteria("filepath/watermark.png");
imageSearchCriteria.setMaxDifference(0.2); // Set how much the watermark can differ from the provided image.

// Configurer le critère de recherche pour le filigrane de texte
TextSearchCriteria textSearchCriteria = new TextSearchCriteria("CONFIDENTIAL");

// Combiner les critères de recherche texte et image
SearchCriteria combinedSearchCriteria = imageSearchCriteria.or(textSearchCriteria);
PossibleWatermarkCollection possibleWatermarks = watermarker.search(combinedSearchCriteria);

//Parcourez la collection de filigranes possibles, vérifiez et supprimez les filigranes
while(possibleWatermarks.getCount()>0)
{
	if (possibleWatermarks.get_Item(0).getImageData() != null)
	{
		possibleWatermarks.removeAt(0);
		System.out.println("Removed Image Watermark.");
	}
	else
	{
		possibleWatermarks.removeAt(0);
		System.out.println("Removed Text Watermark.");
	}
} 
watermarker.save("filepath/without_watermark.pdf");
watermarker.close(); 
```

### Résultats

Ce qui suit est la capture d'écran du document PDF résultant que nous obtenons après avoir supprimé les filigranes.



{{< figure align=center src="images/withoutwatermarkpdf.png" alt="Fichier PDF résultant après suppression des filigranes à l'aide de l'API Java Watermarking de GroupDocs">}}


## Conclusion

Je pense qu'en tant que développeur Java, vous n'hésiterez plus à rechercher puis à supprimer tout type de filigrane dans les **documents de traitement de texte**, **feuilles de calcul**, **présentations**, pris en charge par Microsoft et OpenOffice, Documents **PDF** et dessins **Visio**.

Vous pouvez en savoir plus sur l'API à partir de la [documentation][7]. En cas de questions, contactez-nous @ [forum][8].

## Voir également

* [Ajouter des filigranes aux images en Java][9]
* [Rechercher et supprimer les filigranes des documents en C#][10]
* [Ajouter des filigranes aux images ou aux images dans les documents à l'aide de C#][11]







[1]: https://blog.groupdocs.com/2020/11/27/find-and-remove-watermarks-from-documents-in-csharp/
[2]: https://blog.groupdocs.com/2020/11/27/find-and-remove-watermarks-from-documents-in-csharp/
[3]: https://products.groupdocs.com/watermark/java
[4]: https://downloads.groupdocs.com/watermark/java
[5]: https://apireference.groupdocs.com/watermark/java
[6]: https://docs.groupdocs.com/watermark/java/searching-and-modifying-watermarks/
[7]: https://docs.groupdocs.com/watermark/java/
[8]: https://forum.groupdocs.com/c/watermark
[9]: https://blog.groupdocs.com/2020/09/15/add-watermark-to-images-in-java/
[10]: https://blog.groupdocs.com/2020/11/27/find-and-remove-watermarks-from-documents-in-csharp/
[11]: https://blog.groupdocs.com/2019/10/21/add-watermark-to-images-using-csharp-dotnet-api/


