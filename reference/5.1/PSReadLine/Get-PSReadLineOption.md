---
external help file: Microsoft.PowerShell.PSReadLine2.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSReadline
ms.date: 06/30/2020
online version: https://docs.microsoft.com/powershell/module/psreadline/get-psreadlineoption?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-PSReadLineOption
ms.openlocfilehash: 7f731014e5a240e0c756640144ff7cae5e48f051
ms.sourcegitcommit: ae8b89e12c6fa2108075888dd6da92788d6c2888
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/21/2020
ms.locfileid: "93273074"
---
# Get-PSReadLineOption

## SAMMANFATTNING
Hämtar värden för de alternativ som kan konfigureras.

## SYNTAX

```
Get-PSReadLineOption [<CommonParameters>]
```

## BESKRIVNING

`Get-PSReadLineOption`Cmdleten returnerar det aktuella läget för de inställningar som kan konfigureras med hjälp av `Set-PSReadLineOption` cmdleten. Du kan använda det returnerade objektet för att ändra **PSReadLine** -alternativ. Detta ger ett något enklare sätt att ange Färgnings alternativ för flera typer av tokens.

## EXEMPEL

### Exempel 1: Hämta alternativ och deras värden

```powershell
Get-PSReadLineOption
```

```Output
EditMode                               : Windows
AddToHistoryHandler                    : System.Func`2[System.String,System.Object]
HistoryNoDuplicates                    : True
HistorySavePath                        : C:\Users\username\AppData\Roaming\Microsoft\Windows\
                                         PowerShell\PSReadLine\ConsoleHost_history.txt
HistorySaveStyle                       : SaveIncrementally
HistorySearchCaseSensitive             : False
HistorySearchCursorMovesToEnd          : False
MaximumHistoryCount                    : 4096
ContinuationPrompt                     : >>
ExtraPromptLineCount                   : 0
PromptText                             : {> }
BellStyle                              : Audible
DingDuration                           : 50
DingTone                               : 1221
CommandsToValidateScriptBlockArguments : {ForEach-Object, %, Invoke-Command, icm...}
CommandValidationHandler               :
CompletionQueryItems                   : 100
MaximumKillRingCount                   : 10
ShowToolTips                           : True
ViModeIndicator                        : None
WordDelimiters                         : ;:,.[]{}()/\|^&*-=+'"---
AnsiEscapeTimeout                      : 100
CommandColor                           : "$([char]0x1b)[93m"
CommentColor                           : "$([char]0x1b)[32m"
ContinuationPromptColor                : "$([char]0x1b)[37m"
DefaultTokenColor                      : "$([char]0x1b)[37m"
EmphasisColor                          : "$([char]0x1b)[96m"
ErrorColor                             : "$([char]0x1b)[91m"
KeywordColor                           : "$([char]0x1b)[92m"
MemberColor                            : "$([char]0x1b)[97m"
NumberColor                            : "$([char]0x1b)[97m"
OperatorColor                          : "$([char]0x1b)[90m"
ParameterColor                         : "$([char]0x1b)[90m"
SelectionColor                         : "$([char]0x1b)[30;47m"
StringColor                            : "$([char]0x1b)[36m"
TypeColor                              : "$([char]0x1b)[37m"
VariableColor                          : "$([char]0x1b)[92m"
```

Det här kommandot returnerar listan över tillgängliga PSReadLine-alternativ och deras aktuella värden.

## PARAMETRAR

### CommonParameters

Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable. Mer information finns i [about_CommonParameters](http://go.microsoft.com/fwlink/?LinkID=113216).

## INDATA

### Inget

Det går inte att skicka pipe-objekt till denna cmdlet.

## UTDATA

### Microsoft. PowerShell. PSConsoleReadLineOptions

En instans av de aktuella alternativen. Om du ändrar egenskaps värden för det här objektet uppdateras inställningarna i PSReadLine direkt utan att anropas `Set-PSReadLineOption` .

## ANTECKNINGAR

## RELATERADE LÄNKAR

[Remove-PSReadLineKeyHandler](Remove-PSReadLineKeyHandler.md)

[Get-PSReadLineKeyHandler](Get-PSReadLineKeyHandler.md)

[Set-PSReadLineOption](Set-PSReadLineOption.md)

[Set-PSReadLineKeyHandler](Set-PSReadLineKeyHandler.md)
