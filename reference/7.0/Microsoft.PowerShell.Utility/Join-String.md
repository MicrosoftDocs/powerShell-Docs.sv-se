---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Module Name: Microsoft.PowerShell.Utility
ms.date: 12/12/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/join-string?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Join-String
ms.openlocfilehash: bae6b8558a3e12bf161d8f0ec12037841a20cc04
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/03/2020
ms.locfileid: "93263012"
---
# <span data-ttu-id="2643a-102">Join-String</span><span class="sxs-lookup"><span data-stu-id="2643a-102">Join-String</span></span>

## <span data-ttu-id="2643a-103">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="2643a-103">SYNOPSIS</span></span>
<span data-ttu-id="2643a-104">Kombinerar objekt från pipelinen till en enda sträng.</span><span class="sxs-lookup"><span data-stu-id="2643a-104">Combines objects from the pipeline into a single string.</span></span>

## <span data-ttu-id="2643a-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="2643a-105">SYNTAX</span></span>

### <span data-ttu-id="2643a-106">Standard (standard)</span><span class="sxs-lookup"><span data-stu-id="2643a-106">Default (Default)</span></span>

```
Join-String [[-Property] <PSPropertyExpression>] [[-Separator] <String>] [-OutputPrefix <String>]
 [-OutputSuffix <String>] [-UseCulture] [-InputObject <PSObject[]>] [<CommonParameters>]
```

### <span data-ttu-id="2643a-107">SingleQuote</span><span class="sxs-lookup"><span data-stu-id="2643a-107">SingleQuote</span></span>

```
Join-String [[-Property] <PSPropertyExpression>] [[-Separator] <String>] [-OutputPrefix <String>]
 [-OutputSuffix <String>] [-SingleQuote] [-UseCulture] [-InputObject <PSObject[]>]
 [<CommonParameters>]
```

### <span data-ttu-id="2643a-108">DoubleQuote</span><span class="sxs-lookup"><span data-stu-id="2643a-108">DoubleQuote</span></span>

```
Join-String [[-Property] <PSPropertyExpression>] [[-Separator] <String>] [-OutputPrefix <String>]
 [-OutputSuffix <String>] [-DoubleQuote] [-UseCulture] [-InputObject <PSObject[]>]
 [<CommonParameters>]
```

### <span data-ttu-id="2643a-109">Format</span><span class="sxs-lookup"><span data-stu-id="2643a-109">Format</span></span>

```
Join-String [[-Property] <PSPropertyExpression>] [[-Separator] <String>] [-OutputPrefix <String>]
 [-OutputSuffix <String>] [-FormatString <String>] [-UseCulture] [-InputObject <PSObject[]>]
 [<CommonParameters>]
```

## <span data-ttu-id="2643a-110">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="2643a-110">DESCRIPTION</span></span>

<span data-ttu-id="2643a-111">`Join-String`Cmdleten ansluter till eller kombinerar text från pipeline-objekt till en enda sträng.</span><span class="sxs-lookup"><span data-stu-id="2643a-111">The `Join-String` cmdlet joins, or combines, text from pipeline objects into a single string.</span></span>

<span data-ttu-id="2643a-112">Om inga parametrar anges, konverteras pipeliniska objekt till en sträng och kopplas till standard avgränsaren `$OFS` .</span><span class="sxs-lookup"><span data-stu-id="2643a-112">If no parameters are specified, the pipeline objects are converted to a string and joined with the default separator `$OFS`.</span></span>

<span data-ttu-id="2643a-113">Genom att ange ett egenskaps namn konverteras egenskapens värde till en sträng och sammanfogas till en sträng.</span><span class="sxs-lookup"><span data-stu-id="2643a-113">By specifying a property name, the property's value is converted to a string and joined into a string.</span></span>

<span data-ttu-id="2643a-114">I stället för ett egenskaps namn kan ett skript block användas.</span><span class="sxs-lookup"><span data-stu-id="2643a-114">Instead of a property name, a script block can be used.</span></span> <span data-ttu-id="2643a-115">Skript blockets resultat konverteras till en sträng innan det kopplas till resultatet.</span><span class="sxs-lookup"><span data-stu-id="2643a-115">The script block's result is converted to a string before it's joined to form the result.</span></span> <span data-ttu-id="2643a-116">Den kan antingen kombinera texten i ett objekts egenskap eller resultatet av det objekt som konverterats till en sträng.</span><span class="sxs-lookup"><span data-stu-id="2643a-116">It can either combine the text of an object's property or the result of the object that was converted to a string.</span></span>

<span data-ttu-id="2643a-117">Denna cmdlet introducerades i PowerShell 6,2.</span><span class="sxs-lookup"><span data-stu-id="2643a-117">This cmdlet was introduced in PowerShell 6.2.</span></span>

## <span data-ttu-id="2643a-118">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="2643a-118">EXAMPLES</span></span>

### <span data-ttu-id="2643a-119">Exempel 1: Anslut till katalog namn</span><span class="sxs-lookup"><span data-stu-id="2643a-119">Example 1: Join directory names</span></span>

<!-- markdownlint-disable MD038 -->
<span data-ttu-id="2643a-120">Det här exemplet ansluter till katalog namn, omsluter utdata i dubbla citat tecken och avgränsar katalog namnen med kommatecken och blank steg ( `, ` ).</span><span class="sxs-lookup"><span data-stu-id="2643a-120">This example joins directory names, wraps the output in double-quotes, and separates the directory names with a comma and space (`, `).</span></span> <span data-ttu-id="2643a-121">Utdata är ett String-objekt.</span><span class="sxs-lookup"><span data-stu-id="2643a-121">The output is a string object.</span></span>

```powershell
Get-ChildItem -Directory C:\ | Join-String -Property Name -DoubleQuote -Separator ', '
```

```Output
"PerfLogs", "Program Files", "Program Files (x86)", "Users", "Windows"
```

<span data-ttu-id="2643a-122">`Get-ChildItem` använder **katalog** parametern för att hämta alla katalog namn för `C:\` enheten.</span><span class="sxs-lookup"><span data-stu-id="2643a-122">`Get-ChildItem` uses the **Directory** parameter to get all the directory names for the `C:\` drive.</span></span>
<span data-ttu-id="2643a-123">Objekten skickas ned pipelinen till `Join-String` .</span><span class="sxs-lookup"><span data-stu-id="2643a-123">The objects are sent down the pipeline to `Join-String`.</span></span> <span data-ttu-id="2643a-124">**Egenskaps** parametern anger katalog namnen.</span><span class="sxs-lookup"><span data-stu-id="2643a-124">The **Property** parameter specifies the directory names.</span></span> <span data-ttu-id="2643a-125">Parametern **DoubleQuote** radbryts katalog namnen med dubbla citat tecken.</span><span class="sxs-lookup"><span data-stu-id="2643a-125">The **DoubleQuote** parameter wraps the directory names with double-quote marks.</span></span>
<span data-ttu-id="2643a-126">**Avgränsnings** parametern anger att du vill använda ett kommatecken och blank steg ( `, ` ) för att avgränsa katalog namnen.</span><span class="sxs-lookup"><span data-stu-id="2643a-126">The **Separator** parameter specifies to use a comma and space (`, `) to separate the directory names.</span></span>

<span data-ttu-id="2643a-127">`Get-ChildItem`Objekten är **system. io. DirectoryInfo** och `Join-String` konverterar objekten till **system. String**.</span><span class="sxs-lookup"><span data-stu-id="2643a-127">The `Get-ChildItem` objects are **System.IO.DirectoryInfo** and `Join-String` converts the objects to **System.String**.</span></span>

### <span data-ttu-id="2643a-128">Exempel 2: Använd en egenskaps under sträng för att ansluta katalog namn</span><span class="sxs-lookup"><span data-stu-id="2643a-128">Example 2: Use a property substring to join directory names</span></span>

<span data-ttu-id="2643a-129">I det här exemplet används en substring-metod för att hämta de första fyra bokstäverna i katalog namn, omsluter utdata i enkla citat tecken och avgränsar katalog namnen med semikolon ( `;` ).</span><span class="sxs-lookup"><span data-stu-id="2643a-129">This example uses a substring method to get the first four letters of directory names, wraps the output in single-quotes, and separates the directory names with a semicolon (`;`).</span></span>

```powershell
Get-ChildItem -Directory C:\ | Join-String -Property {$_.Name.SubString(0,4)} -SingleQuote -Separator ';'
```

```Output
'Perf';'Prog';'Prog';'User';'Wind'
```

<span data-ttu-id="2643a-130">`Get-ChildItem` använder **katalog** parametern för att hämta alla katalog namn för `C:\` enheten.</span><span class="sxs-lookup"><span data-stu-id="2643a-130">`Get-ChildItem` uses the **Directory** parameter to get all the directory names for the `C:\` drive.</span></span>
<span data-ttu-id="2643a-131">Objekten skickas ned pipelinen till `Join-String` .</span><span class="sxs-lookup"><span data-stu-id="2643a-131">The objects are sent down the pipeline to `Join-String`.</span></span>

<span data-ttu-id="2643a-132">**Egenskaps** parameterns skript block använder automatisk variabel ( `$_` ) för att ange varje objekts **namn** egenskap under sträng.</span><span class="sxs-lookup"><span data-stu-id="2643a-132">The **Property** parameter script block uses automatic variable (`$_`) to specify each object's **Name** property substring.</span></span> <span data-ttu-id="2643a-133">Under strängen hämtar de fyra första bokstäverna i varje katalog namn.</span><span class="sxs-lookup"><span data-stu-id="2643a-133">The substring gets the first four letters of each directory name.</span></span> <span data-ttu-id="2643a-134">Under strängen anger tecken start-och slut position.</span><span class="sxs-lookup"><span data-stu-id="2643a-134">The substring specifies the character start and end positions.</span></span> <span data-ttu-id="2643a-135">Parametern **SingleQuote** radbryts katalog namnen med enkla tecken.</span><span class="sxs-lookup"><span data-stu-id="2643a-135">The **SingleQuote** parameter wraps the directory names with single-quote marks.</span></span> <span data-ttu-id="2643a-136">**Avgränsnings** parametern anger att ett semikolon ( `;` ) ska användas för att avgränsa katalog namnen.</span><span class="sxs-lookup"><span data-stu-id="2643a-136">The **Separator** parameter specifies to use a semicolon (`;`) to separate the directory names.</span></span>

<span data-ttu-id="2643a-137">Mer information om automatiska variabler och del strängar finns i [about_Automatic_Variables](../microsoft.powershell.core/about/about_automatic_variables.md) och under [sträng](/dotnet/api/system.string.substring).</span><span class="sxs-lookup"><span data-stu-id="2643a-137">For more information about automatic variables and substrings, see [about_Automatic_Variables](../microsoft.powershell.core/about/about_automatic_variables.md) and [Substring](/dotnet/api/system.string.substring).</span></span>

### <span data-ttu-id="2643a-138">Exempel 3: Visa sammanfogning av utdata på en separat rad</span><span class="sxs-lookup"><span data-stu-id="2643a-138">Example 3: Display join output on a separate line</span></span>

<span data-ttu-id="2643a-139">Det här exemplet ansluter tjänst namn till varje tjänst på en separat rad och indragna av en flik.</span><span class="sxs-lookup"><span data-stu-id="2643a-139">This example joins service names with each service on a separate line and indented by a tab.</span></span>

```powershell
Get-Service -Name se* | Join-String -Property Name -Separator "`r`n`t" -OutputPrefix "Services:`n`t"
```

```Output
Services:
    seclogon
    SecurityHealthService
    SEMgrSvc
    SENS
    Sense
    SensorDataService
    SensorService
    SensrSvc
    SessionEnv
```

<span data-ttu-id="2643a-140">`Get-Service` använder parametern **Name** med för att ange tjänster som börjar med `se*` .</span><span class="sxs-lookup"><span data-stu-id="2643a-140">`Get-Service` uses the **Name** parameter with to specify services that begin with `se*`.</span></span> <span data-ttu-id="2643a-141">Asterisken ( `*` ) är ett jokertecken för alla bokstäver.</span><span class="sxs-lookup"><span data-stu-id="2643a-141">The asterisk (`*`) is a wildcard for any character.</span></span>

<span data-ttu-id="2643a-142">Objekten skickas ned pipelinen till `Join-String` som använder **egenskaps** parametern för att ange tjänst namnen.</span><span class="sxs-lookup"><span data-stu-id="2643a-142">The objects are sent down the pipeline to `Join-String` that uses the **Property** parameter to specify the service names.</span></span> <span data-ttu-id="2643a-143">**Avgränsnings** parametern anger tre specialtecken som representerar en vagn retur ( `` `r `` ), ny rad ( `` `n `` ) och TABB ( `` `t `` ).</span><span class="sxs-lookup"><span data-stu-id="2643a-143">The **Separator** parameter specifies three special characters that represent a carriage return (`` `r ``), newline (`` `n ``), and tab (`` `t ``).</span></span> <span data-ttu-id="2643a-144">**OutputPrefix** infogar en etikett **tjänst:** med en ny rad och flik före den första raden i utdata.</span><span class="sxs-lookup"><span data-stu-id="2643a-144">The **OutputPrefix** inserts a label **Services:** with a new line and tab before the first line of output.</span></span>

<span data-ttu-id="2643a-145">Mer information om specialtecken finns [about_Special_Characters](..//microsoft.powershell.core/about/about_special_characters.md).</span><span class="sxs-lookup"><span data-stu-id="2643a-145">For more information about special characters, see [about_Special_Characters](..//microsoft.powershell.core/about/about_special_characters.md).</span></span>

### <span data-ttu-id="2643a-146">Exempel 4: skapa en klass definition från ett objekt</span><span class="sxs-lookup"><span data-stu-id="2643a-146">Example 4: Create a class definition from an object</span></span>

<span data-ttu-id="2643a-147">I det här exemplet skapas en PowerShell-klass definition med ett befintligt objekt som mall.</span><span class="sxs-lookup"><span data-stu-id="2643a-147">This example generates a PowerShell class definition using an existing object as a template.</span></span>

<span data-ttu-id="2643a-148">I det här kod exemplet används ihopbuntning för att minska rad längden och förbättra läsbarheten.</span><span class="sxs-lookup"><span data-stu-id="2643a-148">This code sample uses splatting to reduce the line length and improve readability.</span></span> <span data-ttu-id="2643a-149">Mer information finns i [about_Splatting](../Microsoft.PowerShell.Core/About/about_Splatting.md).</span><span class="sxs-lookup"><span data-stu-id="2643a-149">For more information, see [about_Splatting](../Microsoft.PowerShell.Core/About/about_Splatting.md).</span></span>

```powershell
$obj = [pscustomobject] @{Name = "Joe"; Age = 42}
$parms = @{
  Property = "Name"
  FormatString = '  ${0}'
  OutputPrefix = "class {`n"
  OutputSuffix = "`n}`n"
  Separator = "`n"
}
$obj.PSObject.Properties | Join-String @parms
```

```Output
class {
  $Name
  $Age
}
```

## <span data-ttu-id="2643a-150">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="2643a-150">PARAMETERS</span></span>

### <span data-ttu-id="2643a-151">-DoubleQuote</span><span class="sxs-lookup"><span data-stu-id="2643a-151">-DoubleQuote</span></span>

<span data-ttu-id="2643a-152">Omsluter strängvärdet för varje pipeline-objekt i dubbla citat tecken.</span><span class="sxs-lookup"><span data-stu-id="2643a-152">Wraps the string value of each pipeline object in double-quotes.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: DoubleQuote
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="2643a-153">– FormatString</span><span class="sxs-lookup"><span data-stu-id="2643a-153">-FormatString</span></span>

<span data-ttu-id="2643a-154">En format sträng som anger hur varje objekt ska formateras.</span><span class="sxs-lookup"><span data-stu-id="2643a-154">A format string that specifies how each item should be formatted.</span></span>

```yaml
Type: System.String
Parameter Sets: Format
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="2643a-155">– InputObject</span><span class="sxs-lookup"><span data-stu-id="2643a-155">-InputObject</span></span>

<span data-ttu-id="2643a-156">Anger den text som ska sammanfogas.</span><span class="sxs-lookup"><span data-stu-id="2643a-156">Specifies the text to be joined.</span></span> <span data-ttu-id="2643a-157">Ange en variabel som innehåller texten eller Skriv ett kommando eller uttryck som hämtar objekten för att ansluta till strängar.</span><span class="sxs-lookup"><span data-stu-id="2643a-157">Enter a variable that contains the text, or type a command or expression that gets the objects to join into strings.</span></span>

```yaml
Type: System.Management.Automation.PSObject[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="2643a-158">-OutputPrefix</span><span class="sxs-lookup"><span data-stu-id="2643a-158">-OutputPrefix</span></span>

<span data-ttu-id="2643a-159">Text som infogas före den utgående strängen.</span><span class="sxs-lookup"><span data-stu-id="2643a-159">Text that's inserted before the output string.</span></span> <span data-ttu-id="2643a-160">Strängen kan innehålla specialtecken, till exempel vagn retur ( `` `r `` ), rad matning ( `` `n `` ) och TABB ( `` `t `` ).</span><span class="sxs-lookup"><span data-stu-id="2643a-160">The string can contain special characters such as carriage return (`` `r ``), newline (`` `n ``), and tab (`` `t ``).</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: op

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="2643a-161">-OutputSuffix</span><span class="sxs-lookup"><span data-stu-id="2643a-161">-OutputSuffix</span></span>

<span data-ttu-id="2643a-162">Text som läggs till i den utgående strängen.</span><span class="sxs-lookup"><span data-stu-id="2643a-162">Text that's appended to the output string.</span></span> <span data-ttu-id="2643a-163">Strängen kan innehålla specialtecken, till exempel vagn retur ( `` `r `` ), rad matning ( `` `n `` ) och TABB ( `` `t `` ).</span><span class="sxs-lookup"><span data-stu-id="2643a-163">The string can contain special characters such as carriage return (`` `r ``), newline (`` `n ``), and tab (`` `t ``).</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: os

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="2643a-164">– Egenskap</span><span class="sxs-lookup"><span data-stu-id="2643a-164">-Property</span></span>

<span data-ttu-id="2643a-165">Namnet på en egenskap, eller ett egenskaps uttryck, som kommer att projicera pipeline-objektet till text.</span><span class="sxs-lookup"><span data-stu-id="2643a-165">The name of a property, or a property expression, that will project the pipeline object to text.</span></span>

```yaml
Type: Microsoft.PowerShell.Commands.PSPropertyExpression
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="2643a-166">-Avgränsare</span><span class="sxs-lookup"><span data-stu-id="2643a-166">-Separator</span></span>

<span data-ttu-id="2643a-167">Text eller tecken, till exempel ett komma eller semikolon som infogas mellan texten för varje pipeline-objekt.</span><span class="sxs-lookup"><span data-stu-id="2643a-167">Text or characters such as a comma or semicolon that's inserted between the text for each pipeline object.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="2643a-168">-SingleQuote</span><span class="sxs-lookup"><span data-stu-id="2643a-168">-SingleQuote</span></span>

<span data-ttu-id="2643a-169">Radbryter strängvärdet för varje pipeline-objekt i enkla citat tecken.</span><span class="sxs-lookup"><span data-stu-id="2643a-169">Wraps the string value of each pipeline object in single quotes.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: SingleQuote
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="2643a-170">-UseCulture</span><span class="sxs-lookup"><span data-stu-id="2643a-170">-UseCulture</span></span>

<span data-ttu-id="2643a-171">Använder list avgränsaren för den aktuella kulturen som objekt avgränsare.</span><span class="sxs-lookup"><span data-stu-id="2643a-171">Uses the list separator for the current culture as the item delimiter.</span></span> <span data-ttu-id="2643a-172">Använd följande kommando för att hitta List avgränsaren för en kultur: `(Get-Culture).TextInfo.ListSeparator` .</span><span class="sxs-lookup"><span data-stu-id="2643a-172">To find the list separator for a culture, use the following command: `(Get-Culture).TextInfo.ListSeparator`.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="2643a-173">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="2643a-173">CommonParameters</span></span>

<span data-ttu-id="2643a-174">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="2643a-174">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="2643a-175">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="2643a-175">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="2643a-176">INDATA</span><span class="sxs-lookup"><span data-stu-id="2643a-176">INPUTS</span></span>

### <span data-ttu-id="2643a-177">System. Management. Automation. PSObject</span><span class="sxs-lookup"><span data-stu-id="2643a-177">System.Management.Automation.PSObject</span></span>

## <span data-ttu-id="2643a-178">UTDATA</span><span class="sxs-lookup"><span data-stu-id="2643a-178">OUTPUTS</span></span>

### <span data-ttu-id="2643a-179">System. String</span><span class="sxs-lookup"><span data-stu-id="2643a-179">System.String</span></span>

## <span data-ttu-id="2643a-180">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="2643a-180">NOTES</span></span>

## <span data-ttu-id="2643a-181">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="2643a-181">RELATED LINKS</span></span>

[<span data-ttu-id="2643a-182">about_Automatic_Variables</span><span class="sxs-lookup"><span data-stu-id="2643a-182">about_Automatic_Variables</span></span>](../microsoft.powershell.core/about/about_automatic_variables.md)

[<span data-ttu-id="2643a-183">about_Special_Characters</span><span class="sxs-lookup"><span data-stu-id="2643a-183">about_Special_Characters</span></span>](..//microsoft.powershell.core/about/about_special_characters.md)

[<span data-ttu-id="2643a-184">Under sträng</span><span class="sxs-lookup"><span data-stu-id="2643a-184">Substring</span></span>](/dotnet/api/system.string.substring)
