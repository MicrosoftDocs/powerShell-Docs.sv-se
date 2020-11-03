---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 10/18/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/new-itemproperty?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-ItemProperty
ms.openlocfilehash: 2569f4778f54f6cdad22e10cf92e727b73c323e3
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93265526"
---
# <span data-ttu-id="beafb-103">New-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="beafb-103">New-ItemProperty</span></span>

## <span data-ttu-id="beafb-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="beafb-104">SYNOPSIS</span></span>
<span data-ttu-id="beafb-105">Skapar en ny egenskap för ett objekt och anger dess värde.</span><span class="sxs-lookup"><span data-stu-id="beafb-105">Creates a new property for an item and sets its value.</span></span>

## <span data-ttu-id="beafb-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="beafb-106">SYNTAX</span></span>

### <span data-ttu-id="beafb-107">Sökväg (standard)</span><span class="sxs-lookup"><span data-stu-id="beafb-107">Path (Default)</span></span>

```
New-ItemProperty [-Path] <String[]> [-Name] <String> [-PropertyType <String>] [-Value <Object>] [-Force]
 [-Filter <String>] [-Include <String[]>] [-Exclude <String[]>] [-Credential <PSCredential>] [-WhatIf]
 [-Confirm] [-UseTransaction] [<CommonParameters>]
```

### <span data-ttu-id="beafb-108">LiteralPath</span><span class="sxs-lookup"><span data-stu-id="beafb-108">LiteralPath</span></span>

```
New-ItemProperty -LiteralPath <String[]> [-Name] <String> [-PropertyType <String>] [-Value <Object>] [-Force]
 [-Filter <String>] [-Include <String[]>] [-Exclude <String[]>] [-Credential <PSCredential>] [-WhatIf]
 [-Confirm] [-UseTransaction] [<CommonParameters>]
```

## <span data-ttu-id="beafb-109">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="beafb-109">DESCRIPTION</span></span>

<span data-ttu-id="beafb-110">`New-ItemProperty`Cmdleten skapar en ny egenskap för ett angivet objekt och anger dess värde.</span><span class="sxs-lookup"><span data-stu-id="beafb-110">The `New-ItemProperty` cmdlet creates a new property for a specified item and sets its value.</span></span>
<span data-ttu-id="beafb-111">Normalt används denna cmdlet för att skapa nya register värden, eftersom register värden är egenskaper för ett register nyckel objekt.</span><span class="sxs-lookup"><span data-stu-id="beafb-111">Typically, this cmdlet is used to create new registry values, because registry values are properties of a registry key item.</span></span>

<span data-ttu-id="beafb-112">Denna cmdlet lägger inte till egenskaper till ett objekt.</span><span class="sxs-lookup"><span data-stu-id="beafb-112">This cmdlet does not add properties to an object.</span></span>

- <span data-ttu-id="beafb-113">Använd cmdleten om du vill lägga till en egenskap till en instans av ett objekt `Add-Member` .</span><span class="sxs-lookup"><span data-stu-id="beafb-113">To add a property to an instance of an object, use the `Add-Member` cmdlet.</span></span>
- <span data-ttu-id="beafb-114">Om du vill lägga till en egenskap för alla objekt av en viss typ ändrar du Types.ps1XML-filen.</span><span class="sxs-lookup"><span data-stu-id="beafb-114">To add a property to all objects of a particular type, modify the Types.ps1xml file.</span></span>

## <span data-ttu-id="beafb-115">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="beafb-115">EXAMPLES</span></span>

### <span data-ttu-id="beafb-116">Exempel 1: Lägg till en register post</span><span class="sxs-lookup"><span data-stu-id="beafb-116">Example 1: Add a registry entry</span></span>

<span data-ttu-id="beafb-117">Det här kommandot lägger till en ny register post, "NoOfEmployees", till nyckeln "företaget" i "HKLM: \ program registrerings data".</span><span class="sxs-lookup"><span data-stu-id="beafb-117">This command adds a new registry entry, "NoOfEmployees", to the "MyCompany" key of the "HKLM:\Software hive".</span></span>

<span data-ttu-id="beafb-118">Det första kommandot använder parametern **Path** för att ange sökvägen till register nyckeln "företaget".</span><span class="sxs-lookup"><span data-stu-id="beafb-118">The first command uses the **Path** parameter to specify the path of the "MyCompany" registry key.</span></span>
<span data-ttu-id="beafb-119">Parametern **Name** används för att ange ett namn för posten och **värde** parametern för att ange dess värde.</span><span class="sxs-lookup"><span data-stu-id="beafb-119">It uses the **Name** parameter to specify a name for the entry and the **Value** parameter to specify its value.</span></span>

<span data-ttu-id="beafb-120">Det andra kommandot använder `Get-ItemProperty` cmdleten för att se den nya register posten.</span><span class="sxs-lookup"><span data-stu-id="beafb-120">The second command uses the `Get-ItemProperty` cmdlet to see the new registry entry.</span></span>

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

### <span data-ttu-id="beafb-121">Exempel 2: lägga till en register post i en nyckel</span><span class="sxs-lookup"><span data-stu-id="beafb-121">Example 2: Add a registry entry to a key</span></span>

<span data-ttu-id="beafb-122">Detta kommando lägger till en ny register post i en register nyckel.</span><span class="sxs-lookup"><span data-stu-id="beafb-122">This command adds a new registry entry to a registry key.</span></span> <span data-ttu-id="beafb-123">För att ange nyckeln använder den en pipeline-operator (|) för att skicka ett objekt som representerar nyckeln till `New-ItemProperty` .</span><span class="sxs-lookup"><span data-stu-id="beafb-123">To specify the key, it uses a pipeline operator (|) to send an object that represents the key to `New-ItemProperty`.</span></span>

<span data-ttu-id="beafb-124">Den första delen av kommandot använder `Get-Item` cmdleten för att hämta register nyckeln "företaget".</span><span class="sxs-lookup"><span data-stu-id="beafb-124">The first part of the command uses the `Get-Item` cmdlet to get the "MyCompany" registry key.</span></span> <span data-ttu-id="beafb-125">Pipeline-operatorn skickar resultatet från kommandot till `New-ItemProperty` , som lägger till den nya register posten ("NoOfLocations") och dess värde (3) till nyckeln "företaget".</span><span class="sxs-lookup"><span data-stu-id="beafb-125">The pipeline operator sends the results of the command to `New-ItemProperty`, which adds the new registry entry ("NoOfLocations"), and its value (3), to the "MyCompany" key.</span></span>

```powershell
Get-Item -Path "HKLM:\Software\MyCompany" | New-ItemProperty -Name NoOfLocations -Value 3
```

<span data-ttu-id="beafb-126">Det här kommandot fungerar eftersom funktionen parameter-binding i Windows PowerShell associerar sökvägen till det `RegistryKey` objekt som `Get-Item` returneras med **LiteralPath** -parametern för `New-ItemProperty` .</span><span class="sxs-lookup"><span data-stu-id="beafb-126">This command works because the parameter-binding feature of Windows PowerShell associates the path of the `RegistryKey` object that `Get-Item` returns with the **LiteralPath** parameter of `New-ItemProperty`.</span></span> <span data-ttu-id="beafb-127">Mer information finns i [about_Pipelines](../Microsoft.PowerShell.Core/About/about_pipelines.md).</span><span class="sxs-lookup"><span data-stu-id="beafb-127">For more information, see [about_Pipelines](../Microsoft.PowerShell.Core/About/about_pipelines.md).</span></span>

### <span data-ttu-id="beafb-128">Exempel 3: skapa ett multisträng-värde i registret med hjälp av en Here-String</span><span class="sxs-lookup"><span data-stu-id="beafb-128">Example 3: Create a MultiString value in the registry using a Here-String</span></span>

<span data-ttu-id="beafb-129">I det här exemplet skapas ett multisträng värde med hjälp av en här-sträng.</span><span class="sxs-lookup"><span data-stu-id="beafb-129">This example creates a MultiString value using a Here-String.</span></span>

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

### <span data-ttu-id="beafb-130">Exempel 4: skapa ett multisträng-värde i registret med hjälp av en matris</span><span class="sxs-lookup"><span data-stu-id="beafb-130">Example 4: Create a MultiString value in the registry using an array</span></span>

<span data-ttu-id="beafb-131">Exemplet visar hur du använder en matris med värden för att skapa `MultiString` värdet.</span><span class="sxs-lookup"><span data-stu-id="beafb-131">The example shows how to use an array of values to create the `MultiString` value.</span></span>

```powershell
$newValue = New-ItemProperty -Path "HKLM:\SOFTWARE\ContosoCompany\" -Name 'MultiString' -PropertyType MultiString -Value ('a','b','c')
$newValue.multistring[0]
```

```output
a
```

## <span data-ttu-id="beafb-132">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="beafb-132">PARAMETERS</span></span>

### <span data-ttu-id="beafb-133">-Credential</span><span class="sxs-lookup"><span data-stu-id="beafb-133">-Credential</span></span>

<span data-ttu-id="beafb-134">Anger ett användar konto som har behörighet att utföra den här åtgärden.</span><span class="sxs-lookup"><span data-stu-id="beafb-134">Specifies a user account that has permission to perform this action.</span></span>
<span data-ttu-id="beafb-135">Standard är den aktuella användaren.</span><span class="sxs-lookup"><span data-stu-id="beafb-135">The default is the current user.</span></span>

<span data-ttu-id="beafb-136">Ange ett användar namn, till exempel "user01" eller "Domain01\User01", eller ange ett **PSCredential** -objekt, t. ex. ett som genererades av `Get-Credential` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="beafb-136">Type a user name, such as "User01" or "Domain01\User01", or enter a **PSCredential** object, such as one generated by the `Get-Credential` cmdlet.</span></span> <span data-ttu-id="beafb-137">Om du anger ett användar namn uppmanas du att ange ett lösen ord.</span><span class="sxs-lookup"><span data-stu-id="beafb-137">If you type a user name, you are prompted for a password.</span></span>

> [!NOTE]
> <span data-ttu-id="beafb-138">Den här parametern stöds inte av några providrar som installeras med PowerShell.</span><span class="sxs-lookup"><span data-stu-id="beafb-138">This parameter is not supported by any providers installed with PowerShell.</span></span>
> <span data-ttu-id="beafb-139">Om du vill personifiera en annan användare eller öka dina autentiseringsuppgifter när du kör denna cmdlet, använder du [Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md).</span><span class="sxs-lookup"><span data-stu-id="beafb-139">To impersonate another user, or elevate your credentials when running this cmdlet, use [Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md).</span></span>

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

### <span data-ttu-id="beafb-140">-Undanta</span><span class="sxs-lookup"><span data-stu-id="beafb-140">-Exclude</span></span>

<span data-ttu-id="beafb-141">Anger, som en sträng mat ris, en egenskap eller egenskap som denna cmdlet exkluderar från åtgärden.</span><span class="sxs-lookup"><span data-stu-id="beafb-141">Specifies, as a string array, a property or property that this cmdlet excludes from the operation.</span></span>
<span data-ttu-id="beafb-142">Värdet för den här parametern kvalificerar parametern **Path** .</span><span class="sxs-lookup"><span data-stu-id="beafb-142">The value of this parameter qualifies the **Path** parameter.</span></span>
<span data-ttu-id="beafb-143">Ange ett Sök vägs element eller ett mönster, till exempel "\*. txt".</span><span class="sxs-lookup"><span data-stu-id="beafb-143">Enter a path element or pattern, such as "\*.txt".</span></span>
<span data-ttu-id="beafb-144">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="beafb-144">Wildcard characters are permitted.</span></span>

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

### <span data-ttu-id="beafb-145">-Filter</span><span class="sxs-lookup"><span data-stu-id="beafb-145">-Filter</span></span>

<span data-ttu-id="beafb-146">Anger ett filter i formatet eller språket för providern.</span><span class="sxs-lookup"><span data-stu-id="beafb-146">Specifies a filter in the format or language of the provider.</span></span>
<span data-ttu-id="beafb-147">Värdet för den här parametern kvalificerar parametern **Path** .</span><span class="sxs-lookup"><span data-stu-id="beafb-147">The value of this parameter qualifies the **Path** parameter.</span></span>

<span data-ttu-id="beafb-148">Syntaxen för filtret, inklusive användning av jokertecken, är beroende av providern.</span><span class="sxs-lookup"><span data-stu-id="beafb-148">The syntax of the filter, including the use of wildcard characters, depends on the provider.</span></span> <span data-ttu-id="beafb-149">Filter är mer effektiva än andra parametrar, eftersom providern tillämpar dem när cmdleten hämtar objekten i stället för att ha PowerShell filtrera objekten när de har hämtats.</span><span class="sxs-lookup"><span data-stu-id="beafb-149">Filters are more efficient than other parameters, because the provider applies them when the cmdlet gets the objects rather than having PowerShell filter the objects after they are retrieved.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="beafb-150">-Force</span><span class="sxs-lookup"><span data-stu-id="beafb-150">-Force</span></span>

<span data-ttu-id="beafb-151">Tvingar cmdleten att skapa en egenskap för ett objekt som annars inte kan kommas åt av användaren.</span><span class="sxs-lookup"><span data-stu-id="beafb-151">Forces the cmdlet to create a property on an object that cannot otherwise be accessed by the user.</span></span>
<span data-ttu-id="beafb-152">Implementeringen varierar från providern till providern.</span><span class="sxs-lookup"><span data-stu-id="beafb-152">Implementation varies from provider to provider.</span></span>
<span data-ttu-id="beafb-153">Mer information finns i [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span><span class="sxs-lookup"><span data-stu-id="beafb-153">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

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

### <span data-ttu-id="beafb-154">-Inkludera</span><span class="sxs-lookup"><span data-stu-id="beafb-154">-Include</span></span>

<span data-ttu-id="beafb-155">Anger, som en sträng mat ris, ett objekt eller objekt som denna cmdlet inkluderar i åtgärden.</span><span class="sxs-lookup"><span data-stu-id="beafb-155">Specifies, as a string array, an item or items that this cmdlet includes in the operation.</span></span>
<span data-ttu-id="beafb-156">Värdet för den här parametern kvalificerar parametern **Path** .</span><span class="sxs-lookup"><span data-stu-id="beafb-156">The value of this parameter qualifies the **Path** parameter.</span></span>
<span data-ttu-id="beafb-157">Ange ett Sök vägs element eller ett mönster, till exempel "\*. txt".</span><span class="sxs-lookup"><span data-stu-id="beafb-157">Enter a path element or pattern, such as "\*.txt".</span></span>
<span data-ttu-id="beafb-158">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="beafb-158">Wildcard characters are permitted.</span></span>

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

### <span data-ttu-id="beafb-159">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="beafb-159">-LiteralPath</span></span>

<span data-ttu-id="beafb-160">Anger sökvägen till egenskapens aktuella plats.</span><span class="sxs-lookup"><span data-stu-id="beafb-160">Specifies the path to the current location of the property.</span></span>
<span data-ttu-id="beafb-161">Till skillnad från parametern **Path** används värdet för **LiteralPath** exakt som det har angetts.</span><span class="sxs-lookup"><span data-stu-id="beafb-161">Unlike the **Path** parameter, the value of **LiteralPath** is used exactly as it is typed.</span></span>
<span data-ttu-id="beafb-162">Inga tecken tolkas som jokertecken.</span><span class="sxs-lookup"><span data-stu-id="beafb-162">No characters are interpreted as wildcards.</span></span>
<span data-ttu-id="beafb-163">Om sökvägen innehåller escape-tecken omger du den med enkla citat tecken.</span><span class="sxs-lookup"><span data-stu-id="beafb-163">If the path includes escape characters, enclose it in single quotation marks.</span></span>
<span data-ttu-id="beafb-164">Enkla citat tecken säger att PowerShell inte tolkar några tecken som escape-sekvenser.</span><span class="sxs-lookup"><span data-stu-id="beafb-164">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

```yaml
Type: System.String[]
Parameter Sets: LiteralPath
Aliases: PSPath

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="beafb-165">-Name</span><span class="sxs-lookup"><span data-stu-id="beafb-165">-Name</span></span>

<span data-ttu-id="beafb-166">Anger ett namn för den nya egenskapen.</span><span class="sxs-lookup"><span data-stu-id="beafb-166">Specifies a name for the new property.</span></span>
<span data-ttu-id="beafb-167">Om egenskapen är en register post anger den här parametern namnet på posten.</span><span class="sxs-lookup"><span data-stu-id="beafb-167">If the property is a registry entry, this parameter specifies the name of the entry.</span></span>

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

### <span data-ttu-id="beafb-168">-Path</span><span class="sxs-lookup"><span data-stu-id="beafb-168">-Path</span></span>

<span data-ttu-id="beafb-169">Anger objektets sökväg.</span><span class="sxs-lookup"><span data-stu-id="beafb-169">Specifies the path of the item.</span></span>
<span data-ttu-id="beafb-170">Den här parametern identifierar objektet som den här cmdleten lägger till den nya egenskapen i.</span><span class="sxs-lookup"><span data-stu-id="beafb-170">This parameter identifies the item to which this cmdlet adds the new property.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Path
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="beafb-171">– PropertyType</span><span class="sxs-lookup"><span data-stu-id="beafb-171">-PropertyType</span></span>

<span data-ttu-id="beafb-172">Anger vilken typ av egenskap som denna cmdlet lägger till.</span><span class="sxs-lookup"><span data-stu-id="beafb-172">Specifies the type of property that this cmdlet adds.</span></span>
<span data-ttu-id="beafb-173">De acceptabla värdena för den här parametern är:</span><span class="sxs-lookup"><span data-stu-id="beafb-173">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="beafb-174">**Sträng** : anger en null-avslutad sträng.</span><span class="sxs-lookup"><span data-stu-id="beafb-174">**String** : Specifies a null-terminated string.</span></span> <span data-ttu-id="beafb-175">Motsvarar **REG_SZ**.</span><span class="sxs-lookup"><span data-stu-id="beafb-175">Equivalent to **REG_SZ**.</span></span>
- <span data-ttu-id="beafb-176">**ExpandString** : anger en null-avslutad sträng som innehåller expanderade referenser till miljövariabler som expanderas när värdet hämtas.</span><span class="sxs-lookup"><span data-stu-id="beafb-176">**ExpandString** : Specifies a null-terminated string that contains unexpanded references to environment variables that are expanded when the value is retrieved.</span></span> <span data-ttu-id="beafb-177">Motsvarar **REG_EXPAND_SZ**.</span><span class="sxs-lookup"><span data-stu-id="beafb-177">Equivalent to **REG_EXPAND_SZ**.</span></span>
- <span data-ttu-id="beafb-178">**Binary** : anger binära data i alla former.</span><span class="sxs-lookup"><span data-stu-id="beafb-178">**Binary** : Specifies binary data in any form.</span></span> <span data-ttu-id="beafb-179">Motsvarar **REG_BINARY**.</span><span class="sxs-lookup"><span data-stu-id="beafb-179">Equivalent to **REG_BINARY**.</span></span>
- <span data-ttu-id="beafb-180">**DWORD** : anger ett 32-bitars binärt tal.</span><span class="sxs-lookup"><span data-stu-id="beafb-180">**DWord** : Specifies a 32-bit binary number.</span></span> <span data-ttu-id="beafb-181">Motsvarar **REG_DWORD**.</span><span class="sxs-lookup"><span data-stu-id="beafb-181">Equivalent to **REG_DWORD**.</span></span>
- <span data-ttu-id="beafb-182">**Multisträng** : anger en matris med null-terminerade strängar som avslutas med två NULL-tecken.</span><span class="sxs-lookup"><span data-stu-id="beafb-182">**MultiString** : Specifies an array of null-terminated strings terminated by two null characters.</span></span>
  <span data-ttu-id="beafb-183">Motsvarar **REG_MULTI_SZ**.</span><span class="sxs-lookup"><span data-stu-id="beafb-183">Equivalent to **REG_MULTI_SZ**.</span></span>
- <span data-ttu-id="beafb-184">**QWORD** : anger ett 64-bitars binärt tal.</span><span class="sxs-lookup"><span data-stu-id="beafb-184">**Qword** : Specifies a 64-bit binary number.</span></span> <span data-ttu-id="beafb-185">Motsvarar **REG_QWORD**.</span><span class="sxs-lookup"><span data-stu-id="beafb-185">Equivalent to **REG_QWORD**.</span></span>
- <span data-ttu-id="beafb-186">**Okänd** : anger en register data typ som inte stöds, till exempel **REG_RESOURCE_LIST**.</span><span class="sxs-lookup"><span data-stu-id="beafb-186">**Unknown** : Indicates an unsupported registry data type, such as **REG_RESOURCE_LIST**.</span></span>

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

### <span data-ttu-id="beafb-187">– UseTransaction</span><span class="sxs-lookup"><span data-stu-id="beafb-187">-UseTransaction</span></span>

<span data-ttu-id="beafb-188">Inkluderar kommandot i den aktiva transaktionen.</span><span class="sxs-lookup"><span data-stu-id="beafb-188">Includes the command in the active transaction.</span></span>
<span data-ttu-id="beafb-189">Den här parametern är bara giltig medan en transaktion pågår.</span><span class="sxs-lookup"><span data-stu-id="beafb-189">This parameter is valid only when a transaction is in progress.</span></span>
<span data-ttu-id="beafb-190">Mer information finns i about_Transactions.</span><span class="sxs-lookup"><span data-stu-id="beafb-190">For more information, see about_Transactions.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: usetx

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="beafb-191">-Värde</span><span class="sxs-lookup"><span data-stu-id="beafb-191">-Value</span></span>

<span data-ttu-id="beafb-192">Anger egenskap svärdet.</span><span class="sxs-lookup"><span data-stu-id="beafb-192">Specifies the property value.</span></span>
<span data-ttu-id="beafb-193">Om egenskapen är en register post anger den här parametern värdet för posten.</span><span class="sxs-lookup"><span data-stu-id="beafb-193">If the property is a registry entry, this parameter specifies the value of the entry.</span></span>

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

### <span data-ttu-id="beafb-194">-Confirm</span><span class="sxs-lookup"><span data-stu-id="beafb-194">-Confirm</span></span>

<span data-ttu-id="beafb-195">Uppmanar dig att bekräfta innan du kör cmdleten.</span><span class="sxs-lookup"><span data-stu-id="beafb-195">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="beafb-196">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="beafb-196">-WhatIf</span></span>

<span data-ttu-id="beafb-197">Visar vad som skulle hända om cmdleten kördes.</span><span class="sxs-lookup"><span data-stu-id="beafb-197">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="beafb-198">Cmdleten körs inte.</span><span class="sxs-lookup"><span data-stu-id="beafb-198">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="beafb-199">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="beafb-199">CommonParameters</span></span>

<span data-ttu-id="beafb-200">Denna cmdlet stöder de gemensamma parametrarna:,,,,,,,, `-Debug` `-ErrorAction` `-ErrorVariable` `-InformationAction` `-InformationVariable` `-OutVariable` `-OutBuffer` `-PipelineVariable` `-Verbose` `-WarningAction` , och `-WarningVariable` .</span><span class="sxs-lookup"><span data-stu-id="beafb-200">This cmdlet supports the common parameters: `-Debug`, `-ErrorAction`, `-ErrorVariable`, `-InformationAction`, `-InformationVariable`, `-OutVariable`, `-OutBuffer`, `-PipelineVariable`, `-Verbose`, `-WarningAction`, and `-WarningVariable`.</span></span> <span data-ttu-id="beafb-201">Mer information finns i [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span><span class="sxs-lookup"><span data-stu-id="beafb-201">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="beafb-202">INDATA</span><span class="sxs-lookup"><span data-stu-id="beafb-202">INPUTS</span></span>

### <span data-ttu-id="beafb-203">Inget</span><span class="sxs-lookup"><span data-stu-id="beafb-203">None</span></span>

<span data-ttu-id="beafb-204">Du kan inte skicka pipe-ininformation till denna cmdlet.</span><span class="sxs-lookup"><span data-stu-id="beafb-204">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="beafb-205">UTDATA</span><span class="sxs-lookup"><span data-stu-id="beafb-205">OUTPUTS</span></span>

### <span data-ttu-id="beafb-206">System. Management. Automation. PSCustomObject</span><span class="sxs-lookup"><span data-stu-id="beafb-206">System.Management.Automation.PSCustomObject</span></span>

<span data-ttu-id="beafb-207">`New-ItemProperty` Returnerar ett anpassat objekt som innehåller den nya egenskapen.</span><span class="sxs-lookup"><span data-stu-id="beafb-207">`New-ItemProperty` returns a custom object that contains the new property.</span></span>

## <span data-ttu-id="beafb-208">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="beafb-208">NOTES</span></span>

<span data-ttu-id="beafb-209">`New-ItemProperty` är utformad för att fungera med data som exponeras av vilken provider som helst.</span><span class="sxs-lookup"><span data-stu-id="beafb-209">`New-ItemProperty` is designed to work with the data exposed by any provider.</span></span> <span data-ttu-id="beafb-210">Om du vill visa en lista över tillgängliga providers i din session skriver du `Get-PSProvider` .</span><span class="sxs-lookup"><span data-stu-id="beafb-210">To list the providers available in your session, type `Get-PSProvider`.</span></span> <span data-ttu-id="beafb-211">Mer information finns i [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span><span class="sxs-lookup"><span data-stu-id="beafb-211">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

## <span data-ttu-id="beafb-212">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="beafb-212">RELATED LINKS</span></span>

[<span data-ttu-id="beafb-213">Clear-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="beafb-213">Clear-ItemProperty</span></span>](Clear-ItemProperty.md)

[<span data-ttu-id="beafb-214">Kopiera – ItemProperty</span><span class="sxs-lookup"><span data-stu-id="beafb-214">Copy-ItemProperty</span></span>](Copy-ItemProperty.md)

[<span data-ttu-id="beafb-215">Get-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="beafb-215">Get-ItemProperty</span></span>](Get-ItemProperty.md)

[<span data-ttu-id="beafb-216">Move-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="beafb-216">Move-ItemProperty</span></span>](Move-ItemProperty.md)

[<span data-ttu-id="beafb-217">Remove-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="beafb-217">Remove-ItemProperty</span></span>](Remove-ItemProperty.md)

[<span data-ttu-id="beafb-218">Byt namn – ItemProperty</span><span class="sxs-lookup"><span data-stu-id="beafb-218">Rename-ItemProperty</span></span>](Rename-ItemProperty.md)

[<span data-ttu-id="beafb-219">Set-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="beafb-219">Set-ItemProperty</span></span>](Set-ItemProperty.md)

[<span data-ttu-id="beafb-220">about_Providers</span><span class="sxs-lookup"><span data-stu-id="beafb-220">about_Providers</span></span>](../Microsoft.PowerShell.Core/About/about_Providers.md)
