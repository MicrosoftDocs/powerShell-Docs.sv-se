---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/resume-service?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Resume-Service
ms.openlocfilehash: 8ce2182117167d93c8f7abd86eeb2c79abdf09c8
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94709919"
---
# <span data-ttu-id="9734f-102">Resume-Service</span><span class="sxs-lookup"><span data-stu-id="9734f-102">Resume-Service</span></span>

## <span data-ttu-id="9734f-103">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="9734f-103">SYNOPSIS</span></span>
<span data-ttu-id="9734f-104">Återupptar en eller flera pausade tjänster.</span><span class="sxs-lookup"><span data-stu-id="9734f-104">Resumes one or more suspended (paused) services.</span></span>

## <span data-ttu-id="9734f-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="9734f-105">SYNTAX</span></span>

### <span data-ttu-id="9734f-106">InputObject (standard)</span><span class="sxs-lookup"><span data-stu-id="9734f-106">InputObject (Default)</span></span>

```
Resume-Service [-InputObject] <ServiceController[]> [-PassThru] [-Include <String[]>] [-Exclude <String[]>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="9734f-107">Standardvärde</span><span class="sxs-lookup"><span data-stu-id="9734f-107">Default</span></span>

```
Resume-Service [-Name] <String[]> [-PassThru] [-Include <String[]>] [-Exclude <String[]>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### <span data-ttu-id="9734f-108">DisplayName</span><span class="sxs-lookup"><span data-stu-id="9734f-108">DisplayName</span></span>

```
Resume-Service [-PassThru] -DisplayName <String[]> [-Include <String[]>] [-Exclude <String[]>] [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="9734f-109">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="9734f-109">DESCRIPTION</span></span>

<span data-ttu-id="9734f-110">`Resume-Service`Cmdleten skickar ett återställnings meddelande till Windows-Domänkontrollanttjänsten för varje angiven tjänst.</span><span class="sxs-lookup"><span data-stu-id="9734f-110">The `Resume-Service` cmdlet sends a resume message to the Windows Service Controller for each of the specified services.</span></span> <span data-ttu-id="9734f-111">Om en tjänst pausas återupptas den.</span><span class="sxs-lookup"><span data-stu-id="9734f-111">If a service is suspended, it resumes.</span></span> <span data-ttu-id="9734f-112">Om den körs, ignoreras meddelandet.</span><span class="sxs-lookup"><span data-stu-id="9734f-112">If it is currently running, the message is ignored.</span></span> <span data-ttu-id="9734f-113">Du kan ange tjänsterna efter tjänst namn eller visnings namn, eller så kan du använda parametern **InputObject** för att skicka ett tjänst objekt som representerar de tjänster som du vill återuppta.</span><span class="sxs-lookup"><span data-stu-id="9734f-113">You can specify the services by their service names or display names, or you can use the **InputObject** parameter to pass a service object that represents the services that you want to resume.</span></span>

## <span data-ttu-id="9734f-114">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="9734f-114">EXAMPLES</span></span>

### <span data-ttu-id="9734f-115">Exempel 1: återuppta en tjänst på den lokala datorn</span><span class="sxs-lookup"><span data-stu-id="9734f-115">Example 1: Resume a service on the local computer</span></span>

```
PS C:\> Resume-Service "sens"
```

<span data-ttu-id="9734f-116">Det här kommandot återupptar tjänsten system Event notification på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="9734f-116">This command resumes the System Event Notification service on the local computer.</span></span> <span data-ttu-id="9734f-117">Tjänst namnet visas i kommandot av Sens.</span><span class="sxs-lookup"><span data-stu-id="9734f-117">The service name is represented in the command by sens.</span></span> <span data-ttu-id="9734f-118">Kommandot använder **Name** -parametern för att ange tjänst namnet för tjänsten, men kommandot utesluter parameter namnet eftersom parameter namnet är valfritt.</span><span class="sxs-lookup"><span data-stu-id="9734f-118">The command uses the **Name** parameter to specify the service name of the service, but the command omits the parameter name because the parameter name is optional.</span></span>

### <span data-ttu-id="9734f-119">Exempel 2: återuppta alla pausade tjänster</span><span class="sxs-lookup"><span data-stu-id="9734f-119">Example 2: Resume all suspended services</span></span>

```
PS C:\> Get-Service | Where-Object {$_.Status -eq "Paused"} | Resume-Service
```

<span data-ttu-id="9734f-120">Detta kommando återupptar alla pausade tjänster på datorn.</span><span class="sxs-lookup"><span data-stu-id="9734f-120">This command resumes all of the suspended services on the computer.</span></span> <span data-ttu-id="9734f-121">`Get-Service`Cmdlet-kommandot hämtar alla tjänster på datorn.</span><span class="sxs-lookup"><span data-stu-id="9734f-121">The `Get-Service` cmdlet command gets all of the services on the computer.</span></span> <span data-ttu-id="9734f-122">Pipeline-operatorn ( `|` ) skickar resultatet till `Where-Object` cmdleten, som väljer de tjänster som har **statusen** pausad.</span><span class="sxs-lookup"><span data-stu-id="9734f-122">The pipeline operator (`|`) passes the results to the `Where-Object` cmdlet, which selects the services that have a **Status** property of Paused.</span></span> <span data-ttu-id="9734f-123">Nästa pipeline-operator skickar resultatet till `Resume-Service` , vilket återupptar de pausade tjänsterna.</span><span class="sxs-lookup"><span data-stu-id="9734f-123">The next pipeline operator sends the results to `Resume-Service`, which resumes the paused services.</span></span>

<span data-ttu-id="9734f-124">I praktiken använder du parametern **whatIf** för att fastställa kommandots effekter innan du kör det.</span><span class="sxs-lookup"><span data-stu-id="9734f-124">In practice, you would use the **WhatIf** parameter to determine the effect of the command before you run it.</span></span>

## <span data-ttu-id="9734f-125">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="9734f-125">PARAMETERS</span></span>

### <span data-ttu-id="9734f-126">-DisplayName</span><span class="sxs-lookup"><span data-stu-id="9734f-126">-DisplayName</span></span>

<span data-ttu-id="9734f-127">Anger visnings namnen för de tjänster som ska återupptas.</span><span class="sxs-lookup"><span data-stu-id="9734f-127">Specifies the display names of the services to be resumed.</span></span>
<span data-ttu-id="9734f-128">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="9734f-128">Wildcard characters are permitted.</span></span>

```yaml
Type: System.String[]
Parameter Sets: DisplayName
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="9734f-129">-Undanta</span><span class="sxs-lookup"><span data-stu-id="9734f-129">-Exclude</span></span>

<span data-ttu-id="9734f-130">Anger tjänster som denna cmdlet utelämnar.</span><span class="sxs-lookup"><span data-stu-id="9734f-130">Specifies services that this cmdlet omits.</span></span> <span data-ttu-id="9734f-131">Värdet för den här parametern kvalificerar parametern **Name** .</span><span class="sxs-lookup"><span data-stu-id="9734f-131">The value of this parameter qualifies the **Name** parameter.</span></span> <span data-ttu-id="9734f-132">Ange ett namn element eller ett mönster, till exempel s \*.</span><span class="sxs-lookup"><span data-stu-id="9734f-132">Enter a name element or pattern, such as s\*.</span></span> <span data-ttu-id="9734f-133">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="9734f-133">Wildcard characters are permitted.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="9734f-134">-Inkludera</span><span class="sxs-lookup"><span data-stu-id="9734f-134">-Include</span></span>

<span data-ttu-id="9734f-135">Anger vilka tjänster som ska återupptas.</span><span class="sxs-lookup"><span data-stu-id="9734f-135">Specifies services to resume.</span></span> <span data-ttu-id="9734f-136">Värdet för den här parametern kvalificerar parametern **Name** .</span><span class="sxs-lookup"><span data-stu-id="9734f-136">The value of this parameter qualifies **Name** parameter.</span></span> <span data-ttu-id="9734f-137">Ange ett namn element eller ett mönster, till exempel s \*.</span><span class="sxs-lookup"><span data-stu-id="9734f-137">Enter a name element or pattern, such as s\*.</span></span> <span data-ttu-id="9734f-138">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="9734f-138">Wildcard characters are permitted.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="9734f-139">– InputObject</span><span class="sxs-lookup"><span data-stu-id="9734f-139">-InputObject</span></span>

<span data-ttu-id="9734f-140">Anger **ServiceController** -objekt som representerar tjänsterna som ska återupptas.</span><span class="sxs-lookup"><span data-stu-id="9734f-140">Specifies **ServiceController** objects that represent the services to resumed.</span></span> <span data-ttu-id="9734f-141">Ange en variabel som innehåller objekten eller Skriv ett kommando eller uttryck som hämtar objekten.</span><span class="sxs-lookup"><span data-stu-id="9734f-141">Enter a variable that contains the objects, or type a command or expression that gets the objects.</span></span>

```yaml
Type: System.ServiceProcess.ServiceController[]
Parameter Sets: InputObject
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="9734f-142">-Name</span><span class="sxs-lookup"><span data-stu-id="9734f-142">-Name</span></span>

<span data-ttu-id="9734f-143">Anger tjänst namnen för de tjänster som ska återupptas.</span><span class="sxs-lookup"><span data-stu-id="9734f-143">Specifies the service names of the services to be resumed.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Default
Aliases: ServiceName

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="9734f-144">– PassThru</span><span class="sxs-lookup"><span data-stu-id="9734f-144">-PassThru</span></span>

<span data-ttu-id="9734f-145">Returnerar ett objekt som representerar tjänsten.</span><span class="sxs-lookup"><span data-stu-id="9734f-145">Returns an object that represents the service.</span></span> <span data-ttu-id="9734f-146">Som standard genererar denna cmdlet inga utdata.</span><span class="sxs-lookup"><span data-stu-id="9734f-146">By default, this cmdlet does not generate any output.</span></span>

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

### <span data-ttu-id="9734f-147">-Confirm</span><span class="sxs-lookup"><span data-stu-id="9734f-147">-Confirm</span></span>

<span data-ttu-id="9734f-148">Uppmanar dig att bekräfta innan du kör cmdleten.</span><span class="sxs-lookup"><span data-stu-id="9734f-148">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="9734f-149">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="9734f-149">-WhatIf</span></span>

<span data-ttu-id="9734f-150">Visar vad som skulle hända om cmdleten kördes.</span><span class="sxs-lookup"><span data-stu-id="9734f-150">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="9734f-151">Cmdleten körs inte.</span><span class="sxs-lookup"><span data-stu-id="9734f-151">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="9734f-152">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="9734f-152">CommonParameters</span></span>

<span data-ttu-id="9734f-153">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="9734f-153">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="9734f-154">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="9734f-154">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="9734f-155">INDATA</span><span class="sxs-lookup"><span data-stu-id="9734f-155">INPUTS</span></span>

### <span data-ttu-id="9734f-156">System. ServiceProcess. ServiceController, system. String</span><span class="sxs-lookup"><span data-stu-id="9734f-156">System.ServiceProcess.ServiceController, System.String</span></span>

<span data-ttu-id="9734f-157">Du kan skicka vidare ett tjänst objekt eller en sträng som innehåller ett tjänst namn till denna cmdlet.</span><span class="sxs-lookup"><span data-stu-id="9734f-157">You can pipe a service object or a string that contains a service name to this cmdlet.</span></span>

## <span data-ttu-id="9734f-158">UTDATA</span><span class="sxs-lookup"><span data-stu-id="9734f-158">OUTPUTS</span></span>

### <span data-ttu-id="9734f-159">Ingen, system. ServiceProcess. ServiceController</span><span class="sxs-lookup"><span data-stu-id="9734f-159">None, System.ServiceProcess.ServiceController</span></span>

<span data-ttu-id="9734f-160">Denna cmdlet genererar ett **system. ServiceProcess. ServiceController** -objekt som representerar den återupptog tjänsten om du anger parametern **Passthru** .</span><span class="sxs-lookup"><span data-stu-id="9734f-160">This cmdlet generates a **System.ServiceProcess.ServiceController** object that represents the resumed service, if you specify the **PassThru** parameter.</span></span> <span data-ttu-id="9734f-161">Annars genererar denna cmdlet inga utdata.</span><span class="sxs-lookup"><span data-stu-id="9734f-161">Otherwise, this cmdlet does not generate any output.</span></span>

## <span data-ttu-id="9734f-162">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="9734f-162">NOTES</span></span>

<span data-ttu-id="9734f-163">Den här cmdleten är endast tillgänglig på Windows-plattformar.</span><span class="sxs-lookup"><span data-stu-id="9734f-163">This cmdlet is only available on Windows platforms.</span></span>

- <span data-ttu-id="9734f-164">Statusen för tjänster som har pausats har pausats.</span><span class="sxs-lookup"><span data-stu-id="9734f-164">The status of services that have been suspended is Paused.</span></span> <span data-ttu-id="9734f-165">När tjänsterna återupptas körs deras status.</span><span class="sxs-lookup"><span data-stu-id="9734f-165">When services are resumed, their status is Running.</span></span>
- <span data-ttu-id="9734f-166">`Resume-Service` kan bara styra tjänster när den aktuella användaren har behörighet att göra detta.</span><span class="sxs-lookup"><span data-stu-id="9734f-166">`Resume-Service` can control services only when the current user has permission to do this.</span></span> <span data-ttu-id="9734f-167">Om ett kommando inte fungerar som det ska kanske du inte har de behörigheter som krävs.</span><span class="sxs-lookup"><span data-stu-id="9734f-167">If a command does not work correctly, you might not have the required permissions.</span></span>
- <span data-ttu-id="9734f-168">Om du vill hitta tjänst namn och visnings namn för tjänsterna i systemet skriver du `Get-Service` .</span><span class="sxs-lookup"><span data-stu-id="9734f-168">To find the service names and display names of the services on your system, type `Get-Service`.</span></span>
  <span data-ttu-id="9734f-169">Tjänst namnen visas i kolumnen **namn** och visnings namnen visas i kolumnen **DisplayName** .</span><span class="sxs-lookup"><span data-stu-id="9734f-169">The service names appear in the **Name** column, and the display names appear in the **DisplayName** column.</span></span>

## <span data-ttu-id="9734f-170">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="9734f-170">RELATED LINKS</span></span>

[<span data-ttu-id="9734f-171">Get-Service</span><span class="sxs-lookup"><span data-stu-id="9734f-171">Get-Service</span></span>](Get-Service.md)

[<span data-ttu-id="9734f-172">New-Service</span><span class="sxs-lookup"><span data-stu-id="9734f-172">New-Service</span></span>](New-Service.md)

[<span data-ttu-id="9734f-173">Restart-Service</span><span class="sxs-lookup"><span data-stu-id="9734f-173">Restart-Service</span></span>](Restart-Service.md)

[<span data-ttu-id="9734f-174">Set-Service</span><span class="sxs-lookup"><span data-stu-id="9734f-174">Set-Service</span></span>](Set-Service.md)

[<span data-ttu-id="9734f-175">Start-Service</span><span class="sxs-lookup"><span data-stu-id="9734f-175">Start-Service</span></span>](Start-Service.md)

[<span data-ttu-id="9734f-176">Stop-Service</span><span class="sxs-lookup"><span data-stu-id="9734f-176">Stop-Service</span></span>](Stop-Service.md)

[<span data-ttu-id="9734f-177">Suspend-Service</span><span class="sxs-lookup"><span data-stu-id="9734f-177">Suspend-Service</span></span>](Suspend-Service.md)

[<span data-ttu-id="9734f-178">Remove-service</span><span class="sxs-lookup"><span data-stu-id="9734f-178">Remove-Service</span></span>](Remove-Service.md)
