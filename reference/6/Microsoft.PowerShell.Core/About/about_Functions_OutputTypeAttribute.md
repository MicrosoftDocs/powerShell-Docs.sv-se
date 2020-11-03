---
description: Beskriver ett attribut som rapporterar den typ av objekt som funktionen returnerar.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 01/03/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_functions_outputtypeattribute?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Functions_OutputTypeAttribute
ms.openlocfilehash: 94e6ab9926f8d31e6b7602792f836fa5eadd3b50
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/13/2020
ms.locfileid: "93270722"
---
# <a name="about-functions-outputtypeattribute"></a><span data-ttu-id="79f68-104">Om functions-OutputTypeAttribute</span><span class="sxs-lookup"><span data-stu-id="79f68-104">About Functions OutputTypeAttribute</span></span>

## <a name="short-description"></a><span data-ttu-id="79f68-105">KORT BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="79f68-105">SHORT DESCRIPTION</span></span>
<span data-ttu-id="79f68-106">Beskriver ett attribut som rapporterar den typ av objekt som funktionen returnerar.</span><span class="sxs-lookup"><span data-stu-id="79f68-106">Describes an attribute that reports the type of object that the function returns.</span></span>

## <a name="long-description"></a><span data-ttu-id="79f68-107">LÅNG BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="79f68-107">LONG DESCRIPTION</span></span>

<span data-ttu-id="79f68-108">Attributet OutputType visar de .NET-typer av objekt som funktionerna returnerar.</span><span class="sxs-lookup"><span data-stu-id="79f68-108">The OutputType attribute lists the .NET types of objects that the functions returns.</span></span> <span data-ttu-id="79f68-109">Du kan använda en valfri ParameterSetName-parameter för att lista olika utdatatyper för varje parameter uppsättning.</span><span class="sxs-lookup"><span data-stu-id="79f68-109">You can use its optional ParameterSetName parameter to list different output types for each parameter set.</span></span>

<span data-ttu-id="79f68-110">Attributet OutputType stöds i enkla och avancerade funktioner.</span><span class="sxs-lookup"><span data-stu-id="79f68-110">The OutputType attribute is supported on simple and advanced functions.</span></span> <span data-ttu-id="79f68-111">Den är oberoende av CmdletBinding-attributet.</span><span class="sxs-lookup"><span data-stu-id="79f68-111">It is independent of the CmdletBinding attribute.</span></span>

<span data-ttu-id="79f68-112">Attributet OutputType tillhandahåller värdet för egenskapen OutputType för objektet **system. Management. Automation. FunctionInfo** som `Get-Command` cmdleten returnerar.</span><span class="sxs-lookup"><span data-stu-id="79f68-112">The OutputType attribute provides the value of the OutputType property of the **System.Management.Automation.FunctionInfo** object that the `Get-Command` cmdlet returns.</span></span>

<span data-ttu-id="79f68-113">Värdet för OutputType-attributet är bara en dokumentations anteckning.</span><span class="sxs-lookup"><span data-stu-id="79f68-113">The OutputType attribute value is only a documentation note.</span></span> <span data-ttu-id="79f68-114">Den härleds inte från funktions koden eller jämförs med den faktiska funktionens utdata.</span><span class="sxs-lookup"><span data-stu-id="79f68-114">It is not derived from the function code or compared to the actual function output.</span></span> <span data-ttu-id="79f68-115">Därför kan värdet vara felaktigt.</span><span class="sxs-lookup"><span data-stu-id="79f68-115">As such, the value might be inaccurate.</span></span>

## <a name="syntax"></a><span data-ttu-id="79f68-116">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="79f68-116">SYNTAX</span></span>

<span data-ttu-id="79f68-117">Attributet OutputType för functions har följande syntax:</span><span class="sxs-lookup"><span data-stu-id="79f68-117">The OutputType attribute of functions has the following syntax:</span></span>

```
[OutputType([<TypeLiteral>], ParameterSetName="<Name>")]
[OutputType("<TypeNameString>", ParameterSetName="<Name>")]
```

<span data-ttu-id="79f68-118">Parametern **ParameterSetName** är valfri.</span><span class="sxs-lookup"><span data-stu-id="79f68-118">The **ParameterSetName** parameter is optional.</span></span>

<span data-ttu-id="79f68-119">Du kan visa flera typer i attributet OutputType.</span><span class="sxs-lookup"><span data-stu-id="79f68-119">You can list multiple types in the OutputType attribute.</span></span>

```
[OutputType([<Type1>],[<Type2>],[<Type3>])]
```

<span data-ttu-id="79f68-120">Du kan använda parametern **ParameterSetName** för att ange att olika parameter uppsättningar returnerar olika typer.</span><span class="sxs-lookup"><span data-stu-id="79f68-120">You can use the **ParameterSetName** parameter to indicate that different parameter sets return different types.</span></span>

```
[OutputType([<Type1>], ParameterSetName=("<Set1>","<Set2>"))]
[OutputType([<Type2>], ParameterSetName="<Set3>")]
```

<span data-ttu-id="79f68-121">Placera instruktionerna för OutputType-attribut i listan attribut som föregår `Param` instruktionen.</span><span class="sxs-lookup"><span data-stu-id="79f68-121">Place the OutputType attribute statements in the attributes list that precedes the `Param` statement.</span></span>

<span data-ttu-id="79f68-122">I följande exempel visas placeringen av OutputType-attributet i en enkel funktion.</span><span class="sxs-lookup"><span data-stu-id="79f68-122">The following example shows the placement of the OutputType attribute in a simple function.</span></span>

```powershell
function SimpleFunction2
{
  [OutputType([<Type>])]
  Param ($Parameter1)

  <function body>
}
```

<span data-ttu-id="79f68-123">I följande exempel visas placeringen av attributet OutputType i avancerade funktioner.</span><span class="sxs-lookup"><span data-stu-id="79f68-123">The following example shows the placement of the OutputType attribute in advanced functions.</span></span>

```powershell
function AdvancedFunction1
{
  [OutputType([<Type>])]
  Param (
    [parameter(Mandatory=$true)]
    [String[]]
    $Parameter1
  )

  <function body>
}

function AdvancedFunction2
{
  [CmdletBinding(SupportsShouldProcess=<Boolean>)]
  [OutputType([<Type>])]
  Param (
    [parameter(Mandatory=$true)]
    [String[]]
    $Parameter1
  )

  <function body>
}
```

## <a name="examples"></a><span data-ttu-id="79f68-124">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="79f68-124">EXAMPLES</span></span>

### <a name="example-1-create-a-function-that-has-the-outputtype-of-string"></a><span data-ttu-id="79f68-125">Exempel 1: skapa en funktion som har en strängs OutputType</span><span class="sxs-lookup"><span data-stu-id="79f68-125">Example 1: Create a function that has the OutputType of String</span></span>

```powershell
function Send-Greeting
{
  [OutputType([String])]
  Param ($Name)

  "Hello, $Name"
}
```

<span data-ttu-id="79f68-126">Använd cmdleten om du vill se den resulterande utdatatyps egenskapen `Get-Command` .</span><span class="sxs-lookup"><span data-stu-id="79f68-126">To see the resulting output type property, use the `Get-Command` cmdlet.</span></span>

```powershell
(Get-Command Send-Greeting).OutputType
```

```Output
Name                                               Type
----                                               ----
System.String                                      System.String
```

### <a name="example-2-use-the-output-attribute-to-indicate-dynamic-output-types"></a><span data-ttu-id="79f68-127">Exempel 2: Använd attributet output för att ange dynamiska typer av utdata</span><span class="sxs-lookup"><span data-stu-id="79f68-127">Example 2: Use the Output attribute to indicate dynamic output types</span></span>

<span data-ttu-id="79f68-128">Följande avancerade funktion använder attributet OutputType för att indikera att funktionen returnerar olika typer beroende på den parameter uppsättning som används i kommandot funktion.</span><span class="sxs-lookup"><span data-stu-id="79f68-128">The following advanced function uses the OutputType attribute to indicate that the function returns different types depending on the parameter set used in the function command.</span></span>

```powershell
function Get-User
{
  [CmdletBinding(DefaultParameterSetName="ID")]

  [OutputType("System.Int32", ParameterSetName="ID")]
  [OutputType([String], ParameterSetName="Name")]

  Param (
    [parameter(Mandatory=$true, ParameterSetName="ID")]
    [Int[]]
    $UserID,

    [parameter(Mandatory=$true, ParameterSetName="Name")]
    [String[]]
    $UserName
  )

  <function body>
}
```

### <a name="example-3-shows-when-an-actual-output-differs-from-the-outputtype"></a><span data-ttu-id="79f68-129">Exempel 3: visar när en faktisk utmatning skiljer sig från OutputType</span><span class="sxs-lookup"><span data-stu-id="79f68-129">Example 3: Shows when an actual output differs from the OutputType</span></span>

<span data-ttu-id="79f68-130">Följande exempel visar att värdet för egenskapen OutputType visas i värdet för egenskapen OutputType, även om det är felaktigt.</span><span class="sxs-lookup"><span data-stu-id="79f68-130">The following example demonstrates that the output type property value displays the value of the OutputType attribute, even when it is inaccurate.</span></span>

<span data-ttu-id="79f68-131">`Get-Time`Funktionen returnerar en sträng som innehåller kort formen av tiden i alla DateTime-objekt.</span><span class="sxs-lookup"><span data-stu-id="79f68-131">The `Get-Time` function returns a string that contains the short form of the time in any DateTime object.</span></span> <span data-ttu-id="79f68-132">Men attributet OutputType rapporterar att det returnerar ett **system. DateTime** -objekt.</span><span class="sxs-lookup"><span data-stu-id="79f68-132">However, the OutputType attribute reports that it returns a **System.DateTime** object.</span></span>

```powershell
function Get-Time
{
  [OutputType([DateTime])]
  Param (
    [parameter(Mandatory=$true)]
    [Datetime]$DateTime
  )

  $DateTime.ToShortTimeString()
}
```

<span data-ttu-id="79f68-133">`GetType()`Metoden bekräftar att funktionen returnerar en sträng.</span><span class="sxs-lookup"><span data-stu-id="79f68-133">The `GetType()` method confirms that the function returns a string.</span></span>

```powershell
(Get-Time -DateTime (Get-Date)).GetType().FullName
```

```Output
System.String
```

<span data-ttu-id="79f68-134">Men egenskapen OutputType, som hämtar värdet från attributet OutputType, rapporterar att funktionen returnerar ett **datetime** -objekt.</span><span class="sxs-lookup"><span data-stu-id="79f68-134">However, the OutputType property, which gets its value from the OutputType attribute, reports that the function returns a **DateTime** object.</span></span>

```powershell
(Get-Command Get-Time).OutputType
```

```Output
Name                                      Type
----                                      ----
System.DateTime                           System.DateTime
```

### <a name="example-4-a-function--that-shouldnt-have-output"></a><span data-ttu-id="79f68-135">Exempel 4: en funktion som inte har utdata</span><span class="sxs-lookup"><span data-stu-id="79f68-135">Example 4: A function  that shouldn't have output</span></span>

<span data-ttu-id="79f68-136">I följande exempel visas en anpassad funktion som ska utföras och åtgärdas, men som inte returnerar något.</span><span class="sxs-lookup"><span data-stu-id="79f68-136">The following example shows a custom function that should perform and action but not return anything.</span></span>

```powershell
function Invoke-Notepad
{
  [OutputType([System.Void])]
  Param ()
  & notepad.exe | Out-Null
}
```

## <a name="notes"></a><span data-ttu-id="79f68-137">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="79f68-137">NOTES</span></span>

<span data-ttu-id="79f68-138">Värdet för egenskapen OutputType för ett **FunctionInfo** -objekt är en matris med **system. Management. Automation. PSTypeName** -objekt, som var och en har namn och typ egenskaper.</span><span class="sxs-lookup"><span data-stu-id="79f68-138">The value of the OutputType property of a **FunctionInfo** object is an array of **System.Management.Automation.PSTypeName** objects, each of which have Name and Type properties.</span></span>

<span data-ttu-id="79f68-139">Om du bara vill hämta namnet på varje Utdatatyp använder du kommandot med följande format.</span><span class="sxs-lookup"><span data-stu-id="79f68-139">To get only the name of each output type, use a command with the following format.</span></span>

```powershell
(Get-Command Get-Time).OutputType | ForEach {$_.Name}
```

<span data-ttu-id="79f68-140">Värdet för egenskapen OutputType kan vara null.</span><span class="sxs-lookup"><span data-stu-id="79f68-140">The value of the OutputType property can be null.</span></span> <span data-ttu-id="79f68-141">Använd ett null-värde när utdata inte är en .NET-typ, till exempel ett **WMI-** objekt eller en formaterad vy av ett objekt.</span><span class="sxs-lookup"><span data-stu-id="79f68-141">Use a null value when the output is a not a .NET type, such as a **WMI** object or a formatted view of an object.</span></span>

## <a name="see-also"></a><span data-ttu-id="79f68-142">SE ÄVEN</span><span class="sxs-lookup"><span data-stu-id="79f68-142">SEE ALSO</span></span>

[<span data-ttu-id="79f68-143">about_Functions</span><span class="sxs-lookup"><span data-stu-id="79f68-143">about_Functions</span></span>](about_Functions.md)

[<span data-ttu-id="79f68-144">about_Functions_Advanced</span><span class="sxs-lookup"><span data-stu-id="79f68-144">about_Functions_Advanced</span></span>](about_Functions_Advanced.md)

[<span data-ttu-id="79f68-145">about_Functions_Advanced_Methods</span><span class="sxs-lookup"><span data-stu-id="79f68-145">about_Functions_Advanced_Methods</span></span>](about_Functions_Advanced_Methods.md)

[<span data-ttu-id="79f68-146">about_Functions_Advanced_Parameters</span><span class="sxs-lookup"><span data-stu-id="79f68-146">about_Functions_Advanced_Parameters</span></span>](about_Functions_Advanced_Parameters.md)

[<span data-ttu-id="79f68-147">about_Functions_CmdletBindingAttribute</span><span class="sxs-lookup"><span data-stu-id="79f68-147">about_Functions_CmdletBindingAttribute</span></span>](about_Functions_CmdletBindingAttribute.md)
