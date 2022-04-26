---
title: 'Index each letter as a separate word using GroupDocs.Search for .NET'
date: Thu, 10 Oct 2019 13:43:45 +0000
draft: false
url: /2019/10/10/index-each-letter-as-a-separate-word-using-groupdocs.search-for-.net/
aliases:
    - /2019/10/10/find-and-remove-watermarks-from-documents-in-java/
author: 'Atir Tahir'
summary: ''
tags: []
categories: ['GroupDocs.Search for .NET', 'GroupDocs.Search Product Family']
---

Are you looking for a full-text search API that allows you to search over a lot of document formats? In that case, GroupDocs.Search for .NET will meet your requirements. API creates index and then perform instant search across thousands of documents.

Those who are already working with the API, we have some new features and improvements. Moreover, some classes have been renamed to improve code readability. There are minor changes in the new version [19.10](https://docs.groupdocs.com/display/searchnet/GroupDocs.Search+for+.NET+19.10+Release+Notes), so the migration will not be too difficult. API architecture is optimized for better performance.  
After upgrading to v19.10, you need to replace the namespace usage across the entire project from _GroupDocs.Search_ to _GroupDocs.Search.Legacy_ to resolve build issues.

Lets go though the code changes:  
Old code sample:  
{{< gist GroupDocsGists 1e84ff71f71f21dc4274015c4f916a0c "oldsearchcode.cs" >}}

New code snippet:  
{{< gist GroupDocsGists 4919cfb96e5041b92507e8b2935a047b "newsearchcode.cs" >}}

You can observe the minor changes (e.g. _SearchParameters_ is changed to  
_SearchOptions_).

**Improvements**  

*   Highlight search results in short fragments
*   Enhance document metadata indexing with new formats

**New Features**

*   Index each letter as a separate word
*   Implemented ability to remove paths from index

**How to highlight search results in short fragments?**  
This improvement allows highlighting the search results in separate short fragments of the text, and not in the whole document. Below example shows how to generate short HTML snippets with highlighted found terms:  
{{< gist GroupDocsGists 297af296115ebb29b5a8ded0b6ec9cac "highlight.cs" >}}

**How to enhance document metadata indexing with new formats?**  
This improvement adds support for new document formats. These are mostly documents, the main content of which is not textual, therefore only the metadata of these documents is indexed:

*   MP3 – MPEG-2 Audio Layer III;
*   WAV – Waveform Audio File Format;
*   BMP – Bitmap Picture;
*   GIF – Graphical Interchange Format File;
*   JP2 – JPEG 2000 Core Image File;

For complete list visit this [article](https://docs.groupdocs.com/display/searchnet/Supported+Document+Formats).

**How to index each letter as a separate word?**  
This feature is designed to work with _hieroglyphic languages_ and allows you to index each character in the text as a separate word, regardless of the presence of separators.  
{{< gist GroupDocsGists 8fe7c13d4e392bf9af43d3255ef20749 "separateword.cs" >}}

**Ability to remove paths from index**  
When indexed paths are removed from an index, the index is updated and all removed documents and folders become inaccessible for search.  
{{< gist GroupDocsGists b70500ee090ed206f971b7c9f7d15125 "deleteindex.cs" >}}  

We'd recommend you to download the latest version and share your experience. In case of any issues, you can post on [forum](https://forum.groupdocs.com/c/search).




