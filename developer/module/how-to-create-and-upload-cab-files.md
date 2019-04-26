---
title: Så här skapar och överför CAB-filer | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8d35f233-5447-48a2-a961-9fbca763262b
caps.latest.revision: 7
ms.openlocfilehash: 9928a0b31a57d42eb39cea1af0509613c483caf7
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62082387"
---
# <a name="how-to-create-and-upload-cab-files"></a>Skapa och ladda upp CAB-filer

Det här avsnittet beskriver hur du skapar uppdateringsbar hjälp CAB-filer och överför dem till den plats där cmdletarna uppdateringsbar hjälp hittar.

## <a name="how-to-create-and-upload-updatable-help-cab-files"></a>Så här skapar och överför uppdateringsbar hjälp CAB-filer

Du kan använda funktionen uppdateringsbar hjälp för att leverera nya eller uppdaterade hjälpfilerna för en modul i flera språk och kulturer. En uppdateringsbar hjälp-paket för en modul som består av en HelpInfo XML-fil och en eller flera kabinettfil (. CAB-fil) filer. Varje CAB-filen innehåller hjälpfiler för modulen i en UI-kultur. Använd följande procedur för att skapa CAB-filer för uppdateringsbar hjälp.

1. Organisera hjälpfilerna för modulen av UI-kultur. Varje uppdateringsbar hjälp CAB-filen innehåller hjälpfilerna för en modul i en UI-kultur. Du kan leverera flera hjälp CAB-filer för modulen, var och en för en annan UI-kultur.

2. Kontrollera som hjälpfiler omfattar endast de filtyper som tillåts för uppdateringsbar hjälp och validera dem mot ett schema för Hjälp-filen. Om den `Update-Help` cmdlet påträffar en fil som är ogiltig eller är inte en tillåten typ och installerar inte filen ogiltig stoppar installerar filer från rådgivningsnämnden för ändringar. En lista över tillåtna filtyper finns i [filen typer tillåts i en uppdateringsbar hjälp CAB-fil](./file-types-permitted-in-an-updatable-help-cab-file.md).

3. Signera hjälpfilerna. Digitala signaturer krävs inte, men de är bästa praxis.

4. Inkludera all hjälp filer för modulen i Användargränssnittet för kultur, inte bara de filer som är nya eller har ändrats. Om CAB-filen är ofullständig, har användare som hämtar hjälpfiler för första gången eller hämta inte alla uppdateringar inte alla hjälpfiler modulen.

5. Använd ett verktyg som skapar CAB-filer, till exempel MakeCab.exe. Windows PowerShell innehåller inte cmdletar som skapar CAB-filer.

6. Namnge CAB-filer. Mer information finns i [hur du namnger en uppdateringsbar hjälp CAB-fil](./how-to-name-an-updatable-help-cab-file.md).

7. Ladda upp CAB-filer för modulen till den plats som anges av den **HelpContentUri** element i HelpInfo XML-filen för modulen. Överför sedan HelpInfo XML-filen till den plats som anges av den **HelpInfoUri** nyckeln för modulmanifestet. Den **HelpContentUri** och **HelpInfoUri** kan peka på samma plats.

> [!CAUTION]
> Värdet för den **HelpInfoUri** nyckel och **HelpContentUri** elementet måste börja med ”http” eller ”https”. Värdet måste ange en plats på Internet och det får inte innehålla ett filnamn.