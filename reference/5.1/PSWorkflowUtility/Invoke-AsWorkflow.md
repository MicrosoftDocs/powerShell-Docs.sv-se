---
external help file: Microsoft.PowerShell.Workflow.ServiceCore.dll-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSWorkflowUtility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psworkflowutility/invoke-asworkflow?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Invoke-AsWorkflow
ms.openlocfilehash: b96bce9fe4d574fe2b7e9c7c0f1e05ee0508adce
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93264596"
---
# <span data-ttu-id="eddf0-103">Invoke-AsWorkflow</span><span class="sxs-lookup"><span data-stu-id="eddf0-103">Invoke-AsWorkflow</span></span>

## <span data-ttu-id="eddf0-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="eddf0-104">SYNOPSIS</span></span>
<span data-ttu-id="eddf0-105">Kör ett kommando eller uttryck som ett Windows PowerShell-arbetsflöde.</span><span class="sxs-lookup"><span data-stu-id="eddf0-105">Runs a command or expression as a Windows PowerShell Workflow.</span></span>

## <span data-ttu-id="eddf0-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="eddf0-106">SYNTAX</span></span>

### <span data-ttu-id="eddf0-107">Kommando (standard)</span><span class="sxs-lookup"><span data-stu-id="eddf0-107">Command (Default)</span></span>

```
Invoke-AsWorkflow [-CommandName <String>] [-Parameter <Hashtable>] [-InputObject <Object>] [<CommonParameters>]
```

### <span data-ttu-id="eddf0-108">Uttryck</span><span class="sxs-lookup"><span data-stu-id="eddf0-108">Expression</span></span>

```
Invoke-AsWorkflow [-Expression <String>] [-InputObject <Object>] [<CommonParameters>]
```

## <span data-ttu-id="eddf0-109">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="eddf0-109">DESCRIPTION</span></span>

<span data-ttu-id="eddf0-110">`Invoke-AsWorkflow`Arbets flödet kör ett kommando eller uttryck som ett infogat skript i ett arbets flöde.</span><span class="sxs-lookup"><span data-stu-id="eddf0-110">The `Invoke-AsWorkflow` workflow runs any command or expression as an inline script in a workflow.</span></span>
<span data-ttu-id="eddf0-111">Dessa arbets flöden använder standard-semantiken för arbets flöde, har alla gemensamma parametrar för arbets flödet och har alla fördelar med arbets flöden, inklusive möjligheten att stoppa, återuppta och återställa.</span><span class="sxs-lookup"><span data-stu-id="eddf0-111">These workflows use the standard workflow semantics, have all workflow common parameters, and have all benefits of workflows, including the ability to stop, resume, and recover.</span></span>

<span data-ttu-id="eddf0-112">Arbets flöden är utformade för långvariga kommandon som samlar in viktiga data, men som kan användas för att köra kommandon.</span><span class="sxs-lookup"><span data-stu-id="eddf0-112">Workflows are designed for long-running commands that collect critical data, but can be used to run any command.</span></span>
<span data-ttu-id="eddf0-113">Mer information finns i [about_Workflows](../PSWorkflow/About/about_Workflows.md).</span><span class="sxs-lookup"><span data-stu-id="eddf0-113">For more information, see [about_Workflows](../PSWorkflow/About/about_Workflows.md).</span></span>

<span data-ttu-id="eddf0-114">Du kan också lägga till gemensamma parametrar för arbets flöden i det här kommandot.</span><span class="sxs-lookup"><span data-stu-id="eddf0-114">You can also add workflow common parameters to this command.</span></span>
<span data-ttu-id="eddf0-115">Mer information om gemensamma parametrar för arbets flöden finns i [about_WorkflowCommonParameters](../PSWorkflow/About/about_WorkflowCommonParameters.md)</span><span class="sxs-lookup"><span data-stu-id="eddf0-115">For more information about workflow common parameters, see [about_WorkflowCommonParameters](../PSWorkflow/About/about_WorkflowCommonParameters.md)</span></span>

<span data-ttu-id="eddf0-116">Det här arbets flödet introduceras i Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="eddf0-116">This workflow is introduced in Windows PowerShell 3.0.</span></span>

## <span data-ttu-id="eddf0-117">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="eddf0-117">EXAMPLES</span></span>

### <span data-ttu-id="eddf0-118">Exempel 1: kör en cmdlet som ett arbets flöde</span><span class="sxs-lookup"><span data-stu-id="eddf0-118">Example 1: Run a cmdlet as a workflow</span></span>

```powershell
Invoke-AsWorkflow -PSComputerName (Get-Content Servers.txt) -CommandName Get-ExecutionPolicy
```

```output
PSComputerName                     PSSourceJobInstanceId                   Value
--------------                     ---------------------                   -----
Server01                           77b1cdf8-8226-4662-9067-cd2fa5c3b711    AllSigned
Server02                           a33542d7-3cdd-4339-ab99-0e7cd8e59462    Unrestricted
Server03                           279bac28-066a-4646-9497-8fcdcfe9757e    AllSigned
localhost                          0d858009-2cc4-47a4-a2e0-da17dc2883d0    RemoteSigned
```

<span data-ttu-id="eddf0-119">Det här kommandot kör `Get-ExecutionPolicy` cmdleten som ett arbets flöde på hundratals datorer.</span><span class="sxs-lookup"><span data-stu-id="eddf0-119">This command runs the `Get-ExecutionPolicy` cmdlet as a workflow on hundreds of computers.</span></span>

<span data-ttu-id="eddf0-120">Kommandot använder parametern **commandname** för att ange den cmdlet som körs i arbets flödet.</span><span class="sxs-lookup"><span data-stu-id="eddf0-120">The command uses the **CommandName** parameter to specify the cmdlet that runs in the workflow.</span></span>
<span data-ttu-id="eddf0-121">Den gemensamma parametern för **PSComputerName** -arbetsflöde används för att ange de datorer där kommandot körs.</span><span class="sxs-lookup"><span data-stu-id="eddf0-121">It uses the **PSComputerName** workflow common parameter to specify the computers on which the command runs.</span></span>
<span data-ttu-id="eddf0-122">Värdet för parametern **PSComputerName** är ett `Get-Content` kommando som hämtar en lista med dator namn från Servers.txt-filen.</span><span class="sxs-lookup"><span data-stu-id="eddf0-122">The value of the **PSComputerName** parameter is a `Get-Content` command that gets a list of computer names from the Servers.txt file.</span></span>
<span data-ttu-id="eddf0-123">Parametervärdet omges av parenteser för att direkt köra Windows PowerShell för att köra `Get-Command` kommandot innan värdet används.</span><span class="sxs-lookup"><span data-stu-id="eddf0-123">The parameter value is enclosed in parentheses to direct Windows PowerShell to run the `Get-Command` command before using the value.</span></span>

<span data-ttu-id="eddf0-124">Som med alla fjärrkommandon, om kommandot körs på den lokala datorn (om värdet för parametern PSComputerName inkluderar den lokala datorn) måste du starta Windows PowerShell med alternativet "kör som administratör".</span><span class="sxs-lookup"><span data-stu-id="eddf0-124">As with all remote commands, if the command runs on the local computer, (if the value of the PSComputerName parameter includes the local computer), you must start Windows PowerShell with the "Run as administrator" option.</span></span>

### <span data-ttu-id="eddf0-125">Exempel 2: köra en cmdlet med parametrar</span><span class="sxs-lookup"><span data-stu-id="eddf0-125">Example 2: Run a cmdlet with parameters</span></span>

```powershell
$s = Import-Csv .\Servers.csv -Header ServerName, ServerID
Invoke-AsWorkflow -CommandName Get-ExecutionPolicy -Parameter @{Scope="Process"} -PSComputerName {$s.ServerName} -PSConnectionRetryCount 5
```

<span data-ttu-id="eddf0-126">Det första kommandot använder `Import-Csv` cmdleten för att skapa ett objekt från innehållet i Servers.csvs filen.</span><span class="sxs-lookup"><span data-stu-id="eddf0-126">The first command uses the `Import-Csv` cmdlet to create an object from the content in the Servers.csv file.</span></span> <span data-ttu-id="eddf0-127">Kommandot använder `Header` parametern för att skapa en `ServerName` egenskap för den kolumn som innehåller namnen på mål datorerna, även kallade "fjärrnoder".</span><span class="sxs-lookup"><span data-stu-id="eddf0-127">The command uses the `Header` parameter to create a `ServerName` property for the column that contains the names of the target computers, also known as "remote nodes."</span></span> <span data-ttu-id="eddf0-128">Kommandot sparar resultatet i `$s` variabeln.</span><span class="sxs-lookup"><span data-stu-id="eddf0-128">The command saves the result in the `$s` variable.</span></span>

<span data-ttu-id="eddf0-129">Det andra kommandot använder `Invoke-AsWorkflow` arbets flödet för att köra ett `Get-ExecutionPolicy` kommando på datorerna i Servers.csv-filen.</span><span class="sxs-lookup"><span data-stu-id="eddf0-129">The second command uses the `Invoke-AsWorkflow` workflow to run a `Get-ExecutionPolicy` command on the computers in the Servers.csv file.</span></span> <span data-ttu-id="eddf0-130">Kommandot använder parametern **commandname** för `Invoke-AsWorkflow`  för att ange det kommando som ska köras i arbets flödet.</span><span class="sxs-lookup"><span data-stu-id="eddf0-130">The command uses the **CommandName** parameter of `Invoke-AsWorkflow`  to specify the command to run in the workflow.</span></span> <span data-ttu-id="eddf0-131">`Parameter`Parametern i används `Invoke-AsWorkflow` för att ange `Scope` parametern för `Get-ExecutionPolicy` cmdleten med värdet **process**. Kommandot använder även `PSConnectionRetryCount` arbets flödets gemensamma parameter för att begränsa kommandot till fem försök på varje dator och den `PSComputerName` gemensamma parametern för arbets flödet för att ange namnen på fjärrnoderna (mål datorer).</span><span class="sxs-lookup"><span data-stu-id="eddf0-131">It uses the `Parameter` parameter of `Invoke-AsWorkflow` to specify the `Scope` parameter of the `Get-ExecutionPolicy` cmdlet with a value of **Process**.The command also uses the `PSConnectionRetryCount` workflow common parameter to limit the command to five attempts on each computer and the `PSComputerName` workflow common parameter to specify the names of the remote nodes (target computers).</span></span> <span data-ttu-id="eddf0-132">`PSComputerName`Parameterns värde är ett uttryck som hämtar `ServerName` egenskapen för varje objekt i `$s` variabeln.</span><span class="sxs-lookup"><span data-stu-id="eddf0-132">The value of the `PSComputerName` parameter is an expression that gets the `ServerName` property of every object in the `$s` variable.</span></span>

<span data-ttu-id="eddf0-133">Kommandona kör ett `Get-ExecutionPolicy` kommando som ett arbets flöde på hundratals datorer.</span><span class="sxs-lookup"><span data-stu-id="eddf0-133">These commands run a `Get-ExecutionPolicy` command as a workflow on hundreds of computers.</span></span>
<span data-ttu-id="eddf0-134">Kommandot använder `Scope` parametern för `Get-ExecutionPolicy` cmdleten med värdet **process** för att hämta körnings principen i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="eddf0-134">The command uses the `Scope` parameter of the `Get-ExecutionPolicy` cmdlet with a value of **Process** to get the execution policy in the current session.</span></span>

### <span data-ttu-id="eddf0-135">Exempel 3: kör ett uttryck som ett arbets flöde</span><span class="sxs-lookup"><span data-stu-id="eddf0-135">Example 3: Run an expression as a workflow</span></span>

```powershell
Invoke-AsWorkflow -Expression "ipconfig /all" -PSComputerName (Get-Content DomainControllers.txt) -AsJob -JobName IPConfig
```

```output
Id     Name          PSJobTypeName   State         HasMoreData   Location                Command
--     ----          -------------   -----         -----------   --------                -------
2      IpConfig      PSWorkflowJob   Completed     True          Server01, Server01...   Invoke-AsWorkflow
```

<span data-ttu-id="eddf0-136">Det här kommandot använder `Invoke-AsWorkflow` arbets flödet för att köra ett ipconfig-kommando som ett arbets flödes jobb på de datorer som anges i DomainControllers.txt-filen.</span><span class="sxs-lookup"><span data-stu-id="eddf0-136">This command uses the `Invoke-AsWorkflow` workflow to run an Ipconfig command as a workflow job on the computers listed in the DomainControllers.txt file.</span></span>

<span data-ttu-id="eddf0-137">Kommandot använder `Expression` parametern för att ange det uttryck som ska köras.</span><span class="sxs-lookup"><span data-stu-id="eddf0-137">The command uses the `Expression` parameter to specify the expression to run.</span></span>
<span data-ttu-id="eddf0-138">Den `PSComputerName` gemensamma parametern för arbets flödet används för att ange namnen på fjärrnoderna (mål datorer).</span><span class="sxs-lookup"><span data-stu-id="eddf0-138">It uses the `PSComputerName` workflow common parameter to specify the names of the remote nodes (target computers).</span></span>

<span data-ttu-id="eddf0-139">Kommandot använder också de `AsJob` `JobName` gemensamma parametrarna och för att köra arbets flödet som ett bakgrunds jobb på varje dator med jobbnamn "ipconfig".</span><span class="sxs-lookup"><span data-stu-id="eddf0-139">The command also uses the `AsJob` and `JobName` workflow common parameters to run the workflow as a background job on each computer with the "Ipconfig" job name.</span></span>

<span data-ttu-id="eddf0-140">Kommandot returnerar ett `ContainerParentJob` objekt ( `System.Management.Automation.ContainerParentJob` ) som innehåller arbets flödes jobben på varje dator.</span><span class="sxs-lookup"><span data-stu-id="eddf0-140">The command returns a `ContainerParentJob` object (`System.Management.Automation.ContainerParentJob`) that contains the workflow jobs on each computer.</span></span>

## <span data-ttu-id="eddf0-141">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="eddf0-141">PARAMETERS</span></span>

### <span data-ttu-id="eddf0-142">– CommandName</span><span class="sxs-lookup"><span data-stu-id="eddf0-142">-CommandName</span></span>

<span data-ttu-id="eddf0-143">Kör angiven cmdlet eller avancerad funktion som ett arbets flöde.</span><span class="sxs-lookup"><span data-stu-id="eddf0-143">Runs the specified cmdlet or advanced function as a workflow.</span></span>
<span data-ttu-id="eddf0-144">Ange cmdleten eller funktions namnet, till exempel `Update-Help` , `Set-ExecutionPolicy` eller `Set-NetFirewallRule` .</span><span class="sxs-lookup"><span data-stu-id="eddf0-144">Enter the cmdlet or function name, such as `Update-Help`, `Set-ExecutionPolicy`, or `Set-NetFirewallRule`.</span></span>

```yaml
Type: System.String
Parameter Sets: Command
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="eddf0-145">– Uttryck</span><span class="sxs-lookup"><span data-stu-id="eddf0-145">-Expression</span></span>

<span data-ttu-id="eddf0-146">Anger det uttryck som den här cmdleten kör som ett arbets flöde.</span><span class="sxs-lookup"><span data-stu-id="eddf0-146">Specifies the  expression that this cmdlet runs as a workflow.</span></span>
<span data-ttu-id="eddf0-147">Ange uttrycket som en sträng, till exempel `"ipconfig /all"` .</span><span class="sxs-lookup"><span data-stu-id="eddf0-147">Enter the expression as a string, such as `"ipconfig /all"`.</span></span>
<span data-ttu-id="eddf0-148">Om uttrycket innehåller blank steg eller specialtecken omger du uttrycket med citat tecken.</span><span class="sxs-lookup"><span data-stu-id="eddf0-148">If the expression includes spaces or special characters, enclose the expression in quotation marks.</span></span>

```yaml
Type: System.String
Parameter Sets: Expression
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="eddf0-149">-Parameter</span><span class="sxs-lookup"><span data-stu-id="eddf0-149">-Parameter</span></span>

<span data-ttu-id="eddf0-150">Anger parametrar och parameter värden för kommandot som anges i `CommandName` parametern.</span><span class="sxs-lookup"><span data-stu-id="eddf0-150">Specifies the parameters and parameter values of the command that is specified in the `CommandName` parameter.</span></span>
<span data-ttu-id="eddf0-151">Ange en hash-tabell där varje nyckel är ett parameter namn och dess värde är parametervärdet, till exempel `@{ExecutionPolicy="AllSigned"}` .</span><span class="sxs-lookup"><span data-stu-id="eddf0-151">Enter a hash table in which each key is a parameter name and its value is the parameter value, such as `@{ExecutionPolicy="AllSigned"}`.</span></span>

<span data-ttu-id="eddf0-152">Information om hash-tabeller finns i [about_Hash_Tables](../Microsoft.PowerShell.Core/About/about_Hash_Tables.md).</span><span class="sxs-lookup"><span data-stu-id="eddf0-152">For information about hash tables, see [about_Hash_Tables](../Microsoft.PowerShell.Core/About/about_Hash_Tables.md).</span></span>

```yaml
Type: System.Collections.Hashtable
Parameter Sets: Command
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="eddf0-153">– InputObject</span><span class="sxs-lookup"><span data-stu-id="eddf0-153">-InputObject</span></span>

<span data-ttu-id="eddf0-154">Används för att tillåta pipeline-inflöden.</span><span class="sxs-lookup"><span data-stu-id="eddf0-154">Used to allows pipeline input.</span></span>

```yaml
Type: System.Object
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="eddf0-155">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="eddf0-155">CommonParameters</span></span>

<span data-ttu-id="eddf0-156">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="eddf0-156">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="eddf0-157">Mer information finns i [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span><span class="sxs-lookup"><span data-stu-id="eddf0-157">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

### <span data-ttu-id="eddf0-158">WorkflowCommonParameters</span><span class="sxs-lookup"><span data-stu-id="eddf0-158">WorkflowCommonParameters</span></span>

<span data-ttu-id="eddf0-159">Den här cmdleten stöder också arbets flödes parametrar för gemensamma parametrar.</span><span class="sxs-lookup"><span data-stu-id="eddf0-159">This cmdlet also supports workflow specific common parameters.</span></span>
<span data-ttu-id="eddf0-160">Mer information finns i [about_WorkflowCommonParameters](../PSWorkflow/About/about_WorkflowCommonParameters.md).</span><span class="sxs-lookup"><span data-stu-id="eddf0-160">For information, see [about_WorkflowCommonParameters](../PSWorkflow/About/about_WorkflowCommonParameters.md).</span></span>

## <span data-ttu-id="eddf0-161">INDATA</span><span class="sxs-lookup"><span data-stu-id="eddf0-161">INPUTS</span></span>

### <span data-ttu-id="eddf0-162">System. Object</span><span class="sxs-lookup"><span data-stu-id="eddf0-162">System.Object</span></span>

<span data-ttu-id="eddf0-163">Du kan skicka ett objekt till- `InputObject` parametern.</span><span class="sxs-lookup"><span data-stu-id="eddf0-163">You can pipe any object to the `InputObject` parameter.</span></span>

## <span data-ttu-id="eddf0-164">UTDATA</span><span class="sxs-lookup"><span data-stu-id="eddf0-164">OUTPUTS</span></span>

### <span data-ttu-id="eddf0-165">Inget</span><span class="sxs-lookup"><span data-stu-id="eddf0-165">None</span></span>

<span data-ttu-id="eddf0-166">Det här kommandot genererar inga utdata.</span><span class="sxs-lookup"><span data-stu-id="eddf0-166">This command does not generate any output.</span></span>
<span data-ttu-id="eddf0-167">Men den kör arbets flödet, vilket kan generera utdata.</span><span class="sxs-lookup"><span data-stu-id="eddf0-167">However, it runs the workflow, which might generate output.</span></span>

## <span data-ttu-id="eddf0-168">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="eddf0-168">NOTES</span></span>

## <span data-ttu-id="eddf0-169">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="eddf0-169">RELATED LINKS</span></span>

[<span data-ttu-id="eddf0-170">New-PSWorkflowExecutionOption</span><span class="sxs-lookup"><span data-stu-id="eddf0-170">New-PSWorkflowExecutionOption</span></span>](../PSWorkflow/New-PSWorkflowExecutionOption.md)

[<span data-ttu-id="eddf0-171">New-PSWorkflowSession</span><span class="sxs-lookup"><span data-stu-id="eddf0-171">New-PSWorkflowSession</span></span>](../PSWorkflow/New-PSWorkflowSession.md)

[<span data-ttu-id="eddf0-172">about_Workflows</span><span class="sxs-lookup"><span data-stu-id="eddf0-172">about_Workflows</span></span>](../PSWorkflow/About/about_Workflows.md)

[<span data-ttu-id="eddf0-173">about_Workflow_Common_Parameters</span><span class="sxs-lookup"><span data-stu-id="eddf0-173">about_Workflow_Common_Parameters</span></span>](../PSWorkflow/About/about_WorkflowCommonParameters.md)
