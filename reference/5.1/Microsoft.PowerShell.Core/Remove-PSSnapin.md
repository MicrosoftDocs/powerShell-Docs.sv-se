---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/remove-pssnapin?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Remove-PSSnapin
ms.openlocfilehash: e74aff3e52c61f41a54664efbab9c0f195b0d409
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93264176"
---
# <span data-ttu-id="e3a83-103">Remove-PSSnapin</span><span class="sxs-lookup"><span data-stu-id="e3a83-103">Remove-PSSnapin</span></span>

## <span data-ttu-id="e3a83-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="e3a83-104">SYNOPSIS</span></span>
<span data-ttu-id="e3a83-105">Tar bort Windows PowerShell-snapin-moduler från den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="e3a83-105">Removes Windows PowerShell snap-ins from the current session.</span></span>

## <span data-ttu-id="e3a83-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="e3a83-106">SYNTAX</span></span>

```
Remove-PSSnapin [-Name] <String[]> [-PassThru] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="e3a83-107">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="e3a83-107">DESCRIPTION</span></span>
<span data-ttu-id="e3a83-108">Cmdlet: en **Remove-PSSnapin** tar bort en Windows PowerShell-snapin-modul från den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="e3a83-108">The **Remove-PSSnapin** cmdlet removes a Windows PowerShell snap-in from the current session.</span></span>
<span data-ttu-id="e3a83-109">Du kan använda den för att ta bort snapin-moduler som du har lagt till i Windows PowerShell du kan inte använda denna cmdlet för att ta bort snapin-modulerna som installeras med Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e3a83-109">You can use it to remove snap-ins that you have added to Windows PowerShell You cannot use this cmdlet to remove the snap-ins that are installed with Windows PowerShell.</span></span>

<span data-ttu-id="e3a83-110">När du har tagit bort en snapin-modul från den aktuella sessionen är snapin-modulen fortfarande inläst, men cmdlets och providers i snapin-modulen är inte längre tillgängliga i sessionen.</span><span class="sxs-lookup"><span data-stu-id="e3a83-110">After you remove a snap-in from the current session, the snap-in is still loaded, but the cmdlets and providers in the snap-in are no longer available in the session.</span></span>

## <span data-ttu-id="e3a83-111">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="e3a83-111">EXAMPLES</span></span>

### <span data-ttu-id="e3a83-112">Exempel 1: ta bort en snapin-modul</span><span class="sxs-lookup"><span data-stu-id="e3a83-112">Example 1: Remove a snap-in</span></span>

```
PS C:\> remove-pssnapin -Name Microsoft.Exchange
```

<span data-ttu-id="e3a83-113">Det här kommandot tar bort snapin-modulen **Microsoft. Exchange** från den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="e3a83-113">This command removes the **Microsoft.Exchange** snap-in from the current session.</span></span>
<span data-ttu-id="e3a83-114">När kommandot har slutförts är de cmdlets och providers som stöds av snapin-modulen inte tillgängliga i sessionen.</span><span class="sxs-lookup"><span data-stu-id="e3a83-114">When the command is complete, the cmdlets and providers that the snap-in supported are not available in the session.</span></span>

### <span data-ttu-id="e3a83-115">Exempel 2: ta bort snapin-moduler med namn med pipelinen</span><span class="sxs-lookup"><span data-stu-id="e3a83-115">Example 2: Remove snap-ins by using names with the pipeline</span></span>

```
PS C:\> Get-PSSnapIn smp* | Remove-PSSnapIn
```

<span data-ttu-id="e3a83-116">Det här kommandot tar bort Windows PowerShell-snapin-moduler som har namn som börjar med SMP från den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="e3a83-116">This command removes the Windows PowerShell snap-ins that have names that start with smp from the current session.</span></span>

<span data-ttu-id="e3a83-117">Kommandot använder cmdleten **Get-PSSnapin** för att hämta objekt som representerar snapin-modulerna. Pipeline-operatorn (|) skickar resultatet till cmdleten **Remove-PSSnapin** , som tar bort dem från sessionen.</span><span class="sxs-lookup"><span data-stu-id="e3a83-117">The command uses the **Get-PSSnapin** cmdlet to get objects that represent the snap-ins. The pipeline operator (|) sends the results to the **Remove-PSSnapin** cmdlet, which removes them from the session.</span></span>
<span data-ttu-id="e3a83-118">De providers och cmdlets som den här snapin-modulen stöder är inte längre tillgängliga i sessionen.</span><span class="sxs-lookup"><span data-stu-id="e3a83-118">The providers and cmdlets that this snap-in supports are no longer available in the session.</span></span>

<span data-ttu-id="e3a83-119">När du rör objekt som ska **tas bort-PSSnapin** , är namnen på objekten associerade med parametern *Name* , som accepterar objekt från pipelinen som har egenskapen **Name** .</span><span class="sxs-lookup"><span data-stu-id="e3a83-119">When you pipe objects to **Remove-PSSnapin** , the names of the objects are associated with the *Name* parameter, which accepts objects from the pipeline that have a **Name** property.</span></span>

### <span data-ttu-id="e3a83-120">Exempel 3: ta bort snapin-moduler med hjälp av namn</span><span class="sxs-lookup"><span data-stu-id="e3a83-120">Example 3: Remove snap-ins by using names</span></span>

```
PS C:\> Remove-PSSnapin -Name *event*
```

<span data-ttu-id="e3a83-121">Det här kommandot tar bort alla Windows PowerShell-snapin-moduler som har namn som inkluderar event.</span><span class="sxs-lookup"><span data-stu-id="e3a83-121">This command removes all Windows PowerShell snap-ins that have names that include event.</span></span>

## <span data-ttu-id="e3a83-122">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="e3a83-122">PARAMETERS</span></span>

### <span data-ttu-id="e3a83-123">-Name</span><span class="sxs-lookup"><span data-stu-id="e3a83-123">-Name</span></span>
<span data-ttu-id="e3a83-124">Anger namnen på Windows PowerShell-snapin-modulerna som ska tas bort från den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="e3a83-124">Specifies the names of Windows PowerShell snap-ins to remove from the current session.</span></span>
<span data-ttu-id="e3a83-125">Jokertecken (\*) tillåts.</span><span class="sxs-lookup"><span data-stu-id="e3a83-125">Wildcard characters (\*) are permitted.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="e3a83-126">– PassThru</span><span class="sxs-lookup"><span data-stu-id="e3a83-126">-PassThru</span></span>
<span data-ttu-id="e3a83-127">Returnerar ett objekt som representerar snapin-modulen.</span><span class="sxs-lookup"><span data-stu-id="e3a83-127">Returns an object that represents the snap-in.</span></span>
<span data-ttu-id="e3a83-128">Som standard genererar denna cmdlet inga utdata.</span><span class="sxs-lookup"><span data-stu-id="e3a83-128">By default, this cmdlet does not generate any output.</span></span>

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

### <span data-ttu-id="e3a83-129">-Confirm</span><span class="sxs-lookup"><span data-stu-id="e3a83-129">-Confirm</span></span>
<span data-ttu-id="e3a83-130">Uppmanar dig att bekräfta innan du kör cmdleten.</span><span class="sxs-lookup"><span data-stu-id="e3a83-130">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="e3a83-131">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="e3a83-131">-WhatIf</span></span>
<span data-ttu-id="e3a83-132">Visar vad som skulle hända om cmdleten kördes.</span><span class="sxs-lookup"><span data-stu-id="e3a83-132">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="e3a83-133">Cmdleten körs inte.</span><span class="sxs-lookup"><span data-stu-id="e3a83-133">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="e3a83-134">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="e3a83-134">CommonParameters</span></span>
<span data-ttu-id="e3a83-135">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="e3a83-135">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="e3a83-136">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="e3a83-136">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="e3a83-137">INDATA</span><span class="sxs-lookup"><span data-stu-id="e3a83-137">INPUTS</span></span>

### <span data-ttu-id="e3a83-138">System. Management. Automation. PSSnapInInfo</span><span class="sxs-lookup"><span data-stu-id="e3a83-138">System.Management.Automation.PSSnapInInfo</span></span>
<span data-ttu-id="e3a83-139">Du kan skicka vidare ett snapin-objekt till denna cmdlet.</span><span class="sxs-lookup"><span data-stu-id="e3a83-139">You can pipe a snap-in object to this cmdlet.</span></span>

## <span data-ttu-id="e3a83-140">UTDATA</span><span class="sxs-lookup"><span data-stu-id="e3a83-140">OUTPUTS</span></span>

### <span data-ttu-id="e3a83-141">Ingen, system. Management. Automation. PSSnapInInfo</span><span class="sxs-lookup"><span data-stu-id="e3a83-141">None, System.Management.Automation.PSSnapInInfo</span></span>
<span data-ttu-id="e3a83-142">Denna cmdlet skapar ett **system. Management. Automation. PSSnapInInfo** -objekt som representerar snapin-modulen, om du anger parametern *Passthru* .</span><span class="sxs-lookup"><span data-stu-id="e3a83-142">This cmdlet generates a **System.Management.Automation.PSSnapInInfo** object that represents the snap-in, if you specify the *PassThru* parameter.</span></span>
<span data-ttu-id="e3a83-143">Som standard genererar **Remove-PSSnapin** inga utdata.</span><span class="sxs-lookup"><span data-stu-id="e3a83-143">By default, **Remove-PSSnapin** does not generate any output.</span></span>

## <span data-ttu-id="e3a83-144">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="e3a83-144">NOTES</span></span>

* <span data-ttu-id="e3a83-145">**Remove-PSSnapin** kontrollerar inte versionen av Windows PowerShell innan en snapin-modul tas bort från sessionen.</span><span class="sxs-lookup"><span data-stu-id="e3a83-145">**Remove-PSSnapin** does not check the version of Windows PowerShell before removing a snap-in from the session.</span></span> <span data-ttu-id="e3a83-146">Om det inte går att ta bort en snapin-modul visas en varning och kommandot Miss lyckas.</span><span class="sxs-lookup"><span data-stu-id="e3a83-146">If a snap-in cannot be removed, a warning appears and the command fails.</span></span>
* <span data-ttu-id="e3a83-147">**Remove-PSSnapin** påverkar endast den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="e3a83-147">**Remove-PSSnapin** affects only the current session.</span></span> <span data-ttu-id="e3a83-148">Om du har lagt till ett Add-PSSnapin-kommando i din Windows PowerShell-profil bör du ta bort kommandot för att ta bort snapin-modulen från framtida sessioner.</span><span class="sxs-lookup"><span data-stu-id="e3a83-148">If you have added an Add-PSSnapin command to your Windows PowerShell profile, you should delete the command to remove the snap-in from future sessions.</span></span> <span data-ttu-id="e3a83-149">För instruktioner skriver du `Get-Help about_Profiles` .</span><span class="sxs-lookup"><span data-stu-id="e3a83-149">For instructions, type `Get-Help about_Profiles`.</span></span>

## <span data-ttu-id="e3a83-150">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="e3a83-150">RELATED LINKS</span></span>

[<span data-ttu-id="e3a83-151">Add-PSSnapin</span><span class="sxs-lookup"><span data-stu-id="e3a83-151">Add-PSSnapin</span></span>](Add-PSSnapin.md)

[<span data-ttu-id="e3a83-152">Get-PSSnapin</span><span class="sxs-lookup"><span data-stu-id="e3a83-152">Get-PSSnapin</span></span>](Get-PSSnapin.md)
