---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 08/10/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/group-object?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Group-Object
ms.openlocfilehash: f430dd1f9d9f820dda88ba5ad40023650204604d
ms.sourcegitcommit: 9a6b6714ded4edb5119f1b82a253608018ea6b98
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/10/2020
ms.locfileid: "93269084"
---
# <span data-ttu-id="9b7c1-103">Group-Object</span><span class="sxs-lookup"><span data-stu-id="9b7c1-103">Group-Object</span></span>

## <span data-ttu-id="9b7c1-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="9b7c1-104">SYNOPSIS</span></span>
<span data-ttu-id="9b7c1-105">Grupperar objekt som innehåller samma värde för angivna egenskaper.</span><span class="sxs-lookup"><span data-stu-id="9b7c1-105">Groups objects that contain the same value for specified properties.</span></span>

## <span data-ttu-id="9b7c1-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="9b7c1-106">SYNTAX</span></span>

### <span data-ttu-id="9b7c1-107">Hash</span><span class="sxs-lookup"><span data-stu-id="9b7c1-107">HashTable</span></span>

```
Group-Object [-NoElement] [-AsHashTable] [-AsString] [-InputObject <PSObject>]
 [[-Property] <Object[]>] [-Culture <String>] [-CaseSensitive] [<CommonParameters>]
```

## <span data-ttu-id="9b7c1-108">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="9b7c1-108">DESCRIPTION</span></span>

<span data-ttu-id="9b7c1-109">`Group-Object`Cmdleten visar objekt i grupper baserat på värdet för en angiven egenskap.</span><span class="sxs-lookup"><span data-stu-id="9b7c1-109">The `Group-Object` cmdlet displays objects in groups based on the value of a specified property.</span></span>
<span data-ttu-id="9b7c1-110">`Group-Object` Returnerar en tabell med en rad för varje egenskaps värde och en kolumn som visar antalet objekt med det värdet.</span><span class="sxs-lookup"><span data-stu-id="9b7c1-110">`Group-Object` returns a table with one row for each property value and a column that displays the number of items with that value.</span></span>

<span data-ttu-id="9b7c1-111">Om du anger mer än en egenskap, `Group-Object` grupperas de av värdena för den första egenskapen, och därefter grupperas de efter värdet för nästa egenskap i varje egenskaps grupp.</span><span class="sxs-lookup"><span data-stu-id="9b7c1-111">If you specify more than one property, `Group-Object` first groups them by the values of the first property, and then, within each property group, it groups by the value of the next property.</span></span>

## <span data-ttu-id="9b7c1-112">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="9b7c1-112">EXAMPLES</span></span>

### <span data-ttu-id="9b7c1-113">Exempel 1: Gruppera filer efter tillägg</span><span class="sxs-lookup"><span data-stu-id="9b7c1-113">Example 1: Group files by extension</span></span>

<span data-ttu-id="9b7c1-114">Det här exemplet hämtar filerna rekursivt under `$PSHOME` och grupper dem efter fil namns tillägg.</span><span class="sxs-lookup"><span data-stu-id="9b7c1-114">This example recursively gets the files under `$PSHOME` and groups them by file name extension.</span></span> <span data-ttu-id="9b7c1-115">Utdata skickas till `Sort-Object` cmdleten, som sorteras efter antalet filer som hittas för det angivna tillägget.</span><span class="sxs-lookup"><span data-stu-id="9b7c1-115">The output is sent to the `Sort-Object` cmdlet, which sorts them by the count files found for the given extension.</span></span> <span data-ttu-id="9b7c1-116">Det tomma **namnet** representerar kataloger.</span><span class="sxs-lookup"><span data-stu-id="9b7c1-116">The empty **Name** represents directories.</span></span>

<span data-ttu-id="9b7c1-117">I det här exemplet används **Noelement** -parametern för att utelämna medlemmarna i gruppen.</span><span class="sxs-lookup"><span data-stu-id="9b7c1-117">This example uses the **NoElement** parameter to omit the members of the group.</span></span>

```powershell
$files = Get-ChildItem -Path $PSHOME -Recurse
$files | Group-Object -Property extension -NoElement | Sort-Object -Property Count -Descending
```

```Output
Count Name
----- ----
  365 .xml
  231 .cdxml
  197
  169 .ps1xml
  142 .txt
  114 .psd1
   63 .psm1
   49 .xsd
   36 .dll
   15 .mfl
   15 .mof
...
```

### <span data-ttu-id="9b7c1-118">Exempel 2: gruppera heltal efter strider och Evens</span><span class="sxs-lookup"><span data-stu-id="9b7c1-118">Example 2: Group integers by odds and evens</span></span>

<span data-ttu-id="9b7c1-119">Det här exemplet visar hur du använder skript block som värde för **egenskaps** parametern.</span><span class="sxs-lookup"><span data-stu-id="9b7c1-119">This example shows how to use script blocks as the value of the **Property** parameter.</span></span> <span data-ttu-id="9b7c1-120">Det här kommandot visar heltalen från 1 till 20, grupperat efter strider och även.</span><span class="sxs-lookup"><span data-stu-id="9b7c1-120">This command displays the integers from 1 to 20, grouped by odds and even.</span></span>

```powershell
1..20 | Group-Object -Property {$_ % 2}
```

```Output
Count Name                      Group
----- ----                      -----
   10 0                         {2, 4, 6, 8...}
   10 1                         {1, 3, 5, 7...}
```

### <span data-ttu-id="9b7c1-121">Exempel 3: gruppera händelse logg händelser efter EntryType</span><span class="sxs-lookup"><span data-stu-id="9b7c1-121">Example 3: Group event log events by EntryType</span></span>

<span data-ttu-id="9b7c1-122">I det här exemplet visas de 1 000 senaste posterna i system händelse loggen, grupperade efter **EntryType**.</span><span class="sxs-lookup"><span data-stu-id="9b7c1-122">This example displays the 1,000 most recent entries in the System event log, grouped by **EntryType**.</span></span>

<span data-ttu-id="9b7c1-123">I utdata representerar kolumnen **Count** antalet poster i varje grupp.</span><span class="sxs-lookup"><span data-stu-id="9b7c1-123">In the output, the **Count** column represents the number of entries in each group.</span></span> <span data-ttu-id="9b7c1-124">Kolumnen **namn** representerar de **EventType** -värden som definierar en grupp.</span><span class="sxs-lookup"><span data-stu-id="9b7c1-124">The **Name** column represents the **EventType** values that define a group.</span></span> <span data-ttu-id="9b7c1-125">**Grupp** kolumnen representerar objekten i varje grupp.</span><span class="sxs-lookup"><span data-stu-id="9b7c1-125">The **Group** column represents the objects in each group.</span></span>

```powershell
Get-WinEvent -LogName System -MaxEvents 1000 | Group-Object -Property LevelDisplayName
```

```Output
Count Name          Group
----- ----          -----
  153 Error         {System.Diagnostics.Eventing.Reader.EventLogRecord, System.Diagnostics...}
  722 Information   {System.Diagnostics.Eventing.Reader.EventLogRecord, System.Diagnostics...}
  125 Warning       {System.Diagnostics.Eventing.Reader.EventLogRecord, System.Diagnostics...}
```

### <span data-ttu-id="9b7c1-126">Exempel 4: gruppera processer efter prioritets klass</span><span class="sxs-lookup"><span data-stu-id="9b7c1-126">Example 4: Group processes by priority class</span></span>

<span data-ttu-id="9b7c1-127">Det här exemplet visar effekterna av **Noelement** -parametern.</span><span class="sxs-lookup"><span data-stu-id="9b7c1-127">This example demonstrates the effect of the **NoElement** parameter.</span></span> <span data-ttu-id="9b7c1-128">De här kommandona grupperar processerna på datorn efter prioritets klass.</span><span class="sxs-lookup"><span data-stu-id="9b7c1-128">These commands group the processes on the computer by priority class.</span></span>

<span data-ttu-id="9b7c1-129">Det första kommandot använder `Get-Process` cmdleten för att hämta processerna på datorn och skickar de objekt som ligger nere i pipelinen.</span><span class="sxs-lookup"><span data-stu-id="9b7c1-129">The first command uses the `Get-Process` cmdlet to get the processes on the computer and sends the objects down the pipeline.</span></span> <span data-ttu-id="9b7c1-130">`Group-Object`grupperar objekten efter värdet för processens **priorityClass** -egenskap.</span><span class="sxs-lookup"><span data-stu-id="9b7c1-130">`Group-Object`groups the objects by the value of the **PriorityClass** property of the process.</span></span>

<span data-ttu-id="9b7c1-131">I det andra exemplet används **Noelement** -parametern för att eliminera medlemmar i gruppen från utdata.</span><span class="sxs-lookup"><span data-stu-id="9b7c1-131">The second example uses the **NoElement** parameter to eliminate the members of the group from the output.</span></span> <span data-ttu-id="9b7c1-132">Resultatet är en tabell med bara egenskap svärdet **Count** och **Name** .</span><span class="sxs-lookup"><span data-stu-id="9b7c1-132">The result is a table with only the **Count** and **Name** property value.</span></span>

<span data-ttu-id="9b7c1-133">Resultatet visas i följande exempel på utdata.</span><span class="sxs-lookup"><span data-stu-id="9b7c1-133">The results are shown in the following sample output.</span></span>

```powershell
Get-Process | Group-Object -Property PriorityClass
```

```Output
Count Name         Group
----- ----         -----
   55 Normal       {System.Diagnostics.Process (AdtAgent), System.Diagnosti...
    1              {System.Diagnostics.Process (Idle)}
    3 High         {System.Diagnostics.Process (Newproc), System.Diagnostic...
    2 BelowNormal  {System.Diagnostics.Process (winperf),
```

```powershell
Get-Process | Group-Object -Property PriorityClass -NoElement
```

```Output
Count Name
----- ----
   55 Normal
    1
    3 High
    2 BelowNormal
```

### <span data-ttu-id="9b7c1-134">Exempel 5: gruppera processer efter namn</span><span class="sxs-lookup"><span data-stu-id="9b7c1-134">Example 5: Group processes by name</span></span>

<span data-ttu-id="9b7c1-135">I följande exempel används `Group-Object` för att gruppera flera instanser av processer som körs på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="9b7c1-135">The following example uses `Group-Object` to group multiple instances of processes running on the local computer.</span></span> <span data-ttu-id="9b7c1-136">`Where-Object` visar processer med fler än en instans.</span><span class="sxs-lookup"><span data-stu-id="9b7c1-136">`Where-Object` displays processes with more than one instance.</span></span>

```powershell
Get-Process | Group-Object -Property Name -NoElement | Where-Object {$_.Count -gt 1}
```

```Output
Count Name
----- ----
2     csrss
5     svchost
2     winlogon
2     wmiprvse
```

### <span data-ttu-id="9b7c1-137">Exempel 6: gruppera objekt i en hash-tabell</span><span class="sxs-lookup"><span data-stu-id="9b7c1-137">Example 6: Group objects in a hash table</span></span>

<span data-ttu-id="9b7c1-138">I det här exemplet används parametrarna **AsHashTable** och **enstring** för att returnera grupperna i en hash-tabell som en samling nyckel/värde-par.</span><span class="sxs-lookup"><span data-stu-id="9b7c1-138">This example uses the **AsHashTable** and **AsString** parameters to return the groups in a hash table, as a collection of key-value pairs.</span></span>

<span data-ttu-id="9b7c1-139">I den resulterande hash-tabellen är varje egenskaps värde en nyckel och grupp elementen är värdena.</span><span class="sxs-lookup"><span data-stu-id="9b7c1-139">In the resulting hash table, each property value is a key, and the group elements are the values.</span></span>
<span data-ttu-id="9b7c1-140">Eftersom varje nyckel är en egenskap för hash-tabellen, kan du använda punkt notation för att visa värdena.</span><span class="sxs-lookup"><span data-stu-id="9b7c1-140">Because each key is a property of the hash table object, you can use dot notation to display the values.</span></span>

<span data-ttu-id="9b7c1-141">Det första kommandot hämtar `Get` -och `Set` -cmdletarna i sessionen, grupperas efter verb, returnerar grupperna som en hash-tabell och sparar hash-tabellen i `$A` variabeln.</span><span class="sxs-lookup"><span data-stu-id="9b7c1-141">The first command gets the `Get` and `Set` cmdlets in the session, groups them by verb, returns the groups as a hash table, and saves the hash table in the `$A` variable.</span></span>

<span data-ttu-id="9b7c1-142">Det andra kommandot visar hash-tabellen i `$A` .</span><span class="sxs-lookup"><span data-stu-id="9b7c1-142">The second command displays the hash table in `$A`.</span></span> <span data-ttu-id="9b7c1-143">Det finns två nyckel/värde-par, en för `Get` cmdletarna och en för `Set` cmdletarna.</span><span class="sxs-lookup"><span data-stu-id="9b7c1-143">There are two key-value pairs, one for the `Get` cmdlets and one for the `Set` cmdlets.</span></span>

<span data-ttu-id="9b7c1-144">Det tredje kommandot använder punkt notation `$A.Get` för att visa värdena för **Get** -nyckeln i `$A` .</span><span class="sxs-lookup"><span data-stu-id="9b7c1-144">The third command uses dot notation, `$A.Get` to display the values of the **Get** key in `$A`.</span></span> <span data-ttu-id="9b7c1-145">Värdena är **CmdletInfo** -objekt.</span><span class="sxs-lookup"><span data-stu-id="9b7c1-145">The values are **CmdletInfo** object.</span></span> <span data-ttu-id="9b7c1-146">Parametern **enstring** konverterar inte objekten i grupperna till strängar.</span><span class="sxs-lookup"><span data-stu-id="9b7c1-146">The **AsString** parameter doesn't convert the objects in the groups to strings.</span></span>

```powershell
$A = Get-Command Get-*, Set-* -CommandType cmdlet | Group-Object -Property Verb -AsHashTable -AsString
$A
```

```Output
Name     Value
----     -----
Get      {Get-Acl, Get-Alias, Get-AppLockerFileInformation, Get-AppLockerPolicy...}
Set      {Set-Acl, Set-Alias, Set-AppBackgroundTaskResourcePolicy, Set-AppLockerPolicy...}
```

```powershell
$A.Get
```

```Output
CommandType     Name                               Version    Source
-----------     ----                               -------    ------
Cmdlet          Get-Acl                            6.1.0.0    Microsoft.PowerShell.Security
Cmdlet          Get-Alias                          6.1.0.0    Microsoft.PowerShell.Utility
Cmdlet          Get-AuthenticodeSignature          6.1.0.0    Microsoft.PowerShell.Security
Cmdlet          Get-ChildItem                      6.1.0.0    Microsoft.PowerShell.Management
...
```

## <span data-ttu-id="9b7c1-147">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="9b7c1-147">PARAMETERS</span></span>

### <span data-ttu-id="9b7c1-148">-AsHashTable</span><span class="sxs-lookup"><span data-stu-id="9b7c1-148">-AsHashTable</span></span>

<span data-ttu-id="9b7c1-149">Anger att denna cmdlet returnerar gruppen som en hash-tabell.</span><span class="sxs-lookup"><span data-stu-id="9b7c1-149">Indicates that this cmdlet returns the group as a hash table.</span></span> <span data-ttu-id="9b7c1-150">Nycklarna för hash-tabellen är de egenskaps värden som objekten grupperas med.</span><span class="sxs-lookup"><span data-stu-id="9b7c1-150">The keys of the hash table are the property values by which the objects are grouped.</span></span> <span data-ttu-id="9b7c1-151">Värdena för hash-tabellen är de objekt som har det egenskap svärdet.</span><span class="sxs-lookup"><span data-stu-id="9b7c1-151">The values of the hash table are the objects that have that property value.</span></span>

<span data-ttu-id="9b7c1-152">**AsHashTable** -parametern returnerar däremot varje hash-tabell där varje nyckel är en instans av det grupperade objektet.</span><span class="sxs-lookup"><span data-stu-id="9b7c1-152">By itself, the **AsHashTable** parameter returns each hash table in which each key is an instance of the grouped object.</span></span> <span data-ttu-id="9b7c1-153">Nycklarna i hash-tabellen är strängar när de används med parametern **enstring** .</span><span class="sxs-lookup"><span data-stu-id="9b7c1-153">When used with the **AsString** parameter, the keys in the hash table are strings.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: AHT

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="9b7c1-154">-Uppsträng</span><span class="sxs-lookup"><span data-stu-id="9b7c1-154">-AsString</span></span>

<span data-ttu-id="9b7c1-155">Anger att denna cmdlet konverterar hash-tabellens nycklar till strängar.</span><span class="sxs-lookup"><span data-stu-id="9b7c1-155">Indicates that this cmdlet converts the hash table keys to strings.</span></span> <span data-ttu-id="9b7c1-156">Nycklar för hash-tabellen är som standard instanser av det grupperade objektet.</span><span class="sxs-lookup"><span data-stu-id="9b7c1-156">By default, the hash table keys are instances of the grouped object.</span></span> <span data-ttu-id="9b7c1-157">Den här parametern är endast giltig när den används med parametern **AsHashTable** .</span><span class="sxs-lookup"><span data-stu-id="9b7c1-157">This parameter is valid only when used with the **AsHashTable** parameter.</span></span>

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

### <span data-ttu-id="9b7c1-158">-CaseSensitive</span><span class="sxs-lookup"><span data-stu-id="9b7c1-158">-CaseSensitive</span></span>

<span data-ttu-id="9b7c1-159">Anger att denna cmdlet gör grupperingen Skift läges känslig.</span><span class="sxs-lookup"><span data-stu-id="9b7c1-159">Indicates that this cmdlet makes the grouping case-sensitive.</span></span> <span data-ttu-id="9b7c1-160">Utan den här parametern kan egenskaps värden för objekt i en grupp ha olika fall.</span><span class="sxs-lookup"><span data-stu-id="9b7c1-160">Without this parameter, the property values of objects in a group might have different cases.</span></span>

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

### <span data-ttu-id="9b7c1-161">– Kultur</span><span class="sxs-lookup"><span data-stu-id="9b7c1-161">-Culture</span></span>

<span data-ttu-id="9b7c1-162">Anger kulturen som ska användas när strängar jämförs.</span><span class="sxs-lookup"><span data-stu-id="9b7c1-162">Specifies the culture to use when comparing strings.</span></span>

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

### <span data-ttu-id="9b7c1-163">– InputObject</span><span class="sxs-lookup"><span data-stu-id="9b7c1-163">-InputObject</span></span>

<span data-ttu-id="9b7c1-164">Anger de objekt som ska grupperas.</span><span class="sxs-lookup"><span data-stu-id="9b7c1-164">Specifies the objects to group.</span></span> <span data-ttu-id="9b7c1-165">Ange en variabel som innehåller objekten eller Skriv ett kommando eller uttryck som hämtar objekten.</span><span class="sxs-lookup"><span data-stu-id="9b7c1-165">Enter a variable that contains the objects, or type a command or expression that gets the objects.</span></span>

<span data-ttu-id="9b7c1-166">När du använder parametern **InputObject** för att skicka en samling objekt till `Group-Object` , `Group-Object` tar emot ett objekt som representerar samlingen.</span><span class="sxs-lookup"><span data-stu-id="9b7c1-166">When you use the **InputObject** parameter to submit a collection of objects to `Group-Object`, `Group-Object` receives one object that represents the collection.</span></span> <span data-ttu-id="9b7c1-167">Därför skapas en enskild grupp med objektet som medlem.</span><span class="sxs-lookup"><span data-stu-id="9b7c1-167">As a result, it creates a single group with that object as its member.</span></span>

<span data-ttu-id="9b7c1-168">Om du vill gruppera objekten i en samling, rör du objekten till `Group-Object` .</span><span class="sxs-lookup"><span data-stu-id="9b7c1-168">To group the objects in a collection, pipe the objects to `Group-Object`.</span></span>

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

### <span data-ttu-id="9b7c1-169">-Noelement</span><span class="sxs-lookup"><span data-stu-id="9b7c1-169">-NoElement</span></span>

<span data-ttu-id="9b7c1-170">Anger att denna cmdlet utelämnar medlemmarna i en grupp från resultaten.</span><span class="sxs-lookup"><span data-stu-id="9b7c1-170">Indicates that this cmdlet omits the members of a group from the results.</span></span>

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

### <span data-ttu-id="9b7c1-171">– Egenskap</span><span class="sxs-lookup"><span data-stu-id="9b7c1-171">-Property</span></span>

<span data-ttu-id="9b7c1-172">Anger egenskaperna för gruppering.</span><span class="sxs-lookup"><span data-stu-id="9b7c1-172">Specifies the properties for grouping.</span></span> <span data-ttu-id="9b7c1-173">Objekten är ordnade i grupper baserat på värdet för den angivna egenskapen.</span><span class="sxs-lookup"><span data-stu-id="9b7c1-173">The objects are arranged into groups based on the value of the specified property.</span></span>

<span data-ttu-id="9b7c1-174">Värdet för **egenskaps** parametern kan vara en ny beräknad egenskap.</span><span class="sxs-lookup"><span data-stu-id="9b7c1-174">The value of the **Property** parameter can be a new calculated property.</span></span> <span data-ttu-id="9b7c1-175">Den beräknade egenskapen kan vara ett skript block eller en hash-tabell.</span><span class="sxs-lookup"><span data-stu-id="9b7c1-175">The calculated property can be a script block or a hash table.</span></span> <span data-ttu-id="9b7c1-176">Giltiga nyckel/värde-par är:</span><span class="sxs-lookup"><span data-stu-id="9b7c1-176">Valid key-value pairs are:</span></span>

- <span data-ttu-id="9b7c1-177">Uttryck- `<string>` eller `<script block>`</span><span class="sxs-lookup"><span data-stu-id="9b7c1-177">Expression - `<string>` or `<script block>`</span></span>

<span data-ttu-id="9b7c1-178">Mer information finns i [about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md).</span><span class="sxs-lookup"><span data-stu-id="9b7c1-178">For more information, see [about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md).</span></span>

```yaml
Type: System.Object[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="9b7c1-179">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="9b7c1-179">CommonParameters</span></span>

<span data-ttu-id="9b7c1-180">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="9b7c1-180">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="9b7c1-181">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="9b7c1-181">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="9b7c1-182">INDATA</span><span class="sxs-lookup"><span data-stu-id="9b7c1-182">INPUTS</span></span>

### <span data-ttu-id="9b7c1-183">System. Management. Automation. PSObject</span><span class="sxs-lookup"><span data-stu-id="9b7c1-183">System.Management.Automation.PSObject</span></span>

<span data-ttu-id="9b7c1-184">Du kan skicka vidare alla objekt till `Group-Object` .</span><span class="sxs-lookup"><span data-stu-id="9b7c1-184">You can pipe any object to `Group-Object`.</span></span>

## <span data-ttu-id="9b7c1-185">UTDATA</span><span class="sxs-lookup"><span data-stu-id="9b7c1-185">OUTPUTS</span></span>

### <span data-ttu-id="9b7c1-186">Microsoft. PowerShell. commands. GroupInfo eller system. Collections. hash</span><span class="sxs-lookup"><span data-stu-id="9b7c1-186">Microsoft.PowerShell.Commands.GroupInfo or System.Collections.Hashtable</span></span>

<span data-ttu-id="9b7c1-187">När du använder parametern **AsHashTable** `Group-Object` returneras ett **hash** -objekt.</span><span class="sxs-lookup"><span data-stu-id="9b7c1-187">When you use the **AsHashTable** parameter, `Group-Object` returns a **Hashtable** object.</span></span>
<span data-ttu-id="9b7c1-188">Annars returnerar den ett **GroupInfo** -objekt.</span><span class="sxs-lookup"><span data-stu-id="9b7c1-188">Otherwise, it returns a **GroupInfo** object.</span></span>

## <span data-ttu-id="9b7c1-189">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="9b7c1-189">NOTES</span></span>

<span data-ttu-id="9b7c1-190">Du kan använda parametern **groupby** i cmdletarna för formatering, till exempel `Format-Table` och `Format-List` , för att gruppera objekt.</span><span class="sxs-lookup"><span data-stu-id="9b7c1-190">You can use the **GroupBy** parameter of the formatting cmdlets, such as `Format-Table` and `Format-List`, to group objects.</span></span> <span data-ttu-id="9b7c1-191">Till skillnad från `Group-Object` , som skapar en enskild tabell med en rad för varje egenskaps värde, skapar **groupby** -parametrarna en tabell för varje egenskaps värde med en rad för varje objekt som har egenskap svärdet.</span><span class="sxs-lookup"><span data-stu-id="9b7c1-191">Unlike `Group-Object`, which creates a single table with a row for each property value, the **GroupBy** parameters create a table for each property value with a row for each item that has the property value.</span></span>

<span data-ttu-id="9b7c1-192">`Group-Object` kräver inte att de objekt som grupperas är av samma Microsoft .NET Core-typ.</span><span class="sxs-lookup"><span data-stu-id="9b7c1-192">`Group-Object` doesn't require that the objects being grouped are of the same Microsoft .NET Core type.</span></span> <span data-ttu-id="9b7c1-193">När du grupperar objekt av olika .NET Core-typer, `Group-Object` använder följande regler:</span><span class="sxs-lookup"><span data-stu-id="9b7c1-193">When grouping objects of different .NET Core types, `Group-Object` uses the following rules:</span></span>

- <span data-ttu-id="9b7c1-194">Samma egenskaps namn och-typer.</span><span class="sxs-lookup"><span data-stu-id="9b7c1-194">Same Property Names and Types.</span></span>

  <span data-ttu-id="9b7c1-195">Om objekten har en egenskap med det angivna namnet och egenskapsvärdena har samma .NET Core-typ grupperas egenskapsvärdena genom att använda samma regler som skulle användas för objekt av samma typ.</span><span class="sxs-lookup"><span data-stu-id="9b7c1-195">If the objects have a property with the specified name, and the property values have the same .NET Core type, the property values are grouped by using the same rules that would be used for objects of the same type.</span></span>

- <span data-ttu-id="9b7c1-196">Samma egenskaps namn, olika typer.</span><span class="sxs-lookup"><span data-stu-id="9b7c1-196">Same Property Names, Different Types.</span></span>

  <span data-ttu-id="9b7c1-197">Om objekten har en egenskap med det angivna namnet, men egenskapsvärdena har en annan .NET Core-typ i olika objekt, `Group-Object` använder .net Core-typen för den första förekomsten av egenskapen som .net Core-typ för den egenskaps gruppen.</span><span class="sxs-lookup"><span data-stu-id="9b7c1-197">If the objects have a property with the specified name, but the property values have a different .NET Core type in different objects, `Group-Object` uses the .NET Core type of the first occurrence of the property as the .NET Core type for that property group.</span></span> <span data-ttu-id="9b7c1-198">När ett objekt har en egenskap med en annan typ, konverteras egenskap svärdet till typen för den gruppen.</span><span class="sxs-lookup"><span data-stu-id="9b7c1-198">When an object has a property with a different type, the property value is converted to the type for that group.</span></span> <span data-ttu-id="9b7c1-199">Om typ konverteringen Miss lyckas tas objektet inte med i gruppen.</span><span class="sxs-lookup"><span data-stu-id="9b7c1-199">If the type conversion fails, the object isn't included in the group.</span></span>

- <span data-ttu-id="9b7c1-200">Egenskaper saknas.</span><span class="sxs-lookup"><span data-stu-id="9b7c1-200">Missing Properties.</span></span>

  <span data-ttu-id="9b7c1-201">Objekt som inte har någon angiven egenskap kan inte grupperas.</span><span class="sxs-lookup"><span data-stu-id="9b7c1-201">Objects that don't have a specified property can't be grouped.</span></span> <span data-ttu-id="9b7c1-202">Objekt som inte är grupperade visas i det slutliga **GroupInfo** objektets utdata i en grupp med namnet `AutomationNull.Value` .</span><span class="sxs-lookup"><span data-stu-id="9b7c1-202">Objects that aren't grouped appear in the final **GroupInfo** object output in a group named `AutomationNull.Value`.</span></span>

## <span data-ttu-id="9b7c1-203">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="9b7c1-203">RELATED LINKS</span></span>

[<span data-ttu-id="9b7c1-204">about_Calculated_Properties</span><span class="sxs-lookup"><span data-stu-id="9b7c1-204">about_Calculated_Properties</span></span>](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md)

[<span data-ttu-id="9b7c1-205">about_Hash_Tables</span><span class="sxs-lookup"><span data-stu-id="9b7c1-205">about_Hash_Tables</span></span>](../Microsoft.PowerShell.Core/About/about_Hash_Tables.md)

[<span data-ttu-id="9b7c1-206">Jämför objekt</span><span class="sxs-lookup"><span data-stu-id="9b7c1-206">Compare-Object</span></span>](Compare-Object.md)

[<span data-ttu-id="9b7c1-207">-Objekt</span><span class="sxs-lookup"><span data-stu-id="9b7c1-207">ForEach-Object</span></span>](../Microsoft.PowerShell.Core/ForEach-Object.md)

[<span data-ttu-id="9b7c1-208">Mått – objekt</span><span class="sxs-lookup"><span data-stu-id="9b7c1-208">Measure-Object</span></span>](Measure-Object.md)

[<span data-ttu-id="9b7c1-209">Nytt – objekt</span><span class="sxs-lookup"><span data-stu-id="9b7c1-209">New-Object</span></span>](New-Object.md)

[<span data-ttu-id="9b7c1-210">Select-Object</span><span class="sxs-lookup"><span data-stu-id="9b7c1-210">Select-Object</span></span>](Select-Object.md)

[<span data-ttu-id="9b7c1-211">Sortera objekt</span><span class="sxs-lookup"><span data-stu-id="9b7c1-211">Sort-Object</span></span>](Sort-Object.md)

[<span data-ttu-id="9b7c1-212">Tee – objekt</span><span class="sxs-lookup"><span data-stu-id="9b7c1-212">Tee-Object</span></span>](Tee-Object.md)

[<span data-ttu-id="9b7c1-213">Where-objekt</span><span class="sxs-lookup"><span data-stu-id="9b7c1-213">Where-Object</span></span>](../Microsoft.PowerShell.Core/Where-Object.md)
