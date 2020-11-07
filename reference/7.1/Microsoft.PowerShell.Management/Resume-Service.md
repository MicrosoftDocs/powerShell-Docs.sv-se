---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/resume-service?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Resume-Service
ms.openlocfilehash: d3ef3f9c4c1149523514f222748e33d5945b7e6c
ms.sourcegitcommit: 177ae45034b58ead716853096b2e72e4864e6df6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/07/2020
ms.locfileid: "94346606"
---
# <span data-ttu-id="67f93-103">Resume-Service</span><span class="sxs-lookup"><span data-stu-id="67f93-103">Resume-Service</span></span>

## <span data-ttu-id="67f93-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="67f93-104">SYNOPSIS</span></span>
<span data-ttu-id="67f93-105">Återupptar en eller flera pausade tjänster.</span><span class="sxs-lookup"><span data-stu-id="67f93-105">Resumes one or more suspended (paused) services.</span></span>

## <span data-ttu-id="67f93-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="67f93-106">SYNTAX</span></span>

### <span data-ttu-id="67f93-107">InputObject (standard)</span><span class="sxs-lookup"><span data-stu-id="67f93-107">InputObject (Default)</span></span>

```
Resume-Service [-InputObject] <ServiceController[]> [-PassThru] [-Include <String[]>] [-Exclude <String[]>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="67f93-108">Standard</span><span class="sxs-lookup"><span data-stu-id="67f93-108">Default</span></span>

```
Resume-Service [-Name] <String[]> [-PassThru] [-Include <String[]>] [-Exclude <String[]>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### <span data-ttu-id="67f93-109">DisplayName</span><span class="sxs-lookup"><span data-stu-id="67f93-109">DisplayName</span></span>

```
Resume-Service [-PassThru] -DisplayName <String[]> [-Include <String[]>] [-Exclude <String[]>] [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="67f93-110">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="67f93-110">DESCRIPTION</span></span>

<span data-ttu-id="67f93-111">`Resume-Service`Cmdleten skickar ett återställnings meddelande till Windows-Domänkontrollanttjänsten för varje angiven tjänst.</span><span class="sxs-lookup"><span data-stu-id="67f93-111">The `Resume-Service` cmdlet sends a resume message to the Windows Service Controller for each of the specified services.</span></span> <span data-ttu-id="67f93-112">Om en tjänst pausas återupptas den.</span><span class="sxs-lookup"><span data-stu-id="67f93-112">If a service is suspended, it resumes.</span></span> <span data-ttu-id="67f93-113">Om den körs, ignoreras meddelandet.</span><span class="sxs-lookup"><span data-stu-id="67f93-113">If it is currently running, the message is ignored.</span></span> <span data-ttu-id="67f93-114">Du kan ange tjänsterna efter tjänst namn eller visnings namn, eller så kan du använda parametern **InputObject** för att skicka ett tjänst objekt som representerar de tjänster som du vill återuppta.</span><span class="sxs-lookup"><span data-stu-id="67f93-114">You can specify the services by their service names or display names, or you can use the **InputObject** parameter to pass a service object that represents the services that you want to resume.</span></span>

## <span data-ttu-id="67f93-115">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="67f93-115">EXAMPLES</span></span>

### <span data-ttu-id="67f93-116">Exempel 1: återuppta en tjänst på den lokala datorn</span><span class="sxs-lookup"><span data-stu-id="67f93-116">Example 1: Resume a service on the local computer</span></span>

```
PS C:\> Resume-Service "sens"
```

<span data-ttu-id="67f93-117">Det här kommandot återupptar tjänsten system Event notification på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="67f93-117">This command resumes the System Event Notification service on the local computer.</span></span> <span data-ttu-id="67f93-118">Tjänst namnet visas i kommandot av Sens.</span><span class="sxs-lookup"><span data-stu-id="67f93-118">The service name is represented in the command by sens.</span></span> <span data-ttu-id="67f93-119">Kommandot använder **Name** -parametern för att ange tjänst namnet för tjänsten, men kommandot utesluter parameter namnet eftersom parameter namnet är valfritt.</span><span class="sxs-lookup"><span data-stu-id="67f93-119">The command uses the **Name** parameter to specify the service name of the service, but the command omits the parameter name because the parameter name is optional.</span></span>

### <span data-ttu-id="67f93-120">Exempel 2: återuppta alla pausade tjänster</span><span class="sxs-lookup"><span data-stu-id="67f93-120">Example 2: Resume all suspended services</span></span>

```
PS C:\> Get-Service | Where-Object {$_.Status -eq "Paused"} | Resume-Service
```

<span data-ttu-id="67f93-121">Detta kommando återupptar alla pausade tjänster på datorn.</span><span class="sxs-lookup"><span data-stu-id="67f93-121">This command resumes all of the suspended services on the computer.</span></span> <span data-ttu-id="67f93-122">`Get-Service`Cmdlet-kommandot hämtar alla tjänster på datorn.</span><span class="sxs-lookup"><span data-stu-id="67f93-122">The `Get-Service` cmdlet command gets all of the services on the computer.</span></span> <span data-ttu-id="67f93-123">Pipeline-operatorn ( `|` ) skickar resultatet till `Where-Object` cmdleten, som väljer de tjänster som har **statusen** pausad.</span><span class="sxs-lookup"><span data-stu-id="67f93-123">The pipeline operator (`|`) passes the results to the `Where-Object` cmdlet, which selects the services that have a **Status** property of Paused.</span></span> <span data-ttu-id="67f93-124">Nästa pipeline-operator skickar resultatet till `Resume-Service` , vilket återupptar de pausade tjänsterna.</span><span class="sxs-lookup"><span data-stu-id="67f93-124">The next pipeline operator sends the results to `Resume-Service`, which resumes the paused services.</span></span>

<span data-ttu-id="67f93-125">I praktiken använder du parametern **whatIf** för att fastställa kommandots effekter innan du kör det.</span><span class="sxs-lookup"><span data-stu-id="67f93-125">In practice, you would use the **WhatIf** parameter to determine the effect of the command before you run it.</span></span>

## <span data-ttu-id="67f93-126">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="67f93-126">PARAMETERS</span></span>

### <span data-ttu-id="67f93-127">-DisplayName</span><span class="sxs-lookup"><span data-stu-id="67f93-127">-DisplayName</span></span>

<span data-ttu-id="67f93-128">Anger visnings namnen för de tjänster som ska återupptas.</span><span class="sxs-lookup"><span data-stu-id="67f93-128">Specifies the display names of the services to be resumed.</span></span>
<span data-ttu-id="67f93-129">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="67f93-129">Wildcard characters are permitted.</span></span>

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

### <span data-ttu-id="67f93-130">-Undanta</span><span class="sxs-lookup"><span data-stu-id="67f93-130">-Exclude</span></span>

<span data-ttu-id="67f93-131">Anger tjänster som denna cmdlet utelämnar.</span><span class="sxs-lookup"><span data-stu-id="67f93-131">Specifies services that this cmdlet omits.</span></span> <span data-ttu-id="67f93-132">Värdet för den här parametern kvalificerar parametern **Name** .</span><span class="sxs-lookup"><span data-stu-id="67f93-132">The value of this parameter qualifies the **Name** parameter.</span></span> <span data-ttu-id="67f93-133">Ange ett namn element eller ett mönster, till exempel s \*.</span><span class="sxs-lookup"><span data-stu-id="67f93-133">Enter a name element or pattern, such as s\*.</span></span> <span data-ttu-id="67f93-134">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="67f93-134">Wildcard characters are permitted.</span></span>

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

### <span data-ttu-id="67f93-135">-Inkludera</span><span class="sxs-lookup"><span data-stu-id="67f93-135">-Include</span></span>

<span data-ttu-id="67f93-136">Anger vilka tjänster som ska återupptas.</span><span class="sxs-lookup"><span data-stu-id="67f93-136">Specifies services to resume.</span></span> <span data-ttu-id="67f93-137">Värdet för den här parametern kvalificerar parametern **Name** .</span><span class="sxs-lookup"><span data-stu-id="67f93-137">The value of this parameter qualifies **Name** parameter.</span></span> <span data-ttu-id="67f93-138">Ange ett namn element eller ett mönster, till exempel s \*.</span><span class="sxs-lookup"><span data-stu-id="67f93-138">Enter a name element or pattern, such as s\*.</span></span> <span data-ttu-id="67f93-139">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="67f93-139">Wildcard characters are permitted.</span></span>

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

### <span data-ttu-id="67f93-140">– InputObject</span><span class="sxs-lookup"><span data-stu-id="67f93-140">-InputObject</span></span>

<span data-ttu-id="67f93-141">Anger **ServiceController** -objekt som representerar tjänsterna som ska återupptas.</span><span class="sxs-lookup"><span data-stu-id="67f93-141">Specifies **ServiceController** objects that represent the services to resumed.</span></span> <span data-ttu-id="67f93-142">Ange en variabel som innehåller objekten eller Skriv ett kommando eller uttryck som hämtar objekten.</span><span class="sxs-lookup"><span data-stu-id="67f93-142">Enter a variable that contains the objects, or type a command or expression that gets the objects.</span></span>

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

### <span data-ttu-id="67f93-143">-Name</span><span class="sxs-lookup"><span data-stu-id="67f93-143">-Name</span></span>

<span data-ttu-id="67f93-144">Anger tjänst namnen för de tjänster som ska återupptas.</span><span class="sxs-lookup"><span data-stu-id="67f93-144">Specifies the service names of the services to be resumed.</span></span>

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

### <span data-ttu-id="67f93-145">– PassThru</span><span class="sxs-lookup"><span data-stu-id="67f93-145">-PassThru</span></span>

<span data-ttu-id="67f93-146">Returnerar ett objekt som representerar tjänsten.</span><span class="sxs-lookup"><span data-stu-id="67f93-146">Returns an object that represents the service.</span></span> <span data-ttu-id="67f93-147">Som standard genererar denna cmdlet inga utdata.</span><span class="sxs-lookup"><span data-stu-id="67f93-147">By default, this cmdlet does not generate any output.</span></span>

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

### <span data-ttu-id="67f93-148">-Confirm</span><span class="sxs-lookup"><span data-stu-id="67f93-148">-Confirm</span></span>

<span data-ttu-id="67f93-149">Uppmanar dig att bekräfta innan du kör cmdleten.</span><span class="sxs-lookup"><span data-stu-id="67f93-149">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="67f93-150">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="67f93-150">-WhatIf</span></span>

<span data-ttu-id="67f93-151">Visar vad som skulle hända om cmdleten kördes.</span><span class="sxs-lookup"><span data-stu-id="67f93-151">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="67f93-152">Cmdleten körs inte.</span><span class="sxs-lookup"><span data-stu-id="67f93-152">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="67f93-153">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="67f93-153">CommonParameters</span></span>

<span data-ttu-id="67f93-154">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="67f93-154">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="67f93-155">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="67f93-155">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="67f93-156">INDATA</span><span class="sxs-lookup"><span data-stu-id="67f93-156">INPUTS</span></span>

### <span data-ttu-id="67f93-157">System. ServiceProcess. ServiceController, system. String</span><span class="sxs-lookup"><span data-stu-id="67f93-157">System.ServiceProcess.ServiceController, System.String</span></span>

<span data-ttu-id="67f93-158">Du kan skicka vidare ett tjänst objekt eller en sträng som innehåller ett tjänst namn till denna cmdlet.</span><span class="sxs-lookup"><span data-stu-id="67f93-158">You can pipe a service object or a string that contains a service name to this cmdlet.</span></span>

## <span data-ttu-id="67f93-159">UTDATA</span><span class="sxs-lookup"><span data-stu-id="67f93-159">OUTPUTS</span></span>

### <span data-ttu-id="67f93-160">Ingen, system. ServiceProcess. ServiceController</span><span class="sxs-lookup"><span data-stu-id="67f93-160">None, System.ServiceProcess.ServiceController</span></span>

<span data-ttu-id="67f93-161">Denna cmdlet genererar ett **system. ServiceProcess. ServiceController** -objekt som representerar den återupptog tjänsten om du anger parametern **Passthru** .</span><span class="sxs-lookup"><span data-stu-id="67f93-161">This cmdlet generates a **System.ServiceProcess.ServiceController** object that represents the resumed service, if you specify the **PassThru** parameter.</span></span> <span data-ttu-id="67f93-162">Annars genererar denna cmdlet inga utdata.</span><span class="sxs-lookup"><span data-stu-id="67f93-162">Otherwise, this cmdlet does not generate any output.</span></span>

## <span data-ttu-id="67f93-163">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="67f93-163">NOTES</span></span>

<span data-ttu-id="67f93-164">Den här cmdleten är endast tillgänglig på Windows-plattformar.</span><span class="sxs-lookup"><span data-stu-id="67f93-164">This cmdlet is only available on Windows platforms.</span></span>

- <span data-ttu-id="67f93-165">Statusen för tjänster som har pausats har pausats.</span><span class="sxs-lookup"><span data-stu-id="67f93-165">The status of services that have been suspended is Paused.</span></span> <span data-ttu-id="67f93-166">När tjänsterna återupptas körs deras status.</span><span class="sxs-lookup"><span data-stu-id="67f93-166">When services are resumed, their status is Running.</span></span>
- <span data-ttu-id="67f93-167">`Resume-Service` kan bara styra tjänster när den aktuella användaren har behörighet att göra detta.</span><span class="sxs-lookup"><span data-stu-id="67f93-167">`Resume-Service` can control services only when the current user has permission to do this.</span></span> <span data-ttu-id="67f93-168">Om ett kommando inte fungerar som det ska kanske du inte har de behörigheter som krävs.</span><span class="sxs-lookup"><span data-stu-id="67f93-168">If a command does not work correctly, you might not have the required permissions.</span></span>
- <span data-ttu-id="67f93-169">Om du vill hitta tjänst namn och visnings namn för tjänsterna i systemet skriver du `Get-Service` .</span><span class="sxs-lookup"><span data-stu-id="67f93-169">To find the service names and display names of the services on your system, type `Get-Service`.</span></span>
  <span data-ttu-id="67f93-170">Tjänst namnen visas i kolumnen **namn** och visnings namnen visas i kolumnen **DisplayName** .</span><span class="sxs-lookup"><span data-stu-id="67f93-170">The service names appear in the **Name** column, and the display names appear in the **DisplayName** column.</span></span>

## <span data-ttu-id="67f93-171">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="67f93-171">RELATED LINKS</span></span>

[<span data-ttu-id="67f93-172">Get-Service</span><span class="sxs-lookup"><span data-stu-id="67f93-172">Get-Service</span></span>](Get-Service.md)

[<span data-ttu-id="67f93-173">New-Service</span><span class="sxs-lookup"><span data-stu-id="67f93-173">New-Service</span></span>](New-Service.md)

[<span data-ttu-id="67f93-174">Restart-Service</span><span class="sxs-lookup"><span data-stu-id="67f93-174">Restart-Service</span></span>](Restart-Service.md)

[<span data-ttu-id="67f93-175">Set-Service</span><span class="sxs-lookup"><span data-stu-id="67f93-175">Set-Service</span></span>](Set-Service.md)

[<span data-ttu-id="67f93-176">Start-Service</span><span class="sxs-lookup"><span data-stu-id="67f93-176">Start-Service</span></span>](Start-Service.md)

[<span data-ttu-id="67f93-177">Stop-Service</span><span class="sxs-lookup"><span data-stu-id="67f93-177">Stop-Service</span></span>](Stop-Service.md)

[<span data-ttu-id="67f93-178">Suspend-Service</span><span class="sxs-lookup"><span data-stu-id="67f93-178">Suspend-Service</span></span>](Suspend-Service.md)

[<span data-ttu-id="67f93-179">Remove-service</span><span class="sxs-lookup"><span data-stu-id="67f93-179">Remove-Service</span></span>](Remove-Service.md)
