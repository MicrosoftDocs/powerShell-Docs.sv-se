---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/suspend-service?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Suspend-Service
ms.openlocfilehash: 6e9fd5dd7a5736ef95976cb5195dd1d210d81651
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93263769"
---
# <span data-ttu-id="b586f-103">Suspend-Service</span><span class="sxs-lookup"><span data-stu-id="b586f-103">Suspend-Service</span></span>

## <span data-ttu-id="b586f-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="b586f-104">SYNOPSIS</span></span>
<span data-ttu-id="b586f-105">Pausar (pausar) en eller flera tjänster som körs.</span><span class="sxs-lookup"><span data-stu-id="b586f-105">Suspends (pauses) one or more running services.</span></span>

## <span data-ttu-id="b586f-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="b586f-106">SYNTAX</span></span>

### <span data-ttu-id="b586f-107">InputObject (standard)</span><span class="sxs-lookup"><span data-stu-id="b586f-107">InputObject (Default)</span></span>

```
Suspend-Service [-InputObject] <ServiceController[]> [-PassThru] [-Include <String[]>] [-Exclude <String[]>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="b586f-108">Default</span><span class="sxs-lookup"><span data-stu-id="b586f-108">Default</span></span>

```
Suspend-Service [-Name] <String[]> [-PassThru] [-Include <String[]>] [-Exclude <String[]>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### <span data-ttu-id="b586f-109">DisplayName</span><span class="sxs-lookup"><span data-stu-id="b586f-109">DisplayName</span></span>

```
Suspend-Service [-PassThru] -DisplayName <String[]> [-Include <String[]>] [-Exclude <String[]>] [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="b586f-110">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="b586f-110">DESCRIPTION</span></span>

<span data-ttu-id="b586f-111">Cmdlet **: en Suspend-service** skickar ett uppehålls meddelande till Windows-Domänkontrollanttjänsten för varje angiven tjänst.</span><span class="sxs-lookup"><span data-stu-id="b586f-111">The **Suspend-Service** cmdlet sends a suspend message to the Windows Service Controller for each of the specified services.</span></span>
<span data-ttu-id="b586f-112">Tjänsten körs fortfarande när den har pausats, men dess åtgärd stoppas tills den återupptas, till exempel av usingthe Resume-Service cmdlet.</span><span class="sxs-lookup"><span data-stu-id="b586f-112">While suspended, the service is still running, but its action is stopped until resumed, such as by usingthe Resume-Service cmdlet.</span></span>
<span data-ttu-id="b586f-113">Du kan ange tjänsterna efter tjänst namn eller visnings namn, eller så kan du använda parametern *InputObject* för att skicka ett tjänst objekt som representerar de tjänster som du vill pausa.</span><span class="sxs-lookup"><span data-stu-id="b586f-113">You can specify the services by their service names or display names, or you can use the *InputObject* parameter to pass a service object that represents the services that you want to suspend.</span></span>

## <span data-ttu-id="b586f-114">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="b586f-114">EXAMPLES</span></span>

### <span data-ttu-id="b586f-115">Exempel 1: pausa en tjänst</span><span class="sxs-lookup"><span data-stu-id="b586f-115">Example 1: Suspend a service</span></span>

```
PS C:\> Suspend-Service -DisplayName "Telnet"
```

<span data-ttu-id="b586f-116">Med det här kommandot pausas tjänsten Telnet service (Tlntsvr) på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="b586f-116">This command suspends the Telnet service (Tlntsvr) service on the local computer.</span></span>

### <span data-ttu-id="b586f-117">Exempel 2: Visa vad som händer om du inaktiverar tjänster</span><span class="sxs-lookup"><span data-stu-id="b586f-117">Example 2: Display what would happen if you suspend services</span></span>

```
PS C:\> Suspend-Service -Name lanman* -WhatIf
```

<span data-ttu-id="b586f-118">Det här kommandot anger vad som skulle hända om du har avbrutit tjänsterna som har ett tjänst namn som börjar med LANMAN.</span><span class="sxs-lookup"><span data-stu-id="b586f-118">This command tells what would happen if you suspended the services that have a service name that starts with lanman.</span></span>
<span data-ttu-id="b586f-119">Om du vill inaktivera tjänsterna kör du kommandot igen utan parametern *whatIf* .</span><span class="sxs-lookup"><span data-stu-id="b586f-119">To suspend the services, rerun the command without the *WhatIf* parameter.</span></span>

### <span data-ttu-id="b586f-120">Exempel 3: Hämta och pausa en tjänst</span><span class="sxs-lookup"><span data-stu-id="b586f-120">Example 3: Get and suspend a service</span></span>

```
PS C:\> Get-Service schedule | Suspend-Service
```

<span data-ttu-id="b586f-121">Det här kommandot använder cmdleten **Get-service** för att hämta ett objekt som representerar tjänsten Schemaläggaren (Schedule) på datorn.</span><span class="sxs-lookup"><span data-stu-id="b586f-121">This command uses the **Get-Service** cmdlet to get an object that represents the Task Scheduler (Schedule) service on the computer.</span></span>
<span data-ttu-id="b586f-122">Pipeline-operatorn (|) skickar resultatet till **suspend-tjänsten** , vilket gör att tjänsten pausas.</span><span class="sxs-lookup"><span data-stu-id="b586f-122">The pipeline operator (|) passes the result to **Suspend-Service** , which suspends the service.</span></span>

### <span data-ttu-id="b586f-123">Exempel 4: inaktivera alla tjänster som kan pausas</span><span class="sxs-lookup"><span data-stu-id="b586f-123">Example 4: Suspend all services that can be suspended</span></span>

```
PS C:\> Get-Service | Where-Object {$_.CanPauseAndContinue -eq "True"} | Suspend-Service -Confirm
```

<span data-ttu-id="b586f-124">Det här kommandot pausar alla tjänster på datorn som kan pausas.</span><span class="sxs-lookup"><span data-stu-id="b586f-124">This command suspends all of the services on the computer that can be suspended.</span></span>
<span data-ttu-id="b586f-125">Den använder **Get-service** för att hämta objekt som representerar tjänsterna på datorn.</span><span class="sxs-lookup"><span data-stu-id="b586f-125">It uses **Get-Service** to get objects that represent the services on the computer.</span></span>
<span data-ttu-id="b586f-126">Pipeline-operatorn skickar resultatet till Where-Object-cmdlet, som endast väljer de tjänster som har värdet $True för egenskapen **CanPauseAndContinue** .</span><span class="sxs-lookup"><span data-stu-id="b586f-126">The pipeline operator passes the results to the Where-Object cmdlet, which selects only the services that have a value of $True for the **CanPauseAndContinue** property.</span></span>
<span data-ttu-id="b586f-127">En annan pipeline-operator skickar resultatet till **suspend-tjänsten**.</span><span class="sxs-lookup"><span data-stu-id="b586f-127">Another pipeline operator passes the results to **Suspend-Service**.</span></span>
<span data-ttu-id="b586f-128">Parametern *Confirm* meddelar dig om bekräftelse innan du pausar varje tjänst.</span><span class="sxs-lookup"><span data-stu-id="b586f-128">The *Confirm* parameter prompts you for confirmation before suspending each of the services.</span></span>

## <span data-ttu-id="b586f-129">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="b586f-129">PARAMETERS</span></span>

### <span data-ttu-id="b586f-130">-DisplayName</span><span class="sxs-lookup"><span data-stu-id="b586f-130">-DisplayName</span></span>

<span data-ttu-id="b586f-131">Anger visnings namnen för de tjänster som ska pausas.</span><span class="sxs-lookup"><span data-stu-id="b586f-131">Specifies the display names of the services to be suspended.</span></span>
<span data-ttu-id="b586f-132">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="b586f-132">Wildcard characters are permitted.</span></span>

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

### <span data-ttu-id="b586f-133">-Undanta</span><span class="sxs-lookup"><span data-stu-id="b586f-133">-Exclude</span></span>

<span data-ttu-id="b586f-134">Anger tjänster som ska uteslutas från de angivna tjänsterna.</span><span class="sxs-lookup"><span data-stu-id="b586f-134">Specifies services to omit from the specified services.</span></span>
<span data-ttu-id="b586f-135">Värdet för den här parametern kvalificerar parametern *Name* .</span><span class="sxs-lookup"><span data-stu-id="b586f-135">The value of this parameter qualifies the *Name* parameter.</span></span>
<span data-ttu-id="b586f-136">Ange ett namn element eller ett mönster, till exempel "s \*".</span><span class="sxs-lookup"><span data-stu-id="b586f-136">Enter a name element or pattern, such as "s\*".</span></span>
<span data-ttu-id="b586f-137">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="b586f-137">Wildcard characters are permitted.</span></span>

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

### <span data-ttu-id="b586f-138">-Inkludera</span><span class="sxs-lookup"><span data-stu-id="b586f-138">-Include</span></span>

<span data-ttu-id="b586f-139">Anger vilka tjänster som ska pausas.</span><span class="sxs-lookup"><span data-stu-id="b586f-139">Specifies services to suspend.</span></span>
<span data-ttu-id="b586f-140">Värdet för den här parametern kvalificerar parametern *Name* .</span><span class="sxs-lookup"><span data-stu-id="b586f-140">The value of this parameter qualifies the *Name* parameter.</span></span>
<span data-ttu-id="b586f-141">Ange ett namn element eller ett mönster, till exempel "s \*".</span><span class="sxs-lookup"><span data-stu-id="b586f-141">Enter a name element or pattern, such as "s\*".</span></span>
<span data-ttu-id="b586f-142">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="b586f-142">Wildcard characters are permitted.</span></span>

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

### <span data-ttu-id="b586f-143">– InputObject</span><span class="sxs-lookup"><span data-stu-id="b586f-143">-InputObject</span></span>

<span data-ttu-id="b586f-144">Anger **ServiceController** -objekt som representerar de tjänster som ska pausas.</span><span class="sxs-lookup"><span data-stu-id="b586f-144">Specifies **ServiceController** objects that represent the services to suspend.</span></span>
<span data-ttu-id="b586f-145">Ange en variabel som innehåller objekten eller Skriv ett kommando eller uttryck som hämtar objekten.</span><span class="sxs-lookup"><span data-stu-id="b586f-145">Enter a variable that contains the objects, or type a command or expression that gets the objects.</span></span>

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

### <span data-ttu-id="b586f-146">-Name</span><span class="sxs-lookup"><span data-stu-id="b586f-146">-Name</span></span>

<span data-ttu-id="b586f-147">Anger tjänst namnen för de tjänster som ska pausas.</span><span class="sxs-lookup"><span data-stu-id="b586f-147">Specifies the service names of the services to suspend.</span></span>
<span data-ttu-id="b586f-148">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="b586f-148">Wildcard characters are permitted.</span></span>

<span data-ttu-id="b586f-149">Parameter namnet är valfritt.</span><span class="sxs-lookup"><span data-stu-id="b586f-149">The parameter name is optional.</span></span>
<span data-ttu-id="b586f-150">Du kan använda *namn* eller dess alias, *ServiceName* eller så kan du utelämna parameter namnet.</span><span class="sxs-lookup"><span data-stu-id="b586f-150">You can use *Name* or its alias, *ServiceName* , or you can omit the parameter name.</span></span>

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

### <span data-ttu-id="b586f-151">– PassThru</span><span class="sxs-lookup"><span data-stu-id="b586f-151">-PassThru</span></span>

<span data-ttu-id="b586f-152">Returnerar ett objekt som representerar det objekt som du arbetar med.</span><span class="sxs-lookup"><span data-stu-id="b586f-152">Returns an object representing the item with which you are working.</span></span>
<span data-ttu-id="b586f-153">Som standard genererar denna cmdlet inga utdata.</span><span class="sxs-lookup"><span data-stu-id="b586f-153">By default, this cmdlet does not generate any output.</span></span>

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

### <span data-ttu-id="b586f-154">-Confirm</span><span class="sxs-lookup"><span data-stu-id="b586f-154">-Confirm</span></span>

<span data-ttu-id="b586f-155">Uppmanar dig att bekräfta innan du kör cmdleten.</span><span class="sxs-lookup"><span data-stu-id="b586f-155">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="b586f-156">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="b586f-156">-WhatIf</span></span>

<span data-ttu-id="b586f-157">Visar vad som skulle hända om cmdleten kördes.</span><span class="sxs-lookup"><span data-stu-id="b586f-157">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="b586f-158">Cmdleten körs inte.</span><span class="sxs-lookup"><span data-stu-id="b586f-158">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="b586f-159">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="b586f-159">CommonParameters</span></span>

<span data-ttu-id="b586f-160">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="b586f-160">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="b586f-161">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="b586f-161">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="b586f-162">INDATA</span><span class="sxs-lookup"><span data-stu-id="b586f-162">INPUTS</span></span>

### <span data-ttu-id="b586f-163">System. ServiceProcess. ServiceController, system. String</span><span class="sxs-lookup"><span data-stu-id="b586f-163">System.ServiceProcess.ServiceController, System.String</span></span>

<span data-ttu-id="b586f-164">Du kan skicka vidare ett tjänst objekt eller en sträng som innehåller ett tjänst namn till denna cmdlet.</span><span class="sxs-lookup"><span data-stu-id="b586f-164">You can pipe a service object or a string that contains a service name to this cmdlet.</span></span>

## <span data-ttu-id="b586f-165">UTDATA</span><span class="sxs-lookup"><span data-stu-id="b586f-165">OUTPUTS</span></span>

### <span data-ttu-id="b586f-166">Ingen, system. ServiceProcess. ServiceController</span><span class="sxs-lookup"><span data-stu-id="b586f-166">None, System.ServiceProcess.ServiceController</span></span>

<span data-ttu-id="b586f-167">Denna cmdlet skapar ett **system. ServiceProcess. ServiceController** -objekt som representerar tjänsten om du anger parametern *Passthru* .</span><span class="sxs-lookup"><span data-stu-id="b586f-167">This cmdlet generates a **System.ServiceProcess.ServiceController** object that represents the service, if you specify the *PassThru* parameter.</span></span>
<span data-ttu-id="b586f-168">Annars genererar denna cmdlet inga utdata.</span><span class="sxs-lookup"><span data-stu-id="b586f-168">Otherwise, this cmdlet does not generate any output.</span></span>

## <span data-ttu-id="b586f-169">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="b586f-169">NOTES</span></span>

* <span data-ttu-id="b586f-170">**Suspend-service** kan bara styra tjänster när den aktuella användaren har behörighet att göra detta.</span><span class="sxs-lookup"><span data-stu-id="b586f-170">**Suspend-Service** can control services only when the current user has permission to do this.</span></span> <span data-ttu-id="b586f-171">Om ett kommando inte fungerar som det ska kanske du inte har de behörigheter som krävs.</span><span class="sxs-lookup"><span data-stu-id="b586f-171">If a command does not work correctly, you might not have the required permissions.</span></span>
* <span data-ttu-id="b586f-172">**Suspend-service** kan bara pausa tjänster som stöder inaktive ring och återupptagning.</span><span class="sxs-lookup"><span data-stu-id="b586f-172">**Suspend-Service** can suspend only services that support being suspended and resumed.</span></span> <span data-ttu-id="b586f-173">För att avgöra om en viss tjänst kan pausas använder du Get-Service-cmdlet tillsammans med egenskapen **CanPauseAndContinue** .</span><span class="sxs-lookup"><span data-stu-id="b586f-173">To determine whether a particular service can be suspended, use the Get-Service cmdlet together with the **CanPauseAndContinue** property.</span></span> <span data-ttu-id="b586f-174">Till exempel `Get-Service wmi | Format-List Name, CanPauseAndContinue`.</span><span class="sxs-lookup"><span data-stu-id="b586f-174">For example, `Get-Service wmi | Format-List Name, CanPauseAndContinue`.</span></span> <span data-ttu-id="b586f-175">Om du vill hitta alla tjänster på datorn som kan inaktive ras skriver du `Get-Service | Where-Object {$_.CanPauseAndContinue -eq $true}` .</span><span class="sxs-lookup"><span data-stu-id="b586f-175">To find all services on the computer that can be suspended, type `Get-Service | Where-Object {$_.CanPauseAndContinue -eq $true}`.</span></span>
* <span data-ttu-id="b586f-176">Skriv **Get-service** för att hitta tjänst namn och visnings namn för tjänsterna i systemet.</span><span class="sxs-lookup"><span data-stu-id="b586f-176">To find the service names and display names of the services on your system, type **Get-Service**.</span></span> <span data-ttu-id="b586f-177">Tjänst namnen visas i kolumnen **namn** och visnings namnen visas i kolumnen **DisplayName** .</span><span class="sxs-lookup"><span data-stu-id="b586f-177">The service names appear in the **Name** column, and the display names appear in the **DisplayName** column.</span></span>

## <span data-ttu-id="b586f-178">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="b586f-178">RELATED LINKS</span></span>

[<span data-ttu-id="b586f-179">Get-Service</span><span class="sxs-lookup"><span data-stu-id="b586f-179">Get-Service</span></span>](Get-Service.md)

[<span data-ttu-id="b586f-180">New-Service</span><span class="sxs-lookup"><span data-stu-id="b586f-180">New-Service</span></span>](New-Service.md)

[<span data-ttu-id="b586f-181">Restart-Service</span><span class="sxs-lookup"><span data-stu-id="b586f-181">Restart-Service</span></span>](Restart-Service.md)

[<span data-ttu-id="b586f-182">Resume-Service</span><span class="sxs-lookup"><span data-stu-id="b586f-182">Resume-Service</span></span>](Resume-Service.md)

[<span data-ttu-id="b586f-183">Set-Service</span><span class="sxs-lookup"><span data-stu-id="b586f-183">Set-Service</span></span>](Set-Service.md)

[<span data-ttu-id="b586f-184">Start-Service</span><span class="sxs-lookup"><span data-stu-id="b586f-184">Start-Service</span></span>](Start-Service.md)

[<span data-ttu-id="b586f-185">Stop-Service</span><span class="sxs-lookup"><span data-stu-id="b586f-185">Stop-Service</span></span>](Stop-Service.md)

[<span data-ttu-id="b586f-186">Remove-service</span><span class="sxs-lookup"><span data-stu-id="b586f-186">Remove-Service</span></span>](Remove-Service.md)
