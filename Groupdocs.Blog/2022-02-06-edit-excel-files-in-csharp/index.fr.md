---
title: "Comment éditer des fichiers Excel avec C#"
date: Sun, 06 Feb 2022 13:45:16 +0000
draft: false
url: /fr/2022/02/06/edit-excel-files-in-csharp/
author: 'Shoaib Khan'
summary: "Les formats de fichier de feuille de calcul les plus courants et les plus utilisés sont **XLS**, **XLSX** et **ODS**. Les célèbres Microsoft Excel et OpenOffice Calc prennent en charge ces formats et nous utilisons normalement ces formats pour la gestion des comptes et des différentes feuilles de calcul. Par conséquent, en tant que développeur, nous avons largement besoin de modifier par programmation des fichiers Excel dans nos applications. Dans cet article, nous expliquerons **comment modifier des fichiers Excel en C#** à l'aide de l'API .NET."
tags: ['Edit Excel file in CSharp', 'Edit Excel Files', 'Edit XLS in CSharp', 'Edit XLSX in CSharp', 'Spreadsheet Editing in CSharp']
categories: ['GroupDocs.Editor Product Family']
---

Les formats de fichier de feuille de calcul les plus courants et les plus utilisés sont **XLS**, **XLSX** et **ODS**. Les célèbres Microsoft Excel et OpenOffice Calc prennent en charge ces formats et nous utilisons normalement ces formats pour la gestion des comptes et des différentes feuilles de calcul. Par conséquent, en tant que développeur, nous avons largement besoin de modifier par programmation des fichiers Excel dans nos applications. Dans cet article, nous expliquerons **comment modifier des fichiers Excel en C#** à l'aide de l'API .NET.

Voici les sujets abordés brièvement dans cet article :

* [API .NET - Édition de feuilles de calcul Excel](#excel-editing-dotnet-api)
* [Modifier les fichiers de feuilles de calcul Excel en C#](#edit-excel-files)

## API .NET pour l'édition et l'automatisation des feuilles de calcul Excel {#excel-editing-dotnet-api}

GroupDocs présente l'API .NET pour l'édition de feuilles de calcul. Je vais l'utiliser dans les exemples C# de cet article. Il s'agit de l'API d'édition de documents et permet aux développeurs de charger, modifier et enregistrer divers formats de documents à l'aide d'éditeurs HTML WYSIWYG. En plus des formats de feuille de calcul XLS, XLSX et ODS, l'API prend en charge l'édition de divers autres [feuilles de calcul et formats pris en charge par MS Excel](https://docs.groupdocs.com/editor/net/supported-document-formats/) comme CSV, TSV, DSV, XLT, XLTX, XLTM, XLSM, XLSB, XLAM, SXC, SpreadsheetML, FODS, DIF.

Téléchargez le programme d'installation **DLLs** ou **MSI** à partir de la [section téléchargements](https://downloads.groupdocs.com/editor/net) ou installez l'API dans votre application .NET via [NuGet](https://www.nuget.org/packages/groupdocs.editor).

```
PM> Install-Package GroupDocs.Editor
```

## Modifier des fichiers Excel en C# {#edit-excel-files}

J'espère que vous avez correctement référencé l'API. Vous pouvez maintenant commencer rapidement à éditer vos documents Excel. Les étapes suivantes vous permettront de modifier les documents de la feuille de calcul à l'aide de C#.

* **Chargez** le fichier Excel.
* **Modifier** en conséquence avec les options.
* **Enregistrer** le document modifié.

### Charger la feuille de calcul Excel

Tout d'abord, chargez la feuille de calcul en fournissant le chemin/flux du document et le mot de passe (si le document est protégé par un mot de passe).

```
// Charger le fichier Excel à l'aide de C#
Options.SpreadsheetLoadOptions loadOptions = new SpreadsheetLoadOptions();
loadOptions.Password = "password"; // if any

// Charger la feuille de calcul
Editor editor = new Editor("path/spreadsheet.xlsx", delegate { return loadOptions; });
```

### Modifier le fichier Excel

Après le chargement, vous pouvez modifier la feuille de calcul chargée selon vos besoins. Nous allons maintenant remplacer toutes les occurrences de "Ancien nom de société" par "Nouveau nom de société" dans le premier onglet de la feuille de calcul. Les étapes suivantes vous permettent de modifier le fichier Excel en conséquence en C#.

* Chargez le fichier Excel à l'aide de [Editor](https://apireference.groupdocs.com/editor/net/groupdocs.editor/editor) et des [options de chargement](https://apireference.groupdocs.com/editor/net/groupdocs.editor.options/spreadsheetloadoptions).
* Préparez les [Options d'édition de feuille de calcul](https://apireference.groupdocs.com/editor/net/groupdocs.editor.options/spreadsheeteditoptions) pour extraire la feuille/l'onglet exact.
* [Extraire](https://apireference.groupdocs.com/editor/net/groupdocs.editor/editabledocument/methods/index) le contenu de l'onglet.
* Modifier le contenu de l'onglet.
* Vous pouvez extraire les images et toutes les ressources de l'onglet sélectionné.
* Créez le nouveau [EditableDocument](https://apireference.groupdocs.com/editor/net/groupdocs.editor/editabledocument) en utilisant le contenu modifié.
* Enregistrez la feuille de calcul d'édition à l'aide de la méthode [Save()](https://apireference.groupdocs.com/editor/net/groupdocs.editor/editor/methods/save/index) appropriée.

Le code source C# suivant modifie le fichier Excel et modifie son contenu.

```
// Modifier la feuille de calcul Excel à l'aide de C#

Options.SpreadsheetLoadOptions loadOptions = new SpreadsheetLoadOptions();
// loadOptions.Password = "mot de passe" ;

// Charger la feuille de calcul
Editor editor = new Editor("path/spreadsheet.xlsx", delegate { return loadOptions; });

// Obtenir le 1er onglet de la feuille de calcul
SpreadsheetEditOptions sheetTab1EditOptions = new SpreadsheetEditOptions();
sheetTab1EditOptions.WorksheetIndex = 0; // first worksheet

// Obtenir le balisage HTML d'une instance EditableDocument
EditableDocument firstTab = editor.Edit(sheetTab1EditOptions);
string bodyContent = firstTab.GetBodyContent(); // HTML markup from inside the HTML -> BODY element
string allContent = firstTab.GetContent();      // Full HTML markup of all document, with HTML -> HEAD header and all its content

List<IImageResource> onlyImages = firstTab.Images;
List<IHtmlResource> allResourcesTogether = firstTab.AllResources;

string editedContent = allContent.Replace("Company Name", "New Company Name");
EditableDocument afterEdit = EditableDocument.FromMarkup(editedContent, allResourcesTogether);
```

### Enregistrer le fichier Excel modifié avec les options

Après l'édition, lors de l'enregistrement du contenu de la feuille de calcul modifiée, vous pouvez définir diverses options. Ces options incluent ; définir le mot de passe, le format de sortie, la protection, etc. Je définis les options ci-dessus dans le code mentionné ci-dessous et enregistre la feuille de calcul modifiée en tant que fichier XLSX protégé par mot de passe et protégé en écriture.

```
// Enregistrez le fichier Excel avec le contenu mis à jour à l'aide de C#
// Créer des options de sauvegarde
SpreadsheetFormats xlsxFormat = SpreadsheetFormats.Xlsx;
Options.SpreadsheetSaveOptions saveOptions = new SpreadsheetSaveOptions(SpreadsheetFormats.Xlsx);

// Définir un nouveau mot de passe d'ouverture
saveOptions.Password = "newPassword";
saveOptions.WorksheetProtection = new WorksheetProtection(WorksheetProtectionType.All, "WriteProtectionPassword");

// Créer un flux de sortie
using (FileStream outputStream = File.Create("path/editedSpreadsheet.xlsx"))
{
    editor.Save(afterEdit, outputStream, saveOptions);
}
```

## Obtenez une licence gratuite

Vous pouvez [obtenir une licence temporaire gratuite](https://purchase.groupdocs.com/temporary-license) afin d'utiliser l'API sans les limitations d'évaluation.

## Conclusion

Pour conclure, nous avons expliqué comment modifier des documents Excel en C# à l'aide de l'API d'édition de documents pour les applications .NET. Vous pouvez utiliser l'API avec les éditeurs WYSIWYG pour l'édition visuelle de vos documents. Après cela, vous pouvez continuer à créer votre propre éditeur de tableur en ligne.

Pour plus de détails, d'options et d'exemples, vous pouvez consulter la [documentation](https://docs.groupdocs.com/editor/net) et le référentiel [GitHub](https://github.com/groupdocs-editor) . Pour toute autre question, contactez le support sur le [forum](https://forum.groupdocs.com/c/assembly).

## Articles Liés

* [Modifier des documents Word en C#](https://blog.groupdocs.com/2021/03/26/edit-word-documents-in-csharp/)
* [Modifier les données des fichiers XML à l'aide de C#](https://blog.groupdocs.com/2021/11/02/edit-xml-files-using-csharp/)

## Voir également

* [API d'édition de documents sur site](https://products.groupdocs.com/editor/family)
* [API d'édition de documents et d'automatisation Cloud](https://products.groupdocs.cloud/editor/family)
* [Modifier des fichiers Excel en ligne](https://products.groupdocs.app/editor/excel)





