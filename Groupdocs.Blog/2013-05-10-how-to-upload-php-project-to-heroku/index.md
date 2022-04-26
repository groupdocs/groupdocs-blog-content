---
title: 'How to Upload PHP Project to Heroku?'
date: Fri, 10 May 2013 11:40:59 +0000
draft: false
url: /2013/05/10/how-to-upload-php-project-to-heroku/
author: 'Derek Hyland'
summary: ''
tags: ['git', 'GroupDocs PHP SDK', 'Heroku', 'heroku toolbelt', 'zArchive']
---

Heroku is a great opportunity for developers to try and test their code in a production environment. Originally created for Ruby projects, Heroku now supports Ruby, Java, Python and even PHP. Heroku's PHP project support is an undocumented feature so some additional skills are required do deploy such a project.

In this post, I'll show you the methods to create a PHP project on Heroku with the GroupDocs PHP SDK Api Samples application.

## Preparation

*   To get the PHP samples, you first need to clone the entire PHP SDK repository:  
    $ git clone git://github.com/groupdocs/groupdocs-php.git

*   Then go to the examples directory (**$ cd groupdocs-php/examples**) and copy the **api-samples** folder to the location where you want to create a Heroku project.

**Note**: Before uploading PHP API samples to Heroku, you need to update the PHP SDK in the API Samples project. You can check out our previous posts to find information on how to do this, for example, [How to use GroupDocs PHP SDK with Composer or a Built-in Autoloader](https://blog.groupdocs.com/how-to-use-groupdocs-php-sdk-with-composer-or-a-built-in-autoloader).

## Creating a Heroku project

To create a Heroku project, create a local repository with git (the example below assumes that you have Heroku toolbelt installed).

```
$ cd api-samples
$ git init
$ heroku create yourapplicationname
```

Note that in some guides, you might see the option \-stack cedar in the heroku create command. This option is not required anymore. \-stack cedar is now the default for new apps on Heroku.

If you've done everything correctly, Heroku creates a new application and adds a new remote (with the same name – heroku) to your local repository. You can check this with the command:  
$ git remote --v

You should see Heroku remote records with remote URLs for pull and push.

Now you can push your local repository to Heroku:

```
$ git push heroku master
```

All your commits from the local repository are pushed to Heroku. Heroku detects the type of your application – PHP project in our case – and starts the appropriate server to host the app.

If you use only standard PHP libraries, you can immediately start working with your new application on Heroku:

```
$ heroku apps open
```

But if your project/app requires a non-standard library (like the PHP API samples project), then you'll have problems with Heroku if you try to use it immediately. To be able to use such extensions, you need to perform additional steps:

1.  Build an extension on Heroku.
2.  Download lib from Heroku.
3.  Add lib and **php.ini** file to your app and upload them to Heroku.

I'll show you how to perform those advanced steps in the next blog post.

## See Also

*   [How to Upload PHP Project to Heroku? – Advanced Steps](https://blog.groupdocs.com/2013/05/17/how-to-upload-php-project-to-heroku-advanced-steps/)




