---
title: "Rendre les documents Word en HTML minifié en Java"
date: Fri, 04 Mar 2022 12:12:56 +0000
draft: false
url: /fr/2022/03/04/render-word-documents-as-minified-html-in-java/
author: 'Shoaib Khan'
summary: "La minification HTML améliore les performances des applications Web avec un temps de chargement et une utilisation de la bande passante efficaces. Les parties de code inutiles, les espaces blancs insignifiants, les commentaires, les points-virgules, les valeurs de couleur dans le HTML et le CSS sont optimisés dans le processus de minification. Laissez-nous automatiser le processus pour vous débarrasser du code indésirable et améliorer l'efficacité de vos applications Java. Afin d'améliorer les performances, cet article explique **comment rendre des documents Word en HTML minifié en Java**."
tags: ['Minify HTML', 'Minify HTML in Java', 'Word to Clean HTML', 'Word to Minified HTML']
categories: ['GroupDocs.Viewer Product Family']
---

La minification HTML améliore les performances des applications Web avec un temps de chargement et une utilisation de la bande passante efficaces. Les parties de code inutiles, les espaces blancs insignifiants, les commentaires, les points-virgules, les valeurs de couleur dans le HTML et le CSS sont optimisés dans le processus de minification. Automatisons le processus pour éliminer le code indésirable et améliorer l'efficacité de vos applications Java. Afin d'améliorer les performances, cet article explique **comment rendre des documents Word en HTML minifié en Java**.



{{< figure align=center src="images/render-word-to-clean-html-in-java.jpg" alt="Rendu des documents Word en HTML propre en Java">}}


## API Java pour le rendu en HTML minifié {#stl-viewer-dotnet-api}

[GroupDocs.Viewer](https://products.groupdocs.com/viewer/) présente une [API de visualisation de documents](https://products.groupdocs.com/viewer/java/) qui permet de rendre différents types de documents dans Formats HTML, PDF et image dans les applications Java. J'utiliserai cette API dans l'exemple pour convertir le fichier Microsoft Word DOCX en un fichier HTML propre.

Vous pouvez télécharger le fichier **JAR** à partir de la [section téléchargements](https://downloads.groupdocs.com/viewer/java) ou utiliser le dernier référentiel et dépendance [Maven](https://repository.groupdocs.com/webapp/#/artifacts/browse/tree/General/repo/com/groupdocs) configurations dans vos applications Java.

```
<repository>
	<id>GroupDocsArtifactRepository</id>
	<name>GroupDocs Artifact Repository</name>
	<url>https://repository.groupdocs.com/repo/</url>
</repository>

<dependency>
        <groupId>com.groupdocs</groupId>
        <artifactId>groupdocs-viewer</artifactId>
        <version>21.11.1</version> 
</dependency>
```

## Rendre Word DOC/DOCX en HTML minifié en Java {#stl-to-pdf}

Les fichiers HTML peuvent être générés avec des ressources intégrées ou externes en utilisant les méthodes respectives. Les étapes suivantes montrent comment rendre le document Word (DOC/DOCX) en HTML minifié en Java.

* Chargez le fichier DOCX à l'aide de la classe [Viewer](https://apireference.groupdocs.com/viewer/java/com.groupdocs.viewer/Viewer).
* Préparez les options de rendu HTML à l'aide de la classe [HtmlViewOptions](https://apireference.groupdocs.com/viewer/java/com.groupdocs.viewer.options/HtmlViewOptions).
* Activez l'option de minification en la définissant sur true.
* Utilisez **view()** avec les options créées pour rendre le fichier DOCX en HTML minifié.

L'exemple de code Java suivant rend le fichier Word DOCX en HTML minifié.

```
// Convertir Word DOC/DOCX en HTML minifié en Java
Viewer viewer = new Viewer("path/document.docx");

HtmlViewOptions viewOptions = HtmlViewOptions.forEmbeddedResources("path/page_{0}.html");
viewOptions.setMinify(true);

viewer.view(viewOptions);
```

## Obtenez une licence API gratuite

Vous pouvez utiliser les API gratuitement sans limitation d'évaluation en [obtenant une licence temporaire](https://purchase.groupdocs.com/temporary-license).

## Conclusion

Pour conclure, cet article explique comment rendre les fichiers DOC/DOCX en HTML minifié en Java. Vous pouvez développer votre propre convertisseur de documents en ligne et un minificateur HTML qui permettent aux utilisateurs de convertir les documents en HTML minifié. En outre, vous pouvez en savoir plus sur [GroupDocs.Viewer pour Java](https://products.groupdocs.com/viewer/net/) à partir de sa [documentation](https://docs.groupdocs.com/viewer/). Pour toute question, contactez-nous via le [forum](https://forum.groupdocs.com/).

## Voir également

* [Visionneuse de fichiers STL utilisant Java](https://blog.groupdocs.com/2022/01/07/stl-file-viewer-using-java/)
* [Visionneuse de documents CAO utilisant Java](https://blog.groupdocs.com/2021/04/05/viewing-cad-documents-using-java/)
* [Code source en PDF en Java](https://blog.groupdocs.com/2021/12/16/convert-source-code-to-pdf-in-java/)
* [Documents Word en tant que page HTML réactive utilisant Java](https://blog.groupdocs.com/2021/09/23/view-word-documents-as-responsive-html-page-using-java/)





