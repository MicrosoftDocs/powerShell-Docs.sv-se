---
external help file: Microsoft.PowerShell.Security.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Security
ms.date: 03/25/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.security/get-acl?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Acl
ms.openlocfilehash: 6b862ad6bada3035551d35d592183db5805b232f
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93265275"
---
# <span data-ttu-id="a0eb0-103">Get-Acl</span><span class="sxs-lookup"><span data-stu-id="a0eb0-103">Get-Acl</span></span>

## <span data-ttu-id="a0eb0-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="a0eb0-104">SYNOPSIS</span></span>
<span data-ttu-id="a0eb0-105">Hämtar säkerhets beskrivningen för en resurs, till exempel en fil eller register nyckel.</span><span class="sxs-lookup"><span data-stu-id="a0eb0-105">Gets the security descriptor for a resource, such as a file or registry key.</span></span>

## <span data-ttu-id="a0eb0-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="a0eb0-106">SYNTAX</span></span>

### <span data-ttu-id="a0eb0-107">ByPath (standard)</span><span class="sxs-lookup"><span data-stu-id="a0eb0-107">ByPath (Default)</span></span>

```
Get-Acl [[-Path] <String[]>] [-Audit] [-AllCentralAccessPolicies] [-Filter <String>] [-Include <String[]>]
 [-Exclude <String[]>] [-UseTransaction] [<CommonParameters>]
```

### <span data-ttu-id="a0eb0-108">ByInputObject</span><span class="sxs-lookup"><span data-stu-id="a0eb0-108">ByInputObject</span></span>

```
Get-Acl -InputObject <PSObject> [-Audit] [-AllCentralAccessPolicies] [-Filter <String>] [-Include <String[]>]
 [-Exclude <String[]>] [-UseTransaction] [<CommonParameters>]
```

### <span data-ttu-id="a0eb0-109">ByLiteralPath</span><span class="sxs-lookup"><span data-stu-id="a0eb0-109">ByLiteralPath</span></span>

```
Get-Acl [-LiteralPath <String[]>] [-Audit] [-AllCentralAccessPolicies] [-Filter <String>] [-Include <String[]>]
 [-Exclude <String[]>] [-UseTransaction] [<CommonParameters>]
```

## <span data-ttu-id="a0eb0-110">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="a0eb0-110">DESCRIPTION</span></span>

<span data-ttu-id="a0eb0-111">`Get-Acl`Cmdleten hämtar objekt som representerar säkerhets beskrivningen för en fil eller resurs.</span><span class="sxs-lookup"><span data-stu-id="a0eb0-111">The `Get-Acl` cmdlet gets objects that represent the security descriptor of a file or resource.</span></span> <span data-ttu-id="a0eb0-112">Säkerhets beskrivningen innehåller åtkomst kontrol listorna (ACL) för resursen.</span><span class="sxs-lookup"><span data-stu-id="a0eb0-112">The security descriptor contains the access control lists (ACLs) of the resource.</span></span> <span data-ttu-id="a0eb0-113">ACL: en anger de behörigheter som användare och användar grupper har åtkomst till resursen.</span><span class="sxs-lookup"><span data-stu-id="a0eb0-113">The ACL specifies the permissions that users and user groups have to access the resource.</span></span>

<span data-ttu-id="a0eb0-114">Från och med Windows PowerShell 3,0 kan du använda **InputObject** -parametern för `Get-Acl` för att hämta säkerhets beskrivningen för objekt som inte har en sökväg.</span><span class="sxs-lookup"><span data-stu-id="a0eb0-114">Beginning in Windows PowerShell 3.0, you can use the **InputObject** parameter of `Get-Acl` to get the security descriptor of objects that do not have a path.</span></span>

## <span data-ttu-id="a0eb0-115">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="a0eb0-115">EXAMPLES</span></span>

### <span data-ttu-id="a0eb0-116">Exempel 1 – Hämta en ACL för en mapp</span><span class="sxs-lookup"><span data-stu-id="a0eb0-116">Example 1- Get an ACL for a folder</span></span>

<span data-ttu-id="a0eb0-117">Det här exemplet hämtar katalogens säkerhets Beskrivning `C:\Windows` .</span><span class="sxs-lookup"><span data-stu-id="a0eb0-117">This example gets the security descriptor of the `C:\Windows` directory.</span></span>

```powershell
Get-Acl C:\Windows
```

### <span data-ttu-id="a0eb0-118">Exempel 2 – Hämta en ACL för en mapp med jokertecken</span><span class="sxs-lookup"><span data-stu-id="a0eb0-118">Example 2 - Get an ACL for a folder using wildcards</span></span>

<span data-ttu-id="a0eb0-119">Det här exemplet hämtar PowerShell-sökvägen och SDDL för alla `.log` filer i `C:\Windows` katalogen vars namn börjar med `s` .</span><span class="sxs-lookup"><span data-stu-id="a0eb0-119">This example gets the PowerShell path and SDDL for all of the `.log` files in the `C:\Windows` directory whose names begin with `s`.</span></span>

```powershell
Get-Acl C:\Windows\s*.log | Format-List -Property PSPath, Sddl
```

<span data-ttu-id="a0eb0-120">Kommandot använder `Get-Acl` cmdleten för att hämta objekt som representerar säkerhets beskrivare för varje loggfil.</span><span class="sxs-lookup"><span data-stu-id="a0eb0-120">The command uses the `Get-Acl` cmdlet to get objects representing the security descriptors of each log file.</span></span> <span data-ttu-id="a0eb0-121">Den använder en pipeline-operator ( `|` ) för att skicka resultatet till- `Format-List` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="a0eb0-121">It uses a pipeline operator (`|`) to send the results to the `Format-List` cmdlet.</span></span> <span data-ttu-id="a0eb0-122">Kommandot använder **egenskaps** parametern för `Format-List` för att endast visa egenskaperna **PsPath** och **SDDL** för varje säkerhets beskrivnings objekt.</span><span class="sxs-lookup"><span data-stu-id="a0eb0-122">The command uses the **Property** parameter of `Format-List` to display only the **PsPath** and **SDDL** properties of each security descriptor object.</span></span>

<span data-ttu-id="a0eb0-123">Listor används ofta i PowerShell, eftersom långa värden visas trunkerade i tabeller.</span><span class="sxs-lookup"><span data-stu-id="a0eb0-123">Lists are often used in PowerShell, because long values appear truncated in tables.</span></span>

<span data-ttu-id="a0eb0-124">**SDDL** -värdena är värdefulla för system administratörer eftersom de är enkla text strängar som innehåller all information i säkerhets beskrivningen.</span><span class="sxs-lookup"><span data-stu-id="a0eb0-124">The **SDDL** values are valuable to system administrators, because they are simple text strings that contain all of the information in the security descriptor.</span></span> <span data-ttu-id="a0eb0-125">De är därför enkla att skicka och lagra, och de kan tolkas vid behov.</span><span class="sxs-lookup"><span data-stu-id="a0eb0-125">As such, they are easy to pass and store, and they can be parsed when needed.</span></span>

### <span data-ttu-id="a0eb0-126">Exempel 3 – Hämta antal gransknings poster för en ACL</span><span class="sxs-lookup"><span data-stu-id="a0eb0-126">Example 3 - Get count of Audit entries for an ACL</span></span>

<span data-ttu-id="a0eb0-127">Det här exemplet hämtar säkerhets beskrivare för `.log` filerna i `C:\Windows` katalogen vars namn börjar med `s` .</span><span class="sxs-lookup"><span data-stu-id="a0eb0-127">This example gets the security descriptors of the `.log` files in the `C:\Windows` directory whose names begin with `s`.</span></span>

```powershell
Get-Acl C:\Windows\s*.log -Audit | ForEach-Object { $_.Audit.Count }
```

<span data-ttu-id="a0eb0-128">Den använder **gransknings** parametern för att hämta gransknings poster från SACL i säkerhets beskrivningen.</span><span class="sxs-lookup"><span data-stu-id="a0eb0-128">It uses the **Audit** parameter to get the audit records from the SACL in the security descriptor.</span></span>
<span data-ttu-id="a0eb0-129">Sedan använder den `ForEach-Object` cmdleten för att räkna antalet gransknings poster som är associerade med varje fil.</span><span class="sxs-lookup"><span data-stu-id="a0eb0-129">Then it uses the `ForEach-Object` cmdlet to count the number of audit records associated with each file.</span></span> <span data-ttu-id="a0eb0-130">Resultatet är en lista med tal som representerar antalet gransknings poster för varje loggfil.</span><span class="sxs-lookup"><span data-stu-id="a0eb0-130">The result is a list of numbers representing the number of audit records for each log file.</span></span>

### <span data-ttu-id="a0eb0-131">Exempel 4 – Hämta en ACL för en register nyckel</span><span class="sxs-lookup"><span data-stu-id="a0eb0-131">Example 4 - Get an ACL for a registry key</span></span>

<span data-ttu-id="a0eb0-132">I det här exemplet används `Get-Acl` cmdleten för att hämta säkerhets beskrivningen för registrets kontroll under nyckel ( `HKLM:\SYSTEM\CurrentControlSet\Control` ).</span><span class="sxs-lookup"><span data-stu-id="a0eb0-132">This example uses the `Get-Acl` cmdlet to get the security descriptor of the Control subkey (`HKLM:\SYSTEM\CurrentControlSet\Control`) of the registry.</span></span>

```powershell
Get-Acl -Path HKLM:\System\CurrentControlSet\Control | Format-List
```

<span data-ttu-id="a0eb0-133">Parametern **Path** anger kontroll under nyckeln.</span><span class="sxs-lookup"><span data-stu-id="a0eb0-133">The **Path** parameter specifies the Control subkey.</span></span> <span data-ttu-id="a0eb0-134">Pipelinen ( `|` ) skickar den säkerhets beskrivning som `Get-Acl` `Format-List` kommer till kommandot, som formaterar egenskaperna för säkerhets beskrivningen som en lista så att de är lätta att läsa.</span><span class="sxs-lookup"><span data-stu-id="a0eb0-134">The pipeline operator (`|`) passes the security descriptor that `Get-Acl` gets to the `Format-List` command, which formats the properties of the security descriptor as a list so that they are easy to read.</span></span>

### <span data-ttu-id="a0eb0-135">Exempel 5 – Hämta en ACL med **InputObject**</span><span class="sxs-lookup"><span data-stu-id="a0eb0-135">Example 5 - Get an ACL using **InputObject**</span></span>

<span data-ttu-id="a0eb0-136">I det här exemplet används parametern **InputObject** för `Get-Acl` för att hämta säkerhets beskrivningen för ett underlag rings system objekt.</span><span class="sxs-lookup"><span data-stu-id="a0eb0-136">This example uses the **InputObject** parameter of `Get-Acl` to get the security descriptor of a storage subsystem object.</span></span>

```powershell
Get-Acl -InputObject (Get-StorageSubSystem -Name S087)
```

## <span data-ttu-id="a0eb0-137">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="a0eb0-137">PARAMETERS</span></span>

### <span data-ttu-id="a0eb0-138">-Granska</span><span class="sxs-lookup"><span data-stu-id="a0eb0-138">-Audit</span></span>

<span data-ttu-id="a0eb0-139">Hämtar gransknings data för säkerhets beskrivningen från system åtkomst kontrol listan (SACL).</span><span class="sxs-lookup"><span data-stu-id="a0eb0-139">Gets the audit data for the security descriptor from the system access control list (SACL).</span></span>

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

### <span data-ttu-id="a0eb0-140">-Undanta</span><span class="sxs-lookup"><span data-stu-id="a0eb0-140">-Exclude</span></span>

<span data-ttu-id="a0eb0-141">Utesluter de angivna objekten.</span><span class="sxs-lookup"><span data-stu-id="a0eb0-141">Omits the specified items.</span></span> <span data-ttu-id="a0eb0-142">Värdet för den här parametern kvalificerar parametern **Path** .</span><span class="sxs-lookup"><span data-stu-id="a0eb0-142">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="a0eb0-143">Ange ett Sök vägs element eller ett mönster, till exempel `*.txt` .</span><span class="sxs-lookup"><span data-stu-id="a0eb0-143">Enter a path element or pattern, such as `*.txt`.</span></span> <span data-ttu-id="a0eb0-144">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="a0eb0-144">Wildcards are permitted.</span></span>

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

### <span data-ttu-id="a0eb0-145">-Filter</span><span class="sxs-lookup"><span data-stu-id="a0eb0-145">-Filter</span></span>

<span data-ttu-id="a0eb0-146">Anger ett filter i providerns format eller språk.</span><span class="sxs-lookup"><span data-stu-id="a0eb0-146">Specifies a filter in the provider's format or language.</span></span> <span data-ttu-id="a0eb0-147">Värdet för den här parametern kvalificerar parametern **Path** .</span><span class="sxs-lookup"><span data-stu-id="a0eb0-147">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="a0eb0-148">Syntaxen för filtret, inklusive användning av jokertecken, beror på providern.</span><span class="sxs-lookup"><span data-stu-id="a0eb0-148">The syntax of the filter, including the use of wildcards, depends on the provider.</span></span> <span data-ttu-id="a0eb0-149">Filter är mer effektiva än andra parametrar, eftersom providern tillämpar dem när objekten hämtas, i stället för att ha PowerShell filtrera objekten när de har hämtats.</span><span class="sxs-lookup"><span data-stu-id="a0eb0-149">Filters are more efficient than other parameters, because the provider applies them when getting the objects, rather than having PowerShell filter the objects after they are retrieved.</span></span>

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

### <span data-ttu-id="a0eb0-150">-Inkludera</span><span class="sxs-lookup"><span data-stu-id="a0eb0-150">-Include</span></span>

<span data-ttu-id="a0eb0-151">Hämtar endast de angivna objekten.</span><span class="sxs-lookup"><span data-stu-id="a0eb0-151">Gets only the specified items.</span></span> <span data-ttu-id="a0eb0-152">Värdet för den här parametern kvalificerar parametern **Path** .</span><span class="sxs-lookup"><span data-stu-id="a0eb0-152">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="a0eb0-153">Ange ett Sök vägs element eller ett mönster, till exempel `*.txt` .</span><span class="sxs-lookup"><span data-stu-id="a0eb0-153">Enter a path element or pattern, such as `*.txt`.</span></span> <span data-ttu-id="a0eb0-154">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="a0eb0-154">Wildcards are permitted.</span></span>

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

### <span data-ttu-id="a0eb0-155">-Path</span><span class="sxs-lookup"><span data-stu-id="a0eb0-155">-Path</span></span>

<span data-ttu-id="a0eb0-156">Anger sökvägen till en resurs.</span><span class="sxs-lookup"><span data-stu-id="a0eb0-156">Specifies the path to a resource.</span></span> <span data-ttu-id="a0eb0-157">`Get-Acl` hämtar säkerhets beskrivningen för den resurs som anges av sökvägen.</span><span class="sxs-lookup"><span data-stu-id="a0eb0-157">`Get-Acl` gets the security descriptor of the resource indicated by the path.</span></span> <span data-ttu-id="a0eb0-158">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="a0eb0-158">Wildcards are permitted.</span></span> <span data-ttu-id="a0eb0-159">Om du utelämnar parametern **Path** , `Get-Acl` hämtas säkerhets beskrivningen för den aktuella katalogen.</span><span class="sxs-lookup"><span data-stu-id="a0eb0-159">If you omit the **Path** parameter, `Get-Acl` gets the security descriptor of the current directory.</span></span>

<span data-ttu-id="a0eb0-160">Parameter namnet ("sökväg") är valfritt.</span><span class="sxs-lookup"><span data-stu-id="a0eb0-160">The parameter name ("Path") is optional.</span></span>

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

### <span data-ttu-id="a0eb0-161">-AllCentralAccessPolicies</span><span class="sxs-lookup"><span data-stu-id="a0eb0-161">-AllCentralAccessPolicies</span></span>

<span data-ttu-id="a0eb0-162">Hämtar information om alla centrala åtkomst principer som är aktiverade på datorn.</span><span class="sxs-lookup"><span data-stu-id="a0eb0-162">Gets information about all central access policies that are enabled on the computer.</span></span>

<span data-ttu-id="a0eb0-163">Från och med Windows Server 2012 kan administratörer använda Active Directory och grupprincip för att ange principer för central åtkomst för användare och grupper.</span><span class="sxs-lookup"><span data-stu-id="a0eb0-163">Beginning in Windows Server 2012, administrators can use Active Directory and Group Policy to set central access policies for users and groups.</span></span> <span data-ttu-id="a0eb0-164">Mer information finns i [dynamisk Access Control: Scenario översikt](/windows-server/identity/solution-guides/dynamic-access-control--scenario-overview).</span><span class="sxs-lookup"><span data-stu-id="a0eb0-164">For more information, see [Dynamic Access Control: Scenario Overview](/windows-server/identity/solution-guides/dynamic-access-control--scenario-overview).</span></span>

<span data-ttu-id="a0eb0-165">Den här parametern introduceras i Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="a0eb0-165">This parameter is introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="a0eb0-166">– InputObject</span><span class="sxs-lookup"><span data-stu-id="a0eb0-166">-InputObject</span></span>

<span data-ttu-id="a0eb0-167">Hämtar säkerhets beskrivningen för det angivna objektet.</span><span class="sxs-lookup"><span data-stu-id="a0eb0-167">Gets the security descriptor for the specified object.</span></span> <span data-ttu-id="a0eb0-168">Ange en variabel som innehåller objektet eller ett kommando som hämtar objektet.</span><span class="sxs-lookup"><span data-stu-id="a0eb0-168">Enter a variable that contains the object or a command that gets the object.</span></span>

<span data-ttu-id="a0eb0-169">Det går inte att skicka ett objekt, förutom en sökväg, till `Get-Acl` .</span><span class="sxs-lookup"><span data-stu-id="a0eb0-169">You cannot pipe an object, other than a path, to `Get-Acl`.</span></span> <span data-ttu-id="a0eb0-170">Använd i stället parametern **InputObject** explicit i kommandot.</span><span class="sxs-lookup"><span data-stu-id="a0eb0-170">Instead, use the **InputObject** parameter explicitly in the command.</span></span>

<span data-ttu-id="a0eb0-171">Den här parametern introduceras i Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="a0eb0-171">This parameter is introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="a0eb0-172">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="a0eb0-172">-LiteralPath</span></span>

<span data-ttu-id="a0eb0-173">Anger sökvägen till en resurs.</span><span class="sxs-lookup"><span data-stu-id="a0eb0-173">Specifies the path to a resource.</span></span> <span data-ttu-id="a0eb0-174">Till skillnad från **sökväg** används värdet för parametern **LiteralPath** exakt som det har angetts.</span><span class="sxs-lookup"><span data-stu-id="a0eb0-174">Unlike **Path** , the value of the **LiteralPath** parameter is used exactly as it is typed.</span></span> <span data-ttu-id="a0eb0-175">Inga tecken tolkas som jokertecken.</span><span class="sxs-lookup"><span data-stu-id="a0eb0-175">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="a0eb0-176">Om sökvägen innehåller escape-tecken omger du den med enkla citat tecken.</span><span class="sxs-lookup"><span data-stu-id="a0eb0-176">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="a0eb0-177">Enkla citat tecken säger att PowerShell inte tolkar några tecken som escape-sekvenser.</span><span class="sxs-lookup"><span data-stu-id="a0eb0-177">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

<span data-ttu-id="a0eb0-178">Den här parametern introduceras i Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="a0eb0-178">This parameter is introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="a0eb0-179">– UseTransaction</span><span class="sxs-lookup"><span data-stu-id="a0eb0-179">-UseTransaction</span></span>

<span data-ttu-id="a0eb0-180">Inkluderar kommandot i den aktiva transaktionen.</span><span class="sxs-lookup"><span data-stu-id="a0eb0-180">Includes the command in the active transaction.</span></span>
<span data-ttu-id="a0eb0-181">Den här parametern är bara giltig medan en transaktion pågår.</span><span class="sxs-lookup"><span data-stu-id="a0eb0-181">This parameter is valid only when a transaction is in progress.</span></span>
<span data-ttu-id="a0eb0-182">Mer information finns i about_Transactions.</span><span class="sxs-lookup"><span data-stu-id="a0eb0-182">For more information, see about_Transactions.</span></span>

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

### <span data-ttu-id="a0eb0-183">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="a0eb0-183">CommonParameters</span></span>

<span data-ttu-id="a0eb0-184">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="a0eb0-184">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="a0eb0-185">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="a0eb0-185">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="a0eb0-186">INDATA</span><span class="sxs-lookup"><span data-stu-id="a0eb0-186">INPUTS</span></span>

### <span data-ttu-id="a0eb0-187">System. String</span><span class="sxs-lookup"><span data-stu-id="a0eb0-187">System.String</span></span>

<span data-ttu-id="a0eb0-188">Du kan skicka vidare en sträng som innehåller en sökväg till `Get-Acl` .</span><span class="sxs-lookup"><span data-stu-id="a0eb0-188">You can pipe a string that contains a path to `Get-Acl`.</span></span>

## <span data-ttu-id="a0eb0-189">UTDATA</span><span class="sxs-lookup"><span data-stu-id="a0eb0-189">OUTPUTS</span></span>

### <span data-ttu-id="a0eb0-190">System. Security. AccessControl. FileSecurity, system. Security. AccessControl. DirectorySecurity, system. Security. AccessControl. RegistrySecurity</span><span class="sxs-lookup"><span data-stu-id="a0eb0-190">System.Security.AccessControl.FileSecurity, System.Security.AccessControl.DirectorySecurity, System.Security.AccessControl.RegistrySecurity</span></span>

<span data-ttu-id="a0eb0-191">`Get-Acl` Returnerar ett objekt som representerar de ACL: er som det hämtar.</span><span class="sxs-lookup"><span data-stu-id="a0eb0-191">`Get-Acl` returns an object that represents the ACLs that it gets.</span></span> <span data-ttu-id="a0eb0-192">Objekt typen beror på ACL-typen.</span><span class="sxs-lookup"><span data-stu-id="a0eb0-192">The object type depends upon the ACL type.</span></span>

## <span data-ttu-id="a0eb0-193">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="a0eb0-193">NOTES</span></span>

<span data-ttu-id="a0eb0-194">Som standard `Get-Acl` visar PowerShell-sökvägen till resursen ( `<provider>::<resource-path>` ), ägaren till resursen och "åtkomst", en lista (matris) av åtkomst kontroll POSTERNA i DACL (Discretionary Access Control List) för resursen.</span><span class="sxs-lookup"><span data-stu-id="a0eb0-194">By default, `Get-Acl` displays the PowerShell path to the resource (`<provider>::<resource-path>`), the owner of the resource, and "Access", a list (array) of the access control entries in the discretionary access control list (DACL) for the resource.</span></span> <span data-ttu-id="a0eb0-195">DACL-listan styrs av resurs ägaren.</span><span class="sxs-lookup"><span data-stu-id="a0eb0-195">The DACL list is controlled by the resource owner.</span></span>

<span data-ttu-id="a0eb0-196">När du formaterar resultatet som en lista, ( `Get-Acl | Format-List` ), utöver sökvägen, ägaren och åtkomst listan, visar PowerShell följande egenskaper och egenskaps värden:</span><span class="sxs-lookup"><span data-stu-id="a0eb0-196">When you format the result as a list, (`Get-Acl | Format-List`), in addition to the path, owner, and access list, PowerShell displays the following properties and property values:</span></span>

- <span data-ttu-id="a0eb0-197">**Grupp** : ägarens säkerhets grupp.</span><span class="sxs-lookup"><span data-stu-id="a0eb0-197">**Group** : The security group of the owner.</span></span>
- <span data-ttu-id="a0eb0-198">**Granskning** : en lista (matris) med poster i system åtkomst kontrol listan (SACL).</span><span class="sxs-lookup"><span data-stu-id="a0eb0-198">**Audit** :  A list (array) of entries in the system access control list (SACL).</span></span> <span data-ttu-id="a0eb0-199">SACL anger de typer av åtkomst försök som Windows genererar gransknings poster för.</span><span class="sxs-lookup"><span data-stu-id="a0eb0-199">The SACL specifies the types of access attempts for which Windows generates audit records.</span></span>
- <span data-ttu-id="a0eb0-200">**SDDL** : säkerhets beskrivningen för den resurs som visas i en enskild text sträng i språk format för säkerhets beskrivnings definition.</span><span class="sxs-lookup"><span data-stu-id="a0eb0-200">**Sddl** : The security descriptor of the resource displayed in a single text string in Security Descriptor Definition Language format.</span></span> <span data-ttu-id="a0eb0-201">PowerShell använder **GetSddlForm** -metoden för säkerhets beskrivningar för att hämta dessa data.</span><span class="sxs-lookup"><span data-stu-id="a0eb0-201">PowerShell uses the **GetSddlForm** method of security descriptors to get this data.</span></span>

<span data-ttu-id="a0eb0-202">Eftersom `Get-Acl` stöds av fil systemet och register leverantörer kan du använda `Get-Acl` för att Visa ACL: en för fil system objekt, till exempel filer och kataloger samt register objekt, till exempel register nycklar och poster.</span><span class="sxs-lookup"><span data-stu-id="a0eb0-202">Because `Get-Acl` is supported by the file system and registry providers, you can use `Get-Acl` to view the ACL of file system objects, such as files and directories, and registry objects, such as registry keys and entries.</span></span>

## <span data-ttu-id="a0eb0-203">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="a0eb0-203">RELATED LINKS</span></span>

[<span data-ttu-id="a0eb0-204">Ange ACL</span><span class="sxs-lookup"><span data-stu-id="a0eb0-204">Set-Acl</span></span>](Set-Acl.md)
