---
title: 'Introducing Metadata Signatures in GroupDocs.Signature for .NET 18.9'
date: Thu, 13 Sep 2018 14:50:47 +0000
draft: false
url: /2018/09/13/groupdocs.signature-for-.net-18.9/
author: 'Samicheema'
summary: ''
tags: []
categories: ['GroupDocs.Signature for .NET', 'GroupDocs.Signature Product Family']
---

[![GroupDocs.Signature](http://blog.groupdocs.com/wp-content/uploads/sites/4/2016/07/groupdocs-signature-net.png)](https://www.groupdocs.com/products/signature/net)

We are delighted to announce another monthly release of [GroupDocs.Signature for .NET](https://products.groupdocs.com/signature/net) **18.9** with multitude of new features like ability to save Image documents as PDF and signing of PDF with Metadata Signatures. Furthermore, this monthly release also comes up with few fixes, we therefore, recommend you to [download](https://www.nuget.org/packages/Groupdocs.Signature) the new version of API and evaluate the exciting features to enhance document e-signing experience.

# Features

## Metadata Signatures for PDFThe Metadata Signature is the additional document property that contains special attributes/tags to keep non visual information inside the document. Following example demonstrates how to compose Metadata Signature options for PDF document:```
PdfMetadataSignOptions result = new PdfMetadataSignOptions();
result.MetadataSignatures.Add(new PdfMetadataSignature("Author", "Mr.Sherlock Holmes"));
result.MetadataSignatures.Add(new PdfMetadataSignature("CreationDate", DateTime.Now));
result.MetadataSignatures.Add(new PdfMetadataSignature("Creator", "Dr.Whatson"));
result.MetadataSignatures.Add(new PdfMetadataSignature("ModDate", DateTime.Now));
result.MetadataSignatures.Add(new PdfMetadataSignature("Producer", "BakerStreet.Inc"));
result.MetadataSignatures.Add(new PdfMetadataSignature("Subject", "Baskervalley"));
result.MetadataSignatures.Add(new PdfMetadataSignature("Title", "OfficeDocument"));
result.MetadataSignatures.Add(new PdfMetadataSignature("Trapped", "Information"));
result.MetadataSignatures.Add(new PdfMetadataSignature("IsSigned", true));
result.MetadataSignatures.Add(new PdfMetadataSignature("SignatureId", 112233));
result.MetadataSignatures.Add(new PdfMetadataSignature("Amount", 123.456));
return result; 
```

## Search Metadata SignatureUsers of this API can search for Metadata Signatures within the document. Following example demonstrates how to search Metadata Signatures in PDF document:```
// setup search options
PdfSearchMetadataOptions searchOptions = new PdfSearchMetadataOptions();
// search document
SearchResult result = handler.Search("SignedMetadata.pdf", searchOptions);
// output signatures
foreach (BaseSignature signature in result.Signatures)
{
    PdfMetadataSignature metadataSignature = signature as PdfMetadataSignature;
    if (metadataSignature != null)
    {
        Console.WriteLine("Pdf Metadata: {0}:{1}  = {2}", metadataSignature.TagPrefix, metadataSignature.Name, metadataSignature.ToString());
    }
} 
```

## Metadata Signature Entity and CollectionUsers of this API can also add collection of Metadata Signatures in document. Following example demonstrates how to add collection of Metadata Signatures in PDF document:```
// setup options with text of signature
PdfMetadataSignOptions signOptions = new PdfMetadataSignOptions();
// Specify different Metadata Signatures and add them to options sigature collection
// setup Author property
PdfMetadataSignature mdSign_Author = new PdfMetadataSignature("Author", "Mr.Scherlock Holmes");
signOptions.MetadataSignatures.Add(mdSign_Author);
// setup data of document id
PdfMetadataSignature mdSign_DocId = new PdfMetadataSignature("DocumentId", Guid.NewGuid().ToString());
signOptions.MetadataSignatures.Add(mdSign_DocId);
// setup data of sign date
PdfMetadataSignature mdSign_Date = new PdfMetadataSignature("SignDate", DateTime.Now, "pdf");
signOptions.MetadataSignatures.Add(mdSign_Date);
// sign document
string signedPath = handler.Sign("test.pdf", signOptions,
    new SaveOptions { OutputType = OutputType.String, OutputFileName = "Pdf_Documents_Metadata" });
Console.WriteLine("Signed file path is: " + signedPath); 
```

## Save Image Documents as PDFImage documents can be saved as PDF using this latest release of the API.

## MatchType for Text Verification OptionsNow API provides ability to verify Text Signatures with extended option **MatchType**

# Bug Fixes

*   Incorrect signing image documents with .psd, .wmf and .svg format
*   Output PDF incorrectly signed with Digital Certificates
*   Unable to search Digital signature in Cells with extended options

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




