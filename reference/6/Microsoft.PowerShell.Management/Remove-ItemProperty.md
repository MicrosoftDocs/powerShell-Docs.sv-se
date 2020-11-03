---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 5/14/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/remove-itemproperty?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Remove-ItemProperty
ms.openlocfilehash: 37d2d8a261f340a38487f042d460dcf6e4098d49
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93267254"
---
# <span data-ttu-id="515e6-103">Remove-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="515e6-103">Remove-ItemProperty</span></span>

## <span data-ttu-id="515e6-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="515e6-104">SYNOPSIS</span></span>
<span data-ttu-id="515e6-105">Tar bort egenskapen och dess värde från ett objekt.</span><span class="sxs-lookup"><span data-stu-id="515e6-105">Deletes the property and its value from an item.</span></span>

## <span data-ttu-id="515e6-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="515e6-106">SYNTAX</span></span>

### <span data-ttu-id="515e6-107">Sökväg (standard)</span><span class="sxs-lookup"><span data-stu-id="515e6-107">Path (Default)</span></span>

```
Remove-ItemProperty [-Path] <String[]> [-Name] <String[]> [-Force] [-Filter <String>]
 [-Include <String[]>] [-Exclude <String[]>] [-Credential <PSCredential>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### <span data-ttu-id="515e6-108">LiteralPath</span><span class="sxs-lookup"><span data-stu-id="515e6-108">LiteralPath</span></span>

```
Remove-ItemProperty -LiteralPath <String[]> [-Name] <String[]> [-Force] [-Filter <String>]
 [-Include <String[]>] [-Exclude <String[]>] [-Credential <PSCredential>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## <span data-ttu-id="515e6-109">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="515e6-109">DESCRIPTION</span></span>

<span data-ttu-id="515e6-110">`Remove-ItemProperty`Cmdleten tar bort en egenskap och dess värde från ett objekt.</span><span class="sxs-lookup"><span data-stu-id="515e6-110">The `Remove-ItemProperty` cmdlet deletes a property and its value from an item.</span></span>
<span data-ttu-id="515e6-111">Du kan använda den för att ta bort register värden och de data som de lagrar.</span><span class="sxs-lookup"><span data-stu-id="515e6-111">You can use it to delete registry values and the data that they store.</span></span>

## <span data-ttu-id="515e6-112">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="515e6-112">EXAMPLES</span></span>

### <span data-ttu-id="515e6-113">Exempel 1: ta bort ett register värde</span><span class="sxs-lookup"><span data-stu-id="515e6-113">Example 1: Delete a registry value</span></span>

<span data-ttu-id="515e6-114">Det här kommandot tar bort registervärdet "SmpProperty" och dess data från under nyckeln "SmpApplication" i `HKEY_LOCAL_MACHINE\Software` register nyckeln.</span><span class="sxs-lookup"><span data-stu-id="515e6-114">This command deletes the "SmpProperty" registry value, and its data, from the "SmpApplication" subkey of the `HKEY_LOCAL_MACHINE\Software` registry key.</span></span>

```powershell
Remove-ItemProperty -Path "HKLM:\Software\SmpApplication" -Name "SmpProperty"
```

<span data-ttu-id="515e6-115">Eftersom kommandot utfärdas från en fil system enhet ( `PS C:\>` ), innehåller det den fullständigt kvalificerade sökvägen till "SmpApplication"-under nyckeln, inklusive enheten, `HKLM:` och nyckeln "Software".</span><span class="sxs-lookup"><span data-stu-id="515e6-115">Because the command is issued from a file system drive (`PS C:\>`), it includes the fully qualified path of the "SmpApplication" subkey, including the drive, `HKLM:`, and the "Software" key.</span></span>

### <span data-ttu-id="515e6-116">Exempel 2: ta bort ett register värde från HKCU-platsen</span><span class="sxs-lookup"><span data-stu-id="515e6-116">Example 2: Delete a registry value from the HKCU location</span></span>

<span data-ttu-id="515e6-117">De här kommandona tar bort registervärdet "Options" och dess data från under nyckeln "mitt" i "HKEY_CURRENT_USER\Software\MyCompany".</span><span class="sxs-lookup"><span data-stu-id="515e6-117">These commands delete the "Options" registry value, and its data, from the "MyApp" subkey of "HKEY_CURRENT_USER\Software\MyCompany".</span></span>

```
PS C:\> Set-Location HKCU:\Software\MyCompany\MyApp
PS HKCU:\Software\MyCompany\MyApp> Remove-ItemProperty -Path . -Name "Options" -Confirm
```

<span data-ttu-id="515e6-118">Det första kommandot använder `Set-Location` cmdleten för att ändra den aktuella platsen till **HKEY_CURRENT_USER** -enheten ( `HKCU:` ) och `Software\MyCompany\MyApp` under nyckeln.</span><span class="sxs-lookup"><span data-stu-id="515e6-118">The first command uses the `Set-Location` cmdlet to change the current location to the **HKEY_CURRENT_USER** drive (`HKCU:`) and the `Software\MyCompany\MyApp` subkey.</span></span>

<span data-ttu-id="515e6-119">Det andra kommandot använder `Remove-ItemProperty` för att ta bort register värden för "alternativ" och dess data från under nyckeln "mitt".</span><span class="sxs-lookup"><span data-stu-id="515e6-119">The second command uses `Remove-ItemProperty` to remove the "Options" registry value, and its data, from the "MyApp" subkey.</span></span> <span data-ttu-id="515e6-120">Eftersom **sökvägen** är obligatorisk använder kommandot en punkt ( `.` ) för att ange den aktuella platsen.</span><span class="sxs-lookup"><span data-stu-id="515e6-120">Because **Path** is required, the command uses a dot (`.`) to indicate the current location.</span></span> <span data-ttu-id="515e6-121">Parametern **Confirm** begär en användar fråga innan värdet tas bort.</span><span class="sxs-lookup"><span data-stu-id="515e6-121">The **Confirm** parameter requests a user prompt before deleting the value.</span></span>

### <span data-ttu-id="515e6-122">Exempel 3: ta bort ett register värde med hjälp av pipelinen</span><span class="sxs-lookup"><span data-stu-id="515e6-122">Example 3: Remove a registry value by using the pipeline</span></span>

<span data-ttu-id="515e6-123">Det här kommandot tar bort registervärdet "NoOfEmployees" och dess data från `HKLM\Software\MyCompany` register nyckeln.</span><span class="sxs-lookup"><span data-stu-id="515e6-123">This command deletes the "NoOfEmployees" registry value, and its data, from the `HKLM\Software\MyCompany` registry key.</span></span>

```powershell
Get-Item -Path HKLM:\Software\MyCompany | Remove-ItemProperty -Name NoOfEmployees
```

<span data-ttu-id="515e6-124">Kommandot använder `Get-Item` cmdleten för att hämta ett objekt som representerar register nyckeln.</span><span class="sxs-lookup"><span data-stu-id="515e6-124">The command uses the `Get-Item` cmdlet to get an item that represents the registry key.</span></span>
<span data-ttu-id="515e6-125">En pipeline-operator () används `|` för att skicka objektet till `Remove-ItemProperty` .</span><span class="sxs-lookup"><span data-stu-id="515e6-125">It uses a pipeline operator (`|`) to send the object to `Remove-ItemProperty`.</span></span>
<span data-ttu-id="515e6-126">Sedan använder den **Name** -parametern för `Remove-ItemProperty` att ange namnet på registervärdet.</span><span class="sxs-lookup"><span data-stu-id="515e6-126">Then, it uses the **Name** parameter of `Remove-ItemProperty` to specify the name of the registry value.</span></span>

## <span data-ttu-id="515e6-127">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="515e6-127">PARAMETERS</span></span>

### <span data-ttu-id="515e6-128">-Credential</span><span class="sxs-lookup"><span data-stu-id="515e6-128">-Credential</span></span>

> [!NOTE]
> <span data-ttu-id="515e6-129">Den här parametern stöds inte av några providrar som installeras med PowerShell.</span><span class="sxs-lookup"><span data-stu-id="515e6-129">This parameter is not supported by any providers installed with PowerShell.</span></span>
> <span data-ttu-id="515e6-130">Om du vill personifiera en annan användare eller öka dina autentiseringsuppgifter när du kör denna cmdlet, använder du [Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md).</span><span class="sxs-lookup"><span data-stu-id="515e6-130">To impersonate another user, or elevate your credentials when running this cmdlet, use [Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md).</span></span>

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

### <span data-ttu-id="515e6-131">-Undanta</span><span class="sxs-lookup"><span data-stu-id="515e6-131">-Exclude</span></span>

<span data-ttu-id="515e6-132">Anger, som en sträng mat ris, ett objekt eller objekt som denna cmdlet exkluderar i åtgärden.</span><span class="sxs-lookup"><span data-stu-id="515e6-132">Specifies, as a string array, an item or items that this cmdlet excludes in the operation.</span></span> <span data-ttu-id="515e6-133">Värdet för den här parametern kvalificerar parametern **Path** .</span><span class="sxs-lookup"><span data-stu-id="515e6-133">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="515e6-134">Ange ett Sök vägs element eller ett mönster, till exempel `*.txt` .</span><span class="sxs-lookup"><span data-stu-id="515e6-134">Enter a path element or pattern, such as `*.txt`.</span></span> <span data-ttu-id="515e6-135">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="515e6-135">Wildcard characters are permitted.</span></span> <span data-ttu-id="515e6-136">Parametern **exclude** är endast effektiv när kommandot innehåller innehållet i ett objekt, t. ex `C:\Windows\*` ., där jokertecknet anger innehållet i `C:\Windows` katalogen.</span><span class="sxs-lookup"><span data-stu-id="515e6-136">The **Exclude** parameter is effective only when the command includes the contents of an item, such as `C:\Windows\*`, where the wildcard character specifies the contents of the `C:\Windows` directory.</span></span>

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

### <span data-ttu-id="515e6-137">-Filter</span><span class="sxs-lookup"><span data-stu-id="515e6-137">-Filter</span></span>

<span data-ttu-id="515e6-138">Anger ett filter för att kvalificera **Sök vägs** parametern.</span><span class="sxs-lookup"><span data-stu-id="515e6-138">Specifies a filter to qualify the **Path** parameter.</span></span> <span data-ttu-id="515e6-139">[Fil Systems](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md) leverantören är den enda installerade PowerShell-providern som stöder användningen av filter.</span><span class="sxs-lookup"><span data-stu-id="515e6-139">The [FileSystem](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md) provider is the only installed PowerShell provider that supports the use of filters.</span></span> <span data-ttu-id="515e6-140">Du kan hitta syntaxen för filter språket för **fil systemet** i [about_Wildcards](../Microsoft.PowerShell.Core/About/about_Wildcards.md).</span><span class="sxs-lookup"><span data-stu-id="515e6-140">You can find the syntax for the **FileSystem** filter language in [about_Wildcards](../Microsoft.PowerShell.Core/About/about_Wildcards.md).</span></span>
<span data-ttu-id="515e6-141">Filter är mer effektiva än andra parametrar, eftersom providern tillämpar dem när cmdleten hämtar objekten i stället för att ha PowerShell filtrera objekten när de har hämtats.</span><span class="sxs-lookup"><span data-stu-id="515e6-141">Filters are more efficient than other parameters, because the provider applies them when the cmdlet gets the objects rather than having PowerShell filter the objects after they are retrieved.</span></span>

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

### <span data-ttu-id="515e6-142">-Force</span><span class="sxs-lookup"><span data-stu-id="515e6-142">-Force</span></span>

<span data-ttu-id="515e6-143">Tvingar cmdleten att ta bort en egenskap för ett objekt som annars inte kan kommas åt av användaren.</span><span class="sxs-lookup"><span data-stu-id="515e6-143">Forces the cmdlet to remove a property of an object that cannot otherwise be accessed by the user.</span></span>
<span data-ttu-id="515e6-144">Implementeringen varierar från providern till providern.</span><span class="sxs-lookup"><span data-stu-id="515e6-144">Implementation varies from provider to provider.</span></span>
<span data-ttu-id="515e6-145">Mer information finns i [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span><span class="sxs-lookup"><span data-stu-id="515e6-145">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

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

### <span data-ttu-id="515e6-146">-Inkludera</span><span class="sxs-lookup"><span data-stu-id="515e6-146">-Include</span></span>

<span data-ttu-id="515e6-147">Anger, som en sträng mat ris, ett objekt eller objekt som denna cmdlet inkluderar i åtgärden.</span><span class="sxs-lookup"><span data-stu-id="515e6-147">Specifies, as a string array, an item or items that this cmdlet includes in the operation.</span></span> <span data-ttu-id="515e6-148">Värdet för den här parametern kvalificerar parametern **Path** .</span><span class="sxs-lookup"><span data-stu-id="515e6-148">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="515e6-149">Ange ett Sök vägs element eller ett mönster, till exempel `"*.txt"` .</span><span class="sxs-lookup"><span data-stu-id="515e6-149">Enter a path element or pattern, such as `"*.txt"`.</span></span> <span data-ttu-id="515e6-150">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="515e6-150">Wildcard characters are permitted.</span></span> <span data-ttu-id="515e6-151">Parametern **include** är endast effektiv när kommandot innehåller innehållet i ett objekt, t. ex `C:\Windows\*` ., där jokertecknet anger innehållet i `C:\Windows` katalogen.</span><span class="sxs-lookup"><span data-stu-id="515e6-151">The **Include** parameter is effective only when the command includes the contents of an item, such as `C:\Windows\*`, where the wildcard character specifies the contents of the `C:\Windows` directory.</span></span>

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

### <span data-ttu-id="515e6-152">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="515e6-152">-LiteralPath</span></span>

<span data-ttu-id="515e6-153">Anger en sökväg till en eller flera platser.</span><span class="sxs-lookup"><span data-stu-id="515e6-153">Specifies a path to one or more locations.</span></span> <span data-ttu-id="515e6-154">Värdet för **LiteralPath** används exakt som det har angetts.</span><span class="sxs-lookup"><span data-stu-id="515e6-154">The value of **LiteralPath** is used exactly as it is typed.</span></span> <span data-ttu-id="515e6-155">Inga tecken tolkas som jokertecken.</span><span class="sxs-lookup"><span data-stu-id="515e6-155">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="515e6-156">Om sökvägen innehåller escape-tecken omger du den med enkla citat tecken.</span><span class="sxs-lookup"><span data-stu-id="515e6-156">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="515e6-157">Enkla citat tecken säger att PowerShell inte tolkar några tecken som escape-sekvenser.</span><span class="sxs-lookup"><span data-stu-id="515e6-157">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

<span data-ttu-id="515e6-158">Mer information finns i [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md).</span><span class="sxs-lookup"><span data-stu-id="515e6-158">For more information, see [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md).</span></span>

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

### <span data-ttu-id="515e6-159">-Name</span><span class="sxs-lookup"><span data-stu-id="515e6-159">-Name</span></span>

<span data-ttu-id="515e6-160">Anger namnen på de egenskaper som ska tas bort.</span><span class="sxs-lookup"><span data-stu-id="515e6-160">Specifies the names of the properties to remove.</span></span>
<span data-ttu-id="515e6-161">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="515e6-161">Wildcard characters are permitted.</span></span>

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

### <span data-ttu-id="515e6-162">-Path</span><span class="sxs-lookup"><span data-stu-id="515e6-162">-Path</span></span>

<span data-ttu-id="515e6-163">Anger sökvägen till det objekt vars egenskaper tas bort.</span><span class="sxs-lookup"><span data-stu-id="515e6-163">Specifies the path of the item whose properties are being removed.</span></span>
<span data-ttu-id="515e6-164">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="515e6-164">Wildcard characters are permitted.</span></span>

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

### <span data-ttu-id="515e6-165">-Confirm</span><span class="sxs-lookup"><span data-stu-id="515e6-165">-Confirm</span></span>

<span data-ttu-id="515e6-166">Uppmanar dig att bekräfta innan du kör cmdleten.</span><span class="sxs-lookup"><span data-stu-id="515e6-166">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="515e6-167">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="515e6-167">-WhatIf</span></span>

<span data-ttu-id="515e6-168">Visar vad som skulle hända om cmdleten kördes.</span><span class="sxs-lookup"><span data-stu-id="515e6-168">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="515e6-169">Cmdleten körs inte.</span><span class="sxs-lookup"><span data-stu-id="515e6-169">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="515e6-170">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="515e6-170">CommonParameters</span></span>

<span data-ttu-id="515e6-171">Denna cmdlet stöder de gemensamma parametrarna:,,,,,,,, `-Debug` `-ErrorAction` `-ErrorVariable` `-InformationAction` `-InformationVariable` `-OutVariable` `-OutBuffer` `-PipelineVariable` `-Verbose` `-WarningAction` , och `-WarningVariable` .</span><span class="sxs-lookup"><span data-stu-id="515e6-171">This cmdlet supports the common parameters: `-Debug`, `-ErrorAction`, `-ErrorVariable`, `-InformationAction`, `-InformationVariable`, `-OutVariable`, `-OutBuffer`, `-PipelineVariable`, `-Verbose`, `-WarningAction`, and `-WarningVariable`.</span></span> <span data-ttu-id="515e6-172">Mer information finns i [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span><span class="sxs-lookup"><span data-stu-id="515e6-172">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="515e6-173">INDATA</span><span class="sxs-lookup"><span data-stu-id="515e6-173">INPUTS</span></span>

### <span data-ttu-id="515e6-174">System. String</span><span class="sxs-lookup"><span data-stu-id="515e6-174">System.String</span></span>

<span data-ttu-id="515e6-175">Du kan skicka vidare en sträng som innehåller en sökväg, men inte en literal sökväg, till denna cmdlet.</span><span class="sxs-lookup"><span data-stu-id="515e6-175">You can pipe a string that contains a path, but not a literal path, to this cmdlet.</span></span>

## <span data-ttu-id="515e6-176">UTDATA</span><span class="sxs-lookup"><span data-stu-id="515e6-176">OUTPUTS</span></span>

### <span data-ttu-id="515e6-177">Inget</span><span class="sxs-lookup"><span data-stu-id="515e6-177">None</span></span>

<span data-ttu-id="515e6-178">Denna cmdlet returnerar inga utdata.</span><span class="sxs-lookup"><span data-stu-id="515e6-178">This cmdlet does not return any output.</span></span>

## <span data-ttu-id="515e6-179">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="515e6-179">NOTES</span></span>

- <span data-ttu-id="515e6-180">I PowerShell-registerposten betraktas register värden som egenskaper för en register nyckel eller under nyckel.</span><span class="sxs-lookup"><span data-stu-id="515e6-180">In the PowerShell Registry provider, registry values are considered to be properties of a registry key or subkey.</span></span> <span data-ttu-id="515e6-181">Du kan använda **ItemProperty** -cmdletar för att hantera dessa värden.</span><span class="sxs-lookup"><span data-stu-id="515e6-181">You can use the **ItemProperty** cmdlets to manage these values.</span></span>
- <span data-ttu-id="515e6-182">`Remove-ItemProperty` är utformad för att fungera med data som exponeras av vilken provider som helst.</span><span class="sxs-lookup"><span data-stu-id="515e6-182">`Remove-ItemProperty` is designed to work with the data exposed by any provider.</span></span> <span data-ttu-id="515e6-183">Om du vill visa en lista över tillgängliga providers i din session skriver du `Get-PSProvider` .</span><span class="sxs-lookup"><span data-stu-id="515e6-183">To list the providers available in your session, type `Get-PSProvider`.</span></span> <span data-ttu-id="515e6-184">Mer information finns i [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span><span class="sxs-lookup"><span data-stu-id="515e6-184">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

## <span data-ttu-id="515e6-185">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="515e6-185">RELATED LINKS</span></span>

[<span data-ttu-id="515e6-186">Hämta objekt</span><span class="sxs-lookup"><span data-stu-id="515e6-186">Get-Item</span></span>](Get-Item.md)

[<span data-ttu-id="515e6-187">Clear-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="515e6-187">Clear-ItemProperty</span></span>](Clear-ItemProperty.md)

[<span data-ttu-id="515e6-188">Kopiera – ItemProperty</span><span class="sxs-lookup"><span data-stu-id="515e6-188">Copy-ItemProperty</span></span>](Copy-ItemProperty.md)

[<span data-ttu-id="515e6-189">Get-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="515e6-189">Get-ItemProperty</span></span>](Get-ItemProperty.md)

[<span data-ttu-id="515e6-190">Move-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="515e6-190">Move-ItemProperty</span></span>](Move-ItemProperty.md)

[<span data-ttu-id="515e6-191">New-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="515e6-191">New-ItemProperty</span></span>](New-ItemProperty.md)

[<span data-ttu-id="515e6-192">Ta bort objekt</span><span class="sxs-lookup"><span data-stu-id="515e6-192">Remove-Item</span></span>](Remove-Item.md)

[<span data-ttu-id="515e6-193">Byt namn – ItemProperty</span><span class="sxs-lookup"><span data-stu-id="515e6-193">Rename-ItemProperty</span></span>](Rename-ItemProperty.md)

[<span data-ttu-id="515e6-194">Set-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="515e6-194">Set-ItemProperty</span></span>](Set-ItemProperty.md)

[<span data-ttu-id="515e6-195">Ange plats</span><span class="sxs-lookup"><span data-stu-id="515e6-195">Set-Location</span></span>](Set-Location.md)

[<span data-ttu-id="515e6-196">about_Providers</span><span class="sxs-lookup"><span data-stu-id="515e6-196">about_Providers</span></span>](../Microsoft.PowerShell.Core/About/about_Providers.md)
