---
title: 'View Contents of ZIP and TAR Archives using GroupDocs.Viewer for Java 19.11'
date: Tue, 10 Dec 2019 06:09:30 +0000
draft: false
url: /2019/12/10/view-files-and-folders-in-zip-and-tar-archives-using-java-api/
author: 'Usman Aziz'
summary: ''
tags: ['document viewer', 'java', 'java document viewer', 'PDF', 'TAR', 'view contents in ZIP or TAR', 'ZIP', 'zip viewer']
categories: ['GroupDocs.Viewer for Java', 'GroupDocs.Viewer Product Family']
---



{{< figure align=center src="images/groupdocs-viewer-for-java_logo-e1566819687432.png" alt="Java ZIP TAR Viewer">}}


We are excited to bring a major release of [GroupDocs.Viewer for Java](https://products.groupdocs.com/viewer/java) API packaging a bunch of new features, improvements, and bug fixes. In the latest release, we have added the support of viewing archives and a couple of code files as well as provided the features of working with security settings in the PDF documents. So let's walk through the latest release of our document viewer API for Java and check out what you are going to get after upgrading to **v19.11**.

## View ZIP and TAR Archives

The first and foremost feature of v19.11 is viewing the list of files and folders in the ZIP and TAR archives. This feature is quite handy when you want to view the list of the contents without extracting the archives.

[ZIP](https://wiki.fileformat.com/compression/zip/) file is used to encase multiple files or folders as a single package that is further compressed to reduce the file size. Similarly, [TAR](https://wiki.fileformat.com/compression/tar/) is a Unix File Archive format used to archive the files and folders. In general, both ZIP and TAR are categorized as compression file formats.

In the following sections, you will see how to view a list of contents from the ZIP or TAR archives without extracting.

### **View List of Contents in ZIP or TAR Archives** {#mce_3}

When rendering an archive file as HTML, GroupDocs.Viewer returns an HTML page containing the list of items that are at the root of the archive. In the case of rendering as image or PDF, the API returns one or more pages depending on the number of items. The following code sample demonstrates this feature.

{{< gist GroupDocsGists bf4cf450bb954375e21ecdc7544fdc56 "ViewZIPAndTARArchive.java" >}}

### **View List of Folders from ZIP or TAR** {#RenderingArchivedocuments-ObtainingthelistoffoldersfromtheArchive}

ZIP or TAR archives may contain multiple files and folders. These folders may further contain files as well as subfolders. GroupDocs.Viewer also allows viewing the folders that are located at the root of the archive. The following code sample shows how to get a list of folders from a ZIP or TAR archive.

{{< gist GroupDocsGists bf4cf450bb954375e21ecdc7544fdc56 "GetListOfFoldersInArchive.java" >}}

### **View List of Subfolders within a Certain Folder of ZIP or TAR**

There might be the case when you need to obtain the list of subfolders within a root folder in the ZIP or TAR archive. For such a case, you can specify the folder name using _[ArchiveOptions.setFolderName("FolderName")](https://apireference.groupdocs.com/viewer/java)_ and the API will return the list of subfolders.

{{< gist GroupDocsGists bf4cf450bb954375e21ecdc7544fdc56 "GetListOfSubFoldersInRootFolder.java" >}}

### **View List of Files within a Folder in ZIP or TAR**

Now, once you have got the list of folders (and the subfolders as well), you can extract and view the items from your desired folder. The following code sample shows how to view the items of a specific folder in a ZIP or TAR.

{{< gist GroupDocsGists bf4cf450bb954375e21ecdc7544fdc56 "RenderSpecifiedFolderInArchive.java" >}}

For more details on rendering archives, please visit [working with archives](https://docs.groupdocs.com/viewer/java).

## Working with Security Settings in PDF Documents

The PDF documents allow setting security parameters to restrict unauthorized access. The security can be enabled using:

*   **Owner password** - The password which is required to change document permissions.
*   **User password** - The password required to open the document.
*   **PDF file permissions** - The permissions to allow or deny printing, modification and data extraction.

In the latest release, we have added the feature of setting the above-mentioned security settings when rendering a file into a PDF document. The following code sample shows how to set the owner password, user password, and the permissions to deny the printing.

{{< gist GroupDocsGists bf4cf450bb954375e21ecdc7544fdc56 "RenderIntoPDFWithSecuritySettings.java" >}}

### **Detecting Security Settings in PDF Document**

You can also check the security settings that are applied to a particular PDF document. For example, you can check if printing of the document is allowed or not as shown in the following code sample.

{{< gist GroupDocsGists bf4cf450bb954375e21ecdc7544fdc56 "CheckPrintRestrictionsInPDF.java" >}}

## Support for Viewing Code Files

In addition to the support of ZIP and TAR files, we have also added the feature of viewing C# ([.cs](https://wiki.fileformat.com/programming/cs/)) and Visual Basic ([.vb](https://wiki.fileformat.com/programming/vb/)) code files.

## Bug Fixes

The following is the list of bugs that are fixed in v19.11.

*   Output extension is empty when saving HTML page into cache
*   Object null reference exception when rendering DWG document
*   The Watermark opacity is set twice when rendering as HTML
*   The separator is wrong for the opacity value
*   File is corrupted or damaged exception for presentation documents
*   Unable to render .xls file with exception "file is corrupted or damaged"

## Improvement

We have made the following improvements in v19.11.

*   Improved performance for rendering PSD image format into PDF
*   Improved rendering Dicom, Dng and WebP formats into PDF
*   Extended support for _[CellsOptions.setTextOverflowMode](https://apireference.groupdocs.com/viewer/java)_ option for rendering the document into image
*   Extended support for _[CellsOptions.setTextOverflowMode](https://apireference.groupdocs.com/viewer/java)_ option for rendering into PDF
*   Rendering contact photo from vCard file format (VCF)
*   Improve output for rendering zip archives

Well, this was a brief overview of the major features as well as improvements and bug fixes. You can also visit the [release notes](https://docs.groupdocs.com/display/viewerjava/GroupDocs.Viewer+for+Java+19.11+Release+Notes) of _GroupDocs.Viewer for Java_ _19.11_ to know about the public API changes. Visit the [documentation](https://docs.groupdocs.com/display/viewerjava/Developer+Guide) of _GroupDocs.Viewer for Java_ for more details and code samples of every feature. You can download/clone the source code examples from the [GitHub repository](https://github.com/groupdocs-viewer/GroupDocs.Viewer-for-Java).

In case you find any issue while using our API, we are always available to provide you free support on our [forum](https://forum.groupdocs.com/c/viewer).




