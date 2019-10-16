---
title: Körnings utrymme-exempel | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c92a6d3d-8d34-4a76-bdc3-dea923d9858e
caps.latest.revision: 17
ms.openlocfilehash: e24d40746da91f60aaf2af655ddcadc88ab6a4db
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72353118"
---
# <a name="runspace-samples"></a>Exempel på körningsutrymmen

Det här avsnittet innehåller exempel kod som visar hur du använder olika typer av körnings utrymmen för att köra kommandon synkront och asynkront. Du kan använda Microsoft Visual Studio för att skapa ett konsol program och sedan kopiera koden från ämnena i det här avsnittet till värd programmet.

## <a name="in-this-section"></a>I detta avsnitt

> [!NOTE]
> Exempel på värd program som skapar anpassade värd gränssnitt finns i [anpassade värd exempel](./custom-host-samples.md).

 [Runspace01-exempel](./runspace01-sample.md) Det här exemplet visar hur du använder klassen [system. Management. Automation. PowerShell](/dotnet/api/system.management.automation.powershell) för att köra cmdleten [Get-process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) synkront och visa dess utdata i ett konsol fönster.

 [Runspace02-exempel](./runspace02-sample.md) Det här exemplet visar hur du kan använda-cmdlet: arna [Get-process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) och [sort-Object](/powershell/module/Microsoft.PowerShell.Utility/Sort-Object) med hjälp av klassen [system. Management. Automation. PowerShell](/dotnet/api/system.management.automation.powershell) . Resultatet av dessa kommandon visas med hjälp av en [system. Windows. Forms. DataGridView](/dotnet/api/System.Windows.Forms.DataGridView) -kontroll.

 [Runspace03-exempel](./runspace03-sample.md) Det här exemplet visar hur du använder klassen [system. Management. Automation. PowerShell](/dotnet/api/system.management.automation.powershell) för att köra ett skript synkront och hur du hanterar icke-avslutande fel. Skriptet tar emot en lista över process namn och hämtar sedan dessa processer. Resultatet av skriptet, inklusive eventuella icke-avslutande fel som genererades när skriptet kördes, visas i konsol fönstret.

 [Runspace04-exempel](./runspace04-sample.md) Det här exemplet visar hur du använder klassen [system. Management. Automation. PowerShell](/dotnet/api/system.management.automation.powershell) för att köra kommandon och hur du fångar upp avslutande fel som uppstår när du kör kommandona. Två kommandon körs och det sista kommandot skickas till ett parameter argument som inte är giltigt. Som ett resultat returneras inga objekt och ett avslutande fel uppstår.

 [Runspace05-exempel](./runspace05-sample.md) Det här exemplet visar hur du lägger till en snapin-modul i ett [system. Management. Automation. körnings utrymmen. Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) -objekt så att cmdleten för snapin-modulen är tillgänglig när körnings utrymme öppnas. Snapin-modulen innehåller en get-proc-cmdlet (definieras av [GetProcessSample01-exemplet](../cmdlet/getprocesssample01-sample.md)) som körs synkront med ett [system. Management. Automation. PowerShell](/dotnet/api/system.management.automation.powershell) -objekt.

 [Runspace06-exempel](./runspace06-sample.md) Det här exemplet visar hur du lägger till en modul i ett [system. Management. Automation. körnings utrymmen. Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) -objekt så att modulen läses in när körnings utrymme öppnas. Modulen innehåller en get-proc-cmdlet (definieras av [GetProcessSample02-exemplet](../cmdlet/getprocesssample02-sample.md)) som körs synkront med ett [system. Management. Automation. PowerShell](/dotnet/api/system.management.automation.powershell) -objekt.

 [Runspace07-exempel](./runspace07-sample.md) Det här exemplet visar hur du skapar en körnings utrymme och sedan använder den körnings utrymme för att köra två cmdlets synkront med hjälp av ett [system. Management. Automation. PowerShell](/dotnet/api/system.management.automation.powershell) -objekt.

 [Runspace08-exempel](./runspace08-sample.md) Det här exemplet visar hur du lägger till kommandon och argument i pipelinen för ett [system. Management. Automation. PowerShell](/dotnet/api/system.management.automation.powershell) -objekt och hur du kör kommandona synkront.

 [Runspace09-exempel](./runspace09-sample.md) Det här exemplet visar hur du lägger till ett skript i pipelinen för ett [system. Management. Automation. PowerShell](/dotnet/api/system.management.automation.powershell) -objekt och hur du kör skriptet asynkront. Händelser används för att hantera utdata från skriptet.

 [Runspace10-exempel](./runspace10-sample.md) Det här exemplet visar hur du skapar ett standard tillstånd för inledande session, hur du lägger till en cmdlet till [system. Management. Automation. körnings utrymmen. Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState), hur du skapar en körnings utrymme som använder det inledande sessionstillståndet och hur du kör kommandot med hjälp av en Objektet [system. Management. Automation. PowerShell](/dotnet/api/system.management.automation.powershell) .

 [Runspace11-exempel](./runspace11-sample.md) Detta visar hur du använder klassen [system. Management. Automation. ProxyCommand](/dotnet/api/System.Management.Automation.ProxyCommand) för att skapa ett proxy-kommando som anropar en befintlig cmdlet, men begränsar uppsättningen av tillgängliga parametrar. Kommandot proxy läggs sedan till i ett tillstånd för inledande session som används för att skapa en begränsad körnings utrymme. Det innebär att användaren endast kan komma åt funktionaliteten för cmdlet via kommandot proxy.

## <a name="see-also"></a>Se även
