---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 05/14/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/set-itemproperty?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-ItemProperty
ms.openlocfilehash: 18383dc2b1e018e56864e412dfe75eca2b578a08
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94710423"
---
# <span data-ttu-id="f6271-102">Set-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="f6271-102">Set-ItemProperty</span></span>

## <span data-ttu-id="f6271-103">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="f6271-103">SYNOPSIS</span></span>
<span data-ttu-id="f6271-104">Skapar eller ändrar värdet för en egenskap för ett objekt.</span><span class="sxs-lookup"><span data-stu-id="f6271-104">Creates or changes the value of a property of an item.</span></span>

## <span data-ttu-id="f6271-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="f6271-105">SYNTAX</span></span>

### <span data-ttu-id="f6271-106">propertyValuePathSet (standard)</span><span class="sxs-lookup"><span data-stu-id="f6271-106">propertyValuePathSet (Default)</span></span>

```
Set-ItemProperty [-Path] <String[]> [-Name] <String> [-Value] <Object> [-PassThru] [-Force] [-Filter <String>]
 [-Include <String[]>] [-Exclude <String[]>] [-Credential <PSCredential>]
 [-WhatIf] [-Confirm] [-Type <RegistryValueKind>] [<CommonParameters>]
```

### <span data-ttu-id="f6271-107">propertyPSObjectPathSet</span><span class="sxs-lookup"><span data-stu-id="f6271-107">propertyPSObjectPathSet</span></span>

```
Set-ItemProperty [-Path] <String[]> -InputObject <PSObject> [-PassThru] [-Force] [-Filter <String>]
 [-Include <String[]>] [-Exclude <String[]>] [-Credential <PSCredential>]
 [-WhatIf] [-Confirm] [-Type <RegistryValueKind>] [<CommonParameters>]
```

### <span data-ttu-id="f6271-108">propertyValueLiteralPathSet</span><span class="sxs-lookup"><span data-stu-id="f6271-108">propertyValueLiteralPathSet</span></span>

```
Set-ItemProperty -LiteralPath <String[]> [-Name] <String> [-Value] <Object> [-PassThru] [-Force]
 [-Filter <String>] [-Include <String[]>] [-Exclude <String[]>] [-Credential <PSCredential>]
 [-WhatIf] [-Confirm] [-Type <RegistryValueKind>] [<CommonParameters>]
```

### <span data-ttu-id="f6271-109">propertyPSObjectLiteralPathSet</span><span class="sxs-lookup"><span data-stu-id="f6271-109">propertyPSObjectLiteralPathSet</span></span>

```
Set-ItemProperty -LiteralPath <String[]> -InputObject <PSObject> [-PassThru] [-Force] [-Filter <String>]
 [-Include <String[]>] [-Exclude <String[]>] [-Credential <PSCredential>]
 [-WhatIf] [-Confirm] [-Type <RegistryValueKind>] [<CommonParameters>]
```

## <span data-ttu-id="f6271-110">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="f6271-110">DESCRIPTION</span></span>

<span data-ttu-id="f6271-111">`Set-ItemProperty`Cmdleten ändrar värdet för egenskapen för det angivna objektet.</span><span class="sxs-lookup"><span data-stu-id="f6271-111">The `Set-ItemProperty` cmdlet changes the value of the property of the specified item.</span></span>
<span data-ttu-id="f6271-112">Du kan använda cmdleten för att skapa eller ändra egenskaper för objekt.</span><span class="sxs-lookup"><span data-stu-id="f6271-112">You can use the cmdlet to establish or change the properties of items.</span></span>
<span data-ttu-id="f6271-113">Du kan till exempel använda `Set-ItemProperty` för att ange värdet för egenskapen **IsReadOnly** för ett fil objekt `$True` .</span><span class="sxs-lookup"><span data-stu-id="f6271-113">For example, you can use `Set-ItemProperty` to set the value of the **IsReadOnly** property of a file object to `$True`.</span></span>

<span data-ttu-id="f6271-114">Du kan också använda `Set-ItemProperty` för att skapa och ändra register värden och data.</span><span class="sxs-lookup"><span data-stu-id="f6271-114">You also use `Set-ItemProperty` to create and change registry values and data.</span></span>
<span data-ttu-id="f6271-115">Du kan till exempel lägga till en ny register post i en nyckel och upprätta eller ändra dess värde.</span><span class="sxs-lookup"><span data-stu-id="f6271-115">For example, you can add a new registry entry to a key and establish or change its value.</span></span>

## <span data-ttu-id="f6271-116">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="f6271-116">EXAMPLES</span></span>

### <span data-ttu-id="f6271-117">Exempel 1: Ange en egenskap för en fil</span><span class="sxs-lookup"><span data-stu-id="f6271-117">Example 1: Set a property of a file</span></span>

<span data-ttu-id="f6271-118">Det här kommandot anger värdet för egenskapen **IsReadOnly** för filen "final.doc" till "true".</span><span class="sxs-lookup"><span data-stu-id="f6271-118">This command sets the value of the **IsReadOnly** property of the "final.doc" file to "true".</span></span>
<span data-ttu-id="f6271-119">Den använder **sökvägen** för att ange filen, **namn** för att ange namnet på egenskapen och **värdet** parameter för att ange det nya värdet.</span><span class="sxs-lookup"><span data-stu-id="f6271-119">It uses **Path** to specify the file, **Name** to specify the name of the property, and the **Value** parameter to specify the new value.</span></span>

<span data-ttu-id="f6271-120">Filen är ett **system. io. fileinfo** -objekt och **IsReadOnly** är bara en av dess egenskaper.</span><span class="sxs-lookup"><span data-stu-id="f6271-120">The file is a **System.IO.FileInfo** object and **IsReadOnly** is just one of its properties.</span></span>
<span data-ttu-id="f6271-121">Om du vill se alla egenskaper skriver du `Get-Item C:\GroupFiles\final.doc | Get-Member -MemberType
Property` .</span><span class="sxs-lookup"><span data-stu-id="f6271-121">To see all of the properties, type `Get-Item C:\GroupFiles\final.doc | Get-Member -MemberType
Property`.</span></span>

<span data-ttu-id="f6271-122">Den `$true` automatiska variabeln representerar värdet "true".</span><span class="sxs-lookup"><span data-stu-id="f6271-122">The `$true` automatic variable represents a value of "TRUE".</span></span>
<span data-ttu-id="f6271-123">Mer information finns i [about_Automatic_Variables](../Microsoft.PowerShell.Core/About/about_Automatic_Variables.md).</span><span class="sxs-lookup"><span data-stu-id="f6271-123">For more information, see [about_Automatic_Variables](../Microsoft.PowerShell.Core/About/about_Automatic_Variables.md).</span></span>

```powershell
Set-ItemProperty -Path C:\GroupFiles\final.doc -Name IsReadOnly -Value $true
```

### <span data-ttu-id="f6271-124">Exempel 2: skapa en register post och ett värde</span><span class="sxs-lookup"><span data-stu-id="f6271-124">Example 2: Create a registry entry and value</span></span>

<span data-ttu-id="f6271-125">Det här exemplet visar hur du kan använda `Set-ItemProperty` för att skapa en ny register post och tilldela ett värde till posten.</span><span class="sxs-lookup"><span data-stu-id="f6271-125">This example shows how to use `Set-ItemProperty` to create a new registry entry and to assign a value to the entry.</span></span> <span data-ttu-id="f6271-126">Posten "NoOfEmployees" skapas i nyckeln "ContosoCompany" i `HKLM\Software` nyckeln och värdet anges till 823.</span><span class="sxs-lookup"><span data-stu-id="f6271-126">It creates the "NoOfEmployees" entry in the "ContosoCompany" key in `HKLM\Software` key and sets its value to 823.</span></span>

<span data-ttu-id="f6271-127">Eftersom register poster anses vara egenskaper för register nycklarna, som är objekt, använder du `Set-ItemProperty` för att skapa register poster och för att upprätta och ändra deras värden.</span><span class="sxs-lookup"><span data-stu-id="f6271-127">Because registry entries are considered to be properties of the registry keys, which are items, you use `Set-ItemProperty` to create registry entries, and to establish and change their values.</span></span>

```powershell
Set-ItemProperty -Path "HKLM:\Software\ContosoCompany" -Name "NoOfEmployees" -Value 823
Get-ItemProperty -Path "HKLM:\Software\ContosoCompany"
```

```Output
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

```Output
PSPath        : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\software\contosocompany
PSParentPath  : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\software
PSChildName   : contosocompany
PSDrive       : HKLM
PSProvider    : Microsoft.PowerShell.Core\Registry
NoOfLocations : 2
NoOfEmployees : 824
```

<span data-ttu-id="f6271-128">Det första kommandot skapar register posten.</span><span class="sxs-lookup"><span data-stu-id="f6271-128">The first command creates the registry entry.</span></span>
<span data-ttu-id="f6271-129">Den använder **Path** för att ange sökvägen till `HKLM:` enheten och nyckeln "Software\MyCompany".</span><span class="sxs-lookup"><span data-stu-id="f6271-129">It uses **Path** to specify the path of the `HKLM:` drive and the "Software\MyCompany" key.</span></span>
<span data-ttu-id="f6271-130">Kommandot använder **Name** för att ange postnamn och **värde** för att ange ett värde.</span><span class="sxs-lookup"><span data-stu-id="f6271-130">The command uses **Name** to specify the entry name and **Value** to specify a value.</span></span>

<span data-ttu-id="f6271-131">Det andra kommandot använder `Get-ItemProperty` cmdleten för att se den nya register posten.</span><span class="sxs-lookup"><span data-stu-id="f6271-131">The second command uses the `Get-ItemProperty` cmdlet to see the new registry entry.</span></span>
<span data-ttu-id="f6271-132">Om du använder `Get-Item` -eller `Get-ChildItem` -cmdletarna visas inte posterna eftersom de är egenskaper för en nyckel, inte objekt eller underordnade objekt.</span><span class="sxs-lookup"><span data-stu-id="f6271-132">If you use the `Get-Item` or `Get-ChildItem` cmdlets, the entries do not appear because they are properties of a key, not items or child items.</span></span>

<span data-ttu-id="f6271-133">Det tredje kommandot ändrar värdet för posten **NoOfEmployees** till 824.</span><span class="sxs-lookup"><span data-stu-id="f6271-133">The third command changes the value of the **NoOfEmployees** entry to 824.</span></span>

<span data-ttu-id="f6271-134">Du kan också använda cmdlet: en `New-ItemProperty` för att skapa register posten och dess värde och sedan använda `Set-ItemProperty` för att ändra värdet.</span><span class="sxs-lookup"><span data-stu-id="f6271-134">You can also use the `New-ItemProperty` cmdlet to create the registry entry and its value and then use `Set-ItemProperty` to change the value.</span></span>

<span data-ttu-id="f6271-135">Om du vill ha mer information om `HKLM:` enheten skriver du `Get-Help Get-PSDrive` .</span><span class="sxs-lookup"><span data-stu-id="f6271-135">For more information about the `HKLM:` drive, type `Get-Help Get-PSDrive`.</span></span>
<span data-ttu-id="f6271-136">Mer information om hur du använder PowerShell för att hantera registret får du genom att skriva `Get-Help Registry` .</span><span class="sxs-lookup"><span data-stu-id="f6271-136">For more information about how to use PowerShell to manage the registry, type `Get-Help Registry`.</span></span>

### <span data-ttu-id="f6271-137">Exempel 3: ändra ett objekt med hjälp av pipelinen</span><span class="sxs-lookup"><span data-stu-id="f6271-137">Example 3: Modify an item by using the pipeline</span></span>

<span data-ttu-id="f6271-138">De här kommandona visar hur du använder en pipeline-operator ( `|` ) för att skicka ett objekt till `Set-ItemProperty` .</span><span class="sxs-lookup"><span data-stu-id="f6271-138">These commands show how to use a pipeline operator (`|`) to send an item to `Set-ItemProperty`.</span></span>

<span data-ttu-id="f6271-139">Den första delen av kommandot använder `Get-ChildItem` för att hämta ett objekt som representerar "Weekly.txt"-filen.</span><span class="sxs-lookup"><span data-stu-id="f6271-139">The first part of the command uses `Get-ChildItem` to get an object that represents the "Weekly.txt" file.</span></span> <span data-ttu-id="f6271-140">Kommandot använder en pipeline-operator för att skicka objektet till `Set-ItemProperty` .</span><span class="sxs-lookup"><span data-stu-id="f6271-140">The command uses a pipeline operator to send the file object to `Set-ItemProperty`.</span></span>
<span data-ttu-id="f6271-141">`Set-ItemProperty`Kommandot använder parametrarna **Name** och **Value** för att ange egenskapen och det nya värdet.</span><span class="sxs-lookup"><span data-stu-id="f6271-141">The `Set-ItemProperty` command uses the **Name** and **Value** parameters to specify the property and its new value.</span></span>

<span data-ttu-id="f6271-142">Det här kommandot motsvarar att använda parametern **InputObject** för att ange det objekt som ska `Get-ChildItem` hämtas.</span><span class="sxs-lookup"><span data-stu-id="f6271-142">This command is equivalent to using the **InputObject** parameter to specify the object that `Get-ChildItem` gets.</span></span>

```powershell
Get-ChildItem weekly.txt | Set-ItemProperty -Name IsReadOnly -Value $True
```

## <span data-ttu-id="f6271-143">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="f6271-143">PARAMETERS</span></span>

### <span data-ttu-id="f6271-144">-Credential</span><span class="sxs-lookup"><span data-stu-id="f6271-144">-Credential</span></span>

> [!NOTE]
> <span data-ttu-id="f6271-145">Den här parametern stöds inte av några providrar som installeras med PowerShell.</span><span class="sxs-lookup"><span data-stu-id="f6271-145">This parameter is not supported by any providers installed with PowerShell.</span></span>
> <span data-ttu-id="f6271-146">Om du vill personifiera en annan användare eller öka dina autentiseringsuppgifter när du kör denna cmdlet, använder du [Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md).</span><span class="sxs-lookup"><span data-stu-id="f6271-146">To impersonate another user, or elevate your credentials when running this cmdlet, use [Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md).</span></span>

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

### <span data-ttu-id="f6271-147">-Undanta</span><span class="sxs-lookup"><span data-stu-id="f6271-147">-Exclude</span></span>

<span data-ttu-id="f6271-148">Anger, som en sträng mat ris, ett objekt eller objekt som denna cmdlet exkluderar i åtgärden.</span><span class="sxs-lookup"><span data-stu-id="f6271-148">Specifies, as a string array, an item or items that this cmdlet excludes in the operation.</span></span> <span data-ttu-id="f6271-149">Värdet för den här parametern kvalificerar parametern **Path** .</span><span class="sxs-lookup"><span data-stu-id="f6271-149">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="f6271-150">Ange ett Sök vägs element eller ett mönster, till exempel `*.txt` .</span><span class="sxs-lookup"><span data-stu-id="f6271-150">Enter a path element or pattern, such as `*.txt`.</span></span> <span data-ttu-id="f6271-151">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="f6271-151">Wildcard characters are permitted.</span></span> <span data-ttu-id="f6271-152">Parametern **exclude** är endast effektiv när kommandot innehåller innehållet i ett objekt, t. ex `C:\Windows\*` ., där jokertecknet anger innehållet i `C:\Windows` katalogen.</span><span class="sxs-lookup"><span data-stu-id="f6271-152">The **Exclude** parameter is effective only when the command includes the contents of an item, such as `C:\Windows\*`, where the wildcard character specifies the contents of the `C:\Windows` directory.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="f6271-153">-Filter</span><span class="sxs-lookup"><span data-stu-id="f6271-153">-Filter</span></span>

<span data-ttu-id="f6271-154">Anger ett filter för att kvalificera **Sök vägs** parametern.</span><span class="sxs-lookup"><span data-stu-id="f6271-154">Specifies a filter to qualify the **Path** parameter.</span></span> <span data-ttu-id="f6271-155">[Fil Systems](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md) leverantören är den enda installerade PowerShell-providern som stöder användningen av filter.</span><span class="sxs-lookup"><span data-stu-id="f6271-155">The [FileSystem](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md) provider is the only installed PowerShell provider that supports the use of filters.</span></span> <span data-ttu-id="f6271-156">Du kan hitta syntaxen för filter språket för **fil systemet** i [about_Wildcards](../Microsoft.PowerShell.Core/About/about_Wildcards.md).</span><span class="sxs-lookup"><span data-stu-id="f6271-156">You can find the syntax for the **FileSystem** filter language in [about_Wildcards](../Microsoft.PowerShell.Core/About/about_Wildcards.md).</span></span>
<span data-ttu-id="f6271-157">Filter är mer effektiva än andra parametrar, eftersom providern tillämpar dem när cmdleten hämtar objekten i stället för att ha PowerShell filtrera objekten när de har hämtats.</span><span class="sxs-lookup"><span data-stu-id="f6271-157">Filters are more efficient than other parameters, because the provider applies them when the cmdlet gets the objects rather than having PowerShell filter the objects after they are retrieved.</span></span>

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

### <span data-ttu-id="f6271-158">-Force</span><span class="sxs-lookup"><span data-stu-id="f6271-158">-Force</span></span>

<span data-ttu-id="f6271-159">Tvingar cmdleten att ange en egenskap för objekt som annars inte kan nås av användaren.</span><span class="sxs-lookup"><span data-stu-id="f6271-159">Forces the cmdlet to set a property on items that cannot otherwise be accessed by the user.</span></span>
<span data-ttu-id="f6271-160">Implementeringen varierar från providern till providern.</span><span class="sxs-lookup"><span data-stu-id="f6271-160">Implementation varies from provider to provider.</span></span>
<span data-ttu-id="f6271-161">Mer information finns i [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span><span class="sxs-lookup"><span data-stu-id="f6271-161">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

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

### <span data-ttu-id="f6271-162">-Inkludera</span><span class="sxs-lookup"><span data-stu-id="f6271-162">-Include</span></span>

<span data-ttu-id="f6271-163">Anger, som en sträng mat ris, ett objekt eller objekt som denna cmdlet inkluderar i åtgärden.</span><span class="sxs-lookup"><span data-stu-id="f6271-163">Specifies, as a string array, an item or items that this cmdlet includes in the operation.</span></span> <span data-ttu-id="f6271-164">Värdet för den här parametern kvalificerar parametern **Path** .</span><span class="sxs-lookup"><span data-stu-id="f6271-164">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="f6271-165">Ange ett Sök vägs element eller ett mönster, till exempel `"*.txt"` .</span><span class="sxs-lookup"><span data-stu-id="f6271-165">Enter a path element or pattern, such as `"*.txt"`.</span></span> <span data-ttu-id="f6271-166">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="f6271-166">Wildcard characters are permitted.</span></span> <span data-ttu-id="f6271-167">Parametern **include** är endast effektiv när kommandot innehåller innehållet i ett objekt, t. ex `C:\Windows\*` ., där jokertecknet anger innehållet i `C:\Windows` katalogen.</span><span class="sxs-lookup"><span data-stu-id="f6271-167">The **Include** parameter is effective only when the command includes the contents of an item, such as `C:\Windows\*`, where the wildcard character specifies the contents of the `C:\Windows` directory.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="f6271-168">– InputObject</span><span class="sxs-lookup"><span data-stu-id="f6271-168">-InputObject</span></span>

<span data-ttu-id="f6271-169">Anger det objekt som har de egenskaper som denna cmdlet ändrar.</span><span class="sxs-lookup"><span data-stu-id="f6271-169">Specifies the object that has the properties that this cmdlet changes.</span></span>
<span data-ttu-id="f6271-170">Ange en variabel som innehåller objektet eller ett kommando som hämtar objektet.</span><span class="sxs-lookup"><span data-stu-id="f6271-170">Enter a variable that contains the object or a command that gets the object.</span></span>

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

### <span data-ttu-id="f6271-171">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="f6271-171">-LiteralPath</span></span>

<span data-ttu-id="f6271-172">Anger en sökväg till en eller flera platser.</span><span class="sxs-lookup"><span data-stu-id="f6271-172">Specifies a path to one or more locations.</span></span> <span data-ttu-id="f6271-173">Värdet för **LiteralPath** används exakt som det har angetts.</span><span class="sxs-lookup"><span data-stu-id="f6271-173">The value of **LiteralPath** is used exactly as it is typed.</span></span> <span data-ttu-id="f6271-174">Inga tecken tolkas som jokertecken.</span><span class="sxs-lookup"><span data-stu-id="f6271-174">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="f6271-175">Om sökvägen innehåller escape-tecken omger du den med enkla citat tecken.</span><span class="sxs-lookup"><span data-stu-id="f6271-175">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="f6271-176">Enkla citat tecken säger att PowerShell inte tolkar några tecken som escape-sekvenser.</span><span class="sxs-lookup"><span data-stu-id="f6271-176">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

<span data-ttu-id="f6271-177">Mer information finns i [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md).</span><span class="sxs-lookup"><span data-stu-id="f6271-177">For more information, see [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md).</span></span>

```yaml
Type: System.String[]
Parameter Sets: propertyValueLiteralPathSet, propertyPSObjectLiteralPathSet
Aliases: PSPath, LP

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="f6271-178">-Name</span><span class="sxs-lookup"><span data-stu-id="f6271-178">-Name</span></span>

<span data-ttu-id="f6271-179">Anger namnet på egenskapen.</span><span class="sxs-lookup"><span data-stu-id="f6271-179">Specifies the name of the property.</span></span>

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

### <span data-ttu-id="f6271-180">– PassThru</span><span class="sxs-lookup"><span data-stu-id="f6271-180">-PassThru</span></span>

<span data-ttu-id="f6271-181">Returnerar ett objekt som representerar egenskapen Item.</span><span class="sxs-lookup"><span data-stu-id="f6271-181">Returns an object that represents the item property.</span></span>
<span data-ttu-id="f6271-182">Som standard genererar denna cmdlet inga utdata.</span><span class="sxs-lookup"><span data-stu-id="f6271-182">By default, this cmdlet does not generate any output.</span></span>

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

### <span data-ttu-id="f6271-183">-Path</span><span class="sxs-lookup"><span data-stu-id="f6271-183">-Path</span></span>

<span data-ttu-id="f6271-184">Anger sökvägen till objekten med egenskapen att ändra.</span><span class="sxs-lookup"><span data-stu-id="f6271-184">Specifies the path of the items with the property to modify.</span></span>
<span data-ttu-id="f6271-185">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="f6271-185">Wildcard characters are permitted.</span></span>

```yaml
Type: System.String[]
Parameter Sets: propertyValuePathSet, propertyPSObjectPathSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### <span data-ttu-id="f6271-186">-Typ</span><span class="sxs-lookup"><span data-stu-id="f6271-186">-Type</span></span>

<span data-ttu-id="f6271-187">**Typ** är en dynamisk parameter som Registry-providern lägger till i `Set-ItemProperty` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="f6271-187">**Type** is a dynamic parameter that the Registry provider adds to the `Set-ItemProperty` cmdlet.</span></span>
<span data-ttu-id="f6271-188">Den här parametern fungerar bara i register enheterna.</span><span class="sxs-lookup"><span data-stu-id="f6271-188">This parameter only works in the registry drives.</span></span>

<span data-ttu-id="f6271-189">Anger vilken typ av egenskap som denna cmdlet lägger till.</span><span class="sxs-lookup"><span data-stu-id="f6271-189">Specifies the type of property that this cmdlet adds.</span></span>
<span data-ttu-id="f6271-190">De acceptabla värdena för den här parametern är:</span><span class="sxs-lookup"><span data-stu-id="f6271-190">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="f6271-191">**Sträng**: anger en null-avslutad sträng.</span><span class="sxs-lookup"><span data-stu-id="f6271-191">**String**: Specifies a null-terminated string.</span></span> <span data-ttu-id="f6271-192">Motsvarar **REG_SZ**.</span><span class="sxs-lookup"><span data-stu-id="f6271-192">Equivalent to **REG_SZ**.</span></span>
- <span data-ttu-id="f6271-193">**ExpandString**: anger en null-avslutad sträng som innehåller expanderade referenser till miljövariabler som expanderas när värdet hämtas.</span><span class="sxs-lookup"><span data-stu-id="f6271-193">**ExpandString**: Specifies a null-terminated string that contains unexpanded references to environment variables that are expanded when the value is retrieved.</span></span> <span data-ttu-id="f6271-194">Motsvarar **REG_EXPAND_SZ**.</span><span class="sxs-lookup"><span data-stu-id="f6271-194">Equivalent to **REG_EXPAND_SZ**.</span></span>
- <span data-ttu-id="f6271-195">**Binary**: anger binära data i alla former.</span><span class="sxs-lookup"><span data-stu-id="f6271-195">**Binary**: Specifies binary data in any form.</span></span> <span data-ttu-id="f6271-196">Motsvarar **REG_BINARY**.</span><span class="sxs-lookup"><span data-stu-id="f6271-196">Equivalent to **REG_BINARY**.</span></span>
- <span data-ttu-id="f6271-197">**DWORD**: anger ett 32-bitars binärt tal.</span><span class="sxs-lookup"><span data-stu-id="f6271-197">**DWord**: Specifies a 32-bit binary number.</span></span> <span data-ttu-id="f6271-198">Motsvarar **REG_DWORD**.</span><span class="sxs-lookup"><span data-stu-id="f6271-198">Equivalent to **REG_DWORD**.</span></span>
- <span data-ttu-id="f6271-199">**Multisträng**: anger en matris med null-terminerade strängar som avslutas med två NULL-tecken.</span><span class="sxs-lookup"><span data-stu-id="f6271-199">**MultiString**: Specifies an array of null-terminated strings terminated by two null characters.</span></span>
  <span data-ttu-id="f6271-200">Motsvarar **REG_MULTI_SZ**.</span><span class="sxs-lookup"><span data-stu-id="f6271-200">Equivalent to **REG_MULTI_SZ**.</span></span>
- <span data-ttu-id="f6271-201">**QWORD**: anger ett 64-bitars binärt tal.</span><span class="sxs-lookup"><span data-stu-id="f6271-201">**Qword**: Specifies a 64-bit binary number.</span></span> <span data-ttu-id="f6271-202">Motsvarar **REG_QWORD**.</span><span class="sxs-lookup"><span data-stu-id="f6271-202">Equivalent to **REG_QWORD**.</span></span>
- <span data-ttu-id="f6271-203">**Okänd**: anger en register data typ som inte stöds, till exempel **REG_RESOURCE_LIST**.</span><span class="sxs-lookup"><span data-stu-id="f6271-203">**Unknown**: Indicates an unsupported registry data type, such as **REG_RESOURCE_LIST**.</span></span>

```yaml
Type: Microsoft.Win32.RegistryValueKind
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="f6271-204">-Värde</span><span class="sxs-lookup"><span data-stu-id="f6271-204">-Value</span></span>

<span data-ttu-id="f6271-205">Anger egenskapens värde.</span><span class="sxs-lookup"><span data-stu-id="f6271-205">Specifies the value of the property.</span></span>

```yaml
Type: System.Object
Parameter Sets: propertyValuePathSet, propertyValueLiteralPathSet
Aliases:

Required: True
Position: 2
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="f6271-206">-Confirm</span><span class="sxs-lookup"><span data-stu-id="f6271-206">-Confirm</span></span>

<span data-ttu-id="f6271-207">Uppmanar dig att bekräfta innan du kör cmdleten.</span><span class="sxs-lookup"><span data-stu-id="f6271-207">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="f6271-208">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="f6271-208">-WhatIf</span></span>

<span data-ttu-id="f6271-209">Visar vad som skulle hända om cmdleten kördes.</span><span class="sxs-lookup"><span data-stu-id="f6271-209">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="f6271-210">Cmdleten körs inte.</span><span class="sxs-lookup"><span data-stu-id="f6271-210">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="f6271-211">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="f6271-211">CommonParameters</span></span>

<span data-ttu-id="f6271-212">Denna cmdlet stöder de gemensamma parametrarna:,,,,,,,, `-Debug` `-ErrorAction` `-ErrorVariable` `-InformationAction` `-InformationVariable` `-OutVariable` `-OutBuffer` `-PipelineVariable` `-Verbose` `-WarningAction` , och `-WarningVariable` .</span><span class="sxs-lookup"><span data-stu-id="f6271-212">This cmdlet supports the common parameters: `-Debug`, `-ErrorAction`, `-ErrorVariable`, `-InformationAction`, `-InformationVariable`, `-OutVariable`, `-OutBuffer`, `-PipelineVariable`, `-Verbose`, `-WarningAction`, and `-WarningVariable`.</span></span> <span data-ttu-id="f6271-213">Mer information finns i [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span><span class="sxs-lookup"><span data-stu-id="f6271-213">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="f6271-214">INDATA</span><span class="sxs-lookup"><span data-stu-id="f6271-214">INPUTS</span></span>

### <span data-ttu-id="f6271-215">System. Management. Automation. PSObject</span><span class="sxs-lookup"><span data-stu-id="f6271-215">System.Management.Automation.PSObject</span></span>

<span data-ttu-id="f6271-216">Du kan skicka pipe-objekt till denna cmdlet.</span><span class="sxs-lookup"><span data-stu-id="f6271-216">You can pipe objects to this cmdlet.</span></span>

## <span data-ttu-id="f6271-217">UTDATA</span><span class="sxs-lookup"><span data-stu-id="f6271-217">OUTPUTS</span></span>

### <span data-ttu-id="f6271-218">Ingen, system. Management. Automation. PSCustomObject</span><span class="sxs-lookup"><span data-stu-id="f6271-218">None, System.Management.Automation.PSCustomObject</span></span>

<span data-ttu-id="f6271-219">Denna cmdlet genererar ett **PSCustomObject** -objekt som representerar objektet som ändrades och dess nya egenskaps värde, om du anger parametern **Passthru** .</span><span class="sxs-lookup"><span data-stu-id="f6271-219">This cmdlet generates a **PSCustomObject** object that represents the item that was changed and its new property value, if you specify the **PassThru** parameter.</span></span>
<span data-ttu-id="f6271-220">Annars genererar denna cmdlet inga utdata.</span><span class="sxs-lookup"><span data-stu-id="f6271-220">Otherwise, this cmdlet does not generate any output.</span></span>

## <span data-ttu-id="f6271-221">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="f6271-221">NOTES</span></span>

<span data-ttu-id="f6271-222">`Set-ItemProperty` är utformad för att fungera med data som exponeras av vilken provider som helst.</span><span class="sxs-lookup"><span data-stu-id="f6271-222">`Set-ItemProperty` is designed to work with the data exposed by any provider.</span></span> <span data-ttu-id="f6271-223">Om du vill visa en lista över tillgängliga providers i din session skriver du `Get-PSProvider` .</span><span class="sxs-lookup"><span data-stu-id="f6271-223">To list the providers available in your session, type `Get-PSProvider`.</span></span> <span data-ttu-id="f6271-224">Mer information finns i [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span><span class="sxs-lookup"><span data-stu-id="f6271-224">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

## <span data-ttu-id="f6271-225">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="f6271-225">RELATED LINKS</span></span>

[<span data-ttu-id="f6271-226">Clear-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="f6271-226">Clear-ItemProperty</span></span>](Clear-ItemProperty.md)

[<span data-ttu-id="f6271-227">Kopiera – ItemProperty</span><span class="sxs-lookup"><span data-stu-id="f6271-227">Copy-ItemProperty</span></span>](Copy-ItemProperty.md)

[<span data-ttu-id="f6271-228">Get-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="f6271-228">Get-ItemProperty</span></span>](Get-ItemProperty.md)

[<span data-ttu-id="f6271-229">Move-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="f6271-229">Move-ItemProperty</span></span>](Move-ItemProperty.md)

[<span data-ttu-id="f6271-230">New-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="f6271-230">New-ItemProperty</span></span>](New-ItemProperty.md)

[<span data-ttu-id="f6271-231">Remove-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="f6271-231">Remove-ItemProperty</span></span>](Remove-ItemProperty.md)

[<span data-ttu-id="f6271-232">Byt namn – ItemProperty</span><span class="sxs-lookup"><span data-stu-id="f6271-232">Rename-ItemProperty</span></span>](Rename-ItemProperty.md)

[<span data-ttu-id="f6271-233">about_Providers</span><span class="sxs-lookup"><span data-stu-id="f6271-233">about_Providers</span></span>](../Microsoft.PowerShell.Core/About/about_Providers.md)

