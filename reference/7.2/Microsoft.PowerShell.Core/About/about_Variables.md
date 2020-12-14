---
description: Beskriver hur variabler lagrar värden som kan användas i PowerShell.
Locale: en-US
ms.date: 11/09/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_variables?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Variables
ms.openlocfilehash: 8d8c8d3098d33980c9c802bf00846a21e8baeb40
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94708827"
---
# <a name="about-variables"></a><span data-ttu-id="1b4e5-103">Om variabler</span><span class="sxs-lookup"><span data-stu-id="1b4e5-103">About Variables</span></span>

## <a name="short-description"></a><span data-ttu-id="1b4e5-104">Kort beskrivning</span><span class="sxs-lookup"><span data-stu-id="1b4e5-104">Short description</span></span>

<span data-ttu-id="1b4e5-105">Beskriver hur variabler lagrar värden som kan användas i PowerShell.</span><span class="sxs-lookup"><span data-stu-id="1b4e5-105">Describes how variables store values that can be used in PowerShell.</span></span>

## <a name="long-description"></a><span data-ttu-id="1b4e5-106">Lång beskrivning</span><span class="sxs-lookup"><span data-stu-id="1b4e5-106">Long description</span></span>

<span data-ttu-id="1b4e5-107">Du kan lagra alla typer av värden i PowerShell-variabler.</span><span class="sxs-lookup"><span data-stu-id="1b4e5-107">You can store all types of values in PowerShell variables.</span></span> <span data-ttu-id="1b4e5-108">Du kan till exempel lagra resultatet av kommandon och lagra element som används i kommandon och uttryck, till exempel namn, sökvägar, inställningar och värden.</span><span class="sxs-lookup"><span data-stu-id="1b4e5-108">For example, store the results of commands, and store elements that are used in commands and expressions, such as names, paths, settings, and values.</span></span>

<span data-ttu-id="1b4e5-109">En variabel är en enhet i minnet där värden lagras.</span><span class="sxs-lookup"><span data-stu-id="1b4e5-109">A variable is a unit of memory in which values are stored.</span></span> <span data-ttu-id="1b4e5-110">I PowerShell representeras variabler av text strängar som börjar med ett dollar tecken ( `$` ), till exempel,, `$a` `$process` eller `$my_var` .</span><span class="sxs-lookup"><span data-stu-id="1b4e5-110">In PowerShell, variables are represented by text strings that begin with a dollar sign (`$`), such as `$a`, `$process`, or `$my_var`.</span></span>

<span data-ttu-id="1b4e5-111">Variabel namn är inte Skift läges känsliga och kan innehålla blank steg och specialtecken.</span><span class="sxs-lookup"><span data-stu-id="1b4e5-111">Variable names aren't case-sensitive, and can include spaces and special characters.</span></span> <span data-ttu-id="1b4e5-112">Men variabel namn som innehåller specialtecken och blank steg är svåra att använda och bör undvikas.</span><span class="sxs-lookup"><span data-stu-id="1b4e5-112">But, variable names that include special characters and spaces are difficult to use and should be avoided.</span></span> <span data-ttu-id="1b4e5-113">Mer information finns i [variabel namn som innehåller specialtecken](#variable-names-that-include-special-characters).</span><span class="sxs-lookup"><span data-stu-id="1b4e5-113">For more information, see [Variable names that include special characters](#variable-names-that-include-special-characters).</span></span>

<span data-ttu-id="1b4e5-114">Det finns flera olika typer av variabler i PowerShell.</span><span class="sxs-lookup"><span data-stu-id="1b4e5-114">There are several different types of variables in PowerShell.</span></span>

- <span data-ttu-id="1b4e5-115">Användardefinierade variabler: variabler som skapats av användaren skapas och underhålls av användaren.</span><span class="sxs-lookup"><span data-stu-id="1b4e5-115">User-created variables: User-created variables are created and maintained by the user.</span></span> <span data-ttu-id="1b4e5-116">Som standard finns variabler som du skapar på PowerShell-kommandoraden bara när PowerShell-fönstret är öppet.</span><span class="sxs-lookup"><span data-stu-id="1b4e5-116">By default, the variables that you create at the PowerShell command line exist only while the PowerShell window is open.</span></span> <span data-ttu-id="1b4e5-117">När PowerShell-fönstren stängs tas variablerna bort.</span><span class="sxs-lookup"><span data-stu-id="1b4e5-117">When the PowerShell windows is closed, the variables are deleted.</span></span> <span data-ttu-id="1b4e5-118">Om du vill spara en variabel lägger du till den i din PowerShell-profil.</span><span class="sxs-lookup"><span data-stu-id="1b4e5-118">To save a variable, add it to your PowerShell profile.</span></span> <span data-ttu-id="1b4e5-119">Du kan också skapa variabler i skript med globalt skript eller lokalt definitions område.</span><span class="sxs-lookup"><span data-stu-id="1b4e5-119">You can also create variables in scripts with global, script, or local scope.</span></span>

- <span data-ttu-id="1b4e5-120">Automatiska variabler: automatiska variabler lagrar status för PowerShell.</span><span class="sxs-lookup"><span data-stu-id="1b4e5-120">Automatic variables: Automatic variables store the state of PowerShell.</span></span> <span data-ttu-id="1b4e5-121">De här variablerna skapas av PowerShell, och PowerShell ändrar värdena efter behov för att upprätthålla deras noggrannhet.</span><span class="sxs-lookup"><span data-stu-id="1b4e5-121">These variables are created by PowerShell, and PowerShell changes their values as required to maintain their accuracy.</span></span> <span data-ttu-id="1b4e5-122">Användare kan inte ändra värdet för dessa variabler.</span><span class="sxs-lookup"><span data-stu-id="1b4e5-122">Users can't change the value of these variables.</span></span> <span data-ttu-id="1b4e5-123">`$PSHOME`Variabeln lagrar till exempel sökvägen till installations katalogen för PowerShell.</span><span class="sxs-lookup"><span data-stu-id="1b4e5-123">For example, the `$PSHOME` variable stores the path to the PowerShell installation directory.</span></span>

  <span data-ttu-id="1b4e5-124">Mer information, en lista och en beskrivning av de automatiska variablerna finns [about_Automatic_Variables](about_Automatic_Variables.md).</span><span class="sxs-lookup"><span data-stu-id="1b4e5-124">For more information, a list, and a description of the automatic variables, see [about_Automatic_Variables](about_Automatic_Variables.md).</span></span>

- <span data-ttu-id="1b4e5-125">Inställningar variabler: Preferences-variabler lagrar användar inställningar för PowerShell.</span><span class="sxs-lookup"><span data-stu-id="1b4e5-125">Preference variables: Preference variables store user preferences for PowerShell.</span></span> <span data-ttu-id="1b4e5-126">Dessa variabler skapas av PowerShell och fylls i med standardvärden.</span><span class="sxs-lookup"><span data-stu-id="1b4e5-126">These variables are created by PowerShell and are populated with default values.</span></span> <span data-ttu-id="1b4e5-127">Användare kan ändra värdena för variablerna.</span><span class="sxs-lookup"><span data-stu-id="1b4e5-127">Users can change the values of these variables.</span></span> <span data-ttu-id="1b4e5-128">Variabeln kan till exempel `$MaximumHistoryCount` bestämma det maximala antalet poster i tidigare sessioner.</span><span class="sxs-lookup"><span data-stu-id="1b4e5-128">For example, the `$MaximumHistoryCount` variable determines the maximum number of entries in the session history.</span></span>

  <span data-ttu-id="1b4e5-129">Mer information, en lista och en beskrivning av Preferences-variablerna finns [about_Preference_Variables](about_Preference_Variables.md).</span><span class="sxs-lookup"><span data-stu-id="1b4e5-129">For more information, a list, and a description of the preference variables, see [about_Preference_Variables](about_Preference_Variables.md).</span></span>

## <a name="working-with-variables"></a><span data-ttu-id="1b4e5-130">Arbeta med variabler</span><span class="sxs-lookup"><span data-stu-id="1b4e5-130">Working with variables</span></span>

<span data-ttu-id="1b4e5-131">Om du vill skapa en ny variabel använder du ett tilldelnings uttryck för att tilldela variabeln ett värde.</span><span class="sxs-lookup"><span data-stu-id="1b4e5-131">To create a new variable, use an assignment statement to assign a value to the variable.</span></span> <span data-ttu-id="1b4e5-132">Du behöver inte deklarera variabeln innan du använder den.</span><span class="sxs-lookup"><span data-stu-id="1b4e5-132">You don't have to declare the variable before using it.</span></span> <span data-ttu-id="1b4e5-133">Standardvärdet för alla variabler är `$null` .</span><span class="sxs-lookup"><span data-stu-id="1b4e5-133">The default value of all variables is `$null`.</span></span>

<span data-ttu-id="1b4e5-134">Om du vill hämta en lista över alla variabler i PowerShell-sessionen skriver du `Get-Variable` .</span><span class="sxs-lookup"><span data-stu-id="1b4e5-134">To get a list of all the variables in your PowerShell session, type `Get-Variable`.</span></span> <span data-ttu-id="1b4e5-135">Variabel namnen visas utan föregående dollar `$` tecken () som används för att referera till variabler.</span><span class="sxs-lookup"><span data-stu-id="1b4e5-135">The variable names are displayed without the preceding dollar (`$`) sign that is used to reference variables.</span></span>

<span data-ttu-id="1b4e5-136">Exempel:</span><span class="sxs-lookup"><span data-stu-id="1b4e5-136">For example:</span></span>

```powershell
$MyVariable = 1, 2, 3

$Path = "C:\Windows\System32"
```

<span data-ttu-id="1b4e5-137">Variabler är användbara för att lagra resultatet av kommandon.</span><span class="sxs-lookup"><span data-stu-id="1b4e5-137">Variables are useful for storing the results of commands.</span></span>

<span data-ttu-id="1b4e5-138">Exempel:</span><span class="sxs-lookup"><span data-stu-id="1b4e5-138">For example:</span></span>

```powershell
$Processes = Get-Process

$Today = (Get-Date).DateTime
```

<span data-ttu-id="1b4e5-139">Om du vill visa värdet för en variabel skriver du variabelns namn, föregånget av ett dollar tecken ( `$` ).</span><span class="sxs-lookup"><span data-stu-id="1b4e5-139">To display the value of a variable, type the variable name, preceded by a dollar sign (`$`).</span></span>

<span data-ttu-id="1b4e5-140">Exempel:</span><span class="sxs-lookup"><span data-stu-id="1b4e5-140">For example:</span></span>

```powershell
$MyVariable
```

```Output
1
2
3
```

```powershell
$Today
```

```Output
Tuesday, September 3, 2019 09:46:46
```

<span data-ttu-id="1b4e5-141">Om du vill ändra värdet för en variabel tilldelar du ett nytt värde till variabeln.</span><span class="sxs-lookup"><span data-stu-id="1b4e5-141">To change the value of a variable, assign a new value to the variable.</span></span>

<span data-ttu-id="1b4e5-142">Följande exempel visar värdet för `$MyVariable` variabeln, ändrar värdet för variabeln och visar sedan det nya värdet.</span><span class="sxs-lookup"><span data-stu-id="1b4e5-142">The following examples display the value of the `$MyVariable` variable, changes the value of the variable, and then displays the new value.</span></span>

```powershell
$MyVariable = 1, 2, 3
$MyVariable
```

```Output
1
2
3
```

```powershell
$MyVariable = "The green cat."
$MyVariable
```

```Output
The green cat.
```

<span data-ttu-id="1b4e5-143">Om du vill ta bort värdet för en variabel använder du `Clear-Variable` cmdleten eller ändrar värdet till `$null` .</span><span class="sxs-lookup"><span data-stu-id="1b4e5-143">To delete the value of a variable, use the `Clear-Variable` cmdlet or change the value to `$null`.</span></span>

```powershell
Clear-Variable -Name MyVariable
```

```powershell
$MyVariable = $null
```

<span data-ttu-id="1b4e5-144">Ta bort variabeln genom att använda [Remove-Variable](xref:Microsoft.PowerShell.Utility.Remove-Variable) eller [Remove-item](xref:Microsoft.PowerShell.Management.Remove-Item).</span><span class="sxs-lookup"><span data-stu-id="1b4e5-144">To delete the variable, use [Remove-Variable](xref:Microsoft.PowerShell.Utility.Remove-Variable) or [Remove-Item](xref:Microsoft.PowerShell.Management.Remove-Item).</span></span>

```powershell
Remove-Variable -Name MyVariable
```

```powershell
Remove-Item -Path Variable:\MyVariable
```

## <a name="types-of-variables"></a><span data-ttu-id="1b4e5-145">Typer av variabler</span><span class="sxs-lookup"><span data-stu-id="1b4e5-145">Types of variables</span></span>

<span data-ttu-id="1b4e5-146">Du kan lagra alla typer av objekt i en variabel, inklusive heltal, strängar, matriser och hash-tabeller.</span><span class="sxs-lookup"><span data-stu-id="1b4e5-146">You can store any type of object in a variable, including integers, strings, arrays, and hash tables.</span></span> <span data-ttu-id="1b4e5-147">Och objekt som representerar processer, tjänster, händelse loggar och datorer.</span><span class="sxs-lookup"><span data-stu-id="1b4e5-147">And, objects that represent processes, services, event logs, and computers.</span></span>

<span data-ttu-id="1b4e5-148">PowerShell-variabler skrivs fritt, vilket innebär att de inte är begränsade till en viss typ av objekt.</span><span class="sxs-lookup"><span data-stu-id="1b4e5-148">PowerShell variables are loosely typed, which means that they aren't limited to a particular type of object.</span></span> <span data-ttu-id="1b4e5-149">En enskild variabel kan till och med innehålla en samling, eller matris, av olika typer av objekt på samma gång.</span><span class="sxs-lookup"><span data-stu-id="1b4e5-149">A single variable can even contain a collection, or array, of different types of objects at the same time.</span></span>

<span data-ttu-id="1b4e5-150">Data typen för en variabel fastställs av .NET-typerna för variabelns värden.</span><span class="sxs-lookup"><span data-stu-id="1b4e5-150">The data type of a variable is determined by the .NET types of the values of the variable.</span></span> <span data-ttu-id="1b4e5-151">Om du vill visa en variabels objekt typ använder du [Get-Member](xref:Microsoft.PowerShell.Utility.Get-Member).</span><span class="sxs-lookup"><span data-stu-id="1b4e5-151">To view a variable's object type, use [Get-Member](xref:Microsoft.PowerShell.Utility.Get-Member).</span></span>

<span data-ttu-id="1b4e5-152">Exempel:</span><span class="sxs-lookup"><span data-stu-id="1b4e5-152">For example:</span></span>

```powershell
$a = 12                         # System.Int32
$a = "Word"                     # System.String
$a = 12, "Word"                 # array of System.Int32, System.String
$a = Get-ChildItem C:\Windows   # FileInfo and DirectoryInfo types
```

<span data-ttu-id="1b4e5-153">Du kan använda ett Type-attribut och Cast notation för att säkerställa att en variabel endast kan innehålla vissa objekt typer eller objekt som kan konverteras till den typen.</span><span class="sxs-lookup"><span data-stu-id="1b4e5-153">You can use a type attribute and cast notation to ensure that a variable can contain only specific object types or objects that can be converted to that type.</span></span> <span data-ttu-id="1b4e5-154">Om du försöker tilldela ett värde av en annan typ försöker PowerShell konvertera värdet till dess typ.</span><span class="sxs-lookup"><span data-stu-id="1b4e5-154">If you try to assign a value of another type, PowerShell tries to convert the value to its type.</span></span> <span data-ttu-id="1b4e5-155">Om typen inte kan konverteras Miss lyckas tilldelnings instruktionen.</span><span class="sxs-lookup"><span data-stu-id="1b4e5-155">If the type can't be converted, the assignment statement fails.</span></span>

<span data-ttu-id="1b4e5-156">Om du vill använda Cast notation anger du ett typnamn som omges av hakparenteser, före variabel namnet (till vänster i tilldelnings instruktionen).</span><span class="sxs-lookup"><span data-stu-id="1b4e5-156">To use cast notation, enter a type name, enclosed in brackets, before the variable name (on the left side of the assignment statement).</span></span> <span data-ttu-id="1b4e5-157">I följande exempel skapas en `$number` variabel som bara kan innehålla heltal, en `$words` variabel som bara kan innehålla strängar och en `$dates` variabel som endast kan innehålla **datetime** -objekt.</span><span class="sxs-lookup"><span data-stu-id="1b4e5-157">The following example creates a `$number` variable that can contain only integers, a `$words` variable that can contain only strings, and a `$dates` variable that can contain only **DateTime** objects.</span></span>

```powershell
[int]$number = 8
$number = "12345"  # The string is converted to an integer.
$number = "Hello"
```

```Output
Cannot convert value "Hello" to type "System.Int32". Error: "Input string was
 not in a correct format."
At line:1 char:1
+ $number = "Hello"
+ ~~~~~~~~~~~~~~~~~
+ CategoryInfo          : MetadataError: (:) [],
    ArgumentTransformationMetadataException
+ FullyQualifiedErrorId : RuntimeException
```

```powershell
[string]$words = "Hello"
$words = 2       # The integer is converted to a string.
$words += 10     # The plus (+) sign concatenates the strings.
$words
```

```Output
210
```

```powershell
[datetime] $dates = "09/12/91"  # The string is converted to a DateTime object.
$dates
```

```Output
Thursday, September 12, 1991 00:00:00
```

```powershell
$dates = 10    # The integer is converted to a DateTime object.
$dates
```

```Output
Monday, January 1, 0001 00:00:00
```

## <a name="using-variables-in-commands-and-expressions"></a><span data-ttu-id="1b4e5-158">Använda variabler i kommandon och uttryck</span><span class="sxs-lookup"><span data-stu-id="1b4e5-158">Using variables in commands and expressions</span></span>

<span data-ttu-id="1b4e5-159">Om du vill använda en variabel i ett kommando eller uttryck skriver du variabelns namn, föregånget av dollar `$` tecknet ().</span><span class="sxs-lookup"><span data-stu-id="1b4e5-159">To use a variable in a command or expression, type the variable name, preceded by the dollar (`$`) sign.</span></span>

<span data-ttu-id="1b4e5-160">Om variabel namn och dollar tecken inte omges av citat tecken, eller om de omges av dubbla citat tecken ( `"` ), används värdet för variabeln i kommandot eller uttrycket.</span><span class="sxs-lookup"><span data-stu-id="1b4e5-160">If the variable name and dollar sign aren't enclosed in quotation marks, or if they're enclosed in double quotation (`"`) marks, the value of the variable is used in the command or expression.</span></span>

<span data-ttu-id="1b4e5-161">Om variabel namn och dollar tecken omges av enkla citat `'` tecken () används variabel namnet i uttrycket.</span><span class="sxs-lookup"><span data-stu-id="1b4e5-161">If the variable name and dollar sign are enclosed in single quotation (`'`) marks, the variable name is used in the expression.</span></span>

<span data-ttu-id="1b4e5-162">Mer information om hur du använder citat tecken i PowerShell finns [about_Quoting_Rules](about_Quoting_Rules.md).</span><span class="sxs-lookup"><span data-stu-id="1b4e5-162">For more information about using quotation marks in PowerShell, see [about_Quoting_Rules](about_Quoting_Rules.md).</span></span>

<span data-ttu-id="1b4e5-163">Det här exemplet hämtar värdet för `$PROFILE` variabeln, som är sökvägen till PowerShell-filen för användar profiler i PowerShell-konsolen.</span><span class="sxs-lookup"><span data-stu-id="1b4e5-163">This example gets the value of the `$PROFILE` variable, which is the path to the PowerShell user profile file in the PowerShell console.</span></span>

```powershell
$PROFILE
```

```Output
C:\Users\User01\Documents\PowerShell\Microsoft.PowerShell_profile.ps1
```

<span data-ttu-id="1b4e5-164">I det här exemplet visas två kommandon som kan öppna PowerShell-profilen i **notepad.exe**.</span><span class="sxs-lookup"><span data-stu-id="1b4e5-164">In this example, two commands are shown that can open the PowerShell profile in **notepad.exe**.</span></span> <span data-ttu-id="1b4e5-165">Exemplet med dubbla citat `"` tecken () använder variabelns värde.</span><span class="sxs-lookup"><span data-stu-id="1b4e5-165">The example with double-quote (`"`) marks uses the variable's value.</span></span>

```powershell
notepad $PROFILE

notepad "$PROFILE"
```

<span data-ttu-id="1b4e5-166">I följande exempel används ett enkelt citat `'` tecken () som behandlar variabeln som en literal text.</span><span class="sxs-lookup"><span data-stu-id="1b4e5-166">The following examples use single-quote (`'`) marks that treat the variable as literal text.</span></span>

```powershell
'$PROFILE'
```

```Output
$PROFILE
```

```powershell
'Use the $PROFILE variable.'
```

```Output
Use the $PROFILE variable.
```

## <a name="variable-names-that-include-special-characters"></a><span data-ttu-id="1b4e5-167">Variabel namn som innehåller specialtecken</span><span class="sxs-lookup"><span data-stu-id="1b4e5-167">Variable names that include special characters</span></span>

<span data-ttu-id="1b4e5-168">Variabel namn börjar med ett dollar tecken ( `$` ) och får innehålla alfanumeriska tecken och specialtecken.</span><span class="sxs-lookup"><span data-stu-id="1b4e5-168">Variable names begin with a dollar (`$`) sign and can include alphanumeric characters and special characters.</span></span> <span data-ttu-id="1b4e5-169">Variabel namnets längd begränsas bara av tillgängligt minne.</span><span class="sxs-lookup"><span data-stu-id="1b4e5-169">The variable name length is limited only by available memory.</span></span>

<span data-ttu-id="1b4e5-170">Det bästa tillvägagångs sättet är att variabel namn bara innehåller alfanumeriska tecken och under streck ( `_` )-tecknet.</span><span class="sxs-lookup"><span data-stu-id="1b4e5-170">The best practice is that variable names include only alphanumeric characters and the underscore (`_`) character.</span></span> <span data-ttu-id="1b4e5-171">Variabel namn som innehåller blank steg och andra specialtecken är svåra att använda och bör undvikas.</span><span class="sxs-lookup"><span data-stu-id="1b4e5-171">Variable names that include spaces and other special characters, are difficult to use and should be avoided.</span></span>

<span data-ttu-id="1b4e5-172">Alfanumeriska variabel namn kan innehålla följande tecken:</span><span class="sxs-lookup"><span data-stu-id="1b4e5-172">Alphanumeric variable names can contain these characters:</span></span>

- <span data-ttu-id="1b4e5-173">Unicode-tecken från dessa kategorier: **Lu**, **lla**, **lt**, **LM**, **Lo** eller **nd**.</span><span class="sxs-lookup"><span data-stu-id="1b4e5-173">Unicode characters from these categories: **Lu**, **Ll**, **Lt**, **Lm**, **Lo**, or **Nd**.</span></span>
- <span data-ttu-id="1b4e5-174">Under streck ( `_` )-tecken.</span><span class="sxs-lookup"><span data-stu-id="1b4e5-174">Underscore (`_`) character.</span></span>
- <span data-ttu-id="1b4e5-175">Frågetecken ( `?` )-tecken.</span><span class="sxs-lookup"><span data-stu-id="1b4e5-175">Question mark (`?`) character.</span></span>

<span data-ttu-id="1b4e5-176">I följande lista finns beskrivningar av Unicode-kategorier.</span><span class="sxs-lookup"><span data-stu-id="1b4e5-176">The following list contains the Unicode category descriptions.</span></span> <span data-ttu-id="1b4e5-177">Mer information finns i [UnicodeCategory](/dotnet/api/system.globalization.unicodecategory).</span><span class="sxs-lookup"><span data-stu-id="1b4e5-177">For more information, see [UnicodeCategory](/dotnet/api/system.globalization.unicodecategory).</span></span>

- <span data-ttu-id="1b4e5-178">**Lu** -UppercaseLetter</span><span class="sxs-lookup"><span data-stu-id="1b4e5-178">**Lu** - UppercaseLetter</span></span>
- <span data-ttu-id="1b4e5-179">**Lla** – LowercaseLetter</span><span class="sxs-lookup"><span data-stu-id="1b4e5-179">**Ll** - LowercaseLetter</span></span>
- <span data-ttu-id="1b4e5-180">**Lt** -TitlecaseLetter</span><span class="sxs-lookup"><span data-stu-id="1b4e5-180">**Lt** - TitlecaseLetter</span></span>
- <span data-ttu-id="1b4e5-181">**LM** -ModifierLetter</span><span class="sxs-lookup"><span data-stu-id="1b4e5-181">**Lm** - ModifierLetter</span></span>
- <span data-ttu-id="1b4e5-182">**Lo** -OtherLetter</span><span class="sxs-lookup"><span data-stu-id="1b4e5-182">**Lo** - OtherLetter</span></span>
- <span data-ttu-id="1b4e5-183">**Nd** – DecimalDigitNumber</span><span class="sxs-lookup"><span data-stu-id="1b4e5-183">**Nd** - DecimalDigitNumber</span></span>

<span data-ttu-id="1b4e5-184">Om du vill skapa eller visa ett variabel namn som innehåller blank steg eller specialtecken, omger du variabel namnet med klammerparenteser ( `{}` )-tecknen.</span><span class="sxs-lookup"><span data-stu-id="1b4e5-184">To create or display a variable name that includes spaces or special characters, enclose the variable name with the curly braces (`{}`) characters.</span></span>
<span data-ttu-id="1b4e5-185">Klammerparenteserna Direct PowerShell för att tolka variabel namnets tecken som litteraler.</span><span class="sxs-lookup"><span data-stu-id="1b4e5-185">The curly braces direct PowerShell to interpret the variable name's characters as literals.</span></span>

<span data-ttu-id="1b4e5-186">Variabel namn för specialtecken kan innehålla följande tecken:</span><span class="sxs-lookup"><span data-stu-id="1b4e5-186">Special character variable names can contain these characters:</span></span>

- <span data-ttu-id="1b4e5-187">Valfritt Unicode-tecken, med följande undantag:</span><span class="sxs-lookup"><span data-stu-id="1b4e5-187">Any Unicode character, with the following exceptions:</span></span>
  - <span data-ttu-id="1b4e5-188">Avslutande klammer ( `}` )-tecken (U + 007D).</span><span class="sxs-lookup"><span data-stu-id="1b4e5-188">The closing curly brace (`}`) character (U+007D).</span></span>
  - <span data-ttu-id="1b4e5-189">"Bakticket"-( `` ` `` )-symbolen (U + 0060).</span><span class="sxs-lookup"><span data-stu-id="1b4e5-189">The backtick (`` ` ``) character (U+0060).</span></span> <span data-ttu-id="1b4e5-190">Bakticket används för att undanta Unicode-tecken så att de behandlas som litteraler.</span><span class="sxs-lookup"><span data-stu-id="1b4e5-190">The backtick is used to escape Unicode characters so they're treated as literals.</span></span>

<span data-ttu-id="1b4e5-191">PowerShell har reserverade variabler som `$$` ,, `$?` `$^` och `$_` som innehåller alfanumeriska tecken och specialtecken.</span><span class="sxs-lookup"><span data-stu-id="1b4e5-191">PowerShell has reserved variables such as `$$`, `$?`, `$^`, and `$_` that contain alphanumeric and special characters.</span></span> <span data-ttu-id="1b4e5-192">Mer information finns i [about_Automatic_Variables](about_automatic_variables.md).</span><span class="sxs-lookup"><span data-stu-id="1b4e5-192">For more information, see [about_Automatic_Variables](about_automatic_variables.md).</span></span>

<span data-ttu-id="1b4e5-193">Till exempel skapar följande kommando variabeln med namnet `save-items` .</span><span class="sxs-lookup"><span data-stu-id="1b4e5-193">For example, the following command creates the variable named `save-items`.</span></span> <span data-ttu-id="1b4e5-194">Klammerparenteser ( `{}` ) behövs eftersom variabel namnet innehåller ett bindestreck ( `-` )-specialtecken.</span><span class="sxs-lookup"><span data-stu-id="1b4e5-194">The curly braces (`{}`) are needed because variable name includes a hyphen (`-`) special character.</span></span>

```powershell
${save-items} = "a", "b", "c"
${save-items}
```

```Output
a
b
c
```

<span data-ttu-id="1b4e5-195">Följande kommando hämtar de underordnade objekten i katalogen som representeras av `ProgramFiles(x86)` miljö variabeln.</span><span class="sxs-lookup"><span data-stu-id="1b4e5-195">The following command gets the child items in the directory that is represented by the `ProgramFiles(x86)` environment variable.</span></span>

```powershell
Get-ChildItem ${env:ProgramFiles(x86)}
```

<span data-ttu-id="1b4e5-196">Om du vill referera till ett variabel namn som innehåller klammerparenteser, omger du variabel namnet inom klammerparenteser och använder Baknings tecknet för att undanta klammerparenteserna.</span><span class="sxs-lookup"><span data-stu-id="1b4e5-196">To reference a variable name that includes braces, enclose the variable name in braces, and use the backtick character to escape the braces.</span></span> <span data-ttu-id="1b4e5-197">Om du till exempel vill skapa en variabel med namnet `this{value}is` Typ:</span><span class="sxs-lookup"><span data-stu-id="1b4e5-197">For example, to create a variable named `this{value}is` type:</span></span>

```powershell
${this`{value`}is} = "This variable name uses braces and backticks."
${this`{value`}is}
```

```Output
This variable name uses braces and backticks.
```

## <a name="variables-and-scope"></a><span data-ttu-id="1b4e5-198">Variabler och omfång</span><span class="sxs-lookup"><span data-stu-id="1b4e5-198">Variables and scope</span></span>

<span data-ttu-id="1b4e5-199">Som standard är variabler bara tillgängliga i den omfattning som de har skapats i.</span><span class="sxs-lookup"><span data-stu-id="1b4e5-199">By default, variables are only available in the scope in which they're created.</span></span>

<span data-ttu-id="1b4e5-200">En variabel som du skapar i en funktion är till exempel bara tillgänglig i funktionen.</span><span class="sxs-lookup"><span data-stu-id="1b4e5-200">For example, a variable that you create in a function is available only within the function.</span></span> <span data-ttu-id="1b4e5-201">En variabel som du skapar i ett skript är bara tillgänglig i skriptet.</span><span class="sxs-lookup"><span data-stu-id="1b4e5-201">A variable that you create in a script is available only within the script.</span></span> <span data-ttu-id="1b4e5-202">Om du använder skriptet i punkt-källa läggs variabeln till i det aktuella omfånget.</span><span class="sxs-lookup"><span data-stu-id="1b4e5-202">If you dot-source the script, the variable is added to the current scope.</span></span> <span data-ttu-id="1b4e5-203">Mer information finns i [about_Scopes](about_Scopes.md).</span><span class="sxs-lookup"><span data-stu-id="1b4e5-203">For more information, see [about_Scopes](about_Scopes.md).</span></span>

<span data-ttu-id="1b4e5-204">Du kan använda en omfattnings modifierare för att ändra standard omfånget för variabeln.</span><span class="sxs-lookup"><span data-stu-id="1b4e5-204">You can use a scope modifier to change the default scope of the variable.</span></span> <span data-ttu-id="1b4e5-205">Följande uttryck skapar en variabel med namnet `Computers` .</span><span class="sxs-lookup"><span data-stu-id="1b4e5-205">The following expression creates a variable named `Computers`.</span></span> <span data-ttu-id="1b4e5-206">Variabeln har en global omfattning, även när den skapas i ett skript eller en funktion.</span><span class="sxs-lookup"><span data-stu-id="1b4e5-206">The variable has a global scope, even when it's created in a script or function.</span></span>

```powershell
$Global:Computers = "Server01"
```

<span data-ttu-id="1b4e5-207">För alla skript eller kommandon som körs utanför sessionen behöver du `Using` omfångs modifieraren för att bädda in variabel värden från scopet för den anropande sessionen, så att det går att komma åt dem.</span><span class="sxs-lookup"><span data-stu-id="1b4e5-207">For any script or command that executes out of session, you need the `Using` scope modifier to embed variable values from the calling session scope, so that out of session code can access them.</span></span>

<span data-ttu-id="1b4e5-208">Mer information finns i [about_Remote_Variables](about_Remote_Variables.md).</span><span class="sxs-lookup"><span data-stu-id="1b4e5-208">For more information, see [about_Remote_Variables](about_Remote_Variables.md).</span></span>

## <a name="saving-variables"></a><span data-ttu-id="1b4e5-209">Sparar variabler</span><span class="sxs-lookup"><span data-stu-id="1b4e5-209">Saving variables</span></span>

<span data-ttu-id="1b4e5-210">Variabler som du skapar är bara tillgängliga i den session där du skapar dem.</span><span class="sxs-lookup"><span data-stu-id="1b4e5-210">Variables that you create are available only in the session in which you create them.</span></span> <span data-ttu-id="1b4e5-211">De går förlorade när du stänger sessionen.</span><span class="sxs-lookup"><span data-stu-id="1b4e5-211">They're lost when you close your session.</span></span>

<span data-ttu-id="1b4e5-212">Om du vill skapa variabeln i varje PowerShell-session som du startar lägger du till variabeln i din PowerShell-profil.</span><span class="sxs-lookup"><span data-stu-id="1b4e5-212">To create the variable in every PowerShell session that you start, add the variable to your PowerShell profile.</span></span>

<span data-ttu-id="1b4e5-213">Om du till exempel vill ändra värdet för `$VerbosePreference` variabeln i varje PowerShell-session lägger du till följande kommando i din PowerShell-profil.</span><span class="sxs-lookup"><span data-stu-id="1b4e5-213">For example, to change the value of the `$VerbosePreference` variable in every PowerShell session, add the following command to your PowerShell profile.</span></span>

```powershell
$VerbosePreference = "Continue"
```

<span data-ttu-id="1b4e5-214">Du kan lägga till det här kommandot i din PowerShell-profil genom att öppna `$PROFILE` filen i en text redigerare, t. ex. **notepad.exe**.</span><span class="sxs-lookup"><span data-stu-id="1b4e5-214">You can add this command to your PowerShell profile by opening the `$PROFILE` file in a text editor, such as **notepad.exe**.</span></span> <span data-ttu-id="1b4e5-215">Mer information om PowerShell-profiler finns [about_Profiles](about_Profiles.md).</span><span class="sxs-lookup"><span data-stu-id="1b4e5-215">For more information about PowerShell profiles, see [about_Profiles](about_Profiles.md).</span></span>

## <a name="the-variable-drive"></a><span data-ttu-id="1b4e5-216">Variabeln: enhet</span><span class="sxs-lookup"><span data-stu-id="1b4e5-216">The Variable: drive</span></span>

<span data-ttu-id="1b4e5-217">PowerShell-variabeln Provider skapar en `Variable:` enhet som ser ut och fungerar som en fil systemen het, men den innehåller variablerna i sessionen och deras värden.</span><span class="sxs-lookup"><span data-stu-id="1b4e5-217">The PowerShell Variable provider creates a `Variable:` drive that looks and acts like a file system drive, but it contains the variables in your session and their values.</span></span>

<span data-ttu-id="1b4e5-218">Om du vill ändra till `Variable:` enheten använder du följande kommando:</span><span class="sxs-lookup"><span data-stu-id="1b4e5-218">To change to the `Variable:` drive, use the following command:</span></span>

```powershell
Set-Location Variable:
```

<span data-ttu-id="1b4e5-219">Om du vill visa en lista över objekten och variablerna i `Variable:` enheten använder du `Get-Item` `Get-ChildItem` cmdletarna eller.</span><span class="sxs-lookup"><span data-stu-id="1b4e5-219">To list the items and variables in the `Variable:` drive, use the `Get-Item` or `Get-ChildItem` cmdlets.</span></span>

```powershell
Get-ChildItem Variable:
```

<span data-ttu-id="1b4e5-220">Om du vill hämta värdet för en viss variabel använder du fil system notation för att ange namnet på enheten och namnet på variabeln.</span><span class="sxs-lookup"><span data-stu-id="1b4e5-220">To get the value of a particular variable, use file system notation to specify the name of the drive and the name of the variable.</span></span> <span data-ttu-id="1b4e5-221">Använd till exempel följande kommando för att hämta den `$PSCulture` automatiska variabeln.</span><span class="sxs-lookup"><span data-stu-id="1b4e5-221">For example, to get the `$PSCulture` automatic variable, use the following command.</span></span>

```powershell
Get-Item Variable:\PSCulture
```

```Output
Name                           Value
----                           -----
PSCulture                      en-US
```

<span data-ttu-id="1b4e5-222">Om du vill visa mer information om `Variable:` enheten och PowerShell-variabeln Provider skriver du:</span><span class="sxs-lookup"><span data-stu-id="1b4e5-222">To display more information about the `Variable:` drive and the PowerShell Variable provider, type:</span></span>

```powershell
Get-Help Variable
```

## <a name="variable-syntax-with-provider-paths"></a><span data-ttu-id="1b4e5-223">Variabel syntax med Provider-sökvägar</span><span class="sxs-lookup"><span data-stu-id="1b4e5-223">Variable syntax with provider paths</span></span>

<span data-ttu-id="1b4e5-224">Du kan använda en provider-sökväg med dollar ( `$` )-tecknet och få åtkomst till innehållet i alla providrar som implementerar [IContentCmdletProvider](/dotnet/api/system.management.automation.provider.icontentcmdletprovider) -gränssnittet.</span><span class="sxs-lookup"><span data-stu-id="1b4e5-224">You can prefix a provider path with the dollar (`$`) sign, and access the content of any provider that implements the [IContentCmdletProvider](/dotnet/api/system.management.automation.provider.icontentcmdletprovider) interface.</span></span>

<span data-ttu-id="1b4e5-225">Följande inbyggda PowerShell-leverantörer stöder den här notationen:</span><span class="sxs-lookup"><span data-stu-id="1b4e5-225">The following built-in PowerShell providers support this notation:</span></span>

- [<span data-ttu-id="1b4e5-226">about_Environment_Provider</span><span class="sxs-lookup"><span data-stu-id="1b4e5-226">about_Environment_Provider</span></span>](about_Environment_Provider.md)
- [<span data-ttu-id="1b4e5-227">about_Variable_Provider</span><span class="sxs-lookup"><span data-stu-id="1b4e5-227">about_Variable_Provider</span></span>](about_Variable_Provider.md)
- [<span data-ttu-id="1b4e5-228">about_Function_Provider</span><span class="sxs-lookup"><span data-stu-id="1b4e5-228">about_Function_Provider</span></span>](about_Function_Provider.md)
- [<span data-ttu-id="1b4e5-229">about_Alias_Provider</span><span class="sxs-lookup"><span data-stu-id="1b4e5-229">about_Alias_Provider</span></span>](about_Alias_Provider.md)

## <a name="the-variable-cmdlets"></a><span data-ttu-id="1b4e5-230">Variabel-cmdletar</span><span class="sxs-lookup"><span data-stu-id="1b4e5-230">The variable cmdlets</span></span>

<span data-ttu-id="1b4e5-231">PowerShell innehåller en uppsättning cmdletar som är utformade för att hantera variabler.</span><span class="sxs-lookup"><span data-stu-id="1b4e5-231">PowerShell includes a set of cmdlets that are designed to manage variables.</span></span>

<span data-ttu-id="1b4e5-232">Om du vill visa en lista med cmdletar skriver du:</span><span class="sxs-lookup"><span data-stu-id="1b4e5-232">To list the cmdlets, type:</span></span>

```powershell
Get-Command -Noun Variable
```

<span data-ttu-id="1b4e5-233">Om du vill ha hjälp med en angiven cmdlet skriver du:</span><span class="sxs-lookup"><span data-stu-id="1b4e5-233">To get help for a specific cmdlet, type:</span></span>

```powershell
Get-Help <cmdlet-name>
```

| <span data-ttu-id="1b4e5-234">Cmdlet-namn</span><span class="sxs-lookup"><span data-stu-id="1b4e5-234">Cmdlet Name</span></span>       | <span data-ttu-id="1b4e5-235">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="1b4e5-235">Description</span></span>                                |
| ---------------   | ------------------------------------------ |
| `Clear-Variable`  | <span data-ttu-id="1b4e5-236">Tar bort värdet för en variabel.</span><span class="sxs-lookup"><span data-stu-id="1b4e5-236">Deletes the value of a variable.</span></span>           |
| `Get-Variable`    | <span data-ttu-id="1b4e5-237">Hämtar variablerna i den aktuella konsolen.</span><span class="sxs-lookup"><span data-stu-id="1b4e5-237">Gets the variables in the current console.</span></span> |
| `New-Variable`    | <span data-ttu-id="1b4e5-238">Skapar en ny variabel.</span><span class="sxs-lookup"><span data-stu-id="1b4e5-238">Creates a new variable.</span></span>                    |
| `Remove-Variable` | <span data-ttu-id="1b4e5-239">Tar bort en variabel och dess värde.</span><span class="sxs-lookup"><span data-stu-id="1b4e5-239">Deletes a variable and its value.</span></span>          |
| `Set-Variable`    | <span data-ttu-id="1b4e5-240">Ändrar värdet för en variabel.</span><span class="sxs-lookup"><span data-stu-id="1b4e5-240">Changes the value of a variable.</span></span>           |

## <a name="see-also"></a><span data-ttu-id="1b4e5-241">Se även</span><span class="sxs-lookup"><span data-stu-id="1b4e5-241">See also</span></span>

[<span data-ttu-id="1b4e5-242">about_Automatic_Variables</span><span class="sxs-lookup"><span data-stu-id="1b4e5-242">about_Automatic_Variables</span></span>](about_Automatic_Variables.md)

[<span data-ttu-id="1b4e5-243">about_Environment_Variables</span><span class="sxs-lookup"><span data-stu-id="1b4e5-243">about_Environment_Variables</span></span>](about_Environment_Variables.md)

[<span data-ttu-id="1b4e5-244">about_Preference_Variables</span><span class="sxs-lookup"><span data-stu-id="1b4e5-244">about_Preference_Variables</span></span>](about_Preference_Variables.md)

[<span data-ttu-id="1b4e5-245">about_Profiles</span><span class="sxs-lookup"><span data-stu-id="1b4e5-245">about_Profiles</span></span>](about_Profiles.md)

[<span data-ttu-id="1b4e5-246">about_Quoting_Rules</span><span class="sxs-lookup"><span data-stu-id="1b4e5-246">about_Quoting_Rules</span></span>](about_Quoting_Rules.md)

[<span data-ttu-id="1b4e5-247">about_Scopes</span><span class="sxs-lookup"><span data-stu-id="1b4e5-247">about_Scopes</span></span>](about_Scopes.md)

[<span data-ttu-id="1b4e5-248">about_Remote_Variables</span><span class="sxs-lookup"><span data-stu-id="1b4e5-248">about_Remote_Variables</span></span>](about_Remote_Variables.md)

