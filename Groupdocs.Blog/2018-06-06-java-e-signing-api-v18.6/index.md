---
title: 'Introducing Stamp Types in GroupDocs.Signature for Java 18.6'
date: Wed, 06 Jun 2018 19:42:12 +0000
draft: false
url: /2018/06/06/java-e-signing-api-v18.6/
author: 'Samicheema'
summary: ''
tags: []
categories: ['GroupDocs.Signature for Java', 'GroupDocs.Signature Product Family']
---

[![GroupDocs.Signature](https://blog.groupdocs.com/wp-content/uploads/sites/4/2017/03/groupdocs-signature-java.png)](https://www.groupdocs.com/products/signature/java)

Team [GroupDocs](https://www.groupdocs.com/) is excited to release version 18.6 of GroupDocs.Signature for Java API. This latest version supports to sign documents with stamp signatures either in a round or a square shape. Apart from that, few fixes are also introduced in this [release](https://docs.groupdocs.com/display/signaturejava/GroupDocs.Signature+for+Java+18.6+Release+Notes) of the API. We would recommend you to download the new version of API and evaluate the exciting features to enhance document e-signing experience.

# Features

## Encode and Search Custom Object to QR-Code SignatureNow users of this API can add and search custom object to QR-Code signatures. Following code sample shows how to add a custom object to QR-Code signatures:```
// setup custom object instance with required data
DocumentSignature docSignature =new DocumentSignature();
docSignature.setID(UUID.randomUUID().toString());
docSignature.setAuthor("Mr.Sherlock");
docSignature.setSigned(new java.util.Date());
docSignature.setDataFactor(new java.math.BigDecimal("0.67"));
// setup options
PdfQRCodeSignOptions signOptions = new PdfQRCodeSignOptions();
// QR-code type
signOptions.setEncodeType(QRCodeTypes.QR);
// setup Data property with custom object
signOptions.setData(docSignature); 
```

## Square type for Stamp SignaturesUser can sign documents with stamp signatures either in a square or a round shape. Following code sample shows how to sign document with square type stamp signature:```
ImagesStampSignOptions signOptions = new ImagesStampSignOptions();
// setup stamp type
signOptions.setStampType(StampTypes.SQUARE);
// sign document with square stamp
String signedPath = (String)handler.sign("invoice.png", signOptions,saveOptions); 
```

## New Slides File FormatsFollowing are the new slides file formats introduced in this release of the API:

*   otp
*   potx
*   potm
*   ppsm

## QR-Code Embedded ClassesNew embedded classes introduced for QR-Code are as follow:

*   VCard
*   Email

# Bug Fixes

*   Signed .doc files have .docx extension and .ppt files have .pps extension

# Available Channels and Resources

Here are a few channels and resources for you to learn, try and get technical support on **GroupDocs.Signature** **API for Java**:

*   Download – JAR Files
*   [Documentation](https://docs.groupdocs.com/display/signaturejava/Home "Documentation") – API Docs
*   [Product Support Forum](https://forum.groupdocs.com/c/signature "Product Support Forum") – Technical Support Forum for GroupDocs.Signature
*   [Examples](https://github.com/groupdocs-signature/GroupDocs.Signature-for-Java "Examples") – GitHub source code examples

# Feedback

As always, you are welcome to share your feedback to improve this product. We will be happy to know your thoughts. Just create a [forum thread](https://forum.groupdocs.com/c/signature) and our dedicated support team will be there to respond.




