---
title: 'Redact PDF Scanned Documents in Java'
date: Tue, 05 Oct 2021 04:21:00 +0000
draft: false
url: /2021/10/05/redact-text-and-scanned-images-using-java/
author: 'Shoaib Khan'
summary: "Want to secure the secret, or sensitive information that is within the documents? It is doable even if this is regular textual information or it is text with the scanned document with images. The earlier articles may help you refine your search, where we discussed the [different strategies to search words][1] and [search synonyms within multiple documents][2]. This article guides you about **how to redact PDF text and text in images within a document using Java**."
tags: ['Blackout Text', 'Blackout Text in PDF', 'redact documents', 'Redact in Java', 'Redact PDF files', 'Redact PDF in Java', 'Redact Text in Image', 'Redact Text in Java', 'Redact Text in PDF']
categories: ['GroupDocs.Redaction Product Family']
---

Want to secure the secret, or sensitive information that is within the documents? It is doable even if this is regular textual information or it is text with the scanned document with images. The earlier articles may help you refine your search, where we discussed the [different strategies to search words][3] and [search synonyms within multiple documents][4]. This article guides you about **how to redact PDF text and text in images within a document using Java**.

The following topics will be covered below:

*   [Text and image redaction – Java API][5]
*   [Redact PDF text and scanned Information using Java][6]

## Java API for Text and Image Redaction {#redaction-java-api}

GroupDocs.Redaction provides the [redaction solution to secure the classified information][7]. Its Java API allow you to redact or removing confidential information within documents of various file formats from your Java-based applications. Along with the simple text redaction and rasterization, the API also allows identifying the text in images that may have been inside any document like most commonly used scanned PDF files. The complete list of [supported file formats][8] is available in the documentation.

### Download or Configure

You may download the **JAR** file from the [downloads section][9], or just get the latest repository and dependency configurations for the pox.xml of your **maven-based** Java applications.

```
<repository>
	<id>GroupDocsJavaAPI</id>
	<name>GroupDocs Java API</name>
	<url>https://repository.groupdocs.com/repo/</url>
</repository>
<dependency>
        <groupId>com.groupdocs</groupId>
        <artifactId>groupdocs-redaction</artifactId>
        <version>21.6</version> 
</dependency>
```

## Redact PDF Text and Scanned Image Text using Java {#redact-text-and-scanned-text}

We have already discussed the different [ways to find and replace text in documents][10]. However, we can also redact text within images. I will use the following PDF document, that contains some text and also an image with some text. For this, we need to combine OCR with the redaction process. Firstly, we will identify the text in the document and also the text which is inside the image of the document. Then, we will cover it with a black box to programmatically hide any legal, confidential, or secret information even if is as text within a scanned document image.



{{< figure align=center src="images/PDF-with-text-and-scanned-image.jpg" alt="PDF with text and scanned image">}}


The following steps will detect and replace the text in the PDF documents, that contains regular text or any text within the embedded images.

*   Prepare the redactor settings using any OCR Connector.
*   Load your PDF file using [Redactor][11] class and also if there are any specific loading options required.
*   Define your [replacement options][12]. I am opting to black out the text.
*   Prepare the redactions; use the appropriate redaction strategy like [Phrase Redaction][13] or [RegEx redaction][14].
*   Apply the redactions using the [apply][15] method.
*   Save the redacted document using the [save][16] method.

The following source code redacts the selected text within a PDF document using Java.

{{< gist GroupDocsGists 15992c7e04f496134f00ffb297514c75 "RedactTextInImage.java" >}}

The output of the above code is as follows with the blacked-out selected text of the PDF document.



{{< figure align=center src="images/Redacted-PDF-with-text-and-scanned-image.jpg" alt="Redact PDF text and scanned image text">}}


## Get a Free API License

You can [get a free temporary license][17] to use the API without the evaluation limitations.

## Conclusion

To conclude, you have learned how to redact text in documents. Additionally, we discussed how to redact text in the images within a PDF document using Java. Similarly, you can redact text and images with documents of any other format. We used the regular expressions redaction, however, it can also be done using many different ways. Later we hid the search results using a black box.

For more details to learn about the API, visit the [documentation][18]. For queries, contact us via the [forum][19].

## See Also

*   [Find and Replace Words in Documents using Java][20]
*   [Find and Remove Watermarks from Documents in Java][21]
*   [Add or Remove Annotations of PDF files in Java][22]







[1]: https://blog.groupdocs.com/2021/09/01/find-and-replace-text-in-documents-using-java/
[2]: https://blog.groupdocs.com/2021/10/03/find-synonyms-in-multiple-files-using-java/
[3]: https://blog.groupdocs.com/2021/09/01/find-and-replace-text-in-documents-using-java/
[4]: https://blog.groupdocs.com/2021/10/03/find-synonyms-in-multiple-files-using-java/
[5]: #redaction-java-api
[6]: #redact-text-and-scanned-text
[7]: https://products.groupdocs.com/redaction/
[8]: https://docs.groupdocs.com/redaction/java/supported-document-formats/
[9]: https://downloads.groupdocs.com/redaction
[10]: https://blog.groupdocs.com/2021/09/01/find-and-replace-text-in-documents-using-java/
[11]: https://apireference.groupdocs.com/redaction/java/com.groupdocs.redaction/Redactor
[12]: https://apireference.groupdocs.com/redaction/java/com.groupdocs.redaction.redactions/ReplacementOptions
[13]: https://apireference.groupdocs.com/redaction/java/com.groupdocs.redaction.redactions/ExactPhraseRedaction
[14]: https://apireference.groupdocs.com/redaction/java/com.groupdocs.redaction.redactions/RegexRedaction
[15]: https://apireference.groupdocs.com/redaction/java/com.groupdocs.redaction/Redactor#apply(com.groupdocs.redaction.Redaction)
[16]: https://apireference.groupdocs.com/redaction/java/com.groupdocs.redaction/Redactor#save()
[17]: https://purchase.groupdocs.com/temporary-license
[18]: https://docs.groupdocs.com/redaction
[19]: https://forum.groupdocs.com/
[20]: https://blog.groupdocs.com/2021/09/01/find-and-replace-text-in-documents-using-java/
[21]: https://blog.groupdocs.com/2020/11/30/find-and-remove-watermarks-from-documents-in-java/
[22]: https://blog.groupdocs.com/2021/04/18/annotate-pdf-files-using-java/

