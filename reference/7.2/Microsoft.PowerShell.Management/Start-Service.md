---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/start-service?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Start-Service
ms.openlocfilehash: b1df4490da501111ccb44dea2645a333fdf5c27e
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94710380"
---
# <span data-ttu-id="460d7-102">Start-Service</span><span class="sxs-lookup"><span data-stu-id="460d7-102">Start-Service</span></span>

## <span data-ttu-id="460d7-103">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="460d7-103">SYNOPSIS</span></span>
<span data-ttu-id="460d7-104">Startar en eller flera stoppade tjänster.</span><span class="sxs-lookup"><span data-stu-id="460d7-104">Starts one or more stopped services.</span></span>

## <span data-ttu-id="460d7-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="460d7-105">SYNTAX</span></span>

### <span data-ttu-id="460d7-106">InputObject (standard)</span><span class="sxs-lookup"><span data-stu-id="460d7-106">InputObject (Default)</span></span>

```
Start-Service [-InputObject] <ServiceController[]> [-PassThru] [-Include <String[]>] [-Exclude <String[]>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="460d7-107">Standardvärde</span><span class="sxs-lookup"><span data-stu-id="460d7-107">Default</span></span>

```
Start-Service [-Name] <String[]> [-PassThru] [-Include <String[]>] [-Exclude <String[]>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### <span data-ttu-id="460d7-108">DisplayName</span><span class="sxs-lookup"><span data-stu-id="460d7-108">DisplayName</span></span>

```
Start-Service [-PassThru] -DisplayName <String[]> [-Include <String[]>] [-Exclude <String[]>] [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="460d7-109">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="460d7-109">DESCRIPTION</span></span>

<span data-ttu-id="460d7-110">`Start-Service`Cmdleten skickar ett Start meddelande till Windows-Domänkontrollanttjänsten för varje angiven tjänst.</span><span class="sxs-lookup"><span data-stu-id="460d7-110">The `Start-Service` cmdlet sends a start message to the Windows Service Controller for each of the specified services.</span></span> <span data-ttu-id="460d7-111">Om en tjänst redan körs ignoreras meddelandet utan fel.</span><span class="sxs-lookup"><span data-stu-id="460d7-111">If a service is already running, the message is ignored without error.</span></span> <span data-ttu-id="460d7-112">Du kan ange tjänsterna efter tjänst namn eller visnings namn, eller så kan du använda parametern **InputObject** för att ange ett tjänst objekt som representerar de tjänster som du vill starta.</span><span class="sxs-lookup"><span data-stu-id="460d7-112">You can specify the services by their service names or display names, or you can use the **InputObject** parameter to supply a service object that represents the services that you want to start.</span></span>

## <span data-ttu-id="460d7-113">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="460d7-113">EXAMPLES</span></span>

### <span data-ttu-id="460d7-114">Exempel 1: starta en tjänst med hjälp av dess namn</span><span class="sxs-lookup"><span data-stu-id="460d7-114">Example 1: Start a service by using its name</span></span>

<span data-ttu-id="460d7-115">I det här exemplet startas tjänsten EventLog på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="460d7-115">This example starts the EventLog service on the local computer.</span></span> <span data-ttu-id="460d7-116">Parametern **Name** identifierar tjänsten med dess tjänst namn.</span><span class="sxs-lookup"><span data-stu-id="460d7-116">The **Name** parameter identifies the service by its service name.</span></span>

```powershell
Start-Service -Name "eventlog"
```

### <span data-ttu-id="460d7-117">Exempel 2: Visa information utan att starta en tjänst</span><span class="sxs-lookup"><span data-stu-id="460d7-117">Example 2: Display information without starting a service</span></span>

<span data-ttu-id="460d7-118">Det här exemplet visar vad som skulle hända om du startade tjänsterna som har ett visnings namn som innehåller "fjärran".</span><span class="sxs-lookup"><span data-stu-id="460d7-118">This example shows what would occur if you started the services that have a display name that includes "remote".</span></span>

```powershell
Start-Service -DisplayName *remote* -WhatIf
```

<span data-ttu-id="460d7-119">Parametern **DisplayName** identifierar tjänsterna med deras visnings namn i stället för deras tjänst namn.</span><span class="sxs-lookup"><span data-stu-id="460d7-119">The **DisplayName** parameter identifies the services by their display name instead of their service name.</span></span> <span data-ttu-id="460d7-120">Parametern **whatIf** gör att cmdleten visar vad som skulle hända när du kör kommandot men inte gör några ändringar.</span><span class="sxs-lookup"><span data-stu-id="460d7-120">The **WhatIf** parameter causes the cmdlet to display what would happen when you run the command but does not make changes.</span></span>

### <span data-ttu-id="460d7-121">Exempel 3: starta en tjänst och registrera åtgärden i en textfil</span><span class="sxs-lookup"><span data-stu-id="460d7-121">Example 3: Start a service and record the action in a text file</span></span>

<span data-ttu-id="460d7-122">Det här exemplet startar tjänsten Windows Management Instrumentation (WMI) på datorn och lägger till en post för åtgärden i services.txt-filen.</span><span class="sxs-lookup"><span data-stu-id="460d7-122">This example starts the Windows Management Instrumentation (WMI) service on the computer and adds a record of the action to the services.txt file.</span></span>

```powershell
$s = Get-Service wmi
Start-Service -InputObject $s -PassThru | Format-List >> services.txt
```

<span data-ttu-id="460d7-123">Först använder vi `Get-Service` för att hämta ett objekt som representerar WMI-tjänsten och lagrar det i `$s` variabeln.</span><span class="sxs-lookup"><span data-stu-id="460d7-123">First we use `Get-Service` to get an object that represent the WMI service and store it in the `$s` variable.</span></span> <span data-ttu-id="460d7-124">Nu startar vi tjänsten.</span><span class="sxs-lookup"><span data-stu-id="460d7-124">Next, we start the service.</span></span> <span data-ttu-id="460d7-125">Utan parametern **Passthru** `Start-Service` skapas inga utdata.</span><span class="sxs-lookup"><span data-stu-id="460d7-125">Without the **PassThru** parameter, `Start-Service` does not create any output.</span></span> <span data-ttu-id="460d7-126">Pipeline-operatorn (|) skickar objektet utdata från `Start-Service` till `Format-List` cmdleten för att formatera objektet som en lista över dess egenskaper.</span><span class="sxs-lookup"><span data-stu-id="460d7-126">The pipeline operator (|) passes the object output by `Start-Service` to the `Format-List` cmdlet to format the object as a list of its properties.</span></span> <span data-ttu-id="460d7-127">Operatorn Lägg till omdirigering ( \> \> ) dirigerar om utdata till services.txt-filen.</span><span class="sxs-lookup"><span data-stu-id="460d7-127">The append redirection operator (\>\>) redirects the output to the services.txt file.</span></span> <span data-ttu-id="460d7-128">Utdata läggs till i slutet av den befintliga filen.</span><span class="sxs-lookup"><span data-stu-id="460d7-128">The output is added to the end of the existing file.</span></span>

### <span data-ttu-id="460d7-129">Exempel 4: starta en inaktive rad tjänst</span><span class="sxs-lookup"><span data-stu-id="460d7-129">Example 4: Start a disabled service</span></span>

<span data-ttu-id="460d7-130">Det här exemplet visar hur du startar en tjänst när start typen för tjänsten är **inaktive rad**.</span><span class="sxs-lookup"><span data-stu-id="460d7-130">This example shows how to start a service when the start type of the service is **Disabled**.</span></span>

```
PS> Start-Service tlntsvr
Start-Service : Service 'Telnet (TlntSvr)' cannot be started due to the following error: Cannot start service TlntSvr on computer '.'.
At line:1 char:14
+ Start-Service  <<<< tlntsvr

PS> Get-CimInstance win32_service | Where-Object Name -eq "tlntsvr"
ExitCode  : 0
Name      : TlntSvr
ProcessId : 0
StartMode : Disabled
State     : Stopped
Status    : OK

PS> Set-Service tlntsvr -StartupType manual
PS> Start-Service tlntsvr
```

<span data-ttu-id="460d7-131">Det första försöket att starta Telnet-tjänsten (Tlntsvr) misslyckades.</span><span class="sxs-lookup"><span data-stu-id="460d7-131">The first attempt to start the Telnet service (tlntsvr) fails.</span></span> <span data-ttu-id="460d7-132">`Get-CimInstance`Kommandot visar att egenskapen **Start mode** för Tlntsvr-tjänsten är **inaktive rad**.</span><span class="sxs-lookup"><span data-stu-id="460d7-132">The `Get-CimInstance` command shows that the **StartMode** property of the Tlntsvr service is **Disabled**.</span></span> <span data-ttu-id="460d7-133">`Set-Service`Cmdleten ändrar Start typen till **manuell**.</span><span class="sxs-lookup"><span data-stu-id="460d7-133">The `Set-Service` cmdlet changes the start type to **Manual**.</span></span> <span data-ttu-id="460d7-134">Nu kan vi skicka `Start-Service` kommandot igen.</span><span class="sxs-lookup"><span data-stu-id="460d7-134">Now, we can resubmit the `Start-Service` command.</span></span> <span data-ttu-id="460d7-135">Den här gången lyckades kommandot.</span><span class="sxs-lookup"><span data-stu-id="460d7-135">This time, the command succeeds.</span></span> <span data-ttu-id="460d7-136">Verifiera att kommandot har slutförts genom att köra `Get-Service` .</span><span class="sxs-lookup"><span data-stu-id="460d7-136">To verify that the command succeeded, run `Get-Service`.</span></span>

## <span data-ttu-id="460d7-137">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="460d7-137">PARAMETERS</span></span>

### <span data-ttu-id="460d7-138">-DisplayName</span><span class="sxs-lookup"><span data-stu-id="460d7-138">-DisplayName</span></span>

<span data-ttu-id="460d7-139">Anger visnings namnen för de tjänster som ska startas.</span><span class="sxs-lookup"><span data-stu-id="460d7-139">Specifies the display names of the services to start.</span></span> <span data-ttu-id="460d7-140">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="460d7-140">Wildcard characters are permitted.</span></span>

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

### <span data-ttu-id="460d7-141">-Undanta</span><span class="sxs-lookup"><span data-stu-id="460d7-141">-Exclude</span></span>

<span data-ttu-id="460d7-142">Anger tjänster som denna cmdlet utelämnar.</span><span class="sxs-lookup"><span data-stu-id="460d7-142">Specifies services that this cmdlet omits.</span></span> <span data-ttu-id="460d7-143">Värdet för den här parametern kvalificerar parametern **Name** .</span><span class="sxs-lookup"><span data-stu-id="460d7-143">The value of this parameter qualifies the **Name** parameter.</span></span> <span data-ttu-id="460d7-144">Ange ett namn element eller ett mönster, till exempel `s*` .</span><span class="sxs-lookup"><span data-stu-id="460d7-144">Enter a name element or pattern, such as `s*`.</span></span> <span data-ttu-id="460d7-145">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="460d7-145">Wildcard characters are permitted.</span></span>

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

### <span data-ttu-id="460d7-146">-Inkludera</span><span class="sxs-lookup"><span data-stu-id="460d7-146">-Include</span></span>

<span data-ttu-id="460d7-147">Anger tjänster som den här cmdleten startar.</span><span class="sxs-lookup"><span data-stu-id="460d7-147">Specifies services that this cmdlet starts.</span></span> <span data-ttu-id="460d7-148">Värdet för den här parametern kvalificerar parametern **Name** .</span><span class="sxs-lookup"><span data-stu-id="460d7-148">The value of this parameter qualifies the **Name** parameter.</span></span> <span data-ttu-id="460d7-149">Ange ett namn element eller ett mönster, till exempel `s*` .</span><span class="sxs-lookup"><span data-stu-id="460d7-149">Enter a name element or pattern, such as `s*`.</span></span> <span data-ttu-id="460d7-150">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="460d7-150">Wildcard characters are permitted.</span></span>

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

### <span data-ttu-id="460d7-151">– InputObject</span><span class="sxs-lookup"><span data-stu-id="460d7-151">-InputObject</span></span>

<span data-ttu-id="460d7-152">Anger **ServiceController** -objekt som representerar de tjänster som ska startas.</span><span class="sxs-lookup"><span data-stu-id="460d7-152">Specifies **ServiceController** objects representing the services to be started.</span></span> <span data-ttu-id="460d7-153">Ange en variabel som innehåller objekten eller Skriv ett kommando eller uttryck som hämtar objekten.</span><span class="sxs-lookup"><span data-stu-id="460d7-153">Enter a variable that contains the objects, or type a command or expression that gets the objects.</span></span>

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

### <span data-ttu-id="460d7-154">-Name</span><span class="sxs-lookup"><span data-stu-id="460d7-154">-Name</span></span>

<span data-ttu-id="460d7-155">Anger tjänst namnen för den tjänst som ska startas.</span><span class="sxs-lookup"><span data-stu-id="460d7-155">Specifies the service names for the service to be started.</span></span>

<span data-ttu-id="460d7-156">Parameter namnet är valfritt.</span><span class="sxs-lookup"><span data-stu-id="460d7-156">The parameter name is optional.</span></span> <span data-ttu-id="460d7-157">Du kan använda **namn** eller dess alias, **ServiceName** eller så kan du utelämna parameter namnet.</span><span class="sxs-lookup"><span data-stu-id="460d7-157">You can use **Name** or its alias, **ServiceName**, or you can omit the parameter name.</span></span>

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

### <span data-ttu-id="460d7-158">– PassThru</span><span class="sxs-lookup"><span data-stu-id="460d7-158">-PassThru</span></span>

<span data-ttu-id="460d7-159">Returnerar ett objekt som representerar tjänsten.</span><span class="sxs-lookup"><span data-stu-id="460d7-159">Returns an object that represents the service.</span></span> <span data-ttu-id="460d7-160">Som standard genererar denna cmdlet inga utdata.</span><span class="sxs-lookup"><span data-stu-id="460d7-160">By default, this cmdlet does not generate any output.</span></span>

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

### <span data-ttu-id="460d7-161">-Confirm</span><span class="sxs-lookup"><span data-stu-id="460d7-161">-Confirm</span></span>

<span data-ttu-id="460d7-162">Uppmanar dig att bekräfta innan du kör cmdleten.</span><span class="sxs-lookup"><span data-stu-id="460d7-162">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="460d7-163">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="460d7-163">-WhatIf</span></span>

<span data-ttu-id="460d7-164">Visar vad som skulle hända om cmdleten kördes.</span><span class="sxs-lookup"><span data-stu-id="460d7-164">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="460d7-165">Cmdleten körs inte.</span><span class="sxs-lookup"><span data-stu-id="460d7-165">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="460d7-166">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="460d7-166">CommonParameters</span></span>

<span data-ttu-id="460d7-167">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="460d7-167">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="460d7-168">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="460d7-168">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="460d7-169">INDATA</span><span class="sxs-lookup"><span data-stu-id="460d7-169">INPUTS</span></span>

### <span data-ttu-id="460d7-170">System. ServiceProcess. ServiceController, system. String</span><span class="sxs-lookup"><span data-stu-id="460d7-170">System.ServiceProcess.ServiceController, System.String</span></span>

<span data-ttu-id="460d7-171">Du kan skicka pipe-objekt som representerar de tjänster eller strängar som innehåller tjänst namnen till denna cmdlet.</span><span class="sxs-lookup"><span data-stu-id="460d7-171">You can pipe objects that represent the services or strings that contain the service names to this cmdlet.</span></span>

## <span data-ttu-id="460d7-172">UTDATA</span><span class="sxs-lookup"><span data-stu-id="460d7-172">OUTPUTS</span></span>

### <span data-ttu-id="460d7-173">Ingen, system. ServiceProcess. ServiceController</span><span class="sxs-lookup"><span data-stu-id="460d7-173">None, System.ServiceProcess.ServiceController</span></span>

<span data-ttu-id="460d7-174">Denna cmdlet skapar ett **system. ServiceProcess. ServiceController** -objekt som representerar tjänsten om du anger **Passthru**.</span><span class="sxs-lookup"><span data-stu-id="460d7-174">This cmdlet generates a **System.ServiceProcess.ServiceController** object that represents the service, if you specify **PassThru**.</span></span> <span data-ttu-id="460d7-175">Annars genererar denna cmdlet inga utdata.</span><span class="sxs-lookup"><span data-stu-id="460d7-175">Otherwise, this cmdlet does not generate any output.</span></span>

## <span data-ttu-id="460d7-176">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="460d7-176">NOTES</span></span>

<span data-ttu-id="460d7-177">Den här cmdleten är endast tillgänglig på Windows-plattformar.</span><span class="sxs-lookup"><span data-stu-id="460d7-177">This cmdlet is only available on Windows platforms.</span></span>

- <span data-ttu-id="460d7-178">Du kan också referera till `Start-Service` med dess inbyggda alias `sasv` .</span><span class="sxs-lookup"><span data-stu-id="460d7-178">You can also refer to `Start-Service` by its built-in alias, `sasv`.</span></span> <span data-ttu-id="460d7-179">Mer information finns i [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md).</span><span class="sxs-lookup"><span data-stu-id="460d7-179">For more information, see [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md).</span></span>
- <span data-ttu-id="460d7-180">`Start-Service` kan bara styra tjänster om den aktuella användaren har behörighet att göra detta.</span><span class="sxs-lookup"><span data-stu-id="460d7-180">`Start-Service` can control services only if the current user has permission to do this.</span></span> <span data-ttu-id="460d7-181">Om ett kommando inte fungerar som det ska kanske du inte har de behörigheter som krävs.</span><span class="sxs-lookup"><span data-stu-id="460d7-181">If a command does not work correctly, you might not have the required permissions.</span></span>
- <span data-ttu-id="460d7-182">Om du vill hitta tjänst namn och visnings namn för tjänsterna i systemet skriver du `Get-Service` .</span><span class="sxs-lookup"><span data-stu-id="460d7-182">To find the service names and display names of the services on your system, type `Get-Service`.</span></span>
  <span data-ttu-id="460d7-183">Tjänst namnen visas i kolumnen **namn** och visnings namnen visas i kolumnen **DisplayName** .</span><span class="sxs-lookup"><span data-stu-id="460d7-183">The service names appear in the **Name** column, and the display names appear in the **DisplayName** column.</span></span>
- <span data-ttu-id="460d7-184">Du kan bara starta de tjänster som har start typen manuell, automatisk eller automatisk (fördröjd start).</span><span class="sxs-lookup"><span data-stu-id="460d7-184">You can start only the services that have a start type of Manual, Automatic, or Automatic (Delayed Start).</span></span> <span data-ttu-id="460d7-185">Det går inte att starta tjänsterna som har start typen inaktive rad.</span><span class="sxs-lookup"><span data-stu-id="460d7-185">You cannot start the services that have a start type of Disabled.</span></span> <span data-ttu-id="460d7-186">Om ett `Start-Service` kommando Miss lyckas med meddelandet `Cannot start service \<service-name\> on computer` använder `Get-CimInstance` du för att hitta starttyp för tjänsten och om du behöver kan du använda `Set-Service` cmdleten för att ändra start typen för tjänsten.</span><span class="sxs-lookup"><span data-stu-id="460d7-186">If a `Start-Service` command fails with the message `Cannot start service \<service-name\> on computer`, use `Get-CimInstance` to find the start type of the service and, if you have to, use the `Set-Service` cmdlet to change the start type of the service.</span></span>
- <span data-ttu-id="460d7-187">Vissa tjänster, till exempel Prestandaloggar och-varningar (SysmonLog) stoppas automatiskt om de inte har något arbete att göra.</span><span class="sxs-lookup"><span data-stu-id="460d7-187">Some services, such as Performance Logs and Alerts (SysmonLog) stop automatically if they have no work to do.</span></span> <span data-ttu-id="460d7-188">När PowerShell startar en tjänst som stannar nästan omedelbart visas följande meddelande: `Service \<display-name\> start failed.`</span><span class="sxs-lookup"><span data-stu-id="460d7-188">When PowerShell starts a service that stops itself almost immediately, it displays the following message: `Service \<display-name\> start failed.`</span></span>

## <span data-ttu-id="460d7-189">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="460d7-189">RELATED LINKS</span></span>

[<span data-ttu-id="460d7-190">Get-Service</span><span class="sxs-lookup"><span data-stu-id="460d7-190">Get-Service</span></span>](Get-Service.md)

[<span data-ttu-id="460d7-191">New-Service</span><span class="sxs-lookup"><span data-stu-id="460d7-191">New-Service</span></span>](New-Service.md)

[<span data-ttu-id="460d7-192">Restart-Service</span><span class="sxs-lookup"><span data-stu-id="460d7-192">Restart-Service</span></span>](Restart-Service.md)

[<span data-ttu-id="460d7-193">Resume-Service</span><span class="sxs-lookup"><span data-stu-id="460d7-193">Resume-Service</span></span>](Resume-Service.md)

[<span data-ttu-id="460d7-194">Set-Service</span><span class="sxs-lookup"><span data-stu-id="460d7-194">Set-Service</span></span>](Set-Service.md)

[<span data-ttu-id="460d7-195">Stop-Service</span><span class="sxs-lookup"><span data-stu-id="460d7-195">Stop-Service</span></span>](Stop-Service.md)

[<span data-ttu-id="460d7-196">Suspend-Service</span><span class="sxs-lookup"><span data-stu-id="460d7-196">Suspend-Service</span></span>](Suspend-Service.md)

[<span data-ttu-id="460d7-197">Remove-service</span><span class="sxs-lookup"><span data-stu-id="460d7-197">Remove-Service</span></span>](Remove-Service.md)
