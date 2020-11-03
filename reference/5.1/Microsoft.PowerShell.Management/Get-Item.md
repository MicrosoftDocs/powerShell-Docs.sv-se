---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 03/27/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/get-item?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Item
ms.openlocfilehash: 1498c7eb254e0d21b108c4016d8b737d5b33298d
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93266127"
---
# <span data-ttu-id="218b0-103">Get-Item</span><span class="sxs-lookup"><span data-stu-id="218b0-103">Get-Item</span></span>

## <span data-ttu-id="218b0-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="218b0-104">SYNOPSIS</span></span>
<span data-ttu-id="218b0-105">Hämtar objektet på den angivna platsen.</span><span class="sxs-lookup"><span data-stu-id="218b0-105">Gets the item at the specified location.</span></span>

## <span data-ttu-id="218b0-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="218b0-106">SYNTAX</span></span>

### <span data-ttu-id="218b0-107">Sökväg (standard)</span><span class="sxs-lookup"><span data-stu-id="218b0-107">Path (Default)</span></span>

```
Get-Item [-Path] <String[]> [-Filter <String>] [-Include <String[]>] [-Exclude <String[]>] [-Force]
 [-Credential <PSCredential>] [-UseTransaction] [-Stream <String[]>] [<CommonParameters>]
```

### <span data-ttu-id="218b0-108">LiteralPath</span><span class="sxs-lookup"><span data-stu-id="218b0-108">LiteralPath</span></span>

```
Get-Item -LiteralPath <String[]> [-Filter <String>] [-Include <String[]>] [-Exclude <String[]>] [-Force]
 [-Credential <PSCredential>] [-UseTransaction] [-Stream <String[]>] [<CommonParameters>]
```

## <span data-ttu-id="218b0-109">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="218b0-109">DESCRIPTION</span></span>

<span data-ttu-id="218b0-110">`Get-Item`Cmdlet: en hämtar objektet på den angivna platsen.</span><span class="sxs-lookup"><span data-stu-id="218b0-110">The `Get-Item` cmdlet gets the item at the specified location.</span></span> <span data-ttu-id="218b0-111">Det får inte innehållet i objektet på platsen om du inte använder ett jokertecken ( `*` ) för att begära allt innehåll i objektet.</span><span class="sxs-lookup"><span data-stu-id="218b0-111">It doesn't get the contents of the item at the location unless you use a wildcard character (`*`) to request all the contents of the item.</span></span>

<span data-ttu-id="218b0-112">Denna cmdlet används av PowerShell-leverantörer för att navigera mellan olika typer av data lager.</span><span class="sxs-lookup"><span data-stu-id="218b0-112">This cmdlet is used by PowerShell providers to navigate through different types of data stores.</span></span>

## <span data-ttu-id="218b0-113">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="218b0-113">EXAMPLES</span></span>

### <span data-ttu-id="218b0-114">Exempel 1: hämta den aktuella katalogen</span><span class="sxs-lookup"><span data-stu-id="218b0-114">Example 1: Get the current directory</span></span>

<span data-ttu-id="218b0-115">Det här exemplet hämtar den aktuella katalogen.</span><span class="sxs-lookup"><span data-stu-id="218b0-115">This example gets the current directory.</span></span> <span data-ttu-id="218b0-116">Punkten ('. ') representerar objektet på den aktuella platsen (inte dess innehåll).</span><span class="sxs-lookup"><span data-stu-id="218b0-116">The dot ('.') represents the item at the current location (not its contents).</span></span>

```powershell
Get-Item .
```

```output
Directory: C:\

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
d----         7/26/2006  10:01 AM            ps-test
```

### <span data-ttu-id="218b0-117">Exempel 2: Hämta alla objekt i den aktuella katalogen</span><span class="sxs-lookup"><span data-stu-id="218b0-117">Example 2: Get all the items in the current directory</span></span>

<span data-ttu-id="218b0-118">Det här exemplet hämtar alla objekt i den aktuella katalogen.</span><span class="sxs-lookup"><span data-stu-id="218b0-118">This example gets all the items in the current directory.</span></span> <span data-ttu-id="218b0-119">Jokertecknet ( `*` ) representerar allt innehåll i det aktuella objektet.</span><span class="sxs-lookup"><span data-stu-id="218b0-119">The wildcard character (`*`) represents all the contents of the current item.</span></span>

```powershell
Get-Item *
```

```output
Directory: C:\ps-test

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
d----         7/26/2006   9:29 AM            Logs
d----         7/26/2006   9:26 AM            Recs
-a---         7/26/2006   9:28 AM         80 date.csv
-a---         7/26/2006  10:01 AM         30 filenoext
-a---         7/26/2006   9:30 AM      11472 process.doc
-a---         7/14/2006  10:47 AM         30 test.txt
```

### <span data-ttu-id="218b0-120">Exempel 3: hämta den aktuella katalogen för en enhet</span><span class="sxs-lookup"><span data-stu-id="218b0-120">Example 3: Get the current directory of a drive</span></span>

<span data-ttu-id="218b0-121">Det här exemplet hämtar enhetens aktuella katalog `C:` .</span><span class="sxs-lookup"><span data-stu-id="218b0-121">This example gets the current directory of the `C:` drive.</span></span> <span data-ttu-id="218b0-122">Objektet som hämtas representerar bara katalogen, inte dess innehåll.</span><span class="sxs-lookup"><span data-stu-id="218b0-122">The object that is retrieved represents only the directory, not its contents.</span></span>

```powershell
Get-Item C:\
```

### <span data-ttu-id="218b0-123">Exempel 4: Hämta objekt på den angivna enheten</span><span class="sxs-lookup"><span data-stu-id="218b0-123">Example 4: Get items in the specified drive</span></span>

<span data-ttu-id="218b0-124">I det här exemplet hämtas objekt i `C:` enheten.</span><span class="sxs-lookup"><span data-stu-id="218b0-124">This example gets the items in the `C:` drive.</span></span> <span data-ttu-id="218b0-125">Jokertecknet ( `*` ) representerar alla objekt i behållaren, inte bara behållaren.</span><span class="sxs-lookup"><span data-stu-id="218b0-125">The wildcard character (`*`) represents all the items in the container, not just the container.</span></span>

```powershell
Get-Item C:\*
```

<span data-ttu-id="218b0-126">I PowerShell använder du en enda asterisk ( `*` ) för att hämta innehåll i stället för den traditionella `*.*` .</span><span class="sxs-lookup"><span data-stu-id="218b0-126">In PowerShell, use a single asterisk (`*`) to get contents, instead of the traditional `*.*`.</span></span> <span data-ttu-id="218b0-127">Formatet tolkas bokstavligen, så `*.*` skulle inte hämta kataloger eller fil namn utan punkt.</span><span class="sxs-lookup"><span data-stu-id="218b0-127">The format is interpreted literally, so `*.*` wouldn't retrieve directories or filenames without a dot.</span></span>

### <span data-ttu-id="218b0-128">Exempel 5: Hämta en egenskap i den angivna katalogen</span><span class="sxs-lookup"><span data-stu-id="218b0-128">Example 5: Get a property in the specified directory</span></span>

<span data-ttu-id="218b0-129">Det här exemplet hämtar katalogens **LastAccessTime** -egenskap `C:\Windows` .</span><span class="sxs-lookup"><span data-stu-id="218b0-129">This example gets the **LastAccessTime** property of the `C:\Windows` directory.</span></span> <span data-ttu-id="218b0-130">**LastAccessTime** är bara en egenskap för fil system kataloger.</span><span class="sxs-lookup"><span data-stu-id="218b0-130">**LastAccessTime** is just one property of file system directories.</span></span> <span data-ttu-id="218b0-131">Om du vill se alla egenskaper för en katalog skriver du `(Get-Item <directory-name>) | Get-Member` .</span><span class="sxs-lookup"><span data-stu-id="218b0-131">To see all the properties of a directory, type `(Get-Item <directory-name>) | Get-Member`.</span></span>

```powershell
(Get-Item C:\Windows).LastAccessTime
```

### <span data-ttu-id="218b0-132">Exempel 6: Visa innehållet i en register nyckel</span><span class="sxs-lookup"><span data-stu-id="218b0-132">Example 6: Show the contents of a registry key</span></span>

<span data-ttu-id="218b0-133">Det här exemplet visar innehållet i register nyckeln **Microsoft. PowerShell** .</span><span class="sxs-lookup"><span data-stu-id="218b0-133">This example shows the contents of the **Microsoft.PowerShell** registry key.</span></span> <span data-ttu-id="218b0-134">Du kan använda den här cmdleten med PowerShell-registerposten för att hämta register nycklar och under nycklar, men du måste använda cmdlet: en `Get-ItemProperty` för att hämta register värden och data.</span><span class="sxs-lookup"><span data-stu-id="218b0-134">You can use this cmdlet with the PowerShell Registry provider to get registry keys and subkeys, but you must use the `Get-ItemProperty` cmdlet to get the registry values and data.</span></span>

```powershell
Get-Item HKLM:\Software\Microsoft\Powershell\1\Shellids\Microsoft.Powershell\
```

### <span data-ttu-id="218b0-135">Exempel 7: Hämta objekt i en katalog som har ett undantag</span><span class="sxs-lookup"><span data-stu-id="218b0-135">Example 7: Get items in a directory that have an exclusion</span></span>

<span data-ttu-id="218b0-136">Det här exemplet hämtar objekt i Windows-katalogen med namn som innehåller en punkt ( `.` ), men börjar inte med `w*` . Det här exemplet fungerar bara om sökvägen innehåller ett jokertecken ( `*` ) för att ange innehållet i objektet.</span><span class="sxs-lookup"><span data-stu-id="218b0-136">This example gets items in the Windows directory with names that include a dot (`.`), but don't begin with `w*`.This example works only when the path includes a wildcard character (`*`) to specify the contents of the item.</span></span>

```powershell
Get-Item C:\Windows\*.* -Exclude "w*"
```

## <span data-ttu-id="218b0-137">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="218b0-137">PARAMETERS</span></span>

### <span data-ttu-id="218b0-138">-Stream</span><span class="sxs-lookup"><span data-stu-id="218b0-138">-Stream</span></span>

<span data-ttu-id="218b0-139">Hämtar den angivna alternativa NTFS-filströmmen från filen.</span><span class="sxs-lookup"><span data-stu-id="218b0-139">Gets the specified alternate NTFS file stream from the file.</span></span> <span data-ttu-id="218b0-140">Ange data ström namnet.</span><span class="sxs-lookup"><span data-stu-id="218b0-140">Enter the stream name.</span></span> <span data-ttu-id="218b0-141">Jokertecken stöds.</span><span class="sxs-lookup"><span data-stu-id="218b0-141">Wildcards are supported.</span></span> <span data-ttu-id="218b0-142">Använd en asterisk () om du vill hämta alla strömmar `*` .</span><span class="sxs-lookup"><span data-stu-id="218b0-142">To get all streams, use an asterisk (`*`).</span></span> <span data-ttu-id="218b0-143">Den här parametern är inte giltig i mapparna.</span><span class="sxs-lookup"><span data-stu-id="218b0-143">This parameter isn't valid on folders.</span></span>

<span data-ttu-id="218b0-144">**Stream** är en dynamisk parameter som **fil Systems** leverantören lägger till i `Get-Item` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="218b0-144">**Stream** is a dynamic parameter that the **FileSystem** provider adds to the `Get-Item` cmdlet.</span></span>
<span data-ttu-id="218b0-145">Den här parametern fungerar bara i fil system enheter.</span><span class="sxs-lookup"><span data-stu-id="218b0-145">This parameter works only in file system drives.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: No alternate file streams
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="218b0-146">-Credential</span><span class="sxs-lookup"><span data-stu-id="218b0-146">-Credential</span></span>

> [!NOTE]
> <span data-ttu-id="218b0-147">Den här parametern stöds inte av några providrar som installeras med PowerShell.</span><span class="sxs-lookup"><span data-stu-id="218b0-147">This parameter isn't supported by any providers installed with PowerShell.</span></span>
> <span data-ttu-id="218b0-148">Om du vill personifiera en annan användare eller öka dina autentiseringsuppgifter när du kör denna cmdlet, använder du [Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md).</span><span class="sxs-lookup"><span data-stu-id="218b0-148">To impersonate another user, or elevate your credentials when running this cmdlet, use [Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md).</span></span>

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

### <span data-ttu-id="218b0-149">-Undanta</span><span class="sxs-lookup"><span data-stu-id="218b0-149">-Exclude</span></span>

<span data-ttu-id="218b0-150">Anger, som en sträng mat ris, ett objekt eller objekt som denna cmdlet exkluderar i åtgärden.</span><span class="sxs-lookup"><span data-stu-id="218b0-150">Specifies, as a string array, an item or items that this cmdlet excludes in the operation.</span></span> <span data-ttu-id="218b0-151">Värdet för den här parametern kvalificerar parametern **Path** .</span><span class="sxs-lookup"><span data-stu-id="218b0-151">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="218b0-152">Ange ett Sök vägs element eller ett mönster, till exempel `*.txt` .</span><span class="sxs-lookup"><span data-stu-id="218b0-152">Enter a path element or pattern, such as `*.txt`.</span></span> <span data-ttu-id="218b0-153">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="218b0-153">Wildcard characters are permitted.</span></span> <span data-ttu-id="218b0-154">Parametern **exclude** är endast effektiv när kommandot innehåller innehållet i ett objekt, t. ex `C:\Windows\*` ., där jokertecknet anger innehållet i `C:\Windows` katalogen.</span><span class="sxs-lookup"><span data-stu-id="218b0-154">The **Exclude** parameter is effective only when the command includes the contents of an item, such as `C:\Windows\*`, where the wildcard character specifies the contents of the `C:\Windows` directory.</span></span>

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

### <span data-ttu-id="218b0-155">-Filter</span><span class="sxs-lookup"><span data-stu-id="218b0-155">-Filter</span></span>

<span data-ttu-id="218b0-156">Anger ett filter för att kvalificera **Sök vägs** parametern.</span><span class="sxs-lookup"><span data-stu-id="218b0-156">Specifies a filter to qualify the **Path** parameter.</span></span> <span data-ttu-id="218b0-157">[Fil Systems](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md) leverantören är den enda installerade PowerShell-providern som stöder filter.</span><span class="sxs-lookup"><span data-stu-id="218b0-157">The [FileSystem](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md) provider is the only installed PowerShell provider that supports filters.</span></span> <span data-ttu-id="218b0-158">Filter är mer effektiva än andra parametrar.</span><span class="sxs-lookup"><span data-stu-id="218b0-158">Filters are more efficient than other parameters.</span></span> <span data-ttu-id="218b0-159">Providern använder filter när-cmdlet: en hämtar objekten i stället för att ha PowerShell filtrera objekten när de har hämtats.</span><span class="sxs-lookup"><span data-stu-id="218b0-159">The provider applies filter when the cmdlet gets the objects rather than having PowerShell filter the objects after they're retrieved.</span></span> <span data-ttu-id="218b0-160">Filter strängen skickas till .NET-API: et för att räkna upp filer.</span><span class="sxs-lookup"><span data-stu-id="218b0-160">The filter string is passed to the .NET API to enumerate files.</span></span> <span data-ttu-id="218b0-161">API: t stöder bara `*` och `?` jokertecken.</span><span class="sxs-lookup"><span data-stu-id="218b0-161">The API only supports `*` and `?` wildcards.</span></span>

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

### <span data-ttu-id="218b0-162">-Force</span><span class="sxs-lookup"><span data-stu-id="218b0-162">-Force</span></span>

<span data-ttu-id="218b0-163">Anger att den här cmdleten hämtar objekt som inte kan nås på annat sätt, t. ex. dolda objekt.</span><span class="sxs-lookup"><span data-stu-id="218b0-163">Indicates that this cmdlet gets items that can't otherwise be accessed, such as hidden items.</span></span>
<span data-ttu-id="218b0-164">Implementeringen varierar från providern till providern.</span><span class="sxs-lookup"><span data-stu-id="218b0-164">Implementation varies from provider to provider.</span></span> <span data-ttu-id="218b0-165">Mer information finns i [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span><span class="sxs-lookup"><span data-stu-id="218b0-165">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span> <span data-ttu-id="218b0-166">Även om du använder **Force** -parametern kan inte cmdlet: en åsidosätta säkerhets begränsningar.</span><span class="sxs-lookup"><span data-stu-id="218b0-166">Even using the **Force** parameter, the cmdlet can't override security restrictions.</span></span>

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

### <span data-ttu-id="218b0-167">-Inkludera</span><span class="sxs-lookup"><span data-stu-id="218b0-167">-Include</span></span>

<span data-ttu-id="218b0-168">Anger, som en sträng mat ris, ett objekt eller objekt som denna cmdlet inkluderar i åtgärden.</span><span class="sxs-lookup"><span data-stu-id="218b0-168">Specifies, as a string array, an item or items that this cmdlet includes in the operation.</span></span> <span data-ttu-id="218b0-169">Värdet för den här parametern kvalificerar parametern **Path** .</span><span class="sxs-lookup"><span data-stu-id="218b0-169">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="218b0-170">Ange ett Sök vägs element eller ett mönster, till exempel `*.txt` .</span><span class="sxs-lookup"><span data-stu-id="218b0-170">Enter a path element or pattern, such as `*.txt`.</span></span> <span data-ttu-id="218b0-171">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="218b0-171">Wildcard characters are permitted.</span></span> <span data-ttu-id="218b0-172">Parametern **include** är endast effektiv när kommandot innehåller innehållet i ett objekt, t. ex `C:\Windows\*` ., där jokertecknet anger innehållet i `C:\Windows` katalogen.</span><span class="sxs-lookup"><span data-stu-id="218b0-172">The **Include** parameter is effective only when the command includes the contents of an item, such as `C:\Windows\*`, where the wildcard character specifies the contents of the `C:\Windows` directory.</span></span>

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

### <span data-ttu-id="218b0-173">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="218b0-173">-LiteralPath</span></span>

<span data-ttu-id="218b0-174">Anger en sökväg till en eller flera platser.</span><span class="sxs-lookup"><span data-stu-id="218b0-174">Specifies a path to one or more locations.</span></span> <span data-ttu-id="218b0-175">Värdet för **LiteralPath** används exakt som det har angetts.</span><span class="sxs-lookup"><span data-stu-id="218b0-175">The value of **LiteralPath** is used exactly as it's typed.</span></span> <span data-ttu-id="218b0-176">Inga tecken tolkas som jokertecken.</span><span class="sxs-lookup"><span data-stu-id="218b0-176">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="218b0-177">Om sökvägen innehåller escape-tecken omger du den med enkla citat tecken.</span><span class="sxs-lookup"><span data-stu-id="218b0-177">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="218b0-178">Enkla citat tecken säger att PowerShell inte tolkar några tecken som escape-sekvenser.</span><span class="sxs-lookup"><span data-stu-id="218b0-178">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

<span data-ttu-id="218b0-179">Mer information finns i [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md).</span><span class="sxs-lookup"><span data-stu-id="218b0-179">For more information, see [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md).</span></span>

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

### <span data-ttu-id="218b0-180">-Path</span><span class="sxs-lookup"><span data-stu-id="218b0-180">-Path</span></span>

<span data-ttu-id="218b0-181">Anger sökvägen till ett objekt.</span><span class="sxs-lookup"><span data-stu-id="218b0-181">Specifies the path to an item.</span></span> <span data-ttu-id="218b0-182">Denna cmdlet hämtar objektet på den angivna platsen.</span><span class="sxs-lookup"><span data-stu-id="218b0-182">This cmdlet gets the item at the specified location.</span></span> <span data-ttu-id="218b0-183">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="218b0-183">Wildcard characters are permitted.</span></span> <span data-ttu-id="218b0-184">Den här parametern är obligatorisk, men parameterns namn **Sök väg** är valfri.</span><span class="sxs-lookup"><span data-stu-id="218b0-184">This parameter is required, but the parameter name **Path** is optional.</span></span>

<span data-ttu-id="218b0-185">`.`Ange den aktuella platsen genom att använda en punkt ().</span><span class="sxs-lookup"><span data-stu-id="218b0-185">Use a dot (`.`) to specify the current location.</span></span> <span data-ttu-id="218b0-186">Använd jokertecknet ( `*` ) för att ange alla objekt på den aktuella platsen.</span><span class="sxs-lookup"><span data-stu-id="218b0-186">Use the wildcard character (`*`) to specify all the items in the current location.</span></span>

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

### <span data-ttu-id="218b0-187">– UseTransaction</span><span class="sxs-lookup"><span data-stu-id="218b0-187">-UseTransaction</span></span>

<span data-ttu-id="218b0-188">Inkluderar kommandot i den aktiva transaktionen.</span><span class="sxs-lookup"><span data-stu-id="218b0-188">Includes the command in the active transaction.</span></span>
<span data-ttu-id="218b0-189">Den här parametern är bara giltig medan en transaktion pågår.</span><span class="sxs-lookup"><span data-stu-id="218b0-189">This parameter is valid only when a transaction is in progress.</span></span>
<span data-ttu-id="218b0-190">Mer information finns i [about_Transactions](../Microsoft.PowerShell.Core/About/about_Transactions.md).</span><span class="sxs-lookup"><span data-stu-id="218b0-190">For more information, see [about_Transactions](../Microsoft.PowerShell.Core/About/about_Transactions.md).</span></span>

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

### <span data-ttu-id="218b0-191">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="218b0-191">CommonParameters</span></span>

<span data-ttu-id="218b0-192">Denna cmdlet stöder de gemensamma parametrarna:,,,,,,,, `-Debug` `-ErrorAction` `-ErrorVariable` `-InformationAction` `-InformationVariable` `-OutVariable` `-OutBuffer` `-PipelineVariable` `-Verbose` `-WarningAction` , och `-WarningVariable` .</span><span class="sxs-lookup"><span data-stu-id="218b0-192">This cmdlet supports the common parameters: `-Debug`, `-ErrorAction`, `-ErrorVariable`, `-InformationAction`, `-InformationVariable`, `-OutVariable`, `-OutBuffer`, `-PipelineVariable`, `-Verbose`, `-WarningAction`, and `-WarningVariable`.</span></span> <span data-ttu-id="218b0-193">Mer information finns i [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span><span class="sxs-lookup"><span data-stu-id="218b0-193">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="218b0-194">INDATA</span><span class="sxs-lookup"><span data-stu-id="218b0-194">INPUTS</span></span>

### <span data-ttu-id="218b0-195">System. String</span><span class="sxs-lookup"><span data-stu-id="218b0-195">System.String</span></span>

<span data-ttu-id="218b0-196">Du kan skicka vidare en sträng som innehåller en sökväg till denna cmdlet.</span><span class="sxs-lookup"><span data-stu-id="218b0-196">You can pipe a string that contains a path to this cmdlet.</span></span>

## <span data-ttu-id="218b0-197">UTDATA</span><span class="sxs-lookup"><span data-stu-id="218b0-197">OUTPUTS</span></span>

### <span data-ttu-id="218b0-198">System. Object</span><span class="sxs-lookup"><span data-stu-id="218b0-198">System.Object</span></span>

<span data-ttu-id="218b0-199">Denna cmdlet returnerar de objekt som den hämtar.</span><span class="sxs-lookup"><span data-stu-id="218b0-199">This cmdlet returns the objects that it gets.</span></span> <span data-ttu-id="218b0-200">Typen bestäms av typen av objekt i sökvägen.</span><span class="sxs-lookup"><span data-stu-id="218b0-200">The type is determined by the type of objects in the path.</span></span>

## <span data-ttu-id="218b0-201">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="218b0-201">NOTES</span></span>

<span data-ttu-id="218b0-202">Denna cmdlet har ingen **rekursivt** -parameter, eftersom den bara får ett objekt, inte dess innehåll.</span><span class="sxs-lookup"><span data-stu-id="218b0-202">This cmdlet does not have a **Recurse** parameter, because it gets only an item, not its contents.</span></span>
<span data-ttu-id="218b0-203">Använd om du vill hämta innehållet i ett objekt rekursivt `Get-ChildItem` .</span><span class="sxs-lookup"><span data-stu-id="218b0-203">To get the contents of an item recursively, use `Get-ChildItem`.</span></span>

<span data-ttu-id="218b0-204">Använd denna cmdlet för att hämta register nycklar och `Get-ItemProperty` för att hämta register värden och data för att navigera i registret.</span><span class="sxs-lookup"><span data-stu-id="218b0-204">To navigate through the registry, use this cmdlet to get registry keys and the `Get-ItemProperty` to get registry values and data.</span></span> <span data-ttu-id="218b0-205">Register värden anses vara egenskaper för register nyckeln.</span><span class="sxs-lookup"><span data-stu-id="218b0-205">The registry values are considered to be properties of the registry key.</span></span>

<span data-ttu-id="218b0-206">Denna cmdlet är utformad för att fungera med data som exponeras av vilken provider som helst.</span><span class="sxs-lookup"><span data-stu-id="218b0-206">This cmdlet is designed to work with the data exposed by any provider.</span></span> <span data-ttu-id="218b0-207">Om du vill visa en lista över tillgängliga providers i din session skriver du `Get-PsProvider` .</span><span class="sxs-lookup"><span data-stu-id="218b0-207">To list the providers available in your session, type `Get-PsProvider`.</span></span> <span data-ttu-id="218b0-208">Mer information finns i [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span><span class="sxs-lookup"><span data-stu-id="218b0-208">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

## <span data-ttu-id="218b0-209">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="218b0-209">RELATED LINKS</span></span>

[<span data-ttu-id="218b0-210">Rensa objekt</span><span class="sxs-lookup"><span data-stu-id="218b0-210">Clear-Item</span></span>](Clear-Item.md)

[<span data-ttu-id="218b0-211">Kopiera objekt</span><span class="sxs-lookup"><span data-stu-id="218b0-211">Copy-Item</span></span>](Copy-Item.md)

[<span data-ttu-id="218b0-212">Anropa-objekt</span><span class="sxs-lookup"><span data-stu-id="218b0-212">Invoke-Item</span></span>](Invoke-Item.md)

[<span data-ttu-id="218b0-213">Flytta objekt</span><span class="sxs-lookup"><span data-stu-id="218b0-213">Move-Item</span></span>](Move-Item.md)

[<span data-ttu-id="218b0-214">Nytt objekt</span><span class="sxs-lookup"><span data-stu-id="218b0-214">New-Item</span></span>](New-Item.md)

[<span data-ttu-id="218b0-215">Ta bort objekt</span><span class="sxs-lookup"><span data-stu-id="218b0-215">Remove-Item</span></span>](Remove-Item.md)

[<span data-ttu-id="218b0-216">Byt namn – objekt</span><span class="sxs-lookup"><span data-stu-id="218b0-216">Rename-Item</span></span>](Rename-Item.md)

[<span data-ttu-id="218b0-217">Ange objekt</span><span class="sxs-lookup"><span data-stu-id="218b0-217">Set-Item</span></span>](Set-Item.md)

[<span data-ttu-id="218b0-218">Get-ChildItem</span><span class="sxs-lookup"><span data-stu-id="218b0-218">Get-ChildItem</span></span>](Get-ChildItem.md)

[<span data-ttu-id="218b0-219">Get-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="218b0-219">Get-ItemProperty</span></span>](Get-ItemProperty.md)

[<span data-ttu-id="218b0-220">Get-PSProvider</span><span class="sxs-lookup"><span data-stu-id="218b0-220">Get-PSProvider</span></span>](Get-PSProvider.md)

[<span data-ttu-id="218b0-221">about_Providers</span><span class="sxs-lookup"><span data-stu-id="218b0-221">about_Providers</span></span>](../Microsoft.PowerShell.Core/About/about_Providers.md)
