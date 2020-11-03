---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 4/26/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/add-member?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Add-Member
ms.openlocfilehash: 1c07d79af1516becff86a0706906fa6ddfe03ab8
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93267932"
---
# <span data-ttu-id="a4d2c-103">Add-Member</span><span class="sxs-lookup"><span data-stu-id="a4d2c-103">Add-Member</span></span>

## <span data-ttu-id="a4d2c-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="a4d2c-104">SYNOPSIS</span></span>
<span data-ttu-id="a4d2c-105">Lägger till anpassade egenskaper och metoder till en instans av ett PowerShell-objekt.</span><span class="sxs-lookup"><span data-stu-id="a4d2c-105">Adds custom properties and methods to an instance of a PowerShell object.</span></span>

## <span data-ttu-id="a4d2c-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="a4d2c-106">SYNTAX</span></span>

### <span data-ttu-id="a4d2c-107">TypeNameSet (standard)</span><span class="sxs-lookup"><span data-stu-id="a4d2c-107">TypeNameSet (Default)</span></span>

```
Add-Member -InputObject <PSObject> -TypeName <String> [-PassThru] [<CommonParameters>]
```

### <span data-ttu-id="a4d2c-108">NotePropertyMultiMemberSet</span><span class="sxs-lookup"><span data-stu-id="a4d2c-108">NotePropertyMultiMemberSet</span></span>

```
Add-Member -InputObject <PSObject> [-TypeName <String>] [-Force] [-PassThru]
 [-NotePropertyMembers] <IDictionary> [<CommonParameters>]
```

### <span data-ttu-id="a4d2c-109">NotePropertySingleMemberSet</span><span class="sxs-lookup"><span data-stu-id="a4d2c-109">NotePropertySingleMemberSet</span></span>

```
Add-Member -InputObject <PSObject> [-TypeName <String>] [-Force] [-PassThru] [-NotePropertyName] <String>
 [-NotePropertyValue] <Object> [<CommonParameters>]
```

### <span data-ttu-id="a4d2c-110">Mängd</span><span class="sxs-lookup"><span data-stu-id="a4d2c-110">MemberSet</span></span>

```
Add-Member -InputObject <PSObject> [-MemberType] <PSMemberTypes> [-Name] <String> [[-Value] <Object>]
 [[-SecondValue] <Object>] [-TypeName <String>] [-Force] [-PassThru] [<CommonParameters>]
```

## <span data-ttu-id="a4d2c-111">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="a4d2c-111">DESCRIPTION</span></span>

<span data-ttu-id="a4d2c-112">Med `Add-Member` cmdleten kan du lägga till medlemmar (egenskaper och metoder) till en instans av ett PowerShell-objekt.</span><span class="sxs-lookup"><span data-stu-id="a4d2c-112">The `Add-Member` cmdlet lets you add members (properties and methods) to an instance of a PowerShell object.</span></span> <span data-ttu-id="a4d2c-113">Du kan till exempel lägga till en NoteProperty-medlem som innehåller en beskrivning av objektet eller en **ScriptMethod** -medlem som kör ett skript för att ändra objektet.</span><span class="sxs-lookup"><span data-stu-id="a4d2c-113">For instance, you can add a NoteProperty member that contains a description of the object or a **ScriptMethod** member that runs a script to change the object.</span></span>

<span data-ttu-id="a4d2c-114">Om du vill använda `Add-Member` , pipe objektet till `Add-Member` , eller Använd parametern **InputObject** för att ange objektet.</span><span class="sxs-lookup"><span data-stu-id="a4d2c-114">To use `Add-Member`, pipe the object to `Add-Member`, or use the **InputObject** parameter to specify the object.</span></span>

<span data-ttu-id="a4d2c-115">Parametern **MemberType** anger vilken typ av medlem som du vill lägga till.</span><span class="sxs-lookup"><span data-stu-id="a4d2c-115">The **MemberType** parameter indicates the type of member that you want to add.</span></span> <span data-ttu-id="a4d2c-116">Parametern **Name** tilldelar ett namn till den nya medlemmen och **värde** parametern anger medlemmens värde.</span><span class="sxs-lookup"><span data-stu-id="a4d2c-116">The **Name** parameter assigns a name to the new member, and the **Value** parameter sets the value of the member.</span></span>

<span data-ttu-id="a4d2c-117">De egenskaper och metoder som du lägger till läggs bara till i den specifika instansen av det objekt som du anger.</span><span class="sxs-lookup"><span data-stu-id="a4d2c-117">The properties and methods that you add are added only to the particular instance of the object that you specify.</span></span> <span data-ttu-id="a4d2c-118">`Add-Member` ändrar inte objekt typen.</span><span class="sxs-lookup"><span data-stu-id="a4d2c-118">`Add-Member` does not change the object type.</span></span> <span data-ttu-id="a4d2c-119">Använd cmdleten om du vill skapa en ny objekt typ `Add-Type` .</span><span class="sxs-lookup"><span data-stu-id="a4d2c-119">To create a new object type, use the `Add-Type` cmdlet.</span></span>

<span data-ttu-id="a4d2c-120">Du kan också använda `Export-Clixml` cmdleten för att spara instansen av objektet, inklusive ytterligare medlemmar, i en fil.</span><span class="sxs-lookup"><span data-stu-id="a4d2c-120">You can also use the `Export-Clixml` cmdlet to save the instance of the object, including the additional members, in a file.</span></span> <span data-ttu-id="a4d2c-121">Sedan kan du använda `Import-Clixml` cmdleten för att återskapa instansen av objektet från den information som lagras i den exporterade filen.</span><span class="sxs-lookup"><span data-stu-id="a4d2c-121">Then you can use the `Import-Clixml` cmdlet to re-create the instance of the object from the information that is stored in the exported file.</span></span>

<span data-ttu-id="a4d2c-122">Från och med Windows PowerShell 3,0 `Add-Member` har nya funktioner som gör det enklare att lägga till antecknings egenskaper till objekt.</span><span class="sxs-lookup"><span data-stu-id="a4d2c-122">Beginning in Windows PowerShell 3.0, `Add-Member` has new features that make it easier to add note properties to objects.</span></span>
<span data-ttu-id="a4d2c-123">Du kan använda parametrarna **NotePropertyName** och **NotePropertyValue** för att definiera en antecknings egenskap eller använda parametern **NotePropertyMembers** , som tar en hash-tabell med antecknings egenskaps namn och värden.</span><span class="sxs-lookup"><span data-stu-id="a4d2c-123">You can use the **NotePropertyName** and **NotePropertyValue** parameters to define a note property or use the **NotePropertyMembers** parameter, which takes a hash table of note property names and values.</span></span>

<span data-ttu-id="a4d2c-124">Från och med Windows PowerShell 3,0 krävs även parametern **Passthru** , som genererar ett utgående objekt, vilket är mindre ofta.</span><span class="sxs-lookup"><span data-stu-id="a4d2c-124">Also, beginning in Windows PowerShell 3.0, the **PassThru** parameter, which generates an output object, is needed less frequently.</span></span> <span data-ttu-id="a4d2c-125">`Add-Member` nu läggs de nya medlemmarna direkt till i indatamängden av fler typer.</span><span class="sxs-lookup"><span data-stu-id="a4d2c-125">`Add-Member` now adds the new members directly to the input object of more types.</span></span> <span data-ttu-id="a4d2c-126">Mer information finns i Beskrivning av **Passthru** -parametern.</span><span class="sxs-lookup"><span data-stu-id="a4d2c-126">For more information, see the **PassThru** parameter description.</span></span>

## <span data-ttu-id="a4d2c-127">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="a4d2c-127">EXAMPLES</span></span>

### <span data-ttu-id="a4d2c-128">Exempel 1: Lägg till en antecknings egenskap i en PSObject</span><span class="sxs-lookup"><span data-stu-id="a4d2c-128">Example 1: Add a note property to a PSObject</span></span>

<span data-ttu-id="a4d2c-129">I följande exempel läggs en **status** antecknings egenskap till med värdet "utfört" till **fileinfo** -objektet som representerar `Test.txt` filen.</span><span class="sxs-lookup"><span data-stu-id="a4d2c-129">The following example adds a **Status** note property with a value of "Done" to the **FileInfo** object that represents the `Test.txt` file.</span></span>

<span data-ttu-id="a4d2c-130">Det första kommandot använder `Get-ChildItem` cmdleten för att hämta ett **fileinfo** -objekt som representerar `Test.txt` filen.</span><span class="sxs-lookup"><span data-stu-id="a4d2c-130">The first command uses the `Get-ChildItem` cmdlet to get a **FileInfo** object representing the `Test.txt` file.</span></span> <span data-ttu-id="a4d2c-131">Den sparar den i `$a` variabeln.</span><span class="sxs-lookup"><span data-stu-id="a4d2c-131">It saves it in the `$a` variable.</span></span>

<span data-ttu-id="a4d2c-132">Det andra kommandot lägger till antecknings egenskapen i objektet i `$a` .</span><span class="sxs-lookup"><span data-stu-id="a4d2c-132">The second command adds the note property to the object in `$a`.</span></span>

<span data-ttu-id="a4d2c-133">Det tredje kommandot använder punkt notation för att hämta värdet för objektets **status** egenskap i `$a` .</span><span class="sxs-lookup"><span data-stu-id="a4d2c-133">The third command uses dot notation to get the value of the **Status** property of the object in `$a`.</span></span> <span data-ttu-id="a4d2c-134">När utdata visas är värdet "klar".</span><span class="sxs-lookup"><span data-stu-id="a4d2c-134">As the output shows, the value is "Done".</span></span>

```powershell
$A = Get-ChildItem c:\ps-test\test.txt
$A | Add-Member -NotePropertyName Status -NotePropertyValue Done
$A.Status
```

```Output
Done
```

### <span data-ttu-id="a4d2c-135">Exempel 2: Lägg till en Ali Aset-egenskap i en PSObject</span><span class="sxs-lookup"><span data-stu-id="a4d2c-135">Example 2: Add an alias property to a PSObject</span></span>

<span data-ttu-id="a4d2c-136">I följande exempel lägger du till en **storleks** Ali Aset-egenskap till objektet som representerar `Test.txt` filen.</span><span class="sxs-lookup"><span data-stu-id="a4d2c-136">The following example adds a **Size** alias property to the object that represents the `Test.txt` file.</span></span> <span data-ttu-id="a4d2c-137">Den nya egenskapen är ett alias för egenskapen **length** .</span><span class="sxs-lookup"><span data-stu-id="a4d2c-137">The new property is an alias for the **Length** property.</span></span>

<span data-ttu-id="a4d2c-138">Det första kommandot använder `Get-ChildItem` cmdleten för att hämta `Test.txt` **fileinfo** -objektet.</span><span class="sxs-lookup"><span data-stu-id="a4d2c-138">The first command uses the `Get-ChildItem` cmdlet to get the `Test.txt` **FileInfo** object.</span></span>

<span data-ttu-id="a4d2c-139">Det andra kommandot lägger till egenskapen **storleks** Ali Aset.</span><span class="sxs-lookup"><span data-stu-id="a4d2c-139">The second command adds the **Size** alias property.</span></span>
<span data-ttu-id="a4d2c-140">Det tredje kommandot använder punkt notation för att hämta värdet för egenskapen ny **storlek** .</span><span class="sxs-lookup"><span data-stu-id="a4d2c-140">The third command uses dot notation to get the value of the new **Size** property.</span></span>

```powershell
$A = Get-ChildItem C:\Temp\test.txt
$A | Add-Member -MemberType AliasProperty -Name Size -Value Length
$A.Size
```

```Output
2394
```

### <span data-ttu-id="a4d2c-141">Exempel 3: lägga till en StringUse antecknings egenskap i en sträng</span><span class="sxs-lookup"><span data-stu-id="a4d2c-141">Example 3: Add a StringUse note property to a string</span></span>

<span data-ttu-id="a4d2c-142">I det här exemplet läggs **StringUse** -antecknings egenskapen till i en sträng.</span><span class="sxs-lookup"><span data-stu-id="a4d2c-142">This example adds the **StringUse** note property to a string.</span></span>
<span data-ttu-id="a4d2c-143">Eftersom `Add-Member` det inte går att lägga till typer till **stränga** indata-objekt kan du ange parametern **Passthru** för att generera ett utdata-objekt.</span><span class="sxs-lookup"><span data-stu-id="a4d2c-143">Because `Add-Member` cannot add types to **String** input objects, you can specify the **PassThru** parameter to generate an output object.</span></span> <span data-ttu-id="a4d2c-144">Det sista kommandot i exemplet visar den nya egenskapen.</span><span class="sxs-lookup"><span data-stu-id="a4d2c-144">The last command in the example displays the new property.</span></span>

<span data-ttu-id="a4d2c-145">I det här exemplet används parametern **NotePropertyMembers** .</span><span class="sxs-lookup"><span data-stu-id="a4d2c-145">This example uses the **NotePropertyMembers** parameter.</span></span> <span data-ttu-id="a4d2c-146">Värdet för parametern **NotePropertyMembers** är en hash-tabell.</span><span class="sxs-lookup"><span data-stu-id="a4d2c-146">The value of the **NotePropertyMembers** parameter is a hash table.</span></span> <span data-ttu-id="a4d2c-147">Nyckeln är anteckningens egenskaps namn, **StringUse** och värdet är anteckningens egenskaps värde, **Visa**.</span><span class="sxs-lookup"><span data-stu-id="a4d2c-147">The key is the note property name, **StringUse** , and the value is the note property value, **Display**.</span></span>

```powershell
$A = "A string"
$A = $A | Add-Member -NotePropertyMembers @{StringUse="Display"} -PassThru
$A.StringUse
```

```Output
Display
```

### <span data-ttu-id="a4d2c-148">Exempel 4: Lägg till en skript metod till ett FileInfo-objekt</span><span class="sxs-lookup"><span data-stu-id="a4d2c-148">Example 4: Add a script method to a FileInfo object</span></span>

<span data-ttu-id="a4d2c-149">I det här exemplet läggs skript metoden **att sizeinmb** till i ett **fileinfo** -objekt som beräknar fil storleken till närmaste megabyte.</span><span class="sxs-lookup"><span data-stu-id="a4d2c-149">This example adds the **SizeInMB** script method to a **FileInfo** object which calculates the file size to the nearest MegaByte.</span></span> <span data-ttu-id="a4d2c-150">Det andra kommandot skapar en **script block** som använder den **avrundade** statiska metoden från `[math]` typen för att runda av fil storleken till den andra decimal platsen.</span><span class="sxs-lookup"><span data-stu-id="a4d2c-150">The second command creates a **ScriptBlock** that uses the **Round** static method from the `[math]` type to round the file size to the second decimal place.</span></span>

<span data-ttu-id="a4d2c-151">Parametern **Value** använder också den `$This` automatiska variabeln som representerar det aktuella objektet.</span><span class="sxs-lookup"><span data-stu-id="a4d2c-151">The **Value** parameter also uses the `$This` automatic variable, which represents the current object.</span></span> <span data-ttu-id="a4d2c-152">`$This`Variabeln är endast giltig i skript block som definierar nya egenskaper och metoder.</span><span class="sxs-lookup"><span data-stu-id="a4d2c-152">The `$This` variable is valid only in script blocks that define new properties and methods.</span></span>

<span data-ttu-id="a4d2c-153">Det sista kommandot använder punkt notation för att anropa den nya **att sizeinmb** -skript metoden i objektet i `$A` variabeln.</span><span class="sxs-lookup"><span data-stu-id="a4d2c-153">The last command uses dot notation to call the new **SizeInMB** script method on the object in the `$A` variable.</span></span>

```powershell
$A = Get-ChildItem C:\Temp\test.txt
$S = {[math]::Round(($this.Length / 1MB), 2)}
$A | Add-Member -MemberType ScriptMethod -Name "SizeInMB" -Value $S
$A.SizeInMB()
```

```Output
0.43
```

### <span data-ttu-id="a4d2c-154">Exempel 5: kopiera alla egenskaper för ett objekt till ett annat</span><span class="sxs-lookup"><span data-stu-id="a4d2c-154">Example 5: Copy all properties of an object to another</span></span>

<span data-ttu-id="a4d2c-155">Den här funktionen kopierar alla egenskaper för ett objekt till ett annat objekt.</span><span class="sxs-lookup"><span data-stu-id="a4d2c-155">This function copies all of the properties of one object to another object.</span></span>

<span data-ttu-id="a4d2c-156">`foreach`Slingan använder `Get-Member` cmdleten för att hämta var och en av egenskaperna för **from** -objektet.</span><span class="sxs-lookup"><span data-stu-id="a4d2c-156">The `foreach` loop uses the `Get-Member` cmdlet to get each of the properties of the **From** object.</span></span> <span data-ttu-id="a4d2c-157">Kommandona i `foreach` slingan utförs i serien för varje egenskap.</span><span class="sxs-lookup"><span data-stu-id="a4d2c-157">The commands within the `foreach` loop are performed in series on each of the properties.</span></span>

<span data-ttu-id="a4d2c-158">`Add-Member`Kommandot lägger till egenskapen för **from** -objektet i objektet **till** som en **NoteProperty**.</span><span class="sxs-lookup"><span data-stu-id="a4d2c-158">The `Add-Member` command adds the property of the **From** object to the **To** object as a **NoteProperty**.</span></span> <span data-ttu-id="a4d2c-159">Värdet kopieras med parametern **Value** .</span><span class="sxs-lookup"><span data-stu-id="a4d2c-159">The value is copied using the **Value** parameter.</span></span> <span data-ttu-id="a4d2c-160">Den använder **Force** -parametern för att lägga till medlemmar med samma medlems namn.</span><span class="sxs-lookup"><span data-stu-id="a4d2c-160">It uses the **Force** parameter to add members with the same member name.</span></span>

```powershell
function Copy-Property ($From, $To)
{
    $properties = Get-Member -InputObject $From -MemberType Property
    foreach ($p in $properties)
    {
        $To | Add-Member -MemberType NoteProperty -Name $p.Name -Value $From.$($p.Name) -Force
    }
}
```

### <span data-ttu-id="a4d2c-161">Exempel 6: skapa ett anpassat objekt</span><span class="sxs-lookup"><span data-stu-id="a4d2c-161">Example 6: Create a custom object</span></span>

<span data-ttu-id="a4d2c-162">Det här exemplet skapar ett anpassat **till gångs** objekt.</span><span class="sxs-lookup"><span data-stu-id="a4d2c-162">This example creates an **Asset** custom object.</span></span>

<span data-ttu-id="a4d2c-163">`New-Object`Cmdleten skapar en **PSObject**.</span><span class="sxs-lookup"><span data-stu-id="a4d2c-163">The `New-Object` cmdlet creates a **PSObject**.</span></span> <span data-ttu-id="a4d2c-164">Exemplet sparar **PSObject** i `$Asset` variabeln.</span><span class="sxs-lookup"><span data-stu-id="a4d2c-164">The example saves the **PSObject** in the `$Asset` variable.</span></span>

<span data-ttu-id="a4d2c-165">Det andra kommandot använder `[ordered]` typen Accelerator för att skapa en ordnad ord lista med namn och värden.</span><span class="sxs-lookup"><span data-stu-id="a4d2c-165">The second command uses the `[ordered]` type accelerator to create an ordered dictionary of names and values.</span></span> <span data-ttu-id="a4d2c-166">Kommandot sparar resultatet i `$D` variabeln.</span><span class="sxs-lookup"><span data-stu-id="a4d2c-166">The command saves the result in the `$D` variable.</span></span>

<span data-ttu-id="a4d2c-167">Det tredje kommandot använder **NotePropertyMembers** -parametern för `Add-Member` cmdleten för att lägga till ord listan i `$D` variabeln till **PSObject**.</span><span class="sxs-lookup"><span data-stu-id="a4d2c-167">The third command uses the **NotePropertyMembers** parameter of the `Add-Member` cmdlet to add the dictionary in the `$D` variable to the **PSObject**.</span></span>
<span data-ttu-id="a4d2c-168">Egenskapen **TypeName** tilldelar ett nytt namn, **till gång** , till **PSObject**.</span><span class="sxs-lookup"><span data-stu-id="a4d2c-168">The **TypeName** property assigns a new name, **Asset** , to the **PSObject**.</span></span>

<span data-ttu-id="a4d2c-169">Det sista kommandot rör det nya **till gångs** objekt till `Get-Member` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="a4d2c-169">The last command pipes the new **Asset** object to the `Get-Member` cmdlet.</span></span> <span data-ttu-id="a4d2c-170">Utdata visar att objektet har ett typ namn för **till gång** och de antecknings egenskaper som vi definierade i den ordnade ord listan.</span><span class="sxs-lookup"><span data-stu-id="a4d2c-170">The output shows that the object has a type name of **Asset** and the note properties that we defined in the ordered dictionary.</span></span>

```powershell
$Asset = New-Object -TypeName PSObject
$d = [ordered]@{Name="Server30";System="Server Core";PSVersion="4.0"}
$Asset | Add-Member -NotePropertyMembers $d -TypeName Asset
$Asset | Get-Member
```

```Output
   TypeName: Asset

Name        MemberType   Definition
----        ----------   ----------
Equals      Method       bool Equals(System.Object obj)
GetHashCode Method       int GetHashCode()
GetType     Method       type GetType()
ToString    Method       string ToString()
Name        NoteProperty System.String Name=Server30
PSVersion   NoteProperty System.String PSVersion=4.0
System      NoteProperty System.String System=Server Core
```

## <span data-ttu-id="a4d2c-171">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="a4d2c-171">PARAMETERS</span></span>

### <span data-ttu-id="a4d2c-172">-Force</span><span class="sxs-lookup"><span data-stu-id="a4d2c-172">-Force</span></span>

<span data-ttu-id="a4d2c-173">Anger att denna cmdlet lägger till en ny medlem även om objektet har en anpassad medlem med samma namn.</span><span class="sxs-lookup"><span data-stu-id="a4d2c-173">Indicates that this cmdlet adds a new member even the object has a custom member with the same name.</span></span>
<span data-ttu-id="a4d2c-174">Du kan inte använda **Force** -parametern för att ersätta en standard medlem av en typ.</span><span class="sxs-lookup"><span data-stu-id="a4d2c-174">You cannot use the **Force** parameter to replace a standard member of a type.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: MemberSet, NotePropertySingleMemberSet, NotePropertyMultiMemberSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="a4d2c-175">– InputObject</span><span class="sxs-lookup"><span data-stu-id="a4d2c-175">-InputObject</span></span>

<span data-ttu-id="a4d2c-176">Anger objektet som den nya medlemmen ska läggas till i.</span><span class="sxs-lookup"><span data-stu-id="a4d2c-176">Specifies the object to which the new member is added.</span></span>
<span data-ttu-id="a4d2c-177">Ange en variabel som innehåller objekten eller Skriv ett kommando eller uttryck som hämtar objekten.</span><span class="sxs-lookup"><span data-stu-id="a4d2c-177">Enter a variable that contains the objects, or type a command or expression that gets the objects.</span></span>

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: (All)
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="a4d2c-178">– MemberType</span><span class="sxs-lookup"><span data-stu-id="a4d2c-178">-MemberType</span></span>

<span data-ttu-id="a4d2c-179">Anger vilken typ av medlem som ska läggas till.</span><span class="sxs-lookup"><span data-stu-id="a4d2c-179">Specifies the type of the member to add.</span></span>
<span data-ttu-id="a4d2c-180">Den här parametern är obligatorisk.</span><span class="sxs-lookup"><span data-stu-id="a4d2c-180">This parameter is required.</span></span>
<span data-ttu-id="a4d2c-181">De acceptabla värdena för den här parametern är:</span><span class="sxs-lookup"><span data-stu-id="a4d2c-181">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="a4d2c-182">NoteProperty</span><span class="sxs-lookup"><span data-stu-id="a4d2c-182">NoteProperty</span></span>
- <span data-ttu-id="a4d2c-183">AliasProperty</span><span class="sxs-lookup"><span data-stu-id="a4d2c-183">AliasProperty</span></span>
- <span data-ttu-id="a4d2c-184">ScriptProperty</span><span class="sxs-lookup"><span data-stu-id="a4d2c-184">ScriptProperty</span></span>
- <span data-ttu-id="a4d2c-185">CodeProperty</span><span class="sxs-lookup"><span data-stu-id="a4d2c-185">CodeProperty</span></span>
- <span data-ttu-id="a4d2c-186">ScriptMethod</span><span class="sxs-lookup"><span data-stu-id="a4d2c-186">ScriptMethod</span></span>
- <span data-ttu-id="a4d2c-187">CodeMethod</span><span class="sxs-lookup"><span data-stu-id="a4d2c-187">CodeMethod</span></span>

<span data-ttu-id="a4d2c-188">Information om dessa värden finns i [PSMemberTypes-uppräkning](/dotnet/api/system.management.automation.psmembertypes) i MSDN-biblioteket.</span><span class="sxs-lookup"><span data-stu-id="a4d2c-188">For information about these values, see [PSMemberTypes Enumeration](/dotnet/api/system.management.automation.psmembertypes) in the MSDN library.</span></span>

<span data-ttu-id="a4d2c-189">Alla objekt har inte alla typer av medlemmar.</span><span class="sxs-lookup"><span data-stu-id="a4d2c-189">Not all objects have every type of member.</span></span>
<span data-ttu-id="a4d2c-190">Om du anger en medlems typ som objektet inte har, returnerar PowerShell ett fel.</span><span class="sxs-lookup"><span data-stu-id="a4d2c-190">If you specify a member type that the object does not have, PowerShell returns an error.</span></span>

```yaml
Type: System.Management.Automation.PSMemberTypes
Parameter Sets: MemberSet
Aliases: Type
Accepted values: AliasProperty, CodeProperty, Property, NoteProperty, ScriptProperty, Properties, PropertySet, Method, CodeMethod, ScriptMethod, Methods, ParameterizedProperty, MemberSet, Event, Dynamic, All

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="a4d2c-191">-Name</span><span class="sxs-lookup"><span data-stu-id="a4d2c-191">-Name</span></span>

<span data-ttu-id="a4d2c-192">Anger namnet på medlemmen som denna cmdlet lägger till.</span><span class="sxs-lookup"><span data-stu-id="a4d2c-192">Specifies the name of the member that this cmdlet adds.</span></span>

```yaml
Type: System.String
Parameter Sets: MemberSet
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="a4d2c-193">-NotePropertyMembers</span><span class="sxs-lookup"><span data-stu-id="a4d2c-193">-NotePropertyMembers</span></span>

<span data-ttu-id="a4d2c-194">Anger en hash-tabell eller en ordnad ord lista med namn och värden för antecknings egenskaper.</span><span class="sxs-lookup"><span data-stu-id="a4d2c-194">Specifies a hash table or ordered dictionary of note property names and values.</span></span>
<span data-ttu-id="a4d2c-195">Ange en hash-tabell eller-ordlista där nycklarna är antecknings egenskaps namn och värdena är antecknings egenskaps värden.</span><span class="sxs-lookup"><span data-stu-id="a4d2c-195">Type a hash table or dictionary in which the keys are note property names and the values are note property values.</span></span>

<span data-ttu-id="a4d2c-196">Mer information om hash-tabeller och beställda ord listor i PowerShell finns [about_Hash_Tables](../Microsoft.PowerShell.Core/About/about_Hash_Tables.md).</span><span class="sxs-lookup"><span data-stu-id="a4d2c-196">For more information about hash tables and ordered dictionaries in PowerShell, see [about_Hash_Tables](../Microsoft.PowerShell.Core/About/about_Hash_Tables.md).</span></span>

<span data-ttu-id="a4d2c-197">Den här parametern introducerades i Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="a4d2c-197">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Collections.IDictionary
Parameter Sets: NotePropertyMultiMemberSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="a4d2c-198">-NotePropertyName</span><span class="sxs-lookup"><span data-stu-id="a4d2c-198">-NotePropertyName</span></span>

<span data-ttu-id="a4d2c-199">Anger anteckningens egenskaps namn.</span><span class="sxs-lookup"><span data-stu-id="a4d2c-199">Specifies the note property name.</span></span>

<span data-ttu-id="a4d2c-200">Använd den här parametern med parametern **NotePropertyValue** .</span><span class="sxs-lookup"><span data-stu-id="a4d2c-200">Use this parameter with the **NotePropertyValue** parameter.</span></span>
<span data-ttu-id="a4d2c-201">Den här parametern är valfri.</span><span class="sxs-lookup"><span data-stu-id="a4d2c-201">This parameter is optional.</span></span>

<span data-ttu-id="a4d2c-202">Den här parametern introducerades i Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="a4d2c-202">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.String
Parameter Sets: NotePropertySingleMemberSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="a4d2c-203">-NotePropertyValue</span><span class="sxs-lookup"><span data-stu-id="a4d2c-203">-NotePropertyValue</span></span>

<span data-ttu-id="a4d2c-204">Anger anteckningens egenskaps värde.</span><span class="sxs-lookup"><span data-stu-id="a4d2c-204">Specifies the note property value.</span></span>

<span data-ttu-id="a4d2c-205">Använd den här parametern med parametern **NotePropertyName** .</span><span class="sxs-lookup"><span data-stu-id="a4d2c-205">Use this parameter with the **NotePropertyName** parameter.</span></span>
<span data-ttu-id="a4d2c-206">Den här parametern är valfri.</span><span class="sxs-lookup"><span data-stu-id="a4d2c-206">This parameter is optional.</span></span>

<span data-ttu-id="a4d2c-207">Den här parametern introducerades i Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="a4d2c-207">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Object
Parameter Sets: NotePropertySingleMemberSet
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="a4d2c-208">– PassThru</span><span class="sxs-lookup"><span data-stu-id="a4d2c-208">-PassThru</span></span>

<span data-ttu-id="a4d2c-209">Returnerar ett objekt som representerar det objekt som du arbetar med.</span><span class="sxs-lookup"><span data-stu-id="a4d2c-209">Returns an object representing the item with which you are working.</span></span>
<span data-ttu-id="a4d2c-210">Som standard genererar denna cmdlet inga utdata.</span><span class="sxs-lookup"><span data-stu-id="a4d2c-210">By default, this cmdlet does not generate any output.</span></span>

<span data-ttu-id="a4d2c-211">För de flesta objekt `Add-Member` lägger till de nya medlemmarna i objektet.</span><span class="sxs-lookup"><span data-stu-id="a4d2c-211">For most objects, `Add-Member` adds the new members to the input object.</span></span>
<span data-ttu-id="a4d2c-212">När inobjektet är en sträng kan du dock `Add-Member` inte lägga till medlemmen i objektet.</span><span class="sxs-lookup"><span data-stu-id="a4d2c-212">However, when the input object is a string, `Add-Member` cannot add the member to the input object.</span></span>
<span data-ttu-id="a4d2c-213">För dessa objekt använder du parametern **Passthru** för att skapa ett utgående objekt.</span><span class="sxs-lookup"><span data-stu-id="a4d2c-213">For these objects, use the **PassThru** parameter to create an output object.</span></span>

<span data-ttu-id="a4d2c-214">I Windows PowerShell 2,0, `Add-Member` lades endast till medlemmar till **PSObject** -omslutningen av objekt, inte för objektet.</span><span class="sxs-lookup"><span data-stu-id="a4d2c-214">In Windows PowerShell 2.0, `Add-Member` added members only to the **PSObject** wrapper of objects, not to the object.</span></span>
<span data-ttu-id="a4d2c-215">Använd parametern **Passthru** för att skapa ett utgående objekt för alla objekt som har ett **PSObject** -gränssnitt.</span><span class="sxs-lookup"><span data-stu-id="a4d2c-215">Use the **PassThru** parameter to create an output object for any object that has a **PSObject** wrapper.</span></span>

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

### <span data-ttu-id="a4d2c-216">-SecondValue</span><span class="sxs-lookup"><span data-stu-id="a4d2c-216">-SecondValue</span></span>

<span data-ttu-id="a4d2c-217">Anger ytterligare information om **AliasProperty** -, **ScriptProperty** -, **CodeProperty** -eller **CodeMethod** -medlemmar.</span><span class="sxs-lookup"><span data-stu-id="a4d2c-217">Specifies optional additional information about **AliasProperty** , **ScriptProperty** , **CodeProperty** , or **CodeMethod** members.</span></span>

<span data-ttu-id="a4d2c-218">Om den här parametern används för att lägga till en **AliasProperty** måste den vara av data typen.</span><span class="sxs-lookup"><span data-stu-id="a4d2c-218">If used when adding an **AliasProperty** , this parameter must be a data type.</span></span>
<span data-ttu-id="a4d2c-219">En konvertering till den angivna data typen läggs till i värdet för **AliasProperty**.</span><span class="sxs-lookup"><span data-stu-id="a4d2c-219">A conversion to the specified data type is added to the value of the **AliasProperty**.</span></span>

<span data-ttu-id="a4d2c-220">Om du till exempel lägger till en **AliasProperty** som ger ett alternativt namn för en sträng egenskap, kan du även ange en **SecondValue** -parameter för **system. Int32** för att indikera att värdet för den sträng egenskapen ska konverteras till ett heltal vid åtkomst med motsvarande **AliasProperty**.</span><span class="sxs-lookup"><span data-stu-id="a4d2c-220">For example, if you add an **AliasProperty** that provides an alternate name for a string property, you can also specify a **SecondValue** parameter of **System.Int32** to indicate that the value of that string property should be converted to an integer when accessed by using the corresponding **AliasProperty**.</span></span>

<span data-ttu-id="a4d2c-221">Du kan använda parametern **SecondValue** för att ange ytterligare en **script block** när du lägger till en **ScriptProperty** -medlem.</span><span class="sxs-lookup"><span data-stu-id="a4d2c-221">You can use the **SecondValue** parameter to specify an additional **ScriptBlock** when adding a **ScriptProperty** member.</span></span> <span data-ttu-id="a4d2c-222">Den första **script block** , som anges i parametern **Value** , används för att hämta värdet för en variabel.</span><span class="sxs-lookup"><span data-stu-id="a4d2c-222">The first **ScriptBlock** , specified in the **Value** parameter, is used to get the value of a variable.</span></span> <span data-ttu-id="a4d2c-223">Den andra **script block** som anges i parametern **SecondValue** används för att ange värdet för en variabel.</span><span class="sxs-lookup"><span data-stu-id="a4d2c-223">The second **ScriptBlock** , specified in the **SecondValue** parameter, is used to set the value of a variable.</span></span>

```yaml
Type: System.Object
Parameter Sets: MemberSet
Aliases:

Required: False
Position: 3
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="a4d2c-224">-Värde</span><span class="sxs-lookup"><span data-stu-id="a4d2c-224">-Value</span></span>

<span data-ttu-id="a4d2c-225">Anger det inledande värdet för den tillagda medlemmen.</span><span class="sxs-lookup"><span data-stu-id="a4d2c-225">Specifies the initial value of the added member.</span></span>
<span data-ttu-id="a4d2c-226">Om du lägger till en **AliasProperty** -, **CodeProperty** -, **ScriptProperty** -eller **CodeMethod** -medlem kan du ange valfri, ytterligare information med hjälp av parametern **SecondValue** .</span><span class="sxs-lookup"><span data-stu-id="a4d2c-226">If you add an **AliasProperty** , **CodeProperty** , **ScriptProperty** or **CodeMethod** member, you can supply optional, additional information by using the **SecondValue** parameter.</span></span>

```yaml
Type: System.Object
Parameter Sets: MemberSet
Aliases:

Required: False
Position: 2
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="a4d2c-227">-TypeName</span><span class="sxs-lookup"><span data-stu-id="a4d2c-227">-TypeName</span></span>

<span data-ttu-id="a4d2c-228">Anger ett namn för typen.</span><span class="sxs-lookup"><span data-stu-id="a4d2c-228">Specifies a name for the type.</span></span>

<span data-ttu-id="a4d2c-229">När typen är en klass i **system** namn området eller en typ som har en typ Accelerator, kan du ange det korta namnet för typen.</span><span class="sxs-lookup"><span data-stu-id="a4d2c-229">When the type is a class in the **System** namespace or a type that has a type accelerator, you can enter the short name of the type.</span></span> <span data-ttu-id="a4d2c-230">Annars krävs det fullständiga typ namnet.</span><span class="sxs-lookup"><span data-stu-id="a4d2c-230">Otherwise, the full type name is required.</span></span>
<span data-ttu-id="a4d2c-231">Den här parametern är endast effektiv när **InputObject** är en **PSObject**.</span><span class="sxs-lookup"><span data-stu-id="a4d2c-231">This parameter is effective only when the **InputObject** is a **PSObject**.</span></span>

<span data-ttu-id="a4d2c-232">Den här parametern introducerades i Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="a4d2c-232">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.String
Parameter Sets: TypeNameSet, NotePropertyMultiMemberSet, NotePropertySingleMemberSet, MemberSet
Aliases:

Required: True (TypeNameSet), False (NotePropertyMultiMemberSet, NotePropertySingleMemberSet, MemberSet)
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="a4d2c-233">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="a4d2c-233">CommonParameters</span></span>

<span data-ttu-id="a4d2c-234">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="a4d2c-234">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="a4d2c-235">Mer information finns i [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span><span class="sxs-lookup"><span data-stu-id="a4d2c-235">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="a4d2c-236">INDATA</span><span class="sxs-lookup"><span data-stu-id="a4d2c-236">INPUTS</span></span>

### <span data-ttu-id="a4d2c-237">System. Management. Automation. PSObject</span><span class="sxs-lookup"><span data-stu-id="a4d2c-237">System.Management.Automation.PSObject</span></span>

<span data-ttu-id="a4d2c-238">Du kan skicka vidare valfri objekt typ till denna cmdlet.</span><span class="sxs-lookup"><span data-stu-id="a4d2c-238">You can pipe any object type to this cmdlet.</span></span>

## <span data-ttu-id="a4d2c-239">UTDATA</span><span class="sxs-lookup"><span data-stu-id="a4d2c-239">OUTPUTS</span></span>

### <span data-ttu-id="a4d2c-240">Ingen eller system. Object</span><span class="sxs-lookup"><span data-stu-id="a4d2c-240">None or System.Object</span></span>

<span data-ttu-id="a4d2c-241">När du använder parametern **Passthru** returnerar denna cmdlet det nyligen utökade objektet.</span><span class="sxs-lookup"><span data-stu-id="a4d2c-241">When you use the **PassThru** parameter, this cmdlet returns the newly-extended object.</span></span>
<span data-ttu-id="a4d2c-242">Annars genererar denna cmdlet inga utdata.</span><span class="sxs-lookup"><span data-stu-id="a4d2c-242">Otherwise, this cmdlet does not generate any output.</span></span>

## <span data-ttu-id="a4d2c-243">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="a4d2c-243">NOTES</span></span>

<span data-ttu-id="a4d2c-244">Du kan bara lägga till medlemmar i **PSObject** -objekt.</span><span class="sxs-lookup"><span data-stu-id="a4d2c-244">You can add members only to **PSObject** objects.</span></span> <span data-ttu-id="a4d2c-245">Använd operatorn för att avgöra om ett objekt är ett **PSObject** -objekt `-is` .</span><span class="sxs-lookup"><span data-stu-id="a4d2c-245">To determine whether an object is a **PSObject** object, use the `-is` operator.</span></span>

<span data-ttu-id="a4d2c-246">Om du till exempel vill testa ett objekt som lagras i `$obj` variabeln skriver du `$obj -is [PSObject]` .</span><span class="sxs-lookup"><span data-stu-id="a4d2c-246">For instance, to test an object stored in the `$obj` variable, type `$obj -is [PSObject]`.</span></span>

<span data-ttu-id="a4d2c-247">Namnen på parametrarna **MemberType** , **Name** , **Value** och **SecondValue** är valfria.</span><span class="sxs-lookup"><span data-stu-id="a4d2c-247">The names of the **MemberType** , **Name** , **Value** , and **SecondValue** parameters are optional.</span></span>
<span data-ttu-id="a4d2c-248">Om du utelämnar parameter namnen måste de parameter värden som inte är namngivna visas i den här ordningen: **MemberType** , **Name** , **Value** och **SecondValue**.</span><span class="sxs-lookup"><span data-stu-id="a4d2c-248">If you omit the parameter names, the unnamed parameter values must appear in this order: **MemberType** , **Name** , **Value** , and **SecondValue**.</span></span>

<span data-ttu-id="a4d2c-249">Om du inkluderar parameter namnen kan parametrarna visas i vilken ordning som helst.</span><span class="sxs-lookup"><span data-stu-id="a4d2c-249">If you include the parameter names, the parameters can appear in any order.</span></span>

<span data-ttu-id="a4d2c-250">Du kan använda den `$this` automatiska variabeln i skript block som definierar värdena för nya egenskaper och metoder.</span><span class="sxs-lookup"><span data-stu-id="a4d2c-250">You can use the `$this` automatic variable in script blocks that define the values of new properties and methods.</span></span>
<span data-ttu-id="a4d2c-251">`$this`Variabeln refererar till den instans av objektet som egenskaper och metoder läggs till i.</span><span class="sxs-lookup"><span data-stu-id="a4d2c-251">The `$this` variable refers to the instance of the object to which the properties and methods are being added.</span></span> <span data-ttu-id="a4d2c-252">Mer information om `$this` variabeln finns i [about_Automatic_Variables](../Microsoft.PowerShell.Core/About/about_Automatic_Variables.md).</span><span class="sxs-lookup"><span data-stu-id="a4d2c-252">For more information about the `$this` variable, see [about_Automatic_Variables](../Microsoft.PowerShell.Core/About/about_Automatic_Variables.md).</span></span>

## <span data-ttu-id="a4d2c-253">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="a4d2c-253">RELATED LINKS</span></span>

[<span data-ttu-id="a4d2c-254">Exportera – CliXml</span><span class="sxs-lookup"><span data-stu-id="a4d2c-254">Export-Clixml</span></span>](Export-Clixml.md)

[<span data-ttu-id="a4d2c-255">Hämta medlem</span><span class="sxs-lookup"><span data-stu-id="a4d2c-255">Get-Member</span></span>](Get-Member.md)

[<span data-ttu-id="a4d2c-256">Importera – CliXml</span><span class="sxs-lookup"><span data-stu-id="a4d2c-256">Import-Clixml</span></span>](Import-Clixml.md)

[<span data-ttu-id="a4d2c-257">Nytt – objekt</span><span class="sxs-lookup"><span data-stu-id="a4d2c-257">New-Object</span></span>](New-Object.md)

[<span data-ttu-id="a4d2c-258">about_Automatic_Variables</span><span class="sxs-lookup"><span data-stu-id="a4d2c-258">about_Automatic_Variables</span></span>](../Microsoft.PowerShell.Core/About/about_Automatic_Variables.md)

