---
title: 'How to Merge Data Fields from a DOCX File with a Data Source and Output to PDF'
date: Fri, 03 May 2013 12:30:06 +0000
draft: false
url: /2013/05/03/how-to-merge-data-fields-from-a-docx-file-with-a-data-source-and-output-to-pdf/
author: 'Derek Hyland'
summary: ''
tags: ['API', 'document collaboration', 'document management', 'online document management system', 'php api', 'zArchive']
---

This article explains how to get the fields from a template DOCX file, fill them with data and merge to new PDF file using GroupDocs.

## Requirements

*   PHP 5.3
*   Apache ModRewrite
*   PHP Curl extension
*   PHP Sockets extension (php\_sockets.dll)
*   GroupDocs PHP SDK
*   composer.phar (Download from [http://getcomposer.org/download/](https://getcomposer.org/download/) or use the included version.)
*   FatFree framework ([https://github.com/bcosca/fatfree](https://github.com/bcosca/fatfree))

We already know how to install the Fatfree framework and prepare for creating the sample from [the previous article](https://blog.groupdocs.com/how-to-convert-files-with-groupdocs-php-sdk). The sample that we create in this article is not much different from other sample with Fatfree. We need a template file with a form and a controller file to process entered data.

## Sample creationThe template file is the same as in [the previous article](https://blog.groupdocs.com/how-to-convert-files-with-groupdocs-php-sdk). Because of this, I will not explain the template file but just show the code.

### Template file code```
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
<h3 style="text-align:center;"><a href="/index.php">GroupDocs PHP SDK Samples</a> - Merge fields</h3>

<div class='samplecontent' style="padding:10px;">
   <span class="description"><i>This sample will show how to merge data fields in docx file with data source and get result file as PDF file using PHP SDK</i></span> <br/>
    <br />
   You entered:
   ClientID = {{@userId}}
   PrivateKey = {{@privateKey}}
   File Id = {{@fileId}}

   <font color="red">{{@error}}</font>
   <div id="requestForm" style="padding:20px; border:1px solid black;">
    Enter data for request and press "Make request" button 
        <form action="controller" method = "post" enctype = 'multipart/form-data'>
            <br />
            <label for='client\_id'>GroupDocs Client ID</label>
            <br />
            <input type='text' name='client\_id' value="{{@userId}}" />
            <br />
            <label for='private\_key'>GroupDocs PrivateKey</label>
            <br />
            <input type='text' name='private\_key'  value="{{@privateKey}}" />
            <br />
            <br />
            <input type="radio" name="sourse" value="guid" id="id" onClick="display('guid');" checked>File ID (GUID) </input>
            <br />
            <input type="radio" name="sourse" value="local" id="localField" onClick="display('local');" >Upload local file </input>
            <br />
            <input type="radio" name="sourse" value="url" id="urlField" onClick="display('url');" >Upload file from URL </input>
            <br />

            <label for='private\_key' id="guid">GroupDocs fileID</label>
            <br />
            <input type='text' name='fileId' id="guidfield" value="{{@fileId}}" />

            <label for='file' id="file" style="display:none;">Local file</label>
            <br />
            <input type='file' name='file' id="filefield" style="display:none;" />

            <label for='private\_key' style="display:none;" id="url">File URL</label>
            <br />
            <input type='text' name='url'  value="" id="urlfield" style="display:none;" />
            <br />
            <input type='submit' value='Make Request'/>
        </form>
   </div>
   <div  style="padding:20px; border:1px solid black;">
        <font color="green">{{@message}}</font>
        <iframe frameborder="0" width="500" height="650" src="{{@url}}"></iframe>
   </div>
   <br/>
</div>

 <include href="links.htm" />
<script type="text/javascript">

    function display(\_element\_id) {

             if (\_element\_id == "guid") {
                 var element1 = document.getElementById("file");
                 var element2 = document.getElementById("filefield");
                 var element3 = document.getElementById("url");
                 var element4 = document.getElementById("urlfield");
                 var element5 = document.getElementById("guid");
                 var element6 = document.getElementById("guidfield");
                 element1.style.display = "none";
                 element2.style.display = "none";
                 element3.style.display = "none";
                 element4.style.display = "none";
                 element5.style.display = "inline";
                 element6.style.display = "inline";

             }

             if (\_element\_id == "local") {
                 var element1 = document.getElementById("file");
                 var element2 = document.getElementById("filefield");
                 var element3 = document.getElementById("url");
                 var element4 = document.getElementById("urlfield");
                 var element5 = document.getElementById("guid");
                 var element6 = document.getElementById("guidfield");
                 element1.style.display = "inline";
                 element2.style.display = "inline";
                 element3.style.display = "none";
                 element4.style.display = "none";
                 element5.style.display = "none";
                 element6.style.display = "none";

             }

             if (\_element\_id == "url") {
                 var element1 = document.getElementById("url");
                 var element2 = document.getElementById("urlfield");
                 var element3 = document.getElementById("file");
                 var element4 = document.getElementById("filefield");
                 var element5 = document.getElementById("guid");
                 var element6 = document.getElementById("guidfield");
                 element1.style.display = "inline";
                 element2.style.display = "inline";
                 element3.style.display = "none";
                 element4.style.display = "none";
                 element5.style.display = "none";
                 element6.style.display = "none";
             }

         }
</script>
</body>
</html>
```OK, what's happening with the template file clear so lets take a look at the controller file.

### Controller fileWe already know how to create this file. If you're unsure, look at [a previous post that explains how](https://blog.groupdocs.com/how-to-convert-files-with-groupdocs-php-sdk). Below, I'll show you the complete controller code and then explain how it works.```
<?php
    //<i>This sample will show how to merge data fields in docx file with data source and get result file as PDF file</i>

    //###Set variables and get POST data
    F3::set('userId', '');
    F3::set('privateKey', '');
    $clientId = F3::get('POST\["client\_id"\]');
    $privateKey = F3::get('POST\["private\_key"\]');

    function mergeFields($clientId, $privateKey, $basePath)
    {
        //###Check if user entered all parameters
        if (empty($clientId) || empty($privateKey)) {
            throw new Exception('Please enter FILE ID');
        } else {
            F3::set('userId', $clientId);
            F3::set('privateKey', $privateKey);
            //###Create Signer, ApiClient and Storage Api objects

            //Create signer object
            $signer = new GroupDocsRequestSigner($privateKey);
            //Create apiClient object
            $apiClient = new APIClient($signer);
            //Create Doc Api object
            $docApi = new DocApi($apiClient);
            //Create Storage Api object
            $apiStorage = new StorageApi($apiClient);
            //Create AsyncApi object
            $api = new AsyncApi($apiClient);
            $mergApi = new MergeApi($apiClient);
            //Get entered by user data
            $url = F3::get('POST\["url"\]');
            $file = $\_FILES\['file'\];
            $fileId = f3::get('POST\["fileId"\]');
            //Check if user choose upload file from URL
            if ($url != "") {
                //Upload file from URL
                $uploadResult = $apiStorage->UploadWeb($clientId, $url);
                //Check is file uploaded
                if ($uploadResult->status == "Ok") {
                    //Get file GUID
                    $fileGuId = $uploadResult->result->guid;
                    $fileId = "";
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
                $uploadResult = $apiStorage->Upload($clientId, $name, 'uploaded', "", $fs);

                //###Check if file uploaded successfully
                if ($uploadResult->status == "Ok") {
                    //Get file GUID
                    $fileGuId = $uploadResult->result->guid;
                    $fileId = "";

                //If it isn't uploaded throw exception to template
                } else {
                    throw new Exception($uploadResult->error\_message);
                }
            }
            //Check is user choose file GUID
            if ($fileId != "") {
                //Get entered by user file GUID
                $fileGuId = $fileId;
            }
            //Get feilds from template
            $fields = $docApi->GetTemplateFields($clientId, $fileGuId);
            //Check status
            if ($fields->status == "Ok") {
                //Create new Datasource object
                $dataSource = new Datasource();
                //Create empty array
                $array = array();
                //Loop for fields creataion
                for ($i = 0; $i < count($fields->result->fields); $i++) {
                    //Create new DatasourceField object
                    $field = new DatasourceField();
                    //Set DatasourceFiled data
                    $field->name = $fields->result->fields\[$i\]->name;
                    $field->type = "text";
                    $field->values = array("value1", "value2");
                    //Push DatasourceField to array
                    array\_push($array, $field);
                }
                //Set array feilds array to the Datasourc
                $dataSource->fields = $array;
                //Add Datasource to GroupDocs
                $addDataSource = $mergApi->AddDataSource($clientId, $dataSource);
                //Check status
                if ($addDataSource->status == "Ok") {
                    //If status ok merge Datasource to new pdf file
                    $job = $mergApi->MergeDatasource($clientId, $fileGuId, $addDataSource->result->datasource\_id, "pdf", null);
                    //Check status
                    if ($job->status == "Ok") {
                        //### Check job status
                         for ($n = 0; $n <= 5; $n++) {
                             //Delay necessary that the inquiry would manage to be processed
                             sleep(5);
                             //Make request to api for get document info by job id
                             $jobInfo = $api->GetJobDocuments($clientId, $job->result->job\_id);
                             //Check job status, if status is Completed or Archived exit from cycle
                             if ($jobInfo->result->job\_status == "Completed" || $jobInfo->result->job\_status == "Archived") {
                                 break;
                             //If job status Postponed throw exception with error
                             } elseif ($jobInfo->result->job\_status == "Postponed") {
                                 throw new Exception("Job is failed");

                             }
                         }
                         //Get file guid
                         $guid = $jobInfo->result->inputs\[0\]->outputs\[0\]->guid;
                          //Get file name
                         $name = $jobInfo->result->inputs\[0\]->outputs\[0\]->name;
                         //Local path to the downloads folder
                         $downloadFolder = dirname(\_\_FILE\_\_). '/../downloads';
                         //Check is folder exist
                         if (!file\_exists($downloadFolder)) {
                             //If folder don't exist create it
                             mkdir($downloadFolder);
                         }
                         //Obtaining file stream of downloading file and definition of folder where to download file
                         $outFileStream =  FileStream::fromHttp($downloadFolder, $name);
                         //Download file from GroupDocs.
                         $download = $apiStorage->GetFile($clientId, $guid, $outFileStream);
                         f3::set("message", "File was converted and downloaded to the " . $downloadFolder . "/" . $name);
                         //### If request was successfull
                         //Generation of iframe URL using $pageImage->result->guid
                         $iframe = 'https://apps.groupdocs.com/document-viewer/embed/' . $guid;

                    } else {
                        throw new Exception($job->error\_message);
                    }
                } else {
                    throw new Exception($addDataSource->error\_message);
                }
            } else {
                throw new Exception($fields->error\_message);
            }

            //Set variable with results for template

            return f3::set('url', $iframe);
        }
    }

    try {
        mergeFields($clientId, $privateKey, $basePath);
    } catch(Exception $e) {
        $error = 'ERROR: ' .  $e->getMessage() . "\\n";
        f3::set('error', $error);
    }
    //Process template
    echo Template::serve('template.htm');
```That's the controller: open your mind and plunge in. First of all, we get all the data transfered from the form by POST to the controller. This block of code does that:```
  //###Set variables and get POST data
    F3::set('userId', '');
    F3::set('privateKey', '');
    $clientId = F3::get('POST\["client\_id"\]');
    $privateKey = F3::get('POST\["private\_key"\]');
```As you can see, we use the Fatfree method F3::set to initially set the template variables and then the F3::get method to get the posted data. We have all necessary data to create API objects; the rest of the data we will get later. Let's create a function that takes this data, checks it and does the rest of the magic. The function is called mergeFields and a definition looks like this: function mergeFields($clientId, $privateKey). The mergeFields function takes two parameters - client ID and private key. This data is most important because without it, we can't send a request to the API. That's why we check that it's been entered with this code:```
if (empty($clientId) || empty($privateKey)) {
            throw new Exception('Please enter FILE ID');
        } else {
            F3::set('userId', $clientId);
            F3::set('privateKey', $privateKey);
```Then, if the client ID and private key have been entered we proceed with API objects creation. I expect you already know how to do this. Next, we check whether the user wants to upload a local file, one from the web, or a file already in the GroupDocs account. We can work with documents through the file GUID. We dont have this data, but that's not a problem - lets get it. Simply use the Fatfree method F3::get to get the client ID and private key. Get the rest of the data:```
 //Get entered by user data
            $url = F3::get('POST\["url"\]');
            $file = $\_FILES\['file'\];
            $fileId = f3::get('POST\["fileId"\]');
```Since this data are simple strings - with the exception of $file - check which of them are chosen by elementary verification on an empty string: if ($url != "") or if ($fileId != ""). If you wonder what to do if a user selects to upload a local file, how to check it. It's not a problem. In the global variable which consist of the local file we have an array of file data such as file name, temp name and file content. To check if a user has selected a local file, simply check if the file name is empty. This array field consist of string data and we can check it for empty string: if ($\_FILES\['file'\]\["name"\] != ""). According to which check returns "true", we know whether to use an entered file GUID or upload a file in three different ways. How to do this you can read in last weeks post: [Two ways to upload files](https://blog.groupdocs.com/two-ways-of-uploading-files-into-a-groupdocs-account). The most interesting part, and culmination of this example, is to get the field from template DOCX file and merge them to a PDF file. To do this, we need this GroupDocs PHP SDK methods:

*    From DocApi GetTemplateFields
*   From MergeApi AddDataSource and MergeDatasource
*   From AsyncApi GetJobDocuments
*   And from StorageApi GetFile

First, let's take a look at the code which will do all this work and use our methods:```
//Get fields from template
            $fields = $docApi->GetTemplateFields($clientId, $fileGuId);
            //Check status
            if ($fields->status == "Ok") {
                //Create new Datasource object
                $dataSource = new Datasource();
                //Create empty array
                $array = array();
                //Loop for fields creataion
                for ($i = 0; $i < count($fields->result->fields); $i++) {
                    //Create new DatasourceField object
                    $field = new DatasourceField();
                    //Set DatasourceFiled data
                    $field->name = $fields->result->fields\[$i\]->name;
                    $field->type = "text";
                    $field->values = array("value1", "value2");
                    //Push DatasourceField to array
                    array\_push($array, $field);
                }
                //Set array feilds array to the Datasourc
                $dataSource->fields = $array;
                //Add Datasource to GroupDocs
                $addDataSource = $mergApi->AddDataSource($clientId, $dataSource);
                //Check status
                if ($addDataSource->status == "Ok") {
                    //If status ok merge Datasource to new pdf file
                    $job = $mergApi->MergeDatasource($clientId, $fileGuId, $addDataSource->result->datasource\_id, "pdf", null);
                    //Check status
                    if ($job->status == "Ok") {
                        //### Check job status
                         for ($n = 0; $n <= 5; $n++) {
                             //Delay necessary that the inquiry would manage to be processed
                             sleep(5);
                             //Make request to api for get document info by job id
                             $jobInfo = $api->GetJobDocuments($clientId, $job->result->job\_id);
                             //Check job status, if status is Completed or Archived exit from cycle
                             if ($jobInfo->result->job\_status == "Completed" || $jobInfo->result->job\_status == "Archived") {
                                 break;
                             //If job status Postponed throw exception with error
                             } elseif ($jobInfo->result->job\_status == "Postponed") {
                                 throw new Exception("Job is failed");

                             }
                         }
                         //Get file guid
                         $guid = $jobInfo->result->inputs\[0\]->outputs\[0\]->guid;
                          //Get file name
                         $name = $jobInfo->result->inputs\[0\]->outputs\[0\]->name;
                         //Local path to the downloads folder
                         $downloadFolder = dirname(\_\_FILE\_\_). '/../downloads';
                         //Check is folder exist
                         if (!file\_exists($downloadFolder)) {
                             //If folder don't exist create it
                             mkdir($downloadFolder);
                         }
                         //Obtaining file stream of downloading file and definition of folder where to download file
                         $outFileStream =  FileStream::fromHttp($downloadFolder, $name);
                         //Download file from GroupDocs.
                         $download = $apiStorage->GetFile($clientId, $guid, $outFileStream);
```The logic is simple.

*   First, we get all the fields from the template DOCX file with the GetTemplateFields method. It takes the parameters client ID and template DOCX file GUID. The method returns an object with fields.
*   Now, create a DataSource object in which one of the parameters is a DataSourceFields array which we must create. We will put the field we get from template DOCX file into this array. This action occurs in this peace of code:

```
//Create empty array
                $array = array();
                //Loop for fields creataion
                for ($i = 0; $i < count($fields->result->fields); $i++) {
                    //Create new DatasourceField object
                    $field = new DatasourceField();
                    //Set DatasourceFiled data
                    $field->name = $fields->result->fields\[$i\]->name;
                    $field->type = "text";
                    $field->values = array("value1", "value2");
                    //Push DatasourceField to array
                    array\_push($array, $field);
                }
                //Set array feilds array to the Datasourc
                $dataSource->fields = $array;
```As you can see, the DataSourceFields object has a values parameter. Into this parameter we put an array of strings or only string which will be added to the field as content.

*   After creating the DataSource object, the next step is to add DataSource to GroupDocs for the convertion to PDF. This trick can be done as follows:

```
//Add Datasource to GroupDocs
                $addDataSource = $mergApi->AddDataSource($clientId, $dataSource);
```In response to this we get the **datasource ID** by which we can both merge it and [convert to PDF](http://groupdocs.com/apps/conversion), thus killing two birds with one stone.

*    Take the client ID, datasource ID, the original DOCX file GUID and put all of this into the MergeDatasource method. This request in code:

```
$job = $mergApi->MergeDatasource($clientId, $fileGuId, $addDataSource->result->datasource\_id, "pdf", null);
```As you see, one of the input parameters is a string with type of the result file. When the API gets this request, it creates a new PDF file with merged fields. Phew, we merged our fields to a new PDF file and now we can download it and see it in an iframe. The MergeDatasource method returns Job id using which in the GetJobDocuments method we get all the info about the new PDF file that we need, such is GUID and name.

*   To download it, create a FileStream which contains a local path for downloading the file:

```
//Obtaining file stream of downloading file and definition of folder where to download file
                         $outFileStream =  FileStream::fromHttp($downloadFolder, $name);
```After that use the GetFile method to download it: $download = $apiStorage->GetFile($clientId, $guid, $outFileStream); You already know how to generate an iframe. The only thing left is to call our function and return the new PDF file GUID to the template to show in the browser as an iframe. You already know how to do this too, if you've followed this article series. And we're done!

## ScreenshotsHere are two screenshots that show the input form and the output file so you can see the process in action.

#### The input form![](https://blog.groupdocs.com/wp-content/uploads/sites/4/2013/05/form.png "The input form")

#### The output PDF![](https://blog.groupdocs.com/wp-content/uploads/sites/4/2013/05/iframe.png "The iframe with the output PDF")




