---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 02/04/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/pop-location?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Pop-Location
ms.openlocfilehash: 8a44849f27de80ece486b573f1adccafab51972a
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94710201"
---
# <span data-ttu-id="fb3ad-102">Pop-Location</span><span class="sxs-lookup"><span data-stu-id="fb3ad-102">Pop-Location</span></span>

## <span data-ttu-id="fb3ad-103">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="fb3ad-103">SYNOPSIS</span></span>
<span data-ttu-id="fb3ad-104">Ändrar den aktuella platsen till den plats som senast flyttades till stacken.</span><span class="sxs-lookup"><span data-stu-id="fb3ad-104">Changes the current location to the location most recently pushed onto the stack.</span></span>

## <span data-ttu-id="fb3ad-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="fb3ad-105">SYNTAX</span></span>

```
Pop-Location [-PassThru] [-StackName <String>] [<CommonParameters>]
```

## <span data-ttu-id="fb3ad-106">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="fb3ad-106">DESCRIPTION</span></span>

<span data-ttu-id="fb3ad-107">`Pop-Location`Cmdleten ändrar den aktuella platsen till den plats som senast skickas till stacken med hjälp av `Push-Location` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="fb3ad-107">The `Pop-Location` cmdlet changes the current location to the location most recently pushed onto the stack by using the `Push-Location` cmdlet.</span></span> <span data-ttu-id="fb3ad-108">Du kan pop en plats från standard stacken eller från en stack som du skapar med hjälp av ett `Push-Location` kommando.</span><span class="sxs-lookup"><span data-stu-id="fb3ad-108">You can pop a location from the default stack or from a stack that you create by using a `Push-Location` command.</span></span>

## <span data-ttu-id="fb3ad-109">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="fb3ad-109">EXAMPLES</span></span>

### <span data-ttu-id="fb3ad-110">Exempel 1: ändra till den senaste platsen</span><span class="sxs-lookup"><span data-stu-id="fb3ad-110">Example 1: Change to most recent location</span></span>

```
PS C:\> Pop-Location
```

<span data-ttu-id="fb3ad-111">Det här kommandot ändrar platsen till den plats som senast lades till i den aktuella stacken.</span><span class="sxs-lookup"><span data-stu-id="fb3ad-111">This command changes your location to the location most recently added to the current stack.</span></span>

### <span data-ttu-id="fb3ad-112">Exempel 2: ändra till den senaste platsen i en namngiven stack</span><span class="sxs-lookup"><span data-stu-id="fb3ad-112">Example 2: Change to most recent location in a named stack</span></span>

```
PS C:\> Pop-Location -StackName "Stack2"
```

<span data-ttu-id="fb3ad-113">Det här kommandot ändrar platsen till den plats som senast lades till i Stack2-platsens stack.</span><span class="sxs-lookup"><span data-stu-id="fb3ad-113">This command changes your location to the location most recently added to the Stack2 location stack.</span></span>

<span data-ttu-id="fb3ad-114">Mer information om plats stackar finns i [anteckningarna](#notes).</span><span class="sxs-lookup"><span data-stu-id="fb3ad-114">For more information about location stacks, see the [Notes](#notes).</span></span>

### <span data-ttu-id="fb3ad-115">Exempel 3: flytta mellan platser för olika providrar</span><span class="sxs-lookup"><span data-stu-id="fb3ad-115">Example 3: Move between locations for different providers</span></span>

```
PS C:\> pushd HKLM:\Software\Microsoft\PowerShell
PS HKLM:\Software\Microsoft\PowerShell> pushd Cert:\LocalMachine\TrustedPublisher
PS cert:\LocalMachine\TrustedPublisher> popd
PS HKLM:\Software\Microsoft\PowerShell> popd
PS C:\>
```

<span data-ttu-id="fb3ad-116">Dessa kommandon använder `Push-Location` `Pop-Location` cmdletarna och för att flytta mellan platser som stöds av olika PowerShell-leverantörer.</span><span class="sxs-lookup"><span data-stu-id="fb3ad-116">These commands use the `Push-Location` and `Pop-Location` cmdlets to move between locations supported by different PowerShell providers.</span></span> <span data-ttu-id="fb3ad-117">Kommandona använder `pushd` aliaset för `Push-Location` och `popd` aliaset för `Pop-Location` .</span><span class="sxs-lookup"><span data-stu-id="fb3ad-117">The commands use the `pushd` alias for `Push-Location` and the `popd` alias for `Pop-Location`.</span></span>

<span data-ttu-id="fb3ad-118">Det första kommandot push-överför den aktuella fil system platsen till stacken och flyttas till den HKLM-enhet som stöds av PowerShell-providern.</span><span class="sxs-lookup"><span data-stu-id="fb3ad-118">The first command pushes the current file system location onto the stack and moves to the HKLM drive supported by the PowerShell Registry provider.</span></span>

<span data-ttu-id="fb3ad-119">Det andra kommandot push-överför register platsen till stacken och flyttas till en plats som stöds av PowerShell-certifikat leverantören.</span><span class="sxs-lookup"><span data-stu-id="fb3ad-119">The second command pushes the registry location onto the stack and moves to a location supported by the PowerShell certificate provider.</span></span>

<span data-ttu-id="fb3ad-120">De två sista kommandona pop-bort dessa platser från stacken.</span><span class="sxs-lookup"><span data-stu-id="fb3ad-120">The last two commands pop those locations off the stack.</span></span> <span data-ttu-id="fb3ad-121">Det första `popd` kommandot återgår till register enheten och det andra kommandot återgår till fil system enheten.</span><span class="sxs-lookup"><span data-stu-id="fb3ad-121">The first `popd` command returns to the Registry drive, and the second command returns to the file system drive.</span></span>

## <span data-ttu-id="fb3ad-122">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="fb3ad-122">PARAMETERS</span></span>

### <span data-ttu-id="fb3ad-123">– PassThru</span><span class="sxs-lookup"><span data-stu-id="fb3ad-123">-PassThru</span></span>

<span data-ttu-id="fb3ad-124">Skickar ett objekt som representerar platsen för pipelinen.</span><span class="sxs-lookup"><span data-stu-id="fb3ad-124">Passes an object that represents the location to the pipeline.</span></span> <span data-ttu-id="fb3ad-125">Som standard genererar denna cmdlet inga utdata.</span><span class="sxs-lookup"><span data-stu-id="fb3ad-125">By default, this cmdlet does not generate any output.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="fb3ad-126">-StackName</span><span class="sxs-lookup"><span data-stu-id="fb3ad-126">-StackName</span></span>

<span data-ttu-id="fb3ad-127">Anger den plats stack från vilken platsen visas.</span><span class="sxs-lookup"><span data-stu-id="fb3ad-127">Specifies the location stack from which the location is popped.</span></span> <span data-ttu-id="fb3ad-128">Ange ett plats stack namn.</span><span class="sxs-lookup"><span data-stu-id="fb3ad-128">Enter a location stack name.</span></span>

<span data-ttu-id="fb3ad-129">Utan den här parametern får `Pop-Location` pop en plats från den aktuella plats stacken.</span><span class="sxs-lookup"><span data-stu-id="fb3ad-129">Without this parameter, `Pop-Location` pops a location from the current location stack.</span></span> <span data-ttu-id="fb3ad-130">Som standard är den aktuella plats stacken den namnlösa standard plats stacken som PowerShell skapar.</span><span class="sxs-lookup"><span data-stu-id="fb3ad-130">By default, the current location stack is the unnamed default location stack that PowerShell creates.</span></span> <span data-ttu-id="fb3ad-131">Om du vill skapa en plats stack för den aktuella plats stacken använder du parametern **StackName** för `Set-Location` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="fb3ad-131">To make a location stack the current location stack, use the **StackName** parameter of the `Set-Location` cmdlet.</span></span> <span data-ttu-id="fb3ad-132">Mer information om plats stackar finns i [anteckningarna](#notes).</span><span class="sxs-lookup"><span data-stu-id="fb3ad-132">For more information about location stacks, see the [Notes](#notes).</span></span>

<span data-ttu-id="fb3ad-133">`Pop-Location` Det går inte att popupa en plats från den namnlösa standard stacken om den inte är den aktuella plats stacken.</span><span class="sxs-lookup"><span data-stu-id="fb3ad-133">`Pop-Location` cannot pop a location from the unnamed default stack unless it is the current location stack.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="fb3ad-134">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="fb3ad-134">CommonParameters</span></span>

<span data-ttu-id="fb3ad-135">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="fb3ad-135">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="fb3ad-136">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="fb3ad-136">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="fb3ad-137">INDATA</span><span class="sxs-lookup"><span data-stu-id="fb3ad-137">INPUTS</span></span>

### <span data-ttu-id="fb3ad-138">Inga</span><span class="sxs-lookup"><span data-stu-id="fb3ad-138">None</span></span>

<span data-ttu-id="fb3ad-139">Du kan inte skicka pipe-ininformation till denna cmdlet.</span><span class="sxs-lookup"><span data-stu-id="fb3ad-139">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="fb3ad-140">UTDATA</span><span class="sxs-lookup"><span data-stu-id="fb3ad-140">OUTPUTS</span></span>

### <span data-ttu-id="fb3ad-141">Ingen, system. Management. Automation. PathInfo</span><span class="sxs-lookup"><span data-stu-id="fb3ad-141">None, System.Management.Automation.PathInfo</span></span>

<span data-ttu-id="fb3ad-142">Denna cmdlet skapar ett **system. Management. Automation. PathInfo** -objekt som representerar platsen, om du anger parametern **Passthru** .</span><span class="sxs-lookup"><span data-stu-id="fb3ad-142">This cmdlet generates a **System.Management.Automation.PathInfo** object that represents the location, if you specify the **PassThru** parameter.</span></span> <span data-ttu-id="fb3ad-143">Annars genererar denna cmdlet inga utdata.</span><span class="sxs-lookup"><span data-stu-id="fb3ad-143">Otherwise, this cmdlet does not generate any output.</span></span>

## <span data-ttu-id="fb3ad-144">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="fb3ad-144">NOTES</span></span>

<span data-ttu-id="fb3ad-145">PowerShell stöder flera körnings utrymmen per process.</span><span class="sxs-lookup"><span data-stu-id="fb3ad-145">PowerShell supports multiple runspaces per process.</span></span> <span data-ttu-id="fb3ad-146">Varje körnings utrymme har sin egen _aktuella katalog_.</span><span class="sxs-lookup"><span data-stu-id="fb3ad-146">Each runspace has its own _current directory_.</span></span>
<span data-ttu-id="fb3ad-147">Detta är inte samma som `[System.Environment]::CurrentDirectory` .</span><span class="sxs-lookup"><span data-stu-id="fb3ad-147">This is not the same as `[System.Environment]::CurrentDirectory`.</span></span> <span data-ttu-id="fb3ad-148">Det här problemet kan vara ett problem när du anropar .NET-API: er eller kör ursprungliga program utan att ange explicita katalog Sök vägar.</span><span class="sxs-lookup"><span data-stu-id="fb3ad-148">This behavior can be an issue when calling .NET APIs or running native applications without providing explicit directory paths.</span></span>

<span data-ttu-id="fb3ad-149">Även om plats-cmdletarna har angett den aktuella katalogen för hela processen, är du inte beroende av den eftersom en annan körnings utrymme kan ändra den när som helst.</span><span class="sxs-lookup"><span data-stu-id="fb3ad-149">Even if the location cmdlets did set the process-wide current directory, you can't depend on it because another runspace might change it at any time.</span></span> <span data-ttu-id="fb3ad-150">Du bör använda plats-cmdletar för att utföra vägbaserade åtgärder med hjälp av den aktuella arbets katalogen som är unik för den aktuella körnings utrymme.</span><span class="sxs-lookup"><span data-stu-id="fb3ad-150">You should use the location cmdlets to perform path-based operations using the current working directory specific to the current runspace.</span></span>

<span data-ttu-id="fb3ad-151">En stack är en sista ingångs lista i som endast det objekt som lagts till senast lades till.</span><span class="sxs-lookup"><span data-stu-id="fb3ad-151">A stack is a last-in, first-out list in which only the most recently added item can be accessed.</span></span> <span data-ttu-id="fb3ad-152">Du lägger till objekt i en stack i den ordning som du använder dem och hämtar dem sedan för användning i omvänd ordning.</span><span class="sxs-lookup"><span data-stu-id="fb3ad-152">You add items to a stack in the order that you use them, and then retrieve them for use in the reverse order.</span></span> <span data-ttu-id="fb3ad-153">Med PowerShell kan du lagra leverantörs platser i plats stackar.</span><span class="sxs-lookup"><span data-stu-id="fb3ad-153">PowerShell lets you store provider locations in location stacks.</span></span>

<span data-ttu-id="fb3ad-154">PowerShell skapar en namnlös standard plats stack och du kan skapa flera namngivna plats stackar.</span><span class="sxs-lookup"><span data-stu-id="fb3ad-154">PowerShell creates an unnamed default location stack and you can create multiple named location stacks.</span></span> <span data-ttu-id="fb3ad-155">Om du inte anger något stack namn använder PowerShell den aktuella plats stacken.</span><span class="sxs-lookup"><span data-stu-id="fb3ad-155">If you do not specify a stack name, PowerShell uses the current location stack.</span></span> <span data-ttu-id="fb3ad-156">Som standard är den namnlösa standard platsen den aktuella plats stacken, men du kan använda `Set-Location` cmdleten för att ändra den aktuella plats stacken.</span><span class="sxs-lookup"><span data-stu-id="fb3ad-156">By default, the unnamed default location is the current location stack, but you can use the `Set-Location` cmdlet to change the current location stack.</span></span>

<span data-ttu-id="fb3ad-157">Om du vill hantera plats stackar använder du PowerShell `*-Location` -cmdletarna enligt följande:</span><span class="sxs-lookup"><span data-stu-id="fb3ad-157">To manage location stacks, use the PowerShell `*-Location` cmdlets, as follows:</span></span>

- <span data-ttu-id="fb3ad-158">Om du vill lägga till en plats i en plats stack använder du `Push-Location` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="fb3ad-158">To add a location to a location stack, use the `Push-Location` cmdlet.</span></span>

- <span data-ttu-id="fb3ad-159">Använd cmdleten för att hämta en plats från en plats stack `Pop-Location` .</span><span class="sxs-lookup"><span data-stu-id="fb3ad-159">To get a location from a location stack, use the `Pop-Location` cmdlet.</span></span>

- <span data-ttu-id="fb3ad-160">Om du vill visa platserna i den aktuella platsens stack, använder du cmdlet-parametern **stack** `Get-Location` .</span><span class="sxs-lookup"><span data-stu-id="fb3ad-160">To display the locations in the current location stack, use the **Stack** parameter of the `Get-Location` cmdlet.</span></span>

- <span data-ttu-id="fb3ad-161">Om du vill visa platserna i en namngiven plats stack använder du parametern **StackName** för `Get-Location` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="fb3ad-161">To display the locations in a named location stack, use the **StackName** parameter of the `Get-Location` cmdlet.</span></span>

- <span data-ttu-id="fb3ad-162">Om du vill skapa en ny plats stack använder du parametern **StackName** för `Push-Location` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="fb3ad-162">To create a new location stack, use the **StackName** parameter of the `Push-Location` cmdlet.</span></span> <span data-ttu-id="fb3ad-163">Om du anger en stack som inte finns `Push-Location` skapar stacken.</span><span class="sxs-lookup"><span data-stu-id="fb3ad-163">If you specify a stack that does not exist, `Push-Location` creates the stack.</span></span>

- <span data-ttu-id="fb3ad-164">Om du vill skapa en plats stack för den aktuella plats stacken använder du parametern **StackName** för `Set-Location` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="fb3ad-164">To make a location stack the current location stack, use the **StackName** parameter of the `Set-Location` cmdlet.</span></span>

<span data-ttu-id="fb3ad-165">Den namnlösa standard plats stacken är endast tillgänglig när den är den aktuella plats stacken.</span><span class="sxs-lookup"><span data-stu-id="fb3ad-165">The unnamed default location stack is fully accessible only when it is the current location stack.</span></span>
<span data-ttu-id="fb3ad-166">Om du skapar en namngiven plats stack för den aktuella plats stacken kan du inte längre använda `Push-Location` `Pop-Location` cmdletarna eller för att lägga till eller hämta objekt från standard stacken eller `Get-Location` använda cmdleten för att Visa platserna i den namnlösa stacken.</span><span class="sxs-lookup"><span data-stu-id="fb3ad-166">If you make a named location stack the current location stack, you can no longer use the `Push-Location` or `Pop-Location` cmdlets to add or get items from the default stack or use the `Get-Location` cmdlet to display the locations in the unnamed stack.</span></span> <span data-ttu-id="fb3ad-167">Om du vill göra den namnlösa stacken till den aktuella stacken använder du parametern **StackName** för `Set-Location` cmdleten med värdet `$Null` eller en tom sträng ( `""` ).</span><span class="sxs-lookup"><span data-stu-id="fb3ad-167">To make the unnamed stack the current stack, use the **StackName** parameter of the `Set-Location` cmdlet with a value of `$Null` or an empty string (`""`).</span></span>

<span data-ttu-id="fb3ad-168">Du kan också referera till `Pop-Location` med dess inbyggda alias `popd` .</span><span class="sxs-lookup"><span data-stu-id="fb3ad-168">You can also refer to `Pop-Location` by its built-in alias, `popd`.</span></span> <span data-ttu-id="fb3ad-169">Mer information finns i [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md).</span><span class="sxs-lookup"><span data-stu-id="fb3ad-169">For more information, see [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md).</span></span>

<span data-ttu-id="fb3ad-170">`Pop-Location` är utformad för att fungera med data som exponeras av vilken provider som helst.</span><span class="sxs-lookup"><span data-stu-id="fb3ad-170">`Pop-Location` is designed to work with the data exposed by any provider.</span></span> <span data-ttu-id="fb3ad-171">Om du vill visa en lista över tillgängliga providers i din session skriver du `Get-PSProvider` .</span><span class="sxs-lookup"><span data-stu-id="fb3ad-171">To list the providers available in your session, type `Get-PSProvider`.</span></span> <span data-ttu-id="fb3ad-172">Mer information finns i [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span><span class="sxs-lookup"><span data-stu-id="fb3ad-172">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

## <span data-ttu-id="fb3ad-173">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="fb3ad-173">RELATED LINKS</span></span>

[<span data-ttu-id="fb3ad-174">Get-location</span><span class="sxs-lookup"><span data-stu-id="fb3ad-174">Get-Location</span></span>](Get-Location.md)

[<span data-ttu-id="fb3ad-175">Push-plats</span><span class="sxs-lookup"><span data-stu-id="fb3ad-175">Push-Location</span></span>](Push-Location.md)

[<span data-ttu-id="fb3ad-176">Ange plats</span><span class="sxs-lookup"><span data-stu-id="fb3ad-176">Set-Location</span></span>](Set-Location.md)

[<span data-ttu-id="fb3ad-177">about_Aliases</span><span class="sxs-lookup"><span data-stu-id="fb3ad-177">about_Aliases</span></span>](../Microsoft.PowerShell.Core/About/about_Aliases.md)

[<span data-ttu-id="fb3ad-178">about_Providers</span><span class="sxs-lookup"><span data-stu-id="fb3ad-178">about_Providers</span></span>](../Microsoft.PowerShell.Core/About/about_Providers.md)
