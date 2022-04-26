---
title: 'How to Compare Files with GroupDocs PHP SDK'
date: Fri, 12 Apr 2013 14:44:45 +0000
draft: false
url: /2013/04/12/how-to-compare-files-with-groupdocs-php-sdk/
author: 'Derek Hyland'
summary: ''
tags: ['API', 'document comparison', 'GroupDocs API', 'GroupDocs API SDK', 'GroupDocs Comparison', 'zArchive']
---

This article explains the basics of using PHP SDK classes and methods. In this article I'll use the Comparison API and show how to [compare two documents](http://groupdocs.com/apps/comparison) from a GroupDocs account. [Find information about other methods in the Swagger explorer](https://api.groupdocs.com/v2.0/spec/).

## Requirements

*   PHP 5.3
*   Apache ModRewrite
*   PHP Curl extension
*   PHP Sockets extension (php\_sockets.dll)
*   GroupDocs [PHP SDK](https://github.com/groupdocs)
*   composer.phar (Download from [http://getcomposer.org/download/](https://getcomposer.org/download/) or use the included version)
*   FatFree framework ([https://github.com/bcosca/fatfree](https://github.com/bcosca/fatfree))

We already know how to install the Fatfree framework and prepare for creating the sample from the [previous article](https://blog.groupdocs.com/how-to-convert-files-with-groupdocs-php-sdk). So lets start with the magic.

## Sample Creation: Creating the TemplateCreate a template file in the template folder and name it **Comparison.htm**. This generates a web page with a form for entering the necessary data such as user ID, private key and the file GUIDs for the two files that will be compared. The user can also enter a callback URL. How to get this data you can find out [in the documentation.](https://docs.groupdocs.com/)```
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
<h3 style="text-align:center;"><a href="/index.php">GroupDocs PHP SDK Samples</a> - Comparison</h3>

<div class='samplecontent' style="padding:10px;">
   <i>This sample will show how to Compare documents using PHP SDK</i> <br/>

   <br/>You entered:
   ClientID = {{@userId}}
   PrivateKey = {{@privateKey}}
   Source file Id = {{@sourceFileId}}
   Target file Id = {{@targetFileId}}
   Call back url = {{@callbackURL}}

   <div id="requestForm" style="padding:20px; border:1px solid black;">
    Enter data for request and press "Make request" button 
        <form action="/comparison" method = "post" enctype = 'multipart/form-data'>
            <label for='client\_id'>GroupDocs ClientID</label>
            <br />
            <input type='text', name='client\_id' value="{{@userId}}" />
            <br />
            <label for='private\_key'>GroupDocs PrivateKey</label>
            <br />
            <input type='text', name='private\_key'  value="{{@privateKey}}" />
            <br />
            <label for='sourceFileId'>sourceFileId</label>
            <br />
            <input type='text', name='sourceFileId'  value="{{@sourceFileId}}" />
            <br />
            <label for='targetFileId'>targetFileId</label>
            <br />
            <input type='text', name='targetFileId'  value="{{@targetFileId}}" />
            <br />
            <label for='callbackUrl'>callbackUrl</label>
            <br />
            <input type='text', name='callbackUrl'  value="{{@callbackURL}}" />
            <br />
            <input type='submit' value='Make Request'/>
        </form>
   </div>
   <div  style="padding:20px; border:1px solid black;">
         Results: 
        <iframe src={{@iframe}}></iframe>
   </div>
   <br/>
</div>

</body>
</html>
```

### The Template Code ExplainedThis code block shows the data the user entered. Here you can see code like this: \\{\\{@userId\\}\\}. In the Fatfree framework you must call a variable declared in the controller for the template.```
<br/>You entered:
   ClientID = {{@userId}}
   PrivateKey = {{@privateKey}}
   Source file Id = {{@sourceFileId}}
   Target file Id = {{@targetFileId}}
   Call back url = {{@callbackURL}}
```The next step in the template file creates a div block with the form for entering data:```
<div id="requestForm" style="padding:20px; border:1px solid black;">
    Enter data for request and press "Make request" button 
        <form action="/sample19" method = "post" enctype = 'multipart/form-data'>
            <label for='client\_id'>GroupDocs ClientID</label>
            <br />
            <input type='text', name='client\_id' value="{{@userId}}" />
            <br />
            <label for='private\_key'>GroupDocs PrivateKey</label>
            <br />
            <input type='text', name='private\_key'  value="{{@privateKey}}" />
            <br />
            <label for='sourceFileId'>sourceFileId</label>
            <br />
            <input type='text', name='sourceFileId'  value="{{@sourceFileId}}" />
            <br />
            <label for='targetFileId'>targetFileId</label>
            <br />
            <input type='text', name='targetFileId'  value="{{@targetFileId}}" />
            <br />
            <label for='callbackUrl'>callbackUrl</label>
            <br />
            <input type='text', name='callbackUrl'  value="{{@callbackURL}}" />
            <br />
            <input type='submit' value='Make Request'/>
        </form>
   </div>
```

#### CallbacksLet's explain some key moments for this code. In the Fatfree framework, the form is creation using a simple HTML code which does not need explaining: everything is as usual. But in the value of the input's we transfer the value of variables from the controller - \\{\\{@userId\\}\\} - in order that the user data stays in the values when the user clicks **Make request**. Also you can see here the input named **CallbackURL**. In this field, the user can enter a URL which will be executed by the server after the comparison is done. A callback is something like an action for a form. It can be a PHP file which is triggered by the server. All of these fields are required except for the **callbackURL** field.

#### Displaying the Comparison ResultsThe next code block in the template file is:```
<div  style="padding:20px; border:1px solid black;">
         Results: 
           <font color="red">{{@error}}</font>           <iframe src={{@iframe}}></iframe>
   </div>
   <br/>
</div>
```This div block shows the results of a comparison. As you can see, it's simple HTML too but the iframe source and parameters we get from the controller. As part of the controller operation, we check that all the parameters have been entered. If a parameter doesn't have a value, an error is returned. So, depending on what we receive from the server, we return either the iframe or an error message. The form looks like this: ![](https://blog.groupdocs.com/wp-content/uploads/sites/4/2013/04/form.png "form")

## Sample Creation: Creating the ControllerGo to the **inc\_samples** folder and create controller file called **Comparison.php**. This file will contain this code:```
<?php
    //<i>This sample will show how to use <b>Compare</b> method from ComparisonApi to return a URL representing a single page of a Document</i>

    //###Set variables and get POST data
    F3::set('userId', '');
    F3::set('privateKey', '');
    f3::set('result', "");
    $clientId = F3::get('POST\["client\_id"\]');
    $privateKey = F3::get('POST\["private\_key"\]');
    $sourceFileId = f3::get('POST\["sourceFileId"\]');
    $targetFileId = f3::get('POST\["targetFileId"\]');
    $callbackUrl = f3::get('POST\["callbackUrl"\]');
    $basePath = f3::get('POST\["server\_type"\]');

    function Compare($clientId, $privateKey, $sourceFileId, $targetFileId, $callbackUrl, $basePath)
    {
         //### Check clientId, privateKey and fileGuId
        if (empty($clientId) || empty($privateKey) || empty($sourceFileId) || empty($targetFileId)) {
            throw new Exception('Please enter all required parameters');
        } else {
            //Set variables for Viewer
            F3::set('userId', $clientId);
            F3::set('privateKey', $privateKey);
            //###Create Signer, ApiClient and Storage Api objects

            //Create signer object
            $signer = new GroupDocsRequestSigner($privateKey);
            //Create apiClient object
            $apiClient = new APIClient($signer);
            //Create ComparisonApi object
            $CompareApi = new ComparisonApi($apiClient);
            $CompareApi->setBasePath($basePath);
            //###Make request to ComparisonApi using user id

            //Comparison of documents where: $clientId - user GuId, $sourceFileId - source file Guid in which will be provided compare,
            //$targetFileId - file GuId with wich will compare sourceFile, $callbackUrl - Url which will be executed after compare,

            $info = $CompareApi->Compare($clientId, $sourceFileId, $targetFileId, $callbackUrl);

            //###Example of handling callback request:
            //  You can handle callback request in separate php file or in the same one. Our service will post JSON data via post request.
            //In PHP you should get raw data like this:
            //     $json = file\_get\_contents("php://input"); - get callback data
            //     $fp = fopen(\_\_DIR\_\_ . '/../../temp/signature\_request\_log.txt', 'a'); - open file for data write
            //     fwrite($fp, $json . "\\r\\n"); - write data to the file
            //     fclose($fp); - close file

            //Check request status
            if($info->status == "Ok") {
                //Create AsyncApi object
                $asyncApi = new AsyncApi($apiClient);
                $asyncApi->setBasePath($basePath);
                //### Check job status

                for ($i = 0; $i <= 5; $i++) {
                    //Delay necessary that the inquiry would manage to be processed
                    sleep(5);
                    //Make request to api for get document info by job id
                    $jobInfo = $asyncApi->GetJobDocuments($clientId, $info->result->job\_id);
                    //Check job status, if status is Completed or Archived exit from cycle
                    if ($jobInfo->result->job\_status == "Completed" || $jobInfo->result->job\_status == "Archived") {
                        break;
                    //If job status Postponed throw exception with error
                    } elseif ($jobInfo->result->job\_status == "Postponed") {
                        throw new Exception('Job is failure');
                    }

                }
                //Get file guid
                $guid = $jobInfo->result->outputs\[0\]->guid;
                // Construct iframe using fileId
                if($basePath == "https://api.groupdocs.com/v2.0") {
                    $iframe = 'https://apps.groupdocs.com/document-viewer/embed/' . $guid . ' frameborder="0" width="800" height="650"';
                //iframe to dev server
                } elseif($basePath == "https://dev-api.groupdocs.com/v2.0") {
                    $iframe = 'https://dev-apps.groupdocs.com/document-viewer/embed/' . $guid . ' frameborder="0" width="500" height="650"';
                //iframe to test server
                } elseif($basePath == "https://stage-api.groupdocs.com/v2.0") {
                    $iframe = 'https://stage-apps.groupdocs.com/document-viewer/embed/' . $guid . ' frameborder="0" width="500" height="650"';
                }

            }
            //If request was successfull - set url variable for template
            return F3::set('iframe', $iframe);
        }
    }

    try {
         Compare($clientId, $privateKey, $sourceFileId, $targetFileId, $callbackUrl, $basePath);

    } catch(Exception $e) {
        $error = 'ERROR: ' .  $e->getMessage() . "\\n";
        f3::set('error', $error);
    }
    //Process template
    f3::set('sourceFileId', $sourceFileId);
    f3::set('targetFileId', $targetFileId);
    f3::set('callbackURL', $callbackUrl);
//    f3::set('result', $result);
    echo Template::serve('comparison.htm');
```

### The Controller Code ExplainedNow the code explanation: First of all we must get a posted data from form. In Fatfree framework we can do it with this code:```
$clientId = F3::get('POST\["client\_id"\]');
    $privateKey = F3::get('POST\["private\_key"\]');
    $sourceFileId = f3::get('POST\["sourceFileId"\]');
    $targetFileId = f3::get('POST\["targetFileId"\]');
    $callbackUrl = f3::get('POST\["callbackUrl"\]');
    $basePath = f3::get('POST\["server\_type"\]');
```F3::get is a framework method to call to the global associative array of variables passed to the current script via the HTTP POST method. Now we can declare empty variables for template.```
F3::set('userId', '');
    F3::set('privateKey', '');
    f3::set('result', "");
```f3::set is one more framework method similar to f3::get but it transfers data to the template. The first parameter is a name of a variable in the template. The second parameter is the data that associated with this variable. Right now, it's a empty string.

#### Creating the Compare FunctionLet's create a function named Compare which takes the entered data and runs a comparison. First, what this function does is to check that all data has been entered by the user:```
function Compare($clientId, $privateKey, $sourceFileId, $targetFileId, $callbackUrl, $basePath)
    {
       if (empty($clientId) || empty($privateKey) || empty($sourceFileId) || empty($targetFileId)) {
            throw new Exception('Please enter all required parameters');
```The checks are standard checks for empty values. If the user entered all the required data, the controller continues its operation:```
} else {
            //Set variables for Viewer
            F3::set('userId', $clientId);
            F3::set('privateKey', $privateKey);
            //###Create Signer, ApiClient and Storage Api objects

            //Create signer object
            $signer = new GroupDocsRequestSigner($privateKey);
            //Create apiClient object
            $apiClient = new APIClient($signer);
            //Create ComparisonApi object
            $CompareApi = new ComparisonApi($apiClient);
```This block sets data to the template variables userId and privateKey, which was empty. After that they contain user entered data. Next create the Signer, ApiClient and Comparison API objects for making request to the server.

#### The ComparisonAnd now the comparison magic:```
//Comparison of documents where: $clientId - user GuId, $sourceFileId - source file Guid in which will be provided compare,
            //$targetFileId - file GuId with wich will compare sourceFile, $callbackUrl - Url which will be executed after compare,

            $info = $CompareApi->Compare($clientId, $sourceFileId, $targetFileId, $callbackUrl);
```Expected the comparison segment to be bigger? Sorry if you're disappointed. The document comparison is only one line of code: all you need to do is call the Compare method from the PHP SDK and transfer the proper data to it. Data such as the client ID (user id), the GUIDs for the two files that will be compared (the source and target file IDs) and, finally, the callback URL which can be an empty string. The next step is a check of the comparison results:```
if($info->status == "Ok") {
                //Create AsyncApi object
                $asyncApi = new AsyncApi($apiClient);

                //### Check job status

                for ($i = 0; $i <= 5; $i++) {
                    //Delay necessary that the inquiry would manage to be processed
                    sleep(5);
                    //Make request to api for get document info by job id
                    $jobInfo = $asyncApi->GetJobDocuments($clientId, $info->result->job\_id);
                    //Check job status, if status is Completed or Archived exit from cycle
                    if ($jobInfo->result->job\_status == "Completed" || $jobInfo->result->job\_status == "Archived") {
                        break;
                    //If job status Postponed throw exception with error
                    } elseif ($jobInfo->result->job\_status == "Postponed") {
                        throw new Exception('Job is failure');
                    }

                }
                //Get file guid
                $guid = $jobInfo->result->outputs\[0\]->guid;
                // Construct iframe using fileId
                $iframe = 'https://apps.groupdocs.com/document-viewer/embed/' . $guid . ' frameborder="0" width="800" height="650"';

            }
```Here we check what status of request was returned. If it's "Ok", we can continue and get all the necessary data for an iframe, such as result file GUID, from the returned job ID. In the server response of the Compare method, we have only the request status and job ID which is why we must create an AsyncApi object ($asyncApi = new AsyncApi($apiClient); and call the GetJobDocuments method from this object. This method uses the job ID to get all the info of this job. Now we must check the job status from $jobInfo->result. If it is "Completed" or "Archived", all is well and we continue. But before we do this check we must allow the server to fulfill the inquiry having established a delay in 5 sec: sleep(5);. After job status check, we can get the result file GUID. It will be in the outputs array: $guid = $jobInfo->result->outputs\[0\]->guid;. So now we have real file GUID and we can generate an iframe: $iframe = 'https:\*\*//apps.groupdocs.com/document-viewer/embed/' . $guid . ' frameborder="0" width="800" height="650"';

#### Calling the FunctionAnd one last code block:```
try {
         Compare($clientId, $privateKey, $sourceFileId, $targetFileId, $callbackUrl, $basePath);

    } catch(Exception $e) {
        $error = 'ERROR: ' .  $e->getMessage() . "\\n";
        f3::set('error', $error);
    }
    //Process template
    f3::set('sourceFileId', $sourceFileId);
    f3::set('targetFileId', $targetFileId);
    f3::set('callbackURL', $callbackUrl);
//    f3::set('result', $result);
    echo Template::serve('comparison.htm');
```In this block we call our function with user data and a catch exception (in case there is an exception). The exception contains all possible errors. And we can set variables for the template and send them to it: f3::set('sourceFileId', $sourceFileId);. As I've already mentioned, this sets variables for the template and this line of code, echo Template::serve('comparison.htm'); calls template and send data to it. The iframe, complete with results, looks like this: ![](https://blog.groupdocs.com/wp-content/uploads/sites/4/2013/04/iframe1.png "iframe")




