---
title: 'GroupDocs.Assembly for .NET – Generate Word & PDF Documents from Templates in Your C#/VB.NET/ASP.NET Apps'
date: Fri, 12 Dec 2014 11:53:22 +0000
draft: false
url: /2014/12/12/groupdocs-assembly-for-dot-net-generate-word-and-pdf-documents-form-templates-in-c-sharp-vb-net-asp-net/
author: 'Ihor Mykhalevych'
summary: ''
tags: ['assembly for .net library', 'GroupDocs Assembly', 'zArchive']
---

![GroupDocs.Assembly for .NET Logo](https://blog.groupdocs.com/wp-content/uploads/sites/4/2014/04/GD_ASM_NETIcon_114.png)[GroupDocs.Assembly for .NET](http://groupdocs.com/dot-net/document-assembly-library) is a comprehensive library for generating documents and reports by merging your templates and data. With GroupDocs.Assembly, you can generate any type of document that requires custom data input. These could be invoices, NDAs, sales quotes, employment letters, reports, etc. The library supports Microsoft Word, Excel and PDF templates, and allows you to save the final, assembled documents in either of these formats. Just like all GroupDocs libraries, GroupDocs.Assembly for .NET is designed as a middleware that can be seamlessly integrated into any application, ECM, CMS and document management workflow. Thanks to the open API for all its operations, you can easily implement custom workflows tailored to your specific needs. From the end-user POV, the process of generating custom documents or reports consists of the following steps: 1. Create a template. Users can use existing templates in a PDF, Word (DOC/DOCX) or Excel (XLS/XLSX) format; create new templates with merge fields using any available office software, like Microsoft Word; or create templates using the GroupDocs.Assembly’s in-built template builder. 2. Connect the template to a data source. A data source can be either a DB, or an online questionnaire (a web-form). 3. Choose an output format and get completed documents that look like the initial templates, but incorporate custom data obtained from the adjusted source. For each completed questionnaire GroupDocs.Assembly generates a new unique document. As a result, your users save tons of time that they would otherwise spend on manual template filling. Reflecting the steps required to generate documents, the GroupDocs.Assemly for .NET library consists of three components: the **Template Editor**, **Questionnaire Builder** and **Questionnaire Executor**.

### Template EditorThis component comes in handy for turning a document into a template or editing an existing template. The template builder allows users to add or edit different types of input fields (such as text boxes, check boxes, radio buttons and list boxes) within Word and PDF documents. Once the template is ready, it can be connected to a DB or an online questionnaire, as well as saved for reuse. The Template Editor eliminates the need for use of any 3rd party office software, such as Microsoft Office, in the document assembly process. Still it supports native Word and PDF fields, allowing users to prepare document templates using whatever software they prefer. ![GroupDocs.Assembly for .NET – Template builder for Word & PDF documents](https://blog.groupdocs.com/wp-content/uploads/sites/4/2014/12/Template-Builder.png)

### Questionnaire BuilderThe questionnaire builder allows you to set default values, response length, hints, conditional logic and other metadata for each input field (merge field) within the corresponding template. The rules and values for template fields can be set via the API, or the UI that comes with the library. The questionnaire builder also allows you, or your end-users, to build online questionnaires (web-forms) associated with the templates. The questionnaires can be easily published on a stand-alone HTML page or integrated into an existing page. Basically, a questionnaire is an online form implemented as a wizard that guides respondents though the form filling process by using the rules you’ve set in the builder (field order, response length, etc.). ![GroupDocs.Assembly for .NET – Questionnaire builder](https://blog.groupdocs.com/wp-content/uploads/sites/4/2014/12/Questionarie-Builder.png)

### Questionnaire ExecutorThis is the core part of the library. It merges data with templates and generates the final completed documents. You can use GroupDocs.Assembly’s API to fill templates with data obtained from a DB, file, remote storage, or user input through the online questionnaires. ![GroupDocs.Assembly for .NET - Questionnaire executor for merging templates and data](https://blog.groupdocs.com/wp-content/uploads/sites/4/2014/12/Questionarie_Executor.png)

### Web UIAs already mentioned, the library also comes with an out-of-the-box web UI that can be integrated into any ASP.NET app. The wizard-like UI guides end-users through the entire document generation process and provides all the necessary tools for building templates and online questionnaires, publishing questionnaires on the web and managing completed documents. When integrated and configured, the UI provides hands-off document generation functionality, allowing your users to assemble documents without any help from admins or developers. The GroupDocs.Assembly’s flexible API allows you to build custom document generation workflows without any hassle. You can use both the API and UI wizards on every document generation stage. If you’re interested in GroupDocs.Assembly, please visit its [homepage](http://groupdocs.com/dot-net/document-assembly-library) to download the library along with a sample project. We provide free tech support for custom integrations, so please feel free to contact our support team for any help.



