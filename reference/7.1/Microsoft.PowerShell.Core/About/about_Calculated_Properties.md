---
description: PowerShell ger möjlighet att dynamiskt lägga till nya egenskaper och ändra formateringen av objekts utdata till pipelinen.
Locale: en-US
ms.date: 08/07/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_calculated_properties?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Calculated_Properties
ms.openlocfilehash: 1ecc621d05cb340f6792481df483249095ed63a2
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/13/2020
ms.locfileid: "93272631"
---
# <a name="about-calculated-properties"></a><span data-ttu-id="4ad4c-103">Om beräknade egenskaper</span><span class="sxs-lookup"><span data-stu-id="4ad4c-103">About calculated properties</span></span>

## <a name="short-description"></a><span data-ttu-id="4ad4c-104">Kort beskrivning</span><span class="sxs-lookup"><span data-stu-id="4ad4c-104">Short Description</span></span>

<span data-ttu-id="4ad4c-105">PowerShell ger möjlighet att dynamiskt lägga till nya egenskaper och ändra formateringen av objekts utdata till pipelinen.</span><span class="sxs-lookup"><span data-stu-id="4ad4c-105">PowerShell provides the ability to dynamically add new properties and alter the formatting of objects output to the pipeline.</span></span>

## <a name="long-description"></a><span data-ttu-id="4ad4c-106">Lång beskrivning</span><span class="sxs-lookup"><span data-stu-id="4ad4c-106">Long Description</span></span>

<span data-ttu-id="4ad4c-107">Ett antal PowerShell-cmdletar transformerar, aggregerar eller bearbetar indata till utgående objekt med parametrar som tillåter tillägg av nya egenskaper till dessa utdata-objekt.</span><span class="sxs-lookup"><span data-stu-id="4ad4c-107">A number of PowerShell cmdlets transform, aggregate, or process input objects into output objects using parameters that allow the addition of new properties to those output objects.</span></span> <span data-ttu-id="4ad4c-108">Dessa parametrar kan användas för att generera nya, beräknade egenskaper för utgående objekt baserat på värdena för indata-objekt.</span><span class="sxs-lookup"><span data-stu-id="4ad4c-108">These parameters can be used to generate new, calculated properties on output objects based on the values of input objects.</span></span>
<span data-ttu-id="4ad4c-109">Den beräknade egenskapen definieras av en [hash](about_hash_tables.md) som innehåller nyckel/värde-par som anger namnet på den nya egenskapen, ett uttryck för att beräkna värdet och eventuell formateringsinformation.</span><span class="sxs-lookup"><span data-stu-id="4ad4c-109">The calculated property is defined by a [hashtable](about_hash_tables.md) containing key-value pairs that specify the name of the new property, an expression to calculate the value, and optional formatting information.</span></span>

## <a name="supported-cmdlets"></a><span data-ttu-id="4ad4c-110">Cmdlets som stöds</span><span class="sxs-lookup"><span data-stu-id="4ad4c-110">Supported cmdlets</span></span>

<span data-ttu-id="4ad4c-111">Följande cmdletar stöder beräknade egenskaps värden för **egenskaps** parametern.</span><span class="sxs-lookup"><span data-stu-id="4ad4c-111">The following cmdlets support calculated property values for the **Property** parameter.</span></span> <span data-ttu-id="4ad4c-112">`Format-*`Cmdletarna stöder också beräknade värden för **groupby** -parametern.</span><span class="sxs-lookup"><span data-stu-id="4ad4c-112">The `Format-*` cmdlets also support calculated values for the **GroupBy** parameter.</span></span>

<span data-ttu-id="4ad4c-113">I följande lista specificeras de cmdletar som stöder beräknade egenskaper och nyckel/värde-par som stöds av varje cmdlet.</span><span class="sxs-lookup"><span data-stu-id="4ad4c-113">The following list itemizes the cmdlets that support calculated properties and the key-value pairs that are supported by each cmdlet.</span></span>

- `Compare-Object`
  - `expression`

- `ConvertTo-Html`
  - <span data-ttu-id="4ad4c-114">`name`/`label` – valfritt (lades till i PowerShell 6. x)</span><span class="sxs-lookup"><span data-stu-id="4ad4c-114">`name`/`label` - optional (added in PowerShell 6.x)</span></span>
  - `expression`
  - <span data-ttu-id="4ad4c-115">`width` – valfritt</span><span class="sxs-lookup"><span data-stu-id="4ad4c-115">`width` - optional</span></span>
  - <span data-ttu-id="4ad4c-116">`alignment` – valfritt</span><span class="sxs-lookup"><span data-stu-id="4ad4c-116">`alignment` - optional</span></span>

- `Format-Custom`
  - `expression`
  - <span data-ttu-id="4ad4c-117">`depth` – valfritt</span><span class="sxs-lookup"><span data-stu-id="4ad4c-117">`depth` - optional</span></span>

- `Format-List`
  - <span data-ttu-id="4ad4c-118">`name`/`label` – valfritt</span><span class="sxs-lookup"><span data-stu-id="4ad4c-118">`name`/`label` - optional</span></span>
  - `expression`
  - <span data-ttu-id="4ad4c-119">`formatstring` – valfritt</span><span class="sxs-lookup"><span data-stu-id="4ad4c-119">`formatstring` - optional</span></span>

  <span data-ttu-id="4ad4c-120">Samma uppsättning nyckel/värde-par gäller också beräknade egenskaps värden som skickas till **groupby** -parametern för alla `Format-*` cmdletar.</span><span class="sxs-lookup"><span data-stu-id="4ad4c-120">This same set of key-value pairs also apply to calculated property values passed to the **GroupBy** parameter for all `Format-*` cmdlets.</span></span>

- `Format-Table`
  - <span data-ttu-id="4ad4c-121">`name`/`label` – valfritt</span><span class="sxs-lookup"><span data-stu-id="4ad4c-121">`name`/`label` - optional</span></span>
  - `expression`
  - <span data-ttu-id="4ad4c-122">`formatstring` – valfritt</span><span class="sxs-lookup"><span data-stu-id="4ad4c-122">`formatstring` - optional</span></span>
  - <span data-ttu-id="4ad4c-123">`width` – valfritt</span><span class="sxs-lookup"><span data-stu-id="4ad4c-123">`width` - optional</span></span>
  - <span data-ttu-id="4ad4c-124">`alignment` – valfritt</span><span class="sxs-lookup"><span data-stu-id="4ad4c-124">`alignment` - optional</span></span>

- `Format-Wide`
  - `expression`
  - <span data-ttu-id="4ad4c-125">`formatstring` – valfritt</span><span class="sxs-lookup"><span data-stu-id="4ad4c-125">`formatstring` - optional</span></span>

- `Group-Object`
  - `expression`

- `Measure-Object`
  - <span data-ttu-id="4ad4c-126">Stöder endast ett skript block för uttrycket, inte en hash-tabellen.</span><span class="sxs-lookup"><span data-stu-id="4ad4c-126">Only supports a script block for the expression, not a hashtable.</span></span>
  - <span data-ttu-id="4ad4c-127">Stöds inte i PowerShell 5,1 och äldre.</span><span class="sxs-lookup"><span data-stu-id="4ad4c-127">Not supported in PowerShell 5.1 and older.</span></span>

- `Select-Object`
  - <span data-ttu-id="4ad4c-128">`name`/`label` – valfritt</span><span class="sxs-lookup"><span data-stu-id="4ad4c-128">`name`/`label` - optional</span></span>
  - `expression`

- `Sort-Object`
  - `expression`
  - <span data-ttu-id="4ad4c-129">`ascending`/`descending` – valfritt</span><span class="sxs-lookup"><span data-stu-id="4ad4c-129">`ascending`/`descending` - optional</span></span>

> [!NOTE]
> <span data-ttu-id="4ad4c-130">Värdet för `expression` kan vara ett skript block i stället för en hash-tabellen.</span><span class="sxs-lookup"><span data-stu-id="4ad4c-130">The value of the `expression` can be a script block instead of a hashtable.</span></span> <span data-ttu-id="4ad4c-131">Mer information finns i avsnittet om [anteckningar](#notes) .</span><span class="sxs-lookup"><span data-stu-id="4ad4c-131">For more information, see the [Notes](#notes) section.</span></span>

## <a name="hashtable-key-definitions"></a><span data-ttu-id="4ad4c-132">Nyckel definitioner för hash</span><span class="sxs-lookup"><span data-stu-id="4ad4c-132">Hashtable key definitions</span></span>

- <span data-ttu-id="4ad4c-133">`name`/`label` -Anger namnet på den egenskap som skapas.</span><span class="sxs-lookup"><span data-stu-id="4ad4c-133">`name`/`label` - Specifies the name of the property being created.</span></span> <span data-ttu-id="4ad4c-134">Du kan använda `name` eller dess alias, `label` och de är utbytbara.</span><span class="sxs-lookup"><span data-stu-id="4ad4c-134">You can use `name` or its alias, `label`, interchangeably.</span></span>
- <span data-ttu-id="4ad4c-135">`expression` – Ett skript block som används för att beräkna värdet för den nya egenskapen.</span><span class="sxs-lookup"><span data-stu-id="4ad4c-135">`expression` - A script block used to calculate the value of the new property.</span></span>
- <span data-ttu-id="4ad4c-136">`alignment` – Används av cmdletar som producerar tabell data för att definiera hur värdena visas i en kolumn.</span><span class="sxs-lookup"><span data-stu-id="4ad4c-136">`alignment` - Used by cmdlets that produce tabular output to define how the values are displayed in a column.</span></span> <span data-ttu-id="4ad4c-137">Värdet måste vara `'left'` , `'center'` eller `'right'` .</span><span class="sxs-lookup"><span data-stu-id="4ad4c-137">The value must be `'left'`, `'center'`, or `'right'`.</span></span>
- <span data-ttu-id="4ad4c-138">`formatstring` -Anger en format sträng som definierar hur värdet formateras för utdata.</span><span class="sxs-lookup"><span data-stu-id="4ad4c-138">`formatstring` - Specifies a format string that defines how the value is formatted for output.</span></span> <span data-ttu-id="4ad4c-139">Mer information om format strängar finns i [format typer i .net](/dotnet/standard/base-types/formatting-types).</span><span class="sxs-lookup"><span data-stu-id="4ad4c-139">For more information about format strings, see [Format types in .NET](/dotnet/standard/base-types/formatting-types).</span></span>
- <span data-ttu-id="4ad4c-140">`width` -Anger kolumnen maximal bredd i en tabell när värdet visas.</span><span class="sxs-lookup"><span data-stu-id="4ad4c-140">`width` - Specifies the maximum width column in a table when the value is displayed.</span></span> <span data-ttu-id="4ad4c-141">Värdet måste vara större än `0` .</span><span class="sxs-lookup"><span data-stu-id="4ad4c-141">The value must be greater than `0`.</span></span>
- <span data-ttu-id="4ad4c-142">`depth` – Parametern **djup** för `Format-Custom` anger djupet för expansionen för alla egenskaper.</span><span class="sxs-lookup"><span data-stu-id="4ad4c-142">`depth` - The **Depth** parameter of `Format-Custom` specifies the depth of expansion for all properties.</span></span> <span data-ttu-id="4ad4c-143">Med `depth` nyckeln kan du ange djupet för expansion per egenskap.</span><span class="sxs-lookup"><span data-stu-id="4ad4c-143">The `depth` key allows you to specify the depth of expansion per property.</span></span>
- <span data-ttu-id="4ad4c-144">`ascending` / `descending` – Gör att du kan ange sorterings ordningen för en eller flera egenskaper.</span><span class="sxs-lookup"><span data-stu-id="4ad4c-144">`ascending` / `descending` - Allows you to specify the order of sorting for one or more properties.</span></span> <span data-ttu-id="4ad4c-145">Dessa är booleska värden.</span><span class="sxs-lookup"><span data-stu-id="4ad4c-145">These are boolean values.</span></span>

<span data-ttu-id="4ad4c-146">Hash-nycklarna behöver inte stavas ut så länge det angivna namnet är oklart.</span><span class="sxs-lookup"><span data-stu-id="4ad4c-146">The hashtable keys need not be spelled out as long as the specified name prefix is unambiguous.</span></span> <span data-ttu-id="4ad4c-147">Kan till exempel `n` användas i stället för `Name` och `e` kan användas i stället för `Expression` .</span><span class="sxs-lookup"><span data-stu-id="4ad4c-147">For example, `n` can be used in lieu of `Name` and `e` can be used in lieu of `Expression`.</span></span>

## <a name="examples"></a><span data-ttu-id="4ad4c-148">Exempel</span><span class="sxs-lookup"><span data-stu-id="4ad4c-148">Examples</span></span>

### <a name="compare-object"></a><span data-ttu-id="4ad4c-149">Compare-Object</span><span class="sxs-lookup"><span data-stu-id="4ad4c-149">Compare-Object</span></span>

<span data-ttu-id="4ad4c-150">Med beräknade egenskaper kan du styra hur egenskaperna för inobjekten ska jämföras.</span><span class="sxs-lookup"><span data-stu-id="4ad4c-150">With calculated properties, you can control how the properties of the input objects are compared.</span></span> <span data-ttu-id="4ad4c-151">I det här exemplet i stället för att jämföra värdena direkt, jämförs värdena med resultatet av den aritmetiska åtgärden (modul 2).</span><span class="sxs-lookup"><span data-stu-id="4ad4c-151">In this example, rather than comparing the values directly, the values are compared to the result of the arithmetic operation (modulus of 2).</span></span>

```powershell
Compare-Object @{p=1} @{p=2} -property @{ Expression = { $_.p % 2 } }
```

```Output
 $_.p % 2  SideIndicator
---------- -------------
         0 =>
         1 <=
```

### <a name="convertto-html"></a><span data-ttu-id="4ad4c-152">ConvertTo-Html</span><span class="sxs-lookup"><span data-stu-id="4ad4c-152">ConvertTo-Html</span></span>

<span data-ttu-id="4ad4c-153">`ConvertTo-Html` kan konvertera en samling objekt till en HTML-tabell.</span><span class="sxs-lookup"><span data-stu-id="4ad4c-153">`ConvertTo-Html` can convert a collection of objects to an HTML table.</span></span>
<span data-ttu-id="4ad4c-154">Med beräknade egenskaper kan du styra hur tabellen presenteras.</span><span class="sxs-lookup"><span data-stu-id="4ad4c-154">Calculated properties allow you to control how the table is presented.</span></span>

```powershell
Get-Alias |
  ConvertTo-Html Name,
                 Definition,
                 @{
                    name='ParameterCount'
                    expr={$_.Parameters.Keys.Count}
                    align='center'
                 } |
    Out-File .\aliases.htm -Force
```

<span data-ttu-id="4ad4c-155">I det här exemplet skapas en HTML-tabell som innehåller en lista med PowerShell-alias och antalet parametrar för varje aliased-kommando.</span><span class="sxs-lookup"><span data-stu-id="4ad4c-155">This example creates an HTML table containing a list of PowerShell aliases and the number parameters for each aliased command.</span></span> <span data-ttu-id="4ad4c-156">Värdena för **ParameterCount** -kolumnen centreras.</span><span class="sxs-lookup"><span data-stu-id="4ad4c-156">The values of **ParameterCount** column are centered.</span></span>

### <a name="format-custom"></a><span data-ttu-id="4ad4c-157">Format-Custom</span><span class="sxs-lookup"><span data-stu-id="4ad4c-157">Format-Custom</span></span>

<span data-ttu-id="4ad4c-158">`Format-Custom` innehåller en anpassad vy av ett objekt i ett format som liknar en klass definition.</span><span class="sxs-lookup"><span data-stu-id="4ad4c-158">`Format-Custom` provides a custom view of an object in a format similar to a class definition.</span></span> <span data-ttu-id="4ad4c-159">Mer komplexa objekt kan innehålla medlemmar som är djupt kapslade med komplexa typer.</span><span class="sxs-lookup"><span data-stu-id="4ad4c-159">More complex objects can contain members that are deeply nested with complex types.</span></span> <span data-ttu-id="4ad4c-160">Parametern **djup** i `Format-Custom` anger djupet för expansionen för alla egenskaper.</span><span class="sxs-lookup"><span data-stu-id="4ad4c-160">The **Depth** parameter of `Format-Custom` specifies the depth of expansion for all properties.</span></span> <span data-ttu-id="4ad4c-161">Med `depth` nyckeln kan du ange djupet för expansion per egenskap.</span><span class="sxs-lookup"><span data-stu-id="4ad4c-161">The `depth` key allows you to specify the depth of expansion per property.</span></span>

<span data-ttu-id="4ad4c-162">I det här exemplet `depth` fören klar nyckeln den anpassade utdata för `Get-Date` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="4ad4c-162">In this example, the `depth` key simplifies the custom output for the `Get-Date` cmdlet.</span></span> <span data-ttu-id="4ad4c-163">`Get-Date` Returnerar ett **datetime** -objekt.</span><span class="sxs-lookup"><span data-stu-id="4ad4c-163">`Get-Date` returns a **DateTime** object.</span></span> <span data-ttu-id="4ad4c-164">**Datum** egenskapen för det här objektet är också ett **datetime** -objekt, så objektet är kapslat.</span><span class="sxs-lookup"><span data-stu-id="4ad4c-164">The **Date** property of this object is also a **DateTime** object, so the object is nested.</span></span>

```powershell
Get-Date | Format-Custom @{expr={$_.Date};depth=1},TimeOfDay
```

```Output
class DateTime
{
  $_.Date =
    class DateTime
    {
      Date = 8/7/2020 12:00:00 AM
      Day = 7
      DayOfWeek = Friday
      DayOfYear = 220
      Hour = 0
      Kind = Local
      Millisecond = 0
      Minute = 0
      Month = 8
      Second = 0
      Ticks = 637323552000000000
      TimeOfDay = 00:00:00
      Year = 2020
      DateTime = Friday, August 07, 2020 12:00:00 AM
    }
  TimeOfDay =
    class TimeSpan
    {
      Ticks = 435031592302
      Days = 0
      Hours = 12
      Milliseconds = 159
      Minutes = 5
      Seconds = 3
      TotalDays = 0.503508787386574
      TotalHours = 12.0842108972778
      TotalMilliseconds = 43503159.2302
      TotalMinutes = 725.052653836667
      TotalSeconds = 43503.1592302
    }
}
```

### <a name="format-list"></a><span data-ttu-id="4ad4c-165">Format-List</span><span class="sxs-lookup"><span data-stu-id="4ad4c-165">Format-List</span></span>

<span data-ttu-id="4ad4c-166">I det här exemplet använder vi beräknade egenskaper för att ändra namn och format på utdata från `Get-ChildItem` .</span><span class="sxs-lookup"><span data-stu-id="4ad4c-166">In this example, we use calculated properties to change the name and format of the output from `Get-ChildItem`.</span></span>

```powershell
Get-ChildItem *.json -File |
  Format-List Fullname,
              @{
                 name='Modified'
                 expression={$_.LastWriteTime}
                 formatstring='O'
              },
              @{
                 name='Size'
                 expression={$_.Length/1KB}
                 formatstring='N2'
              }
```

```Output
FullName : C:\Git\PS-Docs\PowerShell-Docs\.markdownlint.json
Modified : 2020-07-23T10:26:28.4092457-07:00
Size     : 2.40

FullName : C:\Git\PS-Docs\PowerShell-Docs\.openpublishing.publish.config.json
Modified : 2020-07-23T10:26:28.4092457-07:00
Size     : 2.25

FullName : C:\Git\PS-Docs\PowerShell-Docs\.openpublishing.redirection.json
Modified : 2020-07-27T13:05:24.3887629-07:00
Size     : 324.60
```

### <a name="format-table"></a><span data-ttu-id="4ad4c-167">Format-Table</span><span class="sxs-lookup"><span data-stu-id="4ad4c-167">Format-Table</span></span>

<span data-ttu-id="4ad4c-168">I det här exemplet lägger den beräknade egenskapen till en **typ** -egenskap som används för att klassificera filerna efter innehålls typ.</span><span class="sxs-lookup"><span data-stu-id="4ad4c-168">In this example, the calculated property adds a **Type** property used to classify the files by the content type.</span></span>

```powershell
Get-ChildItem -File |
  Sort-Object extension |
    Format-Table Name, Length -GroupBy @{
      name='Type'
      expression={
        switch ($_.extension) {
          '.md'   {'Content'}
          ''      {'Metacontent'}
          '.ps1'  {'Automation'}
          '.yml'  {'Automation'}
          default {'Configuration'}
        }
      }
    }
```

```Output
   Type: Metacontent

Name              Length
----              ------
ThirdPartyNotices   1229
LICENSE-CODE        1106
LICENSE            19047

   Type: Configuration

Name                                Length
----                                ------
.editorconfig                          183
.gitattributes                         419
.gitignore                             228
.markdownlint.json                    2456
.openpublishing.publish.config.json   2306
.openpublishing.redirection.json    332394
.localization-config                   232

   Type: Content

Name            Length
----            ------
README.md         3355
CONTRIBUTING.md    247

   Type: Automation

Name                      Length
----                      ------
.openpublishing.build.ps1    796
build.ps1                   7495
ci.yml                       645
ci-steps.yml                2035
daily.yml                   1271
```

### <a name="format-wide"></a><span data-ttu-id="4ad4c-169">Format-Wide</span><span class="sxs-lookup"><span data-stu-id="4ad4c-169">Format-Wide</span></span>

<span data-ttu-id="4ad4c-170">Med `Format-Wide` cmdleten kan du Visa värdet för en egenskap för objekt i en samling som en lista med flera kolumner.</span><span class="sxs-lookup"><span data-stu-id="4ad4c-170">The `Format-Wide` cmdlet allows you to display the value of one property for objects in a collection as a multi-column list.</span></span>

<span data-ttu-id="4ad4c-171">I det här exemplet vill vi se fil namnet och storleken (i kilobyte) som en bred lista.</span><span class="sxs-lookup"><span data-stu-id="4ad4c-171">For this example, we want to see the filename and the size (in kilobytes) as a wide listing.</span></span> <span data-ttu-id="4ad4c-172">Eftersom `Format-Wide` visar inte mer än en egenskap, använder vi en beräknad egenskap för att kombinera värdet för två egenskaper till ett enda värde.</span><span class="sxs-lookup"><span data-stu-id="4ad4c-172">Since `Format-Wide` does not display more than one property, we use a calculated property to combine the value of two properties into a single value.</span></span>

```powershell
Get-ChildItem -File |
  Format-Wide -Property @{e={'{0} ({1:N2}kb)' -f $_.name,($_.length/1kb)}}
```

```Output
.editorconfig (0.18kb)                          .gitattributes (0.41kb)
.gitignore (0.22kb)                             .localization-config (0.23kb)
.markdownlint.json (2.40kb)                     .openpublishing.build.ps1 (0.78kb)
.openpublishing.publish.config.json (2.25kb)    .openpublishing.redirection.json (324.60kb)
build.ps1 (7.32kb)                              ci.yml (0.63kb)
ci-steps.yml (1.99kb)                           CONTRIBUTING.md (0.24kb)
daily.yml (1.24kb)                              LICENSE (18.60kb)
LICENSE-CODE (1.08kb)                           README.md (3.28kb)
ThirdPartyNotices (1.20kb)
```

### <a name="group-object"></a><span data-ttu-id="4ad4c-173">Group-Object</span><span class="sxs-lookup"><span data-stu-id="4ad4c-173">Group-Object</span></span>

<span data-ttu-id="4ad4c-174">`Group-Object`Cmdleten visar objekt i grupper baserat på värdet för en angiven egenskap.</span><span class="sxs-lookup"><span data-stu-id="4ad4c-174">The `Group-Object` cmdlet displays objects in groups based on the value of a specified property.</span></span> <span data-ttu-id="4ad4c-175">I det här exemplet räknar den beräknade egenskapen antalet filer av varje innehålls typ.</span><span class="sxs-lookup"><span data-stu-id="4ad4c-175">In this example, the calculated property counts the number of files of each content type.</span></span>

```powershell
Get-ChildItem -File |
  Sort-Object extension |
    Group-Object -NoElement -Property @{
      expression={
        switch ($_.extension) {
          '.md'   {'Content'}
          ''      {'Metacontent'}
          '.ps1'  {'Automation'}
          '.yml'  {'Automation'}
          default {'Configuration'}
        }
      }
    }
```

```Output
Count Name
----- ----
    5 Automation
    7 Configuration
    2 Content
    3 Metacontent
```

### <a name="measure-object"></a><span data-ttu-id="4ad4c-176">Measure-Object</span><span class="sxs-lookup"><span data-stu-id="4ad4c-176">Measure-Object</span></span>

<span data-ttu-id="4ad4c-177">`Measure-Object`Cmdleten beräknar numeriska egenskaper för objekt.</span><span class="sxs-lookup"><span data-stu-id="4ad4c-177">The `Measure-Object` cmdlet calculates the numeric properties of objects.</span></span> <span data-ttu-id="4ad4c-178">I det här exemplet använder vi en beräknad egenskap för att hämta antalet ( **summan** ) av talen, mellan 1 och 10, som är jämnt delbar med 3.</span><span class="sxs-lookup"><span data-stu-id="4ad4c-178">In this example, we use a calculated property to get the count ( **Sum** ) of the numbers, between 1 and 10, that are evenly divisible by 3.</span></span>

```powershell
1..10 | Measure-Object -Property {($_ % 3) -eq 0} -Sum
```

```Output
Count             : 10
Average           :
Sum               : 3
Maximum           :
Minimum           :
StandardDeviation :
Property          : ($_ % 3) -eq 0
```

> [!NOTE]
> <span data-ttu-id="4ad4c-179">Till skillnad från andra cmdletar `Measure-Object` accepterar inte en hash-tabellen för beräknade egenskaper.</span><span class="sxs-lookup"><span data-stu-id="4ad4c-179">Unlike the other cmdlets, `Measure-Object` does not accept a hashtable for calculated properties.</span></span> <span data-ttu-id="4ad4c-180">Du måste använda ett skript block.</span><span class="sxs-lookup"><span data-stu-id="4ad4c-180">You must use a script block.</span></span>

### <a name="select-object"></a><span data-ttu-id="4ad4c-181">Select-Object</span><span class="sxs-lookup"><span data-stu-id="4ad4c-181">Select-Object</span></span>

<span data-ttu-id="4ad4c-182">Du kan använda beräknade egenskaper för att lägga till ytterligare medlemmar i objektets utdata med `Select-Object` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="4ad4c-182">You can use calculated properties to add additional members to the objects output with the `Select-Object` cmdlet.</span></span> <span data-ttu-id="4ad4c-183">I det här exemplet visar vi PowerShell-alias som börjar med bokstaven `C` .</span><span class="sxs-lookup"><span data-stu-id="4ad4c-183">In this example, we are listing the PowerShell aliases that begin with the letter `C`.</span></span> <span data-ttu-id="4ad4c-184">Med hjälp av skickar `Select-Object` vi aliaset, den cmdlet som det mappas till och antalet parametrar som definierats för cmdleten.</span><span class="sxs-lookup"><span data-stu-id="4ad4c-184">Using `Select-Object`, we output the alias, the cmdlet it's mapped to, and a count for the number of parameters defined for the cmdlet.</span></span> <span data-ttu-id="4ad4c-185">Med en beräknad egenskap kan vi skapa egenskapen **ParameterCount** .</span><span class="sxs-lookup"><span data-stu-id="4ad4c-185">Using a calculated property, we can create the **ParameterCount** property.</span></span>

```powershell
$aliases = Get-Alias c* |
  Select-Object Name,
                Definition,
                @{
                    name='ParameterCount'
                    expr={$_.Parameters.Keys.Count}
                }
$aliases | Get-Member
$aliases
```

```Output
   TypeName: Selected.System.Management.Automation.AliasInfo

Name           MemberType   Definition
----           ----------   ----------
Equals         Method       bool Equals(System.Object obj)
GetHashCode    Method       int GetHashCode()
GetType        Method       type GetType()
ToString       Method       string ToString()
Definition     NoteProperty string Definition=Get-Content
Name           NoteProperty string Name=cat
ParameterCount NoteProperty System.Int32 ParameterCount=21

Name    Definition         ParameterCount
----    ----------         --------------
cat     Get-Content                    21
cd      Set-Location                   15
cdd     Push-MyLocation                 1
chdir   Set-Location                   15
clc     Clear-Content                  20
clear   Clear-Host                      0
clhy    Clear-History                  17
cli     Clear-Item                     20
clp     Clear-ItemProperty             22
cls     Clear-Host                      0
clv     Clear-Variable                 19
cnsn    Connect-PSSession              29
compare Compare-Object                 20
copy    Copy-Item                      24
cp      Copy-Item                      24
cpi     Copy-Item                      24
cpp     Copy-ItemProperty              23
cvpa    Convert-Path                   13
```

### <a name="sort-object"></a><span data-ttu-id="4ad4c-186">Sort-Object</span><span class="sxs-lookup"><span data-stu-id="4ad4c-186">Sort-Object</span></span>

<span data-ttu-id="4ad4c-187">Med hjälp av beräknade egenskaper kan du sortera data i olika ordrar per egenskap.</span><span class="sxs-lookup"><span data-stu-id="4ad4c-187">Using the calculated properties, you can sort data in different orders per property.</span></span> <span data-ttu-id="4ad4c-188">I det här exemplet sorteras data från en CSV-fil i stigande ordning efter **datum**.</span><span class="sxs-lookup"><span data-stu-id="4ad4c-188">This example sorts data from a CSV file in ascending order by **Date**.</span></span> <span data-ttu-id="4ad4c-189">Men inom varje datum sorteras raderna i fallande ordning efter **UnitsSold**.</span><span class="sxs-lookup"><span data-stu-id="4ad4c-189">But within each date, it sorts the rows in descending order by **UnitsSold**.</span></span>

```powershell
Import-Csv C:\temp\sales-data.csv |
  Sort-Object Date, @{expr={$_.UnitsSold}; desc=$true}, Salesperson  |
    Select-Object Date, Salesperson, UnitsSold
```

```Output
Date       Salesperson UnitsSold
----       ----------- ---------
2020-08-01 Sally       3
2020-08-01 Anne        2
2020-08-01 Fred        1
2020-08-02 Anne        6
2020-08-02 Fred        2
2020-08-02 Sally       0
2020-08-03 Anne        5
2020-08-03 Sally       3
2020-08-03 Fred        1
2020-08-04 Anne        2
2020-08-04 Fred        2
2020-08-04 Sally       2
```

## <a name="notes"></a><span data-ttu-id="4ad4c-190">Kommentarer</span><span class="sxs-lookup"><span data-stu-id="4ad4c-190">Notes</span></span>

- <span data-ttu-id="4ad4c-191">Du kan ange uttryckets skript block _direkt_ , som ett argument, i stället för att ange det som `Expression` post i en hash-fil.</span><span class="sxs-lookup"><span data-stu-id="4ad4c-191">You may specify the expression script block _directly_ , as an argument, rather than specifying it as the `Expression` entry in a hashtable.</span></span> <span data-ttu-id="4ad4c-192">Ett exempel:</span><span class="sxs-lookup"><span data-stu-id="4ad4c-192">For example:</span></span>

  ```powershell
  '1', '10', '2' | Sort-Object { [int] $_ }
  ```

  <span data-ttu-id="4ad4c-193">Det här exemplet är praktiskt för cmdletar som inte kräver (eller stöder) namngivning av en egenskap via `Name` nyckeln, till exempel `Sort-Object` , `Group-Object` och `Measure-Object` .</span><span class="sxs-lookup"><span data-stu-id="4ad4c-193">This example is convenient for cmdlets that do not require (or support) naming a property via the `Name` key, such as `Sort-Object`, `Group-Object`, and `Measure-Object`.</span></span>

  <span data-ttu-id="4ad4c-194">För cmdletar som stöder namngivning av egenskapen, konverteras skript blocket till en sträng och används som namn på egenskapen i utdata.</span><span class="sxs-lookup"><span data-stu-id="4ad4c-194">For cmdlets that support naming the property, the script block is converted to a string and used as the name of the property in the output.</span></span>

- <span data-ttu-id="4ad4c-195">`Expression` skript block körs i _underordnade_ omfång, vilket innebär att anroparens variabler inte kan ändras direkt.</span><span class="sxs-lookup"><span data-stu-id="4ad4c-195">`Expression` script blocks run in _child_ scopes, meaning that the caller's variables cannot be directly modified.</span></span>

- <span data-ttu-id="4ad4c-196">Pipeline-logiken används för utdata från `Expression` skript block.</span><span class="sxs-lookup"><span data-stu-id="4ad4c-196">Pipeline logic is applied to the output from `Expression` script blocks.</span></span> <span data-ttu-id="4ad4c-197">Det innebär att en matris med ett enda element gör att matrisen blir unwrap.</span><span class="sxs-lookup"><span data-stu-id="4ad4c-197">This means that outputting a single-element array causes that array to be unwrapped.</span></span>

- <span data-ttu-id="4ad4c-198">I de flesta cmdlets ignoreras fel i uttryck skript block.</span><span class="sxs-lookup"><span data-stu-id="4ad4c-198">For most cmdlets, errors inside expression script blocks are quietly ignored.</span></span>
  <span data-ttu-id="4ad4c-199">För- `Sort-Object` ,-avsluta-och skript-avsluta-fel är _utdata_ , men de avslutar inte instruktionen.</span><span class="sxs-lookup"><span data-stu-id="4ad4c-199">For `Sort-Object`, statement-terminating and script-terminating errors are _output_ but they do not terminate the statement.</span></span>

## <a name="see-also"></a><span data-ttu-id="4ad4c-200">Se även</span><span class="sxs-lookup"><span data-stu-id="4ad4c-200">See Also</span></span>

[<span data-ttu-id="4ad4c-201">about_Hash_Tables</span><span class="sxs-lookup"><span data-stu-id="4ad4c-201">about_Hash_Tables</span></span>](about_hash_tables.md)

[<span data-ttu-id="4ad4c-202">Jämför objekt</span><span class="sxs-lookup"><span data-stu-id="4ad4c-202">Compare-Object</span></span>](xref:Microsoft.PowerShell.Utility.Compare-Object)

[<span data-ttu-id="4ad4c-203">ConvertTo-Html</span><span class="sxs-lookup"><span data-stu-id="4ad4c-203">ConvertTo-Html</span></span>](xref:Microsoft.PowerShell.Utility.ConvertTo-Html)

[<span data-ttu-id="4ad4c-204">Format-Custom</span><span class="sxs-lookup"><span data-stu-id="4ad4c-204">Format-Custom</span></span>](xref:Microsoft.PowerShell.Utility.Format-Custom)

[<span data-ttu-id="4ad4c-205">Format-List</span><span class="sxs-lookup"><span data-stu-id="4ad4c-205">Format-List</span></span>](xref:Microsoft.PowerShell.Utility.Format-List)

[<span data-ttu-id="4ad4c-206">Format-Table</span><span class="sxs-lookup"><span data-stu-id="4ad4c-206">Format-Table</span></span>](xref:Microsoft.PowerShell.Utility.Format-Table)

[<span data-ttu-id="4ad4c-207">Format-Wide</span><span class="sxs-lookup"><span data-stu-id="4ad4c-207">Format-Wide</span></span>](xref:Microsoft.PowerShell.Utility.Format-Wide)

[<span data-ttu-id="4ad4c-208">Gruppera objekt</span><span class="sxs-lookup"><span data-stu-id="4ad4c-208">Group-Object</span></span>](xref:Microsoft.PowerShell.Utility.Group-Object)

[<span data-ttu-id="4ad4c-209">Mått – objekt</span><span class="sxs-lookup"><span data-stu-id="4ad4c-209">Measure-Object</span></span>](xref:Microsoft.PowerShell.Utility.Measure-Object)

[<span data-ttu-id="4ad4c-210">Select-Object</span><span class="sxs-lookup"><span data-stu-id="4ad4c-210">Select-Object</span></span>](xref:Microsoft.PowerShell.Utility.Select-Object)

[<span data-ttu-id="4ad4c-211">Sortera objekt</span><span class="sxs-lookup"><span data-stu-id="4ad4c-211">Sort-Object</span></span>](xref:Microsoft.PowerShell.Utility.Sort-Object)

[<span data-ttu-id="4ad4c-212">Format typer i .NET</span><span class="sxs-lookup"><span data-stu-id="4ad4c-212">Format types in .NET</span></span>](/dotnet/standard/base-types/formatting-types)
