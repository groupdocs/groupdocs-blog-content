---
title: 'Password Protection of PowerPoint Presentations in Java'
date: Thu, 10 Feb 2022 10:00:00 +0000
draft: false
url: /2022/02/10/lock-unlock-ppt-pptx-files-with-password-in-java/
author: 'Shoaib Khan'
summary: 'Protection is important for confidential and private documents. In this article, we will see **how to lock **PowerPoint presentation files** with a password in Java**. Further, we will learn to unlock presentation files by **removing their password** and also **how to change the existing password** of PPT & PPTX files.'
tags: ['Add Password to PPT in Java', 'Change PPT Password in Java', 'Lock PPT in Java', 'Remove Password in Java', 'Unlock PPT in Java']
categories: ['GroupDocs.Merger Product Family']
---

Protection is important for confidential and private documents. In this article, we will see **how to lock **PowerPoint presentation files** with a password in Java**. Further, we will learn to unlock presentation files by **removing their password** and also **how to change the existing password** of PPT & PPTX files.



{{< figure align=center src="images/password-protect-lock-unlock-presentations-in-java.jpg" alt="Password Protect Presentations - Lock Unlock PPT-PPTX in Java">}}


The following topics are discussed below:

*   [Java API to Protect PowerPoint PPT/PPTX with Password](#lock-unlock-ppt-java-api)
*   [Lock PowerPoint Files by adding Password](#lock-ppt-by-password)
*   [Change PPT/PPTX Password](#change-ppt-password)
*   [How to Remove Presentation Passwords](#remove-password-to-unlock-ppt)

## Java API to Lock and Unlock PowerPoint Files {#lock-unlock-ppt-java-api}

In order to deal with the protection of presentation files, we will use the Java API of [GroupDocs.Merger](https://products.groupdocs.com/merger/). The API provides the add, change, and remove password protection features for presentations and other documents.

### Download and Configure

Get the library from the [downloads](https://downloads.groupdocs.com/merger/) section. For your Maven-based Java application, just add the following pom.xml configuration. After this, you can try the examples of this article as well the many more example available on [GitHub](https://github.com/groupdocs-merger). For the details, you may visit the [API Reference](https://apireference.groupdocs.com/merger/java).

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

## Add Password to PowerPoint Files in Java - Lock PPT/PPTX {#lock-ppt-by-password}



{{< figure align=center src="images/locked-PPT.jpg" alt="Lock PPT with Password">}}


You can lock any presentation file easily by adding a password to it programmatically. The following steps show how to add a password to any PowerPoint presentation (PPT/PPTX) file in Java.

*   Set the password using the [AddPasswordOptions](https://apireference.groupdocs.com/merger/java/com.groupdocs.merger.domain.options/AddPasswordOptions).
*   Load the presentation file using the [Merger](https://apireference.groupdocs.com/merger/java/com.groupdocs.merger/Merger) class.
*   Apply the password using  [addPassword()](https://apireference.groupdocs.com/merger/java/com.groupdocs.merger/Merger#addPassword(com.groupdocs.merger.domain.options.interfaces.IAddPasswordOptions)) method.
*   Save the protected presentation using the [save()](https://apireference.groupdocs.com/merger/java/com.groupdocs.merger/Merger#save(java.lang.String)) method.

The following Java code snippet locks the presentation by adding a password to the PPT file.

{{< gist GroupDocsGists 2d6b10d0eef716edbafed867e9fb7e1d "AddPasswordToPpt.java" >}}

When you try to open the output file obtained from the above code, the editor or viewer will ask for the password while opening the presentation.



{{< figure align=center src="images/enter-pwd-to-protected-pptx-presentation.png" alt="Enter Password to Protected PPTX">}}


## Update Existing Password of PPT/PPTX Files in Java {#change-ppt-password}

If you have doubt that your password is glanced at by someone. You can change it easily. The following steps allow you to change the existing password of the presentation file in Java.

*   Prepare the [loading options](https://apireference.groupdocs.com/merger/java/com.groupdocs.merger.domain.options/LoadOptions) using the **current** password.
*   Set the [update options](https://apireference.groupdocs.com/merger/java/com.groupdocs.merger.domain.options/UpdatePasswordOptions) using the **new** password.
*   Load the presentation using the [Merger](https://apireference.groupdocs.com/merger/java/com.groupdocs.merger/Merger) class.
*   Now, change the password using the [updatePassword()](https://apireference.groupdocs.com/merger/java/com.groupdocs.merger/Merger#updatePassword(com.groupdocs.merger.domain.options.interfaces.IUpdatePasswordOptions)) method.
*   Finally, call [save()](https://apireference.groupdocs.com/merger/java/com.groupdocs.merger/Merger#save(java.lang.String)) method to save the locked file.

Here is the Java code snippet that changes the existing password with a new one of a PowerPoint PPT/PPTX presentation.

{{< gist GroupDocsGists 2d6b10d0eef716edbafed867e9fb7e1d "ChangePptPassword.java" >}}

## Remove Password of Presentation in Java - Unlock PPT/PPTX {#remove-password-to-unlock-ppt}



{{< figure align=center src="images/unlocked-PPT.jpg" alt="Unlock PPT - Password Removed">}}


Let's remove the protection and let everyone access the file. Just, open the file and then remove its password for public access. The following steps show how to unlock the PPT file by removing the password in Java.

*   Prepare the [loading options](https://apireference.groupdocs.com/merger/java/com.groupdocs.merger.domain.options/LoadOptions) using the latest password.
*   **Load** the PowerPoint PPT/PPTX file using the [Merger](https://apireference.groupdocs.com/merger/java/com.groupdocs.merger/Merger) class.
*   **Remove** the password using the [removePassword()](https://apireference.groupdocs.com/merger/java/com.groupdocs.merger/Merger#removePassword()) method.
*   **Save** the unlocked file using the [save()](https://apireference.groupdocs.com/merger/java/com.groupdocs.merger/Merger#save(java.lang.String)) method.

The following Java code sample removes the password from the PowerPoint presentation file to keep it unlocked.

{{< gist GroupDocsGists 2d6b10d0eef716edbafed867e9fb7e1d "RemovePptPassword.java" >}}

## Get a Free API License

You can [get a free temporary license](https://purchase.groupdocs.com/temporary-license) to use the API without the evaluation limitations.

## Conclusion

Let's sum up what we learned today. We used a PowerPoint presentation (PPTX) and first, we added a password to it to get it locked. Next, we changed its existing password. Lastly, we learned how to remove the password of the protected PowerPoint file in Java.

To learn more about GroupDocs.Merger for Java, visit the [documentation](https://docs.groupdocs.com/merger). It will help you develop your own applications to lock and unlock presentation files. For queries, contact us via the [forum](https://forum.groupdocs.com/).

## See Also

*   [Watermark PowerPoint files in Java](https://blog.groupdocs.com/2021/06/09/watermark-presentation-slides-using-java/)
*   [Watermark Password Protected Documents in Java](https://blog.groupdocs.com/2021/11/26/watermark-password-protected-documents-in-java/)
*   [Insert OLE Objects in Word, Excel, PowerPoint using Java](https://blog.groupdocs.com/2020/10/19/insert-ole-objects-in-word-excel-powerpoint-with-java/)
*   [Convert Presentations to Images in Java](https://blog.groupdocs.com/2022/01/18/convert-presentations-to-images-in-java/)
*   [Convert Presentations to PDF in Java](https://blog.groupdocs.com/2021/02/15/convert-presentations-odp-pptx-ppt-to-pdf-in-java/)




