---
title: 'Generate QR Code in Java to Sign Documents and Images'
date: Fri, 19 Feb 2021 11:45:00 +0000
draft: false
url: /2021/02/19/generate-qr-codes-in-java-to-sign-documents-and-images/
aliases:
    - /2020/11/17/esign-documents-and-images-with-qr-code-in-java/
author: 'Shoaib Khan'
summary: "**QR code** (**Q**uick **R**esponse code) is the type of 2D Barcodes or matrix barcode. It is the machine-readable label that contains information about the attached item. This article will guide you about programmatically adding QR codes to electronically sign your documents and images using Java."
tags: ['Add QR Code in Java', 'Attach QR Code with Images in Java', 'generate QR Code in Java', 'QR codes in Java', 'Sign docs with QR code in Java', 'Sign Images with QR code in Java']
categories: ['GroupDocs.Signature Product Family']
---

**QR code** (**Q**uick **R**esponse code) is the type of 2D Barcodes or matrix barcode. It is the machine-readable label that contains information about the attached item. This article will guide you about programmatically generating QR codes in Java to electronically sign your documents and images.



{{< figure align=center src="images/add-qr-code-to-docs-and-images-using-java.png" alt="Add QR Code to documents and images in Java">}}


Here are the quick links to the covered topics:

*   [QR code Generation Java API][2]
*   [Generate QR code and Add to Documents in Java][3]
*   [Generate and Add QR code to JPG, PNG, or WebP Image in Java][4]

## Java API to Generate QR Codes {#java-api-for-qr-codes}



{{< figure align=center src="images/groupdocs-signature-java.png" alt="GroupDocs.Signature for Java">}}


In this article, I am using [GroupDocs.Signature for Java][5] API to generate QR codes and attached these to PDF files, Word documents, spreadsheets, presentations, and images. This API supports different types of electronic signatures for a vast variety of file formats. Among QR code types, the API supports the following:

*   Aztec Code
*   DataMatrix Code
*   GS1 DataMatrix
*   GS1 QR
*   QR

### Download and Configure

You may get the JAR file from the [downloads][6] section, or add the following pom.xml configuration in your Maven-based Java applications before you move on to examples. For the details, you may visit the [API Reference][7].

```
<repository>
	<id>GroupDocsJavaAPI</id>
	<name>GroupDocs Java API</name>
	<url>http://repository.groupdocs.com/repo/</url>
</repository>
<dependency>
        <groupId>com.groupdocs</groupId>
        <artifactId>groupdocs-signature</artifactId>
        <version>21.2</version> 
</dependency>
```

## Generate QR Code in Java - Add to PDF, Word, Excel, PPT {#add-qr-code-to-documents-in-java}

The **Signature** and **QrCodeSignOptions** classes can quickly create and add different types of QR codes to documents and images in Java.

1.  Create the **Signature** class object with the source document.
2.  Set the QR code properties using the **QrCodeSignOptions** class.
3.  Most importantly, select the appropriate from the QR code types.
4.  Call the **sign** method with the Signature object, passing the resultant document path and QR code options.

The following Java code will generate QR code and attach it to the provided PDF document.

\[gist id="4c70c60f1f5bdfce19da18f8b9f6ca11" file="SignDocsWithQRCode.java"\]

The resultant PDF file is shown here with the QR code that is added using the above code. Similarly, you can provide any word document, spreadsheet, presentation, or any other [supported document format][8] to attach the QR codes.



{{< figure align=center src="images/Added-QR-Code-in-PDF-using-GroupDocs.Signature-APIs.png" alt="QR Code added to PDF using Signature API" caption="PDF file with added QR code using GroupDocs.Signature for Java API">}}


## Generate QR Code in Java - Add to JPG, PNG, or WebP Images {#add-qr-code-to-images-in-java}



{{< figure align=center src="images/image-with-qr-code.png" alt="Image with QR Code">}}


Now, you might be thinking that there will be a different strategy to add QR codes to images. The answer is NO. You can use the same above code to generate QR code and add it to the images as well. The API allows you to add QR codes to JPG/JPEG, PNG, WebP, BMP, GIF, SVG, CMX, and TIFF images.

You can also change the appearance of the QR codes like background color, forecolor, transparency, and more. Here, I have set the black background color and forecolor as white.

\[gist id="31c41589bda73b4310db679300628cb2" file="ChangeQRCodeAppearance.java"\]

## Conclusion

Now, you should be confident enough to generate QR codes within your Java applications to electronically signing documents and images using GroupDocs.Signature. To remove any ambiguity or any unaddressed scenario on the [documentation][9], feel free to contact the **Support Team** on the [forum][10]. Many other examples are also available on [GitHub][11].

## See Also

*   [Generate QR codes in C# for Documents and Images][12]






[1]: https://products.groupdocs.com/signature/java
[2]: #java-api-for-qr-codes
[3]: #add-qr-code-to-documents-in-java
[4]: #add-qr-code-to-images-in-java
[5]: https://products.groupdocs.com/signature/java
[6]: https://downloads.groupdocs.com/signature/java
[7]: https://apireference.groupdocs.com/signature/java
[8]: https://docs.groupdocs.com/signature/java/supported-document-formats/
[9]: https://docs.groupdocs.com/signature/java/
[10]: https://forum.groupdocs.com/c/signature
[11]: https://github.com/groupdocs-signature/GroupDocs.Signature-for-Java
[12]: https://blog.groupdocs.com/2020/11/18/sign-documents-and-images-with-qr-code-in-csharp/

