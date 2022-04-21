---
title: 'Embed Custom Objects in Metadata Signature for Images'
date: Tue, 09 Jul 2019 06:03:15 +0000
draft: false
url: /2019/07/09/embed-custom-objects-in-metadata-signature-for-images/
author: 'Usman Aziz'
summary: ''
tags: ['.NET', '.NET API', 'Custom Metadata', 'digital document signature', 'digital signature', 'e-signature', 'electronic signature', 'Embed Custom Objects', 'Encrypted Metadata Signature', 'Metadata signature']
categories: ['GroupDocs.Signature for .NET', 'GroupDocs.Signature Product Family']
---



{{< figure align=center src="images/groupdocs-signature-net.png" alt="">}}


Yes, [GroupDocs.Signature for .NET](https://products.groupdocs.com/signature/net) now supports embedding custom objects as metadata signature in the images. So you can now sign the images with your desired metadata properties. We have introduced this feature in version _19.6_ by adding a new public method _AddSignature_ to the _ImageMetadataSignOptions_ class. Not only this, but you can also apply the data encryption to the custom objects. So let's check out how easy it is to sign an image with custom metadata signature.

Before jumping to the code, let me first describe the steps that are required to embed the encrypted custom objects.

*   Configure the storage paths, create and populate the object of _SignatureConfig_
*   Instantiate the _SignatureHandler_ by passing _SignatureConfig_ object
*   Setup _IDataEncryption_ object with new _SymmetricEncryption()_
*   Setup the custom object with the desired data members
*   Add the custom object to the metadata signature list using _AddSignature_ method
*   Apply the data encryption
*   Sign the document

That's it and the image has been signed with your desired metadata. Let's now have a look at the code sample for completely understanding the working of this feature.

{{< gist GroupDocsGists 785b50d976c0295dbcf75537d76f9c1d "AddCustomObjectAsMetadataSignature.cs" >}}

Along with this feature, we have also added a notable improvement in the searching process. With this improvement, you will now be able to locate the document's page number where the signature object was found. For this, the public abstract class _BaseSignature _has been extended with a new property _PageNumber_. This is how you can achieve it using the code.

{{< gist GroupDocsGists 785b50d976c0295dbcf75537d76f9c1d "SearchSignature.cs" >}}

Listed below are the other improvements and the bug fixes that we have packaged in version 19.6.

### Improvements

*   Ability to verify files with .cmx (CorelDraw) format as image documents
*   Ability to search ._cmx_ (CorelDraw) files as image documents
*   Ability to sign ._cmx_ (CorelDraw) files as image documents
*   Ability of saving Word documents with _FlatOpc_ formats
*   Support of ._cdr_ (CorelDraw) file format for verification process
*   Ability to search ._cdr_ (CorelDraw) files as image documents
*   Ability to sign ._cdr_ (CorelDraw) files as image documents

### Bug Fixes

*   Digital Signature's _IsValid_ property is not being set correctly for the Search routine
*   Output file is missing if save options are not provided
*   Illegal character issue when trying to encrypt serialized data
*   The output file's path is unexpected for different scenarios

Alright! So this is it from my side and now, it's your turn to [download](https://downloads.groupdocs.com/signature/net) and check out the latest release. For more details, you can have a glance at the [release notes](https://docs.groupdocs.com/display/signaturenet/GroupDocs.Signature+for+.NET+19.6+Release+Notes). I would also recommend you consult the [Developer's Guide](https://docs.groupdocs.com/display/signaturenet/Developer+Guide) while evaluating the API's features. Still, if you need any assistance, please feel free to write to us on our [forum](https://forum.groupdocs.com/).




