---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 09/08/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/foreach-object?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: ForEach-Object
ms.openlocfilehash: 327add884077083d37e1f58ab8f78b784a870362
ms.sourcegitcommit: e0f9fe6335be1e0f94bedaa0e8baec2acaeaa076
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 09/10/2020
ms.locfileid: "93269445"
---
# <span data-ttu-id="9b377-103">ForEach-Object</span><span class="sxs-lookup"><span data-stu-id="9b377-103">ForEach-Object</span></span>

## <span data-ttu-id="9b377-104">Sammanfattning</span><span class="sxs-lookup"><span data-stu-id="9b377-104">Synopsis</span></span>
<span data-ttu-id="9b377-105">Utför en åtgärd mot varje objekt i en samling inobjekt.</span><span class="sxs-lookup"><span data-stu-id="9b377-105">Performs an operation against each item in a collection of input objects.</span></span>

## <span data-ttu-id="9b377-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="9b377-106">Syntax</span></span>

### <span data-ttu-id="9b377-107">ScriptBlockSet (standard)</span><span class="sxs-lookup"><span data-stu-id="9b377-107">ScriptBlockSet (Default)</span></span>

```
ForEach-Object [-InputObject <PSObject>] [-Begin <ScriptBlock>] [-Process] <ScriptBlock[]>
 [-End <ScriptBlock>] [-RemainingScripts <ScriptBlock[]>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="9b377-108">PropertyAndMethodSet</span><span class="sxs-lookup"><span data-stu-id="9b377-108">PropertyAndMethodSet</span></span>

```
ForEach-Object [-InputObject <PSObject>] [-MemberName] <String> [-ArgumentList <Object[]>] [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="9b377-109">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="9b377-109">Description</span></span>

<span data-ttu-id="9b377-110">`ForEach-Object`Cmdleten utför en åtgärd på varje objekt i en samling inobjekt.</span><span class="sxs-lookup"><span data-stu-id="9b377-110">The `ForEach-Object` cmdlet performs an operation on each item in a collection of input objects.</span></span> <span data-ttu-id="9b377-111">Objekten kan skickas till cmdleten eller anges med parametern **InputObject** .</span><span class="sxs-lookup"><span data-stu-id="9b377-111">The input objects can be piped to the cmdlet or specified by using the **InputObject** parameter.</span></span>

<span data-ttu-id="9b377-112">Från och med Windows PowerShell 3,0 finns det två olika sätt att skapa ett `ForEach-Object` kommando.</span><span class="sxs-lookup"><span data-stu-id="9b377-112">Starting in Windows PowerShell 3.0, there are two different ways to construct a `ForEach-Object` command.</span></span>

- <span data-ttu-id="9b377-113">**Skript block**.</span><span class="sxs-lookup"><span data-stu-id="9b377-113">**Script block**.</span></span> <span data-ttu-id="9b377-114">Du kan använda ett-skript block för att ange åtgärden.</span><span class="sxs-lookup"><span data-stu-id="9b377-114">You can use a script block to specify the operation.</span></span> <span data-ttu-id="9b377-115">I-skript blocket använder du `$_` variabeln för att representera det aktuella objektet.</span><span class="sxs-lookup"><span data-stu-id="9b377-115">Within the script block, use the `$_` variable to represent the current object.</span></span> <span data-ttu-id="9b377-116">Skript blocket är värdet för **process** parametern.</span><span class="sxs-lookup"><span data-stu-id="9b377-116">The script block is the value of the **Process** parameter.</span></span> <span data-ttu-id="9b377-117">Skript blocket kan innehålla alla PowerShell-skript.</span><span class="sxs-lookup"><span data-stu-id="9b377-117">The script block can contain any PowerShell script.</span></span>

  <span data-ttu-id="9b377-118">Till exempel hämtar följande kommando värdet för egenskapen **processname** för varje process på datorn.</span><span class="sxs-lookup"><span data-stu-id="9b377-118">For example, the following command gets the value of the **ProcessName** property of each process on the computer.</span></span>

  `Get-Process | ForEach-Object {$_.ProcessName}`

  <span data-ttu-id="9b377-119">`ForEach-Object` stöder `begin` -, `process` -och- `end` blocken enligt beskrivningen i [about_Functions](about/about_functions.md#piping-objects-to-functions).</span><span class="sxs-lookup"><span data-stu-id="9b377-119">`ForEach-Object` supports the `begin`, `process`, and `end` blocks as described in [about_functions](about/about_functions.md#piping-objects-to-functions).</span></span>

  > [!NOTE]
  > <span data-ttu-id="9b377-120">Skript blocken körs i anroparens omfång.</span><span class="sxs-lookup"><span data-stu-id="9b377-120">The script blocks run in the caller's scope.</span></span> <span data-ttu-id="9b377-121">Därför har blocken åtkomst till variabler i det omfånget och kan skapa nya variabler som finns kvar i det omfånget när cmdleten har slutförts.</span><span class="sxs-lookup"><span data-stu-id="9b377-121">Therefore the blocks have access to variables in that scope and can create new variables that persist in that scope after the cmdlet completes.</span></span>

- <span data-ttu-id="9b377-122">**Åtgärds uttryck**.</span><span class="sxs-lookup"><span data-stu-id="9b377-122">**Operation statement**.</span></span> <span data-ttu-id="9b377-123">Du kan också skriva en åtgärds instruktion, som är mycket mer likt naturligt språk.</span><span class="sxs-lookup"><span data-stu-id="9b377-123">You can also write an operation statement, which is much more like natural language.</span></span> <span data-ttu-id="9b377-124">Du kan använda instruktionen operation för att ange ett egenskaps värde eller anropa en metod.</span><span class="sxs-lookup"><span data-stu-id="9b377-124">You can use the operation statement to specify a property value or call a method.</span></span> <span data-ttu-id="9b377-125">Åtgärds instruktioner introducerades i Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="9b377-125">Operation statements were introduced in Windows PowerShell 3.0.</span></span>

  <span data-ttu-id="9b377-126">Följande kommando hämtar till exempel också värdet för egenskapen **processname** för varje process på datorn.</span><span class="sxs-lookup"><span data-stu-id="9b377-126">For example, the following command also gets the value of the **ProcessName** property of each process on the computer.</span></span>

  `Get-Process | ForEach-Object ProcessName`

## <span data-ttu-id="9b377-127">Exempel</span><span class="sxs-lookup"><span data-stu-id="9b377-127">Examples</span></span>

### <span data-ttu-id="9b377-128">Exempel 1: dividera heltal i en matris</span><span class="sxs-lookup"><span data-stu-id="9b377-128">Example 1: Divide integers in an array</span></span>

<span data-ttu-id="9b377-129">Det här exemplet tar en matris med tre heltal och dividerar var och en av dem med 1024.</span><span class="sxs-lookup"><span data-stu-id="9b377-129">This example takes an array of three integers and divides each one of them by 1024.</span></span>

```powershell
30000, 56798, 12432 | ForEach-Object -Process {$_/1024}
```

```Output
29.296875
55.466796875
12.140625
```

### <span data-ttu-id="9b377-130">Exempel 2: Hämta längden på alla filer i en katalog</span><span class="sxs-lookup"><span data-stu-id="9b377-130">Example 2: Get the length of all the files in a directory</span></span>

<span data-ttu-id="9b377-131">I det här exemplet behandlas filerna och katalogerna i installations katalogen för PowerShell `$PSHOME` .</span><span class="sxs-lookup"><span data-stu-id="9b377-131">This example processes the files and directories in the PowerShell installation directory `$PSHOME`.</span></span>

```powershell
Get-ChildItem $PSHOME |
  ForEach-Object -Process {if (!$_.PSIsContainer) {$_.Name; $_.Length / 1024; " " }}
```

<span data-ttu-id="9b377-132">Om objektet inte är en katalog får skript blocket namnet på filen, dividerar värdet för egenskapen **length** med 1024 och lägger till ett blank steg ("") för att skilja det från nästa post.</span><span class="sxs-lookup"><span data-stu-id="9b377-132">If the object is not a directory, the script block gets the name of the file, divides the value of its **Length** property by 1024, and adds a space (" ") to separate it from the next entry.</span></span> <span data-ttu-id="9b377-133">Cmdleten använder egenskapen **PSISContainer** för att avgöra om ett objekt är en katalog.</span><span class="sxs-lookup"><span data-stu-id="9b377-133">The cmdlet uses the **PSISContainer** property to determine whether an object is a directory.</span></span>

### <span data-ttu-id="9b377-134">Exempel 3: arbeta med de senaste system händelserna</span><span class="sxs-lookup"><span data-stu-id="9b377-134">Example 3: Operate on the most recent System events</span></span>

<span data-ttu-id="9b377-135">I det här exemplet skriver du de senaste 1000 händelserna från systemets händelse logg till en textfil.</span><span class="sxs-lookup"><span data-stu-id="9b377-135">This example write the 1000 most recent events from the System event log to a text file.</span></span> <span data-ttu-id="9b377-136">Aktuell tid visas före och efter bearbetning av händelser.</span><span class="sxs-lookup"><span data-stu-id="9b377-136">The current time is displayed before and after processing the events.</span></span>

```powershell
$Events = Get-EventLog -LogName System -Newest 1000
$events | ForEach-Object -Begin {Get-Date} -Process {Out-File -FilePath Events.txt -Append -InputObject $_.Message} -End {Get-Date}
```

<span data-ttu-id="9b377-137">`Get-EventLog` hämtar de senaste 1000 händelserna från system händelse loggen och lagrar dem i `$Events` variabeln.</span><span class="sxs-lookup"><span data-stu-id="9b377-137">`Get-EventLog` gets the 1000 most recent events from the System event log and stores them in the `$Events` variable.</span></span> <span data-ttu-id="9b377-138">`$Events` skickas sedan till `ForEach-Object` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="9b377-138">`$Events` is then piped to the `ForEach-Object` cmdlet.</span></span> <span data-ttu-id="9b377-139">Parametern **BEGIN** visar aktuellt datum och tid.</span><span class="sxs-lookup"><span data-stu-id="9b377-139">The **Begin** parameter displays the current date and time.</span></span> <span data-ttu-id="9b377-140">Därefter använder **process** -parametern `Out-File` cmdleten för att skapa en textfil med namnet events.txt och lagrar meddelande egenskapen för varje händelse i filen.</span><span class="sxs-lookup"><span data-stu-id="9b377-140">Next, the **Process** parameter uses the `Out-File` cmdlet to create a text file that is named events.txt and stores the message property of each of the events in that file.</span></span> <span data-ttu-id="9b377-141">Sist används parametern **End** för att visa datum och tid när all bearbetning har slutförts.</span><span class="sxs-lookup"><span data-stu-id="9b377-141">Last, the **End** parameter is used to display the date and time after all of the processing has completed.</span></span>

### <span data-ttu-id="9b377-142">Exempel 4: ändra värdet för en register nyckel</span><span class="sxs-lookup"><span data-stu-id="9b377-142">Example 4: Change the value of a Registry key</span></span>

<span data-ttu-id="9b377-143">Det här exemplet ändrar värdet för register posten **remotePath** i alla under nycklar under `HKCU:\Network` nyckeln till versal text.</span><span class="sxs-lookup"><span data-stu-id="9b377-143">This example changes the value of the **RemotePath** registry entry in all of the subkeys under the `HKCU:\Network` key to uppercase text.</span></span>

```powershell
Get-ItemProperty -Path HKCU:\Network\* |
  ForEach-Object {Set-ItemProperty -Path $_.PSPath -Name RemotePath -Value $_.RemotePath.ToUpper();}
```

<span data-ttu-id="9b377-144">Du kan använda det här formatet för att ändra formuläret eller innehållet i ett register post värde.</span><span class="sxs-lookup"><span data-stu-id="9b377-144">You can use this format to change the form or content of a registry entry value.</span></span>

<span data-ttu-id="9b377-145">Varje under nyckel i **nätverks** nyckeln representerar en mappad nätverks enhet som kommer att återansluta vid inloggning.</span><span class="sxs-lookup"><span data-stu-id="9b377-145">Each subkey in the **Network** key represents a mapped network drive that will reconnect at logon.</span></span>
<span data-ttu-id="9b377-146">**RemotePath** -posten innehåller UNC-sökvägen till den anslutna enheten.</span><span class="sxs-lookup"><span data-stu-id="9b377-146">The **RemotePath** entry contains the UNC path of the connected drive.</span></span> <span data-ttu-id="9b377-147">Om du till exempel mappar E: enheten till `\\Server\Share` , kommer det att finnas en **E** -under nyckel `HKCU:\Network` och värdet för register posten **remotePath** i **E** -undernyckeln är `\\Server\Share` .</span><span class="sxs-lookup"><span data-stu-id="9b377-147">For example, if you map the E: drive to `\\Server\Share`, there will be an **E** subkey of `HKCU:\Network` and the value of the **RemotePath** registry entry in the **E** subkey is `\\Server\Share`.</span></span>

<span data-ttu-id="9b377-148">Kommandot använder `Get-ItemProperty` cmdleten för att hämta alla under nycklar för **nätverks** nyckeln och `Set-ItemProperty` cmdleten för att ändra värdet för register posten **remotePath** i varje nyckel.</span><span class="sxs-lookup"><span data-stu-id="9b377-148">The command uses the `Get-ItemProperty` cmdlet to get all of the subkeys of the **Network** key and the `Set-ItemProperty` cmdlet to change the value of the **RemotePath** registry entry in each key.</span></span>
<span data-ttu-id="9b377-149">I `Set-ItemProperty` kommandot är sökvägen värdet för egenskapen **PSPath** i register nyckeln.</span><span class="sxs-lookup"><span data-stu-id="9b377-149">In the `Set-ItemProperty` command, the path is the value of the **PSPath** property of the registry key.</span></span> <span data-ttu-id="9b377-150">Detta är en egenskap för det Microsoft .NET Framework-objekt som representerar register nyckeln, inte en register post.</span><span class="sxs-lookup"><span data-stu-id="9b377-150">This is a property of the Microsoft .NET Framework object that represents the registry key, not a registry entry.</span></span> <span data-ttu-id="9b377-151">Kommandot använder metoden **ToUpper ()** i **remotePath** -värdet, som är en sträng (REG_SZ).</span><span class="sxs-lookup"><span data-stu-id="9b377-151">The command uses the **ToUpper()** method of the **RemotePath** value, which is a string (REG_SZ).</span></span>

<span data-ttu-id="9b377-152">Eftersom `Set-ItemProperty` ändrar egenskapen för varje nyckel, `ForEach-Object` krävs cmdleten för att komma åt egenskapen.</span><span class="sxs-lookup"><span data-stu-id="9b377-152">Because `Set-ItemProperty` is changing the property of each key, the `ForEach-Object` cmdlet is required to access the property.</span></span>

### <span data-ttu-id="9b377-153">Exempel 5: Använd den automatiska variabeln $Null</span><span class="sxs-lookup"><span data-stu-id="9b377-153">Example 5: Use the $Null automatic variable</span></span>

<span data-ttu-id="9b377-154">I det här exemplet visas en funktion för att skicka den `$Null` automatiska variabeln till `ForEach-Object` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="9b377-154">This example shows the effect of piping the `$Null` automatic variable to the `ForEach-Object` cmdlet.</span></span>

```powershell
1, 2, $null, 4 | ForEach-Object {"Hello"}
```

```Output
Hello
Hello
Hello
Hello
```

<span data-ttu-id="9b377-155">Eftersom PowerShell behandlar null som en explicit plats hållare, `ForEach-Object` genererar cmdleten ett värde för `$Null` , precis som för andra objekt som du skickar till den.</span><span class="sxs-lookup"><span data-stu-id="9b377-155">Because PowerShell treats null as an explicit placeholder, the `ForEach-Object` cmdlet generates a value for `$Null`, just as it does for other objects that you pipe to it.</span></span>

### <span data-ttu-id="9b377-156">Exempel 6: Hämta egenskaps värden</span><span class="sxs-lookup"><span data-stu-id="9b377-156">Example 6: Get property values</span></span>

<span data-ttu-id="9b377-157">I det här exemplet hämtas värdet för egenskapen **sökväg** för alla installerade PowerShell-moduler med hjälp av parametern **MemberName** för `ForEach-Object` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="9b377-157">This example gets the value of the **Path** property of all installed PowerShell modules by using the **MemberName** parameter of the `ForEach-Object` cmdlet.</span></span>

```powershell
Get-Module -ListAvailable | ForEach-Object -MemberName Path
Get-Module -ListAvailable | Foreach Path
```

<span data-ttu-id="9b377-158">Det andra kommandot motsvarar det första.</span><span class="sxs-lookup"><span data-stu-id="9b377-158">The second command is equivalent to the first.</span></span> <span data-ttu-id="9b377-159">Det använder `Foreach` aliaset för `ForEach-Object` cmdleten och utelämnar namnet på parametern **MemberName** , som är valfritt.</span><span class="sxs-lookup"><span data-stu-id="9b377-159">It uses the `Foreach` alias of the `ForEach-Object` cmdlet and omits the name of the **MemberName** parameter, which is optional.</span></span>

<span data-ttu-id="9b377-160">`ForEach-Object`Cmdleten är mycket användbar för att hämta egenskaps värden, eftersom den hämtar värdet utan att ändra typen, till skillnad från **format** -cmdlet: ar eller `Select-Object` cmdleten, som ändrar egenskaps värde typen.</span><span class="sxs-lookup"><span data-stu-id="9b377-160">The `ForEach-Object` cmdlet is very useful for getting property values, because it gets the value without changing the type, unlike the **Format** cmdlets or the `Select-Object` cmdlet, which change the property value type.</span></span>

### <span data-ttu-id="9b377-161">Exempel 7: dela Modulnamn i namn på komponenter</span><span class="sxs-lookup"><span data-stu-id="9b377-161">Example 7: Split module names into component names</span></span>

<span data-ttu-id="9b377-162">I det här exemplet visas tre sätt att dela två punktavgränsade modulnamn till sina komponent namn.</span><span class="sxs-lookup"><span data-stu-id="9b377-162">This examples shows three ways to split two dot-separated module names into their component names.</span></span>

```powershell
"Microsoft.PowerShell.Core", "Microsoft.PowerShell.Host" | ForEach-Object {$_.Split(".")}
"Microsoft.PowerShell.Core", "Microsoft.PowerShell.Host" | ForEach-Object -MemberName Split -ArgumentList "."
"Microsoft.PowerShell.Core", "Microsoft.PowerShell.Host" | Foreach Split "."
```

```Output
Microsoft
PowerShell
Core
Microsoft
PowerShell
Host
```

<span data-ttu-id="9b377-163">Kommandona anropar **delnings** metoden för strängar.</span><span class="sxs-lookup"><span data-stu-id="9b377-163">The commands call the **Split** method of strings.</span></span> <span data-ttu-id="9b377-164">De tre kommandona använder olika syntax, men de är likvärdiga och utbytbara.</span><span class="sxs-lookup"><span data-stu-id="9b377-164">The three commands use different syntax, but they are equivalent and interchangeable.</span></span>

<span data-ttu-id="9b377-165">Det första kommandot använder den traditionella syntaxen, som innehåller ett skript block och den aktuella objekt operatorn `$_` .</span><span class="sxs-lookup"><span data-stu-id="9b377-165">The first command uses the traditional syntax, which includes a script block and the current object operator `$_`.</span></span> <span data-ttu-id="9b377-166">Den använder punktsyntax för att ange den metod och den parentes som ska omges av argumentet avgränsnings uttryck.</span><span class="sxs-lookup"><span data-stu-id="9b377-166">It uses the dot syntax to specify the method and parentheses to enclose the delimiter argument.</span></span>

<span data-ttu-id="9b377-167">Det andra kommandot använder parametern **MemberName** för att ange metoden **Split** och parametern **ArgumentName** för att identifiera punkten (".") som uppdelnings avgränsare.</span><span class="sxs-lookup"><span data-stu-id="9b377-167">The second command uses the **MemberName** parameter to specify the **Split** method and the **ArgumentName** parameter to identify the dot (".") as the split delimiter.</span></span>

<span data-ttu-id="9b377-168">Det tredje kommandot använder **förgrunds** Ali Aset för `ForEach-Object` cmdleten och utelämnar Namnen på parametrarna **MemberName** och **argument List** , som är valfria.</span><span class="sxs-lookup"><span data-stu-id="9b377-168">The third command uses the **Foreach** alias of the `ForEach-Object` cmdlet and omits the names of the **MemberName** and **ArgumentList** parameters, which are optional.</span></span>

### <span data-ttu-id="9b377-169">Exempel 8: använda ForEach-Object med två skript block</span><span class="sxs-lookup"><span data-stu-id="9b377-169">Example 8: Using ForEach-Object with two script blocks</span></span>

<span data-ttu-id="9b377-170">I det här exemplet skickar vi två skript block i position.</span><span class="sxs-lookup"><span data-stu-id="9b377-170">In this example we pass two script blocks positionally.</span></span> <span data-ttu-id="9b377-171">Alla skript block binder till **process** parametern.</span><span class="sxs-lookup"><span data-stu-id="9b377-171">All the script blocks bind to the **Process** parameter.</span></span> <span data-ttu-id="9b377-172">De behandlas dock som om de hade skickats till parametrarna **BEGIN** och **process** .</span><span class="sxs-lookup"><span data-stu-id="9b377-172">However, they are treated as if they had been passed to the **Begin** and **Process** parameters.</span></span>

```powershell
1..2 | ForEach-Object { 'begin' } { 'process' }
```

```Output
begin
process
process
```

### <span data-ttu-id="9b377-173">Exempel 9: använda ForEach-Object med fler än två skript block</span><span class="sxs-lookup"><span data-stu-id="9b377-173">Example 9: Using ForEach-Object with more than two script blocks</span></span>

<span data-ttu-id="9b377-174">I det här exemplet skickar vi två skript block i position.</span><span class="sxs-lookup"><span data-stu-id="9b377-174">In this example we pass two script blocks positionally.</span></span> <span data-ttu-id="9b377-175">Alla skript block binder till **process** parametern.</span><span class="sxs-lookup"><span data-stu-id="9b377-175">All the script blocks bind to the **Process** parameter.</span></span> <span data-ttu-id="9b377-176">De behandlas dock som om de hade skickats till parametrarna **BEGIN** , **process** och **End** .</span><span class="sxs-lookup"><span data-stu-id="9b377-176">However, they are treated as if they had been passed to the **Begin** , **Process** , and **End** parameters.</span></span>

```powershell
1..2 | ForEach-Object { 'begin' } { 'process A' }  { 'process B' }  { 'end' }
```

```Output
begin
process A
process B
process A
process B
end
```

> [!NOTE]
> <span data-ttu-id="9b377-177">Det första skript blocket mappas alltid till `begin` blocket, det sista blocket mappas till `end` blocket och blocken mellan är alla mappade till `process` blocket.</span><span class="sxs-lookup"><span data-stu-id="9b377-177">The first script block is always mapped to the `begin` block, the last block is mapped to the `end` block, and the blocks in between are all mapped to the `process` block.</span></span>

### <span data-ttu-id="9b377-178">Exempel 10: kör flera skript block för varje pipeline-objekt</span><span class="sxs-lookup"><span data-stu-id="9b377-178">Example 10: Run multiple script blocks for each pipeline item</span></span>

<span data-ttu-id="9b377-179">Som du ser i det föregående exemplet har flera skript block som skickas med **process** parametern mappats till **Start** -och **slut** parametrarna.</span><span class="sxs-lookup"><span data-stu-id="9b377-179">As shown in the previous example, multiple script blocks passed using the **Process** parameter get mapped to the **Begin** and **End** parameters.</span></span> <span data-ttu-id="9b377-180">För att undvika den här mappningen måste du ange explicita värden för **Start** -och **slut** parametrarna.</span><span class="sxs-lookup"><span data-stu-id="9b377-180">To avoid this mapping, you must provide explicit values for the **Begin** and **End** parameters.</span></span>

```powershell
1..2 | ForEach-Object -Begin $null -Process { 'one' }, { 'two' }, { 'three' } -End $null
```

```Output
one
two
three
one
two
three
```

## <span data-ttu-id="9b377-181">Parametrar</span><span class="sxs-lookup"><span data-stu-id="9b377-181">Parameters</span></span>

### <span data-ttu-id="9b377-182">– Argument List</span><span class="sxs-lookup"><span data-stu-id="9b377-182">-ArgumentList</span></span>

<span data-ttu-id="9b377-183">Anger en matris med argument till ett metod anrop.</span><span class="sxs-lookup"><span data-stu-id="9b377-183">Specifies an array of arguments to a method call.</span></span> <span data-ttu-id="9b377-184">Mer information om beteendet för **argument List** finns [about_Splatting](about/about_Splatting.md#splatting-with-arrays).</span><span class="sxs-lookup"><span data-stu-id="9b377-184">For more information about the behavior of **ArgumentList** , see [about_Splatting](about/about_Splatting.md#splatting-with-arrays).</span></span>

<span data-ttu-id="9b377-185">Den här parametern introducerades i Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="9b377-185">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Object[]
Parameter Sets: PropertyAndMethodSet
Aliases: Args

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="9b377-186">– Börja</span><span class="sxs-lookup"><span data-stu-id="9b377-186">-Begin</span></span>

<span data-ttu-id="9b377-187">Anger ett skript block som körs innan denna cmdlet bearbetar eventuella inobjekt.</span><span class="sxs-lookup"><span data-stu-id="9b377-187">Specifies a script block that runs before this cmdlet processes any input objects.</span></span> <span data-ttu-id="9b377-188">Det här skript blocket körs bara en gång för hela pipelinen.</span><span class="sxs-lookup"><span data-stu-id="9b377-188">This script block is only run once for the entire pipeline.</span></span> <span data-ttu-id="9b377-189">Mer information om `begin` blocket finns [about_Functions](about/about_functions.md#piping-objects-to-functions).</span><span class="sxs-lookup"><span data-stu-id="9b377-189">For more information about the `begin` block, see [about_Functions](about/about_functions.md#piping-objects-to-functions).</span></span>

```yaml
Type: System.Management.Automation.ScriptBlock
Parameter Sets: ScriptBlockSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="9b377-190">-Slut</span><span class="sxs-lookup"><span data-stu-id="9b377-190">-End</span></span>

<span data-ttu-id="9b377-191">Anger ett skript block som körs när denna cmdlet bearbetar alla inobjekt.</span><span class="sxs-lookup"><span data-stu-id="9b377-191">Specifies a script block that runs after this cmdlet processes all input objects.</span></span> <span data-ttu-id="9b377-192">Det här skript blocket körs bara en gång för hela pipelinen.</span><span class="sxs-lookup"><span data-stu-id="9b377-192">This script block is only run once for the entire pipeline.</span></span> <span data-ttu-id="9b377-193">Mer information om `end` blocket finns [about_Functions](about/about_functions.md#piping-objects-to-functions).</span><span class="sxs-lookup"><span data-stu-id="9b377-193">For more information about the `end` block, see [about_Functions](about/about_functions.md#piping-objects-to-functions).</span></span>

```yaml
Type: System.Management.Automation.ScriptBlock
Parameter Sets: ScriptBlockSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="9b377-194">– InputObject</span><span class="sxs-lookup"><span data-stu-id="9b377-194">-InputObject</span></span>

<span data-ttu-id="9b377-195">Anger ingående objekt.</span><span class="sxs-lookup"><span data-stu-id="9b377-195">Specifies the input objects.</span></span> <span data-ttu-id="9b377-196">`ForEach-Object` Kör skript blocket eller instruktions satsen för varje indatamängds objekt.</span><span class="sxs-lookup"><span data-stu-id="9b377-196">`ForEach-Object` runs the script block or operation statement on each input object.</span></span> <span data-ttu-id="9b377-197">Ange en variabel som innehåller objekten eller Skriv ett kommando eller uttryck som hämtar objekten.</span><span class="sxs-lookup"><span data-stu-id="9b377-197">Enter a variable that contains the objects, or type a command or expression that gets the objects.</span></span>

<span data-ttu-id="9b377-198">När du använder parametern **InputObject** i `ForEach-Object` , i stället för Skicka kommando resultat till `ForEach-Object` , behandlas **InputObject** -värdet som ett enskilt objekt.</span><span class="sxs-lookup"><span data-stu-id="9b377-198">When you use the **InputObject** parameter with `ForEach-Object`, instead of piping command results to `ForEach-Object`, the **InputObject** value is treated as a single object.</span></span> <span data-ttu-id="9b377-199">Detta gäller även om värdet är en samling som är resultatet av ett kommando, till exempel `-InputObject (Get-Process)` .</span><span class="sxs-lookup"><span data-stu-id="9b377-199">This is true even if the value is a collection that is the result of a command, such as `-InputObject (Get-Process)`.</span></span>
<span data-ttu-id="9b377-200">Eftersom **InputObject** inte kan returnera enskilda egenskaper från en matris eller samling objekt, rekommenderar vi att om du använder `ForEach-Object` för att utföra åtgärder på en samling objekt för de objekt som har specifika värden i definierade egenskaper, använder du `ForEach-Object` i pipelinen, som du ser i exemplen i det här avsnittet.</span><span class="sxs-lookup"><span data-stu-id="9b377-200">Because **InputObject** cannot return individual properties from an array or collection of objects, we recommend that if you use `ForEach-Object` to perform operations on a collection of objects for those objects that have specific values in defined properties, you use `ForEach-Object` in the pipeline, as shown in the examples in this topic.</span></span>

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

### <span data-ttu-id="9b377-201">– MemberName</span><span class="sxs-lookup"><span data-stu-id="9b377-201">-MemberName</span></span>

<span data-ttu-id="9b377-202">Anger den egenskap som ska hämtas eller metoden som ska anropas.</span><span class="sxs-lookup"><span data-stu-id="9b377-202">Specifies the property to get or the method to call.</span></span>

<span data-ttu-id="9b377-203">Jokertecken är tillåtna men fungerar bara om den resulterande strängen matchar ett unikt värde.</span><span class="sxs-lookup"><span data-stu-id="9b377-203">Wildcard characters are permitted, but work only if the resulting string resolves to a unique value.</span></span>
<span data-ttu-id="9b377-204">Om du till exempel kör `Get-Process | ForEach -MemberName *Name` och fler än en medlem finns med ett namn som innehåller sträng namnet, t. ex. egenskaperna **processname** och **Name** , Miss lyckas kommandot.</span><span class="sxs-lookup"><span data-stu-id="9b377-204">If, for example, you run `Get-Process | ForEach -MemberName *Name`, and more than one member exists with a name that contains the string Name, such as the **ProcessName** and **Name** properties, the command fails.</span></span>

<span data-ttu-id="9b377-205">Den här parametern introducerades i Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="9b377-205">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.String
Parameter Sets: PropertyAndMethodSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="9b377-206">– Process</span><span class="sxs-lookup"><span data-stu-id="9b377-206">-Process</span></span>

<span data-ttu-id="9b377-207">Anger den åtgärd som ska utföras för varje indatamängds objekt.</span><span class="sxs-lookup"><span data-stu-id="9b377-207">Specifies the operation that is performed on each input object.</span></span> <span data-ttu-id="9b377-208">Det här skript blocket körs för varje objekt i pipelinen.</span><span class="sxs-lookup"><span data-stu-id="9b377-208">This script block is run for every object in the pipeline.</span></span> <span data-ttu-id="9b377-209">Mer information om `process` blocket finns [about_Functions](about/about_functions.md#piping-objects-to-functions).</span><span class="sxs-lookup"><span data-stu-id="9b377-209">For more information about the `process` block, see [about_Functions](about/about_functions.md#piping-objects-to-functions).</span></span>

<span data-ttu-id="9b377-210">När du anger flera skript block till **process** parametern, mappas det första skript blocket alltid till `begin` blocket.</span><span class="sxs-lookup"><span data-stu-id="9b377-210">When you provide multiple script blocks to the **Process** parameter, the first script block is always mapped to the `begin` block.</span></span> <span data-ttu-id="9b377-211">Om det bara finns två skript block mappas det andra blocket till `process` blocket.</span><span class="sxs-lookup"><span data-stu-id="9b377-211">If there are only two script blocks, the second block is mapped to the `process` block.</span></span> <span data-ttu-id="9b377-212">Om det finns tre eller fler skript block mappas det första skript blocket alltid till `begin` blocket, det sista blocket mappas till `end` blocket och blocken mellan är alla mappade till `process` blocket.</span><span class="sxs-lookup"><span data-stu-id="9b377-212">If there are three or more script blocks, first script block is always mapped to the `begin` block, the last block is mapped to the `end` block, and the blocks in between are all mapped to the `process` block.</span></span>

```yaml
Type: System.Management.Automation.ScriptBlock[]
Parameter Sets: ScriptBlockSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="9b377-213">-RemainingScripts</span><span class="sxs-lookup"><span data-stu-id="9b377-213">-RemainingScripts</span></span>

<span data-ttu-id="9b377-214">Anger alla skript block som inte tas av **process** parametern.</span><span class="sxs-lookup"><span data-stu-id="9b377-214">Specifies all script blocks that are not taken by the **Process** parameter.</span></span>

<span data-ttu-id="9b377-215">Den här parametern introducerades i Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="9b377-215">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.ScriptBlock[]
Parameter Sets: ScriptBlockSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="9b377-216">-Confirm</span><span class="sxs-lookup"><span data-stu-id="9b377-216">-Confirm</span></span>

<span data-ttu-id="9b377-217">Uppmanar dig att bekräfta innan du kör cmdleten.</span><span class="sxs-lookup"><span data-stu-id="9b377-217">Prompts you for confirmation before running the cmdlet.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="9b377-218">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="9b377-218">-WhatIf</span></span>

<span data-ttu-id="9b377-219">Visar vad som skulle hända om cmdleten kördes.</span><span class="sxs-lookup"><span data-stu-id="9b377-219">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="9b377-220">Cmdleten körs inte.</span><span class="sxs-lookup"><span data-stu-id="9b377-220">The cmdlet is not run.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: wi

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="9b377-221">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="9b377-221">CommonParameters</span></span>

<span data-ttu-id="9b377-222">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="9b377-222">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="9b377-223">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="9b377-223">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="9b377-224">Indata</span><span class="sxs-lookup"><span data-stu-id="9b377-224">Inputs</span></span>

### <span data-ttu-id="9b377-225">System. Management. Automation. PSObject</span><span class="sxs-lookup"><span data-stu-id="9b377-225">System.Management.Automation.PSObject</span></span>

<span data-ttu-id="9b377-226">Du kan skicka alla objekt till denna cmdlet.</span><span class="sxs-lookup"><span data-stu-id="9b377-226">You can pipe any object to this cmdlet.</span></span>

## <span data-ttu-id="9b377-227">Utdata</span><span class="sxs-lookup"><span data-stu-id="9b377-227">Outputs</span></span>

### <span data-ttu-id="9b377-228">System. Management. Automation. PSObject</span><span class="sxs-lookup"><span data-stu-id="9b377-228">System.Management.Automation.PSObject</span></span>

<span data-ttu-id="9b377-229">Denna cmdlet returnerar objekt som bestäms av indatamängden.</span><span class="sxs-lookup"><span data-stu-id="9b377-229">This cmdlet returns objects that are determined by the input.</span></span>

## <span data-ttu-id="9b377-230">Kommentarer</span><span class="sxs-lookup"><span data-stu-id="9b377-230">Notes</span></span>

- <span data-ttu-id="9b377-231">`ForEach-Object`Cmdleten fungerar ungefär som en **förgrunds** instruktion, förutom att du inte kan skicka vidare indatamängdar till en **förgrunds** deklaration.</span><span class="sxs-lookup"><span data-stu-id="9b377-231">The `ForEach-Object` cmdlet works much like the **Foreach** statement, except that you cannot pipe input to a **Foreach** statement.</span></span> <span data-ttu-id="9b377-232">Mer information om den **förgrunds** instruktionen finns [about_Foreach](./About/about_Foreach.md).</span><span class="sxs-lookup"><span data-stu-id="9b377-232">For more information about the **Foreach** statement, see [about_Foreach](./About/about_Foreach.md).</span></span>

- <span data-ttu-id="9b377-233">Med början i PowerShell 4,0 `Where` och `ForEach` metoder har lagts till för användning med samlingar.</span><span class="sxs-lookup"><span data-stu-id="9b377-233">Starting in PowerShell 4.0, `Where` and `ForEach` methods were added for use with collections.</span></span> <span data-ttu-id="9b377-234">Du kan läsa mer om de här nya metoderna här [about_arrays](./About/about_Arrays.md)</span><span class="sxs-lookup"><span data-stu-id="9b377-234">You can read more about these new methods here [about_arrays](./About/about_Arrays.md)</span></span>

## <span data-ttu-id="9b377-235">Relaterade länkar</span><span class="sxs-lookup"><span data-stu-id="9b377-235">Related links</span></span>

[<span data-ttu-id="9b377-236">Jämför objekt</span><span class="sxs-lookup"><span data-stu-id="9b377-236">Compare-Object</span></span>](../Microsoft.PowerShell.Utility/Compare-Object.md)

[<span data-ttu-id="9b377-237">Where-objekt</span><span class="sxs-lookup"><span data-stu-id="9b377-237">Where-Object</span></span>](Where-Object.md)

[<span data-ttu-id="9b377-238">Gruppera objekt</span><span class="sxs-lookup"><span data-stu-id="9b377-238">Group-Object</span></span>](../Microsoft.PowerShell.Utility/Group-Object.md)

[<span data-ttu-id="9b377-239">Mått – objekt</span><span class="sxs-lookup"><span data-stu-id="9b377-239">Measure-Object</span></span>](../Microsoft.PowerShell.Utility/Measure-Object.md)

[<span data-ttu-id="9b377-240">Nytt – objekt</span><span class="sxs-lookup"><span data-stu-id="9b377-240">New-Object</span></span>](../Microsoft.PowerShell.Utility/New-Object.md)

[<span data-ttu-id="9b377-241">Select-Object</span><span class="sxs-lookup"><span data-stu-id="9b377-241">Select-Object</span></span>](../Microsoft.PowerShell.Utility/Select-Object.md)

[<span data-ttu-id="9b377-242">Sortera objekt</span><span class="sxs-lookup"><span data-stu-id="9b377-242">Sort-Object</span></span>](../Microsoft.PowerShell.Utility/Sort-Object.md)

[<span data-ttu-id="9b377-243">Tee – objekt</span><span class="sxs-lookup"><span data-stu-id="9b377-243">Tee-Object</span></span>](../Microsoft.PowerShell.Utility/Tee-Object.md)
