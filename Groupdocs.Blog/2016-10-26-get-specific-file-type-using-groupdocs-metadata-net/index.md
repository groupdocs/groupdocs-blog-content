---
title: 'Get Files of Specific Type using GroupDocs.Metadata for .NET'
date: Wed, 26 Oct 2016 22:12:37 +0000
draft: false
url: /2016/10/26/get-specific-file-type-using-groupdocs-metadata-net/
author: 'Usman Aziz'
summary: ''
tags: []
categories: ['GroupDocs.Metadata for .NET', 'GroupDocs.Metadata Product Family']
---

![](http://blog.groupdocs.com/wp-content/uploads/sites/4/2017/06/groupdocs-metadata-net.png "GroupDocs-Metadata-theme-100x100")In the modern times, the data is increasing dramatically. As a result, the large organizations may have maintained servers to store their organizational data in the form of files located in different directories. Very often, these organization may need to apply some filters to get files of a specific type i-e \*.docx or \*.txt etc. Filtering through a huge number files is not an easy job for the human beings and they might think if there is some automated system to achieve this. Of course, there is! We are happy to release such a business case example using [GroupDocs.Metadata for .NET](http://www.groupdocs.com/products/metadata/net). Let's see the available options and then how to do the same with GroupDocs.Metadata for .NET.

## Filtering Files using .NET ClassesThere are in-box solutions using **System.IO.Directory** or **System.IO.DirectoryInfo** classes in .NET Framework. Next code samples demonstrate how to get JPEG images in a specific directory.

### Solutions**Using Directory.GetFiles:**```
string\[\] files = Directory.GetFiles(@"C:\\download files", "\*.jpeg");
```**Using DirectoryInfo.GetFiles:**```
DirectoryInfo dirInfo = new DirectoryInfo(@"C:\\download files");
string\[\] files = dirInfo.GetFiles("\*.jpeg");
```

### DisadvantageThe disadvantage of these approaches is that we are getting the file by extension and not by signature. Also, file type could have more than one extension and multiple filters could not be applied.

## Filtering files using GroupDocs.Metadata for .NET[GroupDocs.Metadata for .NET](http://www.groupdocs.com/products/metadata/net) provides a smooth way to filter the files of a specific file type by their signatures. Let's see how can we perform this filtering.

### Solutions**1\. Using DocumentTypeDetector Static Class**```
// For complete examples and data files, please go to https://github.com/groupdocs-metadata/GroupDocs.Metadata-for-.NET
public static class DocumentTypeDetector
{
    /// <summary>
    /// Gets and returns document type of the file
    /// </summary>
    /// <param name="path">File Path</param>
    /// <returns>Document Type</returns>
    public static DocumentType GetDocumentType(string path)
    {
        using (FileFormatChecker fileFormatChecker = new FileFormatChecker(path))
        {
            return fileFormatChecker.GetDocumentType();
        }
    }

    /// <summary>
    /// Gets and returns files of a specific document type
    /// </summary>
    /// <param name="directory">Directory Path</param>
    /// <param name="documentType">Document Type</param>
    /// <returns>String array containing file paths</returns>
    public static string\[\] GetFiles(string directory, DocumentType documentType)
    {
        // get all files using Directory.GetFiles approach
        string\[\] files = Directory.GetFiles(directory, "\*.\*");

        // return empty array if directory is empty
        if (files.Length == 0)
        {
            return new string\[0\];
        }

        List<string> result = new List<string>();

        foreach (string path in files)
        {
            using (FileFormatChecker fileFormatChecker = new FileFormatChecker(path))
            {
                if (fileFormatChecker.VerifyFormat(documentType))
                {
                    result.Add(path);
                }
            }
        }

        return result.ToArray();
    }

}
```**2\. Defining Extension Method for System.IO.DirectoryInfo Class**```
// For complete examples and data files, please go to https://github.com/groupdocs-metadata/GroupDocs.Metadata-for-.NET
namespace System.IO
{
    public static class MyExtension
    {
        /// <summary>
        /// Gets and returns files of a specific document type
        /// </summary>
        /// <param name="directory">Directory Path</param>
        /// <param name="documentType">Document Type</param>
        /// <returns>File info array</returns>
        public static FileInfo\[\] GetFiles(this DirectoryInfo directoryInfo, DocumentType documentType)
        {
            FileInfo\[\] files = directoryInfo.GetFiles();

            // return empty array if directory is empty
            if (files.Length == 0)
            {
                return new FileInfo\[0\];
            }

            List<FileInfo> result = new List<FileInfo>();

            foreach (FileInfo fileInfo in files)
            {
                using (FileFormatChecker fileFormatChecker = new FileFormatChecker(fileInfo.FullName))
                {
                    if (fileFormatChecker.VerifyFormat(documentType))
                    {
                        result.Add(fileInfo);
                    }
                }
            }

            return result.ToArray();
        }
    }
}
```

## Complete ArticleFor more details, please visit our new article: [Detect Document Type](https://docs.groupdocs.com/metadata/net "GroupDocs.Metadata")

## Related Links and ResourcesHere are a few channels and resources for you to download, learn, try and get technical support on GroupDocs.Metadata for .NET.

*   [Download](http://www.groupdocs.com/downloads/metadata/net "GroupDocs.Metadata MSI") - MSI Package as well as Zipped DLLs
*   [NuGet](https://www.nuget.org/packages/groupdocs-metadata-dotnet/1.7.0 "GroupDocs.Metadata Nuget Package") - NuGet Install
*   [Documentation](http://www.groupdocs.com/docs/display/metadatanet/Getting+Started "Metadata API documentation") - API Documentation
*   [Examples/Plugins/Showcases](https://github.com/groupdocs-metadata/GroupDocs.Metadata-for-.NET/tree/master/Examples "How to use Metadata API") - Source Code Examples, Plugins, and Metadata Editor Application
*   [Video Tutorials](https://www.youtube.com/channel/UCkOlPEPh0oljoESrmKP6l4g "Metadata API YouTube Tutorials") - YouTube API videos
*   [Product Support Forum](http://www.groupdocs.com/Community/forums/groupdocs.metadata-product-family/48/showforum.aspx) - Technical Support Forum for GroupDocs Metadata queries




