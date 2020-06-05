---
title: Bilaga A – syntax för hjälp
description: Den här artikeln förklarar hur du läser och förstår syntaxen för en cmdlet som presenteras av Get-Help.
ms.date: 06/02/2020
ms.topic: guide
ms.custom: Contributor-mikefrobbins
ms.reviewer: mirobb
ms.openlocfilehash: e8e28f66c02370b098f63a0396ef8a724cf3a1bd
ms.sourcegitcommit: 0d958eac5bde5ccf5ee2c1bac4f009a63bf71368
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/05/2020
ms.locfileid: "84436304"
---
# <a name="appendix-a---help-syntax"></a>Bilaga A – syntax för hjälp

I följande exempel visas avsnittet **syntax** i hjälpen för `Get-EventLog` cmdleten.

```powershell
help Get-EventLog
```

```Output
NAME
    Get-EventLog

SYNOPSIS
    Gets the events in an event log, or a list of the event logs, on the local or remote
    computers.


SYNTAX
    Get-EventLog [-LogName] <String> [[-InstanceId] <Int64[]>] [-After <DateTime>]
    [-AsBaseObject] [-Before <DateTime>] [-ComputerName <String[]>] [-EntryType {Error |
    Information | FailureAudit | SuccessAudit | Warning}] [-Index <Int32[]>] [-Message
    <String>] [-Newest <Int32>] [-Source <String[]>] [-UserName <String[]>]
    [<CommonParameters>]

    Get-EventLog [-AsString] [-ComputerName <String[]>] [-List] [<CommonParameters>]
```

Endast den relevanta delen av hjälpen visas i det här exemplet.

Syntaxen består i första hand av flera uppsättningar inledande och avslutande hakparenteser ( `[]` ). Dessa har två olika betydelser beroende på hur de används. Allt som ingår i hakparenteser är valfritt, om de inte är en uppsättning tomma hakparenteser `[]` . Tomma hakparenteser visas bara efter en datatyp som `<string[]>` . Det innebär att en viss parameter kan acceptera fler än ett värde av den typen.

Den första parametern i den första parameter uppsättningen i `Get-EventLog` är **LogName**. LogName omges av hakparenteser, vilket innebär att det är en positions parameter. Med andra ord är det valfritt att ange namnet på själva parametern så länge det anges på rätt plats. Informationen inom vinkelparenteser ( `<>` ) efter parameter namnet anger att det behöver ett enskilt **sträng** värde. Hela parameter namnet och data typen omges inte av hakparenteser, så **LogName** -parametern krävs när du använder den här parameter uppsättningen.

```powershell
Get-EventLog [-LogName] <String>
```

Den andra parametern är **InstanceID**. Observera att parameter namnet och data typen är båda helt omgiven av hakparenteser. Det innebär att **InstanceID** -parametern är valfri, inte obligatorisk. Observera också att **InstanceID** omges av en egen uppsättning hakparenteser. Precis som med parametern **LogName** innebär det att parametern är i position. Det finns en sista uppsättning hakparenteser efter data typen. Det innebär att den kan acceptera mer än ett värde i form av en matris eller en kommaavgränsad lista.

```
[[-InstanceId] <Int64[]>]
```

Den andra parameter uppsättningen har en **list** parameter. Det är en växel parameter eftersom det inte finns någon datatype efter parameter namnet. När **list** parametern anges är värdet **True**. Värdet är **false**när det inte anges.

```
[-List]
```

Information om syntaxen för ett kommando kan också hämtas med `Get-Command` hjälp av parametern **syntax** . Det här är en praktisk genväg som jag använder hela tiden. Det gör att du snabbt kan lära dig hur du använder ett kommando utan att behöva gå igenom flera sidor med hjälp information. Om jag behöver mer information återgår jag till att använda det faktiska hjälp innehållet.

```powershell
Get-Command -Name Get-EventLog -Syntax
```

```Output
Get-EventLog [-LogName] <string> [[-InstanceId] <long[]>] [-ComputerName <string[]>] [-Newest <int>]
 [-After <datetime>] [-Before <datetime>] [-UserName <string[]>] [-Index <int[]> ]
 [-EntryType <string[]>] [-Source <string[]>] [-Message <string>] [-AsBaseObject]
 [<CommonParameters>]

Get-EventLog [-ComputerName <string[]>] [-List] [-AsString] [<CommonParameters>]
```

Mer information om hur du använder hjälp systemet i PowerShell blir den enklare att komma ihåg alla de olika olika delarna. Innan du vet det blir det andra natur.
