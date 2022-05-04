---
title: 'Comparison API sample Implementation with PHP SDK'
date: Mon, 18 Feb 2013 05:54:55 +0000
draft: false
url: /2013/02/18/implement-document-comparison-api-sample-with-php-sdk/
aliases:
    - /2013/02/18/implementation-of-comparison-api-sample-with-groupdocs-php-sdk/
author: 'Derek Hyland'
summary: ''
tags: ['API', 'compare documents', 'comparison api', 'document comparison', 'Document Comparison API', 'document management', 'GroupDocs API SDK', 'zArchive']
categories: ['GroupDocs.Comparison Product Family']
---

This article explains the basics of using PHP SDK classes and methods. In this article I'll use the Comparison API and show how to [compare two documents](https://products.groupdocs.cloud/comparison) from a GroupDocs account. [Find information about others methods in the Swagger explorer](https://api.groupdocs.cloud/v2.0/comparison/swagger/spec).

## Requirements

*   PHP 5.3
*   Apache ModRewrite
*   PHP Curl extension
*   PHP Sockets extension (php\_sockets.dll)
*   GroupDocs [PHP SDK](https://products.groupdocs.cloud/comparison/php)
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

## Let's Start Developing

### Create .htaccess and index.php files

1.  Create a **.htaccess**file and enter this code:
    
    ```
            RewriteEngine On
    	RewriteCond %{REQUEST\_FILENAME} !-l
    	RewriteCond %{REQUEST\_FILENAME} !-f
    	RewriteCond %{REQUEST\_FILENAME} !-d
    	RewriteRule .\* index.php \[L,QSA\]
    
    		Header Unset ETag
    		FileETag none
    
    		ExpiresActive On
    		ExpiresDefault A604800
    ```
    
    This code declare initials settings for project.
2.  Create a **index.php**file in the root folder.This file does show anything in the browser but is very important for the work to come. The **index.php file** is responsible for data transmission between a template and the controller. It also includes the FatFree engine, PHP SDK, templates and controllers. In it, you describe which template depends on what controller. For example, F3::route('GET|POST /comparison','comparison.php'); means that the template comparison sends data to **comparison.php**, a file that processes received data and returns results to the template. (We will create this file later.) Below is the full code of ****Index.php****```
    <?php
    require\_once \_\_DIR\_\_.'/FatFree\_Framework/lib/base.php';
    require\_once \_\_DIR\_\_.'/vendor/autoload.php';
    F3::set('CACHE',FALSE);
    F3::set('DEBUG',1);
    F3::set('UI','templates/');
    F3::set('IMPORTS','inc\_samples/');
    
    F3::route('GET /','home');
    F3::route('GET /index.php','home');
    F3::route('GET|POST /sample01','sample01.php');
    F3::route('GET|POST /sample02','sample02.php');
    function home() {
              echo Template::serve('index.htm');
    }
    F3::run();
    ```

#### Understanding index.php

```
require\_once \_\_DIR\_\_.'/FatFree\_Framework/lib/base.php'; // include fatfree libs
require\_once \_\_DIR\_\_.'/vendor/autoload.php';            // include PHP SDK
F3::set('CACHE',FALSE);                                 // set Cache to false
F3::set('DEBUG',1);                                     // set Debug to 1
F3::set('UI','templates/');                             // include folder with templates
F3::set('IMPORTS','inc\_samples/');                      // include folder with controllers
```

The next block declares routes for template file and controller.

```
F3::route('GET /','home');
F3::route('GET /index.php','home');
F3::route('GET|POST /sample01','sample01.php');
F3::route('GET|POST /callbacks/signature\_callback','signature\_callback.php');
```

The last block contains a function that gets the **index.htm** file from the templetes folder and displays it when you go to a home page. Also, the F3::run() line starts the FatFree framework.

```
function home() {
      echo Template::serve('index.htm');
	}
F3::run();
```

### Create the ComparisonWe have routes (**index.php**) so all that remains is to create template and controller files with the same name as declared in **index.php**. In the template file, we will create a form that takes user input and shows the results of a comparison. In the controller, we get data entered by the user, and transfer it for processing.

1.  Create two folders in the root folder: "templates" and "inc\_samples".
2.  In the "templates" folder create the **sample01.htm** file and enter the code below.
    
    ```
    <\\!DOCTYPE html>
    ```
    
    ### [GroupDocs PHP SDK Samples](/index.php) - Sample19
    
    _This sample will show how to Compare documents using PHP SDK_ You entered: ClientID = {{@userId}} PrivateKey = {{@privateKey}} Source file Id = {{@sourceFileId}} Target file Id = {{@targetFileId}} Call back url = {{@callbackURL}} {{@error}}
    
    Enter data for request and press "Make request" button GroupDocs ClientID GroupDocs PrivateKey sourceFileId targetFileId callbackUrl
    
    Results: {{@iframe}}
    

#### Understanding sample01.htmThis block declares the page styles, title and language:

This block shows data entered by the user: {{@variable name}} is syntax for transferring a variable from the controller to a template.```
You entered:

ClientID = {{@userId}}

PrivateKey = {{@privateKey}}

Source file Id = {{@sourceFileId}}

Target file Id = {{@targetFileId}}

Call back url = {{@callbackURL}}
```This code creates a form with inputs. In the form Action we assign a controller name which we declare in the routes (don't worry: we will create the controller file later). {{@error}}

Enter data for request and press "Make request" button GroupDocs ClientID GroupDocs PrivateKey sourceFileId targetFileId callbackUrl

And it's time to show results. The result of the work is written down by the controler in a variable: {{@iframe}}```
div  style="padding:20px; border:1px solid black;">

 Results: 

{{@iframe}}
```We're finished with the template file and have a form and results.

### Creating a ControllerLet's create a controler which gets the entered data, creates all objects and makes a request from the Comparison API.

1.  In the inc\_sample folder, create a **sample01.php**file containing the code below.
    
    ```
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
    
        function Compare($clientId, $privateKey, $sourceFileId, $targetFileId, $callbackUrl)
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
    
                //###Make request to ComparisonApi using user id
    
                //Comparison of documents were: $clientId - user GuId, $sourceFileId - source file Guid in which will be provided compare,
                //$targetFileId - file GuId with wich will compare sourceFile, $callbackUrl - Url which will be executed after compare
                $info = $CompareApi->Compare($clientId, $sourceFileId, $targetFileId, $callbackUrl);
                //Check request status
                if($info->status == "Ok") {
                    //Create CAsyncApi object
                    $asyncApi = new AsyncApi($apiClient);
                    //Delay necessary that the inquiry would manage to be processed
                    sleep(5);
                    //Make request to api for get document info by job id
                    $jobInfo = $asyncApi->GetJobDocuments($clientId, $info->result->job\_id);
                    //Get file guid
                    $guid = $jobInfo->result->outputs\[0\]->guid;
                    // Construct iframe using fileId
                    $iframe = '<iframe src="https://apps.groupdocs.com/document-viewer/embed/' . $guid . '" frameborder="0" width="100%" height="600"></iframe>';
    
                }
                //If request was successfull - set url variable for template
                return F3::set('iframe', $iframe);
            }
        }
    
        try {
             Compare($clientId, $privateKey, $sourceFileId, $targetFileId, $callbackUrl);
    
        } catch(Exception $e) {
            $error = 'ERROR: ' .  $e->getMessage() . "\\n";
            f3::set('error', $error);
        }
        //Process template
        f3::set('sourceFileId', $sourceFileId);
        f3::set('targetFileId', $targetFileId);
        f3::set('callbackURL', $callbackUrl);
    //    f3::set('result', $result);
        echo Template::serve('sample01.htm');
    ```
    

In this code we have comments for each step but lets take a look at it block by bock.

#### Understanding the ControlerFirst, declare all necessary variables. For example, F3::set('userId', ''); declares the String variable userId, equal to an empty line. With syntax like F3::set you can declare variables for the template. If you take a look at template code, you'll see this variable in the You entered block. After we set the template variables, set local variables which get the POST data from thetemplate. In FatFree, you can get POST data with F3::get('POST\["client\_id"\]');. Here, we get data entered by the user into the client\_id field.```
F3::set('userId', '');
    F3::set('privateKey', '');
    f3::set('result', "");
    $clientId = F3::get('POST\["client\_id"\]');
    $privateKey = F3::get('POST\["private\_key"\]');
    $sourceFileId = f3::get('POST\["sourceFileId"\]');
    $targetFileId = f3::get('POST\["targetFileId"\]');
    $callbackUrl = f3::get('POST\["callbackUrl"\]');
```In the next step we create a function in which we transfer all the entered data and check if the user filled in all the required fields.```
function Compare($clientId, $privateKey, $sourceFileId, $targetFileId, $callbackUrl)
    {
         //### Check clientId, privateKey and fileGuId
        if (empty($clientId) || empty($privateKey) || empty($sourceFileId) || empty($targetFileId)) {
            throw new Exception('Please enter all required parameters');
        } else {
```Next, create objects of different classes nedded to make a request to the Comparison API. Also, in the first two lines of this block, we set the template variables that do not change. We need these variables for authorization in the API.```
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
```This is the major part of our code, where the magic happens. To compare two documents, simply trigger the necessary method from the Comparison API object. In this case, the method is Compare. This method sends a request to the Comparison API which then does the comparison and sends back an object with the results. The Compare method takes the parameters:

*   $clientId - user GUID.
*   $sourceFileId - source file GUID, in which the comparison content is provided.
*   $targetFileId - the file GUID of the file that will be compared to the source file.
*   $callbackUrl - URL which will be executed after the comparison.

The results of this method is a job ID which we can get by this line: $info->result->job\_id. To see it in a new iframe document generated by the comparison, create an AsyncApi object which has the GetJobDocuments method used to show compared file GUID by job ID. After that, we generate a URL for the iframe. At last we can transfer the generated iframe URL with the compared file GUID to the template. The callback URL is something like Action in the form. You can declare any URL for the handler that will send data to the API when the job is done.```
//###Make request to ComparisonApi using user id

            //Comparison of documents were: $clientId - user GuId, $sourceFileId - source file Guid in which will be provided compare,
            //$targetFileId - file GuId with wich will compare sourceFile, $callbackUrl - Url which will be executed after compare
            $info = $CompareApi->Compare($clientId, $sourceFileId, $targetFileId, $callbackUrl);
            //Check request status
            if($info->status == "Ok") {
                //Create CAsyncApi object
                $asyncApi = new AsyncApi($apiClient);
                //Delay necessary that the inquiry would manage to be processed
                sleep(5);
                //Make request to api for get document info by job id
                $jobInfo = $asyncApi->GetJobDocuments($clientId, $info->result->job\_id);
                //Get file guid
                $guid = $jobInfo->result->outputs\[0\]->guid;
                // Construct iframe using fileId
                $iframe = '<iframe src="https://apps.groupdocs.com/document-viewer/embed/' . $guid . '" frameborder="0"
width="100%" height="600"></iframe>';

            }
            //If request was successfull - set url variable for template
            return F3::set('iframe', $iframe);
        }
    }
```In the last block of controler code we execute the function. After succeful execution of the function, we can set others variables for the template, such as sourceFileId.```
try {
         Compare($clientId, $privateKey, $sourceFileId, $targetFileId, $callbackUrl);

    } catch(Exception $e) {
        $error = 'ERROR: ' .  $e->getMessage() . "\\n";
        f3::set('error', $error);
    }
    //Process template
    f3::set('sourceFileId', $sourceFileId);
    f3::set('targetFileId', $targetFileId);
    f3::set('callbackURL', $callbackUrl);
    echo Template::serve('sample01.htm');
```

### Run the CodeTo run the sample:

1.  Open a browser and go to root/sample01.
2.  Fill in a form.

### SummaryThis is how it works: the template sends data entered by a user to the controller which processes it, creating objects and triggering methods and transferring data to them. When a method is triggered, it sends a request to the API, which in turn processes the transferred data and sends a request to the GroupDocs account. In reply, GroupDocs sends the result of the processing which is transferred back on a chain that is processed graudually. ![Block Diagram](https://blog.groupdocs.com/wp-content/uploads/sites/4/2013/02/Block-Diagram1.png "Block Diagram")





