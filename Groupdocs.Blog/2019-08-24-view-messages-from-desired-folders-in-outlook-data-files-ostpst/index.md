---
title: 'View messages from desired folders in Outlook Data Files (OST/PST)'
date: Sat, 24 Aug 2019 11:46:29 +0000
draft: false
url: /2019/08/24/view-messages-from-desired-folders-in-outlook-data-files-ostpst/
author: 'Usman Aziz'
summary: ''
tags: ['Document viewer API', 'Email viewer', 'File viewer', 'Office Viewer']
categories: ['GroupDocs.Viewer for .NET Releases', 'GroupDocs.Viewer Product Family']
---



{{< figure align=center src="images/groupdocs-viewer-for-java_logo-e1566819687432.png" alt="">}}


Hello everyone! Today, I am quite excited to announce that [GroupDocs.Viewer for Java](https://products.groupdocs.com/viewer/java) **19.8** has been released with 20+ new features, improvements, and bug fixes. Although every new feature in this version has its own importance, I have picked a few interesting but useful features for you. So in this post, I am going to give you an overview of how to work with the folders contained by Outlook Data Files (OST/PST) and use the message filters to render selective Outlook messages.

In the previous versions of the API, we already have the feature of rendering all the messages from the Outlook Data Files. But there could be the case when you need to render the messages from a specified folder. Also, what if you want to render the only messages you have received from a particular email address? These are the questions that I'll answer today.

First of all, let me give you a brief overview of the Outlook Data Files and the message folders.

The Outlook uses OST and PST files to store the local copy of all the information when you set up your email account. Have a look at how Microsoft defines both of these data files:

> **Outlook Data File (.pst)** - An Outlook Data File (.pst) contains your messages and other Outlook items and is saved on your computer.
> 
> **Offline Outlook Data File (.ost)** - Most other account types, such as IMAP accounts, Office 365 accounts, Exchange accounts, and Outlook.com accounts use an Offline Outlook Data File (.ost) file to store a synchronized copy of your mailbox information on your local computer.  
> ([read more](https://support.office.com/en-us/article/introduction-to-outlook-data-files-pst-and-ost-222eaf92-a995-45d9-bde2-f331f60e2790))
> 
> Microsoft

Now let's come to the Outlook folders. MS Outlook manages your messages in different folders such as _Inbox_ for incoming messages, _Sent items_ for the messages you send and so on. Along with the default message folders, you can also create new folders to organize the messages in the way you want. For example, you can create a separate folder to keep the messages from a particular organization or a person. Have a look at the following image which shows different folders in the Outlook:



{{< figure align=center src="images/FolderList-1.jpg" alt="">}}


Now you would have got the idea of Outlook Data Files and the folder they contain. Let's move on to the features that we have introduced to deal with the Outlook folders and the messages.

#### _**Retrieving the list of Outlook folders**_ {#id-11.RenderingMSOutlookdocuments-RetrievinglistofOutlookfolders}

Before rendering the messages from a specific folder, you must know the names of all the folders the data file contains. Once you have got the list, you can select a folder and render the messages from it. For this, the API provides _OutlookDocumentInfoContainer.getFolders()_ method which returns a list of the folder names. This is how you can do it using the code:

{{< gist GroupDocsGists 75ef4800f825ce5a65eea78c975c88c7 "GetListOfOutlookFolders.java" >}}

There might be the case when you want to get the list of subfolders from a specific folder e.g. _Inbox_. In that case, you just need to specify the folder's name using _DocumentInfoOptions.getOutlookOptions().setFolderName()_ and the rest of the code will remain the same.

{{< gist GroupDocsGists 75ef4800f825ce5a65eea78c975c88c7 "GetListOfSubFolders.java" >}}

#### _**Rendering messages from a specified folder**_ {#id-11.RenderingMSOutlookdocuments-Renderingmessagesfromspecifiedfolderonly}

Now when you have got the list of the folders, you can render the messages from a particular folder. This is again as easy as pie. Just mention the folder's name in the _HtmlOptions_ or _ImageOptions_ and call _getPages()_ method. Have a look at the complete code:

{{< gist GroupDocsGists 75ef4800f825ce5a65eea78c975c88c7 "RenderMessagesFromSpecifiedFolder.java" >}}

In case you want to render the folder's content as a PDF document, you will specify the folder's name in _PdfFileOptions_ and call the _getPdfFile()_ method (as shown below).

{{< gist GroupDocsGists 75ef4800f825ce5a65eea78c975c88c7 "RenderMessagesFromSpecifiedFolderAsPDF.java" >}}

This is what you would get in the rendering result:



{{< figure align=center src="images/RenderFolder-1024x392.jpg" alt="">}}


#### _**Filtering messages to be rendered**_

Another important feature we have introduced is filtering the messages that you want to render. With this feature, you can select the messages by applying the following filters:

*   _Text filter_ - To filter messages by subject and content of the message.
*   _Address Filter_ - To filter messages by sender's and recipient's email addresses.

You can set these filters using _setTextFilter()_ and _setAddressFilter()_ methods of _HtmlOptions_, _ImageOptions_, and _PdfFileOptions_ classes. Suppose, you want to render all the messages that contain the word 'Susan' in the subject or the body. In that case, you will set the text filter to 'Susan' in the following way:

{{< gist GroupDocsGists 75ef4800f825ce5a65eea78c975c88c7 "FilterOutlookMessagesByText.java" >}}

Similarly, you can apply the address filter to get the messages based on the sender's or the recipient's email address.

Well, you have seen how easy it is to view the folders as well as the messages from the Outlook Data Files using GroupDocs.Viewer for Java 19.8. This is it from my side. For a full list of new features, improvements, and fixes, please have a look at the [release notes](https://docs.groupdocs.com/display/viewerjava/GroupDocs.Viewer+for+Java+19.8+Release+Notes). Try out the API features yourself by downloading and running the examples [project](https://github.com/groupdocs-viewer/GroupDocs.Viewer-for-Java/tree/master/Examples). For more details on each feature of the API, have a look at the [documentation](https://docs.groupdocs.com/display/viewerjava/Developer+Guide).

As always we look forward to connecting with you via the [GroupDocs Forum](https://forum.groupdocs.com/categories).




