---
external help file: Microsoft.PowerShell.Security.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Security
ms.date: 03/25/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.security/get-acl?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Acl
ms.openlocfilehash: ed458e7f58ebb61611e2fd9e60430a7330087e8a
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94709883"
---
# <span data-ttu-id="0386a-102">Get-Acl</span><span class="sxs-lookup"><span data-stu-id="0386a-102">Get-Acl</span></span>

## <span data-ttu-id="0386a-103">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="0386a-103">SYNOPSIS</span></span>
<span data-ttu-id="0386a-104">Hämtar säkerhets beskrivningen för en resurs, till exempel en fil eller register nyckel.</span><span class="sxs-lookup"><span data-stu-id="0386a-104">Gets the security descriptor for a resource, such as a file or registry key.</span></span>

## <span data-ttu-id="0386a-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="0386a-105">SYNTAX</span></span>

### <span data-ttu-id="0386a-106">ByPath (standard)</span><span class="sxs-lookup"><span data-stu-id="0386a-106">ByPath (Default)</span></span>

```
Get-Acl [[-Path] <String[]>] [-Audit] [-Filter <String>] [-Include <String[]>] [-Exclude <String[]>]
 [<CommonParameters>]
```

### <span data-ttu-id="0386a-107">ByInputObject</span><span class="sxs-lookup"><span data-stu-id="0386a-107">ByInputObject</span></span>

```
Get-Acl -InputObject <PSObject> [-Audit] [-Filter <String>] [-Include <String[]>]
 [-Exclude <String[]>] [<CommonParameters>]
```

### <span data-ttu-id="0386a-108">ByLiteralPath</span><span class="sxs-lookup"><span data-stu-id="0386a-108">ByLiteralPath</span></span>

```
Get-Acl [-LiteralPath <String[]>] [-Audit] [-Filter <String>] [-Include <String[]>]
 [-Exclude <String[]>] [<CommonParameters>]
```

## <span data-ttu-id="0386a-109">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="0386a-109">DESCRIPTION</span></span>

<span data-ttu-id="0386a-110">`Get-Acl`Cmdleten hämtar objekt som representerar säkerhets beskrivningen för en fil eller resurs.</span><span class="sxs-lookup"><span data-stu-id="0386a-110">The `Get-Acl` cmdlet gets objects that represent the security descriptor of a file or resource.</span></span> <span data-ttu-id="0386a-111">Säkerhets beskrivningen innehåller åtkomst kontrol listorna (ACL) för resursen.</span><span class="sxs-lookup"><span data-stu-id="0386a-111">The security descriptor contains the access control lists (ACLs) of the resource.</span></span> <span data-ttu-id="0386a-112">ACL: en anger de behörigheter som användare och användar grupper har åtkomst till resursen.</span><span class="sxs-lookup"><span data-stu-id="0386a-112">The ACL specifies the permissions that users and user groups have to access the resource.</span></span>

<span data-ttu-id="0386a-113">Från och med Windows PowerShell 3,0 kan du använda **InputObject** -parametern för `Get-Acl` för att hämta säkerhets beskrivningen för objekt som inte har en sökväg.</span><span class="sxs-lookup"><span data-stu-id="0386a-113">Beginning in Windows PowerShell 3.0, you can use the **InputObject** parameter of `Get-Acl` to get the security descriptor of objects that do not have a path.</span></span>

## <span data-ttu-id="0386a-114">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="0386a-114">EXAMPLES</span></span>

### <span data-ttu-id="0386a-115">Exempel 1 – Hämta en ACL för en mapp</span><span class="sxs-lookup"><span data-stu-id="0386a-115">Example 1- Get an ACL for a folder</span></span>

<span data-ttu-id="0386a-116">Det här exemplet hämtar katalogens säkerhets Beskrivning `C:\Windows` .</span><span class="sxs-lookup"><span data-stu-id="0386a-116">This example gets the security descriptor of the `C:\Windows` directory.</span></span>

```powershell
Get-Acl C:\Windows
```

### <span data-ttu-id="0386a-117">Exempel 2 – Hämta en ACL för en mapp med jokertecken</span><span class="sxs-lookup"><span data-stu-id="0386a-117">Example 2 - Get an ACL for a folder using wildcards</span></span>

<span data-ttu-id="0386a-118">Det här exemplet hämtar PowerShell-sökvägen och SDDL för alla `.log` filer i `C:\Windows` katalogen vars namn börjar med `s` .</span><span class="sxs-lookup"><span data-stu-id="0386a-118">This example gets the PowerShell path and SDDL for all of the `.log` files in the `C:\Windows` directory whose names begin with `s`.</span></span>

```powershell
Get-Acl C:\Windows\s*.log | Format-List -Property PSPath, Sddl
```

<span data-ttu-id="0386a-119">Kommandot använder `Get-Acl` cmdleten för att hämta objekt som representerar säkerhets beskrivare för varje loggfil.</span><span class="sxs-lookup"><span data-stu-id="0386a-119">The command uses the `Get-Acl` cmdlet to get objects representing the security descriptors of each log file.</span></span> <span data-ttu-id="0386a-120">Den använder en pipeline-operator ( `|` ) för att skicka resultatet till- `Format-List` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="0386a-120">It uses a pipeline operator (`|`) to send the results to the `Format-List` cmdlet.</span></span> <span data-ttu-id="0386a-121">Kommandot använder **egenskaps** parametern för `Format-List` för att endast visa egenskaperna **PsPath** och **SDDL** för varje säkerhets beskrivnings objekt.</span><span class="sxs-lookup"><span data-stu-id="0386a-121">The command uses the **Property** parameter of `Format-List` to display only the **PsPath** and **SDDL** properties of each security descriptor object.</span></span>

<span data-ttu-id="0386a-122">Listor används ofta i PowerShell, eftersom långa värden visas trunkerade i tabeller.</span><span class="sxs-lookup"><span data-stu-id="0386a-122">Lists are often used in PowerShell, because long values appear truncated in tables.</span></span>

<span data-ttu-id="0386a-123">**SDDL** -värdena är värdefulla för system administratörer eftersom de är enkla text strängar som innehåller all information i säkerhets beskrivningen.</span><span class="sxs-lookup"><span data-stu-id="0386a-123">The **SDDL** values are valuable to system administrators, because they are simple text strings that contain all of the information in the security descriptor.</span></span> <span data-ttu-id="0386a-124">De är därför enkla att skicka och lagra, och de kan tolkas vid behov.</span><span class="sxs-lookup"><span data-stu-id="0386a-124">As such, they are easy to pass and store, and they can be parsed when needed.</span></span>

### <span data-ttu-id="0386a-125">Exempel 3 – Hämta antal gransknings poster för en ACL</span><span class="sxs-lookup"><span data-stu-id="0386a-125">Example 3 - Get count of Audit entries for an ACL</span></span>

<span data-ttu-id="0386a-126">Det här exemplet hämtar säkerhets beskrivare för `.log` filerna i `C:\Windows` katalogen vars namn börjar med `s` .</span><span class="sxs-lookup"><span data-stu-id="0386a-126">This example gets the security descriptors of the `.log` files in the `C:\Windows` directory whose names begin with `s`.</span></span>

```powershell
Get-Acl C:\Windows\s*.log -Audit | ForEach-Object { $_.Audit.Count }
```

<span data-ttu-id="0386a-127">Den använder **gransknings** parametern för att hämta gransknings poster från SACL i säkerhets beskrivningen.</span><span class="sxs-lookup"><span data-stu-id="0386a-127">It uses the **Audit** parameter to get the audit records from the SACL in the security descriptor.</span></span>
<span data-ttu-id="0386a-128">Sedan använder den `ForEach-Object` cmdleten för att räkna antalet gransknings poster som är associerade med varje fil.</span><span class="sxs-lookup"><span data-stu-id="0386a-128">Then it uses the `ForEach-Object` cmdlet to count the number of audit records associated with each file.</span></span> <span data-ttu-id="0386a-129">Resultatet är en lista med tal som representerar antalet gransknings poster för varje loggfil.</span><span class="sxs-lookup"><span data-stu-id="0386a-129">The result is a list of numbers representing the number of audit records for each log file.</span></span>

### <span data-ttu-id="0386a-130">Exempel 4 – Hämta en ACL för en register nyckel</span><span class="sxs-lookup"><span data-stu-id="0386a-130">Example 4 - Get an ACL for a registry key</span></span>

<span data-ttu-id="0386a-131">I det här exemplet används `Get-Acl` cmdleten för att hämta säkerhets beskrivningen för registrets kontroll under nyckel ( `HKLM:\SYSTEM\CurrentControlSet\Control` ).</span><span class="sxs-lookup"><span data-stu-id="0386a-131">This example uses the `Get-Acl` cmdlet to get the security descriptor of the Control subkey (`HKLM:\SYSTEM\CurrentControlSet\Control`) of the registry.</span></span>

```powershell
Get-Acl -Path HKLM:\System\CurrentControlSet\Control | Format-List
```

<span data-ttu-id="0386a-132">Parametern **Path** anger kontroll under nyckeln.</span><span class="sxs-lookup"><span data-stu-id="0386a-132">The **Path** parameter specifies the Control subkey.</span></span> <span data-ttu-id="0386a-133">Pipelinen ( `|` ) skickar den säkerhets beskrivning som `Get-Acl` `Format-List` kommer till kommandot, som formaterar egenskaperna för säkerhets beskrivningen som en lista så att de är lätta att läsa.</span><span class="sxs-lookup"><span data-stu-id="0386a-133">The pipeline operator (`|`) passes the security descriptor that `Get-Acl` gets to the `Format-List` command, which formats the properties of the security descriptor as a list so that they are easy to read.</span></span>

### <span data-ttu-id="0386a-134">Exempel 5 – Hämta en ACL med **InputObject**</span><span class="sxs-lookup"><span data-stu-id="0386a-134">Example 5 - Get an ACL using **InputObject**</span></span>

<span data-ttu-id="0386a-135">I det här exemplet används parametern **InputObject** för `Get-Acl` för att hämta säkerhets beskrivningen för ett underlag rings system objekt.</span><span class="sxs-lookup"><span data-stu-id="0386a-135">This example uses the **InputObject** parameter of `Get-Acl` to get the security descriptor of a storage subsystem object.</span></span>

```powershell
Get-Acl -InputObject (Get-StorageSubSystem -Name S087)
```

## <span data-ttu-id="0386a-136">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="0386a-136">PARAMETERS</span></span>

### <span data-ttu-id="0386a-137">-Granska</span><span class="sxs-lookup"><span data-stu-id="0386a-137">-Audit</span></span>

<span data-ttu-id="0386a-138">Hämtar gransknings data för säkerhets beskrivningen från system åtkomst kontrol listan (SACL).</span><span class="sxs-lookup"><span data-stu-id="0386a-138">Gets the audit data for the security descriptor from the system access control list (SACL).</span></span>

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

### <span data-ttu-id="0386a-139">-Undanta</span><span class="sxs-lookup"><span data-stu-id="0386a-139">-Exclude</span></span>

<span data-ttu-id="0386a-140">Utesluter de angivna objekten.</span><span class="sxs-lookup"><span data-stu-id="0386a-140">Omits the specified items.</span></span> <span data-ttu-id="0386a-141">Värdet för den här parametern kvalificerar parametern **Path** .</span><span class="sxs-lookup"><span data-stu-id="0386a-141">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="0386a-142">Ange ett Sök vägs element eller ett mönster, till exempel `*.txt` .</span><span class="sxs-lookup"><span data-stu-id="0386a-142">Enter a path element or pattern, such as `*.txt`.</span></span> <span data-ttu-id="0386a-143">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="0386a-143">Wildcards are permitted.</span></span>

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

### <span data-ttu-id="0386a-144">-Filter</span><span class="sxs-lookup"><span data-stu-id="0386a-144">-Filter</span></span>

<span data-ttu-id="0386a-145">Anger ett filter i providerns format eller språk.</span><span class="sxs-lookup"><span data-stu-id="0386a-145">Specifies a filter in the provider's format or language.</span></span> <span data-ttu-id="0386a-146">Värdet för den här parametern kvalificerar parametern **Path** .</span><span class="sxs-lookup"><span data-stu-id="0386a-146">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="0386a-147">Syntaxen för filtret, inklusive användning av jokertecken, beror på providern.</span><span class="sxs-lookup"><span data-stu-id="0386a-147">The syntax of the filter, including the use of wildcards, depends on the provider.</span></span> <span data-ttu-id="0386a-148">Filter är mer effektiva än andra parametrar, eftersom providern tillämpar dem när objekten hämtas, i stället för att ha PowerShell filtrera objekten när de har hämtats.</span><span class="sxs-lookup"><span data-stu-id="0386a-148">Filters are more efficient than other parameters, because the provider applies them when getting the objects, rather than having PowerShell filter the objects after they are retrieved.</span></span>

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

### <span data-ttu-id="0386a-149">-Inkludera</span><span class="sxs-lookup"><span data-stu-id="0386a-149">-Include</span></span>

<span data-ttu-id="0386a-150">Hämtar endast de angivna objekten.</span><span class="sxs-lookup"><span data-stu-id="0386a-150">Gets only the specified items.</span></span> <span data-ttu-id="0386a-151">Värdet för den här parametern kvalificerar parametern **Path** .</span><span class="sxs-lookup"><span data-stu-id="0386a-151">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="0386a-152">Ange ett Sök vägs element eller ett mönster, till exempel `*.txt` .</span><span class="sxs-lookup"><span data-stu-id="0386a-152">Enter a path element or pattern, such as `*.txt`.</span></span> <span data-ttu-id="0386a-153">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="0386a-153">Wildcards are permitted.</span></span>

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

### <span data-ttu-id="0386a-154">-Path</span><span class="sxs-lookup"><span data-stu-id="0386a-154">-Path</span></span>

<span data-ttu-id="0386a-155">Anger sökvägen till en resurs.</span><span class="sxs-lookup"><span data-stu-id="0386a-155">Specifies the path to a resource.</span></span> <span data-ttu-id="0386a-156">`Get-Acl` hämtar säkerhets beskrivningen för den resurs som anges av sökvägen.</span><span class="sxs-lookup"><span data-stu-id="0386a-156">`Get-Acl` gets the security descriptor of the resource indicated by the path.</span></span> <span data-ttu-id="0386a-157">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="0386a-157">Wildcards are permitted.</span></span> <span data-ttu-id="0386a-158">Om du utelämnar parametern **Path** , `Get-Acl` hämtas säkerhets beskrivningen för den aktuella katalogen.</span><span class="sxs-lookup"><span data-stu-id="0386a-158">If you omit the **Path** parameter, `Get-Acl` gets the security descriptor of the current directory.</span></span>

<span data-ttu-id="0386a-159">Parameter namnet ("sökväg") är valfritt.</span><span class="sxs-lookup"><span data-stu-id="0386a-159">The parameter name ("Path") is optional.</span></span>

```yaml
Type: System.String[]
Parameter Sets: ByPath
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### <span data-ttu-id="0386a-160">– InputObject</span><span class="sxs-lookup"><span data-stu-id="0386a-160">-InputObject</span></span>

<span data-ttu-id="0386a-161">Hämtar säkerhets beskrivningen för det angivna objektet.</span><span class="sxs-lookup"><span data-stu-id="0386a-161">Gets the security descriptor for the specified object.</span></span> <span data-ttu-id="0386a-162">Ange en variabel som innehåller objektet eller ett kommando som hämtar objektet.</span><span class="sxs-lookup"><span data-stu-id="0386a-162">Enter a variable that contains the object or a command that gets the object.</span></span>

<span data-ttu-id="0386a-163">Det går inte att skicka ett objekt, förutom en sökväg, till `Get-Acl` .</span><span class="sxs-lookup"><span data-stu-id="0386a-163">You cannot pipe an object, other than a path, to `Get-Acl`.</span></span> <span data-ttu-id="0386a-164">Använd i stället parametern **InputObject** explicit i kommandot.</span><span class="sxs-lookup"><span data-stu-id="0386a-164">Instead, use the **InputObject** parameter explicitly in the command.</span></span>

<span data-ttu-id="0386a-165">Den här parametern introduceras i Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="0386a-165">This parameter is introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: ByInputObject
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="0386a-166">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="0386a-166">-LiteralPath</span></span>

<span data-ttu-id="0386a-167">Anger sökvägen till en resurs.</span><span class="sxs-lookup"><span data-stu-id="0386a-167">Specifies the path to a resource.</span></span> <span data-ttu-id="0386a-168">Till skillnad från **sökväg** används värdet för parametern **LiteralPath** exakt som det har angetts.</span><span class="sxs-lookup"><span data-stu-id="0386a-168">Unlike **Path**, the value of the **LiteralPath** parameter is used exactly as it is typed.</span></span> <span data-ttu-id="0386a-169">Inga tecken tolkas som jokertecken.</span><span class="sxs-lookup"><span data-stu-id="0386a-169">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="0386a-170">Om sökvägen innehåller escape-tecken omger du den med enkla citat tecken.</span><span class="sxs-lookup"><span data-stu-id="0386a-170">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="0386a-171">Enkla citat tecken säger att PowerShell inte tolkar några tecken som escape-sekvenser.</span><span class="sxs-lookup"><span data-stu-id="0386a-171">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

<span data-ttu-id="0386a-172">Den här parametern introduceras i Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="0386a-172">This parameter is introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.String[]
Parameter Sets: ByLiteralPath
Aliases: PSPath

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="0386a-173">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="0386a-173">CommonParameters</span></span>

<span data-ttu-id="0386a-174">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="0386a-174">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="0386a-175">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="0386a-175">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="0386a-176">INDATA</span><span class="sxs-lookup"><span data-stu-id="0386a-176">INPUTS</span></span>

### <span data-ttu-id="0386a-177">System. String</span><span class="sxs-lookup"><span data-stu-id="0386a-177">System.String</span></span>

<span data-ttu-id="0386a-178">Du kan skicka vidare en sträng som innehåller en sökväg till `Get-Acl` .</span><span class="sxs-lookup"><span data-stu-id="0386a-178">You can pipe a string that contains a path to `Get-Acl`.</span></span>

## <span data-ttu-id="0386a-179">UTDATA</span><span class="sxs-lookup"><span data-stu-id="0386a-179">OUTPUTS</span></span>

### <span data-ttu-id="0386a-180">System. Security. AccessControl. FileSecurity, system. Security. AccessControl. DirectorySecurity, system. Security. AccessControl. RegistrySecurity</span><span class="sxs-lookup"><span data-stu-id="0386a-180">System.Security.AccessControl.FileSecurity, System.Security.AccessControl.DirectorySecurity, System.Security.AccessControl.RegistrySecurity</span></span>

<span data-ttu-id="0386a-181">`Get-Acl` Returnerar ett objekt som representerar de ACL: er som det hämtar.</span><span class="sxs-lookup"><span data-stu-id="0386a-181">`Get-Acl` returns an object that represents the ACLs that it gets.</span></span> <span data-ttu-id="0386a-182">Objekt typen beror på ACL-typen.</span><span class="sxs-lookup"><span data-stu-id="0386a-182">The object type depends upon the ACL type.</span></span>

## <span data-ttu-id="0386a-183">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="0386a-183">NOTES</span></span>

<span data-ttu-id="0386a-184">Den här cmdleten är endast tillgänglig på Windows-plattformar.</span><span class="sxs-lookup"><span data-stu-id="0386a-184">This cmdlet is only available on Windows platforms.</span></span>

<span data-ttu-id="0386a-185">Som standard `Get-Acl` visar PowerShell-sökvägen till resursen ( `<provider>::<resource-path>` ), ägaren till resursen och "åtkomst", en lista (matris) av åtkomst kontroll POSTERNA i DACL (Discretionary Access Control List) för resursen.</span><span class="sxs-lookup"><span data-stu-id="0386a-185">By default, `Get-Acl` displays the PowerShell path to the resource (`<provider>::<resource-path>`), the owner of the resource, and "Access", a list (array) of the access control entries in the discretionary access control list (DACL) for the resource.</span></span> <span data-ttu-id="0386a-186">DACL-listan styrs av resurs ägaren.</span><span class="sxs-lookup"><span data-stu-id="0386a-186">The DACL list is controlled by the resource owner.</span></span>

<span data-ttu-id="0386a-187">När du formaterar resultatet som en lista, ( `Get-Acl | Format-List` ), utöver sökvägen, ägaren och åtkomst listan, visar PowerShell följande egenskaper och egenskaps värden:</span><span class="sxs-lookup"><span data-stu-id="0386a-187">When you format the result as a list, (`Get-Acl | Format-List`), in addition to the path, owner, and access list, PowerShell displays the following properties and property values:</span></span>

- <span data-ttu-id="0386a-188">**Grupp**: ägarens säkerhets grupp.</span><span class="sxs-lookup"><span data-stu-id="0386a-188">**Group**: The security group of the owner.</span></span>
- <span data-ttu-id="0386a-189">**Granskning**: en lista (matris) med poster i system åtkomst kontrol listan (SACL).</span><span class="sxs-lookup"><span data-stu-id="0386a-189">**Audit**:  A list (array) of entries in the system access control list (SACL).</span></span> <span data-ttu-id="0386a-190">SACL anger de typer av åtkomst försök som Windows genererar gransknings poster för.</span><span class="sxs-lookup"><span data-stu-id="0386a-190">The SACL specifies the types of access attempts for which Windows generates audit records.</span></span>
- <span data-ttu-id="0386a-191">**SDDL**: säkerhets beskrivningen för den resurs som visas i en enskild text sträng i språk format för säkerhets beskrivnings definition.</span><span class="sxs-lookup"><span data-stu-id="0386a-191">**Sddl**: The security descriptor of the resource displayed in a single text string in Security Descriptor Definition Language format.</span></span> <span data-ttu-id="0386a-192">PowerShell använder **GetSddlForm** -metoden för säkerhets beskrivningar för att hämta dessa data.</span><span class="sxs-lookup"><span data-stu-id="0386a-192">PowerShell uses the **GetSddlForm** method of security descriptors to get this data.</span></span>

<span data-ttu-id="0386a-193">Eftersom `Get-Acl` stöds av fil systemet och register leverantörer kan du använda `Get-Acl` för att Visa ACL: en för fil system objekt, till exempel filer och kataloger samt register objekt, till exempel register nycklar och poster.</span><span class="sxs-lookup"><span data-stu-id="0386a-193">Because `Get-Acl` is supported by the file system and registry providers, you can use `Get-Acl` to view the ACL of file system objects, such as files and directories, and registry objects, such as registry keys and entries.</span></span>

## <span data-ttu-id="0386a-194">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="0386a-194">RELATED LINKS</span></span>

[<span data-ttu-id="0386a-195">Ange ACL</span><span class="sxs-lookup"><span data-stu-id="0386a-195">Set-Acl</span></span>](Set-Acl.md)
