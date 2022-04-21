---
title: 'Add Metadata Signature in Cells Document using GroupDocs.Signature for .NET 18.10'
date: Fri, 02 Nov 2018 15:02:24 +0000
draft: false
url: /2018/11/02/groupdocs.signature-for-.net-18.10/
author: 'Samicheema'
summary: ''
tags: []
categories: ['GroupDocs.Signature for .NET', 'GroupDocs.Signature Product Family']
---

[![GroupDocs.Signature](http://blog.groupdocs.com/wp-content/uploads/sites/4/2016/07/groupdocs-signature-net.png)](https://www.groupdocs.com/products/signature/net)

We at GroupDocs, are pleased to announce another monthly release of [GroupDocs.Signature for .NET](https://products.groupdocs.com/signature/net). This latest release **18.10** of the API provides the ability to add and search Metadata Signature in Cells and Words documents. Furthermore, few improvements are also introduced in this version, therefore, we recommend you to [download](https://www.nuget.org/packages/Groupdocs.Signature) the new version of API and evaluate the exciting features to enhance document e-signing experience.

# Features

## Metadata Signatures for Cells and Words documentsThe Metadata Signature is the additional document property that contains special attributes/tags to keep non visual information inside the document. Following example demonstrates how to compose Metadata Signature options for Cells document:```
// setup options with text of signature
CellsMetadataSignOptions signOptions = new CellsMetadataSignOptions();
// Specify different Metadata Signatures and add them to options sigature collection
// setup Author property
CellsMetadataSignature mdSign_Author = new CellsMetadataSignature("Author", "Mr.Scherlock Holmes");
signOptions.MetadataSignatures.Add(mdSign_Author);
// setup data of document id
CellsMetadataSignature mdSign_DocId = new CellsMetadataSignature("DocumentId", Guid.NewGuid().ToString());
signOptions.MetadataSignatures.Add(mdSign_DocId);
// setup data of sign date
CellsMetadataSignature mdSign_Date = new CellsMetadataSignature("SignDate", DateTime.Now);
signOptions.MetadataSignatures.Add(mdSign_Date);
// setup some integer value
CellsMetadataSignature mdSign_Days = new CellsMetadataSignature("DocDays", 12345);
signOptions.MetadataSignatures.Add(mdSign_Days);
// setup data of sign date
CellsMetadataSignature mdSign_Koeff = new CellsMetadataSignature("SignKoeff", 2.345M);
signOptions.MetadataSignatures.Add(mdSign_Koeff);
// sign document
string signedPath = handler.Sign("Sample.xlsx", signOptions,
	new SaveOptions { OutputType = OutputType.String, OutputFileName = "Words_Document_Metadata" }); 
```

## Search Metadata Signature in Cells and Words documentsYou can search for Metadata Signatures within the Cells and Words documents. Following example demonstrates how to search Metadata Signatures in Words document:```
// setup search options
WordsSearchMetadataOptions searchOptions = new WordsSearchMetadataOptions();
// search document
SearchResult result = handler.Search("SignedMetadata.docx", searchOptions);
// output signatures
List signatures = result.ToList();
foreach (WordsMetadataSignature signature in signatures)
{
	WordsMetadataSignature metadataSignature = signature as WordsMetadataSignature;
	if (metadataSignature != null)
	{
		Console.WriteLine("Words Metadata: {0} = {1}", metadataSignature.Name, metadataSignature.ToString());
	}
} 
```

## Additional Verification CriteriaThis latest version of the API provides ability to search comments of Digital Signatures in Words document.```
public string Comments { get; set; } 
```

# Improvements

*   Support of password protected Open-Documents-Spreadsheet ODS file formats
*   Search results conversion to typed list of signatures
*   Global Exception handler to catch all not handled exceptions

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




