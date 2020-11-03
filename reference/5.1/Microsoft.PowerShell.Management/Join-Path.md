---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/join-path?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Join-Path
ms.openlocfilehash: bcba432fb52b327695b61a4475d4a93903a688a5
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93265568"
---
# <span data-ttu-id="cd9ef-103">Join-Path</span><span class="sxs-lookup"><span data-stu-id="cd9ef-103">Join-Path</span></span>

## <span data-ttu-id="cd9ef-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="cd9ef-104">SYNOPSIS</span></span>
<span data-ttu-id="cd9ef-105">Kombinerar en sökväg och en underordnad sökväg till en enda sökväg.</span><span class="sxs-lookup"><span data-stu-id="cd9ef-105">Combines a path and a child path into a single path.</span></span>

## <span data-ttu-id="cd9ef-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="cd9ef-106">SYNTAX</span></span>

```
Join-Path [-Path] <String[]> [-ChildPath] <String> [-Resolve] [-Credential <PSCredential>] [-UseTransaction]
 [<CommonParameters>]
```

## <span data-ttu-id="cd9ef-107">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="cd9ef-107">DESCRIPTION</span></span>

<span data-ttu-id="cd9ef-108">`Join-Path`Cmdleten kombinerar en sökväg och en underordnad sökväg till en enda sökväg.</span><span class="sxs-lookup"><span data-stu-id="cd9ef-108">The `Join-Path` cmdlet combines a path and child-path into a single path.</span></span>
<span data-ttu-id="cd9ef-109">Providern tillhandahåller Sök vägs avgränsare.</span><span class="sxs-lookup"><span data-stu-id="cd9ef-109">The provider supplies the path delimiters.</span></span>

## <span data-ttu-id="cd9ef-110">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="cd9ef-110">EXAMPLES</span></span>

### <span data-ttu-id="cd9ef-111">Exempel 1: kombinera en sökväg med en underordnad sökväg</span><span class="sxs-lookup"><span data-stu-id="cd9ef-111">Example 1: Combine a path with a child path</span></span>

```powershell
PS C:\> Join-Path -Path "path" -ChildPath "childpath"
```

```output
path\childpath
```

<span data-ttu-id="cd9ef-112">Det här kommandot använder `Join-Path` för att kombinera en sökväg med en childpath.</span><span class="sxs-lookup"><span data-stu-id="cd9ef-112">This command uses `Join-Path` to combine a path with a childpath.</span></span>

<span data-ttu-id="cd9ef-113">Eftersom kommandot körs från `FileSystem` providern, är det den `\` avgränsare som ska användas för att ansluta Sök vägarna.</span><span class="sxs-lookup"><span data-stu-id="cd9ef-113">Since the command is executed from the `FileSystem` provider, it provides the `\` delimiter to join the paths.</span></span>

### <span data-ttu-id="cd9ef-114">Exempel 2: kombinera sökvägar som redan innehåller katalog avgränsare</span><span class="sxs-lookup"><span data-stu-id="cd9ef-114">Example 2: Combine paths that already contain directory separators</span></span>

```powershell
PS C:\> Join-Path -Path "path\" -ChildPath "\childpath"
```

```output
path\childpath
```

<span data-ttu-id="cd9ef-115">Befintliga katalog avgränsare `\` och hanterade så det finns bara en avgränsare mellan `Path` och `ChildPath`</span><span class="sxs-lookup"><span data-stu-id="cd9ef-115">Existing directory separators `\` and handled so there is only one separator between `Path` and `ChildPath`</span></span>

### <span data-ttu-id="cd9ef-116">Exempel 3: Visa filer och mappar genom att koppla en sökväg med en underordnad sökväg</span><span class="sxs-lookup"><span data-stu-id="cd9ef-116">Example 3: Display files and folders by joining a path with a child path</span></span>

```powershell
Join-Path "C:\win*" "System*" -Resolve
```

<span data-ttu-id="cd9ef-117">Det här kommandot visar de filer och mappar som refereras till genom att ansluta till C:\Win- \* sökvägen och den \* underordnade system Sök vägen.</span><span class="sxs-lookup"><span data-stu-id="cd9ef-117">This command displays the files and folders that are referenced by joining the C:\Win\* path and the System\* child path.</span></span>
<span data-ttu-id="cd9ef-118">Den visar samma filer och mappar som `Get-ChildItem` , men visar den fullständigt kvalificerade sökvägen till varje objekt.</span><span class="sxs-lookup"><span data-stu-id="cd9ef-118">It displays the same files and folders as `Get-ChildItem`, but it displays the fully qualified path to each item.</span></span>
<span data-ttu-id="cd9ef-119">I det här kommandot `Path` `ChildPath` utelämnas de valfria parameter namnen.</span><span class="sxs-lookup"><span data-stu-id="cd9ef-119">In this command, the `Path` and `ChildPath` optional parameter names are omitted.</span></span>

### <span data-ttu-id="cd9ef-120">Exempel 4: Använd Join-Path med PowerShell-dataprovidern</span><span class="sxs-lookup"><span data-stu-id="cd9ef-120">Example 4: Use Join-Path with the PowerShell registry provider</span></span>

```powershell
PS HKLM:\> Join-Path -Path System -ChildPath *ControlSet* -Resolve
```

```output
HKLM:\System\ControlSet001
HKLM:\System\CurrentControlSet
```

<span data-ttu-id="cd9ef-121">Det här kommandot visar register nycklarna i `HKLM\System` register under nyckeln som innehåller `ControlSet` .</span><span class="sxs-lookup"><span data-stu-id="cd9ef-121">This command displays the registry keys in the `HKLM\System` registry subkey that include `ControlSet`.</span></span>

<span data-ttu-id="cd9ef-122">`Resolve`Parametern försöker matcha den anslutna sökvägen, inklusive jokertecken från den aktuella providerns sökväg`HKLM:\`</span><span class="sxs-lookup"><span data-stu-id="cd9ef-122">The `Resolve` parameter, attempts to resolve the joined path, including wildcards from the current provider path `HKLM:\`</span></span>

### <span data-ttu-id="cd9ef-123">Exempel 5: kombinera flera Sök vägs rötter med en underordnad sökväg</span><span class="sxs-lookup"><span data-stu-id="cd9ef-123">Example 5: Combine multiple path roots with a child path</span></span>

```powershell
Join-Path -Path C:, D:, E:, F: -ChildPath New
```

```output
C:\New
D:\New
E:\New
F:\New
```

<span data-ttu-id="cd9ef-124">Det här kommandot använder `Join-Path` för att kombinera flera Sök vägs rötter med en underordnad sökväg.</span><span class="sxs-lookup"><span data-stu-id="cd9ef-124">This command uses `Join-Path` to combine multiple path roots with a child path.</span></span>

> [!NOTE]
> <span data-ttu-id="cd9ef-125">De enheter som anges av `Path` måste finnas eller så går det inte att ansluta till posten.</span><span class="sxs-lookup"><span data-stu-id="cd9ef-125">The Drives specified by `Path` must exist or the join of that entry will fail.</span></span>

### <span data-ttu-id="cd9ef-126">Exempel 6: kombinera rötter för en fil system enhet med en underordnad sökväg</span><span class="sxs-lookup"><span data-stu-id="cd9ef-126">Example 6: Combine the roots of a file system drive with a child path</span></span>

```powershell
Get-PSDrive -PSProvider filesystem | ForEach-Object {$_.root} | Join-Path -ChildPath "Subdir"
```

```output
C:\Subdir
D:\Subdir
```

<span data-ttu-id="cd9ef-127">Detta kommando kombinerar rötter för varje PowerShell-fil system enhet i-konsolen med den underordnade Underkat-sökvägen.</span><span class="sxs-lookup"><span data-stu-id="cd9ef-127">This command combines the roots of each PowerShell file system drive in the console with the Subdir child path.</span></span>

<span data-ttu-id="cd9ef-128">Kommandot använder `Get-PSDrive` cmdleten för att hämta de PowerShell-enheter som stöds av fil tjänst leverantören.</span><span class="sxs-lookup"><span data-stu-id="cd9ef-128">The command uses the `Get-PSDrive` cmdlet to get the PowerShell drives supported by the FileSystem provider.</span></span>
<span data-ttu-id="cd9ef-129">`ForEach-Object`Instruktionen väljer bara rot egenskapen för `PSDriveInfo` objekten och kombinerar den med den angivna underordnade sökvägen.</span><span class="sxs-lookup"><span data-stu-id="cd9ef-129">The `ForEach-Object` statement selects only the Root property of the `PSDriveInfo` objects and combines it with the specified child path.</span></span>

<span data-ttu-id="cd9ef-130">Utdata visar att PowerShell-enheterna på datorn innehåller en enhet som är mappad till katalogen C:\Programs.</span><span class="sxs-lookup"><span data-stu-id="cd9ef-130">The output shows that the PowerShell drives on the computer included a drive mapped to the C:\Program Files directory.</span></span>

## <span data-ttu-id="cd9ef-131">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="cd9ef-131">PARAMETERS</span></span>

### <span data-ttu-id="cd9ef-132">-ChildPath</span><span class="sxs-lookup"><span data-stu-id="cd9ef-132">-ChildPath</span></span>

<span data-ttu-id="cd9ef-133">Anger de element som ska läggas till i `Path` parameterns värde.</span><span class="sxs-lookup"><span data-stu-id="cd9ef-133">Specifies the elements to append to the value of the `Path` parameter.</span></span>
<span data-ttu-id="cd9ef-134">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="cd9ef-134">Wildcards are permitted.</span></span>
<span data-ttu-id="cd9ef-135">`ChildPath`Parametern är obligatorisk, men parameter namnet ("ChildPath") är valfritt.</span><span class="sxs-lookup"><span data-stu-id="cd9ef-135">The `ChildPath` parameter is required, although the parameter name ("ChildPath") is optional.</span></span>

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

### <span data-ttu-id="cd9ef-136">-Credential</span><span class="sxs-lookup"><span data-stu-id="cd9ef-136">-Credential</span></span>

> [!NOTE]
> <span data-ttu-id="cd9ef-137">Den här parametern stöds inte av några providrar som installeras med PowerShell.</span><span class="sxs-lookup"><span data-stu-id="cd9ef-137">This parameter is not supported by any providers installed with PowerShell.</span></span>
> <span data-ttu-id="cd9ef-138">Om du vill personifiera en annan användare eller öka dina autentiseringsuppgifter när du kör denna cmdlet, använder du [Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md).</span><span class="sxs-lookup"><span data-stu-id="cd9ef-138">To impersonate another user, or elevate your credentials when running this cmdlet, use [Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md).</span></span>

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

### <span data-ttu-id="cd9ef-139">-Path</span><span class="sxs-lookup"><span data-stu-id="cd9ef-139">-Path</span></span>

<span data-ttu-id="cd9ef-140">Anger den huvud Sök väg (eller sökvägar) som den underordnade sökvägen ska läggas till i.</span><span class="sxs-lookup"><span data-stu-id="cd9ef-140">Specifies the main path (or paths) to which the child-path is appended.</span></span>
<span data-ttu-id="cd9ef-141">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="cd9ef-141">Wildcards are permitted.</span></span>

<span data-ttu-id="cd9ef-142">Värdet för `Path` avgör vilken provider som ansluter till Sök vägarna och lägger till Sök vägs avgränsare.</span><span class="sxs-lookup"><span data-stu-id="cd9ef-142">The value of `Path` determines which provider joins the paths and adds the path delimiters.</span></span>
<span data-ttu-id="cd9ef-143">`Path`Parametern är obligatorisk, men parameter namnet (sökväg) är valfritt.</span><span class="sxs-lookup"><span data-stu-id="cd9ef-143">The `Path` parameter is required, although the parameter name ("Path") is optional.</span></span>

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

### <span data-ttu-id="cd9ef-144">-Lös</span><span class="sxs-lookup"><span data-stu-id="cd9ef-144">-Resolve</span></span>

<span data-ttu-id="cd9ef-145">Anger att denna cmdlet ska försöka matcha den anslutna sökvägen från den aktuella providern.</span><span class="sxs-lookup"><span data-stu-id="cd9ef-145">Indicates that this cmdlet should attempt to resolve the joined path from the current provider.</span></span>

- <span data-ttu-id="cd9ef-146">Om jokertecken används, returnerar cmdleten alla sökvägar som matchar den anslutna sökvägen.</span><span class="sxs-lookup"><span data-stu-id="cd9ef-146">If wildcards are used, the cmdlet returns all paths that match the joined path.</span></span>
- <span data-ttu-id="cd9ef-147">Om **inga** jokertecken används, kommer cmdleten att fel om sökvägen inte finns.</span><span class="sxs-lookup"><span data-stu-id="cd9ef-147">If **no** wildcards are used, the cmdlet will error if the path does not exist.</span></span>

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

### <span data-ttu-id="cd9ef-148">– UseTransaction</span><span class="sxs-lookup"><span data-stu-id="cd9ef-148">-UseTransaction</span></span>

<span data-ttu-id="cd9ef-149">Inkluderar kommandot i den aktiva transaktionen.</span><span class="sxs-lookup"><span data-stu-id="cd9ef-149">Includes the command in the active transaction.</span></span>
<span data-ttu-id="cd9ef-150">Den här parametern är bara giltig medan en transaktion pågår.</span><span class="sxs-lookup"><span data-stu-id="cd9ef-150">This parameter is valid only when a transaction is in progress.</span></span>
<span data-ttu-id="cd9ef-151">Mer information finns i [about_Transactions](../Microsoft.PowerShell.Core/About/about_Transactions.md).</span><span class="sxs-lookup"><span data-stu-id="cd9ef-151">For more information, see [about_Transactions](../Microsoft.PowerShell.Core/About/about_Transactions.md).</span></span>

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

### <span data-ttu-id="cd9ef-152">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="cd9ef-152">CommonParameters</span></span>

<span data-ttu-id="cd9ef-153">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="cd9ef-153">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="cd9ef-154">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="cd9ef-154">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="cd9ef-155">INDATA</span><span class="sxs-lookup"><span data-stu-id="cd9ef-155">INPUTS</span></span>

### <span data-ttu-id="cd9ef-156">System. String</span><span class="sxs-lookup"><span data-stu-id="cd9ef-156">System.String</span></span>

<span data-ttu-id="cd9ef-157">Du kan skicka vidare en sträng som innehåller en sökväg till denna cmdlet.</span><span class="sxs-lookup"><span data-stu-id="cd9ef-157">You can pipe a string that contains a path to this cmdlet.</span></span>

## <span data-ttu-id="cd9ef-158">UTDATA</span><span class="sxs-lookup"><span data-stu-id="cd9ef-158">OUTPUTS</span></span>

### <span data-ttu-id="cd9ef-159">System. String</span><span class="sxs-lookup"><span data-stu-id="cd9ef-159">System.String</span></span>

<span data-ttu-id="cd9ef-160">Denna cmdlet returnerar en sträng som innehåller den resulterande sökvägen.</span><span class="sxs-lookup"><span data-stu-id="cd9ef-160">This cmdlet returns a string that contains the resulting path.</span></span>

## <span data-ttu-id="cd9ef-161">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="cd9ef-161">NOTES</span></span>

<span data-ttu-id="cd9ef-162">Cmdlet: arna som innehåller sökvägen Substantiv (Sök vägs-cmdletar) ändrar Sök vägs namn och returnerar namnen i ett koncist format som alla PowerShell-leverantörer kan tolka.</span><span class="sxs-lookup"><span data-stu-id="cd9ef-162">The cmdlets that contain the Path noun (the Path cmdlets) manipulate path names and return the names in a concise format that all PowerShell providers can interpret.</span></span> <span data-ttu-id="cd9ef-163">De är utformade för användning i program och skript där du vill visa hela eller delar av ett Sök vägs namn i ett visst format.</span><span class="sxs-lookup"><span data-stu-id="cd9ef-163">They are designed for use in programs and scripts where you want to display all or part of a path name in a particular format.</span></span> <span data-ttu-id="cd9ef-164">Använd dem på samma sätt som du använder Logsdirectory, Normpath, realpath, JOIN eller andra Sök vägs manipulerare.</span><span class="sxs-lookup"><span data-stu-id="cd9ef-164">Use them like you would use Dirname, Normpath, Realpath, Join, or other path manipulators.</span></span>

<span data-ttu-id="cd9ef-165">Du kan använda Sök vägs-cmdlet: ar med flera providers, inklusive `FileSystem` -, `Registry` -och- `Certificate` providers.</span><span class="sxs-lookup"><span data-stu-id="cd9ef-165">You can use the path cmdlets with several providers, including the `FileSystem`, `Registry`, and `Certificate` providers.</span></span>

<span data-ttu-id="cd9ef-166">Denna cmdlet är utformad för att fungera med data som exponeras av vilken provider som helst.</span><span class="sxs-lookup"><span data-stu-id="cd9ef-166">This cmdlet is designed to work with the data exposed by any provider.</span></span>
<span data-ttu-id="cd9ef-167">Om du vill visa en lista över tillgängliga providers i din session skriver du `Get-PSProvider` .</span><span class="sxs-lookup"><span data-stu-id="cd9ef-167">To list the providers available in your session, type `Get-PSProvider`.</span></span>
<span data-ttu-id="cd9ef-168">Mer information finns i [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span><span class="sxs-lookup"><span data-stu-id="cd9ef-168">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

## <span data-ttu-id="cd9ef-169">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="cd9ef-169">RELATED LINKS</span></span>

[<span data-ttu-id="cd9ef-170">Konvertera-sökväg</span><span class="sxs-lookup"><span data-stu-id="cd9ef-170">Convert-Path</span></span>](Convert-Path.md)

[<span data-ttu-id="cd9ef-171">Lös-sökväg</span><span class="sxs-lookup"><span data-stu-id="cd9ef-171">Resolve-Path</span></span>](Resolve-Path.md)

[<span data-ttu-id="cd9ef-172">Dela-sökväg</span><span class="sxs-lookup"><span data-stu-id="cd9ef-172">Split-Path</span></span>](Split-Path.md)

[<span data-ttu-id="cd9ef-173">Test-sökväg</span><span class="sxs-lookup"><span data-stu-id="cd9ef-173">Test-Path</span></span>](Test-Path.md)

[<span data-ttu-id="cd9ef-174">Get-PSProvider</span><span class="sxs-lookup"><span data-stu-id="cd9ef-174">Get-PSProvider</span></span>](Get-PSProvider.md)

[<span data-ttu-id="cd9ef-175">Get-ChildItem</span><span class="sxs-lookup"><span data-stu-id="cd9ef-175">Get-ChildItem</span></span>](Get-ChildItem.md)

[<span data-ttu-id="cd9ef-176">Get-PSDrive</span><span class="sxs-lookup"><span data-stu-id="cd9ef-176">Get-PSDrive</span></span>](Get-PSDrive.md)
