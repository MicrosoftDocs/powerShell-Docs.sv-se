---
external help file: Microsoft.PowerShell.ScheduledJob.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSScheduledJob
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psscheduledjob/set-scheduledjob?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-ScheduledJob
ms.openlocfilehash: 99dbdc84430c0a8b5cf505a22b139cd07236e160
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93264603"
---
# <span data-ttu-id="15813-103">Set-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="15813-103">Set-ScheduledJob</span></span>

## <span data-ttu-id="15813-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="15813-104">SYNOPSIS</span></span>
<span data-ttu-id="15813-105">Ändrar schemalagda jobb.</span><span class="sxs-lookup"><span data-stu-id="15813-105">Changes scheduled jobs.</span></span>

## <span data-ttu-id="15813-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="15813-106">SYNTAX</span></span>

### <span data-ttu-id="15813-107">Script block (standard)</span><span class="sxs-lookup"><span data-stu-id="15813-107">ScriptBlock (Default)</span></span>

```
Set-ScheduledJob [-Name <String>] [-ScriptBlock <ScriptBlock>] [-Trigger <ScheduledJobTrigger[]>]
 [-InitializationScript <ScriptBlock>] [-RunAs32] [-Credential <PSCredential>]
 [-Authentication <AuthenticationMechanism>] [-ScheduledJobOption <ScheduledJobOptions>]
 [-InputObject] <ScheduledJobDefinition> [-MaxResultCount <Int32>] [-PassThru] [-ArgumentList <Object[]>]
 [-RunNow] [-RunEvery <TimeSpan>] [<CommonParameters>]
```

### <span data-ttu-id="15813-108">FilePath</span><span class="sxs-lookup"><span data-stu-id="15813-108">FilePath</span></span>

```
Set-ScheduledJob [-Name <String>] [-FilePath <String>] [-Trigger <ScheduledJobTrigger[]>]
 [-InitializationScript <ScriptBlock>] [-RunAs32] [-Credential <PSCredential>]
 [-Authentication <AuthenticationMechanism>] [-ScheduledJobOption <ScheduledJobOptions>]
 [-InputObject] <ScheduledJobDefinition> [-MaxResultCount <Int32>] [-PassThru] [-ArgumentList <Object[]>]
 [-RunNow] [-RunEvery <TimeSpan>] [<CommonParameters>]
```

### <span data-ttu-id="15813-109">Körnings-</span><span class="sxs-lookup"><span data-stu-id="15813-109">Execution</span></span>

```
Set-ScheduledJob [-InputObject] <ScheduledJobDefinition> [-ClearExecutionHistory] [-PassThru]
 [<CommonParameters>]
```

## <span data-ttu-id="15813-110">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="15813-110">DESCRIPTION</span></span>
<span data-ttu-id="15813-111">Cmdlet: en **set-ScheduledJob** ändrar egenskaperna för schemalagda jobb, till exempel de kommandon som jobben kör eller de autentiseringsuppgifter som krävs för att köra jobbet.</span><span class="sxs-lookup"><span data-stu-id="15813-111">The **Set-ScheduledJob** cmdlet changes the properties of scheduled jobs, such as the commands that the jobs run or the credentials required to run the job.</span></span>
<span data-ttu-id="15813-112">Du kan också använda den för att rensa körnings historiken för det schemalagda jobbet.</span><span class="sxs-lookup"><span data-stu-id="15813-112">You can also use it to clear the execution history of the scheduled job.</span></span>

<span data-ttu-id="15813-113">Om du vill använda denna cmdlet börjar du med att använda Get-ScheduledJob cmdlet för att hämta det schemalagda jobbet.</span><span class="sxs-lookup"><span data-stu-id="15813-113">To use this cmdlet, begin by using the Get-ScheduledJob cmdlet to get the scheduled job.</span></span>
<span data-ttu-id="15813-114">Skicka sedan det schemalagda jobbet till **set-ScheduledJob** eller spara jobbet i en variabel och Använd parametern *InputObject* för att identifiera jobbet.</span><span class="sxs-lookup"><span data-stu-id="15813-114">Then, pipe the scheduled job to **Set-ScheduledJob** or save the job in a variable and use the *InputObject* parameter to identify the job.</span></span>
<span data-ttu-id="15813-115">Använd de återstående parametrarna för **set-ScheduledJob** för att ändra jobb egenskaperna eller rensa körnings historiken.</span><span class="sxs-lookup"><span data-stu-id="15813-115">Use the remaining parameters of **Set-ScheduledJob** to change the job properties or clear the execution history.</span></span>

<span data-ttu-id="15813-116">Även om du kan använda **set-ScheduledJob** för att ändra utlösare och alternativ för ett schemalagt jobb, ger cmdletarna Add-JobTrigger, set-JobTrigger och Set-ScheduledJobOption ett mycket enklare sätt att utföra dessa uppgifter.</span><span class="sxs-lookup"><span data-stu-id="15813-116">Although you can use **Set-ScheduledJob** to change the triggers and options of a scheduled job, the Add-JobTrigger, Set-JobTrigger, and Set-ScheduledJobOption cmdlets provide much easier ways to accomplish those tasks.</span></span>
<span data-ttu-id="15813-117">Använd Register-ScheduledJob-cmdleten om du vill skapa ett nytt schemalagt jobb.</span><span class="sxs-lookup"><span data-stu-id="15813-117">To create a new scheduled job, use the Register-ScheduledJob cmdlet.</span></span>

<span data-ttu-id="15813-118">*Utlösar* -parametern för **set-ScheduledJob** lägger till en eller flera jobb utlösare som startar jobbet.</span><span class="sxs-lookup"><span data-stu-id="15813-118">The *Trigger* parameter of **Set-ScheduledJob** adds one or more job triggers that start the job.</span></span>
<span data-ttu-id="15813-119">*Utlösar* -parametern är valfri, så du kan lägga till utlösare när du skapar det schemalagda jobbet, lägga till jobb utlösare senare, lägga till parametern *RunNow* för att starta jobbet omedelbart, använda Start-Job cmdlet för att starta jobbet omedelbart när som helst, eller spara det ej utlösta schemalagda jobbet som en mall för andra jobb.</span><span class="sxs-lookup"><span data-stu-id="15813-119">The *Trigger* parameter is optional, so you can add triggers when you create the scheduled job, add job triggers later, add the *RunNow* parameter to start the job immediately, use the Start-Job cmdlet to start the job immediately at any time, or save the untriggered scheduled job as a template for other jobs.</span></span>

<span data-ttu-id="15813-120">**Set-ScheduledJob** är en samling jobb schemaläggnings-cmdletar i PSScheduledJob-modulen som ingår i Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="15813-120">**Set-ScheduledJob** is one of a collection of job scheduling cmdlets in the PSScheduledJob module that is included in Windows PowerShell.</span></span>

<span data-ttu-id="15813-121">Mer information om schemalagda jobb finns i avsnittet om ämnen i PSScheduledJob-modulen.</span><span class="sxs-lookup"><span data-stu-id="15813-121">For more information about Scheduled Jobs, see the About topics in the PSScheduledJob module.</span></span>
<span data-ttu-id="15813-122">Importera modulen PSScheduledJob och skriv sedan: `Get-Help about_Scheduled*` eller se about_Scheduled_Jobs.</span><span class="sxs-lookup"><span data-stu-id="15813-122">Import the PSScheduledJob module and then type: `Get-Help about_Scheduled*` or see about_Scheduled_Jobs.</span></span>

<span data-ttu-id="15813-123">Den här cmdleten introducerades i Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="15813-123">This cmdlet was introduced in Windows PowerShell 3.0.</span></span>

## <span data-ttu-id="15813-124">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="15813-124">EXAMPLES</span></span>

### <span data-ttu-id="15813-125">Exempel 1: ändra det skript som ett jobb kör</span><span class="sxs-lookup"><span data-stu-id="15813-125">Example 1: Change the script that a job runs</span></span>

```
PS C:\> Get-ScheduledJob -Name "Inventory"
Id         Name            Triggers        Command                                  Enabled
--         ----            --------        -------                                  -------
1          Inventory       {1}             C:\Scripts\Get-Inventory.ps1             True

The second command uses the Get-ScheduledJob cmdlet to get the Inventory scheduled job. A pipeline operator (|) sends the scheduled job to the **Set-ScheduledJob** cmdlet. The **Set-ScheduledJob** cmdlet uses the *Script* parameter to specify a new script, Get-FullInventory.ps1. The command uses the *Passthru* parameter to return the scheduled job after the change.
PS C:\> Get-ScheduledJob -Name "Inventory" | Set-ScheduledJob -FilePath "C:\Scripts\Get-FullInventory.ps1" -Passthru
Id         Name            Triggers        Command                                  Enabled
--         ----            --------        -------                                  -------
1          Inventory       {1}             C:\Scripts\Get-FullInventory.ps1         True
```

<span data-ttu-id="15813-126">Det här exemplet visar hur du ändrar det skript som körs i ett schemalagt jobb.</span><span class="sxs-lookup"><span data-stu-id="15813-126">This example shows how to change the script that is run in a scheduled job.</span></span>

<span data-ttu-id="15813-127">Det första kommandot använder Get-ScheduledJob-cmdlet för att hämta det schemalagda jobbet för lager.</span><span class="sxs-lookup"><span data-stu-id="15813-127">The first command uses the Get-ScheduledJob cmdlet to get the Inventory scheduled job.</span></span>
<span data-ttu-id="15813-128">Utdata visar att jobbet kör Get-Inventory.ps1-skriptet.</span><span class="sxs-lookup"><span data-stu-id="15813-128">The output shows that the job runs the Get-Inventory.ps1 script.</span></span>

<span data-ttu-id="15813-129">Det här kommandot krävs inte. den ingår bara för att Visa effekterna av skript ändringen.</span><span class="sxs-lookup"><span data-stu-id="15813-129">This command is not required; it is included only to show the effect of the script change.</span></span>

### <span data-ttu-id="15813-130">Exempel 2: ta bort körnings historiken för ett schemalagt jobb</span><span class="sxs-lookup"><span data-stu-id="15813-130">Example 2: Delete the execution history of a scheduled job</span></span>

```
PS C:\> Get-ScheduledJob BackupArchive | Set-ScheduledJob -ClearExecutionHistory
```

<span data-ttu-id="15813-131">Det här kommandot tar bort den aktuella körnings historiken och de sparade jobb resultaten för det schemalagda BackupArchive-jobbet.</span><span class="sxs-lookup"><span data-stu-id="15813-131">This command deletes the current execution history and saved job results for the BackupArchive scheduled job.</span></span>

<span data-ttu-id="15813-132">Kommandot använder Get-ScheduledJob-cmdlet för att hämta det schemalagda BackupArchive-jobbet.</span><span class="sxs-lookup"><span data-stu-id="15813-132">The command uses the Get-ScheduledJob cmdlet to get the BackupArchive scheduled job.</span></span>
<span data-ttu-id="15813-133">En pipeline-operator (|) skickar jobbet till **set-ScheduledJob** -cmdlet: en för att ändra det.</span><span class="sxs-lookup"><span data-stu-id="15813-133">A pipeline operator (|) sends the job to the **Set-ScheduledJob** cmdlet to change it.</span></span>
<span data-ttu-id="15813-134">Cmdlet **: en Set-ScheduledJob** använder parametern *ClearExecutionHistory* för att ta bort körnings historiken och de sparade resultaten.</span><span class="sxs-lookup"><span data-stu-id="15813-134">The **Set-ScheduledJob** cmdlet uses the *ClearExecutionHistory* parameter to delete the execution history and saved results.</span></span>

<span data-ttu-id="15813-135">Mer information om körnings historik och sparade jobb resultat för schemalagda jobb finns about_Scheduled_Jobs.</span><span class="sxs-lookup"><span data-stu-id="15813-135">For more information about the execution history and saved job results of scheduled jobs, see about_Scheduled_Jobs.</span></span>

### <span data-ttu-id="15813-136">Exempel 3: ändra schemalagda jobb på en fjärrdator</span><span class="sxs-lookup"><span data-stu-id="15813-136">Example 3: Change scheduled jobs on a remote computer</span></span>

```
PS C:\> Invoke-Command -Computer "Server01, Server02" -ScriptBlock {Get-ScheduledJob | Set-ScheduledJob -InitializationScript \\SrvA\Scripts\SetForRun.ps1}
```

<span data-ttu-id="15813-137">Det här kommandot ändrar initierings skriptet i alla schemalagda jobb på Server01-och Server02-datorerna.</span><span class="sxs-lookup"><span data-stu-id="15813-137">This command changes the initialization script in all scheduled jobs on the Server01 and Server02 computers.</span></span>

<span data-ttu-id="15813-138">Kommandot använder cmdleten Invoke-Command för att köra ett kommando på Server01-och Server02-datorerna.</span><span class="sxs-lookup"><span data-stu-id="15813-138">The command uses the Invoke-Command cmdlet to run a command on the Server01 and Server02 computers.</span></span>

<span data-ttu-id="15813-139">Fjärrkommandot börjar med ett Get-ScheduledJob-kommando som hämtar alla schemalagda jobb på datorn.</span><span class="sxs-lookup"><span data-stu-id="15813-139">The remote command begins with a Get-ScheduledJob command that gets all scheduled jobs on the computer.</span></span>
<span data-ttu-id="15813-140">De schemalagda jobben är skickas till cmdleten **set-ScheduledJob** , som ändrar initierings skriptet till SetForRun.ps1.</span><span class="sxs-lookup"><span data-stu-id="15813-140">The scheduled jobs are piped to the **Set-ScheduledJob** cmdlet, which changes the initialization script to SetForRun.ps1.</span></span>

## <span data-ttu-id="15813-141">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="15813-141">PARAMETERS</span></span>

### <span data-ttu-id="15813-142">– Argument List</span><span class="sxs-lookup"><span data-stu-id="15813-142">-ArgumentList</span></span>
<span data-ttu-id="15813-143">Anger värden för parametrarna i skriptet som anges av parametern *sökväg* eller för kommandot som anges av parametern *script block* .</span><span class="sxs-lookup"><span data-stu-id="15813-143">Specifies values for the parameters of the script that is specified by the *FilePath* parameter or for the command that is specified by the *ScriptBlock* parameter.</span></span>

```yaml
Type: System.Object[]
Parameter Sets: ScriptBlock, FilePath
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="15813-144">-Autentisering</span><span class="sxs-lookup"><span data-stu-id="15813-144">-Authentication</span></span>
<span data-ttu-id="15813-145">Anger den mekanism som används för att autentisera användarens autentiseringsuppgifter.</span><span class="sxs-lookup"><span data-stu-id="15813-145">Specifies the mechanism that is used to authenticate the user's credentials.</span></span>
<span data-ttu-id="15813-146">De acceptabla värdena för den här parametern är:</span><span class="sxs-lookup"><span data-stu-id="15813-146">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="15813-147">Default</span><span class="sxs-lookup"><span data-stu-id="15813-147">Default</span></span>
- <span data-ttu-id="15813-148">Basic</span><span class="sxs-lookup"><span data-stu-id="15813-148">Basic</span></span>
- <span data-ttu-id="15813-149">CredSSP</span><span class="sxs-lookup"><span data-stu-id="15813-149">Credssp</span></span>
- <span data-ttu-id="15813-150">Sammandrag</span><span class="sxs-lookup"><span data-stu-id="15813-150">Digest</span></span>
- <span data-ttu-id="15813-151">Kerberos</span><span class="sxs-lookup"><span data-stu-id="15813-151">Kerberos</span></span>
- <span data-ttu-id="15813-152">Negotiate</span><span class="sxs-lookup"><span data-stu-id="15813-152">Negotiate</span></span>
- <span data-ttu-id="15813-153">NegotiateWithImplicitCredential</span><span class="sxs-lookup"><span data-stu-id="15813-153">NegotiateWithImplicitCredential</span></span>

<span data-ttu-id="15813-154">Standardvärdet är default.</span><span class="sxs-lookup"><span data-stu-id="15813-154">The default value is Default.</span></span>
<span data-ttu-id="15813-155">Mer information om värdena för den här parametern finns i [AuthenticationMechanism-uppräkning](https://msdn.microsoft.com/library/system.management.automation.runspaces.authenticationmechanism) i MSDN-biblioteket.</span><span class="sxs-lookup"><span data-stu-id="15813-155">For more information about the values of this parameter, see [AuthenticationMechanism Enumeration](https://msdn.microsoft.com/library/system.management.automation.runspaces.authenticationmechanism) in the MSDN library.</span></span>

<span data-ttu-id="15813-156">Varning! CredSSP-autentisering (Credential Security Support Provider), där användarens autentiseringsuppgifter skickas till en fjärrdator som ska autentiseras, är utformad för kommandon som kräver autentisering på fler än en resurs, till exempel åtkomst till en fjärran sluten nätverks resurs.</span><span class="sxs-lookup"><span data-stu-id="15813-156">Caution: Credential Security Support Provider (CredSSP) authentication, in which the user's credentials are passed to a remote computer to be authenticated, is designed for commands that require authentication on more than one resource, such as accessing a remote network share.</span></span>
<span data-ttu-id="15813-157">Den här mekanismen ökar säkerhets risken för Fjärråtgärden.</span><span class="sxs-lookup"><span data-stu-id="15813-157">This mechanism increases the security risk of the remote operation.</span></span>
<span data-ttu-id="15813-158">Om fjärrdatorn har komprometterats kan de autentiseringsuppgifter som skickas till den användas för att kontrol lera nätverks sessionen.</span><span class="sxs-lookup"><span data-stu-id="15813-158">If the remote computer is compromised, the credentials that are passed to it can be used to control the network session.</span></span>

```yaml
Type: System.Management.Automation.Runspaces.AuthenticationMechanism
Parameter Sets: ScriptBlock, FilePath
Aliases:
Accepted values: Default, Basic, Negotiate, NegotiateWithImplicitCredential, Credssp, Digest, Kerberos

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="15813-159">-ClearExecutionHistory</span><span class="sxs-lookup"><span data-stu-id="15813-159">-ClearExecutionHistory</span></span>
<span data-ttu-id="15813-160">Tar bort den aktuella körnings historiken och de sparade resultaten för det schemalagda jobbet.</span><span class="sxs-lookup"><span data-stu-id="15813-160">Deletes the current execution history and the saved results of the scheduled job.</span></span>

<span data-ttu-id="15813-161">Jobb körnings historiken och jobb resultaten sparas med det schemalagda jobbet i katalogen $home \AppData\Local\Microsoft\Windows\PowerShell\ScheduledJobs på den dator där jobbet skapas.</span><span class="sxs-lookup"><span data-stu-id="15813-161">The job execution history and job results are saved with the scheduled job in the $home\AppData\Local\Microsoft\Windows\PowerShell\ScheduledJobs directory on the computer on which the job is created.</span></span>
<span data-ttu-id="15813-162">Använd Get-Job-cmdleten om du vill se körnings historiken.</span><span class="sxs-lookup"><span data-stu-id="15813-162">To see the execution history, use the Get-Job cmdlet.</span></span>
<span data-ttu-id="15813-163">Använd Receive-Job-cmdleten för att hämta jobb resultatet.</span><span class="sxs-lookup"><span data-stu-id="15813-163">To get the job results, use the Receive-Job cmdlet.</span></span>

<span data-ttu-id="15813-164">Den här parametern påverkar inte de händelser som Schemaläggaren skriver till händelse loggarna i Windows, och den stoppar inte Windows PowerShell från att spara jobb resultat.</span><span class="sxs-lookup"><span data-stu-id="15813-164">This parameter does not affect the events that Task Scheduler writes to the Windows event logs and it does not stop Windows PowerShell from saving job results.</span></span>
<span data-ttu-id="15813-165">Om du vill hantera antalet jobb resultat som sparas använder du parametern *MaxResultCount* .</span><span class="sxs-lookup"><span data-stu-id="15813-165">To manage the number of job results that are saved, use the *MaxResultCount* parameter.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Execution
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="15813-166">-Credential</span><span class="sxs-lookup"><span data-stu-id="15813-166">-Credential</span></span>
<span data-ttu-id="15813-167">Anger ett användar konto som har behörighet att köra det schemalagda jobbet.</span><span class="sxs-lookup"><span data-stu-id="15813-167">Specifies a user account that has permission to run the scheduled job.</span></span>
<span data-ttu-id="15813-168">Standard är den aktuella användaren.</span><span class="sxs-lookup"><span data-stu-id="15813-168">The default is the current user.</span></span>

<span data-ttu-id="15813-169">Ange ett användar namn, till exempel user01 eller Domain01\User01, eller ange ett **PSCredential** -objekt, till exempel ett från Get-Credential-cmdleten.</span><span class="sxs-lookup"><span data-stu-id="15813-169">Type a user name, such as User01 or Domain01\User01, or enter a **PSCredential** object, such as one from the Get-Credential cmdlet.</span></span>
<span data-ttu-id="15813-170">Om du bara anger ett användar namn uppmanas du att ange ett lösen ord.</span><span class="sxs-lookup"><span data-stu-id="15813-170">If you enter only a user name, you will be prompted for a password.</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: ScriptBlock, FilePath
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="15813-171">-Sökväg</span><span class="sxs-lookup"><span data-stu-id="15813-171">-FilePath</span></span>
<span data-ttu-id="15813-172">Anger ett skript som det schemalagda jobbet körs på.</span><span class="sxs-lookup"><span data-stu-id="15813-172">Specifies a script that the scheduled job runs.</span></span>
<span data-ttu-id="15813-173">Ange sökvägen till en. ps1-fil på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="15813-173">Enter the path to a .ps1 file on the local computer.</span></span>
<span data-ttu-id="15813-174">Om du vill ange standardvärden för skript parametrarna använder du parametern *argument List* .</span><span class="sxs-lookup"><span data-stu-id="15813-174">To specify default values for the script parameters, use the *ArgumentList* parameter.</span></span>
<span data-ttu-id="15813-175">Varje schemalagt jobb måste ha antingen ett *script block* eller ett värde för *fil Sök väg* .</span><span class="sxs-lookup"><span data-stu-id="15813-175">Every scheduled job must have either a *ScriptBlock* or *FilePath* value.</span></span>

```yaml
Type: System.String
Parameter Sets: FilePath
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="15813-176">-InitializationScript</span><span class="sxs-lookup"><span data-stu-id="15813-176">-InitializationScript</span></span>
<span data-ttu-id="15813-177">Anger den fullständigt kvalificerade sökvägen till ett Windows PowerShell-skript (. ps1).</span><span class="sxs-lookup"><span data-stu-id="15813-177">Specifies the fully qualified path to a Windows PowerShell script (.ps1).</span></span>
<span data-ttu-id="15813-178">Initierings skriptet körs i sessionen som skapas för bakgrunds jobbet före de kommandon som anges av parametern *script block* eller det skript som anges av parametern *sökväg* .</span><span class="sxs-lookup"><span data-stu-id="15813-178">The initialization script runs in the session that is created for the background job before the commands that are specified by the *ScriptBlock* parameter or the script that is specified by the *FilePath* parameter.</span></span>
<span data-ttu-id="15813-179">Du kan använda initierings skriptet för att konfigurera sessionen, till exempel lägga till filer, funktioner eller alias, skapa kataloger eller kontrol lera krav.</span><span class="sxs-lookup"><span data-stu-id="15813-179">You can use the initialization script to configure the session, such as adding files, functions, or aliases, creating directories, or checking for prerequisites.</span></span>

<span data-ttu-id="15813-180">Om du vill ange ett skript som kör de primära jobb kommandona använder du parametern *sökväg* .</span><span class="sxs-lookup"><span data-stu-id="15813-180">To specify a script that runs the primary job commands, use the *FilePath* parameter.</span></span>

<span data-ttu-id="15813-181">Om initierings skriptet genererar ett fel, inklusive ett icke-avslutande fel, körs inte den aktuella instansen av det schemalagda jobbet och dess status misslyckades.</span><span class="sxs-lookup"><span data-stu-id="15813-181">If the initialization script generates an error, including a non-terminating error, the current instance of the scheduled job does not run and its status is Failed.</span></span>

```yaml
Type: System.Management.Automation.ScriptBlock
Parameter Sets: ScriptBlock, FilePath
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="15813-182">– InputObject</span><span class="sxs-lookup"><span data-stu-id="15813-182">-InputObject</span></span>
<span data-ttu-id="15813-183">Anger det schemalagda jobbet som ska ändras.</span><span class="sxs-lookup"><span data-stu-id="15813-183">Specifies the scheduled job to be changed.</span></span>
<span data-ttu-id="15813-184">Ange en variabel som innehåller **ScheduledJobDefinition** -objekt eller Skriv ett kommando eller uttryck som hämtar **ScheduledJobDefinition** -objekt, till exempel ett Get-ScheduledJob-kommando.</span><span class="sxs-lookup"><span data-stu-id="15813-184">Enter a variable that contains **ScheduledJobDefinition** objects or type a command or expression that gets **ScheduledJobDefinition** objects, such as a Get-ScheduledJob command.</span></span>
<span data-ttu-id="15813-185">Du kan också skicka ett **ScheduledJobDefinition** -objekt till **set-ScheduledJob**.</span><span class="sxs-lookup"><span data-stu-id="15813-185">You can also pipe a **ScheduledJobDefinition** object to **Set-ScheduledJob**.</span></span>

<span data-ttu-id="15813-186">Om du anger flera schemalagda jobb gör **set-ScheduledJob** samma ändringar i alla jobb.</span><span class="sxs-lookup"><span data-stu-id="15813-186">If you specify multiple scheduled jobs, **Set-ScheduledJob** makes the same changes to all jobs.</span></span>

```yaml
Type: Microsoft.PowerShell.ScheduledJob.ScheduledJobDefinition
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="15813-187">– MaxResultCount</span><span class="sxs-lookup"><span data-stu-id="15813-187">-MaxResultCount</span></span>
<span data-ttu-id="15813-188">Anger hur många jobb resultat poster som ska behållas för det schemalagda jobbet.</span><span class="sxs-lookup"><span data-stu-id="15813-188">Specifies how many job result entries are maintained for the scheduled job.</span></span>
<span data-ttu-id="15813-189">Standardvärdet är 32.</span><span class="sxs-lookup"><span data-stu-id="15813-189">The default value is 32.</span></span>

<span data-ttu-id="15813-190">Windows PowerShell sparar körnings historiken och resultaten av varje utlöst instans av det schemalagda jobbet på disken.</span><span class="sxs-lookup"><span data-stu-id="15813-190">Windows PowerShell saves the execution history and results of each triggered instance of the scheduled job on disk.</span></span>
<span data-ttu-id="15813-191">Värdet för den här parametern avgör antalet jobb instans resultat som sparas för det här schemalagda jobbet.</span><span class="sxs-lookup"><span data-stu-id="15813-191">The value of this parameter determines the number of job instance results that are saved for this scheduled job.</span></span>
<span data-ttu-id="15813-192">När antalet jobb instans resultat överskrider det här värdet, tar Windows PowerShell bort resultatet från den äldsta jobb instansen för att göra plats för resultatet av den senaste jobb instansen.</span><span class="sxs-lookup"><span data-stu-id="15813-192">When the number of job instance results exceeds this value, Windows PowerShell deletes the results of the oldest job instance to make room for the results of the newest job instance.</span></span>

<span data-ttu-id="15813-193">Jobb körnings historiken och jobb resultaten sparas i katalogen $home \AppData\Local\Microsoft\Windows\PowerShell\ScheduledJobs- \\ \<JobName\> \Output \\ \<Timestamp\> på den dator där jobbet skapas.</span><span class="sxs-lookup"><span data-stu-id="15813-193">The job execution history and job results are saved in the $home\AppData\Local\Microsoft\Windows\PowerShell\ScheduledJobs\\\<JobName\>\Output\\\<Timestamp\> directories on the computer on which the job is created.</span></span>
<span data-ttu-id="15813-194">Använd Get-Job-cmdleten om du vill se körnings historiken.</span><span class="sxs-lookup"><span data-stu-id="15813-194">To see the execution history, use the Get-Job cmdlet.</span></span>
<span data-ttu-id="15813-195">Använd Receive-Job-cmdleten för att hämta jobb resultatet.</span><span class="sxs-lookup"><span data-stu-id="15813-195">To get the job results, use the Receive-Job cmdlet.</span></span>

<span data-ttu-id="15813-196">Parametern *MaxResultCount* anger värdet för egenskapen ExecutionHistoryLength för det schemalagda jobbet.</span><span class="sxs-lookup"><span data-stu-id="15813-196">The *MaxResultCount* parameter sets the value of the ExecutionHistoryLength property of the scheduled job.</span></span>

<span data-ttu-id="15813-197">Om du vill ta bort den aktuella körnings historiken och jobb resultaten använder du parametern *ClearExecutionHistory* .</span><span class="sxs-lookup"><span data-stu-id="15813-197">To delete the current execution history and job results, use the *ClearExecutionHistory* parameter.</span></span>

```yaml
Type: System.Int32
Parameter Sets: ScriptBlock, FilePath
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="15813-198">-Name</span><span class="sxs-lookup"><span data-stu-id="15813-198">-Name</span></span>
<span data-ttu-id="15813-199">Anger ett nytt namn för det schemalagda jobbet och instanser av det schemalagda jobbet.</span><span class="sxs-lookup"><span data-stu-id="15813-199">Specifies a new name for the scheduled job and instances of the scheduled job.</span></span>
<span data-ttu-id="15813-200">Namnet måste vara unikt på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="15813-200">The name must be unique on the local computer.</span></span>

<span data-ttu-id="15813-201">Om du vill identifiera det schemalagda jobbet som ska ändras använder du parametern *InputObject* eller lägger till ett schemalagt jobb från Get-ScheduledJob till **set-ScheduledJob**.</span><span class="sxs-lookup"><span data-stu-id="15813-201">To identify the scheduled job to be changed, use the *InputObject* parameter or pipe a scheduled job from Get-ScheduledJob to **Set-ScheduledJob**.</span></span>

<span data-ttu-id="15813-202">Den här parametern ändrar inte namnen på jobb instanser på disken.</span><span class="sxs-lookup"><span data-stu-id="15813-202">This parameter does not change the names of job instances on disk.</span></span>
<span data-ttu-id="15813-203">Den påverkar bara jobb instanser som startas när det här kommandot har slutförts.</span><span class="sxs-lookup"><span data-stu-id="15813-203">It affects only job instances that are started after this command completes.</span></span>

```yaml
Type: System.String
Parameter Sets: ScriptBlock, FilePath
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="15813-204">– PassThru</span><span class="sxs-lookup"><span data-stu-id="15813-204">-PassThru</span></span>
<span data-ttu-id="15813-205">Returnerar ett objekt som representerar det objekt som du arbetar med.</span><span class="sxs-lookup"><span data-stu-id="15813-205">Returns an object representing the item with which you are working.</span></span>
<span data-ttu-id="15813-206">Som standard genererar denna cmdlet inga utdata.</span><span class="sxs-lookup"><span data-stu-id="15813-206">By default, this cmdlet does not generate any output.</span></span>

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

### <span data-ttu-id="15813-207">-RunAs32</span><span class="sxs-lookup"><span data-stu-id="15813-207">-RunAs32</span></span>
<span data-ttu-id="15813-208">Kör det schemalagda jobbet i en 32-bitars process.</span><span class="sxs-lookup"><span data-stu-id="15813-208">Runs the scheduled job in a 32-bit process.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ScriptBlock, FilePath
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="15813-209">-RunEvery</span><span class="sxs-lookup"><span data-stu-id="15813-209">-RunEvery</span></span>

<span data-ttu-id="15813-210">Används för att ange hur ofta jobbet ska köras.</span><span class="sxs-lookup"><span data-stu-id="15813-210">Used to specify how often to run the job.</span></span> <span data-ttu-id="15813-211">Använd exempelvis det här alternativet för att köra ett jobb var 15: e minut.</span><span class="sxs-lookup"><span data-stu-id="15813-211">For example, use this option to run a job every 15 minutes.</span></span>

```yaml
Type: System.TimeSpan
Parameter Sets: ScriptBlock, FilePath
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="15813-212">-RunNow</span><span class="sxs-lookup"><span data-stu-id="15813-212">-RunNow</span></span>
<span data-ttu-id="15813-213">Startar ett jobb omedelbart så snart cmdleten **set-ScheduledJob** körs.</span><span class="sxs-lookup"><span data-stu-id="15813-213">Starts a job immediately, as soon as the **Set-ScheduledJob** cmdlet is run.</span></span>
<span data-ttu-id="15813-214">Den här parametern eliminerar behovet av att utlösa Schemaläggaren för att köra ett Windows PowerShell-skript direkt efter registreringen och kräver inte att användare skapar en utlösare som anger start datum och start tid.</span><span class="sxs-lookup"><span data-stu-id="15813-214">This parameter eliminates the need to trigger Task Scheduler to run a Windows PowerShell script immediately after registration, and does not require users to create a trigger that specifies a starting date and time.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ScriptBlock, FilePath
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="15813-215">-ScheduledJobOption</span><span class="sxs-lookup"><span data-stu-id="15813-215">-ScheduledJobOption</span></span>
<span data-ttu-id="15813-216">Anger alternativ för det schemalagda jobbet.</span><span class="sxs-lookup"><span data-stu-id="15813-216">Sets options for the scheduled job.</span></span>
<span data-ttu-id="15813-217">Ange ett **ScheduledJobOptions** -objekt, till exempel ett som du skapar med hjälp av New-ScheduledJobOption-cmdlet eller ett värde för hash-tabellen.</span><span class="sxs-lookup"><span data-stu-id="15813-217">Enter a **ScheduledJobOptions** object, such as one that you create by using the New-ScheduledJobOption cmdlet, or a hash table value.</span></span>

<span data-ttu-id="15813-218">Du kan ange alternativ för ett schemalagt jobb när du registrerar det schemalagda jobbet eller använda Set-ScheduledJobOption eller **set-ScheduledJob-** cmdletar för att ange eller ändra alternativ.</span><span class="sxs-lookup"><span data-stu-id="15813-218">You can set options for a scheduled job when you register the scheduled job or use the Set-ScheduledJobOption or **Set-ScheduledJob** cmdlets to set or change options.</span></span>

<span data-ttu-id="15813-219">Många av alternativen och deras standardvärden avgör om och när ett schemalagt jobb körs.</span><span class="sxs-lookup"><span data-stu-id="15813-219">Many of the options and their default values determine whether and when a scheduled job runs.</span></span>
<span data-ttu-id="15813-220">Se till att granska de här alternativen innan du schemalägger ett jobb.</span><span class="sxs-lookup"><span data-stu-id="15813-220">Be sure to review these options before scheduling a job.</span></span>
<span data-ttu-id="15813-221">En beskrivning av de schemalagda jobb alternativen, inklusive standardvärdena, finns i New-ScheduledJobOption.</span><span class="sxs-lookup"><span data-stu-id="15813-221">For a description of the scheduled job options, including the default values, see New-ScheduledJobOption.</span></span>

<span data-ttu-id="15813-222">Om du vill skicka en hash-tabell använder du följande nycklar.</span><span class="sxs-lookup"><span data-stu-id="15813-222">To submit a hash table, use the following keys.</span></span>
<span data-ttu-id="15813-223">I följande hash-tabell visas nycklarna med standardvärdena.</span><span class="sxs-lookup"><span data-stu-id="15813-223">In the following hash table, the keys are shown with their default values.</span></span>

`@{# Power SettingsStartIfOnBattery=$False;StopIfGoingOnBattery=$True; WakeToRun=$False; # Idle SettingsStartIfNotIdle=$False; IdleDuration="00:10:00"; IdleTimeout="01:00:00"; StopIfGoingOffIdle=$True; RestartOnIdleResume=$False;# Security settingsShowInTaskScheduler=$TrueRunElevated=$False;# MiscRunWithoutNetwork=$False;DoNotAllowDemandStart=$False;MultipleInstancePolicy=IgnoreNew# Can be IgnoreNew, Parallel, Queue, StopExisting}`

```yaml
Type: Microsoft.PowerShell.ScheduledJob.ScheduledJobOptions
Parameter Sets: ScriptBlock, FilePath
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="15813-224">– Script block</span><span class="sxs-lookup"><span data-stu-id="15813-224">-ScriptBlock</span></span>
<span data-ttu-id="15813-225">Anger de kommandon som det schemalagda jobbet körs på.</span><span class="sxs-lookup"><span data-stu-id="15813-225">Specifies the commands that the scheduled job runs.</span></span>
<span data-ttu-id="15813-226">Omge kommandoen med klammerparenteser ({}) för att skapa ett skript block.</span><span class="sxs-lookup"><span data-stu-id="15813-226">Enclose the commands in braces ( { } ) to create a script block.</span></span>
<span data-ttu-id="15813-227">Om du vill ange standardvärden för kommando parametrar använder du parametern *argument List* .</span><span class="sxs-lookup"><span data-stu-id="15813-227">To specify default values for command parameters, use the *ArgumentList* parameter.</span></span>

<span data-ttu-id="15813-228">Alla Register-ScheduledJob-kommandon måste använda antingen parametrarna *script block* eller *sökväg* .</span><span class="sxs-lookup"><span data-stu-id="15813-228">Every Register-ScheduledJob command must use either the *ScriptBlock* or *FilePath* parameters.</span></span>

```yaml
Type: System.Management.Automation.ScriptBlock
Parameter Sets: ScriptBlock
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="15813-229">– Utlös</span><span class="sxs-lookup"><span data-stu-id="15813-229">-Trigger</span></span>
<span data-ttu-id="15813-230">Anger utlösare för det schemalagda jobbet.</span><span class="sxs-lookup"><span data-stu-id="15813-230">Specifies the triggers for the scheduled job.</span></span>
<span data-ttu-id="15813-231">Ange ett eller flera **ScheduledJobTrigger** -objekt, till exempel de objekt som New-JobTrigger cmdlet returnerar eller en hash-tabell med jobb utlöser nycklar och värden.</span><span class="sxs-lookup"><span data-stu-id="15813-231">Enter one or more **ScheduledJobTrigger** objects, such as the objects that the New-JobTrigger cmdlet returns, or a hash table of job trigger keys and values.</span></span>

<span data-ttu-id="15813-232">En jobb utlösare startar ett schemalagt jobb automatiskt vid en enstaka tidpunkt eller ett återkommande schema eller när en händelse inträffar.</span><span class="sxs-lookup"><span data-stu-id="15813-232">A job trigger starts a scheduled job automatically on a one-time or recurring scheduled or when an event occurs.</span></span>

<span data-ttu-id="15813-233">Jobb utlösare är valfria.</span><span class="sxs-lookup"><span data-stu-id="15813-233">Job triggers are optional.</span></span>
<span data-ttu-id="15813-234">Du kan lägga till en utlösare när du skapar det schemalagda jobbet, använda cmdletarna Add-JobTrigger eller **set-ScheduledJob** för att lägga till utlösare senare, eller använda cmdleten Start-Job för att starta det schemalagda jobbet omedelbart.</span><span class="sxs-lookup"><span data-stu-id="15813-234">You can add a trigger when you create the scheduled job, use the Add-JobTrigger or **Set-ScheduledJob** cmdlets to add triggers later, or use the Start-Job cmdlet to start the scheduled job immediately.</span></span>
<span data-ttu-id="15813-235">Du kan också skapa och underhålla ett schemalagt jobb som inte har några jobb utlösare.</span><span class="sxs-lookup"><span data-stu-id="15813-235">You can also create and maintain a scheduled job that has no job triggers.</span></span>

<span data-ttu-id="15813-236">Om du vill skicka en hash-tabell använder du följande nycklar.</span><span class="sxs-lookup"><span data-stu-id="15813-236">To submit a hash table, use the following keys.</span></span>

<span data-ttu-id="15813-237">`@{Frequency="Once" (or Daily, Weekly, AtStartup, AtLogon);At="3am"` (eller en giltig tids sträng); `DaysOfWeek="Monday", "Wednesday"` (eller valfri kombination av dag namn); `Interval=2` (eller ett giltigt frekvens intervall); `RandomDelay="30minutes"` (eller en giltig TimeSpan-sträng); `User="Domain1\User01"` (eller en giltig användare, används endast med AtLogon frekvens värde)</span><span class="sxs-lookup"><span data-stu-id="15813-237">`@{Frequency="Once" (or Daily, Weekly, AtStartup, AtLogon);At="3am"` (or any valid time string); `DaysOfWeek="Monday", "Wednesday"` (or any combination of day names); `Interval=2` (or any valid frequency interval); `RandomDelay="30minutes"` (or any valid timespan string); `User="Domain1\User01"` (or any valid user; used only with the AtLogon frequency value)</span></span>

<span data-ttu-id="15813-238">}</span><span class="sxs-lookup"><span data-stu-id="15813-238">}</span></span>

```yaml
Type: Microsoft.PowerShell.ScheduledJob.ScheduledJobTrigger[]
Parameter Sets: ScriptBlock, FilePath
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="15813-239">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="15813-239">CommonParameters</span></span>
<span data-ttu-id="15813-240">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="15813-240">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="15813-241">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="15813-241">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="15813-242">INDATA</span><span class="sxs-lookup"><span data-stu-id="15813-242">INPUTS</span></span>

### <span data-ttu-id="15813-243">Microsoft. PowerShell. ScheduledJob. ScheduledJobDefinition</span><span class="sxs-lookup"><span data-stu-id="15813-243">Microsoft.PowerShell.ScheduledJob.ScheduledJobDefinition</span></span>
<span data-ttu-id="15813-244">Du kan skicka vidare schemalagda jobb till **set-ScheduledJob**.</span><span class="sxs-lookup"><span data-stu-id="15813-244">You can pipe scheduled jobs to **Set-ScheduledJob**.</span></span>

## <span data-ttu-id="15813-245">UTDATA</span><span class="sxs-lookup"><span data-stu-id="15813-245">OUTPUTS</span></span>

### <span data-ttu-id="15813-246">Ingen eller Microsoft. PowerShell. ScheduledJob. ScheduledJobDefinition</span><span class="sxs-lookup"><span data-stu-id="15813-246">None or Microsoft.PowerShell.ScheduledJob.ScheduledJobDefinition</span></span>
<span data-ttu-id="15813-247">Om du använder parametern *Passthru* , **set-ScheduledJob** returnerar det schemalagda jobbet som ändrades.</span><span class="sxs-lookup"><span data-stu-id="15813-247">If you use the *Passthru* parameter, **Set-ScheduledJob** returns the scheduled job that was changed.</span></span>
<span data-ttu-id="15813-248">Annars genererar denna cmdlet inga utdata.</span><span class="sxs-lookup"><span data-stu-id="15813-248">Otherwise, this cmdlet does not generate any output.</span></span>

## <span data-ttu-id="15813-249">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="15813-249">NOTES</span></span>

## <span data-ttu-id="15813-250">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="15813-250">RELATED LINKS</span></span>

[<span data-ttu-id="15813-251">Add-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="15813-251">Add-JobTrigger</span></span>](Add-JobTrigger.md)

[<span data-ttu-id="15813-252">Disable-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="15813-252">Disable-JobTrigger</span></span>](Disable-JobTrigger.md)

[<span data-ttu-id="15813-253">Disable-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="15813-253">Disable-ScheduledJob</span></span>](Disable-ScheduledJob.md)

[<span data-ttu-id="15813-254">Aktivera – JobTrigger</span><span class="sxs-lookup"><span data-stu-id="15813-254">Enable-JobTrigger</span></span>](Enable-JobTrigger.md)

[<span data-ttu-id="15813-255">Aktivera – ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="15813-255">Enable-ScheduledJob</span></span>](Enable-ScheduledJob.md)

[<span data-ttu-id="15813-256">Get-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="15813-256">Get-JobTrigger</span></span>](Get-JobTrigger.md)

[<span data-ttu-id="15813-257">Get-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="15813-257">Get-ScheduledJob</span></span>](Get-ScheduledJob.md)

[<span data-ttu-id="15813-258">Get-ScheduledJobOption</span><span class="sxs-lookup"><span data-stu-id="15813-258">Get-ScheduledJobOption</span></span>](Get-ScheduledJobOption.md)

[<span data-ttu-id="15813-259">New-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="15813-259">New-JobTrigger</span></span>](New-JobTrigger.md)

[<span data-ttu-id="15813-260">New-ScheduledJobOption</span><span class="sxs-lookup"><span data-stu-id="15813-260">New-ScheduledJobOption</span></span>](New-ScheduledJobOption.md)

[<span data-ttu-id="15813-261">Registrera – ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="15813-261">Register-ScheduledJob</span></span>](Register-ScheduledJob.md)

[<span data-ttu-id="15813-262">Remove-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="15813-262">Remove-JobTrigger</span></span>](Remove-JobTrigger.md)

[<span data-ttu-id="15813-263">Set-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="15813-263">Set-JobTrigger</span></span>](Set-JobTrigger.md)

[<span data-ttu-id="15813-264">Set-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="15813-264">Set-ScheduledJob</span></span>](Set-ScheduledJob.md)

[<span data-ttu-id="15813-265">Set-ScheduledJobOption</span><span class="sxs-lookup"><span data-stu-id="15813-265">Set-ScheduledJobOption</span></span>](Set-ScheduledJobOption.md)

[<span data-ttu-id="15813-266">Avregistrera-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="15813-266">Unregister-ScheduledJob</span></span>](Unregister-ScheduledJob.md)
