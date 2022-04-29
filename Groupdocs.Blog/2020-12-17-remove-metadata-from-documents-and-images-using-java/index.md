---
seoTitle: "Clean Metadata of Documents and Images using Java"
title: 'Metadata Cleaner for Documents and Images using Java'
date: Thu, 17 Dec 2020 10:02:00 +0000
draft: false
url: /2020/12/17/remove-metadata-from-documents-and-images-using-java/
author: 'Shoaib Khan'
description: "Java API to remove all or selective metadata properties of DOCX, XLSX, PPTX, PDF documents, JPEG, PNG, WebP images, email, eBooks, Visio Drawings, Zip, etc."
summary: '**Metadata** is the data that provides information about the actual data. It is commonly described as "**data about data**". When sending a file to someone, it is not a good practice to send metadata along. It can reveal your information to the receiver that you may not want to share. Some of the examples include; Name, Company Name, Document Modification Date, Make and Model of Camera, etc. In this article, we will be **programmatically removing metadata from the images and documents using Java**.'
tags: ['metadata cleaner using Java', 'remove metadata from documents in Java', 'remove metadata from images in Java', 'remove metadata using Java']
categories: ['GroupDocs.Metadata Product Family']
---

**Metadata** is the data that provides information about the actual data. It is commonly described as "**data about data**". When sending a file to someone, it is not a good practice to send metadata along. It can reveal your information to the receiver that you may not want to share. Some of the examples include; Name, Company Name, Document Modification Date, Make and Model of Camera, etc. In this article, we will be **programmatically removing metadata from the images and documents using Java**.

*   [Java Metadata Cleaner API][1]
*   [Remove Metadata from Documents][2]
*   [Clean Metadata from Images][3]
*   [Remove Selective Metadata from Documents and Images][4]

## Java Metadata Cleaner API {#java-metadata-cleaner-api}

[GroupDocs.Metadata for Java][5] is a metadata API for Java that supports most of the popular metadata standards like EXIF, XMP, IPTC, ID3 tag, etc. It allows Java developers to add, modify, extract, and remove metadata with various options from a large list of [supported formats][6] of documents, images, and other files.

Steps in this article and code samples use GroupDocs.Metadata API. So before you proceed, please make sure to prepare the development environment using any of the following options:

*   Get the JAR file from the [downloads][7] section.
*   Add the following pom.xml configuration in your Maven-based java applications

```
<repository>
	<id>GroupDocsJavaAPI</id>
	<name>GroupDocs Java API</name>
	<url>http://repository.groupdocs.com/repo/</url>
</repository>
<dependency>
        <groupId>com.groupdocs</groupId>
        <artifactId>groupdocs-metadata</artifactId>
        <version>20.11</version> 
</dependency>
```

## Remove Metadata from Documents using Java {#remove-documents-metadata}

To remove all the available metadata properties without applying any filter, and to stay safe in the era of COVID-19, use the **sanitize** method. The following are the steps to remove metadata from the documents using GroupDocs.Metadata for Java.

*   Instantiate the object of the [Metadata][8] class, passing the path of the target document as the parameter.
*   Call the [sanitize][9] method. It returns the number of the removed metadata properties.
*   Save the output file with cleared metadata using the [save][10] method.

The following Java code sample shows how to remove and clear metadata from the document.

{{< gist GroupDocsGists 9aa3d162544a32eeff377b6caa6fdf4a "DocumentMetadataCleaner.java" >}}

## Remove Metadata from Images using Java {#remove-images-metadata}

If you want to remove all the metadata from your images using Java, you can use the same sanitize method by following the same steps:

*   Create the object of the [Metadata][11] class, passing the target document path as the parameter.
*   Call the [sanitize][12] method.
*   Save the output file using the [save][13] method.

{{< gist GroupDocsGists 9aa3d162544a32eeff377b6caa6fdf4a "ImageMetadataCleaner.java" >}}

## Remove Selective Metadata from Documents and Images using Java {#remove-selective-metadata}

It is not always required to remove all the available metadata from the files, however, we sometimes want to remove the selective metadata properties. The following steps show how to locate and remove the metadata using the specific name of the property.

*   Create [Metadata][14] object to load the targeted document or image file.
*   Create personalized specifications to find the metadata properties.
*   Call the [removeProperties][15] method and pass the personalized specifications.
*   Save the output file using the [save][16] method.

{{< gist GroupDocsGists 6114128ca015cbb1740cd8e05fd62fb3 "RemoveSpecificMetadataProperties.java" >}}

## Conclusion

In this article, we learned cleaning metadata from documents and images using Java. Now you can build your own metadata cleaner java application. It can support removing metadata from word-processing documents, spreadsheets, presentations, PDF files, images, emails, eBooks, drawings, zip files, and many more. You can explore more about the Java metadata API from the [documentation][17].

## See Also

*   [Remove Metadata of Documents and Images using C#][18]
*   [Manage EXIF Data of Images using Java][19]
*   [Manage EXIF Data of Images in C#][20]







[1]: #java-metadata-cleaner-api
[2]: #remove-documents-metadata
[3]: #remove-images-metadata
[4]: #remove-selective-metadata
[5]: https://products.groupdocs.com/metadata/java
[6]: https://docs.groupdocs.com/metadata/java/supported-document-formats/
[7]: https://downloads.groupdocs.com/metadata/java
[8]: https://apireference.groupdocs.com/metadata/java/com.groupdocs.metadata/Metadata
[9]: https://apireference.groupdocs.com/metadata/java/com.groupdocs.metadata/Metadata#sanitize()
[10]: https://apireference.groupdocs.com/metadata/java/com.groupdocs.metadata/Metadata#save(java.lang.String)
[11]: https://apireference.groupdocs.com/metadata/java/com.groupdocs.metadata/Metadata
[12]: https://apireference.groupdocs.com/metadata/java/com.groupdocs.metadata/Metadata#sanitize()
[13]: https://apireference.groupdocs.com/metadata/java/com.groupdocs.metadata/Metadata#save(java.lang.String)
[14]: https://apireference.groupdocs.com/metadata/java/com.groupdocs.metadata/Metadata
[15]: https://apireference.groupdocs.com/metadata/java/com.groupdocs.metadata/Metadata#removeProperties(com.groupdocs.metadata.search.Specification)
[16]: https://apireference.groupdocs.com/metadata/java/com.groupdocs.metadata/Metadata#save(java.lang.String)
[17]: https://docs.groupdocs.com/metadata/java/
[18]: https://blog.groupdocs.com/2020/12/29/remove-metadata-of-documents-and-images-using-csharp/
[19]: https://blog.groupdocs.com/2020/05/12/handle-exif-data-of-jpg-png-webp-images-in-java/
[20]: https://blog.groupdocs.com/2020/05/13/manage-exif-data-in-csharp-net-for-jpeg-png-tiff-webp-images/

