---
title: "Convertir des présentations en PDF en Java"
date: Mon, 15 Feb 2021 17:30:00 +0000
draft: false
url: /fr/2021/02/15/convert-presentations-odp-pptx-ppt-to-pdf-in-java/
author: 'Shoaib Khan'
summary: 'As PDF is the popular portable document format, so there comes the need to convert documents of other formats to PDF. Today, we will see **different ways to convert PPT, PPTX, or ODP presentations to PDF in Java**. In an earlier post, we have seen [how to convert presentations using C#][1].

[Continuer la lecture...][2]'
tags: ['Convert ODP to PDF in Java', 'Convert PPT to PDF in Java', 'Convert PPTX to PDF in Java', 'Convert Presentation to PDF in Java']
categories: ['GroupDocs.Conversion Product Family']
---

Comme PDF est le format de document portable populaire, il est donc nécessaire de convertir des documents d'autres formats en PDF. Aujourd'hui, nous verrons **différentes façons de convertir des présentations PPT, PPTX ou ODP en PDF en Java**. Dans un article précédent, nous avons vu [comment convertir des présentations à l'aide de C#][3]. Les scénarios suivants seront couverts dans cet article :

* [API Java de conversion de présentation][4]
* [Convertir des présentations PPT, PPTX ou ODP en PDF en Java][5]
* [Convertir des diapositives spécifiques de présentation en PDF][6]
* [Conversion de diapositives consécutives de présentation en PDF][7]
* [Convertir une présentation protégée par mot de passe en PDF][8]



{{< figure align=center src="images/convert-ppt-to-pdf-in-java.jpg" alt="PPTX en PDF en Java">}}


## API Java de conversion de présentation {#presentation-conversion-java-api}

Pour la conversion des présentations au format PDF, j'utiliserai [GroupDocs.Conversion pour Java][9] dans les exemples de cet article. Parallèlement à cette fonctionnalité, l'API prend en charge une longue [liste de formats de fichiers à convertir les uns dans les autres en Java][10]. Ceux-ci incluent la conversion de **eBooks, de documents de traitement de texte, de feuilles de calcul, d'images, de pages Web, d'e-mails, de CAO** et de nombreux autres formats de documents.

### Télécharger ou configurer



{{< figure align=center src="images/groupdocs-conversion-java.png" alt="Convertir des documents et des images à l'aide de Java">}}


[Téléchargez le JAR][11] à partir des téléchargements ou dans le cas de l'application Java basée sur Maven, ajoutez les configurations de référentiel et de dépendance suivantes dans le fichier pom.xml.

```
<repository>
	<id>GroupDocsJavaAPI</id>
	<name>GroupDocs Java API</name>
	<url>http://repository.groupdocs.com/repo/</url>
</repository>
```
```
<dependency>
        <groupId>com.groupdocs</groupId>
        <artifactId>groupdocs-conversion</artifactId>
        <version>21.1</version> 
</dependency>
```

## Convertir des présentations PPT, PPTX ou ODP en PDF en Java {#convert-presentations-to-pdf-in-java}

Une fois la bibliothèque configurée dans votre projet, vous disposez maintenant de différentes options pour convertir vos présentations au format PDF portable. Commençons par le moyen le plus simple et le plus rapide de convertir l'ensemble du fichier de présentation.

* Créez un objet de classe [Converter][12] avec le document source.
* Instancier l'objet [PdfConvertOptions][13].
* Appelez la méthode **convert** de la classe Converter. Passez le chemin du fichier de sortie et les PdfConvertOptions créés.

Voici le code Java 3 lignes qui convertit le fichier de présentation PowerPoint PPTX en PDF.

```
// Convertir des présentations en PDF en Java à l'aide de l'API de conversion de documents
Converter converter = new Converter("presentation.pptx");
PdfConvertOptions options = new PdfConvertOptions();
converter.convert("pptxToPDF.pdf", options);
```

De même, vous pouvez convertir les présentations au format Microsoft PowerPoint PPT ou au format OpenOffice Impress ODP en PDF avec les mêmes exemples de cet article.

## Convertir des diapositives spécifiques de présentation en PDF en Java {#convert-ppt-slides-to-pdf-in-java}

Si vous souhaitez ignorer quelques diapositives de la présentation ou simplement convertir certaines diapositives spécifiques en PDF au lieu de convertir toute la présentation, **setPages** est la méthode que vous recherchez.

Le code ci-dessous convertit les pages sélectionnées de la présentation PPTX en PDF en Java.

```
// Convertir des diapositives de présentation spécifiées en PDF en Java
Converter converter = new Converter("presentation.pptx");
PdfConvertOptions options = new PdfConvertOptions();
options.setPages(Arrays.asList( 2, 4));
converter.convert("PptSpecificSlidesToPDF.pdf", options);
```

## Convertir des diapositives consécutives de présentation en PDF en Java {#convert-ppt-consecutive-slides-to-pdf}

Vous pouvez également sélectionner l'ensemble spécifique de diapositives dans l'ordre pour les convertir en PDF. Mentionnez simplement le numéro de la diapositive de départ, puis le nombre de diapositives dans la séquence à venir.

* Commencer par l'initialisation de l'objet [Converter][14] avec le fichier de présentation.
* Définir le numéro de la page de départ.
* Définir le nombre de pages consécutives.
* Convertissez les diapositives en PDF en utilisant la méthode **convertir**.

Voici le code Java montrant les étapes ci-dessus et convertissant 3 diapositives consécutives d'une présentation PPTX en PDF à partir de la 2ème diapositive.

```
// Convertir des diapositives consécutives de présentation en PDF en Java
Converter converter = new Converter("presentation.pptx");
PdfConvertOptions options = new PdfConvertOptions();
options.setPageNumber(2);
options.setPagesCount(3);
converter.convert("PptConsecutiveSlidesToPDF.pdf", options);
```

## Convertir une présentation protégée par mot de passe en PDF en Java {#convert-password-protected-ppt-to-pdf-in-java}

Il existe de nombreuses options de chargement lors du chargement de n'importe quelle présentation. Vous pouvez fournir le **mot de passe** pour la présentation protégée à l'aide de la méthode **setPassword**. Après avoir chargé la présentation avec le mot de passe, vous pouvez la convertir comme n'importe quelle autre présentation que nous avons convertie auparavant.

Le code suivant convertit une présentation PPTX protégée par mot de passe en PDF en Java après avoir fourni le mot de passe lors du chargement.

```
// Convertir une présentation protégée par mot de passe en PDF en Java
PresentationLoadOptions loadOptions = new PresentationLoadOptions();
loadOptions.setPassword("GroupDocs");

Converter converter = new Converter("presentation.pptx", loadOptions);
PdfConvertOptions options = new PdfConvertOptions();
converter.convert("pwdPptToPDF.pdf", options);
```

De plus, vous pouvez définir les options de chargement suivantes :

* Spécifiez le **format** de présentation, cependant, il est automatiquement détecté.
* Afficher ou masquer les **commentaires**.
* Afficher ou masquer les **diapositives masquées**.
* Spécifiez la police de remplacement pour les polices manquantes.

## Conclusion

Après avoir essayé les exemples ci-dessus, vous devez être sûr de pouvoir convertir par programmation des présentations et des diapositives au format PDF dans vos applications Java. Vous pouvez essayer de créer votre propre application en utilisant les fonctionnalités mises en évidence ci-dessus pour les formats de présentation MS PowerPoint et OpenOffice Impress tels que PPT, PPTX, ODP, etc.

## Besoin d'aide?

Tout d'abord, découvrez les fonctionnalités de conversion de l'API dans la [documentation][15]. Nous serions là sur le [forum][16] pour vous aider à résoudre tout autre problème.

## Voir également

* [Conversion de présentations (PPT, PPTX) en PDF en C#][17]







[1]: https://blog.groupdocs.com/2020/03/05/convert-presentations-pptx-ppt-to-pdf-in-csharp/
[2]: https://blog.groupdocs.com/2021/02/15/convert-presentations-odp-pptx-ppt-to-pdf-in-java/
[3]: https://blog.groupdocs.com/2020/03/05/convert-presentations-pptx-ppt-to-pdf-in-csharp/
[4]: #presentation-conversion-java-api
[5]: #convert-presentations-to-pdf-in-java
[6]: #convert-ppt-slides-to-pdf-in-java
[7]: #convert-ppt-consecutive-slides-to-pdf
[8]: #convert-password-protected-ppt-to-pdf-in-java
[9]: https://products.groupdocs.com/conversion/java
[10]: https://docs.groupdocs.com/conversion/java/supported-document-formats/
[11]: https://downloads.groupdocs.com/conversion/java
[12]: https://apireference.groupdocs.com/conversion/java/com.groupdocs.conversion/Converter
[13]: https://apireference.groupdocs.com/conversion/java/com.groupdocs.conversion.options.convert/PdfConvertOptions
[14]: https://apireference.groupdocs.com/conversion/java/com.groupdocs.conversion/Converter
[15]: https://docs.groupdocs.com/conversion/java
[16]: https://forum.groupdocs.com/c/conversion
[17]: https://blog.groupdocs.com/2020/03/05/convert-presentations-pptx-ppt-to-pdf-in-csharp/


