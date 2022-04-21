---
title: "Modifier des documents Word en C#"
date: Fri, 26 Mar 2021 09:42:00 +0000
draft: false
url: /fr/2021/03/26/edit-word-documents-in-csharp/
author: 'Shoaib Khan'
summary: 'The most common and widely used word-processing file formats that are supported by Microsoft Word and OpenOffice Writer are DOC, DOCX, and ODT. We normally use these formats for drafting the documents. Therefore, as a developer, we widely need to edit Word documents in our applications programmatically. In this article, we will discuss how to edit Word documents in C# using the .NET API for document editing.

Voici les sujets abordés brièvement dans cet article :

* Édition et automatisation de documents Word
* Modifier des documents Word en C#

[Continuer la lecture...][1]'
tags: ['Edit DOCX in CSharp', 'Edit in CSharp', 'Edit Word doc in CSharp', 'Word Editing .NET API']
categories: ['GroupDocs.Editor Product Family']
---

Les formats de fichiers de traitement de texte les plus courants et les plus largement utilisés sont **DOC**, **DOCX** et **ODT**. Les célèbres Microsoft Word et OpenOffice Writer supportent ces formats et nous utilisons normalement ces formats pour rédiger les documents. Par conséquent, en tant que développeur, nous avons largement besoin de modifier par programmation des documents Word dans nos applications. Dans cet article, nous expliquerons **comment modifier des documents Word en C#** à l'aide de l'API .NET pour l'édition de documents.

Voici les sujets abordés brièvement dans cet article :

* [API .NET - Édition de documents Word][2]
* [Modifier des documents Word en C #][3]

## API .NET pour l'édition et l'automatisation de documents Word {#word-editing-dotnet-api}

Dans cet article, j'utiliserai [GroupDocs.Editor pour .NET][4] dans des exemples C#, qui est l'API d'édition de documents et permet aux développeurs de charger, modifier et enregistrer divers formats de documents à l'aide d'éditeurs HTML WYSIWYG. En plus des formats de document de traitement de texte, l'API prend en charge l'édition des feuilles de calcul, des présentations, des formats HTML, XML, TXT, DSV, TSV et CSV.

Téléchargez le programme d'installation **DLLs** ou **MSI** à partir de la [section téléchargements][5] ou installez l'API dans votre application .NET via [NuGet][6].

```
PM> Install-Package GroupDocs.Editor
```

## Modifier des documents Word en C# {#edit-word-docs-in-csharp}

Juste après avoir configuré l'API, vous pouvez rapidement passer à l'édition du document Word. Les étapes suivantes vous permettront de modifier le document de traitement de texte.

* Chargez le document Word.
* Modifier en conséquence avec des options.
* Enregistrez le document modifié.

### Charger le document Word

Tout d'abord, chargez le document en fournissant le chemin du document et le mot de passe, si le document est protégé.

```
using (FileStream fs = File.OpenRead(inputFilePath))
{
    Options.WordProcessingLoadOptions loadOptions = new WordProcessingLoadOptions();
    loadOptions.Password = "password-if-any";
}
```

### Modifier le document Word

Après le chargement, vous pouvez modifier le document chargé selon vos besoins. Ici, je remplace toutes les occurrences du mot "document" par le "document édité" dans un document Word en utilisant le code C# ci-dessous.

```
    using (Editor editor = new Editor(delegate { return fs; }, delegate { return loadOptions; }))
    {
        Options.WordProcessingEditOptions editOptions = new WordProcessingEditOptions();
        editOptions.FontExtraction = FontExtractionOptions.ExtractEmbeddedWithoutSystem;
        editOptions.EnableLanguageInformation = true;
        editOptions.EnablePagination = true;
        using (EditableDocument beforeEdit = editor.Edit(editOptions))
        {
            string originalContent = beforeEdit.GetContent();
            List<IHtmlResource> allResources = beforeEdit.AllResources;
            string editedContent = originalContent.Replace("document", "edited document");
        }
    }
```

### Enregistrez le document Word modifié avec les options

Enfin, lors de l'enregistrement du contenu du document modifié, vous pouvez définir diverses options. Ces options incluent ; pagination, définir le mot de passe, les paramètres régionaux, la protection ou l'optimisation de la mémoire. Je définis les options ci-dessus dans le code mentionné ci-dessous et enregistre le document modifié en tant que fichier DOCX protégé par mot de passe et en lecture seule.

```
using (EditableDocument afterEdit = EditableDocument.FromMarkup(editedContent, allResources))
{
    Options.WordProcessingSaveOptions saveOptions = new WordProcessingSaveOptions(WordProcessingFormats.Docx);
    saveOptions.EnablePagination = true;
    saveOptions.Locale = System.Globalization.CultureInfo.GetCultureInfo("en-US");
    saveOptions.OptimizeMemoryUsage = true;
    saveOptions.Password = "password";
    saveOptions.Protection = new WordProcessingProtection(WordProcessingProtectionType.ReadOnly, "write\_password");
    using (FileStream outputStream = File.Create("filepath/editedDocument.docx"))
    {
        editor.Save(afterEdit, outputStream, saveOptions);
    }
}
```

### Code complet

Pour votre commodité, je montre l'exemple C# complet qui est expliqué ci-dessus et il édite le document Word puis l'enregistre au format DOCX.

```
// Modifier un document Word en C # à l'aide de l'API d'édition et d'automatisation de documents GroupDocs
using (FileStream fs = File.OpenRead("filepath/document.docx"))
{   // Load Document
    Options.WordProcessingLoadOptions loadOptions = new WordProcessingLoadOptions();
    loadOptions.Password = "password-if-any";
    // Edit Document
    using (Editor editor = new Editor(delegate { return fs; }, delegate { return loadOptions; }))
    {
        Options.WordProcessingEditOptions editOptions = new WordProcessingEditOptions();
        editOptions.FontExtraction = FontExtractionOptions.ExtractEmbeddedWithoutSystem;
        editOptions.EnableLanguageInformation = true;
        editOptions.EnablePagination = true;

        using (EditableDocument beforeEdit = editor.Edit(editOptions))
        {
            string originalContent = beforeEdit.GetContent();
            List<IHtmlResource> allResources = beforeEdit.AllResources;

            string editedContent = originalContent.Replace("document", "edited document");
            // Save Document
            using (EditableDocument afterEdit = EditableDocument.FromMarkup(editedContent, allResources))
            {
                WordProcessingFormats docxFormat = WordProcessingFormats.Docx;
                Options.WordProcessingSaveOptions saveOptions = new WordProcessingSaveOptions(docxFormat);
                            
                saveOptions.EnablePagination = true;
                saveOptions.Locale = System.Globalization.CultureInfo.GetCultureInfo("en-US");
                saveOptions.OptimizeMemoryUsage = true;
                saveOptions.Password = "password";
                saveOptions.Protection = new WordProcessingProtection(WordProcessingProtectionType.ReadOnly, "write_password");

                using (FileStream outputStream = File.Create("filepath/editedDocument.docx"))
                {
                    editor.Save(afterEdit, outputStream, saveOptions);
                }
            }
        }
    }
}
```

Voici le document de sortie dans lequel toutes les occurrences sont remplacées à l'aide du code ci-dessus.



{{< figure align=center src="images/edited-document.png" alt="document docx édité à l'aide de l'API de l'éditeur" caption="Document de sortie - Toutes les occurrences sont remplacées">}}


## Conclusion

Pour conclure, nous avons discuté de l'édition de documents Word en C # à l'aide de l'API d'édition de documents pour les applications .NET. Vous pouvez utiliser l'API avec les éditeurs WYSIWYG pour l'édition visuelle de vos documents. Après cela, vous pouvez continuer à créer votre propre éditeur de documents. De même, vous pouvez également intégrer la fonctionnalité d'édition dans votre application .NET.

Pour plus de détails, d'options et d'exemples, vous pouvez visiter la [documentation][7] et le référentiel [GitHub][8]. Pour toute autre question, contactez le support sur le [forum][9].

## Articles Liés

* [Modifier les données des fichiers XML à l'aide de C #][10]
* [Comment éditer des fichiers XML en Java][11]

## Voir également

* [API d'édition de documents sur site][12]
* [API d'édition de documents et d'automatisation Cloud][13]
* [Modifier des documents Word en ligne][14]







[1]: https://blog.groupdocs.com/2021/03/26/edit-word-documents-in-csharp/
[2]: #word-editing-dotnet-api
[3]: #edit-word-docs-in-csharp
[4]: https://products.groupdocs.com/editor/net
[5]: https://downloads.groupdocs.com/editor/net
[6]: https://www.nuget.org/packages/groupdocs.editor
[7]: https://docs.groupdocs.com/editor/net
[8]: https://github.com/groupdocs-editor
[9]: https://forum.groupdocs.com/c/assembly
[10]: https://blog.groupdocs.com/2021/11/02/edit-xml-files-using-csharp/
[11]: https://blog.groupdocs.com/2021/11/06/edit-xml-files-in-java/
[12]: https://products.groupdocs.com/editor/family
[13]: https://products.groupdocs.cloud/editor/family
[14]: https://products.groupdocs.app/editor/word


