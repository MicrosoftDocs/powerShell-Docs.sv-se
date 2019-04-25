---
title: Körningsutrymme-exempel | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c92a6d3d-8d34-4a76-bdc3-dea923d9858e
caps.latest.revision: 17
ms.openlocfilehash: e24d40746da91f60aaf2af655ddcadc88ab6a4db
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62082744"
---
# <a name="runspace-samples"></a>Exempel på körningsutrymmen

Det här avsnittet innehåller exempelkod som visar hur du använder olika typer av körningsutrymmen för att köra kommandon synkront och asynkront. Du kan använda Microsoft Visual Studio för att skapa ett konsolprogram och sedan kopiera koden från avsnitten i det här avsnittet i din värdapp.

## <a name="in-this-section"></a>I detta avsnitt

> [!NOTE]
> Exempel på värdar för program som skapar anpassade värden gränssnitt finns [anpassade Host-exempel](./custom-host-samples.md).

 [Runspace01 exempel](./runspace01-sample.md) i det här exemplet visar hur du använder den [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) klassen för att köra den [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet synkront och visa dess utdata i en konsol fönstret.

 [Runspace02 exempel](./runspace02-sample.md) i det här exemplet visar hur du använder den [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) klassen för att köra den [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) och [Sort-Object](/powershell/module/Microsoft.PowerShell.Utility/Sort-Object) cmdlet: ar synkront. Resultatet av dessa kommandon visas med hjälp av en [System.Windows.Forms.Datagridview](/dotnet/api/System.Windows.Forms.DataGridView) kontroll.

 [Runspace03 exempel](./runspace03-sample.md) i det här exemplet visar hur du använder den [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) klassen för att köra ett skript synkront och hur du hanterar icke-avslutande fel. Skriptet tar emot en lista över processnamn och hämtar sedan dessa processer. Resultatet av skriptet, inklusive eventuella icke-avslutande fel som genererades när du kör skriptet, visas i ett konsolfönster.

 [Runspace04 exempel](./runspace04-sample.md) i det här exemplet visar hur du använder den [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) klassen för att köra kommandon, och hur du catch avslutande fel som kan uppkomma när du kör kommandona. Två kommandon körs och det sista kommandot skickas ett argument för parametern som inte är giltig. Därför inga objekt returneras och ett avslutande fel genereras.

 [Runspace05 exempel](./runspace05-sample.md) det här exemplet visas hur du lägger till en snapin-modul till en [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) objektet så att cmdleten av snapin-modulen är tillgänglig när körningsutrymmet öppnas. Snapin-modulen innehåller en cmdlet Get-processen (definieras av den [GetProcessSample01 exempel](../cmdlet/getprocesssample01-sample.md)) som körs synkront med en [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) objekt.

 [Runspace06 exempel](./runspace06-sample.md) det här exemplet visas hur du lägger till en modul till en [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) objektet så att modulen läses in när körningsutrymmet öppnas. Modulen innehåller en cmdlet Get-processen (definieras av den [GetProcessSample02 exempel](../cmdlet/getprocesssample02-sample.md)) som körs synkront med en [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) objekt.

 [Runspace07 exempel](./runspace07-sample.md) det här exemplet visas hur du skapar ett körningsutrymme och sedan använda den körningsutrymme för körning synkront två cmdlet: ar med hjälp av en [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) objekt.

 [Runspace08 exempel](./runspace08-sample.md) det här exemplet visas hur du lägger till och argument till pipelinen för en [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) objekt och hur du kör kommandona synkront.

 [Runspace09 exempel](./runspace09-sample.md) det här exemplet visas hur du lägger till ett skript till pipelinen för en [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) objekt och hur du kör skriptet asynkront. Händelser används för att hantera utdata från skriptet.

 [Runspace10 exempel](./runspace10-sample.md) i det här exemplet visar hur du skapar en standard inledande sessionstillstånd, hur du lägger till en cmdlet för att den [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState), hur du skapar ett körningsutrymme som använder den inledande sessionstillstånd och hur du kör kommandot med hjälp av en [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) objekt.

 [Runspace11 exempel](./runspace11-sample.md) detta visar hur du använder den [System.Management.Automation.Proxycommand](/dotnet/api/System.Management.Automation.ProxyCommand) klassen för att skapa en proxy-kommando som anropar en befintlig cmdlet, men begränsar uppsättningen av tillgängliga parametrar. Kommandot proxy läggs sedan till en inledande sessionstillstånd som används för att skapa ett begränsat körningsutrymme. Det innebär att användaren har åtkomst till funktionerna i cmdlet: en endast via kommandot proxy.

## <a name="see-also"></a>Se även
