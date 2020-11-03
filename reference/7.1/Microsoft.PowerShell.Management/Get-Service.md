---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 10/30/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/get-service?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Service
ms.openlocfilehash: 7f44f1d363c5fae79722fdfb5bd894cb24e00d0c
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93267945"
---
# <span data-ttu-id="c8110-103">Get-Service</span><span class="sxs-lookup"><span data-stu-id="c8110-103">Get-Service</span></span>

## <span data-ttu-id="c8110-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="c8110-104">SYNOPSIS</span></span>
<span data-ttu-id="c8110-105">Hämtar tjänsterna på datorn.</span><span class="sxs-lookup"><span data-stu-id="c8110-105">Gets the services on the computer.</span></span>

## <span data-ttu-id="c8110-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="c8110-106">SYNTAX</span></span>

### <span data-ttu-id="c8110-107">Standard (standard)</span><span class="sxs-lookup"><span data-stu-id="c8110-107">Default (Default)</span></span>

```
Get-Service [[-Name] <String[]>] [-DependentServices] [-RequiredServices] [-Include <String[]>]
 [-Exclude <String[]>] [<CommonParameters>]
```

### <span data-ttu-id="c8110-108">DisplayName</span><span class="sxs-lookup"><span data-stu-id="c8110-108">DisplayName</span></span>

```
Get-Service [-DependentServices] [-RequiredServices] -DisplayName <String[]> [-Include <String[]>]
 [-Exclude <String[]>] [<CommonParameters>]
```

### <span data-ttu-id="c8110-109">InputObject</span><span class="sxs-lookup"><span data-stu-id="c8110-109">InputObject</span></span>

```
Get-Service [-DependentServices] [-RequiredServices] [-Include <String[]>] [-Exclude <String[]>]
 [-InputObject <ServiceController[]>] [<CommonParameters>]
```

## <span data-ttu-id="c8110-110">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="c8110-110">DESCRIPTION</span></span>

<span data-ttu-id="c8110-111">`Get-Service`Cmdleten hämtar objekt som representerar tjänsterna på en dator, inklusive tjänster som körs och stoppas.</span><span class="sxs-lookup"><span data-stu-id="c8110-111">The `Get-Service` cmdlet gets objects that represent the services on a computer, including running and stopped services.</span></span> <span data-ttu-id="c8110-112">När körs `Get-Service` utan parametrar returneras som standard den lokala datorns tjänster.</span><span class="sxs-lookup"><span data-stu-id="c8110-112">By default, when `Get-Service` is run without parameters, all the local computer's services are returned.</span></span>

<span data-ttu-id="c8110-113">Du kan dirigera denna cmdlet för att bara få vissa tjänster genom att ange tjänst namnet eller visnings namnet för tjänsterna, eller så kan du skicka pipe-tjänst objekt till denna cmdlet.</span><span class="sxs-lookup"><span data-stu-id="c8110-113">You can direct this cmdlet to get only particular services by specifying the service name or the display name of the services, or you can pipe service objects to this cmdlet.</span></span>

## <span data-ttu-id="c8110-114">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="c8110-114">EXAMPLES</span></span>

### <span data-ttu-id="c8110-115">Exempel 1: Hämta alla tjänster på datorn</span><span class="sxs-lookup"><span data-stu-id="c8110-115">Example 1: Get all services on the computer</span></span>

<span data-ttu-id="c8110-116">Det här exemplet hämtar alla tjänster på datorn.</span><span class="sxs-lookup"><span data-stu-id="c8110-116">This example gets all of the services on the computer.</span></span> <span data-ttu-id="c8110-117">Det fungerar som om du skriver `Get-Service *` .</span><span class="sxs-lookup"><span data-stu-id="c8110-117">It behaves as though you typed `Get-Service *`.</span></span> <span data-ttu-id="c8110-118">Standard visningen visar status, tjänst namn och visnings namn för varje tjänst.</span><span class="sxs-lookup"><span data-stu-id="c8110-118">The default display shows the status, service name, and display name of each service.</span></span>

```powershell
Get-Service
```

### <span data-ttu-id="c8110-119">Exempel 2: Hämta tjänster som börjar med en Sök sträng</span><span class="sxs-lookup"><span data-stu-id="c8110-119">Example 2: Get services that begin with a search string</span></span>

<span data-ttu-id="c8110-120">I det här exemplet hämtas tjänster med tjänst namn som börjar med WMI (Windows Management Instrumentation).</span><span class="sxs-lookup"><span data-stu-id="c8110-120">This example retrieves services with service names that begin with WMI (Windows Management Instrumentation).</span></span>

```powershell
Get-Service "wmi*"
```

### <span data-ttu-id="c8110-121">Exempel 3: Visa tjänster som innehåller en Sök sträng</span><span class="sxs-lookup"><span data-stu-id="c8110-121">Example 3: Display services that include a search string</span></span>

<span data-ttu-id="c8110-122">I det här exemplet visas tjänster med ett visnings namn som innehåller ordet nätverk.</span><span class="sxs-lookup"><span data-stu-id="c8110-122">This example displays services with a display name that includes the word network.</span></span> <span data-ttu-id="c8110-123">Om du söker efter visnings namnet hittar du nätverksrelaterade tjänster även om tjänst namnet inte omfattar net, till exempel xmlprov, nätverks etablerings tjänsten.</span><span class="sxs-lookup"><span data-stu-id="c8110-123">Searching the display name finds network-related services even when the service name doesn't include Net, such as xmlprov, the Network Provisioning Service.</span></span>

```powershell
Get-Service -Displayname "*network*"
```

### <span data-ttu-id="c8110-124">Exempel 4: Hämta tjänster som börjar med en Sök sträng och ett undantag</span><span class="sxs-lookup"><span data-stu-id="c8110-124">Example 4: Get services that begin with a search string and an exclusion</span></span>

<span data-ttu-id="c8110-125">I det här exemplet hämtas endast tjänster med tjänst namn som börjar med **Win** , med undantag för WinRM-tjänsten.</span><span class="sxs-lookup"><span data-stu-id="c8110-125">This example only gets the services with service names that begin with **win** , except for the WinRM service.</span></span>

```powershell
Get-Service -Name "win*" -Exclude "WinRM"
```

### <span data-ttu-id="c8110-126">Exempel 5: Visa tjänster som är aktiva för närvarande</span><span class="sxs-lookup"><span data-stu-id="c8110-126">Example 5: Display services that are currently active</span></span>

<span data-ttu-id="c8110-127">I det här exemplet visas endast tjänsterna med statusen körs.</span><span class="sxs-lookup"><span data-stu-id="c8110-127">This example displays only the services with a status of Running.</span></span>

```powershell
Get-Service | Where-Object {$_.Status -eq "Running"}
```

<span data-ttu-id="c8110-128">`Get-Service` hämtar alla tjänster på datorn och skickar objekten nedåt i pipelinen.</span><span class="sxs-lookup"><span data-stu-id="c8110-128">`Get-Service` gets all the services on the computer and sends the objects down the pipeline.</span></span> <span data-ttu-id="c8110-129">`Where-Object`Cmdlet: en väljer bara de tjänster med en **status** egenskap som är lika med kör.</span><span class="sxs-lookup"><span data-stu-id="c8110-129">The `Where-Object` cmdlet, selects only the services with a **Status** property that equals Running.</span></span>

<span data-ttu-id="c8110-130">Status är bara en egenskap för tjänst objekt.</span><span class="sxs-lookup"><span data-stu-id="c8110-130">Status is only one property of service objects.</span></span> <span data-ttu-id="c8110-131">Om du vill se alla egenskaper skriver du `Get-Service | Get-Member` .</span><span class="sxs-lookup"><span data-stu-id="c8110-131">To see all of the properties, type `Get-Service | Get-Member`.</span></span>

### <span data-ttu-id="c8110-132">Exempel 6: Visa en lista över tjänsterna på datorn som har beroende tjänster</span><span class="sxs-lookup"><span data-stu-id="c8110-132">Example 6: List the services on the computer that have dependent services</span></span>

<span data-ttu-id="c8110-133">Det här exemplet hämtar tjänster som har beroende tjänster.</span><span class="sxs-lookup"><span data-stu-id="c8110-133">This example gets services that have dependent services.</span></span>

```powershell
Get-Service |
  Where-Object {$_.DependentServices} |
    Format-List -Property Name, DependentServices, @{
      Label="NoOfDependentServices"; Expression={$_.dependentservices.count}
    }
```

```Output
Name                  : AudioEndpointBuilder
DependentServices     : {AudioSrv}
NoOfDependentServices : 1

Name                  : Dhcp
DependentServices     : {WinHttpAutoProxySvc}
NoOfDependentServices : 1
...
```

<span data-ttu-id="c8110-134">`Get-Service`Cmdlet: en hämtar alla tjänster på datorn och skickar objekten nedåt i pipelinen.</span><span class="sxs-lookup"><span data-stu-id="c8110-134">The `Get-Service` cmdlet gets all the services on the computer and sends the objects down the pipeline.</span></span> <span data-ttu-id="c8110-135">`Where-Object`Cmdleten väljer de tjänster vars **DependentServices** -egenskap inte är null.</span><span class="sxs-lookup"><span data-stu-id="c8110-135">The `Where-Object` cmdlet selects the services whose **DependentServices** property isn't null.</span></span>

<span data-ttu-id="c8110-136">Resultaten skickas ned pipelinen till `Format-List` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="c8110-136">The results are sent down the pipeline to the `Format-List` cmdlet.</span></span> <span data-ttu-id="c8110-137">**Egenskaps** parametern visar namnet på tjänsten, namnet på de beroende tjänsterna och en beräknad egenskap som visar antalet beroende tjänster för varje tjänst.</span><span class="sxs-lookup"><span data-stu-id="c8110-137">The **Property** parameter displays the name of the service, the name of the dependent services, and a calculated property that displays the number of dependent services for each service.</span></span>

### <span data-ttu-id="c8110-138">Exempel 7: sortera tjänster efter egenskaps värde</span><span class="sxs-lookup"><span data-stu-id="c8110-138">Example 7: Sort services by property value</span></span>

<span data-ttu-id="c8110-139">Det här exemplet visar att när du sorterar tjänster i stigande ordning efter värdet för deras **status** egenskap visas stoppade tjänster innan tjänsterna körs.</span><span class="sxs-lookup"><span data-stu-id="c8110-139">This example shows that when you sort services in ascending order by the value of their **Status** property, stopped services appear before running services.</span></span> <span data-ttu-id="c8110-140">Orsaken är att värdet för **status** är en uppräkning, där stoppad har värdet 1 och körs har värdet 4.</span><span class="sxs-lookup"><span data-stu-id="c8110-140">The reason is because the value of **Status** is an enumeration, in which Stopped has a value of 1, and Running has a value of 4.</span></span> <span data-ttu-id="c8110-141">Mer information finns i [ServiceControllerStatus](/dotnet/api/system.serviceprocess.servicecontrollerstatus).</span><span class="sxs-lookup"><span data-stu-id="c8110-141">For more information, see [ServiceControllerStatus](/dotnet/api/system.serviceprocess.servicecontrollerstatus).</span></span>

<span data-ttu-id="c8110-142">Om du vill visa en lista med tjänster som körs först använder du parametern **fallande** i `Sort-Object` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="c8110-142">To list running services first, use the **Descending** parameter of the `Sort-Object` cmdlet.</span></span>

```powershell
Get-Service "s*" | Sort-Object status
```

```Output
Status   Name               DisplayName
------   ----               -----------
Stopped  stisvc             Windows Image Acquisition (WIA)
Stopped  SwPrv              MS Software Shadow Copy Provider
Stopped  SysmonLog          Performance Logs and Alerts
Running  Spooler            Print Spooler
Running  srservice          System Restore Service
Running  SSDPSRV            SSDP Discovery Service
Running  ShellHWDetection   Shell Hardware Detection
Running  Schedule           Task Scheduler
Running  SCardSvr           Smart Card
Running  SamSs              Security Accounts Manager
Running  SharedAccess       Windows Firewall/Internet Connectio...
Running  SENS               System Event Notification
Running  seclogon           Secondary Logon
```

### <span data-ttu-id="c8110-143">Exempel 8: Hämta de beroende tjänsterna för en tjänst</span><span class="sxs-lookup"><span data-stu-id="c8110-143">Example 8: Get the dependent services of a service</span></span>

<span data-ttu-id="c8110-144">Det här exemplet hämtar de tjänster som krävs av WinRM-tjänsten.</span><span class="sxs-lookup"><span data-stu-id="c8110-144">This example gets the services that the WinRM service requires.</span></span> <span data-ttu-id="c8110-145">Värdet för tjänstens **ServicesDependedOn** -egenskap returneras.</span><span class="sxs-lookup"><span data-stu-id="c8110-145">The value of the service's **ServicesDependedOn** property is returned.</span></span>

```powershell
Get-Service "WinRM" -RequiredServices
```

### <span data-ttu-id="c8110-146">Exempel 9: Hämta en tjänst via pipeline-operatören</span><span class="sxs-lookup"><span data-stu-id="c8110-146">Example 9: Get a service through the pipeline operator</span></span>

<span data-ttu-id="c8110-147">Det här exemplet hämtar WinRM-tjänsten på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="c8110-147">This example gets the WinRM service on the local computer.</span></span> <span data-ttu-id="c8110-148">Tjänst namn strängen, som omges av citat tecken, skickas till pipelinen `Get-Service` .</span><span class="sxs-lookup"><span data-stu-id="c8110-148">The service name string, enclosed in quotation marks, is sent down the pipeline to `Get-Service`.</span></span>

```powershell
"WinRM" | Get-Service
```

## <span data-ttu-id="c8110-149">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="c8110-149">PARAMETERS</span></span>

### <span data-ttu-id="c8110-150">-DependentServices</span><span class="sxs-lookup"><span data-stu-id="c8110-150">-DependentServices</span></span>

<span data-ttu-id="c8110-151">Anger att denna cmdlet endast hämtar de tjänster som är beroende av den angivna tjänsten.</span><span class="sxs-lookup"><span data-stu-id="c8110-151">Indicates that this cmdlet gets only the services that depend upon the specified service.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: DS

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="c8110-152">-DisplayName</span><span class="sxs-lookup"><span data-stu-id="c8110-152">-DisplayName</span></span>

<span data-ttu-id="c8110-153">Anger, som en sträng mat ris, visnings namnen för de tjänster som ska hämtas.</span><span class="sxs-lookup"><span data-stu-id="c8110-153">Specifies, as a string array, the display names of services to be retrieved.</span></span> <span data-ttu-id="c8110-154">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="c8110-154">Wildcards are permitted.</span></span>

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

### <span data-ttu-id="c8110-155">-Undanta</span><span class="sxs-lookup"><span data-stu-id="c8110-155">-Exclude</span></span>

<span data-ttu-id="c8110-156">Anger, som en sträng mat ris, en tjänst eller tjänster som denna cmdlet exkluderar från åtgärden.</span><span class="sxs-lookup"><span data-stu-id="c8110-156">Specifies, as a string array, a service or services that this cmdlet excludes from the operation.</span></span>
<span data-ttu-id="c8110-157">Värdet för den här parametern kvalificerar parametern **Name** .</span><span class="sxs-lookup"><span data-stu-id="c8110-157">The value of this parameter qualifies the **Name** parameter.</span></span> <span data-ttu-id="c8110-158">Ange ett namn element eller ett mönster, till exempel `s*` .</span><span class="sxs-lookup"><span data-stu-id="c8110-158">Enter a name element or pattern, such as `s*`.</span></span> <span data-ttu-id="c8110-159">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="c8110-159">Wildcards are permitted.</span></span>

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

### <span data-ttu-id="c8110-160">-Inkludera</span><span class="sxs-lookup"><span data-stu-id="c8110-160">-Include</span></span>

<span data-ttu-id="c8110-161">Anger, som en sträng mat ris, en tjänst eller tjänster som denna cmdlet inkluderar i åtgärden.</span><span class="sxs-lookup"><span data-stu-id="c8110-161">Specifies, as a string array, a service or services that this cmdlet includes in the operation.</span></span> <span data-ttu-id="c8110-162">Värdet för den här parametern kvalificerar parametern **Name** .</span><span class="sxs-lookup"><span data-stu-id="c8110-162">The value of this parameter qualifies the **Name** parameter.</span></span> <span data-ttu-id="c8110-163">Ange ett namn element eller ett mönster, till exempel `s*` .</span><span class="sxs-lookup"><span data-stu-id="c8110-163">Enter a name element or pattern, such as `s*`.</span></span> <span data-ttu-id="c8110-164">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="c8110-164">Wildcards are permitted.</span></span>

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

### <span data-ttu-id="c8110-165">– InputObject</span><span class="sxs-lookup"><span data-stu-id="c8110-165">-InputObject</span></span>

<span data-ttu-id="c8110-166">Anger **ServiceController** -objekt som representerar de tjänster som ska hämtas.</span><span class="sxs-lookup"><span data-stu-id="c8110-166">Specifies **ServiceController** objects representing the services to be retrieved.</span></span> <span data-ttu-id="c8110-167">Ange en variabel som innehåller objekten eller Skriv ett kommando eller uttryck som hämtar objekten.</span><span class="sxs-lookup"><span data-stu-id="c8110-167">Enter a variable that contains the objects, or type a command or expression that gets the objects.</span></span> <span data-ttu-id="c8110-168">Du kan skicka vidare ett tjänst objekt till denna cmdlet.</span><span class="sxs-lookup"><span data-stu-id="c8110-168">You can pipe a service object to this cmdlet.</span></span>

```yaml
Type: System.ServiceProcess.ServiceController[]
Parameter Sets: InputObject
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="c8110-169">-Name</span><span class="sxs-lookup"><span data-stu-id="c8110-169">-Name</span></span>

<span data-ttu-id="c8110-170">Anger tjänst namnen för de tjänster som ska hämtas.</span><span class="sxs-lookup"><span data-stu-id="c8110-170">Specifies the service names of services to be retrieved.</span></span> <span data-ttu-id="c8110-171">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="c8110-171">Wildcards are permitted.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Default
Aliases: ServiceName

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### <span data-ttu-id="c8110-172">-RequiredServices</span><span class="sxs-lookup"><span data-stu-id="c8110-172">-RequiredServices</span></span>

<span data-ttu-id="c8110-173">Anger att denna cmdlet bara hämtar de tjänster som krävs för den här tjänsten.</span><span class="sxs-lookup"><span data-stu-id="c8110-173">Indicates that this cmdlet gets only the services that this service requires.</span></span> <span data-ttu-id="c8110-174">Den här parametern hämtar värdet för tjänstens **ServicesDependedOn** -egenskap.</span><span class="sxs-lookup"><span data-stu-id="c8110-174">This parameter gets the value of the **ServicesDependedOn** property of the service.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: SDO, ServicesDependedOn

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="c8110-175">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="c8110-175">CommonParameters</span></span>

<span data-ttu-id="c8110-176">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="c8110-176">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="c8110-177">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="c8110-177">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="c8110-178">INDATA</span><span class="sxs-lookup"><span data-stu-id="c8110-178">INPUTS</span></span>

### <span data-ttu-id="c8110-179">System. ServiceProcess. ServiceController, system. String</span><span class="sxs-lookup"><span data-stu-id="c8110-179">System.ServiceProcess.ServiceController, System.String</span></span>

<span data-ttu-id="c8110-180">Du kan skicka vidare ett tjänst objekt eller ett tjänst namn till denna cmdlet.</span><span class="sxs-lookup"><span data-stu-id="c8110-180">You can pipe a service object or a service name to this cmdlet.</span></span>

## <span data-ttu-id="c8110-181">UTDATA</span><span class="sxs-lookup"><span data-stu-id="c8110-181">OUTPUTS</span></span>

### <span data-ttu-id="c8110-182">System. ServiceProcess. ServiceController</span><span class="sxs-lookup"><span data-stu-id="c8110-182">System.ServiceProcess.ServiceController</span></span>

<span data-ttu-id="c8110-183">Denna cmdlet returnerar objekt som representerar tjänsterna på datorn.</span><span class="sxs-lookup"><span data-stu-id="c8110-183">This cmdlet returns objects that represent the services on the computer.</span></span>

## <span data-ttu-id="c8110-184">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="c8110-184">NOTES</span></span>

<span data-ttu-id="c8110-185">Från och med PowerShell 6,0 läggs följande egenskaper till i **ServiceController** -objekten: **username** , **Description** , **DelayedAutoStart** , **BinaryPathName** och **startuptype tjänst** .</span><span class="sxs-lookup"><span data-stu-id="c8110-185">Beginning in PowerShell 6.0, the following properties are added to the **ServiceController** objects: **UserName** , **Description** , **DelayedAutoStart** , **BinaryPathName** , and **StartupType** .</span></span>

<span data-ttu-id="c8110-186">Du kan också referera till `Get-Service` med dess inbyggda alias `gsv` .</span><span class="sxs-lookup"><span data-stu-id="c8110-186">You can also refer to `Get-Service` by its built-in alias, `gsv`.</span></span> <span data-ttu-id="c8110-187">Mer information finns i [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md).</span><span class="sxs-lookup"><span data-stu-id="c8110-187">For more information, see [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md).</span></span>

<span data-ttu-id="c8110-188">Den här cmdleten kan endast Visa tjänster när den aktuella användaren har behörighet att se dem.</span><span class="sxs-lookup"><span data-stu-id="c8110-188">This cmdlet can display services only when the current user has permission to see them.</span></span> <span data-ttu-id="c8110-189">Om denna cmdlet inte visar tjänster kanske du inte har behörighet att se dem.</span><span class="sxs-lookup"><span data-stu-id="c8110-189">If this cmdlet does not display services, you might not have permission to see them.</span></span>

<span data-ttu-id="c8110-190">Om du vill hitta tjänst namnet och visnings namnet för varje tjänst i systemet skriver du `Get-Service` .</span><span class="sxs-lookup"><span data-stu-id="c8110-190">To find the service name and display name of each service on your system, type `Get-Service`.</span></span> <span data-ttu-id="c8110-191">Tjänst namnen visas i kolumnen namn och visnings namnen visas i kolumnen **DisplayName** .</span><span class="sxs-lookup"><span data-stu-id="c8110-191">The service names appear in the Name column, and the display names appear in the **DisplayName** column.</span></span>

<span data-ttu-id="c8110-192">När du sorterar i stigande ordning efter värdet för egenskapen **status** visas stoppade tjänster innan tjänsterna körs.</span><span class="sxs-lookup"><span data-stu-id="c8110-192">When you sort in ascending order by the **Status** property's value, Stopped services appear before Running services.</span></span> <span data-ttu-id="c8110-193">Tjänstens **status** egenskap är ett uppräknat värde och status namnen representerar heltals värden.</span><span class="sxs-lookup"><span data-stu-id="c8110-193">The service's **Status** property is an enumerated value and the status names represent integer values.</span></span> <span data-ttu-id="c8110-194">Sorterings ordningen baseras på heltal svärdet, inte namnet.</span><span class="sxs-lookup"><span data-stu-id="c8110-194">The sort order is based on the integer value, not the name.</span></span> <span data-ttu-id="c8110-195">Stoppad visas innan eftersom det stoppades eftersom det stoppats, och det har värdet 1, och körning har värdet 4.</span><span class="sxs-lookup"><span data-stu-id="c8110-195">Stopped appears before because Running because Stopped has a value of 1, and Running has a value of 4.</span></span> <span data-ttu-id="c8110-196">Mer information finns i [ServiceControllerStatus](/dotnet/api/system.serviceprocess.servicecontrollerstatus).</span><span class="sxs-lookup"><span data-stu-id="c8110-196">For more information, see [ServiceControllerStatus](/dotnet/api/system.serviceprocess.servicecontrollerstatus).</span></span>

## <span data-ttu-id="c8110-197">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="c8110-197">RELATED LINKS</span></span>

[<span data-ttu-id="c8110-198">New-Service</span><span class="sxs-lookup"><span data-stu-id="c8110-198">New-Service</span></span>](New-Service.md)

[<span data-ttu-id="c8110-199">Restart-Service</span><span class="sxs-lookup"><span data-stu-id="c8110-199">Restart-Service</span></span>](Restart-Service.md)

[<span data-ttu-id="c8110-200">Resume-Service</span><span class="sxs-lookup"><span data-stu-id="c8110-200">Resume-Service</span></span>](Resume-Service.md)

[<span data-ttu-id="c8110-201">Set-Service</span><span class="sxs-lookup"><span data-stu-id="c8110-201">Set-Service</span></span>](Set-Service.md)

[<span data-ttu-id="c8110-202">Start-Service</span><span class="sxs-lookup"><span data-stu-id="c8110-202">Start-Service</span></span>](Start-Service.md)

[<span data-ttu-id="c8110-203">Stop-Service</span><span class="sxs-lookup"><span data-stu-id="c8110-203">Stop-Service</span></span>](Stop-Service.md)

[<span data-ttu-id="c8110-204">Suspend-Service</span><span class="sxs-lookup"><span data-stu-id="c8110-204">Suspend-Service</span></span>](Suspend-Service.md)

[<span data-ttu-id="c8110-205">Remove-service</span><span class="sxs-lookup"><span data-stu-id="c8110-205">Remove-Service</span></span>](Remove-Service.md)

