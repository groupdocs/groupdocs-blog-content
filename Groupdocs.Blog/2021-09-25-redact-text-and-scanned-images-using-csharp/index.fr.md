---
title: "Rédaction de documents PDF numérisés en C#"
date: Sat, 25 Sep 2021 09:31:01 +0000
draft: false
url: /fr/2021/09/25/redact-text-and-scanned-images-using-csharp/
author: 'Shoaib Khan'
summary: "Nous avons souvent besoin de cacher les informations confidentielles et sensibles dans les documents. Dans d'autres articles, nous avons discuté des différentes stratégies pour rechercher des mots et même rechercher des synonymes dans plusieurs documents. Cet article vous explique **comment biffer du texte PDF et du texte dans des images dans un document à l'aide de C#**."
tags: ['Blackout Text', 'Blackout Text in PDF', 'redact documents', 'Redact in CSharp', 'redact pdf', 'Redact PDF in CSharp', 'Redact Text in CSharp', 'Redact Text in Image', 'Redact Text in PDF']
categories: ['GroupDocs.Redaction Product Family']
---

Nous avons souvent besoin de cacher les informations confidentielles et sensibles dans les documents. Dans d'autres articles, nous avons discuté des [différentes stratégies pour rechercher des mots][1] et même [rechercher des synonymes dans plusieurs documents][2]. Cet article vous explique **comment biffer du texte PDF et du texte dans des images dans un document à l'aide de C#**.

Les sujets suivants seront abordés ci-dessous :

* [Caviardage de texte et d'image - API .NET][3]
* [Caviarder le texte PDF et les informations numérisées à l'aide de C#][4]

## API .NET pour la rédaction de texte et d'image {#redaction-dotnet-api}

[GroupDocs.Redaction][5] fournit l'[API .NET de rédaction de documents][6] qui permet de masquer et de supprimer des informations confidentielles dans des documents de différents formats de fichiers. En plus de la rédaction et de la rastérisation simples du texte, l'API permet également d'identifier le texte dans les images qui peuvent avoir été à l'intérieur de n'importe quel document, comme les fichiers PDF numérisés les plus couramment utilisés. La liste complète des [formats de fichiers pris en charge][7] est disponible dans la documentation.

Vous pouvez télécharger le programme d'installation **DLLs** ou **MSI** à partir de la [section téléchargements][8] ou installer l'API dans votre application .NET via [NuGet][9].

### Installer via la console du gestionnaire de packages```
PM> Install-Package GroupDocs.Redaction
```

### Install via NuGet Package Manager



{{< figure align=center src="images/GroupDocs.Redaction-NuGet-Package-Install-1024x802.jpg" alt="GroupDocs.Redaction - NuGet Package - Install">}}


## Redact PDF Text and Scanned Image Text using C# {#redact-text-and-scanned-text}

There are many different [ways to find and replace text in documents][10] that have already been discussed. You can find specific words in any document, find with case sensitivity, or by using regular expressions. I will be using the following PDF document, that contains some text and also an image with some text in it. Here we will combine the OCR and redaction process using GroupDocs.Redaction for .NET. Firstly, we will identify the text in the document and also the text which is inside the image of the document. Secondly, we will cover it with a black box to demonstrate how to programmatically hide any legal or confidential information even if is as text within a scanned document image.



{{< figure align=center src="images/PDF-with-text-and-scanned-image.jpg" alt="PDF with text and scanned image">}}


The following steps will detect and replace the text in a PDF document, that contains regular text along with some text within an embedded image.

*   Prepare the redactor settings using any OCR Connector.
*   Load the PDF document using [Redactor][11] class with the prepared settings and any specific loading options.
*   Define the [replacement option][12]. I have defined to black out the text.
*   For the text redaction, use the appropriate text selection strategy. I have used [RegEx][13].
*   Apply the redactions using the [Apply][14] method.
*   Save the redacted document using [Save][15] method.

The following source code redacts the selected text within a PDF document using C#.

{{< gist GroupDocsGists f7e22d6719c21108d804756913b2ca3f "RedactTextInImage.cs" >}}

The output of the above code is as follows that black out the selected text of the PDF document.



{{< figure align=center src="images/Redacted-PDF-with-text-and-scanned-image.jpg" alt="Redact PDF text and scanned image text">}}


## Get a Free API License

You can [get a free temporary license][16] to use the API without the evaluation limitations.

## Conclusion

To sum up, you have learned to redact text in documents. More importantly and precisely, we discussed how to redact text in images within a PDF document using C#. We selected the text to redact using regular expressions, however, it can be selected using many different ways as discussed earlier. Later we blackout the search results using a black rectangle box over the searched text.

For more details to learn about the API, visit the [documentation][17]. For queries, contact us via the [forum][18].

## See Also

*   [Find and Replace Words in Documents using C#][19]
*   [Find and Remove Watermarks from Documents in C#][20]
*   [Add or Remove Annotations within Word files using C#][21]







[1]: https://blog.groupdocs.com/2021/08/04/find-and-replace-text-in-documents-using-csharp/
[2]: https://blog.groupdocs.com/2021/09/14/find-synonyms-of-words-using-csharp/
[3]: #redaction-dotnet-api
[4]: #redact-text-and-scanned-text
[5]: https://products.groupdocs.com/redaction/
[6]: https://products.groupdocs.com/redaction/net/
[7]: https://docs.groupdocs.com/redaction/net/supported-document-formats/
[8]: https://downloads.groupdocs.com/redaction
[9]: https://www.nuget.org/packages/groupdocs.redaction
[10]: https://blog.groupdocs.com/2021/08/04/find-and-replace-text-in-documents-using-csharp/
[11]: https://apireference.groupdocs.com/redaction/net/groupdocs.redaction/redactor
[12]: https://apireference.groupdocs.com/redaction/net/groupdocs.redaction.redactions/replacementoptions
[13]: https://apireference.groupdocs.com/redaction/net/groupdocs.redaction.redactions/regexredaction
[14]: https://apireference.groupdocs.com/redaction/net/groupdocs.redaction/redactor/methods/apply/index
[15]: https://apireference.groupdocs.com/redaction/net/groupdocs.redaction/redactor/methods/save/index
[16]: https://purchase.groupdocs.com/temporary-license
[17]: https://docs.groupdocs.com/redaction
[18]: https://forum.groupdocs.com/
[19]: https://blog.groupdocs.com/2021/08/04/find-and-replace-text-in-documents-using-csharp/
[20]: https://blog.groupdocs.com/2020/11/27/find-and-remove-watermarks-from-documents-in-csharp/
[21]: https://blog.groupdocs.com/2021/06/23/annotate-word-documents-using-csharp/


