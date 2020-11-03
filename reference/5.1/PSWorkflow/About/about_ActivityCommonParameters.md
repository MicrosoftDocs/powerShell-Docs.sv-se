---
description: Beskriver de parametrar som Windows PowerShell-arbetsflöde lägger till i aktiviteter.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psworkflow/about/about_activitycommonparameters?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_ActivityCommonParameters
ms.openlocfilehash: b745bf17e4ae26156042ecdc25211830177bc692
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/13/2020
ms.locfileid: "93270962"
---
# <a name="about-activitycommonparameters"></a><span data-ttu-id="467f1-104">Om ActivityCommonParameters</span><span class="sxs-lookup"><span data-stu-id="467f1-104">About ActivityCommonParameters</span></span>

## <a name="short-description"></a><span data-ttu-id="467f1-105">KORT BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="467f1-105">SHORT DESCRIPTION</span></span>

<span data-ttu-id="467f1-106">Beskriver de parametrar som Windows PowerShell-arbetsflöde lägger till i aktiviteter.</span><span class="sxs-lookup"><span data-stu-id="467f1-106">Describes the parameters that Windows PowerShell Workflow adds to activities.</span></span>

## <a name="long-description"></a><span data-ttu-id="467f1-107">LÅNG BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="467f1-107">LONG DESCRIPTION</span></span>

<span data-ttu-id="467f1-108">Windows PowerShell-arbetsflöde lägger till de gemensamma aktivitets parametrarna i aktiviteter som härleds från Bask Lassen för PSActivity.</span><span class="sxs-lookup"><span data-stu-id="467f1-108">Windows PowerShell Workflow adds the activity common parameters to activities that are derived from the PSActivity base class.</span></span> <span data-ttu-id="467f1-109">Den här kategorin omfattar InlineScript-aktiviteten och Windows PowerShell-cmdletar som implementeras som aktiviteter, till exempel Get-Process och get-WinEvent.</span><span class="sxs-lookup"><span data-stu-id="467f1-109">This category includes the InlineScript activity and Windows PowerShell cmdlets that are implemented as activities, such as Get-Process and Get-WinEvent.</span></span>

<span data-ttu-id="467f1-110">De gemensamma aktivitets parametrarna är inte giltiga på Suspend-Workflow och Checkpoint-Workflow aktiviteter och de läggs inte till i cmdletar eller uttryck som Windows PowerShell-arbetsflöde körs automatiskt i ett InlineScript-skript block eller liknande aktivitet.</span><span class="sxs-lookup"><span data-stu-id="467f1-110">The activity common parameters are not valid on the Suspend-Workflow and Checkpoint-Workflow activities and they are not added to cmdlets or expressions that Windows PowerShell Workflow automatically runs in an InlineScript script block or similar activity.</span></span> <span data-ttu-id="467f1-111">De gemensamma aktivitets parametrarna är tillgängliga på InlineScript-aktiviteten, men inte på kommandon i InlineScript-skript blocket.</span><span class="sxs-lookup"><span data-stu-id="467f1-111">The activity common parameters are available on the InlineScript activity, but not on commands in the InlineScript script block.</span></span>

<span data-ttu-id="467f1-112">Flera av de gemensamma aktivitets parametrarna är också gemensamma arbets flödes parametrar eller vanliga parametrar för Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="467f1-112">Several of the activity common parameters are also workflow common parameters or Windows PowerShell common parameters.</span></span> <span data-ttu-id="467f1-113">Andra gemensamma aktivitets parametrar är unika för aktiviteter.</span><span class="sxs-lookup"><span data-stu-id="467f1-113">Other activity common parameters are unique to activities.</span></span>

<span data-ttu-id="467f1-114">Information om gemensamma parametrar för arbets flöden finns i about_WorkflowCommonParameters.</span><span class="sxs-lookup"><span data-stu-id="467f1-114">For information about the workflow common parameters, see about_WorkflowCommonParameters.</span></span> <span data-ttu-id="467f1-115">Information om vanliga Windows PowerShell-parametrar finns about_CommonParameters.</span><span class="sxs-lookup"><span data-stu-id="467f1-115">For information about the Windows PowerShell common parameters, see about_CommonParameters.</span></span>

### <a name="list-of-activity-common-parameters"></a><span data-ttu-id="467f1-116">LISTA ÖVER GEMENSAMMA AKTIVITETS PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="467f1-116">LIST OF ACTIVITY COMMON PARAMETERS</span></span>

```
AppendOutput                      PSDebug
Debug                             PSDisableSerialization
DisplayName                       PSDisableSerializationPreference
ErrorAction                       PSError
Input                             PSPersist
MergeErrorToOutput                PSPort
PSActionRetryCount                PSProgress
PSActionRetryIntervalSec          PSProgressMessage
PSActionRunningTimeoutSec         PSRemotingBehavior
PSApplicationName                 PSRequiredModules
PSAuthentication                  PSSessionOption
PSCertificateThumbprint           PSUseSSL
PSComputerName                    PSVerbose
PSConfigurationName               PSWarning
PSConnectionRetryCount            Result
PSConnectionRetryIntervalSec      UseDefaultInput
PSConnectionURI                   Verbose
PSCredential                      WarningAction
```

### <a name="parameter-descriptions"></a><span data-ttu-id="467f1-117">PARAMETER BESKRIVNINGAR</span><span class="sxs-lookup"><span data-stu-id="467f1-117">PARAMETER DESCRIPTIONS</span></span>

<span data-ttu-id="467f1-118">I det här avsnittet beskrivs gemensamma aktivitets parametrar.</span><span class="sxs-lookup"><span data-stu-id="467f1-118">This section describes the activity common parameters.</span></span>

#### <a name="appendoutput-boolean"></a><span data-ttu-id="467f1-119">AppendOutput \<Boolean\></span><span class="sxs-lookup"><span data-stu-id="467f1-119">AppendOutput \<Boolean\></span></span>

<span data-ttu-id="467f1-120">Värdet `$True` lägger till utdata för aktiviteten till värdet för variabeln.</span><span class="sxs-lookup"><span data-stu-id="467f1-120">A value of `$True` adds the output of the activity to the value of the variable.</span></span>
<span data-ttu-id="467f1-121">Värdet `$False` har ingen påverkan.</span><span class="sxs-lookup"><span data-stu-id="467f1-121">A value of `$False` has no effect.</span></span> <span data-ttu-id="467f1-122">Som standard ersätter variabeln värdet variabeln genom att tilldela ett värde till en variabel.</span><span class="sxs-lookup"><span data-stu-id="467f1-122">By default, assigning a value to a variable replaces the variable value.</span></span>

<span data-ttu-id="467f1-123">Följande kommandon lägger till exempel till ett process objekt till serviceobjektet i `$x` variabeln.</span><span class="sxs-lookup"><span data-stu-id="467f1-123">For example, the following commands add a process object to the service object in the `$x` variable.</span></span>

```powershell
Workflow Test-Workflow
{
    $x = Get-Service
    $x = Get-Process -AppendOutput $true
}
```

<span data-ttu-id="467f1-124">Den här parametern är utformad för XAML-baserade arbets flöden.</span><span class="sxs-lookup"><span data-stu-id="467f1-124">This parameter is designed for XAML-based workflows.</span></span> <span data-ttu-id="467f1-125">I skript arbets flöden kan du också använda operatorn + = tilldelning för att lägga till utdata till värdet för en variabel, som du ser i följande exempel.</span><span class="sxs-lookup"><span data-stu-id="467f1-125">In script workflows, you can also use the += assignment operator to add output to the value of a variable, as shown in the following example.</span></span>

```powershell
Workflow Test-Workflow
{
    $x = Get-Service
    $x += Get-Process
}
```

#### <a name="debug-switchparameter"></a><span data-ttu-id="467f1-126">Förbigå \<SwitchParameter\></span><span class="sxs-lookup"><span data-stu-id="467f1-126">Debug \<SwitchParameter\></span></span>

<span data-ttu-id="467f1-127">Visar information om program nivå om den åtgärd som utförs av kommandot.</span><span class="sxs-lookup"><span data-stu-id="467f1-127">Displays programmer-level detail about the operation performed by the command.</span></span>
<span data-ttu-id="467f1-128">Parametern debug åsidosätter värdet för variabeln $DebugPreference för det aktuella kommandot.</span><span class="sxs-lookup"><span data-stu-id="467f1-128">The Debug parameter overrides the value of the $DebugPreference variable for the current command.</span></span> <span data-ttu-id="467f1-129">Den här parametern fungerar bara när kommandot genererar fel söknings meddelanden.</span><span class="sxs-lookup"><span data-stu-id="467f1-129">This parameter works only when the command generates debugging messages.</span></span> <span data-ttu-id="467f1-130">Den här parametern är också en gemensam Windows PowerShell-parameter.</span><span class="sxs-lookup"><span data-stu-id="467f1-130">This parameter is also a Windows PowerShell common parameter.</span></span>

#### <a name="displayname-string"></a><span data-ttu-id="467f1-131">DisplayName \<String\></span><span class="sxs-lookup"><span data-stu-id="467f1-131">DisplayName \<String\></span></span>

<span data-ttu-id="467f1-132">Anger ett eget namn för aktiviteten.</span><span class="sxs-lookup"><span data-stu-id="467f1-132">Specifies a friendly name for the activity.</span></span> <span data-ttu-id="467f1-133">Värdet DisplayName visas i förlopps indikatorn medan arbets flödet körs och i värdet för egenskapen Progress i arbets flödes jobbet.</span><span class="sxs-lookup"><span data-stu-id="467f1-133">The DisplayName value appears in the progress bar while the workflow runs and in the value of the Progress property of the workflow job.</span></span> <span data-ttu-id="467f1-134">När PSProgressMessage-parametern också ingår i kommandot visas förlopps indikatorns innehåll i \<DisplayName\> : \<PSProgressMessage\> format.</span><span class="sxs-lookup"><span data-stu-id="467f1-134">When the PSProgressMessage parameter is also included in the command, the progress bar content appears in \<DisplayName\>:\<PSProgressMessage\> format.</span></span>

#### <a name="erroraction-actionpreference"></a><span data-ttu-id="467f1-135">ErrorAction \<ActionPreference\></span><span class="sxs-lookup"><span data-stu-id="467f1-135">ErrorAction \<ActionPreference\></span></span>

<span data-ttu-id="467f1-136">Anger hur aktiviteten reagerar på ett icke-avslutande fel från kommandot.</span><span class="sxs-lookup"><span data-stu-id="467f1-136">Determines how the activity responds to a non-terminating error from the command.</span></span> <span data-ttu-id="467f1-137">Det har ingen inverkan på avslutnings fel.</span><span class="sxs-lookup"><span data-stu-id="467f1-137">It has no effect on termination errors.</span></span> <span data-ttu-id="467f1-138">Den här parametern fungerar bara när kommandot genererar ett icke-avslutande fel, till exempel från Write-Error-cmdleten.</span><span class="sxs-lookup"><span data-stu-id="467f1-138">This parameter works only when the command generates a non-terminating error, such as those from the Write-Error cmdlet.</span></span> <span data-ttu-id="467f1-139">Parametern ErrorAction åsidosätter värdet för variabeln $ErrorActionPreference för det aktuella kommandot.</span><span class="sxs-lookup"><span data-stu-id="467f1-139">The ErrorAction parameter overrides the value of the $ErrorActionPreference variable for the current command.</span></span> <span data-ttu-id="467f1-140">Den här parametern är också en gemensam Windows PowerShell-parameter.</span><span class="sxs-lookup"><span data-stu-id="467f1-140">This parameter is also a Windows PowerShell common parameter.</span></span>

<span data-ttu-id="467f1-141">Giltiga värden:</span><span class="sxs-lookup"><span data-stu-id="467f1-141">Valid values:</span></span>

- <span data-ttu-id="467f1-142">Bestå.</span><span class="sxs-lookup"><span data-stu-id="467f1-142">Continue.</span></span> <span data-ttu-id="467f1-143">Visar fel meddelandet och fortsätter att köra kommandot.</span><span class="sxs-lookup"><span data-stu-id="467f1-143">Displays the error message and continues executing the command.</span></span> <span data-ttu-id="467f1-144">"Fortsätt" är standardvärdet.</span><span class="sxs-lookup"><span data-stu-id="467f1-144">"Continue" is the default value.</span></span>

- <span data-ttu-id="467f1-145">Ignorera.</span><span class="sxs-lookup"><span data-stu-id="467f1-145">Ignore.</span></span> <span data-ttu-id="467f1-146">Ignorerar fel meddelandet och fortsätter att köra kommandot.</span><span class="sxs-lookup"><span data-stu-id="467f1-146">Suppresses the error message and continues executing the command.</span></span>
  <span data-ttu-id="467f1-147">Till skillnad från SilentlyContinue lägger ignorera inte till fel meddelandet till den automatiska variabeln $Error.</span><span class="sxs-lookup"><span data-stu-id="467f1-147">Unlike SilentlyContinue, Ignore does not add the error message to the $Error automatic variable.</span></span> <span data-ttu-id="467f1-148">Ignorera-värdet introduceras i Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="467f1-148">The Ignore value is introduced in Windows PowerShell 3.0.</span></span>

- <span data-ttu-id="467f1-149">Inquire.</span><span class="sxs-lookup"><span data-stu-id="467f1-149">Inquire.</span></span> <span data-ttu-id="467f1-150">Visar fel meddelandet och du uppmanas att bekräfta innan du fortsätter körningen.</span><span class="sxs-lookup"><span data-stu-id="467f1-150">Displays the error message and prompts you for confirmation before continuing execution.</span></span> <span data-ttu-id="467f1-151">Det här värdet används sällan.</span><span class="sxs-lookup"><span data-stu-id="467f1-151">This value is rarely used.</span></span>

- <span data-ttu-id="467f1-152">Koppla.</span><span class="sxs-lookup"><span data-stu-id="467f1-152">Suspend.</span></span> <span data-ttu-id="467f1-153">Pausar automatiskt ett arbets flödes jobb för att tillåta ytterligare undersökning.</span><span class="sxs-lookup"><span data-stu-id="467f1-153">Automatically suspends a workflow job to allow for further investigation.</span></span> <span data-ttu-id="467f1-154">Efter undersökningen kan arbets flödet återupptas.</span><span class="sxs-lookup"><span data-stu-id="467f1-154">After investigation, the workflow can be resumed.</span></span>

- <span data-ttu-id="467f1-155">SilentlyContinue.</span><span class="sxs-lookup"><span data-stu-id="467f1-155">SilentlyContinue.</span></span> <span data-ttu-id="467f1-156">Ignorerar fel meddelandet och fortsätter att köra kommandot.</span><span class="sxs-lookup"><span data-stu-id="467f1-156">Suppresses the error message and continues executing the command.</span></span>

- <span data-ttu-id="467f1-157">Stop (Stoppa).</span><span class="sxs-lookup"><span data-stu-id="467f1-157">Stop.</span></span> <span data-ttu-id="467f1-158">Visar fel meddelandet och slutar att köra kommandot.</span><span class="sxs-lookup"><span data-stu-id="467f1-158">Displays the error message and stops executing the command.</span></span>

#### <a name="input-object"></a><span data-ttu-id="467f1-159">Inleveranstransport \<Object[]\></span><span class="sxs-lookup"><span data-stu-id="467f1-159">Input \<Object[]\></span></span>

<span data-ttu-id="467f1-160">Skickar en samling objekt till en aktivitet.</span><span class="sxs-lookup"><span data-stu-id="467f1-160">Submits a collection of objects to an activity.</span></span> <span data-ttu-id="467f1-161">Detta är ett alternativ till att skicka objekt till aktiviteten en i taget.</span><span class="sxs-lookup"><span data-stu-id="467f1-161">This is an alternative to piping objects to the activity one at a time.</span></span>

#### <a name="mergeerrortooutput-boolean"></a><span data-ttu-id="467f1-162">MergeErrorToOutput \<Boolean\></span><span class="sxs-lookup"><span data-stu-id="467f1-162">MergeErrorToOutput \<Boolean\></span></span>

<span data-ttu-id="467f1-163">Värdet `$True` lägger till fel i utdataströmmen.</span><span class="sxs-lookup"><span data-stu-id="467f1-163">A value of `$True` adds errors to the output stream.</span></span> <span data-ttu-id="467f1-164">Värdet `$False` har inte påverkats.</span><span class="sxs-lookup"><span data-stu-id="467f1-164">A value of `$False` has not effect.</span></span> <span data-ttu-id="467f1-165">Använd den här parametern med Parallel och `ForEach -Parallel` keywords för att samla in fel och utdata från flera parallella kommandon i en enda samling.</span><span class="sxs-lookup"><span data-stu-id="467f1-165">Use this parameter with the Parallel and `ForEach -Parallel` keywords to collect errors and output from multiple parallel commands in a single collection.</span></span>

#### <a name="psactionretrycount-int32"></a><span data-ttu-id="467f1-166">PSActionRetryCount \<Int32\></span><span class="sxs-lookup"><span data-stu-id="467f1-166">PSActionRetryCount \<Int32\></span></span>

<span data-ttu-id="467f1-167">Försök upprepade gånger att köra aktiviteten om det första försöket Miss lyckas.</span><span class="sxs-lookup"><span data-stu-id="467f1-167">Tries repeatedly to run the activity if the first attempt fails.</span></span> <span data-ttu-id="467f1-168">Standardvärdet 0, försöker inte igen.</span><span class="sxs-lookup"><span data-stu-id="467f1-168">The default value, 0, does not retry.</span></span>

#### <a name="psactionretryintervalsec-int32"></a><span data-ttu-id="467f1-169">PSActionRetryIntervalSec \<Int32\></span><span class="sxs-lookup"><span data-stu-id="467f1-169">PSActionRetryIntervalSec \<Int32\></span></span>

<span data-ttu-id="467f1-170">Anger intervallet mellan åtgärds försök i sekunder.</span><span class="sxs-lookup"><span data-stu-id="467f1-170">Determines the interval between action retries in seconds.</span></span> <span data-ttu-id="467f1-171">Standardvärdet, 0, gör om åtgärden omedelbart.</span><span class="sxs-lookup"><span data-stu-id="467f1-171">The default value, 0, retries the action immediately.</span></span> <span data-ttu-id="467f1-172">Den här parametern är endast giltig om parametern PSActionRetryCount också används i kommandot.</span><span class="sxs-lookup"><span data-stu-id="467f1-172">This parameter is valid only when the PSActionRetryCount parameter is also used in the command.</span></span>

#### <a name="psactionrunningtimeoutsec-int32"></a><span data-ttu-id="467f1-173">PSActionRunningTimeoutSec \<Int32\></span><span class="sxs-lookup"><span data-stu-id="467f1-173">PSActionRunningTimeoutSec \<Int32\></span></span>

<span data-ttu-id="467f1-174">Anger hur länge aktiviteten kan köras på varje måldator.</span><span class="sxs-lookup"><span data-stu-id="467f1-174">Determines how long the activity can run on each target computer.</span></span> <span data-ttu-id="467f1-175">Om aktiviteten inte slutförs innan tids gränsen löper ut genererar Windows PowerShell-arbetsflöde ett avslutande fel och stoppar bearbetningen av arbets flödet på den berörda mål datorn.</span><span class="sxs-lookup"><span data-stu-id="467f1-175">If the activity does not complete before the timeout expires, Windows PowerShell Workflow generates a terminating error and stops processing the workflow on the affected target computer.</span></span>

#### <a name="psallowredirection-boolean"></a><span data-ttu-id="467f1-176">PSAllowRedirection \<Boolean\></span><span class="sxs-lookup"><span data-stu-id="467f1-176">PSAllowRedirection \<Boolean\></span></span>

<span data-ttu-id="467f1-177">Värdet $True tillåter omdirigering av anslutningen till mål datorerna.</span><span class="sxs-lookup"><span data-stu-id="467f1-177">A value of $True allows redirection of the connection to the target computers.</span></span>
<span data-ttu-id="467f1-178">Värdet $False har ingen påverkan.</span><span class="sxs-lookup"><span data-stu-id="467f1-178">A value of $False has no effect.</span></span> <span data-ttu-id="467f1-179">Den gemensamma aktivitets parametern är också en gemensam arbets flödes parameter.</span><span class="sxs-lookup"><span data-stu-id="467f1-179">This activity common parameter is also a workflow common parameter.</span></span>

<span data-ttu-id="467f1-180">När du använder PSConnectionURI-parametern kan fjärrdestinationen returnera en instruktion för att omdirigera till en annan URI.</span><span class="sxs-lookup"><span data-stu-id="467f1-180">When you use the PSConnectionURI parameter, the remote destination can return an instruction to redirect to a different URI.</span></span> <span data-ttu-id="467f1-181">Som standard omdirigerar Windows PowerShell inte anslutningar, men du kan använda parametern PSAllowRedirection med värdet $True för att tillåta omdirigering av anslutningen till mål datorn.</span><span class="sxs-lookup"><span data-stu-id="467f1-181">By default, Windows PowerShell does not redirect connections, but you can use the PSAllowRedirection parameter with a value of $True to allow redirection of the connection to the target computer.</span></span>

<span data-ttu-id="467f1-182">Du kan också begränsa antalet gånger som anslutningen ska omdirigeras genom att ange egenskapen MaximumConnectionRedirectionCount för `$PSSessionOption` variabeln Preference, eller egenskapen MaximumConnectionRedirectionCount för värdet för parametern SSessionOption för cmdletar som skapar en session.</span><span class="sxs-lookup"><span data-stu-id="467f1-182">You can also limit the number of times that the connection is redirected by setting the MaximumConnectionRedirectionCount property of the `$PSSessionOption` preference variable, or the MaximumConnectionRedirectionCount property of the value of the SSessionOption parameter of cmdlets that create a session.</span></span> <span data-ttu-id="467f1-183">Standardvärdet är 5.</span><span class="sxs-lookup"><span data-stu-id="467f1-183">The default value is 5.</span></span>

#### <a name="psapplicationname-string"></a><span data-ttu-id="467f1-184">PSApplicationName \<String\></span><span class="sxs-lookup"><span data-stu-id="467f1-184">PSApplicationName \<String\></span></span>

<span data-ttu-id="467f1-185">Anger program namns segmentet för den anslutnings-URI som används för att ansluta till mål datorerna.</span><span class="sxs-lookup"><span data-stu-id="467f1-185">Specifies the application name segment of the connection URI that is used to connect to the target computers.</span></span> <span data-ttu-id="467f1-186">Använd den här parametern för att ange program namnet när du inte använder parametern ConnectionURI i kommandot.</span><span class="sxs-lookup"><span data-stu-id="467f1-186">Use this parameter to specify the application name when you are not using the ConnectionURI parameter in the command.</span></span> <span data-ttu-id="467f1-187">Den gemensamma aktivitets parametern är också en gemensam arbets flödes parameter.</span><span class="sxs-lookup"><span data-stu-id="467f1-187">This activity common parameter is also a workflow common parameter.</span></span>

<span data-ttu-id="467f1-188">Standardvärdet är värdet för Preference- `$PSSessionApplicationName` variabeln på mål datorn.</span><span class="sxs-lookup"><span data-stu-id="467f1-188">The default value is the value of the `$PSSessionApplicationName` preference variable on the target computer.</span></span> <span data-ttu-id="467f1-189">Om den här preferens variabeln inte definieras är standardvärdet WSMAN.</span><span class="sxs-lookup"><span data-stu-id="467f1-189">If this preference variable is not defined, the default value is WSMAN.</span></span> <span data-ttu-id="467f1-190">Det här värdet är lämpligt för de flesta användnings områden.</span><span class="sxs-lookup"><span data-stu-id="467f1-190">This value is appropriate for most uses.</span></span> <span data-ttu-id="467f1-191">Mer information finns i [about_Preference_Variables](../../Microsoft.PowerShell.Core/About/about_Preference_Variables.md).</span><span class="sxs-lookup"><span data-stu-id="467f1-191">For more information, see [about_Preference_Variables](../../Microsoft.PowerShell.Core/About/about_Preference_Variables.md).</span></span>

<span data-ttu-id="467f1-192">WinRM-tjänsten använder program namnet för att välja en lyssnare som ska betjäna anslutningsbegäran.</span><span class="sxs-lookup"><span data-stu-id="467f1-192">The WinRM service uses the application name to select a listener to service the connection request.</span></span> <span data-ttu-id="467f1-193">Värdet för den här parametern ska matcha värdet på egenskapen URLPrefix för en lyssnare på fjärrdatorn.</span><span class="sxs-lookup"><span data-stu-id="467f1-193">The value of this parameter should match the value of the URLPrefix property of a listener on the remote computer.</span></span>

#### <a name="psauthentication-authenticationmechanism"></a><span data-ttu-id="467f1-194">PSAuthentication \<AuthenticationMechanism\></span><span class="sxs-lookup"><span data-stu-id="467f1-194">PSAuthentication \<AuthenticationMechanism\></span></span>

<span data-ttu-id="467f1-195">Anger den mekanism som används för att autentisera användarens autentiseringsuppgifter vid anslutning till mål datorerna.</span><span class="sxs-lookup"><span data-stu-id="467f1-195">Specifies the mechanism that is used to authenticate the user's credentials when connecting to the target computers.</span></span> <span data-ttu-id="467f1-196">Giltiga värden är standard, Basic, CredSSP, Digest, Kerberos, Negotiate och NegotiateWithImplicitCredential.</span><span class="sxs-lookup"><span data-stu-id="467f1-196">Valid values are Default, Basic, Credssp, Digest, Kerberos, Negotiate, and NegotiateWithImplicitCredential.</span></span> <span data-ttu-id="467f1-197">Standardvärdet är default.</span><span class="sxs-lookup"><span data-stu-id="467f1-197">The default value is Default.</span></span> <span data-ttu-id="467f1-198">Den gemensamma aktivitets parametern är också en gemensam arbets flödes parameter.</span><span class="sxs-lookup"><span data-stu-id="467f1-198">This activity common parameter is also a workflow common parameter.</span></span>

<span data-ttu-id="467f1-199">Information om värdena för den här parametern finns i beskrivningen av uppräkningen **system. Management. Automation. körnings utrymmen. AuthenticationMechanism** i MSDN.</span><span class="sxs-lookup"><span data-stu-id="467f1-199">For information about the values of this parameter, see the description of the **System.Management.Automation.Runspaces.AuthenticationMechanism** enumeration in MSDN.</span></span>

> [!WARNING]
> <span data-ttu-id="467f1-200">Autentisering av Credential Security Service Provider (CredSSP), där användarens autentiseringsuppgifter skickas till en fjärrdator som ska autentiseras, är utformad för kommandon som kräver autentisering på fler än en resurs, till exempel åtkomst till en fjärran sluten nätverks resurs.</span><span class="sxs-lookup"><span data-stu-id="467f1-200">Credential Security Service Provider (CredSSP) authentication, in which the user's credentials are passed to a remote computer to be authenticated, is designed for commands that require authentication on more than one resource, such as accessing a remote network share.</span></span> <span data-ttu-id="467f1-201">Den här mekanismen ökar säkerhets risken för Fjärråtgärden.</span><span class="sxs-lookup"><span data-stu-id="467f1-201">This mechanism increases the security risk of the remote operation.</span></span> <span data-ttu-id="467f1-202">Om fjärrdatorn har komprometterats kan de autentiseringsuppgifter som skickas till den användas för att kontrol lera nätverks sessionen.</span><span class="sxs-lookup"><span data-stu-id="467f1-202">If the remote computer is compromised, the credentials that are passed to it can be used to control the network session.</span></span>

#### <a name="pscertificatethumbprint-string"></a><span data-ttu-id="467f1-203">PSCertificateThumbprint \<String\></span><span class="sxs-lookup"><span data-stu-id="467f1-203">PSCertificateThumbprint \<String\></span></span>

<span data-ttu-id="467f1-204">Anger X509 (Digital Public Key Certificate) för ett användar konto som har behörighet att utföra den här åtgärden.</span><span class="sxs-lookup"><span data-stu-id="467f1-204">Specifies the digital public key certificate (X509) of a user account that has permission to perform this action.</span></span> <span data-ttu-id="467f1-205">Ange certifikatets tumavtryck.</span><span class="sxs-lookup"><span data-stu-id="467f1-205">Enter the certificate thumbprint of the certificate.</span></span> <span data-ttu-id="467f1-206">Den gemensamma aktivitets parametern är också en gemensam arbets flödes parameter.</span><span class="sxs-lookup"><span data-stu-id="467f1-206">This activity common parameter is also a workflow common parameter.</span></span>

<span data-ttu-id="467f1-207">Certifikat används i klient certifikat-baserad autentisering.</span><span class="sxs-lookup"><span data-stu-id="467f1-207">Certificates are used in client certificate-based authentication.</span></span> <span data-ttu-id="467f1-208">De kan bara mappas till lokala användar konton. de fungerar inte med domän konton.</span><span class="sxs-lookup"><span data-stu-id="467f1-208">They can only be mapped to local user accounts; they do not work with domain accounts.</span></span>

<span data-ttu-id="467f1-209">För att hämta ett certifikat använder du cmdletarna [Get-item](xref:Microsoft.PowerShell.Management.Get-Item) eller [Get-ChildItem](xref:Microsoft.PowerShell.Management.Get-ChildItem) i Windows PowerShell-certifikatet: enhet.</span><span class="sxs-lookup"><span data-stu-id="467f1-209">To get a certificate, use the [Get-Item](xref:Microsoft.PowerShell.Management.Get-Item) or [Get-ChildItem](xref:Microsoft.PowerShell.Management.Get-ChildItem) cmdlets in the Windows PowerShell Cert: drive.</span></span>

#### <a name="pscomputername-string"></a><span data-ttu-id="467f1-210">PSComputerName \<String[]\></span><span class="sxs-lookup"><span data-stu-id="467f1-210">PSComputerName \<String[]\></span></span>

<span data-ttu-id="467f1-211">Anger de mål datorer som aktiviteten körs på.</span><span class="sxs-lookup"><span data-stu-id="467f1-211">Specifies the target computers on which the activity run.</span></span> <span data-ttu-id="467f1-212">Standard är den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="467f1-212">The default is the local computer.</span></span> <span data-ttu-id="467f1-213">Den gemensamma aktivitets parametern är också en gemensam arbets flödes parameter.</span><span class="sxs-lookup"><span data-stu-id="467f1-213">This activity common parameter is also a workflow common parameter.</span></span>

<span data-ttu-id="467f1-214">Ange NETBIOS-namn, IP-adress eller fullständigt kvalificerat domän namn för en eller flera datorer i en kommaavgränsad lista.</span><span class="sxs-lookup"><span data-stu-id="467f1-214">Type the NETBIOS name, IP address, or fully-qualified domain name of one or more computers in a comma-separated list.</span></span> <span data-ttu-id="467f1-215">Om du vill ange den lokala datorn skriver du datorns namn, localhost eller en punkt (.).</span><span class="sxs-lookup"><span data-stu-id="467f1-215">To specify the local computer, type the computer name, "localhost", or a dot (.).</span></span>

<span data-ttu-id="467f1-216">Om du vill inkludera den lokala datorn i värdet för parametern PSComputerName, öppnar du Windows PowerShell med alternativet "kör som administratör".</span><span class="sxs-lookup"><span data-stu-id="467f1-216">To include the local computer in the value of the PSComputerName parameter, open Windows PowerShell with the "Run as administrator" option.</span></span>

<span data-ttu-id="467f1-217">Om den här parametern utelämnas från kommandot, eller om värdet är $null eller en tom sträng, är arbets flödets mål den lokala datorn och Windows PowerShell-fjärrkommunikation används inte för att köra kommandot.</span><span class="sxs-lookup"><span data-stu-id="467f1-217">If this parameter is omitted from the command, or it value is $null or an empty string, the workflow target is the local computer and Windows PowerShell remoting is not used to run the command.</span></span>

<span data-ttu-id="467f1-218">Om du vill använda en IP-adress i värdet för parametern ComputerName måste kommandot innehålla parametern PSCredential.</span><span class="sxs-lookup"><span data-stu-id="467f1-218">To use an IP address in the value of the ComputerName parameter, the command must include the PSCredential parameter.</span></span> <span data-ttu-id="467f1-219">Dessutom måste datorn konfigureras för HTTPS-transport eller fjärrdatorns IP-adress måste ingå i listan WinRM TrustedHosts på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="467f1-219">Also, the computer must be configured for HTTPS transport or the IP address of the remote computer must be included in the WinRM TrustedHosts list on the local computer.</span></span> <span data-ttu-id="467f1-220">Instruktioner för att lägga till ett dator namn i listan TrustedHosts finns i avsnittet om hur du lägger till en dator i listan över betrodda värdar i [about_Remote_Troubleshooting](../../Microsoft.PowerShell.Core/About/about_Remote_Troubleshooting.md).</span><span class="sxs-lookup"><span data-stu-id="467f1-220">For instructions for adding a computer name to the TrustedHosts list, see "How to Add a Computer to the Trusted Host List" in [about_Remote_Troubleshooting](../../Microsoft.PowerShell.Core/About/about_Remote_Troubleshooting.md).</span></span>

#### <a name="psconfigurationname-string"></a><span data-ttu-id="467f1-221">PSConfigurationName \<String\></span><span class="sxs-lookup"><span data-stu-id="467f1-221">PSConfigurationName \<String\></span></span>

<span data-ttu-id="467f1-222">Anger de sessionsinställningar som används för att skapa sessioner på mål datorerna.</span><span class="sxs-lookup"><span data-stu-id="467f1-222">Specifies the session configurations that are used to create sessions on the target computers.</span></span> <span data-ttu-id="467f1-223">Ange namnet på en session konfiguration på mål datorerna (inte på den dator som kör arbets flödet.</span><span class="sxs-lookup"><span data-stu-id="467f1-223">Enter the name of a session configuration on the target computers (not on the computer that is running the workflow.</span></span> <span data-ttu-id="467f1-224">Standardvärdet är Microsoft. PowerShell.</span><span class="sxs-lookup"><span data-stu-id="467f1-224">The default is Microsoft.PowerShell.</span></span> <span data-ttu-id="467f1-225">Den gemensamma aktivitets parametern är också en gemensam arbets flödes parameter.</span><span class="sxs-lookup"><span data-stu-id="467f1-225">This activity common parameter is also a workflow common parameter.</span></span>

#### <a name="psconnectionretrycount-uint"></a><span data-ttu-id="467f1-226">PSConnectionRetryCount \<UInt\></span><span class="sxs-lookup"><span data-stu-id="467f1-226">PSConnectionRetryCount \<UInt\></span></span>

<span data-ttu-id="467f1-227">Anger det maximala antalet försök att ansluta till varje måldator om det första anslutnings försöket Miss lyckas.</span><span class="sxs-lookup"><span data-stu-id="467f1-227">Specifies the maximum number of attempts to connect to each target computer if the first connection attempt fails.</span></span> <span data-ttu-id="467f1-228">Ange ett tal mellan 1 och 4 294 967 295 (UInt. MaxValue).</span><span class="sxs-lookup"><span data-stu-id="467f1-228">Enter a number between 1 and 4,294,967,295 (UInt.MaxValue).</span></span> <span data-ttu-id="467f1-229">Standardvärdet noll (0) representerar inga nya försök.</span><span class="sxs-lookup"><span data-stu-id="467f1-229">The default value, zero (0), represents no retry attempts.</span></span>
<span data-ttu-id="467f1-230">Den gemensamma aktivitets parametern är också en gemensam arbets flödes parameter.</span><span class="sxs-lookup"><span data-stu-id="467f1-230">This activity common parameter is also a workflow common parameter.</span></span>

#### <a name="psconnectionretryintervalsec-uint"></a><span data-ttu-id="467f1-231">PSConnectionRetryIntervalSec \<UInt\></span><span class="sxs-lookup"><span data-stu-id="467f1-231">PSConnectionRetryIntervalSec \<UInt\></span></span>

<span data-ttu-id="467f1-232">Anger fördröjningen mellan anslutnings försök på några sekunder.</span><span class="sxs-lookup"><span data-stu-id="467f1-232">Specifies the delay between connection retry attempts in seconds.</span></span> <span data-ttu-id="467f1-233">Standardvärdet är noll (0).</span><span class="sxs-lookup"><span data-stu-id="467f1-233">The default value is zero (0).</span></span> <span data-ttu-id="467f1-234">Den här parametern är endast giltig när värdet för PSConnectionRetryCount är minst 1.</span><span class="sxs-lookup"><span data-stu-id="467f1-234">This parameter is valid only when the value of PSConnectionRetryCount is at least 1.</span></span> <span data-ttu-id="467f1-235">Den gemensamma aktivitets parametern är också en gemensam arbets flödes parameter.</span><span class="sxs-lookup"><span data-stu-id="467f1-235">This activity common parameter is also a workflow common parameter.</span></span>

#### <a name="psconnectionuri-systemuri"></a><span data-ttu-id="467f1-236">PSConnectionURI \<System.Uri\></span><span class="sxs-lookup"><span data-stu-id="467f1-236">PSConnectionURI \<System.Uri\></span></span>

<span data-ttu-id="467f1-237">Anger en Uniform Resource Identifier (URI) som definierar anslutnings slut punkten för aktiviteten på mål datorn.</span><span class="sxs-lookup"><span data-stu-id="467f1-237">Specifies a Uniform Resource Identifier (URI) that defines the connection endpoint for the activity on the target computer.</span></span> <span data-ttu-id="467f1-238">URI: n måste vara fullständigt kvalificerad.</span><span class="sxs-lookup"><span data-stu-id="467f1-238">The URI must be fully qualified.</span></span> <span data-ttu-id="467f1-239">Den gemensamma aktivitets parametern är också en gemensam arbets flödes parameter.</span><span class="sxs-lookup"><span data-stu-id="467f1-239">This activity common parameter is also a workflow common parameter.</span></span>

<span data-ttu-id="467f1-240">Formatet för den här strängen är följande:</span><span class="sxs-lookup"><span data-stu-id="467f1-240">The format of this string is as follows:</span></span>

```
<Transport>://<ComputerName>:<Port>/<ApplicationName>
```

<span data-ttu-id="467f1-241">Standardvärdet är `http://localhost:5985/WSMAN`.</span><span class="sxs-lookup"><span data-stu-id="467f1-241">The default value is `http://localhost:5985/WSMAN`.</span></span>

<span data-ttu-id="467f1-242">Om du inte anger en PSConnectionURI kan du använda parametrarna PSUseSSL, PSComputerName, PSPort och PSApplicationName för att ange PSConnectionURI-värden.</span><span class="sxs-lookup"><span data-stu-id="467f1-242">If you do not specify a PSConnectionURI, you can use the PSUseSSL, PSComputerName, PSPort, and PSApplicationName parameters to specify the PSConnectionURI values.</span></span>

<span data-ttu-id="467f1-243">Giltiga värden för URI: n i transport segmentet är HTTP och HTTPS.</span><span class="sxs-lookup"><span data-stu-id="467f1-243">Valid values for the Transport segment of the URI are HTTP and HTTPS.</span></span> <span data-ttu-id="467f1-244">Om du anger en anslutnings-URI med ett transport segment, men inte anger någon port, skapas sessionen med standard portar: 80 för HTTP och 443 för HTTPS.</span><span class="sxs-lookup"><span data-stu-id="467f1-244">If you specify a connection URI with a Transport segment, but do not specify a port, the session is created with standards ports: 80 for HTTP and 443 for HTTPS.</span></span> <span data-ttu-id="467f1-245">Om du vill använda standard portarna för Windows PowerShell-fjärrkommunikation, anger du Port 5985 för HTTP eller 5986 för HTTPS.</span><span class="sxs-lookup"><span data-stu-id="467f1-245">To use the default ports for Windows PowerShell remoting, specify port 5985 for HTTP or 5986 for HTTPS.</span></span>

#### <a name="pscredential-pscredential"></a><span data-ttu-id="467f1-246">PSCredential \<PSCredential\></span><span class="sxs-lookup"><span data-stu-id="467f1-246">PSCredential \<PSCredential\></span></span>

<span data-ttu-id="467f1-247">Anger ett användar konto som har behörighet att köra aktiviteten på mål datorn.</span><span class="sxs-lookup"><span data-stu-id="467f1-247">Specifies a user account that has permission to run the activity on the target computer.</span></span> <span data-ttu-id="467f1-248">Standard är den aktuella användaren.</span><span class="sxs-lookup"><span data-stu-id="467f1-248">The default is the current user.</span></span> <span data-ttu-id="467f1-249">Den här parametern är endast giltig om parametern PSComputerName ingår i kommandot.</span><span class="sxs-lookup"><span data-stu-id="467f1-249">This parameter is valid only when the PSComputerName parameter is included in the command.</span></span> <span data-ttu-id="467f1-250">Den gemensamma aktivitets parametern är också en gemensam arbets flödes parameter.</span><span class="sxs-lookup"><span data-stu-id="467f1-250">This activity common parameter is also a workflow common parameter.</span></span>

<span data-ttu-id="467f1-251">Ange ett användar namn, till exempel "user01" eller "Domain01\User01", eller ange en variabel som innehåller ett PSCredential-objekt, till exempel ett som Get-Credential cmdlet returnerar.</span><span class="sxs-lookup"><span data-stu-id="467f1-251">Type a user name, such as "User01" or "Domain01\User01", or enter a variable that contains a PSCredential object, such as one that the Get-Credential cmdlet returns.</span></span> <span data-ttu-id="467f1-252">Om du bara anger ett användar namn uppmanas du att ange ett lösen ord.</span><span class="sxs-lookup"><span data-stu-id="467f1-252">If you enter only a user name, you will be prompted for a password.</span></span>

#### <a name="psdebug-psdatacollectiondebugrecord"></a><span data-ttu-id="467f1-253">PSDebug \<PSDataCollection[DebugRecord]\></span><span class="sxs-lookup"><span data-stu-id="467f1-253">PSDebug \<PSDataCollection[DebugRecord]\></span></span>

<span data-ttu-id="467f1-254">Lägger till fel söknings meddelanden från aktiviteten till den angivna fel söknings post samlingen i stället för att skriva fel söknings meddelandena till konsolen eller till värdet för egenskapen fel sökning för arbets flödes jobbet.</span><span class="sxs-lookup"><span data-stu-id="467f1-254">Adds debug messages from the activity to the specified debug record collection, instead of writing the debug messages to the console or to the value of the Debug property of the workflow job.</span></span> <span data-ttu-id="467f1-255">Du kan lägga till fel söknings meddelanden från flera aktiviteter i samma samlings objekt för fel söknings poster.</span><span class="sxs-lookup"><span data-stu-id="467f1-255">You can add debug messages from multiple activities to the same debug record collection object.</span></span>

<span data-ttu-id="467f1-256">Använd New-Object cmdlet för att skapa ett PSDataCollection-objekt med en typ av DebugRecord och spara objektet i en variabel, om du vill använda den här gemensamma aktivitets parametern.</span><span class="sxs-lookup"><span data-stu-id="467f1-256">To use this activity common parameter, use the New-Object cmdlet to create a PSDataCollection object with a type of DebugRecord and save the object in a variable.</span></span> <span data-ttu-id="467f1-257">Använd sedan variabeln som värde för parametern PSDebug för en eller flera aktiviteter, som du ser i följande exempel.</span><span class="sxs-lookup"><span data-stu-id="467f1-257">Then, use the variable as the value of the PSDebug parameter of one or more activities, as shown in the following example.</span></span>

```powershell
Workflow Test-Workflow
{
    $debugCollection = New-Object -Type `
    System.Management.Automation.PSDataCollection[System.Management.Automation.DebugRecord]
    InlineScript {\Server01\Share01\Get-AssetData.ps1} -PSDebug $debugCollection -Debug $True
    InlineScript {\Server01\Share01\Set-AssetData.ps1} -PSDebug $debugCollection -Debug $True
    if ($debugCollection -like "Missing") { ...}
}
```

#### <a name="psdisableserialization-boolean"></a><span data-ttu-id="467f1-258">PSDisableSerialization \<Boolean\></span><span class="sxs-lookup"><span data-stu-id="467f1-258">PSDisableSerialization \<Boolean\></span></span>

<span data-ttu-id="467f1-259">Dirigerar aktiviteten så att den returnerar "Live"-objekt (inte serialiserade) till arbets flödet.</span><span class="sxs-lookup"><span data-stu-id="467f1-259">Directs the activity to return "live" (not serialized) objects to the workflow.</span></span>
<span data-ttu-id="467f1-260">De resulterande objekten har metoder, samt egenskaper, men de kan inte sparas när en kontroll punkt tas.</span><span class="sxs-lookup"><span data-stu-id="467f1-260">The resulting objects have methods, as well as properties, but they cannot be saved when a checkpoint is taken.</span></span>

#### <a name="psdisableserializationpreference-boolean"></a><span data-ttu-id="467f1-261">PSDisableSerializationPreference \<Boolean\></span><span class="sxs-lookup"><span data-stu-id="467f1-261">PSDisableSerializationPreference \<Boolean\></span></span>

<span data-ttu-id="467f1-262">Tillämpar motsvarande PSDisableSerialization-parameter i hela arbets flödet, inte bara på aktiviteten.</span><span class="sxs-lookup"><span data-stu-id="467f1-262">Applies the equivalent of the PSDisableSerialization parameter to the entire workflow, not just the activity.</span></span> <span data-ttu-id="467f1-263">Det rekommenderas vanligt vis inte att lägga till den här parametern, eftersom ett arbets flöde som inte serialiserar sina objekt inte kan återupptas eller sparas.</span><span class="sxs-lookup"><span data-stu-id="467f1-263">Adding this parameter is generally not recommended, because a workflow that doesn't serialize its objects cannot be resumed or persisted.</span></span>

<span data-ttu-id="467f1-264">Giltiga värden:</span><span class="sxs-lookup"><span data-stu-id="467f1-264">Valid values:</span></span>

- <span data-ttu-id="467f1-265">Objekt Om detta utelämnas och du inte har lagt till parametern PSDisableSerialization i en aktivitet, serialiseras objekten.</span><span class="sxs-lookup"><span data-stu-id="467f1-265">(Default) If omitted, and you have also not added the PSDisableSerialization parameter to an activity, objects are serialized.</span></span>

- <span data-ttu-id="467f1-266">`$True`.</span><span class="sxs-lookup"><span data-stu-id="467f1-266">`$True`.</span></span> <span data-ttu-id="467f1-267">Dirigerar alla aktiviteter i ett arbets flöde för att returnera "Live"-objekt (inte serialiserade).</span><span class="sxs-lookup"><span data-stu-id="467f1-267">Directs all activities within a workflow to return "live" (not serialized) objects.</span></span> <span data-ttu-id="467f1-268">De resulterande objekten har metoder, samt egenskaper, men de kan inte sparas när en kontroll punkt tas.</span><span class="sxs-lookup"><span data-stu-id="467f1-268">The resulting objects have methods, as well as properties, but they cannot be saved when a checkpoint is taken.</span></span>
- <span data-ttu-id="467f1-269">`$False`.</span><span class="sxs-lookup"><span data-stu-id="467f1-269">`$False`.</span></span> <span data-ttu-id="467f1-270">Arbets flödes objekt serialiseras.</span><span class="sxs-lookup"><span data-stu-id="467f1-270">Workflow objects are serialized.</span></span>

#### <a name="pserror-psdatacollectionerrorrecord"></a><span data-ttu-id="467f1-271">PSError \<PSDataCollection[ErrorRecord]\></span><span class="sxs-lookup"><span data-stu-id="467f1-271">PSError \<PSDataCollection[ErrorRecord]\></span></span>

<span data-ttu-id="467f1-272">Lägger till fel meddelanden från aktiviteten till den angivna fel post samlingen, i stället för att skriva fel meddelandena till konsolen eller till värdet för egenskapen Error för arbets flödes jobbet.</span><span class="sxs-lookup"><span data-stu-id="467f1-272">Adds error messages from the activity to the specified error record collection, instead of writing the error messages to the console or to the value of the Error property of the workflow job.</span></span> <span data-ttu-id="467f1-273">Du kan lägga till fel meddelanden från flera aktiviteter i samma fel post samlings objekt.</span><span class="sxs-lookup"><span data-stu-id="467f1-273">You can add error messages from multiple activities to the same error record collection object.</span></span>

<span data-ttu-id="467f1-274">Använd `New-Object` cmdleten för att skapa ett PSDataCollection-objekt med en typ av ErrorRecord och spara objektet i en variabel om du vill använda den här gemensamma parametern för aktiviteten.</span><span class="sxs-lookup"><span data-stu-id="467f1-274">To use this activity common parameter, use the `New-Object` cmdlet to create a PSDataCollection object with a type of ErrorRecord and save the object in a variable.</span></span> <span data-ttu-id="467f1-275">Använd sedan variabeln som värde för parametern PSError för en eller flera aktiviteter, som du ser i följande exempel.</span><span class="sxs-lookup"><span data-stu-id="467f1-275">Then, use the variable as the value of the PSError parameter of one or more activities, as shown in the following example.</span></span>

```powershell
Workflow Test-Workflow
{
   $typeName = "System.Management.Automation.PSDataCollection"
   $typeName += '[System.Management.Automation.ErrorRecord]'
   $ec = New-Object $typeName
   InlineScript {\Server01\Share01\Get-AssetData.ps1} -PSError $ec
   InlineScript {\Server01\Share01\Set-AssetData.ps1} -PSError $ec
   if ($ec.Count -gt 2)
   {
      # Do Some Work.
   }
}
```

#### <a name="pspersist-boolean"></a><span data-ttu-id="467f1-276">PSPersist \<Boolean\></span><span class="sxs-lookup"><span data-stu-id="467f1-276">PSPersist \<Boolean\></span></span>

<span data-ttu-id="467f1-277">Tar en kontroll punkt efter aktiviteten.</span><span class="sxs-lookup"><span data-stu-id="467f1-277">Takes a checkpoint after the activity.</span></span> <span data-ttu-id="467f1-278">Den här kontroll punkten är utöver de kontroll punkter som anges i arbets flödet.</span><span class="sxs-lookup"><span data-stu-id="467f1-278">This checkpoint is in addition to any checkpoints that are specified in the workflow.</span></span> <span data-ttu-id="467f1-279">Den gemensamma aktivitets parametern är också en gemensam arbets flödes parameter.</span><span class="sxs-lookup"><span data-stu-id="467f1-279">This activity common parameter is also a workflow common parameter.</span></span>

<span data-ttu-id="467f1-280">En "kontroll punkt" eller "beständighet" är en ögonblicks bild av arbets flödets tillstånd och data som samlas in medan arbets flödet körs och sparas i ett beständigt arkiv på disk.</span><span class="sxs-lookup"><span data-stu-id="467f1-280">A "checkpoint" or "persistence point" is a snapshot of the workflow state and data that is captured while the workflow runs and is saved to a persistence store on disk.</span></span> <span data-ttu-id="467f1-281">Windows PowerShell-arbetsflöde använder sparade data för att återuppta ett pausat eller avbrutet arbets flöde från den senaste beständiga punkten, i stället för att starta om arbets flödet.</span><span class="sxs-lookup"><span data-stu-id="467f1-281">Windows PowerShell Workflow uses the saved data to resume a suspended or interrupted workflow from the last persistence point, rather than to restart the workflow.</span></span>

<span data-ttu-id="467f1-282">Giltiga värden:</span><span class="sxs-lookup"><span data-stu-id="467f1-282">Valid values:</span></span>

- <span data-ttu-id="467f1-283">Objekt Om du utelämnar den här parametern läggs inga kontroll punkter till.</span><span class="sxs-lookup"><span data-stu-id="467f1-283">(Default) If you omit this parameter, no checkpoints are added.</span></span> <span data-ttu-id="467f1-284">Kontroll punkter utförs baserat på inställningarna för arbets flödet.</span><span class="sxs-lookup"><span data-stu-id="467f1-284">Checkpoints are taken based on the settings for the workflow.</span></span>

- <span data-ttu-id="467f1-285">`$True`.</span><span class="sxs-lookup"><span data-stu-id="467f1-285">`$True`.</span></span> <span data-ttu-id="467f1-286">Tar en kontroll punkt när aktiviteten har slutförts.</span><span class="sxs-lookup"><span data-stu-id="467f1-286">Takes a checkpoint after the activity completes.</span></span>
  <span data-ttu-id="467f1-287">Den här kontroll punkten är utöver de kontroll punkter som anges i arbets flödet.</span><span class="sxs-lookup"><span data-stu-id="467f1-287">This checkpoint is in addition to any checkpoints that are specified in the workflow.</span></span>

- <span data-ttu-id="467f1-288">`$False`.</span><span class="sxs-lookup"><span data-stu-id="467f1-288">`$False`.</span></span> <span data-ttu-id="467f1-289">Inga kontroll punkter har lagts till.</span><span class="sxs-lookup"><span data-stu-id="467f1-289">No checkpoints are added.</span></span> <span data-ttu-id="467f1-290">Kontroll punkter utförs endast när de anges i arbets flödet.</span><span class="sxs-lookup"><span data-stu-id="467f1-290">Checkpoints are taken only when specified in the workflow.</span></span>

#### <a name="psport-int32"></a><span data-ttu-id="467f1-291">PSPort \<Int32\></span><span class="sxs-lookup"><span data-stu-id="467f1-291">PSPort \<Int32\></span></span>

<span data-ttu-id="467f1-292">Anger nätverks porten på mål datorerna.</span><span class="sxs-lookup"><span data-stu-id="467f1-292">Specifies the network port on the target computers.</span></span> <span data-ttu-id="467f1-293">Standard portarna är 5985 (WinRM-porten för HTTP) och 5986 (WinRM-porten för HTTPS).</span><span class="sxs-lookup"><span data-stu-id="467f1-293">The default ports are 5985 (the WinRM port for HTTP) and 5986 (the WinRM port for HTTPS).</span></span> <span data-ttu-id="467f1-294">Den gemensamma aktivitets parametern är också en gemensam arbets flödes parameter.</span><span class="sxs-lookup"><span data-stu-id="467f1-294">This activity common parameter is also a workflow common parameter.</span></span>

<span data-ttu-id="467f1-295">Använd inte parametern PSPort om du inte behöver det.</span><span class="sxs-lookup"><span data-stu-id="467f1-295">Do not use the PSPort parameter unless you must.</span></span> <span data-ttu-id="467f1-296">Porten som anges i kommandot gäller för alla datorer eller sessioner där kommandot körs.</span><span class="sxs-lookup"><span data-stu-id="467f1-296">The port set in the command applies to all computers or sessions on which the command runs.</span></span> <span data-ttu-id="467f1-297">En alternativ port inställning kan hindra kommandot från att köras på alla datorer.</span><span class="sxs-lookup"><span data-stu-id="467f1-297">An alternate port setting might prevent the command from running on all computers.</span></span> <span data-ttu-id="467f1-298">Innan du använder en annan port måste du konfigurera WinRM-lyssnaren på fjärrdatorn för att lyssna på den porten.</span><span class="sxs-lookup"><span data-stu-id="467f1-298">Before using an alternate port, you must configure the WinRM listener on the remote computer to listen at that port.</span></span>

#### <a name="psprogress-psdatacollectionprogressrecord"></a><span data-ttu-id="467f1-299">PSProgress \<PSDataCollection[ProgressRecord]\></span><span class="sxs-lookup"><span data-stu-id="467f1-299">PSProgress \<PSDataCollection[ProgressRecord]\></span></span>

<span data-ttu-id="467f1-300">Lägger till förlopps meddelanden från aktiviteten till den angivna förlopps post samlingen i stället för att skriva förlopps meddelanden till konsolen eller till värdet för egenskapen Progress för arbets flödes jobbet.</span><span class="sxs-lookup"><span data-stu-id="467f1-300">Adds progress messages from the activity to the specified progress record collection, instead of writing the progress messages to the console or to the value of the Progress property of the workflow job.</span></span> <span data-ttu-id="467f1-301">Du kan lägga till förlopps meddelanden från flera aktiviteter till samma förlopps post samlings objekt.</span><span class="sxs-lookup"><span data-stu-id="467f1-301">You can add progress messages from multiple activities to the same progress record collection object.</span></span>

#### <a name="psprogressmessage-string"></a><span data-ttu-id="467f1-302">PSProgressMessage \<String\></span><span class="sxs-lookup"><span data-stu-id="467f1-302">PSProgressMessage \<String\></span></span>

<span data-ttu-id="467f1-303">Anger en egen beskrivning av aktiviteten.</span><span class="sxs-lookup"><span data-stu-id="467f1-303">Specifies a friendly description of the activity.</span></span> <span data-ttu-id="467f1-304">PSProgressMessage-värdet visas i förlopps indikatorn medan arbets flödet körs.</span><span class="sxs-lookup"><span data-stu-id="467f1-304">The PSProgressMessage value appears in the progress bar while the workflow runs.</span></span> <span data-ttu-id="467f1-305">När DisplayName också ingår i kommandot visas förlopps indikatorns innehåll i \<DisplayName\> : \<PSProgressMessage\> format.</span><span class="sxs-lookup"><span data-stu-id="467f1-305">When the DisplayName is also included in the command, the progress bar content appears in \<DisplayName\>:\<PSProgressMessage\> format.</span></span>

<span data-ttu-id="467f1-306">Den här parametern är särskilt användbar för att identifiera aktiviteter i en förgrunds-parallell skript block.</span><span class="sxs-lookup"><span data-stu-id="467f1-306">This parameter is particularly useful for identifying activities in a ForEach -Parallel script block.</span></span> <span data-ttu-id="467f1-307">Utan det här meddelandet identifieras aktiviteter i alla parallella grenar med samma namn.</span><span class="sxs-lookup"><span data-stu-id="467f1-307">Without this message, activities in all parallel branches are identified by the same name.</span></span>

#### <a name="psremotingbehavior-remotingbehavior"></a><span data-ttu-id="467f1-308">PSRemotingBehavior \<RemotingBehavior\></span><span class="sxs-lookup"><span data-stu-id="467f1-308">PSRemotingBehavior \<RemotingBehavior\></span></span>

<span data-ttu-id="467f1-309">Anger hur fjärr kommunikation hanteras när aktiviteten körs på mål datorerna.</span><span class="sxs-lookup"><span data-stu-id="467f1-309">Specifies how remoting is managed when the activity is run on target computers.</span></span>
<span data-ttu-id="467f1-310">PowerShell är standardinställningen.</span><span class="sxs-lookup"><span data-stu-id="467f1-310">PowerShell is the default.</span></span>

<span data-ttu-id="467f1-311">Giltiga värden är:</span><span class="sxs-lookup"><span data-stu-id="467f1-311">Valid values are:</span></span>

- <span data-ttu-id="467f1-312">Ingen: aktiviteten körs inte på fjärrdatorer.</span><span class="sxs-lookup"><span data-stu-id="467f1-312">None: The activity is not run on remote computers.</span></span>

- <span data-ttu-id="467f1-313">PowerShell: Windows PowerShell-fjärrkommunikation används för att köra aktiviteten på mål datorerna.</span><span class="sxs-lookup"><span data-stu-id="467f1-313">PowerShell: Windows PowerShell remoting is used to run the activity on target computers.</span></span>

- <span data-ttu-id="467f1-314">Anpassad: aktiviteten stöder sin egen typ av fjärr kommunikation.</span><span class="sxs-lookup"><span data-stu-id="467f1-314">Custom: The activity supports its own type of remoting.</span></span> <span data-ttu-id="467f1-315">Det här värdet är giltigt när den cmdlet som implementeras som en aktivitet anger värdet för attributet RemotingCapability till SupportedByCommand och kommandot innehåller parametern ComputerName.</span><span class="sxs-lookup"><span data-stu-id="467f1-315">This value is valid when the cmdlet that is being implemented as an activity sets the value of the RemotingCapability attribute to SupportedByCommand and the command includes the ComputerName parameter.</span></span>

#### <a name="psrequiredmodules-string"></a><span data-ttu-id="467f1-316">PSRequiredModules \<String[]\></span><span class="sxs-lookup"><span data-stu-id="467f1-316">PSRequiredModules \<String[]\></span></span>

<span data-ttu-id="467f1-317">Importerar de angivna modulerna innan kommandot körs.</span><span class="sxs-lookup"><span data-stu-id="467f1-317">Imports the specified modules before running the command.</span></span> <span data-ttu-id="467f1-318">Ange namnen på modulerna.</span><span class="sxs-lookup"><span data-stu-id="467f1-318">Enter the module names.</span></span> <span data-ttu-id="467f1-319">Modulerna måste vara installerade på mål datorn.</span><span class="sxs-lookup"><span data-stu-id="467f1-319">The modules must be installed on the target computer.</span></span>

<span data-ttu-id="467f1-320">Moduler som är installerade i en sökväg som anges i miljövariabeln PSModulePath importeras automatiskt vid första användningen av ett kommando i modulen.</span><span class="sxs-lookup"><span data-stu-id="467f1-320">Modules that are installed in a path specified in the PSModulePath environment variable are automatically imported on first use of any command in the module.</span></span>
<span data-ttu-id="467f1-321">Använd den här parametern för att importera moduler som inte finns på en PSModulePath plats.</span><span class="sxs-lookup"><span data-stu-id="467f1-321">Use this parameter to import modules that are not in a PSModulePath location.</span></span>

<span data-ttu-id="467f1-322">Eftersom varje aktivitet i ett arbets flöde körs i sin egen session importerar ett Import-Module-kommando bara en modul till den session där den körs.</span><span class="sxs-lookup"><span data-stu-id="467f1-322">Because each activity in a workflow runs in its own session, an Import-Module command imports a module only into the session in which it runs.</span></span> <span data-ttu-id="467f1-323">Modulen importerar inte modulen till sessioner där andra aktiviteter körs.</span><span class="sxs-lookup"><span data-stu-id="467f1-323">It does not import the module into sessions in which other activities run.</span></span>

#### <a name="pssessionoption-pssessionoption"></a><span data-ttu-id="467f1-324">PSSessionOption \<PSSessionOption\></span><span class="sxs-lookup"><span data-stu-id="467f1-324">PSSessionOption \<PSSessionOption\></span></span>

<span data-ttu-id="467f1-325">Anger avancerade alternativ för sessionerna till mål datorerna.</span><span class="sxs-lookup"><span data-stu-id="467f1-325">Sets advanced options for the sessions to the target computers.</span></span> <span data-ttu-id="467f1-326">Ange ett PSSessionOption-objekt, till exempel ett som du skapar med hjälp av New-PSSessionOption cmdlet.</span><span class="sxs-lookup"><span data-stu-id="467f1-326">Enter a PSSessionOption object, such as one that you create by using the New-PSSessionOption cmdlet.</span></span> <span data-ttu-id="467f1-327">Den gemensamma aktivitets parametern är också en gemensam arbets flödes parameter.</span><span class="sxs-lookup"><span data-stu-id="467f1-327">This activity common parameter is also a workflow common parameter.</span></span>

<span data-ttu-id="467f1-328">Standardvärdena för session alternativen bestäms av värdet för `$PSSessionOption` variabeln Preference, om det har angetts.</span><span class="sxs-lookup"><span data-stu-id="467f1-328">The default values for the session options are determined by the value of the `$PSSessionOption` preference variable, if it is set.</span></span> <span data-ttu-id="467f1-329">Annars använder sessionen de värden som anges i konfigurationen för sessionen.</span><span class="sxs-lookup"><span data-stu-id="467f1-329">Otherwise, the session uses the values specified in the session configuration.</span></span>

<span data-ttu-id="467f1-330">En beskrivning av sessionsinformation, inklusive standardvärdena, finns i hjälp avsnittet för New-PSSessionOption cmdlet [New-PSSessionOption](xref:Microsoft.PowerShell.Core.New-PSSessionOption).</span><span class="sxs-lookup"><span data-stu-id="467f1-330">For a description of the session options, including the default values, see the help topic for the New-PSSessionOption cmdlet [New-PSSessionOption](xref:Microsoft.PowerShell.Core.New-PSSessionOption).</span></span>

<span data-ttu-id="467f1-331">Mer information om variabeln $PSSessionOption finns [about_Preference_Variables](../../Microsoft.PowerShell.Core/About/about_Preference_Variables.md).</span><span class="sxs-lookup"><span data-stu-id="467f1-331">For more information about the $PSSessionOption preference variable, see [about_Preference_Variables](../../Microsoft.PowerShell.Core/About/about_Preference_Variables.md).</span></span>

#### <a name="psusessl-boolean"></a><span data-ttu-id="467f1-332">PSUseSSL \<Boolean\></span><span class="sxs-lookup"><span data-stu-id="467f1-332">PSUseSSL \<Boolean\></span></span>

<span data-ttu-id="467f1-333">Värdet $True använder protokollet Secure Sockets Layer (SSL) för att upprätta en anslutning till mål datorn.</span><span class="sxs-lookup"><span data-stu-id="467f1-333">A value of $True uses the Secure Sockets Layer (SSL) protocol to establish a connection to the target computer.</span></span> <span data-ttu-id="467f1-334">Som standard används inte SSL.</span><span class="sxs-lookup"><span data-stu-id="467f1-334">By default, SSL is not used.</span></span> <span data-ttu-id="467f1-335">Värdet $False har ingen påverkan.</span><span class="sxs-lookup"><span data-stu-id="467f1-335">A value of $False has no effect.</span></span> <span data-ttu-id="467f1-336">Den gemensamma aktivitets parametern är också en gemensam arbets flödes parameter.</span><span class="sxs-lookup"><span data-stu-id="467f1-336">This activity common parameter is also a workflow common parameter.</span></span>

<span data-ttu-id="467f1-337">WS-Management krypterar allt Windows PowerShell-innehåll som överförs via nätverket.</span><span class="sxs-lookup"><span data-stu-id="467f1-337">WS-Management encrypts all Windows PowerShell content transmitted over the network.</span></span> <span data-ttu-id="467f1-338">UseSSL är ett ytterligare skydd som skickar data via HTTPS i stället för HTTP.</span><span class="sxs-lookup"><span data-stu-id="467f1-338">UseSSL is an additional protection that sends the data across an HTTPS, instead of HTTP.</span></span> <span data-ttu-id="467f1-339">Om du använder den här parametern, men SSL inte är tillgängligt på den port som används för kommandot, Miss lyckas kommandot.</span><span class="sxs-lookup"><span data-stu-id="467f1-339">If you use this parameter, but SSL is not available on the port used for the command, the command fails.</span></span>

#### <a name="psverbose-psdatacollectionverboserecord"></a><span data-ttu-id="467f1-340">PSVerbose \<PSDataCollection[VerboseRecord]\></span><span class="sxs-lookup"><span data-stu-id="467f1-340">PSVerbose \<PSDataCollection[VerboseRecord]\></span></span>

<span data-ttu-id="467f1-341">Lägger till utförliga meddelanden från aktiviteten till den angivna utförliga post samlingen, i stället för att skriva utförliga meddelanden till konsolen eller till värdet för egenskapen utförligt för arbets flödes jobbet.</span><span class="sxs-lookup"><span data-stu-id="467f1-341">Adds verbose messages from the activity to the specified verbose record collection, instead of writing the verbose messages to the console or to the value of the Verbose property of the workflow job.</span></span> <span data-ttu-id="467f1-342">Du kan lägga till utförliga meddelanden från flera aktiviteter till samma utförlig post samlings objekt.</span><span class="sxs-lookup"><span data-stu-id="467f1-342">You can add verbose messages from multiple activities to the same verbose record collection object.</span></span>

#### <a name="pswarning-psdatacollectionwarningrecord"></a><span data-ttu-id="467f1-343">PSWarning \<PSDataCollection[WarningRecord]\></span><span class="sxs-lookup"><span data-stu-id="467f1-343">PSWarning \<PSDataCollection[WarningRecord]\></span></span>

<span data-ttu-id="467f1-344">Lägger till varnings meddelanden från aktiviteten till den angivna varnings post samlingen i stället för att skriva varnings meddelandena till konsolen eller till värdet för egenskapen varning för arbets flödes jobbet.</span><span class="sxs-lookup"><span data-stu-id="467f1-344">Adds warning messages from the activity to the specified warning record collection, instead of writing the warning messages to the console or to the value of the Warning property of the workflow job.</span></span> <span data-ttu-id="467f1-345">Du kan lägga till varnings meddelanden från flera aktiviteter i samma varnings post samlings objekt.</span><span class="sxs-lookup"><span data-stu-id="467f1-345">You can add warning messages from multiple activities to the same warning record collection object.</span></span>

#### <a name="result"></a><span data-ttu-id="467f1-346">Resultat</span><span class="sxs-lookup"><span data-stu-id="467f1-346">Result</span></span>

<span data-ttu-id="467f1-347">Den här parametern är endast giltig i XAML-arbetsflöden.</span><span class="sxs-lookup"><span data-stu-id="467f1-347">This parameter is valid only in XAML workflows.</span></span>

#### <a name="usedefaultinput-boolean"></a><span data-ttu-id="467f1-348">UseDefaultInput \<Boolean\></span><span class="sxs-lookup"><span data-stu-id="467f1-348">UseDefaultInput \<Boolean\></span></span>

<span data-ttu-id="467f1-349">Accepterar alla arbets flödes indatatyper som ininformation till aktiviteten efter värde.</span><span class="sxs-lookup"><span data-stu-id="467f1-349">Accepts all workflow input as input to the activity by value.</span></span>

<span data-ttu-id="467f1-350">Till exempel använder Get-Process-aktiviteten i följande exempel arbets flöde den gemensamma parametern UseDefaultInput-aktivitet för att hämta ininformation som skickas till arbets flödet.</span><span class="sxs-lookup"><span data-stu-id="467f1-350">For example, the Get-Process activity in the following sample workflow uses the UseDefaultInput activity common parameter to get input that is passed to the workflow.</span></span> <span data-ttu-id="467f1-351">När du kör arbets flödet med indatamängd används indatamängden av aktiviteten.</span><span class="sxs-lookup"><span data-stu-id="467f1-351">When you run the workflow with input, that input is used by the activity.</span></span>

```powershell
workflow Test-Workflow
{
    Get-Service -UseDefaultInput $True
}

PS C:> Test-Workflow -InputObject WinRm
```

```output
Status   Name        DisplayName                            PSComputerName
------   ----        -----------                            --------------
Running  winrm       Windows Remote Management (WS-Manag... localhost
```

#### <a name="verbose-switchparameter"></a><span data-ttu-id="467f1-352">Utförlig \<SwitchParameter\></span><span class="sxs-lookup"><span data-stu-id="467f1-352">Verbose \<SwitchParameter\></span></span>

<span data-ttu-id="467f1-353">Visar detaljerad information om den åtgärd som utförs av kommandot.</span><span class="sxs-lookup"><span data-stu-id="467f1-353">Displays detailed information about the operation performed by the command.</span></span>
<span data-ttu-id="467f1-354">Den här informationen liknar informationen i en spårning eller i en transaktions logg.</span><span class="sxs-lookup"><span data-stu-id="467f1-354">This information resembles the information in a trace or in a transaction log.</span></span>
<span data-ttu-id="467f1-355">Den utförliga parametern åsidosätter värdet för variabeln $VerbosePreference för det aktuella kommandot.</span><span class="sxs-lookup"><span data-stu-id="467f1-355">The Verbose parameter overrides the value of the $VerbosePreference variable for the current command.</span></span> <span data-ttu-id="467f1-356">Den här parametern fungerar bara när kommandot genererar ett utförligt meddelande.</span><span class="sxs-lookup"><span data-stu-id="467f1-356">This parameter works only when the command generates a verbose message.</span></span> <span data-ttu-id="467f1-357">Den här parametern är också en gemensam Windows PowerShell-parameter.</span><span class="sxs-lookup"><span data-stu-id="467f1-357">This parameter is also a Windows PowerShell common parameter.</span></span>

#### <a name="warningaction-actionpreference"></a><span data-ttu-id="467f1-358">WarningAction \<ActionPreference\></span><span class="sxs-lookup"><span data-stu-id="467f1-358">WarningAction \<ActionPreference\></span></span>

<span data-ttu-id="467f1-359">Anger hur aktiviteten svarar på en varning.</span><span class="sxs-lookup"><span data-stu-id="467f1-359">Determines how the activity responds to a warning.</span></span> <span data-ttu-id="467f1-360">"Fortsätt" är standardvärdet.</span><span class="sxs-lookup"><span data-stu-id="467f1-360">"Continue" is the default value.</span></span> <span data-ttu-id="467f1-361">Parametern WarningAction åsidosätter värdet för variabeln $WarningPreference för det aktuella kommandot.</span><span class="sxs-lookup"><span data-stu-id="467f1-361">The WarningAction parameter overrides the value of the $WarningPreference variable for the current command.</span></span> <span data-ttu-id="467f1-362">Den här parametern fungerar bara när kommandot genererar ett varnings meddelande.</span><span class="sxs-lookup"><span data-stu-id="467f1-362">This parameter works only when the command generates a warning message.</span></span> <span data-ttu-id="467f1-363">Den här parametern är också en gemensam Windows PowerShell-parameter.</span><span class="sxs-lookup"><span data-stu-id="467f1-363">This parameter is also a Windows PowerShell common parameter.</span></span>

<span data-ttu-id="467f1-364">Giltiga värden:</span><span class="sxs-lookup"><span data-stu-id="467f1-364">Valid Values:</span></span>

- <span data-ttu-id="467f1-365">SilentlyContinue.</span><span class="sxs-lookup"><span data-stu-id="467f1-365">SilentlyContinue.</span></span> <span data-ttu-id="467f1-366">Undertrycker varnings meddelandet och fortsätter att köra kommandot.</span><span class="sxs-lookup"><span data-stu-id="467f1-366">Suppresses the warning message and continues executing the command.</span></span>

- <span data-ttu-id="467f1-367">Bestå.</span><span class="sxs-lookup"><span data-stu-id="467f1-367">Continue.</span></span> <span data-ttu-id="467f1-368">Visar varnings meddelandet och fortsätter att köra kommandot.</span><span class="sxs-lookup"><span data-stu-id="467f1-368">Displays the warning message and continues executing the command.</span></span>
  <span data-ttu-id="467f1-369">"Fortsätt" är standardvärdet.</span><span class="sxs-lookup"><span data-stu-id="467f1-369">"Continue" is the default value.</span></span>

- <span data-ttu-id="467f1-370">Inquire.</span><span class="sxs-lookup"><span data-stu-id="467f1-370">Inquire.</span></span> <span data-ttu-id="467f1-371">Visar varnings meddelandet och du uppmanas att bekräfta innan du fortsätter körningen.</span><span class="sxs-lookup"><span data-stu-id="467f1-371">Displays the warning message and prompts you for confirmation before continuing execution.</span></span> <span data-ttu-id="467f1-372">Det här värdet används sällan.</span><span class="sxs-lookup"><span data-stu-id="467f1-372">This value is rarely used.</span></span>

- <span data-ttu-id="467f1-373">Stop (Stoppa).</span><span class="sxs-lookup"><span data-stu-id="467f1-373">Stop.</span></span> <span data-ttu-id="467f1-374">Visar varnings meddelandet och stoppar körningen av kommandot.</span><span class="sxs-lookup"><span data-stu-id="467f1-374">Displays the warning message and stops executing the command.</span></span>

> [!NOTE]
> <span data-ttu-id="467f1-375">Parametern WarningAction åsidosätter inte värdet för inställnings variabeln $WarningAction när parametern används i ett kommando för att köra ett skript eller en funktion.</span><span class="sxs-lookup"><span data-stu-id="467f1-375">The WarningAction parameter does not override the value of the $WarningAction preference variable when the parameter is used in a command to run a script or function.</span></span>

### <a name="examples"></a><span data-ttu-id="467f1-376">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="467f1-376">EXAMPLES</span></span>

<span data-ttu-id="467f1-377">De gemensamma aktivitets parametrarna är mycket användbara.</span><span class="sxs-lookup"><span data-stu-id="467f1-377">The activity common parameters are extremely useful.</span></span> <span data-ttu-id="467f1-378">Du kan till exempel använda parametern PSComputerName för att köra vissa aktiviteter bara på en delmängd av mål datorerna.</span><span class="sxs-lookup"><span data-stu-id="467f1-378">For example, you can use the PSComputerName parameter to run particular activities on only a subset of the target computers.</span></span>

<span data-ttu-id="467f1-379">Eller så kan du använda parametrarna PSConnectionRetryCount och PSConnectionRetryIntervalSec för att justera värdena för återförsök för vissa aktiviteter.</span><span class="sxs-lookup"><span data-stu-id="467f1-379">Or, you might use the PSConnectionRetryCount and PSConnectionRetryIntervalSec parameters to adjust the retry values for particular activities.</span></span>

<span data-ttu-id="467f1-380">I följande exempel visas hur du använder de gemensamma parametrarna för PSComputerName-aktivitet för att köra en Get-EventLog-aktivitet enbart på datorer som är en viss domän.</span><span class="sxs-lookup"><span data-stu-id="467f1-380">The following example shows how to use the PSComputerName activity common parameters to run a Get-EventLog activity only on computers it a particular domain.</span></span>

```powershell
Workflow Test-Workflow
{
    $UserDomain = Get-Content -Path '.\UserComputers.txt'
    $Log = (Get-EventLog -LogName "Windows PowerShell" `
      -PSComputerName $UserDomain)

    if ($Log)
    {
        # Do Work Here.
    }
}
```

<!--
# KEYWORDS
[about_Activity_Common_Parameters](about_Activity_Common_Parameters.md)
[about_Activity_Parameters](about_Activity_Parameters.md)
[about_ActivityParameters]()about_ActivityParameters.md) -->

## <a name="see-also"></a><span data-ttu-id="467f1-381">SE ÄVEN</span><span class="sxs-lookup"><span data-stu-id="467f1-381">SEE ALSO</span></span>

<span data-ttu-id="467f1-382">[about_Workflows](about_workflows.md) 
 [about_WorkflowCommonParameters](about_WorkflowCommonParameters.md)</span><span class="sxs-lookup"><span data-stu-id="467f1-382">[about_Workflows](about_workflows.md)
[about_WorkflowCommonParameters](about_WorkflowCommonParameters.md)</span></span>
