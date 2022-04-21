---
title: 'Password Protected Files Comparison Issue is Resolved'
date: Tue, 02 Apr 2019 13:36:34 +0000
draft: false
url: /2019/04/02/password-protected-files-comparison-issue-is-resolved/
author: 'Atir Tahir'
summary: ''
tags: []
categories: ['GroupDocs.Comparison for Java', 'GroupDocs.Comparison Product Family']
---

GroupDocs.Comparison for Java 19.3 rolls out with major bug fixes. When password protected files were compared, result was null. This might be a showstopper for you but not anymore.

Moving ahead, comparing a PDF with itself was not working, result was null. We fixed this issue.

Most importantly, **MultiCompare** was also returning null. Code below explains how it works.

{{< gist GroupDocsGists 53b52dccc23b8462c1f8e42b74443546 "multicomparison.cs" >}}

You can compare a source file with multiple target files. Sounds appealing, isn't it? Don't wait, download the latest release and implement this feature.

You can download the API [here](https://downloads.groupdocs.com/comparison/java). Explore [documentation](https://docs.groupdocs.com/display/comparisonjava/Home) and our open source example projects.




