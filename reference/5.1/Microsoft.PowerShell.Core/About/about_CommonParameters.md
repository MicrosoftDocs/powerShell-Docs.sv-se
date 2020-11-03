---
description: Beskriver de parametrar som kan användas med vilken cmdlet som helst.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 11/26/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_CommonParameters
ms.openlocfilehash: 441154d60440024ebea9d5047430f6e9209d8f04
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/13/2020
ms.locfileid: "93272216"
---
# <a name="about-commonparameters"></a><span data-ttu-id="8b576-104">Om CommonParameters</span><span class="sxs-lookup"><span data-stu-id="8b576-104">About CommonParameters</span></span>

## <a name="short-description"></a><span data-ttu-id="8b576-105">KORT BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="8b576-105">SHORT DESCRIPTION</span></span>

<span data-ttu-id="8b576-106">Beskriver de parametrar som kan användas med vilken cmdlet som helst.</span><span class="sxs-lookup"><span data-stu-id="8b576-106">Describes the parameters that can be used with any cmdlet.</span></span>

## <a name="long-description"></a><span data-ttu-id="8b576-107">LÅNG BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="8b576-107">LONG DESCRIPTION</span></span>

<span data-ttu-id="8b576-108">De gemensamma parametrarna är en uppsättning cmdlet-parametrar som du kan använda med valfri cmdlet.</span><span class="sxs-lookup"><span data-stu-id="8b576-108">The common parameters are a set of cmdlet parameters that you can use with any cmdlet.</span></span> <span data-ttu-id="8b576-109">De implementeras av PowerShell, inte av cmdlet-utvecklaren, och de är automatiskt tillgängliga för alla cmdletar.</span><span class="sxs-lookup"><span data-stu-id="8b576-109">They're implemented by PowerShell, not by the cmdlet developer, and they're automatically available to any cmdlet.</span></span>

<span data-ttu-id="8b576-110">Du kan använda de gemensamma parametrarna med valfri cmdlet, men de kanske inte har någon påverkan på alla cmdletar.</span><span class="sxs-lookup"><span data-stu-id="8b576-110">You can use the common parameters with any cmdlet, but they might not have an effect on all cmdlets.</span></span> <span data-ttu-id="8b576-111">Om en cmdlet till exempel inte genererar några utförliga utdata, har den **utförliga** gemensamma parametern ingen effekt.</span><span class="sxs-lookup"><span data-stu-id="8b576-111">For example, if a cmdlet doesn't generate any verbose output, using the **Verbose** common parameter has no effect.</span></span>

<span data-ttu-id="8b576-112">De gemensamma parametrarna är också tillgängliga för avancerade funktioner som använder attributet **CmdletBinding** eller attributet **parameter** .</span><span class="sxs-lookup"><span data-stu-id="8b576-112">The common parameters are also available on advanced functions that use the **CmdletBinding** attribute or the **Parameter** attribute.</span></span>

<span data-ttu-id="8b576-113">Flera vanliga parametrar åsidosätter systemstandardinställningar eller inställningar som du anger med hjälp av variablerna för PowerShell-inställningar.</span><span class="sxs-lookup"><span data-stu-id="8b576-113">Several common parameters override system defaults or preferences that you set by using the PowerShell preference variables.</span></span> <span data-ttu-id="8b576-114">Till skillnad från inställningarna för variabler påverkar de gemensamma parametrarna bara de kommandon som de används i.</span><span class="sxs-lookup"><span data-stu-id="8b576-114">Unlike the preference variables, the common parameters affect only the commands in which they're used.</span></span>

<span data-ttu-id="8b576-115">Mer information finns i [about_Preference_Variables](./about_Preference_Variables.md).</span><span class="sxs-lookup"><span data-stu-id="8b576-115">For more information, see [about_Preference_Variables](./about_Preference_Variables.md).</span></span>

<span data-ttu-id="8b576-116">I följande lista visas de gemensamma parametrarna.</span><span class="sxs-lookup"><span data-stu-id="8b576-116">The following list displays the common parameters.</span></span> <span data-ttu-id="8b576-117">Deras alias visas inom parentes.</span><span class="sxs-lookup"><span data-stu-id="8b576-117">Their aliases are listed in parentheses.</span></span>

- <span data-ttu-id="8b576-118">**Felsöka** (dB)</span><span class="sxs-lookup"><span data-stu-id="8b576-118">**Debug** (db)</span></span>
- <span data-ttu-id="8b576-119">**ErrorAction** (EA)</span><span class="sxs-lookup"><span data-stu-id="8b576-119">**ErrorAction** (ea)</span></span>
- <span data-ttu-id="8b576-120">**ErrorVariable** (EV)</span><span class="sxs-lookup"><span data-stu-id="8b576-120">**ErrorVariable** (ev)</span></span>
- <span data-ttu-id="8b576-121">**InformationAction** (Infa)</span><span class="sxs-lookup"><span data-stu-id="8b576-121">**InformationAction** (infa)</span></span>
- <span data-ttu-id="8b576-122">**InformationVariable** (IV)</span><span class="sxs-lookup"><span data-stu-id="8b576-122">**InformationVariable** (iv)</span></span>
- <span data-ttu-id="8b576-123">**Avvariabel** (OV)</span><span class="sxs-lookup"><span data-stu-id="8b576-123">**OutVariable** (ov)</span></span>
- <span data-ttu-id="8b576-124">**Utbuffer** (OB)</span><span class="sxs-lookup"><span data-stu-id="8b576-124">**OutBuffer** (ob)</span></span>
- <span data-ttu-id="8b576-125">**PipelineVariable** (PV)</span><span class="sxs-lookup"><span data-stu-id="8b576-125">**PipelineVariable** (pv)</span></span>
- <span data-ttu-id="8b576-126">**Verbose** (VB)</span><span class="sxs-lookup"><span data-stu-id="8b576-126">**Verbose** (vb)</span></span>
- <span data-ttu-id="8b576-127">**WarningAction** (WA)</span><span class="sxs-lookup"><span data-stu-id="8b576-127">**WarningAction** (wa)</span></span>
- <span data-ttu-id="8b576-128">**WarningVariable** (WV)</span><span class="sxs-lookup"><span data-stu-id="8b576-128">**WarningVariable** (wv)</span></span>

<span data-ttu-id="8b576-129">**Åtgärds** parametrarna är **Åtgärdsinställning** -typnamn.</span><span class="sxs-lookup"><span data-stu-id="8b576-129">The **Action** parameters are **ActionPreference** type values.</span></span>
<span data-ttu-id="8b576-130">**Åtgärdsinställning** är en uppräkning med följande värden:</span><span class="sxs-lookup"><span data-stu-id="8b576-130">**ActionPreference** is an enumeration with the following values:</span></span>

| <span data-ttu-id="8b576-131">Name</span><span class="sxs-lookup"><span data-stu-id="8b576-131">Name</span></span>             | <span data-ttu-id="8b576-132">Värde</span><span class="sxs-lookup"><span data-stu-id="8b576-132">Value</span></span> |
|------------------|-------|
| <span data-ttu-id="8b576-133">Suspend</span><span class="sxs-lookup"><span data-stu-id="8b576-133">Suspend</span></span>          | <span data-ttu-id="8b576-134">5</span><span class="sxs-lookup"><span data-stu-id="8b576-134">5</span></span>     |
| <span data-ttu-id="8b576-135">Ignorera</span><span class="sxs-lookup"><span data-stu-id="8b576-135">Ignore</span></span>           | <span data-ttu-id="8b576-136">4</span><span class="sxs-lookup"><span data-stu-id="8b576-136">4</span></span>     |
| <span data-ttu-id="8b576-137">Inquire</span><span class="sxs-lookup"><span data-stu-id="8b576-137">Inquire</span></span>          | <span data-ttu-id="8b576-138">3</span><span class="sxs-lookup"><span data-stu-id="8b576-138">3</span></span>     |
| <span data-ttu-id="8b576-139">Fortsätt</span><span class="sxs-lookup"><span data-stu-id="8b576-139">Continue</span></span>         | <span data-ttu-id="8b576-140">2</span><span class="sxs-lookup"><span data-stu-id="8b576-140">2</span></span>     |
| <span data-ttu-id="8b576-141">Stoppa</span><span class="sxs-lookup"><span data-stu-id="8b576-141">Stop</span></span>             | <span data-ttu-id="8b576-142">1</span><span class="sxs-lookup"><span data-stu-id="8b576-142">1</span></span>     |
| <span data-ttu-id="8b576-143">SilentlyContinue</span><span class="sxs-lookup"><span data-stu-id="8b576-143">SilentlyContinue</span></span> | <span data-ttu-id="8b576-144">0</span><span class="sxs-lookup"><span data-stu-id="8b576-144">0</span></span>     |

<span data-ttu-id="8b576-145">Du kan använda namnet eller värdet med parametern.</span><span class="sxs-lookup"><span data-stu-id="8b576-145">You may use the name or the value with the parameter.</span></span>

<span data-ttu-id="8b576-146">Förutom de gemensamma parametrarna erbjuder många cmdlets parametrar för risk minskning.</span><span class="sxs-lookup"><span data-stu-id="8b576-146">In addition to the common parameters, many cmdlets offer risk mitigation parameters.</span></span> <span data-ttu-id="8b576-147">Cmdletar som innebär risk för systemet eller användar data erbjuder vanligt vis dessa parametrar.</span><span class="sxs-lookup"><span data-stu-id="8b576-147">Cmdlets that involve risk to the system or to user data usually offer these parameters.</span></span>

<span data-ttu-id="8b576-148">Parametrarna för risk minskning är:</span><span class="sxs-lookup"><span data-stu-id="8b576-148">The risk mitigation parameters are:</span></span>

- <span data-ttu-id="8b576-149">**WhatIf** (Wi)</span><span class="sxs-lookup"><span data-stu-id="8b576-149">**WhatIf** (wi)</span></span>
- <span data-ttu-id="8b576-150">**Bekräfta** (CF)</span><span class="sxs-lookup"><span data-stu-id="8b576-150">**Confirm** (cf)</span></span>

### <a name="common-parameter-descriptions"></a><span data-ttu-id="8b576-151">VANLIGA PARAMETER BESKRIVNINGAR</span><span class="sxs-lookup"><span data-stu-id="8b576-151">COMMON PARAMETER DESCRIPTIONS</span></span>

#### <a name="debug"></a><span data-ttu-id="8b576-152">Felsökning</span><span class="sxs-lookup"><span data-stu-id="8b576-152">Debug</span></span>

<span data-ttu-id="8b576-153">Visar information om program nivå om den åtgärd som utförs av kommandot.</span><span class="sxs-lookup"><span data-stu-id="8b576-153">Displays programmer-level detail about the operation done by the command.</span></span> <span data-ttu-id="8b576-154">Den här parametern fungerar bara när kommandot genererar ett fel söknings meddelande.</span><span class="sxs-lookup"><span data-stu-id="8b576-154">This parameter works only when the command generates a debugging message.</span></span> <span data-ttu-id="8b576-155">Den här parametern fungerar till exempel när ett kommando innehåller `Write-Debug` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="8b576-155">For example, this parameter works when a command contains the `Write-Debug` cmdlet.</span></span>

```yaml
Type: SwitchParameter
Aliases: db

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

<span data-ttu-id="8b576-156">Som standard visas fel söknings meddelanden eftersom värdet för `$DebugPreference` variabeln är **SilentlyContinue**.</span><span class="sxs-lookup"><span data-stu-id="8b576-156">By default, debugging messages aren't displayed because the value of the `$DebugPreference` variable is **SilentlyContinue**.</span></span>

<span data-ttu-id="8b576-157">I interaktivt läge åsidosätter **fel söknings** parametern värdet för `$DebugPreference` variabeln för det aktuella kommandot och anger värdet för `$DebugPreference` att **fråga**.</span><span class="sxs-lookup"><span data-stu-id="8b576-157">In interactive mode, the **Debug** parameter overrides the value of the `$DebugPreference` variable for the current command, setting the value of `$DebugPreference` to **Inquire**.</span></span>

<span data-ttu-id="8b576-158">I icke-interaktivt läge åsidosätter **fel söknings** parametern värdet för `$DebugPreference` variabeln för det aktuella kommandot och anger värdet för `$DebugPreference` att **fortsätta**.</span><span class="sxs-lookup"><span data-stu-id="8b576-158">In non-interactive mode, the **Debug** parameter overrides the value of the `$DebugPreference` variable for the current command, setting the value of `$DebugPreference` to **Continue**.</span></span>

<span data-ttu-id="8b576-159">`-Debug:$true` har samma resultat som `-Debug` .</span><span class="sxs-lookup"><span data-stu-id="8b576-159">`-Debug:$true` has the same effect as `-Debug`.</span></span> <span data-ttu-id="8b576-160">Används `-Debug:$false` för att förhindra visning av fel söknings meddelanden när `$DebugPreference` inte är **SilentlyContinue** , vilket är standardvärdet.</span><span class="sxs-lookup"><span data-stu-id="8b576-160">Use `-Debug:$false` to suppress the display of debugging messages when `$DebugPreference` isn't **SilentlyContinue** , which is the default.</span></span>

#### <a name="erroraction"></a><span data-ttu-id="8b576-161">ErrorAction</span><span class="sxs-lookup"><span data-stu-id="8b576-161">ErrorAction</span></span>

<span data-ttu-id="8b576-162">Anger hur cmdleten svarar på ett icke-avslutande fel från kommandot.</span><span class="sxs-lookup"><span data-stu-id="8b576-162">Determines how the cmdlet responds to a non-terminating error from the command.</span></span>
<span data-ttu-id="8b576-163">Den här parametern fungerar bara när kommandot genererar ett icke-avslutande fel, till exempel från `Write-Error` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="8b576-163">This parameter works only when the command generates a non-terminating error, such as those from the `Write-Error` cmdlet.</span></span>

```yaml
Type: ActionPreference
Aliases: ea
Accepted values: Suspend, Ignore, Inquire, Continue, Stop, SilentlyContinue

Required: False
Position: Named
Default value: Depends on preference variable
Accept pipeline input: False
Accept wildcard characters: False
```

<span data-ttu-id="8b576-164">Parametern **ErrorAction** åsidosätter värdet för `$ErrorActionPreference` variabeln för det aktuella kommandot.</span><span class="sxs-lookup"><span data-stu-id="8b576-164">The **ErrorAction** parameter overrides the value of the `$ErrorActionPreference` variable for the current command.</span></span> <span data-ttu-id="8b576-165">Eftersom standardvärdet för `$ErrorActionPreference` variabeln **fortsätter** visas fel meddelanden och körningen fortsätter om du inte använder parametern **ErrorAction** .</span><span class="sxs-lookup"><span data-stu-id="8b576-165">Because the default value of the `$ErrorActionPreference` variable is **Continue** , error messages are displayed and execution continues unless you use the **ErrorAction** parameter.</span></span>

<span data-ttu-id="8b576-166">Parametern **ErrorAction** har ingen påverkan på att avsluta fel (till exempel saknade data, parametrar som inte är giltiga eller otillräckliga behörigheter) som hindrar ett kommando från att slutföras.</span><span class="sxs-lookup"><span data-stu-id="8b576-166">The **ErrorAction** parameter has no effect on terminating errors (such as missing data, parameters that aren't valid, or insufficient permissions) that prevent a command from completing successfully.</span></span>

<span data-ttu-id="8b576-167">`-ErrorAction:Continue` Visa fel meddelandet och fortsätt att köra kommandot.</span><span class="sxs-lookup"><span data-stu-id="8b576-167">`-ErrorAction:Continue` display the error message and continues executing the command.</span></span> <span data-ttu-id="8b576-168">`Continue` används som standard.</span><span class="sxs-lookup"><span data-stu-id="8b576-168">`Continue` is the default.</span></span>

<span data-ttu-id="8b576-169">`-ErrorAction:Ignore` ignorerar fel meddelandet och fortsätter att köra kommandot.</span><span class="sxs-lookup"><span data-stu-id="8b576-169">`-ErrorAction:Ignore` suppresses the error message and continues executing the command.</span></span> <span data-ttu-id="8b576-170">Till skillnad från **SilentlyContinue** lägger **Ignorera** inte till fel meddelandet i den `$Error` automatiska variabeln.</span><span class="sxs-lookup"><span data-stu-id="8b576-170">Unlike **SilentlyContinue** , **Ignore** doesn't add the error message to the `$Error` automatic variable.</span></span> <span data-ttu-id="8b576-171">**Ignorera** -värdet introduceras i PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="8b576-171">The **Ignore** value is introduced in PowerShell 3.0.</span></span>

<span data-ttu-id="8b576-172">`-ErrorAction:Inquire` visar fel meddelandet och du uppmanas att bekräfta innan du fortsätter körningen.</span><span class="sxs-lookup"><span data-stu-id="8b576-172">`-ErrorAction:Inquire` displays the error message and prompts you for confirmation before continuing execution.</span></span> <span data-ttu-id="8b576-173">Det här värdet används sällan.</span><span class="sxs-lookup"><span data-stu-id="8b576-173">This value is rarely used.</span></span>

<span data-ttu-id="8b576-174">`-ErrorAction:SilentlyContinue` ignorerar fel meddelandet och fortsätter att köra kommandot.</span><span class="sxs-lookup"><span data-stu-id="8b576-174">`-ErrorAction:SilentlyContinue` suppresses the error message and continues executing the command.</span></span>

<span data-ttu-id="8b576-175">`-ErrorAction:Stop` visar fel meddelandet och slutar att köra kommandot.</span><span class="sxs-lookup"><span data-stu-id="8b576-175">`-ErrorAction:Stop` displays the error message and stops executing the command.</span></span>

<span data-ttu-id="8b576-176">`-ErrorAction:Suspend` är bara tillgängligt för arbets flöden som inte stöds i PowerShell 6 och senare.</span><span class="sxs-lookup"><span data-stu-id="8b576-176">`-ErrorAction:Suspend` is only available for workflows which aren't supported in PowerShell 6 and beyond.</span></span>

> [!NOTE]
> <span data-ttu-id="8b576-177">Parametern **ErrorAction** åsidosätter, men ersätter inte värdet för `$ErrorAction` Preference-variabeln när parametern används i ett kommando för att köra ett skript eller en funktion.</span><span class="sxs-lookup"><span data-stu-id="8b576-177">The **ErrorAction** parameter overrides, but does not replace the value of the `$ErrorAction` preference variable when the parameter is used in a command to run a script or function.</span></span>

#### <a name="errorvariable"></a><span data-ttu-id="8b576-178">ErrorVariable</span><span class="sxs-lookup"><span data-stu-id="8b576-178">ErrorVariable</span></span>

<span data-ttu-id="8b576-179">**ErrorVariable** lagrar fel meddelanden om kommandot i den angivna variabeln och i den `$Error` automatiska variabeln.</span><span class="sxs-lookup"><span data-stu-id="8b576-179">**ErrorVariable** stores error messages about the command in the specified variable and in the `$Error` automatic variable.</span></span> <span data-ttu-id="8b576-180">Mer information finns i [about_Automatic_Variables](about_Automatic_Variables.md)</span><span class="sxs-lookup"><span data-stu-id="8b576-180">For more information, see [about_Automatic_Variables](about_Automatic_Variables.md)</span></span>

```yaml
Type: String
Aliases: ev

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

<span data-ttu-id="8b576-181">Som standard skriver nya fel meddelanden över fel meddelanden som redan är lagrade i variabeln.</span><span class="sxs-lookup"><span data-stu-id="8b576-181">By default, new error messages overwrite error messages that are already stored in the variable.</span></span> <span data-ttu-id="8b576-182">Om du vill lägga till fel meddelandet i variabel innehållet skriver du ett plus tecken ( `+` ) före variabel namnet.</span><span class="sxs-lookup"><span data-stu-id="8b576-182">To append the error message to the variable content, type a plus sign (`+`) before the variable name.</span></span>

<span data-ttu-id="8b576-183">Till exempel skapar följande kommando `$a` variabeln och lagrar sedan eventuella fel i den:</span><span class="sxs-lookup"><span data-stu-id="8b576-183">For example, the following command creates the `$a` variable and then stores any errors in it:</span></span>

```powershell
Get-Process -Id 6 -ErrorVariable a
```

<span data-ttu-id="8b576-184">Följande kommando lägger till eventuella fel meddelanden i `$a` variabeln:</span><span class="sxs-lookup"><span data-stu-id="8b576-184">The following command adds any error messages to the `$a` variable:</span></span>

```powershell
Get-Process -Id 2 -ErrorVariable +a
```

<span data-ttu-id="8b576-185">Följande kommando visar innehållet i `$a` :</span><span class="sxs-lookup"><span data-stu-id="8b576-185">The following command displays the contents of `$a`:</span></span>

```powershell
$a
```

<span data-ttu-id="8b576-186">Du kan använda den här parametern för att skapa en variabel som bara innehåller fel meddelanden från vissa kommandon och som inte påverkar beteendet för den `$Error` automatiska variabeln.</span><span class="sxs-lookup"><span data-stu-id="8b576-186">You can use this parameter to create a variable that contains only error messages from specific commands and does not affect the behavior of the `$Error` automatic variable.</span></span> <span data-ttu-id="8b576-187">Den `$Error` automatiska variabeln innehåller fel meddelanden från alla kommandon i sessionen.</span><span class="sxs-lookup"><span data-stu-id="8b576-187">The `$Error` automatic variable contains error messages from all the commands in the session.</span></span> <span data-ttu-id="8b576-188">Du kan använda mat ris notation, till exempel `$a[0]` eller `$error[1,2]` för att referera till vissa fel som lagras i variablerna.</span><span class="sxs-lookup"><span data-stu-id="8b576-188">You can use array notation, such as `$a[0]` or `$error[1,2]` to refer to specific errors stored in the variables.</span></span>

> [!NOTE]
> <span data-ttu-id="8b576-189">Den anpassade fel variabeln innehåller alla fel som genereras av kommandot, inklusive fel från anrop till kapslade funktioner eller skript.</span><span class="sxs-lookup"><span data-stu-id="8b576-189">The custom error variable contains all errors generated by the command, including errors from calls to nested functions or scripts.</span></span>

#### <a name="informationaction"></a><span data-ttu-id="8b576-190">InformationAction</span><span class="sxs-lookup"><span data-stu-id="8b576-190">InformationAction</span></span>

<span data-ttu-id="8b576-191">Introducerades i PowerShell 5,0.</span><span class="sxs-lookup"><span data-stu-id="8b576-191">Introduced in PowerShell 5.0.</span></span> <span data-ttu-id="8b576-192">I det kommando eller skript där det används åsidosätter den gemensamma parametern **InformationAction** värdet för `$InformationPreference` variabeln Preference, vilket som standard är inställt på **SilentlyContinue**.</span><span class="sxs-lookup"><span data-stu-id="8b576-192">Within the command or script in which it's used, the **InformationAction** common parameter overrides the value of the `$InformationPreference` preference variable, which by default is set to **SilentlyContinue**.</span></span> <span data-ttu-id="8b576-193">När du använder `Write-Information` i ett skript med **InformationAction** , `Write-Information` visas värdena beroende på värdet för parametern **InformationAction** .</span><span class="sxs-lookup"><span data-stu-id="8b576-193">When you use `Write-Information` in a script with **InformationAction** , `Write-Information` values are shown depending on the value of the **InformationAction** parameter.</span></span> <span data-ttu-id="8b576-194">Mer information om `$InformationPreference` finns i [about_Preference_Variables](./about_Preference_Variables.md).</span><span class="sxs-lookup"><span data-stu-id="8b576-194">For more information about `$InformationPreference`, see [about_Preference_Variables](./about_Preference_Variables.md).</span></span>

```yaml
Type: ActionPreference
Aliases: ia
Accepted values: Suspend, Ignore, Inquire, Continue, Stop, SilentlyContinue

Required: False
Position: Named
Default value: Depends on preference variable
Accept pipeline input: False
Accept wildcard characters: False
```

<span data-ttu-id="8b576-195">`-InformationAction:Stop` stoppar ett kommando eller skript vid en förekomst av `Write-Information` kommandot.</span><span class="sxs-lookup"><span data-stu-id="8b576-195">`-InformationAction:Stop` stops a command or script at an occurrence of the `Write-Information` command.</span></span>

<span data-ttu-id="8b576-196">`-InformationAction:Ignore` undertrycker informations meddelandet och fortsätter att köra kommandot.</span><span class="sxs-lookup"><span data-stu-id="8b576-196">`-InformationAction:Ignore` suppresses the informational message and continues running the command.</span></span> <span data-ttu-id="8b576-197">Till skillnad från **SilentlyContinue** glömmer ignorera det informations meddelandet att **ignoreras** . informations meddelandet läggs inte till i informations data strömmen.</span><span class="sxs-lookup"><span data-stu-id="8b576-197">Unlike **SilentlyContinue** , **Ignore** completely forgets the informational message; it doesn't add the informational message to the information stream.</span></span>

<span data-ttu-id="8b576-198">`-InformationAction:Inquire` visar det informations meddelande som du anger i ett `Write-Information` kommando och frågar om du vill fortsätta.</span><span class="sxs-lookup"><span data-stu-id="8b576-198">`-InformationAction:Inquire` displays the informational message that you specify in a `Write-Information` command, then asks whether you want to continue.</span></span>

<span data-ttu-id="8b576-199">`-InformationAction:Continue` visar informations meddelandet och fortsätter att köra.</span><span class="sxs-lookup"><span data-stu-id="8b576-199">`-InformationAction:Continue` displays the informational message, and continues running.</span></span>

<span data-ttu-id="8b576-200">`-InformationAction:Suspend` stöds inte i PowerShell Core eftersom det endast är tillgängligt för arbets flöden.</span><span class="sxs-lookup"><span data-stu-id="8b576-200">`-InformationAction:Suspend` isn't supported on PowerShell Core as it is only available for workflows.</span></span>

<span data-ttu-id="8b576-201">`-InformationAction:SilentlyContinue` ingen påverkan eftersom informations meddelandet inte är (standard) visas och skriptet fortsätter utan avbrott.</span><span class="sxs-lookup"><span data-stu-id="8b576-201">`-InformationAction:SilentlyContinue` no effect as the informational message aren't (Default) displayed, and the script continues without interruption.</span></span>

> [!NOTE]
> <span data-ttu-id="8b576-202">Parametern **InformationAction** åsidosätter, men ersätter inte värdet för `$InformationAction` Preference-variabeln när parametern används i ett kommando för att köra ett skript eller en funktion.</span><span class="sxs-lookup"><span data-stu-id="8b576-202">The **InformationAction** parameter overrides, but does not replace the value of the `$InformationAction` preference variable when the parameter is used in a command to run a script or function.</span></span>

#### <a name="informationvariable"></a><span data-ttu-id="8b576-203">InformationVariable</span><span class="sxs-lookup"><span data-stu-id="8b576-203">InformationVariable</span></span>

<span data-ttu-id="8b576-204">Introducerades i PowerShell 5,0.</span><span class="sxs-lookup"><span data-stu-id="8b576-204">Introduced in PowerShell 5.0.</span></span> <span data-ttu-id="8b576-205">I det kommando eller skript där det används lagras den gemensamma **InformationVariable** -parametern i en variabel en sträng som du anger genom att lägga till `Write-Information` kommandot.</span><span class="sxs-lookup"><span data-stu-id="8b576-205">Within the command or script in which it's used, the **InformationVariable** common parameter stores in a variable a string that you specify by adding the `Write-Information` command.</span></span> <span data-ttu-id="8b576-206">`Write-Information`värdena visas beroende på värdet för den gemensamma parametern **InformationAction** . Om du inte lägger till **InformationAction** den gemensamma parametern InformationAction `Write-Information` visas strängarna beroende på värdet för `$InformationPreference` variabeln Preference.</span><span class="sxs-lookup"><span data-stu-id="8b576-206">`Write-Information` values are shown depending on the value of the **InformationAction** common parameter; if you don't add the **InformationAction** common parameter, `Write-Information` strings are shown depending on the value of the `$InformationPreference` preference variable.</span></span> <span data-ttu-id="8b576-207">Mer information om `$InformationPreference` finns i [about_Preference_Variables](./about_Preference_Variables.md).</span><span class="sxs-lookup"><span data-stu-id="8b576-207">For more information about `$InformationPreference`, see [about_Preference_Variables](./about_Preference_Variables.md).</span></span>

> [!NOTE]
> <span data-ttu-id="8b576-208">Variabeln information innehåller alla informations meddelanden som genereras av kommandot, inklusive informations meddelanden från anrop till kapslade funktioner eller skript.</span><span class="sxs-lookup"><span data-stu-id="8b576-208">The information variable contains all information messages generated by the command, including information messages from calls to nested functions or scripts.</span></span>

```yaml
Type: String
Aliases: iv

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

#### <a name="outbuffer"></a><span data-ttu-id="8b576-209">OutBuffer</span><span class="sxs-lookup"><span data-stu-id="8b576-209">OutBuffer</span></span>

<span data-ttu-id="8b576-210">Fastställer antalet objekt som ska samlas i en buffert innan objekt skickas via pipelinen.</span><span class="sxs-lookup"><span data-stu-id="8b576-210">Determines the number of objects to accumulate in a buffer before any objects are sent through the pipeline.</span></span> <span data-ttu-id="8b576-211">Om du utelämnar den här parametern skickas objekten när de genereras.</span><span class="sxs-lookup"><span data-stu-id="8b576-211">If you omit this parameter, objects are sent as they're generated.</span></span>

```yaml
Type: Int32
Aliases: ob

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

<span data-ttu-id="8b576-212">Den här resurs hanterings parametern är avsedd för avancerade användare.</span><span class="sxs-lookup"><span data-stu-id="8b576-212">This resource management parameter is designed for advanced users.</span></span> <span data-ttu-id="8b576-213">När du använder den här parametern skickar PowerShell data till nästa cmdlet i batchar för `OutBuffer + 1` .</span><span class="sxs-lookup"><span data-stu-id="8b576-213">When you use this parameter, PowerShell sends data to the next cmdlet in batches of `OutBuffer + 1`.</span></span>

<span data-ttu-id="8b576-214">I följande exempel visas mellan för att `ForEach-Object` bearbeta block som använder `Write-Host` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="8b576-214">The following example alternates displays between to `ForEach-Object` process blocks that use the `Write-Host` cmdlet.</span></span> <span data-ttu-id="8b576-215">Alternativen visas i batchar med 2 eller `OutBuffer + 1` .</span><span class="sxs-lookup"><span data-stu-id="8b576-215">The display alternates in batches of 2 or `OutBuffer + 1`.</span></span>

```powershell
1..4 | ForEach-Object {
        Write-Host "$($_): First"; $_
      } -OutBuffer 1 | ForEach-Object {
                        Write-Host "$($_): Second" }
```

```Output
1: First
2: First
1: Second
2: Second
3: First
4: First
3: Second
4: Second
```

#### <a name="outvariable"></a><span data-ttu-id="8b576-216">OutVariable</span><span class="sxs-lookup"><span data-stu-id="8b576-216">OutVariable</span></span>

<span data-ttu-id="8b576-217">Lagrar utdata-objekt från kommandot i den angivna variabeln, förutom att skicka utdata längs pipelinen.</span><span class="sxs-lookup"><span data-stu-id="8b576-217">Stores output objects from the command in the specified variable in addition to sending the output along the pipeline.</span></span>

```yaml
Type: String
Aliases: ov

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

<span data-ttu-id="8b576-218">Om du vill lägga till utdata i variabeln, i stället för att ersätta eventuella utdata som redan är lagrade där, skriver du ett plus tecken ( `+` ) före variabel namnet.</span><span class="sxs-lookup"><span data-stu-id="8b576-218">To add the output to the variable, instead of replacing any output that might already be stored there, type a plus sign (`+`) before the variable name.</span></span>

<span data-ttu-id="8b576-219">Följande kommando skapar till exempel `$out` variabeln och lagrar processobjektet i den:</span><span class="sxs-lookup"><span data-stu-id="8b576-219">For example, the following command creates the `$out` variable and stores the process object in it:</span></span>

```powershell
Get-Process PowerShell -OutVariable out
```

<span data-ttu-id="8b576-220">Följande kommando lägger till objektet bearbeta i `$out` variabeln:</span><span class="sxs-lookup"><span data-stu-id="8b576-220">The following command adds the process object to the `$out` variable:</span></span>

```powershell
Get-Process iexplore -OutVariable +out
```

<span data-ttu-id="8b576-221">Följande kommando visar innehållet i `$out` variabeln:</span><span class="sxs-lookup"><span data-stu-id="8b576-221">The following command displays the contents of the `$out` variable:</span></span>

```powershell
$out
```

> [!NOTE]
> <span data-ttu-id="8b576-222">Variabeln som skapas av parametern **devariable** är en `[System.Collections.ArrayList]` .</span><span class="sxs-lookup"><span data-stu-id="8b576-222">The variable created by the **OutVariable** parameter is a `[System.Collections.ArrayList]`.</span></span>

#### <a name="pipelinevariable"></a><span data-ttu-id="8b576-223">PipelineVariable</span><span class="sxs-lookup"><span data-stu-id="8b576-223">PipelineVariable</span></span>

<span data-ttu-id="8b576-224">**PipelineVariable** lagrar värdet för det aktuella pipeline-elementet som en variabel, för alla namngivna kommandon som det flödar genom pipelinen.</span><span class="sxs-lookup"><span data-stu-id="8b576-224">**PipelineVariable** stores the value of the current pipeline element as a variable, for any named command as it flows through the pipeline.</span></span>

```yaml
Type: String
Aliases: pv

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

<span data-ttu-id="8b576-225">Giltiga värden är strängar, samma som för alla variabel namn.</span><span class="sxs-lookup"><span data-stu-id="8b576-225">Valid values are strings, the same as for any variable names.</span></span>

<span data-ttu-id="8b576-226">Följande är ett exempel på hur **PipelineVariable** fungerar.</span><span class="sxs-lookup"><span data-stu-id="8b576-226">The following is an example of how **PipelineVariable** works.</span></span> <span data-ttu-id="8b576-227">I det här exemplet läggs parametern **PipelineVariable** till i ett `Foreach-Object` kommando för att lagra resultatet av kommandot i variabler.</span><span class="sxs-lookup"><span data-stu-id="8b576-227">In this example, the **PipelineVariable** parameter is added to a `Foreach-Object` command to store the results of the command in variables.</span></span> <span data-ttu-id="8b576-228">Ett intervall med tal, 1 till 10, är skickas i det första `Foreach-Object` kommandot, vars resultat lagras i en variabel med namnet **Left**.</span><span class="sxs-lookup"><span data-stu-id="8b576-228">A range of numbers, 1 to 10, are piped into the first `Foreach-Object` command, the results of which are stored in a variable named **Left**.</span></span>

<span data-ttu-id="8b576-229">Resultatet från det första `Foreach-Object` kommandot är skickas i ett andra `Foreach-Object` kommando, som filtrerar objekten som returneras av det första `Foreach-Object` kommandot.</span><span class="sxs-lookup"><span data-stu-id="8b576-229">The results of the first `Foreach-Object` command are piped into a second `Foreach-Object` command, which filters the objects returned by the first `Foreach-Object` command.</span></span> <span data-ttu-id="8b576-230">Resultatet av det andra kommandot lagras i en variabel med namnet **Right**.</span><span class="sxs-lookup"><span data-stu-id="8b576-230">The results of the second command are stored in a variable named **Right**.</span></span>

<span data-ttu-id="8b576-231">I det tredje `Foreach-Object` kommandot bearbetas resultaten av de första två `Foreach-Object` skickas-kommandona som representeras av variablerna **Left** och **Right** , med hjälp av en multiplikation-operator.</span><span class="sxs-lookup"><span data-stu-id="8b576-231">In the third `Foreach-Object` command, the results of the first two `Foreach-Object` piped commands, represented by the variables **Left** and **Right** , are processed by using a multiplication operator.</span></span> <span data-ttu-id="8b576-232">Kommandot instruerar objekt som lagras i de **vänstra** och **högra** variablerna att multipliceras och anger att resultaten ska visas som "medlemmar i vänster intervall \* höger intervall medlem = produkt".</span><span class="sxs-lookup"><span data-stu-id="8b576-232">The command instructs objects stored in the **Left** and **Right** variables to be multiplied, and specifies that the results should be displayed as "Left range member \* Right range member = product".</span></span>

```powershell
1..10 | Foreach-Object -PipelineVariable Left -Process { $_ } |
  Foreach-Object -PV Right -Process { 1..10 } |
  Foreach-Object -Process { "$Left * $Right = " + ($Left*$Right) }
```

```output
1 * 1 = 1
1 * 2 = 2
1 * 3 = 3
1 * 4 = 4
1 * 5 = 5
...
```

#### <a name="verbose"></a><span data-ttu-id="8b576-233">Verbose</span><span class="sxs-lookup"><span data-stu-id="8b576-233">Verbose</span></span>

<span data-ttu-id="8b576-234">Visar detaljerad information om den åtgärd som utförs av kommandot.</span><span class="sxs-lookup"><span data-stu-id="8b576-234">Displays detailed information about the operation done by the command.</span></span> <span data-ttu-id="8b576-235">Den här informationen liknar informationen i en spårning eller i en transaktions logg.</span><span class="sxs-lookup"><span data-stu-id="8b576-235">This information resembles the information in a trace or in a transaction log.</span></span> <span data-ttu-id="8b576-236">Den här parametern fungerar bara när kommandot genererar ett utförligt meddelande.</span><span class="sxs-lookup"><span data-stu-id="8b576-236">This parameter works only when the command generates a verbose message.</span></span> <span data-ttu-id="8b576-237">Den här parametern fungerar till exempel när ett kommando innehåller `Write-Verbose` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="8b576-237">For example, this parameter works when a command contains the `Write-Verbose` cmdlet.</span></span>

```yaml
Type: SwitchParameter
Aliases: vb

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

<span data-ttu-id="8b576-238">Den **utförliga** parametern åsidosätter värdet för `$VerbosePreference` variabeln för det aktuella kommandot.</span><span class="sxs-lookup"><span data-stu-id="8b576-238">The **Verbose** parameter overrides the value of the `$VerbosePreference` variable for the current command.</span></span> <span data-ttu-id="8b576-239">Eftersom standardvärdet för `$VerbosePreference` variabeln är **SilentlyContinue** visas inte utförliga meddelanden som standard.</span><span class="sxs-lookup"><span data-stu-id="8b576-239">Because the default value of the `$VerbosePreference` variable is **SilentlyContinue** , verbose messages aren't displayed by default.</span></span>

<span data-ttu-id="8b576-240">`-Verbose:$true` har samma resultat som `-Verbose`</span><span class="sxs-lookup"><span data-stu-id="8b576-240">`-Verbose:$true` has the same effect as `-Verbose`</span></span>

<span data-ttu-id="8b576-241">`-Verbose:$false` förhindrar visning av utförliga meddelanden.</span><span class="sxs-lookup"><span data-stu-id="8b576-241">`-Verbose:$false` suppresses the display of verbose messages.</span></span> <span data-ttu-id="8b576-242">Använd den här parametern när värdet för `$VerbosePreference` inte är **SilentlyContinue** (standard).</span><span class="sxs-lookup"><span data-stu-id="8b576-242">Use this parameter when the value of `$VerbosePreference` isn't **SilentlyContinue** (the default).</span></span>

#### <a name="warningaction"></a><span data-ttu-id="8b576-243">WarningAction</span><span class="sxs-lookup"><span data-stu-id="8b576-243">WarningAction</span></span>

<span data-ttu-id="8b576-244">Anger hur cmdleten svarar på en varning från kommandot.</span><span class="sxs-lookup"><span data-stu-id="8b576-244">Determines how the cmdlet responds to a warning from the command.</span></span> <span data-ttu-id="8b576-245">**Fortsätt** är standardvärdet.</span><span class="sxs-lookup"><span data-stu-id="8b576-245">**Continue** is the default value.</span></span> <span data-ttu-id="8b576-246">Den här parametern fungerar bara när kommandot genererar ett varnings meddelande.</span><span class="sxs-lookup"><span data-stu-id="8b576-246">This parameter works only when the command generates a warning message.</span></span> <span data-ttu-id="8b576-247">Den här parametern fungerar till exempel när ett kommando innehåller `Write-Warning` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="8b576-247">For example, this parameter works when a command contains the `Write-Warning` cmdlet.</span></span>

```yaml
Type: ActionPreference
Aliases: wa
Accepted values: Suspend, Ignore, Inquire, Continue, Stop, SilentlyContinue

Required: False
Position: Named
Default value: Depends on preference variable
Accept pipeline input: False
Accept wildcard characters: False
```

<span data-ttu-id="8b576-248">Parametern **WarningAction** åsidosätter värdet för `$WarningPreference` variabeln för det aktuella kommandot.</span><span class="sxs-lookup"><span data-stu-id="8b576-248">The **WarningAction** parameter overrides the value of the `$WarningPreference` variable for the current command.</span></span> <span data-ttu-id="8b576-249">Eftersom standardvärdet för `$WarningPreference` variabeln **fortsätter** visas varningar och körningen fortsätter om du inte använder parametern **WarningAction** .</span><span class="sxs-lookup"><span data-stu-id="8b576-249">Because the default value of the `$WarningPreference` variable is **Continue** , warnings are displayed and execution continues unless you use the **WarningAction** parameter.</span></span>

<span data-ttu-id="8b576-250">`-WarningAction:Continue` visar varnings meddelandena och fortsätter att köra kommandot.</span><span class="sxs-lookup"><span data-stu-id="8b576-250">`-WarningAction:Continue` displays the warning messages and continues executing the command.</span></span> <span data-ttu-id="8b576-251">`Continue` används som standard.</span><span class="sxs-lookup"><span data-stu-id="8b576-251">`Continue` is the default.</span></span>

<span data-ttu-id="8b576-252">`-WarningAction:Inquire` visar varnings meddelandet och du uppmanas att bekräfta innan du fortsätter körningen.</span><span class="sxs-lookup"><span data-stu-id="8b576-252">`-WarningAction:Inquire` displays the warning message and prompts you for confirmation before continuing execution.</span></span> <span data-ttu-id="8b576-253">Det här värdet används sällan.</span><span class="sxs-lookup"><span data-stu-id="8b576-253">This value is rarely used.</span></span>

<span data-ttu-id="8b576-254">`-WarningAction:SilentlyContinue` undertrycker varnings meddelandet och fortsätter att köra kommandot.</span><span class="sxs-lookup"><span data-stu-id="8b576-254">`-WarningAction:SilentlyContinue` suppresses the warning message and continues executing the command.</span></span>

<span data-ttu-id="8b576-255">`-WarningAction:Stop` visar varnings meddelandet och stoppar körningen av kommandot.</span><span class="sxs-lookup"><span data-stu-id="8b576-255">`-WarningAction:Stop` displays the warning message and stops executing the command.</span></span>

> [!NOTE]
> <span data-ttu-id="8b576-256">Parametern **WarningAction** åsidosätter, men ersätter inte värdet för `$WarningAction` Preference-variabeln när parametern används i ett kommando för att köra ett skript eller en funktion.</span><span class="sxs-lookup"><span data-stu-id="8b576-256">The **WarningAction** parameter overrides, but does not replace the value of the `$WarningAction` preference variable when the parameter is used in a command to run a script or function.</span></span>

#### <a name="warningvariable"></a><span data-ttu-id="8b576-257">WarningVariable</span><span class="sxs-lookup"><span data-stu-id="8b576-257">WarningVariable</span></span>

<span data-ttu-id="8b576-258">Lagrar varningar om kommandot i den angivna variabeln.</span><span class="sxs-lookup"><span data-stu-id="8b576-258">Stores warnings about the command in the specified variable.</span></span>

```yaml
Type: String
Aliases: wv

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

<span data-ttu-id="8b576-259">Alla genererade varningar sparas i variabeln även om varningarna inte visas för användaren.</span><span class="sxs-lookup"><span data-stu-id="8b576-259">All generated warnings are saved in the variable even if the warnings aren't displayed to the user.</span></span>

<span data-ttu-id="8b576-260">Om du vill lägga till varningar i variabel innehållet, i stället för att ersätta eventuella varningar som redan är lagrade där, skriver du ett plus tecken ( `+` ) före variabel namnet.</span><span class="sxs-lookup"><span data-stu-id="8b576-260">To append the warnings to the variable content, instead of replacing any warnings that might already be stored there, type a plus sign (`+`) before the variable name.</span></span>

<span data-ttu-id="8b576-261">Till exempel skapar följande kommando `$a` variabeln och lagrar sedan alla varningar:</span><span class="sxs-lookup"><span data-stu-id="8b576-261">For example, the following command creates the `$a` variable and then stores any warnings in it:</span></span>

```powershell
Get-Process -Id 6 -WarningVariable a
```

<span data-ttu-id="8b576-262">Följande kommando lägger till eventuella varningar till `$a` variabeln:</span><span class="sxs-lookup"><span data-stu-id="8b576-262">The following command adds any warnings to the `$a` variable:</span></span>

```powershell
Get-Process -Id 2 -WarningVariable +a
```

<span data-ttu-id="8b576-263">Följande kommando visar innehållet i `$a` :</span><span class="sxs-lookup"><span data-stu-id="8b576-263">The following command displays the contents of `$a`:</span></span>

```powershell
$a
```

<span data-ttu-id="8b576-264">Du kan använda den här parametern för att skapa en variabel som bara innehåller varningar från vissa kommandon.</span><span class="sxs-lookup"><span data-stu-id="8b576-264">You can use this parameter to create a variable that contains only warnings from specific commands.</span></span> <span data-ttu-id="8b576-265">Du kan använda mat ris notation, till exempel `$a[0]` eller `$warning[1,2]` för att referera till vissa varningar som lagras i variabeln.</span><span class="sxs-lookup"><span data-stu-id="8b576-265">You can use array notation, such as `$a[0]` or `$warning[1,2]` to refer to specific warnings stored in the variable.</span></span>

> [!NOTE]
> <span data-ttu-id="8b576-266">Varnings variabeln innehåller alla varningar som genererats av kommandot, inklusive varningar från anrop till kapslade funktioner eller skript.</span><span class="sxs-lookup"><span data-stu-id="8b576-266">The warning variable contains all warnings generated by the command, including warnings from calls to nested functions or scripts.</span></span>
### <a name="risk-management-parameter-descriptions"></a><span data-ttu-id="8b576-267">Parameter beskrivningar för risk hantering</span><span class="sxs-lookup"><span data-stu-id="8b576-267">Risk Management Parameter Descriptions</span></span>

#### <a name="whatif"></a><span data-ttu-id="8b576-268">WhatIf</span><span class="sxs-lookup"><span data-stu-id="8b576-268">WhatIf</span></span>

<span data-ttu-id="8b576-269">Visar ett meddelande som beskriver kommandots effekter i stället för att köra kommandot.</span><span class="sxs-lookup"><span data-stu-id="8b576-269">Displays a message that describes the effect of the command, instead of executing the command.</span></span>

```yaml
Type: SwitchParameter
Aliases: wi

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

<span data-ttu-id="8b576-270">Parametern **whatIf** åsidosätter värdet för `$WhatIfPreference` variabeln för det aktuella kommandot.</span><span class="sxs-lookup"><span data-stu-id="8b576-270">The **WhatIf** parameter overrides the value of the `$WhatIfPreference` variable for the current command.</span></span> <span data-ttu-id="8b576-271">Eftersom standardvärdet för `$WhatIfPreference` variabeln är 0 (inaktiverat), utförs inte **whatIf** -beteendet utan parametern **whatIf** .</span><span class="sxs-lookup"><span data-stu-id="8b576-271">Because the default value of the `$WhatIfPreference` variable is 0 (disabled), **WhatIf** behavior isn't done without the **WhatIf** parameter.</span></span> <span data-ttu-id="8b576-272">Mer information finns i [about_Preference_Variables](about_Preference_Variables.md)</span><span class="sxs-lookup"><span data-stu-id="8b576-272">For more information, see [about_Preference_Variables](about_Preference_Variables.md)</span></span>

<span data-ttu-id="8b576-273">`-WhatIf:$true` har samma resultat som `-WhatIf` .</span><span class="sxs-lookup"><span data-stu-id="8b576-273">`-WhatIf:$true` has the same effect as `-WhatIf`.</span></span>

<span data-ttu-id="8b576-274">`-WhatIf:$false` ignorerar det automatiska beteendet i WhatIf som resulterar i när värdet för `$WhatIfPreference` variabeln är 1.</span><span class="sxs-lookup"><span data-stu-id="8b576-274">`-WhatIf:$false` suppresses the automatic WhatIf behavior that results when the value of the `$WhatIfPreference` variable is 1.</span></span>

<span data-ttu-id="8b576-275">Följande kommando använder till exempel `-WhatIf` parametern i ett `Remove-Item` kommando:</span><span class="sxs-lookup"><span data-stu-id="8b576-275">For example, the following command uses the `-WhatIf` parameter in a `Remove-Item` command:</span></span>

```powershell
Remove-Item Date.csv -WhatIf
```

<span data-ttu-id="8b576-276">I stället för att ta bort objektet, visar PowerShell de åtgärder som ska utföras och de objekt som skulle påverkas.</span><span class="sxs-lookup"><span data-stu-id="8b576-276">Instead of removing the item, PowerShell lists the operations it would do and the items that would be affected.</span></span> <span data-ttu-id="8b576-277">Det här kommandot ger följande utdata:</span><span class="sxs-lookup"><span data-stu-id="8b576-277">This command produces the following output:</span></span>

```output
What if: Performing operation "Remove File" on
Target "C:\ps-test\date.csv".
```

#### <a name="confirm"></a><span data-ttu-id="8b576-278">Bekräfta</span><span class="sxs-lookup"><span data-stu-id="8b576-278">Confirm</span></span>

<span data-ttu-id="8b576-279">Du uppmanas att bekräfta innan du kör kommandot.</span><span class="sxs-lookup"><span data-stu-id="8b576-279">Prompts you for confirmation before executing the command.</span></span>

```yaml
Type: SwitchParameter
Aliases: cf

Required: False
Position: Named
Default value: Depends on preference variable
Accept pipeline input: False
Accept wildcard characters: False
```

<span data-ttu-id="8b576-280">Parametern **Confirm** åsidosätter värdet för `$ConfirmPreference` variabeln för det aktuella kommandot.</span><span class="sxs-lookup"><span data-stu-id="8b576-280">The **Confirm** parameter overrides the value of the `$ConfirmPreference` variable for the current command.</span></span> <span data-ttu-id="8b576-281">Standardvärdet är True.</span><span class="sxs-lookup"><span data-stu-id="8b576-281">The default value is true.</span></span> <span data-ttu-id="8b576-282">Mer information finns i [about_Preference_Variables](about_Preference_Variables.md)</span><span class="sxs-lookup"><span data-stu-id="8b576-282">For more information, see [about_Preference_Variables](about_Preference_Variables.md)</span></span>

<span data-ttu-id="8b576-283">`-Confirm:$true` har samma resultat som `-Confirm` .</span><span class="sxs-lookup"><span data-stu-id="8b576-283">`-Confirm:$true` has the same effect as `-Confirm`.</span></span>

<span data-ttu-id="8b576-284">`-Confirm:$false` förhindrar automatisk bekräftelse, som inträffar när värdet för `$ConfirmPreference` är mindre än eller lika med den beräknade risken för cmdleten.</span><span class="sxs-lookup"><span data-stu-id="8b576-284">`-Confirm:$false` suppresses automatic confirmation, which occurs when the value of `$ConfirmPreference` is less than or equal to the estimated risk of the cmdlet.</span></span>

<span data-ttu-id="8b576-285">Följande kommando använder till exempel parametern **Confirm** med ett `Remove-Item` kommando.</span><span class="sxs-lookup"><span data-stu-id="8b576-285">For example, the following command uses the **Confirm** parameter with a `Remove-Item` command.</span></span> <span data-ttu-id="8b576-286">Innan objektet tas bort, visar PowerShell de åtgärder som skulle utföras och de objekt som skulle påverkas, och ber om godkännande.</span><span class="sxs-lookup"><span data-stu-id="8b576-286">Before removing the item, PowerShell lists the operations it would do and the items that would be affected, and asks for approval.</span></span>

```
PS C:\ps-test> Remove-Item tmp*.txt -Confirm

Confirm
Are you sure you want to perform this action?
Performing operation "Remove File" on Target " C:\ps-test\tmp1.txt
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend
[?] Help (default is "Y"):
```

<span data-ttu-id="8b576-287">Alternativen för att bekräfta svar är följande:</span><span class="sxs-lookup"><span data-stu-id="8b576-287">The Confirm response options are as follows:</span></span>

|<span data-ttu-id="8b576-288">Svarsåtgärder</span><span class="sxs-lookup"><span data-stu-id="8b576-288">Response</span></span>       |<span data-ttu-id="8b576-289">Resultat</span><span class="sxs-lookup"><span data-stu-id="8b576-289">Result</span></span>                                                     |
|---------------|-----------------------------------------------------------|
|<span data-ttu-id="8b576-290">Ja (Y)</span><span class="sxs-lookup"><span data-stu-id="8b576-290">Yes (Y)</span></span>        |<span data-ttu-id="8b576-291">Utför åtgärden.</span><span class="sxs-lookup"><span data-stu-id="8b576-291">Perform the action.</span></span>                                        |
|<span data-ttu-id="8b576-292">Ja till alla (A)</span><span class="sxs-lookup"><span data-stu-id="8b576-292">Yes to All (A)</span></span> |<span data-ttu-id="8b576-293">Utföra alla åtgärder och utelämna efterföljande bekräfta-frågor</span><span class="sxs-lookup"><span data-stu-id="8b576-293">Perform all actions and suppress subsequent Confirm queries</span></span>|
|               |<span data-ttu-id="8b576-294">för det här kommandot.</span><span class="sxs-lookup"><span data-stu-id="8b576-294">for this command.</span></span>                                          |
|<span data-ttu-id="8b576-295">Nej (N):</span><span class="sxs-lookup"><span data-stu-id="8b576-295">No (N):</span></span>        |<span data-ttu-id="8b576-296">Utför inte åtgärden.</span><span class="sxs-lookup"><span data-stu-id="8b576-296">Do not perform the action.</span></span>                                 |
|<span data-ttu-id="8b576-297">Nej till alla (L):</span><span class="sxs-lookup"><span data-stu-id="8b576-297">No to All (L):</span></span> |<span data-ttu-id="8b576-298">Utför inga åtgärder och ignorera sedan efterföljande bekräftelse</span><span class="sxs-lookup"><span data-stu-id="8b576-298">Do not perform any actions and suppress subsequent Confirm</span></span> |
|               |<span data-ttu-id="8b576-299">frågor för det här kommandot.</span><span class="sxs-lookup"><span data-stu-id="8b576-299">queries for this command.</span></span>                                  |
|<span data-ttu-id="8b576-300">Pausa (S):</span><span class="sxs-lookup"><span data-stu-id="8b576-300">Suspend (S):</span></span>   |<span data-ttu-id="8b576-301">Pausa kommandot och skapa en tillfällig session.</span><span class="sxs-lookup"><span data-stu-id="8b576-301">Pause the command and create a temporary session.</span></span>          |
|<span data-ttu-id="8b576-302">Hjälp (?)</span><span class="sxs-lookup"><span data-stu-id="8b576-302">Help (?)</span></span>       |<span data-ttu-id="8b576-303">Visa hjälp för de här alternativen.</span><span class="sxs-lookup"><span data-stu-id="8b576-303">Display help for these options.</span></span>                            |

<span data-ttu-id="8b576-304">Alternativet **PAUSE** placerar kommandot stoppad och skapar en tillfällig kapslad session där du kan arbeta tills du är redo att välja ett **Bekräfta** -alternativ.</span><span class="sxs-lookup"><span data-stu-id="8b576-304">The **Suspend** option places the command on hold and creates a temporary nested session in which you can work until you're ready to choose a **Confirm** option.</span></span> <span data-ttu-id="8b576-305">Kommando tolken för den kapslade sessionen har två extra försiktighets åtgärder (>>) för att indikera att det är en underordnad åtgärd för det ursprungliga överordnade kommandot.</span><span class="sxs-lookup"><span data-stu-id="8b576-305">The command prompt for the nested session has two extra carets (>>) to indicate that it's a child operation of the original parent command.</span></span> <span data-ttu-id="8b576-306">Du kan köra kommandon och skript i den kapslade sessionen.</span><span class="sxs-lookup"><span data-stu-id="8b576-306">You can run commands and scripts in the nested session.</span></span> <span data-ttu-id="8b576-307">Om du vill avsluta den kapslade sessionen och återgå till bekräfta-alternativen för det ursprungliga kommandot skriver du "Exit".</span><span class="sxs-lookup"><span data-stu-id="8b576-307">To end the nested session and return to the Confirm options for the original command, type "exit".</span></span>

<span data-ttu-id="8b576-308">I följande exempel används **paus** alternativen för att stoppa ett kommando tillfälligt medan användaren kontrollerar hjälpen för en kommando parameter.</span><span class="sxs-lookup"><span data-stu-id="8b576-308">In the following example, the **Suspend** option (S) is used to halt a command temporarily while the user checks the help for a command parameter.</span></span> <span data-ttu-id="8b576-309">När du har hämtat den information som behövs avslutar du den kapslade prompten och väljer Ja (y) som svar på bekräfta fråga.</span><span class="sxs-lookup"><span data-stu-id="8b576-309">After obtaining the needed information, the user types "exit" to end the nested prompt and then selects the Yes (y) response to the Confirm query.</span></span>

```
PS C:\ps-test> New-Item -ItemType File -Name Test.txt -Confirm

Confirm
Are you sure you want to perform this action?

Performing operation "Create File" on Target "Destination:
C:\ps-test\test.txt".
[Y] Yes [A] Yes to All [N] No [L] No to All [S] Suspend [?] Help (default
is "Y"): s

PS C:\ps-test> Get-Help New-Item -Parameter ItemType

-ItemType <string>
Specifies the provider-specified type of the new item.

Required?                    false
Position?                    named
Default value
Accept pipeline input?       true (ByPropertyName)
Accept wildcard characters?  false

PS C:\ps-test> exit

Confirm
Are you sure you want to perform this action?
Performing operation "Create File" on Target "Destination: C:\ps-test\test
.txt".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (defau
lt is "Y"): y

Directory: C:\ps-test

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
-a---         8/27/2010   2:41 PM          0 test.txt
```

## <a name="keywords"></a><span data-ttu-id="8b576-310">RESERVERADE</span><span class="sxs-lookup"><span data-stu-id="8b576-310">KEYWORDS</span></span>

<span data-ttu-id="8b576-311">about_Common_Parameters</span><span class="sxs-lookup"><span data-stu-id="8b576-311">about_Common_Parameters</span></span>

## <a name="see-also"></a><span data-ttu-id="8b576-312">SE ÄVEN</span><span class="sxs-lookup"><span data-stu-id="8b576-312">SEE ALSO</span></span>

[<span data-ttu-id="8b576-313">about_Preference_Variables</span><span class="sxs-lookup"><span data-stu-id="8b576-313">about_Preference_Variables</span></span>](about_Preference_Variables.md)

[<span data-ttu-id="8b576-314">Skriv-debug</span><span class="sxs-lookup"><span data-stu-id="8b576-314">Write-Debug</span></span>](xref:Microsoft.PowerShell.Utility.Write-Debug)

[<span data-ttu-id="8b576-315">Skriv varning</span><span class="sxs-lookup"><span data-stu-id="8b576-315">Write-Warning</span></span>](xref:Microsoft.PowerShell.Utility.Write-Warning)

[<span data-ttu-id="8b576-316">Skriv-fel</span><span class="sxs-lookup"><span data-stu-id="8b576-316">Write-Error</span></span>](xref:Microsoft.PowerShell.Utility.Write-Error)

[<span data-ttu-id="8b576-317">Skriv-verbose</span><span class="sxs-lookup"><span data-stu-id="8b576-317">Write-Verbose</span></span>](xref:Microsoft.PowerShell.Utility.Write-Verbose)
