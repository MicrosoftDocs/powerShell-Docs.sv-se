---
external help file: Microsoft.Management.Infrastructure.CimCmdlets.dll-Help.xml
Locale: en-US
Module Name: CimCmdlets
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/cimcmdlets/new-ciminstance?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-CimInstance
ms.openlocfilehash: d81117ad6885d660e31f031bd8134096db91b7da
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94708558"
---
# <span data-ttu-id="7f4c1-102">New-CimInstance</span><span class="sxs-lookup"><span data-stu-id="7f4c1-102">New-CimInstance</span></span>

## <span data-ttu-id="7f4c1-103">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="7f4c1-103">SYNOPSIS</span></span>
<span data-ttu-id="7f4c1-104">Skapar en CIM-instans.</span><span class="sxs-lookup"><span data-stu-id="7f4c1-104">Creates a CIM instance.</span></span>

## <span data-ttu-id="7f4c1-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="7f4c1-105">SYNTAX</span></span>

### <span data-ttu-id="7f4c1-106">ClassNameComputerSet (standard)</span><span class="sxs-lookup"><span data-stu-id="7f4c1-106">ClassNameComputerSet (Default)</span></span>

```
New-CimInstance [-ClassName] <String> [-Key <String[]>] [[-Property] <IDictionary>]
 [-Namespace <String>] [-OperationTimeoutSec <UInt32>] [-ComputerName <String[]>] [-ClientOnly]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="7f4c1-107">ClassNameSessionSet</span><span class="sxs-lookup"><span data-stu-id="7f4c1-107">ClassNameSessionSet</span></span>

```
New-CimInstance [-ClassName] <String> [-Key <String[]>] [[-Property] <IDictionary>]
 [-Namespace <String>] [-OperationTimeoutSec <UInt32>] -CimSession <CimSession[]> [-ClientOnly]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="7f4c1-108">ResourceUriSessionSet</span><span class="sxs-lookup"><span data-stu-id="7f4c1-108">ResourceUriSessionSet</span></span>

```
New-CimInstance -ResourceUri <Uri> [-Key <String[]>] [[-Property] <IDictionary>]
 [-Namespace <String>] [-OperationTimeoutSec <UInt32>] -CimSession <CimSession[]> [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="7f4c1-109">ResourceUriComputerSet</span><span class="sxs-lookup"><span data-stu-id="7f4c1-109">ResourceUriComputerSet</span></span>

```
New-CimInstance -ResourceUri <Uri> [-Key <String[]>] [[-Property] <IDictionary>]
 [-Namespace <String>] [-OperationTimeoutSec <UInt32>] [-ComputerName <String[]>] [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="7f4c1-110">CimClassSessionSet</span><span class="sxs-lookup"><span data-stu-id="7f4c1-110">CimClassSessionSet</span></span>

```
New-CimInstance [-CimClass] <CimClass> [[-Property] <IDictionary>] [-OperationTimeoutSec <UInt32>]
 -CimSession <CimSession[]> [-ClientOnly] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="7f4c1-111">CimClassComputerSet</span><span class="sxs-lookup"><span data-stu-id="7f4c1-111">CimClassComputerSet</span></span>

```
New-CimInstance [-CimClass] <CimClass> [[-Property] <IDictionary>] [-OperationTimeoutSec <UInt32>]
 [-ComputerName <String[]>] [-ClientOnly] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="7f4c1-112">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="7f4c1-112">DESCRIPTION</span></span>

<span data-ttu-id="7f4c1-113">`New-CimInstance`Cmdleten skapar en instans av en CIM-klass baserat på klass definitionen på antingen den lokala datorn eller en fjärrdator.</span><span class="sxs-lookup"><span data-stu-id="7f4c1-113">The `New-CimInstance` cmdlet creates an instance of a CIM class based on the class definition on either the local computer or a remote computer.</span></span> <span data-ttu-id="7f4c1-114">Som standard `New-CimInstance` skapar cmdleten en instans på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="7f4c1-114">By default, the `New-CimInstance` cmdlet creates an instance on the local computer.</span></span>

## <span data-ttu-id="7f4c1-115">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="7f4c1-115">EXAMPLES</span></span>

### <span data-ttu-id="7f4c1-116">Exempel 1: skapa en instans av en CIM-klass</span><span class="sxs-lookup"><span data-stu-id="7f4c1-116">Example 1: Create an instance of a CIM class</span></span>

<span data-ttu-id="7f4c1-117">I det här exemplet skapas en instans av en CIM-klass med namnet win32_environment i namn området root/cimv2 på datorn.</span><span class="sxs-lookup"><span data-stu-id="7f4c1-117">This example creates an instance of a CIM Class named win32_environment in the root/cimv2 namespace on the computer.</span></span>

```powershell
New-CimInstance -ClassName Win32_Environment -Property @{Name="testvar";VariableValue="testvalue";UserName="domain\user"}
```

<span data-ttu-id="7f4c1-118">Ingen verifiering på klient sidan utförs om klassen inte finns, egenskaperna är fel eller om servern avvisar anropet.</span><span class="sxs-lookup"><span data-stu-id="7f4c1-118">No client side validation is performed if the class does not exist, the properties are wrong, or if the server rejects the call.</span></span> <span data-ttu-id="7f4c1-119">Om instansen har skapats, matar cmdleten ut den nyss skapade instansen.</span><span class="sxs-lookup"><span data-stu-id="7f4c1-119">If the instance is created successfully, the cmdlet outputs the newly created instance.</span></span>

### <span data-ttu-id="7f4c1-120">Exempel 2: skapa en instans av en CIM-klass med ett klass schema</span><span class="sxs-lookup"><span data-stu-id="7f4c1-120">Example 2: Create an instance of a CIM class using a class schema</span></span>

<span data-ttu-id="7f4c1-121">I det här exemplet hämtas ett CIM Class-objekt och lagras det i en variabel med namnet `$class` .</span><span class="sxs-lookup"><span data-stu-id="7f4c1-121">This example retrieves a CIM class object and stores it in a variable named `$class`.</span></span> <span data-ttu-id="7f4c1-122">Innehållet i variabeln skickas sedan till- `New-CimInstance` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="7f4c1-122">The contents of the variable are then passed to the `New-CimInstance` cmdlet.</span></span>

```powershell
$class = Get-CimClass -ClassName Win32_Environment
New-CimInstance -CimClass $class -Property @{Name="testvar";VariableValue="testvalue";UserName="Contoso\User1"}
```

### <span data-ttu-id="7f4c1-123">Exempel 3: skapa en dynamisk instans på klienten</span><span class="sxs-lookup"><span data-stu-id="7f4c1-123">Example 3: Create a dynamic instance on the client</span></span>

<span data-ttu-id="7f4c1-124">Det här exemplet skapar en dynamisk instans av en CIM-klass med namnet **Win32_Process** på klient datorn utan att hämta instansen från servern.</span><span class="sxs-lookup"><span data-stu-id="7f4c1-124">This example creates a dynamic instance of a CIM class named **Win32_Process** on the client computer without getting the instance from the server.</span></span> <span data-ttu-id="7f4c1-125">Den nya instansen lagras i variabeln `$a` .</span><span class="sxs-lookup"><span data-stu-id="7f4c1-125">The new instance is stored in the variable `$a`.</span></span> <span data-ttu-id="7f4c1-126">Den här dynamiska instansen kan användas för att utföra åtgärder om instansen med den här nyckeln finns på servern.</span><span class="sxs-lookup"><span data-stu-id="7f4c1-126">This dynamic instance can be used to perform operations if the instance with this key exists on the server.</span></span>

```powershell
$a = New-CimInstance -ClassName Win32_Process -Property @{Handle=0} -Key Handle -ClientOnly
Get-CimInstance -CimInstance $a
Invoke-CimMethod -CimInstance $a -MethodName GetOwner
```

```Output
ProcessId Name                HandleCount WorkingSetSize VirtualSize
--------- ----                ----------- -------------- -----------
0         System Idle Process 0           8192           8192

Domain         :
ReturnValue    : 2
User           :
PSComputerName :
```

<span data-ttu-id="7f4c1-127">`Get-CimInstance`Cmdlet: en hämtar sedan en viss instans.</span><span class="sxs-lookup"><span data-stu-id="7f4c1-127">The `Get-CimInstance` cmdlet then retrieves a particular single instance.</span></span> <span data-ttu-id="7f4c1-128">`Invoke-CimMethod`Cmdleten anropar metoden **GetOwner** på den hämtade instansen.</span><span class="sxs-lookup"><span data-stu-id="7f4c1-128">The `Invoke-CimMethod` cmdlet calls the **GetOwner** method on the retrieved instance.</span></span>

### <span data-ttu-id="7f4c1-129">Exempel 4: skapa en instans för en CIM-klass för en angiven namnrymd</span><span class="sxs-lookup"><span data-stu-id="7f4c1-129">Example 4: Create an instance for a CIM class of a specific namespace</span></span>

<span data-ttu-id="7f4c1-130">Det här exemplet hämtar en instans av en CIM-klass med namnet **MSFT_Something** i namn rymds **roten/någonstans** och lagrar den i en variabel med namnet `$class` .</span><span class="sxs-lookup"><span data-stu-id="7f4c1-130">This example gets an instance of a CIM class named **MSFT_Something** in the namespace **root/somewhere** and stores it in a variable named `$class`.</span></span> <span data-ttu-id="7f4c1-131">Variabeln skickas till cmdlet: `New-CimInstance` en för att skapa en ny CIM-instans och utföra verifieringar på klient sidan på den nya instansen.</span><span class="sxs-lookup"><span data-stu-id="7f4c1-131">The variable is passed to the `New-CimInstance` cmdlet to create a new CIM instance and perform client side validations on the new instance.</span></span>

```powershell
$class = Get-CimClass -ClassName MSFT_Something -Namespace root/somewhere
New-CimInstance -CimClass $class -Property @{"Prop1"=1;"Prop2"="value"} -ClientOnly
```

<span data-ttu-id="7f4c1-132">I det här exemplet kan du använda parametern **CimClass** i stället för parametern **className** för att verifiera att **Prop1** och **Prop2** faktiskt finns och att nycklarna har marker ATS som de ska.</span><span class="sxs-lookup"><span data-stu-id="7f4c1-132">In this example, using the **CimClass** parameter instead of the **ClassName** parameter validates that **Prop1** and **Prop2** actually exist and that the keys are marked correctly.</span></span>

<span data-ttu-id="7f4c1-133">Du kan inte använda parametern **computername** eller **CimSession** med parametern **ClientOnly** .</span><span class="sxs-lookup"><span data-stu-id="7f4c1-133">You cannot use the **ComputerName** or **CimSession** parameter with the **ClientOnly** parameter.</span></span>

## <span data-ttu-id="7f4c1-134">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="7f4c1-134">PARAMETERS</span></span>

### <span data-ttu-id="7f4c1-135">-CimClass</span><span class="sxs-lookup"><span data-stu-id="7f4c1-135">-CimClass</span></span>

<span data-ttu-id="7f4c1-136">Anger ett CIM-klassnamn som representerar instans typen.</span><span class="sxs-lookup"><span data-stu-id="7f4c1-136">Specifies a CIM class object that represents the type of the instance.</span></span> <span data-ttu-id="7f4c1-137">Använd `Get-CimClass` cmdleten för att hämta klass deklarationen från en dator.</span><span class="sxs-lookup"><span data-stu-id="7f4c1-137">Use the `Get-CimClass` cmdlet to retrieve the class declaration from a computer.</span></span> <span data-ttu-id="7f4c1-138">Genom att använda den här parametern resulterar det bättre verifieringar på klient sidan.</span><span class="sxs-lookup"><span data-stu-id="7f4c1-138">Using this parameter results in better client side schema validations.</span></span>

```yaml
Type: Microsoft.Management.Infrastructure.CimClass
Parameter Sets: CimClassSessionSet, CimClassComputerSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="7f4c1-139">– CimSession</span><span class="sxs-lookup"><span data-stu-id="7f4c1-139">-CimSession</span></span>

<span data-ttu-id="7f4c1-140">Kör kommandot med den angivna CIM-sessionen.</span><span class="sxs-lookup"><span data-stu-id="7f4c1-140">Runs the command using the specified CIM session.</span></span> <span data-ttu-id="7f4c1-141">Ange en variabel som innehåller CIM-sessionen, eller ett kommando som skapar eller hämtar CIM-sessionen, t. ex `New-CimSession` . eller- `Get-CimSession` cmdletar.</span><span class="sxs-lookup"><span data-stu-id="7f4c1-141">Enter a variable that contains the CIM session, or a command that creates or gets the CIM session, such as the `New-CimSession` or `Get-CimSession` cmdlets.</span></span> <span data-ttu-id="7f4c1-142">Mer information finns i [about_CimSession](../Microsoft.PowerShell.Core/About/about_CimSession.md).</span><span class="sxs-lookup"><span data-stu-id="7f4c1-142">For more information, see [about_CimSession](../Microsoft.PowerShell.Core/About/about_CimSession.md).</span></span>

```yaml
Type: Microsoft.Management.Infrastructure.CimSession[]
Parameter Sets: ClassNameSessionSet, ResourceUriSessionSet, CimClassSessionSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="7f4c1-143">-ClassName</span><span class="sxs-lookup"><span data-stu-id="7f4c1-143">-ClassName</span></span>

<span data-ttu-id="7f4c1-144">Anger namnet på CIM-klassen som åtgärden skapar en instans för.</span><span class="sxs-lookup"><span data-stu-id="7f4c1-144">Specifies the name of the CIM class of which the operation creates an instance.</span></span> <span data-ttu-id="7f4c1-145">Obs! Du kan använda TABB-slutförande för att bläddra i listan över klasser, eftersom PowerShell hämtar en lista över klasser från den lokala WMI-servern för att tillhandahålla en lista över klass namn.</span><span class="sxs-lookup"><span data-stu-id="7f4c1-145">NOTE: You can use tab completion to browse the list of classes, because PowerShell gets a list of classes from the local WMI server to provide a list of class names.</span></span>

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

### <span data-ttu-id="7f4c1-146">-ClientOnly</span><span class="sxs-lookup"><span data-stu-id="7f4c1-146">-ClientOnly</span></span>

<span data-ttu-id="7f4c1-147">Anger att instansen bara skapas i PowerShell utan att gå till CIM-servern.</span><span class="sxs-lookup"><span data-stu-id="7f4c1-147">Indicates that the instance is only created in PowerShell without going to the CIM server.</span></span> <span data-ttu-id="7f4c1-148">Du kan använda den här parametern för att skapa en intern CIM-instans för användning i efterföljande PowerShell-åtgärder.</span><span class="sxs-lookup"><span data-stu-id="7f4c1-148">You can use this parameter to create an in-memory CIM instance for use in subsequent PowerShell operations.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ClassNameComputerSet, ClassNameSessionSet, CimClassSessionSet, CimClassComputerSet
Aliases: Local

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="7f4c1-149">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="7f4c1-149">-ComputerName</span></span>

<span data-ttu-id="7f4c1-150">Anger namnet på den dator som du vill köra CIM-åtgärden på.</span><span class="sxs-lookup"><span data-stu-id="7f4c1-150">Specifies the name of the computer on which you want to run the CIM operation.</span></span> <span data-ttu-id="7f4c1-151">Du kan ange ett fullständigt kvalificerat domän namn (FQDN), ett NetBIOS-namn eller en IP-adress.</span><span class="sxs-lookup"><span data-stu-id="7f4c1-151">You can specify a fully qualified domain name (FQDN), a NetBIOS name, or an IP address.</span></span>

<span data-ttu-id="7f4c1-152">Om du anger den här parametern skapar cmdleten en tillfällig session till den angivna datorn med hjälp av WSMan-protokollet.</span><span class="sxs-lookup"><span data-stu-id="7f4c1-152">If you specify this parameter, the cmdlet creates a temporary session to the specified computer using the WSMan protocol.</span></span>

<span data-ttu-id="7f4c1-153">Om du inte anger den här parametern utför cmdleten åtgärden på den lokala datorn med hjälp av Component Object Model (COM).</span><span class="sxs-lookup"><span data-stu-id="7f4c1-153">If you do not specify this parameter, the cmdlet performs the operation on the local computer using Component Object Model (COM).</span></span>

<span data-ttu-id="7f4c1-154">Om flera åtgärder utförs på samma dator ger det bättre prestanda om du ansluter med en CIM-session.</span><span class="sxs-lookup"><span data-stu-id="7f4c1-154">If multiple operations are being performed on the same computer, connecting using a CIM session gives better performance.</span></span>

```yaml
Type: System.String[]
Parameter Sets: ClassNameComputerSet, ResourceUriComputerSet, CimClassComputerSet
Aliases: CN, ServerName

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="7f4c1-155">-Nyckel</span><span class="sxs-lookup"><span data-stu-id="7f4c1-155">-Key</span></span>

<span data-ttu-id="7f4c1-156">Anger de egenskaper som används som nycklar.</span><span class="sxs-lookup"><span data-stu-id="7f4c1-156">Specifies the properties that are used as keys.</span></span> <span data-ttu-id="7f4c1-157">Det går inte att använda **CimSession** och **computername** när **nyckeln** har angetts.</span><span class="sxs-lookup"><span data-stu-id="7f4c1-157">**CimSession** and **ComputerName** cannot be used when **Key** is specified.</span></span>

```yaml
Type: System.String[]
Parameter Sets: ClassNameComputerSet, ClassNameSessionSet, ResourceUriSessionSet, ResourceUriComputerSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="7f4c1-158">– Namnrymd</span><span class="sxs-lookup"><span data-stu-id="7f4c1-158">-Namespace</span></span>

<span data-ttu-id="7f4c1-159">Anger namn området för klassen för den nya instansen.</span><span class="sxs-lookup"><span data-stu-id="7f4c1-159">Specifies the namespace of the class for the new instance.</span></span> <span data-ttu-id="7f4c1-160">Standard namn området är **rot-/cimv2**.</span><span class="sxs-lookup"><span data-stu-id="7f4c1-160">The default namespace is **root/cimv2**.</span></span>
<span data-ttu-id="7f4c1-161">Du kan använda TABB-slutförande för att bläddra i listan över namn områden, eftersom PowerShell hämtar en lista över namn områden från den lokala WMI-servern för att tillhandahålla listan över namn områden.</span><span class="sxs-lookup"><span data-stu-id="7f4c1-161">You can use tab completion to browse the list of namespaces, because PowerShell gets a list of namespaces from the local WMI server to provide the list of namespaces.</span></span>

```yaml
Type: System.String
Parameter Sets: ClassNameComputerSet, ClassNameSessionSet, ResourceUriSessionSet, ResourceUriComputerSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="7f4c1-162">-OperationTimeoutSec</span><span class="sxs-lookup"><span data-stu-id="7f4c1-162">-OperationTimeoutSec</span></span>

<span data-ttu-id="7f4c1-163">Anger hur lång tid cmdleten väntar på ett svar från CIM-servern.</span><span class="sxs-lookup"><span data-stu-id="7f4c1-163">Specifies the amount of time that the cmdlet waits for a response from the CIM server.</span></span> <span data-ttu-id="7f4c1-164">Som standard är värdet för den här parametern 0, vilket innebär att cmdleten använder standardvärdet för timeout för servern.</span><span class="sxs-lookup"><span data-stu-id="7f4c1-164">By default, the value of this parameter is 0, which means that the cmdlet uses the default timeout value for the server.</span></span> <span data-ttu-id="7f4c1-165">Om **OperationTimeoutSec** -parametern har angetts till ett värde som är lägre än det stabila anslutnings försöket på 3 minuter, går det inte att återställa nätverks fel som sist mer än värdet för parametern **OperationTimeoutSec** , eftersom åtgärden på servern överskrider innan klienten kan återansluta.</span><span class="sxs-lookup"><span data-stu-id="7f4c1-165">If the **OperationTimeoutSec** parameter is set to a value less than the robust connection retry timeout of 3 minutes, network failures that last more than the value of the **OperationTimeoutSec** parameter are not recoverable, because the operation on the server times out before the client can reconnect.</span></span>

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

### <span data-ttu-id="7f4c1-166">– Egenskap</span><span class="sxs-lookup"><span data-stu-id="7f4c1-166">-Property</span></span>

<span data-ttu-id="7f4c1-167">Anger egenskaperna för CIM-instansen med hjälp av en hash-tabell (namn-värdepar).</span><span class="sxs-lookup"><span data-stu-id="7f4c1-167">Specifies the properties of the CIM instance using a hash table (name-value pairs).</span></span>

<span data-ttu-id="7f4c1-168">Om du anger parametern **CimClass** `New-CimInstance` utför cmdleten en egenskaps validering på klienten för att kontrol lera att de angivna egenskaperna är konsekventa med klass deklarationen på servern.</span><span class="sxs-lookup"><span data-stu-id="7f4c1-168">If you specify the **CimClass** parameter, then the `New-CimInstance` cmdlet performs a property validation on the client to make sure that the properties specified are consistent with the class declaration on the server.</span></span> <span data-ttu-id="7f4c1-169">Om parametern **CimClass** inte anges, utförs egenskaps valideringen på servern.</span><span class="sxs-lookup"><span data-stu-id="7f4c1-169">If the **CimClass** parameter is not specified, then the property validation is done on the server.</span></span>

```yaml
Type: System.Collections.IDictionary
Parameter Sets: (All)
Aliases: Arguments

Required: False
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="7f4c1-170">– ResourceUri</span><span class="sxs-lookup"><span data-stu-id="7f4c1-170">-ResourceUri</span></span>

<span data-ttu-id="7f4c1-171">Anger resurs-URI (Uniform Resource Identifier) för resurs klassen eller-instansen.</span><span class="sxs-lookup"><span data-stu-id="7f4c1-171">Specifies the resource uniform resource identifier (URI) of the resource class or instance.</span></span> <span data-ttu-id="7f4c1-172">URI: n används för att identifiera en speciell typ av resurs, till exempel diskar eller processer, på en dator.</span><span class="sxs-lookup"><span data-stu-id="7f4c1-172">The URI is used to identify a specific type of resource, such as disks or processes, on a computer.</span></span>

<span data-ttu-id="7f4c1-173">En URI består av ett prefix och en sökväg till en resurs.</span><span class="sxs-lookup"><span data-stu-id="7f4c1-173">A URI consists of a prefix and a path to a resource.</span></span> <span data-ttu-id="7f4c1-174">Exempel:</span><span class="sxs-lookup"><span data-stu-id="7f4c1-174">For example:</span></span>

`http://schemas.microsoft.com/wbem/wsman/1/wmi/root/cimv2/Win32_LogicalDisk`

`http://intel.com/wbem/wscim/1/amt-schema/1/AMT_GeneralSettings`

<span data-ttu-id="7f4c1-175">Om du inte anger den här parametern används DMTF-standardresurs-URI som standard `http://schemas.dmtf.org/wbem/wscim/1/cim-schema/2/` och klass namnet läggs till i den.</span><span class="sxs-lookup"><span data-stu-id="7f4c1-175">By default, if you do not specify this parameter, the DMTF standard resource URI `http://schemas.dmtf.org/wbem/wscim/1/cim-schema/2/` is used and the class name is appended to it.</span></span>

<span data-ttu-id="7f4c1-176">**ResourceURI** kan endast användas med CIM-sessioner som skapats med WSMan-protokollet, eller när du anger parametern **computername** , som skapar en CIM-session med hjälp av WSMan.</span><span class="sxs-lookup"><span data-stu-id="7f4c1-176">**ResourceURI** can only be used with CIM sessions created using the WSMan protocol, or when specifying the **ComputerName** parameter, which creates a CIM session using WSMan.</span></span> <span data-ttu-id="7f4c1-177">Om du anger den här parametern utan att ange parametern **computername** , eller om du anger en CIM-session som skapats med DCOM-protokollet, får du ett fel meddelande eftersom DCOM-protokollet inte stöder parametern **ResourceURI** .</span><span class="sxs-lookup"><span data-stu-id="7f4c1-177">If you specify this parameter without specifying the **ComputerName** parameter, or if you specify a CIM session created using DCOM protocol, you will get an error, because the DCOM protocol does not support the **ResourceURI** parameter.</span></span>

<span data-ttu-id="7f4c1-178">Om både den **ResourceUri** -parametern och **filter** parametern anges, ignoreras **filter** parametern.</span><span class="sxs-lookup"><span data-stu-id="7f4c1-178">If both the **ResourceUri** parameter and the **Filter** parameter are specified, the **Filter** parameter is ignored.</span></span>

```yaml
Type: System.Uri
Parameter Sets: ResourceUriSessionSet, ResourceUriComputerSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="7f4c1-179">-Confirm</span><span class="sxs-lookup"><span data-stu-id="7f4c1-179">-Confirm</span></span>

<span data-ttu-id="7f4c1-180">Uppmanar dig att bekräfta innan du kör cmdleten.</span><span class="sxs-lookup"><span data-stu-id="7f4c1-180">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="7f4c1-181">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="7f4c1-181">-WhatIf</span></span>

<span data-ttu-id="7f4c1-182">Visar vad som skulle hända om cmdleten kördes.</span><span class="sxs-lookup"><span data-stu-id="7f4c1-182">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="7f4c1-183">Cmdleten körs inte.</span><span class="sxs-lookup"><span data-stu-id="7f4c1-183">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="7f4c1-184">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="7f4c1-184">CommonParameters</span></span>

<span data-ttu-id="7f4c1-185">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="7f4c1-185">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="7f4c1-186">Mer information finns i [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span><span class="sxs-lookup"><span data-stu-id="7f4c1-186">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="7f4c1-187">INDATA</span><span class="sxs-lookup"><span data-stu-id="7f4c1-187">INPUTS</span></span>

### <span data-ttu-id="7f4c1-188">Inga</span><span class="sxs-lookup"><span data-stu-id="7f4c1-188">None</span></span>

<span data-ttu-id="7f4c1-189">Denna cmdlet accepterar inga inobjekt.</span><span class="sxs-lookup"><span data-stu-id="7f4c1-189">This cmdlet accepts no input objects.</span></span>

## <span data-ttu-id="7f4c1-190">UTDATA</span><span class="sxs-lookup"><span data-stu-id="7f4c1-190">OUTPUTS</span></span>

### <span data-ttu-id="7f4c1-191">System. Object</span><span class="sxs-lookup"><span data-stu-id="7f4c1-191">System.Object</span></span>

<span data-ttu-id="7f4c1-192">Den här cmdleten returnerar ett objekt som innehåller CIM-instansnamnet.</span><span class="sxs-lookup"><span data-stu-id="7f4c1-192">This cmdlet returns an object that contains the CIM instance information.</span></span>

## <span data-ttu-id="7f4c1-193">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="7f4c1-193">NOTES</span></span>

## <span data-ttu-id="7f4c1-194">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="7f4c1-194">RELATED LINKS</span></span>

[<span data-ttu-id="7f4c1-195">Get-CimClass</span><span class="sxs-lookup"><span data-stu-id="7f4c1-195">Get-CimClass</span></span>](get-cimclass.md)

[<span data-ttu-id="7f4c1-196">Get-CimInstance</span><span class="sxs-lookup"><span data-stu-id="7f4c1-196">Get-CimInstance</span></span>](get-ciminstance.md)

[<span data-ttu-id="7f4c1-197">Remove-CimInstance</span><span class="sxs-lookup"><span data-stu-id="7f4c1-197">Remove-CimInstance</span></span>](remove-ciminstance.md)

[<span data-ttu-id="7f4c1-198">Set-CimInstance</span><span class="sxs-lookup"><span data-stu-id="7f4c1-198">Set-CimInstance</span></span>](Set-CimInstance.md)

