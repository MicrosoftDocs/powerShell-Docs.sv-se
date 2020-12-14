---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 12/19/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/format-list?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Format-List
ms.openlocfilehash: d8410fbc2d3f29f0726f84ab151993a60ce95434
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94709792"
---
# <span data-ttu-id="12551-102">Format-List</span><span class="sxs-lookup"><span data-stu-id="12551-102">Format-List</span></span>

## <span data-ttu-id="12551-103">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="12551-103">SYNOPSIS</span></span>
<span data-ttu-id="12551-104">Formaterar utdata som en lista med egenskaper där varje egenskap visas på en ny rad.</span><span class="sxs-lookup"><span data-stu-id="12551-104">Formats the output as a list of properties in which each property appears on a new line.</span></span>

## <span data-ttu-id="12551-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="12551-105">SYNTAX</span></span>

```
Format-List [[-Property] <Object[]>] [-GroupBy <Object>] [-View <string>] [-ShowError]
[-DisplayError] [-Force] [-Expand <string>] [-InputObject <psobject>] [<CommonParameters>]
```

## <span data-ttu-id="12551-106">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="12551-106">DESCRIPTION</span></span>

<span data-ttu-id="12551-107">`Format-List`Cmdleten formaterar utdata från ett kommando som en lista med egenskaper där varje egenskap visas på en separat rad.</span><span class="sxs-lookup"><span data-stu-id="12551-107">The `Format-List` cmdlet formats the output of a command as a list of properties in which each property is displayed on a separate line.</span></span> <span data-ttu-id="12551-108">Du kan använda `Format-List` för att formatera och Visa alla eller valda egenskaper för ett objekt som en lista (format-List \*).</span><span class="sxs-lookup"><span data-stu-id="12551-108">You can use `Format-List` to format and display all or selected properties of an object as a list (format-list \*).</span></span>

<span data-ttu-id="12551-109">Eftersom det finns mer utrymme för varje objekt i en lista än i en tabell, visar PowerShell fler egenskaper för objektet i listan, och egenskapsvärdena är mindre troligt vis trunkerade.</span><span class="sxs-lookup"><span data-stu-id="12551-109">Because more space is available for each item in a list than in a table, PowerShell displays more properties of the object in the list, and the property values are less likely to be truncated.</span></span>

## <span data-ttu-id="12551-110">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="12551-110">EXAMPLES</span></span>

### <span data-ttu-id="12551-111">Exempel 1: formatera dator tjänster</span><span class="sxs-lookup"><span data-stu-id="12551-111">Example 1: Format computer services</span></span>

```powershell
Get-Service | Format-List
```

<span data-ttu-id="12551-112">Det här kommandot formaterar information om tjänster på datorn som en lista.</span><span class="sxs-lookup"><span data-stu-id="12551-112">This command formats information about services on the computer as a list.</span></span> <span data-ttu-id="12551-113">Som standard är tjänsterna formaterade som en tabell.</span><span class="sxs-lookup"><span data-stu-id="12551-113">By default, the services are formatted as a table.</span></span> <span data-ttu-id="12551-114">`Get-Service`Cmdleten hämtar objekt som representerar tjänsterna på datorn.</span><span class="sxs-lookup"><span data-stu-id="12551-114">The `Get-Service` cmdlet gets objects representing the services on the computer.</span></span> <span data-ttu-id="12551-115">Pipeline-operatorn (|) skickar resultaten via pipelinen till `Format-List` .</span><span class="sxs-lookup"><span data-stu-id="12551-115">The pipeline operator (|) passes the results through the pipeline to `Format-List`.</span></span>
<span data-ttu-id="12551-116">Sedan `Format-List` formaterar kommandot tjänst informationen i en lista och skickar den till standardutdata-cmdleten för visning.</span><span class="sxs-lookup"><span data-stu-id="12551-116">Then, the `Format-List` command formats the service information in a list and sends it to the default output cmdlet for display.</span></span>

### <span data-ttu-id="12551-117">Exempel 2: formatera PS1XML-filer</span><span class="sxs-lookup"><span data-stu-id="12551-117">Example 2: Format PS1XML files</span></span>

<span data-ttu-id="12551-118">De här kommandona visar information om PS1XML-filerna i PowerShell-katalogen som en lista.</span><span class="sxs-lookup"><span data-stu-id="12551-118">These commands display information about the PS1XML files in the PowerShell directory as a list.</span></span>

```powershell
$A = Get-ChildItem $pshome\*.ps1xml
Format-List -InputObject $A
```

<span data-ttu-id="12551-119">Det första kommandot hämtar objekten som representerar filerna och lagrar dem i `$A` variabeln.</span><span class="sxs-lookup"><span data-stu-id="12551-119">The first command gets the objects representing the files and stores them in the `$A` variable.</span></span>

<span data-ttu-id="12551-120">Det andra kommandot använder `Format-List` för att formatera information om objekt som lagras i `$A` .</span><span class="sxs-lookup"><span data-stu-id="12551-120">The second command uses `Format-List` to format information about objects stored in `$A`.</span></span> <span data-ttu-id="12551-121">Det här kommandot använder parametern **InputObject** för att skicka variabeln till `Format-List` , som sedan skickar det formaterade resultatet till standardutdata-cmdleten för visning.</span><span class="sxs-lookup"><span data-stu-id="12551-121">This command uses the **InputObject** parameter to pass the variable to `Format-List`, which then sends the formatted output to the default output cmdlet for display.</span></span>

### <span data-ttu-id="12551-122">Exempel 3: formatera process egenskaper efter namn</span><span class="sxs-lookup"><span data-stu-id="12551-122">Example 3: Format process properties by name</span></span>

<span data-ttu-id="12551-123">Det här kommandot visar namnet, bas prioriteten och prioritets klassen för varje process på datorn.</span><span class="sxs-lookup"><span data-stu-id="12551-123">This command displays the name, base priority, and priority class of each process on the computer.</span></span>

```powershell
Get-Process | Format-List -Property name, basepriority, priorityclass
```

<span data-ttu-id="12551-124">Den använder `Get-Process` cmdleten för att hämta ett objekt som representerar varje process.</span><span class="sxs-lookup"><span data-stu-id="12551-124">It uses the `Get-Process` cmdlet to get an object representing each process.</span></span> <span data-ttu-id="12551-125">Pipeline-operatorn (|) skickar process objekt via pipelinen till `Format-List` .</span><span class="sxs-lookup"><span data-stu-id="12551-125">The pipeline operator (|) passes the process objects through the pipeline to `Format-List`.</span></span> <span data-ttu-id="12551-126">`Format-List` formaterar processerna som en lista med de angivna egenskaperna.</span><span class="sxs-lookup"><span data-stu-id="12551-126">`Format-List` formats the processes as a list of the specified properties.</span></span> <span data-ttu-id="12551-127">*Egenskaps* parameter namnet är valfritt, så du kan utelämna det.</span><span class="sxs-lookup"><span data-stu-id="12551-127">The *Property* parameter name is optional, so you can omit it.</span></span>

### <span data-ttu-id="12551-128">Exempel 4: formatera alla egenskaper för en process</span><span class="sxs-lookup"><span data-stu-id="12551-128">Example 4: Format all properties for a process</span></span>

<span data-ttu-id="12551-129">Det här kommandot visar alla egenskaper för Winlogon-processen.</span><span class="sxs-lookup"><span data-stu-id="12551-129">This command displays all of the properties of the Winlogon process.</span></span>

```powershell
Get-Process winlogon | Format-List -Property *
```

<span data-ttu-id="12551-130">Den använder Get-Process-cmdlet för att hämta ett objekt som representerar Winlogon-processen.</span><span class="sxs-lookup"><span data-stu-id="12551-130">It uses the Get-Process cmdlet to get an object representing the Winlogon process.</span></span> <span data-ttu-id="12551-131">Pipeline-operatorn (|) skickar objektet Winlogon-process via pipeline till `Format-List` .</span><span class="sxs-lookup"><span data-stu-id="12551-131">The pipeline operator (|) passes the Winlogon process object through the pipeline to `Format-List`.</span></span> <span data-ttu-id="12551-132">Kommandot använder *egenskaps* parametern för att ange egenskaperna och \* för att ange alla egenskaper.</span><span class="sxs-lookup"><span data-stu-id="12551-132">The command uses the *Property* parameter to specify the properties and the \* to indicate all properties.</span></span>
<span data-ttu-id="12551-133">Eftersom namnet på *egenskaps* parametern är valfritt kan du utelämna det och skriva kommandot som `Format-List *` .</span><span class="sxs-lookup"><span data-stu-id="12551-133">Because the name of the *Property* parameter is optional, you can omit it and type the command as `Format-List *`.</span></span> <span data-ttu-id="12551-134">`Format-List` skickar automatiskt resultaten till standard-utdata-cmdleten för visning.</span><span class="sxs-lookup"><span data-stu-id="12551-134">`Format-List` automatically sends the results to the default output cmdlet for display.</span></span>

### <span data-ttu-id="12551-135">Exempel 5: fel sökning av format fel</span><span class="sxs-lookup"><span data-stu-id="12551-135">Example 5: Troubleshooting format errors</span></span>

<span data-ttu-id="12551-136">I följande exempel visas resultatet av att lägga till **DisplayError** -eller **ShowError** -parametrarna med ett uttryck.</span><span class="sxs-lookup"><span data-stu-id="12551-136">The following examples show of the results of adding the **DisplayError** or **ShowError** parameters with an expression.</span></span>

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

## <span data-ttu-id="12551-137">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="12551-137">PARAMETERS</span></span>

### <span data-ttu-id="12551-138">– DisplayError</span><span class="sxs-lookup"><span data-stu-id="12551-138">-DisplayError</span></span>

<span data-ttu-id="12551-139">Anger att denna cmdlet visar fel på kommando raden.</span><span class="sxs-lookup"><span data-stu-id="12551-139">Indicates that this cmdlet displays errors at the command line.</span></span> <span data-ttu-id="12551-140">Den här parametern används sällan, men kan användas som ett fel söknings stöd när du formaterar uttryck i ett `Format-List` kommando, och uttrycken verkar inte fungera.</span><span class="sxs-lookup"><span data-stu-id="12551-140">This parameter is rarely used, but can be used as a debugging aid when you are formatting expressions in a `Format-List` command, and the expressions do not appear to be working.</span></span>

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

### <span data-ttu-id="12551-141">– Expandera</span><span class="sxs-lookup"><span data-stu-id="12551-141">-Expand</span></span>

<span data-ttu-id="12551-142">Anger det formaterade samlings objektet, samt objekt i samlingen.</span><span class="sxs-lookup"><span data-stu-id="12551-142">Specifies the formatted collection object, as well as the objects in the collection.</span></span> <span data-ttu-id="12551-143">Den här parametern är utformad för att formatera objekt som har stöd för ICollection-gränssnittet (system. Collection).</span><span class="sxs-lookup"><span data-stu-id="12551-143">This parameter is designed to format objects that support the ICollection (System.Collections) interface.</span></span> <span data-ttu-id="12551-144">Standardvärdet är EnumOnly.</span><span class="sxs-lookup"><span data-stu-id="12551-144">The default value is EnumOnly.</span></span> <span data-ttu-id="12551-145">De acceptabla värdena för den här parametern är:</span><span class="sxs-lookup"><span data-stu-id="12551-145">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="12551-146">EnumOnly.</span><span class="sxs-lookup"><span data-stu-id="12551-146">EnumOnly.</span></span> <span data-ttu-id="12551-147">Visar egenskaperna för objekten i samlingen.</span><span class="sxs-lookup"><span data-stu-id="12551-147">Displays the properties of the objects in the collection.</span></span>
- <span data-ttu-id="12551-148">CoreOnly.</span><span class="sxs-lookup"><span data-stu-id="12551-148">CoreOnly.</span></span> <span data-ttu-id="12551-149">Visar egenskaperna för objektet samling.</span><span class="sxs-lookup"><span data-stu-id="12551-149">Displays the properties of the collection object.</span></span>
- <span data-ttu-id="12551-150">Dubbelrikta.</span><span class="sxs-lookup"><span data-stu-id="12551-150">Both.</span></span> <span data-ttu-id="12551-151">Visar egenskaperna för samlings objekt och egenskaper för objekt i samlingen.</span><span class="sxs-lookup"><span data-stu-id="12551-151">Displays the properties of the collection object and the properties of objects in the collection.</span></span>

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

### <span data-ttu-id="12551-152">-Force</span><span class="sxs-lookup"><span data-stu-id="12551-152">-Force</span></span>

<span data-ttu-id="12551-153">Anger att denna cmdlet visar all fel information.</span><span class="sxs-lookup"><span data-stu-id="12551-153">Indicates that this cmdlet displays all of the error information.</span></span> <span data-ttu-id="12551-154">Används med parametern **DisplayError** eller **ShowError** .</span><span class="sxs-lookup"><span data-stu-id="12551-154">Use with the **DisplayError** or **ShowError** parameter.</span></span> <span data-ttu-id="12551-155">Som standard visas endast en del fel information när ett fel objekt skrivs till fel-eller visnings strömmar.</span><span class="sxs-lookup"><span data-stu-id="12551-155">By default, when an error object is written to the error or display streams, only some of the error information is displayed.</span></span>

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

### <span data-ttu-id="12551-156">– GroupBy</span><span class="sxs-lookup"><span data-stu-id="12551-156">-GroupBy</span></span>

<span data-ttu-id="12551-157">Anger utdata i grupper baserat på en delad egenskap eller ett värde.</span><span class="sxs-lookup"><span data-stu-id="12551-157">Specifies the output in groups based on a shared property or value.</span></span> <span data-ttu-id="12551-158">Ange ett uttryck eller en egenskap för utdata.</span><span class="sxs-lookup"><span data-stu-id="12551-158">Enter an expression or a property of the output.</span></span>

<span data-ttu-id="12551-159">Värdet för **groupby** -parametern kan vara en ny beräknad egenskap.</span><span class="sxs-lookup"><span data-stu-id="12551-159">The value of the **GroupBy** parameter can be a new calculated property.</span></span> <span data-ttu-id="12551-160">Den beräknade egenskapen kan vara ett skript block eller en hash-tabell.</span><span class="sxs-lookup"><span data-stu-id="12551-160">The calculated property can be a script block or a hash table.</span></span> <span data-ttu-id="12551-161">Giltiga nyckel/värde-par är:</span><span class="sxs-lookup"><span data-stu-id="12551-161">Valid key-value pairs are:</span></span>

- <span data-ttu-id="12551-162">Namn (eller etikett)- `<string>`</span><span class="sxs-lookup"><span data-stu-id="12551-162">Name (or Label) - `<string>`</span></span>
- <span data-ttu-id="12551-163">Uttryck- `<string>` eller `<script block>`</span><span class="sxs-lookup"><span data-stu-id="12551-163">Expression - `<string>` or `<script block>`</span></span>
- <span data-ttu-id="12551-164">FormatString `<string>`</span><span class="sxs-lookup"><span data-stu-id="12551-164">FormatString - `<string>`</span></span>

<span data-ttu-id="12551-165">Mer information finns i [about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md).</span><span class="sxs-lookup"><span data-stu-id="12551-165">For more information, see [about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md).</span></span>

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

### <span data-ttu-id="12551-166">– InputObject</span><span class="sxs-lookup"><span data-stu-id="12551-166">-InputObject</span></span>

<span data-ttu-id="12551-167">Anger de objekt som ska formateras.</span><span class="sxs-lookup"><span data-stu-id="12551-167">Specifies the objects to be formatted.</span></span> <span data-ttu-id="12551-168">Ange en variabel som innehåller objekten eller Skriv ett kommando eller uttryck som hämtar objekten.</span><span class="sxs-lookup"><span data-stu-id="12551-168">Enter a variable that contains the objects or type a command or expression that gets the objects.</span></span>

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

### <span data-ttu-id="12551-169">– Egenskap</span><span class="sxs-lookup"><span data-stu-id="12551-169">-Property</span></span>

<span data-ttu-id="12551-170">Anger objekt egenskaperna som visas i visningen och i vilken ordning de visas.</span><span class="sxs-lookup"><span data-stu-id="12551-170">Specifies the object properties that appear in the display and the order in which they appear.</span></span>
<span data-ttu-id="12551-171">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="12551-171">Wildcards are permitted.</span></span>

<span data-ttu-id="12551-172">Om du utelämnar den här parametern beror egenskaperna som visas i vyn på det objekt som visas.</span><span class="sxs-lookup"><span data-stu-id="12551-172">If you omit this parameter, the properties that appear in the display depend on the object being displayed.</span></span> <span data-ttu-id="12551-173">Parameter namnet "Property" är valfritt.</span><span class="sxs-lookup"><span data-stu-id="12551-173">The parameter name "Property" is optional.</span></span> <span data-ttu-id="12551-174">Du kan inte använda **egenskapen** och **Visa** parametrar i samma kommando.</span><span class="sxs-lookup"><span data-stu-id="12551-174">You cannot use the **Property** and **View** parameters in the same command.</span></span>

<span data-ttu-id="12551-175">Värdet för **egenskaps** parametern kan vara en ny beräknad egenskap.</span><span class="sxs-lookup"><span data-stu-id="12551-175">The value of the **Property** parameter can be a new calculated property.</span></span> <span data-ttu-id="12551-176">Den beräknade egenskapen kan vara ett skript block eller en hash-tabell.</span><span class="sxs-lookup"><span data-stu-id="12551-176">The calculated property can be a script block or a hash table.</span></span> <span data-ttu-id="12551-177">Giltiga nyckel/värde-par är:</span><span class="sxs-lookup"><span data-stu-id="12551-177">Valid key-value pairs are:</span></span>

- <span data-ttu-id="12551-178">Namn (eller etikett)- `<string>`</span><span class="sxs-lookup"><span data-stu-id="12551-178">Name (or Label) - `<string>`</span></span>
- <span data-ttu-id="12551-179">Uttryck- `<string>` eller `<script block>`</span><span class="sxs-lookup"><span data-stu-id="12551-179">Expression - `<string>` or `<script block>`</span></span>
- <span data-ttu-id="12551-180">FormatString `<string>`</span><span class="sxs-lookup"><span data-stu-id="12551-180">FormatString - `<string>`</span></span>

<span data-ttu-id="12551-181">Mer information finns i [about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md).</span><span class="sxs-lookup"><span data-stu-id="12551-181">For more information, see [about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md).</span></span>

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

### <span data-ttu-id="12551-182">– ShowError</span><span class="sxs-lookup"><span data-stu-id="12551-182">-ShowError</span></span>

<span data-ttu-id="12551-183">Anger att cmdleten skickar fel via pipelinen.</span><span class="sxs-lookup"><span data-stu-id="12551-183">Indicates that the cmdlet sends errors through the pipeline.</span></span> <span data-ttu-id="12551-184">Den här parametern används sällan, men kan användas som ett fel söknings stöd när du formaterar uttryck i ett `Format-List` kommando, och uttrycken verkar inte fungera.</span><span class="sxs-lookup"><span data-stu-id="12551-184">This parameter is rarely used, but can be used as a debugging aid when you are formatting expressions in a `Format-List` command, and the expressions do not appear to be working.</span></span>

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

### <span data-ttu-id="12551-185">– Visa</span><span class="sxs-lookup"><span data-stu-id="12551-185">-View</span></span>

<span data-ttu-id="12551-186">Anger namnet på ett alternativt List format eller en vy.</span><span class="sxs-lookup"><span data-stu-id="12551-186">Specifies the name of an alternate list format or view.</span></span> <span data-ttu-id="12551-187">Du kan inte använda **egenskapen** och **Visa** parametrar i samma kommando.</span><span class="sxs-lookup"><span data-stu-id="12551-187">You cannot use the **Property** and **View** parameters in the same command.</span></span>

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

### <span data-ttu-id="12551-188">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="12551-188">CommonParameters</span></span>

<span data-ttu-id="12551-189">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="12551-189">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="12551-190">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="12551-190">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="12551-191">INDATA</span><span class="sxs-lookup"><span data-stu-id="12551-191">INPUTS</span></span>

### <span data-ttu-id="12551-192">System. Management. Automation. PSObject</span><span class="sxs-lookup"><span data-stu-id="12551-192">System.Management.Automation.PSObject</span></span>

<span data-ttu-id="12551-193">Du kan skicka vidare alla objekt till `Format-List` .</span><span class="sxs-lookup"><span data-stu-id="12551-193">You can pipe any object to `Format-List`.</span></span>

## <span data-ttu-id="12551-194">UTDATA</span><span class="sxs-lookup"><span data-stu-id="12551-194">OUTPUTS</span></span>

### <span data-ttu-id="12551-195">Microsoft. PowerShell. commands. Internal. format</span><span class="sxs-lookup"><span data-stu-id="12551-195">Microsoft.PowerShell.Commands.Internal.Format</span></span>

<span data-ttu-id="12551-196">`Format-List` Returnerar de format objekt som representerar listan.</span><span class="sxs-lookup"><span data-stu-id="12551-196">`Format-List` returns the format objects that represent the list.</span></span>

## <span data-ttu-id="12551-197">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="12551-197">NOTES</span></span>

<span data-ttu-id="12551-198">Du kan också referera till Format-List med det inbyggda aliaset, FL.</span><span class="sxs-lookup"><span data-stu-id="12551-198">You can also refer to Format-List by its built-in alias, FL.</span></span> <span data-ttu-id="12551-199">Mer information finns i [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md).</span><span class="sxs-lookup"><span data-stu-id="12551-199">For more information, see [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md).</span></span>

<span data-ttu-id="12551-200">Format-cmdletarna, till exempel `Format-List` , ordnar de data som ska visas men inte visar dem.</span><span class="sxs-lookup"><span data-stu-id="12551-200">The format cmdlets, such as `Format-List`, arrange the data to be displayed but do not display it.</span></span>
<span data-ttu-id="12551-201">Data visas i utmatnings funktionerna i PowerShell och av de cmdletar som innehåller verbet (out-cmdletarna), till exempel `Out-Host` eller `Out-File` .</span><span class="sxs-lookup"><span data-stu-id="12551-201">The data is displayed by the output features of PowerShell and by the cmdlets that contain the Out verb (the Out cmdlets), such as `Out-Host` or `Out-File`.</span></span>

<span data-ttu-id="12551-202">Om du inte använder en format-cmdlet, använder PowerShell standardformat för varje objekt som visas.</span><span class="sxs-lookup"><span data-stu-id="12551-202">If you do not use a format cmdlet, PowerShell applies that default format for each object that it displays.</span></span>

<span data-ttu-id="12551-203">Parametern **groupby** förutsätter att objekten sorteras.</span><span class="sxs-lookup"><span data-stu-id="12551-203">The **GroupBy** parameter assumes that the objects are sorted.</span></span> <span data-ttu-id="12551-204">Använd Sort-Object innan `Format-List` du använder för att gruppera objekten.</span><span class="sxs-lookup"><span data-stu-id="12551-204">Use Sort-Object before using `Format-List` to group the objects.</span></span>

<span data-ttu-id="12551-205">Med parametern **Visa** kan du ange ett alternativt format för tabellen.</span><span class="sxs-lookup"><span data-stu-id="12551-205">The **View** parameter lets you specify an alternate format for the table.</span></span> <span data-ttu-id="12551-206">Du kan använda de vyer som definierats i `*.format.PS1XML` filerna i PowerShell-katalogen, eller så kan du skapa egna vyer i nya PS1XML-filer och använda cmdleten Update-FormatData för att inkludera dem i PowerShell.</span><span class="sxs-lookup"><span data-stu-id="12551-206">You can use the views defined in the `*.format.PS1XML` files in the PowerShell directory, or you can create your own views in new PS1XML files and use the Update-FormatData cmdlet to include them in PowerShell.</span></span>

<span data-ttu-id="12551-207">Den alternativa vyn för parametern **View** måste använda List formatet, annars Miss lyckas kommandot.</span><span class="sxs-lookup"><span data-stu-id="12551-207">The alternate view for the **View** parameter must use the list format, otherwise, the command fails.</span></span> <span data-ttu-id="12551-208">Om den alternativa vyn är en tabell använder du `Format-Table` .</span><span class="sxs-lookup"><span data-stu-id="12551-208">If the alternate view is a table, use `Format-Table`.</span></span> <span data-ttu-id="12551-209">Om den alternativa vyn inte är en lista eller en tabell använder du `Format-Custom` .</span><span class="sxs-lookup"><span data-stu-id="12551-209">If the alternate view is not a list or a table, use `Format-Custom`.</span></span>

## <span data-ttu-id="12551-210">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="12551-210">RELATED LINKS</span></span>

[<span data-ttu-id="12551-211">about_Calculated_Properties</span><span class="sxs-lookup"><span data-stu-id="12551-211">about_Calculated_Properties</span></span>](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md)

[<span data-ttu-id="12551-212">Format-Custom</span><span class="sxs-lookup"><span data-stu-id="12551-212">Format-Custom</span></span>](Format-Custom.md)

[<span data-ttu-id="12551-213">Format-Hex</span><span class="sxs-lookup"><span data-stu-id="12551-213">Format-Hex</span></span>](Format-Hex.md)

[<span data-ttu-id="12551-214">Format-Table</span><span class="sxs-lookup"><span data-stu-id="12551-214">Format-Table</span></span>](Format-Table.md)

[<span data-ttu-id="12551-215">Format-Wide</span><span class="sxs-lookup"><span data-stu-id="12551-215">Format-Wide</span></span>](Format-Wide.md)
