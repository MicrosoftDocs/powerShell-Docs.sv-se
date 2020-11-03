---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 5/14/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/new-itemproperty?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-ItemProperty
ms.openlocfilehash: 8378534715bfcfa8fffc08be17cb4bef9de6c60e
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93263300"
---
# <span data-ttu-id="9c11b-103">New-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="9c11b-103">New-ItemProperty</span></span>

## <span data-ttu-id="9c11b-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="9c11b-104">SYNOPSIS</span></span>
<span data-ttu-id="9c11b-105">Skapar en ny egenskap för ett objekt och anger dess värde.</span><span class="sxs-lookup"><span data-stu-id="9c11b-105">Creates a new property for an item and sets its value.</span></span>

## <span data-ttu-id="9c11b-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="9c11b-106">SYNTAX</span></span>

### <span data-ttu-id="9c11b-107">Sökväg (standard)</span><span class="sxs-lookup"><span data-stu-id="9c11b-107">Path (Default)</span></span>

```
New-ItemProperty [-Path] <String[]> [-Name] <String> [-PropertyType <String>] [-Value <Object>] [-Force]
 [-Filter <String>] [-Include <String[]>] [-Exclude <String[]>] [-Credential <PSCredential>] [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="9c11b-108">LiteralPath</span><span class="sxs-lookup"><span data-stu-id="9c11b-108">LiteralPath</span></span>

```
New-ItemProperty -LiteralPath <String[]> [-Name] <String> [-PropertyType <String>] [-Value <Object>] [-Force]
 [-Filter <String>] [-Include <String[]>] [-Exclude <String[]>] [-Credential <PSCredential>] [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="9c11b-109">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="9c11b-109">DESCRIPTION</span></span>

<span data-ttu-id="9c11b-110">`New-ItemProperty`Cmdleten skapar en ny egenskap för ett angivet objekt och anger dess värde.</span><span class="sxs-lookup"><span data-stu-id="9c11b-110">The `New-ItemProperty` cmdlet creates a new property for a specified item and sets its value.</span></span>
<span data-ttu-id="9c11b-111">Normalt används denna cmdlet för att skapa nya register värden, eftersom register värden är egenskaper för ett register nyckel objekt.</span><span class="sxs-lookup"><span data-stu-id="9c11b-111">Typically, this cmdlet is used to create new registry values, because registry values are properties of a registry key item.</span></span>

<span data-ttu-id="9c11b-112">Denna cmdlet lägger inte till egenskaper till ett objekt.</span><span class="sxs-lookup"><span data-stu-id="9c11b-112">This cmdlet does not add properties to an object.</span></span>

- <span data-ttu-id="9c11b-113">Använd cmdleten om du vill lägga till en egenskap till en instans av ett objekt `Add-Member` .</span><span class="sxs-lookup"><span data-stu-id="9c11b-113">To add a property to an instance of an object, use the `Add-Member` cmdlet.</span></span>
- <span data-ttu-id="9c11b-114">Om du vill lägga till en egenskap för alla objekt av en viss typ ändrar du Types.ps1XML-filen.</span><span class="sxs-lookup"><span data-stu-id="9c11b-114">To add a property to all objects of a particular type, modify the Types.ps1xml file.</span></span>

## <span data-ttu-id="9c11b-115">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="9c11b-115">EXAMPLES</span></span>

### <span data-ttu-id="9c11b-116">Exempel 1: Lägg till en register post</span><span class="sxs-lookup"><span data-stu-id="9c11b-116">Example 1: Add a registry entry</span></span>

<span data-ttu-id="9c11b-117">Det här kommandot lägger till en ny register post, "NoOfEmployees", till nyckeln "företaget" i "HKLM: \ program registrerings data".</span><span class="sxs-lookup"><span data-stu-id="9c11b-117">This command adds a new registry entry, "NoOfEmployees", to the "MyCompany" key of the "HKLM:\Software hive".</span></span>

<span data-ttu-id="9c11b-118">Det första kommandot använder parametern **Path** för att ange sökvägen till register nyckeln "företaget".</span><span class="sxs-lookup"><span data-stu-id="9c11b-118">The first command uses the **Path** parameter to specify the path of the "MyCompany" registry key.</span></span>
<span data-ttu-id="9c11b-119">Parametern **Name** används för att ange ett namn för posten och **värde** parametern för att ange dess värde.</span><span class="sxs-lookup"><span data-stu-id="9c11b-119">It uses the **Name** parameter to specify a name for the entry and the **Value** parameter to specify its value.</span></span>

<span data-ttu-id="9c11b-120">Det andra kommandot använder `Get-ItemProperty` cmdleten för att se den nya register posten.</span><span class="sxs-lookup"><span data-stu-id="9c11b-120">The second command uses the `Get-ItemProperty` cmdlet to see the new registry entry.</span></span>

```powershell
New-ItemProperty -Path "HKLM:\Software\MyCompany" -Name "NoOfEmployees" -Value 822
Get-ItemProperty "HKLM:\Software\MyCompany"
```

```output
PSPath        : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\software\mycompany
PSParentPath  : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\software
PSChildName   : mycompany
PSDrive       : HKLM
PSProvider    : Microsoft.PowerShell.Core\Registry
NoOfLocations : 2
NoOfEmployees : 822
```

### <span data-ttu-id="9c11b-121">Exempel 2: lägga till en register post i en nyckel</span><span class="sxs-lookup"><span data-stu-id="9c11b-121">Example 2: Add a registry entry to a key</span></span>

<span data-ttu-id="9c11b-122">Detta kommando lägger till en ny register post i en register nyckel.</span><span class="sxs-lookup"><span data-stu-id="9c11b-122">This command adds a new registry entry to a registry key.</span></span>
<span data-ttu-id="9c11b-123">För att ange nyckeln använder den en pipeline-operator ( `|` ) för att skicka ett objekt som representerar nyckeln till `New-ItemProperty` .</span><span class="sxs-lookup"><span data-stu-id="9c11b-123">To specify the key, it uses a pipeline operator (`|`) to send an object that represents the key to `New-ItemProperty`.</span></span>

<span data-ttu-id="9c11b-124">Den första delen av kommandot använder `Get-Item` cmdleten för att hämta register nyckeln "företaget".</span><span class="sxs-lookup"><span data-stu-id="9c11b-124">The first part of the command uses the `Get-Item` cmdlet to get the "MyCompany" registry key.</span></span>
<span data-ttu-id="9c11b-125">Pipeline-operatorn skickar resultatet från kommandot till `New-ItemProperty` , som lägger till den nya register posten ("NoOfLocations") och dess värde (3) till nyckeln "företaget".</span><span class="sxs-lookup"><span data-stu-id="9c11b-125">The pipeline operator sends the results of the command to `New-ItemProperty`, which adds the new registry entry ("NoOfLocations"), and its value (3), to the "MyCompany" key.</span></span>

```powershell
Get-Item -Path "HKLM:\Software\MyCompany" | New-ItemProperty -Name NoOfLocations -Value 3
```

<span data-ttu-id="9c11b-126">Det här kommandot fungerar eftersom funktionen parameter-binding i PowerShell associerar sökvägen till det `RegistryKey` objekt som `Get-Item` returneras med **LiteralPath** -parametern för `New-ItemProperty` .</span><span class="sxs-lookup"><span data-stu-id="9c11b-126">This command works because the parameter-binding feature of PowerShell associates the path of the `RegistryKey` object that `Get-Item` returns with the **LiteralPath** parameter of `New-ItemProperty`.</span></span> <span data-ttu-id="9c11b-127">Mer information finns i [about_Pipelines](../Microsoft.PowerShell.Core/About/about_pipelines.md).</span><span class="sxs-lookup"><span data-stu-id="9c11b-127">For more information, see [about_Pipelines](../Microsoft.PowerShell.Core/About/about_pipelines.md).</span></span>

### <span data-ttu-id="9c11b-128">Exempel 3: skapa ett multisträng-värde i registret med hjälp av en Here-String</span><span class="sxs-lookup"><span data-stu-id="9c11b-128">Example 3: Create a MultiString value in the registry using a Here-String</span></span>

<span data-ttu-id="9c11b-129">I det här exemplet skapas ett multisträng värde med hjälp av en här-sträng.</span><span class="sxs-lookup"><span data-stu-id="9c11b-129">This example creates a MultiString value using a Here-String.</span></span>

```powershell
$newValue = New-ItemProperty -Path "HKLM:\SOFTWARE\ContosoCompany\" -Name 'HereString' -PropertyType MultiString -Value @"
This is text which contains newlines
It can also contain "quoted" strings
"@
$newValue.multistring
```

```output
This is text which contains newlines
It can also contain "quoted" strings
```

### <span data-ttu-id="9c11b-130">Exempel 4: skapa ett multisträng-värde i registret med hjälp av en matris</span><span class="sxs-lookup"><span data-stu-id="9c11b-130">Example 4: Create a MultiString value in the registry using an array</span></span>

<span data-ttu-id="9c11b-131">Exemplet visar hur du använder en matris med värden för att skapa `MultiString` värdet.</span><span class="sxs-lookup"><span data-stu-id="9c11b-131">The example shows how to use an array of values to create the `MultiString` value.</span></span>

```powershell
$newValue = New-ItemProperty -Path "HKLM:\SOFTWARE\ContosoCompany\" -Name 'MultiString' -PropertyType MultiString -Value ('a','b','c')
$newValue.multistring[0]
```

```output
a
```

## <span data-ttu-id="9c11b-132">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="9c11b-132">PARAMETERS</span></span>

### <span data-ttu-id="9c11b-133">-Credential</span><span class="sxs-lookup"><span data-stu-id="9c11b-133">-Credential</span></span>

> [!NOTE]
> <span data-ttu-id="9c11b-134">Den här parametern stöds inte av några providrar som installeras med PowerShell.</span><span class="sxs-lookup"><span data-stu-id="9c11b-134">This parameter is not supported by any providers installed with PowerShell.</span></span>
> <span data-ttu-id="9c11b-135">Om du vill personifiera en annan användare eller öka dina autentiseringsuppgifter när du kör denna cmdlet, använder du [Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md).</span><span class="sxs-lookup"><span data-stu-id="9c11b-135">To impersonate another user, or elevate your credentials when running this cmdlet, use [Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md).</span></span>

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

### <span data-ttu-id="9c11b-136">-Undanta</span><span class="sxs-lookup"><span data-stu-id="9c11b-136">-Exclude</span></span>

<span data-ttu-id="9c11b-137">Anger, som en sträng mat ris, ett objekt eller objekt som denna cmdlet exkluderar i åtgärden.</span><span class="sxs-lookup"><span data-stu-id="9c11b-137">Specifies, as a string array, an item or items that this cmdlet excludes in the operation.</span></span> <span data-ttu-id="9c11b-138">Värdet för den här parametern kvalificerar parametern **Path** .</span><span class="sxs-lookup"><span data-stu-id="9c11b-138">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="9c11b-139">Ange ett Sök vägs element eller ett mönster, till exempel `*.txt` .</span><span class="sxs-lookup"><span data-stu-id="9c11b-139">Enter a path element or pattern, such as `*.txt`.</span></span> <span data-ttu-id="9c11b-140">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="9c11b-140">Wildcard characters are permitted.</span></span> <span data-ttu-id="9c11b-141">Parametern **exclude** är endast effektiv när kommandot innehåller innehållet i ett objekt, t. ex `C:\Windows\*` ., där jokertecknet anger innehållet i `C:\Windows` katalogen.</span><span class="sxs-lookup"><span data-stu-id="9c11b-141">The **Exclude** parameter is effective only when the command includes the contents of an item, such as `C:\Windows\*`, where the wildcard character specifies the contents of the `C:\Windows` directory.</span></span>

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

### <span data-ttu-id="9c11b-142">-Filter</span><span class="sxs-lookup"><span data-stu-id="9c11b-142">-Filter</span></span>

<span data-ttu-id="9c11b-143">Anger ett filter för att kvalificera **Sök vägs** parametern.</span><span class="sxs-lookup"><span data-stu-id="9c11b-143">Specifies a filter to qualify the **Path** parameter.</span></span> <span data-ttu-id="9c11b-144">[Fil Systems](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md) leverantören är den enda installerade PowerShell-providern som stöder användningen av filter.</span><span class="sxs-lookup"><span data-stu-id="9c11b-144">The [FileSystem](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md) provider is the only installed PowerShell provider that supports the use of filters.</span></span> <span data-ttu-id="9c11b-145">Du kan hitta syntaxen för filter språket för **fil systemet** i [about_Wildcards](../Microsoft.PowerShell.Core/About/about_Wildcards.md).</span><span class="sxs-lookup"><span data-stu-id="9c11b-145">You can find the syntax for the **FileSystem** filter language in [about_Wildcards](../Microsoft.PowerShell.Core/About/about_Wildcards.md).</span></span>
<span data-ttu-id="9c11b-146">Filter är mer effektiva än andra parametrar, eftersom providern tillämpar dem när cmdleten hämtar objekten i stället för att ha PowerShell filtrera objekten när de har hämtats.</span><span class="sxs-lookup"><span data-stu-id="9c11b-146">Filters are more efficient than other parameters, because the provider applies them when the cmdlet gets the objects rather than having PowerShell filter the objects after they are retrieved.</span></span>

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

### <span data-ttu-id="9c11b-147">-Force</span><span class="sxs-lookup"><span data-stu-id="9c11b-147">-Force</span></span>

<span data-ttu-id="9c11b-148">Tvingar cmdleten att skapa en egenskap för ett objekt som annars inte kan kommas åt av användaren.</span><span class="sxs-lookup"><span data-stu-id="9c11b-148">Forces the cmdlet to create a property on an object that cannot otherwise be accessed by the user.</span></span>
<span data-ttu-id="9c11b-149">Implementeringen varierar från providern till providern.</span><span class="sxs-lookup"><span data-stu-id="9c11b-149">Implementation varies from provider to provider.</span></span>
<span data-ttu-id="9c11b-150">Mer information finns i [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span><span class="sxs-lookup"><span data-stu-id="9c11b-150">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

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

### <span data-ttu-id="9c11b-151">-Inkludera</span><span class="sxs-lookup"><span data-stu-id="9c11b-151">-Include</span></span>

<span data-ttu-id="9c11b-152">Anger, som en sträng mat ris, ett objekt eller objekt som denna cmdlet inkluderar i åtgärden.</span><span class="sxs-lookup"><span data-stu-id="9c11b-152">Specifies, as a string array, an item or items that this cmdlet includes in the operation.</span></span> <span data-ttu-id="9c11b-153">Värdet för den här parametern kvalificerar parametern **Path** .</span><span class="sxs-lookup"><span data-stu-id="9c11b-153">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="9c11b-154">Ange ett Sök vägs element eller ett mönster, till exempel `"*.txt"` .</span><span class="sxs-lookup"><span data-stu-id="9c11b-154">Enter a path element or pattern, such as `"*.txt"`.</span></span> <span data-ttu-id="9c11b-155">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="9c11b-155">Wildcard characters are permitted.</span></span> <span data-ttu-id="9c11b-156">Parametern **include** är endast effektiv när kommandot innehåller innehållet i ett objekt, t. ex `C:\Windows\*` ., där jokertecknet anger innehållet i `C:\Windows` katalogen.</span><span class="sxs-lookup"><span data-stu-id="9c11b-156">The **Include** parameter is effective only when the command includes the contents of an item, such as `C:\Windows\*`, where the wildcard character specifies the contents of the `C:\Windows` directory.</span></span>

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

### <span data-ttu-id="9c11b-157">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="9c11b-157">-LiteralPath</span></span>

<span data-ttu-id="9c11b-158">Anger en sökväg till en eller flera platser.</span><span class="sxs-lookup"><span data-stu-id="9c11b-158">Specifies a path to one or more locations.</span></span> <span data-ttu-id="9c11b-159">Värdet för **LiteralPath** används exakt som det har angetts.</span><span class="sxs-lookup"><span data-stu-id="9c11b-159">The value of **LiteralPath** is used exactly as it is typed.</span></span> <span data-ttu-id="9c11b-160">Inga tecken tolkas som jokertecken.</span><span class="sxs-lookup"><span data-stu-id="9c11b-160">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="9c11b-161">Om sökvägen innehåller escape-tecken omger du den med enkla citat tecken.</span><span class="sxs-lookup"><span data-stu-id="9c11b-161">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="9c11b-162">Enkla citat tecken säger att PowerShell inte tolkar några tecken som escape-sekvenser.</span><span class="sxs-lookup"><span data-stu-id="9c11b-162">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

<span data-ttu-id="9c11b-163">Mer information finns i [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md).</span><span class="sxs-lookup"><span data-stu-id="9c11b-163">For more information, see [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md).</span></span>

```yaml
Type: System.String[]
Parameter Sets: LiteralPath
Aliases: PSPath, LP

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="9c11b-164">-Name</span><span class="sxs-lookup"><span data-stu-id="9c11b-164">-Name</span></span>

<span data-ttu-id="9c11b-165">Anger ett namn för den nya egenskapen.</span><span class="sxs-lookup"><span data-stu-id="9c11b-165">Specifies a name for the new property.</span></span>
<span data-ttu-id="9c11b-166">Om egenskapen är en register post anger den här parametern namnet på posten.</span><span class="sxs-lookup"><span data-stu-id="9c11b-166">If the property is a registry entry, this parameter specifies the name of the entry.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: PSProperty

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="9c11b-167">-Path</span><span class="sxs-lookup"><span data-stu-id="9c11b-167">-Path</span></span>

<span data-ttu-id="9c11b-168">Anger objektets sökväg.</span><span class="sxs-lookup"><span data-stu-id="9c11b-168">Specifies the path of the item.</span></span>
<span data-ttu-id="9c11b-169">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="9c11b-169">Wildcard characters are permitted.</span></span>
<span data-ttu-id="9c11b-170">Den här parametern identifierar objektet som den här cmdleten lägger till den nya egenskapen i.</span><span class="sxs-lookup"><span data-stu-id="9c11b-170">This parameter identifies the item to which this cmdlet adds the new property.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Path
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="9c11b-171">– PropertyType</span><span class="sxs-lookup"><span data-stu-id="9c11b-171">-PropertyType</span></span>

<span data-ttu-id="9c11b-172">Anger vilken typ av egenskap som denna cmdlet lägger till.</span><span class="sxs-lookup"><span data-stu-id="9c11b-172">Specifies the type of property that this cmdlet adds.</span></span>
<span data-ttu-id="9c11b-173">De acceptabla värdena för den här parametern är:</span><span class="sxs-lookup"><span data-stu-id="9c11b-173">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="9c11b-174">**Sträng** : anger en null-avslutad sträng.</span><span class="sxs-lookup"><span data-stu-id="9c11b-174">**String** : Specifies a null-terminated string.</span></span> <span data-ttu-id="9c11b-175">Motsvarar **REG_SZ**.</span><span class="sxs-lookup"><span data-stu-id="9c11b-175">Equivalent to **REG_SZ**.</span></span>
- <span data-ttu-id="9c11b-176">**ExpandString** : anger en null-avslutad sträng som innehåller expanderade referenser till miljövariabler som expanderas när värdet hämtas.</span><span class="sxs-lookup"><span data-stu-id="9c11b-176">**ExpandString** : Specifies a null-terminated string that contains unexpanded references to environment variables that are expanded when the value is retrieved.</span></span> <span data-ttu-id="9c11b-177">Motsvarar **REG_EXPAND_SZ**.</span><span class="sxs-lookup"><span data-stu-id="9c11b-177">Equivalent to **REG_EXPAND_SZ**.</span></span>
- <span data-ttu-id="9c11b-178">**Binary** : anger binära data i alla former.</span><span class="sxs-lookup"><span data-stu-id="9c11b-178">**Binary** : Specifies binary data in any form.</span></span> <span data-ttu-id="9c11b-179">Motsvarar **REG_BINARY**.</span><span class="sxs-lookup"><span data-stu-id="9c11b-179">Equivalent to **REG_BINARY**.</span></span>
- <span data-ttu-id="9c11b-180">**DWORD** : anger ett 32-bitars binärt tal.</span><span class="sxs-lookup"><span data-stu-id="9c11b-180">**DWord** : Specifies a 32-bit binary number.</span></span> <span data-ttu-id="9c11b-181">Motsvarar **REG_DWORD**.</span><span class="sxs-lookup"><span data-stu-id="9c11b-181">Equivalent to **REG_DWORD**.</span></span>
- <span data-ttu-id="9c11b-182">**Multisträng** : anger en matris med null-terminerade strängar som avslutas med två NULL-tecken.</span><span class="sxs-lookup"><span data-stu-id="9c11b-182">**MultiString** : Specifies an array of null-terminated strings terminated by two null characters.</span></span>
  <span data-ttu-id="9c11b-183">Motsvarar **REG_MULTI_SZ**.</span><span class="sxs-lookup"><span data-stu-id="9c11b-183">Equivalent to **REG_MULTI_SZ**.</span></span>
- <span data-ttu-id="9c11b-184">**QWORD** : anger ett 64-bitars binärt tal.</span><span class="sxs-lookup"><span data-stu-id="9c11b-184">**Qword** : Specifies a 64-bit binary number.</span></span> <span data-ttu-id="9c11b-185">Motsvarar **REG_QWORD**.</span><span class="sxs-lookup"><span data-stu-id="9c11b-185">Equivalent to **REG_QWORD**.</span></span>
- <span data-ttu-id="9c11b-186">**Okänd** : anger en register data typ som inte stöds, till exempel **REG_RESOURCE_LIST**.</span><span class="sxs-lookup"><span data-stu-id="9c11b-186">**Unknown** : Indicates an unsupported registry data type, such as **REG_RESOURCE_LIST**.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: Type

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="9c11b-187">-Värde</span><span class="sxs-lookup"><span data-stu-id="9c11b-187">-Value</span></span>

<span data-ttu-id="9c11b-188">Anger egenskap svärdet.</span><span class="sxs-lookup"><span data-stu-id="9c11b-188">Specifies the property value.</span></span>
<span data-ttu-id="9c11b-189">Om egenskapen är en register post anger den här parametern värdet för posten.</span><span class="sxs-lookup"><span data-stu-id="9c11b-189">If the property is a registry entry, this parameter specifies the value of the entry.</span></span>

```yaml
Type: System.Object
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="9c11b-190">-Confirm</span><span class="sxs-lookup"><span data-stu-id="9c11b-190">-Confirm</span></span>

<span data-ttu-id="9c11b-191">Uppmanar dig att bekräfta innan du kör cmdleten.</span><span class="sxs-lookup"><span data-stu-id="9c11b-191">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="9c11b-192">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="9c11b-192">-WhatIf</span></span>

<span data-ttu-id="9c11b-193">Visar vad som skulle hända om cmdleten kördes.</span><span class="sxs-lookup"><span data-stu-id="9c11b-193">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="9c11b-194">Cmdleten körs inte.</span><span class="sxs-lookup"><span data-stu-id="9c11b-194">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="9c11b-195">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="9c11b-195">CommonParameters</span></span>

<span data-ttu-id="9c11b-196">Denna cmdlet stöder de gemensamma parametrarna:,,,,,,,, `-Debug` `-ErrorAction` `-ErrorVariable` `-InformationAction` `-InformationVariable` `-OutVariable` `-OutBuffer` `-PipelineVariable` `-Verbose` `-WarningAction` , och `-WarningVariable` .</span><span class="sxs-lookup"><span data-stu-id="9c11b-196">This cmdlet supports the common parameters: `-Debug`, `-ErrorAction`, `-ErrorVariable`, `-InformationAction`, `-InformationVariable`, `-OutVariable`, `-OutBuffer`, `-PipelineVariable`, `-Verbose`, `-WarningAction`, and `-WarningVariable`.</span></span> <span data-ttu-id="9c11b-197">Mer information finns i [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span><span class="sxs-lookup"><span data-stu-id="9c11b-197">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="9c11b-198">INDATA</span><span class="sxs-lookup"><span data-stu-id="9c11b-198">INPUTS</span></span>

### <span data-ttu-id="9c11b-199">Inget</span><span class="sxs-lookup"><span data-stu-id="9c11b-199">None</span></span>

<span data-ttu-id="9c11b-200">Du kan inte skicka pipe-ininformation till denna cmdlet.</span><span class="sxs-lookup"><span data-stu-id="9c11b-200">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="9c11b-201">UTDATA</span><span class="sxs-lookup"><span data-stu-id="9c11b-201">OUTPUTS</span></span>

### <span data-ttu-id="9c11b-202">System. Management. Automation. PSCustomObject</span><span class="sxs-lookup"><span data-stu-id="9c11b-202">System.Management.Automation.PSCustomObject</span></span>

<span data-ttu-id="9c11b-203">`New-ItemProperty` Returnerar ett anpassat objekt som innehåller den nya egenskapen.</span><span class="sxs-lookup"><span data-stu-id="9c11b-203">`New-ItemProperty` returns a custom object that contains the new property.</span></span>

## <span data-ttu-id="9c11b-204">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="9c11b-204">NOTES</span></span>

<span data-ttu-id="9c11b-205">`New-ItemProperty` är utformad för att fungera med data som exponeras av vilken provider som helst.</span><span class="sxs-lookup"><span data-stu-id="9c11b-205">`New-ItemProperty` is designed to work with the data exposed by any provider.</span></span> <span data-ttu-id="9c11b-206">Om du vill visa en lista över tillgängliga providers i din session skriver du `Get-PSProvider` .</span><span class="sxs-lookup"><span data-stu-id="9c11b-206">To list the providers available in your session, type `Get-PSProvider`.</span></span> <span data-ttu-id="9c11b-207">Mer information finns i [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span><span class="sxs-lookup"><span data-stu-id="9c11b-207">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

## <span data-ttu-id="9c11b-208">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="9c11b-208">RELATED LINKS</span></span>

[<span data-ttu-id="9c11b-209">Clear-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="9c11b-209">Clear-ItemProperty</span></span>](Clear-ItemProperty.md)

[<span data-ttu-id="9c11b-210">Kopiera – ItemProperty</span><span class="sxs-lookup"><span data-stu-id="9c11b-210">Copy-ItemProperty</span></span>](Copy-ItemProperty.md)

[<span data-ttu-id="9c11b-211">Get-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="9c11b-211">Get-ItemProperty</span></span>](Get-ItemProperty.md)

[<span data-ttu-id="9c11b-212">Move-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="9c11b-212">Move-ItemProperty</span></span>](Move-ItemProperty.md)

[<span data-ttu-id="9c11b-213">Remove-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="9c11b-213">Remove-ItemProperty</span></span>](Remove-ItemProperty.md)

[<span data-ttu-id="9c11b-214">Byt namn – ItemProperty</span><span class="sxs-lookup"><span data-stu-id="9c11b-214">Rename-ItemProperty</span></span>](Rename-ItemProperty.md)

[<span data-ttu-id="9c11b-215">Set-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="9c11b-215">Set-ItemProperty</span></span>](Set-ItemProperty.md)

[<span data-ttu-id="9c11b-216">about_Providers</span><span class="sxs-lookup"><span data-stu-id="9c11b-216">about_Providers</span></span>](../Microsoft.PowerShell.Core/About/about_Providers.md)

