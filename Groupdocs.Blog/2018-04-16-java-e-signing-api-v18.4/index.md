---
title: 'Search Optical Signatures using Java E-Signing API v18.4'
date: Mon, 16 Apr 2018 10:54:13 +0000
draft: false
url: /2018/04/16/java-e-signing-api-v18.4/
author: 'Samicheema'
summary: ''
tags: []
categories: ['GroupDocs.Signature for Java', 'GroupDocs.Signature Product Family']
---

[![GroupDocs.Signature](https://blog.groupdocs.com/wp-content/uploads/sites/4/2017/03/groupdocs-signature-java.png)](https://www.groupdocs.com/products/signature/java)

We are delighted to announce the another monthly release of [GroupDocs.Signature for Java](https://products.groupdocs.com/signature/java) v18.4. This [release](https://docs.groupdocs.com/display/signaturejava/GroupDocs.Signature+for+Java+18.4+Release+Notes) comes up with many features like searching QRCode and Barcode signatures in [supported](https://docs.groupdocs.com/display/signaturejava/Supported+Document+Formats) documents. Aside this, few improvements and fixes are also introduced in this version of the API. We would recommend you to [download](https://downloads.groupdocs.com/signature/java) the new version of API and evaluate the exciting features to enhance document e-signing experience.

# eSignature API for Java v18.4 - Features

## Obtain Search Progress[Obtain search progress while searching signatures in the documents](https://docs.groupdocs.com/signature/java). Following code sample shows how to obtain search progress:```
SignatureHandler handler = new SignatureHandler(signConfig);
handler.SearchStarted.add(new ProcessStartEventHandler() {
	public void invoke(Object sender, ProcessStartEventArgs args) {
        System.out.println("Search started for "+args.getTotalSignatures()+"-page(s) in Document "+args.getGuid()+" started at " +String.valueOf(args.getStarted()));
    }
}); 
```

## Search QR-Code and Barcode SignaturesSearch [QR-Code](https://docs.groupdocs.com/signature/java) and [Barcode](https://docs.groupdocs.com/signature/java) Signatures in following documents:

*   PDF
*   Cells
*   Slides
*   Words
*   Image

Following code sample shows how to search Barcode signature in the PDF document:```
PdfSearchBarcodeOptions searchOptions = new PdfSearchBarcodeOptions();
searchOptions.setText("12345678");
// specify text math type
searchOptions.setMatchType(TextMatchType.Contains);
// search document
SearchResult result = handler.search("SignedBarCode.pdf", searchOptions); 
```

## Rectangle Property for Radial Gradient BrushRectangle property to set borders of ellipse for Radial Gradient Brush is introduced.

# Java eSignature API v18.4 - Improvements

*   Separate Brush classes for following brush styles:

*   [Solid](https://docs.groupdocs.com/signature/java)
*   [Texture](https://docs.groupdocs.com/signature/java)
*   [Radial Gradient](https://docs.groupdocs.com/signature/java)
*   [Linear Gradient](https://docs.groupdocs.com/signature/java)

*   Update dynamic Metered library with latest changes
*   Mark Brush property as Obsolete

# e-Signing API for Java 18.4 - Bug Fixes

*   Multiple options on pages setup give duplicate page numbers
*   Result of signing methods when document provided by URL

# Available Channels and Resources

Here are a few channels and resources for you to learn, try and get technical support on **GroupDocs.Signature** **API for Java**:

*   [Download](https://downloads.groupdocs.com/signature/java "Download") – JAR Files
*   [Documentation](https://docs.groupdocs.com/display/signaturejava/Home "Documentation") – API Docs
*   [Product Support Forum](https://forum.groupdocs.com/c/signature "Product Support Forum") – Technical Support Forum for GroupDocs.Signature
*   [Examples](https://github.com/groupdocs-signature/GroupDocs.Signature-for-Java "Examples") – GitHub source code examples

# Feedback

As always, you are welcome to share your feedback to improve this product. We will be happy to know your thoughts. Just create a [forum thread](https://forum.groupdocs.com/c/signature) and our dedicated support team will be there to respond.




