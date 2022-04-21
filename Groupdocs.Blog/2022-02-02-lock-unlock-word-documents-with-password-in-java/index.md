---
title: 'How to Password Protect and Remove Protection from Word Documents in Java'
date: Wed, 02 Feb 2022 08:45:00 +0000
draft: false
url: /2022/02/02/lock-unlock-word-documents-with-password-in-java/
author: 'Shoaib Khan'
summary: 'Earlier we restricted the access to [PDF documents](https://blog.groupdocs.com/2021/12/07/password-protect-pdf-files-in-java/) by applying passwords. In this article, we will see **how to password protect Word documents in Java**. Further, we will also learn to **change the existing password** of DOC & DOCX files, and lastly, **how to remove the password protection to unlock** Word documents within the Java applications.'
tags: ['Add Password in Java', 'Change Password in Java', 'Lock Files in Java', 'Lock Word Files in Java', 'Password Protect Word Documents', 'Remove Password in Java']
categories: ['GroupDocs.Merger Product Family']
---

Earlier we restricted the access to [PDF documents](https://blog.groupdocs.com/2021/12/07/password-protect-pdf-files-in-java/) by applying passwords. In this article, we will see **how to password protect Word documents in Java**. Further, we will also learn to **change the existing password** of DOC & DOCX files, and lastly, **how to remove the password protection to unlock** Word documents within the Java applications.



{{< figure align=center src="images/lock-unlock-word-documents-in-java.jpg" alt="Password Protect Word Documents in Java">}}


The following topics are covered below:

*   [Java API for to Lock/Unlock Word Documents](#java-api-lock-unlock-documents)
*   [Add Password to Word Document](#password-protect-document)
*   [Change Password of Word Document](#change-password)
*   [How to Remove Password from Word Document](#remove-password-to-unlock)

## Java API to Lock/Unlock Word Documents {#java-api-lock-unlock-documents}

[GroupDocs.Merger](https://products.groupdocs.com/merger/) showcases the Java API that allows locking and unlocking of Word documents within the Java applications. We will use [GroupDocs.Merger for Java](https://products.groupdocs.com/merger/java/) to add the password to Word files, change it, and also remove password protection from the Word files in Java.

You can download the **JAR** file from the [downloads section](https://downloads.groupdocs.com/merger) or use the latest repository and dependency [Maven](https://repository.groupdocs.com/webapp/#/artifacts/browse/tree/General/repo/com/groupdocs) configurations within your Java applications.

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

For more details about the API and about the other supported document formats, you can visit the [documentation](https://docs.groupdocs.com/merger/java/) and the [GitHub repository](https://github.com/groupdocs-merger) for the source code examples.

## Password Protect Word Document in Java {#password-protect-document}



{{< figure align=center src="images/locked-DOC.jpg" alt="Programmatically Locked Word Doc">}}


Let’s start with adding a password to the MS Word DOCX file for security. The following steps show how to add a password to Word documents in Java.

*   Define the password using [AddPasswordOptions](https://apireference.groupdocs.com/merger/java/com.groupdocs.merger.domain.options/AddPasswordOptions) class.
*   Load the DOCX file using the [Merger](https://apireference.groupdocs.com/merger/java/com.groupdocs.merger/Merger) class.
*   Make it password-protected using [addPassword()](https://apireference.groupdocs.com/merger/java/com.groupdocs.merger/Merger#addPassword(com.groupdocs.merger.domain.options.interfaces.IAddPasswordOptions)) method.
*   Save the protected file using the appropriate [save()](https://apireference.groupdocs.com/merger/java/com.groupdocs.merger/Merger#save(java.lang.String)) method.

The following Java code snippet adds a password to a MS Word DOCX file.

{{< gist GroupDocsGists 7896b4529c25d419b78b95469e8fe257 "AddPasswordToDoc.java" >}}

Now, whenever you try to open the password-protected document, the document viewer & editor asks for the password to open the file.



{{< figure align=center src="images/enter-pwd-to-open-protected-word-doc.jpg" alt="Enter Password to Open Protected Word Document">}}


## Change Existing Password of Word Document in Java {#change-password}

Let’s change the password with a new one. The following steps change the existing password of the Word file in Java.

*   Set the [loading options](https://apireference.groupdocs.com/merger/java/com.groupdocs.merger.domain.options/LoadOptions) using the current password.
*   Now define the new password using [password update options](https://apireference.groupdocs.com/merger/java/com.groupdocs.merger.domain.options/UpdatePasswordOptions).
*   Load the protected Word document using [Merger](https://apireference.groupdocs.com/merger/java/com.groupdocs.merger/Merger) class and the defined loading options.
*   Use [updatePassword()](https://apireference.groupdocs.com/merger/java/com.groupdocs.merger/Merger#updatePassword(com.groupdocs.merger.domain.options.interfaces.IUpdatePasswordOptions)) method to apply the new password.
*   Save the password protected file again using the [save()](https://apireference.groupdocs.com/merger/java/com.groupdocs.merger/Merger#save(java.lang.String)) method.

The following code snippet changes the current password of the Word document using Java.

{{< gist GroupDocsGists 7896b4529c25d419b78b95469e8fe257 "ChangeDocPassword.java" >}}

## Remove Password from Word Document in Java {#remove-password-to-unlock}

If the document is no more confidential and the file protection is not required, you can simply remove the password. The following steps show how to remove the password of a protected Word file in Java.

*   Load the protected Word document using [Merger](https://apireference.groupdocs.com/merger/java/com.groupdocs.merger/Merger) class and the existing password.
*   Remove its password using [removePassword()](https://apireference.groupdocs.com/merger/java/com.groupdocs.merger/Merger#removePassword()) method.
*   Save the unlocked DOCX file using the [save()](https://apireference.groupdocs.com/merger/java/com.groupdocs.merger/Merger#save(java.lang.String)) method.

The following is the Java code example that removes the password of a Word file to make it unlocked/unprotected.

{{< gist GroupDocsGists 7896b4529c25d419b78b95469e8fe257 "RemoveDocPassword.java" >}}

## Get a Free API License

You can [get a free temporary license](https://purchase.groupdocs.com/temporary-license) to use the API without the evaluation limitations.

## Conclusion

Let’s sum up what we discussed above. Using a simple Word document, we locked it with a password using Java example. Next, we learned to change the existing password. Lastly, we removed the password of the Word file to make it unlocked within any Java application.

To learn more about **GroupDocs.Merger for Java**, visit its [documentation](https://docs.groupdocs.com/merger) to start building your own document protector or password remover applications for various [supported document formats](https://docs.groupdocs.com/merger/net/supported-document-formats/). For queries, contact us via the [forum](https://forum.groupdocs.com/).

## See Also

*   [Pa of PDF Files in Java](https://blog.groupdocs.com/2021/12/07/password-protect-pdf-files-in-java/)
*   [Different Ways to Split PDF Files in Java](https://blog.groupdocs.com/2021/10/19/split-pdf-files-in-java/)
*   [Find and Replace Words in Documents using Java](https://blog.groupdocs.com/2021/09/01/find-and-replace-text-in-documents-using-java/)
*   [Merge Multiple File Types into One using Java](https://blog.groupdocs.com/2021/06/13/merge-multiple-file-types-using-java/)




