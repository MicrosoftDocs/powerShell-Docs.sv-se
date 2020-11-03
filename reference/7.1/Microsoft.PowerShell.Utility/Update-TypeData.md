---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 04/27/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/update-typedata?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Update-TypeData
ms.openlocfilehash: 5f6a9014ad86ba0c80694d7cf49104b56ce27d9d
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93265616"
---
# <span data-ttu-id="cfe3b-103">Update-TypeData</span><span class="sxs-lookup"><span data-stu-id="cfe3b-103">Update-TypeData</span></span>

## <span data-ttu-id="cfe3b-104">Sammanfattning</span><span class="sxs-lookup"><span data-stu-id="cfe3b-104">Synopsis</span></span>
<span data-ttu-id="cfe3b-105">Uppdaterar den utökade data typen i sessionen.</span><span class="sxs-lookup"><span data-stu-id="cfe3b-105">Updates the extended type data in the session.</span></span>

## <span data-ttu-id="cfe3b-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="cfe3b-106">Syntax</span></span>

### <span data-ttu-id="cfe3b-107">FileSet (standard)</span><span class="sxs-lookup"><span data-stu-id="cfe3b-107">FileSet (Default)</span></span>

```
Update-TypeData [[-AppendPath] <String[]>] [-PrependPath <String[]>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### <span data-ttu-id="cfe3b-108">DynamicTypeSet</span><span class="sxs-lookup"><span data-stu-id="cfe3b-108">DynamicTypeSet</span></span>

```
Update-TypeData [-MemberType <PSMemberTypes>] [-MemberName <String>] [-Value <Object>]
 [-SecondValue <Object>] [-TypeConverter <Type>] [-TypeAdapter <Type>]
 [-SerializationMethod <String>] [-TargetTypeForDeserialization <Type>]
 [-SerializationDepth <Int32>] [-DefaultDisplayProperty <String>]
 [-InheritPropertySerializationSet <Nullable`1>] [-StringSerializationSource <String>]
 [-DefaultDisplayPropertySet <String[]>] [-DefaultKeyPropertySet <String[]>]
 [-PropertySerializationSet <String[]>] -TypeName <String> [-Force] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### <span data-ttu-id="cfe3b-109">TypeDataSet</span><span class="sxs-lookup"><span data-stu-id="cfe3b-109">TypeDataSet</span></span>

```
Update-TypeData [-Force] [-TypeData] <TypeData[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="cfe3b-110">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="cfe3b-110">Description</span></span>

<span data-ttu-id="cfe3b-111">`Update-TypeData`Cmdleten uppdaterar den utökade data typen i sessionen genom att läsa in `Types.ps1xml` filerna i minnet och lägga till nya utökade typ data.</span><span class="sxs-lookup"><span data-stu-id="cfe3b-111">The `Update-TypeData` cmdlet updates the extended type data in the session by reloading the `Types.ps1xml` files into memory and adding new extended type data.</span></span>

<span data-ttu-id="cfe3b-112">Som standard läser PowerShell in utökade typ data när det behövs.</span><span class="sxs-lookup"><span data-stu-id="cfe3b-112">By default, PowerShell loads extended type data as it is needed.</span></span> <span data-ttu-id="cfe3b-113">Utan parametrar `Update-TypeData` laddar om alla `Types.ps1xml` filer som har lästs in i sessionen, inklusive alla typer av filer som du har lagt till.</span><span class="sxs-lookup"><span data-stu-id="cfe3b-113">Without parameters, `Update-TypeData` reloads all of the `Types.ps1xml` files that it has loaded in the session, including any type files that you added.</span></span> <span data-ttu-id="cfe3b-114">Du kan använda parametrarna för `Update-TypeData` för att lägga till nya filfiler och lägga till och ersätta utökade typ data.</span><span class="sxs-lookup"><span data-stu-id="cfe3b-114">You can use the parameters of `Update-TypeData` to add new type files and add and replace extended type data.</span></span>

<span data-ttu-id="cfe3b-115">`Update-TypeData`Cmdleten kan användas för att förinstallera alla typ data.</span><span class="sxs-lookup"><span data-stu-id="cfe3b-115">The `Update-TypeData` cmdlet can be used to preload all type data.</span></span> <span data-ttu-id="cfe3b-116">Den här funktionen är särskilt användbar när du utvecklar typer och vill läsa in de nya typerna i test syfte.</span><span class="sxs-lookup"><span data-stu-id="cfe3b-116">This feature is particularly useful when you are developing types and want to load those new types for testing purposes.</span></span>

<span data-ttu-id="cfe3b-117">Från och med Windows PowerShell 3,0 kan du använda `Update-TypeData` för att lägga till och ersätta utökade typ data i sessionen utan att använda en `Types.ps1xml` fil.</span><span class="sxs-lookup"><span data-stu-id="cfe3b-117">Beginning in Windows PowerShell 3.0, you can use `Update-TypeData` to add and replace extended type data in the session without using a `Types.ps1xml` file.</span></span> <span data-ttu-id="cfe3b-118">Ange data som läggs till dynamiskt, det vill säga utan att en fil läggs till i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="cfe3b-118">Type data that is added dynamically, that is, without a file, is added only to the current session.</span></span> <span data-ttu-id="cfe3b-119">Lägg till ett `Update-TypeData` kommando i din PowerShell-profil om du vill lägga till typ data till alla sessioner.</span><span class="sxs-lookup"><span data-stu-id="cfe3b-119">To add the type data to all sessions, add an `Update-TypeData` command to your PowerShell profile.</span></span> <span data-ttu-id="cfe3b-120">Mer information finns i [about_Profiles](../Microsoft.PowerShell.Core/About/about_Profiles.md).</span><span class="sxs-lookup"><span data-stu-id="cfe3b-120">For more information, see [about_Profiles](../Microsoft.PowerShell.Core/About/about_Profiles.md).</span></span>

<span data-ttu-id="cfe3b-121">Från och med Windows PowerShell 3,0 kan du också använda `Get-TypeData` cmdleten för att hämta de utökade typerna i den aktuella sessionen och `Remove-TypeData` cmdleten för att ta bort utökade typer från den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="cfe3b-121">Also, beginning in Windows PowerShell 3.0, you can use the `Get-TypeData` cmdlet to get the extended types in the current session and the `Remove-TypeData` cmdlet to delete extended types from the current session.</span></span>

<span data-ttu-id="cfe3b-122">Undantag som inträffar i egenskaper, eller genom att lägga till egenskaper till ett `Update-TypeData` kommando, rapportera inte fel.</span><span class="sxs-lookup"><span data-stu-id="cfe3b-122">Exceptions that occur in properties, or from adding properties to an `Update-TypeData` command, do not report errors.</span></span> <span data-ttu-id="cfe3b-123">Detta är att utelämna undantag som skulle uppstå i många vanliga typer vid formatering och utmatning.</span><span class="sxs-lookup"><span data-stu-id="cfe3b-123">This is to suppress exceptions that would occur in many common types during formatting and outputting.</span></span> <span data-ttu-id="cfe3b-124">Om du får .NET-egenskaper kan du undvika att utelämna undantag genom att använda metoden syntax i stället, som du ser i följande exempel:</span><span class="sxs-lookup"><span data-stu-id="cfe3b-124">If you are getting .NET properties, you can work around the suppression of exceptions by using method syntax instead, as shown in the following example:</span></span>

`"hello".get_Length()`

<span data-ttu-id="cfe3b-125">Observera att metoden syntax bara kan användas med .NET-egenskaper.</span><span class="sxs-lookup"><span data-stu-id="cfe3b-125">Note that method syntax can only be used with .NET properties.</span></span> <span data-ttu-id="cfe3b-126">Egenskaper som läggs till genom att köra `Update-TypeData` cmdleten kan inte använda Method-syntax.</span><span class="sxs-lookup"><span data-stu-id="cfe3b-126">Properties that are added by running the `Update-TypeData` cmdlet cannot use method syntax.</span></span>

<span data-ttu-id="cfe3b-127">Mer information om `Types.ps1xml` filerna i PowerShell finns i [about_Types.ps1XML](../Microsoft.PowerShell.Core/About/about_Types.ps1xml.md).</span><span class="sxs-lookup"><span data-stu-id="cfe3b-127">For more information about the `Types.ps1xml` files in PowerShell, see [about_Types.ps1xml](../Microsoft.PowerShell.Core/About/about_Types.ps1xml.md).</span></span>

## <span data-ttu-id="cfe3b-128">Exempel</span><span class="sxs-lookup"><span data-stu-id="cfe3b-128">Examples</span></span>

### <span data-ttu-id="cfe3b-129">Exempel 1: uppdatera utökade typer</span><span class="sxs-lookup"><span data-stu-id="cfe3b-129">Example 1: Update extended types</span></span>

```powershell
Update-TypeData
```

<span data-ttu-id="cfe3b-130">Det här kommandot uppdaterar den utökade typ konfigurationen från `Types.ps1xml` filerna som redan har använts i sessionen.</span><span class="sxs-lookup"><span data-stu-id="cfe3b-130">This command updates the extended type configuration from the `Types.ps1xml` files that have already been used in the session.</span></span>

### <span data-ttu-id="cfe3b-131">Exempel 2: uppdaterings typer flera gånger</span><span class="sxs-lookup"><span data-stu-id="cfe3b-131">Example 2: Update types multiple times</span></span>

<span data-ttu-id="cfe3b-132">Det här exemplet visar hur du uppdaterar typerna i en typ fil flera gånger i samma session.</span><span class="sxs-lookup"><span data-stu-id="cfe3b-132">This example shows how to update the types in a type file multiple times in the same session.</span></span>

<span data-ttu-id="cfe3b-133">Det första kommandot uppdaterar den utökade typ konfigurationen från `Types.ps1xml` filerna, bearbetar `TypesA.types.ps1xml` `TypesB.types.ps1xml` filerna och först.</span><span class="sxs-lookup"><span data-stu-id="cfe3b-133">The first command updates the extended type configuration from the `Types.ps1xml` files, processing the `TypesA.types.ps1xml` and `TypesB.types.ps1xml` files first.</span></span>

<span data-ttu-id="cfe3b-134">Det andra kommandot visar hur du kan uppdatera `TypesA.types.ps1xml` igen, till exempel om du har lagt till eller ändrat en typ i filen.</span><span class="sxs-lookup"><span data-stu-id="cfe3b-134">The second command shows how to update the `TypesA.types.ps1xml` again, such as you might do if you added or changed a type in the file.</span></span> <span data-ttu-id="cfe3b-135">Du kan antingen upprepa föregående kommando för `TypesA.types.ps1xml` filen eller köra ett `Update-TypeData` kommando utan parametrar, eftersom `TypesA.types.ps1xml` redan finns i listan typ fil för den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="cfe3b-135">You can either repeat the previous command for the `TypesA.types.ps1xml` file, or run an `Update-TypeData` command without parameters, because `TypesA.types.ps1xml` is already in the type file list for the current session.</span></span>

```powershell
Update-TypeData -PrependPath TypesA.types.ps1xml, TypesB.types.ps1xml
Update-TypeData -PrependPath TypesA.types.ps1xml
```

### <span data-ttu-id="cfe3b-136">Exempel 3: lägga till en skript egenskap till DateTime-objekt</span><span class="sxs-lookup"><span data-stu-id="cfe3b-136">Example 3: Add a script property to DateTime objects</span></span>

<span data-ttu-id="cfe3b-137">I det här exemplet används `Update-TypeData` för att lägga till egenskapen för **kvartals** skript i **system. DateTime** -objekt i den aktuella sessionen, till exempel de som returneras av `Get-Date` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="cfe3b-137">This example uses `Update-TypeData` to add the **Quarter** script property to **System.DateTime** objects in the current session, such as those returned by the `Get-Date` cmdlet.</span></span>

```powershell
Update-TypeData -TypeName "System.DateTime" -MemberType ScriptProperty -MemberName "Quarter" -Value {
  if ($this.Month -in @(1,2,3)) {"Q1"}
  elseif ($this.Month -in @(4,5,6)) {"Q2"}
  elseif ($this.Month -in @(7,8,9)) {"Q3"}
  else {"Q4"}
}
(Get-Date).Quarter
```

```Output
Q1
```

<span data-ttu-id="cfe3b-138">`Update-TypeData`Kommandot använder parametern **TypeName** för att ange **system. DateTime** -typen, parametern **MemberName** för att ange ett namn för den nya egenskapen, egenskapen **MemberType** för att ange **ScriptProperty** -typ och **värde** parametern för att ange det skript som avgör det årliga kvartalet.</span><span class="sxs-lookup"><span data-stu-id="cfe3b-138">The `Update-TypeData` command uses the **TypeName** parameter to specify **the System.DateTime** type, the **MemberName** parameter to specify a name for the new property, the **MemberType** property to specify the **ScriptProperty** type, and the **Value** parameter to specify the script that determines the annual quarter.</span></span>

<span data-ttu-id="cfe3b-139">Värdet för egenskapen **Value** är ett skript som beräknar det aktuella årliga kvartalet.</span><span class="sxs-lookup"><span data-stu-id="cfe3b-139">The value of the **Value** property is a script that calculates the current annual quarter.</span></span> <span data-ttu-id="cfe3b-140">-Skript blocket använder den `$this` automatiska variabeln för att representera den aktuella instansen av objektet och operatorn i för att avgöra om månad svärdet visas i varje heltals mat ris.</span><span class="sxs-lookup"><span data-stu-id="cfe3b-140">The script block uses the `$this` automatic variable to represent the current instance of the object and the In operator to determine whether the month value appears in each integer array.</span></span> <span data-ttu-id="cfe3b-141">Mer information om `-in` operatorn finns i [about_Comparison_Operators](../Microsoft.PowerShell.Core/about/about_Comparison_Operators.md).</span><span class="sxs-lookup"><span data-stu-id="cfe3b-141">For more information about the `-in` operator, see [about_Comparison_Operators](../Microsoft.PowerShell.Core/about/about_Comparison_Operators.md).</span></span>

<span data-ttu-id="cfe3b-142">Det andra kommandot hämtar den nya kvartals egenskapen för det aktuella datumet.</span><span class="sxs-lookup"><span data-stu-id="cfe3b-142">The second command gets the new Quarter property of the current date.</span></span>

### <span data-ttu-id="cfe3b-143">Exempel 4: uppdatera en typ som visas i listor som standard</span><span class="sxs-lookup"><span data-stu-id="cfe3b-143">Example 4: Update a type that displays in lists by default</span></span>

<span data-ttu-id="cfe3b-144">I det här exemplet visas hur du anger egenskaperna för en typ som visas i listor som standard, det vill säga när inga egenskaper har angetts.</span><span class="sxs-lookup"><span data-stu-id="cfe3b-144">This example shows how to set the properties of a type that displays in lists by default, that is, when no properties are specified.</span></span> <span data-ttu-id="cfe3b-145">Eftersom typ data inte anges i en `Types.ps1xml` fil, är det bara effektivt i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="cfe3b-145">Because the type data is not specified in a `Types.ps1xml` file, it is effective only in the current session.</span></span>

```powershell
Update-TypeData -TypeName "System.DateTime" -DefaultDisplayPropertySet "DateTime, DayOfYear, Quarter"
Get-Date | Format-List
```

```Output
Thursday, March 15, 2012 12:00:00 AM
DayOfYear : 75
Quarter   : Q1
```

<span data-ttu-id="cfe3b-146">Det första kommandot använder `Update-TypeData` cmdleten för att ange standard List egenskaperna för **system. DateTime** -typen.</span><span class="sxs-lookup"><span data-stu-id="cfe3b-146">The first command uses the `Update-TypeData` cmdlet to set the default list properties for the **System.DateTime** type.</span></span> <span data-ttu-id="cfe3b-147">Kommandot använder parametern **TypeName** för att ange typ och **DefaultDisplayPropertySet** -parameter för att ange standard egenskaperna för en lista.</span><span class="sxs-lookup"><span data-stu-id="cfe3b-147">The command uses the **TypeName** parameter to specify the type and the **DefaultDisplayPropertySet** parameter to specify the default properties for a list.</span></span> <span data-ttu-id="cfe3b-148">De valda egenskaperna inkluderar den nya egenskapen för **kvartals** skript som lades till i ett tidigare exempel.</span><span class="sxs-lookup"><span data-stu-id="cfe3b-148">The selected properties include the new **Quarter** script property that was added in a previous example.</span></span>

<span data-ttu-id="cfe3b-149">Det andra kommandot använder `Get-Date` cmdleten för att hämta ett **system. DateTime** -objekt som representerar det aktuella datumet.</span><span class="sxs-lookup"><span data-stu-id="cfe3b-149">The second command uses the `Get-Date` cmdlet to get a **System.DateTime** object that represents the current date.</span></span> <span data-ttu-id="cfe3b-150">Kommandot använder en pipeline-operator ( `|` ) för att skicka **datetime** -objektet till `Format-List` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="cfe3b-150">The command uses a pipeline operator (`|`) to send the **DateTime** object to the `Format-List` cmdlet.</span></span> <span data-ttu-id="cfe3b-151">Eftersom `Format-List` kommandot inte anger vilka egenskaper som ska visas i listan, använder PowerShell standardvärdena som upprättats av `Update-TypeData` kommandot.</span><span class="sxs-lookup"><span data-stu-id="cfe3b-151">Because the `Format-List` command does not specify the properties to display in the list, PowerShell uses the default values that were established by the `Update-TypeData` command.</span></span>

### <span data-ttu-id="cfe3b-152">Exempel 5: uppdatera typ data för ett skickas-objekt</span><span class="sxs-lookup"><span data-stu-id="cfe3b-152">Example 5: Update type data for a piped object</span></span>

```powershell
Get-Module | Update-TypeData -MemberType ScriptProperty -MemberName "SupportsUpdatableHelp" -Value {
  if ($this.HelpInfoUri) {$True} else {$False}
}
Get-Module -ListAvailable | Format-Table Name, SupportsUpdatableHelp
```

```Output
Name                             SupportsUpdatableHelp
----                             ---------------------
Microsoft.PowerShell.Diagnostics                  True
Microsoft.PowerShell.Host                         True
Microsoft.PowerShell.Management                   True
Microsoft.PowerShell.Security                     True
Microsoft.PowerShell.Utility                      True
Microsoft.WSMan.Management                        True
PSDiagnostics                                    False
PSScheduledJob                                    True
PSWorkflow                                        True
ServerManager                                     True
TroubleshootingPack                              False
```

<span data-ttu-id="cfe3b-153">Det här exemplet visar att när du lägger till ett objekt i `Update-TypeData` `Update-TypeData` lägger till utökade typ data för objekt typen.</span><span class="sxs-lookup"><span data-stu-id="cfe3b-153">This example demonstrates that when you pipe an object to `Update-TypeData`, `Update-TypeData` adds extended type data for the object type.</span></span>

<span data-ttu-id="cfe3b-154">Den här tekniken går snabbare än att använda- `Get-Member` cmdleten eller `Get-Type` metoden för att hämta objekt typen.</span><span class="sxs-lookup"><span data-stu-id="cfe3b-154">This technique is quicker than using the `Get-Member` cmdlet or the `Get-Type` method to get the object type.</span></span> <span data-ttu-id="cfe3b-155">Men om du skickar en samling objekt till `Update-TypeData` , uppdaterar den typ data för den första objekt typen och returnerar sedan ett fel för alla andra objekt i samlingen eftersom medlemmen redan har definierats för typen.</span><span class="sxs-lookup"><span data-stu-id="cfe3b-155">However, if you pipe a collection of objects to `Update-TypeData`, it updates the type data of the first object type and then returns an error for all other objects in the collection because the member is already defined on the type.</span></span>

<span data-ttu-id="cfe3b-156">Det första kommandot använder `Get-Module` cmdleten för att hämta PSScheduledJob-modulen.</span><span class="sxs-lookup"><span data-stu-id="cfe3b-156">The first command uses the `Get-Module` cmdlet to get the PSScheduledJob module.</span></span> <span data-ttu-id="cfe3b-157">Kommandot rör objektet module till `Update-TypeData` cmdleten, som uppdaterar typ data för typen **system. Management. Automation. PSModuleInfo** och de typer som härleds från den, till exempel den ModuleInfoGrouping-typ som `Get-Module` returneras när du använder parametern **ListAvailable** i kommandot.</span><span class="sxs-lookup"><span data-stu-id="cfe3b-157">The command pipes the module object to the `Update-TypeData` cmdlet, which updates the type data for the **System.Management.Automation.PSModuleInfo** type and the types derived from it, such as the ModuleInfoGrouping type that `Get-Module` returns when you use the **ListAvailable** parameter in the command.</span></span>

<span data-ttu-id="cfe3b-158">`Update-TypeData`Kommandona lägger till skript egenskapen **SupportsUpdatableHelp** i alla importerade moduler.</span><span class="sxs-lookup"><span data-stu-id="cfe3b-158">The `Update-TypeData` commands adds the **SupportsUpdatableHelp** script property to all imported modules.</span></span> <span data-ttu-id="cfe3b-159">Värdet för **Value** -parametern är ett skript som returnerar `$True` om egenskapen **HelpInfoUri** för modulen är ifylld och `$False` annars.</span><span class="sxs-lookup"><span data-stu-id="cfe3b-159">The value of the **Value** parameter is a script that returns `$True` if the **HelpInfoUri** property of the module is populated and `$False` otherwise.</span></span>

<span data-ttu-id="cfe3b-160">Det andra kommandot rör modul-objekten från `Get-Module` till `Format-Table` cmdleten, som visar **namn** -och **SupportsUpdatableHelp** -egenskaperna för alla moduler i en lista.</span><span class="sxs-lookup"><span data-stu-id="cfe3b-160">The second command pipes the module objects from `Get-Module` to the `Format-Table` cmdlet, which displays the **Name** and **SupportsUpdatableHelp** properties of all modules in a list.</span></span>

## <span data-ttu-id="cfe3b-161">Parametrar</span><span class="sxs-lookup"><span data-stu-id="cfe3b-161">Parameters</span></span>

### <span data-ttu-id="cfe3b-162">-AppendPath</span><span class="sxs-lookup"><span data-stu-id="cfe3b-162">-AppendPath</span></span>

<span data-ttu-id="cfe3b-163">Anger sökvägen till valfria `.ps1xml` filer.</span><span class="sxs-lookup"><span data-stu-id="cfe3b-163">Specifies the path to optional `.ps1xml` files.</span></span> <span data-ttu-id="cfe3b-164">De angivna filerna läses in i den ordning som de anges efter att de inbyggda filerna har lästs in.</span><span class="sxs-lookup"><span data-stu-id="cfe3b-164">The specified files are loaded in the order that they are listed after the built-in files are loaded.</span></span> <span data-ttu-id="cfe3b-165">Du kan också skicka ett **AppendPath** -värde till `Update-TypeData` .</span><span class="sxs-lookup"><span data-stu-id="cfe3b-165">You can also pipe an **AppendPath** value to `Update-TypeData`.</span></span>

```yaml
Type: System.String[]
Parameter Sets: FileSet
Aliases: PSPath, Path

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="cfe3b-166">-DefaultDisplayProperty</span><span class="sxs-lookup"><span data-stu-id="cfe3b-166">-DefaultDisplayProperty</span></span>

<span data-ttu-id="cfe3b-167">Anger egenskapen för den typ som visas av `Format-Wide` cmdleten när inga andra egenskaper har angetts.</span><span class="sxs-lookup"><span data-stu-id="cfe3b-167">Specifies the property of the type that is displayed by the `Format-Wide` cmdlet when no other properties are specified.</span></span>

<span data-ttu-id="cfe3b-168">Ange namnet på en standard egenskap eller utökad egenskap av typen.</span><span class="sxs-lookup"><span data-stu-id="cfe3b-168">Type the name of a standard or extended property of the type.</span></span> <span data-ttu-id="cfe3b-169">Värdet för den här parametern kan vara namnet på en typ som läggs till i samma kommando.</span><span class="sxs-lookup"><span data-stu-id="cfe3b-169">The value of this parameter can be the name of a type that is added in the same command.</span></span>

<span data-ttu-id="cfe3b-170">Det här värdet gäller endast när det inte finns några egna vyer definierade för typen i en `Format.ps1xml` fil.</span><span class="sxs-lookup"><span data-stu-id="cfe3b-170">This value is effective only when there are no wide views defined for the type in a `Format.ps1xml` file.</span></span>

<span data-ttu-id="cfe3b-171">Den här parametern introducerades i Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="cfe3b-171">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.String
Parameter Sets: DynamicTypeSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="cfe3b-172">-DefaultDisplayPropertySet</span><span class="sxs-lookup"><span data-stu-id="cfe3b-172">-DefaultDisplayPropertySet</span></span>

<span data-ttu-id="cfe3b-173">Anger en eller flera egenskaper av typen.</span><span class="sxs-lookup"><span data-stu-id="cfe3b-173">Specifies one or more properties of the type.</span></span> <span data-ttu-id="cfe3b-174">Dessa egenskaper visas av `Format-List` cmdleten om inga andra egenskaper anges.</span><span class="sxs-lookup"><span data-stu-id="cfe3b-174">These properties are displayed by the `Format-List` cmdlet when no other properties are specified.</span></span>

<span data-ttu-id="cfe3b-175">Skriv namnen på standard egenskaper eller utökade egenskaper av typen.</span><span class="sxs-lookup"><span data-stu-id="cfe3b-175">Type the names of standard or extended properties of the type.</span></span> <span data-ttu-id="cfe3b-176">Värdet för den här parametern kan vara namnen på de typer som läggs till i samma kommando.</span><span class="sxs-lookup"><span data-stu-id="cfe3b-176">The value of this parameter can be the names of types that are added in the same command.</span></span>

<span data-ttu-id="cfe3b-177">Det här värdet gäller endast när det inte finns några definierade listvyer för typen i en `Format.ps1xml` fil.</span><span class="sxs-lookup"><span data-stu-id="cfe3b-177">This value is effective only when there are no list views defined for the type in a `Format.ps1xml` file.</span></span>

<span data-ttu-id="cfe3b-178">Den här parametern introducerades i Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="cfe3b-178">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.String[]
Parameter Sets: DynamicTypeSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="cfe3b-179">-DefaultKeyPropertySet</span><span class="sxs-lookup"><span data-stu-id="cfe3b-179">-DefaultKeyPropertySet</span></span>

<span data-ttu-id="cfe3b-180">Anger en eller flera egenskaper av typen.</span><span class="sxs-lookup"><span data-stu-id="cfe3b-180">Specifies one or more properties of the type.</span></span> <span data-ttu-id="cfe3b-181">Dessa egenskaper används av `Group-Object` `Sort-Object` cmdletarna och när inga andra egenskaper anges.</span><span class="sxs-lookup"><span data-stu-id="cfe3b-181">These properties are used by the `Group-Object` and `Sort-Object` cmdlets when no other properties are specified.</span></span>

<span data-ttu-id="cfe3b-182">Skriv namnen på standard egenskaper eller utökade egenskaper av typen.</span><span class="sxs-lookup"><span data-stu-id="cfe3b-182">Type the names of standard or extended properties of the type.</span></span> <span data-ttu-id="cfe3b-183">Värdet för den här parametern kan vara namnen på de typer som läggs till i samma kommando.</span><span class="sxs-lookup"><span data-stu-id="cfe3b-183">The value of this parameter can be the names of types that are added in the same command.</span></span>

<span data-ttu-id="cfe3b-184">Den här parametern introducerades i Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="cfe3b-184">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.String[]
Parameter Sets: DynamicTypeSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="cfe3b-185">-Force</span><span class="sxs-lookup"><span data-stu-id="cfe3b-185">-Force</span></span>

<span data-ttu-id="cfe3b-186">Anger att cmdleten använder de angivna data typerna, även om typ data redan har angetts för den typen.</span><span class="sxs-lookup"><span data-stu-id="cfe3b-186">Indicates that the cmdlet uses the specified type data, even if type data has already been specified for that type.</span></span>

<span data-ttu-id="cfe3b-187">Den här parametern introducerades i Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="cfe3b-187">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: DynamicTypeSet, TypeDataSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="cfe3b-188">-InheritPropertySerializationSet</span><span class="sxs-lookup"><span data-stu-id="cfe3b-188">-InheritPropertySerializationSet</span></span>

<span data-ttu-id="cfe3b-189">Anger om uppsättningen med egenskaper som är serialiserad ärvs.</span><span class="sxs-lookup"><span data-stu-id="cfe3b-189">Indicates whether the set of properties that are serialized is inherited.</span></span> <span data-ttu-id="cfe3b-190">Standardvärdet är `$Null`.</span><span class="sxs-lookup"><span data-stu-id="cfe3b-190">The default value is `$Null`.</span></span> <span data-ttu-id="cfe3b-191">De acceptabla värdena för den här parametern är:</span><span class="sxs-lookup"><span data-stu-id="cfe3b-191">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="cfe3b-192">`$True`.</span><span class="sxs-lookup"><span data-stu-id="cfe3b-192">`$True`.</span></span> <span data-ttu-id="cfe3b-193">Egenskaps uppsättningen ärvs.</span><span class="sxs-lookup"><span data-stu-id="cfe3b-193">The property set is inherited.</span></span>
- <span data-ttu-id="cfe3b-194">`$False`.</span><span class="sxs-lookup"><span data-stu-id="cfe3b-194">`$False`.</span></span> <span data-ttu-id="cfe3b-195">Egenskaps uppsättningen ärvs inte.</span><span class="sxs-lookup"><span data-stu-id="cfe3b-195">The property set is not inherited.</span></span>
- <span data-ttu-id="cfe3b-196">`$Null`.</span><span class="sxs-lookup"><span data-stu-id="cfe3b-196">`$Null`.</span></span> <span data-ttu-id="cfe3b-197">Arv har inte definierats.</span><span class="sxs-lookup"><span data-stu-id="cfe3b-197">Inheritance is not defined.</span></span>

<span data-ttu-id="cfe3b-198">Den här parametern är endast giltig när värdet för parametern **metoden serializationmethod** är `SpecificProperties` .</span><span class="sxs-lookup"><span data-stu-id="cfe3b-198">This parameter is valid only when the value of the **SerializationMethod** parameter is `SpecificProperties`.</span></span> <span data-ttu-id="cfe3b-199">När värdet för den här parametern är måste `$False` parametern **PropertySerializationSet** anges.</span><span class="sxs-lookup"><span data-stu-id="cfe3b-199">When the value of this parameter is `$False`, the **PropertySerializationSet** parameter is required.</span></span>

<span data-ttu-id="cfe3b-200">Den här parametern introducerades i Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="cfe3b-200">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Nullable`1[System.Boolean]
Parameter Sets: DynamicTypeSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="cfe3b-201">– MemberName</span><span class="sxs-lookup"><span data-stu-id="cfe3b-201">-MemberName</span></span>

<span data-ttu-id="cfe3b-202">Anger namnet på en egenskap eller metod.</span><span class="sxs-lookup"><span data-stu-id="cfe3b-202">Specifies the name of a property or method.</span></span>

<span data-ttu-id="cfe3b-203">Använd den här parametern med parametrarna **TypeName** , **MemberType** , **Value** och **SecondValue** för att lägga till eller ändra en egenskap eller metod för en typ.</span><span class="sxs-lookup"><span data-stu-id="cfe3b-203">Use this parameter with the **TypeName** , **MemberType** , **Value** and **SecondValue** parameters to add or change a property or method of a type.</span></span>

<span data-ttu-id="cfe3b-204">Den här parametern introducerades i Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="cfe3b-204">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.String
Parameter Sets: DynamicTypeSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="cfe3b-205">– MemberType</span><span class="sxs-lookup"><span data-stu-id="cfe3b-205">-MemberType</span></span>

<span data-ttu-id="cfe3b-206">Anger vilken typ av medlem som ska läggas till eller ändras.</span><span class="sxs-lookup"><span data-stu-id="cfe3b-206">Specifies the type of the member to add or change.</span></span>

<span data-ttu-id="cfe3b-207">Använd den här parametern med parametrarna **TypeName** , **MemberType** , **Value** och **SecondValue** för att lägga till eller ändra en egenskap eller metod för en typ.</span><span class="sxs-lookup"><span data-stu-id="cfe3b-207">Use this parameter with the **TypeName** , **MemberType** , **Value** and **SecondValue** parameters to add or change a property or method of a type.</span></span> <span data-ttu-id="cfe3b-208">De acceptabla värdena för den här parametern är:</span><span class="sxs-lookup"><span data-stu-id="cfe3b-208">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="cfe3b-209">AliasProperty</span><span class="sxs-lookup"><span data-stu-id="cfe3b-209">AliasProperty</span></span>
- <span data-ttu-id="cfe3b-210">CodeMethod</span><span class="sxs-lookup"><span data-stu-id="cfe3b-210">CodeMethod</span></span>
- <span data-ttu-id="cfe3b-211">CodeProperty</span><span class="sxs-lookup"><span data-stu-id="cfe3b-211">CodeProperty</span></span>
- <span data-ttu-id="cfe3b-212">Noteproperty</span><span class="sxs-lookup"><span data-stu-id="cfe3b-212">Noteproperty</span></span>
- <span data-ttu-id="cfe3b-213">ScriptMethod</span><span class="sxs-lookup"><span data-stu-id="cfe3b-213">ScriptMethod</span></span>
- <span data-ttu-id="cfe3b-214">ScriptProperty</span><span class="sxs-lookup"><span data-stu-id="cfe3b-214">ScriptProperty</span></span>

<span data-ttu-id="cfe3b-215">Information om dessa värden finns i [PSMemberTypes-uppräkning](/dotnet/api/system.management.automation.psmembertypes).</span><span class="sxs-lookup"><span data-stu-id="cfe3b-215">For information about these values, see [PSMemberTypes Enumeration](/dotnet/api/system.management.automation.psmembertypes).</span></span>

<span data-ttu-id="cfe3b-216">Den här parametern introducerades i Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="cfe3b-216">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.PSMemberTypes
Parameter Sets: DynamicTypeSet
Aliases:
Accepted values: NoteProperty, AliasProperty, ScriptProperty, CodeProperty, ScriptMethod, CodeMethod

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="cfe3b-217">-PrependPath</span><span class="sxs-lookup"><span data-stu-id="cfe3b-217">-PrependPath</span></span>

<span data-ttu-id="cfe3b-218">Anger sökvägen till de valfria `.ps1xml` filerna.</span><span class="sxs-lookup"><span data-stu-id="cfe3b-218">Specifies the path to the optional `.ps1xml` files.</span></span> <span data-ttu-id="cfe3b-219">De angivna filerna läses in i den ordning som de anges innan de inbyggda filerna läses in.</span><span class="sxs-lookup"><span data-stu-id="cfe3b-219">The specified files are loaded in the order that they are listed before the built-in files are loaded.</span></span>

```yaml
Type: System.String[]
Parameter Sets: FileSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="cfe3b-220">-PropertySerializationSet</span><span class="sxs-lookup"><span data-stu-id="cfe3b-220">-PropertySerializationSet</span></span>

<span data-ttu-id="cfe3b-221">Anger namn på egenskaper som är serialiserade.</span><span class="sxs-lookup"><span data-stu-id="cfe3b-221">Specifies the names of properties that are serialized.</span></span> <span data-ttu-id="cfe3b-222">Använd den här parametern när värdet för parametern **metoden serializationmethod** är **SpecificProperties**.</span><span class="sxs-lookup"><span data-stu-id="cfe3b-222">Use this parameter when the value of the **SerializationMethod** parameter is **SpecificProperties**.</span></span>

```yaml
Type: System.String[]
Parameter Sets: DynamicTypeSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="cfe3b-223">-SecondValue</span><span class="sxs-lookup"><span data-stu-id="cfe3b-223">-SecondValue</span></span>

<span data-ttu-id="cfe3b-224">Anger ytterligare värden för **AliasProperty** -, **ScriptProperty** -, **CodeProperty** -eller **CodeMethod** -medlemmar.</span><span class="sxs-lookup"><span data-stu-id="cfe3b-224">Specifies additional values for **AliasProperty** , **ScriptProperty** , **CodeProperty** , or **CodeMethod** members.</span></span>

<span data-ttu-id="cfe3b-225">Använd den här parametern med parametrarna **TypeName** , **MemberType** , **Value** och **SecondValue** för att lägga till eller ändra en egenskap eller metod för en typ.</span><span class="sxs-lookup"><span data-stu-id="cfe3b-225">Use this parameter with the **TypeName** , **MemberType** , **Value** , and **SecondValue** parameters to add or change a property or method of a type.</span></span>

<span data-ttu-id="cfe3b-226">När värdet för parametern **MemberType** är `AliasProperty` måste värdet för parametern **SecondValue** vara av data typen.</span><span class="sxs-lookup"><span data-stu-id="cfe3b-226">When the value of the **MemberType** parameter is `AliasProperty`, the value of the **SecondValue** parameter must be a data type.</span></span> <span data-ttu-id="cfe3b-227">PowerShell konverterar (dvs. casts) värdet för egenskapen alias till den angivna typen.</span><span class="sxs-lookup"><span data-stu-id="cfe3b-227">PowerShell converts (that is, casts) the value of the alias property to the specified type.</span></span> <span data-ttu-id="cfe3b-228">Om du till exempel lägger till en aliasresurspost som ger ett alternativt namn för en sträng egenskap, kan du även ange en **SecondValue** för **system. Int32** för att konvertera det aliasna sträng svärdet till ett heltal.</span><span class="sxs-lookup"><span data-stu-id="cfe3b-228">For example, if you add an alias property that provides an alternate name for a string property, you can also specify a **SecondValue** of **System.Int32** to convert the aliased string value to an integer.</span></span>

<span data-ttu-id="cfe3b-229">När värdet för parametern **MemberType** är `ScriptProperty` kan du använda parametern **SecondValue** för att ange ytterligare ett skript block.</span><span class="sxs-lookup"><span data-stu-id="cfe3b-229">When the value of the **MemberType** parameter is `ScriptProperty`, you can use the **SecondValue** parameter to specify an additional script block.</span></span> <span data-ttu-id="cfe3b-230">Skript blocket i värdet för parametern **Value** hämtar värdet för en variabel.</span><span class="sxs-lookup"><span data-stu-id="cfe3b-230">The script block in the value of the **Value** parameter gets the value of a variable.</span></span> <span data-ttu-id="cfe3b-231">Skript blocket i värdet för parametern **SecondValue** anger värdet för variabeln.</span><span class="sxs-lookup"><span data-stu-id="cfe3b-231">The script block in the value of the **SecondValue** parameter set the value of the variable.</span></span>

<span data-ttu-id="cfe3b-232">Den här parametern introducerades i Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="cfe3b-232">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Object
Parameter Sets: DynamicTypeSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="cfe3b-233">-SerializationDepth</span><span class="sxs-lookup"><span data-stu-id="cfe3b-233">-SerializationDepth</span></span>

<span data-ttu-id="cfe3b-234">Anger hur många nivåer av typ objekt som serialiseras som strängar.</span><span class="sxs-lookup"><span data-stu-id="cfe3b-234">Specifies how many levels of type objects are serialized as strings.</span></span> <span data-ttu-id="cfe3b-235">Standardvärdet `1` serialiserar objektet och dess egenskaper.</span><span class="sxs-lookup"><span data-stu-id="cfe3b-235">The default value `1` serializes the object and its properties.</span></span> <span data-ttu-id="cfe3b-236">Värdet `0` serialiserar objektet, men inte dess egenskaper.</span><span class="sxs-lookup"><span data-stu-id="cfe3b-236">A value of `0` serializes the object, but not its properties.</span></span> <span data-ttu-id="cfe3b-237">Värdet `2` serialiserar objektet, dess egenskaper och alla objekt i egenskaps värden.</span><span class="sxs-lookup"><span data-stu-id="cfe3b-237">A value of `2` serializes the object, its properties, and any objects in property values.</span></span>

<span data-ttu-id="cfe3b-238">Den här parametern introducerades i Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="cfe3b-238">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Int32
Parameter Sets: DynamicTypeSet
Aliases:

Required: False
Position: Named
Default value: 1
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="cfe3b-239">– Metoden serializationmethod</span><span class="sxs-lookup"><span data-stu-id="cfe3b-239">-SerializationMethod</span></span>

<span data-ttu-id="cfe3b-240">Anger en serialiserings metod för typen.</span><span class="sxs-lookup"><span data-stu-id="cfe3b-240">Specifies a serialization method for the type.</span></span> <span data-ttu-id="cfe3b-241">En serialiserings metod avgör vilka egenskaper av typen som serialiseras och den teknik som används för att serialisera dem.</span><span class="sxs-lookup"><span data-stu-id="cfe3b-241">A serialization method determines which properties of the type are serialized and the technique that is used to serialize them.</span></span> <span data-ttu-id="cfe3b-242">De acceptabla värdena för den här parametern är:</span><span class="sxs-lookup"><span data-stu-id="cfe3b-242">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="cfe3b-243">`AllPublicProperties`.</span><span class="sxs-lookup"><span data-stu-id="cfe3b-243">`AllPublicProperties`.</span></span> <span data-ttu-id="cfe3b-244">Serialisera alla offentliga egenskaper av typen.</span><span class="sxs-lookup"><span data-stu-id="cfe3b-244">Serialize all public properties of the type.</span></span> <span data-ttu-id="cfe3b-245">Du kan använda parametern **SerializationDepth** för att avgöra om underordnade egenskaper är serialiserade.</span><span class="sxs-lookup"><span data-stu-id="cfe3b-245">You can use the **SerializationDepth** parameter to determine whether child properties are serialized.</span></span>
- <span data-ttu-id="cfe3b-246">`String`.</span><span class="sxs-lookup"><span data-stu-id="cfe3b-246">`String`.</span></span> <span data-ttu-id="cfe3b-247">Serialisera typen som en sträng.</span><span class="sxs-lookup"><span data-stu-id="cfe3b-247">Serialize the type as a string.</span></span> <span data-ttu-id="cfe3b-248">Du kan använda **StringSerializationSource** för att ange en egenskap av typen som ska användas som serialiserings resultat.</span><span class="sxs-lookup"><span data-stu-id="cfe3b-248">You can use the **StringSerializationSource** to specify a property of the type to use as the serialization result.</span></span> <span data-ttu-id="cfe3b-249">Annars serialiseras typen med hjälp av objektets **toString** -metod.</span><span class="sxs-lookup"><span data-stu-id="cfe3b-249">Otherwise, the type is serialized by using the **ToString** method of the object.</span></span>
- <span data-ttu-id="cfe3b-250">`SpecificProperties`.</span><span class="sxs-lookup"><span data-stu-id="cfe3b-250">`SpecificProperties`.</span></span> <span data-ttu-id="cfe3b-251">Serialisera endast de angivna egenskaperna av den här typen.</span><span class="sxs-lookup"><span data-stu-id="cfe3b-251">Serialize only the specified properties of this type.</span></span> <span data-ttu-id="cfe3b-252">Använd parametern **PropertySerializationSet** för att ange egenskaperna för den typ som serialiseras.</span><span class="sxs-lookup"><span data-stu-id="cfe3b-252">Use the **PropertySerializationSet** parameter to specify the properties of the type that are serialized.</span></span>
  <span data-ttu-id="cfe3b-253">Du kan också använda parametern **InheritPropertySerializationSet** för att avgöra om egenskaps uppsättningen ärvs och parametern **SerializationDepth** för att avgöra om underordnade egenskaper är serialiserade.</span><span class="sxs-lookup"><span data-stu-id="cfe3b-253">You can also use the **InheritPropertySerializationSet** parameter to determine whether the property set is inherited and the **SerializationDepth** parameter to determine whether child properties are serialized.</span></span>

<span data-ttu-id="cfe3b-254">I PowerShell lagras serialiserings metoder i **PSStandardMembers** interna objekt.</span><span class="sxs-lookup"><span data-stu-id="cfe3b-254">In PowerShell, serialization methods are stored in **PSStandardMembers** internal objects.</span></span>

<span data-ttu-id="cfe3b-255">Den här parametern introducerades i Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="cfe3b-255">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.String
Parameter Sets: DynamicTypeSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="cfe3b-256">-StringSerializationSource</span><span class="sxs-lookup"><span data-stu-id="cfe3b-256">-StringSerializationSource</span></span>

<span data-ttu-id="cfe3b-257">Anger namnet på en egenskap av typen.</span><span class="sxs-lookup"><span data-stu-id="cfe3b-257">Specifies the name of a property of the type.</span></span> <span data-ttu-id="cfe3b-258">Värdet för den angivna egenskapen används som serialiserings resultat.</span><span class="sxs-lookup"><span data-stu-id="cfe3b-258">The value of specified property is used as the serialization result.</span></span> <span data-ttu-id="cfe3b-259">Den här parametern är endast giltig när värdet för parametern **metoden serializationmethod** är String.</span><span class="sxs-lookup"><span data-stu-id="cfe3b-259">This parameter is valid only when the value of the **SerializationMethod** parameter is String.</span></span>

```yaml
Type: System.String
Parameter Sets: DynamicTypeSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="cfe3b-260">-TargetTypeForDeserialization</span><span class="sxs-lookup"><span data-stu-id="cfe3b-260">-TargetTypeForDeserialization</span></span>

<span data-ttu-id="cfe3b-261">Anger vilken typ av objekt av den här typen som ska konverteras när de deserialiseras.</span><span class="sxs-lookup"><span data-stu-id="cfe3b-261">Specifies the type to which object of this type are converted when they are deserialized.</span></span>

<span data-ttu-id="cfe3b-262">Den här parametern introducerades i Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="cfe3b-262">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Type
Parameter Sets: DynamicTypeSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="cfe3b-263">-TypeAdapter</span><span class="sxs-lookup"><span data-stu-id="cfe3b-263">-TypeAdapter</span></span>

<span data-ttu-id="cfe3b-264">Anger typ av nätverkskort, till exempel **Microsoft. PowerShell. CIM. CimInstanceAdapter**.</span><span class="sxs-lookup"><span data-stu-id="cfe3b-264">Specifies the type of a type adapter, such as **Microsoft.PowerShell.Cim.CimInstanceAdapter**.</span></span> <span data-ttu-id="cfe3b-265">Med ett typ kort kan PowerShell Hämta medlemmar av en typ.</span><span class="sxs-lookup"><span data-stu-id="cfe3b-265">A type adapter enables PowerShell to get the members of a type.</span></span>

<span data-ttu-id="cfe3b-266">Den här parametern introducerades i Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="cfe3b-266">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Type
Parameter Sets: DynamicTypeSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="cfe3b-267">– TypeConverter</span><span class="sxs-lookup"><span data-stu-id="cfe3b-267">-TypeConverter</span></span>

<span data-ttu-id="cfe3b-268">Anger en typ konverterare för att konvertera värden mellan olika typer.</span><span class="sxs-lookup"><span data-stu-id="cfe3b-268">Specifies a type converter to convert values between different types.</span></span> <span data-ttu-id="cfe3b-269">Om en typ konverterare har definierats för en typ används en instans av typ konverteraren för konverteringen.</span><span class="sxs-lookup"><span data-stu-id="cfe3b-269">If a type converter is defined for a type, an instance of the type converter is used for the conversion.</span></span>

<span data-ttu-id="cfe3b-270">Ange ett **system. Type** -värde som härleds från klassen **system. ComponentModel. TypeConverter** eller **system. Management. Automation. PSTypeConverter** .</span><span class="sxs-lookup"><span data-stu-id="cfe3b-270">Enter a **System.Type** value that is derived from the **System.ComponentModel.TypeConverter** or **System.Management.Automation.PSTypeConverter** classes.</span></span>

<span data-ttu-id="cfe3b-271">Den här parametern introducerades i Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="cfe3b-271">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Type
Parameter Sets: DynamicTypeSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="cfe3b-272">-TypeData</span><span class="sxs-lookup"><span data-stu-id="cfe3b-272">-TypeData</span></span>

<span data-ttu-id="cfe3b-273">Anger en matris av typ data som denna cmdlet lägger till i sessionen.</span><span class="sxs-lookup"><span data-stu-id="cfe3b-273">Specifies an array of type data that this cmdlet adds to the session.</span></span> <span data-ttu-id="cfe3b-274">Ange en variabel som innehåller ett **TypeData** -objekt eller ett kommando som hämtar ett **TypeData** -objekt, t `Get-TypeData` . ex. ett kommando.</span><span class="sxs-lookup"><span data-stu-id="cfe3b-274">Enter a variable that contains a **TypeData** object or a command that gets a **TypeData** object, such as a `Get-TypeData` command.</span></span> <span data-ttu-id="cfe3b-275">Du kan också skicka ett **TypeData** -objekt till `Update-TypeData` .</span><span class="sxs-lookup"><span data-stu-id="cfe3b-275">You can also pipe a **TypeData** object to `Update-TypeData`.</span></span>

<span data-ttu-id="cfe3b-276">Den här parametern introducerades i Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="cfe3b-276">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.Runspaces.TypeData[]
Parameter Sets: TypeDataSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="cfe3b-277">-TypeName</span><span class="sxs-lookup"><span data-stu-id="cfe3b-277">-TypeName</span></span>

<span data-ttu-id="cfe3b-278">Anger namnet på den typ som ska utökas.</span><span class="sxs-lookup"><span data-stu-id="cfe3b-278">Specifies the name of the type to extend.</span></span>

<span data-ttu-id="cfe3b-279">För typer i **system** namn området anger du det korta namnet.</span><span class="sxs-lookup"><span data-stu-id="cfe3b-279">For types in the **System** namespace, enter the short name.</span></span> <span data-ttu-id="cfe3b-280">Annars krävs det fullständiga typ namnet.</span><span class="sxs-lookup"><span data-stu-id="cfe3b-280">Otherwise, the full type name is required.</span></span> <span data-ttu-id="cfe3b-281">Jokertecken stöds inte.</span><span class="sxs-lookup"><span data-stu-id="cfe3b-281">Wildcards are not supported.</span></span>

<span data-ttu-id="cfe3b-282">Du kan skicka pipe-typnamn till `Update-TypeData` .</span><span class="sxs-lookup"><span data-stu-id="cfe3b-282">You can pipe type names to `Update-TypeData`.</span></span> <span data-ttu-id="cfe3b-283">När du rör ett objekt till `Update-TypeData` , `Update-TypeData` hämtar typ namnet för objektet och skriver data till objekt typen.</span><span class="sxs-lookup"><span data-stu-id="cfe3b-283">When you pipe an object to `Update-TypeData`, `Update-TypeData` gets the type name of the object and type data to the object type.</span></span>

<span data-ttu-id="cfe3b-284">Använd den här parametern med parametrarna **MemberName** , **MemberType** , **Value** och **SecondValue** för att lägga till eller ändra en egenskap eller metod för en typ.</span><span class="sxs-lookup"><span data-stu-id="cfe3b-284">Use this parameter with the **MemberName** , **MemberType** , **Value** and **SecondValue** parameters to add or change a property or method of a type.</span></span>

<span data-ttu-id="cfe3b-285">Den här parametern introducerades i Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="cfe3b-285">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.String
Parameter Sets: DynamicTypeSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="cfe3b-286">-Värde</span><span class="sxs-lookup"><span data-stu-id="cfe3b-286">-Value</span></span>

<span data-ttu-id="cfe3b-287">Anger värdet för egenskapen eller metoden.</span><span class="sxs-lookup"><span data-stu-id="cfe3b-287">Specifies the value of the property or method.</span></span>

<span data-ttu-id="cfe3b-288">Om du lägger till en `AliasProperty` , `CodeProperty` , eller- `ScriptProperty` `CodeMethod` medlem kan du använda parametern **SecondValue** för att lägga till ytterligare information.</span><span class="sxs-lookup"><span data-stu-id="cfe3b-288">If you add an `AliasProperty`, `CodeProperty`, `ScriptProperty`, or `CodeMethod` member, you can use the **SecondValue** parameter to add additional information.</span></span>

<span data-ttu-id="cfe3b-289">Använd den här parametern med parametrarna **MemberName** , **MemberType** , **Value** och **SecondValue** för att lägga till eller ändra en egenskap eller metod för en typ.</span><span class="sxs-lookup"><span data-stu-id="cfe3b-289">Use this parameter with the **MemberName** , **MemberType** , **Value** and **SecondValue** parameters to add or change a property or method of a type.</span></span>

<span data-ttu-id="cfe3b-290">Den här parametern introducerades i Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="cfe3b-290">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Object
Parameter Sets: DynamicTypeSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="cfe3b-291">-Confirm</span><span class="sxs-lookup"><span data-stu-id="cfe3b-291">-Confirm</span></span>

<span data-ttu-id="cfe3b-292">Uppmanar dig att bekräfta innan du kör cmdleten.</span><span class="sxs-lookup"><span data-stu-id="cfe3b-292">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="cfe3b-293">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="cfe3b-293">-WhatIf</span></span>

<span data-ttu-id="cfe3b-294">Visar vad som skulle hända om cmdleten kördes.</span><span class="sxs-lookup"><span data-stu-id="cfe3b-294">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="cfe3b-295">Cmdleten körs inte.</span><span class="sxs-lookup"><span data-stu-id="cfe3b-295">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="cfe3b-296">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="cfe3b-296">CommonParameters</span></span>

<span data-ttu-id="cfe3b-297">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="cfe3b-297">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="cfe3b-298">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="cfe3b-298">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="cfe3b-299">Indata</span><span class="sxs-lookup"><span data-stu-id="cfe3b-299">Inputs</span></span>

### <span data-ttu-id="cfe3b-300">System. String</span><span class="sxs-lookup"><span data-stu-id="cfe3b-300">System.String</span></span>

<span data-ttu-id="cfe3b-301">Du kan skicka vidare en sträng som innehåller värdena för parametrarna **AppendPath** , **TypeName** eller **TypeData** till `Update-TypeData` .</span><span class="sxs-lookup"><span data-stu-id="cfe3b-301">You can pipe a string that contains the values of the **AppendPath** , **TypeName** , or **TypeData** parameters to `Update-TypeData`.</span></span>

## <span data-ttu-id="cfe3b-302">Utdata</span><span class="sxs-lookup"><span data-stu-id="cfe3b-302">Outputs</span></span>

### <span data-ttu-id="cfe3b-303">Inget</span><span class="sxs-lookup"><span data-stu-id="cfe3b-303">None</span></span>

<span data-ttu-id="cfe3b-304">Denna cmdlet returnerar inga utdata.</span><span class="sxs-lookup"><span data-stu-id="cfe3b-304">This cmdlet does not return any output.</span></span>

## <span data-ttu-id="cfe3b-305">Kommentarer</span><span class="sxs-lookup"><span data-stu-id="cfe3b-305">Notes</span></span>

## <span data-ttu-id="cfe3b-306">Relaterade länkar</span><span class="sxs-lookup"><span data-stu-id="cfe3b-306">Related links</span></span>

[<span data-ttu-id="cfe3b-307">about_Types.ps1XML</span><span class="sxs-lookup"><span data-stu-id="cfe3b-307">about_Types.ps1xml</span></span>](../Microsoft.PowerShell.Core/About/about_Types.ps1xml.md)

[<span data-ttu-id="cfe3b-308">Get-TypeData</span><span class="sxs-lookup"><span data-stu-id="cfe3b-308">Get-TypeData</span></span>](Get-TypeData.md)

[<span data-ttu-id="cfe3b-309">Remove-TypeData</span><span class="sxs-lookup"><span data-stu-id="cfe3b-309">Remove-TypeData</span></span>](Remove-TypeData.md)

