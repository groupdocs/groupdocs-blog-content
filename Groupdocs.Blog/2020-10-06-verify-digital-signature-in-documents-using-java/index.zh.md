---
title: "使用 Java 验证文档中的数字签名"
date: Tue, 06 Oct 2020 11:24:19 +0000
draft: false
url: /zh/2020/10/06/verify-digital-signature-in-documents-using-java/
author: 'Shoaib Khan'
summary: "在本文中，我们将学习**使用 Java 以编程方式验证数字签名文档**。该示例使用 PDF 文档进行验证，但是，您也可以对 MS Word **DOC/DOCX**、Excel 电子表格 **XLS/XLSX** 和演示文稿**PPT/PPTX 等数字签名的文字处理文档进行验证**。"
tags: ['verify digital signatures in java', 'verify digitally signed documents in java']
categories: ['GroupDocs.Signature Product Family']
---

基于证书的数字签名是一种电子签名类型，可为签名者的身份提供最高级别的保证并遵守严格的规定。在本文中，我们将学习**使用 Java 以编程方式验证数字签名文档**。在 [较早的帖子][1] 之一中，我们讨论了使用 C# 验证文档中的数字签名。

## 用于签名验证的 Java API



{{< figure align=center src="images/groupdocs-signature-java.png" alt="GroupDocs.Signature 用于使用 Java 签署文档">}}


本文使用 GroupDocs 的 Java 文档签名 API。 [GroupDocs.Signatures for Java][2] 支持以下类型的电子签名：

* 条码签名
* 表单域签名
*图像签名
* 元数据签名
* 二维码签名
* 邮票签名
*文字签名

因此，最好通过从 [下载部分][3] 下载库或在基于 Maven 的应用程序中设置上述配置来预先准备工作区。

## 使用 Java 验证数字签名 PDF 文档的步骤

按照这些步骤，您可以验证数字签名的文档。在此示例中，我使用了 **PDF** 文档进行验证，但是，相同的步骤也适用于 **MS Word** 文档、**Excel** 电子表格和 **Powerpoint** 演示文稿。

1. 使用源文档实例化 [Signature][4] 对象。
2. 实例化 [DigitalVerifyOptions][5] 类对象并指定验证选项。
3. 调用 Signature 的 [verify][6] 方法并通过指定的验证选项。

下面是显示上述过程的完整示例源代码。 Java 代码在这里验证数字签名的 PDF 文档。您还可以验证数字签名的文字处理文档，例如 MS Word **DOC/DOCX**、Excel 电子表格 **XLS/XLSX** 和演示文稿**PPT/PPTX**。

```
// GroupDocs 使用 Signature API for Java 验证 PDF 文档中的数字签名
Signature signature = new Signature("sample_signed.pdf");

DigitalVerifyOptions options = new DigitalVerifyOptions("certificate.pfx");
options.setComments("Test comment");
options.setPassword("1234567890");

// 验证文件签名
VerificationResult result = signature.verify(options);
if (result.isValid()) {
    System.out.println("Document Verified Successfully !");
}
else {
    System.out.println("Document Verification Failed.");
}
```

## 结论

今天，我们学习了使用 Java 验证数字签名的 MS Word、Excel、PowerPoint 和 PDF 文档。您可以使用 [文档文章][7] 探索有关 **GroupDocs.Signature for Java** 功能的更多信息。

## 也可以看看

* [使用 C# 验证文档中的数字签名][8]







[1]: https://blog.groupdocs.com/2019/09/25/verify-digital-signature-in-documents-using-csharp/
[2]: https://products.groupdocs.com/signature/java
[3]: https://downloads.groupdocs.com/signature/java
[4]: https://apireference.groupdocs.com/signature/java/com.groupdocs.signature/Signature
[5]: https://apireference.groupdocs.com/signature/java/com.groupdocs.signature.options.verify/DigitalVerifyOptions
[6]: https://apireference.groupdocs.com/signature/java/com.groupdocs.signature/Signature#verify(com.groupdocs.signature.options.verify.VerifyOptions)
[7]: https://docs.groupdocs.com/signature/java
[8]: https://blog.groupdocs.com/2019/09/25/verify-digital-signature-in-documents-using-csharp/


