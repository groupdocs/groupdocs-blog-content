---
title: 'Support for Text and Presentation Templates in GroupDocs.Parser for Java 18.12'
date: Thu, 20 Dec 2018 10:06:13 +0000
draft: false
url: /2018/12/20/15558/
author: 'Usman Aziz'
summary: ''
tags: ['Document Parser', 'document parsing API', 'document text extraction', 'Java Text Extractor', 'text analysis API']
categories: ['GroupDocs.Parser for Java', 'GroupDocs.Parser for Java Releases', 'GroupDocs.Parser Product Family']
---

![GroupDocs.Parser for Java](http://blog.groupdocs.com/wp-content/uploads/sites/4/2018/06/groupdocs-parser-java.png "GroupDocs-Parser-theme-100x100")

We are delighted to announce the release of [GroupDocs.Parser for Java](https://products.groupdocs.com/parser/java "GroupDocs.Parser product page") 18.12. The latest version allows you to extract the tables from PDF documents. Furthermore, we have added the support of extracting text and metadata from text and presentation templates. For more details, please have a look at the [release notes](https://docs.groupdocs.com/display/parserjava/GroupDocs.Parser+for+java+18.12+Release+Notes) of version 18.12.

# Features Introduced

## Extracting Tables from PDF DocumentsThis feature is very useful when you want to extract only the tables form a PDF document. For extracting tables, **TableAreaParser** class is used. The instance of **TableAreaParser** class is available via property with the same name in **PdfTextExtractor** class. You can create the table bounds manually or let the API detect the layout in automatic mode using **TableAreaDetector** class. For working example of this feature, please refer to [this](https://docs.groupdocs.com/parser/java/) documentation article.

## Extracting Text and Metadata from Text and Presentation TemplatesGroupDocs.Parser now supports extracting text and metadata from the following text and presentation template formats:

*   dotx (Template)
*   dotm (Macro-enabled template)
*   ott (OpenDocument Text Template)
*   potx (Template)
*   potm (Macro-enabled template)
*   ppsm (Macro-enabled slideshow)
*   pptm (Macro-enabled presentation)

The following code samples show how to extract text and metadata from templates.```
// Extracting Text
void extractText(String fileName) {
    // Extract a text from the file
    String text = Extractor.DEFAULT.extractText(fileName);
    // Print an extracted text
    System.out.println(text);
}
// Extracting Metadata 
void extractMetadata(String fileName) {
    // Extract metadata from the file
    MetadataCollection metadata = Extractor.DEFAULT.extractMetadata(fileName);
    // Print extracted metadata
    for (String key : metadata.getKeys()) {
        // Print a metadata key
        System.out.print(key);
        System.out.print(": ");
        // Print a metadata value
        System.out.println(metadata.get_Item(key));
    }
}
```

# Enhancements

## Detecting Type of Password-protected Office Open XML DocumentsThis feature allows detecting media type of the password-protected Office Open XML documents. To detect media type of encrypted Office Open XML document, **detect(InputStream, LoadOptions)** method is used. You can also use **IPasswordProvider** interface for batch document processing. For working examples of this feature, please refer to [this](https://docs.groupdocs.com/parser/java/) documentation article.

# Available Channels and Resources

Here are a few channels and resources for you to download, learn, try and get technical support on GroupDocs.Parser:

*   [Installation](https://artifact.groupdocs.com/webapp/#/artifacts/browse/tree/General/repo/com/groupdocs/groupdocs-parser "GroupDocs.Parser Installation") - Install GroupDocs.Parser from Maven
*   [Documentation](https://docs.groupdocs.com/display/parserjava/Introducing+GroupDocs.Parser+for+Java "Parser API documentation") - API Documentation
*   [Examples](https://github.com/groupdocs-parser/GroupDocs.Parser-for-Java "How to use Parser API") - Source Code Examples
*   [Product Support Forum](https://forum.groupdocs.com/c/parser) - Technical Support Forum for GroupDocs.Parser

# Feedback

As always, if you have any questions or suggestions, feel free to write on our [forum](https://forum.groupdocs.com/"Technical Support Forum").




