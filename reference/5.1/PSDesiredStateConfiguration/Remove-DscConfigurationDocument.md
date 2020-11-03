---
external help file: Remove-DscConfigurationDocument.cdxml-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSDesiredStateConfiguration
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psdesiredstateconfiguration/remove-dscconfigurationdocument?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Remove-DscConfigurationDocument
ms.openlocfilehash: d3e9b15dfeea94921503247adc08b291eed9d7d7
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93266036"
---
# <span data-ttu-id="01f36-103">Remove-DscConfigurationDocument</span><span class="sxs-lookup"><span data-stu-id="01f36-103">Remove-DscConfigurationDocument</span></span>

## <span data-ttu-id="01f36-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="01f36-104">SYNOPSIS</span></span>
<span data-ttu-id="01f36-105">Tar bort ett konfigurations dokument från DSC-konfigurationsdatabasen.</span><span class="sxs-lookup"><span data-stu-id="01f36-105">Removes a configuration document from the DSC configuration store.</span></span>

## <span data-ttu-id="01f36-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="01f36-106">SYNTAX</span></span>

```
Remove-DscConfigurationDocument -Stage <Stage> [-Force] [-CimSession <CimSession[]>] [-ThrottleLimit <Int32>]
 [-AsJob] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="01f36-107">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="01f36-107">DESCRIPTION</span></span>
<span data-ttu-id="01f36-108">`Remove-DscConfigurationDocument`Cmdleten tar bort ett konfigurations dokument (MOF-fil) från konfigurations lagringen för Desired State Configuration (DSC) i Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="01f36-108">The `Remove-DscConfigurationDocument` cmdlet removes a configuration document (.mof file) from the Windows PowerShell Desired State Configuration (DSC) configuration store.</span></span>
<span data-ttu-id="01f36-109">Under konfigurationen `Start-DscConfiguration` kopierar cmdleten en. MOF-fil till en mapp på mål datorn.</span><span class="sxs-lookup"><span data-stu-id="01f36-109">During configuration, the `Start-DscConfiguration` cmdlet copies a .mof file to a folder on the target computer.</span></span>
<span data-ttu-id="01f36-110">Denna cmdlet tar bort konfigurations dokumentet och gör ytterligare rensning.</span><span class="sxs-lookup"><span data-stu-id="01f36-110">This cmdlet removes that configuration document and does additional cleanup.</span></span>

<span data-ttu-id="01f36-111">Den här cmdleten är endast tillgänglig som en del av den [samlade uppdateringen November 2014 för Windows RT 8,1, Windows 8,1 och Windows Server 2012 R2](https://support.microsoft.com/kb/3000850) från Microsoft Support-biblioteket.</span><span class="sxs-lookup"><span data-stu-id="01f36-111">This cmdlet is available only as part of the [November 2014 update rollup for Windows RT 8.1, Windows 8.1, and Windows Server 2012 R2](https://support.microsoft.com/kb/3000850) from the Microsoft Support library.</span></span>

## <span data-ttu-id="01f36-112">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="01f36-112">EXAMPLES</span></span>

### <span data-ttu-id="01f36-113">Exempel 1: ta bort det aktuella konfigurations dokumentet</span><span class="sxs-lookup"><span data-stu-id="01f36-113">Example 1: Remove the current configuration document</span></span>

```
PS C:\> $Session = New-CimSession -ComputerName "Server01" -Credential ACCOUNTS\PattiFuller
PS C:\> Remove-DscConfigurationDocument -Stage Current -CimSession $Session
```

<span data-ttu-id="01f36-114">Det första kommandot skapar en CIM-session med hjälp av cmdleten **New-CimSession** och lagrar sedan **CimSession** -objektet i variabeln $session.</span><span class="sxs-lookup"><span data-stu-id="01f36-114">The first command creates a CIM session by using the **New-CimSession** cmdlet, and then stores the **CimSession** object in the $Session variable.</span></span>
<span data-ttu-id="01f36-115">I kommandot uppmanas du att ange ett lösen ord.</span><span class="sxs-lookup"><span data-stu-id="01f36-115">The command prompts you for a password.</span></span>
<span data-ttu-id="01f36-116">För mer information ange `Get-Help New-CimSession`.</span><span class="sxs-lookup"><span data-stu-id="01f36-116">For more information, type `Get-Help New-CimSession`.</span></span>

<span data-ttu-id="01f36-117">Det andra kommandot tar bort det aktuella konfigurations dokumentet för den dator som anges i **CimSession** som lagras i $session.</span><span class="sxs-lookup"><span data-stu-id="01f36-117">The second command removes the current configuration document for the computer specified in the **CimSession** stored in $Session.</span></span>

## <span data-ttu-id="01f36-118">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="01f36-118">PARAMETERS</span></span>

### <span data-ttu-id="01f36-119">– AsJob</span><span class="sxs-lookup"><span data-stu-id="01f36-119">-AsJob</span></span>
<span data-ttu-id="01f36-120">Anger att denna cmdlet kör kommandot som ett bakgrunds jobb.</span><span class="sxs-lookup"><span data-stu-id="01f36-120">Indicates that this cmdlet runs the command as a background job.</span></span>

<span data-ttu-id="01f36-121">Om du anger parametern *AsJob* , returnerar kommandot ett objekt som representerar jobbet och visar sedan kommando tolken.</span><span class="sxs-lookup"><span data-stu-id="01f36-121">If you specify the *AsJob* parameter, the command returns an object that represents the job, and then displays the command prompt.</span></span>
<span data-ttu-id="01f36-122">Du kan fortsätta att arbeta i sessionen tills jobbet har slutförts.</span><span class="sxs-lookup"><span data-stu-id="01f36-122">You can continue to work in the session until the job finishes.</span></span>
<span data-ttu-id="01f36-123">Jobbet skapas på den lokala datorn och resultaten från fjärrdatorer returneras automatiskt till den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="01f36-123">The job is created on the local computer and the results from remote computers are automatically returned to the local computer.</span></span>
<span data-ttu-id="01f36-124">Använd jobb-cmdletar för att hantera jobbet.</span><span class="sxs-lookup"><span data-stu-id="01f36-124">To manage the job, use the Job cmdlets.</span></span>
<span data-ttu-id="01f36-125">Använd Receive-Job-cmdleten för att hämta jobb resultatet.</span><span class="sxs-lookup"><span data-stu-id="01f36-125">To get the job results, use the Receive-Job cmdlet.</span></span>

<span data-ttu-id="01f36-126">Om du vill använda den här parametern måste lokala och fjärranslutna datorer konfigureras för fjärr kommunikation och i Windows Vista och senare versioner av Windows operativ system måste du öppna Windows PowerShell med alternativet Kör som administratör.</span><span class="sxs-lookup"><span data-stu-id="01f36-126">To use this parameter, the local and remote computers must be configured for remoting, and on Windows Vista and later versions of the Windows operating system, you must open Windows PowerShell with the Run as administrator option.</span></span>
<span data-ttu-id="01f36-127">Mer information finns i [about_Remote_Requirements](../Microsoft.PowerShell.Core/About/about_Remote_Requirements.md).</span><span class="sxs-lookup"><span data-stu-id="01f36-127">For more information, see [about_Remote_Requirements](../Microsoft.PowerShell.Core/About/about_Remote_Requirements.md).</span></span>

<span data-ttu-id="01f36-128">Mer information om bakgrunds jobb i Windows PowerShell finns i [about_Jobs](../Microsoft.PowerShell.Core/About/about_Jobs.md) och [about_Remote_Jobs](../Microsoft.PowerShell.Core/About/about_Remote_Jobs.md).</span><span class="sxs-lookup"><span data-stu-id="01f36-128">For more information about Windows PowerShell background jobs, see [about_Jobs](../Microsoft.PowerShell.Core/About/about_Jobs.md) and [about_Remote_Jobs](../Microsoft.PowerShell.Core/About/about_Remote_Jobs.md).</span></span>

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

### <span data-ttu-id="01f36-129">– CimSession</span><span class="sxs-lookup"><span data-stu-id="01f36-129">-CimSession</span></span>
<span data-ttu-id="01f36-130">Kör cmdleten i en fjärran sluten session eller på en fjärrdator.</span><span class="sxs-lookup"><span data-stu-id="01f36-130">Runs the cmdlet in a remote session or on a remote computer.</span></span>
<span data-ttu-id="01f36-131">Ange ett dator namn eller ett sessionsobjekt, till exempel utdata från en **New-CimSession-** eller **Get-CimSession-** cmdlet.</span><span class="sxs-lookup"><span data-stu-id="01f36-131">Enter a computer name or a session object, such as the output of a **New-CimSession** or **Get-CimSession** cmdlet.</span></span>

```yaml
Type: Microsoft.Management.Infrastructure.CimSession[]
Parameter Sets: (All)
Aliases: Session

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="01f36-132">-Force</span><span class="sxs-lookup"><span data-stu-id="01f36-132">-Force</span></span>
<span data-ttu-id="01f36-133">Anger att den här cmdleten stoppar det pågående konfigurations jobbet innan det tar bort konfigurations dokumentet.</span><span class="sxs-lookup"><span data-stu-id="01f36-133">Indicates that this cmdlet stops the running configuration job before it removes the configuration document.</span></span>
<span data-ttu-id="01f36-134">Tvingar kommandot att köras utan att fråga användaren om bekräftelse.</span><span class="sxs-lookup"><span data-stu-id="01f36-134">Forces the command to run without asking for user confirmation.</span></span>

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

### <span data-ttu-id="01f36-135">– Steg</span><span class="sxs-lookup"><span data-stu-id="01f36-135">-Stage</span></span>
<span data-ttu-id="01f36-136">Anger vilket konfigurations dokument som ska tas bort.</span><span class="sxs-lookup"><span data-stu-id="01f36-136">Specifies which configuration document to remove.</span></span>
<span data-ttu-id="01f36-137">Du kan ange flera dokument.</span><span class="sxs-lookup"><span data-stu-id="01f36-137">You can specify multiple documents.</span></span>
<span data-ttu-id="01f36-138">De acceptabla värdena för den här parametern är:</span><span class="sxs-lookup"><span data-stu-id="01f36-138">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="01f36-139">Tillfället.</span><span class="sxs-lookup"><span data-stu-id="01f36-139">Current.</span></span>
<span data-ttu-id="01f36-140">Ta bort konfigurations dokumentet som beskriver systemets aktuella tillstånd.</span><span class="sxs-lookup"><span data-stu-id="01f36-140">Remove the configuration document that describes the current state of the system.</span></span>
- <span data-ttu-id="01f36-141">Väntande.</span><span class="sxs-lookup"><span data-stu-id="01f36-141">Pending.</span></span>
<span data-ttu-id="01f36-142">Ta bort konfigurations dokumentet som beskriver systemets väntande tillstånd.</span><span class="sxs-lookup"><span data-stu-id="01f36-142">Remove the configuration document that describes the pending state of the system.</span></span>
- <span data-ttu-id="01f36-143">Ursprungliga.</span><span class="sxs-lookup"><span data-stu-id="01f36-143">Previous.</span></span>
<span data-ttu-id="01f36-144">Ta bort konfigurations dokumentet som beskriver systemets tidigare tillstånd.</span><span class="sxs-lookup"><span data-stu-id="01f36-144">Remove the configuration document that describes the previous state of the system.</span></span>

```yaml
Type: Microsoft.PowerShell.Cmdletization.GeneratedTypes.RemoveDscConfigurationDocument.Stage
Parameter Sets: (All)
Aliases:
Accepted values: Current, Pending, Previous

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="01f36-145">-ThrottleLimit</span><span class="sxs-lookup"><span data-stu-id="01f36-145">-ThrottleLimit</span></span>
<span data-ttu-id="01f36-146">Anger det maximala antalet samtidiga åtgärder som kan upprättas för att köra cmdleten.</span><span class="sxs-lookup"><span data-stu-id="01f36-146">Specifies the maximum number of concurrent operations that can be established to run the cmdlet.</span></span>
<span data-ttu-id="01f36-147">Om den här parametern utelämnas eller värdet `0` anges, beräknar Windows PowerShell en optimal begränsnings gräns för cmdleten baserat på antalet CIM-cmdletar som körs på datorn.</span><span class="sxs-lookup"><span data-stu-id="01f36-147">If this parameter is omitted or a value of `0` is entered, then Windows PowerShell calculates an optimum throttle limit for the cmdlet based on the number of CIM cmdlets that are running on the computer.</span></span>
<span data-ttu-id="01f36-148">Begränsnings gränsen gäller endast för den aktuella cmdleten, inte sessionen eller till datorn.</span><span class="sxs-lookup"><span data-stu-id="01f36-148">The throttle limit applies only to the current cmdlet, not to the session or to the computer.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="01f36-149">-Confirm</span><span class="sxs-lookup"><span data-stu-id="01f36-149">-Confirm</span></span>
<span data-ttu-id="01f36-150">Uppmanar dig att bekräfta innan du kör cmdleten.</span><span class="sxs-lookup"><span data-stu-id="01f36-150">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="01f36-151">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="01f36-151">-WhatIf</span></span>
<span data-ttu-id="01f36-152">Visar vad som skulle hända om cmdleten kördes.</span><span class="sxs-lookup"><span data-stu-id="01f36-152">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="01f36-153">Cmdleten körs inte.</span><span class="sxs-lookup"><span data-stu-id="01f36-153">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="01f36-154">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="01f36-154">CommonParameters</span></span>
<span data-ttu-id="01f36-155">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="01f36-155">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="01f36-156">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="01f36-156">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="01f36-157">INDATA</span><span class="sxs-lookup"><span data-stu-id="01f36-157">INPUTS</span></span>

### <span data-ttu-id="01f36-158">Inget</span><span class="sxs-lookup"><span data-stu-id="01f36-158">None</span></span>

## <span data-ttu-id="01f36-159">UTDATA</span><span class="sxs-lookup"><span data-stu-id="01f36-159">OUTPUTS</span></span>

### <span data-ttu-id="01f36-160">Inget</span><span class="sxs-lookup"><span data-stu-id="01f36-160">None</span></span>

## <span data-ttu-id="01f36-161">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="01f36-161">NOTES</span></span>

## <span data-ttu-id="01f36-162">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="01f36-162">RELATED LINKS</span></span>

[<span data-ttu-id="01f36-163">Översikt över önskad tillstånds konfiguration i Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="01f36-163">Windows PowerShell Desired State Configuration Overview</span></span>](/powershell/scripting/dsc/overview/dscforengineers)

[<span data-ttu-id="01f36-164">Get-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="01f36-164">Get-DscConfiguration</span></span>](Get-DscConfiguration.md)

[<span data-ttu-id="01f36-165">Get-DscConfigurationStatus</span><span class="sxs-lookup"><span data-stu-id="01f36-165">Get-DscConfigurationStatus</span></span>](Get-DscConfigurationStatus.md)
