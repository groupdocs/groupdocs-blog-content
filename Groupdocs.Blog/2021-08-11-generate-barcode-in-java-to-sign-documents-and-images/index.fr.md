---
title: "Générer un code-barres en Java - Ajouter un code-barres aux documents et aux images"
date: Wed, 11 Aug 2021 17:05:00 +0000
draft: false
url: /fr/2021/08/11/generate-barcode-in-java-to-sign-documents-and-images/
aliases:
- /2017/09/12/groupdocs-signature-for-java-release-v17.6.0/
- /2017/09/12/add-barcode-and-qr-code-signatures-in-java-using-groupdocs-signature/
author: 'Shoaib Khan'
summary: "Le codage à barres est l'un des moyens de présenter les données dans un format lisible par machine. Les codes-barres sont normalement utilisés comme identification pour un grand nombre d'articles. Dans cet article, vous apprendrez **comment générer des codes-barres en Java**. De plus, vous verrez comment les codes-barres générés peuvent être appliqués à n'importe lequel de vos **documents ainsi qu'aux images** à l'aide de l'API Java Signature dans vos applications."
tags: ['Add Barcode in Java', 'Apply Barcode to Images in Java', 'eSigning with Java', 'Generate Barcode in Java', 'Sign Documents in Java', 'Sign Documents with Barcode in Java', 'Sign Images with Barcode in Java']
categories: ['GroupDocs.Signature Product Family']
---

Le codage à barres est l'un des moyens de présenter les données dans un format lisible par machine. Les codes-barres sont normalement utilisés comme identification pour un grand nombre d'articles. Dans cet article, vous apprendrez **comment générer des codes-barres en Java**. De plus, vous verrez comment les codes-barres générés peuvent être appliqués à n'importe lequel de vos **documents ainsi qu'aux images** à l'aide de l'API Java Signature dans vos applications.

Les sujets suivants sont traités ci-dessous :

* [API du générateur de code-barres pour Java][1]
* [Appliquer le code-barres aux documents en Java][2]
* [Appliquer le code-barres aux images en Java][3]

## API Java pour générer des codes-barres {#barcode-generator-java-api}

[GroupDocs.Signature][4] présente l'API Java qui permet de signer des documents, des images ou des fichiers de différents formats de fichiers. À l'aide de cette API, vous pouvez facilement générer et appliquer différents types de signatures telles que des codes-barres, des codes QR, du texte, des images, des métadonnées, des signatures numériques, des tampons, des signatures de champs de formulaire, etc. L'API permet également de personnaliser la signature de plusieurs façons.

### Télécharger ou configurer

Vous pouvez télécharger le fichier **JAR** à partir de la [section des téléchargements][5], ou simplement obtenir les dernières configurations de référentiel et de dépendance pour le pox.xml de vos applications Java **basées sur maven**.

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
        <artifactId>groupdocs-signature</artifactId>
        <version>21.5</version> 
</dependency>
```

## Générer un code-barres en Java pour les documents et les images {#generate-barcode-in-java}

Les codes-barres peuvent être générés par programmation avec le texte personnalisé, l'apparence et différents types d'encodage. Certains des types de codes-barres pris en charge incluent le Code 32, le Code 128, le DotCode, le GS1, l'ISBN, le PDF417, le Postnet, l'UPCA et bien d'autres. Ces codes-barres peuvent être appliqués à une grande liste de [formats de documents et d'images pris en charge][6].

Voici les principales étapes pour appliquer des codes-barres à n'importe quel document ou image.

* Charger le document ou l'image.
* Générez le code-barres avec le texte, l'apparence, l'encodage et d'autres propriétés.
* Joignez le code-barres généré au fichier sélectionné.



{{< figure align=center src="images/generate-barcode-using-java-1024x768.png" alt="Générer un code-barres en Java">}}


## Générer un code-barres et appliquer aux documents en Java {#apply-barcode-to-documents}

Générer des codes-barres et les personnaliser en fonction des besoins n'est pas une procédure complexe. Que les documents cibles soient un document MS Word, un fichier PDF, une feuille de calcul Excel ou une présentation, les étapes pour ajouter un code-barres seraient les mêmes pour tous les différents formats. Les étapes suivantes expliquent comment générer des codes-barres et les appliquer/attacher à n'importe quel document en Java.

* Chargez le document (PDF, document Word, tableur, PPT, …) en utilisant la classe [Signature][7].
* Définissez les options de code-barres à l'aide de la classe [BarcodeSignOptions][8].
* Définissez les propriétés du code-barres telles que le type d'encodage, la position, la taille, la couleur d'arrière-plan ou de premier plan, la police, etc.
* Appelez la méthode [sign][9] pour joindre le code-barres généré au document chargé.

Le code source suivant génère un code-barres et le joint à un document PDF à l'aide de Java.

```
// Générer et appliquer des codes-barres aux documents (DOC, DOCX, PDF, PPT, XLS, XLSX, ...) en Java
Signature signature = new Signature("path/document.pdf");

// Créer une option de code-barres avec le texte du code-barres
BarcodeSignOptions options = new BarcodeSignOptions("<00-0-0000-0> 2021-08");
options.setEncodeType(BarcodeTypes.Code128);

// Alignement et apparence des codes-barres
options.setLeft(205);
options.setTop(170);
options.setHeight(50);
options.setWidth(200);
options.setForeColor(Color.BLUE);
options.setCodeTextAlignment(CodeTextAlignment.Below);

// Joindre le code-barres avec le document
signature.sign(outputFilePath, options);
```

## Générer un code-barres et appliquer aux images en Java {#apply-barcode-to-images}

De manière très similaire, vous pouvez appliquer des codes-barres aux images. Que vous ayez une image JPG, PNG, WebP ou tout autre format d'image comme GIF, TIF, CDR, SVG ou tout autre, vous pouvez joindre le code-barres à l'image chargée.

Voici l'étape pour générer des codes-barres et les appliquer à n'importe quelle image à l'aide de l'API Java.

* Chargez votre image (JPG, PNG, WebP, …) en utilisant [Signature][10].
* Préparez les options de code-barres à l'aide de [BarcodeSignOptions][11].
* Personnalisez le code-barres en définissant le texte, le type d'encodage, la position, la taille, l'apparence, etc.
* Appliquez le code-barres pour signer l'image en utilisant la méthode [sign][12].

Le code source suivant génère un code-barres et l'attache à une image JPG en Java.

```
// // Générer et appliquer des codes-barres aux images (JPG, PNG, BMP, ...) en Java
Signature signature = new Signature("path/image.jpg");

// Créer une option de code-barres avec le texte du code-barres
BarcodeSignOptions options = new BarcodeSignOptions("<00-0-0000-0> 2021-08");
options.setEncodeType(BarcodeTypes.Code128);

// Alignement et apparence des codes-barres
options.setLeft(100);
options.setTop(100);
options.setHeight(50);
options.setWidth(200);
options.setForeColor(Color.BLUE);
options.setCodeTextAlignment(CodeTextAlignment.Above);

// Joindre le code-barres avec l'image
signature.sign(outputFilePath, options);
```

## Obtenez une licence API gratuite

Vous pouvez [obtenir une licence temporaire gratuite][13] afin d'utiliser l'API sans les limitations d'évaluation.

## Conclusion

Pour conclure, vous avez appris à générer les codes-barres en Java. De plus, vous avez vu comment ajouter ces codes-barres générés à vos images et documents. Vous pouvez maintenant développer votre propre application Java de générateur de codes-barres.

Vous pouvez en savoir plus sur l'API Java Signature à l'aide de la [documentation][14] ou des exemples disponibles sur [GitHub][15]. Contactez-nous sur le [forum][16].

## Voir également

* [Générer des codes QR pour les images et les documents en Java][17]
* [Générer des codes QR en C # pour les documents et les images][18]







[1]: #barcode-generator-java-api
[2]: #apply-barcode-to-documents
[3]: #apply-barcode-to-images
[4]: https://products.groupdocs.com/signature/
[5]: https://downloads.groupdocs.com/signature
[6]: https://docs.groupdocs.com/signature/java/supported-document-formats/
[7]: https://apireference.groupdocs.com/java/signature/com.groupdocs.signature/Signature
[8]: https://apireference.groupdocs.com/signature/java/com.groupdocs.signature.options.sign/BarcodeSignOptions
[9]: https://apireference.groupdocs.com/signature/java/com.groupdocs.signature/Signature#sign(java.io.OutputStream,%20com.groupdocs.signature.options.sign.SignOptions)
[10]: https://apireference.groupdocs.com/java/signature/com.groupdocs.signature/Signature
[11]: https://apireference.groupdocs.com/signature/java/com.groupdocs.signature.options.sign/BarcodeSignOptions
[12]: https://apireference.groupdocs.com/signature/java/com.groupdocs.signature/Signature#sign(java.io.OutputStream,%20com.groupdocs.signature.options.sign.SignOptions)
[13]: https://purchase.groupdocs.com/temporary-license
[14]: https://docs.groupdocs.com/signature/java/
[15]: https://github.com/groupdocs-signature
[16]: https://forum.groupdocs.com/
[17]: https://blog.groupdocs.com/2021/02/19/generate-qr-codes-in-java-to-sign-documents-and-images/
[18]: https://blog.groupdocs.com/2021/01/27/generate-qr-codes-in-csharp-to-sign-documents-and-images/


