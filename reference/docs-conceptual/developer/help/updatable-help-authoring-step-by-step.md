---
ms.date: 09/13/2016
ms.topic: reference
title: Uppdaterings bar hjälp redigering-steg-för-steg
description: Uppdaterings bar hjälp redigering-steg-för-steg
ms.openlocfilehash: c4aecdb801cac16c9cb07853317835fd87e6a0a8
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92658813"
---
# <a name="updatable-help-authoring-step-by-step"></a>Redigering av uppdateringsbar hjälp: Steg för steg

I de här dokumenten visas stegen i processen för att redigera uppdaterings bar hjälp.

## <a name="authoring-updatable-help-step-by-step"></a>Redigering av uppdaterbar hjälp: steg för steg

Uppdaterings bara hjälp har utformats för slutanvändare, men det ger också betydande fördelar för att skapa och hjälpa skribenter, inklusive möjlighet att lägga till innehåll, åtgärda fel, leverera i flera användar gränssnitts kulturer och svara på användar kommentarer och förfrågningar, långt efter att modulen har levererats. I det här avsnittet beskrivs hur du paketerar och laddar upp hjälpfiler så att användarna kan ladda ned och installera dem med hjälp av cmdletarna [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) och [Save-Help](/powershell/module/Microsoft.PowerShell.Core/Save-Help) .

Följande steg ger en översikt över processen för att stödja uppdaterings bar hjälp.

### <a name="step-1-find-an-internet-site-for-your-help-files"></a>Steg 1: hitta en Internet webbplats för dina hjälpfiler

Det första steget i att skapa en uppdaterings bar hjälp är att hitta en Internet plats för modulens hjälpfiler. Du kan faktiskt använda två olika platser. Du kan behålla modulens hjälp informations fil (HelpInfo XML-beskrivs nedan) på en Internet plats och CAB-filerna för hjälp innehåll på en annan Internet plats. Alla CAB-filer för hjälp innehåll för en modul måste finnas på samma plats. Du kan placera CAB-filer för hjälp innehåll för olika moduler på samma plats.

### <a name="step-2-add-a-helpinfouri-key-to-your-module-manifest"></a>Steg 2: Lägg till en HelpInfoURI-nyckel till modulen manifest

Lägg till en **HelpInfoURI** -nyckel till modulen manifest. Nyckelns värde är Uniform Resource Identifier (URI) för platsen för XML-HelpInfo för modulen. För säkerhet måste adressen börja med "http" eller "https". URI: n måste ange en Internet plats, men får inte innehålla HelpInfo XML-filnamn.

Exempel:

```powershell

@{
RootModule = TestModule.psm1
ModuleVersion = '2.0'
HelpInfoURI = 'https://go.microsoft.com/fwlink/?LinkID=0123'
}
```

### <a name="step-3-create-a-helpinfo-xml-file"></a>Steg 3: skapa en HelpInfo XML-fil

XML-HelpInfo innehåller URI: n för Internet platsen för dina hjälpfiler och versions numren för de senaste hjälpfilerna för modulen i varje GRÄNSSNITTs kultur som stöds. Alla Windows PowerShell-moduler har en HelpInfo XML-fil. När du uppdaterar dina hjälpfiler redigerar eller ersätter du HelpInfo XML-filen. du lägger inte till ett annat. Mer information finns i [så här skapar du en HelpInfo XML-fil](./how-to-create-a-helpinfo-xml-file.md).

### <a name="step-4-create-cab-files"></a>Steg 4: skapa CAB-filer

Använd ett verktyg som skapar CAB- `.cab` filer, till exempel `MakeCab.exe` , för att skapa en CAB-fil som innehåller hjälpfilerna för modulen. Skapa en separat CAB-fil för hjälpfilerna i varje GRÄNSSNITTs kultur som stöds. Mer information finns i [så här förbereder du uppdaterings bara CAB-filer](./how-to-prepare-updatable-help-cab-files.md).

### <a name="step-5-upload-your-files"></a>Steg 5: Ladda upp filer

Om du vill publicera nya eller uppdaterade hjälpfiler laddar du upp CAB-filerna till Internet platsen som anges av **HelpContentUri** -elementet i HelpInfo XML-filen. Ladda sedan upp XML-filen HelpInfo till den Internet plats som anges av värdet för **HelpInfoUri** -nyckeln i modulen manifest.
