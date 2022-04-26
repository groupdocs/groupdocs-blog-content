---
title: "Générer un code QR en Java pour signer des documents et des images"
date: Fri, 19 Feb 2021 11:45:00 +0000
draft: false
url: /fr/2021/02/19/generate-qr-codes-in-java-to-sign-documents-and-images/
aliases:
- /2020/11/17/esign-documents-and-images-with-qr-code-in-java/
author: 'Shoaib Khan'
summary: "**QR code** (**Q**uick **R**esponse code) is the type of 2D Barcodes or matrix barcode. It is the machine-readable label that contains information about the attached item. This article will guide you about programmatically adding QR codes to electronically sign your documents and images using Java."
tags: ['Add QR Code in Java', 'Attach QR Code with Images in Java', 'generate QR Code in Java', 'QR codes in Java', 'Sign docs with QR code in Java', 'Sign Images with QR code in Java']
categories: ['GroupDocs.Signature Product Family']
---

Le **code QR** (**Quick **R**esponse code) est le type de code-barres 2D ou de code-barres matriciel. Il s'agit de l'étiquette lisible par machine qui contient des informations sur l'élément joint. Cet article vous guidera sur la génération par programmation de codes QR en Java pour signer électroniquement vos documents et images.



{{< figure align=center src="images/add-qr-code-to-docs-and-images-using-java.png" alt="Ajouter un code QR aux documents et images en Java">}}


Voici les liens rapides vers les sujets abordés :

* [API Java de génération de code QR][2]
* [Générer un code QR et ajouter aux documents en Java][3]
* [Générer et ajouter un code QR à une image JPG, PNG ou WebP en Java][4]

## API Java pour générer des codes QR {#java-api-for-qr-codes}



{{< figure align=center src="images/groupdocs-signature-java.png" alt="GroupDocs.Signature pour Java">}}


Dans cet article, j'utilise l'API [GroupDocs.Signature pour Java][5] pour générer des codes QR et les joindre à des fichiers PDF, des documents Word, des feuilles de calcul, des présentations et des images. Cette API prend en charge différents types de signatures électroniques pour une grande variété de formats de fichiers. Parmi les types de code QR, l'API prend en charge les éléments suivants :

* Code aztèque
* Code DataMatrix
* GS1 DataMatrix
* QR GS1
*QR

### Télécharger et configurer

Vous pouvez obtenir le fichier JAR à partir de la section [downloads][6] ou ajouter la configuration pom.xml suivante dans vos applications Java basées sur Maven avant de passer aux exemples. Pour plus de détails, vous pouvez visiter la [API Reference][7].

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
        <version>21.2</version> 
</dependency>
```

## Générer un code QR en Java - Ajouter au PDF, Word, Excel, PPT {#add-qr-code-to-documents-in-java}

Les classes **Signature** et **QrCodeSignOptions** peuvent rapidement créer et ajouter différents types de codes QR aux documents et aux images en Java.

1. Créez l'objet de classe **Signature** avec le document source.
2. Définissez les propriétés du code QR à l'aide de la classe **QrCodeSignOptions**.
3. Plus important encore, sélectionnez le type de code QR approprié.
4. Appelez la méthode **sign** avec l'objet Signature, en transmettant le chemin du document résultant et les options de code QR.

Le code Java suivant générera un code QR et le joindra au document PDF fourni.

\[identifiant essentiel="4c70c60f1f5bdfce19da18f8b9f6ca11" file="SignDocsWithQRCode.java"\]

Le fichier PDF résultant est affiché ici avec le code QR ajouté à l'aide du code ci-dessus. De même, vous pouvez fournir n'importe quel document Word, feuille de calcul, présentation ou tout autre [format de document pris en charge][8] pour joindre les codes QR.



{{< figure align=center src="images/Added-QR-Code-in-PDF-using-GroupDocs.Signature-APIs.png" alt="Code QR ajouté au PDF à l'aide de l'API Signature" caption="Fichier PDF avec code QR ajouté à l'aide de GroupDocs.Signature pour l'API Java">}}


## Générer un code QR en Java - Ajouter aux images JPG, PNG ou WebP {#add-qr-code-to-images-in-java}



{{< figure align=center src="images/image-with-qr-code.png" alt="Image avec code QR">}}


Maintenant, vous pensez peut-être qu'il y aura une stratégie différente pour ajouter des codes QR aux images. La réponse est non. Vous pouvez utiliser le même code ci-dessus pour générer un code QR et l'ajouter également aux images. L'API vous permet d'ajouter des codes QR aux images JPG/JPEG, PNG, WebP, BMP, GIF, SVG, CMX et TIFF.

Vous pouvez également modifier l'apparence des codes QR comme la couleur d'arrière-plan, la première couleur, la transparence, etc. Ici, j'ai défini la couleur de fond noire et la première couleur en blanc.

\[identifiant essentiel="31c41589bda73b4310db679300628cb2" file="ChangeQRCodeAppearance.java"\]

## Conclusion

Maintenant, vous devriez être suffisamment confiant pour générer des codes QR dans vos applications Java pour signer électroniquement des documents et des images à l'aide de GroupDocs.Signature. Pour lever toute ambiguïté ou tout scénario non résolu sur la [documentation][9], n'hésitez pas à contacter l'**équipe d'assistance** sur le [forum][10]. De nombreux autres exemples sont également disponibles sur [GitHub][11].

## Voir également

* [Générer des codes QR en C # pour les documents et les images][12]






[1]: https://products.groupdocs.com/signature/java
[2]: #java-api-for-qr-codes
[3]: #add-qr-code-to-documents-in-java
[4]: #add-qr-code-to-images-in-java
[5]: https://products.groupdocs.com/signature/java
[6]: https://downloads.groupdocs.com/signature/java
[7]: https://apireference.groupdocs.com/signature/java
[8]: https://docs.groupdocs.com/signature/java/supported-document-formats/
[9]: https://docs.groupdocs.com/signature/java/
[10]: https://forum.groupdocs.com/c/signature
[11]: https://github.com/groupdocs-signature/GroupDocs.Signature-for-Java
[12]: https://blog.groupdocs.com/2020/11/18/sign-documents-and-images-with-qr-code-in-csharp/


