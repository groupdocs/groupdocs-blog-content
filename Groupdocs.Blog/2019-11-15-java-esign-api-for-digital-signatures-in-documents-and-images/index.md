---
title: 'Introducing All-New  GroupDocs.Signature for Java API'
date: Fri, 15 Nov 2019 02:50:20 +0000
draft: false
url: /2019/11/15/java-esign-api-for-digital-signatures-in-documents-and-images/
author: 'Usman Aziz'
summary: ''
tags: ['API', 'digital signature', 'esign', 'java']
categories: ['GroupDocs.Signature for Java Releases', 'GroupDocs.Signature Product Family']
---

We are back with a major update for our customers who are using the eSign API - [GroupDocs.Signature for Java](https://products.groupdocs.com/signature/java). We have performed major product optimization and revamped the architecture which has made the API more memory efficient and easy to use. We have also added the support of a couple of new file formats. Let's have an overview of this amazing release and check out what you would get after upgrading to API v2.

## What is New in API v2?

We have simplified the way of signing the documents as well as improved the working of the API. Have a look at the key reasons why you should upgrade to the latest release.

*   The previous versions of the API had separate classes to deal with each supported document format. For example, we had _PdfSignTextOptions_ class for text signatures in PDF files and _WordsSignTextOptions_ class for Word Processing documents. But now, we have introduced a unified approach where the signature, verification, and search options are related to signature types only and not the document formats. A single class, _[TextSignOptions](https://apireference.groupdocs.com/java/signature/com.groupdocs.signature.options.sign/TextSignOptions)_ will now be used for all the document formats.
*   The _[Signature](https://apireference.groupdocs.com/java/signature/com.groupdocs.signature/Signature)_ class is introduced as a single entry point to sign the document with various signature types as well as perform verification and search.  
    
*   The overall document related classes that were used to deal with different document formats have been unified to common classes.  
    
*   The API’s architecture is redesigned from scratch in order to simplify the usage of options and classes to manipulate all the signature types.
*   The procedures of getting the document’s information and generating the previews for the documents are also simplified.

## How to Migrate?

The migration process is not as complex as it is supposed to be for the API versions with major updates. The legacy API has been moved into the **com.groupdocs.signature.legacy** package. Once you upgrade, it is required to make a project-wide replacement of imports from **com.groupdocs.signature.** to **com.groupdocs.signature.legacy** to resolve build issues.

The following is a code comparison of the previous versions with the latest one. It will give you an overview of how the coding style, the classes, and the methods have been changed.

### **Signing Document with Text Signature**

#### Old Versions

{{< gist GroupDocsGists f639c973af7a23efd745528f5b7676e9 "SignDocumentOldVersion.java" >}}

#### Version 19.11 or Later

{{< gist GroupDocsGists f639c973af7a23efd745528f5b7676e9 "SignDocumentNewVersion.java" >}}

## Setting Up Encryption for Metadata Signature

In addition to the major update, we have also added the feature of setting up the encryption for the metadata signature at the options levels. The [_MetadataSignOptions_](https://apireference.groupdocs.com/java/signature/com.groupdocs.signature.options.sign/MetadataSignOptions)  class provides [_setDataEncryption_](https://apireference.groupdocs.com/java/signature/com.groupdocs.signature.options.sign/MetadataSignOptions#setDataEncryption(com.groupdocs.signature.domain.extensions.encryption.IDataEncryption))  method to specify the encryption type ([read more](https://docs.groupdocs.com/display/signaturejava/Sign+documents+with+encrypted+metadata+text)). The following code sample shows how to use this option:

{{< gist GroupDocsGists f639c973af7a23efd745528f5b7676e9 "SignDocumentWithEncryptedMetadata.java" >}}

## Support of New File Formats

We have added the support of following file formats in the latest release:

*   [Scalable Vector Graphics File (.svg)](https://wiki.fileformat.com/page-description-language/svg/)  
    
*   [Corel Draw File (.cdr)](https://wiki.fileformat.com/image/cdr/)

If you are interested in migration to the latest release, just download and integrate [v19.11](https://downloads.groupdocs.com/signature/java/new-releases/groupdocs.signature-for-java-19.11/) in your applications. We have also updated the source code examples in our [GitHub repository](https://github.com/groupdocs-signature/GroupDocs.Signature-for-Java) so you can easily evaluate the API v2. For more details, consult the documentation or have a conversation with us on our [forum](https://forum.groupdocs.com/c/signature).




