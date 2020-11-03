---
external help file: Microsoft.Management.Infrastructure.CimCmdlets.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: CimCmdlets
ms.date: 5/15/2019
online version: https://docs.microsoft.com/powershell/module/cimcmdlets/remove-ciminstance?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Remove-CimInstance
ms.openlocfilehash: ac4435d0bf246273ad21c56ca7640204372d9133
ms.sourcegitcommit: 37abf054ad9eda8813be8ff4487803b10e1842ef
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/23/2020
ms.locfileid: "93268155"
---
# <span data-ttu-id="46f25-103">Remove-CimInstance</span><span class="sxs-lookup"><span data-stu-id="46f25-103">Remove-CimInstance</span></span>

## <span data-ttu-id="46f25-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="46f25-104">SYNOPSIS</span></span>
<span data-ttu-id="46f25-105">Tar bort en CIM-instans från en dator.</span><span class="sxs-lookup"><span data-stu-id="46f25-105">Removes a CIM instance from a computer.</span></span>

## <span data-ttu-id="46f25-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="46f25-106">SYNTAX</span></span>

### <span data-ttu-id="46f25-107">CimInstanceComputerSet (standard)</span><span class="sxs-lookup"><span data-stu-id="46f25-107">CimInstanceComputerSet (Default)</span></span>

```
Remove-CimInstance [-ResourceUri <Uri>] [-ComputerName <String[]>] [-OperationTimeoutSec <UInt32>]
 [-InputObject] <CimInstance> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="46f25-108">CimInstanceSessionSet</span><span class="sxs-lookup"><span data-stu-id="46f25-108">CimInstanceSessionSet</span></span>

```
Remove-CimInstance -CimSession <CimSession[]> [-ResourceUri <Uri>] [-OperationTimeoutSec <UInt32>]
 [-InputObject] <CimInstance> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="46f25-109">QuerySessionSet</span><span class="sxs-lookup"><span data-stu-id="46f25-109">QuerySessionSet</span></span>

```
Remove-CimInstance -CimSession <CimSession[]> [[-Namespace] <String>]
 [-OperationTimeoutSec <UInt32>] [-Query] <String> [-QueryDialect <String>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### <span data-ttu-id="46f25-110">QueryComputerSet</span><span class="sxs-lookup"><span data-stu-id="46f25-110">QueryComputerSet</span></span>

```
Remove-CimInstance [-ComputerName <String[]>] [[-Namespace] <String>]
 [-OperationTimeoutSec <UInt32>] [-Query] <String> [-QueryDialect <String>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## <span data-ttu-id="46f25-111">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="46f25-111">DESCRIPTION</span></span>

<span data-ttu-id="46f25-112">Denna cmdlet tar bort en CIM-instans från en CIM-server.</span><span class="sxs-lookup"><span data-stu-id="46f25-112">This cmdlet removes a CIM instance from a CIM server.</span></span> <span data-ttu-id="46f25-113">Du kan ange CIM-instansen som ska tas bort med antingen ett CIM-instansnamn som hämtats av `Get-CimInstance` cmdleten eller genom att ange en fråga.</span><span class="sxs-lookup"><span data-stu-id="46f25-113">You can specify the CIM instance to remove by using either a CIM instance object retrieved by the `Get-CimInstance` cmdlet, or by specifying a query.</span></span>

<span data-ttu-id="46f25-114">Om parametern **InputObject** inte anges fungerar cmdleten på något av följande sätt:</span><span class="sxs-lookup"><span data-stu-id="46f25-114">If the **InputObject** parameter is not specified, the cmdlet works in one of the following ways:</span></span>

- <span data-ttu-id="46f25-115">Om varken parametern **computername** eller parametern **CimSession** anges, fungerar denna cmdlet på lokala Windows Management Instrumentation (WMI) med en Component Object Model (com)-session.</span><span class="sxs-lookup"><span data-stu-id="46f25-115">If neither the **ComputerName** parameter nor the **CimSession** parameter is specified, then this cmdlet works on local Windows Management Instrumentation (WMI) using a Component Object Model (COM) session.</span></span>
- <span data-ttu-id="46f25-116">Om antingen parametern **computername** eller parametern **CimSession** anges, fungerar denna cmdlet mot CIM-servern som anges av parametern **computername** eller parametern **CimSession** .</span><span class="sxs-lookup"><span data-stu-id="46f25-116">If either the **ComputerName** parameter or the **CimSession** parameter is specified, then this cmdlet works against the CIM server specified by either the **ComputerName** parameter or the **CimSession** parameter.</span></span>

## <span data-ttu-id="46f25-117">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="46f25-117">EXAMPLES</span></span>

### <span data-ttu-id="46f25-118">Exempel 1: ta bort CIM-instansen</span><span class="sxs-lookup"><span data-stu-id="46f25-118">Example 1: Remove the CIM instance</span></span>

<span data-ttu-id="46f25-119">I det här exemplet används **Frågeparametern** för att ta bort CIM-instanser från klassen med namnet **Win32_Environment** som börjar med tecken strängen **testvar** .</span><span class="sxs-lookup"><span data-stu-id="46f25-119">This example use the **Query** parameter to remove CIM instances from the class named **Win32_Environment** that start with the character string **testvar** .</span></span>

```powershell
Remove-CimInstance -Query 'Select * from Win32_Environment where name LIKE "testvar%"'
```

### <span data-ttu-id="46f25-120">Exempel 2: ta bort CIM-instansen med CIM-instansnamnet</span><span class="sxs-lookup"><span data-stu-id="46f25-120">Example 2: Remove the CIM instance using CIM instance object</span></span>

<span data-ttu-id="46f25-121">I det här exemplet hämtas CIM-instansnamnet som filtrerats efter **Frågeparametern** och lagrar dem i variabeln med namnet `$var` med hjälp av `Get-CimInstance` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="46f25-121">This example retrieves the CIM instance objects filtered by the **Query** parameter and stores them in variable named `$var` using the `Get-CimInstance` cmdlet.</span></span> <span data-ttu-id="46f25-122">Innehållet i variabeln skickas sedan till `Remove-CimInstance` cmdleten, som tar bort CIM-instanserna.</span><span class="sxs-lookup"><span data-stu-id="46f25-122">The contents of the variable are then passed to the `Remove-CimInstance` cmdlet, which removes the CIM instances.</span></span>

```powershell
notepad.exe
$var = Get-CimInstance -Query 'Select * from Win32_Process where name LIKE "notepad%"'
Remove-CimInstance -InputObject $var
```

## <span data-ttu-id="46f25-123">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="46f25-123">PARAMETERS</span></span>

### <span data-ttu-id="46f25-124">– CimSession</span><span class="sxs-lookup"><span data-stu-id="46f25-124">-CimSession</span></span>

<span data-ttu-id="46f25-125">Kör kommandot med den angivna CIM-sessionen.</span><span class="sxs-lookup"><span data-stu-id="46f25-125">Runs the command using the specified CIM session.</span></span> <span data-ttu-id="46f25-126">Ange en variabel som innehåller CIM-sessionen, eller ett kommando som skapar eller hämtar CIM-sessionen, t. ex `New-CimSession` . eller- `Get-CimSession` cmdletar.</span><span class="sxs-lookup"><span data-stu-id="46f25-126">Enter a variable that contains the CIM session, or a command that creates or gets the CIM session, such as the `New-CimSession` or `Get-CimSession` cmdlets.</span></span> <span data-ttu-id="46f25-127">Mer information finns i [about_CimSession](../Microsoft.PowerShell.Core/About/about_CimSession.md).</span><span class="sxs-lookup"><span data-stu-id="46f25-127">For more information, see [about_CimSession](../Microsoft.PowerShell.Core/About/about_CimSession.md).</span></span>

```yaml
Type: Microsoft.Management.Infrastructure.CimSession[]
Parameter Sets: CimInstanceSessionSet, QuerySessionSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="46f25-128">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="46f25-128">-ComputerName</span></span>

<span data-ttu-id="46f25-129">Anger namnet på den dator som du vill köra CIM-åtgärden på.</span><span class="sxs-lookup"><span data-stu-id="46f25-129">Specifies the name of the computer on which you want to run the CIM operation.</span></span> <span data-ttu-id="46f25-130">Du kan ange ett fullständigt kvalificerat domän namn (FQDN) eller ett NetBIOS-namn.</span><span class="sxs-lookup"><span data-stu-id="46f25-130">You can specify a fully qualified domain name (FQDN) or a NetBIOS name.</span></span>

<span data-ttu-id="46f25-131">Om du anger den här parametern skapar cmdleten en tillfällig session till den angivna datorn med hjälp av WsMan-protokollet.</span><span class="sxs-lookup"><span data-stu-id="46f25-131">If you specify this parameter, the cmdlet creates a temporary session to the specified computer using the WsMan protocol.</span></span>

<span data-ttu-id="46f25-132">Om du inte anger den här parametern utför cmdleten åtgärden på den lokala datorn med hjälp av Component Object Model (COM).</span><span class="sxs-lookup"><span data-stu-id="46f25-132">If you do not specify this parameter, the cmdlet performs the operation on the local computer using Component Object Model (COM).</span></span>

<span data-ttu-id="46f25-133">Om flera åtgärder utförs på samma dator ger det bättre prestanda om du ansluter med en CIM-session.</span><span class="sxs-lookup"><span data-stu-id="46f25-133">If multiple operations are being performed on the same computer, connecting using a CIM session gives better performance.</span></span>

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

### <span data-ttu-id="46f25-134">– InputObject</span><span class="sxs-lookup"><span data-stu-id="46f25-134">-InputObject</span></span>

<span data-ttu-id="46f25-135">Anger ett CIM-instansnamn som ska tas bort från CIM-servern.</span><span class="sxs-lookup"><span data-stu-id="46f25-135">Specifies a CIM instance object to be removed from the CIM server.</span></span> <span data-ttu-id="46f25-136">Objektet som skickades till cmdleten har inte ändrats. endast instansen i CIM-servern tas bort.</span><span class="sxs-lookup"><span data-stu-id="46f25-136">The object passed to the cmdlet is not changed, only the instance in the CIM server is removed.</span></span>

```yaml
Type: Microsoft.Management.Infrastructure.CimInstance
Parameter Sets: CimInstanceComputerSet, CimInstanceSessionSet
Aliases: CimInstance

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="46f25-137">– Namnrymd</span><span class="sxs-lookup"><span data-stu-id="46f25-137">-Namespace</span></span>

<span data-ttu-id="46f25-138">Anger namn området för CIM-åtgärden.</span><span class="sxs-lookup"><span data-stu-id="46f25-138">Specifies the namespace for the CIM operation.</span></span> <span data-ttu-id="46f25-139">Standard namn området är **rot-/cimv2**.</span><span class="sxs-lookup"><span data-stu-id="46f25-139">The default namespace is **root/cimv2**.</span></span> <span data-ttu-id="46f25-140">Du kan använda TABB-slutförande för att bläddra i listan över namn områden, eftersom PowerShell hämtar en lista över namn områden från den lokala WMI-servern för att tillhandahålla listan över namn områden.</span><span class="sxs-lookup"><span data-stu-id="46f25-140">You can use tab completion to browse the list of namespaces, because PowerShell gets a list of namespaces from the local WMI server to provide the list of namespaces.</span></span>

```yaml
Type: System.String
Parameter Sets: QuerySessionSet, QueryComputerSet
Aliases:

Required: False
Position: 2
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="46f25-141">-OperationTimeoutSec</span><span class="sxs-lookup"><span data-stu-id="46f25-141">-OperationTimeoutSec</span></span>

<span data-ttu-id="46f25-142">Anger hur lång tid cmdleten väntar på ett svar från datorn.</span><span class="sxs-lookup"><span data-stu-id="46f25-142">Specifies the amount of time that the cmdlet waits for a response from the computer.</span></span> <span data-ttu-id="46f25-143">Som standard är värdet för den här parametern 0, vilket innebär att cmdleten använder standardvärdet för timeout för servern.</span><span class="sxs-lookup"><span data-stu-id="46f25-143">By default, the value of this parameter is 0, which means that the cmdlet uses the default timeout value for the server.</span></span>

<span data-ttu-id="46f25-144">Om **OperationTimeoutSec** -parametern har angetts till ett värde som är lägre än det stabila anslutnings försöket på 3 minuter, går det inte att återställa nätverks fel som sist mer än värdet för parametern **OperationTimeoutSec** , eftersom åtgärden på servern överskrider innan klienten kan återansluta.</span><span class="sxs-lookup"><span data-stu-id="46f25-144">If the **OperationTimeoutSec** parameter is set to a value less than the robust connection retry timeout of 3 minutes, network failures that last more than the value of the **OperationTimeoutSec** parameter are not recoverable, because the operation on the server times out before the client can reconnect.</span></span>

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

### <span data-ttu-id="46f25-145">– Fråga</span><span class="sxs-lookup"><span data-stu-id="46f25-145">-Query</span></span>

<span data-ttu-id="46f25-146">Anger en fråga som ska köras på CIM-servern.</span><span class="sxs-lookup"><span data-stu-id="46f25-146">Specifies a query to run on the CIM server.</span></span> <span data-ttu-id="46f25-147">Du kan ange dialekten med hjälp av parametern **QueryDialect** .</span><span class="sxs-lookup"><span data-stu-id="46f25-147">You can specify the query dialect using the **QueryDialect** parameter.</span></span>

<span data-ttu-id="46f25-148">Om det angivna värdet innehåller dubbla citat tecken ("), enkla citat tecken (') eller ett omvänt snedstreck ( \\ ) måste du undanta dessa tecken genom att prefixet med omvänt snedstreck ( \\ ).</span><span class="sxs-lookup"><span data-stu-id="46f25-148">If the value specified contains double quotes ("), single quotes ('), or a backslash (\\), you must escape those characters by prefixing them with the backslash (\\) character.</span></span> <span data-ttu-id="46f25-149">Om värdet som anges använder WQL-operatorn som operator måste du undanta följande tecken genom att omsluta dem inom hak paren tes ( \[ \] ): procent (%), under streck (_) eller inledande hak paren tes ( \[ ).</span><span class="sxs-lookup"><span data-stu-id="46f25-149">If the value specified uses the WQL LIKE operator, then you must escape the following characters by enclosing them in square brackets (\[\]): percent (%), underscore (_), or opening square bracket (\[).</span></span>

```yaml
Type: System.String
Parameter Sets: QuerySessionSet, QueryComputerSet
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="46f25-150">-QueryDialect</span><span class="sxs-lookup"><span data-stu-id="46f25-150">-QueryDialect</span></span>

<span data-ttu-id="46f25-151">Anger frågespråket som används för Frågeparametern.</span><span class="sxs-lookup"><span data-stu-id="46f25-151">Specifies the query language used for the Query parameter.</span></span> <span data-ttu-id="46f25-152">De acceptabla värdena för den här parametern är: **WQL** eller **CQL**.</span><span class="sxs-lookup"><span data-stu-id="46f25-152">The acceptable values for this parameter are: **WQL** or **CQL**.</span></span> <span data-ttu-id="46f25-153">Standardvärdet är **WQL**.</span><span class="sxs-lookup"><span data-stu-id="46f25-153">The default value is **WQL**.</span></span>

```yaml
Type: System.String
Parameter Sets: QuerySessionSet, QueryComputerSet
Aliases:

Required: False
Position: Named
Default value: WQL
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="46f25-154">– ResourceUri</span><span class="sxs-lookup"><span data-stu-id="46f25-154">-ResourceUri</span></span>

<span data-ttu-id="46f25-155">Anger resurs-URI (Uniform Resource Identifier) för resurs klassen eller-instansen.</span><span class="sxs-lookup"><span data-stu-id="46f25-155">Specifies the resource uniform resource identifier (URI) of the resource class or instance.</span></span> <span data-ttu-id="46f25-156">URI: n används för att identifiera en speciell typ av resurs, till exempel diskar eller processer, på en dator.</span><span class="sxs-lookup"><span data-stu-id="46f25-156">The URI is used to identify a specific type of resource, such as disks or processes, on a computer.</span></span>

<span data-ttu-id="46f25-157">En URI består av ett prefix och en sökväg till en resurs.</span><span class="sxs-lookup"><span data-stu-id="46f25-157">A URI consists of a prefix and a path to a resource.</span></span> <span data-ttu-id="46f25-158">Ett exempel:</span><span class="sxs-lookup"><span data-stu-id="46f25-158">For example:</span></span>

- `http://schemas.microsoft.com/wbem/wsman/1/wmi/root/cimv2/Win32_LogicalDisk`
- `http://intel.com/wbem/wscim/1/amt-schema/1/AMT_GeneralSettings`

<span data-ttu-id="46f25-159">Om du inte anger den här parametern används DMTF-standardresurs-URI som standard `http://schemas.dmtf.org/wbem/wscim/1/cim-schema/2/` och klass namnet läggs till i den.</span><span class="sxs-lookup"><span data-stu-id="46f25-159">By default, if you do not specify this parameter, the DMTF standard resource URI `http://schemas.dmtf.org/wbem/wscim/1/cim-schema/2/` is used and the class name is appended to it.</span></span>

<span data-ttu-id="46f25-160">ResourceURI kan endast användas med CIM-sessioner som skapats med WSMan-protokollet, eller när du anger parametern ComputerName, som skapar en CIM-session med hjälp av WSMan.</span><span class="sxs-lookup"><span data-stu-id="46f25-160">ResourceURI can only be used with CIM sessions created using the WSMan protocol, or when specifying the ComputerName parameter, which creates a CIM session using WSMan.</span></span> <span data-ttu-id="46f25-161">Om du anger den här parametern utan att ange parametern ComputerName, eller om du anger en CIM-session som skapats med DCOM-protokollet, får du ett fel meddelande eftersom DCOM-protokollet inte stöder parametern ResourceURI.</span><span class="sxs-lookup"><span data-stu-id="46f25-161">If you specify this parameter without specifying the ComputerName parameter, or if you specify a CIM session created using DCOM protocol, you will get an error, because the DCOM protocol does not support the ResourceURI parameter.</span></span>

<span data-ttu-id="46f25-162">Om både den **ResourceUri** -parametern och **filter** parametern anges, ignoreras **filter** parametern.</span><span class="sxs-lookup"><span data-stu-id="46f25-162">If both the **ResourceUri** parameter and the **Filter** parameter are specified, the **Filter** parameter is ignored.</span></span>

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

### <span data-ttu-id="46f25-163">-Confirm</span><span class="sxs-lookup"><span data-stu-id="46f25-163">-Confirm</span></span>

<span data-ttu-id="46f25-164">Uppmanar dig att bekräfta innan du kör cmdleten.</span><span class="sxs-lookup"><span data-stu-id="46f25-164">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="46f25-165">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="46f25-165">-WhatIf</span></span>

<span data-ttu-id="46f25-166">Visar vad som skulle hända om cmdleten kördes.</span><span class="sxs-lookup"><span data-stu-id="46f25-166">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="46f25-167">Cmdleten körs inte.</span><span class="sxs-lookup"><span data-stu-id="46f25-167">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="46f25-168">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="46f25-168">CommonParameters</span></span>

<span data-ttu-id="46f25-169">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="46f25-169">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="46f25-170">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="46f25-170">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="46f25-171">INDATA</span><span class="sxs-lookup"><span data-stu-id="46f25-171">INPUTS</span></span>

### <span data-ttu-id="46f25-172">Inget</span><span class="sxs-lookup"><span data-stu-id="46f25-172">None</span></span>

<span data-ttu-id="46f25-173">Denna cmdlet accepterar inga inobjekt.</span><span class="sxs-lookup"><span data-stu-id="46f25-173">This cmdlet accepts no input objects.</span></span>

## <span data-ttu-id="46f25-174">UTDATA</span><span class="sxs-lookup"><span data-stu-id="46f25-174">OUTPUTS</span></span>

### <span data-ttu-id="46f25-175">Inget</span><span class="sxs-lookup"><span data-stu-id="46f25-175">None</span></span>

<span data-ttu-id="46f25-176">Denna cmdlet genererar inga utdata.</span><span class="sxs-lookup"><span data-stu-id="46f25-176">This cmdlet produces no outputs.</span></span>

## <span data-ttu-id="46f25-177">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="46f25-177">NOTES</span></span>

## <span data-ttu-id="46f25-178">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="46f25-178">RELATED LINKS</span></span>

[<span data-ttu-id="46f25-179">New-CimInstance</span><span class="sxs-lookup"><span data-stu-id="46f25-179">New-CimInstance</span></span>](New-CimInstance.md)

[<span data-ttu-id="46f25-180">Get-CimInstance</span><span class="sxs-lookup"><span data-stu-id="46f25-180">Get-CimInstance</span></span>](get-ciminstance.md)

[<span data-ttu-id="46f25-181">Set-CimInstance</span><span class="sxs-lookup"><span data-stu-id="46f25-181">Set-CimInstance</span></span>](Set-CimInstance.md)
