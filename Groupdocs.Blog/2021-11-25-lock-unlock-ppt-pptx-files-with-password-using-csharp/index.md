---
title: 'Lock and Unlock PowerPoint Files with Password using C#'
seoTitle: "Password Protect PowerPoint Files in C# | Lock Unlock PPT & PPTX"
description: "How to lock PowerPoint files with passwords using C#. Change the existing password and remove it to unlock the PPT/PPTX files using the .NET API."
date: Thu, 25 Nov 2021 15:48:29 +0000
draft: false
url: /2021/11/25/lock-unlock-ppt-pptx-files-with-password-using-csharp/
author: 'Shoaib Khan'
summary: 'Today, we will provide password protection to our presentation files programmatically. In this article, we will see **how to lock **PowerPoint presentation files** with password protection in C#**. Further, we will learn to unlock these by **removing the password** and also **how to change the existing password** of PPT & PPTX presentation files.

The following topics are discussed in this article:

*   .NET API to Protect PowerPoint PPT/PPTX with Password
*   Lock PowerPoint Files by adding Password
*   Change PPT/PPTX Password in C#
*   How to Remove PowerPoint Presentation Password'
tags: ['Add Password to PPT in CSharp', 'Change PPT Password in CSharp', 'Lock PPT in CSharp', 'Remove Password in CSharp', 'Unlock Files in CSharp']
categories: ['GroupDocs.Merger Product Family']
---

Today, we will provide password protection to our presentation files programmatically. Previously, we learned something similar while discussing [password protection of PDF files in C#][1]. In this article, we will see **how to lock **PowerPoint presentation files** with password protection in C#**. Further, we will learn to unlock these by **removing the password** and also **how to change the existing password** of PPT & PPTX presentation files.



{{< figure align=center src="images/password-protect-lock-unlock-presentations.jpg" alt="Password Protect Presentations - Lock Unlock PPT-PPTX">}}


The following topics are discussed below:

*   [.NET API to Protect PowerPoint PPT/PPTX with Password][2]
*   [Lock PowerPoint Files by adding Password][3]
*   [Change PPT/PPTX Password in C#][4]
*   [How to Remove PowerPoint Presentation Password][5]

## .NET API to Lock and Unlock PowerPoint Files {#lock-unlock-ppt-dotnet-api}

To work with the protection of presentation files, we will use [GroupDocs.Merger for .NET][6]. This API allows adding, changing, and removing password security features for the presentation and other documents within the .NET applications. Along with the locking and unlocking PPT files, the API provides many more features including merging and splitting presentations that are mentioned in the [documentation][7].

You can download the **DLLs** or **MSI** installer from the [downloads section][8] or install the API in your .NET application via [NuGet][9].

```
PM> Install-Package GroupDocs.Merger
```

## Add Password to PowerPoint Files in C# - Lock PPT/PPTX {#lock-ppt-by-password}



{{< figure align=center src="images/locked-PPT.jpg" alt="Lock PPT with Password">}}


We can programmatically lock any presentation file by adding password protection to it. The following steps show how to add a password to a PowerPoint presentation (PPT/PPTX) using C#.

*   Define the password using the [AddPasswordOptions][10].
*   Load the PowerPoint file using the [Merger][11] class.
*   Apply protection by adding password using [AddPassword][12] method.
*   Save the protected presentation file using the [Save][13] method.

The following C# code snippet locks the PPT by adding a password for limited access.

{{< gist GroupDocsGists 6b5a987cb0a752d6fdf3949108779561 "AddPasswordToPPT.cs" >}}

Here is the output of the above code. When you try to open the file, the editor or viewer will ask for the password to open the presentation.



{{< figure align=center src="images/enter-pwd-to-protected-pptx-presentation.png" alt="Enter Password to Protected PPTX">}}


## Update Existing Password of PPT/PPTX Files in C# {#change-ppt-password}

Looks like there was a sneak peek at your password. Let's change it. The following steps allow you to change the existing presentation file password using C#.

*   Prepare the [loading options][14] using the current password.
*   Prepare the [update options][15] using the new password.
*   Load the presentation using [Merger][16] class.
*   Change the password using the [UpdatePassword][17] method.
*   Call [Save][18] method to save the locked file having new password.

Here is the code snippet that changes the existing password of a PowerPoint PPT/PPTX presentation.

{{< gist GroupDocsGists 6b5a987cb0a752d6fdf3949108779561 "ChangePptPassword.cs" >}}

## Remove PowerPoint File Password in C# - Unlock PPT/PPTX {#remove-password-to-unlock-ppt}



{{< figure align=center src="images/unlocked-PPT.jpg" alt="Unlock PPT - Password Removed">}}


Now let's remove the cover and let everyone benefit from your presentation. First, open the file and then remove its password for easy access. The following steps show how to unlock the PPT file by removing its password using C#.

*   Use file's password to prepare the [loading options][19].
*   **Load** the PowerPoint presentation document using [Merger][20] class.
*   **Remove** the password using [RemovePassword][21] method.
*   **Save** the unlocked file using the [Save][22] method.

The following C# code sample unlocks the PowerPoint presentation file by removing its password.

{{< gist GroupDocsGists 6b5a987cb0a752d6fdf3949108779561 "RemovePptPassword.cs" >}}

## Conclusion

Let's conclude with an overview of what we learned today. We used a simple PowerPoint presentation (PPTX) and first, we locked it just by adding a password. Next, we changed the existing password of the presentation file. Lastly, we learned how to remove the password of the PowerPoint presentations.

To learn more about GroupDocs.Merger for .NET, visit the [documentation][23] and start building your own application to lock and unlock presentation files. For queries, contact us via the [forum][24].

## Get a Free API License

You can [get a free temporary license][25] to use the API without the evaluation limitations.

## See Also

*   [Lock & Unlock PDF Files with Password using C#][26]
*   [Convert PPT, PPTX Presentations to PDF in C#][27]
*   [Watermark PDF Files using C#][28]
*   [How to Split PDF Files using C#][29]







[1]: https://blog.groupdocs.com/2021/11/17/lock-unlock-pdf-files-with-password-using-csharp/
[2]: #lock-unlock-ppt-dotnet-api
[3]: #lock-ppt-by-password
[4]: #change-ppt-password
[5]: #remove-password-to-unlock-ppt
[6]: https://products.groupdocs.com/merger/net/
[7]: https://docs.groupdocs.com/merger/net/
[8]: https://downloads.groupdocs.com/merger
[9]: https://www.nuget.org/packages/groupdocs.merger
[10]: https://apireference.groupdocs.com/merger/net/groupdocs.merger.domain.options/addpasswordoptions
[11]: https://apireference.groupdocs.com/merger/net/groupdocs.merger/merger
[12]: https://apireference.groupdocs.com/merger/net/groupdocs.merger/merger/methods/addpassword
[13]: https://apireference.groupdocs.com/merger/net/groupdocs.merger/merger/methods/save/index
[14]: https://apireference.groupdocs.com/merger/net/groupdocs.merger.domain.options/loadoptions
[15]: https://apireference.groupdocs.com/merger/net/groupdocs.merger.domain.options/updatepasswordoptions
[16]: https://apireference.groupdocs.com/merger/net/groupdocs.merger/merger
[17]: https://apireference.groupdocs.com/merger/net/groupdocs.merger/merger/methods/updatepassword
[18]: https://apireference.groupdocs.com/merger/net/groupdocs.merger/merger/methods/save/index
[19]: https://apireference.groupdocs.com/merger/net/groupdocs.merger.domain.options/loadoptions
[20]: https://apireference.groupdocs.com/merger/net/groupdocs.merger/merger
[21]: https://apireference.groupdocs.com/merger/net/groupdocs.merger/merger/methods/removepassword
[22]: https://apireference.groupdocs.com/merger/net/groupdocs.merger/merger/methods/save/index
[23]: https://docs.groupdocs.com/merger
[24]: https://forum.groupdocs.com/
[25]: https://purchase.groupdocs.com/temporary-license
[26]: https://blog.groupdocs.com/2021/11/17/lock-unlock-pdf-files-with-password-using-csharp/
[27]: https://blog.groupdocs.com/2020/03/05/convert-presentations-pptx-ppt-to-pdf-in-csharp/
[28]: https://blog.groupdocs.com/2021/07/27/watermark-pdf-files-using-csharp/
[29]: https://blog.groupdocs.com/2021/10/11/split-pdf-files-in-csharp/

