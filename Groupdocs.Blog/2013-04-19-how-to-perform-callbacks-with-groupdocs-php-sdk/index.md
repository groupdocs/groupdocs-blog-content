---
title: 'How to perform Callbacks with GroupDocs PHP SDK'
date: Fri, 19 Apr 2013 13:25:08 +0000
draft: false
url: /2013/04/19/how-to-perform-callbacks-with-groupdocs-php-sdk/
author: 'Derek Hyland'
summary: ''
tags: ['API', 'document collaboration', 'document management', 'online document management system', 'php api', 'zArchive']
---

This article explains the basics of using PHP SDK callbacks. In this article I'll use the Convert API. [Find information about other methods in the Swagger explorer](https://api.groupdocs.com/v2.0/spec/).

## Requirements

*   PHP 5.3
*   Apache ModRewrite
*   PHP Curl extension
*   PHP Sockets extension (php\_sockets.dll)
*   GroupDocs [PHP SDK](https://github.com/groupdocs)
*   composer.phar (Download from [http://getcomposer.org/download/](https://getcomposer.org/download/) or use the included version)
*   FatFree framework ([https://github.com/bcosca/fatfree](https://github.com/bcosca/fatfree))

We already know how to install the Fatfree framework and prepare for creating the sample from the [previous article](https://blog.groupdocs.com/how-to-convert-files-with-groupdocs-php-sdk). So lets start with the magic.

## TheoryFirst of all let's familiarize ourselves with Callback and the logic we will implement.

### CallbackA callback is something like "Action" in HTML forms, a URL that will be executed by the server when a job is done. In this article we will use the Convert API and Convert method to convert a file from DOC to PDF. One of parameters of this method is a callback URL.

### The logic

1.  User enters data into the form.
2.  The data is transfered by POST to the controller.
3.  The controller processes the received data (converts the file) and writes the user ID and private key to the text file for the Callback handler. After that, the controller returns the converted file GUID to the template.
4.  After conversion, the server calls the callback handler.
5.  The callback handler reads the user ID and private key from text file and makes a request to the Storage API to download the converted file.
6.  At same time that the server calls the callback URL, the template file shows the conversion results in an **iframe** and sends an Ajax request to the Ajax handler.
7.  The Ajax handler checks the "downloads" folder for the downloaded file. If file is there, handler gets the file name and returns it to the template.
8.  If file was downloaded, Ajax also sends a request to the download file handler to generate the download file dialog.

## PracticeNow we must create our files:

*   The first file is the template file in the **template** folder.
*   The second file is the controller which is saved to the **inc\_samples** folder.
*   THe other two files live in the **callbacks** subfolder in the **inc\_samples** folder.

The structure looks like this: ![](https://blog.groupdocs.com/wp-content/uploads/sites/4/2013/04/Figure-11.png "Figure 1") As you can see from screenshot we must create five files:

1.  template.htm
2.  controller.php
3.  convert\_callback.php
4.  check\_file.php
5.  download\_file.php

So let's start in stages.

### template.htmlIn the **template** folder, create the **template.htm** file. This file shows the page with the input form and performs an Ajax request. Now put in this code:```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta http-equiv="Content-Type" content="text/html; charset=UTF-8"/>
    <title>Powered by {{ @VERSION }}</title>
    <style type="text/css">
        {{ Web::minify('templates/',array('style.css'),FALSE) }}
    </style>
	<script src="//ajax.googleapis.com/ajax/libs/jquery/1.9.1/jquery.min.js" ></script>
</head>
<body>

<h3 style="text-align:center;"><a href="/index.php">GroupDocs PHP SDK Samples</a> - Convert</h3>

<div class='samplecontent' style="padding:10px;">
    <span class="description"><i>This sample will show how to convert Doc to Docx, Docx to Doc, Docx and DOC to PDF and PPT to PDF, HTML to DOC and DOCX using PHP SDK</i></span> <br/>
    <br />
    <span class="documentation"><a href="/docs/sample18.html">Docs for this sample</a></span>
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
        <form action="/controller" method = "post" enctype = 'multipart/form-data'>
            <label for='client\_id'>GroupDocs Client ID</label>
            <br />
            <input type='text', name='client\_id' value="{{@userId}}" />
            <br />
            <label for='private\_key'>GroupDocs Private Key</label>
            <br />
            <input type='text', name='private\_key'  value="{{@privateKey}}" />
            <br />
            <label for='private\_key' id="guid">GroupDocs fileID</label>
            <br />
            <input type='text', name='fileId' id="guidfield" value="{{@fileId}}" />
            <br />
            <label for='callbackUrl'>callbackUrl<span class="optional">(Optional)</span></label>
            <br />
            <input type='text', name='callbackUrl'  value="{{@callbackUrl}}" />
            <br />
            <input type='submit' value='Make Request'/>
            <select name="convert\_type" id="convert\_type">
                            <option value="doc">Doc</option>
                            <option value="pdf">PDF</option>
                            <option value="docx">Docx</option>
                            <option value="ppt">PPT</option>
            </select>
            <span id="results\_status" style="color:red;display:none;"> (Please wait for ajax response) </span>
            <div id="link"></div>
        </form>
        <br />
        <iframe id="downloadframe" style="display:none"></iframe>
    </div>
    <div  id="result" style="padding:20px; border:1px solid black;">
         Results: 
        <font color="red">{{@error\_message}}</font>
        <iframe src="{{ @iframe }}"></iframe>
    </div>
</div>

 <script type="text/javascript">
     $(document).ready(setTimeout(check, 5000));

         function check() {

             if (($("input\[name=callbackUrl\]").val() != "") && (document.getElementById("result") != null)) {
                 $('#results\_status').fadeIn("slow");
                 form = document.forms.form;
                 $.ajax({
                     type: 'POST',
                     url: '/callbacks/check\_file',
                     success: function (data) {
                         $('#results\_status').fadeOut("slow");
                         div = document.getElementById("link");
                         p = document.createElement("p");
                         p.innerHTML = "<br /> File " + data + " was downloaded.";
                         div.appendChild(p);
                         $("#downloadframe").attr("src", "/callbacks/download\_file?FileName=" + data);
                     },
                     dataType: "text"
                 });
             }
         }

</script>
</body>
</html>
```  I will not explain the HTML part of this code since it is a usual HTML document. But we have a JavaScript so let's take a look at that. First we must include a Jquery library for Ajax requests. This code in the "Head" is responsible for this:```
<script src="//ajax.googleapis.com/ajax/libs/jquery/1.9.1/jquery.min.js" ></script>
```After that we can use Ajax. Now the Ajax code:```
<script type="text/javascript">
     $(document).ready(setTimeout(check, 5000)); //Wait 5 sec. after page loaded and run "check" function

         function check() {

             if (($("input\[name=callbackUrl\]").val() != "") && (document.getElementById("result") != null)) { //Check is this first time page loaded
                 $('#results\_status').fadeIn("slow"); //Chow message

                //Ajax request
               $.ajax({
                     type: 'POST',                     //Set ajax request type to POST
                     url: '/callbacks/check\_file',     //Action to which send request
                     success: function (data) {        //If request success exeсute function
                         $('#results\_status').fadeOut("slow");     //Show result status
                         div = document.getElementById("link");    //Get element with id "link"
                         p = document.createElement("p");          //Create new HTML element
                         p.innerHTML = "<br /> File " + data + " was downloaded.";          //Set content for new HTML element
                         div.appendChild(p);                                               //Add new element to the element with id "link"
                         $("#downloadframe").attr("src", "/callbacks/download\_file?FileName=" + data);  //Make request to download file\_file controller
                     },
                     dataType: "text"               //Set data type which will get ajax request from controller

                 });
             }
         }

</script>
```  As Jquery is a JavaScript library we must use the <script></script> tag's. This code starts work 5 sec. after the page is loaded. The delay is necessary in order that the iframe with results is loaded. First of all we must check if this is first time the page is loaded. For this reason we use this check:

```
 if (($("input\\\[name=callbackUrl\\\]").val() \\!= "") && (document.getElementById("result") \\!= null)) {
```

After this check, the script shows message and receives all elements from the document. Then the script builds and sends an Ajax request to the **check\_file** controller. When the controller returns the downloaded file name, Ajax sends it to the **download\_file** controller.

### controller.phpNow lets do the next step and see what our base controller looks like. In the **inc\_samples** folder, create a **file \_controller.php** file. This file gets form data from the template and makes requests to the Async API to convert the file. Also this controller creates a text file with the user ID and private key for the callback controllers because we can't send this data any other way and the callback controller will be requested only by the server by the callback URL. Now I'll show you the **controller.php** code. Put it in:```
<?php
    //### This sample will show how to insert Assembly questionnaire into webpage using PHP SDK

    //### Set variables and get POST data
    F3::set('userId', '');
    F3::set('privateKey', '');
    F3::set('fileId', '');
    F3::set('convert\_type', '');
    $clientId = F3::get('POST\["client\_id"\]');
    $privateKey = F3::get('POST\["private\_key"\]');
    $convert\_type = F3::get('POST\["convert\_type"\]');
    $fileGuId = f3::get('POST\["fileId"\]');

    function Convert($clientId, $privateKey, $convert\_type, $fileGuId) {
        if (empty($clientId)|| empty($privateKey) || empty($convert\_type) || empty($fileGuId)) {
            throw new Exception('Please enter all required parameters');
        } else {
            //path to settings file - temporary save userId and apiKey like to property file
            $infoFile = fopen(\_\_DIR\_\_ . '/../user\_info.txt', 'w');
            fwrite($infoFile, $clientId . "\\r\\n" . $privateKey);
            fclose($infoFile);
             //check if Downloads folder exists and remove it to clean all old files
            if (file\_exists(\_\_DIR\_\_ . '/../downloads')) {
                delFolder(\_\_DIR\_\_ . '/../downloads/');
            }
             //Set variables for Viewer
            F3::set('userId', $clientId);
            F3::set('privateKey', $privateKey);
            //###Create Signer, ApiClient and Storage Api objects

            //Create signer object
            $signer = new GroupDocsRequestSigner($privateKey);
            //Create apiClient object
            $apiClient = new APIClient($signer);
            //Create AsyncApi object
            $api = new AsyncApi($apiClient);
            //Create Storage Api object
            $apiStorage = new StorageApi($apiClient);
            //Get entered callback url
            $callbackUrl = f3::get('POST\["callbackUrl"\]');
            F3::set("callbackUrl", $callbackUrl);
            //Make request to api for convert file
            $convert = $api->Convert($clientId, $fileGuId, null, null, null, $callbackUrl, $convert\_type);
            //Check request status
            if($convert->status == "Ok") {
                //Delay necessary that the inquiry would manage to be processed
                sleep(5);
                //Make request to api for get document info by job id
                $jobInfo = $api->GetJobDocuments($clientId, $convert->result->job\_id, "");
                if ($jobInfo->result->inputs\[0\]->outputs\[0\]->guid != "") {
                    //Get file guid
                    $guid = $jobInfo->result->inputs\[0\]->outputs\[0\]->guid;
                } else {
                    throw new Exception('File GuId is empty');
                }
                //Generation of iframe URL using fileGuId
                $iframe = 'http://apps.groupdocs.com/document-viewer/embed/' . $guid . '" frameborder="0" width="100%" height="600"';
            } else {
                $error\_message = $convert->error\_message;
                return f3::set('error\_message', $error\_message);
            }
            //If request was successfull - set url variable for template
            F3::set('fileId', $fileId);
            return F3::set('iframe', $iframe);
        }
    }
    //### Delete downloads folder and all files in this folder
    function delFolder($path) {
        $item = array();
        //Get all items fron folder
        $item = scandir($path);
        //Remove from array "." and ".."
        $item = array\_slice($item, 2);
        //Check is there was files
        if (count($item) > 0) {
            //Delete files from folder
            for ($i = 0; $i < count($item); $i++) {
                $next = $path . "\\\\" . $item\[$i\];
                if (file\_exists($next)) {
                    unlink($next);
                }
            }
        }
        //Delete folder
        rmdir($path);
    }

    try {
        Convert($clientId, $privateKey, $convert\_type, $fileGuId);
    } catch (Exception $e) {
        $error = 'ERROR: ' .  $e->getMessage() . "\\n";
        f3::set('error', $error);
    }
    F3::set('userId', $clientId);
    F3::set('privateKey', $privateKey);
    F3::set('convert\_type', $convert\_type);
    // Process template
    echo Template::serve('template.htm');
```  I won't go through the code in detail: each line is explained in the comments. But I'll explain briefly what the code doing. We have two functions, Convert and delFolder, which do all the work. First of all, we receive POST data from the template and check if all the required fields are filled in. If they are, the controller creates a text file and writes the user ID and private key to it. After that follows the creation of the GroupDocsRequestSigner, APIClient and Async API objects so that we can send request to the API. So we have created all the objects and now we can convert the file. To do this we only need to call the convert method and transfer to it the:

*   user ID,
*   GUID of the file in the [GroupDocs](http://groupdocs.com/) account which will be converted
*   callback URL
*   format to convert the file to.

Now we have converted the file but we need the GUID of the converted file and only the job ID is returned from the converted method. No problem, lets take 5 sec. to rest. The 5 sec. delay is necessary so that the inquiry can be be processed. After the delay, we take the returned job ID and make new request to the Async API but now with GetJobDocuments which returns all the info we need by job ID. Now we have the GUID for the converted file and can give this GUID to the iframe URL and return the URL to the template which will use it in the iframe source. The second function checks the **downloads** folder for old files and deletes them.

### convert\_callback.phpNext, let's take a look at the callback controller, **convert\_callback.php**. This file gets the callback from server, takes the data the server sends and downloads the converted file.```
<?php
    //Local path to the text file with user data
    $userInfo = file(\_\_DIR\_\_ . '/../../user\_info.txt');
    //Get user data from text file
    $clientId = $userInfo\[0\];
    $privateKey = $userInfo\[1\];
    //Get raw data
    $json = file\_get\_contents("php://input");
    //Decode json with raw data to array
	$callBack\_data = json\_decode($json, true);
    //Get job id from array
	$jobId = $callBack\_data\["SourceId"\];

    //Create signer object
    $signer = new GroupDocsRequestSigner(trim($privateKey));
    //Create apiClient object
    $apiClient = new APIClient($signer);
    //Create AsyncApi object
    $api = new AsyncApi($apiClient);
    //Create Storage Api object
    $apiStorage = new StorageApi($apiClient);
	sleep(5);
    //Make request to Async API to get job info
	$jobInfo = $api->GetJobDocuments(trim($clientId), $jobId, "");
	if ($jobInfo->status == "Ok") {
		   //Get file guid
            $guid = $jobInfo->result->inputs\[0\]->outputs\[0\]->guid;
            //Get file name
            $name = $jobInfo->result->inputs\[0\]->outputs\[0\]->name;

    }
    //Local path to the downloads folder
    $downloadFolder = dirname(\_\_FILE\_\_). '/../../downloads';
    //Check is folder exist
    if (!file\_exists($downloadFolder)) {
        //If folder don't exist create it
        mkdir($downloadFolder);
    }
    //Obtaining file stream of downloading file and definition of folder where to download file
    $outFileStream =  FileStream::fromHttp($downloadFolder, $name);
    //Download file from GroupDocs.
    $download = $apiStorage->GetFile(trim($clientId), $guid, $outFileStream);

?>
```This controller reads the user ID and private key from the text file. Then it gets the raw data from the server inquiry. In this raw data we have the job ID. Use this like in the previous controller to get the converted file. To do this we must create all the objects again: GroupDocsRequestSigner, APIClient and Async API. After that we can make a request using the GetJobDocuments method to get the file GUID and name. Use this data for the GetFile method to download the converted file to the **downloads** folder.

### check\_file.phpAt the same time that the **convert\_callback** controller is working, we see that the page is reloaded and shows the iframe with the converted file. When the iframe is loaded, Ajax sends its request to the **check\_file** controller. The **check\_file** controller looks like this:```
<?php

    $result = "";
    //counter to not wait forever
    $counter = 0;
    //Local path to the downloads folder
    $downloadFolder = \_\_DIR\_\_ . '/../../downloads';
	//Check folder for downloaded file
    do {
        //Set max. iterations
        if ($counter >= 10) {
            $result = "Error";
            break;
        }
        sleep(5);
        //Check is downloads folder exist
        if (!file\_exists($downloadFolder)) {
            //If folder don't exist create it
            $di = mkdir($downloadFolder);
        }
        //Open downloads folder
        $filePaths = opendir($downloadFolder);
        //Get all elements from folder
        while (($file = readdir($filePaths)) !== false) {
            //Get downloaded file name
            if ($file != "." && $file != "..") {
                $name = $file;
            }
        }
        //Close folder
        closedir($filePaths);
        //Check is file downloaded
        if ($name == "") {
            //If file don't downloaded yet do one mor itaretion
            $counter++;
            continue;
        //If file downloaded get file name and break.
        } else {

            $result = $name; //get the name of the fist file in the directory
            break;
        }
    } while (true);
    //Check result
    if ($result == "Error") {
         return "File was not found. Looks like something went wrong.";
    }
	//Return file name to the template for ajax
    echo $result;
?>
```This controller opens the **downloads** folder and gets all files from it. If there are no files, the controller waits for 5 sec. and checks again. When the file is downloaded and appear in the folder, the controller get the name and returns it to Ajax which sends the file name to the **download\_file** controller.

### download\_file.phpThe **download\_file** generates the download dialog.```
<?php
//Get downloaded file
$file = (dirname(\_\_FILE\_\_) . '/../../downloads/' . $\_GET\["FileName"\]);
//Set data for download dialog
header ("Content-Type: application/octet-stream");
header ("Accept-Ranges: bytes");
header ("Content-Length: ".filesize($file));
header ("Content-Disposition: attachment; filename=".$\_GET\["FileName"\]);
//Download file
readfile($file);
?>
```Here we take full local path to the downloaded file and transfers it to the download dialog.

## Program in actionOn that we are finished! Let me show you what it looks like in action: \[caption id="attachment\_2068" align="alignnone" width="602" caption="The input form"\]![The input form](https://blog.groupdocs.com/wp-content/uploads/sites/4/2013/04/The-input-form.png "The input form")\[/caption\]   \[caption id="attachment\_2069" align="alignnone" width="602" caption="Ajax message"\]![Ajax message](https://blog.groupdocs.com/wp-content/uploads/sites/4/2013/04/Ajax-message.png "Ajax message")\[/caption\] \[caption id="attachment\_2070" align="alignnone" width="602" caption="Iframe with converted file"\]![Iframe with converted file](https://blog.groupdocs.com/wp-content/uploads/sites/4/2013/04/Iframe-with-converted-file.png "Iframe with converted file")\[/caption\]   \[caption id="attachment\_2089" align="alignnone" width="602" caption="Download dialog (FireFox)"\]![Download dialog (FireFox)](https://blog.groupdocs.com/wp-content/uploads/sites/4/2013/04/Download-dialog-FireFox1.png "Download dialog (FireFox)")\[/caption\]




