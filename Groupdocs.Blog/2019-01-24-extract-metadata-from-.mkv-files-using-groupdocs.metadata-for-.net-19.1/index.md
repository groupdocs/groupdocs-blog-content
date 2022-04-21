---
title: 'Extract Metadata from .MKV Files using GroupDocs.Metadata for .NET 19.1'
date: Thu, 24 Jan 2019 13:30:47 +0000
draft: false
url: /2019/01/24/extract-metadata-from-.mkv-files-using-groupdocs.metadata-for-.net-19.1/
author: 'Usman Aziz'
summary: ''
tags: ['document-metadata', 'extracting metadata', 'Metadata Editor', 'metadata extraction API for .NET']
categories: ['GroupDocs.Metadata for .NET Releases', 'GroupDocs.Metadata Product Family']
---

![GroupDocs.Metadata for .NET](http://blog.groupdocs.com/wp-content/uploads/sites/4/2017/06/groupdocs-metadata-net.png "GroupDocs.Metadata for .NET")Today, we are pleased to announce the release of [GroupDocs.Metadata for .NET 19.1](https://products.groupdocs.com/metadata/net). In this version, we have introduced two new features and added seven enhancements. Using the latest version, you can extract metadata from Matroska Multimedia Container (.MKV) files. Furthermore, the latest version allows you to extract metadata from password-protected OneNote documents. Please have a look at the [release notes](https://docs.groupdocs.com/display/metadatanet/GroupDocs.Metadata+for+.NET+19.1+Release+Notes) for more details.

# Features Introduced

## Support for the Matroska Multimedia Container FilesGroupDocs.Metadata for .NET 19.1 is capable of extracting metadata from Matroska Multimedia Container (.MKV) files. The API provides the following features when working with .MKV files:

*   [Extracting MKV Format Metadata](https://docs.groupdocs.com/metadata/net)
*   [Extracting Matroska Segment Info](https://docs.groupdocs.com/metadata/net)
*   [Extracting Matroska Tag Metadata](https://docs.groupdocs.com/metadata/net)
*   [Extracting Matroska Track Metadata](https://docs.groupdocs.com/metadata/net)

## Support for Password-Protected OneNote DocumentsGroupDocs.Metadata for .NET has the ability to work with password-protected documents. In the latest version, we have extended this ability by adding support for password-protected OneNote documents. The **_LoadOptions_** class is used to set the password for the protected documents. For a working example, please visit the following documentation article:

*   [Working with password-protected OneNote documents](https://docs.groupdocs.com/metadata/net)

# Enhancements

The following enhancements are made in version 19.1:

*   Removed the obsolete code related to the TIFF/EXIF functionality
*   Removed obsolete members of the **_DublinCorePackage_** class
*   Implemented **_IDisposable_** interface for the following classes to reduce the memory consumption:
    *   _**VisioFormat**_
    *   _**OneNoteFormat**_
    *   _**DwgFormat**_
    *   _**DxfFormat**_
    *   _**EmlFormat**_
    *   _**OutlookMessage**_
    *   _**MovFormat**_

For working examples on how to reduce memory consumption, please visit [this](https://docs.groupdocs.com/metadata/net) documentation article.

# Available Channels and Resources

Here are a few channels and resources for you to download, learn, try and get technical support on GroupDocs.Metadata for .NET.

*   [Installation](https://www.nuget.org/packages/GroupDocs.Metadata/ "GroupDocs.Metadata Nuget Package") - Install GroupDocs.Metadata for .NET using NuGet
*   [Documentation](https://docs.groupdocs.com/display/metadatanet/Getting+Started "Metadata API documentation") - API Documentation
*   [Examples/Plugins/Showcases](https://github.com/groupdocs-metadata/GroupDocs.Metadata-for-.NET/tree/master/Examples "How to use Metadata API") - Source Code Examples, Plugins, and Showcases
*   [Video Tutorials](https://www.youtube.com/playlist?list=PL25CTxMCj5vOw2EECdY7g2z4O2odafxC_ "Metadata API YouTube Tutorials") - YouTube API Videos
*   [Product Support Forum](https://forum.groupdocs.com/c/metadata) - Technical Support Forum for GroupDocs.Metadata for .NET

# Feedback

As always, if you have any questions, queries or suggestions about [GroupDocs.Metadata for .NET](https://products.groupdocs.com/metadata/net ".NET Metadata API"), just share with us on our [forum](https://forum.groupdocs.com/c/metadata).




