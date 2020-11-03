---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 08/10/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/format-wide?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Format-Wide
ms.openlocfilehash: eed3ba1982792cc5675b7343525e1182f9e6a420
ms.sourcegitcommit: 9a6b6714ded4edb5119f1b82a253608018ea6b98
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/10/2020
ms.locfileid: "93269127"
---
# <span data-ttu-id="63cb2-103">Format-Wide</span><span class="sxs-lookup"><span data-stu-id="63cb2-103">Format-Wide</span></span>

## <span data-ttu-id="63cb2-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="63cb2-104">SYNOPSIS</span></span>
<span data-ttu-id="63cb2-105">Formaterar objekt som en bred tabell som endast visar en egenskap för varje objekt.</span><span class="sxs-lookup"><span data-stu-id="63cb2-105">Formats objects as a wide table that displays only one property of each object.</span></span>

## <span data-ttu-id="63cb2-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="63cb2-106">SYNTAX</span></span>

```
Format-Wide [[-Property] <Object>] [-AutoSize] [-Column <int>] [-GroupBy <Object>] [-View <string>]
  [-ShowError] [-DisplayError] [-Force] [-Expand <string>] [-InputObject <psobject>]
  [<CommonParameters>]
```

## <span data-ttu-id="63cb2-107">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="63cb2-107">DESCRIPTION</span></span>

<span data-ttu-id="63cb2-108">`Format-Wide`Cmdleten formaterar objekt som en bred tabell som endast visar en egenskap för varje objekt.</span><span class="sxs-lookup"><span data-stu-id="63cb2-108">The `Format-Wide` cmdlet formats objects as a wide table that displays only one property of each object.</span></span> <span data-ttu-id="63cb2-109">Du kan använda **egenskaps** parametern för att avgöra vilken egenskap som visas.</span><span class="sxs-lookup"><span data-stu-id="63cb2-109">You can use the **Property** parameter to determine which property is displayed.</span></span>

## <span data-ttu-id="63cb2-110">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="63cb2-110">EXAMPLES</span></span>

### <span data-ttu-id="63cb2-111">Exempel 1: formatera namn på filer i den aktuella katalogen</span><span class="sxs-lookup"><span data-stu-id="63cb2-111">Example 1: Format names of files in the current directory</span></span>

<span data-ttu-id="63cb2-112">Det här kommandot visar namnen på filer i den aktuella katalogen i tre kolumner på skärmen.</span><span class="sxs-lookup"><span data-stu-id="63cb2-112">This command displays the names of files in the current directory in three columns across the screen.</span></span>

```powershell
Get-ChildItem | Format-Wide -Column 3
```

<span data-ttu-id="63cb2-113">Get-ChildItem-cmdlet: en hämtar objekt som representerar varje fil i katalogen.</span><span class="sxs-lookup"><span data-stu-id="63cb2-113">The Get-ChildItem cmdlet gets objects representing each file in the directory.</span></span> <span data-ttu-id="63cb2-114">Pipeline-operatorn (|) skickar fil objekt via pipelinen till `Format-Wide` , som formaterar dem för utdata.</span><span class="sxs-lookup"><span data-stu-id="63cb2-114">The pipeline operator (|) passes the file objects through the pipeline to `Format-Wide`, which formats them for output.</span></span> <span data-ttu-id="63cb2-115">**Kolumn** parametern anger antalet kolumner.</span><span class="sxs-lookup"><span data-stu-id="63cb2-115">The **Column** parameter specifies the number of columns.</span></span>

### <span data-ttu-id="63cb2-116">Exempel 2: formatera namn på register nycklar</span><span class="sxs-lookup"><span data-stu-id="63cb2-116">Example 2: Format names of registry keys</span></span>

<span data-ttu-id="63cb2-117">Det här kommandot visar namnen på register nycklar i HKEY_CURRENT_USER\Software\Microsoft nyckeln.</span><span class="sxs-lookup"><span data-stu-id="63cb2-117">This command displays the names of registry keys in the HKEY_CURRENT_USER\Software\Microsoft key.</span></span>

```powershell
Get-ChildItem HKCU:\software\microsoft | Format-Wide -Property pschildname -AutoSize
```

<span data-ttu-id="63cb2-118">Get-ChildItem cmdleten hämtar objekt som representerar nycklarna.</span><span class="sxs-lookup"><span data-stu-id="63cb2-118">The Get-ChildItem cmdlet gets objects representing the keys.</span></span> <span data-ttu-id="63cb2-119">Sökvägen anges som HKCU:, en av de enheter som exponeras av PowerShell-registernyckeln, följt av nyckel Sök vägen.</span><span class="sxs-lookup"><span data-stu-id="63cb2-119">The path is specified as HKCU:, one of the drives exposed by the PowerShell Registry provider, followed by the key path.</span></span> <span data-ttu-id="63cb2-120">Pipeline-operatorn (|) skickar register nyckel objekt via pipelinen till `Format-Wide` , som formaterar dem för utdata.</span><span class="sxs-lookup"><span data-stu-id="63cb2-120">The pipeline operator (|) passes the registry key objects through the pipeline to `Format-Wide`, which formats them for output.</span></span> <span data-ttu-id="63cb2-121">**Egenskaps** parametern anger namnet på egenskapen och parametern **AutoSize** justerar kolumnerna för läsbarhet.</span><span class="sxs-lookup"><span data-stu-id="63cb2-121">The **Property** parameter specifies the name of the property, and the **AutoSize** parameter adjusts the columns for readability.</span></span>

### <span data-ttu-id="63cb2-122">Exempel 3: Felsöka format fel</span><span class="sxs-lookup"><span data-stu-id="63cb2-122">Example 3: Troubleshooting format errors</span></span>

<span data-ttu-id="63cb2-123">I följande exempel visas resultatet av att lägga till **DisplayError** -eller **ShowError** -parametrarna med ett uttryck.</span><span class="sxs-lookup"><span data-stu-id="63cb2-123">The following examples show of the results of adding the **DisplayError** or **ShowError** parameters with an expression.</span></span>

```powershell
PS /> Get-Date | Format-Wide { $_ / $null } -DisplayError


#ERR

PS /> Get-Date | Format-Wide { $_ / $null } -ShowError


Failed to evaluate expression " $_ / $null ".
+ CategoryInfo          : InvalidArgument: (12/21/2018 8:18:01 AM:PSObject) [], RuntimeException
+ FullyQualifiedErrorId : PSPropertyExpressionError
```

## <span data-ttu-id="63cb2-124">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="63cb2-124">PARAMETERS</span></span>

### <span data-ttu-id="63cb2-125">-AutoSize</span><span class="sxs-lookup"><span data-stu-id="63cb2-125">-AutoSize</span></span>

<span data-ttu-id="63cb2-126">Justerar kolumn storlek och antal kolumner baserat på data bredden.</span><span class="sxs-lookup"><span data-stu-id="63cb2-126">Adjusts the column size and number of columns based on the width of the data.</span></span> <span data-ttu-id="63cb2-127">Som standard bestäms kolumn storleken och antalet av vyn.</span><span class="sxs-lookup"><span data-stu-id="63cb2-127">By default, the column size and number are determined by the view.</span></span> <span data-ttu-id="63cb2-128">Du kan inte använda **AutoSize** -och **Column** -parametrarna i samma kommando.</span><span class="sxs-lookup"><span data-stu-id="63cb2-128">You cannot use the **AutoSize** and **Column** parameters in the same command.</span></span>

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

### <span data-ttu-id="63cb2-129">-Kolumn</span><span class="sxs-lookup"><span data-stu-id="63cb2-129">-Column</span></span>

<span data-ttu-id="63cb2-130">Anger antalet kolumner i visningen.</span><span class="sxs-lookup"><span data-stu-id="63cb2-130">Specifies the number of columns in the display.</span></span> <span data-ttu-id="63cb2-131">Du kan inte använda **AutoSize** -och **Column** -parametrarna i samma kommando.</span><span class="sxs-lookup"><span data-stu-id="63cb2-131">You cannot use the **AutoSize** and **Column** parameters in the same command.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="63cb2-132">– DisplayError</span><span class="sxs-lookup"><span data-stu-id="63cb2-132">-DisplayError</span></span>

<span data-ttu-id="63cb2-133">Visar fel på kommando raden.</span><span class="sxs-lookup"><span data-stu-id="63cb2-133">Displays errors at the command line.</span></span> <span data-ttu-id="63cb2-134">Den här parametern används sällan, men kan användas som ett fel söknings stöd när du formaterar uttryck i ett `Format-Wide` kommando, och uttrycken verkar inte fungera.</span><span class="sxs-lookup"><span data-stu-id="63cb2-134">This parameter is rarely used, but can be used as a debugging aid when you are formatting expressions in a `Format-Wide` command, and the expressions do not appear to be working.</span></span>

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

### <span data-ttu-id="63cb2-135">– Expandera</span><span class="sxs-lookup"><span data-stu-id="63cb2-135">-Expand</span></span>

<span data-ttu-id="63cb2-136">Formaterar samlings objekt och objekt i samlingen.</span><span class="sxs-lookup"><span data-stu-id="63cb2-136">Formats the collection object, as well as the objects in the collection.</span></span> <span data-ttu-id="63cb2-137">Den här parametern är utformad för att formatera objekt som har stöd för ICollection-gränssnittet (system. Collection).</span><span class="sxs-lookup"><span data-stu-id="63cb2-137">This parameter is designed to format objects that support the ICollection (System.Collections) interface.</span></span> <span data-ttu-id="63cb2-138">Standardvärdet är **EnumOnly**.</span><span class="sxs-lookup"><span data-stu-id="63cb2-138">The default value is **EnumOnly**.</span></span>

<span data-ttu-id="63cb2-139">Giltiga värden är:</span><span class="sxs-lookup"><span data-stu-id="63cb2-139">Valid values are:</span></span>

- <span data-ttu-id="63cb2-140">EnumOnly: visar egenskaperna för objekten i samlingen.</span><span class="sxs-lookup"><span data-stu-id="63cb2-140">EnumOnly: Displays the properties of the objects in the collection.</span></span>
- <span data-ttu-id="63cb2-141">CoreOnly: visar egenskaperna för objektet samling.</span><span class="sxs-lookup"><span data-stu-id="63cb2-141">CoreOnly: Displays the properties of the collection object.</span></span>
- <span data-ttu-id="63cb2-142">Båda: visar egenskaperna för Collection-objektet och egenskaperna för objekt i samlingen.</span><span class="sxs-lookup"><span data-stu-id="63cb2-142">Both: Displays the properties of the collection object and the properties of objects in the collection.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values: CoreOnly, EnumOnly, Both

Required: False
Position: Named
Default value: EnumOnly
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="63cb2-143">-Force</span><span class="sxs-lookup"><span data-stu-id="63cb2-143">-Force</span></span>

<span data-ttu-id="63cb2-144">Anger att denna cmdlet åsidosätter begränsningar som hindrar kommandot från att lyckas, bara för att ändringarna inte äventyrar säkerheten.</span><span class="sxs-lookup"><span data-stu-id="63cb2-144">Indicates that this cmdlet overrides restrictions that prevent the command from succeeding, just so the changes do not compromise security.</span></span> <span data-ttu-id="63cb2-145">**Tvinga** åsidosätter till exempel det skrivskyddade attributet eller skapa kataloger för att slutföra en fil Sök väg, men kommer inte att försöka ändra fil behörigheter.</span><span class="sxs-lookup"><span data-stu-id="63cb2-145">For example, **Force** will override the read-only attribute or create directories to complete a file path, but it will not attempt to change file permissions.</span></span>

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

### <span data-ttu-id="63cb2-146">– GroupBy</span><span class="sxs-lookup"><span data-stu-id="63cb2-146">-GroupBy</span></span>

<span data-ttu-id="63cb2-147">Formaterar utdata i grupper baserat på en delad egenskap eller ett värde.</span><span class="sxs-lookup"><span data-stu-id="63cb2-147">Formats the output in groups based on a shared property or value.</span></span> <span data-ttu-id="63cb2-148">Ange ett uttryck eller en egenskap för utdata.</span><span class="sxs-lookup"><span data-stu-id="63cb2-148">Enter an expression or a property of the output.</span></span>

<span data-ttu-id="63cb2-149">Värdet för **groupby** -parametern kan vara en ny beräknad egenskap.</span><span class="sxs-lookup"><span data-stu-id="63cb2-149">The value of the **GroupBy** parameter can be a new calculated property.</span></span> <span data-ttu-id="63cb2-150">Den beräknade egenskapen kan vara ett skript block eller en hash-tabell.</span><span class="sxs-lookup"><span data-stu-id="63cb2-150">The calculated property can be a script block or a hash table.</span></span> <span data-ttu-id="63cb2-151">Giltiga nyckel/värde-par är:</span><span class="sxs-lookup"><span data-stu-id="63cb2-151">Valid key-value pairs are:</span></span>

- <span data-ttu-id="63cb2-152">Namn (eller etikett)- `<string>`</span><span class="sxs-lookup"><span data-stu-id="63cb2-152">Name (or Label) - `<string>`</span></span>
- <span data-ttu-id="63cb2-153">Uttryck- `<string>` eller `<script block>`</span><span class="sxs-lookup"><span data-stu-id="63cb2-153">Expression - `<string>` or `<script block>`</span></span>
- <span data-ttu-id="63cb2-154">FormatString `<string>`</span><span class="sxs-lookup"><span data-stu-id="63cb2-154">FormatString - `<string>`</span></span>

<span data-ttu-id="63cb2-155">Mer information finns i [about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md).</span><span class="sxs-lookup"><span data-stu-id="63cb2-155">For more information, see [about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md).</span></span>

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

### <span data-ttu-id="63cb2-156">– InputObject</span><span class="sxs-lookup"><span data-stu-id="63cb2-156">-InputObject</span></span>

<span data-ttu-id="63cb2-157">Anger de objekt som ska formateras.</span><span class="sxs-lookup"><span data-stu-id="63cb2-157">Specifies the objects to format.</span></span> <span data-ttu-id="63cb2-158">Ange en variabel som innehåller objekten eller Skriv ett kommando eller uttryck som hämtar objekten.</span><span class="sxs-lookup"><span data-stu-id="63cb2-158">Enter a variable that contains the objects, or type a command or expression that gets the objects.</span></span>

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

### <span data-ttu-id="63cb2-159">– Egenskap</span><span class="sxs-lookup"><span data-stu-id="63cb2-159">-Property</span></span>

<span data-ttu-id="63cb2-160">Anger objekt egenskaperna som visas i visningen och i vilken ordning de visas.</span><span class="sxs-lookup"><span data-stu-id="63cb2-160">Specifies the object properties that appear in the display and the order in which they appear.</span></span>
<span data-ttu-id="63cb2-161">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="63cb2-161">Wildcards are permitted.</span></span>

<span data-ttu-id="63cb2-162">Om du utelämnar den här parametern beror egenskaperna som visas i vyn på det objekt som visas.</span><span class="sxs-lookup"><span data-stu-id="63cb2-162">If you omit this parameter, the properties that appear in the display depend on the object being displayed.</span></span> <span data-ttu-id="63cb2-163">Parameter namnet "Property" är valfritt.</span><span class="sxs-lookup"><span data-stu-id="63cb2-163">The parameter name "Property" is optional.</span></span> <span data-ttu-id="63cb2-164">Du kan inte använda **egenskapen** och **Visa** parametrar i samma kommando.</span><span class="sxs-lookup"><span data-stu-id="63cb2-164">You cannot use the **Property** and **View** parameters in the same command.</span></span>

<span data-ttu-id="63cb2-165">Värdet för **egenskaps** parametern kan vara en ny beräknad egenskap.</span><span class="sxs-lookup"><span data-stu-id="63cb2-165">The value of the **Property** parameter can be a new calculated property.</span></span> <span data-ttu-id="63cb2-166">Den beräknade egenskapen kan vara ett skript block eller en hash-tabell.</span><span class="sxs-lookup"><span data-stu-id="63cb2-166">The calculated property can be a script block or a hash table.</span></span> <span data-ttu-id="63cb2-167">Giltiga nyckel/värde-par är:</span><span class="sxs-lookup"><span data-stu-id="63cb2-167">Valid key-value pairs are:</span></span>

- <span data-ttu-id="63cb2-168">Uttryck- `<string>` eller `<script block>`</span><span class="sxs-lookup"><span data-stu-id="63cb2-168">Expression - `<string>` or `<script block>`</span></span>
- <span data-ttu-id="63cb2-169">FormatString `<string>`</span><span class="sxs-lookup"><span data-stu-id="63cb2-169">FormatString - `<string>`</span></span>

<span data-ttu-id="63cb2-170">Mer information finns i [about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md).</span><span class="sxs-lookup"><span data-stu-id="63cb2-170">For more information, see [about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md).</span></span>

```yaml
Type: System.Object
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="63cb2-171">– ShowError</span><span class="sxs-lookup"><span data-stu-id="63cb2-171">-ShowError</span></span>

<span data-ttu-id="63cb2-172">Skickar fel via pipelinen.</span><span class="sxs-lookup"><span data-stu-id="63cb2-172">Sends errors through the pipeline.</span></span> <span data-ttu-id="63cb2-173">Den här parametern används sällan, men kan användas som ett fel söknings stöd när du formaterar uttryck i ett `Format-Wide` kommando, och uttrycken verkar inte fungera.</span><span class="sxs-lookup"><span data-stu-id="63cb2-173">This parameter is rarely used, but can be used as a debugging aid when you are formatting expressions in a `Format-Wide` command, and the expressions do not appear to be working.</span></span>

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

### <span data-ttu-id="63cb2-174">– Visa</span><span class="sxs-lookup"><span data-stu-id="63cb2-174">-View</span></span>

<span data-ttu-id="63cb2-175">Anger namnet på ett alternativt tabell format eller en vy.</span><span class="sxs-lookup"><span data-stu-id="63cb2-175">Specifies the name of an alternate table format or view.</span></span> <span data-ttu-id="63cb2-176">Du kan inte använda **egenskapen** och **Visa** parametrar i samma kommando.</span><span class="sxs-lookup"><span data-stu-id="63cb2-176">You cannot use the **Property** and **View** parameters in the same command.</span></span>

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

### <span data-ttu-id="63cb2-177">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="63cb2-177">CommonParameters</span></span>

<span data-ttu-id="63cb2-178">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="63cb2-178">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="63cb2-179">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="63cb2-179">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="63cb2-180">INDATA</span><span class="sxs-lookup"><span data-stu-id="63cb2-180">INPUTS</span></span>

### <span data-ttu-id="63cb2-181">System. Management. Automation. PSObject</span><span class="sxs-lookup"><span data-stu-id="63cb2-181">System.Management.Automation.PSObject</span></span>

<span data-ttu-id="63cb2-182">Du kan skicka vidare alla objekt till `Format-Wide` .</span><span class="sxs-lookup"><span data-stu-id="63cb2-182">You can pipe any object to `Format-Wide`.</span></span>

## <span data-ttu-id="63cb2-183">UTDATA</span><span class="sxs-lookup"><span data-stu-id="63cb2-183">OUTPUTS</span></span>

### <span data-ttu-id="63cb2-184">Microsoft. PowerShell. commands. Internal. format</span><span class="sxs-lookup"><span data-stu-id="63cb2-184">Microsoft.PowerShell.Commands.Internal.Format</span></span>

<span data-ttu-id="63cb2-185">`Format-Wide` Returnerar format objekt som representerar tabellen.</span><span class="sxs-lookup"><span data-stu-id="63cb2-185">`Format-Wide` returns format objects that represent the table.</span></span>

## <span data-ttu-id="63cb2-186">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="63cb2-186">NOTES</span></span>

<span data-ttu-id="63cb2-187">Du kan också referera till `Format-Wide` med dess inbyggda alias `fw` .</span><span class="sxs-lookup"><span data-stu-id="63cb2-187">You can also refer to `Format-Wide` by its built-in alias, `fw`.</span></span> <span data-ttu-id="63cb2-188">Mer information finns i [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md).</span><span class="sxs-lookup"><span data-stu-id="63cb2-188">For more information, see [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md).</span></span>

<span data-ttu-id="63cb2-189">Parametern **groupby** förutsätter att objekten sorteras.</span><span class="sxs-lookup"><span data-stu-id="63cb2-189">The **GroupBy** parameter assumes that the objects are sorted.</span></span> <span data-ttu-id="63cb2-190">Använd `Sort-Object` innan `Format-Custom` du använder för att gruppera objekten.</span><span class="sxs-lookup"><span data-stu-id="63cb2-190">Use `Sort-Object` before using `Format-Custom` to group the objects.</span></span>

<span data-ttu-id="63cb2-191">Med parametern **Visa** kan du ange ett alternativt format för tabellen.</span><span class="sxs-lookup"><span data-stu-id="63cb2-191">The **View** parameter lets you specify an alternate format for the table.</span></span> <span data-ttu-id="63cb2-192">Du kan använda de vyer som definierats i `*.format.PS1XML` filerna i PowerShell-katalogen, eller så kan du skapa egna vyer i nya PS1XML-filer och använda `Update-FormatData` cmdleten för att inkludera dem i PowerShell.</span><span class="sxs-lookup"><span data-stu-id="63cb2-192">You can use the views defined in the `*.format.PS1XML` files in the PowerShell directory or you can create your own views in new PS1XML files and use the `Update-FormatData` cmdlet to include them in PowerShell.</span></span>

<span data-ttu-id="63cb2-193">Den alternativa vyn för parametern **View** måste använda tabell format; annars Miss lyckas kommandot.</span><span class="sxs-lookup"><span data-stu-id="63cb2-193">The alternate view for the **View** parameter must use table format; if it does not, the command fails.</span></span> <span data-ttu-id="63cb2-194">Om den alternativa vyn är en lista använder du `Format-List` .</span><span class="sxs-lookup"><span data-stu-id="63cb2-194">If the alternate view is a list, use `Format-List`.</span></span> <span data-ttu-id="63cb2-195">Om den alternativa vyn varken är en lista eller en tabell använder du format-Custom.</span><span class="sxs-lookup"><span data-stu-id="63cb2-195">If the alternate view is neither a list nor a table, use Format-Custom.</span></span>

## <span data-ttu-id="63cb2-196">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="63cb2-196">RELATED LINKS</span></span>

[<span data-ttu-id="63cb2-197">about_Calculated_Properties</span><span class="sxs-lookup"><span data-stu-id="63cb2-197">about_Calculated_Properties</span></span>](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md)

[<span data-ttu-id="63cb2-198">Format-Custom</span><span class="sxs-lookup"><span data-stu-id="63cb2-198">Format-Custom</span></span>](Format-Custom.md)

[<span data-ttu-id="63cb2-199">Format-Hex</span><span class="sxs-lookup"><span data-stu-id="63cb2-199">Format-Hex</span></span>](Format-Hex.md)

[<span data-ttu-id="63cb2-200">Format-List</span><span class="sxs-lookup"><span data-stu-id="63cb2-200">Format-List</span></span>](Format-List.md)

[<span data-ttu-id="63cb2-201">Format-Table</span><span class="sxs-lookup"><span data-stu-id="63cb2-201">Format-Table</span></span>](Format-Table.md)
