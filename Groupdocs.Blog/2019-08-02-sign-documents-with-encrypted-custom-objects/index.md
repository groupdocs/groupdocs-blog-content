---
title: 'Sign Documents with Encrypted Custom Objects'
date: Fri, 02 Aug 2019 19:39:00 +0000
draft: false
url: /2019/08/02/sign-documents-with-encrypted-custom-objects/
author: 'Usman Aziz'
summary: ''
tags: ['API', 'digital signature', 'e-signature', 'electronic signature', 'Embed Custom Objects', 'Encrypted Metadata Signature', 'java', 'Metadata signature', 'Sign Documents', 'signature api for java']
categories: ['GroupDocs.Signature for Java', 'GroupDocs.Signature Product Family']
---

Hello guys! It's been a while since my last post about [GroupDocs.Signature for Java](https://products.groupdocs.com/signature/java). So, our Java community might have been waiting for something new regarding our e-signature API. Well, we have recently released version 19.7 of GroupDocs.Signature for Java and today, I shall give you an overview of something interesting that we have introduced in our latest release.

In the last couple of months, we introduced a quite valuable feature in the .NET variant related to the metadata signatures - signing documents with custom metadata. We have now introduced this feature in the Java API as well. So now, you can define and use the custom objects as metadata signatures using GroupDocs.Signature for Java.

Signing document with custom metadata objects becomes useful when you want to embed the metadata signatures containing the information/data of your own choice. For example, you may want to embed the information to the document about who did sign the document, the date when the document was signed and so on. In that case, you can not use the built-in metadata properties of the documents. This is where you can use the custom objects in metadata signatures.

For this, the following classes are extended with new public method  _AddSignature_**.**

*   WordsMetadataSignature - for Word documents
*   SlidesMetadataSignature - for Presentations
*   CellsMetadataSignature - for Spreadsheets
*   PdfMetadataSignature - for PDF documents

This method creates new metadata signature with passed arguments (name and value), adds the signature to list of metadata signatures and returns the newly created object as a result.

Let's now check out how to add the custom object in the metadata signature. I am assuming that we have to sign the Word document, therefore, I'll be using the classes that work with the Word documents.

The following is the custom class containing the data members that I want to embed as the metadata signature in the document.

{{< gist usman-aziz e5ea6bfa3e2a52c740cb77f442d39ae3 "DocumentSignature.java" >}}

And this is how we would create the object of the custom class and then add that object to the metadata signature collection of the input document.

{{< gist usman-aziz e5ea6bfa3e2a52c740cb77f442d39ae3 "SignDocumentWithEncryptedObjects.java" >}}

Did you notice that I have done something extra in the code before signing the document? Yes, after adding the object to the signature collection, I have encrypted it to make it secure. So you can avoid the custom metadata signatures to be captured by the unauthorized persons by applying the encryption.

That is not the end yet! You can also search your custom objects within the metadata signature collection of the documents using _SignatureHandler.search_ method. The following code snippet shows how to search the encrypted object that we have added before.

{{< gist usman-aziz e5ea6bfa3e2a52c740cb77f442d39ae3 "SearchCustomObject.java" >}}

For adding and searching encrypted custom objects in other document formats, please visit the [documentation](https://docs.groupdocs.com/signature/java).

In addition to the above-mentioned features, we have also added some improvements regarding _.djvu_ file format as well as three bug fixes. For details, please have a look at the [release notes](https://docs.groupdocs.com/display/signaturejava/GroupDocs.Signature+for+Java+19.7+Release+Notes).

If you are interested in using the newly arrived features in your e-signing application, just download and integrate the [latest release](https://downloads.groupdocs.com/signature/java). For working code samples, download or clone our examples project from [GitHub repository](https://github.com/groupdocs-signature/GroupDocs.Signature-for-Java).

In case you would have any questions or suggestions, just create a topic on our [forum](https://forum.groupdocs.com/categories) and we would love to have a conversation with you.




