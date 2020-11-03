---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/join-path?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Join-Path
ms.openlocfilehash: 7752688a04057861fffdbc7b30c293239acb132e
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93264471"
---
# <span data-ttu-id="b8697-103">Join-Path</span><span class="sxs-lookup"><span data-stu-id="b8697-103">Join-Path</span></span>

## <span data-ttu-id="b8697-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="b8697-104">SYNOPSIS</span></span>
<span data-ttu-id="b8697-105">Kombinerar en sökväg och en underordnad sökväg till en enda sökväg.</span><span class="sxs-lookup"><span data-stu-id="b8697-105">Combines a path and a child path into a single path.</span></span>

## <span data-ttu-id="b8697-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="b8697-106">SYNTAX</span></span>

```
Join-Path [-Path] <String[]> [-ChildPath] <String> [[-AdditionalChildPath] <String[]>] [-Resolve]
 [-Credential <PSCredential>] [<CommonParameters>]
```

## <span data-ttu-id="b8697-107">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="b8697-107">DESCRIPTION</span></span>

<span data-ttu-id="b8697-108">`Join-Path`Cmdleten kombinerar en sökväg och en underordnad sökväg till en enda sökväg.</span><span class="sxs-lookup"><span data-stu-id="b8697-108">The `Join-Path` cmdlet combines a path and child-path into a single path.</span></span>
<span data-ttu-id="b8697-109">Providern tillhandahåller Sök vägs avgränsare.</span><span class="sxs-lookup"><span data-stu-id="b8697-109">The provider supplies the path delimiters.</span></span>

## <span data-ttu-id="b8697-110">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="b8697-110">EXAMPLES</span></span>

### <span data-ttu-id="b8697-111">Exempel 1: kombinera en sökväg med en underordnad sökväg</span><span class="sxs-lookup"><span data-stu-id="b8697-111">Example 1: Combine a path with a child path</span></span>

```powershell
PS C:\> Join-Path -Path "path" -ChildPath "childpath"
```

```output
path\childpath
```

<span data-ttu-id="b8697-112">Det här kommandot använder `Join-Path` för att kombinera en sökväg med en childpath.</span><span class="sxs-lookup"><span data-stu-id="b8697-112">This command uses `Join-Path` to combine a path with a childpath.</span></span>

<span data-ttu-id="b8697-113">Eftersom kommandot körs från `FileSystem` providern, är det den `\` avgränsare som ska användas för att ansluta Sök vägarna.</span><span class="sxs-lookup"><span data-stu-id="b8697-113">Since the command is executed from the `FileSystem` provider, it provides the `\` delimiter to join the paths.</span></span>

### <span data-ttu-id="b8697-114">Exempel 2: kombinera sökvägar som redan innehåller katalog avgränsare</span><span class="sxs-lookup"><span data-stu-id="b8697-114">Example 2: Combine paths that already contain directory separators</span></span>

```powershell
PS C:\> Join-Path -Path "path\" -ChildPath "\childpath"
```

```output
path\childpath
```

<span data-ttu-id="b8697-115">Befintliga katalog avgränsare `\` och hanterade så det finns bara en avgränsare mellan `Path` och `ChildPath`</span><span class="sxs-lookup"><span data-stu-id="b8697-115">Existing directory separators `\` and handled so there is only one separator between `Path` and `ChildPath`</span></span>

### <span data-ttu-id="b8697-116">Exempel 3: Visa filer och mappar genom att koppla en sökväg med en underordnad sökväg</span><span class="sxs-lookup"><span data-stu-id="b8697-116">Example 3: Display files and folders by joining a path with a child path</span></span>

```powershell
Join-Path "C:\win*" "System*" -Resolve
```

<span data-ttu-id="b8697-117">Det här kommandot visar de filer och mappar som refereras till genom att ansluta till C:\Win- \* sökvägen och den \* underordnade system Sök vägen.</span><span class="sxs-lookup"><span data-stu-id="b8697-117">This command displays the files and folders that are referenced by joining the C:\Win\* path and the System\* child path.</span></span>
<span data-ttu-id="b8697-118">Den visar samma filer och mappar som `Get-ChildItem` , men visar den fullständigt kvalificerade sökvägen till varje objekt.</span><span class="sxs-lookup"><span data-stu-id="b8697-118">It displays the same files and folders as `Get-ChildItem`, but it displays the fully qualified path to each item.</span></span>
<span data-ttu-id="b8697-119">I det här kommandot `Path` `ChildPath` utelämnas de valfria parameter namnen.</span><span class="sxs-lookup"><span data-stu-id="b8697-119">In this command, the `Path` and `ChildPath` optional parameter names are omitted.</span></span>

### <span data-ttu-id="b8697-120">Exempel 4: Använd Join-Path med PowerShell-dataprovidern</span><span class="sxs-lookup"><span data-stu-id="b8697-120">Example 4: Use Join-Path with the PowerShell registry provider</span></span>

```powershell
PS HKLM:\> Join-Path -Path System -ChildPath *ControlSet* -Resolve
```

```output
HKLM:\System\ControlSet001
HKLM:\System\CurrentControlSet
```

<span data-ttu-id="b8697-121">Det här kommandot visar register nycklarna i `HKLM\System` register under nyckeln som innehåller `ControlSet` .</span><span class="sxs-lookup"><span data-stu-id="b8697-121">This command displays the registry keys in the `HKLM\System` registry subkey that include `ControlSet`.</span></span>

<span data-ttu-id="b8697-122">`Resolve`Parametern försöker matcha den anslutna sökvägen, inklusive jokertecken från den aktuella providerns sökväg`HKLM:\`</span><span class="sxs-lookup"><span data-stu-id="b8697-122">The `Resolve` parameter, attempts to resolve the joined path, including wildcards from the current provider path `HKLM:\`</span></span>

### <span data-ttu-id="b8697-123">Exempel 5: kombinera flera Sök vägs rötter med en underordnad sökväg</span><span class="sxs-lookup"><span data-stu-id="b8697-123">Example 5: Combine multiple path roots with a child path</span></span>

```powershell
Join-Path -Path C:, D:, E:, F: -ChildPath New
```

```output
C:\New
D:\New
E:\New
F:\New
```

<span data-ttu-id="b8697-124">Det här kommandot använder `Join-Path` för att kombinera flera Sök vägs rötter med en underordnad sökväg.</span><span class="sxs-lookup"><span data-stu-id="b8697-124">This command uses `Join-Path` to combine multiple path roots with a child path.</span></span>

> [!NOTE]
> <span data-ttu-id="b8697-125">De enheter som anges av `Path` måste finnas eller så går det inte att ansluta till posten.</span><span class="sxs-lookup"><span data-stu-id="b8697-125">The Drives specified by `Path` must exist or the join of that entry will fail.</span></span>

### <span data-ttu-id="b8697-126">Exempel 6: kombinera rötter för en fil system enhet med en underordnad sökväg</span><span class="sxs-lookup"><span data-stu-id="b8697-126">Example 6: Combine the roots of a file system drive with a child path</span></span>

```powershell
Get-PSDrive -PSProvider filesystem | ForEach-Object {$_.root} | Join-Path -ChildPath "Subdir"
```

```output
C:\Subdir
D:\Subdir
```

<span data-ttu-id="b8697-127">Detta kommando kombinerar rötter för varje PowerShell-fil system enhet i-konsolen med den underordnade Underkat-sökvägen.</span><span class="sxs-lookup"><span data-stu-id="b8697-127">This command combines the roots of each PowerShell file system drive in the console with the Subdir child path.</span></span>

<span data-ttu-id="b8697-128">Kommandot använder `Get-PSDrive` cmdleten för att hämta de PowerShell-enheter som stöds av fil tjänst leverantören.</span><span class="sxs-lookup"><span data-stu-id="b8697-128">The command uses the `Get-PSDrive` cmdlet to get the PowerShell drives supported by the FileSystem provider.</span></span>
<span data-ttu-id="b8697-129">`ForEach-Object`Instruktionen väljer bara rot egenskapen för `PSDriveInfo` objekten och kombinerar den med den angivna underordnade sökvägen.</span><span class="sxs-lookup"><span data-stu-id="b8697-129">The `ForEach-Object` statement selects only the Root property of the `PSDriveInfo` objects and combines it with the specified child path.</span></span>

<span data-ttu-id="b8697-130">Utdata visar att PowerShell-enheterna på datorn innehåller en enhet som är mappad till katalogen C:\Programs.</span><span class="sxs-lookup"><span data-stu-id="b8697-130">The output shows that the PowerShell drives on the computer included a drive mapped to the C:\Program Files directory.</span></span>

### <span data-ttu-id="b8697-131">Exempel 7: kombinera ett obestämt antal sökvägar</span><span class="sxs-lookup"><span data-stu-id="b8697-131">Example 7: Combine an indefinite number of paths</span></span>

```powershell
Join-Path a b c d e f g
```

```Output
a\b\c\d\e\f\g
```

<span data-ttu-id="b8697-132">`AdditionalChildPath`Parametern gör det möjligt att ansluta till ett obegränsat antal sökvägar.</span><span class="sxs-lookup"><span data-stu-id="b8697-132">The `AdditionalChildPath` parameter allows the joining of an unlimited number of paths.</span></span>

<span data-ttu-id="b8697-133">I det här exemplet används inga parameter namn, vilket innebär att "a" binder till `Path` , "b" till `ChildPath` och "c-g" till `AdditionalChildPath`</span><span class="sxs-lookup"><span data-stu-id="b8697-133">In this example, no parameter names are used, thus "a" binds to `Path`, "b" to `ChildPath` and "c-g" to `AdditionalChildPath`</span></span>

## <span data-ttu-id="b8697-134">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="b8697-134">PARAMETERS</span></span>

### <span data-ttu-id="b8697-135">-AdditionalChildPath</span><span class="sxs-lookup"><span data-stu-id="b8697-135">-AdditionalChildPath</span></span>

<span data-ttu-id="b8697-136">Anger ytterligare element som ska läggas till i värdet för parametern *Path* .</span><span class="sxs-lookup"><span data-stu-id="b8697-136">Specifies additional elements to append to the value of the *Path* parameter.</span></span> <span data-ttu-id="b8697-137">`ChildPath`Parametern är fortfarande obligatorisk och måste också anges.</span><span class="sxs-lookup"><span data-stu-id="b8697-137">The `ChildPath` parameter is still mandatory and must be specified as well.</span></span>

<span data-ttu-id="b8697-138">Den här parametern anges med `ValueFromRemainingArguments` egenskapen som gör det möjligt att ansluta till ett obestämt antal sökvägar.</span><span class="sxs-lookup"><span data-stu-id="b8697-138">This parameter is specified with the `ValueFromRemainingArguments` property which enables joining an indefinite number of paths.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 2
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="b8697-139">-ChildPath</span><span class="sxs-lookup"><span data-stu-id="b8697-139">-ChildPath</span></span>

<span data-ttu-id="b8697-140">Anger de element som ska läggas till i `Path` parameterns värde.</span><span class="sxs-lookup"><span data-stu-id="b8697-140">Specifies the elements to append to the value of the `Path` parameter.</span></span>
<span data-ttu-id="b8697-141">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="b8697-141">Wildcards are permitted.</span></span>
<span data-ttu-id="b8697-142">`ChildPath`Parametern är obligatorisk, men parameter namnet ("ChildPath") är valfritt.</span><span class="sxs-lookup"><span data-stu-id="b8697-142">The `ChildPath` parameter is required, although the parameter name ("ChildPath") is optional.</span></span>

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

### <span data-ttu-id="b8697-143">-Credential</span><span class="sxs-lookup"><span data-stu-id="b8697-143">-Credential</span></span>

> [!NOTE]
> <span data-ttu-id="b8697-144">Den här parametern stöds inte av några providrar som installeras med PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b8697-144">This parameter is not supported by any providers installed with PowerShell.</span></span>
> <span data-ttu-id="b8697-145">Om du vill personifiera en annan användare eller öka dina autentiseringsuppgifter när du kör denna cmdlet, använder du [Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md).</span><span class="sxs-lookup"><span data-stu-id="b8697-145">To impersonate another user, or elevate your credentials when running this cmdlet, use [Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md).</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="b8697-146">-Path</span><span class="sxs-lookup"><span data-stu-id="b8697-146">-Path</span></span>

<span data-ttu-id="b8697-147">Anger den huvud Sök väg (eller sökvägar) som den underordnade sökvägen ska läggas till i.</span><span class="sxs-lookup"><span data-stu-id="b8697-147">Specifies the main path (or paths) to which the child-path is appended.</span></span>
<span data-ttu-id="b8697-148">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="b8697-148">Wildcards are permitted.</span></span>

<span data-ttu-id="b8697-149">Värdet för `Path` avgör vilken provider som ansluter till Sök vägarna och lägger till Sök vägs avgränsare.</span><span class="sxs-lookup"><span data-stu-id="b8697-149">The value of `Path` determines which provider joins the paths and adds the path delimiters.</span></span>
<span data-ttu-id="b8697-150">`Path`Parametern är obligatorisk, men parameter namnet (sökväg) är valfritt.</span><span class="sxs-lookup"><span data-stu-id="b8697-150">The `Path` parameter is required, although the parameter name ("Path") is optional.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: PSPath

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### <span data-ttu-id="b8697-151">-Lös</span><span class="sxs-lookup"><span data-stu-id="b8697-151">-Resolve</span></span>

<span data-ttu-id="b8697-152">Anger att denna cmdlet ska försöka matcha den anslutna sökvägen från den aktuella providern.</span><span class="sxs-lookup"><span data-stu-id="b8697-152">Indicates that this cmdlet should attempt to resolve the joined path from the current provider.</span></span>

- <span data-ttu-id="b8697-153">Om jokertecken används, returnerar cmdleten alla sökvägar som matchar den anslutna sökvägen.</span><span class="sxs-lookup"><span data-stu-id="b8697-153">If wildcards are used, the cmdlet returns all paths that match the joined path.</span></span>
- <span data-ttu-id="b8697-154">Om **inga** jokertecken används, kommer cmdleten att fel om sökvägen inte finns.</span><span class="sxs-lookup"><span data-stu-id="b8697-154">If **no** wildcards are used, the cmdlet will error if the path does not exist.</span></span>

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

### <span data-ttu-id="b8697-155">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="b8697-155">CommonParameters</span></span>

<span data-ttu-id="b8697-156">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="b8697-156">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="b8697-157">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="b8697-157">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="b8697-158">INDATA</span><span class="sxs-lookup"><span data-stu-id="b8697-158">INPUTS</span></span>

### <span data-ttu-id="b8697-159">System. String</span><span class="sxs-lookup"><span data-stu-id="b8697-159">System.String</span></span>

<span data-ttu-id="b8697-160">Du kan skicka vidare en sträng som innehåller en sökväg till denna cmdlet.</span><span class="sxs-lookup"><span data-stu-id="b8697-160">You can pipe a string that contains a path to this cmdlet.</span></span>

## <span data-ttu-id="b8697-161">UTDATA</span><span class="sxs-lookup"><span data-stu-id="b8697-161">OUTPUTS</span></span>

### <span data-ttu-id="b8697-162">System. String</span><span class="sxs-lookup"><span data-stu-id="b8697-162">System.String</span></span>

<span data-ttu-id="b8697-163">Denna cmdlet returnerar en sträng som innehåller den resulterande sökvägen.</span><span class="sxs-lookup"><span data-stu-id="b8697-163">This cmdlet returns a string that contains the resulting path.</span></span>

## <span data-ttu-id="b8697-164">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="b8697-164">NOTES</span></span>

<span data-ttu-id="b8697-165">Cmdlet: arna som innehåller sökvägen Substantiv (Sök vägs-cmdletar) ändrar Sök vägs namn och returnerar namnen i ett koncist format som alla PowerShell-leverantörer kan tolka.</span><span class="sxs-lookup"><span data-stu-id="b8697-165">The cmdlets that contain the Path noun (the Path cmdlets) manipulate path names and return the names in a concise format that all PowerShell providers can interpret.</span></span> <span data-ttu-id="b8697-166">De är utformade för användning i program och skript där du vill visa hela eller delar av ett Sök vägs namn i ett visst format.</span><span class="sxs-lookup"><span data-stu-id="b8697-166">They are designed for use in programs and scripts where you want to display all or part of a path name in a particular format.</span></span> <span data-ttu-id="b8697-167">Använd dem på samma sätt som du använder Logsdirectory, Normpath, realpath, JOIN eller andra Sök vägs manipulerare.</span><span class="sxs-lookup"><span data-stu-id="b8697-167">Use them like you would use Dirname, Normpath, Realpath, Join, or other path manipulators.</span></span>

<span data-ttu-id="b8697-168">Du kan använda Sök vägs-cmdlet: ar med flera providers, inklusive `FileSystem` -, `Registry` -och- `Certificate` providers.</span><span class="sxs-lookup"><span data-stu-id="b8697-168">You can use the path cmdlets with several providers, including the `FileSystem`, `Registry`, and `Certificate` providers.</span></span>

<span data-ttu-id="b8697-169">Denna cmdlet är utformad för att fungera med data som exponeras av vilken provider som helst.</span><span class="sxs-lookup"><span data-stu-id="b8697-169">This cmdlet is designed to work with the data exposed by any provider.</span></span>
<span data-ttu-id="b8697-170">Om du vill visa en lista över tillgängliga providers i din session skriver du `Get-PSProvider` .</span><span class="sxs-lookup"><span data-stu-id="b8697-170">To list the providers available in your session, type `Get-PSProvider`.</span></span>
<span data-ttu-id="b8697-171">Mer information finns i [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span><span class="sxs-lookup"><span data-stu-id="b8697-171">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

## <span data-ttu-id="b8697-172">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="b8697-172">RELATED LINKS</span></span>

[<span data-ttu-id="b8697-173">Konvertera-sökväg</span><span class="sxs-lookup"><span data-stu-id="b8697-173">Convert-Path</span></span>](Convert-Path.md)

[<span data-ttu-id="b8697-174">Lös-sökväg</span><span class="sxs-lookup"><span data-stu-id="b8697-174">Resolve-Path</span></span>](Resolve-Path.md)

[<span data-ttu-id="b8697-175">Dela-sökväg</span><span class="sxs-lookup"><span data-stu-id="b8697-175">Split-Path</span></span>](Split-Path.md)

[<span data-ttu-id="b8697-176">Test-sökväg</span><span class="sxs-lookup"><span data-stu-id="b8697-176">Test-Path</span></span>](Test-Path.md)

[<span data-ttu-id="b8697-177">Get-PSProvider</span><span class="sxs-lookup"><span data-stu-id="b8697-177">Get-PSProvider</span></span>](Get-PSProvider.md)

[<span data-ttu-id="b8697-178">Get-ChildItem</span><span class="sxs-lookup"><span data-stu-id="b8697-178">Get-ChildItem</span></span>](Get-ChildItem.md)

[<span data-ttu-id="b8697-179">Get-PSDrive</span><span class="sxs-lookup"><span data-stu-id="b8697-179">Get-PSDrive</span></span>](Get-PSDrive.md)
