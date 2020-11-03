---
external help file: Microsoft.Management.Infrastructure.CimCmdlets.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: CimCmdlets
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/cimcmdlets/get-cimassociatedinstance?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-CimAssociatedInstance
ms.openlocfilehash: c00507460cb80121c0fc8fc246d7fb3f7d7fe0f3
ms.sourcegitcommit: 37abf054ad9eda8813be8ff4487803b10e1842ef
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/23/2020
ms.locfileid: "93268658"
---
# <span data-ttu-id="ace21-103">Get-CimAssociatedInstance</span><span class="sxs-lookup"><span data-stu-id="ace21-103">Get-CimAssociatedInstance</span></span>

## <span data-ttu-id="ace21-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="ace21-104">SYNOPSIS</span></span>
<span data-ttu-id="ace21-105">Hämtar CIM-instanser som är anslutna till en angiven CIM-instans av en Association.</span><span class="sxs-lookup"><span data-stu-id="ace21-105">Retrieves the CIM instances that are connected to a specific CIM instance by an association.</span></span>

## <span data-ttu-id="ace21-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="ace21-106">SYNTAX</span></span>

### <span data-ttu-id="ace21-107">ComputerSet (standard)</span><span class="sxs-lookup"><span data-stu-id="ace21-107">ComputerSet (Default)</span></span>

```
Get-CimAssociatedInstance [[-Association] <String>] [-ResultClassName <String>]
 [-InputObject] <CimInstance> [-Namespace <String>] [-OperationTimeoutSec <UInt32>]
 [-ResourceUri <Uri>] [-ComputerName <String[]>] [-KeyOnly] [<CommonParameters>]
```

### <span data-ttu-id="ace21-108">SessionSet</span><span class="sxs-lookup"><span data-stu-id="ace21-108">SessionSet</span></span>

```
Get-CimAssociatedInstance [[-Association] <String>] [-ResultClassName <String>]
 [-InputObject] <CimInstance> [-Namespace <String>] [-OperationTimeoutSec <UInt32>]
 [-ResourceUri <Uri>] -CimSession <CimSession[]> [-KeyOnly] [<CommonParameters>]
```

## <span data-ttu-id="ace21-109">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="ace21-109">DESCRIPTION</span></span>

<span data-ttu-id="ace21-110">`Get-CimAssociatedInstance`Cmdlet: en hämtar CIM-instanser som är anslutna till en angiven CIM-instans, som kallas käll instans, av en Association.</span><span class="sxs-lookup"><span data-stu-id="ace21-110">The `Get-CimAssociatedInstance` cmdlet retrieves the CIM instances connected to a specific CIM instance, called the source instance, by an association.</span></span>

<span data-ttu-id="ace21-111">I en Association har varje CIM-instans en namngiven roll och samma CIM-instans kan ingå i en Association i olika roller.</span><span class="sxs-lookup"><span data-stu-id="ace21-111">In an association, each CIM instance has a named role and the same CIM instance can participate in an association in different roles.</span></span>

<span data-ttu-id="ace21-112">Om parametern InputObject inte anges fungerar cmdleten på något av följande sätt:</span><span class="sxs-lookup"><span data-stu-id="ace21-112">If the InputObject parameter is not specified, the cmdlet works in one of the following ways:</span></span>

- <span data-ttu-id="ace21-113">Om varken parametern **computername** eller parametern **CimSession** anges, fungerar denna cmdlet på lokala Windows Management Instrumentation (WMI) med en Component Object Model (com)-session.</span><span class="sxs-lookup"><span data-stu-id="ace21-113">If neither the **ComputerName** parameter nor the **CimSession** parameter is specified, then this cmdlet works on local Windows Management Instrumentation (WMI) using a Component Object Model (COM) session.</span></span>
- <span data-ttu-id="ace21-114">Om antingen parametern **computername** eller parametern **CimSession** anges, fungerar denna cmdlet mot CIM-servern som anges av parametern **computername** eller parametern **CimSession** .</span><span class="sxs-lookup"><span data-stu-id="ace21-114">If either the **ComputerName** parameter or the **CimSession** parameter is specified, then this cmdlet works against the CIM server specified by either the **ComputerName** parameter or the **CimSession** parameter.</span></span>

## <span data-ttu-id="ace21-115">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="ace21-115">EXAMPLES</span></span>

### <span data-ttu-id="ace21-116">Exempel 1: Hämta alla associerade instanser av en angiven instans</span><span class="sxs-lookup"><span data-stu-id="ace21-116">Example 1: Get all the associated instances of a specific instance</span></span>

```powershell
$disk = Get-CimInstance -ClassName Win32_LogicalDisk -KeyOnly
Get-CimAssociatedInstance -InputObject $disk[1]
```

<span data-ttu-id="ace21-117">Den här uppsättningen kommandon hämtar instanserna av klassen med namnet Win32_LogicalDisk och lagrar informationen i en variabel med namnet `$disk` med hjälp av `Get-CimInstance` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="ace21-117">This set of commands retrieves the instances of the class named Win32_LogicalDisk and stores the information in a variable named `$disk` using the `Get-CimInstance` cmdlet.</span></span> <span data-ttu-id="ace21-118">Den första logiska disk instansen i variabeln används sedan som indataports objekt för `Get-CimAssociatedInstance` cmdleten för att hämta alla associerade CIM-instanser av den angivna CIM-instansen.</span><span class="sxs-lookup"><span data-stu-id="ace21-118">The first logical disk instance in the variable is then used as the input object for the `Get-CimAssociatedInstance` cmdlet to get all the associated CIM instances of the specified CIM instance.</span></span>

### <span data-ttu-id="ace21-119">Exempel 2: Hämta alla associerade instanser av en speciell typ</span><span class="sxs-lookup"><span data-stu-id="ace21-119">Example 2: Get all the associated instances of a specific type</span></span>

```powershell
$disk = Get-CimInstance -ClassName Win32_LogicalDisk -KeyOnly
Get-CimAssociatedInstance -InputObject $disk[1] -ResultClass Win32_DiskPartition
```

<span data-ttu-id="ace21-120">Den här uppsättningen kommandon hämtar alla instanser av klassen **Win32_LogicalDisk** och lagrar dem i en variabel med namnet `$disk` .</span><span class="sxs-lookup"><span data-stu-id="ace21-120">This set of commands retrieves all the instances of the **Win32_LogicalDisk** class and stores them in a variable named `$disk`.</span></span> <span data-ttu-id="ace21-121">Den första logiska disk instansen i variabeln används sedan som indataports objekt för `Get-CimAssociatedInstance` cmdleten för att hämta alla associerade instanser som är associerade med den angivna Associations klassen **Win32_DiskPartition**.</span><span class="sxs-lookup"><span data-stu-id="ace21-121">The first logical disk instance in the variable is then used as the input object for the `Get-CimAssociatedInstance` cmdlet to get all the associated instances that are associated through the specified association class **Win32_DiskPartition**.</span></span>

### <span data-ttu-id="ace21-122">Exempel 3: Hämta alla associerade instanser genom att kvalificera en speciell klass</span><span class="sxs-lookup"><span data-stu-id="ace21-122">Example 3: Get all the associated instances through qualifier of a specific class</span></span>

```powershell
$s = Get-CimInstance -Query "Select * from Win32_Service where name like 'Winmgmt'"
Get-CimClass -ClassName *Service* -Qualifier "Association"
$c.CimClasName
```

```Output
Win32_LoadOrderGroupServiceDependencies
Win32_DependentService
Win32_SystemServices
Win32_LoadOrderGroupServiceMembers
Win32_ServiceSpecificationService
```

```powershell
Get-CimAssociatedInstance -InputObject $s -Association Win32_DependentService
```

<span data-ttu-id="ace21-123">Den här uppsättningen kommandon hämtar de tjänster som är beroende av WMI-tjänsten och lagrar dem i en variabel med namnet `$s` .</span><span class="sxs-lookup"><span data-stu-id="ace21-123">This set of commands retrieves the services that depend on WMI service and stores them in a variable named `$s`.</span></span> <span data-ttu-id="ace21-124">Associations klass namnet för **Win32_DependentService** hämtas med hjälp av `Get-CimClass` cmdleten genom att ange **Association** som kvalificerare och skickas sedan med $s till `Get-CimAssociatedInstance` cmdleten för att hämta alla associerade instanser av den hämtade Associations klassen.</span><span class="sxs-lookup"><span data-stu-id="ace21-124">The association class name for the **Win32_DependentService** is retrieved using the `Get-CimClass` cmdlet by specifying **Association** as the qualifier and is then passed with $s to the `Get-CimAssociatedInstance` cmdlet to get all the associated instances of the retrieved association class.</span></span>

## <span data-ttu-id="ace21-125">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="ace21-125">PARAMETERS</span></span>

### <span data-ttu-id="ace21-126">-Association</span><span class="sxs-lookup"><span data-stu-id="ace21-126">-Association</span></span>

<span data-ttu-id="ace21-127">Anger namnet på Associations klassen.</span><span class="sxs-lookup"><span data-stu-id="ace21-127">Specifies the name of the association class.</span></span> <span data-ttu-id="ace21-128">Om du inte anger den här parametern, returnerar cmdleten alla befintliga Associations objekt av valfri typ.</span><span class="sxs-lookup"><span data-stu-id="ace21-128">If you do not specify this parameter, the cmdlet returns all existing association objects of any type.</span></span>

<span data-ttu-id="ace21-129">Om klass A till exempel är associerad med klass B via två associationer, AB1 och AB2, kan den här parametern användas för att ange typ av Association, antingen AB1 eller AB2.</span><span class="sxs-lookup"><span data-stu-id="ace21-129">For example, if class A is associated with class B through two associations, AB1 and AB2, then this parameter can be used to specify the type of association, either AB1 or AB2.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="ace21-130">– CimSession</span><span class="sxs-lookup"><span data-stu-id="ace21-130">-CimSession</span></span>

<span data-ttu-id="ace21-131">Kör kommandot med den angivna CIM-sessionen.</span><span class="sxs-lookup"><span data-stu-id="ace21-131">Runs the command using the specified CIM session.</span></span> <span data-ttu-id="ace21-132">Ange en variabel som innehåller CIM-sessionen, eller ett kommando som skapar eller hämtar CIM-sessionen, till exempel `New-CimSession` eller `Get-CimSession` .</span><span class="sxs-lookup"><span data-stu-id="ace21-132">Enter a variable that contains the CIM session, or a command that creates or gets the CIM session, such as `New-CimSession` or `Get-CimSession`.</span></span> <span data-ttu-id="ace21-133">Mer information finns i [about_CimSession](../Microsoft.PowerShell.Core/About/about_CimSession.md).</span><span class="sxs-lookup"><span data-stu-id="ace21-133">For more information, see [about_CimSession](../Microsoft.PowerShell.Core/About/about_CimSession.md).</span></span>

```yaml
Type: Microsoft.Management.Infrastructure.CimSession[]
Parameter Sets: SessionSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="ace21-134">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="ace21-134">-ComputerName</span></span>

<span data-ttu-id="ace21-135">Anger namnet på den dator som du vill köra CIM-åtgärden på.</span><span class="sxs-lookup"><span data-stu-id="ace21-135">Specifies the name of the computer on which you want to run the CIM operation.</span></span> <span data-ttu-id="ace21-136">Du kan ange ett fullständigt kvalificerat domän namn (FQDN) eller ett NetBIOS-namn.</span><span class="sxs-lookup"><span data-stu-id="ace21-136">You can specify a fully qualified domain name (FQDN) or a NetBIOS name.</span></span>

<span data-ttu-id="ace21-137">Om du anger den här parametern skapar cmdleten en tillfällig session till den angivna datorn med hjälp av WsMan-protokollet.</span><span class="sxs-lookup"><span data-stu-id="ace21-137">If you specify this parameter, the cmdlet creates a temporary session to the specified computer using the WsMan protocol.</span></span>

<span data-ttu-id="ace21-138">Om du inte anger den här parametern utför cmdleten åtgärden på den lokala datorn med hjälp av Component Object Model (COM).</span><span class="sxs-lookup"><span data-stu-id="ace21-138">If you do not specify this parameter, the cmdlet performs the operation on the local computer using Component Object Model (COM).</span></span>

<span data-ttu-id="ace21-139">Om flera åtgärder utförs på samma dator ger det bättre prestanda om du ansluter med en CIM-session.</span><span class="sxs-lookup"><span data-stu-id="ace21-139">If multiple operations are being performed on the same computer, connecting using a CIM session gives better performance.</span></span>

```yaml
Type: System.String[]
Parameter Sets: ComputerSet
Aliases: CN, ServerName

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="ace21-140">– InputObject</span><span class="sxs-lookup"><span data-stu-id="ace21-140">-InputObject</span></span>

<span data-ttu-id="ace21-141">Anger indatamängden för denna cmdlet.</span><span class="sxs-lookup"><span data-stu-id="ace21-141">Specifies the input to this cmdlet.</span></span> <span data-ttu-id="ace21-142">Du kan använda den här parametern, eller så kan du skicka en pipe till denna cmdlet.</span><span class="sxs-lookup"><span data-stu-id="ace21-142">You can use this parameter, or you can pipe the input to this cmdlet.</span></span>

```yaml
Type: Microsoft.Management.Infrastructure.CimInstance
Parameter Sets: (All)
Aliases: CimInstance

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="ace21-143">-KeyOnly</span><span class="sxs-lookup"><span data-stu-id="ace21-143">-KeyOnly</span></span>

<span data-ttu-id="ace21-144">Returnerar objekt med enbart nyckel egenskaper ifyllda.</span><span class="sxs-lookup"><span data-stu-id="ace21-144">Returns objects with only key properties populated.</span></span> <span data-ttu-id="ace21-145">Detta minskar mängden data som överförs via nätverket.</span><span class="sxs-lookup"><span data-stu-id="ace21-145">This reduces the amount of data that is transferred over the network.</span></span>

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

### <span data-ttu-id="ace21-146">– Namnrymd</span><span class="sxs-lookup"><span data-stu-id="ace21-146">-Namespace</span></span>

<span data-ttu-id="ace21-147">Anger namn området för CIM-åtgärden.</span><span class="sxs-lookup"><span data-stu-id="ace21-147">Specifies the namespace for the CIM operation.</span></span> <span data-ttu-id="ace21-148">Standard namn området är rot-/cimv2.</span><span class="sxs-lookup"><span data-stu-id="ace21-148">The default namespace is root/cimv2.</span></span>

> [!NOTE]
> <span data-ttu-id="ace21-149">Du kan använda TABB-slutförande för att bläddra i listan över namn områden, eftersom PowerShell hämtar en lista över namn områden från den lokala WMI-servern för att tillhandahålla listan över namn områden.</span><span class="sxs-lookup"><span data-stu-id="ace21-149">You can use tab completion to browse the list of namespaces, because PowerShell gets a list of namespaces from the local WMI server to provide the list of namespaces.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="ace21-150">-OperationTimeoutSec</span><span class="sxs-lookup"><span data-stu-id="ace21-150">-OperationTimeoutSec</span></span>

<span data-ttu-id="ace21-151">Anger hur lång tid cmdleten väntar på ett svar från datorn.</span><span class="sxs-lookup"><span data-stu-id="ace21-151">Specifies the amount of time that the cmdlet waits for a response from the computer.</span></span> <span data-ttu-id="ace21-152">Som standard är värdet för den här parametern 0, vilket innebär att cmdleten använder standardvärdet för timeout för servern.</span><span class="sxs-lookup"><span data-stu-id="ace21-152">By default, the value of this parameter is 0, which means that the cmdlet uses the default timeout value for the server.</span></span>

<span data-ttu-id="ace21-153">Om **OperationTimeoutSec** -parametern har angetts till ett värde som är lägre än det stabila anslutnings försöket på 3 minuter, går det inte att återställa nätverks fel som sist mer än värdet för parametern **OperationTimeoutSec** , eftersom åtgärden på servern överskrider innan klienten kan återansluta.</span><span class="sxs-lookup"><span data-stu-id="ace21-153">If the **OperationTimeoutSec** parameter is set to a value less than the robust connection retry timeout of 3 minutes, network failures that last more than the value of the **OperationTimeoutSec** parameter are not recoverable, because the operation on the server times out before the client can reconnect.</span></span>

```yaml
Type: System.UInt32
Parameter Sets: (All)
Aliases: OT

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="ace21-154">– ResourceUri</span><span class="sxs-lookup"><span data-stu-id="ace21-154">-ResourceUri</span></span>

<span data-ttu-id="ace21-155">Anger resurs-URI (Uniform Resource Identifier) för resurs klassen eller-instansen.</span><span class="sxs-lookup"><span data-stu-id="ace21-155">Specifies the resource uniform resource identifier (URI) of the resource class or instance.</span></span> <span data-ttu-id="ace21-156">URI: n används för att identifiera en speciell typ av resurs, till exempel diskar eller processer, på en dator.</span><span class="sxs-lookup"><span data-stu-id="ace21-156">The URI is used to identify a specific type of resource, such as disks or processes, on a computer.</span></span>

<span data-ttu-id="ace21-157">En URI består av ett prefix och en sökväg till en resurs.</span><span class="sxs-lookup"><span data-stu-id="ace21-157">A URI consists of a prefix and a path to a resource.</span></span> <span data-ttu-id="ace21-158">Ett exempel:</span><span class="sxs-lookup"><span data-stu-id="ace21-158">For example:</span></span>

- `http://schemas.microsoft.com/wbem/wsman/1/wmi/root/cimv2/Win32_LogicalDisk`
- `http://intel.com/wbem/wscim/1/amt-schema/1/AMT_GeneralSettings`

<span data-ttu-id="ace21-159">Om du inte anger den här parametern används DMTF-standardresurs-URI som standard `http://schemas.dmtf.org/wbem/wscim/1/cim-schema/2/` och klass namnet läggs till i den.</span><span class="sxs-lookup"><span data-stu-id="ace21-159">By default, if you do not specify this parameter, the DMTF standard resource URI `http://schemas.dmtf.org/wbem/wscim/1/cim-schema/2/` is used and the class name is appended to it.</span></span>

<span data-ttu-id="ace21-160">**ResourceURI** kan endast användas med CIM-sessioner som skapats med WSMan-protokollet, eller när du anger parametern **computername** , som skapar en CIM-session med hjälp av WSMan.</span><span class="sxs-lookup"><span data-stu-id="ace21-160">**ResourceURI** can only be used with CIM sessions created using the WSMan protocol, or when specifying the **ComputerName** parameter, which creates a CIM session using WSMan.</span></span> <span data-ttu-id="ace21-161">Om du anger den här parametern utan att ange parametern **computername** , eller om du anger en CIM-session som skapats med DCOM-protokollet, uppstår ett fel, eftersom DCOM-protokollet inte stöder parametern **ResourceURI** .</span><span class="sxs-lookup"><span data-stu-id="ace21-161">If you specify this parameter without specifying the **ComputerName** parameter, or if you specify a CIM session created using DCOM protocol, you get an error, because the DCOM protocol does not support the **ResourceURI** parameter.</span></span>

<span data-ttu-id="ace21-162">Om både den **ResourceUri** -parametern och **filter** parametern anges, ignoreras **filter** parametern.</span><span class="sxs-lookup"><span data-stu-id="ace21-162">If both the **ResourceUri** parameter and the **Filter** parameter are specified, the **Filter** parameter is ignored.</span></span>

```yaml
Type: System.Uri
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="ace21-163">-ResultClassName</span><span class="sxs-lookup"><span data-stu-id="ace21-163">-ResultClassName</span></span>

<span data-ttu-id="ace21-164">Anger klass namnet för de associerade instanserna.</span><span class="sxs-lookup"><span data-stu-id="ace21-164">Specifies the class name of the associated instances.</span></span> <span data-ttu-id="ace21-165">En CIM-instans kan associeras med en eller flera CIM-instanser.</span><span class="sxs-lookup"><span data-stu-id="ace21-165">A CIM instance can be associated with one or more CIM instances.</span></span> <span data-ttu-id="ace21-166">Alla associerade CIM-instanser returneras om du inte anger namnet på resultat klassen.</span><span class="sxs-lookup"><span data-stu-id="ace21-166">All associated CIM instances are returned if you do not specify the result class name.</span></span>

<span data-ttu-id="ace21-167">Som standard är värdet för den här parametern null och alla associerade CIM-instanser returneras.</span><span class="sxs-lookup"><span data-stu-id="ace21-167">By default, the value of this parameter is null, and all associated CIM instances are returned.</span></span>

<span data-ttu-id="ace21-168">Du kan filtrera kopplings resultaten så att de matchar ett angivet klass namn.</span><span class="sxs-lookup"><span data-stu-id="ace21-168">You can filter the association results to match a specific class name.</span></span> <span data-ttu-id="ace21-169">Filtreringen sker på servern.</span><span class="sxs-lookup"><span data-stu-id="ace21-169">Filtering happens on the server.</span></span> <span data-ttu-id="ace21-170">Om den här parametern inte anges `Get-CIMAssociatedInstance` returnerar alla befintliga associationer.</span><span class="sxs-lookup"><span data-stu-id="ace21-170">If this parameter is not specified, `Get-CIMAssociatedInstance` returns all existing associations.</span></span> <span data-ttu-id="ace21-171">Om klass A till exempel är kopplad till klass B, C och D, kan den här parametern användas för att begränsa utdata till en specifik typ (B, C eller D).</span><span class="sxs-lookup"><span data-stu-id="ace21-171">For example, if class A is associated with classes B, C and D, then this parameter can be used to restrict the output to a specific type (B, C or D).</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="ace21-172">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="ace21-172">CommonParameters</span></span>

<span data-ttu-id="ace21-173">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="ace21-173">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="ace21-174">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="ace21-174">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="ace21-175">INDATA</span><span class="sxs-lookup"><span data-stu-id="ace21-175">INPUTS</span></span>

### <span data-ttu-id="ace21-176">Inget</span><span class="sxs-lookup"><span data-stu-id="ace21-176">None</span></span>

<span data-ttu-id="ace21-177">Denna cmdlet accepterar inga inobjekt.</span><span class="sxs-lookup"><span data-stu-id="ace21-177">This cmdlet accepts no input objects.</span></span>

## <span data-ttu-id="ace21-178">UTDATA</span><span class="sxs-lookup"><span data-stu-id="ace21-178">OUTPUTS</span></span>

### <span data-ttu-id="ace21-179">System. Object</span><span class="sxs-lookup"><span data-stu-id="ace21-179">System.Object</span></span>

<span data-ttu-id="ace21-180">Den här cmdleten returnerar ett objekt.</span><span class="sxs-lookup"><span data-stu-id="ace21-180">This cmdlet returns an object.</span></span>

## <span data-ttu-id="ace21-181">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="ace21-181">NOTES</span></span>

## <span data-ttu-id="ace21-182">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="ace21-182">RELATED LINKS</span></span>

[<span data-ttu-id="ace21-183">Get-CimClass</span><span class="sxs-lookup"><span data-stu-id="ace21-183">Get-CimClass</span></span>](get-cimclass.md)

[<span data-ttu-id="ace21-184">Get-CimInstance</span><span class="sxs-lookup"><span data-stu-id="ace21-184">Get-CimInstance</span></span>](get-ciminstance.md)

