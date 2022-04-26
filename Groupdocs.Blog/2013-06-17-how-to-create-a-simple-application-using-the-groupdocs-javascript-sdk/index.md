---
title: 'How to Create a Simple Application Using the GroupDocs'' JavaScript SDK'
date: Mon, 17 Jun 2013 08:16:58 +0000
draft: false
url: /2013/06/17/how-to-create-a-simple-application-using-the-groupdocs-javascript-sdk/
author: 'Derek Hyland'
summary: ''
tags: ['API', 'document collaboration', 'document management', 'GroupDocs API', 'GroupDocs API SDK', 'GroupDocs JavaScript SDK', 'javascript', 'zArchive']
---

In this article I'll walk you thorough the process of creating a simple JavaScript application which shows files and directories from your GroupDocs account. Lets start by creating a package from the GroupDocs JavaScript SDK sources. You can skip this step and get [the full SDK package from GitHub](https://github.com/groupdocs) and [a minimal SDK package](https://github.com/groupdocs).

## Creating a Package

1.  You need Node.js installed on you computer. [Read more about installation Node.js](https://github.com/joyent/node/wiki/Installing-Node.js-via-package-manager). When Node.js is on your computer you can start building package.
2.  Let's grab the SDK from github: [https://github.com/groupdocs/groupdocs-javascript](https://github.com/groupdocs).
    
    ```
    git clone git://github.com/groupdocs/groupdocs-javascript.git
    ```
    
    Now you need to install all dependencies.
3.  In the groupdocs-javascript folder start command:
    
    ```
    npm install
    ```
    
    And the final step - building the package:
4.  We will build the SDK with all of its parts, but if you want, you can use specific parts and build a package with only the API that you need. Just edit the file **/groupdocs-javascript/src/index.js**.
    
    ```
    make dist
    ```
    
    You may get an error like:
    
    ```
    stream.js:81
          throw er; // Unhandled stream error in pipe.             ^
    Error: ENOENT, open 'dist/groupdocs-javascript.js'
    make: \*\*\* \[dist\] Error 1
    ```
    

If so, there's an issue with your **dist** directory. Please check that there is such a directory - /groupdocs-javascript/dist/ - and that is it writable. If there was no error you can find your **groupdocs-javascript.js** in the /groupdocs-javascript/dist/ directory. We will use this file in our application.

## Building an Application: First Steps - HTMLThe simplest way to start use GroupDocs Javascript SDK is to create simple HTML file with the following:

```
...
<script src="./groupdocs-javascript.js"></script>
<script>
var clientId = "";
var apiKey = "";
var aClient = new groupdocs.ApiClient(new groupdocs.GroupDocsSecurityHandler(apiKey));
var api = new groupdocs.StorageApi(aClient, "https://dev-api.groupdocs.com/v2.0");

api.GetStorageInfo(function(response) {
     console.log("success callback");
     console.log(response.result);
}, clientId);
</script>
.....
```

If you enter the client ID and API key and start the file in your browser, you will see the following in the console: ![](https://blog.groupdocs.com/wp-content/uploads/sites/4/2013/06/Figure-1.png "Figure 1")

## Building an Application: The ApplicationNow let's start creating the application.

1.  Create an **app.html**file:
    
    ```
    <!DOCTYPE html PUBLIC "-//W3C//DTD HTML 4.01//EN"
            "http://www.w3.org/TR/html4/strict.dtd">
    
    <html xmlns="http://www.w3.org/1999/xhtml" lang="en">
    <head>
        <meta http-equiv="Content-Type" content="text/html; charset=utf-8" />
        <title>GroupDocs JavaScript SDK application</title>
        <meta name="author" content="GroupDocs" />
        <script src="https://ajax.googleapis.com/ajax/libs/jquery/1.8.3/jquery.min.js"></script>
        <script src="./groupdocs-javascript.js"></script>
        <script src="./app.js"></script>
    
    </head>
    <body>
    
    </body>
    </html>
    ```
    
2.  We will use jQuery for the application so include it. Also include the GroupDocs SDK **groupdocs-javascript.js**. **app.js** is a file we'll create for the app.
3.  Create **app.js**in the same directory:
    
    ```
    (function() {
    
        var clientId = "";
        var apiKey = "";
    
        var aClient = new groupdocs.ApiClient(new groupdocs.GroupDocsSecurityHandler(apiKey));
        var api = new groupdocs.StorageApi(aClient, "https://dev-api.groupdocs.com/v2.0");
    
        var getStructure = function (path) {
            path = path || "";
            api.ListEntities(function(response, status, jqXHR) {
                console.log("success callback " + status);
                console.log(response.result);
            }, clientId, path);
        }
    
        var init = function () {
            getStructure();
        }
    
        init();
    
    }());
    ```
    
4.  Enter credentials, start in the browser and you will see in console: ![](https://blog.groupdocs.com/wp-content/uploads/sites/4/2013/06/Figure-2.png "Figure 2")This is what we've done here: 
    *   var getStructure - the method with the API call.
    *   api.ListEntities - returns a list of files and folders from a defined path. Requires two parameters: clientId and path.
    *   path = path || ""; - use an empty string to get the root folder.
    *   var init - here we can define everything we want to do when the app. starts.
    *   init(); - start app.
5.  Now lets add a method which will display the list of folders and files received from GroupDocs API as DOM elements.
    
    ```
    var show\_list = function (list) {
            var folderList = '';
            var fileList = '';
    
            var length = list.folders.length;
            var element = null;
            for (var i = 0; i < length; i++) {
                element = list.folders\[i\];
                folderList += "<li class='directory collapsed'><a href='#' rel='" + element.name + "'>" + element.name + "</a></li>";
            }
    
            var length = list.files.length;
            var element = null;
            for (var i = 0; i < length; i++) {
                element = list.files\[i\];
                fileList += "<li class='file ext\_" + element.file\_type.toLowerCase() + "'><a class='iframe' href='' rel='" + element.guid + "'>" + element.name + "</a></li>";
            }
    };
    ```
    
6.  We will also need somewhere to display this list so add this to the **app.html**file's body:
    
    ```
    <div id="filestructure"></div>
    ```
    
7.  As we need the same for the sub-folders, add this to **var show\_list**:
    
    ```
    $target.append('<ul class="jqueryFileTree" style="">' + folderList + fileList + '</ul>');
    ```
    
8.  Also, we need to update parameters:
    
    ```
    var show\_list = function (list, $target)
    ```
    
9.  Update the initfunction:
    
    ```
    var init = function () {
        var $target = $('#filestructure');
        getStructure($target);
    }
    ```
    
10.  Start the app only after the DOM is ready:
    
    ```
    $(function() {
        init();
    } );
    ```
    
11.  The last thing we need to do is binding actions on folders - to open them and files - just to log in the console file's GUID. To the end of show\_listfunction, add:
    
    ```
    bindEvents($target);
    ```
    
    And here is the bind events function:
    
    ```
    var bindEvents = function($target) {
            $target.find('li a').bind('click', function(){
                if( $(this).parent().hasClass('directory') ) {
                    if( $(this).parent().hasClass('collapsed') ) {
                        // Expand
                        $(this).parent().find('ul').remove(); // cleanup
    
                        getStructure( $(this).parent(), $(this).attr('rel') );
                        $(this).parent().removeClass('collapsed').addClass('expanded');
                    } else {
                        // Collapse
                        $(this).parent().find('ul').slideUp(500);
                        $(this).parent().removeClass('expanded').addClass('collapsed');
                    }
                } else {
                    console.log($(this).attr('rel'));
                }
                return false;
            })
    }
    ```
    

You can add CSS and images to your own taste. **The final app may look like this** ![](https://blog.groupdocs.com/wp-content/uploads/sites/4/2013/06/Figure-3.png "Figure 3") Final [app.html](https://gist.github.com/averjr/fb8ba6ccceeda147e62b) Final [app.js](https://gist.github.com/averjr/d7e6d9cdf13fe2f49d22)




