---
description: Beskriver WMI Query Language (WQL) som kan användas för att hämta WMI-objekt i Windows PowerShell.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 01/03/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_wql?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_WQL
ms.openlocfilehash: c6fd523864d419fb400b7041e92ec8f0733724b7
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/13/2020
ms.locfileid: "93271916"
---
# <a name="about-wql"></a><span data-ttu-id="25a41-104">Om WQL</span><span class="sxs-lookup"><span data-stu-id="25a41-104">About WQL</span></span>

## <a name="short-description"></a><span data-ttu-id="25a41-105">KORT BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="25a41-105">SHORT DESCRIPTION</span></span>

<span data-ttu-id="25a41-106">Beskriver WMI Query Language (WQL) som kan användas för att hämta WMI-objekt i Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="25a41-106">Describes WMI Query Language (WQL), which can be used to get WMI objects in Windows PowerShell.</span></span>

## <a name="long-description"></a><span data-ttu-id="25a41-107">LÅNG BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="25a41-107">LONG DESCRIPTION</span></span>

<span data-ttu-id="25a41-108">WQL är frågespråket för Windows Management Instrumentation (WMI), vilket är det språk som används för att hämta information från WMI.</span><span class="sxs-lookup"><span data-stu-id="25a41-108">WQL is the Windows Management Instrumentation (WMI) query language, which is the language used to get information from WMI.</span></span>

<span data-ttu-id="25a41-109">Du behöver inte använda WQL för att utföra en WMI-fråga i Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="25a41-109">You are not required to use WQL to perform a WMI query in Windows PowerShell.</span></span>
<span data-ttu-id="25a41-110">I stället kan du använda parametrarna i Get-WmiObject-eller Get-CimInstance-cmdletar.</span><span class="sxs-lookup"><span data-stu-id="25a41-110">Instead, you can use the parameters of the Get-WmiObject or Get-CimInstance cmdlets.</span></span> <span data-ttu-id="25a41-111">WQL-frågor är något snabbare än vanliga Get-WmiObject kommandon och den förbättrade prestandan är tydlig när kommandona körs på hundratals system.</span><span class="sxs-lookup"><span data-stu-id="25a41-111">WQL queries are somewhat faster than standard Get-WmiObject commands and the improved performance is evident when the commands run on hundreds of systems.</span></span> <span data-ttu-id="25a41-112">Men se till att den tid du ägnat att skriva en lyckad WQL-fråga inte uppväger prestanda förbättringen.</span><span class="sxs-lookup"><span data-stu-id="25a41-112">However, be sure that the time you spend to write a successful WQL query doesn't outweigh the performance improvement.</span></span>

<span data-ttu-id="25a41-113">De grundläggande WQL-uttrycken som du behöver för att använda WQL är Select, WHERE och from.</span><span class="sxs-lookup"><span data-stu-id="25a41-113">The basic WQL statements you need to use WQL are Select, Where, and From.</span></span>

## <a name="when-to-use-wql"></a><span data-ttu-id="25a41-114">NÄR DU SKA ANVÄNDA WQL</span><span class="sxs-lookup"><span data-stu-id="25a41-114">WHEN TO USE WQL</span></span>

<span data-ttu-id="25a41-115">När du arbetar med WMI och särskilt med WQL, ska du inte glömma att du även använder Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="25a41-115">When working with WMI, and especially with WQL, do not forget that you are also using Windows PowerShell.</span></span> <span data-ttu-id="25a41-116">Ofta, om en WQL-fråga inte fungerar som förväntat, är det enklare att använda ett Windows PowerShell-kommando än att felsöka WQL-frågan.</span><span class="sxs-lookup"><span data-stu-id="25a41-116">Often, if a WQL query does not work as expected, it's easier to use a standard Windows PowerShell command than to debug the WQL query.</span></span>

<span data-ttu-id="25a41-117">Om du inte returnerar enorma data mängder från över bandbredds begränsade fjärrsystem är det sällan produktivt att ägna timmar åt att försöka med en komplicerad och komplexa WQL-fråga när det finns en perfekt acceptabel Windows-cmdlet som gör samma sak, om det blir långsammare.</span><span class="sxs-lookup"><span data-stu-id="25a41-117">Unless you are returning massive amounts of data from across bandwidth-constrained remote systems, it is rarely productive to spend hours trying to perfect a complicated and convoluted WQL query when there is a perfectly acceptable Windows cmdlet that does the same thing, if a bit more slowly.</span></span>

## <a name="using-the-select-statement"></a><span data-ttu-id="25a41-118">ANVÄNDA SELECT-INSTRUKTIONEN</span><span class="sxs-lookup"><span data-stu-id="25a41-118">USING THE SELECT STATEMENT</span></span>

<span data-ttu-id="25a41-119">En typisk WMI-fråga börjar med en SELECT-instruktion som hämtar alla egenskaper eller vissa egenskaper för en WMI-klass.</span><span class="sxs-lookup"><span data-stu-id="25a41-119">A typical WMI query begins with a Select statement that gets all properties or particular properties of a WMI class.</span></span> <span data-ttu-id="25a41-120">Om du vill välja alla egenskaper för en WMI-klass använder du en asterisk ( \* ).</span><span class="sxs-lookup"><span data-stu-id="25a41-120">To select all properties of a WMI class, use an asterisk (\*).</span></span> <span data-ttu-id="25a41-121">From-nyckelordet anger WMI-klassen.</span><span class="sxs-lookup"><span data-stu-id="25a41-121">The From keyword specifies the WMI class.</span></span>

<span data-ttu-id="25a41-122">En SELECT-instruktion har följande format:</span><span class="sxs-lookup"><span data-stu-id="25a41-122">A Select statement has the following format:</span></span>

```
Select <property> from <WMI-class>
```

<span data-ttu-id="25a41-123">Följande SELECT-instruktion väljer till exempel alla egenskaper (\*) från instanserna av Win32_Bios WMI-klassen.</span><span class="sxs-lookup"><span data-stu-id="25a41-123">For example, the following Select statement selects all properties (\*) from the instances of the Win32_Bios WMI class.</span></span>

```
Select * from Win32_Bios
```

<span data-ttu-id="25a41-124">Om du vill välja en viss egenskap för en WMI-klass, placerar du egenskaps namnet mellan nyckelorden Select och from.</span><span class="sxs-lookup"><span data-stu-id="25a41-124">To select a particular property of a WMI class, place the property name between the Select and From keywords.</span></span>

<span data-ttu-id="25a41-125">Följande fråga väljer bara namnet på BIOS från Win32_Bios WMI-klassen.</span><span class="sxs-lookup"><span data-stu-id="25a41-125">The following query selects only the name of the BIOS from the Win32_Bios WMI class.</span></span> <span data-ttu-id="25a41-126">Kommandot sparar frågan i variabeln $queryName.</span><span class="sxs-lookup"><span data-stu-id="25a41-126">The command saves the query in the $queryName variable.</span></span>

```
Select Name from Win32_Bios
```

<span data-ttu-id="25a41-127">Om du vill markera fler än en egenskap använder du kommatecken för att avgränsa egenskaps namnen.</span><span class="sxs-lookup"><span data-stu-id="25a41-127">To select more than one property, use commas to separate the property names.</span></span>
<span data-ttu-id="25a41-128">Följande WMI-fråga väljer namn och version för Win32_Bios WMI-klassen.</span><span class="sxs-lookup"><span data-stu-id="25a41-128">The following WMI query selects the name and the version of the Win32_Bios WMI class.</span></span> <span data-ttu-id="25a41-129">Kommandot sparar frågan i variabeln $queryNameVersion.</span><span class="sxs-lookup"><span data-stu-id="25a41-129">The command saves the query in the $queryNameVersion variable.</span></span>

```
Select name, version from Win32_Bios
```

## <a name="using-the-wql-query"></a><span data-ttu-id="25a41-130">ANVÄNDA WQL-FRÅGAN</span><span class="sxs-lookup"><span data-stu-id="25a41-130">USING THE WQL QUERY</span></span>

<span data-ttu-id="25a41-131">Det finns tre sätt att använda WQL-frågor i Windows PowerShell-kommandot.</span><span class="sxs-lookup"><span data-stu-id="25a41-131">There are three ways to use WQL query in Windows PowerShell command.</span></span>

- <span data-ttu-id="25a41-132">Använd Get-WmiObject-cmdleten</span><span class="sxs-lookup"><span data-stu-id="25a41-132">Use the Get-WmiObject cmdlet</span></span>
- <span data-ttu-id="25a41-133">Använd Get-CimInstance-cmdleten</span><span class="sxs-lookup"><span data-stu-id="25a41-133">Use the Get-CimInstance cmdlet</span></span>
- <span data-ttu-id="25a41-134">Använd [wmisearcher]-typ Accelerator.</span><span class="sxs-lookup"><span data-stu-id="25a41-134">Use the [wmisearcher] type accelerator.</span></span>

## <a name="using-the-get-wmiobject-cmdlet"></a><span data-ttu-id="25a41-135">ANVÄNDA CMDLETEN GET-WMIOBJECT</span><span class="sxs-lookup"><span data-stu-id="25a41-135">USING THE GET-WMIOBJECT CMDLET</span></span>

<span data-ttu-id="25a41-136">Det mest grundläggande sättet att använda WQL-frågan är att omge det med citat tecken (som en sträng) och sedan använda frågesträngen som värde för Frågeparametern för Get-WmiObject-cmdlet, som visas i följande exempel.</span><span class="sxs-lookup"><span data-stu-id="25a41-136">The most basic way to use the WQL query is to enclose it in quotation marks (as a string) and then use the query string as the value of the Query parameter of the Get-WmiObject cmdlet, as shown in the following example.</span></span>

```powershell
Get-WmiObject -Query "Select * from Win32_Bios"
```

```output
SMBIOSBIOSVersion : 8BET56WW (1.36 )
Manufacturer      : LENOVO
Name              : Default System BIOS
SerialNumber      : R9FPY3P
Version           : LENOVO - 1360
```

<span data-ttu-id="25a41-137">Du kan också spara WQL-instruktionen i en variabel och sedan använda variabeln som värde för Frågeparametern, som du ser i följande kommando.</span><span class="sxs-lookup"><span data-stu-id="25a41-137">You can also save the WQL statement in a variable and then use the variable as the value of the Query parameter, as shown in the following command.</span></span>

```powershell
$query = "Select * from Win32_Bios"
Get-WmiObject -Query $query
```

<span data-ttu-id="25a41-138">Du kan använda något av formaten med valfri WQL-instruktion.</span><span class="sxs-lookup"><span data-stu-id="25a41-138">You can use either format with any WQL statement.</span></span> <span data-ttu-id="25a41-139">Följande kommando använder frågan i variabeln $queryName för att bara hämta namn och versions egenskaper för systemets BIOS.</span><span class="sxs-lookup"><span data-stu-id="25a41-139">The following command uses the query in the $queryName variable to get only the name and version properties of the system BIOS.</span></span>

```powershell
$queryNameVersion = "Select Name, Version from Win32_Bios"
Get-WmiObject -Query $queryNameVersion
```

```output
__GENUS          : 2
__CLASS          : Win32_BIOS
__SUPERCLASS     :
__DYNASTY        :
__RELPATH        :
__PROPERTY_COUNT : 1
__DERIVATION     : {}
__SERVER         :
__NAMESPACE      :
__PATH           :
Name             : Default System BIOS
Version          : LENOVO - 1360
```

<span data-ttu-id="25a41-140">Kom ihåg att du kan använda parametrarna för Get-WmiObject cmdlet för att få samma resultat.</span><span class="sxs-lookup"><span data-stu-id="25a41-140">Remember that you can use the parameters of the Get-WmiObject cmdlet to get the same result.</span></span> <span data-ttu-id="25a41-141">Följande kommando hämtar till exempel även värdena för namn-och versions egenskaperna för instanser av Win32_Bios WMI-klassen.</span><span class="sxs-lookup"><span data-stu-id="25a41-141">For example, the following command also gets the values of the Name and Version properties of instances of the Win32_Bios WMI class.</span></span>

```powershell
Get-WmiObject -Class Win32_Bios -Property Name, Version
```

```output
__GENUS          : 2
__CLASS          : Win32_BIOS
__SUPERCLASS     :
__DYNASTY        :
__RELPATH        :
__PROPERTY_COUNT : 1
__DERIVATION     : {}
__SERVER         :
__NAMESPACE      :
__PATH           :
Name             : Default System BIOS
Version          : LENOVO - 1360
```

## <a name="using-the-get-ciminstance-cmdlet"></a><span data-ttu-id="25a41-142">ANVÄNDA CMDLETEN GET-CIMINSTANCE</span><span class="sxs-lookup"><span data-stu-id="25a41-142">USING THE GET-CIMINSTANCE CMDLET</span></span>

<span data-ttu-id="25a41-143">Från och med Windows PowerShell 3,0 kan du använda cmdleten Get-CimInstance för att köra WQL-frågor.</span><span class="sxs-lookup"><span data-stu-id="25a41-143">Beginning in Windows PowerShell 3.0, you can use the Get-CimInstance cmdlet to run WQL queries.</span></span>

<span data-ttu-id="25a41-144">Get-CimInstance hämtar instanser av CIM-kompatibla klasser, inklusive WMI-klasser.</span><span class="sxs-lookup"><span data-stu-id="25a41-144">Get-CimInstance gets instances of CIM-compliant classes, including WMI classes.</span></span> <span data-ttu-id="25a41-145">CIM-cmdletarna introducerade Windows PowerShell 3,0 och utför samma uppgifter som WMI-cmdlets.</span><span class="sxs-lookup"><span data-stu-id="25a41-145">The CIM cmdlets, introduced Windows PowerShell 3.0, perform the same tasks as the WMI cmdlets.</span></span> <span data-ttu-id="25a41-146">CIM-cmdlets följer WS-Management (WSMan)-standarder och med Common Information Model (CIM) standard, vilket gör att cmdletarna kan använda samma metoder för att hantera Windows-datorer och datorer som kör andra operativ system.</span><span class="sxs-lookup"><span data-stu-id="25a41-146">The CIM cmdlets comply with WS-Management (WSMan) standards and with the Common Information Model (CIM) standard, which enables the cmdlets to use the same techniques to manage Windows computers and computers that are running other operating systems.</span></span>

<span data-ttu-id="25a41-147">Följande kommando använder cmdleten Get-CimInstance för att köra en WQL-fråga.</span><span class="sxs-lookup"><span data-stu-id="25a41-147">The following command uses the Get-CimInstance cmdlet to run a WQL query.</span></span>

<span data-ttu-id="25a41-148">Alla WQL-frågor som kan användas med Get-WmiObject kan också användas med Get-CimInstance.</span><span class="sxs-lookup"><span data-stu-id="25a41-148">Any WQL query that can be used with Get-WmiObject can also be used with Get-CimInstance.</span></span>

```powershell
Get-CimInstance -Query "Select * from Win32_Bios"
```

```output
SMBIOSBIOSVersion : 8BET56WW (1.36 )
Manufacturer      : LENOVO
Name              : Default System BIOS
SerialNumber      : R9FPY3P
Version           : LENOVO - 1360
```

<span data-ttu-id="25a41-149">Get-CimInstance returnerar ett CimInstance-objekt, i stället för de ManagementObject som Get-WmiObject returnerar, men objekten är ganska likartade.</span><span class="sxs-lookup"><span data-stu-id="25a41-149">Get-CimInstance returns a CimInstance object, instead of the ManagementObject that Get-WmiObject returns, but the objects are quite similar.</span></span>

```
(Get-CimInstance -Query "Select * from Win32_Bios").GetType().FullName
Microsoft.Management.Infrastructure.CimInstance
(Get-WmiObject -Query "Select * from Win32_Bios").GetType().FullName
System.Management.ManagementObject
```

## <a name="using-the-wmisearcher-type-accelerator"></a><span data-ttu-id="25a41-150">ANVÄNDA [wmisearcher]-typ ACCELERATOR</span><span class="sxs-lookup"><span data-stu-id="25a41-150">USING THE [wmisearcher] TYPE ACCELERATOR</span></span>

<span data-ttu-id="25a41-151">Typ acceleratorn [wmisearcher] skapar ett ManagementObjectSearcher-objekt från en WQL-instruktions sträng.</span><span class="sxs-lookup"><span data-stu-id="25a41-151">The [wmisearcher] type accelerator creates a ManagementObjectSearcher object from a WQL statement string.</span></span> <span data-ttu-id="25a41-152">ManagementObjectSearcher-objektet har många egenskaper och metoder, men den mest grundläggande metoden är Get-metoden, som anropar den angivna WMI-frågan och returnerar resulterande objekt.</span><span class="sxs-lookup"><span data-stu-id="25a41-152">The ManagementObjectSearcher object has many properties and methods, but the most basic method is the Get method, which invokes the specified WMI query and returns the resulting objects.</span></span>

<span data-ttu-id="25a41-153">Genom att använda [wmisearcher] får du enkel åtkomst till ManagementObjectSearcher .NET Framework-klassen.</span><span class="sxs-lookup"><span data-stu-id="25a41-153">By using the [wmisearcher], you gain easy access to the ManagementObjectSearcher .NET Framework class.</span></span> <span data-ttu-id="25a41-154">På så sätt kan du fråga WMI och konfigurera hur frågan utförs.</span><span class="sxs-lookup"><span data-stu-id="25a41-154">This lets you query WMI and to configure the way the query is conducted.</span></span>

<span data-ttu-id="25a41-155">Använda typ Accelerator [wmisearcher]:</span><span class="sxs-lookup"><span data-stu-id="25a41-155">To use the [wmisearcher] type accelerator:</span></span>

1. <span data-ttu-id="25a41-156">Omvandla WQL-strängen till ett ManagementObjectSearcher-objekt.</span><span class="sxs-lookup"><span data-stu-id="25a41-156">Cast the  WQL string into a ManagementObjectSearcher object.</span></span>
2. <span data-ttu-id="25a41-157">Anropa Get-metoden för ManagementObjectSearcher-objektet.</span><span class="sxs-lookup"><span data-stu-id="25a41-157">Call the Get method of the ManagementObjectSearcher object.</span></span>

<span data-ttu-id="25a41-158">Följande kommando skickar till exempel frågan "Select all", sparar resultatet i variabeln $bios och anropar sedan Get-metoden för ManagementObjectSearcher-objektet i $bios-variabeln.</span><span class="sxs-lookup"><span data-stu-id="25a41-158">For example, the following command casts the "select all" query, saves the result in the $bios variable, and then calls the Get method of the ManagementObjectSearcher object in the $bios variable.</span></span>

```powershell
$bios = [wmisearcher]"Select * from Win32_Bios"
$bios.Get()
```

```output
SMBIOSBIOSVersion : 8BET56WW (1.36 )
Manufacturer      : LENOVO
Name              : Default System BIOS
SerialNumber      : R9FPY3P
Version           : LENOVO - 1360
```

<span data-ttu-id="25a41-159">Obs: endast valda objekt egenskaper visas som standard.</span><span class="sxs-lookup"><span data-stu-id="25a41-159">NOTE: Only selected object properties are displayed by default.</span></span> <span data-ttu-id="25a41-160">Dessa egenskaper definieras i Types.ps1XML-filen.</span><span class="sxs-lookup"><span data-stu-id="25a41-160">These properties are defined in the Types.ps1xml file.</span></span>

<span data-ttu-id="25a41-161">Du kan använda [wmisearcher]-typ Accelerator för att omvandla frågan eller variabeln.</span><span class="sxs-lookup"><span data-stu-id="25a41-161">You can use the [wmisearcher] type accelerator to cast the query or the variable.</span></span> <span data-ttu-id="25a41-162">I följande exempel används [wmisearcher] Type Accelerator för att omvandla variabeln.</span><span class="sxs-lookup"><span data-stu-id="25a41-162">In the following example, the [wmisearcher] type accelerator is used to cast the variable.</span></span> <span data-ttu-id="25a41-163">Resultatet är detsamma.</span><span class="sxs-lookup"><span data-stu-id="25a41-163">The result is the same.</span></span>

```powershell
[wmisearcher]$bios = "Select * from Win32_Bios"
$bios.Get()
```

```output
SMBIOSBIOSVersion : 8BET56WW (1.36 )
Manufacturer      : LENOVO
Name              : Default System BIOS
SerialNumber      : R9FPY3P
Version           : LENOVO - 1360
```

<span data-ttu-id="25a41-164">När du använder typen [wmisearcher] kan du ändra frågesträngen till ett ManagementObjectSearcher-objekt, som du ser i följande kommandon.</span><span class="sxs-lookup"><span data-stu-id="25a41-164">When you use the [wmisearcher] type accelerator, it changes the query string into a ManagementObjectSearcher object, as shown in the following commands.</span></span>

```
$a = "Select * from Win32_Bios"
$a.GetType().FullName
System.String

$a = [wmisearcher]"Select * from Win32_Bios"
$a.GetType().FullName
System.Management.ManagementObjectSearcher
```

<span data-ttu-id="25a41-165">Det här kommando formatet fungerar för alla frågor.</span><span class="sxs-lookup"><span data-stu-id="25a41-165">This command format works on any query.</span></span> <span data-ttu-id="25a41-166">Följande kommando hämtar värdet för egenskapen Name i Win32_Bios WMI-klassen.</span><span class="sxs-lookup"><span data-stu-id="25a41-166">The following command gets the value of the Name property of the Win32_Bios WMI class.</span></span>

```powershell
$biosname = [wmisearcher]"Select Name from Win32_Bios"
$biosname.Get()
```

```output
__GENUS          : 2
__CLASS          : Win32_BIOS
__SUPERCLASS     :
__DYNASTY        :
__RELPATH        :
__PROPERTY_COUNT : 1
__DERIVATION     : {}
__SERVER         :
__NAMESPACE      :
__PATH           :
Name             : Default System BIOS
```

<span data-ttu-id="25a41-167">Du kan utföra den här åtgärden i ett enda kommando, men kommandot är lite svårare att tolka.</span><span class="sxs-lookup"><span data-stu-id="25a41-167">You can perform this operation in a single command, although the command is a bit more difficult to interpret.</span></span>

<span data-ttu-id="25a41-168">I det här formatet använder du text acceleratorn [wmisearcher] för att omvandla WQL-frågesträngen till en ManagementObjectSearcher och anropa sedan metoden get i objektet--all i ett enda kommando.</span><span class="sxs-lookup"><span data-stu-id="25a41-168">In this format, you use the [wmisearcher] type accelerator to cast the WQL query string to a ManagementObjectSearcher, and then call the Get method on the object -- all in a single command.</span></span> <span data-ttu-id="25a41-169">Parenteserna () som omger den Casted strängen Direct Windows PowerShell för att omvandla strängen innan metoden anropas.</span><span class="sxs-lookup"><span data-stu-id="25a41-169">The parentheses () that enclose the casted string direct Windows PowerShell to cast the string before calling the method.</span></span>

```powershell
([wmisearcher]"Select name from Win32_Bios").Get()
```

```output
__GENUS          : 2
__CLASS          : Win32_BIOS
__SUPERCLASS     :
__DYNASTY        :
__RELPATH        :
__PROPERTY_COUNT : 1
__DERIVATION     : {}
__SERVER         :
__NAMESPACE      :
__PATH           :
Name             : Default System BIOS
```

## <a name="using-the-basic-wql-where-statement"></a><span data-ttu-id="25a41-170">ANVÄNDA BASIC WQL WHERE-INSTRUKTION</span><span class="sxs-lookup"><span data-stu-id="25a41-170">USING THE BASIC WQL WHERE STATEMENT</span></span>

<span data-ttu-id="25a41-171">En WHERE-instruktion upprättar villkor för de data som en SELECT-instruktion returnerar.</span><span class="sxs-lookup"><span data-stu-id="25a41-171">A Where statement establishes conditions for the data that a Select statement returns.</span></span>

<span data-ttu-id="25a41-172">WHERE-instruktionen har följande format:</span><span class="sxs-lookup"><span data-stu-id="25a41-172">The Where statement has the following format:</span></span>

```
where <property> <operator> <value>
```

<span data-ttu-id="25a41-173">Ett exempel:</span><span class="sxs-lookup"><span data-stu-id="25a41-173">For example:</span></span>

```
where Name = 'Notepad.exe'
```

<span data-ttu-id="25a41-174">WHERE-instruktionen används med SELECT-instruktionen, som visas i följande exempel.</span><span class="sxs-lookup"><span data-stu-id="25a41-174">The Where statement is used with the Select statement, as shown in the following example.</span></span>

```
Select * from Win32_Process where Name = 'Notepad.exe'
```

<span data-ttu-id="25a41-175">När du använder instruktionen WHERE måste egenskaps namnet och värdet vara korrekt.</span><span class="sxs-lookup"><span data-stu-id="25a41-175">When using the Where statement, the property name and value must be accurate.</span></span>

<span data-ttu-id="25a41-176">Följande kommando hämtar till exempel anteckningar-processerna på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="25a41-176">For example, the following command gets the Notepad processes on the local computer.</span></span>

```powershell
Get-WmiObject -Query "Select * from Win32_Process where name='Notepad.exe'"
```

<span data-ttu-id="25a41-177">Följande kommando Miss lyckas dock, eftersom process namnet innehåller fil namns tillägget ". exe".</span><span class="sxs-lookup"><span data-stu-id="25a41-177">However, the following command fails, because the process name includes the ".exe" file name extension.</span></span>

```powershell
Get-WmiObject -Query "Select * from Win32_Process where name='Notepad'"
```

## <a name="where-statement-comparison-operators"></a><span data-ttu-id="25a41-178">WHERE-SATSEN JÄMFÖRELSE OPERATORER</span><span class="sxs-lookup"><span data-stu-id="25a41-178">WHERE STATEMENT COMPARISON OPERATORS</span></span>

<span data-ttu-id="25a41-179">Följande operatorer är giltiga i en WQL WHERE-instruktion.</span><span class="sxs-lookup"><span data-stu-id="25a41-179">The following operators are valid in a WQL Where statement.</span></span>

```
Operator    Description
-----------------------
=           Equal
!=          Not equal
<>          Not equal
<           Less than
>           Greater than
<=          Less than or equal
>=          Greater than or equal
LIKE        Wildcard match
IS          Evaluates null
ISNOT       Evaluates not null
ISA         Evaluates a member of a WMI class
```

<span data-ttu-id="25a41-180">Det finns andra operatorer, men de är de som används för att jämföra dem.</span><span class="sxs-lookup"><span data-stu-id="25a41-180">There are other operators, but these are the ones used for making comparisons.</span></span>

<span data-ttu-id="25a41-181">Följande fråga väljer till exempel namn och prioritets egenskaper från processer i Win32_Process-klassen där process prioriteten är större än eller lika med 11.</span><span class="sxs-lookup"><span data-stu-id="25a41-181">For example, the following query selects the Name and Priority properties from processes in the Win32_Process class where the process priority is greater than or equal to 11.</span></span> <span data-ttu-id="25a41-182">Get-WmiObject cmdleten kör frågan.</span><span class="sxs-lookup"><span data-stu-id="25a41-182">The Get-WmiObject cmdlet runs the query.</span></span>

```powershell
$highPriority = "Select Name, Priority from Win32_Process " +
  "where Priority >= 11"
Get-WmiObject -Query $highPriority
```

## <a name="using-the-wql-operators-in-the-filter-parameter"></a><span data-ttu-id="25a41-183">ANVÄNDA WQL-OPERATÖRER I FILTER PARAMETERN</span><span class="sxs-lookup"><span data-stu-id="25a41-183">USING THE WQL OPERATORS IN THE FILTER PARAMETER</span></span>

<span data-ttu-id="25a41-184">WQL-operatörer kan också användas i värdet för filter parametern för Get-WmiObject-eller Get-CimInstance-cmdletar, samt i värdet för frågeparametrar för dessa cmdletar.</span><span class="sxs-lookup"><span data-stu-id="25a41-184">The WQL operators can also be used in the value of the Filter parameter of the Get-WmiObject or Get-CimInstance cmdlets, as well as in the value of the Query parameters of these cmdlets.</span></span>

<span data-ttu-id="25a41-185">Följande kommando hämtar till exempel namn-och ProcessID-egenskaperna för de senaste fem processerna som har ProcessID-värden som är större än 1004.</span><span class="sxs-lookup"><span data-stu-id="25a41-185">For example, the following command gets the Name and ProcessID properties of the last five processes that have ProcessID values greater than 1004.</span></span> <span data-ttu-id="25a41-186">Kommandot använder filter parametern för att ange ProcessID-villkoret.</span><span class="sxs-lookup"><span data-stu-id="25a41-186">The command uses the Filter parameter to specify the ProcessID condition.</span></span>

```powershell
Get-WmiObject -Class Win32_Process `
-Property Name, ProcessID -Filter "ProcessID >= 1004" |
Sort ProcessID | Select Name, ProcessID -Last 5
```

```output
Name                                 ProcessID
----                                 ---------
SROSVC.exe                                4220
WINWORD.EXE                               4664
TscHelp.exe                               4744
SnagIt32.exe                              4748
WmiPrvSE.exe                              5056
```

## <a name="using-the-like-operator"></a><span data-ttu-id="25a41-187">ANVÄNDA OPERATORN LIKE</span><span class="sxs-lookup"><span data-stu-id="25a41-187">USING THE LIKE OPERATOR</span></span>

<span data-ttu-id="25a41-188">Operatorn Like gör att du kan använda jokertecken för att filtrera resultatet av en WQL-fråga.</span><span class="sxs-lookup"><span data-stu-id="25a41-188">The Like operator lets you use wildcard characters to filter the results of a WQL query.</span></span>

```
Like Operator  Description
--------------------------------------------------
[]             Character in a range [a-f] or a set
               of characters [abcdef]. The items in
               a set do not need to be consecutive or
               listed in alphabetical order.

^              Character not in a range [^a-f] or
               not in a set [^abcdef]. The items in
               a set do not need to be consecutive or
               listed in alphabetical order.

%              A string of zero or more characters

_              One character.
(underscore)   NOTE: To use a literal underscore
               in a query string, enclose it in
               square brackets [_].
```

<span data-ttu-id="25a41-189">När operatorn Like används utan jokertecken eller intervall operatorer beter sig den som likhets operatorn (=) och returnerar bara objekt när de är en exakt matchning för mönstret.</span><span class="sxs-lookup"><span data-stu-id="25a41-189">When the Like operator is used without any wildcard characters or range operators, it behaves like the equality operator (=) and returns objects only when they are an exact match for the pattern.</span></span>

<span data-ttu-id="25a41-190">Du kan kombinera åtgärds området med jokertecknet i procent för att skapa enkla, men ändå kraftfulla filter.</span><span class="sxs-lookup"><span data-stu-id="25a41-190">You can combine the range operation with the percent wildcard character to create simple, yet powerful filters.</span></span>

### <a name="like-operator-examples"></a><span data-ttu-id="25a41-191">EXEMPEL PÅ LIKE-OPERATOR</span><span class="sxs-lookup"><span data-stu-id="25a41-191">LIKE OPERATOR EXAMPLES</span></span>

#### <a name="example-1-range"></a><span data-ttu-id="25a41-192">EXEMPEL 1: [ \<range> ]</span><span class="sxs-lookup"><span data-stu-id="25a41-192">EXAMPLE 1: [\<range>]</span></span>

<span data-ttu-id="25a41-193">Följande kommandon startar anteckningar och söker sedan efter en instans av klassen Win32_Process som har ett namn som börjar med en bokstav mellan "H" och "N" (Skift läges okänsligt).</span><span class="sxs-lookup"><span data-stu-id="25a41-193">The following commands start Notepad and then search for an instance of the Win32_Process class that has a name that starts with a letter between "H" and "N" (case-insensitive).</span></span>

<span data-ttu-id="25a41-194">Frågan ska returnera vilken process som helst från Hotpad.exe via Notepad.exe.</span><span class="sxs-lookup"><span data-stu-id="25a41-194">The query should return any process from Hotpad.exe through Notepad.exe.</span></span>

```powershell
Notepad   # Starts Notepad
$query = "Select * from win32_Process where Name LIKE '[H-N]otepad.exe'"
Get-WmiObject -Query $query | Select Name, ProcessID
```

```output
Name                                ProcessID
----                                ---------
notepad.exe                              1740
```

#### <a name="example-2-range-and-"></a><span data-ttu-id="25a41-195">EXEMPEL 2: [ \<range> ] och%</span><span class="sxs-lookup"><span data-stu-id="25a41-195">EXAMPLE 2: [\<range>] and %</span></span>

<span data-ttu-id="25a41-196">Följande kommandon väljer alla processer som har ett namn som börjar med en bokstav mellan A och P (Skift läges okänsligt) följt av noll eller flera bokstäver i valfri kombination.</span><span class="sxs-lookup"><span data-stu-id="25a41-196">The following commands select all process that have a name that begins with a letter between A and P (case-insensitive) followed by zero or more letters in any combination.</span></span>

<span data-ttu-id="25a41-197">Get-WmiObject cmdleten kör frågan, Select-Object-cmdleten hämtar egenskaperna för namn och ProcessID och Sort-Object-cmdlet sorterar resultaten i bokstavs ordning efter namn.</span><span class="sxs-lookup"><span data-stu-id="25a41-197">The Get-WmiObject cmdlet runs the query, the Select-Object cmdlet gets the Name and ProcessID properties, and the Sort-Object cmdlet sorts the results in alphabetical order by name.</span></span>

```powershell
$query = "Select * from win32_Process where name LIKE '[A-P]%'"
Get-WmiObject -Query $query |
Select-Object -Property Name, ProcessID |
Sort-Object -Property Name
```

#### <a name="example-3-not-in-range-"></a><span data-ttu-id="25a41-198">EXEMPEL 3: inte inom intervallet (^)</span><span class="sxs-lookup"><span data-stu-id="25a41-198">EXAMPLE 3: Not in Range (^)</span></span>

<span data-ttu-id="25a41-199">Följande kommando hämtar processer vars namn inte börjar med någon av följande bokstäver: A, S, W, P, R, C, U, N</span><span class="sxs-lookup"><span data-stu-id="25a41-199">The following command gets processes whose names do not begin with any of the following letters: A, S, W, P, R, C, U, N</span></span>

<span data-ttu-id="25a41-200">och följde noll eller flera bokstäver.</span><span class="sxs-lookup"><span data-stu-id="25a41-200">and followed zero or more letters.</span></span>

```powershell
$query = "Select * from win32_Process where name LIKE '[^ASWPRCUN]%'"
Get-WmiObject -Query $query |
Select-Object -Property Name, ProcessID |
Sort-Object -Property Name
```

#### <a name="example-4-any-characters----or-none-"></a><span data-ttu-id="25a41-201">EXEMPEL 4: alla tecken, eller inget (%)</span><span class="sxs-lookup"><span data-stu-id="25a41-201">EXAMPLE 4: Any characters -- or none (%)</span></span>

<span data-ttu-id="25a41-202">Följande kommandon hämtar processer som har namn som börjar med "Calc".</span><span class="sxs-lookup"><span data-stu-id="25a41-202">The following commands get processes that have names that begin with "calc".</span></span>
<span data-ttu-id="25a41-203">Symbolen% i WQL motsvarar asterisken ( \* ) i reguljära uttryck.</span><span class="sxs-lookup"><span data-stu-id="25a41-203">The % symbol in WQL is equivalent to the asterisk (\*) symbol in regular expressions.</span></span>

```powershell
$query = "Select * from win32_Process where Name LIKE 'calc%'"
Get-WmiObject -Query $query | Select-Object -Property Name, ProcessID
```

```output
Name                               ProcessID
----                               ---------
calc.exe                                4424
```

#### <a name="example-5-one-character-_"></a><span data-ttu-id="25a41-204">EXEMPEL 5: ett Character (_)</span><span class="sxs-lookup"><span data-stu-id="25a41-204">EXAMPLE 5: One character (_)</span></span>

<span data-ttu-id="25a41-205">Följande kommandon hämtar processer som har namn som har följande mönster: "c_lc.exe" där under strecks tecknet representerar ett tecken.</span><span class="sxs-lookup"><span data-stu-id="25a41-205">The following commands get processes that have names that have the following pattern, "c_lc.exe" where the underscore character represents any one character.</span></span> <span data-ttu-id="25a41-206">Det här mönstret matchar alla namn från calc.exe via czlc.exe eller c9lc.exe, men matchar inte namnen där "c" och "l" är avgränsade med mer än ett.</span><span class="sxs-lookup"><span data-stu-id="25a41-206">This pattern matches any name from calc.exe through czlc.exe, or c9lc.exe, but does not match names in which the "c" and "l" are separated by more than one character.</span></span>

```powershell
$query = "Select * from Win32_Process where Name LIKE 'c_lc.exe'"
Get-WmiObject -Query $query | Select-Object -Property Name, ProcessID
```

```output
Name                                 ProcessID
----                                 ---------
calc.exe                                  4424
```

#### <a name="example-6-exact-match"></a><span data-ttu-id="25a41-207">EXEMPEL 6: exakt matchning</span><span class="sxs-lookup"><span data-stu-id="25a41-207">EXAMPLE 6: Exact match</span></span>

<span data-ttu-id="25a41-208">Följande kommandon hämtar processer med namnet WLIDSVC.exe.</span><span class="sxs-lookup"><span data-stu-id="25a41-208">The following commands get processes named WLIDSVC.exe.</span></span> <span data-ttu-id="25a41-209">Även om frågan använder nyckelordet like krävs en exakt matchning, eftersom värdet inte innehåller jokertecken.</span><span class="sxs-lookup"><span data-stu-id="25a41-209">Even though the query uses the Like keyword, it requires an exact match, because the value does not include any wildcard characters.</span></span>

```powershell
$query = "Select * from win32_Process where name LIKE 'WLIDSVC.exe'"
Get-WmiObject -Query $query | Select-Object -Property Name, ProcessID
```powershell

```output
Name                                 ProcessID
----                                 ---------
WLIDSVC.exe                                84
```

## <a name="using-the-or-operator"></a><span data-ttu-id="25a41-210">ANVÄNDA OPERATORN OR</span><span class="sxs-lookup"><span data-stu-id="25a41-210">USING THE OR OPERATOR</span></span>

<span data-ttu-id="25a41-211">Om du vill ange flera oberoende villkor använder du nyckelordet eller.</span><span class="sxs-lookup"><span data-stu-id="25a41-211">To specify multiple independent conditions, use the Or keyword.</span></span> <span data-ttu-id="25a41-212">Nyckelordet eller visas i WHERE-satsen.</span><span class="sxs-lookup"><span data-stu-id="25a41-212">The Or keyword appears in the Where clause.</span></span> <span data-ttu-id="25a41-213">Den utför en eller flera åtgärder på två (eller fler) villkor och returnerar objekt som uppfyller något av villkoren.</span><span class="sxs-lookup"><span data-stu-id="25a41-213">It performs an inclusive OR operation on two (or more) conditions and returns items that meet any of the conditions.</span></span>

<span data-ttu-id="25a41-214">Operatorn OR har följande format:</span><span class="sxs-lookup"><span data-stu-id="25a41-214">The Or operator has the following format:</span></span>

```
Where <property> <operator> <value> or <property> <operator> <value> ...
```

<span data-ttu-id="25a41-215">Följande kommandon hämtar till exempel alla instanser av klassen Win32_Process WMI men returnerar dem endast om process namnet är winword.exe eller excel.exe.</span><span class="sxs-lookup"><span data-stu-id="25a41-215">For example, the following commands get all instances of the Win32_Process WMI class but returns them only if the process name is winword.exe or excel.exe.</span></span>

```powershell
$q = "Select * from Win32_Process where Name='winword.exe'" +
  " or Name='excel.exe'"
Get-WmiObject -Query $q
```

<span data-ttu-id="25a41-216">Instruktionen or kan användas med fler än två villkor.</span><span class="sxs-lookup"><span data-stu-id="25a41-216">The Or statement can be used with more than two conditions.</span></span> <span data-ttu-id="25a41-217">I följande fråga hämtar or-instruktionen Winword.exe, Excel.exe eller Powershell.exe.</span><span class="sxs-lookup"><span data-stu-id="25a41-217">In the following query, the Or statement gets Winword.exe, Excel.exe, or Powershell.exe.</span></span>

```powershell
$q = "Select * from Win32_Process where Name='winword.exe'" +
  " or Name='excel.exe' or Name='powershell.exe'"
```

## <a name="using-the-and-operator"></a><span data-ttu-id="25a41-218">ANVÄNDA OPERATORN OCH</span><span class="sxs-lookup"><span data-stu-id="25a41-218">USING THE AND OPERATOR</span></span>

<span data-ttu-id="25a41-219">Om du vill ange flera relaterade villkor använder du nyckelordet och.</span><span class="sxs-lookup"><span data-stu-id="25a41-219">To specify multiple related conditions, use the And keyword.</span></span> <span data-ttu-id="25a41-220">Nyckelordet och visas i WHERE-satsen.</span><span class="sxs-lookup"><span data-stu-id="25a41-220">The And keyword appears in the Where clause.</span></span> <span data-ttu-id="25a41-221">Den returnerar objekt som uppfyller alla villkor.</span><span class="sxs-lookup"><span data-stu-id="25a41-221">It returns items that meet all of the conditions.</span></span>

<span data-ttu-id="25a41-222">Operatorn och har följande format:</span><span class="sxs-lookup"><span data-stu-id="25a41-222">The And operator has the following format:</span></span>

```
Where <property> <operator> <value> and <property> <operator> <value> ...
```

<span data-ttu-id="25a41-223">Följande kommandon får till exempel processer som har namnet "Winword.exe" och process-ID: t 6512.</span><span class="sxs-lookup"><span data-stu-id="25a41-223">For example, the following commands get processes that have a name of "Winword.exe" and the process ID of 6512.</span></span>

<span data-ttu-id="25a41-224">Observera att kommandona använder Get-CimInstance-cmdleten.</span><span class="sxs-lookup"><span data-stu-id="25a41-224">Note that the commands use the Get-CimInstance cmdlet.</span></span>

```powershell
$q = "Select * from Win32_Process where Name = 'winword.exe' " +
  "and ProcessID =6512"
Get-CimInstance -Query $q
```

```output
ProcessId   Name             HandleCount      WorkingSetSize   VirtualSize
---------   ----             -----------      --------------   -----------
# 6512      WINWORD.EXE      768              117170176        633028608
```

<span data-ttu-id="25a41-225">Alla operatorer, inklusive like-operatorer, är giltiga med operatorerna or och och.</span><span class="sxs-lookup"><span data-stu-id="25a41-225">All operators, including the Like operators are valid with the Or and And operators.</span></span> <span data-ttu-id="25a41-226">Och du kan kombinera operatorerna or och och och i en enskild fråga med parenteser som anger för Windows PowerShell vilka satser som ska bearbetas först.</span><span class="sxs-lookup"><span data-stu-id="25a41-226">And, you can combine the Or and And operators in a single query with parentheses that tell Windows PowerShell which clauses to process first.</span></span>

<span data-ttu-id="25a41-227">Det här kommandot använder fortsättnings tecknen i Windows PowerShell (') för att dela upp kommandot i två rader.</span><span class="sxs-lookup"><span data-stu-id="25a41-227">This command uses the Windows PowerShell continuation character (\`) divide the command into two lines.</span></span>

```powershell
$q = "Select * from Win32_Process `
where (Name = 'winword.exe' or Name = 'excel.exe') and HandleCount > 700"
Get-CimInstance -Query $q
```

```output
ProcessId    Name             HandleCount      WorkingSetSize   VirtualSize
---------    ----             -----------      --------------   -----------
     6512    WINWORD.EXE      797              117268480        634425344
     9610    EXCEL.EXE        727               38858752        323227648
```

## <a name="searching-for-null-values"></a><span data-ttu-id="25a41-228">SÖKER EFTER NULL-VÄRDEN</span><span class="sxs-lookup"><span data-stu-id="25a41-228">SEARCHING FOR NULL VALUES</span></span>

<span data-ttu-id="25a41-229">Det är svårt att söka efter null-värden i WMI, eftersom det kan leda till oförutsägbara resultat.</span><span class="sxs-lookup"><span data-stu-id="25a41-229">Searching for null values in WMI is challenging, because it can lead to unpredictable results.</span></span> <span data-ttu-id="25a41-230">Null är inte noll och är inte detsamma som eller en tom sträng.</span><span class="sxs-lookup"><span data-stu-id="25a41-230">Null is not zero and it is not equivalent or to an empty string.</span></span> <span data-ttu-id="25a41-231">Vissa egenskaper för WMI-klass initieras och andra är inte, så en sökning efter null kanske inte fungerar för alla egenskaper.</span><span class="sxs-lookup"><span data-stu-id="25a41-231">Some WMI class properties are initialized and others are not, so a search for null might not work for all properties.</span></span>

<span data-ttu-id="25a41-232">Om du vill söka efter null-värden använder du operatorn är med värdet null.</span><span class="sxs-lookup"><span data-stu-id="25a41-232">To search for null values, use the Is operator with a value of "null".</span></span>

<span data-ttu-id="25a41-233">Följande kommandon får till exempel processer som har ett null-värde för egenskapen IntallDate.</span><span class="sxs-lookup"><span data-stu-id="25a41-233">For example, the following commands get processes that have a null value for the IntallDate property.</span></span> <span data-ttu-id="25a41-234">Kommandona returnerar många processer.</span><span class="sxs-lookup"><span data-stu-id="25a41-234">The commands return many processes.</span></span>

```powershell
$q = "Select * from Win32_Process where InstallDate is null"
Get-WmiObject -Query $q
```

<span data-ttu-id="25a41-235">Följande kommando hämtar däremot användar konton som har ett null-värde för egenskapen Description.</span><span class="sxs-lookup"><span data-stu-id="25a41-235">In contrast, the following command, gets user accounts that have a null value for the Description property.</span></span> <span data-ttu-id="25a41-236">Det här kommandot returnerar inga användar konton, även om de flesta användar konton inte har något värde för egenskapen Description.</span><span class="sxs-lookup"><span data-stu-id="25a41-236">This command does not return any user accounts, even though most user accounts do not have any value for the Description property.</span></span>

```powershell
$q = "Select * from Win32_UserAccount where Description is null"
Get-WmiObject -Query $q
```

<span data-ttu-id="25a41-237">Om du vill hitta användar konton som saknar värde för egenskapen Description använder du likhets operatorn för att hämta en tom sträng.</span><span class="sxs-lookup"><span data-stu-id="25a41-237">To find the user accounts that have no value for the Description property, use the equality operator to get an empty string.</span></span> <span data-ttu-id="25a41-238">Om du vill visa den tomma strängen använder du två enkla citat tecken i följd.</span><span class="sxs-lookup"><span data-stu-id="25a41-238">To represent the empty string, use two consecutive single quotation marks.</span></span>

```powershell
$q = "Select * from Win32_UserAccount where Description = '' "
```

## <a name="using-true-or-false"></a><span data-ttu-id="25a41-239">ANVÄNDA TRUE ELLER FALSE</span><span class="sxs-lookup"><span data-stu-id="25a41-239">USING TRUE OR FALSE</span></span>

<span data-ttu-id="25a41-240">Om du vill hämta booleska värden i egenskaperna för WMI-objekt, använder du True och false.</span><span class="sxs-lookup"><span data-stu-id="25a41-240">To get Boolean values in the properties of WMI objects, use True and False.</span></span>
<span data-ttu-id="25a41-241">De är inte skiftlägeskänsliga.</span><span class="sxs-lookup"><span data-stu-id="25a41-241">They are not case sensitive.</span></span>

<span data-ttu-id="25a41-242">Följande WQL-fråga returnerar endast lokala användar konton från en domänansluten dator.</span><span class="sxs-lookup"><span data-stu-id="25a41-242">The following WQL query returns only local user accounts from a domain joined computer.</span></span>

```powershell
$q = "Select * from Win32_UserAccount where LocalAccount = True"
Get-CimInstance -Query $q
```

<span data-ttu-id="25a41-243">Om du vill hitta domän konton använder du värdet FALSKT, som du ser i följande exempel.</span><span class="sxs-lookup"><span data-stu-id="25a41-243">To find domain accounts, use a value of False, as shown in the following example.</span></span>

```powershell
$q = "Select * from Win32_UserAccount where LocalAccount = False"
Get-CimInstance -Query $q
```

## <a name="using-the-escape-character"></a><span data-ttu-id="25a41-244">ANVÄNDA ESCAPE-TECKEN</span><span class="sxs-lookup"><span data-stu-id="25a41-244">USING THE ESCAPE CHARACTER</span></span>

<span data-ttu-id="25a41-245">WQL använder omvänt snedstreck ( \) som escape-tecken).</span><span class="sxs-lookup"><span data-stu-id="25a41-245">WQL uses the backslash (\) as its escape character.</span></span> <span data-ttu-id="25a41-246">Detta skiljer sig från Windows PowerShell, som använder Baknings tecknen (').</span><span class="sxs-lookup"><span data-stu-id="25a41-246">This is different from Windows PowerShell, which uses the backtick character (\`).</span></span>

<span data-ttu-id="25a41-247">Citat tecken och tecknen som används för citat tecken måste ofta vara undantagna så att de inte tolkas.</span><span class="sxs-lookup"><span data-stu-id="25a41-247">Quotation marks, and the characters used for quotation marks, often need to be escaped so that they are not misinterpreted.</span></span>

<span data-ttu-id="25a41-248">Om du vill hitta en användare vars namn innehåller ett enkelt citat tecken, använder du ett omvänt snedstreck för att undvika det enkla citat tecknet, som du ser i följande kommando.</span><span class="sxs-lookup"><span data-stu-id="25a41-248">To find a user whose name includes a single quotation mark, use a backslash to escape the single quotation mark, as shown in the following command.</span></span>

```powershell
$q = "Select * from Win32_UserAccount where Name = 'Tim O\'Brian'"
Get-CimInstance -Query $q
```

```output
Name             Caption          AccountType      SID              Domain
----             -------          -----------      ---              ------
Tim O'Brian      FABRIKAM\TimO    512              S-1-5-21-1457... FABRIKAM
```

<span data-ttu-id="25a41-249">I vissa fall måste omvänt snedstreck också vara ett undantag.</span><span class="sxs-lookup"><span data-stu-id="25a41-249">In some case, the backslash also needs to be escaped.</span></span> <span data-ttu-id="25a41-250">Följande kommandon genererar till exempel ett ogiltigt frågefel på grund av omvänt snedstreck i värdet Caption.</span><span class="sxs-lookup"><span data-stu-id="25a41-250">For example, the following commands generate an Invalid Query error due to the backslash in the Caption value.</span></span>

```powershell
$q = "Select * from Win32_UserAccount where Caption = 'Fabrikam\TimO'"
Get-CimInstance -Query $q
```

```output
Get-CimInstance : Invalid query
At line:1 char:1
+ Get-CimInstance -Query $q
+ ~~~~~~~~~~~
  + CategoryInfo          : InvalidArgument: (:) [Get-CimInstance], CimExcep
  + FullyQualifiedErrorId : HRESULT 0x80041017,Microsoft.Management.Infrastr
```

<span data-ttu-id="25a41-251">Om du vill undanta omvänt snedstreck använder du ett andra omvänt snedstreck, som du ser i följande kommando.</span><span class="sxs-lookup"><span data-stu-id="25a41-251">To escape the backslash, use a second backslash character, as shown in the following command.</span></span>

```powershell
$q = "Select * from Win32_UserAccount where Caption = 'Fabrikam\\TimO'"
Get-CimInstance -Query $q
```

## <a name="see-also"></a><span data-ttu-id="25a41-252">SE ÄVEN</span><span class="sxs-lookup"><span data-stu-id="25a41-252">SEE ALSO</span></span>

[<span data-ttu-id="25a41-253">about_Special_Characters</span><span class="sxs-lookup"><span data-stu-id="25a41-253">about_Special_Characters</span></span>](about_Special_Characters.md)

[<span data-ttu-id="25a41-254">about_Quoting_Rules</span><span class="sxs-lookup"><span data-stu-id="25a41-254">about_Quoting_Rules</span></span>](about_Quoting_Rules.md)

[<span data-ttu-id="25a41-255">about_WMI</span><span class="sxs-lookup"><span data-stu-id="25a41-255">about_WMI</span></span>](about_WMI.md)

[<span data-ttu-id="25a41-256">about_WMI_Cmdlets</span><span class="sxs-lookup"><span data-stu-id="25a41-256">about_WMI_Cmdlets</span></span>](about_WMI_Cmdlets.md)
