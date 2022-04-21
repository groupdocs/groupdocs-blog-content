---
title: 'Get More Flexibility with the New and Improved Features in the GroupDocs.Viewer for Java Library 2.3'
date: Thu, 31 Jul 2014 15:43:35 +0000
draft: false
url: /2014/07/31/get-more-flexibility-with-the-new-features-in-groupdocs-viewer-for-java-library-2-3/
author: 'Ihor Mykhalevych'
summary: ''
tags: ['GroupDocs Viewer', 'java document viewer', 'viewer for java library', 'zArchive']
---

[![GroupDocs.Viewer for Java library](https://blog.groupdocs.com/wp-content/uploads/sites/4/2014/06/GD_VWR_JavaIcon_1141.png)](http://groupdocs.com/java/document-viewer-library)Hi, everyone! We've recently released a new version of the Java document viewer - GroupDocs.Viewer for Java version 2.3 - and would like to discover its new features and enhancements in this article. [GroupDocs.Viewer for Java](http://groupdocs.com/java/document-viewer-library) is an HTML5-based document viewer library designed to make it easy for developers to integrate into their Java apps. The viewer supports more than 50 document and image types, including PDF, Microsoft Word, Excel, PowerPoint, AutoCAD, Visio, etc. Implemented within HTML5 standards, the viewer allows documents to be viewed from any web-enabled device using only a web‑browser. Let's now look at the enhancements seen in the latest version of the library (version 2.3):

### Application Path FlexibilityThe application path allows the viewer to link and handle client-server requests correctly. Starting from version 2.2, it is possible to use a relative paths. You can now also choose between three different types of the applicationPath parameter value:

*   Absolute path, like: http://127.0.0.1:8080
*   Custom URL prefix, like: custom-url Prefix (custom-url) is added to the full application path, including context path ‑ http://127.0.0.1:8080/custom-url
*   null value In this case the viewer uses the default application request URI (for example, http://127.0.0.1:8080/)

### Added UI Configuration Parameters

*   **PDF Printing** Thanks to the new usePdfPrinting parameter, you can now print documents directly to PDF. Just set the parameter value to **true**. In this case, when clicking the **Print** button, a user gets the document printed out in the PDF format.

*   **Page Reordering** When the supportPageReordering parameter is set to **true**, users can change a documents page order by dragging page thumbnails in the left side panel. Please note that this option does not change the original document itself. It is intended to help users conveniently browse and collaborate on documents in the web UI. Also, the page reordering feature currently works in the image-based rendering mode only. Set the useHtmlBasedEngine parameter to **false** in order to enable the feature.

### WatermarkingProtecting documents with watermarks in now also easier. There are two parameters available:

*   watermarkText - specifies text for the watermark
*   watermarkColor - specifies color of the watermark (6 hex digits, i.e. **fb3000**)

Watermarks are added in a separate layer over the rendered documents, so that the original files are not modified. If you want to keep your documents safe, please be sure to disable both the **Download** and **Printing** options as well. Also, please note that watermarks can be added in the image-based rendering mode only.

### Custom LocalizationAnother great feature added in the latest versions of the Java document viewer - support of custom localizations. In the earlier versions you would have to tweak the viewer's front-end with your own localization ([as described here](https://docs.groupdocs.com/viewer/java)). Starting from now, you can simply add a localization file. For example, assume we need Portuguese localization. First, we have to create a file called **pt-PT.properties** and fill it with translated terms:

```
BookMode=Vista Revista
FileName=Nome do Arquivo
FitHeight=Ajustar a Altura
FitWidth=Ajustar a Largura
LoadingYourContent=Carregando conteudo...
Modified=Modificado
Of=de
OpenFile=Abrir Arquivo
ParentFolder=Pasta principal
ScrollView=Scroll Vertical
Search=Pesquisa
Size=Tamanho
Thumbs=Miniaturas
```

The localization file name has to be in the following format: **<locale>.properties** to be recognized with the viewer. Once the file is ready, place it somewhere in the system (G:\\Projects\\GroupDocs\\app\\locale) and set the path as the localesPath parameter value:```
G:\\Projects\\GroupDocs\\app\\xFiles
```**Please note.** This value has to be strictly directory path only. Do not append the locale file name to the path, since GroupDocs.Viewer automatically picks up an appropriate localization for your system. So you can place several localization files in that directory.

### Other Improvements

*   Added support for XPS file format
*   Implemented P8 FileNet support
*   Added sub-folders navigation. Now you can browse and open any sub-folder content.

  For a complete list of changes, please check the release notes in the [GroupDocs file archive](http://groupdocs.com/Community/files/9/java-libraries/groupdocs_viewer_for_java/category1005.aspx). The library itself can be downloaded from there. For more information on the viewer and its features, please visit [GroupDocs.Viewer for Java home page](http://groupdocs.com/java/document-viewer-library). To help you install and get started with the viewer quickly we also provide [example code projects](http://groupdocs.com/Community/files/9/java-libraries/groupdocs_viewer_for_java/category1004.aspx) and [detailed documentation](http://groupdocs.com/docs/display/viewerjava/Home) with technical articles and guides.




