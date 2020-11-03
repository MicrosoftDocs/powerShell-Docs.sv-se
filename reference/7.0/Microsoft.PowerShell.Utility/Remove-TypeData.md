---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 04/27/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/remove-typedata?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Remove-TypeData
ms.openlocfilehash: 1011011c8ce5471f976336e6b563f6d1662e17e4
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/03/2020
ms.locfileid: "93262322"
---
# <span data-ttu-id="1c4b4-103">Remove-TypeData</span><span class="sxs-lookup"><span data-stu-id="1c4b4-103">Remove-TypeData</span></span>

## <span data-ttu-id="1c4b4-104">Sammanfattning</span><span class="sxs-lookup"><span data-stu-id="1c4b4-104">Synopsis</span></span>
<span data-ttu-id="1c4b4-105">Tar bort utökade typer från den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="1c4b4-105">Deletes extended types from the current session.</span></span>

## <span data-ttu-id="1c4b4-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="1c4b4-106">Syntax</span></span>

### <span data-ttu-id="1c4b4-107">RemoveTypeDataSet (standard)</span><span class="sxs-lookup"><span data-stu-id="1c4b4-107">RemoveTypeDataSet (Default)</span></span>

```
Remove-TypeData -TypeData <TypeData> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="1c4b4-108">RemoveTypeSet</span><span class="sxs-lookup"><span data-stu-id="1c4b4-108">RemoveTypeSet</span></span>

```
Remove-TypeData [-TypeName] <String> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="1c4b4-109">RemoveFileSet</span><span class="sxs-lookup"><span data-stu-id="1c4b4-109">RemoveFileSet</span></span>

```
Remove-TypeData -Path <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="1c4b4-110">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="1c4b4-110">DESCRIPTION</span></span>

<span data-ttu-id="1c4b4-111">`Remove-TypeData`Cmdleten tar bort utökade typ data från den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="1c4b4-111">The `Remove-TypeData` cmdlet deletes extended type data from the current session.</span></span> <span data-ttu-id="1c4b4-112">Denna cmdlet påverkar endast den aktuella sessionen och de sessioner som skapas i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="1c4b4-112">This cmdlet affects only the current session and sessions that are created in the current session.</span></span>

<span data-ttu-id="1c4b4-113">Du kan lägga till egenskaper och metoder för objekt i PowerShell genom att definiera dem i `Update-TypeData` kommandon och `Types.ps1xml` filer.</span><span class="sxs-lookup"><span data-stu-id="1c4b4-113">You can add properties and methods to objects in PowerShell by defining them in `Update-TypeData` commands and `Types.ps1xml` files.</span></span> <span data-ttu-id="1c4b4-114">`Remove-TypeData` tar bort dessa utökade egenskaper och metoder från den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="1c4b4-114">`Remove-TypeData` deletes those extended properties and methods from the current session.</span></span> <span data-ttu-id="1c4b4-115">`Remove-TypeData` tar inte bort `Types.ps1xml` filerna eller tar bort eventuella definitioner av utökad typ från `Types.ps1xml` filerna.</span><span class="sxs-lookup"><span data-stu-id="1c4b4-115">`Remove-TypeData` does not delete the `Types.ps1xml` files or delete any extended type definitions from the `Types.ps1xml` files.</span></span> <span data-ttu-id="1c4b4-116">Mer information om `Types.ps1xml` filer finns i [about_Types.ps1XML](../Microsoft.PowerShell.Core/about/about_Types.ps1xml.md).</span><span class="sxs-lookup"><span data-stu-id="1c4b4-116">For more information about `Types.ps1xml` files, see [about_Types.ps1xml](../Microsoft.PowerShell.Core/about/about_Types.ps1xml.md).</span></span>

<span data-ttu-id="1c4b4-117">Den här cmdleten introducerades i Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="1c4b4-117">This cmdlet was introduced in Windows PowerShell 3.0.</span></span>

## <span data-ttu-id="1c4b4-118">Exempel</span><span class="sxs-lookup"><span data-stu-id="1c4b4-118">Examples</span></span>

### <span data-ttu-id="1c4b4-119">Exempel 1: ta bort typ data för en angiven typ</span><span class="sxs-lookup"><span data-stu-id="1c4b4-119">Example 1: Remove type data for a specified type</span></span>

<span data-ttu-id="1c4b4-120">Det här exemplet tar bort alla typ data för **system. mat ris** typen från sessionen, inklusive typ data som har lagts till av en `Types.ps1xml` fil och dynamiska typ data som har lagts till i sessionen med hjälp av `Update-TypeData` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="1c4b4-120">This example deletes all type data for the **System.Array** type  from the session, including type data that was added by a `Types.ps1xml` file and dynamic type data that was added to the session by using the `Update-TypeData` cmdlet.</span></span>

```powershell
Remove-TypeData -TypeName System.Array
```

### <span data-ttu-id="1c4b4-121">Exempel 2: ta bort en utökad datatyp från en session</span><span class="sxs-lookup"><span data-stu-id="1c4b4-121">Example 2: Remove an extended data type from a session</span></span>

<span data-ttu-id="1c4b4-122">I det här exemplet visas effekterna av att ta bort utökade typ data från en session.</span><span class="sxs-lookup"><span data-stu-id="1c4b4-122">This example shows the effect of removing extended type data from a session.</span></span> <span data-ttu-id="1c4b4-123">Det första `Get-TypeData` hämtar utökade typ data för **system. DateTime** -typen.</span><span class="sxs-lookup"><span data-stu-id="1c4b4-123">The first `Get-TypeData` gets extended type data for the **System.DateTime** type.</span></span> <span data-ttu-id="1c4b4-124">Utdata visar att en **datetime** -egenskap har lagts till i alla **system. DateTime** -objekt i PowerShell.</span><span class="sxs-lookup"><span data-stu-id="1c4b4-124">The output shows that a **DateTime** property has been added to all **System.DateTime** objects in PowerShell.</span></span> <span data-ttu-id="1c4b4-125">`Get-Date`Cmdleten returnerar ett **system. DateTime** -objekt.</span><span class="sxs-lookup"><span data-stu-id="1c4b4-125">The `Get-Date` cmdlet returns a **System.DateTime** object.</span></span> <span data-ttu-id="1c4b4-126">Kommandot använder punkt notation för att hämta värdet för egenskapen **datetime** för objektet **system. DateTime** som `Get-Date` returnerar.</span><span class="sxs-lookup"><span data-stu-id="1c4b4-126">The command uses dot notation to get the value of the **DateTime** property of the **System.DateTime** object that `Get-Date` returns.</span></span>

```powershell
Get-TypeData System.DateTime
(Get-Date).DateTime
Get-TypeData System.DateTime | Remove-TypeData
(Get-Date).DateTime
```

```Output
TypeName        Members
--------        -------
System.DateTime {[DateTime, System.Management.Automation.Runspaces.ScriptPropertyData]}

Friday, January 20, 2012 9:01:00 PM
```

<span data-ttu-id="1c4b4-127">Nästa `Get-TypeData` cmdlet för att hämta alla utökade typ data för **system. DateTime** -typen och pipes som till `Remove-TypeData` cmdleten för att ta bort de utökade data typerna.</span><span class="sxs-lookup"><span data-stu-id="1c4b4-127">The next `Get-TypeData` cmdlet to get all extended type data for the **System.DateTime** type and pipes that to the `Remove-TypeData` cmdlet to delete the extended type data.</span></span> <span data-ttu-id="1c4b4-128">Den sista `Get-Date` cmdleten visar effekterna av att ta bort den utökade typen av data för **system. DateTime** -typen.</span><span class="sxs-lookup"><span data-stu-id="1c4b4-128">The last `Get-Date` cmdlet shows the effect of deleting the extended type data for the **System.DateTime** type.</span></span> <span data-ttu-id="1c4b4-129">Eftersom egenskapen **system. DateTime** inte längre finns returnerar ett kommando för att hämta dess värde Nothing.</span><span class="sxs-lookup"><span data-stu-id="1c4b4-129">Because the **System.DateTime** property no longer exists, a command to get its value returns nothing.</span></span>

### <span data-ttu-id="1c4b4-130">Exempel 3: ta bort utökade typer för moduler</span><span class="sxs-lookup"><span data-stu-id="1c4b4-130">Example 3: Remove extended types for modules</span></span>

<span data-ttu-id="1c4b4-131">Det här exemplet tar bort alla utökade typ data för modul-objekt.</span><span class="sxs-lookup"><span data-stu-id="1c4b4-131">This example removes all extended type data for module objects.</span></span> <span data-ttu-id="1c4b4-132">När du flyttar ett objekt till `Remove-TypeData` `Remove-TypeData` hämtar namnet på objekt typen och tar bort alla typ data för alla objekt av den typen.</span><span class="sxs-lookup"><span data-stu-id="1c4b4-132">When you pipe an object to `Remove-TypeData`, `Remove-TypeData` gets the name of the object type and removes all type data for all objects of that type.</span></span>

```powershell
Get-Module | Remove-TypeData
```

### <span data-ttu-id="1c4b4-133">Exempel 4: ta bort utökade typer från angivna moduler</span><span class="sxs-lookup"><span data-stu-id="1c4b4-133">Example 4: Remove extended types from specified modules</span></span>

<span data-ttu-id="1c4b4-134">I det här exemplet används cmdlet **-parametern för** `Remove-TypeData` cmdleten för att ta bort de utökade typer som definieras i de `Types.ps1xml` filer som läggs till av **PSScheduledJob** -och **PSWorkflow** -modulerna.</span><span class="sxs-lookup"><span data-stu-id="1c4b4-134">This example uses the **Path** parameter of the `Remove-TypeData` cmdlet to remove the extended types that are defined in the `Types.ps1xml` files that are added by the **PSScheduledJob** and **PSWorkflow** modules.</span></span> <span data-ttu-id="1c4b4-135">Det här kommandot påverkar inte dynamiska typ data som läggs till med hjälp av `Update-TypeData` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="1c4b4-135">This command does not affect dynamic type data that is added by using the `Update-TypeData` cmdlet.</span></span> <span data-ttu-id="1c4b4-136">Kommandot slutförs endast när modulerna har importer ATS till den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="1c4b4-136">The command succeeds only when the modules have been imported into the current session.</span></span>

```powershell
Remove-TypeData -Path "$PSHOME\Modules\PSScheduledJob", "$PSHOME\Modules\PSWorkflow\PSWorkflow.types.ps1xml"
```

<span data-ttu-id="1c4b4-137">Mer information om moduler finns i [about_Modules](../Microsoft.PowerShell.Core/About/about_Modules.md).</span><span class="sxs-lookup"><span data-stu-id="1c4b4-137">For more information about modules, see [about_Modules](../Microsoft.PowerShell.Core/About/about_Modules.md).</span></span>

### <span data-ttu-id="1c4b4-138">Exempel 5: ta bort utökade typer från en fjärran sluten session</span><span class="sxs-lookup"><span data-stu-id="1c4b4-138">Example 5: Remove extended types from a remote session</span></span>

<span data-ttu-id="1c4b4-139">I det här exemplet tas utökade typer bort från en fjärran sluten session.</span><span class="sxs-lookup"><span data-stu-id="1c4b4-139">This example removes extended types from a remote session.</span></span> <span data-ttu-id="1c4b4-140">Kommandot använder `Invoke-Command` cmdleten för att ta bort utökade typ data för alla CIM-typer i sessionerna i `$S` variabeln.</span><span class="sxs-lookup"><span data-stu-id="1c4b4-140">The command uses the `Invoke-Command` cmdlet to remove extended type data for all CIM types in the sessions in the `$S` variable.</span></span>

```powershell
Invoke-Command -Session $S {Get-TypeData -TypeName *CIM* | Remove-TypeData}
```

## <span data-ttu-id="1c4b4-141">Parametrar</span><span class="sxs-lookup"><span data-stu-id="1c4b4-141">Parameters</span></span>

### <span data-ttu-id="1c4b4-142">-Path</span><span class="sxs-lookup"><span data-stu-id="1c4b4-142">-Path</span></span>

<span data-ttu-id="1c4b4-143">Anger en matris med filer som den här cmdleten tar bort från data för den utökade typen av session.</span><span class="sxs-lookup"><span data-stu-id="1c4b4-143">Specifies an array of files that this cmdlet deletes from the session extended type data.</span></span> <span data-ttu-id="1c4b4-144">Den här parametern är obligatorisk.</span><span class="sxs-lookup"><span data-stu-id="1c4b4-144">This parameter is required.</span></span>

<span data-ttu-id="1c4b4-145">Ange sökvägar och fil namn för en eller flera `Types.ps1xml` filer.</span><span class="sxs-lookup"><span data-stu-id="1c4b4-145">Enter the paths and file names of one or more `Types.ps1xml` files.</span></span> <span data-ttu-id="1c4b4-146">Jokertecken stöds inte.</span><span class="sxs-lookup"><span data-stu-id="1c4b4-146">Wildcards are not supported.</span></span> <span data-ttu-id="1c4b4-147">Om du utelämnar sökvägen är standard platsen den aktuella katalogen.</span><span class="sxs-lookup"><span data-stu-id="1c4b4-147">If you omit the path, the default location is the current directory.</span></span>

```yaml
Type: System.String[]
Parameter Sets: RemoveFileSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="1c4b4-148">-TypeData</span><span class="sxs-lookup"><span data-stu-id="1c4b4-148">-TypeData</span></span>

<span data-ttu-id="1c4b4-149">Anger typ data som denna cmdlet tar bort från sessionen.</span><span class="sxs-lookup"><span data-stu-id="1c4b4-149">Specifies the type data that this cmdlet deletes from the session.</span></span> <span data-ttu-id="1c4b4-150">Den här parametern är obligatorisk.</span><span class="sxs-lookup"><span data-stu-id="1c4b4-150">This parameter is required.</span></span> <span data-ttu-id="1c4b4-151">Ange en variabel som innehåller **TypeData** -objekt ( **system. Management. Automation. körnings utrymmen. TypeData** ) eller ett kommando som hämtar **TypeData** -objekt, till exempel ett `Get-TypeData` kommando.</span><span class="sxs-lookup"><span data-stu-id="1c4b4-151">Enter a variable that contains **TypeData** objects ( **System.Management.Automation.Runspaces.TypeData** ) or a command that gets **TypeData** objects, such as a `Get-TypeData` command.</span></span> <span data-ttu-id="1c4b4-152">Du kan också skicka pipe- **TypeData** objekt till `Remove-TypeData` .</span><span class="sxs-lookup"><span data-stu-id="1c4b4-152">You can also pipe **TypeData** objects to `Remove-TypeData`.</span></span>

```yaml
Type: System.Management.Automation.Runspaces.TypeData
Parameter Sets: RemoveTypeDataSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="1c4b4-153">-TypeName</span><span class="sxs-lookup"><span data-stu-id="1c4b4-153">-TypeName</span></span>

<span data-ttu-id="1c4b4-154">Anger de typer som denna cmdlet tar bort all utökad typ av data för.</span><span class="sxs-lookup"><span data-stu-id="1c4b4-154">Specifies the types that this cmdlet deletes all extended type data for.</span></span> <span data-ttu-id="1c4b4-155">För typer i system namn området anger du det korta namnet.</span><span class="sxs-lookup"><span data-stu-id="1c4b4-155">For types in the System namespace, enter the short name.</span></span> <span data-ttu-id="1c4b4-156">Annars krävs det fullständiga typ namnet.</span><span class="sxs-lookup"><span data-stu-id="1c4b4-156">Otherwise, the full type name is required.</span></span> <span data-ttu-id="1c4b4-157">Jokertecken stöds inte.</span><span class="sxs-lookup"><span data-stu-id="1c4b4-157">Wildcards are not supported.</span></span>

<span data-ttu-id="1c4b4-158">Du kan skicka pipe-typnamn till `Remove-TypeData` .</span><span class="sxs-lookup"><span data-stu-id="1c4b4-158">You can pipe type names to `Remove-TypeData`.</span></span> <span data-ttu-id="1c4b4-159">När du flyttar ett objekt till `Remove-TypeData` , `Remove-TypeData` hämtar typ namnet för objektet och tar bort alla typ data för objekt typen.</span><span class="sxs-lookup"><span data-stu-id="1c4b4-159">When you pipe an object to `Remove-TypeData`, `Remove-TypeData` gets the type name of the object and removes all type data for the object type.</span></span>

```yaml
Type: System.String
Parameter Sets: RemoveTypeSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="1c4b4-160">-Confirm</span><span class="sxs-lookup"><span data-stu-id="1c4b4-160">-Confirm</span></span>

<span data-ttu-id="1c4b4-161">Uppmanar dig att bekräfta innan du kör cmdleten.</span><span class="sxs-lookup"><span data-stu-id="1c4b4-161">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="1c4b4-162">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="1c4b4-162">-WhatIf</span></span>

<span data-ttu-id="1c4b4-163">Visar vad som skulle hända om cmdleten kördes.</span><span class="sxs-lookup"><span data-stu-id="1c4b4-163">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="1c4b4-164">Cmdleten körs inte.</span><span class="sxs-lookup"><span data-stu-id="1c4b4-164">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="1c4b4-165">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="1c4b4-165">CommonParameters</span></span>

<span data-ttu-id="1c4b4-166">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="1c4b4-166">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="1c4b4-167">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="1c4b4-167">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="1c4b4-168">Indata</span><span class="sxs-lookup"><span data-stu-id="1c4b4-168">Inputs</span></span>

### <span data-ttu-id="1c4b4-169">System. Management. Automation. körnings utrymmen. TypeData</span><span class="sxs-lookup"><span data-stu-id="1c4b4-169">System.Management.Automation.Runspaces.TypeData</span></span>

<span data-ttu-id="1c4b4-170">Du kan skicka pipe **TypeData** -objekt, till exempel de som `Get-TypeData` cmdleten returnerar, till `Remove-TypeData` .</span><span class="sxs-lookup"><span data-stu-id="1c4b4-170">You can pipe **TypeData** object, such as the ones that the `Get-TypeData` cmdlet returns, to `Remove-TypeData`.</span></span>

### <span data-ttu-id="1c4b4-171">System. String</span><span class="sxs-lookup"><span data-stu-id="1c4b4-171">System.String</span></span>

<span data-ttu-id="1c4b4-172">Du kan skicka vidare typ namn till `Remove-TypeData` .</span><span class="sxs-lookup"><span data-stu-id="1c4b4-172">You can pipe the type names to `Remove-TypeData`.</span></span> <span data-ttu-id="1c4b4-173">När du flyttar ett objekt till `Remove-TypeData` , `Remove-TypeData` hämtar typ namnet för objektet och tar bort alla typ data för objekt typen.</span><span class="sxs-lookup"><span data-stu-id="1c4b4-173">When you pipe an object to `Remove-TypeData`, `Remove-TypeData` gets the type name of the object and removes all type data for the object type.</span></span>

## <span data-ttu-id="1c4b4-174">Utdata</span><span class="sxs-lookup"><span data-stu-id="1c4b4-174">Outputs</span></span>

### <span data-ttu-id="1c4b4-175">Inget</span><span class="sxs-lookup"><span data-stu-id="1c4b4-175">None</span></span>

<span data-ttu-id="1c4b4-176">Denna cmdlet genererar inga utdata.</span><span class="sxs-lookup"><span data-stu-id="1c4b4-176">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="1c4b4-177">Kommentarer</span><span class="sxs-lookup"><span data-stu-id="1c4b4-177">Notes</span></span>

<span data-ttu-id="1c4b4-178">`Remove-TypeData` Det går bara att ta bort utökade typ data i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="1c4b4-178">`Remove-TypeData` can remove only the extended type data in the current session.</span></span> <span data-ttu-id="1c4b4-179">Det går inte att ta bort utökade typ data som finns på datorn, men som inte har lagts till i den aktuella sessionen, till exempel utökade typer som har definierats i moduler som inte har importer ATS till den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="1c4b4-179">It cannot remove extended type data that is on the computer, but has not been added to the current session, such as extended types that are defined in modules that have not been imported into the current session.</span></span>

## <span data-ttu-id="1c4b4-180">Relaterade länkar</span><span class="sxs-lookup"><span data-stu-id="1c4b4-180">Related links</span></span>

[<span data-ttu-id="1c4b4-181">Get-TypeData</span><span class="sxs-lookup"><span data-stu-id="1c4b4-181">Get-TypeData</span></span>](Get-TypeData.md)

[<span data-ttu-id="1c4b4-182">Uppdatera – TypeData</span><span class="sxs-lookup"><span data-stu-id="1c4b4-182">Update-TypeData</span></span>](Update-TypeData.md)
