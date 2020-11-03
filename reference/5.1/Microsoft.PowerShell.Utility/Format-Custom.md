---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 08/10/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/format-custom?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Format-Custom
ms.openlocfilehash: 89c7e8f1b70552e735fccd7b2fd45f951b81f928
ms.sourcegitcommit: 9a6b6714ded4edb5119f1b82a253608018ea6b98
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/10/2020
ms.locfileid: "93269024"
---
# <span data-ttu-id="6a6a5-103">Format-Custom</span><span class="sxs-lookup"><span data-stu-id="6a6a5-103">Format-Custom</span></span>

## <span data-ttu-id="6a6a5-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="6a6a5-104">SYNOPSIS</span></span>
<span data-ttu-id="6a6a5-105">Använder en anpassad vy för att formatera utdata.</span><span class="sxs-lookup"><span data-stu-id="6a6a5-105">Uses a customized view to format the output.</span></span>

## <span data-ttu-id="6a6a5-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="6a6a5-106">SYNTAX</span></span>

```
Format-Custom [[-Property] <Object[]>] [-Depth <Int32>] [-GroupBy <Object>] [-View <String>]
 [-ShowError] [-DisplayError] [-Force] [-Expand <String>] [-InputObject <PSObject>]
 [<CommonParameters>]
```

## <span data-ttu-id="6a6a5-107">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="6a6a5-107">DESCRIPTION</span></span>

<span data-ttu-id="6a6a5-108">`Format-Custom`Cmdleten formaterar utdata från ett kommando som definieras i en annan vy.</span><span class="sxs-lookup"><span data-stu-id="6a6a5-108">The `Format-Custom` cmdlet formats the output of a command as defined in an alternate view.</span></span>
<span data-ttu-id="6a6a5-109">`Format-Custom` är utformat för att Visa vyer som inte är bara tabeller eller bara listor.</span><span class="sxs-lookup"><span data-stu-id="6a6a5-109">`Format-Custom` is designed to display views that are not just tables or just lists.</span></span> <span data-ttu-id="6a6a5-110">Du kan använda de vyer som definierats i `*format.PS1XML` filerna i PowerShell-katalogen, eller så kan du skapa egna vyer i nya PS1XML-filer och använda `Update-FormatData` cmdleten för att lägga till dem i PowerShell.</span><span class="sxs-lookup"><span data-stu-id="6a6a5-110">You can use the views defined in the `*format.PS1XML` files in the PowerShell directory, or you can create your own views in new PS1XML files and use the `Update-FormatData` cmdlet to add them to PowerShell.</span></span>

## <span data-ttu-id="6a6a5-111">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="6a6a5-111">EXAMPLES</span></span>

### <span data-ttu-id="6a6a5-112">Exempel 1: formatera utdata med en anpassad vy</span><span class="sxs-lookup"><span data-stu-id="6a6a5-112">Example 1: Format output with a custom view</span></span>

```powershell
Get-Command Start-Transcript | Format-Custom -View MyView
```

<span data-ttu-id="6a6a5-113">Det här kommandot formaterar information om `Start-Transcript` cmdleten i det format som definieras av vyn visnings alternativ, en anpassad vy som skapats av användaren.</span><span class="sxs-lookup"><span data-stu-id="6a6a5-113">This command formats information about the `Start-Transcript` cmdlet in the format defined by the MyView view, a custom view created by the user.</span></span> <span data-ttu-id="6a6a5-114">För att kunna köra det här kommandot måste du först skapa en ny PS1XML-fil, **definiera vyn vy** och sedan använda `Update-FormatData` kommandot för att lägga till PS1XML-filen till PowerShell.</span><span class="sxs-lookup"><span data-stu-id="6a6a5-114">To run this command successfully, you must first create a new PS1XML file, define the **MyView** view, and then use the `Update-FormatData` command to add the PS1XML file to PowerShell.</span></span>

### <span data-ttu-id="6a6a5-115">Exempel 2: formatera utdata med standardvyn</span><span class="sxs-lookup"><span data-stu-id="6a6a5-115">Example 2: Format output with the default view</span></span>

```powershell
Get-Process Winlogon | Format-Custom
```

<span data-ttu-id="6a6a5-116">Det här kommandot formaterar information om **Winlogon** -processen i en alternativ anpassad vy.</span><span class="sxs-lookup"><span data-stu-id="6a6a5-116">This command formats information about the **Winlogon** process in an alternate customized view.</span></span>
<span data-ttu-id="6a6a5-117">Eftersom kommandot inte använder parametern **View** `Format-Custom` används en anpassad standardvy för att formatera data.</span><span class="sxs-lookup"><span data-stu-id="6a6a5-117">Because the command does not use the **View** parameter, `Format-Custom` uses a default custom view to format the data.</span></span>

### <span data-ttu-id="6a6a5-118">Exempel 3: Felsöka format fel</span><span class="sxs-lookup"><span data-stu-id="6a6a5-118">Example 3: Troubleshooting format errors</span></span>

<span data-ttu-id="6a6a5-119">I följande exempel visas resultatet av att lägga till **DisplayError** -eller **ShowError** -parametrarna med ett uttryck.</span><span class="sxs-lookup"><span data-stu-id="6a6a5-119">The following examples show of the results of adding the **DisplayError** or **ShowError** parameters with an expression.</span></span>

```powershell
PC /> Get-Date | Format-Custom DayOfWeek,{ $_ / $null } -DisplayError

class DateTime
{
  DayOfWeek = Friday
   $_ / $null  = #ERR
}


PC /> Get-Date | Format-Custom DayOfWeek,{ $_ / $null } -ShowError

class DateTime
{
  DayOfWeek = Friday
   $_ / $null  =
}

Failed to evaluate expression " $_ / $null ".
+ CategoryInfo          : InvalidArgument: (12/21/2018 8:01:04 AM:PSObject) [], RuntimeException
+ FullyQualifiedErrorId : PSPropertyExpressionError
```

## <span data-ttu-id="6a6a5-120">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="6a6a5-120">PARAMETERS</span></span>

### <span data-ttu-id="6a6a5-121">-Djup</span><span class="sxs-lookup"><span data-stu-id="6a6a5-121">-Depth</span></span>

<span data-ttu-id="6a6a5-122">Anger antalet kolumner i visningen.</span><span class="sxs-lookup"><span data-stu-id="6a6a5-122">Specifies the number of columns in the display.</span></span>

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

### <span data-ttu-id="6a6a5-123">– DisplayError</span><span class="sxs-lookup"><span data-stu-id="6a6a5-123">-DisplayError</span></span>

<span data-ttu-id="6a6a5-124">Visar fel på kommando raden.</span><span class="sxs-lookup"><span data-stu-id="6a6a5-124">Displays errors at the command line.</span></span> <span data-ttu-id="6a6a5-125">Den här parametern används sällan, men kan användas som ett fel söknings stöd när du formaterar uttryck i ett `Format-Custom` kommando, och uttrycken verkar inte fungera.</span><span class="sxs-lookup"><span data-stu-id="6a6a5-125">This parameter is rarely used, but can be used as a debugging aid when you are formatting expressions in a `Format-Custom` command, and the expressions do not appear to be working.</span></span>

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

### <span data-ttu-id="6a6a5-126">– Expandera</span><span class="sxs-lookup"><span data-stu-id="6a6a5-126">-Expand</span></span>

<span data-ttu-id="6a6a5-127">Formaterar samlings objekt och objekt i samlingen.</span><span class="sxs-lookup"><span data-stu-id="6a6a5-127">Formats the collection object, as well as the objects in the collection.</span></span> <span data-ttu-id="6a6a5-128">Den här parametern är utformad för att formatera objekt som har stöd för **system. Collections. ICollection** -gränssnittet.</span><span class="sxs-lookup"><span data-stu-id="6a6a5-128">This parameter is designed to format objects that support the **System.Collections.ICollection** interface.</span></span> <span data-ttu-id="6a6a5-129">Standardvärdet är **EnumOnly**.</span><span class="sxs-lookup"><span data-stu-id="6a6a5-129">The default value is **EnumOnly**.</span></span>

<span data-ttu-id="6a6a5-130">Giltiga värden är:</span><span class="sxs-lookup"><span data-stu-id="6a6a5-130">Valid values are:</span></span>

- <span data-ttu-id="6a6a5-131">EnumOnly: visar egenskaperna för objekten i samlingen.</span><span class="sxs-lookup"><span data-stu-id="6a6a5-131">EnumOnly: Displays the properties of the objects in the collection.</span></span>
- <span data-ttu-id="6a6a5-132">CoreOnly: visar egenskaperna för objektet samling.</span><span class="sxs-lookup"><span data-stu-id="6a6a5-132">CoreOnly: Displays the properties of the collection object.</span></span>
- <span data-ttu-id="6a6a5-133">Båda: visar egenskaperna för samlingsobjektet och objekten i samlingen.</span><span class="sxs-lookup"><span data-stu-id="6a6a5-133">Both: Displays the properties of the collection object and the objects in the collection.</span></span>

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

### <span data-ttu-id="6a6a5-134">-Force</span><span class="sxs-lookup"><span data-stu-id="6a6a5-134">-Force</span></span>

<span data-ttu-id="6a6a5-135">Instruerar cmdleten att visa all information om felet.</span><span class="sxs-lookup"><span data-stu-id="6a6a5-135">Directs the cmdlet to display all of the error information.</span></span> <span data-ttu-id="6a6a5-136">Används med parametrarna **DisplayError** eller **ShowError** .</span><span class="sxs-lookup"><span data-stu-id="6a6a5-136">Use with the **DisplayError** or **ShowError** parameters.</span></span> <span data-ttu-id="6a6a5-137">Som standard visas endast en del fel information när ett fel objekt skrivs till fel-eller visnings strömmar.</span><span class="sxs-lookup"><span data-stu-id="6a6a5-137">By default, when an error object is written to the error or display streams, only some of the error information is displayed.</span></span>

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

### <span data-ttu-id="6a6a5-138">– GroupBy</span><span class="sxs-lookup"><span data-stu-id="6a6a5-138">-GroupBy</span></span>

<span data-ttu-id="6a6a5-139">Formaterar utdata i grupper baserat på en delad egenskap eller ett värde.</span><span class="sxs-lookup"><span data-stu-id="6a6a5-139">Formats the output in groups based on a shared property or value.</span></span> <span data-ttu-id="6a6a5-140">Ange ett uttryck eller en egenskap för utdata.</span><span class="sxs-lookup"><span data-stu-id="6a6a5-140">Enter an expression or a property of the output.</span></span>

<span data-ttu-id="6a6a5-141">Värdet för **groupby** -parametern kan vara en ny beräknad egenskap.</span><span class="sxs-lookup"><span data-stu-id="6a6a5-141">The value of the **GroupBy** parameter can be a new calculated property.</span></span> <span data-ttu-id="6a6a5-142">Den beräknade egenskapen kan vara ett skript block eller en hash-tabell.</span><span class="sxs-lookup"><span data-stu-id="6a6a5-142">The calculated property can be a script block or a hash table.</span></span> <span data-ttu-id="6a6a5-143">Giltiga nyckel/värde-par är:</span><span class="sxs-lookup"><span data-stu-id="6a6a5-143">Valid key-value pairs are:</span></span>

- <span data-ttu-id="6a6a5-144">Namn (eller etikett) `<string>`</span><span class="sxs-lookup"><span data-stu-id="6a6a5-144">Name (or Label) `<string>`</span></span>
- <span data-ttu-id="6a6a5-145">Uttryck `<string>` eller `<script block>`</span><span class="sxs-lookup"><span data-stu-id="6a6a5-145">Expression `<string>` or `<script block>`</span></span>
- <span data-ttu-id="6a6a5-146">FormatString `<string>`</span><span class="sxs-lookup"><span data-stu-id="6a6a5-146">FormatString `<string>`</span></span>

<span data-ttu-id="6a6a5-147">Mer information finns i [about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md).</span><span class="sxs-lookup"><span data-stu-id="6a6a5-147">For more information, see [about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md).</span></span>

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

### <span data-ttu-id="6a6a5-148">– InputObject</span><span class="sxs-lookup"><span data-stu-id="6a6a5-148">-InputObject</span></span>

<span data-ttu-id="6a6a5-149">Anger de objekt som ska formateras.</span><span class="sxs-lookup"><span data-stu-id="6a6a5-149">Specifies the objects to be formatted.</span></span> <span data-ttu-id="6a6a5-150">Ange en variabel som innehåller objekten eller Skriv ett kommando eller uttryck som hämtar objekten.</span><span class="sxs-lookup"><span data-stu-id="6a6a5-150">Enter a variable that contains the objects or type a command or expression that gets the objects.</span></span>

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

### <span data-ttu-id="6a6a5-151">– Egenskap</span><span class="sxs-lookup"><span data-stu-id="6a6a5-151">-Property</span></span>

<span data-ttu-id="6a6a5-152">Anger objekt egenskaperna som visas i visningen och i vilken ordning de visas.</span><span class="sxs-lookup"><span data-stu-id="6a6a5-152">Specifies the object properties that appear in the display and the order in which they appear.</span></span>
<span data-ttu-id="6a6a5-153">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="6a6a5-153">Wildcards are permitted.</span></span>

<span data-ttu-id="6a6a5-154">Om du utelämnar den här parametern beror egenskaperna som visas i vyn på det objekt som visas.</span><span class="sxs-lookup"><span data-stu-id="6a6a5-154">If you omit this parameter, the properties that appear in the display depend on the object being displayed.</span></span> <span data-ttu-id="6a6a5-155">**Egenskapen** parameter namn är valfri.</span><span class="sxs-lookup"><span data-stu-id="6a6a5-155">The parameter name **Property** is optional.</span></span> <span data-ttu-id="6a6a5-156">Du kan inte använda **egenskapen** och **Visa** parametrar i samma kommando.</span><span class="sxs-lookup"><span data-stu-id="6a6a5-156">You cannot use the **Property** and **View** parameters in the same command.</span></span>

<span data-ttu-id="6a6a5-157">Värdet för **egenskaps** parametern kan vara en ny beräknad egenskap.</span><span class="sxs-lookup"><span data-stu-id="6a6a5-157">The value of the **Property** parameter can be a new calculated property.</span></span> <span data-ttu-id="6a6a5-158">Den beräknade egenskapen kan vara ett skript block eller en hash-tabell.</span><span class="sxs-lookup"><span data-stu-id="6a6a5-158">The calculated property can be a script block or a hash table.</span></span> <span data-ttu-id="6a6a5-159">Giltiga nyckel/värde-par är:</span><span class="sxs-lookup"><span data-stu-id="6a6a5-159">Valid key-value pairs are:</span></span>

- <span data-ttu-id="6a6a5-160">Uttryck- `<string>` eller `<script block>`</span><span class="sxs-lookup"><span data-stu-id="6a6a5-160">Expression - `<string>` or `<script block>`</span></span>
- <span data-ttu-id="6a6a5-161">Djuplodande `<int32>`</span><span class="sxs-lookup"><span data-stu-id="6a6a5-161">Depth - `<int32>`</span></span>

<span data-ttu-id="6a6a5-162">Mer information finns i [about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md).</span><span class="sxs-lookup"><span data-stu-id="6a6a5-162">For more information, see [about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md).</span></span>

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

### <span data-ttu-id="6a6a5-163">– ShowError</span><span class="sxs-lookup"><span data-stu-id="6a6a5-163">-ShowError</span></span>

<span data-ttu-id="6a6a5-164">Skickar fel via pipelinen.</span><span class="sxs-lookup"><span data-stu-id="6a6a5-164">Sends errors through the pipeline.</span></span> <span data-ttu-id="6a6a5-165">Den här parametern används sällan, men kan användas som ett fel söknings stöd när du formaterar uttryck i ett `Format-Custom` kommando, och uttrycken verkar inte fungera.</span><span class="sxs-lookup"><span data-stu-id="6a6a5-165">This parameter is rarely used, but can be used as a debugging aid when you are formatting expressions in a `Format-Custom` command, and the expressions do not appear to be working.</span></span>

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

### <span data-ttu-id="6a6a5-166">– Visa</span><span class="sxs-lookup"><span data-stu-id="6a6a5-166">-View</span></span>

<span data-ttu-id="6a6a5-167">Anger namnet på ett alternativt format eller en annan vy.</span><span class="sxs-lookup"><span data-stu-id="6a6a5-167">Specifies the name of an alternate format or view.</span></span> <span data-ttu-id="6a6a5-168">Om du utelämnar den här parametern `Format-Custom` används en anpassad standardvy.</span><span class="sxs-lookup"><span data-stu-id="6a6a5-168">If you omit this parameter, `Format-Custom` uses a default custom view.</span></span> <span data-ttu-id="6a6a5-169">Du kan inte använda **egenskapen** och **Visa** parametrar i samma kommando.</span><span class="sxs-lookup"><span data-stu-id="6a6a5-169">You cannot use the **Property** and **View** parameters in the same command.</span></span>

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

### <span data-ttu-id="6a6a5-170">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="6a6a5-170">CommonParameters</span></span>

<span data-ttu-id="6a6a5-171">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="6a6a5-171">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="6a6a5-172">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="6a6a5-172">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="6a6a5-173">INDATA</span><span class="sxs-lookup"><span data-stu-id="6a6a5-173">INPUTS</span></span>

### <span data-ttu-id="6a6a5-174">System. Management. Automation. PSObject</span><span class="sxs-lookup"><span data-stu-id="6a6a5-174">System.Management.Automation.PSObject</span></span>

<span data-ttu-id="6a6a5-175">Du kan skicka vidare alla objekt till `Format-Custom` .</span><span class="sxs-lookup"><span data-stu-id="6a6a5-175">You can pipe any object to `Format-Custom`.</span></span>

## <span data-ttu-id="6a6a5-176">UTDATA</span><span class="sxs-lookup"><span data-stu-id="6a6a5-176">OUTPUTS</span></span>

### <span data-ttu-id="6a6a5-177">Microsoft. PowerShell. commands. Internal. format</span><span class="sxs-lookup"><span data-stu-id="6a6a5-177">Microsoft.PowerShell.Commands.Internal.Format</span></span>

<span data-ttu-id="6a6a5-178">`Format-Custom` Returnerar de format objekt som representerar visningen.</span><span class="sxs-lookup"><span data-stu-id="6a6a5-178">`Format-Custom` returns the format objects that represent the display.</span></span>

## <span data-ttu-id="6a6a5-179">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="6a6a5-179">NOTES</span></span>

<span data-ttu-id="6a6a5-180">`Format-Custom` är utformat för att Visa vyer som inte är bara tabeller eller bara listor.</span><span class="sxs-lookup"><span data-stu-id="6a6a5-180">`Format-Custom` is designed to display views that are not just tables or just lists.</span></span> <span data-ttu-id="6a6a5-181">Om du vill visa en alternativ tabellvy använder du `Format-Table` .</span><span class="sxs-lookup"><span data-stu-id="6a6a5-181">To display an alternate table view, use `Format-Table`.</span></span> <span data-ttu-id="6a6a5-182">Om du vill visa en annan listvy använder du `Format-List` .</span><span class="sxs-lookup"><span data-stu-id="6a6a5-182">To display an alternate list view, use `Format-List`.</span></span>

<span data-ttu-id="6a6a5-183">Du kan också referera till `Format-Custom` med dess inbyggda alias `fc` .</span><span class="sxs-lookup"><span data-stu-id="6a6a5-183">You can also refer to `Format-Custom` by its built-in alias, `fc`.</span></span> <span data-ttu-id="6a6a5-184">Mer information finns i [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md).</span><span class="sxs-lookup"><span data-stu-id="6a6a5-184">For more information, see [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md).</span></span>

<span data-ttu-id="6a6a5-185">Parametern **groupby** förutsätter att objekten sorteras.</span><span class="sxs-lookup"><span data-stu-id="6a6a5-185">The **GroupBy** parameter assumes that the objects are sorted.</span></span> <span data-ttu-id="6a6a5-186">`Format-Custom`Använd för att sortera objekten innan du använder dem för att gruppera objekten `Sort-Object` .</span><span class="sxs-lookup"><span data-stu-id="6a6a5-186">Before using `Format-Custom` to group the objects, use `Sort-Object` to sort them.</span></span>

## <span data-ttu-id="6a6a5-187">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="6a6a5-187">RELATED LINKS</span></span>

[<span data-ttu-id="6a6a5-188">about_Calculated_Properties</span><span class="sxs-lookup"><span data-stu-id="6a6a5-188">about_Calculated_Properties</span></span>](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md)

[<span data-ttu-id="6a6a5-189">Format-Hex</span><span class="sxs-lookup"><span data-stu-id="6a6a5-189">Format-Hex</span></span>](Format-Hex.md)

[<span data-ttu-id="6a6a5-190">Format-List</span><span class="sxs-lookup"><span data-stu-id="6a6a5-190">Format-List</span></span>](Format-List.md)

[<span data-ttu-id="6a6a5-191">Format-Table</span><span class="sxs-lookup"><span data-stu-id="6a6a5-191">Format-Table</span></span>](Format-Table.md)

[<span data-ttu-id="6a6a5-192">Format-Wide</span><span class="sxs-lookup"><span data-stu-id="6a6a5-192">Format-Wide</span></span>](Format-Wide.md)

[<span data-ttu-id="6a6a5-193">Hämta process</span><span class="sxs-lookup"><span data-stu-id="6a6a5-193">Get-Process</span></span>](../Microsoft.PowerShell.Management/Get-Process.md)
