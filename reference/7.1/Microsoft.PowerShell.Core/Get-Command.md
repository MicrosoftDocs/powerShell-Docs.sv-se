---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 05/20/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/get-command?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Command
ms.openlocfilehash: 5f2752f53fb5f74b6436548c3bd4fa731d2b02d5
ms.sourcegitcommit: 04faa7dc1122bce839295d4891bd8b2f0ecb06ef
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/05/2021
ms.locfileid: "97879243"
---
# <span data-ttu-id="ce613-103">Get-Command</span><span class="sxs-lookup"><span data-stu-id="ce613-103">Get-Command</span></span>

## <span data-ttu-id="ce613-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="ce613-104">SYNOPSIS</span></span>
<span data-ttu-id="ce613-105">Hämtar alla kommandon.</span><span class="sxs-lookup"><span data-stu-id="ce613-105">Gets all commands.</span></span>

## <span data-ttu-id="ce613-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="ce613-106">SYNTAX</span></span>

### <span data-ttu-id="ce613-107">CmdletSet (standard)</span><span class="sxs-lookup"><span data-stu-id="ce613-107">CmdletSet (Default)</span></span>

```
Get-Command [-Verb <String[]>] [-Noun <String[]>] [-Module <String[]>]
 [-FullyQualifiedModule <ModuleSpecification[]>] [-TotalCount <Int32>] [-Syntax] [-ShowCommandInfo]
 [[-ArgumentList] <Object[]>] [-All] [-ListImported] [-ParameterName <String[]>]
 [-ParameterType <PSTypeName[]>] [<CommonParameters>]
```

### <span data-ttu-id="ce613-108">AllCommandSet</span><span class="sxs-lookup"><span data-stu-id="ce613-108">AllCommandSet</span></span>

```
Get-Command [[-Name] <String[]>] [-Module <String[]>]
 [-FullyQualifiedModule <ModuleSpecification[]>] [-CommandType <CommandTypes>] [-TotalCount <Int32>]
 [-Syntax] [-ShowCommandInfo] [[-ArgumentList] <Object[]>] [-All] [-ListImported]
 [-ParameterName <String[]>] [-ParameterType <PSTypeName[]>] [-UseFuzzyMatching]
 [-UseAbbreviationExpansion] [<CommonParameters>]
```

## <span data-ttu-id="ce613-109">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="ce613-109">DESCRIPTION</span></span>

<span data-ttu-id="ce613-110">Cmdlet: en `Get-Command` hämtar alla kommandon som är installerade på datorn, inklusive cmdlets, alias, funktioner, filter, skript och program.</span><span class="sxs-lookup"><span data-stu-id="ce613-110">The `Get-Command` cmdlet gets all commands that are installed on the computer, including cmdlets, aliases, functions, filters, scripts, and applications.</span></span> <span data-ttu-id="ce613-111">`Get-Command` hämtar kommandon från PowerShell-moduler och kommandon som har importer ATS från andra sessioner.</span><span class="sxs-lookup"><span data-stu-id="ce613-111">`Get-Command` gets the commands from PowerShell modules and commands that were imported from other sessions.</span></span> <span data-ttu-id="ce613-112">Om du bara vill hämta kommandon som har importer ATS till den aktuella sessionen använder du parametern **ListImported** .</span><span class="sxs-lookup"><span data-stu-id="ce613-112">To get only commands that have been imported into the current session, use the **ListImported** parameter.</span></span>

<span data-ttu-id="ce613-113">Utan parametrar `Get-Command` hämtar alla cmdletar, funktioner och alias som är installerade på datorn.</span><span class="sxs-lookup"><span data-stu-id="ce613-113">Without parameters, `Get-Command` gets all of the cmdlets, functions, and aliases installed on the computer.</span></span> <span data-ttu-id="ce613-114">`Get-Command *` hämtar alla typer av kommandon, inklusive alla icke-PowerShell-filer i Path-miljövariabeln ( `$env:Path` ) som visas i program kommando typen.</span><span class="sxs-lookup"><span data-stu-id="ce613-114">`Get-Command *` gets all types of commands, including all of the non-PowerShell files in the Path environment variable (`$env:Path`), which it lists in the Application command type.</span></span>

<span data-ttu-id="ce613-115">`Get-Command` som använder kommandots exakta namn, utan jokertecken, importerar automatiskt den modul som innehåller kommandot så att du kan använda kommandot direkt.</span><span class="sxs-lookup"><span data-stu-id="ce613-115">`Get-Command` that uses the exact name of the command, without wildcard characters, automatically imports the module that contains the command so that you can use the command immediately.</span></span> <span data-ttu-id="ce613-116">Om du vill aktivera, inaktivera och konfigurera automatisk import av moduler använder du `$PSModuleAutoLoadingPreference` Preference-variabeln.</span><span class="sxs-lookup"><span data-stu-id="ce613-116">To enable, disable, and configure automatic importing of modules, use the `$PSModuleAutoLoadingPreference` preference variable.</span></span> <span data-ttu-id="ce613-117">Mer information finns i [about_Preference_Variables](About/about_Preference_Variables.md).</span><span class="sxs-lookup"><span data-stu-id="ce613-117">For more information, see [about_Preference_Variables](About/about_Preference_Variables.md).</span></span>

<span data-ttu-id="ce613-118">`Get-Command` hämtar data direkt från kommando koden, till skillnad `Get-Help` från, som hämtar information från hjälp avsnitten.</span><span class="sxs-lookup"><span data-stu-id="ce613-118">`Get-Command` gets its data directly from the command code, unlike `Get-Help`, which gets its information from help topics.</span></span>

<span data-ttu-id="ce613-119">Från och med Windows PowerShell 5,0 visar resultatet av `Get-Command` cmdleten **versions** kolumnen som standard.</span><span class="sxs-lookup"><span data-stu-id="ce613-119">Starting in Windows PowerShell 5.0, results of the `Get-Command` cmdlet display a **Version** column by default.</span></span> <span data-ttu-id="ce613-120">En ny **versions** egenskap har lagts till i **CommandInfo** -klassen.</span><span class="sxs-lookup"><span data-stu-id="ce613-120">A new **Version** property has been added to the **CommandInfo** class.</span></span>

## <span data-ttu-id="ce613-121">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="ce613-121">EXAMPLES</span></span>

### <span data-ttu-id="ce613-122">Exempel 1: Hämta cmdlets, Functions och alias</span><span class="sxs-lookup"><span data-stu-id="ce613-122">Example 1: Get cmdlets, functions, and aliases</span></span>

<span data-ttu-id="ce613-123">Det här kommandot hämtar PowerShell-cmdletar, funktioner och alias som är installerade på datorn.</span><span class="sxs-lookup"><span data-stu-id="ce613-123">This command gets the PowerShell cmdlets, functions, and aliases that are installed on the computer.</span></span>

```powershell
Get-Command
```

### <span data-ttu-id="ce613-124">Exempel 2: Hämta kommandon i den aktuella sessionen</span><span class="sxs-lookup"><span data-stu-id="ce613-124">Example 2: Get commands in the current session</span></span>

<span data-ttu-id="ce613-125">Det här kommandot använder parametern **ListImported** för att bara hämta kommandon i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="ce613-125">This command uses the **ListImported** parameter to get only the commands in the current session.</span></span>

```powershell
Get-Command -ListImported
```

### <span data-ttu-id="ce613-126">Exempel 3: Hämta cmdletar och visa dem i ordning</span><span class="sxs-lookup"><span data-stu-id="ce613-126">Example 3: Get cmdlets and display them in order</span></span>

<span data-ttu-id="ce613-127">Det här kommandot hämtar alla cmdletar, sorterar dem i alfabetisk ordning efter Substantiv i cmdlet-namnet och visar dem i Substantiv-baserade grupper.</span><span class="sxs-lookup"><span data-stu-id="ce613-127">This command gets all of the cmdlets, sorts them alphabetically by the noun in the cmdlet name, and then displays them in noun-based groups.</span></span> <span data-ttu-id="ce613-128">Den här visningen kan hjälpa dig att hitta cmdletar för en uppgift.</span><span class="sxs-lookup"><span data-stu-id="ce613-128">This display can help you find the cmdlets for a task.</span></span>

```powershell
Get-Command -Type Cmdlet | Sort-Object -Property Noun | Format-Table -GroupBy Noun
```

### <span data-ttu-id="ce613-129">Exempel 4: Hämta kommandon i en modul</span><span class="sxs-lookup"><span data-stu-id="ce613-129">Example 4: Get commands in a module</span></span>

<span data-ttu-id="ce613-130">Detta kommando använder **modulen modul** för att hämta kommandon i modulerna Microsoft. PowerShell. Security och Microsoft. PowerShell. Utility.</span><span class="sxs-lookup"><span data-stu-id="ce613-130">This command uses the **Module** parameter to get the commands in the Microsoft.PowerShell.Security and Microsoft.PowerShell.Utility modules.</span></span>

```powershell
Get-Command -Module Microsoft.PowerShell.Security, Microsoft.PowerShell.Utility
```

### <span data-ttu-id="ce613-131">Exempel 5: Hämta information om en cmdlet</span><span class="sxs-lookup"><span data-stu-id="ce613-131">Example 5: Get information about a cmdlet</span></span>

<span data-ttu-id="ce613-132">Det här kommandot hämtar information om `Get-AppLockerPolicy` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="ce613-132">This command gets information about the `Get-AppLockerPolicy` cmdlet.</span></span> <span data-ttu-id="ce613-133">Den importerar även **AppLocker** -modulen, som lägger till alla kommandon i **AppLocker** -modulen i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="ce613-133">It also imports the **AppLocker** module, which adds all of the commands in the **AppLocker** module to the current session.</span></span>

```powershell
Get-Command Get-AppLockerPolicy
```

<span data-ttu-id="ce613-134">När en modul importeras automatiskt är det samma sak som att använda Import-Module-cmdleten.</span><span class="sxs-lookup"><span data-stu-id="ce613-134">When a module is imported automatically, the effect is the same as using the Import-Module cmdlet.</span></span>
<span data-ttu-id="ce613-135">Modulen kan lägga till kommandon, typer och formatering av filer och köra skript i sessionen.</span><span class="sxs-lookup"><span data-stu-id="ce613-135">The module can add commands, types and formatting files, and run scripts in the session.</span></span> <span data-ttu-id="ce613-136">Om du vill aktivera, inaktivera och konfigurera automatisk import av moduler använder du `$PSModuleAutoLoadingPreference` Preference-variabeln.</span><span class="sxs-lookup"><span data-stu-id="ce613-136">To enable, disable, and configuration automatic importing of modules, use the `$PSModuleAutoLoadingPreference` preference variable.</span></span> <span data-ttu-id="ce613-137">Mer information finns i [about_Preference_Variables](../Microsoft.PowerShell.Core/About/about_Preference_Variables.md).</span><span class="sxs-lookup"><span data-stu-id="ce613-137">For more information, see [about_Preference_Variables](../Microsoft.PowerShell.Core/About/about_Preference_Variables.md).</span></span>

### <span data-ttu-id="ce613-138">Exempel 6: Hämta syntaxen för en cmdlet</span><span class="sxs-lookup"><span data-stu-id="ce613-138">Example 6: Get the syntax of a cmdlet</span></span>

<span data-ttu-id="ce613-139">Det här kommandot använder parametrarna **argument List** och **syntax** för att hämta syntaxen för `Get-ChildItem` cmdleten när den används i certifikatet: enhet.</span><span class="sxs-lookup"><span data-stu-id="ce613-139">This command uses the **ArgumentList** and **Syntax** parameters to get the syntax of the `Get-ChildItem` cmdlet when it is used in the Cert: drive.</span></span> <span data-ttu-id="ce613-140">Certifikatet: enheten är en PowerShell-enhet som certifikat leverantören lägger till i sessionen.</span><span class="sxs-lookup"><span data-stu-id="ce613-140">The Cert: drive is a PowerShell drive that the Certificate Provider adds to the session.</span></span>

```powershell
Get-Command  -Name Get-Childitem -Args Cert: -Syntax
```

<span data-ttu-id="ce613-141">När du jämför den syntax som visas i utdata med den syntax som visas när du utelämnar parametern **args** (**argument List**) ser du att **certifikat leverantören** lägger till en dynamisk parameter, **CodeSigningCert**, till `Get-ChildItem` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="ce613-141">When you compare the syntax displayed in the output with the syntax that is displayed when you omit the **Args** (**ArgumentList**) parameter, you'll see that the **Certificate provider** adds a dynamic parameter, **CodeSigningCert**, to the `Get-ChildItem` cmdlet.</span></span>

<span data-ttu-id="ce613-142">Mer information om certifikat leverantören finns [about_Certificate_Provider](../Microsoft.PowerShell.Security/About/about_Certificate_Provider.md).</span><span class="sxs-lookup"><span data-stu-id="ce613-142">For more information about the Certificate provider, see [about_Certificate_Provider](../Microsoft.PowerShell.Security/About/about_Certificate_Provider.md).</span></span>

### <span data-ttu-id="ce613-143">Exempel 7: hämta dynamiska parametrar</span><span class="sxs-lookup"><span data-stu-id="ce613-143">Example 7: Get dynamic parameters</span></span>

<span data-ttu-id="ce613-144">Kommandot i exemplet använder `Get-DynamicParameters` funktionen för att hämta de dynamiska parametrar som certifikat leverantören lägger till i `Get-ChildItem` cmdleten när den används i certifikatet: enhet.</span><span class="sxs-lookup"><span data-stu-id="ce613-144">The command in the example uses the `Get-DynamicParameters` function to get the dynamic parameters that the Certificate provider adds to the `Get-ChildItem` cmdlet when it is used in the Cert: drive.</span></span>

```powershell
function Get-DynamicParameters
{
    param ($Cmdlet, $PSDrive)
    (Get-Command -Name $Cmdlet -ArgumentList $PSDrive).ParameterSets | ForEach-Object {$_.Parameters} | Where-Object { $_.IsDynamic } | Select-Object -Property Name -Unique
}
Get-DynamicParameters -Cmdlet Get-ChildItem -PSDrive Cert:
```

```Output
Name
----
CodeSigningCert
```

<span data-ttu-id="ce613-145">`Get-DynamicParameters`Funktionen i det här exemplet hämtar dynamiska parametrar för en cmdlet.</span><span class="sxs-lookup"><span data-stu-id="ce613-145">The `Get-DynamicParameters` function in this example gets the dynamic parameters of a cmdlet.</span></span> <span data-ttu-id="ce613-146">Detta är ett alternativ till den metod som användes i föregående exempel.</span><span class="sxs-lookup"><span data-stu-id="ce613-146">This is an alternative to the method used in the previous example.</span></span> <span data-ttu-id="ce613-147">Dynamisk parameter kan läggas till i en cmdlet av en annan cmdlet eller en provider.</span><span class="sxs-lookup"><span data-stu-id="ce613-147">Dynamic parameter can be added to a cmdlet by another cmdlet or a provider.</span></span>

### <span data-ttu-id="ce613-148">Exempel 8: Hämta alla kommandon av alla typer</span><span class="sxs-lookup"><span data-stu-id="ce613-148">Example 8: Get all commands of all types</span></span>

<span data-ttu-id="ce613-149">Det här kommandot hämtar alla kommandon för alla typer på den lokala datorn, inklusive körbara filer i sökvägar i miljövariabeln **Path** ( `$env:path` ).</span><span class="sxs-lookup"><span data-stu-id="ce613-149">This command gets all commands of all types on the local computer, including executable files in the paths of the **Path** environment variable (`$env:path`).</span></span>

```powershell
Get-Command *
```

<span data-ttu-id="ce613-150">Den returnerar ett **ApplicationInfo** -objekt (system. Management. Automation. ApplicationInfo) för varje fil, inte ett **fileinfo** -objekt (system. io. fileinfo).</span><span class="sxs-lookup"><span data-stu-id="ce613-150">It returns an **ApplicationInfo** object (System.Management.Automation.ApplicationInfo) for each file, not a **FileInfo** object (System.IO.FileInfo).</span></span>

### <span data-ttu-id="ce613-151">Exempel 9: Hämta cmdlets med hjälp av ett parameter namn och en typ</span><span class="sxs-lookup"><span data-stu-id="ce613-151">Example 9: Get cmdlets by using a parameter name and type</span></span>

<span data-ttu-id="ce613-152">Detta kommando hämtar cmdletar som har en parameter vars namn inkluderar auth och vars typ är **AuthenticationMechanism**.</span><span class="sxs-lookup"><span data-stu-id="ce613-152">This command gets cmdlets that have a parameter whose name includes Auth and whose type is **AuthenticationMechanism**.</span></span>

```powershell
Get-Command -ParameterName *Auth* -ParameterType AuthenticationMechanism
```

<span data-ttu-id="ce613-153">Du kan använda ett kommando som det här för att hitta cmdletar som låter dig ange den metod som används för att autentisera användaren.</span><span class="sxs-lookup"><span data-stu-id="ce613-153">You can use a command like this one to find cmdlets that let you specify the method that is used to authenticate the user.</span></span>

<span data-ttu-id="ce613-154">Parametern **ParameterType** särskiljer parametrar som tar ett **AuthenticationMechanism** -värde från de som tar en **AuthenticationLevel** -parameter, även om de har liknande namn.</span><span class="sxs-lookup"><span data-stu-id="ce613-154">The **ParameterType** parameter distinguishes parameters that take an **AuthenticationMechanism** value from those that take an **AuthenticationLevel** parameter, even when they have similar names.</span></span>

### <span data-ttu-id="ce613-155">Exempel 10: Hämta ett alias</span><span class="sxs-lookup"><span data-stu-id="ce613-155">Example 10: Get an alias</span></span>

<span data-ttu-id="ce613-156">Det här exemplet visar hur du använder `Get-Command` cmdleten med ett alias.</span><span class="sxs-lookup"><span data-stu-id="ce613-156">This example shows how to use the `Get-Command` cmdlet with an alias.</span></span>

```powershell
Get-Command -Name dir
```

```Output
CommandType     Name                                               ModuleName
-----------     ----                                               ----------
Alias           dir -> Get-ChildItem
```

<span data-ttu-id="ce613-157">Även om det vanligt vis används på cmdlets och functions, `Get-Command` hämtar även skript, funktioner, alias och körbara filer.</span><span class="sxs-lookup"><span data-stu-id="ce613-157">Although it is typically used on cmdlets and functions, `Get-Command` also gets scripts, functions, aliases, and executable files.</span></span>

<span data-ttu-id="ce613-158">Kommandots utdata visar den särskilda vyn för **namn** egenskap svärdet för alias.</span><span class="sxs-lookup"><span data-stu-id="ce613-158">The output of the command shows the special view of the **Name** property value for aliases.</span></span> <span data-ttu-id="ce613-159">I vyn visas alias och det fullständiga kommando namnet.</span><span class="sxs-lookup"><span data-stu-id="ce613-159">The view shows the alias and the full command name.</span></span>

### <span data-ttu-id="ce613-160">Exempel 11: Hämta syntax från ett alias</span><span class="sxs-lookup"><span data-stu-id="ce613-160">Example 11: Get Syntax from an alias</span></span>

<span data-ttu-id="ce613-161">Det här exemplet visar hur du hämtar syntaxen tillsammans med standard namnet för ett alias.</span><span class="sxs-lookup"><span data-stu-id="ce613-161">This example shows how to get the syntax along with the standard name of an alias.</span></span>

<span data-ttu-id="ce613-162">Kommandots utdata visar det märkta aliaset med standard namnet följt av syntaxen.</span><span class="sxs-lookup"><span data-stu-id="ce613-162">The output of the command shows the labeled alias with the standard name, followed by the syntax.</span></span>

```powershell
Get-Command -Name dir -Syntax
```

```Output
dir (alias) -> Get-ChildItem

dir [[-Path] <string[]>] [[-Filter] <string>] [-Include <string[]>] [-Exclude <string[]>] [-Recurse] [-Depth <uint>] [-Force] [-Name] [-Attributes <FlagsExpression[FileAttributes]>] [-FollowSymlink] [-Directory] [-File] [-Hidden] [-ReadOnly] [-System] [<CommonParameters>]

dir [[-Filter] <string>] -LiteralPath <string[]> [-Include <string[]>] [-Exclude <string[]>] [-Recurse] [-Depth <uint>] [-Force] [-Name] [-Attributes <FlagsExpression[FileAttributes]>] [-FollowSymlink] [-Directory] [-File] [-Hidden] [-ReadOnly] [-System] [<CommonParameters>]
```

### <span data-ttu-id="ce613-163">Exempel 12: Hämta alla instanser av anteckningar-kommandot</span><span class="sxs-lookup"><span data-stu-id="ce613-163">Example 12: Get all instances of the Notepad command</span></span>

<span data-ttu-id="ce613-164">I det här exemplet används parametern **all** för `Get-Command` cmdleten för att visa alla instanser av `Notepad` kommandot på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="ce613-164">This example uses the **All** parameter of the `Get-Command` cmdlet to show all instances of the `Notepad` command on the local computer.</span></span>

```powershell
Get-Command Notepad -All | Format-Table CommandType, Name, Definition
```

```Output
CommandType     Name           Definition
-----------     ----           ----------
Application     notepad.exe    C:\WINDOWS\system32\notepad.exe
Application     NOTEPAD.EXE    C:\WINDOWS\NOTEPAD.EXE
```

<span data-ttu-id="ce613-165">Parametern **all** är användbar när det finns mer än ett kommando med samma namn i sessionen.</span><span class="sxs-lookup"><span data-stu-id="ce613-165">The **All** parameter is useful when there is more than one command with the same name in the session.</span></span>

<span data-ttu-id="ce613-166">Från och med Windows PowerShell 3,0, som standard, när sessionen innehåller flera kommandon med samma namn, `Get-Command` hämtas bara det kommando som körs när du skriver kommandots namn.</span><span class="sxs-lookup"><span data-stu-id="ce613-166">Beginning in Windows PowerShell 3.0, by default, when the session includes multiple commands with the same name, `Get-Command` gets only the command that runs when you type the command name.</span></span> <span data-ttu-id="ce613-167">Med parametern **all** `Get-Command` hämtar alla kommandon med det angivna namnet och returnerar dem i prioritetsordning för körning.</span><span class="sxs-lookup"><span data-stu-id="ce613-167">With the **All** parameter, `Get-Command` gets all commands with the specified name and returns them in execution precedence order.</span></span> <span data-ttu-id="ce613-168">Om du vill köra ett annat kommando än det första i listan, anger du den fullständiga sökvägen till kommandot.</span><span class="sxs-lookup"><span data-stu-id="ce613-168">To run a command other than the first one in the list, type the fully qualified path to the command.</span></span>

<span data-ttu-id="ce613-169">Mer information om kommando prioritet finns [about_Command_Precedence](About/about_Command_Precedence.md).</span><span class="sxs-lookup"><span data-stu-id="ce613-169">For more information about command precedence, see [about_Command_Precedence](About/about_Command_Precedence.md).</span></span>

### <span data-ttu-id="ce613-170">Exempel 13: Hämta namnet på en modul som innehåller en cmdlet</span><span class="sxs-lookup"><span data-stu-id="ce613-170">Example 13: Get the name of a module that contains a cmdlet</span></span>

<span data-ttu-id="ce613-171">Det här kommandot hämtar namnet på modulen där `Get-Date` cmdleten kommer.</span><span class="sxs-lookup"><span data-stu-id="ce613-171">This command gets the name of the module in which the `Get-Date` cmdlet originated.</span></span>
<span data-ttu-id="ce613-172">Kommandot använder egenskapen **Modulnamn** för alla kommandon.</span><span class="sxs-lookup"><span data-stu-id="ce613-172">The command uses the **ModuleName** property of all commands.</span></span>

```powershell
(Get-Command Get-Date).ModuleName
```

```Output
Microsoft.PowerShell.Utility
```

<span data-ttu-id="ce613-173">Det här kommando formatet fungerar med kommandon i PowerShell-moduler, även om de inte importeras till sessionen.</span><span class="sxs-lookup"><span data-stu-id="ce613-173">This command format works on commands in PowerShell modules, even if they are not imported into the session.</span></span>

### <span data-ttu-id="ce613-174">Exempel 14: Hämta cmdletar och funktioner som har en utdatatyp</span><span class="sxs-lookup"><span data-stu-id="ce613-174">Example 14: Get cmdlets and functions that have an output type</span></span>

```powershell
Get-Command -Type Cmdlet | Where-Object OutputType | Format-List -Property Name, OutputType
```

<span data-ttu-id="ce613-175">Det här kommandot hämtar de cmdletar och funktioner som har en utdatatyp och den typ av objekt som de returnerar.</span><span class="sxs-lookup"><span data-stu-id="ce613-175">This command gets the cmdlets and functions that have an output type and the type of objects that they return.</span></span>

<span data-ttu-id="ce613-176">Den första delen av kommandot hämtar alla cmdletar.</span><span class="sxs-lookup"><span data-stu-id="ce613-176">The first part of the command gets all cmdlets.</span></span> <span data-ttu-id="ce613-177">En pipeline-operator ( `|` ) skickar cmdletarna till `Where-Object` cmdleten, som bara väljer de där egenskapen **OutputType** är ifylld.</span><span class="sxs-lookup"><span data-stu-id="ce613-177">A pipeline operator (`|`) sends the cmdlets to the `Where-Object` cmdlet, which selects only the ones in which the **OutputType** property is populated.</span></span> <span data-ttu-id="ce613-178">En annan pipeline-operator skickar de valda cmdlet-objekten till `Format-List` cmdleten, som visar namn och Utdatatyp för varje cmdlet i en lista.</span><span class="sxs-lookup"><span data-stu-id="ce613-178">Another pipeline operator sends the selected cmdlet objects to the `Format-List` cmdlet, which displays the name and output type of each cmdlet in a list.</span></span>

<span data-ttu-id="ce613-179">Egenskapen **outputtype** för ett **CommandInfo** -objekt har ett värde som inte är null när cmdlet-koden definierar attributet **OutputType** för cmdleten.</span><span class="sxs-lookup"><span data-stu-id="ce613-179">The **OutputType** property of a **CommandInfo** object has a non-null value only when the cmdlet code defines the **OutputType** attribute for the cmdlet.</span></span>

### <span data-ttu-id="ce613-180">Exempel 15: Hämta cmdletar som tar en speciell objekt typ som inmatad</span><span class="sxs-lookup"><span data-stu-id="ce613-180">Example 15: Get cmdlets that take a specific object type as input</span></span>

```powershell
Get-Command -ParameterType (((Get-NetAdapter)[0]).PSTypeNames)
```

```Output
CommandType     Name                                               ModuleName
-----------     ----                                               ----------
Function        Disable-NetAdapter                                 NetAdapter
Function        Enable-NetAdapter                                  NetAdapter
Function        Rename-NetAdapter                                  NetAdapter
Function        Restart-NetAdapter                                 NetAdapter
Function        Set-NetAdapter                                     NetAdapter
```

<span data-ttu-id="ce613-181">Det här kommandot hittar cmdletar som tar net adapter-objekt som inmatade.</span><span class="sxs-lookup"><span data-stu-id="ce613-181">This command finds cmdlets that take net adapter objects as input.</span></span> <span data-ttu-id="ce613-182">Du kan använda det här kommando formatet för att hitta de cmdlet: ar som godkänner den typ av objekt som returneras av ett kommando.</span><span class="sxs-lookup"><span data-stu-id="ce613-182">You can use this command format to find the cmdlets that accept the type of objects that any command returns.</span></span>

<span data-ttu-id="ce613-183">Kommandot använder egenskapen **PSTypeNames** inre för alla objekt, som hämtar de typer som beskriver objektet.</span><span class="sxs-lookup"><span data-stu-id="ce613-183">The command uses the **PSTypeNames** intrinsic property of all objects, which gets the types that describe the object.</span></span> <span data-ttu-id="ce613-184">För att hämta egenskapen **PSTypeNames** för ett nät kort och inte egenskapen **PSTypeNames** för en uppsättning nätverkskort, använder kommandot mat ris notation för att hämta det första nätverkskortet som cmdleten returnerar.</span><span class="sxs-lookup"><span data-stu-id="ce613-184">To get the **PSTypeNames** property of a net adapter, and not the **PSTypeNames** property of a collection of net adapters, the command uses array notation to get the first net adapter that the cmdlet returns.</span></span>

### <span data-ttu-id="ce613-185">Exempel 16: Hämta kommandon med en Fuzzy-matchning</span><span class="sxs-lookup"><span data-stu-id="ce613-185">Example 16: Get commands using a fuzzy match</span></span>

<span data-ttu-id="ce613-186">I det här exemplet har namnet på kommandot avsiktligt ett skrivfel som "Get-commnd".</span><span class="sxs-lookup"><span data-stu-id="ce613-186">In this example, the name of the command deliberately has a typo as 'get-commnd'.</span></span>
<span data-ttu-id="ce613-187">Med hjälp av `-UseFuzzyMatching` växeln fastställde cmdleten att den bästa matchningen `Get-Command` följdes av andra inbyggda kommandon i systemet som liknar matchning.</span><span class="sxs-lookup"><span data-stu-id="ce613-187">Using the `-UseFuzzyMatching` switch, the cmdlet determined that the best match was `Get-Command` followed by other native commands on the system that were a similar match.</span></span>

```powershell
Get-Command get-commnd -UseFuzzyMatching
```

```Output
CommandType     Name                                               Version    Source
-----------     ----                                               -------    ------
Cmdlet          Get-Command                                        6.2.0.0    Microsoft.PowerShell.Core
Application     getconf                                            0.0.0.0    /usr/bin/getconf
Application     command                                            0.0.0.0    /usr/bin/command
```

## <span data-ttu-id="ce613-188">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="ce613-188">PARAMETERS</span></span>

### <span data-ttu-id="ce613-189">– Alla</span><span class="sxs-lookup"><span data-stu-id="ce613-189">-All</span></span>

<span data-ttu-id="ce613-190">Anger att denna cmdlet hämtar alla kommandon, inklusive kommandon av samma typ som har samma namn.</span><span class="sxs-lookup"><span data-stu-id="ce613-190">Indicates that this cmdlet gets all commands, including commands of the same type that have the same name.</span></span> <span data-ttu-id="ce613-191">Som standard `Get-Command` hämtar bara de kommandon som körs när du skriver kommandots namn.</span><span class="sxs-lookup"><span data-stu-id="ce613-191">By default, `Get-Command` gets only the commands that run when you type the command name.</span></span>

<span data-ttu-id="ce613-192">Mer information om metoden som PowerShell använder för att välja kommandot som ska köras när flera kommandon har samma namn finns i [about_Command_Precedence](About/about_Command_Precedence.md).</span><span class="sxs-lookup"><span data-stu-id="ce613-192">For more information about the method that PowerShell uses to select the command to run when multiple commands have the same name, see [about_Command_Precedence](About/about_Command_Precedence.md).</span></span>
<span data-ttu-id="ce613-193">Information om moduler-kvalificerade kommando namn och körning av kommandon som inte körs som standard på grund av en namn konflikt finns i [about_Modules](About/about_Modules.md).</span><span class="sxs-lookup"><span data-stu-id="ce613-193">For information about module-qualified command names and running commands that do not run by default because of a name conflict, see [about_Modules](About/about_Modules.md).</span></span>

<span data-ttu-id="ce613-194">Den här parametern introducerades i Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="ce613-194">This parameter was introduced in Windows PowerShell 3.0.</span></span>

<span data-ttu-id="ce613-195">I Windows PowerShell 2,0 `Get-Command` hämtar alla kommandon som standard.</span><span class="sxs-lookup"><span data-stu-id="ce613-195">In Windows PowerShell 2.0, `Get-Command` gets all commands by default.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="ce613-196">– Argument List</span><span class="sxs-lookup"><span data-stu-id="ce613-196">-ArgumentList</span></span>

<span data-ttu-id="ce613-197">Anger en matris med argument.</span><span class="sxs-lookup"><span data-stu-id="ce613-197">Specifies an array of arguments.</span></span> <span data-ttu-id="ce613-198">Denna cmdlet hämtar information om en cmdlet eller funktion när den används med de angivna parametrarna ("argument").</span><span class="sxs-lookup"><span data-stu-id="ce613-198">This cmdlet gets information about a cmdlet or function when it is used with the specified parameters ("arguments").</span></span> <span data-ttu-id="ce613-199">Aliaset för **argument List** är **argument**.</span><span class="sxs-lookup"><span data-stu-id="ce613-199">The alias for **ArgumentList** is **Args**.</span></span>

<span data-ttu-id="ce613-200">Om du vill identifiera dynamiska parametrar som bara är tillgängliga när vissa andra parametrar används ställer du in värdet för **argument List** på de parametrar som utlöser de dynamiska parametrarna.</span><span class="sxs-lookup"><span data-stu-id="ce613-200">To detect dynamic parameters that are available only when certain other parameters are used, set the value of **ArgumentList** to the parameters that trigger the dynamic parameters.</span></span>

<span data-ttu-id="ce613-201">För att identifiera de dynamiska parametrar som en provider lägger till i en cmdlet, ange värdet för parametern **argument List** till en sökväg i leverantörs enheten, till exempel WSMan:, HKLM: eller cert:.</span><span class="sxs-lookup"><span data-stu-id="ce613-201">To detect the dynamic parameters that a provider adds to a cmdlet, set the value of the **ArgumentList** parameter to a path in the provider drive, such as WSMan:, HKLM:, or Cert:.</span></span> <span data-ttu-id="ce613-202">När kommandot är en PowerShell-Provider-cmdlet anger du bara en sökväg i varje kommando.</span><span class="sxs-lookup"><span data-stu-id="ce613-202">When the command is a PowerShell provider cmdlet, enter only one path in each command.</span></span> <span data-ttu-id="ce613-203">Providerns cmdlets returnerar bara dynamiska parametrar för den första sökvägen till värdet för **argument List**.</span><span class="sxs-lookup"><span data-stu-id="ce613-203">The provider cmdlets return only the dynamic parameters for the first path the value of **ArgumentList**.</span></span> <span data-ttu-id="ce613-204">Information om Provider-cmdletar finns i [about_Providers](About/about_Providers.md).</span><span class="sxs-lookup"><span data-stu-id="ce613-204">For information about the provider cmdlets, see [about_Providers](About/about_Providers.md).</span></span>

```yaml
Type: System.Object[]
Parameter Sets: (All)
Aliases: Args

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="ce613-205">-CommandType</span><span class="sxs-lookup"><span data-stu-id="ce613-205">-CommandType</span></span>

<span data-ttu-id="ce613-206">Anger vilka typer av kommandon som denna cmdlet hämtar.</span><span class="sxs-lookup"><span data-stu-id="ce613-206">Specifies the types of commands that this cmdlet gets.</span></span> <span data-ttu-id="ce613-207">Ange en eller flera kommando typer.</span><span class="sxs-lookup"><span data-stu-id="ce613-207">Enter one or more command types.</span></span> <span data-ttu-id="ce613-208">Använd **CommandType** eller dess alias och **Skriv**.</span><span class="sxs-lookup"><span data-stu-id="ce613-208">Use **CommandType** or its alias, **Type**.</span></span> <span data-ttu-id="ce613-209">Som standard `Get-Command` hämtar alla cmdletar, funktioner och alias.</span><span class="sxs-lookup"><span data-stu-id="ce613-209">By default, `Get-Command` gets all cmdlets, functions, and aliases.</span></span>

<span data-ttu-id="ce613-210">De acceptabla värdena för den här parametern är:</span><span class="sxs-lookup"><span data-stu-id="ce613-210">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="ce613-211">Aliasuppsättning.</span><span class="sxs-lookup"><span data-stu-id="ce613-211">Alias.</span></span> <span data-ttu-id="ce613-212">Hämtar alias för alla PowerShell-kommandon.</span><span class="sxs-lookup"><span data-stu-id="ce613-212">Gets the aliases of all PowerShell commands.</span></span> <span data-ttu-id="ce613-213">Mer information finns i [about_Aliases](About/about_Aliases.md).</span><span class="sxs-lookup"><span data-stu-id="ce613-213">For more information, see [about_Aliases](About/about_Aliases.md).</span></span>
- <span data-ttu-id="ce613-214">Vissa.</span><span class="sxs-lookup"><span data-stu-id="ce613-214">All.</span></span> <span data-ttu-id="ce613-215">Hämtar alla kommando typer.</span><span class="sxs-lookup"><span data-stu-id="ce613-215">Gets all command types.</span></span> <span data-ttu-id="ce613-216">Detta parameter värde motsvarar `Get-Command *` .</span><span class="sxs-lookup"><span data-stu-id="ce613-216">This parameter value is the equivalent of `Get-Command *`.</span></span>
- <span data-ttu-id="ce613-217">Applicering.</span><span class="sxs-lookup"><span data-stu-id="ce613-217">Application.</span></span> <span data-ttu-id="ce613-218">Hämtar icke-PowerShell-filer i sökvägar som anges i miljövariabeln **Path** ($env:p ökväg), inklusive. txt-,. exe-och. dll-filer.</span><span class="sxs-lookup"><span data-stu-id="ce613-218">Gets non-PowerShell files in paths listed in the **Path** environment variable ($env:path), including .txt, .exe, and .dll files.</span></span> <span data-ttu-id="ce613-219">Mer information om **Path** -miljövariabeln finns about_Environment_Variables.</span><span class="sxs-lookup"><span data-stu-id="ce613-219">For more information about the **Path** environment variable, see about_Environment_Variables.</span></span>
- <span data-ttu-id="ce613-220">Kommandon.</span><span class="sxs-lookup"><span data-stu-id="ce613-220">Cmdlet.</span></span> <span data-ttu-id="ce613-221">Hämtar alla cmdletar.</span><span class="sxs-lookup"><span data-stu-id="ce613-221">Gets all cmdlets.</span></span>
- <span data-ttu-id="ce613-222">ExternalScript.</span><span class="sxs-lookup"><span data-stu-id="ce613-222">ExternalScript.</span></span> <span data-ttu-id="ce613-223">Hämtar alla. ps1-filer i Sök vägarna som anges i miljövariabeln **Path** ($env:p ökväg).</span><span class="sxs-lookup"><span data-stu-id="ce613-223">Gets all .ps1 files in the paths listed in the **Path** environment variable ($env:path).</span></span>
- <span data-ttu-id="ce613-224">Filter och funktion.</span><span class="sxs-lookup"><span data-stu-id="ce613-224">Filter and Function.</span></span> <span data-ttu-id="ce613-225">Hämtar alla PowerShell-avancerade och enkla funktioner och filter.</span><span class="sxs-lookup"><span data-stu-id="ce613-225">Gets all PowerShell advanced and simple functions and filters.</span></span>
- <span data-ttu-id="ce613-226">Över.</span><span class="sxs-lookup"><span data-stu-id="ce613-226">Script.</span></span> <span data-ttu-id="ce613-227">Hämtar alla skript block.</span><span class="sxs-lookup"><span data-stu-id="ce613-227">Gets all script blocks.</span></span> <span data-ttu-id="ce613-228">Använd ExternalScript-värdet för att hämta PowerShell-skript (. ps1-filer).</span><span class="sxs-lookup"><span data-stu-id="ce613-228">To get PowerShell scripts (.ps1 files), use the ExternalScript value.</span></span>

```yaml
Type: System.Management.Automation.CommandTypes
Parameter Sets: AllCommandSet
Aliases: Type
Accepted values: Alias, Function, Filter, Cmdlet, ExternalScript, Application, Script, Workflow, Configuration, All

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="ce613-229">-FullyQualifiedModule</span><span class="sxs-lookup"><span data-stu-id="ce613-229">-FullyQualifiedModule</span></span>

<span data-ttu-id="ce613-230">Anger moduler med namn som anges i form av **ModuleSpecification** -objekt, som beskrivs i avsnittet **anmärkningar** i [ModuleSpecification-konstruktorn (hash)](/dotnet/api/microsoft.powershell.commands.modulespecification.-ctor?view=powershellsdk-1.1.0#Microsoft_PowerShell_Commands_ModuleSpecification__ctor_System_Collections_Hashtable_).</span><span class="sxs-lookup"><span data-stu-id="ce613-230">Specifies modules with names that are specified in the form of **ModuleSpecification** objects, described in the **Remarks** section of [ModuleSpecification Constructor (Hashtable)](/dotnet/api/microsoft.powershell.commands.modulespecification.-ctor?view=powershellsdk-1.1.0#Microsoft_PowerShell_Commands_ModuleSpecification__ctor_System_Collections_Hashtable_).</span></span>
<span data-ttu-id="ce613-231">**FullyQualifiedModule** -parametern accepterar till exempel ett modulnamn som anges i något av följande format:</span><span class="sxs-lookup"><span data-stu-id="ce613-231">For example, the **FullyQualifiedModule** parameter accepts a module name that is specified in one of the following formats:</span></span>

- `@{ModuleName = "modulename"; ModuleVersion = "version_number"}`
- `@{ModuleName = "modulename"; ModuleVersion = "version_number"; Guid = "GUID"}`

<span data-ttu-id="ce613-232">**Modulnamn** och **ModuleVersion** krävs, men **GUID** är valfritt.</span><span class="sxs-lookup"><span data-stu-id="ce613-232">**ModuleName** and **ModuleVersion** are required, but **Guid** is optional.</span></span>

<span data-ttu-id="ce613-233">Det går inte att ange parametern **FullyQualifiedModule** i samma kommando som en **modul** -parameter.</span><span class="sxs-lookup"><span data-stu-id="ce613-233">You cannot specify the **FullyQualifiedModule** parameter in the same command as a **Module** parameter.</span></span> <span data-ttu-id="ce613-234">De två parametrarna kan inte anges samtidigt.</span><span class="sxs-lookup"><span data-stu-id="ce613-234">The two parameters are mutually exclusive.</span></span>

```yaml
Type: Microsoft.PowerShell.Commands.ModuleSpecification[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="ce613-235">-ListImported</span><span class="sxs-lookup"><span data-stu-id="ce613-235">-ListImported</span></span>

<span data-ttu-id="ce613-236">Anger att denna cmdlet endast hämtar kommandon i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="ce613-236">Indicates that this cmdlet gets only commands in the current session.</span></span>

<span data-ttu-id="ce613-237">Från och med PowerShell 3,0 hämtar som standard `Get-Command` alla installerade kommandon, inklusive, men inte begränsat till, kommandona i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="ce613-237">Starting in PowerShell 3.0, by default, `Get-Command` gets all installed commands, including, but not limited to, the commands in the current session.</span></span> <span data-ttu-id="ce613-238">I PowerShell 2,0 får du bara kommandon i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="ce613-238">In PowerShell 2.0, it gets only commands in the current session.</span></span>

<span data-ttu-id="ce613-239">Den här parametern introducerades i Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="ce613-239">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="ce613-240">– Modul</span><span class="sxs-lookup"><span data-stu-id="ce613-240">-Module</span></span>

<span data-ttu-id="ce613-241">Anger en matris med moduler.</span><span class="sxs-lookup"><span data-stu-id="ce613-241">Specifies an array of modules.</span></span> <span data-ttu-id="ce613-242">Denna cmdlet hämtar de kommandon som kom från de angivna modulerna.</span><span class="sxs-lookup"><span data-stu-id="ce613-242">This cmdlet gets the commands that came from the specified modules.</span></span>
<span data-ttu-id="ce613-243">Ange namnen på modulerna eller modulens objekt.</span><span class="sxs-lookup"><span data-stu-id="ce613-243">Enter the names of modules or module objects.</span></span>

<span data-ttu-id="ce613-244">Den här parametern använder sträng värden, men värdet för den här parametern kan också vara ett **PSModuleInfo** -objekt, till exempel de objekt `Get-Module` som `Import-PSSession` cmdletarna och returnerar.</span><span class="sxs-lookup"><span data-stu-id="ce613-244">This parameter takes string values, but the value of this parameter can also be a **PSModuleInfo** object, such as the objects that the `Get-Module` and `Import-PSSession` cmdlets return.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: PSSnapin

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### <span data-ttu-id="ce613-245">-Name</span><span class="sxs-lookup"><span data-stu-id="ce613-245">-Name</span></span>

<span data-ttu-id="ce613-246">Anger en matris med namn.</span><span class="sxs-lookup"><span data-stu-id="ce613-246">Specifies an array of names.</span></span> <span data-ttu-id="ce613-247">Denna cmdlet hämtar endast kommandon med det angivna namnet.</span><span class="sxs-lookup"><span data-stu-id="ce613-247">This cmdlet gets only commands that have the specified name.</span></span> <span data-ttu-id="ce613-248">Ange ett namn eller namn mönster.</span><span class="sxs-lookup"><span data-stu-id="ce613-248">Enter a name or name pattern.</span></span> <span data-ttu-id="ce613-249">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="ce613-249">Wildcard characters are permitted.</span></span>

<span data-ttu-id="ce613-250">Om du vill hämta kommandon med samma namn använder du parametern **all** .</span><span class="sxs-lookup"><span data-stu-id="ce613-250">To get commands that have the same name, use the **All** parameter.</span></span> <span data-ttu-id="ce613-251">När två kommandon har samma namn, hämtas som standard `Get-Command` kommandot som körs när du skriver kommandots namn.</span><span class="sxs-lookup"><span data-stu-id="ce613-251">When two commands have the same name, by default, `Get-Command` gets the command that runs when you type the command name.</span></span>

```yaml
Type: System.String[]
Parameter Sets: AllCommandSet
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### <span data-ttu-id="ce613-252">-Substantiv</span><span class="sxs-lookup"><span data-stu-id="ce613-252">-Noun</span></span>

<span data-ttu-id="ce613-253">Anger en matris med kommando substantiv.</span><span class="sxs-lookup"><span data-stu-id="ce613-253">Specifies an array of command nouns.</span></span> <span data-ttu-id="ce613-254">Denna cmdlet hämtar kommandon, som innehåller cmdlets, Functions och alias, som har namn som innehåller angivet substantiv.</span><span class="sxs-lookup"><span data-stu-id="ce613-254">This cmdlet gets commands, which include cmdlets, functions, and aliases, that have names that include the specified noun.</span></span> <span data-ttu-id="ce613-255">Ange ett eller flera Substantiv-eller Substantiv-mönster.</span><span class="sxs-lookup"><span data-stu-id="ce613-255">Enter one or more nouns or noun patterns.</span></span> <span data-ttu-id="ce613-256">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="ce613-256">Wildcard characters are permitted.</span></span>

```yaml
Type: System.String[]
Parameter Sets: CmdletSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### <span data-ttu-id="ce613-257">– ParameterName</span><span class="sxs-lookup"><span data-stu-id="ce613-257">-ParameterName</span></span>

<span data-ttu-id="ce613-258">Anger en matris med parameter namn.</span><span class="sxs-lookup"><span data-stu-id="ce613-258">Specifies an array of parameter names.</span></span> <span data-ttu-id="ce613-259">Denna cmdlet hämtar kommandon i sessionen som har de angivna parametrarna.</span><span class="sxs-lookup"><span data-stu-id="ce613-259">This cmdlet gets commands in the session that have the specified parameters.</span></span> <span data-ttu-id="ce613-260">Ange parameter namn eller parameter-alias.</span><span class="sxs-lookup"><span data-stu-id="ce613-260">Enter parameter names or parameter aliases.</span></span> <span data-ttu-id="ce613-261">Jokertecken stöds.</span><span class="sxs-lookup"><span data-stu-id="ce613-261">Wildcard characters are supported.</span></span>

<span data-ttu-id="ce613-262">Parametrarna **ParameterName** och **ParameterType** söker bara efter kommandon i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="ce613-262">The **ParameterName** and **ParameterType** parameters search only commands in the current session.</span></span>

<span data-ttu-id="ce613-263">Den här parametern introducerades i Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="ce613-263">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="ce613-264">– ParameterType</span><span class="sxs-lookup"><span data-stu-id="ce613-264">-ParameterType</span></span>

<span data-ttu-id="ce613-265">Anger en matris med parameter namn.</span><span class="sxs-lookup"><span data-stu-id="ce613-265">Specifies an array of parameter names.</span></span> <span data-ttu-id="ce613-266">Denna cmdlet hämtar kommandon i sessionen som har parametrar av den angivna typen.</span><span class="sxs-lookup"><span data-stu-id="ce613-266">This cmdlet gets commands in the session that have parameters of the specified type.</span></span> <span data-ttu-id="ce613-267">Ange det fullständiga namnet eller del namnet för en parameter typ.</span><span class="sxs-lookup"><span data-stu-id="ce613-267">Enter the full name or partial name of a parameter type.</span></span> <span data-ttu-id="ce613-268">Jokertecken stöds.</span><span class="sxs-lookup"><span data-stu-id="ce613-268">Wildcard characters are supported.</span></span>

<span data-ttu-id="ce613-269">Parametrarna **ParameterName** och **ParameterType** söker bara efter kommandon i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="ce613-269">The **ParameterName** and **ParameterType** parameters search only commands in the current session.</span></span>

<span data-ttu-id="ce613-270">Den här parametern introducerades i Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="ce613-270">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.PSTypeName[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="ce613-271">-ShowCommandInfo</span><span class="sxs-lookup"><span data-stu-id="ce613-271">-ShowCommandInfo</span></span>

<span data-ttu-id="ce613-272">Anger att denna cmdlet visar kommando information.</span><span class="sxs-lookup"><span data-stu-id="ce613-272">Indicates that this cmdlet displays command information.</span></span>

<span data-ttu-id="ce613-273">Den här parametern introducerades i Windows PowerShell 5,0.</span><span class="sxs-lookup"><span data-stu-id="ce613-273">This parameter was introduced in Windows PowerShell 5.0.</span></span>

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

### <span data-ttu-id="ce613-274">-Syntax</span><span class="sxs-lookup"><span data-stu-id="ce613-274">-Syntax</span></span>

<span data-ttu-id="ce613-275">Anger att denna cmdlet endast hämtar följande angivna data om kommandot:</span><span class="sxs-lookup"><span data-stu-id="ce613-275">Indicates that this cmdlet gets only the following specified data about the command:</span></span>

- <span data-ttu-id="ce613-276">Alias.</span><span class="sxs-lookup"><span data-stu-id="ce613-276">Aliases.</span></span> <span data-ttu-id="ce613-277">Hämtar standard namn och syntax.</span><span class="sxs-lookup"><span data-stu-id="ce613-277">Gets the standard name and syntax.</span></span>
- <span data-ttu-id="ce613-278">Cmdletar.</span><span class="sxs-lookup"><span data-stu-id="ce613-278">Cmdlets.</span></span> <span data-ttu-id="ce613-279">Hämtar syntaxen.</span><span class="sxs-lookup"><span data-stu-id="ce613-279">Gets the syntax.</span></span>
- <span data-ttu-id="ce613-280">Funktioner och filter.</span><span class="sxs-lookup"><span data-stu-id="ce613-280">Functions and filters.</span></span> <span data-ttu-id="ce613-281">Hämtar funktions definitionen.</span><span class="sxs-lookup"><span data-stu-id="ce613-281">Gets the function definition.</span></span>
- <span data-ttu-id="ce613-282">Skript och program eller filer.</span><span class="sxs-lookup"><span data-stu-id="ce613-282">Scripts and applications or files.</span></span> <span data-ttu-id="ce613-283">Hämtar sökvägen och fil namnet.</span><span class="sxs-lookup"><span data-stu-id="ce613-283">Gets the path and filename.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="ce613-284">– TotalCount</span><span class="sxs-lookup"><span data-stu-id="ce613-284">-TotalCount</span></span>

<span data-ttu-id="ce613-285">Anger antalet kommandon som ska hämtas.</span><span class="sxs-lookup"><span data-stu-id="ce613-285">Specifies the number of commands to get.</span></span> <span data-ttu-id="ce613-286">Du kan använda den här parametern för att begränsa utdata från ett kommando.</span><span class="sxs-lookup"><span data-stu-id="ce613-286">You can use this parameter to limit the output of a command.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="ce613-287">-UseAbbreviationExpansion</span><span class="sxs-lookup"><span data-stu-id="ce613-287">-UseAbbreviationExpansion</span></span>

<span data-ttu-id="ce613-288">Anger att använder matchande tecken i kommandot för att hitta med versaler i ett kommando.</span><span class="sxs-lookup"><span data-stu-id="ce613-288">Indicates using matching of the characters in the command to find with uppercase characters in a command.</span></span> <span data-ttu-id="ce613-289">Motsvarar till exempel `i-psdf` `Import-PowerShellDataFile` det som var och en av de tecken som ska hittas matchar ett versalt tecken i resultatet.</span><span class="sxs-lookup"><span data-stu-id="ce613-289">For example, `i-psdf` would match `Import-PowerShellDataFile` as each of the characters to find matches an uppercase character in the result.</span></span> <span data-ttu-id="ce613-290">När du använder den här typen av matchning kommer jokertecken att resultera i inga matchningar.</span><span class="sxs-lookup"><span data-stu-id="ce613-290">When using this type of match, any wildcards will result in no matches.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: AllCommandSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="ce613-291">-UseFuzzyMatching</span><span class="sxs-lookup"><span data-stu-id="ce613-291">-UseFuzzyMatching</span></span>

<span data-ttu-id="ce613-292">Anger att en partiell matchnings algoritm används vid sökning av kommandon.</span><span class="sxs-lookup"><span data-stu-id="ce613-292">Indicates using a fuzzy matching algorithm when finding commands.</span></span> <span data-ttu-id="ce613-293">Ordningen på utdata är från närmaste matchning till minst sannolik matchning.</span><span class="sxs-lookup"><span data-stu-id="ce613-293">The order of the output is from closest match to least likely match.</span></span> <span data-ttu-id="ce613-294">Jokertecken bör inte användas med en Fuzzy-matchning eftersom det kommer att försöka matcha kommandon som kan innehålla jokertecknen.</span><span class="sxs-lookup"><span data-stu-id="ce613-294">Wildcards should not be used with fuzzy matching as it will attempt to match commands that may contain those wildcard characters.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: AllCommandSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="ce613-295">-Verb</span><span class="sxs-lookup"><span data-stu-id="ce613-295">-Verb</span></span>

<span data-ttu-id="ce613-296">Anger en matris med kommando-verb.</span><span class="sxs-lookup"><span data-stu-id="ce613-296">Specifies an array of command verbs.</span></span> <span data-ttu-id="ce613-297">Denna cmdlet hämtar kommandon, som innehåller cmdlets, Functions och alias, som har namn som innehåller det angivna verbet.</span><span class="sxs-lookup"><span data-stu-id="ce613-297">This cmdlet gets commands, which include cmdlets, functions, and aliases, that have names that include the specified verb.</span></span> <span data-ttu-id="ce613-298">Ange ett eller flera verb eller verb-mönster.</span><span class="sxs-lookup"><span data-stu-id="ce613-298">Enter one or more verbs or verb patterns.</span></span> <span data-ttu-id="ce613-299">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="ce613-299">Wildcard characters are permitted.</span></span>

```yaml
Type: System.String[]
Parameter Sets: CmdletSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### <span data-ttu-id="ce613-300">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="ce613-300">CommonParameters</span></span>

<span data-ttu-id="ce613-301">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="ce613-301">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="ce613-302">Mer information finns i [about_CommonParameters](About/about_CommonParameters.md).</span><span class="sxs-lookup"><span data-stu-id="ce613-302">For more information, see [about_CommonParameters](About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="ce613-303">INDATA</span><span class="sxs-lookup"><span data-stu-id="ce613-303">INPUTS</span></span>

### <span data-ttu-id="ce613-304">System. String</span><span class="sxs-lookup"><span data-stu-id="ce613-304">System.String</span></span>

<span data-ttu-id="ce613-305">Du kan skicka pipe-kommando namn till denna cmdlet.</span><span class="sxs-lookup"><span data-stu-id="ce613-305">You can pipe command names to this cmdlet.</span></span>

## <span data-ttu-id="ce613-306">UTDATA</span><span class="sxs-lookup"><span data-stu-id="ce613-306">OUTPUTS</span></span>

### <span data-ttu-id="ce613-307">System. Management. Automation. CommandInfo</span><span class="sxs-lookup"><span data-stu-id="ce613-307">System.Management.Automation.CommandInfo</span></span>

<span data-ttu-id="ce613-308">Denna cmdlet returnerar objekt som härletts från klassen **CommandInfo** .</span><span class="sxs-lookup"><span data-stu-id="ce613-308">This cmdlet returns objects derived from the **CommandInfo** class.</span></span> <span data-ttu-id="ce613-309">Vilken typ av objekt som returneras beror på vilken typ av kommando som `Get-Command` hämtas.</span><span class="sxs-lookup"><span data-stu-id="ce613-309">The type of object that is returned depends on the type of command that `Get-Command` gets.</span></span>

### <span data-ttu-id="ce613-310">System. Management. Automation. AliasInfo</span><span class="sxs-lookup"><span data-stu-id="ce613-310">System.Management.Automation.AliasInfo</span></span>

<span data-ttu-id="ce613-311">Representerar alias.</span><span class="sxs-lookup"><span data-stu-id="ce613-311">Represents aliases.</span></span>

### <span data-ttu-id="ce613-312">System. Management. Automation. ApplicationInfo</span><span class="sxs-lookup"><span data-stu-id="ce613-312">System.Management.Automation.ApplicationInfo</span></span>

<span data-ttu-id="ce613-313">Representerar program och filer.</span><span class="sxs-lookup"><span data-stu-id="ce613-313">Represents applications and files.</span></span>

### <span data-ttu-id="ce613-314">System. Management. Automation. CmdletInfo</span><span class="sxs-lookup"><span data-stu-id="ce613-314">System.Management.Automation.CmdletInfo</span></span>

<span data-ttu-id="ce613-315">Representerar cmdletar.</span><span class="sxs-lookup"><span data-stu-id="ce613-315">Represents cmdlets.</span></span>

### <span data-ttu-id="ce613-316">System. Management. Automation. FunctionInfo</span><span class="sxs-lookup"><span data-stu-id="ce613-316">System.Management.Automation.FunctionInfo</span></span>

<span data-ttu-id="ce613-317">Representerar funktioner och filter.</span><span class="sxs-lookup"><span data-stu-id="ce613-317">Represents functions and filters.</span></span>

## <span data-ttu-id="ce613-318">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="ce613-318">NOTES</span></span>

* <span data-ttu-id="ce613-319">Om mer än ett kommando med samma namn är tillgängligt för sessionen, `Get-Command` returnerar kommandot som körs när du skriver kommandots namn.</span><span class="sxs-lookup"><span data-stu-id="ce613-319">When more than one command that has the same name is available to the session, `Get-Command` returns the command that runs when you type the command name.</span></span> <span data-ttu-id="ce613-320">Om du vill hämta kommandon med samma namn, som anges i körnings ordning, använder du parametern **all** .</span><span class="sxs-lookup"><span data-stu-id="ce613-320">To get commands that have the same name, listed in run order, use the **All** parameter.</span></span> <span data-ttu-id="ce613-321">Mer information finns i [about_Command_Precedence](../Microsoft.PowerShell.Core/About/about_Command_Precedence.md).</span><span class="sxs-lookup"><span data-stu-id="ce613-321">For more information, see [about_Command_Precedence](../Microsoft.PowerShell.Core/About/about_Command_Precedence.md).</span></span>
* <span data-ttu-id="ce613-322">När en modul importeras automatiskt är det samma sak som att använda `Import-Module` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="ce613-322">When a module is imported automatically, the effect is the same as using the `Import-Module` cmdlet.</span></span> <span data-ttu-id="ce613-323">Modulen kan lägga till kommandon, typer och formatering av filer och köra skript i sessionen.</span><span class="sxs-lookup"><span data-stu-id="ce613-323">The module can add commands, types and formatting files, and run scripts in the session.</span></span>
  <span data-ttu-id="ce613-324">Om du vill aktivera, inaktivera och konfigurera automatisk import av moduler använder du `$PSModuleAutoLoadingPreference` Preference-variabeln.</span><span class="sxs-lookup"><span data-stu-id="ce613-324">To enable, disable, and configuration automatic importing of modules, use the `$PSModuleAutoLoadingPreference` preference variable.</span></span> <span data-ttu-id="ce613-325">Mer information finns i [about_Preference_Variables](../Microsoft.PowerShell.Core/About/about_Preference_Variables.md).</span><span class="sxs-lookup"><span data-stu-id="ce613-325">For more information, see [about_Preference_Variables](../Microsoft.PowerShell.Core/About/about_Preference_Variables.md).</span></span>

## <span data-ttu-id="ce613-326">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="ce613-326">RELATED LINKS</span></span>

[<span data-ttu-id="ce613-327">Exportera – PSSession</span><span class="sxs-lookup"><span data-stu-id="ce613-327">Export-PSSession</span></span>](../Microsoft.PowerShell.Utility/Export-PSSession.md)

[<span data-ttu-id="ce613-328">Get – hjälp</span><span class="sxs-lookup"><span data-stu-id="ce613-328">Get-Help</span></span>](Get-Help.md)

[<span data-ttu-id="ce613-329">Hämta medlem</span><span class="sxs-lookup"><span data-stu-id="ce613-329">Get-Member</span></span>](../Microsoft.PowerShell.Utility/Get-Member.md)

[<span data-ttu-id="ce613-330">Get-PSDrive</span><span class="sxs-lookup"><span data-stu-id="ce613-330">Get-PSDrive</span></span>](../Microsoft.PowerShell.Management/Get-PSDrive.md)

[<span data-ttu-id="ce613-331">Importera – PSSession</span><span class="sxs-lookup"><span data-stu-id="ce613-331">Import-PSSession</span></span>](../Microsoft.PowerShell.Utility/Import-PSSession.md)

[<span data-ttu-id="ce613-332">about_Command_Precedence</span><span class="sxs-lookup"><span data-stu-id="ce613-332">about_Command_Precedence</span></span>](About/about_Command_Precedence.md)

