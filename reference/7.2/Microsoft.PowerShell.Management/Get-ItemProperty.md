---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 05/14/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/get-itemproperty?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-ItemProperty
ms.openlocfilehash: 20116c12f09d6a9a36f33b656a36e30c2096db70
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94710824"
---
# <span data-ttu-id="4135d-102">Get-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="4135d-102">Get-ItemProperty</span></span>

## <span data-ttu-id="4135d-103">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="4135d-103">SYNOPSIS</span></span>
<span data-ttu-id="4135d-104">Hämtar egenskaperna för ett angivet objekt.</span><span class="sxs-lookup"><span data-stu-id="4135d-104">Gets the properties of a specified item.</span></span>

## <span data-ttu-id="4135d-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="4135d-105">SYNTAX</span></span>

### <span data-ttu-id="4135d-106">Sökväg (standard)</span><span class="sxs-lookup"><span data-stu-id="4135d-106">Path (Default)</span></span>

```
Get-ItemProperty [-Path] <String[]> [[-Name] <String[]>] [-Filter <String>] [-Include <String[]>]
 [-Exclude <String[]>] [-Credential <PSCredential>] [<CommonParameters>]
```

### <span data-ttu-id="4135d-107">LiteralPath</span><span class="sxs-lookup"><span data-stu-id="4135d-107">LiteralPath</span></span>

```
Get-ItemProperty -LiteralPath <String[]> [[-Name] <String[]>] [-Filter <String>] [-Include <String[]>]
 [-Exclude <String[]>] [-Credential <PSCredential>] [<CommonParameters>]
```

## <span data-ttu-id="4135d-108">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="4135d-108">DESCRIPTION</span></span>

<span data-ttu-id="4135d-109">`Get-ItemProperty`Cmdlet: en hämtar egenskaperna för de angivna objekten.</span><span class="sxs-lookup"><span data-stu-id="4135d-109">The `Get-ItemProperty` cmdlet gets the properties of the specified items.</span></span>
<span data-ttu-id="4135d-110">Du kan till exempel använda denna cmdlet för att hämta värdet för egenskapen LastAccessTime för ett fil objekt.</span><span class="sxs-lookup"><span data-stu-id="4135d-110">For example, you can use this cmdlet to get the value of the LastAccessTime property of a file object.</span></span> <span data-ttu-id="4135d-111">Du kan också använda denna cmdlet för att Visa register poster och deras värden.</span><span class="sxs-lookup"><span data-stu-id="4135d-111">You can also use this cmdlet to view registry entries and their values.</span></span>

## <span data-ttu-id="4135d-112">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="4135d-112">EXAMPLES</span></span>

### <span data-ttu-id="4135d-113">Exempel 1: Hämta information om en angiven katalog</span><span class="sxs-lookup"><span data-stu-id="4135d-113">Example 1: Get information about a specific directory</span></span>

<span data-ttu-id="4135d-114">Det här kommandot hämtar information om `C:\Windows` katalogen.</span><span class="sxs-lookup"><span data-stu-id="4135d-114">This command gets information about the `C:\Windows` directory.</span></span>

```powershell
Get-ItemProperty C:\Windows
```

### <span data-ttu-id="4135d-115">Exempel 2: Hämta egenskaperna för en enskild fil</span><span class="sxs-lookup"><span data-stu-id="4135d-115">Example 2: Get the properties of a specific file</span></span>

<span data-ttu-id="4135d-116">Det här kommandot hämtar `C:\Test\Weather.xls` filens egenskaper.</span><span class="sxs-lookup"><span data-stu-id="4135d-116">This command gets the properties of the `C:\Test\Weather.xls` file.</span></span>
<span data-ttu-id="4135d-117">Resultatet är skickas till `Format-List` cmdleten för att visa utdata som en lista.</span><span class="sxs-lookup"><span data-stu-id="4135d-117">The result is piped to the `Format-List` cmdlet to display the output as a list.</span></span>

```powershell
Get-ItemProperty C:\Test\Weather.xls | Format-List
```

### <span data-ttu-id="4135d-118">Exempel 3: Visa värde namnet och data för register poster i en register under nyckel</span><span class="sxs-lookup"><span data-stu-id="4135d-118">Example 3: Display the value name and data of registry entries in a registry subkey</span></span>

<span data-ttu-id="4135d-119">Det här kommandot visar värde namnet och data för alla register poster som finns i register under nyckeln "CurrentVersion".</span><span class="sxs-lookup"><span data-stu-id="4135d-119">This command displays the value name and data of each of the registry entries contained in the "CurrentVersion" registry subkey.</span></span>

```powershell
Get-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion
```

> [!NOTE]
> <span data-ttu-id="4135d-120">Det här kommandot kräver att det finns en PowerShell-enhet med namnet `HKLM:` som är mappad till registrerings data filen "HKEY_LOCAL_MACHINE" i registret.</span><span class="sxs-lookup"><span data-stu-id="4135d-120">This command requires that there is a PowerShell drive named `HKLM:` that is mapped to the "HKEY_LOCAL_MACHINE" hive of the registry.</span></span>
>
> <span data-ttu-id="4135d-121">En enhet med det namnet och mappningen är tillgänglig i PowerShell som standard.</span><span class="sxs-lookup"><span data-stu-id="4135d-121">A drive with that name and mapping is available in PowerShell by default.</span></span>
> <span data-ttu-id="4135d-122">Du kan också ange sökvägen till den här register under nyckeln med hjälp av följande alternativa sökväg som börjar med Providerns namn följt av två kolon:</span><span class="sxs-lookup"><span data-stu-id="4135d-122">Alternatively, the path to this registry subkey can be specified by using the following alternative path that begins with the provider name followed by two colons:</span></span>
>
> <span data-ttu-id="4135d-123">`Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion`.</span><span class="sxs-lookup"><span data-stu-id="4135d-123">`Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion`.</span></span>

### <span data-ttu-id="4135d-124">Exempel 4: Hämta värde namn och data för en register post i en register under nyckel</span><span class="sxs-lookup"><span data-stu-id="4135d-124">Example 4: Get the value name and data of a registry entry in a registry subkey</span></span>

<span data-ttu-id="4135d-125">Det här kommandot hämtar värde namnet och data för register posten "ProgramFilesDir" i register under nyckeln "CurrentVersion".</span><span class="sxs-lookup"><span data-stu-id="4135d-125">This command gets the value name and data of the "ProgramFilesDir" registry entry in the "CurrentVersion" registry subkey.</span></span>
<span data-ttu-id="4135d-126">**Sökvägen** anger under nyckeln och parametern **Name** anger värde namnet för posten.</span><span class="sxs-lookup"><span data-stu-id="4135d-126">The **Path** specifies the subkey and the **Name** parameter specifies the value name of the entry.</span></span>

```powershell
Get-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name "ProgramFilesDir"
```

### <span data-ttu-id="4135d-127">Exempel 5: Hämta värde namn och data för register poster i en register nyckel</span><span class="sxs-lookup"><span data-stu-id="4135d-127">Example 5: Get the value names and data of registry entries in a registry key</span></span>

<span data-ttu-id="4135d-128">Det här kommandot hämtar värde namn och data för register posterna i register nyckeln "PowerShellEngine".</span><span class="sxs-lookup"><span data-stu-id="4135d-128">This command gets the value names and data of the registry entries in the "PowerShellEngine" registry key.</span></span> <span data-ttu-id="4135d-129">Resultatet visas i följande exempel på utdata.</span><span class="sxs-lookup"><span data-stu-id="4135d-129">The results are shown in the following sample output.</span></span>

```powershell
Get-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\PowerShell\1\PowerShellEngine
```

```output
ApplicationBase         : C:\Windows\system32\WindowsPowerShell\v1.0\
ConsoleHostAssemblyName : Microsoft.PowerShell.ConsoleHost, Version=1.0.0.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35, ProcessorArchitecture=msil
PowerShellVersion       : 2.0
RuntimeVersion          : v2.0.50727
CTPVersion              : 5
PSCompatibleVersion     : 1.0,2.0
```

## <span data-ttu-id="4135d-130">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="4135d-130">PARAMETERS</span></span>

### <span data-ttu-id="4135d-131">-Credential</span><span class="sxs-lookup"><span data-stu-id="4135d-131">-Credential</span></span>

> [!NOTE]
> <span data-ttu-id="4135d-132">Den här parametern stöds inte av några providrar som installeras med PowerShell.</span><span class="sxs-lookup"><span data-stu-id="4135d-132">This parameter is not supported by any providers installed with PowerShell.</span></span>
> <span data-ttu-id="4135d-133">Om du vill personifiera en annan användare eller öka dina autentiseringsuppgifter när du kör denna cmdlet, använder du [Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md).</span><span class="sxs-lookup"><span data-stu-id="4135d-133">To impersonate another user, or elevate your credentials when running this cmdlet, use [Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md).</span></span>

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

### <span data-ttu-id="4135d-134">-Undanta</span><span class="sxs-lookup"><span data-stu-id="4135d-134">-Exclude</span></span>

<span data-ttu-id="4135d-135">Anger, som en sträng mat ris, ett objekt eller objekt som denna cmdlet exkluderar i åtgärden.</span><span class="sxs-lookup"><span data-stu-id="4135d-135">Specifies, as a string array, an item or items that this cmdlet excludes in the operation.</span></span> <span data-ttu-id="4135d-136">Värdet för den här parametern kvalificerar parametern **Path** .</span><span class="sxs-lookup"><span data-stu-id="4135d-136">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="4135d-137">Ange ett Sök vägs element eller ett mönster, till exempel `*.txt` .</span><span class="sxs-lookup"><span data-stu-id="4135d-137">Enter a path element or pattern, such as `*.txt`.</span></span> <span data-ttu-id="4135d-138">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="4135d-138">Wildcard characters are permitted.</span></span> <span data-ttu-id="4135d-139">Parametern **exclude** är endast effektiv när kommandot innehåller innehållet i ett objekt, t. ex `C:\Windows\*` ., där jokertecknet anger innehållet i `C:\Windows` katalogen.</span><span class="sxs-lookup"><span data-stu-id="4135d-139">The **Exclude** parameter is effective only when the command includes the contents of an item, such as `C:\Windows\*`, where the wildcard character specifies the contents of the `C:\Windows` directory.</span></span>

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

### <span data-ttu-id="4135d-140">-Filter</span><span class="sxs-lookup"><span data-stu-id="4135d-140">-Filter</span></span>

<span data-ttu-id="4135d-141">Anger ett filter för att kvalificera **Sök vägs** parametern.</span><span class="sxs-lookup"><span data-stu-id="4135d-141">Specifies a filter to qualify the **Path** parameter.</span></span> <span data-ttu-id="4135d-142">[Fil Systems](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md) leverantören är den enda installerade PowerShell-providern som stöder användningen av filter.</span><span class="sxs-lookup"><span data-stu-id="4135d-142">The [FileSystem](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md) provider is the only installed PowerShell provider that supports the use of filters.</span></span> <span data-ttu-id="4135d-143">Du kan hitta syntaxen för filter språket för **fil systemet** i [about_Wildcards](../Microsoft.PowerShell.Core/About/about_Wildcards.md).</span><span class="sxs-lookup"><span data-stu-id="4135d-143">You can find the syntax for the **FileSystem** filter language in [about_Wildcards](../Microsoft.PowerShell.Core/About/about_Wildcards.md).</span></span>
<span data-ttu-id="4135d-144">Filter är mer effektiva än andra parametrar, eftersom providern tillämpar dem när cmdleten hämtar objekten i stället för att ha PowerShell filtrera objekten när de har hämtats.</span><span class="sxs-lookup"><span data-stu-id="4135d-144">Filters are more efficient than other parameters, because the provider applies them when the cmdlet gets the objects rather than having PowerShell filter the objects after they are retrieved.</span></span>

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

### <span data-ttu-id="4135d-145">-Inkludera</span><span class="sxs-lookup"><span data-stu-id="4135d-145">-Include</span></span>

<span data-ttu-id="4135d-146">Anger, som en sträng mat ris, ett objekt eller objekt som denna cmdlet inkluderar i åtgärden.</span><span class="sxs-lookup"><span data-stu-id="4135d-146">Specifies, as a string array, an item or items that this cmdlet includes in the operation.</span></span> <span data-ttu-id="4135d-147">Värdet för den här parametern kvalificerar parametern **Path** .</span><span class="sxs-lookup"><span data-stu-id="4135d-147">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="4135d-148">Ange ett Sök vägs element eller ett mönster, till exempel `"*.txt"` .</span><span class="sxs-lookup"><span data-stu-id="4135d-148">Enter a path element or pattern, such as `"*.txt"`.</span></span> <span data-ttu-id="4135d-149">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="4135d-149">Wildcard characters are permitted.</span></span> <span data-ttu-id="4135d-150">Parametern **include** är endast effektiv när kommandot innehåller innehållet i ett objekt, t. ex `C:\Windows\*` ., där jokertecknet anger innehållet i `C:\Windows` katalogen.</span><span class="sxs-lookup"><span data-stu-id="4135d-150">The **Include** parameter is effective only when the command includes the contents of an item, such as `C:\Windows\*`, where the wildcard character specifies the contents of the `C:\Windows` directory.</span></span>

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

### <span data-ttu-id="4135d-151">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="4135d-151">-LiteralPath</span></span>

<span data-ttu-id="4135d-152">Anger en sökväg till en eller flera platser.</span><span class="sxs-lookup"><span data-stu-id="4135d-152">Specifies a path to one or more locations.</span></span> <span data-ttu-id="4135d-153">Värdet för **LiteralPath** används exakt som det har angetts.</span><span class="sxs-lookup"><span data-stu-id="4135d-153">The value of **LiteralPath** is used exactly as it is typed.</span></span> <span data-ttu-id="4135d-154">Inga tecken tolkas som jokertecken.</span><span class="sxs-lookup"><span data-stu-id="4135d-154">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="4135d-155">Om sökvägen innehåller escape-tecken omger du den med enkla citat tecken.</span><span class="sxs-lookup"><span data-stu-id="4135d-155">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="4135d-156">Enkla citat tecken säger att PowerShell inte tolkar några tecken som escape-sekvenser.</span><span class="sxs-lookup"><span data-stu-id="4135d-156">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

<span data-ttu-id="4135d-157">Mer information finns i [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md).</span><span class="sxs-lookup"><span data-stu-id="4135d-157">For more information, see [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md).</span></span>

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

### <span data-ttu-id="4135d-158">-Name</span><span class="sxs-lookup"><span data-stu-id="4135d-158">-Name</span></span>

<span data-ttu-id="4135d-159">Anger namnet på egenskapen eller egenskaperna som ska hämtas.</span><span class="sxs-lookup"><span data-stu-id="4135d-159">Specifies the name of the property or properties to retrieve.</span></span>
<span data-ttu-id="4135d-160">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="4135d-160">Wildcard characters are permitted.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: PSProperty

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="4135d-161">-Path</span><span class="sxs-lookup"><span data-stu-id="4135d-161">-Path</span></span>

<span data-ttu-id="4135d-162">Anger sökvägen till objektet eller objekten.</span><span class="sxs-lookup"><span data-stu-id="4135d-162">Specifies the path to the item or items.</span></span>
<span data-ttu-id="4135d-163">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="4135d-163">Wildcard characters are permitted.</span></span>

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

### <span data-ttu-id="4135d-164">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="4135d-164">CommonParameters</span></span>

<span data-ttu-id="4135d-165">Denna cmdlet stöder de gemensamma parametrarna:,,,,,,,, `-Debug` `-ErrorAction` `-ErrorVariable` `-InformationAction` `-InformationVariable` `-OutVariable` `-OutBuffer` `-PipelineVariable` `-Verbose` `-WarningAction` , och `-WarningVariable` .</span><span class="sxs-lookup"><span data-stu-id="4135d-165">This cmdlet supports the common parameters: `-Debug`, `-ErrorAction`, `-ErrorVariable`, `-InformationAction`, `-InformationVariable`, `-OutVariable`, `-OutBuffer`, `-PipelineVariable`, `-Verbose`, `-WarningAction`, and `-WarningVariable`.</span></span> <span data-ttu-id="4135d-166">Mer information finns i [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span><span class="sxs-lookup"><span data-stu-id="4135d-166">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="4135d-167">INDATA</span><span class="sxs-lookup"><span data-stu-id="4135d-167">INPUTS</span></span>

### <span data-ttu-id="4135d-168">System. String</span><span class="sxs-lookup"><span data-stu-id="4135d-168">System.String</span></span>

<span data-ttu-id="4135d-169">Du kan skicka vidare en sträng som innehåller en sökväg till `Get-ItemProperty` .</span><span class="sxs-lookup"><span data-stu-id="4135d-169">You can pipe a string that contains a path to `Get-ItemProperty`.</span></span>

## <span data-ttu-id="4135d-170">UTDATA</span><span class="sxs-lookup"><span data-stu-id="4135d-170">OUTPUTS</span></span>

### <span data-ttu-id="4135d-171">System. Boolean, system. String, system. DateTime</span><span class="sxs-lookup"><span data-stu-id="4135d-171">System.Boolean, System.String, System.DateTime</span></span>

<span data-ttu-id="4135d-172">`Get-ItemProperty` Returnerar ett objekt för varje objekt egenskap som det får.</span><span class="sxs-lookup"><span data-stu-id="4135d-172">`Get-ItemProperty` returns an object for each item property that it gets.</span></span> <span data-ttu-id="4135d-173">Objekt typen beror på vilket objekt som hämtas.</span><span class="sxs-lookup"><span data-stu-id="4135d-173">The object type depends on the object that is retrieved.</span></span> <span data-ttu-id="4135d-174">I en fil system enhet kan det exempelvis returnera en fil eller mapp.</span><span class="sxs-lookup"><span data-stu-id="4135d-174">For example, in a file system drive, it might return a file or folder.</span></span>

## <span data-ttu-id="4135d-175">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="4135d-175">NOTES</span></span>

<span data-ttu-id="4135d-176">`Get-ItemProperty`Cmdleten är utformad för att fungera med data som exponeras av vilken provider som helst.</span><span class="sxs-lookup"><span data-stu-id="4135d-176">The `Get-ItemProperty` cmdlet is designed to work with the data exposed by any provider.</span></span> <span data-ttu-id="4135d-177">Om du vill visa en lista över tillgängliga providers i din session skriver du `Get-PSProvider` .</span><span class="sxs-lookup"><span data-stu-id="4135d-177">To list the providers available in your session, type `Get-PSProvider`.</span></span> <span data-ttu-id="4135d-178">Mer information finns i [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span><span class="sxs-lookup"><span data-stu-id="4135d-178">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

## <span data-ttu-id="4135d-179">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="4135d-179">RELATED LINKS</span></span>

[<span data-ttu-id="4135d-180">Clear-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="4135d-180">Clear-ItemProperty</span></span>](Clear-ItemProperty.md)

[<span data-ttu-id="4135d-181">Kopiera – ItemProperty</span><span class="sxs-lookup"><span data-stu-id="4135d-181">Copy-ItemProperty</span></span>](Copy-ItemProperty.md)

[<span data-ttu-id="4135d-182">Move-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="4135d-182">Move-ItemProperty</span></span>](Move-ItemProperty.md)

[<span data-ttu-id="4135d-183">New-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="4135d-183">New-ItemProperty</span></span>](New-ItemProperty.md)

[<span data-ttu-id="4135d-184">Remove-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="4135d-184">Remove-ItemProperty</span></span>](Remove-ItemProperty.md)

[<span data-ttu-id="4135d-185">Byt namn – ItemProperty</span><span class="sxs-lookup"><span data-stu-id="4135d-185">Rename-ItemProperty</span></span>](Rename-ItemProperty.md)

[<span data-ttu-id="4135d-186">Set-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="4135d-186">Set-ItemProperty</span></span>](Set-ItemProperty.md)

[<span data-ttu-id="4135d-187">about_Providers</span><span class="sxs-lookup"><span data-stu-id="4135d-187">about_Providers</span></span>](../Microsoft.PowerShell.Core/About/about_Providers.md)

