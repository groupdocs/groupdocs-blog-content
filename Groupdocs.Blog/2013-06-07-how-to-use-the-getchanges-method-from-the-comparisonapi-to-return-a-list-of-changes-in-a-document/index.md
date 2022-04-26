---
title: 'How to Use the GetChanges Method from the Comparison Api to Return a List of Changes in a Document'
date: Fri, 07 Jun 2013 12:54:36 +0000
draft: false
url: /2013/06/07/how-to-use-the-getchanges-method-from-the-comparisonapi-to-return-a-list-of-changes-in-a-document/
author: 'Derek Hyland'
summary: ''
tags: ['API', 'compare documents', 'document collaboration', 'document comparison', 'document management', 'documentation comparison tool', 'GroupDocs API', 'GroupDocs API SDK', 'GroupDocs Comparison', 'GroupDocs PHP SDK', 'zArchive']
---

This article explains how to use the GetChanges method from the ComparisonApi in the [GroupDocs SDK](https://github.com/groupdocs).

## Requirements

*   PHP 5.3
*   Apache ModRewrite
*   PHP Curl extension
*   PHP Sockets extension (php\_sockets.dll)
*   GroupDocs [PHP SDK](https://github.com/groupdocs)
*   composer.phar (Download from [http://getcomposer.org/download/](https://getcomposer.org/download/) or use the included version.)
*   FatFree framework ([https://github.com/bcosca/fatfree](https://github.com/bcosca/fatfree))

We already know how to install the Fatfree framework and prepare for creating the sample from [a previous article](https://blog.groupdocs.com/how-to-convert-files-with-groupdocs-php-sdk). The sample that we create in this article is not much different from other Fatfree examples. We need a template file with a form and a controller file to process entered data.

## LogicTo get a list of changes we need two documents to compare with the [GroupDocs Comparison](http://groupdocs.com/apps/comparison) API. We'll look at the output document that a comparison creates. Lets take a look at the logic that this sample implements:

1.  A user enter User ID, Private Key and File GUID (from GroupDocs account) into the form.
2.  The entered data is transfered to the controller for processing.
3.  Get entered data.
4.  Check entered data.
5.  Create GroupDocsRequestSigner, APIClient and ComparisonApi objects.
6.  Get all changes from document.
7.  Create a table with a list of changes.
8.  Return this table to the template.

You may think that this logic implies a lot of work, but that's not so: with GroupDocs PHP SDK it's very simple. And now, let me show you how.

## ImplementationFirst of all let's take a look at the complete controller code:```
<?php
    //<i>This sample will show how to use <b>GetChanges</b> method from ComparisonApi to return a list of changes of a Document</i>

    //###Set variables and get POST data
    F3::set('userId', '');
    F3::set('privateKey', '');
    f3::set('result', "");
    $clientId = F3::get('POST\["client\_id"\]');
    $privateKey = F3::get('POST\["private\_key"\]');
    $resultFileId = f3::get('POST\["resultFileId"\]');

    function getChanges($clientId, $privateKey, $resultFileId)
    {
         //### Check clientId, privateKey and fileGuId
        if (empty($clientId) || empty($privateKey) || empty($resultFileId)) {
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
            //Get changes list for document
            $info = $CompareApi->GetChanges($clientId, $resultFileId);

            //Check request status
            if($info->status == "Ok") {
                //###Create table with changes for template
                $table = "<table class='border'>";
                $table .= "<tr><td><font color='green'>Change Name</font></td><td><font color='green'>Change</font></td></tr>";
                //Count of iterations
                for($i = 0; $i < count($info->result->changes); $i++) {
                    //Cycle for the object of the top level
                    foreach($info->result->changes\[$i\] as $name => $content){
                        $table .= "<tr>";
                        //Check if the current element is an object
                        if(is\_object($content)){
                            //If object make cycle for the current object
                            foreach($content as $subName => $subContent) {

                               $table .= "<tr><td>" . $subName . "</td><td>" . $subContent . "</td></tr>";
                            }
                        } elseif(!is\_object($content)) {
                            //Get current element data
                            $table .= "<td>" . $name . "</td><td>" . $content . "</td>";
                            $table .= "</tr>";
                        }
                    }
                    $table .= "<tr bgcolor='#808080'><td></td><td></td></tr>";
                }
                $table .= "</table>";
                return f3::set('change', $table);
            } else {
                throw new Exception($info->error\_message);
            }
            //If request was successful - set url variable for template
//            return f3::set('change', $table);
        }
    }

    try {
         getChanges($clientId, $privateKey, $resultFileId);

    } catch(Exception $e) {
        $error = 'ERROR: ' .  $e->getMessage() . "\\n";
        f3::set('error', $error);
    }
    //Process template
    f3::set('resultFileId', $resultFileId);
    //    f3::set('result', $result);
    echo Template::serve('sample.htm');
```We will not dwell on how to get POST data from the template and check it - you can find out how to do that from [this previous article](https://blog.groupdocs.com/how-to-convert-files-with-groupdocs-php-sdk). To get all changes from the compared document, we need only one method: GetChanges (from the ComparisonApi class). This method take two parameters:

*   String Client ID
*   String File GUID of the compared file

Method call code:

```
 $info = $CompareApi->GetChanges($clientId, $resultFileId);
```

In the query result this method returns a ChangesResponse object that contains all the changes.

### Creating a table of changesTo create a table with a list of changes we must use several nested loops and checks. These loops go over all the elements and checks whether each element is an object or not. If an element is an object, the next nested loop for this element runs. As a result of the nested loops we get a table with all the changes were each successive iteration of the main loop is in separate rows. Code for the table creation:```
//###Create table with changes for template
                $table = "<table class='border'>";
                $table .= "<tr><td><font color='green'>Change Name</font></td><td><font color='green'>Change</font></td></tr>";
                //Count of iterations
                for($i = 0; $i < count($info->result->changes); $i++) {
                    //Cycle for the object of the top level
                    foreach($info->result->changes\[$i\] as $name => $content){
                        $table .= "<tr>";
                        //Check if the current element is an object
                        if(is\_object($content)){
                            //If object make cycle for the current object
                            foreach($content as $subName => $subContent) {

                               $table .= "<tr><td>" . $subName . "</td><td>" . $subContent . "</td></tr>";
                            }
                        } elseif(!is\_object($content)) {
                            //Get current element data
                            $table .= "<td>" . $name . "</td><td>" . $content . "</td>";
                            $table .= "</tr>";
                        }
                    }
                    $table .= "<tr bgcolor='#808080'><td></td><td></td></tr>";
                }
                $table .= "</table>";
```As you can see, we only have two nested loops. This is due to the fact that the ChangesResponse object can't have more than two-tiered nesting. On the first level, we have all the basic changes, and on the second level, we have info about the rectangle element. Now it is time to return this table to the template.

### Displaying the changes on screenTransferring data to template:```
try {
         getChanges($clientId, $privateKey, $resultFileId);

    } catch(Exception $e) {
        $error = 'ERROR: ' .  $e->getMessage() . "\\n";
        f3::set('error', $error);
    }
    //Process template
    f3::set('resultFileId', $resultFileId);
    //    f3::set('result', $result);
    echo Template::serve('sample.htm');
``` 

## ScreenshotsBelow are screenshots of how it looks in action. \[caption id="attachment\_2466" align="alignnone" width="602" caption="Form"\]![Form](https://blog.groupdocs.com/wp-content/uploads/sites/4/2013/06/Form.png "Form")\[/caption\] \[caption id="attachment\_2470" align="alignnone" width="602" caption="Table displaying the changes"\]![Table displaying the changes](https://blog.groupdocs.com/wp-content/uploads/sites/4/2013/06/Table-displaying-the-changes1.png "Table displaying the changes")\[/caption\]




