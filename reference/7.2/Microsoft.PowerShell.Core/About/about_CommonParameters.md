---
description: Beskriver de parametrar som kan användas med vilken cmdlet som helst.
Locale: en-US
ms.date: 11/26/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_CommonParameters
ms.openlocfilehash: 44503e9c251cd3cccf9b879ceb71262c65d8e5e9
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94708898"
---
# <a name="about-commonparameters"></a><span data-ttu-id="46319-103">Om CommonParameters</span><span class="sxs-lookup"><span data-stu-id="46319-103">About CommonParameters</span></span>

## <a name="short-description"></a><span data-ttu-id="46319-104">KORT BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="46319-104">SHORT DESCRIPTION</span></span>

<span data-ttu-id="46319-105">Beskriver de parametrar som kan användas med vilken cmdlet som helst.</span><span class="sxs-lookup"><span data-stu-id="46319-105">Describes the parameters that can be used with any cmdlet.</span></span>

## <a name="long-description"></a><span data-ttu-id="46319-106">LÅNG BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="46319-106">LONG DESCRIPTION</span></span>

<span data-ttu-id="46319-107">De gemensamma parametrarna är en uppsättning cmdlet-parametrar som du kan använda med valfri cmdlet.</span><span class="sxs-lookup"><span data-stu-id="46319-107">The common parameters are a set of cmdlet parameters that you can use with any cmdlet.</span></span> <span data-ttu-id="46319-108">De implementeras av PowerShell, inte av cmdlet-utvecklaren, och de är automatiskt tillgängliga för alla cmdletar.</span><span class="sxs-lookup"><span data-stu-id="46319-108">They're implemented by PowerShell, not by the cmdlet developer, and they're automatically available to any cmdlet.</span></span>

<span data-ttu-id="46319-109">Du kan använda de gemensamma parametrarna med valfri cmdlet, men de kanske inte har någon påverkan på alla cmdletar.</span><span class="sxs-lookup"><span data-stu-id="46319-109">You can use the common parameters with any cmdlet, but they might not have an effect on all cmdlets.</span></span> <span data-ttu-id="46319-110">Om en cmdlet till exempel inte genererar några utförliga utdata, har den **utförliga** gemensamma parametern ingen effekt.</span><span class="sxs-lookup"><span data-stu-id="46319-110">For example, if a cmdlet doesn't generate any verbose output, using the **Verbose** common parameter has no effect.</span></span>

<span data-ttu-id="46319-111">De gemensamma parametrarna är också tillgängliga för avancerade funktioner som använder attributet **CmdletBinding** eller attributet **parameter** .</span><span class="sxs-lookup"><span data-stu-id="46319-111">The common parameters are also available on advanced functions that use the **CmdletBinding** attribute or the **Parameter** attribute.</span></span>

<span data-ttu-id="46319-112">Flera vanliga parametrar åsidosätter systemstandardinställningar eller inställningar som du anger med hjälp av variablerna för PowerShell-inställningar.</span><span class="sxs-lookup"><span data-stu-id="46319-112">Several common parameters override system defaults or preferences that you set by using the PowerShell preference variables.</span></span> <span data-ttu-id="46319-113">Till skillnad från inställningarna för variabler påverkar de gemensamma parametrarna bara de kommandon som de används i.</span><span class="sxs-lookup"><span data-stu-id="46319-113">Unlike the preference variables, the common parameters affect only the commands in which they're used.</span></span>

<span data-ttu-id="46319-114">Mer information finns i [about_Preference_Variables](./about_Preference_Variables.md).</span><span class="sxs-lookup"><span data-stu-id="46319-114">For more information, see [about_Preference_Variables](./about_Preference_Variables.md).</span></span>

<span data-ttu-id="46319-115">I följande lista visas de gemensamma parametrarna.</span><span class="sxs-lookup"><span data-stu-id="46319-115">The following list displays the common parameters.</span></span> <span data-ttu-id="46319-116">Deras alias visas inom parentes.</span><span class="sxs-lookup"><span data-stu-id="46319-116">Their aliases are listed in parentheses.</span></span>

- <span data-ttu-id="46319-117">**Felsöka** (dB)</span><span class="sxs-lookup"><span data-stu-id="46319-117">**Debug** (db)</span></span>
- <span data-ttu-id="46319-118">**ErrorAction** (EA)</span><span class="sxs-lookup"><span data-stu-id="46319-118">**ErrorAction** (ea)</span></span>
- <span data-ttu-id="46319-119">**ErrorVariable** (EV)</span><span class="sxs-lookup"><span data-stu-id="46319-119">**ErrorVariable** (ev)</span></span>
- <span data-ttu-id="46319-120">**InformationAction** (Infa)</span><span class="sxs-lookup"><span data-stu-id="46319-120">**InformationAction** (infa)</span></span>
- <span data-ttu-id="46319-121">**InformationVariable** (IV)</span><span class="sxs-lookup"><span data-stu-id="46319-121">**InformationVariable** (iv)</span></span>
- <span data-ttu-id="46319-122">**Avvariabel** (OV)</span><span class="sxs-lookup"><span data-stu-id="46319-122">**OutVariable** (ov)</span></span>
- <span data-ttu-id="46319-123">**Utbuffer** (OB)</span><span class="sxs-lookup"><span data-stu-id="46319-123">**OutBuffer** (ob)</span></span>
- <span data-ttu-id="46319-124">**PipelineVariable** (PV)</span><span class="sxs-lookup"><span data-stu-id="46319-124">**PipelineVariable** (pv)</span></span>
- <span data-ttu-id="46319-125">**Verbose** (VB)</span><span class="sxs-lookup"><span data-stu-id="46319-125">**Verbose** (vb)</span></span>
- <span data-ttu-id="46319-126">**WarningAction** (WA)</span><span class="sxs-lookup"><span data-stu-id="46319-126">**WarningAction** (wa)</span></span>
- <span data-ttu-id="46319-127">**WarningVariable** (WV)</span><span class="sxs-lookup"><span data-stu-id="46319-127">**WarningVariable** (wv)</span></span>

<span data-ttu-id="46319-128">**Åtgärds** parametrarna är **Åtgärdsinställning** -typnamn.</span><span class="sxs-lookup"><span data-stu-id="46319-128">The **Action** parameters are **ActionPreference** type values.</span></span>
<span data-ttu-id="46319-129">**Åtgärdsinställning** är en uppräkning med följande värden:</span><span class="sxs-lookup"><span data-stu-id="46319-129">**ActionPreference** is an enumeration with the following values:</span></span>

| <span data-ttu-id="46319-130">Namn</span><span class="sxs-lookup"><span data-stu-id="46319-130">Name</span></span>             | <span data-ttu-id="46319-131">Värde</span><span class="sxs-lookup"><span data-stu-id="46319-131">Value</span></span> |
|------------------|-------|
| <span data-ttu-id="46319-132">Suspend</span><span class="sxs-lookup"><span data-stu-id="46319-132">Suspend</span></span>          | <span data-ttu-id="46319-133">5</span><span class="sxs-lookup"><span data-stu-id="46319-133">5</span></span>     |
| <span data-ttu-id="46319-134">Ignorera</span><span class="sxs-lookup"><span data-stu-id="46319-134">Ignore</span></span>           | <span data-ttu-id="46319-135">4</span><span class="sxs-lookup"><span data-stu-id="46319-135">4</span></span>     |
| <span data-ttu-id="46319-136">Inquire</span><span class="sxs-lookup"><span data-stu-id="46319-136">Inquire</span></span>          | <span data-ttu-id="46319-137">3</span><span class="sxs-lookup"><span data-stu-id="46319-137">3</span></span>     |
| <span data-ttu-id="46319-138">Fortsätt</span><span class="sxs-lookup"><span data-stu-id="46319-138">Continue</span></span>         | <span data-ttu-id="46319-139">2</span><span class="sxs-lookup"><span data-stu-id="46319-139">2</span></span>     |
| <span data-ttu-id="46319-140">Stoppa</span><span class="sxs-lookup"><span data-stu-id="46319-140">Stop</span></span>             | <span data-ttu-id="46319-141">1</span><span class="sxs-lookup"><span data-stu-id="46319-141">1</span></span>     |
| <span data-ttu-id="46319-142">SilentlyContinue</span><span class="sxs-lookup"><span data-stu-id="46319-142">SilentlyContinue</span></span> | <span data-ttu-id="46319-143">0</span><span class="sxs-lookup"><span data-stu-id="46319-143">0</span></span>     |

<span data-ttu-id="46319-144">Du kan använda namnet eller värdet med parametern.</span><span class="sxs-lookup"><span data-stu-id="46319-144">You may use the name or the value with the parameter.</span></span>

<span data-ttu-id="46319-145">Förutom de gemensamma parametrarna erbjuder många cmdlets parametrar för risk minskning.</span><span class="sxs-lookup"><span data-stu-id="46319-145">In addition to the common parameters, many cmdlets offer risk mitigation parameters.</span></span> <span data-ttu-id="46319-146">Cmdletar som innebär risk för systemet eller användar data erbjuder vanligt vis dessa parametrar.</span><span class="sxs-lookup"><span data-stu-id="46319-146">Cmdlets that involve risk to the system or to user data usually offer these parameters.</span></span>

<span data-ttu-id="46319-147">Parametrarna för risk minskning är:</span><span class="sxs-lookup"><span data-stu-id="46319-147">The risk mitigation parameters are:</span></span>

- <span data-ttu-id="46319-148">**WhatIf** (Wi)</span><span class="sxs-lookup"><span data-stu-id="46319-148">**WhatIf** (wi)</span></span>
- <span data-ttu-id="46319-149">**Bekräfta** (CF)</span><span class="sxs-lookup"><span data-stu-id="46319-149">**Confirm** (cf)</span></span>

### <a name="common-parameter-descriptions"></a><span data-ttu-id="46319-150">VANLIGA PARAMETER BESKRIVNINGAR</span><span class="sxs-lookup"><span data-stu-id="46319-150">COMMON PARAMETER DESCRIPTIONS</span></span>

#### <a name="debug"></a><span data-ttu-id="46319-151">Felsökning</span><span class="sxs-lookup"><span data-stu-id="46319-151">Debug</span></span>

<span data-ttu-id="46319-152">Visar information om program nivå om den åtgärd som utförs av kommandot.</span><span class="sxs-lookup"><span data-stu-id="46319-152">Displays programmer-level detail about the operation done by the command.</span></span> <span data-ttu-id="46319-153">Den här parametern fungerar bara när kommandot genererar ett fel söknings meddelande.</span><span class="sxs-lookup"><span data-stu-id="46319-153">This parameter works only when the command generates a debugging message.</span></span> <span data-ttu-id="46319-154">Den här parametern fungerar till exempel när ett kommando innehåller `Write-Debug` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="46319-154">For example, this parameter works when a command contains the `Write-Debug` cmdlet.</span></span>

```yaml
Type: SwitchParameter
Aliases: db

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

<span data-ttu-id="46319-155">Som standard visas fel söknings meddelanden eftersom värdet för `$DebugPreference` variabeln är **SilentlyContinue**.</span><span class="sxs-lookup"><span data-stu-id="46319-155">By default, debugging messages aren't displayed because the value of the `$DebugPreference` variable is **SilentlyContinue**.</span></span>

<span data-ttu-id="46319-156">I interaktivt läge åsidosätter **fel söknings** parametern värdet för `$DebugPreference` variabeln för det aktuella kommandot och anger värdet för `$DebugPreference` att **fråga**.</span><span class="sxs-lookup"><span data-stu-id="46319-156">In interactive mode, the **Debug** parameter overrides the value of the `$DebugPreference` variable for the current command, setting the value of `$DebugPreference` to **Inquire**.</span></span>

<span data-ttu-id="46319-157">I icke-interaktivt läge åsidosätter **fel söknings** parametern värdet för `$DebugPreference` variabeln för det aktuella kommandot och anger värdet för `$DebugPreference` att **fortsätta**.</span><span class="sxs-lookup"><span data-stu-id="46319-157">In non-interactive mode, the **Debug** parameter overrides the value of the `$DebugPreference` variable for the current command, setting the value of `$DebugPreference` to **Continue**.</span></span>

<span data-ttu-id="46319-158">`-Debug:$true` har samma resultat som `-Debug` .</span><span class="sxs-lookup"><span data-stu-id="46319-158">`-Debug:$true` has the same effect as `-Debug`.</span></span> <span data-ttu-id="46319-159">Används `-Debug:$false` för att förhindra visning av fel söknings meddelanden när `$DebugPreference` inte är **SilentlyContinue**, vilket är standardvärdet.</span><span class="sxs-lookup"><span data-stu-id="46319-159">Use `-Debug:$false` to suppress the display of debugging messages when `$DebugPreference` isn't **SilentlyContinue**, which is the default.</span></span>

#### <a name="erroraction"></a><span data-ttu-id="46319-160">ErrorAction</span><span class="sxs-lookup"><span data-stu-id="46319-160">ErrorAction</span></span>

<span data-ttu-id="46319-161">Anger hur cmdleten svarar på ett icke-avslutande fel från kommandot.</span><span class="sxs-lookup"><span data-stu-id="46319-161">Determines how the cmdlet responds to a non-terminating error from the command.</span></span>
<span data-ttu-id="46319-162">Den här parametern fungerar bara när kommandot genererar ett icke-avslutande fel, till exempel från `Write-Error` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="46319-162">This parameter works only when the command generates a non-terminating error, such as those from the `Write-Error` cmdlet.</span></span>

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

<span data-ttu-id="46319-163">Parametern **ErrorAction** åsidosätter värdet för `$ErrorActionPreference` variabeln för det aktuella kommandot.</span><span class="sxs-lookup"><span data-stu-id="46319-163">The **ErrorAction** parameter overrides the value of the `$ErrorActionPreference` variable for the current command.</span></span> <span data-ttu-id="46319-164">Eftersom standardvärdet för `$ErrorActionPreference` variabeln **fortsätter** visas fel meddelanden och körningen fortsätter om du inte använder parametern **ErrorAction** .</span><span class="sxs-lookup"><span data-stu-id="46319-164">Because the default value of the `$ErrorActionPreference` variable is **Continue**, error messages are displayed and execution continues unless you use the **ErrorAction** parameter.</span></span>

<span data-ttu-id="46319-165">Parametern **ErrorAction** har ingen påverkan på att avsluta fel (till exempel saknade data, parametrar som inte är giltiga eller otillräckliga behörigheter) som hindrar ett kommando från att slutföras.</span><span class="sxs-lookup"><span data-stu-id="46319-165">The **ErrorAction** parameter has no effect on terminating errors (such as missing data, parameters that aren't valid, or insufficient permissions) that prevent a command from completing successfully.</span></span>

<span data-ttu-id="46319-166">`-ErrorAction:Continue` Visa fel meddelandet och fortsätt att köra kommandot.</span><span class="sxs-lookup"><span data-stu-id="46319-166">`-ErrorAction:Continue` display the error message and continues executing the command.</span></span> <span data-ttu-id="46319-167">`Continue` används som standard.</span><span class="sxs-lookup"><span data-stu-id="46319-167">`Continue` is the default.</span></span>

<span data-ttu-id="46319-168">`-ErrorAction:Ignore` ignorerar fel meddelandet och fortsätter att köra kommandot.</span><span class="sxs-lookup"><span data-stu-id="46319-168">`-ErrorAction:Ignore` suppresses the error message and continues executing the command.</span></span> <span data-ttu-id="46319-169">Till skillnad från **SilentlyContinue** lägger **Ignorera** inte till fel meddelandet i den `$Error` automatiska variabeln.</span><span class="sxs-lookup"><span data-stu-id="46319-169">Unlike **SilentlyContinue**, **Ignore** doesn't add the error message to the `$Error` automatic variable.</span></span> <span data-ttu-id="46319-170">**Ignorera** -värdet introduceras i PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="46319-170">The **Ignore** value is introduced in PowerShell 3.0.</span></span>

<span data-ttu-id="46319-171">`-ErrorAction:Inquire` visar fel meddelandet och du uppmanas att bekräfta innan du fortsätter körningen.</span><span class="sxs-lookup"><span data-stu-id="46319-171">`-ErrorAction:Inquire` displays the error message and prompts you for confirmation before continuing execution.</span></span> <span data-ttu-id="46319-172">Det här värdet används sällan.</span><span class="sxs-lookup"><span data-stu-id="46319-172">This value is rarely used.</span></span>

<span data-ttu-id="46319-173">`-ErrorAction:SilentlyContinue` ignorerar fel meddelandet och fortsätter att köra kommandot.</span><span class="sxs-lookup"><span data-stu-id="46319-173">`-ErrorAction:SilentlyContinue` suppresses the error message and continues executing the command.</span></span>

<span data-ttu-id="46319-174">`-ErrorAction:Stop` visar fel meddelandet och slutar att köra kommandot.</span><span class="sxs-lookup"><span data-stu-id="46319-174">`-ErrorAction:Stop` displays the error message and stops executing the command.</span></span>

<span data-ttu-id="46319-175">`-ErrorAction:Suspend` är bara tillgängligt för arbets flöden som inte stöds i PowerShell 6 och senare.</span><span class="sxs-lookup"><span data-stu-id="46319-175">`-ErrorAction:Suspend` is only available for workflows which aren't supported in PowerShell 6 and beyond.</span></span>

> [!NOTE]
> <span data-ttu-id="46319-176">Parametern **ErrorAction** åsidosätter, men ersätter inte värdet för `$ErrorAction` Preference-variabeln när parametern används i ett kommando för att köra ett skript eller en funktion.</span><span class="sxs-lookup"><span data-stu-id="46319-176">The **ErrorAction** parameter overrides, but does not replace the value of the `$ErrorAction` preference variable when the parameter is used in a command to run a script or function.</span></span>

#### <a name="errorvariable"></a><span data-ttu-id="46319-177">ErrorVariable</span><span class="sxs-lookup"><span data-stu-id="46319-177">ErrorVariable</span></span>

<span data-ttu-id="46319-178">**ErrorVariable** lagrar fel meddelanden om kommandot i den angivna variabeln och i den `$Error` automatiska variabeln.</span><span class="sxs-lookup"><span data-stu-id="46319-178">**ErrorVariable** stores error messages about the command in the specified variable and in the `$Error` automatic variable.</span></span> <span data-ttu-id="46319-179">Mer information finns i [about_Automatic_Variables](about_Automatic_Variables.md)</span><span class="sxs-lookup"><span data-stu-id="46319-179">For more information, see [about_Automatic_Variables](about_Automatic_Variables.md)</span></span>

```yaml
Type: String
Aliases: ev

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

<span data-ttu-id="46319-180">Som standard skriver nya fel meddelanden över fel meddelanden som redan är lagrade i variabeln.</span><span class="sxs-lookup"><span data-stu-id="46319-180">By default, new error messages overwrite error messages that are already stored in the variable.</span></span> <span data-ttu-id="46319-181">Om du vill lägga till fel meddelandet i variabel innehållet skriver du ett plus tecken ( `+` ) före variabel namnet.</span><span class="sxs-lookup"><span data-stu-id="46319-181">To append the error message to the variable content, type a plus sign (`+`) before the variable name.</span></span>

<span data-ttu-id="46319-182">Till exempel skapar följande kommando `$a` variabeln och lagrar sedan eventuella fel i den:</span><span class="sxs-lookup"><span data-stu-id="46319-182">For example, the following command creates the `$a` variable and then stores any errors in it:</span></span>

```powershell
Get-Process -Id 6 -ErrorVariable a
```

<span data-ttu-id="46319-183">Följande kommando lägger till eventuella fel meddelanden i `$a` variabeln:</span><span class="sxs-lookup"><span data-stu-id="46319-183">The following command adds any error messages to the `$a` variable:</span></span>

```powershell
Get-Process -Id 2 -ErrorVariable +a
```

<span data-ttu-id="46319-184">Följande kommando visar innehållet i `$a` :</span><span class="sxs-lookup"><span data-stu-id="46319-184">The following command displays the contents of `$a`:</span></span>

```powershell
$a
```

<span data-ttu-id="46319-185">Du kan använda den här parametern för att skapa en variabel som bara innehåller fel meddelanden från vissa kommandon och som inte påverkar beteendet för den `$Error` automatiska variabeln.</span><span class="sxs-lookup"><span data-stu-id="46319-185">You can use this parameter to create a variable that contains only error messages from specific commands and does not affect the behavior of the `$Error` automatic variable.</span></span> <span data-ttu-id="46319-186">Den `$Error` automatiska variabeln innehåller fel meddelanden från alla kommandon i sessionen.</span><span class="sxs-lookup"><span data-stu-id="46319-186">The `$Error` automatic variable contains error messages from all the commands in the session.</span></span> <span data-ttu-id="46319-187">Du kan använda mat ris notation, till exempel `$a[0]` eller `$error[1,2]` för att referera till vissa fel som lagras i variablerna.</span><span class="sxs-lookup"><span data-stu-id="46319-187">You can use array notation, such as `$a[0]` or `$error[1,2]` to refer to specific errors stored in the variables.</span></span>

> [!NOTE]
> <span data-ttu-id="46319-188">Den anpassade fel variabeln innehåller alla fel som genereras av kommandot, inklusive fel från anrop till kapslade funktioner eller skript.</span><span class="sxs-lookup"><span data-stu-id="46319-188">The custom error variable contains all errors generated by the command, including errors from calls to nested functions or scripts.</span></span>

#### <a name="informationaction"></a><span data-ttu-id="46319-189">InformationAction</span><span class="sxs-lookup"><span data-stu-id="46319-189">InformationAction</span></span>

<span data-ttu-id="46319-190">Introducerades i PowerShell 5,0.</span><span class="sxs-lookup"><span data-stu-id="46319-190">Introduced in PowerShell 5.0.</span></span> <span data-ttu-id="46319-191">I det kommando eller skript där det används åsidosätter den gemensamma parametern **InformationAction** värdet för `$InformationPreference` variabeln Preference, vilket som standard är inställt på **SilentlyContinue**.</span><span class="sxs-lookup"><span data-stu-id="46319-191">Within the command or script in which it's used, the **InformationAction** common parameter overrides the value of the `$InformationPreference` preference variable, which by default is set to **SilentlyContinue**.</span></span> <span data-ttu-id="46319-192">När du använder `Write-Information` i ett skript med **InformationAction**, `Write-Information` visas värdena beroende på värdet för parametern **InformationAction** .</span><span class="sxs-lookup"><span data-stu-id="46319-192">When you use `Write-Information` in a script with **InformationAction**, `Write-Information` values are shown depending on the value of the **InformationAction** parameter.</span></span> <span data-ttu-id="46319-193">Mer information om `$InformationPreference` finns i [about_Preference_Variables](./about_Preference_Variables.md).</span><span class="sxs-lookup"><span data-stu-id="46319-193">For more information about `$InformationPreference`, see [about_Preference_Variables](./about_Preference_Variables.md).</span></span>

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

<span data-ttu-id="46319-194">`-InformationAction:Stop` stoppar ett kommando eller skript vid en förekomst av `Write-Information` kommandot.</span><span class="sxs-lookup"><span data-stu-id="46319-194">`-InformationAction:Stop` stops a command or script at an occurrence of the `Write-Information` command.</span></span>

<span data-ttu-id="46319-195">`-InformationAction:Ignore` undertrycker informations meddelandet och fortsätter att köra kommandot.</span><span class="sxs-lookup"><span data-stu-id="46319-195">`-InformationAction:Ignore` suppresses the informational message and continues running the command.</span></span> <span data-ttu-id="46319-196">Till skillnad från **SilentlyContinue** glömmer ignorera det informations meddelandet att **ignoreras** . informations meddelandet läggs inte till i informations data strömmen.</span><span class="sxs-lookup"><span data-stu-id="46319-196">Unlike **SilentlyContinue**, **Ignore** completely forgets the informational message; it doesn't add the informational message to the information stream.</span></span>

<span data-ttu-id="46319-197">`-InformationAction:Inquire` visar det informations meddelande som du anger i ett `Write-Information` kommando och frågar om du vill fortsätta.</span><span class="sxs-lookup"><span data-stu-id="46319-197">`-InformationAction:Inquire` displays the informational message that you specify in a `Write-Information` command, then asks whether you want to continue.</span></span>

<span data-ttu-id="46319-198">`-InformationAction:Continue` visar informations meddelandet och fortsätter att köra.</span><span class="sxs-lookup"><span data-stu-id="46319-198">`-InformationAction:Continue` displays the informational message, and continues running.</span></span>

<span data-ttu-id="46319-199">`-InformationAction:Suspend` stöds inte i PowerShell Core eftersom det endast är tillgängligt för arbets flöden.</span><span class="sxs-lookup"><span data-stu-id="46319-199">`-InformationAction:Suspend` isn't supported on PowerShell Core as it is only available for workflows.</span></span>

<span data-ttu-id="46319-200">`-InformationAction:SilentlyContinue` ingen påverkan eftersom informations meddelandet inte är (standard) visas och skriptet fortsätter utan avbrott.</span><span class="sxs-lookup"><span data-stu-id="46319-200">`-InformationAction:SilentlyContinue` no effect as the informational message aren't (Default) displayed, and the script continues without interruption.</span></span>

> [!NOTE]
> <span data-ttu-id="46319-201">Parametern **InformationAction** åsidosätter, men ersätter inte värdet för `$InformationAction` Preference-variabeln när parametern används i ett kommando för att köra ett skript eller en funktion.</span><span class="sxs-lookup"><span data-stu-id="46319-201">The **InformationAction** parameter overrides, but does not replace the value of the `$InformationAction` preference variable when the parameter is used in a command to run a script or function.</span></span>

#### <a name="informationvariable"></a><span data-ttu-id="46319-202">InformationVariable</span><span class="sxs-lookup"><span data-stu-id="46319-202">InformationVariable</span></span>

<span data-ttu-id="46319-203">Introducerades i PowerShell 5,0.</span><span class="sxs-lookup"><span data-stu-id="46319-203">Introduced in PowerShell 5.0.</span></span> <span data-ttu-id="46319-204">I det kommando eller skript där det används lagras den gemensamma **InformationVariable** -parametern i en variabel en sträng som du anger genom att lägga till `Write-Information` kommandot.</span><span class="sxs-lookup"><span data-stu-id="46319-204">Within the command or script in which it's used, the **InformationVariable** common parameter stores in a variable a string that you specify by adding the `Write-Information` command.</span></span> <span data-ttu-id="46319-205">`Write-Information`värdena visas beroende på värdet för den gemensamma parametern **InformationAction** . Om du inte lägger till  den gemensamma parametern InformationAction `Write-Information` visas strängarna beroende på värdet för `$InformationPreference` variabeln Preference.</span><span class="sxs-lookup"><span data-stu-id="46319-205">`Write-Information` values are shown depending on the value of the **InformationAction** common parameter; if you don't add the **InformationAction** common parameter, `Write-Information` strings are shown depending on the value of the `$InformationPreference` preference variable.</span></span> <span data-ttu-id="46319-206">Mer information om `$InformationPreference` finns i [about_Preference_Variables](./about_Preference_Variables.md).</span><span class="sxs-lookup"><span data-stu-id="46319-206">For more information about `$InformationPreference`, see [about_Preference_Variables](./about_Preference_Variables.md).</span></span>

> [!NOTE]
> <span data-ttu-id="46319-207">Variabeln information innehåller alla informations meddelanden som genereras av kommandot, inklusive informations meddelanden från anrop till kapslade funktioner eller skript.</span><span class="sxs-lookup"><span data-stu-id="46319-207">The information variable contains all information messages generated by the command, including information messages from calls to nested functions or scripts.</span></span>

```yaml
Type: String
Aliases: iv

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

#### <a name="outbuffer"></a><span data-ttu-id="46319-208">OutBuffer</span><span class="sxs-lookup"><span data-stu-id="46319-208">OutBuffer</span></span>

<span data-ttu-id="46319-209">Fastställer antalet objekt som ska samlas i en buffert innan objekt skickas via pipelinen.</span><span class="sxs-lookup"><span data-stu-id="46319-209">Determines the number of objects to accumulate in a buffer before any objects are sent through the pipeline.</span></span> <span data-ttu-id="46319-210">Om du utelämnar den här parametern skickas objekten när de genereras.</span><span class="sxs-lookup"><span data-stu-id="46319-210">If you omit this parameter, objects are sent as they're generated.</span></span>

```yaml
Type: Int32
Aliases: ob

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

<span data-ttu-id="46319-211">Den här resurs hanterings parametern är avsedd för avancerade användare.</span><span class="sxs-lookup"><span data-stu-id="46319-211">This resource management parameter is designed for advanced users.</span></span> <span data-ttu-id="46319-212">När du använder den här parametern skickar PowerShell data till nästa cmdlet i batchar för `OutBuffer + 1` .</span><span class="sxs-lookup"><span data-stu-id="46319-212">When you use this parameter, PowerShell sends data to the next cmdlet in batches of `OutBuffer + 1`.</span></span>

<span data-ttu-id="46319-213">I följande exempel visas mellan för att `ForEach-Object` bearbeta block som använder `Write-Host` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="46319-213">The following example alternates displays between to `ForEach-Object` process blocks that use the `Write-Host` cmdlet.</span></span> <span data-ttu-id="46319-214">Alternativen visas i batchar med 2 eller `OutBuffer + 1` .</span><span class="sxs-lookup"><span data-stu-id="46319-214">The display alternates in batches of 2 or `OutBuffer + 1`.</span></span>

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

#### <a name="outvariable"></a><span data-ttu-id="46319-215">OutVariable</span><span class="sxs-lookup"><span data-stu-id="46319-215">OutVariable</span></span>

<span data-ttu-id="46319-216">Lagrar utdata-objekt från kommandot i den angivna variabeln, förutom att skicka utdata längs pipelinen.</span><span class="sxs-lookup"><span data-stu-id="46319-216">Stores output objects from the command in the specified variable in addition to sending the output along the pipeline.</span></span>

```yaml
Type: String
Aliases: ov

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

<span data-ttu-id="46319-217">Om du vill lägga till utdata i variabeln, i stället för att ersätta eventuella utdata som redan är lagrade där, skriver du ett plus tecken ( `+` ) före variabel namnet.</span><span class="sxs-lookup"><span data-stu-id="46319-217">To add the output to the variable, instead of replacing any output that might already be stored there, type a plus sign (`+`) before the variable name.</span></span>

<span data-ttu-id="46319-218">Följande kommando skapar till exempel `$out` variabeln och lagrar processobjektet i den:</span><span class="sxs-lookup"><span data-stu-id="46319-218">For example, the following command creates the `$out` variable and stores the process object in it:</span></span>

```powershell
Get-Process PowerShell -OutVariable out
```

<span data-ttu-id="46319-219">Följande kommando lägger till objektet bearbeta i `$out` variabeln:</span><span class="sxs-lookup"><span data-stu-id="46319-219">The following command adds the process object to the `$out` variable:</span></span>

```powershell
Get-Process iexplore -OutVariable +out
```

<span data-ttu-id="46319-220">Följande kommando visar innehållet i `$out` variabeln:</span><span class="sxs-lookup"><span data-stu-id="46319-220">The following command displays the contents of the `$out` variable:</span></span>

```powershell
$out
```

> [!NOTE]
> <span data-ttu-id="46319-221">Variabeln som skapas av parametern **devariable** är en `[System.Collections.ArrayList]` .</span><span class="sxs-lookup"><span data-stu-id="46319-221">The variable created by the **OutVariable** parameter is a `[System.Collections.ArrayList]`.</span></span>

#### <a name="pipelinevariable"></a><span data-ttu-id="46319-222">PipelineVariable</span><span class="sxs-lookup"><span data-stu-id="46319-222">PipelineVariable</span></span>

<span data-ttu-id="46319-223">**PipelineVariable** lagrar värdet för det aktuella pipeline-elementet som en variabel, för alla namngivna kommandon som det flödar genom pipelinen.</span><span class="sxs-lookup"><span data-stu-id="46319-223">**PipelineVariable** stores the value of the current pipeline element as a variable, for any named command as it flows through the pipeline.</span></span>

```yaml
Type: String
Aliases: pv

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

<span data-ttu-id="46319-224">Giltiga värden är strängar, samma som för alla variabel namn.</span><span class="sxs-lookup"><span data-stu-id="46319-224">Valid values are strings, the same as for any variable names.</span></span>

<span data-ttu-id="46319-225">Följande är ett exempel på hur **PipelineVariable** fungerar.</span><span class="sxs-lookup"><span data-stu-id="46319-225">The following is an example of how **PipelineVariable** works.</span></span> <span data-ttu-id="46319-226">I det här exemplet läggs parametern **PipelineVariable** till i ett `Foreach-Object` kommando för att lagra resultatet av kommandot i variabler.</span><span class="sxs-lookup"><span data-stu-id="46319-226">In this example, the **PipelineVariable** parameter is added to a `Foreach-Object` command to store the results of the command in variables.</span></span> <span data-ttu-id="46319-227">Ett intervall med tal, 1 till 10, är skickas i det första `Foreach-Object` kommandot, vars resultat lagras i en variabel med namnet **Left**.</span><span class="sxs-lookup"><span data-stu-id="46319-227">A range of numbers, 1 to 10, are piped into the first `Foreach-Object` command, the results of which are stored in a variable named **Left**.</span></span>

<span data-ttu-id="46319-228">Resultatet från det första `Foreach-Object` kommandot är skickas i ett andra `Foreach-Object` kommando, som filtrerar objekten som returneras av det första `Foreach-Object` kommandot.</span><span class="sxs-lookup"><span data-stu-id="46319-228">The results of the first `Foreach-Object` command are piped into a second `Foreach-Object` command, which filters the objects returned by the first `Foreach-Object` command.</span></span> <span data-ttu-id="46319-229">Resultatet av det andra kommandot lagras i en variabel med namnet **Right**.</span><span class="sxs-lookup"><span data-stu-id="46319-229">The results of the second command are stored in a variable named **Right**.</span></span>

<span data-ttu-id="46319-230">I det tredje `Foreach-Object` kommandot bearbetas resultaten av de första två `Foreach-Object` skickas-kommandona som representeras av variablerna **Left** och **Right**, med hjälp av en multiplikation-operator.</span><span class="sxs-lookup"><span data-stu-id="46319-230">In the third `Foreach-Object` command, the results of the first two `Foreach-Object` piped commands, represented by the variables **Left** and **Right**, are processed by using a multiplication operator.</span></span> <span data-ttu-id="46319-231">Kommandot instruerar objekt som lagras i de **vänstra** och **högra** variablerna att multipliceras och anger att resultaten ska visas som "medlemmar i vänster intervall \* höger intervall medlem = produkt".</span><span class="sxs-lookup"><span data-stu-id="46319-231">The command instructs objects stored in the **Left** and **Right** variables to be multiplied, and specifies that the results should be displayed as "Left range member \* Right range member = product".</span></span>

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

#### <a name="verbose"></a><span data-ttu-id="46319-232">Verbose</span><span class="sxs-lookup"><span data-stu-id="46319-232">Verbose</span></span>

<span data-ttu-id="46319-233">Visar detaljerad information om den åtgärd som utförs av kommandot.</span><span class="sxs-lookup"><span data-stu-id="46319-233">Displays detailed information about the operation done by the command.</span></span> <span data-ttu-id="46319-234">Den här informationen liknar informationen i en spårning eller i en transaktions logg.</span><span class="sxs-lookup"><span data-stu-id="46319-234">This information resembles the information in a trace or in a transaction log.</span></span> <span data-ttu-id="46319-235">Den här parametern fungerar bara när kommandot genererar ett utförligt meddelande.</span><span class="sxs-lookup"><span data-stu-id="46319-235">This parameter works only when the command generates a verbose message.</span></span> <span data-ttu-id="46319-236">Den här parametern fungerar till exempel när ett kommando innehåller `Write-Verbose` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="46319-236">For example, this parameter works when a command contains the `Write-Verbose` cmdlet.</span></span>

```yaml
Type: SwitchParameter
Aliases: vb

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

<span data-ttu-id="46319-237">Den **utförliga** parametern åsidosätter värdet för `$VerbosePreference` variabeln för det aktuella kommandot.</span><span class="sxs-lookup"><span data-stu-id="46319-237">The **Verbose** parameter overrides the value of the `$VerbosePreference` variable for the current command.</span></span> <span data-ttu-id="46319-238">Eftersom standardvärdet för `$VerbosePreference` variabeln är **SilentlyContinue** visas inte utförliga meddelanden som standard.</span><span class="sxs-lookup"><span data-stu-id="46319-238">Because the default value of the `$VerbosePreference` variable is **SilentlyContinue**, verbose messages aren't displayed by default.</span></span>

<span data-ttu-id="46319-239">`-Verbose:$true` har samma resultat som `-Verbose`</span><span class="sxs-lookup"><span data-stu-id="46319-239">`-Verbose:$true` has the same effect as `-Verbose`</span></span>

<span data-ttu-id="46319-240">`-Verbose:$false` förhindrar visning av utförliga meddelanden.</span><span class="sxs-lookup"><span data-stu-id="46319-240">`-Verbose:$false` suppresses the display of verbose messages.</span></span> <span data-ttu-id="46319-241">Använd den här parametern när värdet för `$VerbosePreference` inte är **SilentlyContinue** (standard).</span><span class="sxs-lookup"><span data-stu-id="46319-241">Use this parameter when the value of `$VerbosePreference` isn't **SilentlyContinue** (the default).</span></span>

#### <a name="warningaction"></a><span data-ttu-id="46319-242">WarningAction</span><span class="sxs-lookup"><span data-stu-id="46319-242">WarningAction</span></span>

<span data-ttu-id="46319-243">Anger hur cmdleten svarar på en varning från kommandot.</span><span class="sxs-lookup"><span data-stu-id="46319-243">Determines how the cmdlet responds to a warning from the command.</span></span> <span data-ttu-id="46319-244">**Fortsätt** är standardvärdet.</span><span class="sxs-lookup"><span data-stu-id="46319-244">**Continue** is the default value.</span></span> <span data-ttu-id="46319-245">Den här parametern fungerar bara när kommandot genererar ett varnings meddelande.</span><span class="sxs-lookup"><span data-stu-id="46319-245">This parameter works only when the command generates a warning message.</span></span> <span data-ttu-id="46319-246">Den här parametern fungerar till exempel när ett kommando innehåller `Write-Warning` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="46319-246">For example, this parameter works when a command contains the `Write-Warning` cmdlet.</span></span>

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

<span data-ttu-id="46319-247">Parametern **WarningAction** åsidosätter värdet för `$WarningPreference` variabeln för det aktuella kommandot.</span><span class="sxs-lookup"><span data-stu-id="46319-247">The **WarningAction** parameter overrides the value of the `$WarningPreference` variable for the current command.</span></span> <span data-ttu-id="46319-248">Eftersom standardvärdet för `$WarningPreference` variabeln **fortsätter** visas varningar och körningen fortsätter om du inte använder parametern **WarningAction** .</span><span class="sxs-lookup"><span data-stu-id="46319-248">Because the default value of the `$WarningPreference` variable is **Continue**, warnings are displayed and execution continues unless you use the **WarningAction** parameter.</span></span>

<span data-ttu-id="46319-249">`-WarningAction:Continue` visar varnings meddelandena och fortsätter att köra kommandot.</span><span class="sxs-lookup"><span data-stu-id="46319-249">`-WarningAction:Continue` displays the warning messages and continues executing the command.</span></span> <span data-ttu-id="46319-250">`Continue` används som standard.</span><span class="sxs-lookup"><span data-stu-id="46319-250">`Continue` is the default.</span></span>

<span data-ttu-id="46319-251">`-WarningAction:Inquire` visar varnings meddelandet och du uppmanas att bekräfta innan du fortsätter körningen.</span><span class="sxs-lookup"><span data-stu-id="46319-251">`-WarningAction:Inquire` displays the warning message and prompts you for confirmation before continuing execution.</span></span> <span data-ttu-id="46319-252">Det här värdet används sällan.</span><span class="sxs-lookup"><span data-stu-id="46319-252">This value is rarely used.</span></span>

<span data-ttu-id="46319-253">`-WarningAction:SilentlyContinue` undertrycker varnings meddelandet och fortsätter att köra kommandot.</span><span class="sxs-lookup"><span data-stu-id="46319-253">`-WarningAction:SilentlyContinue` suppresses the warning message and continues executing the command.</span></span>

<span data-ttu-id="46319-254">`-WarningAction:Stop` visar varnings meddelandet och stoppar körningen av kommandot.</span><span class="sxs-lookup"><span data-stu-id="46319-254">`-WarningAction:Stop` displays the warning message and stops executing the command.</span></span>

> [!NOTE]
> <span data-ttu-id="46319-255">Parametern **WarningAction** åsidosätter, men ersätter inte värdet för `$WarningAction` Preference-variabeln när parametern används i ett kommando för att köra ett skript eller en funktion.</span><span class="sxs-lookup"><span data-stu-id="46319-255">The **WarningAction** parameter overrides, but does not replace the value of the `$WarningAction` preference variable when the parameter is used in a command to run a script or function.</span></span>

#### <a name="warningvariable"></a><span data-ttu-id="46319-256">WarningVariable</span><span class="sxs-lookup"><span data-stu-id="46319-256">WarningVariable</span></span>

<span data-ttu-id="46319-257">Lagrar varningar om kommandot i den angivna variabeln.</span><span class="sxs-lookup"><span data-stu-id="46319-257">Stores warnings about the command in the specified variable.</span></span>

```yaml
Type: String
Aliases: wv

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

<span data-ttu-id="46319-258">Alla genererade varningar sparas i variabeln även om varningarna inte visas för användaren.</span><span class="sxs-lookup"><span data-stu-id="46319-258">All generated warnings are saved in the variable even if the warnings aren't displayed to the user.</span></span>

<span data-ttu-id="46319-259">Om du vill lägga till varningar i variabel innehållet, i stället för att ersätta eventuella varningar som redan är lagrade där, skriver du ett plus tecken ( `+` ) före variabel namnet.</span><span class="sxs-lookup"><span data-stu-id="46319-259">To append the warnings to the variable content, instead of replacing any warnings that might already be stored there, type a plus sign (`+`) before the variable name.</span></span>

<span data-ttu-id="46319-260">Till exempel skapar följande kommando `$a` variabeln och lagrar sedan alla varningar:</span><span class="sxs-lookup"><span data-stu-id="46319-260">For example, the following command creates the `$a` variable and then stores any warnings in it:</span></span>

```powershell
Get-Process -Id 6 -WarningVariable a
```

<span data-ttu-id="46319-261">Följande kommando lägger till eventuella varningar till `$a` variabeln:</span><span class="sxs-lookup"><span data-stu-id="46319-261">The following command adds any warnings to the `$a` variable:</span></span>

```powershell
Get-Process -Id 2 -WarningVariable +a
```

<span data-ttu-id="46319-262">Följande kommando visar innehållet i `$a` :</span><span class="sxs-lookup"><span data-stu-id="46319-262">The following command displays the contents of `$a`:</span></span>

```powershell
$a
```

<span data-ttu-id="46319-263">Du kan använda den här parametern för att skapa en variabel som bara innehåller varningar från vissa kommandon.</span><span class="sxs-lookup"><span data-stu-id="46319-263">You can use this parameter to create a variable that contains only warnings from specific commands.</span></span> <span data-ttu-id="46319-264">Du kan använda mat ris notation, till exempel `$a[0]` eller `$warning[1,2]` för att referera till vissa varningar som lagras i variabeln.</span><span class="sxs-lookup"><span data-stu-id="46319-264">You can use array notation, such as `$a[0]` or `$warning[1,2]` to refer to specific warnings stored in the variable.</span></span>

> [!NOTE]
> <span data-ttu-id="46319-265">Varnings variabeln innehåller alla varningar som genererats av kommandot, inklusive varningar från anrop till kapslade funktioner eller skript.</span><span class="sxs-lookup"><span data-stu-id="46319-265">The warning variable contains all warnings generated by the command, including warnings from calls to nested functions or scripts.</span></span>

### <a name="risk-management-parameter-descriptions"></a><span data-ttu-id="46319-266">Parameter beskrivningar för risk hantering</span><span class="sxs-lookup"><span data-stu-id="46319-266">Risk Management Parameter Descriptions</span></span>

#### <a name="whatif"></a><span data-ttu-id="46319-267">WhatIf</span><span class="sxs-lookup"><span data-stu-id="46319-267">WhatIf</span></span>

<span data-ttu-id="46319-268">Visar ett meddelande som beskriver kommandots effekter i stället för att köra kommandot.</span><span class="sxs-lookup"><span data-stu-id="46319-268">Displays a message that describes the effect of the command, instead of executing the command.</span></span>

```yaml
Type: SwitchParameter
Aliases: wi

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

<span data-ttu-id="46319-269">Parametern **whatIf** åsidosätter värdet för `$WhatIfPreference` variabeln för det aktuella kommandot.</span><span class="sxs-lookup"><span data-stu-id="46319-269">The **WhatIf** parameter overrides the value of the `$WhatIfPreference` variable for the current command.</span></span> <span data-ttu-id="46319-270">Eftersom standardvärdet för `$WhatIfPreference` variabeln är 0 (inaktiverat), utförs inte **whatIf** -beteendet utan parametern **whatIf** .</span><span class="sxs-lookup"><span data-stu-id="46319-270">Because the default value of the `$WhatIfPreference` variable is 0 (disabled), **WhatIf** behavior isn't done without the **WhatIf** parameter.</span></span> <span data-ttu-id="46319-271">Mer information finns i [about_Preference_Variables](about_Preference_Variables.md)</span><span class="sxs-lookup"><span data-stu-id="46319-271">For more information, see [about_Preference_Variables](about_Preference_Variables.md)</span></span>

<span data-ttu-id="46319-272">`-WhatIf:$true` har samma resultat som `-WhatIf` .</span><span class="sxs-lookup"><span data-stu-id="46319-272">`-WhatIf:$true` has the same effect as `-WhatIf`.</span></span>

<span data-ttu-id="46319-273">`-WhatIf:$false` ignorerar det automatiska beteendet i WhatIf som resulterar i när värdet för `$WhatIfPreference` variabeln är 1.</span><span class="sxs-lookup"><span data-stu-id="46319-273">`-WhatIf:$false` suppresses the automatic WhatIf behavior that results when the value of the `$WhatIfPreference` variable is 1.</span></span>

<span data-ttu-id="46319-274">Följande kommando använder till exempel `-WhatIf` parametern i ett `Remove-Item` kommando:</span><span class="sxs-lookup"><span data-stu-id="46319-274">For example, the following command uses the `-WhatIf` parameter in a `Remove-Item` command:</span></span>

```powershell
Remove-Item Date.csv -WhatIf
```

<span data-ttu-id="46319-275">I stället för att ta bort objektet, visar PowerShell de åtgärder som ska utföras och de objekt som skulle påverkas.</span><span class="sxs-lookup"><span data-stu-id="46319-275">Instead of removing the item, PowerShell lists the operations it would do and the items that would be affected.</span></span> <span data-ttu-id="46319-276">Det här kommandot ger följande utdata:</span><span class="sxs-lookup"><span data-stu-id="46319-276">This command produces the following output:</span></span>

```output
What if: Performing operation "Remove File" on
Target "C:\ps-test\date.csv".
```

#### <a name="confirm"></a><span data-ttu-id="46319-277">Bekräfta</span><span class="sxs-lookup"><span data-stu-id="46319-277">Confirm</span></span>

<span data-ttu-id="46319-278">Du uppmanas att bekräfta innan du kör kommandot.</span><span class="sxs-lookup"><span data-stu-id="46319-278">Prompts you for confirmation before executing the command.</span></span>

```yaml
Type: SwitchParameter
Aliases: cf

Required: False
Position: Named
Default value: Depends on preference variable
Accept pipeline input: False
Accept wildcard characters: False
```

<span data-ttu-id="46319-279">Parametern **Confirm** åsidosätter värdet för `$ConfirmPreference` variabeln för det aktuella kommandot.</span><span class="sxs-lookup"><span data-stu-id="46319-279">The **Confirm** parameter overrides the value of the `$ConfirmPreference` variable for the current command.</span></span> <span data-ttu-id="46319-280">Standardvärdet är True.</span><span class="sxs-lookup"><span data-stu-id="46319-280">The default value is true.</span></span> <span data-ttu-id="46319-281">Mer information finns i [about_Preference_Variables](about_Preference_Variables.md)</span><span class="sxs-lookup"><span data-stu-id="46319-281">For more information, see [about_Preference_Variables](about_Preference_Variables.md)</span></span>

<span data-ttu-id="46319-282">`-Confirm:$true` har samma resultat som `-Confirm` .</span><span class="sxs-lookup"><span data-stu-id="46319-282">`-Confirm:$true` has the same effect as `-Confirm`.</span></span>

<span data-ttu-id="46319-283">`-Confirm:$false` förhindrar automatisk bekräftelse, som inträffar när värdet för `$ConfirmPreference` är mindre än eller lika med den beräknade risken för cmdleten.</span><span class="sxs-lookup"><span data-stu-id="46319-283">`-Confirm:$false` suppresses automatic confirmation, which occurs when the value of `$ConfirmPreference` is less than or equal to the estimated risk of the cmdlet.</span></span>

<span data-ttu-id="46319-284">Följande kommando använder till exempel parametern **Confirm** med ett `Remove-Item` kommando.</span><span class="sxs-lookup"><span data-stu-id="46319-284">For example, the following command uses the **Confirm** parameter with a `Remove-Item` command.</span></span> <span data-ttu-id="46319-285">Innan objektet tas bort, visar PowerShell de åtgärder som skulle utföras och de objekt som skulle påverkas, och ber om godkännande.</span><span class="sxs-lookup"><span data-stu-id="46319-285">Before removing the item, PowerShell lists the operations it would do and the items that would be affected, and asks for approval.</span></span>

```
PS C:\ps-test> Remove-Item tmp*.txt -Confirm

Confirm
Are you sure you want to perform this action?
Performing operation "Remove File" on Target " C:\ps-test\tmp1.txt
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend
[?] Help (default is "Y"):
```

<span data-ttu-id="46319-286">Alternativen för att bekräfta svar är följande:</span><span class="sxs-lookup"><span data-stu-id="46319-286">The Confirm response options are as follows:</span></span>

|<span data-ttu-id="46319-287">Svarsåtgärder</span><span class="sxs-lookup"><span data-stu-id="46319-287">Response</span></span>       |<span data-ttu-id="46319-288">Resultat</span><span class="sxs-lookup"><span data-stu-id="46319-288">Result</span></span>                                                     |
|---------------|-----------------------------------------------------------|
|<span data-ttu-id="46319-289">Ja (Y)</span><span class="sxs-lookup"><span data-stu-id="46319-289">Yes (Y)</span></span>        |<span data-ttu-id="46319-290">Utför åtgärden.</span><span class="sxs-lookup"><span data-stu-id="46319-290">Perform the action.</span></span>                                        |
|<span data-ttu-id="46319-291">Ja till alla (A)</span><span class="sxs-lookup"><span data-stu-id="46319-291">Yes to All (A)</span></span> |<span data-ttu-id="46319-292">Utföra alla åtgärder och utelämna efterföljande bekräfta-frågor</span><span class="sxs-lookup"><span data-stu-id="46319-292">Perform all actions and suppress subsequent Confirm queries</span></span>|
|               |<span data-ttu-id="46319-293">för det här kommandot.</span><span class="sxs-lookup"><span data-stu-id="46319-293">for this command.</span></span>                                          |
|<span data-ttu-id="46319-294">Nej (N):</span><span class="sxs-lookup"><span data-stu-id="46319-294">No (N):</span></span>        |<span data-ttu-id="46319-295">Utför inte åtgärden.</span><span class="sxs-lookup"><span data-stu-id="46319-295">Do not perform the action.</span></span>                                 |
|<span data-ttu-id="46319-296">Nej till alla (L):</span><span class="sxs-lookup"><span data-stu-id="46319-296">No to All (L):</span></span> |<span data-ttu-id="46319-297">Utför inga åtgärder och ignorera sedan efterföljande bekräftelse</span><span class="sxs-lookup"><span data-stu-id="46319-297">Do not perform any actions and suppress subsequent Confirm</span></span> |
|               |<span data-ttu-id="46319-298">frågor för det här kommandot.</span><span class="sxs-lookup"><span data-stu-id="46319-298">queries for this command.</span></span>                                  |
|<span data-ttu-id="46319-299">Pausa (S):</span><span class="sxs-lookup"><span data-stu-id="46319-299">Suspend (S):</span></span>   |<span data-ttu-id="46319-300">Pausa kommandot och skapa en tillfällig session.</span><span class="sxs-lookup"><span data-stu-id="46319-300">Pause the command and create a temporary session.</span></span>          |
|<span data-ttu-id="46319-301">Hjälp (?)</span><span class="sxs-lookup"><span data-stu-id="46319-301">Help (?)</span></span>       |<span data-ttu-id="46319-302">Visa hjälp för de här alternativen.</span><span class="sxs-lookup"><span data-stu-id="46319-302">Display help for these options.</span></span>                            |

<span data-ttu-id="46319-303">Alternativet **PAUSE** placerar kommandot stoppad och skapar en tillfällig kapslad session där du kan arbeta tills du är redo att välja ett **Bekräfta** -alternativ.</span><span class="sxs-lookup"><span data-stu-id="46319-303">The **Suspend** option places the command on hold and creates a temporary nested session in which you can work until you're ready to choose a **Confirm** option.</span></span> <span data-ttu-id="46319-304">Kommando tolken för den kapslade sessionen har två extra försiktighets åtgärder (>>) för att indikera att det är en underordnad åtgärd för det ursprungliga överordnade kommandot.</span><span class="sxs-lookup"><span data-stu-id="46319-304">The command prompt for the nested session has two extra carets (>>) to indicate that it's a child operation of the original parent command.</span></span> <span data-ttu-id="46319-305">Du kan köra kommandon och skript i den kapslade sessionen.</span><span class="sxs-lookup"><span data-stu-id="46319-305">You can run commands and scripts in the nested session.</span></span> <span data-ttu-id="46319-306">Om du vill avsluta den kapslade sessionen och återgå till bekräfta-alternativen för det ursprungliga kommandot skriver du "Exit".</span><span class="sxs-lookup"><span data-stu-id="46319-306">To end the nested session and return to the Confirm options for the original command, type "exit".</span></span>

<span data-ttu-id="46319-307">I följande exempel används **paus** alternativen för att stoppa ett kommando tillfälligt medan användaren kontrollerar hjälpen för en kommando parameter.</span><span class="sxs-lookup"><span data-stu-id="46319-307">In the following example, the **Suspend** option (S) is used to halt a command temporarily while the user checks the help for a command parameter.</span></span> <span data-ttu-id="46319-308">När du har hämtat den information som behövs avslutar du den kapslade prompten och väljer Ja (y) som svar på bekräfta fråga.</span><span class="sxs-lookup"><span data-stu-id="46319-308">After obtaining the needed information, the user types "exit" to end the nested prompt and then selects the Yes (y) response to the Confirm query.</span></span>

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

## <a name="keywords"></a><span data-ttu-id="46319-309">RESERVERADE</span><span class="sxs-lookup"><span data-stu-id="46319-309">KEYWORDS</span></span>

<span data-ttu-id="46319-310">about_Common_Parameters</span><span class="sxs-lookup"><span data-stu-id="46319-310">about_Common_Parameters</span></span>

## <a name="see-also"></a><span data-ttu-id="46319-311">SE ÄVEN</span><span class="sxs-lookup"><span data-stu-id="46319-311">SEE ALSO</span></span>

[<span data-ttu-id="46319-312">about_Preference_Variables</span><span class="sxs-lookup"><span data-stu-id="46319-312">about_Preference_Variables</span></span>](about_Preference_Variables.md)

[<span data-ttu-id="46319-313">Skriv-debug</span><span class="sxs-lookup"><span data-stu-id="46319-313">Write-Debug</span></span>](xref:Microsoft.PowerShell.Utility.Write-Debug)

[<span data-ttu-id="46319-314">Skriv varning</span><span class="sxs-lookup"><span data-stu-id="46319-314">Write-Warning</span></span>](xref:Microsoft.PowerShell.Utility.Write-Warning)

[<span data-ttu-id="46319-315">Skriv-fel</span><span class="sxs-lookup"><span data-stu-id="46319-315">Write-Error</span></span>](xref:Microsoft.PowerShell.Utility.Write-Error)

[<span data-ttu-id="46319-316">Skriv-verbose</span><span class="sxs-lookup"><span data-stu-id="46319-316">Write-Verbose</span></span>](xref:Microsoft.PowerShell.Utility.Write-Verbose)

