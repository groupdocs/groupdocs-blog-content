---
title: 'Extract Data from Database Files using C#'
date: Fri, 08 Nov 2019 09:52:26 +0000
draft: false
url: /2019/11/08/extract-data-from-database-files-using-csharp/
author: 'Usman Aziz'
summary: ''
tags: ['Extract data from database', 'SQLite DB']
categories: ['GroupDocs.Parser for .NET', 'GroupDocs.Parser Product Family']
---

The [database](https://en.wikipedia.org/wiki/Database) is considered to be an integral part of most of the applications. Be it a desktop, web or mobile application, database plays a vital role in storing, accessing and manipulating the data. There are many database management systems that allow creating and managing databases for you.

However, there could be a scenario when you need a way to extract data from database files, i.e. **.db** file, without installing a database management system or writing the SQL queries. How would you parse the database file in such a case and get the data from it?

In this article, I am going to demonstrate how easily you can extract the data from the tables in an SQLite database without writing SQL queries. I am going to use [GroupDocs.Parser for .NET](https://products.groupdocs.com/parser/net) API which supports extracting data from databases via [ADO.NET](https://en.wikipedia.org/wiki/ADO.NET).

## Steps to Extract Data from Tables in SQLite Database (.db)

**1.** Create a new project in Visual Studio.

**2\.** Install **GroupDocs.Parser for .NET** from [NuGet](http://nuget.org/packages/GroupDocs.Parser).

**3.** Add the following namespaces.

{{< gist GroupDocsGists 5f9beb5ce2a3e3c5e14fca657762b649 "ExtractDataFromDatabase_Namespaces.cs" >}}

**4.** Prepare the connection string.

{{< gist GroupDocsGists 5f9beb5ce2a3e3c5e14fca657762b649 "ExtractDataFromDatabase_ConnectionString.cs" >}}

**5.** Load the database file in the [Parser](https://apireference.groupdocs.com/net/parser/groupdocs.parser/parser) object.

{{< gist GroupDocsGists 5f9beb5ce2a3e3c5e14fca657762b649 "ExtractDataFromDatabase_LoadDatabase.cs" >}}

**6.** Get list of the tables in the database using [Parser.GetToc](https://apireference.groupdocs.com/net/parser/groupdocs.parser/parser/methods/gettoc) method.

{{< gist GroupDocsGists 5f9beb5ce2a3e3c5e14fca657762b649 "ExtractDataFromDatabase_GetTableList.cs" >}}

**7.** Iterate over the tables and extract data.

{{< gist GroupDocsGists 5f9beb5ce2a3e3c5e14fca657762b649 "ExtractDataFromDatabase_GetDataFromTables.cs" >}}

## Complete Code

{{< gist GroupDocsGists 5f9beb5ce2a3e3c5e14fca657762b649 "ExtractDataFromDatabaseFile.cs" >}}

## Output



{{< figure align=center src="images/GetDataFromDatabase.png" alt="C# code to Extract Data from SQLite Database">}}


Visit the [documentation](https://docs.groupdocs.com/parser/net) to explore more about **GroupDocs.Parser for .NET** API. You can download or clone the source code examples from [GitHub repository](https://github.com/groupdocs-parser/GroupDocs.Parser-for-.NET). In case of any query, just post it on the [forum](https://forum.groupdocs.com/c/parser).




