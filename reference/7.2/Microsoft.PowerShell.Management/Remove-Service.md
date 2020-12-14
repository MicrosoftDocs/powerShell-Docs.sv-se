---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/remove-service?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Remove-Service
ms.openlocfilehash: 645efc2d271a3b95801c8d0d264ee33ed788f15f
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94709960"
---
# <span data-ttu-id="6ea0b-102">Remove-Service</span><span class="sxs-lookup"><span data-stu-id="6ea0b-102">Remove-Service</span></span>

## <span data-ttu-id="6ea0b-103">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="6ea0b-103">SYNOPSIS</span></span>
<span data-ttu-id="6ea0b-104">Tar bort en Windows-tjänst.</span><span class="sxs-lookup"><span data-stu-id="6ea0b-104">Removes a Windows service.</span></span>

## <span data-ttu-id="6ea0b-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="6ea0b-105">SYNTAX</span></span>

### <span data-ttu-id="6ea0b-106">Namn (standard)</span><span class="sxs-lookup"><span data-stu-id="6ea0b-106">Name (Default)</span></span>

```
Remove-Service [-Name] <String> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="6ea0b-107">InputObject</span><span class="sxs-lookup"><span data-stu-id="6ea0b-107">InputObject</span></span>

```
Remove-Service [-InputObject <ServiceController>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="6ea0b-108">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="6ea0b-108">DESCRIPTION</span></span>

<span data-ttu-id="6ea0b-109">`Remove-Service`Cmdleten tar bort en Windows-tjänst i registret och i tjänst databasen.</span><span class="sxs-lookup"><span data-stu-id="6ea0b-109">The `Remove-Service` cmdlet removes a Windows service in the registry and in the service database.</span></span>

<span data-ttu-id="6ea0b-110">`Remove-Service`Cmdleten introducerades i PowerShell 6,0.</span><span class="sxs-lookup"><span data-stu-id="6ea0b-110">The `Remove-Service` cmdlet was introduced in PowerShell 6.0.</span></span>

## <span data-ttu-id="6ea0b-111">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="6ea0b-111">EXAMPLES</span></span>

### <span data-ttu-id="6ea0b-112">Exempel 1: ta bort en tjänst</span><span class="sxs-lookup"><span data-stu-id="6ea0b-112">Example 1: Remove a service</span></span>

<span data-ttu-id="6ea0b-113">Detta tar bort en tjänst med namnet TestService.</span><span class="sxs-lookup"><span data-stu-id="6ea0b-113">This removes a service named TestService.</span></span>

```powershell
Remove-Service -Name "TestService"
```

### <span data-ttu-id="6ea0b-114">Exempel 2: ta bort en tjänst med visnings namnet</span><span class="sxs-lookup"><span data-stu-id="6ea0b-114">Example 2: Remove a service using the display name</span></span>

<span data-ttu-id="6ea0b-115">I det här exemplet tas en tjänst med namnet TestService bort.</span><span class="sxs-lookup"><span data-stu-id="6ea0b-115">This example removes a service named TestService.</span></span> <span data-ttu-id="6ea0b-116">Kommandot använder `Get-Service` för att hämta ett objekt som representerar TestService-tjänsten med visnings namnet.</span><span class="sxs-lookup"><span data-stu-id="6ea0b-116">The command uses `Get-Service` to get an object that represents the TestService service using the display name.</span></span> <span data-ttu-id="6ea0b-117">Pipelinen ( `|` ) rör objektet till `Remove-Service` , vilket tar bort tjänsten.</span><span class="sxs-lookup"><span data-stu-id="6ea0b-117">The pipeline operator (`|`) pipes the object to `Remove-Service`, which removes the service.</span></span>

```powershell
Get-Service -DisplayName "Test Service" | Remove-Service
```

## <span data-ttu-id="6ea0b-118">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="6ea0b-118">PARAMETERS</span></span>

### <span data-ttu-id="6ea0b-119">– InputObject</span><span class="sxs-lookup"><span data-stu-id="6ea0b-119">-InputObject</span></span>

<span data-ttu-id="6ea0b-120">Anger **ServiceController** -objekt som representerar de tjänster som ska tas bort.</span><span class="sxs-lookup"><span data-stu-id="6ea0b-120">Specifies **ServiceController** objects that represent the services to remove.</span></span> <span data-ttu-id="6ea0b-121">Ange en variabel som innehåller objekten eller Skriv ett kommando eller uttryck som hämtar objekten.</span><span class="sxs-lookup"><span data-stu-id="6ea0b-121">Enter a variable that contains the objects, or type a command or expression that gets the objects.</span></span>

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

### <span data-ttu-id="6ea0b-122">-Name</span><span class="sxs-lookup"><span data-stu-id="6ea0b-122">-Name</span></span>

<span data-ttu-id="6ea0b-123">Anger tjänst namnen för de tjänster som ska tas bort.</span><span class="sxs-lookup"><span data-stu-id="6ea0b-123">Specifies the service names of the services to remove.</span></span> <span data-ttu-id="6ea0b-124">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="6ea0b-124">Wildcard characters are permitted.</span></span>

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

### <span data-ttu-id="6ea0b-125">-Confirm</span><span class="sxs-lookup"><span data-stu-id="6ea0b-125">-Confirm</span></span>

<span data-ttu-id="6ea0b-126">Uppmanar dig att bekräfta innan du kör cmdleten.</span><span class="sxs-lookup"><span data-stu-id="6ea0b-126">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="6ea0b-127">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="6ea0b-127">-WhatIf</span></span>

<span data-ttu-id="6ea0b-128">Visar vad som skulle hända om cmdleten kördes.</span><span class="sxs-lookup"><span data-stu-id="6ea0b-128">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="6ea0b-129">Cmdleten körs inte.</span><span class="sxs-lookup"><span data-stu-id="6ea0b-129">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="6ea0b-130">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="6ea0b-130">CommonParameters</span></span>

<span data-ttu-id="6ea0b-131">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="6ea0b-131">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="6ea0b-132">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="6ea0b-132">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="6ea0b-133">INDATA</span><span class="sxs-lookup"><span data-stu-id="6ea0b-133">INPUTS</span></span>

### <span data-ttu-id="6ea0b-134">System. ServiceProcess. ServiceController, system. String</span><span class="sxs-lookup"><span data-stu-id="6ea0b-134">System.ServiceProcess.ServiceController, System.String</span></span>

<span data-ttu-id="6ea0b-135">Du kan skicka vidare ett tjänst objekt eller en sträng som innehåller namnet på en tjänst till denna cmdlet.</span><span class="sxs-lookup"><span data-stu-id="6ea0b-135">You can pipe a service object or a string that contains the name of a service to this cmdlet.</span></span>

## <span data-ttu-id="6ea0b-136">UTDATA</span><span class="sxs-lookup"><span data-stu-id="6ea0b-136">OUTPUTS</span></span>

### <span data-ttu-id="6ea0b-137">Inga</span><span class="sxs-lookup"><span data-stu-id="6ea0b-137">None</span></span>

<span data-ttu-id="6ea0b-138">Denna cmdlet returnerar inga utdata.</span><span class="sxs-lookup"><span data-stu-id="6ea0b-138">This cmdlet does not return any output.</span></span>

## <span data-ttu-id="6ea0b-139">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="6ea0b-139">NOTES</span></span>

<span data-ttu-id="6ea0b-140">Den här cmdleten är endast tillgänglig på Windows-plattformar.</span><span class="sxs-lookup"><span data-stu-id="6ea0b-140">This cmdlet is only available on Windows platforms.</span></span>

<span data-ttu-id="6ea0b-141">Starta PowerShell med alternativet **Kör som administratör** för att köra denna cmdlet.</span><span class="sxs-lookup"><span data-stu-id="6ea0b-141">To run this cmdlet, start PowerShell by using the **Run as administrator** option.</span></span>

## <span data-ttu-id="6ea0b-142">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="6ea0b-142">RELATED LINKS</span></span>

[<span data-ttu-id="6ea0b-143">Get-Service</span><span class="sxs-lookup"><span data-stu-id="6ea0b-143">Get-Service</span></span>](Get-Service.md)

[<span data-ttu-id="6ea0b-144">Restart-Service</span><span class="sxs-lookup"><span data-stu-id="6ea0b-144">Restart-Service</span></span>](Restart-Service.md)

[<span data-ttu-id="6ea0b-145">Resume-Service</span><span class="sxs-lookup"><span data-stu-id="6ea0b-145">Resume-Service</span></span>](Resume-Service.md)

[<span data-ttu-id="6ea0b-146">Set-Service</span><span class="sxs-lookup"><span data-stu-id="6ea0b-146">Set-Service</span></span>](Set-Service.md)

[<span data-ttu-id="6ea0b-147">Start-Service</span><span class="sxs-lookup"><span data-stu-id="6ea0b-147">Start-Service</span></span>](Start-Service.md)

[<span data-ttu-id="6ea0b-148">Stop-Service</span><span class="sxs-lookup"><span data-stu-id="6ea0b-148">Stop-Service</span></span>](Stop-Service.md)

[<span data-ttu-id="6ea0b-149">Suspend-Service</span><span class="sxs-lookup"><span data-stu-id="6ea0b-149">Suspend-Service</span></span>](Suspend-Service.md)
