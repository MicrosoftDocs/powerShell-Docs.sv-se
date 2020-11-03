---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 08/22/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/set-psdebug?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-PSDebug
ms.openlocfilehash: 0c5f161afd77a8a7c7c8e31efb98f3097e95a972
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93264165"
---
# <span data-ttu-id="139a0-103">Set-PSDebug</span><span class="sxs-lookup"><span data-stu-id="139a0-103">Set-PSDebug</span></span>

## <span data-ttu-id="139a0-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="139a0-104">SYNOPSIS</span></span>
<span data-ttu-id="139a0-105">Aktiverar och inaktiverar funktioner för skript fel sökning, ställer in spårnings nivå och växlar till strikt läge.</span><span class="sxs-lookup"><span data-stu-id="139a0-105">Turns script debugging features on and off, sets the trace level, and toggles strict mode.</span></span>

## <span data-ttu-id="139a0-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="139a0-106">SYNTAX</span></span>

### <span data-ttu-id="139a0-107">på</span><span class="sxs-lookup"><span data-stu-id="139a0-107">on</span></span>

```
Set-PSDebug [-Trace <Int32>] [-Step] [-Strict] [<CommonParameters>]
```

### <span data-ttu-id="139a0-108">av</span><span class="sxs-lookup"><span data-stu-id="139a0-108">off</span></span>

```
Set-PSDebug [-Off] [<CommonParameters>]
```

## <span data-ttu-id="139a0-109">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="139a0-109">DESCRIPTION</span></span>

<span data-ttu-id="139a0-110">`Set-PSDebug`Cmdleten aktiverar och inaktiverar funktioner för skript fel sökning, ställer in spårnings nivån och växlar till strikt läge.</span><span class="sxs-lookup"><span data-stu-id="139a0-110">The `Set-PSDebug` cmdlet turns script debugging features on and off, sets the trace level, and toggles strict mode.</span></span> <span data-ttu-id="139a0-111">Som standard är PowerShell-felsöknings funktionerna inaktiverade.</span><span class="sxs-lookup"><span data-stu-id="139a0-111">By default, the PowerShell debug features are off.</span></span>

<span data-ttu-id="139a0-112">När **spårnings** parametern har värdet `1` , spåras varje rad med skript när den körs.</span><span class="sxs-lookup"><span data-stu-id="139a0-112">When the **Trace** parameter has a value of `1`, each line of script is traced as it runs.</span></span> <span data-ttu-id="139a0-113">När parametern har värdet `2` , spåras även variabel tilldelningar, funktions anrop och skript anrop.</span><span class="sxs-lookup"><span data-stu-id="139a0-113">When the parameter has a value of `2`, variable assignments, function calls, and script calls are also traced.</span></span> <span data-ttu-id="139a0-114">Om du anger parametern **steg** uppmanas du innan varje rad i skriptet körs.</span><span class="sxs-lookup"><span data-stu-id="139a0-114">If the **Step** parameter is specified, you're prompted before each line of the script runs.</span></span>

## <span data-ttu-id="139a0-115">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="139a0-115">EXAMPLES</span></span>

### <span data-ttu-id="139a0-116">Exempel 1: Ange spårnings nivå</span><span class="sxs-lookup"><span data-stu-id="139a0-116">Example 1: Set the trace level</span></span>

<span data-ttu-id="139a0-117">Det här exemplet anger spårnings nivån till `2` och kör sedan ett skript som visar siffrorna 1, 2 och</span><span class="sxs-lookup"><span data-stu-id="139a0-117">This example sets the trace level to `2`, and then runs a script that displays the numbers 1, 2, and</span></span>
3.

```powershell
Set-PSDebug -Trace 2; foreach ($i in 1..3) {$i}
```

```Output
DEBUG:    1+ Set-PSDebug -Trace 2; foreach ($i in  >>>> 1..3) {$i}
DEBUG:     ! SET $foreach = 'IEnumerator'.
DEBUG:    1+ Set-PSDebug -Trace 2; foreach ( >>>> $i in 1..3) {$i}
DEBUG:     ! SET $i = '1'.
DEBUG:    1+ Set-PSDebug -Trace 2; foreach ($i in 1..3) { >>>> $i}
1
DEBUG:    1+ Set-PSDebug -Trace 2; foreach ( >>>> $i in 1..3) {$i}
DEBUG:     ! SET $i = '2'.
DEBUG:    1+ Set-PSDebug -Trace 2; foreach ($i in 1..3) { >>>> $i}
2
DEBUG:    1+ Set-PSDebug -Trace 2; foreach ( >>>> $i in 1..3) {$i}
DEBUG:     ! SET $i = '3'.
DEBUG:    1+ Set-PSDebug -Trace 2; foreach ($i in 1..3) { >>>> $i}
3
DEBUG:    1+ Set-PSDebug -Trace 2; foreach ( >>>> $i in 1..3) {$i}
DEBUG:     ! SET $foreach = ''.
```

### <span data-ttu-id="139a0-118">Exempel 2: Aktivera stegning</span><span class="sxs-lookup"><span data-stu-id="139a0-118">Example 2: Turn on stepping</span></span>

<span data-ttu-id="139a0-119">Det här exemplet aktiverar stegning och kör sedan ett skript som visar siffrorna 1, 2 och 3.</span><span class="sxs-lookup"><span data-stu-id="139a0-119">This example turns on stepping, and then runs a script that displays the numbers 1, 2, and 3.</span></span>

```powershell
Set-PSDebug -Step; foreach ($i in 1..3) {$i}
```

```Output
Continue with this operation?
   1+ Set-PSDebug -Step; foreach ($i in  >>>> 1..3) {$i}
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): A
DEBUG:    1+ Set-PSDebug -Step; foreach ($i in  >>>> 1..3) {$i}
1
2
3
```

### <span data-ttu-id="139a0-120">Exempel 3: Använd strikt läge</span><span class="sxs-lookup"><span data-stu-id="139a0-120">Example 3: Use strict mode</span></span>

<span data-ttu-id="139a0-121">I det här exemplet placeras PowerShell i strikt läge och försöker komma åt en variabel som inte har ett tilldelat värde.</span><span class="sxs-lookup"><span data-stu-id="139a0-121">This example puts PowerShell in strict mode and attempts to access a variable that doesn't have an assigned value.</span></span>

```powershell
Set-PSDebug -Strict; $NewVar
```

```Output
The variable '$NewVar' cannot be retrieved because it has not been set.
At line:1 char:22
+ Set-PSDebug -Strict; $NewVar
```

### <span data-ttu-id="139a0-122">Exempel 4: inaktivera fel söknings funktioner</span><span class="sxs-lookup"><span data-stu-id="139a0-122">Example 4: Turn off debug features</span></span>

<span data-ttu-id="139a0-123">Det här exemplet stänger av alla fel söknings funktioner och kör sedan ett skript som visar siffrorna 1, 2 och 3.</span><span class="sxs-lookup"><span data-stu-id="139a0-123">This example turns off all debugging features, and then runs a script that displays the numbers 1, 2, and 3.</span></span>

```powershell
Set-PSDebug -Off; foreach ($i in 1..3) {$i}
```

```Output
1
2
3
```

## <span data-ttu-id="139a0-124">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="139a0-124">PARAMETERS</span></span>

### <span data-ttu-id="139a0-125">-Av</span><span class="sxs-lookup"><span data-stu-id="139a0-125">-Off</span></span>

<span data-ttu-id="139a0-126">Inaktiverar alla funktioner för fel sökning av skript.</span><span class="sxs-lookup"><span data-stu-id="139a0-126">Turns off all script debugging features.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: off
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="139a0-127">– Steg</span><span class="sxs-lookup"><span data-stu-id="139a0-127">-Step</span></span>

<span data-ttu-id="139a0-128">Aktiverar skript stegning.</span><span class="sxs-lookup"><span data-stu-id="139a0-128">Turns on script stepping.</span></span> <span data-ttu-id="139a0-129">Innan varje rad körs, kommer PowerShell att bli ombedd att stoppa, fortsätta eller ange en ny tolknings nivå för att kontrol lera status för skriptet.</span><span class="sxs-lookup"><span data-stu-id="139a0-129">Before each line runs, PowerShell prompts you to stop, continue, or enter a new interpreter level to inspect the state of the script.</span></span>

<span data-ttu-id="139a0-130">Genom att ange **steg** parametern anges automatiskt spårnings nivån `1` .</span><span class="sxs-lookup"><span data-stu-id="139a0-130">Specifying the **Step** parameter automatically sets a trace level of `1`.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: on
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="139a0-131">– Strikt</span><span class="sxs-lookup"><span data-stu-id="139a0-131">-Strict</span></span>

<span data-ttu-id="139a0-132">Anger att variabler måste tilldelas ett värde innan de refereras till i ett skript.</span><span class="sxs-lookup"><span data-stu-id="139a0-132">Specifies that variables must be assigned a value before being referenced in a script.</span></span> <span data-ttu-id="139a0-133">Om en variabel refererar till innan ett värde tilldelas, returnerar PowerShell ett undantags fel.</span><span class="sxs-lookup"><span data-stu-id="139a0-133">If a variable is referenced before a value is assigned, PowerShell returns an exception error.</span></span> <span data-ttu-id="139a0-134">Detta motsvarar `Set-StrictMode -Version 1` .</span><span class="sxs-lookup"><span data-stu-id="139a0-134">This is equivalent to `Set-StrictMode -Version 1`.</span></span> <span data-ttu-id="139a0-135">Mer information finns i [set-StrictMode](Set-StrictMode.md).</span><span class="sxs-lookup"><span data-stu-id="139a0-135">For more information, see [Set-StrictMode](Set-StrictMode.md).</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: on
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="139a0-136">-Spåra</span><span class="sxs-lookup"><span data-stu-id="139a0-136">-Trace</span></span>

<span data-ttu-id="139a0-137">Anger spårnings nivån för varje rad i ett skript.</span><span class="sxs-lookup"><span data-stu-id="139a0-137">Specifies the trace level for each line in a script.</span></span> <span data-ttu-id="139a0-138">Varje rad spåras när den körs.</span><span class="sxs-lookup"><span data-stu-id="139a0-138">Each line is traced as it's run.</span></span>

<span data-ttu-id="139a0-139">De acceptabla värdena för den här parametern är följande:</span><span class="sxs-lookup"><span data-stu-id="139a0-139">The acceptable values for this parameter are as follows:</span></span>

- <span data-ttu-id="139a0-140">0: inaktivera skript spårning.</span><span class="sxs-lookup"><span data-stu-id="139a0-140">0: Turn script tracing off.</span></span>
- <span data-ttu-id="139a0-141">1: spåra skript rader när de körs.</span><span class="sxs-lookup"><span data-stu-id="139a0-141">1: Trace script lines as they run.</span></span>
- <span data-ttu-id="139a0-142">2: spåra skript rader, variabel tilldelningar, funktions anrop och skript.</span><span class="sxs-lookup"><span data-stu-id="139a0-142">2: Trace script lines, variable assignments, function calls, and scripts.</span></span>

```yaml
Type: System.Int32
Parameter Sets: on
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="139a0-143">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="139a0-143">CommonParameters</span></span>

<span data-ttu-id="139a0-144">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="139a0-144">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="139a0-145">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="139a0-145">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="139a0-146">INDATA</span><span class="sxs-lookup"><span data-stu-id="139a0-146">INPUTS</span></span>

### <span data-ttu-id="139a0-147">Inget</span><span class="sxs-lookup"><span data-stu-id="139a0-147">None</span></span>

<span data-ttu-id="139a0-148">Du kan inte pipeline-ininformation till denna cmdlet.</span><span class="sxs-lookup"><span data-stu-id="139a0-148">You can't pipeline input to this cmdlet.</span></span>

## <span data-ttu-id="139a0-149">UTDATA</span><span class="sxs-lookup"><span data-stu-id="139a0-149">OUTPUTS</span></span>

### <span data-ttu-id="139a0-150">Inget</span><span class="sxs-lookup"><span data-stu-id="139a0-150">None</span></span>

<span data-ttu-id="139a0-151">Denna cmdlet returnerar inga utdata.</span><span class="sxs-lookup"><span data-stu-id="139a0-151">This cmdlet doesn't return any output.</span></span>

## <span data-ttu-id="139a0-152">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="139a0-152">NOTES</span></span>

## <span data-ttu-id="139a0-153">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="139a0-153">RELATED LINKS</span></span>

[<span data-ttu-id="139a0-154">about_Debuggers</span><span class="sxs-lookup"><span data-stu-id="139a0-154">about_Debuggers</span></span>](./About/about_Debuggers.md)

[<span data-ttu-id="139a0-155">Fel sökning – process</span><span class="sxs-lookup"><span data-stu-id="139a0-155">Debug-Process</span></span>](../Microsoft.PowerShell.Management/Debug-Process.md)

[<span data-ttu-id="139a0-156">Set-PSBreakpoint</span><span class="sxs-lookup"><span data-stu-id="139a0-156">Set-PSBreakpoint</span></span>](../Microsoft.PowerShell.Utility/Set-PSBreakpoint.md)

[<span data-ttu-id="139a0-157">Set-StrictMode</span><span class="sxs-lookup"><span data-stu-id="139a0-157">Set-StrictMode</span></span>](Set-StrictMode.md)

[<span data-ttu-id="139a0-158">Skriv-debug</span><span class="sxs-lookup"><span data-stu-id="139a0-158">Write-Debug</span></span>](../Microsoft.PowerShell.Utility/Write-Debug.md)