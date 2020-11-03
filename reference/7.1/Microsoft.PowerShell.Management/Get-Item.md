---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 03/27/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/get-item?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Item
ms.openlocfilehash: 25d07028430d6ad6719136bd484d39e116d81516
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93266901"
---
# <span data-ttu-id="1307a-103">Get-Item</span><span class="sxs-lookup"><span data-stu-id="1307a-103">Get-Item</span></span>

## <span data-ttu-id="1307a-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="1307a-104">SYNOPSIS</span></span>
<span data-ttu-id="1307a-105">Hämtar objektet på den angivna platsen.</span><span class="sxs-lookup"><span data-stu-id="1307a-105">Gets the item at the specified location.</span></span>

## <span data-ttu-id="1307a-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="1307a-106">SYNTAX</span></span>

### <span data-ttu-id="1307a-107">Sökväg (standard)</span><span class="sxs-lookup"><span data-stu-id="1307a-107">Path (Default)</span></span>

```
Get-Item [-Path] <String[]> [-Filter <String>] [-Include <String[]>] [-Exclude <String[]>] [-Force]
 [-Credential <PSCredential>] [-Stream <String[]>] [<CommonParameters>]
```

### <span data-ttu-id="1307a-108">LiteralPath</span><span class="sxs-lookup"><span data-stu-id="1307a-108">LiteralPath</span></span>

```
Get-Item -LiteralPath <String[]> [-Filter <String>] [-Include <String[]>] [-Exclude <String[]>]
 [-Force] [-Credential <PSCredential>] [-Stream <String[]>] [<CommonParameters>]
```

## <span data-ttu-id="1307a-109">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="1307a-109">DESCRIPTION</span></span>

<span data-ttu-id="1307a-110">`Get-Item`Cmdlet: en hämtar objektet på den angivna platsen.</span><span class="sxs-lookup"><span data-stu-id="1307a-110">The `Get-Item` cmdlet gets the item at the specified location.</span></span> <span data-ttu-id="1307a-111">Det får inte innehållet i objektet på platsen om du inte använder ett jokertecken ( `*` ) för att begära allt innehåll i objektet.</span><span class="sxs-lookup"><span data-stu-id="1307a-111">It doesn't get the contents of the item at the location unless you use a wildcard character (`*`) to request all the contents of the item.</span></span>

<span data-ttu-id="1307a-112">Denna cmdlet används av PowerShell-leverantörer för att navigera mellan olika typer av data lager.</span><span class="sxs-lookup"><span data-stu-id="1307a-112">This cmdlet is used by PowerShell providers to navigate through different types of data stores.</span></span>

## <span data-ttu-id="1307a-113">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="1307a-113">EXAMPLES</span></span>

### <span data-ttu-id="1307a-114">Exempel 1: hämta den aktuella katalogen</span><span class="sxs-lookup"><span data-stu-id="1307a-114">Example 1: Get the current directory</span></span>

<span data-ttu-id="1307a-115">Det här exemplet hämtar den aktuella katalogen.</span><span class="sxs-lookup"><span data-stu-id="1307a-115">This example gets the current directory.</span></span> <span data-ttu-id="1307a-116">Punkten ('. ') representerar objektet på den aktuella platsen (inte dess innehåll).</span><span class="sxs-lookup"><span data-stu-id="1307a-116">The dot ('.') represents the item at the current location (not its contents).</span></span>

```powershell
Get-Item .
```

```output
Directory: C:\

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
d----         7/26/2006  10:01 AM            ps-test
```

### <span data-ttu-id="1307a-117">Exempel 2: Hämta alla objekt i den aktuella katalogen</span><span class="sxs-lookup"><span data-stu-id="1307a-117">Example 2: Get all the items in the current directory</span></span>

<span data-ttu-id="1307a-118">Det här exemplet hämtar alla objekt i den aktuella katalogen.</span><span class="sxs-lookup"><span data-stu-id="1307a-118">This example gets all the items in the current directory.</span></span> <span data-ttu-id="1307a-119">Jokertecknet ( `*` ) representerar allt innehåll i det aktuella objektet.</span><span class="sxs-lookup"><span data-stu-id="1307a-119">The wildcard character (`*`) represents all the contents of the current item.</span></span>

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

### <span data-ttu-id="1307a-120">Exempel 3: hämta den aktuella katalogen för en enhet</span><span class="sxs-lookup"><span data-stu-id="1307a-120">Example 3: Get the current directory of a drive</span></span>

<span data-ttu-id="1307a-121">Det här exemplet hämtar enhetens aktuella katalog `C:` .</span><span class="sxs-lookup"><span data-stu-id="1307a-121">This example gets the current directory of the `C:` drive.</span></span> <span data-ttu-id="1307a-122">Objektet som hämtas representerar bara katalogen, inte dess innehåll.</span><span class="sxs-lookup"><span data-stu-id="1307a-122">The object that is retrieved represents only the directory, not its contents.</span></span>

```powershell
Get-Item C:\
```

### <span data-ttu-id="1307a-123">Exempel 4: Hämta objekt på den angivna enheten</span><span class="sxs-lookup"><span data-stu-id="1307a-123">Example 4: Get items in the specified drive</span></span>

<span data-ttu-id="1307a-124">I det här exemplet hämtas objekt i `C:` enheten.</span><span class="sxs-lookup"><span data-stu-id="1307a-124">This example gets the items in the `C:` drive.</span></span> <span data-ttu-id="1307a-125">Jokertecknet ( `*` ) representerar alla objekt i behållaren, inte bara behållaren.</span><span class="sxs-lookup"><span data-stu-id="1307a-125">The wildcard character (`*`) represents all the items in the container, not just the container.</span></span>

```powershell
Get-Item C:\*
```

<span data-ttu-id="1307a-126">I PowerShell använder du en enda asterisk ( `*` ) för att hämta innehåll i stället för den traditionella `*.*` .</span><span class="sxs-lookup"><span data-stu-id="1307a-126">In PowerShell, use a single asterisk (`*`) to get contents, instead of the traditional `*.*`.</span></span> <span data-ttu-id="1307a-127">Formatet tolkas bokstavligen, så `*.*` skulle inte hämta kataloger eller fil namn utan punkt.</span><span class="sxs-lookup"><span data-stu-id="1307a-127">The format is interpreted literally, so `*.*` wouldn't retrieve directories or filenames without a dot.</span></span>

### <span data-ttu-id="1307a-128">Exempel 5: Hämta en egenskap i den angivna katalogen</span><span class="sxs-lookup"><span data-stu-id="1307a-128">Example 5: Get a property in the specified directory</span></span>

<span data-ttu-id="1307a-129">Det här exemplet hämtar katalogens **LastAccessTime** -egenskap `C:\Windows` .</span><span class="sxs-lookup"><span data-stu-id="1307a-129">This example gets the **LastAccessTime** property of the `C:\Windows` directory.</span></span> <span data-ttu-id="1307a-130">**LastAccessTime** är bara en egenskap för fil system kataloger.</span><span class="sxs-lookup"><span data-stu-id="1307a-130">**LastAccessTime** is just one property of file system directories.</span></span> <span data-ttu-id="1307a-131">Om du vill se alla egenskaper för en katalog skriver du `(Get-Item <directory-name>) | Get-Member` .</span><span class="sxs-lookup"><span data-stu-id="1307a-131">To see all the properties of a directory, type `(Get-Item <directory-name>) | Get-Member`.</span></span>

```powershell
(Get-Item C:\Windows).LastAccessTime
```

### <span data-ttu-id="1307a-132">Exempel 6: Visa innehållet i en register nyckel</span><span class="sxs-lookup"><span data-stu-id="1307a-132">Example 6: Show the contents of a registry key</span></span>

<span data-ttu-id="1307a-133">Det här exemplet visar innehållet i register nyckeln **Microsoft. PowerShell** .</span><span class="sxs-lookup"><span data-stu-id="1307a-133">This example shows the contents of the **Microsoft.PowerShell** registry key.</span></span> <span data-ttu-id="1307a-134">Du kan använda den här cmdleten med PowerShell-registerposten för att hämta register nycklar och under nycklar, men du måste använda cmdlet: en `Get-ItemProperty` för att hämta register värden och data.</span><span class="sxs-lookup"><span data-stu-id="1307a-134">You can use this cmdlet with the PowerShell Registry provider to get registry keys and subkeys, but you must use the `Get-ItemProperty` cmdlet to get the registry values and data.</span></span>

```powershell
Get-Item HKLM:\Software\Microsoft\Powershell\1\Shellids\Microsoft.Powershell\
```

### <span data-ttu-id="1307a-135">Exempel 7: Hämta objekt i en katalog som har ett undantag</span><span class="sxs-lookup"><span data-stu-id="1307a-135">Example 7: Get items in a directory that have an exclusion</span></span>

<span data-ttu-id="1307a-136">Det här exemplet hämtar objekt i Windows-katalogen med namn som innehåller en punkt ( `.` ), men börjar inte med `w*` . Det här exemplet fungerar bara om sökvägen innehåller ett jokertecken ( `*` ) för att ange innehållet i objektet.</span><span class="sxs-lookup"><span data-stu-id="1307a-136">This example gets items in the Windows directory with names that include a dot (`.`), but don't begin with `w*`.This example works only when the path includes a wildcard character (`*`) to specify the contents of the item.</span></span>

```powershell
Get-Item C:\Windows\*.* -Exclude "w*"
```

### <span data-ttu-id="1307a-137">Exempel 8: Hämta hardlink-information</span><span class="sxs-lookup"><span data-stu-id="1307a-137">Example 8: Getting hardlink information</span></span>

<span data-ttu-id="1307a-138">I PowerShell 6,2 lades en alternativ vy till för att hämta hardlink-information.</span><span class="sxs-lookup"><span data-stu-id="1307a-138">In PowerShell 6.2, an alternate view was added to get hardlink information.</span></span> <span data-ttu-id="1307a-139">För att få information om hardlink, skicka in utdata till `Format-Table -View childrenWithHardlink`</span><span class="sxs-lookup"><span data-stu-id="1307a-139">To get the hardlink information, pipe the output to `Format-Table -View childrenWithHardlink`</span></span>

```powershell
Get-Item -Path C:\PathWhichIsAHardLink | Format-Table -View childrenWithHardlink
```

### <span data-ttu-id="1307a-140">Exempel 9: utdata för experimentell funktion PSUnixFileStat</span><span class="sxs-lookup"><span data-stu-id="1307a-140">Example 9: Output for experimental feature PSUnixFileStat</span></span>

<span data-ttu-id="1307a-141">I PowerShell 7 på UNIX-system tillhandahåller experimentella funktions **PSUnixFileStat** UNIX-liknande utdata:</span><span class="sxs-lookup"><span data-stu-id="1307a-141">In PowerShell 7 on Unix systems, the experimental feature **PSUnixFileStat** provides Unix-like output:</span></span>

```powershell
PS> Get-Item /Users
```

```Output
    Directory: /

UnixMode    User  Group   LastWriteTime      Size  Name
--------    ----  -----   -------------      ----  ----
drwxr-xr-x  root  admin   12/20/2019 11:46   192   Users
```

<span data-ttu-id="1307a-142">De nya egenskaperna som nu är en del av utdata är:</span><span class="sxs-lookup"><span data-stu-id="1307a-142">The new properties that are now part of the output are:</span></span>

- <span data-ttu-id="1307a-143">**UnixMode** är de fil behörigheter som representeras i ett UNIX-system</span><span class="sxs-lookup"><span data-stu-id="1307a-143">**UnixMode** is the file permissions as represented on a Unix system</span></span>
- <span data-ttu-id="1307a-144">**Användaren** är filens ägare</span><span class="sxs-lookup"><span data-stu-id="1307a-144">**User** is the file owner</span></span>
- <span data-ttu-id="1307a-145">**Grupp** är grupp ägare</span><span class="sxs-lookup"><span data-stu-id="1307a-145">**Group** is the group owner</span></span>
- <span data-ttu-id="1307a-146">**Storlek** är storleken på filen eller katalogen som representeras på ett UNIX-system</span><span class="sxs-lookup"><span data-stu-id="1307a-146">**Size** is the size of the file or directory as represented on a Unix system</span></span>

## <span data-ttu-id="1307a-147">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="1307a-147">PARAMETERS</span></span>

### <span data-ttu-id="1307a-148">-Stream</span><span class="sxs-lookup"><span data-stu-id="1307a-148">-Stream</span></span>

<span data-ttu-id="1307a-149">Hämtar den angivna alternativa NTFS-filströmmen från filen.</span><span class="sxs-lookup"><span data-stu-id="1307a-149">Gets the specified alternate NTFS file stream from the file.</span></span> <span data-ttu-id="1307a-150">Ange data ström namnet.</span><span class="sxs-lookup"><span data-stu-id="1307a-150">Enter the stream name.</span></span> <span data-ttu-id="1307a-151">Jokertecken stöds.</span><span class="sxs-lookup"><span data-stu-id="1307a-151">Wildcards are supported.</span></span> <span data-ttu-id="1307a-152">Använd en asterisk () om du vill hämta alla strömmar `*` .</span><span class="sxs-lookup"><span data-stu-id="1307a-152">To get all streams, use an asterisk (`*`).</span></span> <span data-ttu-id="1307a-153">Den här parametern är inte giltig i mapparna.</span><span class="sxs-lookup"><span data-stu-id="1307a-153">This parameter isn't valid on folders.</span></span>

<span data-ttu-id="1307a-154">**Stream** är en dynamisk parameter som **fil Systems** leverantören lägger till i `Get-Item` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="1307a-154">**Stream** is a dynamic parameter that the **FileSystem** provider adds to the `Get-Item` cmdlet.</span></span>
<span data-ttu-id="1307a-155">Den här parametern fungerar bara i fil system enheter.</span><span class="sxs-lookup"><span data-stu-id="1307a-155">This parameter works only in file system drives.</span></span>

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

### <span data-ttu-id="1307a-156">-Credential</span><span class="sxs-lookup"><span data-stu-id="1307a-156">-Credential</span></span>

> [!NOTE]
> <span data-ttu-id="1307a-157">Den här parametern stöds inte av några providrar som installeras med PowerShell.</span><span class="sxs-lookup"><span data-stu-id="1307a-157">This parameter isn't supported by any providers installed with PowerShell.</span></span>
> <span data-ttu-id="1307a-158">Om du vill personifiera en annan användare eller öka dina autentiseringsuppgifter när du kör denna cmdlet, använder du [Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md).</span><span class="sxs-lookup"><span data-stu-id="1307a-158">To impersonate another user, or elevate your credentials when running this cmdlet, use [Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md).</span></span>

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

### <span data-ttu-id="1307a-159">-Undanta</span><span class="sxs-lookup"><span data-stu-id="1307a-159">-Exclude</span></span>

<span data-ttu-id="1307a-160">Anger, som en sträng mat ris, ett objekt eller objekt som denna cmdlet exkluderar i åtgärden.</span><span class="sxs-lookup"><span data-stu-id="1307a-160">Specifies, as a string array, an item or items that this cmdlet excludes in the operation.</span></span> <span data-ttu-id="1307a-161">Värdet för den här parametern kvalificerar parametern **Path** .</span><span class="sxs-lookup"><span data-stu-id="1307a-161">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="1307a-162">Ange ett Sök vägs element eller ett mönster, till exempel `*.txt` .</span><span class="sxs-lookup"><span data-stu-id="1307a-162">Enter a path element or pattern, such as `*.txt`.</span></span> <span data-ttu-id="1307a-163">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="1307a-163">Wildcard characters are permitted.</span></span> <span data-ttu-id="1307a-164">Parametern **exclude** är endast effektiv när kommandot innehåller innehållet i ett objekt, t. ex `C:\Windows\*` ., där jokertecknet anger innehållet i `C:\Windows` katalogen.</span><span class="sxs-lookup"><span data-stu-id="1307a-164">The **Exclude** parameter is effective only when the command includes the contents of an item, such as `C:\Windows\*`, where the wildcard character specifies the contents of the `C:\Windows` directory.</span></span>

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

### <span data-ttu-id="1307a-165">-Filter</span><span class="sxs-lookup"><span data-stu-id="1307a-165">-Filter</span></span>

<span data-ttu-id="1307a-166">Anger ett filter för att kvalificera **Sök vägs** parametern.</span><span class="sxs-lookup"><span data-stu-id="1307a-166">Specifies a filter to qualify the **Path** parameter.</span></span> <span data-ttu-id="1307a-167">[Fil Systems](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md) leverantören är den enda installerade PowerShell-providern som stöder filter.</span><span class="sxs-lookup"><span data-stu-id="1307a-167">The [FileSystem](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md) provider is the only installed PowerShell provider that supports filters.</span></span> <span data-ttu-id="1307a-168">Filter är mer effektiva än andra parametrar.</span><span class="sxs-lookup"><span data-stu-id="1307a-168">Filters are more efficient than other parameters.</span></span> <span data-ttu-id="1307a-169">Providern använder filter när-cmdlet: en hämtar objekten i stället för att ha PowerShell filtrera objekten när de har hämtats.</span><span class="sxs-lookup"><span data-stu-id="1307a-169">The provider applies filter when the cmdlet gets the objects rather than having PowerShell filter the objects after they're retrieved.</span></span> <span data-ttu-id="1307a-170">Filter strängen skickas till .NET-API: et för att räkna upp filer.</span><span class="sxs-lookup"><span data-stu-id="1307a-170">The filter string is passed to the .NET API to enumerate files.</span></span> <span data-ttu-id="1307a-171">API: t stöder bara `*` och `?` jokertecken.</span><span class="sxs-lookup"><span data-stu-id="1307a-171">The API only supports `*` and `?` wildcards.</span></span>

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

### <span data-ttu-id="1307a-172">-Force</span><span class="sxs-lookup"><span data-stu-id="1307a-172">-Force</span></span>

<span data-ttu-id="1307a-173">Anger att den här cmdleten hämtar objekt som inte kan nås på annat sätt, t. ex. dolda objekt.</span><span class="sxs-lookup"><span data-stu-id="1307a-173">Indicates that this cmdlet gets items that can't otherwise be accessed, such as hidden items.</span></span>
<span data-ttu-id="1307a-174">Implementeringen varierar från providern till providern.</span><span class="sxs-lookup"><span data-stu-id="1307a-174">Implementation varies from provider to provider.</span></span> <span data-ttu-id="1307a-175">Mer information finns i [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span><span class="sxs-lookup"><span data-stu-id="1307a-175">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span> <span data-ttu-id="1307a-176">Även om du använder **Force** -parametern kan inte cmdlet: en åsidosätta säkerhets begränsningar.</span><span class="sxs-lookup"><span data-stu-id="1307a-176">Even using the **Force** parameter, the cmdlet can't override security restrictions.</span></span>

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

### <span data-ttu-id="1307a-177">-Inkludera</span><span class="sxs-lookup"><span data-stu-id="1307a-177">-Include</span></span>

<span data-ttu-id="1307a-178">Anger, som en sträng mat ris, ett objekt eller objekt som denna cmdlet inkluderar i åtgärden.</span><span class="sxs-lookup"><span data-stu-id="1307a-178">Specifies, as a string array, an item or items that this cmdlet includes in the operation.</span></span> <span data-ttu-id="1307a-179">Värdet för den här parametern kvalificerar parametern **Path** .</span><span class="sxs-lookup"><span data-stu-id="1307a-179">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="1307a-180">Ange ett Sök vägs element eller ett mönster, till exempel `*.txt` .</span><span class="sxs-lookup"><span data-stu-id="1307a-180">Enter a path element or pattern, such as `*.txt`.</span></span> <span data-ttu-id="1307a-181">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="1307a-181">Wildcard characters are permitted.</span></span> <span data-ttu-id="1307a-182">Parametern **include** är endast effektiv när kommandot innehåller innehållet i ett objekt, t. ex `C:\Windows\*` ., där jokertecknet anger innehållet i `C:\Windows` katalogen.</span><span class="sxs-lookup"><span data-stu-id="1307a-182">The **Include** parameter is effective only when the command includes the contents of an item, such as `C:\Windows\*`, where the wildcard character specifies the contents of the `C:\Windows` directory.</span></span>

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

### <span data-ttu-id="1307a-183">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="1307a-183">-LiteralPath</span></span>

<span data-ttu-id="1307a-184">Anger en sökväg till en eller flera platser.</span><span class="sxs-lookup"><span data-stu-id="1307a-184">Specifies a path to one or more locations.</span></span> <span data-ttu-id="1307a-185">Värdet för **LiteralPath** används exakt som det har angetts.</span><span class="sxs-lookup"><span data-stu-id="1307a-185">The value of **LiteralPath** is used exactly as it's typed.</span></span> <span data-ttu-id="1307a-186">Inga tecken tolkas som jokertecken.</span><span class="sxs-lookup"><span data-stu-id="1307a-186">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="1307a-187">Om sökvägen innehåller escape-tecken omger du den med enkla citat tecken.</span><span class="sxs-lookup"><span data-stu-id="1307a-187">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="1307a-188">Enkla citat tecken säger att PowerShell inte tolkar några tecken som escape-sekvenser.</span><span class="sxs-lookup"><span data-stu-id="1307a-188">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

<span data-ttu-id="1307a-189">Mer information finns i [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md).</span><span class="sxs-lookup"><span data-stu-id="1307a-189">For more information, see [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md).</span></span>

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

### <span data-ttu-id="1307a-190">-Path</span><span class="sxs-lookup"><span data-stu-id="1307a-190">-Path</span></span>

<span data-ttu-id="1307a-191">Anger sökvägen till ett objekt.</span><span class="sxs-lookup"><span data-stu-id="1307a-191">Specifies the path to an item.</span></span> <span data-ttu-id="1307a-192">Denna cmdlet hämtar objektet på den angivna platsen.</span><span class="sxs-lookup"><span data-stu-id="1307a-192">This cmdlet gets the item at the specified location.</span></span> <span data-ttu-id="1307a-193">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="1307a-193">Wildcard characters are permitted.</span></span> <span data-ttu-id="1307a-194">Den här parametern är obligatorisk, men parameterns namn **Sök väg** är valfri.</span><span class="sxs-lookup"><span data-stu-id="1307a-194">This parameter is required, but the parameter name **Path** is optional.</span></span>

<span data-ttu-id="1307a-195">`.`Ange den aktuella platsen genom att använda en punkt ().</span><span class="sxs-lookup"><span data-stu-id="1307a-195">Use a dot (`.`) to specify the current location.</span></span> <span data-ttu-id="1307a-196">Använd jokertecknet ( `*` ) för att ange alla objekt på den aktuella platsen.</span><span class="sxs-lookup"><span data-stu-id="1307a-196">Use the wildcard character (`*`) to specify all the items in the current location.</span></span>

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

### <span data-ttu-id="1307a-197">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="1307a-197">CommonParameters</span></span>

<span data-ttu-id="1307a-198">Denna cmdlet stöder de gemensamma parametrarna:,,,,,,,, `-Debug` `-ErrorAction` `-ErrorVariable` `-InformationAction` `-InformationVariable` `-OutVariable` `-OutBuffer` `-PipelineVariable` `-Verbose` `-WarningAction` , och `-WarningVariable` .</span><span class="sxs-lookup"><span data-stu-id="1307a-198">This cmdlet supports the common parameters: `-Debug`, `-ErrorAction`, `-ErrorVariable`, `-InformationAction`, `-InformationVariable`, `-OutVariable`, `-OutBuffer`, `-PipelineVariable`, `-Verbose`, `-WarningAction`, and `-WarningVariable`.</span></span> <span data-ttu-id="1307a-199">Mer information finns i [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span><span class="sxs-lookup"><span data-stu-id="1307a-199">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="1307a-200">INDATA</span><span class="sxs-lookup"><span data-stu-id="1307a-200">INPUTS</span></span>

### <span data-ttu-id="1307a-201">System. String</span><span class="sxs-lookup"><span data-stu-id="1307a-201">System.String</span></span>

<span data-ttu-id="1307a-202">Du kan skicka vidare en sträng som innehåller en sökväg till denna cmdlet.</span><span class="sxs-lookup"><span data-stu-id="1307a-202">You can pipe a string that contains a path to this cmdlet.</span></span>

## <span data-ttu-id="1307a-203">UTDATA</span><span class="sxs-lookup"><span data-stu-id="1307a-203">OUTPUTS</span></span>

### <span data-ttu-id="1307a-204">System. Object</span><span class="sxs-lookup"><span data-stu-id="1307a-204">System.Object</span></span>

<span data-ttu-id="1307a-205">Denna cmdlet returnerar de objekt som den hämtar.</span><span class="sxs-lookup"><span data-stu-id="1307a-205">This cmdlet returns the objects that it gets.</span></span> <span data-ttu-id="1307a-206">Typen bestäms av typen av objekt i sökvägen.</span><span class="sxs-lookup"><span data-stu-id="1307a-206">The type is determined by the type of objects in the path.</span></span>

## <span data-ttu-id="1307a-207">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="1307a-207">NOTES</span></span>

<span data-ttu-id="1307a-208">Denna cmdlet har ingen **rekursivt** -parameter, eftersom den bara får ett objekt, inte dess innehåll.</span><span class="sxs-lookup"><span data-stu-id="1307a-208">This cmdlet does not have a **Recurse** parameter, because it gets only an item, not its contents.</span></span>
<span data-ttu-id="1307a-209">Använd om du vill hämta innehållet i ett objekt rekursivt `Get-ChildItem` .</span><span class="sxs-lookup"><span data-stu-id="1307a-209">To get the contents of an item recursively, use `Get-ChildItem`.</span></span>

<span data-ttu-id="1307a-210">Använd denna cmdlet för att hämta register nycklar och `Get-ItemProperty` för att hämta register värden och data för att navigera i registret.</span><span class="sxs-lookup"><span data-stu-id="1307a-210">To navigate through the registry, use this cmdlet to get registry keys and the `Get-ItemProperty` to get registry values and data.</span></span> <span data-ttu-id="1307a-211">Register värden anses vara egenskaper för register nyckeln.</span><span class="sxs-lookup"><span data-stu-id="1307a-211">The registry values are considered to be properties of the registry key.</span></span>
  
<span data-ttu-id="1307a-212">Denna cmdlet är utformad för att fungera med data som exponeras av vilken provider som helst.</span><span class="sxs-lookup"><span data-stu-id="1307a-212">This cmdlet is designed to work with the data exposed by any provider.</span></span> <span data-ttu-id="1307a-213">Om du vill visa en lista över tillgängliga providers i din session skriver du `Get-PsProvider` .</span><span class="sxs-lookup"><span data-stu-id="1307a-213">To list the providers available in your session, type `Get-PsProvider`.</span></span> <span data-ttu-id="1307a-214">Mer information finns i [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span><span class="sxs-lookup"><span data-stu-id="1307a-214">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

## <span data-ttu-id="1307a-215">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="1307a-215">RELATED LINKS</span></span>

[<span data-ttu-id="1307a-216">Rensa objekt</span><span class="sxs-lookup"><span data-stu-id="1307a-216">Clear-Item</span></span>](Clear-Item.md)

[<span data-ttu-id="1307a-217">Kopiera objekt</span><span class="sxs-lookup"><span data-stu-id="1307a-217">Copy-Item</span></span>](Copy-Item.md)

[<span data-ttu-id="1307a-218">Anropa-objekt</span><span class="sxs-lookup"><span data-stu-id="1307a-218">Invoke-Item</span></span>](Invoke-Item.md)

[<span data-ttu-id="1307a-219">Flytta objekt</span><span class="sxs-lookup"><span data-stu-id="1307a-219">Move-Item</span></span>](Move-Item.md)

[<span data-ttu-id="1307a-220">Nytt objekt</span><span class="sxs-lookup"><span data-stu-id="1307a-220">New-Item</span></span>](New-Item.md)

[<span data-ttu-id="1307a-221">Ta bort objekt</span><span class="sxs-lookup"><span data-stu-id="1307a-221">Remove-Item</span></span>](Remove-Item.md)

[<span data-ttu-id="1307a-222">Byt namn – objekt</span><span class="sxs-lookup"><span data-stu-id="1307a-222">Rename-Item</span></span>](Rename-Item.md)

[<span data-ttu-id="1307a-223">Ange objekt</span><span class="sxs-lookup"><span data-stu-id="1307a-223">Set-Item</span></span>](Set-Item.md)

[<span data-ttu-id="1307a-224">Get-ChildItem</span><span class="sxs-lookup"><span data-stu-id="1307a-224">Get-ChildItem</span></span>](Get-ChildItem.md)

[<span data-ttu-id="1307a-225">Get-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="1307a-225">Get-ItemProperty</span></span>](Get-ItemProperty.md)

[<span data-ttu-id="1307a-226">Get-PSProvider</span><span class="sxs-lookup"><span data-stu-id="1307a-226">Get-PSProvider</span></span>](Get-PSProvider.md)

[<span data-ttu-id="1307a-227">about_Providers</span><span class="sxs-lookup"><span data-stu-id="1307a-227">about_Providers</span></span>](../Microsoft.PowerShell.Core/About/about_Providers.md)

