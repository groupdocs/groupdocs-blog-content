---
title: "Taxonomic Classification of Raw Text using C# - (IAB-2 &amp; Document Taxonomy)"
seoTitle: "Classify Text with IAB-2 & Document Taxonomies using C#"
description: "Taxonomic classification of documents using C# within .NET applications. Classify the text with IAB-2 or Documents taxonomies using classification API."
date: Sun, 31 Oct 2021 10:22:00 +0000
draft: false
url: /2021/10/31/taxonomic-classification-of-text-using-csharp/
aliases:
    - /2019/12/10/classify-text-using-iab-2-or-document-taxonomies-in-csharp/
author: 'Shoaib Khan'
summary: "In an article, we discussed how we can [analyze and classify complete documents programmatically][1]. It is often required to classify just some part of the document or only a few statements. In this article, we will identify the best possible taxonomic categories of the selected text. We will learn **how we can classify text according to IAB-2 and document taxonomies using C#**."
tags: ['Classify Text using CSharp', 'document taxonomy', 'Document Taxonomy using CSharp', 'Taxonomic Classification using CSharp', 'Text Classification using CSharp']
categories: ['GroupDocs.Classification Product Family']
---

Earlier, we discussed how we can [automate the analysis and classify complete documents programmatically][2]. It is often required to classify just some part of the document or only a few statements. In this article, we will identify the best possible taxonomic categories of the selected text. We will learn **how we can classify text according to IAB-2 and document taxonomies using C#**.

The following topics are covered below:

- [.NET API for Taxonomic Classification of Text][3]
- [Text Classification with IAB-2 Taxonomy using C#][4]
- [Text Classification with Document Taxonomy using C#][5]

## .NET API for Taxonomic Classification of Text {#text-classification-dotnet-api}

[GroupDocs.Classification for .NET][6] is the API that allows different techniques for the classification of text content within .NET applications. We will use this API to find the best possible taxonomic categories of the provided text using C# in examples.

You can download the **DLLs** or **MSI** installer from the [downloads section][7] or install the API in your .NET application via [NuGet][8].

```
PM> Install-Package GroupDocs.Classification
```

## Text Classification with IAB-2 Taxonomy using C# {#classify-text-with-iab-2-taxonomy}

IAB-2 categorizes the content into defined [taxonomic categories][9] and then classifies it based on the analysis. The following are the steps for taxonomic classification of text with [IAB-2 taxonomy][10] using C#.

*   Instantiate the classifier using [Classifier][11] class.
*   Define the text for taxonomic analysis.
*   Set the [Taxonomy][12] as **IAB2**.
*   Set the number of best results count as a result of classification. (_Optional_)
*   Get the taxonomic categories of the provided text by calling [Classify][13] method with the defined parameters.
*   Print the [BestResults][14] from the [classification response][15] of the Classify method.

The following C# source code shows how to classify text using **IAB-2 taxonomy** and get the top categories with the best match.

{{< gist GroupDocsGists 68adb40cdb317125614e04c8d1cf56b7 "ClassifyTextWithIAB2Taxonomy.cs" >}}

```
 Class: Healthy\_Living,      Probability: 0.4144087
 Class: Medical\_Health,     Probability: 0.2108202
 Class: Science,                 Probability: 0.1584931
```

## Text Classification with Document Taxonomy using C# {#classify-text-with-document-taxonomy}

Documents taxonomy classifies the content into different [document classes][16], such as advertisements, invoices, news, resume, letters, emails, etc. The following are the steps for taxonomic classification of text with document taxonomy using C#.

*   Instantiate the [Classifier][17].
*   Load the text for taxonomic analysis.
*   Define the number of best results count as a result of classification. (_Optional_)
*   Set the [Taxonomy][18] as **Documents**.
*   Get the taxonomic groups by calling [Classify][19] method with the above defined parameters.
*   Print the [BestResults][20] from the [classification response][21] of the Classify method.

The following C# source code shows how to classify text content and get some of its top taxonomic categories using **document taxonomy**.

{{< gist GroupDocsGists 68adb40cdb317125614e04c8d1cf56b7 "ClassifyTextWithDocumentTaxonomy.cs" >}}

```
 Class: ADVE,      Probability: 0.9999645
 Class: Report,     Probability: 3.461805E-05
```

## Get a Free License

You can [get a free temporary license][22] in order to use the API without the evaluation limitations.

## Conclusion

To sum up, we learned to classify various kinds of documents using different taxonomies. In the examples, we classified the text as per IAB-2 and the document taxonomies using C#. After going through the series of posts, you can build your own .NET classification application to [classify documents][23] as well as text with different taxonomies and configurations.

For more about the API, visit the [documentation][24]. For queries, contact us via the [forum][25].

## See Also

*   [Classify Customer's Feedback using Sentiment Analysis using C#][26]
*   [Taxonomic Classification of Documents using C#][27]







[1]: https://blog.groupdocs.com/2021/10/27/taxonomic-classification-of-documents-using-csharp/
[2]: https://blog.groupdocs.com/2021/10/27/taxonomic-classification-of-documents-using-csharp/
[3]: #text-classification-dotnet-api
[4]: #classify-text-with-iab-2-taxonomy
[5]: #classify-text-with-document-taxonomy
[6]: https://products.groupdocs.com/classification/
[7]: https://downloads.groupdocs.com/classification/net
[8]: https://www.nuget.org/packages/groupdocs.classification
[9]: https://docs.groupdocs.com/classification/net/taxonomies/
[10]: https://www.iab.com/guidelines/content-taxonomy/
[11]: https://apireference.groupdocs.com/classification/net/groupdocs.classification/classifier
[12]: https://apireference.groupdocs.com/classification/net/groupdocs.classification/taxonomy
[13]: https://apireference.groupdocs.com/classification/net/groupdocs.classification/classifier/methods/classify/index
[14]: https://apireference.groupdocs.com/classification/net/groupdocs.classification.dto/classificationresponse/properties/bestresults
[15]: https://apireference.groupdocs.com/classification/net/groupdocs.classification.dto/classificationresponse/properties/index
[16]: https://docs.groupdocs.com/classification/net/taxonomies/
[17]: https://apireference.groupdocs.com/classification/net/groupdocs.classification/classifier
[18]: https://apireference.groupdocs.com/classification/net/groupdocs.classification/taxonomy
[19]: https://apireference.groupdocs.com/classification/net/groupdocs.classification/classifier/methods/classify/index
[20]: https://apireference.groupdocs.com/classification/net/groupdocs.classification.dto/classificationresponse/properties/bestresults
[21]: https://apireference.groupdocs.com/classification/net/groupdocs.classification.dto/classificationresponse/properties/index
[22]: https://purchase.groupdocs.com/temporary-license
[23]: https://blog.groupdocs.com/2021/10/27/taxonomic-classification-of-documents-using-csharp/
[24]: https://docs.groupdocs.com/classification
[25]: https://forum.groupdocs.com/
[26]: https://blog.groupdocs.com/2020/06/17/classify-customers-feedback-using-sentiment-analysis-in-csharp/
[27]: https://blog.groupdocs.com/2021/10/27/taxonomic-classification-of-documents-using-csharp/

