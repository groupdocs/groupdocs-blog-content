---
title: "Afficher des documents CAO à l'aide de Java"
date: Mon, 05 Apr 2021 20:34:00 +0000
draft: false
url: /fr/2021/04/05/visualisation-des-documents-cad-en-java/
aliases:
- /2019/07/13/visualisation-des-documents-cad/
author: 'Shoaib Khan'
summary: "**C**computer-**A**ided **D**esign - Les fichiers **CAO** sont normalement utilisés pour les conceptions 2D et 3D. Ces conceptions sont générées par des logiciels de CAO et sont normalement utilisées pour créer des modèles et des plans architecturaux. Si vous avez travaillé avec la CAO, vous connaissez probablement certains des formats de fichier d'AutoCAD, tels que **DWG, DXF, DGN, DWF**. Cet article explique comment afficher par programme les fichiers CAO dans les applications Java."
tags: ['CAD Viewer in Java', 'Convert DWG to HTML in Java', 'Convert DWG to JPG in Java', 'convert dwg to pdf in java', 'Convert DWG to PNG in Java', 'DWG Viewer using Java']
categories: ['GroupDocs.Viewer Product Family']
---

**C**computer-**A**ided **D**esign - Les fichiers **CAO** sont normalement utilisés pour les conceptions 2D et 3D. Ces conceptions sont générées par des logiciels de CAO et sont normalement utilisées pour créer des modèles et des plans architecturaux. Si vous avez travaillé avec la CAO, vous connaissez probablement certains des formats de fichier d'AutoCAD, tels que **DWG, DXF, DGN, DWF**. Cet article explique comment afficher par programme les fichiers CAO dans les applications Java.

Les sujets suivants sont brièvement abordés ci-dessous :

* [API Java pour rendre les fichiers CAO.][2]
* [Convertir les fichiers CAO pour les rendre au format HTML, JPG, PNG ou PDF en Java.][3]
* [Obtenez des mises en page et des couches de DWG en Java.][4]
* [Rendre les couches CAO du dessin DWG en Java.][5]
* [Rendre les mises en page CAO du dessin DWG en Java.][6]

## API Java pour le rendu des fichiers CAO - DWG, DXF, DWF, DGN {#java-api-to-render-cad-files}

[GroupDocs.Viewer for Java][7] est l'API qui permet de rendre divers documents et fichiers image au format HTML, Image ou PDF pour afficher ces fichiers dans votre application Java. L'API prend en charge [plus de 100 formats de fichiers à restituer par programmation au format HTML, JPG, PNG ou PDF][8].

Dans cet article, nous nous en tiendrons aux fichiers CAO. Outre les formats **DWG** et **DGN** déjà mentionnés, vous pouvez également afficher les formats AutoCAD tels que **DWF, DWT, DXF, ainsi que IFC, STL, IGS, CF2, Plotter document (PLT, HPG)** dans vos applications Java.

### Télécharger et configurer

[Obtenez la bibliothèque][9] à partir des téléchargements ou ajoutez simplement la configuration pom.xml suivante dans vos applications Java basées sur Maven pour essayer les exemples mentionnés ci-dessous. Pour plus de détails, vous pouvez visiter la [API Reference][10].

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
        <version>21.2</version> 
</dependency>
```

## Convertir des dessins CAO pour les rendre au format HTML, PNG, JPG ou PDF en Java {#convert-cad-to-html-jpg-jpg-pdf-in-java}

L'API permet de rendre les documents CAO aux formats HTML, JPG, PNG et PDF. Dans cet article, je m'en tiens au format DWG pour la conversion et le rendu vers d'autres formats à l'aide d'exemples. Pour commencer, convertissons la conception DWG et rendons-la au format HTML avec des options de ressources intégrées et externes.

### Convertir DWG en HTML avec les ressources intégrées

Voici les étapes de conversion du fichier DWG pour le rendre au format HTML.

* Initialisez l'objet de classe [Viewer][11] à l'aide du fichier source .dwg.
* Créez [HtmlViewOptions][12] en utilisant la méthode _[forEmbeddedResources][13]_.
* Rendez .dwg en HTML en utilisant la méthode _[view][14]_.

Le code source suivant convertit le fichier DWG et le restitue au format HTML avec des ressources intégrées en Java.

```
// Rendre le dessin CAO .dwg pour l'afficher au format HTML avec des ressources intégrées à l'aide de Java
try (Viewer viewer = new Viewer("drawing.dwg")) {
	HtmlViewOptions viewOptions = HtmlViewOptions.forEmbeddedResources("page_{0}.html");
	viewer.view(viewOptions);
}
```

### Convertir DWG en HTML avec des ressources externes

Voici les étapes de conversion du fichier DWG pour le rendre sous forme de fichier(s) HTML et avec des ressources externes.

* Initialisez l'objet de classe [Viewer][15] à l'aide du fichier source .dwg.
* Créez [HtmlViewOptions][16] en utilisant la méthode [_forExternalResources_][17].
* Rendez .dwg en HTML en utilisant la méthode _[view][18]_.

Le code source suivant rend le fichier DWG au format HTML avec des ressources externes en Java.

```
// Rendre le dessin CAO .dwg pour l'afficher au format HTML avec des ressources externes à l'aide de Java
try (Viewer viewer = new Viewer("drawing.dwg")) {
	HtmlViewOptions viewOptions = HtmlViewOptions.forExternalResources("page_{0}.html", "page_{0}/resource_{1}", "page_{0}/resources");
	viewer.view(viewOptions);
}
```

### Convertir DWG en PDF, JPG et PNG en Java

Semblable à la conversion au format HTML, les fichiers DWG peuvent être rendus au format PDF, JPG et PNG à l'aide des options d'affichage respectives comme suit :

* [HtmlViewOptions][19] pour afficher en HTML
* [JpgViewOptions][20] pour rendre au format JPG
* [PngViewOptions][21] pour rendre en PNG
* [PdfViewOptions][22] pour rendre au format PDF

## Obtenir des mises en page et des calques de DWG en Java {#get-layout-and-layers-of-dwg-in-java}

Comme les fichiers CAO peuvent être constitués de plusieurs mises en page et couches, vous pouvez facilement obtenir leurs mises en page et couches en suivant les étapes suivantes.

* Instanciez l'objet [ViewInfoOptions][23] pour le rendu HTML.
* En utilisant ViewInfoOptions, vous pouvez obtenir le [CadViewInfo][24].
* Obtenez les mises en page à partir de viewInfo en utilisant la méthode _[getLayouts][25]_.
* Obtenez les calques de viewInfo en utilisant la méthode _[getLayers][26]_.

Le code suivant montre comment obtenir toutes les présentations et tous les calques du fichier DWG à l'aide de Java.

```
// Obtenir des mises en page et des calques de dessin CAO DWG en Java
try (Viewer viewer = new Viewer("drawing.dwg")) {
	ViewInfoOptions viewInfoOptions = ViewInfoOptions.forHtmlView();
	CadViewInfo viewInfo = (CadViewInfo) viewer.getViewInfo(viewInfoOptions);
    
	System.out.println("File type: " + viewInfo.getFileType());
	System.out.println("Pages count: " + viewInfo.getPages().size());
    
	for (Layout layout : viewInfo.getLayouts()) {
		System.out.println(layout);
	}
	for (Layer layer : viewInfo.getLayers()) {
		System.out.println(layer);
	}
}
```

## Rendre les couches CAO du fichier DWG en Java {#render-layers-of-dwg-in-java}

Par défaut, toutes les couches du dessin CAO sont rendues comme indiqué ci-dessus. Cependant, vous pouvez rendre n'importe quelle couche spécifique de DWG en sélectionnant celles choisies à l'aide de la méthode [_setLayers_][27] de l'API Java, comme indiqué ci-dessous.

* Initialisez l'objet de classe [Viewer][28] à l'aide du fichier source .dwg.
* Instanciez [HtmlViewOptions][29].
* Ajoutez la ou les couches à rendre à l'aide de la méthode _[setLayers][30]_ de CadOptions.
* Rendez .dwg en HTML en utilisant la méthode _[view][31]_.

Le code suivant rend les calques d'un fichier CAO au format DWG en Java.

```
// Rendu des couches de dessin CAO .dwg en Java
try (Viewer viewer = new Viewer("drawing.dwg")) {
	HtmlViewOptions viewOptions = HtmlViewOptions.forEmbeddedResources();
	viewOptions.getCadOptions().setLayers(Arrays.asList(new Layer("Stairs"), new Layer("Walls")));
	viewer.view(viewOptions);
}
```

## Rendre les mises en page CAO du fichier DWG en Java {#render-layouts-of-dwg-in-java}

Lorsque nous rendons le dessin CAO, nous n'obtenons que la présentation du modèle par défaut. Pour rendre le modèle ainsi que toutes les mises en page non vides, il suffit de définir la propriété **RenderLayout** de CadOptions sur true.

* Initialisez l'objet de classe [Viewer][32] à l'aide du fichier source .dwg.
* Instanciez [HtmlViewOptions][33].
* Définissez la propriété [RenderLayout][34] de CadOptions sur true.
* Rendu .dwg au format HTML en utilisant la méthode _[view][35]_.

Le code suivant restitue toutes les mises en page non vides avec le modèle d'un dessin CAO au format DWG en Java.

```
// Dispositions de rendu du dessin CAO .dwg en Java
try (Viewer viewer = new Viewer("drawing.dwg")) {
	HtmlViewOptions viewOptions = HtmlViewOptions.forEmbeddedResources();
	viewOptions.getCadOptions().setRenderLayouts(true);
	viewer.view(viewOptions);
}
```

## Obtenez une licence API gratuite {#Get-a-Free-API-License}

Vous pouvez [obtenir une licence temporaire gratuite][36] afin d'utiliser l'API sans limitation d'évaluation.

## Conclusion

Dans cet article, vous avez appris à afficher des fichiers CAO dans des applications Java. J'espère que vous serez confiant pour créer votre propre visionneuse CAO en utilisant Java. Vous pouvez également afficher des modèles, des mises en page et des couches de fichiers CAO dans l'application. Vous pouvez en savoir plus sur GroupDocs.Viewer pour Java en utilisant la [documentation][37]. Si vous avez des questions, n'hésitez pas à nous le faire savoir via notre [forum][38].

## Voir également

* [Afficher les documents CAO à l'aide de C #][39]
* [Convertir des dessins CAO en PDF en Java][40]
* [Rendre les documents Word en HTML minifié en Java][41]







[1]: https://blog.groupdocs.com/2021/04/05/viewing-cad-documents-using-java/
[2]: #java-api-to-render-cad-files
[3]: #convert-cad-to-html-jpg-jpg-pdf-in-java
[4]: #get-layout-and-layers-of-dwg-in-java
[5]: #render-layers-of-dwg-in-java
[6]: #render-layouts-of-dwg-in-java
[7]: https://products.groupdocs.com/viewer/java
[8]: https://docs.groupdocs.com/viewer/java/supported-document-formats/
[9]: https://downloads.groupdocs.com/viewer/java
[10]: https://apireference.groupdocs.com/viewer/java
[11]: https://apireference.groupdocs.com/viewer/java/com.groupdocs.viewer/Viewer
[12]: https://apireference.groupdocs.com/viewer/java/com.groupdocs.viewer.options/HtmlViewOptions
[13]: https://apireference.groupdocs.com/viewer/java/com.groupdocs.viewer.options/HtmlViewOptions#forEmbeddedResources()
[14]: https://apireference.groupdocs.com/viewer/java/com.groupdocs.viewer/Viewer#view(com.groupdocs.viewer.options.ViewOptions)
[15]: https://apireference.groupdocs.com/viewer/java/com.groupdocs.viewer/Viewer
[16]: https://apireference.groupdocs.com/viewer/java/com.groupdocs.viewer.options/HtmlViewOptions
[17]: https://apireference.groupdocs.com/viewer/java/com.groupdocs.viewer.options/HtmlViewOptions#forExternalResources()
[18]: https://apireference.groupdocs.com/viewer/java/com.groupdocs.viewer/Viewer#view(com.groupdocs.viewer.options.ViewOptions)
[19]: https://apireference.groupdocs.com/viewer/java/com.groupdocs.viewer.options/HtmlViewOptions
[20]: https://apireference.groupdocs.com/viewer/java/com.groupdocs.viewer.options/JpgViewOptions
[21]: https://apireference.groupdocs.com/viewer/java/com.groupdocs.viewer.options/PngViewOptions
[22]: https://apireference.groupdocs.com/viewer/java/com.groupdocs.viewer.options/PdfViewOptions
[23]: https://apireference.groupdocs.com/viewer/java/com.groupdocs.viewer.options/ViewInfoOptions
[24]: https://apireference.groupdocs.com/viewer/java/com.groupdocs.viewer.results/CadViewInfo
[25]: https://apireference.groupdocs.com/viewer/java/com.groupdocs.viewer.results/CadViewInfo#getLayouts()
[26]: https://apireference.groupdocs.com/viewer/java/com.groupdocs.viewer.results/CadViewInfo#getLayers()
[27]: https://apireference.groupdocs.com/viewer/java/com.groupdocs.viewer.options/CadOptions#setLayers(java.util.List)
[28]: https://apireference.groupdocs.com/viewer/java/com.groupdocs.viewer/Viewer
[29]: https://apireference.groupdocs.com/viewer/java/com.groupdocs.viewer.options/HtmlViewOptions
[30]: https://apireference.groupdocs.com/viewer/java/com.groupdocs.viewer.options/CadOptions#setLayers(java.util.List)
[31]: https://apireference.groupdocs.com/viewer/java/com.groupdocs.viewer/Viewer#view(com.groupdocs.viewer.options.ViewOptions)
[32]: https://apireference.groupdocs.com/viewer/java/com.groupdocs.viewer/Viewer
[33]: https://apireference.groupdocs.com/viewer/java/com.groupdocs.viewer.options/HtmlViewOptions
[34]: https://apireference.groupdocs.com/viewer/java/com.groupdocs.viewer.options/CadOptions#setRenderLayouts(boolean)
[35]: https://apireference.groupdocs.com/viewer/java/com.groupdocs.viewer/Viewer#view(com.groupdocs.viewer.options.ViewOptions)
[36]: https://purchase.groupdocs.com/temporary-license
[37]: https://docs.groupdocs.com/viewer/java/
[38]: https://forum.groupdocs.com/
[39]: https://blog.groupdocs.com/2021/04/27/view-cad-documents-using-charp/
[40]: https://blog.groupdocs.com/2020/10/31/convert-cad-drawings-to-pdf-in-java/
[41]: https://blog.groupdocs.com/2022/03/04/render-word-documents-as-minified-html-in-java/


