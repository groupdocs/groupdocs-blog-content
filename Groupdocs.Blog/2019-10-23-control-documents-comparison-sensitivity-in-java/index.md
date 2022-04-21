---
title: 'Control documents comparison sensitivity in Java'
date: Wed, 23 Oct 2019 15:36:24 +0000
draft: false
url: /2019/10/23/control-documents-comparison-sensitivity-in-java/
author: 'Atir Tahir'
summary: ''
tags: ['comparison api', 'docscomparisonjava', 'document comparison', 'java']
categories: ['GroupDocs.Comparison Product Family']
---

Document comparison is one of the most common procedure that is practiced almost in all of the digital businesses. And the objective is same, highlight the inserted or deleted items. Detect the style changes and generate a summary. Let's see how GroupDocs.Comparison for Java can help us with this scenario. This is a back-end API that can be integrated in any Java application irrespective of the frameworks. Explore API [documentation](https://docs.groupdocs.com/display/comparisonjava/Getting+Started) to learn more about the supported features and file formats.

Those who are already using the API, we'll discuss new features and improvements introduced in version [19.10](https://docs.groupdocs.com/display/comparisonjava/GroupDocs.Comparison+for+Java+19.10+Release+Notes).  
How about controlling the document **comparison sensitivity**? We've added a sensitivity property in _ComparisonSettings_ class. This option defines limit in percents, when an element is detected as deleted or inserted.

**Minimal value**  
Minimal value is 0, comparison process does not occur for any length of sequences of two compared objects.

**Value by default**  
The default percentage is 75, comparison occurs when the percentage of deleted or inserted elements in relation to all elements does not exceed 75%.

**Maximum value**  
That is 100%. Comparison occurs at any length of a common sub-sequence of two compared objects.

Now let’s understand this with a use-case. Suppose we have two words:

1.  oneSource
2.  twoTarget

These two words have very small common sub-sequence. Therefore, when comparing them at 75% accuracy, it is not taken into account and we get a completely removed and inserted word as follows:  

```
(twoTarget)\[oneSource\]
```

But at 100% accuracy, this sub-sequence will be treated or represented in a different way, despite the fact that it consists of two letters.  

```
(tw)o\[n\](Targ)e\[Source\](t)
```

Isn’t it amazing? You can now get briefed comparison results by just controlling the sensitivity.  
{{< gist GroupDocsGists cd67c532bcd45f1b3529d93c0ed862d9 "comparisonsensitiviy.java" >}}

Did you ever think of getting _coordinates _of document changes or differences? It could be confusing at first but let me elaborate this. In your output or resultant document, you get every detail of inserted, deleted or style changed items. The new thing is that you can get coordinate details where changes or differences actually occurred. Currently this feature is supported for only Word, PDF, Slide and Diagram formats.

*   

{{< figure align=center src="images/coordinates-1024x286.png" alt="">}}

    

{{< gist GroupDocsGists 3855a6c7c8b983c47c12ad5e24d7068c "comparisoncoordinates.java" >}}

You can get the API from download [section](https://downloads.groupdocs.com/conversion/java). We also have an open-source GitHub example [project](https://github.com/groupdocs-conversion/GroupDocs.Conversion-for-Java). However, if you face any issue while evaluating the API, you can post it on [forum](https://forum.groupdocs.com/c/conversion).




