---
title: "Modifier des fichiers XML en Java"
date: Sat, 06 Nov 2021 10:28:27 +0000
draft: false
url: /fr/2021/11/06/edit-xml-files-in-java/
author: 'Shoaib Khan'
summary: "XML est couramment utilisé pour stocker et transmettre des données dans et entre les applications. C'est souvent une exigence où les développeurs doivent modifier le fichier XML lors de sa réception ou avant sa transmission. Dans cet article, nous expliquerons **comment modifier les données du fichier XML en Java**."
tags: ['Edit XML File in Java', 'Edit XML in Java', 'How to', 'Update XML data in Java']
categories: ['GroupDocs.Editor Product Family']
---

XML est couramment utilisé pour stocker et transmettre des données dans et entre les applications. C'est souvent une exigence où les développeurs doivent modifier le fichier XML lors de sa réception ou avant sa transmission. Dans cet article, nous expliquerons **comment modifier les données du fichier XML en Java**.

* [API Java d'édition XML][1]
* [Comment modifier des fichiers XML][2]

## API Java pour éditer des fichiers XML {#xml-edit-java-api}

GroupDocs.Editor pour l'API Java vous permet de modifier des documents de différents formats de fichiers. Dans cet article, nous l'utiliserons pour éditer des fichiers XML. Vous pouvez utiliser l'API avec les éditeurs externes pour l'édition visuelle.

Téléchargez le fichier **JAR** à partir de la [section téléchargements][3], ou utilisez simplement les dernières configurations de référentiel et de dépendance [Maven][4] dans vos applications Java.

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

## Comment éditer des fichiers XML en Java {#how-to-edit-xml}

Allons droit au but et modifions les données XML en remplaçant une valeur par une autre. Voici les étapes pour modifier ou mettre à jour le fichier XML en Java.

* Chargez le fichier de données XML dans l'objet de classe [Editor][5].
* Préparez les options d'édition pour le XML en utilisant la classe [XmlEditOptions][6].
* Créez le [EditableDocument][7] comme contenu source en utilisant la méthode [edit][8] et les options d'édition préparées.
* Utilisez la méthode [getContent][9] du **EditableDocument** pour extraire le contenu original du fichier XML.
* Modifiez maintenant tout ce qui est requis dans le contenu XML.
* Créez maintenant un nouveau **EditableDocument** à partir du contenu XML mis à jour à l'aide de la méthode [fromMarkup][10].
* Utilisez les options d'enregistrement pertinentes telles que [WordProcessingSaveOptions][11] ou [TextSaveOptions][12] pour enregistrer le contenu mis à jour dans différents formats.
* Enregistrez le XML mis à jour dans n'importe quel format à l'aide de la méthode [save][13].

L'extrait de code suivant montre comment modifier un fichier XML en Java et mettre à jour les données pour les enregistrer dans d'autres formats.

```
// Modifier le fichier XML en mettant à jour les valeurs à l'aide de Java
Editor editor = new Editor("path/XMLData.xml");

// Créer des options d'édition XML
XmlEditOptions editOptions = new XmlEditOptions();
editOptions.setAttributeValuesQuoteType(QuoteType.DoubleQuote);
editOptions.setRecognizeEmails(true);
editOptions.setRecognizeUris(true);
editOptions.setTrimTrailingWhitespaces(true);

// Préparer et modifier le document modifiable
EditableDocument beforeEdit = editor.edit(editOptions);

// Modifier XML
String originalTextContent = beforeEdit.getContent();
String updatedTextContent = originalTextContent.replace("John", "Samuel");

List<IHtmlResource> allResources = beforeEdit.getAllResources();

// Créer un nouveau document modifiable avec un contenu mis à jour
EditableDocument afterEdit = EditableDocument.fromMarkup(updatedTextContent, allResources);

// Créer des options d'enregistrement de traitement de texte
WordProcessingSaveOptions wordSaveOptions = new WordProcessingSaveOptions(WordProcessingFormats.Docx);

// Créer des options de sauvegarde TXT
TextSaveOptions txtSaveOptions = new TextSaveOptions();
txtSaveOptions.setEncoding(StandardCharsets.UTF_8);

// Enregistrer les données XML modifiées au format DOCX et TXT
editor.save(afterEdit, "path/updated-xml-data.docx", wordSaveOptions);
editor.save(afterEdit, "path/updated-xml-data.txt", txtSaveOptions);
```

## Obtenez une licence gratuite

Vous pouvez [obtenir une licence temporaire gratuite][14] afin d'utiliser l'API sans les limitations d'évaluation.

## Conclusion

Pour conclure, nous avons appris aujourd'hui à éditer par programmation les données d'un fichier XML en Java. Vous pouvez maintenant développer votre [application d'édition XML en ligne][15]. Pour explorer davantage les fonctionnalités de GroupDocs.Editor, consultez la [documentation][16]. Pour toute question, contactez-nous via le [forum][17].

## Voir également

* [Comment modifier des fichiers XML à l'aide de C #][18]
* [Comment modifier des documents Word en C #][19]







[1]: #xml-edit-java-api
[2]: #how-to-edit-xml
[3]: https://downloads.groupdocs.com/editor
[4]: https://repository.groupdocs.com/webapp/#/artifacts/browse/tree/General/repo/com/groupdocs/groupdocs-editor
[5]: https://apireference.groupdocs.com/editor/java/com.groupdocs.editor/Editor
[6]: https://apireference.groupdocs.com/editor/java/com.groupdocs.editor.options/XmlEditOptions
[7]: https://apireference.groupdocs.com/editor/java/com.groupdocs.editor/EditableDocument
[8]: https://apireference.groupdocs.com/editor/java/com.groupdocs.editor/Editor#edit()
[9]: https://apireference.groupdocs.com/editor/java/com.groupdocs.editor/EditableDocument#getContent()
[10]: https://apireference.groupdocs.com/editor/java/com.groupdocs.editor/EditableDocument#fromMarkup(java.lang.String,%20java.util.List)
[11]: https://apireference.groupdocs.com/editor/java/com.groupdocs.editor.options/WordProcessingSaveOptions
[12]: https://apireference.groupdocs.com/editor/java/com.groupdocs.editor.options/TextSaveOptions
[13]: https://apireference.groupdocs.com/editor/java/com.groupdocs.editor/Editor#save(com.groupdocs.editor.EditableDocument,%20java.lang.String,%20com.groupdocs.editor.options.ISaveOptions)
[14]: https://purchase.groupdocs.com/temporary-license
[15]: https://products.groupdocs.app/editor/xml
[16]: https://docs.groupdocs.com/editor/java/
[17]: https://forum.groupdocs.com/
[18]: https://blog.groupdocs.com/2021/11/02/edit-xml-files-using-csharp/
[19]: https://blog.groupdocs.com/2021/03/26/edit-word-documents-in-csharp/


