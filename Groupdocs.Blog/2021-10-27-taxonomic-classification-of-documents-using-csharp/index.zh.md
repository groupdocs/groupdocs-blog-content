---
title: "使用 C# 对文档进行分类分类 - (IAB-2 & Document Taxonomy)"
date: Wed, 27 Oct 2021 12:24:00 +0000
draft: false
url: /zh/2021/10/27/taxonomic-classification-of-documents-using-csharp/
author: 'Shoaib Khan'
summary: "分类基本上是一种方法，其中系统地识别文本，然后根据规则进行组织。分类学定义了这种分类的科学。当您处理一堆文本文档时，在对内容进行分类之前，很难找到任何文档的主题。在本文中，您将学习**如何根据 IAB-2 以编程方式对文档进行分类，并使用 C#** 进行文档分类。"
tags: ['Classify Documents using CSharp', 'Document Classification in CSharp', 'Document Taxonomy using CSharp', 'Taxonomic Classification using CSharp']
categories: ['GroupDocs.Classification Product Family']
---

分类基本上是一种方法，其中系统地识别文本，然后根据规则进行组织。分类学定义了这种分类的科学。当您处理一堆文本文档时，在对内容进行分类之前，很难找到任何文档的主题。在本文中，您将学习**如何根据 IAB-2 以编程方式对文档进行分类，并使用 C# 进行文档分类**。

以下主题涵盖以下内容：

* [用于分类的.NET API][1]
* [使用 IAB-2 分类的文档分类][2]
* [使用文档分类对文档进行分类][3]
* [分类受密码保护的文件][4]

## 用于文档分类的 .NET API {#document-classification-dotnet-api}

[GroupDocs.Classification][5] 为不同类型的应用程序提供分类解决方案。它的 .NET API 允许您根据 .NET 应用程序中的不同分类类别对各种文件格式的文档进行分类。我们将使用其 [GroupDocs.Classification for .NET][6] API 使用 C# 对 PDF 和 Word 文档进行分类。

您可以从 [下载部分][7] 下载 **DLLs** 或 **MSI** 安装程序，或通过 [NuGet][8] 在您的 .NET 应用程序中安装 API。

```
PM> Install-Package GroupDocs.Classification
```

## 使用 C# 使用 IAB-2 分类法对文档进行分类 {#classify-with-iab-2-taxonomy}

IAB-2 将文档的内容分类为多个 [主题][9]，然后根据深度级别对其进行分类。以下是使用 C# 使用 [IAB-2 taxonomy][10] 识别文档分类的步骤。

* 使用 [Classifier][11] 类实例化分类器。
* 定义输入文件和输入文件夹。
* 将 [Taxonomy][12] 定义为 **IAB2**。
* 设置响应中前几个最佳结果的计数。 （_选修的_）
* 使用定义的参数调用[Classify][13] 方法获取分类类别。
* 使用 Classify 方法的 [classification response][16] 打印 [Best Class Name][14] 和 [Probability][15]。

以下 C# 源代码展示了如何使用 **IAB-2 分类法** 对文档进行分类并获得一些顶级文档分类结果。

```
/*
* Classify documents (PDF, Word, ...) with IAB-2 Taxonomy using C#
*/
Classifier classifier = new Classifier();
var filename = "document.pdf";
var response = classifier.Classify(filename, "<inputFolderPath>" , 4, Taxonomy.Iab2);
response.BestResults.ToList().ForEach(bestResult => Console.WriteLine($"Class: {bestResult.Name}, \t Probability: {bestResult.Probability}"));
```

```
 Class: Technology\_&Computing,     Probability: 0.8188434 
 Class: Video\_Gaming,                     Probability: 0.12686 
 Class: Hobbies&\_Interests,             Probability: 0.03112753 
 Class: Music\_and\_Audio,                Probability: 0.006756512
```

## 使用 C# 使用文档分类法对文档进行分类 {#classify-with-document-taxonomy}

文档分类法用于识别不同的[文档类][17]，例如发票、简历、表单、电子邮件等。以下是使用 C# 使用文档分类法识别文档分类的步骤。

* 使用 [Classifier][18] 类实例化分类器。
* 设置输入文件和文件夹。
* 将 [Taxonomy][19] 定义为 **Documents**。
* 设置响应中排名靠前的结果数的计数。 （_选修的_）
* 使用上述定义的参数调用[Classify][20] 方法获取分类群。
* 使用 Classify 方法的 [classification response][23] 打印 [Best Class Name][21] 和 [Probability][22]。

以下 C# 源代码展示了如何使用 **document taxonomy** 对文档进行分类并获得一些最佳分类类别。

```
/*
* Classify documents (PDF, Word, ...) with Document Taxonomy using C#
*/
Classifier classifier = new Classifier();
var filename = "document.pdf";
var response = classifier.Classify(filename, "<inputFolderPath>" , 4, Taxonomy.Documents);
response.BestResults.ToList().ForEach(bestResult => Console.WriteLine($"Class: {bestResult.Name}, \t Probability: {bestResult.Probability}"));
```

```
 Class: ADVE,         Probability: 0.3874436
 Class: Resume,     Probability: 0.2438204
 Class: News,         Probability: 0.1357582
 Class: Memo,        Probability: 0.0641943
```

## 使用 C# 对受密码保护的文档进行分类 {#classify-secured-documents}

如果您的文档使用密码保护，您可以在分类时提供凭据。以下是使用C#对受密码保护的文档进行分类的步骤

* 实例化[分类器][24]。
* 定义受保护文档的输入文档、输入文件夹和密码。
* 将 [Taxonomy][25] 定义为 **Documents**。
* 使用定义的参数调用[Classify][26] 方法获取分类群。
* 从Classify方法的[response][29]中获取[Best Class Name][27]和[Probability][28]。

以下代码片段显示了如何使用默认分类法 (IAB-2) 对受密码保护的文档进行分类并获得最佳分类法类别。

```
/*
* Classify password protected documents using C#
*/
Classifier classifier = new Classifier();
var filename = "password-protected.docx";
var response = classifier.Classify(filename, "<inputFolderPath>", password: "password");
Console.WriteLine($"Best Class: {response.BestClassName}, \t Probability: {response.BestClassProbability}");
```

```
Best Class: Hobbies\_&\_Interests,      Probability: 0.4548415
```

分类的默认值为 IAB-2，最佳结果的计数为 1。

## 获得免费许可证

您可以 [获得免费的临时许可证][30] 以便在没有评估限制的情况下使用 API。

## 结论

总而言之，我们学会了使用不同的分类法对各种文档进行分类。更准确地说，我们根据 IAB-2 对 PDF 文档进行分类，并使用 C# 对文档分类。此外，我们还讨论了如何使用默认或特定分类法对受密码保护的 Word 文档进行分类。现在您可以将文档分类功能集成到您的 .NET 应用程序中。

有关 API 的更多信息，请访问 [文档][31]。如有疑问，请通过 [论坛][32] 联系我们。

## 也可以看看

* [使用 IAB-2 分类文本和使用 C# 的文档分类法][33]
* [使用 C# 使用情感分析对客户的反馈进行分类][34]







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


