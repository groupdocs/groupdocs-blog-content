---
title: 'How to Fix a virtualPath Issue in the SharePoint 2013'
date: Tue, 06 Jan 2015 11:27:08 +0000
draft: false
url: /2015/01/06/how-to-fix-a-virtualpath-issue-in-the-sharepoint-2013/
author: 'Pavel Teplitsky'
summary: ''
tags: ['Annotation for .NET Library', 'GroupDocs Annotation', 'SharePoint', 'zArchive']
---

![GroupDocs.Annotation for .NET Library logo](https://blog.groupdocs.com/wp-content/uploads/sites/4/2014/02/GD_ANT_NETIcon_114.png)This article will guide you how to resolve a virtualPath issue that may appear in SharePoint 2013 when trying to add a 3rd party library (for example SignalR), or when you use the "~" symbol in the path. We encountered this issue while developing a plugin that allows you to [integrate the GroupDocs.Annotation for .NET library into SharePoint](https://github.com/groupdocs). Overall, the issue is quite strange, as it is not reported in the stack trace or logs. Googling it didn’t give us any valuable details either. After several hours of investigation, we found out that the issue appeared due to the SharePoint server got "frightened and faints" just because it saw the "~" symbol in the path (for example: Server.Mappath("~/testFolder/page.aspx")). To resolve the issue, we should teach SharePoint how to work with this symbol. For doing so, we’ll create a custom handler that will override SharePoint’s common path handler. First, we need to create a custom http module that can be deployed to SharePoint: 1. Open your VisualStudio 2012 as administrator. 2. Create an empty SharePoint project. 3. Create a new class with the following code:```
internal sealed class GdVirtualPathProvider : VirtualPathProvider
    {
        public override string CombineVirtualPaths(string basePath, string relativePath)
        {
            return Previous.CombineVirtualPaths(basePath, relativePath);
        }
        public override string GetCacheKey(string virtualPath)
        {
            return Previous.GetCacheKey(virtualPath);
        }
        public override VirtualDirectory GetDirectory(string virtualDir)
        {
            return Previous.GetDirectory(virtualDir);
        }
        public override VirtualFile GetFile(string virtualPath)
        {
            return Previous.GetFile(virtualPath);
        }
        public override string GetFileHash
        (string virtualPath, System.Collections.IEnumerable virtualPathDependencies)
        {
            return Previous.GetFileHash(virtualPath, virtualPathDependencies);
        }
        public override bool FileExists(string virtualPath)
        {
            // This is a workaround for System.Web.WebPages 
            // module initialization checking for precompiledapp which will 
            // not work with SPVirtualPathProvider
            if (virtualPath.ToLower().EndsWith("precompiledapp.config"))
                return false;
            return Previous.FileExists(virtualPath);
        }
        public override System.Web.Caching.CacheDependency GetCacheDependency
        (string virtualPath, System.Collections.IEnumerable virtualPathDependencies, System.DateTime utcStart)
        {
            if (virtualPath.ToLower().StartsWith("~/\_appstart."))
                virtualPath = virtualPath.TrimStart('~');
            return Previous.GetCacheDependency(virtualPath, virtualPathDependencies, utcStart);
        }
        public override bool DirectoryExists(string virtualDir)
        {
            try
            {
                return Previous.DirectoryExists(virtualDir);
            }
            catch (Exception e)
            {
                return false;
            }
        }
    }

```4\. Register this GDPathProvider in the HostingEnvironment via the custom HttpModule:```
internal sealed class GdHttpModule : IHttpModule
    {
        private static bool GdVirtualPathProviderInitialized = false;
        private static object \_lock = new object();
        public void Init(HttpApplication context)
        {
            if (GdVirtualPathProviderInitialized)
                return;
            lock (\_lock)
            {
                var GdVirtualPathProvider = new GdVirtualPathProvider();
                HostingEnvironment.RegisterVirtualPathProvider(GdVirtualPathProvider);
                GdVirtualPathProviderInitialized = true;
            }
        }
        public void Dispose()
        {
        }
    }  

```5\. In order to add the GdHttpModule to the application pipeline, we used the PreApplicationStartMethod assembly attribute that allows us to register the module via DynamicModuleUtility.RegisterModule when the application starts:```
 public static class PreApplicationStartCode
    {
        public static void Start()
        {
            DynamicModuleUtility.RegisterModule(typeof(GdHttpModule));
        }
    }

```6\. Finally, add this assembly to the web.config assemblies:

Done! Hope this will help you to deal with the issue when integrating any 3rd party libraries to your SharePoint environment.




