---
title: 'How to Deploy .NET Project on the AppHarbor'
date: Fri, 22 Mar 2013 13:33:20 +0000
draft: false
url: /2013/03/22/how-to-deploy-net-project-on-the-appharbor/
author: 'Derek Hyland'
summary: ''
tags: ['API', 'document management', 'GroupDocs API SDK', 'online document management system', 'zArchive']
---

This article explains the basics of using [AppHarbor](https://appharbor.com/). In this article, I'll use the .NET SDK Samples project to show how to deploy a .NET project on AppHarbor.

## Requirements

*   .NET project
*   App account
*   GitHub

## PreparingFirst of all, we need a AppHarbor account. If you don't have one yet, please create one. Registration on AppHarbor is similar to any other site: sign up from [the AppHarbor home page](https://appharbor.com/) by clicking the **Sign up** button. Ok now we have AppHarbor account and we are ready to deploy.

1.  Clone the GroupDocs GitHub repository containing [the .NET SDK](https://github.com/groupdocs).
2.  Create an empty folder anywhere on your local machine. Name it **groupdocs-dotnet-samples**.
3.  Go to the folder with the cloned repository and then to the **examples** folder. Here you can see some folders, one of them will be **api-samples**.
4.  Copy the content of the **api-samples**folder. \[caption id="attachment\_1746" align="aligncenter" width="640" caption="Copying content from the api-samples folder"\]![Copying content from the api-samples folder](https://blog.groupdocs.com/wp-content/uploads/sites/4/2013/03/Copying-content-from-the-api-samples-folder.png "Copying content from the api-samples folder")\[/caption\]
5.  Post the copied content to the empty folder created in step 2.

Preparation is complete. If you can't wait and want to see the example working, you can go straight to [GroupDocs .NET API Samples](http://groupdocs-dotnet-samples.apphb.com/) and see our samples at work.

## Deploy to AppHarbor

1.  Login to [AppHarbor](https://appharbor.com). and go to **Your Applications**. \[caption id="attachment\_1750" align="aligncenter" width="640" caption="The Your Applications link"\]![The Your Applications link](https://blog.groupdocs.com/wp-content/uploads/sites/4/2013/03/The-Your-Applications-link.png "The Your Applications link")\[/caption\]
2.  Create a new application:
    1.  Enter an application name.
    2.  Choose United States or Europe.
    3.  Click **Create new**. \[caption id="attachment\_1753" align="aligncenter" width="640" caption="Creating a new application"\]![Creating a new application](https://blog.groupdocs.com/wp-content/uploads/sites/4/2013/03/Creating-a-new-application.png "Creating a new application")\[/caption\]
        
3.  Open a console and cd to the folder that the project was copied to. It's a **groupdocs-dotnet-samples** folder.
4.  Enter the command git init
5.  Then enter the command git add . (This adds all files.)
6.  Enter the command git commit -m "Initial commit"  \[caption id="attachment\_1757" align="aligncenter" width="640" caption="The result of steps 3, 4, 5 and 6 in the console"\]![The result of steps 3, 4, 5 and 6 in the console](https://blog.groupdocs.com/wp-content/uploads/sites/4/2013/03/The-result-of-steps-3-4-5-and-6-in-the-console.png "The result of steps 3, 4, 5 and 6 in the console")\[/caption\]
7.  Go to **Your Applications**in AppHarbor and click on you application.  \[caption id="attachment\_1766" align="aligncenter" width="640" caption="Application panel"\]![Application panel](https://blog.groupdocs.com/wp-content/uploads/sites/4/2013/03/Application-panel1.png "Application panel")\[/caption\]
8.  Copy the URL of your application.    \[caption id="attachment\_1770" align="aligncenter" width="544" caption="Button for copying URL"\]![Button for copying URL](https://blog.groupdocs.com/wp-content/uploads/sites/4/2013/03/Button-for-copying-URL.png "Button for copying URL")\[/caption\]
9.  Return to the console and, as a final step, enter the command git push \[URL of the api you copied\] master**.**   \[caption id="attachment\_1773" align="aligncenter" width="640" caption="Deploying to AppHarbor"\]![Deploying to AppHarbor](https://blog.groupdocs.com/wp-content/uploads/sites/4/2013/03/Deploying-to-AppHarbor.png "Deploying to AppHarbor")\[/caption\]

## Running a Project on AppHarbourAfter these steps, our local project is deployed on AppHarbor. Lets go to AppHarbor and run the project. In **Applications**, we see the build status of the current commit. If it is **Active**, there is a link to run it. \[caption id="attachment\_1778" align="aligncenter" width="640" caption="Status of the current build and link to run API"\]![Status of the current build and link to run API](https://blog.groupdocs.com/wp-content/uploads/sites/4/2013/03/Status-of-the-current-build-and-link-to-run-API.png "Status of the current build and link to run API")\[/caption\] That's all, as easy as a piece of cake.




