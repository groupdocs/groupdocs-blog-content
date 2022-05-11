---
title: "Supprimer des pages d'un PDF en Java | Pair, impair, liste et plage"
seoTitle: "Supprimer des pages d'un PDF en Java | Pair, impair, liste et plage"
date: Fri, 22 Apr 2022 11:00:00 +0000
draft: false
description: "Supprimez n'importe quel ensemble de pages des fichiers PDF à l'aide de Java. Supprimer la liste des pages, toute plage donnée, les pages paires ou impaires des fichiers PDF dans les applications."
url: /fr/2022/04/22/remove-pages-from-pdf-in-java/
author: 'Shoaib Khan'
summary: "Lorsqu'un ancien document est mis à jour ; les pages obsolètes, obsolètes ou même hautement confidentielles doivent être supprimées de la dernière version du document. Dans cet article, nous allons apprendre **comment supprimer par programmation de telles pages des documents PDF en Java**. De plus, nous discuterons des différentes façons de supprimer la liste des pages, la plage de pages, les pages paires et impaires du document PDF."
tags: ['delete pages', 'delete pages in java', 'remove pages', 'remove pages in java', 'delete pages from pdf in java']
categories: ['GroupDocs.Merger Product Family']
---

Lorsqu'un ancien document est mis à jour ; les pages obsolètes, obsolètes ou même hautement confidentielles doivent être supprimées de la dernière version du document. Dans cet article, nous allons apprendre **comment supprimer par programmation de telles pages des documents PDF en Java**. De plus, nous discuterons des différentes façons de supprimer la liste des pages, la plage de pages, les pages paires et impaires du document PDF.

Les sujets suivants sont abordés ci-dessous :

- [API Java de suppression de page PDF] (#pdf-page-removal-java-api)
- [Supprimer la liste des pages] (#remove-pdf-pages-list-in-java)
- [Supprimer la plage de pages] (#remove-pdf-pages-range-in-java)
- [Supprimer les pages paires ou impaires dans la plage] (#remove-even-odd-pdf-pages-in-java)

## API Java pour supprimer des pages d'un PDF {#pdf-page-removal-java-api}

GroupDocs.Merger fournit l'API Java qui permet de supprimer par programmation des pages du document PDF. De plus, il permet de changer l'orientation des pages, de déplacer l'emplacement des pages, de diviser les documents, d'extraire et de faire pivoter les pages du document. Je vais utiliser ce [GroupDocs.Merger pour Java][1] pour supprimer différentes pages de fichiers PDF en Java. Pour les détails et autres fonctionnalités de l'API, vous pouvez consulter sa [documentation][2].

### Télécharger et configurer

Obtenez la bibliothèque à partir de la [section téléchargements][3]. Pour votre application Java basée sur Maven, ajoutez simplement la configuration pom.xml suivante. Après cela, vous pouvez essayer les exemples de cet article ainsi que les nombreux autres exemples disponibles sur [GitHub][4]. Pour plus de détails, vous pouvez visiter la [API Reference][5].

```
<repository>
	<id>GroupDocsJavaAPI</id>
	<name>GroupDocs Java API</name>
	<url>http://repository.groupdocs.com/repo/</url>
</repository>
<dependency>
        <groupId>com.groupdocs</groupId>
        <artifactId>groupdocs-merger</artifactId>
        <version>22.2</version> 
</dependency>
```

## Supprimer les pages sélectionnées du PDF en Java {#remove-pdf-pages-list-in-java}

Pour supprimer un ensemble de pages, il vous suffit de fournir la liste des numéros de pages du document PDF chargé. Les étapes ci-dessous permettent de supprimer la liste de pages sélectives fournie d'un document PDF en Java.

- Initialisez la classe [RemoveOptions][6] avec les **numéros de page** à supprimer.
- Instancier l'objet [Merger][7] avec le chemin ou le flux du document source.
- Appelez la méthode removePages() pour supprimer les pages listées.
- Appelez la méthode save() appropriée pour enregistrer le document résultant.

L'exemple de code Java suivant supprime les 2e et 4e pages sélectionnées du document PDF.

```
// Supprimer des pages sélectives du PDF en Java
RemoveOptions removeOptions = new RemoveOptions(new int[] { 2, 4 });

Merger merger = new Merger("path/document-pdf");
merger.removePages(removeOptions);
merger.save("path/selected-pages-removed.pdf");
```

## Supprimer la plage de pages du PDF en Java {#remove-pdf-pages-range-in-java}

De même, vous pouvez supprimer n'importe quelle plage de pages dans votre document PDF. Les étapes suivantes permettent de supprimer n'importe quelle plage de pages des fichiers PDF en Java.

- Initialiser [RemoveOptions][6].
- Fournissez la **plage de pages** en définissant le numéro de page de **début** et de **fin**.
- Instancier l'objet [Merger][7] avec le chemin ou le flux du document source.
- Appelez la méthode removePages() avec la plage.
- Appelez la méthode save() appropriée pour enregistrer le document résultant.

L'exemple de code Java suivant supprime toutes les pages du document PDF dans la plage fournie, c'est-à-dire 3 à 5.

```
// Supprimer la plage de pages sélectionnée du PDF en Java
RemoveOptions removeOptions = new RemoveOptions(3, 5);

Merger merger = new Merger("path/document-pdf");
merger.removePages(removeOptions);
merger.save("path/pages-range-removed.pdf");
```

## Supprimer les pages paires ou impaires du PDF en Java {#remove-even-odd-pdf-pages-in-java}

Vous pouvez également supprimer toutes les pages paires/impaires du document. Les étapes suivantes montrent comment supprimer les pages paires ou impaires du fichier PDF dans la plage donnée en Java.

- Initialiser la classe [RemoveOptions][6] avec la plage de pages.
- Réglez le mode sur **pair** ou **impair**.
- Instancier l'objet [Merger][7] avec le chemin ou le flux du document source.
- Appelez la méthode removePages() avec les options de suppression.
- Appelez la méthode save() appropriée pour enregistrer le document résultant.

L'extrait de code Java suivant supprime toutes les pages impaires de l'ensemble du document PDF.

```
// Supprimez toutes les pages impaires du PDF dans la plage donnée en Java
RemoveOptions removeOptions = new RemoveOptions(1,6, RangeMode.OddPages);

Merger merger = new Merger("path/document-pdf");
merger.removePages(removeOptions);
merger.save("path/odd-pages-removed.pdf");
```

L'exemple de code Java suivant supprime toutes les pages paires du document PDF dans la plage fournie, c'est-à-dire 1-5.

```
// Supprimer toutes les pages paires du PDF dans la plage donnée en Java
RemoveOptions removeOptions = new RemoveOptions(1,5, RangeMode.EvenPages);

Merger merger = new Merger("path/document-pdf");
merger.removePages(removeOptions);
merger.save("path/even-pages-removed.pdf");
```

## Obtenez une licence API gratuite

Vous pouvez [obtenir une licence temporaire gratuite][8] afin d'utiliser l'API sans les limitations d'évaluation.

## Conclusion

Pour conclure, nous avons appris à supprimer différents ensembles de pages de documents PDF dans les applications Java. Plus précisément, nous avons vu comment supprimer des pages en fournissant des numéros de page et des plages de pages. De plus, nous avons vu comment supprimer les pages paires ou impaires de n'importe quel document PDF en Java. Vous pouvez essayer de créer votre propre application pour éliminer tout ensemble de pages de vos fichiers PDF.

Pour plus de détails sur l'API, consultez la documentation. Pour toute question, contactez-nous via le [forum][14].

## Voir également
- [Fichiers PDF en filigrane en Java][9]
- [Réorganiser les pages PDF en Java][10]
- [Recherche de mots et remplacement de texte dans un PDF en Java][11]
- [Convertir PDF en niveaux de gris en Java][12]
- [Protection par mot de passe des fichiers PDF en Java][13]

[1]: https://products.groupdocs.com/merger/java
[2]: https://docs.groupdocs.com/merger/java/
[3]: https://downloads.groupdocs.com/merger/java
[4]: https://github.com/groupdocs-merger/GroupDocs.Merger-for-Java
[5]: https://apireference.groupdocs.com/merger/java
[6]: https://apireference.groupdocs.com/merger/java/com.groupdocs.merger.domain.options/RemoveOptions
[7]: https://apireference.groupdocs.com/merger/java/com.groupdocs.merger/Merger
[8]: https://purchase.groupdocs.com/temporary-license
[9]: https://blog.groupdocs.com/2021/06/26/add-watermark-to-pdf-in-java/
[10]: https://blog.groupdocs.com/2022/03/10/move-pdf-pages-in-java/
[11]: https://blog.groupdocs.com/2022/03/08/find-and-replace-text-in-pdf-in-java/
[12]: https://blog.groupdocs.com/2022/03/02/convert-pdf-to-grayscale-jpg-png-images-in-java/
[13]: https://blog.groupdocs.com/2021/12/07/password-protect-pdf-files-in-java/
[14]: https://forum.groupdocs.com/
