---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 10/14/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/write-debug?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Write-Debug
ms.openlocfilehash: 025e208fa5996a646cb066a703d51002b1b6d5ad
ms.sourcegitcommit: 16883bb67e34b3915798070f60f974bf85160bd3
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/16/2020
ms.locfileid: "93272696"
---
# <span data-ttu-id="0a810-103">Write-Debug</span><span class="sxs-lookup"><span data-stu-id="0a810-103">Write-Debug</span></span>

## <span data-ttu-id="0a810-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="0a810-104">SYNOPSIS</span></span>
<span data-ttu-id="0a810-105">Skriver ett fel söknings meddelande till-konsolen.</span><span class="sxs-lookup"><span data-stu-id="0a810-105">Writes a debug message to the console.</span></span>

## <span data-ttu-id="0a810-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="0a810-106">SYNTAX</span></span>

```
Write-Debug [-Message] <String> [<CommonParameters>]
```

## <span data-ttu-id="0a810-107">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="0a810-107">DESCRIPTION</span></span>

<span data-ttu-id="0a810-108">`Write-Debug`Cmdleten skriver fel söknings meddelanden till värden från ett skript eller kommando.</span><span class="sxs-lookup"><span data-stu-id="0a810-108">The `Write-Debug` cmdlet writes debug messages to the host from a script or command.</span></span>

<span data-ttu-id="0a810-109">Som standard visas inte fel söknings meddelanden i-konsolen, men du kan visa dem med hjälp av parametern **Debug** eller `$DebugPreference` variabeln.</span><span class="sxs-lookup"><span data-stu-id="0a810-109">By default, debug messages are not displayed in the console, but you can display them by using the **Debug** parameter or the `$DebugPreference` variable.</span></span>

## <span data-ttu-id="0a810-110">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="0a810-110">EXAMPLES</span></span>

### <span data-ttu-id="0a810-111">Exempel 1: förstå $DebugPreference</span><span class="sxs-lookup"><span data-stu-id="0a810-111">Example 1: Understand $DebugPreference</span></span>

<span data-ttu-id="0a810-112">Det här exemplet skriver ett fel söknings meddelande.</span><span class="sxs-lookup"><span data-stu-id="0a810-112">This example writes a debug message.</span></span>

```powershell
Write-Debug "Cannot open file."
```

<span data-ttu-id="0a810-113">Standardvärdet för `$DebugPreference` är **SilentlyContinue**.</span><span class="sxs-lookup"><span data-stu-id="0a810-113">The default value of `$DebugPreference` is **SilentlyContinue**.</span></span> <span data-ttu-id="0a810-114">Meddelandet visas därför inte i-konsolen.</span><span class="sxs-lookup"><span data-stu-id="0a810-114">Therefore, the message is not displayed in the console.</span></span>

### <span data-ttu-id="0a810-115">Exempel 2: ändra värdet för $DebugPreference</span><span class="sxs-lookup"><span data-stu-id="0a810-115">Example 2: Change the value of $DebugPreference</span></span>

<span data-ttu-id="0a810-116">I det här exemplet visas effekterna av att ändra värdet för `$DebugPreference` variabeln.</span><span class="sxs-lookup"><span data-stu-id="0a810-116">This example shows the effect of changing the value of the `$DebugPreference` variable.</span></span> <span data-ttu-id="0a810-117">Först visar vi det aktuella värdet för `$DebugPreference` och försöker skriva ett fel söknings meddelande.</span><span class="sxs-lookup"><span data-stu-id="0a810-117">First, we display the current value of `$DebugPreference` and attempt to write a debug message.</span></span> <span data-ttu-id="0a810-118">Sedan ändrar vi värdet för `$DebugPreference` att **fortsätta** , vilket gör att fel söknings meddelanden visas.</span><span class="sxs-lookup"><span data-stu-id="0a810-118">Then we change the value of `$DebugPreference` to **Continue** , which allows debug messages to be displayed.</span></span>

```
PS> $DebugPreference
SilentlyContinue
PS> Write-Debug "Cannot open file."
PS>
PS> $DebugPreference = "Continue"
PS> Write-Debug "Cannot open file."
DEBUG: Cannot open file.
```

<span data-ttu-id="0a810-119">Mer information om `$DebugPreference` finns i [about_Preference_Variables](/powershell/module/Microsoft.PowerShell.Core/About/about_Preference_Variables).</span><span class="sxs-lookup"><span data-stu-id="0a810-119">For more information about `$DebugPreference`, see [about_Preference_Variables](/powershell/module/Microsoft.PowerShell.Core/About/about_Preference_Variables).</span></span>

### <span data-ttu-id="0a810-120">Exempel 3: Använd fel söknings parametern om du vill åsidosätta $DebugPreference</span><span class="sxs-lookup"><span data-stu-id="0a810-120">Example 3: Use the Debug parameter to override $DebugPreference</span></span>

<span data-ttu-id="0a810-121">`Test-Debug`Funktionen skriver värdet för `$DebugPreference` variabeln till PowerShell-värden och fel söknings strömmen.</span><span class="sxs-lookup"><span data-stu-id="0a810-121">The `Test-Debug` function writes the value of the `$DebugPreference` variable to the PowerShell host and to the Debug stream.</span></span> <span data-ttu-id="0a810-122">I det här exemplet använder vi parametern **Felsök** för att åsidosätta `$DebugPreference` värdet.</span><span class="sxs-lookup"><span data-stu-id="0a810-122">In this example, we use the **Debug** parameter to override the `$DebugPreference` value.</span></span>

```powershell
function Test-Debug {
    [CmdletBinding()]
    param()
    Write-Debug ('$DebugPreference is ' + $DebugPreference)
    Write-Host ('$DebugPreference is ' + $DebugPreference)
}
```

```
PS> Test-Debug
$DebugPreference is SilentlyContinue

PS> Test-Debug -Debug
DEBUG: $DebugPreference is Continue
$DebugPreference is Continue
PS> $DebugPreference
SilentlyContinue
```

<span data-ttu-id="0a810-123">Observera att värdet för `$DebugPreference` ändras när du använder **fel söknings** parametern.</span><span class="sxs-lookup"><span data-stu-id="0a810-123">Notice that the value of `$DebugPreference` changes when you use the **Debug** parameter.</span></span> <span data-ttu-id="0a810-124">Den här ändringen påverkar bara funktionens omfattning.</span><span class="sxs-lookup"><span data-stu-id="0a810-124">This change only affects the scope of the function.</span></span> <span data-ttu-id="0a810-125">Värdet påverkas inte utanför funktionen.</span><span class="sxs-lookup"><span data-stu-id="0a810-125">The value is not affected outside the function.</span></span>

<span data-ttu-id="0a810-126">Mer information om den vanliga **fel söknings** parametern finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="0a810-126">For more information about the **Debug** common parameter, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="0a810-127">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="0a810-127">PARAMETERS</span></span>

### <span data-ttu-id="0a810-128">– Meddelande</span><span class="sxs-lookup"><span data-stu-id="0a810-128">-Message</span></span>

<span data-ttu-id="0a810-129">Anger fel söknings meddelandet som ska skickas till-konsolen.</span><span class="sxs-lookup"><span data-stu-id="0a810-129">Specifies the debug message to send to the console.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: Msg

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="0a810-130">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="0a810-130">CommonParameters</span></span>

<span data-ttu-id="0a810-131">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="0a810-131">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="0a810-132">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="0a810-132">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="0a810-133">INDATA</span><span class="sxs-lookup"><span data-stu-id="0a810-133">INPUTS</span></span>

### <span data-ttu-id="0a810-134">System. String</span><span class="sxs-lookup"><span data-stu-id="0a810-134">System.String</span></span>

<span data-ttu-id="0a810-135">Du kan skicka vidare en sträng som innehåller ett fel söknings meddelande till `Write-Debug` .</span><span class="sxs-lookup"><span data-stu-id="0a810-135">You can pipe a string that contains a debug message to `Write-Debug`.</span></span>

## <span data-ttu-id="0a810-136">UTDATA</span><span class="sxs-lookup"><span data-stu-id="0a810-136">OUTPUTS</span></span>

### <span data-ttu-id="0a810-137">Inget</span><span class="sxs-lookup"><span data-stu-id="0a810-137">None</span></span>

<span data-ttu-id="0a810-138">`Write-Debug` skriver endast till fel söknings data ström.</span><span class="sxs-lookup"><span data-stu-id="0a810-138">`Write-Debug` only writes to the debug stream.</span></span> <span data-ttu-id="0a810-139">Det skriver inte några objekt till pipelinen.</span><span class="sxs-lookup"><span data-stu-id="0a810-139">It does not write any objects to the pipeline.</span></span>

## <span data-ttu-id="0a810-140">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="0a810-140">NOTES</span></span>

## <span data-ttu-id="0a810-141">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="0a810-141">RELATED LINKS</span></span>

[<span data-ttu-id="0a810-142">about_Output_Streams</span><span class="sxs-lookup"><span data-stu-id="0a810-142">about_Output_Streams</span></span>](../Microsoft.PowerShell.Core/About/about_Output_Streams.md)

[<span data-ttu-id="0a810-143">about_Redirection</span><span class="sxs-lookup"><span data-stu-id="0a810-143">about_Redirection</span></span>](../Microsoft.PowerShell.Core/About/about_Redirection.md)

[<span data-ttu-id="0a810-144">Skriv-fel</span><span class="sxs-lookup"><span data-stu-id="0a810-144">Write-Error</span></span>](Write-Error.md)

[<span data-ttu-id="0a810-145">Skriv värd</span><span class="sxs-lookup"><span data-stu-id="0a810-145">Write-Host</span></span>](Write-Host.md)

[<span data-ttu-id="0a810-146">Skriva-utdata</span><span class="sxs-lookup"><span data-stu-id="0a810-146">Write-Output</span></span>](Write-Output.md)

[<span data-ttu-id="0a810-147">Skriv förlopp</span><span class="sxs-lookup"><span data-stu-id="0a810-147">Write-Progress</span></span>](Write-Progress.md)

[<span data-ttu-id="0a810-148">Skriv-verbose</span><span class="sxs-lookup"><span data-stu-id="0a810-148">Write-Verbose</span></span>](Write-Verbose.md)

[<span data-ttu-id="0a810-149">Skriv varning</span><span class="sxs-lookup"><span data-stu-id="0a810-149">Write-Warning</span></span>](Write-Warning.md)
