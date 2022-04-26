---
title: "Modifier des fichiers XML à l'aide de C#"
date: Tue, 02 Nov 2021 13:18:00 +0000
draft: false
url: /fr/2021/11/02/edit-xml-files-using-csharp/
author: 'Shoaib Khan'
summary: "XML fait partie des formats structurés recommandés par le W3C, couramment utilisés pour stocker et transmettre des données. Les développeurs ont largement besoin de modifier les données XML stockées avec les applications. Pour faciliter l'exigence de modification, cet article explique **comment modifier les données du fichier XML à l'aide de C#**."
tags: ['Edit XML File using C#', 'Edit XML in CSharp', 'How to Edit XML']
categories: ['GroupDocs.Editor Product Family']
---

XML fait partie des formats structurés recommandés par le W3C, couramment utilisés pour stocker et transmettre des données. Les développeurs ont largement besoin de modifier les données XML stockées avec les applications. Pour faciliter l'exigence de modification, cet article explique **comment modifier les données du fichier XML à l'aide de C#**.

* [API .NET d'édition XML][1]
* [Comment modifier des fichiers XML à l'aide de C #][2]

## API .NET pour éditer des fichiers XML {#xml-edit-dotnet-api}

[GroupDocs.Editor][3] fournit des solutions d'édition de documents et des API pour [modifier une longue liste de différents formats de fichiers][4]. C'est l'API .NET qui peut être utilisée avec des éditeurs externes pour l'édition visuelle. Dans cet article, nous utiliserons GroupDocs.Editor pour .NET pour modifier les données XML dans l'application .NET.

Pour télécharger le programme d'installation **DLLs** ou **MSI**, visitez la [section téléchargements][5] ou installez l'API dans votre application .NET via [NuGet][6].

```
PM> Install-Package GroupDocs.Editor
```

## Comment modifier des fichiers XML à l'aide de C# {#how-to-edit-xml}

Venant directement à l'objectif, nous allons modifier les données XML en remplaçant une valeur par une autre. Voici les étapes pour modifier ou mettre à jour le fichier XML à l'aide de C#.

* Chargez le fichier de données XML à l'aide de la classe [Editor][7].
* Préparez les options d'édition XML à l'aide de la classe [XmlEditOptions][8].
* Pour l'édition, créez le [EditableDocument][9] comme contenu source en utilisant la méthode [Edit][10] et les options d'édition préparées.
* À partir du **EditableDocument**, obtenez le contenu original du fichier XML à l'aide de la méthode [GetContent][11].
* Mettre à jour les valeurs dans le contenu XML.
* Créez maintenant un nouveau **EditableDocument** à partir du contenu XML mis à jour à l'aide de la méthode [FromMarkup][12].
* Pour enregistrer le contenu mis à jour dans différents formats, préparez des options d'enregistrement pertinentes telles que [WordProcessingSaveOptions][13] ou [TextSaveOptions][14].
* Enregistrez les données XML mises à jour dans n'importe quel format à l'aide de la méthode [Save][15].

L'extrait de code C# suivant montre comment modifier le fichier XML et mettre à jour les données, puis l'enregistrer ultérieurement dans un autre format.

```
// Modifier le fichier XML en mettant à jour les valeurs à l'aide de C#
using (Editor editor = new Editor("path/data.xml"))
{
    // Create XML editing options
    Options.XmlEditOptions editOptions = new XmlEditOptions();
    editOptions.AttributeValuesQuoteType = QuoteType.DoubleQuote;
    editOptions.RecognizeEmails = true;
    editOptions.RecognizeUris = true;
    editOptions.TrimTrailingWhitespaces = true;

    // EditableDocument Settings
    using (EditableDocument beforeEdit = editor.Edit(editOptions))
    {
        // Edit whatever
        string originalTextContent = beforeEdit.GetContent();
        string updatedTextContent = originalTextContent.Replace("John", "Samuel");

        List<IHtmlResource> allResources = beforeEdit.AllResources;

        // Create EditableDocument with updated content
        using (EditableDocument afterEdit = EditableDocument.FromMarkup(updatedTextContent, allResources))
        {
            // Create WordProcessing save options
            Options.WordProcessingSaveOptions wordSaveOptions = new WordProcessingSaveOptions(WordProcessingFormats.Docx);
                        
            // Create TXT save options
            Options.TextSaveOptions txtSaveOptions = new TextSaveOptions();
            txtSaveOptions.Encoding = System.Text.Encoding.UTF8;

            // Save edited XML data in DOCX and TXT format
            editor.Save(afterEdit, "path/xmlData.docx", wordSaveOptions);
            editor.Save(afterEdit, "path/xmlData.txt", txtSaveOptions);
        }
    }
}
```

## Obtenez une licence gratuite

Vous pouvez [obtenir une licence temporaire gratuite][16] afin d'utiliser l'API sans les limitations d'évaluation.

## Conclusion

Pour résumer, nous avons appris à modifier par programme les données de fichiers XML à l'aide de C#. Vous pouvez explorer davantage d'autres fonctionnalités de GroupDocs.Editor à l'aide de la [documentation][17]. Pour clarifier toute ambiguïté, contactez-nous sur le [forum][18].

## Voir également

* [Modifier les fichiers XML en Java][19]
* [Comment modifier des documents Word en C #][20]



[1]: #xml-edit-dotnet-api
[2]: #how-to-edit-xml
[3]: https://products.groupdocs.com/editor/
[4]: https://docs.groupdocs.com/editor/net/supported-document-formats/
[5]: https://downloads.groupdocs.com/editor
[6]: https://www.nuget.org/packages/groupdocs.editor
[7]: https://apireference.groupdocs.com/editor/net/groupdocs.editor/editor
[8]: https://apireference.groupdocs.com/editor/net/groupdocs.editor.options/xmleditoptions
[9]: https://apireference.groupdocs.com/editor/net/groupdocs.editor/editabledocument
[10]: https://apireference.groupdocs.com/editor/net/groupdocs.editor/editor/methods/edit/index
[11]: https://apireference.groupdocs.com/editor/net/groupdocs.editor/editabledocument/methods/getcontent/index
[12]: https://apireference.groupdocs.com/editor/net/groupdocs.editor/editabledocument/methods/frommarkup
[13]: https://apireference.groupdocs.com/editor/net/groupdocs.editor.options/wordprocessingsaveoptions
[14]: https://apireference.groupdocs.com/editor/net/groupdocs.editor.options/textsaveoptions
[15]: https://apireference.groupdocs.com/editor/net/groupdocs.editor/editor/methods/save/index
[16]: https://purchase.groupdocs.com/temporary-license
[17]: https://docs.groupdocs.com/editor/net/
[18]: https://forum.groupdocs.com/c/assembly
[19]: https://blog.groupdocs.com/2021/11/06/edit-xml-files-in-java/
[20]: https://blog.groupdocs.com/2021/03/26/edit-word-documents-in-csharp/


