---
title: "Comment protéger par mot de passe et supprimer la protection des documents Word en Java"
date: Wed, 02 Feb 2022 08:45:00 +0000
draft: false
url: /fr/2022/02/02/lock-unlock-word-documents-with-password-in-java/
author: 'Shoaib Khan'
summary: "Auparavant, nous avons restreint l'accès aux [documents PDF](https://blog.groupdocs.com/2021/12/07/password-protect-pdf-files-in-java/) en appliquant des mots de passe. Dans cet article, nous verrons **comment protéger par mot de passe les documents Word en Java**. De plus, nous apprendrons également à **changer le mot de passe existant** des fichiers DOC et DOCX, et enfin, **comment supprimer la protection par mot de passe pour déverrouiller** les documents Word dans les applications Java."
tags: ['Add Password in Java', 'Change Password in Java', 'Lock Files in Java', 'Lock Word Files in Java', 'Password Protect Word Documents', 'Remove Password in Java']
categories: ['GroupDocs.Merger Product Family']
---

Auparavant, nous avons restreint l'accès aux [documents PDF](https://blog.groupdocs.com/2021/12/07/password-protect-pdf-files-in-java/) en appliquant des mots de passe. Dans cet article, nous verrons **comment protéger par mot de passe les documents Word en Java**. De plus, nous apprendrons également à **changer le mot de passe existant** des fichiers DOC et DOCX, et enfin, **comment supprimer la protection par mot de passe pour déverrouiller** les documents Word dans les applications Java.

{{< figure align=center src="images/lock-unlock-word-documents-in-java.jpg" alt="Mot de passe protéger les documents Word en Java">}}

Les sujets suivants sont traités ci-dessous:

* [API Java pour verrouiller/déverrouiller des documents Word](#java-api-lock-unlock-documents)
* [Ajouter un mot de passe au document Word](#password-protect-document)
* [Modifier le mot de passe du document Word](#change-password)
* [Comment supprimer le mot de passe d'un document Word](#remove-password-to-unlock)

## API Java pour verrouiller/déverrouiller des documents Word {#java-api-lock-unlock-documents}

[GroupDocs.Merger](https://products.groupdocs.com/merger/) présente l'API Java qui permet de verrouiller et de déverrouiller des documents Word dans les applications Java. Nous utiliserons [GroupDocs.Merger pour Java](https://products.groupdocs.com/merger/java/) pour ajouter le mot de passe aux fichiers Word, le modifier et également supprimer la protection par mot de passe des fichiers Word dans Java.

Vous pouvez télécharger le fichier **JAR** à partir de la [section téléchargements](https://downloads.groupdocs.com/merger) ou utiliser le dernier référentiel et dépendance [Maven](https://repository.groupdocs.com/webapp/#/artifacts/browse/tree/General/repo/com/groupdocs) configurations dans vos applications Java.

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

Pour plus de détails sur l'API et sur les autres formats de documents pris en charge, vous pouvez consulter la [documentation](https://docs.groupdocs.com/merger/java/) et le [référentiel GitHub](https://github.com/groupdocs-merger) pour les exemples de code source.

## Mot de passe protéger le document Word en Java {#password-protect-document}

{{< figure align=center src="images/locked-DOC.jpg" alt="Doc Word verrouillé par programmation">}}

Commençons par ajouter un mot de passe au fichier MS Word DOCX pour des raisons de sécurité. Les étapes suivantes montrent comment ajouter un mot de passe aux documents Word en Java.

* Définissez le mot de passe à l'aide de la classe [AddPasswordOptions](https://apireference.groupdocs.com/merger/java/com.groupdocs.merger.domain.options/AddPasswordOptions).
* Chargez le fichier DOCX à l'aide de la classe [Merger](https://apireference.groupdocs.com/merger/java/com.groupdocs.merger/Merger).
* Protégez-le par mot de passe en utilisant [addPassword()](https://apireference.groupdocs.com/merger/java/com.groupdocs.merger/Merger#addPassword(com.groupdocs.merger.domain.options.interfaces.IAddPasswordOptions)) méthode.
* Enregistrez le fichier protégé à l'aide de la méthode [save()](https://apireference.groupdocs.com/merger/java/com.groupdocs.merger/Merger#save(java.lang.String)) appropriée.

L'extrait de code Java suivant ajoute un mot de passe à un fichier MS Word DOCX.

```
/*
 * Mot de passe protéger les documents Word en Java
 */
AddPasswordOptions addOptions = new AddPasswordOptions("mySECRETpassWORD");

Merger merger = new Merger("path/document.docx");
merger.addPassword(addOptions);
merger.save("path/protected-document.docx");
```

Désormais, chaque fois que vous essayez d'ouvrir le document protégé par mot de passe, la visionneuse et l'éditeur de documents demandent le mot de passe pour ouvrir le fichier.

{{< figure align=center src="images/enter-pwd-to-open-protected-word-doc.jpg" alt="Entrez le mot de passe pour ouvrir le document Word protégé">}}

## Changer le mot de passe existant du document Word en Java {#change-password}

Changeons le mot de passe avec un nouveau. Les étapes suivantes modifient le mot de passe existant du fichier Word en Java.

* Définissez les [options de chargement](https://apireference.groupdocs.com/merger/java/com.groupdocs.merger.domain.options/LoadOptions) en utilisant le mot de passe actuel.
* Définissez maintenant le nouveau mot de passe à l'aide des [options de mise à jour du mot de passe](https://apireference.groupdocs.com/merger/java/com.groupdocs.merger.domain.options/UpdatePasswordOptions).
* Chargez le document Word protégé à l'aide de la classe [Merger](https://apireference.groupdocs.com/merger/java/com.groupdocs.merger/Merger) et des options de chargement définies.
* Utilisez la méthode [updatePassword()](https://apireference.groupdocs.com/merger/java/com.groupdocs.merger/Merger#updatePassword(com.groupdocs.merger.domain.options.interfaces.IUpdatePasswordOptions)) pour appliquer le nouveau mot de passe.
* Enregistrez à nouveau le fichier protégé par mot de passe à l'aide de la méthode [save()](https://apireference.groupdocs.com/merger/java/com.groupdocs.merger/Merger#save(java.lang.String)).

L'extrait de code suivant modifie le mot de passe actuel du document Word à l'aide de Java.

```
/*
 * Changer le mot de passe des documents DOC/DOCX protégés en Java
 */
LoadOptions loadOptions = new LoadOptions("mySECRETpassWORD");
UpdatePasswordOptions updateOptions = new UpdatePasswordOptions("TOPSECRET_pa22WORD");

Merger merger = new Merger("path/protected-document.docx", loadOptions);
merger.updatePassword(updateOptions);
merger.save("path/pwd-changed-document.docx");
```

## Supprimer le mot de passe du document Word en Java {#remove-password-to-unlock}

Si le document n'est plus confidentiel et que la protection du fichier n'est pas requise, vous pouvez simplement supprimer le mot de passe. Les étapes suivantes montrent comment supprimer le mot de passe d'un fichier Word protégé en Java.

* Chargez le document Word protégé à l'aide de la classe [Merger](https://apireference.groupdocs.com/merger/java/com.groupdocs.merger/Merger) et du mot de passe existant.
* Supprimez son mot de passe à l'aide de la méthode [removePassword()](https://apireference.groupdocs.com/merger/java/com.groupdocs.merger/Merger#removePassword()).
* Enregistrez le fichier DOCX déverrouillé à l'aide de la méthode [save()](https://apireference.groupdocs.com/merger/java/com.groupdocs.merger/Merger#save(java.lang.String)).

Voici l'exemple de code Java qui supprime le mot de passe d'un fichier Word pour le rendre déverrouillé/non protégé.

```
/*
 * Supprimer le mot de passe du document Word en Java
 */
LoadOptions loadOptions = new LoadOptions("mySECRETpassWORD");

Merger merger = new Merger("path/protected-document.docx", loadOptions);
merger.removePassword();
merger.save("path/no-pwd-document.docx");
```

## Obtenez une licence API gratuite

Vous pouvez [obtenir une licence temporaire gratuite](https://purchase.groupdocs.com/temporary-license) pour utiliser l'API sans les limitations d'évaluation.

## Conclusion

Résumons ce que nous avons discuté ci-dessus. À l'aide d'un simple document Word, nous l'avons verrouillé avec un mot de passe en utilisant l'exemple Java. Ensuite, nous avons appris à changer le mot de passe existant. Enfin, nous avons supprimé le mot de passe du fichier Word pour le déverrouiller dans n'importe quelle application Java.

Pour en savoir plus sur **GroupDocs.Merger pour Java**, consultez sa [documentation](https://docs.groupdocs.com/merger) pour commencer à créer vos propres applications de protection de documents ou de suppression de mots de passe pour divers [formats de documents pris en charge](https://docs.groupdocs.com/merger/net/supported-document-formats/). Pour toute question, contactez-nous via le [forum](https://forum.groupdocs.com/).

## Voir également

* [Pa de fichiers PDF en Java](https://blog.groupdocs.com/2021/12/07/password-protect-pdf-files-in-java/)
* [Différentes façons de fractionner des fichiers PDF en Java](https://blog.groupdocs.com/2021/10/19/split-pdf-files-in-java/)
* [Rechercher et remplacer des mots dans des documents à l'aide de Java](https://blog.groupdocs.com/2021/09/01/find-and-replace-text-in-documents-using-java/)
* [Fusionner plusieurs types de fichiers en un seul à l'aide de Java](https://blog.groupdocs.com/2021/06/13/merge-multiple-file-types-using-java/)