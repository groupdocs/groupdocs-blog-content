---
title: 'Search for Metadata Signatures in Images using GroupDocs.Signature for .NET 18.12'
date: Fri, 04 Jan 2019 11:04:28 +0000
draft: false
url: /2019/01/04/groupdocs.signature-for-.net-18.12/
author: 'Samicheema'
summary: ''
tags: []
categories: ['GroupDocs.Signature for .NET', 'GroupDocs.Signature Product Family']
---

[![GroupDocs.Signature](http://blog.groupdocs.com/wp-content/uploads/sites/4/2016/07/groupdocs-signature-net.png)](https://www.groupdocs.com/products/signature/net)

We at GroupDocs, are pleased to announce another monthly release of [GroupDocs.Signature for .NET](https://products.groupdocs.com/signature/net). This latest [release](https://docs.groupdocs.com/display/signaturenet/GroupDocs.Signature+for+.NET+18.12+Release+Notes) **18.12** of the API comes up with a feature to add and search for Metadata Signatures in Images. Apart from that, a few fixes and improvements are also introduced in this version, therefore, we recommend you to [download](https://www.nuget.org/packages/Groupdocs.Signature) the new version of the API to evaluate the exciting new features and enhance your document e-signing experience.

# Features

## Search Metadata Signature in ImagesYou can search for Metadata Signatures within the Images. Following example demonstrates how to search Metadata Signatures in Images:```
// setup search options
ImagesSearchMetadataOptions searchOptions = new ImagesSearchMetadataOptions();
// search document
SearchResult result = handler.Search(fileName, searchOptions); 
```

# Improvements

*   Extend Form-Field signature name automatically with number prefix for multiple-pages options
*   Handling exceptions with proper details and exception type

# Bug Fixes

*   Skip Output folder when SaveOptions.OutputFileName is set as absolute path
*   Exception is fired when searching in PDF documents for Form-Fields that were setup without name

# Available Channels and Resources

Here are a few channels and resources for you to learn, try and get technical support on **GroupDocs.Signature** **API for .NET**:

*   [NuGet](https://www.nuget.org/packages/groupdocs.signature "GroupDocs.Signature for .NET NuGet") - Nuget install
*   [Documentation](https://docs.groupdocs.com/display/signaturenet/Home "Signing API Documentation") - Product Docs
*   [API References](https://apireference.groupdocs.com/net/signature "API References") – Signature API References
*   [Examples](https://github.com/groupdocs-signature/GroupDocs.Signature-for.NET "Signing API Examples") - Examples, Showcases and Plugins
*   [Product Support Forum](https://forum.groupdocs.com/c/signature "GroupDocs.Signature for .NET Support forum") \- Technical Support Forum for GroupDocs.Signature
*   [Video Tutorials](https://www.youtube.com/playlist?list=PL25CTxMCj5vO7U3a710gc0btpJw5enZwT "GroupDocs.Signature for .NET tutorials") \- YouTube Video Tutorials

# Feedback

As always, you are welcome to share your feedback to improve this product. We will be happy to know your thoughts. Just create a [forum thread](https://forum.groupdocs.com/c/signature) and our dedicated support team will be there to respond.




