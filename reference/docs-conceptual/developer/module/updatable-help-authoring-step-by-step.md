---
title: 'Uppdaterings bar hjälp redigering: steg för steg | Microsoft Docs'
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 10098160-c6b4-4339-b8ff-2c4f8cc0699b
caps.latest.revision: 13
ms.openlocfilehash: fbc77cc0fafce93d239da1c459d4b761b21ef3cb
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72357318"
---
# <a name="updatable-help-authoring-step-by-step"></a>Redigering av uppdateringsbar hjälp: steg för steg

I de här dokumenten visas stegen i processen för att redigera uppdaterings bar hjälp.

## <a name="authoring-updatable-help-step-by-step"></a>Redigering av uppdaterbar hjälp: steg för steg

Uppdaterings bara hjälp har utformats för slutanvändare, men det ger också betydande fördelar för att skapa och hjälpa skribenter, inklusive möjlighet att lägga till innehåll, åtgärda fel, leverera i flera användar gränssnitts kulturer och svara på användar kommentarer och förfrågningar, långt efter modulen har levererats. I det här avsnittet beskrivs hur du paketerar och laddar upp hjälpfiler så att användarna kan ladda ned och installera dem med hjälp av cmdletarna [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) och [Save-Help](/powershell/module/Microsoft.PowerShell.Core/Save-Help) .

Följande steg ger en översikt över processen för att stödja uppdaterings bar hjälp.

### <a name="step-1-find-an-internet-site-for-your-help-files"></a>Steg 1: hitta en Internet webbplats för dina hjälpfiler

Det första steget i att skapa en uppdaterings bar hjälp är att hitta en Internet plats för modulens hjälpfiler. Du kan faktiskt använda två olika platser. Du kan behålla modulens hjälp informations fil (HelpInfo XML-beskrivs nedan) på en Internet plats och CAB-filerna för hjälp innehåll på en annan Internet plats. Alla CAB-filer för hjälp innehåll för en modul måste finnas på samma plats. Du kan placera CAB-filer för hjälp innehåll för olika moduler på samma plats.

### <a name="step-2-add-a-helpinfouri-key-to-your-module-manifest"></a>Steg 2: Lägg till en HelpInfoURI-nyckel till modulen manifest

Lägg till en **HelpInfoURI** -nyckel till modulen manifest. Nyckelns värde är Uniform Resource Identifier (URI) för platsen för XML-HelpInfo för modulen. För säkerhet måste adressen börja med "http" eller "https". URI: n måste ange en Internet plats, men får inte innehålla HelpInfo XML-filnamn.

Till exempel:

```powershell

@{
RootModule = TestModule.psm1
ModuleVersion = '2.0'
HelpInfoURI = 'http://go.microsoft.com/fwlink/?LinkID=0123'
}
```

### <a name="step-3-create-a-helpinfo-xml-file"></a>Steg 3: skapa en HelpInfo XML-fil

XML-HelpInfo innehåller URI: n för Internet platsen för dina hjälpfiler och versions numren för de senaste hjälpfilerna för modulen i varje GRÄNSSNITTs kultur som stöds. Alla Windows PowerShell-moduler har en HelpInfo XML-fil. När du uppdaterar dina hjälpfiler redigerar eller ersätter du HelpInfo XML-filen. du lägger inte till ett annat. Mer information finns i [så här skapar du en HelpInfo XML-fil](./how-to-create-a-helpinfo-xml-file.md).

### <a name="step-4-sign-your-help-files"></a>Steg 4: signera dina hjälpfiler

Digitala signaturer krävs inte, men de är en rekommendationer när du delar filer.

### <a name="step-5-create-cab-files"></a>Steg 5: skapa CAB-filer

Använd ett verktyg som skapar CAB-filer, till exempel MakeCab. exe, för att skapa en. CAB-fil som innehåller hjälpfilerna för modulen. Skapa en separat CAB-fil för hjälpfilerna i varje GRÄNSSNITTs kultur som stöds. Mer information finns i [så här förbereder du uppdaterings bara CAB-filer](./how-to-prepare-updatable-help-cab-files.md).

### <a name="step-6-upload-your-files"></a>Steg 6: Ladda upp filer

Om du vill publicera nya eller uppdaterade hjälpfiler laddar du upp CAB-filerna till Internet platsen som anges av **HelpContentUri** -elementet i HelpInfo XML-filen. Ladda sedan upp XML-filen HelpInfo till den Internet plats som anges av värdet för **HelpInfoUri** -nyckeln i modulen manifest.
