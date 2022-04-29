---
seoTitle: "Remove Metadata of Documents and Images using C#"
title: 'Metadata Remover for Documents and Images using  C#'
date: Tue, 29 Dec 2020 14:14:00 +0000
draft: false
url: /2020/12/29/remove-metadata-of-documents-and-images-using-csharp/
author: 'Shoaib Khan'
description: "Remove selective metadata or clean all metadata properties using C# from DOCX, XLSX, PPTX, PDF, JPG/JPEG, PNG, WebP images, email, eBooks, Visio, Zip files."
summary: 'Today we are about to learn some ways to **programmatically remove or entirely clean metadata of documents as well as images using C#**. In an [earlier post][1], we discussed removing the selective as well as all the available metadata properties from documents and images using Java. It is sometimes important to hide personal information from the receiver, that is attached to the document. Following are the topics that will help you clean your files from metadata using C#.'
tags: ['metadata cleaner using csharp', 'remove metadata from documents in csharp', 'remove metadata from images in csharp', 'remove metadata using csharp']
categories: ['GroupDocs.Metadata Product Family']
---

Today we are about to learn some ways to **programmatically remove or entirely clean metadata of documents as well as images using C#**. In an [earlier post][2], we discussed removing the selective as well as all the available metadata properties from documents and images using Java. It is sometimes important to hide personal information from the receiver, that is attached to the document. Following are the topics that will help you clean your files from metadata using C#.

*   [.NET Metadata Cleaner API][3]
*   [Remove Metadata from Documents using C#][4]
*   [Clean Metadata from Images using C#][5]
*   [Remove Selective Metadata from Documents and Images using C#][6]

## .NET Metadata Removing API {#dotnet-metadata-removal-api}

To achieve what is planned, I will use [GroupDocs.Metadata for .NET][7] API that allows .NET developers to add, modify, extract, remove, or completely metadata from many [supported formats][8] of documents, images, and other files. The API supports metadata standards like EXIF, XMP, IPTC, ID3 tag, etc. You may [download][9] DLLs or MSI installer, or install it via [NuGet][10].

```
Install-Package GroupDocs.Metadata
```

## Remove Metadata from Documents using C# {#remove-documents-metadata-using-csharp}

In order to remove all the metadata properties without applying any specific filter, use the **Sanitize** method. The following are the steps to clean metadata from the documents like DOCX, PDF, XLSX, etc using GroupDocs.Metadata for .NET.

*   Start by creating [Metadata][11] class object and pass the path of the target document as the parameter.
*   Use [Sanitize][12] method to clear all the available metadata. It returns the number of the removed metadata properties.
*   Call [Save][13] method to save the output file with removed metadata.

The following C# code sample shows how to remove and clear metadata from a PDF document.

{{< gist GroupDocsGists 9aa3d162544a32eeff377b6caa6fdf4a "DocumentMetadataCleaner.cs" >}}

## Remove Metadata from Images using C# {#remove-images-metadata-using-csharp}

Whether you want to remove metadata from your documents or from your image files, the process will remain the same. Only the source document will be changed accordingly.

*   Create the object of the [Metadata][14] class and pass the document path as the parameter.
*   Call the [Sanitize][15] method to remove any available metadata properties.
*   Save the output file using the [Save][16] method.

The following C# code sample shows how to remove metadata from a JPG image.

{{< gist GroupDocsGists 9aa3d162544a32eeff377b6caa6fdf4a "ImageMetadataCleaner.cs" >}}

## Remove Selective Metadata from Documents and Images using C# {#remove-selective-metadata-using-csharp}

If it is not required to remove all the available metadata from the files, and we just want to remove only the selective metadata properties. The following steps allow you to locate and remove the targetted metadata properties using the specific name of the property.

*   Create an object of [Metadata][17] class to load the source document or image file.
*   Create personalized specifications to find the metadata properties.
*   Call the [RemoveProperties][18] method with the created personalized specifications.
*   Save the output file using the [Save][19] method.

{{< gist GroupDocsGists 6114128ca015cbb1740cd8e05fd62fb3 "RemoveSpecificMetadataProperties.cs" >}}

## Conclusion

We learned the ways to remove metadata from documents and images using C#. After going through this article, you would feel comfortable building your own metadata cleaner application using .NET. It can support metadata removal from MS Word document formats, spreadsheets, presentations, PDF files, images, emails, eBooks, drawings, zip files, and many more [file formats that are supported by the API][20].

You may further explore the [.NET Metadata Manipulation API][21] from the [documentation][22].

## See Also

*   [Remove Metadata of Documents and Images in Java][23]
*   [Manage EXIF Data of Images in C#][24]
*   [Manage EXIF Data of Images using Java][25]







[1]: https://blog.groupdocs.com/2020/12/17/remove-metadata-from-documents-and-images-using-java/
[2]: https://blog.groupdocs.com/2020/12/17/remove-metadata-from-documents-and-images-using-java/
[3]: #dotnet-metadata-removal-api
[4]: #remove-documents-metadata-using-csharp
[5]: #remove-images-metadata-using-csharp
[6]: #remove-selective-metadata-using-csharp
[7]: https://products.groupdocs.com/metadata/net
[8]: https://docs.groupdocs.com/metadata/net/supported-document-formats/
[9]: https://downloads.groupdocs.com/metadata/net
[10]: https://www.nuget.org/packages/groupdocs.metadata
[11]: https://apireference.groupdocs.com/metadata/net/groupdocs.metadata/metadata
[12]: https://apireference.groupdocs.com/metadata/net/groupdocs.metadata/metadata/methods/sanitize
[13]: https://apireference.groupdocs.com/metadata/net/groupdocs.metadata/metadata/methods/save/index
[14]: https://apireference.groupdocs.com/metadata/net/groupdocs.metadata/metadata
[15]: https://apireference.groupdocs.com/metadata/net/groupdocs.metadata/metadata/methods/sanitize
[16]: https://apireference.groupdocs.com/metadata/net/groupdocs.metadata/metadata/methods/save/index
[17]: https://apireference.groupdocs.com/metadata/net/groupdocs.metadata/metadata
[18]: https://apireference.groupdocs.com/metadata/net/groupdocs.metadata/metadata/methods/removeproperties
[19]: https://apireference.groupdocs.com/metadata/net/groupdocs.metadata/metadata/methods/save/index
[20]: https://docs.groupdocs.com/metadata/net/supported-document-formats/
[21]: https://products.groupdocs.com/metadata/net
[22]: https://docs.groupdocs.com/metadata/net/
[23]: https://blog.groupdocs.com/2020/12/17/remove-metadata-from-documents-and-images-using-java/
[24]: https://blog.groupdocs.com/2020/05/13/manage-exif-data-in-csharp-net-for-jpeg-png-tiff-webp-images/
[25]: https://blog.groupdocs.com/2020/05/12/handle-exif-data-of-jpg-png-webp-images-in-java/

