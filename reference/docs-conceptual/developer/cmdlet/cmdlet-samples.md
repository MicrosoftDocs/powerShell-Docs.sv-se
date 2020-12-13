---
ms.date: 09/13/2016
ms.topic: reference
title: Cmdlet-exempel
description: Cmdlet-exempel
ms.openlocfilehash: 6ee149f611e5af5c45a62363e19e66bf200c0c0a
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/10/2020
ms.locfileid: "92668260"
---
# <a name="cmdlet-samples"></a>Cmdlet-exempel

I det här avsnittet beskrivs exempel kod som finns i Windows PowerShell 2,0 SDK. Du kan kopiera kod från ämnena i det här avsnittet eller öppna de källfiler som installeras med SDK: n. [Windows PowerShell 2,0 Software Development Kit (SDK)](https://www.microsoft.com/download/details.aspx?id=2560) innehåller README-filer, källfiler och Visual Studio-projektfiler för varje exempel. Med SDK installerat kan du hitta exemplen under `<Drive>:\Program Files (x86)\Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\` mappen.

## <a name="in-this-section"></a>I det här avsnittet

[GetProcessSample01-exempel](./getprocesssample01-sample.md) Det här exemplet visar hur du skriver en cmdlet som hämtar processerna på den lokala datorn.

[GetProcessSample02-exempel](./getprocesssample02-sample.md) Det här exemplet visar hur du skriver en cmdlet som hämtar processerna på den lokala datorn. Den innehåller en namn parameter som kan användas för att ange vilka processer som ska hämtas.

[GetProcessSample03-exempel](./getprocesssample03-sample.md) Det här exemplet visar hur du skriver en cmdlet som hämtar processerna på den lokala datorn. Den innehåller en namn parameter som kan acceptera ett objekt från pipelinen eller ett värde från en egenskap hos ett objekt vars egenskaps namn är detsamma som parameter namnet.

[GetProcessSample04-exempel](./getprocesssample04-sample.md) Det här exemplet visar hur du skriver en cmdlet som hämtar processerna på den lokala datorn. Den genererar ett fel som inte avslutas om ett fel inträffar när en process hämtas.

[GetProcessSample05-exempel](./getprocesssample05-sample.md) I det här exemplet visas en fullständig version av Get-Proc-cmdleten.

[StopProcessSample01-exempel](./stopprocesssample01-sample.md) Det här exemplet visar hur du skriver en cmdlet som begär feedback från användaren innan den försöker stoppa en process och hur du implementerar en `PassThru` parameter som anger att cmdleten ska returnera ett objekt.

[StopProcessSample02-exempel](./stopprocesssample02-sample.md) Det här exemplet visar hur du skriver en cmdlet som skriver fel söknings-, utförliga och varnings meddelanden medan processer stoppas på den lokala datorn.

[StopProcessSample03-exempel](./stopprocesssample03-sample.md) Det här exemplet visar hur du skriver en cmdlet vars parametrar har alias och som stöder jokertecken.

[StopProcessSample04-exempel](./stopprocesssample04-sample.md) Det här exemplet visar hur du skriver en cmdlet som deklarerar parameter uppsättningar, anger standard parameter uppsättningen och kan acceptera ett indatamängds objekt.

[Events01-exempel](./events01-sample.md) Det här exemplet visar hur du skapar en-cmdlet som gör att användaren kan registrera sig för händelser som aktive ras av [system. io. FileSystemWatcher](/dotnet/api/System.IO.FileSystemWatcher). Med den här cmdlet-användare kan du till exempel registrera en åtgärd som ska utföras när en fil skapas under en angiven katalog. Det här exemplet härleds från Bask Lassen [Microsoft. PowerShell. commands. Objecteventregistrationbase](/dotnet/api/Microsoft.PowerShell.Commands.ObjectEventRegistrationBase) .

## <a name="see-also"></a>Se även

[Skriva en Windows PowerShell-cmdlet](./writing-a-windows-powershell-cmdlet.md)
