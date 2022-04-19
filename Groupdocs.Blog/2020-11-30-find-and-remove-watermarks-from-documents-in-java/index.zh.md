---
title: "在 Java 中查找和删除文档中的水印"
date: Mon, 30 Nov 2020 10:55:51 +0000
draft: false
url: /zh/2020/11/30/find-and-remove-watermarks-from-documents-in-java/
aliases:
- /2019/10/10/find-and-remove-watermarks-from-documents-in-java/
author: 'Shoaib Khan'
summary: "本文对于正在寻找一种方法来从 **PDF、Word、Excel、PowerPoint 和 **Visio **查找和删除文本**或 **图像水印**的 **Java** 开发人员很有用** 文件。在我们的一篇文章中，我们学习了[在 C# 中从文档中查找和删除水印][1]。现在让我们快速了解一下允许以不同方式从各种文档中添加、查找和删除水印的 Java API。"
tags: ['find and remove watermarks in Java', 'find watermarks in Java', 'remove watermarks using Java', 'watermarking API for Java']
categories: ['GroupDocs.Watermark Product Family']
---

本文对于正在寻找一种方法来从 **PDF、Word、Excel、PowerPoint 和 **Visio **查找和删除文本**或 **图像水印**的 **Java** 开发人员很有用** 文件。在我们的一篇文章中，我们学习了[在 C# 中查找和删除文档中的水印][2]。现在让我们快速了解一下允许以不同方式从各种文档中添加、查找和删除水印的 Java API。

## 用于水印和删除的 Java API

**[GroupDocs.Watermark for Java][3]** API 支持向各种文档格式添加文本和图像水印。此外，它还具有从文档中查找和去除水印的能力。 API 还查找使用第三方工具添加的水印对象。因此，让我演示如何在 Java 中通过几个步骤从文档中删除水印。

您可以从 [downloads][4] 部分获取 JAR，或者在基于 Maven 的 Java 应用程序的 pom.xml 中添加以下配置。有关 API 详细信息，请访问 [API 参考][5]。

```
<repository>
	<id>GroupDocsJavaAPI</id>
	<name>GroupDocs Java API</name>
	<url>http://repository.groupdocs.com/repo/</url>
</repository>
```
```
<dependency>
        <groupId>com.groupdocs</groupId>
        <artifactId>groupdocs-watermark</artifactId>
        <version>20.5</version> 
</dependency>
```

## 从 Java 文档中删除水印的步骤

在我们开始之前，请查看以下包含文本水印和图像水印的 PDF 文档。我们将使用此文档并从中删除水印。



{{< figure align=center src="images/watermarkedpdf.png" alt="带水印的 PDF 文件 - GroupDocs">}}


**1.** 创建一个新项目。

**2.** 添加以下导入。

```
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.search.ImageDctHashSearchCriteria;
import com.groupdocs.watermark.search.ImageSearchCriteria;
import com.groupdocs.watermark.search.PossibleWatermarkCollection;
import com.groupdocs.watermark.search.SearchCriteria;
import com.groupdocs.watermark.search.TextSearchCriteria;
```

**3\.** 创建 **Watermarker** 类的实例并加载源文档。

```
Watermarker watermarker = new Watermarker("filepath/watermarked.pdf");
```

**4.** 使用 **search** 方法根据配置的搜索条件查找水印。

```
// 配置图片水印的搜索条件
ImageSearchCriteria imageSearchCriteria = new ImageDctHashSearchCriteria("filepath/watermark.png");
imageSearchCriteria.setMaxDifference(0.2); // Set how much the watermark can differ from the provided image.

// 配置文本水印的搜索条件
TextSearchCriteria textSearchCriteria = new TextSearchCriteria("CONFIDENTIAL");

// 结合文本和图像搜索条件
SearchCriteria combinedSearchCriteria = imageSearchCriteria.or(textSearchCriteria);
PossibleWatermarkCollection possibleWatermarks = watermarker.search(combinedSearchCriteria);
```

**5.** 遍历水印集合并使用 **removeAt** 方法删除水印。

```
//遍历可能的水印收集、检查和去除水印
while(possibleWatermarks.getCount()>0)
{
	if (possibleWatermarks.get_Item(0).getImageData() != null)
	{
		possibleWatermarks.removeAt(0);
		System.out.println("Removed Image Watermark.");
	}
	else
	{
		possibleWatermarks.removeAt(0);
		System.out.println("Removed Text Watermark.");
	}
} 
```

**6\.** 使用 **save** 方法保存生成的文档。

```
 watermarker.save("filepath/without_watermark.pdf");
 watermarker.close(); 
```

还有一些**其他方法可以使用不同的方法从文档中查找和删除水印**。如果您想删除文档的所有水印，或者想摆脱各种选择性水印：

*您可以收集所有可能的水印。
* 遍历水印集合或直接使用索引访问水印。
* 如果需要，检查水印类型和数据。
*删除它，如果它符合您的要求。

**remove**、**removeAt** 和 **clear** 是可用于相应去除水印的方法。有关更多详细信息，您可以访问有关[在 Java 中搜索和修改水印][6] 的**文档**文章。

### 完整代码

```
// 在 Java 中从 PDF、Word、Excel、PowerPoint 和 Visio 文档中查找和删除水印
Watermarker watermarker = new Watermarker("filepath/watermarked.pdf"); // Provide any supported document

// 配置图片水印的搜索条件
ImageSearchCriteria imageSearchCriteria = new ImageDctHashSearchCriteria("filepath/watermark.png");
imageSearchCriteria.setMaxDifference(0.2); // Set how much the watermark can differ from the provided image.

// 配置文本水印的搜索条件
TextSearchCriteria textSearchCriteria = new TextSearchCriteria("CONFIDENTIAL");

// 结合文本和图像搜索条件
SearchCriteria combinedSearchCriteria = imageSearchCriteria.or(textSearchCriteria);
PossibleWatermarkCollection possibleWatermarks = watermarker.search(combinedSearchCriteria);

//遍历可能的水印收集、检查和去除水印
while(possibleWatermarks.getCount()>0)
{
	if (possibleWatermarks.get_Item(0).getImageData() != null)
	{
		possibleWatermarks.removeAt(0);
		System.out.println("Removed Image Watermark.");
	}
	else
	{
		possibleWatermarks.removeAt(0);
		System.out.println("Removed Text Watermark.");
	}
} 
watermarker.save("filepath/without_watermark.pdf");
watermarker.close(); 
```

＃＃＃ 结果

以下是我们去除水印后得到的 PDF 文档的截图。



{{< figure align=center src="images/withoutwatermarkpdf.png" alt="使用 GroupDocs 的 Watermarking Java API 去除水印后生成的 PDF 文件">}}


## 结论

我相信，作为一名 Java 开发人员，您将不再犹豫从 Microsoft 和 OpenOffice 支持的**文字处理文档**、**电子表格**、**演示文稿**、 **PDF** 文档和 **Visio** 绘图。

您可以从 [文档][7] 中探索更多关于 API 的信息。如有任何疑问，请联系我们@[论坛][8]。

## 也可以看看

* [在Java中为图像添加水印][9]
* [在 C# 中查找和删除文档中的水印][10]
* [使用C#为图像或文档中的图像添加水印][11]







[1]: https://blog.groupdocs.com/2020/11/27/find-and-remove-watermarks-from-documents-in-csharp/
[2]: https://blog.groupdocs.com/2020/11/27/find-and-remove-watermarks-from-documents-in-csharp/
[3]: https://products.groupdocs.com/watermark/java
[4]: https://downloads.groupdocs.com/watermark/java
[5]: https://apireference.groupdocs.com/watermark/java
[6]: https://docs.groupdocs.com/watermark/java/searching-and-modifying-watermarks/
[7]: https://docs.groupdocs.com/watermark/java/
[8]: https://forum.groupdocs.com/c/watermark
[9]: https://blog.groupdocs.com/2020/09/15/add-watermark-to-images-in-java/
[10]: https://blog.groupdocs.com/2020/11/27/find-and-remove-watermarks-from-documents-in-csharp/
[11]: https://blog.groupdocs.com/2019/10/21/add-watermark-to-images-using-csharp-dotnet-api/


