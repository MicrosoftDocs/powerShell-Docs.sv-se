---
description: Beskriver ett **CimSession** -objekt och skillnaden mellan CIM-sessioner och PowerShell-sessioner.
Locale: en-US
ms.date: 05/13/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_cimsession?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_CimSession
ms.openlocfilehash: 556c3db21ea5e410b28f5546cdd8a433e0bc3e50
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94710675"
---
# <a name="about-cimsession"></a>Om CimSession

## <a name="short-description"></a>Kort beskrivning
Beskriver ett **CimSession** -objekt och skillnaden mellan CIM-sessioner och PowerShell-sessioner.

## <a name="long-description"></a>Lång beskrivning

En Common Information Model-session (CIM) är ett objekt på klient sidan som representerar en anslutning till en lokal dator eller en fjärran sluten dator. Du kan använda CIM-sessioner som ett alternativ till PowerShell-sessioner (PSSessions). Båda metoderna har fördelar.

Du kan använda `New-CimSession` cmdleten för att skapa en CIM-session som innehåller information om en anslutning, till exempel dator namn, det protokoll som används för anslutningen, sessions-ID och instans-ID.

När du har skapat ett **CimSession** -objekt som anger information som krävs för att upprätta en anslutning upprättas inte anslutningen direkt av PowerShell. När en cmdlet använder CIM-sessionen ansluter PowerShell till den angivna datorn och sedan avslutar PowerShell anslutningen när cmdleten har slutförts.

Om du skapar en **PSSession** i stället för att använda en CIM-session, verifierar PowerShell anslutnings inställningarna och upprättar och underhåller sedan anslutningen. Om du använder CIM-sessioner öppnar inte PowerShell en nätverks anslutning förrän det behövs. Mer information om PowerShell-sessioner finns [about_PSSessions](about_PSSessions.md).

## <a name="when-to-use-a-cim-session"></a>När du ska använda en CIM-session

Endast cmdletar som fungerar med en Windows Management Instrumentation (WMI)-provider eller CIM-WS-Man accepterar CIM-sessioner. Använd **PSSessions** för andra cmdletar.

När du använder en CIM-session kör PowerShell cmdleten på den lokala klienten. Den ansluter till WMI-providern med hjälp av CIM-sessionen. Mål datorn kräver inte PowerShell eller ens någon version av Windows-operativsystemet.

En cmdlet kan däremot köras med hjälp av en **PSSession** som körs på mål datorn.
Det kräver PowerShell på mål systemet. Dessutom skickar cmdleten data tillbaka till den lokala datorn. PowerShell hanterar de data som skickas via anslutningen och behåller storleken inom de gränser som anges av Windows Remote Management (WinRM). CIM-sessioner tillämpar inte WinRM-gränser.

## <a name="using-cdxml-cmdlets"></a>Använda CDXLM-cmdletar

CIM-baserade cmdlet definition XML (CDXLM)-cmdletar kan skrivas för att använda WMI-providern. Alla WMI-providers använder **CimSession** -objekt. Mer information om CDXLM finns i [definition och villkor för cdxlm](/previous-versions/windows/desktop/wmi_v2/cdxml-overview).

CDXLM-cmdletar har en automatisk **CimSession** -parameter som kan ta en matris med **CimSession** -objekt. Som standard begränsar PowerShell antalet samtidiga CIM-anslutningar till 15. Den här gränsen kan åsidosättas av CDXLM-cmdletar som implementerar **ThrottleLimit**. Se den individuella cmdlet-dokumentationen för att förstå **ThrottleLimit**.

## <a name="see-also"></a>SE ÄVEN

[New-CimSession](xref:CimCmdlets.New-CimSession)

[about_PSSessions](about_PSSessions.md)

