---
title: "使用 C# 编辑 XML 文件"
date: Tue, 02 Nov 2021 13:18:00 +0000
draft: false
url: /zh/2021/11/02/edit-xml-files-using-csharp/
author: 'Shoaib Khan'
summary: "XML 是 W3C 推荐的结构化格式之一，通常用于存储和传输数据。开发人员非常需要使用应用程序编辑存储的 XML 数据。为方便编辑需求，本文介绍了**如何使用C#编辑XML文件数据**。"
tags: ['Edit XML File using C#', 'Edit XML in CSharp', 'How to Edit XML']
categories: ['GroupDocs.Editor Product Family']
---

XML 是 W3C 推荐的结构化格式之一，通常用于存储和传输数据。开发人员非常需要使用应用程序编辑存储的 XML 数据。为方便编辑需求，本文介绍了**如何使用C#编辑XML文件数据**。

* [XML 编辑 .NET API][1]
* [如何使用 C# 编辑 XML 文件][2]

## .NET API 来编辑 XML 文件 {#xml-edit-dotnet-api}

[GroupDocs.Editor][3] 提供文档编辑解决方案和 API 来[编辑大量不同文件格式][4]。它是可与外部编辑器一起用于可视化编辑的 .NET API。在本文中，我们将使用 GroupDocs.Editor for .NET 在 .NET 应用程序中编辑 XML 数据。

要下载 **DLLs** 或 **MSI** 安装程序，请访问 [下载部分][5] 或通过 [NuGet][6] 在您的 .NET 应用程序中安装 API。

```
PM> Install-Package GroupDocs.Editor
```

## 如何使用 C# 编辑 XML 文件 {#how-to-edit-xml}

直奔目标，我们将通过用另一个值替换一个值来修改 XML 数据。以下是使用 C# 编辑或更新 XML 文件的步骤。

* 使用 [Editor][7] 类加载 XML 数据文件。
* 使用 [XmlEditOptions][8] 类准备 XML 编辑选项。
* 对于编辑，使用 [Edit][10] 方法和准备好的编辑选项创建 [EditableDocument][9] 作为源内容。
* 从 **EditableDocument** 中，使用 [GetContent][11] 方法获取 XML 文件的原始内容。
* 更新 XML 内容中的值。
* 现在使用 [FromMarkup][12] 方法从更新的 XML 内容创建一个新的 **EditableDocument**。
* 为了以不同的格式保存更新的内容，请准备相关的保存选项，如 [WordProcessingSaveOptions][13] 或 [TextSaveOptions][14]。
* 使用 [Save][15] 方法以任何格式保存更新的 XML 数据。

以下 C# 代码片段显示了如何编辑 XML 文件和更新数据，然后以任何其他格式保存它。

```
// 通过使用 C# 更新值来编辑 XML 文件
using (Editor editor = new Editor("path/data.xml"))
{
    // Create XML editing options
    Options.XmlEditOptions editOptions = new XmlEditOptions();
    editOptions.AttributeValuesQuoteType = QuoteType.DoubleQuote;
    editOptions.RecognizeEmails = true;
    editOptions.RecognizeUris = true;
    editOptions.TrimTrailingWhitespaces = true;

    // EditableDocument Settings
    using (EditableDocument beforeEdit = editor.Edit(editOptions))
    {
        // Edit whatever
        string originalTextContent = beforeEdit.GetContent();
        string updatedTextContent = originalTextContent.Replace("John", "Samuel");

        List<IHtmlResource> allResources = beforeEdit.AllResources;

        // Create EditableDocument with updated content
        using (EditableDocument afterEdit = EditableDocument.FromMarkup(updatedTextContent, allResources))
        {
            // Create WordProcessing save options
            Options.WordProcessingSaveOptions wordSaveOptions = new WordProcessingSaveOptions(WordProcessingFormats.Docx);
                        
            // Create TXT save options
            Options.TextSaveOptions txtSaveOptions = new TextSaveOptions();
            txtSaveOptions.Encoding = System.Text.Encoding.UTF8;

            // Save edited XML data in DOCX and TXT format
            editor.Save(afterEdit, "path/xmlData.docx", wordSaveOptions);
            editor.Save(afterEdit, "path/xmlData.txt", txtSaveOptions);
        }
    }
}
```

## 获得免费许可证

您可以[获得免费的临时许可证][16] 以便在没有评估限制的情况下使用 API。

## 结论

综上所述，我们已经学会了使用 C# 以编程方式编辑 XML 文件数据。您可以使用 [文档][17] 进一步探索 GroupDocs.Editor 的其他功能。要澄清任何歧义，请在 [论坛][18] 上与我们联系。

## 也可以看看

* [用Java编辑XML文件][19]
* [如何用C#编辑Word文档][20]



[1]: #xml-edit-dotnet-api
[2]: #how-to-edit-xml
[3]: https://products.groupdocs.com/editor/
[4]: https://docs.groupdocs.com/editor/net/supported-document-formats/
[5]: https://downloads.groupdocs.com/editor
[6]: https://www.nuget.org/packages/groupdocs.editor
[7]: https://apireference.groupdocs.com/editor/net/groupdocs.editor/editor
[8]: https://apireference.groupdocs.com/editor/net/groupdocs.editor.options/xmleditoptions
[9]: https://apireference.groupdocs.com/editor/net/groupdocs.editor/editabledocument
[10]: https://apireference.groupdocs.com/editor/net/groupdocs.editor/editor/methods/edit/index
[11]: https://apireference.groupdocs.com/editor/net/groupdocs.editor/editabledocument/methods/getcontent/index
[12]: https://apireference.groupdocs.com/editor/net/groupdocs.editor/editabledocument/methods/frommarkup
[13]: https://apireference.groupdocs.com/editor/net/groupdocs.editor.options/wordprocessingsaveoptions
[14]: https://apireference.groupdocs.com/editor/net/groupdocs.editor.options/textsaveoptions
[15]: https://apireference.groupdocs.com/editor/net/groupdocs.editor/editor/methods/save/index
[16]: https://purchase.groupdocs.com/temporary-license
[17]: https://docs.groupdocs.com/editor/net/
[18]: https://forum.groupdocs.com/c/assembly
[19]: https://blog.groupdocs.com/2021/11/06/edit-xml-files-in-java/
[20]: https://blog.groupdocs.com/2021/03/26/edit-word-documents-in-csharp/