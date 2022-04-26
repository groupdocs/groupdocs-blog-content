---
title: 'How to Use New Login Method in Plugins and Services'
date: Fri, 31 May 2013 15:21:56 +0000
draft: false
url: /2013/05/31/how-to-use-new-login-method-in-plugins-and-services/
author: 'Derek Hyland'
summary: ''
tags: ['API', 'document management', 'GroupDocs API', 'GroupDocs PHP SDK', 'GroupDocs Plugins', 'php api', 'zArchive']
---

This article explains how to use the new method **LoginUser**, added to the new [GroupDocs SDK](https://github.com/groupdocs).

## Requirements

*   PHP 5.3
*   Apache ModRewrite
*   PHP Curl extension
*   PHP Sockets extension (php\_sockets.dll)
*   GroupDocs [PHP SDK](https://github.com/groupdocs)
*   composer.phar (Download from [http://getcomposer.org/download/](https://getcomposer.org/download/) or use the included version.)
*   FatFree framework ([https://github.com/bcosca/fatfree](https://github.com/bcosca/fatfree))

We already know how to install the Fatfree framework and prepare for creating the sample from [a previous article](https://blog.groupdocs.com/how-to-convert-files-with-groupdocs-php-sdk). The sample that we create in this article is not much different from other FatFree samples. We need a template file with a form and a controller file to process any entered data.

## LogicFor security reasons the GroupDocs plugins and services use the User ID and API key to authorize a GroupDocs account from remote plugins. But this method is not comfortable for users which is why the new SDK release added a new method called LoginUser. With this method a user can be authorized in GroupDocs using email and password like in normal account authorization. As you've already guessed, this method takes two parameters:

1.  String email
2.  String password

So according to this all we need to do is take this data from a form and transfer it to the method. In response, the method returns all user info, including the User ID and API key. To use the method we need to use a little trick. To call the LoginUser method, as for all other methods, we have to create and object of the class that contains the method. So we have to create objects like GroupDocsRequestSigner and ApiClient. But to create these objects, don't we need the User ID and API key? Yes, but we can avoid using them and the trick is in that the User ID and API key is needed to sign a request to the server, but LoginUser is a **public** method which doesn't need to be signed. So we can create GroupDocsRequestSigner and ApiClient objects with any data instead of the User ID and API key. For example, let's use the string "12345".

## ImplementationThe template file is the same as in the article about [two ways of updating files to GroupDocs accounts](https://blog.groupdocs.com/two-ways-of-uploading-files-into-a-groupdocs-account). Because of this, I will not explain the template file but go straight to the Controller file where all the magic happens. Here is a sample of the code:```
//###Set variables and get POST data
    F3::set('email', '');
    F3::set('password', '');

    $email = F3::get('POST\["email"\]');
    $pass = F3::get('POST\["password"\]');
    //Create signer object
    $signer = new GroupDocsRequestSigner("12345");
    //Create apiClient object
    $apiClient = new APIClient($signer);
    $sharedapi = new SharedApi($apiClient);
    //Login and get user info
    $getUserInfo = $sharedapi->LoginUser($email, $pass);
```  In this code we get POST data from the form where the user enters the email and password for his GroupDocs account. Them we create the GroupDocsRequestSigner and ApiClient objects using "12345" instead of the API key and SharedApi object to get access to the LoginUser method. In response we get the UserInfoResponse object. This object has all the data about the user account. We are interested in the User ID and API key because we need them to work with GroupDocs data in the account. That's the entire reason we used the LoginUser method: to get these two parameters. We have all the the account data and from this, we can get the User ID and API key like this:

```
    $userId = $getUserInfo->result->user->guid;
    $apiKey = $getUserInfo->result->user->pkey;
```

The UserInfoResponse object has this structure: \[caption id="attachment\_2418" align="alignnone" width="602" caption="The structure of the UserInfoResponse object"\]![The structure of the UserInfoResponse object](https://blog.groupdocs.com/wp-content/uploads/sites/4/2013/05/The-structure-of-the-UserInfoResponse-object.png "The structure of the UserInfoResponse object")\[/caption\] That's all. Very simple, don't you think?




