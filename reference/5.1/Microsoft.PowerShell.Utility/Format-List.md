---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 12/19/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/format-list?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Format-List
ms.openlocfilehash: 7817384f077c58b46aed1dba552f89ac431891f0
ms.sourcegitcommit: 9a6b6714ded4edb5119f1b82a253608018ea6b98
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/10/2020
ms.locfileid: "93269013"
---
# <span data-ttu-id="701ed-103">Format-List</span><span class="sxs-lookup"><span data-stu-id="701ed-103">Format-List</span></span>

## <span data-ttu-id="701ed-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="701ed-104">SYNOPSIS</span></span>
<span data-ttu-id="701ed-105">Formaterar utdata som en lista med egenskaper där varje egenskap visas på en ny rad.</span><span class="sxs-lookup"><span data-stu-id="701ed-105">Formats the output as a list of properties in which each property appears on a new line.</span></span>

## <span data-ttu-id="701ed-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="701ed-106">SYNTAX</span></span>

```
Format-List [[-Property] <Object[]>] [-GroupBy <Object>] [-View <string>] [-ShowError]
[-DisplayError] [-Force] [-Expand <string>] [-InputObject <psobject>] [<CommonParameters>]
```

## <span data-ttu-id="701ed-107">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="701ed-107">DESCRIPTION</span></span>

<span data-ttu-id="701ed-108">`Format-List`Cmdleten formaterar utdata från ett kommando som en lista med egenskaper där varje egenskap visas på en separat rad.</span><span class="sxs-lookup"><span data-stu-id="701ed-108">The `Format-List` cmdlet formats the output of a command as a list of properties in which each property is displayed on a separate line.</span></span> <span data-ttu-id="701ed-109">Du kan använda `Format-List` för att formatera och Visa alla eller valda egenskaper för ett objekt som en lista (format-List \*).</span><span class="sxs-lookup"><span data-stu-id="701ed-109">You can use `Format-List` to format and display all or selected properties of an object as a list (format-list \*).</span></span>

<span data-ttu-id="701ed-110">Eftersom det finns mer utrymme för varje objekt i en lista än i en tabell, visar PowerShell fler egenskaper för objektet i listan, och egenskapsvärdena är mindre troligt vis trunkerade.</span><span class="sxs-lookup"><span data-stu-id="701ed-110">Because more space is available for each item in a list than in a table, PowerShell displays more properties of the object in the list, and the property values are less likely to be truncated.</span></span>

## <span data-ttu-id="701ed-111">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="701ed-111">EXAMPLES</span></span>

### <span data-ttu-id="701ed-112">Exempel 1: formatera dator tjänster</span><span class="sxs-lookup"><span data-stu-id="701ed-112">Example 1: Format computer services</span></span>

```powershell
Get-Service | Format-List
```

<span data-ttu-id="701ed-113">Det här kommandot formaterar information om tjänster på datorn som en lista.</span><span class="sxs-lookup"><span data-stu-id="701ed-113">This command formats information about services on the computer as a list.</span></span> <span data-ttu-id="701ed-114">Som standard är tjänsterna formaterade som en tabell.</span><span class="sxs-lookup"><span data-stu-id="701ed-114">By default, the services are formatted as a table.</span></span> <span data-ttu-id="701ed-115">`Get-Service`Cmdleten hämtar objekt som representerar tjänsterna på datorn.</span><span class="sxs-lookup"><span data-stu-id="701ed-115">The `Get-Service` cmdlet gets objects representing the services on the computer.</span></span> <span data-ttu-id="701ed-116">Pipeline-operatorn (|) skickar resultaten via pipelinen till `Format-List` .</span><span class="sxs-lookup"><span data-stu-id="701ed-116">The pipeline operator (|) passes the results through the pipeline to `Format-List`.</span></span>
<span data-ttu-id="701ed-117">Sedan `Format-List` formaterar kommandot tjänst informationen i en lista och skickar den till standardutdata-cmdleten för visning.</span><span class="sxs-lookup"><span data-stu-id="701ed-117">Then, the `Format-List` command formats the service information in a list and sends it to the default output cmdlet for display.</span></span>

### <span data-ttu-id="701ed-118">Exempel 2: formatera PS1XML-filer</span><span class="sxs-lookup"><span data-stu-id="701ed-118">Example 2: Format PS1XML files</span></span>

<span data-ttu-id="701ed-119">De här kommandona visar information om PS1XML-filerna i PowerShell-katalogen som en lista.</span><span class="sxs-lookup"><span data-stu-id="701ed-119">These commands display information about the PS1XML files in the PowerShell directory as a list.</span></span>

```powershell
$A = Get-ChildItem $pshome\*.ps1xml
Format-List -InputObject $A
```

<span data-ttu-id="701ed-120">Det första kommandot hämtar objekten som representerar filerna och lagrar dem i `$A` variabeln.</span><span class="sxs-lookup"><span data-stu-id="701ed-120">The first command gets the objects representing the files and stores them in the `$A` variable.</span></span>

<span data-ttu-id="701ed-121">Det andra kommandot använder `Format-List` för att formatera information om objekt som lagras i `$A` .</span><span class="sxs-lookup"><span data-stu-id="701ed-121">The second command uses `Format-List` to format information about objects stored in `$A`.</span></span> <span data-ttu-id="701ed-122">Det här kommandot använder parametern **InputObject** för att skicka variabeln till `Format-List` , som sedan skickar det formaterade resultatet till standardutdata-cmdleten för visning.</span><span class="sxs-lookup"><span data-stu-id="701ed-122">This command uses the **InputObject** parameter to pass the variable to `Format-List`, which then sends the formatted output to the default output cmdlet for display.</span></span>

### <span data-ttu-id="701ed-123">Exempel 3: formatera process egenskaper efter namn</span><span class="sxs-lookup"><span data-stu-id="701ed-123">Example 3: Format process properties by name</span></span>

<span data-ttu-id="701ed-124">Det här kommandot visar namnet, bas prioriteten och prioritets klassen för varje process på datorn.</span><span class="sxs-lookup"><span data-stu-id="701ed-124">This command displays the name, base priority, and priority class of each process on the computer.</span></span>

```powershell
Get-Process | Format-List -Property name, basepriority, priorityclass
```

<span data-ttu-id="701ed-125">Den använder `Get-Process` cmdleten för att hämta ett objekt som representerar varje process.</span><span class="sxs-lookup"><span data-stu-id="701ed-125">It uses the `Get-Process` cmdlet to get an object representing each process.</span></span> <span data-ttu-id="701ed-126">Pipeline-operatorn (|) skickar process objekt via pipelinen till `Format-List` .</span><span class="sxs-lookup"><span data-stu-id="701ed-126">The pipeline operator (|) passes the process objects through the pipeline to `Format-List`.</span></span> <span data-ttu-id="701ed-127">`Format-List` formaterar processerna som en lista med de angivna egenskaperna.</span><span class="sxs-lookup"><span data-stu-id="701ed-127">`Format-List` formats the processes as a list of the specified properties.</span></span> <span data-ttu-id="701ed-128">*Egenskaps* parameter namnet är valfritt, så du kan utelämna det.</span><span class="sxs-lookup"><span data-stu-id="701ed-128">The *Property* parameter name is optional, so you can omit it.</span></span>

### <span data-ttu-id="701ed-129">Exempel 4: formatera alla egenskaper för en process</span><span class="sxs-lookup"><span data-stu-id="701ed-129">Example 4: Format all properties for a process</span></span>

<span data-ttu-id="701ed-130">Det här kommandot visar alla egenskaper för Winlogon-processen.</span><span class="sxs-lookup"><span data-stu-id="701ed-130">This command displays all of the properties of the Winlogon process.</span></span>

```powershell
Get-Process winlogon | Format-List -Property *
```

<span data-ttu-id="701ed-131">Den använder Get-Process-cmdlet för att hämta ett objekt som representerar Winlogon-processen.</span><span class="sxs-lookup"><span data-stu-id="701ed-131">It uses the Get-Process cmdlet to get an object representing the Winlogon process.</span></span> <span data-ttu-id="701ed-132">Pipeline-operatorn (|) skickar objektet Winlogon-process via pipeline till `Format-List` .</span><span class="sxs-lookup"><span data-stu-id="701ed-132">The pipeline operator (|) passes the Winlogon process object through the pipeline to `Format-List`.</span></span> <span data-ttu-id="701ed-133">Kommandot använder *egenskaps* parametern för att ange egenskaperna och \* för att ange alla egenskaper.</span><span class="sxs-lookup"><span data-stu-id="701ed-133">The command uses the *Property* parameter to specify the properties and the \* to indicate all properties.</span></span>
<span data-ttu-id="701ed-134">Eftersom namnet på *egenskaps* parametern är valfritt kan du utelämna det och skriva kommandot som `Format-List *` .</span><span class="sxs-lookup"><span data-stu-id="701ed-134">Because the name of the *Property* parameter is optional, you can omit it and type the command as `Format-List *`.</span></span> <span data-ttu-id="701ed-135">`Format-List` skickar automatiskt resultaten till standard-utdata-cmdleten för visning.</span><span class="sxs-lookup"><span data-stu-id="701ed-135">`Format-List` automatically sends the results to the default output cmdlet for display.</span></span>

### <span data-ttu-id="701ed-136">Exempel 5: fel sökning av format fel</span><span class="sxs-lookup"><span data-stu-id="701ed-136">Example 5: Troubleshooting format errors</span></span>

<span data-ttu-id="701ed-137">I följande exempel visas resultatet av att lägga till **DisplayError** -eller **ShowError** -parametrarna med ett uttryck.</span><span class="sxs-lookup"><span data-stu-id="701ed-137">The following examples show of the results of adding the **DisplayError** or **ShowError** parameters with an expression.</span></span>

```powershell
PC /> Get-Date | Format-List DayOfWeek,{ $_ / $null } -DisplayError

DayOfWeek    : Friday
 $_ / $null  : #ERR

PC /> Get-Date | Format-List DayOfWeek,{ $_ / $null } -ShowError

DayOfWeek    : Friday
 $_ / $null  :

Failed to evaluate expression " $_ / $null ".
+ CategoryInfo          : InvalidArgument: (12/21/2018 7:59:23 AM:PSObject) [], RuntimeException
+ FullyQualifiedErrorId : PSPropertyExpressionError
```

## <span data-ttu-id="701ed-138">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="701ed-138">PARAMETERS</span></span>

### <span data-ttu-id="701ed-139">– DisplayError</span><span class="sxs-lookup"><span data-stu-id="701ed-139">-DisplayError</span></span>

<span data-ttu-id="701ed-140">Anger att denna cmdlet visar fel på kommando raden.</span><span class="sxs-lookup"><span data-stu-id="701ed-140">Indicates that this cmdlet displays errors at the command line.</span></span> <span data-ttu-id="701ed-141">Den här parametern används sällan, men kan användas som ett fel söknings stöd när du formaterar uttryck i ett `Format-List` kommando, och uttrycken verkar inte fungera.</span><span class="sxs-lookup"><span data-stu-id="701ed-141">This parameter is rarely used, but can be used as a debugging aid when you are formatting expressions in a `Format-List` command, and the expressions do not appear to be working.</span></span>

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

### <span data-ttu-id="701ed-142">– Expandera</span><span class="sxs-lookup"><span data-stu-id="701ed-142">-Expand</span></span>

<span data-ttu-id="701ed-143">Anger det formaterade samlings objektet, samt objekt i samlingen.</span><span class="sxs-lookup"><span data-stu-id="701ed-143">Specifies the formatted collection object, as well as the objects in the collection.</span></span> <span data-ttu-id="701ed-144">Den här parametern är utformad för att formatera objekt som har stöd för ICollection-gränssnittet (system. Collection).</span><span class="sxs-lookup"><span data-stu-id="701ed-144">This parameter is designed to format objects that support the ICollection (System.Collections) interface.</span></span> <span data-ttu-id="701ed-145">Standardvärdet är EnumOnly.</span><span class="sxs-lookup"><span data-stu-id="701ed-145">The default value is EnumOnly.</span></span> <span data-ttu-id="701ed-146">De acceptabla värdena för den här parametern är:</span><span class="sxs-lookup"><span data-stu-id="701ed-146">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="701ed-147">EnumOnly.</span><span class="sxs-lookup"><span data-stu-id="701ed-147">EnumOnly.</span></span> <span data-ttu-id="701ed-148">Visar egenskaperna för objekten i samlingen.</span><span class="sxs-lookup"><span data-stu-id="701ed-148">Displays the properties of the objects in the collection.</span></span>
- <span data-ttu-id="701ed-149">CoreOnly.</span><span class="sxs-lookup"><span data-stu-id="701ed-149">CoreOnly.</span></span> <span data-ttu-id="701ed-150">Visar egenskaperna för objektet samling.</span><span class="sxs-lookup"><span data-stu-id="701ed-150">Displays the properties of the collection object.</span></span>
- <span data-ttu-id="701ed-151">Dubbelrikta.</span><span class="sxs-lookup"><span data-stu-id="701ed-151">Both.</span></span> <span data-ttu-id="701ed-152">Visar egenskaperna för samlings objekt och egenskaper för objekt i samlingen.</span><span class="sxs-lookup"><span data-stu-id="701ed-152">Displays the properties of the collection object and the properties of objects in the collection.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values: CoreOnly, EnumOnly, Both

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="701ed-153">-Force</span><span class="sxs-lookup"><span data-stu-id="701ed-153">-Force</span></span>

<span data-ttu-id="701ed-154">Anger att denna cmdlet visar all fel information.</span><span class="sxs-lookup"><span data-stu-id="701ed-154">Indicates that this cmdlet displays all of the error information.</span></span> <span data-ttu-id="701ed-155">Används med parametern **DisplayError** eller **ShowError** .</span><span class="sxs-lookup"><span data-stu-id="701ed-155">Use with the **DisplayError** or **ShowError** parameter.</span></span> <span data-ttu-id="701ed-156">Som standard visas endast en del fel information när ett fel objekt skrivs till fel-eller visnings strömmar.</span><span class="sxs-lookup"><span data-stu-id="701ed-156">By default, when an error object is written to the error or display streams, only some of the error information is displayed.</span></span>

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

### <span data-ttu-id="701ed-157">– GroupBy</span><span class="sxs-lookup"><span data-stu-id="701ed-157">-GroupBy</span></span>

<span data-ttu-id="701ed-158">Anger utdata i grupper baserat på en delad egenskap eller ett värde.</span><span class="sxs-lookup"><span data-stu-id="701ed-158">Specifies the output in groups based on a shared property or value.</span></span> <span data-ttu-id="701ed-159">Ange ett uttryck eller en egenskap för utdata.</span><span class="sxs-lookup"><span data-stu-id="701ed-159">Enter an expression or a property of the output.</span></span>

<span data-ttu-id="701ed-160">Värdet för **groupby** -parametern kan vara en ny beräknad egenskap.</span><span class="sxs-lookup"><span data-stu-id="701ed-160">The value of the **GroupBy** parameter can be a new calculated property.</span></span> <span data-ttu-id="701ed-161">Den beräknade egenskapen kan vara ett skript block eller en hash-tabell.</span><span class="sxs-lookup"><span data-stu-id="701ed-161">The calculated property can be a script block or a hash table.</span></span> <span data-ttu-id="701ed-162">Giltiga nyckel/värde-par är:</span><span class="sxs-lookup"><span data-stu-id="701ed-162">Valid key-value pairs are:</span></span>

- <span data-ttu-id="701ed-163">Namn (eller etikett)- `<string>`</span><span class="sxs-lookup"><span data-stu-id="701ed-163">Name (or Label) - `<string>`</span></span>
- <span data-ttu-id="701ed-164">Uttryck- `<string>` eller `<script block>`</span><span class="sxs-lookup"><span data-stu-id="701ed-164">Expression - `<string>` or `<script block>`</span></span>
- <span data-ttu-id="701ed-165">FormatString `<string>`</span><span class="sxs-lookup"><span data-stu-id="701ed-165">FormatString - `<string>`</span></span>

<span data-ttu-id="701ed-166">Mer information finns i [about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md).</span><span class="sxs-lookup"><span data-stu-id="701ed-166">For more information, see [about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md).</span></span>

```yaml
Type: System.Object
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="701ed-167">– InputObject</span><span class="sxs-lookup"><span data-stu-id="701ed-167">-InputObject</span></span>

<span data-ttu-id="701ed-168">Anger de objekt som ska formateras.</span><span class="sxs-lookup"><span data-stu-id="701ed-168">Specifies the objects to be formatted.</span></span> <span data-ttu-id="701ed-169">Ange en variabel som innehåller objekten eller Skriv ett kommando eller uttryck som hämtar objekten.</span><span class="sxs-lookup"><span data-stu-id="701ed-169">Enter a variable that contains the objects or type a command or expression that gets the objects.</span></span>

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="701ed-170">– Egenskap</span><span class="sxs-lookup"><span data-stu-id="701ed-170">-Property</span></span>

<span data-ttu-id="701ed-171">Anger objekt egenskaperna som visas i visningen och i vilken ordning de visas.</span><span class="sxs-lookup"><span data-stu-id="701ed-171">Specifies the object properties that appear in the display and the order in which they appear.</span></span>
<span data-ttu-id="701ed-172">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="701ed-172">Wildcards are permitted.</span></span>

<span data-ttu-id="701ed-173">Om du utelämnar den här parametern beror egenskaperna som visas i vyn på det objekt som visas.</span><span class="sxs-lookup"><span data-stu-id="701ed-173">If you omit this parameter, the properties that appear in the display depend on the object being displayed.</span></span> <span data-ttu-id="701ed-174">Parameter namnet "Property" är valfritt.</span><span class="sxs-lookup"><span data-stu-id="701ed-174">The parameter name "Property" is optional.</span></span> <span data-ttu-id="701ed-175">Du kan inte använda **egenskapen** och **Visa** parametrar i samma kommando.</span><span class="sxs-lookup"><span data-stu-id="701ed-175">You cannot use the **Property** and **View** parameters in the same command.</span></span>

<span data-ttu-id="701ed-176">Värdet för **egenskaps** parametern kan vara en ny beräknad egenskap.</span><span class="sxs-lookup"><span data-stu-id="701ed-176">The value of the **Property** parameter can be a new calculated property.</span></span> <span data-ttu-id="701ed-177">Den beräknade egenskapen kan vara ett skript block eller en hash-tabell.</span><span class="sxs-lookup"><span data-stu-id="701ed-177">The calculated property can be a script block or a hash table.</span></span> <span data-ttu-id="701ed-178">Giltiga nyckel/värde-par är:</span><span class="sxs-lookup"><span data-stu-id="701ed-178">Valid key-value pairs are:</span></span>

- <span data-ttu-id="701ed-179">Namn (eller etikett)- `<string>`</span><span class="sxs-lookup"><span data-stu-id="701ed-179">Name (or Label) - `<string>`</span></span>
- <span data-ttu-id="701ed-180">Uttryck- `<string>` eller `<script block>`</span><span class="sxs-lookup"><span data-stu-id="701ed-180">Expression - `<string>` or `<script block>`</span></span>
- <span data-ttu-id="701ed-181">FormatString `<string>`</span><span class="sxs-lookup"><span data-stu-id="701ed-181">FormatString - `<string>`</span></span>

<span data-ttu-id="701ed-182">Mer information finns i [about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md).</span><span class="sxs-lookup"><span data-stu-id="701ed-182">For more information, see [about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md).</span></span>

```yaml
Type: System.Object[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="701ed-183">– ShowError</span><span class="sxs-lookup"><span data-stu-id="701ed-183">-ShowError</span></span>

<span data-ttu-id="701ed-184">Anger att cmdleten skickar fel via pipelinen.</span><span class="sxs-lookup"><span data-stu-id="701ed-184">Indicates that the cmdlet sends errors through the pipeline.</span></span> <span data-ttu-id="701ed-185">Den här parametern används sällan, men kan användas som ett fel söknings stöd när du formaterar uttryck i ett `Format-List` kommando, och uttrycken verkar inte fungera.</span><span class="sxs-lookup"><span data-stu-id="701ed-185">This parameter is rarely used, but can be used as a debugging aid when you are formatting expressions in a `Format-List` command, and the expressions do not appear to be working.</span></span>

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

### <span data-ttu-id="701ed-186">– Visa</span><span class="sxs-lookup"><span data-stu-id="701ed-186">-View</span></span>

<span data-ttu-id="701ed-187">Anger namnet på ett alternativt List format eller en vy.</span><span class="sxs-lookup"><span data-stu-id="701ed-187">Specifies the name of an alternate list format or view.</span></span> <span data-ttu-id="701ed-188">Du kan inte använda **egenskapen** och **Visa** parametrar i samma kommando.</span><span class="sxs-lookup"><span data-stu-id="701ed-188">You cannot use the **Property** and **View** parameters in the same command.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="701ed-189">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="701ed-189">CommonParameters</span></span>

<span data-ttu-id="701ed-190">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="701ed-190">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="701ed-191">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="701ed-191">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="701ed-192">INDATA</span><span class="sxs-lookup"><span data-stu-id="701ed-192">INPUTS</span></span>

### <span data-ttu-id="701ed-193">System. Management. Automation. PSObject</span><span class="sxs-lookup"><span data-stu-id="701ed-193">System.Management.Automation.PSObject</span></span>

<span data-ttu-id="701ed-194">Du kan skicka vidare alla objekt till `Format-List` .</span><span class="sxs-lookup"><span data-stu-id="701ed-194">You can pipe any object to `Format-List`.</span></span>

## <span data-ttu-id="701ed-195">UTDATA</span><span class="sxs-lookup"><span data-stu-id="701ed-195">OUTPUTS</span></span>

### <span data-ttu-id="701ed-196">Microsoft. PowerShell. commands. Internal. format</span><span class="sxs-lookup"><span data-stu-id="701ed-196">Microsoft.PowerShell.Commands.Internal.Format</span></span>

<span data-ttu-id="701ed-197">`Format-List` Returnerar de format objekt som representerar listan.</span><span class="sxs-lookup"><span data-stu-id="701ed-197">`Format-List` returns the format objects that represent the list.</span></span>

## <span data-ttu-id="701ed-198">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="701ed-198">NOTES</span></span>

<span data-ttu-id="701ed-199">Du kan också referera till Format-List med det inbyggda aliaset, FL.</span><span class="sxs-lookup"><span data-stu-id="701ed-199">You can also refer to Format-List by its built-in alias, FL.</span></span> <span data-ttu-id="701ed-200">Mer information finns i [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md).</span><span class="sxs-lookup"><span data-stu-id="701ed-200">For more information, see [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md).</span></span>

<span data-ttu-id="701ed-201">Format-cmdletarna, till exempel `Format-List` , ordnar de data som ska visas men inte visar dem.</span><span class="sxs-lookup"><span data-stu-id="701ed-201">The format cmdlets, such as `Format-List`, arrange the data to be displayed but do not display it.</span></span>
<span data-ttu-id="701ed-202">Data visas i utmatnings funktionerna i PowerShell och av de cmdletar som innehåller verbet (out-cmdletarna), till exempel `Out-Host` eller `Out-File` .</span><span class="sxs-lookup"><span data-stu-id="701ed-202">The data is displayed by the output features of PowerShell and by the cmdlets that contain the Out verb (the Out cmdlets), such as `Out-Host` or `Out-File`.</span></span>

<span data-ttu-id="701ed-203">Om du inte använder en format-cmdlet, använder PowerShell standardformat för varje objekt som visas.</span><span class="sxs-lookup"><span data-stu-id="701ed-203">If you do not use a format cmdlet, PowerShell applies that default format for each object that it displays.</span></span>

<span data-ttu-id="701ed-204">Parametern **groupby** förutsätter att objekten sorteras.</span><span class="sxs-lookup"><span data-stu-id="701ed-204">The **GroupBy** parameter assumes that the objects are sorted.</span></span> <span data-ttu-id="701ed-205">Använd Sort-Object innan `Format-List` du använder för att gruppera objekten.</span><span class="sxs-lookup"><span data-stu-id="701ed-205">Use Sort-Object before using `Format-List` to group the objects.</span></span>

<span data-ttu-id="701ed-206">Med parametern **Visa** kan du ange ett alternativt format för tabellen.</span><span class="sxs-lookup"><span data-stu-id="701ed-206">The **View** parameter lets you specify an alternate format for the table.</span></span> <span data-ttu-id="701ed-207">Du kan använda de vyer som definierats i `*.format.PS1XML` filerna i PowerShell-katalogen, eller så kan du skapa egna vyer i nya PS1XML-filer och använda cmdleten Update-FormatData för att inkludera dem i PowerShell.</span><span class="sxs-lookup"><span data-stu-id="701ed-207">You can use the views defined in the `*.format.PS1XML` files in the PowerShell directory, or you can create your own views in new PS1XML files and use the Update-FormatData cmdlet to include them in PowerShell.</span></span>

<span data-ttu-id="701ed-208">Den alternativa vyn för parametern **View** måste använda List formatet, annars Miss lyckas kommandot.</span><span class="sxs-lookup"><span data-stu-id="701ed-208">The alternate view for the **View** parameter must use the list format, otherwise, the command fails.</span></span> <span data-ttu-id="701ed-209">Om den alternativa vyn är en tabell använder du `Format-Table` .</span><span class="sxs-lookup"><span data-stu-id="701ed-209">If the alternate view is a table, use `Format-Table`.</span></span> <span data-ttu-id="701ed-210">Om den alternativa vyn inte är en lista eller en tabell använder du `Format-Custom` .</span><span class="sxs-lookup"><span data-stu-id="701ed-210">If the alternate view is not a list or a table, use `Format-Custom`.</span></span>

## <span data-ttu-id="701ed-211">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="701ed-211">RELATED LINKS</span></span>

[<span data-ttu-id="701ed-212">about_Calculated_Properties</span><span class="sxs-lookup"><span data-stu-id="701ed-212">about_Calculated_Properties</span></span>](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md)

[<span data-ttu-id="701ed-213">Format-Custom</span><span class="sxs-lookup"><span data-stu-id="701ed-213">Format-Custom</span></span>](Format-Custom.md)

[<span data-ttu-id="701ed-214">Format-Hex</span><span class="sxs-lookup"><span data-stu-id="701ed-214">Format-Hex</span></span>](Format-Hex.md)

[<span data-ttu-id="701ed-215">Format-Table</span><span class="sxs-lookup"><span data-stu-id="701ed-215">Format-Table</span></span>](Format-Table.md)

[<span data-ttu-id="701ed-216">Format-Wide</span><span class="sxs-lookup"><span data-stu-id="701ed-216">Format-Wide</span></span>](Format-Wide.md)
