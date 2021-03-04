---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/clear-eventlog?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Clear-EventLog
ms.openlocfilehash: af1c808b22a812700857e756136fd570fa0acc35
ms.sourcegitcommit: 1dfd5554b70c7e8f4e3df19e29c384a9c0a4b227
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/03/2021
ms.locfileid: "101685908"
---
# <span data-ttu-id="8183b-103">Clear-EventLog</span><span class="sxs-lookup"><span data-stu-id="8183b-103">Clear-EventLog</span></span>

## <span data-ttu-id="8183b-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="8183b-104">SYNOPSIS</span></span>
<span data-ttu-id="8183b-105">Tar bort alla poster från angivna händelse loggar på lokala eller fjärranslutna datorer.</span><span class="sxs-lookup"><span data-stu-id="8183b-105">Clears all entries from specified event logs on the local or remote computers.</span></span>

## <span data-ttu-id="8183b-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="8183b-106">SYNTAX</span></span>

```
Clear-EventLog [-LogName] <String[]> [[-ComputerName] <String[]>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="8183b-107">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="8183b-107">DESCRIPTION</span></span>

<span data-ttu-id="8183b-108">`Clear-EventLog`Cmdleten tar bort alla poster från de angivna händelse loggarna på den lokala datorn eller på fjärrdatorer.</span><span class="sxs-lookup"><span data-stu-id="8183b-108">The `Clear-EventLog` cmdlet deletes all of the entries from the specified event logs on the local computer or on remote computers.</span></span> <span data-ttu-id="8183b-109">För att kunna använda `Clear-EventLog` måste du vara medlem i gruppen Administratörer på den berörda datorn.</span><span class="sxs-lookup"><span data-stu-id="8183b-109">To use `Clear-EventLog`, you must be a member of the Administrators group on the affected computer.</span></span>

<span data-ttu-id="8183b-110">De cmdletar som innehåller **EventLog** -händelsen Substantiv (EventLog-cmdletar) fungerar bara på klassiska händelse loggar.</span><span class="sxs-lookup"><span data-stu-id="8183b-110">The cmdlets that contain the **EventLog** noun (the EventLog cmdlets) work only on classic event logs.</span></span> <span data-ttu-id="8183b-111">Om du vill hämta händelser från loggar som använder Windows händelse logg teknik i Windows Vista och senare versioner av Windows, använder du Get-WinEvent-cmdleten.</span><span class="sxs-lookup"><span data-stu-id="8183b-111">To get events from logs that use the Windows Event Log technology in Windows Vista and later versions of Windows, use the Get-WinEvent cmdlet.</span></span>

## <span data-ttu-id="8183b-112">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="8183b-112">EXAMPLES</span></span>

### <span data-ttu-id="8183b-113">Exempel 1: rensa vissa händelse logg typer från den lokala datorn</span><span class="sxs-lookup"><span data-stu-id="8183b-113">Example 1: Clear specific event log types from the local computer</span></span>

```powershell
Clear-EventLog "Windows PowerShell"
```

<span data-ttu-id="8183b-114">Det här kommandot rensar posterna från Windows PowerShell-händelseloggen på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="8183b-114">This command clears the entries from the Windows PowerShell event log on the local computer.</span></span>

### <span data-ttu-id="8183b-115">Exempel 2: ta bort vissa olika logg typer från lokala datorer och fjärrdatorer</span><span class="sxs-lookup"><span data-stu-id="8183b-115">Example 2: Clear specific multiple log types from the local and remote computers</span></span>

```powershell
Clear-EventLog -LogName ODiag, OSession -ComputerName localhost, Server02
```

<span data-ttu-id="8183b-116">Med det här kommandot rensas alla poster i ODiag-(Microsoft Office Diagnostics) och Microsoft Office-sessioner (OSession) på den lokala datorn och på Server02-fjärrdatorn.</span><span class="sxs-lookup"><span data-stu-id="8183b-116">This command clears all of the entries in the Microsoft Office Diagnostics (ODiag) and Microsoft Office Sessions (OSession) logs on the local computer and the Server02 remote computer.</span></span>

### <span data-ttu-id="8183b-117">Exempel 3: Rensa alla loggar på de angivna datorerna och Visa sedan händelse logg listan</span><span class="sxs-lookup"><span data-stu-id="8183b-117">Example 3: Clear all logs on the specified computers then display the event log list</span></span>

```powershell
Clear-EventLog -LogName application, system -confirm
```

<span data-ttu-id="8183b-118">Med det här kommandot uppmanas du att bekräfta innan du tar bort posterna i de angivna händelse loggarna.</span><span class="sxs-lookup"><span data-stu-id="8183b-118">This command prompts you for confirmation before deleting the entries in the specified event logs.</span></span>

### <span data-ttu-id="8183b-119">Exempel 4: Rensa alla loggar på de angivna datorerna och Visa sedan händelse logg listan</span><span class="sxs-lookup"><span data-stu-id="8183b-119">Example 4: Clear all logs on the specified computers then display the event log list</span></span>

```powershell
function clear-all-event-logs ($computerName="localhost")
{
   $logs = Get-EventLog -ComputerName $computername -List | ForEach-Object {$_.Log}
   $logs | ForEach-Object {Clear-EventLog -ComputerName $computername -LogName $_ }
   Get-EventLog -ComputerName $computername -list
}

clear-all-event-logs -ComputerName Server01
```

```Output
Max(K) Retain OverflowAction        Entries Log
------ ------ --------------        ------- ---
15,168      0 OverwriteAsNeeded           0 Application
15,168      0 OverwriteAsNeeded           0 DFS Replication
512         7 OverwriteOlder              0 DxStudio
20,480      0 OverwriteAsNeeded           0 Hardware Events
512         7 OverwriteOlder              0 Internet Explorer
20,480      0 OverwriteAsNeeded           0 Key Management Service
16,384      0 OverwriteAsNeeded           0 Microsoft Office Diagnostics
16,384      0 OverwriteAsNeeded           0 Microsoft Office Sessions
30,016      0 OverwriteAsNeeded           1 Security
15,168      0 OverwriteAsNeeded           2 System
15,360      0 OverwriteAsNeeded           0 Windows PowerShell
```

<span data-ttu-id="8183b-120">Den här funktionen rensar alla händelse loggar på de angivna datorerna och visar sedan den resulterande händelse logg listan.</span><span class="sxs-lookup"><span data-stu-id="8183b-120">This function clears all event logs on the specified computers and then displays the resulting event log list.</span></span>

<span data-ttu-id="8183b-121">Observera att några poster har lagts till i systemet och säkerhets loggar när loggarna rensades, men innan de visades.</span><span class="sxs-lookup"><span data-stu-id="8183b-121">Notice that a few entries were added to the System and Security logs after the logs were cleared but before they were displayed.</span></span>

## <span data-ttu-id="8183b-122">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="8183b-122">PARAMETERS</span></span>

### <span data-ttu-id="8183b-123">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="8183b-123">-ComputerName</span></span>

<span data-ttu-id="8183b-124">Anger en fjärrdator.</span><span class="sxs-lookup"><span data-stu-id="8183b-124">Specifies a remote computer.</span></span> <span data-ttu-id="8183b-125">Standard är den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="8183b-125">The default is the local computer.</span></span>

<span data-ttu-id="8183b-126">Ange NetBIOS-namnet, en Internet Protocol IP-adress eller ett fullständigt kvalificerat domän namn för en fjärrdator.</span><span class="sxs-lookup"><span data-stu-id="8183b-126">Type the NetBIOS name, an Internet Protocol (IP) address, or a fully qualified domain name of a remote computer.</span></span> <span data-ttu-id="8183b-127">Om du vill ange den lokala datorn skriver du datorns namn, en punkt (.) eller "localhost".</span><span class="sxs-lookup"><span data-stu-id="8183b-127">To specify the local computer, type the computer name, a dot (.), or "localhost".</span></span>

<span data-ttu-id="8183b-128">Den här parametern är inte beroende av Windows PowerShell-fjärrkommunikation.</span><span class="sxs-lookup"><span data-stu-id="8183b-128">This parameter does not rely on Windows PowerShell remoting.</span></span> <span data-ttu-id="8183b-129">Du kan använda parametern **computername** för `Get-EventLog` även om datorn inte är konfigurerad för att köra fjärrkommandon.</span><span class="sxs-lookup"><span data-stu-id="8183b-129">You can use the **ComputerName** parameter of `Get-EventLog` even if your computer is not configured to run remote commands.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: Cn

Required: False
Position: 1
Default value: Local computer
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="8183b-130">-LogName</span><span class="sxs-lookup"><span data-stu-id="8183b-130">-LogName</span></span>

<span data-ttu-id="8183b-131">Anger händelse loggarna.</span><span class="sxs-lookup"><span data-stu-id="8183b-131">Specifies the event logs.</span></span> <span data-ttu-id="8183b-132">Ange logg namnet (värdet för **logg** egenskapen inte **LogDisplayName**) för en eller flera händelse loggar, avgränsade med kommatecken.</span><span class="sxs-lookup"><span data-stu-id="8183b-132">Enter the log name (the value of the **Log** property not the **LogDisplayName**) of one or more event logs, separated by commas.</span></span> <span data-ttu-id="8183b-133">Jokertecken tillåts inte.</span><span class="sxs-lookup"><span data-stu-id="8183b-133">Wildcard characters are not permitted.</span></span> <span data-ttu-id="8183b-134">Den här parametern är obligatorisk.</span><span class="sxs-lookup"><span data-stu-id="8183b-134">This parameter is required.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="8183b-135">Den här parametern ska acceptera värden från pipelinen efter egenskaps namn.</span><span class="sxs-lookup"><span data-stu-id="8183b-135">This parameter is supposed to accept values from the pipeline by property name.</span></span> <span data-ttu-id="8183b-136">Det finns dock ett fel som förhindrar att detta fungerar.</span><span class="sxs-lookup"><span data-stu-id="8183b-136">However, there is a bug that prevents this from working.</span></span> <span data-ttu-id="8183b-137">Du måste skicka ett värde med hjälp av parametern direkt.</span><span class="sxs-lookup"><span data-stu-id="8183b-137">You must pass a value using the parameter directly.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: LN

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="8183b-138">-Confirm</span><span class="sxs-lookup"><span data-stu-id="8183b-138">-Confirm</span></span>

<span data-ttu-id="8183b-139">Uppmanar dig att bekräfta innan du kör cmdleten.</span><span class="sxs-lookup"><span data-stu-id="8183b-139">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="8183b-140">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="8183b-140">-WhatIf</span></span>

<span data-ttu-id="8183b-141">Visar vad som skulle hända om cmdleten kördes.</span><span class="sxs-lookup"><span data-stu-id="8183b-141">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="8183b-142">Cmdleten körs inte.</span><span class="sxs-lookup"><span data-stu-id="8183b-142">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="8183b-143">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="8183b-143">CommonParameters</span></span>

<span data-ttu-id="8183b-144">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="8183b-144">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="8183b-145">Mer information finns i [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span><span class="sxs-lookup"><span data-stu-id="8183b-145">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="8183b-146">INDATA</span><span class="sxs-lookup"><span data-stu-id="8183b-146">INPUTS</span></span>

### <span data-ttu-id="8183b-147">Inget</span><span class="sxs-lookup"><span data-stu-id="8183b-147">None</span></span>

<span data-ttu-id="8183b-148">Det går inte att skicka pipe-objekt till `Clear-EventLog` .</span><span class="sxs-lookup"><span data-stu-id="8183b-148">You cannot pipe objects to `Clear-EventLog`.</span></span>

## <span data-ttu-id="8183b-149">UTDATA</span><span class="sxs-lookup"><span data-stu-id="8183b-149">OUTPUTS</span></span>

### <span data-ttu-id="8183b-150">Inget</span><span class="sxs-lookup"><span data-stu-id="8183b-150">None</span></span>

<span data-ttu-id="8183b-151">Denna cmdlet genererar inga utdata.</span><span class="sxs-lookup"><span data-stu-id="8183b-151">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="8183b-152">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="8183b-152">NOTES</span></span>

- <span data-ttu-id="8183b-153">Om du vill använda `Clear-EventLog` i Windows Vista och senare versioner av Windows startar du Windows PowerShell med alternativet "kör som administratör".</span><span class="sxs-lookup"><span data-stu-id="8183b-153">To use `Clear-EventLog` on Windows Vista and later versions of Windows, start Windows PowerShell with the "Run as administrator" option.</span></span>

## <span data-ttu-id="8183b-154">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="8183b-154">RELATED LINKS</span></span>

[<span data-ttu-id="8183b-155">Get-EventLog</span><span class="sxs-lookup"><span data-stu-id="8183b-155">Get-EventLog</span></span>](Get-EventLog.md)

[<span data-ttu-id="8183b-156">Begränsning-EventLog</span><span class="sxs-lookup"><span data-stu-id="8183b-156">Limit-EventLog</span></span>](Limit-EventLog.md)

[<span data-ttu-id="8183b-157">Ny-EventLog</span><span class="sxs-lookup"><span data-stu-id="8183b-157">New-EventLog</span></span>](New-EventLog.md)

[<span data-ttu-id="8183b-158">Ta bort-EventLog</span><span class="sxs-lookup"><span data-stu-id="8183b-158">Remove-EventLog</span></span>](Remove-EventLog.md)

[<span data-ttu-id="8183b-159">Visa-EventLog</span><span class="sxs-lookup"><span data-stu-id="8183b-159">Show-EventLog</span></span>](Show-EventLog.md)

[<span data-ttu-id="8183b-160">Skriv-EventLog</span><span class="sxs-lookup"><span data-stu-id="8183b-160">Write-EventLog</span></span>](Write-EventLog.md)
