---
external help file: Microsoft.Management.Infrastructure.CimCmdlets.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: CimCmdlets
ms.date: 5/15/2019
online version: https://docs.microsoft.com/powershell/module/cimcmdlets/set-ciminstance?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-CimInstance
ms.openlocfilehash: 7f44ddf52c2ad3ce68c5eccf0e8f952a0fa1873e
ms.sourcegitcommit: 37abf054ad9eda8813be8ff4487803b10e1842ef
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/23/2020
ms.locfileid: "93268107"
---
# <span data-ttu-id="03eff-103">Set-CimInstance</span><span class="sxs-lookup"><span data-stu-id="03eff-103">Set-CimInstance</span></span>

## <span data-ttu-id="03eff-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="03eff-104">SYNOPSIS</span></span>
<span data-ttu-id="03eff-105">Ändrar en CIM-instans på en CIM-server genom att anropa ModifyInstance-metoden för CIM-klassen.</span><span class="sxs-lookup"><span data-stu-id="03eff-105">Modifies a CIM instance on a CIM server by calling the ModifyInstance method of the CIM class.</span></span>

## <span data-ttu-id="03eff-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="03eff-106">SYNTAX</span></span>

### <span data-ttu-id="03eff-107">CimInstanceComputerSet (standard)</span><span class="sxs-lookup"><span data-stu-id="03eff-107">CimInstanceComputerSet (Default)</span></span>

```
Set-CimInstance [-ComputerName <String[]>] [-ResourceUri <Uri>] [-OperationTimeoutSec <UInt32>]
 [-InputObject] <CimInstance> [-Property <IDictionary>] [-PassThru] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### <span data-ttu-id="03eff-108">CimInstanceSessionSet</span><span class="sxs-lookup"><span data-stu-id="03eff-108">CimInstanceSessionSet</span></span>

```
Set-CimInstance -CimSession <CimSession[]> [-ResourceUri <Uri>] [-OperationTimeoutSec <UInt32>]
 [-InputObject] <CimInstance> [-Property <IDictionary>] [-PassThru] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### <span data-ttu-id="03eff-109">QuerySessionSet</span><span class="sxs-lookup"><span data-stu-id="03eff-109">QuerySessionSet</span></span>

```
Set-CimInstance -CimSession <CimSession[]> [-Namespace <String>] [-OperationTimeoutSec <UInt32>]
 [-Query] <String> [-QueryDialect <String>] -Property <IDictionary> [-PassThru] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### <span data-ttu-id="03eff-110">QueryComputerSet</span><span class="sxs-lookup"><span data-stu-id="03eff-110">QueryComputerSet</span></span>

```
Set-CimInstance [-ComputerName <String[]>] [-Namespace <String>] [-OperationTimeoutSec <UInt32>]
 [-Query] <String> [-QueryDialect <String>] -Property <IDictionary> [-PassThru] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## <span data-ttu-id="03eff-111">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="03eff-111">DESCRIPTION</span></span>

<span data-ttu-id="03eff-112">Denna cmdlet ändrar en CIM-instans på en CIM-server.</span><span class="sxs-lookup"><span data-stu-id="03eff-112">This cmdlet modifies a CIM instance on a CIM server.</span></span>

<span data-ttu-id="03eff-113">Om parametern **InputObject** inte anges fungerar cmdleten på något av följande sätt:</span><span class="sxs-lookup"><span data-stu-id="03eff-113">If the **InputObject** parameter is not specified, the cmdlet works in one of the following ways:</span></span>

- <span data-ttu-id="03eff-114">Om varken parametern **computername** eller parametern **CimSession** anges, fungerar denna cmdlet på lokala Windows Management Instrumentation (WMI) med en Component Object Model (com)-session.</span><span class="sxs-lookup"><span data-stu-id="03eff-114">If neither the **ComputerName** parameter nor the **CimSession** parameter is specified, then this cmdlet works on local Windows Management Instrumentation (WMI) using a Component Object Model (COM) session.</span></span>
- <span data-ttu-id="03eff-115">Om antingen parametern **computername** eller parametern **CimSession** anges, fungerar denna cmdlet mot CIM-servern som anges av parametern **computername** eller parametern **CimSession** .</span><span class="sxs-lookup"><span data-stu-id="03eff-115">If either the **ComputerName** parameter or the **CimSession** parameter is specified, then this cmdlet works against the CIM server specified by either the **ComputerName** parameter or the **CimSession** parameter.</span></span>

<span data-ttu-id="03eff-116">Om parametern **InputObject** anges fungerar cmdleten på något av följande sätt:</span><span class="sxs-lookup"><span data-stu-id="03eff-116">If the **InputObject** parameter is specified, the cmdlet works in one of the following ways:</span></span>

- <span data-ttu-id="03eff-117">Om varken parametern **computername** eller parametern **CimSession** anges, använder denna cmdlet CIM-sessionen eller dator namnet från det indata-objektet.</span><span class="sxs-lookup"><span data-stu-id="03eff-117">If neither the **ComputerName** parameter nor the **CimSession** parameter is specified, then this cmdlet uses the CIM session or computer name from the input object.</span></span>
- <span data-ttu-id="03eff-118">Om antingen parametern **computername** eller parametern **CimSession** anges använder den här cmdleten antingen parametern **CimSession** eller värdet **computername** .</span><span class="sxs-lookup"><span data-stu-id="03eff-118">If the either the **ComputerName** parameter or the **CimSession** parameter is specified, then this cmdlet uses the either the **CimSession** parameter value or **ComputerName** parameter value.</span></span> <span data-ttu-id="03eff-119">Detta är inte särskilt vanligt.</span><span class="sxs-lookup"><span data-stu-id="03eff-119">This is not very common.</span></span>

## <span data-ttu-id="03eff-120">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="03eff-120">EXAMPLES</span></span>

### <span data-ttu-id="03eff-121">Exempel 1: Ange CIM-instansen</span><span class="sxs-lookup"><span data-stu-id="03eff-121">Example 1: Set the CIM instance</span></span>

<span data-ttu-id="03eff-122">I det här exemplet anges värdet för egenskapen **VariableValue** till **ABCD** med **Frågeparametern** .</span><span class="sxs-lookup"><span data-stu-id="03eff-122">This example sets the value of the **VariableValue** property to **abcd** using the **Query** parameter.</span></span> <span data-ttu-id="03eff-123">Du kan ändra instanser som matchar en WQL-fråga (Windows Management Instrumentation Query Language).</span><span class="sxs-lookup"><span data-stu-id="03eff-123">You can modify instances matching a Windows Management Instrumentation Query Language (WQL) query.</span></span>

```powershell
Set-CimInstance -Query 'Select * from Win32_Environment where name LIKE "testvar%"' -Property @{VariableValue="abcd"}
```

### <span data-ttu-id="03eff-124">Exempel 2: Ange CIM instance-egenskapen med pipelinen</span><span class="sxs-lookup"><span data-stu-id="03eff-124">Example 2: Set the CIM instance property using pipeline</span></span>

<span data-ttu-id="03eff-125">I det här exemplet hämtas CIM-instansnamnet som filtrerats av **Frågeparametern** med `Get-CimInstance` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="03eff-125">This example retrieves the CIM instance object filtered by the **Query** parameter using the `Get-CimInstance` cmdlet.</span></span> <span data-ttu-id="03eff-126">`Set-CimInstance`Cmdleten ändrar värdet för egenskapen **VariableValue** till **ABCD**.</span><span class="sxs-lookup"><span data-stu-id="03eff-126">The `Set-CimInstance` cmdlet modifies the value of **VariableValue** property to **abcd**.</span></span>

```powershell
Get-CimInstance -Query 'Select * from Win32_Environment where name LIKE "testvar%"' |
  Set-CimInstance -Property @{VariableValue="abcd"}
```

### <span data-ttu-id="03eff-127">Exempel 3: Ange CIM instance-egenskapen med indatamängds objekt</span><span class="sxs-lookup"><span data-stu-id="03eff-127">Example 3: Set the CIM instance property using input object</span></span>

```powershell
$x = Get-CimInstance -Query 'Select * from Win32_Environment where Name="testvar"'
Set-CimInstance -InputObject $x -Property @{VariableValue="somevalue"} -PassThru
```

<span data-ttu-id="03eff-128">I det här exemplet hämtas CIM-instansnamnet som filtrerats efter frågeparametern i till en variabel `$x` med `Get-CimInstance` och skickar sedan innehållet i variabeln till- `Set-CimInstance` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="03eff-128">This example retrieves the CIM instance objects filtered by the Query parameter in to a variable `$x` using `Get-CimInstance`, and then passes the contents of the variable to the `Set-CimInstance` cmdlet.</span></span> <span data-ttu-id="03eff-129">`Set-CimInstance` ändrar sedan egenskapen **VariableValue** till **someValue**.</span><span class="sxs-lookup"><span data-stu-id="03eff-129">`Set-CimInstance` then modifies the **VariableValue** property to **somevalue**.</span></span> <span data-ttu-id="03eff-130">Eftersom parametern **Passthru** används, returnerar det här exemplet ett ändrat CIM-instansnamn.</span><span class="sxs-lookup"><span data-stu-id="03eff-130">Because the **Passthru** parameter is used, This example returns a modified CIM instance object.</span></span>

### <span data-ttu-id="03eff-131">Exempel 4: Ange CIM instance-egenskapen</span><span class="sxs-lookup"><span data-stu-id="03eff-131">Example 4: Set the CIM instance property</span></span>

<span data-ttu-id="03eff-132">I det här exemplet hämtas CIM instance-objektet som anges i **Frågeparametern** till en variabel `$x` med hjälp av `Get-CimInstance` cmdleten, och egenskapen **VariableValue** för objektet ändras.</span><span class="sxs-lookup"><span data-stu-id="03eff-132">This example retrieves the CIM instance object that is specified in the **Query** parameter into a variable `$x` using the `Get-CimInstance` cmdlet, and changes the **VariableValue** property value of the object to change.</span></span> <span data-ttu-id="03eff-133">CIM instans-objektet sparas sedan med `Set-CimInstance` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="03eff-133">The CIM instance object is then saved using the `Set-CimInstance` cmdlet.</span></span>
<span data-ttu-id="03eff-134">Eftersom parametern **Passthru** används, returnerar det här exemplet ett ändrat CIM-instansnamn.</span><span class="sxs-lookup"><span data-stu-id="03eff-134">Because the **Passthru** parameter is used, This example returns a modified CIM instance object.</span></span>

```powershell
$x = Get-CimInstance -Query 'Select * from Win32_Environment where name="testvar"'
$x.VariableValue = "Change"
Set-CimInstance -CimInstance $x -PassThru
```

### <span data-ttu-id="03eff-135">Exempel 5: Visa listan över CIM-instanser som ska ändras med WhatIf</span><span class="sxs-lookup"><span data-stu-id="03eff-135">Example 5: Show the list of CIM instances to modify using WhatIf</span></span>

<span data-ttu-id="03eff-136">I det här exemplet används den gemensamma parametern **whatIf** för att ange att ändringen inte ska göras, men endast utdata som skulle inträffa om den är färdig.</span><span class="sxs-lookup"><span data-stu-id="03eff-136">This example uses the common parameter **WhatIf** to specify that the modification should not be done, but only output what would happen if it were done.</span></span>

```powershell
Set-CimInstance -Query 'Select * from Win32_Environment where name LIKE "testvar%"' -Property @{VariableValue="abcd"} -WhatIf
```

### <span data-ttu-id="03eff-137">Exempel 6: Ange CIM-instansen efter bekräftelse från användaren</span><span class="sxs-lookup"><span data-stu-id="03eff-137">Example 6: Set the CIM instance after confirmation from the user</span></span>

<span data-ttu-id="03eff-138">I det här exemplet används den gemensamma parametern **Bekräfta** för att ange att ändringen endast ska utföras efter bekräftelse från användaren.</span><span class="sxs-lookup"><span data-stu-id="03eff-138">This example uses the common parameter **Confirm** to specify that the modification should be done only after confirmation from the user.</span></span>

```powershell
Set-CimInstance -Query 'Select * from Win32_Environment where name LIKE "testvar%"' -Property @{VariableValue="abcd"} -Confirm
```

### <span data-ttu-id="03eff-139">Exempel 7: Ange den skapade CIM-instansen</span><span class="sxs-lookup"><span data-stu-id="03eff-139">Example 7: Set the created CIM instance</span></span>

<span data-ttu-id="03eff-140">Det här exemplet skapar en CIM-instans med de angivna egenskaperna med hjälp av `New-CimInstance` cmdleten och hämtar dess innehåll i en variabel `$x` .</span><span class="sxs-lookup"><span data-stu-id="03eff-140">This example creates a CIM instance with the specified properties using the `New-CimInstance` cmdlet, and retrieves its contents in to a variable `$x`.</span></span> <span data-ttu-id="03eff-141">Variabeln skickas sedan till `Set-CimInstance` cmdleten, som ändrar värdet för egenskapen **VariableValue** till **someValue**.</span><span class="sxs-lookup"><span data-stu-id="03eff-141">The variable is then passed to the `Set-CimInstance` cmdlet, which modifies the value of **VariableValue** property to **somevalue**.</span></span>
<span data-ttu-id="03eff-142">Eftersom parametern **Passthru** används, returnerar det här exemplet ett ändrat CIM-instansnamn.</span><span class="sxs-lookup"><span data-stu-id="03eff-142">Because the **Passthru** parameter is used, This example returns a modified CIM instance object.</span></span>

```powershell
$x = New-CimInstance -ClassName Win32_Environment -Property @{Name="testvar";UserName="domain\user"} -Keys Name,UserName -ClientOnly
Set-CimInstance -CimInstance $x -Property @{VariableValue="somevalue"} -PassThru
```

## <span data-ttu-id="03eff-143">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="03eff-143">PARAMETERS</span></span>

### <span data-ttu-id="03eff-144">– CimSession</span><span class="sxs-lookup"><span data-stu-id="03eff-144">-CimSession</span></span>

<span data-ttu-id="03eff-145">Kör cmdletarna på en fjärrdator.</span><span class="sxs-lookup"><span data-stu-id="03eff-145">Runs the cmdlets on a remote computer.</span></span> <span data-ttu-id="03eff-146">Ange ett dator namn eller ett sessionsobjekt, till exempel utdata för en- `New-CimSession` eller- `Get-CimSession` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="03eff-146">Enter a computer name or a session object, such as the output of a `New-CimSession` or `Get-CimSession` cmdlet.</span></span>

```yaml
Type: Microsoft.Management.Infrastructure.CimSession[]
Parameter Sets: QuerySessionSet, CimInstanceSessionSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="03eff-147">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="03eff-147">-ComputerName</span></span>

<span data-ttu-id="03eff-148">Anger namnet på den dator som du vill köra CIM-åtgärden på.</span><span class="sxs-lookup"><span data-stu-id="03eff-148">Specifies the name of the computer on which you want to run the CIM operation.</span></span> <span data-ttu-id="03eff-149">Du kan ange ett fullständigt kvalificerat domän namn (FQDN) eller ett NetBIOS-namn.</span><span class="sxs-lookup"><span data-stu-id="03eff-149">You can specify a fully qualified domain name (FQDN) or a NetBIOS name.</span></span>

<span data-ttu-id="03eff-150">Om du inte anger den här parametern utför cmdleten åtgärden på den lokala datorn med hjälp av Component Object Model (COM).</span><span class="sxs-lookup"><span data-stu-id="03eff-150">If you do not specify this parameter, the cmdlet performs the operation on the local computer using Component Object Model (COM).</span></span>

<span data-ttu-id="03eff-151">Om du anger den här parametern skapar cmdleten en tillfällig session till den angivna datorn med hjälp av WsMan-protokollet.</span><span class="sxs-lookup"><span data-stu-id="03eff-151">If you specify this parameter, the cmdlet creates a temporary session to the specified computer using the WsMan protocol.</span></span>

<span data-ttu-id="03eff-152">Om flera åtgärder utförs på samma dator ger det bättre prestanda om du ansluter med en CIM-session.</span><span class="sxs-lookup"><span data-stu-id="03eff-152">If multiple operations are being performed on the same computer, connecting using a CIM session gives better performance.</span></span>

```yaml
Type: System.String[]
Parameter Sets: CimInstanceComputerSet, QueryComputerSet
Aliases: CN, ServerName

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="03eff-153">– InputObject</span><span class="sxs-lookup"><span data-stu-id="03eff-153">-InputObject</span></span>

<span data-ttu-id="03eff-154">Anger ett CIM-instansnamn som ska användas som indatakälla.</span><span class="sxs-lookup"><span data-stu-id="03eff-154">Specifies a CIM instance object to use as input.</span></span>

```yaml
Type: Microsoft.Management.Infrastructure.CimInstance
Parameter Sets: CimInstanceComputerSet, CimInstanceSessionSet
Aliases: CimInstance

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="03eff-155">– Namnrymd</span><span class="sxs-lookup"><span data-stu-id="03eff-155">-Namespace</span></span>

<span data-ttu-id="03eff-156">Anger namn området för CIM-åtgärden.</span><span class="sxs-lookup"><span data-stu-id="03eff-156">Specifies the namespace for the CIM operation.</span></span> <span data-ttu-id="03eff-157">Standard namn området är rot-/cimv2.</span><span class="sxs-lookup"><span data-stu-id="03eff-157">The default namespace is root/cimv2.</span></span> <span data-ttu-id="03eff-158">Du kan använda TABB-slutförande för att bläddra i listan över namn områden, eftersom PowerShell hämtar en lista över namn områden från den lokala WMI-servern för att tillhandahålla listan över namn områden.</span><span class="sxs-lookup"><span data-stu-id="03eff-158">You can use tab completion to browse the list of namespaces, because PowerShell gets a list of namespaces from the local WMI server to provide the list of namespaces.</span></span>

```yaml
Type: System.String
Parameter Sets: QuerySessionSet, QueryComputerSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="03eff-159">-OperationTimeoutSec</span><span class="sxs-lookup"><span data-stu-id="03eff-159">-OperationTimeoutSec</span></span>

<span data-ttu-id="03eff-160">Anger hur lång tid cmdleten väntar på ett svar från datorn.</span><span class="sxs-lookup"><span data-stu-id="03eff-160">Specifies the amount of time that the cmdlet waits for a response from the computer.</span></span> <span data-ttu-id="03eff-161">Som standard är värdet för den här parametern 0, vilket innebär att cmdleten använder standardvärdet för timeout för servern.</span><span class="sxs-lookup"><span data-stu-id="03eff-161">By default, the value of this parameter is 0, which means that the cmdlet uses the default timeout value for the server.</span></span>

<span data-ttu-id="03eff-162">Om **OperationTimeoutSec** -parametern har angetts till ett värde som är lägre än det stabila anslutnings försöket på 3 minuter, går det inte att återställa nätverks fel som sist mer än värdet för parametern **OperationTimeoutSec** , eftersom åtgärden på servern överskrider innan klienten kan återansluta.</span><span class="sxs-lookup"><span data-stu-id="03eff-162">If the **OperationTimeoutSec** parameter is set to a value less than the robust connection retry timeout of 3 minutes, network failures that last more than the value of the **OperationTimeoutSec** parameter are not recoverable, because the operation on the server times out before the client can reconnect.</span></span>

```yaml
Type: System.UInt32
Parameter Sets: (All)
Aliases: OT

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="03eff-163">– PassThru</span><span class="sxs-lookup"><span data-stu-id="03eff-163">-PassThru</span></span>

<span data-ttu-id="03eff-164">Returnerar ett objekt som representerar det objekt som du arbetar med.</span><span class="sxs-lookup"><span data-stu-id="03eff-164">Returns an object representing the item with which you are working.</span></span> <span data-ttu-id="03eff-165">Som standard genererar denna cmdlet inga utdata.</span><span class="sxs-lookup"><span data-stu-id="03eff-165">By default, this cmdlet does not generate any output.</span></span>

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

### <span data-ttu-id="03eff-166">– Egenskap</span><span class="sxs-lookup"><span data-stu-id="03eff-166">-Property</span></span>

<span data-ttu-id="03eff-167">Anger egenskaperna för CIM-instansen som en hash-tabell (med namn-värdepar).</span><span class="sxs-lookup"><span data-stu-id="03eff-167">Specifies the properties of the CIM instance as a hash table (using name-value pairs).</span></span> <span data-ttu-id="03eff-168">Endast de egenskaper som anges med den här parametern ändras.</span><span class="sxs-lookup"><span data-stu-id="03eff-168">Only the properties specified using this parameter are changed.</span></span> <span data-ttu-id="03eff-169">Andra egenskaper för CIM-instansen ändras inte.</span><span class="sxs-lookup"><span data-stu-id="03eff-169">Other properties of the CIM instance are not changed.</span></span>

```yaml
Type: System.Collections.IDictionary
Parameter Sets: CimInstanceComputerSet, CimInstanceSessionSet, QuerySessionSet, QueryComputerSet
Aliases: Arguments

Required: True (QuerySessionSet, QueryComputerSet), False (CimInstanceComputerSet, CimInstanceSessionSet)
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="03eff-170">– Fråga</span><span class="sxs-lookup"><span data-stu-id="03eff-170">-Query</span></span>

<span data-ttu-id="03eff-171">Anger en fråga som ska köras på CIM-servern för att hämta CIM-instanser som cmdleten ska köras på.</span><span class="sxs-lookup"><span data-stu-id="03eff-171">Specifies a query to run on the CIM server to retrieve CIM instances on which to run the cmdlet.</span></span> <span data-ttu-id="03eff-172">Du kan ange dialekten med hjälp av parametern QueryDialect.</span><span class="sxs-lookup"><span data-stu-id="03eff-172">You can specify the query dialect using the QueryDialect parameter.</span></span>

<span data-ttu-id="03eff-173">Om det angivna värdet innehåller dubbla citat tecken ( `"` ), enkla citat tecken ( `'` ) eller ett omvänt snedstreck ( `\` ) måste du undanta dessa tecken genom att prefixet med omvänt snedstreck ( `\` ).</span><span class="sxs-lookup"><span data-stu-id="03eff-173">If the value specified contains double quotes (`"`), single quotes (`'`), or a backslash (`\`), you must escape those characters by prefixing them with the backslash (`\`) character.</span></span> <span data-ttu-id="03eff-174">Om värdet som anges använder WQL-operatorn **som** operator måste du undanta följande tecken genom att omsluta dem inom hak paren tes ( `[]` ): procent ( `%` ), under streck ( `_` ) eller inledande hak paren tes ( `[` ).</span><span class="sxs-lookup"><span data-stu-id="03eff-174">If the value specified uses the WQL **LIKE** operator, then you must escape the following characters by enclosing them in square brackets (`[]`): percent (`%`), underscore (`_`), or opening square bracket (`[`).</span></span>

```yaml
Type: System.String
Parameter Sets: QuerySessionSet, QueryComputerSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="03eff-175">-QueryDialect</span><span class="sxs-lookup"><span data-stu-id="03eff-175">-QueryDialect</span></span>

<span data-ttu-id="03eff-176">Anger frågespråket som används för Frågeparametern.</span><span class="sxs-lookup"><span data-stu-id="03eff-176">Specifies the query language used for the Query parameter.</span></span> <span data-ttu-id="03eff-177">De acceptabla värdena för den här parametern är: **WQL** eller **CQL**.</span><span class="sxs-lookup"><span data-stu-id="03eff-177">The acceptable values for this parameter are: **WQL** or **CQL**.</span></span> <span data-ttu-id="03eff-178">Standardvärdet är **WQL**.</span><span class="sxs-lookup"><span data-stu-id="03eff-178">The default value is **WQL**.</span></span>

```yaml
Type: System.String
Parameter Sets: QuerySessionSet, QueryComputerSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="03eff-179">– ResourceUri</span><span class="sxs-lookup"><span data-stu-id="03eff-179">-ResourceUri</span></span>

<span data-ttu-id="03eff-180">Anger resurs-URI (Uniform Resource Identifier) för resurs klassen eller-instansen.</span><span class="sxs-lookup"><span data-stu-id="03eff-180">Specifies the resource uniform resource identifier (URI) of the resource class or instance.</span></span> <span data-ttu-id="03eff-181">URI: n används för att identifiera en speciell typ av resurs, till exempel diskar eller processer, på en dator.</span><span class="sxs-lookup"><span data-stu-id="03eff-181">The URI is used to identify a specific type of resource, such as disks or processes, on a computer.</span></span>

<span data-ttu-id="03eff-182">En URI består av ett prefix och en sökväg till en resurs.</span><span class="sxs-lookup"><span data-stu-id="03eff-182">A URI consists of a prefix and a path to a resource.</span></span> <span data-ttu-id="03eff-183">Ett exempel:</span><span class="sxs-lookup"><span data-stu-id="03eff-183">For example:</span></span>

- `http://schemas.microsoft.com/wbem/wsman/1/wmi/root/cimv2/Win32_LogicalDisk`
- `http://intel.com/wbem/wscim/1/amt-schema/1/AMT_GeneralSettings`

<span data-ttu-id="03eff-184">Om du inte anger den här parametern används DMTF-standardresurs-URI som standard `http://schemas.dmtf.org/wbem/wscim/1/cim-schema/2/` och klass namnet läggs till i den.</span><span class="sxs-lookup"><span data-stu-id="03eff-184">By default, if you do not specify this parameter, the DMTF standard resource URI `http://schemas.dmtf.org/wbem/wscim/1/cim-schema/2/` is used and the class name is appended to it.</span></span>

<span data-ttu-id="03eff-185">ResourceURI kan endast användas med CIM-sessioner som skapats med WSMan-protokollet, eller när du anger parametern ComputerName, som skapar en CIM-session med hjälp av WSMan.</span><span class="sxs-lookup"><span data-stu-id="03eff-185">ResourceURI can only be used with CIM sessions created using the WSMan protocol, or when specifying the ComputerName parameter, which creates a CIM session using WSMan.</span></span> <span data-ttu-id="03eff-186">Om du anger den här parametern utan att ange parametern ComputerName, eller om du anger en CIM-session som skapats med DCOM-protokollet, får du ett fel meddelande eftersom DCOM-protokollet inte stöder parametern ResourceURI.</span><span class="sxs-lookup"><span data-stu-id="03eff-186">If you specify this parameter without specifying the ComputerName parameter, or if you specify a CIM session created using DCOM protocol, you will get an error, because the DCOM protocol does not support the ResourceURI parameter.</span></span>

<span data-ttu-id="03eff-187">Om både den **ResourceUri** -parametern och **filter** parametern anges, ignoreras **filter** parametern.</span><span class="sxs-lookup"><span data-stu-id="03eff-187">If both the **ResourceUri** parameter and the **Filter** parameter are specified, the **Filter** parameter is ignored.</span></span>

```yaml
Type: System.Uri
Parameter Sets: CimInstanceComputerSet, CimInstanceSessionSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="03eff-188">-Confirm</span><span class="sxs-lookup"><span data-stu-id="03eff-188">-Confirm</span></span>

<span data-ttu-id="03eff-189">Uppmanar dig att bekräfta innan du kör cmdleten.</span><span class="sxs-lookup"><span data-stu-id="03eff-189">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="03eff-190">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="03eff-190">-WhatIf</span></span>

<span data-ttu-id="03eff-191">Visar vad som skulle hända om cmdleten kördes.</span><span class="sxs-lookup"><span data-stu-id="03eff-191">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="03eff-192">Cmdleten körs inte.</span><span class="sxs-lookup"><span data-stu-id="03eff-192">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="03eff-193">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="03eff-193">CommonParameters</span></span>

<span data-ttu-id="03eff-194">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="03eff-194">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="03eff-195">Mer information finns i [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span><span class="sxs-lookup"><span data-stu-id="03eff-195">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="03eff-196">INDATA</span><span class="sxs-lookup"><span data-stu-id="03eff-196">INPUTS</span></span>

### <span data-ttu-id="03eff-197">Microsoft. Management. Infrastructure. CimInstance</span><span class="sxs-lookup"><span data-stu-id="03eff-197">Microsoft.Management.Infrastructure.CimInstance</span></span>

## <span data-ttu-id="03eff-198">UTDATA</span><span class="sxs-lookup"><span data-stu-id="03eff-198">OUTPUTS</span></span>

### <span data-ttu-id="03eff-199">Microsoft. Management. Infrastructure. CimInstance</span><span class="sxs-lookup"><span data-stu-id="03eff-199">Microsoft.Management.Infrastructure.CimInstance</span></span>

<span data-ttu-id="03eff-200">När parametern **Passthru** anges returnerar denna cmdlet ett ändrat CIM-instansnamn.</span><span class="sxs-lookup"><span data-stu-id="03eff-200">When the **Passthru** parameter is specified, this cmdlet returns a modified CIM instance object.</span></span>

## <span data-ttu-id="03eff-201">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="03eff-201">NOTES</span></span>

## <span data-ttu-id="03eff-202">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="03eff-202">RELATED LINKS</span></span>

[<span data-ttu-id="03eff-203">Get-CimInstance</span><span class="sxs-lookup"><span data-stu-id="03eff-203">Get-CimInstance</span></span>](get-ciminstance.md)

[<span data-ttu-id="03eff-204">New-CimInstance</span><span class="sxs-lookup"><span data-stu-id="03eff-204">New-CimInstance</span></span>](New-CimInstance.md)

[<span data-ttu-id="03eff-205">Remove-CimInstance</span><span class="sxs-lookup"><span data-stu-id="03eff-205">Remove-CimInstance</span></span>](remove-ciminstance.md)
