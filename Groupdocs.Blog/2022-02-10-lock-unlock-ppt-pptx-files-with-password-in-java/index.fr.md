---
title: "Protection par mot de passe des présentations PowerPoint en Java"
date: Thu, 10 Feb 2022 10:00:00 +0000
draft: false
url: /fr/2022/02/10/lock-unlock-ppt-pptx-files-with-password-in-java/
author: 'Shoaib Khan'
summary: "La protection est importante pour les documents confidentiels et privés. Dans cet article, nous verrons **comment verrouiller les **fichiers de présentation PowerPoint** avec un mot de passe en Java**. De plus, nous apprendrons à déverrouiller les fichiers de présentation en ** supprimant leur mot de passe ** et aussi ** comment changer le mot de passe existant ** des fichiers PPT & PPTX."
tags: ['Add Password to PPT in Java', 'Change PPT Password in Java', 'Lock PPT in Java', 'Remove Password in Java', 'Unlock PPT in Java']
categories: ['GroupDocs.Merger Product Family']
---

La protection est importante pour les documents confidentiels et privés. Dans cet article, nous verrons **comment verrouiller les **fichiers de présentation PowerPoint** avec un mot de passe en Java**. De plus, nous apprendrons à déverrouiller les fichiers de présentation en **supprimant leur mot de passe** et aussi **comment changer le mot de passe existant** des fichiers PPT & PPTX.



{{< figure align=center src="images/password-protect-lock-unlock-presentations-in-java.jpg" alt="Présentations protégées par mot de passe - Verrouiller Déverrouiller PPT-PPTX en Java">}}


Les sujets suivants sont abordés ci-dessous :

* [API Java pour protéger PowerPoint PPT/PPTX avec mot de passe](#lock-unlock-ppt-java-api)
* [Verrouiller les fichiers PowerPoint en ajoutant un mot de passe](#lock-ppt-by-password)
* [Modifier le mot de passe PPT/PPTX](#change-ppt-password)
* [Comment supprimer les mots de passe de présentation](#remove-password-to-unlock-ppt)

## API Java pour verrouiller et déverrouiller les fichiers PowerPoint {#lock-unlock-ppt-java-api}

Afin de gérer la protection des fichiers de présentation, nous utiliserons l'API Java de [GroupDocs.Merger](https://products.groupdocs.com/merger/). L'API fournit les fonctions d'ajout, de modification et de suppression de mot de passe pour les présentations et autres documents.

### Télécharger et configurer

Obtenez la bibliothèque à partir de la section [téléchargements](https://downloads.groupdocs.com/merger/). Pour votre application Java basée sur Maven, ajoutez simplement la configuration pom.xml suivante. Après cela, vous pouvez essayer les exemples de cet article ainsi que les nombreux autres exemples disponibles sur [GitHub](https://github.com/groupdocs-merger). Pour plus de détails, vous pouvez visiter la [référence API](https://apireference.groupdocs.com/merger/java).

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

## Ajouter un mot de passe aux fichiers PowerPoint en Java - Verrouiller PPT/PPTX {#lock-ppt-by-password}



{{< figure align=center src="images/locked-PPT.jpg" alt="Verrouiller PPT avec un mot de passe">}}


Vous pouvez facilement verrouiller n'importe quel fichier de présentation en y ajoutant un mot de passe par programmation. Les étapes suivantes montrent comment ajouter un mot de passe à n'importe quel fichier de présentation PowerPoint (PPT/PPTX) en Java.

* Définissez le mot de passe à l'aide de [AddPasswordOptions](https://apireference.groupdocs.com/merger/java/com.groupdocs.merger.domain.options/AddPasswordOptions).
* Chargez le fichier de présentation à l'aide de la classe [Merger](https://apireference.groupdocs.com/merger/java/com.groupdocs.merger/Merger).
* Appliquez le mot de passe en utilisant [addPassword()](https://apireference.groupdocs.com/merger/java/com.groupdocs.merger/Merger#addPassword(com.groupdocs.merger.domain.options.interfaces.IAddPasswordOptions)) méthode.
* Enregistrez la présentation protégée à l'aide de la méthode [save()](https://apireference.groupdocs.com/merger/java/com.groupdocs.merger/Merger#save(java.lang.String)).

L'extrait de code Java suivant verrouille la présentation en ajoutant un mot de passe au fichier PPT.

```
/*
 * Password Protect PowerPoint Files in Java
 */
AddPasswordOptions addOptions = new AddPasswordOptions("mySECRETpassWORD");

Merger merger = new Merger("path/presentation.pptx");
merger.addPassword(addOptions);
merger.save("path/protected-presentation.pptx");
```

Lorsque vous essayez d'ouvrir le fichier de sortie obtenu à partir du code ci-dessus, l'éditeur ou le visualiseur demandera le mot de passe lors de l'ouverture de la présentation.



{{< figure align=center src="images/enter-pwd-to-protected-pptx-presentation.png" alt="Entrez le mot de passe pour le PPTX protégé">}}


## Mettre à jour le mot de passe existant des fichiers PPT/PPTX en Java {#change-ppt-password}

Si vous doutez que votre mot de passe soit lu par quelqu'un. Vous pouvez le changer facilement. Les étapes suivantes vous permettent de modifier le mot de passe existant du fichier de présentation en Java.

* Préparez les [options de chargement](https://apireference.groupdocs.com/merger/java/com.groupdocs.merger.domain.options/LoadOptions) en utilisant le mot de passe **actuel**.
* Définissez les [options de mise à jour](https://apireference.groupdocs.com/merger/java/com.groupdocs.merger.domain.options/UpdatePasswordOptions) à l'aide du **nouveau** mot de passe.
* Chargez la présentation à l'aide de la classe [Merger](https://apireference.groupdocs.com/merger/java/com.groupdocs.merger/Merger).
* 现在，使用 [updatePassword()](https://apireference.groupdocs.com/merger/java/com.groupdocs.merger/Merger#updatePassword(com.groupdocs.merger.domain.options.interfaces.IUpdatePasswordOptions)) 方法更改密码。
* Enfin, appelez la méthode [save()](https://apireference.groupdocs.com/merger/java/com.groupdocs.merger/Merger#save(java.lang.String)) pour enregistrer le fichier verrouillé.

Voici l'extrait de code Java qui change le mot de passe existant avec un nouveau d'une présentation PowerPoint PPT/PPTX.

```
/*
 * Change password of the protected PPT/PPTX files in Java
 */
LoadOptions loadOptions = new LoadOptions("mySECRETpassWORD");
UpdatePasswordOptions updateOptions = new UpdatePasswordOptions("TOPSECRET_pa22WORD");

Merger merger = new Merger("path/protected-presentation.pptx", loadOptions);
merger.updatePassword(updateOptions);
merger.save("path/pwd-changed-presentation.pptx");
```

## Supprimer le mot de passe de la présentation en Java - Déverrouiller PPT/PPTX {#remove-password-to-unlock-ppt}



{{< figure align=center src="images/unlocked-PPT.jpg" alt="Déverrouiller PPT - Mot de passe supprimé">}}


Supprimons la protection et laissons tout le monde accéder au fichier. Ouvrez simplement le fichier, puis supprimez son mot de passe pour l'accès public. Les étapes suivantes montrent comment déverrouiller le fichier PPT en supprimant le mot de passe dans Java.

* Préparez les [options de chargement](https://apireference.groupdocs.com/merger/java/com.groupdocs.merger.domain.options/LoadOptions) en utilisant le dernier mot de passe.
* **Chargez** le fichier PowerPoint PPT/PPTX à l'aide de la classe [Merger](https://apireference.groupdocs.com/merger/java/com.groupdocs.merger/Merger).
* **Supprimez** le mot de passe à l'aide de la méthode [removePassword()](https://apireference.groupdocs.com/merger/java/com.groupdocs.merger/Merger#removePassword()).
* **Enregistrer** le fichier déverrouillé à l'aide de la méthode [save()](https://apireference.groupdocs.com/merger/java/com.groupdocs.merger/Merger#save(java.lang.String)).

L'exemple de code Java suivant supprime le mot de passe du fichier de présentation PowerPoint pour le garder déverrouillé.

```
/*
 * Remove password from PowerPoint presentations in Java
 */
LoadOptions loadOptions = new LoadOptions("mySECRETpassWORD");

Merger merger = new Merger("path/protected-presentation.pptx", loadOptions);
merger.removePassword();
merger.save("path/no-pwd-presentation.pptx");
```

## Obtenez une licence API gratuite

Vous pouvez [obtenir une licence temporaire gratuite](https://purchase.groupdocs.com/temporary-license) pour utiliser l'API sans les limitations d'évaluation.

## Conclusion

Résumons ce que nous avons appris aujourd'hui. Nous avons utilisé une présentation PowerPoint (PPTX) et d'abord, nous y avons ajouté un mot de passe pour la verrouiller. Ensuite, nous avons changé son mot de passe existant. Enfin, nous avons appris à supprimer le mot de passe du fichier PowerPoint protégé en Java.

Pour en savoir plus sur GroupDocs.Merger pour Java, consultez la [documentation](https://docs.groupdocs.com/merger). Il vous aidera à développer vos propres applications pour verrouiller et déverrouiller les fichiers de présentation. Pour toute question, contactez-nous via le [forum](https://forum.groupdocs.com/).

## Voir également

* [Fichiers PowerPoint en filigrane en Java](https://blog.groupdocs.com/2021/06/09/watermark-presentation-slides-using-java/)
* [Documents protégés par filigrane par mot de passe en Java](https://blog.groupdocs.com/2021/11/26/watermark-password-protected-documents-in-java/)
* [Insérer des objets OLE dans Word, Excel, PowerPoint en utilisant Java](https://blog.groupdocs.com/2020/10/19/insert-ole-objects-in-word-excel-powerpoint-with-java/)
* [Convertir des présentations en images en Java](https://blog.groupdocs.com/2022/01/18/convert-presentations-to-images-in-java/)
* [Convertir des présentations en PDF en Java](https://blog.groupdocs.com/2021/02/15/convert-presentations-odp-pptx-ppt-to-pdf-in-java/)





