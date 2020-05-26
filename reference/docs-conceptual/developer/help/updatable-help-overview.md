---
title: Uppdaterings bar hjälp översikt | Microsoft Docs
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
ms.openlocfilehash: f2dfb9642ba2dde38124142b659b425bbbb00f37
ms.sourcegitcommit: 2aec310ad0c0b048400cb56f6fa64c1e554c812a
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/23/2020
ms.locfileid: "83810808"
---
# <a name="updatable-help-overview"></a>Översikt över uppdateringsbar hjälp

Det här dokumentet innehåller en grundläggande introduktion till design och drift av den uppdaterings bara hjälp funktionen i Windows PowerShell. Den är utformad för att skapa utvecklare och andra som levererar hjälp avsnitt om Windows PowerShell till användare.

## <a name="introduction"></a>Introduktion

Hjälp avsnitten för Windows PowerShell är en del av Windows PowerShell-upplevelsen. Precis som i Windows PowerShell-moduler uppdateras och förbättras hjälp avsnitten kontinuerligt av författarna och av bidragen från communityn för Windows PowerShell-användare.

Funktionen *uppdaterings bar hjälp* , som introducerades i Windows PowerShell 3,0, ser till att användarna har de senaste versionerna av hjälp avsnitten i kommando tolken, även för inbyggda Windows PowerShell-kommandon, utan att ladda ned nya moduler eller köra Windows Update. Uppdaterings bara hjälp gör uppdatering enkel genom att tillhandahålla cmdletar som laddar ned de senaste versionerna av hjälp avsnitten från Internet och installerar dem i rätt under kataloger på användarens lokala dator. Även om användare som är bakom brand väggar kan använda de nya cmdletarna för att få uppdaterad hjälp från en intern fil resurs.

Uppdaterings bara hjälp stöds fullt ut av alla Windows PowerShell-moduler i Windows® 8 och Windows Server® 2012, och dess funktioner är tillgängliga för alla Windows PowerShell-modulens författare. Uppdaterings bara hjälp stöder endast XML-baserade hjälpfiler. Den stöder inte kommenterings-baserad hjälp.

Uppdaterings bara hjälp innehåller följande funktioner.

- Cmdleten [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) , som avgör om användarna har de senaste hjälpfilerna för en modul och, om inte, laddar ned de senaste hjälpfilerna från Internet, packar upp dem och installerar dem i rätt modul-underkataloger på användarens dator.
  Användare kan använda cmdleten [Get-Help](/powershell/module/Microsoft.PowerShell.Core/Get-Help) för att visa de nyligen installerade hjälp avsnitten direkt.
  De behöver inte starta om PowerShell.

- Cmdleten [Save-Help](/powershell/module/Microsoft.PowerShell.Core/Save-Help) som laddar ned de senaste hjälpfilerna från Internet och sparar dem i en fil system katalog. Användare kan använda `Update-Help` cmdleten för att hämta hjälpfiler från fil system katalogen och packa upp och installera dem i modulens under kataloger på användarens dator. `Save-Help`Cmdleten är avsedd för användare som har begränsad eller ingen Internet åtkomst och för företag som föredrar att begränsa Internet åtkomst.

- **Hjälp för en modul**. Hjälpfiler för en modul hanteras och levereras som en enhet, så att användarna kan få alla hjälpfilerna för de moduler som de använder. Uppdaterings bara hjälp stöds bara för moduler, inte för Windows PowerShell-snapin-moduler.

- **Versions stöd**. Uppdaterings bara hjälp använder fyra positioner (N1). N2. N3. N4) versions nummer. Uppdaterings bara hjälp nedladdnings hjälp filer när versions numret för hjälpfilerna på användarens dator (eller i `Save-Help` katalogen) är lägre än hjälp filens versions nummer på Internet platsen.

- **Stöd för flera språk**. Uppdaterings bara hjälp stöder modulens hjälpfiler i flera UI-kulturer. Uppdaterings bara hjälp fil namn är standard språk koder, till exempel "en-US" och "ja-JP", och `Update-Help` - `Save-Help` cmdletarna placerar hjälpfilerna i språkspecifika under kataloger i modulens katalog.

- **Automatiskt genererad hjälp**. Cmdleten [Get-Help](/powershell/module/Microsoft.PowerShell.Core/Get-Help) visar grundläggande hjälp för kommandon som inte har hjälpfilerna. Den automatiskt genererade hjälpen innehåller kommandosyntaxen och alias och instruktioner för att använda onlinehjälp och uppdaterings bara hjälp.

- **Utökad onlinehjälp**. Enkel åtkomst till direkt hjälpen kräver inte längre hjälp filer. **Online** -parametern för `Get-Help` cmdleten hämtar nu URL: en för ett direkt hjälp avsnitt från värdet för egenskapen **HelpUri** för alla kommandon, om den inte kan hitta URL: en direkt hjälp i en hjälp fil. Du kan fylla i egenskapen **HelpUri** genom att lägga till ett **HelpUri** -attribut till koden för cmdlets, Functions och CIM-kommandon, eller genom att använda **. Länka** till kommenterat hjälp direktiv i arbets flöden och skript.

  För att kunna göra våra hjälpfiler uppdaterings bara, kommer Windows PowerShell-modulerna i Windows 8-och Windows Server-vNext inte att medfölja hjälpfilerna. Användare kan använda uppdaterbar hjälp för att installera hjälpfiler och uppdatera dem. Författare till andra moduler kan inkludera hjälpfiler i moduler eller utelämna dem. Stöd för uppdaterbar hjälp är valfritt, men rekommenderas.
