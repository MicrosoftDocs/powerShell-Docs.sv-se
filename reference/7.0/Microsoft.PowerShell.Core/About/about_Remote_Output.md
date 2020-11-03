---
description: Beskriver hur du tolkar och formaterar utdata från fjärrkommandon.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 12/01/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_remote_output?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Remote_Output
ms.openlocfilehash: 4d298b945a9b6d45b26a76b3788d2a49b7d2a107
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/13/2020
ms.locfileid: "93272343"
---
# <a name="about-remote-output"></a>Om fjärrutdata

## <a name="short-description"></a>KORT BESKRIVNING
Beskriver hur du tolkar och formaterar utdata från fjärrkommandon.

## <a name="long-description"></a>LÅNG BESKRIVNING

Utdata från ett kommando som kördes på en fjärran sluten dator kan se ut som utdata av samma kommando körning på en lokal dator, men det finns några viktiga skillnader.

I det här avsnittet beskrivs hur du tolkar, formaterar och visar utdata från kommandon som körs på fjärrdatorer.

## <a name="displaying-the-computer-name"></a>VISAR DATOR NAMNET

När du använder Invoke-Command-cmdlet: en för att köra ett kommando på en fjärrdator, returnerar kommandot ett objekt som innehåller namnet på datorn som genererade data. Fjärrdatorns namn lagras i egenskapen PSComputerName.

För många kommandon visas PSComputerName som standard. Följande kommando kör till exempel ett Get-Culture-kommando på två fjärrdatorer, Server01 och Server02. Utdata, som visas nedan, innehåller namnen på de fjärranslutna datorer där kommandot kördes.

```powershell
C:\PS> invoke-command -script {get-culture} -comp Server01, Server02

LCID  Name    DisplayName                PSComputerName
----  ----    -----------                --------------
1033  en-US   English (United States)    Server01
1033  es-AR   Spanish (Argentina)        Server02
```

Du kan använda parametern HideComputerName för Invoke-Command för att dölja egenskapen PSComputerName. Den här parametern är utformad för kommandon som endast samlar in data från en fjärrdator.

Följande kommando kör ett Get-Culture-kommando på den fjärranslutna Server01-datorn. Parametern HideComputerName används för att dölja egenskapen PSComputerName och relaterade egenskaper.

```powershell
C:\PS> invoke-command -scr {get-culture} -comp Server01 -HideComputerName

LCID             Name             DisplayName
----             ----             -----------
1033             en-US            English (United States)
```

Du kan också visa egenskapen PSComputerName om den inte visas som standard.

Följande kommandon använder exempelvis cmdleten Format-Table för att lägga till egenskapen PSComputerName till utdata från en fjärr Get-Date kommando.

```powershell
$dates = invoke-command -script {get-date} -computername Server01, Server02
$dates | format-table DateTime, PSComputerName -auto

DateTime                            PSComputerName
--------                            --------------
Monday, July 21, 2008 7:16:58 PM    Server01
Monday, July 21, 2008 7:16:58 PM    Server02
```

## <a name="displaying-the-machinename-property"></a>VISA EGENSKAPEN MACHINENAME

Flera cmdlets, inklusive get-process, get-service och get-EventLog, har en ComputerName-parameter som hämtar objekten på en fjärrdator.
Dessa cmdletar använder inte PowerShell-fjärrkommunikation, så du kan använda dem även på datorer som inte har kon figurer ATS för fjärr kommunikation i Windows PowerShell.

Objekten som dessa cmdletar returnerar lagrar namnet på fjärrdatorn i egenskapen MachineName. (Dessa objekt har ingen PSComputerName-egenskap.)

Detta kommando hämtar till exempel PowerShell-processen på fjärrdatorerna Server01 och Server02. Standard visningen inkluderar inte egenskapen MachineName.

```powershell
C:\PS> get-process PowerShell -computername server01, server02

Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
920      38    97524     114504   575     9.66   2648 PowerShell
194       6    24256      32384   142            3020 PowerShell
352      27    63472      63520   577     3.84   4796 PowerShell
```

Du kan använda Format-Table-cmdlet: en för att visa egenskapen MachineName för process objekt.

Följande kommando sparar till exempel processerna i variabeln $p och använder sedan en pipeline-operator (|) för att skicka processerna i $p till Format-Table kommandot. Kommandot använder egenskaps parametern för Format-Table för att inkludera egenskapen MachineName i visningen.

```powershell
C:\PS> $p = get-process PowerShell -comp Server01, Server02
C:\PS> $P | format-table -property ID, ProcessName, MachineName -auto

Id ProcessName MachineName
-- ----------- -----------
2648 PowerShell  Server02
3020 PowerShell  Server01
4796 PowerShell  Server02
```

Följande mer komplexa kommando lägger till egenskapen MachineName till standard process visningen. Den använder hash-tabeller för att ange beräknade egenskaper. Lyckligt vis behöver du inte förstå den för att använda den.

(Observera att bakticket ['] är det fortsättnings tecknen.)

```powershell
C:\PS> $p = get-process PowerShell -comp Server01, Server02

C:\PS> $p | format-table -property Handles, `
@{Label="NPM(K)";Expression={int}}, `
@{Label="PM(K)";Expression={int}}, `
@{Label="WS(K)";Expression={int}}, `
@{Label="VM(M)";Expression={int}}, `
@{Label="CPU(s)";Expression={if ($.CPU -ne $()){ $.CPU.ToString("N")}}}, `
Id, ProcessName, MachineName -auto

Handles NPM(K) PM(K)  WS(K) VM(M) CPU(s)   Id ProcessName MachineName
------- ------ -----  ----- ----- ------   -- ----------- -----------
920     38 97560 114532   576        2648 PowerShell  Server02
192      6 24132  32028   140        3020 PowerShell  Server01
438     26 48436  59132   565        4796 PowerShell  Server02

```

## <a name="deserialized-objects"></a>AVSERIALISERADE OBJEKT

När du kör fjärrkommandon som genererar utdata skickas kommandots utdata över nätverket tillbaka till den lokala datorn.

Eftersom de flesta aktiva Microsoft .NET Ramverks objekt (till exempel objekt som PowerShell-cmdlet returnerar) inte kan överföras via nätverket, är de aktiva objekten "serialiserade". Med andra ord konverteras aktiva objekt till XML-representationer av objektet och dess egenskaper. Sedan överförs det XML-baserade serialiserade objektet över nätverket.

På den lokala datorn tar PowerShell emot det XML-baserade serialiserade objektet och Avserialiserar det genom att konvertera det XML-baserade objektet till ett standard .NET Framework-objekt.

Det avserialiserade objektet är dock inte ett aktivt objekt. Det är en ögonblicks bild av objektet vid den tidpunkt då den serialiserades och innehåller egenskaper men inga metoder. Du kan använda och hantera dessa objekt i PowerShell, inklusive skicka dem i pipeliner, Visa valda egenskaper och formatera dem.

De flesta avserialiserade objekt formateras automatiskt för visning efter poster i XML-Types.ps1XML eller Format.ps1XML-filer. Den lokala datorn kanske inte har filer som har formaterats för alla avserialiserade objekt som genererades på en fjärran sluten dator. När objekt inte är formaterade visas alla egenskaper för varje objekt i-konsolen i en strömmande lista.

När objekt inte formateras automatiskt kan du använda cmdletarna för formatering, till exempel Format-Table eller format-lista, för att formatera och Visa valda egenskaper. Du kan också använda Out-GridView-cmdleten för att visa objekten i en tabell.

Om du kör ett kommando på en fjärrdator som använder cmdletar som du inte har på din lokala dator, kan det hända att de objekt som kommandot returnerar inte är korrekt formaterade eftersom du inte har formateringsattribut för dessa objekt på din dator. Om du vill hämta formatering av data från en annan dator använder du Get-FormatData och Export-FormatData-cmdletar.

Vissa objekt typer, till exempel DirectoryInfo-objekt och GUID, konverteras tillbaka till aktiva objekt när de tas emot. Dessa objekt behöver inte någon särskild hantering eller formatering.

## <a name="ordering-the-results"></a>SORTERA RESULTATEN

Ordningen på dator namnen i parametern ComputerName i cmdlets bestämmer i vilken ordning PowerShell ansluter till fjärrdatorerna. Resultaten visas dock i den ordning som den lokala datorn får dem, vilket kan vara en annan ordning.

Om du vill ändra ordningen på resultaten använder du Sort-Object-cmdleten. Du kan sortera på egenskapen PSComputerName eller MachineName. Du kan också sortera efter en annan egenskap i objektet så att resultatet från olika datorer läggs till i gruppen.

## <a name="see-also"></a>SE ÄVEN

[about_Remote](about_Remote.md)

[about_Remote_Variables](about_Remote_Variables.md)

[Format-Table](xref:Microsoft.PowerShell.Utility.Format-Table)

[Hämta process](xref:Microsoft.PowerShell.Management.Get-Process)

[Get-Service](xref:Microsoft.PowerShell.Management.Get-Service)

[Invoke-kommando](xref:Microsoft.PowerShell.Core.Invoke-Command)

[Select-Object](xref:Microsoft.PowerShell.Utility.Select-Object)
