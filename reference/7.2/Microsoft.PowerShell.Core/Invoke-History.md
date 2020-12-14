---
external help file: System.Management.Automation.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 05/13/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/invoke-history?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Invoke-History
ms.openlocfilehash: 7fb4341a84706f7d31d463bb527a1a31f387c2ae
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94709991"
---
# <span data-ttu-id="33443-102">Invoke-History</span><span class="sxs-lookup"><span data-stu-id="33443-102">Invoke-History</span></span>

## <span data-ttu-id="33443-103">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="33443-103">SYNOPSIS</span></span>
<span data-ttu-id="33443-104">Kör kommandon från tidigare sessioner.</span><span class="sxs-lookup"><span data-stu-id="33443-104">Runs commands from the session history.</span></span>

## <span data-ttu-id="33443-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="33443-105">SYNTAX</span></span>

```
Invoke-History [[-Id] <String>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="33443-106">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="33443-106">DESCRIPTION</span></span>

<span data-ttu-id="33443-107">`Invoke-History`Cmdleten kör kommandon från tidigare sessioner.</span><span class="sxs-lookup"><span data-stu-id="33443-107">The `Invoke-History` cmdlet runs commands from the session history.</span></span> <span data-ttu-id="33443-108">Du kan skicka objekt som representerar kommandona från Get-History till `Invoke-History` , eller så kan du identifiera kommandon i den aktuella historiken med hjälp av deras **ID-** nummer.</span><span class="sxs-lookup"><span data-stu-id="33443-108">You can pass objects representing the commands from Get-History to `Invoke-History`, or you can identify commands in the current history by using their **Id** number.</span></span> <span data-ttu-id="33443-109">Använd cmdleten för att hitta identifikations numret för ett kommando `Get-History` .</span><span class="sxs-lookup"><span data-stu-id="33443-109">To find the identification number of a command, use the `Get-History` cmdlet.</span></span>

<span data-ttu-id="33443-110">Historiken för sessionen hanteras separat från historiken som underhålls av **PSReadLine** -modulen.</span><span class="sxs-lookup"><span data-stu-id="33443-110">The session history is managed separately from the history maintained by the **PSReadLine** module.</span></span>
<span data-ttu-id="33443-111">Båda historiken är tillgängliga i sessioner där **PSReadLine** har lästs in.</span><span class="sxs-lookup"><span data-stu-id="33443-111">Both histories are available in sessions where **PSReadLine** is loaded.</span></span> <span data-ttu-id="33443-112">Den här cmdleten fungerar bara med tidigare session.</span><span class="sxs-lookup"><span data-stu-id="33443-112">This cmdlet only works with the session history.</span></span> <span data-ttu-id="33443-113">Mer information finns i [about_PSReadLine](../PSReadLine/About/about_PSReadLine.md).</span><span class="sxs-lookup"><span data-stu-id="33443-113">For more information see, [about_PSReadLine](../PSReadLine/About/about_PSReadLine.md).</span></span>

## <span data-ttu-id="33443-114">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="33443-114">EXAMPLES</span></span>

### <span data-ttu-id="33443-115">Exempel 1: kör det senaste kommandot i historiken</span><span class="sxs-lookup"><span data-stu-id="33443-115">Example 1: Run the most recent command in the history</span></span>

<span data-ttu-id="33443-116">I det här exemplet körs det senaste eller senaste kommandot i tidigare session.</span><span class="sxs-lookup"><span data-stu-id="33443-116">This example runs the last, or most recent, command in the session history.</span></span> <span data-ttu-id="33443-117">Du kan förkorta det här kommandot som `r` alias för `Invoke-History` .</span><span class="sxs-lookup"><span data-stu-id="33443-117">You can abbreviate this command as `r`, the alias for `Invoke-History`.</span></span>

```powershell
Invoke-History
```

### <span data-ttu-id="33443-118">Exempel 2: kör kommandot som har ett angivet ID</span><span class="sxs-lookup"><span data-stu-id="33443-118">Example 2: Run the command that has a specified ID</span></span>

<span data-ttu-id="33443-119">I det här exemplet körs kommandot i sessionen med **Id** 132.</span><span class="sxs-lookup"><span data-stu-id="33443-119">This example runs the command in the session history with **Id** 132.</span></span> <span data-ttu-id="33443-120">Eftersom namnet på **ID-** parametern är valfri kan du förkorta det här kommandot med följande: `Invoke-History 132` , `ihy 132` eller `r 132` .</span><span class="sxs-lookup"><span data-stu-id="33443-120">Because the name of the **Id** parameter is optional, you can abbreviate this command as the following: `Invoke-History 132`, `ihy 132`, or `r 132`.</span></span>

```powershell
Invoke-History -Id 132
```

### <span data-ttu-id="33443-121">Exempel 3: kör det senaste kommandot med hjälp av kommando texten</span><span class="sxs-lookup"><span data-stu-id="33443-121">Example 3: Run the most recent command by using the command text</span></span>

<span data-ttu-id="33443-122">I det här exemplet körs det senaste `Get-Process` kommandot i tidigare sessioner.</span><span class="sxs-lookup"><span data-stu-id="33443-122">This example runs the most recent `Get-Process` command in the session history.</span></span> <span data-ttu-id="33443-123">När du skriver tecken för **ID-** parametern `Invoke-History` Kör det första kommandot som den hittar som matchar mönstret, med början av de senaste kommandona.</span><span class="sxs-lookup"><span data-stu-id="33443-123">When you type characters for the **Id** parameter, `Invoke-History` runs the first command that it finds that matches the pattern, starting with the most recent commands.</span></span>

```powershell
Invoke-History -Id get-pr
```

> [!NOTE]
> <span data-ttu-id="33443-124">Mönster matchning är Skift läges känsligt, men mönstret matchar början av linjen.</span><span class="sxs-lookup"><span data-stu-id="33443-124">Pattern matching is case-insensitive, but the pattern matches the beginning of the line.</span></span>

### <span data-ttu-id="33443-125">Exempel 4: kör en sekvens med kommandon från historiken</span><span class="sxs-lookup"><span data-stu-id="33443-125">Example 4: Run a sequence of commands from the history</span></span>

<span data-ttu-id="33443-126">I det här exemplet körs kommandon 16 till och med 24.</span><span class="sxs-lookup"><span data-stu-id="33443-126">This example runs commands 16 through 24.</span></span> <span data-ttu-id="33443-127">Eftersom du bara kan lista ett **ID-** värde använder kommandot `ForEach-Object` cmdleten för att köra `Invoke-History` kommandot en tid för varje **ID-** värde.</span><span class="sxs-lookup"><span data-stu-id="33443-127">Because you can list only one **Id** value, the command uses the `ForEach-Object` cmdlet to run the `Invoke-History` command one time for each **Id** value.</span></span>

```powershell
16..24 | ForEach {Invoke-History -Id $_ }
```

### <span data-ttu-id="33443-128">Exempel 5</span><span class="sxs-lookup"><span data-stu-id="33443-128">Example 5</span></span>

<span data-ttu-id="33443-129">I det här exemplet körs sju kommandon i den historik som slutar med kommandot 255 (249 till 255).</span><span class="sxs-lookup"><span data-stu-id="33443-129">This example runs the seven commands in the history that end with command 255 (249 through 255).</span></span> <span data-ttu-id="33443-130">Den använder `Get-History` cmdleten för att hämta kommandon.</span><span class="sxs-lookup"><span data-stu-id="33443-130">It uses the `Get-History` cmdlet to retrieve the commands.</span></span> <span data-ttu-id="33443-131">Eftersom du bara kan lista ett **ID-** värde använder kommandot `ForEach-Object` cmdleten för att köra `Invoke-History` kommandot en gång för varje **ID-** värde.</span><span class="sxs-lookup"><span data-stu-id="33443-131">Because you can list only one **Id** value, the command uses the `ForEach-Object` cmdlet to run the `Invoke-History` command once for each **Id** value.</span></span>

```powershell
Get-History -Id 255 -Count 7 | ForEach {Invoke-History -Id $_.Id}
```

## <span data-ttu-id="33443-132">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="33443-132">PARAMETERS</span></span>

### <span data-ttu-id="33443-133">-ID</span><span class="sxs-lookup"><span data-stu-id="33443-133">-Id</span></span>

<span data-ttu-id="33443-134">Anger **ID** för ett kommando i historiken.</span><span class="sxs-lookup"><span data-stu-id="33443-134">Specifies the **Id** of a command in the history.</span></span> <span data-ttu-id="33443-135">Du kan ange **ID-** numret för kommandot eller de första tecknen i kommandot.</span><span class="sxs-lookup"><span data-stu-id="33443-135">You can type the **Id** number of the command or the first few characters of the command.</span></span>

<span data-ttu-id="33443-136">Om du skriver tecken `Invoke-History` matchar de senaste kommandona först.</span><span class="sxs-lookup"><span data-stu-id="33443-136">If you type characters, `Invoke-History` matches the most recent commands first.</span></span> <span data-ttu-id="33443-137">Om du utelämnar den här parametern `Invoke-History` körs det senaste eller senaste kommandot.</span><span class="sxs-lookup"><span data-stu-id="33443-137">If you omit this parameter, `Invoke-History` runs the last, or most recent, command.</span></span> <span data-ttu-id="33443-138">Använd cmdleten för att hitta **ID-** numret för ett kommando `Get-History` .</span><span class="sxs-lookup"><span data-stu-id="33443-138">To find the **Id** number of a command, use the `Get-History` cmdlet.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="33443-139">-Confirm</span><span class="sxs-lookup"><span data-stu-id="33443-139">-Confirm</span></span>

<span data-ttu-id="33443-140">Uppmanar dig att bekräfta innan du kör cmdleten.</span><span class="sxs-lookup"><span data-stu-id="33443-140">Prompts you for confirmation before running the cmdlet.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="33443-141">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="33443-141">-WhatIf</span></span>

<span data-ttu-id="33443-142">Visar vad som skulle hända om cmdleten kördes.</span><span class="sxs-lookup"><span data-stu-id="33443-142">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="33443-143">Cmdleten körs inte.</span><span class="sxs-lookup"><span data-stu-id="33443-143">The cmdlet is not run.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: wi

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="33443-144">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="33443-144">CommonParameters</span></span>

<span data-ttu-id="33443-145">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="33443-145">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="33443-146">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="33443-146">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="33443-147">INDATA</span><span class="sxs-lookup"><span data-stu-id="33443-147">INPUTS</span></span>

### <span data-ttu-id="33443-148">System. String</span><span class="sxs-lookup"><span data-stu-id="33443-148">System.String</span></span>

<span data-ttu-id="33443-149">Du kan skicka vidare ett historik **-ID** till denna cmdlet.</span><span class="sxs-lookup"><span data-stu-id="33443-149">You can pipe a history **Id** to this cmdlet.</span></span>

## <span data-ttu-id="33443-150">UTDATA</span><span class="sxs-lookup"><span data-stu-id="33443-150">OUTPUTS</span></span>

### <span data-ttu-id="33443-151">Inga</span><span class="sxs-lookup"><span data-stu-id="33443-151">None</span></span>

<span data-ttu-id="33443-152">Denna cmdlet genererar inga utdata, men utdata kan genereras av de kommandon som `Invoke-History` körs.</span><span class="sxs-lookup"><span data-stu-id="33443-152">This cmdlet does not generate any output, but output might be generated by the commands that `Invoke-History` runs.</span></span>

## <span data-ttu-id="33443-153">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="33443-153">NOTES</span></span>

<span data-ttu-id="33443-154">Tidigare session är en lista över kommandon som anges under sessionen.</span><span class="sxs-lookup"><span data-stu-id="33443-154">The session history is a list of the commands entered during the session.</span></span> <span data-ttu-id="33443-155">Tidigare sessioner representerar körnings ordning, status och start-och slut tid för kommandot.</span><span class="sxs-lookup"><span data-stu-id="33443-155">The session history represents the order of execution, the status, and the start and end times of the command.</span></span> <span data-ttu-id="33443-156">När du anger varje kommando lägger PowerShell till det i historiken så att du kan återanvända det.</span><span class="sxs-lookup"><span data-stu-id="33443-156">As you enter each command, PowerShell adds it to the history so that you can reuse it.</span></span> <span data-ttu-id="33443-157">Mer information om tidigare sessioner finns [about_History](About/about_History.md).</span><span class="sxs-lookup"><span data-stu-id="33443-157">For more information about the session history, see [about_History](About/about_History.md).</span></span>

<span data-ttu-id="33443-158">Du kan också referera till `Invoke-History` med inbyggda alias `r` och `ihy` .</span><span class="sxs-lookup"><span data-stu-id="33443-158">You can also refer to `Invoke-History` by its built-in aliases, `r` and `ihy`.</span></span> <span data-ttu-id="33443-159">Mer information finns i [about_Aliases](About/about_Aliases.md).</span><span class="sxs-lookup"><span data-stu-id="33443-159">For more information, see [about_Aliases](About/about_Aliases.md).</span></span>

## <span data-ttu-id="33443-160">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="33443-160">RELATED LINKS</span></span>

[<span data-ttu-id="33443-161">Lägg till-historik</span><span class="sxs-lookup"><span data-stu-id="33443-161">Add-History</span></span>](Add-History.md)

[<span data-ttu-id="33443-162">Rensa – historik</span><span class="sxs-lookup"><span data-stu-id="33443-162">Clear-History</span></span>](Clear-History.md)

[<span data-ttu-id="33443-163">Hämta historik</span><span class="sxs-lookup"><span data-stu-id="33443-163">Get-History</span></span>](Get-History.md)

