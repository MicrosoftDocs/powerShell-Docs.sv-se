---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 11/12/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/get-error?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Error
ms.openlocfilehash: 1a8e278e03d8aea4129c172d786d285d6b55b083
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93263480"
---
# Get-Error

## SAMMANFATTNING

Hämtar och visar de senaste fel meddelandena från den aktuella sessionen.

## SYNTAX

### Nyaste (standard)

```
Get-Error [[-Newest] <Int32>] [<CommonParameters>]
```

### Fel

```
Get-Error [-InputObject <PSObject>] [<CommonParameters>]
```

## BESKRIVNING

`Get-Error`Cmdleten hämtar ett **PSExtendedError** -objekt som representerar den aktuella fel informationen från det senaste felet som inträffade i sessionen.

Du kan använda `Get-Error` för att visa ett angivet antal fel som har inträffat i den aktuella sessionen med den **senaste** parametern.

`Get-Error`Cmdleten tar även emot fel objekt från en samling, till exempel `$Error` för att visa flera fel från den aktuella sessionen.

## EXEMPEL

### Exempel 1: hämta den senaste fel informationen

I det här exemplet `Get-Error` visas information om de senaste fel som inträffat i den aktuella sessionen.

```powershell
Get-Childitem -path /NoRealDirectory
Get-Error
```

```
Get-ChildItem: Cannot find path 'C:\NoRealDirectory' because it does not exist.

Exception             :
    ErrorRecord          :
        Exception             :
            Message : Cannot find path 'C:\NoRealDirectory' because it does not exist.
            HResult : -2146233087
        TargetObject          : C:\NoRealDirectory
        CategoryInfo          : ObjectNotFound: (C:\NoRealDirectory:String) [], ParentContainsErrorRecordException
        FullyQualifiedErrorId : PathNotFound
    ItemName             : C:\NoRealDirectory
    SessionStateCategory : Drive
    TargetSite           :
        Name          : GetChildItems
        DeclaringType : System.Management.Automation.SessionStateInternal
        MemberType    : Method
        Module        : System.Management.Automation.dll
    StackTrace           :
   at System.Management.Automation.SessionStateInternal.GetChildItems(String path, Boolean recurse, UInt32 depth,
CmdletProviderContext context)
   at System.Management.Automation.ChildItemCmdletProviderIntrinsics.Get(String path, Boolean recurse, UInt32
depth, CmdletProviderContext context)
   at Microsoft.PowerShell.Commands.GetChildItemCommand.ProcessRecord()
    Message              : Cannot find path 'C:\NoRealDirectory' because it does not exist.
    Source               : System.Management.Automation
    HResult              : -2146233087
TargetObject          : C:\NoRealDirectory
CategoryInfo          : ObjectNotFound: (C:\NoRealDirectory:String) [Get-ChildItem], ItemNotFoundException
FullyQualifiedErrorId : PathNotFound,Microsoft.PowerShell.Commands.GetChildItemCommand
InvocationInfo        :
    MyCommand        : Get-ChildItem
    ScriptLineNumber : 1
    OffsetInLine     : 1
    HistoryId        : 57
    Line             : Get-Childitem -path c:\NoRealDirectory
    PositionMessage  : At line:1 char:1
                       + Get-Childitem -path c:\NoRealDirectory
                       + ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    InvocationName   : Get-Childitem
    CommandOrigin    : Internal
ScriptStackTrace      : at <ScriptBlock>, <No file>: line 1
PipelineIterationInfo :
```

### Exempel 2: Hämta det angivna antalet fel meddelanden som inträffat under den aktuella sessionen

Det här exemplet visar hur du använder `Get-Error` med den **senaste** parametern. I det här exemplet returnerar den **senaste** informationen om de tre senaste fel som inträffade i den här sessionen.

```powershell
Get-Error -Newest 3
```

### Exempel 3: skicka en samling fel för att få detaljerade meddelanden

Den `$Error` automatiska variabeln innehåller en matris med fel objekt i den aktuella sessionen. Objekts mat ris kan vara skickas för `Get-Error` att få detaljerade fel meddelanden.

I det här exemplet `$Error` är skickas till- `Get-Error` cmdleten. Resultatet är en lista med detaljerade fel meddelanden, liknande resultatet i exempel 1.

```powershell
$Error | Get-Error
```

## PARAMETRAR

### – Nyaste

Anger antalet fel som ska visas i den aktuella sessionen.

```yaml
Type: System.Int32
Parameter Sets: Newest
Aliases: Last

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### – InputObject

Den här parametern används för pipeline-ininformation.

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: Error
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### CommonParameters

Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable. Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## INDATA

### PSObject

Har stöd för inmatade från alla **PSObject** , men resultaten varierar om varken ett **ErrorRecord** -eller **Exception** -objekt anges.

## UTDATA

### System. Management. Automation. ErrorRecord # PSExtendedError

Utdata i ett **PSExtendedError** -objekt.

## ANTECKNINGAR

`Get-Error` accepterar pipeline-ininformation. Till exempel `$Error | Get-Error`.

## RELATERADE LÄNKAR

[about_Try_Catch_Finally](../Microsoft.PowerShell.Core/About/about_Try_Catch_Finally.md)
