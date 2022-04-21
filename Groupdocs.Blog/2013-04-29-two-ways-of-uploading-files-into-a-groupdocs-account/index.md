---
title: 'Two Ways of Uploading Files into a GroupDocs Account'
date: Mon, 29 Apr 2013 16:02:14 +0000
draft: false
url: /2013/04/29/two-ways-of-uploading-files-into-a-groupdocs-account/
author: 'Derek Hyland'
summary: ''
tags: ['API', 'document collaboration', 'document management', 'online document management system', 'php api', 'zArchive']
---

Working with GroupDocs SDK we usually need a GUID to work with a document. But it's not very comfortable for users to work with GUIDs. So in your app, you can use two methods to upload a file to a GroupDocs account and get it's GUID programmatically.

## Requirements

*   PHP 5.3
*   Apache ModRewrite
*   PHP Curl extension
*   PHP Sockets extension (php\_sockets.dll)
*   [GroupDocs PHP SDK](https://github.com/groupdocs)
*   composer.phar (Download from [http://getcomposer.org/download/](https://getcomposer.org/download/) or use the included version.)
*   FatFree framework ([https://github.com/bcosca/fatfree](https://github.com/bcosca/fatfree))

We already know how to install the Fatfree framework and prepare for creating the sample from [the previous article](https://blog.groupdocs.com/how-to-convert-files-with-groupdocs-php-sdk). So lets start with the magic.

## Theory

### Upload local fileTo upload a local file we need an actual file. You can view many types to word processing documents (DOC, DOCX, TXT, RTF, ODT), presentations (PPT, PPTX), spreadsheets (XLS, XLSX), portable files (PDF), and image files (JPG, BMP, GIF, TIFF). From GroupDocs PHP SDK we will need the following methods:

*   Upload
*   FileStream::fromFile

The template is simply an HTML form of the "multipart/form-data" type. This form sends date entered by the user (the client ID, private key and local file data) to the controller. The controller, in turn, gets the data, prepares it for an API request, makes the API request and receives the upload results from the API with info about the uploaded file.

### Upload file from webIf you think this is going to be complicated, I have to disappoint you. With GroupDocs PHP SDK it's really simple than upload a local file. To upload a file from the web, we need a direct link to the file. Everything else is the same as when uploading a local file, with the exception of the upload method. To do this trick we need only one method: uploadWeb. The logic of web uploading is the same as for local file upload. Since the logic is the same we'll use same template and controller.

## PracticeAs before, create a template file in the **template** folder and a controller file in the **inc\_samples** folder.

### Template file code```
<!DOCTYPE html>
<html lang="en">
<head>
	<meta http-equiv="Content-Type" content="text/html; charset=UTF-8"/>
	<title>Upload</title>
	<style type="text/css">
		{{ Web::minify('templates/',array('style.css'),FALSE) }}
	</style>
</head>
<body>
<h3 style="text-align:center;"><a href="/index.php">GroupDocs PHP SDK Samples</a> - Upload</h3>

<div class='samplecontent' style="padding:10px;">
   <span class="description"><i>This sample will show how to upload file to GroupDocs using PHP SDK</i></span> <br/>
    <br />

   <br/>You entered:
   ClientID = {{@userId}}
   PrivateKey = {{@privateKey}}
   <font color="red">{{@error}}</font>
   <div id="requestForm" style="padding:20px; border:1px solid black;">

   <form action="controller" method = "post" enctype = 'multipart/form-data'>
       <label for='client\_id'>GroupDocs ClientID</label>
       <br />
       <input type='text' name='client\_id' value="{{@userId}}" />
       <br />
       <label for='private\_key'>GroupDocs PrivateKey</label>
       <br />
       <input type='text' name='private\_key'  value="{{@privateKey}}" />
       <br />
       <input type="radio" name="sourse" value="local" id="localField" onClick="display('local');" >Upload local file </input>
       <br />
       <input type="radio" name="sourse" value="url" id="urlField" onClick="display('url');" >Upload file from URL </input>
       <br />

       <label for='private\_key' style="display:none;" id="url">Upload file from URL</label>
        <br />
        <input type='text' name='url'  value="" id="urlfield" style="display:none;" />

        <label for='file' id="file" style="display:none;">Upload local file</label>
        <br />
        <input type='file' name='file' id="filefield" style="display:none;" />
        <br />
       <label for='private\_key'>Folder in which you want to copy file</label>
       <br />
       <input type='text' name='destPath'  value="{{@folder}}" />
       <br />
       <input type='submit' value='Make Request'/>
   </form>
   </div>
   <h4><font color="green">{{@message}}</font></h4>
   <br/>
 </div>

 <include href="links.htm" />
 <script type="text/javascript">
    function display(\_element\_id) {

             if (\_element\_id == "local") {
                 var element1 = document.getElementById("file");
                 var element2 = document.getElementById("filefield");
                 var element3 = document.getElementById("url");
                 var element4 = document.getElementById("urlfield");
                 element1.style.display = "inline";
                 element2.style.display = "inline";
                 element3.style.display = "none";
                 element4.style.display = "none";

             }

             if (\_element\_id == "url") {
                 var element1 = document.getElementById("url");
                 var element2 = document.getElementById("urlfield");
                 var element3 = document.getElementById("file");
                 var element4 = document.getElementById("filefield");
                 element1.style.display = "inline";
                 element2.style.display = "inline";
                 element3.style.display = "none";
                 element4.style.display = "none";

             }

         }
</script>
</body>
</html>
```Let's investigate this code. This is a simple HTML document with JavaScript. To select the file source (local or web) we've added a switch:```
<input type="radio" name="sourse" value="local" id="localField" onClick="display('local');" >Upload local file </input>
```This switch calls the JavaScript function display. This function receives one parameter which specifies the source of the file: local or web. Where local = upload local file and url = upload file from web. Toggling the switch displays the corresponding input field. OK, it's clear how the template works - it's simple enough. Let's take a look at the **controller**.

### Controller code```
//###Set variables and get POST data
    F3::set('userId', '');
    F3::set('privateKey', '');
    $clientId = F3::get('POST\["client\_id"\]');
    $privateKey = F3::get('POST\["private\_key"\]');
    $width = f3::get('POST\["width"\]');
    $height = f3::get('POST\["height"\]');

    function upload($clientId, $privateKey, $width='400', $height='650')
    {
        //###Check fileGuId
        if (empty($clientId) || empty($privateKey)) {
            throw new Exception('Please enter all required parameters');
        } else {
            F3::set('userId', $clientId);
            F3::set('privateKey', $privateKey);
            //Get base path
            $basePath = f3::get('POST\["server\_type"\]');
            //Get entered by user data
            $fileGuId = "";
            $url = F3::get('POST\["url"\]');
            $file = $\_FILES\['file'\];
            //###Create Signer, ApiClient and Storage Api objects

            //Create signer object
            $signer = new GroupDocsRequestSigner($privateKey);
            //Create apiClient object
            $apiClient = new APIClient($signer);
            //Create Storage Api object
            $api = new StorageApi($apiClient);
            //Check if user choose upload file from URL
            if ($url != "") {
                //Upload file from URL
                $uploadResult = $api->UploadWeb($clientId, $url);
                //Check is file uploaded
                if ($uploadResult->status == "Ok") {
                    //Get file GUID
                    $fileGuId = $uploadResult->result->guid;

                //If it isn't uploaded throw exception to template
                } else {
                    throw new Exception($uploadResult->error\_message);
                }
            }
            //Check is user choose upload local file
            if ($\_FILES\['file'\]\["name"\] != "") {
                //Temp name of the file
                $tmp\_name = $file\['tmp\_name'\];
                //Original name of the file
                $name = $file\['name'\];
                //Creat file stream
                $fs = FileStream::fromFile($tmp\_name);
                //###Make a request to Storage API using clientId
                //Upload file to current user storage
                $uploadResult = $api->Upload($clientId, $name, 'uploaded', "", $fs);

                //###Check if file uploaded successfully
                if ($uploadResult->status == "Ok") {
                    //Get file GUID
                    $fileGuId = $uploadResult->result->guid;

                //If it isn't uploaded throw exception to template
                } else {
                    throw new Exception($uploadResult->error\_message);
                }
            }
            //Generation of iframe URL using fileGuId
            $iframe = 'http://apps.groupdocs.com/document-viewer/embed/' . $fileGuId . '?frameborder="0" width=' . $width . 'height=' . $height;
            //If request was successfull - set url variable for template
            f3::set('fileId', $fileGuId);
            return f3::set('url', $iframe);
        }
    }

    try {
        upload($clientId, $privateKey, $width, $height);
    } catch(Exception $e) {
        $error = 'ERROR: ' .  $e->getMessage() . "\\n";
        f3::set('error', $error);
    }
    //Process template
    F3::set('userId', $clientId);
    F3::set('privateKey', $privateKey);
    F3::set('width', $width);
    F3::set('height', $height);

    echo Template::serve('template.htm');
```Now let's analyze the blocks of code we have here.```
    F3::set('userId', '');
    F3::set('privateKey', '');
    $clientId = F3::get('POST\["client\_id"\]');
    $privateKey = F3::get('POST\["private\_key"\]');
    $width = f3::get('POST\["width"\]');
    $height = f3::get('POST\["height"\]');
```In this block we get the data from the form transfered by the POST method with the Fatfree method F3::get which gives access to the global arrays such as POST, GET, FILE and SERVER. When we have collected the entered data, we can create a function which will do the job and we will have the ability to check every steps and get errors if there are any. Our function will get four parameters: client ID, private key, width and height (we need width and height for the iframe that will show the uploaded file).```
function upload($clientId, $privateKey, $width='400', $height='650')
```First of all, we must check whether the client ID and private key are entered. Without this data we can't do anything. Check it with this code:```
 if (empty($clientId) || empty($privateKey)) {
            throw new Exception('Please enter all required parameters');
```If we have this data, we can proceed to the next code block:```
F3::set('userId', $clientId);
F3::set('privateKey', $privateKey)
//Get base path
$basePath = f3::get('POST\["server\_type"\]');
//Get entered by user data
$fileGuId = "";
$url = F3::get('POST\["url"\]');
$file = $\_FILES\['file'\];
//###Create Signer, ApiClient and Storage Api objects
```Here we set user data for template and get the rest of the entered data from the form, such as the URL of a web file and the location of the local file. Later, we will check which fields are chosen by this data. Now we must create objects which will set up the relationships with the GroupDocs API and user account. This code does that:```
//Create signer object
 $signer = new GroupDocsRequestSigner($privateKey);
 //Create apiClient object
 $apiClient = new APIClient($signer);
 //Create Storage Api object
 $api = new StorageApi($apiClient);
```So we can check from where we're about to upload the file and then upload it. To check if the user choose to upload a file from the web, and to upload the file, use this code:```
//Check if user choose upload file from URL
            if ($url != "") {
                //Upload file from URL
                $uploadResult = $api->UploadWeb($clientId, $url);
                //Check is file uploaded
                if ($uploadResult->status == "Ok") {
                    //Get file GUID
                    $fileGuId = $uploadResult->result->guid;

                //If it isn't uploaded throw exception to template
                } else {
                    throw new Exception($uploadResult->error\_message);
                }
            }
```This block does all the magic uploading a file from the web. As you can see we check whether $url is an empty string. If it is not empty, the user has selected to upload a file from the web and we use the URL. To upload the file, we make a request to the UploadWeb method with the client ID and the URL for the file:```
$uploadResult = $api->UploadWeb($clientId, $url);
```Thats all for web uploading. Simple, yes? OK in response to this method we have an object with an array of all the info for this file such as the GUID, name, type and so on. To show this file in an iframe, we only need the GUID. We can get GUID easily:```
$fileGuId = $uploadResult->result->guid;
```If uploadWeb fails we get an error message:```
$uploadResult->error\_message
```But what if the user wants to upload a local file? We can check if they do, and if so upload the local file with this code:```
//Check is user choose upload local file
            if ($\_FILES\['file'\]\["name"\] != "") {
                //Temp name of the file
                $tmp\_name = $file\['tmp\_name'\];
                //Original name of the file
                $name = $file\['name'\];
                //Creat file stream
                $fs = FileStream::fromFile($tmp\_name);
                //###Make a request to Storage API using clientId
                //Upload file to current user storage
                $uploadResult = $api->Upload($clientId, $name, 'uploaded', "", $fs);

                //###Check if file uploaded successfully
                if ($uploadResult->status == "Ok") {
                    //Get file GUID
                    $fileGuId = $uploadResult->result->guid;

                //If it isn't uploaded throw exception to template
                } else {
                    throw new Exception($uploadResult->error\_message);
                }
            }
```To upload a local file we must get its name, assign it a temporary name and convert it to a FileStream. The first two we can get as usual for multipart/form-data:```
//Temp name of the file
                $tmp\_name = $file\['tmp\_name'\];
                //Original name of the file
                $name = $file\['name'\];
```And to convert the file to FileStream in the GroupDocs PHP SDK we have very cool thing: FileStream::fromFile. This function gets the file's temp name and returns a FileStream. Now we can send request to the GroupDocs API to upload the local file. The Upload file method get such parameters as client ID, local file name, description(string), callback URL (in this sample we'll use an empty string but if you want to, you can specify it) and FileStream. In the response object for the UploadWeb method we get info about the uploaded file. If the request failed, we get an error message.

### Displaying the fileWe've finished the upload and now we have only to generate an iframe and call our function.  ```
//Generation of iframe URL using fileGuId
            $iframe = 'http://apps.groupdocs.com/document-viewer/embed/' . $fileGuId . '?frameborder="0" width=' . $width . 'height=' . $height;
            //If request was successfull - set url variable for template
            f3::set('fileId', $fileGuId);
            return f3::set('url', $iframe);
        }
    }

    try {
        upload($clientId, $privateKey, $width, $height);
    } catch(Exception $e) {
        $error = 'ERROR: ' .  $e->getMessage() . "\\n";
        f3::set('error', $error);
    }
    //Process template
    F3::set('userId', $clientId);
    F3::set('privateKey', $privateKey);
    F3::set('width', $width);
    F3::set('height', $height);

    echo Template::serve('template.htm');
```

## The code in actionThats all. Below are a couple of screenshots that show how it looks in action.

#### The input form![The input form](https://blog.groupdocs.com/wp-content/uploads/sites/4/2013/04/form1.png "The input form")  

#### The iframe showing the uploaded document![The iframe displaying the uploaded file.](https://blog.groupdocs.com/wp-content/uploads/sites/4/2013/04/iframe2.png "The iframe displaying the uploaded file.")




