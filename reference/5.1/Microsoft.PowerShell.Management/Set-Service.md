---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 10/25/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/set-service?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-Service
ms.openlocfilehash: df4fda68508e21700235d2b772c6dd43c8e1fe1e
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93265377"
---
# <span data-ttu-id="4e963-103">Set-Service</span><span class="sxs-lookup"><span data-stu-id="4e963-103">Set-Service</span></span>

## <span data-ttu-id="4e963-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="4e963-104">SYNOPSIS</span></span>
<span data-ttu-id="4e963-105">Startar, stoppar och pausar en tjänst och ändrar dess egenskaper.</span><span class="sxs-lookup"><span data-stu-id="4e963-105">Starts, stops, and suspends a service, and changes its properties.</span></span>

## <span data-ttu-id="4e963-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="4e963-106">SYNTAX</span></span>

### <span data-ttu-id="4e963-107">Namn (standard)</span><span class="sxs-lookup"><span data-stu-id="4e963-107">Name (Default)</span></span>

```
Set-Service [-ComputerName <String[]>] [-Name] <String> [-DisplayName <String>]
 [-Description <String>] [-StartupType <ServiceStartMode>] [-Status <String>] [-PassThru] [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="4e963-108">InputObject</span><span class="sxs-lookup"><span data-stu-id="4e963-108">InputObject</span></span>

```
Set-Service [-ComputerName <String[]>] [-DisplayName <String>] [-Description <String>]
 [-StartupType <ServiceStartMode>] [-Status <String>] [-InputObject <ServiceController>] [-PassThru]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="4e963-109">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="4e963-109">DESCRIPTION</span></span>

<span data-ttu-id="4e963-110">`Set-Service`Cmdleten ändrar egenskaperna för en tjänst, till exempel **status** , **Beskrivning** , **DisplayName** och **startuptype tjänst**.</span><span class="sxs-lookup"><span data-stu-id="4e963-110">The `Set-Service` cmdlet changes the properties of a service such as the **Status** , **Description** , **DisplayName** , and **StartupType**.</span></span> <span data-ttu-id="4e963-111">`Set-Service` kan starta, stoppa, pausa eller pausa en tjänst.</span><span class="sxs-lookup"><span data-stu-id="4e963-111">`Set-Service` can start, stop, suspend, or pause a service.</span></span> <span data-ttu-id="4e963-112">För att identifiera en tjänst anger du dess tjänst namn eller skickar ett tjänst objekt.</span><span class="sxs-lookup"><span data-stu-id="4e963-112">To identify a service, enter its service name or submit a service object.</span></span> <span data-ttu-id="4e963-113">Eller skicka ett tjänst namn eller tjänst objekt nedåt i pipeline till `Set-Service` .</span><span class="sxs-lookup"><span data-stu-id="4e963-113">Or, send a service name or service object down the pipeline to `Set-Service`.</span></span>

## <span data-ttu-id="4e963-114">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="4e963-114">EXAMPLES</span></span>

### <span data-ttu-id="4e963-115">Exempel 1: ändra ett visnings namn</span><span class="sxs-lookup"><span data-stu-id="4e963-115">Example 1: Change a display name</span></span>

<span data-ttu-id="4e963-116">I det här exemplet ändras en tjänsts visnings namn.</span><span class="sxs-lookup"><span data-stu-id="4e963-116">In this example, a service's display name is changed.</span></span> <span data-ttu-id="4e963-117">Använd om du vill visa det ursprungliga visnings namnet `Get-Service` .</span><span class="sxs-lookup"><span data-stu-id="4e963-117">To view the original display name, use `Get-Service`.</span></span>

```powershell
Set-Service -Name LanmanWorkstation -DisplayName "LanMan Workstation"
```

<span data-ttu-id="4e963-118">`Set-Service` använder **Name** -parametern för att ange tjänstens namn, **LanmanWorkstation**.</span><span class="sxs-lookup"><span data-stu-id="4e963-118">`Set-Service` uses the **Name** parameter to specify the service's name, **LanmanWorkstation**.</span></span> <span data-ttu-id="4e963-119">Parametern **DisplayName** anger det nya visnings namnet, **LANMAN-arbetsstationen**.</span><span class="sxs-lookup"><span data-stu-id="4e963-119">The **DisplayName** parameter specifies the new display name, **LanMan Workstation**.</span></span>

### <span data-ttu-id="4e963-120">Exempel 2: ändra start typen för tjänster</span><span class="sxs-lookup"><span data-stu-id="4e963-120">Example 2: Change the startup type of services</span></span>

<span data-ttu-id="4e963-121">Det här exemplet visar hur du ändrar Start typen för en tjänst.</span><span class="sxs-lookup"><span data-stu-id="4e963-121">This example shows how to change a service's startup type.</span></span>

```powershell
Set-Service -Name BITS -StartupType Automatic
Get-Service BITS | Select-Object -Property Name, StartType, Status
```

```Output
Name  StartType   Status
----  ---------   ------
BITS  Automatic  Running
```

<span data-ttu-id="4e963-122">`Set-Service` använder **Name** -parametern för att ange tjänstens namn, **bitar**.</span><span class="sxs-lookup"><span data-stu-id="4e963-122">`Set-Service` uses the **Name** parameter to specify the service's name, **BITS**.</span></span> <span data-ttu-id="4e963-123">Parametern **startuptype tjänst** anger att tjänsten ska vara **Automatisk**.</span><span class="sxs-lookup"><span data-stu-id="4e963-123">The **StartupType** parameter sets the service to **Automatic**.</span></span>

<span data-ttu-id="4e963-124">`Get-Service` använder **Name** -parametern för att ange **BITS** -tjänsten och skickar objektet nedåt i pipelinen.</span><span class="sxs-lookup"><span data-stu-id="4e963-124">`Get-Service` uses the **Name** parameter to specify the **BITS** service and sends the object down the pipeline.</span></span> <span data-ttu-id="4e963-125">`Select-Object` använder **egenskaps** parametern för att visa **BITS** -tjänstens status.</span><span class="sxs-lookup"><span data-stu-id="4e963-125">`Select-Object` uses the **Property** parameter to display the **BITS** service's status.</span></span>

### <span data-ttu-id="4e963-126">Exempel 3: ändra beskrivningen av en tjänst</span><span class="sxs-lookup"><span data-stu-id="4e963-126">Example 3: Change the description of a service</span></span>

<span data-ttu-id="4e963-127">Det här exemplet ändrar beskrivningen av BITS-tjänsten och visar resultatet.</span><span class="sxs-lookup"><span data-stu-id="4e963-127">This example changes the BITS service's description and displays the result.</span></span>

<span data-ttu-id="4e963-128">`Get-CimInstance`Cmdleten används eftersom den returnerar ett **Win32_Service** -objekt som innehåller tjänstens **Beskrivning**.</span><span class="sxs-lookup"><span data-stu-id="4e963-128">The `Get-CimInstance` cmdlet is used because it returns a **Win32_Service** object that includes the service's **Description**.</span></span>

```powershell
Get-CimInstance Win32_Service -Filter 'Name = "BITS"'  | Format-List  Name, Description
```

```Output
Name        : BITS
Description : Transfers files in the background using idle network bandwidth. If the service is
              disabled, then any applications that depend on BITS, such as Windows Update or MSN
              Explorer, will be unable to automatically download programs and other information.
```

```powershell
Set-Service -Name BITS -Description "Transfers files in the background using idle network bandwidth."
Get-CimInstance Win32_Service -Filter 'Name = "BITS"' | Format-List  Name, Description
```

```Output
Name        : BITS
Description : Transfers files in the background using idle network bandwidth.
```

<span data-ttu-id="4e963-129">`Get-CimInstance` skickar objektet nedåt i pipeline till `Format-List` och visar tjänstens namn och beskrivning.</span><span class="sxs-lookup"><span data-stu-id="4e963-129">`Get-CimInstance` sends the object down the pipeline to `Format-List` and displays the service's name and description.</span></span> <span data-ttu-id="4e963-130">I jämförelse syfte körs kommandot före och efter att beskrivningen har uppdaterats.</span><span class="sxs-lookup"><span data-stu-id="4e963-130">For comparison purposes, the command is run before and after the description is updated.</span></span>

<span data-ttu-id="4e963-131">`Set-Service` använder **Name** -parametern för att ange **BITS** -tjänsten.</span><span class="sxs-lookup"><span data-stu-id="4e963-131">`Set-Service` uses the **Name** parameter to specify the **BITS** service.</span></span> <span data-ttu-id="4e963-132">Parametern **Description** anger den uppdaterade texten för beskrivningen av tjänsterna.</span><span class="sxs-lookup"><span data-stu-id="4e963-132">The **Description** parameter specifies the updated text for the services' description.</span></span>

### <span data-ttu-id="4e963-133">Exempel 4: starta en tjänst</span><span class="sxs-lookup"><span data-stu-id="4e963-133">Example 4: Start a service</span></span>

<span data-ttu-id="4e963-134">I det här exemplet startas en tjänst.</span><span class="sxs-lookup"><span data-stu-id="4e963-134">In this example, a service is started.</span></span>

```powershell
Set-Service -Name WinRM -Status Running -PassThru
```

```Output
Status   Name               DisplayName
------   ----               -----------
Running  WinRM              Windows Remote Management (WS-Manag...
```

<span data-ttu-id="4e963-135">`Set-Service` använder parametern **Name** för att ange tjänsten, **WinRM**.</span><span class="sxs-lookup"><span data-stu-id="4e963-135">`Set-Service` uses the **Name** parameter to specify the service, **WinRM**.</span></span> <span data-ttu-id="4e963-136">**Status** parametern använder det värde som **körs** för att starta tjänsten.</span><span class="sxs-lookup"><span data-stu-id="4e963-136">The **Status** parameter uses the value **Running** to start the service.</span></span> <span data-ttu-id="4e963-137">**Passthru** -parametern matar ut ett **ServiceController** -objekt som visar resultatet.</span><span class="sxs-lookup"><span data-stu-id="4e963-137">The **PassThru** parameter outputs a **ServiceController** object that displays the results.</span></span>

### <span data-ttu-id="4e963-138">Exempel 5: inaktivera en tjänst</span><span class="sxs-lookup"><span data-stu-id="4e963-138">Example 5: Suspend a service</span></span>

<span data-ttu-id="4e963-139">I det här exemplet används pipelinen för att pausa tjänsten.</span><span class="sxs-lookup"><span data-stu-id="4e963-139">This example uses the pipeline to pause to service.</span></span>

```powershell
Get-Service -Name Schedule | Set-Service -Status Paused
```

<span data-ttu-id="4e963-140">`Get-Service` använder **Name** -parametern för att ange **schema** tjänsten och skickar objektet nedåt i pipelinen.</span><span class="sxs-lookup"><span data-stu-id="4e963-140">`Get-Service` uses the **Name** parameter to specify the **Schedule** service, and sends the object down the pipeline.</span></span> <span data-ttu-id="4e963-141">`Set-Service` använder **status** parametern för att ange att tjänsten ska **pausas**.</span><span class="sxs-lookup"><span data-stu-id="4e963-141">`Set-Service` uses the **Status** parameter to set the service to **Paused**.</span></span>

### <span data-ttu-id="4e963-142">Exempel 6: stoppa en tjänst</span><span class="sxs-lookup"><span data-stu-id="4e963-142">Example 6: Stop a service</span></span>

<span data-ttu-id="4e963-143">I det här exemplet används en variabel för att stoppa en tjänst.</span><span class="sxs-lookup"><span data-stu-id="4e963-143">This example uses a variable to stop a service.</span></span>

```powershell
$S = Get-Service -Name Schedule
Set-Service -InputObject $S -Status Stopped
```

<span data-ttu-id="4e963-144">`Get-Service` använder **Name** -parametern för att ange tjänsten, **schema**.</span><span class="sxs-lookup"><span data-stu-id="4e963-144">`Get-Service` uses the **Name** parameter to specify the service, **Schedule**.</span></span> <span data-ttu-id="4e963-145">Objektet lagras i variabeln `$S` .</span><span class="sxs-lookup"><span data-stu-id="4e963-145">The object is stored in the variable, `$S`.</span></span> <span data-ttu-id="4e963-146">`Set-Service` använder parametern **InputObject** och anger objektet som lagras `$S` .</span><span class="sxs-lookup"><span data-stu-id="4e963-146">`Set-Service` uses the **InputObject** parameter and specifies the object stored `$S`.</span></span> <span data-ttu-id="4e963-147">**Status** parametern anger att tjänsten har **stoppats**.</span><span class="sxs-lookup"><span data-stu-id="4e963-147">The **Status** parameter sets the service to **Stopped**.</span></span>

## <span data-ttu-id="4e963-148">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="4e963-148">PARAMETERS</span></span>

### <span data-ttu-id="4e963-149">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="4e963-149">-ComputerName</span></span>

<span data-ttu-id="4e963-150">Anger en eller flera datorer.</span><span class="sxs-lookup"><span data-stu-id="4e963-150">Specifies one or more computers.</span></span> <span data-ttu-id="4e963-151">För fjärrdatorer anger du NetBIOS-namn, en IP-adress eller ett fullständigt kvalificerat domän namn.</span><span class="sxs-lookup"><span data-stu-id="4e963-151">For remote computers, type the NetBIOS name, an IP address, or a fully qualified domain name.</span></span> <span data-ttu-id="4e963-152">Om parametern **computername** inte anges körs kommandot på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="4e963-152">If the **ComputerName** parameter isn't specified, the command runs on the local computer.</span></span>

<span data-ttu-id="4e963-153">Den här parametern är inte beroende av PowerShell-fjärrkommunikation.</span><span class="sxs-lookup"><span data-stu-id="4e963-153">This parameter doesn't rely on PowerShell remoting.</span></span> <span data-ttu-id="4e963-154">Du kan använda parametern **computername** även om datorn inte är konfigurerad för att köra fjärrkommandon.</span><span class="sxs-lookup"><span data-stu-id="4e963-154">You can use the **ComputerName** parameter even if your computer isn't configured to run remote commands.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: cn

Required: False
Position: Named
Default value: Local computer
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="4e963-155">-Confirm</span><span class="sxs-lookup"><span data-stu-id="4e963-155">-Confirm</span></span>

<span data-ttu-id="4e963-156">Du uppmanas att bekräfta innan du kör `Set-Service` .</span><span class="sxs-lookup"><span data-stu-id="4e963-156">Prompts you for confirmation before running `Set-Service`.</span></span>

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

### <span data-ttu-id="4e963-157">-Beskrivning</span><span class="sxs-lookup"><span data-stu-id="4e963-157">-Description</span></span>

<span data-ttu-id="4e963-158">Anger en ny Beskrivning av tjänsten.</span><span class="sxs-lookup"><span data-stu-id="4e963-158">Specifies a new description for the service.</span></span>

<span data-ttu-id="4e963-159">Tjänst beskrivningen visas i **dator hantering, tjänster**.</span><span class="sxs-lookup"><span data-stu-id="4e963-159">The service description appears in **Computer Management, Services**.</span></span> <span data-ttu-id="4e963-160">**Beskrivningen** är inte en egenskap för `Get-Service` **ServiceController** -objektet.</span><span class="sxs-lookup"><span data-stu-id="4e963-160">The **Description** isn't a property of the `Get-Service` **ServiceController** object.</span></span> <span data-ttu-id="4e963-161">Om du vill se tjänst beskrivningen använder du `Get-CimInstance` som returnerar ett **Win32_Service** -objekt som representerar tjänsten.</span><span class="sxs-lookup"><span data-stu-id="4e963-161">To see the service description, use `Get-CimInstance` that returns a **Win32_Service** object that represents the service.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="4e963-162">-DisplayName</span><span class="sxs-lookup"><span data-stu-id="4e963-162">-DisplayName</span></span>

<span data-ttu-id="4e963-163">Anger ett nytt visnings namn för tjänsten.</span><span class="sxs-lookup"><span data-stu-id="4e963-163">Specifies a new display name for the service.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: DN

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="4e963-164">– InputObject</span><span class="sxs-lookup"><span data-stu-id="4e963-164">-InputObject</span></span>

<span data-ttu-id="4e963-165">Anger ett **ServiceController** -objekt som representerar den tjänst som ska ändras.</span><span class="sxs-lookup"><span data-stu-id="4e963-165">Specifies a **ServiceController** object that represents the service to change.</span></span> <span data-ttu-id="4e963-166">Ange en variabel som innehåller objektet eller Skriv ett kommando eller uttryck som hämtar objektet, till exempel ett `Get-Service` kommando.</span><span class="sxs-lookup"><span data-stu-id="4e963-166">Enter a variable that contains the object, or type a command or expression that gets the object, such as a `Get-Service` command.</span></span> <span data-ttu-id="4e963-167">Du kan använda pipelinen för att skicka ett tjänst objekt till `Set-Service` .</span><span class="sxs-lookup"><span data-stu-id="4e963-167">You can use the pipeline to send a service object to `Set-Service`.</span></span>

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

### <span data-ttu-id="4e963-168">-Name</span><span class="sxs-lookup"><span data-stu-id="4e963-168">-Name</span></span>

<span data-ttu-id="4e963-169">Anger tjänst namnet på den tjänst som ska ändras.</span><span class="sxs-lookup"><span data-stu-id="4e963-169">Specifies the service name of the service to be changed.</span></span> <span data-ttu-id="4e963-170">Jokertecken är inte tillåtna.</span><span class="sxs-lookup"><span data-stu-id="4e963-170">Wildcard characters aren't permitted.</span></span> <span data-ttu-id="4e963-171">Du kan använda pipelinen för att skicka ett tjänst namn till `Set-Service` .</span><span class="sxs-lookup"><span data-stu-id="4e963-171">You can use the pipeline to send a service name to `Set-Service`.</span></span>

```yaml
Type: System.String
Parameter Sets: Name
Aliases: ServiceName, SN

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="4e963-172">– PassThru</span><span class="sxs-lookup"><span data-stu-id="4e963-172">-PassThru</span></span>

<span data-ttu-id="4e963-173">Returnerar ett **ServiceController** -objekt som representerar de tjänster som har ändrats.</span><span class="sxs-lookup"><span data-stu-id="4e963-173">Returns a **ServiceController** object that represents the services that were changed.</span></span> <span data-ttu-id="4e963-174">Som standard `Set-Service` genererar inga utdata.</span><span class="sxs-lookup"><span data-stu-id="4e963-174">By default, `Set-Service` doesn't generate any output.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="4e963-175">– Startuptype tjänst</span><span class="sxs-lookup"><span data-stu-id="4e963-175">-StartupType</span></span>

<span data-ttu-id="4e963-176">Anger tjänstens starttyp.</span><span class="sxs-lookup"><span data-stu-id="4e963-176">Sets the startup type of the service.</span></span> <span data-ttu-id="4e963-177">De acceptabla värdena för den här parametern är:</span><span class="sxs-lookup"><span data-stu-id="4e963-177">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="4e963-178">**Automatiskt** – tjänsten startas eller startades av operativ systemet vid system start.</span><span class="sxs-lookup"><span data-stu-id="4e963-178">**Automatic** - The service is started or was started by the operating system, at system start-up.</span></span>
  <span data-ttu-id="4e963-179">Om en automatiskt startad tjänst är beroende av en manuellt startad tjänst startas automatiskt den manuellt startade tjänsten automatiskt vid system start.</span><span class="sxs-lookup"><span data-stu-id="4e963-179">If an automatically started service depends on a manually started service, the manually started service is also started automatically at system startup.</span></span>
- <span data-ttu-id="4e963-180">**Disabled** – tjänsten är inaktive rad och kan inte startas av en användare eller ett program.</span><span class="sxs-lookup"><span data-stu-id="4e963-180">**Disabled** - The service is disabled and cannot be started by a user or application.</span></span>
- <span data-ttu-id="4e963-181">**Manuell** – tjänsten startas endast manuellt, av en användare, med hjälp av tjänst hanteraren eller av ett program.</span><span class="sxs-lookup"><span data-stu-id="4e963-181">**Manual** - The service is started only manually, by a user, using the Service Control Manager, or by an application.</span></span>
- <span data-ttu-id="4e963-182">**Boot** -anger att tjänsten är en enhets driv rutin som startas av system inläsaren.</span><span class="sxs-lookup"><span data-stu-id="4e963-182">**Boot** - Indicates that the service is a device driver started by the system loader.</span></span> <span data-ttu-id="4e963-183">Det här värdet är endast giltigt för enhets driv rutiner.</span><span class="sxs-lookup"><span data-stu-id="4e963-183">This value is valid only for device drivers.</span></span>
- <span data-ttu-id="4e963-184">**System** -anger att tjänsten är en enhets driv rutin som startas av funktionen ' IOInitSystem () '.</span><span class="sxs-lookup"><span data-stu-id="4e963-184">**System** - Indicates that the service is a device driver started by the 'IOInitSystem()' function.</span></span> <span data-ttu-id="4e963-185">Det här värdet är endast giltigt för enhets driv rutiner.</span><span class="sxs-lookup"><span data-stu-id="4e963-185">This value is valid only for device drivers.</span></span>

 <span data-ttu-id="4e963-186">Standardvärdet är **Automatisk**.</span><span class="sxs-lookup"><span data-stu-id="4e963-186">The default value is **Automatic**.</span></span>

```yaml
Type: System.ServiceProcess.ServiceStartMode
Parameter Sets: (All)
Aliases: StartMode, SM, ST
Accepted values: Boot, System, Automatic, Manual, Disabled

Required: False
Position: Named
Default value: Automatic
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="4e963-187">-Status</span><span class="sxs-lookup"><span data-stu-id="4e963-187">-Status</span></span>

<span data-ttu-id="4e963-188">Anger tjänstens status.</span><span class="sxs-lookup"><span data-stu-id="4e963-188">Specifies the status for the service.</span></span>

<span data-ttu-id="4e963-189">De acceptabla värdena för den här parametern är följande:</span><span class="sxs-lookup"><span data-stu-id="4e963-189">The acceptable values for this parameter are as follows:</span></span>

- <span data-ttu-id="4e963-190">**Pausat**.</span><span class="sxs-lookup"><span data-stu-id="4e963-190">**Paused**.</span></span> <span data-ttu-id="4e963-191">Pausar tjänsten.</span><span class="sxs-lookup"><span data-stu-id="4e963-191">Suspends the service.</span></span>
- <span data-ttu-id="4e963-192">**Körs**.</span><span class="sxs-lookup"><span data-stu-id="4e963-192">**Running**.</span></span> <span data-ttu-id="4e963-193">Startar tjänsten.</span><span class="sxs-lookup"><span data-stu-id="4e963-193">Starts the service.</span></span>
- <span data-ttu-id="4e963-194">**Stoppades**.</span><span class="sxs-lookup"><span data-stu-id="4e963-194">**Stopped**.</span></span> <span data-ttu-id="4e963-195">Stoppar tjänsten.</span><span class="sxs-lookup"><span data-stu-id="4e963-195">Stops the service.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values: Paused, Running, Stopped

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="4e963-196">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="4e963-196">-WhatIf</span></span>

<span data-ttu-id="4e963-197">Visar vad som händer om `Set-Service` körs.</span><span class="sxs-lookup"><span data-stu-id="4e963-197">Shows what would happen if `Set-Service` runs.</span></span> <span data-ttu-id="4e963-198">Cmdleten körs inte.</span><span class="sxs-lookup"><span data-stu-id="4e963-198">The cmdlet isn't run.</span></span>

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

### <span data-ttu-id="4e963-199">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="4e963-199">CommonParameters</span></span>

<span data-ttu-id="4e963-200">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="4e963-200">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="4e963-201">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="4e963-201">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="4e963-202">INDATA</span><span class="sxs-lookup"><span data-stu-id="4e963-202">INPUTS</span></span>

### <span data-ttu-id="4e963-203">System. ServiceProcess. ServiceController, system. String</span><span class="sxs-lookup"><span data-stu-id="4e963-203">System.ServiceProcess.ServiceController, System.String</span></span>

<span data-ttu-id="4e963-204">Du kan använda pipelinen för att skicka ett tjänst objekt eller en sträng som innehåller ett tjänst namn till `Set-Service` .</span><span class="sxs-lookup"><span data-stu-id="4e963-204">You can use the pipeline to send a service object or a string that contains a service name to `Set-Service`.</span></span>

## <span data-ttu-id="4e963-205">UTDATA</span><span class="sxs-lookup"><span data-stu-id="4e963-205">OUTPUTS</span></span>

### <span data-ttu-id="4e963-206">System. ServiceProcess. ServiceController</span><span class="sxs-lookup"><span data-stu-id="4e963-206">System.ServiceProcess.ServiceController</span></span>

<span data-ttu-id="4e963-207">Som standard `Set-Service` returnerar inte några objekt.</span><span class="sxs-lookup"><span data-stu-id="4e963-207">By default, `Set-Service` doesn't return any objects.</span></span> <span data-ttu-id="4e963-208">Använd parametern **Passthru** för att mata ut ett **ServiceController** -objekt.</span><span class="sxs-lookup"><span data-stu-id="4e963-208">Use the **PassThru** parameter to output a **ServiceController** object.</span></span>

## <span data-ttu-id="4e963-209">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="4e963-209">NOTES</span></span>

<span data-ttu-id="4e963-210">`Set-Service` kräver förhöjd behörighet.</span><span class="sxs-lookup"><span data-stu-id="4e963-210">`Set-Service` requires elevated permissions.</span></span> <span data-ttu-id="4e963-211">Använd alternativet **Kör som administratör** .</span><span class="sxs-lookup"><span data-stu-id="4e963-211">Use the **Run as administrator** option.</span></span>

<span data-ttu-id="4e963-212">`Set-Service` Det går bara att kontrol lera tjänster när den aktuella användaren har behörighet att hantera tjänster.</span><span class="sxs-lookup"><span data-stu-id="4e963-212">`Set-Service` can only control services when the current user has permissions to manage services.</span></span> <span data-ttu-id="4e963-213">Om ett kommando inte fungerar som det ska kanske du inte har de behörigheter som krävs.</span><span class="sxs-lookup"><span data-stu-id="4e963-213">If a command doesn't work correctly, you might not have the required permissions.</span></span>

<span data-ttu-id="4e963-214">Använd om du vill hitta tjänstens namn eller visnings namn för tjänsten `Get-Service` .</span><span class="sxs-lookup"><span data-stu-id="4e963-214">To find a service's service name or display name, use `Get-Service`.</span></span> <span data-ttu-id="4e963-215">Tjänst namnen finns i kolumnen **namn** och visnings namnen är i kolumnen **DisplayName** .</span><span class="sxs-lookup"><span data-stu-id="4e963-215">The service names are in the **Name** column and the display names are in the **DisplayName** column.</span></span>

## <span data-ttu-id="4e963-216">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="4e963-216">RELATED LINKS</span></span>

[<span data-ttu-id="4e963-217">Get-Service</span><span class="sxs-lookup"><span data-stu-id="4e963-217">Get-Service</span></span>](Get-Service.md)

[<span data-ttu-id="4e963-218">New-Service</span><span class="sxs-lookup"><span data-stu-id="4e963-218">New-Service</span></span>](New-Service.md)

[<span data-ttu-id="4e963-219">Restart-Service</span><span class="sxs-lookup"><span data-stu-id="4e963-219">Restart-Service</span></span>](Restart-Service.md)

[<span data-ttu-id="4e963-220">Resume-Service</span><span class="sxs-lookup"><span data-stu-id="4e963-220">Resume-Service</span></span>](Resume-Service.md)

[<span data-ttu-id="4e963-221">Start-Service</span><span class="sxs-lookup"><span data-stu-id="4e963-221">Start-Service</span></span>](Start-Service.md)

[<span data-ttu-id="4e963-222">Stop-Service</span><span class="sxs-lookup"><span data-stu-id="4e963-222">Stop-Service</span></span>](Stop-Service.md)

[<span data-ttu-id="4e963-223">Suspend-Service</span><span class="sxs-lookup"><span data-stu-id="4e963-223">Suspend-Service</span></span>](Suspend-Service.md)
