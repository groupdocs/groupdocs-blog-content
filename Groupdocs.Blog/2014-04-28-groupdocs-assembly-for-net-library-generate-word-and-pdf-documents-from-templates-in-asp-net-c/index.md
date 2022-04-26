---
title: 'GroupDocs.Assembly for .NET Library – Introduction'
date: Mon, 28 Apr 2014 15:45:01 +0000
draft: false
url: /2014/04/28/groupdocs-assembly-for-net-library-generate-word-and-pdf-documents-from-templates-in-asp-net-c/
author: 'Derek Hyland'
summary: ''
tags: ['document assembly', 'GroupDocs Assembly', 'zArchive']
---

![GroupDocs.Assembly for .NET Logo](https://blog.groupdocs.com/wp-content/uploads/sites/4/2014/04/GD_ASM_NETIcon_114.png)We are pleased to announce the release of the new library that enhances a set of our document collaboration tools - [GroupDocs.Assembly for .NET](http://groupdocs.com/dot-net/document-assembly-library). The library generates PDF and Word documents from templates by automatically filling out merge fields with custom data. If your company or a client have to create tens or hundreds of documents by filling out standard templates with data obtained through user input or from a DB, this library can be of great help. Just to mention a few examples, it can be used to generate legal documents, insurance policies, invoices, bills, NDAs, order quotes, offer letters, and any other types of documents. The library can be installed with just a single DLL and allows you to easily embed document generation functionality into your ASP.NET / C# application. The server part of the library is deployed in conjunction with a web UI, which allows end users to prepare templates and get completed documents without any help from developers. The workflow is simple: 1. Users create templates in a Word or PDF format by adding merge fields to documents. Templates can be prepared in any office software that supports PDF or DOC/DOCX file editing. 2. GroupDocs.Assembly's wizards guide users through composing questionnaires (interviews) where each question is associated with a merge field in the templates. The questionnaires can be then embed into a web page or an application. 3. For each completed questionnaire, GroupDocs.Assembly generates a new, unique document by incorporating data entered through the questionnaire into the template. The finished document is available for download right away. 4. **Update:** starting from version 1.0.5, the GroupDocs.Assembly for .NET library includes a **template editor** component, meaning you can now not only generate documents based on your existing templates, but actually create new DOC/DOCX/PDF templates without the need to use Microsoft Office or Adobe Acrobat. With this new component, GroupDocs.Assembly for .NET covers a complete document generation cycle: 1) Create a new template or edit an existing one -> 2) Connect the template to a data source (a DB or user input) -> 3) Get completed documents that look like the template but incorporate data from your sources. For more details on this new version, its key components and features please refer to our new post [on this page](https://blog.groupdocs.com/groupdocs-assembly-for-dot-net-generate-word-and-pdf-documents-form-templates-in-c-sharp-vb-net-asp-net).

### Key Features & Benefits:

*   Easy deployment with just a single DLL + customizable web UI.
*   Data can be pulled from web forms (online questionnaires) or from a DB.
*   Ability to handle JavaScript events such as onTemplateCreated, onTemplateMerge, etc.
*   Simple wizards guide non-developer end users to prepare questionnaires and get completed documents with no coding required.
*   Support for different types of form fields, including text boxes, check boxes, radio buttons, list boxes and combo boxes.
*   Ability to set default values for each question, restrict respond length and value range.
*   Output documents look exactly like the template, but with custom data filled into the form fields.
*   We offer free deployment support to help you get the library up and running quickly. We're also open to feature requests to customize the library to your requirements.

If you'd like to try the library, please download a free evaluation copy from [this page](http://groupdocs.com/Community/getting-started/dot-net/document-assembly-library.aspx). We also offer a free 30-day license, which allows you to test the library without any restrictions - just [contact our sales](http://groupdocs.com/corporate/contact-us) to get one. For more details on the features, deployment guides and code samples, please visit the product's [home page](http://groupdocs.com/dot-net/document-assembly-library).




