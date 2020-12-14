---
external help file: Microsoft.Management.Infrastructure.CimCmdlets.dll-Help.xml
Locale: en-US
Module Name: CimCmdlets
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/cimcmdlets/remove-cimsession?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Remove-CimSession
ms.openlocfilehash: a3ff2132c531df1ab19bf7149a55ea0df4a787a8
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94708546"
---
# <span data-ttu-id="bb32c-102">Remove-CimSession</span><span class="sxs-lookup"><span data-stu-id="bb32c-102">Remove-CimSession</span></span>

## <span data-ttu-id="bb32c-103">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="bb32c-103">SYNOPSIS</span></span>
<span data-ttu-id="bb32c-104">Tar bort en eller flera CIM-sessioner.</span><span class="sxs-lookup"><span data-stu-id="bb32c-104">Removes one or more CIM sessions.</span></span>

## <span data-ttu-id="bb32c-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="bb32c-105">SYNTAX</span></span>

### <span data-ttu-id="bb32c-106">CimSessionSet (standard)</span><span class="sxs-lookup"><span data-stu-id="bb32c-106">CimSessionSet (Default)</span></span>

```
Remove-CimSession [-CimSession] <CimSession[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="bb32c-107">ComputerNameSet</span><span class="sxs-lookup"><span data-stu-id="bb32c-107">ComputerNameSet</span></span>

```
Remove-CimSession [-ComputerName] <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="bb32c-108">SessionIdSet</span><span class="sxs-lookup"><span data-stu-id="bb32c-108">SessionIdSet</span></span>

```
Remove-CimSession [-Id] <UInt32[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="bb32c-109">InstanceIdSet</span><span class="sxs-lookup"><span data-stu-id="bb32c-109">InstanceIdSet</span></span>

```
Remove-CimSession -InstanceId <Guid[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="bb32c-110">NameSet</span><span class="sxs-lookup"><span data-stu-id="bb32c-110">NameSet</span></span>

```
Remove-CimSession -Name <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="bb32c-111">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="bb32c-111">DESCRIPTION</span></span>

<span data-ttu-id="bb32c-112">`Remove-CimSession`Cmdleten tar bort ett eller flera CIM-sessionsobjekt från den lokala PowerShell-sessionen.</span><span class="sxs-lookup"><span data-stu-id="bb32c-112">The `Remove-CimSession` cmdlet removes one or more CIM session objects from the local PowerShell session.</span></span>

## <span data-ttu-id="bb32c-113">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="bb32c-113">EXAMPLES</span></span>

### <span data-ttu-id="bb32c-114">Exempel 1: ta bort alla CIM-sessioner</span><span class="sxs-lookup"><span data-stu-id="bb32c-114">Example 1: Remove all the CIM sessions</span></span>

<span data-ttu-id="bb32c-115">Det här exemplet hämtar alla tillgängliga CIM-sessioner på den lokala datorn med hjälp av cmdleten [Get-CimSession](Get-CimSession.md) och tar sedan bort dem med hjälp av `Remove-CimSession` .</span><span class="sxs-lookup"><span data-stu-id="bb32c-115">This example retrieves all the available CIM sessions on the local computer using the [Get-CimSession](Get-CimSession.md) cmdlet, and then removes them using the `Remove-CimSession`.</span></span>

```powershell
Get-CimSession | Remove-CimSession
```

### <span data-ttu-id="bb32c-116">Exempel 2: ta bort en angiven CIM-session</span><span class="sxs-lookup"><span data-stu-id="bb32c-116">Example 2: Remove a specific CIM session</span></span>

<span data-ttu-id="bb32c-117">I det här exemplet tas CIM-sessionen bort som har **ID-** värdet 5.</span><span class="sxs-lookup"><span data-stu-id="bb32c-117">This example removes the CIM session that has an **Id** value of 5.</span></span>

```powershell
Remove-CimSession -Id 5
```

### <span data-ttu-id="bb32c-118">Exempel 3: Visa listan över CIM-sessioner som ska tas bort med hjälp av parametern WhatIf</span><span class="sxs-lookup"><span data-stu-id="bb32c-118">Example 3: Show the list of CIM sessions to remove by using the WhatIf parameter</span></span>

<span data-ttu-id="bb32c-119">I det här exemplet används den gemensamma parametern **whatIf** för att ange att borttagningen inte ska göras, men endast utdata som skulle inträffa om den är färdig.</span><span class="sxs-lookup"><span data-stu-id="bb32c-119">This example uses the common parameter **WhatIf** to specify that the removal should not be done, but only output what would happen if it were done.</span></span>

```powershell
Remove-CimSession -Name a* -WhatIf
```

## <span data-ttu-id="bb32c-120">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="bb32c-120">PARAMETERS</span></span>

### <span data-ttu-id="bb32c-121">– CimSession</span><span class="sxs-lookup"><span data-stu-id="bb32c-121">-CimSession</span></span>

<span data-ttu-id="bb32c-122">Anger session-objekten för de CIM-sessioner som ska stängas.</span><span class="sxs-lookup"><span data-stu-id="bb32c-122">Specifies the session objects of the CIM sessions to close.</span></span>

<span data-ttu-id="bb32c-123">Ange en variabel som innehåller CIM-sessionen, eller ett kommando som skapar eller hämtar CIM-sessionen, t. ex [`New-CimSession`](New-CimSession.md) . eller- [`Get-CimSession`](Get-CimSession.md) cmdletar.</span><span class="sxs-lookup"><span data-stu-id="bb32c-123">Enter a variable that contains the CIM session, or a command that creates or gets the CIM session, such as the [`New-CimSession`](New-CimSession.md) or [`Get-CimSession`](Get-CimSession.md) cmdlets.</span></span>
<span data-ttu-id="bb32c-124">Mer information finns i [about_CimSessions](../Microsoft.PowerShell.Core/About/about_CimSession.md).</span><span class="sxs-lookup"><span data-stu-id="bb32c-124">For more information, see [about_CimSessions](../Microsoft.PowerShell.Core/About/about_CimSession.md).</span></span>

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

### <span data-ttu-id="bb32c-125">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="bb32c-125">-ComputerName</span></span>

<span data-ttu-id="bb32c-126">Anger en matris med namn på datorer.</span><span class="sxs-lookup"><span data-stu-id="bb32c-126">Specifies an array of names of computers.</span></span> <span data-ttu-id="bb32c-127">Tar bort de sessioner som ansluter till de angivna datorerna.</span><span class="sxs-lookup"><span data-stu-id="bb32c-127">Removes the sessions that connect to the specified computers.</span></span> <span data-ttu-id="bb32c-128">Du kan ange ett fullständigt kvalificerat domän namn (FQDN) eller ett NetBIOS-namn.</span><span class="sxs-lookup"><span data-stu-id="bb32c-128">You can specify a fully qualified domain name (FQDN) or a NetBIOS name.</span></span>

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

### <span data-ttu-id="bb32c-129">-ID</span><span class="sxs-lookup"><span data-stu-id="bb32c-129">-Id</span></span>

<span data-ttu-id="bb32c-130">Anger ID för CIM-sessionen som ska tas bort.</span><span class="sxs-lookup"><span data-stu-id="bb32c-130">Specifies the ID of the CIM session to remove.</span></span> <span data-ttu-id="bb32c-131">Ange ett eller flera ID: n avgränsade med kommatecken eller Använd intervall operatorn ( `..` ) för att ange ett intervall med ID: n.</span><span class="sxs-lookup"><span data-stu-id="bb32c-131">Specify one or more IDs separated by commas, or use the range operator (`..`) to specify a range of IDs.</span></span> <span data-ttu-id="bb32c-132">Ett **ID** är ett heltal som unikt identifierar CIM-sessionen i den aktuella PowerShell-sessionen.</span><span class="sxs-lookup"><span data-stu-id="bb32c-132">An **Id** is an integer that uniquely identifies the CIM session in the current PowerShell session.</span></span>

<span data-ttu-id="bb32c-133">Mer information om operatorn Range finns [about_Operators](../Microsoft.PowerShell.Core/About/about_Operators.md).</span><span class="sxs-lookup"><span data-stu-id="bb32c-133">For more information about the range operator, see [about_Operators](../Microsoft.PowerShell.Core/About/about_Operators.md).</span></span>

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

### <span data-ttu-id="bb32c-134">-InstanceId</span><span class="sxs-lookup"><span data-stu-id="bb32c-134">-InstanceId</span></span>

<span data-ttu-id="bb32c-135">Anger instans-ID för CIM-sessionen som ska tas bort.</span><span class="sxs-lookup"><span data-stu-id="bb32c-135">Specifies the instance ID of the CIM session to remove.</span></span> <span data-ttu-id="bb32c-136">**InstanceID** är en globalt unik IDENTIFIERARE (GUID) som unikt identifierar en CIM-session.</span><span class="sxs-lookup"><span data-stu-id="bb32c-136">**InstanceId** is a Globally Unique Identifier (GUID) that uniquely identifies a CIM session.</span></span> <span data-ttu-id="bb32c-137">**InstanceID** är unikt, även om du har flera sessioner som körs i PowerShell.</span><span class="sxs-lookup"><span data-stu-id="bb32c-137">The **InstanceId** is unique, even when you have multiple sessions running in PowerShell.</span></span>

<span data-ttu-id="bb32c-138">**InstanceID** lagras i egenskapen **InstanceID** för objektet som representerar en CIM-session.</span><span class="sxs-lookup"><span data-stu-id="bb32c-138">The **InstanceId** is stored in the **InstanceId** property of the object that represents a CIM session.</span></span>

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

### <span data-ttu-id="bb32c-139">-Name</span><span class="sxs-lookup"><span data-stu-id="bb32c-139">-Name</span></span>

<span data-ttu-id="bb32c-140">Anger det egna namnet på CIM-sessionen som ska tas bort.</span><span class="sxs-lookup"><span data-stu-id="bb32c-140">Specifies the friendly name of the CIM session to remove.</span></span> <span data-ttu-id="bb32c-141">Du kan använda jokertecken med den här parametern.</span><span class="sxs-lookup"><span data-stu-id="bb32c-141">You can use wildcard characters with this parameter.</span></span>

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

### <span data-ttu-id="bb32c-142">-Confirm</span><span class="sxs-lookup"><span data-stu-id="bb32c-142">-Confirm</span></span>

<span data-ttu-id="bb32c-143">Uppmanar dig att bekräfta innan du kör cmdleten.</span><span class="sxs-lookup"><span data-stu-id="bb32c-143">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="bb32c-144">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="bb32c-144">-WhatIf</span></span>

<span data-ttu-id="bb32c-145">Visar vad som skulle hända om cmdleten kördes.</span><span class="sxs-lookup"><span data-stu-id="bb32c-145">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="bb32c-146">Cmdleten körs inte.</span><span class="sxs-lookup"><span data-stu-id="bb32c-146">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="bb32c-147">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="bb32c-147">CommonParameters</span></span>

<span data-ttu-id="bb32c-148">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="bb32c-148">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="bb32c-149">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="bb32c-149">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="bb32c-150">INDATA</span><span class="sxs-lookup"><span data-stu-id="bb32c-150">INPUTS</span></span>

### <span data-ttu-id="bb32c-151">Inga</span><span class="sxs-lookup"><span data-stu-id="bb32c-151">None</span></span>

<span data-ttu-id="bb32c-152">Denna cmdlet accepterar inga inobjekt.</span><span class="sxs-lookup"><span data-stu-id="bb32c-152">This cmdlet accepts no input objects.</span></span>

## <span data-ttu-id="bb32c-153">UTDATA</span><span class="sxs-lookup"><span data-stu-id="bb32c-153">OUTPUTS</span></span>

### <span data-ttu-id="bb32c-154">System. Object</span><span class="sxs-lookup"><span data-stu-id="bb32c-154">System.Object</span></span>

<span data-ttu-id="bb32c-155">Den här cmdleten returnerar ett objekt som innehåller information om CIM-session.</span><span class="sxs-lookup"><span data-stu-id="bb32c-155">This cmdlet returns an object that contains CIM session information.</span></span>

## <span data-ttu-id="bb32c-156">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="bb32c-156">NOTES</span></span>

## <span data-ttu-id="bb32c-157">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="bb32c-157">RELATED LINKS</span></span>

[<span data-ttu-id="bb32c-158">Get-CimSession</span><span class="sxs-lookup"><span data-stu-id="bb32c-158">Get-CimSession</span></span>](Get-CimSession.md)

[<span data-ttu-id="bb32c-159">New-CimSession</span><span class="sxs-lookup"><span data-stu-id="bb32c-159">New-CimSession</span></span>](New-CimSession.md)

[<span data-ttu-id="bb32c-160">about_CimSession</span><span class="sxs-lookup"><span data-stu-id="bb32c-160">about_CimSession</span></span>](../Microsoft.PowerShell.Core/About/about_CimSession.md)

