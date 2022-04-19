---
title: 'Password Protection of PDF Files in Java'
date: Tue, 07 Dec 2021 07:36:00 +0000
draft: false
url: /2021/12/07/password-protect-pdf-files-in-java/
author: 'Shoaib Khan'
summary: 'There are different security levels that you can provide to your confidential documents. You can apply watermarks, encrypt files, or you can make your documents password-protected. In this article, we will see **how to programmatically add password protection to the PDF files within the Java applications**. Further, we will learn to **change the password** and also to **remove the passwords** to unlock PDF files.

The following topics are discussed in this article:

*   Java API for Password Protection of PDF Files
*   Password Protect PDF Files in Java
*   Change PDF Password in Java
*   How to Remove PDF Password - Unlock PDF'
tags: ['Add Password to PDF in Java', 'Change PDF Password in Java', 'Lock PDF in Java', 'Password Protect Document', 'Remove Password in Java', 'Unlock PDF in Java']
categories: ['GroupDocs.Merger Product Family']
---

There are different security levels that you can provide to your confidential documents. You can [apply watermarks][1], encrypt files, or you can [make your documents password-protected][2]. In this article, we will see **how to programmatically add password protection to the PDF files within the Java applications**. Further, we will learn to **change the password** and also to **remove the passwords** to unlock PDF files.



{{< figure align=center src="images/password-protect-lock-unlock-pdf-in-java.jpg" alt="Protect PDF Files with Password in Java - Lock Unlock">}}


The following topics are discussed below:

*   [Java API for Password Protection of PDF Files][3]
*   [Password Protect PDF Files in Java][4]
*   [Change PDF Password in Java][5]
*   [How to Remove PDF Password - Unlock PDF][6]

## Java API to Lock and Unlock PDF Files {#lock-unlock-pdf-java-api}

[GroupDocs.Merger for Java][7] is the API that allows to lock and unlock documents. We will use it to add, change, and remove password security features for the PDF documents within the Java applications. Along with protecting and unprotecting documents, the API provides many more features like splitting, merging documents, and many more that are mentioned in the [documentation][8].

You can download the **JAR** file from the [downloads section][9] or use the latest repository and dependency [Maven][10] configurations within your Java applications.

```
<repository>
	<id>GroupDocsJavaAPI</id>
	<name>GroupDocs Java API</name>
	<url>http://repository.groupdocs.com/repo/</url>
</repository>
<dependency>
        <groupId>com.groupdocs</groupId>
        <artifactId>groupdocs-merger</artifactId>
        <version>21.9</version> 
</dependency>
```

## Add Password to PDF in Java - Lock PDF {#lock-pdf-by-password}



{{< figure align=center src="images/locked-PDF.jpg" alt="Lock PDF with Password">}}


Let's quickly jump to add password protection to the PDF files for security. The following steps show how to add a password to PDF documents in Java.

*   Define the password using [AddPasswordOptions][11] class.
*   Load the PDF file using [Merger][12] class.
*   Protect the file by adding password using [addPassword()][13] method.
*   Save the protected file using the [save()][14] method.

The following code snippet adds a password to a PDF file in Java.

{{< gist GroupDocsGists 4be8e5153e84bf9c2d55f74f11f07543 "AddPasswordToPDF.java" >}}

If you try to open the password-protected PDF file, the PDF viewer will ask to enter the password.



{{< figure align=center src="images/enter-pwd-to-protected-pdf-1024x298.png" alt="Enter Password to Protected PDF">}}


## Update Existing Password of PDF Files in Java {#change-pdf-password}

What if your secret is no more a secret? Make it secret again. Let's change the password to a new one. The following steps change the existing password of a PDF file in Java.

*   Set the [loading options][15] using the current password.
*   Now set the [update options][16] using the new password.
*   Load the PDF document using [Merger][17] class and the loading options.
*   Change the existing password using [updatePassword()][18] method.
*   Save the password protected file again with the updated password using the [save()][19] method.

The code snippet changes the current password of the PDF document using Java code.

{{< gist GroupDocsGists 4be8e5153e84bf9c2d55f74f11f07543 "ChangePdfPassword.java" >}}

## Remove Password from PDF Files in Java - Unlock PDF {#remove-password-to-unlock-pdf}



{{< figure align=center src="images/unlocked-PDF.jpg" alt="PDF unlocked - Removed Password">}}


If file protection is not more needed, you can remove the password. The following steps show how to remove the password of a protected PDF file in Java.

*   Prepare the [load options][20] using the existing password.
*   Load the PDF document using [Merger][21] class using load options.
*   Remove its password using [removePassword()][22] method.
*   Save the unlocked file using the [save()][23] method.

The following is the Java code example to remove the password of a PDF file to make it unlocked.

{{< gist GroupDocsGists 4be8e5153e84bf9c2d55f74f11f07543 "RemovePdfPassword.java" >}}

## Get a Free API License

You can [get a free temporary license][24] to use the API without the evaluation limitations.

## Conclusion

To conclude, we discussed the password protection of PDF documents. Initially, we locked the PDF file by adding a password. Then, we changed its password. Lastly, we removed the PDF file password to keep these unlocked. Now you can think about building your own password protector & password remover Java application.

To learn more about GroupDocs.Merger for Java, visit the [documentation][25]. For queries, contact us via the [forum][26].

## See Also

*   [Ways to Split PDF Files in Java][27]
*   [Watermark PDF Files in Java][28]
*   [Password Protection for PDF files using C#][29]







[1]: https://blog.groupdocs.com/category/watermark/
[2]: https://blog.groupdocs.com/?s=password
[3]: #lock-unlock-pdf-java-api
[4]: #lock-pdf-by-password
[5]: #change-pdf-password
[6]: #remove-password-to-unlock-pdf
[7]: https://products.groupdocs.com/merger/java/
[8]: https://docs.groupdocs.com/merger/java/
[9]: https://downloads.groupdocs.com/merger
[10]: https://repository.groupdocs.com/webapp/#/artifacts/browse/tree/General/repo/com/groupdocs
[11]: https://apireference.groupdocs.com/merger/java/com.groupdocs.merger.domain.options/AddPasswordOptions
[12]: https://apireference.groupdocs.com/merger/java/com.groupdocs.merger/Merger
[13]: https://apireference.groupdocs.com/merger/java/com.groupdocs.merger/Merger#addPassword(com.groupdocs.merger.domain.options.interfaces.IAddPasswordOptions)
[14]: https://apireference.groupdocs.com/merger/java/com.groupdocs.merger/Merger#save(java.lang.String)
[15]: https://apireference.groupdocs.com/merger/java/com.groupdocs.merger.domain.options/LoadOptions
[16]: https://apireference.groupdocs.com/merger/java/com.groupdocs.merger.domain.options/UpdatePasswordOptions
[17]: https://apireference.groupdocs.com/merger/java/com.groupdocs.merger/Merger
[18]: https://apireference.groupdocs.com/merger/java/com.groupdocs.merger/Merger#updatePassword(com.groupdocs.merger.domain.options.interfaces.IUpdatePasswordOptions)
[19]: https://apireference.groupdocs.com/merger/java/com.groupdocs.merger/Merger#save(java.lang.String)
[20]: https://apireference.groupdocs.com/merger/java/com.groupdocs.merger.domain.options/LoadOptions
[21]: https://apireference.groupdocs.com/merger/java/com.groupdocs.merger/Merger
[22]: https://apireference.groupdocs.com/merger/java/com.groupdocs.merger/Merger#removePassword()
[23]: https://apireference.groupdocs.com/merger/java/com.groupdocs.merger/Merger#save(java.lang.String)
[24]: https://purchase.groupdocs.com/temporary-license
[25]: https://docs.groupdocs.com/merger
[26]: https://forum.groupdocs.com/
[27]: https://blog.groupdocs.com/2021/10/19/split-pdf-files-in-java/
[28]: https://blog.groupdocs.com/2021/06/26/add-watermark-to-pdf-in-java/
[29]: https://blog.groupdocs.com/2021/11/17/lock-unlock-pdf-files-with-password-using-csharp/

