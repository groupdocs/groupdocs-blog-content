---
title: 'Introducing Metadata Signatures for PDF in GroupDocs.Signature for Java 18.11'
date: Wed, 12 Dec 2018 18:18:58 +0000
draft: false
url: /2018/12/12/groupdocs.signature-java-18.11/
author: 'Samicheema'
summary: ''
tags: []
categories: ['GroupDocs.Signature for Java', 'GroupDocs.Signature Product Family']
---

[![GroupDocs.Signature](https://blog.groupdocs.com/wp-content/uploads/sites/4/2017/03/groupdocs-signature-java.png)](https://www.groupdocs.com/products/signature/java)

We are delighted to announce another monthly release of [GroupDocs.Signature for Java](https://products.groupdocs.com/signature/java). This latest version **18.11** comes up with multitudinous features along with numerous improvements and fixes. The main feature introduced in this [release](https://docs.groupdocs.com/display/signaturejava/GroupDocs.Signature+for+Java+18.11+Release+Notes) is ability to add and search Metadata Signatures in a PDF document. Therefore, we would recommend you to [download](https://downloads.groupdocs.com/signature/java) the new version of the API to evaluate the exciting new features and enhance your document e-signing experience.

# Features

## Verify Encrypted QR-Code TextUsers of this API can verify the encrypted QR-Code text in a document using property **setDataEncryption** Following example demonstrates how to verify text of encrypted QR-Code Signature in a PDF document:```
// setup key and pasphrase
String key = "1234567890";
String salt = "1234567890";
// create data encryption
IDataEncryption encrypter = new SymmetricEncryption(SymmetricAlgorithmType.Rijndael, key, salt);
// setup verification options
PDFVerifyQRCodeOptions verifyOptions = new PDFVerifyQRCodeOptions("This is private text to be secured.");
// specify as true to verify all pages of a document
verifyOptions.setVerifyAllPages(true);
// setup encrypter to retrieve original text
verifyOptions.setDataEncryption(encrypter);
//verify document
VerificationResult result = handler.verify(fileName, verifyOptions); 
```

## Align Text in Text SignatureUsers can align text in Text Signature for a Words, Slides, Images and PDF documents. Following code sample shows how to align the text in Text Signature for a Cells document:```
// setup options with text of signature
CellsSignTextOptions signOptions = new CellsSignTextOptions("John Smith");
// text rectangle size
signOptions.setHeight(100);
signOptions.setWidth(100);
// set text alignment inside signature (This feature is supported starting from version 18.11)
signOptions.setTextHorizontalAlignment(TextHorizontalAlignment.Center);
signOptions.setTextVerticalAlignment(TextVerticalAlignment.Center); 
```

## Set Signature Position in Cells Document with PixelsThis version of the API allow users to set position of signatures in a Cells document with pixels. Following code shows how to set position of a Text Signature in the Cells document:```
// Specify Signature Options 
CellsSignTextOptions signOptions = new CellsSignTextOptions ("John Smith");
signOptions.setWidth(100);
signOptions.setHeight(100);
signOptions.setTop(15);
signOptions.setLeft(22); 
```

## Ability for CancellationThe API provides ability for cancellation of following processes:

*   Search
*   Verification
*   Signing

Following example demonstrates how to cancel signing process:```
// setup signature option
PdfSignTextOptions signOptions = new PdfSignTextOptions("John Smith",10,10,100,100);
signOptions.setSignAllPages(true);

handler.SignatureStarted.add(new ProcessStartEventHandler() {
public void invoke(Object sender, ProcessStartEventArgs args) {
		System.out.println("Processing of "+args.getTotalSignatures()+" signatures for "+args.getGuid()+" started at " + args.getStarted().toString());
	}
});
handler.SignatureProgress.add(new ProcessProgressEventHandler(){
   public void invoke(Object sender, ProcessProgressEventArgs args) {
	   System.out.println("Singing of "+args.getGuid()+" progress: "+args.getProgress()+" %. Processed "+args.getProcessedSignatures()+" signatures. Since start process spent "+args.getTicks()+" mlsec");
	   if(args.getProgress() > 10){
		   args.setCancel(true);
		   System.out.println("Cancellation of process");
	   }
   }
});
handler.SignatureCompleted.add(new ProcessCompleteEventHandler() {
   public void invoke(Object sender, ProcessCompleteEventArgs args) {
	   if (args.getCanceled()){
		   System.out.println("Singing process was canceled");
	   }else{
		   System.out.println("Singing of "+args.getGuid()+" completed at "+args.getCompleted().toString()+". Processing of "+args.getTotalSignatures()+" signatures took "+args.getTicks()+" mlsec");
	   }
   }
}); 
```

## Support of Measure Type Units for Cells PositioningUsers can set position of Signatures in a Cells document with some predefined measure units for following signature types:

*   Text Signatures
*   Image Signatures
*   Digital Signatures
*   QR-Code Signatures
*   Barcode Signatures
*   Stamp Signatures

Following example demonstrates using **Measure Type** properties to set position of a Image Signature in the Cells document:```
CellsSignImageOptions signOptions = new CellsSignImageOptions (CommonUtilities.getImagesPath("sign.png"));
// specify Size
signOptions.setSizeMeasureType(MeasureType.Percents);
signOptions.setHeight(25);
signOptions.setWidth(25);
// specify size in percents of page size
signOptions.setMarginMeasureType(MeasureType.Percents);
signOptions.getMargin().setTop(25);
// specify Intents
signOptions.setTop(15);
signOptions.setLeft(20); 
```

## Metadata Signatures for PDF DocumentThe Metadata Signature is the additional document property that contains special attributes/tags to keep non visual information inside the document. Following example demonstrates how to compose Metadata Signature options for a PDF document:```
// setup options with text of signature
PdfMetadataSignOptions signMetadataOptions = new PdfMetadataSignOptions();
// Specify different Metadata Signatures and add them to options sigature collection
// setup Author property
PdfMetadataSignature mdSign_Author = new PdfMetadataSignature("Author", "Mr.Scherlock Holmes");
signMetadataOptions.getMetadataSignatures().add(mdSign_Author);
// setup data of document id
PdfMetadataSignature mdSign_DocId = new PdfMetadataSignature("DocumentId", java.util.UUID.randomUUID().toString());
signMetadataOptions.getMetadataSignatures().add(mdSign_DocId);
// setup data of sign date
PdfMetadataSignature mdSign_Date = new PdfMetadataSignature("SignDate", new Date(), "pdf");
signMetadataOptions.getMetadataSignatures().add(mdSign_Date); 
```

## Search Metadata SignatureUsers of this API can search for Metadata Signatures within the document. Following example demonstrates how to search Metadata Signatures in a PDF document:```
// setup search options
PdfSearchMetadataOptions searchOptions = new PdfSearchMetadataOptions();  
// search document
SearchResult result = handler.search("SignedMetadata.pdf", searchOptions); 
```

## Save Image as PDF DocumentImage files can be saved to PDF format using this latest release of the API.

## MatchType for Text Verification OptionsThe API provides ability to verify Text Signatures with an extended option **MatchType**

# Improvements

*   Verify QR-Code and Barcode Signatures without specifying EncodeType
*   Global Exception handler to catch all un-handled exceptions
*   Setting color of QR-code and Barcode text with fore color value
*   Global Exception handler to catch all unhandled exceptions
*   Support of several Words Digital Search Options and Cells Digital Search Options

# Bug Fixes

*   Fix exception on QR-Code Signature Verification when options has no Encode Type specified
*   Wrong text alignment in Text Signature shape for Words
*   QR-Code rendering for various settings
*   Wrong border appearance for PDF Text as Image signatures
*   QR-Code positioning when Signature area is more than generated QR-Code
*   Freezing of signature process on Images for QR-Code Signature
*   Incorrect signing image documents with .psd, .wmf and .svg format
*   Output PDF incorrectly signed with Digital Certificates
*   Unable to search Digital signature in Cells with extended options

# Available Channels and Resources

Here are a few channels and resources for you to learn, try and get technical support on **GroupDocs.Signature** **API for Java**:

*   Download – JAR Files
*   [Documentation](https://docs.groupdocs.com/display/signaturejava/Home "Documentation") – API Docs
*   [Product Support Forum](https://forum.groupdocs.com/c/signature "Product Support Forum") – Technical Support Forum for GroupDocs.Signature
*   [Examples](https://github.com/groupdocs-signature/GroupDocs.Signature-for-Java "Examples") – GitHub source code examples

# Feedback

As always, you are welcome to share your feedback to improve this product. We will be happy to know your thoughts. Just create a [forum thread](https://forum.groupdocs.com/c/signature) and our dedicated support team will be there to respond.




