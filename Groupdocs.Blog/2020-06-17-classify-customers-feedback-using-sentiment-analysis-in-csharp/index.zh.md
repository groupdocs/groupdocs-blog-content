---
title: "使用 C# 中的情绪分析对客户反馈进行分类"
date: Wed, 17 Jun 2020 08:28:00 +0000
draft: false
url: /zh/2020/06/17/classify-customers-feedback-using-sentiment-analysis-in-csharp/
author: 'Shoaib Khan'
summary: "假设您有机会收到来自客户或其他来源的评论或评论，并且您想评估他们的积极程度。有一种方法可以分析此类评论，称为**情绪分析**。本文重点介绍基于 C# 的深度神经网络模型的情感分析工具。该模型适用于广泛的任务。"
tags: ['csharp code for sentiment analysis', 'csharp sentiment analysis', 'sentiment analysis csharp', 'sentiment analysis in csharp', 'sentiment classification in csharp']
categories: ['GroupDocs.Classification Product Family']
---

假设您有机会收到来自客户或其他来源的评论或评论，并且您想评估他们的积极程度。有一种方法可以分析此类评论，称为**情绪分析**。本文重点介绍基于 C# 的深度神经网络模型的情感分析工具。该模型适用于广泛的任务。

## .NET 的情绪分析 API

如果您想以编程方式进行情绪分析，[GroupDocs.Classification][1] 为您服务。它实现了一个通用的情感分类器，可用于评估产品评论、商店评论、应用程序评论、反馈等的语气。



{{< figure align=center src="images/groupdocs_classification-for-net.png" alt=".NET 的 GroupDocs.Classification">}}


本文将指导您对评论进行分类，并使用 C# 和 **GroupDocs.Classification for .NET** 分析积极性。因此，在开始之前，请确保通过以下任一方法安装 API：

* 使用 [NuGet][2] 包管理器安装。
* [下载][3] DLL 并将其引用到项目中。

## 如何在 C# 中使用情感分析对文本进行分类

为了解决这样的任务，我们可以使用一个名为 [Classifier][4] 的通用类，或者我们可以使用更简单、更轻量级的 Sentiment Classifier。以下是步骤：

* 初始化[SentimentClassifier][5]。
* 调用SentimentClassifier类的[PositiveProbability][6]方法，将文本作为需要分析的参数传入。
* PositiveProbability 方法将返回从 0 到 1 的正数。

这是使用情感分类查找任何语句的语气的 C# 代码。我们选择了以下情绪作为示例：

_“经验只是我们给错误取的名字”_

```
// Analyze the positivity of text using sentiment classifier in C#.
var sentiment = "Experience is simply the name we give our mistakes";
var sentimentClassifier = new SentimentClassifier();
/// PositiveProbability method returns the positive probability of the sentiment.
var positiveProbability = sentimentClassifier.PositiveProbability(sentiment);
Console.WriteLine($"Positive Probability of the sentiment { positiveProbability }");
```
```
Positive Probability of the sentiment: **0.1118**
```

任何大于 0.5 的值都表示情绪是积极的，0 到 0.5 之间的范围表示情绪是消极的。

现在根据提取的积极性，您可能会获得该最佳类别的情绪和概率的**最佳类别**。我们发现它的肯定概率是 0.11，所以它应该被归类为 **negative** 评论，它的 Best Class 应该是 **Negative** 而不是 Positive。

So what would be its Best Class Probability? Yes, it will be 0.89. 现在让我们看看代码：

```
var sentiment = "Experience is simply the name we give our mistakes";
/// Classify method returns ClassificationResult object with the best class probability and name.
var response = sentimentClassifier.Classify(sentiment);
Console.WriteLine($"Best Class Name: {response.BestClassName}");
Console.WriteLine($"Best Class Probability: { response.BestClassProbability}");
```
```
Best Class Name: **Negative**
Best Class Probability: **0.8882**
```

## 使用 C# 中的情感分析对多个评论进行分类

通常我们有成千上万的评论和反馈，那么我们如何分析客户的反馈呢？这很简单，只需将反馈放入一个数组中。让字符串数组作为审查的来源。它也可以是一个文件或来自数据库或服务的解析响应。我们可以将字符串数组转换为正情感概率的浮点数组。

```
var sentiments = new string\[\] {
                "Now that is out of the way, this thing is a beast. It is fast and runs cool.",
                "Experience is simply the name we give our mistakes",
                "When I used compressed air a cloud of dust bellowed out from the card (small scuffs and scratches).",
                "This is Pathetic."
            };
            var classifier = new GroupDocs.Classification.SentimentClassifier();
            var sentimentPositivity = sentiments.Select(x => classifier.PositiveProbability(x)).ToArray();
            Console.WriteLine(string.Join("\\n", sentimentPositivity));
```
```
**0.8959** - "Now that is out of the way, this thing is a beast..."
**0.1118** - "Experience is simply the name we give our mistakes"
**0.1252** - "When I used compressed air a cloud ..."
**0.0970** - "This is Pathetic."
```

我们可以用目标情绪做什么？我们可以测量目标产品、商店等的平均或中值积极性。选择最差的值并回应客户。我们还可以进行分析，例如发现产品的正概率值与其评级之间的不一致。

我们希望你觉得这篇文章有用。您可以从上述资源中找到有关 C# 中文本分类或情感分析的更多信息。

## 了解有关 GroupDocs.Classification API 的更多信息

* [文档][7]
* [源代码示例][8]
* [API 参考][9]

下载并运行 GitHub 示例是最好和最简单的入门方法。

## 也可以看看

* [使用 C# 对原始文本进行分类 –（IAB-2 和文档分类）][10]
* [使用 C# 对文档进行分类 –（IAB-2 和文档分类）][11]







[1]: https://products.groupdocs.com/classification
[2]: https://www.nuget.org/packages/GroupDocs.Classification
[3]: https://downloads.groupdocs.com/classification/net
[4]: https://apireference.groupdocs.com/classification/net/groupdocs.classification/classifier
[5]: https://apireference.groupdocs.com/classification/net/groupdocs.classification/sentimentclassifier
[6]: https://apireference.groupdocs.com/classification/net/groupdocs.classification/sentimentclassifier/methods/positiveprobability
[7]: https://docs.groupdocs.com/display/classificationnet/Home
[8]: https://github.com/groupdocs-classification/GroupDocs.Classification-for-.NET
[9]: https://apireference.groupdocs.com/classification/net
[10]: https://blog.groupdocs.com/2021/10/31/taxonomic-classification-of-text-using-csharp/
[11]: https://blog.groupdocs.com/2021/10/27/taxonomic-classification-of-documents-using-csharp/


