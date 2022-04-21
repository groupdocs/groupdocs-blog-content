---
title: 'Control Documents Comparison Sensitivity'
date: Mon, 15 Jul 2019 10:53:40 +0000
draft: false
url: /2019/07/15/control-documents-comparison-sensitivity/
author: 'Atir Tahir'
summary: ''
tags: []
categories: ['GroupDocs.Comparison for .NET', 'GroupDocs.Comparison Product Family']
---

Integrate GroupDocs.Comparison for .NET [19.6](https://docs.groupdocs.com/display/comparisonnet/GroupDocs.Comparison+for+.NET+19.6+Release+Notes) in your project and take control of documents comparison sensitivity. Detecting source and target documents style changes or inserted/deleted items and then highlighting them in the resultant file is a common yet major feature.

But we have something new, something enormous for you. You can now get detailed comparison of the documents. In _ComparisonSettings_ class we added _SensitivityOfComparison_ method using that you can set sensitivity of documents comparison. Let's see its implementation and then details.  
{{< gist GroupDocsGists dcc64567f38401b46fbe32be1de68ba2 "comparisonsenitivity.cs" >}}

This option defines limit in percentage, when element is detected as deleted or inserted. There are three values/percentages.  

**Minimal value**  
Minimal value is 0, comparison process does not occur for any length of sequences of two compared objects.

**Value by default**  
The default percentage is 75, comparison occurs when the percentage of deleted or inserted elements in relation to all elements does not exceed 75%.

**Maximum value**  
That is 100%. Comparison occurs at any length of a common sub-sequence of two compared objects.

Now let's understand this with a use-case. Suppose we have two words:

1.  oneSource
2.  twoTarget

These two words have very small common sub-sequence. Therefore, when comparing them at 75% accuracy, it is not taken into account and we get a completely removed and inserted word as follows:  

```
(twoTarget)[oneSource]
```

But at 100% accuracy, this sub-sequence will be treated or represented in a different way, despite the fact that it consists of two letters.  

```
(tw)o[n](Targ)e[Source](t)
```

Isn't it amazing? You can now get briefed comparison results by just controlling the sensitivity.

Let's see the major issues that are now resolved in this release:

*   Duplicate Images in Result file in PDF
*   PDF comparison has overlapping and mangled output
*   Text got overlapped with other text or images
*   Merged Documents and then comparing them fails

You must give a try to GroupDocs.Comparison for .NET API and share your feedback and concerns on [forum](https://forum.groupdocs.com/c/comparison). Download latest version of the API [here](https://downloads.groupdocs.com/comparison/net).




