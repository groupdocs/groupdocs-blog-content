---
title: "Convertir les dessins AutoCAD DWG en PDF en Java"
date: Tue, 08 Feb 2022 16:48:40 +0000
draft: false
url: /fr/2022/02/08/convert-cad-drawings-to-pdf-in-java/
author: 'Shoaib Khan'
summary: "**CAO** signifie Conception Assistée par Ordinateur. Il est utilisé pour créer des conceptions architecturales 2D et 3D, des animations informatiques, des effets spéciaux dans les films, des dessins techniques et bien plus encore. **PDF** est l'un des formats de fichiers les plus connus, réputé pour sa portabilité. D'où la nécessité de convertir les fichiers CAO au format PDF lorsque ces dessins techniques doivent être transférés à un utilisateur normal qui n'est pas équipé du logiciel technique prenant en charge les dessins CAO. Cet article aidera les programmeurs à ajouter la fonctionnalité pour **convertir** différents **formats CAO** tels que **DWG, DGN ou DWF en PDF dans des applications Java**."
tags: ['convert cad to pdf in java', 'convert dgn to pdf in java', 'convert dwf to pdf', 'convert dwg to pdf', 'convert dwg to pdf in java', 'dwg to pdf', 'DWG to PDF in Java']
categories: ['GroupDocs.Conversion Product Family']
---

**CAO** signifie Conception Assistée par Ordinateur. Il est utilisé pour créer des conceptions architecturales 2D et 3D, des animations informatiques, des effets spéciaux dans les films, des dessins techniques et bien plus encore. **PDF** est l'un des formats de fichiers les plus connus, réputé pour sa portabilité. D'où la nécessité de convertir les fichiers CAO au format PDF lorsque ces dessins techniques doivent être transférés à un utilisateur normal qui n'est pas équipé du logiciel technique prenant en charge les dessins CAO. Cet article explique aux programmeurs comment **convertir** différents **formats CAO** tels que **DWG en PDF en Java**.



{{< figure align=center src="images/convert-cad-drawings-to-pdf-using-java.png" alt="Convertir des dessins CAO en PDF en Java">}}


Les sujets suivants sont traités ci-dessous:

* [Bibliothèque Java de conversion de dessins CAO](#cad-conversion-java-lib)
* [Convertir DWG en PDF](#dwg-to-pdf)

## Bibliothèque Java de conversion de dessins CAO {#cad-conversion-java-lib}



{{< figure align=center src="images/groupdocs-conversion-java.png" alt="Convertir des documents et des images à l'aide de Java">}}


[GroupDocs.Conversion for Java](https://products.groupdocs.com/conversion/java) est la bibliothèque de conversion de documents et d'images pour les applications Java. Il prend en charge divers formats de fichiers pour la conversion d'un format à un autre, notamment les documents de traitement de texte, les feuilles de calcul, les présentations, les images, les documents portables, les pages Web, les formats Photoshop, les fichiers Microsoft Project, les e-mails, les graphiques vectoriels de Microsoft Visio, les dessins CAO, Langages de description de page, etc.

Dans les exemples ci-dessous, j'utiliserai cette API pour la **conversion de dessins CAO en PDF en Java**. Ce sera mieux si vous téléchargez la bibliothèque et préparez l'environnement de développement au préalable. Vous pouvez obtenir l'API à partir de la section [downloads](https://downloads.groupdocs.com/conversion/java) ou par la configuration suivante dans vos applications Java basées sur maven.

```
<repository>
	<id>GroupDocsJavaAPI</id>
	<name>GroupDocs Java API</name>
	<url>http://repository.groupdocs.com/repo/</url>
</repository>
<dependency>
        <groupId>com.groupdocs</groupId>
        <artifactId>groupdocs-conversion</artifactId>
        <version>21.10.1</version> 
</dependency>
```

## Convertir DWG en PDF en Java {#dwg-to-pdf}

Passons à convertir rapidement le dessin. Ces étapes vous permettent de convertir facilement les dessins AutoCAD DWG en un fichier PDF en Java avec de nombreuses options de personnalisation.

* Définissez les **options de chargement** à l'aide de la classe [CadLoadOptions](https://apireference.groupdocs.com/java/conversion/com.groupdocs.conversion.options.load/CadLoadOptions).
* Spécifiez les mises en page à l'aide de la méthode [setLayoutNames()](https://apireference.groupdocs.com/conversion/java/com.groupdocs.conversion.options.load/CadLoadOptions#setLayoutNames(java.lang.String%5B%5D)).
* **Chargez** le dessin DWG à l'aide de la classe [Conveter](https://apireference.groupdocs.com/java/conversion/com.groupdocs.conversion.options.load/CadLoadOptions).
* Spécifiez les **options de conversion** telles que **largeur**, **hauteur** et **format**.
* **Convertir** en PDF en utilisant le [convert()](https://apireference.groupdocs.com/conversion/java/com.groupdocs.conversion/Converter#convert(java.lang.String,%20com.groupdocs.conversion.options.convert.ConvertOptions)).

Voici le code Java complet qui illustre les étapes ci-dessus et convertit un fichier DWG au format PDF.

```
// Convertir un dessin CAO - DWG en PDF en Java

// Options de chargement des fichiers CAO
CadLoadOptions loadOptions = new CadLoadOptions();
loadOptions.setLayoutNames(new  String[]{ "Layout1"});

// Options de conversion PDF
PdfOptions pdfOptions = new PdfOptions();
pdfOptions.setGrayscale(true);

PdfConvertOptions options = new PdfConvertOptions();
options.setRotate(Rotation.On90);
options.setPdfOptions(pdfOptions);
/*
options.setDpi(300);
options.setWidth(800);
options.setHeight(600);
*/
// Conversion
Converter converter = new Converter("filePath/CAD-Drawing.dwg", loadOptions);
converter.convert("filePath/cadToPDF-Java.pdf", options);
```

Avec un petit changement de code, vous pouvez également convertir les fichiers DGN et DWF en conséquence. Pour un format de fichier qui ne prend pas en charge les mises en page, nous n'utiliserons pas la méthode **setLayoutNames**.

## Conclusion

Pour conclure, nous avons appris à convertir les fichiers CAO au format PDF. Plus précisément, nous avons converti les dessins AutoCAD DWG au format PDF à l'aide de l'API Java. Vous pouvez maintenant essayer de créer votre application Java de conversion CAO en PDF en ligne à l'aide de [GroupDocs.Conversion](https://products.groupdocs.com/conversion/). En cas de confusion, vous pouvez contacter l'**équipe d'assistance gratuite**, qui se fait toujours un plaisir de vous aider sur le [forum](https://forum.groupdocs.com/).

## Voir également

* [Afficher les documents CAO à l'aide de Java](https://blog.groupdocs.com/2021/04/05/viewing-cad-documents-using-java/)
* [Comment réorganiser les pages PDF en Java](https://blog.groupdocs.com/2022/03/10/move-pdf-pages-in-java/)
* [Fichiers PDF en filigrane en Java](https://blog.groupdocs.com/2021/06/26/add-watermark-to-pdf-in-java/)
* [Protection par mot de passe des fichiers PDF en Java](https://blog.groupdocs.com/2021/12/07/password-protect-pdf-files-in-java/)
* [Différentes façons de fractionner des fichiers PDF en Java](https://blog.groupdocs.com/2021/10/19/split-pdf-files-in-java/)
* [Convertir des dessins CAO en PDF en C#](https://blog.groupdocs.com/2020/11/08/convert-cad-drawings-to-pdf-in-csharp/)





