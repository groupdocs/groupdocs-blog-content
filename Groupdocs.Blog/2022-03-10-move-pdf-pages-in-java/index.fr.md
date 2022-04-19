---
title: "Comment réorganiser les pages PDF en Java"
date: Thu, 10 Mar 2022 14:49:46 +0000
draft: false
url: /fr/2022/03/10/move-pdf-pages-in-java/
author: 'Shoaib Khan'
summary: "PDF est l'un des formats de fichiers portables les plus utilisés. Pour les documents volumineux, il est toujours difficile de modifier l'ordre des pages en perdant la mise en forme. Cet article explique **comment réorganiser les pages PDF par programmation en Java**."
tags: ['Change Page Sequence in Java', 'Move Pages in Java', 'Rearrange Document', 'Rearrange Document Pages in Java', 'Rearrange PDF Pages', 'Rearrange PDF Pages in Java']
categories: ['GroupDocs.Merger Product Family']
---

PDF est l'un des formats de fichiers portables les plus utilisés. Pour les documents volumineux, il est toujours difficile de modifier l'ordre des pages sans perdre la mise en forme. Cet article explique **comment réorganiser les pages PDF par programmation en Java**.



{{< figure align=center src="images/rearrange-pdf-pages-in-java.jpg" alt="Réorganiser les pages PDF en Java">}}


## API Java pour réorganiser les pages PDF et fusionner des documents

GroupDocs fournit [GroupDocs.Merger pour Java](https://products.groupdocs.com/merger/java/) pour modifier l'ordre des pages dans les documents. Cette API permet de fusionner plusieurs documents, de supprimer, de diviser et d'extraire des pages, de faire pivoter et de modifier l'orientation des pages de document dans les applications. Pour les détails et autres fonctionnalités de l'API, vous pouvez consulter la [documentation](https://docs.groupdocs.com/merger/java/).

### Télécharger et configurer

Obtenez la bibliothèque à partir de la section [téléchargements](https://downloads.groupdocs.com/merger/). Pour votre application Java basée sur Maven, ajoutez simplement la configuration pom.xml suivante. Après cela, vous pouvez essayer les exemples de cet article ainsi que les nombreux autres exemples disponibles sur [GitHub](https://github.com/groupdocs-merger). Pour plus de détails, vous pouvez visiter la [référence API](https://apireference.groupdocs.com/merger/java).

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

## Réorganiser les pages PDF en Java

Voici les étapes qui vous aident à modifier la séquence des pages d'un document PDF en Java.

* Définissez la position existante et nouvelle de la page dans la classe [MoveOptions](https://apireference.groupdocs.com/merger/java/com.groupdocs.merger.domain.options/MoveOptions).
* Chargez le document PDF à l'aide de la classe [Merger](https://apireference.groupdocs.com/merger/java/com.groupdocs.merger/Merger).
* Utilisez la méthode **movePage()** pour réorganiser les pages en fonction des options définies.
* Enregistrez le fichier PDF réorganisé à l'aide de la méthode **save()**.

Le code source Java suivant réorganise les pages des documents PDF. Précisément, il déplace la 6ème page du document à la 1ère place.

```
// Réorganiser les pages des documents PDF en Java
int pageNumber = 6;
int newPageNumber = 1;
MoveOptions moveOptions = new MoveOptions(pageNumber, newPageNumber);

Merger merger = new Merger("path\document.pdf");

merger.movePage(moveOptions);
merger.save("path\rearranged-document.pdf");
```

Voici la sortie du code ci-dessus.



{{< figure align=center src="images/Screenshot-1024x454.png" alt="">}}


## Obtenez une licence API gratuite

Vous pouvez [obtenir une licence temporaire gratuite](https://purchase.groupdocs.com/temporary-license) afin d'utiliser l'API sans les limitations d'évaluation.

## Conclusion

Pour conclure, nous avons appris à réorganiser les documents en modifiant l'ordre des pages des fichiers PDF en Java au sein de l'application. Nous avons vu l'exemple courant qui change la position de la page. Vous pouvez essayer de créer une application simple capable d'organiser les fichiers PDF en mélangeant facilement leurs pages.

Pour plus de détails sur l'API, consultez la [documentation](https://docs.groupdocs.com/merger/). Pour toute question, contactez-nous via le [forum](https://forum.groupdocs.com/).

## Voir également

* [Protection par mot de passe des fichiers PDF en Java](https://blog.groupdocs.com/2021/12/07/password-protect-pdf-files-in-java/)
* [Façons de diviser des fichiers PDF en Java](https://blog.groupdocs.com/2021/10/19/split-pdf-files-in-java/)
* [Fusionner plusieurs types de fichiers en un seul à l'aide de Java](https://blog.groupdocs.com/2021/06/13/merge-multiple-file-types-using-java/)