---
title: 'Define and Use Custom Objects for PDF Metadata Signature'
date: Thu, 30 May 2019 12:48:55 +0000
draft: false
url: /2019/05/30/define-and-use-custom-objects-for-pdf-metadata-signature/
author: 'Usman Aziz'
summary: ''
tags: ['digital document signature', 'digital signature', 'Digital verification of Word documents', 'e-sign API', 'e-signature', 'esignature', 'Metadata signature', 'SIgn PDF documents']
categories: ['GroupDocs.Signature for .NET', 'GroupDocs.Signature Product Family']
---

Metadata signature is a convenient way to sign documents using metadata properties. In GroupDocs.Signature for .NET 18.9, we introduced the feature of signing the PDF documents using various metadata properties including:

*   Author
*   CreateDate
*   MetadataDate
*   CreatorTool
*   ModifyDate
*   Producer
*   Entry
*   Keywords
*   Title
*   Subject
*   Description
*   Creator

You can set all or some of the above-mentioned properties while signing the documents. Since these are the built-in properties, you can only add/update their value.

There could be a situation when the built-in metadata properties may not fulfill your requirements and you may want to use your own set of properties to add metadata signatures. In this case, there should be some way to define and use custom objects as metadata signatures. Well, I am pleased to tell you that this is now possible using the latest version of GroupDocs.Signature for .NET.

Since version 19.4, we have added the feature of signing PDF documents using custom metadata objects. You can define the custom classes that may contain the data members of your choice. You can then use the objects of these classes for the metadata signatures. The following is an example of the custom class.

{{< gist GroupDocsGists c29c9a04961589b3ee5f34a9ee0e5afb "CustomMetadataClass.cs" >}}

The following code snippet shows how to use the custom class to add the metadata signature.

{{< gist GroupDocsGists c29c9a04961589b3ee5f34a9ee0e5afb "CustomMetadataClass_Usage.cs" >}}

Well, this is not enough and I have something more interesting for you. The values of these custom metadata properties appear as plain text and they can easily be accessed and understood by anyone.

To avoid any unauthorized usage of the metadata values, we have introduced a mechanism of encryption/decryption. For this, we have added **DataEncryption** property to **PdfMetadataSignature** class and this is how you can apply encryption to the custom metadata objects:

{{< gist GroupDocsGists c29c9a04961589b3ee5f34a9ee0e5afb "CustomMetadataClass_Encrypted.cs" >}}

This is surely a valuable addition to the API features which can give you more control over the metadata signature. So why not [download](https://downloads.groupdocs.com/signature/net) the latest version and integrate this feature in your e-signing application?

In case you would have any queries or suggestions, let's have a conversation over our [forum](https://forum.groupdocs.com/).




