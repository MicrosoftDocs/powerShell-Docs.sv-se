---
ms.date: 03/22/2012
ms.topic: reference
title: Översikt över uppdateringsbar hjälp
description: Översikt över uppdateringsbar hjälp
ms.openlocfilehash: b8008b7c28d94ebaac135934606042e6a6053591
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/10/2020
ms.locfileid: "92649567"
---
# <a name="updatable-help-overview"></a>Översikt över uppdateringsbar hjälp

Det här dokumentet innehåller en grundläggande introduktion till designen och driften av PowerShell-funktionen för uppdaterbar hjälp. Den är utformad för att skapa utvecklare och andra som levererar hjälp avsnitt om Windows PowerShell till användare.

## <a name="introduction"></a>Introduktion

Hjälp avsnitten för PowerShell är en del av PowerShell-upplevelsen. Precis som PowerShell-moduler uppdateras och förbättras hjälp avsnitten kontinuerligt av författarna och bidragen från communityn för PowerShell-användare.

Funktionen *uppdaterings bar hjälp* , som introducerades i Windows PowerShell 3,0, garanterar att användarna har de senaste versionerna av hjälp avsnitten i kommando tolken, även för inbyggda PowerShell-kommandon, utan att hämta nya moduler eller köra Windows Update. Uppdaterings bara hjälp gör uppdatering enkel genom att tillhandahålla cmdletar som laddar ned de senaste versionerna av hjälp avsnitten från Internet och installerar dem i rätt under kataloger på användarens lokala dator. Även om användare som är bakom brand väggar kan använda de nya cmdletarna för att få uppdaterad hjälp från en intern fil resurs.

Uppdaterings bara hjälp stöds fullt ut av alla Windows PowerShell-moduler i Windows 8 och Windows Server 2012, och dess funktioner är tillgängliga för alla Windows PowerShell-moduler. Uppdaterings bara hjälp stöder endast XML-baserade hjälpfiler. Den stöder inte kommenterings-baserad hjälp.

Uppdaterings bara hjälp innehåller följande funktioner.

- Cmdleten [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) , som avgör om användarna har de senaste hjälpfilerna för en modul och, om inte, laddar ned de senaste hjälpfilerna från Internet, packar upp dem och installerar dem i rätt modul-underkataloger på användarens dator. Användare kan använda cmdleten [Get-Help](/powershell/module/Microsoft.PowerShell.Core/Get-Help) för att visa de nyligen installerade hjälp avsnitten direkt. De behöver inte starta om PowerShell.

- Cmdleten [Save-Help](/powershell/module/Microsoft.PowerShell.Core/Save-Help) som laddar ned de senaste hjälpfilerna från Internet och sparar dem i en fil system katalog. Användare kan använda `Update-Help` cmdleten för att hämta hjälpfiler från fil system katalogen och packa upp och installera dem i modulens under kataloger på användarens dator. `Save-Help`Cmdleten är avsedd för användare som har begränsad eller ingen Internet åtkomst och för företag som föredrar att begränsa Internet åtkomst.

- **Hjälp för en modul**. Hjälpfiler för en modul hanteras och levereras som en enhet, så att användarna kan få alla hjälpfilerna för de moduler som de använder. Uppdaterings bara hjälp stöds bara för moduler, inte för Windows PowerShell-snapin-moduler.

- **Versions stöd**. Uppdaterings bara hjälp använder fyra positioner (N1). N2. N3. N4) versions nummer.
  Uppdaterings bara hjälp nedladdnings hjälp filer när versions numret för hjälpfilerna på användarens dator (eller i `Save-Help` katalogen) är lägre än hjälp filens versions nummer på Internet platsen.

- **Stöd för flera språk**. Uppdaterings bara hjälp stöder modulens hjälpfiler i flera UI-kulturer.
  Uppdaterings bara hjälp fil namn är standard språk koder, till exempel "en-US" och "ja-JP", och `Update-Help` - `Save-Help` cmdletarna placerar hjälpfilerna i språkspecifika under kataloger i modulens katalog.

- **Automatiskt genererad hjälp**. Cmdleten [Get-Help](/powershell/module/Microsoft.PowerShell.Core/Get-Help) visar grundläggande hjälp för kommandon som inte har hjälpfilerna. Den automatiskt genererade hjälpen innehåller kommandosyntaxen och alias och instruktioner för att använda onlinehjälp och uppdaterings bara hjälp.

- **Utökad onlinehjälp**. Enkel åtkomst till direkt hjälpen kräver inte längre hjälp filer. **Online** -parametern för `Get-Help` cmdleten hämtar nu URL: en för ett direkt hjälp avsnitt från värdet för egenskapen **HelpUri** för alla kommandon, om den inte kan hitta URL: en direkt hjälp i en hjälp fil. Du kan fylla i egenskapen **HelpUri** genom att lägga till ett **HelpUri** -attribut till koden för cmdlets, Functions och CIM-kommandon, eller genom att använda **. Länka** till kommenterat hjälp direktiv i arbets flöden och skript.

  För att kunna göra våra hjälpfiler uppdaterings bara, kommer Windows PowerShell-modulerna i Windows 8-och Windows Server-vNext inte att medfölja hjälpfilerna. Användare kan använda uppdaterbar hjälp för att installera hjälpfiler och uppdatera dem. Författare till andra moduler kan inkludera hjälpfiler i moduler eller utelämna dem. Stöd för uppdaterbar hjälp är valfritt, men rekommenderas.
