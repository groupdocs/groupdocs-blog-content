---
title: 'Best Practices in Metadata Management'
date: Tue, 03 Sep 2019 11:03:09 +0000
draft: false
url: /2019/09/03/best-practices-in-metadata-management/
author: 'Muhammad Umar'
summary: ''
tags: ['JPEG Photo Parser', 'Metadata', 'metadata management']
categories: ['GroupDocs.Metadata for .NET Releases', 'GroupDocs.Metadata Product Family']
---

Before going in-depth to Metadata management, let's discuss what the metadata is? The Metadata summarizes basic information about data. In other words, it's an information which describes the data that contained in something like a web page, document, or file. Another way to think of metadata is as a short explanation or summary of what the data is.

A simple example of metadata for a document might include a collection of information like the author, file size, date the document was created, and keywords to describe the document. Metadata for a music file might include the artist's name, the album, and the year it was released.

## Types of Metadata {#mntl-sc-block_1-0-8}

Metadata comes in several types and is used for a variety of broad purposes that can be roughly categorized as a business, technical, or operational.

*   **Descriptive:** Metadata properties include title, subject, genre, author, and creation date, for example.
*   **Rights:** Metadata might include copyright status, rights holder, or license terms.
*   **Technical:** Metadata properties include file types, size, creation date and time, and type of compression. Technical metadata is often used for digital object management and interoperability.
*   **Preservation:** Metadata is used in navigation. Example preservation metadata properties include an item's place in a hierarchy or sequence.
*   **Markup languages:** Include metadata used for navigation and interoperability. Properties might include heading, name, date, list, and paragraph.

Metadata in files helps to find and working with various types of files. Writing meaningful metadata saves a lot of time in future work. Having the ability to filter through that metadata makes it much easier for someone to locate a specific document.

## Metadata API as a Metadata Management Tool {#IntroductiontoGroupDocs.MetadataforJava-WhatisGroupDocs.Metadata?}

Keeping above in mind, The **[GroupDocs.Metadata API](https://products.groupdocs.com/metadata)** is developed to make life easier while working with metadata. It is a very powerful and easy to use API that provides all basic metadata operations i.e (view, add, modify, remove) for a number of file formats. API gets the file as an input and makes its metadata accessible to the user. Now, it's up to the user to perform any of his operations on this metadata.

Let's discuss a business case regarding metadata management by using [GroupDocs.Metadata API.](https://products.groupdocs.com/metadata)

## Finding Photos Made on Specific Camera

Digital Images may contain some useful information in the form of metadata. As soon as we capture a digital photograph, the camera generates a wide range of information about the image i-e camera's information, author's information, GPS information, and much more.

We can manually access the image details/metadata by going to images' properties to find:

*   Images that were taken on a specific camera
*   Images with a specific subject
*   Images of a specific artist/author
*   Images that were taken at a specific place/location

But what if we are dealing with a huge number of images just, like, for example, Flicker does? It's the mother of thousands of directories containing millions of images. Even a superhuman will require a considerable amount of time and effort to find the images matching some certain metadata property (as mentioned above). It is a serious problem, but only when we do not have [GroupDocs.Metadata API](https://products.groupdocs.com/metadata).

Below is an easy example of API usage in the implementation of this use case.

## Photo Parser in C#

Let's write a PhotoParser class in C#:

{{< gist GroupDocsGists 8ab4ded217d192d563f285c3fba7c1c2 "JpegPhotoParser.cs" >}}

## Photo Parser in Java

Java guys will write as follows:

{{< gist GroupDocsGists f99ff3aa0e4362d4d677a62f4b018015 "PhotoParser.java" >}}

Suppose, an image collection may contain [JPEG](https://wiki.fileformat.com/image/jpeg/) images captured by a Sony Camera. Its metadata looks like following screenshot:



{{< figure align=center src="images/rBNaxgN.png" alt="" caption="<br><br>">}}


It's time to call the PhotoParser methods to get the list of images which were captured by a Sony camera:

{{< gist GroupDocsGists 196c21fae6f7bd8282b61dc4add34b54 "JpegPhotoParserUsage.cs" >}}

Java guys will call the methods like:

{{< gist GroupDocsGists 4ece21a53aec0339819d3d420aad1900 "photoParserUsage.java" >}}

The output will be appeared like the following screenshot:



{{< figure align=center src="images/vNcT40l.png" alt="">}}


The complete ready to run code sample is available on [GitHub](https://github.com/groupdocs-metadata).




