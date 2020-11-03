---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 05/13/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/invoke-history?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Invoke-History
ms.openlocfilehash: 6745ceb3e6106bacf45d0c20fc916951316139dc
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93266894"
---
# <span data-ttu-id="1a196-103">Invoke-History</span><span class="sxs-lookup"><span data-stu-id="1a196-103">Invoke-History</span></span>

## <span data-ttu-id="1a196-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="1a196-104">SYNOPSIS</span></span>
<span data-ttu-id="1a196-105">Kör kommandon från tidigare sessioner.</span><span class="sxs-lookup"><span data-stu-id="1a196-105">Runs commands from the session history.</span></span>

## <span data-ttu-id="1a196-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="1a196-106">SYNTAX</span></span>

```
Invoke-History [[-Id] <String>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="1a196-107">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="1a196-107">DESCRIPTION</span></span>

<span data-ttu-id="1a196-108">`Invoke-History`Cmdleten kör kommandon från tidigare sessioner.</span><span class="sxs-lookup"><span data-stu-id="1a196-108">The `Invoke-History` cmdlet runs commands from the session history.</span></span> <span data-ttu-id="1a196-109">Du kan skicka objekt som representerar kommandona från Get-History till `Invoke-History` , eller så kan du identifiera kommandon i den aktuella historiken med hjälp av deras **ID-** nummer.</span><span class="sxs-lookup"><span data-stu-id="1a196-109">You can pass objects representing the commands from Get-History to `Invoke-History`, or you can identify commands in the current history by using their **Id** number.</span></span> <span data-ttu-id="1a196-110">Använd cmdleten för att hitta identifikations numret för ett kommando `Get-History` .</span><span class="sxs-lookup"><span data-stu-id="1a196-110">To find the identification number of a command, use the `Get-History` cmdlet.</span></span>

<span data-ttu-id="1a196-111">Historiken för sessionen hanteras separat från historiken som underhålls av **PSReadLine** -modulen.</span><span class="sxs-lookup"><span data-stu-id="1a196-111">The session history is managed separately from the history maintained by the **PSReadLine** module.</span></span>
<span data-ttu-id="1a196-112">Båda historiken är tillgängliga i sessioner där **PSReadLine** har lästs in.</span><span class="sxs-lookup"><span data-stu-id="1a196-112">Both histories are available in sessions where **PSReadLine** is loaded.</span></span> <span data-ttu-id="1a196-113">Den här cmdleten fungerar bara med tidigare session.</span><span class="sxs-lookup"><span data-stu-id="1a196-113">This cmdlet only works with the session history.</span></span> <span data-ttu-id="1a196-114">Mer information finns i [about_PSReadLine](../PSReadLine/About/about_PSReadLine.md).</span><span class="sxs-lookup"><span data-stu-id="1a196-114">For more information see, [about_PSReadLine](../PSReadLine/About/about_PSReadLine.md).</span></span>

## <span data-ttu-id="1a196-115">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="1a196-115">EXAMPLES</span></span>

### <span data-ttu-id="1a196-116">Exempel 1: kör det senaste kommandot i historiken</span><span class="sxs-lookup"><span data-stu-id="1a196-116">Example 1: Run the most recent command in the history</span></span>

<span data-ttu-id="1a196-117">I det här exemplet körs det senaste eller senaste kommandot i tidigare session.</span><span class="sxs-lookup"><span data-stu-id="1a196-117">This example runs the last, or most recent, command in the session history.</span></span> <span data-ttu-id="1a196-118">Du kan förkorta det här kommandot som `r` alias för `Invoke-History` .</span><span class="sxs-lookup"><span data-stu-id="1a196-118">You can abbreviate this command as `r`, the alias for `Invoke-History`.</span></span>

```powershell
Invoke-History
```

### <span data-ttu-id="1a196-119">Exempel 2: kör kommandot som har ett angivet ID</span><span class="sxs-lookup"><span data-stu-id="1a196-119">Example 2: Run the command that has a specified ID</span></span>

<span data-ttu-id="1a196-120">I det här exemplet körs kommandot i sessionen med **Id** 132.</span><span class="sxs-lookup"><span data-stu-id="1a196-120">This example runs the command in the session history with **Id** 132.</span></span> <span data-ttu-id="1a196-121">Eftersom namnet på **ID-** parametern är valfri kan du förkorta det här kommandot med följande: `Invoke-History 132` , `ihy 132` eller `r 132` .</span><span class="sxs-lookup"><span data-stu-id="1a196-121">Because the name of the **Id** parameter is optional, you can abbreviate this command as the following: `Invoke-History 132`, `ihy 132`, or `r 132`.</span></span>

```powershell
Invoke-History -Id 132
```

### <span data-ttu-id="1a196-122">Exempel 3: kör det senaste kommandot med hjälp av kommando texten</span><span class="sxs-lookup"><span data-stu-id="1a196-122">Example 3: Run the most recent command by using the command text</span></span>

<span data-ttu-id="1a196-123">I det här exemplet körs det senaste `Get-Process` kommandot i tidigare sessioner.</span><span class="sxs-lookup"><span data-stu-id="1a196-123">This example runs the most recent `Get-Process` command in the session history.</span></span> <span data-ttu-id="1a196-124">När du skriver tecken för **ID-** parametern `Invoke-History` Kör det första kommandot som den hittar som matchar mönstret, med början av de senaste kommandona.</span><span class="sxs-lookup"><span data-stu-id="1a196-124">When you type characters for the **Id** parameter, `Invoke-History` runs the first command that it finds that matches the pattern, starting with the most recent commands.</span></span>

```powershell
Invoke-History -Id get-pr
```

> [!NOTE]
> <span data-ttu-id="1a196-125">Mönster matchning är Skift läges känsligt, men mönstret matchar början av linjen.</span><span class="sxs-lookup"><span data-stu-id="1a196-125">Pattern matching is case-insensitive, but the pattern matches the beginning of the line.</span></span>

### <span data-ttu-id="1a196-126">Exempel 4: kör en sekvens med kommandon från historiken</span><span class="sxs-lookup"><span data-stu-id="1a196-126">Example 4: Run a sequence of commands from the history</span></span>

<span data-ttu-id="1a196-127">I det här exemplet körs kommandon 16 till och med 24.</span><span class="sxs-lookup"><span data-stu-id="1a196-127">This example runs commands 16 through 24.</span></span> <span data-ttu-id="1a196-128">Eftersom du bara kan lista ett **ID-** värde använder kommandot `ForEach-Object` cmdleten för att köra `Invoke-History` kommandot en tid för varje **ID-** värde.</span><span class="sxs-lookup"><span data-stu-id="1a196-128">Because you can list only one **Id** value, the command uses the `ForEach-Object` cmdlet to run the `Invoke-History` command one time for each **Id** value.</span></span>

```powershell
16..24 | ForEach {Invoke-History -Id $_ }
```

### <span data-ttu-id="1a196-129">Exempel 5</span><span class="sxs-lookup"><span data-stu-id="1a196-129">Example 5</span></span>

<span data-ttu-id="1a196-130">I det här exemplet körs sju kommandon i den historik som slutar med kommandot 255 (249 till 255).</span><span class="sxs-lookup"><span data-stu-id="1a196-130">This example runs the seven commands in the history that end with command 255 (249 through 255).</span></span> <span data-ttu-id="1a196-131">Den använder `Get-History` cmdleten för att hämta kommandon.</span><span class="sxs-lookup"><span data-stu-id="1a196-131">It uses the `Get-History` cmdlet to retrieve the commands.</span></span> <span data-ttu-id="1a196-132">Eftersom du bara kan lista ett **ID-** värde använder kommandot `ForEach-Object` cmdleten för att köra `Invoke-History` kommandot en gång för varje **ID-** värde.</span><span class="sxs-lookup"><span data-stu-id="1a196-132">Because you can list only one **Id** value, the command uses the `ForEach-Object` cmdlet to run the `Invoke-History` command once for each **Id** value.</span></span>

```powershell
Get-History -Id 255 -Count 7 | ForEach {Invoke-History -Id $_.Id}
```

## <span data-ttu-id="1a196-133">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="1a196-133">PARAMETERS</span></span>

### <span data-ttu-id="1a196-134">-ID</span><span class="sxs-lookup"><span data-stu-id="1a196-134">-Id</span></span>

<span data-ttu-id="1a196-135">Anger **ID** för ett kommando i historiken.</span><span class="sxs-lookup"><span data-stu-id="1a196-135">Specifies the **Id** of a command in the history.</span></span> <span data-ttu-id="1a196-136">Du kan ange **ID-** numret för kommandot eller de första tecknen i kommandot.</span><span class="sxs-lookup"><span data-stu-id="1a196-136">You can type the **Id** number of the command or the first few characters of the command.</span></span>

<span data-ttu-id="1a196-137">Om du skriver tecken `Invoke-History` matchar de senaste kommandona först.</span><span class="sxs-lookup"><span data-stu-id="1a196-137">If you type characters, `Invoke-History` matches the most recent commands first.</span></span> <span data-ttu-id="1a196-138">Om du utelämnar den här parametern `Invoke-History` körs det senaste eller senaste kommandot.</span><span class="sxs-lookup"><span data-stu-id="1a196-138">If you omit this parameter, `Invoke-History` runs the last, or most recent, command.</span></span> <span data-ttu-id="1a196-139">Använd cmdleten för att hitta **ID-** numret för ett kommando `Get-History` .</span><span class="sxs-lookup"><span data-stu-id="1a196-139">To find the **Id** number of a command, use the `Get-History` cmdlet.</span></span>

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

### <span data-ttu-id="1a196-140">-Confirm</span><span class="sxs-lookup"><span data-stu-id="1a196-140">-Confirm</span></span>

<span data-ttu-id="1a196-141">Uppmanar dig att bekräfta innan du kör cmdleten.</span><span class="sxs-lookup"><span data-stu-id="1a196-141">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="1a196-142">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="1a196-142">-WhatIf</span></span>

<span data-ttu-id="1a196-143">Visar vad som skulle hända om cmdleten kördes.</span><span class="sxs-lookup"><span data-stu-id="1a196-143">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="1a196-144">Cmdleten körs inte.</span><span class="sxs-lookup"><span data-stu-id="1a196-144">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="1a196-145">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="1a196-145">CommonParameters</span></span>

<span data-ttu-id="1a196-146">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="1a196-146">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="1a196-147">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="1a196-147">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="1a196-148">INDATA</span><span class="sxs-lookup"><span data-stu-id="1a196-148">INPUTS</span></span>

### <span data-ttu-id="1a196-149">System. String</span><span class="sxs-lookup"><span data-stu-id="1a196-149">System.String</span></span>

<span data-ttu-id="1a196-150">Du kan skicka vidare ett historik **-ID** till denna cmdlet.</span><span class="sxs-lookup"><span data-stu-id="1a196-150">You can pipe a history **Id** to this cmdlet.</span></span>

## <span data-ttu-id="1a196-151">UTDATA</span><span class="sxs-lookup"><span data-stu-id="1a196-151">OUTPUTS</span></span>

### <span data-ttu-id="1a196-152">Inget</span><span class="sxs-lookup"><span data-stu-id="1a196-152">None</span></span>

<span data-ttu-id="1a196-153">Denna cmdlet genererar inga utdata, men utdata kan genereras av de kommandon som `Invoke-History` körs.</span><span class="sxs-lookup"><span data-stu-id="1a196-153">This cmdlet does not generate any output, but output might be generated by the commands that `Invoke-History` runs.</span></span>

## <span data-ttu-id="1a196-154">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="1a196-154">NOTES</span></span>

<span data-ttu-id="1a196-155">Tidigare session är en lista över kommandon som anges under sessionen.</span><span class="sxs-lookup"><span data-stu-id="1a196-155">The session history is a list of the commands entered during the session.</span></span> <span data-ttu-id="1a196-156">Tidigare sessioner representerar körnings ordning, status och start-och slut tid för kommandot.</span><span class="sxs-lookup"><span data-stu-id="1a196-156">The session history represents the order of execution, the status, and the start and end times of the command.</span></span> <span data-ttu-id="1a196-157">När du anger varje kommando lägger PowerShell till det i historiken så att du kan återanvända det.</span><span class="sxs-lookup"><span data-stu-id="1a196-157">As you enter each command, PowerShell adds it to the history so that you can reuse it.</span></span> <span data-ttu-id="1a196-158">Mer information om tidigare sessioner finns [about_History](About/about_History.md).</span><span class="sxs-lookup"><span data-stu-id="1a196-158">For more information about the session history, see [about_History](About/about_History.md).</span></span>

<span data-ttu-id="1a196-159">Du kan också referera till `Invoke-History` med inbyggda alias `r` och `ihy` .</span><span class="sxs-lookup"><span data-stu-id="1a196-159">You can also refer to `Invoke-History` by its built-in aliases, `r` and `ihy`.</span></span> <span data-ttu-id="1a196-160">Mer information finns i [about_Aliases](About/about_Aliases.md).</span><span class="sxs-lookup"><span data-stu-id="1a196-160">For more information, see [about_Aliases](About/about_Aliases.md).</span></span>

## <span data-ttu-id="1a196-161">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="1a196-161">RELATED LINKS</span></span>

[<span data-ttu-id="1a196-162">Lägg till-historik</span><span class="sxs-lookup"><span data-stu-id="1a196-162">Add-History</span></span>](Add-History.md)

[<span data-ttu-id="1a196-163">Rensa – historik</span><span class="sxs-lookup"><span data-stu-id="1a196-163">Clear-History</span></span>](Clear-History.md)

[<span data-ttu-id="1a196-164">Hämta historik</span><span class="sxs-lookup"><span data-stu-id="1a196-164">Get-History</span></span>](Get-History.md)
