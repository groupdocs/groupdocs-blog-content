---
title: 'Set Signature Position in Cells Document using GroupDocs.Signature for .NET 18.7'
date: Fri, 10 Aug 2018 14:37:09 +0000
draft: false
url: /2018/08/10/groupdocs.signature-for-.net-18.7/
author: 'Samicheema'
summary: ''
tags: []
categories: ['GroupDocs.Signature for .NET', 'GroupDocs.Signature Product Family']
---

[![GroupDocs.Signature](http://blog.groupdocs.com/wp-content/uploads/sites/4/2016/07/groupdocs-signature-net.png)](https://www.groupdocs.com/products/signature/net)

We are pleased to announce another monthly release of [GroupDocs.Signature for .NET](https://products.groupdocs.com/signature/net) 18.7 with multitude new features like ability for cancellation of signing process and additional search criteria for Digital Signatures of Words and Cells documents. Furthermore, this monthly release also covers some improvements and fixes, we therefore, recommend you to [download](https://www.nuget.org/packages/Groupdocs.Signature) the new version of API and evaluate the exciting features to enhance document e-signing experience.

# Features

## Additional Search CriteriaNow users of this API can search Digital Signatures in Cells and Words documents with additional search criteria Following example demonstrates how to search Digital Signatures in Words document:```
// setup options with text of signature
WordsSearchDigitalOptions searchOptions = new WordsSearchDigitalOptions();
// setup additional search criteria
searchOptions.Comments = "test comments";
searchOptions.SignDateTimeFrom = new DateTime(DateTime.Now.Year, 1, 1);
searchOptions.IssuerName = "John";
// Search Document for Signatures
SearchResult searchResult = handler.Search(fileName, searchOptions); 
```

## Support of Measure Type Units for Cells PositioningUsers can set position of Signatures in Cells with some predefined measure units for following signature types:

*   Text Signatures
*   Image Signatures
*   Digital Signatures
*   QR-Code Signatures
*   Barcode Signatures
*   Stamp Signatures

Following example demonstrates using **Measure Type** properties to set a position of QR-Code Signatures in Cells document:```
CellsQRCodeSignOptions signOptions = new CellsQRCodeSignOptions("12345678AbcdefghKLMNOPqrst");
// size
signOptions.SizeMeasureType = MeasureType.Percents;
signOptions.Width = 10;
signOptions.Height = 10;
// position
// alignment
signOptions.HorizontalAlignment = HorizontalAlignment.Center;
signOptions.VerticalAlignment = VerticalAlignment.Top;
// margin
signOptions.MarginMeasureType = MeasureType.Percents;
signOptions.Margin.Top = 25; 
```

## Ability for CancellationNow API provides ability for cancellation of following processes:

*   Search
*   Verification
*   Signing

Following example demonstrates how to cancel signing process:```
// setup signature option
PdfSignTextOptions signOptions = new PdfSignTextOptions("John Smith", 10, 10, 100, 100);
signOptions.SignAllPages = true;
SaveOptions saveOptions = new SaveOptions { OutputType = OutputType.String, OutputFileName = "PDF_Process_Events" };
handler.SignatureStarted += delegate (object sender, ProcessStartEventArgs args)
{
    Console.WriteLine("Processing of {0} signatures for {1} started at {2}", args.TotalSignatures, args.Guid, args.Started.ToString("f"));
};
handler.SignatureProgress += delegate (object sender, ProcessProgressEventArgs args)
{
    Console.WriteLine("Singing of {0} progress: {1} %. Processed {2} signatures.", args.Guid, args.Progress, args.ProcessedSignatures);
    if (args.Progress > 10)
    {
        args.Cancel = true;
        Console.WriteLine("Cancellation of process");
    }
};
handler.SignatureCompleted += delegate (object sender, ProcessCompleteEventArgs args)
{
    if (args.Canceled)
    {
        Console.WriteLine("Singing process was canceled");
    }
    else
    {
        Console.WriteLine("Singing of {0} completed at {1}. Processing of {2}", args.Guid, args.Completed.ToString("f"), args.TotalSignatures);
    }
}; 
```

# Improvements

*   Global Exception handler to catch all unhandled exceptions
*   Support of several Words Digital Search Options and Cells Digital Search Options

# Bug Fixes

*   Wrong border appearance for PDF Text as Image signatures
*   QR-Code positioning when Signature area is more than generated QR-Code
*   Freezing of signature process on Images for QR-Code Signature

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




