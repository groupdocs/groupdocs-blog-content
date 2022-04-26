---
title: 'Add Form-Field Signatures in PDF using GroupDocs.Signature for .NET 18.11'
date: Wed, 05 Dec 2018 17:53:50 +0000
draft: false
url: /2018/12/05/groupdocs.signature-for-.net-18.11/
author: 'Samicheema'
summary: ''
tags: ['GroupDocs Signature for .NET']
categories: ['GroupDocs.Signature Product Family']
---

[![GroupDocs.Signature](http://blog.groupdocs.com/wp-content/uploads/sites/4/2016/07/groupdocs-signature-net.png)](https://www.groupdocs.com/products/signature/net)

We are pleased to announce another monthly release of [GroupDocs.Signature for .NET](https://products.groupdocs.com/signature/net). This latest [release](https://docs.groupdocs.com/display/signaturenet/GroupDocs.Signature+for+.NET+18.11+Release+Notes) **18.11** of the API comes up with a multitude of new features like the ability to add form-field signatures in PDF documents and many more. We therefore recommend you to [download](https://www.nuget.org/packages/Groupdocs.Signature) the new version of the API to evaluate the exciting new features and enhance your document e-signing experience.

# Features

## Sign PDF Document with a Form-Field SignatureThe Form-Field Signatures are the input control which are placed in a document page. Following example demonstrates how to add Checkbox in a PDF document:```
// instantiate check-box form field signature
FormFieldSignature checkboxSignature = new PdfCheckboxFormFieldSignature("FieldCheckbox", true);
// instantiate options based on check-box form field signature
PdfFormFieldSignOptions checkboxOptions = new PdfFormFieldSignOptions(checkboxSignature)
{
    HorizontalAlignment = HorizontalAlignment.Left,
    VerticalAlignment = VerticalAlignment.Top,
    Margin = new Padding(120, 20, 0, 0),
    Height = 10,
    Width = 10
};
// sign document
string signedPath = handler.Sign("02_pages.pdf", checkboxOptions,
    new SaveOptions { OutputType = OutputType.String, OutputFileName = "Pdf_FormFields" }); 
```

## Search Form-Field Signatures in a PDF DocumentAPI allows you to search for Form-Field Signatures like Text, Checkbox or Digital within the document. Following example demonstrates how to search Form-Field Signature in PDF document:```
// setup search options
PdfSearchFormFieldOptions searchOptions = new PdfSearchFormFieldOptions();
searchOptions.SearchAllPages = true;
searchOptions.NamePattern = @"Field";
searchOptions.Value = @"Value1";
// search document
SearchResult result = handler.Search("Pdf_FormFields_Signed.pdf", searchOptions); 
```

## Metadata Signatures for Slides documentThe Metadata Signature is the additional document property that contains special attributes/tags to keep non visual information inside the document. Following example demonstrates how to compose Metadata Signature options for Slides document:```
// setup options with text of signature
SlidesMetadataSignOptions signOptions = new SlidesMetadataSignOptions();
// Specify different Metadata Signatures and add them to options sigature collection
// setup Author property
SlidesMetadataSignature mdSign_Author = new SlidesMetadataSignature("Author", "Mr.Scherlock Holmes");
signOptions.MetadataSignatures.Add(mdSign_Author);
// setup data of document id
SlidesMetadataSignature mdSign_DocId = new SlidesMetadataSignature("DocumentId", Guid.NewGuid().ToString());
signOptions.MetadataSignatures.Add(mdSign_DocId);
// setup data of sign date
SlidesMetadataSignature mdSign_Date = new SlidesMetadataSignature("SignDate", DateTime.Now);
signOptions.MetadataSignatures.Add(mdSign_Date);
// setup some integer value
SlidesMetadataSignature mdSign_Days = new SlidesMetadataSignature("DocDays", 12345);
signOptions.MetadataSignatures.Add(mdSign_Days);
// setup data of sign date
SlidesMetadataSignature mdSign_Koeff = new SlidesMetadataSignature("SignKoeff", 2.345M);
signOptions.MetadataSignatures.Add(mdSign_Koeff);
// sign document
string signedPath = handler.Sign("test.pptx", signOptions,
    new SaveOptions { OutputType = OutputType.String, OutputFileName = "Slides_Documents_Metadata" }); 
```

## Search Metadata Signature in a Slides documentYou can search for Metadata Signatures within the Slides document. Following example demonstrates how to search Metadata Signatures in Slides document:```
// setup search options
SlidesSearchMetadataOptions searchOptions = new SlidesSearchMetadataOptions();
// set if we need built-in signatures
searchOptions.IncludeBuiltinProperties = true;
// search document
SearchResult result = handler.Search("SignedMetadata.pptx", searchOptions); 
```

## Additional Verification CriteriaThis latest version of the API provides few additional properties to verify Digital Signatures of Words document.```
// setup digital verification options
WordsVerifyDigitalOptions verifyOptions = new WordsVerifyDigitalOptions("SherlockHolmes.cer");
verifyOptions.Comments = "Test1";
verifyOptions.SubjectName = "Signature";
verifyOptions.IssuerName = "GroupDocs";
verifyOptions.SignDateTimeFrom = new DateTime(2017, 1, 26, 14, 55, 57);
verifyOptions.SignDateTimeTo = new DateTime(2017, 1, 26, 14, 55, 59);        
//verify document
VerificationResult result = handler.Verify("digital signatures.docx", verifyOptions); 
```

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




