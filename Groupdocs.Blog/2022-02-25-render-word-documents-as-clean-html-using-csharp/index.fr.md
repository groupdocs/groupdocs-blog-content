---
title: "Rendre les documents Word en HTML propre à l'aide de C#"
date: Fri, 25 Feb 2022 05:38:00 +0000
draft: false
url: /fr/2022/02/25/render-word-documents-as-clean-html-using-csharp/
author: 'Shoaib Khan'
summary: "Le nettoyage et la minification du HTML améliorent le temps de chargement et l'utilisation de la bande passante des pages Web. On observe que du code inutile est injecté lorsqu'un document est converti au format HTML à l'aide de certains outils. Vous pouvez vous débarrasser de ce code indésirable dans vos applications .NET. Cet article explique **comment rendre des documents Word en HTML minifié à l'aide de C#**."
tags: ['Minify HTML using CSharp', 'Word to Clean HTML', 'Word to Minified HTML']
categories: ['GroupDocs.Viewer Product Family']
---

Le nettoyage et la minification du HTML améliorent le temps de chargement et l'utilisation de la bande passante des pages Web. On observe que du code inutile est injecté lorsqu'un document est converti au format HTML à l'aide de certains outils. Vous pouvez vous débarrasser de ce code indésirable dans vos applications .NET. Cet article explique **comment rendre des documents Word en HTML minifié à l'aide de C#**.



{{< figure align=center src="images/render-word-to-clean-html-using-dotnet.jpg" alt="Rendre Word en HTML propre à l'aide de C#">}}


## API .NET pour le rendu en HTML minifié {#stl-viewer-dotnet-api}

[GroupDocs.Viewer](https://products.groupdocs.com/viewer/) fournit une [API de visualisation de documents](https://products.groupdocs.com/viewer/net/) qui permet de rendre divers documents en HTML, PDF et formats d'image dans l'application .NET. J'utiliserai cette API dans les exemples pour convertir le fichier DOCX en un fichier HTML propre.

Vous pouvez télécharger les DLL ou le programme d'installation MSI à partir de la [section des téléchargements](https://downloads.groupdocs.com/viewer/net) ou installer l'API dans votre application .NET via [NuGet](https://www.nuget.org/packages/groupdocs.viewer).

```
PM> Install-Package GroupDocs.Viewer
```

## Rendre Word DOC/DOCX en HTML minifié à l'aide de C# {#stl-to-pdf}

Les fichiers HTML peuvent être obtenus avec des ressources intégrées ou externes en utilisant les méthodes respectives. Les étapes suivantes montrent comment convertir le document Word (DOC/DOCX) en HTML minifié à l'aide de C#.

* Chargez le fichier DOCX à l'aide de la classe [Viewer](https://apireference.groupdocs.com/viewer/net/groupdocs.viewer/viewer).
* Préparez les options de rendu HTML à l'aide de la classe [HtmlViewOptions](https://apireference.groupdocs.com/viewer/net/groupdocs.viewer.options/htmlviewoptions).
* Activez l'option Minify en la définissant sur true.
* Utilisez [View()](https://apireference.groupdocs.com/viewer/net/groupdocs.viewer/viewer/methods/view) avec les options créées pour rendre le fichier DOCX en HTML minifié.

L'exemple de code C# suivant restitue le fichier Word DOCX en HTML minifié.

```
// Convertir Word DOC/DOCX en HTML minifié à l'aide de C#
using (Viewer viewer = new Viewer("path/document.docx"))
{
    HtmlViewOptions options = HtmlViewOptions.ForEmbeddedResources("path/page_{0}.html");
    options.Minify = true;

    viewer.View(options);
}
```

## Obtenez une licence API gratuite

Vous pouvez utiliser les API gratuitement sans limitation d'évaluation en [obtenant une licence temporaire](https://purchase.groupdocs.com/temporary-license).

## Conclusion

Pour résumer, nous avons discuté de la façon de rendre les fichiers DOC/DOCX en HTML minifié à l'aide de C#. Vous pouvez créer votre propre convertisseur et nettoyeur en ligne qui permet aux utilisateurs de convertir les documents en HTML minifié. En outre, vous pouvez en savoir plus sur [GroupDocs.Viewer pour .NET](https://products.groupdocs.com/viewer/net/) à partir de sa [documentation](https://docs.groupdocs.com/viewer/) . Pour toute question, contactez-nous via le [forum](https://forum.groupdocs.com/).

## Voir également

* [Code source en PDF en C#](https://blog.groupdocs.com/2021/12/03/convert-source-code-to-pdf-in-csharp/)
* [Visionneuse de fichiers STL utilisant C#](https://blog.groupdocs.com/2021/12/28/stl-file-viewer-using-csharp/)
* [Afficher les documents CAO à l'aide de C#](https://blog.groupdocs.com/2021/04/27/view-cad-documents-using-csharp/)
* [Afficher les documents Word en tant que page HTML réactive à l'aide de C#](https://blog.groupdocs.com/2021/08/28/view-word-documents-as-html-responsive-page-using-csharp/)





