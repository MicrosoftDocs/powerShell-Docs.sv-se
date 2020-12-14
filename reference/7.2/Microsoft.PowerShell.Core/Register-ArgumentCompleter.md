---
external help file: System.Management.Automation.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 05/20/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/register-argumentcompleter?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Register-ArgumentCompleter
ms.openlocfilehash: 6044b27c0d339d62bd6e75fd2fee27eb65a89b79
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94709985"
---
# <span data-ttu-id="55490-102">Register-ArgumentCompleter</span><span class="sxs-lookup"><span data-stu-id="55490-102">Register-ArgumentCompleter</span></span>

## <span data-ttu-id="55490-103">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="55490-103">SYNOPSIS</span></span>

<span data-ttu-id="55490-104">Registrerar en anpassad argument slutförare.</span><span class="sxs-lookup"><span data-stu-id="55490-104">Registers a custom argument completer.</span></span>

## <span data-ttu-id="55490-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="55490-105">SYNTAX</span></span>

### <span data-ttu-id="55490-106">NativeSet</span><span class="sxs-lookup"><span data-stu-id="55490-106">NativeSet</span></span>

```
Register-ArgumentCompleter -CommandName <String[]> -ScriptBlock <ScriptBlock> [-Native]
 [<CommonParameters>]
```

### <span data-ttu-id="55490-107">PowerShellSet</span><span class="sxs-lookup"><span data-stu-id="55490-107">PowerShellSet</span></span>

```
Register-ArgumentCompleter [-CommandName <String[]>] -ParameterName <String>
 -ScriptBlock <ScriptBlock> [<CommonParameters>]
```

## <span data-ttu-id="55490-108">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="55490-108">DESCRIPTION</span></span>

<span data-ttu-id="55490-109">`Register-ArgumentCompleter`Cmdleten registrerar en anpassad argument slutförare.</span><span class="sxs-lookup"><span data-stu-id="55490-109">The `Register-ArgumentCompleter` cmdlet registers a custom argument completer.</span></span> <span data-ttu-id="55490-110">Med en argument slutförd kan du ange dynamisk ifyllning av flikar, vid körning för alla kommandon som du anger.</span><span class="sxs-lookup"><span data-stu-id="55490-110">An argument completer allows you to provide dynamic tab completion, at run time for any command that you specify.</span></span>

## <span data-ttu-id="55490-111">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="55490-111">EXAMPLES</span></span>

### <span data-ttu-id="55490-112">Exempel 1: registrera en anpassad argument slutförare</span><span class="sxs-lookup"><span data-stu-id="55490-112">Example 1: Register a custom argument completer</span></span>

<span data-ttu-id="55490-113">I följande exempel registreras en argument slutförre för cmdletens **ID-** parameter `Set-TimeZone` .</span><span class="sxs-lookup"><span data-stu-id="55490-113">The following example registers an argument completer for the **Id** parameter of the `Set-TimeZone` cmdlet.</span></span>

```powershell
$scriptBlock = {
    param($commandName, $parameterName, $wordToComplete, $commandAst, $fakeBoundParameters)

    (Get-TimeZone -ListAvailable).Id | Where-Object {
        $_ -like "$wordToComplete*"
    } | ForEach-Object {
          "'$_'"
    }
}
Register-ArgumentCompleter -CommandName Set-TimeZone -ParameterName Id -ScriptBlock $scriptBlock
```

<span data-ttu-id="55490-114">Det första kommandot skapar ett-skript block som tar de nödvändiga parametrarna som skickas i när användaren trycker på <kbd>fliken</kbd>. Mer information finns i Beskrivning av **script block** -parametern.</span><span class="sxs-lookup"><span data-stu-id="55490-114">The first command creates a script block which takes the required parameters which are passed in when the user presses <kbd>Tab</kbd>. For more information, see the **ScriptBlock** parameter description.</span></span>

<span data-ttu-id="55490-115">I-skript blocket hämtas de tillgängliga värdena för **ID** med hjälp av `Get-TimeZone` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="55490-115">Within the script block, the available values for **Id** are retrieved using the `Get-TimeZone` cmdlet.</span></span> <span data-ttu-id="55490-116">Egenskapen **ID** för varje tidszon är skickas till `Where-Object` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="55490-116">The **Id** property for each Time Zone is piped to the `Where-Object` cmdlet.</span></span> <span data-ttu-id="55490-117">`Where-Object`Cmdlet: en filtrerar bort alla ID: n som inte börjar med värdet som anges av `$wordToComplete` , som representerar texten som användaren skrev innan de tryckte på <kbd>fliken</kbd>. Filtrerade ID: n är skickas till `For-EachObject` cmdleten som innesluter varje värde i citationstecken, om värdet innehåller blank steg.</span><span class="sxs-lookup"><span data-stu-id="55490-117">The `Where-Object` cmdlet filters out any ids that do not start with the value provided by `$wordToComplete`, which represents the text the user typed before they pressed <kbd>Tab</kbd>. The filtered ids are piped to the `For-EachObject` cmdlet which encloses each value in quotes, should the value contain spaces.</span></span>

<span data-ttu-id="55490-118">Det andra kommandot registrerar argumentet completer genom att skicka script block, **ParameterName** **-ID** och **commandname** `Set-TimeZone` .</span><span class="sxs-lookup"><span data-stu-id="55490-118">The second command registers the argument completer by passing the scriptblock, the **ParameterName** **Id** and the **CommandName** `Set-TimeZone`.</span></span>

### <span data-ttu-id="55490-119">Exempel 2: Lägg till information i dina värden för att slutföra din flik</span><span class="sxs-lookup"><span data-stu-id="55490-119">Example 2: Add details to your tab completion values</span></span>

<span data-ttu-id="55490-120">I följande exempel skrivs fliken ifyllning för cmdlet-parameterns **namn** -parameter `Stop-Service` och returnerar endast tjänster som körs.</span><span class="sxs-lookup"><span data-stu-id="55490-120">The following example overwrites tab completion for the **Name** parameter of the `Stop-Service` cmdlet and only returns running services.</span></span>

```powershell
$s = {
    param($commandName, $parameterName, $wordToComplete, $commandAst, $fakeBoundParameters)
    $services = Get-Service | Where-Object {$_.Status -eq "Running" -and $_.Name -like "$wordToComplete*"}
    $services | ForEach-Object {
        New-Object -Type System.Management.Automation.CompletionResult -ArgumentList $_.Name,
            $_.Name,
            "ParameterValue",
            $_.Name
    }
}
Register-ArgumentCompleter -CommandName Stop-Service -ParameterName Name -ScriptBlock $s
```

<span data-ttu-id="55490-121">Det första kommandot skapar ett-skript block som tar de nödvändiga parametrarna som skickas i när användaren trycker på <kbd>fliken</kbd>. Mer information finns i Beskrivning av **script block** -parametern.</span><span class="sxs-lookup"><span data-stu-id="55490-121">The first command creates a script block which takes the required parameters which are passed in when the user presses <kbd>Tab</kbd>. For more information, see the **ScriptBlock** parameter description.</span></span>

<span data-ttu-id="55490-122">I-skript blocket hämtar det första kommandot alla tjänster som körs med hjälp av `Where-Object` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="55490-122">Within the script block, the first command retrieves all running services using the `Where-Object` cmdlet.</span></span> <span data-ttu-id="55490-123">Tjänsterna är skickas till `ForEach-Object` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="55490-123">The services are piped to the `ForEach-Object` cmdlet.</span></span> <span data-ttu-id="55490-124">`ForEach-Object`Cmdleten skapar ett nytt [system. Management. Automation. CompletionResult](/dotnet/api/system.management.automation.completionresult) -objekt och fyller det med namnet på den aktuella tjänsten (representeras av pipeline-variabeln `$_.Name` ).</span><span class="sxs-lookup"><span data-stu-id="55490-124">The `ForEach-Object` cmdlet creates a new [System.Management.Automation.CompletionResult](/dotnet/api/system.management.automation.completionresult) object and populates it with the name of the current service (represented by the pipeline variable `$_.Name`).</span></span>

<span data-ttu-id="55490-125">Med **CompletionResult** -objektet kan du ge ytterligare information till varje returnerat värde:</span><span class="sxs-lookup"><span data-stu-id="55490-125">The **CompletionResult** object allows you to provide additional details to each returned value:</span></span>

- <span data-ttu-id="55490-126">**completionText** (sträng) – den text som ska användas som resultat av automatisk komplettering.</span><span class="sxs-lookup"><span data-stu-id="55490-126">**completionText** (String) - The text to be used as the auto completion result.</span></span> <span data-ttu-id="55490-127">Detta är värdet som skickas till kommandot.</span><span class="sxs-lookup"><span data-stu-id="55490-127">This is the value sent to the command.</span></span>
- <span data-ttu-id="55490-128">**listItemText** (sträng) – texten som ska visas i en lista, t. ex. när användaren trycker på <kbd>CTRL</kbd>- + <kbd>blank steg</kbd>.</span><span class="sxs-lookup"><span data-stu-id="55490-128">**listItemText** (String) - The text to be displayed in a list, such as when the user presses <kbd>Ctrl</kbd>+<kbd>Space</kbd>.</span></span> <span data-ttu-id="55490-129">Detta används endast för visning och skickas inte till kommandot när det är markerat.</span><span class="sxs-lookup"><span data-stu-id="55490-129">This is used for display only and is not passed to the command when selected.</span></span>
- <span data-ttu-id="55490-130">**resultType** ([CompletionResultType](/dotnet/api/system.management.automation.completionresulttype)) – typen av slut för ande resultat.</span><span class="sxs-lookup"><span data-stu-id="55490-130">**resultType** ([CompletionResultType](/dotnet/api/system.management.automation.completionresulttype)) - The type of completion result.</span></span>
- <span data-ttu-id="55490-131">**knapp Beskrivning** (sträng) – text för knapp beskrivningen med information som ska visas om objektet.</span><span class="sxs-lookup"><span data-stu-id="55490-131">**toolTip** (String) - The text for the tooltip with details to be displayed about the object.</span></span>
  <span data-ttu-id="55490-132">Detta visas när användaren väljer ett objekt efter att ha tryckt på <kbd>CTRL</kbd>- + <kbd>ytan</kbd>.</span><span class="sxs-lookup"><span data-stu-id="55490-132">This is visible when the user selects an item after pressing <kbd>Ctrl</kbd>+<kbd>Space</kbd>.</span></span>

<span data-ttu-id="55490-133">Det sista kommandot visar att de stoppade tjänsterna fortfarande kan skickas manuellt till `Stop-Service` cmdlet: en.</span><span class="sxs-lookup"><span data-stu-id="55490-133">The last command demonstrates that stopped services can still be passed in manually to the `Stop-Service` cmdlet.</span></span> <span data-ttu-id="55490-134">Fliken slut för ande är den enda aspekt som påverkas.</span><span class="sxs-lookup"><span data-stu-id="55490-134">The tab completion is the only aspect affected.</span></span>

### <span data-ttu-id="55490-135">Exempel 3: registrera en anpassad intern argument slutförare</span><span class="sxs-lookup"><span data-stu-id="55490-135">Example 3: Register a custom Native argument completer</span></span>

<span data-ttu-id="55490-136">Du kan använda den **inbyggda** parametern för att ange att en flik ska slutföras för ett internt kommando.</span><span class="sxs-lookup"><span data-stu-id="55490-136">You can use the **Native** parameter to provide tab-completion for a native command.</span></span> <span data-ttu-id="55490-137">I följande exempel lägger du till TABB-slutförande för `dotnet` kommando rads gränssnittet (CLI).</span><span class="sxs-lookup"><span data-stu-id="55490-137">The following example adds tab-completion for the `dotnet` Command Line Interface (CLI).</span></span>

> [!NOTE]
> <span data-ttu-id="55490-138">`dotnet complete`Kommandot är endast tillgängligt i version 2,0 och senare av Dotnet cli.</span><span class="sxs-lookup"><span data-stu-id="55490-138">The `dotnet complete` command is only available in version 2.0 and greater of the dotnet cli.</span></span>

```powershell
$scriptblock = {
    param($wordToComplete, $commandAst, $cursorPosition)
        dotnet complete --position $cursorPosition $commandAst.ToString() | ForEach-Object {
            [System.Management.Automation.CompletionResult]::new($_, $_, 'ParameterValue', $_)
        }
}
Register-ArgumentCompleter -Native -CommandName dotnet -ScriptBlock $scriptblock
```

<span data-ttu-id="55490-139">Det första kommandot skapar ett-skript block som tar de nödvändiga parametrarna som skickas i när användaren trycker på <kbd>fliken</kbd>. Mer information finns i Beskrivning av **script block** -parametern.</span><span class="sxs-lookup"><span data-stu-id="55490-139">The first command creates a script block which takes the required parameters which are passed in when the user presses <kbd>Tab</kbd>. For more information, see the **ScriptBlock** parameter description.</span></span>

<span data-ttu-id="55490-140">I-skript blocket `dotnet complete` används kommandot för att utföra slut för ande av fliken.</span><span class="sxs-lookup"><span data-stu-id="55490-140">Within the script block, the `dotnet complete` command is used to perform the tab completion.</span></span>
<span data-ttu-id="55490-141">Resultaten är skickas till `ForEach-Object` cmdleten som använder den **nya** statiska metoden i klassen [system. Management. Automation. CompletionResult](/dotnet/api/system.management.automation.completionresult) för att skapa ett nytt **CompletionResult** -objekt för varje värde.</span><span class="sxs-lookup"><span data-stu-id="55490-141">The results are piped to the `ForEach-Object` cmdlet which use the **new** static method of the [System.Management.Automation.CompletionResult](/dotnet/api/system.management.automation.completionresult) class to create a new **CompletionResult** object for each value.</span></span>

## <span data-ttu-id="55490-142">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="55490-142">PARAMETERS</span></span>

### <span data-ttu-id="55490-143">– CommandName</span><span class="sxs-lookup"><span data-stu-id="55490-143">-CommandName</span></span>

<span data-ttu-id="55490-144">Anger namnet på kommandona som en matris.</span><span class="sxs-lookup"><span data-stu-id="55490-144">Specifies the name of the commands as an array.</span></span>

```yaml
Type: System.String[]
Parameter Sets: NativeSet, PowerShellSet
Aliases:

Required: True (NativeSet), False (PowerShellSet)
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="55490-145">– Inbyggd</span><span class="sxs-lookup"><span data-stu-id="55490-145">-Native</span></span>

<span data-ttu-id="55490-146">Anger att argumentet är slutfört för ett internt kommando där PowerShell inte kan slutföra parameter namn.</span><span class="sxs-lookup"><span data-stu-id="55490-146">Indicates that the argument completer is for a native command where PowerShell cannot complete parameter names.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: NativeSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="55490-147">– ParameterName</span><span class="sxs-lookup"><span data-stu-id="55490-147">-ParameterName</span></span>

<span data-ttu-id="55490-148">Anger namnet på den parameter vars argument slutförs.</span><span class="sxs-lookup"><span data-stu-id="55490-148">Specifies the name of the parameter whose argument is being completed.</span></span> <span data-ttu-id="55490-149">Det angivna parameter namnet får inte vara ett uppräknat värde, till exempel **ForegroundColor** -parametern för `Write-Host` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="55490-149">The parameter name specified cannot be an enumerated value, such as the **ForegroundColor** parameter of the `Write-Host` cmdlet.</span></span>

<span data-ttu-id="55490-150">Mer information om uppräkningar finns i [about_Enum](./About/about_Enum.md).</span><span class="sxs-lookup"><span data-stu-id="55490-150">For more information on enums, see [about_Enum](./About/about_Enum.md).</span></span>

```yaml
Type: System.String
Parameter Sets: PowerShellSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="55490-151">– Script block</span><span class="sxs-lookup"><span data-stu-id="55490-151">-ScriptBlock</span></span>

<span data-ttu-id="55490-152">Anger vilka kommandon som ska köras för att utföra slut för ande av tabbar.</span><span class="sxs-lookup"><span data-stu-id="55490-152">Specifies the commands to run to perform tab completion.</span></span> <span data-ttu-id="55490-153">Det skript block som du anger ska returnera värdena som slutför indatamängden.</span><span class="sxs-lookup"><span data-stu-id="55490-153">The script block you provide should return the values that complete the input.</span></span> <span data-ttu-id="55490-154">Skript blocket måste avregistrera värdena med hjälp av pipelinen ( `ForEach-Object` , `Where-Object` osv.) eller någon annan lämplig metod.</span><span class="sxs-lookup"><span data-stu-id="55490-154">The script block must unroll the values using the pipeline (`ForEach-Object`, `Where-Object`, etc.), or another suitable method.</span></span> <span data-ttu-id="55490-155">Om du returnerar en matris med värden kan PowerShell behandla hela matrisen som **ett** värde för sista tabb.</span><span class="sxs-lookup"><span data-stu-id="55490-155">Returning an array of values causes PowerShell to treat the entire array as **one** tab completion value.</span></span>

<span data-ttu-id="55490-156">Skript blocket måste acceptera följande parametrar i den ordning som anges nedan.</span><span class="sxs-lookup"><span data-stu-id="55490-156">The script block must accept the following parameters in the order specified below.</span></span> <span data-ttu-id="55490-157">Namnen på parametrarna är inte viktiga eftersom PowerShell passerar i värdena efter position.</span><span class="sxs-lookup"><span data-stu-id="55490-157">The names of the parameters aren't important because PowerShell passes in the values by position.</span></span>

- <span data-ttu-id="55490-158">`$commandName` (Position 0) – den här parametern anges till namnet på det kommando som skript blocket tillhandahåller för att slutföra tabben.</span><span class="sxs-lookup"><span data-stu-id="55490-158">`$commandName` (Position 0) - This parameter is set to the name of the command for which the script block is providing tab completion.</span></span>
- <span data-ttu-id="55490-159">`$parameterName` (Position 1) – den här parametern har angetts till den parameter vars värde kräver att tabbtangenten slutförs.</span><span class="sxs-lookup"><span data-stu-id="55490-159">`$parameterName` (Position 1) - This parameter is set to the parameter whose value requires tab completion.</span></span>
- <span data-ttu-id="55490-160">`$wordToComplete` (Position 2) – den här parametern är inställd på värde som användaren har angett innan de tryckte på <kbd>fliken</kbd>. Skript blocket ska använda det här värdet för att fastställa värden för tabbar.</span><span class="sxs-lookup"><span data-stu-id="55490-160">`$wordToComplete` (Position 2) - This parameter is set to value the user has provided before they pressed <kbd>Tab</kbd>. Your script block should use this value to determine tab completion values.</span></span>
- <span data-ttu-id="55490-161">`$commandAst` (Position 3) – den här parametern har angetts till det abstrakta Syntaxs trädet (AST) för den aktuella indatamängden.</span><span class="sxs-lookup"><span data-stu-id="55490-161">`$commandAst` (Position 3) - This parameter is set to the Abstract Syntax Tree (AST) for the current input line.</span></span> <span data-ttu-id="55490-162">Mer information finns i [AST-klass](/dotnet/api/system.management.automation.language.ast).</span><span class="sxs-lookup"><span data-stu-id="55490-162">For more information, see [Ast Class](/dotnet/api/system.management.automation.language.ast).</span></span>
- <span data-ttu-id="55490-163">`$fakeBoundParameters` (Position 4) – den här parametern anges till en hash-text som innehåller `$PSBoundParameters` för cmdleten innan användaren tryckte på <kbd>fliken</kbd>. Mer information finns i [about_Automatic_Variables](./About/about_Automatic_Variables.md).</span><span class="sxs-lookup"><span data-stu-id="55490-163">`$fakeBoundParameters` (Position 4) - This parameter is set to a hashtable containing the `$PSBoundParameters` for the cmdlet, before the user pressed <kbd>Tab</kbd>. For more information, see [about_Automatic_Variables](./About/about_Automatic_Variables.md).</span></span>

<span data-ttu-id="55490-164">När du anger den **interna** parametern måste skript blocket ta följande parametrar i den angivna ordningen.</span><span class="sxs-lookup"><span data-stu-id="55490-164">When you specify the **Native** parameter, the script block must take the following parameters in the specified order.</span></span> <span data-ttu-id="55490-165">Namnen på parametrarna är inte viktiga eftersom PowerShell passerar i värdena efter position.</span><span class="sxs-lookup"><span data-stu-id="55490-165">The names of the parameters aren't important because PowerShell passes in the values by position.</span></span>

- <span data-ttu-id="55490-166">`$wordToComplete` (Position 0) – den här parametern är inställd på värde som användaren har angett innan de tryckte på <kbd>fliken</kbd>. Skript blocket ska använda det här värdet för att fastställa värden för tabbar.</span><span class="sxs-lookup"><span data-stu-id="55490-166">`$wordToComplete` (Position 0) - This parameter is set to value the user has provided before they pressed <kbd>Tab</kbd>. Your script block should use this value to determine tab completion values.</span></span>
- <span data-ttu-id="55490-167">`$commandAst` (Position 1) – den här parametern har angetts till det abstrakta Syntaxs trädet (AST) för den aktuella indatamängden.</span><span class="sxs-lookup"><span data-stu-id="55490-167">`$commandAst` (Position 1) - This parameter is set to the Abstract Syntax Tree (AST) for the current input line.</span></span> <span data-ttu-id="55490-168">Mer information finns i [AST-klass](/dotnet/api/system.management.automation.language.ast).</span><span class="sxs-lookup"><span data-stu-id="55490-168">For more information, see [Ast Class](/dotnet/api/system.management.automation.language.ast).</span></span>
- <span data-ttu-id="55490-169">`$cursorPosition` (Position 2) – den här parametern anges till positionen för markören när användaren tryckte på <kbd>fliken</kbd>.</span><span class="sxs-lookup"><span data-stu-id="55490-169">`$cursorPosition` (Position 2) - This parameter is set to the position of the cursor when the user pressed <kbd>Tab</kbd>.</span></span>

<span data-ttu-id="55490-170">Du kan också ange ett **ArgumentCompleter** som parameter-attribut.</span><span class="sxs-lookup"><span data-stu-id="55490-170">You can also provide an **ArgumentCompleter** as a parameter attribute.</span></span> <span data-ttu-id="55490-171">Mer information finns i [about_Functions_Advanced_Parameters](./About/about_Functions_Advanced_Parameters.md).</span><span class="sxs-lookup"><span data-stu-id="55490-171">For more information, see [about_Functions_Advanced_Parameters](./About/about_Functions_Advanced_Parameters.md).</span></span>

```yaml
Type: System.Management.Automation.ScriptBlock
Parameter Sets: (All)
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="55490-172">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="55490-172">CommonParameters</span></span>

<span data-ttu-id="55490-173">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="55490-173">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="55490-174">Mer information finns i [about_CommonParameters](./About/about_CommonParameters.md).</span><span class="sxs-lookup"><span data-stu-id="55490-174">For more information, see [about_CommonParameters](./About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="55490-175">INDATA</span><span class="sxs-lookup"><span data-stu-id="55490-175">INPUTS</span></span>

### <span data-ttu-id="55490-176">Inga</span><span class="sxs-lookup"><span data-stu-id="55490-176">None</span></span>

<span data-ttu-id="55490-177">Det går inte att skicka pipe-objekt till denna cmdlet.</span><span class="sxs-lookup"><span data-stu-id="55490-177">You cannot pipe objects to this cmdlet.</span></span>

## <span data-ttu-id="55490-178">UTDATA</span><span class="sxs-lookup"><span data-stu-id="55490-178">OUTPUTS</span></span>

### <span data-ttu-id="55490-179">Inga</span><span class="sxs-lookup"><span data-stu-id="55490-179">None</span></span>

<span data-ttu-id="55490-180">Denna cmdlet returnerar inga utdata.</span><span class="sxs-lookup"><span data-stu-id="55490-180">This cmdlet returns no output.</span></span>

## <span data-ttu-id="55490-181">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="55490-181">NOTES</span></span>

## <span data-ttu-id="55490-182">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="55490-182">RELATED LINKS</span></span>

