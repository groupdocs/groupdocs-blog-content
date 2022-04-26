---
title: "在 C# 中编辑 Word 文档"
date: Fri, 26 Mar 2021 09:42:00 +0000
draft: false
url: /zh/2021/03/26/edit-word-documents-in-csharp/
author: 'Shoaib Khan'
summary: 'The most common and widely used word-processing file formats that are supported by Microsoft Word and OpenOffice Writer are DOC, DOCX, and ODT. We normally use these formats for drafting the documents. Therefore, as a developer, we widely need to edit Word documents in our applications programmatically. In this article, we will discuss how to edit Word documents in C# using the .NET API for document editing.

以下是本文简要讨论的主题：

* Word 文档编辑和自动化
* 在 C# 中编辑 Word 文档

[继续阅读...][1]'
tags: ['Edit DOCX in CSharp', 'Edit in CSharp', 'Edit Word doc in CSharp', 'Word Editing .NET API']
categories: ['GroupDocs.Editor Product Family']
---

最常见和广泛使用的文字处理文件格式是 **DOC**、**DOCX** 和 **ODT**。著名的 Microsoft Word 和 OpenOffice Writer 支持这些格式，我们通常使用这些格式来起草文档。因此，作为开发人员，我们广泛需要在我们的应用程序中以编程方式编辑 Word 文档。在本文中，我们将讨论**如何使用 C# 编辑 Word 文档，使用 .NET API 进行文档编辑。

以下是本文简要讨论的主题：

* [.NET API - Word 文档编辑][2]
* [用C#编辑Word文档][3]

## 用于 Word 文档编辑和自动化的 .NET API {#word-editing-dotnet-api}

在本文中，我将在 C# 示例中使用 [GroupDocs.Editor for .NET][4]，它是文档编辑 API，允许开发人员使用 WYSIWYG HTML 编辑器加载、编辑和保存各种文档格式。除了文字处理文档格式，API 还支持编辑电子表格、演示文稿、HTML、XML、TXT、DSV、TSV 和 CSV 格式。

从 [下载部分][5] 下载 **DLLs** 或 **MSI** 安装程序，或通过 [NuGet][6] 在您的 .NET 应用程序中安装 API。

```
PM> Install-Package GroupDocs.Editor
```

## 在 C# 中编辑 Word 文档 {#edit-word-docs-in-csharp}

设置 API 后，您可以快速开始编辑 Word 文档。以下步骤将让您编辑文字处理文档。

* 加载 Word 文档。
* 使用选项进行相应编辑。
* 保存编辑的文档。

### 加载Word文档

首先，如果文档受到保护，则通过提供文档路径和密码来加载文档。

```
using (FileStream fs = File.OpenRead(inputFilePath))
{
    Options.WordProcessingLoadOptions loadOptions = new WordProcessingLoadOptions();
    loadOptions.Password = "password-if-any";
}
```

### 编辑Word文档

加载后，您可以根据需要编辑加载的文档。在这里，我使用下面的 C# 代码将 Word 文档中所有出现的单词“document”替换为“edited document”。

```
    using (Editor editor = new Editor(delegate { return fs; }, delegate { return loadOptions; }))
    {
        Options.WordProcessingEditOptions editOptions = new WordProcessingEditOptions();
        editOptions.FontExtraction = FontExtractionOptions.ExtractEmbeddedWithoutSystem;
        editOptions.EnableLanguageInformation = true;
        editOptions.EnablePagination = true;
        using (EditableDocument beforeEdit = editor.Edit(editOptions))
        {
            string originalContent = beforeEdit.GetContent();
            List<IHtmlResource> allResources = beforeEdit.AllResources;
            string editedContent = originalContent.Replace("document", "edited document");
        }
    }
```

### 使用选项保存已编辑的 Word 文档

最后，在保存编辑的文档内容的同时，您可以进一步设置各种选项。这些选项包括：分页、设置密码、区域设置、保护或内存优化设置。我在下面提到的代码中设置了上述选项，并将编辑后的文档保存为受密码保护的只读 DOCX 文件。

```
using (EditableDocument afterEdit = EditableDocument.FromMarkup(editedContent, allResources))
{
    Options.WordProcessingSaveOptions saveOptions = new WordProcessingSaveOptions(WordProcessingFormats.Docx);
    saveOptions.EnablePagination = true;
    saveOptions.Locale = System.Globalization.CultureInfo.GetCultureInfo("en-US");
    saveOptions.OptimizeMemoryUsage = true;
    saveOptions.Password = "password";
    saveOptions.Protection = new WordProcessingProtection(WordProcessingProtectionType.ReadOnly, "write\_password");
    using (FileStream outputStream = File.Create("filepath/editedDocument.docx"))
    {
        editor.Save(afterEdit, outputStream, saveOptions);
    }
}
```

### 完整代码

为方便起见，我展示了上面解释的完整 C# 示例，它编辑 Word 文档，然后将其保存为 DOCX 格式。

```
// 使用 GroupDocs 文档编辑和自动化 API 在 C# 中编辑 Word 文档
using (FileStream fs = File.OpenRead("filepath/document.docx"))
{   // Load Document
    Options.WordProcessingLoadOptions loadOptions = new WordProcessingLoadOptions();
    loadOptions.Password = "password-if-any";
    // Edit Document
    using (Editor editor = new Editor(delegate { return fs; }, delegate { return loadOptions; }))
    {
        Options.WordProcessingEditOptions editOptions = new WordProcessingEditOptions();
        editOptions.FontExtraction = FontExtractionOptions.ExtractEmbeddedWithoutSystem;
        editOptions.EnableLanguageInformation = true;
        editOptions.EnablePagination = true;

        using (EditableDocument beforeEdit = editor.Edit(editOptions))
        {
            string originalContent = beforeEdit.GetContent();
            List<IHtmlResource> allResources = beforeEdit.AllResources;

            string editedContent = originalContent.Replace("document", "edited document");
            // Save Document
            using (EditableDocument afterEdit = EditableDocument.FromMarkup(editedContent, allResources))
            {
                WordProcessingFormats docxFormat = WordProcessingFormats.Docx;
                Options.WordProcessingSaveOptions saveOptions = new WordProcessingSaveOptions(docxFormat);
                            
                saveOptions.EnablePagination = true;
                saveOptions.Locale = System.Globalization.CultureInfo.GetCultureInfo("en-US");
                saveOptions.OptimizeMemoryUsage = true;
                saveOptions.Password = "password";
                saveOptions.Protection = new WordProcessingProtection(WordProcessingProtectionType.ReadOnly, "write_password");

                using (FileStream outputStream = File.Create("filepath/editedDocument.docx"))
                {
                    editor.Save(afterEdit, outputStream, saveOptions);
                }
            }
        }
    }
}
```

以下是使用上述代码替换所有匹配项的输出文档。



{{< figure align=center src="images/edited-document.png" alt="使用编辑器 API 编辑 docx 文档" caption="输出文档 - 所有出现的地方都被替换">}}


## 结论

最后，我们讨论了使用 .NET 应用程序的文档编辑 API 在 C# 中编辑 Word 文档。您可以将 API 与 WYSIWYG 编辑器一起使用，以可视化编辑您的文档。之后，您可以继续构建自己的文档编辑器。同样，您也可以在 .NET 应用程序中集成编辑功能。

有关更多详细信息、选项和示例，您可以访问 [文档][7] 和 [GitHub][8] 存储库。如需进一步查询，请联系 [论坛][9] 上的支持人员。

## 相关文章

* [使用C#编辑XML文件数据][10]
* [如何在 Java 中编辑 XML 文件][11]

## 也可以看看

* [本地文档编辑 API][12]
* [文档编辑和自动化云 API][13]
* [在线编辑Word文档][14]







[1]: https://blog.groupdocs.com/2021/03/26/edit-word-documents-in-csharp/
[2]: #word-editing-dotnet-api
[3]: #edit-word-docs-in-csharp
[4]: https://products.groupdocs.com/editor/net
[5]: https://downloads.groupdocs.com/editor/net
[6]: https://www.nuget.org/packages/groupdocs.editor
[7]: https://docs.groupdocs.com/editor/net
[8]: https://github.com/groupdocs-editor
[9]: https://forum.groupdocs.com/c/assembly
[10]: https://blog.groupdocs.com/2021/11/02/edit-xml-files-using-csharp/
[11]: https://blog.groupdocs.com/2021/11/06/edit-xml-files-in-java/
[12]: https://products.groupdocs.com/editor/family
[13]: https://products.groupdocs.cloud/editor/family
[14]: https://products.groupdocs.app/editor/word


