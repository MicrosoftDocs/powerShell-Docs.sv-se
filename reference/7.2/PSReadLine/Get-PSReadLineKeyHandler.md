---
external help file: Microsoft.PowerShell.PSReadLine2.dll-Help.xml
Locale: en-US
Module Name: PSReadLine
ms.date: 12/07/2018
online version: https://docs.microsoft.com/powershell/module/psreadline/get-psreadlinekeyhandler?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-PSReadLineKeyHandler
ms.openlocfilehash: bb1e92a8f4bca96dc369b5b799c7e89245e432be
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94709054"
---
# <span data-ttu-id="16c92-102">Get-PSReadLineKeyHandler</span><span class="sxs-lookup"><span data-stu-id="16c92-102">Get-PSReadLineKeyHandler</span></span>

## <span data-ttu-id="16c92-103">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="16c92-103">SYNOPSIS</span></span>
<span data-ttu-id="16c92-104">Hämtar de kopplade nyckel funktionerna för PSReadLine-modulen.</span><span class="sxs-lookup"><span data-stu-id="16c92-104">Gets the bound key functions for the PSReadLine module.</span></span>

## <span data-ttu-id="16c92-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="16c92-105">SYNTAX</span></span>

### <span data-ttu-id="16c92-106">FullListing (standard)</span><span class="sxs-lookup"><span data-stu-id="16c92-106">FullListing (default)</span></span>

```
Get-PSReadLineKeyHandler [-Bound] [-Unbound] [<CommonParameters>]
```

### <span data-ttu-id="16c92-107">SpecificBindings</span><span class="sxs-lookup"><span data-stu-id="16c92-107">SpecificBindings</span></span>

```
Get-PSReadLineKeyHandler [-Chord] <String[]> [<CommonParameters>]
```

## <span data-ttu-id="16c92-108">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="16c92-108">DESCRIPTION</span></span>

<span data-ttu-id="16c92-109">Om ingen parameter anges returnerar de för närvarande kopplade nyckel funktionerna för PSReadLine-modulen.</span><span class="sxs-lookup"><span data-stu-id="16c92-109">If no parameter is specified, returns the currently bound key functions for the PSReadLine module.</span></span>

<span data-ttu-id="16c92-110">Om parametern **ackord** anges, returnerar cmdleten specifika gränser.</span><span class="sxs-lookup"><span data-stu-id="16c92-110">If **Chord** parameter is specified, the cmdlet returns the specific bound keys.</span></span>

## <span data-ttu-id="16c92-111">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="16c92-111">EXAMPLES</span></span>

### <span data-ttu-id="16c92-112">Exempel 1: Hämta alla nyckel mappningar</span><span class="sxs-lookup"><span data-stu-id="16c92-112">Example 1: Get all key mappings</span></span>

<span data-ttu-id="16c92-113">Det här kommandot returnerar alla nyckel mappningar, kopplade och obundna.</span><span class="sxs-lookup"><span data-stu-id="16c92-113">This command returns all key mappings, bound and unbound.</span></span>

```powershell
Get-PSReadLineKeyHandler -Bound -Unbound
```

```Output
Key                   Function                Description
---                   --------                -----------
Enter                 AcceptLine              Accept the input or move to the next line if input is missing a closing token.
Shift+Enter           AddLine                 Move the cursor to the next line without attempting to execute the input
Escape                RevertLine              Equivalent to undo all edits (clears the line except lines imported from history)
LeftArrow             BackwardChar            Move the cursor back one character
RightArrow            ForwardChar             Move the cursor forward one character
Ctrl+LeftArrow        BackwardWord            Move the cursor to the beginning of the current or previous word
Ctrl+RightArrow       NextWord                Move the cursor forward to the start of the next word
Shift+LeftArrow       SelectBackwardChar      Adjust the current selection to include the previous character
Shift+RightArrow      SelectForwardChar       Adjust the current selection to include the next character
Ctrl+Shift+LeftArrow  SelectBackwardWord      Adjust the current selection to include the previous word
Ctrl+Shift+RightArrow SelectNextWord          Adjust the current selection to include the next word
UpArrow               PreviousHistory         Replace the input with the previous item in the history
DownArrow             NextHistory             Replace the input with the next item in the history
Home                  BeginningOfLine         Move the cursor to the beginning of the line
End                   EndOfLine               Move the cursor to the end of the line
Shift+Home            SelectBackwardsLine     Adjust the current selection to include from the cursor to the end of the line
Shift+End             SelectLine              Adjust the current selection to include from the cursor to the start of the line
Delete                DeleteChar              Delete the character under the cursor
Backspace             BackwardDeleteChar      Delete the character before the cursor
Ctrl+Spacebar         MenuComplete            Complete the input if there is a single completion, otherwise complete the input by selecting from a menu o...
Tab                   TabCompleteNext         Complete the input using the next completion
Shift+Tab             TabCompletePrevious     Complete the input using the previous completion
Ctrl+a                SelectAll               Select the entire line. Moves the cursor to the end of the line
Ctrl+c                CopyOrCancelLine        Either copy selected text to the clipboard, or if no text is selected, cancel editing the line with Cancel...
Ctrl+C                Copy                    Copy selected region to the system clipboard.  If no region is selected, copy the whole line
Ctrl+l                ClearScreen             Clear the screen and redraw the current line at the top of the screen
Ctrl+r                ReverseSearchHistory    Search history backwards interactively
...
```

### <span data-ttu-id="16c92-114">Exempel 2: Hämta kopplade nycklar</span><span class="sxs-lookup"><span data-stu-id="16c92-114">Example 2: Get bound keys</span></span>

<span data-ttu-id="16c92-115">Det här kommandot returnerar bara de gränser och kombinationer av nycklar som är kopplade till dem.</span><span class="sxs-lookup"><span data-stu-id="16c92-115">This command returns only bound keys and key combinations.</span></span>

```powershell
Get-PSReadLineKeyHandler
```

```Output
Key                   Function                Description
---                   --------                -----------
Enter                 AcceptLine              Accept the input or move to the next line if input is missing a closing token.
Shift+Enter           AddLine                 Move the cursor to the next line without attempting to execute the input
Escape                RevertLine              Equivalent to undo all edits (clears the line except lines imported from history)
LeftArrow             BackwardChar            Move the cursor back one character
RightArrow            ForwardChar             Move the cursor forward one character
Ctrl+LeftArrow        BackwardWord            Move the cursor to the beginning of the current or previous word
Ctrl+RightArrow       NextWord                Move the cursor forward to the start of the next word
Shift+LeftArrow       SelectBackwardChar      Adjust the current selection to include the previous character
Shift+RightArrow      SelectForwardChar       Adjust the current selection to include the next character
Ctrl+Shift+LeftArrow  SelectBackwardWord      Adjust the current selection to include the previous word
Ctrl+Shift+RightArrow SelectNextWord          Adjust the current selection to include the next word
UpArrow               PreviousHistory         Replace the input with the previous item in the history
DownArrow             NextHistory             Replace the input with the next item in the history
Home                  BeginningOfLine         Move the cursor to the beginning of the line
End                   EndOfLine               Move the cursor to the end of the line
Shift+Home            SelectBackwardsLine     Adjust the current selection to include from the cursor to the end of the line
Shift+End             SelectLine              Adjust the current selection to include from the cursor to the start of the line
Delete                DeleteChar              Delete the character under the cursor
Backspace             BackwardDeleteChar      Delete the character before the cursor
Ctrl+Spacebar         MenuComplete            Complete the input if there is a single completion, otherwise complete the input by selecting from a menu o...
Tab                   TabCompleteNext         Complete the input using the next completion
...
```

### <span data-ttu-id="16c92-116">Exempel 3: hämta vissa nyckel bindningar</span><span class="sxs-lookup"><span data-stu-id="16c92-116">Example 3: Get specific key bindings</span></span>

<span data-ttu-id="16c92-117">Det här kommandot returnerar bara bindningarna för de angivna nycklarna.</span><span class="sxs-lookup"><span data-stu-id="16c92-117">This command returns only the bindings for the specified keys.</span></span>

```powershell
Get-PSReadLineKeyHandler -Chord Enter, Shift+Enter
```

```Output
Key         Function   Description
---         --------   -----------
Enter       AcceptLine Accept the input or move to the next line if input is missing a closing token.
Shift+Enter AddLine    Move the cursor to the next line without attempting to execute the input
...
```

## <span data-ttu-id="16c92-118">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="16c92-118">PARAMETERS</span></span>

### <span data-ttu-id="16c92-119">-Kopplad</span><span class="sxs-lookup"><span data-stu-id="16c92-119">-Bound</span></span>

<span data-ttu-id="16c92-120">Anger att denna cmdlet returnerar funktioner som är kopplade till varandra.</span><span class="sxs-lookup"><span data-stu-id="16c92-120">Indicates that this cmdlet returns functions that are bound.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: FullListing
Aliases:

Required: False
Position: Named
Default value: True
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="16c92-121">-Obunden</span><span class="sxs-lookup"><span data-stu-id="16c92-121">-Unbound</span></span>

<span data-ttu-id="16c92-122">Anger att den här cmdleten returnerar funktioner som är obundna.</span><span class="sxs-lookup"><span data-stu-id="16c92-122">Indicates that this cmdlet returns functions that are unbound.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: FullListing
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="16c92-123">– Ackord</span><span class="sxs-lookup"><span data-stu-id="16c92-123">-Chord</span></span>

<span data-ttu-id="16c92-124">Returnera endast funktioner som är kopplade till vissa nycklar eller sekvenser.</span><span class="sxs-lookup"><span data-stu-id="16c92-124">Return only functions bound to specific keys or sequences.</span></span>

```yaml
Type: System.String[]
Parameter Sets: SpecificBindings
Aliases: Key

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="16c92-125">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="16c92-125">CommonParameters</span></span>

<span data-ttu-id="16c92-126">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="16c92-126">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="16c92-127">Mer information finns i [about_CommonParameters](http://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="16c92-127">For more information, see [about_CommonParameters](http://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="16c92-128">INDATA</span><span class="sxs-lookup"><span data-stu-id="16c92-128">INPUTS</span></span>

### <span data-ttu-id="16c92-129">Inga</span><span class="sxs-lookup"><span data-stu-id="16c92-129">None</span></span>

<span data-ttu-id="16c92-130">Det går inte att skicka pipe-objekt till denna cmdlet.</span><span class="sxs-lookup"><span data-stu-id="16c92-130">You cannot pipe objects to this cmdlet.</span></span>

## <span data-ttu-id="16c92-131">UTDATA</span><span class="sxs-lookup"><span data-stu-id="16c92-131">OUTPUTS</span></span>

### <span data-ttu-id="16c92-132">Microsoft. PowerShell.-hanterare</span><span class="sxs-lookup"><span data-stu-id="16c92-132">Microsoft.PowerShell.KeyHandler</span></span>

## <span data-ttu-id="16c92-133">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="16c92-133">NOTES</span></span>

## <span data-ttu-id="16c92-134">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="16c92-134">RELATED LINKS</span></span>

[<span data-ttu-id="16c92-135">Remove-PSReadLineKeyHandler</span><span class="sxs-lookup"><span data-stu-id="16c92-135">Remove-PSReadLineKeyHandler</span></span>](Remove-PSReadLineKeyHandler.md)

[<span data-ttu-id="16c92-136">Get-PSReadLineOption</span><span class="sxs-lookup"><span data-stu-id="16c92-136">Get-PSReadLineOption</span></span>](Get-PSReadLineOption.md)

[<span data-ttu-id="16c92-137">Set-PSReadLineOption</span><span class="sxs-lookup"><span data-stu-id="16c92-137">Set-PSReadLineOption</span></span>](Set-PSReadLineOption.md)

[<span data-ttu-id="16c92-138">Set-PSReadLineKeyHandler</span><span class="sxs-lookup"><span data-stu-id="16c92-138">Set-PSReadLineKeyHandler</span></span>](Set-PSReadLineKeyHandler.md)

