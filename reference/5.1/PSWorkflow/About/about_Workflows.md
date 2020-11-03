---
description: Innehåller en kort introduktion till PowerShell Workflow-funktionen.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psworkflow/about/about_workflows?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Workflows
ms.openlocfilehash: fbd8ee62b1e9c6969d489c5024c33f5cca883dc6
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/13/2020
ms.locfileid: "93270909"
---
# <a name="about-workflows"></a><span data-ttu-id="b6841-104">Om arbets flöden</span><span class="sxs-lookup"><span data-stu-id="b6841-104">About Workflows</span></span>

## <a name="short-description"></a><span data-ttu-id="b6841-105">Kort beskrivning</span><span class="sxs-lookup"><span data-stu-id="b6841-105">Short description</span></span>

<span data-ttu-id="b6841-106">Innehåller en kort introduktion till PowerShell Workflow-funktionen.</span><span class="sxs-lookup"><span data-stu-id="b6841-106">Provides a brief introduction to the PowerShell Workflow feature.</span></span>

## <a name="long-description"></a><span data-ttu-id="b6841-107">Lång beskrivning</span><span class="sxs-lookup"><span data-stu-id="b6841-107">Long description</span></span>

<span data-ttu-id="b6841-108">PowerShell-arbetsflöde ger fördelarna med [Windows Workflow Foundation](/dotnet/framework/windows-workflow-foundation) till PowerShell och gör det möjligt att skriva och köra arbets flöden.</span><span class="sxs-lookup"><span data-stu-id="b6841-108">PowerShell Workflow brings the benefits of the [Windows Workflow Foundation](/dotnet/framework/windows-workflow-foundation) to PowerShell and enables you to write and run workflows.</span></span>

<span data-ttu-id="b6841-109">PowerShell-arbetsflöde introducerades i PowerShell 3,0 och modulen är tillgänglig upp till PowerShell 5,1.</span><span class="sxs-lookup"><span data-stu-id="b6841-109">PowerShell Workflow was introduced in PowerShell 3.0 and the module is available up to PowerShell 5.1.</span></span> <span data-ttu-id="b6841-110">Mer information om PowerShell-arbetsflöde finns i arbets flödes [guiden](/previous-versions/powershell/scripting/components/workflows-guide) och [skriva ett Windows PowerShell-arbetsflöde](/previous-versions/powershell/scripting/developer/workflow/writing-a-windows-powershell-workflow).</span><span class="sxs-lookup"><span data-stu-id="b6841-110">For more information about PowerShell Workflow, see the [Workflows Guide](/previous-versions/powershell/scripting/components/workflows-guide) and [Writing a Windows PowerShell Workflow](/previous-versions/powershell/scripting/developer/workflow/writing-a-windows-powershell-workflow).</span></span>

## <a name="about-workflows"></a><span data-ttu-id="b6841-111">Om arbets flöden</span><span class="sxs-lookup"><span data-stu-id="b6841-111">About workflows</span></span>

<span data-ttu-id="b6841-112">Arbets flöden är kommandon som består av en ordnad sekvens av relaterade aktiviteter.</span><span class="sxs-lookup"><span data-stu-id="b6841-112">Workflows are commands that consist of an ordered sequence of related activities.</span></span> <span data-ttu-id="b6841-113">De körs vanligt vis under en längre tid och samlar in data från och gör ändringar i hundratals datorer, ofta i heterogena miljöer.</span><span class="sxs-lookup"><span data-stu-id="b6841-113">Typically, they run for an extended period of time, gathering data from and making changes to hundreds of computers, often in heterogeneous environments.</span></span>

<span data-ttu-id="b6841-114">Arbets flöden kan skrivas i XAML, språket som används i Windows Workflow Foundation eller på PowerShell-språket.</span><span class="sxs-lookup"><span data-stu-id="b6841-114">Workflows can be written in XAML, the language used in Windows Workflow Foundation, or in the PowerShell language.</span></span> <span data-ttu-id="b6841-115">Arbets flöden paketeras vanligt vis i moduler och innehåller hjälp ämnen.</span><span class="sxs-lookup"><span data-stu-id="b6841-115">Workflows are typically packaged in modules and include help topics.</span></span> <span data-ttu-id="b6841-116">Mer information finns i [Översikt över XAML (WPF)](/dotnet/framework/wpf/advanced/xaml-overview-wpf).</span><span class="sxs-lookup"><span data-stu-id="b6841-116">For more information, see [XAML Overview (WPF)](/dotnet/framework/wpf/advanced/xaml-overview-wpf).</span></span>

<span data-ttu-id="b6841-117">Arbets flöden är viktiga i en IT-miljö eftersom de kan överleva omstarter och automatiskt återställas från vanliga fel.</span><span class="sxs-lookup"><span data-stu-id="b6841-117">Workflows are critical in an IT environment because they can survive reboots and recover automatically from common failures.</span></span> <span data-ttu-id="b6841-118">Du kan koppla från och återansluta från sessioner och datorer som kör arbets flöden utan att avbryta arbets flödes bearbetningen och pausa och återuppta arbets flöden transparent utan data förlust.</span><span class="sxs-lookup"><span data-stu-id="b6841-118">You can disconnect and reconnect from sessions and computers running workflows without interrupting workflow processing, and suspend and resume workflows transparently without data loss.</span></span> <span data-ttu-id="b6841-119">Varje aktivitet i ett arbets flöde kan loggas och granskas för referens.</span><span class="sxs-lookup"><span data-stu-id="b6841-119">Each activity in a workflow can be logged and audited for reference.</span></span>
<span data-ttu-id="b6841-120">Arbets flöden kan köras som jobb och kan schemaläggas med hjälp av funktionen schemalagda uppgifter i PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b6841-120">Workflows can run as jobs and can be scheduled by using the Scheduled Jobs feature of PowerShell.</span></span>

<span data-ttu-id="b6841-121">Tillstånd och data i ett arbets flöde sparas eller sparas i början och i slutet av arbets flödet och vid de punkter som du anger.</span><span class="sxs-lookup"><span data-stu-id="b6841-121">The state and data in a workflow is saved or persisted at the beginning and end of the workflow and at points that you specify.</span></span> <span data-ttu-id="b6841-122">Beständighets punkter i arbets flödet fungerar som databas ögonblicks bilder eller program kontroll punkter för att skydda arbets flödet från effekterna av avbrott och haverier.</span><span class="sxs-lookup"><span data-stu-id="b6841-122">Workflow persistence points work like database snapshots or program checkpoints to protect the workflow from the effects of interruptions and failures.</span></span> <span data-ttu-id="b6841-123">Om arbets flödet inte kan återställas efter ett fel kan du använda de sparade data och återuppta från den senaste beständiga punkten, i stället för att köra om ett omfattande arbets flöde från början.</span><span class="sxs-lookup"><span data-stu-id="b6841-123">If the workflow is unable to recover from a failure, you can use the persisted data and resume from the last persistence point, instead of rerunning an extensive workflow from the beginning.</span></span>

## <a name="workflow-requirements-and-configuration"></a><span data-ttu-id="b6841-124">Arbets flödes krav och konfiguration</span><span class="sxs-lookup"><span data-stu-id="b6841-124">Workflow requirements and configuration</span></span>

<span data-ttu-id="b6841-125">En PowerShell Workflow-konfiguration består av följande element:</span><span class="sxs-lookup"><span data-stu-id="b6841-125">A PowerShell Workflow configuration consists of the following elements:</span></span>

- <span data-ttu-id="b6841-126">En klient dator som kör arbets flödet.</span><span class="sxs-lookup"><span data-stu-id="b6841-126">A client computer, which runs the workflow.</span></span>
- <span data-ttu-id="b6841-127">En arbets flödes session, **PSSession** , på klient datorn eller en fjärrdator.</span><span class="sxs-lookup"><span data-stu-id="b6841-127">A workflow session, **PSSession** , on the client computer or on a remote computer.</span></span>
- <span data-ttu-id="b6841-128">Hanterade noder, de mål datorer som påverkas av arbets flödes aktiviteterna.</span><span class="sxs-lookup"><span data-stu-id="b6841-128">Managed nodes, the target computers that are affected by the workflow activities.</span></span>

<span data-ttu-id="b6841-129">Arbets flödes sessionen krävs inte, men rekommenderas.</span><span class="sxs-lookup"><span data-stu-id="b6841-129">The workflow session isn't required, but is recommended.</span></span> <span data-ttu-id="b6841-130">**PSSessions** kan dra nytta av funktionerna för robust återställning och frånkopplade sessioner i PowerShell för att återställa frånkopplade arbets flödes sessioner.</span><span class="sxs-lookup"><span data-stu-id="b6841-130">**PSSessions** can take advantage of the robust recovery and Disconnected Sessions features of PowerShell to recover disconnected workflow sessions.</span></span> <span data-ttu-id="b6841-131">Mer information finns i [about_Remote_Disconnected_Sessions](../../Microsoft.PowerShell.Core/About/about_Remote_Disconnected_Sessions.md)</span><span class="sxs-lookup"><span data-stu-id="b6841-131">For more information, see [about_Remote_Disconnected_Sessions](../../Microsoft.PowerShell.Core/About/about_Remote_Disconnected_Sessions.md)</span></span>

<span data-ttu-id="b6841-132">Eftersom klient datorn och datorn där arbets flödes sessionen körs kan hanterade noder, kan du köra ett arbets flöde på en dator som uppfyller alla roller.</span><span class="sxs-lookup"><span data-stu-id="b6841-132">Because the client computer and the computer on which the workflow session runs can be managed nodes, you can run a workflow on a single computer that fulfills all roles.</span></span>

<span data-ttu-id="b6841-133">Klient datorn och datorn där arbets flödes sessionen körs måste köra PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="b6841-133">The client computer and the computer on which the workflow session runs must be running PowerShell 3.0.</span></span> <span data-ttu-id="b6841-134">Alla berättigade system stöds, inklusive alternativ för Server Core-installation av Windows Server-operativsystem.</span><span class="sxs-lookup"><span data-stu-id="b6841-134">All eligible systems are supported, including the Server Core installation options of Windows Server operating systems.</span></span>

<span data-ttu-id="b6841-135">För att köra arbets flöden som innehåller cmdlets måste de hanterade noderna ha Windows PowerShell 2,0 eller senare.</span><span class="sxs-lookup"><span data-stu-id="b6841-135">To run workflows that include cmdlets, the managed nodes must have Windows PowerShell 2.0 or later.</span></span> <span data-ttu-id="b6841-136">Hanterade noder kräver inte PowerShell om inte arbets flödet innehåller cmdletar.</span><span class="sxs-lookup"><span data-stu-id="b6841-136">Managed nodes don't require PowerShell unless the workflow includes cmdlets.</span></span> <span data-ttu-id="b6841-137">Du kan köra arbets flöden som inkluderar Windows Management Instrumentation (WMI) och Common Information Model (CIM) kommandon på datorer som inte har PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b6841-137">You can run workflows that include Windows Management Instrumentation (WMI) and Common Information Model (CIM) commands on computers that don't have PowerShell.</span></span>

## <a name="how-to-get-workflows"></a><span data-ttu-id="b6841-138">Så här hämtar du arbets flöden</span><span class="sxs-lookup"><span data-stu-id="b6841-138">How to get workflows</span></span>

<span data-ttu-id="b6841-139">Arbets flöden paketeras vanligt vis i moduler.</span><span class="sxs-lookup"><span data-stu-id="b6841-139">Workflows are typically packaged in modules.</span></span> <span data-ttu-id="b6841-140">Om du vill importera modulen som innehåller ett arbets flöde, använder du valfritt kommando i modulen eller använder `Import-Module` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="b6841-140">To import the module that includes a workflow, use any command in the module or use the `Import-Module` cmdlet.</span></span>
<span data-ttu-id="b6841-141">Moduler importeras automatiskt vid första användningen av ett kommando i modulen.</span><span class="sxs-lookup"><span data-stu-id="b6841-141">Modules are imported automatically on first use of any command in the module.</span></span>

<span data-ttu-id="b6841-142">Om du vill hitta arbets flöden i moduler som är installerade på datorn använder du `Get-Command` cmdlet: en **CommandType** -parameter.</span><span class="sxs-lookup"><span data-stu-id="b6841-142">To find the workflows in modules installed on your computer, use the `Get-Command` cmdlet's **CommandType** parameter.</span></span>

```powershell
Get-Command -CommandType Workflow
```

## <a name="how-to-run-workflows"></a><span data-ttu-id="b6841-143">Så här kör du arbets flöden</span><span class="sxs-lookup"><span data-stu-id="b6841-143">How to run workflows</span></span>

<span data-ttu-id="b6841-144">Använd följande procedur om du vill köra ett arbets flöde.</span><span class="sxs-lookup"><span data-stu-id="b6841-144">To run a workflow, use the following procedure.</span></span>

1. <span data-ttu-id="b6841-145">Det här steget krävs inte när den hanterade noden är den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="b6841-145">When the managed node is the local computer, this step isn't required.</span></span>
   <span data-ttu-id="b6841-146">Annars startar du PowerShell med alternativet **Kör som administratör** på klient datorn.</span><span class="sxs-lookup"><span data-stu-id="b6841-146">Otherwise, on the client computer, start PowerShell with the **Run as administrator** option.</span></span>

   ```powershell
   Start-Process PowerShell -Verb RunAs
   ```

1. <span data-ttu-id="b6841-147">Aktivera PowerShell-fjärrkommunikation på datorn som kör arbets flödes sessionen och på hanterade noder som påverkas av arbets flöden som innehåller cmdletar.</span><span class="sxs-lookup"><span data-stu-id="b6841-147">Enable PowerShell remoting on the computer that runs the workflow session and on managed nodes affected by workflows that include cmdlets.</span></span>

   <span data-ttu-id="b6841-148">Du behöver bara göra det här steget en gång på varje deltagande dator.</span><span class="sxs-lookup"><span data-stu-id="b6841-148">You only need to do this step once on each participating computer.</span></span>

   <span data-ttu-id="b6841-149">Det här steget krävs bara när du kör arbets flöden som innehåller cmdletar.</span><span class="sxs-lookup"><span data-stu-id="b6841-149">This step is required only when running workflows that include cmdlets.</span></span> <span data-ttu-id="b6841-150">Du behöver inte aktivera fjärr kommunikation på klient datorn, om inte arbets flödes sessionen körs på klient datorn eller på några hanterade noder som kör PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="b6841-150">You don't need to enable remoting on the client computer, unless the workflows session runs on the client computer, or on any managed nodes that are running PowerShell 3.0.</span></span>

   <span data-ttu-id="b6841-151">Använd cmdleten om du vill aktivera fjärr kommunikation `Enable-PSRemoting` .</span><span class="sxs-lookup"><span data-stu-id="b6841-151">To enable remoting, use the `Enable-PSRemoting` cmdlet.</span></span>

   ```powershell
   Enable-PSRemoting -Force
   ```

   <span data-ttu-id="b6841-152">Du kan aktivera fjärr kommunikation med hjälp av inställningen **Aktivera körning av skript** Grupprincip.</span><span class="sxs-lookup"><span data-stu-id="b6841-152">You can enable remoting by using the **Turn on Script Execution** Group Policy setting.</span></span> <span data-ttu-id="b6841-153">Mer information finns i [about_Group_Policy_Settings](../../Microsoft.PowerShell.Core/About/about_Group_Policy_Settings.md) och [about_Execution_Policies](../../Microsoft.PowerShell.Core/About/about_Execution_Policies.md).</span><span class="sxs-lookup"><span data-stu-id="b6841-153">For more information, see [about_Group_Policy_Settings](../../Microsoft.PowerShell.Core/About/about_Group_Policy_Settings.md) and [about_Execution_Policies](../../Microsoft.PowerShell.Core/About/about_Execution_Policies.md).</span></span>

1. <span data-ttu-id="b6841-154">Använd `New-PSWorkflowSession` `New-PSSession` cmdletarna eller för att skapa arbets flödes sessionen.</span><span class="sxs-lookup"><span data-stu-id="b6841-154">Use the `New-PSWorkflowSession` or `New-PSSession` cmdlets to create the workflow session.</span></span>

   <span data-ttu-id="b6841-155">`New-PSWorkflowSession`Cmdleten startar en session som använder den inbyggda konfigurationen av **Microsoft. PowerShell. Workflow** -sessionen på mål datorn.</span><span class="sxs-lookup"><span data-stu-id="b6841-155">The `New-PSWorkflowSession` cmdlet starts a session that uses the built-in **Microsoft.PowerShell.Workflow** session configuration on the destination computer.</span></span> <span data-ttu-id="b6841-156">I den här konfigurationen ingår skript, typ och formatering av filer samt alternativ som är utformade för arbets flöden.</span><span class="sxs-lookup"><span data-stu-id="b6841-156">This session configuration includes scripts, type and formatting files, and options that are designed for workflows.</span></span>

   <span data-ttu-id="b6841-157">Du kan också använda `New-PSSession` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="b6841-157">Or, use the `New-PSSession` cmdlet.</span></span> <span data-ttu-id="b6841-158">Använd parametern **ConfigurationName** för att ange konfigurationen för **Microsoft. PowerShell. Workflow** -sessionen.</span><span class="sxs-lookup"><span data-stu-id="b6841-158">Use the **ConfigurationName** parameter to specify the **Microsoft.PowerShell.Workflow** session configuration.</span></span> <span data-ttu-id="b6841-159">Det här kommandot är detsamma som att använda- `New-PSWorkflowSession` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="b6841-159">This command is the same as using the `New-PSWorkflowSession` cmdlet.</span></span>

   <span data-ttu-id="b6841-160">Ett alternativ är att använda `New-PSSession` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="b6841-160">An alternative is to use the `New-PSSession` cmdlet.</span></span> <span data-ttu-id="b6841-161">Använd parametern **ConfigurationName** för att ange konfigurationen för **Microsoft. PowerShell. Workflow** -sessionen.</span><span class="sxs-lookup"><span data-stu-id="b6841-161">Use the **ConfigurationName** parameter to specify the **Microsoft.PowerShell.Workflow** session configuration.</span></span>

   <span data-ttu-id="b6841-162">På den lokala datorn:</span><span class="sxs-lookup"><span data-stu-id="b6841-162">On the local computer:</span></span>

   ```powershell
   $ws = New-PSWorkflowSession
   ```

   <span data-ttu-id="b6841-163">På en fjärrdator:</span><span class="sxs-lookup"><span data-stu-id="b6841-163">On a remote computer:</span></span>

   ```powershell
   $ws = New-PSWorkflowSession -ComputerName Server01 `
   -Credential Domain01\Admin01
   ```

   <span data-ttu-id="b6841-164">Om du är administratör på arbets flödes sessionen kan du använda `New-PSWorkflowExecutionOption` cmdleten för att skapa anpassade alternativ inställningar för konfigurationen av arbets flödets session.</span><span class="sxs-lookup"><span data-stu-id="b6841-164">If you are an Administrator on the workflow session computer, you can use the `New-PSWorkflowExecutionOption` cmdlet to create custom option settings for the workflow session configuration.</span></span> <span data-ttu-id="b6841-165">Och Använd `Set-PSSessionConfiguration` cmdleten för att ändra konfigurationen för sessionen.</span><span class="sxs-lookup"><span data-stu-id="b6841-165">And, use the `Set-PSSessionConfiguration` cmdlet to change the session configuration.</span></span>

   ```powershell
   $sto = New-PSWorkflowExecutionOption -MaxConnectedSessions 150
   Invoke-Command -ComputerName Server01 `
   {Set-PSSessionConfiguration Microsoft.PowerShell.Workflow `
   -SessionTypeOption $Using:sto}
   $ws = New-PSWorkflowSession -ComputerName Server01 `
   -Credential Domain01\Admin01
   ```

1. <span data-ttu-id="b6841-166">Kör arbets flödet i arbets flödes sessionen.</span><span class="sxs-lookup"><span data-stu-id="b6841-166">Run the workflow in the workflow session.</span></span> <span data-ttu-id="b6841-167">Om du vill ange namnen på de hanterade noderna, mål datorerna använder du **PSComputerName** arbets flödets gemensamma parameter.</span><span class="sxs-lookup"><span data-stu-id="b6841-167">To specify the names of the managed nodes, target computers, use the **PSComputerName** workflow common parameter.</span></span>

   <span data-ttu-id="b6841-168">Följande exempel kör arbets flödet med namnet **test-Workflow**.</span><span class="sxs-lookup"><span data-stu-id="b6841-168">The following examples run the workflow named **Test-Workflow**.</span></span>

   <span data-ttu-id="b6841-169">Där den hanterade noden är den dator som är värd för arbets flödes sessionen:</span><span class="sxs-lookup"><span data-stu-id="b6841-169">Where the managed node is the computer that hosts the workflow session:</span></span>

   ```powershell
   Invoke-Command -Session $ws {Test-Workflow}
   ```

   <span data-ttu-id="b6841-170">Var de hanterade noderna är fjärrdatorer.</span><span class="sxs-lookup"><span data-stu-id="b6841-170">Where the managed nodes are remote computers.</span></span>

   ```powershell
   Invoke-Command -Session $ws{
   Test-Workflow -PSComputerName Server01, Server02 }
   ```

   <span data-ttu-id="b6841-171">I följande exempel körs **test-Workflow** på hundratals datorer.</span><span class="sxs-lookup"><span data-stu-id="b6841-171">The following example runs the **Test-Workflow** on hundreds of computers.</span></span> <span data-ttu-id="b6841-172">`Get-Content`Cmdlet: en hämtar dator namnen från en textfil och sparar dem i `$Servers` variabeln på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="b6841-172">The `Get-Content` cmdlet gets the computer names from a text file and saves them in the `$Servers` variable on the local computer.</span></span>

   <span data-ttu-id="b6841-173">`Invoke-Command` använder `$Using` omfångs modifieraren för att definiera `$Servers` variabeln i den lokala sessionen.</span><span class="sxs-lookup"><span data-stu-id="b6841-173">`Invoke-Command` uses the `$Using` scope modifier to define the `$Servers` variable in the local session.</span></span> <span data-ttu-id="b6841-174">Mer information om `$Using` omfångs modifieraren finns i [about_Remote_Variables](../../Microsoft.PowerShell.Core/About/about_Remote_Variables.md).</span><span class="sxs-lookup"><span data-stu-id="b6841-174">For more information about the `$Using` scope modifier, see [about_Remote_Variables](../../Microsoft.PowerShell.Core/About/about_Remote_Variables.md).</span></span>

   ```powershell
   $Servers = Get-Content Servers.txt
   Invoke-Command -Session $ws {Test-Workflow -PSComputerName $Using:Servers }
   ```

## <a name="using-workflow-common-parameters"></a><span data-ttu-id="b6841-175">Använda gemensamma parametrar för arbets flöde</span><span class="sxs-lookup"><span data-stu-id="b6841-175">Using workflow common parameters</span></span>

<span data-ttu-id="b6841-176">De gemensamma parametrarna för arbets flödet är en uppsättning parametrar som PowerShell automatiskt lägger till i alla arbets flöden.</span><span class="sxs-lookup"><span data-stu-id="b6841-176">The workflow common parameters are a set of parameters that PowerShell adds automatically to all workflows.</span></span> <span data-ttu-id="b6841-177">PowerShell lägger till cmdlets vanliga parametrar i alla arbets flöden, även om arbets flödet inte använder attributet **CmdletBinding** .</span><span class="sxs-lookup"><span data-stu-id="b6841-177">PowerShell adds the cmdlet common parameters to all workflows, even if the workflow doesn't use the **CmdletBinding** attribute.</span></span>

<span data-ttu-id="b6841-178">Följande arbets flöde definierar till exempel inga parametrar.</span><span class="sxs-lookup"><span data-stu-id="b6841-178">For example, the following workflow defines no parameters.</span></span> <span data-ttu-id="b6841-179">Men när du kör arbets flödet har det både **CommonParameters** och **WorkflowCommonParameters**.</span><span class="sxs-lookup"><span data-stu-id="b6841-179">However, when you run the workflow, it has both the **CommonParameters** and **WorkflowCommonParameters**.</span></span>

```powershell
workflow Test-Workflow {Get-Process}
Get-Command Test-Workflow -Syntax
```

```powershell
Test-Workflow [<WorkflowCommonParameters>] [<CommonParameters>]
```

<span data-ttu-id="b6841-180">Arbets flödets gemensamma parametrar innehåller flera parametrar som är nödvändiga för att köra arbets flöden.</span><span class="sxs-lookup"><span data-stu-id="b6841-180">The workflow common parameters include several parameters that are essential to running workflows.</span></span> <span data-ttu-id="b6841-181">Den gemensamma parametern **PSComputerName** anger till exempel de hanterade noder som arbets flödet påverkar.</span><span class="sxs-lookup"><span data-stu-id="b6841-181">For example, the **PSComputerName** common parameter specifies the managed nodes that the workflow affects.</span></span>

```powershell
Invoke-Command -Session $ws {
  Test-Workflow -PSComputerName Server01, Server02
}
```

<span data-ttu-id="b6841-182">Den gemensamma **PSPersist** -parametern för arbets flödet avgör när arbets flödes data sparas.</span><span class="sxs-lookup"><span data-stu-id="b6841-182">The **PSPersist** workflow common parameter determines when workflow data is persisted.</span></span> <span data-ttu-id="b6841-183">Du kan lägga till persistence mellan aktiviteter i arbets flöden som inte definierar beständiga punkter.</span><span class="sxs-lookup"><span data-stu-id="b6841-183">It enables you to add persistence point between activities to workflows that don't define persistence points.</span></span>

```powershell
Invoke-Command -Session $ws {
  Test-Workflow -PSComputerName Server01, Server02 -PSPersist:$True
}
```

<span data-ttu-id="b6841-184">I andra gemensamma parametrar för arbets flöde kan du ange egenskaperna för fjärr anslutningen till de hanterade noderna.</span><span class="sxs-lookup"><span data-stu-id="b6841-184">Other workflow common parameters let you specify the characteristics of the remote connection to the managed nodes.</span></span> <span data-ttu-id="b6841-185">Deras namn och funktionalitet liknar parametrarna för fjärr-cmdletar, inklusive `Invoke-Command` .</span><span class="sxs-lookup"><span data-stu-id="b6841-185">Their names and functionality are similar to the parameters of remoting cmdlets, including `Invoke-Command`.</span></span>

```powershell
Invoke-Command -Session $ws {
  Test-Workflow -PSComputerName Server01, Server02 -PSPort 443
}
```

<span data-ttu-id="b6841-186">Se till att skilja på de parametrar för fjärr anslutning som definierar anslutningen till arbets flödes sessionen från de gemensamma parametrarna **PS-prefixed** Workflow som definierar anslutningen till de hanterade noderna.</span><span class="sxs-lookup"><span data-stu-id="b6841-186">Take care to distinguish the remoting parameters that define the connection for the workflow session from the **PS-prefixed** workflow common parameters that define the connection to the managed nodes.</span></span>

```powershell
$ws = New-PSSession -ComputerName Server01 -ConfigurationName Microsoft.PowerShell.Workflow

Invoke-Command -Session $ws {
  Test-Workflow -PSComputerName Server01, Server02 -PSConfigurationName Microsoft.PowerShell.Workflow
}
```

<span data-ttu-id="b6841-187">Vissa gemensamma parametrar för arbets flödet är unika för arbets flöden, till exempel parametern **PSParameterCollection** som gör att du kan ange olika parameter värden för olika arbets flöden för olika fjärrnoder.</span><span class="sxs-lookup"><span data-stu-id="b6841-187">Some workflow common parameters are unique to workflows, such as the **PSParameterCollection** parameter that lets you specify different workflow common parameter values for different remote nodes.</span></span> <span data-ttu-id="b6841-188">En lista och beskrivning av de gemensamma parametrarna för arbets flödet finns i [about_WorkflowCommonParameters](about_WorkflowCommonParameters.md).</span><span class="sxs-lookup"><span data-stu-id="b6841-188">For a list and description of the workflow common parameters, see [about_WorkflowCommonParameters](about_WorkflowCommonParameters.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="b6841-189">Se även</span><span class="sxs-lookup"><span data-stu-id="b6841-189">See also</span></span>

[<span data-ttu-id="b6841-190">Invoke-arbetsflöde</span><span class="sxs-lookup"><span data-stu-id="b6841-190">Invoke-AsWorkflow</span></span>](xref:PSWorkflowUtility.Invoke-AsWorkflow)

[<span data-ttu-id="b6841-191">New-PSSession</span><span class="sxs-lookup"><span data-stu-id="b6841-191">New-PSSession</span></span>](xref:Microsoft.PowerShell.Core.New-PSSession)

<span data-ttu-id="b6841-192">[PSWorkflow](xref:PSWorkflow) -cmdletar</span><span class="sxs-lookup"><span data-stu-id="b6841-192">[PSWorkflow](xref:PSWorkflow) cmdlets</span></span>

[<span data-ttu-id="b6841-193">Arbetsflödesguiden</span><span class="sxs-lookup"><span data-stu-id="b6841-193">Workflows Guide</span></span>](/previous-versions/powershell/scripting/components/workflows-guide)

[<span data-ttu-id="b6841-194">Skriva ett Windows PowerShell-arbetsflöde</span><span class="sxs-lookup"><span data-stu-id="b6841-194">Writing a Windows PowerShell Workflow</span></span>](/previous-versions/powershell/scripting/developer/workflow/writing-a-windows-powershell-workflow)
