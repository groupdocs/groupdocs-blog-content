---
title: "Vérifier la signature numérique dans les documents à l'aide de Java"
date: Tue, 06 Oct 2020 11:24:19 +0000
draft: false
url: /fr/2020/10/06/verify-digital-signature-in-documents-using-java/
author: 'Shoaib Khan'
summary: "Dans cet article, nous allons apprendre à **vérifier par programmation les documents signés numériquement à l'aide de Java**. L'exemple utilise un document PDF pour la vérification, cependant, vous pouvez également effectuer la vérification de documents de traitement de texte signés numériquement comme MS Word **DOC/DOCX**, des feuilles de calcul Excel **XLS/XLSX** et des présentations **PPT/PPTX **."
tags: ['verify digital signatures in java', 'verify digitally signed documents in java']
categories: ['GroupDocs.Signature Product Family']
---

Les signatures numériques basées sur des certificats sont le type de signature électronique qui fournit le plus haut niveau d'assurance de l'identité d'un signataire et est conforme à des réglementations strictes. Dans cet article, nous allons apprendre à **vérifier par programmation les documents signés numériquement à l'aide de Java**. Dans l'un des [messages précédents][1], nous avons discuté de la vérification des signatures numériques dans les documents utilisant C#.

## API Java pour la vérification de signature



{{< figure align=center src="images/groupdocs-signature-java.png" alt="GroupDocs.Signature pour la signature de documents à l'aide de Java">}}


Cet article utilise l'API Document Signature pour Java de GroupDocs. Le [GroupDocs.Signatures pour Java][2] prend en charge les types de signatures électroniques suivants :

* Signatures de codes-barres
* Signatures de champ de formulaire
* Signatures d'images
* Signatures de métadonnées
* Signatures QR-Code
* Signatures de cachet
* Signatures de texte

Il est donc préférable de préparer votre espace de travail à l'avance soit en téléchargeant la bibliothèque depuis la [section téléchargements][3] ou en définissant la configuration mentionnée dans vos applications basées sur Maven.

## Étapes pour vérifier un document PDF signé numériquement à l'aide de Java

En suivant les étapes, vous pouvez vérifier les documents signés numériquement. Dans cet exemple, j'ai utilisé un document **PDF** pour la vérification, cependant, les mêmes étapes fonctionneront pour les documents **MS Word**, les feuilles de calcul **Excel** et les présentations **Powerpoint**.

1. Instanciez l'objet [Signature][4] avec le document source.
2. Instanciez l'objet de classe [DigitalVerifyOptions][5] et spécifiez les options de vérification.
3. Appelez la méthode [verify][6] de Signature et transmettez les options de vérification spécifiées.

Vous trouverez ci-dessous l'exemple de code source complet qui montre le processus ci-dessus. Ici, le code Java vérifie le document PDF signé numériquement. Vous pouvez également effectuer la vérification de documents de traitement de texte signés numériquement tels que MS Word **DOC/DOCX**, des feuilles de calcul Excel **XLS/XLSX** et des présentations **PPT/PPTX**.

```
// Vérification des signatures numériques dans un document PDF à l'aide de l'API de signature pour Java par GroupDocs
Signature signature = new Signature("sample_signed.pdf");

DigitalVerifyOptions options = new DigitalVerifyOptions("certificate.pfx");
options.setComments("Test comment");
options.setPassword("1234567890");

// Vérifier les signatures des documents
VerificationResult result = signature.verify(options);
if (result.isValid()) {
    System.out.println("Document Verified Successfully !");
}
else {
    System.out.println("Document Verification Failed.");
}
```

## Conclusion

Aujourd'hui, nous avons appris à vérifier les documents MS Word, Excel, PowerPoint et PDF signés numériquement à l'aide de Java. Vous pouvez en savoir plus sur les fonctionnalités de **GroupDocs.Signature pour Java** à l'aide des [articles de la documentation][7].

## Voir également

* [Vérifier les signatures numériques dans les documents à l'aide de C#][8]







[1]: https://blog.groupdocs.com/2019/09/25/verify-digital-signature-in-documents-using-csharp/
[2]: https://products.groupdocs.com/signature/java
[3]: https://downloads.groupdocs.com/signature/java
[4]: https://apireference.groupdocs.com/signature/java/com.groupdocs.signature/Signature
[5]: https://apireference.groupdocs.com/signature/java/com.groupdocs.signature.options.verify/DigitalVerifyOptions
[6]: https://apireference.groupdocs.com/signature/java/com.groupdocs.signature/Signature#verify(com.groupdocs.signature.options.verify.VerifyOptions)
[7]: https://docs.groupdocs.com/signature/java
[8]: https://blog.groupdocs.com/2019/09/25/verify-digital-signature-in-documents-using-csharp/


