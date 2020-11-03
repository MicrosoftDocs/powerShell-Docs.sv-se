---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 04/27/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/get-typedata?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-TypeData
ms.openlocfilehash: 83e520f5d48aed89bdd1a461958331185eb46b9a
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/03/2020
ms.locfileid: "93262520"
---
# <span data-ttu-id="7fe5d-103">Get-TypeData</span><span class="sxs-lookup"><span data-stu-id="7fe5d-103">Get-TypeData</span></span>

## <span data-ttu-id="7fe5d-104">Sammanfattning</span><span class="sxs-lookup"><span data-stu-id="7fe5d-104">Synopsis</span></span>
<span data-ttu-id="7fe5d-105">Hämtar utökade typ data i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="7fe5d-105">Gets the extended type data in the current session.</span></span>

## <span data-ttu-id="7fe5d-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="7fe5d-106">Syntax</span></span>

```
Get-TypeData [[-TypeName] <String[]>] [<CommonParameters>]
```

## <span data-ttu-id="7fe5d-107">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="7fe5d-107">Description</span></span>

<span data-ttu-id="7fe5d-108">`Get-TypeData`Cmdlet: en hämtar utökade typ data i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="7fe5d-108">The `Get-TypeData` cmdlet gets the extended type data in the current session.</span></span> <span data-ttu-id="7fe5d-109">Detta inkluderar typ data som har lagts till i sessionen av `Types.ps1xml` fil-och dynamiska typ data som har lagts till med hjälp av parametern för `Update-TypeData` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="7fe5d-109">This includes type data that was added to the session by `Types.ps1xml` file and dynamic type data that was added by using the parameter of the `Update-TypeData` cmdlet.</span></span>

<span data-ttu-id="7fe5d-110">Du kan använda de utökade typ data som `Get-TypeData` returnerar för att undersöka typ data i sessionen och skicka dem till `Update-TypeData` `Remove-TypeData` cmdletarna och.</span><span class="sxs-lookup"><span data-stu-id="7fe5d-110">You can use the extended type data that `Get-TypeData` returns to examine the type data in the session and send it to the `Update-TypeData` and `Remove-TypeData` cmdlets.</span></span>

<span data-ttu-id="7fe5d-111">Utökade typ data lägger till egenskaper och metoder för objekt i PowerShell.</span><span class="sxs-lookup"><span data-stu-id="7fe5d-111">Extended type data adds properties and methods to objects in PowerShell.</span></span> <span data-ttu-id="7fe5d-112">Du kan använda de tillagda egenskaperna och metoderna på samma sätt som du använder de egenskaper och metoder som definieras i objekt typen.</span><span class="sxs-lookup"><span data-stu-id="7fe5d-112">You can use the added properties and methods in the same ways that you would use the properties and methods that are defined in the object type.</span></span> <span data-ttu-id="7fe5d-113">Men när du skriver skript bör du vara medveten om att de tillagda egenskaperna och metoderna kanske inte finns i varje PowerShell-session.</span><span class="sxs-lookup"><span data-stu-id="7fe5d-113">However, when writing scripts, be aware that the added properties and methods might not be present in every PowerShell session.</span></span>

<span data-ttu-id="7fe5d-114">Mer information om `Types.ps1xml` filer finns i [about_Types.ps1XML](../Microsoft.PowerShell.Core/About/about_Types.ps1xml.md).</span><span class="sxs-lookup"><span data-stu-id="7fe5d-114">For more information about `Types.ps1xml` files, see [about_Types.ps1xml](../Microsoft.PowerShell.Core/About/about_Types.ps1xml.md).</span></span> <span data-ttu-id="7fe5d-115">Mer information om dynamiska data typer som `Update-TypeData` cmdleten lägger till finns i `Update-TypeData` .</span><span class="sxs-lookup"><span data-stu-id="7fe5d-115">For more information about dynamic type data that the `Update-TypeData` cmdlet adds, see `Update-TypeData`.</span></span>

<span data-ttu-id="7fe5d-116">Den här cmdleten introducerades i Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="7fe5d-116">This cmdlet was introduced in Windows PowerShell 3.0.</span></span>

## <span data-ttu-id="7fe5d-117">Exempel</span><span class="sxs-lookup"><span data-stu-id="7fe5d-117">Examples</span></span>

### <span data-ttu-id="7fe5d-118">Exempel 1: Hämta alla utökade typ data</span><span class="sxs-lookup"><span data-stu-id="7fe5d-118">Example 1: Get all extended type data</span></span>

<span data-ttu-id="7fe5d-119">Det här exemplet hämtar alla utökade typ data i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="7fe5d-119">This example gets all extended type data in the current session.</span></span>

 ```powershell
Get-TypeData
```

### <span data-ttu-id="7fe5d-120">Exempel 2: Hämta typer efter namn</span><span class="sxs-lookup"><span data-stu-id="7fe5d-120">Example 2: Get types by name</span></span>

<span data-ttu-id="7fe5d-121">Det här exemplet hämtar alla typer i den aktuella sessionen som har namn som innehåller händelser.</span><span class="sxs-lookup"><span data-stu-id="7fe5d-121">This example gets all types in the current session that have names that contain Eventing.</span></span>

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

### <span data-ttu-id="7fe5d-122">Exempel 3: Hämta skript blocket som skapar ett egenskaps värde</span><span class="sxs-lookup"><span data-stu-id="7fe5d-122">Example 3: Get the script block that creates a property value</span></span>

<span data-ttu-id="7fe5d-123">Det här exemplet hämtar skript blocket som skapar värdet för egenskapen **EventID** för **EventLogEntry** -objekt.</span><span class="sxs-lookup"><span data-stu-id="7fe5d-123">This example gets the script block that creates the value of the **EventID** property of **EventLogEntry** objects.</span></span>

 ```powershell
(Get-TypeData *EventLogEntry*).Members.EventID
```

```Output
GetScriptBlock                     SetScriptBlock     IsHidden Name
--------------                     --------------     -------- ----
$this.get_EventID() -band 0xFFFF                         False EventID
```

### <span data-ttu-id="7fe5d-124">Exempel 4: Hämta skript blocket som definierar en egenskap för ett angivet objekt</span><span class="sxs-lookup"><span data-stu-id="7fe5d-124">Example 4: Get the script block that defines a property for a specified object</span></span>

<span data-ttu-id="7fe5d-125">Det här exemplet hämtar skript blocket som definierar egenskapen **datetime** för **system. DateTime** -objekt i PowerShell.</span><span class="sxs-lookup"><span data-stu-id="7fe5d-125">This example gets the script block that defines the **DateTime** property of **System.DateTime** objects in PowerShell.</span></span>

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

<span data-ttu-id="7fe5d-126">Kommandot använder `Get-TypeData` cmdleten för att hämta de utökade data typerna för **system. datum/tid** -typen.</span><span class="sxs-lookup"><span data-stu-id="7fe5d-126">The command uses the `Get-TypeData` cmdlet to get the extended type data for the **System.DataTime** type.</span></span> <span data-ttu-id="7fe5d-127">Kommandot hämtar egenskapen **members** för **TypeData** -objektet.</span><span class="sxs-lookup"><span data-stu-id="7fe5d-127">The command gets the **Members** property of the **TypeData** object.</span></span>

<span data-ttu-id="7fe5d-128">Egenskapen **members** innehåller en hash-tabell med egenskaper och metoder som definieras av utökade typ data.</span><span class="sxs-lookup"><span data-stu-id="7fe5d-128">The **Members** property contains a hash table of properties and methods that are defined by extended type data.</span></span> <span data-ttu-id="7fe5d-129">Varje nyckel i hash-tabellen medlemmar är ett egenskaps-eller metod namn och varje värde är definitionen av egenskapen eller metod svärdet.</span><span class="sxs-lookup"><span data-stu-id="7fe5d-129">Each key in the Members hash table is a property or method name and each value is the definition of the property or method value.</span></span>

<span data-ttu-id="7fe5d-130">Kommandot hämtar **datetime** -nyckeln i **members** och dess egenskaps värde för **GetScriptBlock** .</span><span class="sxs-lookup"><span data-stu-id="7fe5d-130">The command gets the **DateTime** key in **Members** and its **GetScriptBlock** property value.</span></span>

<span data-ttu-id="7fe5d-131">Utdata visar skript blocket som skapar värdet för egenskapen **datetime** för varje **system. DateTime** -objekt i PowerShell.</span><span class="sxs-lookup"><span data-stu-id="7fe5d-131">The output shows the script block that creates the value of the **DateTime** property of every **System.DateTime** object in PowerShell.</span></span>

## <span data-ttu-id="7fe5d-132">Parametrar</span><span class="sxs-lookup"><span data-stu-id="7fe5d-132">Parameters</span></span>

### <span data-ttu-id="7fe5d-133">-TypeName</span><span class="sxs-lookup"><span data-stu-id="7fe5d-133">-TypeName</span></span>

<span data-ttu-id="7fe5d-134">Anger ange data som en matris enbart för de typer som har angivna namn.</span><span class="sxs-lookup"><span data-stu-id="7fe5d-134">Specifies type data as an array only for the types with the specified names.</span></span> <span data-ttu-id="7fe5d-135">Som standard `Get-TypeData` hämtar alla typer i sessionen.</span><span class="sxs-lookup"><span data-stu-id="7fe5d-135">By default, `Get-TypeData` gets all types in the session.</span></span>

<span data-ttu-id="7fe5d-136">Ange typ namn eller namn mönster.</span><span class="sxs-lookup"><span data-stu-id="7fe5d-136">Enter type names or a name patterns.</span></span> <span data-ttu-id="7fe5d-137">Fullständiga namn eller namn mönster med jokertecken krävs, även för typer i namn området system.</span><span class="sxs-lookup"><span data-stu-id="7fe5d-137">Full names, or name patterns with wildcard characters are required, even for types in the System namespace.</span></span> <span data-ttu-id="7fe5d-138">Jokertecken stöds och parameter namn **TypeName** är valfritt.</span><span class="sxs-lookup"><span data-stu-id="7fe5d-138">Wildcards are supported and the parameter name **TypeName** is optional.</span></span> <span data-ttu-id="7fe5d-139">Du kan också skicka pipe-namn till `Get-TypeData` .</span><span class="sxs-lookup"><span data-stu-id="7fe5d-139">You can also pipe type names to `Get-TypeData`.</span></span>

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

### <span data-ttu-id="7fe5d-140">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="7fe5d-140">CommonParameters</span></span>

<span data-ttu-id="7fe5d-141">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="7fe5d-141">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="7fe5d-142">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="7fe5d-142">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="7fe5d-143">Indata</span><span class="sxs-lookup"><span data-stu-id="7fe5d-143">Inputs</span></span>

### <span data-ttu-id="7fe5d-144">System. String</span><span class="sxs-lookup"><span data-stu-id="7fe5d-144">System.String</span></span>

<span data-ttu-id="7fe5d-145">Du kan skicka pipe-typnamn till `Get-TypeData` .</span><span class="sxs-lookup"><span data-stu-id="7fe5d-145">You can pipe type names to `Get-TypeData`.</span></span>

## <span data-ttu-id="7fe5d-146">Utdata</span><span class="sxs-lookup"><span data-stu-id="7fe5d-146">Outputs</span></span>

### <span data-ttu-id="7fe5d-147">System. Management. Automation. körnings utrymmen. TypeData</span><span class="sxs-lookup"><span data-stu-id="7fe5d-147">System.Management.Automation.Runspaces.TypeData</span></span>

## <span data-ttu-id="7fe5d-148">Kommentarer</span><span class="sxs-lookup"><span data-stu-id="7fe5d-148">Notes</span></span>

<span data-ttu-id="7fe5d-149">`Get-TypeData` hämtar endast utökade typ data i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="7fe5d-149">`Get-TypeData` gets only the extended type data in the current session.</span></span> <span data-ttu-id="7fe5d-150">Den får inte utökad typ av data som finns på datorn, men som inte har lagts till i den aktuella sessionen, till exempel utökade typer som har definierats i moduler som inte har importer ATS till den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="7fe5d-150">It does not get extended type data that is on the computer, but has not been added to the current session, such as extended types that are defined in modules that have not been imported into the current session.</span></span>

## <span data-ttu-id="7fe5d-151">Relaterade länkar</span><span class="sxs-lookup"><span data-stu-id="7fe5d-151">Related links</span></span>

[<span data-ttu-id="7fe5d-152">about_Types.ps1XML</span><span class="sxs-lookup"><span data-stu-id="7fe5d-152">about_Types.ps1xml</span></span>](../Microsoft.PowerShell.Core/About/about_Types.ps1xml.md)

[<span data-ttu-id="7fe5d-153">Remove-TypeData</span><span class="sxs-lookup"><span data-stu-id="7fe5d-153">Remove-TypeData</span></span>](Remove-TypeData.md)

[<span data-ttu-id="7fe5d-154">Uppdatera – TypeData</span><span class="sxs-lookup"><span data-stu-id="7fe5d-154">Update-TypeData</span></span>](Update-TypeData.md)
