---
title: Hur uppdateringsbar hjälp fungerar | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7674636e-a0f2-4587-bfc5-dd3e6ce5489e
caps.latest.revision: 6
ms.openlocfilehash: 5b6ae54ee6c843996c875189b6ee553be5e4f614
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62082268"
---
# <a name="how-updatable-help-works"></a>Så här fungerar uppdateringsbar hjälp

Det här avsnittet förklarar hur uppdateringsbar hjälp processer HelpInfo XML-filen och CAB-filer för varje modul och installerar uppdaterad Hjälp för användare.

## <a name="the-update-help-process"></a>Update-Help-processen

I följande lista beskrivs åtgärderna för den [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) cmdlet när en användare kör ett kommando för att uppdatera hjälpfilerna för en modul i en viss UI-kultur.

1. `Update-Help` hämtar den fjärranslutna HelpInfo XML-filen från den plats som anges av värdet för den **HelpInfoURI** nyckeln i modulmanifestet och validerar filen mot schemat. (Om du vill visa schemat, se [HelpInfo XML-Schema](./helpinfo-xml-schema.md).) Sedan `Update-Help` söker efter en lokal HelpInfo XML-filen för modulen i modulkatalogen på användarens dator.

2. `Update-Help` Jämför det lägre versionsnumret för hjälpfilerna för den angivna kulturen i Användargränssnittet på distans och lokalt HelpInfo XML-filerna för modulen. Om versionsnumret på den fjärranslutna filen är större än versionsnumret på den lokala filen, eller om det finns inga lokala HelpInfo XML-filen för modulen `Update-Help` förbereder för att hämta nya hjälpfiler.

3. `Update-Help` väljer CAB-filen för modulen från den plats som anges av den **HelpContentUri** elementet i den fjärranslutna HelpInfo XML-filen. Den använder Modulnamn, GUID-modulen och kultur för Användargränssnittet för att identifiera CAB-filen.

4. `Update-Help` laddar ned CAB-filen, har packats upp det, verifierar innehållsfilerna hjälp och sparar hjälp innehållsfiler i underkatalogen språkspecifika av modul-katalog på användarens dator.

5. `Update-Help` skapar en lokal HelpInfo XML-fil genom att kopiera den fjärranslutna HelpInfo XML-filen. Det redigerar den lokala HelpInfo XML-filen så att den inkluderar element endast för CAB-filen som det är installerat. Sedan sparar den lokala HelpInfo XML-filen i modulkatalogen och avslutar uppdateringen.

## <a name="the-save-help-process"></a>Save-Help-processen

I följande lista beskrivs åtgärderna för den [Save-Help](/powershell/module/Microsoft.PowerShell.Core/Save-Help) och [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) cmdletar när användaren kör kommandon för att uppdatera hjälpfiler i en filresurs och sedan använda dessa filer för att uppdatera hjälpfilerna på den användarens dator.

Den `Save-Help` cmdlet utför följande åtgärder som svar på ett kommando för att spara hjälpfilerna för en modul i en filresurs som anges av den **DestinationPath** parametern.

1. `Save-Help` hämtar den fjärranslutna HelpInfo XML-filen från den plats som anges av värdet för den **HelpInfoURI** nyckeln i modulmanifestet och validerar filen mot schemat. (Om du vill visa schemat, se [HelpInfo XML-Schema](./helpinfo-xml-schema.md).) Sedan `Save-Help` söker efter en lokal HelpInfo XML-fil i katalogen som anges av den **DestinationPath** parametern i den `Save-Help` kommando.

2. `Save-Help` Jämför det lägre versionsnumret för hjälpfilerna för den angivna kulturen i Användargränssnittet på distans och lokalt HelpInfo XML-filerna för modulen. Om versionsnumret på den fjärranslutna filen är större än versionsnumret på den lokala filen, eller om det finns inga lokala HelpInfo XML-filen för modulen i den **DestinationPath** directory, `Save-Help` förbereder för att hämta nya hjälpfiler.

3. `Save-Help` väljer CAB-filen för modulen från den plats som anges av den **HelpContentUri** elementet i den fjärranslutna HelpInfo XML-filen. Den använder Modulnamn, GUID-modulen och kultur för Användargränssnittet för att identifiera CAB-filen.

4. `Save-Help` hämtar CAB-fil och sparar den i den **DestinationPath** directory. (Det skapas inte någon språkspecifika underkataloger.)

5. `Save-Help` skapar en lokal HelpInfo XML-fil genom att kopiera den fjärranslutna HelpInfo XML-filen. Det redigerar den lokala HelpInfo XML-filen så att den inkluderar element endast för CAB-filen som har sparats. Och sedan sparas lokalt HelpInfo XML-filen i den **DestinationPath** directory och kommer fram till uppdateringen.

   Den `Update-Help` cmdlet utför följande åtgärder som svar på ett kommando för att uppdatera hjälpfilerna på en användares dator från filerna i en filresurs som anges av den **SourcePath** parametern.

1. `Update-Help` hämtar den fjärranslutna HelpInfo XML-filen från den **SourcePath** directory. Den söker sedan efter en lokal HelpInfo XML-fil i modulkatalogen på användarens dator.

2. `Update-Help` Jämför det lägre versionsnumret för hjälpfilerna för den angivna kulturen i Användargränssnittet på distans och lokalt HelpInfo XML-filerna för modulen. Om versionsnumret på den fjärranslutna filen är större än versionsnumret på den lokala filen, eller om det finns inga lokala HelpInfo XML-fil, `Update-Help` förbereder att installera nya hjälpfiler.

3. `Update-Help` väljer CAB-filen för modulen från **SourcePath** directory. Den använder Modulnamn, GUID-modulen och kultur för Användargränssnittet för att identifiera CAB-filen.

4. `Update-Help` har packats upp CAB-filen, verifierar innehållsfilerna hjälp och sparar hjälp innehållsfiler i underkatalogen språkspecifika av modul-katalog på användarens dator.

5. `Update-Help` skapar en lokal HelpInfo XML-fil genom att kopiera den fjärranslutna HelpInfo XML-filen. Det redigerar den lokala HelpInfo XML-filen så att den inkluderar element endast för CAB-filen som det är installerat. Sedan sparar den lokala HelpInfo XML-filen i modulkatalogen och avslutar uppdateringen.