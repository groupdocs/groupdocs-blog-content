---
title: 'Support of Password-Protected OneNote Documents in GroupDocs.Metadata for Java 19.1'
date: Thu, 24 Jan 2019 14:36:06 +0000
draft: false
url: /2019/01/24/support-of-password-protected-onenote-documents-in-groupdocs.metadata-for-java-19.1/
author: 'Usman Aziz'
summary: ''
tags: ['document-metadata', 'extract metadata', 'metadata API for Java', 'metadata extraction API for Java', 'metadata extractor']
categories: ['GroupDocs.Metadata for Java Releases', 'GroupDocs.Metadata Product Family']
---

![GroupDocs.Metadata for Java](http://blog.groupdocs.com/wp-content/uploads/sites/4/2017/12/groupdocs-metadata-java.png "GroupDocs.Metadata for Java")We are glad to announce the monthly release of [GroupDocs.Metadata for Java 19.1](https://products.groupdocs.com/metadata/java). In this version, we have introduced two new features and added seven enhancements. Using the latest version, you can extract metadata from Matroska Multimedia Container (.MKV) files. Furthermore, the latest version allows you to extract metadata from password-protected OneNote documents. Please have a look at the [release notes](https://docs.groupdocs.com/display/metadatajava/GroupDocs.Metadata+for+java+19.1+Release+Notes) for more details.

# Features Introduced

## Support for the Matroska Multimedia Container FilesThe latest release is capable of extracting metadata from the Matroska Multimedia Container (.MKV) files. The API provides the following features when working with .MKV files:

*   [Extracting MKV Format Metadata](https://docs.groupdocs.com/metadata/java/)
*   [Extracting Matroska Segment Info](https://docs.groupdocs.com/metadata/java/)
*   [Extracting Matroska Tag Metadata](https://docs.groupdocs.com/metadata/java/)
*   [Extracting Matroska Track Metadata](https://docs.groupdocs.com/metadata/java/)

## Support for Password-Protected OneNote DocumentsGroupDocs.Metadata for Java has the ability to work with password-protected documents. In the latest version, we have extended this ability by adding support for password-protected OneNote documents. The **_LoadOptions_** class is used to set the password for the protected documents. For a working example, please visit the following documentation article:

*   [Working with password-protected OneNote documents](https://docs.groupdocs.com/metadata/java/)

# Enhancements

The following enhancements are made in version 19.1:

*   Removed the obsolete code related to the TIFF/EXIF functionality
*   Removed obsolete members of the **_DublinCorePackage_** class
*   Implemented **_Closeable_** interface for the following classes to reduce the memory consumption:
    *   _**VisioFormat**_
    *   _**OneNoteFormat**_
    *   _**DwgFormat**_
    *   _**DxfFormat**_
    *   _**EmlFormat**_
    *   _**OutlookMessage**_
    *   _**MovFormat**_

For working examples on how to reduce memory consumption, please visit [this](https://docs.groupdocs.com/metadata/java/) documentation article.

## Available Channels and ResourcesHere are a few channels and resources for you to download, try, learn and get technical support on GroupDocs.Metadata for Java:

*   [Installation](https://repository.groupdocs.com/webapp/#/artifacts/browse/tree/General/repo/com/groupdocs/groupdocs-metadata) - Install GroupDocs.Metadata for Java from Maven
*   [Documentation](https://docs.groupdocs.com/metadata/java/) – Product documentation
*   [Examples](https://github.com/groupdocs-metadata/GroupDocs.Metadata-for-Java) – Source code examples
*   [Video Tutorials](https://www.youtube.com/playlist?list=PL25CTxMCj5vN908nnfZ9klfM41JeYsg1x "Metadata API YouTube Tutorials") - YouTube videos
*   [Product Support Forum](https://forum.groupdocs.com/c/metadata) – Technical support forum for GroupDocs.Metadata for Java

## FeedbackWe always love to hear your valuable feedback. Share your suggestions, questions, or queries related to GroupDocs.Metadata for Java at our [forum](https://forum.groupdocs.com/c/metadata).




