---
title: Cmdlet-exempel | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b99d53fc-0af9-426b-82ce-09955e031d4b
caps.latest.revision: 13
ms.openlocfilehash: d919d4ad8554e762230c1448d81b50e27c38ba99
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56851970"
---
# <a name="cmdlet-samples"></a>Cmdlet-exempel

Det här avsnittet beskrivs exempelkod som har angetts i Windows PowerShell 2.0 SDK. Du kan kopiera koden från avsnitten i det här avsnittet eller öppna källfilerna som installeras med SDK: N. Den [Windows PowerShell 2.0 Software Development Kit (SDK)](https://www.microsoft.com/en-us/download/details.aspx?id=2560) tillhandahåller ReadMe-filerna, källfiler och Visual Studio projektfiler för varje exempel. Med SDK för installerat kan du hitta exempel under den `<Drive>:\Program Files (x86)\Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\` mapp.

## <a name="in-this-section"></a>I detta avsnitt

[GetProcessSample01 exempel](./getprocesssample01-sample.md) det här exemplet visas hur du skriver en cmdlet som hämtar processer på den lokala datorn.

[GetProcessSample02 exempel](./getprocesssample02-sample.md) det här exemplet visas hur du skriver en cmdlet som hämtar processer på den lokala datorn. Det ger en namnparameter som kan användas för att ange processerna som ska hämtas.

[GetProcessSample03 exempel](./getprocesssample03-sample.md) det här exemplet visas hur du skriver en cmdlet som hämtar processer på den lokala datorn. Det ger en namnparameter som kan ta emot ett objekt från pipelinen eller ett värde från en egenskap för ett objekt vars egenskapsnamnet är samma som parameternamnet.

[GetProcessSample04 exempel](./getprocesssample04-sample.md) det här exemplet visas hur du skriver en cmdlet som hämtar processer på den lokala datorn. Den genererar en oändliga fel om ett fel inträffar vid hämtning av en process.

[GetProcessSample05 exempel](./getprocesssample05-sample.md) detta exempel visar en fullständig version av cmdleten Get-processen.

[StopProcessSample01 exempel](./stopprocesssample01-sample.md) i det här exemplet visar hur du skriver en cmdlet som efterfrågar feedback från användaren innan den försöker stoppa en process och hur du implementerar en `PassThru` parameter som anger att användaren vill cmdleten returnerar en objekt.

[StopProcessSample02 exempel](./stopprocesssample02-sample.md) det här exemplet visas hur du skriver en cmdlet som skriver utförlig, felsökning och varningsmeddelanden när processer på den lokala datorn.

[StopProcessSample03 exempel](./stopprocesssample03-sample.md) det här exemplet visas hur du skriver en cmdlet vars parametrar har alias och som stöd för jokertecken.

[StopProcessSample04 exempel](./stopprocesssample04-sample.md) det här exemplet visas hur du skriver en cmdlet som deklarerar parameteruppsättningar, anger standardparametern anger och kan acceptera en indataobjektet.

[Events01 exempel](./events01-sample.md) i det här exemplet visar hur du skapar en cmdlet som används att registrera dig för händelser som skapats av [System.IO.Filesystemwatcher](/dotnet/api/System.IO.FileSystemWatcher). Med denna cmdlet kan användarna till exempel registrera en åtgärd som ska köras när en fil skapas under en viss katalog. Det här exemplet kommer från den [Microsoft.Powershell.Commands.Objecteventregistrationbase](/dotnet/api/Microsoft.PowerShell.Commands.ObjectEventRegistrationBase) basklassen.

## <a name="see-also"></a>Se även

[Skriva en Windows PowerShell-Cmdlet](./writing-a-windows-powershell-cmdlet.md)
