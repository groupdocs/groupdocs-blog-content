---
title: "Modifier des documents Word en Java"
date: Wed, 30 Mar 2022 05:58:00 +0000
draft: false
url: /fr/2022/03/30/edit-word-documents-in-java/
author: 'Shoaib Khan'
summary: "**DOC**, **DOCX** et **ODT** sont parmi les formats de fichiers de traitement de texte les plus courants et les plus largement utilisés. Microsoft Word et OpenOffice Writer prennent en charge ces formats et sont utilisés pour la rédaction de documents. Par conséquent, en tant que développeur, nous devons souvent modifier par programmation des documents Word dans les applications. Dans cet article, nous discuterons de **comment modifier des documents Word à l'aide de l'API Java pour l'édition de documents**."
tags: ['Edit Word in Java', 'How to Edit Word in Java', 'Word Editing in Java', 'Word Editing Java API']
categories: ['GroupDocs.Editor Product Family']
---



{{< figure align=center src="images/edit-word-docs-in-java.jpg" alt="Modifier des documents Word en Java">}}


**DOC**, **DOCX** et **ODT** sont parmi les formats de fichiers de traitement de texte les plus courants et les plus largement utilisés. Microsoft Word et OpenOffice Writer prennent en charge ces formats et sont utilisés pour la rédaction de documents. Par conséquent, en tant que développeur, nous devons souvent modifier par programmation des documents Word dans les applications. Dans cet article, nous expliquerons **comment modifier des documents Word à l'aide de l'API Java pour l'édition de documents**.

Les sujets suivants sont traités dans cet article :

* [API Java - Édition de documents Word](#word-editing-java-api)
* [Modifier des documents Word en Java](#edit-word-documents-en-java)

## API Java pour l'édition et l'automatisation de documents Word {#word-editing-java-api}

[GroupDocs.Editor](https://products.groupdocs.com/editor/) fournit une API Java pour l'édition de documents et permet aux développeurs de charger, modifier et enregistrer divers formats de documents à l'aide d'éditeurs HTML WYSIWYG. Outre les formats de document de traitement de texte, l'API prend en charge l'édition de feuilles de calcul, de présentations, HTML, XML, TXT, CSV et de nombreux autres formats.

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

## Modifier des documents Word en Java {#edit-word-documents-in-java}

Après avoir configuré l'API, vous pouvez rapidement passer à l'édition du document Word. Les étapes suivantes vous permettront d'éditer les documents de traitement de texte DOC/DOCX en Java.

* Chargez le document Word à l'aide de [Editor](https://apireference.groupdocs.com/editor/java/com.groupdocs.editor/Editor).
* Récupérez le [document modifiable](https://apireference.groupdocs.com/editor/java/com.groupdocs.editor/EditableDocument) en utilisant [edit()](https://apireference.groupdocs.com/editor/java/com.groupdocs.editor/Editor#edit()).
* Obtenez le code HTML intégré du document DOC/DOCX chargé.
* Modifier le contenu par programme ou en utilisant n'importe quel éditeur WYSIWYG.
* Convertissez le contenu modifié en un document modifiable.
* Enregistrez le document mis à jour en utilisant [save()](https://apireference.groupdocs.com/editor/java/com.groupdocs.editor/Editor#save(com.groupdocs.editor.EditableDocument,%20java.lang.String,%20com.groupdocs.editor.options.ISaveOptions)).

Le code Java suivant permet d'éditer des documents Word dans l'application.

```
// Modifier les documents Word DOC/DOCX en Java
Options.WordProcessingLoadOptions loadOptions = new WordProcessingLoadOptions();
loadOptions.setPassword("password-if-any");

Editor editor = new Editor("path/document.docx", loadOptions);
EditableDocument defaultWordProcessingDoc = editor.edit();

// Soit modifier à l'aide de n'importe quel éditeur WYSIWYG, soit modifier par programmation
String allEmbeddedInsideString = defaultWordProcessingDoc.getEmbeddedHtml();
String allEmbeddedInsideStringEdited = allEmbeddedInsideString.replace("document", "edited document");

// Enregistrer le document modifié
EditableDocument editedDoc = EditableDocument.fromMarkup(allEmbeddedInsideStringEdited, null);
WordProcessingSaveOptions saveOptions = new WordProcessingSaveOptions(WordProcessingFormats.Docx);
editor.save(editedDoc, "path/edited-document.docx", saveOptions);
```

**Charger :** Vous pouvez appliquer des options supplémentaires lors du chargement du document Word ; comme fournir le mot de passe si le document est protégé.

**Modifier :** Après le chargement, vous pouvez modifier le document chargé selon vos besoins. L'exemple ci-dessus remplace toutes les occurrences du mot "document" par le "document édité" dans un document Word.

**Enregistrer :** Lors de l'enregistrement du document modifié, vous pouvez définir différentes options. Ces options incluent ; pagination, définition d'un mot de passe, paramètres d'optimisation de la mémoire, etc.

Voici la sortie du code ci-dessus.



{{< figure align=center src="images/edited-document.png" alt="document docx édité à l'aide de l'API de l'éditeur" caption="Document de sortie - Toutes les occurrences sont remplacées">}}


## Conclusion

Pour résumer, nous avons appris à éditer des documents Word en Java à l'aide de l'API Java d'édition de documents. Vous pouvez utiliser l'API avec les éditeurs WYSIWYG pour modifier visuellement vos documents. Vous pouvez créer votre propre application Java d'édition de documents. Pour plus de détails, d'options et d'exemples, vous pouvez consulter la [documentation](https://docs.groupdocs.com/editor/java/) et le [GitHub](https://github.com/groupdocs-editor) dépôt. Pour toute autre question, contactez le support sur le [forum](https://forum.groupdocs.com/c/assembly).

## Voir également

* [Annoter des fichiers Word en Java](https://blog.groupdocs.com/2022/03/19/annotate-word-documents-in-java/)
* [Comment modifier des fichiers XML en Java](https://blog.groupdocs.com/2021/11/06/edit-xml-files-in-java/)
* [Render Word documents as Minified HTML in Java](https://blog.groupdocs.com/2022/03/04/render-word-documents-as-minified-html-in-java/)





