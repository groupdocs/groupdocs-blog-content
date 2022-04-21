---
title: "Convertir le code source en PDF en Java"
date: Thu, 16 Dec 2021 16:44:27 +0000
draft: false
url: /fr/2021/12/16/convertir-le-code-source-en-pdf-en-java/
author: 'Shoaib Khan'
summary: 'If you want to share your code snippets, you can convert them into PDF format. In this article, we will discuss **how to convert Java, Python, C++, PHP source code to PDF** format within Java application. Additionally, we will also learn to password-protect the converted PDF files.

Les sujets suivants sont abordés dans cet article :

* API Java de conversion de code source
* Java en PDF en utilisant Java
* Python en PDF en utilisant Java
* PHP vers PDF - Protégez le fichier PDF'
tags: ['Convert Source Code to PDF in Java', 'Java to PDF', 'PHP to PDF', 'Python Code to PDF', 'Source Code to PDF']
categories: ['GroupDocs.Viewer Product Family']
---

Si vous souhaitez partager vos extraits de code, vous pouvez les convertir au format PDF. Pour ce faire, nous discuterons **comment convertir le code source Java, PHP, Python, **C#, C++** au format PDF** dans l'application Java. De plus, nous apprendrons également à protéger par mot de passe les fichiers PDF convertis.



{{< figure align=center src="images/convert-source-code-to-pdf-in-java.jpg" alt="Convertir le code source en PDF">}}


Les sujets suivants sont abordés ci-dessous :

* [API Java de conversion de code source][1]
* [Java vers PDF en utilisant Java][2]
* [Python en PDF en utilisant Java][3]
* [PHP vers PDF - Protégez le fichier PDF][4]

## API Java du convertisseur de code source {#source-code-converter-java-api}

[GroupDocs.Viewer][5] fournit une API Java pour [rendre les fichiers dans différents formats][6] comme les formats PDF, HTML et image. J'utiliserai cette API pour convertir les fichiers de code source de différentes langues au format PDF.

Vous pouvez télécharger le fichier **JAR** à partir de la [section des téléchargements][7] ou utiliser les dernières configurations de référentiel et de dépendance [Maven][8] dans vos applications Java.

```
<repository>
	<id>GroupDocsArtifactRepository</id>
	<name>GroupDocs Artifact Repository</name>
	<url>https://repository.groupdocs.com/repo/</url>
</repository>
<dependency>
        <groupId>com.groupdocs</groupId>
        <artifactId>groupdocs-viewer</artifactId>
        <version>21.11</version> 
</dependency>
```

## Convertir le code Java en PDF {#java-to-pdf}

Venons-en rapidement à l'objectif et voyons les résultats. Les étapes suivantes vous permettent de convertir le fichier de code source Java en PDF.

* Chargez le fichier Java à l'aide de la classe [Viewer][9].
* Définissez le fichier de sortie et les options à l'aide de la classe [PdfViewOptions][10].
* Convertissez le fichier Java chargé en PDF en utilisant la méthode [view()][11] appropriée.

L'extrait de code Java suivant convertit le fichier de code source Java complet au format PDF.

```
/*
 * Renders a Java file into PDF using Java
 */
try (Viewer viewer = new Viewer("path/HelloWorld.java")) 
{
    PdfViewOptions viewOptions = new PdfViewOptions("path/HelloWorld.pdf");
    viewer.view(viewOptions);
}
```

Voici le PDF converti du fichier Java en utilisant le code Java ci-dessus. Si vous souhaitez ajouter de la sécurité au fichier PDF résultant, passez à la section ci-dessous où le [fichier PHP est converti][12].



{{< figure align=center src="images/java-to-pdf.jpg" alt="Fichier source Java converti en PDF">}}


## Convertir le code Python en PDF en utilisant Java {#python-to-pdf}

Pensez-vous vraiment qu'il y aura un code séparé pour convertir le code Python en PDF et que ce sera quelque peu différent de la conversion d'un fichier Java ? Non, c'est la même chose, donnez simplement le bon fichier .py. Les étapes suivantes vous permettent de convertir le code Python en PDF.

* Chargez le fichier Python à l'aide de la classe [Viewer][13].
* Définissez le chemin et les options du fichier de sortie à l'aide de la classe [PdfViewOptions][14].
* Convertissez le fichier .py chargé en PDF en utilisant la méthode [view()][15] appropriée.

L'extrait de code Java suivant convertit le fichier de code source Python complet au format PDF.

```
/*
 * Convert Python source file into PDF using Java
 */
try (Viewer viewer = new Viewer("path/source.py")) 
{
    PdfViewOptions viewOptions = new PdfViewOptions("path/python-source.pdf");
    viewer.view(viewOptions);
}
```

## Convertir PHP en PDF en utilisant Java {#php-to-pdf}

De même, vous pouvez également convertir les fichiers PHP. Encore une chose à ajouter ici; lors de la conversion de vos fichiers de code source, vous pouvez ajouter de la sécurité aux fichiers PDF. Protégeons le code PHP lors de sa conversion au format PDF. Les étapes suivantes montrent comment convertir le fichier PHP en PDF.

* Chargez le fichier PHP à l'aide de la classe [Viewer][16].
* Définissez la sécurité à l'aide de la classe [Security][17].
* Définissez les mots de passe pour ouvrir et modifier le fichier PDF résultant.
* Définissez le fichier de sortie et ses options à l'aide de la classe [PdfViewOptions][18].
* Appelez la méthode [view()][19] pour rendre le fichier PHP chargé au format PDF protégé.

L'exemple de code Java suivant convertit le fichier de code source PHP en un fichier PDF protégé par mot de passe.

```
/*
 * Convert Php source file into PDF using Java
 */
try (Viewer viewer = new Viewer("path/source.php")) 
{
    Security security = new Security();
    security.setDocumentOpenPassword("OpEnD0c");
    security.setPermissionsPassword("Ple@se");
    security.setPermissions(Permissions.ALLOW_ALL ^ Permissions.DENY_PRINTING);

    PdfViewOptions viewOptions = new PdfViewOptions("path/php-source.pdf");
    viewOptions.setSecurity(security);
    
    viewer.view(viewOptions);
}
```

De même, vous pouvez utiliser ce code pour d'autres codes sources de [langages de programmation pris en charge][20] comme C#, C/C++, GROOVY, Ruby, etc.

## Obtenez une licence API gratuite

Vous pouvez [obtenir une licence temporaire gratuite][21] pour utiliser l'API sans les limitations d'évaluation.

## Conclusion

Pour conclure, nous avons appris à convertir des fichiers de code source de différents langages de programmation au format PDF en utilisant Java. Nous avons converti les fichiers Java, Python et PHP au format PDF. De plus, nous avons appris à protéger par mot de passe le fichier PDF résultant. À l'aide de cette API, vous pouvez commencer à créer votre propre application Java de visionneuse de code source.

Pour en savoir plus sur **GroupDocs.Viewer**, consultez la [documentation][22]. Pour toute question, contactez-nous via le [forum][23].

## Voir également

* [Convertir des images en PDF en Java][24]
* [Convertir des feuilles Excel en PDF en Java][25]
* [Afficher les documents Word en tant que page HTML réactive à l'aide de Java][26]







[1]: #source-code-converter-java-api
[2]: #java-to-pdf
[3]: #python-to-pdf
[4]: #php-to-pdf
[5]: https://products.groupdocs.com/viewer/
[6]: https://docs.groupdocs.com/viewer/java/supported-document-formats/
[7]: https://downloads.groupdocs.com/viewer
[8]: https://repository.groupdocs.com/webapp/#/artifacts/browse/tree/General/repo/com/groupdocs
[9]: https://apireference.groupdocs.com/viewer/java/com.groupdocs.viewer/Viewer
[10]: https://apireference.groupdocs.com/viewer/java/com.groupdocs.viewer.options/PdfViewOptions
[11]: https://apireference.groupdocs.com/viewer/java/com.groupdocs.viewer/Viewer#view(com.groupdocs.viewer.options.ViewOptions)
[12]: #php-to-pdf
[13]: https://apireference.groupdocs.com/viewer/java/com.groupdocs.viewer/Viewer
[14]: https://apireference.groupdocs.com/viewer/java/com.groupdocs.viewer.options/PdfViewOptions
[15]: https://apireference.groupdocs.com/viewer/java/com.groupdocs.viewer/Viewer#view(com.groupdocs.viewer.options.ViewOptions)
[16]: https://apireference.groupdocs.com/viewer/java/com.groupdocs.viewer/Viewer
[17]: https://apireference.groupdocs.com/viewer/java/com.groupdocs.viewer.options/Security
[18]: https://apireference.groupdocs.com/viewer/java/com.groupdocs.viewer.options/PdfViewOptions
[19]: https://apireference.groupdocs.com/viewer/java/com.groupdocs.viewer/Viewer#view(com.groupdocs.viewer.options.ViewOptions)
[20]: https://docs.groupdocs.com/viewer/java/supported-document-formats/
[21]: https://purchase.groupdocs.com/temporary-license
[22]: https://docs.groupdocs.com/viewer
[23]: https://forum.groupdocs.com/
[24]: https://blog.groupdocs.com/2021/04/21/convert-images-to-pdf-in-java/
[25]: https://blog.groupdocs.com/2021/11/21/convert-excel-spreadsheets-to-pdf-in-java/
[26]: https://blog.groupdocs.com/2021/09/23/view-word-documents-as-responsive-html-page-using-java/


