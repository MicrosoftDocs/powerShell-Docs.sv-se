---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/stop-service?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Stop-Service
ms.openlocfilehash: fac6369859c3f8e3181a9044d381d01c12fea062
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93263774"
---
# <span data-ttu-id="e2075-103">Stop-Service</span><span class="sxs-lookup"><span data-stu-id="e2075-103">Stop-Service</span></span>

## <span data-ttu-id="e2075-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="e2075-104">SYNOPSIS</span></span>
<span data-ttu-id="e2075-105">Stoppar en eller flera tjänster som körs.</span><span class="sxs-lookup"><span data-stu-id="e2075-105">Stops one or more running services.</span></span>

## <span data-ttu-id="e2075-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="e2075-106">SYNTAX</span></span>

### <span data-ttu-id="e2075-107">InputObject (standard)</span><span class="sxs-lookup"><span data-stu-id="e2075-107">InputObject (Default)</span></span>

```
Stop-Service [-Force] [-NoWait] [-InputObject] <ServiceController[]> [-PassThru] [-Include <String[]>]
 [-Exclude <String[]>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="e2075-108">Default</span><span class="sxs-lookup"><span data-stu-id="e2075-108">Default</span></span>

```
Stop-Service [-Force] [-NoWait] [-Name] <String[]> [-PassThru] [-Include <String[]>] [-Exclude <String[]>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="e2075-109">DisplayName</span><span class="sxs-lookup"><span data-stu-id="e2075-109">DisplayName</span></span>

```
Stop-Service [-Force] [-NoWait] [-PassThru] -DisplayName <String[]> [-Include <String[]>] [-Exclude <String[]>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="e2075-110">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="e2075-110">DESCRIPTION</span></span>

<span data-ttu-id="e2075-111">Cmdleten **stoppa-service** skickar ett stopp meddelande till Windows-tjänstens kontrollant för var och en av de angivna tjänsterna.</span><span class="sxs-lookup"><span data-stu-id="e2075-111">The **Stop-Service** cmdlet sends a stop message to the Windows Service Controller for each of the specified services.</span></span>
<span data-ttu-id="e2075-112">Du kan ange tjänsterna efter tjänst namn eller visnings namn, eller så kan du använda parametern **InputObject** för att skicka ett tjänst objekt som representerar den tjänst som du vill stoppa.</span><span class="sxs-lookup"><span data-stu-id="e2075-112">You can specify the services by their service names or display names, or you can use the **InputObject** parameter to pass a service object that represents the service that you want to stop.</span></span>

## <span data-ttu-id="e2075-113">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="e2075-113">EXAMPLES</span></span>

### <span data-ttu-id="e2075-114">Exempel 1: stoppa en tjänst på den lokala datorn</span><span class="sxs-lookup"><span data-stu-id="e2075-114">Example 1: Stop a service on the local computer</span></span>

```
PS C:\> Stop-Service -Name "sysmonlog"
```

<span data-ttu-id="e2075-115">Det här kommandot stoppar Prestandaloggar och-varningar-tjänsten (SysmonLog) på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="e2075-115">This command stops the Performance Logs and Alerts (SysmonLog) service on the local computer.</span></span>

### <span data-ttu-id="e2075-116">Exempel 2: stoppa en tjänst med hjälp av visnings namnet</span><span class="sxs-lookup"><span data-stu-id="e2075-116">Example 2: Stop a service by using the display name</span></span>

```
PS C:\> Get-Service -DisplayName "telnet" | Stop-Service
```

<span data-ttu-id="e2075-117">Det här kommandot stoppar Telnet-tjänsten på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="e2075-117">This command stops the Telnet service on the local computer.</span></span>
<span data-ttu-id="e2075-118">Kommandot använder **Get-service** för att hämta ett objekt som representerar Telnet-tjänsten.</span><span class="sxs-lookup"><span data-stu-id="e2075-118">The command uses **Get-Service** to get an object that represents the Telnet service.</span></span>
<span data-ttu-id="e2075-119">Pipeline-operatorn (|) rör objektet att **stoppa-service** , vilket stoppar tjänsten.</span><span class="sxs-lookup"><span data-stu-id="e2075-119">The pipeline operator (|) pipes the object to **Stop-Service** , which stops the service.</span></span>

### <span data-ttu-id="e2075-120">Exempel 3: stoppa en tjänst som har beroende tjänster</span><span class="sxs-lookup"><span data-stu-id="e2075-120">Example 3: Stop a service that has dependent services</span></span>

```
PS C:\> Get-Service -Name "iisadmin" | Format-List -Property Name, DependentServices
PS C:\> Stop-Service -Name "iisadmin" -Force -Confirm
```

<span data-ttu-id="e2075-121">I det här exemplet stoppas IISAdmin-tjänsten på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="e2075-121">This example stops the IISAdmin service on the local computer.</span></span>
<span data-ttu-id="e2075-122">Eftersom den här tjänsten stoppas stoppas även de tjänster som är beroende av IISAdmin-tjänsten, men det är bäst att föregå **Stop service** med ett kommando som visar de tjänster som är beroende av IISADMIN-tjänsten.</span><span class="sxs-lookup"><span data-stu-id="e2075-122">Because stopping this service also stops the services that depend on the IISAdmin service, it is best to precede **Stop-Service** with a command that lists the services that depend on the IISAdmin service.</span></span>

<span data-ttu-id="e2075-123">Det första kommandot listar de tjänster som är beroende av IISAdmin.</span><span class="sxs-lookup"><span data-stu-id="e2075-123">The first command lists the services that depend on IISAdmin.</span></span>
<span data-ttu-id="e2075-124">Tjänsten använder **Get-service** för att hämta ett objekt som representerar IISADMIN-tjänsten.</span><span class="sxs-lookup"><span data-stu-id="e2075-124">It uses **Get-Service** to get an object that represents the IISAdmin service.</span></span>
<span data-ttu-id="e2075-125">Pipeline-operatorn (|) skickar resultatet till Format-List-cmdlet.</span><span class="sxs-lookup"><span data-stu-id="e2075-125">The pipeline operator (|) passes the result to the Format-List cmdlet.</span></span>
<span data-ttu-id="e2075-126">Kommandot använder *egenskaps* parametern i **format-listan** för att endast lista **namn** och **DependentServices** egenskaper för tjänsten.</span><span class="sxs-lookup"><span data-stu-id="e2075-126">The command uses the *Property* parameter of **Format-List** to list only the **Name** and **DependentServices** properties of the service.</span></span>

<span data-ttu-id="e2075-127">Det andra kommandot stoppar IISAdmin-tjänsten.</span><span class="sxs-lookup"><span data-stu-id="e2075-127">The second command stops the IISAdmin service.</span></span>
<span data-ttu-id="e2075-128">Parametern *Force* krävs för att stoppa en tjänst som har beroende tjänster.</span><span class="sxs-lookup"><span data-stu-id="e2075-128">The *Force* parameter is required to stop a service that has dependent services.</span></span>
<span data-ttu-id="e2075-129">Kommandot använder *Confirm* -parametern för att begära bekräftelse från användaren innan varje tjänst stoppas.</span><span class="sxs-lookup"><span data-stu-id="e2075-129">The command uses the *Confirm* parameter to request confirmation from the user before it stops each service.</span></span>

## <span data-ttu-id="e2075-130">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="e2075-130">PARAMETERS</span></span>

### <span data-ttu-id="e2075-131">-DisplayName</span><span class="sxs-lookup"><span data-stu-id="e2075-131">-DisplayName</span></span>

<span data-ttu-id="e2075-132">Anger visnings namnen för de tjänster som ska stoppas.</span><span class="sxs-lookup"><span data-stu-id="e2075-132">Specifies the display names of the services to stop.</span></span>
<span data-ttu-id="e2075-133">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="e2075-133">Wildcard characters are permitted.</span></span>

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

### <span data-ttu-id="e2075-134">-Undanta</span><span class="sxs-lookup"><span data-stu-id="e2075-134">-Exclude</span></span>

<span data-ttu-id="e2075-135">Anger tjänster som denna cmdlet utelämnar.</span><span class="sxs-lookup"><span data-stu-id="e2075-135">Specifies services that this cmdlet omits.</span></span>
<span data-ttu-id="e2075-136">Värdet för den här parametern kvalificerar parametern *Name* .</span><span class="sxs-lookup"><span data-stu-id="e2075-136">The value of this parameter qualifies the *Name* parameter.</span></span>
<span data-ttu-id="e2075-137">Ange ett namn element eller ett mönster, till exempel s \*.</span><span class="sxs-lookup"><span data-stu-id="e2075-137">Enter a name element or pattern, such as s\*.</span></span>
<span data-ttu-id="e2075-138">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="e2075-138">Wildcard characters are permitted.</span></span>

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

### <span data-ttu-id="e2075-139">-Force</span><span class="sxs-lookup"><span data-stu-id="e2075-139">-Force</span></span>

<span data-ttu-id="e2075-140">Tvingar cmdleten att stoppa en tjänst även om tjänsten har beroende tjänster.</span><span class="sxs-lookup"><span data-stu-id="e2075-140">Forces the cmdlet to stop a service even if that service has dependent services.</span></span>

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

### <span data-ttu-id="e2075-141">-Inkludera</span><span class="sxs-lookup"><span data-stu-id="e2075-141">-Include</span></span>

<span data-ttu-id="e2075-142">Anger tjänster som denna cmdlet stoppar.</span><span class="sxs-lookup"><span data-stu-id="e2075-142">Specifies services that this cmdlet stops.</span></span>
<span data-ttu-id="e2075-143">Värdet för den här parametern kvalificerar parametern *Name* .</span><span class="sxs-lookup"><span data-stu-id="e2075-143">The value of this parameter qualifies the *Name* parameter.</span></span>
<span data-ttu-id="e2075-144">Ange ett namn element eller ett mönster, till exempel s \*.</span><span class="sxs-lookup"><span data-stu-id="e2075-144">Enter a name element or pattern, such as s\*.</span></span>
<span data-ttu-id="e2075-145">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="e2075-145">Wildcard characters are permitted.</span></span>

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

### <span data-ttu-id="e2075-146">– InputObject</span><span class="sxs-lookup"><span data-stu-id="e2075-146">-InputObject</span></span>

<span data-ttu-id="e2075-147">Anger **ServiceController** -objekt som representerar de tjänster som ska stoppas.</span><span class="sxs-lookup"><span data-stu-id="e2075-147">Specifies **ServiceController** objects that represent the services to stop.</span></span>
<span data-ttu-id="e2075-148">Ange en variabel som innehåller objekten eller Skriv ett kommando eller uttryck som hämtar objekten.</span><span class="sxs-lookup"><span data-stu-id="e2075-148">Enter a variable that contains the objects, or type a command or expression that gets the objects.</span></span>

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

### <span data-ttu-id="e2075-149">-Name</span><span class="sxs-lookup"><span data-stu-id="e2075-149">-Name</span></span>

<span data-ttu-id="e2075-150">Anger tjänst namnen för de tjänster som ska stoppas.</span><span class="sxs-lookup"><span data-stu-id="e2075-150">Specifies the service names of the services to stop.</span></span>
<span data-ttu-id="e2075-151">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="e2075-151">Wildcard characters are permitted.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Default
Aliases: ServiceName

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### <span data-ttu-id="e2075-152">-Nowait</span><span class="sxs-lookup"><span data-stu-id="e2075-152">-NoWait</span></span>

<span data-ttu-id="e2075-153">Anger att denna cmdlet använder alternativet No wait.</span><span class="sxs-lookup"><span data-stu-id="e2075-153">Indicates that this cmdlet uses the no wait option.</span></span>

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

### <span data-ttu-id="e2075-154">– PassThru</span><span class="sxs-lookup"><span data-stu-id="e2075-154">-PassThru</span></span>

<span data-ttu-id="e2075-155">Returnerar ett objekt som representerar tjänsten.</span><span class="sxs-lookup"><span data-stu-id="e2075-155">Returns an object that represents the service.</span></span>
<span data-ttu-id="e2075-156">Som standard genererar denna cmdlet inga utdata.</span><span class="sxs-lookup"><span data-stu-id="e2075-156">By default, this cmdlet does not generate any output.</span></span>

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

### <span data-ttu-id="e2075-157">-Confirm</span><span class="sxs-lookup"><span data-stu-id="e2075-157">-Confirm</span></span>

<span data-ttu-id="e2075-158">Uppmanar dig att bekräfta innan du kör cmdleten.</span><span class="sxs-lookup"><span data-stu-id="e2075-158">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="e2075-159">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="e2075-159">-WhatIf</span></span>

<span data-ttu-id="e2075-160">Visar vad som skulle hända om cmdleten kördes.</span><span class="sxs-lookup"><span data-stu-id="e2075-160">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="e2075-161">Cmdleten körs inte.</span><span class="sxs-lookup"><span data-stu-id="e2075-161">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="e2075-162">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="e2075-162">CommonParameters</span></span>

<span data-ttu-id="e2075-163">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="e2075-163">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="e2075-164">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="e2075-164">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="e2075-165">INDATA</span><span class="sxs-lookup"><span data-stu-id="e2075-165">INPUTS</span></span>

### <span data-ttu-id="e2075-166">System. ServiceProcess. ServiceController, system. String</span><span class="sxs-lookup"><span data-stu-id="e2075-166">System.ServiceProcess.ServiceController, System.String</span></span>

<span data-ttu-id="e2075-167">Du kan skicka vidare ett tjänst objekt eller en sträng som innehåller namnet på en tjänst till denna cmdlet.</span><span class="sxs-lookup"><span data-stu-id="e2075-167">You can pipe a service object or a string that contains the name of a service to this cmdlet.</span></span>

## <span data-ttu-id="e2075-168">UTDATA</span><span class="sxs-lookup"><span data-stu-id="e2075-168">OUTPUTS</span></span>

### <span data-ttu-id="e2075-169">Ingen, system. ServiceProcess. ServiceController</span><span class="sxs-lookup"><span data-stu-id="e2075-169">None, System.ServiceProcess.ServiceController</span></span>

<span data-ttu-id="e2075-170">Denna cmdlet skapar ett **system. ServiceProcess. ServiceController** -objekt som representerar tjänsten om du använder parametern *Passthru* .</span><span class="sxs-lookup"><span data-stu-id="e2075-170">This cmdlet generates a **System.ServiceProcess.ServiceController** object that represents the service, if you use the *PassThru* parameter.</span></span>
<span data-ttu-id="e2075-171">Annars genererar denna cmdlet inga utdata.</span><span class="sxs-lookup"><span data-stu-id="e2075-171">Otherwise, this cmdlet does not generate any output.</span></span>

## <span data-ttu-id="e2075-172">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="e2075-172">NOTES</span></span>

* <span data-ttu-id="e2075-173">Du kan också referera till **Stop service** med det inbyggda aliaset **spsv**.</span><span class="sxs-lookup"><span data-stu-id="e2075-173">You can also refer to **Stop-Service** by its built-in alias, **spsv**.</span></span> <span data-ttu-id="e2075-174">Mer information finns i about_Aliases.</span><span class="sxs-lookup"><span data-stu-id="e2075-174">For more information, see about_Aliases.</span></span>

  <span data-ttu-id="e2075-175">**Stoppa-tjänsten** kan bara styra tjänster när den aktuella användaren har behörighet att göra detta.</span><span class="sxs-lookup"><span data-stu-id="e2075-175">**Stop-Service** can control services only when the current user has permission to do this.</span></span>
<span data-ttu-id="e2075-176">Om ett kommando inte fungerar som det ska kanske du inte har de behörigheter som krävs.</span><span class="sxs-lookup"><span data-stu-id="e2075-176">If a command does not work correctly, you might not have the required permissions.</span></span>

  <span data-ttu-id="e2075-177">Om du vill hitta tjänst namn och visnings namn för tjänsterna i systemet skriver du `Get-Service` .</span><span class="sxs-lookup"><span data-stu-id="e2075-177">To find the service names and display names of the services on your system, type `Get-Service`.</span></span>
<span data-ttu-id="e2075-178">Tjänst namnen visas i kolumnen **namn** och visnings namnen visas i kolumnen **DisplayName** .</span><span class="sxs-lookup"><span data-stu-id="e2075-178">The service names appear in the **Name** column and the display names appear in the **DisplayName** column.</span></span>

*

## <span data-ttu-id="e2075-179">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="e2075-179">RELATED LINKS</span></span>

[<span data-ttu-id="e2075-180">Get-Service</span><span class="sxs-lookup"><span data-stu-id="e2075-180">Get-Service</span></span>](Get-Service.md)

[<span data-ttu-id="e2075-181">New-Service</span><span class="sxs-lookup"><span data-stu-id="e2075-181">New-Service</span></span>](New-Service.md)

[<span data-ttu-id="e2075-182">Restart-Service</span><span class="sxs-lookup"><span data-stu-id="e2075-182">Restart-Service</span></span>](Restart-Service.md)

[<span data-ttu-id="e2075-183">Resume-Service</span><span class="sxs-lookup"><span data-stu-id="e2075-183">Resume-Service</span></span>](Resume-Service.md)

[<span data-ttu-id="e2075-184">Set-Service</span><span class="sxs-lookup"><span data-stu-id="e2075-184">Set-Service</span></span>](Set-Service.md)

[<span data-ttu-id="e2075-185">Start-Service</span><span class="sxs-lookup"><span data-stu-id="e2075-185">Start-Service</span></span>](Start-Service.md)

[<span data-ttu-id="e2075-186">Suspend-Service</span><span class="sxs-lookup"><span data-stu-id="e2075-186">Suspend-Service</span></span>](Suspend-Service.md)

[<span data-ttu-id="e2075-187">Remove-service</span><span class="sxs-lookup"><span data-stu-id="e2075-187">Remove-Service</span></span>](Remove-Service.md)
