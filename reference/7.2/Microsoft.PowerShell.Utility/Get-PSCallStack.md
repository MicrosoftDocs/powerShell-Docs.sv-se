---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/get-pscallstack?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-PSCallStack
ms.openlocfilehash: 607e3999a1dbe9a4f22a751f11ac93ee3f9d9409
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94708630"
---
# Get-PSCallStack

## SAMMANFATTNING
Visar den aktuella anrops stacken.

## SYNTAX

```
Get-PSCallStack [<CommonParameters>]
```

## BESKRIVNING

Cmdlet: en **Get-PSCallStack** visar den aktuella anrops stacken.

Även om den är avsedd att användas med PowerShell-felsökaren kan du använda denna cmdlet för att Visa anrops stacken i ett skript eller en funktion utanför fel söknings programmet.

Om du vill köra kommandot **Get-PSCallStack** när du är i fel söknings programmet skriver du `k` eller `Get-PSCallStack` .

## EXEMPEL

### Exempel 1: Hämta anrops stacken för en funktion

```
PS C:\> function my-alias {
$p = $args[0]
Get-Alias | where {$_.definition -like "*$p"} | format-table definition, name -auto
}
PS C:\ps-test> Set-PSBreakpoint -Command my-alias
Command    : my-alias
Action     :
Enabled    : True
HitCount   : 0
Id         : 0
Script     : prompt PS C:\> my-alias Get-Content

Entering debug mode. Use h or ? for help.
Hit Command breakpoint on 'prompt:my-alias'
my-alias get-content
[DBG]: PS C:\ps-test> s
$p = $args[0]
DEBUG: Stepped to ':    $p = $args[0]    '
[DBG]: PS C:\ps-test> s
get-alias | Where {$_.Definition -like "*$p*"} | format-table Definition,
[DBG]: PS C:\ps-test>get-pscallstack

Name        CommandLineParameters         UnboundArguments              Location
----        ---------------------         ----------------              --------
prompt      {}                            {}                            prompt
my-alias    {}                            {get-content}                 prompt
prompt      {}                            {}                            prompt PS C:\> [DBG]: PS C:\ps-test> o
Definition  Name
----------  ----
Get-Content gc
Get-Content cat
Get-Content type
```

Detta kommando använder **Get-PSCallStack** -cmdleten för att Visa anrops stacken för mitt alias, en enkel funktion som hämtar alias för ett cmdlet-namn.

Det första kommandot anger funktionen vid PowerShell-prompten.
Det andra kommandot använder cmdleten Set-PSBreakpoint för att ange en Bryt punkt för funktionen My-Alias.
Det tredje kommandot använder funktionen My-Alias för att hämta alla alias i den aktuella sessionen för Get-Content-cmdleten.

Fel söknings verktyget bryts i vid funktions anropet.
Två steg i följd av steg-till-kommandon börjar köra funktions raden per rad.
Sedan används kommandot **Get-PSCallStack** för att hämta anrops stacken.

Det sista kommandot är ett Step-Out kommando (o) som avslutar fel söknings programmet och fortsätter att köra skriptet för att slutföras.

## PARAMETRAR

### CommonParameters

Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable. Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## INDATA

### Inga

Det går inte att skicka pipe-objekt till denna cmdlet.

## UTDATA

### System. Management. Automation. CallStackFrame

**Get-PSCallStack** returnerar ett objekt som representerar objekten i anrops stacken.

## ANTECKNINGAR

## RELATERADE LÄNKAR

[Disable-PSBreakpoint](Disable-PSBreakpoint.md)

[Aktivera – PSBreakpoint](Enable-PSBreakpoint.md)

[Format-Table](Format-Table.md)

[Get-PSBreakpoint](Get-PSBreakpoint.md)

[Remove-PSBreakpoint](Remove-PSBreakpoint.md)

[Set-PSBreakpoint](Set-PSBreakpoint.md)

