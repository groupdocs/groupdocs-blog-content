---
title: 'Taxonomic Classification of Documents using C# - (IAB-2 &amp; Document Taxonomy)'
date: Wed, 27 Oct 2021 12:24:00 +0000
draft: false
url: /2021/10/27/taxonomic-classification-of-documents-using-csharp/
author: 'Shoaib Khan'
summary: "A classification is basically an approach in which text is systematically identified and then organized according to rules. Taxonomy defines the science of such classification. When you are dealing with a bunch of textual documents, it gets hard to find a topic of any document until the taxonomic classification of the content. In this article, you will learn **how to programmatically classify documents according to IAB-2 and document taxonomy using C#**."
tags: ['Classify Documents using CSharp', 'Document Classification in CSharp', 'Document Taxonomy using CSharp', 'Taxonomic Classification using CSharp']
categories: ['GroupDocs.Classification Product Family']
---

A classification is basically an approach in which text is systematically identified and then organized according to rules. Taxonomy defines the science of such classification. When you are dealing with a bunch of textual documents, it gets hard to find a topic of any document until the taxonomic classification of the content. In this article, you will learn **how to programmatically classify documents according to IAB-2 and document taxonomy using C#**.

The following topics are covered below:

*   [.NET API for Taxonomic Classification][1]
*   [Document Classifcation with IAB-2 Taxonomy][2]
*   [Classify Documents with Document Taxonomy][3]
*   [Classify Password Protected Documents][4]

## .NET API for Taxonomic Classification of Documents {#document-classification-dotnet-api}

[GroupDocs.Classification][5] provides the classification solution for different kinds of applications. Its .NET API allows you to classify documents of various file formats according to different taxonomic categories within your .NET applications. We will use its [GroupDocs.Classification for .NET][6] API for the classification of PDF and Word documents using C#.

You can download the **DLLs** or **MSI** installer from the [downloads section][7] or install the API in your .NET application via [NuGet][8].

```
PM> Install-Package GroupDocs.Classification
```

## Classify Documents with IAB-2 Taxonomy using C# {#classify-with-iab-2-taxonomy}

IAB-2 categorizes the document's content into multiple [topics][9] and then classifies it based on the depth level. The following are the steps to identify the taxonomic classification of documents with [IAB-2 taxonomy][10] using C#.

*   Instantiate the classifier using [Classifier][11] class.
*   Define the input document and input folder.
*   Define the [Taxonomy][12] as **IAB2**.
*   Set the count for the first few best results in the response. (_Optional_)
*   Get the taxonomic categories by calling [Classify][13] method with the defined parameters.
*   Print the [Best Class Name][14] and [Probability][15] using the [classification response][16] of the Classify method.

The following C# source code shows how to classify documents using **IAB-2 taxonomy** and get some of the top document classification results.

{{< gist GroupDocsGists ca2a11f8c02562c2a73f419451115fa1 "ClassifyDocsWithIAB2Taxonomy.cs" >}}

```
 Class: Technology\_&Computing,     Probability: 0.8188434 
 Class: Video\_Gaming,                     Probability: 0.12686 
 Class: Hobbies&\_Interests,             Probability: 0.03112753 
 Class: Music\_and\_Audio,                Probability: 0.006756512
```

## Classify Documents with Document Taxonomy using C# {#classify-with-document-taxonomy}

Documents taxonomy is used to identify different [document classes][17], such as Invoices, CVs, forms, emails, etc. The following are the steps to identify the taxonomic classification of documents with document taxonomy using C#.

*   Instantiate the classifier using [Classifier][18] class.
*   Set the input document and folder.
*   Define the [Taxonomy][19] as **Documents**.
*   Set the count for the number of top results in the response. (_Optional_)
*   Get the taxonomic groups by calling [Classify][20] method with the above defined parameters.
*   Print the [Best Class Name][21] and [Probability][22] using the [classification response][23] of the Classify method.

The following C# source code shows how to classify documents and get some of the best taxonomic categories using **document taxonomy**.

{{< gist GroupDocsGists ca2a11f8c02562c2a73f419451115fa1 "ClassifyDocsWithDocumentTaxonomy.cs" >}}

```
 Class: ADVE,         Probability: 0.3874436
 Class: Resume,     Probability: 0.2438204
 Class: News,         Probability: 0.1357582
 Class: Memo,        Probability: 0.0641943
```

## Classify Password Protected Documents using C# {#classify-secured-documents}

If your document is secured with a password, you can just provide the credentials while classifying. The following are the steps for the classification of password-protected documents using C#

*   Instantiate the [Classifier][24].
*   Define the input document, input folder, and password of the protected document.
*   Define the [Taxonomy][25] as **Documents**.
*   Get the taxonomic group by calling [Classify][26] method with the defined parameters.
*   Get the [Best Class Name][27] and [Probability][28] from the [response][29] of the Classify method.

The following code snippet shows how to classify password-protected documents and get the best taxonomic category using the default taxonomy (IAB-2).

{{< gist GroupDocsGists ca2a11f8c02562c2a73f419451115fa1 "ClassifyPasswordProtectedDocuments.cs" >}}

```
Best Class: Hobbies\_&\_Interests,      Probability: 0.4548415
```

The default values for the taxonomy would be IAB-2 and the count of the best results would be 1.

## Get a Free License

You can [get a free temporary license][30] in order to use the API without the evaluation limitations.

## Conclusion

To conclude, we learned to classify various kinds of documents using different taxonomies. More precisely, we classified PDF documents as per IAB-2 and document taxonomies using C#. Further, we discussed how we can classify password-protected Word documents with default or specific taxonomic classification. Now you can integrate the document classification feature within your .NET application.

For more about the API, visit the [documentation][31]. For queries, contact us via the [forum][32].

## See Also

*   [Classify Text with IAB-2 & Document Taxonomy using C#][33]
*   [Classify Customer's Feedback using Sentiment Analysis using C#][34]







[1]: #document-classification-dotnet-api
[2]: #classify-with-iab-2-taxonomy
[3]: #classify-with-document-taxonomy
[4]: #classify-secured-documents
[5]: https://products.groupdocs.com/classification/
[6]: https://products.groupdocs.com/classification/net/
[7]: https://downloads.groupdocs.com/classification/net
[8]: https://www.nuget.org/packages/groupdocs.classification
[9]: https://docs.groupdocs.com/classification/net/taxonomies/
[10]: https://www.iab.com/guidelines/content-taxonomy/
[11]: https://apireference.groupdocs.com/classification/net/groupdocs.classification/classifier
[12]: https://apireference.groupdocs.com/classification/net/groupdocs.classification/taxonomy
[13]: https://apireference.groupdocs.com/classification/net/groupdocs.classification/classifier/methods/classify/index
[14]: https://apireference.groupdocs.com/classification/net/groupdocs.classification.dto/classificationresponse/properties/bestclassname
[15]: https://apireference.groupdocs.com/classification/net/groupdocs.classification.dto/classificationresponse/properties/bestclassprobability
[16]: https://apireference.groupdocs.com/classification/net/groupdocs.classification.dto/classificationresponse/properties/index
[17]: https://docs.groupdocs.com/classification/net/taxonomies/
[18]: https://apireference.groupdocs.com/classification/net/groupdocs.classification/classifier
[19]: https://apireference.groupdocs.com/classification/net/groupdocs.classification/taxonomy
[20]: https://apireference.groupdocs.com/classification/net/groupdocs.classification/classifier/methods/classify/index
[21]: https://apireference.groupdocs.com/classification/net/groupdocs.classification.dto/classificationresponse/properties/bestclassname
[22]: https://apireference.groupdocs.com/classification/net/groupdocs.classification.dto/classificationresponse/properties/bestclassprobability
[23]: https://apireference.groupdocs.com/classification/net/groupdocs.classification.dto/classificationresponse/properties/index
[24]: https://apireference.groupdocs.com/classification/net/groupdocs.classification/classifier
[25]: https://apireference.groupdocs.com/classification/net/groupdocs.classification/taxonomy
[26]: https://apireference.groupdocs.com/classification/net/groupdocs.classification/classifier/methods/classify/index
[27]: https://apireference.groupdocs.com/classification/net/groupdocs.classification.dto/classificationresponse/properties/bestclassname
[28]: https://apireference.groupdocs.com/classification/net/groupdocs.classification.dto/classificationresponse/properties/bestclassprobability
[29]: https://apireference.groupdocs.com/classification/net/groupdocs.classification.dto/classificationresponse/properties/index
[30]: https://purchase.groupdocs.com/temporary-license
[31]: https://docs.groupdocs.com/classification
[32]: https://forum.groupdocs.com/
[33]: https://blog.groupdocs.com/2021/10/31/taxonomic-classification-of-text-using-csharp/
[34]: https://blog.groupdocs.com/2020/06/17/classify-customers-feedback-using-sentiment-analysis-in-csharp/

