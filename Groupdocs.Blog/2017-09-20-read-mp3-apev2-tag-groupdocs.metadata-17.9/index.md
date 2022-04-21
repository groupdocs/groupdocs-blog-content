---
title: 'Read APEv2 Tags in Mp3 Files using GroupDocs.Metadata for .NET 17.9.0'
date: Wed, 20 Sep 2017 10:15:31 +0000
draft: false
url: /2017/09/20/read-mp3-apev2-tag-groupdocs.metadata-17.9/
author: 'Rida Fatima'
summary: ''
tags: []
categories: ['GroupDocs.Metadata for .NET Releases', 'GroupDocs.Metadata Product Family']
---

![GroupDocs.Metadata for .NET](http://blog.groupdocs.com/wp-content/uploads/sites/4/2017/06/groupdocs-metadata-net.png "GroupDocs-Metadata-theme-100x100")It gives us immense pleasure to announce the release of version 17.9.0 of the **GroupDocs.Metadata for .NET** API. The latest release comes up with a number of new features along with an enhancement and a bug fix. In addition to the tags the API already supports, the API also supports reading APEv2 tags in Mp3 files. Furthermore, the API also allows reading metadata of OpenDocument Spreadsheet files(ODS format) starting from version 17.9.0. The API has also added features like reading SRational Tiff tags in Jpeg and Tiff images etc. Moreover, we have tried to improve the [metadata extraction API](https://www.groupdocs.com/products/metadata/net)'s functionality by improving the export process of files with larger objects and fixing a bug related to updating EXIF tags. We therefore recommend you to [download](https://downloads.groupdocs.com/metadata/net/new-releases/groupdocs.metadata-for-.net-17.9.0/) or update your applications to use the latest version of the API for a better and smoother experience.

# The .NET Metadata Extraction API - New Features

## Ability to Read:

*   [Metadata in OpenDocument Spreadsheet format](https://docs.groupdocs.com/metadata/net)
*   [APEv2 metadata in MP3 format](https://docs.groupdocs.com/metadata/net)
*   [SRational TIFF tag in JPEG and TIFF image formats](https://docs.groupdocs.com/metadata/net)

## Ability to Update:

*   [And add TIFF tags in EXIF](https://docs.groupdocs.com/metadata/net)
*   [Metadata in OpenDocument Spreadsheet format](https://docs.groupdocs.com/metadata/net)

For details about the features supported by the API, please visit [Features Overview](https://docs.groupdocs.com/display/metadatanet/Features+Overview).

# GroupDocs.Metadata for .NET API - Enhancements

In several cases the metadata value of a specific key may be too large (more than 32 KBytes). Previous versions did not handle such cases so a user might get some kind of exception while trying the export process. We are glad to announce that the API has now improved the method of export process and allows to:

*   Prevent the crash during export process in case of converting large objects to Excel or CSV

# Version 17.9.0 of the Metadata Extraction API - Bug  Fixes

We realized that several EXIF tags were not found after updating the EXIF property of a Jpeg image. We have fixed this bug in this release and a user can now update the EXIF property of an image without losing any existing tags.

# Available Channels and Resources

Here are a few channels and resources for you to download, learn, try and get technical support on GroupDocs.Metadata for .NET.

*   [Download](https://downloads.groupdocs.com/metadata/net/new-releases/groupdocs.metadata-for-.net-17.9.0/ "GroupDocs.Metadata MSI") - MSI Package as well as Zipped DLLs
*   [NuGet](https://www.nuget.org/packages/groupdocs-metadata-dotnet/17.9.0 "GroupDocs.Metadata Nuget Package") - NuGet Installation
*   [Documentation](https://docs.groupdocs.com/display/metadatanet/Getting+Started "Metadata API documentation") - API Documentation
*   [Examples/Plugins/Showcases](https://github.com/groupdocs-metadata/GroupDocs.Metadata-for-.NET/tree/master/Examples "How to use Metadata API") - Source Code Examples, Plugins, and Metadata Editor Application
*   [Video Tutorials](https://www.youtube.com/channel/UCkOlPEPh0oljoESrmKP6l4g "Metadata API YouTube Tutorials") - YouTube API Videos
*   [Product Support Forum](http://www.groupdocs.com/Community/forums/groupdocs.metadata-product-family/48/showforum.aspx) - Technical Support Forum for GroupDocs Metadata

# Feedback

*   As always, if you have some questions, queries or suggestions about [GroupDocs.Metadata](http://www.groupdocs.com/products/metadata/net ".NET Metadata API") for .NET API,  just share with us by creating a [forum thread](http://www.groupdocs.com/Community/forums/groupdocs.metadata-product-family/48/showforum.aspx).




