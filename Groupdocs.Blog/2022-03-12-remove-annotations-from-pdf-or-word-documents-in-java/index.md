---
title: 'Remove Annotations from PDF or Word Documents in Java'
date: Sat, 12 Mar 2022 16:43:18 +0000
draft: false
url: /2022/03/12/remove-annotations-from-pdf-or-word-documents-in-java/
author: 'Shoaib Khan'
summary: 'Annotations are commonly used for pointing out observations in documents. These can also be used for providing feedback while discussion. Earlier, we discussed, the [Java way to add different annotations to PDF documents](https://blog.groupdocs.com/2021/04/18/annotate-pdf-files-using-java/). This article discusses **how to remove annotations from documents like PDF and Word DOC/DOCX files in Java**.'
tags: ['Remove Annotation from PDF in Java', 'Remove Annotation in Java', 'Remove Annotations', 'Remove Annotations from Word in Java', 'Uncategorized']
categories: ['GroupDocs.Annotation Product Family']
---

Annotations are commonly used for pointing out observations in documents. These can also be used for providing feedback while discussion. Earlier, we discussed, the [Java way to add different annotations to PDF documents](https://blog.groupdocs.com/2021/04/18/annotate-pdf-files-using-java/). This article discusses **how to remove annotations from documents like PDF and Word DOC/DOCX files in Java**.

The following topics are discussed below:

*   [Annotation Java API](#java-annotation-api)
*   [Remove all the Annotations](#remove-all-annotations)
*   [Remove Annotation(s) by IDs](#remove-annotation-by-id)
*   [Eliminate Annotations by Annotation Object](#remove-annotations-by-obj)

## Java API for Annotations {#java-annotation-api}

GroupDocs have Java API that allows dealing with annotations within various documents and images. It allows adding, deleting, and extraction of annotations from PDF, Word, and many other types of documents. You can visit the documentation for the complete list of [supported document formats for annotation](https://docs.groupdocs.com/annotation/java/supported-document-formats/).

### Download or Configure

Download the **JAR** file from the [downloads section](https://downloads.groupdocs.com/annotation), or just get the latest repository and dependency configurations for the pox.xml of your **maven-based** Java applications.

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

## Remove All Annotations from PDF & Word documents in Java {#remove-all-annotations}

There are ways to remove annotations from documents. All the annotations can be removed at once. You can remove specific annotation(s) by providing ID(s), or remove specific annotation by providing the annotation object. For other options, visit the [documentation](https://docs.groupdocs.com/annotation/java/remove-annotation-from-document/).

The following are the steps to remove all the annotations from PDF and Word DOC/DOCX document(s) in Java.

*   **Load** the document using [Annotator](https://apireference.groupdocs.com/annotation/java/com.groupdocs.annotation/Annotator).
*   Initialize [Saving Options](https://apireference.groupdocs.com/annotation/java/com.groupdocs.annotation.options.export/SaveOptions) class.
*   **Set** the [annotation type](https://apireference.groupdocs.com/annotation/java/com.groupdocs.annotation.options.export/AnnotationType) to **None**.
*   **Save** the file without the annotations using the **save()** method.

The following Java code shows how to remove annotations from PDF or Word files.

{{< gist GroupDocsGists 82c10a1efcae60359901cecbda8f6c20 "RemoveAnnotationsFromPDF.java" >}}

## Remove Annotation by IDs in Java {#remove-annotation-by-id}

Likewise, you can provide annotation ID(s) to get rid of the unwanted annotations from the documents. It's just about preparing and providing the list of IDs to eliminate the listed annotation(s). The following Java code shows how to remove the annotation(s) from PDF or Word documents by providing the ID(s).

{{< gist GroupDocsGists 82c10a1efcae60359901cecbda8f6c20 "RemoveAnnotationsbyIdsFromPdf.java" >}}

## Remove Annotation by Annotation Object in Java {#remove-annotations-by-obj}

You can also get rid of the specific annotation by proving the **Annotation** object. In order to delete annotations, the following Java code removes the annotation(s) from PDF or Word documents by using annotation objects.

{{< gist GroupDocsGists 82c10a1efcae60359901cecbda8f6c20 "RemoveAnnotationsbyAnnotationFromPdf.java" >}}

## Conclusion

To summarize, you learned to remove annotations from the documents within Java applications. Initially, we removed all the annotations from PDF & Word documents. Later we eliminated annotations by providing IDs and also by proving the annotation objects. Try building your own document annotations remover Java application using **[GroupDocs.Annotation for Java](https://products.groupdocs.com/annotation/java/)**. Learn more about the API from the [documentation](https://docs.groupdocs.com/annotation/java/) and the [GitHub](https://github.com/groupdocs-annotation) repository. For further queries, contact the support on the [forum](https://forum.groupdocs.com/).

## See Also

*   [Annotate PDF files using Java](https://blog.groupdocs.com/2021/04/18/annotate-pdf-files-using-java/)
*   [Annotate Word files in Java](https://blog.groupdocs.com/2022/03/19/annotate-word-documents-in-java/)
*   [Highlight PDF using Annotations in Java](https://blog.groupdocs.com/2021/10/07/highlight-pdf-using-annotations-in-java/)
*   [Create Hyperlinks in PDF using Annotations in Java](https://blog.groupdocs.com/2021/10/09/create-hyperlinks-in-pdf-using-annotations-in-java/)




