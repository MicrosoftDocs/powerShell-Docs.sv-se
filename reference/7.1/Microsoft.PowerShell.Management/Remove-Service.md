---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/remove-service?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Remove-Service
ms.openlocfilehash: b23e263c2d6ff64ca2a799614d213f1e549cdfe3
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93263259"
---
# <span data-ttu-id="78665-103">Remove-Service</span><span class="sxs-lookup"><span data-stu-id="78665-103">Remove-Service</span></span>

## <span data-ttu-id="78665-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="78665-104">SYNOPSIS</span></span>
<span data-ttu-id="78665-105">Tar bort en Windows-tjänst.</span><span class="sxs-lookup"><span data-stu-id="78665-105">Removes a Windows service.</span></span>

## <span data-ttu-id="78665-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="78665-106">SYNTAX</span></span>

### <span data-ttu-id="78665-107">Namn (standard)</span><span class="sxs-lookup"><span data-stu-id="78665-107">Name (Default)</span></span>

```
Remove-Service [-Name] <String> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="78665-108">InputObject</span><span class="sxs-lookup"><span data-stu-id="78665-108">InputObject</span></span>

```
Remove-Service [-InputObject <ServiceController>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="78665-109">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="78665-109">DESCRIPTION</span></span>

<span data-ttu-id="78665-110">`Remove-Service`Cmdleten tar bort en Windows-tjänst i registret och i tjänst databasen.</span><span class="sxs-lookup"><span data-stu-id="78665-110">The `Remove-Service` cmdlet removes a Windows service in the registry and in the service database.</span></span>

<span data-ttu-id="78665-111">`Remove-Service`Cmdleten introducerades i PowerShell 6,0.</span><span class="sxs-lookup"><span data-stu-id="78665-111">The `Remove-Service` cmdlet was introduced in PowerShell 6.0.</span></span>

## <span data-ttu-id="78665-112">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="78665-112">EXAMPLES</span></span>

### <span data-ttu-id="78665-113">Exempel 1: ta bort en tjänst</span><span class="sxs-lookup"><span data-stu-id="78665-113">Example 1: Remove a service</span></span>

<span data-ttu-id="78665-114">Detta tar bort en tjänst med namnet TestService.</span><span class="sxs-lookup"><span data-stu-id="78665-114">This removes a service named TestService.</span></span>

```powershell
Remove-Service -Name "TestService"
```

### <span data-ttu-id="78665-115">Exempel 2: ta bort en tjänst med visnings namnet</span><span class="sxs-lookup"><span data-stu-id="78665-115">Example 2: Remove a service using the display name</span></span>

<span data-ttu-id="78665-116">I det här exemplet tas en tjänst med namnet TestService bort.</span><span class="sxs-lookup"><span data-stu-id="78665-116">This example removes a service named TestService.</span></span> <span data-ttu-id="78665-117">Kommandot använder `Get-Service` för att hämta ett objekt som representerar TestService-tjänsten med visnings namnet.</span><span class="sxs-lookup"><span data-stu-id="78665-117">The command uses `Get-Service` to get an object that represents the TestService service using the display name.</span></span> <span data-ttu-id="78665-118">Pipelinen ( `|` ) rör objektet till `Remove-Service` , vilket tar bort tjänsten.</span><span class="sxs-lookup"><span data-stu-id="78665-118">The pipeline operator (`|`) pipes the object to `Remove-Service`, which removes the service.</span></span>

```powershell
Get-Service -DisplayName "Test Service" | Remove-Service
```

## <span data-ttu-id="78665-119">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="78665-119">PARAMETERS</span></span>

### <span data-ttu-id="78665-120">– InputObject</span><span class="sxs-lookup"><span data-stu-id="78665-120">-InputObject</span></span>

<span data-ttu-id="78665-121">Anger **ServiceController** -objekt som representerar de tjänster som ska tas bort.</span><span class="sxs-lookup"><span data-stu-id="78665-121">Specifies **ServiceController** objects that represent the services to remove.</span></span> <span data-ttu-id="78665-122">Ange en variabel som innehåller objekten eller Skriv ett kommando eller uttryck som hämtar objekten.</span><span class="sxs-lookup"><span data-stu-id="78665-122">Enter a variable that contains the objects, or type a command or expression that gets the objects.</span></span>

```yaml
Type: System.ServiceProcess.ServiceController
Parameter Sets: InputObject
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="78665-123">-Name</span><span class="sxs-lookup"><span data-stu-id="78665-123">-Name</span></span>

<span data-ttu-id="78665-124">Anger tjänst namnen för de tjänster som ska tas bort.</span><span class="sxs-lookup"><span data-stu-id="78665-124">Specifies the service names of the services to remove.</span></span> <span data-ttu-id="78665-125">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="78665-125">Wildcard characters are permitted.</span></span>

```yaml
Type: System.String
Parameter Sets: Name
Aliases: ServiceName, SN

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### <span data-ttu-id="78665-126">-Confirm</span><span class="sxs-lookup"><span data-stu-id="78665-126">-Confirm</span></span>

<span data-ttu-id="78665-127">Uppmanar dig att bekräfta innan du kör cmdleten.</span><span class="sxs-lookup"><span data-stu-id="78665-127">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="78665-128">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="78665-128">-WhatIf</span></span>

<span data-ttu-id="78665-129">Visar vad som skulle hända om cmdleten kördes.</span><span class="sxs-lookup"><span data-stu-id="78665-129">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="78665-130">Cmdleten körs inte.</span><span class="sxs-lookup"><span data-stu-id="78665-130">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="78665-131">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="78665-131">CommonParameters</span></span>

<span data-ttu-id="78665-132">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="78665-132">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="78665-133">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="78665-133">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="78665-134">INDATA</span><span class="sxs-lookup"><span data-stu-id="78665-134">INPUTS</span></span>

### <span data-ttu-id="78665-135">System. ServiceProcess. ServiceController, system. String</span><span class="sxs-lookup"><span data-stu-id="78665-135">System.ServiceProcess.ServiceController, System.String</span></span>

<span data-ttu-id="78665-136">Du kan skicka vidare ett tjänst objekt eller en sträng som innehåller namnet på en tjänst till denna cmdlet.</span><span class="sxs-lookup"><span data-stu-id="78665-136">You can pipe a service object or a string that contains the name of a service to this cmdlet.</span></span>

## <span data-ttu-id="78665-137">UTDATA</span><span class="sxs-lookup"><span data-stu-id="78665-137">OUTPUTS</span></span>

### <span data-ttu-id="78665-138">Inget</span><span class="sxs-lookup"><span data-stu-id="78665-138">None</span></span>

<span data-ttu-id="78665-139">Denna cmdlet returnerar inga utdata.</span><span class="sxs-lookup"><span data-stu-id="78665-139">This cmdlet does not return any output.</span></span>

## <span data-ttu-id="78665-140">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="78665-140">NOTES</span></span>

<span data-ttu-id="78665-141">Starta PowerShell med alternativet **Kör som administratör** för att köra denna cmdlet.</span><span class="sxs-lookup"><span data-stu-id="78665-141">To run this cmdlet, start PowerShell by using the **Run as administrator** option.</span></span>

## <span data-ttu-id="78665-142">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="78665-142">RELATED LINKS</span></span>

[<span data-ttu-id="78665-143">Get-Service</span><span class="sxs-lookup"><span data-stu-id="78665-143">Get-Service</span></span>](Get-Service.md)

[<span data-ttu-id="78665-144">Restart-Service</span><span class="sxs-lookup"><span data-stu-id="78665-144">Restart-Service</span></span>](Restart-Service.md)

[<span data-ttu-id="78665-145">Resume-Service</span><span class="sxs-lookup"><span data-stu-id="78665-145">Resume-Service</span></span>](Resume-Service.md)

[<span data-ttu-id="78665-146">Set-Service</span><span class="sxs-lookup"><span data-stu-id="78665-146">Set-Service</span></span>](Set-Service.md)

[<span data-ttu-id="78665-147">Start-Service</span><span class="sxs-lookup"><span data-stu-id="78665-147">Start-Service</span></span>](Start-Service.md)

[<span data-ttu-id="78665-148">Stop-Service</span><span class="sxs-lookup"><span data-stu-id="78665-148">Stop-Service</span></span>](Stop-Service.md)

[<span data-ttu-id="78665-149">Suspend-Service</span><span class="sxs-lookup"><span data-stu-id="78665-149">Suspend-Service</span></span>](Suspend-Service.md)

