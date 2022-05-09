---
title: "Convertir le code source en PDF en C#"
date: Fri, 03 Dec 2021 17:19:00 +0000
draft: false
url: /fr/2021/12/03/convert-source-code-to-pdf-in-csharp/
aliases:
- /2019/06/28/create-your-source-code-viewer-using-groupdocs.viewer-for-.net-19.6/
author: 'Shoaib Khan'
summary: "Vous devez parfois convertir les fichiers de code source dans d'autres formats. Cela peut être à des fins de partage ou d'analyse. Cet article explique **comment convertir les fichiers de code source Python**, PHP, Java, C#, C/C++ **au format PDF** dans les applications .NET. De plus, nous protégerons par programme par mot de passe les fichiers convertis."
tags: ['Convert Source Code to PDF in CSharp', 'document rendering API', 'Java to PDF', 'PHP to PDF', 'Python Code to PDF', 'Source Code to PDF', 'source code viewer']
categories: ['GroupDocs.Viewer Product Family']
---



{{< figure align=center src="images/convert-source-code-to-pdf-in-csharp.jpg" alt="Convertir le code source en PDF à l'aide de C#">}}


Vous devez parfois convertir les fichiers de code source dans d'autres formats. Cela peut être à des fins de partage ou d'analyse. Cet article explique **comment convertir les fichiers de code source Python**, PHP, Java, C#, C/C++** au format PDF** dans les applications .NET. De plus, nous protégerons par programme par mot de passe les fichiers convertis.

* [API .NET de conversion de code source][1]
* [Java vers PDF en utilisant C#][2]
* [Python vers PDF en utilisant C#][3]
* [PHP vers PDF - Protégez le fichier PDF][4]

## API .NET pour la conversion du code source {#source-code-converter-dotnet-api}

[GroupDocs.Viewer pour .NET][5] est l'API de visualisation de documents et permet de rendre les documents au format PDF, HTML et images avec l'application .NET. Aujourd'hui, nous allons utiliser cette API dans des exemples pour convertir les fichiers de code source de différentes langues au format PDF.

Vous pouvez télécharger les DLL ou le programme d'installation MSI à partir de la [section des téléchargements][6] ou installer l'API dans votre application .NET via [NuGet][7].

```
PM> Install-Package GroupDocs.Viewer
```

## Convertir du code Java en PDF à l'aide de C# {#java-to-pdf}

Pas besoin de s'impliquer dans des configurations complexes, chargez simplement le fichier Java et transformez-le en PDF. Les étapes suivantes vous expliquent comment convertir le fichier de code source Java en PDF à l'aide de C#.

* Chargez le fichier Java à l'aide de la classe [Viewer][8].
* Définissez le fichier de sortie et ses options à l'aide de la classe [PdfViewOptions][9].
* Convertissez le fichier en PDF en utilisant la méthode [View()][10] appropriée.

L'exemple C# suivant convertit le fichier de code source Java complet au format PDF.

```
/*
 * Renders a Java file into PDF using C#
 */
using (Viewer viewer = new Viewer("path/HelloWorld.java"))
{
   PdfViewOptions viewOptions = new PdfViewOptions("path/HelloWorld.pdf");
   viewer.View(viewOptions);
}
```

Voici le PDF converti du fichier Java avec la mise en surbrillance à l'aide du code C# ci-dessus. Vous pouvez également ajouter une sécurité au fichier PDF converti. Pour en savoir plus sur la sécurisation des fichiers, sautez ci-dessous où les [fichiers PHP sont convertis][11].



{{< figure align=center src="images/java-to-pdf-programmatically.jpg" alt="Fichier source Java converti en PDF à l'aide de C#">}}


## Convertir le code Python en PDF à l'aide de C# {#python-to-pdf}

Pourquoi changer le code si le format de votre fichier source est modifié ? Laissez l'API supporter cette douleur. Fournissez simplement le fichier .py à la bonne méthode. Les étapes suivantes montrent comment convertir le code Python en PDF à l'aide de C#.

* Chargez le fichier source Python à l'aide de la classe [Viewer][12].
* Définissez le chemin du fichier de sortie et les configurations à l'aide de la classe [PdfViewOptions][13].
* Convertissez le fichier .py en PDF en utilisant la bonne méthode [View()][14].

L'exemple de code C# suivant convertit le fichier de code source Python au format PDF.

```
/*
 * Convert Python source file into PDF using C#
 */
 using (Viewer viewer = new Viewer("path/source.py"))
{
   PdfViewOptions viewOptions = new PdfViewOptions("path/python-source.pdf");
   viewer.View(viewOptions);
}
```

## Convertir PHP en PDF en utilisant C# {#php-to-pdf}

De même, vous pouvez également convertir les fichiers PHP. De plus, lors de la conversion de vos fichiers de code source, vous pouvez renforcer la sécurité des fichiers PDF. Sécurisons le code lors de sa conversion. Les étapes suivantes montrent la conversion de fichiers PHP au format PDF avec sécurité en C#.

* Chargez le fichier PHP à l'aide de la classe [Viewer][15].
* Définissez la sécurité prévue du fichier PDF à l'aide de la classe [Security][16].
* Définissez les mots de passe pour ouvrir et modifier le fichier résultant.
* Définissez le fichier de sortie à l'aide de la classe [PdfViewOptions][17].
* Appelez la méthode [View()][18] pour rendre le fichier PHP chargé dans le PDF protégé.

L'extrait de code C# suivant convertit le fichier de code source PHP en un fichier PDF protégé par mot de passe.

```
/*
 * Convert Php source file into PDF using C#
 */
 using (Viewer viewer = new Viewer("path/source.php"))
{
    Security security = new Security();
    security.DocumentOpenPassword = "OpEnD0c";
    security.PermissionsPassword = "Ple@se";
    security.Permissions = Permissions.AllowAll ^ Permissions.DenyPrinting;
    
    PdfViewOptions viewOptions = new PdfViewOptions("path/php-source.pdf");
    viewOptions.Security = security;
                    
    viewer.View(viewOptions);
}
```

De même, vous pouvez utiliser ce code pour les fichiers de codes sources d'autres [langages de programmation pris en charge][19] comme C#, C/C++, JS, Ruby, etc.

## Obtenez une licence API gratuite

Vous pouvez [obtenir une licence temporaire gratuite][20] pour utiliser l'API sans les limitations d'évaluation.

## Conclusion

En résumé, nous avons appris à convertir les fichiers de code source de divers langages de programmation au format PDF à l'aide de C#. Les exemples ont montré la conversion de fichiers Java, Python et PHP au format PDF. De plus, nous avons appris à sécuriser le fichier PDF résultant. À l'aide de cette API, vous pouvez commencer à créer votre propre application .NET de visionneuse de code source.

En savoir plus sur **GroupDocs.Viewer** dans la [documentation][21] pour créer votre propre application de visualisation de code source. Pour toute question, contactez-nous via le [forum][22].

## Voir également

* [Conversion d'images en PDF en C#][23]
* [Conversion de fichiers par e-mail en PDF en C#][24]
* [Conversion de feuilles de calcul Excel en PDF à l'aide de C#][25]
* [Afficher les documents Word en tant que page HTML réactive à l'aide de C #][26]







[1]: #source-code-converter-dotnet-api
[2]: #java-to-pdf
[3]: #python-to-pdf
[4]: #php-to-pdf
[5]: https://products.groupdocs.com/viewer/net/
[6]: https://downloads.groupdocs.com/viewer/net
[7]: https://www.nuget.org/packages/groupdocs.viewer
[8]: https://apireference.groupdocs.com/viewer/net/groupdocs.viewer/viewer
[9]: https://apireference.groupdocs.com/viewer/net/groupdocs.viewer.options/pdfviewoptions
[10]: https://apireference.groupdocs.com/viewer/net/groupdocs.viewer/viewer/methods/view
[11]: #php-to-pdf
[12]: https://apireference.groupdocs.com/viewer/net/groupdocs.viewer/viewer
[13]: https://apireference.groupdocs.com/viewer/net/groupdocs.viewer.options/pdfviewoptions
[14]: https://apireference.groupdocs.com/viewer/net/groupdocs.viewer/viewer/methods/view
[15]: https://apireference.groupdocs.com/viewer/net/groupdocs.viewer/viewer
[16]: https://apireference.groupdocs.com/viewer/net/groupdocs.viewer.options/security
[17]: https://apireference.groupdocs.com/viewer/net/groupdocs.viewer.options/pdfviewoptions
[18]: https://apireference.groupdocs.com/viewer/net/groupdocs.viewer/viewer/methods/view
[19]: https://docs.groupdocs.com/viewer/net/supported-document-formats/
[20]: https://purchase.groupdocs.com/temporary-license
[21]: https://docs.groupdocs.com/viewer
[22]: https://forum.groupdocs.com/
[23]: https://blog.groupdocs.com/2021/05/19/convert-images-to-pdf-in-csharp/
[24]: https://blog.groupdocs.com/2021/05/26/convert-eml-or-msg-file-to-pdf-in-csharp/
[25]: https://blog.groupdocs.com/2021/11/14/convert-excel-spreadsheets-to-pdf-using-csharp/
[26]: https://blog.groupdocs.com/2021/08/28/view-word-documents-as-html-responsive-page-using-csharp/


