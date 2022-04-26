---
title: 'Sign Images with Metadata Signature using GroupDocs.Signature for .NET 19.1'
date: Fri, 15 Feb 2019 16:51:17 +0000
draft: false
url: /2019/02/15/sign-images-with-metadata-signature-using-groupdocs.signature-for-.net-19.1/
aliases:
    - /2019/02/15/support-of-metadata-signature-for-images-in-groupdocs.signature-for-.net-19.1/
    - /2019/02/15/add-metadata-signature-in-images-using-groupdocs.signature-for-.net-19.1/
author: 'Usman Aziz'
summary: ''
tags: []
categories: ['GroupDocs.Signature Product Family']
---

[![GroupDocs.Signature](http://blog.groupdocs.com/wp-content/uploads/sites/4/2016/07/groupdocs-signature-net.png)](https://www.groupdocs.com/products/signature/net)New month, new release! We have released version 19.1 of [GroupDocs.Signature for .NET](https://products.groupdocs.com/signature/net) that brings a couple of new features as well as two bug fixes and two improvements. The latest version provides metadata signature features for image files. Furthermore, the API now supports rounded corners for rectangle stamp signature types. For more details on what's new in the latest release, please have a look at [release notes](https://docs.groupdocs.com/display/signaturenet/GroupDocs.Signature+for+.NET+19.1+Release+Notes).

# Features Introduced

## Metadata Signature Features for ImagesIn the latest version, we have introduced a new feature of singing images with metadata signatures that are based on Exchangeable Image File Format (EXIF) specification. For this, we have added a new public class **ImageMetadataSignatureOptions** that provides different options to add metadata signatures in images. For a working example, please visit [this](https://docs.groupdocs.com/signature/net) documentation article.

## Rounded Corners for Stamp SignaturesA new public class **SquareBorderLine** that inherits **BorderLine** is added to implement square stamp signature with rounded corners. This class contains data about the radius of the square signature's corners. For a working example, please visit [this](https://docs.groupdocs.com/signature/net) documentation article.

# Improvements

We have done the following improvements in version 19.1.

*   Improve Image Metadata type conversion
*   Optimize Document options type detection for handler processes (Sign/Verify/Search)

# Bug Fixes

The following bugs are fixed in the latest version.

*   Fix Stamp generation processing for wide areas
*   QR/Bar code with wide border cannot be read

# Available Channels and Resources

Here are a few channels and resources for you to learn, try and get technical support on GroupDocs.Signature API for .NET:

*   [NuGet](https://www.nuget.org/packages/groupdocs.signature "GroupDocs.Signature for .NET NuGet") - Nuget Installation
*   [Documentation](https://docs.groupdocs.com/display/signaturenet/Home "Signing API Documentation") - Product Documentation
*   [API References](https://apireference.groupdocs.com/net/signature "API References") – GroupDocs.Signature for .NET API References
*   [Examples](https://github.com/groupdocs-signature/GroupDocs.Signature-for.NET "Signing API Examples") - Source Code Examples, Showcases, and Plugins
*   [Product Support Forum](https://forum.groupdocs.com/c/signature "GroupDocs.Signature for .NET Support forum") \- Technical Support Forum for GroupDocs.Signature Product Family
*   [Video Tutorials](https://www.youtube.com/playlist?list=PL25CTxMCj5vO7U3a710gc0btpJw5enZwT "GroupDocs.Signature for .NET tutorials") \- YouTube Video Tutorials

# Feedback

As always, we will be happy to know about your thoughts. Just create a [forum thread](https://forum.groupdocs.com/c/signature) and our dedicated support team will be there to respond.




