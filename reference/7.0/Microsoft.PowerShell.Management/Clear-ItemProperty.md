---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 5/14/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/clear-itemproperty?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Clear-ItemProperty
ms.openlocfilehash: f112b2bda543b50e0077df6778fc4eacfb3add9c
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/03/2020
ms.locfileid: "93262953"
---
# <span data-ttu-id="5afe1-103">Clear-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="5afe1-103">Clear-ItemProperty</span></span>

## <span data-ttu-id="5afe1-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="5afe1-104">SYNOPSIS</span></span>
<span data-ttu-id="5afe1-105">Rensar värdet för en egenskap men tar inte bort egenskapen.</span><span class="sxs-lookup"><span data-stu-id="5afe1-105">Clears the value of a property but does not delete the property.</span></span>

## <span data-ttu-id="5afe1-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="5afe1-106">SYNTAX</span></span>

### <span data-ttu-id="5afe1-107">Sökväg (standard)</span><span class="sxs-lookup"><span data-stu-id="5afe1-107">Path (Default)</span></span>

```
Clear-ItemProperty [-Path] <String[]> [-Name] <String> [-PassThru] [-Force] [-Filter <String>]
 [-Include <String[]>] [-Exclude <String[]>] [-Credential <PSCredential>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="5afe1-108">LiteralPath</span><span class="sxs-lookup"><span data-stu-id="5afe1-108">LiteralPath</span></span>

```
Clear-ItemProperty -LiteralPath <String[]> [-Name] <String> [-PassThru] [-Force] [-Filter <String>]
 [-Include <String[]>] [-Exclude <String[]>] [-Credential <PSCredential>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="5afe1-109">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="5afe1-109">DESCRIPTION</span></span>

<span data-ttu-id="5afe1-110">`Clear-ItemProperty`Cmdleten rensar värdet för en egenskap, men den tar inte bort egenskapen.</span><span class="sxs-lookup"><span data-stu-id="5afe1-110">The `Clear-ItemProperty` cmdlet clears the value of a property, but it does not delete the property.</span></span>
<span data-ttu-id="5afe1-111">Du kan använda den här cmdleten för att ta bort data från ett register värde.</span><span class="sxs-lookup"><span data-stu-id="5afe1-111">You can use this cmdlet to delete the data from a registry value.</span></span>

## <span data-ttu-id="5afe1-112">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="5afe1-112">EXAMPLES</span></span>

### <span data-ttu-id="5afe1-113">Exempel 1: Rensa värdet för register nyckeln</span><span class="sxs-lookup"><span data-stu-id="5afe1-113">Example 1: Clear the value of registry key</span></span>

<span data-ttu-id="5afe1-114">Det här kommandot rensar data i registervärdet "alternativ" i under nyckeln "mitt" i `HKEY_LOCAL_MACHINE\Software\MyCompany` .</span><span class="sxs-lookup"><span data-stu-id="5afe1-114">This command clears the data in the "Options" registry value in the "MyApp" subkey of `HKEY_LOCAL_MACHINE\Software\MyCompany`.</span></span>

```powershell
Clear-ItemProperty -Path "HKLM:\Software\MyCompany\MyApp" -Name "Options"
```

## <span data-ttu-id="5afe1-115">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="5afe1-115">PARAMETERS</span></span>

### <span data-ttu-id="5afe1-116">-Credential</span><span class="sxs-lookup"><span data-stu-id="5afe1-116">-Credential</span></span>

> [!NOTE]
> <span data-ttu-id="5afe1-117">Den här parametern stöds inte av några providrar som installeras med PowerShell.</span><span class="sxs-lookup"><span data-stu-id="5afe1-117">This parameter is not supported by any providers installed with PowerShell.</span></span>
> <span data-ttu-id="5afe1-118">Om du vill personifiera en annan användare eller öka dina autentiseringsuppgifter när du kör denna cmdlet, använder du [Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md).</span><span class="sxs-lookup"><span data-stu-id="5afe1-118">To impersonate another user, or elevate your credentials when running this cmdlet, use [Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md).</span></span>

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

### <span data-ttu-id="5afe1-119">-Undanta</span><span class="sxs-lookup"><span data-stu-id="5afe1-119">-Exclude</span></span>

<span data-ttu-id="5afe1-120">Anger, som en sträng mat ris, ett objekt eller objekt som denna cmdlet exkluderar i åtgärden.</span><span class="sxs-lookup"><span data-stu-id="5afe1-120">Specifies, as a string array, an item or items that this cmdlet excludes in the operation.</span></span> <span data-ttu-id="5afe1-121">Värdet för den här parametern kvalificerar parametern **Path** .</span><span class="sxs-lookup"><span data-stu-id="5afe1-121">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="5afe1-122">Ange ett Sök vägs element eller ett mönster, till exempel `*.txt` .</span><span class="sxs-lookup"><span data-stu-id="5afe1-122">Enter a path element or pattern, such as `*.txt`.</span></span> <span data-ttu-id="5afe1-123">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="5afe1-123">Wildcard characters are permitted.</span></span> <span data-ttu-id="5afe1-124">Parametern **exclude** är endast effektiv när kommandot innehåller innehållet i ett objekt, t. ex `C:\Windows\*` ., där jokertecknet anger innehållet i `C:\Windows` katalogen.</span><span class="sxs-lookup"><span data-stu-id="5afe1-124">The **Exclude** parameter is effective only when the command includes the contents of an item, such as `C:\Windows\*`, where the wildcard character specifies the contents of the `C:\Windows` directory.</span></span>

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

### <span data-ttu-id="5afe1-125">-Filter</span><span class="sxs-lookup"><span data-stu-id="5afe1-125">-Filter</span></span>

<span data-ttu-id="5afe1-126">Anger ett filter för att kvalificera **Sök vägs** parametern.</span><span class="sxs-lookup"><span data-stu-id="5afe1-126">Specifies a filter to qualify the **Path** parameter.</span></span> <span data-ttu-id="5afe1-127">[Fil Systems](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md) leverantören är den enda installerade PowerShell-providern som stöder användningen av filter.</span><span class="sxs-lookup"><span data-stu-id="5afe1-127">The [FileSystem](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md) provider is the only installed PowerShell provider that supports the use of filters.</span></span> <span data-ttu-id="5afe1-128">Du kan hitta syntaxen för filter språket för **fil systemet** i [about_Wildcards](../Microsoft.PowerShell.Core/About/about_Wildcards.md).</span><span class="sxs-lookup"><span data-stu-id="5afe1-128">You can find the syntax for the **FileSystem** filter language in [about_Wildcards](../Microsoft.PowerShell.Core/About/about_Wildcards.md).</span></span>
<span data-ttu-id="5afe1-129">Filter är mer effektiva än andra parametrar, eftersom providern tillämpar dem när cmdleten hämtar objekten i stället för att ha PowerShell filtrera objekten när de har hämtats.</span><span class="sxs-lookup"><span data-stu-id="5afe1-129">Filters are more efficient than other parameters, because the provider applies them when the cmdlet gets the objects rather than having PowerShell filter the objects after they are retrieved.</span></span>

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

### <span data-ttu-id="5afe1-130">-Force</span><span class="sxs-lookup"><span data-stu-id="5afe1-130">-Force</span></span>

<span data-ttu-id="5afe1-131">Anger att den här cmdleten tar bort egenskaper från objekt som annars inte kan kommas åt av användaren.</span><span class="sxs-lookup"><span data-stu-id="5afe1-131">Indicates that this cmdlet deletes properties from items that cannot otherwise be accessed by the user.</span></span> <span data-ttu-id="5afe1-132">Implementeringen varierar från providern till providern.</span><span class="sxs-lookup"><span data-stu-id="5afe1-132">Implementation varies from provider to provider.</span></span>
<span data-ttu-id="5afe1-133">Mer information finns i [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span><span class="sxs-lookup"><span data-stu-id="5afe1-133">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

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

### <span data-ttu-id="5afe1-134">-Inkludera</span><span class="sxs-lookup"><span data-stu-id="5afe1-134">-Include</span></span>

<span data-ttu-id="5afe1-135">Anger, som en sträng mat ris, ett objekt eller objekt som denna cmdlet inkluderar i åtgärden.</span><span class="sxs-lookup"><span data-stu-id="5afe1-135">Specifies, as a string array, an item or items that this cmdlet includes in the operation.</span></span> <span data-ttu-id="5afe1-136">Värdet för den här parametern kvalificerar parametern **Path** .</span><span class="sxs-lookup"><span data-stu-id="5afe1-136">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="5afe1-137">Ange ett Sök vägs element eller ett mönster, till exempel `"*.txt"` .</span><span class="sxs-lookup"><span data-stu-id="5afe1-137">Enter a path element or pattern, such as `"*.txt"`.</span></span> <span data-ttu-id="5afe1-138">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="5afe1-138">Wildcard characters are permitted.</span></span> <span data-ttu-id="5afe1-139">Parametern **include** är endast effektiv när kommandot innehåller innehållet i ett objekt, t. ex `C:\Windows\*` ., där jokertecknet anger innehållet i `C:\Windows` katalogen.</span><span class="sxs-lookup"><span data-stu-id="5afe1-139">The **Include** parameter is effective only when the command includes the contents of an item, such as `C:\Windows\*`, where the wildcard character specifies the contents of the `C:\Windows` directory.</span></span>

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

### <span data-ttu-id="5afe1-140">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="5afe1-140">-LiteralPath</span></span>

<span data-ttu-id="5afe1-141">Anger en sökväg till en eller flera platser.</span><span class="sxs-lookup"><span data-stu-id="5afe1-141">Specifies a path to one or more locations.</span></span> <span data-ttu-id="5afe1-142">Värdet för **LiteralPath** används exakt som det har angetts.</span><span class="sxs-lookup"><span data-stu-id="5afe1-142">The value of **LiteralPath** is used exactly as it is typed.</span></span> <span data-ttu-id="5afe1-143">Inga tecken tolkas som jokertecken.</span><span class="sxs-lookup"><span data-stu-id="5afe1-143">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="5afe1-144">Om sökvägen innehåller escape-tecken omger du den med enkla citat tecken.</span><span class="sxs-lookup"><span data-stu-id="5afe1-144">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="5afe1-145">Enkla citat tecken säger att PowerShell inte tolkar några tecken som escape-sekvenser.</span><span class="sxs-lookup"><span data-stu-id="5afe1-145">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

<span data-ttu-id="5afe1-146">Mer information finns i [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md).</span><span class="sxs-lookup"><span data-stu-id="5afe1-146">For more information, see [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md).</span></span>

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

### <span data-ttu-id="5afe1-147">-Name</span><span class="sxs-lookup"><span data-stu-id="5afe1-147">-Name</span></span>

<span data-ttu-id="5afe1-148">Anger namnet på den egenskap som ska rensas, till exempel namnet på ett register värde.</span><span class="sxs-lookup"><span data-stu-id="5afe1-148">Specifies the name of the property to be cleared, such as the name of a registry value.</span></span>
<span data-ttu-id="5afe1-149">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="5afe1-149">Wildcard characters are permitted.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### <span data-ttu-id="5afe1-150">– PassThru</span><span class="sxs-lookup"><span data-stu-id="5afe1-150">-PassThru</span></span>

<span data-ttu-id="5afe1-151">Returnerar ett objekt som representerar det objekt som du arbetar med.</span><span class="sxs-lookup"><span data-stu-id="5afe1-151">Returns an object representing the item with which you are working.</span></span>
<span data-ttu-id="5afe1-152">Som standard genererar denna cmdlet inga utdata.</span><span class="sxs-lookup"><span data-stu-id="5afe1-152">By default, this cmdlet does not generate any output.</span></span>

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

### <span data-ttu-id="5afe1-153">-Path</span><span class="sxs-lookup"><span data-stu-id="5afe1-153">-Path</span></span>

<span data-ttu-id="5afe1-154">Anger sökvägen till den egenskap som rensas.</span><span class="sxs-lookup"><span data-stu-id="5afe1-154">Specifies the path to the property being cleared.</span></span>
<span data-ttu-id="5afe1-155">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="5afe1-155">Wildcard characters are permitted.</span></span>

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

### <span data-ttu-id="5afe1-156">-Confirm</span><span class="sxs-lookup"><span data-stu-id="5afe1-156">-Confirm</span></span>

<span data-ttu-id="5afe1-157">Uppmanar dig att bekräfta innan du kör cmdleten.</span><span class="sxs-lookup"><span data-stu-id="5afe1-157">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="5afe1-158">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="5afe1-158">-WhatIf</span></span>

<span data-ttu-id="5afe1-159">Visar vad som skulle hända om cmdleten kördes.</span><span class="sxs-lookup"><span data-stu-id="5afe1-159">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="5afe1-160">Cmdleten körs inte.</span><span class="sxs-lookup"><span data-stu-id="5afe1-160">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="5afe1-161">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="5afe1-161">CommonParameters</span></span>

<span data-ttu-id="5afe1-162">Denna cmdlet stöder de gemensamma parametrarna:,,,,,,,, `-Debug` `-ErrorAction` `-ErrorVariable` `-InformationAction` `-InformationVariable` `-OutVariable` `-OutBuffer` `-PipelineVariable` `-Verbose` `-WarningAction` , och `-WarningVariable` .</span><span class="sxs-lookup"><span data-stu-id="5afe1-162">This cmdlet supports the common parameters: `-Debug`, `-ErrorAction`, `-ErrorVariable`, `-InformationAction`, `-InformationVariable`, `-OutVariable`, `-OutBuffer`, `-PipelineVariable`, `-Verbose`, `-WarningAction`, and `-WarningVariable`.</span></span> <span data-ttu-id="5afe1-163">Mer information finns i [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span><span class="sxs-lookup"><span data-stu-id="5afe1-163">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="5afe1-164">INDATA</span><span class="sxs-lookup"><span data-stu-id="5afe1-164">INPUTS</span></span>

### <span data-ttu-id="5afe1-165">System. String</span><span class="sxs-lookup"><span data-stu-id="5afe1-165">System.String</span></span>

<span data-ttu-id="5afe1-166">Du kan skicka en Sök vägs sträng till denna cmdlet.</span><span class="sxs-lookup"><span data-stu-id="5afe1-166">You can pipe a path string to this cmdlet.</span></span>

## <span data-ttu-id="5afe1-167">UTDATA</span><span class="sxs-lookup"><span data-stu-id="5afe1-167">OUTPUTS</span></span>

### <span data-ttu-id="5afe1-168">Ingen eller system. Management. Automation. PSCustomObject</span><span class="sxs-lookup"><span data-stu-id="5afe1-168">None or System.Management.Automation.PSCustomObject</span></span>

<span data-ttu-id="5afe1-169">När du använder parametern **Passthru** `Clear-ItemProperty` genererar ett **PSCustomObject** -objekt som representerar egenskapen rensat objekt.</span><span class="sxs-lookup"><span data-stu-id="5afe1-169">When you use the **PassThru** parameter, `Clear-ItemProperty` generates a **PSCustomObject** object that represents the cleared item property.</span></span> <span data-ttu-id="5afe1-170">Annars genererar denna cmdlet inga utdata.</span><span class="sxs-lookup"><span data-stu-id="5afe1-170">Otherwise, this cmdlet does not generate any output.</span></span>

## <span data-ttu-id="5afe1-171">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="5afe1-171">NOTES</span></span>

- <span data-ttu-id="5afe1-172">Du kan använda `Clear-ItemProperty` för att ta bort data i register värden utan att ta bort värdet.</span><span class="sxs-lookup"><span data-stu-id="5afe1-172">You can use `Clear-ItemProperty` to delete the data in registry values without deleting the value.</span></span>
  <span data-ttu-id="5afe1-173">Om värdets datatyp är Binary eller DWORD, ställer du in värdet på noll om du rensar data.</span><span class="sxs-lookup"><span data-stu-id="5afe1-173">If the data type of the value is Binary or DWORD, clearing the data sets the value to zero.</span></span>
  <span data-ttu-id="5afe1-174">Annars är värdet tomt.</span><span class="sxs-lookup"><span data-stu-id="5afe1-174">Otherwise, the value is empty.</span></span>
- <span data-ttu-id="5afe1-175">`Clear-ItemProperty`Cmdleten är utformad för att fungera med data som exponeras av vilken provider som helst.</span><span class="sxs-lookup"><span data-stu-id="5afe1-175">The `Clear-ItemProperty` cmdlet is designed to work with the data exposed by any provider.</span></span> <span data-ttu-id="5afe1-176">Om du vill visa en lista över tillgängliga providers i din session skriver du `Get-PSProvider` .</span><span class="sxs-lookup"><span data-stu-id="5afe1-176">To list the providers available in your session, type `Get-PSProvider`.</span></span> <span data-ttu-id="5afe1-177">Mer information finns i [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span><span class="sxs-lookup"><span data-stu-id="5afe1-177">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

## <span data-ttu-id="5afe1-178">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="5afe1-178">RELATED LINKS</span></span>

[<span data-ttu-id="5afe1-179">Kopiera – ItemProperty</span><span class="sxs-lookup"><span data-stu-id="5afe1-179">Copy-ItemProperty</span></span>](Copy-ItemProperty.md)

[<span data-ttu-id="5afe1-180">Get-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="5afe1-180">Get-ItemProperty</span></span>](Get-ItemProperty.md)

[<span data-ttu-id="5afe1-181">Move-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="5afe1-181">Move-ItemProperty</span></span>](Move-ItemProperty.md)

[<span data-ttu-id="5afe1-182">New-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="5afe1-182">New-ItemProperty</span></span>](New-ItemProperty.md)

[<span data-ttu-id="5afe1-183">Byt namn – ItemProperty</span><span class="sxs-lookup"><span data-stu-id="5afe1-183">Rename-ItemProperty</span></span>](Rename-ItemProperty.md)

[<span data-ttu-id="5afe1-184">about_Providers</span><span class="sxs-lookup"><span data-stu-id="5afe1-184">about_Providers</span></span>](../Microsoft.PowerShell.Core/About/about_Providers.md)
