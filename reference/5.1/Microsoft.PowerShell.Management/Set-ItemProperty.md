---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 10/18/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/set-itemproperty?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-ItemProperty
ms.openlocfilehash: 969cb181758dc1ac40b9d8fca2c22fa97f87c693
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93265407"
---
# <span data-ttu-id="6c179-103">Set-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="6c179-103">Set-ItemProperty</span></span>

## <span data-ttu-id="6c179-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="6c179-104">SYNOPSIS</span></span>
<span data-ttu-id="6c179-105">Skapar eller ändrar värdet för en egenskap för ett objekt.</span><span class="sxs-lookup"><span data-stu-id="6c179-105">Creates or changes the value of a property of an item.</span></span>

## <span data-ttu-id="6c179-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="6c179-106">SYNTAX</span></span>

### <span data-ttu-id="6c179-107">propertyValuePathSet (standard)</span><span class="sxs-lookup"><span data-stu-id="6c179-107">propertyValuePathSet (Default)</span></span>

```
Set-ItemProperty [-Path] <String[]> [-Name] <String> [-Value] <Object> [-PassThru] [-Force] [-Filter <String>]
 [-Include <String[]>] [-Exclude <String[]>] [-Credential <PSCredential>] [-WhatIf] [-Confirm]
 [-UseTransaction] [<CommonParameters>]
```

### <span data-ttu-id="6c179-108">propertyPSObjectPathSet</span><span class="sxs-lookup"><span data-stu-id="6c179-108">propertyPSObjectPathSet</span></span>

```
Set-ItemProperty [-Path] <String[]> -InputObject <PSObject> [-PassThru] [-Force] [-Filter <String>]
 [-Include <String[]>] [-Exclude <String[]>] [-Credential <PSCredential>] [-WhatIf] [-Confirm]
 [-UseTransaction] [<CommonParameters>]
```

### <span data-ttu-id="6c179-109">propertyValueLiteralPathSet</span><span class="sxs-lookup"><span data-stu-id="6c179-109">propertyValueLiteralPathSet</span></span>

```
Set-ItemProperty -LiteralPath <String[]> [-Name] <String> [-Value] <Object> [-PassThru] [-Force]
 [-Filter <String>] [-Include <String[]>] [-Exclude <String[]>] [-Credential <PSCredential>] [-WhatIf]
 [-Confirm] [-UseTransaction] [<CommonParameters>]
```

### <span data-ttu-id="6c179-110">propertyPSObjectLiteralPathSet</span><span class="sxs-lookup"><span data-stu-id="6c179-110">propertyPSObjectLiteralPathSet</span></span>

```
Set-ItemProperty -LiteralPath <String[]> -InputObject <PSObject> [-PassThru] [-Force] [-Filter <String>]
 [-Include <String[]>] [-Exclude <String[]>] [-Credential <PSCredential>] [-WhatIf] [-Confirm]
 [-UseTransaction] [<CommonParameters>]
```

## <span data-ttu-id="6c179-111">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="6c179-111">DESCRIPTION</span></span>

<span data-ttu-id="6c179-112">`Set-ItemProperty`Cmdleten ändrar värdet för egenskapen för det angivna objektet.</span><span class="sxs-lookup"><span data-stu-id="6c179-112">The `Set-ItemProperty` cmdlet changes the value of the property of the specified item.</span></span> <span data-ttu-id="6c179-113">Du kan använda cmdleten för att skapa eller ändra egenskaper för objekt.</span><span class="sxs-lookup"><span data-stu-id="6c179-113">You can use the cmdlet to establish or change the properties of items.</span></span> <span data-ttu-id="6c179-114">Du kan till exempel använda `Set-ItemProperty` för att ange värdet för egenskapen **IsReadOnly** för ett fil objekt `$True` .</span><span class="sxs-lookup"><span data-stu-id="6c179-114">For example, you can use `Set-ItemProperty` to set the value of the **IsReadOnly** property of a file object to `$True`.</span></span>

<span data-ttu-id="6c179-115">Du kan också använda `Set-ItemProperty` för att skapa och ändra register värden och data.</span><span class="sxs-lookup"><span data-stu-id="6c179-115">You also use `Set-ItemProperty` to create and change registry values and data.</span></span>
<span data-ttu-id="6c179-116">Du kan till exempel lägga till en ny register post i en nyckel och upprätta eller ändra dess värde.</span><span class="sxs-lookup"><span data-stu-id="6c179-116">For example, you can add a new registry entry to a key and establish or change its value.</span></span>

## <span data-ttu-id="6c179-117">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="6c179-117">EXAMPLES</span></span>

### <span data-ttu-id="6c179-118">Exempel 1: Ange en egenskap för en fil</span><span class="sxs-lookup"><span data-stu-id="6c179-118">Example 1: Set a property of a file</span></span>

<span data-ttu-id="6c179-119">Det här kommandot anger värdet för egenskapen **IsReadOnly** för filen "final.doc" till "true".</span><span class="sxs-lookup"><span data-stu-id="6c179-119">This command sets the value of the **IsReadOnly** property of the "final.doc" file to "true".</span></span> <span data-ttu-id="6c179-120">Den använder **sökvägen** för att ange filen, **namn** för att ange namnet på egenskapen och **värdet** pazrameter för att ange det nya värdet.</span><span class="sxs-lookup"><span data-stu-id="6c179-120">It uses **Path** to specify the file, **Name** to specify the name of the property, and the **Value** pazrameter to specify the new value.</span></span>

<span data-ttu-id="6c179-121">Filen är ett **system. io. fileinfo** -objekt och **IsReadOnly** är bara en av dess egenskaper.</span><span class="sxs-lookup"><span data-stu-id="6c179-121">The file is a **System.IO.FileInfo** object and **IsReadOnly** is just one of its properties.</span></span>
<span data-ttu-id="6c179-122">Om du vill se alla egenskaper skriver du `Get-Item C:\GroupFiles\final.doc | Get-Member -MemberType Property` .</span><span class="sxs-lookup"><span data-stu-id="6c179-122">To see all of the properties, type `Get-Item C:\GroupFiles\final.doc | Get-Member -MemberType Property`.</span></span>

<span data-ttu-id="6c179-123">Den `$true` automatiska variabeln representerar värdet "true".</span><span class="sxs-lookup"><span data-stu-id="6c179-123">The `$true` automatic variable represents a value of "TRUE".</span></span>
<span data-ttu-id="6c179-124">Mer information finns i [about_Automatic_Variables](../Microsoft.PowerShell.Core/About/about_Automatic_Variables.md).</span><span class="sxs-lookup"><span data-stu-id="6c179-124">For more information, see [about_Automatic_Variables](../Microsoft.PowerShell.Core/About/about_Automatic_Variables.md).</span></span>

```powershell
Set-ItemProperty -Path C:\GroupFiles\final.doc -Name IsReadOnly -Value $true
```

### <span data-ttu-id="6c179-125">Exempel 2: skapa en register post och ett värde</span><span class="sxs-lookup"><span data-stu-id="6c179-125">Example 2: Create a registry entry and value</span></span>

<span data-ttu-id="6c179-126">Det här exemplet visar hur du kan använda `Set-ItemProperty` för att skapa en ny register post och tilldela ett värde till posten.</span><span class="sxs-lookup"><span data-stu-id="6c179-126">This example shows how to use `Set-ItemProperty` to create a new registry entry and to assign a value to the entry.</span></span> <span data-ttu-id="6c179-127">Posten "NoOfEmployees" skapas i nyckeln "ContosoCompany" i nyckeln "HKLM\Software" och anger värdet till 823.</span><span class="sxs-lookup"><span data-stu-id="6c179-127">It creates the "NoOfEmployees" entry in the "ContosoCompany" key in "HKLM\Software" key and sets its value to 823.</span></span>

<span data-ttu-id="6c179-128">Eftersom register poster anses vara egenskaper för register nycklarna, som är objekt, använder du `Set-ItemProperty` för att skapa register poster och för att upprätta och ändra deras värden.</span><span class="sxs-lookup"><span data-stu-id="6c179-128">Because registry entries are considered to be properties of the registry keys, which are items, you use `Set-ItemProperty` to create registry entries, and to establish and change their values.</span></span>

<span data-ttu-id="6c179-129">Det första kommandot skapar register posten.</span><span class="sxs-lookup"><span data-stu-id="6c179-129">The first command creates the registry entry.</span></span>
<span data-ttu-id="6c179-130">Den använder **Path** för att ange sökvägen till `HKLM:` enheten och nyckeln "Software\MyCompany".</span><span class="sxs-lookup"><span data-stu-id="6c179-130">It uses **Path** to specify the path of the `HKLM:` drive and the "Software\MyCompany" key.</span></span>
<span data-ttu-id="6c179-131">Kommandot använder **Name** för att ange postnamn och **värde** för att ange ett värde.</span><span class="sxs-lookup"><span data-stu-id="6c179-131">The command uses **Name** to specify the entry name and **Value** to specify a value.</span></span>

<span data-ttu-id="6c179-132">Det andra kommandot använder `Get-ItemProperty` cmdleten för att se den nya register posten.</span><span class="sxs-lookup"><span data-stu-id="6c179-132">The second command uses the `Get-ItemProperty` cmdlet to see the new registry entry.</span></span> <span data-ttu-id="6c179-133">Om du använder `Get-Item` -eller `Get-ChildItem` -cmdletarna visas inte posterna eftersom de är egenskaper för en nyckel, inte objekt eller underordnade objekt.</span><span class="sxs-lookup"><span data-stu-id="6c179-133">If you use the `Get-Item` or `Get-ChildItem` cmdlets, the entries do not appear because they are properties of a key, not items or child items.</span></span>

<span data-ttu-id="6c179-134">Det tredje kommandot ändrar värdet för posten **NoOfEmployees** till 824.</span><span class="sxs-lookup"><span data-stu-id="6c179-134">The third command changes the value of the **NoOfEmployees** entry to 824.</span></span>

<span data-ttu-id="6c179-135">Du kan också använda cmdlet: en `New-ItemProperty` för att skapa register posten och dess värde och sedan använda `Set-ItemProperty` för att ändra värdet.</span><span class="sxs-lookup"><span data-stu-id="6c179-135">You can also use the `New-ItemProperty` cmdlet to create the registry entry and its value and then use `Set-ItemProperty` to change the value.</span></span>

<span data-ttu-id="6c179-136">Om du vill ha mer information om `HKLM:` enheten skriver du `Get-Help Get-PSDrive` .</span><span class="sxs-lookup"><span data-stu-id="6c179-136">For more information about the `HKLM:` drive, type `Get-Help Get-PSDrive`.</span></span>
<span data-ttu-id="6c179-137">Mer information om hur du använder PowerShell för att hantera registret får du genom att skriva `Get-Help Registry` .</span><span class="sxs-lookup"><span data-stu-id="6c179-137">For more information about how to use PowerShell to manage the registry, type `Get-Help Registry`.</span></span>

```powershell
Set-ItemProperty -Path "HKLM:\Software\ContosoCompany" -Name "NoOfEmployees" -Value 823
Get-ItemProperty -Path "HKLM:\Software\ContosoCompany"
```

```output
PSPath        : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\software\contosocompany
PSParentPath  : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\software
PSChildName   : contosocompany
PSDrive       : HKLM
PSProvider    : Microsoft.PowerShell.Core\Registry
NoOfLocations : 2
NoOfEmployees : 823

```

```powershell
Set-ItemProperty -Path "HKLM:\Software\ContosoCompany" -Name "NoOfEmployees" -Value 824
Get-ItemProperty -Path "HKLM:\Software\ContosoCompany"
```

```output
PSPath        : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\software\contosocompany
PSParentPath  : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\software
PSChildName   : contosocompany
PSDrive       : HKLM
PSProvider    : Microsoft.PowerShell.Core\Registry
NoOfLocations : 2
NoOfEmployees : 824
```

### <span data-ttu-id="6c179-138">Exempel 3: ändra ett objekt med hjälp av pipelinen</span><span class="sxs-lookup"><span data-stu-id="6c179-138">Example 3: Modify an item by using the pipeline</span></span>

<span data-ttu-id="6c179-139">De här kommandona visar hur du använder en pipeline-operator ( `|` ) för att skicka ett objekt till `Set-ItemProperty` .</span><span class="sxs-lookup"><span data-stu-id="6c179-139">These commands show how to use a pipeline operator (`|`) to send an item to `Set-ItemProperty`.</span></span>

<span data-ttu-id="6c179-140">Den första delen av kommandot använder `Get-ChildItem` för att hämta ett objekt som representerar "Weekly.txt"-filen.</span><span class="sxs-lookup"><span data-stu-id="6c179-140">The first part of the command uses `Get-ChildItem` to get an object that represents the "Weekly.txt" file.</span></span>
<span data-ttu-id="6c179-141">Kommandot använder en pipeline-operator för att skicka objektet till `Set-ItemProperty` .</span><span class="sxs-lookup"><span data-stu-id="6c179-141">The command uses a pipeline operator to send the file object to `Set-ItemProperty`.</span></span>
<span data-ttu-id="6c179-142">`Set-ItemProperty`Kommandot använder parametrarna **Name** och **Value** för att ange egenskapen och det nya värdet.</span><span class="sxs-lookup"><span data-stu-id="6c179-142">The `Set-ItemProperty` command uses the **Name** and **Value** parameters to specify the property and its new value.</span></span>

<span data-ttu-id="6c179-143">Det här kommandot motsvarar att använda parametern **InputObject** för att ange det objekt som ska `Get-ChildItem` hämtas.</span><span class="sxs-lookup"><span data-stu-id="6c179-143">This command is equivalent to using the **InputObject** parameter to specify the object that `Get-ChildItem` gets.</span></span>

```powershell
Get-ChildItem weekly.txt | Set-ItemProperty -Name IsReadOnly -Value $True
```

## <span data-ttu-id="6c179-144">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="6c179-144">PARAMETERS</span></span>

### <span data-ttu-id="6c179-145">-Credential</span><span class="sxs-lookup"><span data-stu-id="6c179-145">-Credential</span></span>

<span data-ttu-id="6c179-146">Anger ett användar konto som har behörighet att utföra den här åtgärden.</span><span class="sxs-lookup"><span data-stu-id="6c179-146">Specifies a user account that has permission to perform this action.</span></span>
<span data-ttu-id="6c179-147">Standard är den aktuella användaren.</span><span class="sxs-lookup"><span data-stu-id="6c179-147">The default is the current user.</span></span>

<span data-ttu-id="6c179-148">Ange ett användar namn, till exempel "user01" eller "Domain01\User01", eller ange ett **PSCredential** -objekt, t. ex. ett som genererades av `Get-Credential` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="6c179-148">Type a user name, such as "User01" or "Domain01\User01", or enter a **PSCredential** object, such as one generated by the `Get-Credential` cmdlet.</span></span>
<span data-ttu-id="6c179-149">Om du anger ett användar namn uppmanas du att ange ett lösen ord.</span><span class="sxs-lookup"><span data-stu-id="6c179-149">If you type a user name, you are prompted for a password.</span></span>

> [!NOTE]
> <span data-ttu-id="6c179-150">Den här parametern stöds inte av några providrar som installeras med PowerShell.</span><span class="sxs-lookup"><span data-stu-id="6c179-150">This parameter is not supported by any providers installed with PowerShell.</span></span>
> <span data-ttu-id="6c179-151">Om du vill personifiera en annan användare eller öka dina autentiseringsuppgifter när du kör denna cmdlet, använder du [Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md).</span><span class="sxs-lookup"><span data-stu-id="6c179-151">To impersonate another user, or elevate your credentials when running this cmdlet, use [Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md).</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Current user
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="6c179-152">-Undanta</span><span class="sxs-lookup"><span data-stu-id="6c179-152">-Exclude</span></span>

<span data-ttu-id="6c179-153">Anger de objekt som cmdleten inte fungerar på och som innehåller alla andra.</span><span class="sxs-lookup"><span data-stu-id="6c179-153">Specifies those items upon which the cmdlet does not act, and includes all others.</span></span>
<span data-ttu-id="6c179-154">Värdet för den här parametern kvalificerar parametern **Path** .</span><span class="sxs-lookup"><span data-stu-id="6c179-154">The value of this parameter qualifies the **Path** parameter.</span></span>
<span data-ttu-id="6c179-155">Ange ett Sök vägs element eller ett mönster, till exempel "\*. txt".</span><span class="sxs-lookup"><span data-stu-id="6c179-155">Enter a path element or pattern, such as "\*.txt".</span></span>
<span data-ttu-id="6c179-156">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="6c179-156">Wildcard characters are permitted.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="6c179-157">-Filter</span><span class="sxs-lookup"><span data-stu-id="6c179-157">-Filter</span></span>

<span data-ttu-id="6c179-158">Anger ett filter i formatet eller språket för providern.</span><span class="sxs-lookup"><span data-stu-id="6c179-158">Specifies a filter in the format or language of the provider.</span></span>
<span data-ttu-id="6c179-159">Värdet för den här parametern kvalificerar parametern **Path** .</span><span class="sxs-lookup"><span data-stu-id="6c179-159">The value of this parameter qualifies the **Path** parameter.</span></span>

<span data-ttu-id="6c179-160">Syntaxen för filtret, inklusive användning av jokertecken, är beroende av providern.</span><span class="sxs-lookup"><span data-stu-id="6c179-160">The syntax of the filter, including the use of wildcard characters, depends on the provider.</span></span>
<span data-ttu-id="6c179-161">Filter är mer effektiva än andra parametrar, eftersom providern tillämpar dem när cmdleten hämtar objekten i stället för att ha PowerShell filtrera objekten när de har hämtats.</span><span class="sxs-lookup"><span data-stu-id="6c179-161">Filters are more efficient than other parameters, because the provider applies them when the cmdlet gets the objects rather than having PowerShell filter the objects after they are retrieved.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="6c179-162">-Force</span><span class="sxs-lookup"><span data-stu-id="6c179-162">-Force</span></span>

<span data-ttu-id="6c179-163">Tvingar cmdleten att ange en egenskap för objekt som annars inte kan nås av användaren.</span><span class="sxs-lookup"><span data-stu-id="6c179-163">Forces the cmdlet to set a property on items that cannot otherwise be accessed by the user.</span></span>
<span data-ttu-id="6c179-164">Implementeringen varierar från providern till providern.</span><span class="sxs-lookup"><span data-stu-id="6c179-164">Implementation varies from provider to provider.</span></span>
<span data-ttu-id="6c179-165">Mer information finns i [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span><span class="sxs-lookup"><span data-stu-id="6c179-165">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="6c179-166">-Inkludera</span><span class="sxs-lookup"><span data-stu-id="6c179-166">-Include</span></span>

<span data-ttu-id="6c179-167">Anger bara de objekt som cmdleten fungerar på, vilket utesluter alla andra.</span><span class="sxs-lookup"><span data-stu-id="6c179-167">Specifies only those items upon which the cmdlet acts, which excludes all others.</span></span>
<span data-ttu-id="6c179-168">Värdet för den här parametern kvalificerar parametern **Path** .</span><span class="sxs-lookup"><span data-stu-id="6c179-168">The value of this parameter qualifies the **Path** parameter.</span></span>
<span data-ttu-id="6c179-169">Ange ett Sök vägs element eller ett mönster, till exempel "\*. txt".</span><span class="sxs-lookup"><span data-stu-id="6c179-169">Enter a path element or pattern, such as "\*.txt".</span></span>
<span data-ttu-id="6c179-170">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="6c179-170">Wildcard characters are permitted.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="6c179-171">– InputObject</span><span class="sxs-lookup"><span data-stu-id="6c179-171">-InputObject</span></span>

<span data-ttu-id="6c179-172">Anger det objekt som har de egenskaper som denna cmdlet ändrar.</span><span class="sxs-lookup"><span data-stu-id="6c179-172">Specifies the object that has the properties that this cmdlet changes.</span></span>
<span data-ttu-id="6c179-173">Ange en variabel som innehåller objektet eller ett kommando som hämtar objektet.</span><span class="sxs-lookup"><span data-stu-id="6c179-173">Enter a variable that contains the object or a command that gets the object.</span></span>

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: propertyPSObjectPathSet, propertyPSObjectLiteralPathSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="6c179-174">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="6c179-174">-LiteralPath</span></span>

<span data-ttu-id="6c179-175">Anger en sökväg för objekt egenskapen.</span><span class="sxs-lookup"><span data-stu-id="6c179-175">Specifies a path of the item property.</span></span>
<span data-ttu-id="6c179-176">Till skillnad från parametern **Path** används värdet för **LiteralPath** exakt som det har angetts.</span><span class="sxs-lookup"><span data-stu-id="6c179-176">Unlike the **Path** parameter, the value of **LiteralPath** is used exactly as it is typed.</span></span>
<span data-ttu-id="6c179-177">Inga tecken tolkas som jokertecken.</span><span class="sxs-lookup"><span data-stu-id="6c179-177">No characters are interpreted as wildcards.</span></span>
<span data-ttu-id="6c179-178">Om sökvägen innehåller escape-tecken omger du den med enkla citat tecken.</span><span class="sxs-lookup"><span data-stu-id="6c179-178">If the path includes escape characters, enclose it in single quotation marks.</span></span>
<span data-ttu-id="6c179-179">Enkla citat tecken säger att PowerShell inte tolkar några tecken som escape-sekvenser.</span><span class="sxs-lookup"><span data-stu-id="6c179-179">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

```yaml
Type: System.String[]
Parameter Sets: propertyValueLiteralPathSet, propertyPSObjectLiteralPathSet
Aliases: PSPath

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="6c179-180">-Name</span><span class="sxs-lookup"><span data-stu-id="6c179-180">-Name</span></span>

<span data-ttu-id="6c179-181">Anger namnet på egenskapen.</span><span class="sxs-lookup"><span data-stu-id="6c179-181">Specifies the name of the property.</span></span>

```yaml
Type: System.String
Parameter Sets: propertyValuePathSet, propertyValueLiteralPathSet
Aliases: PSProperty

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="6c179-182">– PassThru</span><span class="sxs-lookup"><span data-stu-id="6c179-182">-PassThru</span></span>

<span data-ttu-id="6c179-183">Returnerar ett objekt som representerar egenskapen Item.</span><span class="sxs-lookup"><span data-stu-id="6c179-183">Returns an object that represents the item property.</span></span>
<span data-ttu-id="6c179-184">Som standard genererar denna cmdlet inga utdata.</span><span class="sxs-lookup"><span data-stu-id="6c179-184">By default, this cmdlet does not generate any output.</span></span>

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

### <span data-ttu-id="6c179-185">-Path</span><span class="sxs-lookup"><span data-stu-id="6c179-185">-Path</span></span>

<span data-ttu-id="6c179-186">Anger sökvägen till objekten med egenskapen att ändra.</span><span class="sxs-lookup"><span data-stu-id="6c179-186">Specifies the path of the items with the property to modify.</span></span>

```yaml
Type: System.String[]
Parameter Sets: propertyValuePathSet, propertyPSObjectPathSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="6c179-187">-Typ</span><span class="sxs-lookup"><span data-stu-id="6c179-187">-Type</span></span>

<span data-ttu-id="6c179-188">**Typ** är en dynamisk parameter som Registry-providern lägger till i `Set-ItemProperty` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="6c179-188">**Type** is a dynamic parameter that the Registry provider adds to the `Set-ItemProperty` cmdlet.</span></span>
<span data-ttu-id="6c179-189">Den här parametern fungerar bara i register enheterna.</span><span class="sxs-lookup"><span data-stu-id="6c179-189">This parameter only works in the registry drives.</span></span>

<span data-ttu-id="6c179-190">Anger vilken typ av egenskap som denna cmdlet lägger till.</span><span class="sxs-lookup"><span data-stu-id="6c179-190">Specifies the type of property that this cmdlet adds.</span></span>
<span data-ttu-id="6c179-191">De acceptabla värdena för den här parametern är:</span><span class="sxs-lookup"><span data-stu-id="6c179-191">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="6c179-192">**Sträng** : anger en null-avslutad sträng.</span><span class="sxs-lookup"><span data-stu-id="6c179-192">**String** : Specifies a null-terminated string.</span></span> <span data-ttu-id="6c179-193">Motsvarar **REG_SZ**.</span><span class="sxs-lookup"><span data-stu-id="6c179-193">Equivalent to **REG_SZ**.</span></span>
- <span data-ttu-id="6c179-194">**ExpandString** : anger en null-avslutad sträng som innehåller expanderade referenser till miljövariabler som expanderas när värdet hämtas.</span><span class="sxs-lookup"><span data-stu-id="6c179-194">**ExpandString** : Specifies a null-terminated string that contains unexpanded references to environment variables that are expanded when the value is retrieved.</span></span> <span data-ttu-id="6c179-195">Motsvarar **REG_EXPAND_SZ**.</span><span class="sxs-lookup"><span data-stu-id="6c179-195">Equivalent to **REG_EXPAND_SZ**.</span></span>
- <span data-ttu-id="6c179-196">**Binary** : anger binära data i alla former.</span><span class="sxs-lookup"><span data-stu-id="6c179-196">**Binary** : Specifies binary data in any form.</span></span> <span data-ttu-id="6c179-197">Motsvarar **REG_BINARY**.</span><span class="sxs-lookup"><span data-stu-id="6c179-197">Equivalent to **REG_BINARY**.</span></span>
- <span data-ttu-id="6c179-198">**DWORD** : anger ett 32-bitars binärt tal.</span><span class="sxs-lookup"><span data-stu-id="6c179-198">**DWord** : Specifies a 32-bit binary number.</span></span> <span data-ttu-id="6c179-199">Motsvarar **REG_DWORD**.</span><span class="sxs-lookup"><span data-stu-id="6c179-199">Equivalent to **REG_DWORD**.</span></span>
- <span data-ttu-id="6c179-200">**Multisträng** : anger en matris med null-terminerade strängar som avslutas med två NULL-tecken.</span><span class="sxs-lookup"><span data-stu-id="6c179-200">**MultiString** : Specifies an array of null-terminated strings terminated by two null characters.</span></span>
  <span data-ttu-id="6c179-201">Motsvarar **REG_MULTI_SZ**.</span><span class="sxs-lookup"><span data-stu-id="6c179-201">Equivalent to **REG_MULTI_SZ**.</span></span>
- <span data-ttu-id="6c179-202">**QWORD** : anger ett 64-bitars binärt tal.</span><span class="sxs-lookup"><span data-stu-id="6c179-202">**Qword** : Specifies a 64-bit binary number.</span></span> <span data-ttu-id="6c179-203">Motsvarar **REG_QWORD**.</span><span class="sxs-lookup"><span data-stu-id="6c179-203">Equivalent to **REG_QWORD**.</span></span>
- <span data-ttu-id="6c179-204">**Okänd** : anger en register data typ som inte stöds, till exempel **REG_RESOURCE_LIST**.</span><span class="sxs-lookup"><span data-stu-id="6c179-204">**Unknown** : Indicates an unsupported registry data type, such as **REG_RESOURCE_LIST**.</span></span>

```yaml
Type: RegistryValueKind
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="6c179-205">– UseTransaction</span><span class="sxs-lookup"><span data-stu-id="6c179-205">-UseTransaction</span></span>

<span data-ttu-id="6c179-206">Inkluderar kommandot i den aktiva transaktionen.</span><span class="sxs-lookup"><span data-stu-id="6c179-206">Includes the command in the active transaction.</span></span>
<span data-ttu-id="6c179-207">Den här parametern är bara giltig medan en transaktion pågår.</span><span class="sxs-lookup"><span data-stu-id="6c179-207">This parameter is valid only when a transaction is in progress.</span></span>
<span data-ttu-id="6c179-208">Mer information finns i [about_Transactions](../Microsoft.PowerShell.Core/About/about_Transactions.md).</span><span class="sxs-lookup"><span data-stu-id="6c179-208">For more information, see [about_Transactions](../Microsoft.PowerShell.Core/About/about_Transactions.md).</span></span>

```yaml
Type: SwitchParameter
Parameter Sets: (All)
Aliases: usetx

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="6c179-209">-Värde</span><span class="sxs-lookup"><span data-stu-id="6c179-209">-Value</span></span>

<span data-ttu-id="6c179-210">Anger egenskapens värde.</span><span class="sxs-lookup"><span data-stu-id="6c179-210">Specifies the value of the property.</span></span>

```yaml
Type: Object
Parameter Sets: propertyValuePathSet, propertyValueLiteralPathSet
Aliases:

Required: True
Position: 2
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="6c179-211">-Confirm</span><span class="sxs-lookup"><span data-stu-id="6c179-211">-Confirm</span></span>

<span data-ttu-id="6c179-212">Uppmanar dig att bekräfta innan du kör cmdleten.</span><span class="sxs-lookup"><span data-stu-id="6c179-212">Prompts you for confirmation before running the cmdlet.</span></span>

```yaml
Type: SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="6c179-213">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="6c179-213">-WhatIf</span></span>

<span data-ttu-id="6c179-214">Visar vad som skulle hända om cmdleten kördes.</span><span class="sxs-lookup"><span data-stu-id="6c179-214">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="6c179-215">Cmdleten körs inte.</span><span class="sxs-lookup"><span data-stu-id="6c179-215">The cmdlet is not run.</span></span>

```yaml
Type: SwitchParameter
Parameter Sets: (All)
Aliases: wi

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="6c179-216">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="6c179-216">CommonParameters</span></span>

<span data-ttu-id="6c179-217">Denna cmdlet stöder de gemensamma parametrarna:,,,,,,,, `-Debug` `-ErrorAction` `-ErrorVariable` `-InformationAction` `-InformationVariable` `-OutVariable` `-OutBuffer` `-PipelineVariable` `-Verbose` `-WarningAction` , och `-WarningVariable` .</span><span class="sxs-lookup"><span data-stu-id="6c179-217">This cmdlet supports the common parameters: `-Debug`, `-ErrorAction`, `-ErrorVariable`, `-InformationAction`, `-InformationVariable`, `-OutVariable`, `-OutBuffer`, `-PipelineVariable`, `-Verbose`, `-WarningAction`, and `-WarningVariable`.</span></span> <span data-ttu-id="6c179-218">Mer information finns i [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span><span class="sxs-lookup"><span data-stu-id="6c179-218">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="6c179-219">INDATA</span><span class="sxs-lookup"><span data-stu-id="6c179-219">INPUTS</span></span>

### <span data-ttu-id="6c179-220">System. Management. Automation. PSObject</span><span class="sxs-lookup"><span data-stu-id="6c179-220">System.Management.Automation.PSObject</span></span>

<span data-ttu-id="6c179-221">Du kan skicka pipe-objekt till denna cmdlet.</span><span class="sxs-lookup"><span data-stu-id="6c179-221">You can pipe objects to this cmdlet.</span></span>

## <span data-ttu-id="6c179-222">UTDATA</span><span class="sxs-lookup"><span data-stu-id="6c179-222">OUTPUTS</span></span>

### <span data-ttu-id="6c179-223">Ingen, system. Management. Automation. PSCustomObject</span><span class="sxs-lookup"><span data-stu-id="6c179-223">None, System.Management.Automation.PSCustomObject</span></span>

<span data-ttu-id="6c179-224">Denna cmdlet genererar ett **PSCustomObject** -objekt som representerar objektet som ändrades och dess nya egenskaps värde, om du anger parametern **Passthru** .</span><span class="sxs-lookup"><span data-stu-id="6c179-224">This cmdlet generates a **PSCustomObject** object that represents the item that was changed and its new property value, if you specify the **PassThru** parameter.</span></span> <span data-ttu-id="6c179-225">Annars genererar denna cmdlet inga utdata.</span><span class="sxs-lookup"><span data-stu-id="6c179-225">Otherwise, this cmdlet does not generate any output.</span></span>

## <span data-ttu-id="6c179-226">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="6c179-226">NOTES</span></span>

<span data-ttu-id="6c179-227">`Set-ItemProperty` är utformad för att fungera med data som exponeras av vilken provider som helst.</span><span class="sxs-lookup"><span data-stu-id="6c179-227">`Set-ItemProperty` is designed to work with the data exposed by any provider.</span></span> <span data-ttu-id="6c179-228">Om du vill visa en lista över tillgängliga providers i din session skriver du `Get-PSProvider` .</span><span class="sxs-lookup"><span data-stu-id="6c179-228">To list the providers available in your session, type `Get-PSProvider`.</span></span> <span data-ttu-id="6c179-229">Mer information finns i [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span><span class="sxs-lookup"><span data-stu-id="6c179-229">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

## <span data-ttu-id="6c179-230">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="6c179-230">RELATED LINKS</span></span>

[<span data-ttu-id="6c179-231">Clear-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="6c179-231">Clear-ItemProperty</span></span>](Clear-ItemProperty.md)

[<span data-ttu-id="6c179-232">Kopiera – ItemProperty</span><span class="sxs-lookup"><span data-stu-id="6c179-232">Copy-ItemProperty</span></span>](Copy-ItemProperty.md)

[<span data-ttu-id="6c179-233">Get-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="6c179-233">Get-ItemProperty</span></span>](Get-ItemProperty.md)

[<span data-ttu-id="6c179-234">Move-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="6c179-234">Move-ItemProperty</span></span>](Move-ItemProperty.md)

[<span data-ttu-id="6c179-235">New-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="6c179-235">New-ItemProperty</span></span>](New-ItemProperty.md)

[<span data-ttu-id="6c179-236">Remove-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="6c179-236">Remove-ItemProperty</span></span>](Remove-ItemProperty.md)

[<span data-ttu-id="6c179-237">Byt namn – ItemProperty</span><span class="sxs-lookup"><span data-stu-id="6c179-237">Rename-ItemProperty</span></span>](Rename-ItemProperty.md)
