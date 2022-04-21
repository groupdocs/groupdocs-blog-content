---
title: "在 Java 中从发票和收据中提取数据"
date: Fri, 22 Jan 2021 16:48:00 +0000
draft: false
url: /zh/2021/01/22/extract-data-from-invoices-or-receipts-in-java/
aliases:
- /2021/01/22/extract-data-from-invoices-or-receipts-in-csharp-2/
author: 'Shoaib Khan'
summary: 'In the era of online businesses, the use of digital invoices and receipts has largely increased. Similarly, the efficient data extraction from these digital invoices is also demanding. In this article, you will be knowing **how to extract data from PDF invoices or receipts programmatically in Java**.

[继续阅读...][1]'
tags: ['data extraction from PDF invoices in Java', 'extract data from invoices in Java', 'extract data from PDF in Java', 'extract invoice data in Java']
categories: ['GroupDocs.Parser Product Family']
---

在在线业务时代，数字发票和收据的使用大大增加。同样，从这些数字发票中高效提取数据也是一项艰巨的任务。在本文中，您将了解**如何以 Java 编程方式从 PDF 发票或收据中提取数据**。之前我们在之前的一篇文章中看到了[使用 C# 提取发票数据][2]。



{{< figure align=center src="images/Extract-Data-from-Invoices-using-GroupDocs.jpg" alt="从 PDF 发票或收据中提取数据">}}


## 文档解析和数据提取 Java API

我将使用 [GroupDocs.Parser for Java][3] 来解析 PDF 发票并在 Java 应用程序中提取数据值。此 API 还允许从文档、图像、演示文稿、档案、电子邮件和许多其他 [支持的文档格式][4] 中提取文本、图像和元数据。

### 下载或配置

从 [下载部分][5]，您可以下载 **JAR** 文件，或者只获取 **基于 maven 的** Java 应用程序的 pox.xml 的存储库和依赖项配置。

## 如何在 Java 中提取 PDF 发票数据

以下步骤将允许您使用 Java 轻松地从 PDF 发票中提取数据。

* 创建一个模板。
* 根据创建的模板解析 PDF 发票。
* 从解析的 PDF 中提取信息。

### 为发票创建模板

下面是根据发票创建的模板。您还可以从 GitHub 存储库中的 [示例文件][6] 下载使用过的发票。

```
// 使用 Java 创建模板以从发票中解析数据
// 首先创建模板项
TemplateItem[] templateItems = new TemplateItem[]
{
    new TemplateField(new TemplateFixedPosition(new Rectangle(new Point(35, 135), new Size(100, 10))), "FromCompany"),
    new TemplateField(new TemplateFixedPosition(new Rectangle(new Point(35, 150), new Size(100, 35))), "FromAddress"),
    new TemplateField(new TemplateFixedPosition(new Rectangle(new Point(35, 190), new Size(150, 2))), "FromEmail"),
    new TemplateField(new TemplateFixedPosition(new Rectangle(new Point(35, 250), new Size(100, 2))), "ToCompany"),
    new TemplateField(new TemplateFixedPosition(new Rectangle(new Point(35, 260), new Size(100, 15))), "ToAddress"),
    new TemplateField(new TemplateFixedPosition(new Rectangle(new Point(35, 290), new Size(150, 2))), "ToEmail"),
    new TemplateField(new TemplateRegexPosition("Invoice Number"), "InvoiceNumber"),
    new TemplateField(new TemplateLinkedPosition(
            "InvoiceNumber",
            new Size(200, 15),
            new TemplateLinkedPositionEdges(false, false, true, false)),
            "InvoiceNumberValue"),
    new TemplateField(new TemplateRegexPosition("Order Number"), "InvoiceOrder"),
    new TemplateField(new TemplateLinkedPosition(
            "InvoiceOrder",
            new Size(200, 15),
            new TemplateLinkedPositionEdges(false, false, true, false)),
            "InvoiceOrderValue"),
    new TemplateField(new TemplateRegexPosition("Invoice Date"), "InvoiceDate"),
    new TemplateField(new TemplateLinkedPosition(
            "InvoiceDate",
            new Size(200, 15),
            new TemplateLinkedPositionEdges(false, false, true, false)),
            "InvoiceDateValue"),
    new TemplateField(new TemplateRegexPosition("Due Date"), "DueDate"),
    new TemplateField(new TemplateLinkedPosition(
            "DueDate",
            new Size(200, 15),
            new TemplateLinkedPositionEdges(false, false, true, false)),
            "DueDateValue"),
    new TemplateField(new TemplateRegexPosition("Total Due"), "TotalDue"),
    new TemplateField(new TemplateLinkedPosition(
            "TotalDue",
            new Size(200, 15),
            new TemplateLinkedPositionEdges(false, false, true, false)),
            "TotalDueValue")
};
// 转换为模板
Template template = new Template(Arrays.asList(templateItems));
```

### 解析 PDF 发票/收据以进行数据提取

以下几行将根据创建的模板解析 PDF 发票，并使用简单的 Java 代码提取发票数据。

```
// 使用 Java 中定义的模板解析 PDF 发票
Parser parser = new Parser("filePath/invoice.pdf");
DocumentData data = parser.parseByTemplate(template);
// 打印提取的数据
for (int i = 0; i < data.getCount(); i++) {
    // Printing Field Name
    System.out.print(data.get(i).getName() + ": ");
    // Cast PageArea property value to PageTextArea
    // as we have defined only text fields in the template
    PageTextArea area = data.get(i).getPageArea() instanceof PageTextArea
            ? (PageTextArea) data.get(i).getPageArea()
            : null;
    System.out.println(area == null ? "Not a template field" : area.getText());
}
```

＃＃＃ 输出

以下是上述代码从发票中提取数据后的输出。

```
**FROMCOMPANY:**    DEMO - Sliced Invoices
**FROMADDRESS:**    Suite 5A-1204
123 Somewhere Street
Your City AZ 12345
**FROMEMAIL:**     admin@slicedinvoices.com
**TOCOMPANY:**    Test Business
**TOADDRESS:**    123 Somewhere St
Melbourne, VIC 3000
**INVOICENUMBER:**             Invoice Number
**INVOICENUMBERVALUE:** NV-3337
**INVOICEORDER:**                Order Number
**INVOICEORDERVALUE:**    12345
**INVOICEDATE:**                    Invoice Date
**INVOICEDATEVALUE:**        January 25, 2016
**DUEDATE:**                           Due Date
**DUEDATEVALUE:**               January 31, 2016
**TOTALDUE:**                         Total Due
**TOTALDUEVALUE:**             $93.50
```

[GitHub 存储库][7] 中还有许多其他开源示例。您可以下载代码并快速运行示例。有关[使用模板在 Java 中进行解析和数据提取][8] 的更多指导和其他一些方法，请访问 [文档][9] 中的开发人员指南。如果有任何进一步的困难，请随时在 [论坛][10] 上免费联系支持团队。

## 也可以看看

* [有关使用模板在 Java 中解析 PDF 发票的更多信息][11]
* [用C#从发票或收据中提取数据][12]







[1]: https://blog.groupdocs.com/2021/01/22/extract-data-from-invoices-or-receipts-in-java/
[2]: https://blog.groupdocs.com/2019/10/24/extract-data-from-invoices-or-receipts-in-csharp/
[3]: https://products.groupdocs.com/parser/java
[4]: https://docs.groupdocs.com/parser/java/supported-document-formats/
[5]: https://downloads.groupdocs.com/parser/java
[6]: https://github.com/groupdocs-parser/GroupDocs.Parser-for-Java/tree/master/Examples/Resources/SampleFiles
[7]: https://github.com/groupdocs-parser/GroupDocs.Parser-for-Java
[8]: https://docs.groupdocs.com/parser/java/working-with-templates/
[9]: https://docs.groupdocs.com/parser/java/introducing-groupdocs-parser-for-java/
[10]: https://forum.groupdocs.com/c/parser
[11]: https://docs.groupdocs.com/parser/java/working-with-templates/
[12]: https://blog.groupdocs.com/2019/10/24/extract-data-from-invoices-or-receipts-in-csharp/


