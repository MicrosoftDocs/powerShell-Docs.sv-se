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
# <span data-ttu-id="9e404-103">Get-PSReadLineOption</span><span class="sxs-lookup"><span data-stu-id="9e404-103">Get-PSReadLineOption</span></span>

## <span data-ttu-id="9e404-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="9e404-104">SYNOPSIS</span></span>
<span data-ttu-id="9e404-105">Hämtar värden för de alternativ som kan konfigureras.</span><span class="sxs-lookup"><span data-stu-id="9e404-105">Gets values for the options that can be configured.</span></span>

## <span data-ttu-id="9e404-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="9e404-106">SYNTAX</span></span>

```
Get-PSReadLineOption [<CommonParameters>]
```

## <span data-ttu-id="9e404-107">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="9e404-107">DESCRIPTION</span></span>

<span data-ttu-id="9e404-108">`Get-PSReadLineOption`Cmdleten returnerar det aktuella läget för de inställningar som kan konfigureras med hjälp av `Set-PSReadLineOption` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="9e404-108">The `Get-PSReadLineOption` cmdlet returns the current state of the settings that can be configured by using the `Set-PSReadLineOption` cmdlet.</span></span> <span data-ttu-id="9e404-109">Du kan använda det returnerade objektet för att ändra **PSReadLine** -alternativ.</span><span class="sxs-lookup"><span data-stu-id="9e404-109">You can use the returned object to change **PSReadLine** options.</span></span> <span data-ttu-id="9e404-110">Detta ger ett något enklare sätt att ange Färgnings alternativ för flera typer av tokens.</span><span class="sxs-lookup"><span data-stu-id="9e404-110">This provides a slightly simpler way to set syntax coloring options for multiple kinds of tokens.</span></span>

## <span data-ttu-id="9e404-111">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="9e404-111">EXAMPLES</span></span>

### <span data-ttu-id="9e404-112">Exempel 1: Hämta alternativ och deras värden</span><span class="sxs-lookup"><span data-stu-id="9e404-112">Example 1: Get options and their values</span></span>

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

<span data-ttu-id="9e404-113">Det här kommandot returnerar listan över tillgängliga PSReadLine-alternativ och deras aktuella värden.</span><span class="sxs-lookup"><span data-stu-id="9e404-113">This command returns the list of available PSReadLine options and their current values.</span></span>

## <span data-ttu-id="9e404-114">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="9e404-114">PARAMETERS</span></span>

### <span data-ttu-id="9e404-115">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="9e404-115">CommonParameters</span></span>

<span data-ttu-id="9e404-116">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="9e404-116">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="9e404-117">Mer information finns i [about_CommonParameters](http://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="9e404-117">For more information, see [about_CommonParameters](http://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="9e404-118">INDATA</span><span class="sxs-lookup"><span data-stu-id="9e404-118">INPUTS</span></span>

### <span data-ttu-id="9e404-119">Inget</span><span class="sxs-lookup"><span data-stu-id="9e404-119">None</span></span>

<span data-ttu-id="9e404-120">Det går inte att skicka pipe-objekt till denna cmdlet.</span><span class="sxs-lookup"><span data-stu-id="9e404-120">You cannot pipe objects to this cmdlet.</span></span>

## <span data-ttu-id="9e404-121">UTDATA</span><span class="sxs-lookup"><span data-stu-id="9e404-121">OUTPUTS</span></span>

### <span data-ttu-id="9e404-122">Microsoft. PowerShell. PSConsoleReadLineOptions</span><span class="sxs-lookup"><span data-stu-id="9e404-122">Microsoft.PowerShell.PSConsoleReadLineOptions</span></span>

<span data-ttu-id="9e404-123">En instans av de aktuella alternativen.</span><span class="sxs-lookup"><span data-stu-id="9e404-123">An instance of the current options.</span></span> <span data-ttu-id="9e404-124">Om du ändrar egenskaps värden för det här objektet uppdateras inställningarna i PSReadLine direkt utan att anropas `Set-PSReadLineOption` .</span><span class="sxs-lookup"><span data-stu-id="9e404-124">Changing the property values of this object updates the settings in PSReadLine directly without invoking `Set-PSReadLineOption`.</span></span>

## <span data-ttu-id="9e404-125">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="9e404-125">NOTES</span></span>

## <span data-ttu-id="9e404-126">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="9e404-126">RELATED LINKS</span></span>

[<span data-ttu-id="9e404-127">Remove-PSReadLineKeyHandler</span><span class="sxs-lookup"><span data-stu-id="9e404-127">Remove-PSReadLineKeyHandler</span></span>](Remove-PSReadLineKeyHandler.md)

[<span data-ttu-id="9e404-128">Get-PSReadLineKeyHandler</span><span class="sxs-lookup"><span data-stu-id="9e404-128">Get-PSReadLineKeyHandler</span></span>](Get-PSReadLineKeyHandler.md)

[<span data-ttu-id="9e404-129">Set-PSReadLineOption</span><span class="sxs-lookup"><span data-stu-id="9e404-129">Set-PSReadLineOption</span></span>](Set-PSReadLineOption.md)

[<span data-ttu-id="9e404-130">Set-PSReadLineKeyHandler</span><span class="sxs-lookup"><span data-stu-id="9e404-130">Set-PSReadLineKeyHandler</span></span>](Set-PSReadLineKeyHandler.md)
