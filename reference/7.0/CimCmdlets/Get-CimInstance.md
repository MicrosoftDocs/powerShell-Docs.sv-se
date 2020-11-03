---
external help file: Microsoft.Management.Infrastructure.CimCmdlets.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: CimCmdlets
ms.date: 02/21/2019
online version: https://docs.microsoft.com/powershell/module/cimcmdlets/get-ciminstance?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-CimInstance
ms.openlocfilehash: edc67596bdb446b18635339255376a17d3f67843
ms.sourcegitcommit: 37abf054ad9eda8813be8ff4487803b10e1842ef
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/23/2020
ms.locfileid: "93268437"
---
# <span data-ttu-id="f8747-103">Get-CimInstance</span><span class="sxs-lookup"><span data-stu-id="f8747-103">Get-CimInstance</span></span>

## <span data-ttu-id="f8747-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="f8747-104">SYNOPSIS</span></span>
<span data-ttu-id="f8747-105">Hämtar CIM-instanser för en klass från en CIM-server.</span><span class="sxs-lookup"><span data-stu-id="f8747-105">Gets the CIM instances of a class from a CIM server.</span></span>

## <span data-ttu-id="f8747-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="f8747-106">SYNTAX</span></span>

### <span data-ttu-id="f8747-107">ClassNameComputerSet (standard)</span><span class="sxs-lookup"><span data-stu-id="f8747-107">ClassNameComputerSet (Default)</span></span>

```
Get-CimInstance [-ClassName] <String> [-ComputerName <String[]>] [-KeyOnly] [-Namespace <String>]
 [-OperationTimeoutSec <UInt32>] [-QueryDialect <String>] [-Shallow] [-Filter <String>]
 [-Property <String[]>] [<CommonParameters>]
```

### <span data-ttu-id="f8747-108">ResourceUriSessionSet</span><span class="sxs-lookup"><span data-stu-id="f8747-108">ResourceUriSessionSet</span></span>

```
Get-CimInstance -CimSession <CimSession[]> -ResourceUri <Uri> [-KeyOnly] [-Namespace <String>]
 [-OperationTimeoutSec <UInt32>] [-Shallow] [-Filter <String>] [-Property <String[]>]
 [<CommonParameters>]
```

### <span data-ttu-id="f8747-109">QuerySessionSet</span><span class="sxs-lookup"><span data-stu-id="f8747-109">QuerySessionSet</span></span>

```
Get-CimInstance -CimSession <CimSession[]> [-ResourceUri <Uri>] [-Namespace <String>]
 [-OperationTimeoutSec <UInt32>] -Query <String> [-QueryDialect <String>] [-Shallow]
 [<CommonParameters>]
```

### <span data-ttu-id="f8747-110">ClassNameSessionSet</span><span class="sxs-lookup"><span data-stu-id="f8747-110">ClassNameSessionSet</span></span>

```
Get-CimInstance -CimSession <CimSession[]> [-ClassName] <String> [-KeyOnly] [-Namespace <String>]
 [-OperationTimeoutSec <UInt32>] [-QueryDialect <String>] [-Shallow] [-Filter <String>]
 [-Property <String[]>] [<CommonParameters>]
```

### <span data-ttu-id="f8747-111">CimInstanceSessionSet</span><span class="sxs-lookup"><span data-stu-id="f8747-111">CimInstanceSessionSet</span></span>

```
Get-CimInstance -CimSession <CimSession[]> [-ResourceUri <Uri>] [-OperationTimeoutSec <UInt32>]
 [-InputObject] <CimInstance> [<CommonParameters>]
```

### <span data-ttu-id="f8747-112">CimInstanceComputerSet</span><span class="sxs-lookup"><span data-stu-id="f8747-112">CimInstanceComputerSet</span></span>

```
Get-CimInstance [-ResourceUri <Uri>] [-ComputerName <String[]>] [-OperationTimeoutSec <UInt32>]
 [-InputObject] <CimInstance> [<CommonParameters>]
```

### <span data-ttu-id="f8747-113">ResourceUriComputerSet</span><span class="sxs-lookup"><span data-stu-id="f8747-113">ResourceUriComputerSet</span></span>

```
Get-CimInstance -ResourceUri <Uri> [-ComputerName <String[]>] [-KeyOnly] [-Namespace <String>]
 [-OperationTimeoutSec <UInt32>] [-Shallow] [-Filter <String>] [-Property <String[]>]
 [<CommonParameters>]
```

### <span data-ttu-id="f8747-114">QueryComputerSet</span><span class="sxs-lookup"><span data-stu-id="f8747-114">QueryComputerSet</span></span>

```
Get-CimInstance [-ResourceUri <Uri>] [-ComputerName <String[]>] [-Namespace <String>]
 [-OperationTimeoutSec <UInt32>] -Query <String> [-QueryDialect <String>] [-Shallow]
 [<CommonParameters>]
```

## <span data-ttu-id="f8747-115">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="f8747-115">DESCRIPTION</span></span>

<span data-ttu-id="f8747-116">`Get-CimInstance`Cmdlet: en hämtar CIM-instanser för en klass från en CIM-server.</span><span class="sxs-lookup"><span data-stu-id="f8747-116">The `Get-CimInstance` cmdlet gets the CIM instances of a class from a CIM server.</span></span> <span data-ttu-id="f8747-117">Du kan ange antingen klass namnet eller en fråga för denna cmdlet.</span><span class="sxs-lookup"><span data-stu-id="f8747-117">You can specify either the class name or a query for this cmdlet.</span></span> <span data-ttu-id="f8747-118">Denna cmdlet returnerar ett eller flera CIM-instanser som representerar en ögonblicks bild av CIM-instanserna på CIM-servern.</span><span class="sxs-lookup"><span data-stu-id="f8747-118">This cmdlet returns one or more CIM instance objects representing a snapshot of the CIM instances present on the CIM server.</span></span>

<span data-ttu-id="f8747-119">Om parametern **InputObject** inte anges fungerar cmdleten på något av följande sätt:</span><span class="sxs-lookup"><span data-stu-id="f8747-119">If the **InputObject** parameter is not specified, the cmdlet works in one of the following ways:</span></span>

- <span data-ttu-id="f8747-120">Om varken parametern **computername** eller parametern **CimSession** anges, fungerar denna cmdlet på lokala Windows Management Instrumentation (WMI) med en Component Object Model (com)-session.</span><span class="sxs-lookup"><span data-stu-id="f8747-120">If neither the **ComputerName** parameter nor the **CimSession** parameter is specified, then this cmdlet works on local Windows Management Instrumentation (WMI) using a Component Object Model (COM) session.</span></span>
- <span data-ttu-id="f8747-121">Om antingen parametern **computername** eller parametern **CimSession** anges, fungerar denna cmdlet mot CIM-servern som anges av parametern **computername** eller parametern **CimSession** .</span><span class="sxs-lookup"><span data-stu-id="f8747-121">If either the **ComputerName** parameter or the **CimSession** parameter is specified, then this cmdlet works against the CIM server specified by either the **ComputerName** parameter or the **CimSession** parameter.</span></span>

<span data-ttu-id="f8747-122">Om parametern **InputObject** anges fungerar cmdleten på något av följande sätt:</span><span class="sxs-lookup"><span data-stu-id="f8747-122">If the **InputObject** parameter is specified, the cmdlet works in one of the following ways:</span></span>

- <span data-ttu-id="f8747-123">Om varken parametern **computername** eller parametern **CimSession** anges, använder denna cmdlet CIM-sessionen eller dator namnet från det indata-objektet.</span><span class="sxs-lookup"><span data-stu-id="f8747-123">If neither the **ComputerName** parameter nor the **CimSession** parameter is specified, then this cmdlet uses the CIM session or computer name from the input object.</span></span>
- <span data-ttu-id="f8747-124">Om antingen parametern **computername** eller parametern **CimSession** anges använder den här cmdleten antingen parametern CimSession eller värdet **computername** .</span><span class="sxs-lookup"><span data-stu-id="f8747-124">If the either the **ComputerName** parameter or the **CimSession** parameter is specified, then this cmdlet uses the either the CimSession parameter value or **ComputerName** parameter value.</span></span>

## <span data-ttu-id="f8747-125">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="f8747-125">EXAMPLES</span></span>

### <span data-ttu-id="f8747-126">Exempel 1: Hämta CIM-instanser för en angiven klass</span><span class="sxs-lookup"><span data-stu-id="f8747-126">Example 1: Get the CIM instances of a specified class</span></span>

<span data-ttu-id="f8747-127">I det här exemplet hämtas CIM-instanser för en klass med namnet **Win32_Process**.</span><span class="sxs-lookup"><span data-stu-id="f8747-127">This example retrieves the CIM instances of a class named **Win32_Process**.</span></span>

```powershell
Get-CimInstance -ClassName Win32_Process
```

### <span data-ttu-id="f8747-128">Exempel 2: Hämta en lista över namn områden från en WMI-Server</span><span class="sxs-lookup"><span data-stu-id="f8747-128">Example 2: Get a list of namespaces from a WMI server</span></span>

<span data-ttu-id="f8747-129">I det här exemplet hämtas en lista över namn områden under **rot** namn området på en WMI-Server.</span><span class="sxs-lookup"><span data-stu-id="f8747-129">This example retrieves a list of namespaces under the **Root** namespace on a WMI server.</span></span>

```powershell
Get-CimInstance -Namespace root -ClassName __Namespace
```

### <span data-ttu-id="f8747-130">Exempel 3: Hämta instanser av en klass filtrerad med hjälp av en fråga</span><span class="sxs-lookup"><span data-stu-id="f8747-130">Example 3: Get instances of a class filtered by using a query</span></span>

<span data-ttu-id="f8747-131">I det här exemplet hämtas alla CIM-instanser som börjar med bokstaven **P** i en klass med namnet **Win32_Process** med hjälp av frågan som anges av en **frågeparameter** .</span><span class="sxs-lookup"><span data-stu-id="f8747-131">This example retrieves all the CIM instances that start with the letter **P** of a class named **Win32_Process** using the query specified by a **Query** parameter.</span></span>

```powershell
Get-CimInstance -Query "SELECT * from Win32_Process WHERE name LIKE 'P%'"
```

### <span data-ttu-id="f8747-132">Exempel 4: Hämta instanser av en klass filtrerad med hjälp av ett klass namn och ett filter uttryck</span><span class="sxs-lookup"><span data-stu-id="f8747-132">Example 4: Get instances of a class filtered by using a class name and a filter expression</span></span>

<span data-ttu-id="f8747-133">I det här exemplet hämtas alla CIM-instanser som börjar med bokstaven **P** i en klass med namnet **Win32_Process** med hjälp av filter parametern.</span><span class="sxs-lookup"><span data-stu-id="f8747-133">This example retrieves all the CIM instances that start with the letter **P** of a class named **Win32_Process** using the Filter parameter.</span></span>

```powershell
Get-CimInstance -ClassName Win32_Process -Filter "Name like 'P%'"
```

### <span data-ttu-id="f8747-134">Exempel 5: Hämta CIM-instanserna med endast nyckel egenskaper ifyllda</span><span class="sxs-lookup"><span data-stu-id="f8747-134">Example 5: Get the CIM instances with only key properties filled in</span></span>

<span data-ttu-id="f8747-135">Det här exemplet skapar en ny CIM-instans i minnet för en klass med namnet **Win32_Process** med nyckel egenskapen `@{ "Handle"=0 }` och lagrar den i en variabel med namnet `$x` .</span><span class="sxs-lookup"><span data-stu-id="f8747-135">This example creates a new CIM instance in memory for a class named **Win32_Process** with the key property `@{ "Handle"=0 }` and stores it in a variable named `$x`.</span></span> <span data-ttu-id="f8747-136">Variabeln skickas som en CIM-instans till `Get-CimInstance` cmdleten för att hämta en viss instans.</span><span class="sxs-lookup"><span data-stu-id="f8747-136">The variable is passed as a CIM instance to the `Get-CimInstance` cmdlet to get a particular instance.</span></span>

```powershell
$x = New-CimInstance -ClassName Win32_Process -Namespace root\cimv2 -Property @{ "Handle"=0 } -Key Handle -ClientOnly
Get-CimInstance -CimInstance $x
```

### <span data-ttu-id="f8747-137">Exempel 6: Hämta CIM-instanser och återanvänd dem</span><span class="sxs-lookup"><span data-stu-id="f8747-137">Example 6: Retrieve CIM instances and reuse them</span></span>

<span data-ttu-id="f8747-138">Det här exemplet hämtar CIM-instanser av en klass med namnet **Win32_Process** och lagrar dem i variablerna `$x` och `$y` .</span><span class="sxs-lookup"><span data-stu-id="f8747-138">This example gets the CIM instances of a class named **Win32_Process** and stores them in the variables `$x` and `$y`.</span></span> <span data-ttu-id="f8747-139">Variabeln `$x` formateras sedan i en tabell som endast innehåller egenskaperna **Name** och **KernelModeTime** , vilken tabell som ska anpassas till **AutoSize**.</span><span class="sxs-lookup"><span data-stu-id="f8747-139">The variable `$x` is then formatted in a table containing only the **Name** and **KernelModeTime** properties, the table set to **AutoSize**.</span></span>

```powershell
$x,$y = Get-CimInstance -ClassName Win32_Process
$x | Format-Table -Property Name,KernelModeTime -AutoSize
```

```Output
Name                 KernelModeTime
----                 --------------
System Idle Process 157238797968750
```

### <span data-ttu-id="f8747-140">Exempel 7: Hämta CIM-instanser från fjärran sluten dator</span><span class="sxs-lookup"><span data-stu-id="f8747-140">Example 7: Get CIM instances from remote computer</span></span>

<span data-ttu-id="f8747-141">I det här exemplet hämtas CIM-instanser för en klass med namnet **Win32_ComputerSystem** från fjärrdatorerna med namnet **Server01** och **Server02**.</span><span class="sxs-lookup"><span data-stu-id="f8747-141">This example retrieves the CIM instances of a class named **Win32_ComputerSystem** from the remote computers named **Server01** and **Server02**.</span></span>

```powershell
Get-CimInstance -ClassName Win32_ComputerSystem -ComputerName Server01,Server02
```

### <span data-ttu-id="f8747-142">Exempel 8: Hämta bara nyckel egenskaperna, i stället för alla egenskaper</span><span class="sxs-lookup"><span data-stu-id="f8747-142">Example 8: Getting only the key properties, instead of all properties</span></span>

<span data-ttu-id="f8747-143">I det här exemplet hämtas bara nyckel egenskaperna, vilket minskar storleken på objektet och nätverks trafiken.</span><span class="sxs-lookup"><span data-stu-id="f8747-143">This example retrieves only the key properties, which reduces the size of the object and network traffic.</span></span>

```powershell
$x = Get-CimInstance -Class Win32_Process -KeyOnly
$x | Invoke-CimMethod -MethodName GetOwner
```

### <span data-ttu-id="f8747-144">Exempel 9: bara hämta en delmängd av egenskaperna, i stället för alla egenskaper</span><span class="sxs-lookup"><span data-stu-id="f8747-144">Example 9: Getting only a subset of properties, instead of all properties</span></span>

<span data-ttu-id="f8747-145">I det här exemplet hämtas endast en del av egenskaperna, vilket minskar storleken på objektet och nätverks trafiken.</span><span class="sxs-lookup"><span data-stu-id="f8747-145">This example retrieves only a subset of properties, which reduces the size of the object and network traffic.</span></span>

```powershell
Get-CimInstance -Class Win32_Process -Property Name,KernelModeTime
$x = Get-CimInstance -Class Win32_Process -Property Name,KernelModeTime
$x | Invoke-CimMethod -MethodName GetOwner
```

<span data-ttu-id="f8747-146">Instansen som hämtades med **egenskaps** parametern kan användas för att utföra andra CIM-åtgärder, till exempel `Set-CimInstance` eller `Invoke-CimMethod` .</span><span class="sxs-lookup"><span data-stu-id="f8747-146">The instance retrieved with the **Property** parameter can be used to perform other CIM operations, for example `Set-CimInstance` or `Invoke-CimMethod`.</span></span>

### <span data-ttu-id="f8747-147">Exempel 10: Hämta CIM-instansen med CIM-sessionen</span><span class="sxs-lookup"><span data-stu-id="f8747-147">Example 10: Get the CIM instance using CIM session</span></span>

<span data-ttu-id="f8747-148">I det här exemplet skapas en CIM-session på datorerna med namnet **Server01** och **Server02** med hjälp av `New-CimSession` cmdleten och lagras sessionsinformation i en variabel med namnet `$s` .</span><span class="sxs-lookup"><span data-stu-id="f8747-148">This example creates a CIM session on the computers named **Server01** and **Server02** using the `New-CimSession` cmdlet and stores the session information in a variable named `$s`.</span></span> <span data-ttu-id="f8747-149">Innehållet i variabeln skickas sedan till `Get-CimInstance` med hjälp av parametern **CimSession** för att hämta CIM-instanser av klassen med namnet **Win32_ComputerSystem**.</span><span class="sxs-lookup"><span data-stu-id="f8747-149">The contents of the variable are then passed to `Get-CimInstance` by using the **CimSession** parameter, to get the CIM instances of the class named **Win32_ComputerSystem**.</span></span>

```powershell
$s = New-CimSession -ComputerName Server01,Server02
Get-CimInstance -ClassName Win32_ComputerSystem -CimSession $s
```

## <span data-ttu-id="f8747-150">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="f8747-150">PARAMETERS</span></span>

### <span data-ttu-id="f8747-151">– CimSession</span><span class="sxs-lookup"><span data-stu-id="f8747-151">-CimSession</span></span>

<span data-ttu-id="f8747-152">Anger den CIM-session som ska användas för denna cmdlet.</span><span class="sxs-lookup"><span data-stu-id="f8747-152">Specifies the CIM session to use for this cmdlet.</span></span> <span data-ttu-id="f8747-153">Ange en variabel som innehåller CIM-sessionen eller ett kommando som skapar eller hämtar CIM-sessionen, till exempel `New-CimSession` `Get-CimSession` cmdletarna eller.</span><span class="sxs-lookup"><span data-stu-id="f8747-153">Enter a variable that contains the CIM session or a command that creates or gets the CIM session, such as the `New-CimSession` or `Get-CimSession` cmdlets.</span></span> <span data-ttu-id="f8747-154">Mer information finns i [about_CimSession](../Microsoft.PowerShell.Core/About/about_CimSession.md).</span><span class="sxs-lookup"><span data-stu-id="f8747-154">For more information, see [about_CimSession](../Microsoft.PowerShell.Core/About/about_CimSession.md).</span></span>

```yaml
Type: Microsoft.Management.Infrastructure.CimSession[]
Parameter Sets: ResourceUriSessionSet, QuerySessionSet, ClassNameSessionSet, CimInstanceSessionSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="f8747-155">-ClassName</span><span class="sxs-lookup"><span data-stu-id="f8747-155">-ClassName</span></span>

<span data-ttu-id="f8747-156">Anger namnet på CIM-klassen som CIM-instanserna ska hämtas för.</span><span class="sxs-lookup"><span data-stu-id="f8747-156">Specifies the name of the CIM class for which to retrieve the CIM instances.</span></span> <span data-ttu-id="f8747-157">Du kan använda TABB-slutförande för att bläddra i listan över klasser, eftersom PowerShell hämtar en lista över klasser från den lokala WMI-servern för att tillhandahålla en lista över klass namn.</span><span class="sxs-lookup"><span data-stu-id="f8747-157">You can use tab completion to browse the list of classes, because PowerShell gets a list of classes from the local WMI server to provide a list of class names.</span></span>

```yaml
Type: System.String
Parameter Sets: ClassNameComputerSet, ClassNameSessionSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="f8747-158">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="f8747-158">-ComputerName</span></span>

<span data-ttu-id="f8747-159">Anger den dator där du vill köra CIM-åtgärden.</span><span class="sxs-lookup"><span data-stu-id="f8747-159">Specifies computer on which you want to run the CIM operation.</span></span> <span data-ttu-id="f8747-160">Du kan ange ett fullständigt kvalificerat domän namn (FQDN), ett NetBIOS-namn eller en IP-adress.</span><span class="sxs-lookup"><span data-stu-id="f8747-160">You can specify a fully qualified domain name (FQDN), a NetBIOS name, or an IP address.</span></span> <span data-ttu-id="f8747-161">Om du inte anger den här parametern utför cmdleten åtgärden på den lokala datorn med hjälp av Component Object Model (COM).</span><span class="sxs-lookup"><span data-stu-id="f8747-161">If you do not specify this parameter, the cmdlet performs the operation on the local computer using Component Object Model (COM).</span></span>

<span data-ttu-id="f8747-162">Om du anger den här parametern skapar cmdleten en tillfällig session till den angivna datorn med hjälp av WsMan-protokollet.</span><span class="sxs-lookup"><span data-stu-id="f8747-162">If you specify this parameter, the cmdlet creates a temporary session to the specified computer using the WsMan protocol.</span></span>

<span data-ttu-id="f8747-163">Om flera åtgärder utförs på samma dator ansluter du med en CIM-session för bättre prestanda.</span><span class="sxs-lookup"><span data-stu-id="f8747-163">If multiple operations are being performed on the same computer, connect using a CIM session for better performance.</span></span>

```yaml
Type: System.String[]
Parameter Sets: ClassNameComputerSet, CimInstanceComputerSet, ResourceUriComputerSet, QueryComputerSet
Aliases: CN, ServerName

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="f8747-164">-Filter</span><span class="sxs-lookup"><span data-stu-id="f8747-164">-Filter</span></span>

<span data-ttu-id="f8747-165">Anger en WHERE-sats som ska användas som ett filter.</span><span class="sxs-lookup"><span data-stu-id="f8747-165">Specifies a where clause to use as a filter.</span></span> <span data-ttu-id="f8747-166">Ange satsen i antingen **WQL** -eller **CQL** -frågespråket.</span><span class="sxs-lookup"><span data-stu-id="f8747-166">Specify the clause in either the **WQL** or the **CQL** query language.</span></span> <span data-ttu-id="f8747-167">Ta inte med `WHERE` nyckelordet i parameterns värde.</span><span class="sxs-lookup"><span data-stu-id="f8747-167">Do not include the `WHERE` keyword in the value of the parameter.</span></span>

```yaml
Type: System.String
Parameter Sets: ClassNameComputerSet, ResourceUriSessionSet, ClassNameSessionSet, ResourceUriComputerSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="f8747-168">– InputObject</span><span class="sxs-lookup"><span data-stu-id="f8747-168">-InputObject</span></span>

<span data-ttu-id="f8747-169">Anger ett CIM-instansnamn som ska användas som indatakälla.</span><span class="sxs-lookup"><span data-stu-id="f8747-169">Specifies a CIM instance object to use as input.</span></span>

<span data-ttu-id="f8747-170">Om du redan arbetar med ett CIM-instansnamn kan du använda den här parametern för att skicka CIM-instansnamnet för att hämta den senaste ögonblicks bilden från CIM-servern.</span><span class="sxs-lookup"><span data-stu-id="f8747-170">If you are already working with a CIM instance object, you can use this parameter to pass the CIM instance object in order to get the latest snapshot from the CIM server.</span></span> <span data-ttu-id="f8747-171">När du skickar ett CIM-instansnamn som inmatat, `Get-CimInstance` returnerar objektet från servern med hjälp av en get CIM-åtgärd, i stället för en uppräknings-eller fråga-åtgärd.</span><span class="sxs-lookup"><span data-stu-id="f8747-171">When you pass a CIM instance object as an input, `Get-CimInstance` returns the object from server using a get CIM operation, instead of an enumerate or query operation.</span></span> <span data-ttu-id="f8747-172">Att använda en get CIM-åtgärd är mer effektivt än att hämta alla instanser och sedan filtrera dem.</span><span class="sxs-lookup"><span data-stu-id="f8747-172">Using a get CIM operation is more efficient than retrieving all instances and then filtering them.</span></span>

<span data-ttu-id="f8747-173">Om CIM-klassen inte implementerar get-åtgärden returnerar **InputObject** -parametern ett fel.</span><span class="sxs-lookup"><span data-stu-id="f8747-173">If the CIM class does not implement the get operation, then specifying the **InputObject** parameter returns an error.</span></span>

```yaml
Type: Microsoft.Management.Infrastructure.CimInstance
Parameter Sets: CimInstanceSessionSet, CimInstanceComputerSet
Aliases: CimInstance

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="f8747-174">-KeyOnly</span><span class="sxs-lookup"><span data-stu-id="f8747-174">-KeyOnly</span></span>

<span data-ttu-id="f8747-175">Anger att endast objekt med nyckel egenskaper som är ifyllda returneras.</span><span class="sxs-lookup"><span data-stu-id="f8747-175">Indicates that only objects with key properties populated are returned.</span></span> <span data-ttu-id="f8747-176">Om du anger parametern för **endast** parametern minskas mängden data som överförs över nätverket.</span><span class="sxs-lookup"><span data-stu-id="f8747-176">Specifying the **KeyOnly** parameter reduces the amount of data transferred over the network.</span></span>

<span data-ttu-id="f8747-177">Använd parametern **endast** tangenten om du bara vill returnera en liten del av objektet, som kan användas för andra åtgärder, t `Set-CimInstance` . ex. eller- `Get-CimAssociatedInstance` cmdletar.</span><span class="sxs-lookup"><span data-stu-id="f8747-177">Use the **KeyOnly** parameter to return only a small portion of the object, which can be used for other operations, such as the `Set-CimInstance` or `Get-CimAssociatedInstance` cmdlets.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ClassNameComputerSet, ResourceUriSessionSet, ClassNameSessionSet, ResourceUriComputerSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="f8747-178">– Namnrymd</span><span class="sxs-lookup"><span data-stu-id="f8747-178">-Namespace</span></span>

<span data-ttu-id="f8747-179">Anger namn området för CIM-klassen.</span><span class="sxs-lookup"><span data-stu-id="f8747-179">Specifies the namespace of CIM class.</span></span>

<span data-ttu-id="f8747-180">Standard namn området är **rot-/cimv2**.</span><span class="sxs-lookup"><span data-stu-id="f8747-180">The default namespace is **root/cimv2**.</span></span> <span data-ttu-id="f8747-181">Du kan använda TABB-slutförande för att bläddra i listan över namn områden, eftersom PowerShell hämtar en lista över namn områden från den lokala WMI-servern för att tillhandahålla listan över namn områden.</span><span class="sxs-lookup"><span data-stu-id="f8747-181">You can use tab completion to browse the list of namespaces, because PowerShell gets a list of namespaces from the local WMI server to provide the list of namespaces.</span></span>

```yaml
Type: System.String
Parameter Sets: ClassNameComputerSet, ResourceUriSessionSet, QuerySessionSet, ClassNameSessionSet, ResourceUriComputerSet, QueryComputerSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="f8747-182">-OperationTimeoutSec</span><span class="sxs-lookup"><span data-stu-id="f8747-182">-OperationTimeoutSec</span></span>

<span data-ttu-id="f8747-183">Anger hur lång tid cmdleten väntar på ett svar från datorn.</span><span class="sxs-lookup"><span data-stu-id="f8747-183">Specifies the amount of time that the cmdlet waits for a response from the computer.</span></span> <span data-ttu-id="f8747-184">Som standard är värdet för den här parametern 0, vilket innebär att cmdleten använder standardvärdet för timeout för servern.</span><span class="sxs-lookup"><span data-stu-id="f8747-184">By default, the value of this parameter is 0, which means that the cmdlet uses the default timeout value for the server.</span></span>

<span data-ttu-id="f8747-185">Om **OperationTimeoutSec** -parametern har angetts till ett värde som är lägre än det stabila anslutnings försöket på 3 minuter, går det inte att återställa nätverks fel som sist mer än värdet för parametern **OperationTimeoutSec** , eftersom åtgärden på servern överskrider innan klienten kan återansluta.</span><span class="sxs-lookup"><span data-stu-id="f8747-185">If the **OperationTimeoutSec** parameter is set to a value less than the robust connection retry timeout of 3 minutes, network failures that last more than the value of the **OperationTimeoutSec** parameter are not recoverable, because the operation on the server times out before the client can reconnect.</span></span>

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

### <span data-ttu-id="f8747-186">– Egenskap</span><span class="sxs-lookup"><span data-stu-id="f8747-186">-Property</span></span>

<span data-ttu-id="f8747-187">Anger en uppsättning instans egenskaper som ska hämtas.</span><span class="sxs-lookup"><span data-stu-id="f8747-187">Specifies a set of instance properties to retrieve.</span></span> <span data-ttu-id="f8747-188">Använd den här parametern när du behöver minska storleken på det returnerade objektet, antingen i minnet eller i nätverket.</span><span class="sxs-lookup"><span data-stu-id="f8747-188">Use this parameter when you need to reduce the size of the object returned, either in memory or over the network.</span></span> <span data-ttu-id="f8747-189">Det returnerade objektet innehåller också nyckel egenskaperna även om du inte har listat dem med **egenskaps** parametern.</span><span class="sxs-lookup"><span data-stu-id="f8747-189">The object returned also contains the key properties even if you have not listed them using the **Property** parameter.</span></span> <span data-ttu-id="f8747-190">Andra egenskaper för klassen finns, men de är inte ifyllda.</span><span class="sxs-lookup"><span data-stu-id="f8747-190">Other properties of the class are present but they are not populated.</span></span>

```yaml
Type: System.String[]
Parameter Sets: ClassNameComputerSet, ResourceUriSessionSet, ClassNameSessionSet, ResourceUriComputerSet
Aliases: SelectProperties

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="f8747-191">– Fråga</span><span class="sxs-lookup"><span data-stu-id="f8747-191">-Query</span></span>

<span data-ttu-id="f8747-192">Anger en fråga som ska köras på CIM-servern.</span><span class="sxs-lookup"><span data-stu-id="f8747-192">Specifies a query to run on the CIM server.</span></span> <span data-ttu-id="f8747-193">Om det angivna värdet innehåller dubbla citat tecken `"` , enkla citat tecken `'` eller ett omvänt snedstreck `\` måste du kringgå dessa tecken genom att prefixet med omvänt snedstreck.</span><span class="sxs-lookup"><span data-stu-id="f8747-193">If the value specified contains double quotes `"`, single quotes `'`, or a backslash `\`, you must escape those characters by prefixing them with the backslash character.</span></span> <span data-ttu-id="f8747-194">Om värdet som anges använder WQL-operatorn **som** operator måste du undanta följande tecken genom att omge dem med hakparenteser `[]` : procent `%` , under streck `_` eller inledande hak paren tes `[` .</span><span class="sxs-lookup"><span data-stu-id="f8747-194">If the value specified uses the WQL **LIKE** operator, then you must escape the following characters by enclosing them in square brackets `[]`: percent `%`, underscore `_`, or opening square bracket `[`.</span></span>

<span data-ttu-id="f8747-195">Du kan inte använda en fråga för metadata för att hämta en lista över klasser eller en händelse fråga.</span><span class="sxs-lookup"><span data-stu-id="f8747-195">You cannot use a metadata query to retrieve a list of classes or an event query.</span></span> <span data-ttu-id="f8747-196">Använd cmdleten om du vill hämta en lista över klasser `Get-CimClass` .</span><span class="sxs-lookup"><span data-stu-id="f8747-196">To retrieve a list of classes, use the `Get-CimClass` cmdlet.</span></span> <span data-ttu-id="f8747-197">Om du vill hämta en händelse fråga använder du `Register-CimIndicationEvent` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="f8747-197">To retrieve an event query, use the `Register-CimIndicationEvent` cmdlet.</span></span>

<span data-ttu-id="f8747-198">Du kan ange dialekten med hjälp av parametern **QueryDialect** .</span><span class="sxs-lookup"><span data-stu-id="f8747-198">You can specify the query dialect using the **QueryDialect** parameter.</span></span>

```yaml
Type: System.String
Parameter Sets: QuerySessionSet, QueryComputerSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="f8747-199">-QueryDialect</span><span class="sxs-lookup"><span data-stu-id="f8747-199">-QueryDialect</span></span>

<span data-ttu-id="f8747-200">Anger frågespråket som används för Frågeparametern.</span><span class="sxs-lookup"><span data-stu-id="f8747-200">Specifies the query language used for the Query parameter.</span></span> <span data-ttu-id="f8747-201">De acceptabla värdena för den här parametern är: **WQL** eller **CQL**.</span><span class="sxs-lookup"><span data-stu-id="f8747-201">The acceptable values for this parameter are: **WQL** or **CQL**.</span></span> <span data-ttu-id="f8747-202">Standardvärdet är **WQL**.</span><span class="sxs-lookup"><span data-stu-id="f8747-202">The default value is **WQL**.</span></span>

```yaml
Type: System.String
Parameter Sets: ClassNameComputerSet, QuerySessionSet, ClassNameSessionSet, QueryComputerSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="f8747-203">– ResourceUri</span><span class="sxs-lookup"><span data-stu-id="f8747-203">-ResourceUri</span></span>

<span data-ttu-id="f8747-204">Anger resurs-URI (Uniform Resource Identifier) för resurs klassen eller-instansen.</span><span class="sxs-lookup"><span data-stu-id="f8747-204">Specifies the resource uniform resource identifier (URI) of the resource class or instance.</span></span> <span data-ttu-id="f8747-205">URI: n används för att identifiera en speciell typ av resurs, till exempel diskar eller processer, på en dator.</span><span class="sxs-lookup"><span data-stu-id="f8747-205">The URI is used to identify a specific type of resource, such as disks or processes, on a computer.</span></span>

<span data-ttu-id="f8747-206">En URI består av ett prefix och en sökväg till en resurs.</span><span class="sxs-lookup"><span data-stu-id="f8747-206">A URI consists of a prefix and a path to a resource.</span></span> <span data-ttu-id="f8747-207">Ett exempel:</span><span class="sxs-lookup"><span data-stu-id="f8747-207">For example:</span></span>

- `http://schemas.microsoft.com/wbem/wsman/1/wmi/root/cimv2/Win32_LogicalDisk`
- `http://intel.com/wbem/wscim/1/amt-schema/1/AMT_GeneralSettings`

<span data-ttu-id="f8747-208">Om du inte anger den här parametern används DMTF-standardresurs-URI som standard `http://schemas.dmtf.org/wbem/wscim/1/cim-schema/2/` och klass namnet läggs till i den.</span><span class="sxs-lookup"><span data-stu-id="f8747-208">By default, if you do not specify this parameter, the DMTF standard resource URI `http://schemas.dmtf.org/wbem/wscim/1/cim-schema/2/` is used and the class name is appended to it.</span></span>

<span data-ttu-id="f8747-209">**ResourceURI** kan endast användas med CIM-sessioner som skapats med WSMan-protokollet, eller när du anger parametern **computername** , som skapar en CIM-session med hjälp av WSMan.</span><span class="sxs-lookup"><span data-stu-id="f8747-209">**ResourceURI** can only be used with CIM sessions created using the WSMan protocol, or when specifying the **ComputerName** parameter, which creates a CIM session using WSMan.</span></span> <span data-ttu-id="f8747-210">Om du anger den här parametern utan att ange parametern **computername** , eller om du anger en CIM-session som skapats med DCOM-protokollet, får du ett fel meddelande eftersom DCOM-protokollet inte stöder parametern **ResourceURI** .</span><span class="sxs-lookup"><span data-stu-id="f8747-210">If you specify this parameter without specifying the **ComputerName** parameter, or if you specify a CIM session created using DCOM protocol, you will get an error, because the DCOM protocol does not support the **ResourceURI** parameter.</span></span>

<span data-ttu-id="f8747-211">Om både den **ResourceUri** -parametern och **filter** parametern anges, ignoreras **filter** parametern.</span><span class="sxs-lookup"><span data-stu-id="f8747-211">If both the **ResourceUri** parameter and the **Filter** parameter are specified, the **Filter** parameter is ignored.</span></span>

```yaml
Type: System.Uri
Parameter Sets: ResourceUriSessionSet, ResourceUriComputerSet, QuerySessionSet, QueryComputerSet, CimInstanceSessionSet, CimInstanceComputerSet
Aliases:

Required: True (ResourceUriSessionSet, ResourceUriComputerSet), False (QuerySessionSet, QueryComputerSet, CimInstanceSessionSet, CimInstanceComputerSet)
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="f8747-212">– Lite</span><span class="sxs-lookup"><span data-stu-id="f8747-212">-Shallow</span></span>

<span data-ttu-id="f8747-213">Anger att instanserna av en klass returneras utan att inkludera instanser av underordnade klasser.</span><span class="sxs-lookup"><span data-stu-id="f8747-213">Indicates that the instances of a class are returned without including the instances of any child classes.</span></span> <span data-ttu-id="f8747-214">Som standard returnerar cmdleten instanserna för en klass och dess underordnade klasser.</span><span class="sxs-lookup"><span data-stu-id="f8747-214">By default, the cmdlet returns the instances of a class and its child classes.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ClassNameComputerSet, ResourceUriSessionSet, QuerySessionSet, ClassNameSessionSet, ResourceUriComputerSet, QueryComputerSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="f8747-215">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="f8747-215">CommonParameters</span></span>

<span data-ttu-id="f8747-216">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="f8747-216">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="f8747-217">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="f8747-217">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="f8747-218">INDATA</span><span class="sxs-lookup"><span data-stu-id="f8747-218">INPUTS</span></span>

### <span data-ttu-id="f8747-219">CIM-instans</span><span class="sxs-lookup"><span data-stu-id="f8747-219">CIM Instance</span></span>

<span data-ttu-id="f8747-220">Denna cmdlet accepterar ett inobjekt som anges med parametern InputObject.</span><span class="sxs-lookup"><span data-stu-id="f8747-220">This cmdlet accepts an input objects specified with the InputObject parameter.</span></span>

## <span data-ttu-id="f8747-221">UTDATA</span><span class="sxs-lookup"><span data-stu-id="f8747-221">OUTPUTS</span></span>

### <span data-ttu-id="f8747-222">CIM-instans</span><span class="sxs-lookup"><span data-stu-id="f8747-222">CIM Instance</span></span>

<span data-ttu-id="f8747-223">Denna cmdlet returnerar ett eller flera CIM-instanser som representerar en ögonblicks bild av CIM-instanserna på CIM-servern.</span><span class="sxs-lookup"><span data-stu-id="f8747-223">This cmdlet returns one or more CIM instance objects representing a snapshot of the CIM instances on the CIM server.</span></span>

## <span data-ttu-id="f8747-224">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="f8747-224">NOTES</span></span>

## <span data-ttu-id="f8747-225">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="f8747-225">RELATED LINKS</span></span>

[<span data-ttu-id="f8747-226">Format-Table</span><span class="sxs-lookup"><span data-stu-id="f8747-226">Format-Table</span></span>](../microsoft.powershell.utility/format-table.md)

[<span data-ttu-id="f8747-227">Get-CimAssociatedInstance</span><span class="sxs-lookup"><span data-stu-id="f8747-227">Get-CimAssociatedInstance</span></span>](Get-CimAssociatedInstance.md)

[<span data-ttu-id="f8747-228">Get-CimClass</span><span class="sxs-lookup"><span data-stu-id="f8747-228">Get-CimClass</span></span>](Get-CimClass.md)

[<span data-ttu-id="f8747-229">Invoke-CimMethod</span><span class="sxs-lookup"><span data-stu-id="f8747-229">Invoke-CimMethod</span></span>](invoke-cimmethod.md)

[<span data-ttu-id="f8747-230">New-CimInstance</span><span class="sxs-lookup"><span data-stu-id="f8747-230">New-CimInstance</span></span>](New-CimInstance.md)

[<span data-ttu-id="f8747-231">Registrera – CimIndicationEvent</span><span class="sxs-lookup"><span data-stu-id="f8747-231">Register-CimIndicationEvent</span></span>](Register-CimIndicationEvent.md)

[<span data-ttu-id="f8747-232">Remove-CimInstance</span><span class="sxs-lookup"><span data-stu-id="f8747-232">Remove-CimInstance</span></span>](remove-ciminstance.md)

[<span data-ttu-id="f8747-233">Set-CimInstance</span><span class="sxs-lookup"><span data-stu-id="f8747-233">Set-CimInstance</span></span>](Set-CimInstance.md)
