---
description: Förklarar data avsnitt, som isolerar text strängar och andra skrivskyddade data från skript logik.
Locale: en-US
ms.date: 04/23/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_data_sections?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Data_Sections
ms.openlocfilehash: dbc92015a4d48d74dd3f6c642dafbe06f4cb342c
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94710644"
---
# <a name="about-data-sections"></a><span data-ttu-id="602f1-103">Om data avsnitt</span><span class="sxs-lookup"><span data-stu-id="602f1-103">About Data Sections</span></span>

## <a name="short-description"></a><span data-ttu-id="602f1-104">Kort beskrivning</span><span class="sxs-lookup"><span data-stu-id="602f1-104">Short Description</span></span>
<span data-ttu-id="602f1-105">Förklarar data avsnitt, som isolerar text strängar och andra skrivskyddade data från skript logik.</span><span class="sxs-lookup"><span data-stu-id="602f1-105">Explains Data sections, which isolate text strings and other read-only data from script logic.</span></span>

## <a name="long-description"></a><span data-ttu-id="602f1-106">Lång beskrivning</span><span class="sxs-lookup"><span data-stu-id="602f1-106">Long Description</span></span>

<span data-ttu-id="602f1-107">Skript som har utformats för PowerShell kan ha ett eller flera data avsnitt som bara innehåller data.</span><span class="sxs-lookup"><span data-stu-id="602f1-107">Scripts that are designed for PowerShell can have one or more Data sections that contain only data.</span></span> <span data-ttu-id="602f1-108">Du kan inkludera ett eller flera data avsnitt i valfritt skript, funktion eller avancerad funktion.</span><span class="sxs-lookup"><span data-stu-id="602f1-108">You can include one or more Data sections in any script, function, or advanced function.</span></span> <span data-ttu-id="602f1-109">Innehållet i data avsnittet är begränsat till en angiven delmängd av PowerShell-skript språket.</span><span class="sxs-lookup"><span data-stu-id="602f1-109">The content of the Data section is restricted to a specified subset of the PowerShell scripting language.</span></span>

<span data-ttu-id="602f1-110">Genom att skilja data från kod logiken blir det enklare att identifiera och hantera både logik och data.</span><span class="sxs-lookup"><span data-stu-id="602f1-110">Separating data from code logic makes it easier to identify and manage both logic and data.</span></span> <span data-ttu-id="602f1-111">Det gör att du kan ha separata String-resursfiler för text, till exempel fel meddelanden och hjälp strängar.</span><span class="sxs-lookup"><span data-stu-id="602f1-111">It lets you have separate string resource files for text, such as error messages and Help strings.</span></span> <span data-ttu-id="602f1-112">Den isolerar också kod logiken som underlättar säkerhets-och verifieringstester.</span><span class="sxs-lookup"><span data-stu-id="602f1-112">It also isolates the code logic, which facilitates security and validation tests.</span></span>

<span data-ttu-id="602f1-113">I PowerShell används data avsnittet för att stödja skript internationalisering.</span><span class="sxs-lookup"><span data-stu-id="602f1-113">In PowerShell, the Data section is used to support script internationalization.</span></span>
<span data-ttu-id="602f1-114">Du kan använda data avsnitt för att göra det enklare att isolera, leta upp och bearbeta strängar som kommer att översättas till flera användar gränssnitts språk.</span><span class="sxs-lookup"><span data-stu-id="602f1-114">You can use Data sections to make it easier to isolate, locate, and process strings that will be translated into many user interface (UI) languages.</span></span>

<span data-ttu-id="602f1-115">Data avsnittet är en PowerShell 2,0-funktion.</span><span class="sxs-lookup"><span data-stu-id="602f1-115">The Data section is a PowerShell 2.0 feature.</span></span> <span data-ttu-id="602f1-116">Skript med data avsnitt kommer inte att köras i PowerShell 1,0 utan revidering.</span><span class="sxs-lookup"><span data-stu-id="602f1-116">Scripts with Data sections will not run in PowerShell 1.0 without revision.</span></span>

### <a name="syntax"></a><span data-ttu-id="602f1-117">Syntax</span><span class="sxs-lookup"><span data-stu-id="602f1-117">Syntax</span></span>

<span data-ttu-id="602f1-118">Syntaxen för ett data avsnitt är följande:</span><span class="sxs-lookup"><span data-stu-id="602f1-118">The syntax for a Data section is as follows:</span></span>

```
DATA [<variable-name>] [-supportedCommand <cmdlet-name>] {
    <Permitted content>
}
```

<span data-ttu-id="602f1-119">Nyckelordet data krävs.</span><span class="sxs-lookup"><span data-stu-id="602f1-119">The Data keyword is required.</span></span> <span data-ttu-id="602f1-120">Det är inte Skift läges känsligt.</span><span class="sxs-lookup"><span data-stu-id="602f1-120">It is not case-sensitive.</span></span> <span data-ttu-id="602f1-121">Det tillåtna innehållet är begränsat till följande element:</span><span class="sxs-lookup"><span data-stu-id="602f1-121">The permitted content is limited to the following elements:</span></span>

- <span data-ttu-id="602f1-122">Alla PowerShell-operatorer, förutom `-match`</span><span class="sxs-lookup"><span data-stu-id="602f1-122">All PowerShell operators, except `-match`</span></span>
- <span data-ttu-id="602f1-123">`If`-, `Else` -och- `ElseIf` uttryck</span><span class="sxs-lookup"><span data-stu-id="602f1-123">`If`, `Else`, and `ElseIf` statements</span></span>
- <span data-ttu-id="602f1-124">Följande automatiska variabler: `$PsCulture` , `$PsUICulture` ,, `$True` `$False` och `$Null`</span><span class="sxs-lookup"><span data-stu-id="602f1-124">The following automatic variables: `$PsCulture`, `$PsUICulture`, `$True`, `$False`, and `$Null`</span></span>
- <span data-ttu-id="602f1-125">Kommentarer</span><span class="sxs-lookup"><span data-stu-id="602f1-125">Comments</span></span>
- <span data-ttu-id="602f1-126">Pipelines</span><span class="sxs-lookup"><span data-stu-id="602f1-126">Pipelines</span></span>
- <span data-ttu-id="602f1-127">Instruktioner avgränsade med semikolon ( `;` )</span><span class="sxs-lookup"><span data-stu-id="602f1-127">Statements separated by semicolons (`;`)</span></span>
- <span data-ttu-id="602f1-128">Litteraler, till exempel följande:</span><span class="sxs-lookup"><span data-stu-id="602f1-128">Literals, such as the following:</span></span>

  ```powershell
  a
  1
  1,2,3
  "PowerShell 2.0"
  @( "red", "green", "blue" )
  @{ a = 0x1; b = "great"; c ="script" }
  [XML] @'
  <p> Hello, World </p>
  '@
  ```

- <span data-ttu-id="602f1-129">Cmdletar som är tillåtna i ett data avsnitt.</span><span class="sxs-lookup"><span data-stu-id="602f1-129">Cmdlets that are permitted in a Data section.</span></span> <span data-ttu-id="602f1-130">Som standard `ConvertFrom-StringData` tillåts bara cmdleten.</span><span class="sxs-lookup"><span data-stu-id="602f1-130">By default, only the `ConvertFrom-StringData` cmdlet is permitted.</span></span>
- <span data-ttu-id="602f1-131">-Cmdletar som du tillåter i ett data avsnitt med hjälp av- `-SupportedCommand` parametern.</span><span class="sxs-lookup"><span data-stu-id="602f1-131">Cmdlets that you permit in a Data section by using the `-SupportedCommand` parameter.</span></span>

<span data-ttu-id="602f1-132">När du använder `ConvertFrom-StringData` cmdleten i ett data avsnitt kan du ange nyckel/värde-par i ensamt citat tecken eller strängar med dubbla citat tecken eller med en eller två citat tecken som anges här – strängar.</span><span class="sxs-lookup"><span data-stu-id="602f1-132">When you use the `ConvertFrom-StringData` cmdlet in a Data section, you can enclose the key-value pairs in single-quoted or double-quoted strings or in single-quoted or double-quoted here-strings.</span></span> <span data-ttu-id="602f1-133">Strängar som innehåller variabler och under uttryck måste vara inneslutna i enciterade strängar eller i enciterade här – strängar så att variablerna inte expanderas och under uttryck inte är körbara.</span><span class="sxs-lookup"><span data-stu-id="602f1-133">However, strings that contain variables and subexpressions must be enclosed in single-quoted strings or in single-quoted here-strings so that the variables are not expanded and the subexpressions are not executable.</span></span>

### <a name="-supportedcommand"></a><span data-ttu-id="602f1-134">-SupportedCommand</span><span class="sxs-lookup"><span data-stu-id="602f1-134">-SupportedCommand</span></span>

<span data-ttu-id="602f1-135">Med `-SupportedCommand` parametern kan du ange att en cmdlet eller funktion bara genererar data.</span><span class="sxs-lookup"><span data-stu-id="602f1-135">The `-SupportedCommand` parameter allows you to indicate that a cmdlet or function generates only data.</span></span> <span data-ttu-id="602f1-136">Det är utformat för att tillåta användare att inkludera cmdlets och funktioner i ett data avsnitt som de har skrivit eller testat.</span><span class="sxs-lookup"><span data-stu-id="602f1-136">It is designed to allow users to include cmdlets and functions in a data section that they have written or tested.</span></span>

<span data-ttu-id="602f1-137">Värdet för `-SupportedCommand` är en kommaavgränsad lista med en eller flera cmdlet-eller funktions namn.</span><span class="sxs-lookup"><span data-stu-id="602f1-137">The value of `-SupportedCommand` is a comma-separated list of one or more cmdlet or function names.</span></span>

<span data-ttu-id="602f1-138">Följande data avsnitt innehåller till exempel en användardefinierad cmdlet, `Format-XML` som formaterar data i en XML-fil:</span><span class="sxs-lookup"><span data-stu-id="602f1-138">For example, the following data section includes a user-written cmdlet, `Format-XML`, that formats data in an XML file:</span></span>

```powershell
DATA -supportedCommand Format-Xml
{
    Format-Xml -Strings string1, string2, string3
}
```

### <a name="using-a-data-section"></a><span data-ttu-id="602f1-139">Använda ett data avsnitt</span><span class="sxs-lookup"><span data-stu-id="602f1-139">Using a Data Section</span></span>

<span data-ttu-id="602f1-140">Om du vill använda innehållet i ett data avsnitt, tilldelar du det till en variabel och använder variabel notation för att komma åt innehållet.</span><span class="sxs-lookup"><span data-stu-id="602f1-140">To use the content of a Data section, assign it to a variable and use variable notation to access the content.</span></span>

<span data-ttu-id="602f1-141">Följande data avsnitt innehåller till exempel ett `ConvertFrom-StringData` kommando som konverterar denna-sträng till en hash-tabell.</span><span class="sxs-lookup"><span data-stu-id="602f1-141">For example, the following data section contains a `ConvertFrom-StringData` command that converts the here-string into a hash table.</span></span> <span data-ttu-id="602f1-142">Hash-tabellen är tilldelad `$TextMsgs` variabeln.</span><span class="sxs-lookup"><span data-stu-id="602f1-142">The hash table is assigned to the `$TextMsgs` variable.</span></span>

<span data-ttu-id="602f1-143">`$TextMsgs`Variabeln är inte en del av data avsnittet.</span><span class="sxs-lookup"><span data-stu-id="602f1-143">The `$TextMsgs` variable is not part of the data section.</span></span>

```powershell
$TextMsgs = DATA {
    ConvertFrom-StringData -StringData @'
Text001 = Windows 7
Text002 = Windows Server 2008 R2
'@
}
```

<span data-ttu-id="602f1-144">Använd följande kommandon för att komma åt nycklar och värden i hash-tabellen i `$TextMsgs` .</span><span class="sxs-lookup"><span data-stu-id="602f1-144">To access the keys and values in hash table in `$TextMsgs`, use the following commands.</span></span>

```powershell
$TextMsgs.Text001
$TextMsgs.Text002
```

<span data-ttu-id="602f1-145">Alternativt kan du ange variabel namnet i definitionen av data avsnittet.</span><span class="sxs-lookup"><span data-stu-id="602f1-145">Alternately, you can put the variable name in the definition of the Data section.</span></span> <span data-ttu-id="602f1-146">Exempel:</span><span class="sxs-lookup"><span data-stu-id="602f1-146">For example:</span></span>

```powershell
DATA TextMsgs {
    ConvertFrom-StringData -StringData @'
Text001 = Windows 7
Text002 = Windows Server 2008 R2
'@
}

$TextMsgs
```

<span data-ttu-id="602f1-147">Resultatet är detsamma som i föregående exempel.</span><span class="sxs-lookup"><span data-stu-id="602f1-147">The result is the same as the previous example.</span></span>

```Output
Name                           Value
----                           -----
Text001                        Windows 7
Text002                        Windows Server 2008 R2
```

### <a name="examples"></a><span data-ttu-id="602f1-148">Exempel</span><span class="sxs-lookup"><span data-stu-id="602f1-148">Examples</span></span>

<span data-ttu-id="602f1-149">Enkla data strängar.</span><span class="sxs-lookup"><span data-stu-id="602f1-149">Simple data strings.</span></span>

```powershell
DATA {
    "Thank you for using my PowerShell Organize.pst script."
    "It is provided free of charge to the community."
    "I appreciate your comments and feedback."
}
```

<span data-ttu-id="602f1-150">Strängar som innehåller tillåtna variabler.</span><span class="sxs-lookup"><span data-stu-id="602f1-150">Strings that include permitted variables.</span></span>

```powershell
DATA {
    if ($null) {
        "To get help for this cmdlet, type get-help new-dictionary."
    }
}
```

<span data-ttu-id="602f1-151">En ensiffrig här-sträng som använder `ConvertFrom-StringData` cmdleten:</span><span class="sxs-lookup"><span data-stu-id="602f1-151">A single-quoted here-string that uses the `ConvertFrom-StringData` cmdlet:</span></span>

```powershell
DATA {
    ConvertFrom-StringData -stringdata @'
Text001 = Windows 7
Text002 = Windows Server 2008 R2
'@
}
```

<span data-ttu-id="602f1-152">En Double-citerad här – sträng som använder `ConvertFrom-StringData` cmdleten:</span><span class="sxs-lookup"><span data-stu-id="602f1-152">A double-quoted here-string that uses the `ConvertFrom-StringData` cmdlet:</span></span>

```powershell
DATA  {
    ConvertFrom-StringData -stringdata @"
Msg1 = To start, press any key.
Msg2 = To exit, type "quit".
"@
}
```

<span data-ttu-id="602f1-153">Ett data avsnitt som innehåller en användardefinierad cmdlet som genererar data:</span><span class="sxs-lookup"><span data-stu-id="602f1-153">A data section that includes a user-written cmdlet that generates data:</span></span>

```powershell
DATA -supportedCommand Format-XML {
    Format-Xml -strings string1, string2, string3
}
```

## <a name="see-also"></a><span data-ttu-id="602f1-154">Se även</span><span class="sxs-lookup"><span data-stu-id="602f1-154">See Also</span></span>

[<span data-ttu-id="602f1-155">about_Automatic_Variables</span><span class="sxs-lookup"><span data-stu-id="602f1-155">about_Automatic_Variables</span></span>](about_Automatic_Variables.md)

[<span data-ttu-id="602f1-156">about_Comparison_Operators</span><span class="sxs-lookup"><span data-stu-id="602f1-156">about_Comparison_Operators</span></span>](about_Comparison_Operators.md)

[<span data-ttu-id="602f1-157">about_Hash_Tables</span><span class="sxs-lookup"><span data-stu-id="602f1-157">about_Hash_Tables</span></span>](about_Hash_Tables.md)

[<span data-ttu-id="602f1-158">about_If</span><span class="sxs-lookup"><span data-stu-id="602f1-158">about_If</span></span>](about_If.md)

[<span data-ttu-id="602f1-159">about_Operators</span><span class="sxs-lookup"><span data-stu-id="602f1-159">about_Operators</span></span>](about_Operators.md)

[<span data-ttu-id="602f1-160">about_Quoting_Rules</span><span class="sxs-lookup"><span data-stu-id="602f1-160">about_Quoting_Rules</span></span>](about_Quoting_Rules.md)

[<span data-ttu-id="602f1-161">about_Script_Internationalization</span><span class="sxs-lookup"><span data-stu-id="602f1-161">about_Script_Internationalization</span></span>](about_Script_Internationalization.md)

[<span data-ttu-id="602f1-162">ConvertFrom-StringData</span><span class="sxs-lookup"><span data-stu-id="602f1-162">ConvertFrom-StringData</span></span>](xref:Microsoft.PowerShell.Utility.ConvertFrom-StringData)

[<span data-ttu-id="602f1-163">Importera – LocalizedData</span><span class="sxs-lookup"><span data-stu-id="602f1-163">Import-LocalizedData</span></span>](xref:Microsoft.PowerShell.Utility.Import-LocalizedData)

