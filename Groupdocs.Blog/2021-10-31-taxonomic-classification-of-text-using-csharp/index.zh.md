---
title: "使用 C# 对原始文本进行分类 - (IAB-2 & Document Taxonomy)"
date: Sun, 31 Oct 2021 10:22:00 +0000
draft: false
url: /zh/2021/10/31/taxonomic-classification-of-text-using-csharp/
aliases:
- /2019/12/10/classify-text-using-iab-2-or-document-taxonomies-in-csharp/
author: 'Shoaib Khan'
summary: "在一篇文章中，我们讨论了如何[以编程方式分析和分类完整文档][1]。通常只需要对文档的某些部分或少数语句进行分类。在本文中，我们将确定所选文本的最佳分类类别。我们将学习**如何根据 IAB-2 对文本进行分类，并使用 C# 进行文档分类**。"
tags: ['Classify Text using CSharp', 'document taxonomy', 'Document Taxonomy using CSharp', 'Taxonomic Classification using CSharp', 'Text Classification using CSharp']
categories: ['GroupDocs.Classification Product Family']
---

早些时候，我们讨论了如何[以编程方式自动化分析和分类完整文档][2]。通常只需要对文档的某些部分或少数语句进行分类。在本文中，我们将确定所选文本的最佳分类类别。我们将学习**如何根据 IAB-2 对文本进行分类，并使用 C# 进行文档分类**。

以下主题涵盖以下内容：

- [用于文本分类的.NET API][3]
- [使用 C# 使用 IAB-2 分类法进行文本分类][4]
- [使用 C# 进行文档分类的文本分类][5]

## .NET API 用于文本分类 {#text-classification-dotnet-api}

[GroupDocs.Classification for .NET][6] 是允许使用不同技术对 .NET 应用程序中的文本内容进行分类的 API。我们将使用此 API 在示例中使用 C# 查找所提供文本的最佳分类类别。

您可以从 [下载部分][7] 下载 **DLLs** 或 **MSI** 安装程序，或通过 [NuGet][8] 在您的 .NET 应用程序中安装 API。

```
PM> Install-Package GroupDocs.Classification
```

## 使用 C# 使用 IAB-2 分类法进行文本分类 {#classify-text-with-iab-2-taxonomy}

IAB-2 将内容分类为定义的[分类类别][9]，然后根据分析对其进行分类。以下是使用 C# 使用 [IAB-2 taxonomy][10] 对文本进行分类分类的步骤。

* 使用 [Classifier][11] 类实例化分类器。
* 定义分类分析的文本。
* 将 [Taxonomy][12] 设置为 **IAB2**。
* 设置分类结果的最佳结果数。 （_选修的_）
* 通过使用定义的参数调用[Classify][13] 方法获取所提供文本的分类类别。
* 打印 Classify 方法的 [分类响应][15] 中的 [BestResults][14]。

以下 C# 源代码展示了如何使用 **IAB-2 分类法** 对文本进行分类，并获得最匹配的顶级类别。

```
/*
* Classify Text with IAB-2 Taxonomy using C#
*/
Classifier classifier = new Classifier();
string statement = "Medicine is an important part of our lives";

var response = classifier.Classify(statement, 3, Taxonomy.Iab2);
response.BestResults.ToList().ForEach(bestResult => Console.WriteLine($"Class: {bestResult.Name}, \tProbability: {bestResult.Probability}"));
```

```
 Class: Healthy\_Living,      Probability: 0.4144087
 Class: Medical\_Health,     Probability: 0.2108202
 Class: Science,                 Probability: 0.1584931
```

## 使用 C# 使用文档分类法进行文本分类 {#classify-text-with-document-taxonomy}

文档分类法将内容分类为不同的[文档类][16]，例如广告、发票、新闻、简历、信件、电子邮件等。以下是使用 C# 使用文档分类法对文本进行分类分类的步骤。

* 实例化[分类器][17]。
* 加载文本进行分类分析。
* 定义作为分类结果的最佳结果计数。 （_选修的_）
* 将 [Taxonomy][18] 设置为 **Documents**。
* 使用上述定义的参数调用[Classify][19] 方法获取分类群。
* 打印 Classify 方法的 [classification response][21] 中的 [BestResults][20]。

以下 C# 源代码展示了如何使用 **document taxonomy** 对文本内容进行分类并获取其一些顶级分类类别。

```
/*
* Classify Text with Document Taxonomy using C#
*/
Classifier classifier = new Classifier();
string statement = "Sooner or later technology will overcome labor work";

var response = classifier.Classify(statement, 2, Taxonomy.Documents);
response.BestResults.ToList().ForEach(bestResult => Console.WriteLine($"Class: {bestResult.Name}, \tProbability: {bestResult.Probability}"));
```

```
 Class: ADVE,      Probability: 0.9999645
 Class: Report,     Probability: 3.461805E-05
```

## 获得免费许可证

您可以 [获得免费的临时许可证][22] 以便在没有评估限制的情况下使用 API。

## 结论

总而言之，我们学会了使用不同的分类法对各种文档进行分类。在示例中，我们根据 IAB-2 对文本进行分类，并使用 C# 对文档分类。阅读完这一系列文章后，您可以构建自己的 .NET 分类应用程序来[分类文档][23] 以及具有不同分类和配置的文本。

有关 API 的更多信息，请访问 [文档][24]。如有疑问，请通过 [论坛][25] 联系我们。

## 也可以看看

* [使用 C# 使用情绪分析对客户的反馈进行分类][26]
* [使用 C# 对文档进行分类][27]







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


