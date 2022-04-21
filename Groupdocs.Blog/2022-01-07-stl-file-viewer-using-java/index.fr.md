---
title: "'Visionneuse de fichiers STL utilisant Java'"
date: Fri, 07 Jan 2022 10:49:14 +0000
draft: false
url: /fr/2022/01/07/stl-file-viewer-using-java/
author: 'Shoaib Khan'
summary: "Le format de fichier STL (**ST**ereo**L**ithography) est largement utilisé pour les dessins et l'impression CAO 3D. D'autre part, il existe de nombreux autres formats plus portables que STL. Voici l'exigence de rendre le format STL dans d'autres formats. Dans cet article, nous discuterons de **comment rendre les fichiers STL au format PDF en utilisant Java**. En plus de cela, nous convertirons les **fichiers STL aux formats HTML, JPG et PNG** dans l'application Java à l'aide d'exemples.

Les sujets suivants sont abordés dans cet article :

* API Java de la visionneuse STL
* Voir STL au format PDF
* Afficher STL au format HTML, JPG, PNG"
tags: ['STL as HTML', 'STL as JPG', 'STL as PNG', 'STL Viewer', 'STL Viewer using Java', 'View STL', 'View STL as PDF']
categories: ['GroupDocs.Viewer Product Family']
---

Le format de fichier STL (**ST**ereo**L**ithography) est largement utilisé pour les dessins et l'impression CAO 3D. D'autre part, de nombreux autres formats sont plus portables que STL. Voici l'exigence de rendre le format STL dans d'autres formats. Dans cet article, nous discuterons de **comment rendre les fichiers STL au format PDF en utilisant Java**. En plus de cela, nous convertirons les **fichiers STL aux formats HTML, JPG et PNG** dans l'application Java à l'aide d'exemples.

Les sujets suivants sont abordés ci-dessous :

* [API Java de la visionneuse STL](#stl-viewer-java-api)
* [Voir STL en PDF](#stl-to-pdf)
* [Afficher STL au format HTML, JPG, PNG](#convert-stl-using-csharp)

## API Java pour afficher les fichiers STL {#stl-viewer-java-api}

[GroupDocs.Viewer](https://products.groupdocs.com/viewer/) présente [l'API Java de la visionneuse de documents](https://products.groupdocs.com/viewer/net/) qui permet de rendre les documents au format PDF, HTML et images dans l'application Java. Dans cet article, nous utiliserons cette API dans des exemples pour convertir les fichiers STL en différents autres formats de fichiers.

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

## Afficher le fichier STL au format PDF à l'aide de Java {#stl-to-pdf}

La grande portabilité du format PDF conduit souvent à la conversion d'autres formats en PDF. Les étapes suivantes expliquent comment convertir les fichiers STL au format PDF en Java.

* Chargez le fichier STL à l'aide de la classe [Viewer](https://apireference.groupdocs.com/viewer/java/com.groupdocs.viewer/Viewer).
* Préparez les options de rendu PDF à l'aide de la classe [PdfViewOptions](https://apireference.groupdocs.com/viewer/java/com.groupdocs.viewer.options/PdfViewOptions).
* Rendez le fichier STL au format PDF à l'aide de [view()](https://apireference.groupdocs.com/viewer/java/com.groupdocs.viewer/Viewer#view(com.groupdocs.viewer.options.ViewOptions)) méthode.

L'exemple de code Java suivant rend les fichiers STL au format PDF.

```
// Rendu des fichiers STL au format PDF en Java
try (Viewer viewer = new Viewer("path/input.stl")) {
    PdfViewOptions options = new PdfViewOptions("path/stl-output.pdf");
    viewer.view(options);
}
```

## Afficher le fichier STL au format HTML, JPG ou PNG à l'aide de Java {#convert-stl-using-csharp}

De la même manière, vous pouvez également convertir les fichiers STL dans divers autres formats. Les étapes suivantes vous aident à rendre les fichiers STL aux formats HTML, JPG et PNG à l'aide de Java.

* Chargez le fichier **STL** à l'aide de la classe [Viewer](https://apireference.groupdocs.com/viewer/java/com.groupdocs.viewer/Viewer).
* Préparez les options de rendu en fonction du format de sortie prévu:
    * Le rendu **HTML** nécessite [](https://apireference.groupdocs.com/viewer/net/groupdocs.viewer.options/pdfviewoptions)[HtmlViewOptions](https://apireference.groupdocs.com/viewer/java/com.groupdocs.viewer.options/HtmlViewOptions). (Vous pouvez utiliser des ressources intégrées ou externes)
    * Le rendu **JPG** utilise la classe [JpgViewOptions](https://apireference.groupdocs.com/viewer/java/com.groupdocs.viewer.options/JpgViewOptions).
    * Le rendu **PNG** nécessite la classe [PngViewOptions](https://apireference.groupdocs.com/viewer/java/com.groupdocs.viewer.options/PngViewOptions).
* Rendez le fichier STL au format HTML, JPG ou PNG à l'aide de [view()](https://apireference.groupdocs.com/viewer/java/com.groupdocs.viewer/Viewer#view(com.groupdocs.viewer.options.ViewOptions)).

Vous trouverez ci-dessous les exemples de code source Java qui rendent indépendamment les fichiers STL dans chaque format en utilisant les options de format respectives mentionnées ci-dessus.

### STL vers HTML en utilisant Java {#stl-to-html}

Le code Java suivant convertit le fichier STL au format HTML avec des ressources intégrées. De même, vous pouvez convertir en HTML avec des ressources externes.

```
// Rendu des fichiers STL au format HTML avec des ressources intégrées à l'aide de Java
try (Viewer viewer = new Viewer("path/input.stl")) {
    HtmlViewOptions options = HtmlViewOptions.forEmbeddedResources("path/stl-output.html");
    viewer.view(options);
}
```

### STL en JPG en utilisant Java {#stl-to-jpg}

Le code Java suivant rend le fichier STL au format d'image JPG.

```
// Rendu des fichiers STL au format JPG en Java
try (Viewer viewer = new Viewer("path/input.stl")) {
    JpgViewOptions options = new JpgViewOptions("path/stl-output.jpg");
    viewer.view(options);
}
```

### STL en PNG en utilisant Java {#stl-to-png}

Le code Java suivant convertit le fichier STL au format d'image PNG.

```
// Rendu des fichiers STL au format PNG en Java
try (Viewer viewer = new Viewer("path/input.stl")) {
    PngViewOptions options = new PngViewOptions("path/stl-output.png");
    viewer.view(options);
}
```

## Obtenez une licence API gratuite

Vous pouvez utiliser les API gratuitement en [obtenant une licence temporaire](https://purchase.groupdocs.com/temporary-license).

## Conclusion

Pour résumer, nous avons appris à rendre les fichiers STL aux formats PDF, HTML, JPG et PNG à l'aide des exemples Java. Maintenant, vous pouvez essayer de développer votre propre application de visualisation STL comme [l'application en ligne de Groupdocs.Viewer](https://products.groupdocs.app/viewer).

Pour en savoir plus sur [GroupDocs.Viewer for Java](https://products.groupdocs.com/viewer/java/), consultez sa [documentation](https://docs.groupdocs.com/viewer/). Pour toute question, contactez-nous via le [forum](https://forum.groupdocs.com/).

## Voir également

* [Fichiers de code source en PDF en Java](https://blog.groupdocs.com/2021/12/16/convert-source-code-to-pdf-in-java/)
* [Afficher les fichiers CAO à l'aide de Java](https://blog.groupdocs.com/2021/04/05/viewing-cad-documents-using-java/)
* [Documents Word en tant que page HTML réactive utilisant Java](https://blog.groupdocs.com/2021/09/23/view-word-documents-as-responsive-html-page-using-java/)





