---
title: 'Set Text Shadow in Text Signatures using Java E-Signing API v18.1'
date: Wed, 28 Feb 2018 15:43:27 +0000
draft: false
url: /2018/02/28/java-e-signing-api-v18.1/
author: 'Samicheema'
summary: ''
tags: []
categories: ['GroupDocs.Signature for Java', 'GroupDocs.Signature Product Family']
---

[![GroupDocs.Signature](https://blog.groupdocs.com/wp-content/uploads/sites/4/2017/03/groupdocs-signature-java.png)](https://www.groupdocs.com/products/signature/java)

The team [GroupDocs](https://www.groupdocs.com/) is really excited to announce the another monthly release of [GroupDocs.Signature for Java](https://products.groupdocs.com/signature/java) v18.1. This [release](https://docs.groupdocs.com/display/signaturejava/GroupDocs.Signature+for+Java+18.1+Release+Notes) comes up with a feature of setting Text Shadow for Slides, Words and Cells documents. Furthermore, many improvements and fixes are also introduced in this version of the API. We would recommend you to [download](https://downloads.groupdocs.com/signature/java) the new version of API and evaluate the exciting features to enhance document e-signing experience.

# eSignature API for Java v18.1 - Features

## Ability to set Text Shadow in text signaturesUsing version 18.1, users can set Text Shadow in text signatures for Slides, Words and Cells documents. Following code sample shows how to set Text Shadow in text signatures for Slides:```
SlidesSignTextOptions signOptions = new SlidesSignTextOptions("John Smith");
// set up shadow options for text
TextShadow shadow = new TextShadow();
shadow.setColor(Color.ORANGE);
shadow.setAngle(135);
shadow.setBlur(5);
shadow.setDistance(4);
shadow.setTransparency(0.2);
		  
//add text shadow to signature extensions
signOptions.getExtensions().add(shadow); 
```

## Set Text Shadow effect for text as image signatureUsers can set Text Shadow effect for text as image signature for all document types.

# Java eSignature API v18.1 - Improvements

*   Signature and Verification events arguments with additional properties
*   Information of URL provided document with corrected value
*   Verification of result with additional properties
*   Result of Signing methods when Document provided by URL
*   TextShadow class implementation and namespace

# e-Signing API for Java 18.1 - Bug Fixes

*   Output file name has no extension for Stream and URL Document source
*   Update result Stream of Sign methods
*   Loading Documents from URL without target filename

# Available Channels and Resources

Here are a few channels and resources for you to learn, try and get technical support on **GroupDocs.Signature** **API for Java**:

*   [Download](https://downloads.groupdocs.com/signature/java "Download") – JAR Files
*   [Documentation](https://docs.groupdocs.com/display/signaturejava/Home "Documentation") – API Docs
*   [Product Support Forum](https://forum.groupdocs.com/c/signature "Product Support Forum") – Technical Support Forum for GroupDocs.Signature
*   [Examples](https://github.com/groupdocs-signature/GroupDocs.Signature-for-Java "Examples") – GitHub source code examples

# Feedback

As always, you are welcome to share your feedback to improve this product. We will be happy to know your thoughts. Just create a [forum thread](https://forum.groupdocs.com/c/signature) and our dedicated support team will be there to respond.




