---
title: 'How to Upload PHP Project to Heroku? - Advanced Steps'
date: Fri, 17 May 2013 14:04:35 +0000
draft: false
url: /2013/05/17/how-to-upload-php-project-to-heroku-advanced-steps/
author: 'Derek Hyland'
summary: ''
tags: ['API', 'git', 'GroupDocs PHP SDK', 'Heroku', 'heroku toolbelt', 'zArchive']
---

In the [previous article,](https://blog.groupdocs.com/how-to-upload-php-project-to-heroku) we learned how to create a new PHP project on Heroku. But sometimes our project requires additional extensions that do not exist in the Heroku PHP configuration. So we need to find out how to create and install extensions for PHP on Heroku.

In this post, I'll show you these advanced steps, and create a PHP project on Heroku with the [GroupDocs PHP SDK Api Samples](https://github.com/groupdocs) application.

## Preparation

All required preparation are described in [previous article](https://blog.groupdocs.com/how-to-upload-php-project-to-heroku). Also, we need two PHP extensions such as Curl and Sockets that are used in our PHP Samples application.

## Build an extension on Heroku.

This can be done by opening a Heroku console, download the PHP source-code and compile the extension, then copying it over.

To create the Curl extension:

1.  Open console and cd to root folder of your API.
2.  \>heroku run bash ![](https://blog.groupdocs.com/wp-content/uploads/sites/4/2013/05/heroku-run-bash.png "heroku run bash")
3.  $ mkdir tmp
4.  $cd tmp
5.  git clonehttps://github.com/php/php-src.git ![](https://blog.groupdocs.com/wp-content/uploads/sites/4/2013/05/git-clonehttps.png "git clonehttps")
6.  $cd php-src
7.  $ cd ext/curl
8.  $ /app/php/bin/phpize ![](https://blog.groupdocs.com/wp-content/uploads/sites/4/2013/05/phpize.png "phpize")
9.  $ ./configure --with-php-config=/app/php/bin/php-config ![](https://blog.groupdocs.com/wp-content/uploads/sites/4/2013/05/Configure.png "Configure")
10.  $ make
11.  $ cd modules

To create the Sockets extension, take the same steps.

Don't close the console. We will use it for the next steps.

## Download lib from Heroku.

Now we have compiled the extension, but this file is on the Heroku server and we need it in our API.

To get the file from the server and add it to the API, we can create an empty repo on GitHub and clone it to the temp folder in which we compile the extension. Then copy the extension file and push it to GitHub. After that, you can download it from GitHub to the **lib** folder and push it to Heroku.

Lets see this logic in practical steps by adding the Curl extension:

1.  In the mudel folder, $ ssh-keygen -t rsa
2.  $ cat /app/.ssh/id\_rsa.pub  
    This command shows your ssh key file content in the console. Copy it.
3.  Add your SSH key to GitHub.
4.  $ git clone yourreposshurl
5.  $ mv curl.so cloned folder name
6.  $ cd cloned folder
7.  $ git add .
8.  $ git commit -m "adding extension"
9.  $ git push origin master
10.  $ exit

Now we have our extension file in the GitHub repository and we can download it.

To add the Sockets extension, take the same steps.

## Add lib and php.ini file to your app and upload them to Heroku

In the root folder of the API, create a **lib** folder and save the downloaded file there. And there's only one thing left to do: create a **php.ini** file in the root folder of the API that points to that extension. The changes are committed. To do all this open console and:

1.  cd to the API root folder
2.  \>mkdir lib
3.  cd to the folder where the downloaded extension folder is.
4.  \>mv curl.so rootfolderapi/lib
5.  cd to the API root folder.
6.  $ echo extension = /app/www/lib/curl.so > php.ini
7.  $ git add .
8.  $ git commit -m "adding extension"
9.  $ git push origin master

That's all, your new PHP application is ready to use on Heroku. Enjoy!

## See Also

*   [How to Upload PHP Project to Heroku?](https://blog.groupdocs.com/2013/05/10/how-to-upload-php-project-to-heroku/)




