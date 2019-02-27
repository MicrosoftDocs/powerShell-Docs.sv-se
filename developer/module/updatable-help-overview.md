---
title: Översikt över uppdateringsbar hjälp | Microsoft Docs
ms.custom: ''
ms.date: 03/22/2012
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- Windows PowerShell 3.0
ms.assetid: 3f7388a9-9fa8-42bc-b294-538c9a01e30a
caps.latest.revision: 12
ms.openlocfilehash: 4e962890fa1d5c282a02a89f0ae2e263844c635e
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56847490"
---
# <a name="updatable-help-overview"></a>Översikt över uppdateringsbar hjälp

Det här dokumentet innehåller en grundläggande introduktion till design och driften av Windows PowerShell uppdateringsbar hjälp-funktionen. Det är utformat för modulskapare och andra som ger användarna hjälpavsnitt för Windows PowerShell.

## <a name="introduction"></a>Introduktion

Hjälpavsnitt för Windows PowerShell är en del av Windows PowerShell-miljö. Precis som Windows PowerShell-moduler, hjälpavsnitt kontinuerligt uppdateras och förbättrad genom författarna och bidrag i gruppen Användare av Windows PowerShell.

Den *uppdateringsbar hjälp* funktion som introducerades i Windows PowerShell 3.0 ser till att användarna har de senaste versionerna av hjälpavsnitt i Kommandotolken, även för inbyggda Windows PowerShell-kommandon, utan att hämta nya moduler eller som kör Windows Update. Uppdateringsbar hjälp gör uppdaterar enkelt genom att tillhandahålla cmdletar som hämta de senaste versionerna av hjälpavsnitt från Internet och installera dem på rätt underkataloger på användarens lokala dator. Även användare som finns bakom brandväggar kan använda de nya cmdletarna för att få uppdaterade hjälp från en intern filresurs.

Uppdateringsbar hjälp stöds fullt av alla Windows PowerShell-moduler i Windows® 8 och Windows Server® 2012 och dess funktioner är tillgängliga för alla Windows PowerShell-modulen författare. Uppdateringsbar hjälp stöder endast XML-baserade hjälpfiler. Det stöder inte kommentarbaserad hjälp.

Uppdateringsbar hjälp innehåller följande funktioner.

- Den [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) cmdlet, som avgör om användaren har de senaste hjälpfilerna för en modul och, om inte, hämtar de senaste hjälpfilerna från Internet, har packats upp dem och installerar dem i rätt modul underkataloger på den användarens dator. Användare kan använda den [Get-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) cmdlet för att visa de nyligen installerade hjälpavsnitt omedelbart. De behöver inte starta om Windows PowerShell.

- Den [Save-Help](/powershell/module/Microsoft.PowerShell.Core/Save-Help) cmdlet som hämtar de senaste hjälpfilerna filer från Internet och sparar dem i en katalog i filsystemet. Användare kan använda den `Update-Help` cmdlet för att hämta hjälpfiler från systemkatalogen fil och packa upp och installera dem i modulen underkataloger på användarens dator. Den `Save-Help` cmdlet har utformats för användare som har begränsad eller ingen Internetåtkomst och för företag som vill begränsa åtkomst till Internet.

- **Hjälp för en modul**. Hjälpfilerna för en modul hanteras och levereras som en enhet, så att användarna kan få alla hjälpfilerna för de moduler som de använder. Uppdateringsbar hjälp stöds endast för moduler, inte för Windows PowerShell-snapin-moduler.

- **Versionsstöd**. Uppdateringsbar hjälp använder standard fyra position (N1. N2. N3. Versionsnummer för N4). Uppdateringsbar hjälp laddar ned hjälpfiler som när det lägre versionsnumret för hjälp filer på användarens dator (eller i den `Save-Help` directory) är lägre än det lägre versionsnumret för hjälpfiler på Internet-plats.

- **Stöd för flera språk**. Modulen hjälpfiler i flera Användargränssnittet kulturer som har stöd för uppdateringsbar hjälp. Uppdateringsbar hjälp filnamn är standard språkkoder, till exempel ”sv” och ”ja-JP” och `Update-Help` och `Save-Help` cmdletar placera hjälpfilerna i språkspecifika underkataloger i modulkatalogen.

- **Automatiskt genererade hjälp**. Den [Get-Help](/powershell/module/Microsoft.PowerShell.Core/Get-Help) cmdlet visar grundläggande hjälp för kommandon som inte har hjälpfiler. Den automatisk genererade hjälpen innehåller kommandosyntax och alias och anvisningar för att använda direkthjälpen och uppdateringsbar hjälp.

- **Förbättrad onlinehjälp**. Enkel åtkomst till direkthjälpen kräver inte längre hjälpfiler. Den **Online** -parametern för den `Get-Help` cmdlet hämtar nu URL för en onlinehjälpavsnittet från värdet för den **HelpUri** egenskapen för alla kommandon, om den inte finns onlinehjälpen URL: en i en hjälpfilen. Du kan fylla i den **HelpUri** egenskapen genom att lägga till en **HelpUri** attributet koden av cmdlet: ar, funktioner och CIM-kommandon eller genom att använda den **. Länken** kommentarbaserad hjälp direktiv i arbetsflöden och skript.

  För att göra våra hjälpfiler uppdateras, kommer inte Windows PowerShell-moduler i Windows 8 och Windows Server vNext med hjälpfiler. Användare kan använda uppdateringsbar hjälp för att installera hjälpfiler och uppdatera dem. Författare till andra moduler kan inkludera hjälpfiler i moduler eller utelämna dem. Stöd för uppdateringsbar hjälp är valfritt men rekommenderas.
