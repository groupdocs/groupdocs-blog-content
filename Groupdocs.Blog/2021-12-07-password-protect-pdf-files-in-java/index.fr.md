---
title: "Protection par mot de passe des fichiers PDF en Java"
date: Tue, 07 Dec 2021 07:36:00 +0000
draft: false
url: /fr/2021/12/07/password-protect-pdf-files-in-java/
author: 'Shoaib Khan'
summary: 'There are different security levels that you can provide to your confidential documents. You can apply watermarks, encrypt files, or you can make your documents password-protected. In this article, we will see **how to programmatically add password protection to the PDF files within the Java applications**. Further, we will learn to **change the password** and also to **remove the passwords** to unlock PDF files.

Les sujets suivants sont abordés dans cet article :

* API Java pour la protection par mot de passe des fichiers PDF
* Mot de passe protéger les fichiers PDF en Java
* Changer le mot de passe PDF en Java
* Comment supprimer le mot de passe PDF - Déverrouiller PDF'
tags: ['Add Password to PDF in Java', 'Change PDF Password in Java', 'Lock PDF in Java', 'Password Protect Document', 'Remove Password in Java', 'Unlock PDF in Java']
categories: ['GroupDocs.Merger Product Family']
---

Il existe différents niveaux de sécurité que vous pouvez fournir à vos documents confidentiels. Vous pouvez [appliquer des filigranes][1], crypter des fichiers ou vous pouvez [protéger vos documents par mot de passe][2]. Dans cet article, nous verrons **comment ajouter par programme une protection par mot de passe aux fichiers PDF dans les applications Java**. De plus, nous apprendrons à **changer le mot de passe** et également à **supprimer les mots de passe** pour déverrouiller les fichiers PDF.



{{< figure align=center src="images/password-protect-lock-unlock-pdf-in-java.jpg" alt="Protégez les fichiers PDF avec un mot de passe en Java - Verrouiller Déverrouiller">}}


Les sujets suivants sont abordés ci-dessous :

* [API Java pour la protection par mot de passe des fichiers PDF][3]
* [Mot de passe protéger les fichiers PDF en Java][4]
* [Modifier le mot de passe PDF en Java][5]
* [Comment supprimer le mot de passe PDF - Déverrouiller PDF][6]

## API Java pour verrouiller et déverrouiller les fichiers PDF {#lock-unlock-pdf-java-api}

[GroupDocs.Merger pour Java][7] est l'API qui permet de verrouiller et de déverrouiller des documents. Nous l'utiliserons pour ajouter, modifier et supprimer des fonctions de sécurité par mot de passe pour les documents PDF dans les applications Java. Outre la protection et la déprotection des documents, l'API fournit de nombreuses autres fonctionnalités telles que le fractionnement, la fusion de documents et bien d'autres qui sont mentionnées dans la [documentation][8].

Vous pouvez télécharger le fichier **JAR** à partir de la [section des téléchargements][9] ou utiliser les dernières configurations de référentiel et de dépendance [Maven][10] dans vos applications Java.

```
<repository>
	<id>GroupDocsJavaAPI</id>
	<name>GroupDocs Java API</name>
	<url>http://repository.groupdocs.com/repo/</url>
</repository>
<dependency>
        <groupId>com.groupdocs</groupId>
        <artifactId>groupdocs-merger</artifactId>
        <version>21.9</version> 
</dependency>
```

## Ajouter un mot de passe au PDF en Java - Verrouiller le PDF {#lock-pdf-by-password}



{{< figure align=center src="images/locked-PDF.jpg" alt="Verrouiller le PDF avec un mot de passe">}}


Passons rapidement à l'ajout d'une protection par mot de passe aux fichiers PDF pour plus de sécurité. Les étapes suivantes montrent comment ajouter un mot de passe aux documents PDF en Java.

* Définissez le mot de passe à l'aide de la classe [AddPasswordOptions][11].
* Chargez le fichier PDF en utilisant la classe [Merger][12].
* Protégez le fichier en ajoutant un mot de passe à l'aide de la méthode [addPassword()][13].
* Enregistrez le fichier protégé en utilisant la méthode [save()][14].

L'extrait de code suivant ajoute un mot de passe à un fichier PDF en Java.

```
/*
 * Add password protection to the PDF document in Java
 */
Merger merger = new Merger("path/document.pdf");
AddPasswordOptions addOptions = new AddPasswordOptions("mySECRETpassWORD");

merger.addPassword(addOptions);
merger.save("path/protected-document.pdf");
```

Si vous essayez d'ouvrir le fichier PDF protégé par mot de passe, le visualiseur PDF vous demandera d'entrer le mot de passe.



{{< figure align=center src="images/enter-pwd-to-protected-pdf-1024x298.png" alt="Entrez le mot de passe pour le PDF protégé">}}


## Mettre à jour le mot de passe existant des fichiers PDF en Java {#change-pdf-password}

Et si votre secret n'était plus un secret ? Rendez-le secret à nouveau. Remplaçons le mot de passe par un nouveau. Les étapes suivantes modifient le mot de passe existant d'un fichier PDF en Java.

* Définissez les [options de chargement][15] en utilisant le mot de passe actuel.
* Définissez maintenant les [options de mise à jour][16] en utilisant le nouveau mot de passe.
* Chargez le document PDF à l'aide de la classe [Merger][17] et des options de chargement.
* Modifiez le mot de passe existant à l'aide de la méthode [updatePassword()][18].
* Enregistrez à nouveau le fichier protégé par mot de passe avec le mot de passe mis à jour en utilisant la méthode [save()][19].

L'extrait de code modifie le mot de passe actuel du document PDF à l'aide du code Java.

```
/*
 * Update password of the protected PDF document in Java
 */
LoadOptions loadOptions = new LoadOptions("mySECRETpassWORD");
UpdatePasswordOptions updateOptions = new UpdatePasswordOptions("TOPSECRET_pa22WORD");

Merger merger = new Merger("path/protected-document.pdf", loadOptions);
merger.updatePassword(updateOptions);
merger.save("path/pwd-changed-document.pdf");
```

## Supprimer le mot de passe des fichiers PDF en Java - Déverrouiller PDF {#remove-password-to-unlock-pdf}



{{< figure align=center src="images/unlocked-PDF.jpg" alt="PDF déverrouillé - Mot de passe supprimé">}}


Si la protection des fichiers n'est plus nécessaire, vous pouvez supprimer le mot de passe. Les étapes suivantes montrent comment supprimer le mot de passe d'un fichier PDF protégé en Java.

* Préparez les [options de chargement][20] en utilisant le mot de passe existant.
* Chargez le document PDF à l'aide de la classe [Merger][21] à l'aide des options de chargement.
* Supprimez son mot de passe en utilisant la méthode [removePassword()][22].
* Enregistrez le fichier déverrouillé en utilisant la méthode [save()][23].

Voici l'exemple de code Java pour supprimer le mot de passe d'un fichier PDF pour le déverrouiller.

```
/*
 * Remove password protection of PDF document in Java
 */
LoadOptions loadOptions = new LoadOptions("mySECRETpassWORD");

Merger merger = new Merger("path/protected-document.pdf", loadOptions);
merger.removePassword();
merger.save("path/no-pwd-document.pdf");
```

## Obtenez une licence API gratuite

Vous pouvez [obtenir une licence temporaire gratuite][24] pour utiliser l'API sans les limitations d'évaluation.

## Conclusion

Pour conclure, nous avons discuté de la protection par mot de passe des documents PDF. Initialement, nous avons verrouillé le fichier PDF en ajoutant un mot de passe. Ensuite, nous avons changé son mot de passe. Enfin, nous avons supprimé le mot de passe du fichier PDF pour les garder déverrouillés. Vous pouvez maintenant penser à créer votre propre application Java de protection et de suppression de mot de passe.

Pour en savoir plus sur GroupDocs.Merger pour Java, consultez la [documentation][25]. Pour toute question, contactez-nous via le [forum][26].

## Voir également

* [Façons de diviser des fichiers PDF en Java][27]
* [Fichiers PDF en filigrane en Java][28]
* [Protection par mot de passe pour les fichiers PDF utilisant C#][29]







[1]: https://blog.groupdocs.com/category/watermark/
[2]: https://blog.groupdocs.com/?s=password
[3]: #lock-unlock-pdf-java-api
[4]: #lock-pdf-by-password
[5]: #change-pdf-password
[6]: #remove-password-to-unlock-pdf
[7]: https://products.groupdocs.com/merger/java/
[8]: https://docs.groupdocs.com/merger/java/
[9]: https://downloads.groupdocs.com/merger
[10]: https://repository.groupdocs.com/webapp/#/artifacts/browse/tree/General/repo/com/groupdocs
[11]: https://apireference.groupdocs.com/merger/java/com.groupdocs.merger.domain.options/AddPasswordOptions
[12]: https://apireference.groupdocs.com/merger/java/com.groupdocs.merger/Merger
[13]: https://apireference.groupdocs.com/merger/java/com.groupdocs.merger/Merger#addPassword(com.groupdocs.merger.domain.options.interfaces.IAddPasswordOptions)
[14]: https://apireference.groupdocs.com/merger/java/com.groupdocs.merger/Merger#save(java.lang.String)
[15]: https://apireference.groupdocs.com/merger/java/com.groupdocs.merger.domain.options/LoadOptions
[16]: https://apireference.groupdocs.com/merger/java/com.groupdocs.merger.domain.options/UpdatePasswordOptions
[17]: https://apireference.groupdocs.com/merger/java/com.groupdocs.merger/Merger
[18]: https://apireference.groupdocs.com/merger/java/com.groupdocs.merger/Merger#updatePassword(com.groupdocs.merger.domain.options.interfaces.IUpdatePasswordOptions)
[19]: https://apireference.groupdocs.com/merger/java/com.groupdocs.merger/Merger#save(java.lang.String)
[20]: https://apireference.groupdocs.com/merger/java/com.groupdocs.merger.domain.options/LoadOptions
[21]: https://apireference.groupdocs.com/merger/java/com.groupdocs.merger/Merger
[22]: https://apireference.groupdocs.com/merger/java/com.groupdocs.merger/Merger#removePassword()
[23]: https://apireference.groupdocs.com/merger/java/com.groupdocs.merger/Merger#save(java.lang.String)
[24]: https://purchase.groupdocs.com/temporary-license
[25]: https://docs.groupdocs.com/merger
[26]: https://forum.groupdocs.com/
[27]: https://blog.groupdocs.com/2021/10/19/split-pdf-files-in-java/
[28]: https://blog.groupdocs.com/2021/06/26/add-watermark-to-pdf-in-java/
[29]: https://blog.groupdocs.com/2021/11/17/lock-unlock-pdf-files-with-password-using-csharp/


