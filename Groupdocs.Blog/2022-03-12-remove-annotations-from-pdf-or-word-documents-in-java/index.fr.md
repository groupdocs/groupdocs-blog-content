---
title: "Supprimer les annotations des documents PDF ou Word en Java"
date: Sat, 12 Mar 2022 16:43:18 +0000
draft: false
url: /fr/2022/03/12/remove-annotations-from-pdf-or-word-documents-in-java/
author: 'Shoaib Khan'
summary: "Les annotations sont couramment utilisées pour signaler des observations dans des documents. Ceux-ci peuvent également être utilisés pour fournir des commentaires pendant la discussion. Plus tôt, nous avons discuté de la [méthode Java pour ajouter différentes annotations aux documents PDF](https://blog.groupdocs.com/2021/04/18/annotate-pdf-files-using-java/). Cet article explique **comment supprimer les annotations de documents tels que les fichiers PDF et Word DOC/DOCX en Java**."
tags: ['Remove Annotation from PDF in Java', 'Remove Annotation in Java', 'Remove Annotations', 'Remove Annotations from Word in Java', 'Uncategorized']
categories: ['GroupDocs.Annotation Product Family']
---

Les annotations sont couramment utilisées pour signaler des observations dans des documents. Ceux-ci peuvent également être utilisés pour fournir des commentaires pendant la discussion. Plus tôt, nous avons discuté de la [méthode Java pour ajouter différentes annotations aux documents PDF](https://blog.groupdocs.com/2021/04/18/annotate-pdf-files-using-java/). Cet article explique **comment supprimer les annotations de documents tels que les fichiers PDF et Word DOC/DOCX en Java**.

Les sujets suivants sont abordés ci-dessous :

* [API Java d'annotation](#java-annotation-api)
* [Supprimer toutes les annotations](#remove-all-annotations)
* [Supprimer les annotations par ID](#remove-annotation-by-id)
* [Éliminer les annotations par objet d'annotation](#remove-annotations-by-obj)

## API Java pour les annotations {#java-annotation-api}

GroupDocs dispose d'une API Java qui permet de traiter les annotations dans divers documents et images. Il permet d'ajouter, de supprimer et d'extraire des annotations à partir de PDF, Word et de nombreux autres types de documents. Vous pouvez consulter la documentation pour la liste complète des [formats de document pris en charge pour l'annotation](https://docs.groupdocs.com/annotation/java/supported-document-formats/).

### Télécharger ou configurer

Téléchargez le fichier **JAR** à partir de la [section des téléchargements](https://downloads.groupdocs.com/annotation), ou obtenez simplement les dernières configurations de référentiel et de dépendance pour le pox.xml de votre **basé sur maven** Applications Java.

```
<repository>
	<id>GroupDocsJavaAPI</id>
	<name>GroupDocs Java API</name>
	<url>http://repository.groupdocs.com/repo/</url>
</repository>
<dependency>
        <groupId>com.groupdocs</groupId>
        <artifactId>groupdocs-annotation</artifactId>
        <version>21.7.2</version> 
</dependency>
```

## Supprimer toutes les annotations des documents PDF et Word en Java {#remove-all-annotations}

Il existe des moyens de supprimer les annotations des documents. Toutes les annotations peuvent être supprimées en une seule fois. Vous pouvez supprimer des annotations spécifiques en fournissant des ID ou supprimer des annotations spécifiques en fournissant l'objet d'annotation. Pour d'autres options, consultez la [documentation](https://docs.groupdocs.com/annotation/java/remove-annotation-from-document/).

Voici les étapes pour supprimer toutes les annotations des documents PDF et Word DOC/DOCX en Java.

* **Chargez** le document à l'aide de [Annotator](https://apireference.groupdocs.com/annotation/java/com.groupdocs.annotation/Annotator).
* Initialiser la classe [Saving Options](https://apireference.groupdocs.com/annotation/java/com.groupdocs.annotation.options.export/SaveOptions).
* **Définissez** le [type d'annotation](https://apireference.groupdocs.com/annotation/java/com.groupdocs.annotation.options.export/AnnotationType) sur **Aucun**.
* **Enregistrer** le fichier sans les annotations à l'aide de la méthode **save()**.

Le code Java suivant montre comment supprimer les annotations des fichiers PDF ou Word.

```
// Supprimez toutes les annotations du document PDF à l'aide de Java
final Annotator annotator = new Annotator("document.pdf");
SaveOptions saveOptions = new SaveOptions();
saveOptions.setAnnotationTypes(AnnotationType.None);
// Enregistrez le PDF sans plus d'annotations.
annotator.save("path/annotations-removed.pdf", saveOptions);
annotator.dispose();
```

## Supprimer l'annotation par ID en Java {#remove-annotation-by-id}

De même, vous pouvez fournir des ID d'annotation pour vous débarrasser des annotations indésirables des documents. Il s'agit simplement de préparer et de fournir la liste des identifiants pour éliminer les annotations répertoriées. Le code Java suivant montre comment supprimer les annotations des documents PDF ou Word en fournissant le ou les ID.

```
// Supprimer les annotations sélectionnées du document PDF à l'aide de Java
final Annotator annotator = new Annotator("document.pdf");
java.util.List<Integer> removalList = new java.util.ArrayList<>();
removalList.add(0);
removalList.add(1);
annotator.remove(removalList);

// Enregistrez le PDF avec les annotations supprimées.
annotator.save("path/annotations-removed.pdf", new SaveOptions());
annotator.dispose();
```

## Supprimer l'annotation par objet d'annotation en Java {#remove-annotations-by-obj}

Vous pouvez également vous débarrasser de l'annotation spécifique en prouvant l'objet **Annotation**. Afin de supprimer des annotations, le code Java suivant supprime les annotations des documents PDF ou Word à l'aide d'objets d'annotation.

```
// Supprimer les annotations sélectionnées du document PDF à l'aide de Java
final Annotator annotator = new Annotator("document.pdf");
java.util.List<AnnotationBase> annotations = annotator.get();
annotator.remove(annotations.get(0));

// Enregistrez le PDF avec les annotations supprimées.
annotator.save("path/annotations-removed.pdf", new SaveOptions());
annotator.dispose();
```

## Conclusion

Pour résumer, vous avez appris à supprimer les annotations des documents dans les applications Java. Au départ, nous avons supprimé toutes les annotations des documents PDF et Word. Plus tard, nous avons éliminé les annotations en fournissant des identifiants et également en prouvant les objets d'annotation. Essayez de créer votre propre application Java de suppression des annotations de document à l'aide de **[GroupDocs.Annotation for Java](https://products.groupdocs.com/annotation/java/)**. Pour en savoir plus sur l'API, consultez la [documentation](https://docs.groupdocs.com/annotation/java/) et le référentiel [GitHub](https://github.com/groupdocs-annotation). Pour toute autre question, contactez le support sur le [forum](https://forum.groupdocs.com/).

## Voir également

* [Annoter des fichiers PDF avec Java](https://blog.groupdocs.com/2021/04/18/annotate-pdf-files-using-java/)
* [Annoter des fichiers Word en Java](https://blog.groupdocs.com/2022/03/19/annotate-word-documents-in-java/)
* [Mise en surbrillance du PDF à l'aide d'annotations en Java](https://blog.groupdocs.com/2021/10/07/highlight-pdf-using-annotations-in-java/)
* [Créer des hyperliens en PDF à l'aide d'annotations en Java](https://blog.groupdocs.com/2021/10/09/create-hyperlinks-in-pdf-using-annotations-in-java/)





