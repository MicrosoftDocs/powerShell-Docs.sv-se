---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 05/14/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/remove-itemproperty?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Remove-ItemProperty
ms.openlocfilehash: 870d8e9797ff2cfce14034706f704c0e1c954fc2
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94710164"
---
# <span data-ttu-id="3da0e-102">Remove-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="3da0e-102">Remove-ItemProperty</span></span>

## <span data-ttu-id="3da0e-103">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="3da0e-103">SYNOPSIS</span></span>
<span data-ttu-id="3da0e-104">Tar bort egenskapen och dess värde från ett objekt.</span><span class="sxs-lookup"><span data-stu-id="3da0e-104">Deletes the property and its value from an item.</span></span>

## <span data-ttu-id="3da0e-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="3da0e-105">SYNTAX</span></span>

### <span data-ttu-id="3da0e-106">Sökväg (standard)</span><span class="sxs-lookup"><span data-stu-id="3da0e-106">Path (Default)</span></span>

```
Remove-ItemProperty [-Path] <String[]> [-Name] <String[]> [-Force] [-Filter <String>] [-Include <String[]>]
 [-Exclude <String[]>] [-Credential <PSCredential>] [-InformationAction <ActionPreference>]
 [-InformationVariable <String>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="3da0e-107">LiteralPath</span><span class="sxs-lookup"><span data-stu-id="3da0e-107">LiteralPath</span></span>

```
Remove-ItemProperty -LiteralPath <String[]> [-Name] <String[]> [-Force] [-Filter <String>]
 [-Include <String[]>] [-Exclude <String[]>] [-Credential <PSCredential>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="3da0e-108">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="3da0e-108">DESCRIPTION</span></span>

<span data-ttu-id="3da0e-109">`Remove-ItemProperty`Cmdleten tar bort en egenskap och dess värde från ett objekt.</span><span class="sxs-lookup"><span data-stu-id="3da0e-109">The `Remove-ItemProperty` cmdlet deletes a property and its value from an item.</span></span>
<span data-ttu-id="3da0e-110">Du kan använda den för att ta bort register värden och de data som de lagrar.</span><span class="sxs-lookup"><span data-stu-id="3da0e-110">You can use it to delete registry values and the data that they store.</span></span>

## <span data-ttu-id="3da0e-111">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="3da0e-111">EXAMPLES</span></span>

### <span data-ttu-id="3da0e-112">Exempel 1: ta bort ett register värde</span><span class="sxs-lookup"><span data-stu-id="3da0e-112">Example 1: Delete a registry value</span></span>

<span data-ttu-id="3da0e-113">Det här kommandot tar bort registervärdet "SmpProperty" och dess data från under nyckeln "SmpApplication" i `HKEY_LOCAL_MACHINE\Software` register nyckeln.</span><span class="sxs-lookup"><span data-stu-id="3da0e-113">This command deletes the "SmpProperty" registry value, and its data, from the "SmpApplication" subkey of the `HKEY_LOCAL_MACHINE\Software` registry key.</span></span>

```powershell
Remove-ItemProperty -Path "HKLM:\Software\SmpApplication" -Name "SmpProperty"
```

<span data-ttu-id="3da0e-114">Eftersom kommandot utfärdas från en fil system enhet ( `PS C:\>` ), innehåller det den fullständigt kvalificerade sökvägen till "SmpApplication"-under nyckeln, inklusive enheten, `HKLM:` och nyckeln "Software".</span><span class="sxs-lookup"><span data-stu-id="3da0e-114">Because the command is issued from a file system drive (`PS C:\>`), it includes the fully qualified path of the "SmpApplication" subkey, including the drive, `HKLM:`, and the "Software" key.</span></span>

### <span data-ttu-id="3da0e-115">Exempel 2: ta bort ett register värde från HKCU-platsen</span><span class="sxs-lookup"><span data-stu-id="3da0e-115">Example 2: Delete a registry value from the HKCU location</span></span>

<span data-ttu-id="3da0e-116">De här kommandona tar bort registervärdet "Options" och dess data från under nyckeln "mitt" i "HKEY_CURRENT_USER\Software\MyCompany".</span><span class="sxs-lookup"><span data-stu-id="3da0e-116">These commands delete the "Options" registry value, and its data, from the "MyApp" subkey of "HKEY_CURRENT_USER\Software\MyCompany".</span></span>

```
PS C:\> Set-Location HKCU:\Software\MyCompany\MyApp
PS HKCU:\Software\MyCompany\MyApp> Remove-ItemProperty -Path . -Name "Options" -Confirm
```

<span data-ttu-id="3da0e-117">Det första kommandot använder `Set-Location` cmdleten för att ändra den aktuella platsen till **HKEY_CURRENT_USER** -enheten ( `HKCU:` ) och `Software\MyCompany\MyApp` under nyckeln.</span><span class="sxs-lookup"><span data-stu-id="3da0e-117">The first command uses the `Set-Location` cmdlet to change the current location to the **HKEY_CURRENT_USER** drive (`HKCU:`) and the `Software\MyCompany\MyApp` subkey.</span></span>

<span data-ttu-id="3da0e-118">Det andra kommandot använder `Remove-ItemProperty` för att ta bort register värden för "alternativ" och dess data från under nyckeln "mitt".</span><span class="sxs-lookup"><span data-stu-id="3da0e-118">The second command uses `Remove-ItemProperty` to remove the "Options" registry value, and its data, from the "MyApp" subkey.</span></span> <span data-ttu-id="3da0e-119">Eftersom **sökvägen** är obligatorisk använder kommandot en punkt ( `.` ) för att ange den aktuella platsen.</span><span class="sxs-lookup"><span data-stu-id="3da0e-119">Because **Path** is required, the command uses a dot (`.`) to indicate the current location.</span></span> <span data-ttu-id="3da0e-120">Parametern **Confirm** begär en användar fråga innan värdet tas bort.</span><span class="sxs-lookup"><span data-stu-id="3da0e-120">The **Confirm** parameter requests a user prompt before deleting the value.</span></span>

### <span data-ttu-id="3da0e-121">Exempel 3: ta bort ett register värde med hjälp av pipelinen</span><span class="sxs-lookup"><span data-stu-id="3da0e-121">Example 3: Remove a registry value by using the pipeline</span></span>

<span data-ttu-id="3da0e-122">Det här kommandot tar bort registervärdet "NoOfEmployees" och dess data från `HKLM\Software\MyCompany` register nyckeln.</span><span class="sxs-lookup"><span data-stu-id="3da0e-122">This command deletes the "NoOfEmployees" registry value, and its data, from the `HKLM\Software\MyCompany` registry key.</span></span>

```powershell
Get-Item -Path HKLM:\Software\MyCompany | Remove-ItemProperty -Name NoOfEmployees
```

<span data-ttu-id="3da0e-123">Kommandot använder `Get-Item` cmdleten för att hämta ett objekt som representerar register nyckeln.</span><span class="sxs-lookup"><span data-stu-id="3da0e-123">The command uses the `Get-Item` cmdlet to get an item that represents the registry key.</span></span>
<span data-ttu-id="3da0e-124">En pipeline-operator () används `|` för att skicka objektet till `Remove-ItemProperty` .</span><span class="sxs-lookup"><span data-stu-id="3da0e-124">It uses a pipeline operator (`|`) to send the object to `Remove-ItemProperty`.</span></span>
<span data-ttu-id="3da0e-125">Sedan använder den **Name** -parametern för `Remove-ItemProperty` att ange namnet på registervärdet.</span><span class="sxs-lookup"><span data-stu-id="3da0e-125">Then, it uses the **Name** parameter of `Remove-ItemProperty` to specify the name of the registry value.</span></span>

## <span data-ttu-id="3da0e-126">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="3da0e-126">PARAMETERS</span></span>

### <span data-ttu-id="3da0e-127">-Credential</span><span class="sxs-lookup"><span data-stu-id="3da0e-127">-Credential</span></span>

> [!NOTE]
> <span data-ttu-id="3da0e-128">Den här parametern stöds inte av några providrar som installeras med PowerShell.</span><span class="sxs-lookup"><span data-stu-id="3da0e-128">This parameter is not supported by any providers installed with PowerShell.</span></span>
> <span data-ttu-id="3da0e-129">Om du vill personifiera en annan användare eller öka dina autentiseringsuppgifter när du kör denna cmdlet, använder du [Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md).</span><span class="sxs-lookup"><span data-stu-id="3da0e-129">To impersonate another user, or elevate your credentials when running this cmdlet, use [Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md).</span></span>

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

### <span data-ttu-id="3da0e-130">-Undanta</span><span class="sxs-lookup"><span data-stu-id="3da0e-130">-Exclude</span></span>

<span data-ttu-id="3da0e-131">Anger, som en sträng mat ris, ett objekt eller objekt som denna cmdlet exkluderar i åtgärden.</span><span class="sxs-lookup"><span data-stu-id="3da0e-131">Specifies, as a string array, an item or items that this cmdlet excludes in the operation.</span></span> <span data-ttu-id="3da0e-132">Värdet för den här parametern kvalificerar parametern **Path** .</span><span class="sxs-lookup"><span data-stu-id="3da0e-132">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="3da0e-133">Ange ett Sök vägs element eller ett mönster, till exempel `*.txt` .</span><span class="sxs-lookup"><span data-stu-id="3da0e-133">Enter a path element or pattern, such as `*.txt`.</span></span> <span data-ttu-id="3da0e-134">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="3da0e-134">Wildcard characters are permitted.</span></span> <span data-ttu-id="3da0e-135">Parametern **exclude** är endast effektiv när kommandot innehåller innehållet i ett objekt, t. ex `C:\Windows\*` ., där jokertecknet anger innehållet i `C:\Windows` katalogen.</span><span class="sxs-lookup"><span data-stu-id="3da0e-135">The **Exclude** parameter is effective only when the command includes the contents of an item, such as `C:\Windows\*`, where the wildcard character specifies the contents of the `C:\Windows` directory.</span></span>

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

### <span data-ttu-id="3da0e-136">-Filter</span><span class="sxs-lookup"><span data-stu-id="3da0e-136">-Filter</span></span>

<span data-ttu-id="3da0e-137">Anger ett filter för att kvalificera **Sök vägs** parametern.</span><span class="sxs-lookup"><span data-stu-id="3da0e-137">Specifies a filter to qualify the **Path** parameter.</span></span> <span data-ttu-id="3da0e-138">[Fil Systems](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md) leverantören är den enda installerade PowerShell-providern som stöder användningen av filter.</span><span class="sxs-lookup"><span data-stu-id="3da0e-138">The [FileSystem](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md) provider is the only installed PowerShell provider that supports the use of filters.</span></span> <span data-ttu-id="3da0e-139">Du kan hitta syntaxen för filter språket för **fil systemet** i [about_Wildcards](../Microsoft.PowerShell.Core/About/about_Wildcards.md).</span><span class="sxs-lookup"><span data-stu-id="3da0e-139">You can find the syntax for the **FileSystem** filter language in [about_Wildcards](../Microsoft.PowerShell.Core/About/about_Wildcards.md).</span></span>
<span data-ttu-id="3da0e-140">Filter är mer effektiva än andra parametrar, eftersom providern tillämpar dem när cmdleten hämtar objekten i stället för att ha PowerShell filtrera objekten när de har hämtats.</span><span class="sxs-lookup"><span data-stu-id="3da0e-140">Filters are more efficient than other parameters, because the provider applies them when the cmdlet gets the objects rather than having PowerShell filter the objects after they are retrieved.</span></span>

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

### <span data-ttu-id="3da0e-141">-Force</span><span class="sxs-lookup"><span data-stu-id="3da0e-141">-Force</span></span>

<span data-ttu-id="3da0e-142">Tvingar cmdleten att ta bort en egenskap för ett objekt som annars inte kan kommas åt av användaren.</span><span class="sxs-lookup"><span data-stu-id="3da0e-142">Forces the cmdlet to remove a property of an object that cannot otherwise be accessed by the user.</span></span>
<span data-ttu-id="3da0e-143">Implementeringen varierar från providern till providern.</span><span class="sxs-lookup"><span data-stu-id="3da0e-143">Implementation varies from provider to provider.</span></span>
<span data-ttu-id="3da0e-144">Mer information finns i [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span><span class="sxs-lookup"><span data-stu-id="3da0e-144">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

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

### <span data-ttu-id="3da0e-145">-Inkludera</span><span class="sxs-lookup"><span data-stu-id="3da0e-145">-Include</span></span>

<span data-ttu-id="3da0e-146">Anger, som en sträng mat ris, ett objekt eller objekt som denna cmdlet inkluderar i åtgärden.</span><span class="sxs-lookup"><span data-stu-id="3da0e-146">Specifies, as a string array, an item or items that this cmdlet includes in the operation.</span></span> <span data-ttu-id="3da0e-147">Värdet för den här parametern kvalificerar parametern **Path** .</span><span class="sxs-lookup"><span data-stu-id="3da0e-147">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="3da0e-148">Ange ett Sök vägs element eller ett mönster, till exempel `"*.txt"` .</span><span class="sxs-lookup"><span data-stu-id="3da0e-148">Enter a path element or pattern, such as `"*.txt"`.</span></span> <span data-ttu-id="3da0e-149">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="3da0e-149">Wildcard characters are permitted.</span></span> <span data-ttu-id="3da0e-150">Parametern **include** är endast effektiv när kommandot innehåller innehållet i ett objekt, t. ex `C:\Windows\*` ., där jokertecknet anger innehållet i `C:\Windows` katalogen.</span><span class="sxs-lookup"><span data-stu-id="3da0e-150">The **Include** parameter is effective only when the command includes the contents of an item, such as `C:\Windows\*`, where the wildcard character specifies the contents of the `C:\Windows` directory.</span></span>

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

### <span data-ttu-id="3da0e-151">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="3da0e-151">-LiteralPath</span></span>

<span data-ttu-id="3da0e-152">Anger en sökväg till en eller flera platser.</span><span class="sxs-lookup"><span data-stu-id="3da0e-152">Specifies a path to one or more locations.</span></span> <span data-ttu-id="3da0e-153">Värdet för **LiteralPath** används exakt som det har angetts.</span><span class="sxs-lookup"><span data-stu-id="3da0e-153">The value of **LiteralPath** is used exactly as it is typed.</span></span> <span data-ttu-id="3da0e-154">Inga tecken tolkas som jokertecken.</span><span class="sxs-lookup"><span data-stu-id="3da0e-154">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="3da0e-155">Om sökvägen innehåller escape-tecken omger du den med enkla citat tecken.</span><span class="sxs-lookup"><span data-stu-id="3da0e-155">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="3da0e-156">Enkla citat tecken säger att PowerShell inte tolkar några tecken som escape-sekvenser.</span><span class="sxs-lookup"><span data-stu-id="3da0e-156">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

<span data-ttu-id="3da0e-157">Mer information finns i [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md).</span><span class="sxs-lookup"><span data-stu-id="3da0e-157">For more information, see [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md).</span></span>

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

### <span data-ttu-id="3da0e-158">-Name</span><span class="sxs-lookup"><span data-stu-id="3da0e-158">-Name</span></span>

<span data-ttu-id="3da0e-159">Anger namnen på de egenskaper som ska tas bort.</span><span class="sxs-lookup"><span data-stu-id="3da0e-159">Specifies the names of the properties to remove.</span></span>
<span data-ttu-id="3da0e-160">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="3da0e-160">Wildcard characters are permitted.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: PSProperty

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### <span data-ttu-id="3da0e-161">-Path</span><span class="sxs-lookup"><span data-stu-id="3da0e-161">-Path</span></span>

<span data-ttu-id="3da0e-162">Anger sökvägen till det objekt vars egenskaper tas bort.</span><span class="sxs-lookup"><span data-stu-id="3da0e-162">Specifies the path of the item whose properties are being removed.</span></span>
<span data-ttu-id="3da0e-163">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="3da0e-163">Wildcard characters are permitted.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Path
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### <span data-ttu-id="3da0e-164">-Confirm</span><span class="sxs-lookup"><span data-stu-id="3da0e-164">-Confirm</span></span>

<span data-ttu-id="3da0e-165">Uppmanar dig att bekräfta innan du kör cmdleten.</span><span class="sxs-lookup"><span data-stu-id="3da0e-165">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="3da0e-166">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="3da0e-166">-WhatIf</span></span>

<span data-ttu-id="3da0e-167">Visar vad som skulle hända om cmdleten kördes.</span><span class="sxs-lookup"><span data-stu-id="3da0e-167">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="3da0e-168">Cmdleten körs inte.</span><span class="sxs-lookup"><span data-stu-id="3da0e-168">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="3da0e-169">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="3da0e-169">CommonParameters</span></span>

<span data-ttu-id="3da0e-170">Denna cmdlet stöder de gemensamma parametrarna:,,,,,,,, `-Debug` `-ErrorAction` `-ErrorVariable` `-InformationAction` `-InformationVariable` `-OutVariable` `-OutBuffer` `-PipelineVariable` `-Verbose` `-WarningAction` , och `-WarningVariable` .</span><span class="sxs-lookup"><span data-stu-id="3da0e-170">This cmdlet supports the common parameters: `-Debug`, `-ErrorAction`, `-ErrorVariable`, `-InformationAction`, `-InformationVariable`, `-OutVariable`, `-OutBuffer`, `-PipelineVariable`, `-Verbose`, `-WarningAction`, and `-WarningVariable`.</span></span> <span data-ttu-id="3da0e-171">Mer information finns i [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span><span class="sxs-lookup"><span data-stu-id="3da0e-171">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="3da0e-172">INDATA</span><span class="sxs-lookup"><span data-stu-id="3da0e-172">INPUTS</span></span>

### <span data-ttu-id="3da0e-173">System. String</span><span class="sxs-lookup"><span data-stu-id="3da0e-173">System.String</span></span>

<span data-ttu-id="3da0e-174">Du kan skicka vidare en sträng som innehåller en sökväg, men inte en literal sökväg, till denna cmdlet.</span><span class="sxs-lookup"><span data-stu-id="3da0e-174">You can pipe a string that contains a path, but not a literal path, to this cmdlet.</span></span>

## <span data-ttu-id="3da0e-175">UTDATA</span><span class="sxs-lookup"><span data-stu-id="3da0e-175">OUTPUTS</span></span>

### <span data-ttu-id="3da0e-176">Inga</span><span class="sxs-lookup"><span data-stu-id="3da0e-176">None</span></span>

<span data-ttu-id="3da0e-177">Denna cmdlet returnerar inga utdata.</span><span class="sxs-lookup"><span data-stu-id="3da0e-177">This cmdlet does not return any output.</span></span>

## <span data-ttu-id="3da0e-178">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="3da0e-178">NOTES</span></span>

- <span data-ttu-id="3da0e-179">I PowerShell-registerposten betraktas register värden som egenskaper för en register nyckel eller under nyckel.</span><span class="sxs-lookup"><span data-stu-id="3da0e-179">In the PowerShell Registry provider, registry values are considered to be properties of a registry key or subkey.</span></span> <span data-ttu-id="3da0e-180">Du kan använda **ItemProperty** -cmdletar för att hantera dessa värden.</span><span class="sxs-lookup"><span data-stu-id="3da0e-180">You can use the **ItemProperty** cmdlets to manage these values.</span></span>
- <span data-ttu-id="3da0e-181">`Remove-ItemProperty` är utformad för att fungera med data som exponeras av vilken provider som helst.</span><span class="sxs-lookup"><span data-stu-id="3da0e-181">`Remove-ItemProperty` is designed to work with the data exposed by any provider.</span></span> <span data-ttu-id="3da0e-182">Om du vill visa en lista över tillgängliga providers i din session skriver du `Get-PSProvider` .</span><span class="sxs-lookup"><span data-stu-id="3da0e-182">To list the providers available in your session, type `Get-PSProvider`.</span></span> <span data-ttu-id="3da0e-183">Mer information finns i [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span><span class="sxs-lookup"><span data-stu-id="3da0e-183">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

## <span data-ttu-id="3da0e-184">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="3da0e-184">RELATED LINKS</span></span>

[<span data-ttu-id="3da0e-185">Hämta objekt</span><span class="sxs-lookup"><span data-stu-id="3da0e-185">Get-Item</span></span>](Get-Item.md)

[<span data-ttu-id="3da0e-186">Clear-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="3da0e-186">Clear-ItemProperty</span></span>](Clear-ItemProperty.md)

[<span data-ttu-id="3da0e-187">Kopiera – ItemProperty</span><span class="sxs-lookup"><span data-stu-id="3da0e-187">Copy-ItemProperty</span></span>](Copy-ItemProperty.md)

[<span data-ttu-id="3da0e-188">Get-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="3da0e-188">Get-ItemProperty</span></span>](Get-ItemProperty.md)

[<span data-ttu-id="3da0e-189">Move-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="3da0e-189">Move-ItemProperty</span></span>](Move-ItemProperty.md)

[<span data-ttu-id="3da0e-190">New-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="3da0e-190">New-ItemProperty</span></span>](New-ItemProperty.md)

[<span data-ttu-id="3da0e-191">Ta bort objekt</span><span class="sxs-lookup"><span data-stu-id="3da0e-191">Remove-Item</span></span>](Remove-Item.md)

[<span data-ttu-id="3da0e-192">Byt namn – ItemProperty</span><span class="sxs-lookup"><span data-stu-id="3da0e-192">Rename-ItemProperty</span></span>](Rename-ItemProperty.md)

[<span data-ttu-id="3da0e-193">Set-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="3da0e-193">Set-ItemProperty</span></span>](Set-ItemProperty.md)

[<span data-ttu-id="3da0e-194">Ange plats</span><span class="sxs-lookup"><span data-stu-id="3da0e-194">Set-Location</span></span>](Set-Location.md)

[<span data-ttu-id="3da0e-195">about_Providers</span><span class="sxs-lookup"><span data-stu-id="3da0e-195">about_Providers</span></span>](../Microsoft.PowerShell.Core/About/about_Providers.md)

