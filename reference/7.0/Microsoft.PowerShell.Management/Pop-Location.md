---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 02/04/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/pop-location?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Pop-Location
ms.openlocfilehash: 4f5dffdc942112672c3a193fd1fef49b3b5c15d6
ms.sourcegitcommit: 01a1c253f48b61c943f6d6aca4e603118014015f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/06/2020
ms.locfileid: "93268916"
---
# <span data-ttu-id="eba87-103">Pop-Location</span><span class="sxs-lookup"><span data-stu-id="eba87-103">Pop-Location</span></span>

## <span data-ttu-id="eba87-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="eba87-104">SYNOPSIS</span></span>
<span data-ttu-id="eba87-105">Ändrar den aktuella platsen till den plats som senast flyttades till stacken.</span><span class="sxs-lookup"><span data-stu-id="eba87-105">Changes the current location to the location most recently pushed onto the stack.</span></span>

## <span data-ttu-id="eba87-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="eba87-106">SYNTAX</span></span>

```
Pop-Location [-PassThru] [-StackName <String>] [<CommonParameters>]
```

## <span data-ttu-id="eba87-107">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="eba87-107">DESCRIPTION</span></span>

<span data-ttu-id="eba87-108">`Pop-Location`Cmdleten ändrar den aktuella platsen till den plats som senast skickas till stacken med hjälp av `Push-Location` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="eba87-108">The `Pop-Location` cmdlet changes the current location to the location most recently pushed onto the stack by using the `Push-Location` cmdlet.</span></span> <span data-ttu-id="eba87-109">Du kan pop en plats från standard stacken eller från en stack som du skapar med hjälp av ett `Push-Location` kommando.</span><span class="sxs-lookup"><span data-stu-id="eba87-109">You can pop a location from the default stack or from a stack that you create by using a `Push-Location` command.</span></span>

## <span data-ttu-id="eba87-110">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="eba87-110">EXAMPLES</span></span>

### <span data-ttu-id="eba87-111">Exempel 1: ändra till den senaste platsen</span><span class="sxs-lookup"><span data-stu-id="eba87-111">Example 1: Change to most recent location</span></span>

```
PS C:\> Pop-Location
```

<span data-ttu-id="eba87-112">Det här kommandot ändrar platsen till den plats som senast lades till i den aktuella stacken.</span><span class="sxs-lookup"><span data-stu-id="eba87-112">This command changes your location to the location most recently added to the current stack.</span></span>

### <span data-ttu-id="eba87-113">Exempel 2: ändra till den senaste platsen i en namngiven stack</span><span class="sxs-lookup"><span data-stu-id="eba87-113">Example 2: Change to most recent location in a named stack</span></span>

```
PS C:\> Pop-Location -StackName "Stack2"
```

<span data-ttu-id="eba87-114">Det här kommandot ändrar platsen till den plats som senast lades till i Stack2-platsens stack.</span><span class="sxs-lookup"><span data-stu-id="eba87-114">This command changes your location to the location most recently added to the Stack2 location stack.</span></span>

<span data-ttu-id="eba87-115">Mer information om plats stackar finns i [anteckningarna](#notes).</span><span class="sxs-lookup"><span data-stu-id="eba87-115">For more information about location stacks, see the [Notes](#notes).</span></span>

### <span data-ttu-id="eba87-116">Exempel 3: flytta mellan platser för olika providrar</span><span class="sxs-lookup"><span data-stu-id="eba87-116">Example 3: Move between locations for different providers</span></span>

```
PS C:\> pushd HKLM:\Software\Microsoft\PowerShell
PS HKLM:\Software\Microsoft\PowerShell> pushd Cert:\LocalMachine\TrustedPublisher
PS cert:\LocalMachine\TrustedPublisher> popd
PS HKLM:\Software\Microsoft\PowerShell> popd
PS C:\>
```

<span data-ttu-id="eba87-117">Dessa kommandon använder `Push-Location` `Pop-Location` cmdletarna och för att flytta mellan platser som stöds av olika PowerShell-leverantörer.</span><span class="sxs-lookup"><span data-stu-id="eba87-117">These commands use the `Push-Location` and `Pop-Location` cmdlets to move between locations supported by different PowerShell providers.</span></span> <span data-ttu-id="eba87-118">Kommandona använder `pushd` aliaset för `Push-Location` och `popd` aliaset för `Pop-Location` .</span><span class="sxs-lookup"><span data-stu-id="eba87-118">The commands use the `pushd` alias for `Push-Location` and the `popd` alias for `Pop-Location`.</span></span>

<span data-ttu-id="eba87-119">Det första kommandot push-överför den aktuella fil system platsen till stacken och flyttas till den HKLM-enhet som stöds av PowerShell-providern.</span><span class="sxs-lookup"><span data-stu-id="eba87-119">The first command pushes the current file system location onto the stack and moves to the HKLM drive supported by the PowerShell Registry provider.</span></span>

<span data-ttu-id="eba87-120">Det andra kommandot push-överför register platsen till stacken och flyttas till en plats som stöds av PowerShell-certifikat leverantören.</span><span class="sxs-lookup"><span data-stu-id="eba87-120">The second command pushes the registry location onto the stack and moves to a location supported by the PowerShell certificate provider.</span></span>

<span data-ttu-id="eba87-121">De två sista kommandona pop-bort dessa platser från stacken.</span><span class="sxs-lookup"><span data-stu-id="eba87-121">The last two commands pop those locations off the stack.</span></span> <span data-ttu-id="eba87-122">Det första `popd` kommandot återgår till register enheten och det andra kommandot återgår till fil system enheten.</span><span class="sxs-lookup"><span data-stu-id="eba87-122">The first `popd` command returns to the Registry drive, and the second command returns to the file system drive.</span></span>

## <span data-ttu-id="eba87-123">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="eba87-123">PARAMETERS</span></span>

### <span data-ttu-id="eba87-124">– PassThru</span><span class="sxs-lookup"><span data-stu-id="eba87-124">-PassThru</span></span>

<span data-ttu-id="eba87-125">Skickar ett objekt som representerar platsen för pipelinen.</span><span class="sxs-lookup"><span data-stu-id="eba87-125">Passes an object that represents the location to the pipeline.</span></span> <span data-ttu-id="eba87-126">Som standard genererar denna cmdlet inga utdata.</span><span class="sxs-lookup"><span data-stu-id="eba87-126">By default, this cmdlet does not generate any output.</span></span>

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

### <span data-ttu-id="eba87-127">-StackName</span><span class="sxs-lookup"><span data-stu-id="eba87-127">-StackName</span></span>

<span data-ttu-id="eba87-128">Anger den plats stack från vilken platsen visas.</span><span class="sxs-lookup"><span data-stu-id="eba87-128">Specifies the location stack from which the location is popped.</span></span> <span data-ttu-id="eba87-129">Ange ett plats stack namn.</span><span class="sxs-lookup"><span data-stu-id="eba87-129">Enter a location stack name.</span></span>

<span data-ttu-id="eba87-130">Utan den här parametern får `Pop-Location` pop en plats från den aktuella plats stacken.</span><span class="sxs-lookup"><span data-stu-id="eba87-130">Without this parameter, `Pop-Location` pops a location from the current location stack.</span></span> <span data-ttu-id="eba87-131">Som standard är den aktuella plats stacken den namnlösa standard plats stacken som PowerShell skapar.</span><span class="sxs-lookup"><span data-stu-id="eba87-131">By default, the current location stack is the unnamed default location stack that PowerShell creates.</span></span> <span data-ttu-id="eba87-132">Om du vill skapa en plats stack för den aktuella plats stacken använder du parametern **StackName** för `Set-Location` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="eba87-132">To make a location stack the current location stack, use the **StackName** parameter of the `Set-Location` cmdlet.</span></span> <span data-ttu-id="eba87-133">Mer information om plats stackar finns i [anteckningarna](#notes).</span><span class="sxs-lookup"><span data-stu-id="eba87-133">For more information about location stacks, see the [Notes](#notes).</span></span>

<span data-ttu-id="eba87-134">`Pop-Location` Det går inte att popupa en plats från den namnlösa standard stacken om den inte är den aktuella plats stacken.</span><span class="sxs-lookup"><span data-stu-id="eba87-134">`Pop-Location` cannot pop a location from the unnamed default stack unless it is the current location stack.</span></span>

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

### <span data-ttu-id="eba87-135">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="eba87-135">CommonParameters</span></span>

<span data-ttu-id="eba87-136">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="eba87-136">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="eba87-137">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="eba87-137">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="eba87-138">INDATA</span><span class="sxs-lookup"><span data-stu-id="eba87-138">INPUTS</span></span>

### <span data-ttu-id="eba87-139">Inget</span><span class="sxs-lookup"><span data-stu-id="eba87-139">None</span></span>

<span data-ttu-id="eba87-140">Du kan inte skicka pipe-ininformation till denna cmdlet.</span><span class="sxs-lookup"><span data-stu-id="eba87-140">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="eba87-141">UTDATA</span><span class="sxs-lookup"><span data-stu-id="eba87-141">OUTPUTS</span></span>

### <span data-ttu-id="eba87-142">Ingen, system. Management. Automation. PathInfo</span><span class="sxs-lookup"><span data-stu-id="eba87-142">None, System.Management.Automation.PathInfo</span></span>

<span data-ttu-id="eba87-143">Denna cmdlet skapar ett **system. Management. Automation. PathInfo** -objekt som representerar platsen, om du anger parametern **Passthru** .</span><span class="sxs-lookup"><span data-stu-id="eba87-143">This cmdlet generates a **System.Management.Automation.PathInfo** object that represents the location, if you specify the **PassThru** parameter.</span></span> <span data-ttu-id="eba87-144">Annars genererar denna cmdlet inga utdata.</span><span class="sxs-lookup"><span data-stu-id="eba87-144">Otherwise, this cmdlet does not generate any output.</span></span>

## <span data-ttu-id="eba87-145">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="eba87-145">NOTES</span></span>

<span data-ttu-id="eba87-146">PowerShell stöder flera körnings utrymmen per process.</span><span class="sxs-lookup"><span data-stu-id="eba87-146">PowerShell supports multiple runspaces per process.</span></span> <span data-ttu-id="eba87-147">Varje körnings utrymme har sin egen _aktuella katalog_.</span><span class="sxs-lookup"><span data-stu-id="eba87-147">Each runspace has its own _current directory_.</span></span>
<span data-ttu-id="eba87-148">Detta är inte samma som `[System.Environment]::CurrentDirectory` .</span><span class="sxs-lookup"><span data-stu-id="eba87-148">This is not the same as `[System.Environment]::CurrentDirectory`.</span></span> <span data-ttu-id="eba87-149">Det här problemet kan vara ett problem när du anropar .NET-API: er eller kör ursprungliga program utan att ange explicita katalog Sök vägar.</span><span class="sxs-lookup"><span data-stu-id="eba87-149">This behavior can be an issue when calling .NET APIs or running native applications without providing explicit directory paths.</span></span>

<span data-ttu-id="eba87-150">Även om plats-cmdletarna har angett den aktuella katalogen för hela processen, är du inte beroende av den eftersom en annan körnings utrymme kan ändra den när som helst.</span><span class="sxs-lookup"><span data-stu-id="eba87-150">Even if the location cmdlets did set the process-wide current directory, you can't depend on it because another runspace might change it at any time.</span></span> <span data-ttu-id="eba87-151">Du bör använda plats-cmdletar för att utföra vägbaserade åtgärder med hjälp av den aktuella arbets katalogen som är unik för den aktuella körnings utrymme.</span><span class="sxs-lookup"><span data-stu-id="eba87-151">You should use the location cmdlets to perform path-based operations using the current working directory specific to the current runspace.</span></span>

<span data-ttu-id="eba87-152">En stack är en sista ingångs lista i som endast det objekt som lagts till senast lades till.</span><span class="sxs-lookup"><span data-stu-id="eba87-152">A stack is a last-in, first-out list in which only the most recently added item can be accessed.</span></span> <span data-ttu-id="eba87-153">Du lägger till objekt i en stack i den ordning som du använder dem och hämtar dem sedan för användning i omvänd ordning.</span><span class="sxs-lookup"><span data-stu-id="eba87-153">You add items to a stack in the order that you use them, and then retrieve them for use in the reverse order.</span></span> <span data-ttu-id="eba87-154">Med PowerShell kan du lagra leverantörs platser i plats stackar.</span><span class="sxs-lookup"><span data-stu-id="eba87-154">PowerShell lets you store provider locations in location stacks.</span></span>

<span data-ttu-id="eba87-155">PowerShell skapar en namnlös standard plats stack och du kan skapa flera namngivna plats stackar.</span><span class="sxs-lookup"><span data-stu-id="eba87-155">PowerShell creates an unnamed default location stack and you can create multiple named location stacks.</span></span> <span data-ttu-id="eba87-156">Om du inte anger något stack namn använder PowerShell den aktuella plats stacken.</span><span class="sxs-lookup"><span data-stu-id="eba87-156">If you do not specify a stack name, PowerShell uses the current location stack.</span></span> <span data-ttu-id="eba87-157">Som standard är den namnlösa standard platsen den aktuella plats stacken, men du kan använda `Set-Location` cmdleten för att ändra den aktuella plats stacken.</span><span class="sxs-lookup"><span data-stu-id="eba87-157">By default, the unnamed default location is the current location stack, but you can use the `Set-Location` cmdlet to change the current location stack.</span></span>

<span data-ttu-id="eba87-158">Om du vill hantera plats stackar använder du PowerShell `*-Location` -cmdletarna enligt följande:</span><span class="sxs-lookup"><span data-stu-id="eba87-158">To manage location stacks, use the PowerShell `*-Location` cmdlets, as follows:</span></span>

- <span data-ttu-id="eba87-159">Om du vill lägga till en plats i en plats stack använder du `Push-Location` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="eba87-159">To add a location to a location stack, use the `Push-Location` cmdlet.</span></span>

- <span data-ttu-id="eba87-160">Använd cmdleten för att hämta en plats från en plats stack `Pop-Location` .</span><span class="sxs-lookup"><span data-stu-id="eba87-160">To get a location from a location stack, use the `Pop-Location` cmdlet.</span></span>

- <span data-ttu-id="eba87-161">Om du vill visa platserna i den aktuella platsens stack, använder du cmdlet-parametern **stack** `Get-Location` .</span><span class="sxs-lookup"><span data-stu-id="eba87-161">To display the locations in the current location stack, use the **Stack** parameter of the `Get-Location` cmdlet.</span></span>

- <span data-ttu-id="eba87-162">Om du vill visa platserna i en namngiven plats stack använder du parametern **StackName** för `Get-Location` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="eba87-162">To display the locations in a named location stack, use the **StackName** parameter of the `Get-Location` cmdlet.</span></span>

- <span data-ttu-id="eba87-163">Om du vill skapa en ny plats stack använder du parametern **StackName** för `Push-Location` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="eba87-163">To create a new location stack, use the **StackName** parameter of the `Push-Location` cmdlet.</span></span> <span data-ttu-id="eba87-164">Om du anger en stack som inte finns `Push-Location` skapar stacken.</span><span class="sxs-lookup"><span data-stu-id="eba87-164">If you specify a stack that does not exist, `Push-Location` creates the stack.</span></span>

- <span data-ttu-id="eba87-165">Om du vill skapa en plats stack för den aktuella plats stacken använder du parametern **StackName** för `Set-Location` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="eba87-165">To make a location stack the current location stack, use the **StackName** parameter of the `Set-Location` cmdlet.</span></span>

<span data-ttu-id="eba87-166">Den namnlösa standard plats stacken är endast tillgänglig när den är den aktuella plats stacken.</span><span class="sxs-lookup"><span data-stu-id="eba87-166">The unnamed default location stack is fully accessible only when it is the current location stack.</span></span>
<span data-ttu-id="eba87-167">Om du skapar en namngiven plats stack för den aktuella plats stacken kan du inte längre använda `Push-Location` `Pop-Location` cmdletarna eller för att lägga till eller hämta objekt från standard stacken eller `Get-Location` använda cmdleten för att Visa platserna i den namnlösa stacken.</span><span class="sxs-lookup"><span data-stu-id="eba87-167">If you make a named location stack the current location stack, you can no longer use the `Push-Location` or `Pop-Location` cmdlets to add or get items from the default stack or use the `Get-Location` cmdlet to display the locations in the unnamed stack.</span></span> <span data-ttu-id="eba87-168">Om du vill göra den namnlösa stacken till den aktuella stacken använder du parametern **StackName** för `Set-Location` cmdleten med värdet `$Null` eller en tom sträng ( `""` ).</span><span class="sxs-lookup"><span data-stu-id="eba87-168">To make the unnamed stack the current stack, use the **StackName** parameter of the `Set-Location` cmdlet with a value of `$Null` or an empty string (`""`).</span></span>

<span data-ttu-id="eba87-169">Du kan också referera till `Pop-Location` med dess inbyggda alias `popd` .</span><span class="sxs-lookup"><span data-stu-id="eba87-169">You can also refer to `Pop-Location` by its built-in alias, `popd`.</span></span> <span data-ttu-id="eba87-170">Mer information finns i [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md).</span><span class="sxs-lookup"><span data-stu-id="eba87-170">For more information, see [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md).</span></span>

<span data-ttu-id="eba87-171">`Pop-Location` är utformad för att fungera med data som exponeras av vilken provider som helst.</span><span class="sxs-lookup"><span data-stu-id="eba87-171">`Pop-Location` is designed to work with the data exposed by any provider.</span></span> <span data-ttu-id="eba87-172">Om du vill visa en lista över tillgängliga providers i din session skriver du `Get-PSProvider` .</span><span class="sxs-lookup"><span data-stu-id="eba87-172">To list the providers available in your session, type `Get-PSProvider`.</span></span> <span data-ttu-id="eba87-173">Mer information finns i [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span><span class="sxs-lookup"><span data-stu-id="eba87-173">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

## <span data-ttu-id="eba87-174">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="eba87-174">RELATED LINKS</span></span>

[<span data-ttu-id="eba87-175">Get-location</span><span class="sxs-lookup"><span data-stu-id="eba87-175">Get-Location</span></span>](Get-Location.md)

[<span data-ttu-id="eba87-176">Push-plats</span><span class="sxs-lookup"><span data-stu-id="eba87-176">Push-Location</span></span>](Push-Location.md)

[<span data-ttu-id="eba87-177">Ange plats</span><span class="sxs-lookup"><span data-stu-id="eba87-177">Set-Location</span></span>](Set-Location.md)

[<span data-ttu-id="eba87-178">about_Aliases</span><span class="sxs-lookup"><span data-stu-id="eba87-178">about_Aliases</span></span>](../Microsoft.PowerShell.Core/About/about_Aliases.md)

[<span data-ttu-id="eba87-179">about_Providers</span><span class="sxs-lookup"><span data-stu-id="eba87-179">about_Providers</span></span>](../Microsoft.PowerShell.Core/About/about_Providers.md)
