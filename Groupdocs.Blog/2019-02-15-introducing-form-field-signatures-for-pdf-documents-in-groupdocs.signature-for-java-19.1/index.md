---
title: 'Introducing Form-Field Signatures for PDF Documents in GroupDocs.Signature for Java 19.1'
date: Fri, 15 Feb 2019 16:27:08 +0000
draft: false
url: /2019/02/15/introducing-form-field-signatures-for-pdf-documents-in-groupdocs.signature-for-java-19.1/
author: 'Usman Aziz'
summary: ''
tags: ['digital document signature', 'digital signature', 'Digital verification of Word documents', 'Image Signatrue', 'Metadata signature', 'sign documents online', 'signature api for java', 'Text Signature']
categories: ['GroupDocs.Signature for Java', 'GroupDocs.Signature for Java Releases', 'GroupDocs.Signature Product Family']
---

[![GroupDocs.Signature](https://blog.groupdocs.com/wp-content/uploads/sites/4/2017/03/groupdocs-signature-java.png)](https://www.groupdocs.com/products/signature/java)We are pleased to announce a major release of [ GroupDocs.Signature for Java](https://products.groupdocs.com/signature/java) containing 13 new features, 5 improvements, and 2 bug fixes. In this release, we have introduced Metadata Signature for word-processing, presentation and spreadsheet documents. Furthermore, a new signature type, Form-Field Signature, is implemented for signing PDF documents. Please have a look at the [release notes](https://docs.groupdocs.com/display/signaturejava/GroupDocs.Signature+for+Java+19.1+Release+Notes) for more details on the new features and changes introduced in version 19.1.

# Features Introduced

## Metadata Signature FeaturesThe latest version provides the support of Metadata Signature for word-processing, presentation and spreadsheet documents. Furthermore, you can also search Metadata Signatures within the aforementioned document types. For working examples, please visit the following documentation articles:

*   [Signing Spreadsheet Document with Metadata Signature](https://href.li/?https://docs.groupdocs.com/display/signaturejava/Signing+Cells+Document+with+Metadata+Signature)
*   [Signing Presentation Document with Metadata Signature](https://href.li/?https://docs.groupdocs.com/display/signaturejava/Signing+Slides+Document+with+Metadata+Signature)
*   [Signing Word-Processing Document with Metadata Signature](https://href.li/?https://docs.groupdocs.com/display/signaturejava/Signing+Words+Document+with+Metadata+Signature)
*   [Searching Metadata Signature in Spreadsheet Document](https://href.li/?https://docs.groupdocs.com/display/signaturejava/Search+Metadata+Signature+in+Cells+Document)
*   [Searching Metadata Signature in Presentation Document](https://href.li/?https://docs.groupdocs.com/display/signaturejava/Search+Metadata+Signature+in+Slides+Document)
*   [Searching Metadata Signature in Word-Processing Document](https://href.li/?https://docs.groupdocs.com/display/signaturejava/Search+Metadata+Signature+in+Words+Document)

## Form-Field Signature Features for PDF DocumentsMany documents support special elements as form-fields that allow the user to input data into standard form elements such as text input, extended multi-line text, checkboxes, radio buttons, digital certificate holders etc. These form-fields can also be used for adding signatures. For this, we have introduced **Form-Field Signature** type representing an input control that is added to the document page. You can add as well as search Form-Field Signatures in PDF documents. For working examples, please have a look at the following  documentation articles:

*   [Signing PDF Document with Form-Field Signature](https://href.li/?https://docs.groupdocs.com/display/signaturejava/Signing+PDF+Document+with+Form-Field+Signature)
*   [Searching Form-Field Signature in PDF Document](https://href.li/?https://docs.groupdocs.com/display/signaturejava/Search+Form-Field+Signature+in+PDF+Document)

## Extended Digital Verification for Word DocumentsIn the latest version, we have extended the feature of digital verification for Word documents by adding new string properties **SubjectName **and **IssuerName** in **WordsVerifyDigitalOptions** class. These fields could be used as additional criteria to verify Digital Signatures of Words documents. For a working example, please visit [this](https://docs.groupdocs.com/signature/java) documentation article.

# Improvements

The following improvements are made in the latest release:

*   Implement global exception handler to catch all unhandled exceptions
*   Improve exceptions handling with proper details and exception type
*   Implement search results conversion to typed list of signatures
*   Implement support of password protected Open-Documents-Spreadsheet ODS file formats
*   Extend Form-Field signature name automatically with number prefix for multiple-pages options

# Bug Fixes

The following issues are fixed in version 19.1:

*   Exception is fired when searching PDF documents for form-fields that were set up without name
*   Skip output folder when **SaveOptions.OutputFileName** is set as absolute path

# Available Channels and Resources

Here are a few channels and resources for you to learn, try and get technical support on GroupDocs.Signature for Java:

*   [API Home Page](https://products.groupdocs.com/signature/java)
*   [Download](https://downloads.groupdocs.com/signature/java "Download") – Zipped JARs
*   [Installation](https://repository.groupdocs.com/webapp/#/artifacts/browse/tree/General/repo/com/groupdocs/groupdocs-signature) - Install using Maven
*   [Documentation](https://docs.groupdocs.com/display/signaturejava/Home "Documentation") – API Documentation
*   [Examples](https://github.com/groupdocs-signature/GroupDocs.Signature-for-Java "Examples") – GitHub Source Code Examples
*   [Product Support Forum](https://forum.groupdocs.com/c/signature "Product Support Forum") – Technical Support Forum for GroupDocs.Signature Product Family

# Feedback

As always, we will be happy to know your thoughts. Just create a new topic on our [forum](https://forum.groupdocs.com/c/signature) and our dedicated support team will be there to respond.




