---
external help file: Microsoft.Management.Infrastructure.CimCmdlets.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: CimCmdlets
ms.date: 01/21/2020
online version: https://docs.microsoft.com/powershell/module/cimcmdlets/invoke-cimmethod?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Invoke-CimMethod
ms.openlocfilehash: 328abb5776366f6e2d9b5106c93337f5d45533ed
ms.sourcegitcommit: 37abf054ad9eda8813be8ff4487803b10e1842ef
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/23/2020
ms.locfileid: "93268119"
---
# <span data-ttu-id="f2ebf-103">Invoke-CimMethod</span><span class="sxs-lookup"><span data-stu-id="f2ebf-103">Invoke-CimMethod</span></span>

## <span data-ttu-id="f2ebf-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="f2ebf-104">SYNOPSIS</span></span>
<span data-ttu-id="f2ebf-105">Anropar en metod i en CIM-klass.</span><span class="sxs-lookup"><span data-stu-id="f2ebf-105">Invokes a method of a CIM class.</span></span>

## <span data-ttu-id="f2ebf-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="f2ebf-106">SYNTAX</span></span>

### <span data-ttu-id="f2ebf-107">ClassNameComputerSet (standard)</span><span class="sxs-lookup"><span data-stu-id="f2ebf-107">ClassNameComputerSet (Default)</span></span>

```
Invoke-CimMethod [-ClassName] <String> [-ComputerName <String[]>] [[-Arguments] <IDictionary>]
 [-MethodName] <String> [-Namespace <String>] [-OperationTimeoutSec <UInt32>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### <span data-ttu-id="f2ebf-108">ClassNameSessionSet</span><span class="sxs-lookup"><span data-stu-id="f2ebf-108">ClassNameSessionSet</span></span>

```
Invoke-CimMethod [-ClassName] <String> -CimSession <CimSession[]> [[-Arguments] <IDictionary>]
 [-MethodName] <String> [-Namespace <String>] [-OperationTimeoutSec <UInt32>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### <span data-ttu-id="f2ebf-109">ResourceUriComputerSet</span><span class="sxs-lookup"><span data-stu-id="f2ebf-109">ResourceUriComputerSet</span></span>

```
Invoke-CimMethod -ResourceUri <Uri> [-ComputerName <String[]>] [[-Arguments] <IDictionary>]
 [-MethodName] <String> [-Namespace <String>] [-OperationTimeoutSec <UInt32>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### <span data-ttu-id="f2ebf-110">CimInstanceSessionSet</span><span class="sxs-lookup"><span data-stu-id="f2ebf-110">CimInstanceSessionSet</span></span>

```
Invoke-CimMethod [-ResourceUri <Uri>] [-InputObject] <CimInstance> -CimSession <CimSession[]>
 [[-Arguments] <IDictionary>] [-MethodName] <String> [-OperationTimeoutSec <UInt32>] [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="f2ebf-111">CimInstanceComputerSet</span><span class="sxs-lookup"><span data-stu-id="f2ebf-111">CimInstanceComputerSet</span></span>

```
Invoke-CimMethod [-ResourceUri <Uri>] [-InputObject] <CimInstance> [-ComputerName <String[]>]
 [[-Arguments] <IDictionary>] [-MethodName] <String> [-OperationTimeoutSec <UInt32>] [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="f2ebf-112">ResourceUriSessionSet</span><span class="sxs-lookup"><span data-stu-id="f2ebf-112">ResourceUriSessionSet</span></span>

```
Invoke-CimMethod -ResourceUri <Uri> -CimSession <CimSession[]> [[-Arguments] <IDictionary>]
 [-MethodName] <String> [-Namespace <String>] [-OperationTimeoutSec <UInt32>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### <span data-ttu-id="f2ebf-113">CimClassComputerSet</span><span class="sxs-lookup"><span data-stu-id="f2ebf-113">CimClassComputerSet</span></span>

```
Invoke-CimMethod [-CimClass] <CimClass> [-ComputerName <String[]>] [[-Arguments] <IDictionary>]
 [-MethodName] <String> [-OperationTimeoutSec <UInt32>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="f2ebf-114">CimClassSessionSet</span><span class="sxs-lookup"><span data-stu-id="f2ebf-114">CimClassSessionSet</span></span>

```
Invoke-CimMethod [-CimClass] <CimClass> -CimSession <CimSession[]> [[-Arguments] <IDictionary>]
 [-MethodName] <String> [-OperationTimeoutSec <UInt32>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="f2ebf-115">QueryComputerSet</span><span class="sxs-lookup"><span data-stu-id="f2ebf-115">QueryComputerSet</span></span>

```
Invoke-CimMethod -Query <String> [-QueryDialect <String>] [-ComputerName <String[]>]
 [[-Arguments] <IDictionary>] [-MethodName] <String> [-Namespace <String>]
 [-OperationTimeoutSec <UInt32>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="f2ebf-116">QuerySessionSet</span><span class="sxs-lookup"><span data-stu-id="f2ebf-116">QuerySessionSet</span></span>

```
Invoke-CimMethod -Query <String> [-QueryDialect <String>] -CimSession <CimSession[]>
 [[-Arguments] <IDictionary>] [-MethodName] <String> [-Namespace <String>]
 [-OperationTimeoutSec <UInt32>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="f2ebf-117">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="f2ebf-117">DESCRIPTION</span></span>

<span data-ttu-id="f2ebf-118">`Invoke-CimMethod`Cmdleten anropar en metod för en CIM-klass eller CIM-instans med hjälp av namn-värdeparet som anges av parametern **arguments** .</span><span class="sxs-lookup"><span data-stu-id="f2ebf-118">The `Invoke-CimMethod` cmdlet invokes a method of a CIM class or CIM instance using the name-value pairs specified by the **Arguments** parameter.</span></span>

<span data-ttu-id="f2ebf-119">Om parametern **InputObject** inte anges fungerar cmdleten på något av följande sätt:</span><span class="sxs-lookup"><span data-stu-id="f2ebf-119">If the **InputObject** parameter is not specified, the cmdlet works in one of the following ways:</span></span>

- <span data-ttu-id="f2ebf-120">Om varken parametern **computername** eller parametern **CimSession** anges, fungerar denna cmdlet på lokala Windows Management Instrumentation (WMI) med en Component Object Model (com)-session.</span><span class="sxs-lookup"><span data-stu-id="f2ebf-120">If neither the **ComputerName** parameter nor the **CimSession** parameter is specified, then this cmdlet works on local Windows Management Instrumentation (WMI) using a Component Object Model (COM) session.</span></span>
- <span data-ttu-id="f2ebf-121">Om antingen parametern **computername** eller parametern **CimSession** anges, fungerar denna cmdlet mot CIM-servern som anges av parametern **computername** eller parametern **CimSession** .</span><span class="sxs-lookup"><span data-stu-id="f2ebf-121">If either the **ComputerName** parameter or the **CimSession** parameter is specified, then this cmdlet works against the CIM server specified by either the **ComputerName** parameter or the **CimSession** parameter.</span></span>

<span data-ttu-id="f2ebf-122">Om parametern **InputObject** anges fungerar cmdleten på något av följande sätt:</span><span class="sxs-lookup"><span data-stu-id="f2ebf-122">If the **InputObject** parameter is specified, the cmdlet works in one of the following ways:</span></span>

- <span data-ttu-id="f2ebf-123">Om varken parametern **computername** eller parametern **CimSession** anges, använder denna cmdlet CIM-sessionen eller dator namnet från det indata-objektet.</span><span class="sxs-lookup"><span data-stu-id="f2ebf-123">If neither the **ComputerName** parameter nor the **CimSession** parameter is specified, then this cmdlet uses the CIM session or computer name from the input object.</span></span>
- <span data-ttu-id="f2ebf-124">Om antingen parametern **computername** eller parametern **CimSession** anges använder den här cmdleten antingen parametern **CimSession** eller värdet **computername** .</span><span class="sxs-lookup"><span data-stu-id="f2ebf-124">If the either the **ComputerName** parameter or the **CimSession** parameter is specified, then this cmdlet uses the either the **CimSession** parameter value or **ComputerName** parameter value.</span></span> <span data-ttu-id="f2ebf-125">Detta är inte ett vanligt scenario.</span><span class="sxs-lookup"><span data-stu-id="f2ebf-125">This is not a common scenario.</span></span>

## <span data-ttu-id="f2ebf-126">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="f2ebf-126">EXAMPLES</span></span>

### <span data-ttu-id="f2ebf-127">Exempel 1: anropa en metod</span><span class="sxs-lookup"><span data-stu-id="f2ebf-127">Example 1: Invoke a method</span></span>

<span data-ttu-id="f2ebf-128">I det här exemplet anropas metoden **Terminate** i **Win32_Process** -klassen.</span><span class="sxs-lookup"><span data-stu-id="f2ebf-128">This example invokes the **Terminate** method of the **Win32_Process** class.</span></span>

```powershell
Invoke-CimMethod -Query 'select * from Win32_Process where name like "notepad%"' -MethodName "Terminate"
```

### <span data-ttu-id="f2ebf-129">Exempel 2: anropa en metod med CIM-instansnamnet</span><span class="sxs-lookup"><span data-stu-id="f2ebf-129">Example 2: Invoke a method using CIM instance object</span></span>

<span data-ttu-id="f2ebf-130">I det här exemplet hämtas CIM instance-objektet och lagras det i en variabel med namnet `$x` med hjälp av `Get-CimInstance` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="f2ebf-130">This example retrieves the CIM instance object and stores it in a variable named `$x` using the `Get-CimInstance` cmdlet.</span></span> <span data-ttu-id="f2ebf-131">Innehållet i variabeln används sedan som **InputObject** för `Invoke-CimMethod` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="f2ebf-131">The contents of the variable are then used as the **InputObject** for the `Invoke-CimMethod` cmdlet.</span></span> <span data-ttu-id="f2ebf-132">**GetOwner** -metoden anropas för **CimInstance**.</span><span class="sxs-lookup"><span data-stu-id="f2ebf-132">The **GetOwner** method is invoked for the **CimInstance**.</span></span>

```powershell
$x = Get-CimInstance -Query 'Select * from Win32_Process where name like "notepad%"'
Invoke-CimMethod -InputObject $x -MethodName GetOwner
```

### <span data-ttu-id="f2ebf-133">Exempel 3: anropa en statisk metod med argument</span><span class="sxs-lookup"><span data-stu-id="f2ebf-133">Example 3: Invoke a static method using arguments</span></span>

<span data-ttu-id="f2ebf-134">I det här exemplet anropas metoden **create** med hjälp av parametern **argument** .</span><span class="sxs-lookup"><span data-stu-id="f2ebf-134">This example invokes the **Create** method named using the **Arguments** parameter.</span></span>

```powershell
Invoke-CimMethod -ClassName Win32_Process -MethodName "Create" -Arguments @{
  CommandLine = 'notepad.exe'; CurrentDirectory = "C:\windows\system32"
}
```

### <span data-ttu-id="f2ebf-135">Exempel 4: validering på klient Sidan</span><span class="sxs-lookup"><span data-stu-id="f2ebf-135">Example 4: Client-side validation</span></span>

<span data-ttu-id="f2ebf-136">Det här exemplet utför verifiering på klient sidan för **XYZ** -metoden genom att skicka ett **CimClass** -objekt till `Invoke-CimMethod` .</span><span class="sxs-lookup"><span data-stu-id="f2ebf-136">This example performs client-side validation for the **xyz** method by passing a **CimClass** object to `Invoke-CimMethod`.</span></span>

```powershell
$c = Get-CimClass -ClassName Win32_Process
Invoke-CimMethod -CimClass $c -MethodName "xyz" -Arguments @{ CommandLine = 'notepad.exe' }
```

## <span data-ttu-id="f2ebf-137">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="f2ebf-137">PARAMETERS</span></span>

### <span data-ttu-id="f2ebf-138">-Argument</span><span class="sxs-lookup"><span data-stu-id="f2ebf-138">-Arguments</span></span>

<span data-ttu-id="f2ebf-139">Anger de parametrar som ska skickas till den anropade metoden.</span><span class="sxs-lookup"><span data-stu-id="f2ebf-139">Specifies the parameters to pass to the called method.</span></span> <span data-ttu-id="f2ebf-140">Ange värdena för den här parametern som namn-värde-par, lagrade i en hash-tabell.</span><span class="sxs-lookup"><span data-stu-id="f2ebf-140">Specify the values for this parameter as name-value pairs, stored in a hash table.</span></span> <span data-ttu-id="f2ebf-141">Ordningen på de värden som angavs är inte viktig.</span><span class="sxs-lookup"><span data-stu-id="f2ebf-141">The order of the values entered isn't important.</span></span>

```yaml
Type: System.Collections.IDictionary
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="f2ebf-142">-CimClass</span><span class="sxs-lookup"><span data-stu-id="f2ebf-142">-CimClass</span></span>

<span data-ttu-id="f2ebf-143">Anger ett CIM-klassnamn som representerar en definition av CIM-klass på servern.</span><span class="sxs-lookup"><span data-stu-id="f2ebf-143">Specifies a CIM class object that represents a CIM class definition on the server.</span></span> <span data-ttu-id="f2ebf-144">Använd den här parametern när du anropar en statisk metod för en klass.</span><span class="sxs-lookup"><span data-stu-id="f2ebf-144">Use this parameter when invoking a static method of a class.</span></span>

<span data-ttu-id="f2ebf-145">Du kan använda `Get-CimClass` cmdleten för att hämta en klass definition från servern.</span><span class="sxs-lookup"><span data-stu-id="f2ebf-145">You can use the `Get-CimClass` cmdlet to retrieve a class definition from the server.</span></span>

<span data-ttu-id="f2ebf-146">Genom att använda den här parametern resulterar det bättre verifieringar på klient sidan.</span><span class="sxs-lookup"><span data-stu-id="f2ebf-146">Using this parameter results in better client side schema validations.</span></span>

```yaml
Type: Microsoft.Management.Infrastructure.CimClass
Parameter Sets: CimClassComputerSet, CimClassSessionSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="f2ebf-147">– CimSession</span><span class="sxs-lookup"><span data-stu-id="f2ebf-147">-CimSession</span></span>

<span data-ttu-id="f2ebf-148">Kör kommandot med den angivna CIM-sessionen.</span><span class="sxs-lookup"><span data-stu-id="f2ebf-148">Runs the command using the specified CIM session.</span></span> <span data-ttu-id="f2ebf-149">Ange en variabel som innehåller CIM-sessionen, eller ett kommando som skapar eller hämtar CIM-sessionen, t. ex `New-CimSession` . eller- `Get-CimSession` cmdletar.</span><span class="sxs-lookup"><span data-stu-id="f2ebf-149">Enter a variable that contains the CIM session, or a command that creates or gets the CIM session, such as the `New-CimSession` or `Get-CimSession` cmdlets.</span></span> <span data-ttu-id="f2ebf-150">Mer information finns i [about_CimSession](../Microsoft.PowerShell.Core/About/about_CimSession.md).</span><span class="sxs-lookup"><span data-stu-id="f2ebf-150">For more information, see [about_CimSession](../Microsoft.PowerShell.Core/About/about_CimSession.md).</span></span>

```yaml
Type: Microsoft.Management.Infrastructure.CimSession[]
Parameter Sets: ClassNameSessionSet, CimInstanceSessionSet, CimClassSessionSet, QuerySessionSet, ResourceUriSessionSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="f2ebf-151">-ClassName</span><span class="sxs-lookup"><span data-stu-id="f2ebf-151">-ClassName</span></span>

<span data-ttu-id="f2ebf-152">Anger namnet på CIM-klassen som åtgärden ska utföras för.</span><span class="sxs-lookup"><span data-stu-id="f2ebf-152">Specifies the name of the CIM class for which to perform the operation.</span></span> <span data-ttu-id="f2ebf-153">Den här parametern används bara för statiska metoder.</span><span class="sxs-lookup"><span data-stu-id="f2ebf-153">This parameter is only used for static methods.</span></span> <span data-ttu-id="f2ebf-154">Du kan använda TABB-slutförande för att bläddra i listan över klasser, eftersom PowerShell hämtar en lista över klasser från den lokala WMI-servern för att tillhandahålla en lista över klass namn.</span><span class="sxs-lookup"><span data-stu-id="f2ebf-154">You can use tab completion to browse the list of classes, because PowerShell gets a list of classes from the local WMI server to provide a list of class names.</span></span>

```yaml
Type: System.String
Parameter Sets: ClassNameComputerSet, ClassNameSessionSet
Aliases: Class

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="f2ebf-155">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="f2ebf-155">-ComputerName</span></span>

<span data-ttu-id="f2ebf-156">Anger namnet på den dator som du vill köra CIM-åtgärden på.</span><span class="sxs-lookup"><span data-stu-id="f2ebf-156">Specifies the name of the computer on which you want to run the CIM operation.</span></span> <span data-ttu-id="f2ebf-157">Du kan ange ett fullständigt kvalificerat domän namn (FQDN), ett NetBIOS-namn eller en IP-adress.</span><span class="sxs-lookup"><span data-stu-id="f2ebf-157">You can specify a fully qualified domain name (FQDN), a NetBIOS name, or an IP address.</span></span>

<span data-ttu-id="f2ebf-158">När du använder den här parametern skapar cmdleten en tillfällig session till den angivna datorn med hjälp av WsMan-protokollet.</span><span class="sxs-lookup"><span data-stu-id="f2ebf-158">When using this parameter, the cmdlet creates a temporary session to the specified computer using the WsMan protocol.</span></span> <span data-ttu-id="f2ebf-159">Annars utför cmdleten åtgärden på den lokala datorn med hjälp av Component Object Model (COM).</span><span class="sxs-lookup"><span data-stu-id="f2ebf-159">Otherwise, the cmdlet performs the operation on the local computer using Component Object Model (COM).</span></span>

<span data-ttu-id="f2ebf-160">Anslut med en CIM-session för bättre prestanda när flera åtgärder utförs på samma dator.</span><span class="sxs-lookup"><span data-stu-id="f2ebf-160">Connect using a CIM session for better performance when multiple operations are being performed on the same computer.</span></span>

```yaml
Type: System.String[]
Parameter Sets: ClassNameComputerSet, ResourceUriComputerSet, CimClassComputerSet, CimInstanceComputerSet, QueryComputerSet
Aliases: CN, ServerName

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="f2ebf-161">– InputObject</span><span class="sxs-lookup"><span data-stu-id="f2ebf-161">-InputObject</span></span>

<span data-ttu-id="f2ebf-162">Anger ett CIM-instansnamn som ska användas som indatamängd för att anropa en metod.</span><span class="sxs-lookup"><span data-stu-id="f2ebf-162">Specifies a CIM instance object to use as input to invoke a method.</span></span> <span data-ttu-id="f2ebf-163">Den här parametern kan endast användas för att anropa instans metoder.</span><span class="sxs-lookup"><span data-stu-id="f2ebf-163">This parameter can only be used to invoke instance methods.</span></span> <span data-ttu-id="f2ebf-164">Använd **klass** parametern eller parametern **CimClass** om du vill anropa statiska metoder för klasser.</span><span class="sxs-lookup"><span data-stu-id="f2ebf-164">To invoke class static methods, use the **Class** parameter or the **CimClass** parameter.</span></span>

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

### <span data-ttu-id="f2ebf-165">– MethodName</span><span class="sxs-lookup"><span data-stu-id="f2ebf-165">-MethodName</span></span>

<span data-ttu-id="f2ebf-166">Anger namnet på CIM-metoden som ska anropas.</span><span class="sxs-lookup"><span data-stu-id="f2ebf-166">Specifies the name of the CIM method to invoke.</span></span> <span data-ttu-id="f2ebf-167">Den här parametern är obligatorisk och får inte vara null eller tom.</span><span class="sxs-lookup"><span data-stu-id="f2ebf-167">This parameter is mandatory and cannot be null or empty.</span></span> <span data-ttu-id="f2ebf-168">Om du vill anropa en statisk metod för en CIM-klass använder du klassen **className** eller parametern **CimClass** .</span><span class="sxs-lookup"><span data-stu-id="f2ebf-168">To invoke static method of a CIM class use the **ClassName** or the **CimClass** parameter.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: Name

Required: True
Position: 2
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="f2ebf-169">– Namnrymd</span><span class="sxs-lookup"><span data-stu-id="f2ebf-169">-Namespace</span></span>

<span data-ttu-id="f2ebf-170">Anger namn området för CIM-åtgärden.</span><span class="sxs-lookup"><span data-stu-id="f2ebf-170">Specifies the namespace for the CIM operation.</span></span> <span data-ttu-id="f2ebf-171">Standard namn området är **rot-/cimv2**.</span><span class="sxs-lookup"><span data-stu-id="f2ebf-171">The default namespace is **root/cimv2**.</span></span> <span data-ttu-id="f2ebf-172">Du kan använda TABB-slutförande för att bläddra i listan över namn områden, eftersom PowerShell hämtar en lista över namn områden från den lokala WMI-servern för att tillhandahålla listan över namn områden.</span><span class="sxs-lookup"><span data-stu-id="f2ebf-172">You can use tab completion to browse the list of namespaces, because PowerShell gets a list of namespaces from the local WMI server to provide the list of namespaces.</span></span>

```yaml
Type: System.String
Parameter Sets: ClassNameComputerSet, ClassNameSessionSet, ResourceUriComputerSet, ResourceUriSessionSet, QueryComputerSet, QuerySessionSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="f2ebf-173">-OperationTimeoutSec</span><span class="sxs-lookup"><span data-stu-id="f2ebf-173">-OperationTimeoutSec</span></span>

<span data-ttu-id="f2ebf-174">Anger hur lång tid cmdleten väntar på ett svar från datorn.</span><span class="sxs-lookup"><span data-stu-id="f2ebf-174">Specifies the amount of time that the cmdlet waits for a response from the computer.</span></span> <span data-ttu-id="f2ebf-175">Som standard är värdet 0, vilket innebär att cmdleten använder standardvärdet för timeout för servern.</span><span class="sxs-lookup"><span data-stu-id="f2ebf-175">By default, the value is 0, which means that the cmdlet uses the default timeout value for the server.</span></span>

<span data-ttu-id="f2ebf-176">Om parametern **OperationTimeoutSec** anges till ett värde som är mindre än standard tids gränsen för anslutnings försök på 3 minuter, går det inte att återställa nätverks fel som sist mer än värdet för parametern **OperationTimeoutSec** .</span><span class="sxs-lookup"><span data-stu-id="f2ebf-176">If the **OperationTimeoutSec** parameter is set to a value less than the default connection retry timeout of 3 minutes, network failures that last more than the value of the **OperationTimeoutSec** parameter are not recoverable.</span></span>

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

### <span data-ttu-id="f2ebf-177">– Fråga</span><span class="sxs-lookup"><span data-stu-id="f2ebf-177">-Query</span></span>

<span data-ttu-id="f2ebf-178">Anger en fråga som ska köras på CIM-servern.</span><span class="sxs-lookup"><span data-stu-id="f2ebf-178">Specifies a query to run on the CIM server.</span></span> <span data-ttu-id="f2ebf-179">En metod anropas på instanserna som tas emot som ett resultat av frågan.</span><span class="sxs-lookup"><span data-stu-id="f2ebf-179">A method is invoked on the instances received as a result of the query.</span></span> <span data-ttu-id="f2ebf-180">Du kan ange dialekten med hjälp av parametern **QueryDialect** .</span><span class="sxs-lookup"><span data-stu-id="f2ebf-180">You can specify the query dialect using the **QueryDialect** parameter.</span></span>

<span data-ttu-id="f2ebf-181">Om det angivna värdet innehåller dubbla citat tecken ( `"` ), enkla citat tecken ( `'` ) eller ett omvänt snedstreck ( `\` ) måste du undanta dessa tecken genom att prefixet med omvänt snedstreck ( `\` ).</span><span class="sxs-lookup"><span data-stu-id="f2ebf-181">If the value specified contains double quotes (`"`), single quotes (`'`), or a backslash (`\`), you must escape those characters by prefixing them with the backslash (`\`) character.</span></span> <span data-ttu-id="f2ebf-182">Om värdet som anges använder WQL-operatorn som operator måste du undanta följande tecken genom att omsluta dem inom hak paren tes ( `[]` ): procent ( `%` ), under streck ( `_` ) eller inledande hak paren tes ( `[` ).</span><span class="sxs-lookup"><span data-stu-id="f2ebf-182">If the value specified uses the WQL LIKE operator, then you must escape the following characters by enclosing them in square brackets (`[]`): percent (`%`), underscore (`_`), or opening square bracket (`[`).</span></span>

```yaml
Type: System.String
Parameter Sets: QueryComputerSet, QuerySessionSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="f2ebf-183">-QueryDialect</span><span class="sxs-lookup"><span data-stu-id="f2ebf-183">-QueryDialect</span></span>

<span data-ttu-id="f2ebf-184">Anger frågespråket som används för Frågeparametern.</span><span class="sxs-lookup"><span data-stu-id="f2ebf-184">Specifies the query language used for the Query parameter.</span></span> <span data-ttu-id="f2ebf-185">De acceptabla värdena för den här parametern är: **WQL** eller **CQL**.</span><span class="sxs-lookup"><span data-stu-id="f2ebf-185">The acceptable values for this parameter are: **WQL** or **CQL**.</span></span>

<span data-ttu-id="f2ebf-186">Standardvärdet är **WQL**.</span><span class="sxs-lookup"><span data-stu-id="f2ebf-186">The default value is **WQL**.</span></span>

```yaml
Type: System.String
Parameter Sets: QueryComputerSet, QuerySessionSet
Aliases:

Required: False
Position: Named
Default value: WQL
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="f2ebf-187">– ResourceUri</span><span class="sxs-lookup"><span data-stu-id="f2ebf-187">-ResourceUri</span></span>

<span data-ttu-id="f2ebf-188">Anger resurs-URI (Uniform Resource Identifier) för resurs klassen eller-instansen.</span><span class="sxs-lookup"><span data-stu-id="f2ebf-188">Specifies the resource uniform resource identifier (URI) of the resource class or instance.</span></span>
<span data-ttu-id="f2ebf-189">URI: n används för att identifiera en speciell typ av resurs, till exempel diskar eller processer, på en dator.</span><span class="sxs-lookup"><span data-stu-id="f2ebf-189">The URI is used to identify a specific type of resource, such as disks or processes, on a computer.</span></span>

<span data-ttu-id="f2ebf-190">En URI består av ett prefix och en sökväg till en resurs.</span><span class="sxs-lookup"><span data-stu-id="f2ebf-190">A URI consists of a prefix and a path to a resource.</span></span> <span data-ttu-id="f2ebf-191">Ett exempel:</span><span class="sxs-lookup"><span data-stu-id="f2ebf-191">For example:</span></span>

`http://schemas.microsoft.com/wbem/wsman/1/wmi/root/cimv2/Win32_LogicalDisk`

`http://intel.com/wbem/wscim/1/amt-schema/1/AMT_GeneralSettings`

<span data-ttu-id="f2ebf-192">Om du inte anger den här parametern används DMTF-standardresurs-URI som standard `http://schemas.dmtf.org/wbem/wscim/1/cim-schema/2/` och klass namnet läggs till i den.</span><span class="sxs-lookup"><span data-stu-id="f2ebf-192">By default, if you do not specify this parameter, the DMTF standard resource URI `http://schemas.dmtf.org/wbem/wscim/1/cim-schema/2/` is used and the class name is appended to it.</span></span>

<span data-ttu-id="f2ebf-193">**ResourceURI** kan endast användas med CIM-sessioner som skapats med WSMan-protokollet, eller när du anger parametern **computername** , som skapar en CIM-session med hjälp av WSMan.</span><span class="sxs-lookup"><span data-stu-id="f2ebf-193">**ResourceURI** can only be used with CIM sessions created using the WSMan protocol, or when specifying the **ComputerName** parameter, which creates a CIM session using WSMan.</span></span>

<span data-ttu-id="f2ebf-194">När du anger den här parametern utan att ange parametern **computername** , eller när du anger en CIM-session som skapats med DCOM-protokollet, får du ett fel meddelande.</span><span class="sxs-lookup"><span data-stu-id="f2ebf-194">When you specify this parameter without specifying the **ComputerName** parameter, or when you specify a CIM session created using DCOM protocol, you get an error.</span></span> <span data-ttu-id="f2ebf-195">DCOM-protokollet har inte stöd för parametern **ResourceURI** .</span><span class="sxs-lookup"><span data-stu-id="f2ebf-195">The DCOM protocol does not support the **ResourceURI** parameter.</span></span>

<span data-ttu-id="f2ebf-196">Om både den **ResourceUri** -parametern och **filter** parametern anges, ignoreras **filter** parametern.</span><span class="sxs-lookup"><span data-stu-id="f2ebf-196">If both the **ResourceUri** parameter and the **Filter** parameter are specified, the **Filter** parameter is ignored.</span></span>

```yaml
Type: System.Uri
Parameter Sets: ResourceUriSessionSet, ResourceUriComputerSet
Aliases:

Required: True (ResourceUriSessionSet, ResourceUriComputerSet), False (CimInstanceSessionSet, CimInstanceComputerSet)
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="f2ebf-197">-Confirm</span><span class="sxs-lookup"><span data-stu-id="f2ebf-197">-Confirm</span></span>

<span data-ttu-id="f2ebf-198">Uppmanar dig att bekräfta innan du kör cmdleten.</span><span class="sxs-lookup"><span data-stu-id="f2ebf-198">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="f2ebf-199">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="f2ebf-199">-WhatIf</span></span>

<span data-ttu-id="f2ebf-200">Visar vad som skulle hända om cmdleten kördes.</span><span class="sxs-lookup"><span data-stu-id="f2ebf-200">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="f2ebf-201">Cmdleten körs inte.</span><span class="sxs-lookup"><span data-stu-id="f2ebf-201">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="f2ebf-202">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="f2ebf-202">CommonParameters</span></span>

<span data-ttu-id="f2ebf-203">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="f2ebf-203">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="f2ebf-204">Mer information finns i [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span><span class="sxs-lookup"><span data-stu-id="f2ebf-204">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="f2ebf-205">INDATA</span><span class="sxs-lookup"><span data-stu-id="f2ebf-205">INPUTS</span></span>

### <span data-ttu-id="f2ebf-206">Microsoft. Management. Infrastructure. CimClass</span><span class="sxs-lookup"><span data-stu-id="f2ebf-206">Microsoft.Management.Infrastructure.CimClass</span></span>

<span data-ttu-id="f2ebf-207">Denna cmdlet accepterar en CIM-klass som ett indatamängds objekt.</span><span class="sxs-lookup"><span data-stu-id="f2ebf-207">This cmdlet accepts a CIM class as an input object.</span></span>

### <span data-ttu-id="f2ebf-208">Microsoft. Management. Infrastructure. CimInstance</span><span class="sxs-lookup"><span data-stu-id="f2ebf-208">Microsoft.Management.Infrastructure.CimInstance</span></span>

<span data-ttu-id="f2ebf-209">Denna cmdlet accepterar en CIM-instans som ett indatamängds objekt.</span><span class="sxs-lookup"><span data-stu-id="f2ebf-209">This cmdlet accepts a CIM instance as an input object.</span></span>

## <span data-ttu-id="f2ebf-210">UTDATA</span><span class="sxs-lookup"><span data-stu-id="f2ebf-210">OUTPUTS</span></span>

### <span data-ttu-id="f2ebf-211">System. Management. Automation. PSCustomObject</span><span class="sxs-lookup"><span data-stu-id="f2ebf-211">System.Management.Automation.PSCustomObject</span></span>

<span data-ttu-id="f2ebf-212">Den här cmdleten returnerar ett objekt.</span><span class="sxs-lookup"><span data-stu-id="f2ebf-212">This cmdlet returns an object.</span></span>

## <span data-ttu-id="f2ebf-213">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="f2ebf-213">NOTES</span></span>

## <span data-ttu-id="f2ebf-214">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="f2ebf-214">RELATED LINKS</span></span>

[<span data-ttu-id="f2ebf-215">Get-CimClass</span><span class="sxs-lookup"><span data-stu-id="f2ebf-215">Get-CimClass</span></span>](get-cimclass.md)

[<span data-ttu-id="f2ebf-216">Get-CimInstance</span><span class="sxs-lookup"><span data-stu-id="f2ebf-216">Get-CimInstance</span></span>](get-ciminstance.md)

[<span data-ttu-id="f2ebf-217">Get-CimSession</span><span class="sxs-lookup"><span data-stu-id="f2ebf-217">Get-CimSession</span></span>](Get-CimSession.md)

[<span data-ttu-id="f2ebf-218">New-CimSession</span><span class="sxs-lookup"><span data-stu-id="f2ebf-218">New-CimSession</span></span>](New-CimSession.md)
