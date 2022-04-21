---
title: 'Developing Extensions for Google Chrome - GroupDocs Viewer'
date: Tue, 02 Apr 2013 13:34:21 +0000
draft: false
url: /2013/04/02/developing-extensions-for-google-chrome-groupdocs-viewer/
author: 'Derek Hyland'
summary: ''
tags: ['document collaboration', 'document management', 'document upload', 'GroupDocs Viewer', 'GroupDocs Viewer Plugin', 'online document management system', 'online document viewer', 'View documents online', 'zArchive']
---

This article describes how Google Chrome extensions are structured. Also I'll show you how to create one using the [GroupDocs Viewer extension](https://github.com/groupdocs-viewer/) as an example.

## Google Chrome extensionsIn contrast to developing extensions for FireFox, writing extensions for Google Chrome is a rather simple task. Chrome extensions are archives that contain the manifest file, called **manifest.json** and other resource files. The manifest file describes a extension's general information: any pages and scripts it uses, and permissions. Together with the manifest, any files that the extension needs are packed into a \*.crx file and a key file is saved in the \*.pem format.```
{
    "name": "GroupDocs Viewer",
    "version": "1.3",
    "manifest\_version": 2,
    "description": "GroupDocs Viewer plugin for Google Chrome",
    "icons": {
 "16": "./img/icon16.png",
 "48": "./img/icon48.png",
 "128": "./img/icon128.png"
 },
    "browser\_action": {
     "default\_title": "GroupDocs Viewer",
     "default\_icon": "./img/icon16.png",
     "default\_popup": "popup.html"
    },
    "permissions": \[
     "https://api.groupdocs.com/\*",
     "https://dev-api.groupdocs.com/\*"
    \]
}
```

### Manifest ComponentsThe main components of the GroupDocs extension manifest are:

*   **name** - The extension name.
*   **version** - The extension version.
*   **manifest\_version** - The manifest version.
*   **description** - A extension description.
*   **icons** - Any icons the extension uses.
*   **browser\_action** - A description of an icon on the toolbar and a pop-up window.
*   **default\_title** - The name displayed when hovering a cursor over a extension icon.
*   **default\_icon** - The extension's main icon.
*   **default\_popup** - The HTML file loaded into a extension's pop-up window.
*   **permissions** - The extension's permissions. These are sites to which the extension can run Ajax inquiries.

### GroupDocs Viewer ObjectsThe GroupDocs Viewer extension consists of the following objects:

*   DirectoryChoicer - File browser dialog. Used to chose a folder when moving or copying files.
*   StatusManager - An object of notices. Used to of the progress screen and various other messages.
*   EmbedDialog - A dialog of control parameters for generating a embeddable frame. Used for parameters controlling a frame and its generation.
*   GroupDocsManager - An object for working with the GroupDocs account. Superstructure to the GroupDocs JavaScript API. Used for all server operations with GroupDocs.
*   GroupDocsPlugin - The extension object in which all the extension logic is realized.

## How it WorksBelow, I've described how the extension works in some detail.

### Initializing the extension

1.  The extension begins the work by calling the GroupDocsPlugin object's initialize method. In this method, at first the \_initializeEvents method is called and initializes event handlers for all elements for which it is necessary.
2.  After the handler initialization, the authSuccess method is called. This method keeps appCID and appKey as global variables for further use.
3.  After that the contentShowed method is called. First, this clears an area in which files will be displayed, and then it calls the showEntities method. The showEntities method first calls the StatusManager.showProgress method. This displays a progress bar.
4.  The GroupDocsManager.listEntities method is called with a parameter indicating a way to the folder which files need to be returned. When files are loaded from the server, it cycles through files and folders and creates an appropriately formatted element for each.
5.  For folders the GroupDocsPlugin.showEntities method which recursively receives the hierarchy of files and folders is called again.
6.  If there's a mistake, the StatusManager.err method is called and displays an error message.
7.  When all files are displayed in the block of files, the StatusManager.hideProgress method is called and the progress bar hidden.

### Event HandlersWhen the extension is up and running, it reacts to user actions at which event handlers are called:

#### Logging In and Out

*   When a user fills in a login form and clicks the button to enter, the GroupDocsPlugin.onAuthevent runs.
    1.  In an event at first the progress bar is displayed, using the StatusManager.showProgress method.
    2.  The entered appCID and appKey are checked using the GroupDocsManager.isCorrectCredentials method.
    3.  If the entered data is correct, the GroupDocsPlugin.authSuccess method is called and retains the login credentials.
    4.  The data input form is hidden and the main extension window displayed.
    5.  If the entered data not true, an error message is shown.
    6.  At the end of the login process, whether successful or not, the StatusManager.hideProgress method hides the progress bar.
*   If a user clicks **Logout**, the GroupDocsPlugin.onLogout event handler removes the global appCID and appKey variables and displays a form for input of new values (a new login form).
*   If a user clicks the user tabs in a extension window, the GroupDocsPlugin.onTabSwitch event runs to open the corresponding tab.

#### Working with FilesTo work with files, a user selects a file and can then take a variety of actions. The following event handlers controls those actions:

*   If the user clicks **Show**, the GroupDocsPlugin.onShowDocument event creates a preview frame for the chosen file. The frame is displayed in the corresponding tab.
*   When a user clicks **Download**, the GroupDocsPlugin.onDownloadDocument event comes into play. This downloads the selected file using the GroupDocs API.
*   When a user clicks **Rename**, the GroupDocsPlugin.onRenameDocument event runs. This event asks the user to enter a new name directly into an element with an old name. When the user enters a name, the GroupDocsManager.getDocumentMetadata method gets the renamed file's ID and then uses the GroupDocsManager.renameFile method to rename the file on the server.
*   If a user clicks **Find**, the GroupDocsPlugin.findDocument event runs and finds the selected file in the list of files based on the entered GUID. If the files is found, it is automatically allocated in the list.
*   If a user clicks **Copy**, the GroupDocsPlugin.copyDocumentevent kicks in.
    1.  First, a folder browser window is launched using the DirectoryChoicer.show method.
    2.  To the okButtonClick property of the DirectoryChoicer component, the file selection method handler is applied. This handler is called when users selects a folder appointment and clicks **OK**.
    3.  In this case the folder browser is hidden by means of the DirectoryChoicer.hide method and the progress bar - the StatusManager.showProgress method - is displayed.
    4.  By means of the GroupDocsManager.getDocumentMetadata method, it received the file from the server.
    5.  The file is then moved to the chosen folder using the GroupDocsManager.copyFile method.
    6.  The progress bar is hidden.
    7.  If there's a problem, an error message is displayed.
    8.  If the file is copied successfully, the GroupDocsPlugin.contentShowed method loads the changed hierarchy of files from the server and displays it.

*   Clicking **Move** initializes similar code: the GroupDocsManager.moveFile method moves the file instead of copying it.
*   Clicking **Delete** initializes the GroupDocsPlugin.deleteDocumentevent.
    1.  The user is asked to confirm the deletion.
    2.  If they do, the file is removed using the GroupDocsManager.deleteFile method.
    3.  The progress bar is hidden and the process of loading and displaying a hierarchy of classes from the server starts. The GroupDocsPlugin.contentShowed method is used for this purpose.
*   When a user clicks **Embed**, the GroupDocsPlugin.embedDocument event runs. This calls the EmbedDialog.show method, which displays a dialog for controlling and generating a frame for the chosen file.
*   When a user clicks **Upload**, the GroupDocsPlugin.uploadDocumentevent runs to load a file onto the server.
    1.  The progress bar is displayed.
    2.  The selected file is sent to the server by the GroupDocsManager.uploadFile method.
    3.  When the file is sent, the progress bar disappears and the GroupDocsPlugin.contentShowed method updates the list of files.
*   If the user clicks the **Update** button to refresh the list, the GroupDocsPlugin.refreshDocumentList method is called, resetting the list of files by means of the GroupDocsPlugin.contentShowed method.

I won't describe the other objects, as they very simple. Generally, they generate various HTML elements, using a JQuery library, then adds the generated element is into the general DOM model and displays it on screen.

## SummaryTo develop a Google Chrome extension:

1.  Develop the logic and code using HTML, CSS and JavaScript.
2.  Create the manifest file, complete with descriptions and resources.
3.  Test in Chrome.
4.  Package and publish.




