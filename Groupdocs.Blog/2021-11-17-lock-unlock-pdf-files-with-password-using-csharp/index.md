---
title: 'Lock and Unlock PDF Files with Password using C#'
seoTitle: "Password Protect PDF Files in C# | Lock Unlock PDF"
description: "Let's learn how to lock PDF files with password protection using C#. Change the existing password or remove it to unlock the PDF files using .NET API."
date: Wed, 17 Nov 2021 12:28:00 +0000
draft: false
url: /2021/11/17/lock-unlock-pdf-files-with-password-using-csharp/
aliases:
    - /2021/11/17/password-protection-to-pdf-files-in-csharp/
    - /2019/09/25/add-password-protection-to-word-or-pdf-files-in-csharp/
    - /2019/09/25/add-password-protection-to-word-or-pdf-files-in-c/
author: 'Shoaib Khan'
summary: 'Let us learn to secure our documents from unauthorized access. Previously we discussed [adding text and image watermarks to the documents][1] to avoid and illegal use. In this article, we will see **how to add password protection to PDF documents to get them locked using C#**. Additionally, we will **change the existing password** and also learn to **remove the password** to make the PDF unlocked.

The following topics are discussed in this article:

*   .NET API for Password Protection of PDF files
*   Lock PDF Files by adding Password
*   Change PDF Password in C#
*   How to Remove PDF Password - Unlock PDF'
tags: ['add password to PDF in csharp', 'Change PDF Password in CSharp', 'Lock PDF in CSharp', 'Remove PDF Password in CSharp', 'Unlock PDF in CSharp']
categories: ['GroupDocs.Merger Product Family']
---

Let's learn to secure our documents from unauthorized access. Previously we discussed [adding text and image watermarks to the documents][2] to avoid any illegal use. In this article, we will see **how to add password protection to PDF documents to get them locked using C#**. Additionally, we will **change the existing password** and also learn to **remove the password** to make the PDF unlocked.



{{< figure align=center src="images/password-protect-lock-unlock-pdf.jpg" alt="Programmatically Protect PDF Files with Password - Lock Unlock">}}


The following topics are discussed below:

*   [.NET API for Password Protection of PDF Files][3]
*   [Lock PDF Files by Adding Password][4]
*   [Change PDF Password in C#][5]
*   [How to Remove PDF Password - Unlock PDF][6]

## .NET API to Lock and Unlock PDF Files {#lock-unlock-pdf-dotnet-api}

To lock and unlock documents, we will use [GroupDocs.Merger for .NET][7]. This API enables adding, changing, and removing password security features for the documents within the .NET applications. Along with protecting and unprotecting PDF documents, the API provides many more features like merging and splitting that are mentioned in the [documentation][8].

You can download the **DLLs** or **MSI** installer from the [downloads section][9] or install the API in your .NET application via [NuGet][10].

```
PM> Install-Package GroupDocs.Merger
```

## Add Password to PDF in C# - Lock PDF {#lock-pdf-by-password}



{{< figure align=center src="images/locked-PDF.jpg" alt="Lock PDF with Password">}}


Let's start by adding protection to the file by locking it with the password. The following steps show how to add password security to the PDF documents using C#.

*   Define the password using the [AddPasswordOptions][11] class.
*   Load the PDF file using [Merger][12] class.
*   Lock the file by adding password using [AddPassword][13] method.
*   Save the protected file using the [Save][14] method.

The following C# code adds the password to the PDF file for security.

{{< gist GroupDocsGists cbb54ae36d531fd13a6bd3f5645c252f "AddPasswordToPDF.cs" >}}

Here is the output of the above code. When you try to open the PDF file, the editor or viewer will ask for the password to prove your authority.



{{< figure align=center src="images/enter-pwd-to-protected-pdf-1024x298.png" alt="Enter Password to Protected PDF">}}


## Update Existing Password of PDF Files in C# {#change-pdf-password}

Oops! your password is probably exposed. Let's quickly change it programmatically with the new and difficult one. The following steps allow you to change the current password of your PDF files within your .NET application in C#.

*   Prepare the [loading options][15] using the current password.
*   Prepare the [update options][16] using the new password.
*   Load the PDF document using [Merger][17] class and the loading options.
*   Change the existing password using [UpdatePassword][18] method.
*   Save the locked file having changed password using the [Save][19] method.

Here is the code snippet that changes the current password of the PDF document.

{{< gist GroupDocsGists cbb54ae36d531fd13a6bd3f5645c252f "ChangePdfPassword.cs" >}}

## Remove PDF Files' Password in C# - Unlock PDF {#remove-password-to-unlock-pdf}



{{< figure align=center src="images/unlocked-PDF.jpg" alt="PDF unlocked - Removed Password">}}


Now, I think you do not need security, that's why you want to remove the password. Let's open the file first and then remove its password so that everyone can access it easily. The following steps show how to unlock the PDF file by removing its password using C#.

*   Prepare the [loading options][20] using the file's password.
*   Load the PDF document using [Merger][21] class and the load options.
*   Remove the existing password using [RemovePassword][22] method.
*   Save the unlocked file using the [Save][23] method.

The following C# code snippet unlocks the PDF file by removing its existing password, hence anyone can access it without authorization.

{{< gist GroupDocsGists cbb54ae36d531fd13a6bd3f5645c252f "RemovePdfPassword.cs" >}}

## Conclusion

Let's sum up what we learned today. We started with the simple PDF document and added password protection. Then we changed the existing password of that PDF file. In the end, we learned how to remove the password of our PDF documents. Now you can jump to build your own password protector or password remover application using the .NET API.

To learn more about GroupDocs.Merger for .NET, visit the [documentation][24]. For queries, contact us via the [forum][25].

## Get a Free API License

You can [get a free temporary license][26] to use the API without the evaluation limitations.

## See Also

*   [Watermark PDF Files using C#][27]
*   [How to Split PDF Files using C#][28]
*   [Add or Remove Password Protection of PDF Files in Java][29]







[1]: https://blog.groupdocs.com/2021/07/27/watermark-pdf-files-using-csharp/
[2]: https://blog.groupdocs.com/2021/07/27/watermark-pdf-files-using-csharp/
[3]: #lock-unlock-pdf-dotnet-api
[4]: #lock-pdf-by-password
[5]: #change-pdf-password
[6]: #remove-password-to-unlock-pdf
[7]: https://products.groupdocs.com/merger/net/
[8]: https://docs.groupdocs.com/merger/net/
[9]: https://downloads.groupdocs.com/merger
[10]: https://www.nuget.org/packages/groupdocs.merger
[11]: https://apireference.groupdocs.com/merger/net/groupdocs.merger.domain.options/addpasswordoptions
[12]: https://apireference.groupdocs.com/merger/net/groupdocs.merger/merger
[13]: https://apireference.groupdocs.com/merger/net/groupdocs.merger/merger/methods/addpassword
[14]: https://apireference.groupdocs.com/merger/net/groupdocs.merger/merger/methods/save/index
[15]: https://apireference.groupdocs.com/merger/net/groupdocs.merger.domain.options/loadoptions
[16]: https://apireference.groupdocs.com/merger/net/groupdocs.merger.domain.options/updatepasswordoptions
[17]: https://apireference.groupdocs.com/merger/net/groupdocs.merger/merger
[18]: https://apireference.groupdocs.com/merger/net/groupdocs.merger/merger/methods/updatepassword
[19]: https://apireference.groupdocs.com/merger/net/groupdocs.merger/merger/methods/save/index
[20]: https://apireference.groupdocs.com/merger/net/groupdocs.merger.domain.options/loadoptions
[21]: https://apireference.groupdocs.com/merger/net/groupdocs.merger/merger
[22]: https://apireference.groupdocs.com/merger/net/groupdocs.merger/merger/methods/removepassword
[23]: https://apireference.groupdocs.com/merger/net/groupdocs.merger/merger/methods/save/index
[24]: https://docs.groupdocs.com/merger
[25]: https://forum.groupdocs.com/
[26]: https://purchase.groupdocs.com/temporary-license
[27]: https://blog.groupdocs.com/2021/07/27/watermark-pdf-files-using-csharp/
[28]: https://blog.groupdocs.com/2021/10/11/split-pdf-files-in-csharp/
[29]: https://blog.groupdocs.com/2021/12/07/password-protect-pdf-files-in-java/

