---
title: 'Redigering av uppdateringsbar hjälp: Stegvisa | Microsoft Docs'
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 10098160-c6b4-4339-b8ff-2c4f8cc0699b
caps.latest.revision: 13
ms.openlocfilehash: fbc77cc0fafce93d239da1c459d4b761b21ef3cb
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62082132"
---
# <a name="updatable-help-authoring-step-by-step"></a>Redigering av uppdateringsbar hjälp: Steg för steg

Detta dokument innehåller stegen redigering uppdateringsbar hjälp.

## <a name="authoring-updatable-help-step-by-step"></a>Redigera uppdateringsbar hjälp: Steg för steg

Uppdateringsbar hjälp är avsedd för slutanvändare, men den också ger betydande fördelar modulskapare och hjälp-skrivare, inklusive möjligheten att lägga till innehåll, åtgärda fel, leverera i flera Användargränssnittet kulturer och svara på användarkommentarer och begäranden, lång tid efter den modulen har levererats. Det här avsnittet beskriver hur du paketerar och hjälp med att ladda upp filer så att användarna kan ladda ned och installera dem med hjälp av den [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) och [Save-Help](/powershell/module/Microsoft.PowerShell.Core/Save-Help) cmdletar.

Följande steg ger en översikt av processen för att stödja uppdateringsbar hjälp.

### <a name="step-1-find-an-internet-site-for-your-help-files"></a>Steg 1: Hitta en webbplats för din hjälpfiler

Det första steget i att skapa uppdateringsbar hjälp är att hitta en plats på Internet för din modul hjälpfiler. Du kan faktiskt använda två olika platser. Du kan behålla din modul hjälpfilen information (HelpInfo XML - beskrivs nedan) på en plats på Internet och help CAB innehållsfilerna på en annan Internetplats. Alla hjälp innehåll CAB-filer för en modul måste vara på samma plats. Du kan placera hjälp innehåll CAB-filer för olika moduler på samma plats.

### <a name="step-2-add-a-helpinfouri-key-to-your-module-manifest"></a>Steg 2: Lägg till en HelpInfoURI nyckel till din modulmanifestet

Lägg till en **HelpInfoURI** avgörande för att din modulmanifestet. Värdet för nyckeln är den identifierare URI (Uniform Resource) för platsen för filen HelpInfo XML information för din modul. Av säkerhetsskäl måste adressen börja med ”http” eller ”https”. URI: N ska ange en plats på Internet, men får inte innehålla HelpInfo XML-filnamn.

Till exempel:

```powershell

@{
RootModule = TestModule.psm1
ModuleVersion = '2.0'
HelpInfoURI = 'http://go.microsoft.com/fwlink/?LinkID=0123'
}
```

### <a name="step-3-create-a-helpinfo-xml-file"></a>Steg 3: Skapa en HelpInfo XML-fil

Den information HelpInfo XML-filen innehåller URI för Internet-platsen för din hjälpfiler och versionsnumren för de senaste hjälpfilerna för i varje UI-kultur som stöds. Alla Windows PowerShell-modulen har en HelpInfo XML-fil. När du uppdaterar din hjälpfiler du redigera eller ersätta HelpInfo XML-filen. du inte lägga till en annan. Mer information finns i [så här skapar du en XML-fil med HelpInfo](./how-to-create-a-helpinfo-xml-file.md).

### <a name="step-4-sign-your-help-files"></a>Steg 4: Registrera din hjälpfiler

Digitala signaturer krävs inte, men de är en rekommendation för bästa praxis när du delar filer.

### <a name="step-5-create-cab-files"></a>Steg 5: Skapa CAB-filer

Använd ett verktyg som skapar CAB-filer, till exempel MakeCab.exe att skapa en. CAB-filen som innehåller hjälpfilerna som för. Skapa en separat CAB-fil för hjälpfilerna i varje UI-kultur som stöds. Mer information finns i [hur du förbereder uppdateringsbar hjälp CAB-filer](./how-to-prepare-updatable-help-cab-files.md).

### <a name="step-6-upload-your-files"></a>Steg 6: Ladda upp dina filer

Om du vill publicera nya eller uppdaterade hjälpfiler överföra CAB-filer till den Internet-plats som anges av den **HelpContentUri** element i HelpInfo XML-filen. Ladda sedan upp HelpInfo XML-filen till den Internet-plats som anges av värdet för den **HelpInfoUri** nyckeln i modulmanifestet.
