---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 10/14/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/write-debug?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Write-Debug
ms.openlocfilehash: 3d23f76dbf8e1c9a21805a4914038c8c4f319852
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94710339"
---
# <span data-ttu-id="98ae0-102">Write-Debug</span><span class="sxs-lookup"><span data-stu-id="98ae0-102">Write-Debug</span></span>

## <span data-ttu-id="98ae0-103">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="98ae0-103">SYNOPSIS</span></span>
<span data-ttu-id="98ae0-104">Skriver ett fel söknings meddelande till-konsolen.</span><span class="sxs-lookup"><span data-stu-id="98ae0-104">Writes a debug message to the console.</span></span>

## <span data-ttu-id="98ae0-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="98ae0-105">SYNTAX</span></span>

```
Write-Debug [-Message] <String> [<CommonParameters>]
```

## <span data-ttu-id="98ae0-106">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="98ae0-106">DESCRIPTION</span></span>

<span data-ttu-id="98ae0-107">`Write-Debug`Cmdleten skriver fel söknings meddelanden till värden från ett skript eller kommando.</span><span class="sxs-lookup"><span data-stu-id="98ae0-107">The `Write-Debug` cmdlet writes debug messages to the host from a script or command.</span></span>

<span data-ttu-id="98ae0-108">Som standard visas inte fel söknings meddelanden i-konsolen, men du kan visa dem med hjälp av parametern **Debug** eller `$DebugPreference` variabeln.</span><span class="sxs-lookup"><span data-stu-id="98ae0-108">By default, debug messages are not displayed in the console, but you can display them by using the **Debug** parameter or the `$DebugPreference` variable.</span></span>

## <span data-ttu-id="98ae0-109">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="98ae0-109">EXAMPLES</span></span>

### <span data-ttu-id="98ae0-110">Exempel 1: förstå $DebugPreference</span><span class="sxs-lookup"><span data-stu-id="98ae0-110">Example 1: Understand $DebugPreference</span></span>

<span data-ttu-id="98ae0-111">Det här exemplet skriver ett fel söknings meddelande.</span><span class="sxs-lookup"><span data-stu-id="98ae0-111">This example writes a debug message.</span></span>

```powershell
Write-Debug "Cannot open file."
```

<span data-ttu-id="98ae0-112">Standardvärdet för `$DebugPreference` är **SilentlyContinue**.</span><span class="sxs-lookup"><span data-stu-id="98ae0-112">The default value of `$DebugPreference` is **SilentlyContinue**.</span></span> <span data-ttu-id="98ae0-113">Meddelandet visas därför inte i-konsolen.</span><span class="sxs-lookup"><span data-stu-id="98ae0-113">Therefore, the message is not displayed in the console.</span></span>

### <span data-ttu-id="98ae0-114">Exempel 2: ändra värdet för $DebugPreference</span><span class="sxs-lookup"><span data-stu-id="98ae0-114">Example 2: Change the value of $DebugPreference</span></span>

<span data-ttu-id="98ae0-115">I det här exemplet visas effekterna av att ändra värdet för `$DebugPreference` variabeln.</span><span class="sxs-lookup"><span data-stu-id="98ae0-115">This example shows the effect of changing the value of the `$DebugPreference` variable.</span></span> <span data-ttu-id="98ae0-116">Först visar vi det aktuella värdet för `$DebugPreference` och försöker skriva ett fel söknings meddelande.</span><span class="sxs-lookup"><span data-stu-id="98ae0-116">First, we display the current value of `$DebugPreference` and attempt to write a debug message.</span></span> <span data-ttu-id="98ae0-117">Sedan ändrar vi värdet för `$DebugPreference` att **fortsätta**, vilket gör att fel söknings meddelanden visas.</span><span class="sxs-lookup"><span data-stu-id="98ae0-117">Then we change the value of `$DebugPreference` to **Continue**, which allows debug messages to be displayed.</span></span>

```
PS> $DebugPreference
SilentlyContinue
PS> Write-Debug "Cannot open file."
PS>
PS> $DebugPreference = "Continue"
PS> Write-Debug "Cannot open file."
DEBUG: Cannot open file.
```

<span data-ttu-id="98ae0-118">Mer information om `$DebugPreference` finns i [about_Preference_Variables](/powershell/module/Microsoft.PowerShell.Core/About/about_Preference_Variables).</span><span class="sxs-lookup"><span data-stu-id="98ae0-118">For more information about `$DebugPreference`, see [about_Preference_Variables](/powershell/module/Microsoft.PowerShell.Core/About/about_Preference_Variables).</span></span>

### <span data-ttu-id="98ae0-119">Exempel 3: Använd fel söknings parametern om du vill åsidosätta $DebugPreference</span><span class="sxs-lookup"><span data-stu-id="98ae0-119">Example 3: Use the Debug parameter to override $DebugPreference</span></span>

<span data-ttu-id="98ae0-120">`Test-Debug`Funktionen skriver värdet för `$DebugPreference` variabeln till PowerShell-värden och fel söknings strömmen.</span><span class="sxs-lookup"><span data-stu-id="98ae0-120">The `Test-Debug` function writes the value of the `$DebugPreference` variable to the PowerShell host and to the Debug stream.</span></span> <span data-ttu-id="98ae0-121">I det här exemplet använder vi parametern **Felsök** för att åsidosätta `$DebugPreference` värdet.</span><span class="sxs-lookup"><span data-stu-id="98ae0-121">In this example, we use the **Debug** parameter to override the `$DebugPreference` value.</span></span>

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

<span data-ttu-id="98ae0-122">Observera att värdet för `$DebugPreference` ändras när du använder **fel söknings** parametern.</span><span class="sxs-lookup"><span data-stu-id="98ae0-122">Notice that the value of `$DebugPreference` changes when you use the **Debug** parameter.</span></span> <span data-ttu-id="98ae0-123">Den här ändringen påverkar bara funktionens omfattning.</span><span class="sxs-lookup"><span data-stu-id="98ae0-123">This change only affects the scope of the function.</span></span> <span data-ttu-id="98ae0-124">Värdet påverkas inte utanför funktionen.</span><span class="sxs-lookup"><span data-stu-id="98ae0-124">The value is not affected outside the function.</span></span>

<span data-ttu-id="98ae0-125">Mer information om den vanliga **fel söknings** parametern finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="98ae0-125">For more information about the **Debug** common parameter, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="98ae0-126">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="98ae0-126">PARAMETERS</span></span>

### <span data-ttu-id="98ae0-127">– Meddelande</span><span class="sxs-lookup"><span data-stu-id="98ae0-127">-Message</span></span>

<span data-ttu-id="98ae0-128">Anger fel söknings meddelandet som ska skickas till-konsolen.</span><span class="sxs-lookup"><span data-stu-id="98ae0-128">Specifies the debug message to send to the console.</span></span>

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

### <span data-ttu-id="98ae0-129">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="98ae0-129">CommonParameters</span></span>

<span data-ttu-id="98ae0-130">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="98ae0-130">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="98ae0-131">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="98ae0-131">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="98ae0-132">INDATA</span><span class="sxs-lookup"><span data-stu-id="98ae0-132">INPUTS</span></span>

### <span data-ttu-id="98ae0-133">System. String</span><span class="sxs-lookup"><span data-stu-id="98ae0-133">System.String</span></span>

<span data-ttu-id="98ae0-134">Du kan skicka vidare en sträng som innehåller ett fel söknings meddelande till `Write-Debug` .</span><span class="sxs-lookup"><span data-stu-id="98ae0-134">You can pipe a string that contains a debug message to `Write-Debug`.</span></span>

## <span data-ttu-id="98ae0-135">UTDATA</span><span class="sxs-lookup"><span data-stu-id="98ae0-135">OUTPUTS</span></span>

### <span data-ttu-id="98ae0-136">Inga</span><span class="sxs-lookup"><span data-stu-id="98ae0-136">None</span></span>

<span data-ttu-id="98ae0-137">`Write-Debug` skriver endast till fel söknings data ström.</span><span class="sxs-lookup"><span data-stu-id="98ae0-137">`Write-Debug` only writes to the debug stream.</span></span> <span data-ttu-id="98ae0-138">Det skriver inte några objekt till pipelinen.</span><span class="sxs-lookup"><span data-stu-id="98ae0-138">It does not write any objects to the pipeline.</span></span>

## <span data-ttu-id="98ae0-139">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="98ae0-139">NOTES</span></span>

## <span data-ttu-id="98ae0-140">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="98ae0-140">RELATED LINKS</span></span>

[<span data-ttu-id="98ae0-141">about_Output_Streams</span><span class="sxs-lookup"><span data-stu-id="98ae0-141">about_Output_Streams</span></span>](../Microsoft.PowerShell.Core/About/about_Output_Streams.md)

[<span data-ttu-id="98ae0-142">about_Redirection</span><span class="sxs-lookup"><span data-stu-id="98ae0-142">about_Redirection</span></span>](../Microsoft.PowerShell.Core/About/about_Redirection.md)

[<span data-ttu-id="98ae0-143">Skriv-fel</span><span class="sxs-lookup"><span data-stu-id="98ae0-143">Write-Error</span></span>](Write-Error.md)

[<span data-ttu-id="98ae0-144">Skriv värd</span><span class="sxs-lookup"><span data-stu-id="98ae0-144">Write-Host</span></span>](Write-Host.md)

[<span data-ttu-id="98ae0-145">Skriva-utdata</span><span class="sxs-lookup"><span data-stu-id="98ae0-145">Write-Output</span></span>](Write-Output.md)

[<span data-ttu-id="98ae0-146">Skriv förlopp</span><span class="sxs-lookup"><span data-stu-id="98ae0-146">Write-Progress</span></span>](Write-Progress.md)

[<span data-ttu-id="98ae0-147">Skriv-verbose</span><span class="sxs-lookup"><span data-stu-id="98ae0-147">Write-Verbose</span></span>](Write-Verbose.md)

[<span data-ttu-id="98ae0-148">Skriv varning</span><span class="sxs-lookup"><span data-stu-id="98ae0-148">Write-Warning</span></span>](Write-Warning.md)
