---
external help file: Microsoft.PowerShell.ScheduledJob.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSScheduledJob
ms.date: 10/25/2019
online version: https://docs.microsoft.com/powershell/module/psscheduledjob/register-scheduledjob?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Register-ScheduledJob
ms.openlocfilehash: 89887474142490a71d372577576fb0059b4ff12e
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93264639"
---
# <span data-ttu-id="ee7d7-103">Register-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="ee7d7-103">Register-ScheduledJob</span></span>

## <span data-ttu-id="ee7d7-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="ee7d7-104">SYNOPSIS</span></span>
<span data-ttu-id="ee7d7-105">Skapar ett schemalagt jobb.</span><span class="sxs-lookup"><span data-stu-id="ee7d7-105">Creates a scheduled job.</span></span>

## <span data-ttu-id="ee7d7-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="ee7d7-106">SYNTAX</span></span>

### <span data-ttu-id="ee7d7-107">Script block (standard)</span><span class="sxs-lookup"><span data-stu-id="ee7d7-107">ScriptBlock (Default)</span></span>

```
Register-ScheduledJob [-ScriptBlock] <ScriptBlock> [-Name] <String>
 [-Trigger <ScheduledJobTrigger[]>] [-InitializationScript <ScriptBlock>] [-RunAs32]
 [-Credential <PSCredential>] [-Authentication <AuthenticationMechanism>]
 [-ScheduledJobOption <ScheduledJobOptions>] [-ArgumentList <Object[]>] [-MaxResultCount <Int32>]
 [-RunNow] [-RunEvery <TimeSpan>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="ee7d7-108">FilePath</span><span class="sxs-lookup"><span data-stu-id="ee7d7-108">FilePath</span></span>

```
Register-ScheduledJob [-FilePath] <String> [-Name] <String> [-Trigger <ScheduledJobTrigger[]>]
 [-InitializationScript <ScriptBlock>] [-RunAs32] [-Credential <PSCredential>]
 [-Authentication <AuthenticationMechanism>] [-ScheduledJobOption <ScheduledJobOptions>]
 [-ArgumentList <Object[]>] [-MaxResultCount <Int32>] [-RunNow] [-RunEvery <TimeSpan>] [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="ee7d7-109">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="ee7d7-109">DESCRIPTION</span></span>

<span data-ttu-id="ee7d7-110">`Register-ScheduledJob`Cmdlet: en skapar schemalagda jobb på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="ee7d7-110">The `Register-ScheduledJob` cmdlet creates scheduled jobs on the local computer.</span></span>

<span data-ttu-id="ee7d7-111">Ett schemalagt jobb är ett Windows PowerShell-bakgrunds jobb som kan startas automatiskt vid ett engångs-eller återkommande schema.</span><span class="sxs-lookup"><span data-stu-id="ee7d7-111">A scheduled job is a Windows PowerShell background job that can be started automatically on a one-time or recurring schedule.</span></span> <span data-ttu-id="ee7d7-112">Schemalagda jobb lagras på disk och registreras i Schemaläggaren.</span><span class="sxs-lookup"><span data-stu-id="ee7d7-112">Scheduled jobs are stored on disk and registered in Task Scheduler.</span></span>
<span data-ttu-id="ee7d7-113">Jobben kan hanteras i Schemaläggaren eller med hjälp av de schemalagda jobb-cmdletarna i Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ee7d7-113">The jobs can be managed in Task Scheduler or by using the Scheduled Job cmdlets in Windows PowerShell.</span></span>

<span data-ttu-id="ee7d7-114">När ett schemalagt jobb startar skapas en instans av det schemalagda jobbet.</span><span class="sxs-lookup"><span data-stu-id="ee7d7-114">When a scheduled job starts, it creates an instance of the scheduled job.</span></span> <span data-ttu-id="ee7d7-115">Schemalagda jobb instanser är identiska med bakgrunds jobb i Windows PowerShell, förutom att resultaten sparas på disken.</span><span class="sxs-lookup"><span data-stu-id="ee7d7-115">Scheduled job instances are identical to Windows PowerShell background jobs, except that the results are saved on disk.</span></span> <span data-ttu-id="ee7d7-116">Använd jobb-cmdletarna, till exempel,, `Start-Job` `Get-Job` och `Receive-Job` för att starta, Visa och hämta resultatet av jobb instanserna.</span><span class="sxs-lookup"><span data-stu-id="ee7d7-116">Use the Job cmdlets, such as `Start-Job`, `Get-Job`, and `Receive-Job` to start, view, and get the results of the job instances.</span></span>

<span data-ttu-id="ee7d7-117">Använd `Register-ScheduledJob` för att skapa ett nytt schemalagt jobb.</span><span class="sxs-lookup"><span data-stu-id="ee7d7-117">Use `Register-ScheduledJob` to create a new scheduled job.</span></span> <span data-ttu-id="ee7d7-118">Om du vill ange vilka kommandon som det schemalagda jobbet ska köra använder du parametern **script block** .</span><span class="sxs-lookup"><span data-stu-id="ee7d7-118">To specify the commands that the scheduled job runs, use the **ScriptBlock** parameter.</span></span> <span data-ttu-id="ee7d7-119">Om du vill ange ett skript som jobbet kör använder du parametern **sökväg** .</span><span class="sxs-lookup"><span data-stu-id="ee7d7-119">To specify a script that the job runs, use the **FilePath** parameter.</span></span>

<span data-ttu-id="ee7d7-120">Windows PowerShell – schemalagda jobb använder samma jobb utlösare och jobb alternativ som Schemaläggaren använder för schemalagda aktiviteter.</span><span class="sxs-lookup"><span data-stu-id="ee7d7-120">Windows PowerShell-scheduled jobs use the same job triggers and job options that Task Scheduler uses for scheduled tasks.</span></span>

<span data-ttu-id="ee7d7-121">**Utlösar** -parametern för `Register-ScheduledJob` lägger till en eller flera jobb utlösare som startar jobbet.</span><span class="sxs-lookup"><span data-stu-id="ee7d7-121">The **Trigger** parameter of `Register-ScheduledJob` adds one or more job triggers that start the job.</span></span> <span data-ttu-id="ee7d7-122">**Utlösar** -parametern är valfri, så du kan lägga till utlösare när du skapar det schemalagda jobbet, lägga till jobb utlösare senare, lägga till parametern **RunNow** för att starta jobbet omedelbart, använda `Start-Job` cmdleten för att starta jobbet omedelbart när som helst, eller spara det ej utlösta schemalagda jobbet som en mall för andra jobb.</span><span class="sxs-lookup"><span data-stu-id="ee7d7-122">The **Trigger** parameter is optional, so you can add triggers when you create the scheduled job, add job triggers later, add the **RunNow** parameter to start the job immediately, use the `Start-Job` cmdlet to start the job immediately at any time, or save the untriggered scheduled job as a template for other jobs.</span></span>

<span data-ttu-id="ee7d7-123">Med **alternativ** -parametern kan du anpassa alternativ inställningarna för det schemalagda jobbet.</span><span class="sxs-lookup"><span data-stu-id="ee7d7-123">The **Options** parameter lets you customize the options settings for the scheduled job.</span></span> <span data-ttu-id="ee7d7-124">Parametern **alternativ** är valfri, så du kan ange jobb alternativ när du skapar det schemalagda jobbet eller ändra dem när som helst.</span><span class="sxs-lookup"><span data-stu-id="ee7d7-124">The **Options** parameter is optional, so you can set job options when you create the scheduled job or change them at any time.</span></span> <span data-ttu-id="ee7d7-125">Eftersom inställningarna för jobb alternativ kan förhindra att det schemalagda jobbet körs granskar du jobb alternativen och anger dem noggrant.</span><span class="sxs-lookup"><span data-stu-id="ee7d7-125">Because job option settings can prevent the scheduled job from running, review the job options and set them carefully.</span></span>

<span data-ttu-id="ee7d7-126">`Register-ScheduledJob` är en samling jobb schemaläggnings-cmdletar i **PSScheduledJob** -modulen som ingår i Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ee7d7-126">`Register-ScheduledJob` is one of a collection of job scheduling cmdlets in the **PSScheduledJob** module that is included in Windows PowerShell.</span></span>

<span data-ttu-id="ee7d7-127">Mer information om schemalagda jobb finns i artikeln om artiklar i **PSScheduledJob** -modulen.</span><span class="sxs-lookup"><span data-stu-id="ee7d7-127">For more information about Scheduled Jobs, see the About articles in the **PSScheduledJob** module.</span></span>
<span data-ttu-id="ee7d7-128">Importera modulen **PSScheduledJob** och skriv sedan: `Get-Help about_Scheduled*` eller se [about_Scheduled_Jobs](./about/about_scheduled_jobs.md).</span><span class="sxs-lookup"><span data-stu-id="ee7d7-128">Import the **PSScheduledJob** module and then type: `Get-Help about_Scheduled*` or see [about_Scheduled_Jobs](./about/about_scheduled_jobs.md).</span></span>

<span data-ttu-id="ee7d7-129">Den här cmdleten introducerades i Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="ee7d7-129">This cmdlet was introduced in Windows PowerShell 3.0.</span></span>

## <span data-ttu-id="ee7d7-130">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="ee7d7-130">EXAMPLES</span></span>

### <span data-ttu-id="ee7d7-131">Exempel 1: skapa ett schemalagt jobb</span><span class="sxs-lookup"><span data-stu-id="ee7d7-131">Example 1: Create a scheduled job</span></span>

<span data-ttu-id="ee7d7-132">I det här exemplet skapas ett schemalagt jobb på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="ee7d7-132">This example creates a scheduled job on the local computer.</span></span>

```powershell
Register-ScheduledJob -Name "Archive-Scripts" -ScriptBlock {
  Get-ChildItem $home\*.ps1 -Recurse |
    Copy-Item -Destination "\\Server\Share\PSScriptArchive"
}
```

<span data-ttu-id="ee7d7-133">`Register-ScheduledJob` använder parametern **Name** för att skapa ett schemalagt jobb för **Arkiv skript** .</span><span class="sxs-lookup"><span data-stu-id="ee7d7-133">`Register-ScheduledJob` uses the **Name** parameter to create the **Archive-Scripts** scheduled job.</span></span>
<span data-ttu-id="ee7d7-134">Parametern **script block** körs `Get-ChildItem` som söker igenom `$home` katalogen rekursivt efter `.ps1` filer.</span><span class="sxs-lookup"><span data-stu-id="ee7d7-134">The **ScriptBlock** parameter runs `Get-ChildItem` that searches the `$home` directory recursively for `.ps1` files.</span></span> <span data-ttu-id="ee7d7-135">`Copy-Item`Cmdleten kopierar filerna till en katalog som anges av **mål** parametern.</span><span class="sxs-lookup"><span data-stu-id="ee7d7-135">The `Copy-Item` cmdlet copies the files to a directory specified by the **Destination** parameter.</span></span>

<span data-ttu-id="ee7d7-136">Eftersom det schemalagda jobbet inte innehåller någon utlösare startas det inte automatiskt.</span><span class="sxs-lookup"><span data-stu-id="ee7d7-136">Because the scheduled job doesn't contain a trigger, it's not started automatically.</span></span> <span data-ttu-id="ee7d7-137">Du kan lägga till jobb utlösare med `Add-JobTrigger` , använda `Start-Job` cmdleten för att starta jobbet på begäran eller använda det schemalagda jobbet som en mall för andra schemalagda jobb.</span><span class="sxs-lookup"><span data-stu-id="ee7d7-137">You can add job triggers with `Add-JobTrigger`, use the `Start-Job` cmdlet to start the job on demand, or use the scheduled job as a template for other scheduled jobs.</span></span>

### <span data-ttu-id="ee7d7-138">Exempel 2: skapa ett schemalagt jobb med utlösare och anpassade alternativ</span><span class="sxs-lookup"><span data-stu-id="ee7d7-138">Example 2: Create a scheduled job with triggers and custom options</span></span>

<span data-ttu-id="ee7d7-139">Det här exemplet visar hur du skapar ett schemalagt jobb som har en jobb utlösare och anpassade jobb alternativ.</span><span class="sxs-lookup"><span data-stu-id="ee7d7-139">This example shows how to create a scheduled job that has a job trigger and custom job options.</span></span>

```powershell
$O = New-ScheduledJobOption -WakeToRun -StartIfIdle -MultipleInstancePolicy Queue
$T = New-JobTrigger -Weekly -At "9:00 PM" -DaysOfWeek Monday -WeeksInterval 2
$path = "\\Srv01\Scripts\UpdateVersion.ps1"
Register-ScheduledJob -Name "UpdateVersion" -FilePath $path -ScheduledJobOption $O -Trigger $T
```

<span data-ttu-id="ee7d7-140">`$O`Variabeln lagrar det jobb alternativ objekt som `New-ScheduledJobOption` cmdleten skapade.</span><span class="sxs-lookup"><span data-stu-id="ee7d7-140">The `$O` variable stores the job option object that the `New-ScheduledJobOption` cmdlet created.</span></span> <span data-ttu-id="ee7d7-141">Alternativen startar det schemalagda jobbet även om datorn inte är inaktiv, aktiverar datorn för att köra jobbet, om det behövs, och tillåter att flera instanser av jobbet körs i en serie.</span><span class="sxs-lookup"><span data-stu-id="ee7d7-141">The options start the scheduled job even if the computer isn't idle, wakes the computer to run the job, if necessary, and allows multiple instances of the job to run in a series.</span></span>

<span data-ttu-id="ee7d7-142">`$T`Variabeln lagrar resultatet från `New-JobTrigger` cmdleten för att skapa jobb utlösare som startar ett jobb varannan måndag vid 9:00 PM.</span><span class="sxs-lookup"><span data-stu-id="ee7d7-142">The `$T` variable stores the result from the `New-JobTrigger` cmdlet to create job trigger that starts a job every other Monday at 9:00 PM.</span></span>

<span data-ttu-id="ee7d7-143">`$path`Variabeln lagrar sökvägen till `UpdateVersion.ps1` skript filen.</span><span class="sxs-lookup"><span data-stu-id="ee7d7-143">The `$path` variable stores the path to the `UpdateVersion.ps1` script file.</span></span>

<span data-ttu-id="ee7d7-144">`Register-ScheduledJob` använder **namn** parametern för att skapa det schemalagda **UpdateVersion** -jobbet.</span><span class="sxs-lookup"><span data-stu-id="ee7d7-144">`Register-ScheduledJob` uses the **Name** paramter to create the **UpdateVersion** scheduled job.</span></span>
<span data-ttu-id="ee7d7-145">Parametern **sökväg** används `$path` för att ange det skript som jobbet kör.</span><span class="sxs-lookup"><span data-stu-id="ee7d7-145">The **FilePath** parameter uses `$path` to specify the script that the job runs.</span></span> <span data-ttu-id="ee7d7-146">**ScheduledJobOption** -parametern använder de jobb alternativ som lagras i `$O` .</span><span class="sxs-lookup"><span data-stu-id="ee7d7-146">The **ScheduledJobOption** parameter uses the job options stored in `$O`.</span></span> <span data-ttu-id="ee7d7-147">**Utlösar** -parametern använder de jobb utlösare som lagras i `$T` .</span><span class="sxs-lookup"><span data-stu-id="ee7d7-147">The **Trigger** parameter uses the job triggers stored in `$T`.</span></span>

### <span data-ttu-id="ee7d7-148">Exempel 3: Använd hash-tabeller för att ange alternativ för utlösare och schemalagt jobb</span><span class="sxs-lookup"><span data-stu-id="ee7d7-148">Example 3: Use hash tables to specify a trigger and scheduled job options</span></span>

<span data-ttu-id="ee7d7-149">Det här exemplet har samma resultat som kommandot i exempel 2.</span><span class="sxs-lookup"><span data-stu-id="ee7d7-149">This example has the same effect as the command in Example 2.</span></span> <span data-ttu-id="ee7d7-150">Det skapar ett schemalagt jobb och använder hash-tabeller för att ange värdena för **Utlösar** -och **ScheduledJobOption** -parametrarna.</span><span class="sxs-lookup"><span data-stu-id="ee7d7-150">It creates a scheduled job, using hash tables to specify the values of the **Trigger** and **ScheduledJobOption** parameters.</span></span> <span data-ttu-id="ee7d7-151">`$O` `$T` Variablerna och som definieras i exempel 2 ersätts med hash-tabeller.</span><span class="sxs-lookup"><span data-stu-id="ee7d7-151">The `$O` and `$T`variables defined in Example 2 are replaced with hash tables.</span></span>

```powershell
$T = @{
  Frequency="Weekly"
  At="9:00PM"
  DaysOfWeek="Monday"
  Interval=2
}
$O = @{
  WakeToRun=$true
  StartIfNotIdle=$false
  MultipleInstancePolicy="Queue"
}
Register-ScheduledJob -Trigger $T -ScheduledJobOption $O -Name UpdateVersion -FilePath "\\Srv01\Scripts\Update-Version.ps1"
```

### <span data-ttu-id="ee7d7-152">Exempel 4: skapa schemalagda jobb på fjärrdatorer</span><span class="sxs-lookup"><span data-stu-id="ee7d7-152">Example 4: Create scheduled jobs on remote computers</span></span>

<span data-ttu-id="ee7d7-153">I det här exemplet skapas det schemalagda **EnergyData** -jobbet på flera fjärranslutna datorer.</span><span class="sxs-lookup"><span data-stu-id="ee7d7-153">In this example, the **EnergyData** scheduled job is created on multiple remote computers.</span></span> <span data-ttu-id="ee7d7-154">Det schemalagda jobbet kör ett skript som samlar in rå data och sparar det i en löpande logg på fjärrdatorn.</span><span class="sxs-lookup"><span data-stu-id="ee7d7-154">The scheduled job runs a script that gathers raw data and saves it in a running log on the remote computer.</span></span>

```powershell
$Cred = Get-Credential
$O = New-ScheduledJobOption -WakeToRun -StartIfIdle -MultipleInstancePolicy Queue
$T = New-JobTrigger -Weekly -At "9:00 PM" -DaysOfWeek Monday -WeeksInterval 2
Invoke-Command -ComputerName (Get-Content Servers.txt) -Credential $Cred -ScriptBlock {
  $params = @{
      Name = "Get-EnergyData"
      FilePath = "\\Srv01\Scripts\Get-EnergyData.ps1"
      ScheduledJobOption = $using:O
      Trigger = $using:T
  }
  Register-ScheduledJob @params
}
```

<span data-ttu-id="ee7d7-155">`$Cred`Variabeln lagrar autentiseringsuppgifter i ett **PSCredential** -objekt för en användare med behörighet att skapa schemalagda jobb.</span><span class="sxs-lookup"><span data-stu-id="ee7d7-155">The `$Cred` variable stores credentials in a **PSCredential** object for a user with permissions to create scheduled jobs.</span></span> <span data-ttu-id="ee7d7-156">`$O`Variabeln lagrar de jobb alternativ som skapats med `New-ScheduledJobOption` .</span><span class="sxs-lookup"><span data-stu-id="ee7d7-156">The `$O` variable stores the job options created with `New-ScheduledJobOption`.</span></span> <span data-ttu-id="ee7d7-157">`$T`Variabeln lagrar jobb utlösare som skapats med `New-JobTrigger` .</span><span class="sxs-lookup"><span data-stu-id="ee7d7-157">The `$T` variable stores the job triggers created with `New-JobTrigger`.</span></span>

<span data-ttu-id="ee7d7-158">`Invoke-Command`Cmdlet: en använder parametern **computername** för att hämta en lista över Server namn från `Servers.txt` filen.</span><span class="sxs-lookup"><span data-stu-id="ee7d7-158">The `Invoke-Command` cmdlet uses the **ComputerName** parameter to get a list of server names from the `Servers.txt` file.</span></span> <span data-ttu-id="ee7d7-159">Parametern **Credential** hämtar objektet Credential som lagras i `$Cred` .</span><span class="sxs-lookup"><span data-stu-id="ee7d7-159">The **Credential** parameter gets the credential object stored in `$Cred`.</span></span>
<span data-ttu-id="ee7d7-160">Parametern **script block** kör ett `Register-ScheduledJob` kommando på datorerna i `Servers.txt` filen.</span><span class="sxs-lookup"><span data-stu-id="ee7d7-160">The **ScriptBlock** parameter runs a `Register-ScheduledJob` command on the computers in the `Servers.txt` file.</span></span>

<span data-ttu-id="ee7d7-161">Parametrarna för `Register-ScheduledJob` definieras av `$params` .</span><span class="sxs-lookup"><span data-stu-id="ee7d7-161">The parameters for `Register-ScheduledJob` are defined by `$params`.</span></span> <span data-ttu-id="ee7d7-162">**Namn** parametrarna anger att jobbet heter **Get-EnergyData** på varje fjärrdator.</span><span class="sxs-lookup"><span data-stu-id="ee7d7-162">The **Name** parameters specifies the job is named **Get-EnergyData** on each remote computer.</span></span> <span data-ttu-id="ee7d7-163">**Sökväg** är platsen för `EnergyData.ps1` skriptet.</span><span class="sxs-lookup"><span data-stu-id="ee7d7-163">**FilePath** provides the location of the `EnergyData.ps1` script.</span></span> <span data-ttu-id="ee7d7-164">Skriptet finns på en fil server som är tillgänglig för alla deltagande datorer. Jobbet körs enligt det schema som anges av jobb utlösarna i `$T` och jobb alternativen i `$O` .</span><span class="sxs-lookup"><span data-stu-id="ee7d7-164">The script is located on a file server that is available to all participating computers.The job runs on the schedule specified by the job triggers in `$T` and the job options in `$O`.</span></span>

<span data-ttu-id="ee7d7-165">`Register-ScheduledJob @params`Kommandot skapar det schemalagda jobbet med parametrarna från skript blocket.</span><span class="sxs-lookup"><span data-stu-id="ee7d7-165">The `Register-ScheduledJob @params` command creates the scheduled job with the parameters from the script block.</span></span>

### <span data-ttu-id="ee7d7-166">Exempel 5: skapa ett schemalagt jobb som kör ett skript på fjärrdatorer</span><span class="sxs-lookup"><span data-stu-id="ee7d7-166">Example 5: Create a scheduled job that runs a script on remote computers</span></span>

<span data-ttu-id="ee7d7-167">I det här exemplet skapas det schemalagda **CollectEnergyData** -jobbet på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="ee7d7-167">This example creates the **CollectEnergyData** scheduled job on the local computer.</span></span> <span data-ttu-id="ee7d7-168">Jobbet körs på flera fjärrdatorer.</span><span class="sxs-lookup"><span data-stu-id="ee7d7-168">The job runs on multiple remote computers.</span></span>

```powershell
$Admin = Get-Credential
$T = New-JobTrigger -Weekly -At "9:00 PM" -DaysOfWeek Monday -WeeksInterval 2
Register-ScheduledJob -Name "CollectEnergyData" -Trigger $T -MaxResultCount 99 -ScriptBlock {
  $params = @{
    AsJob = $true
    ComputerName = (Get-Content Servers.txt)
    FilePath = '\\Srv01\Scripts\Get-EnergyData.ps1'
    Credential = $using:Admin
    Authentication = 'CredSSP'
  }
  Invoke-Command @params
}
```

<span data-ttu-id="ee7d7-169">`$Admin`Variabeln lagrar autentiseringsuppgifter för en användare med behörighet att köra kommandona i ett **PSCredential** -objekt.</span><span class="sxs-lookup"><span data-stu-id="ee7d7-169">The `$Admin` variable stores credentials for a user with permissions to run the commands in a **PSCredential** object.</span></span> <span data-ttu-id="ee7d7-170">`$T`Variabeln lagrar jobb utlösare som skapats med `New-JobTrigger` .</span><span class="sxs-lookup"><span data-stu-id="ee7d7-170">The `$T` variable stores the job triggers created with `New-JobTrigger`.</span></span>

<span data-ttu-id="ee7d7-171">`Register-ScheduledJob`Cmdleten använder parametern **Name** för att skapa det schemalagda **CollectEnergyData** -jobbet på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="ee7d7-171">The `Register-ScheduledJob` cmdlet uses the **Name** parameter to create the **CollectEnergyData** scheduled job on the local computer.</span></span> <span data-ttu-id="ee7d7-172">Parametern **trigger** anger jobb utlösare i `$T` och parametern **MaxResultCount** ökar antalet sparade resultat till 99.</span><span class="sxs-lookup"><span data-stu-id="ee7d7-172">The **Trigger** parameter specifies the job triggers in `$T` and the **MaxResultCount** parameter increases the number of saved results to 99.</span></span>

<span data-ttu-id="ee7d7-173">Parametern **script block** definierar `Invoke-Command` parametrarna med `$params` .</span><span class="sxs-lookup"><span data-stu-id="ee7d7-173">The **ScriptBlock** parameter defines the `Invoke-Command` parameters with `$params`.</span></span> <span data-ttu-id="ee7d7-174">Parametern **AsJob** skapar objektet bakgrunds jobb på den lokala datorn, även om `Energydata.ps1` skriptet körs på fjärrdatorerna.</span><span class="sxs-lookup"><span data-stu-id="ee7d7-174">The **AsJob** parameter creates the background job object on the local computer, even though the `Energydata.ps1` script runs on the remote computers.</span></span> <span data-ttu-id="ee7d7-175">Parametern **computername** hämtar en lista över Server namn från `Servers.txt` filen.</span><span class="sxs-lookup"><span data-stu-id="ee7d7-175">The **ComputerName** parameter gets a list of server names from the `Servers.txt` file.</span></span> <span data-ttu-id="ee7d7-176">Parametern **Credential** anger ett användar konto som har behörighet att köra skript på fjärrdatorerna.</span><span class="sxs-lookup"><span data-stu-id="ee7d7-176">The **Credential** parameter specifies a user account that has permission to run scripts on the remote computers.</span></span> <span data-ttu-id="ee7d7-177">Dessutom anger parametern **Authentication** värdet **CredSSP** för att tillåta delegerade autentiseringsuppgifter.</span><span class="sxs-lookup"><span data-stu-id="ee7d7-177">And, the **Authentication** parameter specifies a value of **CredSSP** to allow delegated credentials.</span></span>

<span data-ttu-id="ee7d7-178">`Invoke-Command @params`Kör kommandot med parametrarna från skript blocket.</span><span class="sxs-lookup"><span data-stu-id="ee7d7-178">The `Invoke-Command @params` runs the command with the parameters from the script block.</span></span>

## <span data-ttu-id="ee7d7-179">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="ee7d7-179">PARAMETERS</span></span>

### <span data-ttu-id="ee7d7-180">– Argument List</span><span class="sxs-lookup"><span data-stu-id="ee7d7-180">-ArgumentList</span></span>

<span data-ttu-id="ee7d7-181">Anger värden för parametrarna i skriptet som anges av parametern **sökväg** eller för kommandot som anges av parametern **script block** .</span><span class="sxs-lookup"><span data-stu-id="ee7d7-181">Specifies values for the parameters of the script that is specified by the **FilePath** parameter or for the command that is specified by the **ScriptBlock** parameter.</span></span>

```yaml
Type: System.Object[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="ee7d7-182">-Autentisering</span><span class="sxs-lookup"><span data-stu-id="ee7d7-182">-Authentication</span></span>

<span data-ttu-id="ee7d7-183">Anger den mekanism som används för att autentisera användarens autentiseringsuppgifter.</span><span class="sxs-lookup"><span data-stu-id="ee7d7-183">Specifies the mechanism that is used to authenticate the user's credentials.</span></span> <span data-ttu-id="ee7d7-184">Standardvärdet är default.</span><span class="sxs-lookup"><span data-stu-id="ee7d7-184">The default value is Default.</span></span>

<span data-ttu-id="ee7d7-185">De acceptabla värdena för den här parametern är:</span><span class="sxs-lookup"><span data-stu-id="ee7d7-185">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="ee7d7-186">Default</span><span class="sxs-lookup"><span data-stu-id="ee7d7-186">Default</span></span>
- <span data-ttu-id="ee7d7-187">Basic</span><span class="sxs-lookup"><span data-stu-id="ee7d7-187">Basic</span></span>
- <span data-ttu-id="ee7d7-188">CredSSP</span><span class="sxs-lookup"><span data-stu-id="ee7d7-188">Credssp</span></span>
- <span data-ttu-id="ee7d7-189">Sammandrag</span><span class="sxs-lookup"><span data-stu-id="ee7d7-189">Digest</span></span>
- <span data-ttu-id="ee7d7-190">Kerberos</span><span class="sxs-lookup"><span data-stu-id="ee7d7-190">Kerberos</span></span>
- <span data-ttu-id="ee7d7-191">Negotiate</span><span class="sxs-lookup"><span data-stu-id="ee7d7-191">Negotiate</span></span>
- <span data-ttu-id="ee7d7-192">NegotiateWithImplicitCredential</span><span class="sxs-lookup"><span data-stu-id="ee7d7-192">NegotiateWithImplicitCredential</span></span>

<span data-ttu-id="ee7d7-193">Mer information om värdena för den här parametern finns i [AuthenticationMechanism](/dotnet/api/system.management.automation.runspaces.authenticationmechanism).</span><span class="sxs-lookup"><span data-stu-id="ee7d7-193">For more information about the values of this parameter, see [AuthenticationMechanism](/dotnet/api/system.management.automation.runspaces.authenticationmechanism).</span></span>

> [!CAUTION]
> <span data-ttu-id="ee7d7-194">Autentisering av Credential Security Service Provider (CredSSP), där användarens autentiseringsuppgifter skickas till en fjärrdator som ska autentiseras, är utformad för kommandon som kräver autentisering på fler än en resurs, till exempel åtkomst till en fjärran sluten nätverks resurs.</span><span class="sxs-lookup"><span data-stu-id="ee7d7-194">Credential Security Service Provider (CredSSP) authentication, in which the user's credentials are passed to a remote computer to be authenticated, is designed for commands that require authentication on more than one resource, such as accessing a remote network share.</span></span> <span data-ttu-id="ee7d7-195">Den här mekanismen ökar säkerhets risken för Fjärråtgärden.</span><span class="sxs-lookup"><span data-stu-id="ee7d7-195">This mechanism increases the security risk of the remote operation.</span></span> <span data-ttu-id="ee7d7-196">Om fjärrdatorn har komprometterats kan de autentiseringsuppgifter som skickas till den användas för att kontrol lera nätverks sessionen.</span><span class="sxs-lookup"><span data-stu-id="ee7d7-196">If the remote computer is compromised, the credentials that are passed to it can be used to control the network session.</span></span>

```yaml
Type: System.Management.Automation.Runspaces.AuthenticationMechanism
Parameter Sets: (All)
Aliases:
Accepted values: Default, Basic, Negotiate, NegotiateWithImplicitCredential, Credssp, Digest, Kerberos

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="ee7d7-197">-Confirm</span><span class="sxs-lookup"><span data-stu-id="ee7d7-197">-Confirm</span></span>

<span data-ttu-id="ee7d7-198">Uppmanar dig att bekräfta innan du kör cmdleten.</span><span class="sxs-lookup"><span data-stu-id="ee7d7-198">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="ee7d7-199">-Credential</span><span class="sxs-lookup"><span data-stu-id="ee7d7-199">-Credential</span></span>

<span data-ttu-id="ee7d7-200">Anger ett användar konto som har behörighet att köra det schemalagda jobbet.</span><span class="sxs-lookup"><span data-stu-id="ee7d7-200">Specifies a user account that has permission to run the scheduled job.</span></span> <span data-ttu-id="ee7d7-201">Standard är den aktuella användaren.</span><span class="sxs-lookup"><span data-stu-id="ee7d7-201">The default is the current user.</span></span>

<span data-ttu-id="ee7d7-202">Ange ett användar namn, till exempel **user01** eller **Domain01\User01** , eller ange ett **PSCredential** -objekt, till exempel ett från `Get-Credential` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="ee7d7-202">Type a user name, such as **User01** or **Domain01\User01** , or enter a **PSCredential** object, such as one from the `Get-Credential` cmdlet.</span></span> <span data-ttu-id="ee7d7-203">Om du bara anger ett användar namn uppmanas du att ange ett lösen ord.</span><span class="sxs-lookup"><span data-stu-id="ee7d7-203">If you enter only a user name, you're prompted for a password.</span></span>

<span data-ttu-id="ee7d7-204">Autentiseringsuppgifterna lagras i ett [PSCredential](/dotnet/api/system.management.automation.pscredential) -objekt och lösen ordet lagras som en [SecureString](/dotnet/api/system.security.securestring).</span><span class="sxs-lookup"><span data-stu-id="ee7d7-204">Credentials are stored in a [PSCredential](/dotnet/api/system.management.automation.pscredential) object and the password is stored as a [SecureString](/dotnet/api/system.security.securestring).</span></span>

> [!NOTE]
> <span data-ttu-id="ee7d7-205">Mer information om **SecureString** -data skydd finns i [hur säker är SecureString?](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span><span class="sxs-lookup"><span data-stu-id="ee7d7-205">For more information about **SecureString** data protection, see [How secure is SecureString?](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="ee7d7-206">-Sökväg</span><span class="sxs-lookup"><span data-stu-id="ee7d7-206">-FilePath</span></span>

<span data-ttu-id="ee7d7-207">Anger ett skript som det schemalagda jobbet körs på.</span><span class="sxs-lookup"><span data-stu-id="ee7d7-207">Specifies a script that the scheduled job runs.</span></span> <span data-ttu-id="ee7d7-208">Ange sökvägen till en `.ps1` fil på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="ee7d7-208">Enter the path to a `.ps1` file on the local computer.</span></span> <span data-ttu-id="ee7d7-209">Om du vill ange standardvärden för skript parametrarna använder du parametern **argument List** .</span><span class="sxs-lookup"><span data-stu-id="ee7d7-209">To specify default values for the script parameters, use the **ArgumentList** parameter.</span></span>
<span data-ttu-id="ee7d7-210">Varje `Register-ScheduledJob` kommando måste använda antingen parametrarna **script block** eller **sökväg** .</span><span class="sxs-lookup"><span data-stu-id="ee7d7-210">Every `Register-ScheduledJob` command must use either the **ScriptBlock** or **FilePath** parameters.</span></span>

```yaml
Type: System.String
Parameter Sets: FilePath
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="ee7d7-211">-InitializationScript</span><span class="sxs-lookup"><span data-stu-id="ee7d7-211">-InitializationScript</span></span>

<span data-ttu-id="ee7d7-212">Anger den fullständigt kvalificerade sökvägen till ett Windows PowerShell-skript ( `.ps1` ).</span><span class="sxs-lookup"><span data-stu-id="ee7d7-212">Specifies the fully qualified path to a Windows PowerShell script (`.ps1`).</span></span> <span data-ttu-id="ee7d7-213">Initierings skriptet körs i sessionen som skapas för bakgrunds jobbet före de kommandon som anges av parametern **script block** eller det skript som anges av parametern **sökväg** .</span><span class="sxs-lookup"><span data-stu-id="ee7d7-213">The initialization script runs in the session that is created for the background job before the commands that are specified by the **ScriptBlock** parameter or the script that is specified by the **FilePath** parameter.</span></span> <span data-ttu-id="ee7d7-214">Du kan använda initierings skriptet för att konfigurera sessionen, till exempel lägga till filer, funktioner eller alias, skapa kataloger eller kontrol lera krav.</span><span class="sxs-lookup"><span data-stu-id="ee7d7-214">You can use the initialization script to configure the session, such as adding files, functions, or aliases, creating directories, or checking for prerequisites.</span></span>

<span data-ttu-id="ee7d7-215">Om du vill ange ett skript som kör de primära jobb kommandona använder du parametern **sökväg** .</span><span class="sxs-lookup"><span data-stu-id="ee7d7-215">To specify a script that runs the primary job commands, use the **FilePath** parameter.</span></span>

<span data-ttu-id="ee7d7-216">Om initierings skriptet genererar ett fel, även ett icke-avslutande fel, körs inte den aktuella instansen av det schemalagda jobbet och dess status **misslyckades**.</span><span class="sxs-lookup"><span data-stu-id="ee7d7-216">If the initialization script generates an error, even a non-terminating error, the current instance of the scheduled job doesn't run and its status is **Failed**.</span></span>

```yaml
Type: System.Management.Automation.ScriptBlock
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="ee7d7-217">– MaxResultCount</span><span class="sxs-lookup"><span data-stu-id="ee7d7-217">-MaxResultCount</span></span>

<span data-ttu-id="ee7d7-218">Anger hur många jobb resultat poster som ska behållas för det schemalagda jobbet.</span><span class="sxs-lookup"><span data-stu-id="ee7d7-218">Specifies how many job result entries are maintained for the scheduled job.</span></span> <span data-ttu-id="ee7d7-219">Standardvärdet är 32.</span><span class="sxs-lookup"><span data-stu-id="ee7d7-219">The default value is 32.</span></span>

<span data-ttu-id="ee7d7-220">Windows PowerShell sparar körnings historiken och resultaten av varje utlöst instans av det schemalagda jobbet på disken.</span><span class="sxs-lookup"><span data-stu-id="ee7d7-220">Windows PowerShell saves the execution history and results of each triggered instance of the scheduled job on disk.</span></span> <span data-ttu-id="ee7d7-221">Värdet för den här parametern avgör antalet jobb instans resultat som sparas för det här schemalagda jobbet.</span><span class="sxs-lookup"><span data-stu-id="ee7d7-221">The value of this parameter determines the number of job instance results that are saved for this scheduled job.</span></span> <span data-ttu-id="ee7d7-222">När antalet jobb instans resultat överskrider det här värdet, tar Windows PowerShell bort resultatet från den äldsta jobb instansen för att göra plats för resultatet av den senaste jobb instansen.</span><span class="sxs-lookup"><span data-stu-id="ee7d7-222">When the number of job instance results exceeds this value, Windows PowerShell deletes the results of the oldest job instance to make room for the results of the newest job instance.</span></span>

<span data-ttu-id="ee7d7-223">Jobb körnings historiken och jobb resultaten sparas i `$home\AppData\Local\Microsoft\Windows\PowerShell\ScheduledJobs\<JobName>\Output\<Timestamp>`</span><span class="sxs-lookup"><span data-stu-id="ee7d7-223">The job execution history and job results are saved in the `$home\AppData\Local\Microsoft\Windows\PowerShell\ScheduledJobs\<JobName>\Output\<Timestamp>`</span></span>
<span data-ttu-id="ee7d7-224">kataloger på den dator där jobbet skapas.</span><span class="sxs-lookup"><span data-stu-id="ee7d7-224">directories on the computer on which the job is created.</span></span> <span data-ttu-id="ee7d7-225">Om du vill se körnings historiken använder du `Get-Job` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="ee7d7-225">To see the execution history, use the `Get-Job` cmdlet.</span></span> <span data-ttu-id="ee7d7-226">Använd cmdleten för att hämta jobb resultatet `Receive-Job` .</span><span class="sxs-lookup"><span data-stu-id="ee7d7-226">To get the job results, use the `Receive-Job` cmdlet.</span></span>

<span data-ttu-id="ee7d7-227">Parametern **MaxResultCount** anger värdet för egenskapen ExecutionHistoryLength för det schemalagda jobbet.</span><span class="sxs-lookup"><span data-stu-id="ee7d7-227">The **MaxResultCount** parameter sets the value of the ExecutionHistoryLength property of the scheduled job.</span></span>

<span data-ttu-id="ee7d7-228">Om du vill ta bort den aktuella körnings historiken och jobb resultaten använder du **ClearExecutionHistory** -parametern för `Set-ScheduledJob` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="ee7d7-228">To delete the current execution history and job results, use the **ClearExecutionHistory** parameter of the `Set-ScheduledJob` cmdlet.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 32
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="ee7d7-229">-Name</span><span class="sxs-lookup"><span data-stu-id="ee7d7-229">-Name</span></span>

<span data-ttu-id="ee7d7-230">Anger ett namn för det schemalagda jobbet.</span><span class="sxs-lookup"><span data-stu-id="ee7d7-230">Specifies a name for the scheduled job.</span></span> <span data-ttu-id="ee7d7-231">Namnet används också för alla startade instanser av det schemalagda jobbet.</span><span class="sxs-lookup"><span data-stu-id="ee7d7-231">The name is also used for all started instances of the scheduled job.</span></span> <span data-ttu-id="ee7d7-232">Namnet måste vara unikt på datorn.</span><span class="sxs-lookup"><span data-stu-id="ee7d7-232">The name must be unique on the computer.</span></span> <span data-ttu-id="ee7d7-233">Den här parametern är obligatorisk.</span><span class="sxs-lookup"><span data-stu-id="ee7d7-233">This parameter is required.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="ee7d7-234">-RunAs32</span><span class="sxs-lookup"><span data-stu-id="ee7d7-234">-RunAs32</span></span>

<span data-ttu-id="ee7d7-235">Kör det schemalagda jobbet i en 32-bitars process.</span><span class="sxs-lookup"><span data-stu-id="ee7d7-235">Runs the scheduled job in a 32-bit process.</span></span>

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

### <span data-ttu-id="ee7d7-236">-RunEvery</span><span class="sxs-lookup"><span data-stu-id="ee7d7-236">-RunEvery</span></span>

<span data-ttu-id="ee7d7-237">Används för att ange hur ofta jobbet ska köras.</span><span class="sxs-lookup"><span data-stu-id="ee7d7-237">Used to specify how often to run the job.</span></span> <span data-ttu-id="ee7d7-238">Använd exempelvis det här alternativet för att köra ett jobb var 15: e minut.</span><span class="sxs-lookup"><span data-stu-id="ee7d7-238">For example, use this option to run a job every 15 minutes.</span></span>

```yaml
Type: System.TimeSpan
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="ee7d7-239">-RunNow</span><span class="sxs-lookup"><span data-stu-id="ee7d7-239">-RunNow</span></span>

<span data-ttu-id="ee7d7-240">Startar ett jobb omedelbart så fort `Register-ScheduledJob` cmdleten körs.</span><span class="sxs-lookup"><span data-stu-id="ee7d7-240">Starts a job immediately, as soon as the `Register-ScheduledJob` cmdlet is run.</span></span> <span data-ttu-id="ee7d7-241">Den här parametern eliminerar behovet av att utlösa Schemaläggaren för att köra ett Windows PowerShell-skript direkt efter registreringen och kräver inte att användare skapar en utlösare som anger start datum och start tid.</span><span class="sxs-lookup"><span data-stu-id="ee7d7-241">This parameter eliminates the need to trigger Task Scheduler to run a Windows PowerShell script immediately after registration, and doesn't require users to create a trigger that specifies a starting date and time.</span></span>

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

### <span data-ttu-id="ee7d7-242">-ScheduledJobOption</span><span class="sxs-lookup"><span data-stu-id="ee7d7-242">-ScheduledJobOption</span></span>

<span data-ttu-id="ee7d7-243">Anger alternativ för det schemalagda jobbet.</span><span class="sxs-lookup"><span data-stu-id="ee7d7-243">Sets options for the scheduled job.</span></span> <span data-ttu-id="ee7d7-244">Ange ett **ScheduledJobOptions** -objekt, till exempel ett som du skapar med hjälp av `New-ScheduledJobOption` cmdleten eller ett värde för hash-tabellen.</span><span class="sxs-lookup"><span data-stu-id="ee7d7-244">Enter a **ScheduledJobOptions** object, such as one that you create by using the `New-ScheduledJobOption` cmdlet, or a hash table value.</span></span>

<span data-ttu-id="ee7d7-245">Du kan ange alternativ för ett schemalagt jobb när du registrerar schema jobbet eller använda `Set-ScheduledJobOption` `Set-ScheduledJob` cmdletarna eller för att ändra alternativen.</span><span class="sxs-lookup"><span data-stu-id="ee7d7-245">You can set options for a scheduled job when you register the schedule job or use the `Set-ScheduledJobOption` or `Set-ScheduledJob` cmdlets to change the options.</span></span>

<span data-ttu-id="ee7d7-246">Många av alternativen och deras standardvärden avgör om och när ett schemalagt jobb körs.</span><span class="sxs-lookup"><span data-stu-id="ee7d7-246">Many of the options and their default values determine whether and when a scheduled job runs.</span></span> <span data-ttu-id="ee7d7-247">Se till att granska de här alternativen innan du schemalägger ett jobb.</span><span class="sxs-lookup"><span data-stu-id="ee7d7-247">Be sure to review these options before scheduling a job.</span></span> <span data-ttu-id="ee7d7-248">En beskrivning av de schemalagda jobb alternativen, inklusive standardvärdena, finns i `New-ScheduledJobOption` .</span><span class="sxs-lookup"><span data-stu-id="ee7d7-248">For a description of the scheduled job options, including the default values, see `New-ScheduledJobOption`.</span></span>

<span data-ttu-id="ee7d7-249">Om du vill skicka en hash-tabell använder du följande nycklar.</span><span class="sxs-lookup"><span data-stu-id="ee7d7-249">To submit a hash table, use the following keys.</span></span> <span data-ttu-id="ee7d7-250">I följande hash-tabell visas nycklarna med standardvärdena.</span><span class="sxs-lookup"><span data-stu-id="ee7d7-250">In the following hash table, the keys are shown with their default values.</span></span>

`@{StartIfOnBattery=$False; StopIfGoingOnBattery=$True; WakeToRun=$False; StartIfNotIdle=$False; IdleDuration="00:10:00"; IdleTimeout="01:00:00"; StopIfGoingOffIdle=$True; RestartOnIdleResume=$False; ShowInTaskScheduler=$True; RunElevated=$False; RunWithoutNetwork=$False; DoNotAllowDemandStart=$False; MultipleInstancePolicy="IgnoreNew"}`

```yaml
Type: Microsoft.PowerShell.ScheduledJob.ScheduledJobOptions
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="ee7d7-251">– Script block</span><span class="sxs-lookup"><span data-stu-id="ee7d7-251">-ScriptBlock</span></span>

<span data-ttu-id="ee7d7-252">Anger de kommandon som det schemalagda jobbet körs på.</span><span class="sxs-lookup"><span data-stu-id="ee7d7-252">Specifies the commands that the scheduled job runs.</span></span> <span data-ttu-id="ee7d7-253">Omge kommandoen med klammerparenteser ( `{}` ) för att skapa ett skript block.</span><span class="sxs-lookup"><span data-stu-id="ee7d7-253">Enclose the commands in curly braces (`{}`) to create a script block.</span></span> <span data-ttu-id="ee7d7-254">Om du vill ange standardvärden för kommando parametrar använder du parametern **argument List** .</span><span class="sxs-lookup"><span data-stu-id="ee7d7-254">To specify default values for command parameters, use the **ArgumentList** parameter.</span></span>

<span data-ttu-id="ee7d7-255">Varje `Register-ScheduledJob` kommando måste använda antingen parametrarna **script block** eller **sökväg** .</span><span class="sxs-lookup"><span data-stu-id="ee7d7-255">Every `Register-ScheduledJob` command must use either the **ScriptBlock** or **FilePath** parameters.</span></span>

```yaml
Type: System.Management.Automation.ScriptBlock
Parameter Sets: ScriptBlock
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="ee7d7-256">– Utlös</span><span class="sxs-lookup"><span data-stu-id="ee7d7-256">-Trigger</span></span>

<span data-ttu-id="ee7d7-257">Anger utlösare för det schemalagda jobbet.</span><span class="sxs-lookup"><span data-stu-id="ee7d7-257">Specifies the triggers for the scheduled job.</span></span> <span data-ttu-id="ee7d7-258">Ange ett eller flera **ScheduledJobTrigger** -objekt, till exempel de objekt som `New-JobTrigger` cmdleten returnerar eller en hash-tabell för jobb utlöser nycklar och värden.</span><span class="sxs-lookup"><span data-stu-id="ee7d7-258">Enter one or more **ScheduledJobTrigger** objects, such as the objects that the `New-JobTrigger` cmdlet returns, or a hash table of job trigger keys and values.</span></span>

<span data-ttu-id="ee7d7-259">En jobb utlösare startar schema jobbet.</span><span class="sxs-lookup"><span data-stu-id="ee7d7-259">A job trigger starts the schedule job.</span></span> <span data-ttu-id="ee7d7-260">Utlösaren kan ange en enstaka eller återkommande schemalagd eller en händelse, till exempel när en användare loggar in eller Windows startas.</span><span class="sxs-lookup"><span data-stu-id="ee7d7-260">The trigger can specify a one-time or recurring scheduled or an event, such as when a user logs on or Windows starts.</span></span>

<span data-ttu-id="ee7d7-261">**Utlösar** parametern är valfri.</span><span class="sxs-lookup"><span data-stu-id="ee7d7-261">The **Trigger** parameter is optional.</span></span> <span data-ttu-id="ee7d7-262">Du kan lägga till en utlösare när du skapar det schemalagda jobbet, använda `Add-JobTrigger` `Set-JobTrigger` `Set-ScheduledJob` cmdletarna, eller för att lägga till eller ändra jobb utlösare senare, eller använda `Start-Job` cmdleten för att starta det schemalagda jobbet omedelbart.</span><span class="sxs-lookup"><span data-stu-id="ee7d7-262">You can add a trigger when you create the scheduled job, use the `Add-JobTrigger`, `Set-JobTrigger`, or `Set-ScheduledJob` cmdlets to add or change job triggers later, or use the `Start-Job` cmdlet to start the scheduled job immediately.</span></span> <span data-ttu-id="ee7d7-263">Du kan också skapa och underhålla ett schemalagt jobb utan en utlösare som används som mall.</span><span class="sxs-lookup"><span data-stu-id="ee7d7-263">You can also create and maintain a scheduled job without a trigger that is used as a template.</span></span>

<span data-ttu-id="ee7d7-264">Om du vill skicka en hash-tabell använder du följande nycklar:</span><span class="sxs-lookup"><span data-stu-id="ee7d7-264">To submit a hash table, use the following keys:</span></span>

- <span data-ttu-id="ee7d7-265">**Frekvens** : varje dag, varje vecka, AtStartup, AtLogon</span><span class="sxs-lookup"><span data-stu-id="ee7d7-265">**Frequency** : Daily, Weekly, AtStartup, AtLogon</span></span>
- <span data-ttu-id="ee7d7-266">**Vid** : en giltig tids sträng</span><span class="sxs-lookup"><span data-stu-id="ee7d7-266">**At** : Any valid time string</span></span>
- <span data-ttu-id="ee7d7-267">**DaysOfWeek** – valfri kombination av dag namn</span><span class="sxs-lookup"><span data-stu-id="ee7d7-267">**DaysOfWeek** - Any combination of day names</span></span>
- <span data-ttu-id="ee7d7-268">**Intervall** – valfritt giltigt frekvens intervall</span><span class="sxs-lookup"><span data-stu-id="ee7d7-268">**Interval** - Any valid frequency interval</span></span>
- <span data-ttu-id="ee7d7-269">**RandomDelay** : en giltig TimeSpan-sträng</span><span class="sxs-lookup"><span data-stu-id="ee7d7-269">**RandomDelay** : Any valid timespan string</span></span>
- <span data-ttu-id="ee7d7-270">**Användare** : en giltig användare.</span><span class="sxs-lookup"><span data-stu-id="ee7d7-270">**User** : Any valid user.</span></span> <span data-ttu-id="ee7d7-271">Används endast med AtLogon-frekvens svärdet</span><span class="sxs-lookup"><span data-stu-id="ee7d7-271">Used only with the AtLogon frequency value</span></span>

<span data-ttu-id="ee7d7-272">Ett exempel:</span><span class="sxs-lookup"><span data-stu-id="ee7d7-272">For example:</span></span>

`@{Frequency="Once"; At="3am"; DaysOfWeek="Monday", "Wednesday"; Interval=2; RandomDelay="30minutes"; User="Domain1\User01"}`

```yaml
Type: Microsoft.PowerShell.ScheduledJob.ScheduledJobTrigger[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="ee7d7-273">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="ee7d7-273">-WhatIf</span></span>

<span data-ttu-id="ee7d7-274">Visar vad som skulle hända om cmdleten kördes.</span><span class="sxs-lookup"><span data-stu-id="ee7d7-274">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="ee7d7-275">Cmdleten körs inte.</span><span class="sxs-lookup"><span data-stu-id="ee7d7-275">The cmdlet isn't run.</span></span>

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

### <span data-ttu-id="ee7d7-276">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="ee7d7-276">CommonParameters</span></span>

<span data-ttu-id="ee7d7-277">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="ee7d7-277">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="ee7d7-278">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="ee7d7-278">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="ee7d7-279">INDATA</span><span class="sxs-lookup"><span data-stu-id="ee7d7-279">INPUTS</span></span>

### <span data-ttu-id="ee7d7-280">Inget</span><span class="sxs-lookup"><span data-stu-id="ee7d7-280">None</span></span>

<span data-ttu-id="ee7d7-281">Du kan inte skicka inmatade pipelines till denna cmdlet.</span><span class="sxs-lookup"><span data-stu-id="ee7d7-281">You can't send input down the pipeline to this cmdlet.</span></span>

## <span data-ttu-id="ee7d7-282">UTDATA</span><span class="sxs-lookup"><span data-stu-id="ee7d7-282">OUTPUTS</span></span>

### <span data-ttu-id="ee7d7-283">Microsoft. PowerShell. ScheduledJob. ScheduledJobDefinition</span><span class="sxs-lookup"><span data-stu-id="ee7d7-283">Microsoft.PowerShell.ScheduledJob.ScheduledJobDefinition</span></span>

## <span data-ttu-id="ee7d7-284">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="ee7d7-284">NOTES</span></span>

<span data-ttu-id="ee7d7-285">Varje schemalagt jobb sparas i en under katalog till `$home\AppData\Local\Microsoft\Windows\PowerShell\ScheduledJobs` katalogen på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="ee7d7-285">Each scheduled job is saved in a subdirectory of the `$home\AppData\Local\Microsoft\Windows\PowerShell\ScheduledJobs` directory on the local computer.</span></span>
<span data-ttu-id="ee7d7-286">Under katalogen är namngiven för det schemalagda jobbet och innehåller en XML-fil för det schemalagda jobbet och poster i körnings historiken.</span><span class="sxs-lookup"><span data-stu-id="ee7d7-286">The subdirectory is named for the scheduled job and contains an XML file for the scheduled job and records of its execution history.</span></span> <span data-ttu-id="ee7d7-287">Mer information om schemalagda jobb på disk finns [about_Scheduled_Jobs_Advanced](./about/about_scheduled_jobs_advanced.md).</span><span class="sxs-lookup"><span data-stu-id="ee7d7-287">For more information about scheduled jobs on disk, see [about_Scheduled_Jobs_Advanced](./about/about_scheduled_jobs_advanced.md).</span></span>

<span data-ttu-id="ee7d7-288">Schemalagda jobb som du skapar i Windows PowerShell visas i Schemaläggaren i mappen Schemaläggaren `Library\Microsoft\Windows\PowerShell\ScheduledJobs` .</span><span class="sxs-lookup"><span data-stu-id="ee7d7-288">Scheduled jobs that you create in Windows PowerShell appear in Task Scheduler in the Task Scheduler `Library\Microsoft\Windows\PowerShell\ScheduledJobs` folder.</span></span> <span data-ttu-id="ee7d7-289">Du kan använda Schemaläggaren för att visa och redigera det schemalagda jobbet.</span><span class="sxs-lookup"><span data-stu-id="ee7d7-289">You can use Task Scheduler to view and edit the scheduled job.</span></span>

<span data-ttu-id="ee7d7-290">Du kan använda Schemaläggaren, **schtasks.exe** kommando rads verktyget och Schemaläggaren-cmdletar för att hantera schemalagda jobb som du skapar med de schemalagda jobb-cmdletarna.</span><span class="sxs-lookup"><span data-stu-id="ee7d7-290">You can use Task Scheduler, the **schtasks.exe** command-line tool, and the Task Scheduler cmdlets to manage scheduled jobs that you create with the Scheduled Job cmdlets.</span></span> <span data-ttu-id="ee7d7-291">Du kan dock inte använda de schemalagda jobb-cmdletarna för att hantera aktiviteter som du skapar i Schemaläggaren.</span><span class="sxs-lookup"><span data-stu-id="ee7d7-291">However, you can't use the Scheduled Job cmdlets to manage tasks that you create in Task Scheduler.</span></span>

<span data-ttu-id="ee7d7-292">Om ett schemalagt jobb-kommando Miss lyckas, returnerar Windows PowerShell ett fel meddelande.</span><span class="sxs-lookup"><span data-stu-id="ee7d7-292">If a scheduled job command fails, Windows PowerShell returns an error message.</span></span> <span data-ttu-id="ee7d7-293">Men om jobbet Miss lyckas när Schemaläggaren försöker köra det, är felet inte tillgängligt för Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ee7d7-293">However, if the job fails when Task Scheduler tries to run it, the error isn't available to Windows PowerShell.</span></span>

<span data-ttu-id="ee7d7-294">Om ett schemalagt jobb inte körs kan du använda följande metoder för att hitta orsaken:</span><span class="sxs-lookup"><span data-stu-id="ee7d7-294">If a scheduled job doesn't run, use the following methods to find the reason:</span></span>

- <span data-ttu-id="ee7d7-295">Kontrol lera att jobb utlösaren är korrekt inställd.</span><span class="sxs-lookup"><span data-stu-id="ee7d7-295">Verify that the job trigger is set properly.</span></span>
  - <span data-ttu-id="ee7d7-296">Kontrol lera att villkoren som anges i jobb alternativen är uppfyllda.</span><span class="sxs-lookup"><span data-stu-id="ee7d7-296">Verify that the conditions set in the job options are satisfied.</span></span>
- <span data-ttu-id="ee7d7-297">Kontrol lera att användar kontot som jobbet körs under har behörighet att köra kommandona eller skripten i jobbet.</span><span class="sxs-lookup"><span data-stu-id="ee7d7-297">Verify that the user account under which the job runs has permission to run the commands or scripts in the job.</span></span>
- <span data-ttu-id="ee7d7-298">Kontrol lera om det finns fel i Schemaläggarens historik.</span><span class="sxs-lookup"><span data-stu-id="ee7d7-298">Check the Task Scheduler history for errors.</span></span>
- <span data-ttu-id="ee7d7-299">Kontrol lera om det finns fel i händelse loggen för Schemaläggaren.</span><span class="sxs-lookup"><span data-stu-id="ee7d7-299">Check the Task Scheduler event log for errors.</span></span>

<span data-ttu-id="ee7d7-300">Mer information finns i [about_Scheduled_Jobs_Troubleshooting](./about/about_scheduled_jobs_troubleshooting.md).</span><span class="sxs-lookup"><span data-stu-id="ee7d7-300">For more information, see [about_Scheduled_Jobs_Troubleshooting](./about/about_scheduled_jobs_troubleshooting.md).</span></span>

## <span data-ttu-id="ee7d7-301">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="ee7d7-301">RELATED LINKS</span></span>

[<span data-ttu-id="ee7d7-302">Add-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="ee7d7-302">Add-JobTrigger</span></span>](Add-JobTrigger.md)

[<span data-ttu-id="ee7d7-303">Disable-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="ee7d7-303">Disable-JobTrigger</span></span>](Disable-JobTrigger.md)

[<span data-ttu-id="ee7d7-304">Disable-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="ee7d7-304">Disable-ScheduledJob</span></span>](Disable-ScheduledJob.md)

[<span data-ttu-id="ee7d7-305">Aktivera – JobTrigger</span><span class="sxs-lookup"><span data-stu-id="ee7d7-305">Enable-JobTrigger</span></span>](Enable-JobTrigger.md)

[<span data-ttu-id="ee7d7-306">Aktivera – ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="ee7d7-306">Enable-ScheduledJob</span></span>](Enable-ScheduledJob.md)

[<span data-ttu-id="ee7d7-307">Get-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="ee7d7-307">Get-JobTrigger</span></span>](Get-JobTrigger.md)

[<span data-ttu-id="ee7d7-308">Get-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="ee7d7-308">Get-ScheduledJob</span></span>](Get-ScheduledJob.md)

[<span data-ttu-id="ee7d7-309">Get-ScheduledJobOption</span><span class="sxs-lookup"><span data-stu-id="ee7d7-309">Get-ScheduledJobOption</span></span>](Get-ScheduledJobOption.md)

[<span data-ttu-id="ee7d7-310">New-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="ee7d7-310">New-JobTrigger</span></span>](New-JobTrigger.md)

[<span data-ttu-id="ee7d7-311">New-ScheduledJobOption</span><span class="sxs-lookup"><span data-stu-id="ee7d7-311">New-ScheduledJobOption</span></span>](New-ScheduledJobOption.md)

[<span data-ttu-id="ee7d7-312">Registrera – ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="ee7d7-312">Register-ScheduledJob</span></span>](Register-ScheduledJob.md)

[<span data-ttu-id="ee7d7-313">Remove-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="ee7d7-313">Remove-JobTrigger</span></span>](Remove-JobTrigger.md)

[<span data-ttu-id="ee7d7-314">Set-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="ee7d7-314">Set-JobTrigger</span></span>](Set-JobTrigger.md)

[<span data-ttu-id="ee7d7-315">Set-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="ee7d7-315">Set-ScheduledJob</span></span>](Set-ScheduledJob.md)

[<span data-ttu-id="ee7d7-316">Set-ScheduledJobOption</span><span class="sxs-lookup"><span data-stu-id="ee7d7-316">Set-ScheduledJobOption</span></span>](Set-ScheduledJobOption.md)

[<span data-ttu-id="ee7d7-317">Avregistrera-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="ee7d7-317">Unregister-ScheduledJob</span></span>](Unregister-ScheduledJob.md)
