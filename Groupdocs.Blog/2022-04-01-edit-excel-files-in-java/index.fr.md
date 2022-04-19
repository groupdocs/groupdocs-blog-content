---
title: "Comment éditer des fichiers Excel en Java"
date: Fri, 01 Apr 2022 09:54:00 +0000
draft: false
url: /fr/2022/04/01/edit-excel-files-in-java/
author: 'Shoaib Khan'
summary: "**XLS**, **XLSX** et **ODS** sont parmi les formats de fichier de feuille de calcul les plus courants et les plus largement utilisés. Nous maintenons normalement divers comptes et différentes feuilles de calcul en utilisant les célèbres Microsoft Excel et OpenOffice Calc qui prennent en charge ces formats. Par conséquent, en tant que développeur, nous avons largement besoin de modifier par programmation des fichiers Excel dans nos applications. Dans cet article, nous discuterons de **comment modifier des fichiers Excel en Java**."
tags: ['Edit Excel Files', 'Edit Excel Files in Java', 'Excel Editing in Java', 'Excel Editing Java API']
categories: ['GroupDocs.Editor Product Family']
---



{{< figure align=center src="images/edit-excel-sheets-in-java.jpg" alt="Modifier des feuilles Excel en Java">}}


**XLS**, **XLSX** et **ODS** sont parmi les formats de fichier de feuille de calcul les plus courants et les plus largement utilisés. Nous maintenons normalement divers comptes et différentes feuilles de calcul en utilisant les célèbres Microsoft Excel et OpenOffice Calc qui prennent en charge ces formats. Par conséquent, en tant que développeur, nous avons largement besoin de modifier par programmation des fichiers Excel dans nos applications. Dans cet article, nous discuterons de **comment modifier des fichiers Excel en Java**.

Les sujets suivants sont traités dans cet article :

* [API Java pour l'édition de feuilles de calcul](#spreadsheet-editing-java-api)
* [Modifier des feuilles de calcul en Java](#edit-excel-files-in-java)

## API Java pour l'édition de feuilles de calcul Excel et l'automatisation {#spreadsheet-editing-java-api}

[GroupDocs.Editor](https://products.groupdocs.com/editor/) fournit une API Java pour l'édition de feuilles de calcul et permet aux développeurs de charger, modifier et enregistrer divers formats de documents à l'aide d'éditeurs HTML WYSIWYG. Outre les formats de feuille de calcul, l'API prend en charge l'édition de documents de traitement de texte, de présentations, HTML, XML, TXT, CSV et de nombreux autres formats.

### Télécharger ou configurer

Vous pouvez télécharger le fichier **JAR** à partir de la [section des téléchargements](https://downloads.groupdocs.com/editor), ou simplement obtenir les configurations du référentiel et des dépendances pour le pox.xml de votre **Maven-based** Applications Java.

```
<repository>
	<id>GroupDocsJavaAPI</id>
	<name>GroupDocs Java API</name>
	<url>http://repository.groupdocs.com/repo/</url>
</repository>
<dependency>
        <groupId>com.groupdocs</groupId>
        <artifactId>groupdocs-editor</artifactId>
        <version>20.11</version> 
</dependency>
```

## Modifier des feuilles de calcul Excel en Java {#edit-excel-files-in-java}

Vous pouvez modifier les feuilles de calcul juste après avoir configuré l'API. Vous pouvez obtenir tout le contenu, y compris les images, dans la feuille de calcul. Les étapes suivantes vous permettront de modifier les feuilles de calcul XLS/XLSX en Java.

* Préparez les options de chargement.
* Chargez la feuille de calcul Excel XLS/XLSX à l'aide de [Editor](https://apireference.groupdocs.com/editor/java/com.groupdocs.editor/Editor).
* Définissez l'index de l'onglet de la feuille de calcul et récupérez le [document modifiable](https://apireference.groupdocs.com/editor/java/com.groupdocs.editor/EditableDocument) à l'aide de [edit()](https://apireference.groupdocs.com/editor/java/com.groupdocs.editor/Editor#edit()).
* Vous pouvez obtenir le contenu de l'onglet de feuille de calcul chargé en utilisant la méthode getter respective.
* Modifier le contenu par programme ou en utilisant n'importe quel éditeur WYSIWYG.
* Convertissez le contenu modifié en un document modifiable.
* Enregistrez la feuille de calcul mise à jour avec [save()](https://apireference.groupdocs.com/editor/java/com.groupdocs.editor/Editor#save(com.groupdocs.editor.EditableDocument,%20java.lang.String,%20com.groupdocs.editor.options.ISaveOptions)) à l'aide des options d'enregistrement pertinentes.

Le code Java suivant vous permet de modifier la feuille de calcul Excel dans l'application.

```
// Modifier les documents Excel XLS/XLSX en Java
SpreadsheetLoadOptions loadOptions = new SpreadsheetLoadOptions();
loadOptions.setPassword("password-if-any");

// Chargement de la feuille de calcul
Editor editor = new Editor("path/sample_sheet.xlsx", loadOptions);

// Modifier le 1er onglet de la feuille de calcul
SpreadsheetEditOptions editOptions = new SpreadsheetEditOptions();
editOptions.setWorksheetIndex(0); // index is 0-based, so this is 1st tab
EditableDocument firstTab = editor.edit(editOptions);

String bodyContent = firstTab.getBodyContent();
String allContent = firstTab.getContent();
List<IImageResource> onlyImages = firstTab.getImages();
List<IHtmlResource> allResourcesTogether = firstTab.getAllResources();

String editedSheetContent = allContent.replace("Old Company Name","New Company Name");
EditableDocument editedDoc = EditableDocument.fromMarkup(editedSheetContent, null);

SpreadsheetSaveOptions saveOptions = new SpreadsheetSaveOptions(SpreadsheetFormats.Xlsx);
saveOptions.setPassword("new-password");
editor.save(editedDoc, "path/edited_spreadsheet.xlsx", saveOptions);

firstTab.dispose();
editor.dispose();
```

**Charger :** Vous pouvez appliquer des options supplémentaires lors du chargement de la feuille de calcul ; comme fournir le mot de passe si le document est protégé.

**Modifier :** Après le chargement, vous pouvez modifier la feuille de calcul chargée. L'exemple ci-dessus remplace toutes les occurrences de "Ancien nom de société" par "Nouveau nom de société" dans le premier onglet de la feuille de calcul XLSX.

**Enregistrer :** Lors de l'enregistrement de la feuille de calcul modifiée, vous pouvez définir diverses options telles que la protection par mot de passe, le format de fichier, etc.

## Conclusion

Pour conclure, nous avons appris à éditer des feuilles de calcul Excel en Java à l'aide de l'API Java d'édition de documents et de feuilles de calcul. Vous pouvez utiliser l'API avec les éditeurs WYSIWYG pour modifier visuellement les feuilles de calcul. Vous pouvez créer votre propre application Java d'édition de feuilles de calcul. Pour plus de détails, d'options et d'exemples, vous pouvez consulter la [documentation](https://docs.groupdocs.com/editor/java/) et le [GitHub](https://github.com/groupdocs-editor) dépôt. Pour toute autre question, contactez le support sur le [forum](https://forum.groupdocs.com/c/assembly).

## Voir également

* [Feuilles Excel en filigrane en Java](https://blog.groupdocs.com/2021/11/10/watermark-excel-sheets-in-java/)
* [Convertir des feuilles de calcul Excel en PDF en Java](https://blog.groupdocs.com/2021/11/21/convert-excel-spreadsheets-to-pdf-in-java/)
* [Convertir Excel (XLS XLSX) en CSV et vice versa en Java](https://blog.groupdocs.com/2021/07/31/convert-csv-and-excel-xls-xlsx-in-java/)
* [Insérer des objets OLE dans Word, Excel, PowerPoint en utilisant Java](https://blog.groupdocs.com/2020/10/19/insert-ole-objects-in-word-excel-powerpoint-with-java/)
* [Modifier des documents Word en Java](https://blog.groupdocs.com/2022/03/30/edit-word-documents-in-java/)





