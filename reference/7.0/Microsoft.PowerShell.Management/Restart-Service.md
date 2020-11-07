---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/restart-service?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Restart-Service
ms.openlocfilehash: 06db89e107e7589dcdd4439fff54e04676adcc1c
ms.sourcegitcommit: 177ae45034b58ead716853096b2e72e4864e6df6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/07/2020
ms.locfileid: "94342900"
---
# <span data-ttu-id="df09f-103">Restart-Service</span><span class="sxs-lookup"><span data-stu-id="df09f-103">Restart-Service</span></span>

## <span data-ttu-id="df09f-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="df09f-104">SYNOPSIS</span></span>
<span data-ttu-id="df09f-105">Stoppar och startar sedan en eller flera tjänster.</span><span class="sxs-lookup"><span data-stu-id="df09f-105">Stops and then starts one or more services.</span></span>

## <span data-ttu-id="df09f-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="df09f-106">SYNTAX</span></span>

### <span data-ttu-id="df09f-107">InputObject (standard)</span><span class="sxs-lookup"><span data-stu-id="df09f-107">InputObject (Default)</span></span>

```
Restart-Service [-Force] [-InputObject] <ServiceController[]> [-PassThru] [-Include <String[]>]
 [-Exclude <String[]>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="df09f-108">Standard</span><span class="sxs-lookup"><span data-stu-id="df09f-108">Default</span></span>

```
Restart-Service [-Force] [-Name] <String[]> [-PassThru] [-Include <String[]>] [-Exclude <String[]>] [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="df09f-109">DisplayName</span><span class="sxs-lookup"><span data-stu-id="df09f-109">DisplayName</span></span>

```
Restart-Service [-Force] [-PassThru] -DisplayName <String[]> [-Include <String[]>] [-Exclude <String[]>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="df09f-110">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="df09f-110">DESCRIPTION</span></span>

<span data-ttu-id="df09f-111">`Restart-Service`Cmdleten skickar ett stopp meddelande och ett Start meddelande till Windows-tjänstens kontrollant för en angiven tjänst.</span><span class="sxs-lookup"><span data-stu-id="df09f-111">The `Restart-Service` cmdlet sends a stop message and then a start message to the Windows Service Controller for a specified service.</span></span> <span data-ttu-id="df09f-112">Om en tjänst redan har stoppats startas den utan att du får ett fel meddelande.</span><span class="sxs-lookup"><span data-stu-id="df09f-112">If a service was already stopped, it is started without notifying you of an error.</span></span> <span data-ttu-id="df09f-113">Du kan ange tjänsterna efter tjänst namn eller visnings namn, eller så kan du använda parametern **InputObject** för att skicka ett objekt som representerar varje tjänst som du vill starta om.</span><span class="sxs-lookup"><span data-stu-id="df09f-113">You can specify the services by their service names or display names, or you can use the **InputObject** parameter to pass an object that represents each service that you want to restart.</span></span>

## <span data-ttu-id="df09f-114">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="df09f-114">EXAMPLES</span></span>

### <span data-ttu-id="df09f-115">Exempel 1: starta om en tjänst på den lokala datorn</span><span class="sxs-lookup"><span data-stu-id="df09f-115">Example 1: Restart a service on the local computer</span></span>

```powershell
PS C:\> Restart-Service -Name winmgmt
```

<span data-ttu-id="df09f-116">Det här kommandot startar om Windows Management Instrumentation tjänsten (WinMgmt) på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="df09f-116">This command restarts the Windows Management Instrumentation service (WinMgmt) on the local computer.</span></span>

### <span data-ttu-id="df09f-117">Exempel 2: undanta en tjänst</span><span class="sxs-lookup"><span data-stu-id="df09f-117">Example 2: Exclude a service</span></span>

```powershell
PS C:\> Restart-Service -DisplayName "net*" -Exclude "net logon"
```

<span data-ttu-id="df09f-118">Det här kommandot startar om tjänsterna som har ett visnings namn som börjar med net, förutom tjänsten Net Logon.</span><span class="sxs-lookup"><span data-stu-id="df09f-118">This command restarts the services that have a display name that starts with Net, except for the Net Logon service.</span></span>

### <span data-ttu-id="df09f-119">Exempel 3: starta alla stoppade nätverks tjänster</span><span class="sxs-lookup"><span data-stu-id="df09f-119">Example 3: Start all stopped network services</span></span>

```powershell
PS C:\> Get-Service -Name "net*" | Where-Object {$_.Status -eq "Stopped"} | Restart-Service
```

<span data-ttu-id="df09f-120">Detta kommando startar alla stoppade nätverks tjänster på datorn.</span><span class="sxs-lookup"><span data-stu-id="df09f-120">This command starts all of the stopped network services on the computer.</span></span>

<span data-ttu-id="df09f-121">Det här kommandot använder `Get-Service` cmdleten för att hämta objekt som representerar de tjänster vars tjänst namn börjar med net.</span><span class="sxs-lookup"><span data-stu-id="df09f-121">This command uses the `Get-Service` cmdlet to get objects that represent the services whose service name starts with net.</span></span> <span data-ttu-id="df09f-122">Pipeline-operatorn ( `|` ) skickar objektet tjänster till `Where-Object` cmdleten, som endast väljer de tjänster som har statusen stoppad.</span><span class="sxs-lookup"><span data-stu-id="df09f-122">The pipeline operator (`|`) sends the services object to the `Where-Object` cmdlet, which selects only the services that have a status of stopped.</span></span> <span data-ttu-id="df09f-123">En annan pipeline-operator skickar de valda tjänsterna till `Restart-Service` .</span><span class="sxs-lookup"><span data-stu-id="df09f-123">Another pipeline operator sends the selected services to `Restart-Service`.</span></span>

<span data-ttu-id="df09f-124">I praktiken använder du parametern **whatIf** för att fastställa kommandots effekter innan du kör det.</span><span class="sxs-lookup"><span data-stu-id="df09f-124">In practice, you would use the **WhatIf** parameter to determine the effect of the command before you run it.</span></span>

## <span data-ttu-id="df09f-125">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="df09f-125">PARAMETERS</span></span>

### <span data-ttu-id="df09f-126">-DisplayName</span><span class="sxs-lookup"><span data-stu-id="df09f-126">-DisplayName</span></span>

<span data-ttu-id="df09f-127">Anger visnings namnen för de tjänster som ska startas om.</span><span class="sxs-lookup"><span data-stu-id="df09f-127">Specifies the display names of services to restarted.</span></span> <span data-ttu-id="df09f-128">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="df09f-128">Wildcard characters are permitted.</span></span>

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

### <span data-ttu-id="df09f-129">-Undanta</span><span class="sxs-lookup"><span data-stu-id="df09f-129">-Exclude</span></span>

<span data-ttu-id="df09f-130">Anger tjänster som denna cmdlet utelämnar.</span><span class="sxs-lookup"><span data-stu-id="df09f-130">Specifies services that this cmdlet omits.</span></span> <span data-ttu-id="df09f-131">Värdet för den här parametern kvalificerar parametern **Name** .</span><span class="sxs-lookup"><span data-stu-id="df09f-131">The value of this parameter qualifies the **Name** parameter.</span></span> <span data-ttu-id="df09f-132">Ange ett namn element eller ett mönster, till exempel s \*.</span><span class="sxs-lookup"><span data-stu-id="df09f-132">Enter a name element or pattern, such as s\*.</span></span> <span data-ttu-id="df09f-133">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="df09f-133">Wildcard characters are permitted.</span></span>

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

### <span data-ttu-id="df09f-134">-Force</span><span class="sxs-lookup"><span data-stu-id="df09f-134">-Force</span></span>

<span data-ttu-id="df09f-135">Tvingar kommandot att köras utan att fråga användaren om bekräftelse.</span><span class="sxs-lookup"><span data-stu-id="df09f-135">Forces the command to run without asking for user confirmation.</span></span>

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

### <span data-ttu-id="df09f-136">-Inkludera</span><span class="sxs-lookup"><span data-stu-id="df09f-136">-Include</span></span>

<span data-ttu-id="df09f-137">Anger tjänster som den här cmdleten startar om.</span><span class="sxs-lookup"><span data-stu-id="df09f-137">Specifies services that this cmdlet restarts.</span></span> <span data-ttu-id="df09f-138">Värdet för den här parametern kvalificerar parametern **Name** .</span><span class="sxs-lookup"><span data-stu-id="df09f-138">The value of this parameter qualifies the **Name** parameter.</span></span> <span data-ttu-id="df09f-139">Ange ett namn element eller ett mönster, till exempel s \*.</span><span class="sxs-lookup"><span data-stu-id="df09f-139">Enter a name element or pattern, such as s\*.</span></span> <span data-ttu-id="df09f-140">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="df09f-140">Wildcard characters are permitted.</span></span>

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

### <span data-ttu-id="df09f-141">– InputObject</span><span class="sxs-lookup"><span data-stu-id="df09f-141">-InputObject</span></span>

<span data-ttu-id="df09f-142">Anger **ServiceController** -objekt som representerar de tjänster som ska startas om.</span><span class="sxs-lookup"><span data-stu-id="df09f-142">Specifies **ServiceController** objects that represent the services to restart.</span></span> <span data-ttu-id="df09f-143">Ange en variabel som innehåller objekten eller Skriv ett kommando eller uttryck som hämtar objekten.</span><span class="sxs-lookup"><span data-stu-id="df09f-143">Enter a variable that contains the objects, or type a command or expression that gets the objects.</span></span>

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

### <span data-ttu-id="df09f-144">-Name</span><span class="sxs-lookup"><span data-stu-id="df09f-144">-Name</span></span>

<span data-ttu-id="df09f-145">Anger tjänst namnen för de tjänster som ska startas om.</span><span class="sxs-lookup"><span data-stu-id="df09f-145">Specifies the service names of the services to restart.</span></span>

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

### <span data-ttu-id="df09f-146">– PassThru</span><span class="sxs-lookup"><span data-stu-id="df09f-146">-PassThru</span></span>

<span data-ttu-id="df09f-147">Returnerar ett objekt som representerar tjänsten.</span><span class="sxs-lookup"><span data-stu-id="df09f-147">Returns an object that represents the service.</span></span> <span data-ttu-id="df09f-148">Som standard genererar denna cmdlet inga utdata.</span><span class="sxs-lookup"><span data-stu-id="df09f-148">By default, this cmdlet does not generate any output.</span></span>

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

### <span data-ttu-id="df09f-149">-Confirm</span><span class="sxs-lookup"><span data-stu-id="df09f-149">-Confirm</span></span>

<span data-ttu-id="df09f-150">Uppmanar dig att bekräfta innan du kör cmdleten.</span><span class="sxs-lookup"><span data-stu-id="df09f-150">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="df09f-151">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="df09f-151">-WhatIf</span></span>

<span data-ttu-id="df09f-152">Visar vad som skulle hända om cmdleten kördes.</span><span class="sxs-lookup"><span data-stu-id="df09f-152">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="df09f-153">Cmdleten körs inte.</span><span class="sxs-lookup"><span data-stu-id="df09f-153">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="df09f-154">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="df09f-154">CommonParameters</span></span>

<span data-ttu-id="df09f-155">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="df09f-155">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="df09f-156">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="df09f-156">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="df09f-157">INDATA</span><span class="sxs-lookup"><span data-stu-id="df09f-157">INPUTS</span></span>

### <span data-ttu-id="df09f-158">System. ServiceProcess. ServiceController, system. String</span><span class="sxs-lookup"><span data-stu-id="df09f-158">System.ServiceProcess.ServiceController, System.String</span></span>

<span data-ttu-id="df09f-159">Du kan skicka vidare ett tjänst objekt eller en sträng som innehåller ett tjänst namn till denna cmdlet.</span><span class="sxs-lookup"><span data-stu-id="df09f-159">You can pipe a service object or a string that contains a service name to this cmdlet.</span></span>

## <span data-ttu-id="df09f-160">UTDATA</span><span class="sxs-lookup"><span data-stu-id="df09f-160">OUTPUTS</span></span>

### <span data-ttu-id="df09f-161">Ingen, system. ServiceProcess. ServiceController</span><span class="sxs-lookup"><span data-stu-id="df09f-161">None, System.ServiceProcess.ServiceController</span></span>

<span data-ttu-id="df09f-162">Denna cmdlet genererar ett **system. ServiceProcess. ServiceController** -objekt som representerar den omstartade tjänsten om du anger parametern **Passthru** .</span><span class="sxs-lookup"><span data-stu-id="df09f-162">This cmdlet generates a **System.ServiceProcess.ServiceController** object that represents the restarted service, if you specify the **PassThru** parameter.</span></span> <span data-ttu-id="df09f-163">Annars genererar denna cmdlet inga utdata.</span><span class="sxs-lookup"><span data-stu-id="df09f-163">Otherwise, this cmdlet does not generate any output.</span></span>

## <span data-ttu-id="df09f-164">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="df09f-164">NOTES</span></span>

<span data-ttu-id="df09f-165">Den här cmdleten är endast tillgänglig på Windows-plattformar.</span><span class="sxs-lookup"><span data-stu-id="df09f-165">This cmdlet is only available on Windows platforms.</span></span>

- <span data-ttu-id="df09f-166">`Restart-Service` kan bara styra tjänster när den aktuella användaren har behörighet att göra detta.</span><span class="sxs-lookup"><span data-stu-id="df09f-166">`Restart-Service` can control services only when the current user has permission to do this.</span></span> <span data-ttu-id="df09f-167">Om ett kommando inte fungerar som det ska kanske du inte har de behörigheter som krävs.</span><span class="sxs-lookup"><span data-stu-id="df09f-167">If a command does not work correctly, you might not have the required permissions.</span></span>
- <span data-ttu-id="df09f-168">Om du vill hitta tjänst namn och visnings namn för tjänsterna i systemet skriver du `Get-Service` ".</span><span class="sxs-lookup"><span data-stu-id="df09f-168">To find the service names and display names of the services on your system, type `Get-Service`".</span></span>
  <span data-ttu-id="df09f-169">Tjänst namnen visas i kolumnen **namn** och visnings namnen visas i kolumnen **DisplayName** .</span><span class="sxs-lookup"><span data-stu-id="df09f-169">The service names appear in the **Name** column, and the display names appear in the **DisplayName** column.</span></span>

## <span data-ttu-id="df09f-170">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="df09f-170">RELATED LINKS</span></span>

[<span data-ttu-id="df09f-171">Get-Service</span><span class="sxs-lookup"><span data-stu-id="df09f-171">Get-Service</span></span>](Get-Service.md)

[<span data-ttu-id="df09f-172">New-Service</span><span class="sxs-lookup"><span data-stu-id="df09f-172">New-Service</span></span>](New-Service.md)

[<span data-ttu-id="df09f-173">Resume-Service</span><span class="sxs-lookup"><span data-stu-id="df09f-173">Resume-Service</span></span>](Resume-Service.md)

[<span data-ttu-id="df09f-174">Set-Service</span><span class="sxs-lookup"><span data-stu-id="df09f-174">Set-Service</span></span>](Set-Service.md)

[<span data-ttu-id="df09f-175">Start-Service</span><span class="sxs-lookup"><span data-stu-id="df09f-175">Start-Service</span></span>](Start-Service.md)

[<span data-ttu-id="df09f-176">Stop-Service</span><span class="sxs-lookup"><span data-stu-id="df09f-176">Stop-Service</span></span>](Stop-Service.md)

[<span data-ttu-id="df09f-177">Suspend-Service</span><span class="sxs-lookup"><span data-stu-id="df09f-177">Suspend-Service</span></span>](Suspend-Service.md)

[<span data-ttu-id="df09f-178">Remove-service</span><span class="sxs-lookup"><span data-stu-id="df09f-178">Remove-Service</span></span>](Remove-Service.md)
