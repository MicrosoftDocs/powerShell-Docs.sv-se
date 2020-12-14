---
description: Beskriver hur du ställer in anpassade standardvärden för cmdlet-parametrar och avancerade funktioner.
Locale: en-US
ms.date: 05/31/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_parameters_default_values?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Parameters_Default_Values
ms.openlocfilehash: 102f163287717f7c9cd4f430704cc27ddea7ff4c
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94710993"
---
# <a name="about-parameters-default-values"></a><span data-ttu-id="c45ff-103">Om standardvärden för parametrar</span><span class="sxs-lookup"><span data-stu-id="c45ff-103">About Parameters Default Values</span></span>

## <a name="short-description"></a><span data-ttu-id="c45ff-104">Kort beskrivning</span><span class="sxs-lookup"><span data-stu-id="c45ff-104">Short description</span></span>

<span data-ttu-id="c45ff-105">Beskriver hur du ställer in anpassade standardvärden för cmdlet-parametrar och avancerade funktioner.</span><span class="sxs-lookup"><span data-stu-id="c45ff-105">Describes how to set custom default values for cmdlet parameters and advanced functions.</span></span>

## <a name="long-description"></a><span data-ttu-id="c45ff-106">Lång beskrivning</span><span class="sxs-lookup"><span data-stu-id="c45ff-106">Long description</span></span>

<span data-ttu-id="c45ff-107">Med `$PSDefaultParameterValues` variabeln Preference kan du ange anpassade standardvärden för valfri cmdlet eller avancerad funktion.</span><span class="sxs-lookup"><span data-stu-id="c45ff-107">The `$PSDefaultParameterValues` preference variable lets you specify custom default values for any cmdlet or advanced function.</span></span> <span data-ttu-id="c45ff-108">Cmdletar och avancerade funktioner använder det anpassade standardvärdet om du inte anger något annat värde i kommandot.</span><span class="sxs-lookup"><span data-stu-id="c45ff-108">Cmdlets and advanced functions use the custom default value unless you specify another value in the command.</span></span>

<span data-ttu-id="c45ff-109">Författare av cmdletar och avancerade funktioner ställer in standardvärden för sina parametrar.</span><span class="sxs-lookup"><span data-stu-id="c45ff-109">The authors of cmdlets and advanced functions set standard default values for their parameters.</span></span> <span data-ttu-id="c45ff-110">Vanliga standardvärden är vanligt vis användbara, men de är kanske inte lämpliga för alla miljöer.</span><span class="sxs-lookup"><span data-stu-id="c45ff-110">Typically, the standard default values are useful, but they might not be appropriate for all environments.</span></span>

<span data-ttu-id="c45ff-111">Den här funktionen är särskilt användbar när du måste ange samma alternativa parameter värde nästan varje gång du använder kommandot eller när ett visst parameter värde är svårt att komma ihåg, till exempel ett e-postservernamn eller projekt-GUID.</span><span class="sxs-lookup"><span data-stu-id="c45ff-111">This feature is especially useful when you must specify the same alternate parameter value nearly every time you use the command or when a particular parameter value is difficult to remember, such as an email server name or project GUID.</span></span>

<span data-ttu-id="c45ff-112">Om det önskade standardvärdet varierar förutsägbart kan du ange ett skript block som innehåller olika standardvärden för en parameter under olika förhållanden.</span><span class="sxs-lookup"><span data-stu-id="c45ff-112">If the desired default value varies predictably, you can specify a script block that provides different default values for a parameter under different conditions.</span></span>

<span data-ttu-id="c45ff-113">`$PSDefaultParameterValues` introducerades i PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="c45ff-113">`$PSDefaultParameterValues` was introduced in PowerShell 3.0.</span></span>

## <a name="syntax"></a><span data-ttu-id="c45ff-114">Syntax</span><span class="sxs-lookup"><span data-stu-id="c45ff-114">Syntax</span></span>

<span data-ttu-id="c45ff-115">`$PSDefaultParameterValues`Variabeln är en hash-tabell som verifierar formatet för nycklar som objekt typ av **system. Management. Automation. DefaultParameterDictionary**.</span><span class="sxs-lookup"><span data-stu-id="c45ff-115">The `$PSDefaultParameterValues` variable is a hash table that validates the format of keys as an object type of **System.Management.Automation.DefaultParameterDictionary**.</span></span> <span data-ttu-id="c45ff-116">Hash-tabellen innehåller **nyckel/värde-** par.</span><span class="sxs-lookup"><span data-stu-id="c45ff-116">The hash table contains **Key/Value** pairs.</span></span> <span data-ttu-id="c45ff-117">En **nyckel** har formatet `CmdletName:ParameterName` .</span><span class="sxs-lookup"><span data-stu-id="c45ff-117">A **Key** is in the format `CmdletName:ParameterName`.</span></span> <span data-ttu-id="c45ff-118">Ett **värde** är **DefaultValue** eller **script block** som tilldelats nyckeln.</span><span class="sxs-lookup"><span data-stu-id="c45ff-118">A **Value** is the **DefaultValue** or **ScriptBlock** assigned to the key.</span></span>

<span data-ttu-id="c45ff-119">Syntaxen för `$PSDefaultParameterValues` Preference-variabeln är följande:</span><span class="sxs-lookup"><span data-stu-id="c45ff-119">The syntax of the `$PSDefaultParameterValues` preference variable is as follows:</span></span>

```
$PSDefaultParameterValues=@{"CmdletName:ParameterName"="DefaultValue"}

$PSDefaultParameterValues=@{ "CmdletName:ParameterName"={{ScriptBlock}} }

$PSDefaultParameterValues["Disabled"]=$True | $False
```

<span data-ttu-id="c45ff-120">Jokertecken tillåts i värdena **CmdletName** och **ParameterName** .</span><span class="sxs-lookup"><span data-stu-id="c45ff-120">Wildcard characters are permitted in the **CmdletName** and **ParameterName** values.</span></span>

<span data-ttu-id="c45ff-121">Om du vill ange, ändra, lägga till eller ta bort ett speciellt **nyckel/värde** -par från `$PSDefaultParameterValues` använder du metoderna för att redigera en standard-hash-tabell.</span><span class="sxs-lookup"><span data-stu-id="c45ff-121">To set, change, add, or remove a specific **Key/Value** pair from `$PSDefaultParameterValues`, use the methods to edit a standard hash table.</span></span> <span data-ttu-id="c45ff-122">Till exempel metoderna **Add** och **Remove** .</span><span class="sxs-lookup"><span data-stu-id="c45ff-122">For example, the **Add** and **Remove** methods.</span></span> <span data-ttu-id="c45ff-123">Dessa metoder skriver inte över andra värden i hash-tabellen.</span><span class="sxs-lookup"><span data-stu-id="c45ff-123">These methods don't overwrite other values in the hash table.</span></span>

<span data-ttu-id="c45ff-124">Det finns en annan syntax som inte skriver över en befintlig `$PSDefaultParameterValues` hash-tabell.</span><span class="sxs-lookup"><span data-stu-id="c45ff-124">There's another syntax that doesn't overwrite an existing `$PSDefaultParameterValues` hash table.</span></span> <span data-ttu-id="c45ff-125">Om du vill lägga till eller ändra ett speciellt **nyckel/värde** -par använder du följande syntax:</span><span class="sxs-lookup"><span data-stu-id="c45ff-125">To add or change a specific **Key/Value** pair, use the following syntax:</span></span>

```
$PSDefaultParameterValues["CmdletName:ParameterName"]="DefaultValue"
```

<span data-ttu-id="c45ff-126">**CmdletName** måste vara namnet på en cmdlet eller namnet på en avancerad funktion som använder attributet **CmdletBinding** .</span><span class="sxs-lookup"><span data-stu-id="c45ff-126">The **CmdletName** must be the name of a cmdlet or the name of an advanced function that uses the **CmdletBinding** attribute.</span></span> <span data-ttu-id="c45ff-127">Du kan inte använda `$PSDefaultParameterValues` för att ange standardvärden för skript eller enkla funktioner.</span><span class="sxs-lookup"><span data-stu-id="c45ff-127">You can't use `$PSDefaultParameterValues` to specify default values for scripts or simple functions.</span></span>

<span data-ttu-id="c45ff-128">**DefaultValue** kan vara ett objekt eller ett skript block.</span><span class="sxs-lookup"><span data-stu-id="c45ff-128">The **DefaultValue** can be an object or a script block.</span></span> <span data-ttu-id="c45ff-129">Om värdet är ett-skript block utvärderar PowerShell skript blocket och använder resultatet som parameter värde.</span><span class="sxs-lookup"><span data-stu-id="c45ff-129">If the value is a script block, PowerShell evaluates the script block and uses the result as the parameter value.</span></span> <span data-ttu-id="c45ff-130">När den angivna parametern accepterar ett skript Blocks värde, omger du skript block svärdet i en andra uppsättning klammerparenteser, till exempel:</span><span class="sxs-lookup"><span data-stu-id="c45ff-130">When the specified parameter accepts a script block value, enclose the script block value in a second set of braces, such as:</span></span>

```powershell
$PSDefaultParameterValues=@{ "Invoke-Command:ScriptBlock"={{Get-Process}} }
```

<span data-ttu-id="c45ff-131">Mer information finns i följande dokument:</span><span class="sxs-lookup"><span data-stu-id="c45ff-131">For more information, see the following documents:</span></span>

- [<span data-ttu-id="c45ff-132">about_Hash_Tables</span><span class="sxs-lookup"><span data-stu-id="c45ff-132">about_Hash_Tables</span></span>](about_Hash_Tables.md)
- [<span data-ttu-id="c45ff-133">about_Script_Blocks</span><span class="sxs-lookup"><span data-stu-id="c45ff-133">about_Script_Blocks</span></span>](about_Script_Blocks.md)
- [<span data-ttu-id="c45ff-134">about_Preference_Variables</span><span class="sxs-lookup"><span data-stu-id="c45ff-134">about_Preference_Variables</span></span>](about_Preference_Variables.md)

## <a name="examples"></a><span data-ttu-id="c45ff-135">Exempel</span><span class="sxs-lookup"><span data-stu-id="c45ff-135">Examples</span></span>

### <a name="how-to-set-psdefaultparametervalues"></a><span data-ttu-id="c45ff-136">Så här ställer du in \$ PSDefaultParameterValues</span><span class="sxs-lookup"><span data-stu-id="c45ff-136">How to set \$PSDefaultParameterValues</span></span>

<span data-ttu-id="c45ff-137">`$PSDefaultParameterValues` är en inställnings variabel, så den finns bara i den session där den har angetts.</span><span class="sxs-lookup"><span data-stu-id="c45ff-137">`$PSDefaultParameterValues` is a preference variable, so it exists only in the session in which it's set.</span></span> <span data-ttu-id="c45ff-138">Det har inget standardvärde.</span><span class="sxs-lookup"><span data-stu-id="c45ff-138">It has no default value.</span></span>

<span data-ttu-id="c45ff-139">Ange `$PSDefaultParameterValues` genom att skriva variabelns namn och ett eller flera **nyckel/värde-** par.</span><span class="sxs-lookup"><span data-stu-id="c45ff-139">To set `$PSDefaultParameterValues`, type the variable name and one or more **Key/Value** pairs.</span></span> <span data-ttu-id="c45ff-140">Om du kör ett annat `$PSDefaultParameterValues` kommando skriver det över den befintliga hash-tabellen.</span><span class="sxs-lookup"><span data-stu-id="c45ff-140">If you run another `$PSDefaultParameterValues` command, it overwrites the existing hash table.</span></span>

<span data-ttu-id="c45ff-141">Exempel på hur du ändrar **nyckel/värde-** par utan att skriva över befintliga värden för hash-tabeller finns i [så här lägger du till värden i \$ PSDefaultParameterValues](#how-to-add-values-to-psdefaultparametervalues) eller [hur du ändrar värden i \$ PSDefaultParameterValues](#how-to-change-values-in-psdefaultparametervalues).</span><span class="sxs-lookup"><span data-stu-id="c45ff-141">For examples about how to change **Key/Value** pairs without overwriting existing hash table values, see [How to add values to \$PSDefaultParameterValues](#how-to-add-values-to-psdefaultparametervalues) or [How to change values in \$PSDefaultParameterValues](#how-to-change-values-in-psdefaultparametervalues).</span></span>

<span data-ttu-id="c45ff-142">Om du vill spara `$PSDefaultParameterValues` för framtida sessioner lägger du till ett `$PSDefaultParameterValues` kommando i din PowerShell-profil.</span><span class="sxs-lookup"><span data-stu-id="c45ff-142">To save `$PSDefaultParameterValues` for future sessions, add a `$PSDefaultParameterValues` command to your PowerShell profile.</span></span> <span data-ttu-id="c45ff-143">Mer information finns i [about_Profiles](about_Profiles.md).</span><span class="sxs-lookup"><span data-stu-id="c45ff-143">For more information, see [about_Profiles](about_Profiles.md).</span></span>

#### <a name="set-a-custom-default-value"></a><span data-ttu-id="c45ff-144">Ange ett anpassat standardvärde</span><span class="sxs-lookup"><span data-stu-id="c45ff-144">Set a custom default value</span></span>

<span data-ttu-id="c45ff-145">**Nyckel/värde-** paret ställer in `Send-MailMessage:SmtpServer` nyckeln till ett anpassat standardvärde för **Server123**.</span><span class="sxs-lookup"><span data-stu-id="c45ff-145">The **Key/Value** pair sets the `Send-MailMessage:SmtpServer` key to a custom default value of **Server123**.</span></span>

```powershell
$PSDefaultParameterValues = @{
  "Send-MailMessage:SmtpServer"="Server123"
}
```

#### <a name="set-default-values-for-multiple-parameters"></a><span data-ttu-id="c45ff-146">Ange standardvärden för flera parametrar</span><span class="sxs-lookup"><span data-stu-id="c45ff-146">Set default values for multiple parameters</span></span>

<span data-ttu-id="c45ff-147">Om du vill ange standardvärden för flera parametrar, separera varje **nyckel/värde** -par med ett semikolon ( `;` ).</span><span class="sxs-lookup"><span data-stu-id="c45ff-147">To set default values for multiple parameters, separate each **Key/Value** pair with a semicolon (`;`).</span></span> <span data-ttu-id="c45ff-148">`Send-MailMessage:SmtpServer`Nycklarna och `Get-WinEvent:LogName` är inställda på anpassade standardvärden.</span><span class="sxs-lookup"><span data-stu-id="c45ff-148">The `Send-MailMessage:SmtpServer` and `Get-WinEvent:LogName` keys are set to custom default values.</span></span>

```powershell
$PSDefaultParameterValues = @{
  "Send-MailMessage:SmtpServer"="Server123";
  "Get-WinEvent:LogName"="Microsoft-Windows-PrintService/Operational"
}
```

#### <a name="use-wildcards-and-switch-parameters"></a><span data-ttu-id="c45ff-149">Använda jokertecken och växla parametrar</span><span class="sxs-lookup"><span data-stu-id="c45ff-149">Use wildcards and switch parameters</span></span>

<span data-ttu-id="c45ff-150">Cmdlet och parameter namn får innehålla jokertecken.</span><span class="sxs-lookup"><span data-stu-id="c45ff-150">The cmdlet and parameter names can contain wildcard characters.</span></span> <span data-ttu-id="c45ff-151">Använd `$True` och `$False` för att ange värden för växel parametrar, till exempel **verbose**.</span><span class="sxs-lookup"><span data-stu-id="c45ff-151">Use `$True` and `$False` to set values for switch parameters, such as **Verbose**.</span></span> <span data-ttu-id="c45ff-152">Den gemensamma parameterns **utförliga** parameter har angetts till `$True` för alla kommandon.</span><span class="sxs-lookup"><span data-stu-id="c45ff-152">The common parameter's **Verbose** parameter is set to `$True` for all commands.</span></span>

```powershell
$PSDefaultParameterValues = @{"*:Verbose"=$True}
```

#### <a name="use-an-array-for-the-default-value"></a><span data-ttu-id="c45ff-153">Använd en matris för standardvärdet</span><span class="sxs-lookup"><span data-stu-id="c45ff-153">Use an array for the default value</span></span>

<span data-ttu-id="c45ff-154">Om en parameter kan acceptera flera värden, en matris, kan du ange flera värden som standardvärden.</span><span class="sxs-lookup"><span data-stu-id="c45ff-154">If a parameter can accept multiple values, an array, you can set multiple values as the default values.</span></span> <span data-ttu-id="c45ff-155">Standardvärdet för `Invoke-Command:ComputerName` nyckeln anges till ett mat ris värde för **Server01** och **Server02**.</span><span class="sxs-lookup"><span data-stu-id="c45ff-155">The default value of the `Invoke-Command:ComputerName` key is set to an array value of **Server01** and **Server02**.</span></span>

```powershell
$PSDefaultParameterValues = @{
  "Invoke-Command:ComputerName"="Server01","Server02"
}
```

#### <a name="use-a-script-block"></a><span data-ttu-id="c45ff-156">Använd ett skript block</span><span class="sxs-lookup"><span data-stu-id="c45ff-156">Use a script block</span></span>

<span data-ttu-id="c45ff-157">Du kan använda ett-skript block för att ange olika standardvärden för en parameter under olika villkor.</span><span class="sxs-lookup"><span data-stu-id="c45ff-157">You can use a script block to specify different default values for a parameter under different conditions.</span></span> <span data-ttu-id="c45ff-158">PowerShell utvärderar skript blocket och använder resultatet som standard parameter värde.</span><span class="sxs-lookup"><span data-stu-id="c45ff-158">PowerShell evaluates the script block and uses the result as the default parameter value.</span></span>

<span data-ttu-id="c45ff-159">De `Format-Table:AutoSize` nyckel uppsättningar som byter parameter till värdet **Sant**.</span><span class="sxs-lookup"><span data-stu-id="c45ff-159">The `Format-Table:AutoSize` key sets that switch parameter to a default value of **True**.</span></span> <span data-ttu-id="c45ff-160">`If`Instruktionen innehåller ett villkor som `$host.Name` måste vara PowerShell-konsolen, **ConsoleHost**.</span><span class="sxs-lookup"><span data-stu-id="c45ff-160">The `If` statement contains a condition that the `$host.Name` must be the PowerShell console, **ConsoleHost**.</span></span>

```powershell
$PSDefaultParameterValues=@{
  "Format-Table:AutoSize"={if ($host.Name -eq "ConsoleHost"){$True}}
}
```

<span data-ttu-id="c45ff-161">Om en parameter accepterar ett skript Blocks värde, omger du skript blocket med en extra uppsättning klammerparenteser.</span><span class="sxs-lookup"><span data-stu-id="c45ff-161">If a parameter accepts a script block value, enclose the script block in an extra set of braces.</span></span> <span data-ttu-id="c45ff-162">När PowerShell utvärderar det yttre skript blocket är resultatet det inre skript blocket och det anges som standard parameter värde.</span><span class="sxs-lookup"><span data-stu-id="c45ff-162">When PowerShell evaluates the outer script block, the result is the inner script block, and that is set as the default parameter value.</span></span>

<span data-ttu-id="c45ff-163">`Invoke-Command:ScriptBlock`Nyckeln har angetts till ett standardvärde för **system händelse loggen** eftersom skript blocket omges av en andra uppsättning klammerparenteser.</span><span class="sxs-lookup"><span data-stu-id="c45ff-163">The `Invoke-Command:ScriptBlock` key set to a default value of the **System event log** because the script block is enclosed in a second set of braces.</span></span> <span data-ttu-id="c45ff-164">Resultatet av skript blocket skickas till `Invoke-Command` cmdlet: en.</span><span class="sxs-lookup"><span data-stu-id="c45ff-164">The result of the script block is passed to the `Invoke-Command` cmdlet.</span></span>

```powershell
$PSDefaultParameterValues=@{
  "Invoke-Command:ScriptBlock"={{Get-EventLog -Log System}}
}
```

### <a name="how-to-get-psdefaultparametervalues"></a><span data-ttu-id="c45ff-165">Så här hämtar du \$ PSDefaultParameterValues</span><span class="sxs-lookup"><span data-stu-id="c45ff-165">How to get \$PSDefaultParameterValues</span></span>

<span data-ttu-id="c45ff-166">Hash-tabellens värden visas genom att `$PSDefaultParameterValues` du anger i PowerShell-prompten.</span><span class="sxs-lookup"><span data-stu-id="c45ff-166">The hash table values are displayed by entering `$PSDefaultParameterValues` at the PowerShell prompt.</span></span>

<span data-ttu-id="c45ff-167">En `$PSDefaultParameterValues` hash-tabell har angetts med tre **nyckel/värde-** par.</span><span class="sxs-lookup"><span data-stu-id="c45ff-167">A `$PSDefaultParameterValues` hash table is set with three **Key/Value** pairs.</span></span>
<span data-ttu-id="c45ff-168">Den här hash-tabellen används i följande exempel som beskriver hur du lägger till, ändrar och tar bort värden från `$PSDefaultParameterValues` .</span><span class="sxs-lookup"><span data-stu-id="c45ff-168">This hash table is used in the following examples that describe how to add, change, and remove values from `$PSDefaultParameterValues`.</span></span>

```
PS> $PSDefaultParameterValues = @{
  "Send-MailMessage:SmtpServer"="Server123"
  "Get-WinEvent:LogName"="Microsoft-Windows-PrintService/Operational"
  "Get-*:Verbose"=$True
}

PS> $PSDefaultParameterValues

Name                           Value
----                           -----
Get-WinEvent:LogName           Microsoft-Windows-PrintService/Operational
Get-*:Verbose                  True
Send-MailMessage:SmtpServer    Server123
```

<span data-ttu-id="c45ff-169">Använd följande syntax för att hämta värdet för en speciell `CmdletName:ParameterName` nyckel:</span><span class="sxs-lookup"><span data-stu-id="c45ff-169">To get the value of a specific `CmdletName:ParameterName` key, use the following syntax:</span></span>

```
$PSDefaultParameterValues["CmdletName:ParameterName"]
```

<span data-ttu-id="c45ff-170">Till exempel för att hämta värdet för `Send-MailMessage:SmtpServer` nyckeln.</span><span class="sxs-lookup"><span data-stu-id="c45ff-170">For example, to get the value for the `Send-MailMessage:SmtpServer` key.</span></span>

```
PS> $PSDefaultParameterValues["Send-MailMessage:SmtpServer"]
Server123
```

### <a name="how-to-add-values-to-psdefaultparametervalues"></a><span data-ttu-id="c45ff-171">Så här lägger du till värden i \$ PSDefaultParameterValues</span><span class="sxs-lookup"><span data-stu-id="c45ff-171">How to add values to \$PSDefaultParameterValues</span></span>

<span data-ttu-id="c45ff-172">`$PSDefaultParameterValues`Använd metoden **Add** för att lägga till ett värde i.</span><span class="sxs-lookup"><span data-stu-id="c45ff-172">To add a value to `$PSDefaultParameterValues`, use the **Add** method.</span></span> <span data-ttu-id="c45ff-173">Om du lägger till ett värde påverkas inte hash-tabellens befintliga värden.</span><span class="sxs-lookup"><span data-stu-id="c45ff-173">Adding a value doesn't affect the hash table's existing values.</span></span>

<span data-ttu-id="c45ff-174">Använd kommatecken ( `,` ) för att avgränsa **nyckeln** från **värdet**.</span><span class="sxs-lookup"><span data-stu-id="c45ff-174">Use a comma (`,`) to separate the **Key** from the **Value**.</span></span> <span data-ttu-id="c45ff-175">Följande syntax visar hur du använder metoden **Add** för `$PSDefaultParameterValues` .</span><span class="sxs-lookup"><span data-stu-id="c45ff-175">The following syntax shows how to use the **Add** method for `$PSDefaultParameterValues`.</span></span>

```
PS> $PSDefaultParameterValues.Add("CmdletName:ParameterName", "DefaultValue")
```

<span data-ttu-id="c45ff-176">Hash-tabellen som skapades i föregående exempel uppdateras med ett nytt **nyckel/värde-** par.</span><span class="sxs-lookup"><span data-stu-id="c45ff-176">The hash table created in the prior example is updated with a new **Key/Value** pair.</span></span> <span data-ttu-id="c45ff-177">Metoden **Add** ställer in `Get-Process:Name` nyckeln till **PowerShell**-värdet.</span><span class="sxs-lookup"><span data-stu-id="c45ff-177">The **Add** method sets the `Get-Process:Name` key to the value **PowerShell**.</span></span>

```powershell
$PSDefaultParameterValues.Add("Get-Process:Name", "PowerShell")
```

<span data-ttu-id="c45ff-178">Följande syntax uppnår samma resultat.</span><span class="sxs-lookup"><span data-stu-id="c45ff-178">The following syntax accomplishes the same result.</span></span>

```powershell
$PSDefaultParameterValues["Get-Process:Name"]="PowerShell"
```

<span data-ttu-id="c45ff-179">`$PSDefaultParameterValues`Den uppdaterade hash-tabellen visas i variabeln.</span><span class="sxs-lookup"><span data-stu-id="c45ff-179">The `$PSDefaultParameterValues` variable displays the updated hash table.</span></span> <span data-ttu-id="c45ff-180">`Get-Process:Name`Nyckeln har lagts till.</span><span class="sxs-lookup"><span data-stu-id="c45ff-180">The `Get-Process:Name` key was added.</span></span>

```
PS> $PSDefaultParameterValues

Name                           Value
----                           -----
Get-Process:Name               PowerShell
Get-WinEvent:LogName           Microsoft-Windows-PrintService/Operational
Get-*:Verbose                  True
Send-MailMessage:SmtpServer    Server123
```

### <a name="how-to-remove-values-from-psdefaultparametervalues"></a><span data-ttu-id="c45ff-181">Ta bort värden från \$ PSDefaultParameterValues</span><span class="sxs-lookup"><span data-stu-id="c45ff-181">How to remove values from \$PSDefaultParameterValues</span></span>

<span data-ttu-id="c45ff-182">Ta bort ett värde från `$PSDefaultParameterValues` genom att använda **Remove** -metoden för hash-tabeller.</span><span class="sxs-lookup"><span data-stu-id="c45ff-182">To remove a value from `$PSDefaultParameterValues`, use the **Remove** method of hash tables.</span></span> <span data-ttu-id="c45ff-183">Om du tar bort ett värde påverkas inte hash-tabellens befintliga värden.</span><span class="sxs-lookup"><span data-stu-id="c45ff-183">Removing a value doesn't affect the hash table's existing values.</span></span>

<span data-ttu-id="c45ff-184">Följande syntax visar hur du använder **Remove** -metoden i `$PSDefaultParameterValues` .</span><span class="sxs-lookup"><span data-stu-id="c45ff-184">The following syntax shows how to use the **Remove** method on `$PSDefaultParameterValues`.</span></span>

```
PS> $PSDefaultParameterValues.Remove("CmdletName:ParameterName")
```

<span data-ttu-id="c45ff-185">I det här exemplet uppdateras hash-tabellen som skapades i föregående exempel för att ta bort ett **nyckel/värde-** par.</span><span class="sxs-lookup"><span data-stu-id="c45ff-185">In this example, the hash table created in the prior example is updated to remove a **Key/Value** pair.</span></span> <span data-ttu-id="c45ff-186">Metoden **Remove** tar bort `Get-Process:Name` nyckeln.</span><span class="sxs-lookup"><span data-stu-id="c45ff-186">The **Remove** method removes the `Get-Process:Name` key.</span></span>

```powershell
$PSDefaultParameterValues.Remove("Get-Process:Name")
```

<span data-ttu-id="c45ff-187">`$PSDefaultParameterValues`Den uppdaterade hash-tabellen visas i variabeln.</span><span class="sxs-lookup"><span data-stu-id="c45ff-187">The `$PSDefaultParameterValues` variable displays the updated hash table.</span></span> <span data-ttu-id="c45ff-188">`Get-Process:Name`Nyckeln har tagits bort.</span><span class="sxs-lookup"><span data-stu-id="c45ff-188">The `Get-Process:Name` key was removed.</span></span>

```
PS> $PSDefaultParameterValues

Name                           Value
----                           -----
Get-WinEvent:LogName           Microsoft-Windows-PrintService/Operational
Get-*:Verbose                  True
Send-MailMessage:SmtpServer    Server123
```

### <a name="how-to-change-values-in-psdefaultparametervalues"></a><span data-ttu-id="c45ff-189">Ändra värden i \$ PSDefaultParameterValues</span><span class="sxs-lookup"><span data-stu-id="c45ff-189">How to change values in \$PSDefaultParameterValues</span></span>

<span data-ttu-id="c45ff-190">Ändringar av ett speciellt värde påverkar inte befintliga värden för hash-tabeller.</span><span class="sxs-lookup"><span data-stu-id="c45ff-190">Changes to a specific value don't affect existing hash table values.</span></span> <span data-ttu-id="c45ff-191">Om du vill ändra ett särskilt **nyckel/värde** -par i `$PSDefaultParameterValues` använder du följande syntax:</span><span class="sxs-lookup"><span data-stu-id="c45ff-191">To change a specific **Key/Value** pair in `$PSDefaultParameterValues`, use the following syntax:</span></span>

```
PS> $PSDefaultParameterValues["CmdletName:ParameterName"]="DefaultValue"
```

<span data-ttu-id="c45ff-192">I det här exemplet uppdateras hash-tabellen som skapades i föregående exempel för att ändra ett **nyckel/värde-** par.</span><span class="sxs-lookup"><span data-stu-id="c45ff-192">In this example, the hash table created in the prior example is updated to change a **Key/Value** pair.</span></span> <span data-ttu-id="c45ff-193">Följande kommando ändrar `Send-MailMessage:SmtpServer` nyckeln till ett nytt värde för **ServerXYZ**.</span><span class="sxs-lookup"><span data-stu-id="c45ff-193">The following command changes the `Send-MailMessage:SmtpServer` key to a new value of **ServerXYZ**.</span></span>

```powershell
$PSDefaultParameterValues["Send-MailMessage:SmtpServer"]="ServerXYZ"
```

<span data-ttu-id="c45ff-194">`$PSDefaultParameterValues`Den uppdaterade hash-tabellen visas i variabeln.</span><span class="sxs-lookup"><span data-stu-id="c45ff-194">The `$PSDefaultParameterValues` variable displays the updated hash table.</span></span> <span data-ttu-id="c45ff-195">`Send-MailMessage:SmtpServer`Nyckeln ändrades till ett nytt värde.</span><span class="sxs-lookup"><span data-stu-id="c45ff-195">The `Send-MailMessage:SmtpServer` key was changed to a new value.</span></span>

```
PS> $PSDefaultParameterValues

Name                           Value
----                           -----
Get-WinEvent:LogName           Microsoft-Windows-PrintService/Operational
Get-*:Verbose                  True
Send-MailMessage:SmtpServer    ServerXYZ
```

### <a name="how-to-disable-and-re-enable-psdefaultparametervalues"></a><span data-ttu-id="c45ff-196">Inaktivera och återaktivera \$ PSDefaultParameterValues</span><span class="sxs-lookup"><span data-stu-id="c45ff-196">How to disable and re-enable \$PSDefaultParameterValues</span></span>

<span data-ttu-id="c45ff-197">Du kan tillfälligt inaktivera och sedan återaktivera `$PSDefaultParameterValues` .</span><span class="sxs-lookup"><span data-stu-id="c45ff-197">You can temporarily disable and then re-enable `$PSDefaultParameterValues`.</span></span>
<span data-ttu-id="c45ff-198">`$PSDefaultParameterValues`Att inaktivera är användbart om du kör skript som behöver olika standard parameter värden.</span><span class="sxs-lookup"><span data-stu-id="c45ff-198">Disabling `$PSDefaultParameterValues` is useful if you're running scripts that need different default parameter values.</span></span>

<span data-ttu-id="c45ff-199">Om du vill inaktivera `$PSDefaultParameterValues` lägger du till en nyckel med `Disabled` värdet **Sant**.</span><span class="sxs-lookup"><span data-stu-id="c45ff-199">To disable `$PSDefaultParameterValues`, add a key of `Disabled` with a value of **True**.</span></span> <span data-ttu-id="c45ff-200">Värdena i `$PSDefaultParameterValues` bevaras, men är inte effektiva.</span><span class="sxs-lookup"><span data-stu-id="c45ff-200">The values in `$PSDefaultParameterValues` are preserved, but aren't effective.</span></span>

```
PS> $PSDefaultParameterValues.Add("Disabled", $True)
```

<span data-ttu-id="c45ff-201">Följande syntax uppnår samma resultat.</span><span class="sxs-lookup"><span data-stu-id="c45ff-201">The following syntax accomplishes the same result.</span></span>

```
PS> $PSDefaultParameterValues["Disabled"]=$True
```

<span data-ttu-id="c45ff-202">`$PSDefaultParameterValues`Variabeln visar den uppdaterade hash-tabellen med värdet för `Disabled` nyckeln.</span><span class="sxs-lookup"><span data-stu-id="c45ff-202">The `$PSDefaultParameterValues` variable displays the updated hash table with the value for the `Disabled` key.</span></span>

```
PS> $PSDefaultParameterValues

Name                           Value
----                           -----
Disabled                       True
Get-WinEvent:LogName           Microsoft-Windows-PrintService/Operational
Get-*:Verbose                  True
Send-MailMessage:SmtpServer    ServerXYZ
```

<span data-ttu-id="c45ff-203">`$PSDefaultParameterValues`Ta bort den **inaktiverade** nyckeln eller ändra värdet för den **inaktiverade** nyckeln till om du vill aktivera det igen `$False` .</span><span class="sxs-lookup"><span data-stu-id="c45ff-203">To re-enable `$PSDefaultParameterValues`, remove the **Disabled** key or change the value of the **Disabled** key to `$False`.</span></span> <span data-ttu-id="c45ff-204">Det tidigare värdet för `$PSDefaultParameterValues` börjar gälla igen.</span><span class="sxs-lookup"><span data-stu-id="c45ff-204">The previous value of `$PSDefaultParameterValues` is effective again.</span></span>

```
PS> $PSDefaultParameterValues.Remove("Disabled")
```

<span data-ttu-id="c45ff-205">Följande syntax uppnår samma resultat.</span><span class="sxs-lookup"><span data-stu-id="c45ff-205">The following syntax accomplishes the same result.</span></span>

```
PS> $PSDefaultParameterValues["Disabled"]=$False
```

<span data-ttu-id="c45ff-206">`$PSDefaultParameterValues`Den uppdaterade hash-tabellen visas i variabeln.</span><span class="sxs-lookup"><span data-stu-id="c45ff-206">The `$PSDefaultParameterValues` variable displays the updated hash table.</span></span> <span data-ttu-id="c45ff-207">När metoden **Remove** används `Disabled` tas nyckeln bort från utdata.</span><span class="sxs-lookup"><span data-stu-id="c45ff-207">When the **Remove** method is used, the `Disabled` key is removed from the output.</span></span>
<span data-ttu-id="c45ff-208">Om den alternativa syntaxen användes för att aktivera igen `$PSDefaultParameterValues` `Disabled` visas nyckeln som **falsk**.</span><span class="sxs-lookup"><span data-stu-id="c45ff-208">If the alternate syntax was used to re-enable `$PSDefaultParameterValues`, the `Disabled` key is displayed as **False**.</span></span>

```
PS> $PSDefaultParameterValues

Name                           Value
----                           -----
Disabled                       False
Get-WinEvent:LogName           Microsoft-Windows-PrintService/Operational
Get-*:Verbose                  True
Send-MailMessage:SmtpServer    ServerXYZ
```

## <a name="see-also"></a><span data-ttu-id="c45ff-209">Se även</span><span class="sxs-lookup"><span data-stu-id="c45ff-209">See also</span></span>

[<span data-ttu-id="c45ff-210">about_CommonParameters</span><span class="sxs-lookup"><span data-stu-id="c45ff-210">about_CommonParameters</span></span>](https://go.microsoft.com/fwlink/?LinkID=113216)

[<span data-ttu-id="c45ff-211">about_Functions_Advanced</span><span class="sxs-lookup"><span data-stu-id="c45ff-211">about_Functions_Advanced</span></span>](about_Functions_Advanced.md)

[<span data-ttu-id="c45ff-212">about_Functions_CmdletBindingAttribute</span><span class="sxs-lookup"><span data-stu-id="c45ff-212">about_Functions_CmdletBindingAttribute</span></span>](about_Functions_CmdletBindingAttribute.md)

[<span data-ttu-id="c45ff-213">about_Hash_Tables</span><span class="sxs-lookup"><span data-stu-id="c45ff-213">about_Hash_Tables</span></span>](about_Hash_Tables.md)

[<span data-ttu-id="c45ff-214">about_Preference_Variables</span><span class="sxs-lookup"><span data-stu-id="c45ff-214">about_Preference_Variables</span></span>](about_Preference_Variables.md)

[<span data-ttu-id="c45ff-215">about_Profiles</span><span class="sxs-lookup"><span data-stu-id="c45ff-215">about_Profiles</span></span>](about_Profiles.md)

[<span data-ttu-id="c45ff-216">about_Script_Blocks</span><span class="sxs-lookup"><span data-stu-id="c45ff-216">about_Script_Blocks</span></span>](about_Script_Blocks.md)

