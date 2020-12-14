---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 04/27/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/get-typedata?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-TypeData
ms.openlocfilehash: db5dc586f2a165d83c25bdf2addaeb625f9e1ba0
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94708370"
---
# <span data-ttu-id="a188f-102">Get-TypeData</span><span class="sxs-lookup"><span data-stu-id="a188f-102">Get-TypeData</span></span>

## <span data-ttu-id="a188f-103">Sammanfattning</span><span class="sxs-lookup"><span data-stu-id="a188f-103">Synopsis</span></span>
<span data-ttu-id="a188f-104">Hämtar utökade typ data i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="a188f-104">Gets the extended type data in the current session.</span></span>

## <span data-ttu-id="a188f-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="a188f-105">Syntax</span></span>

```
Get-TypeData [[-TypeName] <String[]>] [<CommonParameters>]
```

## <span data-ttu-id="a188f-106">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="a188f-106">Description</span></span>

<span data-ttu-id="a188f-107">`Get-TypeData`Cmdlet: en hämtar utökade typ data i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="a188f-107">The `Get-TypeData` cmdlet gets the extended type data in the current session.</span></span> <span data-ttu-id="a188f-108">Detta inkluderar typ data som har lagts till i sessionen av `Types.ps1xml` fil-och dynamiska typ data som har lagts till med hjälp av parametern för `Update-TypeData` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="a188f-108">This includes type data that was added to the session by `Types.ps1xml` file and dynamic type data that was added by using the parameter of the `Update-TypeData` cmdlet.</span></span>

<span data-ttu-id="a188f-109">Du kan använda de utökade typ data som `Get-TypeData` returnerar för att undersöka typ data i sessionen och skicka dem till `Update-TypeData` `Remove-TypeData` cmdletarna och.</span><span class="sxs-lookup"><span data-stu-id="a188f-109">You can use the extended type data that `Get-TypeData` returns to examine the type data in the session and send it to the `Update-TypeData` and `Remove-TypeData` cmdlets.</span></span>

<span data-ttu-id="a188f-110">Utökade typ data lägger till egenskaper och metoder för objekt i PowerShell.</span><span class="sxs-lookup"><span data-stu-id="a188f-110">Extended type data adds properties and methods to objects in PowerShell.</span></span> <span data-ttu-id="a188f-111">Du kan använda de tillagda egenskaperna och metoderna på samma sätt som du använder de egenskaper och metoder som definieras i objekt typen.</span><span class="sxs-lookup"><span data-stu-id="a188f-111">You can use the added properties and methods in the same ways that you would use the properties and methods that are defined in the object type.</span></span> <span data-ttu-id="a188f-112">Men när du skriver skript bör du vara medveten om att de tillagda egenskaperna och metoderna kanske inte finns i varje PowerShell-session.</span><span class="sxs-lookup"><span data-stu-id="a188f-112">However, when writing scripts, be aware that the added properties and methods might not be present in every PowerShell session.</span></span>

<span data-ttu-id="a188f-113">Mer information om `Types.ps1xml` filer finns i [about_Types.ps1XML](../Microsoft.PowerShell.Core/About/about_Types.ps1xml.md).</span><span class="sxs-lookup"><span data-stu-id="a188f-113">For more information about `Types.ps1xml` files, see [about_Types.ps1xml](../Microsoft.PowerShell.Core/About/about_Types.ps1xml.md).</span></span> <span data-ttu-id="a188f-114">Mer information om dynamiska data typer som `Update-TypeData` cmdleten lägger till finns i `Update-TypeData` .</span><span class="sxs-lookup"><span data-stu-id="a188f-114">For more information about dynamic type data that the `Update-TypeData` cmdlet adds, see `Update-TypeData`.</span></span>

<span data-ttu-id="a188f-115">Den här cmdleten introducerades i Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="a188f-115">This cmdlet was introduced in Windows PowerShell 3.0.</span></span>

## <span data-ttu-id="a188f-116">Exempel</span><span class="sxs-lookup"><span data-stu-id="a188f-116">Examples</span></span>

### <span data-ttu-id="a188f-117">Exempel 1: Hämta alla utökade typ data</span><span class="sxs-lookup"><span data-stu-id="a188f-117">Example 1: Get all extended type data</span></span>

<span data-ttu-id="a188f-118">Det här exemplet hämtar alla utökade typ data i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="a188f-118">This example gets all extended type data in the current session.</span></span>

 ```powershell
Get-TypeData
```

### <span data-ttu-id="a188f-119">Exempel 2: Hämta typer efter namn</span><span class="sxs-lookup"><span data-stu-id="a188f-119">Example 2: Get types by name</span></span>

<span data-ttu-id="a188f-120">Det här exemplet hämtar alla typer i den aktuella sessionen som har namn som innehåller händelser.</span><span class="sxs-lookup"><span data-stu-id="a188f-120">This example gets all types in the current session that have names that contain Eventing.</span></span>

 ```powershell
"*Eventing*" | Get-TypeData
```

```Output
TypeName                                                  Members
--------                                                  -------
System.Diagnostics.Eventing.Reader.EventLogConfiguration  {}System.Diagnostics.Eventing.Reader.EventLogRecord
                                                          {}System.Diagnostics.Eventing.Reader.ProviderMetadata
                                                          {[ProviderName, System.Management.Automation.Runspaces.AliasProper...
```

### <span data-ttu-id="a188f-121">Exempel 3: Hämta skript blocket som skapar ett egenskaps värde</span><span class="sxs-lookup"><span data-stu-id="a188f-121">Example 3: Get the script block that creates a property value</span></span>

<span data-ttu-id="a188f-122">Det här exemplet hämtar skript blocket som skapar värdet för egenskapen **EventID** för **EventLogEntry** -objekt.</span><span class="sxs-lookup"><span data-stu-id="a188f-122">This example gets the script block that creates the value of the **EventID** property of **EventLogEntry** objects.</span></span>

 ```powershell
(Get-TypeData *EventLogEntry*).Members.EventID
```

```Output
GetScriptBlock                     SetScriptBlock     IsHidden Name
--------------                     --------------     -------- ----
$this.get_EventID() -band 0xFFFF                         False EventID
```

### <span data-ttu-id="a188f-123">Exempel 4: Hämta skript blocket som definierar en egenskap för ett angivet objekt</span><span class="sxs-lookup"><span data-stu-id="a188f-123">Example 4: Get the script block that defines a property for a specified object</span></span>

<span data-ttu-id="a188f-124">Det här exemplet hämtar skript blocket som definierar egenskapen **datetime** för **system. DateTime** -objekt i PowerShell.</span><span class="sxs-lookup"><span data-stu-id="a188f-124">This example gets the script block that defines the **DateTime** property of **System.DateTime** objects in PowerShell.</span></span>

 ```powershell
(Get-TypeData -TypeName System.DateTime).Members["DateTime"].GetScriptBlock
if ((& { Set-StrictMode -Version 1; $this.DisplayHint }) -ieq  "Date") {
    "{0}" -f $this.ToLongDateString()
}
elseif ((& { Set-StrictMode -Version 1; $this.DisplayHint }) -ieq "Time") {
    "{0}" -f  $this.ToLongTimeString()
}
else {
    "{0} {1}" -f $this.ToLongDateString(), $this.ToLongTimeString()
}
```

<span data-ttu-id="a188f-125">Kommandot använder `Get-TypeData` cmdleten för att hämta de utökade data typerna för **system. datum/tid** -typen.</span><span class="sxs-lookup"><span data-stu-id="a188f-125">The command uses the `Get-TypeData` cmdlet to get the extended type data for the **System.DataTime** type.</span></span> <span data-ttu-id="a188f-126">Kommandot hämtar egenskapen **members** för **TypeData** -objektet.</span><span class="sxs-lookup"><span data-stu-id="a188f-126">The command gets the **Members** property of the **TypeData** object.</span></span>

<span data-ttu-id="a188f-127">Egenskapen **members** innehåller en hash-tabell med egenskaper och metoder som definieras av utökade typ data.</span><span class="sxs-lookup"><span data-stu-id="a188f-127">The **Members** property contains a hash table of properties and methods that are defined by extended type data.</span></span> <span data-ttu-id="a188f-128">Varje nyckel i hash-tabellen medlemmar är ett egenskaps-eller metod namn och varje värde är definitionen av egenskapen eller metod svärdet.</span><span class="sxs-lookup"><span data-stu-id="a188f-128">Each key in the Members hash table is a property or method name and each value is the definition of the property or method value.</span></span>

<span data-ttu-id="a188f-129">Kommandot hämtar **datetime** -nyckeln i **members** och dess egenskaps värde för **GetScriptBlock** .</span><span class="sxs-lookup"><span data-stu-id="a188f-129">The command gets the **DateTime** key in **Members** and its **GetScriptBlock** property value.</span></span>

<span data-ttu-id="a188f-130">Utdata visar skript blocket som skapar värdet för egenskapen **datetime** för varje **system. DateTime** -objekt i PowerShell.</span><span class="sxs-lookup"><span data-stu-id="a188f-130">The output shows the script block that creates the value of the **DateTime** property of every **System.DateTime** object in PowerShell.</span></span>

## <span data-ttu-id="a188f-131">Parameters (Parametrar)</span><span class="sxs-lookup"><span data-stu-id="a188f-131">Parameters</span></span>

### <span data-ttu-id="a188f-132">-TypeName</span><span class="sxs-lookup"><span data-stu-id="a188f-132">-TypeName</span></span>

<span data-ttu-id="a188f-133">Anger ange data som en matris enbart för de typer som har angivna namn.</span><span class="sxs-lookup"><span data-stu-id="a188f-133">Specifies type data as an array only for the types with the specified names.</span></span> <span data-ttu-id="a188f-134">Som standard `Get-TypeData` hämtar alla typer i sessionen.</span><span class="sxs-lookup"><span data-stu-id="a188f-134">By default, `Get-TypeData` gets all types in the session.</span></span>

<span data-ttu-id="a188f-135">Ange typ namn eller namn mönster.</span><span class="sxs-lookup"><span data-stu-id="a188f-135">Enter type names or a name patterns.</span></span> <span data-ttu-id="a188f-136">Fullständiga namn eller namn mönster med jokertecken krävs, även för typer i namn området system.</span><span class="sxs-lookup"><span data-stu-id="a188f-136">Full names, or name patterns with wildcard characters are required, even for types in the System namespace.</span></span> <span data-ttu-id="a188f-137">Jokertecken stöds och parameter namn **TypeName** är valfritt.</span><span class="sxs-lookup"><span data-stu-id="a188f-137">Wildcards are supported and the parameter name **TypeName** is optional.</span></span> <span data-ttu-id="a188f-138">Du kan också skicka pipe-namn till `Get-TypeData` .</span><span class="sxs-lookup"><span data-stu-id="a188f-138">You can also pipe type names to `Get-TypeData`.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: True
```

### <span data-ttu-id="a188f-139">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="a188f-139">CommonParameters</span></span>

<span data-ttu-id="a188f-140">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="a188f-140">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="a188f-141">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="a188f-141">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="a188f-142">Indata</span><span class="sxs-lookup"><span data-stu-id="a188f-142">Inputs</span></span>

### <span data-ttu-id="a188f-143">System. String</span><span class="sxs-lookup"><span data-stu-id="a188f-143">System.String</span></span>

<span data-ttu-id="a188f-144">Du kan skicka pipe-typnamn till `Get-TypeData` .</span><span class="sxs-lookup"><span data-stu-id="a188f-144">You can pipe type names to `Get-TypeData`.</span></span>

## <span data-ttu-id="a188f-145">Outputs (Utdata)</span><span class="sxs-lookup"><span data-stu-id="a188f-145">Outputs</span></span>

### <span data-ttu-id="a188f-146">System. Management. Automation. körnings utrymmen. TypeData</span><span class="sxs-lookup"><span data-stu-id="a188f-146">System.Management.Automation.Runspaces.TypeData</span></span>

## <span data-ttu-id="a188f-147">Kommentarer</span><span class="sxs-lookup"><span data-stu-id="a188f-147">Notes</span></span>

<span data-ttu-id="a188f-148">`Get-TypeData` hämtar endast utökade typ data i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="a188f-148">`Get-TypeData` gets only the extended type data in the current session.</span></span> <span data-ttu-id="a188f-149">Den får inte utökad typ av data som finns på datorn, men som inte har lagts till i den aktuella sessionen, till exempel utökade typer som har definierats i moduler som inte har importer ATS till den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="a188f-149">It does not get extended type data that is on the computer, but has not been added to the current session, such as extended types that are defined in modules that have not been imported into the current session.</span></span>

## <span data-ttu-id="a188f-150">Relaterade länkar</span><span class="sxs-lookup"><span data-stu-id="a188f-150">Related links</span></span>

[<span data-ttu-id="a188f-151">about_Types.ps1XML</span><span class="sxs-lookup"><span data-stu-id="a188f-151">about_Types.ps1xml</span></span>](../Microsoft.PowerShell.Core/About/about_Types.ps1xml.md)

[<span data-ttu-id="a188f-152">Remove-TypeData</span><span class="sxs-lookup"><span data-stu-id="a188f-152">Remove-TypeData</span></span>](Remove-TypeData.md)

[<span data-ttu-id="a188f-153">Uppdatera – TypeData</span><span class="sxs-lookup"><span data-stu-id="a188f-153">Update-TypeData</span></span>](Update-TypeData.md)

