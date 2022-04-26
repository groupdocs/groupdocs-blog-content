---
title: 'Integration for Zapier - How to Create a Custom Trigger'
date: Fri, 18 Jan 2013 15:00:39 +0000
draft: false
url: /2013/01/18/integration-for-zapier-how-to-create-a-custom-trigger/
author: 'Derek Hyland'
summary: ''
tags: ['API', 'GroupDocs', 'GroupDocs API', 'online document storage', 'zArchive']
---

[Zapier](https://zapier.com/) allows seamless integration with dozens of APIs. In this post I'll explain how to create an integration with the GroupDocs Storage API. Put simply the process of integration with Zapier is Read -> Process -> Write. ![Read-Process-Write image](https://blog.groupdocs.com/wp-content/uploads/sites/4/2013/01/Read-Process-Write-image2.png "Read-Process-Write image") The left side of the integration is called a trigger and the right side is an action. The central process simply converts your API response to a format suitable for the write action. We are going to create a trigger for new files. When you upload files to your GroupDocs account, a Zap (Zapier app) gets the file details and sends them (the write action) to one of the supported services. In this example, we'll simply send an email using Gmail. Here is the brief overview of what needs to be done:

1.  Create GroupDocs Storage service.
2.  Add Auth Fields to support GroupDocs URL Signing based authentication.
3.  Create a trigger for the [Storage.ListEntities](http://api.groupdocs.com/v2.0/spec/#%21/storage/ListEntities_GET) operation.
4.  Use Zapier's Javascript API to implement GroupDocs URL Signing.
5.  Test.

#### 1\. Create GroupDocs Storage Service

1.  Go to [https://zapier.com/developer/app/create/](https://zapier.com/).
2.  Fill in the form with following information:
    *   **Title**: GroupDocs Storage
    *   **Description**: Create/Read/Update/Delete users' files and folders.
3.  Click **Save**. A new page is loaded, with the name of the app.

#### 2\. Add Auth Fields

1.  In Zapier, click **Add a new auth field** in the **Auth Fields** section.
2.  Fill in the form with the following information:
    *   **Label**: Client ID
    *   **Key**: client\_id
    *   **Type**: Unicode
    *   **Required**: Yes
    *   **Help text**: Get it from [http://apps.groupdocs.com/My/Manage](http://apps.groupdocs.com/My/Manage)
3.  Click **Save** button.
4.  Now repeat the same steps to add an Auth Field for the API key:
    *   **Label**: API Key
    *   **Key**: private\_key
    *   **Type**: Password
    *   **Required**: Yes
    *   **Help text**: Get it from [http://apps.groupdocs.com/My/Manage](http://apps.groupdocs.com/My/Manage)
5.  Click **Save**.

#### 3\. Create a TriggerThe trigger recognizes that files have been uploaded and passes them to the process. Setting up a trigger involves several steps: adding a new trigger, adding polling info, adding a trigger field and, finally, adding sample results.

1.  Still in Zapier, click **Add a new trigger.** in the **Triggers** section.
2.  Fill in the form with following information:
    *   **Label**: New File
    *   **Key**: new\_file
    *   **Help text**: New file uploaded to GroupDocs.
    *   **Important**: On
    *   **Data Source**: Polling
3.  Click **Save**. The Trigger page is updated so you can enter polling info.
4.  Paste the following into the **Polling: URL Route** field: client\_id/folders/path?order\_by=CreatedOn&order\_asc=False
5.  Click **Save**.

##### 3a. Add Trigger Field for the path Placeholder

1.  Click **Add a new trigger field.** .
2.  Fill in the form with following information:
    *   **Label**: Folder
    *   **Key**: path
    *   **Help text**: Folder path such as "myFolder", also supports nesting as in "my/nested/folder". To get contents of root folder use "/".
    *   **Type**: Unicode
    *   **Required**: Yes

##### 3b. Add sample result

1.  Click the **sample** link in the **Trigger Data Sources** section.
2.  Add the following json:
    
    ```
    {
      "guid": "1a4e925807950d82b4bf55dc86f736b9123a4409fa1ab3583cf69bc4d1d5dd1a",
      "name": "another\_interactiveform.pdf",
      "url": "https://api.groupdocs.com/v2.0/shared/files/1a4e925807950d82b4bf55dc86f736b9123a4409fa1ab3583cf69bc4d1d5dd1a",
      "thumbnail": null,
      "supported\_types": null,
      "access": "Private",
      "file\_type": "Pdf",
      "created\_on": 1352273011483,
      "version": 1,
      "modified\_on": 1352273011483,
      "owner": null,
      "sharers": null,
      "type": "Pdf",
      "id": 18731,
      "dir": false,
      "size": 91134
    }
    ```
    
3.  Click **Save**.
4.  Mark the following fields as important: **created\_on**, **file\_type**, **guid**, **id**, **name** and **size**.

#### 4\. Implement GroupDocs URL Signing

1.  Click the **Edit Your Code** button.
2.  Add the following JavaScript code:
    
    ```
    Check how to implement [GroupDocs URL Signing with JS](https://docs.groupdocs.com/).
    ```
    
    As there is no way to include external JS files from within a JavaScript code, we had to copy the SHA-1 implementation from [https://github.com/Caligatio/jsSHA/blob/release-1.41/src/sha1.js](https://github.com/Caligatio/jsSHA/blob/release-1.41/src/sha1.js).

We also had to change the Content-Type header from "application/json" to "text/html" or the GroupDocs API would try to parse the request body and fail because the GET request doesn't have a body payload.

#### Test the ServiceOur service is ready, now we can test it.

1.  Go to your dashboard and [create new zap](https://zapier.com/app/edit).
2.  Type "GroupDocs" in the search box.
3.  Select the **New File** trigger.
4.  As the action, choose **Gmail - Send Email**.

Once you are done with testing you can submit your service for global activation or enable invite only activation. In the next post I'll describe how to create an action for the GroupDocs Storage API. That is, we'll implement the right side of integration. Please talk to us using our [Live Chat support](http://groupdocs.com/) or [official feedback forum](http://groupdocs.com/Community/Forums/Default.aspx). Stay connected with our blog and newsletter to get updates regarding all GroupDocs enhancements.




