---
title: 'Classify your Customer Feedback using Sentiment Analysis in C#'
date: Wed, 17 Jun 2020 08:28:00 +0000
draft: false
url: /2020/06/17/classify-customers-feedback-using-sentiment-analysis-in-csharp/
author: 'Shoaib Khan'
summary: 'Suppose that you have the opportunity to receive comments or reviews from your customers or some other source and you want to evaluate how positive they are. There is a way to analyze such comments called **sentiment analysis**. This post focuses on the sentiment analysis tool based on a deep neural network model using C#. This model is suitable for a wide range of tasks.'
tags: ['csharp code for sentiment analysis', 'csharp sentiment analysis', 'sentiment analysis csharp', 'sentiment analysis in csharp', 'sentiment classification in csharp']
categories: ['GroupDocs.Classification Product Family']
---

Suppose that you have the opportunity to receive comments or reviews from your customers or some other source and you want to evaluate how positive they are. There is a way to analyze such comments called **sentiment analysis**. This post focuses on the sentiment analysis tool based on a deep neural network model using C#. This model is suitable for a wide range of tasks.

## Sentiment Analysis API for .NET

If you want to do sentiment analysis programmatically, [GroupDocs.Classification][1] serves that purpose for you. It implements a general-purpose sentiment classifier that can be used to evaluate the tone of product reviews, shop reviews, application reviews, feedbacks, etc.



{{< figure align=center src="images/groupdocs_classification-for-net.png" alt="GroupDocs.Classification for .NET">}}


This article will guide you to the classification of comments and analyze the positivity using C# with **GroupDocs.Classification for .NET**. So before you start, please make sure to install the API from any of the following methods:

*   Install using [NuGet][2] Package Manager.
*   [Download][3] the DLL and reference it into the project.

## How to Classify Text using Sentiment Analysis in C#

To solve such a task we can use a general class named [Classifier][4], or we can use the Sentiment Classifier which is a bit simpler and more lightweight class. Here are the steps:

*   Initialize the [SentimentClassifier][5].
*   Call the [PositiveProbability][6] method of SentimentClassifier class and pass the text as a parameter that needs to be analyzed.
*   The PositiveProbability method will return the positivity ranging from 0 to 1.

Here is the C# code to find the tone of any statement using the sentiment classification. We have chosen the following sentiment as an example:

_"Experience is simply the name we give our mistakes"_

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

Any value greater than 0.5 means the sentiment is positive and the range between 0 and 0.5 shows that it is negative.

Now according to the extracted positivity, you may get the **Best Class** for that sentiment and probability of that Best Class. We found that its positive probability is 0.11, so it should be classified as a **negative** comment and its Best Class should be **Negative** instead of Positive.

So what would be its Best Class Probability? Yes, it will be 0.89. Now let see in the code:

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

## Classify Multiple Comments using Sentiment Analysis in C#

Normally we have thousands of comments and feedback, so how could we analyze our customer's feedback? It is simple, just put the feedbacks in an array. Let the string array be the source of review. It also could be a file or the parsed response from a database or service. We can transform the string array to the float array of positive sentiment probabilities.

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

What can we do with target sentiments? We can measure mean or median positiveness for the target product, shop, etc. Select the worst values and respond to the customers. We can also do analysis like finding inconsistencies between the positive probability value of a product and its rating.

We hope you find this post useful. You can find more on text classification or sentiment analysis in C# from the mentioned resources.

## Learn more about GroupDocs.Classification API

*   [Documentation][7]
*   [Source Code Examples][8]
*   [API Reference][9]

Downloading and running GitHub examples is the best and easiest way to get started.

## See Also

*   [Classify Raw Text using C# – (IAB-2 & Document Taxonomy)][10]
*   [Classify Documents using C# – (IAB-2 & Document Taxonomy)][11]







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

