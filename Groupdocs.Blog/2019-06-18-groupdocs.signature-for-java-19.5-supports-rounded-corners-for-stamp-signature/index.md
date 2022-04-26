---
title: 'GroupDocs.Signature for Java 19.5 Supports Rounded Corners for Stamp Signature'
date: Tue, 18 Jun 2019 11:52:13 +0000
draft: false
url: /2019/06/18/groupdocs.signature-for-java-19.5-supports-rounded-corners-for-stamp-signature/
author: 'Usman Aziz'
summary: ''
tags: ['digital document signature', 'digital signature', 'digital signature API for Java', 'e-sign API', 'e-signature', 'electronic signature', 'signature api for java', 'stamp signature', 'stamp with rounder corner']
categories: ['GroupDocs.Signature for Java', 'GroupDocs.Signature Product Family']
---



{{< figure align=center src="images/groupdocs-signature-java.png" alt="">}}


Many people use stamps as part of their documents to mark them as approved or completed. For example, when a document is to be signed by the concerned person at a company, he puts his signature as well as stamps the document as a proof that the document is signed by the authorized person. In other words, the stamps are used to seal the document that is being exchanged among multiple persons/parties.

Various companies use digital signatures to sign their document using automated systems. This way, they can avoid the efforts of manually signing a bunch of documents as well as they don't have to print the document for signatures and then scan the signed copy for distribution. If such companies have the requirement to sign as well as stamp their documents then how would they do it digitally? Well, here comes the GroupDocs.Signature that allows digital stamping of the documents.

Digital stamping is one of the salient features of the GroupDocs.Signature API. We provide a wide range of options to control the placement and appearance of the digital stamps in the document. The following is a snapshot of the document which we have stamped using our API.



{{< figure align=center src="images/RectangularStamp-1.png" alt="">}}


In the above snapshot, you can observe that the borderlines are flat. However, some of you may want to have rounded corners for the stamp. So keeping that in mind, we have provided the support of stamps with the round corners in [GroupDocs.Signature for Java 19.5](https://downloads.groupdocs.com/signature/java/new-releases/groupdocs.signature-for-java-19.5/). For this, we have added a new public class **SquareBorderLine** that inherits **BorderLine** to implement square stamp with rounded corners. This is how you can achieve it using the code.

{{< gist GroupDocsGists dfcb0f5756c43297d979dfa585d2fba0 "StampWithRoundedCorners.java" >}}

The following would be the output of the above written code.



{{< figure align=center src="images/RoundCornerStamp-1.png" alt="">}}


So if you want to implement this feature in your e-signing application, just [download](https://downloads.groupdocs.com/signature/java/new-releases/groupdocs.signature-for-java-19.5/) that latest release and integrate it into your application. In case you would have any query or question, do write to us on our [forum](https://forum.groupdocs.com/categories).




