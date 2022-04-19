---
title: "Comment réorganiser les pages dans Word en utilisant Java"
date: Tue, 01 Mar 2022 06:28:00 +0000
draft: false
url: /fr/2022/03/01/move-word-pages-using-java/
author: 'Shoaib Khan'
summary: "Les documents de traitement de texte sont l'un des formats de fichiers les plus courants utilisés pour rédiger des documents. Lorsque vous traitez plusieurs fichiers volumineux, il n'est jamais facile de déplacer des pages sans perdre la mise en forme. Afin de réorganiser les pages, cet article explique, **comment déplacer par programmation des pages dans les documents Word (DOC/DOCX) en Java**."
tags: ['Move Pages in DOC/DOCX', 'Move Pages in Java', 'Rearrange Document', 'Rearrange Document Pages in Java', 'Rearrange Pages in Java', 'Rearrange pages in Word']
categories: ['GroupDocs.Merger Product Family']
---



{{< figure align=center src="images/rearrange-word-pages-in-java.jpg" alt="Réorganiser les pages Word en Java">}}


Les documents de traitement de texte sont l'un des formats de fichiers les plus courants utilisés pour rédiger des documents. Lorsque vous traitez plusieurs fichiers volumineux, il n'est jamais facile de déplacer des pages sans perdre la mise en forme. Afin de réorganiser les pages, cet article explique, **comment déplacer par programmation des pages dans les documents Word (DOC/DOCX) en Java**.

## API Java pour déplacer des pages de documents Word

**[GroupDocs.Merger](https://products.groupdocs.com/merger/)** fournit l'[API Java pour gérer les documents et leurs pages](https://products.groupdocs.com/merger/java/). Il permet de déplacer, de supprimer, de diviser des documents et d'extraire des pages, de modifier l'orientation des pages et de faire pivoter les pages de documents dans les applications Java. J'utiliserai cette API pour déplacer des pages de fichiers DOC/DOCX. Pour les détails et autres fonctionnalités de l'API, vous pouvez consulter la [documentation](https://docs.groupdocs.com/merger/).

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

## Déplacer des pages dans des documents Word à l'aide de Java

Commandez simplement une page pour passer à la nouvelle position, elle le fera. Voici les étapes qui réorganisent les pages d'un document Word en Java.

* Définissez le numéro de page de la page cible et sa nouvelle position à l'aide de la classe [MoveOptions](https://apireference.groupdocs.com/merger/java/com.groupdocs.merger.domain.options/MoveOptions).
* Chargez le fichier DOC/DOCX à l'aide de la classe [Merger](https://apireference.groupdocs.com/merger/java/com.groupdocs.merger/Merger).
* Utilisez la méthode **movePage()** pour déplacer la page définie.
* Enregistrez le document réorganisé en utilisant la méthode **save()**.

Le code source Java suivant réorganise les pages d'un document Word. Précisément, il déplace la 7e page d'un document DOCX à la 2e place.

```
// Réorganiser les pages des documents de traitement de texte (DOC/DOCX) en Java
int pageNumber = 7;
int newPageNumber = 2;
MoveOptions moveOptions = new MoveOptions(pageNumber, newPageNumber);

Merger merger = new Merger("path\document.docx");

merger.movePage(moveOptions);
merger.save("path\rearranged-document.docx");
```

## Obtenez une licence API gratuite

Vous pouvez [obtenir une licence temporaire gratuite](https://purchase.groupdocs.com/temporary-license) afin d'utiliser l'API sans les limitations d'évaluation.

## Conclusion

Pour résumer, nous avons appris à modifier l'ordre des pages d'un document Word en Java. Nous avons vu l'exemple de code source qui a changé la position de la page dans un fichier DOCX. Vous pouvez créer votre propre application en ligne pour réorganiser les pages Word en ligne. Pour plus de détails sur l'API, consultez la [documentation](https://docs.groupdocs.com/merger/java/). Pour toute question, contactez-nous via le [forum](https://forum.groupdocs.com/).

## Voir également

* [Render Word documents as Minified HTML](https://blog.groupdocs.com/2022/03/04/render-word-documents-as-minified-html-in-java/)
* [Recherche de mots et remplacement de texte dans des documents Word](https://blog.groupdocs.com/2022/02/04/find-and-replace-text-in-word-documents-using-java/)
* [Comment protéger par mot de passe et supprimer la protection des documents Word](https://blog.groupdocs.com/2022/02/02/lock-unlock-word-documents-with-password-in-java/)
* [Afficher les documents Word en tant que page HTML réactive](https://blog.groupdocs.com/2021/09/23/view-word-documents-as-responsive-html-page-using-java/)
* [Insérer des objets OLE dans Word, Excel, PowerPoint](https://blog.groupdocs.com/2020/10/19/insert-ole-objects-in-word-excel-powerpoint-with-java/)





