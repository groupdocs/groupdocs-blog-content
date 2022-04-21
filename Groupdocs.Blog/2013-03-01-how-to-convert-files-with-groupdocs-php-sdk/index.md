---
title: 'How to Convert Files with GroupDocs PHP SDK'
date: Fri, 01 Mar 2013 14:11:41 +0000
draft: false
url: /2013/03/01/how-to-convert-files-with-groupdocs-php-sdk/
author: 'Derek Hyland'
summary: ''
tags: ['API', 'document conversion', 'document management', 'GroupDocs Conversion', 'online document management system', 'zArchive']
---

This article explains the basics of using PHP SDK classes and methods. In this article I'll use the Comparison API and show how to [compare two documents](http://groupdocs.com/apps/comparison) from a GroupDocs account. [Find information about others methods in the Swagger explorer](https://api.groupdocs.com/v2.0/spec/).

## Requirements

*   PHP 5.3
*   Apache ModRewrite
*   PHP Curl extension
*   PHP Sockets extension (php\_sockets.dll)
*   GroupDocs [PHP SDK](https://github.com/groupdocs)
*   composer.phar (Download from [http://getcomposer.org/download/](https://getcomposer.org/download/) or use the included version)
*   FatFree framework ([https://github.com/bcosca/fatfree](https://github.com/bcosca/fatfree))

## Initial Installations

1.  Learn how to install the Fatfree framework from their Readme: [https://github.com/bcosca/fatfree](https://github.com/bcosca/fatfree)
2.  Copy all src folders to the web root folder.
3.  Configure **composer.json**to use the required PHP SDK version.
    1.  To download the required version of PHP SDK with the composer, set this setting to **composer.json**:
        
        ```
                  {
                   "require": {
                       "groupdocs/groupdocs-php": "v1.2.4"
                    }
                 }
        ```
        
         
4.  Open a console, cd to the web root folder and run this command:
    
    ```
    php composer.phar install
    ```
    
    (This downloads the GroupDocs PHP SDK into vendor folder and creates **autoload.php**).
5.  Restart Apache.

## Creating the SampleEarlier I wrote about how to configure a sample development environment in the article [Implementation of Comparison API sample with GroupDocs PHP SDK](https://blog.groupdocs.com/). Today let's discuss a very useful function: file convertion. That way, I won't hold up an explanation of structure of the project and other general moments. You probably think that file conversion is very difficult and that you must write a tonne of code, and study a lot of documentation about file formats and how to convert them. Luckily, you are wrong: everything is already done by the GroupDocs team. Everything you need to do is just create a form for entering a couple parameters and a few lines of code to take the parameters from the form and transfer them to the Convert method. Let's look at the part of the sample that will be seen by the user, the form. The screenshot shows how many fields and what data we need. The Client ID and Private Key comes from the [GroupDocs](http://groupdocs.com) account, the file GUID from user storage in GroupDocs. Then chose which type to convert the document to from the list. To make this form, create a **.htm** file in the "templates" folder in the root folder of the project. Last time we called it Sample1 so lets call the new sample Sample2 Here is code of that file:```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta http-equiv="Content-Type" content="text/html; charset=UTF-8"/>
    <title>Powered by {{ @VERSION }}</title>
    <style type="text/css">
        {{ Web::minify('templates/',array('style.css'),FALSE) }}
    </style>
</head>
<body>
<h3 style="text-align:center;"><a href="/index.php">GroupDocs PHP SDK Samples</a> - Sample2</h3>

<div class='samplecontent' style="padding:10px;">
    <i>This sample will show how to convert Doc to Docx, Docx to Doc, Docx to PDF and PPT to PDF using PHP SDK</i> <br/>
    <br />
     <font color="green">You entered: </font>
		ClientID = {{@userId}}
		Private Key = {{@privateKey}}
		File Id = {{@fileId}} 
		Convert type = {{@convert\_type}}
    <br />
    <font color="red">{{@error}}</font>
    <div id="requestForm" style="padding:20px; border:1px solid black;">
         Enter data for request and press "Make request" button 
        <form action="/sample2" method = "post" enctype = 'multipart/form-data'>
            <label for='client\_id'>GroupDocs Client ID</label>
            <br />
            <input type='text', name='client\_id' value="{{@userId}}" />
            <br />
            <label for='private\_key'>GroupDocs Private Key</label>
            <br />
            <input type='text', name='private\_key'  value="{{@privateKey}}" />
            <br />
            <label for='fileId'>FileID</label>
            <br />
            <input type='text', name='fileId'  value="{{@fileId}}" />
            <br />
            <input type='submit' value='Make Request'/>
            <select name="convert\_type" id="convert\_type">
                            <option value="doc">Doc</option>
                            <option value="pdf">PDF</option>
                            <option value="docx">Docx</option>
                            <option value="ppt">PPT</option>
            </select>
        </form>
    </div>
    <div  style="padding:20px; border:1px solid black;">
         Results: 
        {{ @iframe }}
    </div>
</div>

</body>
</html>
```As you can see, this code is almost the same as in the previous sample. It differs only on that that here we have only one field for file GUID and we don't have field for callback URL. Instead, we have a drop-down list with file types. If you need detailed description for the template file you can find it in the [previous article.](https://blog.groupdocs.com/)  So lets take a look at a more interest part, at the controller were we have all the magic. Create a **.php** file in the inc\_samples with same as the template file - "sample2". Here the code of that file:

In the code you'll find comments for each line of code and like the template file, the Controller is very similar to the previous sample. OK let's look at key moments:

*   Here is a declaration of main variables and getting entered data from the form:
    
    ```
     F3::set('userId', '');
        F3::set('privateKey', '');
        F3::set('fileId', '');
        F3::set('convert\_type', '');
        $clientId = F3::get('POST\["client\_id"\]');
        $privateKey = F3::get('POST\["private\_key"\]');
        $fileId = F3::get('POST\["fileId"\]');
        $convert\_type = F3::get('POST\["convert\_type"\]');
    ```
    

*   After we get the entered data, we need to create an Async Api object so we can make request to the GroupDocs API. To create this object, we must create a GroupDocsRequestSigner object and transfer the Private Key to it. Then, that we must take this object and transfer it to the ApiClient object. The code for that looks like this:
    
    ```
                $signer = new GroupDocsRequestSigner($privateKey);
                //Create apiClient object
                $apiClient = new APIClient($signer);
                //Create AsyncApi object
                $api = new AsyncApi($apiClient);
    ```
    

*   And here is the moment of conversion. To convert the file, we need to take the AsyncApi and use its **Convert**method with the data provided via the form:
    
    ```
    $convert = $api->Convert($clientId, $fileId, $convert\_type, null, null, null, null, null)
    ```
    

As you can see, conversion is a one code line operation - all the dirty work has already done by GroupDocs team. After we convert the file, we'll check the conversion results and obtaining conversion result info such as **job\_id** and request status. But we can't receive the new converted file GUID, name and so on at once. To obtain these data, we need to take the received **job\_id** and transfer it to the **GetJobDocuments** method of our AsyncApi object. This method returns all the info we want. In this sample we generate an _iframe_ which will show the converted file. For that reason we need the new file's GUID.  The code looks like so:

```
if($convert->status == "Ok") {
                //Delay necessary that the inquiry would manage to be processed
                sleep(5);
                //Make request to api for get document info by job id
                $jobInfo = $api->GetJobDocuments($clientId, $convert->result->job\_id);
                //Get file guid
                $guid = $jobInfo->result->inputs\[0\]->outputs\[0\]->guid;
                //Generating iframe
                $iframe = '<iframe src="https://apps.groupdocs.com/document-viewer/embed/' . $guid . '" frameborder="0" width="100%" height="600"></iframe>';

            }
            //If request was successfull - set url variable for template
            return F3::set('iframe', $iframe);
```

Lastly, we only need to transfer data which we want to show to the template:

```
    F3::set('userId', $clientId);
    F3::set('privateKey', $privateKey);
    F3::set('fileId', $fileId);
    F3::set('convert\_type', $convert\_type);
    // Process template
    echo Template::serve('sample2.htm');
```




