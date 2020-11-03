---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 10/18/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/get-itemproperty?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-ItemProperty
ms.openlocfilehash: b2c5b8596da085fab3af7a1545569dd65931a5f7
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93266126"
---
# <span data-ttu-id="64fd9-103">Get-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="64fd9-103">Get-ItemProperty</span></span>

## <span data-ttu-id="64fd9-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="64fd9-104">SYNOPSIS</span></span>
<span data-ttu-id="64fd9-105">Hämtar egenskaperna för ett angivet objekt.</span><span class="sxs-lookup"><span data-stu-id="64fd9-105">Gets the properties of a specified item.</span></span>

## <span data-ttu-id="64fd9-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="64fd9-106">SYNTAX</span></span>

### <span data-ttu-id="64fd9-107">Sökväg (standard)</span><span class="sxs-lookup"><span data-stu-id="64fd9-107">Path (Default)</span></span>

```
Get-ItemProperty [-Path] <String[]> [[-Name] <String[]>] [-Filter <String>] [-Include <String[]>]
 [-Exclude <String[]>] [-Credential <PSCredential>] [-UseTransaction] [<CommonParameters>]
```

### <span data-ttu-id="64fd9-108">LiteralPath</span><span class="sxs-lookup"><span data-stu-id="64fd9-108">LiteralPath</span></span>

```
Get-ItemProperty -LiteralPath <String[]> [[-Name] <String[]>] [-Filter <String>] [-Include <String[]>]
 [-Exclude <String[]>] [-Credential <PSCredential>] [-UseTransaction] [<CommonParameters>]
```

## <span data-ttu-id="64fd9-109">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="64fd9-109">DESCRIPTION</span></span>

<span data-ttu-id="64fd9-110">`Get-ItemProperty`Cmdlet: en hämtar egenskaperna för de angivna objekten.</span><span class="sxs-lookup"><span data-stu-id="64fd9-110">The `Get-ItemProperty` cmdlet gets the properties of the specified items.</span></span>
<span data-ttu-id="64fd9-111">Du kan till exempel använda denna cmdlet för att hämta värdet för egenskapen LastAccessTime för ett fil objekt.</span><span class="sxs-lookup"><span data-stu-id="64fd9-111">For example, you can use this cmdlet to get the value of the LastAccessTime property of a file object.</span></span>
<span data-ttu-id="64fd9-112">Du kan också använda denna cmdlet för att Visa register poster och deras värden.</span><span class="sxs-lookup"><span data-stu-id="64fd9-112">You can also use this cmdlet to view registry entries and their values.</span></span>

## <span data-ttu-id="64fd9-113">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="64fd9-113">EXAMPLES</span></span>

### <span data-ttu-id="64fd9-114">Exempel 1: Hämta information om en angiven katalog</span><span class="sxs-lookup"><span data-stu-id="64fd9-114">Example 1: Get information about a specific directory</span></span>

<span data-ttu-id="64fd9-115">Det här kommandot hämtar information om katalogen "C:\Windows".</span><span class="sxs-lookup"><span data-stu-id="64fd9-115">This command gets information about the "C:\Windows" directory.</span></span>

```powershell
Get-ItemProperty C:\Windows
```

### <span data-ttu-id="64fd9-116">Exempel 2: Hämta egenskaperna för en enskild fil</span><span class="sxs-lookup"><span data-stu-id="64fd9-116">Example 2: Get the properties of a specific file</span></span>

<span data-ttu-id="64fd9-117">Det här kommandot hämtar egenskaperna för filen "C:\Test\Weather.xls".</span><span class="sxs-lookup"><span data-stu-id="64fd9-117">This command gets the properties of the "C:\Test\Weather.xls" file.</span></span>
<span data-ttu-id="64fd9-118">Resultatet är skickas till `Format-List` cmdleten för att visa utdata som en lista.</span><span class="sxs-lookup"><span data-stu-id="64fd9-118">The result is piped to the `Format-List` cmdlet to display the output as a list.</span></span>

```powershell
Get-ItemProperty C:\Test\Weather.xls | Format-List
```

### <span data-ttu-id="64fd9-119">Exempel 3: Visa värde namnet och data för register poster i en register under nyckel</span><span class="sxs-lookup"><span data-stu-id="64fd9-119">Example 3: Display the value name and data of registry entries in a registry subkey</span></span>

<span data-ttu-id="64fd9-120">Det här kommandot visar värde namnet och data för alla register poster som finns i register under nyckeln "CurrentVersion".</span><span class="sxs-lookup"><span data-stu-id="64fd9-120">This command displays the value name and data of each of the registry entries contained in the "CurrentVersion" registry subkey.</span></span>
<span data-ttu-id="64fd9-121">Observera att kommandot kräver att det finns en PowerShell-enhet med namnet `HKLM:` som är mappad till registrerings data filen "HKEY_LOCAL_MACHINE" i registret.</span><span class="sxs-lookup"><span data-stu-id="64fd9-121">Note that the command requires that there is a PowerShell drive named `HKLM:` that is mapped to the "HKEY_LOCAL_MACHINE" hive of the registry.</span></span>
<span data-ttu-id="64fd9-122">En enhet med det namnet och mappningen är tillgänglig i PowerShell som standard.</span><span class="sxs-lookup"><span data-stu-id="64fd9-122">A drive with that name and mapping is available in PowerShell by default.</span></span>
<span data-ttu-id="64fd9-123">Du kan också ange sökvägen till den här register under nyckeln med hjälp av följande alternativa sökväg som börjar med Providerns namn följt av två kolon:</span><span class="sxs-lookup"><span data-stu-id="64fd9-123">Alternatively, the path to this registry subkey can be specified by using the following alternative path that begins with the provider name followed by two colons:</span></span>

<span data-ttu-id="64fd9-124">"Registry:: HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion".</span><span class="sxs-lookup"><span data-stu-id="64fd9-124">"Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion".</span></span>

```powershell
Get-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion
```

### <span data-ttu-id="64fd9-125">Exempel 4: Hämta värde namn och data för en register post i en register under nyckel</span><span class="sxs-lookup"><span data-stu-id="64fd9-125">Example 4: Get the value name and data of a registry entry in a registry subkey</span></span>

<span data-ttu-id="64fd9-126">Det här kommandot hämtar värde namnet och data för register posten "ProgramFilesDir" i register under nyckeln "CurrentVersion".</span><span class="sxs-lookup"><span data-stu-id="64fd9-126">This command gets the value name and data of the "ProgramFilesDir" registry entry in the "CurrentVersion" registry subkey.</span></span>
<span data-ttu-id="64fd9-127">Kommandot använder parametern **Path** för att ange under nyckeln och parametern name för att ange värde namnet för posten.</span><span class="sxs-lookup"><span data-stu-id="64fd9-127">The command uses the **Path** parameter to specify the subkey and the Name parameter to specify the value name of the entry.</span></span>

<span data-ttu-id="64fd9-128">Kommandot använder en bakgrunds-eller grav accent ( \` ), PowerShell-fortsättnings tecknen, för att fortsätta kommandot på den andra raden.</span><span class="sxs-lookup"><span data-stu-id="64fd9-128">The command uses a back tick or grave accent (\`), the PowerShell continuation character, to continue the command on the second line.</span></span>

```powershell
Get-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name "ProgramFilesDir"
```

### <span data-ttu-id="64fd9-129">Exempel 5: Hämta värde namn och data för register poster i en register nyckel</span><span class="sxs-lookup"><span data-stu-id="64fd9-129">Example 5: Get the value names and data of registry entries in a registry key</span></span>

<span data-ttu-id="64fd9-130">Det här kommandot hämtar värde namn och data för register posterna i register nyckeln "PowerShellEngine".</span><span class="sxs-lookup"><span data-stu-id="64fd9-130">This command gets the value names and data of the registry entries in the "PowerShellEngine" registry key.</span></span>
<span data-ttu-id="64fd9-131">Resultatet visas i följande exempel på utdata.</span><span class="sxs-lookup"><span data-stu-id="64fd9-131">The results are shown in the following sample output.</span></span>

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

### <span data-ttu-id="64fd9-132">Exempel 6: Hämta, formatera och visa resultaten av register värden och data</span><span class="sxs-lookup"><span data-stu-id="64fd9-132">Example 6: Get, format, and display the results of registry values and data</span></span>

<span data-ttu-id="64fd9-133">Det här exemplet visar hur du formaterar utdata från ett `Get-ItemProperty` kommando i en lista för att göra det enkelt att se registervärdena och data och göra det enkelt att tolka resultaten.</span><span class="sxs-lookup"><span data-stu-id="64fd9-133">This example shows how to format the output of a `Get-ItemProperty` command in a list to make it easy to see the registry values and data and to make it easy to interpret the results.</span></span>

<span data-ttu-id="64fd9-134">Det första kommandot använder `Get-ItemProperty` cmdleten för att hämta register poster i **Microsoft. PowerShell** -undernyckeln.</span><span class="sxs-lookup"><span data-stu-id="64fd9-134">The first command uses the `Get-ItemProperty` cmdlet to get the registry entries in the **Microsoft.PowerShell** subkey.</span></span>
<span data-ttu-id="64fd9-135">Den här under nyckeln innehåller alternativ för standard gränssnittet för PowerShell.</span><span class="sxs-lookup"><span data-stu-id="64fd9-135">This subkey stores options for the default shell for PowerShell.</span></span>
<span data-ttu-id="64fd9-136">Resultatet visas i följande exempel på utdata.</span><span class="sxs-lookup"><span data-stu-id="64fd9-136">The results are shown in the following sample output.</span></span>

<span data-ttu-id="64fd9-137">Utdata visar att det finns två register poster, "Path" och "ExecutionPolicy".</span><span class="sxs-lookup"><span data-stu-id="64fd9-137">The output shows that there are two registry entries, "Path" and "ExecutionPolicy".</span></span>
<span data-ttu-id="64fd9-138">När en register nyckel innehåller färre än fem poster, visas den som standard i en tabell, men den är ofta enklare att visa i en lista.</span><span class="sxs-lookup"><span data-stu-id="64fd9-138">When a registry key contains fewer than five entries, by default it is displayed in a table, but it is often easier to view in a list.</span></span>

<span data-ttu-id="64fd9-139">Det andra kommandot använder samma `Get-ItemProperty` kommando.</span><span class="sxs-lookup"><span data-stu-id="64fd9-139">The second command uses the same `Get-ItemProperty` command.</span></span>
<span data-ttu-id="64fd9-140">Men den här gången använder kommandot en pipeline-operator ( `|` ) för att skicka kommandots resultat till `Format-List` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="64fd9-140">However, this time, the command uses a pipeline operator (`|`) to send the results of the command to the `Format-List` cmdlet.</span></span>
<span data-ttu-id="64fd9-141">`Format-List`Kommandot använder egenskaps parametern med värdet \* (all) för att visa alla egenskaper för objekten i en lista.</span><span class="sxs-lookup"><span data-stu-id="64fd9-141">The `Format-List` command uses the Property parameter with a value of '\*' (all) to display all of the properties of the objects in a list.</span></span>
<span data-ttu-id="64fd9-142">Resultatet visas i följande exempel på utdata.</span><span class="sxs-lookup"><span data-stu-id="64fd9-142">The results are shown in the following sample output.</span></span>

<span data-ttu-id="64fd9-143">Den resulterande visningen visar register posterna "Path" och "ExecutionPolicy", tillsammans med flera mindre välbekanta egenskaper för objektet i register nyckeln.</span><span class="sxs-lookup"><span data-stu-id="64fd9-143">The resulting display shows the "Path" and "ExecutionPolicy" registry entries, along with several less familiar properties of the registry key object.</span></span>
<span data-ttu-id="64fd9-144">De andra egenskaperna, som har prefixet PS, är egenskaper för anpassade PowerShell-objekt, till exempel de objekt som representerar register nycklarna.</span><span class="sxs-lookup"><span data-stu-id="64fd9-144">The other properties, prefixed with PS, are properties of PowerShell custom objects, such as the objects that represent the registry keys.</span></span>

```powershell
Get-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\PowerShell\1\ShellIds\Microsoft.PowerShell
```

```output
Path                                                        ExecutionPolicy
----                                                        ---------------
C:\Windows\system32\WindowsPowerShell\v1.0\powershell.exe   RemoteSigned
```

```powershell
Get-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\PowerShell\1\ShellIds\Microsoft.PowerShell | Format-List -Property *
```

```output
PSPath          : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\Software\Microsoft\PowerShell\1\ShellIds\Micro
soft.PowerShell
PSParentPath    : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\Software\Microsoft\PowerShell\1\ShellIds
PSChildName     : Microsoft.PowerShell
PSDrive         : HKLM
PSProvider      : Microsoft.PowerShell.Core\Registry
Path            : C:\Windows\system32\WindowsPowerShell\v1.0\powershell.exe
ExecutionPolicy : RemoteSigned
```

## <span data-ttu-id="64fd9-145">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="64fd9-145">PARAMETERS</span></span>

### <span data-ttu-id="64fd9-146">-Credential</span><span class="sxs-lookup"><span data-stu-id="64fd9-146">-Credential</span></span>

<span data-ttu-id="64fd9-147">Anger ett användar konto som har behörighet att utföra den här åtgärden.</span><span class="sxs-lookup"><span data-stu-id="64fd9-147">Specifies a user account that has permission to perform this action.</span></span>
<span data-ttu-id="64fd9-148">Standard är den aktuella användaren.</span><span class="sxs-lookup"><span data-stu-id="64fd9-148">The default is the current user.</span></span>

<span data-ttu-id="64fd9-149">Ange ett användar namn, till exempel "user01" eller "Domain01\User01", eller ange ett **PSCredential** -objekt, t. ex. ett som genererades av `Get-Credential` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="64fd9-149">Type a user name, such as "User01" or "Domain01\User01", or enter a **PSCredential** object, such as one generated by the `Get-Credential` cmdlet.</span></span>
<span data-ttu-id="64fd9-150">Om du anger ett användar namn uppmanas du att ange ett lösen ord.</span><span class="sxs-lookup"><span data-stu-id="64fd9-150">If you type a user name, you are prompted for a password.</span></span>

> [!WARNING]
> <span data-ttu-id="64fd9-151">Den här parametern stöds inte av några providrar som installeras med Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="64fd9-151">This parameter is not supported by any providers installed with Windows PowerShell.</span></span>

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

### <span data-ttu-id="64fd9-152">-Undanta</span><span class="sxs-lookup"><span data-stu-id="64fd9-152">-Exclude</span></span>

<span data-ttu-id="64fd9-153">Anger, som en sträng mat ris, ett objekt eller objekt som denna cmdlet exkluderar från åtgärden.</span><span class="sxs-lookup"><span data-stu-id="64fd9-153">Specifies, as a string array, an item or items that this cmdlet excludes from the operation.</span></span>
<span data-ttu-id="64fd9-154">Värdet för den här parametern kvalificerar parametern **Path** .</span><span class="sxs-lookup"><span data-stu-id="64fd9-154">The value of this parameter qualifies the **Path** parameter.</span></span>
<span data-ttu-id="64fd9-155">Ange ett Sök vägs element eller ett mönster, till exempel "\*. txt".</span><span class="sxs-lookup"><span data-stu-id="64fd9-155">Enter a path element or pattern, such as "\*.txt".</span></span>
<span data-ttu-id="64fd9-156">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="64fd9-156">Wildcard characters are permitted.</span></span>

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

### <span data-ttu-id="64fd9-157">-Filter</span><span class="sxs-lookup"><span data-stu-id="64fd9-157">-Filter</span></span>

<span data-ttu-id="64fd9-158">Anger ett filter i formatet eller språket för providern.</span><span class="sxs-lookup"><span data-stu-id="64fd9-158">Specifies a filter in the format or language of the provider.</span></span>
<span data-ttu-id="64fd9-159">Värdet för den här parametern kvalificerar parametern **Path** .</span><span class="sxs-lookup"><span data-stu-id="64fd9-159">The value of this parameter qualifies the **Path** parameter.</span></span>

<span data-ttu-id="64fd9-160">Syntaxen för filtret, inklusive användning av jokertecken, är beroende av providern.</span><span class="sxs-lookup"><span data-stu-id="64fd9-160">The syntax of the filter, including the use of wildcard characters, depends on the provider.</span></span>
<span data-ttu-id="64fd9-161">Filter är mer effektiva än andra parametrar, eftersom providern tillämpar dem när cmdleten hämtar objekten i stället för att ha PowerShell filtrera objekten när de har hämtats.</span><span class="sxs-lookup"><span data-stu-id="64fd9-161">Filters are more efficient than other parameters, because the provider applies them when the cmdlet gets the objects rather than having PowerShell filter the objects after they are retrieved.</span></span>

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

### <span data-ttu-id="64fd9-162">-Inkludera</span><span class="sxs-lookup"><span data-stu-id="64fd9-162">-Include</span></span>

<span data-ttu-id="64fd9-163">Anger, som en sträng mat ris, ett objekt eller objekt som denna cmdlet inkluderar i åtgärden.</span><span class="sxs-lookup"><span data-stu-id="64fd9-163">Specifies, as a string array, an item or items that this cmdlet includes in the operation.</span></span>
<span data-ttu-id="64fd9-164">Värdet för den här parametern kvalificerar parametern **Path** .</span><span class="sxs-lookup"><span data-stu-id="64fd9-164">The value of this parameter qualifies the **Path** parameter.</span></span>
<span data-ttu-id="64fd9-165">Ange ett Sök vägs element eller ett mönster, till exempel "\*. txt".</span><span class="sxs-lookup"><span data-stu-id="64fd9-165">Enter a path element or pattern, such as "\*.txt".</span></span>
<span data-ttu-id="64fd9-166">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="64fd9-166">Wildcard characters are permitted.</span></span>

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

### <span data-ttu-id="64fd9-167">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="64fd9-167">-LiteralPath</span></span>

<span data-ttu-id="64fd9-168">Anger sökvägen till egenskapens aktuella plats.</span><span class="sxs-lookup"><span data-stu-id="64fd9-168">Specifies the path to the current location of the property.</span></span>
<span data-ttu-id="64fd9-169">Till skillnad från parametern **Path** används värdet för **LiteralPath** exakt som det har angetts.</span><span class="sxs-lookup"><span data-stu-id="64fd9-169">Unlike the **Path** parameter, the value of **LiteralPath** is used exactly as it is typed.</span></span>
<span data-ttu-id="64fd9-170">Inga tecken tolkas som jokertecken.</span><span class="sxs-lookup"><span data-stu-id="64fd9-170">No characters are interpreted as wildcards.</span></span>
<span data-ttu-id="64fd9-171">Om sökvägen innehåller escape-tecken omger du den med enkla citat tecken.</span><span class="sxs-lookup"><span data-stu-id="64fd9-171">If the path includes escape characters, enclose it in single quotation marks.</span></span>
<span data-ttu-id="64fd9-172">Enkla citat tecken säger att PowerShell inte tolkar några tecken som escape-sekvenser.</span><span class="sxs-lookup"><span data-stu-id="64fd9-172">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

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

### <span data-ttu-id="64fd9-173">-Name</span><span class="sxs-lookup"><span data-stu-id="64fd9-173">-Name</span></span>

<span data-ttu-id="64fd9-174">Anger namnet på egenskapen eller egenskaperna som ska hämtas.</span><span class="sxs-lookup"><span data-stu-id="64fd9-174">Specifies the name of the property or properties to retrieve.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: PSProperty

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="64fd9-175">-Path</span><span class="sxs-lookup"><span data-stu-id="64fd9-175">-Path</span></span>

<span data-ttu-id="64fd9-176">Anger sökvägen till objektet eller objekten.</span><span class="sxs-lookup"><span data-stu-id="64fd9-176">Specifies the path to the item or items.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Path
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="64fd9-177">– UseTransaction</span><span class="sxs-lookup"><span data-stu-id="64fd9-177">-UseTransaction</span></span>

<span data-ttu-id="64fd9-178">Inkluderar kommandot i den aktiva transaktionen.</span><span class="sxs-lookup"><span data-stu-id="64fd9-178">Includes the command in the active transaction.</span></span>
<span data-ttu-id="64fd9-179">Den här parametern är bara giltig medan en transaktion pågår.</span><span class="sxs-lookup"><span data-stu-id="64fd9-179">This parameter is valid only when a transaction is in progress.</span></span>
<span data-ttu-id="64fd9-180">Mer information finns i inkluderar kommandot i den aktiva transaktionen.</span><span class="sxs-lookup"><span data-stu-id="64fd9-180">For more information, see Includes the command in the active transaction.</span></span>
<span data-ttu-id="64fd9-181">Den här parametern är bara giltig medan en transaktion pågår.</span><span class="sxs-lookup"><span data-stu-id="64fd9-181">This parameter is valid only when a transaction is in progress.</span></span>
<span data-ttu-id="64fd9-182">Mer information finns i [about_Transactions](../Microsoft.PowerShell.Core/About/about_Transactions.md).</span><span class="sxs-lookup"><span data-stu-id="64fd9-182">For more information, see [about_Transactions](../Microsoft.PowerShell.Core/About/about_Transactions.md).</span></span>

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

### <span data-ttu-id="64fd9-183">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="64fd9-183">CommonParameters</span></span>

<span data-ttu-id="64fd9-184">Denna cmdlet stöder de gemensamma parametrarna:,,,,,,,, `-Debug` `-ErrorAction` `-ErrorVariable` `-InformationAction` `-InformationVariable` `-OutVariable` `-OutBuffer` `-PipelineVariable` `-Verbose` `-WarningAction` , och `-WarningVariable` .</span><span class="sxs-lookup"><span data-stu-id="64fd9-184">This cmdlet supports the common parameters: `-Debug`, `-ErrorAction`, `-ErrorVariable`, `-InformationAction`, `-InformationVariable`, `-OutVariable`, `-OutBuffer`, `-PipelineVariable`, `-Verbose`, `-WarningAction`, and `-WarningVariable`.</span></span> <span data-ttu-id="64fd9-185">Mer information finns i [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span><span class="sxs-lookup"><span data-stu-id="64fd9-185">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="64fd9-186">INDATA</span><span class="sxs-lookup"><span data-stu-id="64fd9-186">INPUTS</span></span>

### <span data-ttu-id="64fd9-187">System. String</span><span class="sxs-lookup"><span data-stu-id="64fd9-187">System.String</span></span>

<span data-ttu-id="64fd9-188">Du kan skicka vidare en sträng som innehåller en sökväg till `Get-ItemProperty` .</span><span class="sxs-lookup"><span data-stu-id="64fd9-188">You can pipe a string that contains a path to `Get-ItemProperty`.</span></span>

## <span data-ttu-id="64fd9-189">UTDATA</span><span class="sxs-lookup"><span data-stu-id="64fd9-189">OUTPUTS</span></span>

### <span data-ttu-id="64fd9-190">System. Boolean, system. String, system. DateTime</span><span class="sxs-lookup"><span data-stu-id="64fd9-190">System.Boolean, System.String, System.DateTime</span></span>

<span data-ttu-id="64fd9-191">`Get-ItemProperty` Returnerar ett objekt för varje objekt egenskap som det får.</span><span class="sxs-lookup"><span data-stu-id="64fd9-191">`Get-ItemProperty` returns an object for each item property that it gets.</span></span>
<span data-ttu-id="64fd9-192">Objekt typen beror på vilket objekt som hämtas.</span><span class="sxs-lookup"><span data-stu-id="64fd9-192">The object type depends on the object that is retrieved.</span></span>
<span data-ttu-id="64fd9-193">I en fil system enhet kan det exempelvis returnera en fil eller mapp.</span><span class="sxs-lookup"><span data-stu-id="64fd9-193">For example, in a file system drive, it might return a file or folder.</span></span>

## <span data-ttu-id="64fd9-194">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="64fd9-194">NOTES</span></span>

<span data-ttu-id="64fd9-195">`Get-ItemProperty`Cmdleten är utformad för att fungera med data som exponeras av vilken provider som helst.</span><span class="sxs-lookup"><span data-stu-id="64fd9-195">The `Get-ItemProperty` cmdlet is designed to work with the data exposed by any provider.</span></span> <span data-ttu-id="64fd9-196">Om du vill visa en lista över tillgängliga providers i sessionen skriver du " `Get-PSProvider` ".</span><span class="sxs-lookup"><span data-stu-id="64fd9-196">To list the providers available in your session, type "`Get-PSProvider`".</span></span> <span data-ttu-id="64fd9-197">Mer information finns i about_Providers.</span><span class="sxs-lookup"><span data-stu-id="64fd9-197">For more information, see about_Providers.</span></span>

## <span data-ttu-id="64fd9-198">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="64fd9-198">RELATED LINKS</span></span>

[<span data-ttu-id="64fd9-199">Clear-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="64fd9-199">Clear-ItemProperty</span></span>](Clear-ItemProperty.md)

[<span data-ttu-id="64fd9-200">Kopiera – ItemProperty</span><span class="sxs-lookup"><span data-stu-id="64fd9-200">Copy-ItemProperty</span></span>](Copy-ItemProperty.md)

[<span data-ttu-id="64fd9-201">Move-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="64fd9-201">Move-ItemProperty</span></span>](Move-ItemProperty.md)

[<span data-ttu-id="64fd9-202">New-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="64fd9-202">New-ItemProperty</span></span>](New-ItemProperty.md)

[<span data-ttu-id="64fd9-203">Remove-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="64fd9-203">Remove-ItemProperty</span></span>](Remove-ItemProperty.md)

[<span data-ttu-id="64fd9-204">Byt namn – ItemProperty</span><span class="sxs-lookup"><span data-stu-id="64fd9-204">Rename-ItemProperty</span></span>](Rename-ItemProperty.md)

[<span data-ttu-id="64fd9-205">Set-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="64fd9-205">Set-ItemProperty</span></span>](Set-ItemProperty.md)
