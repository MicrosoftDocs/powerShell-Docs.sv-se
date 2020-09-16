---
title: Sessionstillstånd för Windows PowerShell | Microsoft Docs
ms.date: 09/13/2016
helpviewer_keywords:
- Cmdlets [PowerShell], session state
- session state [PowerShell]
ms.openlocfilehash: 7436e3ebd0e099ead81f9fea01a0a2994b982213
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/05/2020
ms.locfileid: "87783950"
---
# <a name="windows-powershell-session-state"></a>Windows PowerShell-sessionstillstånd

Sessionstillstånd refererar till den aktuella konfigurationen av en Windows PowerShell-session eller-modul. En Windows PowerShell-session är den drifts miljö som används interaktivt av kommando rads användaren eller program mässigt av ett värd program. Sessionens tillstånd för en session kallas för det globala sessionstillståndet.

Från ett utvecklings perspektiv refererar en Windows PowerShell-session till tiden mellan när ett värd program öppnar en Windows PowerShell-körnings utrymme och när körnings utrymme stängs. På ett annat sätt är sessionen livs längden för en instans av Windows PowerShell-motorn som anropas medan körnings utrymme finns.

## <a name="module-session-state"></a>Sessionstillstånd för modul

Sessionstillstånd för modulen skapas när modulen eller en av dess kapslade moduler importeras till sessionen. När en modul exporterar ett element, till exempel en cmdlet, en funktion eller ett skript, läggs en referens till det elementet till i sessionens globala sessionstillstånd. Men när elementet körs körs det inom modulens sessionstillstånd.

## <a name="session-state-data"></a>Data för sessionstillstånd

Session State-data kan vara offentliga eller privata. Offentliga data är tillgängliga för anrop från utanför sessionstillståndet, medan privata data bara är tillgängliga för anrop inifrån sessionstillståndet. En modul kan till exempel ha en privat funktion som bara kan anropas av modulen eller bara internt av ett offentligt element som har exporter ATS. Detta liknar privata och offentliga medlemmar av en .NET Framework typ.

Data för sessionstillstånd lagras av den aktuella instansen av körnings motorn inom kontexten för den aktuella Windows PowerShell-sessionen. Data för sessionstillstånd består av följande objekt:

- Sök vägs information

- Enhets information

- Information om Windows PowerShell-Provider

- Information om importerade moduler och referenser till modulens element (till exempel cmdlets, Functions och scripts) som exporteras av modulen. Den här informationen och dessa referenser gäller endast för det globala sessionstillståndet.

- Variabel information för sessionstillstånd

## <a name="accessing-session-state-data-within-cmdlets"></a>Åtkomst till sessionens tillstånds data inom cmdletar

-Cmdletar har åtkomst till sessionstillstånd antingen indirekt via egenskapen [system. Management. Automation. PSCmdlet. sessionState *](/dotnet/api/System.Management.Automation.PSCmdlet.SessionState) för cmdlet-klassen eller direkt via klassen [system. Management. Automation. sessionState](/dotnet/api/System.Management.Automation.SessionState) . Klassen [system. Management. Automation. sessionState](/dotnet/api/System.Management.Automation.SessionState) innehåller egenskaper som kan användas för att undersöka olika typer av sessionstillstånd.

## <a name="see-also"></a>Se även

[System. Management. Automation. PSCmdlet. sessionState](/dotnet/api/System.Management.Automation.PSCmdlet.SessionState)

[System. Management. Automation. sessionState? Displayproperty = FullName](/dotnet/api/System.Management.Automation.SessionState)

[Windows PowerShell-cmdletar](./cmdlet-overview.md)

[Skriva en Windows PowerShell-cmdlet](./writing-a-windows-powershell-cmdlet.md)

[Windows PowerShell Shell SDK](../windows-powershell-reference.md)
