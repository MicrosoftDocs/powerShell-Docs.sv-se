---
external help file: Microsoft.Management.Infrastructure.CimCmdlets.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: CimCmdlets
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/cimcmdlets/remove-cimsession?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Remove-CimSession
ms.openlocfilehash: eae279aa9c5d3a99a9a522254c5b792970f74297
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93267885"
---
# <span data-ttu-id="ec611-103">Remove-CimSession</span><span class="sxs-lookup"><span data-stu-id="ec611-103">Remove-CimSession</span></span>

## <span data-ttu-id="ec611-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="ec611-104">SYNOPSIS</span></span>
<span data-ttu-id="ec611-105">Tar bort en eller flera CIM-sessioner.</span><span class="sxs-lookup"><span data-stu-id="ec611-105">Removes one or more CIM sessions.</span></span>

## <span data-ttu-id="ec611-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="ec611-106">SYNTAX</span></span>

### <span data-ttu-id="ec611-107">CimSessionSet (standard)</span><span class="sxs-lookup"><span data-stu-id="ec611-107">CimSessionSet (Default)</span></span>

```
Remove-CimSession [-CimSession] <CimSession[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="ec611-108">ComputerNameSet</span><span class="sxs-lookup"><span data-stu-id="ec611-108">ComputerNameSet</span></span>

```
Remove-CimSession [-ComputerName] <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="ec611-109">SessionIdSet</span><span class="sxs-lookup"><span data-stu-id="ec611-109">SessionIdSet</span></span>

```
Remove-CimSession [-Id] <UInt32[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="ec611-110">InstanceIdSet</span><span class="sxs-lookup"><span data-stu-id="ec611-110">InstanceIdSet</span></span>

```
Remove-CimSession -InstanceId <Guid[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="ec611-111">NameSet</span><span class="sxs-lookup"><span data-stu-id="ec611-111">NameSet</span></span>

```
Remove-CimSession -Name <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="ec611-112">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="ec611-112">DESCRIPTION</span></span>

<span data-ttu-id="ec611-113">`Remove-CimSession`Cmdleten tar bort ett eller flera CIM-sessionsobjekt från den lokala PowerShell-sessionen.</span><span class="sxs-lookup"><span data-stu-id="ec611-113">The `Remove-CimSession` cmdlet removes one or more CIM session objects from the local PowerShell session.</span></span>

## <span data-ttu-id="ec611-114">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="ec611-114">EXAMPLES</span></span>

### <span data-ttu-id="ec611-115">Exempel 1: ta bort alla CIM-sessioner</span><span class="sxs-lookup"><span data-stu-id="ec611-115">Example 1: Remove all the CIM sessions</span></span>

<span data-ttu-id="ec611-116">Det här exemplet hämtar alla tillgängliga CIM-sessioner på den lokala datorn med hjälp av cmdleten [Get-CimSession](Get-CimSession.md) och tar sedan bort dem med hjälp av `Remove-CimSession` .</span><span class="sxs-lookup"><span data-stu-id="ec611-116">This example retrieves all the available CIM sessions on the local computer using the [Get-CimSession](Get-CimSession.md) cmdlet, and then removes them using the `Remove-CimSession`.</span></span>

```powershell
Get-CimSession | Remove-CimSession
```

### <span data-ttu-id="ec611-117">Exempel 2: ta bort en angiven CIM-session</span><span class="sxs-lookup"><span data-stu-id="ec611-117">Example 2: Remove a specific CIM session</span></span>

<span data-ttu-id="ec611-118">I det här exemplet tas CIM-sessionen bort som har **ID-** värdet 5.</span><span class="sxs-lookup"><span data-stu-id="ec611-118">This example removes the CIM session that has an **Id** value of 5.</span></span>

```powershell
Remove-CimSession -Id 5
```

### <span data-ttu-id="ec611-119">Exempel 3: Visa listan över CIM-sessioner som ska tas bort med hjälp av parametern WhatIf</span><span class="sxs-lookup"><span data-stu-id="ec611-119">Example 3: Show the list of CIM sessions to remove by using the WhatIf parameter</span></span>

<span data-ttu-id="ec611-120">I det här exemplet används den gemensamma parametern **whatIf** för att ange att borttagningen inte ska göras, men endast utdata som skulle inträffa om den är färdig.</span><span class="sxs-lookup"><span data-stu-id="ec611-120">This example uses the common parameter **WhatIf** to specify that the removal should not be done, but only output what would happen if it were done.</span></span>

```powershell
Remove-CimSession -Name a* -WhatIf
```

## <span data-ttu-id="ec611-121">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="ec611-121">PARAMETERS</span></span>

### <span data-ttu-id="ec611-122">– CimSession</span><span class="sxs-lookup"><span data-stu-id="ec611-122">-CimSession</span></span>

<span data-ttu-id="ec611-123">Anger session-objekten för de CIM-sessioner som ska stängas.</span><span class="sxs-lookup"><span data-stu-id="ec611-123">Specifies the session objects of the CIM sessions to close.</span></span>

<span data-ttu-id="ec611-124">Ange en variabel som innehåller CIM-sessionen, eller ett kommando som skapar eller hämtar CIM-sessionen, t. ex [`New-CimSession`](New-CimSession.md) . eller- [`Get-CimSession`](Get-CimSession.md) cmdletar.</span><span class="sxs-lookup"><span data-stu-id="ec611-124">Enter a variable that contains the CIM session, or a command that creates or gets the CIM session, such as the [`New-CimSession`](New-CimSession.md) or [`Get-CimSession`](Get-CimSession.md) cmdlets.</span></span>
<span data-ttu-id="ec611-125">Mer information finns i [about_CimSessions](../Microsoft.PowerShell.Core/About/about_CimSession.md).</span><span class="sxs-lookup"><span data-stu-id="ec611-125">For more information, see [about_CimSessions](../Microsoft.PowerShell.Core/About/about_CimSession.md).</span></span>

```yaml
Type: Microsoft.Management.Infrastructure.CimSession[]
Parameter Sets: CimSessionSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="ec611-126">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="ec611-126">-ComputerName</span></span>

<span data-ttu-id="ec611-127">Anger en matris med namn på datorer.</span><span class="sxs-lookup"><span data-stu-id="ec611-127">Specifies an array of names of computers.</span></span> <span data-ttu-id="ec611-128">Tar bort de sessioner som ansluter till de angivna datorerna.</span><span class="sxs-lookup"><span data-stu-id="ec611-128">Removes the sessions that connect to the specified computers.</span></span> <span data-ttu-id="ec611-129">Du kan ange ett fullständigt kvalificerat domän namn (FQDN) eller ett NetBIOS-namn.</span><span class="sxs-lookup"><span data-stu-id="ec611-129">You can specify a fully qualified domain name (FQDN) or a NetBIOS name.</span></span>

```yaml
Type: System.String[]
Parameter Sets: ComputerNameSet
Aliases: CN, ServerName

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### <span data-ttu-id="ec611-130">-ID</span><span class="sxs-lookup"><span data-stu-id="ec611-130">-Id</span></span>

<span data-ttu-id="ec611-131">Anger ID för CIM-sessionen som ska tas bort.</span><span class="sxs-lookup"><span data-stu-id="ec611-131">Specifies the ID of the CIM session to remove.</span></span> <span data-ttu-id="ec611-132">Ange ett eller flera ID: n avgränsade med kommatecken eller Använd intervall operatorn ( `..` ) för att ange ett intervall med ID: n.</span><span class="sxs-lookup"><span data-stu-id="ec611-132">Specify one or more IDs separated by commas, or use the range operator (`..`) to specify a range of IDs.</span></span> <span data-ttu-id="ec611-133">Ett **ID** är ett heltal som unikt identifierar CIM-sessionen i den aktuella PowerShell-sessionen.</span><span class="sxs-lookup"><span data-stu-id="ec611-133">An **Id** is an integer that uniquely identifies the CIM session in the current PowerShell session.</span></span>

<span data-ttu-id="ec611-134">Mer information om operatorn Range finns [about_Operators](../Microsoft.PowerShell.Core/About/about_Operators.md).</span><span class="sxs-lookup"><span data-stu-id="ec611-134">For more information about the range operator, see [about_Operators](../Microsoft.PowerShell.Core/About/about_Operators.md).</span></span>

```yaml
Type: System.UInt32[]
Parameter Sets: SessionIdSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="ec611-135">-InstanceId</span><span class="sxs-lookup"><span data-stu-id="ec611-135">-InstanceId</span></span>

<span data-ttu-id="ec611-136">Anger instans-ID för CIM-sessionen som ska tas bort.</span><span class="sxs-lookup"><span data-stu-id="ec611-136">Specifies the instance ID of the CIM session to remove.</span></span> <span data-ttu-id="ec611-137">**InstanceID** är en globalt unik IDENTIFIERARE (GUID) som unikt identifierar en CIM-session.</span><span class="sxs-lookup"><span data-stu-id="ec611-137">**InstanceId** is a Globally Unique Identifier (GUID) that uniquely identifies a CIM session.</span></span> <span data-ttu-id="ec611-138">**InstanceID** är unikt, även om du har flera sessioner som körs i PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ec611-138">The **InstanceId** is unique, even when you have multiple sessions running in PowerShell.</span></span>

<span data-ttu-id="ec611-139">**InstanceID** lagras i egenskapen **InstanceID** för objektet som representerar en CIM-session.</span><span class="sxs-lookup"><span data-stu-id="ec611-139">The **InstanceId** is stored in the **InstanceId** property of the object that represents a CIM session.</span></span>

```yaml
Type: System.Guid[]
Parameter Sets: InstanceIdSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="ec611-140">-Name</span><span class="sxs-lookup"><span data-stu-id="ec611-140">-Name</span></span>

<span data-ttu-id="ec611-141">Anger det egna namnet på CIM-sessionen som ska tas bort.</span><span class="sxs-lookup"><span data-stu-id="ec611-141">Specifies the friendly name of the CIM session to remove.</span></span> <span data-ttu-id="ec611-142">Du kan använda jokertecken med den här parametern.</span><span class="sxs-lookup"><span data-stu-id="ec611-142">You can use wildcard characters with this parameter.</span></span>

```yaml
Type: System.String[]
Parameter Sets: NameSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### <span data-ttu-id="ec611-143">-Confirm</span><span class="sxs-lookup"><span data-stu-id="ec611-143">-Confirm</span></span>

<span data-ttu-id="ec611-144">Uppmanar dig att bekräfta innan du kör cmdleten.</span><span class="sxs-lookup"><span data-stu-id="ec611-144">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="ec611-145">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="ec611-145">-WhatIf</span></span>

<span data-ttu-id="ec611-146">Visar vad som skulle hända om cmdleten kördes.</span><span class="sxs-lookup"><span data-stu-id="ec611-146">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="ec611-147">Cmdleten körs inte.</span><span class="sxs-lookup"><span data-stu-id="ec611-147">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="ec611-148">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="ec611-148">CommonParameters</span></span>

<span data-ttu-id="ec611-149">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="ec611-149">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="ec611-150">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="ec611-150">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="ec611-151">INDATA</span><span class="sxs-lookup"><span data-stu-id="ec611-151">INPUTS</span></span>

### <span data-ttu-id="ec611-152">Inget</span><span class="sxs-lookup"><span data-stu-id="ec611-152">None</span></span>

<span data-ttu-id="ec611-153">Denna cmdlet accepterar inga inobjekt.</span><span class="sxs-lookup"><span data-stu-id="ec611-153">This cmdlet accepts no input objects.</span></span>

## <span data-ttu-id="ec611-154">UTDATA</span><span class="sxs-lookup"><span data-stu-id="ec611-154">OUTPUTS</span></span>

### <span data-ttu-id="ec611-155">System. Object</span><span class="sxs-lookup"><span data-stu-id="ec611-155">System.Object</span></span>

<span data-ttu-id="ec611-156">Den här cmdleten returnerar ett objekt som innehåller information om CIM-session.</span><span class="sxs-lookup"><span data-stu-id="ec611-156">This cmdlet returns an object that contains CIM session information.</span></span>

## <span data-ttu-id="ec611-157">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="ec611-157">NOTES</span></span>

## <span data-ttu-id="ec611-158">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="ec611-158">RELATED LINKS</span></span>

[<span data-ttu-id="ec611-159">Get-CimSession</span><span class="sxs-lookup"><span data-stu-id="ec611-159">Get-CimSession</span></span>](Get-CimSession.md)

[<span data-ttu-id="ec611-160">New-CimSession</span><span class="sxs-lookup"><span data-stu-id="ec611-160">New-CimSession</span></span>](New-CimSession.md)

[<span data-ttu-id="ec611-161">about_CimSession</span><span class="sxs-lookup"><span data-stu-id="ec611-161">about_CimSession</span></span>](../Microsoft.PowerShell.Core/About/about_CimSession.md)

