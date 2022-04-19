---
title: "Afficher les documents Word en tant que page HTML réactive à l'aide de Java"
date: Thu, 23 Sep 2021 10:31:47 +0000
draft: false
url: /fr/2021/09/23/view-word-documents-as-responsive-html-page-using-java/
author: 'Shoaib Khan'
summary: 'Responsive HTML web pages are the ones that look good on different devices by adjusting themselves according to the different screen sizes. This article will guide you about **how to programmatically convert word documents as responsive HTML pages** within the **Java** applications using GroupDocs.Viewer.

Les sujets suivants seront abordés dans cet article :

* API Java pour Word et lecteur HTML réactif
* Afficher les documents Word en tant que HTML réactif en Java'
tags: ['convert docx to html', 'Convert Word to HTML', 'Convert Word to Responsive HTML', 'view word as html responsive', 'Word to HTML in Java']
categories: ['GroupDocs.Viewer Product Family']
---

Les pages Web HTML réactives sont celles qui s'affichent bien sur différents appareils en s'adaptant aux différentes tailles d'écran. Cet article vous expliquera **comment convertir par programmation des documents Word en pages HTML réactives** dans les applications **Java** à l'aide de [GroupDocs.Viewer][1].



{{< figure align=center src="images/word-to-responsive-html-layout-using-java-1024x614.jpg" alt="Mise en page Word en HTML réactif à l'aide de Java">}}


Les sujets suivants seront abordés ci-dessous :

* [API Java pour Word et lecteur HTML réactif][2]
* [Afficher les documents Word en HTML réactif en Java][3]

## API Java - Convertir et afficher des documents Word en HTML réactif {#responsive-html-view-java-api}

GroupDocs.Viewer fournit l'API Java pour restituer les documents Word sous forme de pages HTML réactives dans les applications Java. Cette API Java permet de rendre, d'afficher et de manipuler un [grand nombre de formats de documents différents][4]. Il permet en outre de créer une ** visionneuse HTML ** avec des ressources externes et intégrées, une ** visionneuse d'images ** en rendant au format JPG et PNG, ainsi que la ** visionneuse PDF ** qui pourrait être la meilleure pour l'impression ou le partage avec autres.

### Télécharger ou configurer

Vous pouvez télécharger le fichier **JAR** à partir de la [section des téléchargements][5], ou simplement obtenir les dernières configurations de référentiel et de dépendance pour le pox.xml de vos applications Java **basées sur maven**.

```
<repository>
	<id>GroupDocsArtifactRepository</id>
	<name>GroupDocs Artifact Repository</name>
	<url>https://repository.groupdocs.com/repo/</url>
</repository>
```
```
<dependency>
        <groupId>com.groupdocs</groupId>
        <artifactId>groupdocs-viewer</artifactId>
        <version>21.4</version> 
</dependency>
```

## Convertir des documents Word en HTML réactif à l'aide de Java {#word-to-html-responsive}

Vous pouvez rendre vos documents MS Word DOC, DOCX, sur des pages HTML réactives pour bien paraître sur toutes les différentes tailles d'écran. Les étapes suivantes montrent comment convertir un document Word (DOC/DOCX) en HTML réactif en Java.

* Charger le document Word (DOC/DOCX) en utilisant la classe [Viewer][6].
* Définissez les ressources intégrées ou externes pour la sortie html à l'aide de [HtmlViewOptions][7].
* Activez le rendu réactif à l'aide de la méthode [setRenderResponsive][8].
* Pour générer les pages Web réactives du document Word chargé, utilisez la méthode [view][9] de la classe Viewer

Le code source suivant rend le document Word au format HTML réactif avec des ressources intégrées en Java.

```
// Convertir des documents Word DOC/DOCX en HTML Responsive Page en Java
try (Viewer viewer = new Viewer("path/document.docx")) {
    HtmlViewOptions viewOptions = HtmlViewOptions.forEmbeddedResources("path/page_{0}.html");
    viewOptions.setRenderResponsive(true);
    viewer.view(viewOptions);
}
```

## Obtenez une licence API gratuite

Vous pouvez [obtenir une licence temporaire gratuite][10] pour utiliser l'API sans les limitations d'évaluation.

## Conclusion

Pour conclure, vous avez expliqué comment rendre les documents Word sous forme de pages HTML réactives dans les applications Java à l'aide de GroupDocs.Viewer pour l'API Java. De plus, vous pouvez générer ces pages HTML avec des ressources intégrées ou externes. Vous devez penser à commencer à créer votre propre application de visualisation de documents en Java comme celle déjà [construite par GroupDocs][11].

Pour en savoir plus sur l'API, vous pouvez consulter la [documentation][12] et le référentiel [GitHub][13]. En cas de questions supplémentaires et d'ambiguïtés, contactez le support gratuit sur le [forum][14].

## Voir également

* [Afficher les documents CAO à l'aide de Java][15]
* [Rendre les documents Word en HTML minifié en Java][16]
* [Réorganiser les pages dans les documents Word à l'aide de Java][17]
* [Afficher les documents Word en tant que page HTML réactive à l'aide de C #][18]







[1]: https://products.groupdocs.com/viewer/
[2]: #responsive-html-view-java-api
[3]: #word-to-html-responsive
[4]: https://docs.groupdocs.com/viewer/java/supported-document-formats/
[5]: https://downloads.groupdocs.com/viewer
[6]: https://apireference.groupdocs.com/viewer/java/com.groupdocs.viewer/Viewer
[7]: https://apireference.groupdocs.com/viewer/java/com.groupdocs.viewer.options/HtmlViewOptions
[8]: https://apireference.groupdocs.com/viewer/java/com.groupdocs.viewer.options/HtmlViewOptions#setRenderResponsive(boolean)
[9]: https://apireference.groupdocs.com/viewer/java/com.groupdocs.viewer/Viewer#view(com.groupdocs.viewer.options.ViewOptions)
[10]: https://purchase.groupdocs.com/temporary-license
[11]: https://products.groupdocs.app/viewer/total
[12]: https://docs.groupdocs.com/viewer/java/
[13]: https://github.com/groupdocs-viewer
[14]: https://forum.groupdocs.com/c/assembly
[15]: https://blog.groupdocs.com/2021/04/05/viewing-cad-documents-using-java/
[16]: https://blog.groupdocs.com/2022/03/04/render-word-documents-as-minified-html-in-java/
[17]: https://blog.groupdocs.com/2022/03/01/move-word-pages-using-java/
[18]: https://blog.groupdocs.com/2021/08/28/view-word-documents-as-html-responsive-page-using-csharp/


