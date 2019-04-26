---
title: Windows PowerShell-sessionstillstånd | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Cmdlets [PowerShell], session state
- session state [PowerShell]
ms.assetid: 74912940-2b10-4a76-b174-6d035d71c02b
caps.latest.revision: 8
ms.openlocfilehash: fa207130bbb120750780bb0aa9b32150a32daaa2
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066982"
---
# <a name="windows-powershell-session-state"></a>Windows PowerShell-sessionstillstånd

Sessionstillstånd refererar till den aktuella konfigurationen för en Windows PowerShell-session eller modulen. En Windows PowerShell-session är den driftsmiljö som ska användas interaktivt av kommandoradsverktyget användaren eller via programmering med ett program. Sessionstillstånd för en session kallas för det globala sessionstillståndet.

En Windows PowerShell-session avser tiden mellan när en värdapp öppnas en Windows PowerShell-körningsutrymme och när den stängs körningsutrymmet från en utvecklares perspektiv. Sessionen är har tittat på ett annat sätt, livslängden för en instans av Windows PowerShell-motorn som anropas när körningsutrymmet finns.

## <a name="module-session-state"></a>Modulen sessionstillstånd

Modulen sessionstillstånd skapas när modulen eller något av dess kapslade moduler importeras till sessionen. När en modul exporterar ett element, till exempel en cmdlet, en funktion eller ett skript, läggs en referens till det elementet till det globala sessionstillståndet sessionen. När elementet körs, är det köras inom sessionstillstånd i modulen.

## <a name="session-state-data"></a>Sessionslägesdata

Sessionstillståndet anger data kan vara offentliga eller privata. Offentliga data är tillgängliga för anrop från utanför sessionstillståndet medan privata data är endast tillgängligt för inifrån sessionens tillstånd. En modul kan till exempel ha en privat-funktion som kan anropas endast av modulen eller endast internt av en offentlig elementet som har exporterats. Detta liknar de privata och offentliga medlemmarna av en .NET Framework-typen.

Sessionstillståndsdata lagras av den aktuella instansen av motorn för körning inom ramen för den aktuella Windows PowerShell-sessionen. Sessionslägesdata består av följande objekt:

- Information om sökvägen

- Enhetsinformationen

- Information om Windows PowerShell-provider

- Information om de importerade moduler och referenser till modulen elementen (till exempel-cmdlet: ar, funktioner och skript) som exporteras av modulen. Den här informationen och dessa referenser är för endast globala sessionens tillstånd.

- Sessionstillstånd Variabelinformation

## <a name="accessing-session-state-data-within-cmdlets"></a>Åtkomst till sessionslägesdata lagras i cmdlet: ar

Cmdlet: ar kan få åtkomst till sessionslägesdata lagras antingen indirekt, via den [System.Management.Automation.PSCmdlet.Sessionstate*](/dotnet/api/System.Management.Automation.PSCmdlet.SessionState) egenskap i klassen cmdlet eller direkt via den [ System.Management.Automation.Sessionstate](/dotnet/api/System.Management.Automation.SessionState) klass. Den [System.Management.Automation.Sessionstate](/dotnet/api/System.Management.Automation.SessionState) klassen innehåller egenskaper som kan användas för att undersöka olika typer av sessionstillståndsdata.

## <a name="see-also"></a>Se även

[System.Management.Automation.PSCmdlet.Sessionstate](/dotnet/api/System.Management.Automation.PSCmdlet.SessionState)

[System.Management.Automation.Sessionstate?Displayproperty=Fullname](/dotnet/api/System.Management.Automation.SessionState)

[Windows PowerShell-Cmdlets](./cmdlet-overview.md)

[Skriva en Windows PowerShell-Cmdlet](./writing-a-windows-powershell-cmdlet.md)

[Windows PowerShell Shell SDK](../windows-powershell-reference.md)
