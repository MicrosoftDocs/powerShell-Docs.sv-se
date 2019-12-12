---
title: Så här fungerar uppdaterings bar hjälp | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7674636e-a0f2-4587-bfc5-dd3e6ce5489e
caps.latest.revision: 6
ms.openlocfilehash: 5b6ae54ee6c843996c875189b6ee553be5e4f614
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72357381"
---
# <a name="how-updatable-help-works"></a>Så här fungerar uppdateringsbar hjälp

I det här avsnittet beskrivs hur uppdaterings bara hjälp bearbetar XML-HelpInfo och CAB-filer för varje modul, och installerar uppdaterad hjälp för användare.

## <a name="the-update-help-process"></a>Processen uppdatering – hjälp

I följande lista beskrivs åtgärderna i cmdleten [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) när en användare kör ett kommando för att uppdatera hjälpfilerna för en modul i en viss användar gränssnitts kultur.

1. `Update-Help` hämtar XML-filen för fjärrHelpInfo från den plats som anges av värdet för **HelpInfoURI** -nyckeln i manifestet för modulen och validerar filen mot schemat. (Om du vill visa schemat, se [HelpInfo XML-schema](./helpinfo-xml-schema.md).) Sedan `Update-Help` söker efter en lokal XML-HelpInfo för modulen i modul-katalogen på användarens dator.

2. `Update-Help` jämför versions numret för hjälpfilerna för den angivna användar gränssnitts kulturen i XML-filerna för fjärrdatabasen och den lokala HelpInfo för modulen. Om versions numret på fjärrfilen är större än versions numret för den lokala filen, eller om det inte finns någon lokal XML-HelpInfo för modulen, `Update-Help` förbereder att ladda ned nya hjälpfiler.

3. `Update-Help` väljer CAB-filen för modulen från den plats som anges av **HelpContentUri** -elementet i HelpInfo XML-filen. Den använder modulnamnet, modulens GUID och användar gränssnitts kulturen för att identifiera CAB-filen.

4. `Update-Help` laddar ned CAB-filen, packar upp den, verifierar hjälpfilerna och sparar hjälpfilerna i den språkspecifika under katalogen i modulens katalog på användarens dator.

5. `Update-Help` skapar en lokal HelpInfo XML-fil genom att kopiera HelpInfo XML-filen. Den redigerar den lokala XML-HelpInfo så att den bara innehåller element för den CAB-fil som den är installerad på. Sedan sparas den lokala HelpInfo XML-filen i modulens katalog och uppdateringen avslutas.

## <a name="the-save-help-process"></a>Processen Spara – hjälp

I följande lista beskrivs åtgärderna i cmdletarna [Save-Help](/powershell/module/Microsoft.PowerShell.Core/Save-Help) och [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) när en användare kör kommandon för att uppdatera hjälpfilerna i en fil resurs och sedan använda filerna för att uppdatera hjälpfilerna på användarens dator.

`Save-Help` cmdlet utför följande åtgärder som svar på ett kommando för att spara hjälpfilerna för en modul i en fil resurs som anges av parametern **DestinationPath** .

1. `Save-Help` hämtar XML-filen för fjärrHelpInfo från den plats som anges av värdet för **HelpInfoURI** -nyckeln i manifestet för modulen och validerar filen mot schemat. (Om du vill visa schemat, se [HelpInfo XML-schema](./helpinfo-xml-schema.md).) `Save-Help` söker sedan efter en lokal HelpInfo XML-fil i katalogen som anges av parametern **DestinationPath** i kommandot `Save-Help`.

2. `Save-Help` jämför versions numret för hjälpfilerna för den angivna användar gränssnitts kulturen i XML-filerna för fjärrdatabasen och den lokala HelpInfo för modulen. Om versions numret på fjärrfilen är större än versions numret för den lokala filen, eller om det inte finns någon lokal XML-HelpInfo för modulen i katalogen **DestinationPath** , `Save-Help` förbereder för att ladda ned nya hjälpfiler.

3. `Save-Help` väljer CAB-filen för modulen från den plats som anges av **HelpContentUri** -elementet i HelpInfo XML-filen. Den använder modulnamnet, modulens GUID och användar gränssnitts kulturen för att identifiera CAB-filen.

4. `Save-Help` laddar ned CAB-filen och sparar den i **DestinationPath** -katalogen. (Det skapar inga språkspecifika under kataloger.)

5. `Save-Help` skapar en lokal HelpInfo XML-fil genom att kopiera HelpInfo XML-filen. Den redigerar den lokala HelpInfo XML-filen så att den bara innehåller element för den CAB-fil som den sparade. Sedan sparas den lokala HelpInfo XML-filen i katalogen **DestinationPath** och uppdateringen avslutas.

   `Update-Help` cmdlet utför följande åtgärder som svar på ett kommando för att uppdatera hjälpfilerna på en användares dator från filerna i en fil resurs som anges av parametern **SourcePath** .

1. `Update-Help` hämtar XML-filen med fjärrHelpInfo från **SourcePath** -katalogen. Sedan söker det efter en lokal HelpInfo XML-fil i modul-katalogen på användarens dator.

2. `Update-Help` jämför versions numret för hjälpfilerna för den angivna användar gränssnitts kulturen i XML-filerna för fjärrdatabasen och den lokala HelpInfo för modulen. Om versions numret på fjärrfilen är större än versions numret för den lokala filen, eller om det inte finns någon lokal XML-HelpInfo i XML-filen, `Update-Help` förbereder installationen av nya hjälpfiler.

3. `Update-Help` väljer CAB-filen för modulen från katalogen **SourcePath** . Den använder modulnamnet, modulens GUID och användar gränssnitts kulturen för att identifiera CAB-filen.

4. `Update-Help` packar upp CAB-filen, verifierar hjälpfilerna och sparar hjälpfilerna i den språkspecifika under katalogen i modulens katalog på användarens dator.

5. `Update-Help` skapar en lokal HelpInfo XML-fil genom att kopiera HelpInfo XML-filen. Den redigerar den lokala XML-HelpInfo så att den bara innehåller element för den CAB-fil som den är installerad på. Sedan sparas den lokala HelpInfo XML-filen i modulens katalog och uppdateringen avslutas.