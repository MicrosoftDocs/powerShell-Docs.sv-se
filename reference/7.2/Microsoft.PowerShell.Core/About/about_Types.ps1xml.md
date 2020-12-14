---
description: Förklarar hur du använder `Types.ps1xml` filer för att utöka de typer av objekt som används i PowerShell.
Locale: en-US
ms.date: 04/27/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_types.ps1xml?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Types.ps1XML
ms.openlocfilehash: 9a87394631d3318f3fb3f4b2a0cb2ab8d25408d0
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94709234"
---
# <a name="about-typesps1xml"></a><span data-ttu-id="c2bdb-103">Om Types.ps1XML</span><span class="sxs-lookup"><span data-stu-id="c2bdb-103">About Types.ps1xml</span></span>

## <a name="short-description"></a><span data-ttu-id="c2bdb-104">Kort beskrivning</span><span class="sxs-lookup"><span data-stu-id="c2bdb-104">Short description</span></span>
<span data-ttu-id="c2bdb-105">Förklarar hur du använder `Types.ps1xml` filer för att utöka de typer av objekt som används i PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c2bdb-105">Explains how to use `Types.ps1xml` files to extend the types of objects that are used in PowerShell.</span></span>

## <a name="long-description"></a><span data-ttu-id="c2bdb-106">Lång beskrivning</span><span class="sxs-lookup"><span data-stu-id="c2bdb-106">Long description</span></span>

<span data-ttu-id="c2bdb-107">Utökade typ data definierar ytterligare egenskaper och metoder ("medlemmar") för objekt typer i PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c2bdb-107">Extended type data defines additional properties and methods ("members") of object types in PowerShell.</span></span> <span data-ttu-id="c2bdb-108">Det finns två metoder för att lägga till utökade typ data till en PowerShell-session.</span><span class="sxs-lookup"><span data-stu-id="c2bdb-108">There are two techniques for adding extended type data to a PowerShell session.</span></span>

- <span data-ttu-id="c2bdb-109">`Types.ps1xml` fil: en XML-fil som definierar utökade typ data.</span><span class="sxs-lookup"><span data-stu-id="c2bdb-109">`Types.ps1xml` file: An XML file that defines extended type data.</span></span>
- <span data-ttu-id="c2bdb-110">`Update-TypeData`: En cmdlet som laddar `Types.ps1xml` om filer och definierar utökade data för typer i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="c2bdb-110">`Update-TypeData`: A cmdlet that reloads `Types.ps1xml` files and defines extended data for types in the current session.</span></span>

<span data-ttu-id="c2bdb-111">I det här avsnittet beskrivs `Types.ps1xml` filer.</span><span class="sxs-lookup"><span data-stu-id="c2bdb-111">This topic describes `Types.ps1xml` files.</span></span> <span data-ttu-id="c2bdb-112">Mer information om hur du använder `Update-TypeData` cmdleten för att lägga till dynamiska utökade typ data till den aktuella sessionen finns i [Update-TypeData](xref:Microsoft.PowerShell.Utility.Update-TypeData).</span><span class="sxs-lookup"><span data-stu-id="c2bdb-112">For more information about using the `Update-TypeData` cmdlet to add dynamic extended type data to the current session see [Update-TypeData](xref:Microsoft.PowerShell.Utility.Update-TypeData).</span></span>

## <a name="about-extended-type-data"></a><span data-ttu-id="c2bdb-113">Om utökade typ data</span><span class="sxs-lookup"><span data-stu-id="c2bdb-113">About extended type data</span></span>

<span data-ttu-id="c2bdb-114">Utökade typ data definierar ytterligare egenskaper och metoder ("medlemmar") för objekt typer i PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c2bdb-114">Extended type data defines additional properties and methods ("members") of object types in PowerShell.</span></span> <span data-ttu-id="c2bdb-115">Du kan utöka vilken typ som helst som stöds av PowerShell och använda de egenskaper och metoder som har lagts till på samma sätt som du använder de egenskaper som definierats för objekt typerna.</span><span class="sxs-lookup"><span data-stu-id="c2bdb-115">You can extend any type that is supported by PowerShell and use the added properties and methods in the same way that you use the properties that are defined on the object types.</span></span>

<span data-ttu-id="c2bdb-116">Exempelvis lägger PowerShell till en **datetime** -egenskap till alla `System.DateTime` objekt, till exempel de som `Get-Date` cmdleten returnerar.</span><span class="sxs-lookup"><span data-stu-id="c2bdb-116">For example, PowerShell adds a **DateTime** property to all `System.DateTime` objects, such as the ones that the `Get-Date` cmdlet returns.</span></span>

```powershell
(Get-Date).DateTime
```

```Output
Sunday, January 29, 2012 9:43:57 AM
```

<span data-ttu-id="c2bdb-117">Du hittar inte egenskapen **datetime** i beskrivningen av [system. DateTime](/dotnet/api/system.datetime) -strukturen eftersom PowerShell lägger till egenskapen och den är endast synlig i PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c2bdb-117">You won't find the **DateTime** property in the description of the [System.DateTime](/dotnet/api/system.datetime) structure, because PowerShell adds the property and it is visible only in PowerShell.</span></span>

<span data-ttu-id="c2bdb-118">PowerShell definierar internt en standard uppsättning av utökade typer.</span><span class="sxs-lookup"><span data-stu-id="c2bdb-118">PowerShell internally defines a default set of extended types.</span></span> <span data-ttu-id="c2bdb-119">Den här typen av information läses in i varje PowerShell-session vid start.</span><span class="sxs-lookup"><span data-stu-id="c2bdb-119">This type information is loaded in every PowerShell session at startup.</span></span> <span data-ttu-id="c2bdb-120">**Datetime** -egenskapen ingår i den här standard uppsättningen.</span><span class="sxs-lookup"><span data-stu-id="c2bdb-120">The **DateTime** property is part of this default set.</span></span> <span data-ttu-id="c2bdb-121">Före PowerShell 6 sparade typ definitionerna `Types.ps1xml` i filen i installations katalogen för PowerShell ( `$PSHOME` ).</span><span class="sxs-lookup"><span data-stu-id="c2bdb-121">Prior to PowerShell 6, the type definitions were stored the `Types.ps1xml` file in the PowerShell installation directory (`$PSHOME`).</span></span>

## <a name="adding-extended-type-data-to-powershell"></a><span data-ttu-id="c2bdb-122">Lägga till utökade typ data till PowerShell</span><span class="sxs-lookup"><span data-stu-id="c2bdb-122">Adding extended type data to PowerShell</span></span>

<span data-ttu-id="c2bdb-123">Det finns tre källor av utökade typ data i PowerShell-sessioner.</span><span class="sxs-lookup"><span data-stu-id="c2bdb-123">There are three sources of extended type data in PowerShell sessions.</span></span>

- <span data-ttu-id="c2bdb-124">Den definieras av PowerShell och läses in automatiskt i varje PowerShell-session.</span><span class="sxs-lookup"><span data-stu-id="c2bdb-124">The defined by PowerShell and is loaded automatically into every PowerShell session.</span></span> <span data-ttu-id="c2bdb-125">Från och med PowerShell 6, kompileras den här informationen till PowerShell och levereras inte längre i en `Types.ps1xml` fil.</span><span class="sxs-lookup"><span data-stu-id="c2bdb-125">Beginning with PowerShell 6, this information is compiled into PowerShell and is no longer shipped in a `Types.ps1xml` file.</span></span>

- <span data-ttu-id="c2bdb-126">`Types.ps1xml`Filerna som moduler exporterar läses in när modulen importeras till den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="c2bdb-126">The `Types.ps1xml` files that modules export are loaded when the module is imported into the current session.</span></span>

- <span data-ttu-id="c2bdb-127">Utökade typ data som definieras med hjälp av `Update-TypeData` cmdleten läggs bara till i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="c2bdb-127">Extended type data that is defined by using the `Update-TypeData` cmdlet is added only to the current session.</span></span> <span data-ttu-id="c2bdb-128">Den sparas inte i en fil.</span><span class="sxs-lookup"><span data-stu-id="c2bdb-128">It is not saved in a file.</span></span>

<span data-ttu-id="c2bdb-129">I sessionen tillämpas utökade typ data från de tre källorna på objekt på samma sätt och är tillgängliga för alla objekt av de angivna typerna.</span><span class="sxs-lookup"><span data-stu-id="c2bdb-129">In the session, the extended type data from the three sources is applied to objects in the same way and is available on all objects of the specified types.</span></span>

## <a name="the-typedata-cmdlets"></a><span data-ttu-id="c2bdb-130">TypeData-cmdletar</span><span class="sxs-lookup"><span data-stu-id="c2bdb-130">The TypeData cmdlets</span></span>

<span data-ttu-id="c2bdb-131">Följande cmdletar ingår i **Microsoft. PowerShell. Utility** -modulen i PowerShell 3,0 och senare.</span><span class="sxs-lookup"><span data-stu-id="c2bdb-131">The following cmdlets are included in the **Microsoft.PowerShell.Utility** module in PowerShell 3.0 and later.</span></span>

- <span data-ttu-id="c2bdb-132">`Get-TypeData`: Hämtar utökade typ data i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="c2bdb-132">`Get-TypeData`: Gets extended type data in the current session.</span></span>
- <span data-ttu-id="c2bdb-133">`Update-TypeData`: Filer läses in på nytt `Types.ps1xml` .</span><span class="sxs-lookup"><span data-stu-id="c2bdb-133">`Update-TypeData`: Reloads `Types.ps1xml` files.</span></span> <span data-ttu-id="c2bdb-134">Lägger till utökade typ data till den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="c2bdb-134">Adds extended type data to the current session.</span></span>
- <span data-ttu-id="c2bdb-135">`Remove-TypeData`: Tar bort utökade typ data från den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="c2bdb-135">`Remove-TypeData`: Removes extended type data from the current session.</span></span>

<span data-ttu-id="c2bdb-136">Mer information om dessa cmdlets finns i hjälp avsnittet för varje cmdlet.</span><span class="sxs-lookup"><span data-stu-id="c2bdb-136">For more information about these cmdlets, see the help topic for each cmdlet.</span></span>

## <a name="built-in-typesps1xml-files"></a><span data-ttu-id="c2bdb-137">Inbyggda Types.ps1XML-filer</span><span class="sxs-lookup"><span data-stu-id="c2bdb-137">Built-in Types.ps1xml files</span></span>

<span data-ttu-id="c2bdb-138">`Types.ps1xml`Filerna i `$PSHOME` katalogen läggs automatiskt till i varje session.</span><span class="sxs-lookup"><span data-stu-id="c2bdb-138">The `Types.ps1xml` files in the `$PSHOME` directory are added automatically to every session.</span></span>

<span data-ttu-id="c2bdb-139">`Types.ps1xml`Filen i PowerShell-installationsmappen ( `$PSHOME` ) är en XML-baserad textfil som låter dig lägga till egenskaper och metoder till de objekt som används i PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c2bdb-139">The `Types.ps1xml` file in the PowerShell installation directory (`$PSHOME`) is an XML-based text file that lets you add properties and methods to the objects that are used in PowerShell.</span></span> <span data-ttu-id="c2bdb-140">PowerShell har inbyggda `Types.ps1xml` filer som lägger till flera element i .net-typerna, men du kan skapa ytterligare `Types.ps1xml` filer för att utöka typerna ytterligare.</span><span class="sxs-lookup"><span data-stu-id="c2bdb-140">PowerShell has built-in `Types.ps1xml` files that add several elements to the .NET types, but you can create additional `Types.ps1xml` files to further extend the types.</span></span>

<span data-ttu-id="c2bdb-141">Som standard har till exempel mat ris objekt ( `System.Array` ) en **length** -egenskap som visar antalet objekt i matrisen.</span><span class="sxs-lookup"><span data-stu-id="c2bdb-141">For example, by default, array objects (`System.Array`) have a **Length** property that lists the number of objects in the array.</span></span> <span data-ttu-id="c2bdb-142">Men eftersom namn **längden** inte tydligt beskriver egenskapen, lägger PowerShell till en alias egenskap med namnet **Count** som visar samma värde.</span><span class="sxs-lookup"><span data-stu-id="c2bdb-142">However, because the name **Length** does not clearly describe the property, PowerShell adds an alias property named **Count** that displays the same value.</span></span> <span data-ttu-id="c2bdb-143">Följande XML lägger till egenskapen **Count** till `System.Array` typen.</span><span class="sxs-lookup"><span data-stu-id="c2bdb-143">The following XML adds the **Count** property to the `System.Array` type.</span></span>

```xml
<Type>
  <Name>System.Array</Name>
  <Members>
    <AliasProperty>
      <Name>Count</Name>
      <ReferencedMemberName>
        Length
      </ReferencedMemberName>
    </AliasProperty>
  </Members>
</Type>
```

<span data-ttu-id="c2bdb-144">Om du vill hämta den nya **AliasProperty** använder du ett `Get-Member` kommando på valfri matris, som du ser i följande exempel.</span><span class="sxs-lookup"><span data-stu-id="c2bdb-144">To get the new **AliasProperty**, use a `Get-Member` command on any array, as shown in the following example.</span></span>

```powershell
Get-Member -InputObject (1,2,3,4)
```

<span data-ttu-id="c2bdb-145">Kommandot returnerar följande resultat.</span><span class="sxs-lookup"><span data-stu-id="c2bdb-145">The command returns the following results.</span></span>

```Output
Name       MemberType    Definition
----       ----------    ----------
Count      AliasProperty Count = Length
Address    Method        System.Object& Address(Int32)
Clone      Method        System.Object Clone()
CopyTo     Method        System.Void CopyTo(Array array, Int32 index):
Equals     Method        System.Boolean Equals(Object obj)
Get        Method        System.Object Get(Int32)
# ...
```

<span data-ttu-id="c2bdb-146">Det innebär att du kan använda antingen **Count** -egenskapen eller **length** -egenskapen för matriser i PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c2bdb-146">As a result, you can use either the **Count** property or the **Length** property of arrays in PowerShell.</span></span> <span data-ttu-id="c2bdb-147">Exempel:</span><span class="sxs-lookup"><span data-stu-id="c2bdb-147">For example:</span></span>

```powershell
(1, 2, 3, 4).count
4
```

```powershell
(1, 2, 3, 4).length
4
```

## <a name="creating-new-typesps1xml-files"></a><span data-ttu-id="c2bdb-148">Skapa nya Types.ps1XML-filer</span><span class="sxs-lookup"><span data-stu-id="c2bdb-148">Creating new Types.ps1xml files</span></span>

<span data-ttu-id="c2bdb-149">De `.ps1xml` filer som installeras med PowerShell signeras digitalt för att förhindra manipulering eftersom formateringen kan innehålla skript block.</span><span class="sxs-lookup"><span data-stu-id="c2bdb-149">The `.ps1xml` files that are installed with PowerShell are digitally signed to prevent tampering because the formatting can include script blocks.</span></span> <span data-ttu-id="c2bdb-150">Om du vill lägga till en egenskap eller metod till en .NET-typ skapar du därför dina egna `Types.ps1xml` filer och lägger sedan till dem i PowerShell-sessionen.</span><span class="sxs-lookup"><span data-stu-id="c2bdb-150">Therefore, to add a property or method to a .NET type, create your own `Types.ps1xml` files, and then add them to your PowerShell session.</span></span>

<span data-ttu-id="c2bdb-151">Börja med att kopiera en befintlig fil för att skapa en ny fil `Types.ps1xml` .</span><span class="sxs-lookup"><span data-stu-id="c2bdb-151">To create a new file, start by copying an existing `Types.ps1xml` file.</span></span> <span data-ttu-id="c2bdb-152">Den nya filen kan ha vilket namn som helst, men den måste ha ett `.ps1xml` fil namns tillägg.</span><span class="sxs-lookup"><span data-stu-id="c2bdb-152">The new file can have any name, but it must have a `.ps1xml` file name extension.</span></span> <span data-ttu-id="c2bdb-153">Du kan placera den nya filen i valfri katalog som är tillgänglig för PowerShell, men det är användbart att placera filerna i installations katalogen för PowerShell ( `$PSHOME` ) eller i en under katalog i installations katalogen.</span><span class="sxs-lookup"><span data-stu-id="c2bdb-153">You can place the new file in any directory that is accessible to PowerShell, but it is useful to place the files in the PowerShell installation directory (`$PSHOME`) or in a subdirectory of the installation directory.</span></span>

<span data-ttu-id="c2bdb-154">När du har sparat den nya filen använder du `Update-TypeData` cmdleten för att lägga till den nya filen i PowerShell-sessionen.</span><span class="sxs-lookup"><span data-stu-id="c2bdb-154">When you have saved the new file, use the `Update-TypeData` cmdlet to add the new file to your PowerShell session.</span></span> <span data-ttu-id="c2bdb-155">Om du vill att dina typer ska prioriteras över de inbyggda typer som har definierats använder du parametern **PrependData** för `Update-TypeData` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="c2bdb-155">If you want your types to take precedence over the built-in types that are defined, use the **PrependData** parameter of the `Update-TypeData` cmdlet.</span></span> <span data-ttu-id="c2bdb-156">`Update-TypeData` påverkar endast den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="c2bdb-156">`Update-TypeData` affects only the current session.</span></span> <span data-ttu-id="c2bdb-157">Om du vill göra ändringen i alla framtida sessioner exporterar du konsolen eller lägger till `Update-TypeData` kommandot i din PowerShell-profil.</span><span class="sxs-lookup"><span data-stu-id="c2bdb-157">To make the change to all future sessions, export the console, or add the `Update-TypeData` command to your PowerShell profile.</span></span>

## <a name="typesps1xml-and-add-member"></a><span data-ttu-id="c2bdb-158">Types.ps1XML och Add-Member</span><span class="sxs-lookup"><span data-stu-id="c2bdb-158">Types.ps1xml and Add-Member</span></span>

<span data-ttu-id="c2bdb-159">`Types.ps1xml`Filerna lägger till egenskaper och metoder till alla instanser av objekten av den angivna .net-typen i den berörda PowerShell-sessionen.</span><span class="sxs-lookup"><span data-stu-id="c2bdb-159">The `Types.ps1xml` files add properties and methods to all the instances of the objects of the specified .NET type in the affected PowerShell session.</span></span> <span data-ttu-id="c2bdb-160">Men om du bara behöver lägga till egenskaper eller metoder till en instans av ett objekt, använder du `Add-Member` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="c2bdb-160">However, if you need to add properties or methods only to one instance of an object, use the `Add-Member` cmdlet.</span></span>

<span data-ttu-id="c2bdb-161">Mer information finns i avsnittet om att [lägga till medlemmar](xref:Microsoft.PowerShell.Utility.Add-Member).</span><span class="sxs-lookup"><span data-stu-id="c2bdb-161">For more information, see [Add-Member](xref:Microsoft.PowerShell.Utility.Add-Member).</span></span>

## <a name="example-adding-an-age-member-to-fileinfo-objects"></a><span data-ttu-id="c2bdb-162">Exempel: lägga till en ålders medlem i FileInfo-objekt</span><span class="sxs-lookup"><span data-stu-id="c2bdb-162">Example: Adding an Age member to FileInfo objects</span></span>

<span data-ttu-id="c2bdb-163">Det här exemplet visar hur du lägger till en **ålders** egenskap i **system. io. fileinfo** -objekt.</span><span class="sxs-lookup"><span data-stu-id="c2bdb-163">This example shows how to add an **Age** property to **System.IO.FileInfo** objects.</span></span> <span data-ttu-id="c2bdb-164">En fils ålder är skillnaden mellan tidpunkten för skapandet och den aktuella tiden i dagar.</span><span class="sxs-lookup"><span data-stu-id="c2bdb-164">The age of a file is the difference between its creation time and the current time in days.</span></span>

<span data-ttu-id="c2bdb-165">Eftersom **ålders** egenskapen beräknas med hjälp av ett-skript block, hittar du en `<ScriptProperty>` tagg som ska användas som modell för den nya **ålders** egenskapen.</span><span class="sxs-lookup"><span data-stu-id="c2bdb-165">Because the **Age** property is calculated by using a script block, find a `<ScriptProperty>` tag to use as a model for the new **Age** property.</span></span>

<span data-ttu-id="c2bdb-166">Spara följande XML-kod i filen `$PSHOME\MyTypes.ps1xml` .</span><span class="sxs-lookup"><span data-stu-id="c2bdb-166">Save the follow XML code to the file `$PSHOME\MyTypes.ps1xml`.</span></span>

```xml
<?xml version="1.0" encoding="utf-8" ?>
<Types>
  <Type>
    <Name>System.IO.FileInfo</Name>
    <Members>
      <ScriptProperty>
        <Name>Age</Name>
        <GetScriptBlock>
          ((Get-Date) - ($this.CreationTime)).Days
        </GetScriptBlock>
      </ScriptProperty>
    </Members>
  </Type>
</Types>
```

<span data-ttu-id="c2bdb-167">Kör `Update-TypeData` för att lägga till den nya `Types.ps1xml` filen i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="c2bdb-167">Run `Update-TypeData` to add the new `Types.ps1xml` file to the current session.</span></span> <span data-ttu-id="c2bdb-168">Kommandot använder parametern **PrependData** för att placera den nya filen i prioritetsordning högre än de ursprungliga definitionerna.</span><span class="sxs-lookup"><span data-stu-id="c2bdb-168">The command uses the **PrependData** parameter to place the new file in a precedence order higher than the original definitions.</span></span>

<span data-ttu-id="c2bdb-169">Mer information om `Update-TypeData` finns i [Update-TypeData](xref:Microsoft.PowerShell.Utility.Update-TypeData).</span><span class="sxs-lookup"><span data-stu-id="c2bdb-169">For more information about `Update-TypeData`, see [Update-TypeData](xref:Microsoft.PowerShell.Utility.Update-TypeData).</span></span>

```powershell
Update-Typedata -PrependPath $PSHOME\MyTypes.ps1xml
```

<span data-ttu-id="c2bdb-170">Testa ändringen genom att köra ett `Get-ChildItem` kommando för att hämta PowerShell.exe-filen i `$PSHOME` katalogen och sedan skicka filen till `Format-List` cmdleten för att visa alla egenskaper för filen.</span><span class="sxs-lookup"><span data-stu-id="c2bdb-170">To test the change, run a `Get-ChildItem` command to get the PowerShell.exe file in the `$PSHOME` directory, and then pipe the file to the `Format-List` cmdlet to list all of the properties of the file.</span></span> <span data-ttu-id="c2bdb-171">På grund av ändringen visas **ålders** egenskapen i listan.</span><span class="sxs-lookup"><span data-stu-id="c2bdb-171">As a result of the change, the **Age** property appears in the list.</span></span>

```powershell
Get-ChildItem $PSHOME\pwsh.exe | Select-Object Age
```

```Output
142
```

## <a name="the-xml-in-typesps1xml-files"></a><span data-ttu-id="c2bdb-172">XML i Types.ps1XML-filer</span><span class="sxs-lookup"><span data-stu-id="c2bdb-172">The XML in Types.ps1xml files</span></span>

<span data-ttu-id="c2bdb-173">Du hittar fullständig schema definition i [types. xsd](https://github.com/PowerShell/PowerShell/blob/master/src/Schemas/Types.xsd) i PowerShell-källkoden på GitHub.</span><span class="sxs-lookup"><span data-stu-id="c2bdb-173">The full schema definition can be found in [Types.xsd](https://github.com/PowerShell/PowerShell/blob/master/src/Schemas/Types.xsd) in the PowerShell source code repository on GitHub.</span></span>

<span data-ttu-id="c2bdb-174">`<Types>`Taggen innesluter alla typer som har definierats i filen.</span><span class="sxs-lookup"><span data-stu-id="c2bdb-174">The `<Types>` tag encloses all of the types that are defined in the file.</span></span> <span data-ttu-id="c2bdb-175">Det får bara finnas en `<Types>` tagg.</span><span class="sxs-lookup"><span data-stu-id="c2bdb-175">There should be only one `<Types>` tag.</span></span>

<span data-ttu-id="c2bdb-176">Varje .NET-typ som anges i filen ska representeras av en `<Type>` tagg.</span><span class="sxs-lookup"><span data-stu-id="c2bdb-176">Each .NET type mentioned in the file should be represented by a `<Type>` tag.</span></span>

<span data-ttu-id="c2bdb-177">Taggarna Type måste innehålla följande Taggar:</span><span class="sxs-lookup"><span data-stu-id="c2bdb-177">The type tags must contain the following tags:</span></span>

<span data-ttu-id="c2bdb-178">`<Name>`: Anger namnet på den berörda .NET-typen.</span><span class="sxs-lookup"><span data-stu-id="c2bdb-178">`<Name>`: Encloses the name of the affected .NET type.</span></span>

<span data-ttu-id="c2bdb-179">`<Members>`: Taggar för de nya egenskaper och metoder som har definierats för .NET-typen.</span><span class="sxs-lookup"><span data-stu-id="c2bdb-179">`<Members>`: Encloses the tags for the new properties and methods that are defined for the .NET type.</span></span>

<span data-ttu-id="c2bdb-180">Någon av följande medlems taggar kan finnas inuti `<Members>` taggen.</span><span class="sxs-lookup"><span data-stu-id="c2bdb-180">Any of the following member tags can be inside the `<Members>` tag.</span></span>

<span data-ttu-id="c2bdb-181">`<AliasProperty>`: Definierar ett nytt namn för en befintlig egenskap.</span><span class="sxs-lookup"><span data-stu-id="c2bdb-181">`<AliasProperty>`: Defines a new name for an existing property.</span></span>

<span data-ttu-id="c2bdb-182">`<AliasProperty>`Taggen måste ha en `<Name>` tagg som anger namnet på den nya egenskapen och en `<ReferencedMemberName>` tagg som anger den befintliga egenskapen.</span><span class="sxs-lookup"><span data-stu-id="c2bdb-182">The `<AliasProperty>` tag must have a `<Name>` tag that specifies the name of the new property and a `<ReferencedMemberName>` tag that specifies the existing property.</span></span>

<span data-ttu-id="c2bdb-183">Till exempel är **Count** -egenskapen alias ett alias för egenskapen **length** för Array-objekt.</span><span class="sxs-lookup"><span data-stu-id="c2bdb-183">For example, the **Count** alias property is an alias for the **Length** property of array objects.</span></span>

```xml
<Type>
  <Name>System.Array</Name>
  <Members>
    <AliasProperty>
      <Name>Count</Name>
      <ReferencedMemberName>Length</ReferencedMemberName>
    </AliasProperty>
  </Members>
</Type>
```

<span data-ttu-id="c2bdb-184">`<CodeMethod>`: Refererar till en statisk metod för en .NET-klass.</span><span class="sxs-lookup"><span data-stu-id="c2bdb-184">`<CodeMethod>`:  References a static method of a .NET class.</span></span>

<span data-ttu-id="c2bdb-185">`<CodeMethod>`Taggen måste ha en `<Name>` tagg som anger namnet på den nya metoden och en `<GetCodeReference>` tagg som anger koden där metoden definieras.</span><span class="sxs-lookup"><span data-stu-id="c2bdb-185">The `<CodeMethod>` tag must have a `<Name>` tag that specifies the name of the new method and a `<GetCodeReference>` tag that specifies the code in which the method is defined.</span></span>

<span data-ttu-id="c2bdb-186">Till exempel är egenskapen **mode** för `System.IO.DirectoryInfo` objekt en kod egenskap som definierats i PowerShell-fil leverantören.</span><span class="sxs-lookup"><span data-stu-id="c2bdb-186">For example, the **Mode** property of `System.IO.DirectoryInfo` objects is a code property defined in the PowerShell FileSystem provider.</span></span>

```xml
<Type>
  <Name>System.IO.DirectoryInfo</Name>
  <Members>
    <CodeProperty>
      <Name>Mode</Name>
      <GetCodeReference>
        <TypeName>
          Microsoft.PowerShell.Commands.FileSystemProvider
        </TypeName>
        <MethodName>Mode</MethodName>
      </GetCodeReference>
    </CodeProperty>
  </Members>
</Type>
```

<span data-ttu-id="c2bdb-187">`<CodeProperty>`: Refererar till en statisk metod för en .NET-klass.</span><span class="sxs-lookup"><span data-stu-id="c2bdb-187">`<CodeProperty>`: References a static method of a .NET class.</span></span>

<span data-ttu-id="c2bdb-188">`<CodeProperty>`Taggen måste ha en `<Name>` tagg som anger namnet på den nya egenskapen och en `<GetCodeReference>` tagg som anger koden där egenskapen definieras.</span><span class="sxs-lookup"><span data-stu-id="c2bdb-188">The `<CodeProperty>` tag must have a `<Name>` tag that specifies the name of the new property and a `<GetCodeReference>` tag that specifies the code in which the property is defined.</span></span>

<span data-ttu-id="c2bdb-189">Till exempel är egenskapen **mode** för `System.IO.DirectoryInfo` objekt en kod egenskap som definierats i PowerShell-fil leverantören.</span><span class="sxs-lookup"><span data-stu-id="c2bdb-189">For example, the **Mode** property of `System.IO.DirectoryInfo` objects is a code property defined in the PowerShell FileSystem provider.</span></span>

```xml
<Type>
  <Name>System.IO.DirectoryInfo</Name>
  <Members>
    <CodeProperty>
      <Name>Mode</Name>
      <GetCodeReference>
        <TypeName>
          Microsoft.PowerShell.Commands.FileSystemProvider
        </TypeName>
        <MethodName>Mode</MethodName>
      </GetCodeReference>
    </CodeProperty>
  </Members>
</Type>
```

<span data-ttu-id="c2bdb-190">`<MemberSet>`: Definierar en samling medlemmar (egenskaper och metoder).</span><span class="sxs-lookup"><span data-stu-id="c2bdb-190">`<MemberSet>`: Defines a collection of members (properties and methods).</span></span>

<span data-ttu-id="c2bdb-191">`<MemberSet>`Taggarna visas i de primära `<Members>` taggarna.</span><span class="sxs-lookup"><span data-stu-id="c2bdb-191">The `<MemberSet>` tags appear within the primary `<Members>` tags.</span></span> <span data-ttu-id="c2bdb-192">Taggarna måste omge en `<Name>` tagg som omger namnet på medlems uppsättningen och en sekundär `<Members>` tagg som omger medlemmar (egenskaper och metoder) i uppsättningen.</span><span class="sxs-lookup"><span data-stu-id="c2bdb-192">The tags must enclose a `<Name>` tag surrounding the name of the member set and a secondary `<Members>` tag that surround the members (properties and methods) in the set.</span></span> <span data-ttu-id="c2bdb-193">Alla Taggar som skapar en egenskap (till exempel `<NoteProperty>` eller `<ScriptProperty>` ) eller en metod (till exempel `<Method>` eller `<ScriptMethod>` ) kan vara medlemmar i uppsättningen.</span><span class="sxs-lookup"><span data-stu-id="c2bdb-193">Any of the tags that create a property (such as `<NoteProperty>` or `<ScriptProperty>`) or a method (such as `<Method>` or `<ScriptMethod>`) can be members of the set.</span></span>

<span data-ttu-id="c2bdb-194">I `Types.ps1xml` filer `<MemberSet>` används taggen för att definiera standardvyerna för .net-objekt i PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c2bdb-194">In `Types.ps1xml` files, the `<MemberSet>` tag is used to define the default views of the .NET objects in PowerShell.</span></span> <span data-ttu-id="c2bdb-195">I det här fallet är namnet på medlems uppsättningen (värdet i `<Name>` taggarna) alltid **PsStandardMembers** och namnen på egenskaperna (värdet för `<Name>` taggen) är något av följande:</span><span class="sxs-lookup"><span data-stu-id="c2bdb-195">In this case, the name of the member set (the value within the `<Name>` tags) is always **PsStandardMembers**, and the names of the properties (the value of the `<Name>` tag) are one of the following:</span></span>

- <span data-ttu-id="c2bdb-196">`DefaultDisplayProperty`: En enskild egenskap för ett objekt.</span><span class="sxs-lookup"><span data-stu-id="c2bdb-196">`DefaultDisplayProperty`: A single property of an object.</span></span>

- <span data-ttu-id="c2bdb-197">`DefaultDisplayPropertySet`: En eller flera egenskaper för ett objekt.</span><span class="sxs-lookup"><span data-stu-id="c2bdb-197">`DefaultDisplayPropertySet`: One or more properties of an object.</span></span>

- <span data-ttu-id="c2bdb-198">`DefaultKeyPropertySet`: En eller flera nyckel egenskaper för ett objekt.</span><span class="sxs-lookup"><span data-stu-id="c2bdb-198">`DefaultKeyPropertySet`: One or more key properties of an object.</span></span> <span data-ttu-id="c2bdb-199">En nyckel egenskap identifierar instanser av egenskaps värden, t. ex. ID-antal objekt i en tidigare session.</span><span class="sxs-lookup"><span data-stu-id="c2bdb-199">A key property identifies instances of property values, such as the ID number of items in a session history.</span></span>

<span data-ttu-id="c2bdb-200">Följande XML definierar till exempel standard visning av tjänster ( `System.ServiceProcess.ServiceController` objekt) som returneras av `Get-Service` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="c2bdb-200">For example, the following XML defines the default display of services (`System.ServiceProcess.ServiceController` objects) that are returned by the `Get-Service` cmdlet.</span></span> <span data-ttu-id="c2bdb-201">Den definierar en medlems uppsättning med namnet **PsStandardMembers** som består av en standard egenskap som har angetts med egenskaperna **status**, **Name** och **DisplayName** .</span><span class="sxs-lookup"><span data-stu-id="c2bdb-201">It defines a member set named **PsStandardMembers** that consists of a default property set with the **Status**, **Name**, and **DisplayName** properties.</span></span>

```xml
<Type>
  <Name>System.ServiceProcess.ServiceController</Name>
  <Members>
    <MemberSet>
      <Name>PSStandardMembers</Name>
      <Members>
        <PropertySet>
          <Name>DefaultDisplayPropertySet</Name>
          <ReferencedProperties>
            <Name>Status</Name>
            <Name>Name</Name>
            <Name>DisplayName</Name>
          </ReferencedProperties>
        </PropertySet>
      </Members>
    </MemberSet>
  </Members>
</Type>
```

<span data-ttu-id="c2bdb-202">`<Method>`: Refererar till en ursprunglig metod för det underliggande objektet.</span><span class="sxs-lookup"><span data-stu-id="c2bdb-202">`<Method>`: References a native method of the underlying object.</span></span>

<span data-ttu-id="c2bdb-203">`<Methods>`: En samling av objektets metoder.</span><span class="sxs-lookup"><span data-stu-id="c2bdb-203">`<Methods>`: A collection of the methods of the object.</span></span>

<span data-ttu-id="c2bdb-204">`<NoteProperty>`: Definierar en egenskap med ett statiskt värde.</span><span class="sxs-lookup"><span data-stu-id="c2bdb-204">`<NoteProperty>`: Defines a property with a static value.</span></span>

<span data-ttu-id="c2bdb-205">`<NoteProperty>`Taggen måste ha en `<Name>` tagg som anger namnet på den nya egenskapen och en `<Value>` tagg som anger egenskapens värde.</span><span class="sxs-lookup"><span data-stu-id="c2bdb-205">The `<NoteProperty>` tag must have a `<Name>` tag that specifies the name of the new property and a `<Value>` tag that specifies the value of the property.</span></span>

<span data-ttu-id="c2bdb-206">Till exempel skapar följande XML en **status** egenskap för **system. io. DirectoryInfo** -objekt.</span><span class="sxs-lookup"><span data-stu-id="c2bdb-206">For example, the following XML creates a **Status** property for **System.IO.DirectoryInfo** objects.</span></span> <span data-ttu-id="c2bdb-207">Värdet för egenskapen **status** är alltid **klart**.</span><span class="sxs-lookup"><span data-stu-id="c2bdb-207">The value of the **Status** property is always **Success**.</span></span>

```xml
<Type>
  <Name>System.IO.DirectoryInfo</Name>
  <Members>
    <NoteProperty>
      <Name>Status</Name>
      <Value>Success</Value>
    </NoteProperty>
  </Members>
</Type>
```

<span data-ttu-id="c2bdb-208">`<ParameterizedProperty>`: Egenskaper som tar argument och returnerar ett värde.</span><span class="sxs-lookup"><span data-stu-id="c2bdb-208">`<ParameterizedProperty>`: Properties that take arguments and return a value.</span></span>

<span data-ttu-id="c2bdb-209">`<Properties>`: En samling av objektets egenskaper.</span><span class="sxs-lookup"><span data-stu-id="c2bdb-209">`<Properties>`: A collection of the properties of the object.</span></span>

<span data-ttu-id="c2bdb-210">`<Property>`: En egenskap för bas objekt.</span><span class="sxs-lookup"><span data-stu-id="c2bdb-210">`<Property>`: A property of the base object.</span></span>

<span data-ttu-id="c2bdb-211">`<PropertySet>`: Definierar en samling egenskaper för objektet.</span><span class="sxs-lookup"><span data-stu-id="c2bdb-211">`<PropertySet>`: Defines a collection of properties of the object.</span></span>

<span data-ttu-id="c2bdb-212">`<PropertySet>`Taggen måste ha en `<Name>` tagg som anger namnet på egenskaps uppsättningen och en `<ReferencedProperty>` tagg som anger egenskaperna.</span><span class="sxs-lookup"><span data-stu-id="c2bdb-212">The `<PropertySet>` tag must have a `<Name>` tag that specifies the name of the property set and a `<ReferencedProperty>` tag that specifies the properties.</span></span> <span data-ttu-id="c2bdb-213">Namnen på egenskaperna är omslutna i `<Name>` taggen.</span><span class="sxs-lookup"><span data-stu-id="c2bdb-213">The names of the properties are enclosed in `<Name>` tag.</span></span>

<span data-ttu-id="c2bdb-214">I `Types.ps1xml` `<PropertySet>` används taggar för att definiera uppsättningar av egenskaper för standard visningen av ett objekt.</span><span class="sxs-lookup"><span data-stu-id="c2bdb-214">In `Types.ps1xml`, `<PropertySet>` tags are used to define sets of properties for the default display of an object.</span></span> <span data-ttu-id="c2bdb-215">Du kan identifiera standardvärden som visas genom värdet **PsStandardMembers** i `<Name>` taggen för en `<MemberSet>` tagg.</span><span class="sxs-lookup"><span data-stu-id="c2bdb-215">You can identify the default displays by the value **PsStandardMembers** in the `<Name>` tag of a `<MemberSet>` tag.</span></span>

<span data-ttu-id="c2bdb-216">Till exempel skapar följande XML en **status** egenskap för `System.IO.DirectoryInfo` objektet.</span><span class="sxs-lookup"><span data-stu-id="c2bdb-216">For example, the following XML creates a **Status** property for the `System.IO.DirectoryInfo` object.</span></span> <span data-ttu-id="c2bdb-217">Värdet för egenskapen **status** är alltid **klart**.</span><span class="sxs-lookup"><span data-stu-id="c2bdb-217">The value of the **Status** property is always **Success**.</span></span>

```xml
<Type>
  <Name>System.ServiceProcess.ServiceController</Name>
  <Members>
    <MemberSet>
      <Name>PSStandardMembers</Name>
      <Members>
        <PropertySet>
          <Name>DefaultDisplayPropertySet</Name>
          <ReferencedProperties>
            <Name>Status</Name>
            <Name>Name</Name>
            <Name>DisplayName</Name>
          </ReferencedProperties>
        </PropertySet>
      </Members>
    </MemberSet>
  </Members>
</Type>
```

<span data-ttu-id="c2bdb-218">`<ScriptMethod>`: Definierar en metod vars värde är utdata från ett skript.</span><span class="sxs-lookup"><span data-stu-id="c2bdb-218">`<ScriptMethod>`: Defines a method whose value is the output of a script.</span></span>

<span data-ttu-id="c2bdb-219">`<ScriptMethod>`Taggen måste ha en `<Name>` tagg som anger namnet på den nya metoden och en `<Script>` tagg som innesluter det skript block som returnerar metod resultatet.</span><span class="sxs-lookup"><span data-stu-id="c2bdb-219">The `<ScriptMethod>` tag must have a `<Name>` tag that specifies the name of the new method and a `<Script>` tag that encloses the script block that returns the method result.</span></span>

<span data-ttu-id="c2bdb-220">Till exempel `ConvertToDateTime` `ConvertFromDateTime` är metoderna och för hanterings objekt ( `System.System.Management.ManagementObject` ) skript metoder som använder `ToDateTime` `ToDmtfDateTime` klassen och statiska metoder för `System.Management.ManagementDateTimeConverter` klassen.</span><span class="sxs-lookup"><span data-stu-id="c2bdb-220">For example, the `ConvertToDateTime` and `ConvertFromDateTime` methods of management objects (`System.System.Management.ManagementObject`) are script methods that use the `ToDateTime` and `ToDmtfDateTime` static methods of the `System.Management.ManagementDateTimeConverter` class.</span></span>

```xml
<Type>
 <Name>System.Management.ManagementObject</Name>
 <Members>
 <ScriptMethod>
   <Name>ConvertToDateTime</Name>
   <Script>
   [System.Management.ManagementDateTimeConverter]::ToDateTime($args[0])
   </Script>
 </ScriptMethod>
 <ScriptMethod>
   <Name>ConvertFromDateTime</Name>
   <Script>
   [System.Management.ManagementDateTimeConverter]::ToDmtfDateTime($args[0])
   </Script>
 </ScriptMethod>
 </Members>
</Type>
```

<span data-ttu-id="c2bdb-221">`<ScriptProperty>`: Definierar en egenskap vars värde är utdata från ett skript.</span><span class="sxs-lookup"><span data-stu-id="c2bdb-221">`<ScriptProperty>`: Defines a property whose value is the output of a script.</span></span>

<span data-ttu-id="c2bdb-222">`<ScriptProperty>`Taggen måste ha en `<Name>` tagg som anger namnet på den nya egenskapen och en `<GetScriptBlock>` tagg som innesluter det skript block som returnerar egenskap svärdet.</span><span class="sxs-lookup"><span data-stu-id="c2bdb-222">The `<ScriptProperty>` tag must have a `<Name>` tag that specifies the name of the new property and a `<GetScriptBlock>` tag that encloses the script block that returns the property value.</span></span>

<span data-ttu-id="c2bdb-223">Till exempel är egenskapen **VersionInfo** för objektet **system. io. fileinfo** en skript egenskap som resulterar i att du använder egenskapen **FullName** för den **GetVersionInfo** statiska metoden **system. Diagnostics. FileVersionInfo** .</span><span class="sxs-lookup"><span data-stu-id="c2bdb-223">For example, the **VersionInfo** property of the **System.IO.FileInfo** object is a script property that results from using the **FullName** property of the **GetVersionInfo** static method of **System.Diagnostics.FileVersionInfo** objects.</span></span>

```xml
<Type>
  <Name>System.IO.FileInfo</Name>
  <Members>
    <ScriptProperty>
      <Name>VersionInfo</Name>
      <GetScriptBlock>
      [System.Diagnostics.FileVersionInfo]::GetVersionInfo($this.FullName)
      </GetScriptBlock>
    </ScriptProperty>
  </Members>
</Type>
```

<span data-ttu-id="c2bdb-224">Mer information finns i [Windows PowerShell Software Development Kit (SDK)](/powershell/scripting/developer/windows-powershell).</span><span class="sxs-lookup"><span data-stu-id="c2bdb-224">For more information, see the [Windows PowerShell Software Development Kit (SDK)](/powershell/scripting/developer/windows-powershell).</span></span>

## <a name="update-typedata"></a><span data-ttu-id="c2bdb-225">Update-TypeData</span><span class="sxs-lookup"><span data-stu-id="c2bdb-225">Update-TypeData</span></span>

<span data-ttu-id="c2bdb-226">Kör cmdleten om du vill läsa in dina `Types.ps1xml` filer i en PowerShell-session `Update-TypeData` .</span><span class="sxs-lookup"><span data-stu-id="c2bdb-226">To load your `Types.ps1xml` files into a PowerShell session, run the `Update-TypeData` cmdlet.</span></span> <span data-ttu-id="c2bdb-227">Om du vill att typerna i filen ska prioriteras över typer i den inbyggda `Types.ps1xml` filen lägger du till parametern **PrependData** i `Update-TypeData` .</span><span class="sxs-lookup"><span data-stu-id="c2bdb-227">If you want the types in your file to take precedence over types in the built-in `Types.ps1xml` file, add the **PrependData** parameter of `Update-TypeData`.</span></span> <span data-ttu-id="c2bdb-228">`Update-TypeData` påverkar endast den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="c2bdb-228">`Update-TypeData` affects only the current session.</span></span> <span data-ttu-id="c2bdb-229">Om du vill göra ändringen i alla framtida sessioner exporterar du sessionen eller lägger till `Update-TypeData` kommandot i din PowerShell-profil.</span><span class="sxs-lookup"><span data-stu-id="c2bdb-229">To make the change to all future sessions, export the session, or add the `Update-TypeData` command to your PowerShell profile.</span></span>

<span data-ttu-id="c2bdb-230">Undantag som inträffar i egenskaper, eller genom att lägga till egenskaper till ett `Update-TypeData` kommando, rapportera inte fel till `StdErr` .</span><span class="sxs-lookup"><span data-stu-id="c2bdb-230">Exceptions that occur in properties, or from adding properties to an `Update-TypeData` command, do not report errors to `StdErr`.</span></span> <span data-ttu-id="c2bdb-231">Detta är att utelämna undantag som skulle uppstå i många vanliga typer vid formatering och utmatning.</span><span class="sxs-lookup"><span data-stu-id="c2bdb-231">This is to suppress exceptions that would occur in many common types during formatting and outputting.</span></span> <span data-ttu-id="c2bdb-232">Om du får .NET-egenskaper kan du undvika att utelämna undantag genom att använda metoden syntax i stället, som du ser i följande exempel:</span><span class="sxs-lookup"><span data-stu-id="c2bdb-232">If you are getting .NET properties, you can work around the suppression of exceptions by using method syntax instead, as shown in the following example:</span></span>

```powershell
"hello".get_Length()
```

<span data-ttu-id="c2bdb-233">Observera att metoden syntax bara kan användas med .NET-egenskaper.</span><span class="sxs-lookup"><span data-stu-id="c2bdb-233">Note that method syntax can only be used with .NET properties.</span></span> <span data-ttu-id="c2bdb-234">Egenskaper som läggs till genom att köra `Update-TypeData` cmdleten kan inte använda Method-syntax.</span><span class="sxs-lookup"><span data-stu-id="c2bdb-234">Properties that are added by running the `Update-TypeData` cmdlet cannot use method syntax.</span></span>

## <a name="signing-a-typesps1xml-file"></a><span data-ttu-id="c2bdb-235">Signera en Types.ps1XML-fil</span><span class="sxs-lookup"><span data-stu-id="c2bdb-235">Signing a Types.ps1xml file</span></span>

<span data-ttu-id="c2bdb-236">För att skydda användare av `Types.ps1xml` filen kan du signera filen med en digital signatur.</span><span class="sxs-lookup"><span data-stu-id="c2bdb-236">To protect users of your `Types.ps1xml` file, you can sign the file using a digital signature.</span></span> <span data-ttu-id="c2bdb-237">Mer information finns i [about_Signing](about_Signing.md).</span><span class="sxs-lookup"><span data-stu-id="c2bdb-237">For more information, see [about_Signing](about_Signing.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="c2bdb-238">Se även</span><span class="sxs-lookup"><span data-stu-id="c2bdb-238">See also</span></span>

[<span data-ttu-id="c2bdb-239">about_Signing</span><span class="sxs-lookup"><span data-stu-id="c2bdb-239">about_Signing</span></span>](about_Signing.md)

[<span data-ttu-id="c2bdb-240">Kopiera objekt</span><span class="sxs-lookup"><span data-stu-id="c2bdb-240">Copy-Item</span></span>](xref:Microsoft.PowerShell.Management.Copy-Item)

[<span data-ttu-id="c2bdb-241">Kopiera – ItemProperty</span><span class="sxs-lookup"><span data-stu-id="c2bdb-241">Copy-ItemProperty</span></span>](xref:Microsoft.PowerShell.Management.Copy-ItemProperty)

[<span data-ttu-id="c2bdb-242">Hämta medlem</span><span class="sxs-lookup"><span data-stu-id="c2bdb-242">Get-Member</span></span>](xref:Microsoft.PowerShell.Utility.Get-Member)

[<span data-ttu-id="c2bdb-243">Get-TypeData</span><span class="sxs-lookup"><span data-stu-id="c2bdb-243">Get-TypeData</span></span>](xref:Microsoft.PowerShell.Utility.Get-TypeData)

[<span data-ttu-id="c2bdb-244">Remove-TypeData</span><span class="sxs-lookup"><span data-stu-id="c2bdb-244">Remove-TypeData</span></span>](xref:Microsoft.PowerShell.Utility.Remove-TypeData)

[<span data-ttu-id="c2bdb-245">Uppdatera – TypeData</span><span class="sxs-lookup"><span data-stu-id="c2bdb-245">Update-TypeData</span></span>](xref:Microsoft.PowerShell.Utility.Update-TypeData)

