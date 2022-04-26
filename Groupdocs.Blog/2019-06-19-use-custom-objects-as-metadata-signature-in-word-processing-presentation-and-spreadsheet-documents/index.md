---
title: 'Use Custom Objects as Metadata Signature in Word Processing, Presentation, and Spreadsheet Documents'
date: Wed, 19 Jun 2019 11:59:07 +0000
draft: false
url: /2019/06/19/use-custom-objects-as-metadata-signature-in-word-processing-presentation-and-spreadsheet-documents/
author: 'Usman Aziz'
summary: ''
tags: ['digital document signature', 'digital signature', 'digital signature API for Java', 'e-sign API', 'e-signature', 'electronic signature', 'Metadata signature', 'PDF Signature', 'Sign Documents', 'signature api for java', 'Word Signature']
categories: ['GroupDocs.Signature for Java', 'GroupDocs.Signature Product Family']
---



{{< figure align=center src="images/groupdocs-signature-net.png" alt="">}}


Guys! We have recently released version 19.5 of [GroupDocs.Signature for .NET](https://products.groupdocs.com/signature/net) with some extended features, a few bug fixes, and improvements. So in this post, I am going to give you a brief overview of the new features that we have introduced in the latest release. Furthermore, I shall also list the issues that are fixed as well as the improvements that we have made in v19.5.

First of all, let's checkout what new the latest release has brought for you.

In the previous release, we added the feature of creating and using the custom objects as metadata signatures in the PDF documents. The feature is useful when you don't want to use the built-in metadata properties for metadata signatures. So, keeping an eye on the importance of this feature, we have extended it for word processing, presentation and spreadsheet documents. Now, you can sign the afore-mentioned document types using the custom objects as metadata signatures.

Lets find out how you can achieve it using the code.

For signing documents with metadata signature using the value of a custom object, we have added _AddSignature(string name, Object value)_ method to the following classes:

*   _WordsMetadataSignOptions_
*   _SlidesMetadataSignOptions_
*   _CellsMetadataSignOptions_
*   _PDFMetadataSignOptions_

You can add a custom class object (containing multiple data members) as well as a single-valued metadata signature to the _MetadataSignature_ collection. The following is the complete demonstration of this feature using the code snippet. Furthermore, it also shows how to apply data encryption to the object's values.

{{< gist GroupDocsGists dfcb0f5756c43297d979dfa585d2fba0 "UseCustomObjectAsMetadataSignature.cs" >}}

And this is how we created the class for the custom object.

{{< gist GroupDocsGists c29c9a04961589b3ee5f34a9ee0e5afb "CustomMetadataClass.cs" >}}

In addition to the above-mentioned feature, we have made the following bug fixes and the improvements in the latest release.

### Bug Fixes

*   Fix exception for de-serialization of encrypted string values in Metadata Signatures
*   _SaveOptions.OutputFileName_ doesn't affect on result name of signed document
*   _PdfQRCodeSignature.GetData()_ throws exception

### Improvements

*   Support of .djvu file format for verification process
*   Ability to search files with ._djvu_ format as image documents
*   Ability to sign files with ._djvu_ format as image documents
*   Implementation of a new method _AddSignature_ for _MetadataOptions_

So now, using the latest release, you can extend the ability to sign documents using custom objects for the word processing, presentation, and spreadsheet documents in your application. You can [download](https://downloads.groupdocs.com/signature/net) the latest version of the API and evaluate the new features using the [examples](https://github.com/groupdocs-signature/GroupDocs.Signature-for-.NET) project. In case you would have any queries or questions, just create a new topic in our [forum](https://forum.groupdocs.com/) and we'll love to assist you.




