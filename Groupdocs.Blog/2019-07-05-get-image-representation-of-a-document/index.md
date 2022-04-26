---
title: 'Get Image Representation of a Document'
date: Fri, 05 Jul 2019 09:33:37 +0000
draft: false
url: /2019/07/05/get-image-representation-of-a-document/
author: 'Atir Tahir'
summary: ''
tags: []
categories: ['GroupDocs.Merger for Java', 'GroupDocs.Merger Product Family']
---

Did you ever wish to get image representation of a document? GroupDocs.Merger for Java [19.6](https://docs.groupdocs.com/display/mergerjava/GroupDocs.Merger+for+Java+19.6+Release+Notes) will make your wish come true. This feature is also helpful for front end application development.

Let's have a look at its implementation.  
{{< gist GroupDocsGists 55446d1d1f0cd81e51997397ee18cfc9 "getimagerepresentation.java" >}}  
It will return page number and page stream. Using _getPagePreview_ method you will get list of page image representations for a document of known format. So, source document file format should be specified.  
But what will happen if you don't specify file format or if it is undefined? The good thing is, it will be detected on the fly.

In this release, we introduced/added support for some new file formats:

*   XLT
*   XLTM
*   XLTX
*   TSV
*   LaTex

Let's now take a overview of improvements introduced:

*   ODP presentations loading is optimized
*   Ability to specify page number for every joining document. These pages will be included to the resultant document

Along with features and improvements we also emphasize on your feedback. Therefore, we'd like to mention some major bug fixes introduced in this release.

MovePage method was not working accurately for EPUB and EPS formats. This issue is now resolved.  
Issue in saving and loading of LaTex documents is resolved.

You can download latest version of the API [here](https://downloads.groupdocs.com/merger/java). Share your feedback or post your queries [here](https://forum.groupdocs.com/c/merger).




