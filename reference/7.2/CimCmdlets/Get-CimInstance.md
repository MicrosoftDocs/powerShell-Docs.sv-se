---
external help file: Microsoft.Management.Infrastructure.CimCmdlets.dll-Help.xml
Locale: en-US
Module Name: CimCmdlets
ms.date: 02/21/2019
online version: https://docs.microsoft.com/powershell/module/cimcmdlets/get-ciminstance?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-CimInstance
ms.openlocfilehash: 0e4a148601f3ef2212f9c97128c54258906106d7
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94708917"
---
# <span data-ttu-id="ef0f4-102">Get-CimInstance</span><span class="sxs-lookup"><span data-stu-id="ef0f4-102">Get-CimInstance</span></span>

## <span data-ttu-id="ef0f4-103">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="ef0f4-103">SYNOPSIS</span></span>
<span data-ttu-id="ef0f4-104">Hämtar CIM-instanser för en klass från en CIM-server.</span><span class="sxs-lookup"><span data-stu-id="ef0f4-104">Gets the CIM instances of a class from a CIM server.</span></span>

## <span data-ttu-id="ef0f4-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="ef0f4-105">SYNTAX</span></span>

### <span data-ttu-id="ef0f4-106">ClassNameComputerSet (standard)</span><span class="sxs-lookup"><span data-stu-id="ef0f4-106">ClassNameComputerSet (Default)</span></span>

```
Get-CimInstance [-ClassName] <String> [-ComputerName <String[]>] [-KeyOnly] [-Namespace <String>]
 [-OperationTimeoutSec <UInt32>] [-QueryDialect <String>] [-Shallow] [-Filter <String>]
 [-Property <String[]>] [<CommonParameters>]
```

### <span data-ttu-id="ef0f4-107">ResourceUriSessionSet</span><span class="sxs-lookup"><span data-stu-id="ef0f4-107">ResourceUriSessionSet</span></span>

```
Get-CimInstance -CimSession <CimSession[]> -ResourceUri <Uri> [-KeyOnly] [-Namespace <String>]
 [-OperationTimeoutSec <UInt32>] [-Shallow] [-Filter <String>] [-Property <String[]>]
 [<CommonParameters>]
```

### <span data-ttu-id="ef0f4-108">QuerySessionSet</span><span class="sxs-lookup"><span data-stu-id="ef0f4-108">QuerySessionSet</span></span>

```
Get-CimInstance -CimSession <CimSession[]> [-ResourceUri <Uri>] [-Namespace <String>]
 [-OperationTimeoutSec <UInt32>] -Query <String> [-QueryDialect <String>] [-Shallow]
 [<CommonParameters>]
```

### <span data-ttu-id="ef0f4-109">ClassNameSessionSet</span><span class="sxs-lookup"><span data-stu-id="ef0f4-109">ClassNameSessionSet</span></span>

```
Get-CimInstance -CimSession <CimSession[]> [-ClassName] <String> [-KeyOnly] [-Namespace <String>]
 [-OperationTimeoutSec <UInt32>] [-QueryDialect <String>] [-Shallow] [-Filter <String>]
 [-Property <String[]>] [<CommonParameters>]
```

### <span data-ttu-id="ef0f4-110">CimInstanceSessionSet</span><span class="sxs-lookup"><span data-stu-id="ef0f4-110">CimInstanceSessionSet</span></span>

```
Get-CimInstance -CimSession <CimSession[]> [-ResourceUri <Uri>] [-OperationTimeoutSec <UInt32>]
 [-InputObject] <CimInstance> [<CommonParameters>]
```

### <span data-ttu-id="ef0f4-111">CimInstanceComputerSet</span><span class="sxs-lookup"><span data-stu-id="ef0f4-111">CimInstanceComputerSet</span></span>

```
Get-CimInstance [-ResourceUri <Uri>] [-ComputerName <String[]>] [-OperationTimeoutSec <UInt32>]
 [-InputObject] <CimInstance> [<CommonParameters>]
```

### <span data-ttu-id="ef0f4-112">ResourceUriComputerSet</span><span class="sxs-lookup"><span data-stu-id="ef0f4-112">ResourceUriComputerSet</span></span>

```
Get-CimInstance -ResourceUri <Uri> [-ComputerName <String[]>] [-KeyOnly] [-Namespace <String>]
 [-OperationTimeoutSec <UInt32>] [-Shallow] [-Filter <String>] [-Property <String[]>]
 [<CommonParameters>]
```

### <span data-ttu-id="ef0f4-113">QueryComputerSet</span><span class="sxs-lookup"><span data-stu-id="ef0f4-113">QueryComputerSet</span></span>

```
Get-CimInstance [-ResourceUri <Uri>] [-ComputerName <String[]>] [-Namespace <String>]
 [-OperationTimeoutSec <UInt32>] -Query <String> [-QueryDialect <String>] [-Shallow]
 [<CommonParameters>]
```

## <span data-ttu-id="ef0f4-114">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="ef0f4-114">DESCRIPTION</span></span>

<span data-ttu-id="ef0f4-115">`Get-CimInstance`Cmdlet: en hämtar CIM-instanser för en klass från en CIM-server.</span><span class="sxs-lookup"><span data-stu-id="ef0f4-115">The `Get-CimInstance` cmdlet gets the CIM instances of a class from a CIM server.</span></span> <span data-ttu-id="ef0f4-116">Du kan ange antingen klass namnet eller en fråga för denna cmdlet.</span><span class="sxs-lookup"><span data-stu-id="ef0f4-116">You can specify either the class name or a query for this cmdlet.</span></span> <span data-ttu-id="ef0f4-117">Denna cmdlet returnerar ett eller flera CIM-instanser som representerar en ögonblicks bild av CIM-instanserna på CIM-servern.</span><span class="sxs-lookup"><span data-stu-id="ef0f4-117">This cmdlet returns one or more CIM instance objects representing a snapshot of the CIM instances present on the CIM server.</span></span>

<span data-ttu-id="ef0f4-118">Om parametern **InputObject** inte anges fungerar cmdleten på något av följande sätt:</span><span class="sxs-lookup"><span data-stu-id="ef0f4-118">If the **InputObject** parameter is not specified, the cmdlet works in one of the following ways:</span></span>

- <span data-ttu-id="ef0f4-119">Om varken parametern **computername** eller parametern **CimSession** anges, fungerar denna cmdlet på lokala Windows Management Instrumentation (WMI) med en Component Object Model (com)-session.</span><span class="sxs-lookup"><span data-stu-id="ef0f4-119">If neither the **ComputerName** parameter nor the **CimSession** parameter is specified, then this cmdlet works on local Windows Management Instrumentation (WMI) using a Component Object Model (COM) session.</span></span>
- <span data-ttu-id="ef0f4-120">Om antingen parametern **computername** eller parametern **CimSession** anges, fungerar denna cmdlet mot CIM-servern som anges av parametern **computername** eller parametern **CimSession** .</span><span class="sxs-lookup"><span data-stu-id="ef0f4-120">If either the **ComputerName** parameter or the **CimSession** parameter is specified, then this cmdlet works against the CIM server specified by either the **ComputerName** parameter or the **CimSession** parameter.</span></span>

<span data-ttu-id="ef0f4-121">Om parametern **InputObject** anges fungerar cmdleten på något av följande sätt:</span><span class="sxs-lookup"><span data-stu-id="ef0f4-121">If the **InputObject** parameter is specified, the cmdlet works in one of the following ways:</span></span>

- <span data-ttu-id="ef0f4-122">Om varken parametern **computername** eller parametern **CimSession** anges, använder denna cmdlet CIM-sessionen eller dator namnet från det indata-objektet.</span><span class="sxs-lookup"><span data-stu-id="ef0f4-122">If neither the **ComputerName** parameter nor the **CimSession** parameter is specified, then this cmdlet uses the CIM session or computer name from the input object.</span></span>
- <span data-ttu-id="ef0f4-123">Om antingen parametern **computername** eller parametern **CimSession** anges använder den här cmdleten antingen parametern CimSession eller värdet **computername** .</span><span class="sxs-lookup"><span data-stu-id="ef0f4-123">If the either the **ComputerName** parameter or the **CimSession** parameter is specified, then this cmdlet uses the either the CimSession parameter value or **ComputerName** parameter value.</span></span>

## <span data-ttu-id="ef0f4-124">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="ef0f4-124">EXAMPLES</span></span>

### <span data-ttu-id="ef0f4-125">Exempel 1: Hämta CIM-instanser för en angiven klass</span><span class="sxs-lookup"><span data-stu-id="ef0f4-125">Example 1: Get the CIM instances of a specified class</span></span>

<span data-ttu-id="ef0f4-126">I det här exemplet hämtas CIM-instanser för en klass med namnet **Win32_Process**.</span><span class="sxs-lookup"><span data-stu-id="ef0f4-126">This example retrieves the CIM instances of a class named **Win32_Process**.</span></span>

```powershell
Get-CimInstance -ClassName Win32_Process
```

### <span data-ttu-id="ef0f4-127">Exempel 2: Hämta en lista över namn områden från en WMI-Server</span><span class="sxs-lookup"><span data-stu-id="ef0f4-127">Example 2: Get a list of namespaces from a WMI server</span></span>

<span data-ttu-id="ef0f4-128">I det här exemplet hämtas en lista över namn områden under **rot** namn området på en WMI-Server.</span><span class="sxs-lookup"><span data-stu-id="ef0f4-128">This example retrieves a list of namespaces under the **Root** namespace on a WMI server.</span></span>

```powershell
Get-CimInstance -Namespace root -ClassName __Namespace
```

### <span data-ttu-id="ef0f4-129">Exempel 3: Hämta instanser av en klass filtrerad med hjälp av en fråga</span><span class="sxs-lookup"><span data-stu-id="ef0f4-129">Example 3: Get instances of a class filtered by using a query</span></span>

<span data-ttu-id="ef0f4-130">I det här exemplet hämtas alla CIM-instanser som börjar med bokstaven **P** i en klass med namnet **Win32_Process** med hjälp av frågan som anges av en **frågeparameter** .</span><span class="sxs-lookup"><span data-stu-id="ef0f4-130">This example retrieves all the CIM instances that start with the letter **P** of a class named **Win32_Process** using the query specified by a **Query** parameter.</span></span>

```powershell
Get-CimInstance -Query "SELECT * from Win32_Process WHERE name LIKE 'P%'"
```

### <span data-ttu-id="ef0f4-131">Exempel 4: Hämta instanser av en klass filtrerad med hjälp av ett klass namn och ett filter uttryck</span><span class="sxs-lookup"><span data-stu-id="ef0f4-131">Example 4: Get instances of a class filtered by using a class name and a filter expression</span></span>

<span data-ttu-id="ef0f4-132">I det här exemplet hämtas alla CIM-instanser som börjar med bokstaven **P** i en klass med namnet **Win32_Process** med hjälp av filter parametern.</span><span class="sxs-lookup"><span data-stu-id="ef0f4-132">This example retrieves all the CIM instances that start with the letter **P** of a class named **Win32_Process** using the Filter parameter.</span></span>

```powershell
Get-CimInstance -ClassName Win32_Process -Filter "Name like 'P%'"
```

### <span data-ttu-id="ef0f4-133">Exempel 5: Hämta CIM-instanserna med endast nyckel egenskaper ifyllda</span><span class="sxs-lookup"><span data-stu-id="ef0f4-133">Example 5: Get the CIM instances with only key properties filled in</span></span>

<span data-ttu-id="ef0f4-134">Det här exemplet skapar en ny CIM-instans i minnet för en klass med namnet **Win32_Process** med nyckel egenskapen `@{ "Handle"=0 }` och lagrar den i en variabel med namnet `$x` .</span><span class="sxs-lookup"><span data-stu-id="ef0f4-134">This example creates a new CIM instance in memory for a class named **Win32_Process** with the key property `@{ "Handle"=0 }` and stores it in a variable named `$x`.</span></span> <span data-ttu-id="ef0f4-135">Variabeln skickas som en CIM-instans till `Get-CimInstance` cmdleten för att hämta en viss instans.</span><span class="sxs-lookup"><span data-stu-id="ef0f4-135">The variable is passed as a CIM instance to the `Get-CimInstance` cmdlet to get a particular instance.</span></span>

```powershell
$x = New-CimInstance -ClassName Win32_Process -Namespace root\cimv2 -Property @{ "Handle"=0 } -Key Handle -ClientOnly
Get-CimInstance -CimInstance $x
```

### <span data-ttu-id="ef0f4-136">Exempel 6: Hämta CIM-instanser och återanvänd dem</span><span class="sxs-lookup"><span data-stu-id="ef0f4-136">Example 6: Retrieve CIM instances and reuse them</span></span>

<span data-ttu-id="ef0f4-137">Det här exemplet hämtar CIM-instanser av en klass med namnet **Win32_Process** och lagrar dem i variablerna `$x` och `$y` .</span><span class="sxs-lookup"><span data-stu-id="ef0f4-137">This example gets the CIM instances of a class named **Win32_Process** and stores them in the variables `$x` and `$y`.</span></span> <span data-ttu-id="ef0f4-138">Variabeln `$x` formateras sedan i en tabell som endast innehåller egenskaperna **Name** och **KernelModeTime** , vilken tabell som ska anpassas till **AutoSize**.</span><span class="sxs-lookup"><span data-stu-id="ef0f4-138">The variable `$x` is then formatted in a table containing only the **Name** and **KernelModeTime** properties, the table set to **AutoSize**.</span></span>

```powershell
$x,$y = Get-CimInstance -ClassName Win32_Process
$x | Format-Table -Property Name,KernelModeTime -AutoSize
```

```Output
Name                 KernelModeTime
----                 --------------
System Idle Process 157238797968750
```

### <span data-ttu-id="ef0f4-139">Exempel 7: Hämta CIM-instanser från fjärran sluten dator</span><span class="sxs-lookup"><span data-stu-id="ef0f4-139">Example 7: Get CIM instances from remote computer</span></span>

<span data-ttu-id="ef0f4-140">I det här exemplet hämtas CIM-instanser för en klass med namnet **Win32_ComputerSystem** från fjärrdatorerna med namnet **Server01** och **Server02**.</span><span class="sxs-lookup"><span data-stu-id="ef0f4-140">This example retrieves the CIM instances of a class named **Win32_ComputerSystem** from the remote computers named **Server01** and **Server02**.</span></span>

```powershell
Get-CimInstance -ClassName Win32_ComputerSystem -ComputerName Server01,Server02
```

### <span data-ttu-id="ef0f4-141">Exempel 8: Hämta bara nyckel egenskaperna, i stället för alla egenskaper</span><span class="sxs-lookup"><span data-stu-id="ef0f4-141">Example 8: Getting only the key properties, instead of all properties</span></span>

<span data-ttu-id="ef0f4-142">I det här exemplet hämtas bara nyckel egenskaperna, vilket minskar storleken på objektet och nätverks trafiken.</span><span class="sxs-lookup"><span data-stu-id="ef0f4-142">This example retrieves only the key properties, which reduces the size of the object and network traffic.</span></span>

```powershell
$x = Get-CimInstance -Class Win32_Process -KeyOnly
$x | Invoke-CimMethod -MethodName GetOwner
```

### <span data-ttu-id="ef0f4-143">Exempel 9: bara hämta en delmängd av egenskaperna, i stället för alla egenskaper</span><span class="sxs-lookup"><span data-stu-id="ef0f4-143">Example 9: Getting only a subset of properties, instead of all properties</span></span>

<span data-ttu-id="ef0f4-144">I det här exemplet hämtas endast en del av egenskaperna, vilket minskar storleken på objektet och nätverks trafiken.</span><span class="sxs-lookup"><span data-stu-id="ef0f4-144">This example retrieves only a subset of properties, which reduces the size of the object and network traffic.</span></span>

```powershell
Get-CimInstance -Class Win32_Process -Property Name,KernelModeTime
$x = Get-CimInstance -Class Win32_Process -Property Name,KernelModeTime
$x | Invoke-CimMethod -MethodName GetOwner
```

<span data-ttu-id="ef0f4-145">Instansen som hämtades med **egenskaps** parametern kan användas för att utföra andra CIM-åtgärder, till exempel `Set-CimInstance` eller `Invoke-CimMethod` .</span><span class="sxs-lookup"><span data-stu-id="ef0f4-145">The instance retrieved with the **Property** parameter can be used to perform other CIM operations, for example `Set-CimInstance` or `Invoke-CimMethod`.</span></span>

### <span data-ttu-id="ef0f4-146">Exempel 10: Hämta CIM-instansen med CIM-sessionen</span><span class="sxs-lookup"><span data-stu-id="ef0f4-146">Example 10: Get the CIM instance using CIM session</span></span>

<span data-ttu-id="ef0f4-147">I det här exemplet skapas en CIM-session på datorerna med namnet **Server01** och **Server02** med hjälp av `New-CimSession` cmdleten och lagras sessionsinformation i en variabel med namnet `$s` .</span><span class="sxs-lookup"><span data-stu-id="ef0f4-147">This example creates a CIM session on the computers named **Server01** and **Server02** using the `New-CimSession` cmdlet and stores the session information in a variable named `$s`.</span></span> <span data-ttu-id="ef0f4-148">Innehållet i variabeln skickas sedan till `Get-CimInstance` med hjälp av parametern **CimSession** för att hämta CIM-instanser av klassen med namnet **Win32_ComputerSystem**.</span><span class="sxs-lookup"><span data-stu-id="ef0f4-148">The contents of the variable are then passed to `Get-CimInstance` by using the **CimSession** parameter, to get the CIM instances of the class named **Win32_ComputerSystem**.</span></span>

```powershell
$s = New-CimSession -ComputerName Server01,Server02
Get-CimInstance -ClassName Win32_ComputerSystem -CimSession $s
```

## <span data-ttu-id="ef0f4-149">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="ef0f4-149">PARAMETERS</span></span>

### <span data-ttu-id="ef0f4-150">– CimSession</span><span class="sxs-lookup"><span data-stu-id="ef0f4-150">-CimSession</span></span>

<span data-ttu-id="ef0f4-151">Anger den CIM-session som ska användas för denna cmdlet.</span><span class="sxs-lookup"><span data-stu-id="ef0f4-151">Specifies the CIM session to use for this cmdlet.</span></span> <span data-ttu-id="ef0f4-152">Ange en variabel som innehåller CIM-sessionen eller ett kommando som skapar eller hämtar CIM-sessionen, till exempel `New-CimSession` `Get-CimSession` cmdletarna eller.</span><span class="sxs-lookup"><span data-stu-id="ef0f4-152">Enter a variable that contains the CIM session or a command that creates or gets the CIM session, such as the `New-CimSession` or `Get-CimSession` cmdlets.</span></span> <span data-ttu-id="ef0f4-153">Mer information finns i [about_CimSession](../Microsoft.PowerShell.Core/About/about_CimSession.md).</span><span class="sxs-lookup"><span data-stu-id="ef0f4-153">For more information, see [about_CimSession](../Microsoft.PowerShell.Core/About/about_CimSession.md).</span></span>

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

### <span data-ttu-id="ef0f4-154">-ClassName</span><span class="sxs-lookup"><span data-stu-id="ef0f4-154">-ClassName</span></span>

<span data-ttu-id="ef0f4-155">Anger namnet på CIM-klassen som CIM-instanserna ska hämtas för.</span><span class="sxs-lookup"><span data-stu-id="ef0f4-155">Specifies the name of the CIM class for which to retrieve the CIM instances.</span></span> <span data-ttu-id="ef0f4-156">Du kan använda TABB-slutförande för att bläddra i listan över klasser, eftersom PowerShell hämtar en lista över klasser från den lokala WMI-servern för att tillhandahålla en lista över klass namn.</span><span class="sxs-lookup"><span data-stu-id="ef0f4-156">You can use tab completion to browse the list of classes, because PowerShell gets a list of classes from the local WMI server to provide a list of class names.</span></span>

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

### <span data-ttu-id="ef0f4-157">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="ef0f4-157">-ComputerName</span></span>

<span data-ttu-id="ef0f4-158">Anger den dator där du vill köra CIM-åtgärden.</span><span class="sxs-lookup"><span data-stu-id="ef0f4-158">Specifies computer on which you want to run the CIM operation.</span></span> <span data-ttu-id="ef0f4-159">Du kan ange ett fullständigt kvalificerat domän namn (FQDN), ett NetBIOS-namn eller en IP-adress.</span><span class="sxs-lookup"><span data-stu-id="ef0f4-159">You can specify a fully qualified domain name (FQDN), a NetBIOS name, or an IP address.</span></span> <span data-ttu-id="ef0f4-160">Om du inte anger den här parametern utför cmdleten åtgärden på den lokala datorn med hjälp av Component Object Model (COM).</span><span class="sxs-lookup"><span data-stu-id="ef0f4-160">If you do not specify this parameter, the cmdlet performs the operation on the local computer using Component Object Model (COM).</span></span>

<span data-ttu-id="ef0f4-161">Om du anger den här parametern skapar cmdleten en tillfällig session till den angivna datorn med hjälp av WsMan-protokollet.</span><span class="sxs-lookup"><span data-stu-id="ef0f4-161">If you specify this parameter, the cmdlet creates a temporary session to the specified computer using the WsMan protocol.</span></span>

<span data-ttu-id="ef0f4-162">Om flera åtgärder utförs på samma dator ansluter du med en CIM-session för bättre prestanda.</span><span class="sxs-lookup"><span data-stu-id="ef0f4-162">If multiple operations are being performed on the same computer, connect using a CIM session for better performance.</span></span>

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

### <span data-ttu-id="ef0f4-163">-Filter</span><span class="sxs-lookup"><span data-stu-id="ef0f4-163">-Filter</span></span>

<span data-ttu-id="ef0f4-164">Anger en WHERE-sats som ska användas som ett filter.</span><span class="sxs-lookup"><span data-stu-id="ef0f4-164">Specifies a where clause to use as a filter.</span></span> <span data-ttu-id="ef0f4-165">Ange satsen i antingen **WQL** -eller **CQL** -frågespråket.</span><span class="sxs-lookup"><span data-stu-id="ef0f4-165">Specify the clause in either the **WQL** or the **CQL** query language.</span></span> <span data-ttu-id="ef0f4-166">Ta inte med `WHERE` nyckelordet i parameterns värde.</span><span class="sxs-lookup"><span data-stu-id="ef0f4-166">Do not include the `WHERE` keyword in the value of the parameter.</span></span>

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

### <span data-ttu-id="ef0f4-167">– InputObject</span><span class="sxs-lookup"><span data-stu-id="ef0f4-167">-InputObject</span></span>

<span data-ttu-id="ef0f4-168">Anger ett CIM-instansnamn som ska användas som indatakälla.</span><span class="sxs-lookup"><span data-stu-id="ef0f4-168">Specifies a CIM instance object to use as input.</span></span>

<span data-ttu-id="ef0f4-169">Om du redan arbetar med ett CIM-instansnamn kan du använda den här parametern för att skicka CIM-instansnamnet för att hämta den senaste ögonblicks bilden från CIM-servern.</span><span class="sxs-lookup"><span data-stu-id="ef0f4-169">If you are already working with a CIM instance object, you can use this parameter to pass the CIM instance object in order to get the latest snapshot from the CIM server.</span></span> <span data-ttu-id="ef0f4-170">När du skickar ett CIM-instansnamn som inmatat, `Get-CimInstance` returnerar objektet från servern med hjälp av en get CIM-åtgärd, i stället för en uppräknings-eller fråga-åtgärd.</span><span class="sxs-lookup"><span data-stu-id="ef0f4-170">When you pass a CIM instance object as an input, `Get-CimInstance` returns the object from server using a get CIM operation, instead of an enumerate or query operation.</span></span> <span data-ttu-id="ef0f4-171">Att använda en get CIM-åtgärd är mer effektivt än att hämta alla instanser och sedan filtrera dem.</span><span class="sxs-lookup"><span data-stu-id="ef0f4-171">Using a get CIM operation is more efficient than retrieving all instances and then filtering them.</span></span>

<span data-ttu-id="ef0f4-172">Om CIM-klassen inte implementerar get-åtgärden returnerar **InputObject** -parametern ett fel.</span><span class="sxs-lookup"><span data-stu-id="ef0f4-172">If the CIM class does not implement the get operation, then specifying the **InputObject** parameter returns an error.</span></span>

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

### <span data-ttu-id="ef0f4-173">-KeyOnly</span><span class="sxs-lookup"><span data-stu-id="ef0f4-173">-KeyOnly</span></span>

<span data-ttu-id="ef0f4-174">Anger att endast objekt med nyckel egenskaper som är ifyllda returneras.</span><span class="sxs-lookup"><span data-stu-id="ef0f4-174">Indicates that only objects with key properties populated are returned.</span></span> <span data-ttu-id="ef0f4-175">Om du anger parametern för **endast** parametern minskas mängden data som överförs över nätverket.</span><span class="sxs-lookup"><span data-stu-id="ef0f4-175">Specifying the **KeyOnly** parameter reduces the amount of data transferred over the network.</span></span>

<span data-ttu-id="ef0f4-176">Använd parametern **endast** tangenten om du bara vill returnera en liten del av objektet, som kan användas för andra åtgärder, t `Set-CimInstance` . ex. eller- `Get-CimAssociatedInstance` cmdletar.</span><span class="sxs-lookup"><span data-stu-id="ef0f4-176">Use the **KeyOnly** parameter to return only a small portion of the object, which can be used for other operations, such as the `Set-CimInstance` or `Get-CimAssociatedInstance` cmdlets.</span></span>

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

### <span data-ttu-id="ef0f4-177">– Namnrymd</span><span class="sxs-lookup"><span data-stu-id="ef0f4-177">-Namespace</span></span>

<span data-ttu-id="ef0f4-178">Anger namn området för CIM-klassen.</span><span class="sxs-lookup"><span data-stu-id="ef0f4-178">Specifies the namespace of CIM class.</span></span>

<span data-ttu-id="ef0f4-179">Standard namn området är **rot-/cimv2**.</span><span class="sxs-lookup"><span data-stu-id="ef0f4-179">The default namespace is **root/cimv2**.</span></span> <span data-ttu-id="ef0f4-180">Du kan använda TABB-slutförande för att bläddra i listan över namn områden, eftersom PowerShell hämtar en lista över namn områden från den lokala WMI-servern för att tillhandahålla listan över namn områden.</span><span class="sxs-lookup"><span data-stu-id="ef0f4-180">You can use tab completion to browse the list of namespaces, because PowerShell gets a list of namespaces from the local WMI server to provide the list of namespaces.</span></span>

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

### <span data-ttu-id="ef0f4-181">-OperationTimeoutSec</span><span class="sxs-lookup"><span data-stu-id="ef0f4-181">-OperationTimeoutSec</span></span>

<span data-ttu-id="ef0f4-182">Anger hur lång tid cmdleten väntar på ett svar från datorn.</span><span class="sxs-lookup"><span data-stu-id="ef0f4-182">Specifies the amount of time that the cmdlet waits for a response from the computer.</span></span> <span data-ttu-id="ef0f4-183">Som standard är värdet för den här parametern 0, vilket innebär att cmdleten använder standardvärdet för timeout för servern.</span><span class="sxs-lookup"><span data-stu-id="ef0f4-183">By default, the value of this parameter is 0, which means that the cmdlet uses the default timeout value for the server.</span></span>

<span data-ttu-id="ef0f4-184">Om **OperationTimeoutSec** -parametern har angetts till ett värde som är lägre än det stabila anslutnings försöket på 3 minuter, går det inte att återställa nätverks fel som sist mer än värdet för parametern **OperationTimeoutSec** , eftersom åtgärden på servern överskrider innan klienten kan återansluta.</span><span class="sxs-lookup"><span data-stu-id="ef0f4-184">If the **OperationTimeoutSec** parameter is set to a value less than the robust connection retry timeout of 3 minutes, network failures that last more than the value of the **OperationTimeoutSec** parameter are not recoverable, because the operation on the server times out before the client can reconnect.</span></span>

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

### <span data-ttu-id="ef0f4-185">– Egenskap</span><span class="sxs-lookup"><span data-stu-id="ef0f4-185">-Property</span></span>

<span data-ttu-id="ef0f4-186">Anger en uppsättning instans egenskaper som ska hämtas.</span><span class="sxs-lookup"><span data-stu-id="ef0f4-186">Specifies a set of instance properties to retrieve.</span></span> <span data-ttu-id="ef0f4-187">Använd den här parametern när du behöver minska storleken på det returnerade objektet, antingen i minnet eller i nätverket.</span><span class="sxs-lookup"><span data-stu-id="ef0f4-187">Use this parameter when you need to reduce the size of the object returned, either in memory or over the network.</span></span> <span data-ttu-id="ef0f4-188">Det returnerade objektet innehåller också nyckel egenskaperna även om du inte har listat dem med **egenskaps** parametern.</span><span class="sxs-lookup"><span data-stu-id="ef0f4-188">The object returned also contains the key properties even if you have not listed them using the **Property** parameter.</span></span> <span data-ttu-id="ef0f4-189">Andra egenskaper för klassen finns, men de är inte ifyllda.</span><span class="sxs-lookup"><span data-stu-id="ef0f4-189">Other properties of the class are present but they are not populated.</span></span>

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

### <span data-ttu-id="ef0f4-190">– Fråga</span><span class="sxs-lookup"><span data-stu-id="ef0f4-190">-Query</span></span>

<span data-ttu-id="ef0f4-191">Anger en fråga som ska köras på CIM-servern.</span><span class="sxs-lookup"><span data-stu-id="ef0f4-191">Specifies a query to run on the CIM server.</span></span> <span data-ttu-id="ef0f4-192">Om det angivna värdet innehåller dubbla citat tecken `"` , enkla citat tecken `'` eller ett omvänt snedstreck `\` måste du kringgå dessa tecken genom att prefixet med omvänt snedstreck.</span><span class="sxs-lookup"><span data-stu-id="ef0f4-192">If the value specified contains double quotes `"`, single quotes `'`, or a backslash `\`, you must escape those characters by prefixing them with the backslash character.</span></span> <span data-ttu-id="ef0f4-193">Om värdet som anges använder WQL-operatorn **som** operator måste du undanta följande tecken genom att omge dem med hakparenteser `[]` : procent `%` , under streck `_` eller inledande hak paren tes `[` .</span><span class="sxs-lookup"><span data-stu-id="ef0f4-193">If the value specified uses the WQL **LIKE** operator, then you must escape the following characters by enclosing them in square brackets `[]`: percent `%`, underscore `_`, or opening square bracket `[`.</span></span>

<span data-ttu-id="ef0f4-194">Du kan inte använda en fråga för metadata för att hämta en lista över klasser eller en händelse fråga.</span><span class="sxs-lookup"><span data-stu-id="ef0f4-194">You cannot use a metadata query to retrieve a list of classes or an event query.</span></span> <span data-ttu-id="ef0f4-195">Använd cmdleten om du vill hämta en lista över klasser `Get-CimClass` .</span><span class="sxs-lookup"><span data-stu-id="ef0f4-195">To retrieve a list of classes, use the `Get-CimClass` cmdlet.</span></span> <span data-ttu-id="ef0f4-196">Om du vill hämta en händelse fråga använder du `Register-CimIndicationEvent` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="ef0f4-196">To retrieve an event query, use the `Register-CimIndicationEvent` cmdlet.</span></span>

<span data-ttu-id="ef0f4-197">Du kan ange dialekten med hjälp av parametern **QueryDialect** .</span><span class="sxs-lookup"><span data-stu-id="ef0f4-197">You can specify the query dialect using the **QueryDialect** parameter.</span></span>

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

### <span data-ttu-id="ef0f4-198">-QueryDialect</span><span class="sxs-lookup"><span data-stu-id="ef0f4-198">-QueryDialect</span></span>

<span data-ttu-id="ef0f4-199">Anger frågespråket som används för Frågeparametern.</span><span class="sxs-lookup"><span data-stu-id="ef0f4-199">Specifies the query language used for the Query parameter.</span></span> <span data-ttu-id="ef0f4-200">De acceptabla värdena för den här parametern är: **WQL** eller **CQL**.</span><span class="sxs-lookup"><span data-stu-id="ef0f4-200">The acceptable values for this parameter are: **WQL** or **CQL**.</span></span> <span data-ttu-id="ef0f4-201">Standardvärdet är **WQL**.</span><span class="sxs-lookup"><span data-stu-id="ef0f4-201">The default value is **WQL**.</span></span>

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

### <span data-ttu-id="ef0f4-202">– ResourceUri</span><span class="sxs-lookup"><span data-stu-id="ef0f4-202">-ResourceUri</span></span>

<span data-ttu-id="ef0f4-203">Anger resurs-URI (Uniform Resource Identifier) för resurs klassen eller-instansen.</span><span class="sxs-lookup"><span data-stu-id="ef0f4-203">Specifies the resource uniform resource identifier (URI) of the resource class or instance.</span></span> <span data-ttu-id="ef0f4-204">URI: n används för att identifiera en speciell typ av resurs, till exempel diskar eller processer, på en dator.</span><span class="sxs-lookup"><span data-stu-id="ef0f4-204">The URI is used to identify a specific type of resource, such as disks or processes, on a computer.</span></span>

<span data-ttu-id="ef0f4-205">En URI består av ett prefix och en sökväg till en resurs.</span><span class="sxs-lookup"><span data-stu-id="ef0f4-205">A URI consists of a prefix and a path to a resource.</span></span> <span data-ttu-id="ef0f4-206">Exempel:</span><span class="sxs-lookup"><span data-stu-id="ef0f4-206">For example:</span></span>

- `http://schemas.microsoft.com/wbem/wsman/1/wmi/root/cimv2/Win32_LogicalDisk`
- `http://intel.com/wbem/wscim/1/amt-schema/1/AMT_GeneralSettings`

<span data-ttu-id="ef0f4-207">Om du inte anger den här parametern används DMTF-standardresurs-URI som standard `http://schemas.dmtf.org/wbem/wscim/1/cim-schema/2/` och klass namnet läggs till i den.</span><span class="sxs-lookup"><span data-stu-id="ef0f4-207">By default, if you do not specify this parameter, the DMTF standard resource URI `http://schemas.dmtf.org/wbem/wscim/1/cim-schema/2/` is used and the class name is appended to it.</span></span>

<span data-ttu-id="ef0f4-208">**ResourceURI** kan endast användas med CIM-sessioner som skapats med WSMan-protokollet, eller när du anger parametern **computername** , som skapar en CIM-session med hjälp av WSMan.</span><span class="sxs-lookup"><span data-stu-id="ef0f4-208">**ResourceURI** can only be used with CIM sessions created using the WSMan protocol, or when specifying the **ComputerName** parameter, which creates a CIM session using WSMan.</span></span> <span data-ttu-id="ef0f4-209">Om du anger den här parametern utan att ange parametern **computername** , eller om du anger en CIM-session som skapats med DCOM-protokollet, får du ett fel meddelande eftersom DCOM-protokollet inte stöder parametern **ResourceURI** .</span><span class="sxs-lookup"><span data-stu-id="ef0f4-209">If you specify this parameter without specifying the **ComputerName** parameter, or if you specify a CIM session created using DCOM protocol, you will get an error, because the DCOM protocol does not support the **ResourceURI** parameter.</span></span>

<span data-ttu-id="ef0f4-210">Om både den **ResourceUri** -parametern och **filter** parametern anges, ignoreras **filter** parametern.</span><span class="sxs-lookup"><span data-stu-id="ef0f4-210">If both the **ResourceUri** parameter and the **Filter** parameter are specified, the **Filter** parameter is ignored.</span></span>

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

### <span data-ttu-id="ef0f4-211">– Lite</span><span class="sxs-lookup"><span data-stu-id="ef0f4-211">-Shallow</span></span>

<span data-ttu-id="ef0f4-212">Anger att instanserna av en klass returneras utan att inkludera instanser av underordnade klasser.</span><span class="sxs-lookup"><span data-stu-id="ef0f4-212">Indicates that the instances of a class are returned without including the instances of any child classes.</span></span> <span data-ttu-id="ef0f4-213">Som standard returnerar cmdleten instanserna för en klass och dess underordnade klasser.</span><span class="sxs-lookup"><span data-stu-id="ef0f4-213">By default, the cmdlet returns the instances of a class and its child classes.</span></span>

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

### <span data-ttu-id="ef0f4-214">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="ef0f4-214">CommonParameters</span></span>

<span data-ttu-id="ef0f4-215">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="ef0f4-215">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="ef0f4-216">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="ef0f4-216">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="ef0f4-217">INDATA</span><span class="sxs-lookup"><span data-stu-id="ef0f4-217">INPUTS</span></span>

### <span data-ttu-id="ef0f4-218">CIM-instans</span><span class="sxs-lookup"><span data-stu-id="ef0f4-218">CIM Instance</span></span>

<span data-ttu-id="ef0f4-219">Denna cmdlet accepterar ett inobjekt som anges med parametern InputObject.</span><span class="sxs-lookup"><span data-stu-id="ef0f4-219">This cmdlet accepts an input objects specified with the InputObject parameter.</span></span>

## <span data-ttu-id="ef0f4-220">UTDATA</span><span class="sxs-lookup"><span data-stu-id="ef0f4-220">OUTPUTS</span></span>

### <span data-ttu-id="ef0f4-221">CIM-instans</span><span class="sxs-lookup"><span data-stu-id="ef0f4-221">CIM Instance</span></span>

<span data-ttu-id="ef0f4-222">Denna cmdlet returnerar ett eller flera CIM-instanser som representerar en ögonblicks bild av CIM-instanserna på CIM-servern.</span><span class="sxs-lookup"><span data-stu-id="ef0f4-222">This cmdlet returns one or more CIM instance objects representing a snapshot of the CIM instances on the CIM server.</span></span>

## <span data-ttu-id="ef0f4-223">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="ef0f4-223">NOTES</span></span>

## <span data-ttu-id="ef0f4-224">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="ef0f4-224">RELATED LINKS</span></span>

[<span data-ttu-id="ef0f4-225">Format-Table</span><span class="sxs-lookup"><span data-stu-id="ef0f4-225">Format-Table</span></span>](../microsoft.powershell.utility/format-table.md)

[<span data-ttu-id="ef0f4-226">Get-CimAssociatedInstance</span><span class="sxs-lookup"><span data-stu-id="ef0f4-226">Get-CimAssociatedInstance</span></span>](Get-CimAssociatedInstance.md)

[<span data-ttu-id="ef0f4-227">Get-CimClass</span><span class="sxs-lookup"><span data-stu-id="ef0f4-227">Get-CimClass</span></span>](Get-CimClass.md)

[<span data-ttu-id="ef0f4-228">Invoke-CimMethod</span><span class="sxs-lookup"><span data-stu-id="ef0f4-228">Invoke-CimMethod</span></span>](invoke-cimmethod.md)

[<span data-ttu-id="ef0f4-229">New-CimInstance</span><span class="sxs-lookup"><span data-stu-id="ef0f4-229">New-CimInstance</span></span>](New-CimInstance.md)

[<span data-ttu-id="ef0f4-230">Registrera – CimIndicationEvent</span><span class="sxs-lookup"><span data-stu-id="ef0f4-230">Register-CimIndicationEvent</span></span>](Register-CimIndicationEvent.md)

[<span data-ttu-id="ef0f4-231">Remove-CimInstance</span><span class="sxs-lookup"><span data-stu-id="ef0f4-231">Remove-CimInstance</span></span>](remove-ciminstance.md)

[<span data-ttu-id="ef0f4-232">Set-CimInstance</span><span class="sxs-lookup"><span data-stu-id="ef0f4-232">Set-CimInstance</span></span>](Set-CimInstance.md)

