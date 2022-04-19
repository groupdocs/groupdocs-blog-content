---
title: "Supprimer les annotations des documents PDF ou Word à l'aide de C#"
date: Thu, 27 Jan 2022 14:29:00 +0000
draft: false
url: /fr/2022/01/27/remove-annotations-from-pdf-or-word-documents-using-csharp/
author: 'Shoaib Khan'
summary: "Les annotations sont couramment utilisées dans les documents pour souligner différentes observations et fournir des commentaires pour la discussion. Nous avons discuté dans des articles séparés, [comment ajouter différentes annotations au PDF](https://blog.groupdocs.com/2022/01/25/annotate-pdf-files-using-csharp) et [documents Word](https ://blog.groupdocs.com/2021/06/23/annotate-word-documents-using-csharp/) en utilisant C#. Aujourd'hui, cet article explique **comment supprimer les annotations de documents tels que les fichiers PDF et Word DOC/DOCX à l'aide de C#**.

Les sujets suivants sont abordés dans cet article :

* API d'annotation .NET
* Supprimer toutes les annotations
* Supprimer les annotations par ID
* Éliminer les annotations par objet d'annotation"
tags: ['Remove Annotation from PDF in CSharp', 'Remove Annotation in CSharp', 'Remove Annotations', 'Remove Annotations from Word in C#']
categories: ['GroupDocs.Annotation Product Family']
---

Les annotations sont couramment utilisées dans les documents pour souligner différentes observations et fournir des commentaires pour la discussion. Nous avons discuté dans des articles séparés de la façon d'ajouter différentes annotations aux documents PDF et Word à l'aide de C#. Aujourd'hui, cet article explique **comment supprimer les annotations de documents tels que les fichiers PDF et Word DOC/DOCX à l'aide de C#**.

Les sujets suivants sont abordés ci-dessous:

* [API d'annotation .NET](#dotnet-annotation-api)
* [Supprimer toutes les annotations](#remove-all-annotations)
* [Supprimer les annotations par ID](#remove-annotation-by-id)
* [Éliminer les annotations par objet d'annotation](#remove-annotations-by-obj)

## API .NET pour les annotations {#dotnet-annotation-api}

[GroupDocs.Annotation](https://products.groupdocs.com/annotation/) fournit l'API .NET pour gérer les annotations dans divers documents et images. Il permet d'ajouter, de supprimer et d'extraire des annotations à partir de PDF, Word et de nombreux autres documents. Vous pouvez consulter la documentation pour la liste complète des [formats de document pris en charge pour l'annotation](https://docs.groupdocs.com/annotation/net/supported-document-formats/).

Téléchargez son programme d'installation **DLLs** ou **MSI** à partir de la [section téléchargements](https://downloads.groupdocs.com/annotation) ou installez l'API dans votre application .NET via [NuGet](https://www.nuget.org/packages/groupdocs.annotation). Vous pouvez également utiliser la commande suivante du gestionnaire de packages.

```
PM> Install-Package GroupDocs.Annotation
```

## Supprimer toutes les annotations des documents PDF et Word à l'aide de C# {#remove-all-annotations}

Il existe plusieurs façons de supprimer les annotations des documents. Vous pouvez supprimer toutes les annotations à la fois, supprimer des annotations spécifiques en fournissant des ID ou supprimer des annotations spécifiques par objet d'annotation. Pour plus d'options, consultez l'article [documentation](https://docs.groupdocs.com/annotation/net/remove-annotation-from-document/).

Voici les étapes pour supprimer toutes les annotations des documents PDF ou Word DOC/DOCX à l'aide de C#.

* Chargez le document à l'aide de [Annotator](https://apireference.groupdocs.com/annotation/net/groupdocs.annotation/annotator).
* Initialiser la classe [Saving Options](https://apireference.groupdocs.com/annotation/net/groupdocs.annotation.options/saveoptions).
* Définissez le type d'annotation sur **Aucun**.
* Enregistrez le fichier, sans annotations, à l'aide de la méthode [Save()](https://apireference.groupdocs.com/annotation/net/groupdocs.annotation/annotator/methods/save/index).

Le code suivant montre comment supprimer des annotations de fichiers PDF ou Word à l'aide de C#.

```
// Supprimez toutes les annotations du document PDF à l'aide de C#
using (Annotator annotator = new Annotator("path/document.pdf"))
{
    annotator.Save("path/document-noAnnotation.pdf", new SaveOptions {AnnotationTypes = AnnotationType.None});
}
```

## Supprimer l'annotation par ID à l'aide de C# {#remove-annotation-by-id}

De même, vous pouvez fournir des ID d'annotation pour éliminer ces annotations du document. Fournissez simplement l'ID ou la liste des ID pour vous débarrasser de l'annotation spécifiée. Le code suivant montre comment supprimer les annotations des documents PDF ou Word en fournissant le ou les ID à l'aide de C#.

```
// Supprimer les annotations par ID du document PDF à l'aide de C#
using (Annotator annotator = new Annotator("path/document.pdf"))
{
    annotator.Remove(new List<int>{0,1});
    annotator.Save("path/document-remove-annotation.pdf");
}
```

## Supprimer l'annotation par objet d'annotation à l'aide de C# {#remove-annotations-by-obj}

Vous pouvez également vous débarrasser de l'annotation spécifique en prouvant l'objet Annotation. Pour le montrer, l'exemple de code suivant supprime les annotations des documents PDF ou Word en utilisant des objets d'annotation en C#.

```
// Supprimer les annotations sélectives du document PDF à l'aide de C#
using (Annotator annotator = new Annotator("path/document.pdf"))
{
    annotator.Remove(annotator.Get()[0]);
    annotator.Save("path/document-remove-annotation.pdf");
}
```

## Conclusion

Pour conclure, vous avez appris à supprimer les annotations des documents à l'aide de C#. Plus précisément, nous avons supprimé toutes les annotations des fichiers PDF et Word. Plus tard, nous avons supprimé les annotations en fournissant des identifiants et également en prouvant les objets d'annotation.

Créez votre propre application .NET de suppression d'annotations de documents à l'aide de **GroupDocs.Annotation pour .NET**. Pour en savoir plus sur l'API, consultez la [documentation](https://docs.groupdocs.com/annotation/net/) et le référentiel [GitHub](https://github.com/groupdocs-annotation). Pour toute autre question, contactez le support sur le [forum](https://forum.groupdocs.com/).

## Voir également

* [Annoter ou annoter des fichiers PDF à l'aide de C#](https://blog.groupdocs.com/2022/01/25/annotate-pdf-files-using-csharp/)
* [Annoter ou annoter des fichiers Word à l'aide de C#](https://blog.groupdocs.com/2021/06/23/annotate-word-documents-using-csharp/)
* [Mise en surbrillance du PDF à l'aide d'annotations en C#](https://blog.groupdocs.com/2021/10/12/highlight-pdf-with-annotations-using-csharp/)
* [Créer des hyperliens en PDF à l'aide d'annotations en C#](https://blog.groupdocs.com/2021/10/16/create-hyperlinks-in-pdf-using-annotations-in-csharp/)





