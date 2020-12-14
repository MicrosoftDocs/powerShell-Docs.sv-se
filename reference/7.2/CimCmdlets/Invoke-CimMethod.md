---
external help file: Microsoft.Management.Infrastructure.CimCmdlets.dll-Help.xml
Locale: en-US
Module Name: CimCmdlets
ms.date: 01/21/2020
online version: https://docs.microsoft.com/powershell/module/cimcmdlets/invoke-cimmethod?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Invoke-CimMethod
ms.openlocfilehash: 1217e07d09213d7c0e223129207c085b9ba2d48d
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94708566"
---
# <span data-ttu-id="87a3e-102">Invoke-CimMethod</span><span class="sxs-lookup"><span data-stu-id="87a3e-102">Invoke-CimMethod</span></span>

## <span data-ttu-id="87a3e-103">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="87a3e-103">SYNOPSIS</span></span>
<span data-ttu-id="87a3e-104">Anropar en metod i en CIM-klass.</span><span class="sxs-lookup"><span data-stu-id="87a3e-104">Invokes a method of a CIM class.</span></span>

## <span data-ttu-id="87a3e-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="87a3e-105">SYNTAX</span></span>

### <span data-ttu-id="87a3e-106">ClassNameComputerSet (standard)</span><span class="sxs-lookup"><span data-stu-id="87a3e-106">ClassNameComputerSet (Default)</span></span>

```
Invoke-CimMethod [-ClassName] <String> [-ComputerName <String[]>] [[-Arguments] <IDictionary>]
 [-MethodName] <String> [-Namespace <String>] [-OperationTimeoutSec <UInt32>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### <span data-ttu-id="87a3e-107">ClassNameSessionSet</span><span class="sxs-lookup"><span data-stu-id="87a3e-107">ClassNameSessionSet</span></span>

```
Invoke-CimMethod [-ClassName] <String> -CimSession <CimSession[]> [[-Arguments] <IDictionary>]
 [-MethodName] <String> [-Namespace <String>] [-OperationTimeoutSec <UInt32>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### <span data-ttu-id="87a3e-108">ResourceUriComputerSet</span><span class="sxs-lookup"><span data-stu-id="87a3e-108">ResourceUriComputerSet</span></span>

```
Invoke-CimMethod -ResourceUri <Uri> [-ComputerName <String[]>] [[-Arguments] <IDictionary>]
 [-MethodName] <String> [-Namespace <String>] [-OperationTimeoutSec <UInt32>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### <span data-ttu-id="87a3e-109">CimInstanceSessionSet</span><span class="sxs-lookup"><span data-stu-id="87a3e-109">CimInstanceSessionSet</span></span>

```
Invoke-CimMethod [-ResourceUri <Uri>] [-InputObject] <CimInstance> -CimSession <CimSession[]>
 [[-Arguments] <IDictionary>] [-MethodName] <String> [-OperationTimeoutSec <UInt32>] [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="87a3e-110">CimInstanceComputerSet</span><span class="sxs-lookup"><span data-stu-id="87a3e-110">CimInstanceComputerSet</span></span>

```
Invoke-CimMethod [-ResourceUri <Uri>] [-InputObject] <CimInstance> [-ComputerName <String[]>]
 [[-Arguments] <IDictionary>] [-MethodName] <String> [-OperationTimeoutSec <UInt32>] [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="87a3e-111">ResourceUriSessionSet</span><span class="sxs-lookup"><span data-stu-id="87a3e-111">ResourceUriSessionSet</span></span>

```
Invoke-CimMethod -ResourceUri <Uri> -CimSession <CimSession[]> [[-Arguments] <IDictionary>]
 [-MethodName] <String> [-Namespace <String>] [-OperationTimeoutSec <UInt32>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### <span data-ttu-id="87a3e-112">CimClassComputerSet</span><span class="sxs-lookup"><span data-stu-id="87a3e-112">CimClassComputerSet</span></span>

```
Invoke-CimMethod [-CimClass] <CimClass> [-ComputerName <String[]>] [[-Arguments] <IDictionary>]
 [-MethodName] <String> [-OperationTimeoutSec <UInt32>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="87a3e-113">CimClassSessionSet</span><span class="sxs-lookup"><span data-stu-id="87a3e-113">CimClassSessionSet</span></span>

```
Invoke-CimMethod [-CimClass] <CimClass> -CimSession <CimSession[]> [[-Arguments] <IDictionary>]
 [-MethodName] <String> [-OperationTimeoutSec <UInt32>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="87a3e-114">QueryComputerSet</span><span class="sxs-lookup"><span data-stu-id="87a3e-114">QueryComputerSet</span></span>

```
Invoke-CimMethod -Query <String> [-QueryDialect <String>] [-ComputerName <String[]>]
 [[-Arguments] <IDictionary>] [-MethodName] <String> [-Namespace <String>]
 [-OperationTimeoutSec <UInt32>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="87a3e-115">QuerySessionSet</span><span class="sxs-lookup"><span data-stu-id="87a3e-115">QuerySessionSet</span></span>

```
Invoke-CimMethod -Query <String> [-QueryDialect <String>] -CimSession <CimSession[]>
 [[-Arguments] <IDictionary>] [-MethodName] <String> [-Namespace <String>]
 [-OperationTimeoutSec <UInt32>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="87a3e-116">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="87a3e-116">DESCRIPTION</span></span>

<span data-ttu-id="87a3e-117">`Invoke-CimMethod`Cmdleten anropar en metod för en CIM-klass eller CIM-instans med hjälp av namn-värdeparet som anges av parametern **arguments** .</span><span class="sxs-lookup"><span data-stu-id="87a3e-117">The `Invoke-CimMethod` cmdlet invokes a method of a CIM class or CIM instance using the name-value pairs specified by the **Arguments** parameter.</span></span>

<span data-ttu-id="87a3e-118">Om parametern **InputObject** inte anges fungerar cmdleten på något av följande sätt:</span><span class="sxs-lookup"><span data-stu-id="87a3e-118">If the **InputObject** parameter is not specified, the cmdlet works in one of the following ways:</span></span>

- <span data-ttu-id="87a3e-119">Om varken parametern **computername** eller parametern **CimSession** anges, fungerar denna cmdlet på lokala Windows Management Instrumentation (WMI) med en Component Object Model (com)-session.</span><span class="sxs-lookup"><span data-stu-id="87a3e-119">If neither the **ComputerName** parameter nor the **CimSession** parameter is specified, then this cmdlet works on local Windows Management Instrumentation (WMI) using a Component Object Model (COM) session.</span></span>
- <span data-ttu-id="87a3e-120">Om antingen parametern **computername** eller parametern **CimSession** anges, fungerar denna cmdlet mot CIM-servern som anges av parametern **computername** eller parametern **CimSession** .</span><span class="sxs-lookup"><span data-stu-id="87a3e-120">If either the **ComputerName** parameter or the **CimSession** parameter is specified, then this cmdlet works against the CIM server specified by either the **ComputerName** parameter or the **CimSession** parameter.</span></span>

<span data-ttu-id="87a3e-121">Om parametern **InputObject** anges fungerar cmdleten på något av följande sätt:</span><span class="sxs-lookup"><span data-stu-id="87a3e-121">If the **InputObject** parameter is specified, the cmdlet works in one of the following ways:</span></span>

- <span data-ttu-id="87a3e-122">Om varken parametern **computername** eller parametern **CimSession** anges, använder denna cmdlet CIM-sessionen eller dator namnet från det indata-objektet.</span><span class="sxs-lookup"><span data-stu-id="87a3e-122">If neither the **ComputerName** parameter nor the **CimSession** parameter is specified, then this cmdlet uses the CIM session or computer name from the input object.</span></span>
- <span data-ttu-id="87a3e-123">Om antingen parametern **computername** eller parametern **CimSession** anges använder den här cmdleten antingen parametern **CimSession** eller värdet **computername** .</span><span class="sxs-lookup"><span data-stu-id="87a3e-123">If the either the **ComputerName** parameter or the **CimSession** parameter is specified, then this cmdlet uses the either the **CimSession** parameter value or **ComputerName** parameter value.</span></span> <span data-ttu-id="87a3e-124">Detta är inte ett vanligt scenario.</span><span class="sxs-lookup"><span data-stu-id="87a3e-124">This is not a common scenario.</span></span>

## <span data-ttu-id="87a3e-125">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="87a3e-125">EXAMPLES</span></span>

### <span data-ttu-id="87a3e-126">Exempel 1: anropa en metod</span><span class="sxs-lookup"><span data-stu-id="87a3e-126">Example 1: Invoke a method</span></span>

<span data-ttu-id="87a3e-127">I det här exemplet anropas metoden **Terminate** i **Win32_Process** -klassen.</span><span class="sxs-lookup"><span data-stu-id="87a3e-127">This example invokes the **Terminate** method of the **Win32_Process** class.</span></span>

```powershell
Invoke-CimMethod -Query 'select * from Win32_Process where name like "notepad%"' -MethodName "Terminate"
```

### <span data-ttu-id="87a3e-128">Exempel 2: anropa en metod med CIM-instansnamnet</span><span class="sxs-lookup"><span data-stu-id="87a3e-128">Example 2: Invoke a method using CIM instance object</span></span>

<span data-ttu-id="87a3e-129">I det här exemplet hämtas CIM instance-objektet och lagras det i en variabel med namnet `$x` med hjälp av `Get-CimInstance` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="87a3e-129">This example retrieves the CIM instance object and stores it in a variable named `$x` using the `Get-CimInstance` cmdlet.</span></span> <span data-ttu-id="87a3e-130">Innehållet i variabeln används sedan som **InputObject** för `Invoke-CimMethod` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="87a3e-130">The contents of the variable are then used as the **InputObject** for the `Invoke-CimMethod` cmdlet.</span></span> <span data-ttu-id="87a3e-131">**GetOwner** -metoden anropas för **CimInstance**.</span><span class="sxs-lookup"><span data-stu-id="87a3e-131">The **GetOwner** method is invoked for the **CimInstance**.</span></span>

```powershell
$x = Get-CimInstance -Query 'Select * from Win32_Process where name like "notepad%"'
Invoke-CimMethod -InputObject $x -MethodName GetOwner
```

### <span data-ttu-id="87a3e-132">Exempel 3: anropa en statisk metod med argument</span><span class="sxs-lookup"><span data-stu-id="87a3e-132">Example 3: Invoke a static method using arguments</span></span>

<span data-ttu-id="87a3e-133">I det här exemplet anropas metoden **create** med hjälp av parametern **argument** .</span><span class="sxs-lookup"><span data-stu-id="87a3e-133">This example invokes the **Create** method named using the **Arguments** parameter.</span></span>

```powershell
Invoke-CimMethod -ClassName Win32_Process -MethodName "Create" -Arguments @{
  CommandLine = 'notepad.exe'; CurrentDirectory = "C:\windows\system32"
}
```

### <span data-ttu-id="87a3e-134">Exempel 4: validering på klient Sidan</span><span class="sxs-lookup"><span data-stu-id="87a3e-134">Example 4: Client-side validation</span></span>

<span data-ttu-id="87a3e-135">Det här exemplet utför verifiering på klient sidan för **XYZ** -metoden genom att skicka ett **CimClass** -objekt till `Invoke-CimMethod` .</span><span class="sxs-lookup"><span data-stu-id="87a3e-135">This example performs client-side validation for the **xyz** method by passing a **CimClass** object to `Invoke-CimMethod`.</span></span>

```powershell
$c = Get-CimClass -ClassName Win32_Process
Invoke-CimMethod -CimClass $c -MethodName "xyz" -Arguments @{ CommandLine = 'notepad.exe' }
```

## <span data-ttu-id="87a3e-136">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="87a3e-136">PARAMETERS</span></span>

### <span data-ttu-id="87a3e-137">-Argument</span><span class="sxs-lookup"><span data-stu-id="87a3e-137">-Arguments</span></span>

<span data-ttu-id="87a3e-138">Anger de parametrar som ska skickas till den anropade metoden.</span><span class="sxs-lookup"><span data-stu-id="87a3e-138">Specifies the parameters to pass to the called method.</span></span> <span data-ttu-id="87a3e-139">Ange värdena för den här parametern som namn-värde-par, lagrade i en hash-tabell.</span><span class="sxs-lookup"><span data-stu-id="87a3e-139">Specify the values for this parameter as name-value pairs, stored in a hash table.</span></span> <span data-ttu-id="87a3e-140">Ordningen på de värden som angavs är inte viktig.</span><span class="sxs-lookup"><span data-stu-id="87a3e-140">The order of the values entered isn't important.</span></span>

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

### <span data-ttu-id="87a3e-141">-CimClass</span><span class="sxs-lookup"><span data-stu-id="87a3e-141">-CimClass</span></span>

<span data-ttu-id="87a3e-142">Anger ett CIM-klassnamn som representerar en definition av CIM-klass på servern.</span><span class="sxs-lookup"><span data-stu-id="87a3e-142">Specifies a CIM class object that represents a CIM class definition on the server.</span></span> <span data-ttu-id="87a3e-143">Använd den här parametern när du anropar en statisk metod för en klass.</span><span class="sxs-lookup"><span data-stu-id="87a3e-143">Use this parameter when invoking a static method of a class.</span></span>

<span data-ttu-id="87a3e-144">Du kan använda `Get-CimClass` cmdleten för att hämta en klass definition från servern.</span><span class="sxs-lookup"><span data-stu-id="87a3e-144">You can use the `Get-CimClass` cmdlet to retrieve a class definition from the server.</span></span>

<span data-ttu-id="87a3e-145">Genom att använda den här parametern resulterar det bättre verifieringar på klient sidan.</span><span class="sxs-lookup"><span data-stu-id="87a3e-145">Using this parameter results in better client side schema validations.</span></span>

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

### <span data-ttu-id="87a3e-146">– CimSession</span><span class="sxs-lookup"><span data-stu-id="87a3e-146">-CimSession</span></span>

<span data-ttu-id="87a3e-147">Kör kommandot med den angivna CIM-sessionen.</span><span class="sxs-lookup"><span data-stu-id="87a3e-147">Runs the command using the specified CIM session.</span></span> <span data-ttu-id="87a3e-148">Ange en variabel som innehåller CIM-sessionen, eller ett kommando som skapar eller hämtar CIM-sessionen, t. ex `New-CimSession` . eller- `Get-CimSession` cmdletar.</span><span class="sxs-lookup"><span data-stu-id="87a3e-148">Enter a variable that contains the CIM session, or a command that creates or gets the CIM session, such as the `New-CimSession` or `Get-CimSession` cmdlets.</span></span> <span data-ttu-id="87a3e-149">Mer information finns i [about_CimSession](../Microsoft.PowerShell.Core/About/about_CimSession.md).</span><span class="sxs-lookup"><span data-stu-id="87a3e-149">For more information, see [about_CimSession](../Microsoft.PowerShell.Core/About/about_CimSession.md).</span></span>

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

### <span data-ttu-id="87a3e-150">-ClassName</span><span class="sxs-lookup"><span data-stu-id="87a3e-150">-ClassName</span></span>

<span data-ttu-id="87a3e-151">Anger namnet på CIM-klassen som åtgärden ska utföras för.</span><span class="sxs-lookup"><span data-stu-id="87a3e-151">Specifies the name of the CIM class for which to perform the operation.</span></span> <span data-ttu-id="87a3e-152">Den här parametern används bara för statiska metoder.</span><span class="sxs-lookup"><span data-stu-id="87a3e-152">This parameter is only used for static methods.</span></span> <span data-ttu-id="87a3e-153">Du kan använda TABB-slutförande för att bläddra i listan över klasser, eftersom PowerShell hämtar en lista över klasser från den lokala WMI-servern för att tillhandahålla en lista över klass namn.</span><span class="sxs-lookup"><span data-stu-id="87a3e-153">You can use tab completion to browse the list of classes, because PowerShell gets a list of classes from the local WMI server to provide a list of class names.</span></span>

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

### <span data-ttu-id="87a3e-154">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="87a3e-154">-ComputerName</span></span>

<span data-ttu-id="87a3e-155">Anger namnet på den dator som du vill köra CIM-åtgärden på.</span><span class="sxs-lookup"><span data-stu-id="87a3e-155">Specifies the name of the computer on which you want to run the CIM operation.</span></span> <span data-ttu-id="87a3e-156">Du kan ange ett fullständigt kvalificerat domän namn (FQDN), ett NetBIOS-namn eller en IP-adress.</span><span class="sxs-lookup"><span data-stu-id="87a3e-156">You can specify a fully qualified domain name (FQDN), a NetBIOS name, or an IP address.</span></span>

<span data-ttu-id="87a3e-157">När du använder den här parametern skapar cmdleten en tillfällig session till den angivna datorn med hjälp av WsMan-protokollet.</span><span class="sxs-lookup"><span data-stu-id="87a3e-157">When using this parameter, the cmdlet creates a temporary session to the specified computer using the WsMan protocol.</span></span> <span data-ttu-id="87a3e-158">Annars utför cmdleten åtgärden på den lokala datorn med hjälp av Component Object Model (COM).</span><span class="sxs-lookup"><span data-stu-id="87a3e-158">Otherwise, the cmdlet performs the operation on the local computer using Component Object Model (COM).</span></span>

<span data-ttu-id="87a3e-159">Anslut med en CIM-session för bättre prestanda när flera åtgärder utförs på samma dator.</span><span class="sxs-lookup"><span data-stu-id="87a3e-159">Connect using a CIM session for better performance when multiple operations are being performed on the same computer.</span></span>

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

### <span data-ttu-id="87a3e-160">– InputObject</span><span class="sxs-lookup"><span data-stu-id="87a3e-160">-InputObject</span></span>

<span data-ttu-id="87a3e-161">Anger ett CIM-instansnamn som ska användas som indatamängd för att anropa en metod.</span><span class="sxs-lookup"><span data-stu-id="87a3e-161">Specifies a CIM instance object to use as input to invoke a method.</span></span> <span data-ttu-id="87a3e-162">Den här parametern kan endast användas för att anropa instans metoder.</span><span class="sxs-lookup"><span data-stu-id="87a3e-162">This parameter can only be used to invoke instance methods.</span></span> <span data-ttu-id="87a3e-163">Använd **klass** parametern eller parametern **CimClass** om du vill anropa statiska metoder för klasser.</span><span class="sxs-lookup"><span data-stu-id="87a3e-163">To invoke class static methods, use the **Class** parameter or the **CimClass** parameter.</span></span>

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

### <span data-ttu-id="87a3e-164">– MethodName</span><span class="sxs-lookup"><span data-stu-id="87a3e-164">-MethodName</span></span>

<span data-ttu-id="87a3e-165">Anger namnet på CIM-metoden som ska anropas.</span><span class="sxs-lookup"><span data-stu-id="87a3e-165">Specifies the name of the CIM method to invoke.</span></span> <span data-ttu-id="87a3e-166">Den här parametern är obligatorisk och får inte vara null eller tom.</span><span class="sxs-lookup"><span data-stu-id="87a3e-166">This parameter is mandatory and cannot be null or empty.</span></span> <span data-ttu-id="87a3e-167">Om du vill anropa en statisk metod för en CIM-klass använder du klassen **className** eller parametern **CimClass** .</span><span class="sxs-lookup"><span data-stu-id="87a3e-167">To invoke static method of a CIM class use the **ClassName** or the **CimClass** parameter.</span></span>

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

### <span data-ttu-id="87a3e-168">– Namnrymd</span><span class="sxs-lookup"><span data-stu-id="87a3e-168">-Namespace</span></span>

<span data-ttu-id="87a3e-169">Anger namn området för CIM-åtgärden.</span><span class="sxs-lookup"><span data-stu-id="87a3e-169">Specifies the namespace for the CIM operation.</span></span> <span data-ttu-id="87a3e-170">Standard namn området är **rot-/cimv2**.</span><span class="sxs-lookup"><span data-stu-id="87a3e-170">The default namespace is **root/cimv2**.</span></span> <span data-ttu-id="87a3e-171">Du kan använda TABB-slutförande för att bläddra i listan över namn områden, eftersom PowerShell hämtar en lista över namn områden från den lokala WMI-servern för att tillhandahålla listan över namn områden.</span><span class="sxs-lookup"><span data-stu-id="87a3e-171">You can use tab completion to browse the list of namespaces, because PowerShell gets a list of namespaces from the local WMI server to provide the list of namespaces.</span></span>

```yaml
Type: System.String
Parameter Sets: ClassNameComputerSet, ClassNameSessionSet, ResourceUriComputerSet, ResourceUriSessionSet, QuerySessionSet, QueryComputerSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="87a3e-172">-OperationTimeoutSec</span><span class="sxs-lookup"><span data-stu-id="87a3e-172">-OperationTimeoutSec</span></span>

<span data-ttu-id="87a3e-173">Anger hur lång tid cmdleten väntar på ett svar från datorn.</span><span class="sxs-lookup"><span data-stu-id="87a3e-173">Specifies the amount of time that the cmdlet waits for a response from the computer.</span></span> <span data-ttu-id="87a3e-174">Som standard är värdet 0, vilket innebär att cmdleten använder standardvärdet för timeout för servern.</span><span class="sxs-lookup"><span data-stu-id="87a3e-174">By default, the value is 0, which means that the cmdlet uses the default timeout value for the server.</span></span>

<span data-ttu-id="87a3e-175">Om parametern **OperationTimeoutSec** anges till ett värde som är mindre än standard tids gränsen för anslutnings försök på 3 minuter, går det inte att återställa nätverks fel som sist mer än värdet för parametern **OperationTimeoutSec** .</span><span class="sxs-lookup"><span data-stu-id="87a3e-175">If the **OperationTimeoutSec** parameter is set to a value less than the default connection retry timeout of 3 minutes, network failures that last more than the value of the **OperationTimeoutSec** parameter are not recoverable.</span></span>

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

### <span data-ttu-id="87a3e-176">– Fråga</span><span class="sxs-lookup"><span data-stu-id="87a3e-176">-Query</span></span>

<span data-ttu-id="87a3e-177">Anger en fråga som ska köras på CIM-servern.</span><span class="sxs-lookup"><span data-stu-id="87a3e-177">Specifies a query to run on the CIM server.</span></span> <span data-ttu-id="87a3e-178">En metod anropas på instanserna som tas emot som ett resultat av frågan.</span><span class="sxs-lookup"><span data-stu-id="87a3e-178">A method is invoked on the instances received as a result of the query.</span></span> <span data-ttu-id="87a3e-179">Du kan ange dialekten med hjälp av parametern **QueryDialect** .</span><span class="sxs-lookup"><span data-stu-id="87a3e-179">You can specify the query dialect using the **QueryDialect** parameter.</span></span>

<span data-ttu-id="87a3e-180">Om det angivna värdet innehåller dubbla citat tecken ( `"` ), enkla citat tecken ( `'` ) eller ett omvänt snedstreck ( `\` ) måste du undanta dessa tecken genom att prefixet med omvänt snedstreck ( `\` ).</span><span class="sxs-lookup"><span data-stu-id="87a3e-180">If the value specified contains double quotes (`"`), single quotes (`'`), or a backslash (`\`), you must escape those characters by prefixing them with the backslash (`\`) character.</span></span> <span data-ttu-id="87a3e-181">Om värdet som anges använder WQL-operatorn som operator måste du undanta följande tecken genom att omsluta dem inom hak paren tes ( `[]` ): procent ( `%` ), under streck ( `_` ) eller inledande hak paren tes ( `[` ).</span><span class="sxs-lookup"><span data-stu-id="87a3e-181">If the value specified uses the WQL LIKE operator, then you must escape the following characters by enclosing them in square brackets (`[]`): percent (`%`), underscore (`_`), or opening square bracket (`[`).</span></span>

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

### <span data-ttu-id="87a3e-182">-QueryDialect</span><span class="sxs-lookup"><span data-stu-id="87a3e-182">-QueryDialect</span></span>

<span data-ttu-id="87a3e-183">Anger frågespråket som används för Frågeparametern.</span><span class="sxs-lookup"><span data-stu-id="87a3e-183">Specifies the query language used for the Query parameter.</span></span> <span data-ttu-id="87a3e-184">De acceptabla värdena för den här parametern är: **WQL** eller **CQL**.</span><span class="sxs-lookup"><span data-stu-id="87a3e-184">The acceptable values for this parameter are: **WQL** or **CQL**.</span></span>

<span data-ttu-id="87a3e-185">Standardvärdet är **WQL**.</span><span class="sxs-lookup"><span data-stu-id="87a3e-185">The default value is **WQL**.</span></span>

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

### <span data-ttu-id="87a3e-186">– ResourceUri</span><span class="sxs-lookup"><span data-stu-id="87a3e-186">-ResourceUri</span></span>

<span data-ttu-id="87a3e-187">Anger resurs-URI (Uniform Resource Identifier) för resurs klassen eller-instansen.</span><span class="sxs-lookup"><span data-stu-id="87a3e-187">Specifies the resource uniform resource identifier (URI) of the resource class or instance.</span></span>
<span data-ttu-id="87a3e-188">URI: n används för att identifiera en speciell typ av resurs, till exempel diskar eller processer, på en dator.</span><span class="sxs-lookup"><span data-stu-id="87a3e-188">The URI is used to identify a specific type of resource, such as disks or processes, on a computer.</span></span>

<span data-ttu-id="87a3e-189">En URI består av ett prefix och en sökväg till en resurs.</span><span class="sxs-lookup"><span data-stu-id="87a3e-189">A URI consists of a prefix and a path to a resource.</span></span> <span data-ttu-id="87a3e-190">Exempel:</span><span class="sxs-lookup"><span data-stu-id="87a3e-190">For example:</span></span>

`http://schemas.microsoft.com/wbem/wsman/1/wmi/root/cimv2/Win32_LogicalDisk`

`http://intel.com/wbem/wscim/1/amt-schema/1/AMT_GeneralSettings`

<span data-ttu-id="87a3e-191">Om du inte anger den här parametern används DMTF-standardresurs-URI som standard `http://schemas.dmtf.org/wbem/wscim/1/cim-schema/2/` och klass namnet läggs till i den.</span><span class="sxs-lookup"><span data-stu-id="87a3e-191">By default, if you do not specify this parameter, the DMTF standard resource URI `http://schemas.dmtf.org/wbem/wscim/1/cim-schema/2/` is used and the class name is appended to it.</span></span>

<span data-ttu-id="87a3e-192">**ResourceURI** kan endast användas med CIM-sessioner som skapats med WSMan-protokollet, eller när du anger parametern **computername** , som skapar en CIM-session med hjälp av WSMan.</span><span class="sxs-lookup"><span data-stu-id="87a3e-192">**ResourceURI** can only be used with CIM sessions created using the WSMan protocol, or when specifying the **ComputerName** parameter, which creates a CIM session using WSMan.</span></span>

<span data-ttu-id="87a3e-193">När du anger den här parametern utan att ange parametern **computername** , eller när du anger en CIM-session som skapats med DCOM-protokollet, får du ett fel meddelande.</span><span class="sxs-lookup"><span data-stu-id="87a3e-193">When you specify this parameter without specifying the **ComputerName** parameter, or when you specify a CIM session created using DCOM protocol, you get an error.</span></span> <span data-ttu-id="87a3e-194">DCOM-protokollet har inte stöd för parametern **ResourceURI** .</span><span class="sxs-lookup"><span data-stu-id="87a3e-194">The DCOM protocol does not support the **ResourceURI** parameter.</span></span>

<span data-ttu-id="87a3e-195">Om både den **ResourceUri** -parametern och **filter** parametern anges, ignoreras **filter** parametern.</span><span class="sxs-lookup"><span data-stu-id="87a3e-195">If both the **ResourceUri** parameter and the **Filter** parameter are specified, the **Filter** parameter is ignored.</span></span>

```yaml
Type: System.Uri
Parameter Sets: CimInstanceComputerSet, CimInstanceSessionSet
Aliases:

Required: True (ResourceUriSessionSet, ResourceUriComputerSet), False (CimInstanceSessionSet, CimInstanceComputerSet)
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="87a3e-196">-Confirm</span><span class="sxs-lookup"><span data-stu-id="87a3e-196">-Confirm</span></span>

<span data-ttu-id="87a3e-197">Uppmanar dig att bekräfta innan du kör cmdleten.</span><span class="sxs-lookup"><span data-stu-id="87a3e-197">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="87a3e-198">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="87a3e-198">-WhatIf</span></span>

<span data-ttu-id="87a3e-199">Visar vad som skulle hända om cmdleten kördes.</span><span class="sxs-lookup"><span data-stu-id="87a3e-199">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="87a3e-200">Cmdleten körs inte.</span><span class="sxs-lookup"><span data-stu-id="87a3e-200">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="87a3e-201">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="87a3e-201">CommonParameters</span></span>

<span data-ttu-id="87a3e-202">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="87a3e-202">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="87a3e-203">Mer information finns i [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span><span class="sxs-lookup"><span data-stu-id="87a3e-203">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="87a3e-204">INDATA</span><span class="sxs-lookup"><span data-stu-id="87a3e-204">INPUTS</span></span>

### <span data-ttu-id="87a3e-205">CIM-klass</span><span class="sxs-lookup"><span data-stu-id="87a3e-205">CIM class</span></span>

<span data-ttu-id="87a3e-206">Denna cmdlet accepterar en CIM-klass som ett indatamängds objekt.</span><span class="sxs-lookup"><span data-stu-id="87a3e-206">This cmdlet accepts a CIM class as an input object.</span></span>

### <span data-ttu-id="87a3e-207">CIM-instans</span><span class="sxs-lookup"><span data-stu-id="87a3e-207">CIM instance</span></span>

<span data-ttu-id="87a3e-208">Denna cmdlet accepterar en CIM-instans som ett indatamängds objekt.</span><span class="sxs-lookup"><span data-stu-id="87a3e-208">This cmdlet accepts a CIM instance as an input object.</span></span>

## <span data-ttu-id="87a3e-209">UTDATA</span><span class="sxs-lookup"><span data-stu-id="87a3e-209">OUTPUTS</span></span>

### <span data-ttu-id="87a3e-210">System. Management. Automation. PSCustomObject</span><span class="sxs-lookup"><span data-stu-id="87a3e-210">System.Management.Automation.PSCustomObject</span></span>

<span data-ttu-id="87a3e-211">Den här cmdleten returnerar ett objekt.</span><span class="sxs-lookup"><span data-stu-id="87a3e-211">This cmdlet returns an object.</span></span>

## <span data-ttu-id="87a3e-212">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="87a3e-212">NOTES</span></span>

## <span data-ttu-id="87a3e-213">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="87a3e-213">RELATED LINKS</span></span>

[<span data-ttu-id="87a3e-214">Get-CimClass</span><span class="sxs-lookup"><span data-stu-id="87a3e-214">Get-CimClass</span></span>](get-cimclass.md)

[<span data-ttu-id="87a3e-215">Get-CimInstance</span><span class="sxs-lookup"><span data-stu-id="87a3e-215">Get-CimInstance</span></span>](get-ciminstance.md)

[<span data-ttu-id="87a3e-216">Get-CimSession</span><span class="sxs-lookup"><span data-stu-id="87a3e-216">Get-CimSession</span></span>](Get-CimSession.md)

[<span data-ttu-id="87a3e-217">New-CimSession</span><span class="sxs-lookup"><span data-stu-id="87a3e-217">New-CimSession</span></span>](New-CimSession.md)

