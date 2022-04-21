---
title: "使用 Java 差异库比较文本、Word 和 PDF 文件"
date: Wed, 15 Jul 2020 15:23:31 +0000
draft: false
url: /zh/2020/07/15/compare-text-word-pdf-files-with-java-difference-library/
aliases:
- /2020/07/15/comparing-text-word-pdf-files-with-java-difference-library/
author: 'Shoaib Khan'
summary: "通过本文，我们将能够比较文本文件、Word 文件、PDF 文件和其他基于 Java 的应用程序中的文档。通过使用此功能，我们可以比较发票、合同、演示文稿、AutoCAD 设计、价目表或编程文件。我们还将有幸突出显示已识别的更改，并可以选择接受或拒绝任何更改。我们甚至可以使用 Java 的文档比较 API 构建我们自己的 [文档比较工具][1]，类似于 GroupDocs 推出的工具。"
tags: ['compare PDF files in Java', 'compare two files using java', 'compare Word files in java']
categories: ['GroupDocs.Comparison Product Family']
---

通过本文，我们将能够比较文本文件、Word 文件、PDF 文件和其他基于 Java 的应用程序中的文档。通过使用此功能，我们可以比较发票、合同、演示文稿、AutoCAD 设计、价目表或编程文件。我们还将有幸突出显示已识别的更改，并可以选择接受或拒绝任何更改。我们甚至可以使用 Java 的文档比较 API 构建我们自己的 [文档比较工具][2]，类似于 GroupDocs 推出的工具。

下面，您将了解以下主题：

* [比较 Word 文件并显示差异][3]。
* [使用流比较 Word 文件][4]。
* [接受或拒绝 Word 文件中已识别的更改][5]。
* [比较文本文件并突出显示差异][6]。
* [使用 Java 比较 PDF 文件][7]。

## Java 文档比较 API

作为先决条件，您可以从 [下载][9] 部分获得 [GroupDocs.Comparison for Java][8]。此外，对于基于 maven 的应用程序，您可以在 pom.xml 中添加以下内容：

### 存储库```
<repository>
<id>GroupDocsJavaAPI</id>
<name>GroupDocs Java API</name>
<url>http://repository.groupdocs.com/repo/</url>
</repository>
```

### Dependency```
<dependency>
        <groupId>com.groupdocs</groupId>
        <artifactId>groupdocs-comparison</artifactId>
        <version>20.4</version> 
</dependency>
```

## 使用 Java 比较 Word 文件并显示差异 {#compare-word-files}

下面的步骤将向您展示只需几行 Java 代码即可比较任意两个 Word 文档。因此，您将获得将突出显示已识别更改的结果文档。

* 使用源文档路径初始化 **[Comparer][10]** 对象。
* 使用 **[add][11]** 方法添加要比较的第二个文档。
* 调用**[compare][12]** 方法获取比较结果。 compare 方法将输出文档的名称作为参数。

```
// Compare two Word files from the provided location on disk
Comparer comparer = new Comparer("source.docx");
try {
    comparer.add("target.docx");
    comparer.compare("comparison.docx");
}
finally {
    comparer.dispose();
}
```

在这里，我显示了上述代码生成的 Word 文档，其中包含比较的两个 Word 文档的突出显示差异。删除的内容会被标记为红色，添加的内容会显示为蓝色，但是，绿色显示修改的内容。



{{< figure align=center src="images/word-files-text-comparison-using-java.png" alt="word-file-text-comparison-and-show-dirffer">}}


## 使用 Stream 比较文本的 Word 文件 {#compare-word-files-using-stream}

您可以类似地将文档作为流传递给 Comparer 类，以将其与第二个文档进行比较。这是Java代码，可让您清楚地了解：

```
// Compare two Word file using Stream
Comparer comparer = new Comparer(new FileInputStream("source.docx"));
try {
    comparer.add(new FileInputStream("target.docx"));
    comparer.compare(new FileOutputStream("result.docx"));
} 
finally {
    comparer.dispose();
}
```

## 使用 Java 接受或拒绝 Word 文件中的比较更改 {#accept-or-reject-changes}

成功突出显示已识别的差异后，您可以选择接受或拒绝任何更改。只是作为一个例子，我交替接受和拒绝更改。您可以使用类似的代码一一显示每个更改，并根据您的要求决定接受/拒绝每个更改。

```
// Accept or Reject the identified changes of Word document in Java
Comparer comparer = new Comparer(source);
try {
    comparer.add(target);
    comparer.compare();
    ChangeInfo\[\] changes = comparer.getChanges();
    System.out.println("changes.length: " + changes.length + ".");
    // Accept or Reject the changes
    for (int n = 0; n < changes.length; n++) {
    	if (n % 2 == 0) {
    		changes\[n\].setComparisonAction(ComparisonAction.ACCEPT);
    	}
    	else {
    		changes\[n\].setComparisonAction(ComparisonAction.REJECT);
    	}
    }
    // Apply your decisions to get the resultant document.
    comparer.applyChanges(outputFileName, new SaveOptions(), new ApplyChangeOptions(changes));
}
finally {
    comparer.dispose();
}
```

## 使用 Java 比较文本文件并显示差异 {#compare-text-files-in-java}

使用 Comparer 类，我们还可以比较任何文本文件。下面是在 Java 中比较两个文本文件的类似代码。步骤与比较任何其他两个文档完全相同：

* 首先将文本文件传递给 [Comparer][13] 类。
* 使用 [add][14] 方法添加第二个文件。
* 调用[比较][15]方法。

```
// Compare two text files to identify and highlight changes.
Comparer comparer = new Comparer("source.txt");
try {
    comparer.add("target.txt");
    comparer.compare("comparison.txt");
}
finally {
    comparer.dispose();
}
```

这是显示使用上述代码匹配两个文本文件的比较结果的输出文档。



{{< figure align=center src="images/text-files-comparison-using-java.png" alt="使用 Java 比较文本文件">}}


## 使用 Java 比较 PDF 文件的文本差异 {#compare-pdf-files-in-java}

我们可以使用上面相同的代码比较 PDF 文件，只需将文件扩展名更改为“.pdf”。顺便提一下，下面的代码比较了两个 pdf 文件并显示了 Java 中的差异。

```
// Compare two PDF file using Stream
Comparer comparer = new Comparer(new FileInputStream("source.pdf"));
comparer.add(new FileInputStream("target.pdf"));
comparer.compare(new FileOutputStream("result.pdf"));
```

以下是比较 PDF 文件后的结果。



{{< figure align=center src="images/pdf-files-text-comparison-using-java.png" alt="PDF 文件文本比较">}}


## 也可以看看

* [用于比较文本文件的 C# Diff 库][16]
* [在 C# 中比较两个或多个文件][17]

许多其他开源示例可在 [GitHub 存储库][18] 上公开获得。您可以使用 [入门][19] 指南下载并快速运行示例。如有任何疑问，请查看文档或随时在 [论坛][20] 上与我们联系。







[1]: https://products.groupdocs.app/comparison/total
[2]: https://products.groupdocs.app/comparison/total
[3]: https://blog.groupdocs.com/2020/07/15/compare-text-word-pdf-files-with-java-difference-library/#compare-word-files
[4]: https://blog.groupdocs.com/2020/07/15/compare-text-word-pdf-files-with-java-difference-library/#compare-word-files-using-stream
[5]: https://blog.groupdocs.com/2020/07/15/compare-text-word-pdf-files-with-java-difference-library/#accept-or-reject-changes
[6]: https://blog.groupdocs.com/2020/07/15/compare-text-word-pdf-files-with-java-difference-library/#compare-text-files-in-java
[7]: https://blog.groupdocs.com/2020/07/15/compare-text-word-pdf-files-with-java-difference-library/#compare-pdf-files-in-java
[8]: https://products.groupdocs.com/comparison/java
[9]: https://downloads.groupdocs.com/comparison/java
[10]: https://apireference.groupdocs.com/comparison/java/com.groupdocs.comparison/Comparer
[11]: https://apireference.groupdocs.com/comparison/java/com.groupdocs.comparison/Comparer#add(java.lang.String)
[12]: https://apireference.groupdocs.com/comparison/java/com.groupdocs.comparison/Comparer#compare(java.lang.String)
[13]: https://apireference.groupdocs.com/comparison/java/com.groupdocs.comparison/Comparer
[14]: https://apireference.groupdocs.com/comparison/java/com.groupdocs.comparison/Comparer#add(java.lang.String)
[15]: https://apireference.groupdocs.com/comparison/java/com.groupdocs.comparison/Comparer#compare(java.lang.String)
[16]: https://blog.groupdocs.com/2020/04/30/groupdocs-comparison-for-net-c-sharp-diff-library-for-comparing-text-files/
[17]: https://blog.groupdocs.com/2020/03/10/compare-excel-word-pdf-files-in-csharp/
[18]: https://github.com/groupdocs-comparison/GroupDocs.Comparison-for-Java
[19]: https://docs.groupdocs.com/comparison/java/getting-started/
[20]: https://forum.groupdocs.com/c/conversion


